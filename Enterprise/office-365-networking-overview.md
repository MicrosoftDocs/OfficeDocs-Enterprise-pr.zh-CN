---
title: Microsoft 365 网络连接概述
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: 讨论为什么网络优化对 SaaS 服务非常重要、Microsoft 365 网络的目标以及 SaaS 如何需要不同于其他工作负载的网络。
ms.openlocfilehash: 6dc1ea91607dc43d4e24546f938f4f7ee3af8b3a
ms.sourcegitcommit: 92bbb6d005d005952a9e2055661fcdccfdd0567b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2020
ms.locfileid: "46533497"
---
# <a name="microsoft-365-network-connectivity-overview"></a><span data-ttu-id="0f1a2-103">Microsoft 365 网络连接概述</span><span class="sxs-lookup"><span data-stu-id="0f1a2-103">Microsoft 365 network connectivity overview</span></span>

<span data-ttu-id="0f1a2-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="0f1a2-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="0f1a2-105">Microsoft 365 是分布式软件即服务（SaaS）云，它通过一组不同的微服务和应用程序提供工作效率和协作方案。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-105">Microsoft 365 is a distributed Software-as-a-Service (SaaS) cloud that provides productivity and collaboration scenarios through a diverse set of micro-services and applications.</span></span> <span data-ttu-id="0f1a2-106">Microsoft 365 中的客户端组件（如 Outlook、Word 和 PowerPoint）在用户计算机上运行，并连接到 microsoft 数据中心中运行的 Microsoft 365 的其他组件。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-106">Client components of Microsoft 365 such as Outlook, Word and PowerPoint run on user computers and connect to other components of Microsoft 365 that run in Microsoft datacenters.</span></span> <span data-ttu-id="0f1a2-107">确定 Microsoft 365 最终用户体验质量的最重要因素是网络可靠性和 Microsoft 365 客户端与 Microsoft 365 服务前盖之间的低延迟。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-107">The most significant factor that determines the quality of the Microsoft 365 end user experience is network reliability and low latency between Microsoft 365 clients and Microsoft 365 service front doors.</span></span>

<span data-ttu-id="0f1a2-108">在本文中，您将了解 Microsoft 365 网络的目标，以及为什么 Microsoft 365 网络需要不同的优化方法来优化常规 Internet 流量。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-108">In this article, you will learn about the goals of Microsoft 365 networking, and why Microsoft 365 networking requires a different approach to optimization than generic Internet traffic.</span></span>

## <a name="microsoft-365-networking-goals"></a><span data-ttu-id="0f1a2-109">Microsoft 365 网络目标</span><span class="sxs-lookup"><span data-stu-id="0f1a2-109">Microsoft 365 networking goals</span></span>

<span data-ttu-id="0f1a2-110">Microsoft 365 网络的最终目标是通过在客户端和最接近的 Microsoft 365 终结点之间启用限制性最少的访问来优化最终用户体验。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-110">The ultimate goal of Microsoft 365 networking is to optimize the end user experience by enabling the least restrictive access between clients and the closest Microsoft 365 endpoints.</span></span> <span data-ttu-id="0f1a2-111">最终用户体验的质量与用户正在使用的应用程序的性能和响应直接相关。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-111">The quality of end user experience is directly related to the performance and responsiveness of the application that the user is using.</span></span> <span data-ttu-id="0f1a2-112">例如，Microsoft 团队依赖低延迟，以便用户电话呼叫、会议和共享屏幕协作不会带来任何故障，而 Outlook 依靠强大的网络连接来实现即时搜索功能，从而利用服务器端索引和 AI 功能。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-112">For example, Microsoft Teams relies on low latency so that user phone calls, conferences and shared screen collaborations are glitch-free, and Outlook relies on great networking connectivity for instant search features that leverage server-side indexing and AI capabilities.</span></span>

<span data-ttu-id="0f1a2-113">网络设计中的主要目标是将客户端计算机中的往返时间（RTT）从客户端计算机减少到 Microsoft 全局网络，从而将所有 Microsoft 的数据中心互连在一起的 microsoft 公共网络主干中，以低延迟的方式分布所有 Microsoft 的数据中心，高可用性云应用程序入口点分布在世界各地。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-113">The primary goal in the network design should be to minimize latency by reducing the round-trip time (RTT) from client machines to the Microsoft Global Network, Microsoft's public network backbone that interconnects all of Microsoft's datacenters with low latency, high availability cloud application entry points spread around the world.</span></span> <span data-ttu-id="0f1a2-114">你可以在[Microsoft 如何构建其快速可靠的全局网络](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)中了解有关 Microsoft 全球网络的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-114">You can learn more about the Microsoft Global Network at [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).</span></span>

