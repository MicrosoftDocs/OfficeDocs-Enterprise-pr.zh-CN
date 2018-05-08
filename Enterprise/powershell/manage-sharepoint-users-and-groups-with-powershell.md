---
title: 使用 Office 365 PowerShell 管理 SharePoint Online 用户和组
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要： 使用 Office 365 PowerShell 管理 SharePoint Online 用户、 组和网站。
ms.openlocfilehash: a04bf1538d6f56b760932b5be89b1953fcaa33d5
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="dca1a-103">使用 Office 365 PowerShell 管理 SharePoint Online 用户和组</span><span class="sxs-lookup"><span data-stu-id="dca1a-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="dca1a-104">**摘要：**使用 Office 365 PowerShell 管理 SharePoint Online 用户、 组和网站。</span><span class="sxs-lookup"><span data-stu-id="dca1a-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="dca1a-105">如果要处理的用户帐户或组的大型列表并希望更轻松的方式来管理 SharePoint Online 管理员，您可以使用 Office 365 PowerShell 中。</span><span class="sxs-lookup"><span data-stu-id="dca1a-105">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="dca1a-106">准备工作</span><span class="sxs-lookup"><span data-stu-id="dca1a-106">Before you begin</span></span>

<span data-ttu-id="dca1a-p101">本主题中的过程需要连接到 SharePoint Online。有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="dca1a-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="dca1a-109">获取网站、组和用户的列表</span><span class="sxs-lookup"><span data-stu-id="dca1a-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="dca1a-p102">开始管理用户和组之前，你需要获取网站、组和用户的列表。然后可以使用此信息完成本文中的示例。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="dca1a-112">获取网站列表</span><span class="sxs-lookup"><span data-stu-id="dca1a-112">Get a list of sites</span></span>

<span data-ttu-id="dca1a-113">使用此命令获取租户中的网站列表：</span><span class="sxs-lookup"><span data-stu-id="dca1a-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="dca1a-114">获取组列表</span><span class="sxs-lookup"><span data-stu-id="dca1a-114">Get a list of groups</span></span>

<span data-ttu-id="dca1a-115">使用此命令获取租户中的组列表：</span><span class="sxs-lookup"><span data-stu-id="dca1a-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="dca1a-116">获取用户列表</span><span class="sxs-lookup"><span data-stu-id="dca1a-116">Get a list of users</span></span>

<span data-ttu-id="dca1a-117">使用此命令获取租户中的用户列表：</span><span class="sxs-lookup"><span data-stu-id="dca1a-117">Get a list of the users in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="dca1a-118">将用户添加到网站集管理员组</span><span class="sxs-lookup"><span data-stu-id="dca1a-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="dca1a-p103">**设置 SPOUser**命令用于将用户添加到网站集管理员的网站集上的列表。这是语法的外观：</span><span class="sxs-lookup"><span data-stu-id="dca1a-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="dca1a-121">若要使用这些命令，替换替换所有内引号，包括 < 和 > 字符，并且正确的名称。</span><span class="sxs-lookup"><span data-stu-id="dca1a-121">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="dca1a-122">例如，此命令集添加 Opal Castillo (用户名称 opalc) 的网站集管理员列表 ContosoTest 网站集在 contoso1 租户上：</span><span class="sxs-lookup"><span data-stu-id="dca1a-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="dca1a-123">可以复制和将这些命令粘贴到记事本，将变量值 $tenant、 $site，和 $user 更改为实际值，从您的环境，然后粘贴到您的 SharePoint Online 命令行管理程序窗口以对运行它们。</span><span class="sxs-lookup"><span data-stu-id="dca1a-123">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="dca1a-124">将用户添加到其他网站集管理员组</span><span class="sxs-lookup"><span data-stu-id="dca1a-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="dca1a-125">在该任务中，我们将使用**Add-spouser**命令以将用户添加到网站集上 SharePoint 组。</span><span class="sxs-lookup"><span data-stu-id="dca1a-125">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="dca1a-126">例如，让我们添加 Glen 随时 (用户名称 glenr) 到在 contoso1 租户中的 ContosoTest 网站集审核员组：</span><span class="sxs-lookup"><span data-stu-id="dca1a-126">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="dca1a-127">创建网站集组</span><span class="sxs-lookup"><span data-stu-id="dca1a-127">Create a site collection group</span></span>

<span data-ttu-id="dca1a-128">使用**Set-spositegroup**命令创建新的 SharePoint 组并将其添加到 ContosoTest 网站集。</span><span class="sxs-lookup"><span data-stu-id="dca1a-128">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="dca1a-129">组属性，如权限级别，可以稍后进行更新使用**Set-spositegroup** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dca1a-129">Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="dca1a-130">例如，我们添加到在 contoso1 租户 Contoso 测试网站集的具有仅查看权限的审核员组：</span><span class="sxs-lookup"><span data-stu-id="dca1a-130">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="dca1a-131">从组中删除用户</span><span class="sxs-lookup"><span data-stu-id="dca1a-131">Remove users from a group</span></span>

