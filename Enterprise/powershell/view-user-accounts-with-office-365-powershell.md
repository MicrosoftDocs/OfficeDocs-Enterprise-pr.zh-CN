---
title: "查看用户帐户与 Office 365 PowerShell"
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
- LIL_Placement
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "摘要： 视图、 列表或显示您的用户帐户与 Office 365 PowerShell 的各种方式。"
ms.openlocfilehash: b27f9045d26d4dabd3ada70766491f722d822a91
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="view-user-accounts-with-office-365-powershell"></a>查看用户帐户与 Office 365 PowerShell

 **摘要：**视图、 列表或显示您的用户帐户与 Office 365 PowerShell 的各种方式。
  
尽管可以使用 Office 365 管理中心为 Office 365 租户查看帐户，您还可以使用 Office 365 PowerShell 并做一些 Office 365 管理中心不能。
  
## <a name="before-you-begin"></a>开始之前

若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
## <a name="display-office-365-user-account-information"></a>显示 Office 365 用户帐户信息

若要显示的用户帐户的完整列表，请在 Office 365 PowerShell 命令提示符或 PowerShell 集成脚本环境 (ISE) 运行此命令。
  
```
Get-MsolUser
```

您应看到类似于以下内容的信息：
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**获得 MsolUser** cmdlet 还具有一组参数来筛选显示的用户帐户的组。例如，列表中未授权用户 （用户已被添加到 Office 365，但还没有被授权使用任何服务），对运行此命令。
  
```
Get-MsolUser -UnlicensedUsersOnly
```

您应看到类似于以下内容的信息：
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

有关其他参数以筛选显示的详细信息的显示，用户帐户组请参阅[获取 MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) 。
  
要更好选择列表中的帐户显示，可以使用**对象的位置的**cmdlet **Get MsolUser** cmdlet 的结合。若要合并两个 cmdlet，我们使用"管道"字符"|"，据 Office 365 PowerShell 执行一条命令的结果，并将其发送到下一个命令。下面是一个示例命令，显示具有未指定的使用位置的用户帐户：
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 查找所有具有未指定的使用位置的用户帐户 (**位置对象 {$\_。UsageLocation-eq $Null}** )。在大括号中，该命令指示 Office 365 PowerShell 若要仅查找的帐户的 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
您应看到类似于以下内容的信息：
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

**UsageLocation**属性是与用户帐户相关联的多个属性之一。要查看所有用户帐户的属性，用于**选择对象**cmdlet 和通配符 （*） 以显示所有这些特定的用户帐户。下面是一个示例：
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

