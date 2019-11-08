---
title: 可访问的图表 - SharePoint 灾难恢复到 Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: 本文是名为“SharePoint 灾难恢复到 Microsoft Azure”的图的可访问文本版本。
ms.openlocfilehash: e711452f6e019ceb280d43c2e0167507a0b0ef20
ms.sourcegitcommit: b4514cd852093181dd4c27009a78aca3ca50d2e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2019
ms.locfileid: "38038231"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="b403b-103">可访问的图表 - SharePoint 灾难恢复到 Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="b403b-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="b403b-104">**摘要：** 本文是名为 "SharePoint 灾难恢复到 Microsoft Azure" 的图表的可访问文本版本。</span><span class="sxs-lookup"><span data-stu-id="b403b-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="b403b-105">此海报提供了用于在 Azure 中构建恢复环境的体系结构的示例。 </span><span class="sxs-lookup"><span data-stu-id="b403b-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="b403b-106">具有 Azure 恢复环境的本地环境</span><span class="sxs-lookup"><span data-stu-id="b403b-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="b403b-107">此图显示了使用 Azure 进行恢复的本地环境的生产环境使用的体系结构示例。 </span><span class="sxs-lookup"><span data-stu-id="b403b-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="b403b-108">本地生产环境</span><span class="sxs-lookup"><span data-stu-id="b403b-108">On-premises production environment</span></span>

<span data-ttu-id="b403b-109">随附的图显示了在服务器场中具有四个服务器层级的真实生产环境。 </span><span class="sxs-lookup"><span data-stu-id="b403b-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="b403b-110">第 1 层</span><span class="sxs-lookup"><span data-stu-id="b403b-110">Tier 1</span></span>

<span data-ttu-id="b403b-p101">有两台服务器用于前端服务和查询处理。有一个索引分区提供两台服务器的副本。 </span><span class="sxs-lookup"><span data-stu-id="b403b-p101">There are two servers for front-end services and query processing. There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="b403b-113">第 2 层</span><span class="sxs-lookup"><span data-stu-id="b403b-113">Tier 2</span></span>

<span data-ttu-id="b403b-114">有两台服务器用于该层的分布式缓存。 </span><span class="sxs-lookup"><span data-stu-id="b403b-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="b403b-115">第 3 层</span><span class="sxs-lookup"><span data-stu-id="b403b-115">Tier 3</span></span>

<span data-ttu-id="b403b-p102">该层有三台服务器。每台服务器提供以下服务： </span><span class="sxs-lookup"><span data-stu-id="b403b-p102">There are three servers in this tier. Each server provides the following services:</span></span> 
  
- <span data-ttu-id="b403b-118">后端服务 </span><span class="sxs-lookup"><span data-stu-id="b403b-118">Backend services</span></span> 
    
- <span data-ttu-id="b403b-119">Admin</span><span class="sxs-lookup"><span data-stu-id="b403b-119">Admin</span></span> 
    
- <span data-ttu-id="b403b-120">工作流管理器</span><span class="sxs-lookup"><span data-stu-id="b403b-120">Workflow manager</span></span> 
    
- <span data-ttu-id="b403b-121">爬网</span><span class="sxs-lookup"><span data-stu-id="b403b-121">Crawl</span></span> 
    
- <span data-ttu-id="b403b-122">内容处理</span><span class="sxs-lookup"><span data-stu-id="b403b-122">Content processing</span></span> 
    
- <span data-ttu-id="b403b-123">分析</span><span class="sxs-lookup"><span data-stu-id="b403b-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="b403b-124">第 4 层</span><span class="sxs-lookup"><span data-stu-id="b403b-124">Tier 4</span></span>

