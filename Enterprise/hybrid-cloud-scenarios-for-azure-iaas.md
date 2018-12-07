---
title: Azure IaaS 的混合云方案
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 摘要： 了解混合体系结构和方案的 Microsoft 的基础结构作为服务 (IaaS)-基于 Azure 中的云服务。
ms.openlocfilehash: 441565adae46d50ad1b7139525ff3146c5f88ca3
ms.sourcegitcommit: 82c8fe6393457f0271d1737a09402a420a81c986
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2018
ms.locfileid: "27181033"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="e0bf1-103">适用于 Azure IaaS 的混合云方案</span><span class="sxs-lookup"><span data-stu-id="e0bf1-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="e0bf1-104">**摘要：** 了解作为服务 (IaaS) for Microsoft 的基础结构的混合体系结构和方案-基于 Azure 中的云服务。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="e0bf1-105">通过托管在跨内部 Azure 虚拟网络 (VNet) 中运行的 IT 工作负荷，将本地计算和标识基础结构扩展到云。 </span><span class="sxs-lookup"><span data-stu-id="e0bf1-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="e0bf1-106">Azure IaaS 混合方案体系结构</span><span class="sxs-lookup"><span data-stu-id="e0bf1-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="e0bf1-107">图 1 显示了 Azure 中基于 Microsoft laaS 的混合方案的体系结构。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="e0bf1-108">**图 1：Azure 中基于 Microsoft IaaS 的混合方案**</span><span class="sxs-lookup"><span data-stu-id="e0bf1-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Azure 中基于 Microsoft IaaS 的混合方案](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="e0bf1-110">针对体系结构的每一层：</span><span class="sxs-lookup"><span data-stu-id="e0bf1-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="e0bf1-111">应用和方案</span><span class="sxs-lookup"><span data-stu-id="e0bf1-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="e0bf1-112">IT 工作负荷通常为多层的高可用性应用程序，由 Azure 虚拟机 (VM) 构成。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="e0bf1-113">标识</span><span class="sxs-lookup"><span data-stu-id="e0bf1-113">Identity</span></span>
    
    <span data-ttu-id="e0bf1-114">将标识服务器（如 Windows Sever AD 域控制器）添加到一组在 Azure VNet 中运行的服务器，以进行本地身份验证。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="e0bf1-115">网络</span><span class="sxs-lookup"><span data-stu-id="e0bf1-115">Network</span></span>
    
    <span data-ttu-id="e0bf1-116">使用通过 Internet 建立的站点到站点 VPN 连接，或使用通过到 Azure IaaS 的专用对等建立的 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="e0bf1-117">本地</span><span class="sxs-lookup"><span data-stu-id="e0bf1-117">On-premises</span></span>
    
    <span data-ttu-id="e0bf1-p101">包含与在 Azure 中运行的标识服务器同步的标识服务器。此外还包含在 Azure 中运行的 VM 可访问的资源，如存储和系统管理基础结构。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="directory-synchronization-server-for-office-365"></a><span data-ttu-id="e0bf1-120">Office 365 的目录同步服务器</span><span class="sxs-lookup"><span data-stu-id="e0bf1-120">Directory synchronization server for Office 365</span></span>

<span data-ttu-id="e0bf1-121">从 Azure VNet，运行您的目录同步服务器，如图 2 中所示是扩展到云计算和标识基础结构的示例。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-121">Running your directory synchronization server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="e0bf1-122">**图 2: Azure IaaS 中的 Office 365 的目录同步服务器**</span><span class="sxs-lookup"><span data-stu-id="e0bf1-122">**Figure 2: Directory synchronization server for Office 365 in Azure IaaS**</span></span>

![Azure IaaS 中的 Office 365 的目录同步服务器](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="e0bf1-p102">图 2 中的本地网络承载具有代理服务器和边缘处路由器 Windows Server AD 基础结构。路由器连接到 Azure 网关与站点到站点 VPN 或 ExpressRoute 连接 Azure VNet 边缘内侧。内 VNet，目录同步服务器运行 Azure AD 连接。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-p102">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge. The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection. Inside the VNet, a directory synchronization server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="e0bf1-127">Office 365 的目录同步服务器将与 Office 365 订阅的 Azure AD 租户同步在 Windows Server AD 中的帐户的列表。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-127">A directory synchronization server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="e0bf1-p103">目录同步服务器是运行 Azure AD 连接的基于 Windows 的服务器。用于更快地设置或减少内部部署组织中的服务器数量的部署您在 Azure IaaS 虚拟网络 (VNet) 中的目录同步服务器。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-p103">A directory synchronization server is a Windows-based server that runs Azure AD Connect. For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your directory synchronization server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="e0bf1-130">目录同步服务器轮询 Windows Server AD 的更改，然后将它们与 Office 365 订阅同步。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-130">The directory synchronization server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="e0bf1-131">有关详细信息，请参阅[部署 Microsoft Azure 中 Office 365 目录同步](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="e0bf1-132">业务线 (LOB) 应用程序</span><span class="sxs-lookup"><span data-stu-id="e0bf1-132">Line of business (LOB) application</span></span>

<span data-ttu-id="e0bf1-133">图 3 显示了在 Azure IaaS 中运行的基于服务器的 LOB 应用程序的配置。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="e0bf1-134">**图 3：Azure IaaS 中的 LOB 应用程序**</span><span class="sxs-lookup"><span data-stu-id="e0bf1-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Azure IaaS 中基于服务器的 LOB 应用程序](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="e0bf1-p104">在图 3 中，本地网络托管标识基础结构和用户。它通过站点到站点 VPN 或 ExpressRoute 连接来连接到 Azure IaaS 网关。Azure IaaS 托管包含 LOB 应用程序服务器的虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="e0bf1-139">可以创建在 Azure VM 上运行的 LOB 应用，它驻留在 Azure 数据中心的 Azure VNet 的子网（也称为位置）上。 


</span><span class="sxs-lookup"><span data-stu-id="e0bf1-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="e0bf1-140">因为实际上要将本地基础结构扩展到 Azure，则必须将唯一的专用地址空间分配给 VNet，并更新本地路由表，以确保对每个 VNet 的可访问性。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="e0bf1-141">连接后，可通过远程桌面连接或使用系统管理软件对 VM 进行管理，就像对本地服务器进行管理一样。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="e0bf1-142">通过配置公开的端口，移动或远程用户还可以从 Internet 对这些 VM 进行访问。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="e0bf1-143">有关概念证明配置的信息，请参阅 [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="e0bf1-144">以下为在 Azure VM 上托管的 LOB 应用的属性：</span><span class="sxs-lookup"><span data-stu-id="e0bf1-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="e0bf1-145">多层</span><span class="sxs-lookup"><span data-stu-id="e0bf1-145">Multiple tiers</span></span>
    
    <span data-ttu-id="e0bf1-p105">典型的 LOB 应用使用分层方法。服务器集提供标识、数据库处理、应用程序和逻辑处理以及前端 Web 服务器，以供员工或客户访问。 </span><span class="sxs-lookup"><span data-stu-id="e0bf1-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="e0bf1-148">高可用性</span><span class="sxs-lookup"><span data-stu-id="e0bf1-148">High availability</span></span>
    
    <span data-ttu-id="e0bf1-p106">典型的 LOB 应用通过在每一层中使用多个服务器来提供高可用性。Azure IaaS 为 Azure 可用集内的服务器提供高达 99.9% 的运行时间 SLA。 </span><span class="sxs-lookup"><span data-stu-id="e0bf1-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="e0bf1-151">负载分布</span><span class="sxs-lookup"><span data-stu-id="e0bf1-151">Load distribution</span></span>
    
    <span data-ttu-id="e0bf1-p107">若要在一个层的多个服务器之间分布网络流量负载，可以使用面向 Internet 的或内部的 Azure 负载均衡器。或者，可以使用 Azure 应用商店提供的专用负载均衡器应用程序。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="e0bf1-154">安全性</span><span class="sxs-lookup"><span data-stu-id="e0bf1-154">Security</span></span>
    
    <span data-ttu-id="e0bf1-p108">若要保护服务器避免接收来自 Internet 的未经请求的传入流量，可以使用 Azure 网络安全组。可以为单个虚拟机的子网或网络接口定义允许或拒绝的流量。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="e0bf1-157">Azure 中的 SharePoint Server 2016 场</span><span class="sxs-lookup"><span data-stu-id="e0bf1-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="e0bf1-158">Azure 中一个多层、高可用性 LOB 应用程序的示例是 SharePoint Server 2016 场，如图 4 中所示。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="e0bf1-159">**图 4：Azure IaaS 中具有高可用性的 SharePoint Server 2016 场**</span><span class="sxs-lookup"><span data-stu-id="e0bf1-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS 中具有高可用性的 SharePoint Server 2016 场](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="e0bf1-p109">在图 4 中，本地网络托管标识基础结构和用户。它通过站点到站点 VPN 或 ExpressRoute 连接来连接到 Azure IaaS 网关。Azure VNet 包含 SharePoint Server 2016 场的多个服务器，该场包括前端服务器的单独层、应用程序服务器，SQL Server 群集，以及域控制器。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="e0bf1-164">此配置具有 Azure 中 LOB 应用程序的以下属性： </span><span class="sxs-lookup"><span data-stu-id="e0bf1-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="e0bf1-165">层</span><span class="sxs-lookup"><span data-stu-id="e0bf1-165">Tiers</span></span>
    
    <span data-ttu-id="e0bf1-166">场中运行不同角色的服务器创建多个层，并且每一层都有其自己的子网。
</span><span class="sxs-lookup"><span data-stu-id="e0bf1-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="e0bf1-167">高可用性</span><span class="sxs-lookup"><span data-stu-id="e0bf1-167">High-availability</span></span>
    
    <span data-ttu-id="e0bf1-168">通过在每一层中使用多个服务器，并将一层的所有服务器置于同一个可用性集中来实现高可用性。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="e0bf1-169">负载分布</span><span class="sxs-lookup"><span data-stu-id="e0bf1-169">Load distribution</span></span>
    
    <span data-ttu-id="e0bf1-170">内部 Azure 负载均衡器将传入客户端 Web 流量分布到前端服务器（WEB1 和 WEB2）以及分布到 SQL Server 群集（SQL1、SQL2 和 MN1）的侦听器 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="e0bf1-171">安全性</span><span class="sxs-lookup"><span data-stu-id="e0bf1-171">Security</span></span>
    
    <span data-ttu-id="e0bf1-172">通过每个子网的网络安全组，可以配置允许的入站和出站流量。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="e0bf1-173">按照此方法实现成功的应用：</span><span class="sxs-lookup"><span data-stu-id="e0bf1-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="e0bf1-174">计算和试验</span><span class="sxs-lookup"><span data-stu-id="e0bf1-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="e0bf1-175">请参阅[Microsoft Azure 中的 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)了解 Azure 中运行 SharePoint Server 2016 的优势。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="e0bf1-176">请参阅[Azure 的开发测试环境中的 Intranet SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)生成模拟的开发测试环境</span><span class="sxs-lookup"><span data-stu-id="e0bf1-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="e0bf1-177">设计</span><span class="sxs-lookup"><span data-stu-id="e0bf1-177">Design</span></span>
    
    <span data-ttu-id="e0bf1-178">请参阅[设计 Azure 中的 SharePoint Server 2016 场](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure)以完成整个过程，以确定的 Azure IaaS 网络、 计算、 和存储元素来承载您的服务器场和其设置的集合。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="e0bf1-179">部署</span><span class="sxs-lookup"><span data-stu-id="e0bf1-179">Deploy</span></span>
    
    <span data-ttu-id="e0bf1-180">请参阅[在 Azure 中的 SQL Server AlwaysOn 可用性组与部署 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in)逐步处理的高可用性服务器场中五个阶段的端到端配置。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="e0bf1-181">Azure 中的 Office 365 联合的身份</span><span class="sxs-lookup"><span data-stu-id="e0bf1-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="e0bf1-182">Azure 中的多层、 高可用性的 LOB 应用程序的另一个示例是 Office 365 联合的身份。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="e0bf1-183">**图 5: 高可用性联合的身份基础结构 Azure IaaS 中的 Office 365**</span><span class="sxs-lookup"><span data-stu-id="e0bf1-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![高可用性 Office 365 联合 Azure 中的身份验证基础结构](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="e0bf1-p110">图 5 中的本地网络承载身份基础结构和用户。连接到 Azure IaaS 网关与站点到站点 VPN 或 ExpressRoute 连接。Azure VNet 包含 web 代理服务器、 Active Directory 联合身份验证服务 (AD FS) 服务器和 Windows Server Active Directory (AD) 域控制器。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-p110">In Figure 5, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Windows Server Active Directory (AD) domain controllers.</span></span>
  
<span data-ttu-id="e0bf1-188">此配置具有 Azure 中 LOB 应用程序的以下属性： </span><span class="sxs-lookup"><span data-stu-id="e0bf1-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="e0bf1-189">**层：** 有 web 代理服务器、 AD FS 服务器和 Windows Server AD 域控制器的层。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="e0bf1-190">**负载分布：** 外部 Azure 负载平衡器分发 web 代理对传入客户端身份验证请求并内部 Azure 负载平衡器将分发到 AD FS 服务器的身份验证请求。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="e0bf1-191">按照此方法实现成功的应用：</span><span class="sxs-lookup"><span data-stu-id="e0bf1-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="e0bf1-192">计算和试验</span><span class="sxs-lookup"><span data-stu-id="e0bf1-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="e0bf1-193">请参阅[为 Office 365 开发/测试环境的联盟标识](federated-identity-for-your-office-365-dev-test-environment.md)生成与 Office 365 联合身份验证的模拟的开发测试环境。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="e0bf1-194">部署</span><span class="sxs-lookup"><span data-stu-id="e0bf1-194">Deploy</span></span>
    
    <span data-ttu-id="e0bf1-195">请参阅[在 Azure 中的 Office 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)完成 AD FS 基础结构的高可用性的端到端配置过程中五个阶段的步骤。</span><span class="sxs-lookup"><span data-stu-id="e0bf1-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="e0bf1-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0bf1-196">See Also</span></span>

[<span data-ttu-id="e0bf1-197">面向企业架构师的 Microsoft 混合云</span><span class="sxs-lookup"><span data-stu-id="e0bf1-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="e0bf1-198">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="e0bf1-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


