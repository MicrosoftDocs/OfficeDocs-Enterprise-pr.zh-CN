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
ms.openlocfilehash: 0711bf945b863cb89d45a377f61a139b298ca6d7
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748400"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="26dfc-103">查看用户帐户与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="26dfc-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="26dfc-104">虽然您可以使用 Microsoft 365 管理中心来查看 Office 365 租户的帐户，但您也可以使用 Office 365 PowerShell，并执行管理中心无法执行的某些操作。</span><span class="sxs-lookup"><span data-stu-id="26dfc-104">Although you can use the Microsoft 365 admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="26dfc-105">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="26dfc-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="26dfc-106">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="26dfc-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="26dfc-107">查看所有帐户</span><span class="sxs-lookup"><span data-stu-id="26dfc-107">View all accounts</span></span>

<span data-ttu-id="26dfc-108">若要显示用户帐户的完整列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="26dfc-108">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="26dfc-109">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="26dfc-109">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="26dfc-110">查看特定帐户</span><span class="sxs-lookup"><span data-stu-id="26dfc-110">View a specific account</span></span>

<span data-ttu-id="26dfc-111">若要显示特定的用户帐户，请填写用户帐户的登录帐户名（也称为 "用户主体名称（UPN）"），删除 "<" 和 ">" 字符，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="26dfc-111">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="26dfc-112">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="26dfc-112">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="26dfc-113">查看特定帐户的其他属性值</span><span class="sxs-lookup"><span data-stu-id="26dfc-113">View additional property values for a specific account</span></span>

<span data-ttu-id="26dfc-114">默认情况下， **AzureADUser** cmdlet 仅显示帐户的 ObjectID、DisplayName 和 UserPrincipalName 属性。</span><span class="sxs-lookup"><span data-stu-id="26dfc-114">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="26dfc-115">若要更好地选择要显示的属性列表，可以结合使用**Select 对象**Cmdlet 和**AzureADUser** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26dfc-115">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="26dfc-116">若要组合这两个 cmdlet，我们使用 "管道" 字符 "|"，它通知 Azure Active Directory PowerShell 以获取一个命令的结果，并将其发送到下一个命令。</span><span class="sxs-lookup"><span data-stu-id="26dfc-116">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="26dfc-117">下面是一个显示每个用户帐户的 DisplayName、部门和 UsageLocation 的示例命令：</span><span class="sxs-lookup"><span data-stu-id="26dfc-117">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="26dfc-118">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="26dfc-118">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="26dfc-119">获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-119">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="26dfc-120">仅显示用户帐户名称、部门和使用位置（**选择-对象 DisplayName、部门、UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-120">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="26dfc-121">若要查看用户帐户的所有属性，请使用**Select-Object** cmdlet 和通配符（\*）为特定用户帐户显示所有属性。</span><span class="sxs-lookup"><span data-stu-id="26dfc-121">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="26dfc-122">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="26dfc-122">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="26dfc-123">作为另一个示例，您可以使用以下命令检查特定用户帐户的启用状态：</span><span class="sxs-lookup"><span data-stu-id="26dfc-123">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="26dfc-124">根据通用属性查看一些帐户</span><span class="sxs-lookup"><span data-stu-id="26dfc-124">View some accounts based on a common property</span></span>

<span data-ttu-id="26dfc-125">若要更好地选择要显示的帐户列表，可以结合使用**AzureADUser** Cmdlet 与**Where 对象**cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26dfc-125">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="26dfc-126">若要组合这两个 cmdlet，我们使用 "管道" 字符 "|"，它通知 Azure Active Directory PowerShell 以获取一个命令的结果，并将其发送到下一个命令。</span><span class="sxs-lookup"><span data-stu-id="26dfc-126">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="26dfc-127">下面是一个示例命令，它显示了未指定使用地点的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="26dfc-127">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="26dfc-128">此命令将 Azure Active Directory PowerShell for Graph 指示为：</span><span class="sxs-lookup"><span data-stu-id="26dfc-128">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="26dfc-129">获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-129">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="26dfc-130">查找所有具有未指定使用位置（**其中-对象为\_{$）的用户帐户。UsageLocation-eq $Null}** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-130">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="26dfc-131">在大括号内，该命令指示 Office 365 PowerShell 仅查找 UsageLocation 用户帐户属性（ \*\* $ \_。\*\* 未指定 UsageLocation）（ **-eq $Null** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-131">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="26dfc-132">**UsageLocation**属性只是与用户帐户关联的很多属性中的一个。</span><span class="sxs-lookup"><span data-stu-id="26dfc-132">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="26dfc-133">若要查看用户帐户的所有属性，请使用**Select-Object** cmdlet 和通配符（\*）为特定用户帐户显示所有属性。</span><span class="sxs-lookup"><span data-stu-id="26dfc-133">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="26dfc-134">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="26dfc-134">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="26dfc-135">例如，在此列表中， **City**是用户帐户属性的名称。</span><span class="sxs-lookup"><span data-stu-id="26dfc-135">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="26dfc-136">这意味着您可以使用以下命令列出居住在伦敦的用户的所有用户帐户：</span><span class="sxs-lookup"><span data-stu-id="26dfc-136">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="26dfc-137">在这些示例中显示的 " **Where 对象**" cmdlet 的语法为 **-object {$\_。**</span><span class="sxs-lookup"><span data-stu-id="26dfc-137">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="26dfc-138">[用户帐户属性名称][比较运算符]增值 **}**. > [比较运算符] 为 **-eq** for equals， **-ne**不等于， **-lt**表示小于， **-gt**表示大于，其他。</span><span class="sxs-lookup"><span data-stu-id="26dfc-138">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="26dfc-139">[value] 通常是一个字符串（字母、数字和其他字符的序列）、数值或未指定的 **$Null**> 请参阅[Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1)获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="26dfc-139">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="26dfc-140">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="26dfc-140">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="26dfc-141">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="26dfc-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="26dfc-142">查看所有帐户</span><span class="sxs-lookup"><span data-stu-id="26dfc-142">View all accounts</span></span>

