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
description: 介绍如何使用 office 365 PowerShell 阻止和取消阻止对 Office 365 帐户的访问。
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491388"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 冻结用户账户

**摘要:** 介绍如何使用 office 365 PowerShell 阻止和取消阻止对 Office 365 帐户的访问。
  
阻止访问 office 365 帐户将阻止任何人使用该帐户登录并访问 Office 365 组织中的服务和数据。 您可以使用 Office 365 PowerShell 阻止对单个和多个用户帐户的访问。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
 
### <a name="block-access-to-individual-user-accounts"></a>阻止对单个用户帐户的访问

使用以下语法来阻止单个用户帐户:
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> AzureAD cmdlet 中的-ObjectID 参数可接受帐户登录名 (也称为 "用户主体名称") 或帐户的对象 ID。 
  
此示例阻止访问用户帐户 fabricec@litwareinc.com。
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

若要取消阻止此用户帐户，请运行以下命令：
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

若要根据用户的显示名称显示用户帐户 UPN, 请使用以下命令:
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

本示例显示名为 Caleb Sills 的用户的用户帐户 UPN。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要基于用户的显示名称阻止某个帐户, 请使用以下命令:
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

在任何时候, 都可以使用以下命令检查用户帐户的阻止状态:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>阻止对多个用户帐户的访问

若要阻止对多个用户帐户的访问, 请创建一个文本文件, 其中每行包含一个帐户登录名, 如下所示:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

在以下命令中, 示例文本文件为 C:\My Documents\Accounts.txt。 将此替换为您的文本文件的路径和文件名。
  
若要阻止访问该文本文件中列出的帐户，请运行以下命令：
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

若要解除阻止该文本文件中列出的帐户，请运行以下命令：
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

    
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

在任何时候, 都可以使用以下命令检查用户帐户的阻止状态:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>阻止对多个用户帐户的访问

首先, 创建一个文本文件, 其中每行包含一个帐户, 如下所示:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
在以下命令中, 示例文本文件为 C:\My Documents\Accounts.txt。 将此替换为您的文本文件的路径和文件名。
    
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
