---
title: 发展你的云连接网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: 摘要：了解采用云如何要求使用新的网络基础设施投资方法。
ms.openlocfilehash: c8fba120292b89894850312a84fd6067d925a07f
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872253"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a><span data-ttu-id="50682-103">发展你的云连接网络</span><span class="sxs-lookup"><span data-stu-id="50682-103">Evolving your network for cloud connectivity</span></span>

 <span data-ttu-id="50682-104">**摘要：** 了解采用云如何要求使用新的网络基础设施投资方法。</span><span class="sxs-lookup"><span data-stu-id="50682-104">**Summary:** Understand how cloud adoption requires a new approach to network infrastructure investments.</span></span>
  
<span data-ttu-id="50682-p101">云迁移更改公司网络内部和外部的通信量和通信性质。它还会影响降低安全风险的方法。</span><span class="sxs-lookup"><span data-stu-id="50682-p101">Cloud migration changes the volume and nature of traffic flows within and outside a corporate network. It also affects approaches to mitigating security risk.</span></span>
  
- <span data-ttu-id="50682-107">云之前</span><span class="sxs-lookup"><span data-stu-id="50682-107">Before the cloud</span></span>
    
    <span data-ttu-id="50682-p102">大多数网络基础设施的投资都花在确保到本地数据中心的连接可用、可靠且性能卓越上。对于许多组织来说，Internet 连接对内部业务运营不是很重要。网络边界是避免安全隐患的主要防御措施。</span><span class="sxs-lookup"><span data-stu-id="50682-p102">Most networking infrastructure investments were spent on ensuring available, reliable, and performant connectivity to on-premises datacenters. For many organizations, Internet connectivity was not critical for internal business operations. Network boundaries were primary defenses against security breaches.</span></span>
    
- <span data-ttu-id="50682-111">云之后</span><span class="sxs-lookup"><span data-stu-id="50682-111">After the cloud</span></span>
    
    <span data-ttu-id="50682-p103">利用新的和已迁移的工作效率以及在云中运行的 IT 工作负载，基础设施投资从本地数据中心转向 Internet 连接，这一点现在对内部业务运营至关重要。由于标识和数据通过网络和连接点流向 Microsoft 云服务，联合连接从安全策略转向保护标识和数据。</span><span class="sxs-lookup"><span data-stu-id="50682-p103">With new and migrated productivity and IT workloads running in the cloud, infrastructure investments shift from on-premises datacenters to Internet connectivity, which is now critical for internal business operations. Federated connectivity shifts security strategy to protecting identities and data as they flow through the network and points of connectivity to Microsoft cloud services.</span></span>
    
<span data-ttu-id="50682-p104">网络基础设施投资从连接开始。其他投资取决于云服务的类别。</span><span class="sxs-lookup"><span data-stu-id="50682-p104">Network infrastructure investments begin with connectivity. Additional investments depend on the category of cloud service.</span></span>
  
- <span data-ttu-id="50682-p105">**软件即服务 (SaaS)** Microsoft SaaS 服务包括 Office 365、Microsoft Intune 和 Microsoft Dynamics 365。用户能成功利用 SaaS 服务，要依赖于高可用性和高性能的 Internet 连接或直接到 Microsoft 云服务的连接。</span><span class="sxs-lookup"><span data-stu-id="50682-p105">**Software as a Service (SaaS)** Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365. Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>
    
    <span data-ttu-id="50682-p106">网络体系结构侧重于可靠、冗余的连接和足够的带宽。正在进行的投资包括性能监控和调优。</span><span class="sxs-lookup"><span data-stu-id="50682-p106">Network architecture focuses on reliable, redundant connectivity and ample bandwidth. Ongoing investments include performance monitoring and tuning.</span></span>
    
- <span data-ttu-id="50682-p107">**Azure 平台即服务 (PaaS)** 除了 Microsoft SaaS 服务的投资，多站点或地理位置上分散的 PaaS 应用程序可能需要构建 Azure 流量管理器来分配客户端流量。正在进行的投资包括性能和流量分布监控以及故障转移测试。</span><span class="sxs-lookup"><span data-stu-id="50682-p107">**Azure Platform as a Service (PaaS)** In addition to the investments for Microsoft SaaS services, multi-site or geographically distributed PaaS applications might require architecting Azure Traffic Manager to distribute client traffic. Ongoing investments include performance and traffic distribution monitoring and failover testing.</span></span>
    
