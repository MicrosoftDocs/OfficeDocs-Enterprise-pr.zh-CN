---
title: Office 365 内容传送网络（CDN）快速入门
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 内容传送网络（CDN）快速入门
ms.openlocfilehash: 4abaaa5545bc807c4da297c66fd9ad1fb188adc7
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "44561916"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a><span data-ttu-id="292c8-103">Office 365 内容传送网络（CDN）快速入门</span><span class="sxs-lookup"><span data-stu-id="292c8-103">Office 365 Content Delivery Network (CDN) Quickstart</span></span>

<span data-ttu-id="292c8-104">您可以使用内置的**Office 365 内容传递网络（CDN）** 来托管静态资产（图像、JavaScript、样式表、WOFF 文件），以便为您的 SharePoint Online 页面提供更好的性能。</span><span class="sxs-lookup"><span data-stu-id="292c8-104">You can use the built-in **Office 365 Content Delivery Network (CDN)** to host static assets (images, JavaScript, Stylesheets, WOFF files) to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="292c8-105">Office 365 CDN 将静态资产缓存到距离请求这些资产的浏览器更近的位置，这样可以加快下载速度并减少延迟，进而提高性能。</span><span class="sxs-lookup"><span data-stu-id="292c8-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="292c8-106">此外，Office 365 CDN 使用 HTTP/2 协议改进了压缩和 HTTP 流水线功能。</span><span class="sxs-lookup"><span data-stu-id="292c8-106">Also, the Office 365 CDN uses the HTTP/2 protocol for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="292c8-107">Office 365 CDN 服务被归入 SharePoint Online 订阅。</span><span class="sxs-lookup"><span data-stu-id="292c8-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="292c8-108">有关更多详细信息指南，请参阅[使用 Office 365 内容传送网络（CDN）和 SharePoint Online](use-office-365-cdn-with-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="292c8-108">For more detailed information guidance see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="292c8-109">Office 365 CDN 仅适用于生产（全球）云中的租户。</span><span class="sxs-lookup"><span data-stu-id="292c8-109">The Office 365 CDN is only available to tenants in the production (worldwide) cloud.</span></span> <span data-ttu-id="292c8-110">美国政府、中国和德国云中的租户目前不支持 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="292c8-110">Tenants in the US Government, China and Germany clouds do not currently support the Office 365 CDN.</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a><span data-ttu-id="292c8-111">使用 SharePoint 工具的页面诊断工具标识不在 CDN 中的项目</span><span class="sxs-lookup"><span data-stu-id="292c8-111">Use the Page Diagnostics for SharePoint tool to identify items not in CDN</span></span>

<span data-ttu-id="292c8-112">您可以使用 SharePoint 工具浏览器扩展的**页面诊断**功能，轻松列出可添加到 CDN 源的 sharepoint Online 页面中的资产。</span><span class="sxs-lookup"><span data-stu-id="292c8-112">You can use the **Page Diagnostics for SharePoint tool** browser extension to easily list assets in your SharePoint Online pages that can be added to a CDN origin.</span></span>

<span data-ttu-id="292c8-113">**SharePoint 工具的页面诊断工具**是新 Microsoft Edge （ https://www.microsoft.com/edge) 和同时分析 SharePoint Online 新式门户和经典发布网站页面的 Chrome 浏览器）的浏览器扩展。</span><span class="sxs-lookup"><span data-stu-id="292c8-113">The **Page Diagnostics for SharePoint tool** is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="292c8-114">该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。</span><span class="sxs-lookup"><span data-stu-id="292c8-114">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="292c8-115">要安装和了解适用于 SharePoint 的页面诊断工具，请参阅[使用适用于 SharePoint Online 的页面诊断工具](https://aka.ms/perftool)。</span><span class="sxs-lookup"><span data-stu-id="292c8-115">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](https://aka.ms/perftool).</span></span>

<span data-ttu-id="292c8-116">当您在 SharePoint Online 页上运行 SharePoint 的页面诊断工具时，您可以单击 "**诊断测试**" 选项卡，以查看由 CDN 不承载的资产的列表。</span><span class="sxs-lookup"><span data-stu-id="292c8-116">When you run the Page Diagnostics for SharePoint tool on a SharePoint Online page, you can click the **Diagnostic Tests** tab to see a list of assets not being hosted by the CDN.</span></span> <span data-ttu-id="292c8-117">这些资产将在标题**内容传递网络（CDN）检查**下列出，如下面的屏幕截图中所示。</span><span class="sxs-lookup"><span data-stu-id="292c8-117">These assets will be listed under the heading **Content Delivery Network (CDN) check** as shown in the screenshot below.</span></span>

![页面诊断](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
><span data-ttu-id="292c8-119">页面诊断工具仅适用于 SharePoint Online，无法用于 SharePoint 系统页面。</span><span class="sxs-lookup"><span data-stu-id="292c8-119">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

## <a name="cdn-overview"></a><span data-ttu-id="292c8-120">CDN 概述</span><span class="sxs-lookup"><span data-stu-id="292c8-120">CDN Overview</span></span>

<span data-ttu-id="292c8-121">Office 365 CDN 旨在通过在高速全局网络中分布经常访问的对象（如图像和 javascript 文件）来优化用户的性能，从而减少页面加载时间，并以尽可能接近的方式向用户提供对承载对象的访问权限。</span><span class="sxs-lookup"><span data-stu-id="292c8-121">The Office 365 CDN is designed to optimize performance for users by distributing frequently accessed objects like images and javascript files over a high-speed global network, reducing page load time and providing access to hosted objects as close as possible to the user.</span></span> <span data-ttu-id="292c8-122">CDN 从称为 "_来源_" 的位置提取资产。</span><span class="sxs-lookup"><span data-stu-id="292c8-122">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="292c8-123">来源可以是可通过 URL 访问的 SharePoint 网站、文档库或文件夹。</span><span class="sxs-lookup"><span data-stu-id="292c8-123">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span>

<span data-ttu-id="292c8-124">Office 365 CDN 分为两种基本类型：</span><span class="sxs-lookup"><span data-stu-id="292c8-124">The Office 365 CDN is separated into two basic types:</span></span>

- <span data-ttu-id="292c8-125">**公用 CDN**旨在用于 JS （JavaScript）、CSS （样式表）、Web 字体文件（WOFF、WOFF2）和非专有图像（如公司徽标）。</span><span class="sxs-lookup"><span data-stu-id="292c8-125">**Public CDN** is designed to be used for JS (JavaScript), CSS (StyleSheets), Web Font File (WOFF, WOFF2) and non-proprietary images like company logos.</span></span>
- <span data-ttu-id="292c8-126">**专用 CDN**旨在用于图像（PNG、JPG、JPEG 等）。</span><span class="sxs-lookup"><span data-stu-id="292c8-126">**Private CDN** is designed to be used for images (PNG, JPG, JPEG, etc.).</span></span>

<span data-ttu-id="292c8-127">您可以选择同时为您的组织提供公共来源或专用来源。</span><span class="sxs-lookup"><span data-stu-id="292c8-127">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="292c8-128">大多数组织将选择实现这两个的组合。</span><span class="sxs-lookup"><span data-stu-id="292c8-128">Most organizations will choose to implement a combination of the two.</span></span> <span data-ttu-id="292c8-129">公用和专用选项都提供了类似的性能提升，但各自具有独特的特性和优势。</span><span class="sxs-lookup"><span data-stu-id="292c8-129">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span> <span data-ttu-id="292c8-130">有关公用和专用 CDN 源的详细信息，请参阅[Choose 是否每个源应该是公共的还是专用](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)的。</span><span class="sxs-lookup"><span data-stu-id="292c8-130">For more information about public and private CDN origins, see [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span>

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a><span data-ttu-id="292c8-131">如何使用默认配置启用公用和专用 CDN</span><span class="sxs-lookup"><span data-stu-id="292c8-131">How to enable Public and Private CDN with the default configuration</span></span>
<span data-ttu-id="292c8-132">在对租户 CDN 设置进行更改之前，应验证它是否符合组织的合规性、安全性和隐私策略。</span><span class="sxs-lookup"><span data-stu-id="292c8-132">Before you make changes to the tenant CDN settings, you should verify that it meets compliance, security and privacy policies of your organization.</span></span>

<span data-ttu-id="292c8-133">有关更多详细的配置设置，或者如果您已启用 CDN 并想要添加其他位置（来源），请参阅[使用 SharePoint Online 命令行管理程序设置和配置 Office 365 CDN](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)一节</span><span class="sxs-lookup"><span data-stu-id="292c8-133">For more detailed configuration settings, or if you have already enabled CDN and want to add additional locations (origins), please see the section [Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)</span></span>

<span data-ttu-id="292c8-134">使用 SharePoint Online 命令行管理程序连接到你的租户：</span><span class="sxs-lookup"><span data-stu-id="292c8-134">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

<span data-ttu-id="292c8-135">若要使组织能够将公用源和专用源用于默认配置，请键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="292c8-135">To enable your organization to use both public and private origins with the default configuration, type the following command:</span></span>

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="292c8-136">这些 cmdlet 的输出应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="292c8-136">Output of these cmdlets should look like the following:</span></span>

![SPOTenantCdnEnabled 的输出](media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a><span data-ttu-id="292c8-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="292c8-138">See also</span></span>

[<span data-ttu-id="292c8-139">使用 SharePoint Online 的页面诊断工具</span><span class="sxs-lookup"><span data-stu-id="292c8-139">Use the Page Diagnostics tool for SharePoint Online</span></span>](https://aka.ms/perftool)

[<span data-ttu-id="292c8-140">结合使用 Office 365 内容分发网络和 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="292c8-140">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)

[<span data-ttu-id="292c8-141">内容分发网络</span><span class="sxs-lookup"><span data-stu-id="292c8-141">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="292c8-142">Office 365 网络计划和性能优化</span><span class="sxs-lookup"><span data-stu-id="292c8-142">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="292c8-143">SharePoint 性能系列-Office 365 CDN 视频系列</span><span class="sxs-lookup"><span data-stu-id="292c8-143">SharePoint Performance Series - Office 365 CDN video series</span></span>](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
