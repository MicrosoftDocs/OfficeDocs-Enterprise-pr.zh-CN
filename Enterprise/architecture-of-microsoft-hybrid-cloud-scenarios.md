---
title: "Microsoft 混合云方案的体系结构"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "摘要： 了解 Microsoft 混合云产品的体系结构。"
ms.openlocfilehash: 0909964421cecec455ed3c45c965a330501d361c
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="a46a8-103">Microsoft 混合云方案的体系结构</span><span class="sxs-lookup"><span data-stu-id="a46a8-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="a46a8-104">**摘要：** 了解 Microsoft 混合云产品的体系结构。</span><span class="sxs-lookup"><span data-stu-id="a46a8-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="a46a8-105">使用体系结构方法通过 Microsoft 云服务及平台来计划和实施混合云方案。</span><span class="sxs-lookup"><span data-stu-id="a46a8-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="a46a8-106">**图 1：Microsoft 混合云堆栈**</span><span class="sxs-lookup"><span data-stu-id="a46a8-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Microsoft 混合云堆叠](images/Hybrid_Poster/Hybrid_Cloud_Stack.png)
  
<span data-ttu-id="a46a8-108">图 1 显示了 Microsoft 混合云堆栈及其层，包括内部部署、网络、标识、应用程序和方案，以及云服务（Microsoft SaaS、Azure PaaS 和 Azure PaaS）的类别。</span><span class="sxs-lookup"><span data-stu-id="a46a8-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="a46a8-p101">应用程序和方案层包含本模型中其他文章中详述的特定混合云方案。标识、网络和本地层可与云服务（SaaS、PaaS 或 PaaS）类别共用。</span><span class="sxs-lookup"><span data-stu-id="a46a8-p101">The Apps and scenarios layer contains the specific hybrid cloud scenarios that are detailed in the additional articles of this model. The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="a46a8-111">本地</span><span class="sxs-lookup"><span data-stu-id="a46a8-111">On-premises</span></span>
    
    <span data-ttu-id="a46a8-p102">混合方案的本地基础结构可包括适用于 SharePoint、Exchange、Skype for Business 和业务线应用程序的服务器。它还可以包括数据存储（数据库、列表、文件）。如果没有 ExpressRoute 连接，必须允许通过反向代理或使服务器或数据可从 DMZ 或 Extranet 上访问来访问本地数据存储。</span><span class="sxs-lookup"><span data-stu-id="a46a8-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="a46a8-115">网络</span><span class="sxs-lookup"><span data-stu-id="a46a8-115">Network</span></span>
    
    <span data-ttu-id="a46a8-p103">连接到 Microsoft 云平台和服务有两种选择：现有的 Internet 管道和 ExpressRoute。如果可预知的性能非常重要，请使用 ExpressRoute 连接。可以使用一个 ExpressRoute 连接直接连接到 Microsoft SaaS 服务（Office 365 和 Dynamics 365）、Azure PaaS 服务和 Azure IaaS 服务。</span><span class="sxs-lookup"><span data-stu-id="a46a8-p103">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute. Use an ExpressRoute connection if predictable performance is important. You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure PaaS services.</span></span>
    
- <span data-ttu-id="a46a8-119">标识</span><span class="sxs-lookup"><span data-stu-id="a46a8-119">Identity</span></span>
    
    <span data-ttu-id="a46a8-p104">对于云标识基础结构，根据 Microsoft 云平台的不同有两种方式可选。对于 SaaS 和 Azure IaaS，将本地标识基础结构与 Azure AD 集成，或与本地标识基础结构或第三方标识提供程序联合。对于在 Azure 中运行的 VM，可以将本地标识基础结构（如 Windows Server AD）扩展到 VM 驻留的虚拟网络 (VNet)。</span><span class="sxs-lookup"><span data-stu-id="a46a8-p104">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform. For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers. For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Windows Server AD, to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="a46a8-123">用于三阶段云应用流程的混合云方案</span><span class="sxs-lookup"><span data-stu-id="a46a8-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="a46a8-p105">许多企业（包括 Microsoft 的企业）都使用三阶段方法来应用云。混合云方案可以在每个阶段发挥作用。</span><span class="sxs-lookup"><span data-stu-id="a46a8-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="a46a8-126">将工作效率工作负荷移动到 SaaS</span><span class="sxs-lookup"><span data-stu-id="a46a8-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="a46a8-127">对于当前位于或必须保持在本地的工作效率工作负荷，混合方案允许其与对应的云集成。</span><span class="sxs-lookup"><span data-stu-id="a46a8-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="a46a8-128">在 Azure PaaS 中开发新的和现代应用程序</span><span class="sxs-lookup"><span data-stu-id="a46a8-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="a46a8-129">Azure PaaS 混合应用程序可以安全地利用本地服务器或存储资源。</span><span class="sxs-lookup"><span data-stu-id="a46a8-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="a46a8-130">将现有应用程序移动到 Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="a46a8-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="a46a8-131">对于提升转移以及内置云方案，在 Azure VM 上运行的基于服务器的应用程序提供了便利的预配和缩放功能。</span><span class="sxs-lookup"><span data-stu-id="a46a8-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a46a8-132">See Also</span><span class="sxs-lookup"><span data-stu-id="a46a8-132">See Also</span></span>

[<span data-ttu-id="a46a8-133">面向企业架构师的 Microsoft 混合云</span><span class="sxs-lookup"><span data-stu-id="a46a8-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="a46a8-134">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="a46a8-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="a46a8-135">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="a46a8-135">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



