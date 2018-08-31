---
title: 实现 ExpressRoute for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
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
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: Office 365 ExpressRoute 提供备用路由路径许多 internet 面向 Office 365 服务。Office 365 ExpressRoute 的体系结构基于广告已可访问 internet 的后续重新发布到这些 IP 前缀您已设置 ExpressRoute 电路到的 Office 365 服务的公共 IP 前缀您的网络。与 ExpressRoute 有效地启用多个不同的路由路径，通过 internet 和 ExpressRoute，许多 Office 365 服务。此状态的路由网络上可能表示重大更改至设计您的内部网络拓扑的方式。
ms.openlocfilehash: c4479a236d1419293dbd433e8d3c10a11ea5fb45
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539888"
---
# <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="bd8c8-106">实现 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="bd8c8-106">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="bd8c8-p102">Office 365 ExpressRoute 提供备用路由路径许多 internet 面向 Office 365 服务。Office 365 ExpressRoute 的体系结构基于广告已可访问 internet 的后续重新发布到这些 IP 前缀您已设置 ExpressRoute 电路到的 Office 365 服务的公共 IP 前缀您的网络。与 ExpressRoute 有效地启用多个不同的路由路径，通过 internet 和 ExpressRoute，许多 Office 365 服务。此状态的路由网络上可能表示重大更改至设计您的内部网络拓扑的方式。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p102">ExpressRoute for Office 365 provides an alternate routing path to many internet facing Office 365 services. The architecture of ExpressRoute for Office 365 is based on advertising public IP prefixes of Office 365 services that are already accessible over the Internet into your provisioned ExpressRoute circuits for subsequent redistribution of those IP prefixes into your network. With ExpressRoute you effectively enable several different routing paths, through the internet and through ExpressRoute, for many Office 365 services. This state of routing on your network may represent a significant change to how your internal network topology is designed.</span></span>
  
 <span data-ttu-id="bd8c8-111">**状态：** 完整的指南 v2</span><span class="sxs-lookup"><span data-stu-id="bd8c8-111">**Status:** Complete Guide v2</span></span>
  
<span data-ttu-id="bd8c8-p103">您必须仔细规划 Office 365 实现您 ExpressRoute 以适应还体现出路由可通过两个专线获得与插入到核心网络与 internet 的路由的网络复杂性。如果您和您的团队不执行详细的规划和测试本指南中，没有高风险会遇到间歇性或总断开连接到 Office 365 服务启用 ExpressRoute 电路后。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p103">You must carefully plan your ExpressRoute for Office 365 implementation to accommodate for the network complexities of having routing available via both a dedicated circuit with routes injected into your core network and the internet. If you and your team don't perform the detailed planning and testing in this guide, there is a high risk you'll experience intermittent or a total loss of connectivity to Office 365 services when the ExpressRoute circuit is enabled.</span></span>
  
<span data-ttu-id="bd8c8-p104">若要成功实施，您将需要分析基础结构要求、 穿过详细的网络评估和设计、 仔细规划以暂存、 控制更严格的方式，推出和生成详细的验证和测试计划。对于大型、 分布式环境不经常跨越几个月内实现。本指南旨在帮助您做好计划。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p104">To have a successful implementation, you will need to analyze your infrastructure requirements, go through detailed network assessment and design, carefully plan the rollout in a staged and controlled manner, and build a detailed validation and testing plan. For a large, distributed environment it's not uncommon to see implementations span several months. This guide is designed to help you plan ahead.</span></span>
  
<span data-ttu-id="bd8c8-p105">大型成功部署可能规划执行六个月，它通常包括包括网络、 防火墙和代理服务器管理员、 Office 365 管理员、 安全、 最终用户支持、 项目在组织中的从多个区域的工作组成员管理和管理层的支持。您在规划过程中的投资将降低将遇到停机时间或复杂和昂贵疑难解答中产生的部署故障的可能性。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p105">Large successful deployments may take six months in planning and often include team members from many areas in the organization including networking, Firewall and Proxy server administrators, Office 365 administrators, security, end-user support, project management, and executive sponsorship. Your investment in the planning process will reduce the likelihood that you'll experience deployment failures resulting in downtime or complex and expensive troubleshooting.</span></span>
  
<span data-ttu-id="bd8c8-119">我们期望以下必备启动此实施指南之前完成。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-119">We expect the following pre-requisites to be completed before this implementation guide is started.</span></span>
  
1. <span data-ttu-id="bd8c8-120">您已完成的网络评估，以确定是否建议并批准 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-120">You've completed a network assessment to determine if ExpressRoute is recommended and approved.</span></span>

