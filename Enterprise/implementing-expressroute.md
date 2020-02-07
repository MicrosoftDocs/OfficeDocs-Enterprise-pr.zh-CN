---
title: 实现适用于 Office 365 的 ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: 适用于 Office 365 的 ExpressRoute 提供了到多个面向 internet 的 Office 365 服务的备用路由路径。 适用于 Office 365 的 ExpressRoute 体系结构基于 Office 365 服务的广告公共 IP 前缀，这些前缀已在 Internet 上可通过 Internet 访问，以便随后将这些 IP 前缀再分发到你的网络。 通过 ExpressRoute，可以有效地通过 internet 和 ExpressRoute 为许多 Office 365 服务启用几种不同的路由路径。 你的网络上的路由状态可能会对你的内部网络拓扑的设计进行重大更改。
ms.openlocfilehash: 63d7c887f9900250a81fe1428d8b5b5cd3df9b81
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840179"
---
# <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="a5191-106">实现适用于 Office 365 的 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="a5191-106">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="a5191-107">*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="a5191-107">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="a5191-108">适用于 Office 365 的 ExpressRoute 提供了到多个面向 internet 的 Office 365 服务的备用路由路径。</span><span class="sxs-lookup"><span data-stu-id="a5191-108">ExpressRoute for Office 365 provides an alternate routing path to many internet facing Office 365 services.</span></span> <span data-ttu-id="a5191-109">适用于 Office 365 的 ExpressRoute 体系结构基于 Office 365 服务的广告公共 IP 前缀，这些前缀已在 Internet 上可通过 Internet 访问，以便随后将这些 IP 前缀再分发到你的网络。</span><span class="sxs-lookup"><span data-stu-id="a5191-109">The architecture of ExpressRoute for Office 365 is based on advertising public IP prefixes of Office 365 services that are already accessible over the Internet into your provisioned ExpressRoute circuits for subsequent redistribution of those IP prefixes into your network.</span></span> <span data-ttu-id="a5191-110">通过 ExpressRoute，可以有效地通过 internet 和 ExpressRoute 为许多 Office 365 服务启用几种不同的路由路径。</span><span class="sxs-lookup"><span data-stu-id="a5191-110">With ExpressRoute you effectively enable several different routing paths, through the internet and through ExpressRoute, for many Office 365 services.</span></span> <span data-ttu-id="a5191-111">你的网络上的路由状态可能会对你的内部网络拓扑的设计进行重大更改。</span><span class="sxs-lookup"><span data-stu-id="a5191-111">This state of routing on your network may represent a significant change to how your internal network topology is designed.</span></span>
  
 <span data-ttu-id="a5191-112">**状态：** 完整指南 v2</span><span class="sxs-lookup"><span data-stu-id="a5191-112">**Status:** Complete Guide v2</span></span>
  
<span data-ttu-id="a5191-113">您必须仔细规划您的 ExpressRoute for Office 365 实施，以适应具有通过将路由插入到核心网络和 internet 的专用线路提供的网络复杂性。</span><span class="sxs-lookup"><span data-stu-id="a5191-113">You must carefully plan your ExpressRoute for Office 365 implementation to accommodate for the network complexities of having routing available via both a dedicated circuit with routes injected into your core network and the internet.</span></span> <span data-ttu-id="a5191-114">如果您和您的团队不在本指南中执行详细的规划和测试，则在启用 ExpressRoute 电路时，会有一个高风险，导致连接到 Office 365 服务的连接间歇或总丢失。</span><span class="sxs-lookup"><span data-stu-id="a5191-114">If you and your team don't perform the detailed planning and testing in this guide, there is a high risk you'll experience intermittent or a total loss of connectivity to Office 365 services when the ExpressRoute circuit is enabled.</span></span>
  
<span data-ttu-id="a5191-115">若要成功实施，您需要分析基础结构要求，了解详细的网络评估和设计，仔细规划部署并以暂存和控制的方式，并构建详细的验证和测试计划。</span><span class="sxs-lookup"><span data-stu-id="a5191-115">To have a successful implementation, you will need to analyze your infrastructure requirements, go through detailed network assessment and design, carefully plan the rollout in a staged and controlled manner, and build a detailed validation and testing plan.</span></span> <span data-ttu-id="a5191-116">对于大型的分布式环境，在几个月内查看实现情况并不常见。</span><span class="sxs-lookup"><span data-stu-id="a5191-116">For a large, distributed environment it's not uncommon to see implementations span several months.</span></span> <span data-ttu-id="a5191-117">本指南旨在帮助您提前进行规划。</span><span class="sxs-lookup"><span data-stu-id="a5191-117">This guide is designed to help you plan ahead.</span></span>
  
<span data-ttu-id="a5191-118">大型成功部署可能需要六个月进行规划，并且通常包含来自组织中的许多方面的团队成员，包括网络、防火墙和代理服务器管理员、Office 365 管理员、安全性、最终用户支持、项目管理和执行赞助。</span><span class="sxs-lookup"><span data-stu-id="a5191-118">Large successful deployments may take six months in planning and often include team members from many areas in the organization including networking, Firewall and Proxy server administrators, Office 365 administrators, security, end-user support, project management, and executive sponsorship.</span></span> <span data-ttu-id="a5191-119">您在规划过程中的投资将降低您在宕机或复杂且成本高昂的故障排除方面遇到部署故障的可能性。</span><span class="sxs-lookup"><span data-stu-id="a5191-119">Your investment in the planning process will reduce the likelihood that you'll experience deployment failures resulting in downtime or complex and expensive troubleshooting.</span></span>
  
<span data-ttu-id="a5191-120">在启动本实施指南之前，我们期望完成以下先决条件。</span><span class="sxs-lookup"><span data-stu-id="a5191-120">We expect the following pre-requisites to be completed before this implementation guide is started.</span></span>
  
1. <span data-ttu-id="a5191-121">你已完成网络评估，以确定是否建议并批准 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="a5191-121">You've completed a network assessment to determine if ExpressRoute is recommended and approved.</span></span>

2. <span data-ttu-id="a5191-122">您已选择 ExpressRoute 网络服务提供商。</span><span class="sxs-lookup"><span data-stu-id="a5191-122">You've selected an ExpressRoute network service provider.</span></span> <span data-ttu-id="a5191-123">查找有关[ExpressRoute 合作伙伴和对等位置](https://azure.microsoft.com/documentation/articles/expressroute-locations/)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a5191-123">Find details about the [ExpressRoute partners and peering locations](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span>