- <span data-ttu-id="50682-p108">**Azure 基础结构即服务 (IaaS)** 除了 Microsoft SaaS 和 PaaS 服务的投资，IaaS 中正在运行的 IT 工作负载要求设计和配置 Azure 虚拟网络，这些网络用于承载虚拟机、到虚拟机上运行的应用程序的安全连接、路由、IP 地址、DNS 以及负载平衡。正在进行的投资包括性能和安全监控以及疑难解答。</span><span class="sxs-lookup"><span data-stu-id="50682-p108">**Azure Infrastructure as a Service (IaaS)** In addition to the investments for Microsoft SaaS and PaaS services, running IT workloads in IaaS requires the design and configuration of Azure virtual networks that host virtual machines, secure connectivity to applications running on them, routing, IP addressing, DNS, and load balancing. Ongoing investments include performance and security monitoring and troubleshooting.</span></span>

<span data-ttu-id="50682-p109">[Microsoft 365](https://www.microsoft.com/microsoft-365)是 Office 365、 企业管理 + 安全 (EMS) 和 Windows 10 的组合。Microsoft 365 结合使用多个 SaaS 和完整、 智能解决方案，使所有人都是创作的 Azure 服务和安全地协同工作。</span><span class="sxs-lookup"><span data-stu-id="50682-p109">[Microsoft 365](https://www.microsoft.com/microsoft-365) is a combination of Office 365, Enterprise Management + Security (EMS), and Windows 10. Microsoft 365 combines multiple SaaS and Azure services for a complete, intelligent solution that empowers everyone to be creative and work together securely.</span></span>
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a><span data-ttu-id="50682-126">云中成功的网络投资领域</span><span class="sxs-lookup"><span data-stu-id="50682-126">Areas of networking investment for success in the cloud</span></span>

<span data-ttu-id="50682-p110">企业组织从采用系统的方法来优化 Intranet 中和到 Internet 的网络吞吐量中获益。你可能还会从 ExpressRoute 连接中获益。</span><span class="sxs-lookup"><span data-stu-id="50682-p110">Enterprise organizations benefit from taking a methodical approach to optimizing network throughput across your intranet and to the Internet. You might also benefit from an ExpressRoute connection.</span></span>
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a><span data-ttu-id="50682-129">优化 Intranet 到边缘网络的连接</span><span class="sxs-lookup"><span data-stu-id="50682-129">Optimize intranet connectivity to your edge network</span></span>

<span data-ttu-id="50682-p111">多年来，许多组织已经优化了在内部数据中心中运行的应用程序的 Intranet 连接和性能。由于生产效率和 Microsoft 云中运行的 IT 工作负载，必须额外投资以确保连接的高可用性，还要确保边缘网络和 Intranet 用户之间的通信性能是最佳的。</span><span class="sxs-lookup"><span data-stu-id="50682-p111">Over the years, many organizations have optimized intranet connectivity and performance to applications running in on-premises datacenters. With productivity and IT workloads running in the Microsoft cloud, additional investment must ensure high connectivity availability and that traffic performance between your edge network and your intranet users is optimal.</span></span>
  
### <a name="optimize-throughput-at-your-edge-network"></a><span data-ttu-id="50682-132">优化边缘网络的吞吐量</span><span class="sxs-lookup"><span data-stu-id="50682-132">Optimize throughput at your edge network</span></span>

<span data-ttu-id="50682-133">由于你更多的日常工作效率流量传输至云，你应该仔细检查边缘网络的一套系统，确保它们是最新的，可以提供高可用性并有足够的容量来满足峰值负载。</span><span class="sxs-lookup"><span data-stu-id="50682-133">As more of your day-to-day productivity traffic travels to the cloud, you should closely examine the set of systems at your edge network to ensure that they are current, provide high availability, and have sufficient capacity to meet peak loads.</span></span>
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a><span data-ttu-id="50682-134">对于 Azure、Office 365，和 Dynamics 365 的高级 SLA，请使用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="50682-134">For a high SLA to Azure, Office 365, and Dynamics 365, use ExpressRoute</span></span>

<span data-ttu-id="50682-p112">尽管您可以从边缘网络使用您当前的 Internet 连接，从 Microsoft 云服务之间的通信必须与其他转到 Internet 的 intranet 流量共享管道。此外，您到 Microsoft 云服务的通信受制于 Internet 通信拥塞。</span><span class="sxs-lookup"><span data-stu-id="50682-p112">Although you can use your current Internet connection from your edge network, traffic to and from Microsoft cloud services must share the pipe with other intranet traffic going to the Internet. Additionally, your traffic to Microsoft cloud services is subject to Internet traffic congestion.</span></span>
  
<span data-ttu-id="50682-137">为了实现高级 SLA 和最佳性能，请使用 ExpressRoute，这是你的网络与 Azure、Office 365、Dynamics 365 或所有这三个系统之间的专用 WAN 连接。</span><span class="sxs-lookup"><span data-stu-id="50682-137">For a high SLA and the best performance, use ExpressRoute, a dedicated WAN connection between your network and Azure, Office 365, Dynamics 365, or all three.</span></span> 
  
<span data-ttu-id="50682-p113">ExpressRoute 可以利用你现有的网络提供程序来提供专用连接。通过 ExpressRoute 连接的资源就好像它们位于你的 WAN 中一样，甚至对于地理位置分散的组织也是如此。</span><span class="sxs-lookup"><span data-stu-id="50682-p113">ExpressRoute can leverage your existing network provider for a dedicated connection. Resources connected by ExpressRoute appear as if they are on your WAN, even for geographically-distributed organizations.</span></span>
  
<span data-ttu-id="50682-140">有关详细信息，请参阅[面向 Microsoft 云连接的 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="50682-140">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
## <a name="scope-of-network-investments"></a><span data-ttu-id="50682-141">网络投资的范围</span><span class="sxs-lookup"><span data-stu-id="50682-141">Scope of network investments</span></span>

<span data-ttu-id="50682-p114">网络投资的范围取决于云服务的类别。在 Microsoft 云中投资将最大限度地利用网络团队的投资。IaaS 服务的投资适用于所有投资领域。</span><span class="sxs-lookup"><span data-stu-id="50682-p114">The scope of network investments depend on the category of cloud service. Investing across Microsoft's cloud maximizes the investments of networking teams. For example, investments for IaaS services apply to all investment areas.</span></span>
  
|||||
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="50682-145">投资领域</span><span class="sxs-lookup"><span data-stu-id="50682-145">Investment area</span></span>  <br/> |<span data-ttu-id="50682-146">SaaS</span><span class="sxs-lookup"><span data-stu-id="50682-146">SaaS</span></span>  <br/> |<span data-ttu-id="50682-147">PaaS</span><span class="sxs-lookup"><span data-stu-id="50682-147">PaaS</span></span>  <br/> |<span data-ttu-id="50682-148">IaaS</span><span class="sxs-lookup"><span data-stu-id="50682-148">IaaS</span></span>  <br/> |
|<span data-ttu-id="50682-149">构建可靠、冗余且具有足够带宽的 Internet 连接</span><span class="sxs-lookup"><span data-stu-id="50682-149">Architect reliable, redundant Internet connectivity with ample bandwidth</span></span>  <br/> |<span data-ttu-id="50682-150">应用</span><span class="sxs-lookup"><span data-stu-id="50682-150">Applies</span></span>  <br/> |<span data-ttu-id="50682-151">应用</span><span class="sxs-lookup"><span data-stu-id="50682-151">Applies</span></span>  <br/> |<span data-ttu-id="50682-152">应用</span><span class="sxs-lookup"><span data-stu-id="50682-152">Applies</span></span>  <br/> |
|<span data-ttu-id="50682-153">监控和调整 Internet 吞吐量以提高性能</span><span class="sxs-lookup"><span data-stu-id="50682-153">Monitor and tune Internet throughput for performance</span></span>  <br/> |<span data-ttu-id="50682-154">应用</span><span class="sxs-lookup"><span data-stu-id="50682-154">Applies</span></span>  <br/> |<span data-ttu-id="50682-155">应用</span><span class="sxs-lookup"><span data-stu-id="50682-155">Applies</span></span>  <br/> |<span data-ttu-id="50682-156">应用</span><span class="sxs-lookup"><span data-stu-id="50682-156">Applies</span></span>  <br/> |
|<span data-ttu-id="50682-157">解决 Internet 连接和吞吐量问题</span><span class="sxs-lookup"><span data-stu-id="50682-157">Troubleshoot Internet connectivity and throughput issues</span></span>  <br/> |<span data-ttu-id="50682-158">应用</span><span class="sxs-lookup"><span data-stu-id="50682-158">Applies</span></span>  <br/> |<span data-ttu-id="50682-159">应用</span><span class="sxs-lookup"><span data-stu-id="50682-159">Applies</span></span>  <br/> |<span data-ttu-id="50682-160">应用</span><span class="sxs-lookup"><span data-stu-id="50682-160">Applies</span></span>  <br/> |
|<span data-ttu-id="50682-161">设计 Azure 流量管理器，对不同终结点的流量执行负载平衡</span><span class="sxs-lookup"><span data-stu-id="50682-161">Design Azure Traffic Manager to load balance traffic to different endpoints</span></span>  <br/> ||<span data-ttu-id="50682-162">应用</span><span class="sxs-lookup"><span data-stu-id="50682-162">Applies</span></span>  <br/> |<span data-ttu-id="50682-163">应用</span><span class="sxs-lookup"><span data-stu-id="50682-163">Applies</span></span>  <br/> |
|<span data-ttu-id="50682-164">构建到 Azure 虚拟网络的可靠、冗余的高性能连接</span><span class="sxs-lookup"><span data-stu-id="50682-164">Architect reliable, redundant, and performant connectivity to Azure virtual networks</span></span>  <br/> |||<span data-ttu-id="50682-165">应用</span><span class="sxs-lookup"><span data-stu-id="50682-165">Applies</span></span>  <br/> |
|<span data-ttu-id="50682-166">设计到 Azure 虚拟机的安全连接</span><span class="sxs-lookup"><span data-stu-id="50682-166">Design secure connectivity to Azure virtual machines</span></span>  <br/> |||<span data-ttu-id="50682-167">应用</span><span class="sxs-lookup"><span data-stu-id="50682-167">Applies</span></span>  <br/> |
|<span data-ttu-id="50682-168">设计并实施本地位置和虚拟网络之间的路由</span><span class="sxs-lookup"><span data-stu-id="50682-168">Design and implement routing between on-premises locations and virtual networks</span></span>  <br/> |||<span data-ttu-id="50682-169">应用</span><span class="sxs-lookup"><span data-stu-id="50682-169">Applies</span></span>  <br/> |
|<span data-ttu-id="50682-170">构建并实施内部和面向 Internet 的 IT 工作负载的负载平衡</span><span class="sxs-lookup"><span data-stu-id="50682-170">Architect and implement load balancing for internal and Internet-facing IT workloads</span></span>  <br/> |||<span data-ttu-id="50682-171">应用</span><span class="sxs-lookup"><span data-stu-id="50682-171">Applies</span></span>  <br/> |
|<span data-ttu-id="50682-172">解决虚拟机连接和吞吐量问题</span><span class="sxs-lookup"><span data-stu-id="50682-172">Troubleshoot virtual machine connectivity and throughput issues</span></span>  <br/> |||<span data-ttu-id="50682-173">应用</span><span class="sxs-lookup"><span data-stu-id="50682-173">Applies</span></span>  <br/> |
   
## <a name="next-step"></a><span data-ttu-id="50682-174">后续步骤</span><span class="sxs-lookup"><span data-stu-id="50682-174">Next step</span></span>

[<span data-ttu-id="50682-175">Microsoft 云连接的公共元素</span><span class="sxs-lookup"><span data-stu-id="50682-175">Common elements of Microsoft cloud connectivity</span></span>](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="50682-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50682-176">See also</span></span>

[<span data-ttu-id="50682-177">面向企业架构师的 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="50682-177">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="50682-178">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="50682-178">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