<span data-ttu-id="dca1a-p104">有时必须从某个网站甚至是所有网站删除用户。员工可能从一个部门转移到另一个部门，或离开公司。在 UI 中可以很容易地对一个员工进行这样的操作，但如果是将整个部门从一个网站移动到另一个网站，这并非易事。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p104">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="dca1a-p105">但是通过使用 SharePoint Online 命令行管理程序和 CSV 文件，这，是快速和轻松。在此任务中，您将使用 Windows PowerShell 从网站集安全组中删除用户。然后您将使用 CSV 文件，并从不同站点中删除大量用户。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p105">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="dca1a-p106">我们将使用**Remove-spouser**命令从网站集组中删除单个 Office 365 用户，只需以便我们可以看到该命令的语法。下面是如何语法如下：</span><span class="sxs-lookup"><span data-stu-id="dca1a-p106">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="dca1a-140">例如，我们来移除 Bobby Overby 中 contoso1 租户 Contoso 测试网站集中的网站集审核员组：</span><span class="sxs-lookup"><span data-stu-id="dca1a-140">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="dca1a-p107">假定我们要将 Bobby 从他当前所在的所有组中删除。方法如下：</span><span class="sxs-lookup"><span data-stu-id="dca1a-p107">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="dca1a-p108">这只是一个示例。除非您真正需要从每个组，例如，如果用户离开公司中删除用户，不应运行此命令。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p108">This is just an example. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="dca1a-145">自动化管理大型用户和组列表</span><span class="sxs-lookup"><span data-stu-id="dca1a-145">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="dca1a-p109">若要将数量较大的帐户添加到 SharePoint 网站并向其授予权限，可以使用 Office 365 管理中心，单个 PowerShell 命令或 PowerShell CSV 文件。这些选项，该 CSV 文件是自动执行此任务的最快方式。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p109">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="dca1a-p110">基本过程是创建具有标题 （列） 对应的 Windows PowerShell 脚本所需的参数的 CSV 文件。可以轻松地在 Excel 中创建此类列表，然后将其导出为 CSV 文件。然后，您可以使用 Windows PowerShell 脚本循环访问记录 （行） 在 CSV 文件中，将用户添加到组和网站组。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p110">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="dca1a-p111">例如，我们创建一个 CSV 文件，以定义一组网站集、组和权限。接下来将创建一个 CSV 文件，将用户填充到组中。最后，要创建并运行一个简单的 Windows PowerShell 脚本，此脚本将创建并填充组。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p111">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="dca1a-154">第一个 CSV 文件将一个或多个组添加到一个或多个网站集，并具有以下结构：</span><span class="sxs-lookup"><span data-stu-id="dca1a-154">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="dca1a-155">标头：</span><span class="sxs-lookup"><span data-stu-id="dca1a-155">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="dca1a-156">项目：</span><span class="sxs-lookup"><span data-stu-id="dca1a-156">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="dca1a-157">示例文件如下所示：</span><span class="sxs-lookup"><span data-stu-id="dca1a-157">Here is an example file:</span></span>

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

<span data-ttu-id="dca1a-158">第二个 CSV 文件将一个或多个用户添加到一个或多个组，并具有以下结构：</span><span class="sxs-lookup"><span data-stu-id="dca1a-158">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="dca1a-159">标头：</span><span class="sxs-lookup"><span data-stu-id="dca1a-159">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="dca1a-160">项目：</span><span class="sxs-lookup"><span data-stu-id="dca1a-160">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="dca1a-161">示例文件如下所示：</span><span class="sxs-lookup"><span data-stu-id="dca1a-161">Here is an example file:</span></span>

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

<span data-ttu-id="dca1a-p112">下一步，您必须具有两个 CSV 文件保存到您的驱动器。下面是使用这两个 CSV 文件的示例命令添加权限和组成员身份：</span><span class="sxs-lookup"><span data-stu-id="dca1a-p112">For the next step, you must have the two CSV files saved to your drive. Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="dca1a-p113">脚本导入 CSV 文件内容，并使用的列中的值来填充**新建 SPOSiteGroup**和**Add-spouser**命令的参数。在我们的示例，我们将在驱动器 C 上将这保存到 theO365Admin 文件夹，但您可以将其保存所需的位置。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p113">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="dca1a-p114">现在，让我们使用同一个 CSV 文件的不同网站中删除大量的几组人员。下面是示例命令：</span><span class="sxs-lookup"><span data-stu-id="dca1a-p114">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is an example command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="dca1a-168">生成用户报告</span><span class="sxs-lookup"><span data-stu-id="dca1a-168">Generate user reports</span></span>

<span data-ttu-id="dca1a-p115">您可能想要获取一些网站的简单报告，并显示这些网站的用户、权限级别及其他属性。语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="dca1a-p115">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="dca1a-p116">这将获取以下三个站点的数据，并将它们写到本地驱动器上的文本文件。请注意，参数 – 追加到现有文件将添加新内容。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p116">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="dca1a-173">例如，我们在 Contoso1 租户的 ContosoTest、TeamSite01 和 Project01 网站上运行报告：</span><span class="sxs-lookup"><span data-stu-id="dca1a-173">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="dca1a-p117">请注意，我们必须更改仅 **$site**变量。**$Tenant**变量保留所有三个连续的命令通过其值。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p117">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="dca1a-p118">但是，如果要对每个网站进行此操作，应该怎么做？通过使用以下命令，您无需键入所有这些网站就可以进行操作：</span><span class="sxs-lookup"><span data-stu-id="dca1a-p118">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="dca1a-p119">此报告相当简单，，您可以添加更多代码创建更具体的报表或包含更多详细的信息报告。但这会使您了解如何使用 SharePoint Online Management Shell 管理 SharePoint Online 环境中的用户。</span><span class="sxs-lookup"><span data-stu-id="dca1a-p119">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="dca1a-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dca1a-180">See also</span></span>

[<span data-ttu-id="dca1a-181">连接到 SharePoint Online PowerShell 中</span><span class="sxs-lookup"><span data-stu-id="dca1a-181">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="dca1a-182">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="dca1a-182">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="dca1a-183">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="dca1a-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="dca1a-184">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="dca1a-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

