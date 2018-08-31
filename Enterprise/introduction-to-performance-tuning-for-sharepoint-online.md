---
title: SharePoint Online 性能调整简介
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: 本文介绍了您需要时设计页面以在 SharePoint Online 中的最佳性能，请考虑哪些特定方面。
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539541"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="df96c-103">SharePoint Online 性能调整简介</span><span class="sxs-lookup"><span data-stu-id="df96c-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="df96c-104">本文介绍了您需要时设计页面以在 SharePoint Online 中的最佳性能，请考虑哪些特定方面。</span><span class="sxs-lookup"><span data-stu-id="df96c-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
  
## <a name="in-this-article"></a><span data-ttu-id="df96c-105">本文内容</span><span class="sxs-lookup"><span data-stu-id="df96c-105">In this article</span></span>

- <span data-ttu-id="df96c-106">[SharePoint Online 指标](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics)和[结论达到由于数据](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span><span class="sxs-lookup"><span data-stu-id="df96c-106">[SharePoint Online metrics](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) and [Conclusions reached because of the data](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span></span>
    
- [<span data-ttu-id="df96c-107">检查性能时使用标准用户帐户</span><span class="sxs-lookup"><span data-stu-id="df96c-107">Use a standard user account when checking performance</span></span>](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- <span data-ttu-id="df96c-108">[连接的性能调整的类别](introduction-to-performance-tuning-for-sharepoint-online.md#connect)：[服务器连接](introduction-to-performance-tuning-for-sharepoint-online.md#server)、[网络连接](introduction-to-performance-tuning-for-sharepoint-online.md#network)和[浏览器连接](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span><span class="sxs-lookup"><span data-stu-id="df96c-108">[Connection categories for performance tuning](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [Server connection](introduction-to-performance-tuning-for-sharepoint-online.md#server), [Network connection](introduction-to-performance-tuning-for-sharepoint-online.md#network), and [Browser connection](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span></span>
    
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="df96c-109">SharePoint Online 的指标</span><span class="sxs-lookup"><span data-stu-id="df96c-109">SharePoint Online metrics</span></span>
<span data-ttu-id="df96c-110"><a name="spometrics"> </a></span><span class="sxs-lookup"><span data-stu-id="df96c-110"></span></span>

<span data-ttu-id="df96c-111">SharePoint Online 的以下广泛指标提供有关性能的实际数据：</span><span class="sxs-lookup"><span data-stu-id="df96c-111">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="df96c-112">页面加载的速度</span><span class="sxs-lookup"><span data-stu-id="df96c-112">How fast pages load</span></span>
    
- <span data-ttu-id="df96c-113">每页所需的往返行程数</span><span class="sxs-lookup"><span data-stu-id="df96c-113">How many round trips required per page</span></span>
    
- <span data-ttu-id="df96c-114">服务存在的问题</span><span class="sxs-lookup"><span data-stu-id="df96c-114">Issues with the service</span></span>
    
- <span data-ttu-id="df96c-115">导致性能下降的其他原因</span><span class="sxs-lookup"><span data-stu-id="df96c-115">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="df96c-116">根据数据得出的结论</span><span class="sxs-lookup"><span data-stu-id="df96c-116">Conclusions reached because of the data</span></span>
<span data-ttu-id="df96c-117"><a name="data"> </a></span><span class="sxs-lookup"><span data-stu-id="df96c-117"></span></span>

<span data-ttu-id="df96c-118">数据告诉我们：</span><span class="sxs-lookup"><span data-stu-id="df96c-118">The data tells us:</span></span>
  
- <span data-ttu-id="df96c-119">大多数页面在 SharePoint Online 上运行良好。</span><span class="sxs-lookup"><span data-stu-id="df96c-119">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="df96c-120">非自定义页面加载速度非常快。</span><span class="sxs-lookup"><span data-stu-id="df96c-120">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="df96c-121">OneDrive for Business、工作组网站和系统页面（如 _layouts）等的加载速度都很快。</span><span class="sxs-lookup"><span data-stu-id="df96c-121">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="df96c-122">最慢的 1% 的 SharePoint Online 页面的加载时间超过 5000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="df96c-122">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="df96c-p101">您可以使用的一个简单的基准测试是将您自己门户的加载时间与 OneDrive for Business 主页的加载时间进行比较以衡量性能，因为后者几乎不使用自定义性能。这通常是支持人员在对网络性能问题进行故障排除时将要求您完成的第一步。</span><span class="sxs-lookup"><span data-stu-id="df96c-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="df96c-125">检查性能时使用标准用户帐户</span><span class="sxs-lookup"><span data-stu-id="df96c-125">Use a standard user account when checking performance</span></span>
<span data-ttu-id="df96c-126"><a name="standuser"> </a></span><span class="sxs-lookup"><span data-stu-id="df96c-126"></span></span>

<span data-ttu-id="df96c-127">网站集管理员、 网站所有者、 编辑器或参与者属于其他安全组，具有其他权限，以及因此需要 SharePoint 加载页面的其他元素。</span><span class="sxs-lookup"><span data-stu-id="df96c-127">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="df96c-128">这是适用于 SharePoint 本地和 SharePoint Online，但是内部部署方案中差异将不会很容易发现与 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="df96c-128">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="df96c-129">才能正确评估如何将页面执行的用户，您应使用标准用户帐户以避免加载创作控件和安全组与相关的额外的流量。</span><span class="sxs-lookup"><span data-stu-id="df96c-129">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="df96c-130">用于性能调整的连接类别</span><span class="sxs-lookup"><span data-stu-id="df96c-130">Connection categories for performance tuning</span></span>
<span data-ttu-id="df96c-131"><a name="connect"> </a></span><span class="sxs-lookup"><span data-stu-id="df96c-131"></span></span>

<span data-ttu-id="df96c-p102">您可以将服务器与用户之间的连接分成三个主要部分。设计 SharePoint Online 页面的加载时间时，应该考虑以下事项。</span><span class="sxs-lookup"><span data-stu-id="df96c-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="df96c-134">**服务器。** Microsoft 承载在数据中心中的服务器。</span><span class="sxs-lookup"><span data-stu-id="df96c-134">**Server.** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="df96c-135">**网络。** Microsoft 网络和 Internet 之间的数据中心和您的用户的本地网络。</span><span class="sxs-lookup"><span data-stu-id="df96c-135">**Network.** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="df96c-136">**浏览器。** 其中加载页面。</span><span class="sxs-lookup"><span data-stu-id="df96c-136">**Browser.** Where the page is loaded.</span></span>
    
<span data-ttu-id="df96c-p103">在这三种连接中，95% 的页面缓慢通常是由五种原因所导致。本文中讨论了这些原因：</span><span class="sxs-lookup"><span data-stu-id="df96c-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="df96c-139">导航问题</span><span class="sxs-lookup"><span data-stu-id="df96c-139">Navigation issues</span></span>
    
- <span data-ttu-id="df96c-140">内容汇总</span><span class="sxs-lookup"><span data-stu-id="df96c-140">Content roll up</span></span>
    
- <span data-ttu-id="df96c-141">大型文件</span><span class="sxs-lookup"><span data-stu-id="df96c-141">Large files</span></span>
    
- <span data-ttu-id="df96c-142">对服务器的多个请求</span><span class="sxs-lookup"><span data-stu-id="df96c-142">Many requests to the server</span></span>
    
- <span data-ttu-id="df96c-143">Web 部件处理</span><span class="sxs-lookup"><span data-stu-id="df96c-143">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="df96c-144">服务器连接</span><span class="sxs-lookup"><span data-stu-id="df96c-144">Server connection</span></span>
<span data-ttu-id="df96c-145"><a name="server"> </a></span><span class="sxs-lookup"><span data-stu-id="df96c-145"></span></span>

<span data-ttu-id="df96c-146">很多影响 SharePoint 内部部署的性能的问题也适用于 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="df96c-146">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="df96c-p104">正如您所期望的，在 SharePoint 内部部署中，您对服务器性能的控制力度要强得多。在 SharePoint Online 中则略有不同。您让一台服务器执行的操作越多，呈现页面所需的时间就越长。在 SharePoint 中，在这方面最大的原因是具有多个 Web 部件的复杂页面。</span><span class="sxs-lookup"><span data-stu-id="df96c-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="df96c-151">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="df96c-151">SharePoint Online</span></span>
  
![联机服务器的屏幕截图](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="df96c-153">SharePoint</span><span class="sxs-lookup"><span data-stu-id="df96c-153">SharePoint</span></span>
  
![内部部署服务器的屏幕截图](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="df96c-p105">在 SharePoint Online 中，某些页面请求实际上最终会调用多个服务器。最终可能是服务器之间出现单个请求的请求矩阵。从页面负载的角度来看，这些交互成本很高并将使操作缓慢。</span><span class="sxs-lookup"><span data-stu-id="df96c-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="df96c-158">这些服务器到服务器交互的示例如下：</span><span class="sxs-lookup"><span data-stu-id="df96c-158">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="df96c-159">Web 服务器到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="df96c-159">Web to SQL Servers</span></span>
    
- <span data-ttu-id="df96c-160">Web 服务器到应用程序服务器</span><span class="sxs-lookup"><span data-stu-id="df96c-160">Web to application servers</span></span>
    
<span data-ttu-id="df96c-p106">可能会降低服务器交互速度的另一个原因是缓存未命中。与 SharePoint 内部部署不同，在 SharePoint Online 中有一个非常小的可能，即您可能会命中您之前访问过的页面的相同服务器，这将使对象缓存过时。</span><span class="sxs-lookup"><span data-stu-id="df96c-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="df96c-163">网络连接</span><span class="sxs-lookup"><span data-stu-id="df96c-163">Network connection</span></span>
<span data-ttu-id="df96c-164"><a name="network"> </a></span><span class="sxs-lookup"><span data-stu-id="df96c-164"></span></span>

<span data-ttu-id="df96c-p107">不使用 WAN 进行的本地 SharePoint，您可能使用数据中心和最终用户之间的高速连接。通常，事项易于管理从网络角度。</span><span class="sxs-lookup"><span data-stu-id="df96c-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="df96c-167">在 SharePoint Online 中，有几个因素需要考虑；例如：</span><span class="sxs-lookup"><span data-stu-id="df96c-167">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="df96c-168">Microsoft 网络</span><span class="sxs-lookup"><span data-stu-id="df96c-168">The Microsoft network</span></span>
    
- <span data-ttu-id="df96c-169">Internet</span><span class="sxs-lookup"><span data-stu-id="df96c-169">The Internet</span></span>
    
- <span data-ttu-id="df96c-170">ISP</span><span class="sxs-lookup"><span data-stu-id="df96c-170">The ISP</span></span>
    
<span data-ttu-id="df96c-171">无论使用哪个版本的 SharePoint（和哪个网络），通常会导致网络繁忙的原因包括：</span><span class="sxs-lookup"><span data-stu-id="df96c-171">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="df96c-172">大负载</span><span class="sxs-lookup"><span data-stu-id="df96c-172">Large payload</span></span>
    
- <span data-ttu-id="df96c-173">许多文件</span><span class="sxs-lookup"><span data-stu-id="df96c-173">Many files</span></span>
    
- <span data-ttu-id="df96c-174">到服务器的物理距离较大</span><span class="sxs-lookup"><span data-stu-id="df96c-174">Large physical distance to the server</span></span>
    
<span data-ttu-id="df96c-p108">您可以利用 SharePoint Online 中的一个功能是 Microsoft CDN （内容交付网络）。CDN 基本上是分布式部署跨多个数据中心服务器的集合。CDN 与页面上的内容可以是在服务器上托管接近客户端即使客户端从发起的 SharePoint 服务器远是。Microsoft 将使用此更将来存储页不能自定义，如 SharePoint Online 管理中心主页上的本地实例。有关 Cdn 的详细信息，请参阅[内容交付网络](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)。</span><span class="sxs-lookup"><span data-stu-id="df96c-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="df96c-p109">您需要了解但可能无法执行太多操作的原因是您的 ISP 的连接速度。一个简单的速度测试工具将告诉您连接速度如何。</span><span class="sxs-lookup"><span data-stu-id="df96c-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="df96c-182">浏览器连接</span><span class="sxs-lookup"><span data-stu-id="df96c-182">Browser connection</span></span>
<span data-ttu-id="df96c-183"><a name="browser"> </a></span><span class="sxs-lookup"><span data-stu-id="df96c-183"></span></span>

<span data-ttu-id="df96c-184">从性能的角度来看，使用 Web 浏览器时有几个因素需要考虑。</span><span class="sxs-lookup"><span data-stu-id="df96c-184">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="df96c-p110">访问复杂的页面会影响性能。大多数浏览器只需时平均值较小高速缓存 (约 90 MB) 网页通常是围绕 1.6 MB。这并不需要长，无法获取用完。</span><span class="sxs-lookup"><span data-stu-id="df96c-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="df96c-p111">带宽也可能是问题。例如，如果用户另一个会话中监视视频，这将影响您的 SharePoint 页上的性能。虽然不能阻止用户流式媒体，可以控制的用户将加载页面的方式。</span><span class="sxs-lookup"><span data-stu-id="df96c-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="df96c-191">签出不同 SharePoint Online 页自定义方法的以下文章和其他可帮助您实现最佳性能的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="df96c-191">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="df96c-192">SharePoint Online 的导航选项</span><span class="sxs-lookup"><span data-stu-id="df96c-192">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="df96c-193">SharePoint online 中使用页诊断工具</span><span class="sxs-lookup"><span data-stu-id="df96c-193">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="df96c-194">SharePoint Online 的图像优化</span><span class="sxs-lookup"><span data-stu-id="df96c-194">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="df96c-195">在 SharePoint Online 中延迟加载图像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="df96c-195">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="df96c-196">SharePoint Online 中的缩小和捆绑</span><span class="sxs-lookup"><span data-stu-id="df96c-196">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="df96c-197">使用内容交付网络</span><span class="sxs-lookup"><span data-stu-id="df96c-197">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="df96c-198">使用内容搜索 Web 部件而不内容查询 Web 部件在 SharePoint Online 中提高性能</span><span class="sxs-lookup"><span data-stu-id="df96c-198">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="df96c-199">容量规划和负载测试 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="df96c-199">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="df96c-200">诊断 SharePoint Online 的性能问题</span><span class="sxs-lookup"><span data-stu-id="df96c-200">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="df96c-201">在 SharePoint Online 中使用对象缓存</span><span class="sxs-lookup"><span data-stu-id="df96c-201">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="df96c-202">如何：避免在 SharePoint Online 中受限或受阻止</span><span class="sxs-lookup"><span data-stu-id="df96c-202">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

