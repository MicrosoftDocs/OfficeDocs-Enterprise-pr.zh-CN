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
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理 SharePoint Online 用户和组

 **摘要：**使用 Office 365 PowerShell 管理 SharePoint Online 用户、 组和网站。

如果要处理的用户帐户或组的大型列表并希望更轻松的方式来管理 SharePoint Online 管理员，您可以使用 Office 365 PowerShell 中。 

## <a name="before-you-begin"></a>准备工作

本主题中的过程需要连接到 SharePoint Online。有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>获取网站、组和用户的列表

开始管理用户和组之前，你需要获取网站、组和用户的列表。然后可以使用此信息完成本文中的示例。

### <a name="get-a-list-of-sites"></a>获取网站列表

使用此命令获取租户中的网站列表：

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>获取组列表

使用此命令获取租户中的组列表：

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a>获取用户列表

使用此命令获取租户中的用户列表：

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>将用户添加到网站集管理员组

**设置 SPOUser**命令用于将用户添加到网站集管理员的网站集上的列表。这是语法的外观：

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

若要使用这些命令，替换替换所有内引号，包括 < 和 > 字符，并且正确的名称。

例如，此命令集添加 Opal Castillo (用户名称 opalc) 的网站集管理员列表 ContosoTest 网站集在 contoso1 租户上：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

可以复制和将这些命令粘贴到记事本，将变量值 $tenant、 $site，和 $user 更改为实际值，从您的环境，然后粘贴到您的 SharePoint Online 命令行管理程序窗口以对运行它们。

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>将用户添加到其他网站集管理员组

在该任务中，我们将使用**Add-spouser**命令以将用户添加到网站集上 SharePoint 组。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

例如，让我们添加 Glen 随时 (用户名称 glenr) 到在 contoso1 租户中的 ContosoTest 网站集审核员组：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>创建网站集组

使用**Set-spositegroup**命令创建新的 SharePoint 组并将其添加到 ContosoTest 网站集。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
组属性，如权限级别，可以稍后进行更新使用**Set-spositegroup** cmdlet。

例如，我们添加到在 contoso1 租户 Contoso 测试网站集的具有仅查看权限的审核员组：

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>从组中删除用户

有时必须从某个网站甚至是所有网站删除用户。员工可能从一个部门转移到另一个部门，或离开公司。在 UI 中可以很容易地对一个员工进行这样的操作，但如果是将整个部门从一个网站移动到另一个网站，这并非易事。

但是通过使用 SharePoint Online 命令行管理程序和 CSV 文件，这，是快速和轻松。在此任务中，您将使用 Windows PowerShell 从网站集安全组中删除用户。然后您将使用 CSV 文件，并从不同站点中删除大量用户。 

我们将使用**Remove-spouser**命令从网站集组中删除单个 Office 365 用户，只需以便我们可以看到该命令的语法。下面是如何语法如下：

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
例如，我们来移除 Bobby Overby 中 contoso1 租户 Contoso 测试网站集中的网站集审核员组：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

假定我们要将 Bobby 从他当前所在的所有组中删除。方法如下：

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> 这只是一个示例。除非您真正需要从每个组，例如，如果用户离开公司中删除用户，不应运行此命令。

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>自动化管理大型用户和组列表

若要将数量较大的帐户添加到 SharePoint 网站并向其授予权限，可以使用 Office 365 管理中心，单个 PowerShell 命令或 PowerShell CSV 文件。这些选项，该 CSV 文件是自动执行此任务的最快方式。

基本过程是创建具有标题 （列） 对应的 Windows PowerShell 脚本所需的参数的 CSV 文件。可以轻松地在 Excel 中创建此类列表，然后将其导出为 CSV 文件。然后，您可以使用 Windows PowerShell 脚本循环访问记录 （行） 在 CSV 文件中，将用户添加到组和网站组。 

例如，我们创建一个 CSV 文件，以定义一组网站集、组和权限。接下来将创建一个 CSV 文件，将用户填充到组中。最后，要创建并运行一个简单的 Windows PowerShell 脚本，此脚本将创建并填充组。

第一个 CSV 文件将一个或多个组添加到一个或多个网站集，并具有以下结构：

### <a name="header"></a>标头：

```
Site,Group,PermissionLevels
```

### <a name="item"></a>项目：

```
https://tenant.sharepoint.com/sites/site,group,level
```

示例文件如下所示：

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

第二个 CSV 文件将一个或多个用户添加到一个或多个组，并具有以下结构：

### <a name="header"></a>标头：

```
Group,LoginName,Site
```

### <a name="item"></a>项目：

```
group,login,https://tenant.sharepoint.com/sites/site
```

示例文件如下所示：

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

下一步，您必须具有两个 CSV 文件保存到您的驱动器。下面是使用这两个 CSV 文件的示例命令添加权限和组成员身份：

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

脚本导入 CSV 文件内容，并使用的列中的值来填充**新建 SPOSiteGroup**和**Add-spouser**命令的参数。在我们的示例，我们将在驱动器 C 上将这保存到 theO365Admin 文件夹，但您可以将其保存所需的位置。

现在，让我们使用同一个 CSV 文件的不同网站中删除大量的几组人员。下面是示例命令：

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>生成用户报告

您可能想要获取一些网站的简单报告，并显示这些网站的用户、权限级别及其他属性。语法如下所示：

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

这将获取以下三个站点的数据，并将它们写到本地驱动器上的文本文件。请注意，参数 – 追加到现有文件将添加新内容。

例如，我们在 Contoso1 租户的 ContosoTest、TeamSite01 和 Project01 网站上运行报告：

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

请注意，我们必须更改仅 **$site**变量。**$Tenant**变量保留所有三个连续的命令通过其值。

但是，如果要对每个网站进行此操作，应该怎么做？通过使用以下命令，您无需键入所有这些网站就可以进行操作：

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

此报告相当简单，，您可以添加更多代码创建更具体的报表或包含更多详细的信息报告。但这会使您了解如何使用 SharePoint Online Management Shell 管理 SharePoint Online 环境中的用户。
   
## <a name="see-also"></a>另请参阅

[连接到 SharePoint Online PowerShell 中](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[使用 Office 365 PowerShell 管理 SharePoint Online](create-sharepoint-sites-and-add-users-with-powershell.md)

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

