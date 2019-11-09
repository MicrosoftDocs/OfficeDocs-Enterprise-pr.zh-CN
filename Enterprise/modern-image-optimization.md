---
title: 在 SharePoint Online 新式网站页面中优化图像
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
description: 了解如何在 SharePoint Online 新式网站页面中优化图像。
ms.openlocfilehash: df6fab6fdd02bf6668a86c8d7a3941ece10cc3d1
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078011"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="e9e44-103">在 SharePoint Online 新式网站页面中优化图像</span><span class="sxs-lookup"><span data-stu-id="e9e44-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="e9e44-104">本文将帮助你了解如何在 SharePoint Online 新式网站页面中优化图像。</span><span class="sxs-lookup"><span data-stu-id="e9e44-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="e9e44-105">有关在经典发布网站中优化图像的信息，请参阅 [SharePoint Online 的图像优化](image-optimization-for-sharepoint-online.md)。</span><span class="sxs-lookup"><span data-stu-id="e9e44-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="e9e44-106">要详细了解 SharePoint Online 新式门户中的性能，请参阅[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance)。</span><span class="sxs-lookup"><span data-stu-id="e9e44-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="e9e44-107">使用适用于 SharePoint 的页面诊断工具分析图像优化</span><span class="sxs-lookup"><span data-stu-id="e9e44-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="e9e44-108">**适用于 SharePoint 的页面诊断工具**是一款面向 Chrome 和 [Microsoft Edge 版本 77 或更高版本](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)的浏览器扩展，可用于分析 SharePoint 新式和经典发布网站页面。</span><span class="sxs-lookup"><span data-stu-id="e9e44-108">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="e9e44-109">该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。</span><span class="sxs-lookup"><span data-stu-id="e9e44-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="e9e44-110">要安装和了解适用于 SharePoint 的页面诊断工具，请参阅[使用适用于 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="e9e44-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="e9e44-111">通过适用于 SharePoint 的页面诊断工具分析 SharePoint 新式网站时，可在“_诊断测试_”窗格中查看有关大图像的信息。</span><span class="sxs-lookup"><span data-stu-id="e9e44-111">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="e9e44-112">可能的结果包括：</span><span class="sxs-lookup"><span data-stu-id="e9e44-112">Possible results include:</span></span>

- <span data-ttu-id="e9e44-113">**需要注意**（红色）：页面包含**一个或多个**大小超过 300KB 的图像</span><span class="sxs-lookup"><span data-stu-id="e9e44-113">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="e9e44-114">**不需要执行任何操作**（绿色）：页面不包含大小超过 300KB 的图像</span><span class="sxs-lookup"><span data-stu-id="e9e44-114">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="e9e44-115">如果“**检测到大图像**”结果显示在结果的“**需要注意**”部分，则可以单击结果以查看其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="e9e44-115">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![页面诊断工具结果](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="e9e44-117">修正大图像问题</span><span class="sxs-lookup"><span data-stu-id="e9e44-117">Remediate large image issues</span></span>

<span data-ttu-id="e9e44-118">如果页面包含大小超过 300KB 的图像，请选择“**检测到大图像**”结果以查看哪些图像太大。</span><span class="sxs-lookup"><span data-stu-id="e9e44-118">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="e9e44-119">在 SharePoint Online 新式页面中，将根据浏览器窗口大小和客户端显示器的分辨率自动呈现图像和调整图像大小。</span><span class="sxs-lookup"><span data-stu-id="e9e44-119">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="e9e44-120">在上传到 SharePoint Online 之前，应始终优化网页使用的图像。</span><span class="sxs-lookup"><span data-stu-id="e9e44-120">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="e9e44-121">非常大的图像将自动减小尺寸和分辨率，这可能导致意外的呈现特性。</span><span class="sxs-lookup"><span data-stu-id="e9e44-121">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="e9e44-122">在修改页面来修正性能问题之前，请在分析结果中记下页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="e9e44-122">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="e9e44-123">修改后再次运行工具，查看新结果是否在基线标准范围内，同时检查新的页面加载时间，查看是否有提升。</span><span class="sxs-lookup"><span data-stu-id="e9e44-123">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![页面加载时间结果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="e9e44-125">页面加载时间可能由于网络加载、具体时间和其他暂时条件等各种因素而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e9e44-125">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="e9e44-126">应在更改前后多次测试页面加载时间，以帮助求出结果平均值。</span><span class="sxs-lookup"><span data-stu-id="e9e44-126">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="e9e44-127">相关主题</span><span class="sxs-lookup"><span data-stu-id="e9e44-127">Related topics</span></span>

[<span data-ttu-id="e9e44-128">优化 SharePoint Online 性能</span><span class="sxs-lookup"><span data-stu-id="e9e44-128">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="e9e44-129">优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="e9e44-129">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="e9e44-130">新式 SharePoint 体验中的性能</span><span class="sxs-lookup"><span data-stu-id="e9e44-130">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance.md)

[<span data-ttu-id="e9e44-131">内容分发网络</span><span class="sxs-lookup"><span data-stu-id="e9e44-131">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="e9e44-132">结合使用 Office 365 内容分发网络和 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e9e44-132">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