<span data-ttu-id="b403b-p103">该层有两台服务器。两台服务器均具有三个可用性组，如下所示： </span><span class="sxs-lookup"><span data-stu-id="b403b-p103">There are two servers in this tier. Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="b403b-127">可用性组 #1 提供搜索功能。 </span><span class="sxs-lookup"><span data-stu-id="b403b-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="b403b-128">可用性组 #2 提供内容、配置和服务应用程序。 </span><span class="sxs-lookup"><span data-stu-id="b403b-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="b403b-129">可用性组 #3 提供内容。 </span><span class="sxs-lookup"><span data-stu-id="b403b-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="b403b-p104">该层还有一台文件共享服务器。第 4 层服务器使用日志传送与此服务器通信。该服务器反过来又会通过分布式文件系统复制 (DFSR) 与 Azure 热待机恢复环境中的文件共享服务器通信，如下面一节中所述。 </span><span class="sxs-lookup"><span data-stu-id="b403b-p104">There is also a file sharing server in this tier. The tier 4 servers use log shipping to communicate with this server. This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="b403b-133">Azure 恢复环境</span><span class="sxs-lookup"><span data-stu-id="b403b-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="b403b-134">运行虚拟机的热备用环境</span><span class="sxs-lookup"><span data-stu-id="b403b-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="b403b-p105">随附的图显示了在 Azure 恢复环境中完全复制的本地环境。此环境中的文件共享服务器通过 DFSR 链接到本地环境。DFSR 将日志通过文件共享服务器从生产环境传输到恢复环境。 </span><span class="sxs-lookup"><span data-stu-id="b403b-p105">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment. The file share server in this environment is linked to the on-premises environment through DFSR. DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="b403b-138">概述</span><span class="sxs-lookup"><span data-stu-id="b403b-138">Overview</span></span>

<span data-ttu-id="b403b-139">本地 SharePoint 2013 场的灾难恢复环境可以托管在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="b403b-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="b403b-140"> Azure 基础结构服务提供辅助的数据中心。 </span><span class="sxs-lookup"><span data-stu-id="b403b-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="b403b-141">仅为您使用的资源付费。</span><span class="sxs-lookup"><span data-stu-id="b403b-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="b403b-142">发生灾难后可将小型恢复服务器场向外扩展，以满足规模和容量目标。 </span><span class="sxs-lookup"><span data-stu-id="b403b-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="b403b-143">Azure 中的恢复服务器场配置得尽可能与生产内部部署服务器场相同。 </span><span class="sxs-lookup"><span data-stu-id="b403b-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="b403b-144">服务器角色的表示形式相同。</span><span class="sxs-lookup"><span data-stu-id="b403b-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="b403b-145">自定义配置相同。 </span><span class="sxs-lookup"><span data-stu-id="b403b-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="b403b-146">搜索功能的配置相同（可以是小型的生产服务器）。 </span><span class="sxs-lookup"><span data-stu-id="b403b-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="b403b-147">日志传送和 DFSR 用于将数据库备份和事务日志复制到 Azure 服务器场。 </span><span class="sxs-lookup"><span data-stu-id="b403b-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="b403b-p106">DFSR 用于将日志从生产环境传输到恢复环境。在 WAN 方案中，DFSR 比将日志直接传输到 Azure 中的辅助服务器更有效。</span><span class="sxs-lookup"><span data-stu-id="b403b-p106">DFSR is used to transfer logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="b403b-150">日志重放到基于 Azure 的 SQL Server 计算机。 </span><span class="sxs-lookup"><span data-stu-id="b403b-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="b403b-151">进行日志传送的数据库不会连接到服务器场，直到执行恢复操作。</span><span class="sxs-lookup"><span data-stu-id="b403b-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="b403b-152">故障转移过程： </span><span class="sxs-lookup"><span data-stu-id="b403b-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="b403b-153">停止日志传送。</span><span class="sxs-lookup"><span data-stu-id="b403b-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="b403b-154">停止接受到主服务器场通信。</span><span class="sxs-lookup"><span data-stu-id="b403b-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="b403b-155">重播最后的事务日志。</span><span class="sxs-lookup"><span data-stu-id="b403b-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="b403b-156">将内容数据库附加到服务器场。</span><span class="sxs-lookup"><span data-stu-id="b403b-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="b403b-157">启动完全爬网。</span><span class="sxs-lookup"><span data-stu-id="b403b-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="b403b-158">从复制的服务数据库中还原服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="b403b-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="b403b-159">此解决方案提供的恢复目标包括： </span><span class="sxs-lookup"><span data-stu-id="b403b-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="b403b-160">网站和内容</span><span class="sxs-lookup"><span data-stu-id="b403b-160">Sites and content</span></span> 
    
- <span data-ttu-id="b403b-161">搜索（重新爬网，无搜索历史记录） </span><span class="sxs-lookup"><span data-stu-id="b403b-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="b403b-162">服务</span><span class="sxs-lookup"><span data-stu-id="b403b-162">Services</span></span>
    
