---
title: 使用 Office 365 PowerShell 管理 SharePoint Online 用户和组
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/05/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要：使用 Office 365 PowerShell 管理 SharePoint Online 用户、组和网站。
ms.openlocfilehash: f84e4cda797cd8f1bc4ddf573cb4f1c6f0165da7
ms.sourcegitcommit: 8d1cc95b3641afe547c6d0e05f2dad5d013a0773
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "37975887"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理 SharePoint Online 用户和组

 **摘要：** 使用 Office 365 PowerShell 管理 SharePoint Online 用户、组和网站。

如果您是使用大型用户帐户或组列表的 SharePoint Online 管理员，并且想要更轻松地管理它们，则可以使用 Office 365 PowerShell。 

## <a name="before-you-begin"></a>准备工作

本主题中的过程要求您连接到 SharePoint Online。 有关说明，请参阅[连接到 SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

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

可以使用 **Set-SPOUser** 命令将用户添加到网站集上的网站集管理员列表中。 语法如下所示：

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

若要使用这些命令，请使用正确的名称替换引号内的所有内容，包括 < 和 > 字符。

例如，以下命令集将 Opal Castillo （用户名 opalc）添加到 contoso1 租赁中的 ContosoTest 网站集上的网站集管理员列表：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

您可以将这些命令复制并粘贴到记事本中，将 $tenant、$site 和 $user 的变量值更改为您的环境中的实际值，然后将其粘贴到您的 SharePoint Online 命令行管理程序窗口中，以运行它们。

## <a name="add-a-user-to-other-site-collection-groups"></a>将用户添加到其他网站集组

在此任务中，我们将使用 **Add-SPOUser** 命令将用户添加到网站集上的 SharePoint 组。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

例如，我们将 Glen Rife（用户名 glenr）添加到 contoso1 租赁下 ContosoTest 网站集的审核员组中：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>创建网站集组

您可以使用**remove-spositegroup**命令创建新的 SharePoint 组，并将其添加到 ContosoTest 网站集。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
以后可使用 **Set-SPOSiteGroup** cmdlet 更新组属性（如权限级别）。

例如，在 contoso1 租户中，让我们向审计员组添加对 Contoso Test 网站集的 "仅查看" 权限：

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>从组中删除用户

有时必须从某个网站甚至是所有网站删除用户。员工可能从一个部门转移到另一个部门，或离开公司。在 UI 中可以很容易地对一个员工进行这样的操作，但如果是将整个部门从一个网站移动到另一个网站，这并非易事。

不过，通过使用 SharePoint Online 命令行管理程序和 CSV 文件，这是快速而简单的。 在本任务中，将使用 Windows PowerShell 将用户从一个网站集安全组删除。 然后使用 CSV 文件从不同的网站删除大量用户。 

我们将使用**get-spouser**命令从网站集组中删除单个 Office 365 用户，这样就可以看到命令语法。 语法如下所示：

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
例如，让我们删除 contoso1 租赁中 Contoso Test 网站集的网站集审计员组中的胡继 Overby：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

假定我们要将 Bobby 从他当前所在的所有组中删除。 方法如下：

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> 这只是一个示例。 除非确实需要将用户从每个组中删除（例如，用户离开公司），否则不应运行此命令。

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>自动化管理大型用户和组列表

若要向 SharePoint 网站添加大量帐户并向其授予权限，可以使用 Microsoft 365 管理中心、各个 PowerShell 命令或 PowerShell a CSV 文件。 在这些选择中，CSV 文件是自动执行此任务的最快方法。

基本过程是，创建具有与 Windows PowerShell 脚本所需的参数对应的标头（列）的 CSV 文件。 您可以在 Excel 中轻松创建这样的列表，然后将其导出为 CSV 文件。 然后使用 Windows PowerShell 脚本循环访问 CSV 文件中的记录（行），将用户添加到组，将组添加到网站。 

例如，我们创建一个 CSV 文件，以定义一组网站集、组和权限。接下来将创建一个 CSV 文件，将用户填充到组中。最后，要创建并运行一个简单的 Windows PowerShell 脚本，此脚本将创建并填充组。

第一个 CSV 文件将一个或多个组添加到一个或多个网站集，并具有以下结构：

### <a name="header"></a>邮件

```
Site,Group,PermissionLevels
```

### <a name="item"></a>Item

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

### <a name="header"></a>邮件

```
Group,LoginName,Site
```

### <a name="item"></a>Item

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

然后必须将这两个 CSV 文件保存到驱动器。 下面是使用这两个 CSV 文件并添加权限和组成员身份的示例命令：

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

该脚本将导入 CSV 文件内容，并使用列中的值填充**remove-spositegroup**和**get-spouser**命令的参数。 在我们的示例中，我们将它保存到驱动器 C 上的 theO365Admin 文件夹中，但你可以将其保存到您想要的任何位置。

下面我们来使用相同的 CSV 文件删除不同网站中多个组的一批人员。 下面是一个示例命令：

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

将可以获取这三个网站的数据，并将这些数据写入本地驱动器上的文本文件。 请注意，–Append 参数会将新内容添加到现有文件。

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

请注意，我们只需要更改 **$site**变量。 **$Tenant**变量通过命令的所有三个运行保留其值。

但是，如果要对每个网站进行此操作，应该怎么做？通过使用以下命令，您无需键入所有这些网站就可以进行操作：

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

此报告相当简单，你可以添加更多代码以创建更多特定报告或包括更多详细信息的报告。 但这将使您了解如何使用 SharePoint Online 命令行管理程序来管理 SharePoint Online 环境中的用户。
   
## <a name="see-also"></a>另请参阅

[连接到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[使用 Office 365 PowerShell 管理 SharePoint Online](create-sharepoint-sites-and-add-users-with-powershell.md)

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

