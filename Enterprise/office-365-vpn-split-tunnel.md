---
title: 概述：Office 365 的 VPN 拆分隧道
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/3/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: 指导如何使用 Office 365 VPN 拆分隧道为远程用户优化 Office 365 连接。
ms.openlocfilehash: d8f8d4364804395cd10eceb1aa55422f01cbe079
ms.sourcegitcommit: 58aa8b2e89685490f849e0392d566b7bfb7b933e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547650"
---
# <a name="optimize-office-365-connectivity-for-remote-users-using-vpn-split-tunnelling"></a><span data-ttu-id="81074-103">使用 VPN 拆分隧道为远程用户优化 Office 365 连接</span><span class="sxs-lookup"><span data-stu-id="81074-103">Optimize Office 365 connectivity for remote users using VPN split tunnelling</span></span>
<!---
>[!NOTE]
>This topic is part of a set of topics that address Office 365 optimization for remote users.
>- For VPN split tunnel implementation guidance, see [Implementing VPN split tunnelling for Office 365](office-365-vpn-implement-split-tunnel.md).
>- For information about optimizing Office 365 worldwide tenant performance for users in China, see [Office 365 performance optimization for China users](office-365-networking-china.md).
-->

<span data-ttu-id="81074-104">对于通过 VPN 将远程工作设备与公司网络或云基础结构连接的客户，Microsoft 建议关键 Office 365 场景 **Microsoft Teams**、**SharePoint Online** 和 **Exchange Online** 通过 _VPN 拆分隧道_配置进行路由。</span><span class="sxs-lookup"><span data-stu-id="81074-104">For customers who connect their remote worker devices to the corporate network or cloud infrastructure over VPN, Microsoft recommends that the key Office 365 scenarios **Microsoft Teams**, **SharePoint Online** and **Exchange Online** are routed over a _VPN split tunnel_ configuration.</span></span> <span data-ttu-id="81074-105">作为在新型冠状病毒肺炎（COVID-19）危机等大规模在家办公事件中促使员工持续保证工作效率的一线战略，这一点尤其重要。</span><span class="sxs-lookup"><span data-stu-id="81074-105">This becomes especially important as the first line strategy to facilitate continued employee productivity during large scale work-from-home events such as the COVID-19 crisis.</span></span>

![拆分隧道 VPN 配置](media/vpn-split-tunnelling/vpn-model-2.png)

<span data-ttu-id="81074-107">_图 1：将定义的 Office 365 异常直接发送到服务的 VPN 拆分隧道解决方案。所有其他流量都将遍历 VPN 隧道，而不考虑目标。_</span><span class="sxs-lookup"><span data-stu-id="81074-107">_Figure 1: A VPN split tunnel solution with defined Office 365 exceptions sent directly to the service. All other traffic traverses the VPN tunnel regardless of destination._</span></span>

<span data-ttu-id="81074-108">这种方法的本质是，为企业提供一种简单的方法来降低 VPN 基础结构饱和的风险，并在尽可能短的时间内显著提高 Office 365 的性能。</span><span class="sxs-lookup"><span data-stu-id="81074-108">The essence of this approach is to provide a simple method for enterprises to mitigate the risk of VPN infrastructure saturation and dramatically improve Office 365 performance in the shortest timeframe possible.</span></span> <span data-ttu-id="81074-109">将 VPN 客户端配置为允许最关键、高容量 Office 365 流量绕过 VPN 隧道将获得以下好处：</span><span class="sxs-lookup"><span data-stu-id="81074-109">Configuring VPN clients to allow the most critical, high volume Office 365 traffic to bypass the VPN tunnel achieves the following benefits:</span></span>

