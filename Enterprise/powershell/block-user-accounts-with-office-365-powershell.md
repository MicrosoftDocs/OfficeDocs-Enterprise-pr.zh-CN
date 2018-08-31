---
title: 使用 Office 365 PowerShell 冻结用户账户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
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
ms.openlocfilehash: 748d24f95f9dca651158dae2fe15e9c655eb021e
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915407"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 冻结用户账户

**摘要：** 介绍如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 帐户的访问。
  
阻止对 Office 365 帐户访问可防止任何人使用的帐户登录和访问的服务和 Office 365 组织中的数据。当您阻止访问帐户时，用户将收到以下错误消息，在尝试登录时：
  
![阻止的 Office 365 帐户。](media/o365-powershell-account-blocked.png)
  
Office 365 PowerShell 中可用于阻止对单个访问和多个用户帐户。
  
## <a name="before-you-begin"></a>准备工作

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 当您阻止用户帐户时，可能需要长达 24 小时才能对所有用户的设备和客户端的影响。
    
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

在任何时候，您可以检查阻止的状态的用户帐户，使用以下命令：
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>使用 Office 365 PowerShell 阻止访问多个用户帐户

首先，创建一个文本文件，包含如下所示的每一行上的一个帐户：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
以下命令，在示例文本文件是 C:\My Documents\Accounts.txt。将此替换为文本文件的路径和文件名称。
    
若要阻止访问该文本文件中列出的帐户，请运行以下命令：
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
若要解除阻止该文本文件中列出的帐户，请运行以下命令：
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
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

本示例显示名为 Caleb Sills 的用户的用户帐户 UPN。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要阻止基于用户名的帐户，请使用下列命令：
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

在任何时候，您可以检查阻止的状态的用户帐户，使用以下命令：
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

若要阻止对多个用户帐户的访问，请创建包含一个帐户名，如下所示的每一行上一个文本文件：
    
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

## <a name="see-also"></a>另请参阅

请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：
  
- [使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除和还原用户账户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 向用户帐户分配许可证](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除用户帐户的许可证](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [获取内容](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [Set-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

