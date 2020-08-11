---
title: 使用 PowerShell 查看 Microsoft 365 用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 了解如何使用 PowerShell 以不同方式查看、列出或显示 Microsoft 365 用户帐户。
ms.openlocfilehash: 56da6bfc7b467b6a85a4bd8c84abd4c2ae05913f
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605293"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="b6bd8-103">使用 PowerShell 查看 Microsoft 365 用户帐户</span><span class="sxs-lookup"><span data-stu-id="b6bd8-103">View Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="b6bd8-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="b6bd8-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="b6bd8-105">虽然您可以使用 Microsoft 365 管理中心来查看 Microsoft 365 租户的帐户，但您也可以使用 PowerShell for Microsoft 365 并执行管理中心无法执行的某些操作。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-105">Although you can use the Microsoft 365 admin center to view the accounts for your Microsoft 365 tenant, you can also use PowerShell for Microsoft 365 and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="b6bd8-106">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6bd8-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="b6bd8-107">首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-107">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="b6bd8-108">查看所有帐户</span><span class="sxs-lookup"><span data-stu-id="b6bd8-108">View all accounts</span></span>

<span data-ttu-id="b6bd8-109">若要显示用户帐户的完整列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-109">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="b6bd8-110">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-110">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="b6bd8-111">查看特定帐户</span><span class="sxs-lookup"><span data-stu-id="b6bd8-111">View a specific account</span></span>

<span data-ttu-id="b6bd8-112">若要显示特定的用户帐户，请填写用户帐户的登录帐户名（也称为 "用户主体名称 (UPN) ），删除" < "和" > "字符，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="b6bd8-113">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-113">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="b6bd8-114">查看特定帐户的其他属性值</span><span class="sxs-lookup"><span data-stu-id="b6bd8-114">View additional property values for a specific account</span></span>

<span data-ttu-id="b6bd8-115">默认情况下， **AzureADUser** cmdlet 仅显示帐户的 ObjectID、DisplayName 和 UserPrincipalName 属性。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="b6bd8-116">若要更好地选择要显示的属性列表，可以结合使用**Select** Cmdlet 和**AzureADUser** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-116">To be more selective about the list of properties to display, you can use the **Select** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="b6bd8-117">若要组合这两个 cmdlet，我们使用 "管道" 字符 "|"，它通知 Azure Active Directory PowerShell 以获取一个命令的结果，并将其发送到下一个命令。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-117">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="b6bd8-118">下面是一个显示每个用户帐户的 DisplayName、部门和 UsageLocation 的示例命令：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-118">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

