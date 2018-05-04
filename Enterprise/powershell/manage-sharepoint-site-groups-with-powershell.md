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
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组

 **摘要：**使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。
  
尽管您可以使用 Office 365 管理中心，您可以使用 Office 365 PowerShell 管理 SharePoint Online 网站组。

## <a name="before-you-begin"></a>准备工作

本文中的过程需要连接到 SharePoint Online。有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。

## <a name="view-sharepoint-online-with-office-365-powershell"></a>查看 SharePoint Online 与 Office 365 PowerShell

在 SharePoint Online 管理中心具有用于管理网站用户组一些易于使用的方法。例如，假设您想要查找组和组成员，在https://litwareinc.sharepoint.com/sites/finance网站。下面是您需要对执行的操作：

1. 从 Office 365 管理中心中，单击**资源** > **网站**，然后单击网站的 URL。
2. 在网站集对话框中，单击**转到此网站**。
3. 在网站页上单击**设置**图标 （位于页面的右上角），然后单击**网站设置**:</br>
![SharePoint Online 网站设置](images/spo-site-settings.png)</br>
4. 在网站设置页上单击**用户和权限**下的**网站权限**。

然后对您要查看的下一个网站重复此过程。

若要使用 Office 365 PowerShell 获取组列表，请使用以下命令集：

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

有两种方式来运行在 SharePoint Online 命令行管理程序命令提示符中设置此命令：
- 将命令复制到记事本 （或其他文本编辑器）、 修改 **$siteURL**变量的值、 选择的命令，然后将其粘贴到 SharePoint Online 命令行管理程序命令提示符处。PowerShell 执行操作时，将在停止 >> 提示。按 Enter 执行的每个命令。</br>
- 将命令复制到记事本 （或其他文本编辑器）、 修改 **$siteURL**变量的值，然后保存名称和.ps1 扩展名合适的文件夹中的此文本文件。下一步，指定其路径和文件名称从 SharePoint Online 命令行管理程序命令提示符运行脚本。下面是一个示例：</br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
$x = Get-sposite foreach ($y 中 $x) {写主机 $y.Url-ForegroundColor"黄色"$z = Get-spositegroup-网站 $y.Url foreach ($ 在 $z) {$b = Get-spositegroup-网站 $y.Url-组 $a.Title 写主机 $b.Title-ForegroundColor"青色"$b |Select-object-ExpandProperty 用户写入-主机}}
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

