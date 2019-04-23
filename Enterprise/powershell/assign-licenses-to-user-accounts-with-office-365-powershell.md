---
title: 使用 Office 365 PowerShell 向用户帐户分配许可证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: 说明如何使用 office 365 PowerShell 将 office 365 许可证分配给未经许可的用户。
ms.openlocfilehash: ac2cdb8c303cacc5c9664b877ba86a5b196432b1
ms.sourcegitcommit: 51f9e89e4b9d54f92ef5c70468bda96e664b8a6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "31957643"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 向用户帐户分配许可证

**摘要:** 说明如何使用 office 365 PowerShell 将 office 365 许可证分配给未经许可的用户。
  
用户在向其帐户分配许可计划中的许可证之前, 不能使用任何 Office 365 服务。 您可以使用 Office 365 PowerShell 将许可证快速分配给未经许可的帐户。 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下来, 使用此命令列出租户的许可证计划。

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下来, 获取要向其添加许可证 (也称为用户主体名称 (UPN)) 的帐户的登录名。

最后, 指定用户登录名和许可证计划名称, 并运行这些命令。

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

运行**get-msolaccountsku**命令可以查看组织中每个计划中可用的许可计划和可用许可证的数量。 每个计划中可用的许可证数量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。 有关许可计划、许可证和服务的详细信息, 请参阅[使用 Office 365 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)。
    
若要在组织中查找未授权帐户, 请运行此命令。

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
只能将许可证分配给其**UsageLocation**属性设置为有效的 ISO 3166-1 alpha-2 国家/地区代码的用户帐户。 例如，US 代表美国，FR 代表法国。 某些 Office 365 服务在某些国家/地区不可用。 有关详细信息，请参阅[关于许可证限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。
    
若要查找不具有**UsageLocation**值的帐户, 请运行此命令。

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

若要设置帐户的**UsageLocation**值, 请运行此命令。

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

例如：

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
如果使用 **Get-MsolUser** cmdlet，而未使用 **-All** 参数，只返回前 500 个帐户。

### <a name="assigning-licenses-to-user-accounts"></a>向用户帐户分配许可证
    
若要将许可证分配给用户, 请使用 Office 365 PowerShell 中的以下命令。
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

本示例将**litwareinc: ENTERPRISEPACK** (Office 365 企业版 E3) 许可计划中的许可证分配给未经许可的用户**belindan@litwareinc.com**:
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

若要将许可证分配给多个未经许可的用户, 请运行此命令。
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>您无法使用相同的许可计划为用户分配多个许可证。 如果没有足够可用的许可证，将按照 **Get-MsolUser** cmdlet 返回的顺序为用户分配许可证，直到可用许可证用尽。
>

此示例将**litwareinc: ENTERPRISEPACK** (Office 365 企业版 E3) 许可计划中的许可证分配给所有未经许可的用户:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

本示例将这些相同的许可证分配给美国的销售部门中未经许可的用户:
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a>刚开始接触 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
