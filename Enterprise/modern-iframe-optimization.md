---
title: 在 SharePoint Online 新式发布网页和经典发布网页中优化 iFrame
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
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
description: 了解如何优化 iFrame 在SharePoint Online 新式发布网页和经典发布网页中的性能。
ms.openlocfilehash: 292599a25ea5adb05cc38e4a7d5cb1f756c6143a
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571145"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a><span data-ttu-id="c32e0-103">在 SharePoint Online 新式发布网页和经典发布网页中优化 iFrame</span><span class="sxs-lookup"><span data-stu-id="c32e0-103">Optimize iFrames in SharePoint Online modern and classic publishing site pages</span></span>

<span data-ttu-id="c32e0-104">iFrame 非常适合用于预览视频或其他媒体等丰富的内容。</span><span class="sxs-lookup"><span data-stu-id="c32e0-104">iFrames can be useful for previewing rich content such as videos or other media.</span></span> <span data-ttu-id="c32e0-105">但是，由于 iFrame 会在 SharePoint 网站中加载单独的页面，因此在 iFrame 中加载的内容可包含大型图像、视频，或者包含会拖慢整体页面加载时间且你无法在页面上控制的其他元素。</span><span class="sxs-lookup"><span data-stu-id="c32e0-105">However, because iFrames load a separate page within the SharePoint site page, content loaded in the iFrame could contain large images, videos or other elements that can contribute to overall page load times and that you cannot control on the page.</span></span> <span data-ttu-id="c32e0-106">本文将帮助你了解如何确定页面内 iFrame 在哪些方面影响了用户感知到的延迟，以及如何修正常见问题。</span><span class="sxs-lookup"><span data-stu-id="c32e0-106">This article will help you understand how to determine how iFrames in your pages affect user perceived latency, and how to remediate common issues.</span></span>

>[!NOTE]
><span data-ttu-id="c32e0-107">要详细了解 SharePoint Online 新式网站中的性能，请参阅[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance)。</span><span class="sxs-lookup"><span data-stu-id="c32e0-107">For more information about performance in SharePoint Online modern sites, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a><span data-ttu-id="c32e0-108">通过适用于 SharePoint 的页面诊断工具分析使用 iFrame 的 Web 部件</span><span class="sxs-lookup"><span data-stu-id="c32e0-108">Use the Page Diagnostics for SharePoint tool to analyze web parts using iFrames</span></span>

<span data-ttu-id="c32e0-109">适用于 SharePoint 的页面诊断工具是一款面向新 Microsoft Edge (https://www.microsoft.com/edge)) 和 Chrome 浏览器的浏览器扩展，可用于分析 SharePoint Online 新式门户和经典发布网站页面。</span><span class="sxs-lookup"><span data-stu-id="c32e0-109">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="c32e0-110">该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。</span><span class="sxs-lookup"><span data-stu-id="c32e0-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="c32e0-111">要安装和了解适用于 SharePoint 的页面诊断工具，请参阅[使用适用于 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="c32e0-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="c32e0-112">页面诊断工具仅适用于 SharePoint Online，无法用于 SharePoint 系统页面。</span><span class="sxs-lookup"><span data-stu-id="c32e0-112">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="c32e0-113">通过适用于 SharePoint 的页面诊断工具分析 SharePoint 网页时，可在_诊断测试_窗格中查看包含 iFrame 的 Web 部件的相关信息。</span><span class="sxs-lookup"><span data-stu-id="c32e0-113">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about web parts containing iFrames in the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="c32e0-114">新式页面和经典页面采用相同的基线指标。</span><span class="sxs-lookup"><span data-stu-id="c32e0-114">The baseline metric is the same for modern and classic pages.</span></span>

<span data-ttu-id="c32e0-115">可能的结果包括：</span><span class="sxs-lookup"><span data-stu-id="c32e0-115">Possible results include:</span></span>

- <span data-ttu-id="c32e0-116">**需要注意**（红色）：页面包含 **3 个或更多**使用 iFrame 的 Web 部件</span><span class="sxs-lookup"><span data-stu-id="c32e0-116">**Attention required** (red): The page contains **three or more** web parts using iFrames</span></span>
- <span data-ttu-id="c32e0-117">**改进机会**（黄色）：页面包含**一两个**使用 iFrame 的 Web 部件</span><span class="sxs-lookup"><span data-stu-id="c32e0-117">**Improvement opportunities** (yellow): The page contains **one or two** web parts using iFrames</span></span>
- <span data-ttu-id="c32e0-118">**无需任何操作**（绿色）：页面不包含任何使用 iFrame 的 Web 部件</span><span class="sxs-lookup"><span data-stu-id="c32e0-118">**No action required** (green): The page contains no web parts using iFrames</span></span>

<span data-ttu-id="c32e0-119">如果结果的“**改进机会**”或“**需要注意**”部分显示了“**检测到使用 iFrame 的 Web 部件**”结果，可单击该结果，查看包含 iFrame 的 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="c32e0-119">If the **Web parts using iFrames detected** result appears in either the **Improvement opportunities** or **Attention required)** section of the results, you can click the result to see the web parts that contain iFrames.</span></span>

