---
title: 可访问的图 - Microsoft Exchange 2013 平台选项
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: 本文是名为 Microsoft Exchange 2013 平台选项的图的可访问文本版本，您可在技术图表中找到此图。
ms.openlocfilehash: ddf215544b811257e6d43f212784a3a1e5aac7b0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068588"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="cbc8e-103">可访问的图 - Microsoft Exchange 2013 平台选项</span><span class="sxs-lookup"><span data-stu-id="cbc8e-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="cbc8e-104">**摘要：** 本文是[技术图表](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)中的“Microsoft Exchange 2013 平台选项”图表的可访问文本版本。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="cbc8e-105">本海报介绍哪些业务决策者 (BDM) 和架构师需要了解 Exchange Online 与 Exchange Server 部署，其中包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="cbc8e-106">Exchange 2013 的四个可用平台选项的比较: Exchange Online (Office 365)、Exchange 混合、Exchange Server 本地和提供商托管的 Exchange。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="cbc8e-107">描述 Exchange 2013 中的三项新功能或更新功能。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="cbc8e-108">Exchange 2013 平台的四种不同部署比较</span><span class="sxs-lookup"><span data-stu-id="cbc8e-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="cbc8e-109">比较提供了每个部署选项的信息，包括以下方面：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="cbc8e-110">不同的部署功能的概述</span><span class="sxs-lookup"><span data-stu-id="cbc8e-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="cbc8e-111">实施每个部署选项的优点</span><span class="sxs-lookup"><span data-stu-id="cbc8e-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="cbc8e-112">许可要求</span><span class="sxs-lookup"><span data-stu-id="cbc8e-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="cbc8e-113">所需的体系结构任务</span><span class="sxs-lookup"><span data-stu-id="cbc8e-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="cbc8e-114">IT 专业人员对实施每个部署选项的职责</span><span class="sxs-lookup"><span data-stu-id="cbc8e-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="cbc8e-115">概述</span><span class="sxs-lookup"><span data-stu-id="cbc8e-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="cbc8e-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="cbc8e-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="cbc8e-117">使用 Office 365 可提高效率并降低成本。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="cbc8e-118">随附的图显示了具有 Azure Active Directory 租户的 Exchange Online, 该租户可同步内部部署 Active Directory 域服务 (AD DS) 环境和 Azure Active Directory 租户之间的帐户名称和密码。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-118">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> <span data-ttu-id="cbc8e-119">Active Directory 联合身份验证服务 (AD FS) 是单一登录的必要条件。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-119">Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="cbc8e-120">功能描述：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="cbc8e-121">服务器和服务器软件的操作由 Microsoft 负责。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="cbc8e-122">作为基于云的服务的 Exchange Server 2013 的丰富功能集。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="cbc8e-123">始终与最新功能保持最新。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="cbc8e-124">包含 Exchange Online Protection (EOP) 以提供反垃圾邮件/反恶意软件保护。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="cbc8e-125">通过 99.9% 服务级别协议 (SLA) 实现的内置高可用性。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="cbc8e-126">目录同步, 包括本地 Active Directory 域服务 (AD DS) 和 Azure Active Directory 租户之间的密码。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-126">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant.</span></span> <span data-ttu-id="cbc8e-127">Active Directory 联合身份验证服务 (AD FS) 是单一登录的必要条件。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-127">Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="cbc8e-128">Exchange 混合</span><span class="sxs-lookup"><span data-stu-id="cbc8e-128">Exchange Hybrid</span></span>

