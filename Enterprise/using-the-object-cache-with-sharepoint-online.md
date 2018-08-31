---
title: 在 SharePoint Online 中使用对象缓存
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: 本文介绍使用对象缓存中部署 SharePoint Server 2013 和 SharePoint Online 之间的差异。
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539686"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="ce767-103">在 SharePoint Online 中使用对象缓存</span><span class="sxs-lookup"><span data-stu-id="ce767-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="ce767-104">本文介绍使用对象缓存中部署 SharePoint Server 2013 和 SharePoint Online 之间的差异。</span><span class="sxs-lookup"><span data-stu-id="ce767-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="ce767-p101">依赖于 SharePoint Online 部署中的对象缓存不会产生严重的负面影响。对 SharePoint Online 中的对象缓存的任何依赖都会降低您的页面的可靠性。</span><span class="sxs-lookup"><span data-stu-id="ce767-p101">There is significant negative impact of relying on the object cache in SharePoint Online deployment. Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="ce767-107">SharePoint Online 和 SharePoint Server 2013 如何对象缓存的工作原理</span><span class="sxs-lookup"><span data-stu-id="ce767-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="ce767-p102">承载内部部署 SharePoint Server 2013 后，客户可以承载对象缓存的专用的前端 web 服务器。这意味着缓存专用于一个客户并仅受多少内存已提供并已分配给对象缓存。由于只有一个客户服务的内部部署方案的服务的前端 web 服务器通常有反复到相同的站点发出请求的用户。这意味着缓存完整快速获取并保持完整的列表查询结果和您的用户定期请求的 SharePoint 对象。</span><span class="sxs-lookup"><span data-stu-id="ce767-p102">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache. This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache. Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over. This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![显示内部部署前端 Web 服务器的流量和负载](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="ce767-p103">因此，当用户第二次访问页面时，页面加载时间将有所改善。加载同一页面至少四次后，页面将缓存在所有前端 Web 服务器上。</span><span class="sxs-lookup"><span data-stu-id="ce767-p103">As a result, the second time a user visits a page, the page load time improves. After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="ce767-p104">相比之下，SharePoint Online 中有很多更多的服务器，但也很多更多的网站。每个用户可以连接到的其他前端 web 服务器上没有填充缓存。或者，也许执行获取缓存填充的一个服务器，但该前端 web 服务器的下一个用户请求中不同网站的页面。或者，即使下一个用户请求与对其前一次访问同一页面，它们是到其缓存中没有该页面的其他前端 web 服务器负载平衡。在此最后的情况下，缓存不帮助用户在所有。</span><span class="sxs-lookup"><span data-stu-id="ce767-p104">In contrast, in SharePoint Online there are many more servers but also many more sites. Each user may connect to a different front-end web server that doesn't have the cache populated. Or, perhaps the cache does get populated for a server, but the the next user to that front-end web server requests a page from a different site. Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache. In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="ce767-p105">在下图中，每个圆点表示用户正在请求的页面和它缓存的页面。不同的颜色代表不同的客户正在共享 SaaS 基础结构。</span><span class="sxs-lookup"><span data-stu-id="ce767-p105">In the following figure, each dot represents a page that a user is requesting and where it cached. Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![显示 SharePoint Online 中的对象缓存结果](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="ce767-p106">您可以看到从关系图，其页面的缓存版本与服务器的任何给定用户的可能性很小。另外，由于的大的吞吐量和服务器的多个网站之间共享的事实，缓存不上次长由于没有可用的仅如此多空间来缓存。</span><span class="sxs-lookup"><span data-stu-id="ce767-p106">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim. Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="ce767-125">由于这些原因，依赖于获取缓存的对象的用户不是确保 SharePoint Online 中的优质用户体验和页面加载时间的有效方法。</span><span class="sxs-lookup"><span data-stu-id="ce767-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="ce767-126">如果我们不能依赖于对象缓存来提高 SharePoint Online 中的性能，那么我们应该怎么办？</span><span class="sxs-lookup"><span data-stu-id="ce767-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="ce767-p107">因为您不应依赖于在 SharePoint Online 中缓存，您应评估使用对象缓存的 SharePoint 自定义的备用设计方法。这意味着使用不依赖于对象缓存的针对性能问题的方法来为用户提供良好的结果。本系列中的其他文章中也描述了这一问题，包括：</span><span class="sxs-lookup"><span data-stu-id="ce767-p107">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache. This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users. This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="ce767-130">SharePoint Online 的导航选项</span><span class="sxs-lookup"><span data-stu-id="ce767-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="ce767-131">SharePoint Online 中的缩小和捆绑</span><span class="sxs-lookup"><span data-stu-id="ce767-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="ce767-132">使用内容交付网络</span><span class="sxs-lookup"><span data-stu-id="ce767-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="ce767-133">在 SharePoint Online 中延迟加载图像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="ce767-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

