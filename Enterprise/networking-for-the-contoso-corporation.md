---
title: Contoso Corporation 的网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: 摘要： 了解 Contoso 网络基础结构以及它如何为优化访问与 Microsoft 的云产品使用 ExpressRoute。
ms.openlocfilehash: 89d4182d8a5ef44f936977ec51cc002b51f4b379
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915217"
---
# <a name="networking-for-the-contoso-corporation"></a><span data-ttu-id="6b39f-103">Contoso Corporation 的网络</span><span class="sxs-lookup"><span data-stu-id="6b39f-103">Networking for the Contoso Corporation</span></span>

 <span data-ttu-id="6b39f-104">**摘要：** 了解 Contoso 网络基础结构以及它如何为优化访问与 Microsoft 的云产品使用 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="6b39f-104">**Summary:** Understand the Contoso networking infrastructure and how it can use ExpressRoute for optimized acccess to Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="6b39f-p101">采用云之间的基础结构，Contoso 的网络工程师意识到的网络到基于云的服务旅行的通信方式根本性转变。而不是仅优化到内部部署服务器和数据中心的通信，必须对优化通信到 Internet 边缘通过 Internet 支付等于注意。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p101">To adopt a cloud-inclusive infrastructure, Contoso's network engineers realized the fundamental shift in the way that network traffic to cloud-based services travels. Instead of only optimizing traffic to on-premises servers and datacenters, equal attention must be paid to optimizing traffic to the Internet edge and across the Internet.</span></span>
  
## <a name="contosos-networking-infrastructure"></a><span data-ttu-id="6b39f-107">Contoso 的网络基础结构</span><span class="sxs-lookup"><span data-stu-id="6b39f-107">Contoso's networking infrastructure</span></span>

<span data-ttu-id="6b39f-108">Contoso 具有以下网络基础结构，如图 1 所示。</span><span class="sxs-lookup"><span data-stu-id="6b39f-108">Contoso has the networking infrastructure shown in Figure 1.</span></span>
  
<span data-ttu-id="6b39f-109">**图 1：Contoso 的 WAN 基础结构**</span><span class="sxs-lookup"><span data-stu-id="6b39f-109">**Figure 1: Contoso's WAN infrastructure**</span></span>

![链接总部、区域中心和分支办事处的 Contoso WAN 基础结构](media/Contoso-Poster/Contoso-WW-Net.png)
  
<span data-ttu-id="6b39f-111">图 1 显示 Contoso 在全球的办事处以及他们之间的区域办事处和分支办事处 WAN 链接组。</span><span class="sxs-lookup"><span data-stu-id="6b39f-111">Figure 1 shows the Contoso's offices across the globe and the set of regional and satellite office WAN links between them.</span></span>
  
<span data-ttu-id="6b39f-112">其他网络元素如下：</span><span class="sxs-lookup"><span data-stu-id="6b39f-112">Additional elements of their network are the following:</span></span>
  
- <span data-ttu-id="6b39f-113">本地网络</span><span class="sxs-lookup"><span data-stu-id="6b39f-113">On-premises network</span></span>
    
    <span data-ttu-id="6b39f-p102">WAN 链接连接到地区办事处和给附属的分支和集线器传输配置办事处的地区办事处巴黎总部。内每个办公室，路由器到主机或在使用专用 IP 地址空间的子网无线访问点提供流量。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p102">WAN links connect the Paris headquarters to regional offices and regional offices to satellite offices in a spoke and hub configuration. Within each office, routers deliver traffic to hosts or wireless access points on subnets, which use the private IP address space.</span></span>
    
- <span data-ttu-id="6b39f-116">Internet 连接</span><span class="sxs-lookup"><span data-stu-id="6b39f-116">Internet connectivity</span></span>
    
    <span data-ttu-id="6b39f-p103">每个办事处有其自己的 Internet 连接通过代理服务器。这通常作为 WAN 链接到本地 ISP 还提供公共 IP 地址的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p103">Each office has its own Internet connectivity via a proxy server. This is typically implemented as a WAN link to a local ISP that also provides public IP addresses for the proxy server.</span></span>
    
