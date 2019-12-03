---
title: 查看用户帐户与 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 摘要：使用 Office 365 PowerShell 以多种方式查看、列出或显示您的用户帐户。
ms.openlocfilehash: 28e6ec6936040c6bb84a49e354ae1ee5e9e9de44
ms.sourcegitcommit: 460c722d63e7e604ef0a57ec18fa7900fa6a4157
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "39655834"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>查看用户帐户与 Office 365 PowerShell

虽然您可以使用 Microsoft 365 管理中心来查看 Office 365 租户的帐户，但您也可以使用 Office 365 PowerShell，并执行管理中心无法执行的某些操作。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
### <a name="view-all-accounts"></a>查看所有帐户

若要显示用户帐户的完整列表，请运行以下命令：
  
```powershell
Get-AzureADUser
```

您应看到类似于以下内容的信息：
  
```powershell
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

若要显示特定的用户帐户，请填写用户帐户的登录帐户名（也称为 "用户主体名称（UPN）"），删除 "<" 和 ">" 字符，然后运行以下命令：
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

如以下示例所示：
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>查看特定帐户的其他属性值

默认情况下， **AzureADUser** cmdlet 仅显示帐户的 ObjectID、DisplayName 和 UserPrincipalName 属性。

若要更好地选择要显示的属性列表，可以结合使用**Select 对象**Cmdlet 和**AzureADUser** cmdlet。 若要组合这两个 cmdlet，我们使用 "管道" 字符 "|"，它通知 Azure Active Directory PowerShell 以获取一个命令的结果，并将其发送到下一个命令。 下面是一个显示每个用户帐户的 DisplayName、部门和 UsageLocation 的示例命令：
  
```powershell
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

此命令指示 Office 365 PowerShell：
  
- 获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 仅显示用户帐户名称、部门和使用位置（**选择-对象 DisplayName、部门、UsageLocation** ）。
  
若要查看用户帐户的所有属性，请使用**Select-Object** cmdlet 和通配符（*）为特定用户帐户显示所有属性。 如以下示例所示：
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

作为另一个示例，您可以使用以下命令检查特定用户帐户的启用状态：
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>根据通用属性查看一些帐户

若要更好地选择要显示的帐户列表，可以结合使用**AzureADUser** Cmdlet 与**Where 对象**cmdlet。 若要组合这两个 cmdlet，我们使用 "管道" 字符 "|"，它通知 Azure Active Directory PowerShell 以获取一个命令的结果，并将其发送到下一个命令。 下面是一个示例命令，它显示了未指定使用地点的用户帐户：
  
```powershell
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

此命令将 Azure Active Directory PowerShell for Graph 指示为：
  
- 获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 查找所有具有未指定使用位置（**其中-对象为\_{$）的用户帐户。UsageLocation-eq $Null}** ）。 在大括号内，该命令指示 Office 365 PowerShell 仅查找 UsageLocation 用户帐户属性（ ** $ \_。** 未指定 UsageLocation）（ **-eq $Null** ）。
    
**UsageLocation**属性只是与用户帐户关联的很多属性中的一个。 若要查看用户帐户的所有属性，请使用**Select-Object** cmdlet 和通配符（*）为特定用户帐户显示所有属性。 如以下示例所示：
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

例如，在此列表中， **City**是用户帐户属性的名称。 这意味着您可以使用以下命令列出居住在伦敦的用户的所有用户帐户：
  
```powershell
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  在这些示例中显示的 " **Where 对象**" cmdlet 的语法为 **-object {$\_。** [用户帐户属性名称][比较运算符]增值 **}**. > [比较运算符] 为 **-eq** for equals， **-ne**不等于， **-lt**表示小于， **-gt**表示大于，其他。  [value] 通常是一个字符串（字母、数字和其他字符的序列）、数值或未指定的 **$Null**> 请参阅[Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1)获取详细信息。
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

### <a name="view-all-accounts"></a>查看所有帐户

若要显示用户帐户的完整列表，请运行以下命令：
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
>

您应看到类似于以下内容的信息：
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get-MsolUser** cmdlet 也有一组参数可用于筛选显示的用户帐户组。 例如，对于未授权用户的列表（已添加到 Office 365 但尚未许可使用任何服务的用户），请运行此命令。
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

您应看到类似于以下内容的信息：
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

