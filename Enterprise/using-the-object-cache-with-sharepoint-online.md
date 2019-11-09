---
title: 在 SharePoint Online 中使用对象缓存
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: 本文说明在 SharePoint Server 2013 本地和 SharePoint Online 中使用对象缓存的区别。
ms.openlocfilehash: 4c6cd225bf0f7324dcb23c55adb87e2365d35472
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078021"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="0899c-103">在 SharePoint Online 中使用对象缓存</span><span class="sxs-lookup"><span data-stu-id="0899c-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="0899c-104">本文说明在 SharePoint Server 2013 本地和 SharePoint Online 中使用对象缓存的区别。</span><span class="sxs-lookup"><span data-stu-id="0899c-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="0899c-105">依赖于 SharePoint Online 部署中的对象缓存有严重的负面影响。</span><span class="sxs-lookup"><span data-stu-id="0899c-105">There is significant negative impact of relying on the object cache in SharePoint Online deployment.</span></span> <span data-ttu-id="0899c-106">对 SharePoint Online 中的对象缓存的任何依赖项都会降低页面的可靠性。</span><span class="sxs-lookup"><span data-stu-id="0899c-106">Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="0899c-107">SharePoint Online 和 SharePoint Server 2013 对象缓存的工作原理</span><span class="sxs-lookup"><span data-stu-id="0899c-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="0899c-108">当 SharePoint Server 2013 托管在本地托管时，客户拥有承载对象缓存的专用前端 web 服务器。</span><span class="sxs-lookup"><span data-stu-id="0899c-108">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache.</span></span> <span data-ttu-id="0899c-109">这意味着缓存专用于一个客户，并且仅受可用内存和分配给对象缓存的内存量的限制。</span><span class="sxs-lookup"><span data-stu-id="0899c-109">This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache.</span></span> <span data-ttu-id="0899c-110">由于在本地方案中仅提供了一个客户，因此前端 web 服务器通常会让用户在同一站点之间进行请求。</span><span class="sxs-lookup"><span data-stu-id="0899c-110">Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over.</span></span> <span data-ttu-id="0899c-111">这意味着缓存会快速获取，并将完全保留您的用户在定期请求的列表查询结果和 SharePoint 对象。</span><span class="sxs-lookup"><span data-stu-id="0899c-111">This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![显示内部部署前端 Web 服务器的流量和负载](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="0899c-113">因此，用户第二次访问页面时，页面加载时间会提高。</span><span class="sxs-lookup"><span data-stu-id="0899c-113">As a result, the second time a user visits a page, the page load time improves.</span></span> <span data-ttu-id="0899c-114">在同一页面至少有四个加载后，页面将缓存在所有前端 web 服务器上。</span><span class="sxs-lookup"><span data-stu-id="0899c-114">After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="0899c-115">相比之下，在 SharePoint Online 中，还有许多服务器，还有更多的网站。</span><span class="sxs-lookup"><span data-stu-id="0899c-115">In contrast, in SharePoint Online there are many more servers but also many more sites.</span></span> <span data-ttu-id="0899c-116">每个用户都可以连接到未填充缓存的不同前端 web 服务器。</span><span class="sxs-lookup"><span data-stu-id="0899c-116">Each user may connect to a different front-end web server that doesn't have the cache populated.</span></span> <span data-ttu-id="0899c-117">或者，可能是为服务器填充了缓存，但下一个用户对该前端 web 服务器的请求来自不同网站的页面。</span><span class="sxs-lookup"><span data-stu-id="0899c-117">Or, perhaps the cache does get populated for a server, but the next user to that front-end web server requests a page from a different site.</span></span> <span data-ttu-id="0899c-118">或者，即使下一个用户请求的页面与之前访问的相同，也会将其负载平衡到在其缓存中不包含该页面的其他前端 web 服务器。</span><span class="sxs-lookup"><span data-stu-id="0899c-118">Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache.</span></span> <span data-ttu-id="0899c-119">在这种情况下，缓存根本无法帮助用户。</span><span class="sxs-lookup"><span data-stu-id="0899c-119">In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="0899c-120">在下图中，每个点表示用户正在请求的页面以及缓存的位置。</span><span class="sxs-lookup"><span data-stu-id="0899c-120">In the following figure, each dot represents a page that a user is requesting and where it cached.</span></span> <span data-ttu-id="0899c-121">不同的颜色代表共享使用 SaaS 基础结构的不同客户。</span><span class="sxs-lookup"><span data-stu-id="0899c-121">Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![显示 SharePoint Online 中的对象缓存结果](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="0899c-123">正如您在图表中看到的那样，任何给定用户在其页面的缓存版本中命中一台服务器的机率都很轻巧。</span><span class="sxs-lookup"><span data-stu-id="0899c-123">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim.</span></span> <span data-ttu-id="0899c-124">此外，由于较大的吞吐量以及服务器在很多站点之间共享，因此缓存不会持续很长时间，因为只有这么多的空间可用于缓存。</span><span class="sxs-lookup"><span data-stu-id="0899c-124">Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="0899c-125">出于上述所有原因，依赖于获取缓存对象的用户并不是确保 SharePoint Online 中的质量用户体验和页面加载时间的有效方法。</span><span class="sxs-lookup"><span data-stu-id="0899c-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="0899c-126">如果我们无法依赖对象缓存来提高 SharePoint Online 中的性能，我们应改用什么？</span><span class="sxs-lookup"><span data-stu-id="0899c-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="0899c-127">由于不应依赖 SharePoint Online 中的缓存，因此应评估使用对象缓存的 SharePoint 自定义的替代设计方法。</span><span class="sxs-lookup"><span data-stu-id="0899c-127">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache.</span></span> <span data-ttu-id="0899c-128">这意味着，使用的是性能问题的方法，这些问题不依赖于对象缓存来为用户生成有用的结果。</span><span class="sxs-lookup"><span data-stu-id="0899c-128">This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users.</span></span> <span data-ttu-id="0899c-129">此系列中的一些其他文章中对此进行了说明，包括：</span><span class="sxs-lookup"><span data-stu-id="0899c-129">This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="0899c-130">SharePoint Online 的导航选项</span><span class="sxs-lookup"><span data-stu-id="0899c-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="0899c-131">SharePoint Online 中的缩小和捆绑</span><span class="sxs-lookup"><span data-stu-id="0899c-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="0899c-132">使用内容交付网络</span><span class="sxs-lookup"><span data-stu-id="0899c-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="0899c-133">在 SharePoint Online 中延迟加载图像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="0899c-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

