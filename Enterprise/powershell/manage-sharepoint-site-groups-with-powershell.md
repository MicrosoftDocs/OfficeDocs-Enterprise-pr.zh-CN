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
description: '摘要: 使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。'
ms.openlocfilehash: 04df780732913eaaf80d9bca64db5174089ed80b
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573906"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组

 **摘要:** 使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。
  
虽然您可以使用 Microsoft 365 管理中心, 但您也可以使用 Office 365 PowerShell 管理 SharePoint Online 网站用户组。

## <a name="before-you-begin"></a>准备工作

本文中的过程要求您连接到 SharePoint Online。 有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。

## <a name="view-sharepoint-online-with-office-365-powershell"></a>使用 Office 365 PowerShell 查看 SharePoint Online

SharePoint Online 管理中心具有一些易于使用的方法来管理网站用户组。 例如, 假设您想要查看`https://litwareinc.sharepoint.com/sites/finance`网站的组和组成员。 以下是需要执行的操作：

1. 在 Microsoft 365 管理中心, 单击 "**资源** > **网站**", 然后单击网站的 URL。
2. 在“网站集”对话框中，单击“**转到此网站**”。
3. 在网站页上，单击“**设置**”图标（位于页面的右上角），然后单击“**网站设置**”：<br/>
![SharePoint Online 网站设置](media/spo-site-settings.png)<br/>
4. 在“网站设置”页上的“**用户和权限**”下单击“**网站权限**”。

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

有两种方法可以在 SharePoint Online 命令行管理程序命令提示符中运行此命令集:

- 将命令复制到记事本 (或其他文本编辑器) 中, 修改 **$siteURL**变量的值, 选择命令, 然后将其粘贴到 SharePoint Online 命令行管理程序命令提示符中。 执行此操作时, PowerShell 将在出现**>>** 提示时停止。 按 Enter 键执行 **foreach** 命令。<br/>
- 将命令复制到记事本（或其他文本编辑器），修改 **$siteURL** 变量值，然后在合适的文件夹中使用一个名称和.ps1 扩展名保存该文本文件。 接下来, 通过指定其路径和文件名从 SharePoint Online 命令行管理程序命令提示符处运行脚本。 下面是一个示例命令：

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

在这两种情况下，应该会看到类似下面的内容：

![SharePoint Online 网站用户组](media/SPO-site-groups.png)

这些是已为站点`https://litwareinc.sharepoint.com/sites/finance`创建的所有组, 以及分配给这些组的所有用户。 组名为黄色，以帮助你从其成员中辨别组名。

作为另一个示例, 下面是一个命令集, 其中列出了所有 SharePoint Online 网站的组和所有组成员身份。

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