- <span data-ttu-id="81074-110">立即缓解企业 VPN 体系结构中大多数客户报告的影响 Office 365 用户体验的性能和网络容量问题的根本原因</span><span class="sxs-lookup"><span data-stu-id="81074-110">Immediately mitigates the root cause of a majority of customer-reported performance and network capacity issues in enterprise VPN architectures impacting Office 365 user experience</span></span>
  
  <span data-ttu-id="81074-111">建议的解决方案专门针对 [Office 365 URL 和 IP 地址范围](https://aka.ms/o365ips)主题中分类为**优化**的 Office 365 服务终结点。</span><span class="sxs-lookup"><span data-stu-id="81074-111">The recommended solution specifically targets Office 365 service endpoints categorized as **Optimize** in the topic [Office 365 URLs and IP address ranges](https://aka.ms/o365ips).</span></span> <span data-ttu-id="81074-112">流向这些终结点的流量对延迟和带宽限制非常敏感，使其绕过 VPN 隧道可显著改善最终用户体验，并减少公司网络负载。</span><span class="sxs-lookup"><span data-stu-id="81074-112">Traffic to these endpoints is highly sensitive to latency and bandwidth throttling, and enabling it to bypass the VPN tunnel can dramatically improve the end user experience as well as reduce the corporate network load.</span></span> <span data-ttu-id="81074-113">不构成大部分带宽或用户体验足迹的 Office 365 连接可继续通过 VPN 隧道和 Internet 捆绑的其他流量进行路由。</span><span class="sxs-lookup"><span data-stu-id="81074-113">Office 365 connections that do not constitute the majority of bandwidth or user experience footprint can continue to be routed through the VPN tunnel along with the rest of the Internet-bound traffic.</span></span> <span data-ttu-id="81074-114">有关详细信息，请参阅 [VPN 拆分隧道策略](#the-vpn-split-tunnel-strategy)。</span><span class="sxs-lookup"><span data-stu-id="81074-114">For more information, see [The VPN split tunnel strategy](#the-vpn-split-tunnel-strategy).</span></span>

- <span data-ttu-id="81074-115">可由客户快速配置、测试和实施，无需其他基础结构或应用程序要求</span><span class="sxs-lookup"><span data-stu-id="81074-115">Can be configured, tested and implemented rapidly by customers and with no additional infrastructure or application requirements</span></span>

  <span data-ttu-id="81074-116">根据 VPN 平台和网络体系结构，实现可能只需几个小时。</span><span class="sxs-lookup"><span data-stu-id="81074-116">Depending on the VPN platform and network architecture, implementation can take as little as a few hours.</span></span> <span data-ttu-id="81074-117">有关详细信息，请参阅[实现 VPN 拆分隧道](office-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunnelling)。</span><span class="sxs-lookup"><span data-stu-id="81074-117">For more information, see [Implement VPN split tunnelling](office-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunnelling).</span></span>

- <span data-ttu-id="81074-118">通过不更改其他连接的路由方式（包括到 Internet 的流量）来保留客户 VPN 实现的安全状况</span><span class="sxs-lookup"><span data-stu-id="81074-118">Preserves the security posture of customer VPN implementations by not changing how other connections are routed, including traffic to the Internet</span></span>

  <span data-ttu-id="81074-119">建议的配置遵循 VPN 流量异常的**最低特权**原则，并允许客户实现拆分隧道 VPN，而不会将用户或基础结构暴露于额外的安全风险中。</span><span class="sxs-lookup"><span data-stu-id="81074-119">The recommended configuration follows the **least privilege** principle for VPN traffic exceptions and allows customers to implement split tunnel VPN without exposing users or infrastructure to additional security risks.</span></span> <span data-ttu-id="81074-120">直接路由到 Office 365 终结点的网络流量会进行加密，由 Office 客户端应用程序堆栈验证其完整性，且范围限定为专用于 Office 365 服务的 IP 地址，这些地址在应用程序和网络级别都进行了强化。</span><span class="sxs-lookup"><span data-stu-id="81074-120">Network traffic routed directly to Office 365 endpoints is encrypted, validated for integrity by Office client application stacks and scoped to IP addresses dedicated to Office 365 services which are hardened at both the application and network level.</span></span> <span data-ttu-id="81074-121">有关详细信息，请参阅[安全专业人员和 IT 人员在当前独特的远程工作场景中实现新式安全控制的替代方法（Microsoft 安全团队博客）](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)。</span><span class="sxs-lookup"><span data-stu-id="81074-121">For more information, see [Alternative ways for security professionals and IT to achieve modern security controls in today's unique remote work scenarios (Microsoft Security Team blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).</span></span>

- <span data-ttu-id="81074-122">由大多数企业 VPN 平台在本地提供支持</span><span class="sxs-lookup"><span data-stu-id="81074-122">Is natively supported by most enterprise VPN platforms</span></span>

  <span data-ttu-id="81074-123">Microsoft 与制作商业版 VPN 解决方案的行业合作伙伴持续协作，帮助合作伙伴开发与以上建议一致的解决方案的目标指南和配置模板。</span><span class="sxs-lookup"><span data-stu-id="81074-123">Microsoft continues to collaborate with industry partners producing commercial VPN solutions to help partners develop targeted guidance and configuration templates for their solutions in alignment with the above recommendations.</span></span> <span data-ttu-id="81074-124">有关详细信息，请参阅[适用于常见 VPN 平台的操作指南](office-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms)。</span><span class="sxs-lookup"><span data-stu-id="81074-124">For more information, see [HOWTO guides for common VPN platforms](office-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).</span></span>

>[!TIP]
><span data-ttu-id="81074-125">Microsoft 建议重点关注 Office 365 服务记录的专用 IP 范围上的拆分隧道 VPN 配置。</span><span class="sxs-lookup"><span data-stu-id="81074-125">Microsoft recommends focusing split tunnel VPN configuration on documented dedicated IP ranges for Office 365 services.</span></span> <span data-ttu-id="81074-126">虽然 FQDN 或基于 AppID 的拆分隧道配置可能适用于某些 VPN 客户端平台，但可能不能完全涵盖关键 Office 365 场景，并且可能与基于 IP 的 VPN 路由规则相冲突。</span><span class="sxs-lookup"><span data-stu-id="81074-126">FQDN or AppID-based split tunnel configurations, while possible on certain VPN client platforms, may not fully cover key Office 365 scenarios and may conflict with IP based VPN routing rules.</span></span> <span data-ttu-id="81074-127">因此，Microsoft 不建议使用 Office 365 FQDN 来配置拆分隧道 VPN。</span><span class="sxs-lookup"><span data-stu-id="81074-127">For this reason, Microsoft does not recommend using Office 365 FQDNs to configure split tunnel VPN.</span></span> <span data-ttu-id="81074-128">使用 FQDN 配置在其他相关方案中可能非常有用，例如 .pac 文件自定义或实现代理绕过。</span><span class="sxs-lookup"><span data-stu-id="81074-128">The use of FQDN configuration may be useful in other related scenarios, such as .pac file customizations or to implement proxy bypass.</span></span>

<span data-ttu-id="81074-129">有关完整的实现指南，请参阅[实现 Office 365 的 VPN 拆分隧道](office-365-vpn-implement-split-tunnel.md)。</span><span class="sxs-lookup"><span data-stu-id="81074-129">For full implementation guidance, see [Implementing VPN split tunnelling for Office 365](office-365-vpn-implement-split-tunnel.md).</span></span>

## <a name="the-vpn-split-tunnel-strategy"></a><span data-ttu-id="81074-130">VPN 拆分隧道策略</span><span class="sxs-lookup"><span data-stu-id="81074-130">The VPN split tunnel strategy</span></span>

<span data-ttu-id="81074-131">传统的公司网络通常旨在在预云环境中安全工作，其中最重要的数据、服务和应用程序在本地托管，并且与大多数用户一样直接连接到内部公司网络。</span><span class="sxs-lookup"><span data-stu-id="81074-131">Traditional corporate networks are often designed to work securely for a pre-cloud world where most important data, services, applications are hosted on premises and are directly connected to the internal corporate network, as are the majority of users.</span></span> <span data-ttu-id="81074-132">因此，网络基础结构是围绕这些元素构建的，分支机构通过_多协议标签切换 (MPLS)_ 网络连接到总部，而远程用户必须通过 VPN 连接到公司网络才能访问本地终结点和 Internet。</span><span class="sxs-lookup"><span data-stu-id="81074-132">Thus network infrastructure is built around these elements in that branch offices are connected to the head office via _Multiprotocol Label Switching (MPLS)_ networks, and remote users must connect to the corporate network over a VPN to access both on premises endpoints and the Internet.</span></span> <span data-ttu-id="81074-133">在此模型中，来自远程用户的所有流量都将遍历公司网络，并通过公共出口点路由到云服务。</span><span class="sxs-lookup"><span data-stu-id="81074-133">In this model, all traffic from remote users traverses the corporate network and is routed to the cloud service through a common egress point.</span></span>

![强制 VPN 配置](media/vpn-split-tunnelling/vpn-model-1.png)

<span data-ttu-id="81074-135">_图 2：适用于远程用户的公共 VPN 解决方案，其中所有流量都会被强制流回公司网络，而无需考虑目标_</span><span class="sxs-lookup"><span data-stu-id="81074-135">_Figure 2: A common VPN solution for remote users where all traffic is forced back into the corporate network regardless of destination_</span></span>

<span data-ttu-id="81074-136">随着组织将数据和应用程序移动到云，此模型效率开始下降，因为它很快变得累赘、费用高昂且不可缩放，这严重影响了用户的网络性能和效率，并限制了组织适应不断变化的需求的能力。</span><span class="sxs-lookup"><span data-stu-id="81074-136">As organizations move data and applications to the cloud, this model has begun to become less effective as it quickly becomes cumbersome, expensive and unscalable, significantly impacting network performance and efficiency of users and restricting the ability of the organization to adapt to changing needs.</span></span> <span data-ttu-id="81074-137">许多 Microsoft 客户报告几年前 80% 的网络流量都是指向内部目标，但到 2020 年 80% 以上的流量都连接到一个基于云的外部资源。</span><span class="sxs-lookup"><span data-stu-id="81074-137">Numerous Microsoft customers have reported that a few years ago 80% of network traffic was to an internal destination, but in 2020 80% plus of traffic connects to an external cloud based resource.</span></span>

<span data-ttu-id="81074-138">COVID-19 危机加剧了此问题，需要立即为绝大多数组织提供解决方案。</span><span class="sxs-lookup"><span data-stu-id="81074-138">The COVID-19 crisis has aggravated this problem to require immediate solutions for the vast majority of organizations.</span></span> <span data-ttu-id="81074-139">许多客户发现强制 VPN 模型的缩放性或性能不足以实现 100% 的远程工作场景，例如这次危机所需的远程工作场景。</span><span class="sxs-lookup"><span data-stu-id="81074-139">Many customers have found that the forced VPN model is not scalable or performant enough for 100% remote work scenarios such as that which this crisis has necessitated.</span></span> <span data-ttu-id="81074-140">为使这些组织继续高效运作，需要快速提供解决方案。</span><span class="sxs-lookup"><span data-stu-id="81074-140">Rapid solutions are required for these organization to continue to operate efficiently.</span></span>

<span data-ttu-id="81074-141">对于 Office 365 服务，Microsoft 在为服务设计连接要求时已充分考虑到这一问题，可在其中非常简单快速地优化一组集中的、严格控制和相对静态的服务终结点，以便为访问服务的用户提供高性能，减少 VPN 基础结构的负担，使其能够被仍然需要它的流量使用。</span><span class="sxs-lookup"><span data-stu-id="81074-141">For the Office 365 service, Microsoft has designed the connectivity requirements for the service with this problem squarely in mind, where a focused, tightly controlled and relatively static set of service endpoints can be optimized very simply and quickly so as to deliver high performance for users accessing the service, and reducing the burden on the VPN infrastructure so it can be used by traffic which still requires it.</span></span>

<span data-ttu-id="81074-142">Office 365 将 Office 365 所需的终结点分为三类：**优化**、**允许**和**默认**。</span><span class="sxs-lookup"><span data-stu-id="81074-142">Office 365 categorizes the required endpoints for Office 365 into three categories: **Optimize**, **Allow** and **Default**.</span></span> <span data-ttu-id="81074-143">**优化**终结点是我们的重点，具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="81074-143">**Optimize** endpoints are our focus here and have the following characteristics:</span></span>

- <span data-ttu-id="81074-144">为 Microsoft 拥有和托管的终结点，托管在 Microsoft 基础结构上</span><span class="sxs-lookup"><span data-stu-id="81074-144">Are Microsoft owned and managed endpoints, hosted on Microsoft infrastructure</span></span>
- <span data-ttu-id="81074-145">提供了 IP</span><span class="sxs-lookup"><span data-stu-id="81074-145">Have IPs provided</span></span>
- <span data-ttu-id="81074-146">低更改率，预计仍保持较小数量（目前有 20 个 IP 子网）</span><span class="sxs-lookup"><span data-stu-id="81074-146">Low rate of change and are expected to remain small in number(currently 20 IP subnets)</span></span>
- <span data-ttu-id="81074-147">高容量和/或延迟敏感</span><span class="sxs-lookup"><span data-stu-id="81074-147">Are high volume and/or latency sensitive</span></span>
- <span data-ttu-id="81074-148">可在服务中提供所需的安全元素，而不是在网络上内联</span><span class="sxs-lookup"><span data-stu-id="81074-148">Are able to have required security elements provided in the service rather than inline on the network</span></span>
- <span data-ttu-id="81074-149">约占 Office 365 服务流量的 70-80%</span><span class="sxs-lookup"><span data-stu-id="81074-149">Account for around 70-80% of the volume of traffic to the Office 365 service</span></span>

<span data-ttu-id="81074-150">这组严格限定范围的终结点可以从强制 VPN 隧道中分离出来，并通过用户的本地接口安全直接地发送到 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="81074-150">This tightly scoped set of endpoints can be split out of the forced VPN tunnel and sent securely and directly to the Office 365 service via the user's local interface.</span></span> <span data-ttu-id="81074-151">这称为**拆分隧道**。</span><span class="sxs-lookup"><span data-stu-id="81074-151">This is known as **split tunnelling**.</span></span>

<span data-ttu-id="81074-152">可在服务内的不同层针对这些终结点更高效地传递 DLP、AV 保护、身份验证和访问控制等安全元素。</span><span class="sxs-lookup"><span data-stu-id="81074-152">Security elements such as DLP, AV protection, authentication and access control can all be delivered much more efficiently against these endpoints at different layers within the service.</span></span> <span data-ttu-id="81074-153">由于我们还将大部分流量从 VPN 解决方案中转移出去，这将为仍然依赖于它的业务关键流量释放 VPN 容量。</span><span class="sxs-lookup"><span data-stu-id="81074-153">As we also divert the bulk of the traffic volume away from the VPN solution, this frees the VPN capacity up for business critical traffic which still relies on it.</span></span> <span data-ttu-id="81074-154">在许多情况下，它还应消除通过冗长而昂贵的升级程序来应对这种新操作方式的需要。</span><span class="sxs-lookup"><span data-stu-id="81074-154">It also should remove the need in many cases to go through a lengthy and costly upgrade program to deal with this new way of operating.</span></span>

![拆分隧道 VPN 配置](media/vpn-split-tunnelling/vpn-model-2.png)

<span data-ttu-id="81074-156">_图 3：将定义的 Office 365 异常直接发送到服务的 VPN 拆分隧道解决方案。所有其他流量都将强制流回公司网络（无论目标如何）。_</span><span class="sxs-lookup"><span data-stu-id="81074-156">_Figure 3: A VPN split tunnel solution with defined Office 365 exceptions sent direct to the service. All other traffic is forced back into the corporate network regardless of destination._</span></span>

<span data-ttu-id="81074-157">从安全角度来看，Microsoft 提供了一系列安全功能，可用于提供类似甚至增强的安全性，而不是由本地安全堆栈通过内联检查提供的安全性。</span><span class="sxs-lookup"><span data-stu-id="81074-157">From a security perspective, Microsoft has an array of security features which can be used to provide similar, or even enhanced security than that delivered by inline inspection by on premises security stacks.</span></span> <span data-ttu-id="81074-158">Microsoft 安全团队的博客文章[安全专业人员和 IT 人员在当前独特的远程工作场景中实现新式安全控制的替代方法](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)对可用功能进行了清晰的总结，你将在本文找到更详细的指导。</span><span class="sxs-lookup"><span data-stu-id="81074-158">The Microsoft Security team's blog post [Alternative ways for security professionals and IT to achieve modern security controls in today's unique remote work scenarios](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) has a clear summary of features available and you'll find more detailed guidance within this article.</span></span> <span data-ttu-id="81074-159">有关 Microsoft 实现 VPN 拆分隧道的信息，还可以参阅[运行 VPN：Microsoft 如何让远程工作人员互联](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)。</span><span class="sxs-lookup"><span data-stu-id="81074-159">You can also read about Microsoft's implementation of VPN split tunnelling at [Running on VPN: How Microsoft is keeping its remote workforce connected](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).</span></span>

<span data-ttu-id="81074-160">在许多情况下，可在几个小时内完成此实现，以便快速解决在组织迅速转变到全面远程工作时面临的最紧迫的问题之一。</span><span class="sxs-lookup"><span data-stu-id="81074-160">In many cases, this implementation can be achieved in a matter of hours, allowing rapid resolution to one of the most pressing problems facing organizations as they rapidly shift to full scale remote working.</span></span> <span data-ttu-id="81074-161">有关 VPN 拆分隧道的实现指南，请参阅[实现 Office 365 的 VPN 拆分隧道](office-365-vpn-implement-split-tunnel.md)。</span><span class="sxs-lookup"><span data-stu-id="81074-161">For VPN split tunnel implementation guidance, see [Implementing VPN split tunnelling for Office 365](office-365-vpn-implement-split-tunnel.md).</span></span>

>[!NOTE]
><span data-ttu-id="81074-162">Microsoft 已经承诺至少在 **2020 年 6 月 30 日**前挂起对 Office 365“优化”\*\*\*\* 终结点的更改，以便客户专注于其他挑战，而不是在最初实施后维护终结点白名单。</span><span class="sxs-lookup"><span data-stu-id="81074-162">Microsoft has committed to suspending changes to **Optimize** endpoints for Office 365 until at least **June 30 2020**, allowing customers to focus on other challenges rather than maintaining the endpoint whitelist once initially implemented.</span></span>

## <a name="related-topics"></a><span data-ttu-id="81074-163">相关主题</span><span class="sxs-lookup"><span data-stu-id="81074-163">Related topics</span></span>

[<span data-ttu-id="81074-164">实现 Office 365 的 VPN 拆分隧道</span><span class="sxs-lookup"><span data-stu-id="81074-164">Implementing VPN split tunnelling for Office 365</span></span>](office-365-vpn-implement-split-tunnel.md)

[<span data-ttu-id="81074-165">面向中国用户的 Office 365 性能优化</span><span class="sxs-lookup"><span data-stu-id="81074-165">Office 365 performance optimization for China users</span></span>](office-365-networking-china.md)

[<span data-ttu-id="81074-166">安全专业人员和 IT 人员在当前独特的远程工作场景中实现新式安全控制的替代方法（Microsoft 安全团队博客）</span><span class="sxs-lookup"><span data-stu-id="81074-166">Alternative ways for security professionals and IT to achieve modern security controls in today's unique remote work scenarios (Microsoft Security Team blog)</span></span>](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[<span data-ttu-id="81074-167">增强 Microsoft 的 VPN 性能：使用 Windows 10 VPN 配置文件以允许自动打开连接</span><span class="sxs-lookup"><span data-stu-id="81074-167">Enhancing VPN performance at Microsoft: using Windows 10 VPN profiles to allow auto-on connections</span></span>](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[<span data-ttu-id="81074-168">运行 VPN：Microsoft 如何让远程工作人员互联</span><span class="sxs-lookup"><span data-stu-id="81074-168">Running on VPN: How Microsoft is keeping its remote workforce connected</span></span>](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[<span data-ttu-id="81074-169">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="81074-169">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="81074-170">评估 Office 365 网络连接</span><span class="sxs-lookup"><span data-stu-id="81074-170">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)

[<span data-ttu-id="81074-171">Office 365 网络载入工具</span><span class="sxs-lookup"><span data-stu-id="81074-171">Office 365 Network Onboarding tool</span></span>](https://aka.ms/netonboard)
