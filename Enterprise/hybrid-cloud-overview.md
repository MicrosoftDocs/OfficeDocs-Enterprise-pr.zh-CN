---
title: 混合云概述
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: 摘要： 了解 Microsoft 混合云的定义和元素。
ms.openlocfilehash: c048cfeb840bbb03b1886c7053603cfdc84f37ab
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741428"
---
# <a name="hybrid-cloud-overview"></a><span data-ttu-id="d6d34-103">混合云概述</span><span class="sxs-lookup"><span data-stu-id="d6d34-103">Hybrid cloud overview</span></span>

 <span data-ttu-id="d6d34-104">**摘要：** 了解 Microsoft 混合云的定义和元素。</span><span class="sxs-lookup"><span data-stu-id="d6d34-104">**Summary:** Understand the definition and elements of Microsoft hybrid cloud.</span></span>
  
<span data-ttu-id="d6d34-p101">混合云使用本地网络和云中的计算或存储资源。可以使用混合云作为路径，以将业务及其 IT 需求迁移到云中，或将云平台和服务与现有的本地基础结构集成来作为整体 IT 策略的一部分。</span><span class="sxs-lookup"><span data-stu-id="d6d34-p101">Hybrid cloud uses compute or storage resources on your on-premises network and in the cloud. You can use hybrid cloud as a path to migrate your business and its IT needs to the cloud or integrate cloud platforms and services with your existing on-premises infrastructure as part of your overall IT strategy.</span></span>
  
## <a name="microsoft-hybrid-cloud"></a><span data-ttu-id="d6d34-107">Microsoft 混合云</span><span class="sxs-lookup"><span data-stu-id="d6d34-107">Microsoft hybrid cloud</span></span>

<span data-ttu-id="d6d34-108">Microsoft 混合云是一组将 Microsoft 云平台与本地组件结合使用的业务方案，如： </span><span class="sxs-lookup"><span data-stu-id="d6d34-108">Microsoft hybrid cloud is a set of business scenarios that combine a Microsoft cloud platform with an on-premises component, such as:</span></span> 
  
- <span data-ttu-id="d6d34-109">从本地 SharePoint 场中的内容和 Office 365 的 SharePoint Online 中的内容获取搜索结果。</span><span class="sxs-lookup"><span data-stu-id="d6d34-109">Getting search results from content both in an on-premises SharePoint farm and in SharePoint Online in Office 365.</span></span>
    
- <span data-ttu-id="d6d34-110">在查询本地数据存储的 Azure 中运行的移动应用。</span><span class="sxs-lookup"><span data-stu-id="d6d34-110">A mobile app running in Azure that queries an on-premises data store.</span></span>
    
- <span data-ttu-id="d6d34-111">在 Azure 虚拟机上运行的 Intranet IT 工作负荷。</span><span class="sxs-lookup"><span data-stu-id="d6d34-111">An intranet IT workload running on Azure virtual machines.</span></span>
    
**<span data-ttu-id="d6d34-112">图 1：Microsoft 混合云的组件</span><span class="sxs-lookup"><span data-stu-id="d6d34-112">Figure 1: Components of the Microsoft hybrid cloud</span></span>**

![Microsoft 混合云的组件](media/Hybrid-Poster/MS-Hybrid-Cloud.png)
  
<span data-ttu-id="d6d34-114">图 1 显示跨 Internet 或 ExpressRoute 连接提供的 Microsoft 混合云组件，从本地网络到 Office 365、Azure 平台即服务 (PaaS) 和 Azure 基础结构即服务 (IaaS) 均包含在内。</span><span class="sxs-lookup"><span data-stu-id="d6d34-114">Figure 1 shows the components of the Microsoft hybrid cloud, from an on-premises network to the set of Office 365, Azure Platform as a Service (PaaS), and Azure Infrastructure as a Service (IaaS) services available across the Internet or an ExpressRoute connection.</span></span>
  
<span data-ttu-id="d6d34-115">因为 Microsoft 拥有市场中最完整的云解决方案（包括软件即服务 (SaaS)、Paas 和 laas），你可以：</span><span class="sxs-lookup"><span data-stu-id="d6d34-115">Because Microsoft has the most complete cloud solution in the marketplace—including Software as a Service (SaaS), PaaS, and IaaS—you can:</span></span>
  
