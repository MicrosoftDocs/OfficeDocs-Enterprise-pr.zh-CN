---
title: 在 SharePoint Online 新式发布网页和经典发布网页中优化页面调用
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: 了解如何通过限制到 SharePoint Online 服务终结点的调用数量来优化 SharePoint Online 中的新式和经典发布网页。
ms.openlocfilehash: 608e1e102ae3425fdf24d99b5932f2c616290913
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078421"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>在 SharePoint Online 新式发布网页和经典发布网页中优化页面调用

SharePoint Online 新式和经典发布网页都包含从 SharePoint 功能和 CDN 加载数据（或对其进行调用）的链接。 页面调用次数越多，页面加载所耗时间越长。 这称为**最终用户感知延迟** (**EUPL**)。

本文将帮助你了解如何确定从新式和经典发布网页调用外部终结点的次数及所造成的影响，以及如何限制其对最终用户感知延迟的影响。

>[!NOTE]
>要详细了解 SharePoint Online 新式门户中的性能，请参阅[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance)。

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a>使用适用于 SharePoint 的页面诊断工具分析页面调用

**适用于 SharePoint 的页面诊断工具**是一款面向 Chrome 和 [Microsoft Edge 版本 77 或更高版本](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)的浏览器扩展，可用于分析发布 SharePoint 新式发布网页和经典发布网页。 该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。 要安装和了解适用于 SharePoint 的页面诊断工具，请访问[使用适用于 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)。

通过适用于 SharePoint 的页面诊断工具分析 SharePoint 网页时，可在“_诊断测试_”窗格的“**对 SharePoint 的请求**”结果中查看外部调用相关信息。 如果网页包含的调用低于基线数量，则该行显示为绿色；如果页面超过基线数量，则显示为红色。 新式页面和经典页面的基线数量不相同，因为经典网页使用 HTTP1.1，而新式页面使用 HTTP2.0：

- 新式网页包含的调用不得超过 **25** 次。
- 经典发布页面包含的调用不得超过 **6** 次。

可能的结果包括：

- **需要注意**（红色）：页面超过调用的基线数量
- **需要注意**（绿色）：页面包含的调用低于基线数量

如果“**需要注意**”部分中显示“**对 SharePoint 的请求**”，可单击结果了解详细信息，例如页面上调用总数和 URL 列表。

![对 SharePoint 的请求结果](media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a>修正与页面上调用过多相关的性能问题

如果页面包含太多调用，可在“**对 Sharepoint 的请求**”结果中使用 URL 列表，以确定是否有任何重复的调用、应批处理的调用或返回应缓存的数据的调用。

“**批处理 REST 调用**”可帮助减少性能开销。 要详细了解 API 调用批处理，请参阅[使用 REST API 进行批处理请求](https://docs.microsoft.com/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis)。

通过**使用缓存**来存储 API 调用的结果，让客户端能够使用缓存的数据而不是对每个后续页面加载进行额外的调用，从而提升热请求的性能。 可通过多种方法，根据业务要求处理此解决方案。 通常情况下，如果数据对所有用户都一样，很好的选择是使用 [_Azure Redis_ 缓存](https://azure.microsoft.com/services/cache/)等中间层缓存服务来显著减少对网站的 API 流量，因为用户会从缓存服务中请求数据，而不是直接从 SPO 中请求。 唯一需要的 SPO 调用就是刷新中间层的缓存。 如果每个用户的数据不同，则最好是实现客户端缓存，例如 LocalStorage 或甚至是 Cookie。 这样，同一用户无需在缓存持续时间内发出后续请求，从而减少调用量，但与专用缓存服务相比效率更低。 借助 PnP，几乎无需额外的开发即可使用 LocalStorage。

在修改页面来修正性能问题之前，请在分析结果中记下页面加载时间。 修改后再次运行工具，查看新结果是否在基线标准范围内，同时检查新的页面加载时间，查看是否有提升。

![页面加载时间结果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>页面加载时间可能由于网络加载、具体时间和其他暂时条件等各种因素而有所不同。 应在更改前后多次测试页面加载时间，以帮助求出结果平均值。

## <a name="related-topics"></a>相关主题

[优化 SharePoint Online 性能](tune-sharepoint-online-performance.md)

[优化 Office 365 性能](tune-office-365-performance.md)

[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[内容分发网络](content-delivery-networks.md)

[结合使用 Office 365 内容分发网络和 SharePoint Online](use-office-365-cdn-with-spo.md)
