---
title: 将角色分配给用户帐户与 Office 365 PowerShell
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 摘要： 使用 Office 365 PowerShell 和添加 MsolRoleMember cmdlet 将角色分配给用户帐户。
ms.openlocfilehash: 2af4409020cc4a4e3dd6ff3b8bfcf5f1138f26cd
ms.sourcegitcommit: 3b474e0b9f0c12bb02f8439fb42b80c2f4798ce1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>将角色分配给用户帐户与 Office 365 PowerShell

 **摘要：**使用 Office 365 PowerShell 和**添加 MsolRoleMember** cmdlet 将角色分配给用户帐户。
  
您可以快速而轻松地分配角色通过 Office 365 PowerShell 标识的用户帐户显示名称和角色名称的用户帐户。
  
## <a name="before-you-begin"></a>开始之前

本主题中的过程要求您连接到 Office 365 PowerShell 使用全局管理员帐户。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
## <a name="for-a-single-role-change"></a>单个角色的变化

确定下列因素：
  
- 您想要配置的用户帐户。
    
    若要指定用户帐户，您必须确定其显示名称。要获取完整列表帐户，请使用以下命令：
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令将列出您的用户帐户，按显示名称，一次一屏的显示名称。您可以将列表筛选为一个较小集使用**的**cmdlet。下面是一个示例：
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令将列出为其显示名称的开头是"约翰"的用户帐户。
    
- 要分配的角色。
    
    若要显示可用的角色，您可以分配给用户帐户的列表，请使用以下命令：
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

一旦确定了该帐户的显示名称和角色的名称，可以使用这些命令来为该帐户分配角色：
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

复制命令并将其粘贴到记事本。**$DispName**和 **$roleName**变量的值替换说明文本，删除\<和 > 字符，并将引号。将已修改的行复制并粘贴到您的 Windows Azure 活动目录模块用于 Windows PowerShell 窗口来运行它们。或者，您可以使用 Windows PowerShell 集成脚本环境 (ISE)。
  
这里是完成的命令集的示例：
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a>为多个角色更改

确定下列因素：
  
- 您想要配置的哪个用户帐户。
    
    若要指定用户帐户，您必须确定其显示名称。要获取列表的帐户，请使用以下命令：
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令将列出所有用户帐户，按显示名称，一次一屏的显示名称。您可以将列表筛选为一个较小集使用**的**cmdlet。下面是一个示例：
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令将列出为其显示名称的开头是"约翰"的用户帐户。
    
- 您想要分配给每个用户帐户所属的角色。
    
    若要显示可用的角色，您可以分配给用户帐户的列表，请使用以下命令：
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

接下来，创建以逗号分隔值 (CSV) 文本文件，其中包含显示名称和角色名称的字段。下面是一个示例：
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

下一步，填写该 CSV 文件的位置，PowerShell 命令提示符处运行生成的命令。
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>另请参阅

- [使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
- [添加 MsolRoleMember](https://msdn.microsoft.com/library/dn194120.aspx)
