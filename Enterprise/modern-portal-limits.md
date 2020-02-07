---
title: SharePoint Online 新式门户网站限制
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
description: 了解 SharePoint Online 中新式网站的性能建议。
ms.openlocfilehash: 227eadd780acbe35456ca48204762411bed6c10f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844783"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>SharePoint Online 新式门户网站限制

本文提供了 SharePoint Online 中新式门户网站的性能建议。 使用本文中的准则可优化新式门户网站性能并避免出现常见的性能问题。

## <a name="performance-considerations-for-modern-portal-sites"></a>新式门户网站的性能注意事项

从性能优化的角度来看，有几种特征可使新式门户网站独一无二。 SharePoint Online 中的协作网站和门户网站之间的主要差异是扩展。 与协作网站相比，门户网站通常会向更多的用户提供更多的页面视图，并且可能包含更多的静态内容和可编辑的资源。 此外，新式站点的体系结构与经典网站的不同之处在于，呈现页面和执行代码的大部分处理都是在客户端而不是服务器上进行。

新式门户网站的性能优化主要侧重于一些总体目标：

- 减小每个网站页面的组件的总大小
- 将常见静态文件（如图像、样式表和脚本）的卸载托管到 CDN
- 仅对 SharePoint 和外部终结点的调用限制为必需
- 避免对相同内容的重复请求

本文中的许多准则主要侧重于最大限度地减少和优化对 SharePoint Online 的调用。 每次加载页面时进行重复调用都会影响用户的性能，因为即使信息未发生更改，也会从服务中检索信息。 因此，可以将 SharePoint 请求分类为对所有用户或每个用户所需的呼叫通用的呼叫。 应缓存来自这两个呼叫类别的结果，以优化用户体验。

>[!NOTE]
>使用[sharepoint 工具的页面诊断工具](https://aka.ms/perftool)作为分析 sharepoint Online 网站页面上的特定性能指标的起始点。

## <a name="modern-portal-site-limits-and-recommendations"></a>新式门户网站限制和建议

|**限制**|**建议的最大值**|**Notes**|
|:-----|:-----|:-----|:-----|
|页面和新闻项目  <br/> |每个网站 5,000 个  <br/> |建议将新式门户网站中的页面和新闻项目的数量限制为低于5000。  <br/> |
|页面上的 Web 部件  <br/> |每页20张  <br/> |我们建议每个页面使用20个或更少的总 web 部件，包括现成的 Microsoft web 部件和自定义 web 部件。 <br/> 有关详细信息，请参阅[在 SharePoint Online 新式网站页面中优化 web 部件性能](modern-web-part-optimization.md)。  <br/> |
|页面上的动态 web 部件  <br/> |每页4个  <br/> |向 SharePoint 中的一个或多个查询提取最新数据的动态 web 部件应限制为每页4个。 "_新闻_" web 部件是一个动态 web 部件的示例。 <br/> 有关详细信息，请参阅[在 SharePoint Online 新式网站页面中优化 web 部件性能](modern-web-part-optimization.md)。    <br/> |
|安全组  <br/> |每个站点20个  <br/> |安全组的数量会影响新式门户网站中的许多查询的规模。 我们建议您将安全组的数量限制为尽可能少，并且每个站点不超过20个。  <br/> |
|网站导航中的项目  <br/> |每个站点100  <br/> |建议在网站导航中添加的项目数少于100个，并使用现成的导航控件。  <br/> 有关详细信息，请参阅[优化页面权重中的 SharePoint Online 新式网站页面](modern-page-weight-optimization.md)。 <br/> |
|最大图像大小  <br/> |每个图像 300 Kb  <br/> |建议将图像大小限制为300kb 或更小，并使用 CDN 承载图像、样式表和脚本。 <br/>有关详细信息，请参阅[在 Sharepoint online 新式网站页面中优化图像](modern-image-optimization.md)和[使用 Office 365 内容传送网络（CDN）和 SharePoint online](use-office-365-cdn-with-spo.md)。  <br/> |
|具有编辑权限的用户  <br/> |每个网站200个用户  <br/> |SharePoint 门户网站针对查看和使用内容进行了优化。 对门户的编辑权限应限制为受限制的用户组，因为编辑权限可下载其他控件，因此会对这些用户执行较慢的工作。 因此，拥有编辑权限的用户数过多将影响整体体验。 <br/> |
|第三方 Iframe  <br/> |每页2个  <br/> |Iframe 由于加载单独的外部页面（包括 javascript、CSS 和框架元素等所有关联的内容）而导致速度不可预知。 如果必须使用 Iframe，请将它们的数目限制为2个或更少的页面。<br/> 有关详细信息，请参阅[在 SharePoint Online 新式和经典发布网站页面中优化 iframe](modern-iframe-optimization.md)。 <br/> |
|对 UPA 服务的调用  <br/> |每个用户每小时1个  <br/> |我们建议您对 UPA （User Profile Application）服务不进行_每次请求_调用。 [Microsoft GRAPH API](https://docs.microsoft.com/graph/call-api)和[PageContext](https://docs.microsoft.com/javascript/api/sp-page-context/pagecontext?view=sp-typescript-latest)可用于查询用户信息。  <br/> 如果需要 UPA 服务呼叫，请在需要时进行单个呼叫，然后缓存信息以便在同一会话中重复使用。 |
|对分类服务的调用  <br/> |每个用户每小时5个  <br/> |我们建议您对分类服务不进行_每次请求_调用。 如果分类服务调用是必需的，请缓存信息以便在同一个会话中重复使用。 <br/> 有关详细信息，请参阅[在 SharePoint Online 新式和经典发布网站页面中优化页面调用](modern-page-call-optimization.md)。 <br/> |

## <a name="related-topics"></a>相关主题

[创建运行状况良好的 SharePoint 门户](https://docs.microsoft.com/sharepoint/portal-health)

[优化 SharePoint Online 性能](tune-sharepoint-online-performance.md)

[优化 Office 365 性能](tune-office-365-performance.md)

[SharePoint Online 限制](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[SharePoint Online 门户性能指南](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-performance)
