---
title: SharePoint 2013 的 Microsoft Azure 体系结构
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: 'Summary: SharePoint 2013 solutions can be hosted in Microsoft Azure virtual machines. Learn which type of solutions are a good fit and how to set up Microsoft Azure to host one.'
ms.openlocfilehash: fee388f56faf2b30534d9a56926d9d62a176df19
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997889"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a><span data-ttu-id="6f51d-104">SharePoint 2013 的 Microsoft Azure 体系结构</span><span class="sxs-lookup"><span data-stu-id="6f51d-104">Microsoft Azure Architectures for SharePoint 2013</span></span>

<span data-ttu-id="6f51d-105">Azure 是用于托管 SharePoint Server 2013 解决方案的绝佳环境。</span><span class="sxs-lookup"><span data-stu-id="6f51d-105">Azure is a good environment for hosting a SharePoint Server 2013 solution.</span></span> <span data-ttu-id="6f51d-106">在大多数情况下，我们建议使用 Microsoft 365，但托管在 Azure 中的 SharePoint Server 场可以为特定解决方案提供一个不错的选择。</span><span class="sxs-lookup"><span data-stu-id="6f51d-106">In most cases, we recommend Microsoft 365, but a SharePoint Server farm hosted in Azure can be a good option for specific solutions.</span></span> <span data-ttu-id="6f51d-107">本文介绍如何构建 SharePoint 解决方案，使它们适合 Azure 平台。</span><span class="sxs-lookup"><span data-stu-id="6f51d-107">This article describes how to architect SharePoint solutions so they are a good fit in the Azure platform.</span></span> <span data-ttu-id="6f51d-108">我们将以下面两个特定解决方案为例进行说明：</span><span class="sxs-lookup"><span data-stu-id="6f51d-108">The following two specific solutions are used as examples:</span></span>
  