有关筛选显示显示的用户帐户集的其他参数的详细信息，请参阅[get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))。
  

### <a name="view-a-specific-account"></a>查看特定帐户

若要显示特定的用户帐户，请填写用户帐户的用户帐户的登录名（也称为 "用户主体名称（UPN）"），删除 "<" 和 ">" 字符，然后运行以下命令：
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>根据通用属性查看一些帐户

若要更好地选择要显示的帐户列表，可以结合使用**get-msoluser** Cmdlet 与**Where 对象**cmdlet。 若要组合这两个 cmdlet，我们使用 "管道" 字符 "|"，它会告诉 Office 365 PowerShell 获取一个命令的结果，并将其发送到下一个命令。 下面是一个示例命令，它显示了未指定使用地点的用户帐户：
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

此命令指示 Office 365 PowerShell：
  
- 获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 查找所有具有未指定使用位置（**其中-对象为\_{$）的用户帐户。UsageLocation-eq $Null}** ）。 在大括号内，该命令指示 Office 365 PowerShell 仅查找 UsageLocation 用户帐户属性（ ** $ \_。** 未指定 UsageLocation）（ **-eq $Null** ）。
    
您应看到类似于以下内容的信息：
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

**UsageLocation**属性只是与用户帐户关联的很多属性中的一个。 若要查看用户帐户的所有属性，请使用**Select-Object** cmdlet 和通配符（*）为特定用户帐户显示所有属性。 如以下示例所示：
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

例如，在此列表中， **City**是用户帐户属性的名称。 这意味着您可以使用以下命令列出居住在伦敦的用户的所有用户帐户：
  
```powershell
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  在这些示例中显示的 " **Where 对象**" cmdlet 的语法为 **-object {$\_。** [用户帐户属性名称][比较运算符]增值 **}**.  [比较运算符] 为 **-eq** ，等于， **-ne**表示不等于， **-lt**表示小于， **-gt**表示大于，其他。  [value] 通常是一个字符串（一系列字母、数字和其他字符）、一个数值或未指定 **$Null** 。 有关详细信息，请参阅[Where-Object](https://technet.microsoft.com/library/hh849715.aspx) 。
  
您可以使用以下命令检查用户帐户的阻止状态：
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>查看帐户的其他属性值

默认情况下， **get-msoluser** cmdlet 显示用户帐户的三个属性：
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
如果需要其他属性（如用户所使用的部门和用户使用 Office 365 服务的国家/地区） **，则可以**同时运行**get-msoluser** cmdlet，以指定用户帐户属性列表。 如以下示例所示：
  
```powershell
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

此命令指示 Office 365 PowerShell：
  
- 获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 仅显示用户帐户名称、部门和使用位置（**选择-对象 DisplayName、部门、UsageLocation** ）。
    
您应看到类似于以下内容的信息：
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

通过**选择-对象**cmdlet，您可以选取您想要命令显示的属性并选择这些属性。 若要查看用户帐户的所有属性，请使用通配符（*）为特定用户帐户显示所有属性。 如以下示例所示：
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

若要更好地选择要显示的帐户列表，您还可以使用**对象**之间的 cmdlet。 下面是一个示例命令，它显示了未指定使用地点的用户帐户：
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

此命令指示 Office 365 PowerShell：
  
- 获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 查找所有具有未指定使用位置（**其中-对象为\_{$）的用户帐户。UsageLocation-eq $Null}** ）并将生成的信息发送到下一个命令**|** （）。 在大括号内，该命令指示 Office 365 PowerShell 仅查找 UsageLocation 用户帐户属性（ ** $ \_位于其中）的帐户集。** 未指定 UsageLocation）（ **-eq $Null** ）。
    
- 仅显示用户帐户名称、部门和使用位置（**选择-对象 DisplayName、部门、UsageLocation** ）。
    
您应看到类似于以下内容的信息：
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

如果使用目录同步来创建和管理 Office 365 用户，则可以显示计划了 Office 365 用户的本地帐户。 以下示例假定 Azure AD Connect 已配置为使用 ObjectGUID 的默认源锚点（有关配置源锚点的详细信息，请参阅[AZURE AD Connect：设计概念](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)），并假定已安装 Powershell 的 Active Directory 模块（请参阅[RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)）：

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

