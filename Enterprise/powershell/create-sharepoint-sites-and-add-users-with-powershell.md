---
title: 使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要： 使用 Office 365 PowerShell，可以创建新的 SharePoint Online 网站，并将这些网站中添加用户和组。
ms.openlocfilehash: 61b9338469ed8d01abc76edbf14ed448c3ca00d3
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897165"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="32f35-103">使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户</span><span class="sxs-lookup"><span data-stu-id="32f35-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="32f35-104">**摘要：** 使用 Office 365 PowerShell 中创建新的 SharePoint Online 网站，然后这些网站中添加用户和组。</span><span class="sxs-lookup"><span data-stu-id="32f35-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="32f35-p101">当您使用 Office 365 PowerShell 中创建 SharePoint Online 网站和添加用户时，您可以快速反复执行任务比您可以在 Office 356 管理中心快得多。您还可以执行不能在 Office 356 管理中心执行的任务。</span><span class="sxs-lookup"><span data-stu-id="32f35-p101">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center. You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="32f35-107">准备工作</span><span class="sxs-lookup"><span data-stu-id="32f35-107">Before you begin</span></span>

<span data-ttu-id="32f35-p102">本主题中的过程需要连接到 SharePoint Online。有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="32f35-p102">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="32f35-110">步骤 1：使用 Office 365 PowerShell 创建新的网站集</span><span class="sxs-lookup"><span data-stu-id="32f35-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="32f35-p103">创建多个网站使用 Office 365 PowerShell 和使用示例代码提供和记事本创建的.csv 文件。对于本过程，您将替换占位符信息与您自己网站和租户特定的信息的括号中所示。此过程可创建单个文件和运行使用该文件的单个 Office 365 PowerShell 命令。这使可重复和可移植所执行的操作，并消除了许多，如果可以来自在 SharePoint Online Management Shell 中键入长命令的不是所有错误。有两个部分此过程。首先，您将创建.csv 文件，然后将引用使用 Office 365 PowerShell，将使用其内容来创建网站的.csv 文件。</span><span class="sxs-lookup"><span data-stu-id="32f35-p103">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad. For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information. This process lets you create a single file and run a single Office 365 PowerShell command that uses that file. This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell. There are two parts to this procedure. First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="32f35-p104">Office 365 PowerShell cmdlet 导入 .csv 文件并将其通过管道传递到大括号内的循环中，该循环将读取文件的第一行作为列标题。然后，Office 365 PowerShell cmdlet 循环访问剩余的记录，为每个记录创建一个新的网站集，并根据列标题指定网站集的属性。</span><span class="sxs-lookup"><span data-stu-id="32f35-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="32f35-119">创建 .csv 文件</span><span class="sxs-lookup"><span data-stu-id="32f35-119">Create a .csv file</span></span>

