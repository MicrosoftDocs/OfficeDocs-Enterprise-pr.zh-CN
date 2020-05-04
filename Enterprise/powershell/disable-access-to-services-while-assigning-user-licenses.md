---
title: 在分配用户许可证时禁止访问服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: 了解如何使用 Office 365 PowerShell 将许可证分配给用户帐户并同时禁用特定服务计划。
ms.openlocfilehash: b1fcd8afd9f9fee5b249752821385cd888519a37
ms.sourcegitcommit: 11751463c952f57f397b886eebfbd37790d461af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2020
ms.locfileid: "44009467"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>在分配用户许可证时禁止访问服务

Office 365 订阅随附有针对单个服务的服务计划。 在向用户分配许可证时，Office 365 管理员通常需要禁用某些计划。 使用本文中的说明，可以分配 Office 365 许可证，同时使用 PowerShell 为单个用户帐户或多个用户帐户禁用特定服务计划。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下来，使用此命令列出租户的许可证计划。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下来，获取要向其添加许可证（也称为用户主体名称（UPN））的帐户的登录名。

接下来，编译要启用的服务的列表。 有关许可证计划（也称为产品名称）、其包含的服务计划及其相应的友好名称的完整列表，请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。

对于下面的命令块，请填写用户帐户的用户主体名称、SKU 部件号以及用于启用和删除说明文本和\<和 > 字符的服务计划列表。 然后，在 PowerShell 命令提示符处运行生成的命令。
  
```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

接下来，运行以下命令查看你的当前订阅：
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
>

在显示`Get-MsolAccountSku`命令时：
  
- **AccountSkuId**是组织在 OrganizationName>： \<\<订阅> 格式中的一种订阅。 \<OrganizationName> 是您在 Office 365 中注册时提供的值，并且对于您的组织是唯一的。 \<订阅> 值适用于特定订阅。 例如，对于 litwareinc： ENTERPRISEPACK，组织名称为 litwareinc，订阅名称为 ENTERPRISEPACK （Office 365 企业版 E3）。
    
- **ActiveUnits**是您为订阅购买的许可证的数量。
    
- **WarningUnits**是尚未续订的订阅中的许可证数量，在30天的宽限期后将过期。
    
- **ConsumedUnits**是您为订阅分配给用户的许可证数。
    
请注意包含要许可的用户的 Office 365 订阅的 AccountSkuId。 此外，请确保有足够的许可证可供分配（从**ActiveUnits**中减去**ConsumedUnits** ）。
  
接下来，运行此命令以查看有关所有订阅中可用的 Office 365 服务计划的详细信息：
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

在此命令的显示中，确定在向用户分配许可证时要禁用的服务计划。
  
下面是服务计划及其对应的 Office 365 服务的部分列表。

下表显示了最常用服务的 Office 365 服务计划及其友好名称。 服务计划列表可能会有所不同。 
  
|**服务计划**|**说明**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 权限管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |适用于企业的 Microsoft 365 应用程序 *（以前称为 Office 365 专业增强版）*  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online 计划 2  <br/> |
   
有关许可证计划（也称为产品名称）、其包含的服务计划及其相应的友好名称的完整列表，请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。
   
现在，您已拥有要禁用的 AccountSkuId 和服务计划，您可以为单个用户或多个用户分配许可证。
  
### <a name="for-a-single-user"></a>对于单个用户

对于单个用户，请填写用户帐户的用户主体名称、AccountSkuId 以及要禁用的服务计划列表，并删除说明文本和\<和 > 字符。 然后，在 PowerShell 命令提示符处运行生成的命令。
  
```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

以下是名为 belindan@contoso.com 的帐户的示例命令块，用于 contoso： ENTERPRISEPACK 许可证，要禁用的服务计划包括 RMS_S_ENTERPRISE、SWAY、INTUNE_O365 和 YAMMER_ENTERPRISE：
  
```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a>为多个用户

若要对多个用户执行此管理任务，请创建一个逗号分隔值（CSV）文本文件，该文件包含 UserPrincipalName 和 UsageLocation 字段。 如以下示例所示：
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

接下来，填写输入和输出 CSV 文件的位置、帐户 SKU ID 和要禁用的服务计划的列表，然后在 PowerShell 命令提示符处运行生成的命令。
  
```powershell
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

此 PowerShell 命令块：
  
- 显示每个用户的用户主体名称。
    
- 将自定义许可证分配给每个用户。
    
- 创建一个 CSV 文件，其中包含已处理的所有用户，并显示其许可证状态。
    
## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 禁止访问服务](disable-access-to-services-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 禁止访问 Sway](disable-access-to-sway-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理用户帐户、许可证和组](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
