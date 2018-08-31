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
# <a name="content-delivery-networks"></a><span data-ttu-id="7cf3c-105">内容传递网络</span><span class="sxs-lookup"><span data-stu-id="7cf3c-105">Content delivery networks</span></span>

<span data-ttu-id="7cf3c-p102">使用此信息来了解内容交付网络 (Cdn) 和 Office 365 利用它们。Cdn 有助于使 Office 365 快速且可靠保持为最终用户。Cdn，与 Office 365 云服务快速到用户的浏览器在他们正在使用该服务通过 web 客户端下载泛型内容，如图标。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p102">Use this information to learn about Content Delivery Networks (CDNs) and how Office 365 leverages them. CDNs help keep Office 365 fast and reliable for end users. With CDNs, cloud services like Office 365 quickly download generic content, like icons, to your users' browser when they're using the service through a web client.</span></span>
  
 <span data-ttu-id="7cf3c-109">**在 Head 回**[网络规划和性能优化 Office 365](https://aka.ms/tune)。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-109">**Head back to**[Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a><span data-ttu-id="7cf3c-110">如何应设置我的网络，以使 Cdn 最适合与 Office 365？</span><span class="sxs-lookup"><span data-stu-id="7cf3c-110">How should I set up my network so that CDNs work best with Office 365?</span></span>

<span data-ttu-id="7cf3c-p103">如果您计划[网络连接到 Office 365](network-connectivity.md)，则有助于您了解 Cdn 的工作方式。还有一点了解，您无法连接到 Cdn 筛选 IP 地址。我们为 Office 365，例如 Exchange Online 内的服务提供 Ip 最佳工作量的列表。了解有关[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)我们建议的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p103">If you're planning [Network connectivity to Office 365](network-connectivity.md), it's helpful to understand how CDNs work. It is also important to understand that you can't filter connectivity to the CDNs by IP address. We provide a best effort list of IPs for the services within Office 365, such as Exchange Online. Learn more about our recommendations for [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span></span>
  
## <a name="how-do-cdns-make-services-work-faster"></a><span data-ttu-id="7cf3c-115">CDN 如何使服务更快地工作？</span><span class="sxs-lookup"><span data-stu-id="7cf3c-115">How do CDNs make services work faster?</span></span>

<span data-ttu-id="7cf3c-p104">下载图标类似的常见任务可能占用可更好地用于下载重要的个人内容，如电子邮件或文档的网络带宽。由于 Office 365 使用体系结构，包括 Cdn、 图标、 脚本和其他泛型内容可以从服务器接近下载到客户端计算机，更快地进行下载。这意味着更快地访问您个人的内容，安全地存储在 Office 365 数据中心。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p104">Downloading common things like icons over and over again can take up network bandwidth that can be better used for downloading important personal content, like email or documents. Because Office 365 uses an architecture that includes CDNs, the icons, scripts, and other generic content can be downloaded from servers closer to client computers, making the downloads faster. This means faster access to your personal content, which is securely stored in Office 365 datacenters.</span></span>
  
## <a name="what-exactly-is-a-cdn"></a><span data-ttu-id="7cf3c-119">CDN 到底是什么？</span><span class="sxs-lookup"><span data-stu-id="7cf3c-119">What exactly is a CDN?</span></span>

<span data-ttu-id="7cf3c-p105">Cdn 使用大多数企业云服务。Office 365 云服务具有数百万客户一次下载专有内容 （如电子邮件） 和通用内容 （如图标） 的组合。它是每个人使用，如图标的图像放置接近尽可能的用户的计算机，更有效。尚未，此文件不适用于每个云服务来构建存储此泛型内容，在每个都市的区域，或即使在世界各地，每个主要 Internet 集线器以便这些 Cdn 的一些共享的 CDN 数据中心。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p105">CDNs are used by most enterprise cloud services. Cloud services like Office 365 have millions of customers downloading a mix of proprietary content (such as emails) and generic content (such as icons) at one time. It's more efficient to put images everyone uses, like icons, as close to the user's computer as possible. Yet, it isn't practical for every cloud service to build CDN datacenters that store this generic content in every metropolitan area, or even in every major Internet hub around the world, so some of these CDNs are shared.</span></span>
  
<span data-ttu-id="7cf3c-p106">Cdn 可以私有或公有。专用 Cdn 是拥有和运营的单个公司，并且只有该公司的应用程序和服务可以使用它。公共 Cdn 将运行由租赁对多个公司的使用情况的公司。根据您身在何处，它可能最适合您的 Office 365 下载泛型图像您从 Office 365 拥有的 CDN 和运行、 公共 CDN 或二者的组合。无论使用哪种类型的 CDN，则检索数据的步骤都相同。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p106">CDNs can be private or public. Private CDNs are owned and operated by a single company, and only that company's applications and services can use it. Public CDNs are run by companies who lease usage to multiple companies. Depending on where you're located, it might be most efficient for Office 365 to download generic images for you from a CDN that Office 365 owns and runs, a public CDN, or a combination of the two. Regardless of what type of CDN is used, the steps to retrieve the data are the same.</span></span>
  
1. <span data-ttu-id="7cf3c-129">您的客户端从 Office 365 请求数据。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-129">Your client requests data from Office 365.</span></span>

2. <span data-ttu-id="7cf3c-130">Office 365 直接向您的客户端返回数据，或将定向到 CDN 客户端。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-130">Office 365 either returns the data directly to your client or directs your client to a CDN.</span></span>

3. <span data-ttu-id="7cf3c-131">如果已在 CDN 缓存数据，则您的客户端下载数据直接从最接近的 CDN 位置到您在 internet 上的客户端。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-131">If the data is already cached at the CDN, your client downloads the data directly from the nearest CDN location to your client on the internet.</span></span>

4. <span data-ttu-id="7cf3c-132">如果数据不缓存在 CDN，CDN 节点从 Office 365 请求数据，然后缓存的一段时间后将您的客户端下载的数据的数据的方式。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-132">If the data isn't cached at the CDN, the CDN node requests the data from Office 365 and then cache's the data for a period of time after your client downloads the data.</span></span>

<span data-ttu-id="7cf3c-p107">Cdn 提取的文件和图像的最接近的 Office 365 数据中心和您的客户端反过来，最接近的 CDN 中提取了文件和图像。当用户访问云服务，如读取 Outlook Web App 中的电子邮件用户的浏览器将尝试从 Office 365 数据中心中检索文件和图像。而不是花费的时间和提供这些文件的带宽，Office 365 将浏览器重定向的 cdn。CDN 计算出到用户的浏览器的最接近数据中心，并使用重定向，从中下载泛型图像。使用此 CDN 重定向快速，并将用户保存大量下载时间。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p107">The CDNs pull the files and images from the nearest Office 365 datacenter and in turn, your client pulls the files and images from the nearest CDN. When users are accessing a cloud service, like reading email in Outlook Web App, the user's browser attempts to retrieve the files and images from the Office 365 datacenter. Instead of spending the time and bandwidth delivering the files, Office 365 redirects the browser to the CDN. The CDN figures out the closest datacenter to the user's browser and, using redirection, downloads the generic images from there. Using this CDN redirection is quick, and it saves users a lot of download time.</span></span>
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a><span data-ttu-id="7cf3c-138">是否存在的所有利用 Cdn 的 Fqdn 列表？</span><span class="sxs-lookup"><span data-stu-id="7cf3c-138">Is there a list of all the FQDNs that leverage CDNs?</span></span>

<span data-ttu-id="7cf3c-139">Fqdn 以及它们如何利用 Cdn 的不断变化的列表是指我们已发布的[Office 365 终结点页](https://go.microsoft.com/fwlink/p/?LinkID=293744)获取最新利用 Cdn 的最新 Fqdn。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-139">The list of FQDNs and how they leverage CDNs change over time, refer to our published [Office 365 endpoints page](https://go.microsoft.com/fwlink/p/?LinkID=293744) to get up to date on the latest FQDNs that leverage CDNs.</span></span>
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a><span data-ttu-id="7cf3c-140">是否存在的 Office 365 使用的所有 Cdn 列表？</span><span class="sxs-lookup"><span data-stu-id="7cf3c-140">Is there a list of all the CDNs that Office 365 uses?</span></span>

<span data-ttu-id="7cf3c-p108">使用 Office 365 Cdn 始终是恕和在许多情况下有多个 CDN 合作伙伴配置在事件之一是不可用。使用两个最常见 Cdn 是[Akamai](https://www.akamai.com/us/en/cdn.jsp)和[Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)。这两种 CDN 解决方案具有增强的多个角的世界服务访问的全球运营。存在存储的内容包括常规的 Office 365 脚本、 文件和图像。例如，当您登录到 portal.office.com，图像提取从最接近的 CDN 以加速调制页面加载时间。其他示例包括 Office 365 ProPlus 安装二进制文件存储在 CDN 以加速调制下载最新版本的 Office 所花的时间量。此外，还有一些专用存储的内容上 Cdn 如视频文件的 Office 365 视频。一旦您上载视频，文件加密，然后存储与 Azure Media Services 其加密格式。Office 365 视频播放器检索视频时它是第一次缓存到最接近的 CDN 之前下载以加速调制计以下载该视频的时间量。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p108">The CDNs in use by Office 365 are always subject to change and in many cases there are multiple CDN partners configured in the event one is unavailable. The two most common CDNs in use are [Akamai](https://www.akamai.com/us/en/cdn.jsp) and [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/). Both of these CDN solutions have a global reach enhancing the reach of the service to more corners of the world. The content that is stored there includes general Office 365 scripts, files, and images. For example, when you logon to portal.office.com, the images are pulled from the nearest CDN to speed up the page load times. Other examples include Office 365 ProPlus storing the installation bits on a CDN to speed up the amount of time it takes to download the latest version of Office. There is also some proprietary content that is stored on CDNs such as the video files for Office 365 Video. Once you upload the videos, the files are encrypted and then stored in their encrypted format with Azure Media Services. When the Office 365 video player retrieves the video it is first cached to the nearest CDN before being downloaded to speed up the amount of time it takes to download the video.</span></span>
  
## <a name="does-office-365-offer-a-cdn-that-i-can-use-for-my-own-files"></a><span data-ttu-id="7cf3c-150">Office 365 提供可为我自己的文件使用的 CDN 呢？</span><span class="sxs-lookup"><span data-stu-id="7cf3c-150">Does Office 365 offer a CDN that I can use for my own files?</span></span>

<span data-ttu-id="7cf3c-p109">是的！现在您的 Office 365 订阅包括独立于可以使用专门为您的 SharePoint Online 资产的 Azure 的 CDN。有关如何使用 Office 365 CDN 的信息，请参阅[使用 SharePoint Online 的 Office 365 内容交付网络](use-office-365-cdn-with-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p109">Yes! Your Office 365 subscription now includes a CDN that is separate from Azure that you can use specifically for your SharePoint Online assets. For information on how to use the Office 365 CDN, see [Use the Office 365 content delivery network with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  
## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a><span data-ttu-id="7cf3c-154">可以在我的本地网络上使用我自己 CDN 和缓存的内容？</span><span class="sxs-lookup"><span data-stu-id="7cf3c-154">Can I use my own CDN and cache content on my local network?</span></span>

<span data-ttu-id="7cf3c-155">我们不断正在寻找新方法，以支持客户的需要，在当前探索使用缓存代理解决方案和其他内部部署 CDN 解决方案。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-155">We're continually looking for new ways to support our customers needs and are currently exploring the use of caching proxy solutions and other on-premises CDN solutions.</span></span>
  
## <a name="is-my-data-safe"></a><span data-ttu-id="7cf3c-156">我的数据是否安全？</span><span class="sxs-lookup"><span data-stu-id="7cf3c-156">Is my data safe?</span></span>

<span data-ttu-id="7cf3c-p110">我们需要谨慎以帮助确保我们保护运行您的业务数据。存储在内容交付网络合作伙伴的项加密;例如，与[Office 365 视频](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e)或不客户特定;如 Office 365 ProPlus 的安装文件。通过[Office 365 信任中心](https://go.microsoft.com/fwlink/p/?LinkId=397383)以了解有关保护您的数据和您的隐私我们深入努力上标题。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p110">We take great care to help ensure that we protect the data that runs your business. The items stored at our content delivery network partners is either encrypted; such as with [Office 365 Video](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e), or not customer specific; such as the Office 365 ProPlus installation files. Head on over to the [Office 365 Trust Center](https://go.microsoft.com/fwlink/p/?LinkId=397383) to learn more about our in-depth efforts to protect your data and your privacy.</span></span>
  
## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a><span data-ttu-id="7cf3c-160">如何保护我的网络与所有这些第三方服务？</span><span class="sxs-lookup"><span data-stu-id="7cf3c-160">How can I secure my network with all these 3rd party services?</span></span>

<span data-ttu-id="7cf3c-p111">利用一组广泛的合作伙伴服务允许 Office 365 扩展和满足可用性要求，以及使用 Office 365 时增强用户体验。Office 365 利用第三方服务包括两个证书吊销列表;如 crl.microsoft.com 或 sa.symcb.com 和 Cdn;如 r3.res.outlook.com。每个 CDN FQDN Office 365 使用的自定义 Office 365 的 FQDN，如果您正在发送到 Office 365 的请求的 FQDN 您可以确信，我们控制 FQDN 和基础的内容在该位置。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p111">Leveraging an extensive set of partner services allows Office 365 to scale and meet availability requirements as well as enhance the user experience when using Office 365. The 3rd party services Office 365 leverages include both certificate revocation lists; such as crl.microsoft.com or sa.symcb.com, and CDNs; such as r3.res.outlook.com. Every CDN FQDN Office 365 uses is a custom FQDN for Office 365, if you're sent to a FQDN at the request of Office 365 you can be assured that we control the FQDN and the underlying content at that location.</span></span>
  
<span data-ttu-id="7cf3c-164">客户的仍要将请求发送到 Microsoft 或 Office 365 数据中心中，从第三方，发往请求数据库分隔到我们编写 up 指南上[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-164">For customers that still want to segregate requests destined for a Microsoft or Office 365 datacenter from requests that are destined for a 3rd party, we've written up guidance on [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span></span>
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a><span data-ttu-id="7cf3c-165">我使用的 Office 365 的 Azure ExpressRoute，不会更改操作？</span><span class="sxs-lookup"><span data-stu-id="7cf3c-165">I'm using Azure ExpressRoute for Office 365, does that change things?</span></span>

<span data-ttu-id="7cf3c-p112">[Office 365 的 azure ExpressRoute](azure-expressroute.md)从公共 internet 提供与隔离的 Office 365 基础结构的专用的连接。这意味着客户端将仍需要通过非 ExpressRoute 连接来连接到 Cdn 和其他 Microsoft 基础结构支持 ExpressRoute 的服务列表中未明确包括的连接。有关如何将如发往 Cdn 的请求的特定流量路由的详细信息，请参阅[Office 365 网络流量管理](routing-with-expressroute.md)。</span><span class="sxs-lookup"><span data-stu-id="7cf3c-p112">[Azure ExpressRoute for Office 365](azure-expressroute.md) provides a dedicated connection to Office 365 infrastructure that is segregated from the public internet. This means that clients will still need to connect over non-ExpressRoute connections to connect to CDNs and other Microsoft infrastructure that is not explicitly included in the list of services supported by ExpressRoute. For more information about how to route specific traffic such as requests destined for CDNs, refer to [Office 365 network traffic management](routing-with-expressroute.md).</span></span>
  
<span data-ttu-id="7cf3c-169">这是一个简短的链接，您可以使用回来：[https://aka.ms/o365cdns](https://aka.ms/o365cdns)</span><span class="sxs-lookup"><span data-stu-id="7cf3c-169">Here's a short link you can use to come back: [https://aka.ms/o365cdns](https://aka.ms/o365cdns)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7cf3c-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7cf3c-170">See also</span></span>

[<span data-ttu-id="7cf3c-171">Office 365 终结点常见问题</span><span class="sxs-lookup"><span data-stu-id="7cf3c-171">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