2. <span data-ttu-id="bd8c8-p106">您已选择 ExpressRoute 网络服务提供商。查找有关[ExpressRoute 合作伙伴和对等位置](https://azure.microsoft.com/documentation/articles/expressroute-locations/)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p106">You've selected an ExpressRoute network service provider. Find details about the [ExpressRoute partners and peering locations](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span>

3. <span data-ttu-id="bd8c8-123">您已经已阅读并了解[ExpressRoute 文档](https://azure.microsoft.com/documentation/services/expressroute/)，并能够满足 ExpressRoute 必备端到端内部网络。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-123">You've already read and understand the [ExpressRoute documentation](https://azure.microsoft.com/documentation/services/expressroute/) and your internal network is able to meet ExpressRoute pre-requisites end to end.</span></span>

4. <span data-ttu-id="bd8c8-124">您的团队具有读取的所有公共指南和文档，网址为[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)， [https://aka.ms/ert](https://aka.ms/ert)，并监视若要了解的重要技术详细信息，包括第 9 频道上的[Office 365 培训的 Azure ExpressRoute](https://channel9.msdn.com/series/aer)系列：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-124">Your team has read all of the public guidance and documentation at [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365), [https://aka.ms/ert](https://aka.ms/ert), and watched the [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to gain an understanding of critical technical details including:</span></span>

      - <span data-ttu-id="bd8c8-125">Saas 与服务的 internet 依赖项。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-125">The internet dependencies of SaaS services.</span></span>

      - <span data-ttu-id="bd8c8-126">如何避免非对称的路由和处理复杂路由。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-126">How to avoid asymmetric routes and handle complex routing.</span></span>

      - <span data-ttu-id="bd8c8-127">如何合并外围安全、 可用性和应用程序级别控制。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-127">How to incorporate perimeter security, availability, and application level controls.</span></span>

## <a name="begin-by-gathering-requirements"></a><span data-ttu-id="bd8c8-128">首先收集要求</span><span class="sxs-lookup"><span data-stu-id="bd8c8-128">Begin by gathering requirements</span></span>
<span data-ttu-id="bd8c8-129"><a name="requirements"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-129"></span></span>

<span data-ttu-id="bd8c8-p107">首先确定哪些功能您打算采用贵组织中的服务。您需要确定将使用不同的 Office 365 服务的功能和在您的网络位置将承载使用这些功能的人员。使用方案的目录，您需要添加网络属性的每个这些方案要求;如入站和出站网络通信流和 Office 365 终结点是否可通过 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p107">Start by determining which features and services you plan to adopt within your organization. You need to determine which features of the different Office 365 services will be used and which locations on your network will host people using those features. With the catalog of scenarios, you need to add the network attributes that each of those scenarios require; such as inbound and outbound network traffic flows and if the Office 365 endpoints are available over ExpressRoute or not.</span></span>
  
<span data-ttu-id="bd8c8-133">要收集组织的要求：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-133">To gather your organization's requirements:</span></span>
  
- <span data-ttu-id="bd8c8-p108">目录使用您的组织的 Office 365 服务的入站和出站网络流量。有关不同的 Office 365 方案需要的流的说明，请参阅 Office 365 Url 和 IP 地址范围页。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p108">Catalog the inbound and outbound network traffic for the Office 365 services your organization is using. Consult Office 365 URLs and IP address ranges page for the description of flows that different Office 365 scenarios require.</span></span>

- <span data-ttu-id="bd8c8-136">收集现有显示您的内部 WAN 中枢和拓扑的详细信息，卫星站点，最后一个英里的用户连接，路由到网络外围出口点，并代理服务的连接的网络拓扑的文档。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-136">Gather documentation of existing network topology showing details of your internal WAN backbone and topology, connectivity of satellite sites, last mile user connectivity, routing to network perimeter egress points, and proxy services.</span></span>

  - <span data-ttu-id="bd8c8-137">确定在 Office 365 和其他 Microsoft 服务将连接到，显示 internet 和建议的 ExpressRoute 连接路径的网络图表上的入站的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-137">Identify inbound service endpoints on the network diagrams that Office 365 and other Microsoft services will connect to, showing both internet and proposed ExpressRoute connection paths.</span></span>

  - <span data-ttu-id="bd8c8-138">标识所有用户地理位置和以及哪些位置当前具有到 internet 出口和建议的哪些位置存在出口 ExpressRoute 对等位置的位置之间的 WAN 连接。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-138">Identify all geographic user locations and WAN connectivity between locations along with which locations currently have an egress to the internet and which locations are proposed to have an egress to an ExpressRoute peering location.</span></span>

  - <span data-ttu-id="bd8c8-139">标识所有边缘设备，如代理、 防火墙、 等并目录排列通过 Internet 和 ExpressRoute 转到其关系。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-139">Identify all edge devices, such as proxies, firewalls, and so on and catalog their relationship to flows going over the Internet and ExpressRoute.</span></span>

  - <span data-ttu-id="bd8c8-140">文档是否最终用户将访问 Office 365 服务通过直接路由或间接应用程序代理的 Internet 和 ExpressRoute 流。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-140">Document whether end users will access Office 365 services via direct routing or indirect application proxy for both Internet and ExpressRoute flows.</span></span>

- <span data-ttu-id="bd8c8-141">添加您的租户的位置并且满足-我网络图中的位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-141">Add the location of your tenant and meet-me locations to your network diagram.</span></span>

- <span data-ttu-id="bd8c8-p109">估计的预期和观察到网络性能和延迟特性从主要用户位置到 Office 365。请记住，Office 365 是一全局和分布式的服务，用户将连接到可能不同于其租户的位置的位置。因此，建议衡量和优化通过 ExpressRoute 和 Internet 连接用户和最近 Microsoft 全局网络边缘之间的延迟。从网络评估您的发现可用于帮助完成此任务。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p109">Estimate the expected and observed network performance and latency characteristics from major user locations to Office 365. Keep in mind that Office 365 is a global and distributed set of services and users will be connecting to locations that may be different from the location of their tenant. For this reason, it is recommended to measure and optimize for latency between the user and the closest edge of Microsoft global network over ExpressRoute and Internet connections. You can use your findings from the network assessment to aid with this task.</span></span>

- <span data-ttu-id="bd8c8-p110">列出公司网络安全和高可用性要求所需满足新 ExpressRoute 连接。例如，如何用户继续获取发生的 Internet 出站或 ExpressRoute 电路失败到 Office 365 的访问权限。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p110">List company network security and high availability requirements that need to be met with the new ExpressRoute connection. For example, how do users continue to get access to Office 365 in the event of the Internet egress or ExpressRoute circuit failure.</span></span>

- <span data-ttu-id="bd8c8-p111">文档的入站和出站 Office 365 网络流将使用的 Internet 路径，其中将使用 ExpressRoute。地理位置的用户和您的本地网络拓扑的详细信息的具体情况可能需要为到另一个用户位置不同的计划。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p111">Document which inbound and outbound Office 365 network flows will use the Internet path and which will use ExpressRoute. The specifics of geographical locations of your users and details of your on-premises network topology may require the plan to be different from one user location to another.</span></span>

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a><span data-ttu-id="bd8c8-150">目录出站和入站网络流量</span><span class="sxs-lookup"><span data-stu-id="bd8c8-150">Catalog your outbound and inbound network traffic</span></span>
<span data-ttu-id="bd8c8-151"><a name="trafficCatalog"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-151"></span></span>

<span data-ttu-id="bd8c8-p112">大程度地减少路由和其他网络的复杂性，我们建议您仅使用 ExpressRoute for Office 365 的复习由于法规要求或网络评估的结果的专用连接所需的网络通信流。此外，我们建议您为项目的实施不同的不同阶段阶段 ExpressRoute 路由和方法的出站和入站网络通信流的范围。Office 365 部署 ExpressRoute 的只是用户发起出站网络通信流和离开通过 Internet 的入站的网络通信流可帮助控制增加的拓扑的复杂性和风险的简介 （英文） 的其他非对称路由的可能性。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p112">To minimize routing and other network complexities, we recommend that you only use ExpressRoute for Office 365 for the network traffic flows that are required to go over a dedicated connection due to regulatory requirements or as the result of the network assessment. Additionally, we recommend that you stage the scope of ExpressRoute routing and approach outbound and inbound network traffic flows as different and distinct stages of the implementation project. Deploy ExpressRoute for Office 365 for just user initiated outbound network traffic flows and leave inbound network traffic flows across the Internet can help to control the increase in topological complexity and risks of introducing additional asymmetric routing possibilities.</span></span>
  
<span data-ttu-id="bd8c8-155">您的网络流量目录应包含您必须在本地网络与 Microsoft 之间的所有入站和出站网络连接的列表。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-155">Your network traffic catalog should contain listings of all the inbound and outbound network connections that you'll have between your on-premises network and Microsoft.</span></span>
  
- <span data-ttu-id="bd8c8-p113">出站网络通信流是任何方案，其中启动一个连接从本地环境，如从内部客户端或服务器，与 Microsoft 服务的目标。这些连接可能到 Office 365 直接或间接，例如当连接前往通过代理服务器、 防火墙或其他网络设备路径上 Office 365。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p113">Outbound network traffic flows are any scenarios where a connection is initiated from your on-premises environment, such as from internal clients or servers, with a destination of the Microsoft services. These connections may be direct to Office 365 or indirect, such as when the connection goes through proxy servers, firewalls, or other networking devices on the path to Office 365.</span></span>

- <span data-ttu-id="bd8c8-p114">入站的网络通信流是在其中启动一个连接从 Microsoft 云到本地主机任何方案。这些连接通常需要穿过防火墙和客户安全策略要求的外部起源于流其他安全基础结构。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p114">Inbound network traffic flows are any scenarios where a connection is initiated from the Microsoft cloud to an on-premises host. These connections typically need to go through firewall and other security infrastructure that customer security policy requires for externally originated flows.</span></span>

<span data-ttu-id="bd8c8-160">阅读此文章[与 Office 365 ExpressRoute 路由](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)来确定哪些服务将发送的入站的通信并查找**Office 365 ExpressRoute**标记[Office 365 中的列的**确保路由对称**部分终结点](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)篇参考文章，以确定连接信息的其余部分。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-160">Read the **Ensuring route symmetry** section of the article [Routing with ExpressRoute for Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) to determine which services will send inbound traffic and look for the column marked **ExpressRoute for Office 365** in the [Office 365 endpoints](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) reference article to determine the rest of the connectivity information.</span></span>
  
<span data-ttu-id="bd8c8-161">对于每个服务所需的出站连接，您需要描述包括网络路由、 代理服务器配置、 检查数据包来，该服务的计划的连接和带宽需求。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-161">For each service that requires an outbound connection, you'll want to describe the planned connectivity for the service including network routing, proxy configuration, packet inspection, and bandwidth needs.</span></span>
  
<span data-ttu-id="bd8c8-p115">为每个服务所需的入站的连接，您将需要某些其他信息。Microsoft 云中的服务器将建立到本地网络连接。若要确保正确进行连接，您需要描述包括; 此连接的所有方面将接受这些入站的连接的服务的公共 DNS 条目，CIDR 格式 IPv4 IP 地址，涉及哪些 ISP 设备，则和如何入站的 NAT 或源 NAT 处理这些连接。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p115">For each service that requires an inbound connection, you'll need some additional information. Servers in the Microsoft cloud will establish connections to your on-premises network. to ensure the connections are made correctly, you'll want to describe all aspects of this connectivity, including; the public DNS entries for the services that will accept these inbound connections, the CIDR formatted IPv4 IP addresses, which ISP equipment is involved, and how inbound NAT or source NAT is handled for these connections.</span></span>
  
<span data-ttu-id="bd8c8-p116">入站的连接应检查无论是否要通过 internet 连接或 ExpressRoute 以确保非对称路由尚未引入。在某些情况下，在本地终结点的 Office 365 服务启动 5 月到入站的连接还需要由其他 Microsoft 和非 Microsoft 服务来访问。启用 ExpressRoute 路由到 Office 365 为了这些服务不断开其他方案至关重要。在许多情况下，客户可能需要实现特定更改其内部网络，如基于 NAT，以确保启用 ExpressRoute 后从 Microsoft 的入站的流保持对称的源。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p116">Inbound connections should be reviewed regardless of whether they're connecting over the internet or ExpressRoute to ensure asymmetric routing hasn't been introduced. In some cases, on-premises endpoints that Office 365 services initiate inbound connections to may also need to be accessed by other Microsoft and non-Microsoft services. It is paramount that enabling ExpressRoute routing to these services for Office 365 purposes doesn't break other scenarios. In many cases, customers may need to implement specific changes to their internal network, such as source based NAT, to ensure that inbound flows from Microsoft remain symmetric after ExpressRoute is enabled.</span></span>
  
<span data-ttu-id="bd8c8-p117">下面是详细的所需程度的示例。在这种情况下 Exchange 混合部署将路由到内部部署系统通过 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p117">Here's a sample of the level of detail required. In this case Exchange Hybrid would route to the on-premises system over ExpressRoute.</span></span>

|<span data-ttu-id="bd8c8-171">**Connection 属性**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-171">**Connection property**</span></span>|<span data-ttu-id="bd8c8-172">**值**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-172">**Value**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bd8c8-173">**网络流量方向**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-173">**Network traffic direction**</span></span> <br/> |<span data-ttu-id="bd8c8-174">入站</span><span class="sxs-lookup"><span data-stu-id="bd8c8-174">Inbound</span></span>  <br/> |
|<span data-ttu-id="bd8c8-175">**服务**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-175">**Service**</span></span> <br/> |<span data-ttu-id="bd8c8-176">Exchange 混合</span><span class="sxs-lookup"><span data-stu-id="bd8c8-176">Exchange Hybrid</span></span>  <br/> |
|<span data-ttu-id="bd8c8-177">**公共 Office 365 终结点 （源）**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-177">**Public Office 365 endpoint (source)**</span></span> <br/> |<span data-ttu-id="bd8c8-178">Exchange Online （IP 地址）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-178">Exchange Online (IP addresses)</span></span>  <br/> |
|<span data-ttu-id="bd8c8-179">**公共本地终结点 （目标）**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-179">**Public On-Premises Endpoint (destination)**</span></span> <br/> |<span data-ttu-id="bd8c8-180">5.5.5.5</span><span class="sxs-lookup"><span data-stu-id="bd8c8-180">5.5.5.5</span></span>  <br/> |
|<span data-ttu-id="bd8c8-181">**公共 (Internet) DNS 条目**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-181">**Public (Internet) DNS entry**</span></span> <br/> |<span data-ttu-id="bd8c8-182">Autodiscover.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bd8c8-182">Autodiscover.contoso.com</span></span>  <br/> |
|<span data-ttu-id="bd8c8-183">**将此本地终结点使用的其他 (非-Office 365) Microsoft 服务**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-183">**Will this on-premises endpoint be used for by other (non-Office 365) Microsoft services**</span></span> <br/> |<span data-ttu-id="bd8c8-184">否</span><span class="sxs-lookup"><span data-stu-id="bd8c8-184">No</span></span>  <br/> |
|<span data-ttu-id="bd8c8-185">**将此本地终结点系统使用的用户/Internet 上**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-185">**Will this on-premises endpoint be used by users/systems on the Internet**</span></span> <br/> |<span data-ttu-id="bd8c8-186">是</span><span class="sxs-lookup"><span data-stu-id="bd8c8-186">Yes</span></span>  <br/> |
|<span data-ttu-id="bd8c8-187">**内部发布通过公用终结点的系统**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-187">**Internal systems published through public endpoints**</span></span> <br/> |<span data-ttu-id="bd8c8-188">Exchange Server 客户端访问角色 （本地） 192.168.101 192.168.102、 192.168.103</span><span class="sxs-lookup"><span data-stu-id="bd8c8-188">Exchange Server client access role (on-premises) 192.168.101, 192.168.102, 192.168.103</span></span>  <br/> |
|<span data-ttu-id="bd8c8-189">**公用终结点的 IP advertisement**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-189">**IP advertisement of the public endpoint**</span></span> <br/> |<span data-ttu-id="bd8c8-190">**到 Internet**: 5.5.0.0/16</span><span class="sxs-lookup"><span data-stu-id="bd8c8-190">**To Internet**: 5.5.0.0/16</span></span>  <br/> <span data-ttu-id="bd8c8-191">**到 ExpressRoute**: 5.5.5.0/24</span><span class="sxs-lookup"><span data-stu-id="bd8c8-191">**To ExpressRoute**: 5.5.5.0/24</span></span>  <br/> |
|<span data-ttu-id="bd8c8-192">**安全/外围控件**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-192">**Security/Perimeter Controls**</span></span> <br/> |<span data-ttu-id="bd8c8-193">**Internet 路径**： DeviceID_002</span><span class="sxs-lookup"><span data-stu-id="bd8c8-193">**Internet path**: DeviceID_002</span></span>  <br/> <span data-ttu-id="bd8c8-194">**ExpressRoute 路径**： DeviceID_003</span><span class="sxs-lookup"><span data-stu-id="bd8c8-194">**ExpressRoute path**: DeviceID_003</span></span>  <br/> |
|<span data-ttu-id="bd8c8-195">**高可用性**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-195">**High Availability**</span></span> <br/> |<span data-ttu-id="bd8c8-196">主动/主动跨 2 地理位置冗余</span><span class="sxs-lookup"><span data-stu-id="bd8c8-196">Active/Active across 2 geo-redundant</span></span>  <br/> <span data-ttu-id="bd8c8-197">ExpressRoute 电路-芝加哥和达拉斯</span><span class="sxs-lookup"><span data-stu-id="bd8c8-197">ExpressRoute circuits - Chicago and Dallas</span></span>  <br/> |
|<span data-ttu-id="bd8c8-198">**路径对称控件**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-198">**Path symmetry control**</span></span> <br/> |<span data-ttu-id="bd8c8-199">**方法**： 源 NAT</span><span class="sxs-lookup"><span data-stu-id="bd8c8-199">**Method**: Source NAT</span></span>  <br/> <span data-ttu-id="bd8c8-200">**Internet 路径**： 源 NAT 入站连接到 192.168.5.5</span><span class="sxs-lookup"><span data-stu-id="bd8c8-200">**Internet path**: Source NAT inbound connections to 192.168.5.5</span></span>  <br/> |<span data-ttu-id="bd8c8-201">**ExpressRoute 路径**： 源 NAT 连接到 192.168.1.0 （芝加哥） 和 192.168.2.0 （达拉斯）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-201">**ExpressRoute path**: Source NAT connections to 192.168.1.0 (Chicago) and 192.168.2.0 (Dallas)</span></span>  <br/> |

<span data-ttu-id="bd8c8-202">下面是一种服务，仅出站的示例：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-202">Here's a sample of a service that is outbound only:</span></span>
|<span data-ttu-id="bd8c8-203">**Connection 属性**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-203">**Connection property**</span></span>|<span data-ttu-id="bd8c8-204">**值**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-204">**Value**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bd8c8-205">**网络流量方向**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-205">**Network traffic direction**</span></span> <br/> |<span data-ttu-id="bd8c8-206">出站</span><span class="sxs-lookup"><span data-stu-id="bd8c8-206">Outbound</span></span>  <br/> |
|<span data-ttu-id="bd8c8-207">**服务**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-207">**Service**</span></span> <br/> |<span data-ttu-id="bd8c8-208">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bd8c8-208">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="bd8c8-209">**本地终结点 （源）**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-209">**On-premises endpoint (source)**</span></span> <br/> |<span data-ttu-id="bd8c8-210">用户工作站</span><span class="sxs-lookup"><span data-stu-id="bd8c8-210">User workstation</span></span>  <br/> |
|<span data-ttu-id="bd8c8-211">**公共 Office 365 终结点 （目标）**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-211">**Public Office 365 endpoint (destination)**</span></span> <br/> |<span data-ttu-id="bd8c8-212">SharePoint Online （IP 地址）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-212">SharePoint Online (IP addresses)</span></span>  <br/> |
|<span data-ttu-id="bd8c8-213">**公共 (Internet) DNS 条目**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-213">**Public (Internet) DNS entry**</span></span> <br/> |<span data-ttu-id="bd8c8-214">\*。 sharepoint.com （和其他 Fqdn）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-214">\*.sharepoint.com (and additional FQDNs)</span></span>  <br/> |
|<span data-ttu-id="bd8c8-215">**CDN 引用**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-215">**CDN Referrals**</span></span> <br/> |<span data-ttu-id="bd8c8-216">cdn.sharepointonline.com （和其他 Fqdn）-CDN 提供商维护的 IP 地址)</span><span class="sxs-lookup"><span data-stu-id="bd8c8-216">cdn.sharepointonline.com (and additional FQDNs) - IP addresses maintained by CDN providers)</span></span>  <br/> |
|<span data-ttu-id="bd8c8-217">**IP 广告和使用 NAT**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-217">**IP advertisement and NAT in use**</span></span> <br/> |<span data-ttu-id="bd8c8-218">**Internet 路径/源 NAT**: 1.1.1.0/24</span><span class="sxs-lookup"><span data-stu-id="bd8c8-218">**Internet path/Source NAT**: 1.1.1.0/24</span></span>  <br/> <span data-ttu-id="bd8c8-219">**ExpressRoute 路径/源 NAT**: 1.1.2.0/24 （芝加哥） 和 1.1.3.0/24 （达拉斯）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-219">**ExpressRoute path/Source NAT**: 1.1.2.0/24 (Chicago) and 1.1.3.0/24 (Dallas)</span></span>  <br/> |
|<span data-ttu-id="bd8c8-220">**连接方法**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-220">**Connectivity method**</span></span> <br/> |<span data-ttu-id="bd8c8-221">**Internet**： 通过第 7 层代理 （.pac 文件）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-221">**Internet**: via layer 7 proxy (.pac file)</span></span>  <br/> <span data-ttu-id="bd8c8-222">**ExpressRoute**： 直接路由 （没有代理）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-222">**ExpressRoute**: direct routing (no proxy)</span></span>  <br/> |
|<span data-ttu-id="bd8c8-223">**安全/外围控件**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-223">**Security/Perimeter Controls**</span></span> <br/> |<span data-ttu-id="bd8c8-224">**Internet 路径**： DeviceID_002</span><span class="sxs-lookup"><span data-stu-id="bd8c8-224">**Internet path**: DeviceID_002</span></span>  <br/> <span data-ttu-id="bd8c8-225">**ExpressRoute 路径**： DeviceID_003</span><span class="sxs-lookup"><span data-stu-id="bd8c8-225">**ExpressRoute path**: DeviceID_003</span></span>  <br/> |
|<span data-ttu-id="bd8c8-226">**高可用性**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-226">**High Availability**</span></span> <br/> |<span data-ttu-id="bd8c8-227">**Internet 路径**： 冗余的 internet 出站</span><span class="sxs-lookup"><span data-stu-id="bd8c8-227">**Internet path**: Redundant internet egress</span></span>  <br/> <span data-ttu-id="bd8c8-228">**ExpressRoute 路径**： 主动/主动 ' 作用硬刷跨 2 地理位置冗余 ExpressRoute 电路-芝加哥和达拉斯路由</span><span class="sxs-lookup"><span data-stu-id="bd8c8-228">**ExpressRoute path**: Active/Active 'hot potato' routing across 2 geo-redundant ExpressRoute circuits - Chicago and Dallas</span></span>  <br/> |
|<span data-ttu-id="bd8c8-229">**路径对称控件**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-229">**Path symmetry control**</span></span> <br/> |<span data-ttu-id="bd8c8-230">**方法**： 源的所有连接的 NAT</span><span class="sxs-lookup"><span data-stu-id="bd8c8-230">**Method**: Source NAT for all connections</span></span>  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a><span data-ttu-id="bd8c8-231">网络拓扑设计区域的连接</span><span class="sxs-lookup"><span data-stu-id="bd8c8-231">Your network topology design with regional connectivity</span></span>
<span data-ttu-id="bd8c8-232"><a name="topology"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-232"></span></span>

<span data-ttu-id="bd8c8-p118">了解服务和其关联的网络通信流之后，您可以创建包含这些新连接要求并阐述所做的将使用 Office 365 ExpressRoute 的网络图表。图表应包括：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p118">Once you understand the services and their associated network traffic flows, you can create a network diagram that incorporates these new connectivity requirements and illustrates the changes you'll make to use ExpressRoute for Office 365. Your diagram should include:</span></span>
  
1. <span data-ttu-id="bd8c8-235">从访问 Office 365 和其他服务的所有用户位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-235">All user locations where Office 365 and other services will be accessed from.</span></span>

2. <span data-ttu-id="bd8c8-236">所有 internet 和 ExpressRoute 出口点。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-236">All internet and ExpressRoute egress points.</span></span>

3. <span data-ttu-id="bd8c8-237">出站和入站的所有设备管理网络，包括路由器、 防火墙、 应用程序代理服务器，以及入侵检测/防护注销的连接。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-237">All outbound and inbound devices that manage connectivity in and out of the network, including routers, firewalls, application proxy servers, and intrusion detection/prevention.</span></span>

4. <span data-ttu-id="bd8c8-238">对于所有入站流量，例如接受来自 ADFS web 应用程序代理服务器的连接的内部 ADFS 服务器的内部目标。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-238">Internal destinations for all inbound traffic, such as internal ADFS servers that accept connections from the ADFS web application proxy servers.</span></span>

5. <span data-ttu-id="bd8c8-239">将播发的所有 IP 子网的目录</span><span class="sxs-lookup"><span data-stu-id="bd8c8-239">Catalog of all IP subnets that will be advertised</span></span>

6. <span data-ttu-id="bd8c8-240">确定每个位置人员将在其中访问从 Office 365 并列出 meet-我用于 ExpressRoute 的位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-240">Identify each location where people will access Office 365 from and list the meet-me locations that will be used for ExpressRoute.</span></span>

7. <span data-ttu-id="bd8c8-241">位置和您的内部网络拓扑，其中将接受从 ExpressRoute 获知 Microsoft IP 前缀，部分筛选并传播到。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-241">Locations and portions of your internal network topology, where Microsoft IP prefixes learned from ExpressRoute will be accepted, filtered and propagated to.</span></span>

8. <span data-ttu-id="bd8c8-242">网络拓扑应说明的每个网络段的地理位置和如何与 Microsoft 网络连接通过 ExpressRoute 和/或 Internet。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-242">The network topology should illustrate the geographic location of each network segment and how it connects to the Microsoft network over ExpressRoute and/or the Internet.</span></span>

<span data-ttu-id="bd8c8-243">下图显示了其中的人将使用从 Office 365 到 Office 365 的入站和出站路由广告以及每个位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-243">The diagram below shows each location where people will be using Office 365 from along with the inbound and outbound routing advertisements to Office 365.</span></span>
  
![ExpressRoute 区域地理 meet-我](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
<span data-ttu-id="bd8c8-245">为出站通信，人员访问 Office 365 中三种方式之一：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-245">For outbound traffic, the people access Office 365 in one of three ways:</span></span>
  
1. <span data-ttu-id="bd8c8-246">通过开会会议-我在北美加利福尼亚州内的人员的位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-246">Through a meet-me location in North America for the people in California.</span></span>

2. <span data-ttu-id="bd8c8-247">通过开会会议-我 （香港特别行政区） 中的人员 （香港特别行政区） 中的位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-247">Through a meet-me location in Hong Kong for the people in Hong Kong.</span></span>

3. <span data-ttu-id="bd8c8-248">通过在孟加拉国其中有较少的人员，没有 ExpressRoute 电路设置 internet。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-248">Through the internet in Bangladesh where there are fewer people and no ExpressRoute circuit provisioned.</span></span>

![出站连接的区域的关系图](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
<span data-ttu-id="bd8c8-250">同样，从 Office 365 的入站的网络流量返回三种方式之一：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-250">Similarly, the inbound network traffic from Office 365 returns in one of three ways:</span></span>
  
1. <span data-ttu-id="bd8c8-251">通过开会会议-我在北美加利福尼亚州内的人员的位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-251">Through a meet-me location in North America for the people in California.</span></span>

2. <span data-ttu-id="bd8c8-252">通过开会会议-我 （香港特别行政区） 中的人员 （香港特别行政区） 中的位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-252">Through a meet-me location in Hong Kong for the people in Hong Kong.</span></span>

3. <span data-ttu-id="bd8c8-253">通过在孟加拉国其中有较少的人员，没有 ExpressRoute 电路设置 internet。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-253">Through the internet in Bangladesh where there are fewer people and no ExpressRoute circuit provisioned.</span></span>

![入站的连接的区域的关系图](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a><span data-ttu-id="bd8c8-255">确定适当的 meet-我位置</span><span class="sxs-lookup"><span data-stu-id="bd8c8-255">Determine the appropriate meet-me location</span></span>

<span data-ttu-id="bd8c8-p119">所选内容的 meet-我的位置，它们是其中 ExpressRoute 电路将您的网络连接到 Microsoft 网络的物理位置，受人员将在其中访问 Office 365 中的位置。提供 SaaS，作为 Office 365 无法工作 IaaS 或 PaaS 区域模型下与 Azure 执行相同的方式。相反，Office 365 是一分布式的协作服务，用户可能需要连接到终结点跨多个数据中心和区域，这可能不一定是在同一位置或承载用户的租户的区域。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p119">The selection of meet-me locations, which are the physical location where your ExpressRoute circuit connects your network to the Microsoft network, is influenced by the locations where people will access Office 365 from. As a SaaS offering, Office 365 does not operate under the IaaS or PaaS regional model in the same way Azure does. Instead, Office 365 is a distributed set of collaboration services, where users may need to connect to endpoints across multiple datacenters and regions, which may not necessarily be in the same location or region where the user's tenant is hosted.</span></span>
  
<span data-ttu-id="bd8c8-p120">这意味着您需要做出选择开会会议时最重要的考虑因素-我的 ExpressRoute for Office 365 的位置是将从哪里连接您的组织中的人员。常规建议的最佳的 Office 365 连接是实现路由，以使用户对 Office 365 服务的请求移交关闭到 Microsoft 网络的最短的网络路径，这还通常被称为热硬刷路由。例如，如果大多数 Office 365 用户在一个或两个位置，选择开会会议-我中这些用户的位置最接近的邻近度的位置将创建最佳的设计。如果您的公司具有许多不同的区域中的大量用户，您可能要考虑具有多个 ExpressRoute 电路并且满足-我的位置。对于某些用户位置时，Microsoft 网络和 Office 365 的最短/最优路径可能不是通过内部的 WAN 和 ExpressRoute 开会-我点，但通过 Internet。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p120">This means the most important consideration you need to make when selecting meet-me locations for ExpressRoute for Office 365 is where the people in your organization will be connecting from. The general recommendation for optimal Office 365 connectivity is implement routing, so that user requests to Office 365 services are handed off into the Microsoft network over the shortest network path, this is also often being referred to as 'hot potato' routing. For example, if most of the Office 365 users are in one or two locations, selecting meet-me locations that are in the closest proximity to the location of those users will create the optimal design. If your company has large user populations in many different regions, you may want to consider having multiple ExpressRoute circuits and meet-me locations. For some of your user locations, the shortest/most optimal path into Microsoft network and Office 365, may not be through your internal WAN and ExpressRoute meet-me points, but via the Internet.</span></span>
  
<span data-ttu-id="bd8c8-p121">通常情况下，有多个的满足-我无法选择与您的用户的相对接近区域内的位置。填写下表可指导您做出的决定。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p121">Often times, there are multiple meet-me locations that could be selected within a region with relative proximity to your users. Fill out the following table to guide your decisions.</span></span>

|<span data-ttu-id="bd8c8-266">**计划的 ExpressRoute meet-我中加利福尼亚和纽约位置**</span><span class="sxs-lookup"><span data-stu-id="bd8c8-266">**Planned ExpressRoute meet-me locations in California and New York**</span></span>||
|:-----|:-----|
|<span data-ttu-id="bd8c8-267">位置</span><span class="sxs-lookup"><span data-stu-id="bd8c8-267">Location</span></span>  <br/> |<span data-ttu-id="bd8c8-268">人员数量</span><span class="sxs-lookup"><span data-stu-id="bd8c8-268">Number of people</span></span>  <br/> |<span data-ttu-id="bd8c8-269">通过 Internet 出口预期与 Microsoft 网络延迟</span><span class="sxs-lookup"><span data-stu-id="bd8c8-269">Expected latency to Microsoft network over Internet egress</span></span>  <br/> |<span data-ttu-id="bd8c8-270">与通过 ExpressRoute Microsoft 网络的预期的延迟</span><span class="sxs-lookup"><span data-stu-id="bd8c8-270">Expected latency to Microsoft network over ExpressRoute</span></span>  <br/> |
|<span data-ttu-id="bd8c8-271">洛杉矶</span><span class="sxs-lookup"><span data-stu-id="bd8c8-271">Los Angeles</span></span>  <br/> |<span data-ttu-id="bd8c8-272">10,000</span><span class="sxs-lookup"><span data-stu-id="bd8c8-272">10,000</span></span>  <br/> |<span data-ttu-id="bd8c8-273">~ 时间</span><span class="sxs-lookup"><span data-stu-id="bd8c8-273">~15ms</span></span>  <br/> |<span data-ttu-id="bd8c8-274">~ 10ms （通过硅谷）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-274">~10ms (via Silicon Valley)</span></span>  <br/> |
|<span data-ttu-id="bd8c8-275">华盛顿</span><span class="sxs-lookup"><span data-stu-id="bd8c8-275">Washington DC</span></span>  <br/> |<span data-ttu-id="bd8c8-276">15,000</span><span class="sxs-lookup"><span data-stu-id="bd8c8-276">15,000</span></span>  <br/> |<span data-ttu-id="bd8c8-277">~ 20 毫秒</span><span class="sxs-lookup"><span data-stu-id="bd8c8-277">~20ms</span></span>  <br/> |<span data-ttu-id="bd8c8-278">~ 10ms （通过纽约）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-278">~10ms (via New York)</span></span>  <br/> |
|<span data-ttu-id="bd8c8-279">达拉斯</span><span class="sxs-lookup"><span data-stu-id="bd8c8-279">Dallas</span></span>  <br/> |<span data-ttu-id="bd8c8-280">5,000</span><span class="sxs-lookup"><span data-stu-id="bd8c8-280">5,000</span></span>  <br/> |<span data-ttu-id="bd8c8-281">~ 时间</span><span class="sxs-lookup"><span data-stu-id="bd8c8-281">~15ms</span></span>  <br/> |<span data-ttu-id="bd8c8-282">~ 为 40 毫秒 （通过纽约）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-282">~40ms (via New York)</span></span>  <br/> |

<span data-ttu-id="bd8c8-p122">后显示的 Office 365 区域的全局网络体系结构，ExpressRoute 网络服务提供商满足-我已开发位置和位置的人的数量，所以可以用来标识如果可以进行任何优化。它还可以显示全局发夹网络连接其中流量路由到远处以便听到 meet-我的位置。如果在全局网络发夹发现它应修正才能继续执行。之一查找另一个 meet-我的位置或使用选择性 Internet 临时出口点以避免发夹。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p122">Once the global network architecture showing the Office 365 region, ExpressRoute network service provider meet-me locations, and the quantity of people by location has been developed, it can be used to identify if any optimizations can be made. It may also show global hairpin network connections where traffic routes to a distant location in order to get the meet-me location. If a hairpin on the global network is discovered it should be remediated before continuing. Either find another meet-me location, or use selective Internet breakout egress points to avoid the hairpin.</span></span>
  
<span data-ttu-id="bd8c8-p123">第一个图表中，在北美显示具有两个物理位置客户的示例。您可以看到有关办公地点、 Office 365 租户位置信息和多个选择 ExpressRoute 满足-我的位置。客户在此示例中，选择开会会议-我位置基于两个原则，顺序：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p123">The first diagram, shows an example of a customer with two physical locations in North America. You can see the information about office locations, Office 365 tenant locations, and several choices for ExpressRoute meet-me locations. In this example, the customer has selected the meet-me location based on two principles, in order:</span></span>
  
1. <span data-ttu-id="bd8c8-290">组织中的人员的最接近邻近度。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-290">Closest proximity to the people in their organization.</span></span>

2. <span data-ttu-id="bd8c8-291">在 Microsoft 数据中心承载 Office 365 接近最接近。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-291">Closest in proximity to a Microsoft datacenter where Office 365 is hosted.</span></span>

![ExpressRoute 美国地理 meet-我](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
<span data-ttu-id="bd8c8-p124">稍有扩展此概念进一步示例跨国客户面对类似的信息和决策制定第二个图表显示。此客户具有仅重点增长区域中的其占用的十个人员小型工作组 （孟加拉国） 中的小型办公室。没有 meet-我马德拉斯和 Office 365 与 Microsoft 数据中心中的位置中承载马德拉斯，以便 meet-我位置意义;但是，对于十个人员的其他电路费用是繁重。如查看您的网络时，您需要确定是否比花费资金以获取其他 ExpressRoute 电路更有效参与跨网络发送您的网络通信的延迟。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p124">Expanding this concept slightly further, the second diagram shows an example multi-national customer faced with similar information and decision making. This customer has a small office in Bangladesh with only a small team of ten people focused on growing their footprint in the region. There is a meet-me location in Chennai and a Microsoft datacenter with Office 365 hosted in Chennai so a meet-me location would make sense; however, for ten people, the expense of the additional circuit is burdensome. As you look at your network, you'll need to determine if the latency involved in sending your network traffic across your network is more effective than spending the capital to acquire another ExpressRoute circuit.</span></span>
  
<span data-ttu-id="bd8c8-297">此外，（孟加拉国） 中的十个人员可能会遇到更好的性能，与通过 internet 发送到 Microsoft 网络比他们将上的路由其内部网络，我们介绍性图表中显示，并且重现其网络流量下方。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-297">Alternatively, the ten people in Bangladesh may experience better performance with their network traffic sent over the internet to the Microsoft network than they would routing on their internal network as we showed in the introductory diagrams and reproduced below.</span></span>
  
![出站连接的区域的关系图](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a><span data-ttu-id="bd8c8-299">创建 Office 365 实施计划您 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bd8c8-299">Create your ExpressRoute for Office 365 implementation plan</span></span>
<span data-ttu-id="bd8c8-300"><a name="implementation"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-300"></span></span>

<span data-ttu-id="bd8c8-301">实施计划应包含配置为在您的网络，如下所示配置所有其他基础结构的详细信息或 ExpressRoute 这两个的技术详细的信息。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-301">Your implementation plan should encompass both the technical details of configuring ExpressRoute as well as the details of configuring all the other infrastructure on your network, such as the following.</span></span>
  
- <span data-ttu-id="bd8c8-302">规划 ExpressRoute 和 Internet 之间拆分的服务。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-302">Plan which services split between ExpressRoute and Internet.</span></span>

- <span data-ttu-id="bd8c8-303">规划带宽、 安全、 高可用性和故障转移。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-303">Plan for bandwidth, security, high availability and failover.</span></span>

- <span data-ttu-id="bd8c8-304">设计入站和出站路由，包括正确的不同位置的路由路径优化</span><span class="sxs-lookup"><span data-stu-id="bd8c8-304">Design inbound and outbound routing, including proper routing path optimizations for different locations</span></span>

- <span data-ttu-id="bd8c8-305">决定最 ExpressRoute 路由将播发到您的网络和 what's 选择 Internet 或 ExpressRoute 路径; 客户端的机制例如，直接路由或应用程序代理。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-305">Decide how far ExpressRoute routes will be advertised into your network and what is the mechanism for clients to select Internet or ExpressRoute path; for example, direct routing or application proxy.</span></span>

- <span data-ttu-id="bd8c8-306">规划 DNS 记录的更改，其中包括[发件人策略框架](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx)条目。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-306">Plan DNS record changes, including [Sender Policy Framework](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) entries.</span></span>

- <span data-ttu-id="bd8c8-307">规划 NAT 策略包括出站和入站源 nat。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-307">Plan NAT strategy including outbound and inbound source NAT.</span></span>

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a><span data-ttu-id="bd8c8-308">规划 internet 和 ExpressRoute 网络路径与您路由</span><span class="sxs-lookup"><span data-stu-id="bd8c8-308">Plan your routing with both internet and ExpressRoute network paths</span></span>
<span data-ttu-id="bd8c8-309"><a name="paths"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-309"></span></span>

- <span data-ttu-id="bd8c8-310">在初始部署的所有入站的服务，例如入站电子邮件或混合连接性，建议使用 internet。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-310">For your initial deployment, all inbound services, such as inbound email or hybrid connectivity, are recommended to use the internet.</span></span>

- <span data-ttu-id="bd8c8-311">规划最终用户客户端 LAN 路由，如[配置 PAC/WPAD 文件](https://aka.ms/manageo365endpoints)、 的默认路由、 代理服务器和 BGP 路由广告。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-311">Plan end user client LAN routing, such as [configuring a PAC/WPAD file](https://aka.ms/manageo365endpoints), default route, proxy servers, and BGP route advertisements.</span></span>

- <span data-ttu-id="bd8c8-312">规划外围路由，包括代理服务器、 防火墙和云代理。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-312">Plan perimeter routing, including proxy servers, firewalls, and cloud proxies.</span></span>

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a><span data-ttu-id="bd8c8-313">规划带宽、 安全性、 高可用性和故障转移</span><span class="sxs-lookup"><span data-stu-id="bd8c8-313">Plan your bandwidth, security, high availability and failover</span></span>
<span data-ttu-id="bd8c8-314"><a name="availability"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-314"></span></span>

<span data-ttu-id="bd8c8-p125">创建规划所需的每个主要的 Office 365 工作负载的带宽。单独估计业务联机带宽要求 Exchange Online、 SharePoint Online 和 Skype。您可以使用我们提供的 Exchange Online 和 Skype for Business 作为起点; 估计计算器但是，与用户配置文件和位置的代表性样本试验性测试，需要全面了解您的组织的带宽需求。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p125">Create a plan for bandwidth required for each major Office 365 workload. Separately estimate Exchange Online, SharePoint Online, and Skype for Business Online bandwidth requirements. You can use the estimation calculators we've provided for Exchange Online and Skype for Business as a starting place; however, a pilot test with a representative sample of the user profiles and locations is required to fully understand the bandwidth needs of your organization.</span></span>
  
<span data-ttu-id="bd8c8-318">添加安全在每个 internet 和您计划 ExpressRoute 出口位置的处理方式，请记住所有 ExpressRoute 连接到 Office 365 使用公共对等和仍必须采用安全按照连接到外部您公司的安全策略网络。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-318">Add how security is handled at each internet and ExpressRoute egress location to your plan, remember all ExpressRoute connections to Office 365 use public peering and must still be secured in accordance with your company security policies of connecting to external networks.</span></span>
  
<span data-ttu-id="bd8c8-319">添加到有关哪些人员将受哪些类型的中断和如何，这些人将能够在最简单的方式执行其工作全容量计划的详细信息。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-319">Add details to your plan about which people will be affected by what type of outage and how those people will be able to perform their work at full capacity in the simplest manner.</span></span>
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a><span data-ttu-id="bd8c8-320">规划包括 Skype 的抖动、 延迟、 拥塞现象，和预留的业务要求的带宽要求</span><span class="sxs-lookup"><span data-stu-id="bd8c8-320">Plan bandwidth requirements including Skype for Business requirements on Jitter, Latency, Congestion, and Headroom</span></span>
  
<span data-ttu-id="bd8c8-321">Skype 业务 online 还具有特定的其他网络要求[媒体质量和 Skype 业务 online 中的网络连接性能](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)一文中将详细陈述。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-321">Skype for Business Online also has specific additional network requirements which are detailed in the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>
  
<span data-ttu-id="bd8c8-322">阅读[与 Office 365 ExpressRoute](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)规划网络**带宽规划 Azure ExpressRoute**部分。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-322">Read the section **Bandwidth planning for Azure ExpressRoute** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
<span data-ttu-id="bd8c8-323">当执行与您的试生产用户的带宽评估，您可以使用我们的指南;[Office 365 性能调整使用比较基准和性能历史记录](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-323">When performing a bandwidth assessment with your pilot users, you can use our guide; [Office 365 performance tuning using baselines and performance history](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).</span></span>
  
#### <a name="plan-for-high-availability-requirements"></a><span data-ttu-id="bd8c8-324">规划高可用性要求</span><span class="sxs-lookup"><span data-stu-id="bd8c8-324">Plan for high availability requirements</span></span>
  
<span data-ttu-id="bd8c8-p126">创建规划高可用性，以满足您的需求并将此并入您更新的网络拓扑图。阅读**高可用性和故障转移与 Azure ExpressRoute** [网络规划与 Office 365 ExpressRoute](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)部分。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p126">Create a plan for high availability to meet your needs and incorporate this into your updated network topology diagram. Read the section **High availability and failover with Azure ExpressRoute** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
#### <a name="plan-for-network-security-requirements"></a><span data-ttu-id="bd8c8-327">有关网络安全要求的计划</span><span class="sxs-lookup"><span data-stu-id="bd8c8-327">Plan for network security requirements</span></span>
  
<span data-ttu-id="bd8c8-p127">创建规划，以满足您的网络安全要求和这合并更新的网络拓扑关系图。阅读一节中[网络规划与 Office 365 ExpressRoute](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)**应用到 Office 365 方案的 Azure ExpressRoute 的安全控件**。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p127">Create a plan to meet your network security requirements and incorporate this into your updated network topology diagram. Read the section **Applying security controls to Azure ExpressRoute for Office 365 scenarios** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
### <a name="design-outbound-service-connectivity"></a><span data-ttu-id="bd8c8-330">设计出站服务连接</span><span class="sxs-lookup"><span data-stu-id="bd8c8-330">Design outbound service connectivity</span></span>
<span data-ttu-id="bd8c8-331"><a name="outbound"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-331"></span></span>

<span data-ttu-id="bd8c8-p128">Office 365 ExpressRoute 具有可能不熟悉的*出站*网络要求。具体而言，IP 地址的 Office 365 表示您的用户和网络，并用作出站的网络连接到 Microsoft 源终结点必须遵循下面列出的特定要求。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p128">ExpressRoute for Office 365 has  *outbound*  network requirements that may be unfamiliar. Specifically, the IP addresses that represent your users and networks to Office 365 and act as the source endpoints for outbound network connections to Microsoft must follow specific requirements outlined below.</span></span>
  
1. <span data-ttu-id="bd8c8-334">终结点必须是公共 IP 地址，注册到您的公司或向您提供 ExpressRoute 连接的运营商。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-334">The endpoints must be public IP addresses, that are registered to your company or to carrier providing ExpressRoute connectivity to you.</span></span>

2. <span data-ttu-id="bd8c8-335">终结点向 Microsoft 播发和验证接受通过必须 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-335">The endpoints must be advertised to Microsoft and validated/accepted by ExpressRoute.</span></span>

3. <span data-ttu-id="bd8c8-336">终结点必须不被播发到 Internet 具有相同或更多首选路由跃点数。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-336">The endpoints must not be advertised to the Internet with the same or more preferred routing metric.</span></span>

4. <span data-ttu-id="bd8c8-337">终结点不必须用于连接到未通过 ExpressRoute 配置的 Microsoft 服务。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-337">The endpoints must not be used for connectivity to Microsoft services that are not configured over ExpressRoute.</span></span>

<span data-ttu-id="bd8c8-p129">如果您的网络设计不满足这些要求，则您的用户将体验到 Office 365 和由于路由黑色 holing 或非对称路由其他 Microsoft 服务的连接失败高风险。对 Microsoft 服务请求路由通过 ExpressRoute，但后通过 internet，反之亦然，路由响应的数目和响应都将被状态的网络设备，如防火墙丢弃时，将发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p129">If your network design doesn't meet these requirements, there is a high risk your users will experience connectivity failures to Office 365 and other Microsoft services due to route black holing or asymmetric routing. This occurs when requests to Microsoft services are routed over ExpressRoute, but responses are routed back across the internet, or vice versa, and the responses are dropped by stateful network devices such as firewalls.</span></span>
  
<span data-ttu-id="bd8c8-p130">可以使用满足上述要求的最常用方法是网络的使用源 NAT，实现作为您的一部分或您 ExpressRoute 运营商提供。源 NAT 可以提取的详细信息和专用 IP 寻址的 internet 网络从 ExpressRoute 和;再加适当的 IP 路由广告，提供一个简便的方法，以确保路径对称。如果您使用的特定于 ExpressRoute 对等位置的状态的网络设备，您必须为每个对等以确保路径对称 ExpressRoute 实现单独的 NAT 池。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p130">The most common method you can use to meet the above requirements is to use source NAT, either implemented as a part of your network or provided by your ExpressRoute carrier. Source NAT allows you to abstract the details and private IP addressing of your internet network from ExpressRoute and; coupled with proper IP route advertisements, provide an easy mechanism to ensure path symmetry. If you're using stateful network devices that are specific to ExpressRoute peering locations, you must implement separate NAT pools for each ExpressRoute peering to ensure path symmetry.</span></span>
  
<span data-ttu-id="bd8c8-343">阅读有关[ExpressRoute NAT 要求](https://azure.microsoft.com/documentation/articles/expressroute-nat/)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-343">Read more about the [ExpressRoute NAT requirements](https://azure.microsoft.com/documentation/articles/expressroute-nat/).</span></span>
  
<span data-ttu-id="bd8c8-344">向网络拓扑图添加出站连接的更改。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-344">Add the changes for the outbound connectivity to the network topology diagram.</span></span>
  
### <a name="design-inbound-service-connectivity"></a><span data-ttu-id="bd8c8-345">设计入站的服务连接</span><span class="sxs-lookup"><span data-stu-id="bd8c8-345">Design inbound service connectivity</span></span>
<span data-ttu-id="bd8c8-346"><a name="inbound"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-346"></span></span>

<span data-ttu-id="bd8c8-p131">Office 365 企业部署大多数假设某种形式的从 Office 365 的入站连接到内部部署服务，如 Exchange、 SharePoint 和 Skype 业务混合方案、 邮箱迁移和使用 ADFS 身份验证基础结构。当启用您的本地网络与 Microsoft 之间的出站连接的附加路由路径的 ExpressRoute，这些入站的连接可能无意中会受到非对称路由，即使您打算将这些流将继续使用 Internet。建议使用如下所述的一些预防措施以确保没有 internet 不会影响基于从 Office 365 的入站的流到内部部署系统。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p131">The majority of enterprise Office 365 deployments assume some form of inbound connectivity from Office 365 to on-premises services, such as for Exchange, SharePoint, and Skype for Business hybrid scenarios, mailbox migrations, and authentication using ADFS infrastructure. When ExpressRoute you enable an additional routing path between your on-premises network and Microsoft for outbound connectivity, these inbound connections may inadvertently be impacted by asymmetric routing, even if you intend to have those flows continue to use the Internet. A few precautions described below are recommended to ensure there is no impact to Internet based inbound flows from Office 365 to on-premises systems.</span></span>
  
<span data-ttu-id="bd8c8-p132">要最小化的非对称路由入站的网络通信流风险的所有入站连接应它们路由到此路由的可见性 ExpressRoute 的网络段之前使用源 NAT。如果没有源 NAT 路由到 ExpressRoute 的可见性允许传入连接到网络段，来自 Office 365 的请求将输入从 internet，但返回转到 Office 365 的响应将更喜欢使用 ExpressRoute返回到 Microsoft 网络，导致非对称路由的网络路径。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p132">To minimize the risks of asymmetric routing for inbound network traffic flows, all of the inbound connections should use source NAT before they're routed into segments of your network which have routing visibility into ExpressRoute. If the incoming connections are allowed onto a network segment with routing visibility into ExpressRoute without source NAT, requests originating from Office 365 will enter from the internet, but the response going back to Office 365 will prefer the ExpressRoute network path back to the Microsoft network, causing asymmetric routing.</span></span>
  
<span data-ttu-id="bd8c8-352">您可能会考虑以下的实现模式，以满足此要求之一：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-352">You may consider one of the following implementation patterns to satisfy this requirement:</span></span>
  
1. <span data-ttu-id="bd8c8-353">请求路由到内部网络使用如防火墙的网络设备之前执行源 NAT 或从 Internet 到本地系统的负载路径上的平衡。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-353">Perform source NAT before requests are routed into your internal network using networking equipment such as firewalls or load balancers on the path from the Internet to your on-premises systems.</span></span>

2. <span data-ttu-id="bd8c8-354">确保 ExpressRoute 路由不会传播到网络段入站的服务，例如前端结束服务器或反向代理系统处理的 Internet 连接驻留的位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-354">Ensure that ExpressRoute routes are not propagated to the network segments where inbound services, such as front end servers or reverse proxy systems, handling Internet connections reside.</span></span>

<span data-ttu-id="bd8c8-355">显式考虑您的网络中的这些方案和保留所有入站的网络流量排列通过 Internet 有助于减少部署和操作的非对称路由的风险。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-355">Explicitly accounting for these scenarios in your network and keeping all inbound network traffic flows over the Internet helps to minimize deployment and operational risk of asymmetric routing.</span></span>
  
<span data-ttu-id="bd8c8-p133">可能有的情况，您可以选择通过 ExpressRoute 连接定向某些入站的流。有关这些方案，需要考虑以下其他注意事项。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p133">There may be cases where you may choose to direct some inbound flows over ExpressRoute connections. For these scenarios, take the following additional considerations into account.</span></span>
  
1. <span data-ttu-id="bd8c8-p134">Office 365 可以仅目标本地端点使用公用 Ip 的。这意味着，即使本地入站终结点仅通过 ExpressRoute 公开到 Office 365，它仍然需要有与之关联的公共 IP。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p134">Office 365 can only target on-premises endpoints that use public IPs. This means that even if the on-premises inbound endpoint is only exposed to Office 365 over ExpressRoute, it still needs to have public IP associated with it.</span></span>

2. <span data-ttu-id="bd8c8-p135">Office 365 服务执行来解析内部部署终结点的所有 DNS 名称解析都发生使用公共 DNS。这意味着您必须注册到 Internet 上的 IP 映射的入站的服务终结点的 FQDN。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p135">All DNS name resolution that Office 365 services perform to resolve on-premises endpoints happen using public DNS. This means that you must register inbound service endpoints' FQDN to IP mappings on the Internet.</span></span>

3. <span data-ttu-id="bd8c8-362">为了通过 ExpressRoute 接收的入站的网络连接，这些终结点的公共 IP 子网必须通过 ExpressRoute 播发到 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-362">In order to receive inbound network connections over ExpressRoute, the public IP subnets for these endpoints must to be advertised to Microsoft over ExpressRoute.</span></span>

4. <span data-ttu-id="bd8c8-363">仔细评估这些入站的网络通信流，以确保该适当的安全性和网络控件按照您的公司安全和网络策略应用于它们。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-363">Carefully evaluate these inbound network traffic flows to ensure that proper security and network controls are applied to them in accordance with your company security and network policies.</span></span>

5. <span data-ttu-id="bd8c8-p136">一次在本地入站终结点通过 ExpressRoute 公布到 Microsoft，ExpressRoute 将有效地成为的所有 Microsoft 服务，包括 Office 365 这些终结点的首选路由路径。这意味着，这些终结点子网必须仅用于与 Office 365 服务和 Microsoft 网络上的任何其他服务的通信。否则，您的设计将导致其中来自其他 Microsoft 服务首选路由入站的连接的入站邮件通过 ExpressRoute，同时返回路径将使用 Internet 非对称路由。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p136">Once your on-premises inbound endpoints are advertised to Microsoft over ExpressRoute, ExpressRoute will effectively become the preferred routing path to those endpoints for all Microsoft services, including Office 365. This means that those endpoint subnets must only be used for communications with Office 365 services and no other services on the Microsoft network. Otherwise, your design will cause asymmetric routing where inbound connections from other Microsoft services prefer to route inbound over ExpressRoute, while the return path will use the Internet.</span></span>

6. <span data-ttu-id="bd8c8-p137">在事件 ExpressRoute 电路或满足-我位置已关闭，您需要确保本地入站终结点仍将通过单独的网络路径接受请求。为多个 ExpressRoute 电路通过这些终结点，这可能意味着广告子网。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p137">In the event an ExpressRoute circuit or meet-me location is down, you'll need to ensure the on-premises inbound endpoints are still available to accept requests over a separate network path. This may mean advertising subnets for those endpoints through multiple ExpressRoute circuits.</span></span>

7. <span data-ttu-id="bd8c8-369">我们建议应用输入您的网络通过 ExpressRoute，尤其是当这些流程跨状态的网络设备，如防火墙的所有入站的网络通信流源 NAT。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-369">We recommend applying source NAT for all inbound network traffic flows entering your network through ExpressRoute, especially when these flows cross stateful network devices such as firewalls.</span></span>

8. <span data-ttu-id="bd8c8-p138">某些内部部署服务，例如 ADFS 代理或 Exchange 自动发现，可能会收到从 Office 365 服务和来自 Internet 的用户的入站的请求。这些请求的 Office 365 将通过 Internet 目标用户请求相同 FQDN。允许入站的用户连接从 internet 到内部部署这些终结点，时强制 Office 365 连接使用 ExpressRoute，表示重要路由的复杂性。对于绝大多数客户通过 ExpressRoute 实现此类复杂的方案不建议由于运营考虑事项。此额外开销包括，管理风险的非对称路由，并将要求您仔细跨多个维度管理路由广告和策略。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p138">Some on-premises services, such as ADFS proxy or Exchange autodiscover, may receive inbound requests from both Office 365 services and users from the Internet. For these requests Office 365 will target the same FQDN as user requests over the Internet. Allowing inbound user connections from the internet to those on-premises endpoints, while forcing Office 365 connections to use ExpressRoute, represents significant routing complexity. For the vast majority of customers implementing such complex scenarios over ExpressRoute is not recommended due to operational considerations. This additional overhead includes, managing risks of asymmetric routing and will require you to carefully manage routing advertisements and policies across multiple dimensions.</span></span>

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a><span data-ttu-id="bd8c8-375">更新您的网络拓扑计划，以显示如何将避免非对称的路由</span><span class="sxs-lookup"><span data-stu-id="bd8c8-375">Update your network topology plan to show how you would avoid asymmetric routes</span></span>
<span data-ttu-id="bd8c8-376"><a name="asymmetric"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-376"></span></span>

<span data-ttu-id="bd8c8-p139">您想要避免非对称的路由，以确保您的组织中的人员可以无缝使用 Office 365，以及其他重要服务在 internet 上。有两种导致非对称路由的常见配置客户可以。现在是查看您计划使用以及检查可能存在这些非对称的路由方案之一的网络配置的良机。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p139">You want to avoid asymmetric routing to ensure people in your organization can seamlessly use Office 365 as well as other important services on the internet. There are two common configurations customers have that cause asymmetric routing. Now's a good time to review the network configuration you're planning to use and check if one of these asymmetric routing scenarios could exist.</span></span>
  
<span data-ttu-id="bd8c8-p140">若要开始，我们将检查几个不同的情况下网络图与关联。在此图中，所有服务器接收的入站的请求，如 ADFS 或内部部署混合服务器位于新泽西数据中心和播发到 internet。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p140">To begin, we'll examine a few different situations associated with the following network diagram. In this diagram, all servers that receive inbound requests, such as ADFS or on-premises hybrid servers are in the New Jersey data center and are advertised to the internet.</span></span>
  
1. <span data-ttu-id="bd8c8-382">安全外围网络时，没有任何源 NAT 可用的传入请求。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-382">While the perimeter network is secure, there is no Source NAT available for incoming requests.</span></span>

2. <span data-ttu-id="bd8c8-383">新泽西数据中心中的服务器能够看到 internet 和 ExpressRoute 路由。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-383">The servers in the New Jersey data center are able to see both internet and ExpressRoute routes.</span></span>

![ExpressRoute 连接概述](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
<span data-ttu-id="bd8c8-385">我们还具有如何修复这些建议。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-385">We also have suggestions on how to fix them.</span></span>
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a><span data-ttu-id="bd8c8-386">问题 1： 云到 Internet 上的本地连接</span><span class="sxs-lookup"><span data-stu-id="bd8c8-386">Problem 1: Cloud to on-premises connection over the Internet</span></span>
  
<span data-ttu-id="bd8c8-387">下图说明了您的网络配置不通过 internet 的入站请求从 Microsoft 云提供 NAT 时所采用非对称的网络路径。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-387">The following diagram illustrates the asymmetric network path taken when your network configuration doesn't provide NAT for inbound requests from the Microsoft cloud over the internet.</span></span>
  
1. <span data-ttu-id="bd8c8-388">来自 Office 365 的入站的请求从公共 DNS 检索本地终结点的 IP 地址，并将请求发送到外围网络。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-388">The inbound request from Office 365 retrieves the IP address of the on-premises endpoint from public DNS and sends the request to your perimeter network.</span></span>

2. <span data-ttu-id="bd8c8-389">在此出错的配置，还有配置源 NAT 或可在其中流量是外围网络发送产生的实际源 IP 地址被用作返回目标。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-389">In this faulty configuration, there is no Source NAT configured or available at the perimeter network where the traffic is sent resulting in the actual source IP address being used as the return destination.</span></span>

  - <span data-ttu-id="bd8c8-390">您的网络上的服务器路由到 Office 365 返回流量通过任何可用的 ExpressRoute 网络连接。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-390">The server on your network routes the return traffic to Office 365 through any available ExpressRoute network connection.</span></span>

  - <span data-ttu-id="bd8c8-391">结果是 Office 365，从而导致断开连接到该流非对称路径。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-391">The result is an Asymmetric path for that flow to Office 365, resulting in a broken connection.</span></span>

![ExpressRoute Asymetric 路由问题 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a><span data-ttu-id="bd8c8-393">解决方案 1a： 源 NAT</span><span class="sxs-lookup"><span data-stu-id="bd8c8-393">Solution 1a: Source NAT</span></span>
  
<span data-ttu-id="bd8c8-p141">只将源 NAT 向入站请求解析此配置不正确的网络。在此图示中：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p141">Simply adding a source NAT to the inbound request resolves this misconfigured network. In this diagram:</span></span>
  
1. <span data-ttu-id="bd8c8-p142">传入请求将继续通过新泽西数据中心外围网络中输入。此源 NAT 时才可用。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p142">The incoming request continues to enter through the New Jersey data center's perimeter network. This time Source NAT is available.</span></span>

2. <span data-ttu-id="bd8c8-398">向源 NAT 而不是原始的 IP 地址，相同的网络路径沿着返回的响应中产生相关联的 IP 备份来自服务器路由的响应。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-398">The response from the server routes back toward the IP associated with the Source NAT instead of the original IP address, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由解决方案 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a><span data-ttu-id="bd8c8-400">解决方案 1b： 路由范围</span><span class="sxs-lookup"><span data-stu-id="bd8c8-400">Solution 1b: Route Scoping</span></span>
  
<span data-ttu-id="bd8c8-p143">此外，您可以选择不允许 ExpressRoute BGP 前缀要公布删除这些计算机的备用网络路径。在此图示中：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p143">Alternatively, you can choose to not allow the ExpressRoute BGP prefixes to be advertised, removing the alternate network path for those computers. In this diagram:</span></span>
  
1. <span data-ttu-id="bd8c8-p144">传入请求将继续通过新泽西数据中心外围网络中输入。这次从 Microsoft 广告通过 ExpressRoute 电路前缀不可用到新泽西数据中心。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p144">The incoming request continues to enter through the New Jersey data center's perimeter network. This time the prefixes advertised from Microsoft over the ExpressRoute circuit are not available to the New Jersey data center.</span></span>

2. <span data-ttu-id="bd8c8-405">来自后向 IP 超过可用，唯一的路由相关联的原始的 IP 地址相同的网络路径沿着返回的响应中产生的服务器路由的响应。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-405">The response from the server routes back toward the IP associated with the original IP address over the only route available, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由解决方案 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a><span data-ttu-id="bd8c8-407">问题 2： 云到本地连接，通过 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bd8c8-407">Problem 2: Cloud to on-premises connection over ExpressRoute</span></span>
  
<span data-ttu-id="bd8c8-408">下图说明了您的网络配置不通过 ExpressRoute 的入站请求从 Microsoft 云提供 NAT 时所采用非对称的网络路径。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-408">The following diagram illustrates the asymmetric network path taken when your network configuration doesn't provide NAT for inbound requests from the Microsoft cloud over ExpressRoute.</span></span>
  
1. <span data-ttu-id="bd8c8-409">来自 Office 365 的入站的请求从 DNS 中检索的 IP 地址，并将请求发送到外围网络。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-409">The inbound request from Office 365 retrieves the IP address from DNS and sends the request to your perimeter network.</span></span>

2. <span data-ttu-id="bd8c8-410">在此出错的配置，还有配置源 NAT 或可在其中流量是外围网络发送产生的实际源 IP 地址被用作返回目标。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-410">In this faulty configuration, there is no Source NAT configured or available at the perimeter network where the traffic is sent resulting in the actual source IP address being used as the return destination.</span></span>

  - <span data-ttu-id="bd8c8-411">在您的网络的计算机通过任何可用的 ExpressRoute 网络连接到 Office 365 路由返回流量。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-411">The computer on your network routes the return traffic to Office 365 through any available ExpressRoute network connection.</span></span>

  - <span data-ttu-id="bd8c8-412">结果是指向 Office 365 的非对称的连接。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-412">The result is an Asymmetric connection to Office 365.</span></span>

![ExpressRoute Asymetric 路由问题 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a><span data-ttu-id="bd8c8-414">解决方案 2： 源 NAT</span><span class="sxs-lookup"><span data-stu-id="bd8c8-414">Solution 2: Source NAT</span></span>
  
<span data-ttu-id="bd8c8-p145">只将源 NAT 向入站请求解析此配置不正确的网络。在此图示中：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p145">Simply adding a source NAT to the inbound request resolves this misconfigured network. In this diagram:</span></span>
  
1. <span data-ttu-id="bd8c8-p146">传入请求将继续通过纽约数据中心外围网络中输入。此源 NAT 时才可用。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p146">The incoming request continues to enter through the New York data center's perimeter network. This time Source NAT is available.</span></span>

2. <span data-ttu-id="bd8c8-419">向源 NAT 而不是原始的 IP 地址，相同的网络路径沿着返回的响应中产生相关联的 IP 备份来自服务器路由的响应。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-419">The response from the server routes back toward the IP associated with the Source NAT instead of the original IP address, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由解决方案 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a><span data-ttu-id="bd8c8-421">纸张确认网络设计具有路径对称</span><span class="sxs-lookup"><span data-stu-id="bd8c8-421">Paper verify that the network design has path symmetry</span></span>

<span data-ttu-id="bd8c8-p147">此时，您需要验证纸张上实施计划，提供要在其中使用 Office 365 的不同方案的路由对称。将标识预期人员使用的服务的不同功能时要采取的特定的网络路由。从本地网络和 WAN 路由，外围设备，连接路径;ExpressRoute 或 internet 和到与联机终结点的连接。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p147">At this point, you need to verify on paper that your implementation plan offers route symmetry for the different scenarios in which you'll be using Office 365. You'll identify the specific network route that is expected to be taken when a person uses different features of the service. From the on-premises network and WAN routing, to the perimeter devices, to the connectivity path; ExpressRoute or the internet, and on to the connection to the online endpoint.</span></span>
  
<span data-ttu-id="bd8c8-425">您需要这样做的所有 Office 365 网络服务以前所作为您的组织将采用的服务标识。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-425">You'll need to do this for all of the Office 365 network services that were previously identified as services that your organization will adopt.</span></span>
  
<span data-ttu-id="bd8c8-p148">它有助于执行另一个人使用路由通过此纸张审核。向他们每个网络跃点的地方以获取从其下一步路由，并确保您熟悉的路由路径的说明。请记住 ExpressRoute 始终将提供指向 Microsoft 服务器 IP 地址为其提供比 Internet 默认路由的路由成本更低的更多范围的路由。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p148">It helps to do this paper walk through of routes with a second person. Explain to them where each network hop is expected to get its next route from and ensure that you're familiar with the routing paths. Remember that ExpressRoute will always provide a more scoped route to Microsoft server IP addresses giving it lower route cost than an Internet default route.</span></span>
  
### <a name="design-client-connectivity-configuration"></a><span data-ttu-id="bd8c8-429">设计客户端连接配置</span><span class="sxs-lookup"><span data-stu-id="bd8c8-429">Design Client Connectivity Configuration</span></span>
<span data-ttu-id="bd8c8-430"><a name="asymmetric"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-430"></span></span>

![使用 ExpressRoute PAC 文件](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
<span data-ttu-id="bd8c8-p149">如果您使用代理服务器的 internet 绑定流量则您需要调整任何 PAC 或正确配置客户端配置文件，以确保您的网络上的客户端计算机发送到 Office 365 的所需的 ExpressRoute 流量，而不 transiting您的代理服务器和剩余的通信，包括一些 Office 365 的通信，发送到相关代理服务器。阅读有关[管理 Office 365 终结点](https://aka.ms/manageo365endpoints)我们指南例如 PAC 文件。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p149">If you're using a proxy server for internet bound traffic then you need to adjust any PAC or client configuration files to ensure client computers on your network are correctly configured to send the ExpressRoute traffic you desire to Office 365 without transiting your proxy server, and the remaining traffic, including some Office 365 traffic, is sent to the relevant proxy. Read our guide on [managing Office 365 endpoints](https://aka.ms/manageo365endpoints) for example PAC files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="bd8c8-p150">终结点更改经常、 根据每周的频率。您只应进行更改基于服务和您的组织已采用减少更改您将需要进行保持当前数目的功能。密切注意其中宣布所做的更改和记录保留的所有过去更改，IP 地址来公布的 RSS 源中的**有效日期**无法公布，或从广告，直到到达生效的日期。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p150">The endpoints change frequently, as often as weekly. You should only make changes based on the services and features your organization has adopted to reduce the number of changes you'll need to make to stay current. Pay close attention to the **Effective Date** in the RSS feed where the changes are announced and a record is kept of all past changes, IP addresses that are announced may not be advertised, or removed from advertisement, until the effective date is reached.</span></span>
  
## <a name="build-your-deployment-and-testing-procedures"></a><span data-ttu-id="bd8c8-437">构建您的部署和测试过程</span><span class="sxs-lookup"><span data-stu-id="bd8c8-437">Build your deployment and testing procedures</span></span>
<span data-ttu-id="bd8c8-438"><a name="testing"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-438"></span></span>

<span data-ttu-id="bd8c8-p151">实施计划应包括测试和回滚规划。如果您的实现未按预期运行，应设计计划来影响最小数人员之前在发现问题。以下是一些您计划应考虑的高级别原则。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p151">Your implementation plan should include both testing and rollback planning. If your implementation isn't functioning as expected, the plan should be designed to affect the least number of people before problems are discovered. The following are some high level principles your plan should consider.</span></span>
  
1. <span data-ttu-id="bd8c8-442">阶段网络段和用户服务入职培训大程度地减少中断。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-442">Stage the network segment and user service onboarding to minimize disruption.</span></span>

2. <span data-ttu-id="bd8c8-443">规划测试使用 traceroute 路由和 TCP 连接从单独 internet 连接的主机。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-443">Plan for testing routes with traceroute and TCP connect from a separate internet connected host.</span></span>

3. <span data-ttu-id="bd8c8-444">最好的入站和出站服务测试应与测试 Office 365 租户独立的测试网络上。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-444">Preferably, testing of inbound and outbound services should be done on an isolated test network with a test Office 365 tenant.</span></span>

      - <span data-ttu-id="bd8c8-445">或者，可以执行测试生产网络如果客户尚未不使用 Office 365 或中试验。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-445">Alternatively, testing can be performed on a production network if the customer is not yet using Office 365 or is in pilot.</span></span>

      - <span data-ttu-id="bd8c8-446">此外，测试只能执行测试留出的生产中断期间和监控。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-446">Alternatively, testing can be performed during a production outage that is set aside for test and monitoring only.</span></span>

      - <span data-ttu-id="bd8c8-p152">此外，通过检查路由上第三层路由器的每个节点的每个服务来完成测试。无其他测试是否可能是因为缺少物理测试带来了风险，应仅使用此回退。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p152">Alternatively, testing can be done by checking routes for each service on each layer 3 router node. This fall back should only be used if no other testing is possible since a lack of physical testing introduces risk.</span></span>

### <a name="build-your-deployment-procedures"></a><span data-ttu-id="bd8c8-449">构建您的部署过程</span><span class="sxs-lookup"><span data-stu-id="bd8c8-449">Build your deployment procedures</span></span>

<span data-ttu-id="bd8c8-p153">部署过程应推出的人员的小型组分阶段部署到的人员更大的组之前，测试允许。以下是几种方法可以 ExpressRoute 部署阶段。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p153">Your deployment procedures should roll out to small groups of people in stages to allow for testing before deploying to larger groups of people. The following are several ways to stage the deployment of ExpressRoute.</span></span>
  
1. <span data-ttu-id="bd8c8-452">使用 Microsoft 对等设置 ExpressRoute 和已转发到单个主机仅路由广告暂存测试的目的。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-452">Set up ExpressRoute with Microsoft peering and have the route advertisements forwarded to a single host only for staged testing purposes.</span></span>

2. <span data-ttu-id="bd8c8-453">公布到单个网络段最初 ExpressRoute 网络的路由，展开路由广告网段或地区。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-453">Advertise routes to the ExpressRoute network to a single network segment at first and expand route advertisements by network segment or region.</span></span>

3. <span data-ttu-id="bd8c8-454">如果首次部署 Office 365，用作试验 ExpressRoute 网络部署少量的人员。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-454">If deploying Office 365 for the first time, use the ExpressRoute network deployment as a pilot for a small number of people.</span></span>

4. <span data-ttu-id="bd8c8-455">如果使用代理服务器，或者可以配置测试 PAC 文件定向之前添加更多人加入 ExpressRoute 测试与反馈一个小数字。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-455">If using proxy servers, you can alternatively configure a test PAC file to direct a small number of people to ExpressRoute with testing and feedback before adding more.</span></span>

<span data-ttu-id="bd8c8-p154">实施计划应列出每个必须执行的部署过程或需要用于部署的网络配置的命令。网络中断时间时到达的所有更改从它们已事先编写编写的部署计划和对等方应进行都审阅。在技术 ExpressRoute 的配置，请参阅我们指南。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p154">Your implementation plan should list each of the deployment procedures that must be taken or commands that need to be used to deploy the networking configuration. When the network outage time arrives all of the changes being made should be from the written deployment plan which was written in advance and peer reviewed. See our guidance on the technical configuration of ExpressRoute.</span></span>
  
- <span data-ttu-id="bd8c8-459">如果您已经更改发送电子邮件将继续任何本地服务器的 IP 地址，更新您的 SPF TXT 记录。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-459">Updating your SPF TXT records if you've changed IP addresses for any on-premises servers that will continue to send email.</span></span>

- <span data-ttu-id="bd8c8-460">如果您已经更改 IP 地址，以容纳新的 NAT 配置，更新的内部服务器的任何 DNS 条目。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-460">Updating any DNS entries for on-premises servers if you've changed IP addresses to accommodate a new NAT configuration.</span></span>

- <span data-ttu-id="bd8c8-461">确保您已订阅 RSS 源获取 Office 365 终结点通知，以维护任何路由或代理的配置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-461">Ensure you've subscribed to the RSS feed for Office 365 endpoint notifications to maintain any routing or proxy configurations.</span></span>

<span data-ttu-id="bd8c8-p155">ExpressRoute 部署完毕后应执行的测试计划中的过程。应记录的每个步骤的结果。您必须包含在事件的测试计划结果指示实现未成功回滚到原始生产环境的过程。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p155">After your ExpressRoute deployment is complete the procedures in the test plan should be executed. Results for each procedure should be logged. You must include procedures for rolling back to the original production environment in the event the test plan results indicate the implementation was not successful.</span></span>
  
### <a name="build-your-test-procedures"></a><span data-ttu-id="bd8c8-465">构建您的测试过程</span><span class="sxs-lookup"><span data-stu-id="bd8c8-465">Build your test procedures</span></span>

<span data-ttu-id="bd8c8-p156">您的测试过程应包括用于 Office 365 的每个将使用 ExpressRoute 的出站和入站网络服务和那些将不会测试。这些过程应包括测试从包括用户不是内部企业 LAN 中每个唯一的网络位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p156">Your testing procedures should include tests for each outbound and inbound network service for Office 365 both that will be using ExpressRoute and ones that will not. The procedures should include testing from each unique network location including users who are not on-premises in the corporate LAN.</span></span>
  
<span data-ttu-id="bd8c8-468">测试活动的一些示例包括以下。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-468">Some examples of test activities include the following.</span></span>
  
1. <span data-ttu-id="bd8c8-469">从本地路由器 ping 到网络运算符路由器。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-469">Ping from your on-premises router to your network operator router.</span></span>

2. <span data-ttu-id="bd8c8-470">验证 500 + Office 365 和 CRM Online IP 地址广告都会收到您的本地路由器的。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-470">Validate the 500+ Office 365 and CRM Online IP address advertisements are received by your on-premises router.</span></span>

3. <span data-ttu-id="bd8c8-471">验证您入站和出站 NAT 操作系统 ExpressRoute 与内部网络之间。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-471">Validate your inbound and outbound NAT is operating between ExpressRoute and the internal network.</span></span>

4. <span data-ttu-id="bd8c8-472">验证正在从路由器公布路由到您的 NAT。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-472">Validate that routes to your NAT are being advertised from your router.</span></span>

5. <span data-ttu-id="bd8c8-473">验证 ExpressRoute 已接受您播发的前缀。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-473">Validate that ExpressRoute has accepted your advertised prefixes.</span></span>

      - <span data-ttu-id="bd8c8-474">使用以下 cmdlet 来验证对等广告：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-474">Use the following cmdlet to verify peering advertisements:</span></span>

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. <span data-ttu-id="bd8c8-475">验证您公共的 NAT IP 范围不播发到任何其他 ExpressRoute 或公共 Internet 网络电路通过 Microsoft，除非它是特定与前面的示例更大范围的子集。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-475">Validate your public NAT IP range is not advertised to Microsoft through any other ExpressRoute or public Internet network circuit unless it is a specific subset of a larger range as in the previous example.</span></span>

7. <span data-ttu-id="bd8c8-476">ExpressRoute 电路配对，验证这两个 BGP 会话正在运行。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-476">ExpressRoute circuits are paired, validate that both BGP sessions are running.</span></span>

8. <span data-ttu-id="bd8c8-p157">设置您的 NAT 内部的单个主机，并使用 ping、 tracert 和 tcpping 跨主机 outlook.office365.com 使新电路测试连接。或者，您可以使用 Wireshark 之类的工具或 MSEE 来验证您为镜像端口上的 Microsoft 网络监视器 3.4 是能够连接到与 outlook.office365.com 关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p157">Set up a single host on the inside of your NAT and use ping, tracert, and tcpping to test connectivity across the new circuit to the host outlook.office365.com. Alternatively, you could use a tool such as Wireshark or Microsoft Network Monitor 3.4 on a mirrored port to the MSEE to validate you're able to connect to the IP address associated with outlook.office365.com.</span></span>

9. <span data-ttu-id="bd8c8-479">Exchange Online 的测试应用程序级别功能。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-479">Test application level functionality for Exchange Online.</span></span>

  - <span data-ttu-id="bd8c8-480">测试 Outlook 是能够连接到 Exchange Online 和发送/接收电子邮件。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-480">Test Outlook is able to connect to Exchange Online and send/receive email.</span></span>

  - <span data-ttu-id="bd8c8-481">测试 Outlook 是能够使用联机模式。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-481">Test Outlook is able to use online-mode.</span></span>

  - <span data-ttu-id="bd8c8-482">测试智能手机连接和发送/接收功能。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-482">Test smartphone connectivity and send/receive capability.</span></span>

10. <span data-ttu-id="bd8c8-483">SharePoint online 测试应用程序级别功能</span><span class="sxs-lookup"><span data-stu-id="bd8c8-483">Test application level functionality for SharePoint Online</span></span>

  - <span data-ttu-id="bd8c8-484">测试 OneDrive for Business 同步客户端。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-484">Test OneDrive for Business sync client.</span></span>

  - <span data-ttu-id="bd8c8-485">测试 SharePoint Online web 访问。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-485">Test SharePoint Online web access.</span></span>

11. <span data-ttu-id="bd8c8-486">测试应用程序级别功能的 Skype 商业调用应用场景：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-486">Test application level functionality for Skype for Business calling scenarios:</span></span>

  - <span data-ttu-id="bd8c8-487">作为经过身份验证的用户 [由最终用户的邀请] 加入电话会议。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-487">Join to conference call as authenticated user [invite initiated by end user].</span></span>

  - <span data-ttu-id="bd8c8-488">邀请用户加入电话会议 [从 MCU 发送邀请]。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-488">Invite user to conference call [invite sent from MCU].</span></span>

  - <span data-ttu-id="bd8c8-489">为业务 web 应用程序使用 Skype 的匿名用户加入会议。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-489">Join conference as anonymous user using the Skype for Business web application.</span></span>

  - <span data-ttu-id="bd8c8-490">加入从有线的 PC 连接、 IP 电话和移动设备的呼叫。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-490">Join call from your wired PC connection, IP phone, and mobile device.</span></span>

  - <span data-ttu-id="bd8c8-491">对联盟的用户呼叫 PSTN 验证 o 调用： 完成呼叫，呼叫质量是可接受，是可接受的连接时间。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-491">Call to federated user o Call to PSTN Validation: call is completed, call quality is acceptable, connection time is acceptable.</span></span>

  - <span data-ttu-id="bd8c8-492">验证联系人的状态更新租户的两个成员和联盟用户。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-492">Verify presence status for contacts is updated for both members of the tenant and federated users.</span></span>

### <a name="common-problems"></a><span data-ttu-id="bd8c8-493">常见问题</span><span class="sxs-lookup"><span data-stu-id="bd8c8-493">Common problems</span></span>

<span data-ttu-id="bd8c8-p158">不对称路由是最常见的实现问题。下面是一些常见的源，以查找：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p158">Asymmetric routing is the most common implementation problem. Here are some common sources to look for:</span></span>
  
- <span data-ttu-id="bd8c8-496">使用源就地 NAT 的情况下打开或平面网络路由拓扑。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-496">Using an open or flat network routing topology without source NAT in place.</span></span>

- <span data-ttu-id="bd8c8-497">未使用 SNAT 可将路由到入站服务通过 internet 和 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-497">Not using SNAT to route to inbound services through both the internet and ExpressRoute connections.</span></span>

- <span data-ttu-id="bd8c8-498">不测试 ExpressRoute 在广泛部署之前测试网络上的入站的服务。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-498">Not testing inbound services on ExpressRoute on a test network prior to deploying broadly.</span></span>

## <a name="deploying-expressroute-connectivity-through-your-network"></a><span data-ttu-id="bd8c8-499">通过您的网络的部署 ExpressRoute 连接</span><span class="sxs-lookup"><span data-stu-id="bd8c8-499">Deploying ExpressRoute connectivity through your network</span></span>
<span data-ttu-id="bd8c8-500"><a name="testing"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-500"></span></span>

<span data-ttu-id="bd8c8-p159">阶段部署到一个网络段逐渐推出连接到提供计划，可以回滚的每个新的网络段网络的其他部分，一次。如果您的部署与 Office 365 部署，首先部署到您的 Office 365 试生产用户，并从那里扩展。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p159">Stage your deployment to one segment of the network at a time, progressively rolling out the connectivity to different parts of the network with a plan to roll back for each new network segment. If your deployment is aligned with an Office 365 deployment, deploy to your Office 365 pilot users first and extend from there.</span></span>
  
<span data-ttu-id="bd8c8-503">首先为测试然后对生产的：</span><span class="sxs-lookup"><span data-stu-id="bd8c8-503">First for your test and then for production:</span></span>
  
- <span data-ttu-id="bd8c8-504">运行启用 ExpressRoute 的部署步骤。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-504">Run the deployment steps to enable ExpressRoute.</span></span>

- <span data-ttu-id="bd8c8-505">测试您看到的网络路由符合预期。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-505">Test your seeing the network routes are as expected.</span></span>

- <span data-ttu-id="bd8c8-506">执行测试在每个入站和出站服务。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-506">Perform testing on each inbound and outbound service.</span></span>

- <span data-ttu-id="bd8c8-507">回滚： 如果您发现任何问题。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-507">Rollback if you discover any issues.</span></span>

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a><span data-ttu-id="bd8c8-508">设置与 ExpressRoute 带测试网络段的测试连接</span><span class="sxs-lookup"><span data-stu-id="bd8c8-508">Set up a test connection to ExpressRoute with a test network segment</span></span>

<span data-ttu-id="bd8c8-p160">既然您已经纸张上的已完成的 plan 就可以在小型测试。在此测试将您的本地网络上建立与 Microsoft Peering 到测试子网的单个 ExpressRoute 连接。可连接到测试子网与配置[试用 Office 365 租户](https://go.microsoft.com/fwlink/p/?LinkID=403802)和生产环境中测试子网中包含您将使用的所有出站和入站服务。设置 DNS 的测试网络段，并建立所有入站和出站服务。执行测试计划，并确保您熟悉的每个服务和路由传播路由。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p160">Now that you have the completed plan on paper it is time to test at a small scale. In this test you will establish a single ExpressRoute connection with Microsoft Peering to a test subnet on your on-premises network. You can configure a [trial Office 365 tenant](https://go.microsoft.com/fwlink/p/?LinkID=403802) with connectivity to and from the test subnet and include all outbound and inbound services that you will be using in production in the test subnet. Set up DNS for the test network segment and establish all inbound and outbound services. Execute your test plan and ensure that you are familiar with the routing for each service and the route propagation.</span></span>
  
### <a name="execute-the-deployment-and-test-plans"></a><span data-ttu-id="bd8c8-514">执行部署和测试计划</span><span class="sxs-lookup"><span data-stu-id="bd8c8-514">Execute the deployment and test plans</span></span>

<span data-ttu-id="bd8c8-515">在完成上述的项目，检查关闭区域已完成并确保您和您的团队检查它们之前执行您的部署和测试计划。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-515">As you complete the items described above, check off the areas you've completed and ensure you and your team have reviewed them before executing your deployment and testing plans.</span></span>
  
- <span data-ttu-id="bd8c8-516">出站和入站网络更改所涉及的服务列表。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-516">List of outbound and inbound services that are involved in the network change.</span></span>

- <span data-ttu-id="bd8c8-517">显示 internet 出口和 ExpressRoute 开会全局网络体系结构图示-我的位置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-517">Global network architecture diagram showing both internet egress and ExpressRoute meet-me locations.</span></span>

- <span data-ttu-id="bd8c8-518">网络路由图演示用于部署每个服务的不同的网络路径。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-518">Network routing diagram demonstrating the different network paths used for each service deployed.</span></span>

- <span data-ttu-id="bd8c8-519">如果需要实现的更改和回滚步骤部署计划。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-519">A deployment plan with steps to implement the changes and rollback if needed.</span></span>

- <span data-ttu-id="bd8c8-520">测试每个 Office 365 和网络服务测试计划。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-520">A test plan for testing each Office 365 and network service.</span></span>

- <span data-ttu-id="bd8c8-521">完成的入站和出站服务的生产路由的纸张验证。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-521">Completed paper validation of production routes for inbound and outbound services.</span></span>

- <span data-ttu-id="bd8c8-522">已完成的测试跨测试网络段，包括可用性测试。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-522">A completed test across a test network segment including availability testing.</span></span>

<span data-ttu-id="bd8c8-523">选择中断窗口足够长，若要运行的整个部署规划和测试计划，有一些时间可用于故障排除和滚动回去所需的时间。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-523">Choose an outage window that is long enough to run through the entire deployment plan and the test plan, has some time available for troubleshooting and time for rolling back if required.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="bd8c8-524">由于路由通过 internet 和 ExpressRoute 的复杂性质，建议您使用其他缓冲区时间被添加到此窗口以处理复杂路由的疑难解答。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-524">Due to the complex nature of routing over both the internet and ExpressRoute, it is recommended that additional buffer time is added to this window to handle troubleshooting complex routing.</span></span>
  
### <a name="configure-qos-for-skype-for-business-online"></a><span data-ttu-id="bd8c8-525">配置 QoS 的 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="bd8c8-525">Configure QoS for Skype for Business Online</span></span>

<span data-ttu-id="bd8c8-p161">QoS 所需业务 online Skype 获取语音和会议的好处。确保，ExpressRoute 网络连接不会阻止您其他 Office 365 服务访问的任何后，您可以配置 QoS。[ExpressRoute 和 Skype 业务 online 中的 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)一文中介绍了 QoS 的配置。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p161">QoS is necessary to obtain voice and meeting benefits for Skype for Business Online. You can configure QoS after you have ensured that the ExpressRoute network connection does not block any of your other Office 365 service access. Configuration for QoS is described in the article [ExpressRoute and QoS in Skype for Business Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) .</span></span>
  
## <a name="troubleshooting-your-implementation"></a><span data-ttu-id="bd8c8-529">有关您实现的疑难解答</span><span class="sxs-lookup"><span data-stu-id="bd8c8-529">Troubleshooting your implementation</span></span>
<span data-ttu-id="bd8c8-530"><a name="troubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="bd8c8-530"></span></span>

<span data-ttu-id="bd8c8-p162">查找的第一个位置是实现此指南中的步骤在任何已实施计划中的已错过？返回并运行进一步测试如果可能，以复制错误并对其进行调试的小型网络。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p162">The first place to look is at the steps in this implementation guide, were any missed in your implementation plan? Go back and run further small network testing if possible to replicate the error and debug it there.</span></span>
  
<span data-ttu-id="bd8c8-p163">确定哪些入站或出站测试过程中失败的服务。失败的服务的每个获取专门的 IP 地址和子网。继续操作和引导纸张上的网络拓扑图，并验证路由。验证专门其中 ExpressRoute 路由播发到、 测试该路由中断期间如果可能与跟踪。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p163">Identify which inbound or outbound services failed during testing. Get specifically the IP addresses and subnets for each of the services which failed. Go ahead and walk the network topology diagram on paper and validate the routing. Validate specifically where the ExpressRoute routing is advertised to, Test that routing during the outage if possible with traces.</span></span>
  
<span data-ttu-id="bd8c8-p164">运行 PSPing 网络跟踪向每个客户终结点和评估验证它们按预期的源和目标 IP 地址。运行任何邮件主机端口 25 上公开并确认 SNAT 隐藏的原始源 IP 地址，是否这预期的 telnet。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p164">Run PSPing with a network trace to each customer endpoint and evaluate source and destination IP addresses to validate that they are as expected. Run telnet to any mail host that you expose on port 25 and verify that SNAT is hiding the original source IP address if this is expected.</span></span>
  
<span data-ttu-id="bd8c8-p165">请记住，您需要确保 ExpressRoute 的网络配置的 ExpressRoute 连接部署 Office 365 时优化设计和您已也优化网络如客户端计算机上的其他组件。除了使用本规划指南解决您可能错过的步骤，我们还具有写入[性能疑难解答 for Office 365 的计划](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c)。</span><span class="sxs-lookup"><span data-stu-id="bd8c8-p165">Keep in mind that while deploying Office 365 with an ExpressRoute connection you'll need to ensure both the network configuration for ExpressRoute is optimally designed and you've also optimized the other components on your network such as client computers. In addition to using this planning guide to troubleshoot the steps you may have missed, we also have written a [Performance troubleshooting plan for Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .</span></span>
  
<span data-ttu-id="bd8c8-541">这是一个简短的链接，您可以使用回来：[https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)</span><span class="sxs-lookup"><span data-stu-id="bd8c8-541">Here's a short link you can use to come back: [https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="bd8c8-542">相关主题</span><span class="sxs-lookup"><span data-stu-id="bd8c8-542">Related Topics</span></span>

[<span data-ttu-id="bd8c8-543">与 Office 365 的网络连接</span><span class="sxs-lookup"><span data-stu-id="bd8c8-543">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="bd8c8-544">适用于 Office 365 的 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bd8c8-544">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
  
[<span data-ttu-id="bd8c8-545">管理 ExpressRoute for Office 365 连接</span><span class="sxs-lookup"><span data-stu-id="bd8c8-545">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="bd8c8-546">ExpressRoute for Office 365 路由</span><span class="sxs-lookup"><span data-stu-id="bd8c8-546">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
  
[<span data-ttu-id="bd8c8-547">ExpressRoute for Office 365 网络规划</span><span class="sxs-lookup"><span data-stu-id="bd8c8-547">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
  
[<span data-ttu-id="bd8c8-548">使用 Office 365 方案 (preview) 中 ExpressRoute BGP 社区 （英文）</span><span class="sxs-lookup"><span data-stu-id="bd8c8-548">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)
  
[<span data-ttu-id="bd8c8-549">媒体质量和 Skype 中的网络连接性能 for Business 联机</span><span class="sxs-lookup"><span data-stu-id="bd8c8-549">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="bd8c8-550">为业务 Online 的 Skype 优化您的网络</span><span class="sxs-lookup"><span data-stu-id="bd8c8-550">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[<span data-ttu-id="bd8c8-551">ExpressRoute 和 Skype for Business Online 中的 QoS</span><span class="sxs-lookup"><span data-stu-id="bd8c8-551">ExpressRoute and QoS in Skype for Business Online</span></span>](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[<span data-ttu-id="bd8c8-552">使用 ExpressRoute 呼叫流</span><span class="sxs-lookup"><span data-stu-id="bd8c8-552">Call flow using ExpressRoute</span></span>](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[<span data-ttu-id="bd8c8-553">使用基线和性能历史记录优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="bd8c8-553">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="bd8c8-554">Office 365 的性能疑难解答计划</span><span class="sxs-lookup"><span data-stu-id="bd8c8-554">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
  
[<span data-ttu-id="bd8c8-555">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="bd8c8-555">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="bd8c8-556">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="bd8c8-556">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
