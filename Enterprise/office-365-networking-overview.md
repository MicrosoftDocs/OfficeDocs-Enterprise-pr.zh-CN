---
title: Office 365 网络连接概述
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: 讨论网络优化为何重要 SaaS 服务，Office 365 网络的目标和如何 SaaS 需要从其他工作负荷的不同网络。
ms.openlocfilehash: ebd7410ec5fe421561543f1223e455377e99e625
ms.sourcegitcommit: 09985cb7894725289ef1fc8ddd90b569c285c09e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2018
ms.locfileid: "25002351"
---
# <a name="office-365-network-connectivity-overview"></a><span data-ttu-id="45a3c-103">Office 365 网络连接概述</span><span class="sxs-lookup"><span data-stu-id="45a3c-103">Office 365 network connectivity overview</span></span>

<span data-ttu-id="45a3c-p101">Office 365 提供通过多种多样微服务和应用程序的工作效率和协作方案分布式的软件作为-服务 (SaaS) 云。如 Outlook、 Word 和 PowerPoint 的 Office 365 的客户端组件在用户计算机上运行并连接到 Microsoft 数据中心中运行 Office 365 的其他组件。确定 Office 365 最终用户体验质量最重要的因素是网络可靠性和 Office 365 客户端和 Office 365 服务前盖之间的低延迟。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p101">Office 365 is a distributed Software-as-a-Service (SaaS) cloud that provides productivity and collaboration scenarios through a diverse set of micro-services and applications. Client components of Office 365 such as Outlook, Word and PowerPoint run on user computers and connect to other components of Office 365 that run in Microsoft datacenters. The most significant factor that determines the quality of the Office 365 end user experience is network reliability and low latency between Office 365 clients and Office 365 service front doors.</span></span>

<span data-ttu-id="45a3c-107">本文中，您将了解 Office 365 网络、 目标和 Office 365 网络为什么需要比一般 Internet 通信优化的不同方法。</span><span class="sxs-lookup"><span data-stu-id="45a3c-107">In this article, you will learn about the goals of Office 365 networking, and why Office 365 networking requires a different approach to optimization than generic Internet traffic.</span></span>

## <a name="office-365-networking-goals"></a><span data-ttu-id="45a3c-108">Office 365 网络目标</span><span class="sxs-lookup"><span data-stu-id="45a3c-108">Office 365 networking goals</span></span>

<span data-ttu-id="45a3c-p102">Office 365 网络的最终目标是最松散访问客户端之间的关系较好的 Office 365 终结点，从而优化的最终用户体验。最终用户体验质量直接与的性能和用户使用的应用程序的响应。例如，Microsoft 团队依赖低延迟，以便用户电话呼叫、 会议和共享的屏幕协作是小故障释放，并 Outlook 依赖利用服务器端索引和 AI 的即时搜索功能强大的网络连接能力功能。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p102">The ultimate goal of Office 365 networking is to optimize the end user experience by enabling the least restrictive access between clients and the closest Office 365 endpoints. The quality of end user experience is directly related to the performance and responsiveness of the application that the user is using. For example, Microsoft Teams relies on low latency so that user phone calls, conferences and shared screen collaborations are glitch-free, and Outlook relies on great networking connectivity for instant search features that leverage server-side indexing and AI capabilities.</span></span>

<span data-ttu-id="45a3c-p103">网络设计中的主要目标应以减少延迟通过减少的往返时间 (RTT) 从客户端计算机与 Microsoft 全局网络，Microsoft 的公用网络中枢的互连所有 Microsoft 数据中心的低延迟在世界各地分布的高可用性云应用程序入口点。您可以了解有关在[Microsoft 如何构建其快速且可靠的全局网络](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)的 Microsoft 全局网络的详细信息。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p103">The primary goal in the network design should be to minimize latency by reducing the round-trip time (RTT) from client machines to the Microsoft Global Network, Microsoft's public network backbone that interconnects all of Microsoft's datacenters with low latency, high availability cloud application entry points spread around the world. You can learn more about the Microsoft Global Network at [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).</span></span>

