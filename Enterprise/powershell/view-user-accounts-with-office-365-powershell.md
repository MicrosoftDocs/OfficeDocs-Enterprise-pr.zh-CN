---
title: 查看用户帐户与 Office 365 PowerShell
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 摘要： 查看、 列表或显示您的用户帐户与 Office 365 PowerShell 中的各种方式。
ms.openlocfilehash: e95353602b96babe5c80f7d57462370636dd26fa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730317"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>查看用户帐户与 Office 365 PowerShell

**摘要：** 查看您的用户帐户与 Office 365 PowerShell 中的各种方式。
  
尽管可以使用 Office 365 管理中心以查看 Office 365 租户帐户，您还可以使用 Office 365 PowerShell 并执行某些操作不能在 Office 365 管理中心。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用 Azure Active Directory PowerShell 图模块

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
### <a name="view-all-accounts"></a>查看所有帐户

若要显示的用户帐户的完整列表，请运行以下命令：
  
```
Get-AzureADUser
```

您应看到类似于以下内容的信息：
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>查看特定帐户

若要显示特定的用户帐户，请填充中的用户帐户，也称为的用户主体名称 (UPN) 的登录帐户名称中删除"<"和">"字符，然后运行以下命令：
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

下面是一个示例：
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>查看特定帐户的其他属性值

默认情况下，**获取 AzureADUser** cmdlet 仅显示帐户的 ObjectID、 DisplayName 和 UserPrincipalName 的属性。

要更好选择性要显示的属性列表有关您可以使用**Select-object** cmdlet 与**Get AzureADUser** cmdlet 结合使用。若要合并的两个 cmdlet，我们使用"管道"字符"|"，它指示 Azure Active Directory PowerShell 图形执行一个命令的结果并将其发送到下一个命令。下面是显示的每个用户帐户的显示名称、 部门和 UsageLocation 的示例命令：
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

此命令指示 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 显示仅的用户帐户名称、 部门和使用率位置 （ **Select-object DisplayName、 部门、 UsageLocation** ）。
  
要查看所有用户帐户的属性，用于**Select-object** cmdlet 和通配符 （*） 以显示所有这些特定的用户帐户。下面是一个示例：
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

又如，您可以检查使用以下命令的特定用户帐户启用的状态：
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>查看基于公共属性某些帐户

要更好选择性有关列表帐户显示，您可以使用**Where-object** cmdlet 与**Get AzureADUser** cmdlet 结合使用。若要合并的两个 cmdlet，我们使用"管道"字符"|"，它指示 Azure Active Directory PowerShell 图形执行一个命令的结果并将其发送到下一个命令。下面是显示未指定的使用率位置这些用户帐户的示例命令：
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

此命令指示图形到 Azure Active Directory PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 查找所有未指定的使用率位置的用户帐户 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括号内命令指示 Office 365 PowerShell 中仅查找的帐户在其中 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
与用户帐户关联的许多属性之一的**UsageLocation**属性。要查看所有用户帐户的属性，用于**Select-object** cmdlet 和通配符 （*） 以显示所有这些特定的用户帐户。下面是一个示例：
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

例如，从此列表中，**市/县**是的用户帐户属性的名称。这意味着您可以使用以下命令列出所有的生活中伦敦的用户的用户帐户：
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  以下示例中所示**Where-object** cmdlet 的语法**Where-object {$\_。**[用户帐户属性名][比较运算符][值]**}**。 > [比较运算符] 是 **-eq**等同于的、 不等于为 **-ne** 、 **-lt**小于， **-gt**大于、 和其他人。 [值] 通常是字符串 （的字母、 数字和其他字符序列）、 数字值或 **$Null**的未指定 > 详细信息，请参阅[Where-object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) 。
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用 Windows PowerShell 的 Microsoft Azure Active Directory 模块

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

### <a name="view-all-accounts"></a>查看所有帐户

若要显示的用户帐户的完整列表，请运行以下命令：
  
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