- <span data-ttu-id="d6d34-116">将工作负荷和应用程序迁移到云时，利用现有的本地投资。</span><span class="sxs-lookup"><span data-stu-id="d6d34-116">Leverage your existing on-premises investments as you migrate workloads and applications to the cloud.</span></span>
    
- <span data-ttu-id="d6d34-117">例如，当法规或策略不允许将特定的数据或工作负荷转移到云时，可将混合云方案纳入长期 IT 计划。</span><span class="sxs-lookup"><span data-stu-id="d6d34-117">Incorporate hybrid cloud scenarios into your long-term IT plans, for example, when regulations or policies do not permit moving specific data or workloads to the cloud.</span></span>
    
- <span data-ttu-id="d6d34-118">创建包含多个 Microsoft 云服务和平台的其他混合方案。</span><span class="sxs-lookup"><span data-stu-id="d6d34-118">Create additional hybrid scenarios that include multiple Microsoft cloud services and platforms.</span></span>
    
<span data-ttu-id="d6d34-119">混合云方案与 Microsoft 云服务方案因平台不同而异。</span><span class="sxs-lookup"><span data-stu-id="d6d34-119">Scenarios for hybrid cloud with Microsoft cloud services vary with the platform.</span></span>
  
- <span data-ttu-id="d6d34-120">SaaS</span><span class="sxs-lookup"><span data-stu-id="d6d34-120">SaaS</span></span>
    
    <span data-ttu-id="d6d34-121">Microsoft SaaS 服务包括 Office 365、Microsoft Intune 和 Microsoft Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="d6d34-121">Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365.</span></span> <span data-ttu-id="d6d34-122">采用 Microsoft SaaS 的混合云方案将这些服务与本地服务或应用程序相结合。</span><span class="sxs-lookup"><span data-stu-id="d6d34-122">Hybrid cloud scenarios with Microsoft SaaS combine these services with on-premises services or applications.</span></span> <span data-ttu-id="d6d34-123">例如, 在 Office 365 中运行的 Exchange Online 可以与部署在本地的 Skype for business 2019 集成。</span><span class="sxs-lookup"><span data-stu-id="d6d34-123">For example, Exchange Online running in Office 365 can be integrated with Skype for Business 2019 that is deployed on-premises.</span></span>
    
- <span data-ttu-id="d6d34-124">Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="d6d34-124">Azure PaaS</span></span>
    
    <span data-ttu-id="d6d34-p103">Microsoft Azure PaaS 服务允许你创建基于云的应用程序。采用 Microsoft PaaS 服务的混合云方案将 Azure PaaS 应用与本地资源或应用程序相结合。例如，Azure PaaS 应用可以安全地查询本地数据存储，以获取向移动应用用户进行显示所需的信息。</span><span class="sxs-lookup"><span data-stu-id="d6d34-p103">Microsoft Azure PaaS services allow you to create cloud-based applications. Hybrid cloud scenarios with Azure PaaS services combine an Azure PaaS app with on-premises resources or applications. For example, an Azure PaaS app could securely query an on-premises data store for information needed to display to mobile app users.</span></span>
    
- <span data-ttu-id="d6d34-128">Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="d6d34-128">Azure IaaS</span></span>
    
    <span data-ttu-id="d6d34-p104">借助 Azure IaaS 服务，可以在云中生成并运行基于服务器的 IT 工作负荷，而不是在本地数据中心内。采用 Azure IaaS 服务的混合云方案通常由在虚拟机上运行的 IT 工作负荷组成，该虚拟机以透明方式连接到本地网络。本地用户不会注意到这一差异。</span><span class="sxs-lookup"><span data-stu-id="d6d34-p104">Azure IaaS services allow you to build and run server-based IT workloads in the cloud, rather than in your on-premises datacenter. Hybrid cloud scenarios with Azure IaaS services typically consist of an IT workload that runs on virtual machines that is transparently connected to your on-premises network. Your on-premises users will not notice the difference.</span></span>
    
