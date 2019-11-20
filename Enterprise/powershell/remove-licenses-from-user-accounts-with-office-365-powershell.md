---
title: 使用 Office 365 PowerShell 删除用户帐户的许可证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/23/2019
audience: Admin
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
description: 介绍如何使用 Office 365 PowerShell 删除之前分配给用户的 Office 365 许可证。
ms.openlocfilehash: bfd333b649df1d346a45abc3e8b9e35666f8f582
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747538"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 删除用户帐户的许可证

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下来，使用此命令列出租户的许可证计划。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下来，获取要删除其许可证的帐户的登录名，也称为用户主体名称（UPN）。

最后，指定用户登录和许可证计划名称，删除 "<" 和 ">" 字符，然后运行这些命令。

```powershell
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

   
若要查看组织中的许可计划（**AccountSkuID** ）信息，请参阅下列主题：
    
  - [使用 Office 365 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)
    
  - [使用 Office 365 PowerShell 查看帐户许可证和服务详细信息](view-account-license-and-service-details-with-office-365-powershell.md)
    
如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。
    
### <a name="removing-licenses-from-user-accounts"></a>从用户帐户中删除许可证

要从现有的用户帐户中删除许可证，请使用以下语法：
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

本示例从用户`litwareinc:ENTERPRISEPACK`帐户 BelindaN@litwareinc.com 中删除（Office 365 企业版 E3）许可证。
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>您不能使用 Set-msoluserlicense cmdlet 从*已取消*的许可证中取消分配用户。 您必须为 Microsoft 365 管理中心中的每个用户帐户单独执行此操作。
>

要从一组现有的授权用户中删除许可证，请使用下列方法之一：
  
- **基于现有帐户属性筛选帐户**为此，请使用以下语法：
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

本示例将从`litwareinc:ENTERPRISEPACK`美国的销售部门的用户的所有帐户中删除（Office 365 企业版 E3）许可证。
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **使用特定帐户的列表**为此，请执行以下步骤：
    
1. 创建并保存一个文本文件，其中每一行都有一个帐户，如下所示：
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. 使用以下语法：
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

本示例从文本文件`litwareinc:ENTERPRISEPACK` C:\My Documents\Accounts.txt. 中定义的用户帐户中删除（Office 365 企业版 E3）许可证。
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

要从所有现有的用户帐户中删除许可证，请使用以下语法：
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

本示例从所有`litwareinc:ENTERPRISEPACK`现有的授权用户帐户中删除（Office 365 企业版 E3）许可证。
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

释放许可证的另一种方法是删除用户帐户。 有关详细信息，请参阅[Delete and restore user accounts With Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)。
  
## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a>刚开始接触 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