<span data-ttu-id="45a3c-p104">优化 Office 365 网络性能不需要很复杂。通过以下几项主要原则，可获得最佳性能：</span><span class="sxs-lookup"><span data-stu-id="45a3c-p104">Optimizing Office 365 network performance doesn't need to be complicated. You can get the best possible performance by following a few key principles:</span></span>

- <span data-ttu-id="45a3c-116">确定 Office 365 网络流量</span><span class="sxs-lookup"><span data-stu-id="45a3c-116">Identify Office 365 network traffic</span></span>
- <span data-ttu-id="45a3c-117">到 internet 的 Office 365 网络流量的本地分支出口允许从每个用户连接到 Office 365 的位置的位置</span><span class="sxs-lookup"><span data-stu-id="45a3c-117">Allow local branch egress of Office 365 network traffic to the internet from each location where users connect to Office 365</span></span>
- <span data-ttu-id="45a3c-118">允许 Office 365 流量以绕过代理服务器和数据包检查设备</span><span class="sxs-lookup"><span data-stu-id="45a3c-118">Allow Office 365 traffic to bypass proxies and packet inspection devices</span></span>

<span data-ttu-id="45a3c-119">Office 365 网络连接原则的详细信息，请参阅[Office 365 网络连接原则](office-365-network-connectivity-principles.md)。</span><span class="sxs-lookup"><span data-stu-id="45a3c-119">For more information on Office 365 network connectivity principles, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="traditional-network-architectures-and-saas"></a><span data-ttu-id="45a3c-120">传统网络体系结构和 SaaS</span><span class="sxs-lookup"><span data-stu-id="45a3c-120">Traditional network architectures and SaaS</span></span>

<span data-ttu-id="45a3c-p105">客户端/服务器工作负荷的传统网络体系结构原则设计周围客户端和终结点之间的通信不会扩展外部企业网络外围假设。此外，在很多企业网络中，所有出站的 Internet 连接遍历企业网络和出口从一个中心位置。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p105">Traditional network architecture principles for client/server workloads are designed around the assumption that traffic between clients and endpoints does not extend outside the corporate network perimeter. Also, in many enterprise networks, all outbound Internet connections traverse the corporate network, and egress from a central location.</span></span>

<span data-ttu-id="45a3c-p106">在传统网络体系结构，更高延迟的一般 Internet 通信是必要权衡为了维护网络外围安全和 Internet 通信的性能优化通常需要升级或向外扩展在网络出口点的设备。但是，此方法不能解决 SaaS 服务，例如 Office 365 的理想的网络性能的要求。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p106">In traditional network architectures, higher latency for generic Internet traffic is a necessary tradeoff in order to maintain network perimeter security, and performance optimization for Internet traffic typically involves upgrading or scaling out the equipment at network egress points. However, this approach does not address the requirements for optimum network performance of SaaS services such as Office 365.</span></span>

## <a name="identifying-office-365-network-traffic"></a><span data-ttu-id="45a3c-125">确定 Office 365 网络流量</span><span class="sxs-lookup"><span data-stu-id="45a3c-125">Identifying Office 365 network traffic</span></span>

<span data-ttu-id="45a3c-126">我们正在使其更轻松地识别 Office 365 网络通信，并使其更易于管理网络标识。</span><span class="sxs-lookup"><span data-stu-id="45a3c-126">We're making it easier to identify Office 365 network traffic and making it simpler to manage the network identification.</span></span>

