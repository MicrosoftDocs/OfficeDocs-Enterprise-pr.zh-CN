---
title: SharePoint Online 性能调整简介
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: 本文介绍在设计页面以在 SharePoint Online 中实现最佳性能时需要考虑的特定方面。
ms.openlocfilehash: 5e0d4de44569ad857b28a36b74543c463fe4a80a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41845103"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="88576-103">SharePoint Online 性能优化简介</span><span class="sxs-lookup"><span data-stu-id="88576-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="88576-104">本文介绍在设计页面以在 SharePoint Online 中实现最佳性能时需要考虑的特定方面。</span><span class="sxs-lookup"><span data-stu-id="88576-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="88576-105">SharePoint Online 指标</span><span class="sxs-lookup"><span data-stu-id="88576-105">SharePoint Online metrics</span></span>

<span data-ttu-id="88576-106">SharePoint Online 的以下广义指标提供了有关性能的真实世界数据：</span><span class="sxs-lookup"><span data-stu-id="88576-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="88576-107">页面加载速度</span><span class="sxs-lookup"><span data-stu-id="88576-107">How fast pages load</span></span>
    
- <span data-ttu-id="88576-108">每页所需的往返行程数</span><span class="sxs-lookup"><span data-stu-id="88576-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="88576-109">服务的问题</span><span class="sxs-lookup"><span data-stu-id="88576-109">Issues with the service</span></span>
    
- <span data-ttu-id="88576-110">导致性能下降的其他因素</span><span class="sxs-lookup"><span data-stu-id="88576-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="88576-111">由于数据的原因而达到的结论</span><span class="sxs-lookup"><span data-stu-id="88576-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="88576-112">数据告诉我们：</span><span class="sxs-lookup"><span data-stu-id="88576-112">The data tells us:</span></span>
  
- <span data-ttu-id="88576-113">大多数页面在 SharePoint Online 上性能良好。</span><span class="sxs-lookup"><span data-stu-id="88576-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="88576-114">非自定义页面的加载速度非常快。</span><span class="sxs-lookup"><span data-stu-id="88576-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="88576-115">OneDrive for Business、工作组网站和系统页面（如 _layouts 等）都是快速加载的。</span><span class="sxs-lookup"><span data-stu-id="88576-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="88576-116">最慢的1% 的 SharePoint Online 页面的加载时间超过5000毫秒。</span><span class="sxs-lookup"><span data-stu-id="88576-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="88576-117">您可以使用的一种简单基准测试是通过将您自己的门户的加载时间与 OneDrive for business 主页的加载时间进行比较，因为它使用了极少的自定义功能来衡量性能。</span><span class="sxs-lookup"><span data-stu-id="88576-117">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features.</span></span> <span data-ttu-id="88576-118">这通常是在排除网络性能问题时，第一步支持将会要求你完成此过程。</span><span class="sxs-lookup"><span data-stu-id="88576-118">This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="88576-119">检查性能时使用标准用户帐户</span><span class="sxs-lookup"><span data-stu-id="88576-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="88576-120">网站集管理员、网站所有者、编辑者或参与者属于其他安全组，具有其他权限，因此在页面上有 SharePoint 加载的其他元素。</span><span class="sxs-lookup"><span data-stu-id="88576-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="88576-121">这适用于 SharePoint 本地和 SharePoint Online，但在本地方案中，差别并不像在 SharePoint Online 中那样容易察觉。</span><span class="sxs-lookup"><span data-stu-id="88576-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="88576-122">为了正确评估页面对用户的执行方式，应使用标准用户帐户来避免加载创作控件以及与安全组相关的其他流量。</span><span class="sxs-lookup"><span data-stu-id="88576-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="88576-123">用于性能优化的连接类别</span><span class="sxs-lookup"><span data-stu-id="88576-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="88576-124">您可以将服务器和用户之间的连接分类为三个主要组件。</span><span class="sxs-lookup"><span data-stu-id="88576-124">You can categorize the connections between the server and the user into three main components.</span></span> <span data-ttu-id="88576-125">在设计 SharePoint Online 页以深入了解加载时间时，请考虑这些情况。</span><span class="sxs-lookup"><span data-stu-id="88576-125">Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="88576-126">**Server**Microsoft 在数据中心中托管的服务器。</span><span class="sxs-lookup"><span data-stu-id="88576-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="88576-127">**网络**数据中心和用户之间的 Microsoft 网络、Internet 和本地网络。</span><span class="sxs-lookup"><span data-stu-id="88576-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="88576-128">**浏览器**页面的加载位置。</span><span class="sxs-lookup"><span data-stu-id="88576-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="88576-129">在这三种连接中，通常有五个原因导致慢速页面的95%。</span><span class="sxs-lookup"><span data-stu-id="88576-129">Within these three connections there are typically five reasons that cause 95% of slow pages.</span></span> <span data-ttu-id="88576-130">本文中讨论了上述每个原因：</span><span class="sxs-lookup"><span data-stu-id="88576-130">Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="88576-131">导航问题</span><span class="sxs-lookup"><span data-stu-id="88576-131">Navigation issues</span></span>
    
