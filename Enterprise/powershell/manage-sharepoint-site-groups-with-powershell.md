---
title: 使用 PowerShell 管理 SharePoint Online 网站用户组
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 在本文中，查找使用适用于 Microsoft 365 的 PowerShell 管理 SharePoint Online 网站用户组的过程。
ms.openlocfilehash: 5df2b57db4ac57aaf7905346d090ccde2d96a11c
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605898"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a><span data-ttu-id="be871-103">使用 PowerShell 管理 SharePoint Online 网站用户组</span><span class="sxs-lookup"><span data-stu-id="be871-103">Manage SharePoint Online site groups with PowerShell</span></span>

<span data-ttu-id="be871-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="be871-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="be871-105">虽然您可以使用 Microsoft 365 管理中心，但您也可以使用适用于 Microsoft 365 的 PowerShell 管理 SharePoint Online 网站用户组。</span><span class="sxs-lookup"><span data-stu-id="be871-105">Although you can use the Microsoft 365 admin center, you can also use PowerShell for Microsoft 365 to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="be871-106">准备工作</span><span class="sxs-lookup"><span data-stu-id="be871-106">Before you begin</span></span>

<span data-ttu-id="be871-107">本文中的过程要求您连接到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="be871-107">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="be871-108">有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="be871-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a><span data-ttu-id="be871-109">使用适用于 Microsoft 365 的 PowerShell 查看 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="be871-109">View SharePoint Online with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="be871-110">SharePoint Online 管理中心具有一些易于使用的方法来管理网站用户组。</span><span class="sxs-lookup"><span data-stu-id="be871-110">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="be871-111">例如，假设您想要查看网站的组和组成员 `https://litwareinc.sharepoint.com/sites/finance` 。</span><span class="sxs-lookup"><span data-stu-id="be871-111">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="be871-112">您必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="be871-112">Here's what you have to do to:</span></span>

1. <span data-ttu-id="be871-113">在 SharePoint 管理中心中，单击 "**活动网站**"，然后单击网站的 URL。</span><span class="sxs-lookup"><span data-stu-id="be871-113">From the SharePoint admin center, click **Active sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="be871-114">在 "网站" 页上，单击页面右上角 (的 "**设置**" 图标) ，然后单击 "**网站权限**"。</span><span class="sxs-lookup"><span data-stu-id="be871-114">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page), and then click **Site permissions**.</span></span>

<span data-ttu-id="be871-115">然后对您要查看的下一个网站重复此过程。</span><span class="sxs-lookup"><span data-stu-id="be871-115">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="be871-116">若要获取 PowerShell 为 Microsoft 365 的组列表，可以使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="be871-116">To get a list of the groups with PowerShell for Microsoft 365, you can use the following commands:</span></span>

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="be871-117">有两种方法可以在 SharePoint Online 命令行管理程序命令提示符中运行此命令集：</span><span class="sxs-lookup"><span data-stu-id="be871-117">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="be871-118">将命令复制到记事本中 (或其他文本编辑器) ，修改 **$siteURL**变量的值，选择命令，然后将其粘贴到 SharePoint Online 命令行管理程序命令提示符中。</span><span class="sxs-lookup"><span data-stu-id="be871-118">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="be871-119">执行此操作时，PowerShell 将在出现 **>>** 提示时停止。</span><span class="sxs-lookup"><span data-stu-id="be871-119">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="be871-120">按 Enter 以执行 `foreach` 命令。</span><span class="sxs-lookup"><span data-stu-id="be871-120">Press Enter to execute the `foreach` command.</span></span><br/>
- <span data-ttu-id="be871-121">将命令复制到记事本（或其他文本编辑器），修改 **$siteURL** 变量值，然后在合适的文件夹中使用一个名称和.ps1 扩展名保存该文本文件。</span><span class="sxs-lookup"><span data-stu-id="be871-121">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="be871-122">接下来，通过指定其路径和文件名从 SharePoint Online 命令行管理程序命令提示符处运行脚本。</span><span class="sxs-lookup"><span data-stu-id="be871-122">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="be871-123">下面是一个示例命令：</span><span class="sxs-lookup"><span data-stu-id="be871-123">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="be871-124">在这两种情况下，应该会看到类似下面的内容：</span><span class="sxs-lookup"><span data-stu-id="be871-124">In both cases, you should see something similar to this:</span></span>

![SharePoint Online 网站用户组](media/SPO-site-groups.png)

<span data-ttu-id="be871-126">这些是已为站点创建的所有组 `https://litwareinc.sharepoint.com/sites/finance` ，以及分配给这些组的所有用户。</span><span class="sxs-lookup"><span data-stu-id="be871-126">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="be871-127">组名为黄色，以帮助你从其成员中辨别组名。</span><span class="sxs-lookup"><span data-stu-id="be871-127">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="be871-128">作为另一个示例，下面是一个命令集，其中列出了所有 SharePoint Online 网站的组和所有组成员身份。</span><span class="sxs-lookup"><span data-stu-id="be871-128">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```powershell
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
    
## <a name="see-also"></a><span data-ttu-id="be871-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be871-129">See also</span></span>

[<span data-ttu-id="be871-130">连接到 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="be871-130">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="be871-131">使用 PowerShell 创建 SharePoint Online 网站并添加用户</span><span class="sxs-lookup"><span data-stu-id="be871-131">Create SharePoint Online sites and add users with PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="be871-132">使用 PowerShell 管理 SharePoint Online 用户和组</span><span class="sxs-lookup"><span data-stu-id="be871-132">Manage SharePoint Online users and groups with PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="be871-133">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="be871-133">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="be871-134">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="be871-134">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