- <span data-ttu-id="6b39f-119">Internet 展示</span><span class="sxs-lookup"><span data-stu-id="6b39f-119">Internet presence</span></span>
    
    <span data-ttu-id="6b39f-p104">Contoso 拥有 contoso.com 公共域名。Contoso 公共网站订购产品是一套巴黎所高校中连接到 Internet 的数据中心中的服务器。Contoso 使用 / 24 Internet 上的公用 IP 地址范围。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p104">Contoso owns the contoso.com public domain name. The Contoso public web site for ordering products is a set of servers in an Internet-connected datacenter in the Paris campus. Contoso uses a /24 public IP address range on the Internet.</span></span>
    
## <a name="contosos-app-infrastructure"></a><span data-ttu-id="6b39f-123">Contoso 的应用程序基础结构</span><span class="sxs-lookup"><span data-stu-id="6b39f-123">Contoso's app infrastructure</span></span>

<span data-ttu-id="6b39f-124">针对以下情况，Contoso 构建了其应用程序和服务器基础结构：



</span><span class="sxs-lookup"><span data-stu-id="6b39f-124">Contoso has architected its application and server infrastructure for the following:</span></span>
  
<span data-ttu-id="6b39f-125">**图 2：Contoso 内部应用程序的基础结构**</span><span class="sxs-lookup"><span data-stu-id="6b39f-125">**Figure 2: Contoso's infrastructure for internal applications**</span></span>

![Contoso 内部应用程序的基础结构](media/Contoso-Poster/App-Infra.png)
  
- <span data-ttu-id="6b39f-127">分支办事处使用本地缓存服务器存储经常访问的文档和内部网站。</span><span class="sxs-lookup"><span data-stu-id="6b39f-127">Satellite offices use local caching servers to store frequently-accessed documents and internal web sites.</span></span>
    
- <span data-ttu-id="6b39f-p105">
区域中心将区域应用程序服务器用于区域办事处和分支办事处。这些服务器与巴黎总部的服务器同步。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p105">Regional hubs use regional application servers for the regional and satellite offices. These servers synchronize with servers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="6b39f-130">巴黎园区拥有的数据中心包含为整个组织提供服务的集中式应用程序服务器。</span><span class="sxs-lookup"><span data-stu-id="6b39f-130">The Paris campus has the datacenters that contain the centralized application servers that serve the entire organization.</span></span>
    
<span data-ttu-id="6b39f-p106">对于分支办事处或区域中心办事处的用户，员工所需资源的 60% 可由分支办事处和区域中心办事处服务器提供。其他 40% 的资源请求则必须通过 WAN 链接到巴黎园区。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p106">For users in satellite or regional hub offices, 60% of the resources needed by employees can be served by satellite and regional hub office servers. The additional 40% of resource requests must go over the WAN link to the Paris campus.</span></span>
  
## <a name="contosos-network-analysis"></a><span data-ttu-id="6b39f-133">Contoso 的网络分析</span><span class="sxs-lookup"><span data-stu-id="6b39f-133">Contoso's network analysis</span></span>

<span data-ttu-id="6b39f-134">下面是分析的在他们的网络上适应不同类别的 Microsoft 云服务所需的更改的 Contoso 的结果：</span><span class="sxs-lookup"><span data-stu-id="6b39f-134">Here are the results of Contoso's analysis of the changes needed on their network to accommodate the different categories of Microsoft's cloud offerings:</span></span>
  
