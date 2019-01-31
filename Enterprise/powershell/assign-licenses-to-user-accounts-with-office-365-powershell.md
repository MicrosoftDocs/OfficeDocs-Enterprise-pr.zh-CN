---
title: 使用 Office 365 PowerShell 向用户帐户分配许可证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
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
description: 介绍如何使用 Office 365 PowerShell 中分配给未许可用户的 Office 365 许可证。
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651176"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 向用户帐户分配许可证

**摘要：** 介绍如何使用 Office 365 PowerShell 中分配给未许可用户的 Office 365 许可证。
  
用户无法使用任何 Office 365 服务，直到其帐户已从许可计划分配许可证。您可以使用 Office 365 PowerShell 中快速将许可证分配给未经授权的帐户。 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下来，使用此命令租户中列出的许可计划。

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下来，获取要向其添加许可证，也称为的用户主体名称 (UPN) 的帐户的登录名称。

最后，指定用户登录名和许可计划名称，并运行以下命令。

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

运行**Get-msolaccountsku**命令以查看您的组织中的每个计划中可用的许可计划和可用许可证的数目。每个计划中可用的许可证数是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。有关许可计划、 许可证和服务的详细信息，请参阅[查看许可证和身份验证服务与 Office 365 PowerShell 中](view-licenses-and-services-with-office-365-powershell.md)。
    
要在组织中查找的未经授权的帐户，请运行以下命令。

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
您可以仅许可证分配用户帐户具有**UsageLocation**属性设置为有效的 ISO 3166-1 alpha 2 国家/地区代码。例如，美国的电话和法国 FR 我们。在某些国家/地区，某些 Office 365 服务不可用。有关详细信息，请参阅[关于许可限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。
    
要查找不具有**UsageLocation**值的帐户，请运行以下命令。

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

要设置帐户**UsageLocation**值，请运行以下命令。

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

例如：

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
如果使用 **Get-MsolUser** cmdlet，而未使用 **-All** 参数，只返回前 500 个帐户。

### <a name="assigning-licenses-to-user-accounts"></a>向用户帐户分配许可证
    
若要将许可证分配给用户，请在 Office 365 PowerShell 中使用以下命令。
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

此示例从**litwareinc: enterprisepack** (Office 365 企业版 E3) 许可计划许可的用户**belindan@litwareinc.com**分配许可证：
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

要将许可证分配给多个未经授权的用户，请运行以下命令。
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
>您不能相同的许可计划从多个许可证分配给用户。如果您没有足够的可用许可证，它们可用的许可证运行之前由**Get-msoluser** cmdlet 返回的顺序的用户分配许可证。
>

本示例将从**litwareinc: enterprisepack** (Office 365 企业版 E3) 许可计划许可证分配给所有未经授权的用户中：
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

本示例将这些相同的许可证分配给未许可用户在美国销售部门中：
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>刚开始接触 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
