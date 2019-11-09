---
title: 使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
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
description: 摘要：使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。
ms.openlocfilehash: eedbfbecea0f488b96cfe7a87a2b4851352f4fac
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077981"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="a7f34-103">使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组</span><span class="sxs-lookup"><span data-stu-id="a7f34-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="a7f34-104">**摘要：** 使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。</span><span class="sxs-lookup"><span data-stu-id="a7f34-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="a7f34-105">虽然您可以使用 Microsoft 365 管理中心，但您也可以使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。</span><span class="sxs-lookup"><span data-stu-id="a7f34-105">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="a7f34-106">准备工作</span><span class="sxs-lookup"><span data-stu-id="a7f34-106">Before you begin</span></span>

<span data-ttu-id="a7f34-107">本文中的过程要求您连接到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="a7f34-107">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="a7f34-108">有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="a7f34-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="a7f34-109">使用 Office 365 PowerShell 查看 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a7f34-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="a7f34-110">SharePoint Online 管理中心具有一些易于使用的方法来管理网站用户组。</span><span class="sxs-lookup"><span data-stu-id="a7f34-110">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="a7f34-111">例如，假设您想要查看`https://litwareinc.sharepoint.com/sites/finance`网站的组和组成员。</span><span class="sxs-lookup"><span data-stu-id="a7f34-111">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="a7f34-112">以下是需要执行的操作：</span><span class="sxs-lookup"><span data-stu-id="a7f34-112">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="a7f34-113">在 Microsoft 365 管理中心，单击 "**资源** > **网站**"，然后单击网站的 URL。</span><span class="sxs-lookup"><span data-stu-id="a7f34-113">From the Microsoft 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="a7f34-114">在“网站集”对话框中，单击“**转到此网站**”。</span><span class="sxs-lookup"><span data-stu-id="a7f34-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="a7f34-115">在网站页上，单击“**设置**”图标（位于页面的右上角），然后单击“**网站设置**”：</span><span class="sxs-lookup"><span data-stu-id="a7f34-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span><br/>
<span data-ttu-id="a7f34-116">![SharePoint Online 网站设置](media/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="a7f34-116">![SharePoint Online site settings](media/spo-site-settings.png)</span></span><br/>
4. <span data-ttu-id="a7f34-117">在“网站设置”页上的“**用户和权限**”下单击“**网站权限**”。</span><span class="sxs-lookup"><span data-stu-id="a7f34-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="a7f34-118">然后对您要查看的下一个网站重复此过程。</span><span class="sxs-lookup"><span data-stu-id="a7f34-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="a7f34-119">若要使用 Office 365 PowerShell 获取组列表，请使用以下命令集：</span><span class="sxs-lookup"><span data-stu-id="a7f34-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="a7f34-120">有两种方法可以在 SharePoint Online 命令行管理程序命令提示符中运行此命令集：</span><span class="sxs-lookup"><span data-stu-id="a7f34-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="a7f34-121">将命令复制到记事本（或其他文本编辑器）中，修改 **$siteURL**变量的值，选择命令，然后将其粘贴到 SharePoint Online 命令行管理程序命令提示符中。</span><span class="sxs-lookup"><span data-stu-id="a7f34-121">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="a7f34-122">执行此操作时，PowerShell 将在出现**>>** 提示时停止。</span><span class="sxs-lookup"><span data-stu-id="a7f34-122">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="a7f34-123">按 Enter 键执行 **foreach** 命令。</span><span class="sxs-lookup"><span data-stu-id="a7f34-123">Press Enter to execute the **foreach** command.</span></span><br/>
- <span data-ttu-id="a7f34-124">将命令复制到记事本（或其他文本编辑器），修改 **$siteURL** 变量值，然后在合适的文件夹中使用一个名称和.ps1 扩展名保存该文本文件。</span><span class="sxs-lookup"><span data-stu-id="a7f34-124">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="a7f34-125">接下来，通过指定其路径和文件名从 SharePoint Online 命令行管理程序命令提示符处运行脚本。</span><span class="sxs-lookup"><span data-stu-id="a7f34-125">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="a7f34-126">下面是一个示例命令：</span><span class="sxs-lookup"><span data-stu-id="a7f34-126">Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="a7f34-127">在这两种情况下，应该会看到类似下面的内容：</span><span class="sxs-lookup"><span data-stu-id="a7f34-127">In both cases, you should see something similar to this:</span></span>

![SharePoint Online 网站用户组](media/SPO-site-groups.png)

<span data-ttu-id="a7f34-129">这些是已为站点`https://litwareinc.sharepoint.com/sites/finance`创建的所有组，以及分配给这些组的所有用户。</span><span class="sxs-lookup"><span data-stu-id="a7f34-129">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="a7f34-130">组名为黄色，以帮助你从其成员中辨别组名。</span><span class="sxs-lookup"><span data-stu-id="a7f34-130">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="a7f34-131">作为另一个示例，下面是一个命令集，其中列出了所有 SharePoint Online 网站的组和所有组成员身份。</span><span class="sxs-lookup"><span data-stu-id="a7f34-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="a7f34-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7f34-132">See also</span></span>

[<span data-ttu-id="a7f34-133">连接到 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7f34-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="a7f34-134">使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户</span><span class="sxs-lookup"><span data-stu-id="a7f34-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="a7f34-135">使用 Office 365 PowerShell 管理 SharePoint Online 用户和组</span><span class="sxs-lookup"><span data-stu-id="a7f34-135">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="a7f34-136">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="a7f34-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a7f34-137">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="a7f34-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

