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
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219872"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>SharePoint Online 性能调整简介

本文介绍了您需要时设计页面以在 SharePoint Online 中的最佳性能，请考虑哪些特定方面。
     
## <a name="sharepoint-online-metrics"></a>SharePoint Online 的指标

SharePoint Online 的以下广泛指标提供有关性能的实际数据：
  
- 页面加载的速度
    
- 每页所需的往返行程数
    
- 服务存在的问题
    
- 导致性能下降的其他原因
    
### <a name="conclusions-reached-because-of-the-data"></a>根据数据得出的结论

数据告诉我们：
  
- 大多数页面在 SharePoint Online 上运行良好。
    
- 非自定义页面加载速度非常快。
    
- OneDrive for Business、工作组网站和系统页面（如 _layouts）等的加载速度都很快。
    
- 最慢的 1% 的 SharePoint Online 页面的加载时间超过 5000 毫秒。
    
您可以使用的一个简单的基准测试是将您自己门户的加载时间与 OneDrive for Business 主页的加载时间进行比较以衡量性能，因为后者几乎不使用自定义性能。这通常是支持人员在对网络性能问题进行故障排除时将要求您完成的第一步。
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>检查性能时使用标准用户帐户

网站集管理员、 网站所有者、 编辑器或参与者属于其他安全组，具有其他权限，以及因此需要 SharePoint 加载页面的其他元素。
  
这是适用于 SharePoint 本地和 SharePoint Online，但是内部部署方案中差异将不会很容易发现与 SharePoint Online。
  
才能正确评估如何将页面执行的用户，您应使用标准用户帐户以避免加载创作控件和安全组与相关的额外的流量。
  
## <a name="connection-categories-for-performance-tuning"></a>用于性能调整的连接类别

您可以将服务器与用户之间的连接分成三个主要部分。设计 SharePoint Online 页面的加载时间时，应该考虑以下事项。
  
- **服务器**Microsoft 承载在数据中心中的服务器。
    
- **网络**Microsoft 网络和 Internet 之间的数据中心和您的用户的本地网络。
    
- **浏览器**其中加载页面。
    
在这三种连接中，95% 的页面缓慢通常是由五种原因所导致。本文中讨论了这些原因：
  
- 导航问题
    
- 内容汇总
    
- 大型文件
    
- 对服务器的多个请求
    
- Web 部件处理
    
### <a name="server-connection"></a>服务器连接

很多影响 SharePoint 内部部署的性能的问题也适用于 SharePoint Online。
  
正如您所期望的，在 SharePoint 内部部署中，您对服务器性能的控制力度要强得多。在 SharePoint Online 中则略有不同。您让一台服务器执行的操作越多，呈现页面所需的时间就越长。在 SharePoint 中，在这方面最大的原因是具有多个 Web 部件的复杂页面。
  
SharePoint Server 内部部署
  
![内部部署服务器的屏幕截图](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![联机服务器的屏幕截图](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
在 SharePoint Online 中，某些页面请求实际上最终会调用多个服务器。最终可能是服务器之间出现单个请求的请求矩阵。从页面负载的角度来看，这些交互成本很高并将使操作缓慢。
  
这些服务器到服务器交互的示例如下：
  
- Web 服务器到 SQL Server
    
- Web 服务器到应用程序服务器
    
可能会降低服务器交互速度的另一个原因是缓存未命中。与 SharePoint 内部部署不同，在 SharePoint Online 中有一个非常小的可能，即您可能会命中您之前访问过的页面的相同服务器，这将使对象缓存过时。
  
### <a name="network-connection"></a>网络连接

不使用 WAN 进行的本地 SharePoint，您可能使用数据中心和最终用户之间的高速连接。通常，事项易于管理从网络角度。
  
在 SharePoint Online 中，有几个因素需要考虑；例如：
  
- Microsoft 网络
    
- Internet
    
- ISP
    
无论使用哪个版本的 SharePoint（和哪个网络），通常会导致网络繁忙的原因包括：
  
- 大负载
    
- 许多文件
    
- 到服务器的物理距离较大
    
您可以利用 SharePoint Online 中的一个功能是 Microsoft CDN （内容交付网络）。CDN 基本上是分布式部署跨多个数据中心服务器的集合。CDN 与页面上的内容可以是在服务器上托管接近客户端即使客户端从发起的 SharePoint 服务器远是。Microsoft 将使用此更将来存储页不能自定义，如 SharePoint Online 管理中心主页上的本地实例。有关 Cdn 的详细信息，请参阅[内容交付网络](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks)。
  
您需要了解但可能无法执行太多操作的原因是您的 ISP 的连接速度。一个简单的速度测试工具将告诉您连接速度如何。
  
### <a name="browser-connection"></a>浏览器连接

从性能的角度来看，使用 Web 浏览器时有几个因素需要考虑。
  
访问复杂的页面会影响性能。大多数浏览器只需时平均值较小高速缓存 (约 90 MB) 网页通常是围绕 1.6 MB。这并不需要长，无法获取用完。
  
带宽也可能是问题。例如，如果用户另一个会话中监视视频，这将影响您的 SharePoint 页上的性能。虽然不能阻止用户流式媒体，可以控制的用户将加载页面的方式。
  
签出不同 SharePoint Online 页自定义方法的以下文章和其他可帮助您实现最佳性能的最佳做法。
  
- [SharePoint Online 的导航选项](navigation-options-for-sharepoint-online.md)
    
- [SharePoint online 中使用页诊断工具](page-diagnostics-for-spo.md)
    
- [SharePoint Online 的图像优化](image-optimization-for-sharepoint-online.md)
    
- [在 SharePoint Online 中延迟加载图像和 JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [SharePoint Online 中的缩小和捆绑](minification-and-bundling-in-sharepoint-online.md)
    
- [使用内容交付网络](using-content-delivery-networks-with-sharepoint-online.md)
    
- [使用内容搜索 Web 部件而不内容查询 Web 部件在 SharePoint Online 中提高性能](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [容量规划和负载测试 SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [诊断 SharePoint Online 性能问题](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [在 SharePoint Online 中使用对象缓存](using-the-object-cache-with-sharepoint-online.md)
    
- [如何：避免在 SharePoint Online 中受限或受阻止](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

