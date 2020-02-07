---
title: 可访问的图 - Microsoft Lync 2013 平台选项
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
f1.keywords:
- NOCSH
description: 本文是名为 Microsoft Exchange 2013 平台选项的图的可访问文本版本，您可在技术图表中找到此图。
ms.openlocfilehash: ff03899a57ff7fbd902cd3cacfc2005d27595c55
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844633"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="cbdd1-103">可访问的图 - Microsoft Lync 2013 平台选项</span><span class="sxs-lookup"><span data-stu-id="cbdd1-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="cbdd1-104">**摘要：** 本文是[技术图表](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)中的“Microsoft Lync 2013 平台选项”图表的可访问文本版本。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="cbdd1-105">本海报介绍哪些业务决策者 (BDM) 和架构师需要了解 Lync Online (Office 365) 和 Lync Server 部署，其中包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="cbdd1-106">四个不同的部署选项比较：Lync Online (Office 365)、Lync Online/Server 混合、Lync Server 和提供程序承载的 Lync Server。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="cbdd1-107">部署 Lync 2013 的两个示例方案。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="cbdd1-108">Lync 2013 平台的四种不同部署比较</span><span class="sxs-lookup"><span data-stu-id="cbdd1-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="cbdd1-109">比较提供了每个部署选项的信息，包括以下方面：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="cbdd1-110">不同的部署功能的概述</span><span class="sxs-lookup"><span data-stu-id="cbdd1-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="cbdd1-111">实施每个部署选项的优点</span><span class="sxs-lookup"><span data-stu-id="cbdd1-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="cbdd1-112">许可要求</span><span class="sxs-lookup"><span data-stu-id="cbdd1-112">Licensing requirements</span></span>
    
- <span data-ttu-id="cbdd1-113">所需的体系结构任务</span><span class="sxs-lookup"><span data-stu-id="cbdd1-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="cbdd1-114">IT 专业人员对实施每个部署选项的职责</span><span class="sxs-lookup"><span data-stu-id="cbdd1-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="cbdd1-115">概述</span><span class="sxs-lookup"><span data-stu-id="cbdd1-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="cbdd1-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="cbdd1-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="cbdd1-117">使用 Office 365 多租户计划提高效率并优化成本。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="cbdd1-118">随附的图显示了具有 Azure Active Directory 租户的 Lync Online，它可在本地 Active Directory 域服务 (AD DS) 环境和 Azure Active Directory 租户之间同步帐户名称和密码。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="cbdd1-119">功能描述：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="cbdd1-120">软件即服务 (SaaS)。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="cbdd1-121">始终保持最新的丰富功能集。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="cbdd1-122">包括用于联机帐户的 Azure Active Directory 租户（可用于其他应用程序）。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="cbdd1-123">目录集成包括同步本地 Active Directory 域服务 (AD DS) 环境和 Azure Active Directory 租户之间的帐户名称和密码。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="cbdd1-124">如果需要单一登录 (SSO)，可实施 Active Directory 联合身份验证服务 (AD FS)。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="cbdd1-125">通过 Internet 的客户端通信将会加密并进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="cbdd1-126">对于传统电话设备和公共交换电话网络 (PSTN)，连接通过第三方提供程序实现。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="cbdd1-127">Lync Online/Server 混合（拆分域）</span><span class="sxs-lookup"><span data-stu-id="cbdd1-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="cbdd1-128">您可以将 Office 365 的优势与 Lync 2013 的本地部署相结合。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="cbdd1-p101">随附的图中显示具有 Lync Online 的 Office 365，其中部分用户位于本地，部分用户处于联机状态。此外还显示了部署在本地的边缘服务器。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="cbdd1-131">功能描述：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="cbdd1-132">部分用户位于本地，部分用户处于联机状态，但用户共享同一个 SIP 域（例如 contoso.com）。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="cbdd1-133">利用您现有的 Lync Server 2013 基础结构，包括到 PSTN 的连接。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="cbdd1-134">当用户不需要 PSTN 时轻松添加新的 Lync Online 用户。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="cbdd1-135">按照您的安排，在一段时间后从 Lync 本地迁移到 Lync Online。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="cbdd1-136">与其他 Office 365 应用程序集成，包括 Exchange Online 和 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="cbdd1-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-137">Lync Server</span></span>

