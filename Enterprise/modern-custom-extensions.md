---
title: 在 SharePoint Online 新式网站页面中优化自定义扩展
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: Admin
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
description: 了解如何在 SharePoint Online 新式网站页面上优化自定义扩展的性能。
ms.openlocfilehash: bdc05c4e786d07a18c49766bf37aca7f4fde56da
ms.sourcegitcommit: c024b48115cebfdaadfbc724acc2d065394156e9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "42603813"
---
# <a name="optimize-custom-extension-performance-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="a25b9-103">在 SharePoint Online 新式网站页面中优化自定义扩展的性能</span><span class="sxs-lookup"><span data-stu-id="a25b9-103">Optimize custom extension performance in SharePoint Online modern site pages</span></span>

<span data-ttu-id="a25b9-104">本文将帮助你了解如何确定自定义扩展在哪些方面影响了用户感知到的延迟，以及如何修正常见问题。</span><span class="sxs-lookup"><span data-stu-id="a25b9-104">This article will help you understand how to determine how custom extensions affect user perceived latency, and how to remediate common issues.</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-custom-extensions"></a><span data-ttu-id="a25b9-105">使用适用于 SharePoint 的页面诊断工具分析自定义扩展</span><span class="sxs-lookup"><span data-stu-id="a25b9-105">Use the Page Diagnostics for SharePoint tool to analyze custom extensions</span></span>

<span data-ttu-id="a25b9-106">适用于 SharePoint 的页面诊断工具是一款面向新 Microsoft Edge（https://www.microsoft.com/edge) 和 Chrome 浏览器）的浏览器扩展，可用于分析 SharePoint Online 新式门户和经典发布网站页面。</span><span class="sxs-lookup"><span data-stu-id="a25b9-106">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="a25b9-107">该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。</span><span class="sxs-lookup"><span data-stu-id="a25b9-107">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="a25b9-108">要安装和了解适用于 SharePoint 的页面诊断工具，请参阅[使用适用于 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="a25b9-108">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="a25b9-109">页面诊断工具仅适用于 SharePoint Online，无法在 SharePoint 系统页面上使用。</span><span class="sxs-lookup"><span data-stu-id="a25b9-109">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="a25b9-110">通过适用于 SharePoint 的页面诊断工具分析 SharePoint 网站页面时，可在“_诊断测试_”窗格的“**扩展影响加载时间**”结果中，查看有关超出基线指标的自定义扩展的信息。</span><span class="sxs-lookup"><span data-stu-id="a25b9-110">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about custom extensions that exceed the baseline metric in the **Extensions are impacting load time** result in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="a25b9-111">可能的结果包括：</span><span class="sxs-lookup"><span data-stu-id="a25b9-111">Possible results include:</span></span>

- <span data-ttu-id="a25b9-112">**需要注意**（红色）：加载时间超过**一**秒钟的任何_自定义_扩展。</span><span class="sxs-lookup"><span data-stu-id="a25b9-112">**Attention required** (red): Any _custom_ extension that takes longer than **one** second to load.</span></span> <span data-ttu-id="a25b9-113">测试结果中显示的总加载时间按模块加载和初始化进行细分。</span><span class="sxs-lookup"><span data-stu-id="a25b9-113">Total load time as displayed in test results is broken down by module load and init.</span></span>
- <span data-ttu-id="a25b9-114">**无需执行任何操作**（绿色）：加载扩展所需的时间不超过一秒钟。</span><span class="sxs-lookup"><span data-stu-id="a25b9-114">**No action required** (green): No extension is taking longer than one second to load.</span></span>