<span data-ttu-id="cbc8e-129">您可以利用 Office 365 的优势, 同时维护本地 Exchange Server。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="cbc8e-130">随附的图显示了 Office 365 Exchange Online, 其中某些用户驻留在本地, 并且某些用户是在线托管的。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-130">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online.</span></span> <span data-ttu-id="cbc8e-131">它还显示了在内部部署 Active Directory 域服务 (AD DS) 环境和 Azure Active Directory 租户之间同步帐户名称和密码的 Azure Active Directory 租户。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-131">It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="cbc8e-132">功能描述：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="cbc8e-133">部分用户位于内部部署中，部分用户处于联机状态，且用户共享同一个电子邮件地址空间。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="cbc8e-134">利用现有的 Exchange Server 基础结构。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="cbc8e-135">按照您的安排，在一段时间后从 Exchange 内部部署迁移到 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="cbc8e-136">与其他 Office 365 应用程序集成, 包括 Lync Online 和 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="cbc8e-137">Exchange Server 内部部署</span><span class="sxs-lookup"><span data-stu-id="cbc8e-137">Exchange Server on-premises</span></span>

<span data-ttu-id="cbc8e-138">您可以设计和管理自己的 Exchange Server 2013 基础结构。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="cbc8e-139">随附的图显示了具有内部部署 Active Directory 域服务 (AD DS) 环境的 Exchange Server 基础结构，其中用户位于内部部署中。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="cbc8e-140">功能描述：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="cbc8e-141">对配置最大程度的控制和自定义。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="cbc8e-142">无需在负载平衡层维护会话相关性。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="cbc8e-143">使用数据库可用性组 (DAG) 的简单的高可用性和站点恢复。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="cbc8e-144">托管可用性，可帮助您保持出色的用户体验。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="cbc8e-145">利用现有的硬件和存储基础结构。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="cbc8e-146">提供商承载的 Exchange</span><span class="sxs-lookup"><span data-stu-id="cbc8e-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="cbc8e-147">您可以将 Exchange Server 工作量外包给 Exchange Server 解决方案提供商。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="cbc8e-148">随附的图显示了由提供商运行和维护的 Exchange Server 环境。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="cbc8e-149">功能描述：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="cbc8e-150">服务器和服务器软件的操作由提供商负责。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="cbc8e-151">Exchange Server 基础结构的规划、大小调整、比例缩放和维护均委托给提供商。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="cbc8e-152">服务维护由提供商负责。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="cbc8e-153">Exchange 功能集仅限于提供商部署的软件版本。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="cbc8e-154">实现每个部署选项的优点</span><span class="sxs-lookup"><span data-stu-id="cbc8e-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="cbc8e-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="cbc8e-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="cbc8e-156">此部署选项最适合于：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="cbc8e-157">希望降低内部部署 Exchange 的运营成本的组织。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="cbc8e-158">计划利用其他 Office 365 产品的组织, 如 SharePoint Online 和 Lync Online。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="cbc8e-159">Exchange 混合</span><span class="sxs-lookup"><span data-stu-id="cbc8e-159">Exchange Hybrid</span></span>

<span data-ttu-id="cbc8e-160">此部署选项最适合于：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="cbc8e-161">加速从 Exchange 内部部署到 Exchange Online 的迁移。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="cbc8e-162">支持远程站点，而无需投资分支机构基础结构。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="cbc8e-163">需要将数据维护在内部部署中的具有分公司的跨国企业。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="cbc8e-164">Exchange Server 内部部署</span><span class="sxs-lookup"><span data-stu-id="cbc8e-164">Exchange Server on-premises</span></span>

<span data-ttu-id="cbc8e-165">此部署选项最适合于：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="cbc8e-166">高度自定义的解决方案。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="cbc8e-167">具有第三方组件的旧版解决方案，而这些组件依赖于不受 Exchange Online 支持的硬件和软件。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="cbc8e-168">受数据管理法规限制需要将数据维护在内部部署中的组织。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="cbc8e-169">希望保持对整个平台和解决方案的控制的组织。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="cbc8e-170">提供商承载的 Exchange</span><span class="sxs-lookup"><span data-stu-id="cbc8e-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="cbc8e-171">此部署选项最适合于：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="cbc8e-172">需要 Exchange Server 功能，但希望外包其部署和维护的组织。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="cbc8e-173">需要个性化支持选项的组织。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="cbc8e-174">自定义解决方案，以及与提供商提供的自定义应用程序集成。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="cbc8e-175">具有第三方组件的旧版解决方案，而这些组件依赖于不受 Exchange Online 支持的硬件和软件。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="cbc8e-176">许可要求</span><span class="sxs-lookup"><span data-stu-id="cbc8e-176">License requirements</span></span>

