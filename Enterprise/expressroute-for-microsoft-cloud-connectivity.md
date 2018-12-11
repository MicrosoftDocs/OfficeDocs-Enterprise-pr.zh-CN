---
title: 面向 Microsoft 云连接的 ExpressRoute
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/05/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 摘要： 了解 ExpressRoute 如何帮助你更快、更可靠地与 Microsoft 云服务和平台相连接。
ms.openlocfilehash: a72533673618af01fc2ce6dcc44f84cf94afc215
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213969"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="32396-103">面向 Microsoft 云连接的 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="32396-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="32396-104">**摘要：** 了解 ExpressRoute 如何帮助你更快、更可靠地与 Microsoft 云服务和平台相连接。</span><span class="sxs-lookup"><span data-stu-id="32396-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="32396-105">ExpressRoute 提供了到 Microsoft 云的单独、专用、高吞吐量的网络连接。</span><span class="sxs-lookup"><span data-stu-id="32396-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="32396-106">ExpressRoute 到 Microsoft 云</span><span class="sxs-lookup"><span data-stu-id="32396-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="32396-107">下面是在没有 ExpressRoute 连接的情况下到 Microsoft 云的网络路径。</span><span class="sxs-lookup"><span data-stu-id="32396-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="32396-108">**图 1：没有 ExpressRoute 的网络路径**</span><span class="sxs-lookup"><span data-stu-id="32396-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![图 1：没有 ExpressRoute 的网络路径](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="32396-p101">图 1 显示内部部署网络与 Microsoft 云之间的典型路径。内部部署网络边缘通过到 ISP 的 WAN 链接连接到 Internet。然后，流量流经 Internet 到达 Microsoft 云的边缘。Microsoft 云内的云产品包括 Office 365、Microsoft Azure、Microsoft Intune 和 Dynamics 365。组织的用户可以位于内部部署网络或 Internet。</span><span class="sxs-lookup"><span data-stu-id="32396-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="32396-115">如果没有 ExpressRoute 连接，你唯一可以控制的到 Microsoft 云的流量路径部分（并且与服务提供商有关系）是内部部署网络边缘与 ISP 之间的链接。</span><span class="sxs-lookup"><span data-stu-id="32396-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="32396-116">受限于中断、流量拥塞和恶意用户监视，ISP 与 Microsoft 云边缘之间的路径是 Internet 中尽力而为的传送系统。</span><span class="sxs-lookup"><span data-stu-id="32396-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="32396-117">Internet 中的用户，例如漫游或远程用户，通过 Internet 将他们的流量发送到 Microsoft 云。</span><span class="sxs-lookup"><span data-stu-id="32396-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="32396-118">以下是在有 ExpressRoute 连接的情况下到 Microsoft 云的网络路径。</span><span class="sxs-lookup"><span data-stu-id="32396-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="32396-119">**图 2：有 ExpressRoute 的网络路径**</span><span class="sxs-lookup"><span data-stu-id="32396-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![图 2：有 ExpressRoute 的网络路径](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="32396-p102">图 2 显示了两个网络路径。到 Microsoft Intune 的流量与普通 Internet 流量的路径相同。Office 365、Microsoft Azure 和 Dynamics 365 的流量经过 ExpressRoute 连接，这是内部部署网络边缘与 Microsoft 云边缘之间的专用路径。</span><span class="sxs-lookup"><span data-stu-id="32396-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="32396-p103">ExpressRoute 连接，您现在可以控制，通过与服务提供商的关系，通过从您边缘到 Microsoft 的整个流量路径云边缘。可预测的性能和[99.95%运行时间 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/)可以提供此连接。</span><span class="sxs-lookup"><span data-stu-id="32396-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="32396-p104">基于服务提供商到 Office 365、Azure 和 Dynamics 365 服务的连接，现在可以依靠可预测的吞吐量和延迟。目前不支持 ExpressRoute 到 Microsoft Intune 的连接。</span><span class="sxs-lookup"><span data-stu-id="32396-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="32396-128">通过 ExpressRoute 连接发送的流量不再受限于 Internet 中断、流量拥塞和监视。</span><span class="sxs-lookup"><span data-stu-id="32396-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="32396-p105">Internet 中的用户，例如漫游或远程用户，仍通过 Internet 将他们的流量发送到 Microsoft 云。在 Azure IaaS 中托管的业务应用程序 Intranet 线的流量是一个例外情况，此类流量是通过到内部部署网络的远程访问连接的 ExpressRoute 连接发送的。</span><span class="sxs-lookup"><span data-stu-id="32396-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="32396-131">即使有 ExpressRoute 连接，一些流量仍然通过 Internet 发送，例如 DNS 查询、证书吊销列表检查和内容交付网络 (CDN) 请求。</span><span class="sxs-lookup"><span data-stu-id="32396-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="32396-132">有关详细信息，请参阅下列更多资源：</span><span class="sxs-lookup"><span data-stu-id="32396-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="32396-133">面向 Office 365 的 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="32396-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- <span data-ttu-id="32396-134">[ExpressRoute for Azure](https://azure.microsoft.com/services/expressroute/)（面向 Azure 的 ExpressRoute）</span><span class="sxs-lookup"><span data-stu-id="32396-134">[ExpressRoute for Azure](https://azure.microsoft.com/services/expressroute/)</span></span>
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="32396-135">面向 Azure 的 ExpressRoute 的优点</span><span class="sxs-lookup"><span data-stu-id="32396-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="32396-136">下面是使用面向基于 Azure 的云服务的 ExpressRoute 的一些优点：</span><span class="sxs-lookup"><span data-stu-id="32396-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="32396-p106">**可预知的性能：** 通过到 Microsoft 云边缘的专用路径，你的性能不会受限于 Internet 提供商中断和 Internet 流量高峰。你可以确定并让提供商负责到 Microsoft 云的吞吐量和延迟 SLA。</span><span class="sxs-lookup"><span data-stu-id="32396-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="32396-p107">**流量的数据隐私：** 通过专用 ExpressRoute 连接发送的流量不会受限于恶意用户的 Internet 监视或数据包捕获和分析。这与使用基于多协议标签交换 (MPLS) 的 WAN 链接一样安全。</span><span class="sxs-lookup"><span data-stu-id="32396-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="32396-141">**高吞吐量连接：** 由于 Exchange 提供商和网络服务提供商提供的广泛的 ExpressRoute 连接支持，你最多可以获得 Microsoft 云的 10 Gbps 链接。</span><span class="sxs-lookup"><span data-stu-id="32396-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="32396-142">**降低某些配置的成本：** 虽然 ExpressRoute 连接花费额外的成本，但在某些情况下，与在组织的多个地点增加 Internet 容量相比，一次 ExpressRoute 连接花费的成本更低，可以为 Microsoft 云服务提供足够的吞吐量。</span><span class="sxs-lookup"><span data-stu-id="32396-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="32396-p108">ExpressRoute 连接不能保证每一种配置的性能都会提高。通过低带宽 ExpressRoute 连接实现的性能比高带宽 Internet 连接低，在后一种情况下，与区域性 Microsoft 数据中心仅隔几个跃点。</span><span class="sxs-lookup"><span data-stu-id="32396-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="32396-145">有关使用适用于 Office 365 的 ExpressRoute，请参阅[适用于 Office 365 的 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)。</span><span class="sxs-lookup"><span data-stu-id="32396-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="32396-146">ExpressRoute 连接模型</span><span class="sxs-lookup"><span data-stu-id="32396-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="32396-147">表 1 显示了用于 ExpressRoute 连接的三种主要连接模型。</span><span class="sxs-lookup"><span data-stu-id="32396-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="32396-148">**在云交换中归置**</span><span class="sxs-lookup"><span data-stu-id="32396-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="32396-149">**点到点的以太网**</span><span class="sxs-lookup"><span data-stu-id="32396-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="32396-150">**任意对任意的 (IP VPN) 连接**</span><span class="sxs-lookup"><span data-stu-id="32396-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![ExpressRoute 连接模型：在云交换中归置](media/Network-Poster/ER-Conn1.png)|![ExpressRoute 连接模型：点到点的以太网](media/Network-Poster/ER-Conn2.png)|![ExpressRoute 连接模型：任意对任意的 (IP VPN) 连接](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="32396-154">如果你的数据中心与云交换共同位于某设施内，你可以通过归置提供程序的以太网交换订购到 Microsoft 云的虚拟交叉连接。</span><span class="sxs-lookup"><span data-stu-id="32396-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="32396-155">如果你的数据中心位于你的场所，你可以使用点对点以太网链路连接到 Microsoft 云。</span><span class="sxs-lookup"><span data-stu-id="32396-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="32396-156">如果你已使用 IP VPN (MPLS) 提供程序连接组织的站点，到 Microsoft 云的 ExpressRoute 连接可以用作专用 WAN 中的另一个位置。</span><span class="sxs-lookup"><span data-stu-id="32396-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="32396-157">**表 1：ExpressRoute 连接模型**</span><span class="sxs-lookup"><span data-stu-id="32396-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="32396-158">ExpressRoute 与 Microsoft 云服务的对等关系</span><span class="sxs-lookup"><span data-stu-id="32396-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="32396-p109">一个 ExpressRoute 连接最多支持三个不同的边界网关协议 (BGP) 与 Microsoft 云不同部分的对等关系。BPG 使用对等关系建立信任和交换路由信息。</span><span class="sxs-lookup"><span data-stu-id="32396-p109">A single ExpressRoute connection supports up to three different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="32396-161">**图 3：单个 ExpressRoute 连接中的三个不同的 BGP 关系**</span><span class="sxs-lookup"><span data-stu-id="32396-161">**Figure 3: The three different BGP relationships in a single ExpressRoute connection**</span></span>

