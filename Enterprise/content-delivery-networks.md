---
title: 内容分发网络
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
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
description: 使用此信息可了解内容传递网络 (cdn) 以及 Office 365 如何利用它们。
ms.openlocfilehash: 50f28e8311a501d9bc5b3f2c709fa84b1633e418
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "30636093"
---
# <a name="content-delivery-networks"></a>内容传递网络

本主题中的信息将帮助您了解内容传递网络 (cdn) 及其在 Office 365 中的使用方式。

cdn 帮助使最终用户的 Office 365 快速而可靠。 云服务 (如 Office 365) 使用 cdn 将静态资产缓存在更接近的浏览器上, 以加快下载速度并减少延迟。 公共 cdn 允许更快地下载常规内容 (如 javascript 文件、图标和图像), 而私有 cdn 可以提供对用户内容 (如视频和 SharePoint Online 文档库) 的快速、安全访问权限。
  
 **头返回到**[Office 365 的网络规划和性能调整](https://aka.ms/tune)。
  
## <a name="what-exactly-is-a-cdn"></a>CDN 究竟是什么？

cdn 由大多数企业云服务使用。 云服务 (如 Office 365) 有数百万个客户同时下载专有内容 (如电子邮件) 和通用内容 (如图标)。 将图像作为每个人使用的图像 (如图标) 更有效, 尽可能接近用户的计算机。 然而, 每个云服务都不能构建 CDN 数据中心, 以在每个大都市区域中存储此通用内容, 甚至在世界各地的每个主要 Internet 集线器中都可以共享这些内容, 因此其中一些 cdn 是共享的。
  
cdn 可以是私有或公共的。 专用 cdn 由单个公司拥有和运营, 并且只有该公司的应用程序和服务可以使用它。 公共 cdn 由租赁使用多个公司的公司运行。 根据你所在的位置, office 365 为你从 office 365 拥有和运行的 cdn (公用 cdn, 或二者的组合) 中下载通用映像可能效率最高。 无论使用哪种类型的 CDN, 检索数据的步骤都是相同的。
  
1. 您的客户端请求来自 Office 365 的数据。

2. Office 365 要么将数据直接返回给客户端, 要么将客户端定向到 CDN。

3. 如果数据已缓存在 CDN 上, 客户端将直接从最近的 cdn 位置将数据下载到 internet 上的客户端。

4. 如果数据未在 CDN 上缓存, 则 cdn 节点从 Office 365 请求数据, 然后在客户端下载数据后的一段时间内缓存数据。

cdn 从最接近的 Office 365 数据中心中提取文件和图像, 客户端将从最近的 CDN 中提取文件和图像。 当用户访问云服务 (如在 Outlook Web App 中阅读电子邮件) 时, 用户的浏览器将尝试从 Office 365 datacenter 检索文件和图像。 Office 365 将浏览器重定向到 CDN, 而不是花时间和带宽来传递文件。 CDN 将最接近的数据中心输出到用户的浏览器, 使用重定向, 从此处下载通用图像。 使用此 CDN 重定向是快速的, 它会为用户节省大量下载时间。

## <a name="how-do-cdns-make-services-work-faster"></a>cdn 如何使服务更快地工作？

反复下载图标等常见内容会占用网络带宽, 可以更好地用于下载重要的个人内容, 如电子邮件或文档。 由于 Office 365 使用包含 cdn 的体系结构, 因此可以从更接近客户端计算机的服务器上下载图标、脚本和其他通用内容, 从而使下载速度更快。 这意味着可以更快地访问你的个人内容, 这会在 Office 365 数据中心中安全存储。

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>我应该如何设置我的网络, 以便 cdn 最适合使用 Office 365？

如果您正在规划[与 Office 365 的网络连接](network-connectivity.md), 那么了解 cdn 的工作方式以及应如何管理 CDN 网络通信将非常有用。

为 Office 365 租户启用 CDN 时, 首先要设置用于控制内容源 (在 cdn 上下文中称为 "**来源**")、要通过 CDN 分发的数据分类或文件类型的策略。 访问指定内容的用户将被重定向到 CDN 中的最接近文件位置。 因此, 应使用[管理 Office 365 终结点](managing-office-365-endpoints.md)中概述的最佳做法, 以确保您的网络配置允许客户端浏览器直接访问 cdn, 而不是通过中央代理路由 cdn 通信, 以免引入不必要的延迟。

## <a name="is-my-data-safe"></a>我的数据是否安全？

我们非常小心, 帮助确保我们保护业务运营。 存储在 cdn 中的客户特定数据在传输和静止时都进行加密。

> [!NOTE]
> CDN 提供程序可能具有与 Office 365 信任中心所述的承诺不同的隐私和合规性标准。 通过 CDN 服务缓存的数据可能不符合 Microsoft 数据处理术语 (DPT), 并且可能位于 Office 365 信任中心合规性边界之外。

有关 Office 365 CDN 提供程序的隐私和数据保护的详细信息, 请访问以下内容:  

+ 了解有关 Office 365 隐私和数据保护的详细信息, 请参阅[Microsoft 信任中心](https://www.microsoft.com/trustcenter)
+ 了解有关 azure[信任中心](https://azure.microsoft.com/en-us/overview/trusted-cloud/)的 azure 隐私和数据保护的详细信息
+ 了解有关 Akamai 的隐私和数据保护的详细信息[Akamai 隐私信任中心](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>如何使用所有这些第三方服务保护我的网络？

利用广泛的合作伙伴服务集, office 365 可以在使用 office 365 时扩展和满足可用性要求, 并增强用户体验。 第三方服务 Office 365 利用了证书吊销列表, 它们包括:如 crl.microsoft.com 或 sa.symcb.com, 以及 cdn;例如 r3.res.outlook.com。 每个 CDN FQDN Office 365 使用是 Office 365 的自定义 fqdn。 如果您是在 Office 365 请求时发送到 FQDN, 则可以确保 CDN 提供程序控制该位置的 fqdn 和基础内容。
  
对于仍要将来自第三方的请求与 Microsoft 或 Office 365 数据中心的请求隔离的客户, 我们编写了有关[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)的指南。

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>是否有 Office 365 使用的所有 cdn 的列表？

Office 365 中使用的 cdn 始终可能会发生更改, 在许多情况下, 事件1中配置了多个 CDN 伙伴不可用。 使用的主 cdn 为:

+ [Office 365 (专门针对 SharePoint Online 内容)](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)
+ [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)
+ [Akamai](https://www.akamai.com/us/en/cdn.jsp)

这些 CDN 解决方案在全球范围内增强了服务到世界各地的延伸。 存储的内容包括通用的 Office 365 脚本、文件和图像。 例如, 当您登录到 portal.office.com 时, 将从最接近的 CDN 中提取图像以加快页面加载时间。 其他示例包括 Office 365 专业增强版将安装 bits 存储在 CDN 上, 以加快下载最新版本的 Office 所需的时间量。

还有一些存储在 cdn 上的专有内容, 如 Office 365 视频的视频文件。 上载视频后, 文件将被加密, 然后以其加密格式存储在 Azure 媒体服务中。 当 Office 365 视频播放器检索视频时, 先将其缓存到最近的 CDN, 然后再下载, 以加快下载视频所需的时间量。

有关如何使用 office 365 CDN 的信息, 请参阅[将 office 365 内容传递网络与 SharePoint Online 结合使用](use-office-365-cdn-with-spo.md)。

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>是否存在利用 cdn 的所有 fqdn 的列表？

fqdn 列表以及它们如何在一段时间内利用 cdn 更改, 请参阅我们发布的[Office 365 url 和 IP 地址范围](https://go.microsoft.com/fwlink/p/?LinkID=293744)页面, 获取最新使用 cdn 的 fqdn 的日期。

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>我可以在本地网络上使用我自己的 CDN 和缓存内容吗？

我们正在不断寻找新的方法来支持我们的客户需求, 目前正在探索缓存代理解决方案和其他本地 CDN 解决方案的使用。

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>我使用的是适用于 Office 365 的 Azure ExpressRoute, 是否会改变内容？

[适用于 office 365 的 Azure ExpressRoute](azure-expressroute.md)提供了与公共 internet 隔离的 office 365 基础结构的专用连接。 这意味着客户端仍需要通过非 ExpressRoute 连接进行连接, 以连接到 cdn, 而不是显式包含在 ExpressRoute 支持的服务列表中的其他 Microsoft 基础结构。 有关如何路由特定流量 (如发往 cdn 的请求) 的详细信息, 请参阅[Office 365 网络流量管理](routing-with-expressroute.md)。
  
以下是可以用于返回的简短链接：[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>另请参阅

[管理 Office 365 终结点](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[Office 365 URL 和 IP 地址范围](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[结合使用 Office 365 内容传送网络和 SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Microsoft 信任中心](https://www.microsoft.com/trustcenter)