例如，从该列表中，**城市**是用户帐户属性的名称。这意味着您可以使用以下命令列出所有居住在伦敦的用户的用户帐户：
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  在这些示例中所示**的位置对象**cmdlet 的语法是**对象的位置的 {$\_。**[用户帐户的属性名称][比较运算符][值]**}**。 > [比较运算符] 是**的 eq**的等号、 **-ne**的不等于、 小于、 大于号、 **-gt**和其他人**的长期**> [值] 通常是一个字符串 （一系列字母、 数字和其他字符）未指定的数值或为**$Null** > 的详细信息，请参阅[位置对象](https://technet.microsoft.com/en-us/library/hh849715.aspx)。
  
您可以检查用户帐户需要具有以下命令封锁的状态：
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a>选择要显示的用户帐户属性

默认情况下[获取 MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet 将显示三个用户帐户的属性：
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
如果您需要其他属性，例如在用户所处理的部门和国家/地区，用户使用 Office 365 提供服务，您可以运行**Get MsolUser**结合**选择对象**用于指定用户帐户的列表属性。下面是一个示例：
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 显示仅用户帐户名称、 部门和使用位置 （**选择对象的显示名称、 部门、 UsageLocation** ）。
    
您应看到类似于以下内容的信息：
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

**选择对象**cmdlet 允许您选取要显示命令的属性。要查看所有用户帐户的属性，使用通配符 （*） 显示所有这些特定的用户帐户。下面是一个示例：
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

要更好选择列表中的帐户显示，您还可以使用**对象的位置的**cmdlet。下面是一个示例命令，显示具有未指定的使用位置的用户帐户：
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 查找所有具有未指定的使用位置的用户帐户 (**位置对象 {$\_。UsageLocation-eq $Null}** ) 并将得到的信息发送到下一个命令 ( **|** )。在大括号中，该命令指示 Office 365 PowerShell 若要仅查找的帐户的 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
- 显示仅用户帐户名称、 部门和使用位置 （**选择对象的显示名称、 部门、 UsageLocation** ）。
    
您应看到类似于以下内容的信息：
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a>使用 Azure 活动目录 V2 PowerShell 模块可以显示用户帐户

若要显示与活动目录 V2 PowerShell 的 Azure 模块的用户帐户的属性，使用[Get AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet。但首先，您必须连接到您的订购。有关说明，请参阅[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。
  
### <a name="display-office-365-user-account-information"></a>显示 Office 365 用户帐户信息

若要显示的用户帐户的完整列表，请在 Office 365 PowerShell 命令提示符或 PowerShell 集成脚本环境 (ISE) 运行此命令。
  
```
Get-AzureADUser
```

默认情况下**获取 AzureADUser** cmdlet 将显示三个用户帐户的属性：
  
- 对象 Id
    
- DisplayName
    
- UserPrincipalName
    
要更好选择列表中的帐户显示，可以使用**对象的位置的**cmdlet **Get AzureADUser** cmdlet 的结合。若要合并两个 cmdlet，我们使用"管道"字符"|"，据 Office 365 PowerShell 执行一条命令的结果，并将其发送到下一个命令。下面是一个示例命令，显示具有未指定的使用位置的用户帐户：
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 查找所有具有未指定的使用位置的用户帐户 (**位置对象 {$\_。UsageLocation-eq $Null}** )。在大括号中，该命令指示 Office 365 PowerShell 若要仅查找的帐户的 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
**UsageLocation**属性是与用户帐户相关联的多个属性之一。要查看所有用户帐户的属性，用于**选择对象**cmdlet 和通配符 （*） 以显示所有这些特定的用户帐户，一页一次 （**更多**）。下面是一个示例：
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

例如，**城市**是用户帐户属性的名称。这意味着您可以使用以下命令列出所有居住在伦敦的用户的用户帐户：
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  在这些示例中所示**的位置对象**cmdlet 的语法是**对象的位置的 {$\_。**[用户帐户的属性名称][比较运算符][值]**}**。 > [比较运算符] 是**的 eq**的等号、 **-ne**的不等于、 小于、 大于号、 **-gt**和其他人**的长期**> [值] 通常是一个字符串 （一系列字母、 数字和其他字符）未指定的数值或为**$Null** > 的详细信息，请参阅[位置对象](https://technet.microsoft.com/en-us/library/hh849715.aspx)。
  
### <a name="select-the-user-account-properties-to-display"></a>选择要显示的用户帐户属性

默认情况下**获取 AzureADUser** cmdlet 显示对象 Id、 显示名称，以及范围内的用户帐户属性。如果您需要其他属性，例如在用户所处理的部门和国家/地区，用户使用 Office 365 提供服务，您可以运行**Get AzureADUser**结合**选择对象**用于指定用户的列表帐户属性。下面是一个示例：
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 显示仅用户帐户名称、 部门和使用位置 （**选择对象的显示名称、 部门、 UsageLocation** ）。
    
要更好选择列表中的帐户显示，您还可以使用**对象的位置的**cmdlet。下面是一个示例命令，显示具有未指定的使用位置的用户帐户：
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 查找所有具有未指定的使用位置的用户帐户 (**位置对象 {$\_。UsageLocation-eq $Null}** ) 并将得到的信息发送到下一个命令 ( **|** )。在大括号中，该命令指示 Office 365 PowerShell 若要仅查找的帐户的 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
- 显示仅用户帐户名称、 部门和使用位置 （**选择对象的显示名称、 部门、 UsageLocation** ）。
    
## <a name="new-to-office-365"></a>刚开始接触 Office 365？

||
|:-----|
|![LinkedIn 学习的短图标](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 提供指向新建？**        [Office 365 管理员和 IT 专业人员使用](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5)，LinkedIn 学习者发现免费视频课程。 |
   
## <a name="see-also"></a>See also

#### 

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