<span data-ttu-id="26dfc-143">若要显示用户帐户的完整列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="26dfc-143">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

<span data-ttu-id="26dfc-144">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="26dfc-144">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="26dfc-145">**Get-MsolUser** cmdlet 也有一组参数可用于筛选显示的用户帐户组。</span><span class="sxs-lookup"><span data-stu-id="26dfc-145">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="26dfc-146">例如，对于未授权用户的列表（已添加到 Office 365 但尚未许可使用任何服务的用户），请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="26dfc-146">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="26dfc-147">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="26dfc-147">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="26dfc-148">有关筛选显示显示的用户帐户集的其他参数的详细信息，请参阅[get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))。</span><span class="sxs-lookup"><span data-stu-id="26dfc-148">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="26dfc-149">查看特定帐户</span><span class="sxs-lookup"><span data-stu-id="26dfc-149">View a specific account</span></span>

<span data-ttu-id="26dfc-150">若要显示特定的用户帐户，请填写用户帐户的用户帐户的登录名（也称为 "用户主体名称（UPN）"），删除 "<" 和 ">" 字符，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="26dfc-150">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="26dfc-151">根据通用属性查看一些帐户</span><span class="sxs-lookup"><span data-stu-id="26dfc-151">View some accounts based on a common property</span></span>

