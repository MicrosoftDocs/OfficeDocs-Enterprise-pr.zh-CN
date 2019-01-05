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
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="421b4-103">查看用户帐户与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="421b4-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="421b4-104">**摘要：** 查看您的用户帐户与 Office 365 PowerShell 中的各种方式。</span><span class="sxs-lookup"><span data-stu-id="421b4-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="421b4-105">尽管可以使用 Office 365 管理中心以查看 Office 365 租户帐户，您还可以使用 Office 365 PowerShell 并执行某些操作不能在 Office 365 管理中心。</span><span class="sxs-lookup"><span data-stu-id="421b4-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="421b4-106">使用 Azure Active Directory PowerShell 图模块</span><span class="sxs-lookup"><span data-stu-id="421b4-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="421b4-107">第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="421b4-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="421b4-108">查看所有帐户</span><span class="sxs-lookup"><span data-stu-id="421b4-108">View all accounts</span></span>

<span data-ttu-id="421b4-109">若要显示的用户帐户的完整列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="421b4-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="421b4-110">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="421b4-110">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="421b4-111">查看特定帐户</span><span class="sxs-lookup"><span data-stu-id="421b4-111">View a specific account</span></span>

<span data-ttu-id="421b4-112">若要显示特定的用户帐户，请填充中的用户帐户，也称为的用户主体名称 (UPN) 的登录帐户名称中删除"<"和">"字符，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="421b4-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="421b4-113">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="421b4-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="421b4-114">查看特定帐户的其他属性值</span><span class="sxs-lookup"><span data-stu-id="421b4-114">View additional property values for a specific account</span></span>

<span data-ttu-id="421b4-115">默认情况下，**获取 AzureADUser** cmdlet 仅显示帐户的 ObjectID、 DisplayName 和 UserPrincipalName 的属性。</span><span class="sxs-lookup"><span data-stu-id="421b4-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="421b4-p101">要更好选择性要显示的属性列表有关您可以使用**Select-object** cmdlet 与**Get AzureADUser** cmdlet 结合使用。若要合并的两个 cmdlet，我们使用"管道"字符"|"，它指示 Azure Active Directory PowerShell 图形执行一个命令的结果并将其发送到下一个命令。下面是显示的每个用户帐户的显示名称、 部门和 UsageLocation 的示例命令：</span><span class="sxs-lookup"><span data-stu-id="421b4-p101">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="421b4-119">此命令指示 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="421b4-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="421b4-120">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="421b4-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="421b4-121">显示仅的用户帐户名称、 部门和使用率位置 （ **Select-object DisplayName、 部门、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="421b4-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="421b4-p102">要查看所有用户帐户的属性，用于**Select-object** cmdlet 和通配符 （\*） 以显示所有这些特定的用户帐户。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="421b4-p102">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="421b4-124">又如，您可以检查使用以下命令的特定用户帐户启用的状态：</span><span class="sxs-lookup"><span data-stu-id="421b4-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="421b4-125">查看基于公共属性某些帐户</span><span class="sxs-lookup"><span data-stu-id="421b4-125">View some accounts based on a common property</span></span>

<span data-ttu-id="421b4-p103">要更好选择性有关列表帐户显示，您可以使用**Where-object** cmdlet 与**Get AzureADUser** cmdlet 结合使用。若要合并的两个 cmdlet，我们使用"管道"字符"|"，它指示 Azure Active Directory PowerShell 图形执行一个命令的结果并将其发送到下一个命令。下面是显示未指定的使用率位置这些用户帐户的示例命令：</span><span class="sxs-lookup"><span data-stu-id="421b4-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="421b4-129">此命令指示图形到 Azure Active Directory PowerShell:</span><span class="sxs-lookup"><span data-stu-id="421b4-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="421b4-130">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="421b4-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="421b4-p104">查找所有未指定的使用率位置的用户帐户 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括号内命令指示 Office 365 PowerShell 中仅查找的帐户在其中 UsageLocation 用户帐户属性组 ( \*\* $ \_。UsageLocation\*\* ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="421b4-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="421b4-p105">与用户帐户关联的许多属性之一的**UsageLocation**属性。要查看所有用户帐户的属性，用于**Select-object** cmdlet 和通配符 （\*） 以显示所有这些特定的用户帐户。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="421b4-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="421b4-p106">例如，从此列表中，**市/县**是的用户帐户属性的名称。这意味着您可以使用以下命令列出所有的生活中伦敦的用户的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="421b4-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="421b4-p107">以下示例中所示**Where-object** cmdlet 的语法**Where-object {$\_。**[用户帐户属性名][比较运算符][值]**}**。 > [比较运算符] 是 **-eq**等同于的、 不等于为 **-ne** 、 **-lt**小于， **-gt**大于、 和其他人。 [值] 通常是字符串 （的字母、 数字和其他字符序列）、 数字值或 **$Null**的未指定 > 详细信息，请参阅[Where-object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) 。</span><span class="sxs-lookup"><span data-stu-id="421b4-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="421b4-141">使用 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="421b4-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="421b4-142">第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="421b4-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="421b4-143">查看所有帐户</span><span class="sxs-lookup"><span data-stu-id="421b4-143">View all accounts</span></span>