<span data-ttu-id="b403b-163">Microsoft 咨询服务或合作伙伴可以解决的其他事项： </span><span class="sxs-lookup"><span data-stu-id="b403b-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="b403b-164">正在同步的自定义场解决方案</span><span class="sxs-lookup"><span data-stu-id="b403b-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="b403b-165">到本地数据源的连接（Business Data Connectivity (BDC) 和搜索内容源） </span><span class="sxs-lookup"><span data-stu-id="b403b-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="b403b-166">搜索还原方案</span><span class="sxs-lookup"><span data-stu-id="b403b-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="b403b-167">恢复时间目标 (RTO) 和恢复点目标 (RPO)</span><span class="sxs-lookup"><span data-stu-id="b403b-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="b403b-168">运行虚拟机的冷备用环境</span><span class="sxs-lookup"><span data-stu-id="b403b-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="b403b-169">冷备用环境需要更长时间启动，但成本更低 </span><span class="sxs-lookup"><span data-stu-id="b403b-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="b403b-p107">服务器场已完全构建，但虚拟机在服务器场创建后已停止。当虚拟机运行时，您仅支付处理成本，但存储和网络数据传输成本也适用。 </span><span class="sxs-lookup"><span data-stu-id="b403b-p107">The farm is fully built, but the virtual machines are stopped after the farm is created. You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="b403b-172">如果发生灾难，服务器场中的所有虚拟机都将启动和修补。 </span><span class="sxs-lookup"><span data-stu-id="b403b-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="b403b-173">备份和事务日志将应用到服务器场数据库。 </span><span class="sxs-lookup"><span data-stu-id="b403b-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="b403b-174">以下列表介绍了冷备用环境的附加过程： </span><span class="sxs-lookup"><span data-stu-id="b403b-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="b403b-175">定期打开虚拟机以进行修补、更新并验证环境。 </span><span class="sxs-lookup"><span data-stu-id="b403b-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="b403b-176">运行相应程序以刷新 DNS 和 IP 地址。 </span><span class="sxs-lookup"><span data-stu-id="b403b-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="b403b-177">在故障转移之后设置 SQL AlwaysOn。 </span><span class="sxs-lookup"><span data-stu-id="b403b-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="b403b-p108">随附的图显示了虚拟机上的复制恢复环境。故障转移到冷备用环境后，所有虚拟机均已启动，且所有可用性组均已使用重放日志配置为提供数据库服务器。 </span><span class="sxs-lookup"><span data-stu-id="b403b-p108">The accompanying diagram shows a replicated recovery environment on virtual machines. After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="b403b-180">Azure 中的 SharePoint 恢复环境</span><span class="sxs-lookup"><span data-stu-id="b403b-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="b403b-181">设计和构建 Azure 中的故障转移环境 </span><span class="sxs-lookup"><span data-stu-id="b403b-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="b403b-182">在 Azure 中创建虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="b403b-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="b403b-p109">通过站点间 VPN 连接，将内部部署网络与 Azure 中的虚拟网络相连接。此连接使用 Azure 中的动态网关。 </span><span class="sxs-lookup"><span data-stu-id="b403b-p109">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection. This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="b403b-p110">将一个或多个域控制器部署到 Azure 虚拟网络，并将其配置为与内部部署域一起使用。这些域控制器是目录服务器。 </span><span class="sxs-lookup"><span data-stu-id="b403b-p110">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain. These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="b403b-187">调整 SharePoint 服务器场使其适用于云服务和可用性集。  </span><span class="sxs-lookup"><span data-stu-id="b403b-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="b403b-188">部署 SharePoint 服务器场加上一台文件服务器以承载文件共享。 </span><span class="sxs-lookup"><span data-stu-id="b403b-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="b403b-189">在本地环境和基于 Azure 的恢复环境之间设置日志传送和 DFSR。 </span><span class="sxs-lookup"><span data-stu-id="b403b-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="b403b-190">随附的图显示了具有下列功能的本地环境和 Azure 虚拟网络： </span><span class="sxs-lookup"><span data-stu-id="b403b-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="b403b-191">内部部署环境</span><span class="sxs-lookup"><span data-stu-id="b403b-191">On-premises environment</span></span>

- <span data-ttu-id="b403b-192">Windows Server 2012 RRAS </span><span class="sxs-lookup"><span data-stu-id="b403b-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="b403b-193">Active Directory 服务器</span><span class="sxs-lookup"><span data-stu-id="b403b-193">Active Directory server</span></span> 
    
