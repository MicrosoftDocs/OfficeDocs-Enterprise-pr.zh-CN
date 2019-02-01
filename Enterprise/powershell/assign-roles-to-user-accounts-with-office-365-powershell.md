---
title: 将角色分配给用户帐户与 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/31/2019
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
description: 摘要： 使用 Office 365 PowerShell，可以将角色分配给用户帐户。
ms.openlocfilehash: 702c7358ccca9bb36bd106d742b5c454283ee8b4
ms.sourcegitcommit: d0c870c7a487eda48b11f649b30e4818fd5608aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2019
ms.locfileid: "29690433"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>将角色分配给用户帐户与 Office 365 PowerShell

您可以快速、 方便地向分配角色使用 Office 365 PowerShell 中的用户帐户。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)使用全局管理员帐户。
  
接下来，确定要向角色添加用户帐户的登录名 (示例： fredsm@contoso.com)。这也称为是用户主体名称 (UPN)。

接下来，确定角色的名称。使用此命令列出您可以使用 PowerShell 分配的角色。

````
Get-AzureADDirectoryRole
````

接下来，填写的登录和角色名称，然后运行以下命令。
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

下面是一个已完成的命令集的示例：
  
```
$userName="belindan@contoso.com"
$roleName="Lync Service Administrator"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

若要显示的特定角色的用户名称列表，请使用以下命令。

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)使用全局管理员帐户。
  
### <a name="for-a-single-role-change"></a>单个角色更改

确定以下信息：
  
- 您想要配置用户帐户。
    
    若要指定的用户帐户，您必须确定其显示名称。要获取的完整列表帐户，请使用以下命令：
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令列出的用户帐户，按显示名称，一次一屏的显示名称。可以使用**其中**cmdlet 来筛选一较小的列表。下面是一个示例：
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令将列出其显示名称开头"John"的用户帐户。
    
- 您要分配的角色。
    
    要显示可用的角色，您可以分配给用户帐户的列表，请使用以下命令：
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

一旦您已确定的帐户的显示名称和角色的名称，使用这些命令将角色分配给该帐户：
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

复制命令，并将它们粘贴到记事本。**$DispName**和 **$roleName**变量的值替换的说明文本、 删除\<和 > 字符，并将保留为引号。复制已修改的行并将它们粘贴到您的 Windows Azure Active Directory 模块用于 Windows PowerShell 窗口来运行它们。或者，也可以使用 Windows PowerShell 集成脚本环境 (ISE)。
  
下面是一个已完成的命令集的示例：
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a>多个角色更改

确定以下信息：
  
- 哪些用户帐户想要配置。
    
    若要指定的用户帐户，您必须确定其显示名称。要获取列表帐户，请使用以下命令：
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令将列出所有用户帐户，按显示名称，一次一个屏幕显示名称。可以使用**其中**cmdlet 来筛选一较小的列表。下面是一个示例：
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令将列出其显示名称开头"John"的用户帐户。
    
- 要分配给每个用户帐户的角色。
    
    要显示可用的角色，您可以分配给用户帐户的列表，请使用以下命令：
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

接下来，创建具有显示名称和角色的以逗号分隔值 (CSV) 文本文件名称字段。下面是一个示例：
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

接下来，填写 CSV 文件的位置，然后在 PowerShell 命令提示符处运行生成命令。
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>另请参阅

- [使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
