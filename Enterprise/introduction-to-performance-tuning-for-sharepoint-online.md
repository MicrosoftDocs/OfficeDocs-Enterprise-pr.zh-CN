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
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>SharePoint Online 性能优化简介

本文介绍在设计页面以在 SharePoint Online 中实现最佳性能时需要考虑的特定方面。
     
## <a name="sharepoint-online-metrics"></a>SharePoint Online 指标

SharePoint Online 的以下广义指标提供了有关性能的真实世界数据：
  
- 页面加载速度
    
- 每页所需的往返行程数
    
- 服务的问题
    
- 导致性能下降的其他因素
    
### <a name="conclusions-reached-because-of-the-data"></a>由于数据的原因而达到的结论

数据告诉我们：
  
- 大多数页面在 SharePoint Online 上性能良好。
    
- 非自定义页面的加载速度非常快。
    
- OneDrive for Business、工作组网站和系统页面（如 _layouts 等）都是快速加载的。
    
- 最慢的1% 的 SharePoint Online 页面的加载时间超过5000毫秒。
    
您可以使用的一种简单基准测试是通过将您自己的门户的加载时间与 OneDrive for business 主页的加载时间进行比较，因为它使用了极少的自定义功能来衡量性能。 这通常是在排除网络性能问题时，第一步支持将会要求你完成此过程。
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>检查性能时使用标准用户帐户

网站集管理员、网站所有者、编辑者或参与者属于其他安全组，具有其他权限，因此在页面上有 SharePoint 加载的其他元素。
  
这适用于 SharePoint 本地和 SharePoint Online，但在本地方案中，差别并不像在 SharePoint Online 中那样容易察觉。
  
为了正确评估页面对用户的执行方式，应使用标准用户帐户来避免加载创作控件以及与安全组相关的其他流量。
  
## <a name="connection-categories-for-performance-tuning"></a>用于性能优化的连接类别

您可以将服务器和用户之间的连接分类为三个主要组件。 在设计 SharePoint Online 页以深入了解加载时间时，请考虑这些情况。
  
- **Server**Microsoft 在数据中心中托管的服务器。
    
- **网络**数据中心和用户之间的 Microsoft 网络、Internet 和本地网络。
    
- **浏览器**页面的加载位置。
    
在这三种连接中，通常有五个原因导致慢速页面的95%。 本文中讨论了上述每个原因：
  
- 导航问题
    
- 内容汇总
    
- 大型文件
    
- 对服务器的多个请求
    
- Web 部件处理
    
### <a name="server-connection"></a>服务器连接

许多影响 SharePoint 本地的性能的问题也适用于 SharePoint Online。
  
正如您所期望的那样，您可以在多大程度上控制服务器如何使用本地 SharePoint 进行操作。 SharePoint Online 的内容稍有不同。 您所做的工作越多，呈现页面所需的时间就越长。 在 SharePoint 中，此方面最大的原因是具有多个 web 部件的复杂页面。
  
SharePoint Server 本地
  
![内部部署服务器的屏幕截图](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![联机服务器的屏幕截图](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
通过 SharePoint Online，某些页面请求实际上可能会结束呼叫多台服务器。 您最终可能会在服务器之间请求单个请求的请求矩阵。 从页面加载角度来看，这些交互成本很高，并且会导致速度变慢。
  
这些服务器与服务器交互的示例如下：
  
- Web 到 SQL Server
    
- Web 到应用程序服务器
    
可能导致服务器交互下降的另一件事是缓存未命中。 与本地 SharePoint 不同的是，您可能会遇到一种极轻巧的情况，即您对以前访问过的页面的同一服务器进行了访问;这会使对象缓存过时。
  
### <a name="network-connection"></a>网络连接

使用不使用 WAN 的本地 SharePoint 时，您可以在数据中心和最终用户之间使用高速连接。 通常情况下，从网络的角度来看可以轻松地管理内容。
  
在 SharePoint Online 中，还有其他几个因素需要考虑;例如：
  
- Microsoft 网络
    
- Internet
    
- ISP
    
无论使用的是哪个版本的 SharePoint （和哪个网络），通常会导致网络处于忙碌状态的内容包括：
  
- 大型有效负载
    
- 许多文件
    
- 与服务器的物理距离较大
    
您可以在 SharePoint Online 中使用的一项功能是 Microsoft CDN （内容传递网络）。 CDN 基本上是跨多个数据中心部署的服务器的分布式集合。 利用 CDN，页面上的内容可以托管在服务器附近，即使客户端离原始 SharePoint 服务器远。 Microsoft 将在将来使用此信息来存储无法自定义的页面的本地实例，例如 SharePoint Online 管理中心主页。 有关 Cdn 的详细信息，请参阅[Content 传递网络](https://docs.microsoft.com/office365/enterprise/content-delivery-networks)。
  
您需要注意但可能无法完成的操作是您的 ISP 的连接速度。 简单的速度测试工具将告诉您连接速度。
  
### <a name="browser-connection"></a>浏览器连接

从性能角度来看，有几个因素需要考虑 web 浏览器。
  
访问复杂页面会影响性能。 大多数浏览器只有较小的缓存（围绕90MB），而平均网页通常约为 1.6 MB。 使用此设置不需要很长时间。
  
带宽也可能是一个问题。 例如，如果用户在另一个会话中观看视频，这将影响 SharePoint 页面的性能。 虽然您无法阻止用户处理媒体，但您可以控制页面加载用户的方式。
  
请查看以下文章，了解不同的 SharePoint Online 页面自定义技术和其他最佳实践，以帮助你实现最佳性能。
  
- [SharePoint Online 的导航选项](navigation-options-for-sharepoint-online.md)
    
- [使用 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)
    
- [SharePoint Online 的图像优化](image-optimization-for-sharepoint-online.md)
    
- [在 SharePoint Online 中延迟加载图像和 JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [SharePoint Online 中的缩小和捆绑](minification-and-bundling-in-sharepoint-online.md)
    
- [使用内容交付网络](using-content-delivery-networks-with-sharepoint-online.md)
    
- [使用内容搜索 Web 部件而不是内容查询 Web 部件来提高 SharePoint Online 中的性能](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [容量规划和负载测试 SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [诊断 SharePoint Online 性能问题](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [在 SharePoint Online 中使用对象缓存](using-the-object-cache-with-sharepoint-online.md)
    
- [如何：避免在 SharePoint Online 中受限制或被阻止](https://msdn.microsoft.com/library/office/dn889829.aspx)
    

