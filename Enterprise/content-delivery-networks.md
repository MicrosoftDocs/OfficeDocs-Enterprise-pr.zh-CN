---
title: 内容传递网络
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: 使用此信息来了解内容交付网络 (Cdn) 和 Office 365 利用它们。Cdn 有助于使 Office 365 快速且可靠保持为最终用户。Cdn，与 Office 365 云服务快速到用户的浏览器在他们正在使用该服务通过 web 客户端下载泛型内容，如图标。
ms.openlocfilehash: bcbab3256a0c1ce601abaf3f8b80e998db4bcece
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539793"
---
# <a name="content-delivery-networks"></a>内容传递网络

使用此信息来了解内容交付网络 (Cdn) 和 Office 365 利用它们。Cdn 有助于使 Office 365 快速且可靠保持为最终用户。Cdn，与 Office 365 云服务快速到用户的浏览器在他们正在使用该服务通过 web 客户端下载泛型内容，如图标。
  
 **在 Head 回**[网络规划和性能优化 Office 365](https://aka.ms/tune)。
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>如何应设置我的网络，以使 Cdn 最适合与 Office 365？

如果您计划[网络连接到 Office 365](network-connectivity.md)，则有助于您了解 Cdn 的工作方式。还有一点了解，您无法连接到 Cdn 筛选 IP 地址。我们为 Office 365，例如 Exchange Online 内的服务提供 Ip 最佳工作量的列表。了解有关[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)我们建议的详细信息。
  
## <a name="how-do-cdns-make-services-work-faster"></a>CDN 如何使服务更快地工作？

下载图标类似的常见任务可能占用可更好地用于下载重要的个人内容，如电子邮件或文档的网络带宽。由于 Office 365 使用体系结构，包括 Cdn、 图标、 脚本和其他泛型内容可以从服务器接近下载到客户端计算机，更快地进行下载。这意味着更快地访问您个人的内容，安全地存储在 Office 365 数据中心。
  
## <a name="what-exactly-is-a-cdn"></a>CDN 到底是什么？

Cdn 使用大多数企业云服务。Office 365 云服务具有数百万客户一次下载专有内容 （如电子邮件） 和通用内容 （如图标） 的组合。它是每个人使用，如图标的图像放置接近尽可能的用户的计算机，更有效。尚未，此文件不适用于每个云服务来构建存储此泛型内容，在每个都市的区域，或即使在世界各地，每个主要 Internet 集线器以便这些 Cdn 的一些共享的 CDN 数据中心。
  
Cdn 可以私有或公有。专用 Cdn 是拥有和运营的单个公司，并且只有该公司的应用程序和服务可以使用它。公共 Cdn 将运行由租赁对多个公司的使用情况的公司。根据您身在何处，它可能最适合您的 Office 365 下载泛型图像您从 Office 365 拥有的 CDN 和运行、 公共 CDN 或二者的组合。无论使用哪种类型的 CDN，则检索数据的步骤都相同。
  
1. 您的客户端从 Office 365 请求数据。

2. Office 365 直接向您的客户端返回数据，或将定向到 CDN 客户端。

3. 如果已在 CDN 缓存数据，则您的客户端下载数据直接从最接近的 CDN 位置到您在 internet 上的客户端。

4. 如果数据不缓存在 CDN，CDN 节点从 Office 365 请求数据，然后缓存的一段时间后将您的客户端下载的数据的数据的方式。

Cdn 提取的文件和图像的最接近的 Office 365 数据中心和您的客户端反过来，最接近的 CDN 中提取了文件和图像。当用户访问云服务，如读取 Outlook Web App 中的电子邮件用户的浏览器将尝试从 Office 365 数据中心中检索文件和图像。而不是花费的时间和提供这些文件的带宽，Office 365 将浏览器重定向的 cdn。CDN 计算出到用户的浏览器的最接近数据中心，并使用重定向，从中下载泛型图像。使用此 CDN 重定向快速，并将用户保存大量下载时间。
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>是否存在的所有利用 Cdn 的 Fqdn 列表？

Fqdn 以及它们如何利用 Cdn 的不断变化的列表是指我们已发布的[Office 365 终结点页](https://go.microsoft.com/fwlink/p/?LinkID=293744)获取最新利用 Cdn 的最新 Fqdn。
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>是否存在的 Office 365 使用的所有 Cdn 列表？

使用 Office 365 Cdn 始终是恕和在许多情况下有多个 CDN 合作伙伴配置在事件之一是不可用。使用两个最常见 Cdn 是[Akamai](https://www.akamai.com/us/en/cdn.jsp)和[Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)。这两种 CDN 解决方案具有增强的多个角的世界服务访问的全球运营。存在存储的内容包括常规的 Office 365 脚本、 文件和图像。例如，当您登录到 portal.office.com，图像提取从最接近的 CDN 以加速调制页面加载时间。其他示例包括 Office 365 ProPlus 安装二进制文件存储在 CDN 以加速调制下载最新版本的 Office 所花的时间量。此外，还有一些专用存储的内容上 Cdn 如视频文件的 Office 365 视频。一旦您上载视频，文件加密，然后存储与 Azure Media Services 其加密格式。Office 365 视频播放器检索视频时它是第一次缓存到最接近的 CDN 之前下载以加速调制计以下载该视频的时间量。
  
## <a name="does-office-365-offer-a-cdn-that-i-can-use-for-my-own-files"></a>Office 365 提供可为我自己的文件使用的 CDN 呢？

是的！现在您的 Office 365 订阅包括独立于可以使用专门为您的 SharePoint Online 资产的 Azure 的 CDN。有关如何使用 Office 365 CDN 的信息，请参阅[使用 SharePoint Online 的 Office 365 内容交付网络](use-office-365-cdn-with-spo.md)。
  
## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>可以在我的本地网络上使用我自己 CDN 和缓存的内容？

我们不断正在寻找新方法，以支持客户的需要，在当前探索使用缓存代理解决方案和其他内部部署 CDN 解决方案。
  
## <a name="is-my-data-safe"></a>我的数据是否安全？

我们需要谨慎以帮助确保我们保护运行您的业务数据。存储在内容交付网络合作伙伴的项加密;例如，与[Office 365 视频](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e)或不客户特定;如 Office 365 ProPlus 的安装文件。通过[Office 365 信任中心](https://go.microsoft.com/fwlink/p/?LinkId=397383)以了解有关保护您的数据和您的隐私我们深入努力上标题。
  
## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>如何保护我的网络与所有这些第三方服务？

利用一组广泛的合作伙伴服务允许 Office 365 扩展和满足可用性要求，以及使用 Office 365 时增强用户体验。Office 365 利用第三方服务包括两个证书吊销列表;如 crl.microsoft.com 或 sa.symcb.com 和 Cdn;如 r3.res.outlook.com。每个 CDN FQDN Office 365 使用的自定义 Office 365 的 FQDN，如果您正在发送到 Office 365 的请求的 FQDN 您可以确信，我们控制 FQDN 和基础的内容在该位置。
  
客户的仍要将请求发送到 Microsoft 或 Office 365 数据中心中，从第三方，发往请求数据库分隔到我们编写 up 指南上[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>我使用的 Office 365 的 Azure ExpressRoute，不会更改操作？

[Office 365 的 azure ExpressRoute](azure-expressroute.md)从公共 internet 提供与隔离的 Office 365 基础结构的专用的连接。这意味着客户端将仍需要通过非 ExpressRoute 连接来连接到 Cdn 和其他 Microsoft 基础结构支持 ExpressRoute 的服务列表中未明确包括的连接。有关如何将如发往 Cdn 的请求的特定流量路由的详细信息，请参阅[Office 365 网络流量管理](routing-with-expressroute.md)。
  
这是一个简短的链接，您可以使用回来：[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>另请参阅

[Office 365 终结点常见问题](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
