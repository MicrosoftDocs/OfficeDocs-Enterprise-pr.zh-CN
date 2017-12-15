---
title: "在分配用户许可时，禁用对服务的访问"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "了解如何将许可证分配给用户帐户，并在同一时间使用 Office 365 PowerShell 禁用特定的服务计划。"
ms.openlocfilehash: 907314e13b353e5d5ddbcd8fe467db568473d0b3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>在分配用户许可时，禁用对服务的访问

**摘要：** 了解如何将许可证分配给用户帐户，并在同一时间使用 Office 365 PowerShell 禁用特定的服务计划。
  
Office 365 订阅带有单个服务的服务计划。Office 365 管理员经常需要向用户分配许可证时禁用某些计划。与本文中的说明进行操作，您可以禁用特定服务计划使用 PowerShell 的单个用户帐户或多个用户帐户时分配 Office 365 提供许可证。
  
> [!NOTE]
> 这篇文章基于 Siddhartha Parmar，Microsoft 技术支持升级工程师的工作。 
  
## <a name="before-you-begin"></a>开始之前

若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a>收集有关订阅和服务计划的信息

运行以下命令以查看您当前的订阅：
  
```
Get-MsolAccountSku
```

在显示的`Get-MsolAccountSku`命令：
  
- **AccountSkuId**是在您组织的订阅\<单位名称 >:\<订阅 > 格式。\<单位名称 > 是提供当您注册 Office 365 并为您的组织中是唯一的值。\<订阅 > 值是为特定的预订。例如，对于 litwareinc:ENTERPRISEPACK，组织名称是 litwareinc，而订阅名称是 ENTERPRISEPACK (Office 365 企业 E3)。
    
- **ActiveUnits**为您的订阅购买的许可证的数量。
    
- **WarningUnits**是在您还没有更新的且 30 天宽限期过后将过期的订阅许可证的数量。
    
- **ConsumedUnits**是已指派给订阅的用户许可证的数量。
    
请注意您的 Office 365 订阅包含您想要授予许可的用户 AccountSkuId。另外，请确保有足够的许可来分配 （减去从**ActiveUnits** **ConsumedUnits** ）。
  
下一步，运行以下命令可查看有关 Office 365 提供服务计划所提供的所有订阅的详细信息：
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

通过此命令显示，确定您想要禁用时将许可证分配给用户的服务计划。
  
这里是服务计划和其相应的 Office 365 提供服务的部分列表。
  
|**服务计划**|**描述**|
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
   
既然您已经有 AccountSkuId 和禁用的服务计划，还可以为单个用户或多个用户的许可证。
  
## <a name="for-a-single-user"></a>为单个用户

对于单个用户，填写用户主要名称的用户帐户、 AccountSkuId，以及服务计划的列表禁用和删除 ' 的说明文字和\<和 > 字符。然后，PowerShell 命令提示符处运行生成的命令。
  
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

下面是示例命令块名 belindan@contoso.com，为 contoso:ENTERPRISEPACK 许可证，有关的帐户，若要禁用的服务计划 RMS_S_ENTERPRISE、 SWAY、 INTUNE_O365 和 YAMMER_ENTERPRISE:
  
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

## <a name="for-multiple-users"></a>多个用户

若要为多个用户执行此管理任务，创建范围内和 UsageLocation 字段包含逗号分隔值 (CSV) 文本文件。下面是一个示例：
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

下一步，填写的输入和输出的 CSV 文件、 帐户 SKU ID 和服务计划，若要禁用，列表的位置，然后 PowerShell 命令提示符处运行生成的命令。
  
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

此 PowerShell 命令块：
  
- 显示每个用户的用户主体名称。
    
- 指定自定义每个用户的许可证。
    
- 与已处理的所有用户创建 CSV 文件，并显示其许可证状态。
    
## <a name="see-also"></a>See also

#### 

[使用 Office 365 PowerShell 禁止访问服务](disable-access-to-services-with-office-365-powershell.md)
  
[禁止访问与 Office 365 PowerShell 的 Sway](disable-access-to-sway-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)