![页面诊断工具结果](media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a><span data-ttu-id="c32e0-121">修正 iFrame 性能问题</span><span class="sxs-lookup"><span data-stu-id="c32e0-121">Remediate iFrame performance issues</span></span>

<span data-ttu-id="c32e0-122">使用页面诊断工具中的“**检测到使用 iFrame 的 Web 部件**”结果来确定哪些 Web 部件包含 iFrame 且可能拖慢页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="c32e0-122">Use the **Web parts using iFrames detected** result in the Page Diagnostic tool to determine which web parts contain iFrames and may be contributing to slow page load times.</span></span>

<span data-ttu-id="c32e0-123">iFrame 天生缓慢，这是因为它们会加载包含 javascript、CSS 和框架元素等各种相关内容的单独外部页面，从而可能将网页开销提高至少两个系数。</span><span class="sxs-lookup"><span data-stu-id="c32e0-123">iFrames are inherently slow because they load a separate external page including all associated content such as javascript, CSS and framework elements, potentially increasing the overhead of the site page by a factor of two or more.</span></span>

<span data-ttu-id="c32e0-124">请按照下述指南确保 iFrame 得到最佳使用。</span><span class="sxs-lookup"><span data-stu-id="c32e0-124">Follow the guidance below to ensure optimal use of iFrames.</span></span>

- <span data-ttu-id="c32e0-125">如有可能，在预览一开始较小或没有交互的情况下，请使用图像而不是 iFrame。</span><span class="sxs-lookup"><span data-stu-id="c32e0-125">When possible, use images instead of iFrames if the preview is small to begin with or non-interactive.</span></span>
- <span data-ttu-id="c32e0-126">如果必须使用 iFrame，请尽量减少数量并/或将其移出视区。</span><span class="sxs-lookup"><span data-stu-id="c32e0-126">If iFrames must be used, minimize the number and/or move them out of the viewport.</span></span>
- <span data-ttu-id="c32e0-127">Word、Excel 和 PowerPoint 等内嵌的 Office 文件是交互式的，但加载速度较慢。</span><span class="sxs-lookup"><span data-stu-id="c32e0-127">Embedded Office files like Word, Excel and PowerPoint are interactive, but are slow to load.</span></span> <span data-ttu-id="c32e0-128">通常情况下，带完整文档链接的图像缩略图性能更佳。</span><span class="sxs-lookup"><span data-stu-id="c32e0-128">Image thumbnails with a link to the full document will often perform better.</span></span>
- <span data-ttu-id="c32e0-129">内嵌的 YouTube 视频和 Twitter 源往往在 iFrame 中的性能更好，但使用这些类型的嵌入时需小心谨慎。</span><span class="sxs-lookup"><span data-stu-id="c32e0-129">Embedded YouTube videos and Twitter feeds tend to perform better in iFrames, but use these kinds of embeds judiciously.</span></span>
- <span data-ttu-id="c32e0-130">根据合理理由，独立 Web 部件没有上述限制，但需尽量减少其在视区中的数量和所占位置。</span><span class="sxs-lookup"><span data-stu-id="c32e0-130">Isolated web parts are a reasonable exception, but minimize their number and placement in the viewport.</span></span>
- <span data-ttu-id="c32e0-131">如果 iFrame 位于视区之外，请考虑使用 _IntersectionObserver_ 推迟呈现 iFrame，直到它进入视图。</span><span class="sxs-lookup"><span data-stu-id="c32e0-131">If an iFrame is located out of the viewport, consider using an _IntersectionObserver_ to delay rendering the iFrame until it comes into view.</span></span>

<span data-ttu-id="c32e0-132">在修改页面来修正性能问题之前，请在分析结果中记下页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="c32e0-132">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="c32e0-133">修改后再次运行工具，查看新结果是否在基线标准范围内，同时检查新的页面加载时间，查看是否有提升。</span><span class="sxs-lookup"><span data-stu-id="c32e0-133">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![页面加载时间结果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="c32e0-135">页面加载时间可能由于网络加载、具体时间和其他暂时条件等各种因素而有所不同。</span><span class="sxs-lookup"><span data-stu-id="c32e0-135">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="c32e0-136">应在更改前后多次测试页面加载时间，以帮助求出结果平均值。</span><span class="sxs-lookup"><span data-stu-id="c32e0-136">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="c32e0-137">相关主题</span><span class="sxs-lookup"><span data-stu-id="c32e0-137">Related topics</span></span>

[<span data-ttu-id="c32e0-138">优化 SharePoint Online 性能</span><span class="sxs-lookup"><span data-stu-id="c32e0-138">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="c32e0-139">优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="c32e0-139">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="c32e0-140">新式 SharePoint 体验中的性能</span><span class="sxs-lookup"><span data-stu-id="c32e0-140">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)