<span data-ttu-id="cbdd1-p102">在该部署中，您掌控一切。随附的图显示了具有本地 Active Directory 域服务 (AD DS) 环境的 Lync Server 基础结构，其中用户位于本地。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="cbdd1-140">功能描述：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="cbdd1-141">容量规划和大小。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="cbdd1-142">服务器购置和设置。 </span><span class="sxs-lookup"><span data-stu-id="cbdd1-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="cbdd1-143">部署。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-143">Deployment.</span></span>
    
- <span data-ttu-id="cbdd1-144">横向扩展、修补和操作。  </span><span class="sxs-lookup"><span data-stu-id="cbdd1-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="cbdd1-145">备份数据。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-145">Backing up data.</span></span>
    
- <span data-ttu-id="cbdd1-146">维护故障转移和灾难恢复。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="cbdd1-147">将您的 Lync Server 2013 基础结构连接到 PSTN。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="cbdd1-148">与现有电话设备集成，如专用分组交换机 (PBX)。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="cbdd1-149">提供商承载的 Lync Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="cbdd1-p103">在该部署中，您的提供商掌控一切。随附的图显示了提供商的网络，其中包括他们的服务器和设备以及到本地环境的连接。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="cbdd1-152">功能描述：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="cbdd1-153">容量规划和大小。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="cbdd1-154">服务器购置和设置。 </span><span class="sxs-lookup"><span data-stu-id="cbdd1-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="cbdd1-155">部署。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-155">Deployment.</span></span>
    
- <span data-ttu-id="cbdd1-156">横向扩展、修补和操作。  </span><span class="sxs-lookup"><span data-stu-id="cbdd1-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="cbdd1-157">备份数据。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-157">Backing up data.</span></span>
    
- <span data-ttu-id="cbdd1-158">维护故障转移和灾难恢复。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="cbdd1-159">与现有电话设备集成，如专用分组交换机 (PBX)。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="cbdd1-160">此外，提供商还可以：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="cbdd1-161">在自己的网络中安装他们的服务器和设备，并连接到您的内部部署（实线）。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="cbdd1-162">在本地安装他们的服务器（虚线）。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="cbdd1-163">实现每个部署选项的优点</span><span class="sxs-lookup"><span data-stu-id="cbdd1-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="cbdd1-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="cbdd1-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="cbdd1-165">本地服务器或服务器软件没有运营负担。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="cbdd1-166">Lync Server 2013 作为基于云的服务的通信功能。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="cbdd1-167">Lync 状态、即时消息、音频和视频呼叫、丰富的在线会议和一系列 Web 会议功能。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="cbdd1-168">用于地理分散的组织或主要为移动状态的员工。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="cbdd1-169">Lync Online/Server 混合（拆分域）</span><span class="sxs-lookup"><span data-stu-id="cbdd1-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="cbdd1-170">对远程用户使用 Lync Online，并与业务合作伙伴集成。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="cbdd1-171">加速从 Lync 本地到 Lync Online 的迁移。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="cbdd1-172">无需使用分支办公室设备即可支持远程站点。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="cbdd1-173">轻松增加对新业务收购的 Lync 支持。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="cbdd1-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-174">Lync Server</span></span>

- <span data-ttu-id="cbdd1-175">私有云解决方案。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="cbdd1-176">高度自定义的解决方案。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="cbdd1-177">具有第三方组件的旧版解决方案，而这些组件依赖于不受 Lync Online 支持的硬件和软件。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="cbdd1-178">阻止 AD DS 帐户与 Office 365 同步的隐私限制。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="cbdd1-179">希望保持对整个平台和解决方案的控制的组织。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="cbdd1-180">Lync Enterprise Voice 取代 PBX。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="cbdd1-181">提供商承载的 Lync Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="cbdd1-182">需要 Lync Server 功能，但希望外包其部署和维护的组织。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="cbdd1-183">基于提供商的解决方案</span><span class="sxs-lookup"><span data-stu-id="cbdd1-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="cbdd1-184">高度自定义的解决方案。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="cbdd1-185">具有第三方组件的旧版解决方案，而这些组件依赖于不受 Lync Online 支持的硬件和软件。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="cbdd1-186">Lync Enterprise Voice 取代 PBX。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="cbdd1-187">许可要求</span><span class="sxs-lookup"><span data-stu-id="cbdd1-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="cbdd1-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="cbdd1-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="cbdd1-189">订阅模型。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="cbdd1-190">Lync Online/Server 混合（拆分域）</span><span class="sxs-lookup"><span data-stu-id="cbdd1-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="cbdd1-p104">Office 365  订阅模型。无需其他许可证。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="cbdd1-193">本地 — 所有本地许可证均适用。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="cbdd1-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-194">Lync Server</span></span>

