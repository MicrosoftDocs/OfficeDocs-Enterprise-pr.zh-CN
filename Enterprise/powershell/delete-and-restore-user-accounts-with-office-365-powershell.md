---
title: "使用 Office 365 PowerShell 删除和还原用户账户"
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "了解如何使用 Office 365 PowerShell 删除和还原 Office 365 用户帐户。"
ms.openlocfilehash: fc72d51532780d2ddaaff20ecc6aebab06a001f4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 删除和还原用户账户

**摘要：**了解如何使用 Office 365 PowerShell 删除和还原 Office 365 用户帐户。
  
当您使用 Office 365 PowerShell 删除用户帐户时，该帐户不会被永久删除。您可以在 30 天内还原已删除的用户帐户。
  
## <a name="before-you-begin"></a>准备工作

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>使用 Office 365 PowerShell 阻止对单个用户帐户的访问
<a name="ShortVersion"> </a>

若要删除一个用户帐户，请使用下面的语法：
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

本示例删除用户帐户 BelindaN@litwareinc.com。
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

若要在 30 天的宽限期内还原已删除的用户帐户，请使用下面的语法：
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

本示例还原已删除的帐户 BelindaN@litwareinc.com。
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **注意：**
  
- 若要查看可以还原的已删除用户的列表，请运行以下命令：
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- 如果用户帐户的初始用户主体名称已被另一个帐户使用，那么在还原用户帐户时，请使用  _NewUserPrincipalName_ 参数而不是 _UserPrincipalName_ 来指定一个不同的用户主体名称。
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>使用 Azure Active Directory V2 PowerShell 模块删除用户帐户
<a name="ShortVersion"> </a>

若要使用 Azure Active Directory V2 PowerShell 模块中的 **Remove-AzureADUser** cmdlet，必须先连接到订阅。有关说明，请参阅[使用 Azure Active Directory V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。
  
连接后，使用下列语法删除单个用户帐户：
  
```
Remove-AzureADUser -ObjectID <Account>
```

本示例将删除用户帐户 fabricec@litwareinc.com。
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **Remove-AzureAD** cmdlet 中的 **-ObjectID** 参数可接受帐户名（也称为"用户主体名称"）或帐户的对象 ID。
  
若要显示基于用户名的帐户名称，请使用下列命令：
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本示例显示名为 Caleb Sills 的用户的帐户名称。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要删除基于用户名的帐户，请使用下列命令：
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a>另请参阅
<a name="SeeAlso"> </a>

若要了解如何使用 Office 365 PowerShell 管理用户，请参阅下面这些附加主题：
  
- [使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 冻结用户账户](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 向用户帐户分配许可证](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除用户帐户的许可证](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [Restore-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

