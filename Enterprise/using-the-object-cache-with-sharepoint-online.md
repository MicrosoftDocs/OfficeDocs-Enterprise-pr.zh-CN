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
ms.openlocfilehash: 59f3a69199893cb367d4d28c0c545ebd9dfd1236
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "25769851"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>在 SharePoint Online 中使用对象缓存

本文介绍使用对象缓存中部署 SharePoint Server 2013 和 SharePoint Online 之间的差异。
  
依赖于 SharePoint Online 部署中的对象缓存不会产生严重的负面影响。对 SharePoint Online 中的对象缓存的任何依赖都会降低您的页面的可靠性。 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>SharePoint Online 和 SharePoint Server 2013 如何对象缓存的工作原理

承载内部部署 SharePoint Server 2013 后，客户可以承载对象缓存的专用的前端 web 服务器。这意味着缓存专用于一个客户并仅受多少内存已提供并已分配给对象缓存。由于只有一个客户服务的内部部署方案的服务的前端 web 服务器通常有反复到相同的站点发出请求的用户。这意味着缓存完整快速获取并保持完整的列表查询结果和您的用户定期请求的 SharePoint 对象。
  
![显示内部部署前端 Web 服务器的流量和负载](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
因此，当用户第二次访问页面时，页面加载时间将有所改善。加载同一页面至少四次后，页面将缓存在所有前端 Web 服务器上。
  
相比之下，SharePoint Online 中有很多更多的服务器，但也很多更多的网站。每个用户可以连接到的其他前端 web 服务器上没有填充缓存。或者，也许执行获取填充缓存的一个服务器，但该下一个用户的页上的前端 web 服务器请求从其他网站。或者，即使下一个用户请求与对其前一次访问同一页面，它们是到其缓存中没有该页面的其他前端 web 服务器负载平衡。在此最后的情况下，缓存不帮助用户在所有。
  
在下图中，每个圆点表示用户正在请求的页面和它缓存的页面。不同的颜色代表不同的客户正在共享 SaaS 基础结构。
  
![显示 SharePoint Online 中的对象缓存结果](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
您可以看到从关系图，其页面的缓存版本与服务器的任何给定用户的可能性很小。另外，由于的大的吞吐量和服务器的多个网站之间共享的事实，缓存不上次长由于没有可用的仅如此多空间来缓存。
  
由于这些原因，依赖于获取缓存的对象的用户不是确保 SharePoint Online 中的优质用户体验和页面加载时间的有效方法。
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>如果我们不能依赖于对象缓存来提高 SharePoint Online 中的性能，那么我们应该怎么办？

因为您不应依赖于在 SharePoint Online 中缓存，您应评估使用对象缓存的 SharePoint 自定义的备用设计方法。这意味着使用不依赖于对象缓存的针对性能问题的方法来为用户提供良好的结果。本系列中的其他文章中也描述了这一问题，包括：
  
- [SharePoint Online 的导航选项](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online 中的缩小和捆绑](minification-and-bundling-in-sharepoint-online.md)
    
- [使用内容交付网络](using-content-delivery-networks-with-sharepoint-online.md)
    
- [在 SharePoint Online 中延迟加载图像和 JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

