---
title: 使用 Office 365 PowerShell 删除用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: 了解如何使用 Office 365 PowerShell 删除 Office 365 用户帐户。
ms.openlocfilehash: ca9224c58bda9a0d3e226db17efeb9af8de076f0
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004675"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 删除用户帐户

可使用 Office 365 PowerShell 删除用户帐户。
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。

连接后，使用下列语法删除单个用户帐户：
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

本示例将删除用户帐户 fabricec@litwareinc.com。
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **AzureADUser** cmdlet 中的 **-ObjectID**参数可接受帐户的登录名（也称为 "用户主体名称"）或帐户的对象 ID。
  
若要显示基于用户名的帐户名称，请使用下列命令：
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本示例显示名为 Caleb Sills 的用户的帐户名。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要删除基于用户显示名称的帐户，请使用下列命令：
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块

使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块删除用户帐户时，该帐户不会被永久删除。可以在 30 天内还原已删除的用户帐户。

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

若要删除一个用户帐户，请使用下面的语法：
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
>

本示例删除用户帐户 BelindaN@litwareinc.com。
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

若要在 30 天的宽限期内还原已删除的用户帐户，请使用下面的语法：
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

本示例还原已删除的帐户 BelindaN@litwareinc.com。
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **注意：**
  
- 若要查看可以还原的已删除用户的列表，请运行以下命令：
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- 如果用户帐户的初始用户主体名称已被另一个帐户使用，那么在还原用户帐户时，请使用 _NewUserPrincipalName_ 参数而不是 _UserPrincipalName_ 来指定一个不同的用户主体名称。


## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户、许可证和组](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