<span data-ttu-id="a25b9-115">如果扩展会影响页面加载时间，则结果将显示在结果的**需要注意**部分中。</span><span class="sxs-lookup"><span data-stu-id="a25b9-115">If an extension is impacting page load time, the result appears in the **Attention required** section of the results.</span></span> <span data-ttu-id="a25b9-116">单击结果，以查看有关哪个扩展正在缓慢加载的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a25b9-116">Click the result to see details about which extension is loading slowly.</span></span> <span data-ttu-id="a25b9-117">适用于 SharePoint 的页面诊断工具的未来更新可能包括更新分析规则，因此请确保始终拥有该工具的最新版本。</span><span class="sxs-lookup"><span data-stu-id="a25b9-117">Future updates to the Page Diagnostics for SharePoint tool may include updates to analysis rules, so please ensure you always have the latest version of the tool.</span></span>

![页面加载时间结果](media/page-diagnostics-for-spo/pagediag-extensions-load-time.png)

<span data-ttu-id="a25b9-119">结果中的可用信息包括：</span><span class="sxs-lookup"><span data-stu-id="a25b9-119">Information available in the results includes:</span></span>

- <span data-ttu-id="a25b9-120">**名称和 ID**显示可帮助你在页面上查找扩展的标识信息</span><span class="sxs-lookup"><span data-stu-id="a25b9-120">**Name and ID** shows identifying information that can help you find the extension on the page</span></span>
- <span data-ttu-id="a25b9-121">**总计**显示扩展初始化和加载的总时间</span><span class="sxs-lookup"><span data-stu-id="a25b9-121">**Total** shows the total time for the extension to initialize and load</span></span>
- <span data-ttu-id="a25b9-122">**模块加载**显示提取和加载扩展所需的时间</span><span class="sxs-lookup"><span data-stu-id="a25b9-122">**Module Load** shows the time taken to fetch and load the extension</span></span>
- <span data-ttu-id="a25b9-123">**初始化**显示扩展初始化所花的时间</span><span class="sxs-lookup"><span data-stu-id="a25b9-123">**Init** shows the time taken for the extension to initialize</span></span>

<span data-ttu-id="a25b9-124">提供此信息是为了帮助设计人员和开发人员解决问题。</span><span class="sxs-lookup"><span data-stu-id="a25b9-124">This information is provided to help designers and developers troubleshoot issues.</span></span> <span data-ttu-id="a25b9-125">此信息应提供给你的设计和开发团队。</span><span class="sxs-lookup"><span data-stu-id="a25b9-125">This information should be provided to your design and development team.</span></span>

## <a name="overview-of-extensions"></a><span data-ttu-id="a25b9-126">扩展概述</span><span class="sxs-lookup"><span data-stu-id="a25b9-126">Overview of extensions</span></span>

<span data-ttu-id="a25b9-127">可以使用 SharePoint 框架 (SPFx) 扩展来扩展 SharePoint 用户体验。</span><span class="sxs-lookup"><span data-stu-id="a25b9-127">SharePoint Framework (SPFx) Extensions can be used to extend the SharePoint user experience.</span></span> <span data-ttu-id="a25b9-128">使用 SharePoint 框架扩展，可以自定义 SharePoint 体验的更多方面，包括通知区域、工具栏和列表数据视图。</span><span class="sxs-lookup"><span data-stu-id="a25b9-128">With SharePoint Framework Extensions, you can customize more facets of the SharePoint experience, including notification areas, toolbars, and list data views.</span></span>

<span data-ttu-id="a25b9-129">扩展可能会严重影响 SharePoint 页面的性能，因为它还需要 CPU 和网络资源来完成所需的工作。</span><span class="sxs-lookup"><span data-stu-id="a25b9-129">Extensions can have a bad influence on the performance of a SharePoint page as it also takes CPU and network resources to do required work.</span></span>

<span data-ttu-id="a25b9-130">扩展有四种类型：</span><span class="sxs-lookup"><span data-stu-id="a25b9-130">There are four types of extensions:</span></span>

