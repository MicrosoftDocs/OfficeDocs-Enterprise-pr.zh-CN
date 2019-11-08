---
title: 在 SharePoint Online 新式发布网页和经典发布网页中优化 iFrame
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/17/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: 了解如何优化 iFrame 在SharePoint Online 新式发布网页和经典发布网页中的性能。
ms.openlocfilehash: 4e6695b4afcf5e2f8dc7bd8ccee3d92bbea7e124
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031297"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>在 SharePoint Online 新式发布网页和经典发布网页中优化 iFrame

iFrame 非常适合用于预览视频或其他媒体等丰富的内容。 但是，由于 iFrame 会在 SharePoint 网站中加载单独的页面，因此在 iFrame 中加载的内容可包含大型图像、视频，或者包含会拖慢整体页面加载时间且你无法在页面上控制的其他元素。 本文将帮助你了解如何确定页面内 iFrame 在哪些方面影响了用户感知到的延迟，以及如何修正常见问题。

>[!NOTE]
>要详细了解 SharePoint Online 新式网站中的性能，请参阅[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance)。

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a>通过适用于 SharePoint 的页面诊断工具分析使用 iFrame 的 Web 部件

**适用于 SharePoint 的页面诊断工具**是一款面向 Chrome 和 [Microsoft Edge 版本 77 或更高版本](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)的浏览器扩展，可用于分析发布 SharePoint 新式发布网页和经典发布网页。 该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。 要安装和了解适用于 SharePoint 的页面诊断工具，请访问[使用适用于 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)。

通过适用于 SharePoint 的页面诊断工具分析 SharePoint 网页时，可在_诊断测试_窗格中查看包含 iFrame 的 Web 部件的相关信息。 新式页面和经典页面采用相同的基线指标。

可能的结果包括：

- **需要注意**（红色）：页面包含 **3 个或更多**使用 iFrame 的 Web 部件
- **改进机会**（黄色）：页面包含**一两个**使用 iFrame 的 Web 部件
- **无需任何操作**（绿色）：页面不包含任何使用 iFrame 的 Web 部件

如果结果的“**改进机会**”或“**需要注意**”部分显示了“**检测到使用 iFrame 的 Web 部件**”结果，可单击该结果，查看包含 iFrame 的 Web 部件。

![页面诊断工具结果](media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a>修正 iFrame 性能问题

使用页面诊断工具中的“**检测到使用 iFrame 的 Web 部件**”结果来确定哪些 Web 部件包含 iFrame 且可能拖慢页面加载时间。

iFrame 天生缓慢，这是因为它们会加载包含 javascript、CSS 和框架元素等各种相关内容的单独外部页面，从而可能将网页开销提高至少两个系数。

请按照下述指南确保 iFrame 得到最佳使用。

- 如有可能，在预览一开始较小或没有交互的情况下，请使用图像而不是 iFrame。
- 如果必须使用 iFrame，请尽量减少数量并/或将其移出视区。
- Word、Excel 和 PowerPoint 等内嵌的 Office 文件是交互式的，但加载速度较慢。 通常情况下，带完整文档链接的图像缩略图性能更佳。
- 内嵌的 YouTube 视频和 Twitter 源往往在 iFrame 中的性能更好，但使用这些类型的嵌入时需小心谨慎。
- 根据合理理由，独立 Web 部件没有上述限制，但需尽量减少其在视区中的数量和所占位置。
- 如果 iFrame 位于视区之外，请考虑使用 _IntersectionObserver_ 推迟呈现 iFrame，直到它进入视图。

在修改页面来修正性能问题之前，请在分析结果中记下页面加载时间。 修改后再次运行工具，查看新结果是否在基线标准范围内，同时检查新的页面加载时间，查看是否有提升。

![页面加载时间结果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>页面加载时间可能由于网络加载、具体时间和其他暂时条件等各种因素而有所不同。 应在更改前后多次测试页面加载时间，以帮助求出结果平均值。

## <a name="related-topics"></a>相关主题

[优化 SharePoint Online 性能](tune-sharepoint-online-performance.md)

[优化 Office 365 性能](tune-office-365-performance.md)

[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance.md)
