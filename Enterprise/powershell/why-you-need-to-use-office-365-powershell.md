---
title: 为什么需要使用适用于 Microsoft 365 的 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 摘要：了解为什么必须使用 PowerShell 来管理 Microsoft 365，在某些情况下，在某些情况下可以更有效地管理 Microsoft。
ms.openlocfilehash: ba786acd8b5ad08bad97b11812f0180004e55cb6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229858"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a><span data-ttu-id="03181-103">为什么需要使用适用于 Microsoft 365 的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="03181-103">Why you need to use PowerShell for Microsoft 365</span></span>

<span data-ttu-id="03181-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="03181-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="03181-105">使用 Microsoft 365 管理中心，不仅可以管理 Microsoft 365 用户帐户和许可证，还可以管理 Microsoft 365 服务，例如 Exchange Online、团队和 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="03181-105">With the Microsoft 365 admin center, you can not only manage your Microsoft 365 user accounts and licenses, but you can also manage your Microsoft 365 services such as Exchange Online, Teams, and SharePoint Online.</span></span> <span data-ttu-id="03181-106">不过，您还可以使用 PowerShell 命令管理这些元素，利用命令行和脚本语言环境实现速度、自动化和其他功能。</span><span class="sxs-lookup"><span data-stu-id="03181-106">However, you can also manage these elements with PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="03181-107">在本文中，我们将向你展示可使用 PowerShell 管理 Microsoft 365 的方法：</span><span class="sxs-lookup"><span data-stu-id="03181-107">In this article, we'll show you these ways in which you can use PowerShell to manage Microsoft 365:</span></span>
  
- <span data-ttu-id="03181-108">显示使用 Microsoft 365 管理中心无法看到的其他信息</span><span class="sxs-lookup"><span data-stu-id="03181-108">Reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>
    
- <span data-ttu-id="03181-109">仅配置 PowerShell 可能的功能和设置</span><span class="sxs-lookup"><span data-stu-id="03181-109">Configure features and settings only possible with PowerShell</span></span>
    
- <span data-ttu-id="03181-110">执行批量操作</span><span class="sxs-lookup"><span data-stu-id="03181-110">Perform bulk operations</span></span>
    
- <span data-ttu-id="03181-111">筛选数据</span><span class="sxs-lookup"><span data-stu-id="03181-111">Filtering data</span></span>
    
- <span data-ttu-id="03181-112">打印或保存数据</span><span class="sxs-lookup"><span data-stu-id="03181-112">Print or save data</span></span>
    
- <span data-ttu-id="03181-113">跨服务管理</span><span class="sxs-lookup"><span data-stu-id="03181-113">Manage across services</span></span>
    
<span data-ttu-id="03181-114">在开始之前，请先了解 Microsoft 365 的 PowerShell，它是一组用于 Windows PowerShell 的模块，即基于 Windows 的服务和平台的命令行环境。</span><span class="sxs-lookup"><span data-stu-id="03181-114">Before you begin, understand that PowerShell for Microsoft 365 is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms.</span></span> <span data-ttu-id="03181-115">此环境创建一种命令行管理程序语言，可使用其他模块进行扩展，并提供执行简单或复杂命令或脚本的方法。</span><span class="sxs-lookup"><span data-stu-id="03181-115">This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts.</span></span> <span data-ttu-id="03181-116">例如，在安装适用于 Microsoft 365 模块的 PowerShell 并连接到 Microsoft 365 订阅后，可以运行此命令，以列出 Microsoft Exchange Online 的所有用户邮箱：</span><span class="sxs-lookup"><span data-stu-id="03181-116">For example, after you install the PowerShell for Microsoft 365 modules and connect to your Microsoft 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```powershell
Get-Mailbox
```

<span data-ttu-id="03181-117">使用 Microsoft 365 管理中心也可以轻松地获取邮箱的列表，但计算所有 web 应用程序的所有网站的所有列表中的项目数无法轻松完成。</span><span class="sxs-lookup"><span data-stu-id="03181-117">Getting the list of mailboxes can also be easily done using the Microsoft 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="03181-118">请注意，适用于 Microsoft 365 的 PowerShell 旨在提高和增强管理 Microsoft 365 的能力，而不是替换 Microsoft 365 管理中心。</span><span class="sxs-lookup"><span data-stu-id="03181-118">Please note that PowerShell for Microsoft 365 is designed to augment and enhance your ability to manage Microsoft 365, not to replace the Microsoft 365 admin center.</span></span> <span data-ttu-id="03181-119">作为管理员，您必须至少为 Microsoft 365 使用 PowerShell，因为有一些配置过程只能在 PowerShell 中为 Microsoft 365 命令完成。</span><span class="sxs-lookup"><span data-stu-id="03181-119">As an administrator, you must become at least comfortable with using PowerShell for Microsoft 365 because there are some configuration procedures that can only be done with PowerShell for Microsoft 365 commands.</span></span> <span data-ttu-id="03181-120">在这些情况下，需要了解如何：</span><span class="sxs-lookup"><span data-stu-id="03181-120">In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="03181-121">为 Microsoft 365 模块安装 PowerShell （每台管理员计算机只能执行一次）。</span><span class="sxs-lookup"><span data-stu-id="03181-121">Install the PowerShell for Microsoft 365 modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="03181-122">连接到 Microsoft 365 订阅（为每个 PowerShell 会话完成一次）。</span><span class="sxs-lookup"><span data-stu-id="03181-122">Connect to your Microsoft 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="03181-123">收集运行所需的 PowerShell for Microsoft 365 命令所需的信息。</span><span class="sxs-lookup"><span data-stu-id="03181-123">Gather the information needed to run the required PowerShell for Microsoft 365 commands.</span></span>
    
