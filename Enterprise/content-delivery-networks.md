---
title: 内容分发网络
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/22/2019
audience: ITPro
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
description: 使用此信息了解 Office 365 如何使用内容传递网络（Cdn）来提高性能。
ms.openlocfilehash: 7b9ef7a3742dbbccbc052eca28469c4fb10cdae1
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38029116"
---
# <a name="content-delivery-networks-cdns"></a>内容传递网络（Cdn）

Cdn 帮助使最终用户的 Office 365 快速而可靠。 云服务（如 Office 365）使用 Cdn 将静态资产缓存在更接近的浏览器上，以加快下载速度并降低感觉到的最终用户延迟。 本主题中的信息将帮助您了解内容传递网络（Cdn）及其在 Office 365 中的使用方式。

## <a name="what-exactly-is-a-cdn"></a>CDN 究竟是什么？

CDN 是地理位置分散的网络，由高速骨干网连接的数据中心中的代理服务器和文件服务器组成。 Cdn 用于减少网站或服务中一组指定的文件和对象的延迟和加载时间。 CDN 可能有数千个终结点，可用于从任何位置对传入请求进行最佳处理。

Cdn 通常用于为网站或服务（如 javascript 文件、图标和图像）提供更快的常规内容下载，还可以提供对用户内容（如 SharePoint Online 文档库中的文件、流式媒体文件）的专用访问和自定义代码。

Cdn 由大多数企业云服务使用。 云服务（如 Office 365）有数百万个客户同时下载专有内容（如电子邮件）和通用内容（如图标）。 将图像作为每个人使用的图像（如图标）更有效，尽可能接近用户的计算机。 在每个大都市区域中（甚至在世界各地的每个主要 Internet 集线器中）构建 CDN 数据中心时，每个云服务都不切合实际，因此其中一些 Cdn 是共享的。

## <a name="how-do-cdns-make-services-work-faster"></a>Cdn 如何使服务更快地工作？

同时下载常见对象（如网站图像和图标）可能会占用网络带宽，可以更好地用于下载重要的个人内容，如电子邮件或文档。 由于 Office 365 使用包含 Cdn 的体系结构，因此可以从更接近客户端计算机的服务器上下载图标、脚本和其他通用内容，从而使下载速度更快。 这意味着可以更快地访问你的个人内容，这会在 Office 365 数据中心中安全存储。

Cdn 帮助以多种方式改进云服务性能：

- Cdn 将网络和文件下载负担的一部分从云服务中移出，从而通过减少为静态资产提供服务请求的需求而释放云服务资源，以提供用户内容和其他服务。
- Cdn 是专门为提供低延迟文件访问而构建的，通过实现高性能的网络和文件服务器，以及利用更新的网络协议（如[HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) ）以及高效率的压缩和请求多路复用。
- CDN 网络使用许多全局分布式终结点使内容可尽可能接近用户。

## <a name="the-office-365-cdn"></a>Office 365 CDN