- <span data-ttu-id="a25b9-131">**应用程序定制器**将脚本添加到页面，访问众所周知的 HTML 元素占位符，并使用自定义呈现来扩展它们。</span><span class="sxs-lookup"><span data-stu-id="a25b9-131">**Application Customizers** adds scripts to the page, and accesses well-known HTML element placeholders and extends them with custom renderings.</span></span>
- <span data-ttu-id="a25b9-132">**字段定制器**为列表中的字段数据提供修改的视图。</span><span class="sxs-lookup"><span data-stu-id="a25b9-132">**Field Customizers** provides modified views to data for fields within a list.</span></span>
- <span data-ttu-id="a25b9-133">**命令集**扩展 SharePoint 命令平面以添加新操作，并提供可用于实现行为的客户端代码。</span><span class="sxs-lookup"><span data-stu-id="a25b9-133">**Command Sets** extend the SharePoint command surfaces to add new actions, and provides client-side code that you can use to implement behaviors.</span></span>
- <span data-ttu-id="a25b9-134">**搜索查询修饰符（仅供预览）** 将在执行搜索查询之前被调用。</span><span class="sxs-lookup"><span data-stu-id="a25b9-134">**Search Query Modifier (preview only)** are invoked just before the search query is executed.</span></span>

## <a name="remediate-extension-performance-issues"></a><span data-ttu-id="a25b9-135">修正扩展性能问题</span><span class="sxs-lookup"><span data-stu-id="a25b9-135">Remediate extension performance issues</span></span>

<span data-ttu-id="a25b9-136">按照本节指导来识别和修正“**扩展影响页面加载时间**”结果中列出的扩展的性能问题。</span><span class="sxs-lookup"><span data-stu-id="a25b9-136">Follow the guidance in this section to identify and remediate performance issues with extensions listed in the **Extensions are impacting page load time** results.</span></span>

>[!NOTE]
><span data-ttu-id="a25b9-137">应用程序定制器可能会在页面生命周期的早期阶段执行，并可能会影响页面上其他扩展的性能。</span><span class="sxs-lookup"><span data-stu-id="a25b9-137">Application customizers may be executed in the early stage during the lifecycle of a page and it may influence the performance of other extensions on the page.</span></span>

<span data-ttu-id="a25b9-138">页面诊断工具中的审核结果将显示执行扩展的两个阶段，以帮助确定潜在的性能影响。</span><span class="sxs-lookup"><span data-stu-id="a25b9-138">The audit results in the Page Diagnostic Tool will display two stages of executing an extension in order to help identify the potential performance impact.</span></span>

- <span data-ttu-id="a25b9-139">**模块加载**是加载扩展所需的时间，它受扩展大小的影响，因此最好只将必需的库捆绑在扩展中，同时选择较轻的库。</span><span class="sxs-lookup"><span data-stu-id="a25b9-139">**Module load** is how long it takes to load the extension, which is impacted by the size of an extension so it is a good idea to only bundle the necessary libraries in the extension and to also choose lighter libraries.</span></span>
- <span data-ttu-id="a25b9-140">**初始化**是扩展的初始化时间，扩展开发人员应考虑扩展在初始化阶段是否执行了不必要的工作还是执行太多命令。</span><span class="sxs-lookup"><span data-stu-id="a25b9-140">**Init** is the initialization time of the extension and extension developers should consider whether the extension is doing unnecessary work or executing too many commands during the initializing stage.</span></span>

<span data-ttu-id="a25b9-141">页面作者还可以使用审核结果来查看页面是否具有过多的扩展，因为过多的扩展会对页面的性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="a25b9-141">Page authors can also use the audit result to see whether a page has too many extensions as too many extensions will negatively impact the performance of a page.</span></span>

