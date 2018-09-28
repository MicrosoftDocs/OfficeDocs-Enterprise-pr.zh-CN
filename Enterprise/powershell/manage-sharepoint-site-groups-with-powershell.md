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
ms.openlocfilehash: c68e0905c0abcbea279829be7c841c31409db6cf
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975140"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组

 **摘要：** 使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。
  
尽管您可以使用 Office 365 管理中心，您可以使用 Office 365 PowerShell 管理 SharePoint Online 网站组。

## <a name="before-you-begin"></a>准备工作

本文中的过程需要连接到 SharePoint Online。有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。

## <a name="view-sharepoint-online-with-office-365-powershell"></a>查看 SharePoint Online 与 Office 365 PowerShell

在 SharePoint Online 管理中心具有用于管理网站用户组一些易于使用的方法。例如，假设您想要查找组和组成员，在`https://litwareinc.sharepoint.com/sites/finance`网站。下面是您需要对执行的操作：

1. 从 Office 365 管理中心中，单击**资源** > **网站**，然后单击网站的 URL。
2. 在“网站集”对话框中，单击“**转到此网站**”。
3. 在网站页上，单击“**设置**”图标（位于页面的右上角），然后单击“**网站设置**”：<br/>
![SharePoint Online 网站设置](media/spo-site-settings.png)<br/>
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

- 将命令复制到记事本 （或其他文本编辑器）、 修改 **$siteURL**变量的值、 选择的命令，然后将其粘贴到 SharePoint Online 命令行管理程序命令提示符处。PowerShell 执行操作时，将在停止**>>** 提示。按 Enter 执行**foreach**命令。<br/>
- 将命令复制到记事本 （或其他文本编辑器）、 修改 **$siteURL**变量的值，然后保存名称和.ps1 扩展名合适的文件夹中的此文本文件。下一步，指定其路径和文件名称从 SharePoint Online 命令行管理程序命令提示符运行脚本。下面是示例命令：

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

在这两种情况下，应该会看到类似下面的内容：

![SharePoint Online 网站用户组](media/SPO-site-groups.png)

这是已创建的网站的所有组`https://litwareinc.sharepoint.com/sites/finance`、，以及分配给这些组的所有用户。组名称是黄色可帮助您从其成员的单独的组名称。

又如，下面是一个命令集，列出的组和所有的组成员身份，所有的 SharePoint Online 网站。

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
    
## <a name="see-also"></a>另请参阅

[连接到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户](create-sharepoint-sites-and-add-users-with-powershell.md)

[使用 Office 365 PowerShell 管理 SharePoint Online 用户和组](manage-sharepoint-users-and-groups-with-powershell.md)

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