<span data-ttu-id="0f1a2-115">优化 Microsoft 365 网络性能不需要太复杂。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-115">Optimizing Microsoft 365 network performance doesn't need to be complicated.</span></span> <span data-ttu-id="0f1a2-116">您可以通过遵循以下几个关键原则获取最佳性能：</span><span class="sxs-lookup"><span data-stu-id="0f1a2-116">You can get the best possible performance by following a few key principles:</span></span>

- <span data-ttu-id="0f1a2-117">确定 Microsoft 365 网络流量</span><span class="sxs-lookup"><span data-stu-id="0f1a2-117">Identify Microsoft 365 network traffic</span></span>
- <span data-ttu-id="0f1a2-118">允许从用户连接到 Microsoft 365 的每个位置将 Microsoft 365 网络流量的本地分支出口到 internet</span><span class="sxs-lookup"><span data-stu-id="0f1a2-118">Allow local branch egress of Microsoft 365 network traffic to the internet from each location where users connect to Microsoft 365</span></span>
- <span data-ttu-id="0f1a2-119">允许 Microsoft 365 流量绕过代理和数据包检查设备</span><span class="sxs-lookup"><span data-stu-id="0f1a2-119">Allow Microsoft 365 traffic to bypass proxies and packet inspection devices</span></span>

<span data-ttu-id="0f1a2-120">有关 Microsoft 365 网络连接原则的详细信息，请参阅[microsoft 365 网络连接原则](office-365-network-connectivity-principles.md)。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-120">For more information on Microsoft 365 network connectivity principles, see [Microsoft 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="traditional-network-architectures-and-saas"></a><span data-ttu-id="0f1a2-121">传统网络体系结构和 SaaS</span><span class="sxs-lookup"><span data-stu-id="0f1a2-121">Traditional network architectures and SaaS</span></span>

<span data-ttu-id="0f1a2-122">传统的网络体系结构针对客户端/服务器工作负载的原则旨在假定客户端和终结点之间的通信不会延伸到公司网络外围之外。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-122">Traditional network architecture principles for client/server workloads are designed around the assumption that traffic between clients and endpoints does not extend outside the corporate network perimeter.</span></span> <span data-ttu-id="0f1a2-123">此外，在许多企业网络中，所有出站 Internet 连接都在企业网络中，并从中心位置外出。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-123">Also, in many enterprise networks, all outbound Internet connections traverse the corporate network, and egress from a central location.</span></span>

<span data-ttu-id="0f1a2-124">在传统网络体系结构中，一般 Internet 流量的较高延迟是维护网络外围安全所必需的，而 Internet 流量的性能优化通常涉及在网络传出点升级或扩展设备。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-124">In traditional network architectures, higher latency for generic Internet traffic is a necessary tradeoff in order to maintain network perimeter security, and performance optimization for Internet traffic typically involves upgrading or scaling out the equipment at network egress points.</span></span> <span data-ttu-id="0f1a2-125">但是，此方法并不能满足 Microsoft 365 等 SaaS 服务的最佳网络性能要求。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-125">However, this approach does not address the requirements for optimum network performance of SaaS services such as Microsoft 365.</span></span>

## <a name="identifying-microsoft-365-network-traffic"></a><span data-ttu-id="0f1a2-126">识别 Microsoft 365 网络流量</span><span class="sxs-lookup"><span data-stu-id="0f1a2-126">Identifying Microsoft 365 network traffic</span></span>

<span data-ttu-id="0f1a2-127">我们正在让您更轻松地识别 Microsoft 365 网络流量，并简化管理网络标识的过程。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-127">We're making it easier to identify Microsoft 365 network traffic and making it simpler to manage the network identification.</span></span>

