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
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "摘要： 视图、 列表或显示您的用户帐户与 Office 365 PowerShell 的各种方式。"
ms.openlocfilehash: e9ffa439c1840cbbbd8a47c2835d9427330804be
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="1f59b-103">查看用户帐户与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f59b-103">View user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="1f59b-104">**摘要：**视图、 列表或显示您的用户帐户与 Office 365 PowerShell 的各种方式。</span><span class="sxs-lookup"><span data-stu-id="1f59b-104">**Summary:** View, list, or display your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="1f59b-105">尽管可以使用 Office 365 管理中心为 Office 365 租户查看帐户，您还可以使用 Office 365 PowerShell 并做一些 Office 365 管理中心不能。</span><span class="sxs-lookup"><span data-stu-id="1f59b-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="1f59b-106">准备工作</span><span class="sxs-lookup"><span data-stu-id="1f59b-106">Before you begin</span></span>

<span data-ttu-id="1f59b-p101">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1f59b-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information"></a><span data-ttu-id="1f59b-109">显示 Office 365 用户帐户信息</span><span class="sxs-lookup"><span data-stu-id="1f59b-109">Display Office 365 user account information</span></span>

<span data-ttu-id="1f59b-110">若要显示的用户帐户的完整列表，请在 Office 365 PowerShell 命令提示符或 PowerShell 集成脚本环境 (ISE) 运行此命令。</span><span class="sxs-lookup"><span data-stu-id="1f59b-110">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="1f59b-111">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="1f59b-111">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="1f59b-p102">**获得 MsolUser** cmdlet 还具有一组参数来筛选显示的用户帐户的组。例如，列表中未授权用户 （用户已被添加到 Office 365，但还没有被授权使用任何服务），对运行此命令。</span><span class="sxs-lookup"><span data-stu-id="1f59b-p102">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="1f59b-114">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="1f59b-114">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="1f59b-115">有关其他参数以筛选显示的详细信息的显示，用户帐户组请参阅[获取 MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="1f59b-115">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span></span>
  
<span data-ttu-id="1f59b-p103">要更好选择列表中的帐户显示，可以使用**对象的位置的**cmdlet **Get MsolUser** cmdlet 的结合。若要合并两个 cmdlet，我们使用"管道"字符"|"，据 Office 365 PowerShell 执行一条命令的结果，并将其发送到下一个命令。下面是一个示例命令，显示具有未指定的使用位置的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="1f59b-119">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1f59b-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="1f59b-120">获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="1f59b-120">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="1f59b-p104">查找所有具有未指定的使用位置的用户帐户 (**位置对象 {$\_。UsageLocation-eq $Null}** )。在大括号中，该命令指示 Office 365 PowerShell 若要仅查找的帐户的 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="1f59b-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="1f59b-123">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="1f59b-123">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="1f59b-p105">**UsageLocation**属性是与用户帐户相关联的多个属性之一。要查看所有用户帐户的属性，用于**选择对象**cmdlet 和通配符 （\*） 以显示所有这些特定的用户帐户。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="1f59b-p106">例如，从该列表中，**城市**是用户帐户属性的名称。这意味着您可以使用以下命令列出所有居住在伦敦的用户的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="1f59b-p107">在这些示例中所示**的位置对象**cmdlet 的语法是**对象的位置的 {$\_。**[用户帐户的属性名称][比较运算符][值]**}**。 > [比较运算符] 是**的 eq**的等号、 **-ne**的不等于、 小于、 大于号、 **-gt**和其他人**的长期**> [值] 通常是一个字符串 （一系列字母、 数字和其他字符）未指定的数值或为**$Null** > 的详细信息，请参阅[位置对象](https://technet.microsoft.com/en-us/library/hh849715.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1f59b-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="1f59b-131">您可以检查用户帐户需要具有以下命令封锁的状态：</span><span class="sxs-lookup"><span data-stu-id="1f59b-131">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="1f59b-132">选择要显示的用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="1f59b-132">Select the user account properties to display</span></span>

<span data-ttu-id="1f59b-133">默认情况下[获取 MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet 将显示三个用户帐户的属性：</span><span class="sxs-lookup"><span data-stu-id="1f59b-133">The [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="1f59b-134">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="1f59b-134">UserPrincipalName</span></span>
    
- <span data-ttu-id="1f59b-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1f59b-135">DisplayName</span></span>
    
- <span data-ttu-id="1f59b-136">isLicensed</span><span class="sxs-lookup"><span data-stu-id="1f59b-136">isLicensed</span></span>
    
<span data-ttu-id="1f59b-p108">如果您需要其他属性，例如在用户所处理的部门和国家/地区，用户使用 Office 365 提供服务，您可以运行**Get MsolUser**结合**选择对象**用于指定用户帐户的列表属性。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p108">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="1f59b-139">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1f59b-139">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="1f59b-140">获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="1f59b-140">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="1f59b-141">显示仅用户帐户名称、 部门和使用位置 （**选择对象的显示名称、 部门、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="1f59b-141">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="1f59b-142">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="1f59b-142">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="1f59b-p109">**选择对象**cmdlet 允许您选取要显示命令的属性。要查看所有用户帐户的属性，使用通配符 （\*） 显示所有这些特定的用户帐户。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p109">The **Select-Object** cmdlet allows you to pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="1f59b-p110">要更好选择列表中的帐户显示，您还可以使用**对象的位置的**cmdlet。下面是一个示例命令，显示具有未指定的使用位置的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p110">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="1f59b-148">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1f59b-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="1f59b-149">获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="1f59b-149">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="1f59b-p111">查找所有具有未指定的使用位置的用户帐户 (**位置对象 {$\_。UsageLocation-eq $Null}** ) 并将得到的信息发送到下一个命令 ( **|** )。在大括号中，该命令指示 Office 365 PowerShell 若要仅查找的帐户的 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="1f59b-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="1f59b-152">显示仅用户帐户名称、 部门和使用位置 （**选择对象的显示名称、 部门、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="1f59b-152">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="1f59b-153">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="1f59b-153">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a><span data-ttu-id="1f59b-154">使用 Azure 活动目录 V2 PowerShell 模块可以显示用户帐户</span><span class="sxs-lookup"><span data-stu-id="1f59b-154">Use the Azure Active Directory V2 PowerShell module to display user accounts</span></span>

<span data-ttu-id="1f59b-p112">若要显示与活动目录 V2 PowerShell 的 Azure 模块的用户帐户的属性，使用[Get AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet。但首先，您必须连接到您的订购。有关说明，请参阅[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="1f59b-p112">To display properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet. But first, you must connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="display-office-365-user-account-information"></a><span data-ttu-id="1f59b-158">显示 Office 365 用户帐户信息</span><span class="sxs-lookup"><span data-stu-id="1f59b-158">Display Office 365 user account information</span></span>

<span data-ttu-id="1f59b-159">若要显示的用户帐户的完整列表，请在 Office 365 PowerShell 命令提示符或 PowerShell 集成脚本环境 (ISE) 运行此命令。</span><span class="sxs-lookup"><span data-stu-id="1f59b-159">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="1f59b-160">默认情况下**获取 AzureADUser** cmdlet 将显示三个用户帐户的属性：</span><span class="sxs-lookup"><span data-stu-id="1f59b-160">The **Get-AzureADUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="1f59b-161">对象 Id</span><span class="sxs-lookup"><span data-stu-id="1f59b-161">ObjectID</span></span>
    
- <span data-ttu-id="1f59b-162">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1f59b-162">DisplayName</span></span>
    
- <span data-ttu-id="1f59b-163">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="1f59b-163">UserPrincipalName</span></span>
    
<span data-ttu-id="1f59b-p113">要更好选择列表中的帐户显示，可以使用**对象的位置的**cmdlet **Get AzureADUser** cmdlet 的结合。若要合并两个 cmdlet，我们使用"管道"字符"|"，据 Office 365 PowerShell 执行一条命令的结果，并将其发送到下一个命令。下面是一个示例命令，显示具有未指定的使用位置的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p113">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="1f59b-167">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1f59b-167">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="1f59b-168">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="1f59b-168">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="1f59b-p114">查找所有具有未指定的使用位置的用户帐户 (**位置对象 {$\_。UsageLocation-eq $Null}** )。在大括号中，该命令指示 Office 365 PowerShell 若要仅查找的帐户的 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="1f59b-p114">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="1f59b-p115">**UsageLocation**属性是与用户帐户相关联的多个属性之一。要查看所有用户帐户的属性，用于**选择对象**cmdlet 和通配符 （\*） 以显示所有这些特定的用户帐户，一页一次 （**更多**）。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p115">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account, one page at a time ( **More** ). Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

<span data-ttu-id="1f59b-p116">例如，**城市**是用户帐户属性的名称。这意味着您可以使用以下命令列出所有居住在伦敦的用户的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p116">For example, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="1f59b-p117">在这些示例中所示**的位置对象**cmdlet 的语法是**对象的位置的 {$\_。**[用户帐户的属性名称][比较运算符][值]**}**。 > [比较运算符] 是**的 eq**的等号、 **-ne**的不等于、 小于、 大于号、 **-gt**和其他人**的长期**> [值] 通常是一个字符串 （一系列字母、 数字和其他字符）未指定的数值或为**$Null** > 的详细信息，请参阅[位置对象](https://technet.microsoft.com/en-us/library/hh849715.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1f59b-p117">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
### <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="1f59b-178">选择要显示的用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="1f59b-178">Select the user account properties to display</span></span>

<span data-ttu-id="1f59b-p118">默认情况下**获取 AzureADUser** cmdlet 显示对象 Id、 显示名称，以及范围内的用户帐户属性。如果您需要其他属性，例如在用户所处理的部门和国家/地区，用户使用 Office 365 提供服务，您可以运行**Get AzureADUser**结合**选择对象**用于指定用户的列表帐户属性。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p118">The **Get-AzureADUser** cmdlet by default displays the ObjectID, DisplayName, and UserPrincipalName properties of user accounts. If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-AzureADUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="1f59b-182">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1f59b-182">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="1f59b-183">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="1f59b-183">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="1f59b-184">显示仅用户帐户名称、 部门和使用位置 （**选择对象的显示名称、 部门、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="1f59b-184">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="1f59b-p119">要更好选择列表中的帐户显示，您还可以使用**对象的位置的**cmdlet。下面是一个示例命令，显示具有未指定的使用位置的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="1f59b-p119">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="1f59b-187">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1f59b-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="1f59b-188">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="1f59b-188">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="1f59b-p120">查找所有具有未指定的使用位置的用户帐户 (**位置对象 {$\_。UsageLocation-eq $Null}** ) 并将得到的信息发送到下一个命令 ( **|** )。在大括号中，该命令指示 Office 365 PowerShell 若要仅查找的帐户的 UsageLocation 用户帐户属性组 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="1f59b-p120">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="1f59b-191">显示仅用户帐户名称、 部门和使用位置 （**选择对象的显示名称、 部门、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="1f59b-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
## <a name="new-to-office-365"></a><span data-ttu-id="1f59b-192">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="1f59b-192">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a><span data-ttu-id="1f59b-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f59b-193">See also</span></span>

#### 

[<span data-ttu-id="1f59b-194">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="1f59b-194">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1f59b-195">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="1f59b-195">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1f59b-196">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="1f59b-196">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