## <a name="elements-of-hybrid-cloud"></a><span data-ttu-id="d6d34-132">混合云的元素</span><span class="sxs-lookup"><span data-stu-id="d6d34-132">Elements of hybrid cloud</span></span>

<span data-ttu-id="d6d34-133">在通过 Microsoft 云平台和服务规划和实施混合云方案时，必须考虑以下元素。</span><span class="sxs-lookup"><span data-stu-id="d6d34-133">You must account for the following elements when planning and implementing hybrid cloud scenarios with Microsoft cloud platforms and services.</span></span>
  
- <span data-ttu-id="d6d34-134">网络</span><span class="sxs-lookup"><span data-stu-id="d6d34-134">Networking</span></span>
    
    <span data-ttu-id="d6d34-p105">混合云方案的网络包括到 Microsoft 云平台和服务的连接，以及可在峰值负载下保持性能的足够带宽。有关详细信息，请参阅 [面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)。</span><span class="sxs-lookup"><span data-stu-id="d6d34-p105">Networking for hybrid cloud scenarios includes the connectivity to Microsoft cloud platforms and services and enough bandwidth to be performant under peak loads. For more information, see [Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md).</span></span>
    
- <span data-ttu-id="d6d34-137">标识</span><span class="sxs-lookup"><span data-stu-id="d6d34-137">Identity</span></span>
    
    <span data-ttu-id="d6d34-138">SaaS 和 Azure PaaS 混合方案的标识可包含 Azure AD 作为公用标识提供程序, 该提供程序可以与本地 Active Directory 域服务 (AD ds) 同步, 也可以与 AD ds 或其他标识提供程序联合。</span><span class="sxs-lookup"><span data-stu-id="d6d34-138">Identity for SaaS and Azure PaaS hybrid scenarios can include Azure AD as a common identity provider, which can be synchronized with your on-premises Active Directory Domain Services (AD DS), or federated with AD DS or other identity providers.</span></span> <span data-ttu-id="d6d34-139">还可以将本地标识基础结构扩展到 Azure IaaS。</span><span class="sxs-lookup"><span data-stu-id="d6d34-139">You can also extend your on-premises Identity infrastructure to Azure IaaS.</span></span> <span data-ttu-id="d6d34-140">有关详细信息，请参阅 [企业级结构设计版的 Microsoft 云标识](microsoft-cloud-it-architecture-resources.md#identity)。</span><span class="sxs-lookup"><span data-stu-id="d6d34-140">For more information, see [Microsoft Cloud Identity for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#identity).</span></span>
    
- <span data-ttu-id="d6d34-141">安全性</span><span class="sxs-lookup"><span data-stu-id="d6d34-141">Security</span></span>
    
    <span data-ttu-id="d6d34-p107">混合云方案的安全性包括保护和管理标识、数据保护、管理权限管理、威胁感知和治理及安全策略的实施。有关详细信息，请参阅[面向企业架构师的 Microsoft 云安全性](microsoft-cloud-it-architecture-resources.md#security)。</span><span class="sxs-lookup"><span data-stu-id="d6d34-p107">Security for hybrid cloud scenarios includes protection and management for your identities, data protection, administrative privilege management, threat awareness, and the implementation of governance and security policies. For more information, see [Microsoft Cloud Security for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#security).</span></span>
    
- <span data-ttu-id="d6d34-144">管理</span><span class="sxs-lookup"><span data-stu-id="d6d34-144">Management</span></span>
    
    <span data-ttu-id="d6d34-p108">混合云方案的管理包括维护设置、数据、帐户、策略和权限以及监视正在进行的方案元素的运行状况及其性能的能力。也可使用相同的工具集（如 Systems Management Server）来管理 Azure IaaS 中的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="d6d34-p108">Management for hybrid cloud scenarios includes the ability to maintain settings, data, accounts, policies, and permissions and to monitor the ongoing health of the elements of the scenario and its performance. You can also use the same tool set, such as Systems Management Server, for managing virtual machines in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="d6d34-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6d34-147">See Also</span></span>

[<span data-ttu-id="d6d34-148">面向企业架构师的 Microsoft 混合云</span><span class="sxs-lookup"><span data-stu-id="d6d34-148">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="d6d34-149">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="d6d34-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