<span data-ttu-id="cbc8e-177">下表详细说明了每个部署选项的许可要求。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="cbc8e-178">**部署选项**</span><span class="sxs-lookup"><span data-stu-id="cbc8e-178">**Deployment option**</span></span>|<span data-ttu-id="cbc8e-179">**许可要求**</span><span class="sxs-lookup"><span data-stu-id="cbc8e-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cbc8e-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="cbc8e-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="cbc8e-181">订阅模型</span><span class="sxs-lookup"><span data-stu-id="cbc8e-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="cbc8e-182">Exchange 混合</span><span class="sxs-lookup"><span data-stu-id="cbc8e-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="cbc8e-183">Office 365-订阅模型</span><span class="sxs-lookup"><span data-stu-id="cbc8e-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="cbc8e-184">本地-所有本地许可证均适用 (审查本地的交换服务器的许可证)</span><span class="sxs-lookup"><span data-stu-id="cbc8e-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="cbc8e-185">混合服务器许可证\*</span><span class="sxs-lookup"><span data-stu-id="cbc8e-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="cbc8e-186">Exchange Server 内部部署</span><span class="sxs-lookup"><span data-stu-id="cbc8e-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="cbc8e-187">服务器操作系统</span><span class="sxs-lookup"><span data-stu-id="cbc8e-187">Server Operating System</span></span> <br/>  <span data-ttu-id="cbc8e-188">Exchange 2013 服务器许可证</span><span class="sxs-lookup"><span data-stu-id="cbc8e-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="cbc8e-189">Exchange 2013 客户端访问许可证</span><span class="sxs-lookup"><span data-stu-id="cbc8e-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="cbc8e-190">提供商承载的 Exchange</span><span class="sxs-lookup"><span data-stu-id="cbc8e-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="cbc8e-191">成本基于与提供商签订的协议</span><span class="sxs-lookup"><span data-stu-id="cbc8e-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="cbc8e-192">体系结构任务</span><span class="sxs-lookup"><span data-stu-id="cbc8e-192">Architecture tasks</span></span>

<span data-ttu-id="cbc8e-193">本节列出了每个部署选项的体系结构任务。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="cbc8e-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="cbc8e-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="cbc8e-195">规划和设计目录同步。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="cbc8e-196">确保通过防火墙、代理服务器、网关以及跨 WAN 链接的网络容量和连接。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="cbc8e-197">Exchange 混合</span><span class="sxs-lookup"><span data-stu-id="cbc8e-197">Exchange Hybrid</span></span>

<span data-ttu-id="cbc8e-198">除了 Office 365 和本地环境的体系结构任务之外:</span><span class="sxs-lookup"><span data-stu-id="cbc8e-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="cbc8e-199">决定是否提供单一登录体验。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="cbc8e-200">决定是通过内部部署组织还是通过 Exchange Online Protection 路由入站 Internet 邮件。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="cbc8e-201">Exchange Server 内部部署</span><span class="sxs-lookup"><span data-stu-id="cbc8e-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="cbc8e-202">设计 Exchange 拓扑。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="cbc8e-203">规划服务器硬件的容量。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="cbc8e-204">设计邮件路由拓扑。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="cbc8e-205">设计客户端访问服务器的负载平衡。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="cbc8e-206">使用数据库可用性组规划高可用性。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="cbc8e-207">提供商承载的 Exchange</span><span class="sxs-lookup"><span data-stu-id="cbc8e-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="cbc8e-208">确保通过防火墙、代理服务器、网关以及跨 WAN 链接的网络容量和可用性对您的提供商可用。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="cbc8e-209">IT 专业人员的职责</span><span class="sxs-lookup"><span data-stu-id="cbc8e-209">IT Pro responsibilities</span></span>

