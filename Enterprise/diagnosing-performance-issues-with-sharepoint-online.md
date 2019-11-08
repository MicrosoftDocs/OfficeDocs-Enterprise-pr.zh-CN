---
title: 诊断 SharePoint Online 的性能问题
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/9/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: 本文介绍如何使用 Internet Explorer 开发人员工具诊断 SharePoint Online 网站的常见问题。
ms.openlocfilehash: 2b97098c68eb519ed5a1edc26146c521f39a11d1
ms.sourcegitcommit: fa900775790eb369db1983cd3868b628b699f145
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38033408"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>诊断 SharePoint Online 的性能问题

本文介绍如何使用 Internet Explorer 开发人员工具诊断 SharePoint Online 网站的常见问题。
  
您可以使用三种不同的方法来确定 SharePoint Online 网站上的页面在自定义项中存在性能问题。
  
- F12 工具栏网络监视器

- 与非自定义基线的比较

- SharePoint Online 响应标头指标

本主题介绍如何使用上述每种方法来诊断性能问题。 一旦您发现问题的原因，您可以使用有关改进 SharePoint 性能的文章来解决问题https://aka.ms/tune。
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>使用 F12 工具条诊断 SharePoint Online 中的性能
<a name="F12ToolInfo"> </a>

在本文中，我们将使用 Internet Explorer 11。 其他浏览器上的 F12 开发人员工具的版本具有类似的功能，尽管它们看起来可能略有不同。 有关 F12 开发人员工具的详细信息，请参阅：
  
- [F12 工具的新增功能](https://go.microsoft.com/fwlink/p/?LinkId=522545)

- [使用 F12 开发人员工具](https://go.microsoft.com/fwlink/p/?LinkId=522546)

若要显示开发人员工具，请按**F12**键，然后单击 wi-fi 图标：
  
![F12 开发人员工具 wifi 图标的屏幕截图](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
在 "**网络**" 选项卡上，按绿色的 "播放" 按钮以加载一个页面。 该工具将返回浏览器请求的所有文件，以便获取您要求的页面。 下面的屏幕截图显示了一个这样的列表。
  
![返回页面请求的文件列表的屏幕截图。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
您还可以查看右侧文件的下载时间，如此屏幕截图中所示。
  
![显示从 SharePoint 加载请求页面所需时间的图表](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
这使您能够直观地表示文件加载所需的时间。 绿色线表示浏览器准备呈现页面的时间。 这可让你快速查看可能导致你的网站上的页面负载缓慢的不同文件。
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>为 SharePoint Online 设置非自定义基准
<a name="F12ToolInfo"> </a>

确定网站性能薄弱点的最佳方式是在 SharePoint Online 中设置完全开箱即用的网站集。 通过这种方式，您可以将网站的各个方面与在页面上没有自定义的内容进行比较。 OneDrive for Business 主页是一个不太可能具有任何自定义项的单独网站集的一个很有用的示例。
  
## <a name="viewing-sharepoint-response-header-information"></a>查看 SharePoint 响应头信息
<a name="F12ToolInfo"> </a>

在 SharePoint Online 中，您可以访问发送回每个文件的响应头中的浏览器的信息。 诊断性能问题最有用的值是**SPRequestDuration**，它显示请求对服务器进行处理的时间量。 这有助于确定请求是否非常繁重且占用大量资源。 这是您对服务器为页面提供服务所需的最大的洞察力。

### <a name="to-view-sharepoint-response-header-information"></a>查看 SharePoint 响应头信息
  
1. 确保已安装 F12 工具。 有关下载和安装这些工具的详细信息，请参阅[F12 工具中的新增功能](https://go.microsoft.com/fwlink/p/?LinkId=522545)。

2. 在 F12 工具的 "**网络**" 选项卡上，按绿色的 "播放" 按钮以加载页面。

3. 单击工具返回的 .aspx 文件之一，然后单击 "**详细信息**"。

    ![显示响应头的详细信息](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. 单击 "**响应头**"。

    ![显示响应头的 URL 的图表](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>SharePoint Online 中导致性能问题的原因是什么？
<a name="F12ToolInfo"> </a>

[SharePoint Online 的文章导航选项](navigation-options-for-sharepoint-online.md)显示了使用 SPRequestDuration 值来确定复杂的结构导航导致页面在服务器上进行处理的时间较长的示例。 通过为基线网站（而不是自定义）获取值，可以确定是否有任何给定的文件需要很长时间才能加载。 [SharePoint Online 的导航选项](navigation-options-for-sharepoint-online.md)中使用的示例是主要 .aspx 文件。 该文件包含为您的页面加载运行的大部分 ASP.NET 代码。 根据您使用的网站模板，可以启动 .aspx、default.aspx、default.aspx 或其他名称（如果自定义主页）。 如果此数字比您的基准网站大得多，则表明页面中存在导致性能问题的复杂内容。
  
确定了特定于网站的问题后，建议的方法是找出导致性能不佳的原因是消除了所有可能的原因（如页面自定义），然后将它们逐个添加回网站。 在删除了足够的自定义项后，页面的运行状况很好后，即可逐个添加特定的自定义项。
  
例如，如果您有一个非常复杂的导航，请尝试将导航更改为 "不显示子网站"，然后检查开发人员工具以查看这是否会产生差异。 或者，如果您有大量的内容汇总，请尝试从页面中删除它们，并查看这是否会提高内容。 如果您消除了所有可能的原因并一次将其重新添加到一个中，则可以轻松地确定哪些功能是最大的问题，然后再向解决方案中进行操作。