- [<span data-ttu-id="6f51d-109">Microsoft Azure 中的 SharePoint Server 2013 灾难恢复</span><span class="sxs-lookup"><span data-stu-id="6f51d-109">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [<span data-ttu-id="6f51d-110">Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="6f51d-110">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a><span data-ttu-id="6f51d-111">用于 Azure 基础结构服务的建议 SharePoint 解决方案</span><span class="sxs-lookup"><span data-stu-id="6f51d-111">Recommended SharePoint solutions for Azure Infrastructure Services</span></span>

<span data-ttu-id="6f51d-112">Azure infrastructure services is a compelling option for hosting SharePoint solutions.</span><span class="sxs-lookup"><span data-stu-id="6f51d-112">Azure infrastructure services is a compelling option for hosting SharePoint solutions.</span></span> <span data-ttu-id="6f51d-113">Some solutions are a better fit for this platform than others.</span><span class="sxs-lookup"><span data-stu-id="6f51d-113">Some solutions are a better fit for this platform than others.</span></span> <span data-ttu-id="6f51d-114">The following table shows recommended solutions.</span><span class="sxs-lookup"><span data-stu-id="6f51d-114">The following table shows recommended solutions.</span></span>
  
|<span data-ttu-id="6f51d-115">**解决方案**</span><span class="sxs-lookup"><span data-stu-id="6f51d-115">**Solution**</span></span>|<span data-ttu-id="6f51d-116">**为何建议将此解决方案用于 Azure**</span><span class="sxs-lookup"><span data-stu-id="6f51d-116">**Why this solution is recommended for Azure**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6f51d-117">开发和测试环境</span><span class="sxs-lookup"><span data-stu-id="6f51d-117">Development and test environments</span></span>  <br/> |<span data-ttu-id="6f51d-118">创建和管理这些环境非常容易。</span><span class="sxs-lookup"><span data-stu-id="6f51d-118">It's easy to create and manage these environments.</span></span>  <br/> |
|<span data-ttu-id="6f51d-119">将内部部署 SharePoint 服务器场灾难恢复到 Azure</span><span class="sxs-lookup"><span data-stu-id="6f51d-119">Disaster recovery of on-premises SharePoint farms to Azure</span></span>  <br/> |<span data-ttu-id="6f51d-120">**承载的辅助数据中心** 使用 Azure，而不是在其他地区投资建设辅助数据中心。</span><span class="sxs-lookup"><span data-stu-id="6f51d-120">**Hosted secondary datacenter** Use Azure instead of investing in a secondary datacenter in a different region.</span></span> <br/> <span data-ttu-id="6f51d-121">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment.</span><span class="sxs-lookup"><span data-stu-id="6f51d-121">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment.</span></span> <span data-ttu-id="6f51d-122">The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby.</span><span class="sxs-lookup"><span data-stu-id="6f51d-122">The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby.</span></span> <br/> <span data-ttu-id="6f51d-123">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements.</span><span class="sxs-lookup"><span data-stu-id="6f51d-123">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements.</span></span> <span data-ttu-id="6f51d-124">Scale in when you no longer need the resources.</span><span class="sxs-lookup"><span data-stu-id="6f51d-124">Scale in when you no longer need the resources.</span></span> <br/> <span data-ttu-id="6f51d-125">请参阅[Microsoft Azure 中的 SharePoint Server 2013 灾难恢复](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="6f51d-125">See [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span></span>  <br/> |
|<span data-ttu-id="6f51d-126">使用 Microsoft 365 中不提供的功能和规模的面向 Internet 的网站</span><span class="sxs-lookup"><span data-stu-id="6f51d-126">Internet-facing sites that use features and scale not available in Microsoft 365</span></span>  <br/> |<span data-ttu-id="6f51d-127">**集中精力** 构建一个很棒的网站，而不是构建基础结构。</span><span class="sxs-lookup"><span data-stu-id="6f51d-127">**Focus your efforts** Concentrate on building a great site rather than building infrastructure.</span></span> <br/> <span data-ttu-id="6f51d-128">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need.</span><span class="sxs-lookup"><span data-stu-id="6f51d-128">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need.</span></span> <span data-ttu-id="6f51d-129">Dynamic machine allocation is not supported (auto scale).</span><span class="sxs-lookup"><span data-stu-id="6f51d-129">Dynamic machine allocation is not supported (auto scale).</span></span> <br/> <span data-ttu-id="6f51d-130">**使用 Azure Active Directory (AD)** 利用客户帐户的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="6f51d-130">**Use Azure Active Directory (AD)** Take advantage of Azure AD for customer accounts.</span></span> <br/> <span data-ttu-id="6f51d-131">**添加 Microsoft 365 中不可用的 SharePoint 功能**添加深入报告和 web 分析。</span><span class="sxs-lookup"><span data-stu-id="6f51d-131">**Add SharePoint functionality not available in Microsoft 365** Add deep reporting and web analytics.</span></span> <br/> <span data-ttu-id="6f51d-132">请参阅[Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)。</span><span class="sxs-lookup"><span data-stu-id="6f51d-132">See [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span></span>  <br/> |
|<span data-ttu-id="6f51d-133">支持 Microsoft 365 或本地环境的应用程序场</span><span class="sxs-lookup"><span data-stu-id="6f51d-133">App farms to support Microsoft 365 or on-premises environments</span></span>  <br/> |<span data-ttu-id="6f51d-134">在 Azure 中构建、测试和承载应用程序，以支持内部部署和云环境。</span><span class="sxs-lookup"><span data-stu-id="6f51d-134">**Build, test, and host apps** in Azure to support both on-premises and cloud environments.</span></span> <br/> <span data-ttu-id="6f51d-135">在 Azure 中承载此角色，而无需为内部部署环境购买新硬件。</span><span class="sxs-lookup"><span data-stu-id="6f51d-135">**Host this role** in Azure instead of buying new hardware for on-premises environments.</span></span> <br/> |
   
<span data-ttu-id="6f51d-136">对于 Intranet 以及协作解决方案和工作负载，请考虑下列选项：</span><span class="sxs-lookup"><span data-stu-id="6f51d-136">For intranet and collaboration solutions and workloads, consider the following options:</span></span>
  
- <span data-ttu-id="6f51d-137">确定 Microsoft 365 是否满足你的业务要求，或是否可以成为解决方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="6f51d-137">Determine if Microsoft 365 meets your business requirements or can be part of the solution.</span></span> <span data-ttu-id="6f51d-138">Microsoft 365 提供了一个始终处于最新状态的丰富功能集。</span><span class="sxs-lookup"><span data-stu-id="6f51d-138">Microsoft 365 provides a rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="6f51d-139">如果 Microsoft 365 不符合你的所有业务要求，请考虑从 Microsoft 咨询服务（MCS）的本地部署 SharePoint 2013 的标准实现。</span><span class="sxs-lookup"><span data-stu-id="6f51d-139">If Microsoft 365 does not meet all your business requirements, consider a standard implementation of SharePoint 2013 on premises from Microsoft Consulting Services (MCS).</span></span> <span data-ttu-id="6f51d-140">相比自定义体系结构而言，标准体系结构的支持更快速、便宜和简单。</span><span class="sxs-lookup"><span data-stu-id="6f51d-140">A standard architecture can be a quicker, cheaper, and easier solution for you to support than a customized one.</span></span> 
    
- <span data-ttu-id="6f51d-141">如果标准实现不满足您的业务需求，请考虑使用自定义的内部部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="6f51d-141">If a standard implementation doesn't meet your business requirements, consider a customized on-premises solution.</span></span>
    
- <span data-ttu-id="6f51d-142">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services.</span><span class="sxs-lookup"><span data-stu-id="6f51d-142">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services.</span></span> <span data-ttu-id="6f51d-143">SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span><span class="sxs-lookup"><span data-stu-id="6f51d-143">SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span></span>
    
## <a name="before-you-design-the-azure-environment"></a><span data-ttu-id="6f51d-144">设计 Azure 环境之前</span><span class="sxs-lookup"><span data-stu-id="6f51d-144">Before you design the Azure environment</span></span>

<span data-ttu-id="6f51d-145">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology.</span><span class="sxs-lookup"><span data-stu-id="6f51d-145">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology.</span></span> <span data-ttu-id="6f51d-146">Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span><span class="sxs-lookup"><span data-stu-id="6f51d-146">Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span></span>
  
- [<span data-ttu-id="6f51d-147">面向 SharePoint 2013 IT 专业人员的体系结构设计</span><span class="sxs-lookup"><span data-stu-id="6f51d-147">Architecture design for SharePoint 2013 IT pros</span></span>](https://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [<span data-ttu-id="6f51d-148">Plan for performance and capacity management in SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="6f51d-148">Plan for performance and capacity management in SharePoint Server 2013</span></span>](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a><span data-ttu-id="6f51d-149">确定 Active Directory 域类型</span><span class="sxs-lookup"><span data-stu-id="6f51d-149">Determine the Active Directory domain type</span></span>

<span data-ttu-id="6f51d-150">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup.</span><span class="sxs-lookup"><span data-stu-id="6f51d-150">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup.</span></span> <span data-ttu-id="6f51d-151">At this time, there are two options for SharePoint solutions in Azure.</span><span class="sxs-lookup"><span data-stu-id="6f51d-151">At this time, there are two options for SharePoint solutions in Azure.</span></span> <span data-ttu-id="6f51d-152">These are described in the following table.</span><span class="sxs-lookup"><span data-stu-id="6f51d-152">These are described in the following table.</span></span>
  
|<span data-ttu-id="6f51d-153">**选项**</span><span class="sxs-lookup"><span data-stu-id="6f51d-153">**Option**</span></span>|<span data-ttu-id="6f51d-154">**说明**</span><span class="sxs-lookup"><span data-stu-id="6f51d-154">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6f51d-155">专用域</span><span class="sxs-lookup"><span data-stu-id="6f51d-155">Dedicated domain</span></span>  <br/> |<span data-ttu-id="6f51d-156">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm.</span><span class="sxs-lookup"><span data-stu-id="6f51d-156">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm.</span></span> <span data-ttu-id="6f51d-157">This is a good choice for public-facing Internet sites.</span><span class="sxs-lookup"><span data-stu-id="6f51d-157">This is a good choice for public-facing Internet sites.</span></span>  <br/> |
|<span data-ttu-id="6f51d-158">通过跨界连接扩展本地域</span><span class="sxs-lookup"><span data-stu-id="6f51d-158">Extend the on-premises domain through a cross-premises connection</span></span>  <br/> |<span data-ttu-id="6f51d-159">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises.</span><span class="sxs-lookup"><span data-stu-id="6f51d-159">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises.</span></span> <span data-ttu-id="6f51d-160">You can take advantage of your on-premises Active Directory and DNS implementation.</span><span class="sxs-lookup"><span data-stu-id="6f51d-160">You can take advantage of your on-premises Active Directory and DNS implementation.</span></span>  <br/> <span data-ttu-id="6f51d-161">在 Azure 中构建灾难恢复环境以便从本地服务器场进行故障转移时，将需要跨界连接。</span><span class="sxs-lookup"><span data-stu-id="6f51d-161">A cross-premises connection is required for building a disaster-recovery environment in Azure to fail over to from your on-premises farm.</span></span>  <br/> |
   
<span data-ttu-id="6f51d-162">This article includes design concepts for extending the on-premises domain through a cross-premises connection.</span><span class="sxs-lookup"><span data-stu-id="6f51d-162">This article includes design concepts for extending the on-premises domain through a cross-premises connection.</span></span> <span data-ttu-id="6f51d-163">If your solution uses a dedicated domain, you don't need a cross-premises connection.</span><span class="sxs-lookup"><span data-stu-id="6f51d-163">If your solution uses a dedicated domain, you don't need a cross-premises connection.</span></span>
  
## <a name="design-the-virtual-network"></a><span data-ttu-id="6f51d-164">设计虚拟网络</span><span class="sxs-lookup"><span data-stu-id="6f51d-164">Design the virtual network</span></span>

<span data-ttu-id="6f51d-165">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines.</span><span class="sxs-lookup"><span data-stu-id="6f51d-165">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines.</span></span> <span data-ttu-id="6f51d-166">The virtual network needs a private IP address space, portions of which you assign to the subnets.</span><span class="sxs-lookup"><span data-stu-id="6f51d-166">The virtual network needs a private IP address space, portions of which you assign to the subnets.</span></span>
  
<span data-ttu-id="6f51d-167">如果要通过（灾难恢复环境所必需的）跨域连接将本地网络扩展到 Azure，则必须选择一个未在组织网络中的任何位置使用的专用地址空间，其中可以包括您的本地环境和其他 Azure 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="6f51d-167">If you are extending your on-premises network to Azure through a cross-premises connection (required for a disaster recovery environment), you must choose a private address space that is not already in use elsewhere in your organization network, which can include your on-premises environment and other Azure virtual networks.</span></span> 
  
<span data-ttu-id="6f51d-168">**图 1：本地环境和 Azure 中的虚拟网络。**</span><span class="sxs-lookup"><span data-stu-id="6f51d-168">**Figure 1: On-premises environment with a virtual network in Azure**</span></span>

![Microsoft Azure virtual network design for a SharePoint solution.](media/OPrrasconWA-AZarch.png)
  
<span data-ttu-id="6f51d-172">在此图中：</span><span class="sxs-lookup"><span data-stu-id="6f51d-172">In this diagram:</span></span>
  
- <span data-ttu-id="6f51d-173">A virtual network in Azure is illustrated side-by-side to the on-premises environment.</span><span class="sxs-lookup"><span data-stu-id="6f51d-173">A virtual network in Azure is illustrated side-by-side to the on-premises environment.</span></span> <span data-ttu-id="6f51d-174">The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="6f51d-174">The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="6f51d-175">At this point, the virtual network just includes the subnets and no other architectural elements.</span><span class="sxs-lookup"><span data-stu-id="6f51d-175">At this point, the virtual network just includes the subnets and no other architectural elements.</span></span> <span data-ttu-id="6f51d-176">One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span><span class="sxs-lookup"><span data-stu-id="6f51d-176">One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span></span>
    
## <a name="add-cross-premises-connectivity"></a><span data-ttu-id="6f51d-177">添加跨界连接</span><span class="sxs-lookup"><span data-stu-id="6f51d-177">Add cross-premises connectivity</span></span>

<span data-ttu-id="6f51d-178">The next deployment step is to create the cross-premises connection (if this applies to your solution).</span><span class="sxs-lookup"><span data-stu-id="6f51d-178">The next deployment step is to create the cross-premises connection (if this applies to your solution).</span></span> <span data-ttu-id="6f51d-179">For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span><span class="sxs-lookup"><span data-stu-id="6f51d-179">For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span></span> 
  
<span data-ttu-id="6f51d-180">在计划跨界连接时，您将定义并创建 Azure 网关和到本地网关设备的连接。</span><span class="sxs-lookup"><span data-stu-id="6f51d-180">When you plan for a cross-premises connection, you define and create an Azure gateway and connection to an on-premises gateway device.</span></span>
  
<span data-ttu-id="6f51d-181">**图 2：使用 Azure 网关和本地网关设备提供本地环境和 Azure 之间的站点到站点连接**</span><span class="sxs-lookup"><span data-stu-id="6f51d-181">**Figure 2: Using an Azure gateway and an on-premises gateway device to provide site-to-site connectivity between the on-premises environment and Azure**</span></span>

![通过跨界连接（可以是站点到站点 VPN 连接，也可以是 ExpressRoute）连接到 Azure 虚拟网络的本地环境。](media/AZarch-VPNgtwyconnct.png)
  
<span data-ttu-id="6f51d-183">在此图中：</span><span class="sxs-lookup"><span data-stu-id="6f51d-183">In this diagram:</span></span>
  
- <span data-ttu-id="6f51d-184">添加到上图中时，本地环境将通过跨界连接（可以是站点到站点 VPN 连接，也可以是 ExpressRoute）来连接到 Azure 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="6f51d-184">Adding to the previous diagram, the on-premises environment is connected to the Azure virtual network by a cross-premise connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="6f51d-185">Azure 网关位于网关子网上。</span><span class="sxs-lookup"><span data-stu-id="6f51d-185">An Azure gateway is on a gateway subnet.</span></span>
    
- <span data-ttu-id="6f51d-186">本地环境包括网关设备，如路由器或 VPN 服务器。</span><span class="sxs-lookup"><span data-stu-id="6f51d-186">The on-premises environment includes a gateway device, such as a router or VPN server.</span></span>
    
<span data-ttu-id="6f51d-187">有关规划和创建跨界虚拟网络的其他信息，请参阅[将本地网络连接到 Microsoft Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="6f51d-187">For additional information to plan for and create a cross-premises virtual network, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a><span data-ttu-id="6f51d-188">添加 Active Directory 域服务（AD DS）和 DNS</span><span class="sxs-lookup"><span data-stu-id="6f51d-188">Add Active Directory Domain Services (AD DS) and DNS</span></span>

<span data-ttu-id="6f51d-189">在 Azure 中进行灾难恢复时，您在混合方案中部署 Windows Server AD 和 DNS，其中 Windows Server AD 部署在本地和 Azure 虚拟机上。</span><span class="sxs-lookup"><span data-stu-id="6f51d-189">For disaster recovery in Azure, you deploy Windows Server AD and DNS in a hybrid scenario where Windows Server AD is deployed both on-premises and on Azure virtual machines.</span></span>
  
<span data-ttu-id="6f51d-190">**图 3：混合 Active Directory 域配置**</span><span class="sxs-lookup"><span data-stu-id="6f51d-190">**Figure 3: Hybrid Active Directory domain configuration**</span></span>

![部署到 Azure 虚拟网络和 SharePoint 场子网的 STwo 虚拟机是域控制器和 DNS 服务器的副本](media/AZarch-HyADdomainConfig.png)
  
<span data-ttu-id="6f51d-192">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet.</span><span class="sxs-lookup"><span data-stu-id="6f51d-192">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet.</span></span> <span data-ttu-id="6f51d-193">These virtual machines are replica domain controllers and DNS servers.</span><span class="sxs-lookup"><span data-stu-id="6f51d-193">These virtual machines are replica domain controllers and DNS servers.</span></span> <span data-ttu-id="6f51d-194">They are an extension of the on-premises Windows Server AD environment.</span><span class="sxs-lookup"><span data-stu-id="6f51d-194">They are an extension of the on-premises Windows Server AD environment.</span></span> 
  
<span data-ttu-id="6f51d-195">The following table provides configuration recommendations for these virtual machines in Azure.</span><span class="sxs-lookup"><span data-stu-id="6f51d-195">The following table provides configuration recommendations for these virtual machines in Azure.</span></span> <span data-ttu-id="6f51d-196">Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span><span class="sxs-lookup"><span data-stu-id="6f51d-196">Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span></span>
  
|<span data-ttu-id="6f51d-197">**项**</span><span class="sxs-lookup"><span data-stu-id="6f51d-197">**Item**</span></span>|<span data-ttu-id="6f51d-198">**配置**</span><span class="sxs-lookup"><span data-stu-id="6f51d-198">**Configuration**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6f51d-199">Azure 中的虚拟机大小</span><span class="sxs-lookup"><span data-stu-id="6f51d-199">Virtual machine size in Azure</span></span>  <br/> |<span data-ttu-id="6f51d-200">标准层中的 A1 或 A2 大小</span><span class="sxs-lookup"><span data-stu-id="6f51d-200">A1 or A2 size in the Standard tier</span></span>  <br/> |
|<span data-ttu-id="6f51d-201">操作系统</span><span class="sxs-lookup"><span data-stu-id="6f51d-201">Operating system</span></span>  <br/> |<span data-ttu-id="6f51d-202">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6f51d-202">Windows Server 2012 R2</span></span>  <br/> |
|<span data-ttu-id="6f51d-203">Active Directory 角色</span><span class="sxs-lookup"><span data-stu-id="6f51d-203">Active Directory role</span></span>  <br/> |<span data-ttu-id="6f51d-204">AD DS domain controller designated as a global catalog server.</span><span class="sxs-lookup"><span data-stu-id="6f51d-204">AD DS domain controller designated as a global catalog server.</span></span> <span data-ttu-id="6f51d-205">This configuration reduces egress traffic across the cross-premises connection.</span><span class="sxs-lookup"><span data-stu-id="6f51d-205">This configuration reduces egress traffic across the cross-premises connection.</span></span>  <br/> <span data-ttu-id="6f51d-206">在高更改率（这并不常见）多域环境中，将内部部署域控制器配置为不与 Azure 中的全局目录服务器同步，以减少复制流量。</span><span class="sxs-lookup"><span data-stu-id="6f51d-206">In a multidomain environment with high rates of change (this is not common), configure domain controllers on premises not to sync with the global catalog servers in Azure, to reduce replication traffic.</span></span>  <br/> |
|<span data-ttu-id="6f51d-207">DNS 角色</span><span class="sxs-lookup"><span data-stu-id="6f51d-207">DNS role</span></span>  <br/> |<span data-ttu-id="6f51d-208">在域控制器上安装和配置 DNS 服务器服务。</span><span class="sxs-lookup"><span data-stu-id="6f51d-208">Install and configure the DNS Server service on the domain controllers.</span></span>  <br/> |
|<span data-ttu-id="6f51d-209">数据磁盘</span><span class="sxs-lookup"><span data-stu-id="6f51d-209">Data disks</span></span>  <br/> |<span data-ttu-id="6f51d-210">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks.</span><span class="sxs-lookup"><span data-stu-id="6f51d-210">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks.</span></span> <span data-ttu-id="6f51d-211">Do not place these on the operating system disk or the temporary disks provided by Azure.</span><span class="sxs-lookup"><span data-stu-id="6f51d-211">Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span>  <br/> |
|<span data-ttu-id="6f51d-212">IP 地址</span><span class="sxs-lookup"><span data-stu-id="6f51d-212">IP addresses</span></span>  <br/> |<span data-ttu-id="6f51d-213">使用静态 IP 地址，并在域控制器配置完毕后，将虚拟机网络配置为将这些地址分配到虚拟网络中的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="6f51d-213">Use static IP addresses and configure the virtual network to assign these addresses to the virtual machines in the virtual network after the domain controllers have been configured.</span></span>  <br/> |
   
> [!IMPORTANT]
> <span data-ttu-id="6f51d-214">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681).</span><span class="sxs-lookup"><span data-stu-id="6f51d-214">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681).</span></span> <span data-ttu-id="6f51d-215">These help you determine if a different architecture or different configuration settings are needed for your solution.</span><span class="sxs-lookup"><span data-stu-id="6f51d-215">These help you determine if a different architecture or different configuration settings are needed for your solution.</span></span> 
  
## <a name="add-the-sharepoint-farm"></a><span data-ttu-id="6f51d-216">添加 SharePoint 服务器场</span><span class="sxs-lookup"><span data-stu-id="6f51d-216">Add the SharePoint farm</span></span>

<span data-ttu-id="6f51d-217">将 SharePoint 服务器场虚拟机置于适当的子网的层级中。</span><span class="sxs-lookup"><span data-stu-id="6f51d-217">Place the virtual machines of the SharePoint farm in tiers on the appropriate subnets.</span></span>
  
<span data-ttu-id="6f51d-218">**图 4：SharePoint 虚拟机的位置**</span><span class="sxs-lookup"><span data-stu-id="6f51d-218">**Figure 4: Placement of SharePoint virtual machines**</span></span>

![添加到 SharePoint 场子网内的 Azure 虚拟网络中的数据库服务器和 SharePoint 服务器角色](media/AZarch-SPVMsinCloudSer.png)
  
<span data-ttu-id="6f51d-220">此图构建在上一张图的基础之上，它将 SharePoint 服务器场服务器角色添加到了相应的层级中。</span><span class="sxs-lookup"><span data-stu-id="6f51d-220">This diagram builds on the previous diagrams by adding the SharePoint farm server roles in their respective tiers.</span></span>
  
- <span data-ttu-id="6f51d-221">运行 SQL Server 的两个数据库虚拟机创建数据库层。</span><span class="sxs-lookup"><span data-stu-id="6f51d-221">Two database virtual machines running SQL Server create the database tier.</span></span>
    
- <span data-ttu-id="6f51d-222">运行以下每个层级的 SharePoint Server 2013 的两个虚拟机：前端服务器、分布式缓存服务器和后端服务器。</span><span class="sxs-lookup"><span data-stu-id="6f51d-222">Two virtual machines running SharePoint Server 2013 for each of the following tiers: front end servers, distributed cache servers, and back end servers.</span></span>
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a><span data-ttu-id="6f51d-223">设计和优化可用性集和错误域的服务器角色</span><span class="sxs-lookup"><span data-stu-id="6f51d-223">Design and fine tune server roles for availability sets and fault domains</span></span>

<span data-ttu-id="6f51d-224">A fault domain is a grouping of hardware in which role instances run.</span><span class="sxs-lookup"><span data-stu-id="6f51d-224">A fault domain is a grouping of hardware in which role instances run.</span></span> <span data-ttu-id="6f51d-225">Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time.</span><span class="sxs-lookup"><span data-stu-id="6f51d-225">Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time.</span></span> <span data-ttu-id="6f51d-226">Or, they can fail at the same time because they share the same rack.</span><span class="sxs-lookup"><span data-stu-id="6f51d-226">Or, they can fail at the same time because they share the same rack.</span></span> <span data-ttu-id="6f51d-227">To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain.</span><span class="sxs-lookup"><span data-stu-id="6f51d-227">To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain.</span></span> <span data-ttu-id="6f51d-228">If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span><span class="sxs-lookup"><span data-stu-id="6f51d-228">If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span></span>
  
<span data-ttu-id="6f51d-229">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set.</span><span class="sxs-lookup"><span data-stu-id="6f51d-229">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set.</span></span> <span data-ttu-id="6f51d-230">This ensures that your virtual machines are spread across multiple fault domains.</span><span class="sxs-lookup"><span data-stu-id="6f51d-230">This ensures that your virtual machines are spread across multiple fault domains.</span></span>
  
<span data-ttu-id="6f51d-231">**图 5：使用 Azure 可用性集为 SharePoint 服务器层级提供高可用性**</span><span class="sxs-lookup"><span data-stu-id="6f51d-231">**Figure 5: Use Azure Availability Sets to provide high availability for the SharePoint farm tiers**</span></span>

![SharePoint 2013 解决方案的 Azure 基础结构中的可用性集配置。](media/AZenv-WinAzureAvailSetsHA.png)
  
<span data-ttu-id="6f51d-233">This diagram calls out the configuration of availability sets within the Azure infrastructure.</span><span class="sxs-lookup"><span data-stu-id="6f51d-233">This diagram calls out the configuration of availability sets within the Azure infrastructure.</span></span> <span data-ttu-id="6f51d-234">Each of the following roles share a separate availability set:</span><span class="sxs-lookup"><span data-stu-id="6f51d-234">Each of the following roles share a separate availability set:</span></span>
  
- <span data-ttu-id="6f51d-235">Active Directory 和 DNS</span><span class="sxs-lookup"><span data-stu-id="6f51d-235">Active Directory and DNS</span></span>
    
- <span data-ttu-id="6f51d-236">数据库</span><span class="sxs-lookup"><span data-stu-id="6f51d-236">Database</span></span>
    
- <span data-ttu-id="6f51d-237">后端</span><span class="sxs-lookup"><span data-stu-id="6f51d-237">Back end</span></span>
    
- <span data-ttu-id="6f51d-238">分布式缓存</span><span class="sxs-lookup"><span data-stu-id="6f51d-238">Distribute cache</span></span>
    
- <span data-ttu-id="6f51d-239">前端</span><span class="sxs-lookup"><span data-stu-id="6f51d-239">Front end</span></span>
    
<span data-ttu-id="6f51d-240">The SharePoint farm might need to be fine tuned in the Azure platform.</span><span class="sxs-lookup"><span data-stu-id="6f51d-240">The SharePoint farm might need to be fine tuned in the Azure platform.</span></span> <span data-ttu-id="6f51d-241">To ensure high availability of all components, ensure that the server roles are all configured identically.</span><span class="sxs-lookup"><span data-stu-id="6f51d-241">To ensure high availability of all components, ensure that the server roles are all configured identically.</span></span>
  
<span data-ttu-id="6f51d-242">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals.</span><span class="sxs-lookup"><span data-stu-id="6f51d-242">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals.</span></span> <span data-ttu-id="6f51d-243">This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span><span class="sxs-lookup"><span data-stu-id="6f51d-243">This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span></span>
  
<span data-ttu-id="6f51d-244">**图 6：三层服务器场的容量和性能目标规划示例**</span><span class="sxs-lookup"><span data-stu-id="6f51d-244">**Figure 6: Planning example for capacity and performance goals in a three-tier farm**</span></span>

![具有能满足特定容量和性能目标的组件分配的标准 SharePoint 2013 Internet 网站体系结构](media/AZarch-CapPerfexmpArch.png)
  
<span data-ttu-id="6f51d-246">在此图中：</span><span class="sxs-lookup"><span data-stu-id="6f51d-246">In this diagram:</span></span>
  
- <span data-ttu-id="6f51d-247">显示了三层服务器场：Web 服务器、应用程序服务器和数据库服务器。</span><span class="sxs-lookup"><span data-stu-id="6f51d-247">A three-tier farm is represented: web servers, application servers, and database servers.</span></span>
    
- <span data-ttu-id="6f51d-248">三个 Web 服务器配置相同，均具有多个组件。</span><span class="sxs-lookup"><span data-stu-id="6f51d-248">The three web servers are configured identically with multiple components.</span></span>
    
- <span data-ttu-id="6f51d-249">两个数据库服务器的配置相同。</span><span class="sxs-lookup"><span data-stu-id="6f51d-249">The two database servers are configured identically.</span></span>
    
- <span data-ttu-id="6f51d-250">The three application servers are not configured identically.</span><span class="sxs-lookup"><span data-stu-id="6f51d-250">The three application servers are not configured identically.</span></span> <span data-ttu-id="6f51d-251">These server roles require fine tuning for availability sets in Azure.</span><span class="sxs-lookup"><span data-stu-id="6f51d-251">These server roles require fine tuning for availability sets in Azure.</span></span>
    
<span data-ttu-id="6f51d-252">让我们进一步了解一下应用程序服务器层。</span><span class="sxs-lookup"><span data-stu-id="6f51d-252">Let's look closer at the application server tier.</span></span>
  
<span data-ttu-id="6f51d-253">**图 7：优化之前的应用程序服务器层**</span><span class="sxs-lookup"><span data-stu-id="6f51d-253">**Figure 7: Application server tier before fine tuning**</span></span>

![调整 Microsoft Azure 可用性集之前的示例 SharePoint Server 2013 应用程序服务器层](media/AZarch-AppServtierBefore.png)
  
<span data-ttu-id="6f51d-255">在此图中：</span><span class="sxs-lookup"><span data-stu-id="6f51d-255">In this diagram:</span></span>
  
- <span data-ttu-id="6f51d-256">三个服务器都包含在应用程序层中。</span><span class="sxs-lookup"><span data-stu-id="6f51d-256">Three servers are included in the application tier.</span></span>
    
- <span data-ttu-id="6f51d-257">第一个服务器包含四个组件。</span><span class="sxs-lookup"><span data-stu-id="6f51d-257">The first server includes four components.</span></span>
    
- <span data-ttu-id="6f51d-258">第二个服务器包括三个组件。</span><span class="sxs-lookup"><span data-stu-id="6f51d-258">The second server includes three components.</span></span>
    
- <span data-ttu-id="6f51d-259">第三个服务器包含两个组件。</span><span class="sxs-lookup"><span data-stu-id="6f51d-259">The third server includes two components.</span></span>
    
<span data-ttu-id="6f51d-260">You determine the number of components by the performance and capacity targets for the farm.</span><span class="sxs-lookup"><span data-stu-id="6f51d-260">You determine the number of components by the performance and capacity targets for the farm.</span></span> <span data-ttu-id="6f51d-261">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span><span class="sxs-lookup"><span data-stu-id="6f51d-261">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span></span> <span data-ttu-id="6f51d-262">This increases the number of components beyond what is necessary for performance and capacity.</span><span class="sxs-lookup"><span data-stu-id="6f51d-262">This increases the number of components beyond what is necessary for performance and capacity.</span></span> <span data-ttu-id="6f51d-263">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span><span class="sxs-lookup"><span data-stu-id="6f51d-263">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span>
  
<span data-ttu-id="6f51d-264">**图 8：优化之后的应用程序服务器层**</span><span class="sxs-lookup"><span data-stu-id="6f51d-264">**Figure 8: Application server tier after fine tuning**</span></span>

![调整 Microsoft Azure 可用性集之后的示例 SharePoint Server 2013 应用程序服务器层](media/AZarch-AppServtierAfter.png)
  
<span data-ttu-id="6f51d-266">此图显示了使用相同的四个组件进行相同配置的所有三个应用程序服务器。</span><span class="sxs-lookup"><span data-stu-id="6f51d-266">This diagram shows all three application servers configured identically with the same four components.</span></span>
  
<span data-ttu-id="6f51d-267">将可用性集添加到 SharePoint 场层后，即完成实现过程。</span><span class="sxs-lookup"><span data-stu-id="6f51d-267">When we add availability sets to the tiers of the SharePoint farm, the implementation is complete.</span></span>
  
<span data-ttu-id="6f51d-268">**图 9：Azure 基础结构服务中已完成的 SharePoint 服务器场**</span><span class="sxs-lookup"><span data-stu-id="6f51d-268">**Figure 9: The completed SharePoint farm in Azure infrastructure services**</span></span>

![Azure 基础结构服务中的示例 SharePoint 2013 场，带有虚拟网络、跨界连接、子网、虚拟机和可用性集。](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
<span data-ttu-id="6f51d-270">此图显示在 Azure 基础结构服务中实现的 SharePoint 服务器场，以及为每个层级中的服务器提供故障域的可用性集。</span><span class="sxs-lookup"><span data-stu-id="6f51d-270">This diagram shows the SharePoint farm implemented in Azure infrastructure services, with availability sets to provide fault domains for the servers in each tier.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6f51d-271">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f51d-271">See Also</span></span>

[<span data-ttu-id="6f51d-272">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="6f51d-272">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)
  
[<span data-ttu-id="6f51d-273">Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="6f51d-273">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[<span data-ttu-id="6f51d-274">Microsoft Azure 中的 SharePoint Server 2013 灾难恢复</span><span class="sxs-lookup"><span data-stu-id="6f51d-274">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