- <span data-ttu-id="88576-132">内容汇总</span><span class="sxs-lookup"><span data-stu-id="88576-132">Content roll up</span></span>
    
- <span data-ttu-id="88576-133">大型文件</span><span class="sxs-lookup"><span data-stu-id="88576-133">Large files</span></span>
    
- <span data-ttu-id="88576-134">对服务器的多个请求</span><span class="sxs-lookup"><span data-stu-id="88576-134">Many requests to the server</span></span>
    
- <span data-ttu-id="88576-135">Web 部件处理</span><span class="sxs-lookup"><span data-stu-id="88576-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="88576-136">服务器连接</span><span class="sxs-lookup"><span data-stu-id="88576-136">Server connection</span></span>

<span data-ttu-id="88576-137">许多影响 SharePoint 本地的性能的问题也适用于 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="88576-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="88576-138">正如您所期望的那样，您可以在多大程度上控制服务器如何使用本地 SharePoint 进行操作。</span><span class="sxs-lookup"><span data-stu-id="88576-138">As you would expect, you have far more control over how servers perform with on-premises SharePoint.</span></span> <span data-ttu-id="88576-139">SharePoint Online 的内容稍有不同。</span><span class="sxs-lookup"><span data-stu-id="88576-139">With SharePoint Online things are a little different.</span></span> <span data-ttu-id="88576-140">您所做的工作越多，呈现页面所需的时间就越长。</span><span class="sxs-lookup"><span data-stu-id="88576-140">The more work you make a server do, the longer it takes to render a page.</span></span> <span data-ttu-id="88576-141">在 SharePoint 中，此方面最大的原因是具有多个 web 部件的复杂页面。</span><span class="sxs-lookup"><span data-stu-id="88576-141">With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="88576-142">SharePoint Server 本地</span><span class="sxs-lookup"><span data-stu-id="88576-142">SharePoint Server on-premises</span></span>
  
