---
title: 使用 Office 365 PowerShell 管理 SharePoint Online 用户和组
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2019
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
description: 摘要：使用 Office 365 PowerShell 管理 SharePoint Online 用户、组和网站。
ms.openlocfilehash: e011946fa46455d1c1eba2bdff565bd55ec875bf
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747617"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="32da0-103">使用 Office 365 PowerShell 管理 SharePoint Online 用户和组</span><span class="sxs-lookup"><span data-stu-id="32da0-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

<span data-ttu-id="32da0-104">如果您是使用大型用户帐户或组列表的 SharePoint Online 管理员，并且想要更轻松地管理它们，则可以使用 Office 365 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="32da0-104">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="32da0-105">准备工作</span><span class="sxs-lookup"><span data-stu-id="32da0-105">Before you begin</span></span>

<span data-ttu-id="32da0-106">本主题中的过程要求您连接到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="32da0-106">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="32da0-107">有关说明，请参阅[连接到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="32da0-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="32da0-108">获取网站、组和用户的列表</span><span class="sxs-lookup"><span data-stu-id="32da0-108">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="32da0-p102">开始管理用户和组之前，你需要获取网站、组和用户的列表。然后可以使用此信息完成本文中的示例。</span><span class="sxs-lookup"><span data-stu-id="32da0-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="32da0-111">获取网站列表</span><span class="sxs-lookup"><span data-stu-id="32da0-111">Get a list of sites</span></span>

<span data-ttu-id="32da0-112">使用此命令获取租户中的网站列表：</span><span class="sxs-lookup"><span data-stu-id="32da0-112">Get a list of the sites in your tenant with this command:</span></span>

```powershell
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="32da0-113">获取组列表</span><span class="sxs-lookup"><span data-stu-id="32da0-113">Get a list of groups</span></span>

<span data-ttu-id="32da0-114">使用此命令获取租户中的组列表：</span><span class="sxs-lookup"><span data-stu-id="32da0-114">Get a list of the groups in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="32da0-115">获取用户列表</span><span class="sxs-lookup"><span data-stu-id="32da0-115">Get a list of users</span></span>

<span data-ttu-id="32da0-116">使用此命令获取租户中的用户列表：</span><span class="sxs-lookup"><span data-stu-id="32da0-116">Get a list of the users in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="32da0-117">将用户添加到网站集管理员组</span><span class="sxs-lookup"><span data-stu-id="32da0-117">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="32da0-118">可以使用 **Set-SPOUser** 命令将用户添加到网站集上的网站集管理员列表中。</span><span class="sxs-lookup"><span data-stu-id="32da0-118">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection.</span></span> <span data-ttu-id="32da0-119">语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="32da0-119">This is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="32da0-120">若要使用这些命令，请使用正确的名称替换引号内的所有内容，包括 < 和 > 字符。</span><span class="sxs-lookup"><span data-stu-id="32da0-120">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="32da0-121">例如，以下命令集将 Opal Castillo （用户名 opalc）添加到 contoso1 租赁中的 ContosoTest 网站集上的网站集管理员列表：</span><span class="sxs-lookup"><span data-stu-id="32da0-121">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="32da0-122">您可以将这些命令复制并粘贴到记事本中，将 $tenant、$site 和 $user 的变量值更改为您的环境中的实际值，然后将其粘贴到您的 SharePoint Online 命令行管理程序窗口中，以运行它们。</span><span class="sxs-lookup"><span data-stu-id="32da0-122">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-groups"></a><span data-ttu-id="32da0-123">将用户添加到其他网站集组</span><span class="sxs-lookup"><span data-stu-id="32da0-123">Add a user to other site collection groups</span></span>

<span data-ttu-id="32da0-124">在此任务中，我们将使用 **Add-SPOUser** 命令将用户添加到网站集上的 SharePoint 组。</span><span class="sxs-lookup"><span data-stu-id="32da0-124">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="32da0-125">例如，我们将 Glen Rife（用户名 glenr）添加到 contoso1 租赁下 ContosoTest 网站集的审核员组中：</span><span class="sxs-lookup"><span data-stu-id="32da0-125">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="32da0-126">创建网站集组</span><span class="sxs-lookup"><span data-stu-id="32da0-126">Create a site collection group</span></span>

<span data-ttu-id="32da0-127">您可以使用**remove-spositegroup**命令创建新的 SharePoint 组，并将其添加到 ContosoTest 网站集。</span><span class="sxs-lookup"><span data-stu-id="32da0-127">You use the **New-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="32da0-128">以后可使用 **Set-SPOSiteGroup** cmdlet 更新组属性（如权限级别）。</span><span class="sxs-lookup"><span data-stu-id="32da0-128">Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="32da0-129">例如，在 contoso1 租户中，让我们向审计员组添加对 Contoso Test 网站集的 "仅查看" 权限：</span><span class="sxs-lookup"><span data-stu-id="32da0-129">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="32da0-130">从组中删除用户</span><span class="sxs-lookup"><span data-stu-id="32da0-130">Remove users from a group</span></span>

<span data-ttu-id="32da0-p104">有时必须从某个网站甚至是所有网站删除用户。员工可能从一个部门转移到另一个部门，或离开公司。在 UI 中可以很容易地对一个员工进行这样的操作，但如果是将整个部门从一个网站移动到另一个网站，这并非易事。</span><span class="sxs-lookup"><span data-stu-id="32da0-p104">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="32da0-134">不过，通过使用 SharePoint Online 命令行管理程序和 CSV 文件，这是快速而简单的。</span><span class="sxs-lookup"><span data-stu-id="32da0-134">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="32da0-135">在本任务中，将使用 Windows PowerShell 将用户从一个网站集安全组删除。</span><span class="sxs-lookup"><span data-stu-id="32da0-135">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="32da0-136">然后使用 CSV 文件从不同的网站删除大量用户。</span><span class="sxs-lookup"><span data-stu-id="32da0-136">Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="32da0-137">我们将使用**get-spouser**命令从网站集组中删除单个 Office 365 用户，这样就可以看到命令语法。</span><span class="sxs-lookup"><span data-stu-id="32da0-137">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="32da0-138">语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="32da0-138">Here is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="32da0-139">例如，让我们删除 contoso1 租赁中 Contoso Test 网站集的网站集审计员组中的胡继 Overby：</span><span class="sxs-lookup"><span data-stu-id="32da0-139">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="32da0-140">假定我们要将 Bobby 从他当前所在的所有组中删除。</span><span class="sxs-lookup"><span data-stu-id="32da0-140">Suppose we wanted to remove Bobby from all the groups he is currently in.</span></span> <span data-ttu-id="32da0-141">方法如下：</span><span class="sxs-lookup"><span data-stu-id="32da0-141">Here is how we would do that:</span></span>

```powershell
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="32da0-142">这只是一个示例。</span><span class="sxs-lookup"><span data-stu-id="32da0-142">This is just an example.</span></span> <span data-ttu-id="32da0-143">除非确实需要将用户从每个组中删除（例如，用户离开公司），否则不应运行此命令。</span><span class="sxs-lookup"><span data-stu-id="32da0-143">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="32da0-144">自动化管理大型用户和组列表</span><span class="sxs-lookup"><span data-stu-id="32da0-144">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="32da0-145">若要向 SharePoint 网站添加大量帐户并向其授予权限，可以使用 Microsoft 365 管理中心、各个 PowerShell 命令或 PowerShell a CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="32da0-145">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="32da0-146">在这些选择中，CSV 文件是自动执行此任务的最快方法。</span><span class="sxs-lookup"><span data-stu-id="32da0-146">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="32da0-147">基本过程是，创建具有与 Windows PowerShell 脚本所需的参数对应的标头（列）的 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="32da0-147">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="32da0-148">您可以在 Excel 中轻松创建这样的列表，然后将其导出为 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="32da0-148">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="32da0-149">然后使用 Windows PowerShell 脚本循环访问 CSV 文件中的记录（行），将用户添加到组，将组添加到网站。</span><span class="sxs-lookup"><span data-stu-id="32da0-149">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="32da0-p111">例如，我们创建一个 CSV 文件，以定义一组网站集、组和权限。接下来将创建一个 CSV 文件，将用户填充到组中。最后，要创建并运行一个简单的 Windows PowerShell 脚本，此脚本将创建并填充组。</span><span class="sxs-lookup"><span data-stu-id="32da0-p111">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="32da0-153">第一个 CSV 文件将一个或多个组添加到一个或多个网站集，并具有以下结构：</span><span class="sxs-lookup"><span data-stu-id="32da0-153">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="32da0-154">邮件</span><span class="sxs-lookup"><span data-stu-id="32da0-154">Header:</span></span>

```powershell
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="32da0-155">Item</span><span class="sxs-lookup"><span data-stu-id="32da0-155">Item:</span></span>

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="32da0-156">示例文件如下所示：</span><span class="sxs-lookup"><span data-stu-id="32da0-156">Here is an example file:</span></span>

```powershell
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

<span data-ttu-id="32da0-157">第二个 CSV 文件将一个或多个用户添加到一个或多个组，并具有以下结构：</span><span class="sxs-lookup"><span data-stu-id="32da0-157">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="32da0-158">邮件</span><span class="sxs-lookup"><span data-stu-id="32da0-158">Header:</span></span>

```powershell
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="32da0-159">Item</span><span class="sxs-lookup"><span data-stu-id="32da0-159">Item:</span></span>

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="32da0-160">示例文件如下所示：</span><span class="sxs-lookup"><span data-stu-id="32da0-160">Here is an example file:</span></span>

```powershell
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

<span data-ttu-id="32da0-161">然后必须将这两个 CSV 文件保存到驱动器。</span><span class="sxs-lookup"><span data-stu-id="32da0-161">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="32da0-162">下面是使用这两个 CSV 文件并添加权限和组成员身份的示例命令：</span><span class="sxs-lookup"><span data-stu-id="32da0-162">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="32da0-163">该脚本将导入 CSV 文件内容，并使用列中的值填充**remove-spositegroup**和**get-spouser**命令的参数。</span><span class="sxs-lookup"><span data-stu-id="32da0-163">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="32da0-164">在我们的示例中，我们将它保存到驱动器 C 上的 theO365Admin 文件夹中，但你可以将其保存到您想要的任何位置。</span><span class="sxs-lookup"><span data-stu-id="32da0-164">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="32da0-165">下面我们来使用相同的 CSV 文件删除不同网站中多个组的一批人员。</span><span class="sxs-lookup"><span data-stu-id="32da0-165">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="32da0-166">下面是一个示例命令：</span><span class="sxs-lookup"><span data-stu-id="32da0-166">Here is an example command:</span></span>

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="32da0-167">生成用户报告</span><span class="sxs-lookup"><span data-stu-id="32da0-167">Generate user reports</span></span>

<span data-ttu-id="32da0-p115">您可能想要获取一些网站的简单报告，并显示这些网站的用户、权限级别及其他属性。语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="32da0-p115">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="32da0-170">将可以获取这三个网站的数据，并将这些数据写入本地驱动器上的文本文件。</span><span class="sxs-lookup"><span data-stu-id="32da0-170">This will grab the data for these three sites and write them to a text file on your local drive.</span></span> <span data-ttu-id="32da0-171">请注意，–Append 参数会将新内容添加到现有文件。</span><span class="sxs-lookup"><span data-stu-id="32da0-171">Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="32da0-172">例如，我们在 Contoso1 租户的 ContosoTest、TeamSite01 和 Project01 网站上运行报告：</span><span class="sxs-lookup"><span data-stu-id="32da0-172">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```powershell
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="32da0-173">请注意，我们只需要更改 **$site**变量。</span><span class="sxs-lookup"><span data-stu-id="32da0-173">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="32da0-174">**$Tenant**变量通过命令的所有三个运行保留其值。</span><span class="sxs-lookup"><span data-stu-id="32da0-174">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="32da0-p118">但是，如果要对每个网站进行此操作，应该怎么做？通过使用以下命令，您无需键入所有这些网站就可以进行操作：</span><span class="sxs-lookup"><span data-stu-id="32da0-p118">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="32da0-177">此报告相当简单，你可以添加更多代码以创建更多特定报告或包括更多详细信息的报告。</span><span class="sxs-lookup"><span data-stu-id="32da0-177">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="32da0-178">但这将使您了解如何使用 SharePoint Online 命令行管理程序来管理 SharePoint Online 环境中的用户。</span><span class="sxs-lookup"><span data-stu-id="32da0-178">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="32da0-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32da0-179">See also</span></span>

[<span data-ttu-id="32da0-180">连接到 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="32da0-180">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="32da0-181">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="32da0-181">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="32da0-182">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="32da0-182">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="32da0-183">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="32da0-183">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