- <span data-ttu-id="0f1a2-128">新类别的网络终结点，用于将高度关键的网络流量与不受 Internet 延迟影响的网络流量区分开来。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-128">New categories of network endpoints to differentiate highly critical network traffic from network traffic which is not impacted by Internet latencies.</span></span> <span data-ttu-id="0f1a2-129">在最关键的 "优化" 类别中，只提供了少量 Url 和支持 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-129">There are just a handful of URLs and supporting IP Addresses in the most critical “Optimize” category.</span></span>
- <span data-ttu-id="0f1a2-130">用于脚本使用情况的 Web 服务或 Microsoft 365 网络标识的直接设备配置和更改管理。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-130">Web services for script usage or direct device configuration and change management of Microsoft 365 network identification.</span></span> <span data-ttu-id="0f1a2-131">可以通过 web 服务或 RSS 格式，或使用 Microsoft Flow 模板在电子邮件上获取更改。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-131">Changes are available from the web service, or in RSS format, or on email using a Microsoft Flow template.</span></span>
- <span data-ttu-id="0f1a2-132">Microsoft 合作伙伴提供的[Office 365 网络合作伙伴计划](https://aka.ms/Office365NPP)，这些合作伙伴提供遵循 Microsoft 365 网络连接原则且具有简单配置的设备或服务。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-132">[Office 365 Network partner program](https://aka.ms/Office365NPP) with Microsoft partners who provide devices or services that follow Microsoft 365 network connectivity principles and have simple configuration.</span></span>

## <a name="securing-microsoft-365-connections"></a><span data-ttu-id="0f1a2-133">确保 Microsoft 365 连接的安全</span><span class="sxs-lookup"><span data-stu-id="0f1a2-133">Securing Microsoft 365 connections</span></span>

<span data-ttu-id="0f1a2-134">传统网络安全的目标是强化公司网络外围，以防受到入侵和恶意攻击。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-134">The goal of traditional network security is to harden the corporate network perimeter against intrusion and malicious exploits.</span></span> <span data-ttu-id="0f1a2-135">大多数企业网络使用代理服务器、防火墙、SSL 中断和检查、深度数据包检查和数据丢失防护系统等技术强制 Internet 流量的网络安全。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-135">Most enterprise networks enforce network security for Internet traffic using technologies like proxy servers, firewalls, SSL break and inspect, deep packet inspection, and data loss prevention systems.</span></span> <span data-ttu-id="0f1a2-136">这些技术为常规 Internet 请求提供了重要风险缓解，但在应用于 Microsoft 365 终结点时，可以显著降低性能、可伸缩性和最终用户体验的质量。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-136">These technologies provide important risk mitigation for generic Internet requests but can dramatically reduce performance, scalability, and the quality of end user experience when applied to Microsoft 365 endpoints.</span></span>

<span data-ttu-id="0f1a2-137">Microsoft 365 通过专门为 Microsoft 365 功能和工作负载设计的内置安全和治理功能，帮助满足您组织的内容安全性和数据使用合规性的需求。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-137">Microsoft 365 helps meet your organization's needs for content security and data usage compliance with built-in security and governance features designed specifically for Microsoft 365 features and workloads.</span></span> <span data-ttu-id="0f1a2-138">有关 Microsoft 365 安全性和合规性的详细信息，请参阅[Office 365 安全指南](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-138">For more information about Microsoft 365 security and compliance, see the [Office 365 security roadmap](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).</span></span> <span data-ttu-id="0f1a2-139">有关在 Microsoft 365 流量上执行高级处理的高级网络解决方案的 Microsoft 建议和支持位置的详细信息，请参阅[在 Office 365 流量上使用第三方网络设备或解决方案](https://support.microsoft.com/help/2690045)。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-139">For more information about Microsoft’s recommendations and support position on advanced network solutions that perform advanced-level processing on Microsoft 365 traffic, see [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/help/2690045).</span></span>

## <a name="why-is-microsoft-365-networking-different"></a><span data-ttu-id="0f1a2-140">为什么 Microsoft 365 网络是不同的？</span><span class="sxs-lookup"><span data-stu-id="0f1a2-140">Why is Microsoft 365 networking different?</span></span>

<span data-ttu-id="0f1a2-141">Microsoft 365 设计为使用端点安全性和加密网络连接实现最佳性能，从而减少了对外围安全强制实施的需求。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-141">Microsoft 365 is designed for optimal performance using endpoint security and encrypted network connections, reducing the need for perimeter security enforcement.</span></span> <span data-ttu-id="0f1a2-142">Microsoft 365 数据中心位于世界各地，服务旨在使用各种方法将客户端连接到最佳可用服务终结点。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-142">Microsoft 365 datacenters are located across the world and the service is designed to use various methods for connecting clients to best available service endpoints.</span></span> <span data-ttu-id="0f1a2-143">由于用户数据和处理分布在许多 Microsoft 数据中心之间，因此客户端计算机可以连接到的单个网络终结点。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-143">Since user data and processing is distributed between many Microsoft datacenters, there is no single network endpoint to which client machines can connect.</span></span> <span data-ttu-id="0f1a2-144">实际上，microsoft 365 租户中的数据和服务由 Microsoft 全球网络进行动态优化，以适应最终用户访问它们的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-144">In fact, data and services in your Microsoft 365 tenant are dynamically optimized by the Microsoft Global Network to adapt to the geographic locations from which they are accessed by end users.</span></span>

<span data-ttu-id="0f1a2-145">当 Microsoft 365 流量受到数据包检查和集中出站的制约时，将会创建某些常见的性能问题：</span><span class="sxs-lookup"><span data-stu-id="0f1a2-145">Certain common performance issues are created when Microsoft 365 traffic is subject to packet inspection and centralized egress:</span></span>

- <span data-ttu-id="0f1a2-146">高延迟可能会导致视频和音频流性能极差，以及数据检索、搜索、实时协作、日历忙/闲信息、产品内容和其他服务的响应速度较慢</span><span class="sxs-lookup"><span data-stu-id="0f1a2-146">High latency can cause extremely poor performance of video and audio streams, and slow response of data retrieval, searches, real-time collaboration, calendar free/busy information, in-product content and other services</span></span>
- <span data-ttu-id="0f1a2-147">来自中心位置的附近连接破坏了 Microsoft 365 全局网络的动态路由功能，从而增加了延迟和往返时间</span><span class="sxs-lookup"><span data-stu-id="0f1a2-147">Egressing connections from a central location defeats the dynamic routing capabilities of the Microsoft 365 global network, adding latency and round-trip time</span></span>
- <span data-ttu-id="0f1a2-148">解密受 SSL 保护的 Microsoft 365 网络流量并对其进行重新加密可能会导致协议错误并具有安全风险</span><span class="sxs-lookup"><span data-stu-id="0f1a2-148">Decrypting SSL secured Microsoft 365 network traffic and re-encrypting it can cause protocol errors and has security risk</span></span>

<span data-ttu-id="0f1a2-149">通过允许客户端流量尽可能接近其地理位置来缩短到 Microsoft 365 入口点的网络路径，可以提高连接性能和 Microsoft 365 中的最终用户体验。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-149">Shortening the network path to Microsoft 365 entry points by allowing client traffic to egress as close as possible to their geographic location can improve connectivity performance and the end user experience in Microsoft 365.</span></span> <span data-ttu-id="0f1a2-150">它还可以帮助降低对 Microsoft 365 性能和可靠性的网络体系结构的未来更改的影响。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-150">It can also help to reduce the impact of future changes to the network architecture on Microsoft 365 performance and reliability.</span></span> <span data-ttu-id="0f1a2-151">最佳连接模型是始终提供用户位置的网络出口，无论是在公司网络上还是在远程位置（例如，家庭、旅馆、咖啡店和机场）。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-151">The optimum connectivity model is to always provide network egress at the user's location, regardless of whether this is on the corporate network or remote locations such as home, hotels, coffee shops and airports.</span></span> <span data-ttu-id="0f1a2-152">一般 Internet 流量和基于 WAN 的企业网络流量将单独路由，而不使用本地直接传出模型。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-152">Generic Internet traffic and WAN based corporate network traffic would be separately routed and not use the local direct egress model.</span></span> <span data-ttu-id="0f1a2-153">此本地直接出口模型在下图中表示。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-153">This local direct egress model is represented in the diagram below.</span></span>

![本地出口网络体系结构](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

<span data-ttu-id="0f1a2-155">本地出口体系结构对传统机型上的 Microsoft 365 网络通信有以下好处：</span><span class="sxs-lookup"><span data-stu-id="0f1a2-155">The local egress architecture has the following benefits for Microsoft 365 network traffic over the traditional model:</span></span>
  
- <span data-ttu-id="0f1a2-156">通过优化路由长度提供最佳的 Microsoft 365 性能。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-156">Provides optimal Microsoft 365 performance by optimizing route length.</span></span> <span data-ttu-id="0f1a2-157">最终用户连接通过 Microsoft 全球网络的_分布式服务前端_基础结构动态路由到最近的 microsoft 365 入口点，然后将流量内部路由到 microsoft 的超高延迟高可用性纤程上的数据和服务终结点。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-157">End user connections are dynamically routed to the nearest Microsoft 365 entry point by the Microsoft Global Network's _Distributed Service Front Door_ infrastructure, and traffic is then routed internally to data and service endpoints over Microsoft's ultra-low latency high availability fiber.</span></span>
- <span data-ttu-id="0f1a2-158">通过允许 Microsoft 365 流量的本地出口，绕过代理和流量检查设备，减少公司网络基础结构的负载。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-158">Reduces the load on corporate network infrastructure by allowing local egress for Microsoft 365 traffic, bypassing proxies and traffic inspection devices.</span></span>
- <span data-ttu-id="0f1a2-159">通过利用客户端终结点安全性和云安全功能来保护两端的连接，从而避免应用冗余网络安全技术。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-159">Secures connections on both ends by leveraging client endpoint security and cloud security features, avoiding application of redundant network security technologies.</span></span>

> [!NOTE]
> <span data-ttu-id="0f1a2-160">_分布式服务前端_基础结构是 Microsoft 全球网络的高度可用且可扩展的网络边缘（地理位置分散）。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-160">The _Distributed Service Front Door_ infrastructure is the Microsoft Global Network's highly available and scalable network edge with geographically distributed locations.</span></span> <span data-ttu-id="0f1a2-161">它会终止最终用户连接，并在 Microsoft 全局网络中有效地路由它们。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-161">It terminates end user connections and efficiently routes them within the Microsoft Global Network.</span></span> <span data-ttu-id="0f1a2-162">你可以在[Microsoft 如何构建其快速可靠的全局网络](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)中了解有关 Microsoft 全球网络的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-162">You can learn more about the Microsoft Global Network at [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).</span></span>

<span data-ttu-id="0f1a2-163">有关了解和应用 Microsoft 365 网络连接原则的详细信息，请参阅[microsoft 365 网络连接原则](office-365-network-connectivity-principles.md)。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-163">For more information on understanding and applying Microsoft 365 network connectivity principles, see [Microsoft 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="conclusion"></a><span data-ttu-id="0f1a2-164">总结</span><span class="sxs-lookup"><span data-stu-id="0f1a2-164">Conclusion</span></span>

<span data-ttu-id="0f1a2-165">优化 Microsoft 365 网络性能实际上是为了消除不必要的障碍。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-165">Optimizing Microsoft 365 network performance really comes down to removing unnecessary impediments.</span></span> <span data-ttu-id="0f1a2-166">通过将 Microsoft 365 连接视为受信任的流量，可以防止数据包检查和针对代理带宽的竞争引入延迟。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-166">By treating Microsoft 365 connections as trusted traffic, you can prevent latency from being introduced by packet inspection and competition for proxy bandwidth.</span></span> <span data-ttu-id="0f1a2-167">如果允许客户端计算机和 Office 365 终结点之间的本地连接，则可以通过 Microsoft 全局网络动态路由通信。</span><span class="sxs-lookup"><span data-stu-id="0f1a2-167">Allowing local connections between client machines and Office 365 endpoints enables traffic to be dynamically routed through the Microsoft Global Network.</span></span>

## <a name="related-topics"></a><span data-ttu-id="0f1a2-168">相关主题</span><span class="sxs-lookup"><span data-stu-id="0f1a2-168">Related Topics</span></span>

[<span data-ttu-id="0f1a2-169">Microsoft 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="0f1a2-169">Microsoft 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="0f1a2-170">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="0f1a2-170">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="0f1a2-171">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="0f1a2-171">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="0f1a2-172">Office 365 IP 地址和 URL Web 服务</span><span class="sxs-lookup"><span data-stu-id="0f1a2-172">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="0f1a2-173">评估 Microsoft 365 网络连接</span><span class="sxs-lookup"><span data-stu-id="0f1a2-173">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)

[<span data-ttu-id="0f1a2-174">Microsoft 365 网络计划和性能优化</span><span class="sxs-lookup"><span data-stu-id="0f1a2-174">Network planning and performance tuning for Microsoft 365</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="0f1a2-175">使用基线和性能历史记录优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="0f1a2-175">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="0f1a2-176">Office 365 性能疑难解答计划</span><span class="sxs-lookup"><span data-stu-id="0f1a2-176">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="0f1a2-177">内容分发网络</span><span class="sxs-lookup"><span data-stu-id="0f1a2-177">Content Delivery Networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="0f1a2-178">Microsoft 365 连接测试</span><span class="sxs-lookup"><span data-stu-id="0f1a2-178">Microsoft 365 connectivity test</span></span>](https://aka.ms/netonboard)

[<span data-ttu-id="0f1a2-179">Microsoft 如何构建其快速可靠的全局网络</span><span class="sxs-lookup"><span data-stu-id="0f1a2-179">How Microsoft builds its fast and reliable global network</span></span>](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[<span data-ttu-id="0f1a2-180">Office 365 网络博客</span><span class="sxs-lookup"><span data-stu-id="0f1a2-180">Office 365 Networking blog</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
