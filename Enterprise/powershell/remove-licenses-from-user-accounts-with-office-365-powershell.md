---
title: 使用 Office 365 PowerShell 删除用户帐户的许可证
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: 介绍如何使用 Office 365 PowerShell 中删除之前已分配给用户的 Office 365 许可证。
ms.openlocfilehash: 5b5f4550a5fade7f95669ad455aebd5d5f7fbf34
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651216"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 删除用户帐户的许可证

**摘要：** 介绍如何使用 Office 365 PowerShell 中删除之前已分配给用户的 Office 365 许可证。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下来，使用此命令租户中列出的许可计划。

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下来，获取要为其删除许可证，也称为的用户主体名称 (UPN) 的帐户的登录名称。

最后，指定用户登录和许可计划的名称，删除"<"和">"字符，并运行以下命令。

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

   
若要查看组织中的许可计划 (**AccountSkuID** ) 信息，请参阅以下主题：
    
  - [使用 Office 365 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)
    
  - [使用 Office 365 PowerShell 查看帐户许可证和服务详细信息](view-account-license-and-service-details-with-office-365-powershell.md)
    
如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。
    
### <a name="removing-licenses-from-user-accounts"></a>从用户帐户删除许可证

要从现有的用户帐户中删除许可证，请使用以下语法：
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

此示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3) 许可证的用户帐户 BelindaN@litwareinc.com。
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

要从一组现有的授权用户中删除许可证，请使用下列方法之一：
  
- **筛选器基于现有帐户属性的帐户**若要执行此操作，使用以下语法：
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

此示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3) 许可证从众所周知在美国销售部门中的用户。
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **使用特定帐户的列表**若要执行此操作，执行以下步骤：
    
1. 创建并保存一个文本文件，其中每一行都有一个帐户，如下所示：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. 使用以下语法：
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

此示例删除`litwareinc:ENTERPRISEPACK`从文本文件 C:\My Documents\Accounts.txt 中定义的用户帐户 (Office 365 企业版 E3) 许可证。
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

要从所有现有的用户帐户中删除许可证，请使用以下语法：
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

此示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3) 从所有现有的许可证许可用户帐户。
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

通过删除的用户帐户是另一种方式以释放许可证。有关详细信息，请参阅[删除并还原与 Office 365 PowerShell 中的用户帐户](delete-and-restore-user-accounts-with-office-365-powershell.md)。
  
## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a>刚开始接触 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