<span data-ttu-id="26dfc-152">若要更好地选择要显示的帐户列表，可以结合使用**get-msoluser** Cmdlet 与**Where 对象**cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26dfc-152">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="26dfc-153">若要组合这两个 cmdlet，我们使用 "管道" 字符 "|"，它会告诉 Office 365 PowerShell 获取一个命令的结果，并将其发送到下一个命令。</span><span class="sxs-lookup"><span data-stu-id="26dfc-153">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="26dfc-154">下面是一个示例命令，它显示了未指定使用地点的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="26dfc-154">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="26dfc-155">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="26dfc-155">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="26dfc-156">获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-156">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="26dfc-157">查找所有具有未指定使用位置（**其中-对象为\_{$）的用户帐户。UsageLocation-eq $Null}** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-157">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="26dfc-158">在大括号内，该命令指示 Office 365 PowerShell 仅查找 UsageLocation 用户帐户属性（ \*\* $ \_。\*\* 未指定 UsageLocation）（ **-eq $Null** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-158">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="26dfc-159">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="26dfc-159">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="26dfc-160">**UsageLocation**属性只是与用户帐户关联的很多属性中的一个。</span><span class="sxs-lookup"><span data-stu-id="26dfc-160">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="26dfc-161">若要查看用户帐户的所有属性，请使用**Select-Object** cmdlet 和通配符（\*）为特定用户帐户显示所有属性。</span><span class="sxs-lookup"><span data-stu-id="26dfc-161">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="26dfc-162">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="26dfc-162">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="26dfc-163">例如，在此列表中， **City**是用户帐户属性的名称。</span><span class="sxs-lookup"><span data-stu-id="26dfc-163">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="26dfc-164">这意味着您可以使用以下命令列出居住在伦敦的用户的所有用户帐户：</span><span class="sxs-lookup"><span data-stu-id="26dfc-164">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="26dfc-165">在这些示例中显示的 " **Where 对象**" cmdlet 的语法为 **-object {$\_。**</span><span class="sxs-lookup"><span data-stu-id="26dfc-165">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="26dfc-166">[用户帐户属性名称][比较运算符]增值 **}**.</span><span class="sxs-lookup"><span data-stu-id="26dfc-166">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="26dfc-167">[比较运算符] 为 **-eq** ，等于， **-ne**表示不等于， **-lt**表示小于， **-gt**表示大于，其他。</span><span class="sxs-lookup"><span data-stu-id="26dfc-167">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="26dfc-168">[value] 通常是一个字符串（一系列字母、数字和其他字符）、一个数值或未指定 **$Null** 。</span><span class="sxs-lookup"><span data-stu-id="26dfc-168">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="26dfc-169">有关详细信息，请参阅[Where-Object](https://technet.microsoft.com/library/hh849715.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="26dfc-169">See [Where-Object](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="26dfc-170">您可以使用以下命令检查用户帐户的阻止状态：</span><span class="sxs-lookup"><span data-stu-id="26dfc-170">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="26dfc-171">查看帐户的其他属性值</span><span class="sxs-lookup"><span data-stu-id="26dfc-171">View additional property values for accounts</span></span>

<span data-ttu-id="26dfc-172">默认情况下， **get-msoluser** cmdlet 显示用户帐户的三个属性：</span><span class="sxs-lookup"><span data-stu-id="26dfc-172">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="26dfc-173">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="26dfc-173">UserPrincipalName</span></span>
    
- <span data-ttu-id="26dfc-174">DisplayName</span><span class="sxs-lookup"><span data-stu-id="26dfc-174">DisplayName</span></span>
    
- <span data-ttu-id="26dfc-175">isLicensed</span><span class="sxs-lookup"><span data-stu-id="26dfc-175">isLicensed</span></span>
    
<span data-ttu-id="26dfc-176">如果需要其他属性（如用户所使用的部门和用户使用 Office 365 服务的国家/地区） **，则可以**同时运行**get-msoluser** cmdlet，以指定用户帐户属性列表。</span><span class="sxs-lookup"><span data-stu-id="26dfc-176">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="26dfc-177">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="26dfc-177">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="26dfc-178">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="26dfc-178">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="26dfc-179">获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-179">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="26dfc-180">仅显示用户帐户名称、部门和使用位置（**选择-对象 DisplayName、部门、UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-180">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="26dfc-181">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="26dfc-181">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="26dfc-182">通过**选择-对象**cmdlet，您可以选取您想要命令显示的属性并选择这些属性。</span><span class="sxs-lookup"><span data-stu-id="26dfc-182">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="26dfc-183">若要查看用户帐户的所有属性，请使用通配符（\*）为特定用户帐户显示所有属性。</span><span class="sxs-lookup"><span data-stu-id="26dfc-183">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="26dfc-184">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="26dfc-184">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="26dfc-185">若要更好地选择要显示的帐户列表，您还可以使用**对象**之间的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26dfc-185">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet.</span></span> <span data-ttu-id="26dfc-186">下面是一个示例命令，它显示了未指定使用地点的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="26dfc-186">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="26dfc-187">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="26dfc-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="26dfc-188">获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-188">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="26dfc-189">查找所有具有未指定使用位置（**其中-对象为\_{$）的用户帐户。UsageLocation-eq $Null}** ）并将生成的信息发送到下一个命令**|** （）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-189">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="26dfc-190">在大括号内，该命令指示 Office 365 PowerShell 仅查找 UsageLocation 用户帐户属性（ \*\* $ \_位于其中）的帐户集。\*\* 未指定 UsageLocation）（ **-eq $Null** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-190">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="26dfc-191">仅显示用户帐户名称、部门和使用位置（**选择-对象 DisplayName、部门、UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="26dfc-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="26dfc-192">您应看到类似于以下内容的信息：</span><span class="sxs-lookup"><span data-stu-id="26dfc-192">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="26dfc-193">如果使用目录同步来创建和管理 Office 365 用户，则可以显示计划了 Office 365 用户的本地帐户。</span><span class="sxs-lookup"><span data-stu-id="26dfc-193">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="26dfc-194">以下示例假定 Azure AD Connect 已配置为使用 ObjectGUID 的默认源锚点（有关配置源锚点的详细信息，请参阅[AZURE AD Connect：设计概念](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)），并假定已安装 Powershell 的 Active Directory 模块（请参阅[RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)）：</span><span class="sxs-lookup"><span data-stu-id="26dfc-194">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a><span data-ttu-id="26dfc-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26dfc-195">See also</span></span>

[<span data-ttu-id="26dfc-196">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="26dfc-196">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="26dfc-197">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="26dfc-197">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="26dfc-198">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="26dfc-198">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

