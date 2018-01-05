---
title: "为 Microsoft Azure PaaS 设计网络"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "摘要： 了解如何优化你的网络以便访问 Microsoft Azure PaaS。"
ms.openlocfilehash: d63a7a20d4648b0044a24ea86ad4e9125779a027
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="04060-103">为 Microsoft Azure PaaS 设计网络</span><span class="sxs-lookup"><span data-stu-id="04060-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="04060-104">**摘要：** 了解如何优化你的网络以便访问 Microsoft Azure PaaS。</span><span class="sxs-lookup"><span data-stu-id="04060-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="04060-105">优化 Azure PaaS 应用网络需要有足够的 Internet 带宽，并可以要求网络流量跨多个站点或应用分布。</span><span class="sxs-lookup"><span data-stu-id="04060-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="04060-106">计划将组织 PaaS 应用程序驻留在 Azure 中的步骤</span><span class="sxs-lookup"><span data-stu-id="04060-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

<span data-ttu-id="04060-107">在此处插入章节正文。</span><span class="sxs-lookup"><span data-stu-id="04060-107">Insert section body here.</span></span>
  
1. <span data-ttu-id="04060-108">完成 [Microsoft 云连接的常见元素](common-elements-of-microsoft-cloud-connectivity.md)中的**为 Microsoft 云服务准备网络的步骤**部分。</span><span class="sxs-lookup"><span data-stu-id="04060-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="04060-109">按照[设计 Microsoft SaaS 网络](designing-networking-for-microsoft-saas.md)中的**为 Microsoft SaaS 服务准备网络的步骤**部分的第 2-4 步操作，优化 Internet 带宽。</span><span class="sxs-lookup"><span data-stu-id="04060-109">Optimize your Internet bandwidth using steps 2 – 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="04060-110">确定是否需要到 Azure 的 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="04060-110">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="04060-111">对于基于 Web 的工作负载，确定是否需要 Azure 应用程序网关。</span><span class="sxs-lookup"><span data-stu-id="04060-111">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="04060-112">要使流量分布到不同数据中心内的不同终结点，请确定是否需要 Azure 流量管理器。</span><span class="sxs-lookup"><span data-stu-id="04060-112">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="04060-113">组织 PaaS 应用程序的 Internet 带宽</span><span class="sxs-lookup"><span data-stu-id="04060-113">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="04060-p101">在 Azure PaaS 中托管的组织应用程序要求 Intranet 用户具有 Internet 带宽。有两个选项：</span><span class="sxs-lookup"><span data-stu-id="04060-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="04060-p102">**选项 1：** 使用现有的管道，管道已针对 Internet 通信进行了优化，拥有处理峰值负载的容量。请参阅[为 Microsoft SaaS 设计网络](designing-networking-for-microsoft-saas.md)，了解 Internet 边缘、客户端使用情况和 IT 操作注意事项。</span><span class="sxs-lookup"><span data-stu-id="04060-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="04060-118">**选项 2：** 如果要求高带宽或低延迟，请使用 ExpressRoute 到 Azure 的连接。</span><span class="sxs-lookup"><span data-stu-id="04060-118">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="04060-119">**图 1：用于连接 Azure PaaS 服务的连接选项**</span><span class="sxs-lookup"><span data-stu-id="04060-119">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![图 1：Azure PaaS 服务的连接选项](images/Network_Poster/PaaS1.png)
  
<span data-ttu-id="04060-121">图 1 显示了通过 Internet 管道或 ExpressRoute 连接到 Azure PaaS 服务的内部部署网络。</span><span class="sxs-lookup"><span data-stu-id="04060-121">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="04060-122">Azure 应用程序网关</span><span class="sxs-lookup"><span data-stu-id="04060-122">Azure Application Gateway</span></span>

<span data-ttu-id="04060-123">应用程序级路由和负载平衡服务，使你可以在 Azure 中为 Web 应用、云服务和虚拟机创建一个可扩展、高可用性的 Web 前端。</span><span class="sxs-lookup"><span data-stu-id="04060-123">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="04060-124">**图 2：Azure 应用程序网关**</span><span class="sxs-lookup"><span data-stu-id="04060-124">**Figure 2: Azure Application Gateway**</span></span>