3. <span data-ttu-id="a5191-124">您已阅读并理解[expressroute 文档](https://azure.microsoft.com/documentation/services/expressroute/)，并且您的内部网络能够满足 expressroute 先决条件端到端。</span><span class="sxs-lookup"><span data-stu-id="a5191-124">You've already read and understand the [ExpressRoute documentation](https://azure.microsoft.com/documentation/services/expressroute/) and your internal network is able to meet ExpressRoute pre-requisites end to end.</span></span>

4. <span data-ttu-id="a5191-125">您的团队已阅读频道9上的所有公共指南[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)和[https://aka.ms/ert](https://aka.ms/ert)文档，并对[Azure ExpressRoute for Office 365 培训](https://channel9.msdn.com/series/aer)系列进行了跟踪，以了解关键技术详细信息，包括：</span><span class="sxs-lookup"><span data-stu-id="a5191-125">Your team has read all of the public guidance and documentation at [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365), [https://aka.ms/ert](https://aka.ms/ert), and watched the [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to gain an understanding of critical technical details including:</span></span>

      - <span data-ttu-id="a5191-126">SaaS 服务的 internet 依赖项。</span><span class="sxs-lookup"><span data-stu-id="a5191-126">The internet dependencies of SaaS services.</span></span>

      - <span data-ttu-id="a5191-127">如何避免非对称路由和处理复杂路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-127">How to avoid asymmetric routes and handle complex routing.</span></span>

      - <span data-ttu-id="a5191-128">如何合并外围安全、可用性和应用程序级别的控制。</span><span class="sxs-lookup"><span data-stu-id="a5191-128">How to incorporate perimeter security, availability, and application level controls.</span></span>

## <a name="begin-by-gathering-requirements"></a><span data-ttu-id="a5191-129">通过收集要求开始</span><span class="sxs-lookup"><span data-stu-id="a5191-129">Begin by gathering requirements</span></span>
<span data-ttu-id="a5191-130"><a name="requirements"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-130"><a name="requirements"> </a></span></span>

<span data-ttu-id="a5191-131">首先，确定您计划在组织中采用哪些功能和服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-131">Start by determining which features and services you plan to adopt within your organization.</span></span> <span data-ttu-id="a5191-132">您需要确定将使用不同的 Office 365 服务的功能以及网络上的哪些位置将使用这些功能承载用户。</span><span class="sxs-lookup"><span data-stu-id="a5191-132">You need to determine which features of the different Office 365 services will be used and which locations on your network will host people using those features.</span></span> <span data-ttu-id="a5191-133">在应用场景目录中，需要添加每个方案所需的网络属性;如入站和出站网络流量流，以及 Office 365 终结点是否可通过 ExpressRoute 使用。</span><span class="sxs-lookup"><span data-stu-id="a5191-133">With the catalog of scenarios, you need to add the network attributes that each of those scenarios require; such as inbound and outbound network traffic flows and if the Office 365 endpoints are available over ExpressRoute or not.</span></span>
  
<span data-ttu-id="a5191-134">若要收集组织的要求：</span><span class="sxs-lookup"><span data-stu-id="a5191-134">To gather your organization's requirements:</span></span>
  
- <span data-ttu-id="a5191-135">编录组织使用的 Office 365 服务的入站和出站网络流量。</span><span class="sxs-lookup"><span data-stu-id="a5191-135">Catalog the inbound and outbound network traffic for the Office 365 services your organization is using.</span></span> <span data-ttu-id="a5191-136">有关不同 Office 365 方案所需流的说明，请参阅 Office 365 Url 和 IP 地址范围页面。</span><span class="sxs-lookup"><span data-stu-id="a5191-136">Consult Office 365 URLs and IP address ranges page for the description of flows that different Office 365 scenarios require.</span></span>

- <span data-ttu-id="a5191-137">收集现有网络拓扑的文档，其中显示了内部 WAN 主干和拓扑的详细信息、卫星站点的连接、最后一次英里用户连接、路由到网络外围出口点和代理服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-137">Gather documentation of existing network topology showing details of your internal WAN backbone and topology, connectivity of satellite sites, last mile user connectivity, routing to network perimeter egress points, and proxy services.</span></span>

  - <span data-ttu-id="a5191-138">标识网络关系图上的入站服务终结点，Office 365 和其他 Microsoft 服务将连接到，同时显示 internet 和建议的 ExpressRoute 连接路径。</span><span class="sxs-lookup"><span data-stu-id="a5191-138">Identify inbound service endpoints on the network diagrams that Office 365 and other Microsoft services will connect to, showing both internet and proposed ExpressRoute connection paths.</span></span>

  - <span data-ttu-id="a5191-139">确定位置之间的所有地理位置用户位置和 WAN 连接，以及哪些位置当前有传出到 internet 以及哪些位置被建议将传出到 ExpressRoute 对等位置。</span><span class="sxs-lookup"><span data-stu-id="a5191-139">Identify all geographic user locations and WAN connectivity between locations along with which locations currently have an egress to the internet and which locations are proposed to have an egress to an ExpressRoute peering location.</span></span>

  - <span data-ttu-id="a5191-140">确定所有边缘设备（如代理、防火墙等），并将它们的关系编录为通过 Internet 和 ExpressRoute 传输的流。</span><span class="sxs-lookup"><span data-stu-id="a5191-140">Identify all edge devices, such as proxies, firewalls, and so on and catalog their relationship to flows going over the Internet and ExpressRoute.</span></span>

  - <span data-ttu-id="a5191-141">记录最终用户是否将通过直接路由或间接应用程序代理访问 Internet 和 ExpressRoute 流的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-141">Document whether end users will access Office 365 services via direct routing or indirect application proxy for both Internet and ExpressRoute flows.</span></span>

- <span data-ttu-id="a5191-142">将租户和 "满足我的位置" 位置添加到网络图中。</span><span class="sxs-lookup"><span data-stu-id="a5191-142">Add the location of your tenant and meet-me locations to your network diagram.</span></span>

- <span data-ttu-id="a5191-143">估计从主要用户位置到 Office 365 的预期和观测的网络性能和延迟特征。</span><span class="sxs-lookup"><span data-stu-id="a5191-143">Estimate the expected and observed network performance and latency characteristics from major user locations to Office 365.</span></span> <span data-ttu-id="a5191-144">请注意，Office 365 是一组全局的分布式服务，用户将连接到可能不同于其租户位置的位置。</span><span class="sxs-lookup"><span data-stu-id="a5191-144">Keep in mind that Office 365 is a global and distributed set of services and users will be connecting to locations that may be different from the location of their tenant.</span></span> <span data-ttu-id="a5191-145">出于此原因，建议使用 ExpressRoute 和 Internet 连接衡量和优化用户与 Microsoft 全局网络最接近的边缘之间的延迟。</span><span class="sxs-lookup"><span data-stu-id="a5191-145">For this reason, it is recommended to measure and optimize for latency between the user and the closest edge of Microsoft global network over ExpressRoute and Internet connections.</span></span> <span data-ttu-id="a5191-146">您可以使用网络评估中的发现来帮助执行此任务。</span><span class="sxs-lookup"><span data-stu-id="a5191-146">You can use your findings from the network assessment to aid with this task.</span></span>

- <span data-ttu-id="a5191-147">列出公司网络安全性和需要使用新的 ExpressRoute 连接所需满足的高可用性要求。</span><span class="sxs-lookup"><span data-stu-id="a5191-147">List company network security and high availability requirements that need to be met with the new ExpressRoute connection.</span></span> <span data-ttu-id="a5191-148">例如，在 Internet 出口或 ExpressRoute 电路故障发生时，用户如何继续获取 Office 365 的访问权限。</span><span class="sxs-lookup"><span data-stu-id="a5191-148">For example, how do users continue to get access to Office 365 in the event of the Internet egress or ExpressRoute circuit failure.</span></span>

- <span data-ttu-id="a5191-149">记录哪个入站和出站 Office 365 网络流将使用 Internet 路径，并将使用 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="a5191-149">Document which inbound and outbound Office 365 network flows will use the Internet path and which will use ExpressRoute.</span></span> <span data-ttu-id="a5191-150">你的用户的地理位置的具体信息以及你的本地网络拓扑的详细信息可能要求计划不同于一个用户位置。</span><span class="sxs-lookup"><span data-stu-id="a5191-150">The specifics of geographical locations of your users and details of your on-premises network topology may require the plan to be different from one user location to another.</span></span>

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a><span data-ttu-id="a5191-151">对出站和入站网络流量进行编目</span><span class="sxs-lookup"><span data-stu-id="a5191-151">Catalog your outbound and inbound network traffic</span></span>
<span data-ttu-id="a5191-152"><a name="trafficCatalog"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-152"><a name="trafficCatalog"> </a></span></span>

<span data-ttu-id="a5191-153">为了最大限度地减少路由和其他网络复杂性，我们建议您仅将 ExpressRoute 用于 Office 365，以实现由于法规要求或网络评估结果而需要通过专用连接的网络流量流。</span><span class="sxs-lookup"><span data-stu-id="a5191-153">To minimize routing and other network complexities, we recommend that you only use ExpressRoute for Office 365 for the network traffic flows that are required to go over a dedicated connection due to regulatory requirements or as the result of the network assessment.</span></span> <span data-ttu-id="a5191-154">此外，我们建议你暂存 ExpressRoute 路由的范围，并将出站和入站网络流量流作为实施项目的不同和不同阶段。</span><span class="sxs-lookup"><span data-stu-id="a5191-154">Additionally, we recommend that you stage the scope of ExpressRoute routing and approach outbound and inbound network traffic flows as different and distinct stages of the implementation project.</span></span> <span data-ttu-id="a5191-155">部署适用于 Office 365 的 ExpressRoute 仅供用户启动的出站网络流量流并在 Internet 中留下入站网络流量流，可帮助控制拓扑复杂性和引入额外的非对称的风险增加路由可能性。</span><span class="sxs-lookup"><span data-stu-id="a5191-155">Deploy ExpressRoute for Office 365 for just user initiated outbound network traffic flows and leave inbound network traffic flows across the Internet can help to control the increase in topological complexity and risks of introducing additional asymmetric routing possibilities.</span></span>
  
<span data-ttu-id="a5191-156">您的网络流量目录应包含您在本地网络和 Microsoft 之间拥有的所有入站和出站网络连接的列表。</span><span class="sxs-lookup"><span data-stu-id="a5191-156">Your network traffic catalog should contain listings of all the inbound and outbound network connections that you'll have between your on-premises network and Microsoft.</span></span>
  
- <span data-ttu-id="a5191-157">出站网络流量流是从本地环境（如内部客户端或服务器）使用 Microsoft 服务的目标启动连接的任何场景。</span><span class="sxs-lookup"><span data-stu-id="a5191-157">Outbound network traffic flows are any scenarios where a connection is initiated from your on-premises environment, such as from internal clients or servers, with a destination of the Microsoft services.</span></span> <span data-ttu-id="a5191-158">这些连接可以直接连接到 Office 365 或间接，例如当连接通过代理服务器、防火墙或指向 Office 365 的路径上的其他网络设备时。</span><span class="sxs-lookup"><span data-stu-id="a5191-158">These connections may be direct to Office 365 or indirect, such as when the connection goes through proxy servers, firewalls, or other networking devices on the path to Office 365.</span></span>

- <span data-ttu-id="a5191-159">入站网络流量流是从 Microsoft 云中启动到本地主机的连接的任何场景。</span><span class="sxs-lookup"><span data-stu-id="a5191-159">Inbound network traffic flows are any scenarios where a connection is initiated from the Microsoft cloud to an on-premises host.</span></span> <span data-ttu-id="a5191-160">这些连接通常需要经过防火墙和其他安全基础结构，客户安全策略需要针对外部发起的流。</span><span class="sxs-lookup"><span data-stu-id="a5191-160">These connections typically need to go through firewall and other security infrastructure that customer security policy requires for externally originated flows.</span></span>

<span data-ttu-id="a5191-161">阅读 "确保在 Office 365 终结点参考" [365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)一文中的 "确保哪些服务将发送入站流量" 和 "在[office 终结点](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)参考" 一文中查找标记**为 "ExpressRoute for Office 365** " 的列的 "**确保路由的路由**" 部分，以确定其他连接信息。</span><span class="sxs-lookup"><span data-stu-id="a5191-161">Read the **Ensuring route symmetry** section of the article [Routing with ExpressRoute for Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) to determine which services will send inbound traffic and look for the column marked **ExpressRoute for Office 365** in the [Office 365 endpoints](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) reference article to determine the rest of the connectivity information.</span></span>
  
<span data-ttu-id="a5191-162">对于每个需要出站连接的服务，您需要描述服务的计划连接，包括网络路由、代理配置、数据包检查和带宽需求。</span><span class="sxs-lookup"><span data-stu-id="a5191-162">For each service that requires an outbound connection, you'll want to describe the planned connectivity for the service including network routing, proxy configuration, packet inspection, and bandwidth needs.</span></span>
  
<span data-ttu-id="a5191-163">对于每个需要入站连接的服务，您都需要一些其他信息。</span><span class="sxs-lookup"><span data-stu-id="a5191-163">For each service that requires an inbound connection, you'll need some additional information.</span></span> <span data-ttu-id="a5191-164">Microsoft 云中的服务器将建立与您的本地网络的连接。</span><span class="sxs-lookup"><span data-stu-id="a5191-164">Servers in the Microsoft cloud will establish connections to your on-premises network.</span></span> <span data-ttu-id="a5191-165">若要确保正确建立了连接，您需要描述此连接的各个方面，包括;将接受这些入站连接的服务的公共 DNS 条目、CIDR 格式的 IPv4 IP 地址、涉及的 ISP 设备以及如何处理这些连接的入站 NAT 或源 NAT。</span><span class="sxs-lookup"><span data-stu-id="a5191-165">to ensure the connections are made correctly, you'll want to describe all aspects of this connectivity, including; the public DNS entries for the services that will accept these inbound connections, the CIDR formatted IPv4 IP addresses, which ISP equipment is involved, and how inbound NAT or source NAT is handled for these connections.</span></span>
  
<span data-ttu-id="a5191-166">无论是通过 internet 还是 ExpressRoute 连接入站连接，以确保未引入非对称路由，应查看入站连接。</span><span class="sxs-lookup"><span data-stu-id="a5191-166">Inbound connections should be reviewed regardless of whether they're connecting over the internet or ExpressRoute to ensure asymmetric routing hasn't been introduced.</span></span> <span data-ttu-id="a5191-167">在某些情况下，Office 365 服务启动入站连接的本地终结点可能还需要由其他 Microsoft 和非 Microsoft 服务访问。</span><span class="sxs-lookup"><span data-stu-id="a5191-167">In some cases, on-premises endpoints that Office 365 services initiate inbound connections to may also need to be accessed by other Microsoft and non-Microsoft services.</span></span> <span data-ttu-id="a5191-168">为实现针对 Office 365 的这些服务的 ExpressRoute 路由不会中断其他方案，这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="a5191-168">It is paramount that enabling ExpressRoute routing to these services for Office 365 purposes doesn't break other scenarios.</span></span> <span data-ttu-id="a5191-169">在许多情况下，客户可能需要对内部网络（如基于源的 NAT）实施特定的更改，以确保启用 ExpressRoute 后来自 Microsoft 的入站流仍保持对称。</span><span class="sxs-lookup"><span data-stu-id="a5191-169">In many cases, customers may need to implement specific changes to their internal network, such as source based NAT, to ensure that inbound flows from Microsoft remain symmetric after ExpressRoute is enabled.</span></span>
  
<span data-ttu-id="a5191-170">下面的示例展示了所需的详细信息级别。</span><span class="sxs-lookup"><span data-stu-id="a5191-170">Here's a sample of the level of detail required.</span></span> <span data-ttu-id="a5191-171">在这种情况下，Exchange 混合将通过 ExpressRoute 路由到内部部署系统。</span><span class="sxs-lookup"><span data-stu-id="a5191-171">In this case Exchange Hybrid would route to the on-premises system over ExpressRoute.</span></span>

|<span data-ttu-id="a5191-172">**Connection 属性**</span><span class="sxs-lookup"><span data-stu-id="a5191-172">**Connection property**</span></span>|<span data-ttu-id="a5191-173">**值**</span><span class="sxs-lookup"><span data-stu-id="a5191-173">**Value**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a5191-174">**网络流量方向**</span><span class="sxs-lookup"><span data-stu-id="a5191-174">**Network traffic direction**</span></span> <br/> |<span data-ttu-id="a5191-175">进货</span><span class="sxs-lookup"><span data-stu-id="a5191-175">Inbound</span></span>  <br/> |
|<span data-ttu-id="a5191-176">**服务**</span><span class="sxs-lookup"><span data-stu-id="a5191-176">**Service**</span></span> <br/> |<span data-ttu-id="a5191-177">Exchange 混合</span><span class="sxs-lookup"><span data-stu-id="a5191-177">Exchange Hybrid</span></span>  <br/> |
|<span data-ttu-id="a5191-178">**公共 Office 365 终结点（源）**</span><span class="sxs-lookup"><span data-stu-id="a5191-178">**Public Office 365 endpoint (source)**</span></span> <br/> |<span data-ttu-id="a5191-179">Exchange Online （IP 地址）</span><span class="sxs-lookup"><span data-stu-id="a5191-179">Exchange Online (IP addresses)</span></span>  <br/> |
|<span data-ttu-id="a5191-180">**公共本地终结点（目标）**</span><span class="sxs-lookup"><span data-stu-id="a5191-180">**Public On-Premises Endpoint (destination)**</span></span> <br/> |<span data-ttu-id="a5191-181">5.5.5.5</span><span class="sxs-lookup"><span data-stu-id="a5191-181">5.5.5.5</span></span>  <br/> |
|<span data-ttu-id="a5191-182">**公用（Internet） DNS 条目**</span><span class="sxs-lookup"><span data-stu-id="a5191-182">**Public (Internet) DNS entry**</span></span> <br/> |<span data-ttu-id="a5191-183">Autodiscover.contoso.com</span><span class="sxs-lookup"><span data-stu-id="a5191-183">Autodiscover.contoso.com</span></span>  <br/> |
|<span data-ttu-id="a5191-184">**此本地终结点是否适用于其他（非 Office 365） Microsoft 服务**</span><span class="sxs-lookup"><span data-stu-id="a5191-184">**Will this on-premises endpoint be used for by other (non-Office 365) Microsoft services**</span></span> <br/> |<span data-ttu-id="a5191-185">否</span><span class="sxs-lookup"><span data-stu-id="a5191-185">No</span></span>  <br/> |
|<span data-ttu-id="a5191-186">**Internet 上的用户/系统是否使用此本地终结点**</span><span class="sxs-lookup"><span data-stu-id="a5191-186">**Will this on-premises endpoint be used by users/systems on the Internet**</span></span> <br/> |<span data-ttu-id="a5191-187">是</span><span class="sxs-lookup"><span data-stu-id="a5191-187">Yes</span></span>  <br/> |
|<span data-ttu-id="a5191-188">**通过公用终结点发布的内部系统**</span><span class="sxs-lookup"><span data-stu-id="a5191-188">**Internal systems published through public endpoints**</span></span> <br/> |<span data-ttu-id="a5191-189">Exchange Server 客户端访问角色（本地）192.168.101、192.168.102、192.168.103</span><span class="sxs-lookup"><span data-stu-id="a5191-189">Exchange Server client access role (on-premises) 192.168.101, 192.168.102, 192.168.103</span></span>  <br/> |
|<span data-ttu-id="a5191-190">**公共终结点的 IP 广告**</span><span class="sxs-lookup"><span data-stu-id="a5191-190">**IP advertisement of the public endpoint**</span></span> <br/> |<span data-ttu-id="a5191-191">**到 Internet**： 5.5.0.0/16</span><span class="sxs-lookup"><span data-stu-id="a5191-191">**To Internet**: 5.5.0.0/16</span></span>  <br/> <span data-ttu-id="a5191-192">**到 ExpressRoute**： 5.5.5.0/24</span><span class="sxs-lookup"><span data-stu-id="a5191-192">**To ExpressRoute**: 5.5.5.0/24</span></span>  <br/> |
|<span data-ttu-id="a5191-193">**安全性/外围控件**</span><span class="sxs-lookup"><span data-stu-id="a5191-193">**Security/Perimeter Controls**</span></span> <br/> |<span data-ttu-id="a5191-194">**Internet 路径**： DeviceID_002</span><span class="sxs-lookup"><span data-stu-id="a5191-194">**Internet path**: DeviceID_002</span></span>  <br/> <span data-ttu-id="a5191-195">**ExpressRoute 路径**： DeviceID_003</span><span class="sxs-lookup"><span data-stu-id="a5191-195">**ExpressRoute path**: DeviceID_003</span></span>  <br/> |
|<span data-ttu-id="a5191-196">**高可用性**</span><span class="sxs-lookup"><span data-stu-id="a5191-196">**High Availability**</span></span> <br/> |<span data-ttu-id="a5191-197">跨2地域冗余的主动/主动</span><span class="sxs-lookup"><span data-stu-id="a5191-197">Active/Active across 2 geo-redundant</span></span>  <br/> <span data-ttu-id="a5191-198">ExpressRoute 电路-芝加哥和达拉斯</span><span class="sxs-lookup"><span data-stu-id="a5191-198">ExpressRoute circuits - Chicago and Dallas</span></span>  <br/> |
|<span data-ttu-id="a5191-199">**路径对称控制**</span><span class="sxs-lookup"><span data-stu-id="a5191-199">**Path symmetry control**</span></span> <br/> |<span data-ttu-id="a5191-200">**方法**：源 NAT</span><span class="sxs-lookup"><span data-stu-id="a5191-200">**Method**: Source NAT</span></span>  <br/> <span data-ttu-id="a5191-201">**Internet 路径**：源 NAT 到192.168.5.5 的入站连接</span><span class="sxs-lookup"><span data-stu-id="a5191-201">**Internet path**: Source NAT inbound connections to 192.168.5.5</span></span>  <br/> |<span data-ttu-id="a5191-202">**ExpressRoute 路径**：源 NAT 与192.168.1.0 （芝加哥）和192.168.2.0 （达拉斯）的连接</span><span class="sxs-lookup"><span data-stu-id="a5191-202">**ExpressRoute path**: Source NAT connections to 192.168.1.0 (Chicago) and 192.168.2.0 (Dallas)</span></span>  <br/> |

<span data-ttu-id="a5191-203">以下是仅出站的服务示例：</span><span class="sxs-lookup"><span data-stu-id="a5191-203">Here's a sample of a service that is outbound only:</span></span>

|<span data-ttu-id="a5191-204">**Connection 属性**</span><span class="sxs-lookup"><span data-stu-id="a5191-204">**Connection property**</span></span>|<span data-ttu-id="a5191-205">**值**</span><span class="sxs-lookup"><span data-stu-id="a5191-205">**Value**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a5191-206">**网络流量方向**</span><span class="sxs-lookup"><span data-stu-id="a5191-206">**Network traffic direction**</span></span> <br/> |<span data-ttu-id="a5191-207">出站</span><span class="sxs-lookup"><span data-stu-id="a5191-207">Outbound</span></span>  <br/> |
|<span data-ttu-id="a5191-208">**服务**</span><span class="sxs-lookup"><span data-stu-id="a5191-208">**Service**</span></span> <br/> |<span data-ttu-id="a5191-209">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a5191-209">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="a5191-210">**内部部署终结点（源）**</span><span class="sxs-lookup"><span data-stu-id="a5191-210">**On-premises endpoint (source)**</span></span> <br/> |<span data-ttu-id="a5191-211">用户工作站</span><span class="sxs-lookup"><span data-stu-id="a5191-211">User workstation</span></span>  <br/> |
|<span data-ttu-id="a5191-212">**公共 Office 365 终结点（目标）**</span><span class="sxs-lookup"><span data-stu-id="a5191-212">**Public Office 365 endpoint (destination)**</span></span> <br/> |<span data-ttu-id="a5191-213">SharePoint Online （IP 地址）</span><span class="sxs-lookup"><span data-stu-id="a5191-213">SharePoint Online (IP addresses)</span></span>  <br/> |
|<span data-ttu-id="a5191-214">**公用（Internet） DNS 条目**</span><span class="sxs-lookup"><span data-stu-id="a5191-214">**Public (Internet) DNS entry**</span></span> <br/> |<span data-ttu-id="a5191-215">\*. sharepoint.com （以及其他 Fqdn）</span><span class="sxs-lookup"><span data-stu-id="a5191-215">\*.sharepoint.com (and additional FQDNs)</span></span>  <br/> |
|<span data-ttu-id="a5191-216">**CDN 检索**</span><span class="sxs-lookup"><span data-stu-id="a5191-216">**CDN Referrals**</span></span> <br/> |<span data-ttu-id="a5191-217">cdn.sharepointonline.com （和其他 Fqdn）-由 CDN 提供程序维护的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="a5191-217">cdn.sharepointonline.com (and additional FQDNs) - IP addresses maintained by CDN providers)</span></span>  <br/> |
|<span data-ttu-id="a5191-218">**正在使用的 IP 播发和 NAT**</span><span class="sxs-lookup"><span data-stu-id="a5191-218">**IP advertisement and NAT in use**</span></span> <br/> |<span data-ttu-id="a5191-219">**Internet 路径/源 NAT**： 1.1.1.0/24</span><span class="sxs-lookup"><span data-stu-id="a5191-219">**Internet path/Source NAT**: 1.1.1.0/24</span></span>  <br/> <span data-ttu-id="a5191-220">**ExpressRoute 路径/源 NAT**： 1.1.2.0/24 （芝加哥）和 1.1.3.0/24 （达拉斯）</span><span class="sxs-lookup"><span data-stu-id="a5191-220">**ExpressRoute path/Source NAT**: 1.1.2.0/24 (Chicago) and 1.1.3.0/24 (Dallas)</span></span>  <br/> |
|<span data-ttu-id="a5191-221">**Connectivity 方法**</span><span class="sxs-lookup"><span data-stu-id="a5191-221">**Connectivity method**</span></span> <br/> |<span data-ttu-id="a5191-222">**Internet**： via 第7层代理（pac 文件）</span><span class="sxs-lookup"><span data-stu-id="a5191-222">**Internet**: via layer 7 proxy (.pac file)</span></span>  <br/> <span data-ttu-id="a5191-223">**ExpressRoute**：直接路由（无代理）</span><span class="sxs-lookup"><span data-stu-id="a5191-223">**ExpressRoute**: direct routing (no proxy)</span></span>  <br/> |
|<span data-ttu-id="a5191-224">**安全性/外围控件**</span><span class="sxs-lookup"><span data-stu-id="a5191-224">**Security/Perimeter Controls**</span></span> <br/> |<span data-ttu-id="a5191-225">**Internet 路径**： DeviceID_002</span><span class="sxs-lookup"><span data-stu-id="a5191-225">**Internet path**: DeviceID_002</span></span>  <br/> <span data-ttu-id="a5191-226">**ExpressRoute 路径**： DeviceID_003</span><span class="sxs-lookup"><span data-stu-id="a5191-226">**ExpressRoute path**: DeviceID_003</span></span>  <br/> |
|<span data-ttu-id="a5191-227">**高可用性**</span><span class="sxs-lookup"><span data-stu-id="a5191-227">**High Availability**</span></span> <br/> |<span data-ttu-id="a5191-228">**Internet 路径**：冗余 internet 出口</span><span class="sxs-lookup"><span data-stu-id="a5191-228">**Internet path**: Redundant internet egress</span></span>  <br/> <span data-ttu-id="a5191-229">**ExpressRoute 路径**：跨2个地理位置冗余的 expressroute 电路的主动/主动热刷路线-芝加哥和达拉斯</span><span class="sxs-lookup"><span data-stu-id="a5191-229">**ExpressRoute path**: Active/Active 'hot potato' routing across 2 geo-redundant ExpressRoute circuits - Chicago and Dallas</span></span>  <br/> |
|<span data-ttu-id="a5191-230">**路径对称控制**</span><span class="sxs-lookup"><span data-stu-id="a5191-230">**Path symmetry control**</span></span> <br/> |<span data-ttu-id="a5191-231">**方法**：源 NAT 用于所有连接</span><span class="sxs-lookup"><span data-stu-id="a5191-231">**Method**: Source NAT for all connections</span></span>  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a><span data-ttu-id="a5191-232">区域连接的网络拓扑设计</span><span class="sxs-lookup"><span data-stu-id="a5191-232">Your network topology design with regional connectivity</span></span>
<span data-ttu-id="a5191-233"><a name="topology"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-233"><a name="topology"> </a></span></span>

<span data-ttu-id="a5191-234">了解服务及其关联的网络流量流后，可以创建一个包含这些新的连接要求的网络图，并说明将对 Office 365 使用 ExpressRoute 所做的更改。</span><span class="sxs-lookup"><span data-stu-id="a5191-234">Once you understand the services and their associated network traffic flows, you can create a network diagram that incorporates these new connectivity requirements and illustrates the changes you'll make to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="a5191-235">您的图表应包括：</span><span class="sxs-lookup"><span data-stu-id="a5191-235">Your diagram should include:</span></span>
  
1. <span data-ttu-id="a5191-236">将从其访问 Office 365 和其他服务的所有用户位置。</span><span class="sxs-lookup"><span data-stu-id="a5191-236">All user locations where Office 365 and other services will be accessed from.</span></span>

2. <span data-ttu-id="a5191-237">所有 internet 和 ExpressRoute 出口点。</span><span class="sxs-lookup"><span data-stu-id="a5191-237">All internet and ExpressRoute egress points.</span></span>

3. <span data-ttu-id="a5191-238">管理网络中和外部连接的所有出站和入站设备，包括路由器、防火墙、应用程序代理服务器和入侵检测/预防。</span><span class="sxs-lookup"><span data-stu-id="a5191-238">All outbound and inbound devices that manage connectivity in and out of the network, including routers, firewalls, application proxy servers, and intrusion detection/prevention.</span></span>

4. <span data-ttu-id="a5191-239">所有入站流量的内部目标，例如接受来自 ADFS web 应用程序代理服务器的连接的内部 ADFS 服务器。</span><span class="sxs-lookup"><span data-stu-id="a5191-239">Internal destinations for all inbound traffic, such as internal ADFS servers that accept connections from the ADFS web application proxy servers.</span></span>

5. <span data-ttu-id="a5191-240">将公布的所有 IP 子网的目录</span><span class="sxs-lookup"><span data-stu-id="a5191-240">Catalog of all IP subnets that will be advertised</span></span>

6. <span data-ttu-id="a5191-241">确定用户将从其访问 Office 365 的每个位置，并列出将用于 ExpressRoute 的 "满足我" 的位置。</span><span class="sxs-lookup"><span data-stu-id="a5191-241">Identify each location where people will access Office 365 from and list the meet-me locations that will be used for ExpressRoute.</span></span>

7. <span data-ttu-id="a5191-242">内部网络拓扑的位置和部分，在其中将接受、筛选出从 ExpressRoute 获知的 Microsoft IP 前缀并将其传播到。</span><span class="sxs-lookup"><span data-stu-id="a5191-242">Locations and portions of your internal network topology, where Microsoft IP prefixes learned from ExpressRoute will be accepted, filtered and propagated to.</span></span>

8. <span data-ttu-id="a5191-243">网络拓扑应说明每个网段的地理位置以及它如何通过 ExpressRoute 和/或 Internet 连接到 Microsoft 网络。</span><span class="sxs-lookup"><span data-stu-id="a5191-243">The network topology should illustrate the geographic location of each network segment and how it connects to the Microsoft network over ExpressRoute and/or the Internet.</span></span>

<span data-ttu-id="a5191-244">下图显示了用户将使用 Office 365 的每个位置以及入站和出站路由播发到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="a5191-244">The diagram below shows each location where people will be using Office 365 from along with the inbound and outbound routing advertisements to Office 365.</span></span>
  
![ExpressRoute 区域地理位置会见](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
<span data-ttu-id="a5191-246">对于出站流量，人员通过以下三种方式之一访问 Office 365：</span><span class="sxs-lookup"><span data-stu-id="a5191-246">For outbound traffic, the people access Office 365 in one of three ways:</span></span>
  
1. <span data-ttu-id="a5191-247">通过北美地区的 "满足我的人员" 为加州的人员。</span><span class="sxs-lookup"><span data-stu-id="a5191-247">Through a meet-me location in North America for the people in California.</span></span>

2. <span data-ttu-id="a5191-248">通过中国香港地区的 "我的好友" 位置，为香港地区的人员。</span><span class="sxs-lookup"><span data-stu-id="a5191-248">Through a meet-me location in Hong Kong for the people in Hong Kong.</span></span>

3. <span data-ttu-id="a5191-249">在孟加拉的人较少，并且未预配 ExpressRoute 电路的情况下通过 internet。</span><span class="sxs-lookup"><span data-stu-id="a5191-249">Through the internet in Bangladesh where there are fewer people and no ExpressRoute circuit provisioned.</span></span>

![区域图的出站连接](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
<span data-ttu-id="a5191-251">同样，Office 365 中的入站网络流量通过以下三种方式之一返回：</span><span class="sxs-lookup"><span data-stu-id="a5191-251">Similarly, the inbound network traffic from Office 365 returns in one of three ways:</span></span>
  
1. <span data-ttu-id="a5191-252">通过北美地区的 "满足我的人员" 为加州的人员。</span><span class="sxs-lookup"><span data-stu-id="a5191-252">Through a meet-me location in North America for the people in California.</span></span>

2. <span data-ttu-id="a5191-253">通过中国香港地区的 "我的好友" 位置，为香港地区的人员。</span><span class="sxs-lookup"><span data-stu-id="a5191-253">Through a meet-me location in Hong Kong for the people in Hong Kong.</span></span>

3. <span data-ttu-id="a5191-254">在孟加拉的人较少，并且未预配 ExpressRoute 电路的情况下通过 internet。</span><span class="sxs-lookup"><span data-stu-id="a5191-254">Through the internet in Bangladesh where there are fewer people and no ExpressRoute circuit provisioned.</span></span>

![区域图的入站连接](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a><span data-ttu-id="a5191-256">确定适当的 "符合我的位置" 位置</span><span class="sxs-lookup"><span data-stu-id="a5191-256">Determine the appropriate meet-me location</span></span>

<span data-ttu-id="a5191-257">将您的 ExpressRoute 电路连接到 Microsoft 网络的位置的 "满足我的存储位置" 选择 "满足我的地理位置"，受用户从其访问 Office 365 的位置影响。</span><span class="sxs-lookup"><span data-stu-id="a5191-257">The selection of meet-me locations, which are the physical location where your ExpressRoute circuit connects your network to the Microsoft network, is influenced by the locations where people will access Office 365 from.</span></span> <span data-ttu-id="a5191-258">作为 SaaS 服务，Office 365 不在 IaaS 或 PaaS 区域模型下按照与 Azure 相同的方式运行。</span><span class="sxs-lookup"><span data-stu-id="a5191-258">As a SaaS offering, Office 365 does not operate under the IaaS or PaaS regional model in the same way Azure does.</span></span> <span data-ttu-id="a5191-259">相反，Office 365 是一组分布式服务，在其中用户可能需要连接到多个数据中心和地区的终结点，这可能不一定在承载用户租户的同一位置或区域中。</span><span class="sxs-lookup"><span data-stu-id="a5191-259">Instead, Office 365 is a distributed set of collaboration services, where users may need to connect to endpoints across multiple datacenters and regions, which may not necessarily be in the same location or region where the user's tenant is hosted.</span></span>
  
<span data-ttu-id="a5191-260">这意味着在为 Office 365 选择 "满足我的 ExpressRoute 的用户定位-我的位置" 时，您需要做的最重要的考虑事项是组织中的人员将从其进行连接。</span><span class="sxs-lookup"><span data-stu-id="a5191-260">This means the most important consideration you need to make when selecting meet-me locations for ExpressRoute for Office 365 is where the people in your organization will be connecting from.</span></span> <span data-ttu-id="a5191-261">最佳 Office 365 连接的一般建议是实现路由，以便通过最短网络路径将对 Office 365 服务的用户请求传递到 Microsoft 网络中，这通常也称为 "热刷" 路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-261">The general recommendation for optimal Office 365 connectivity is implement routing, so that user requests to Office 365 services are handed off into the Microsoft network over the shortest network path, this is also often being referred to as 'hot potato' routing.</span></span> <span data-ttu-id="a5191-262">例如，如果大多数 Office 365 用户位于一个或两个位置，则选择 "符合我的位置" 与这些用户的位置最接近的位置将创建最佳设计。</span><span class="sxs-lookup"><span data-stu-id="a5191-262">For example, if most of the Office 365 users are in one or two locations, selecting meet-me locations that are in the closest proximity to the location of those users will create the optimal design.</span></span> <span data-ttu-id="a5191-263">如果贵公司在许多不同的地区拥有大量用户群体，则您可能需要考虑拥有多个 ExpressRoute 电路和 "满足我" 的位置。</span><span class="sxs-lookup"><span data-stu-id="a5191-263">If your company has large user populations in many different regions, you may want to consider having multiple ExpressRoute circuits and meet-me locations.</span></span> <span data-ttu-id="a5191-264">对于你的一些用户位置，Microsoft 网络和 Office 365 中的最短/最佳路径可能不是通过内部 WAN 和 ExpressRoute 符合我的网络点，而是通过 Internet。</span><span class="sxs-lookup"><span data-stu-id="a5191-264">For some of your user locations, the shortest/most optimal path into Microsoft network and Office 365, may not be through your internal WAN and ExpressRoute meet-me points, but via the Internet.</span></span>
  
<span data-ttu-id="a5191-265">通常情况下，可以在与用户相对邻近的区域中选择多个 "符合我的位置"。</span><span class="sxs-lookup"><span data-stu-id="a5191-265">Often times, there are multiple meet-me locations that could be selected within a region with relative proximity to your users.</span></span> <span data-ttu-id="a5191-266">填写下表以指导你的决定。</span><span class="sxs-lookup"><span data-stu-id="a5191-266">Fill out the following table to guide your decisions.</span></span>

|<span data-ttu-id="a5191-267">**加利福尼亚和纽约的计划的 ExpressRoute 符合我的新位置**</span><span class="sxs-lookup"><span data-stu-id="a5191-267">**Planned ExpressRoute meet-me locations in California and New York**</span></span>||
|:-----|:-----|
|<span data-ttu-id="a5191-268">位置</span><span class="sxs-lookup"><span data-stu-id="a5191-268">Location</span></span>  <br/> |<span data-ttu-id="a5191-269">人数</span><span class="sxs-lookup"><span data-stu-id="a5191-269">Number of people</span></span>  <br/> |<span data-ttu-id="a5191-270">Internet 出口的预期延迟到 Microsoft 网络</span><span class="sxs-lookup"><span data-stu-id="a5191-270">Expected latency to Microsoft network over Internet egress</span></span>  <br/> |<span data-ttu-id="a5191-271">通过 ExpressRoute 对 Microsoft 网络的预期延迟</span><span class="sxs-lookup"><span data-stu-id="a5191-271">Expected latency to Microsoft network over ExpressRoute</span></span>  <br/> |
|<span data-ttu-id="a5191-272">Los Angeles</span><span class="sxs-lookup"><span data-stu-id="a5191-272">Los Angeles</span></span>  <br/> |<span data-ttu-id="a5191-273">10,000</span><span class="sxs-lookup"><span data-stu-id="a5191-273">10,000</span></span>  <br/> |<span data-ttu-id="a5191-274">~ 15ms</span><span class="sxs-lookup"><span data-stu-id="a5191-274">~15ms</span></span>  <br/> |<span data-ttu-id="a5191-275">~ 10ms （经由硅谷）</span><span class="sxs-lookup"><span data-stu-id="a5191-275">~10ms (via Silicon Valley)</span></span>  <br/> |
|<span data-ttu-id="a5191-276">华盛顿 DC</span><span class="sxs-lookup"><span data-stu-id="a5191-276">Washington DC</span></span>  <br/> |<span data-ttu-id="a5191-277">15,000</span><span class="sxs-lookup"><span data-stu-id="a5191-277">15,000</span></span>  <br/> |<span data-ttu-id="a5191-278">~ 20 毫秒</span><span class="sxs-lookup"><span data-stu-id="a5191-278">~20ms</span></span>  <br/> |<span data-ttu-id="a5191-279">~ 10ms （通过纽约）</span><span class="sxs-lookup"><span data-stu-id="a5191-279">~10ms (via New York)</span></span>  <br/> |
|<span data-ttu-id="a5191-280">州</span><span class="sxs-lookup"><span data-stu-id="a5191-280">Dallas</span></span>  <br/> |<span data-ttu-id="a5191-281">5,000</span><span class="sxs-lookup"><span data-stu-id="a5191-281">5,000</span></span>  <br/> |<span data-ttu-id="a5191-282">~ 15ms</span><span class="sxs-lookup"><span data-stu-id="a5191-282">~15ms</span></span>  <br/> |<span data-ttu-id="a5191-283">~ 40ms （通过纽约）</span><span class="sxs-lookup"><span data-stu-id="a5191-283">~40ms (via New York)</span></span>  <br/> |

<span data-ttu-id="a5191-284">在显示 Office 365 区域、ExpressRoute 网络服务提供商 "满足我的位置" 和 "按位置的人员数量" 的全局网络体系结构已开发好之后，可以使用它来确定是否可以进行优化。</span><span class="sxs-lookup"><span data-stu-id="a5191-284">Once the global network architecture showing the Office 365 region, ExpressRoute network service provider meet-me locations, and the quantity of people by location has been developed, it can be used to identify if any optimizations can be made.</span></span> <span data-ttu-id="a5191-285">它还可以显示全局发夹网络连接，在此连接中，流量路由到远处的位置以获取 "满足我的位置" 位置。</span><span class="sxs-lookup"><span data-stu-id="a5191-285">It may also show global hairpin network connections where traffic routes to a distant location in order to get the meet-me location.</span></span> <span data-ttu-id="a5191-286">如果发现了全局网络上的发夹，则应在继续操作之前对其进行修正。</span><span class="sxs-lookup"><span data-stu-id="a5191-286">If a hairpin on the global network is discovered it should be remediated before continuing.</span></span> <span data-ttu-id="a5191-287">请找到另一个 "网上邻居" 位置，或使用 "选择性 Internet" 的出站点以避免发夹。</span><span class="sxs-lookup"><span data-stu-id="a5191-287">Either find another meet-me location, or use selective Internet breakout egress points to avoid the hairpin.</span></span>
  
<span data-ttu-id="a5191-288">第一个图表显示了北美有两个物理位置的客户示例。</span><span class="sxs-lookup"><span data-stu-id="a5191-288">The first diagram, shows an example of a customer with two physical locations in North America.</span></span> <span data-ttu-id="a5191-289">您可以查看有关 "office 位置"、"Office 365 租户" 位置以及针对 ExpressRoute "满足我" 位置的几个选项的信息。</span><span class="sxs-lookup"><span data-stu-id="a5191-289">You can see the information about office locations, Office 365 tenant locations, and several choices for ExpressRoute meet-me locations.</span></span> <span data-ttu-id="a5191-290">在此示例中，客户根据两个原则选择了 "符合我的位置"，顺序如下：</span><span class="sxs-lookup"><span data-stu-id="a5191-290">In this example, the customer has selected the meet-me location based on two principles, in order:</span></span>
  
1. <span data-ttu-id="a5191-291">与组织中的人员最接近的距离。</span><span class="sxs-lookup"><span data-stu-id="a5191-291">Closest proximity to the people in their organization.</span></span>

2. <span data-ttu-id="a5191-292">最接近于 Microsoft 数据中心的位置，其中承载 Office 365。</span><span class="sxs-lookup"><span data-stu-id="a5191-292">Closest in proximity to a Microsoft datacenter where Office 365 is hosted.</span></span>

![ExpressRoute 美国地理位置-我](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
<span data-ttu-id="a5191-294">第二个图显示了一个包含类似信息和决策制定的多国客户的示例，这一点更深入地进一步扩展了此概念。</span><span class="sxs-lookup"><span data-stu-id="a5191-294">Expanding this concept slightly further, the second diagram shows an example multi-national customer faced with similar information and decision making.</span></span> <span data-ttu-id="a5191-295">此客户在孟加拉国中有一个小型办公室，只有十个人的一小团队致力于在区域中增长其占用量。</span><span class="sxs-lookup"><span data-stu-id="a5191-295">This customer has a small office in Bangladesh with only a small team of ten people focused on growing their footprint in the region.</span></span> <span data-ttu-id="a5191-296">在金奈中有一个 "满足我的位置" 和一个在金奈中托管 Office 365 的 Microsoft 数据中心，因此 "满足我的位置" 将有意义;但是，对于10人来说，额外电路的费用是繁重的。</span><span class="sxs-lookup"><span data-stu-id="a5191-296">There is a meet-me location in Chennai and a Microsoft datacenter with Office 365 hosted in Chennai so a meet-me location would make sense; however, for ten people, the expense of the additional circuit is burdensome.</span></span> <span data-ttu-id="a5191-297">在查看网络时，您需要确定在网络中发送网络流量所涉及的延迟是否比花费资金来获得另一个 ExpressRoute 电路更有效。</span><span class="sxs-lookup"><span data-stu-id="a5191-297">As you look at your network, you'll need to determine if the latency involved in sending your network traffic across your network is more effective than spending the capital to acquire another ExpressRoute circuit.</span></span>
  
<span data-ttu-id="a5191-298">或者，当我们的网络流量通过 internet 发送到 Microsoft 网络时，孟加拉的10名人员可能会遇到更好的性能，因为在介绍的规划图和复制过程中，他们会在其内部网络上进行路由如下.</span><span class="sxs-lookup"><span data-stu-id="a5191-298">Alternatively, the ten people in Bangladesh may experience better performance with their network traffic sent over the internet to the Microsoft network than they would routing on their internal network as we showed in the introductory diagrams and reproduced below.</span></span>
  
![区域图的出站连接](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a><span data-ttu-id="a5191-300">创建适用于 Office 365 实施计划的 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="a5191-300">Create your ExpressRoute for Office 365 implementation plan</span></span>
<span data-ttu-id="a5191-301"><a name="implementation"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-301"><a name="implementation"> </a></span></span>

<span data-ttu-id="a5191-302">您的实施计划应包括配置 ExpressRoute 的技术详细信息，以及在网络上配置所有其他基础结构的详细信息，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a5191-302">Your implementation plan should encompass both the technical details of configuring ExpressRoute as well as the details of configuring all the other infrastructure on your network, such as the following.</span></span>
  
- <span data-ttu-id="a5191-303">规划在 ExpressRoute 和 Internet 之间分割的服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-303">Plan which services split between ExpressRoute and Internet.</span></span>

- <span data-ttu-id="a5191-304">规划带宽、安全性、高可用性和故障转移。</span><span class="sxs-lookup"><span data-stu-id="a5191-304">Plan for bandwidth, security, high availability and failover.</span></span>

- <span data-ttu-id="a5191-305">设计入站和出站路由，包括针对不同位置的正确路由路径优化</span><span class="sxs-lookup"><span data-stu-id="a5191-305">Design inbound and outbound routing, including proper routing path optimizations for different locations</span></span>

- <span data-ttu-id="a5191-306">确定将向您的网络中播发的 ExpressRoute 路由的距离，以及客户端选择 Internet 或 ExpressRoute 路径的机制是什么;例如，直接路由或应用程序代理。</span><span class="sxs-lookup"><span data-stu-id="a5191-306">Decide how far ExpressRoute routes will be advertised into your network and what is the mechanism for clients to select Internet or ExpressRoute path; for example, direct routing or application proxy.</span></span>

- <span data-ttu-id="a5191-307">规划 DNS 记录更改，包括[发件人策略框架](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx)条目。</span><span class="sxs-lookup"><span data-stu-id="a5191-307">Plan DNS record changes, including [Sender Policy Framework](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) entries.</span></span>

- <span data-ttu-id="a5191-308">规划 NAT 策略，包括出站源 NAT 和入站源 NAT。</span><span class="sxs-lookup"><span data-stu-id="a5191-308">Plan NAT strategy including outbound and inbound source NAT.</span></span>

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a><span data-ttu-id="a5191-309">使用 internet 和 ExpressRoute 网络路径规划路由</span><span class="sxs-lookup"><span data-stu-id="a5191-309">Plan your routing with both internet and ExpressRoute network paths</span></span>
<span data-ttu-id="a5191-310"><a name="paths"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-310"><a name="paths"> </a></span></span>

- <span data-ttu-id="a5191-311">对于初始部署，建议使用 internet 的所有入站服务（如入站电子邮件或混合连接）。</span><span class="sxs-lookup"><span data-stu-id="a5191-311">For your initial deployment, all inbound services, such as inbound email or hybrid connectivity, are recommended to use the internet.</span></span>

- <span data-ttu-id="a5191-312">规划最终用户客户端局域网路由，例如[配置 PAC/WPAD 文件](https://aka.ms/manageo365endpoints)、默认路由、代理服务器和 BGP 路由播发。</span><span class="sxs-lookup"><span data-stu-id="a5191-312">Plan end user client LAN routing, such as [configuring a PAC/WPAD file](https://aka.ms/manageo365endpoints), default route, proxy servers, and BGP route advertisements.</span></span>

- <span data-ttu-id="a5191-313">规划外围路由，包括代理服务器、防火墙和云代理。</span><span class="sxs-lookup"><span data-stu-id="a5191-313">Plan perimeter routing, including proxy servers, firewalls, and cloud proxies.</span></span>

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a><span data-ttu-id="a5191-314">规划带宽、安全性、高可用性和故障转移</span><span class="sxs-lookup"><span data-stu-id="a5191-314">Plan your bandwidth, security, high availability and failover</span></span>
<span data-ttu-id="a5191-315"><a name="availability"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-315"><a name="availability"> </a></span></span>

<span data-ttu-id="a5191-316">制定针对每个主要 Office 365 工作负载所需的带宽的计划。</span><span class="sxs-lookup"><span data-stu-id="a5191-316">Create a plan for bandwidth required for each major Office 365 workload.</span></span> <span data-ttu-id="a5191-317">分别估计 Exchange Online、SharePoint Online 和 Skype for Business Online 带宽要求。</span><span class="sxs-lookup"><span data-stu-id="a5191-317">Separately estimate Exchange Online, SharePoint Online, and Skype for Business Online bandwidth requirements.</span></span> <span data-ttu-id="a5191-318">您可以使用我们为 Exchange Online 和 Skype for Business 提供的估计计算器作为开始位置;但是，必须具有用户配置文件和位置的代表性示例的试点测试，才能充分了解组织的带宽需求。</span><span class="sxs-lookup"><span data-stu-id="a5191-318">You can use the estimation calculators we've provided for Exchange Online and Skype for Business as a starting place; however, a pilot test with a representative sample of the user profiles and locations is required to fully understand the bandwidth needs of your organization.</span></span>
  
<span data-ttu-id="a5191-319">添加在每个 internet 和 ExpressRoute 出口位置处理安全性的方式在您的计划中，记住到 Office 365 的所有 ExpressRoute 连接使用公共对等连接，但仍必须按照与外部连接的公司安全策略进行安全保护networks.</span><span class="sxs-lookup"><span data-stu-id="a5191-319">Add how security is handled at each internet and ExpressRoute egress location to your plan, remember all ExpressRoute connections to Office 365 use public peering and must still be secured in accordance with your company security policies of connecting to external networks.</span></span>
  
<span data-ttu-id="a5191-320">向计划中添加有关哪些人将受到哪种类型的中断影响的详细信息，以及这些人员如何能够以最简单的方式在完全容量内执行其工作的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a5191-320">Add details to your plan about which people will be affected by what type of outage and how those people will be able to perform their work at full capacity in the simplest manner.</span></span>
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a><span data-ttu-id="a5191-321">在抖动、延迟、拥塞和余地上规划包含 Skype for Business 要求的带宽要求</span><span class="sxs-lookup"><span data-stu-id="a5191-321">Plan bandwidth requirements including Skype for Business requirements on Jitter, Latency, Congestion, and Headroom</span></span>
  
<span data-ttu-id="a5191-322">Skype for Business Online 还具有特定的其他网络要求，这些要求在[Skype for Business online 中的文章媒体质量和网络连接性能](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)中进行了详细介绍。</span><span class="sxs-lookup"><span data-stu-id="a5191-322">Skype for Business Online also has specific additional network requirements which are detailed in the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>
  
<span data-ttu-id="a5191-323">阅读[使用 ExpressRoute For Office 365 的网络规划](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)中的**Azure ExpressRoute 的 "带宽规划**" 一节。</span><span class="sxs-lookup"><span data-stu-id="a5191-323">Read the section **Bandwidth planning for Azure ExpressRoute** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
<span data-ttu-id="a5191-324">当你的试点用户执行带宽评估时，你可以使用我们的指南;[使用基线和性能历史记录的 Office 365 性能优化](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)。</span><span class="sxs-lookup"><span data-stu-id="a5191-324">When performing a bandwidth assessment with your pilot users, you can use our guide; [Office 365 performance tuning using baselines and performance history](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).</span></span>
  
#### <a name="plan-for-high-availability-requirements"></a><span data-ttu-id="a5191-325">规划高可用性要求</span><span class="sxs-lookup"><span data-stu-id="a5191-325">Plan for high availability requirements</span></span>
  
<span data-ttu-id="a5191-326">创建高可用性计划以满足您的需求，并将其合并到更新后的网络拓扑图中。</span><span class="sxs-lookup"><span data-stu-id="a5191-326">Create a plan for high availability to meet your needs and incorporate this into your updated network topology diagram.</span></span> <span data-ttu-id="a5191-327">[使用适用于 Office 365 的 ExpressRoute 在网络规划](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)中**使用 Azure ExpressRoute 的高可用性和故障转移**阅读部分。</span><span class="sxs-lookup"><span data-stu-id="a5191-327">Read the section **High availability and failover with Azure ExpressRoute** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
#### <a name="plan-for-network-security-requirements"></a><span data-ttu-id="a5191-328">规划网络安全要求</span><span class="sxs-lookup"><span data-stu-id="a5191-328">Plan for network security requirements</span></span>
  
<span data-ttu-id="a5191-329">创建符合网络安全要求的计划，并将其合并到更新后的网络拓扑图中。</span><span class="sxs-lookup"><span data-stu-id="a5191-329">Create a plan to meet your network security requirements and incorporate this into your updated network topology diagram.</span></span> <span data-ttu-id="a5191-330">阅读[使用 ExpressRoute For office 365 在网络规划](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)中**将安全控制应用于 Azure 365 ExpressRoute**的一节。</span><span class="sxs-lookup"><span data-stu-id="a5191-330">Read the section **Applying security controls to Azure ExpressRoute for Office 365 scenarios** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
### <a name="design-outbound-service-connectivity"></a><span data-ttu-id="a5191-331">设计出站服务连接</span><span class="sxs-lookup"><span data-stu-id="a5191-331">Design outbound service connectivity</span></span>
<span data-ttu-id="a5191-332"><a name="outbound"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-332"><a name="outbound"> </a></span></span>

<span data-ttu-id="a5191-333">适用于 Office 365 的 ExpressRoute 具有可能不熟悉的*出站*网络要求。</span><span class="sxs-lookup"><span data-stu-id="a5191-333">ExpressRoute for Office 365 has  *outbound*  network requirements that may be unfamiliar.</span></span> <span data-ttu-id="a5191-334">具体来说，将用户和网络与 Office 365 表示的 IP 地址，并充当到 Microsoft 的出站网络连接的源终结点，必须遵循下面概述的特定要求。</span><span class="sxs-lookup"><span data-stu-id="a5191-334">Specifically, the IP addresses that represent your users and networks to Office 365 and act as the source endpoints for outbound network connections to Microsoft must follow specific requirements outlined below.</span></span>
  
1. <span data-ttu-id="a5191-335">终结点必须是公共 IP 地址，它们已注册到您的公司或提供与您的 ExpressRoute 连接的运营商。</span><span class="sxs-lookup"><span data-stu-id="a5191-335">The endpoints must be public IP addresses, that are registered to your company or to carrier providing ExpressRoute connectivity to you.</span></span>

2. <span data-ttu-id="a5191-336">必须将终结点播发到 Microsoft 并通过 ExpressRoute 验证/接受这些终结点。</span><span class="sxs-lookup"><span data-stu-id="a5191-336">The endpoints must be advertised to Microsoft and validated/accepted by ExpressRoute.</span></span>

3. <span data-ttu-id="a5191-337">不得将终结点公布到具有相同或更多首选路由指标的 Internet。</span><span class="sxs-lookup"><span data-stu-id="a5191-337">The endpoints must not be advertised to the Internet with the same or more preferred routing metric.</span></span>

4. <span data-ttu-id="a5191-338">终结点不得用于连接到未通过 ExpressRoute 配置的 Microsoft 服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-338">The endpoints must not be used for connectivity to Microsoft services that are not configured over ExpressRoute.</span></span>

<span data-ttu-id="a5191-339">如果您的网络设计不符合这些要求，则您的用户将遇到由于路由黑色 holing 或非对称路由而导致的 Office 365 和其他 Microsoft 服务连接故障的高风险。</span><span class="sxs-lookup"><span data-stu-id="a5191-339">If your network design doesn't meet these requirements, there is a high risk your users will experience connectivity failures to Office 365 and other Microsoft services due to route black holing or asymmetric routing.</span></span> <span data-ttu-id="a5191-340">当通过 ExpressRoute 路由对 Microsoft 服务的请求时，将发生这种情况，但响应通过 internet 路由回来，反之亦然，并且这些响应被状态网络设备（如防火墙）丢弃。</span><span class="sxs-lookup"><span data-stu-id="a5191-340">This occurs when requests to Microsoft services are routed over ExpressRoute, but responses are routed back across the internet, or vice versa, and the responses are dropped by stateful network devices such as firewalls.</span></span>
  
<span data-ttu-id="a5191-341">您可以用来满足上述要求的最常用方法是使用源 NAT，它可以作为网络的一部分实现，也可以由您的 ExpressRoute 运营商提供。</span><span class="sxs-lookup"><span data-stu-id="a5191-341">The most common method you can use to meet the above requirements is to use source NAT, either implemented as a part of your network or provided by your ExpressRoute carrier.</span></span> <span data-ttu-id="a5191-342">源 NAT 允许你从 ExpressRoute 中抽象出 internet 网络的详细信息和专用 IP 寻址，以及结合使用正确的 IP 路由播发，提供一种简单的机制来确保路径对称。</span><span class="sxs-lookup"><span data-stu-id="a5191-342">Source NAT allows you to abstract the details and private IP addressing of your internet network from ExpressRoute and; coupled with proper IP route advertisements, provide an easy mechanism to ensure path symmetry.</span></span> <span data-ttu-id="a5191-343">如果要使用特定于 ExpressRoute 对等位置的有状态网络设备，则必须为每个 ExpressRoute 对等项实现单独的 NAT 池，以确保路径对称。</span><span class="sxs-lookup"><span data-stu-id="a5191-343">If you're using stateful network devices that are specific to ExpressRoute peering locations, you must implement separate NAT pools for each ExpressRoute peering to ensure path symmetry.</span></span>
  
<span data-ttu-id="a5191-344">阅读有关[EXPRESSROUTE NAT 要求](https://azure.microsoft.com/documentation/articles/expressroute-nat/)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a5191-344">Read more about the [ExpressRoute NAT requirements](https://azure.microsoft.com/documentation/articles/expressroute-nat/).</span></span>
  
<span data-ttu-id="a5191-345">将出站连接的更改添加到网络拓扑图中。</span><span class="sxs-lookup"><span data-stu-id="a5191-345">Add the changes for the outbound connectivity to the network topology diagram.</span></span>
  
### <a name="design-inbound-service-connectivity"></a><span data-ttu-id="a5191-346">设计入站服务连接</span><span class="sxs-lookup"><span data-stu-id="a5191-346">Design inbound service connectivity</span></span>
<span data-ttu-id="a5191-347"><a name="inbound"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-347"><a name="inbound"> </a></span></span>

<span data-ttu-id="a5191-348">大多数企业 Office 365 部署假定从 Office 365 到本地服务的某种形式的入站连接，如 Exchange、SharePoint 和 Skype for Business 混合方案、邮箱迁移和使用 ADFS 的身份验证基本.</span><span class="sxs-lookup"><span data-stu-id="a5191-348">The majority of enterprise Office 365 deployments assume some form of inbound connectivity from Office 365 to on-premises services, such as for Exchange, SharePoint, and Skype for Business hybrid scenarios, mailbox migrations, and authentication using ADFS infrastructure.</span></span> <span data-ttu-id="a5191-349">当 ExpressRoute 在本地网络和 Microsoft 之间启用了其他路由路径以实现出站连接时，这些入站连接可能会因非对称路由而意外受到影响，即使您打算让这些流继续使用 Internet。</span><span class="sxs-lookup"><span data-stu-id="a5191-349">When ExpressRoute you enable an additional routing path between your on-premises network and Microsoft for outbound connectivity, these inbound connections may inadvertently be impacted by asymmetric routing, even if you intend to have those flows continue to use the Internet.</span></span> <span data-ttu-id="a5191-350">建议使用下面介绍的一些预防措施，以确保从 Office 365 到本地系统的基于 Internet 的入站流无任何影响。</span><span class="sxs-lookup"><span data-stu-id="a5191-350">A few precautions described below are recommended to ensure there is no impact to Internet based inbound flows from Office 365 to on-premises systems.</span></span>
  
<span data-ttu-id="a5191-351">若要最大限度地降低对入站网络流量流的非对称路由风险，所有入站连接都应先使用源 NAT，然后再将源 NAT 路由到网络段，从而将可见性路由到 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="a5191-351">To minimize the risks of asymmetric routing for inbound network traffic flows, all of the inbound connections should use source NAT before they're routed into segments of your network which have routing visibility into ExpressRoute.</span></span> <span data-ttu-id="a5191-352">如果允许传入连接到在没有源 NAT 的 ExpressRoute 中具有路由可见性的网段，则从 Office 365 发出的请求将从 internet 进入，但返回到 Office 365 的响应将优先于 ExpressRoute返回到 Microsoft 网络的网络路径，从而导致不对称路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-352">If the incoming connections are allowed onto a network segment with routing visibility into ExpressRoute without source NAT, requests originating from Office 365 will enter from the internet, but the response going back to Office 365 will prefer the ExpressRoute network path back to the Microsoft network, causing asymmetric routing.</span></span>
  
<span data-ttu-id="a5191-353">您可以考虑采用以下实现模式之一来满足此要求：</span><span class="sxs-lookup"><span data-stu-id="a5191-353">You may consider one of the following implementation patterns to satisfy this requirement:</span></span>
  
1. <span data-ttu-id="a5191-354">先执行源 NAT，然后再使用网络设备（例如防火墙）或从 Internet 到本地系统的路径上的负载平衡器将请求路由到内部网络。</span><span class="sxs-lookup"><span data-stu-id="a5191-354">Perform source NAT before requests are routed into your internal network using networking equipment such as firewalls or load balancers on the path from the Internet to your on-premises systems.</span></span>

2. <span data-ttu-id="a5191-355">确保 ExpressRoute 路由不会传播到入站服务（如前端服务器或反向代理系统）的网络段，以处理 Internet 连接。</span><span class="sxs-lookup"><span data-stu-id="a5191-355">Ensure that ExpressRoute routes are not propagated to the network segments where inbound services, such as front end servers or reverse proxy systems, handling Internet connections reside.</span></span>

<span data-ttu-id="a5191-356">在网络中显式记帐这些方案，并通过 Internet 保留所有入站网络通信流有助于最大限度地减少非对称路由的部署和操作风险。</span><span class="sxs-lookup"><span data-stu-id="a5191-356">Explicitly accounting for these scenarios in your network and keeping all inbound network traffic flows over the Internet helps to minimize deployment and operational risk of asymmetric routing.</span></span>
  
<span data-ttu-id="a5191-357">在某些情况下，您可能会选择通过 ExpressRoute 连接来指示某些入站流量。</span><span class="sxs-lookup"><span data-stu-id="a5191-357">There may be cases where you may choose to direct some inbound flows over ExpressRoute connections.</span></span> <span data-ttu-id="a5191-358">在这些情况下，请考虑以下其他注意事项。</span><span class="sxs-lookup"><span data-stu-id="a5191-358">For these scenarios, take the following additional considerations into account.</span></span>
  
1. <span data-ttu-id="a5191-359">Office 365 只能面向使用公共 Ip 的本地终结点。</span><span class="sxs-lookup"><span data-stu-id="a5191-359">Office 365 can only target on-premises endpoints that use public IPs.</span></span> <span data-ttu-id="a5191-360">这意味着，即使内部部署入站终结点仅向基于 ExpressRoute 的 Office 365 公开，仍需要与之关联的公用 IP。</span><span class="sxs-lookup"><span data-stu-id="a5191-360">This means that even if the on-premises inbound endpoint is only exposed to Office 365 over ExpressRoute, it still needs to have public IP associated with it.</span></span>

2. <span data-ttu-id="a5191-361">Office 365 服务为解决本地终结点而执行的所有 DNS 名称解析均使用公用 DNS 进行。</span><span class="sxs-lookup"><span data-stu-id="a5191-361">All DNS name resolution that Office 365 services perform to resolve on-premises endpoints happen using public DNS.</span></span> <span data-ttu-id="a5191-362">这意味着，您必须将入站服务终结点 "FQDN" 注册到 Internet 上的 IP 映射。</span><span class="sxs-lookup"><span data-stu-id="a5191-362">This means that you must register inbound service endpoints' FQDN to IP mappings on the Internet.</span></span>

3. <span data-ttu-id="a5191-363">为了通过 ExpressRoute 接收入站网络连接，必须将这些终结点的公共 IP 子网公布到基于 ExpressRoute 的 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a5191-363">In order to receive inbound network connections over ExpressRoute, the public IP subnets for these endpoints must to be advertised to Microsoft over ExpressRoute.</span></span>

4. <span data-ttu-id="a5191-364">仔细评估这些入站网络流量流，以确保按照贵公司的安全和网络策略对其应用正确的安全和网络控制。</span><span class="sxs-lookup"><span data-stu-id="a5191-364">Carefully evaluate these inbound network traffic flows to ensure that proper security and network controls are applied to them in accordance with your company security and network policies.</span></span>

5. <span data-ttu-id="a5191-365">一旦将本地入站终结点通过 ExpressRoute 播发到 Microsoft，ExpressRoute 将有效地成为所有 Microsoft 服务（包括 Office 365）的首选路由路径。</span><span class="sxs-lookup"><span data-stu-id="a5191-365">Once your on-premises inbound endpoints are advertised to Microsoft over ExpressRoute, ExpressRoute will effectively become the preferred routing path to those endpoints for all Microsoft services, including Office 365.</span></span> <span data-ttu-id="a5191-366">这意味着这些终结点子网必须仅用于与 Office 365 服务通信，而不能用于 Microsoft 网络上的其他服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-366">This means that those endpoint subnets must only be used for communications with Office 365 services and no other services on the Microsoft network.</span></span> <span data-ttu-id="a5191-367">否则，您的设计将导致非对称路由，来自其他 Microsoft 服务的入站连接更愿意路由入站传入的 ExpressRoute，而返回路径将使用 Internet。</span><span class="sxs-lookup"><span data-stu-id="a5191-367">Otherwise, your design will cause asymmetric routing where inbound connections from other Microsoft services prefer to route inbound over ExpressRoute, while the return path will use the Internet.</span></span>

6. <span data-ttu-id="a5191-368">如果 ExpressRoute 电路或 "满足我的位置" 断开，则需要确保本地入站终结点仍可在单独的网络路径上接受请求。</span><span class="sxs-lookup"><span data-stu-id="a5191-368">In the event an ExpressRoute circuit or meet-me location is down, you'll need to ensure the on-premises inbound endpoints are still available to accept requests over a separate network path.</span></span> <span data-ttu-id="a5191-369">这可能意味着通过多个 ExpressRoute 电路为这些终结点公布子网。</span><span class="sxs-lookup"><span data-stu-id="a5191-369">This may mean advertising subnets for those endpoints through multiple ExpressRoute circuits.</span></span>

7. <span data-ttu-id="a5191-370">我们建议通过 ExpressRoute 为进入网络的所有入站网络流量应用源 NAT，尤其是当这些流量流经各种状态的网络设备（如防火墙）时。</span><span class="sxs-lookup"><span data-stu-id="a5191-370">We recommend applying source NAT for all inbound network traffic flows entering your network through ExpressRoute, especially when these flows cross stateful network devices such as firewalls.</span></span>

8. <span data-ttu-id="a5191-371">某些本地服务（例如 ADFS 代理或 Exchange 自动发现）可能会收到来自 Internet 的 Office 365 服务和用户的入站请求。</span><span class="sxs-lookup"><span data-stu-id="a5191-371">Some on-premises services, such as ADFS proxy or Exchange autodiscover, may receive inbound requests from both Office 365 services and users from the Internet.</span></span> <span data-ttu-id="a5191-372">对于这些请求，Office 365 将针对与 Internet 上的用户请求相同的 FQDN。</span><span class="sxs-lookup"><span data-stu-id="a5191-372">For these requests Office 365 will target the same FQDN as user requests over the Internet.</span></span> <span data-ttu-id="a5191-373">允许从 internet 到这些本地终结点的入站用户连接，同时强制 Office 365 连接使用 ExpressRoute，这表示显著的路由复杂性。</span><span class="sxs-lookup"><span data-stu-id="a5191-373">Allowing inbound user connections from the internet to those on-premises endpoints, while forcing Office 365 connections to use ExpressRoute, represents significant routing complexity.</span></span> <span data-ttu-id="a5191-374">由于操作方面的考虑，我们不建议大多数客户通过 ExpressRoute 实施此类复杂方案。</span><span class="sxs-lookup"><span data-stu-id="a5191-374">For the vast majority of customers implementing such complex scenarios over ExpressRoute is not recommended due to operational considerations.</span></span> <span data-ttu-id="a5191-375">此额外的开销包括，管理非对称路由的风险，并且将要求您仔细管理跨多个维度的路由广告和策略。</span><span class="sxs-lookup"><span data-stu-id="a5191-375">This additional overhead includes, managing risks of asymmetric routing and will require you to carefully manage routing advertisements and policies across multiple dimensions.</span></span>

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a><span data-ttu-id="a5191-376">更新网络拓扑计划以显示如何避免非对称路由</span><span class="sxs-lookup"><span data-stu-id="a5191-376">Update your network topology plan to show how you would avoid asymmetric routes</span></span>
<span data-ttu-id="a5191-377"><a name="asymmetric"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-377"><a name="asymmetric"> </a></span></span>

<span data-ttu-id="a5191-378">您希望避免使用非对称路由，以确保组织中的人员能够无缝使用 Office 365 以及 internet 上的其他重要服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-378">You want to avoid asymmetric routing to ensure people in your organization can seamlessly use Office 365 as well as other important services on the internet.</span></span> <span data-ttu-id="a5191-379">客户有两个常见配置导致了非对称路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-379">There are two common configurations customers have that cause asymmetric routing.</span></span> <span data-ttu-id="a5191-380">现在我们来回顾一下你计划使用的网络配置，并检查是否可以存在其中一个非对称路由方案。</span><span class="sxs-lookup"><span data-stu-id="a5191-380">Now's a good time to review the network configuration you're planning to use and check if one of these asymmetric routing scenarios could exist.</span></span>
  
<span data-ttu-id="a5191-381">首先，我们将研究与以下网络图相关联的几种不同情况。</span><span class="sxs-lookup"><span data-stu-id="a5191-381">To begin, we'll examine a few different situations associated with the following network diagram.</span></span> <span data-ttu-id="a5191-382">在此图中，接收入站请求的所有服务器（如 ADFS 或内部部署混合服务器）都位于新的 Jersey 数据中心，并将公布到 internet。</span><span class="sxs-lookup"><span data-stu-id="a5191-382">In this diagram, all servers that receive inbound requests, such as ADFS or on-premises hybrid servers are in the New Jersey data center and are advertised to the internet.</span></span>
  
1. <span data-ttu-id="a5191-383">虽然外围网络是安全的，但没有可用于传入请求的源 NAT。</span><span class="sxs-lookup"><span data-stu-id="a5191-383">While the perimeter network is secure, there is no Source NAT available for incoming requests.</span></span>

2. <span data-ttu-id="a5191-384">新 Jersey 数据中心中的服务器可以同时查看 internet 和 ExpressRoute 路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-384">The servers in the New Jersey data center are able to see both internet and ExpressRoute routes.</span></span>

![ExpressRoute 连接概述](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
<span data-ttu-id="a5191-386">我们还提供了有关如何修复这些问题的建议。</span><span class="sxs-lookup"><span data-stu-id="a5191-386">We also have suggestions on how to fix them.</span></span>
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a><span data-ttu-id="a5191-387">问题1：云到 Internet 上的本地连接</span><span class="sxs-lookup"><span data-stu-id="a5191-387">Problem 1: Cloud to on-premises connection over the Internet</span></span>
  
<span data-ttu-id="a5191-388">下图说明了网络配置在 internet 上不提供来自 Microsoft 云的入站请求的 NAT 时所采用的非对称网络路径。</span><span class="sxs-lookup"><span data-stu-id="a5191-388">The following diagram illustrates the asymmetric network path taken when your network configuration doesn't provide NAT for inbound requests from the Microsoft cloud over the internet.</span></span>
  
1. <span data-ttu-id="a5191-389">来自 Office 365 的入站请求从公用 DNS 检索本地终结点的 IP 地址，并将该请求发送到您的外围网络。</span><span class="sxs-lookup"><span data-stu-id="a5191-389">The inbound request from Office 365 retrieves the IP address of the on-premises endpoint from public DNS and sends the request to your perimeter network.</span></span>

2. <span data-ttu-id="a5191-390">在这种错误配置中，未配置源 NAT 或在外围网络中提供通信，这会导致实际源 IP 地址用作返回目标。</span><span class="sxs-lookup"><span data-stu-id="a5191-390">In this faulty configuration, there is no Source NAT configured or available at the perimeter network where the traffic is sent resulting in the actual source IP address being used as the return destination.</span></span>

  - <span data-ttu-id="a5191-391">网络上的服务器通过任何可用的 ExpressRoute 网络连接将返回流量路由到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="a5191-391">The server on your network routes the return traffic to Office 365 through any available ExpressRoute network connection.</span></span>

  - <span data-ttu-id="a5191-392">结果是该流到 Office 365 的一个非对称路径，导致连接中断。</span><span class="sxs-lookup"><span data-stu-id="a5191-392">The result is an Asymmetric path for that flow to Office 365, resulting in a broken connection.</span></span>

![ExpressRoute Asymetric 路由问题1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a><span data-ttu-id="a5191-394">解决方案1a：源 NAT</span><span class="sxs-lookup"><span data-stu-id="a5191-394">Solution 1a: Source NAT</span></span>
  
<span data-ttu-id="a5191-395">仅将源 NAT 添加到入站请求可解析此配置错误的网络。</span><span class="sxs-lookup"><span data-stu-id="a5191-395">Simply adding a source NAT to the inbound request resolves this misconfigured network.</span></span> <span data-ttu-id="a5191-396">在此图中：</span><span class="sxs-lookup"><span data-stu-id="a5191-396">In this diagram:</span></span>
  
1. <span data-ttu-id="a5191-397">传入请求继续通过新 Jersey 数据中心的外围网络进行输入。</span><span class="sxs-lookup"><span data-stu-id="a5191-397">The incoming request continues to enter through the New Jersey data center's perimeter network.</span></span> <span data-ttu-id="a5191-398">此时间源 NAT 可用。</span><span class="sxs-lookup"><span data-stu-id="a5191-398">This time Source NAT is available.</span></span>

2. <span data-ttu-id="a5191-399">来自服务器的响应将发往与源 NAT 关联的 IP，而不是原始 IP 地址，从而导致响应沿相同的网络路径返回。</span><span class="sxs-lookup"><span data-stu-id="a5191-399">The response from the server routes back toward the IP associated with the Source NAT instead of the original IP address, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由解决方案1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a><span data-ttu-id="a5191-401">解决方案1b：路由范围</span><span class="sxs-lookup"><span data-stu-id="a5191-401">Solution 1b: Route Scoping</span></span>
  
<span data-ttu-id="a5191-402">或者，您可以选择不允许公布 ExpressRoute BGP 前缀，从而删除这些计算机的备用网络路径。</span><span class="sxs-lookup"><span data-stu-id="a5191-402">Alternatively, you can choose to not allow the ExpressRoute BGP prefixes to be advertised, removing the alternate network path for those computers.</span></span> <span data-ttu-id="a5191-403">在此图中：</span><span class="sxs-lookup"><span data-stu-id="a5191-403">In this diagram:</span></span>
  
1. <span data-ttu-id="a5191-404">传入请求继续通过新 Jersey 数据中心的外围网络进行输入。</span><span class="sxs-lookup"><span data-stu-id="a5191-404">The incoming request continues to enter through the New Jersey data center's perimeter network.</span></span> <span data-ttu-id="a5191-405">这次，从 Microsoft 通过 ExpressRoute 电路播发的前缀对新的 Jersey 数据中心不可用。</span><span class="sxs-lookup"><span data-stu-id="a5191-405">This time the prefixes advertised from Microsoft over the ExpressRoute circuit are not available to the New Jersey data center.</span></span>

2. <span data-ttu-id="a5191-406">来自服务器的响应将路由回与原始 IP 地址关联的 IP 地址，而不是唯一的路由，从而导致响应沿同一个网络路径返回。</span><span class="sxs-lookup"><span data-stu-id="a5191-406">The response from the server routes back toward the IP associated with the original IP address over the only route available, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由解决方案2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a><span data-ttu-id="a5191-408">问题2：云到基于 ExpressRoute 的本地连接</span><span class="sxs-lookup"><span data-stu-id="a5191-408">Problem 2: Cloud to on-premises connection over ExpressRoute</span></span>
  
<span data-ttu-id="a5191-409">下图显示了在网络配置不为来自 ExpressRoute 的 Microsoft 云中的入站请求提供 NAT 时所采用的非对称网络路径。</span><span class="sxs-lookup"><span data-stu-id="a5191-409">The following diagram illustrates the asymmetric network path taken when your network configuration doesn't provide NAT for inbound requests from the Microsoft cloud over ExpressRoute.</span></span>
  
1. <span data-ttu-id="a5191-410">来自 Office 365 的入站请求从 DNS 检索 IP 地址，并将请求发送到您的外围网络。</span><span class="sxs-lookup"><span data-stu-id="a5191-410">The inbound request from Office 365 retrieves the IP address from DNS and sends the request to your perimeter network.</span></span>

2. <span data-ttu-id="a5191-411">在这种错误配置中，未配置源 NAT 或在外围网络中提供通信，这会导致实际源 IP 地址用作返回目标。</span><span class="sxs-lookup"><span data-stu-id="a5191-411">In this faulty configuration, there is no Source NAT configured or available at the perimeter network where the traffic is sent resulting in the actual source IP address being used as the return destination.</span></span>

  - <span data-ttu-id="a5191-412">网络上的计算机通过任何可用的 ExpressRoute 网络连接将返回流量路由到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="a5191-412">The computer on your network routes the return traffic to Office 365 through any available ExpressRoute network connection.</span></span>

  - <span data-ttu-id="a5191-413">结果是与 Office 365 的非对称连接。</span><span class="sxs-lookup"><span data-stu-id="a5191-413">The result is an Asymmetric connection to Office 365.</span></span>

![ExpressRoute Asymetric 路由问题2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a><span data-ttu-id="a5191-415">解决方案2：源 NAT</span><span class="sxs-lookup"><span data-stu-id="a5191-415">Solution 2: Source NAT</span></span>
  
<span data-ttu-id="a5191-416">仅将源 NAT 添加到入站请求可解析此配置错误的网络。</span><span class="sxs-lookup"><span data-stu-id="a5191-416">Simply adding a source NAT to the inbound request resolves this misconfigured network.</span></span> <span data-ttu-id="a5191-417">在此图中：</span><span class="sxs-lookup"><span data-stu-id="a5191-417">In this diagram:</span></span>
  
1. <span data-ttu-id="a5191-418">传入请求继续通过纽约数据中心的外围网络进入。</span><span class="sxs-lookup"><span data-stu-id="a5191-418">The incoming request continues to enter through the New York data center's perimeter network.</span></span> <span data-ttu-id="a5191-419">此时间源 NAT 可用。</span><span class="sxs-lookup"><span data-stu-id="a5191-419">This time Source NAT is available.</span></span>

2. <span data-ttu-id="a5191-420">来自服务器的响应将发往与源 NAT 关联的 IP，而不是原始 IP 地址，从而导致响应沿相同的网络路径返回。</span><span class="sxs-lookup"><span data-stu-id="a5191-420">The response from the server routes back toward the IP associated with the Source NAT instead of the original IP address, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由解决方案3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a><span data-ttu-id="a5191-422">纸张验证网络设计是否具有对称路径</span><span class="sxs-lookup"><span data-stu-id="a5191-422">Paper verify that the network design has path symmetry</span></span>

<span data-ttu-id="a5191-423">在这种情况下，您需要验证您的实施计划为您将使用 Office 365 的不同方案提供路由对称的纸张。</span><span class="sxs-lookup"><span data-stu-id="a5191-423">At this point, you need to verify on paper that your implementation plan offers route symmetry for the different scenarios in which you'll be using Office 365.</span></span> <span data-ttu-id="a5191-424">当某人使用服务的不同功能时，您将确定应采取的特定网络路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-424">You'll identify the specific network route that is expected to be taken when a person uses different features of the service.</span></span> <span data-ttu-id="a5191-425">从本地网络和 WAN 路由，到外围设备，再到连接路径;ExpressRoute 或 internet，以及与在线终结点的连接。</span><span class="sxs-lookup"><span data-stu-id="a5191-425">From the on-premises network and WAN routing, to the perimeter devices, to the connectivity path; ExpressRoute or the internet, and on to the connection to the online endpoint.</span></span>
  
<span data-ttu-id="a5191-426">您需要为之前标识为您的组织将采用的服务的所有 Office 365 网络服务执行此操作。</span><span class="sxs-lookup"><span data-stu-id="a5191-426">You'll need to do this for all of the Office 365 network services that were previously identified as services that your organization will adopt.</span></span>
  
<span data-ttu-id="a5191-427">这有助于本白皮书通过第二个人的路由进行审核。</span><span class="sxs-lookup"><span data-stu-id="a5191-427">It helps to do this paper walk through of routes with a second person.</span></span> <span data-ttu-id="a5191-428">向其解释：每个网络跃点都应从其获取下一个路由，并确保您熟悉路由路径。</span><span class="sxs-lookup"><span data-stu-id="a5191-428">Explain to them where each network hop is expected to get its next route from and ensure that you're familiar with the routing paths.</span></span> <span data-ttu-id="a5191-429">请注意，ExpressRoute 将始终提供到 Microsoft 服务器 IP 地址的更多作用域路由，从而使路由开销低于 Internet 默认路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-429">Remember that ExpressRoute will always provide a more scoped route to Microsoft server IP addresses giving it lower route cost than an Internet default route.</span></span>
  
### <a name="design-client-connectivity-configuration"></a><span data-ttu-id="a5191-430">设计客户端连接配置</span><span class="sxs-lookup"><span data-stu-id="a5191-430">Design Client Connectivity Configuration</span></span>
<span data-ttu-id="a5191-431"><a name="asymmetric"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-431"><a name="asymmetric"> </a></span></span>

![将 PAC 文件与 ExpressRoute 结合使用](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
<span data-ttu-id="a5191-433">如果要将代理服务器用于 internet 绑定的流量，则需要调整任何 PAC 或客户端配置文件，以确保网络中的客户端计算机正确配置为将所需的 ExpressRoute 流量发送到 Office 365，而不会使用 transiting代理服务器以及其余的流量（包括一些 Office 365 流量）将发送到相关代理。</span><span class="sxs-lookup"><span data-stu-id="a5191-433">If you're using a proxy server for internet bound traffic then you need to adjust any PAC or client configuration files to ensure client computers on your network are correctly configured to send the ExpressRoute traffic you desire to Office 365 without transiting your proxy server, and the remaining traffic, including some Office 365 traffic, is sent to the relevant proxy.</span></span> <span data-ttu-id="a5191-434">阅读有关[管理 Office 365 端点](https://aka.ms/manageo365endpoints)的指南，以获取有关 PAC 文件的示例。</span><span class="sxs-lookup"><span data-stu-id="a5191-434">Read our guide on [managing Office 365 endpoints](https://aka.ms/manageo365endpoints) for example PAC files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a5191-435">终结点经常发生变化，每周经常发生变化。</span><span class="sxs-lookup"><span data-stu-id="a5191-435">The endpoints change frequently, as often as weekly.</span></span> <span data-ttu-id="a5191-436">您只应根据您的组织采用的服务和功能进行更改，以减少所需的更改次数，以确保保持最新。</span><span class="sxs-lookup"><span data-stu-id="a5191-436">You should only make changes based on the services and features your organization has adopted to reduce the number of changes you'll need to make to stay current.</span></span> <span data-ttu-id="a5191-437">请密切注意 RSS 源中的**生效日期**，在该 rss 源中宣布了所做的更改，并保留了所有过去的更改，已发布的 IP 地址可能不会公布，也不会从播发中删除，直到达到生效日期为止。</span><span class="sxs-lookup"><span data-stu-id="a5191-437">Pay close attention to the **Effective Date** in the RSS feed where the changes are announced and a record is kept of all past changes, IP addresses that are announced may not be advertised, or removed from advertisement, until the effective date is reached.</span></span>
  
## <a name="build-your-deployment-and-testing-procedures"></a><span data-ttu-id="a5191-438">生成部署和测试过程</span><span class="sxs-lookup"><span data-stu-id="a5191-438">Build your deployment and testing procedures</span></span>
<span data-ttu-id="a5191-439"><a name="testing"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-439"><a name="testing"> </a></span></span>

<span data-ttu-id="a5191-440">你的实施计划应包括测试和回滚规划。</span><span class="sxs-lookup"><span data-stu-id="a5191-440">Your implementation plan should include both testing and rollback planning.</span></span> <span data-ttu-id="a5191-441">如果您的实施未按预期运行，则计划应设计为在发现问题之前影响最少人数。</span><span class="sxs-lookup"><span data-stu-id="a5191-441">If your implementation isn't functioning as expected, the plan should be designed to affect the least number of people before problems are discovered.</span></span> <span data-ttu-id="a5191-442">以下是您的计划应考虑的一些高级别原则。</span><span class="sxs-lookup"><span data-stu-id="a5191-442">The following are some high level principles your plan should consider.</span></span>
  
1. <span data-ttu-id="a5191-443">暂存网络分段和用户服务的加入，以最大限度地减少中断。</span><span class="sxs-lookup"><span data-stu-id="a5191-443">Stage the network segment and user service onboarding to minimize disruption.</span></span>

2. <span data-ttu-id="a5191-444">规划使用 traceroute 和 TCP 连接从单独的 internet 连接主机测试路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-444">Plan for testing routes with traceroute and TCP connect from a separate internet connected host.</span></span>

3. <span data-ttu-id="a5191-445">最好是在具有测试 Office 365 租户的独立测试网络上完成入站和出站服务的测试。</span><span class="sxs-lookup"><span data-stu-id="a5191-445">Preferably, testing of inbound and outbound services should be done on an isolated test network with a test Office 365 tenant.</span></span>

      - <span data-ttu-id="a5191-446">或者，如果客户尚未使用 Office 365 或在试点中，则可以在生产网络上执行测试。</span><span class="sxs-lookup"><span data-stu-id="a5191-446">Alternatively, testing can be performed on a production network if the customer is not yet using Office 365 or is in pilot.</span></span>

      - <span data-ttu-id="a5191-447">此外，还可以在仅为测试和监控而留出的生产中断期间执行测试。</span><span class="sxs-lookup"><span data-stu-id="a5191-447">Alternatively, testing can be performed during a production outage that is set aside for test and monitoring only.</span></span>

      - <span data-ttu-id="a5191-448">或者，可以通过检查每个第3层路由器节点上每个服务的路由来完成测试。</span><span class="sxs-lookup"><span data-stu-id="a5191-448">Alternatively, testing can be done by checking routes for each service on each layer 3 router node.</span></span> <span data-ttu-id="a5191-449">仅当由于缺少物理测试带来风险而不可能进行其他测试时，才应使用此回退。</span><span class="sxs-lookup"><span data-stu-id="a5191-449">This fall back should only be used if no other testing is possible since a lack of physical testing introduces risk.</span></span>

### <a name="build-your-deployment-procedures"></a><span data-ttu-id="a5191-450">生成部署过程</span><span class="sxs-lookup"><span data-stu-id="a5191-450">Build your deployment procedures</span></span>

<span data-ttu-id="a5191-451">您的部署过程应分步向几个阶段中的小组成员进行测试，然后再将其部署到更大的用户组中。</span><span class="sxs-lookup"><span data-stu-id="a5191-451">Your deployment procedures should roll out to small groups of people in stages to allow for testing before deploying to larger groups of people.</span></span> <span data-ttu-id="a5191-452">下面介绍了几种暂存部署的 ExpressRoute 的方法。</span><span class="sxs-lookup"><span data-stu-id="a5191-452">The following are several ways to stage the deployment of ExpressRoute.</span></span>
  
1. <span data-ttu-id="a5191-453">使用 Microsoft 对等互连设置 ExpressRoute，并将路由播发转发到单个主机，仅用于暂存测试目的。</span><span class="sxs-lookup"><span data-stu-id="a5191-453">Set up ExpressRoute with Microsoft peering and have the route advertisements forwarded to a single host only for staged testing purposes.</span></span>

2. <span data-ttu-id="a5191-454">首先，将到 ExpressRoute 网络的播发路由到单个网段，并按网段或区域展开路由广告。</span><span class="sxs-lookup"><span data-stu-id="a5191-454">Advertise routes to the ExpressRoute network to a single network segment at first and expand route advertisements by network segment or region.</span></span>

3. <span data-ttu-id="a5191-455">如果是首次部署 Office 365，请将 ExpressRoute 网络部署用作针对少数用户的试点。</span><span class="sxs-lookup"><span data-stu-id="a5191-455">If deploying Office 365 for the first time, use the ExpressRoute network deployment as a pilot for a small number of people.</span></span>

4. <span data-ttu-id="a5191-456">如果使用代理服务器，则还可以配置一个测试 PAC 文件，以便在添加更多之前将少量用户引导到使用测试和反馈进行 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="a5191-456">If using proxy servers, you can alternatively configure a test PAC file to direct a small number of people to ExpressRoute with testing and feedback before adding more.</span></span>

<span data-ttu-id="a5191-457">您的实施计划应列出必须采取的每个部署过程，或者需要用于部署网络配置的命令。</span><span class="sxs-lookup"><span data-stu-id="a5191-457">Your implementation plan should list each of the deployment procedures that must be taken or commands that need to be used to deploy the networking configuration.</span></span> <span data-ttu-id="a5191-458">当网络中断时间到达时，所做的所有更改都应来自在提前和同行评审的已编写的部署计划。</span><span class="sxs-lookup"><span data-stu-id="a5191-458">When the network outage time arrives all of the changes being made should be from the written deployment plan which was written in advance and peer reviewed.</span></span> <span data-ttu-id="a5191-459">请参阅我们关于 ExpressRoute 的技术配置的指南。</span><span class="sxs-lookup"><span data-stu-id="a5191-459">See our guidance on the technical configuration of ExpressRoute.</span></span>
  
- <span data-ttu-id="a5191-460">如果已更改任何将继续发送电子邮件的本地服务器的 IP 地址，则更新 SPF TXT 记录。</span><span class="sxs-lookup"><span data-stu-id="a5191-460">Updating your SPF TXT records if you've changed IP addresses for any on-premises servers that will continue to send email.</span></span>

- <span data-ttu-id="a5191-461">如果您更改了 IP 地址以适应新的 NAT 配置，则更新本地服务器的任何 DNS 条目。</span><span class="sxs-lookup"><span data-stu-id="a5191-461">Updating any DNS entries for on-premises servers if you've changed IP addresses to accommodate a new NAT configuration.</span></span>

- <span data-ttu-id="a5191-462">确保已订阅 Office 365 终结点通知的 RSS 源，以维护任何路由或代理配置。</span><span class="sxs-lookup"><span data-stu-id="a5191-462">Ensure you've subscribed to the RSS feed for Office 365 endpoint notifications to maintain any routing or proxy configurations.</span></span>

<span data-ttu-id="a5191-463">在您的 ExpressRoute 部署完成后，应执行测试计划中的过程。</span><span class="sxs-lookup"><span data-stu-id="a5191-463">After your ExpressRoute deployment is complete the procedures in the test plan should be executed.</span></span> <span data-ttu-id="a5191-464">应记录每个过程的结果。</span><span class="sxs-lookup"><span data-stu-id="a5191-464">Results for each procedure should be logged.</span></span> <span data-ttu-id="a5191-465">您必须包括在测试计划结果指示实施未成功的情况中回滚到原始生产环境的过程。</span><span class="sxs-lookup"><span data-stu-id="a5191-465">You must include procedures for rolling back to the original production environment in the event the test plan results indicate the implementation was not successful.</span></span>
  
### <a name="build-your-test-procedures"></a><span data-ttu-id="a5191-466">生成测试过程</span><span class="sxs-lookup"><span data-stu-id="a5191-466">Build your test procedures</span></span>

<span data-ttu-id="a5191-467">您的测试过程应包括每个用于 Office 365 的出站和入站网络服务的测试，这两个都将使用 ExpressRoute，而不是将使用的。</span><span class="sxs-lookup"><span data-stu-id="a5191-467">Your testing procedures should include tests for each outbound and inbound network service for Office 365 both that will be using ExpressRoute and ones that will not.</span></span> <span data-ttu-id="a5191-468">这些过程应包括从每个唯一的网络位置（包括公司 LAN 中不在本地的用户）进行测试。</span><span class="sxs-lookup"><span data-stu-id="a5191-468">The procedures should include testing from each unique network location including users who are not on-premises in the corporate LAN.</span></span>
  
<span data-ttu-id="a5191-469">测试活动的一些示例包括以下几个。</span><span class="sxs-lookup"><span data-stu-id="a5191-469">Some examples of test activities include the following.</span></span>
  
1. <span data-ttu-id="a5191-470">从你的本地路由器 Ping 到你的网络操作员路由器。</span><span class="sxs-lookup"><span data-stu-id="a5191-470">Ping from your on-premises router to your network operator router.</span></span>

2. <span data-ttu-id="a5191-471">验证您的本地路由器是否收到 "500 + Office 365" 和 "CRM Online IP 地址" 广告。</span><span class="sxs-lookup"><span data-stu-id="a5191-471">Validate the 500+ Office 365 and CRM Online IP address advertisements are received by your on-premises router.</span></span>

3. <span data-ttu-id="a5191-472">验证您的入站和出站 NAT 在 ExpressRoute 和内部网络之间是否运行。</span><span class="sxs-lookup"><span data-stu-id="a5191-472">Validate your inbound and outbound NAT is operating between ExpressRoute and the internal network.</span></span>

4. <span data-ttu-id="a5191-473">验证从你的路由器播发到你的 NAT 的路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-473">Validate that routes to your NAT are being advertised from your router.</span></span>

5. <span data-ttu-id="a5191-474">验证 ExpressRoute 是否已接受你的播发前缀。</span><span class="sxs-lookup"><span data-stu-id="a5191-474">Validate that ExpressRoute has accepted your advertised prefixes.</span></span>

      - <span data-ttu-id="a5191-475">使用以下 cmdlet 验证对等通告：</span><span class="sxs-lookup"><span data-stu-id="a5191-475">Use the following cmdlet to verify peering advertisements:</span></span>

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. <span data-ttu-id="a5191-476">验证您的公共 NAT IP 范围不会通过任何其他 ExpressRoute 或公共 Internet 网络电路公布给 Microsoft，除非它是更大范围的特定子集，如前面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="a5191-476">Validate your public NAT IP range is not advertised to Microsoft through any other ExpressRoute or public Internet network circuit unless it is a specific subset of a larger range as in the previous example.</span></span>

7. <span data-ttu-id="a5191-477">ExpressRoute 电路配对，验证两个 BGP 会话是否都在运行。</span><span class="sxs-lookup"><span data-stu-id="a5191-477">ExpressRoute circuits are paired, validate that both BGP sessions are running.</span></span>

8. <span data-ttu-id="a5191-478">在 NAT 内部设置单个主机，并使用 ping、tracert 和 tcpping 测试通过新线路连接到主机 outlook.office365.com 的连接。</span><span class="sxs-lookup"><span data-stu-id="a5191-478">Set up a single host on the inside of your NAT and use ping, tracert, and tcpping to test connectivity across the new circuit to the host outlook.office365.com.</span></span> <span data-ttu-id="a5191-479">此外，还可以在镜像端口上使用 Wireshark 或 Microsoft 网络监视器3.4 等工具，以验证是否能够连接到与 outlook.office365.com 关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a5191-479">Alternatively, you could use a tool such as Wireshark or Microsoft Network Monitor 3.4 on a mirrored port to the MSEE to validate you're able to connect to the IP address associated with outlook.office365.com.</span></span>

9. <span data-ttu-id="a5191-480">测试 Exchange Online 的应用程序级功能。</span><span class="sxs-lookup"><span data-stu-id="a5191-480">Test application level functionality for Exchange Online.</span></span>

  - <span data-ttu-id="a5191-481">测试 Outlook 能够连接到 Exchange Online 和发送/接收电子邮件。</span><span class="sxs-lookup"><span data-stu-id="a5191-481">Test Outlook is able to connect to Exchange Online and send/receive email.</span></span>

  - <span data-ttu-id="a5191-482">测试 Outlook 能够使用联机模式。</span><span class="sxs-lookup"><span data-stu-id="a5191-482">Test Outlook is able to use online-mode.</span></span>

  - <span data-ttu-id="a5191-483">测试智能手机连接和发送/接收功能。</span><span class="sxs-lookup"><span data-stu-id="a5191-483">Test smartphone connectivity and send/receive capability.</span></span>

10. <span data-ttu-id="a5191-484">测试 SharePoint Online 的应用程序级功能</span><span class="sxs-lookup"><span data-stu-id="a5191-484">Test application level functionality for SharePoint Online</span></span>

  - <span data-ttu-id="a5191-485">测试 OneDrive for Business 同步客户端。</span><span class="sxs-lookup"><span data-stu-id="a5191-485">Test OneDrive for Business sync client.</span></span>

  - <span data-ttu-id="a5191-486">测试 SharePoint Online web 访问。</span><span class="sxs-lookup"><span data-stu-id="a5191-486">Test SharePoint Online web access.</span></span>

11. <span data-ttu-id="a5191-487">测试 Skype for Business 呼叫方案的应用程序级功能：</span><span class="sxs-lookup"><span data-stu-id="a5191-487">Test application level functionality for Skype for Business calling scenarios:</span></span>

  - <span data-ttu-id="a5191-488">作为已通过身份验证的用户加入会议呼叫 [由最终用户启动的邀请]。</span><span class="sxs-lookup"><span data-stu-id="a5191-488">Join to conference call as authenticated user [invite initiated by end user].</span></span>

  - <span data-ttu-id="a5191-489">邀请用户加入会议呼叫 [从 MCU 发送邀请]。</span><span class="sxs-lookup"><span data-stu-id="a5191-489">Invite user to conference call [invite sent from MCU].</span></span>

  - <span data-ttu-id="a5191-490">使用 Skype for Business web 应用程序作为匿名用户加入会议。</span><span class="sxs-lookup"><span data-stu-id="a5191-490">Join conference as anonymous user using the Skype for Business web application.</span></span>

  - <span data-ttu-id="a5191-491">从有线电脑连接、IP 电话和移动设备加入呼叫。</span><span class="sxs-lookup"><span data-stu-id="a5191-491">Join call from your wired PC connection, IP phone, and mobile device.</span></span>

  - <span data-ttu-id="a5191-492">呼叫联合用户 o 对 PSTN 验证的呼叫：呼叫已完成，呼叫质量是可接受的，连接时间是可接受的。</span><span class="sxs-lookup"><span data-stu-id="a5191-492">Call to federated user o Call to PSTN Validation: call is completed, call quality is acceptable, connection time is acceptable.</span></span>

  - <span data-ttu-id="a5191-493">验证是否已为租户和联合用户的两个成员更新联系人的状态状态。</span><span class="sxs-lookup"><span data-stu-id="a5191-493">Verify presence status for contacts is updated for both members of the tenant and federated users.</span></span>

### <a name="common-problems"></a><span data-ttu-id="a5191-494">常见问题</span><span class="sxs-lookup"><span data-stu-id="a5191-494">Common problems</span></span>

<span data-ttu-id="a5191-495">非对称路由是最常见的实施问题。</span><span class="sxs-lookup"><span data-stu-id="a5191-495">Asymmetric routing is the most common implementation problem.</span></span> <span data-ttu-id="a5191-496">下面是要查找的一些常见来源：</span><span class="sxs-lookup"><span data-stu-id="a5191-496">Here are some common sources to look for:</span></span>
  
- <span data-ttu-id="a5191-497">在没有源 NAT 的情况下使用开放或单层的网络路由拓扑。</span><span class="sxs-lookup"><span data-stu-id="a5191-497">Using an open or flat network routing topology without source NAT in place.</span></span>

- <span data-ttu-id="a5191-498">不使用 SNAT 通过 internet 和 ExpressRoute 连接路由到入站服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-498">Not using SNAT to route to inbound services through both the internet and ExpressRoute connections.</span></span>

- <span data-ttu-id="a5191-499">在广泛部署之前，不在测试网络上测试 ExpressRoute 上的入站服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-499">Not testing inbound services on ExpressRoute on a test network prior to deploying broadly.</span></span>

## <a name="deploying-expressroute-connectivity-through-your-network"></a><span data-ttu-id="a5191-500">通过网络部署 ExpressRoute 连接</span><span class="sxs-lookup"><span data-stu-id="a5191-500">Deploying ExpressRoute connectivity through your network</span></span>
<span data-ttu-id="a5191-501"><a name="testing"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-501"><a name="testing"> </a></span></span>

<span data-ttu-id="a5191-502">一次将部署转移到网络的一个网段，从而逐步推出与网络的不同部分的连接，并为每个新网络分段回滚的计划。</span><span class="sxs-lookup"><span data-stu-id="a5191-502">Stage your deployment to one segment of the network at a time, progressively rolling out the connectivity to different parts of the network with a plan to roll back for each new network segment.</span></span> <span data-ttu-id="a5191-503">如果您的部署与 Office 365 部署保持一致，请首先部署到 Office 365 试点用户并从那里进行扩展。</span><span class="sxs-lookup"><span data-stu-id="a5191-503">If your deployment is aligned with an Office 365 deployment, deploy to your Office 365 pilot users first and extend from there.</span></span>
  
<span data-ttu-id="a5191-504">首先为你的测试，然后用于生产：</span><span class="sxs-lookup"><span data-stu-id="a5191-504">First for your test and then for production:</span></span>
  
- <span data-ttu-id="a5191-505">运行部署步骤以启用 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="a5191-505">Run the deployment steps to enable ExpressRoute.</span></span>

- <span data-ttu-id="a5191-506">测试您看到的网络路由是预期的。</span><span class="sxs-lookup"><span data-stu-id="a5191-506">Test your seeing the network routes are as expected.</span></span>

- <span data-ttu-id="a5191-507">对每个入站和出站服务执行测试。</span><span class="sxs-lookup"><span data-stu-id="a5191-507">Perform testing on each inbound and outbound service.</span></span>

- <span data-ttu-id="a5191-508">如果发现任何问题，则回滚。</span><span class="sxs-lookup"><span data-stu-id="a5191-508">Rollback if you discover any issues.</span></span>

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a><span data-ttu-id="a5191-509">使用测试网络段设置与 ExpressRoute 的测试连接</span><span class="sxs-lookup"><span data-stu-id="a5191-509">Set up a test connection to ExpressRoute with a test network segment</span></span>

<span data-ttu-id="a5191-510">现在，你已完成了纸上的计划，是时候要按小规模测试。</span><span class="sxs-lookup"><span data-stu-id="a5191-510">Now that you have the completed plan on paper it is time to test at a small scale.</span></span> <span data-ttu-id="a5191-511">在此测试中，将在本地网络上建立一个与 Microsoft 对等测试子网的单一 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="a5191-511">In this test you will establish a single ExpressRoute connection with Microsoft Peering to a test subnet on your on-premises network.</span></span> <span data-ttu-id="a5191-512">您可以使用与 test 子网的连接配置一个[试用版 Office 365 租户](https://go.microsoft.com/fwlink/p/?LinkID=403802)，并在测试子网中包含将在生产中使用的所有出站和入站服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-512">You can configure a [trial Office 365 tenant](https://go.microsoft.com/fwlink/p/?LinkID=403802) with connectivity to and from the test subnet and include all outbound and inbound services that you will be using in production in the test subnet.</span></span> <span data-ttu-id="a5191-513">为测试网段设置 DNS 并建立所有入站和出站服务。</span><span class="sxs-lookup"><span data-stu-id="a5191-513">Set up DNS for the test network segment and establish all inbound and outbound services.</span></span> <span data-ttu-id="a5191-514">执行测试计划并确保您熟悉每个服务和路由传播的路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-514">Execute your test plan and ensure that you are familiar with the routing for each service and the route propagation.</span></span>
  
### <a name="execute-the-deployment-and-test-plans"></a><span data-ttu-id="a5191-515">执行部署和测试计划</span><span class="sxs-lookup"><span data-stu-id="a5191-515">Execute the deployment and test plans</span></span>

<span data-ttu-id="a5191-516">完成上述项目后，请查看已完成的区域，并确保您和您的团队在执行部署和测试计划之前已对其进行了查看。</span><span class="sxs-lookup"><span data-stu-id="a5191-516">As you complete the items described above, check off the areas you've completed and ensure you and your team have reviewed them before executing your deployment and testing plans.</span></span>
  
- <span data-ttu-id="a5191-517">网络更改所涉及的出站和入站服务的列表。</span><span class="sxs-lookup"><span data-stu-id="a5191-517">List of outbound and inbound services that are involved in the network change.</span></span>

- <span data-ttu-id="a5191-518">显示 internet 出口和 ExpressRoute "符合我" 位置的全局网络体系结构图。</span><span class="sxs-lookup"><span data-stu-id="a5191-518">Global network architecture diagram showing both internet egress and ExpressRoute meet-me locations.</span></span>

- <span data-ttu-id="a5191-519">演示用于每个部署的服务的不同网络路径的网络路由图。</span><span class="sxs-lookup"><span data-stu-id="a5191-519">Network routing diagram demonstrating the different network paths used for each service deployed.</span></span>

- <span data-ttu-id="a5191-520">包含实施更改和回滚的步骤的部署计划（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="a5191-520">A deployment plan with steps to implement the changes and rollback if needed.</span></span>

- <span data-ttu-id="a5191-521">测试每个 Office 365 和网络服务的测试计划。</span><span class="sxs-lookup"><span data-stu-id="a5191-521">A test plan for testing each Office 365 and network service.</span></span>

- <span data-ttu-id="a5191-522">已完成对入站和出站服务的生产路由的纸张验证。</span><span class="sxs-lookup"><span data-stu-id="a5191-522">Completed paper validation of production routes for inbound and outbound services.</span></span>

- <span data-ttu-id="a5191-523">包含可用性测试的测试网段中的已完成测试。</span><span class="sxs-lookup"><span data-stu-id="a5191-523">A completed test across a test network segment including availability testing.</span></span>

<span data-ttu-id="a5191-524">选择一个足够长的中断时段来运行整个部署计划和测试计划，可在需要时进行故障排除和回滚的时间。</span><span class="sxs-lookup"><span data-stu-id="a5191-524">Choose an outage window that is long enough to run through the entire deployment plan and the test plan, has some time available for troubleshooting and time for rolling back if required.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="a5191-525">由于在 internet 和 ExpressRoute 上路由的复杂性质，建议在此窗口中添加额外的缓冲时间，以处理复杂路由故障排除。</span><span class="sxs-lookup"><span data-stu-id="a5191-525">Due to the complex nature of routing over both the internet and ExpressRoute, it is recommended that additional buffer time is added to this window to handle troubleshooting complex routing.</span></span>
  
### <a name="configure-qos-for-skype-for-business-online"></a><span data-ttu-id="a5191-526">为 Skype for business Online 配置 QoS</span><span class="sxs-lookup"><span data-stu-id="a5191-526">Configure QoS for Skype for Business Online</span></span>

<span data-ttu-id="a5191-527">若要获取 Skype for business Online 的语音和会议优势，必须具备 QoS。</span><span class="sxs-lookup"><span data-stu-id="a5191-527">QoS is necessary to obtain voice and meeting benefits for Skype for Business Online.</span></span> <span data-ttu-id="a5191-528">在确保 ExpressRoute 网络连接不会阻止任何其他 Office 365 服务访问之后，可以配置 QoS。</span><span class="sxs-lookup"><span data-stu-id="a5191-528">You can configure QoS after you have ensured that the ExpressRoute network connection does not block any of your other Office 365 service access.</span></span> <span data-ttu-id="a5191-529">在[Skype For Business Online 中的 ExpressRoute 和 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)一文中介绍了 QoS 的配置。</span><span class="sxs-lookup"><span data-stu-id="a5191-529">Configuration for QoS is described in the article [ExpressRoute and QoS in Skype for Business Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) .</span></span>
  
## <a name="troubleshooting-your-implementation"></a><span data-ttu-id="a5191-530">实现疑难解答</span><span class="sxs-lookup"><span data-stu-id="a5191-530">Troubleshooting your implementation</span></span>
<span data-ttu-id="a5191-531"><a name="troubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="a5191-531"><a name="troubleshooting"> </a></span></span>

<span data-ttu-id="a5191-532">要查找的第一个位置是实施计划中是否错过了此实施指南中的步骤？</span><span class="sxs-lookup"><span data-stu-id="a5191-532">The first place to look is at the steps in this implementation guide, were any missed in your implementation plan?</span></span> <span data-ttu-id="a5191-533">返回并运行进一步的小型网络测试（如果可能）以复制错误并在该处进行调试。</span><span class="sxs-lookup"><span data-stu-id="a5191-533">Go back and run further small network testing if possible to replicate the error and debug it there.</span></span>
  
<span data-ttu-id="a5191-534">确定测试过程中哪些入站或出站服务失败。</span><span class="sxs-lookup"><span data-stu-id="a5191-534">Identify which inbound or outbound services failed during testing.</span></span> <span data-ttu-id="a5191-535">明确获取每个失败的服务的 IP 地址和子网。</span><span class="sxs-lookup"><span data-stu-id="a5191-535">Get specifically the IP addresses and subnets for each of the services which failed.</span></span> <span data-ttu-id="a5191-536">继续执行并浏览纸张上的网络拓扑图，并验证路由。</span><span class="sxs-lookup"><span data-stu-id="a5191-536">Go ahead and walk the network topology diagram on paper and validate the routing.</span></span> <span data-ttu-id="a5191-537">特别验证 ExpressRoute 路由的播发位置，如果可能，请在中断过程中测试该路由（如果有跟踪）。</span><span class="sxs-lookup"><span data-stu-id="a5191-537">Validate specifically where the ExpressRoute routing is advertised to, Test that routing during the outage if possible with traces.</span></span>
  
<span data-ttu-id="a5191-538">对每个客户终结点运行带网络跟踪的 PSPing，并评估源和目标 IP 地址以验证它们是否符合预期。</span><span class="sxs-lookup"><span data-stu-id="a5191-538">Run PSPing with a network trace to each customer endpoint and evaluate source and destination IP addresses to validate that they are as expected.</span></span> <span data-ttu-id="a5191-539">对在端口25上公开的任何邮件主机运行 telnet，并验证 SNAT 是否在预期的情况中隐藏原始源 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a5191-539">Run telnet to any mail host that you expose on port 25 and verify that SNAT is hiding the original source IP address if this is expected.</span></span>
  
<span data-ttu-id="a5191-540">请记住，在使用 ExpressRoute 连接部署 Office 365 时，您需要确保对 ExpressRoute 的网络配置进行了优化设计，并且还优化了网络上的其他组件（如客户端计算机）。</span><span class="sxs-lookup"><span data-stu-id="a5191-540">Keep in mind that while deploying Office 365 with an ExpressRoute connection you'll need to ensure both the network configuration for ExpressRoute is optimally designed and you've also optimized the other components on your network such as client computers.</span></span> <span data-ttu-id="a5191-541">除了使用此规划指南对可能错过的步骤进行故障排除外，我们还编写了[Office 365 的性能故障排除计划](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c)。</span><span class="sxs-lookup"><span data-stu-id="a5191-541">In addition to using this planning guide to troubleshoot the steps you may have missed, we also have written a [Performance troubleshooting plan for Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .</span></span>
  
<span data-ttu-id="a5191-542">以下是可以用于返回的简短链接：[https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)</span><span class="sxs-lookup"><span data-stu-id="a5191-542">Here's a short link you can use to come back: [https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="a5191-543">相关主题</span><span class="sxs-lookup"><span data-stu-id="a5191-543">Related Topics</span></span>

[<span data-ttu-id="a5191-544">评估 Office 365 网络连接</span><span class="sxs-lookup"><span data-stu-id="a5191-544">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
[<span data-ttu-id="a5191-545">适用于 Office 365 的 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="a5191-545">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
  
[<span data-ttu-id="a5191-546">管理 ExpressRoute for Office 365 连接</span><span class="sxs-lookup"><span data-stu-id="a5191-546">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="a5191-547">使用 ExpressRoute for Office 365 路由</span><span class="sxs-lookup"><span data-stu-id="a5191-547">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
  
[<span data-ttu-id="a5191-548">ExpressRoute for Office 365 网络计划</span><span class="sxs-lookup"><span data-stu-id="a5191-548">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
  
[<span data-ttu-id="a5191-549">在 ExpressRoute for Office 365 场景中使用 BGP 社区（预览）</span><span class="sxs-lookup"><span data-stu-id="a5191-549">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)
  
[<span data-ttu-id="a5191-550">Skype for Business Online 中的媒体质量和网络连接性能</span><span class="sxs-lookup"><span data-stu-id="a5191-550">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="a5191-551">优化 Skype for Business Online 网络</span><span class="sxs-lookup"><span data-stu-id="a5191-551">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[<span data-ttu-id="a5191-552">Skype for Business Online 中的 ExpressRoute 和 QoS</span><span class="sxs-lookup"><span data-stu-id="a5191-552">ExpressRoute and QoS in Skype for Business Online</span></span>](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[<span data-ttu-id="a5191-553">使用 ExpressRoute 的呼叫流</span><span class="sxs-lookup"><span data-stu-id="a5191-553">Call flow using ExpressRoute</span></span>](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[<span data-ttu-id="a5191-554">使用基线和性能历史记录优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="a5191-554">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="a5191-555">Office 365 性能疑难解答计划</span><span class="sxs-lookup"><span data-stu-id="a5191-555">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
  
[<span data-ttu-id="a5191-556">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="a5191-556">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="a5191-557">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="a5191-557">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