- <span data-ttu-id="a25b9-142">**扩展大小和依赖项**</span><span class="sxs-lookup"><span data-stu-id="a25b9-142">**Extension size and dependencies**</span></span>
  - <span data-ttu-id="a25b9-143">最佳静态资源下载需要使用 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="a25b9-143">Use of the Office 365 CDN is required for optimal static resource download.</span></span> <span data-ttu-id="a25b9-144">公用 CDN 来源更适合 _js/css_ 文件。</span><span class="sxs-lookup"><span data-stu-id="a25b9-144">Public CDN origins are preferable for _js/css_ files.</span></span> <span data-ttu-id="a25b9-145">有关使用 Office 365 CDN 的详细信息，请参阅[结合使用 Office 365 内容分发网络 (CDN) 和 SharePoint Online](use-office-365-cdn-with-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="a25b9-145">For more information about using the Office 365 CDN, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="a25b9-146">重复使用作为 SharePoint 框架 (SPFx) 一部分的 _React_ 和 _Fabric 导入_等框架。</span><span class="sxs-lookup"><span data-stu-id="a25b9-146">Reuse frameworks like _React_ and _Fabric imports_ that come as part of the SharePoint Framework (SPFx).</span></span> <span data-ttu-id="a25b9-147">有关详细信息，请参阅 [SharePoint 框架概述](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview)。</span><span class="sxs-lookup"><span data-stu-id="a25b9-147">For more information, see [Overview of the SharePoint Framework](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview).</span></span>
  - <span data-ttu-id="a25b9-148">确保你使用的是最新版本的 SharePoint 框架，并在新版本推出时进行升级。</span><span class="sxs-lookup"><span data-stu-id="a25b9-148">Ensure that you are using the latest version of the SharePoint Framework, and upgrade to new versions as they become available.</span></span>
- <span data-ttu-id="a25b9-149">**数据提取/缓存**</span><span class="sxs-lookup"><span data-stu-id="a25b9-149">**Data fetching/caching**</span></span>
  - <span data-ttu-id="a25b9-150">如果扩展依赖额外的服务器调用来提取数据以进行显示，请确保这些服务器 API 运行快速且/或实施客户端缓存（例如，对于较大的集使用 _localStorage_ 或 _IndexDB_）。</span><span class="sxs-lookup"><span data-stu-id="a25b9-150">If the extension relies on extra server calls to fetch data for display, ensure those server APIs are fast and/or implement client side caching (such as using _localStorage_ or _IndexDB_ for larger sets).</span></span>
  - <span data-ttu-id="a25b9-151">如果需要多次调用来呈现关键数据，请考虑在服务器上进行批处理或将请求合并到单个调用的其他方法。</span><span class="sxs-lookup"><span data-stu-id="a25b9-151">If multiple calls are required to render critical data, consider batching on the server or other methods of consolidating requests to a single call.</span></span>
  - <span data-ttu-id="a25b9-152">或者，如果某些数据元素需要较慢的 API，但对初始呈现并不重要，请将这些元素与在呈现关键数据后执行的单独调用进行分离。</span><span class="sxs-lookup"><span data-stu-id="a25b9-152">Alternatively, if some elements of data require a slower API, but are not critical to initial rendering, decouple these to a separate call that is executed after critical data is rendered.</span></span>
  - <span data-ttu-id="a25b9-153">如果多个部件使用相同的数据，请使用公用数据层以避免重复调用。</span><span class="sxs-lookup"><span data-stu-id="a25b9-153">If multiple parts use the same data, utilize a common data layer to avoid duplicate calls.</span></span>
- <span data-ttu-id="a25b9-154">**呈现时间**</span><span class="sxs-lookup"><span data-stu-id="a25b9-154">**Rendering time**</span></span>
  - <span data-ttu-id="a25b9-155">任何媒体源（如图像和视频）都应根据容器、设备和/或网络的限制进行调整，以避免下载不必要的大型资产。</span><span class="sxs-lookup"><span data-stu-id="a25b9-155">Any media sources like images and videos should be sized to the limits of the container, device and/or network to avoid downloading unnecessary large assets.</span></span> <span data-ttu-id="a25b9-156">有关内容依赖项的详细信息，请参阅[结合使用 Office 365 内容分发网络 (CDN) 和 SharePoint Online](use-office-365-cdn-with-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="a25b9-156">For more information about content dependencies, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="a25b9-157">避免会导致重排、复杂 CSS 规则或复杂动画的 API 调用。</span><span class="sxs-lookup"><span data-stu-id="a25b9-157">Avoid API calls that cause re-flow, complex CSS rules or complicated animations.</span></span> <span data-ttu-id="a25b9-158">有关详细信息，请参阅[最大限度地减少浏览器重排](https://developers.google.com/speed/docs/insights/browser-reflow)。</span><span class="sxs-lookup"><span data-stu-id="a25b9-158">For more information, see [Minimizing browser reflow](https://developers.google.com/speed/docs/insights/browser-reflow).</span></span>
  - <span data-ttu-id="a25b9-159">避免使用链接的长时间运行任务。</span><span class="sxs-lookup"><span data-stu-id="a25b9-159">Avoid use of chained long running tasks.</span></span> <span data-ttu-id="a25b9-160">相反，将长时间运行的任务分成单独的队列。</span><span class="sxs-lookup"><span data-stu-id="a25b9-160">Instead, break long running tasks apart into separate queues.</span></span> <span data-ttu-id="a25b9-161">有关详细信息，请参阅[优化 JavaScript 执行](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution)。</span><span class="sxs-lookup"><span data-stu-id="a25b9-161">For more information, see [Optimize JavaScript Execution](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).</span></span>
  - <span data-ttu-id="a25b9-162">保留相应的空间来异步呈现媒体或视觉元素，以避免跳帧和抖动（也称为 _jank_）。</span><span class="sxs-lookup"><span data-stu-id="a25b9-162">Reserve corresponding space for asynchronously rendering media or visual elements to avoid skipped frames and stuttering (also known as _jank_).</span></span>
  - <span data-ttu-id="a25b9-163">如果某个浏览器不支持用于呈现的功能，请加载填充代码或排除正在运行的相关代码。</span><span class="sxs-lookup"><span data-stu-id="a25b9-163">If a certain browser doesn't support a feature used in rendering, either load a polyfill or exclude running dependent code.</span></span> <span data-ttu-id="a25b9-164">如果该功能不重要，请释放事件处理程序等资源以避免内存泄漏。</span><span class="sxs-lookup"><span data-stu-id="a25b9-164">If the feature is not critical, dispose resources such as event handlers to avoid memory leaks.</span></span>

<span data-ttu-id="a25b9-165">在修改页面来修正性能问题之前，请在分析结果中记下页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="a25b9-165">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="a25b9-166">修改后再次运行工具，查看新结果是否在基线标准范围内，同时检查新的页面加载时间，查看是否有提升。</span><span class="sxs-lookup"><span data-stu-id="a25b9-166">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![页面加载时间结果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="a25b9-168">页面加载时间可能由于网络加载、具体时间和其他暂时条件等各种因素而有所不同。</span><span class="sxs-lookup"><span data-stu-id="a25b9-168">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="a25b9-169">应在更改前后多次测试页面加载时间，以帮助求出结果平均值。</span><span class="sxs-lookup"><span data-stu-id="a25b9-169">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a25b9-170">相关主题</span><span class="sxs-lookup"><span data-stu-id="a25b9-170">Related topics</span></span>

[<span data-ttu-id="a25b9-171">优化 SharePoint Online 性能</span><span class="sxs-lookup"><span data-stu-id="a25b9-171">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="a25b9-172">优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="a25b9-172">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="a25b9-173">新式 SharePoint 体验中的性能</span><span class="sxs-lookup"><span data-stu-id="a25b9-173">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="a25b9-174">内容分发网络</span><span class="sxs-lookup"><span data-stu-id="a25b9-174">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="a25b9-175">结合使用 Office 365 内容分发网络和 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a25b9-175">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)