---
title: 使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要：使用 Office 365 PowerShell 创建新的 SharePoint Online 网站，然后将用户和组添加到这些网站。
ms.openlocfilehash: 17f3a6a6444ced647723f417145c6466dd8d284b
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077991"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="65ab2-103">使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户</span><span class="sxs-lookup"><span data-stu-id="65ab2-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="65ab2-104">**摘要：** 使用 Office 365 PowerShell 创建新的 SharePoint Online 网站，然后将用户和组添加到这些网站。</span><span class="sxs-lookup"><span data-stu-id="65ab2-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="65ab2-105">当您使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户时，您可以在 Office 356 管理中心中快速和重复执行任务快得多。</span><span class="sxs-lookup"><span data-stu-id="65ab2-105">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center.</span></span> <span data-ttu-id="65ab2-106">你还可以执行在 Office 356 管理中心中无法执行的任务。</span><span class="sxs-lookup"><span data-stu-id="65ab2-106">You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="65ab2-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="65ab2-107">Before you begin</span></span>

<span data-ttu-id="65ab2-108">本主题中的过程要求您连接到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="65ab2-108">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="65ab2-109">有关说明，请参阅[连接到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="65ab2-109">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="65ab2-110">步骤 1：使用 Office 365 PowerShell 创建新的网站集</span><span class="sxs-lookup"><span data-stu-id="65ab2-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="65ab2-111">使用 Office 365 PowerShell 和你使用提供的示例代码和记事本创建的 .csv 文件创建多个网站。</span><span class="sxs-lookup"><span data-stu-id="65ab2-111">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad.</span></span> <span data-ttu-id="65ab2-112">在此步骤中，你将使用你自己的网站和租户特定信息替换括号中显示的占位符信息。</span><span class="sxs-lookup"><span data-stu-id="65ab2-112">For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information.</span></span> <span data-ttu-id="65ab2-113">此过程允许您创建一个文件，并运行一个使用该文件的 Office 365 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="65ab2-113">This process lets you create a single file and run a single Office 365 PowerShell command that uses that file.</span></span> <span data-ttu-id="65ab2-114">这使得所采取的操作具有可重复性和可移植性，并可以减少许多（如果不是全部）因向 SharePoint Online 命令行管理程序键入长命令而导致的错误。</span><span class="sxs-lookup"><span data-stu-id="65ab2-114">This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell.</span></span> <span data-ttu-id="65ab2-115">此步骤包括两个部分。</span><span class="sxs-lookup"><span data-stu-id="65ab2-115">There are two parts to this procedure.</span></span> <span data-ttu-id="65ab2-116">首先，你要创建一个 .csv 文件，然后使用 Office 365 PowerShell 引用该 .csv 文件，从而利用该文件的内容来创建网站。</span><span class="sxs-lookup"><span data-stu-id="65ab2-116">First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="65ab2-p104">Office 365 PowerShell cmdlet 导入 .csv 文件并将其通过管道传递到大括号内的循环中，该循环将读取文件的第一行作为列标题。然后，Office 365 PowerShell cmdlet 循环访问剩余的记录，为每个记录创建一个新的网站集，并根据列标题指定网站集的属性。</span><span class="sxs-lookup"><span data-stu-id="65ab2-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="65ab2-119">创建 .csv 文件</span><span class="sxs-lookup"><span data-stu-id="65ab2-119">Create a .csv file</span></span>

1. <span data-ttu-id="65ab2-120">打开记事本，然后向其中粘贴以下文本块：</span><span class="sxs-lookup"><span data-stu-id="65ab2-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="65ab2-121">其中*租户*是你的租户的名称，*所有者*是你要向其授予主网站集管理员角色的租户上的用户用户名。</span><span class="sxs-lookup"><span data-stu-id="65ab2-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="65ab2-122">（当使用记事本以更快地批量替换时，可以按 Ctrl + H。）</span><span class="sxs-lookup"><span data-stu-id="65ab2-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="65ab2-123">将文件以**SiteCollections**的形式保存在桌面上。</span><span class="sxs-lookup"><span data-stu-id="65ab2-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="65ab2-124">在使用这个或任何其他 .csv 或 WindowsPowerShell 脚本文件之前，最好先确保没有多余的或者非打印字符。</span><span class="sxs-lookup"><span data-stu-id="65ab2-124">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters.</span></span> <span data-ttu-id="65ab2-125">在 Word 中打开该文件，在功能区单击“段落”图标以显示非打印字符。</span><span class="sxs-lookup"><span data-stu-id="65ab2-125">Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters.</span></span> <span data-ttu-id="65ab2-126">应该没有多余的非打印字符。</span><span class="sxs-lookup"><span data-stu-id="65ab2-126">There should be no extraneous nonprinting characters.</span></span> <span data-ttu-id="65ab2-127">例如，除了文件末尾的最后一个段落标记之外，应该没有其他任何段落标记。</span><span class="sxs-lookup"><span data-stu-id="65ab2-127">For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="65ab2-128">运行 Windows PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="65ab2-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="65ab2-129">在 Windows PowerShell 提示符处键入或复制并粘贴以下 cmdlet，然后按 Enter 键：</span><span class="sxs-lookup"><span data-stu-id="65ab2-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="65ab2-130">其中， *MyAlias*等于您的用户别名。</span><span class="sxs-lookup"><span data-stu-id="65ab2-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="65ab2-p106">等待 Windows PowerShell 提示符重新出现。可能需要一两分钟。</span><span class="sxs-lookup"><span data-stu-id="65ab2-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="65ab2-133">在 Windows PowerShell 提示符处键入或复制并粘贴以下 cmdlet，然后按 Enter 键：</span><span class="sxs-lookup"><span data-stu-id="65ab2-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="65ab2-134">请注意列表中的新网站集。</span><span class="sxs-lookup"><span data-stu-id="65ab2-134">Note the new site collections in the list.</span></span> <span data-ttu-id="65ab2-135">您应该会看到以下网站集： **contosotest**、 **TeamSite01**、 **Blog01**和**Project01**</span><span class="sxs-lookup"><span data-stu-id="65ab2-135">You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="65ab2-p108">就是这样。你已经使用所创建的 .csv 文件和一个 Windows PowerShell cmdlet 创建了多个网站集。现在，可以创建用户并将其分配给这些网站。</span><span class="sxs-lookup"><span data-stu-id="65ab2-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="65ab2-139">步骤 2：添加用户和组</span><span class="sxs-lookup"><span data-stu-id="65ab2-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="65ab2-p109">现在，您将创建用户并将其添加到网站集组中。然后，您将使用 .csv 文件批量上载新的组和用户。</span><span class="sxs-lookup"><span data-stu-id="65ab2-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="65ab2-142">下列步骤假定您已成功创建网站集 contosotest、TeamSite01、Blog01 和 Project01。</span><span class="sxs-lookup"><span data-stu-id="65ab2-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="65ab2-143">创建 .csv 和 .ps1 文件</span><span class="sxs-lookup"><span data-stu-id="65ab2-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="65ab2-144">打开记事本，然后向其中粘贴以下文本块：</span><span class="sxs-lookup"><span data-stu-id="65ab2-144">Open Notepad, and paste the following text block into it:</span></span><br/>
```
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/><span data-ttu-id="65ab2-145">其中*租户*等于你的租户名称。</span><span class="sxs-lookup"><span data-stu-id="65ab2-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="65ab2-146">将文件以**GroupsAndPermissions**的形式保存到您的桌面。</span><span class="sxs-lookup"><span data-stu-id="65ab2-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="65ab2-147">打开记事本的新实例，然后向其中粘贴以下文本块：</span><span class="sxs-lookup"><span data-stu-id="65ab2-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/><span data-ttu-id="65ab2-148">其中*租户*等于租户名称，*用户名*等于现有用户的用户名。</span><span class="sxs-lookup"><span data-stu-id="65ab2-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="65ab2-149">将文件以**Users. .csv**的形式保存到桌面。</span><span class="sxs-lookup"><span data-stu-id="65ab2-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="65ab2-150">打开记事本的新实例，然后向其中粘贴以下文本块：</span><span class="sxs-lookup"><span data-stu-id="65ab2-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="65ab2-151">其中，MyAlias 等于当前登录的用户的用户名。</span><span class="sxs-lookup"><span data-stu-id="65ab2-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="65ab2-152">将文件以**UsersAndGroups**的形式保存到您的桌面。</span><span class="sxs-lookup"><span data-stu-id="65ab2-152">Save the file to your desktop as **UsersAndGroups.ps1**.</span></span> <span data-ttu-id="65ab2-153">这是一个简单的 Windows PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="65ab2-153">This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="65ab2-154">现在，您可以运行 UsersAndGroup.ps1 脚本以向多个网站集中添加用户和组。</span><span class="sxs-lookup"><span data-stu-id="65ab2-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="65ab2-155">运行 UsersAndGroups.ps1 脚本</span><span class="sxs-lookup"><span data-stu-id="65ab2-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="65ab2-156">返回到 SharePoint Online 命令行管理程序。</span><span class="sxs-lookup"><span data-stu-id="65ab2-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="65ab2-157">在 Windows PowerShell 提示符下键入或复制并粘贴以下行，然后按 Enter 键：</span><span class="sxs-lookup"><span data-stu-id="65ab2-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="65ab2-158">在确认提示符处，按 " **Y**"。</span><span class="sxs-lookup"><span data-stu-id="65ab2-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="65ab2-159">在 Windows PowerShell 提示符下键入或复制并粘贴以下内容，然后按 Enter 键：</span><span class="sxs-lookup"><span data-stu-id="65ab2-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="65ab2-160">其中， *MyAlias*等于您的用户名。</span><span class="sxs-lookup"><span data-stu-id="65ab2-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="65ab2-p111">在继续之前，请等待提示符返回。首先，您将看到这些组在创建时的样子。然后，您将看到添加用户后的重复组列表。</span><span class="sxs-lookup"><span data-stu-id="65ab2-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="65ab2-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65ab2-164">See also</span></span>

[<span data-ttu-id="65ab2-165">连接到 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="65ab2-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="65ab2-166">管理 SharePoint Online 网站组 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="65ab2-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="65ab2-167">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="65ab2-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="65ab2-168">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="65ab2-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

