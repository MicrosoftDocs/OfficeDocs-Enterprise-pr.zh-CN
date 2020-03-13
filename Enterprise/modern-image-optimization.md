---
title: 在 SharePoint Online 新式网站页面中优化图像
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: 了解如何在 SharePoint Online 新式网站页面中优化图像。
ms.openlocfilehash: 592839c68f790ffa35887cd1ff95e5354218d9e8
ms.sourcegitcommit: c024b48115cebfdaadfbc724acc2d065394156e9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "42603751"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>在 SharePoint Online 新式网站页面中优化图像

本文将帮助你了解如何在 SharePoint Online 新式网站页面中优化图像。

有关在经典发布网站中优化图像的信息，请参阅 [SharePoint Online 的图像优化](image-optimization-for-sharepoint-online.md)。

>[!NOTE]
>要详细了解 SharePoint Online 新式门户中的性能，请参阅[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance)。

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>使用适用于 SharePoint 的页面诊断工具分析图像优化

适用于 SharePoint 的页面诊断工具是一款面向新 Microsoft Edge (https://www.microsoft.com/edge)) 和 Chrome 浏览器的浏览器扩展，可用于分析 SharePoint Online 新式门户和经典发布网站页面。 该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。 要安装和了解适用于 SharePoint 的页面诊断工具，请参阅[使用适用于 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)。

>[!NOTE]
>页面诊断工具仅适用于 SharePoint Online，无法用于 SharePoint 系统页面。

通过适用于 SharePoint 的页面诊断工具分析 SharePoint 新式网站时，可在“_诊断测试_”窗格中查看有关大图像的信息。

可能的结果包括：

- **需要注意**（红色）：页面包含**一个或多个**大小超过 300KB 的图像
- **不需要执行任何操作**（绿色）：页面不包含大小超过 300KB 的图像

如果“**检测到大图像**”结果显示在结果的“**需要注意**”部分，则可以单击结果以查看其他详细信息。

![页面诊断工具结果](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>修正大图像问题

如果页面包含大小超过 300KB 的图像，请选择“**检测到大图像**”结果以查看哪些图像太大。 在 SharePoint Online 新式页面中，将根据浏览器窗口大小和客户端显示器的分辨率自动呈现图像和调整图像大小。 在上传到 SharePoint Online 之前，应始终优化网页使用的图像。 非常大的图像将自动减小尺寸和分辨率，这可能导致意外的呈现特性。

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