**Get-msoluser** cmdlet 还具有一套参数筛选的用户帐户显示组。例如，对于未经授权的用户 （已添加到 Office 365 但尚未尚未被许可使用的任何服务的用户） 的列表中，运行此命令。
  
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

有关其他参数，以筛选显示一组的用户帐户显示，请参阅[Get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))。
  

### <a name="view-a-specific-account"></a>查看特定帐户

若要显示特定的用户帐户，请填充的用户帐户，也称为的用户主体名称 (UPN) 的用户帐户的登录名称中删除"<"和">"字符，然后运行以下命令：
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>查看基于公共属性某些帐户

要更好选择性的帐户，若要显示，列表有关您可以使用**Where-object** cmdlet 与**Get-msoluser** cmdlet 结合使用。若要合并的两个 cmdlet，我们使用"管道"字符"|"，它指示 Office 365 PowerShell 中执行一个命令的结果并将其发送到下一个命令。下面是显示未指定的使用率位置这些用户帐户的示例命令：
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

此命令指示 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 查找所有未指定的使用率位置的用户帐户 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括号内命令指示 Office 365 PowerShell 中仅查找的帐户在其中 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
您应看到类似于以下内容的信息：
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

与用户帐户关联的许多属性之一的**UsageLocation**属性。要查看所有用户帐户的属性，用于**Select-object** cmdlet 和通配符 （*） 以显示所有这些特定的用户帐户。下面是一个示例：
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

例如，从此列表中，**市/县**是的用户帐户属性的名称。这意味着您可以使用以下命令列出所有的生活中伦敦的用户的用户帐户：
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  以下示例中所示**Where-object** cmdlet 的语法**Where-object {$\_。**[用户帐户属性名][比较运算符][值]**}**. [比较运算符] 是 **-eq**等同于的、 不等于为 **-ne** 、 **-lt**小于， **-gt**大于、 和其他人。 [值] 是通常字符串 （的字母、 数字和其他字符序列）、 数字值或 **$Null**未指定。有关详细信息，请参阅[Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx) 。
  
您可以检查阻止的状态的用户帐户，使用以下命令：
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>查看其他属性值的帐户

默认情况下**Get-msoluser** cmdlet 显示三个用户帐户的属性：
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
如果您需要其他属性，如适用于用户的部门和国家/地区其中用户使用 Office 365 服务，您可以运行**Get-msoluser**结合**Select-object** cmdlet，以指定用户帐户的列表属性。下面是一个示例：
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

此命令指示 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 显示仅的用户帐户名称、 部门和使用率位置 （ **Select-object DisplayName、 部门、 UsageLocation** ）。
    
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
Scott Wallace           Operations
```

**Select-object** cmdlet，可以选择您希望显示的命令的属性。若要查看所有用户帐户的属性，使用通配符 （*） 显示所有这些特定的用户帐户。下面是一个示例：
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

要更好的帐户，若要显示，列表有关选择性您还可以使用**Where-object** cmdlet。下面是显示未指定的使用率位置这些用户帐户的示例命令：
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

此命令指示 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 查找所有未指定的使用率位置的用户帐户 ( **Where-object {$\_。UsageLocation-eq $Null}** ) 并将生成的信息发送到下一个命令 ( **|** )。该命令的大括号内指示 Office 365 PowerShell 中仅查找的帐户在其中 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
- 显示仅的用户帐户名称、 部门和使用率位置 （ **Select-object DisplayName、 部门、 UsageLocation** ）。
    
您应看到类似于以下内容的信息：
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

如果您正在使用目录同步来创建和管理 Office 365 用户，则可以显示 Office 365 用户已从已计划的本地帐户。以下假定 Azure AD 连接配置为使用默认源定位标记的 ObjectGUID (有关配置源定位的详细信息，请参阅[Azure AD 连接： 设计概念](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) 并假定有 powershell 的 Active Directory 模块已安装 （请参阅[RSAT 工具](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)）：

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