内置 Office 365 内容传送网络（CDN）允许 Office 365 管理员为其组织的 SharePoint Online 页面提供更好的性能，具体方法是缓存静态资产，使其更接近请求的浏览器，这有助于加快下载并降低延迟。 Office 365 CDN 使用[HTTP/2 协议](https://en.wikipedia.org/wiki/HTTP/2)改进了压缩和下载速度。

> [!NOTE]
> Office 365 CDN 仅适用于**生产**（全球）云中的租户。 美国政府、中国和德国云中的租户目前不支持 Office 365 CDN。

Office 365 CDN 由多个 CDN 组成，用户可以在多个位置（即_源_）托管静态资产，并从全局高速网络提供这些资产。 可以添加**公共**源、**私有**源或同时添加这两种源，具体取决于想要托管在 Office 365 CDN 中的内容种类。

![Office 365 CDN 概念图](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 概念图")

Office 365 内的**公共**源中的内容可供匿名访问，并且任何具有托管资产 URL 的人员均可访问它。 由于对公共源中内容的访问属于匿名访问，因此只能使用它们缓存非敏感的常规内容，如 javascript 文件、脚本、图标和图片。 默认情况下，使用 Office 365 CDN 下载常规资源资产（如公共源中的 Office 365 客户端应用程序）。

Office 365 CDN 内的**专用**来源提供对用户内容（如 SharePoint Online 文档库、网站和专有图像）的专用访问。 使用动态生成的令牌保护为私有源中内容的访问提供保护，以便只有有权访问原始文档库或存储位置的用户才能访问它。 Office 365 CDN 中的私有源只能用于 SharePoint Online 内容，并且用户只能通过 SharePoint Online 租户重定向访问资产。

Office 365 CDN 服务被归入 SharePoint Online 订阅。

有关如何使用 Office 365 CDN 的详细信息，请参阅[将 office 365 内容传送网络与 SharePoint Online 结合使用](https://docs.microsoft.com/office365/enterprise/use-office-365-cdn-with-spo)。

若要观看一系列简短视频，以提供有关使用 Office 365 CDN 的概念性和 HOWTO 信息，请访问[SharePoint 开发人员模式和实践 YouTube 频道](https://aka.ms/sppnp-videos)。

## <a name="other-microsoft-cdns"></a>其他 Microsoft Cdn

尽管不是 Office 365 CDN 的一部分，但您可以在 Office 365 租户中使用这些 Cdn 来访问 SharePoint 开发库、自定义代码和其他在 Office 365 CDN 范围之外的用途。

### <a name="azure-cdn"></a>Azure CDN

您可以使用**AZURE cdn**来部署自己的 cdn 实例，以托管自定义 web 部件、库和其他资源资产，从而使您可以对 cdn 存储应用访问密钥，并对 cdn 配置进行更好的控制。 Azure CDN 的使用不是免费的，需要 Azure 订阅。

有关如何配置 Azure CDN 实例的详细信息，请参阅[快速入门：将 azure 存储帐户与 AZURE Cdn 集成](https://docs.microsoft.com/azure/cdn/cdn-create-a-storage-account-with-cdn)。

有关如何将 Azure CDN 用于承载 SharePoint web 部件的示例，请参阅[将 SharePoint 客户端 web 部件部署到 AZURE CDN](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn)。

有关 Azure CDN PowerShell 模块的详细信息，请参阅[使用 PowerShell 管理 AZURE CDN](https://docs.microsoft.com/azure/cdn/cdn-manage-powershell)。

### <a name="microsoft-ajax-cdn"></a>Microsoft Ajax CDN

Microsoft 的**AJAX cdn**是一个只读的 cdn，可提供多种流行的开发库，其中包括 jQuery （及其所有其他库）、ASP.NET Ajax、引导、挖空以及其他。
  
若要将这些脚本包含在项目中，只需将对这些公开的可用库的任何引用替换为对 CDN 地址的引用，而不是将其包含在项目本身中。 例如，使用以下代码链接到 jQuery：

``` html
<script src=https://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

有关如何使用 Microsoft Ajax CDN 的详细信息，请参阅[Microsoft AJAX cdn](https://docs.microsoft.com/aspnet/ajax/cdn/overview)。

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Office 365 如何使用 CDN 中的内容？

无论您为 Office 365 租户配置了什么 CDN，基本数据检索过程都是相同的。

1. 您的客户端（浏览器或 Office 客户端应用程序）从 Office 365 请求数据。

2. Office 365 或者将数据直接返回到客户端，如果数据是由 CDN 托管的一组内容中的一部分，则将客户端重定向到 CDN URL。

    a. 如果数据已缓存在_公用_源中，客户端将直接从最近的 CDN 位置将数据下载到客户端。

    b. 如果数据已缓存在_专用_源中，则 CDN 服务将检查您的 Office 365 用户帐户对源的权限。 如果您拥有权限，SharePoint Online 将动态生成由 CDN 和两个访问令牌中的资产路径组成的自定义 URL，并将自定义 URL 返回给客户端。 然后，您的客户端使用自定义 URL 直接将数据从最近的 CDN 位置下载到客户端。

3. 如果数据未在 CDN 上缓存，则 CDN 节点从 Office 365 请求数据，然后在客户端下载数据后将数据缓存一段时间。

CDN 将最接近的数据中心输出到用户的浏览器，使用重定向，从那里下载请求的数据。 CDN 重定向是快速的，可节省用户大量下载时间。

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>我应该如何设置我的网络，以便 Cdn 最适合使用 Office 365？

在网络上的客户端和 CDN 终结点之间最大限度地减少延迟是确保最佳性能的主要注意事项。 您可以使用[管理 Office 365 终结点](managing-office-365-endpoints.md)中概述的最佳做法，以确保您的网络配置允许客户端浏览器直接访问 cdn，而不是通过中央代理路由 cdn 通信以避免引入不必要的延迟。

您还可以阅读[office 365 网络连接原则](https://aka.ms/o365networkingprinciples)，了解优化 Office 365 网络性能背后的概念。

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>是否有 Office 365 使用的所有 Cdn 的列表？

Office 365 中使用的 Cdn 始终可能会发生更改，在许多情况下，事件1中配置了多个 CDN 伙伴不可用。 Office 365 使用的主 Cdn 为：

|CDN  |Company  |用法  |链接  |
|---------|---------|---------|---------|
|Office 365 CDN     |Akamai         |公用源中的常规资产，私人来源中的 SharePoint 用户内容         |[结合使用 Office 365 内容传送网络和 SharePoint Online](https://docs.microsoft.com/office365/enterprise/use-office-365-cdn-with-spo)         |
|Azure CDN     |Microsoft         |自定义代码、SharePoint 框架解决方案         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Microsoft Ajax CDN （只读）     |Microsoft         |适用于 Ajax、jQuery、ASP.NET、引导和挖空等的通用库。         |[Microsoft Ajax CDN](https://docs.microsoft.com/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>CDN 提供了哪些性能提升？

在从从 Office 365 直接下载的数据与从特定 CDN 下载的数据（如相对于租户的位置和最近的 CDN 终结点的位置）之间测量性能的具体差异时，会涉及许多因素，由 CDN 提供服务的页面上的资产以及网络延迟和带宽的瞬间更改。 但是，简单的 A/B 测试可以帮助显示特定文件的下载时间的差异。

下面的屏幕截图展示了 Office 365 中的本机文件位置与在[Microsoft Ajax 内容传递网络](https://docs.microsoft.com/aspnet/ajax/cdn/overview)上托管的相同文件之间的下载速度差异。 这些屏幕截图来自 Internet Explorer 11 开发人员工具中的 "**网络**" 选项卡。 这些屏幕截图显示热门库 jQuery 的延迟。 若要弹出此屏幕，请在 Internet Explorer 中，按**F12**键并选择 "**网络**" 选项卡，该选项卡 symbolized 带有 wi-fi 图标。
  
![F12 网络的屏幕截图](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
此屏幕截图显示了上载到 SharePoint Online 网站上的母版页样式库的库。 上载库所需的时间为1.51 秒。
  
![加载时间为 1.51 秒的屏幕截图](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
第二个屏幕截图显示了由 Microsoft 的 CDN 提供的相同文件。 这次延迟约为496毫秒。 这是一项较大的改进，并显示了整秒的 shaved，以下载该对象的总时间。
  
![加载时间为 469 毫秒的屏幕截图](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>我的数据是否安全？

我们非常重视保护企业运营的数据。 存储在 Office 365 CDN 中的数据在传输过程和静态数据中均进行加密，并且 Office 365 SharePoint CDN 中的数据访问受 Office 365 用户权限和令牌授权的保护。 必须从你的 Office 365 租户中引用（重定向） Office 365 SharePoint CDN 中的数据请求，否则将不会生成授权令牌。

为了确保您的数据保持安全，我们建议您不要将用户内容或其他敏感数据存储在公用 CDN 中。 由于对公用 CDN 中的数据的访问是匿名的，因此公共 Cdn 应仅用于承载 web 脚本文件、图标、图像和其他非敏感资产等通用内容。

> [!NOTE]
> 第三方 CDN 提供程序可能具有与 Office 365 信任中心所述的承诺不同的隐私和合规性标准。 通过 CDN 服务缓存的数据可能不符合 Microsoft 数据处理术语（DPT），并且可能位于 Office 365 信任中心合规性边界之外。

有关 Office 365 CDN 提供程序的隐私和数据保护的详细信息，请访问以下内容：  

- 了解有关 Office 365 隐私和数据保护的详细信息，请参阅[Microsoft 信任中心](https://www.microsoft.com/trustcenter)
- 了解有关 Akamai 的隐私和数据保护的详细信息[Akamai 隐私信任中心](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)
- 了解有关 azure[信任中心](https://azure.microsoft.com/overview/trusted-cloud/)的 azure 隐私和数据保护的详细信息

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>如何使用所有这些第三方服务保护我的网络？

利用广泛的合作伙伴服务集，Office 365 可以在使用 Office 365 时扩展和满足可用性要求，并增强用户体验。 第三方服务 Office 365 利用了证书吊销列表，它们包括：如 crl.microsoft.com 或 sa.symcb.com，以及 Cdn;例如 r3.res.outlook.com。 Office 365 生成的每个 CDN FQDN 都是 Office 365 的自定义 FQDN。 如果您是在 Office 365 请求时发送到 FQDN，则可以确保 CDN 提供程序控制该位置的 FQDN 和基础内容。
  
对于要将发往 Microsoft 或 Office 365 数据中心的请求与发往第三方的请求隔离的客户，我们编写了有关[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)的指南。

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>是否存在利用 Cdn 的所有 Fqdn 的列表？

Fqdn 列表以及它们如何利用 Cdn 在一段时间内的变化。 请参阅我们发布的[Office 365 url 和 IP 地址范围](https://go.microsoft.com/fwlink/p/?LinkID=293744)页面，获取最新使用 Cdn 的 fqdn 的日期。

您还可以使用[Office 365 IP 地址和 URL Web 服务](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)请求当前的 Office 365 url 和使用 CSV 或 JSON 格式的 IP 地址范围。

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>我可以在本地网络上使用我自己的 CDN 和缓存内容吗？

我们正在不断寻找新的方法来支持我们的客户需求，目前正在探索缓存代理解决方案和其他本地 CDN 解决方案的使用。

尽管它不是 Office 365 CDN 的一部分，但您也可以使用**AZURE cdn**来承载自定义 web 部件、库和其他资源资产，这样您就可以对 cdn 存储应用访问密钥，并对 cdn 配置进行更好的控制。 Azure CDN 的使用不是免费的，需要 Azure 订阅。 有关如何配置 Azure CDN 实例的详细信息，请参阅[快速入门：将 azure 存储帐户与 AZURE Cdn 集成](https://docs.microsoft.com/azure/cdn/cdn-create-a-storage-account-with-cdn)。

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>我使用的是适用于 Office 365 的 Azure ExpressRoute，是否会改变内容？

[适用于 office 365 的 Azure ExpressRoute](azure-expressroute.md)提供了与公共 internet 隔离的 office 365 基础结构的专用连接。 这意味着客户端仍需要通过非 ExpressRoute 连接进行连接，以连接到 Cdn，而不是显式包含在 ExpressRoute 支持的服务列表中的其他 Microsoft 基础结构。 有关如何路由特定流量（如发往 Cdn 的请求）的详细信息，请参阅[Office 365 网络流量管理](routing-with-expressroute.md)。

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>我可以将 Cdn 用于本地 SharePoint Server 吗？

使用 Cdn 仅在 SharePoint Online 上下文中有意义，应避免使用 SharePoint Server。 这是因为，如果服务器位于本地或地理位置，则与地理位置有关的所有优势都不成立。 此外，如果与托管的服务器之间存在网络连接，则可以在没有 Internet 连接的情况下使用网站，因此无法检索 CDN 文件。 否则，如果您的网站所需的库和文件有一个可用且稳定的功能，则应使用 CDN。
  
以下是可以用于返回的简短链接：[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>另请参阅

[Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)

[评估 Office 365 网络连接](assessing-network-connectivity.md)

[管理 Office 365 终结点](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints)

[Office 365 URL 和 IP 地址范围](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[结合使用 Office 365 内容传送网络和 SharePoint Online](https://docs.microsoft.com/office365/enterprise/use-office-365-cdn-with-spo)

[Microsoft 信任中心](https://www.microsoft.com/trustcenter)

[优化 Office 365 性能](tune-office-365-performance.md)
