---
title: 在 SharePoint Online 新式网站页面中优化图像
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
description: 了解如何在 SharePoint Online 新式网站页面中优化图像。
ms.openlocfilehash: b5b1af0e78b3be7f84b1ee83048010feabddf82e
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571125"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="f444a-103">在 SharePoint Online 新式网站页面中优化图像</span><span class="sxs-lookup"><span data-stu-id="f444a-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="f444a-104">本文将帮助你了解如何在 SharePoint Online 新式网站页面中优化图像。</span><span class="sxs-lookup"><span data-stu-id="f444a-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="f444a-105">有关在经典发布网站中优化图像的信息，请参阅 [SharePoint Online 的图像优化](image-optimization-for-sharepoint-online.md)。</span><span class="sxs-lookup"><span data-stu-id="f444a-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="f444a-106">要详细了解 SharePoint Online 新式门户中的性能，请参阅[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance)。</span><span class="sxs-lookup"><span data-stu-id="f444a-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="f444a-107">使用适用于 SharePoint 的页面诊断工具分析图像优化</span><span class="sxs-lookup"><span data-stu-id="f444a-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="f444a-108">适用于 SharePoint 的页面诊断工具是一款面向新 Microsoft Edge (https://www.microsoft.com/edge)) 和 Chrome 浏览器的浏览器扩展，可用于分析 SharePoint Online 新式门户和经典发布网站页面。</span><span class="sxs-lookup"><span data-stu-id="f444a-108">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="f444a-109">该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。</span><span class="sxs-lookup"><span data-stu-id="f444a-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="f444a-110">要安装和了解适用于 SharePoint 的页面诊断工具，请参阅[使用适用于 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="f444a-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="f444a-111">页面诊断工具仅适用于 SharePoint Online，无法用于 SharePoint 系统页面。</span><span class="sxs-lookup"><span data-stu-id="f444a-111">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="f444a-112">通过适用于 SharePoint 的页面诊断工具分析 SharePoint 新式网站时，可在“_诊断测试_”窗格中查看有关大图像的信息。</span><span class="sxs-lookup"><span data-stu-id="f444a-112">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="f444a-113">可能的结果包括：</span><span class="sxs-lookup"><span data-stu-id="f444a-113">Possible results include:</span></span>

- <span data-ttu-id="f444a-114">**需要注意**（红色）：页面包含**一个或多个**大小超过 300KB 的图像</span><span class="sxs-lookup"><span data-stu-id="f444a-114">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="f444a-115">**不需要执行任何操作**（绿色）：页面不包含大小超过 300KB 的图像</span><span class="sxs-lookup"><span data-stu-id="f444a-115">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="f444a-116">如果“**检测到大图像**”结果显示在结果的“**需要注意**”部分，则可以单击结果以查看其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="f444a-116">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![页面诊断工具结果](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="f444a-118">修正大图像问题</span><span class="sxs-lookup"><span data-stu-id="f444a-118">Remediate large image issues</span></span>

<span data-ttu-id="f444a-119">如果页面包含大小超过 300KB 的图像，请选择“**检测到大图像**”结果以查看哪些图像太大。</span><span class="sxs-lookup"><span data-stu-id="f444a-119">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="f444a-120">在 SharePoint Online 新式页面中，将根据浏览器窗口大小和客户端显示器的分辨率自动呈现图像和调整图像大小。</span><span class="sxs-lookup"><span data-stu-id="f444a-120">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="f444a-121">在上传到 SharePoint Online 之前，应始终优化网页使用的图像。</span><span class="sxs-lookup"><span data-stu-id="f444a-121">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="f444a-122">非常大的图像将自动减小尺寸和分辨率，这可能导致意外的呈现特性。</span><span class="sxs-lookup"><span data-stu-id="f444a-122">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="f444a-123">在修改页面来修正性能问题之前，请在分析结果中记下页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="f444a-123">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="f444a-124">修改后再次运行工具，查看新结果是否在基线标准范围内，同时检查新的页面加载时间，查看是否有提升。</span><span class="sxs-lookup"><span data-stu-id="f444a-124">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![页面加载时间结果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="f444a-126">页面加载时间可能由于网络加载、具体时间和其他暂时条件等各种因素而有所不同。</span><span class="sxs-lookup"><span data-stu-id="f444a-126">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="f444a-127">应在更改前后多次测试页面加载时间，以帮助求出结果平均值。</span><span class="sxs-lookup"><span data-stu-id="f444a-127">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="f444a-128">相关主题</span><span class="sxs-lookup"><span data-stu-id="f444a-128">Related topics</span></span>

[<span data-ttu-id="f444a-129">优化 SharePoint Online 性能</span><span class="sxs-lookup"><span data-stu-id="f444a-129">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="f444a-130">优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="f444a-130">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="f444a-131">新式 SharePoint 体验中的性能</span><span class="sxs-lookup"><span data-stu-id="f444a-131">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="f444a-132">内容分发网络</span><span class="sxs-lookup"><span data-stu-id="f444a-132">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="f444a-133">结合使用 Office 365 内容分发网络和 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f444a-133">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
