---
title: 在 SharePoint Online 新式网站页面中优化 Web 部件性能
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/6/2019
audience: Admin
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
description: 了解如何在 SharePoint Online 新式网站页面上优化 Web 部件性能。
ms.openlocfilehash: 859a9481ca29215edf27cc2cbd48510051932d50
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078317"
---
# <a name="optimize-web-part-performance-in-sharepoint-online-modern-site-pages"></a>在 SharePoint Online 新式网站页面中优化 Web 部件性能

SharePoint Online 新式网站页面包含可能影响整个页面加载时间的 Web 部件。 本文将帮助你了解如何确定页面内的 Web 部件在哪些方面影响了用户感知到的延迟，以及如何修正常见问题。

>[!NOTE]
>要详细了解 SharePoint Online 新式门户中的性能，请参阅[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance)。

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts"></a>使用适用于 SharePoint 的页面诊断工具分析 Web 部件

**适用于 SharePoint 的页面诊断工具**是一款面向 Chrome 和 [Microsoft Edge 版本 77 或更高版本](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)的浏览器扩展，可用于分析 SharePoint 新式和经典发布网站页面。 该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。 要安装和了解适用于 SharePoint 的页面诊断工具，请参阅[使用适用于 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)。

通过适用于 SharePoint 的页面诊断工具分析 SharePoint 网站页面时，可在“_诊断测试_”窗格的“**Web 部件影响页面加载时间**”结果中，查看有关超出基线指标的 Web 部件的信息。

可能的结果包括：

- **需要注意**（红色）：加载时间超过**两**秒钟的任何_自定义_ Web 部件。 测试结果中显示的总加载时间按模块加载、延迟加载、初始化和呈现进行细分。
- **改进机会**（黄色）：可能影响页面加载时间的项目将在此部分显示，应该对这些项目进行审查和监控。 这可能包括“开箱即用”(OOTB) Microsoft Web 部件。 此部分显示的任何 Microsoft Web 部件结果都会自动报告给 Microsoft，因此**不需要执行任何操作**。 如果你的页面性能非常缓慢，并且页面上的**所有 Microsoft Web 部件**都显示在“**改进机会**”部分的结果中，则应仅记录支持票证以进行调查。 请注意，未来的页面诊断工具更新将根据 Microsoft Web 部件的特定配置进一步细分结果。
- **不需要执行任何操作**（绿色）：任何 Web 部件返回数据的时间都不超过**两**秒钟。

如果“**Web 部件影响页面加载时间**”结果显示在结果的“**需要注意**”或“**改进机会**”部分，请单击结果以查看有关哪些 Web 部件加载缓慢的详细信息。 适用于 SharePoint 的页面诊断工具的未来更新可能包括更新分析规则，因此请确保始终拥有该工具的最新版本。

![页面诊断工具结果](media/modern-portal-optimization/pagediag-web-part.png)

结果中的可用信息包括：

- “**创建者**”显示 Web 部件是自定义还是 Microsoft OOTB 部件
- “**名称和 ID**”显示可帮助你在页面上查找 Web 部件的标识信息
- “**总计**”显示 Web 部件加载的总时间
- “**模块加载**”显示提取和加载 Web 部件组件所需的时间
- “**延迟加载**”显示页面主要部分中未显示的 Web 部件的延迟加载时间
- “**初始化**”显示 Web 部件初始化所花的时间
- “**呈现**”显示 Web 部件提取和呈现结果所需的时间

提供此信息是为了帮助设计人员和开发人员解决问题。 此信息应提供给你的设计和开发团队。

## <a name="remediate-web-part-performance-issues"></a>修正 Web 部件性能问题

按照本节指导来识别和修正“**Web 部件影响页面加载时间**”结果中列出的 Web 部件的性能问题。

Web 部件性能较差的原因有三类。 使用以下信息确定哪些问题适用于你的方案并进行修正。

- Web 部件脚本大小和依赖项
  - 优化_仅为视图模式_呈现主线方案的初始脚本。
  - 移动使用不频繁的方案并编辑模式代码（如属性窗格）以使用 _import()_ 语句分隔区块。
  - 审查 _package.json_ 文件的依赖项以完全删除任何死代码。 将任何仅限测试/内部版本的依赖项移动到 devDependencies。
  - 最佳静态资源下载需要使用 Office 365 CDN。 公用 CDN 来源更适合 _js/css_ 文件。 有关使用 Office 365 CDN 的详细信息，请参阅[结合使用 Office 365 内容分发网络 (CDN) 和 SharePoint Online](use-office-365-cdn-with-spo.md)。
  - 重复使用作为 SharePoint 框架 (SPFx) 一部分的 _React_ 和 _Fabric 导入_等框架。 有关详细信息，请参阅 [SharePoint 框架概述](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview)。
  - 确保你使用的是最新版本的 SharePoint 框架，并在新版本推出时进行升级。
- 数据提取/缓存
  - 如果 Web 部件依赖额外的服务器调用来提取数据以进行显示，请确保这些服务器 API 运行快速且/或实施客户端缓存（例如，对于较大的集使用 _localStorage_ 或 _IndexDB_）。
  - 如果需要多次调用来呈现关键数据，请考虑在服务器上进行批处理或将请求合并到单个调用的其他方法。
  - 或者，如果某些数据元素需要较慢的 API，但对初始呈现并不重要，请将这些元素与在呈现关键数据后执行的单独调用进行分离。
  - 如果多个部件使用相同的数据，请使用公用数据层以避免重复调用。
- 呈现时间
  - 任何媒体源（如图像和视频）都应根据容器、设备和/或网络的限制进行调整，以避免下载不必要的大型资产。 有关内容依赖项的详细信息，请参阅[结合使用 Office 365 内容分发网络 (CDN) 和 SharePoint Online](use-office-365-cdn-with-spo.md)。
  - 避免会导致重排、复杂 CSS 规则或复杂动画的 API 调用。 有关详细信息，请参阅[最大限度地减少浏览器重排](https://developers.google.com/speed/docs/insights/browser-reflow)。
  - 避免使用链接的长时间运行任务。 相反，将长时间运行的任务分成单独的队列。 有关详细信息，请参阅[优化 JavaScript 执行](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution)。
  - 保留相应的空间来异步呈现媒体或视觉元素，以避免跳帧和抖动（也称为 _jank_）。
  - 如果某个浏览器不支持用于呈现的功能，请加载填充代码或排除正在运行的相关代码。 如果该功能不重要，请释放事件处理程序等资源以避免内存泄漏。

在修改页面来修正性能问题之前，请在分析结果中记下页面加载时间。 修改后再次运行工具，查看新结果是否在基线标准范围内，同时检查新的页面加载时间，查看是否有提升。

![页面加载时间结果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>页面加载时间可能由于网络加载、具体时间和其他暂时条件等各种因素而有所不同。 应在更改前后多次测试页面加载时间，以帮助求出结果平均值。

## <a name="related-topics"></a>相关主题

[优化 SharePoint Online 性能](tune-sharepoint-online-performance.md)

[优化 Office 365 性能](tune-office-365-performance.md)

[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance.md)

[内容分发网络](content-delivery-networks.md)

[结合使用 Office 365 内容分发网络和 SharePoint Online](use-office-365-cdn-with-spo.md)