|<span data-ttu-id="6b39f-135">**Saas 与云产品： Office 365、 EMS 和 Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="6b39f-135">**SaaS cloud offerings: Office 365, EMS, and Dynamics 365**</span></span>|<span data-ttu-id="6b39f-136">**Azure PaaS： 移动应用程序**</span><span class="sxs-lookup"><span data-stu-id="6b39f-136">**Azure PaaS: Mobile applications**</span></span>|<span data-ttu-id="6b39f-137">**Azure IaaS： 基于服务器的工作负荷**</span><span class="sxs-lookup"><span data-stu-id="6b39f-137">**Azure IaaS: Server-based workloads**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6b39f-138">用户能成功利用 SaaS 服务，要依赖于高可用性和高性能的 Internet 连接或直接到 Microsoft 云服务的连接。
</span><span class="sxs-lookup"><span data-stu-id="6b39f-138">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>  <br/> <span data-ttu-id="6b39f-139">对于移动用户，假定他们当前的 Internet 访问权限足够。
</span><span class="sxs-lookup"><span data-stu-id="6b39f-139">For mobile users, their current Internet access is assumed to be adequate.</span></span>  <br/> <span data-ttu-id="6b39f-140">对于 Contoso intranet 上的用户，必须分析并针对到 Internet 的吞吐量和到 Microsoft 的欧洲数据中心托管 Office 365、 EMS 和 Dynamics 365 租户的往返时间优化每个办公室。</span><span class="sxs-lookup"><span data-stu-id="6b39f-140">For users on the Contoso intranet, each office must be analyzed and optimized for throughput to the Internet and round-trip times to Microsoft's Europe datacenter hosting the Office 365, EMS, and Dynamics 365 tenants.</span></span>  <br/> |<span data-ttu-id="6b39f-p107">为更好地支持移动工作人员，旧版应用和一些文件共享站点被修改并部署成了 Azure PaaS 应用。为获得最佳性能，Contoso 计划在全球的多个 Azure 数据中心部署新应用。Azure 流量管理器将客户端应用请求发送到最近的托管应用的 Azure 数据中心，无论它们源自移动用户还是办事处的计算机。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p107">To better support mobile workers, legacy apps and some file sharing sites are being reworked and deployed as Azure PaaS apps. For optimum performance, Contoso plans to deploy the new apps from multiple Azure datacenters across the world. Azure Traffic Manager to send client app requests, whether they originate from a mobile user or a computer in the office, to the nearest Azure datacenter hosting the app.</span></span>  <br/>  <span data-ttu-id="6b39f-144"> 

IT 部门将需要为其网络运行状况监视解决方案添加 PaaS 应用程序性能和流量分发。</span><span class="sxs-lookup"><span data-stu-id="6b39f-144">The IT department will need to add PaaS application performance and traffic distribution to their network health monitoring solution.</span></span> <br/> |<span data-ttu-id="6b39f-145">要将一些旧版和存档服务器从巴黎园区数据中心移出并根据需要添加服务器以进行季度末处理，Contoso 计划使用在 Azure 基础结构服务中运行的虚拟机。 

</span><span class="sxs-lookup"><span data-stu-id="6b39f-145">To move some legacy and archival servers out of the Paris campus datacenters and add servers as needed for quarter-end processing, Contoso plans to use virtual machines running in Azure infrastructure services.</span></span>  <br/> <span data-ttu-id="6b39f-146">包含这些服务器的 Azure 虚拟网络必须为非重叠地址空间、路由和集成 DNS 进行设计。

</span><span class="sxs-lookup"><span data-stu-id="6b39f-146">The Azure virtual networks that contain these servers must be designed for non-overlapping address spaces, routing, and integrated DNS.</span></span>  <br/> <span data-ttu-id="6b39f-147">IT 部门的网络管理和监视系统中必须包含这些新的服务器。</span><span class="sxs-lookup"><span data-stu-id="6b39f-147">The IT department must include these new servers in their network management and monitoring system.</span></span>  <br/> |
   
## <a name="contosos-use-of-expressroute"></a><span data-ttu-id="6b39f-148">ExpressRoute Contoso 的使用</span><span class="sxs-lookup"><span data-stu-id="6b39f-148">Contoso's use of ExpressRoute</span></span>

<span data-ttu-id="6b39f-p108">ExpressRoute 是从您的位置到您的网络连接到 Microsoft 云网络的 Microsoft 对等位置的专用 WAN 连接。ExpressRoute 连接提供可预测的性能和 99.9%正常运行时间 SLA。.</span><span class="sxs-lookup"><span data-stu-id="6b39f-p108">ExpressRoute is a dedicated WAN connection from your location to a Microsoft peering location that connects your network to the Microsoft cloud network. ExpressRoute connections provide predictable performance and a 99.9% uptime SLA. .</span></span>
  