- <span data-ttu-id="45a3c-p107">新类别的网络终结点的不受影响的 Internet 延迟网络流量从区分高度重要的网络通信。有刚才的几个 Url 和支持的最重要的"优化"类别中的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p107">New categories of network endpoints to differentiate highly critical network traffic from network traffic which is not impacted by Internet latencies. There are just a handful of URLs and supporting IP Addresses in the most critical “Optimize” category.</span></span>
- <span data-ttu-id="45a3c-p108">脚本使用情况或直接设备配置和更改管理的 Office 365 网络标识用于 web 服务。更改可从 web 服务，或以 RSS 格式，或使用 Microsoft 流模板的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p108">Web services for script usage or direct device configuration and change management of Office 365 network identification. Changes are available from the web service, or in RSS format, or on email using a Microsoft Flow template.</span></span>
- <span data-ttu-id="45a3c-131">[Office 365 网络合作伙伴计划](http://aka.ms/Office365NPP)与 Microsoft 合作伙伴提供设备或服务，请按照 Office 365 网络连接原则和具有简单的配置。</span><span class="sxs-lookup"><span data-stu-id="45a3c-131">[Office 365 Network partner program](http://aka.ms/Office365NPP) with Microsoft partners who provide devices or services that follow Office 365 network connectivity principles and have simple configuration.</span></span>

## <a name="securing-office-365-connections"></a><span data-ttu-id="45a3c-132">保护 Office 365 连接</span><span class="sxs-lookup"><span data-stu-id="45a3c-132">Securing Office 365 connections</span></span>

<span data-ttu-id="45a3c-p109">传统网络安全的目标是强化企业网络外围免受入侵和恶意攻击。大多数企业网络强制实施网络安全的 Internet 通信使用代理服务器、 防火墙、 SSL 中断的技术，并检查，深度数据包检查和数据丢失防护系统。这些技术提供的通用 Internet 请求的重要风险缓解时，但可以显著减少性能、 可伸缩性和应用到 Office 365 终结点时的最终用户体验质量。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p109">The goal of traditional network security is to harden the corporate network perimeter against intrusion and malicious exploits. Most enterprise networks enforce network security for Internet traffic using technologies like proxy servers, firewalls, SSL break and inspect, deep packet inspection, and data loss prevention systems. These technologies provide important risk mitigation for generic Internet requests but can dramatically reduce performance, scalability, and the quality of end user experience when applied to Office 365 endpoints.</span></span>

<span data-ttu-id="45a3c-p110">Office 365 帮助满足您组织需求的内容安全性和数据使用率遵守内置的安全和管理功能，专为 Office 365 功能和工作负荷设计。有关 Office 365 安全性和遵从性的详细信息，请参阅[Office 365 安全指南](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap)。有关 Microsoft 的建议以及支持位置对 Office 365 流量执行高级处理的高级的网络解决方案的详细信息，请参阅[使用第三方网络设备或在 Office 365 通信解决方案](https://support.microsoft.com/en-us/help/2690045)。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p110">Office 365 helps meet your organization's needs for content security and data usage compliance with built-in security and governance features designed specifically for Office 365 features and workloads. For more information about Office 365 security and compliance, see the [Office 365 security roadmap](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap). For more information about Microsoft’s recommendations and support position on advanced network solutions that perform advanced-level processing on Office 365 traffic, see [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045).</span></span>

## <a name="why-is-office-365-networking-different"></a><span data-ttu-id="45a3c-139">Office 365 网络连接不同</span><span class="sxs-lookup"><span data-stu-id="45a3c-139">Why is Office 365 networking different?</span></span>

<span data-ttu-id="45a3c-p111">Office 365 专为终结点的安全和加密的网络连接，可减少外围安全实施的最佳性能。Office 365 数据中心位于世界各地，该服务旨在用于客户端连接到最佳可用的服务终结点的各种方法。用户数据和处理许多 Microsoft 数据中心之间分布，因为机可以连接到哪些客户端没有单个网络终结点。实际上，数据和 Office 365 租户中的服务动态优化的 Microsoft 全局网络以适应从中被最终用户访问的地理位置。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p111">Office 365 is designed for optimal performance using endpoint security and encrypted network connections, reducing the need for perimeter security enforcement. Office 365 datacenters are located across the world and the service is designed to use various methods for connecting clients to best available service endpoints. Since user data and processing is distributed between many Microsoft datacenters, there is no single network endpoint to which client machines can connect. In fact, data and services in your Office 365 tenant are dynamically optimized by the Microsoft Global Network to adapt to the geographic locations from which they are accessed by end users.</span></span>

<span data-ttu-id="45a3c-144">Office 365 流量受制数据包检测和集中的外出时，将创建某些常见的性能问题：</span><span class="sxs-lookup"><span data-stu-id="45a3c-144">Certain common performance issues are created when Office 365 traffic is subject to packet inspection and centralized egress:</span></span>

- <span data-ttu-id="45a3c-145">高延迟可能导致极差的视频和音频流的性能和数据检索、 搜索、 实时协作、 日历忙/闲信息、 产品内内容和其他服务的响应速度慢</span><span class="sxs-lookup"><span data-stu-id="45a3c-145">High latency can cause extremely poor performance of video and audio streams, and slow response of data retrieval, searches, real-time collaboration, calendar free/busy information, in-product content and other services</span></span>
- <span data-ttu-id="45a3c-146">Egressing 从中心位置破坏了动态路由功能的 Office 365 全局网络连接，增加延迟和往返时间</span><span class="sxs-lookup"><span data-stu-id="45a3c-146">Egressing connections from a central location defeats the dynamic routing capabilities of the Office 365 global network, adding latency and round-trip time</span></span>
- <span data-ttu-id="45a3c-147">解密受 SSL 保护 Office 365 网络流量和重新加密会导致协议错误并且具有安全风险</span><span class="sxs-lookup"><span data-stu-id="45a3c-147">Decrypting SSL secured Office 365 network traffic and re-encrypting it can cause protocol errors and has security risk</span></span>

<span data-ttu-id="45a3c-p112">客户端通信及其地理位置尽可能近出口，从而缩短 Office 365 入口点的网络路径可以提高连接 Office 365 中的性能和最终用户体验。它还有助于降低到在 Office 365 性能和可靠性的网络体系结构的未来更改的影响。获得最佳 connectivity 模型是始终提供在用户的位置，而不考虑此位于企业网络或远程位置，如 home、 酒店或、 咖啡馆和机场网络出口。一般 Internet 通信和 WAN 基于企业网络流量将单独路由和不使用本地直接出口模型。下图中表示此本地直接出口模型。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p112">Shortening the network path to Office 365 entry points by allowing client traffic to egress as close as possible to their geographic location can improve connectivity performance and the end user experience in Office 365. It can also help to reduce the impact of future changes to the network architecture on Office 365 performance and reliability. The optimum connectivity model is to always provide network egress at the user's location, regardless of whether this is on the corporate network or remote locations such as home, hotels, coffee shops and airports. Generic Internet traffic and WAN based corporate network traffic would be separately routed and not use the local direct egress model. This local direct egress model is represented in the diagram below.</span></span>

![本地出口网络体系结构](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

<span data-ttu-id="45a3c-154">本地出口体系结构的优点如下的 Office 365 网络流量通过传统的模型：</span><span class="sxs-lookup"><span data-stu-id="45a3c-154">The local egress architecture has the following benefits for Office 365 network traffic over the traditional model:</span></span>
  
- <span data-ttu-id="45a3c-p113">通过 Office 365 的最佳性能优化路由长度。最终用户连接由 Microsoft 全球网络_分布式服务前盖_基础结构，动态路由到最接近的 Office 365 入口点，然后路由流量内部到数据和服务的终结点通过 Microsoft 的超低的延迟高可用性暗光纤。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p113">Provides optimal Office 365 performance by optimizing route length. End user connections are dynamically routed to the nearest Office 365 entry point by the Microsoft Global Network's _Distributed Service Front Door_ infrastructure, and traffic is then routed internally to data and service endpoints over Microsoft's ultra-low latency high availability dark fiber.</span></span>
- <span data-ttu-id="45a3c-157">对于 Office 365 流量，绕过代理服务器和流量检查设备的本地出口，从而减少了企业网络基础结构上的负载。</span><span class="sxs-lookup"><span data-stu-id="45a3c-157">Reduces the load on corporate network infrastructure by allowing local egress for Office 365 traffic, bypassing proxies and traffic inspection devices.</span></span>
- <span data-ttu-id="45a3c-158">利用客户端终结点安全和云安全功能，避免冗余网络安全技术的应用程序保护两端的连接。</span><span class="sxs-lookup"><span data-stu-id="45a3c-158">Secures connections on both ends by leveraging client endpoint security and cloud security features, avoiding application of redundant network security technologies.</span></span>

> [!NOTE]
> <span data-ttu-id="45a3c-p114">_分布式服务前盖_基础结构是具有地理上分散的位置的 Microsoft 全局网络的高可用性和可扩展性网络边缘。它终止最终用户的连接，并高效地将其路由 Microsoft 全球网络内。您可以了解有关在[Microsoft 如何构建其快速且可靠的全局网络](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)的 Microsoft 全局网络的详细信息。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p114">The _Distributed Service Front Door_ infrastructure is the Microsoft Global Network's highly available and scalable network edge with geographically distributed locations. It terminates end user connections and efficiently routes them within the Microsoft Global Network. You can learn more about the Microsoft Global Network at [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).</span></span>

<span data-ttu-id="45a3c-162">了解并应用 Office 365 网络连接原则的详细信息，请参阅[Office 365 网络连接原则](office-365-network-connectivity-principles#office-365-connectivity-principles)。</span><span class="sxs-lookup"><span data-stu-id="45a3c-162">For more information on understanding and applying Office 365 network connectivity principles, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles#office-365-connectivity-principles).</span></span>

## <a name="conclusion"></a><span data-ttu-id="45a3c-163">结束语</span><span class="sxs-lookup"><span data-stu-id="45a3c-163">Conclusion</span></span>

<span data-ttu-id="45a3c-p115">优化 Office 365 网络性能真正涉及删除不必要的障碍。通过将 Office 365 连接视为受信任流量，您可以防止数据包检测和代理带宽的竞争引入延迟。允许客户端计算机和 Office 365 终结点之间的本地连接启用动态路由通过 Microsoft 全局网络通信。</span><span class="sxs-lookup"><span data-stu-id="45a3c-p115">Optimizing Office 365 network performance really comes down to removing unnecessary impediments. By treating Office 365 connections as trusted traffic, you can prevent latency from being introduced by packet inspection and competition for proxy bandwidth. Allowing local connections between client machines and Office 365 endpoints enables traffic to be dynamically routed through the Microsoft Global Network.</span></span>

## <a name="related-topics"></a><span data-ttu-id="45a3c-167">相关主题</span><span class="sxs-lookup"><span data-stu-id="45a3c-167">Related Topics</span></span>

[<span data-ttu-id="45a3c-168">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="45a3c-168">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="45a3c-169">Office 365 IP 地址和 URL Web 服务</span><span class="sxs-lookup"><span data-stu-id="45a3c-169">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="45a3c-170">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="45a3c-170">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="45a3c-171">Office 365 IP 地址和 URL Web 服务</span><span class="sxs-lookup"><span data-stu-id="45a3c-171">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="45a3c-172">与 Office 365 的网络连接</span><span class="sxs-lookup"><span data-stu-id="45a3c-172">Network connectivity to Office 365</span></span>](network-connectivity.md)

[<span data-ttu-id="45a3c-173">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="45a3c-173">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="45a3c-174">使用基线和性能历史记录优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="45a3c-174">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="45a3c-175">Office 365 的性能疑难解答计划</span><span class="sxs-lookup"><span data-stu-id="45a3c-175">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="45a3c-176">Microsoft 如何构建其快速且可靠的全局网络</span><span class="sxs-lookup"><span data-stu-id="45a3c-176">How Microsoft builds its fast and reliable global network</span></span>](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
