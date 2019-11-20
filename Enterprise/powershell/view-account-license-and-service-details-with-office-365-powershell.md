---
title: 使用 Office 365 PowerShell 查看帐户许可证和服务详细信息
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: 说明如何使用 Office 365 PowerShell 确定已分配给用户的 Office 365 服务。
ms.openlocfilehash: 53668a69d72cdcbe912d550be2b9e571b7f6c0e0
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747471"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>使用 Office 365 PowerShell 查看帐户许可证和服务详细信息

在 Office 365 中，许可计划（也称为 Sku 或 Office 365 计划）的许可证为用户提供了对为这些计划定义的 Office 365 服务的访问权限。 但是，用户可能无法访问当前分配给他们的许可证中可用的所有服务。 您可以使用 Office 365 PowerShell 来查看用户帐户上的服务的状态。 

有关许可计划、许可证和服务的详细信息，请参阅[使用 Office 365 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
接下来，使用此命令列出租户的许可证计划。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

使用这些命令列出每个许可计划中可用的服务。

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

使用这些命令列出分配给用户帐户的许可证。

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

接下来，运行此命令，列出您的组织中可用的许可计划。 

```powershell
Get-MsolAccountSku
```

接下来，运行此命令，列出每个许可计划中可用的服务，以及这些服务的列出顺序（索引号）。

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
```
  
使用此命令可列出分配给用户的许可证以及它们的列出顺序（索引号）。

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

>[!Note]
>如果您使用 **Get-MsolUser** cmdlet 而无需使用 _All_ 参数，仅可返回前 500 个帐户。
>
   

### <a name="to-view-services-for-a-user-account"></a>查看用户帐户的服务

若要查看用户有权访问的所有 Office 365 服务，请使用以下语法：
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

本示例显示用户 BelindaN@litwareinc.com 有权访问的服务。 这将显示与分配给她的帐户相关联的所有许可证相关联的服务。
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

本示例显示了用户 BelindaN@litwareinc.com 可以从分配给她的帐户（索引号为0）的第一个许可证访问的服务。
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

若要查看已分配*多个许可证*的用户的所有服务，请使用以下语法：

```powershell
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="new-to-office-365"></a>刚开始接触 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
