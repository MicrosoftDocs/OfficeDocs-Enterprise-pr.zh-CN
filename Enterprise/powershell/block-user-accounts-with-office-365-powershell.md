---
title: "使用 Office 365 PowerShell 冻结用户账户"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- DecEntMigration
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "解释如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 提供帐户的访问。"
ms.openlocfilehash: f22656426e7aa3adf764a3f90adea84cf57a5e89
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="block-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 冻结用户账户

**摘要：** 解释如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 提供帐户的访问。
  
阻止访问 Office 365 的帐户，可以防止任何人使用该帐户登录并访问服务和 Office 365 提供组织中的数据。如果阻止了对帐户的访问，当他们尝试登录用户会收到下面的错误消息：
  
![阻止的 Office 365 帐户。](images/o365_powershell_account_blocked.png)
  
您可以使用 Office 365 PowerShell 阻止访问单个和多个用户帐户。
  
## <a name="before-you-begin"></a>开始之前

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 如果阻止了用户帐户，可能需要最长为 24 小时才可生效，用户的所有设备和客户端上。
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>使用 Office 365 PowerShell 阻止对单个用户帐户的访问

使用以下语法来阻止对单个用户帐户的访问：
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

此示例阻止访问用户帐户 fabricec@litwareinc.com。
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

若要取消阻止该用户帐户，请运行以下命令：
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

在任何时候，您可以检查用户帐户需要具有以下命令封锁的状态：
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>使用 Office 365 PowerShell 阻止多个用户帐户访问权限

首先，创建一个文本文件，包含如下的每一行上的一个帐户：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
在下面的命令示例文本文件是 C:\My Documents\Accounts.txt。将此替换为您的文本文件的路径和文件名称。
    
若要阻止访问该文本文件中列出的帐户，请运行以下命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUser -UserPrincipalName $_.UserPrincipalName -BlockCredential $true
  ```
若要解除阻止该文本文件中列出的帐户，请运行以下命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUser -UserPrincipalName $_.UserPrincipalName -BlockCredential $false
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a>使用 Azure Active Directory V2 PowerShell 模块阻止访问用户帐户

若要使用 Azure Active Directory V2 PowerShell 模块中的 **New-AzureADUser** cmdlet，首先必须连接到自己的订阅。有关说明，请参阅[连接到 Azure Active Directory V2 PowerShell 模块](https://go.microsoft.com/fwlink/?linkid=842218)。
  
连接后，使用下列语法阻止单个用户帐户：
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> Set-AzureAD cmdlet 中的 -ObjectID 参数可接受帐户名（也称为“用户主体名称”）或帐户的对象 ID。 
  
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
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

本示例显示名为 Caleb 窗台的用户的用户帐户 UPN。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要阻止基于用户名的帐户，请使用下列命令：
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

在任何时候，您可以检查用户帐户需要具有以下命令封锁的状态：
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

要阻止访问的多个用户帐户，请创建一个文本文件，包含如下的每一行上的一个帐户名：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

在下面的命令示例文本文件是 C:\My Documents\Accounts.txt。将此替换为您的文本文件的路径和文件名称。
    
若要阻止访问该文本文件中列出的帐户，请运行以下命令：
    
```
Get-Content "C:\My Documents\Accounts.txt" | Set-AzureADUSer -ObjectID $_.ObjectID -AccountEnabled $true
```

若要解除阻止该文本文件中列出的帐户，请运行以下命令：
    
```
Get-Content "C:\My Documents\Accounts.txt" | Set-AzureADUSer -ObjectID $_.ObjectID -AccountEnabled $false
```

## <a name="see-also"></a>另请参阅
<a name="SeeAlso"> </a>

请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：
  
- [使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除和还原用户账户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 向用户帐户分配许可证](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除用户帐户的许可证](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [获取内容](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [一组 MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [新 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