<span data-ttu-id="421b4-144">若要显示的用户帐户的完整列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="421b4-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="421b4-145">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="421b4-145">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="421b4-p108">**Get-msoluser** cmdlet 还具有一套参数筛选的用户帐户显示组。例如，对于未经授权的用户 （已添加到 Office 365 但尚未尚未被许可使用的任何服务的用户） 的列表中，运行此命令。</span><span class="sxs-lookup"><span data-stu-id="421b4-p108">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="421b4-148">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="421b4-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="421b4-149">有关其他参数，以筛选显示一组的用户帐户显示，请参阅[Get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))。</span><span class="sxs-lookup"><span data-stu-id="421b4-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="421b4-150">查看特定帐户</span><span class="sxs-lookup"><span data-stu-id="421b4-150">View a specific account</span></span>

<span data-ttu-id="421b4-151">若要显示特定的用户帐户，请填充的用户帐户，也称为的用户主体名称 (UPN) 的用户帐户的登录名称中删除"<"和">"字符，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="421b4-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="421b4-152">查看基于公共属性某些帐户</span><span class="sxs-lookup"><span data-stu-id="421b4-152">View some accounts based on a common property</span></span>

<span data-ttu-id="421b4-p109">要更好选择性的帐户，若要显示，列表有关您可以使用**Where-object** cmdlet 与**Get-msoluser** cmdlet 结合使用。若要合并的两个 cmdlet，我们使用"管道"字符"|"，它指示 Office 365 PowerShell 中执行一个命令的结果并将其发送到下一个命令。下面是显示未指定的使用率位置这些用户帐户的示例命令：</span><span class="sxs-lookup"><span data-stu-id="421b4-p109">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="421b4-156">此命令指示 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="421b4-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="421b4-157">获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="421b4-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="421b4-p110">查找所有未指定的使用率位置的用户帐户 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括号内命令指示 Office 365 PowerShell 中仅查找的帐户在其中 UsageLocation 用户帐户属性组 ( \*\* $ \_。UsageLocation\*\* ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="421b4-p110">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="421b4-160">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="421b4-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="421b4-p111">与用户帐户关联的许多属性之一的**UsageLocation**属性。要查看所有用户帐户的属性，用于**Select-object** cmdlet 和通配符 （\*） 以显示所有这些特定的用户帐户。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="421b4-p111">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="421b4-p112">例如，从此列表中，**市/县**是的用户帐户属性的名称。这意味着您可以使用以下命令列出所有的生活中伦敦的用户的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="421b4-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="421b4-p113">以下示例中所示**Where-object** cmdlet 的语法**Where-object {$\_。**[用户帐户属性名][比较运算符][值]**}**. [比较运算符] 是 **-eq**等同于的、 不等于为 **-ne** 、 **-lt**小于， **-gt**大于、 和其他人。 [值] 是通常字符串 （的字母、 数字和其他字符序列）、 数字值或 **$Null**未指定。有关详细信息，请参阅[Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="421b4-p113">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified. See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="421b4-171">您可以检查阻止的状态的用户帐户，使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="421b4-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="421b4-172">查看其他属性值的帐户</span><span class="sxs-lookup"><span data-stu-id="421b4-172">View additional property values for accounts</span></span>

<span data-ttu-id="421b4-173">默认情况下**Get-msoluser** cmdlet 显示三个用户帐户的属性：</span><span class="sxs-lookup"><span data-stu-id="421b4-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="421b4-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="421b4-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="421b4-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="421b4-175">DisplayName</span></span>
    
- <span data-ttu-id="421b4-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="421b4-176">isLicensed</span></span>
    
<span data-ttu-id="421b4-p114">如果您需要其他属性，如适用于用户的部门和国家/地区其中用户使用 Office 365 服务，您可以运行**Get-msoluser**结合**Select-object** cmdlet，以指定用户帐户的列表属性。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="421b4-p114">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="421b4-179">此命令指示 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="421b4-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="421b4-180">获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="421b4-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="421b4-181">显示仅的用户帐户名称、 部门和使用率位置 （ **Select-object DisplayName、 部门、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="421b4-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="421b4-182">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="421b4-182">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="421b4-p115">**Select-object** cmdlet，可以选择您希望显示的命令的属性。若要查看所有用户帐户的属性，使用通配符 （\*） 显示所有这些特定的用户帐户。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="421b4-p115">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="421b4-p116">要更好的帐户，若要显示，列表有关选择性您还可以使用**Where-object** cmdlet。下面是显示未指定的使用率位置这些用户帐户的示例命令：</span><span class="sxs-lookup"><span data-stu-id="421b4-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="421b4-188">此命令指示 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="421b4-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="421b4-189">获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="421b4-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="421b4-p117">查找所有未指定的使用率位置的用户帐户 ( **Where-object {$\_。UsageLocation-eq $Null}** ) 并将生成的信息发送到下一个命令 ( **|** )。该命令的大括号内指示 Office 365 PowerShell 中仅查找的帐户在其中 UsageLocation 用户帐户属性组 ( \*\* $ \_。UsageLocation\*\* ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="421b4-p117">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="421b4-192">显示仅的用户帐户名称、 部门和使用率位置 （ **Select-object DisplayName、 部门、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="421b4-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="421b4-193">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="421b4-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="421b4-p118">如果您正在使用目录同步来创建和管理 Office 365 用户，则可以显示 Office 365 用户已从已计划的本地帐户。以下假定 Azure AD 连接配置为使用默认源定位标记的 ObjectGUID (有关配置源定位的详细信息，请参阅[Azure AD 连接： 设计概念](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) 并假定有 powershell 的 Active Directory 模块已安装 （请参阅[RSAT 工具](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)）：</span><span class="sxs-lookup"><span data-stu-id="421b4-p118">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from. The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a><span data-ttu-id="421b4-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="421b4-196">See also</span></span>

[<span data-ttu-id="421b4-197">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="421b4-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="421b4-198">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="421b4-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="421b4-199">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="421b4-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

