---
title: 使用 Office 365 PowerShell 冻结用户账户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: 介绍如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 帐户的访问。
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546473"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 冻结用户账户

**摘要：** 介绍如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 帐户的访问。
  
阻止对 Office 365 帐户访问可防止任何人使用的帐户登录和访问的服务和 Office 365 组织中的数据。Office 365 PowerShell 中可用于阻止对单个访问和多个用户帐户。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用 Azure Active Directory PowerShell 图模块

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
 
### <a name="block-access-to-individual-user-accounts"></a>阻止对单个用户帐户的访问

使用以下语法阻止单个用户帐户：
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> 设置 AzureAD cmdlet 中的 ObjectID 参数接受任一的帐户登录名称，也称为用户主体名称或该帐户的对象 id。 
  
此示例阻止访问用户帐户 fabricec@litwareinc.com。
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

若要取消阻止此用户帐户，请运行以下命令：
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

若要显示 UPN 基于用户的显示名称的用户帐户，请使用以下命令：
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

本示例显示名为 Caleb Sills 的用户的用户帐户 UPN。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要阻止基于用户的显示名称的帐户，请使用以下命令：
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

在任何时候，您可以检查阻止的状态的用户帐户，使用以下命令：
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>阻止对多个用户帐户的访问

若要阻止对多个用户帐户的访问，请创建包含一个帐户登录名称类似的每一行上一个文本文件：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

以下命令，在示例文本文件是 C:\My Documents\Accounts.txt。将此替换为文本文件的路径和文件名称。
  
若要阻止访问该文本文件中列出的帐户，请运行以下命令：
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

若要解除阻止该文本文件中列出的帐户，请运行以下命令：
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用 Windows PowerShell 的 Microsoft Azure Active Directory 模块

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

    
### <a name="block-access-to-individual-user-accounts"></a>阻止对单个用户帐户的访问

使用以下语法来阻止对单个用户帐户的访问：
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

此示例阻止访问用户帐户 fabricec@litwareinc.com。
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

若要取消阻止该用户帐户，请运行以下命令：
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

在任何时候，您可以检查阻止的状态的用户帐户，使用以下命令：
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>阻止对多个用户帐户的访问

首先，创建一个文本文件，包含如下所示的每一行上的一个帐户：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
以下命令，在示例文本文件是 C:\My Documents\Accounts.txt。将此替换为文本文件的路径和文件名称。
    
若要阻止访问该文本文件中列出的帐户，请运行以下命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
若要解除阻止该文本文件中列出的帐户，请运行以下命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