- <span data-ttu-id="03181-124">成功运行适用于 Microsoft 365 命令的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="03181-124">Run the PowerShell for Microsoft 365 commands successfully.</span></span>
    
<span data-ttu-id="03181-125">在学过这些基本技巧之后，您不需要使用 **Get-Mailbox** 命令列出您的邮箱用户，也不需要明白如何创建像前一个命令那样的新命令来计算您的所有 Web 应用的所有网站的所有列表中的项目数量。</span><span class="sxs-lookup"><span data-stu-id="03181-125">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps.</span></span> <span data-ttu-id="03181-126">Microsoft 和管理员社区可以根据需要为您提供帮助。</span><span class="sxs-lookup"><span data-stu-id="03181-126">Microsoft and the community of administrators can help you with that as needed.</span></span>
  
## <a name="powershell-for-microsoft-365-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a><span data-ttu-id="03181-127">PowerShell for Microsoft 365 可以显示你无法通过 Microsoft 365 管理中心看到的其他信息</span><span class="sxs-lookup"><span data-stu-id="03181-127">PowerShell for Microsoft 365 can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>

<span data-ttu-id="03181-128">Microsoft 365 管理中心显示了大量有用的信息，但这并不意味着它会显示 Microsoft 365 存储在用户、许可证、邮箱和网站上的所有可能的信息。</span><span class="sxs-lookup"><span data-stu-id="03181-128">The Microsoft 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Microsoft 365 stores on users, licenses, mailboxes, and sites.</span></span> <span data-ttu-id="03181-129">下面的示例展示了 Microsoft 365 管理中心中的**用户和组**：</span><span class="sxs-lookup"><span data-stu-id="03181-129">Here is an example for **users and groups** in the Microsoft 365 admin center:</span></span>
  
![Microsoft 365 管理中心中的用户和组的显示示例。](media/o365-powershell-users-and-groups.png)
  
<span data-ttu-id="03181-131">出于多种目的，这显示了你需要知道的信息。</span><span class="sxs-lookup"><span data-stu-id="03181-131">For many purposes, this displays the information you need to know.</span></span> <span data-ttu-id="03181-132">但是，有时你需要了解更多。</span><span class="sxs-lookup"><span data-stu-id="03181-132">However, there are times when you need more.</span></span> <span data-ttu-id="03181-133">例如，Microsoft 365 许可（和用户可使用的 Microsoft 365 功能）取决于该用户的地理位置。</span><span class="sxs-lookup"><span data-stu-id="03181-133">For example, Microsoft 365 licensing (and the Microsoft 365 features available to a user) depend in part on that user's geographic location.</span></span> <span data-ttu-id="03181-134">向居住在美国的用户扩展的策略和功能可能与向居住在印度或比利时的用户扩展的策略和功能不同。</span><span class="sxs-lookup"><span data-stu-id="03181-134">The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium.</span></span> <span data-ttu-id="03181-135">您可以使用 Microsoft 365 管理中心来确定用户的地理位置，步骤如下：</span><span class="sxs-lookup"><span data-stu-id="03181-135">You can use the Microsoft 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="03181-136">双击用户的"显示名称"。</span><span class="sxs-lookup"><span data-stu-id="03181-136">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="03181-137">在用户属性显示窗格中，单击"详细信息"。</span><span class="sxs-lookup"><span data-stu-id="03181-137">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="03181-138">在显示的详细信息中，单击"其他详细信息"。</span><span class="sxs-lookup"><span data-stu-id="03181-138">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="03181-139">向下滚动，直到看见"国家或地区"标题：</span><span class="sxs-lookup"><span data-stu-id="03181-139">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Microsoft 365 管理中心中用户的区域信息示例。](media/o365-powershell-usage-location.png)
  