<span data-ttu-id="cbc8e-210">本节列出了 IT 专业人员对每个部署选项的职责。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="cbc8e-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="cbc8e-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="cbc8e-212">实施目录同步计划。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="cbc8e-213">规划和实施内部和外部 DNS 记录和路由。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="cbc8e-214">为 Office 365 IP 地址和 URL 要求配置代理服务器或防火墙。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="cbc8e-215">管理用户帐户和 Exchange Online 设置。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="cbc8e-216">Exchange 混合</span><span class="sxs-lookup"><span data-stu-id="cbc8e-216">Exchange Hybrid</span></span>

<span data-ttu-id="cbc8e-217">除了针对 Office 365 和本地环境的 IT 专业人员责任之外:</span><span class="sxs-lookup"><span data-stu-id="cbc8e-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="cbc8e-218">配置 Active Directory 联合身份验证服务 (AD FS) 以实现单一登录（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="cbc8e-219">配置 exchange 证书以用于在 Exchange 2013 服务器和 Office 365 之间进行安全通信。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="cbc8e-220">为所需的入站 Internet 邮件路径配置 DNS 记录。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="cbc8e-221">Exchange Server 内部部署</span><span class="sxs-lookup"><span data-stu-id="cbc8e-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="cbc8e-222">配置 Exchange 服务的必要证书。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="cbc8e-223">设置服务器。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-223">Provision the servers.</span></span>
    
- <span data-ttu-id="cbc8e-224">实施 Exchange 邮件路由拓扑。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="cbc8e-225">实施数据库可用性组。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="cbc8e-226">更新和维护 Exchange 服务器。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="cbc8e-227">按照利用情况，根据需要添加或删除服务器。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="cbc8e-228">提供商承载的 Exchange</span><span class="sxs-lookup"><span data-stu-id="cbc8e-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="cbc8e-229">提供商的职责包括:</span><span class="sxs-lookup"><span data-stu-id="cbc8e-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="cbc8e-230">系统和服务维护。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="cbc8e-231">功能的首次推出。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="cbc8e-232">数据保护和灾难恢复。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="cbc8e-233">IT 员工在您的组织中的职责包括创建和管理用户帐户。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="cbc8e-234">更多信息</span><span class="sxs-lookup"><span data-stu-id="cbc8e-234">More information</span></span>