![图 3：单次 ExpressRoute 连接中的三个不同的 BGP 关系](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="32396-p110">图 3 显示了从本地网络 ExpressRoute 连接。ExpressRoute 连接都有三个逻辑的对等关系。Microsoft 对等关系转到 Microsoft SaaS 服务，包括 Office 365 和 Dynamcs CRM Online。公共的对等关系转到 Azure PaaS 服务。专用的对等关系转到 Azure IaaS 和承载虚拟机的虚拟网络网关。</span><span class="sxs-lookup"><span data-stu-id="32396-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection has three logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365 and Dynamcs CRM Online. A public peering relationship goes to Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="32396-168">Microsoft 对等 BGP 关系：</span><span class="sxs-lookup"><span data-stu-id="32396-168">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="32396-169">是从 DMZ 中的某个路由器到 Office 365 和 Dynamics 365 服务的公用地址。</span><span class="sxs-lookup"><span data-stu-id="32396-169">Is from a router in your DMZ to the public addresses of Office 365 and Dynamics 365 services.</span></span> 
    
- <span data-ttu-id="32396-170">支持双向启动的通信。</span><span class="sxs-lookup"><span data-stu-id="32396-170">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="32396-171">公共对等 BGP 关系：</span><span class="sxs-lookup"><span data-stu-id="32396-171">The public peering BGP relationship:</span></span>
  
- <span data-ttu-id="32396-172">是从 DMZ 中的某个路由器到 Azure 服务的公用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="32396-172">Is from a router in your DMZ to the public IP addresses of Azure services.</span></span>
    
- <span data-ttu-id="32396-p111">仅支持从内部部署系统中单向启动的通信。对等关系不支持从 Azure PaaS 服务启动的通信。</span><span class="sxs-lookup"><span data-stu-id="32396-p111">Supports unidirectional-initiated communication from on-premises systems only. The peering relationship does not support communication initiated from Azure PaaS services.</span></span>
    
<span data-ttu-id="32396-175">专用的对等 BGP 关系：</span><span class="sxs-lookup"><span data-stu-id="32396-175">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="32396-176">是从组织网络边缘上的某个路由器到分配给 Azure VNets 的专用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="32396-176">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="32396-177">支持双向启动的通信。</span><span class="sxs-lookup"><span data-stu-id="32396-177">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="32396-178">是从组织网络到 Microsoft 云的扩展，配有内部一致的寻址和路由。</span><span class="sxs-lookup"><span data-stu-id="32396-178">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="32396-179">通过 ExpressRoute 的应用程序部署和流量的示例</span><span class="sxs-lookup"><span data-stu-id="32396-179">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="32396-p112">流量如何流经 ExpressRoute 连接和在 Microsoft 云中传输，相当于来源与目标之间的路径跃点的路由，是一种应用程序的行为。下面是在 Azure 虚拟机上运行的应用程序的一个示例，它通过站点到站点 VPN 连接访问内部部署 SharePoint 场。</span><span class="sxs-lookup"><span data-stu-id="32396-p112">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="32396-182">**图 4：Azure 虚拟机上的访问本地 SharePoint 场的应用程序**</span><span class="sxs-lookup"><span data-stu-id="32396-182">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![图 4：Azure 虚拟机上的访问本地 SharePoint 场的应用程序](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="32396-184">图 4 显示了内部部署 SharePoint 场、内部部署网络和 Azure IaaS 中的虚拟网络之间的站点到站点 VPN 连接、作为 Azure IaaS 虚拟机运行的应用程序服务器，以及应用程序服务器和 SharePoint 场之间的流量。</span><span class="sxs-lookup"><span data-stu-id="32396-184">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="32396-185">应用程序使用内部部署 DNS 查找 SharePoint 场的 IP 地址，所有流量都要通过站点到站点 VPN 连接。</span><span class="sxs-lookup"><span data-stu-id="32396-185">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="32396-186">该组织将内部部署 SharePoint 场迁移到了 Office 365 中的 SharePoint Online 并部署了 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="32396-186">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="32396-187">**图 5：将本地 SharePoint 场移至 SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="32396-187">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![图 5：将本地 SharePoint 场迁移到 SharePoint Online](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="32396-p113">图 5 显示将带有对等关系的 ExpressRoute 连接添加到 Microsoft SaaS 和 Office 365 以及 Azure IaaS 中，其中包含虚拟网络上的应用程序服务器。SharePoint 内部部署场已迁移至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="32396-p113">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="32396-191">具有 Microsoft 和专用对等关系：</span><span class="sxs-lookup"><span data-stu-id="32396-191">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="32396-192">从 Azure 虚拟网络网关中，内部部署位置可通过 ExpressRoute 连接提供。</span><span class="sxs-lookup"><span data-stu-id="32396-192">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="32396-193">从 Office 365 订阅中，边缘设备的公用 IP 地址（如代理服务器）可通过 ExpressRoute 连接提供。</span><span class="sxs-lookup"><span data-stu-id="32396-193">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="32396-194">从内部部署网络边缘中，Azure VNet 的专用 IP 地址和 Office 365 的公用 IP 地址可通过 ExpressRoute 连接提供。</span><span class="sxs-lookup"><span data-stu-id="32396-194">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="32396-195">当应用程序访问 SharePoint Online 的 URL 时，它通过 ExpressRoute 连接将其流量转发到边缘的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="32396-195">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="32396-p114">当代理服务器找到 SharePoint Online 的 IP 地址时，它将通过 ExpressRoute 连接转发回流量。响应流量通过反向路径。</span><span class="sxs-lookup"><span data-stu-id="32396-p114">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="32396-198">**图 6：SharePoint 场迁移到 Office 365 中的 SharePoint Online 时的流量**</span><span class="sxs-lookup"><span data-stu-id="32396-198">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![图 6：SharePoint 场迁移到 Office 365 中的 SharePoint Online 时的流量](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="32396-200">图 6 显示了应用程序服务器和 Office 365 中的 SharePoint Online 之间的流量如何通过专用的对等关系从应用程序服务器流到内部部署网络边缘，然后通过 Microsoft 对等关系从边缘流到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="32396-200">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="32396-201">其结果是出现 Hairpinning 模式，这是路由和应用程序行为导致的后果。</span><span class="sxs-lookup"><span data-stu-id="32396-201">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="32396-202">ExpressRoute 和 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="32396-202">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="32396-203">ExpressRoute 连接具有两个不同的版本：ExpressRoute 和 ExpressRoute Premium。</span><span class="sxs-lookup"><span data-stu-id="32396-203">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="32396-204">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="32396-204">ExpressRoute</span></span>

<span data-ttu-id="32396-205">组织网络与 Microsoft 数据中心之间的流量的流动方式取决于下列各项：</span><span class="sxs-lookup"><span data-stu-id="32396-205">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="32396-206">你的位置。</span><span class="sxs-lookup"><span data-stu-id="32396-206">Your locations.</span></span>
    
- <span data-ttu-id="32396-207">Microsoft 云对等位置（连接到 Microsoft 边缘的物理位置）。</span><span class="sxs-lookup"><span data-stu-id="32396-207">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="32396-208">Microsoft 数据中心位置。</span><span class="sxs-lookup"><span data-stu-id="32396-208">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="32396-209">Microsoft 数据中心和云对等位置都连接到 Microsoft 云网络。</span><span class="sxs-lookup"><span data-stu-id="32396-209">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="32396-p115">创建到 Microsoft 云对等位置的 ExpressRoute 连接时，将你连接到 Microsoft 云网络以及同一个洲的所有 Microsoft 数据中心位置。云对等位置和目标 Microsoft 数据中心之间的流量通过 Microsoft 云网络传送。</span><span class="sxs-lookup"><span data-stu-id="32396-p115">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="32396-212">这可能会导致任意对任意连接模型的本地 Microsoft 数据中心的传送达不到最佳状态。</span><span class="sxs-lookup"><span data-stu-id="32396-212">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="32396-213">**使用的单个 ExpressRoute 连接的地理位置分散的组织的图 7： 示例**</span><span class="sxs-lookup"><span data-stu-id="32396-213">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![使用的单个 ExpressRoute 连接的地理位置分散的组织的图 7： 示例](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="32396-p116">图 7 显示了具有两个位置的组织：美国西北部的位置 1 和东北部的位置 2。它们由任意对任意 WAN 提供程序连接。该组织还有到西海岸的 Microsoft 对等位置的 ExpressRoute 连接。来自东北部的位置 2 且发往东海岸数据中心的流量，必须一直流经组织的 WAN 直到西海岸、Microsoft 对等位置，然后通过 Microsoft 云网络流经全国，返回东海岸数据中心。</span><span class="sxs-lookup"><span data-stu-id="32396-p116">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="32396-219">为实现最佳的传送，使用到区域性 Microsoft 云对等位置的多个 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="32396-219">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="32396-220">**图 8：使用多个 ExpressRoute 连接实现到区域性数据中心的最佳传送**</span><span class="sxs-lookup"><span data-stu-id="32396-220">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![图 8：使用多个 ExpressRoute 连接实现到区域性数据中心的最佳传送](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="32396-p117">图 8 显示了使用到本地 Microsoft 对等位置的两个 ExpressRoute 连接的同一组织，一个连接针对一个位置。在此配置中，来自东北部的位置 2 且发往东海岸数据中心的流量，会直接流至东海岸的对等位置、Microsoft 云网络，然后再到东海岸数据中心。</span><span class="sxs-lookup"><span data-stu-id="32396-p117">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="32396-224">多个 ExpressRoute 连接可以：</span><span class="sxs-lookup"><span data-stu-id="32396-224">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="32396-225">提高本地 Microsoft 数据中心位置的性能。</span><span class="sxs-lookup"><span data-stu-id="32396-225">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="32396-226">在本地 ExpressRoute 连接不可用时提高 Microsoft 云的可用性。</span><span class="sxs-lookup"><span data-stu-id="32396-226">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="32396-p118">这适用于在同一个洲的组织。但是，到该组织所在洲之外的 Microsoft 数据中心的流量将通过 Internet 传送。</span><span class="sxs-lookup"><span data-stu-id="32396-p118">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="32396-229">对于通过 Microsoft 云网络的洲际流量，则必须使用 ExpressRoute Premium 连接。</span><span class="sxs-lookup"><span data-stu-id="32396-229">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="32396-230">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="32396-230">ExpressRoute Premium</span></span>

<span data-ttu-id="32396-231">对于分布在各洲的组织，你可以使用 ExpressRoute Premium。</span><span class="sxs-lookup"><span data-stu-id="32396-231">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="32396-p119">通过 ExpressRoute Premium，可以从任何洲的任何 Microsoft 对等位置到达任何洲的任何 Microsoft 数据中心。洲之间的流量通过 Microsoft 云网络传送。</span><span class="sxs-lookup"><span data-stu-id="32396-p119">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="32396-234">通过多个 ExpressRoute Premium 连接，你可以：</span><span class="sxs-lookup"><span data-stu-id="32396-234">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="32396-235">提高洲本地 Microsoft 数据中心位置的性能。</span><span class="sxs-lookup"><span data-stu-id="32396-235">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="32396-236">在本地 ExpressRoute 连接不可用时提高全局 Microsoft 云的可用性。</span><span class="sxs-lookup"><span data-stu-id="32396-236">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="32396-237">基于 Office 365 ExpressRoute 连接需要 ExpressRoute Premium。</span><span class="sxs-lookup"><span data-stu-id="32396-237">ExpressRoute Premium is required for Office 365-based ExpressRoute connections.</span></span>
  
<span data-ttu-id="32396-238">**图 9：全球范围内的 Microsoft 云网络**</span><span class="sxs-lookup"><span data-stu-id="32396-238">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![图 9：全球范围内的 Microsoft 云网络](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="32396-p120">图 9 显示了全球范围的 Microsoft 云网络的逻辑图，其中网络跨越世界各洲和区域以及它们之间的互连。每个洲都包含部分 Microsoft 云网络，全球企业从其区域中心办事处创建到本地 Microsoft 对等位置的 ExpressRoute Premium 连接。</span><span class="sxs-lookup"><span data-stu-id="32396-p120">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="32396-242">对于区域办事处，适当的 Office 365 流量：</span><span class="sxs-lookup"><span data-stu-id="32396-242">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="32396-243">通过该洲内的 Microsoft 云网络传送至 Office 365 洲数据中心。</span><span class="sxs-lookup"><span data-stu-id="32396-243">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="32396-244">通过洲际 Microsoft 云网络传送至另一个洲的Office 365 数据中心。</span><span class="sxs-lookup"><span data-stu-id="32396-244">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="32396-245">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="32396-245">For more information, see:</span></span>
  
- <span data-ttu-id="32396-246">[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer/)（Azure ExpressRoute for Office 365 培训）</span><span class="sxs-lookup"><span data-stu-id="32396-246">[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer/)</span></span>
    
- [<span data-ttu-id="32396-247">Office 365 的网络规划和性能调整 365</span><span class="sxs-lookup"><span data-stu-id="32396-247">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- <span data-ttu-id="32396-248">[Office 365 Performance Management](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)（Office 365 的性能管理）</span><span class="sxs-lookup"><span data-stu-id="32396-248">[Office 365 Performance Management](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)</span></span>
    
## <a name="expressroute-options"></a><span data-ttu-id="32396-249">ExpressRoute 选项</span><span class="sxs-lookup"><span data-stu-id="32396-249">ExpressRoute options</span></span>

<span data-ttu-id="32396-250">你也可以将以下选项纳入到 ExpressRoute 部署中：</span><span class="sxs-lookup"><span data-stu-id="32396-250">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="32396-251">**边缘的安全性：** 要实现通过 ExpressRoute 连接发送和接收的流量的高级安全性，如流量检查或入侵/恶意软件检测，请将安全装置放入 DMZ 内的流量路径下或 Intranet 边界。</span><span class="sxs-lookup"><span data-stu-id="32396-251">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
    <span data-ttu-id="32396-p121">VM 的 Internet 流量 为防止 Azure VM 直接启动与 Internet 位置的流量，请将默认路由告知 Microsoft。Internet 流量通过 ExpressRoute 连接和内部部署代理服务器传送。从 Azure 虚拟机到 Azure PaaS 服务或 Office 365 的流量将通过 ExpressRoute 连接传送回去。</span><span class="sxs-lookup"><span data-stu-id="32396-p121">Internet traffic for VMs To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="32396-p122">**WAN 优化程序：** 你可以在跨界部署的 Azure 虚拟网络 (VNet) 的专用对等连接两端部署 WAN 优化程序。在 Azure VNet 内部，使用 Azure 市场的 WAN 优化网络设备和用户定义路由通过该设备传送流量。</span><span class="sxs-lookup"><span data-stu-id="32396-p122">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="32396-p123">**服务质量：** 使用流量的 IPv4 标头中的差分服务代码点 (DSCP) 值将其标记为语音、视频/交互式或尽力传送。这对 Microsoft 对等关系以及 Skype for Business Online 流量尤为重要。</span><span class="sxs-lookup"><span data-stu-id="32396-p123">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="32396-259">有关详细信息，请参阅下列更多资源：</span><span class="sxs-lookup"><span data-stu-id="32396-259">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="32396-260">面向 Office 365 的 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="32396-260">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- <span data-ttu-id="32396-261">[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer/)（Azure ExpressRoute for Office 365 培训）</span><span class="sxs-lookup"><span data-stu-id="32396-261">[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer/)</span></span>
    
- <span data-ttu-id="32396-262">[ExpressRoute for Azure](https://azure.microsoft.com/services/expressroute/)（面向 Azure 的 ExpressRoute）</span><span class="sxs-lookup"><span data-stu-id="32396-262">[ExpressRoute for Azure](https://azure.microsoft.com/services/expressroute/)</span></span>
    
## <a name="next-step"></a><span data-ttu-id="32396-263">后续步骤</span><span class="sxs-lookup"><span data-stu-id="32396-263">Next step</span></span>

[<span data-ttu-id="32396-264">为 Microsoft SaaS 设计网络</span><span class="sxs-lookup"><span data-stu-id="32396-264">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="32396-265">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32396-265">See also</span></span>

[<span data-ttu-id="32396-266">面向企业架构师的 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="32396-266">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="32396-267">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="32396-267">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