- <span data-ttu-id="cbdd1-195">服务器操作系统</span><span class="sxs-lookup"><span data-stu-id="cbdd1-195">Server Operating System</span></span>
    
- <span data-ttu-id="cbdd1-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-196">SQL Server</span></span>
    
- <span data-ttu-id="cbdd1-197">Lync 2013 Server 许可证</span><span class="sxs-lookup"><span data-stu-id="cbdd1-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="cbdd1-198">Lync 2013 客户端访问许可证</span><span class="sxs-lookup"><span data-stu-id="cbdd1-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="cbdd1-199">提供商承载的 Lync Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="cbdd1-200">成本基于与 Lync 解决方案提供商签订的协议。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="cbdd1-201">体系结构任务</span><span class="sxs-lookup"><span data-stu-id="cbdd1-201">Architecture tasks</span></span>

<span data-ttu-id="cbdd1-202">本节列出了每个部署选项的体系结构任务。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="cbdd1-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="cbdd1-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="cbdd1-204">规划和设计目录同步。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="cbdd1-205">确保通过防火墙、代理服务器、网关以及跨 WAN 链接的网络容量和可用性。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="cbdd1-206">获取第三方 SSL 证书，提供 Office 365 服务/产品的企业安全性。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="cbdd1-207">决定是否要使用 Internet 协议版本 6 (IPv6) 连接到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="cbdd1-208">Lync Online/Server 混合（拆分域）</span><span class="sxs-lookup"><span data-stu-id="cbdd1-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="cbdd1-209">除 Office 365 和本地环境的任务以外，还需：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="cbdd1-210">确定您希望在 Exchange Server 和 SharePoint 的本地版本和联机版本中使用多少功能集成。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="cbdd1-211">确定对于 Office 365 的请求将使用哪个代理服务器设备（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="cbdd1-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-212">Lync Server</span></span>

<span data-ttu-id="cbdd1-213">在现有本地环境中设计 Lync 环境：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="cbdd1-214">中央和分支办公室的 Lync 拓扑。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="cbdd1-215">服务器硬件，包括虚拟化。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="cbdd1-216">与 Active Directory 域服务 (AD DS) 和 DNS 集成。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="cbdd1-217">Lync 服务器池的负载平衡。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="cbdd1-218">故障转移和灾难恢复。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="cbdd1-219">提供商承载的 Lync Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="cbdd1-220">对于基于云的安装，确定到服务提供商网络的连接。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="cbdd1-221">对于本地安装，确定提供商的 Lync 服务器在网络中的位置。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="cbdd1-222">对于两种类型的安装，确定 AD DS 与您的 PBX 设备的集成。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="cbdd1-223">IT 专业人员的职责</span><span class="sxs-lookup"><span data-stu-id="cbdd1-223">IT Pro responsibilities</span></span>

<span data-ttu-id="cbdd1-224">本节列出了 IT 专业人员对每个部署选项的职责。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="cbdd1-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="cbdd1-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="cbdd1-226">部署和管理 Lync Online (Office 365)：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="cbdd1-227">实施目录同步计划。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="cbdd1-228">规划和实施内部和外部 DNS 记录和路由。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="cbdd1-229">针对 Office 365 IP 地址和 URL 要求配置代理或防火墙。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="cbdd1-230">管理用户帐户和 Lync Online 设置。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="cbdd1-231">Lync Online/Server 混合（拆分域）</span><span class="sxs-lookup"><span data-stu-id="cbdd1-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="cbdd1-232">除 Office 365 和本地环境的任务以外，还需：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="cbdd1-233">配置代理服务器设备（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="cbdd1-234">配置与 Exchange Server 和 SharePoint 的本地版本和联机版本的功能集成。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="cbdd1-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-235">Lync Server</span></span>

