---
title: 将角色分配给用户帐户与 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: '摘要: 使用 Office 365 PowerShell 向用户帐户分配角色。'
ms.openlocfilehash: 78f2e08df6d46588b93dc217d0e16b7c3a350a88
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491988"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>将角色分配给用户帐户与 Office 365 PowerShell

您可以使用 Office 365 PowerShell 快速而轻松地向用户帐户分配角色。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先, 使用全局管理员帐户[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
接下来, 确定要添加到角色的用户帐户的登录名 (例如: fredsm@contoso.com)。 这也称为用户主体名称 (UPN)。

接下来, 确定角色的名称。 [在 Azure Active Directory 中使用此管理员角色权限列表](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)。

>[!Note]
>请注意本文中的注释。 对于 Azure AD PowerShell, 某些角色名称不同。 例如, Microsoft 365 管理中心中的 "sharepoint 管理员" 角色为 Azure AD PowerShell 命名为 "sharepoint 服务管理员"。
>

接下来, 填写登录名和角色名称, 并运行这些命令。
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

下面的示例展示了已完成的命令集:
  
```
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

若要显示特定角色的用户名列表, 请使用这些命令。

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块

首先, 使用全局管理员帐户[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。
  
### <a name="for-a-single-role-change"></a>对于单个角色更改

确定下列事项：
  
- 要配置的用户帐户。
    
    若要指定用户帐户, 必须确定其显示名称。 若要获取完整的列表帐户, 请使用以下命令:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令将列出用户帐户的显示名称, 按显示名称排序, 一次显示一个屏幕。 您可以使用**Where** cmdlet 将列表筛选为一个较小的集。 如以下示例所示：
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令仅列出其显示名称以 "John" 开头的用户帐户。
    
- 要分配的角色。
    
    若要显示可分配给用户帐户的可用角色的列表, 请使用以下命令:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

确定帐户的显示名称和角色的名称后, 请使用以下命令将角色分配给帐户:
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

复制命令并将其粘贴到记事本中。 对于 **$dispName**和 **$roleName**变量, 将说明文本替换为它们的值, 删除\<和 > 字符, 并保留引号。 复制修改过的行并将其粘贴到 windows PowerShell 的 windows Azure Active Directory 模块中, 以运行它们。 或者, 也可以使用 Windows PowerShell 集成脚本环境 (ISE)。
  
下面的示例展示了已完成的命令集:
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a>对于多个角色更改

确定下列事项：
  
- 要配置的用户帐户。
    
    若要指定用户帐户, 必须确定其显示名称。 若要获取列表帐户, 请使用以下命令:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令将列出所有用户帐户的显示名称, 按显示名称排序, 一次显示一个屏幕。 您可以使用**Where** cmdlet 将列表筛选为一个较小的集。 如以下示例所示：
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令仅列出其显示名称以 "John" 开头的用户帐户。
    
- 要分配给每个用户帐户的角色。
    
    若要显示可分配给用户帐户的可用角色的列表, 请使用以下命令:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

接下来, 创建一个包含 "DisplayName" 和 "角色名称" 字段的逗号分隔值 (CSV) 文本文件。 如以下示例所示：
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

接下来, 填写 CSV 文件的位置, 并在 PowerShell 命令提示符处运行生成的命令。
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>另请参阅

- [使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