<span data-ttu-id="6b39f-p109">使用 ExpressRoute 连接时，系统会将您连接到 Microsoft 云网络和相同洲中的所有 Microsoft 数据中心位置。云对等位置和目标 Microsoft 数据中心之间的通信转移 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="6b39f-p109">With an ExpressRoute connection, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network</span></span>
  
<span data-ttu-id="6b39f-154">**图 3：全球范围内的 Microsoft 云网络**</span><span class="sxs-lookup"><span data-stu-id="6b39f-154">**Figure 3: The Microsoft cloud network worldwide**</span></span>

![全球范围内的 Microsoft 云网络](media/Contoso-Poster/MS-WW-Cloud.png)
  
<span data-ttu-id="6b39f-156">图 3 显示针对世界上不同区域的互联 Microsoft 云网络。</span><span class="sxs-lookup"><span data-stu-id="6b39f-156">Figure 3 shows the interconnected Microsoft cloud network for the various regions of the world.</span></span>
  
<span data-ttu-id="6b39f-p110">通过 ExpressRoute Premium，可以从任何洲的任何 Microsoft 对等位置到达任何洲的任何 Microsoft 数据中心。洲之间的流量通过 Microsoft 云网络传送。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p110">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="6b39f-159">根据当前和将来流量 Microsoft 云服务的分析，Contoso 具有执行网络评估，并实现与私钥和公钥对等的 Azure 资源的访问权的任意到任意 （基于 MPLS） ExpressRoute 连接从 Microsoft 对等位置在欧洲巴黎总部的关系。</span><span class="sxs-lookup"><span data-stu-id="6b39f-159">Based on the analysis of current and future traffic to Microsoft's cloud offerings, Contoso has performed a network assessment and implemented an any-to-any (MPLS-based) ExpressRoute connection for access to Azure resources, with private and public peering relationships, from the Paris headquarters to the Microsoft peering location in Europe.</span></span>
  
<span data-ttu-id="6b39f-160">此连接将为 Contoso 的 IT 部门提供：</span><span class="sxs-lookup"><span data-stu-id="6b39f-160">This connection will give Contoso's IT department:</span></span>
  
- <span data-ttu-id="6b39f-161">管理分布式 Azure PaaS 应用的一致性能</span><span class="sxs-lookup"><span data-stu-id="6b39f-161">Consistent performance for administration of distributed Azure PaaS apps</span></span>
    
    <span data-ttu-id="6b39f-p111">所有的 Contoso 的应用程序开发人员和核心基础结构 IT 管理员是巴黎所高校中。使用 Azure PaaS 应用程序分发给不同世界各地的 Azure 数据中心，Contoso 需要从管理的应用程序以及其存储资源，从而包含的文档的 TB 巴黎校园一致的性能。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p111">All of Contoso's application developers and core infrastructure IT administrators are in the Paris campus. With Azure PaaS apps distributed to different Azure datacenters around the world, Contoso needs consistent performance from the Paris campus to administer the apps and their storage resources, which consist of TB of documents.</span></span>
    
- <span data-ttu-id="6b39f-164">具有管理 Azure IaaS 中服务器的一致性能</span><span class="sxs-lookup"><span data-stu-id="6b39f-164">Consistent performance for administration of servers in Azure IaaS</span></span>
    
    <span data-ttu-id="6b39f-p112">Contoso 的数据中心管理员位于巴黎校园和 Azure 中部署的服务器是巴黎数据中心的扩展。对于访问旧版应用程序和存档存储和结束的季度处理，Contoso 需要一致到这些新的服务器的性能。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p112">Contoso's datacenter administrators are in the Paris campus and the servers to be deployed in Azure are an extension of the Paris datacenter. Contoso needs consistent performance to these new servers for access to legacy apps and archival storage and for end-of-quarter processing.</span></span>
    
## <a name="contosos-path-to-cloud-networking-readiness"></a><span data-ttu-id="6b39f-167">Contoso 的路径云网络准备情况</span><span class="sxs-lookup"><span data-stu-id="6b39f-167">Contoso's path to cloud networking readiness</span></span>

