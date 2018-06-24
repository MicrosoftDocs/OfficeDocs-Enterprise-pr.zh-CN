---
title: 分配用户许可证时禁用访问服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: 了解如何将许可证分配给用户帐户和使用 Office 365 PowerShell 中的同时禁用特定的服务计划。
ms.openlocfilehash: 40abaa37b5a88eb69b01779894e851068a6454ee
ms.sourcegitcommit: fe406eacd92dd5b3bd8c127b7bd8f2d0ef216404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2018
ms.locfileid: "20017398"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>分配用户许可证时禁用访问服务

**摘要：** 了解如何将许可证分配给用户帐户和使用 Office 365 PowerShell 中的同时禁用特定的服务计划。
  
Office 365 订阅附带的个别服务的服务计划。Office 365 管理员通常需要禁用某些计划时向用户分配许可证。使用本文中的说明，您可以禁用特定的服务计划使用 PowerShell 为单个用户帐户或多个用户帐户时分配 Office 365 许可证。
  
## <a name="before-you-begin"></a>准备工作

若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a>收集有关订阅和服务计划信息

运行以下命令以查看您当前的订阅：
  
```
Get-MsolAccountSku
```

在显示的`Get-MsolAccountSku`命令：
  
- **AccountSkuId**是您组织中的订阅\<OrganizationName >:\<订阅 > 格式。\<OrganizationName > 是注册 Office 365 中，为您的组织都是唯一时提供的值。\<订阅 > 值是特定订阅。例如，对于 litwareinc: enterprisepack，组织名称为 litwareinc，并且订阅名称是 ENTERPRISEPACK (Office 365 企业版 E3)。
    
- **ActiveUnits**是您已购买订阅的许可证数量。
    
- **WarningUnits**是，您还未更新的且将过期后 30 天的宽限期订阅中的许可证数量。
    
- **ConsumedUnits**已分配给订阅的用户的许可证数量。
    
请注意 AccountSkuId 为您的 Office 365 订阅包含您想要许可证的用户。此外，还要确保有足够的许可证分配 （减去从**ActiveUnits** **ConsumedUnits** ）。
  
接下来，运行以下命令以查看有关所有订阅中可用的 Office 365 服务计划的详细信息：
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

通过此命令显示，确定想要禁用时向用户分配许可证哪些服务计划。
  
下面是服务计划和其相应的 Office 365 服务的部分列表。
  
|**服务计划**|**说明**|
|:-----|:-----|
|SWAY  <br/> |Sway  <br/> |
|INTUNE_O365  <br/> |Office 365 移动设备管理  <br/> |
|YAMMER_ENTERPRISE  <br/> |Yammer  <br/> |
|RMS_S_ENTERPRISE  <br/> |Azure 权限管理 (RMS)  <br/> |
|OFFICESUBSCRIPTION  <br/> |Office Professional Plus  <br/> |
|MCOSTANDARD  <br/> |Skype for Business Online  <br/> |
|SHAREPOINTWAC  <br/> |Office Online  <br/> |
|SHAREPOINTENTERPRISE  <br/> |SharePoint Online  <br/> |
|EXCHANGE_S_ENTERPRISE  <br/> |Exchange Online 计划 2  <br/> |
   
现在，您有 AccountSkuId 以及禁用的服务计划，您可以分配单个用户或多个用户的许可证。
  
## <a name="for-a-single-user"></a>为单个用户

为单个用户，填写的用户帐户、 AccountSkuId，并禁用和删除的说明性文本服务计划的列表的用户主体名称和\<和 > 字符。然后，在 PowerShell 命令提示符处运行生成命令。
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

下面是用于 contoso:ENTERPRISEPACK 许可证，名为 belindan@contoso.com 的帐户的示例命令块，若要禁用的服务计划 RMS_S_ENTERPRISE、 SWAY、 INTUNE_O365 和 YAMMER_ENTERPRISE:
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a>为多个用户

若要执行此管理任务的多个用户，创建包含 UserPrincipalName 和 UsageLocation 字段的逗号分隔值 (CSV) 文本文件。下面是一个示例：
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

接下来，填写的输入和输出 CSV 文件、 SKU ID 的帐户和服务计划，若要禁用，列表的位置，然后在 PowerShell 命令提示符中运行生成命令。
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

此 PowerShell 命令块：
  
- 显示每个用户的用户主体名称。
    
- 分配自定义为每个用户的许可证。
    
- 与已处理的所有用户创建一个 CSV 文件，并显示其许可证状态。
    
## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 禁止访问服务](disable-access-to-services-with-office-365-powershell.md)
  
[禁用对 Sway 与 Office 365 PowerShell 访问](disable-access-to-sway-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)