1. <span data-ttu-id="32f35-120">打开记事本，然后向其中粘贴以下文本块：</span><span class="sxs-lookup"><span data-stu-id="32f35-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="32f35-121">其中*租户*是您的租户的名称和*所有者*是用户向其租户的用户名称您想要授予的网站集主管理员角色。</span><span class="sxs-lookup"><span data-stu-id="32f35-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="32f35-122">（使用记事本更快批量替换时可以按 Ctrl + H。）</span><span class="sxs-lookup"><span data-stu-id="32f35-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="32f35-123">在您的桌面上将文件保存为**SiteCollections.csv**。</span><span class="sxs-lookup"><span data-stu-id="32f35-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="32f35-p105">您使用此或任何其他.csv 或 Windows PowerShell 脚本文件之前，它是很好的做法以确保没有额外的或非打印字符。在 Word 中，在功能区中打开该文件，单击段落图标以显示非打印字符。应该有无无关的非打印字符。例如，应该有超出文件的末尾最后一个没有段落标记。</span><span class="sxs-lookup"><span data-stu-id="32f35-p105">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="32f35-128">运行 Windows PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="32f35-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="32f35-129">在 Windows PowerShell 提示符处键入或复制并粘贴以下 cmdlet，然后按 Enter 键：</span><span class="sxs-lookup"><span data-stu-id="32f35-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="32f35-130">其中*MyAlias*等于您的用户别名。</span><span class="sxs-lookup"><span data-stu-id="32f35-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="32f35-p106">等待 Windows PowerShell 提示符重新出现。可能需要一两分钟。</span><span class="sxs-lookup"><span data-stu-id="32f35-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="32f35-133">在 Windows PowerShell 提示符处键入或复制并粘贴以下 cmdlet，然后按 Enter 键：</span><span class="sxs-lookup"><span data-stu-id="32f35-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="32f35-p107">请注意列表中的新网站集。您应该会看到以下网站集： **contosotest**、 **TeamSite01**、 **Blog01**和**Project01**</span><span class="sxs-lookup"><span data-stu-id="32f35-p107">Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="32f35-p108">就是这样。你已经使用所创建的 .csv 文件和一个 Windows PowerShell cmdlet 创建了多个网站集。现在，可以创建用户并将其分配给这些网站。</span><span class="sxs-lookup"><span data-stu-id="32f35-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="32f35-139">步骤 2：添加用户和组</span><span class="sxs-lookup"><span data-stu-id="32f35-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="32f35-p109">现在，您将创建用户并将其添加到网站集组中。然后，您将使用 .csv 文件批量上载新的组和用户。</span><span class="sxs-lookup"><span data-stu-id="32f35-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="32f35-142">下列步骤假定您已成功创建网站集 contosotest、TeamSite01、Blog01 和 Project01。</span><span class="sxs-lookup"><span data-stu-id="32f35-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="32f35-143">创建 .csv 和 .ps1 文件</span><span class="sxs-lookup"><span data-stu-id="32f35-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="32f35-144">打开记事本，然后向其中粘贴以下文本块：</span><span class="sxs-lookup"><span data-stu-id="32f35-144">Open Notepad, and paste the following text block into it:</span></span><br/>
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
<br/><span data-ttu-id="32f35-145">其中*租户*等于您的租户名称。</span><span class="sxs-lookup"><span data-stu-id="32f35-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="32f35-146">作为**GroupsAndPermissions.csv**保存到您的桌面的文件。</span><span class="sxs-lookup"><span data-stu-id="32f35-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="32f35-147">打开记事本的新实例，然后向其中粘贴以下文本块：</span><span class="sxs-lookup"><span data-stu-id="32f35-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

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
<br/><span data-ttu-id="32f35-148">其中*租户*等于您的租户名称和*用户名*等于现有用户的用户名。</span><span class="sxs-lookup"><span data-stu-id="32f35-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="32f35-149">作为**Users.csv**保存到您的桌面的文件。</span><span class="sxs-lookup"><span data-stu-id="32f35-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="32f35-150">打开记事本的新实例，然后向其中粘贴以下文本块：</span><span class="sxs-lookup"><span data-stu-id="32f35-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="32f35-151">其中 MyAlias 等于当前登录用户的用户名。</span><span class="sxs-lookup"><span data-stu-id="32f35-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="32f35-p110">将文件作为**UsersAndGroups.ps1**保存到您的桌面。这是一个简单的 Windows PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="32f35-p110">Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="32f35-154">现在，您可以运行 UsersAndGroup.ps1 脚本以向多个网站集中添加用户和组。</span><span class="sxs-lookup"><span data-stu-id="32f35-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="32f35-155">运行 UsersAndGroups.ps1 脚本</span><span class="sxs-lookup"><span data-stu-id="32f35-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="32f35-156">返回到 SharePoint Online 命令行管理程序。</span><span class="sxs-lookup"><span data-stu-id="32f35-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="32f35-157">在 Windows PowerShell 提示符下键入或复制并粘贴以下行，然后按 Enter 键：</span><span class="sxs-lookup"><span data-stu-id="32f35-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="32f35-158">在确认提示符处，按**Y**。</span><span class="sxs-lookup"><span data-stu-id="32f35-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="32f35-159">在 Windows PowerShell 提示符下键入或复制并粘贴以下内容，然后按 Enter 键：</span><span class="sxs-lookup"><span data-stu-id="32f35-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="32f35-160">其中*MyAlias*等于您的用户名。</span><span class="sxs-lookup"><span data-stu-id="32f35-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="32f35-p111">在继续之前，请等待提示符返回。首先，您将看到这些组在创建时的样子。然后，您将看到添加用户后的重复组列表。</span><span class="sxs-lookup"><span data-stu-id="32f35-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="32f35-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32f35-164">See also</span></span>

[<span data-ttu-id="32f35-165">连接到 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="32f35-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="32f35-166">管理 Office 365 PowerShell 中的 SharePoint Online 网站用户组</span><span class="sxs-lookup"><span data-stu-id="32f35-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="32f35-167">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="32f35-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="32f35-168">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="32f35-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