<span data-ttu-id="6b39f-168">Contoso 使用以下步骤为 Microsoft 云网络做准备：</span><span class="sxs-lookup"><span data-stu-id="6b39f-168">Contoso uses the following steps to ready their network for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="6b39f-169">优化用于 Internet 访问的员工计算机
</span><span class="sxs-lookup"><span data-stu-id="6b39f-169">Optimize employee computers for Internet access</span></span>
    
    <span data-ttu-id="6b39f-170">检查每台计算机，确保安装了最新的 TCP/IP 堆栈、浏览器、NIC 驱动程序及安全性和操作系统更新。</span><span class="sxs-lookup"><span data-stu-id="6b39f-170">Individual computers will be checked to ensure that the latest TCP/IP stack, browser, NIC drivers, and security and operating system updates are installed.</span></span>
    
2. <span data-ttu-id="6b39f-171">分析每个办事处的 Internet 连接利用率，并根据需要增加带宽</span><span class="sxs-lookup"><span data-stu-id="6b39f-171">Analyze Internet connection utilization at each office and increase as needed</span></span>
    
    <span data-ttu-id="6b39f-172">
如果在利用率达 70% 或以上的情况下运行，将分析每个办事处的当前 Internet 使用情况，并增加 WAN 链接带宽。</span><span class="sxs-lookup"><span data-stu-id="6b39f-172">Each office will be analyzed for the current Internet usage and WAN link bandwidth will be increased if operating at 70% or above utilization.</span></span>
    
3. <span data-ttu-id="6b39f-173">分析每个办事处的 DMZ 系统以获得最佳性能
</span><span class="sxs-lookup"><span data-stu-id="6b39f-173">Analyze DMZ systems at each office for optimal performance</span></span>
    
    <span data-ttu-id="6b39f-p113">分析防火墙、IDS 和 Internet 路径中的其他系统以获得最佳性能。代理服务器将根据需要更新或升级。</span><span class="sxs-lookup"><span data-stu-id="6b39f-p113">Firewalls, IDSs, and other systems in the Internet path will be analyzed for optimal performance. Proxy servers will be updated or upgraded as needed.</span></span>
    
4. <span data-ttu-id="6b39f-176">为巴黎园区添加 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="6b39f-176">Add ExpressRoute for the Paris campus</span></span>
    
    <span data-ttu-id="6b39f-177">提供对 Azure 资源的一致访问权限以管理 Azure PaaS 和 IaaS 工作负载。</span><span class="sxs-lookup"><span data-stu-id="6b39f-177">Provides consistent access to Azure resources for administration of Azure PaaS and IaaS workloads.</span></span>
    
5. <span data-ttu-id="6b39f-178">为 Azure PaaS 应用创建和测试 Azure 流量管理器配置文件</span><span class="sxs-lookup"><span data-stu-id="6b39f-178">Create and test an Azure Traffic Manager profile for Azure PaaS apps</span></span>
    
    <span data-ttu-id="6b39f-179">测试 Azure 流量管理器配置文件，该配置文件使用性能路由方法来获得将 Internet 流量分发到区域位置的体验。</span><span class="sxs-lookup"><span data-stu-id="6b39f-179">Test an Azure Traffic Manager profile that uses the performance routing method to gain experience in distributing Internet traffic to regional locations.</span></span>
    
6. <span data-ttu-id="6b39f-180">为 Azure VNet 保留专用地址空间
</span><span class="sxs-lookup"><span data-stu-id="6b39f-180">Reserve private address space for Azure VNets</span></span>
    
    <span data-ttu-id="6b39f-181">根据 Azure IaaS 中计划的短期和长期服务器数，为 Azure VNet 及其子网保留专用地址空间。</span><span class="sxs-lookup"><span data-stu-id="6b39f-181">Based on the numbers of projected short and long-term servers in Azure IaaS, reserve private address space for Azure VNets and their subnets.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="6b39f-182">See Also</span><span class="sxs-lookup"><span data-stu-id="6b39f-182">See Also</span></span>

[<span data-ttu-id="6b39f-183">Microsoft 云中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="6b39f-183">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="6b39f-184">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="6b39f-184">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="6b39f-185">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="6b39f-185">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



