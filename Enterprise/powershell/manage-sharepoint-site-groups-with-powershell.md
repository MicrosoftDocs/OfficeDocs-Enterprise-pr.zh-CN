---
title: 使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要： 使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。
ms.openlocfilehash: 881e67b7eb2d8bb5e04f83e28569aa54341d16b9
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="5f954-103">使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组</span><span class="sxs-lookup"><span data-stu-id="5f954-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="5f954-104">**摘要：**使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。</span><span class="sxs-lookup"><span data-stu-id="5f954-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="5f954-105">尽管您可以使用 Office 365 管理中心，您可以使用 Office 365 PowerShell 管理 SharePoint Online 网站组。</span><span class="sxs-lookup"><span data-stu-id="5f954-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="5f954-106">准备工作</span><span class="sxs-lookup"><span data-stu-id="5f954-106">Before you begin</span></span>

<span data-ttu-id="5f954-p101">本文中的过程需要连接到 SharePoint Online。有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="5f954-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="5f954-109">查看 SharePoint Online 与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f954-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="5f954-p102">在 SharePoint Online 管理中心具有用于管理网站用户组一些易于使用的方法。例如，假设您想要查看组和组成员，https\://litwareinc.sharepoint.com/sites/finance 网站。下面是您需要对执行的操作：</span><span class="sxs-lookup"><span data-stu-id="5f954-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the https\://litwareinc.sharepoint.com/sites/finance site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="5f954-113">从 Office 365 管理中心中，单击**资源** > **网站**，然后单击网站的 URL。</span><span class="sxs-lookup"><span data-stu-id="5f954-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="5f954-114">在网站集对话框中，单击**转到此网站**。</span><span class="sxs-lookup"><span data-stu-id="5f954-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="5f954-115">在网站页上单击**设置**图标 （位于页面的右上角），然后单击**网站设置**:</span><span class="sxs-lookup"><span data-stu-id="5f954-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="5f954-116">![SharePoint Online 网站设置](images/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="5f954-116">![SharePoint Online site settings](images/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="5f954-117">在网站设置页上单击**用户和权限**下的**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="5f954-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="5f954-118">然后对您要查看的下一个网站重复此过程。</span><span class="sxs-lookup"><span data-stu-id="5f954-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="5f954-119">若要使用 Office 365 PowerShell 获取组列表，请使用以下命令集：</span><span class="sxs-lookup"><span data-stu-id="5f954-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="5f954-120">有两种方式来运行在 SharePoint Online 命令行管理程序命令提示符中设置此命令：</span><span class="sxs-lookup"><span data-stu-id="5f954-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="5f954-p103">将命令复制到记事本 （或其他文本编辑器）、 修改 **$siteURL**变量的值、 选择的命令，然后将其粘贴到 SharePoint Online 命令行管理程序命令提示符处。PowerShell 执行操作时，将在停止**>>** 提示。按 Enter 执行**foreach**命令。</span><span class="sxs-lookup"><span data-stu-id="5f954-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a **>>** prompt. Press Enter to execute the **foreach** command.</span></span></br>
- <span data-ttu-id="5f954-p104">将命令复制到记事本 （或其他文本编辑器）、 修改 **$siteURL**变量的值，然后保存名称和.ps1 扩展名合适的文件夹中的此文本文件。下一步，指定其路径和文件名称从 SharePoint Online 命令行管理程序命令提示符运行脚本。下面是示例命令：</span><span class="sxs-lookup"><span data-stu-id="5f954-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="5f954-127">在这两种情况下，应该会看到类似下面的内容：</span><span class="sxs-lookup"><span data-stu-id="5f954-127">In both cases, you should see something similar to this:</span></span>

![SharePoint Online 网站用户组](images/SPO-site-groups.png)

<span data-ttu-id="5f954-p105">这是已为网站 https 创建的所有组\:/ / litwareinc.sharepoint.com/sites/finance，以及所有用户分配给这些组。组名称是黄色可帮助您从其成员的单独的组名称。</span><span class="sxs-lookup"><span data-stu-id="5f954-p105">These are all the groups that have been created for the site https\://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="5f954-131">又如，下面是一个命令集，列出的组和所有的组成员身份，所有的 SharePoint Online 网站。</span><span class="sxs-lookup"><span data-stu-id="5f954-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a><span data-ttu-id="5f954-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f954-132">See also</span></span>

[<span data-ttu-id="5f954-133">连接到 SharePoint Online PowerShell 中</span><span class="sxs-lookup"><span data-stu-id="5f954-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="5f954-134">创建 SharePoint Online 网站和使用 Office 365 PowerShell 中添加用户</span><span class="sxs-lookup"><span data-stu-id="5f954-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="5f954-135">使用 Office 365 PowerShell 管理 SharePoint Online 用户和组</span><span class="sxs-lookup"><span data-stu-id="5f954-135">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="5f954-136">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="5f954-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5f954-137">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="5f954-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

