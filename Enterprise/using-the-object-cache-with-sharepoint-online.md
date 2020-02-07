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
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: 本文说明在 SharePoint Server 2013 本地和 SharePoint Online 中使用对象缓存的区别。
ms.openlocfilehash: 24d58b692667c897d2f25d41d4216a74382a5390
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841040"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>在 SharePoint Online 中使用对象缓存

本文说明在 SharePoint Server 2013 本地和 SharePoint Online 中使用对象缓存的区别。
  
依赖于 SharePoint Online 部署中的对象缓存有严重的负面影响。 对 SharePoint Online 中的对象缓存的任何依赖项都会降低页面的可靠性。 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>SharePoint Online 和 SharePoint Server 2013 对象缓存的工作原理

当 SharePoint Server 2013 托管在本地托管时，客户拥有承载对象缓存的专用前端 web 服务器。 这意味着缓存专用于一个客户，并且仅受可用内存和分配给对象缓存的内存量的限制。 由于在本地方案中仅提供了一个客户，因此前端 web 服务器通常会让用户在同一站点之间进行请求。 这意味着缓存会快速获取，并将完全保留您的用户在定期请求的列表查询结果和 SharePoint 对象。
  
![显示内部部署前端 Web 服务器的流量和负载](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
因此，用户第二次访问页面时，页面加载时间会提高。 在同一页面至少有四个加载后，页面将缓存在所有前端 web 服务器上。
  
相比之下，在 SharePoint Online 中，还有许多服务器，还有更多的网站。 每个用户都可以连接到未填充缓存的不同前端 web 服务器。 或者，可能是为服务器填充了缓存，但下一个用户对该前端 web 服务器的请求来自不同网站的页面。 或者，即使下一个用户请求的页面与之前访问的相同，也会将其负载平衡到在其缓存中不包含该页面的其他前端 web 服务器。 在这种情况下，缓存根本无法帮助用户。
  
在下图中，每个点表示用户正在请求的页面以及缓存的位置。 不同的颜色代表共享使用 SaaS 基础结构的不同客户。
  
![显示 SharePoint Online 中的对象缓存结果](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
正如您在图表中看到的那样，任何给定用户在其页面的缓存版本中命中一台服务器的机率都很轻巧。 此外，由于较大的吞吐量以及服务器在很多站点之间共享，因此缓存不会持续很长时间，因为只有这么多的空间可用于缓存。
  
出于上述所有原因，依赖于获取缓存对象的用户并不是确保 SharePoint Online 中的质量用户体验和页面加载时间的有效方法。
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>如果我们无法依赖对象缓存来提高 SharePoint Online 中的性能，我们应改用什么？

由于不应依赖 SharePoint Online 中的缓存，因此应评估使用对象缓存的 SharePoint 自定义的替代设计方法。 这意味着，使用的是性能问题的方法，这些问题不依赖于对象缓存来为用户生成有用的结果。 此系列中的一些其他文章中对此进行了说明，包括：
  
- [SharePoint Online 的导航选项](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online 中的缩小和捆绑](minification-and-bundling-in-sharepoint-online.md)
    
- [使用内容交付网络](using-content-delivery-networks-with-sharepoint-online.md)
    
- [在 SharePoint Online 中延迟加载图像和 JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