5. <span data-ttu-id="03181-141">在一张纸上记下用户的显示名称和位置，或将其复制并粘贴至记事本中。</span><span class="sxs-lookup"><span data-stu-id="03181-141">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="03181-142">您必须为每个用户重复此过程。</span><span class="sxs-lookup"><span data-stu-id="03181-142">You must repeat this procedure for each user.</span></span> <span data-ttu-id="03181-143">对于许多用户来说，这可能是一项繁琐的任务。</span><span class="sxs-lookup"><span data-stu-id="03181-143">For many users, this can be a tedious task.</span></span> <span data-ttu-id="03181-144">对于适用于 Microsoft 365 的 PowerShell，你可以使用以下命令为所有用户显示此信息：</span><span class="sxs-lookup"><span data-stu-id="03181-144">With PowerShell for Microsoft 365, you can display this information for all of your users with the following command:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
><span data-ttu-id="03181-145">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="03181-145">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="03181-146">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="03181-146">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="03181-147">下面展示了显示内容示例：</span><span class="sxs-lookup"><span data-stu-id="03181-147">Here is an example of the display:</span></span>
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  <span data-ttu-id="03181-148">此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有用户（ **AzureADUser** ），但仅显示每个用户的名称和位置（**选择 DisplayName、UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="03181-148">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription ( **Get-AzureADUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="03181-149">由于适用于 Microsoft 365 的 PowerShell 支持命令行管理程序语言，因此您可以进一步处理从**AzureADUser**命令获取的信息。</span><span class="sxs-lookup"><span data-stu-id="03181-149">Because PowerShell for Microsoft 365 supports a command shell language, you can further manipulate the information obtained from the **Get-AzureADUser** command.</span></span> <span data-ttu-id="03181-150">例如，您可能希望按照用户的位置对这些用户进行排序，将所有巴西用户组合在一起，将所有美国用户组合在一起，等等。下面是命令：</span><span class="sxs-lookup"><span data-stu-id="03181-150">For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="03181-151">下面展示了显示内容示例：</span><span class="sxs-lookup"><span data-stu-id="03181-151">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  <span data-ttu-id="03181-152">此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有用户，但仅显示每个用户的名称和位置，并首先按其位置以及它们的名称（ **Sort UsageLocation，DisplayName** ）对其进行排序。</span><span class="sxs-lookup"><span data-stu-id="03181-152">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="03181-p110">还可以使用其他筛选条件。例如，如果只想查看巴西用户的信息，请使用下面的命令：</span><span class="sxs-lookup"><span data-stu-id="03181-p110">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="03181-155">下面展示了显示内容示例：</span><span class="sxs-lookup"><span data-stu-id="03181-155">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="03181-156">此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的位置是巴西的所有用户（**其中 {$） \_ 。UsageLocation-eq "BR"}** ），然后显示每个用户的名称和位置。</span><span class="sxs-lookup"><span data-stu-id="03181-156">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="03181-157">**有关较大域的快速说明**</span><span class="sxs-lookup"><span data-stu-id="03181-157">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="03181-158">如果您的域非常大，有数万个用户，那么尝试此文章中介绍的某些示例可能会带来"限制"。</span><span class="sxs-lookup"><span data-stu-id="03181-158">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling."</span></span> <span data-ttu-id="03181-159">这说明，基于计算能力和可用网络带宽等因素，您每次尝试的操作有点多。</span><span class="sxs-lookup"><span data-stu-id="03181-159">That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time.</span></span> <span data-ttu-id="03181-160">因此，较大的组织可能希望将这些 PowerShell 中的某些 365 PowerShell 拆分成两个命令。</span><span class="sxs-lookup"><span data-stu-id="03181-160">Because of that, larger organizations might want to split some of these PowerShell for Microsoft 365 commands into two commands.</span></span> <span data-ttu-id="03181-161">例如，这一个命令将返回所有用户帐户，并显示每个用户的名称和位置。</span><span class="sxs-lookup"><span data-stu-id="03181-161">For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="03181-p112">这对于较小的域非常有用。但在大型组织中，您可能需要将此命令拆分为两个命令：一个命令用于将用户帐户信息存储在一个变量中，另一个命令用于显示所需信息。如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="03181-p112">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

<span data-ttu-id="03181-165">此 PowerShell 命令集的解释如下：</span><span class="sxs-lookup"><span data-stu-id="03181-165">The interpretation of this set of PowerShell commands is:</span></span>
- <span data-ttu-id="03181-166">获取当前 Microsoft 365 订阅中的所有用户，并将信息存储在名为 $x 的变量中（ **$x = AzureADUser** ）。</span><span class="sxs-lookup"><span data-stu-id="03181-166">Get all of the users in the current Microsoft 365 subscription and store the information in a variable named $x ( **$x = Get-AzureADUser** ).</span></span>
- <span data-ttu-id="03181-167">显示变量 $x 的内容，但只包含每个用户的用户名和地理位置 (**$x | Select DisplayName, UsageLocation**)。</span><span class="sxs-lookup"><span data-stu-id="03181-167">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a><span data-ttu-id="03181-168">Microsoft 365 具有仅可为 Microsoft 365 配置 PowerShell 的功能</span><span class="sxs-lookup"><span data-stu-id="03181-168">Microsoft 365 has features that you can only configure with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="03181-169">Microsoft 365 管理中心旨在提供对大多数用户适用的最常见或有意义的管理任务的访问权限。</span><span class="sxs-lookup"><span data-stu-id="03181-169">The Microsoft 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people.</span></span> <span data-ttu-id="03181-170">换句话说，Microsoft 365 管理中心的设计是为了使典型管理员可以使用该工具执行最常见的管理任务。</span><span class="sxs-lookup"><span data-stu-id="03181-170">In other words, the Microsoft 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks.</span></span> <span data-ttu-id="03181-171">通过此定义，意味着有一些任务无法使用 Microsoft 365 管理中心完成。</span><span class="sxs-lookup"><span data-stu-id="03181-171">By this definition, that means that there are some tasks that can't be completed by using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="03181-172">例如，Skype for Business Online 管理中心提供用于创建自定义会议邀请的几个选项：</span><span class="sxs-lookup"><span data-stu-id="03181-172">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![用于在 Skype for Business Online 管理中心内显示自定义会议邀请的示例。](media/o365-powershell-meeting-invitation.png)
  
<span data-ttu-id="03181-p114">借助这些设置，您可以为会议邀请添加少许个性化和专业化。但是，与仅创建自定义会议邀请相比，它对会议配置设置的帮助更多。例如，默认情况下，会议允许：</span><span class="sxs-lookup"><span data-stu-id="03181-p114">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="03181-177">匿名用户获取自动参与每个会议的权限。</span><span class="sxs-lookup"><span data-stu-id="03181-177">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="03181-178">与会者记录会议。</span><span class="sxs-lookup"><span data-stu-id="03181-178">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="03181-179">您组织中的所有用户在加入会议时被指定为演示者。</span><span class="sxs-lookup"><span data-stu-id="03181-179">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="03181-180">这些设置不是从 Skype for Business Online 管理中心提供。</span><span class="sxs-lookup"><span data-stu-id="03181-180">These settings are not available from the Skype for Business Online Admin center.</span></span> <span data-ttu-id="03181-181">但是，可以从 PowerShell for Microsoft 365 中控制它们。</span><span class="sxs-lookup"><span data-stu-id="03181-181">However, you can control them from PowerShell for Microsoft 365.</span></span> <span data-ttu-id="03181-182">下面是一个禁用这三项设置的命令：</span><span class="sxs-lookup"><span data-stu-id="03181-182">Here is a command that disables these three settings:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="03181-183">此命令要求必须安装 [Skype for Business Online PowerShell 模块](https://www.microsoft.com/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="03181-183">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="03181-184">此 PowerShell 命令的解释为：对于新的 Skype for Business Online 会议（ **get-csmeetingconfiguration** ）的设置，禁用允许匿名用户获取会议的自动进入（ **-AdmitAnonymousUsersByDefault $False** ），禁用与会者录制会议的能力（ **-AllowConferenceRecording $False** ），不要将组织中的所有用户指定为演示者（ **-DesignateAsPresenter "None"** ）。</span><span class="sxs-lookup"><span data-stu-id="03181-184">The interpretation of this PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="03181-185">如果改变了主意且希望还原这些默认设置（即启用所有设置），请运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="03181-185">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="03181-186">这仅是一个示例。</span><span class="sxs-lookup"><span data-stu-id="03181-186">This is just one example.</span></span> <span data-ttu-id="03181-187">还有其他一些原因，作为管理员，您需要熟悉为 Microsoft 365 命令运行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="03181-187">There are others, which is why you, as an administrator, need to be comfortable with running PowerShell for Microsoft 365 commands.</span></span>
  
## <a name="powershell-for-microsoft-365-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="03181-188">PowerShell for Microsoft 365 非常适合执行批量操作</span><span class="sxs-lookup"><span data-stu-id="03181-188">PowerShell for Microsoft 365 is great at carrying out bulk operations</span></span>

<span data-ttu-id="03181-189">以往，当你执行一个操作时，像 Microsoft 365 管理中心这样的可视界面非常有用。</span><span class="sxs-lookup"><span data-stu-id="03181-189">Historically, visual interfaces like the Microsoft 365 admin center are most valuable when you have a single operation to perform.</span></span> <span data-ttu-id="03181-190">例如，如果您需要禁用一个用户帐户，则可以使用 Microsoft 365 管理中心快速查找并清除复选框。</span><span class="sxs-lookup"><span data-stu-id="03181-190">For example, if you need to disable one user account, you can use the Microsoft 365 admin center to quickly locate and clear a checkbox.</span></span> <span data-ttu-id="03181-191">这可能比在 PowerShell 中执行类似的操作更简单。</span><span class="sxs-lookup"><span data-stu-id="03181-191">This can be simpler than performing a similar operation in PowerShell.</span></span>
  
<span data-ttu-id="03181-192">但是，如果您必须在一大范围的其他内容中更改许多内容或所选的内容，Microsoft 365 管理中心可能无法充分利用你的时间。</span><span class="sxs-lookup"><span data-stu-id="03181-192">But if you have to change many things or some selected things within a large set of other things, the Microsoft 365 admin center might not be the best use of your time.</span></span> <span data-ttu-id="03181-193">例如，如果您必须更改数以千计的电话号码前缀，或者您需要从所有 SharePoint Online 网站中删除特定用户（Ken Myer），那么如何在 Microsoft 365 管理中心中执行此操作？</span><span class="sxs-lookup"><span data-stu-id="03181-193">For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Microsoft 365 admin center?</span></span>
  
<span data-ttu-id="03181-194">关于后一个示例，你拥有数百个 SharePoint Online 网站，但甚至不知道 Ken Meyer 是哪个群组的成员。</span><span class="sxs-lookup"><span data-stu-id="03181-194">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member.</span></span> <span data-ttu-id="03181-195">这意味着您必须从 Microsoft 365 管理中心开始，然后对每个网站执行此过程：</span><span class="sxs-lookup"><span data-stu-id="03181-195">That means you'll have to start at the Microsoft 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="03181-196">单击网站的"URL"。</span><span class="sxs-lookup"><span data-stu-id="03181-196">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="03181-197">在"网站集属性"框中，单击"网站地址"链接以打开该网站。</span><span class="sxs-lookup"><span data-stu-id="03181-197">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="03181-198">在网站上，单击"共享"。</span><span class="sxs-lookup"><span data-stu-id="03181-198">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="03181-199">在"共享"对话框中，单击显示有权访问该网站的所有用户的链接：</span><span class="sxs-lookup"><span data-stu-id="03181-199">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![在 SharePoint Online 管理中心内查看 SharePoint Online 站点成员的示例。](media/o365-powershell-view-permissions.png)
  
5. <span data-ttu-id="03181-201">在"共享对象"对话框中，单击"高级"。</span><span class="sxs-lookup"><span data-stu-id="03181-201">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="03181-202">向下滚动用户列表，找到并选择 Ken Myer（假设他有权访问该网站），然后单击"删除用户权限"。</span><span class="sxs-lookup"><span data-stu-id="03181-202">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="03181-203">对于数百个网站来说，这可能需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="03181-203">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="03181-204">另一种方法是使用适用于 Microsoft 365 的 PowerShell 和以下命令从所有网站中删除 Ken Myer：</span><span class="sxs-lookup"><span data-stu-id="03181-204">The alternative is to use PowerShell for Microsoft 365 and the following command to remove Ken Myer from all of your sites:</span></span>
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="03181-205">此命令要求您安装[SharePoint Online PowerShell 模块](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="03181-205">This command requires that you install the [SharePoint Online PowerShell module](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="03181-206">此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有 SharePoint 网站（ **get-sposite** ），并为每个网站删除 Ken Meyer （该列表中的用户可以访问它）（ **ForEach {remove-get-spouser-site $） \_ 。Url-Person.loginname "kenmyer@litwareinc.com"}** ）。</span><span class="sxs-lookup"><span data-stu-id="03181-206">The interpretation of this PowerShell command is:  Get all of the SharePoint sites in the current Microsoft 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="03181-207">由于我们要告知 Microsoft 365 从每个站点中删除 Ken Meyer （包括用户不具有访问权限的站点），因此此命令的显示将显示他目前没有访问权限的那些站点的错误。</span><span class="sxs-lookup"><span data-stu-id="03181-207">Because we are telling Microsoft 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access.</span></span> <span data-ttu-id="03181-208">我们可以对此命令使用一个附加条件，使其仅从其登录列表中有 Key Meyer 的网站中删除他，但所列错误对网站本身没有任何坏处。</span><span class="sxs-lookup"><span data-stu-id="03181-208">We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves.</span></span> <span data-ttu-id="03181-209">此命令可能需要几分钟的时间才能运行数百个网站，而不是通过 Microsoft 365 管理中心工作数小时。</span><span class="sxs-lookup"><span data-stu-id="03181-209">This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="03181-p121">下面是另一个批量操作示例。使用此命令将新 SharePoint 管理员 Bonnie Kearney 添加到组织中的所有网站：</span><span class="sxs-lookup"><span data-stu-id="03181-p121">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="03181-212">此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有 SharePoint 网站，并为每个网站提供 Bonnie Kearney 访问，方法是将其登录名添加到网站的 "成员" 组（ **ForEach {get-spouser-site $ \_ 。Url-Person.loginname "bkearney@litwareinc.com"-Group "Members"}** ）。</span><span class="sxs-lookup"><span data-stu-id="03181-212">The interpretation of this PowerShell command is:  Get all of the SharePoint sites in the current Microsoft 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a><span data-ttu-id="03181-213">适用于 Microsoft 365 的 PowerShell 非常适合筛选数据</span><span class="sxs-lookup"><span data-stu-id="03181-213">PowerShell for Microsoft 365 is great at filtering data</span></span>

<span data-ttu-id="03181-214">Microsoft 365 管理中心提供了几种不同的筛选数据的方法，以便快速轻松地找到目标信息子集。</span><span class="sxs-lookup"><span data-stu-id="03181-214">The Microsoft 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information.</span></span> <span data-ttu-id="03181-215">例如，可以通过 Exchange 轻松筛选用户邮箱的几乎所有属性。</span><span class="sxs-lookup"><span data-stu-id="03181-215">For example, Exchange makes it easy to filter on practically any property of a user mailbox.</span></span> <span data-ttu-id="03181-216">例如，下面是居住在布卢明顿市的所有用户的邮箱列表：</span><span class="sxs-lookup"><span data-stu-id="03181-216">For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![在 Microsoft 365 管理中心中执行高级搜索的示例，用于居住在布卢明顿城市的所有用户的邮箱列表。](media/o365-powershell-advanced-search.png)
  
<span data-ttu-id="03181-p123">Exchange 管理中心还允许您组合筛选条件。例如，您可以查找居住在布卢明顿和在财务部门工作的所有用户的邮箱。</span><span class="sxs-lookup"><span data-stu-id="03181-p123">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="03181-p124">但是，在 Exchange 管理中心有一些操作限制。例如，也许您想要查找居住在布卢明顿或圣地亚哥的用户的邮箱或所有不居住在布卢明顿的用户的邮箱。</span><span class="sxs-lookup"><span data-stu-id="03181-p124">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="03181-222">对于适用于 Microsoft 365 的 PowerShell，你可以使用此命令获取居住在布卢明顿或圣地亚哥城市的所有人员的邮箱列表：</span><span class="sxs-lookup"><span data-stu-id="03181-222">With PowerShell for Microsoft 365, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="03181-223">下面展示了显示内容示例：</span><span class="sxs-lookup"><span data-stu-id="03181-223">Here is an example of the display:</span></span>
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  <span data-ttu-id="03181-224">此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有用户，这些用户在圣地亚哥或布卢明顿（**其中 {$）的城市中拥有邮箱。 \_RecipientTypeDetails-eq "UserMailbox"-和（$ \_ 。City-eq "圣地亚哥"-或 $ \_ 。City-eq "布卢明顿"）}** ），然后显示每个名称和城市（**选择 "DisplayName"、"city** "）。</span><span class="sxs-lookup"><span data-stu-id="03181-224">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="03181-225">若要列出居住在布卢明顿之外的用户的所有邮箱，可以运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="03181-225">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="03181-226">下面展示了显示内容示例：</span><span class="sxs-lookup"><span data-stu-id="03181-226">Here is an example of the display:</span></span>
  
```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  <span data-ttu-id="03181-227">此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的邮箱不位于布卢明顿城市（其中 {$）的所有用户\*\* \_ 。RecipientTypeDetails-eq "UserMailbox" 和 $ \_ 。City-ne "布卢明顿"}\*\* ），然后显示每个城市的姓名和城市。</span><span class="sxs-lookup"><span data-stu-id="03181-227">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="03181-228">您还可以在 PowerShell 筛选器中使用通配符，以匹配名称的一部分。</span><span class="sxs-lookup"><span data-stu-id="03181-228">You can also use wildcard characters in your PowerShell filters to match part of a name.</span></span> <span data-ttu-id="03181-229">例如，假设您正在查找某个用户帐户，但是只记得其姓氏是 Anderson，或也许是 Henderson 或 Jorgenson。</span><span class="sxs-lookup"><span data-stu-id="03181-229">For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="03181-230">您可以使用搜索工具在 Microsoft 365 管理中心内跟踪该用户并执行三种不同的搜索：</span><span class="sxs-lookup"><span data-stu-id="03181-230">You could track down that user in the Microsoft 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="03181-231">一次是搜索  *Anderson*</span><span class="sxs-lookup"><span data-stu-id="03181-231">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="03181-232">一次是搜索  *Henderson*</span><span class="sxs-lookup"><span data-stu-id="03181-232">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="03181-233">一次是搜索  *Jorgenson*</span><span class="sxs-lookup"><span data-stu-id="03181-233">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="03181-234">由于所有这三个名称都以 "儿子" 结束，因此您可以告知 PowerShell 显示姓名以 "儿子" 结尾的所有用户。</span><span class="sxs-lookup"><span data-stu-id="03181-234">Because all three of these names end in "son", you can tell PowerShell to display all the users whose name ends in "son".</span></span> <span data-ttu-id="03181-235">命令如下：</span><span class="sxs-lookup"><span data-stu-id="03181-235">Here is the command:</span></span>
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="03181-236">此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有用户，但使用仅列出姓氏以 "儿子" 结尾的用户的筛选器（ **-筛选器 "{LastName-like" \* 儿子 "}"** ）。</span><span class="sxs-lookup"><span data-stu-id="03181-236">The interpretation of this PowerShell command is: Get all of the users in the current Microsoft 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ).</span></span> <span data-ttu-id="03181-237">\*代表任意一组字符，这些字符是用户的姓的字母。</span><span class="sxs-lookup"><span data-stu-id="03181-237">The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="03181-238">适用于 Microsoft 365 的 PowerShell 可轻松打印或保存数据</span><span class="sxs-lookup"><span data-stu-id="03181-238">PowerShell for Microsoft 365 makes it easy to print or save data</span></span>

<span data-ttu-id="03181-239">Microsoft 365 管理中心允许你查看数据列表。</span><span class="sxs-lookup"><span data-stu-id="03181-239">The Microsoft 365 admin center lets you view lists of data.</span></span> <span data-ttu-id="03181-240">下面是显示已启用 Skype for Business Online 的用户列表的 Skype for Business Online 管理中心的一个示例：</span><span class="sxs-lookup"><span data-stu-id="03181-240">Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![用于显示已为 Skype for Business Online 启用的用户列表的 Skype for Business Online 管理中心的示例。](media/o365-powershell-lync-users.png)
  
<span data-ttu-id="03181-242">若要将该信息保存到一个文件，必须复制并将其粘贴到一个文档或 Excel。</span><span class="sxs-lookup"><span data-stu-id="03181-242">To save that information to a file, you must copy and paste it into a document or Excel.</span></span> <span data-ttu-id="03181-243">在任一种情况下，该副本可能需要附加的格式设置。</span><span class="sxs-lookup"><span data-stu-id="03181-243">In either case, the copy might require additional formatting.</span></span> <span data-ttu-id="03181-244">此外，Microsoft 365 管理中心不提供直接打印显示列表的方法。</span><span class="sxs-lookup"><span data-stu-id="03181-244">Additionally, the Microsoft 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="03181-245">幸运的是，您可以使用 PowerShell 不仅显示列表，还可以将其保存到可轻松导入 Excel 的文件中。</span><span class="sxs-lookup"><span data-stu-id="03181-245">Fortunately, you can use PowerShell to not only display the list, but save it to a file that can be easily imported into Excel.</span></span> <span data-ttu-id="03181-246">下面是一个将 Skype for Business Online 用户数据保存为逗号分隔值 (CSV) 文件（一个可轻松导入为 Excel 工作表中的表的文件）的示例命令：</span><span class="sxs-lookup"><span data-stu-id="03181-246">Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="03181-247">下面是显示的一个示例：</span><span class="sxs-lookup"><span data-stu-id="03181-247">Here is an example of the display:</span></span>
  
![保存到逗号分隔值 (CSV) 文件的 Skype for Business Online 用户数据的导入到 Excel 工作表的表示例。](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  <span data-ttu-id="03181-249">此 PowerShell 命令的解释为：在当前 Microsoft 365 订阅中获取所有 Skype for Business Online 用户（ **get-csonlineuser** ），仅获取用户名、UPN 和位置（**选择 DisplayName、UserPrincipalName、UsageLocation** ），然后将该信息保存在名为 C： logsSfBUsers.csv 的 CSV 文件中 \\ \\ （ **Export-CSV-Path "C： \\ logs \\SfBUsers.csv"-NoTypeInformation** ）。</span><span class="sxs-lookup"><span data-stu-id="03181-249">The interpretation of this PowerShell command is: Get all of the Skype for Business Online users in the current Microsoft 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="03181-p131">您可以使用选项将此列表另存为 XML 文件或 HTML 页。事实上，通过其他 PowerShell 命令，您可以将其直接保存为 Excel 文件，该文件具有所需的所有自定义格式。</span><span class="sxs-lookup"><span data-stu-id="03181-p131">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="03181-252">您还可以向 Windows 中的默认打印机发送直接显示列表的 PowerShell 命令的输出。</span><span class="sxs-lookup"><span data-stu-id="03181-252">You can also send the output of a PowerShell command that displays a list directly to the default printer in Windows.</span></span> <span data-ttu-id="03181-253">下面是一个示例命令：</span><span class="sxs-lookup"><span data-stu-id="03181-253">Here is an example command:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="03181-254">打印的文档如下所示：</span><span class="sxs-lookup"><span data-stu-id="03181-254">Here's what your printed document will look like:</span></span>
  
![将在 Windows 中直接列出的 PowerShell 命令输出到默认打印机的已打印文档的示例。](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  <span data-ttu-id="03181-256">此 PowerShell 命令的解释为：在当前 Microsoft 365 订阅中获取所有 Skype for Business Online 用户，仅获取用户名、UPN 和位置，然后将该信息发送到默认的 Windows 打印机（**传出打印机**）。</span><span class="sxs-lookup"><span data-stu-id="03181-256">The interpretation of this PowerShell command is:  Get all of the Skype for Business Online users in the current Microsoft 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="03181-257">打印的文档与 PowerShell 命令窗口中显示的简单格式相同，但在创建 PowerShell 命令以列出所需的内容后，只需添加 **|Out-打印机**到命令的末尾，以获取要从其进行工作的硬副本。</span><span class="sxs-lookup"><span data-stu-id="03181-257">The printed document has the same simple formatting as the display within the PowerShell command window, but once you have created a PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a><span data-ttu-id="03181-258">PowerShell for Microsoft 365 允许您跨服务器产品进行管理</span><span class="sxs-lookup"><span data-stu-id="03181-258">PowerShell for Microsoft 365 lets you manage across server products</span></span>

<span data-ttu-id="03181-259">组成 Microsoft 365 的不同组件设计为协同工作。</span><span class="sxs-lookup"><span data-stu-id="03181-259">The different components that make up Microsoft 365 are designed to work together.</span></span> <span data-ttu-id="03181-260">例如，假设您向 Microsoft 365 添加了一个新用户，在您执行此操作时，您可以将此类信息指定为用户的部门和电话号码。</span><span class="sxs-lookup"><span data-stu-id="03181-260">For example, suppose you add a new user to Microsoft 365 and, when you do, you specify such information as the user's department and phone number.</span></span> <span data-ttu-id="03181-261">如果使用任何 Microsoft 365 服务访问用户信息，则该信息将可用： Skype for Business Online、Exchange 或 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="03181-261">That information will then be available if you access the user's information using any of the Microsoft 365 services: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="03181-p134">不过，此规则适用于跨产品套件的一般信息。特定于产品的信息 - 例如，用户的 Exchange 邮箱的有关信息 - 通常无法跨套件提供。例如，如果您想要知道用户邮箱是否启用，该信息将仅可在 Exchange 管理中心获得。</span><span class="sxs-lookup"><span data-stu-id="03181-p134">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="03181-265">假设您要为您的所有用户生成显示以下信息的报告：</span><span class="sxs-lookup"><span data-stu-id="03181-265">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="03181-266">用户的显示名称</span><span class="sxs-lookup"><span data-stu-id="03181-266">The user's display name</span></span>
    
- <span data-ttu-id="03181-267">用户是否已获得适用于 Microsoft 365 的许可</span><span class="sxs-lookup"><span data-stu-id="03181-267">Whether the user is licensed for Microsoft 365</span></span>
    
- <span data-ttu-id="03181-268">用户的 Exchange 邮箱是否已启用</span><span class="sxs-lookup"><span data-stu-id="03181-268">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="03181-269">用户是否已启用 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="03181-269">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="03181-270">您当前无法使用 Microsoft 365 管理中心来轻松生成此类报告。</span><span class="sxs-lookup"><span data-stu-id="03181-270">You currently cannot use the Microsoft 365 admin center to easily produce such a report.</span></span> <span data-ttu-id="03181-271">相反，您必须创建单独的文档来存储信息（如 Excel 工作表），并从 Microsoft 365 管理中心获取所有用户名和许可信息，从 Exchange 管理中心获取邮箱信息，从 Skype for business Online 管理中心获取 Skype for Business Online 信息，然后逐份打印并合并该信息。</span><span class="sxs-lookup"><span data-stu-id="03181-271">Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Microsoft 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="03181-272">另一种方法是使用 PowerShell 脚本编译该报告。</span><span class="sxs-lookup"><span data-stu-id="03181-272">The alternative is to use a PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="03181-273">以下示例脚本会比到目前为止在本文中看到的命令更复杂。</span><span class="sxs-lookup"><span data-stu-id="03181-273">The following example script is more complicated than the commands you have seen so far in this article.</span></span> <span data-ttu-id="03181-274">但是，它展示了使用 PowerShell 创建信息视图的潜在可能性，这一点也非常困难。</span><span class="sxs-lookup"><span data-stu-id="03181-274">But, it shows the potential of using PowerShell to create views of information that are very difficult to do otherwise.</span></span> <span data-ttu-id="03181-275">下面是可以编译并显示所需列表的脚本：</span><span class="sxs-lookup"><span data-stu-id="03181-275">Here is the script that can compile and display the needed list:</span></span>
  
```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

<span data-ttu-id="03181-276">下面展示了显示内容示例：</span><span class="sxs-lookup"><span data-stu-id="03181-276">Here is an example of the display:</span></span>
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

<span data-ttu-id="03181-277">此 PowerShell 脚本的解释如下：</span><span class="sxs-lookup"><span data-stu-id="03181-277">The interpretation of this PowerShell script is:</span></span>  

- <span data-ttu-id="03181-278">获取当前 Microsoft 365 订阅中的所有用户，并将信息存储在名为 $x 的变量中（ **$x = AzureADUser** ）。</span><span class="sxs-lookup"><span data-stu-id="03181-278">Get all of the users in the current Microsoft 365 subscription and store the information in a variable named $x ( **$x = Get-AzureADUser** ).</span></span>
- <span data-ttu-id="03181-279">启动对 $x 变量中的所有用户运行的循环 (**foreach ($i in $x)**)。</span><span class="sxs-lookup"><span data-stu-id="03181-279">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="03181-280">定义 $y 变量，并将用户的邮箱信息存储在其中 (**$y = Get-Mailbox -Identity $i.UserPrincipalName**)。</span><span class="sxs-lookup"><span data-stu-id="03181-280">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="03181-281">将新属性添加到 IsMailBoxEnabled 用户信息，并将它设置为用户邮箱的 IsMailBoxEnabled 属性值(**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**)。</span><span class="sxs-lookup"><span data-stu-id="03181-281">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="03181-282">定义 $y 变量，并将用户的 Skype for Business Online 信息存储在其中 (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**)。</span><span class="sxs-lookup"><span data-stu-id="03181-282">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="03181-283">将新属性添加到 EnabledForSfB 用户信息，并将它设置为用户的 Skype for Business Online 信息的 Enabled 属性值 (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**)。</span><span class="sxs-lookup"><span data-stu-id="03181-283">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="03181-284">显示用户列表，但仅包括用户名、是否获得许可，以及两个指示是否已启用邮箱和是否已启用 Skype for Business Online 的新属性 (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**)。</span><span class="sxs-lookup"><span data-stu-id="03181-284">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="03181-285">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03181-285">See also</span></span>

[<span data-ttu-id="03181-286">Microsoft 365 的 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="03181-286">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="03181-287">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="03181-287">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="03181-288">在 Microsoft 365 中使用 Windows PowerShell 创建报告</span><span class="sxs-lookup"><span data-stu-id="03181-288">Use Windows PowerShell to create reports in Microsoft 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