<span data-ttu-id="b403b-194">通过虚拟专用网络 (VPN) 网关与 Azure 虚拟网络的本地网络接口。 </span><span class="sxs-lookup"><span data-stu-id="b403b-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="b403b-195">Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="b403b-195">Azure virtual network</span></span>

<span data-ttu-id="b403b-196">与活动 VPN 网关子网的 VPN 网关接口。 </span><span class="sxs-lookup"><span data-stu-id="b403b-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="b403b-197">Azure 虚拟网络中具有三项云服务：</span><span class="sxs-lookup"><span data-stu-id="b403b-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="b403b-198">第一项云服务具有两台具有可用性集的 Active Directory 和 DNS 服务器。 </span><span class="sxs-lookup"><span data-stu-id="b403b-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="b403b-199">第二项云服务有三个服务器组： 两台具有可用性集的分布式缓存服务器。</span><span class="sxs-lookup"><span data-stu-id="b403b-199">The second cloud service has three sets of servers: Two distributed cache servers with an availability set.</span></span> <span data-ttu-id="b403b-200">两台具有可用性集的前端服务器。</span><span class="sxs-lookup"><span data-stu-id="b403b-200">Two front-end servers with an availability set.</span></span> <span data-ttu-id="b403b-201">三台具有可用性集的后端服务器。</span><span class="sxs-lookup"><span data-stu-id="b403b-201">Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="b403b-p112">第三项云服务具有三台具有可用性集的数据库服务器。其中一台数据库服务器是用于日志传送的文件共享以及 SQL Server AlwaysOn 节点多数的第三个节点。 </span><span class="sxs-lookup"><span data-stu-id="b403b-p112">The third cloud service has three database servers with an availability set. One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="b403b-204">构建 AD DS 混合环境</span><span class="sxs-lookup"><span data-stu-id="b403b-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="b403b-205">此解决方案的 AD DS 配置构成混合部署方案，其中 AD DS 一部分部署在本地，一部分部署在 Azure 虚拟机上。 </span><span class="sxs-lookup"><span data-stu-id="b403b-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="b403b-206">重要说明：在 Azure 中部署 AD DS 之前，请阅读在 Microsoft Azure 虚拟机（https://docs.microsoft.com/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100)）上部署 Windows Server Active Directory 的指南。</span><span class="sxs-lookup"><span data-stu-id="b403b-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (https://docs.microsoft.com/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100).</span></span> 
  
 
<span data-ttu-id="b403b-p113">此参考体系结构包括两个配置为域控制器的虚拟机。每个虚拟机配置如下： </span><span class="sxs-lookup"><span data-stu-id="b403b-p113">This reference architecture includes two virtual machines configured as domain controllers. Each is configured as follows:</span></span> 
  
- <span data-ttu-id="b403b-209">大小 — 小。 </span><span class="sxs-lookup"><span data-stu-id="b403b-209">Size — Small.</span></span> 
    
- <span data-ttu-id="b403b-210">操作系统 — Windows Server 2012。  </span><span class="sxs-lookup"><span data-stu-id="b403b-210">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="b403b-p114">角色 — 指定 AD DS 域控制器为全局编录服务器。此配置可以减少通过 VPN 连接的出口通信量。在高变更速率的多域环境中，在内部部署中配置域控制器，使其不与 Azure 中的全局目录服务器同步。  </span><span class="sxs-lookup"><span data-stu-id="b403b-p114">Role — AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the VPN connection. In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="b403b-p115">数据磁盘 — 将 AD DS 数据库、日志和 SYSVOL 放在 Azure 数据磁盘上。不要将它们放在操作系统磁盘或 Azure 提供的临时磁盘上。这一点很关键。</span><span class="sxs-lookup"><span data-stu-id="b403b-p115">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure. This is important.</span></span> 
    
- <span data-ttu-id="b403b-217">角色 — 在域控制器上安装和配置 Windows DNS。</span><span class="sxs-lookup"><span data-stu-id="b403b-217">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="b403b-p116">IP 地址 — 使用动态 IP 地址。这要求您创建一个 Azure 虚拟网络。 </span><span class="sxs-lookup"><span data-stu-id="b403b-p116">IP addresses — Use dynamic IP addresses. This requires you to create an Azure Virtual Network.</span></span> 
    