![图 2：Azure 应用程序网关服务](images/Network_Poster/PaaS2.png)
  
<span data-ttu-id="04060-126">图 2 显示了 Azure 应用程序网关，并展示如何将来自 Internet 的用户请求传送到 Azure Web 应用、云服务或虚拟机。</span><span class="sxs-lookup"><span data-stu-id="04060-126">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="04060-127">应用程序网关当前支持以下项的第 7 层应用程序传送：</span><span class="sxs-lookup"><span data-stu-id="04060-127">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="04060-128">HTTP 负载平衡</span><span class="sxs-lookup"><span data-stu-id="04060-128">HTTP load balancing</span></span>
    
- <span data-ttu-id="04060-129">基于 cookie 的会话关联</span><span class="sxs-lookup"><span data-stu-id="04060-129">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="04060-130">SSL 卸载</span><span class="sxs-lookup"><span data-stu-id="04060-130">SSL offload</span></span>
    
<span data-ttu-id="04060-131">有关详细信息，请参阅[应用程序网关]((https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction))。</span><span class="sxs-lookup"><span data-stu-id="04060-131">For more information, see [Application Gateway]((https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="04060-132">Azure 流量管理器</span><span class="sxs-lookup"><span data-stu-id="04060-132">Azure Traffic Manager</span></span>

<span data-ttu-id="04060-133">将流量分布到不同的终结点，此过程可以包括位于不同的数据中心或外部终结点的云服务或 Azure Web 应用。</span><span class="sxs-lookup"><span data-stu-id="04060-133">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="04060-134">流量管理器使用以下路由方法：</span><span class="sxs-lookup"><span data-stu-id="04060-134">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="04060-135">**故障转移：** 终结点位于相同或不同的 Azure 数据中心内，你想要对所有流量使用主终结点，但在主终结点或备份终结点不可用的情况下提供了备份。</span><span class="sxs-lookup"><span data-stu-id="04060-135">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="04060-136">**轮循机制：** 你想要将负载分布在同一个或不同数据中心的一组终结点上。</span><span class="sxs-lookup"><span data-stu-id="04060-136">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="04060-137">**性能：** 终结点位于不同的地理位置，你想要请求客户端使用延迟最低且距离"最近"的终结点。</span><span class="sxs-lookup"><span data-stu-id="04060-137">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="04060-138">下例显示了三个地理位置分散的 Web 应用。</span><span class="sxs-lookup"><span data-stu-id="04060-138">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="04060-139">**图 3：Azure 流量管理器**</span><span class="sxs-lookup"><span data-stu-id="04060-139">**Figure 3: Azure Traffic Manager**</span></span>

![图 3：Azure 流量管理器](images/Network_Poster/PaaS3.png)
  
<span data-ttu-id="04060-p103">图 3 显示了流量管理器用来将请求传送到在美国、欧洲和亚洲的三个不同 Azure Web 应用的基本过程。在本例中：</span><span class="sxs-lookup"><span data-stu-id="04060-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="04060-143">网站 URL 的用户 DNS 查询定向到 Azure 流量管理器，流量管理器基于性能路由方法返回区域 Web 应用的名称。</span><span class="sxs-lookup"><span data-stu-id="04060-143">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="04060-144">用户启动与欧洲区域 Web 应用之间的流量。</span><span class="sxs-lookup"><span data-stu-id="04060-144">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="04060-145">有关详细信息，请参阅[流量管理器]((https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview))。</span><span class="sxs-lookup"><span data-stu-id="04060-145">For more information, see [Traffic Manager]((https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview))</span></span>
  
## <a name="see-also"></a><span data-ttu-id="04060-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04060-146">See Also</span></span>

[<span data-ttu-id="04060-147">面向企业架构师的 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="04060-147">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="04060-148">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="04060-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="04060-149">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))</span><span class="sxs-lookup"><span data-stu-id="04060-149">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))</span></span>