<span data-ttu-id="b6bd8-119">此命令指示 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-119">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="b6bd8-120">获取用户帐户上的所有信息 ( **AzureADUser** ) 并将其发送到下一个命令 ( **|** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b6bd8-121">仅显示用户帐户名称、部门和使用位置 (**选择 "DisplayName"、"部门"、"UsageLocation"** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-121">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="b6bd8-122">若要查看用户帐户的所有属性，请使用**Select** cmdlet 和通配符 ( \* ) 为特定用户帐户显示所有属性。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-122">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b6bd8-123">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-123">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="b6bd8-124">作为另一个示例，您可以使用以下命令检查特定用户帐户的启用状态：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="b6bd8-125">根据通用属性查看一些帐户</span><span class="sxs-lookup"><span data-stu-id="b6bd8-125">View some accounts based on a common property</span></span>

<span data-ttu-id="b6bd8-126">若要更好地选择要显示的帐户列表，可以结合使用**Where** Cmdlet 和**AzureADUser** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-126">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="b6bd8-127">若要组合这两个 cmdlet，我们使用 "管道" 字符 "|"，它通知 Azure Active Directory PowerShell 以获取一个命令的结果，并将其发送到下一个命令。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-127">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="b6bd8-128">下面是一个示例命令，它显示了未指定使用地点的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-128">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="b6bd8-129">此命令将 Azure Active Directory PowerShell for Graph 指示为：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="b6bd8-130">获取用户帐户上的所有信息 ( **AzureADUser** ) 并将其发送到下一个命令 ( **|** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b6bd8-131">查找未指定使用位置的所有用户帐户 (**其中 {$ \_ 。UsageLocation-eq $Null}** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-131">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="b6bd8-132">在大括号内，该命令指示 PowerShell 仅查找 UsageLocation 用户帐户属性 ( 的帐户集\*\* $ \_ 。\*\* 未 ( **-eq $Null** ) 指定 UsageLocation ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-132">Inside the braces, the command instructs PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="b6bd8-133">**UsageLocation**属性只是与用户帐户关联的很多属性中的一个。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-133">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="b6bd8-134">若要查看用户帐户的所有属性，请使用**Select** cmdlet 和通配符 ( \* ) 为特定用户帐户显示所有属性。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-134">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b6bd8-135">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-135">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="b6bd8-136">例如，在此列表中， **City**是用户帐户属性的名称。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-136">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="b6bd8-137">这意味着您可以使用以下命令列出居住在伦敦的用户的所有用户帐户：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-137">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="b6bd8-138">这些示例中所示的**where** cmdlet 的语法为 **{$ \_ 。**</span><span class="sxs-lookup"><span data-stu-id="b6bd8-138">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="b6bd8-139">[用户帐户属性名称][比较运算符]增值 **}**. > [比较运算符] 为 **-eq** for equals， **-ne**不等于， **-lt**表示小于， **-gt**表示大于，其他。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-139">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="b6bd8-140">[value] 通常是一个字符串， (字母、数字和其他字符的序列) 、数值或未指定> 的 **$Null** 。有关详细信息，请参阅[Where](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-140">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b6bd8-141">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="b6bd8-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b6bd8-142">首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-142">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="b6bd8-143">查看所有帐户</span><span class="sxs-lookup"><span data-stu-id="b6bd8-143">View all accounts</span></span>

<span data-ttu-id="b6bd8-144">若要显示用户帐户的完整列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-144">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

>[!Note]
><span data-ttu-id="b6bd8-145">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-145">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="b6bd8-146">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-146">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="b6bd8-147">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-147">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="b6bd8-148">**Get-MsolUser** cmdlet 也有一组参数可用于筛选显示的用户帐户组。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-148">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="b6bd8-149">例如，对于已添加到 Microsoft 365 但尚未许可使用任何服务) 的用户，未授权用户的列表 (的用户运行此命令。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-149">For example, for the list of unlicensed users (users who've been added to Microsoft 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="b6bd8-150">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-150">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="b6bd8-151">有关筛选显示显示的用户帐户集的其他参数的详细信息，请参阅[get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-151">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  
### <a name="view-a-specific-account"></a><span data-ttu-id="b6bd8-152">查看特定帐户</span><span class="sxs-lookup"><span data-stu-id="b6bd8-152">View a specific account</span></span>

<span data-ttu-id="b6bd8-153">若要显示特定的用户帐户，请填写用户帐户的用户帐户的登录名（也称为 "用户主体名称 (UPN) ），删除" < "和" > "字符，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-153">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="b6bd8-154">根据通用属性查看一些帐户</span><span class="sxs-lookup"><span data-stu-id="b6bd8-154">View some accounts based on a common property</span></span>

<span data-ttu-id="b6bd8-155">若要更好地选择要显示的帐户列表，可以结合使用**Where** Cmdlet 和**get-msoluser** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-155">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="b6bd8-156">若要组合这两个 cmdlet，我们使用 "管道" 字符 "|"，它将通知 PowerShell 获取一个命令的结果，并将其发送到下一个命令。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-156">To combine the two cmdlets, we use the "pipe" character "|", which tells PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="b6bd8-157">下面是一个示例命令，它显示了未指定使用地点的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-157">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="b6bd8-158">此命令指示 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-158">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="b6bd8-159">获取用户帐户上的所有信息 ( **get-msoluser** ) 并将其发送到下一个命令 ( **|** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-159">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b6bd8-160">查找未指定使用位置的所有用户帐户 (**其中 {$ \_ 。UsageLocation-eq $Null}** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-160">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="b6bd8-161">在大括号内，该命令指示 PowerShell 仅查找 UsageLocation 用户帐户属性 ( 的帐户集\*\* $ \_ 。\*\* 未 ( **-eq $Null** ) 指定 UsageLocation ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-161">Inside the braces, the command instructs PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="b6bd8-162">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-162">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="b6bd8-163">**UsageLocation**属性只是与用户帐户关联的很多属性中的一个。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-163">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="b6bd8-164">若要查看用户帐户的所有属性，请使用**Select** cmdlet 和通配符 ( \* ) 为特定用户帐户显示所有属性。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-164">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b6bd8-165">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-165">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="b6bd8-166">例如，在此列表中， **City**是用户帐户属性的名称。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-166">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="b6bd8-167">这意味着您可以使用以下命令列出居住在伦敦的用户的所有用户帐户：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-167">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="b6bd8-168">这些示例中所示的**where** cmdlet 的语法为 **{$ \_ 。**</span><span class="sxs-lookup"><span data-stu-id="b6bd8-168">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="b6bd8-169">[用户帐户属性名称][比较运算符]增值 **}**.</span><span class="sxs-lookup"><span data-stu-id="b6bd8-169">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="b6bd8-170">[比较运算符] 为 **-eq** ，等于， **-ne**表示不等于， **-lt**表示小于， **-gt**表示大于，其他。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-170">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="b6bd8-171">[value] 通常是一个字符串， (字母、数字和其他字符的序列) 、数字值或未指定的 **$Null** 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-171">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="b6bd8-172">有关详细信息，请参阅[何处](https://technet.microsoft.com/library/hh849715.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-172">See [Where](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="b6bd8-173">您可以使用以下命令检查用户帐户的阻止状态：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-173">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="b6bd8-174">查看帐户的其他属性值</span><span class="sxs-lookup"><span data-stu-id="b6bd8-174">View additional property values for accounts</span></span>

<span data-ttu-id="b6bd8-175">默认情况下， **get-msoluser** cmdlet 显示用户帐户的三个属性：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-175">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="b6bd8-176">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="b6bd8-176">UserPrincipalName</span></span>
    
- <span data-ttu-id="b6bd8-177">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b6bd8-177">DisplayName</span></span>
    
- <span data-ttu-id="b6bd8-178">isLicensed</span><span class="sxs-lookup"><span data-stu-id="b6bd8-178">isLicensed</span></span>
    
<span data-ttu-id="b6bd8-179">如果您需要其他属性（如用户所使用的部门和用户使用 Microsoft 365 服务的国家/地区），则可以同时运行**get-msoluser** ，并使用**Select** cmdlet 指定用户帐户属性列表。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-179">If you need additional properties, such as the department the user works for and the country/region where the user uses Microsoft 365 services, you can run **Get-MsolUser** in combination with the **Select** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="b6bd8-180">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-180">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="b6bd8-181">此命令指示 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-181">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="b6bd8-182">获取用户帐户上的所有信息 ( **get-msoluser** ) 并将其发送到下一个命令 ( **|** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b6bd8-183">仅显示用户帐户名称、部门和使用位置 (**选择 "DisplayName"、"部门"、"UsageLocation"** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-183">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="b6bd8-184">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-184">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="b6bd8-185">使用**Select** cmdlet，您可以选取要显示命令的属性并选择这些属性。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-185">The **Select** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="b6bd8-186">若要查看用户帐户的所有属性，请使用通配符 ( \* ) 为特定用户帐户显示所有属性。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-186">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b6bd8-187">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-187">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="b6bd8-188">若要更好地选择要显示的帐户列表，您还可以使用**Where** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-188">To be more selective about the list of accounts to display, you can also use the **Where** cmdlet.</span></span> <span data-ttu-id="b6bd8-189">下面是一个示例命令，它显示了未指定使用地点的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-189">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="b6bd8-190">此命令指示 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-190">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="b6bd8-191">获取用户帐户上的所有信息 ( **get-msoluser** ) 并将其发送到下一个命令 ( **|** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-191">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b6bd8-192">查找未指定使用位置的所有用户帐户 (**其中 {$ \_ 。UsageLocation-eq $Null}** ) 并将生成的信息发送到下一个命令 ( **|** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-192">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="b6bd8-193">在大括号内，该命令指示 PowerShell 仅查找 UsageLocation 用户帐户属性 ( 的帐户集\*\* $ \_ 。\*\* 未 ( **-eq $Null** ) 指定 UsageLocation ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-193">Inside the braces, the command is instructing PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="b6bd8-194">仅显示用户帐户名称、部门和使用位置 (**选择 "DisplayName"、"部门"、"UsageLocation"** ) 。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-194">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="b6bd8-195">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-195">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="b6bd8-196">如果要使用目录同步来创建和管理 Microsoft 365 用户，则可以显示已投影 Microsoft 365 用户的本地帐户。</span><span class="sxs-lookup"><span data-stu-id="b6bd8-196">If you are using directory synchronization to create and manage your Microsoft 365 users, you can display which local account a Microsoft 365 user has been projected from.</span></span> <span data-ttu-id="b6bd8-197">以下示例假定已将 Azure AD Connect 配置为使用 ObjectGUID (的默认源锚点。有关配置源锚点的详细信息，请参阅[AZURE Ad connect：设计概念](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) 并假定已安装用于 PowerShell 的 Active Directory 域服务模块 (参阅[RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)) ：</span><span class="sxs-lookup"><span data-stu-id="b6bd8-197">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory Domain Services module for PowerShell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a><span data-ttu-id="b6bd8-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6bd8-198">See also</span></span>

[<span data-ttu-id="b6bd8-199">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="b6bd8-199">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b6bd8-200">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="b6bd8-200">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b6bd8-201">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="b6bd8-201">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

