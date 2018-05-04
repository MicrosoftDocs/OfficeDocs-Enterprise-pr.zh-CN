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
ms.openlocfilehash: 68be9ce3ef26cb46df6d43716c6719ffd9c172e2
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="df6ff-103">使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组</span><span class="sxs-lookup"><span data-stu-id="df6ff-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="df6ff-104">**摘要：**使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。</span><span class="sxs-lookup"><span data-stu-id="df6ff-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="df6ff-105">尽管您可以使用 Office 365 管理中心，您可以使用 Office 365 PowerShell 管理 SharePoint Online 网站组。</span><span class="sxs-lookup"><span data-stu-id="df6ff-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="df6ff-106">准备工作</span><span class="sxs-lookup"><span data-stu-id="df6ff-106">Before you begin</span></span>

<span data-ttu-id="df6ff-p101">本文中的过程需要连接到 SharePoint Online。有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="df6ff-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="df6ff-109">查看 SharePoint Online 与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="df6ff-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="df6ff-p102">在 SharePoint Online 管理中心具有用于管理网站用户组一些易于使用的方法。例如，假设您想要查找组和组成员，在https://litwareinc.sharepoint.com/sites/finance网站。下面是您需要对执行的操作：</span><span class="sxs-lookup"><span data-stu-id="df6ff-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the https://litwareinc.sharepoint.com/sites/finance site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="df6ff-113">从 Office 365 管理中心中，单击**资源** > **网站**，然后单击网站的 URL。</span><span class="sxs-lookup"><span data-stu-id="df6ff-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="df6ff-114">在网站集对话框中，单击**转到此网站**。</span><span class="sxs-lookup"><span data-stu-id="df6ff-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="df6ff-115">在网站页上单击**设置**图标 （位于页面的右上角），然后单击**网站设置**:</span><span class="sxs-lookup"><span data-stu-id="df6ff-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="df6ff-116">![SharePoint Online 网站设置](images/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="df6ff-116">![SharePoint Online site settings](images/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="df6ff-117">在网站设置页上单击**用户和权限**下的**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="df6ff-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="df6ff-118">然后对您要查看的下一个网站重复此过程。</span><span class="sxs-lookup"><span data-stu-id="df6ff-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="df6ff-119">若要使用 Office 365 PowerShell 获取组列表，请使用以下命令集：</span><span class="sxs-lookup"><span data-stu-id="df6ff-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="df6ff-120">有两种方式来运行在 SharePoint Online 命令行管理程序命令提示符中设置此命令：</span><span class="sxs-lookup"><span data-stu-id="df6ff-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>
- <span data-ttu-id="df6ff-p103">将命令复制到记事本 （或其他文本编辑器）、 修改 **$siteURL**变量的值、 选择的命令，然后将其粘贴到 SharePoint Online 命令行管理程序命令提示符处。PowerShell 执行操作时，将在停止 >> 提示。按 Enter 执行的每个命令。</span><span class="sxs-lookup"><span data-stu-id="df6ff-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a >> prompt. Press Enter to execute the for each command.</span></span></br>
- <span data-ttu-id="df6ff-p104">将命令复制到记事本 （或其他文本编辑器）、 修改 **$siteURL**变量的值，然后保存名称和.ps1 扩展名合适的文件夹中的此文本文件。下一步，指定其路径和文件名称从 SharePoint Online 命令行管理程序命令提示符运行脚本。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="df6ff-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example:</span></span></br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
<span data-ttu-id="df6ff-127">$x = Get-sposite foreach ($y 中 $x) {写主机 $y.Url-ForegroundColor"黄色"$z = Get-spositegroup-网站 $y.Url foreach ($ 在 $z) {$b = Get-spositegroup-网站 $y.Url-组 $a.Title 写主机 $b.Title-ForegroundColor"青色"$b |Select-object-ExpandProperty 用户写入-主机}}</span><span class="sxs-lookup"><span data-stu-id="df6ff-127">$x = Get-SPOSite foreach ($y in $x) { Write-Host $y.Url -ForegroundColor "Yellow" $z = Get-SPOSiteGroup -Site $y.Url foreach ($a in $z) { $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title Write-Host $b.Title -ForegroundColor "Cyan" $b | Select-Object -ExpandProperty Users Write-Host } }</span></span>
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