![内部部署服务器的屏幕截图](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="88576-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="88576-144">SharePoint Online</span></span>
  
![联机服务器的屏幕截图](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="88576-146">通过 SharePoint Online，某些页面请求实际上可能会结束呼叫多台服务器。</span><span class="sxs-lookup"><span data-stu-id="88576-146">With SharePoint Online, certain page requests may actually end up calling multiple servers.</span></span> <span data-ttu-id="88576-147">您最终可能会在服务器之间请求单个请求的请求矩阵。</span><span class="sxs-lookup"><span data-stu-id="88576-147">You could end up with a matrix of requests between servers for an individual request.</span></span> <span data-ttu-id="88576-148">从页面加载角度来看，这些交互成本很高，并且会导致速度变慢。</span><span class="sxs-lookup"><span data-stu-id="88576-148">These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="88576-149">这些服务器与服务器交互的示例如下：</span><span class="sxs-lookup"><span data-stu-id="88576-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="88576-150">Web 到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="88576-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="88576-151">Web 到应用程序服务器</span><span class="sxs-lookup"><span data-stu-id="88576-151">Web to application servers</span></span>
    
<span data-ttu-id="88576-152">可能导致服务器交互下降的另一件事是缓存未命中。</span><span class="sxs-lookup"><span data-stu-id="88576-152">The other thing that can slow down server interactions is cache misses.</span></span> <span data-ttu-id="88576-153">与本地 SharePoint 不同的是，您可能会遇到一种极轻巧的情况，即您对以前访问过的页面的同一服务器进行了访问;这会使对象缓存过时。</span><span class="sxs-lookup"><span data-stu-id="88576-153">Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="88576-154">网络连接</span><span class="sxs-lookup"><span data-stu-id="88576-154">Network connection</span></span>

<span data-ttu-id="88576-155">使用不使用 WAN 的本地 SharePoint 时，您可以在数据中心和最终用户之间使用高速连接。</span><span class="sxs-lookup"><span data-stu-id="88576-155">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users.</span></span> <span data-ttu-id="88576-156">通常情况下，从网络的角度来看可以轻松地管理内容。</span><span class="sxs-lookup"><span data-stu-id="88576-156">Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="88576-157">在 SharePoint Online 中，还有其他几个因素需要考虑;例如：</span><span class="sxs-lookup"><span data-stu-id="88576-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="88576-158">Microsoft 网络</span><span class="sxs-lookup"><span data-stu-id="88576-158">The Microsoft network</span></span>
    
- <span data-ttu-id="88576-159">Internet</span><span class="sxs-lookup"><span data-stu-id="88576-159">The Internet</span></span>
    
- <span data-ttu-id="88576-160">ISP</span><span class="sxs-lookup"><span data-stu-id="88576-160">The ISP</span></span>
    
<span data-ttu-id="88576-161">无论使用的是哪个版本的 SharePoint （和哪个网络），通常会导致网络处于忙碌状态的内容包括：</span><span class="sxs-lookup"><span data-stu-id="88576-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="88576-162">大型有效负载</span><span class="sxs-lookup"><span data-stu-id="88576-162">Large payload</span></span>
    
- <span data-ttu-id="88576-163">许多文件</span><span class="sxs-lookup"><span data-stu-id="88576-163">Many files</span></span>
    
- <span data-ttu-id="88576-164">与服务器的物理距离较大</span><span class="sxs-lookup"><span data-stu-id="88576-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="88576-165">您可以在 SharePoint Online 中使用的一项功能是 Microsoft CDN （内容传递网络）。</span><span class="sxs-lookup"><span data-stu-id="88576-165">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network).</span></span> <span data-ttu-id="88576-166">CDN 基本上是跨多个数据中心部署的服务器的分布式集合。</span><span class="sxs-lookup"><span data-stu-id="88576-166">A CDN is basically a distributed collection of servers deployed across multiple datacenters.</span></span> <span data-ttu-id="88576-167">利用 CDN，页面上的内容可以托管在服务器附近，即使客户端离原始 SharePoint 服务器远。</span><span class="sxs-lookup"><span data-stu-id="88576-167">With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server.</span></span> <span data-ttu-id="88576-168">Microsoft 将在将来使用此信息来存储无法自定义的页面的本地实例，例如 SharePoint Online 管理中心主页。</span><span class="sxs-lookup"><span data-stu-id="88576-168">Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page.</span></span> <span data-ttu-id="88576-169">有关 Cdn 的详细信息，请参阅[Content 传递网络](https://docs.microsoft.com/office365/enterprise/content-delivery-networks)。</span><span class="sxs-lookup"><span data-stu-id="88576-169">For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="88576-170">您需要注意但可能无法完成的操作是您的 ISP 的连接速度。</span><span class="sxs-lookup"><span data-stu-id="88576-170">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP.</span></span> <span data-ttu-id="88576-171">简单的速度测试工具将告诉您连接速度。</span><span class="sxs-lookup"><span data-stu-id="88576-171">A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="88576-172">浏览器连接</span><span class="sxs-lookup"><span data-stu-id="88576-172">Browser connection</span></span>

<span data-ttu-id="88576-173">从性能角度来看，有几个因素需要考虑 web 浏览器。</span><span class="sxs-lookup"><span data-stu-id="88576-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="88576-174">访问复杂页面会影响性能。</span><span class="sxs-lookup"><span data-stu-id="88576-174">Visiting complex pages will affect performance.</span></span> <span data-ttu-id="88576-175">大多数浏览器只有较小的缓存（围绕90MB），而平均网页通常约为 1.6 MB。</span><span class="sxs-lookup"><span data-stu-id="88576-175">Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB.</span></span> <span data-ttu-id="88576-176">使用此设置不需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="88576-176">This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="88576-177">带宽也可能是一个问题。</span><span class="sxs-lookup"><span data-stu-id="88576-177">Bandwidth may also be an issue.</span></span> <span data-ttu-id="88576-178">例如，如果用户在另一个会话中观看视频，这将影响 SharePoint 页面的性能。</span><span class="sxs-lookup"><span data-stu-id="88576-178">For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page.</span></span> <span data-ttu-id="88576-179">虽然您无法阻止用户处理媒体，但您可以控制页面加载用户的方式。</span><span class="sxs-lookup"><span data-stu-id="88576-179">While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="88576-180">请查看以下文章，了解不同的 SharePoint Online 页面自定义技术和其他最佳实践，以帮助你实现最佳性能。</span><span class="sxs-lookup"><span data-stu-id="88576-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="88576-181">SharePoint Online 的导航选项</span><span class="sxs-lookup"><span data-stu-id="88576-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="88576-182">使用 SharePoint Online 的页面诊断工具</span><span class="sxs-lookup"><span data-stu-id="88576-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="88576-183">SharePoint Online 的图像优化</span><span class="sxs-lookup"><span data-stu-id="88576-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="88576-184">在 SharePoint Online 中延迟加载图像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="88576-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="88576-185">SharePoint Online 中的缩小和捆绑</span><span class="sxs-lookup"><span data-stu-id="88576-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="88576-186">使用内容交付网络</span><span class="sxs-lookup"><span data-stu-id="88576-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="88576-187">使用内容搜索 Web 部件而不是内容查询 Web 部件来提高 SharePoint Online 中的性能</span><span class="sxs-lookup"><span data-stu-id="88576-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="88576-188">容量规划和负载测试 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="88576-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="88576-189">诊断 SharePoint Online 性能问题</span><span class="sxs-lookup"><span data-stu-id="88576-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="88576-190">在 SharePoint Online 中使用对象缓存</span><span class="sxs-lookup"><span data-stu-id="88576-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="88576-191">如何：避免在 SharePoint Online 中受限制或被阻止</span><span class="sxs-lookup"><span data-stu-id="88576-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/library/office/dn889829.aspx)
    