<span data-ttu-id="cbdd1-236">在本地环境中部署和管理 Lync Server：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="cbdd1-237">设置服务器。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-237">Provision the servers.</span></span>
    
- <span data-ttu-id="cbdd1-238">部署 Lync 拓扑。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="cbdd1-239">更新 Lync 服务器。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="cbdd1-240">按需要根据使用率添加或删除拓扑服务器。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="cbdd1-241">实施故障转移和灾难恢复环境。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="cbdd1-242">提供商承载的 Lync Server</span><span class="sxs-lookup"><span data-stu-id="cbdd1-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="cbdd1-243">与提供商合作以：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="cbdd1-244">将 Lync Server 集成到您的网络中。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="cbdd1-245">将 Lync Server 与其他 Microsoft 产品或自定义解决方案集成。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="cbdd1-246">监控提供商服务级别协议 (SLA) 的遵守情况。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="cbdd1-247">部署 Lync 2013 的两个示例方案</span><span class="sxs-lookup"><span data-stu-id="cbdd1-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="cbdd1-248">Microsoft Azure 中的目录同步组件</span><span class="sxs-lookup"><span data-stu-id="cbdd1-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="cbdd1-249">根据需要部署虚拟机的能力使得在 Azure 中部署 Office 365 目录同步组件更加快捷。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="cbdd1-250">随附的图显示了具有 Azure Active Directory 租户的 Lync Online，它可在本地 Active Directory 环境和 Azure Active Directory 租户之间同步帐户名称和密码。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="cbdd1-p105">**仅限目录同步服务器**。不在本地环境中部署 64 位目录同步，而应通过 Internet 在 Azure 中配置虚拟机。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="cbdd1-p106">**目录同步 + AD FS**。此选项使您可以支持 Office 365 联合身份 (SSO)，而无需将硬件添加到内部部署基础架构。如果本地 Active Directory 环境不可用，它还可以提供复原。此选项的功能包括：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="cbdd1-257">目录集成组件作为 Azure 虚拟机运行。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="cbdd1-258">通过作为 Azure 虚拟机运行的 AD FS 代理将 AD FS 发布到 Internet。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="cbdd1-259">对于从任何位置连接的用户，客户端身份验证通信由部署为 Azure 虚拟机的 AD FS 服务器和代理处理。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="cbdd1-260">Office 365 中与 Exchange 和 SharePoint 的 Lync 集成</span><span class="sxs-lookup"><span data-stu-id="cbdd1-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="cbdd1-261">Lync Server with Exchange Online 和 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cbdd1-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="cbdd1-262">随附的图显示了连接到本地 Lync Server 2013 服务器场的 Office 365 with Exchange Online 和 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="cbdd1-263">此部署的优势使您能够：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="cbdd1-264">使用 Lync Server 2013 的完整功能集。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="cbdd1-265">利用现有的本地电话设备，例如 PBX。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="cbdd1-266">将 Exchange Online 用于电子邮件，减轻本地电子邮件服务器和存储的负担。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="cbdd1-267">将 SharePoint Online 用于协作，减轻维护本地 SharePoint 服务器的负担。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="cbdd1-268">使用 Lync、Exchange 和 SharePoint 集成功能，包括 Office 365 中的统一消息 (UM)。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="cbdd1-269">Exchange Server with Lync Online</span><span class="sxs-lookup"><span data-stu-id="cbdd1-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="cbdd1-270">随附的图显示了连接到本地 Exchange Server 服务器场的 Office 365 with Lync Online。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="cbdd1-271">此部署的优势使您能够：</span><span class="sxs-lookup"><span data-stu-id="cbdd1-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="cbdd1-272">利用现有的 Exchange 基础结构。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="cbdd1-273">将 Lync Online 用于状态、即时消息和会议功能。</span><span class="sxs-lookup"><span data-stu-id="cbdd1-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

