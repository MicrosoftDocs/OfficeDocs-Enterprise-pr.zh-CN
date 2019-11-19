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
ms.openlocfilehash: abe8f76de07c230c0d1484ccfb57b3b9a7bf8d34
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "38707019"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户

 **摘要：** 使用 Office 365 PowerShell 创建新的 SharePoint Online 网站，然后将用户和组添加到这些网站。

当您使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户时，您可以在 Office 356 管理中心中快速和重复执行任务快得多。 你还可以执行在 Office 356 管理中心中无法执行的任务。 

## <a name="before-you-begin"></a>开始之前

本主题中的过程要求您连接到 SharePoint Online。 有关说明，请参阅[连接到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>步骤 1：使用 Office 365 PowerShell 创建新的网站集

使用 Office 365 PowerShell 和你使用提供的示例代码和记事本创建的 .csv 文件创建多个网站。 在此步骤中，你将使用你自己的网站和租户特定信息替换括号中显示的占位符信息。 此过程允许您创建一个文件，并运行一个使用该文件的 Office 365 PowerShell 命令。 这使得所采取的操作具有可重复性和可移植性，并可以减少许多（如果不是全部）因向 SharePoint Online 命令行管理程序键入长命令而导致的错误。 此步骤包括两个部分。 首先，你要创建一个 .csv 文件，然后使用 Office 365 PowerShell 引用该 .csv 文件，从而利用该文件的内容来创建网站。

Office 365 PowerShell cmdlet 导入 .csv 文件并将其通过管道传递到大括号内的循环中，该循环将读取文件的第一行作为列标题。然后，Office 365 PowerShell cmdlet 循环访问剩余的记录，为每个记录创建一个新的网站集，并根据列标题指定网站集的属性。

### <a name="create-a-csv-file"></a>创建 .csv 文件

1. 打开记事本，然后向其中粘贴以下文本块：<br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>其中*租户*是你的租户的名称，*所有者*是你要向其授予主网站集管理员角色的租户上的用户用户名。<br/>（当使用记事本以更快地批量替换时，可以按 Ctrl + H。）<br/>

2. 将文件以**SiteCollections**的形式保存在桌面上。<br/>

> [!TIP]
> 在使用这个或任何其他 .csv 或 WindowsPowerShell 脚本文件之前，最好先确保没有多余的或者非打印字符。 在 Word 中打开该文件，在功能区单击“段落”图标以显示非打印字符。 应该没有多余的非打印字符。 例如，除了文件末尾的最后一个段落标记之外，应该没有其他任何段落标记。

### <a name="run-the-windows-powershell-command"></a>运行 Windows PowerShell 命令

1. 在 Windows PowerShell 提示符处键入或复制并粘贴以下 cmdlet，然后按 Enter 键：<br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>其中， *MyAlias*等于您的用户别名。<br/>

2. 等待 Windows PowerShell 提示符重新出现。可能需要一两分钟。<br/>

3. 在 Windows PowerShell 提示符处键入或复制并粘贴以下 cmdlet，然后按 Enter 键：<br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. 请注意列表中的新网站集。 您应该会看到以下网站集： **contosotest**、 **TeamSite01**、 **Blog01**和**Project01**

就是这样。你已经使用所创建的 .csv 文件和一个 Windows PowerShell cmdlet 创建了多个网站集。现在，可以创建用户并将其分配给这些网站。

## <a name="step-2-add-users-and-groups"></a>步骤 2：添加用户和组

现在，您将创建用户并将其添加到网站集组中。然后，您将使用 .csv 文件批量上载新的组和用户。

下列步骤假定您已成功创建网站集 contosotest、TeamSite01、Blog01 和 Project01。

### <a name="create-csv-and-ps1-files"></a>创建 .csv 和 .ps1 文件

1. 打开记事本，然后向其中粘贴以下文本块：<br/>
```powershell
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
<br/>其中*租户*等于你的租户名称。<br/>

2. 将文件以**GroupsAndPermissions**的形式保存到您的桌面。<br/>

3. 打开记事本的新实例，然后向其中粘贴以下文本块：<br/>

```powershell
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
<br/>其中*租户*等于租户名称，*用户名*等于现有用户的用户名。<br/>

4. 将文件以**Users. .csv**的形式保存到桌面。<br/>

5. 打开记事本的新实例，然后向其中粘贴以下文本块：<br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>其中，MyAlias 等于当前登录的用户的用户名。<br/>

6. 将文件以**UsersAndGroups**的形式保存到您的桌面。 这是一个简单的 Windows PowerShell 脚本。

现在，您可以运行 UsersAndGroup.ps1 脚本以向多个网站集中添加用户和组。

### <a name="run-usersandgroupsps1-script"></a>运行 UsersAndGroups.ps1 脚本

1. 返回到 SharePoint Online 命令行管理程序。<br/>
2. 在 Windows PowerShell 提示符下键入或复制并粘贴以下行，然后按 Enter 键：<br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. 在确认提示符处，按 " **Y**"。<br/>

4. 在 Windows PowerShell 提示符下键入或复制并粘贴以下内容，然后按 Enter 键：<br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>其中， *MyAlias*等于您的用户名。<br/>

5. 在继续之前，请等待提示符返回。首先，您将看到这些组在创建时的样子。然后，您将看到添加用户后的重复组列表。

## <a name="see-also"></a>另请参阅

[连接到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[管理 SharePoint Online 网站组 Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