<span data-ttu-id="cbc8e-235">若要了解有关 Exchange Online (Office 365) 的详细信息, 请参阅以下内容:</span><span class="sxs-lookup"><span data-stu-id="cbc8e-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="cbc8e-236">Exchange Online 服务说明</span><span class="sxs-lookup"><span data-stu-id="cbc8e-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="cbc8e-237">TechNet 上的 Exchange Online 库</span><span class="sxs-lookup"><span data-stu-id="cbc8e-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="cbc8e-238">Exchange Online 门户</span><span class="sxs-lookup"><span data-stu-id="cbc8e-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="cbc8e-239">要了解有关 Exchange 混合的详细信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="cbc8e-240">[Exchange 2013 混合部署](https://aka.ms/ExchangeHybrid)。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-240">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid).</span></span> <span data-ttu-id="cbc8e-241">应注意, 混合服务器许可证仅在以下情况下是必需的: exchange 2010 组织 with Exchange 2013 混合服务器和 Exchange 2007 组织与 Exchange 2013 或 Exchange 2010 混合服务器。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-241">You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="cbc8e-242">Office 365 登录</span><span class="sxs-lookup"><span data-stu-id="cbc8e-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="cbc8e-243">要了解有关 Exchange 内部部署的详细信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="cbc8e-244">TechNet 上的 Exchange Server 2013 库</span><span class="sxs-lookup"><span data-stu-id="cbc8e-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="cbc8e-245">Exchange Server 2013 门户</span><span class="sxs-lookup"><span data-stu-id="cbc8e-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="cbc8e-246">Exchange Server 2013 体系结构</span><span class="sxs-lookup"><span data-stu-id="cbc8e-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="cbc8e-247">要了解有关提供商承载的 Exchange 的详细信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="cbc8e-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="cbc8e-248">Exchange Server 2013 托管和多租户解决方案和指南</span><span class="sxs-lookup"><span data-stu-id="cbc8e-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="cbc8e-249">Exchange 2013 中的三项新功能或更新功能的描述</span><span class="sxs-lookup"><span data-stu-id="cbc8e-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="cbc8e-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="cbc8e-250">Exchange Online Protection</span></span>

<span data-ttu-id="cbc8e-p105">Exchange Online Protection (EOP) 提供跨全球数据中心网络部署的保护功能层，从而提供反垃圾邮件和反恶意软件保护。这可帮助您简化邮件环境的管理。EOP 包含在 Exchange Online 订阅中，但您也可以将其用于混合部署和内部部署。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-p105">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers. This helps you to simplify the management of your messaging environments. EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="cbc8e-254">随附的图显示了在全局网络中包含 EOP 层的 Exchange Online、Exchange 混合和 Exchange 内部部署的部署。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="cbc8e-255">Exchange Server 部署助理</span><span class="sxs-lookup"><span data-stu-id="cbc8e-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="cbc8e-p106">Exchange Server 部署助理是一个基于 web 的工具，它会询问您几个关于当前环境的问题，然后生成自定义分步检查表，以帮助您为不同类型的方案部署 Exchange Server。不论您是要从 Exchange 的之前版本迁移到 Exchange 2013 还是迁移到 Exchange Online，还是要规划混合基础结构，Exchange Server 部署助理都会针对您的方案创建一个自定义部署检查表。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-p106">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios. Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="cbc8e-258">随附的屏幕截图显示了使用 Exchange Server 部署助理创建的检查表示例。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="cbc8e-259">与 Lync 和 SharePoint 集成</span><span class="sxs-lookup"><span data-stu-id="cbc8e-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="cbc8e-260">Exchange Server 2013 包括与 Lync Server 2013 和 SharePoint Server 2013 集成的许多功能。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-260">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013.</span></span> <span data-ttu-id="cbc8e-261">这些产品将一起提供一整套丰富的功能并改进整个组织的协作。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-261">Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="cbc8e-262">随附的图显示了服务器与服务器之间的身份验证海报并提供了海报的链接。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="cbc8e-263">存档、保留和电子数据展示</span><span class="sxs-lookup"><span data-stu-id="cbc8e-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="cbc8e-264">网站邮箱</span><span class="sxs-lookup"><span data-stu-id="cbc8e-264">Site mailboxes</span></span>
    
- <span data-ttu-id="cbc8e-265">统一联系人存储</span><span class="sxs-lookup"><span data-stu-id="cbc8e-265">Unified contact store</span></span>
    
- <span data-ttu-id="cbc8e-266">高分辨率用户照片</span><span class="sxs-lookup"><span data-stu-id="cbc8e-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="cbc8e-267">Outlook 和 Outlook Web App 中的 Lync 状态</span><span class="sxs-lookup"><span data-stu-id="cbc8e-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="cbc8e-268">服务器间身份验证</span><span class="sxs-lookup"><span data-stu-id="cbc8e-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="cbc8e-269">Voicemail</span><span class="sxs-lookup"><span data-stu-id="cbc8e-269">Voicemail</span></span>
    
- <span data-ttu-id="cbc8e-270">会议录制</span><span class="sxs-lookup"><span data-stu-id="cbc8e-270">Meeting recordings</span></span>
    
- <span data-ttu-id="cbc8e-271">Exchange 任务同步</span><span class="sxs-lookup"><span data-stu-id="cbc8e-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="cbc8e-272">随附的图显示了 Exchange Server 2013 SP1 体系结构海报, 并提供了海报的链接。</span><span class="sxs-lookup"><span data-stu-id="cbc8e-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

