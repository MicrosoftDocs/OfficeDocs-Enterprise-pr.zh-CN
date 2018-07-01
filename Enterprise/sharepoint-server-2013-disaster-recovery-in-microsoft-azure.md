---
title: Microsoft Azure 中的 SharePoint Server 2013 灾难恢复
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 摘要：使用 Azure，你可以为内部部署 SharePoint 服务器场创建灾难恢复环境。本文介绍如何设计和实施此解决方案。
ms.openlocfilehash: 553b2e6bb9d35ab3dba471b01938914a95af23d6
ms.sourcegitcommit: 9f57825b10f20e3813732372541128ef187d52c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "20161795"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a><span data-ttu-id="525bb-104">Microsoft Azure 中的 SharePoint Server 2013 灾难恢复</span><span class="sxs-lookup"><span data-stu-id="525bb-104">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>

 <span data-ttu-id="525bb-p102">**摘要：** 使用 Azure，你可以为内部部署 SharePoint 服务器场创建灾难恢复环境。本文介绍如何设计和实施此解决方案。</span><span class="sxs-lookup"><span data-stu-id="525bb-p102">**Summary:** Using Azure, you can create a disaster-recovery environment for your on-premises SharePoint farm. This article describes how to design and implement this solution.</span></span>

 <span data-ttu-id="525bb-107">**观看 SharePoint Server 2013 灾难恢复概述视频**</span><span class="sxs-lookup"><span data-stu-id="525bb-107">**Watch the SharePoint Server 2013 disaster recovery overview video**</span></span>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 <span data-ttu-id="525bb-p103">当灾难袭击你的 SharePoint 内部部署环境时，头等大事是迅速使系统恢复运行。如果你已有备份环境在 Microsoft Azure 中运行，SharePoint 灾难恢复将更加快速、轻松。本视频介绍 SharePoint 温故障转移环境的主要概念，并补充了本文中提供的完整详细信息。</span><span class="sxs-lookup"><span data-stu-id="525bb-p103">When disaster strikes your SharePoint on-premises environment, your top priority is to get the system running again quickly. Disaster recovery with SharePoint is quicker and easier when you have a backup environment already running in Microsoft Azure. This video explains the main concepts of a SharePoint warm failover environment and complements the full details available in this article.</span></span>
  
<span data-ttu-id="525bb-111">将本文与以下解决方案模型结合使用： **Microsoft Azure 中的 SharePoint 灾难恢复** 。</span><span class="sxs-lookup"><span data-stu-id="525bb-111">Use this article with the following solution model: **SharePoint Disaster Recovery in Microsoft Azure**.</span></span>
  
<span data-ttu-id="525bb-112">[![Azure 中的 SharePoint 灾难恢复过程](images/SP_DR_Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)</span><span class="sxs-lookup"><span data-stu-id="525bb-112">[![SharePoint disaster-recovery process to Azure](images/SP_DR_Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)</span></span>
  
 <span data-ttu-id="525bb-113">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)</span><span class="sxs-lookup"><span data-stu-id="525bb-113">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)</span></span>
  
<span data-ttu-id="525bb-114">本文内容：</span><span class="sxs-lookup"><span data-stu-id="525bb-114">In this article:</span></span>
  
- [<span data-ttu-id="525bb-115">使用 Azure 基础结构服务进行灾难恢复</span><span class="sxs-lookup"><span data-stu-id="525bb-115">Use Azure Infrastructure Services for disaster recovery</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#AZ)
    
- [<span data-ttu-id="525bb-116">解决方案描述</span><span class="sxs-lookup"><span data-stu-id="525bb-116">Solution description</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#SOL)
    
- [<span data-ttu-id="525bb-117">详细体系结构</span><span class="sxs-lookup"><span data-stu-id="525bb-117">Detailed architecture</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#arch)
    
- [<span data-ttu-id="525bb-118">灾难恢复路线图</span><span class="sxs-lookup"><span data-stu-id="525bb-118">Disaster recovery roadmap</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#RDmap)
    
- [<span data-ttu-id="525bb-119">阶段 1：设计灾难恢复环境</span><span class="sxs-lookup"><span data-stu-id="525bb-119">Phase 1: Design the disaster recovery environment</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase1)
    
- [<span data-ttu-id="525bb-120">阶段 2：创建 Azure 虚拟网络和 VPN 连接</span><span class="sxs-lookup"><span data-stu-id="525bb-120">Phase 2: Create the Azure virtual network and VPN connection</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase2)
    
- [<span data-ttu-id="525bb-121">阶段 3：将 Active Directory 和域名服务部署到 Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="525bb-121">Phase 3: Deploy Active Directory and Domain Name Services to the Azure virtual network</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase3)
    
- [<span data-ttu-id="525bb-122">阶段 4：在 Azure 中部署 SharePoint 恢复场</span><span class="sxs-lookup"><span data-stu-id="525bb-122">Phase 4: Deploy the SharePoint recovery farm in Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase4)
    
- [<span data-ttu-id="525bb-123">阶段 5：设置场之间的 DFSR</span><span class="sxs-lookup"><span data-stu-id="525bb-123">Phase 5: Set up DFSR between the farms</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase5)
    
- [<span data-ttu-id="525bb-124">阶段 6：设置到恢复场的日志传送</span><span class="sxs-lookup"><span data-stu-id="525bb-124">Phase 6: Set up log shipping to the recovery farm</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase6)
    
- [<span data-ttu-id="525bb-125">阶段 7：验证故障转移和恢复</span><span class="sxs-lookup"><span data-stu-id="525bb-125">Phase 7: Validate failover and recovery</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase7)
    
- [<span data-ttu-id="525bb-126">Microsoft 概念证明环境</span><span class="sxs-lookup"><span data-stu-id="525bb-126">Microsoft proof-of-concept environment</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#POC)
    
- [<span data-ttu-id="525bb-127">疑难解答提示</span><span class="sxs-lookup"><span data-stu-id="525bb-127">Troubleshooting tips</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Troubleshooting)
    
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a><span data-ttu-id="525bb-128">使用 Azure 基础结构服务进行灾难恢复</span><span class="sxs-lookup"><span data-stu-id="525bb-128">Use Azure Infrastructure Services for disaster recovery</span></span>
<span data-ttu-id="525bb-129"><a name="AZ"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-129"><a name="AZ"> </a></span></span>

<span data-ttu-id="525bb-p104">很多组织没有 SharePoint 的灾难恢复环境，因为在内部构建和维护此环境非常昂贵。Azure 基础结构服务提供了灾难恢复环境极具吸引力的选项，这些选项更加灵活且成本比内部部署方案要低。</span><span class="sxs-lookup"><span data-stu-id="525bb-p104">Many organizations do not have a disaster recovery environment for SharePoint, which can be expensive to build and maintain on-premises. Azure Infrastructure Services provides compelling options for disaster recovery environments that are more flexible and less expensive than the on-premises alternatives.</span></span>
  
<span data-ttu-id="525bb-132">使用 Azure 基础结构服务的优点如下：</span><span class="sxs-lookup"><span data-stu-id="525bb-132">The advantages for using Azure Infrastructure Services include:</span></span>
  
- <span data-ttu-id="525bb-p105">**资源成本更低** 维护和支付比内部部署灾难恢复环境更少的资源。资源数量取决于你选择的灾难恢复环境：冷备用、温备用或热备用。</span><span class="sxs-lookup"><span data-stu-id="525bb-p105">**Fewer costly resources** Maintain and pay for fewer resources than on-premises disaster recovery environments. The number of resources depends on which disaster-recovery environment you choose: cold standby, warm standby, or hot standby.</span></span>
    
- <span data-ttu-id="525bb-p106">**资源灵活性更高** 如果发生灾难，轻松扩展恢复 SharePoint 服务器场以满足负载要求。当你不再需要这些资源时，进行缩放。</span><span class="sxs-lookup"><span data-stu-id="525bb-p106">**Better resource flexibility** In the event of a disaster, easily scale out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources.</span></span>
    
- <span data-ttu-id="525bb-137">**数据中心承诺更低** 使用 Azure 基础结构服务，而不是在其他地区投资建设辅助数据中心。</span><span class="sxs-lookup"><span data-stu-id="525bb-137">**Lower datacenter commitment** Use Azure Infrastructure Services instead of investing in a secondary datacenter in a different region.</span></span>
    
<span data-ttu-id="525bb-p107">对于刚刚开始接触灾难恢复的组织，提供不太复杂的选项；对于具有高弹性要求的组织，则提供一些高级选项。当环境承载在云平台上时，冷备用、温备用和热备用环境的定义略有不同。下表介绍了在 Azure 中构建 SharePoint 恢复场的环境。</span><span class="sxs-lookup"><span data-stu-id="525bb-p107">There are less-complex options for organizations just getting started with disaster recovery and advanced options for organizations with high-resilience requirements. The definitions for cold, warm, and hot standby environments are a little different when the environment is hosted on a cloud platform. The following table describes these environments for building a SharePoint recovery farm in Azure.</span></span>
  
<span data-ttu-id="525bb-141">**表：恢复环境**</span><span class="sxs-lookup"><span data-stu-id="525bb-141">**Table: Recovery environments**</span></span>

|<span data-ttu-id="525bb-142">**恢复环境的类型**</span><span class="sxs-lookup"><span data-stu-id="525bb-142">**Type of recovery environment**</span></span>|<span data-ttu-id="525bb-143">**说明**</span><span class="sxs-lookup"><span data-stu-id="525bb-143">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="525bb-144">热备用</span><span class="sxs-lookup"><span data-stu-id="525bb-144">Hot</span></span>  <br/> |<span data-ttu-id="525bb-145">设置并更新一个完全大小的服务器场，且以备用状态运行。</span><span class="sxs-lookup"><span data-stu-id="525bb-145">A fully sized farm is provisioned, updated, and running on standby.</span></span>  <br/> |
|<span data-ttu-id="525bb-146">温备用</span><span class="sxs-lookup"><span data-stu-id="525bb-146">Warm</span></span>  <br/> |<span data-ttu-id="525bb-147">已构建服务器场，虚拟机正在运行并且已更新。</span><span class="sxs-lookup"><span data-stu-id="525bb-147">The farm is built and virtual machines are running and updated.</span></span>  <br/> <span data-ttu-id="525bb-148">恢复包括附加内容数据库、设置服务应用程序和爬网内容。</span><span class="sxs-lookup"><span data-stu-id="525bb-148">Recovery includes attaching content databases, provisioning service applications, and crawling content.</span></span>  <br/> <span data-ttu-id="525bb-149">服务器场可以是生产服务器场的较小版本，它可以向外扩展以便为整个用户群提供服务。</span><span class="sxs-lookup"><span data-stu-id="525bb-149">The farm can be a smaller version of the production farm and then scaled out to serve the full user base.</span></span>  <br/> |
|<span data-ttu-id="525bb-150">冷备用</span><span class="sxs-lookup"><span data-stu-id="525bb-150">Cold</span></span>  <br/> |<span data-ttu-id="525bb-151">服务器场已完全构建，但虚拟机已停止。</span><span class="sxs-lookup"><span data-stu-id="525bb-151">The farm is fully built, but the virtual machines are stopped.</span></span>  <br/> <span data-ttu-id="525bb-152">维护环境包括偶尔启动虚拟机，以及修补、更新和验证环境。</span><span class="sxs-lookup"><span data-stu-id="525bb-152">Maintaining the environment includes starting the virtual machines from time to time, patching, updating, and verifying the environment.</span></span>  <br/> <span data-ttu-id="525bb-153">启动完整环境发生灾难时。</span><span class="sxs-lookup"><span data-stu-id="525bb-153">Start the full environment in the event of a disaster.</span></span>  <br/> |
   
<span data-ttu-id="525bb-p108">请务必评估你的组织的恢复时间目标 (RTO) 和恢复点目标 (RPO)。这些要求确定了哪个环境是最适合贵组织的投资。</span><span class="sxs-lookup"><span data-stu-id="525bb-p108">It's important to evaluate your organization's Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs). These requirements determine which environment is the most appropriate investment for your organization.</span></span>
  
<span data-ttu-id="525bb-p109">本文中的指南介绍如何实现温备用环境。你也可以对其进行调整使其适合冷备用环境，尽管你需要执行一些其他步骤才能支持此类环境。本文不会介绍如何实现热备用环境。</span><span class="sxs-lookup"><span data-stu-id="525bb-p109">The guidance in this article describes how to implement a warm standby environment. You can also adapt it to a cold standby environment, although you need to follow additional procedures to support this kind of environment. This article does not describe how to implement a hot standby environment.</span></span>
  
<span data-ttu-id="525bb-159">有关灾难恢复解决方案的详细信息，请参阅 [High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114)和[Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228)。</span><span class="sxs-lookup"><span data-stu-id="525bb-159">For more information about disaster recovery solutions, see [High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) and [Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228).</span></span>
  
## <a name="solution-description"></a><span data-ttu-id="525bb-160">解决方案描述</span><span class="sxs-lookup"><span data-stu-id="525bb-160">Solution description</span></span>
<span data-ttu-id="525bb-161"><a name="SOL"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-161"><a name="SOL"> </a></span></span>

<span data-ttu-id="525bb-162">温备用灾难恢复解决方案需要以下环境：</span><span class="sxs-lookup"><span data-stu-id="525bb-162">The warm standby disaster-recovery solution requires the following environment:</span></span>
  
- <span data-ttu-id="525bb-163">内部部署 SharePoint 生产服务器场</span><span class="sxs-lookup"><span data-stu-id="525bb-163">An on-premises SharePoint production farm</span></span>
    
- <span data-ttu-id="525bb-164">Azure 中的恢复 SharePoint 服务器场</span><span class="sxs-lookup"><span data-stu-id="525bb-164">A recovery SharePoint farm in Azure</span></span>
    
- <span data-ttu-id="525bb-165">两个环境之间的站点到站点 VPN 连接</span><span class="sxs-lookup"><span data-stu-id="525bb-165">A site-to-site VPN connection between the two environments</span></span>
    
<span data-ttu-id="525bb-166">下图说明了这三个元素。</span><span class="sxs-lookup"><span data-stu-id="525bb-166">The following figure illustrates these three elements.</span></span>
  
<span data-ttu-id="525bb-167">**图：Azure 中温备用解决方案的元素**</span><span class="sxs-lookup"><span data-stu-id="525bb-167">**Figure: Elements of a warm standby solution in Azure**</span></span>

![Azure 中 SharePoint 温备用状态解决方案的元素](images/AZarch_AZWarmStndby.png)
  
<span data-ttu-id="525bb-169">SQL Server 日志传送与分布式文件系统复制 (DFSR) 用于将数据库备份和事务日志复制到 Azure 中的恢复场：</span><span class="sxs-lookup"><span data-stu-id="525bb-169">SQL Server log shipping with Distributed File System Replication (DFSR) is used to copy database backups and transaction logs to the recovery farm in Azure:</span></span> 
  
- <span data-ttu-id="525bb-p110">DFSR 将日志从生产环境传输到恢复环境。在 WAN 方案中，DFSR 比将日志直接传输到 Azure 中的辅助服务器更有效。</span><span class="sxs-lookup"><span data-stu-id="525bb-p110">DFSR transfers logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span>
    
- <span data-ttu-id="525bb-172">日志将重播到 Azure 恢复环境中的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="525bb-172">Logs are replayed to the SQL Server in the recovery environment in Azure.</span></span>
    
- <span data-ttu-id="525bb-173">你不会在恢复环境中附加日志传送的 SharePoint 内容数据库，除非执行恢复操作。</span><span class="sxs-lookup"><span data-stu-id="525bb-173">You don't attach log-shipped SharePoint content databases in the recovery environment until a recovery exercise is performed.</span></span>
    
<span data-ttu-id="525bb-174">执行下列步骤，恢复服务器场：</span><span class="sxs-lookup"><span data-stu-id="525bb-174">Perform the following steps to recover the farm:</span></span>
  
1. <span data-ttu-id="525bb-175">停止日志传送。</span><span class="sxs-lookup"><span data-stu-id="525bb-175">Stop log shipping.</span></span>
    
2. <span data-ttu-id="525bb-176">停止接受到主服务器场通信。</span><span class="sxs-lookup"><span data-stu-id="525bb-176">Stop accepting traffic to the primary farm.</span></span>
    
3. <span data-ttu-id="525bb-177">重播最后的事务日志。</span><span class="sxs-lookup"><span data-stu-id="525bb-177">Replay the final transaction logs.</span></span>
    
4. <span data-ttu-id="525bb-178">将内容数据库附加到服务器场。</span><span class="sxs-lookup"><span data-stu-id="525bb-178">Attach the content databases to the farm.</span></span>
    
5. <span data-ttu-id="525bb-179">从复制的服务数据库中还原服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="525bb-179">Restore service applications from the replicated services databases.</span></span>
    
6. <span data-ttu-id="525bb-180">将域名系统 (DNS) 记录更新为指向恢复场。</span><span class="sxs-lookup"><span data-stu-id="525bb-180">Update Domain Name System (DNS) records to point to the recovery farm.</span></span>
    
7. <span data-ttu-id="525bb-181">启动完全爬网。</span><span class="sxs-lookup"><span data-stu-id="525bb-181">Start a full crawl.</span></span>
    
<span data-ttu-id="525bb-p111">我们建议你定期演练这些步骤并进行记录，以确保在线恢复顺利运行。附加内容数据库和恢复服务应用程序可能需要一些时间，并且通常涉及一些手动配置。</span><span class="sxs-lookup"><span data-stu-id="525bb-p111">We recommend that you rehearse these steps regularly and document them to help ensure that your live recovery runs smoothly. Attaching content databases and restoring service applications can take some time and typically involves some manual configuration.</span></span>
  
<span data-ttu-id="525bb-184">执行恢复后，此解决方案将提供下表中列出的项目。</span><span class="sxs-lookup"><span data-stu-id="525bb-184">After a recovery is performed, this solution provides the items listed in the following table.</span></span>
  
<span data-ttu-id="525bb-185">**表：解决方案恢复目标**</span><span class="sxs-lookup"><span data-stu-id="525bb-185">**Table: Solution recovery objectives**</span></span>

|<span data-ttu-id="525bb-186">**项**</span><span class="sxs-lookup"><span data-stu-id="525bb-186">**Item**</span></span>|<span data-ttu-id="525bb-187">**说明**</span><span class="sxs-lookup"><span data-stu-id="525bb-187">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="525bb-188">网站和内容</span><span class="sxs-lookup"><span data-stu-id="525bb-188">Sites and content</span></span>  <br/> |<span data-ttu-id="525bb-189">网站和内容在恢复环境中可用。</span><span class="sxs-lookup"><span data-stu-id="525bb-189">Sites and content are available in the recovery environment.</span></span>  <br/> |
|<span data-ttu-id="525bb-190">新的搜索实例</span><span class="sxs-lookup"><span data-stu-id="525bb-190">A new instance of search</span></span>  <br/> |<span data-ttu-id="525bb-p112">在此温备用解决方案中，不会从搜索数据库还原搜索。恢复场中的搜索组件尽可能配置得与生产服务器场类似。网站和内容还原后，会启动完全爬网以重建搜索索引。你不需要等待爬网完成，即可使网站和内容可用。</span><span class="sxs-lookup"><span data-stu-id="525bb-p112">In this warm standby solution, search is not restored from search databases. Search components in the recovery farm are configured as similarly as possible to the production farm. After the sites and content are restored, a full crawl is started to rebuild the search index. You do not need to wait for the crawl to complete to make the sites and content available.</span></span>  <br/> |
|<span data-ttu-id="525bb-195">服务</span><span class="sxs-lookup"><span data-stu-id="525bb-195">Services</span></span>  <br/> | <span data-ttu-id="525bb-p113">将数据存储在数据库中的服务从日志传送的数据库还原。不在数据库中存储数据的服务则直接启动。</span><span class="sxs-lookup"><span data-stu-id="525bb-p113">Services that store data in databases are restored from the log-shipped databases. Services that do not store data in databases are simply started.</span></span> <br/>  <span data-ttu-id="525bb-p114">并非数据库的所有服务都需要还原。下列服务不需要从数据库还原，在故障转移后可以直接启动：</span><span class="sxs-lookup"><span data-stu-id="525bb-p114">Not all services with databases need to be restored. The following services do not need to be restored from databases and can simply be started after failover:</span></span> <br/>  <span data-ttu-id="525bb-200">Usage and Health Data Collection</span><span class="sxs-lookup"><span data-stu-id="525bb-200">Usage and Health Data Collection</span></span> <br/>  <span data-ttu-id="525bb-201">State service</span><span class="sxs-lookup"><span data-stu-id="525bb-201">State service</span></span> <br/>  <span data-ttu-id="525bb-202">Word Automation</span><span class="sxs-lookup"><span data-stu-id="525bb-202">Word automation</span></span> <br/>  <span data-ttu-id="525bb-203">任何其他不使用数据库的服务</span><span class="sxs-lookup"><span data-stu-id="525bb-203">Any other service that doesn't use a database</span></span> <br/> |
   
<span data-ttu-id="525bb-p115">你可以与 Microsoft 咨询服务 (MCS) 或合作伙伴合作以实现更复杂的恢复目标。下表中汇总了详细信息。</span><span class="sxs-lookup"><span data-stu-id="525bb-p115">You can work with Microsoft Consulting Services (MCS) or a partner to address more-complex recovery objectives. These are summarized in the following table.</span></span>
  
<span data-ttu-id="525bb-206">**表：可以由 MCS 或合作伙伴解决的其他项目**</span><span class="sxs-lookup"><span data-stu-id="525bb-206">**Table: Other items that can be addressed by MCS or a partner**</span></span>

|<span data-ttu-id="525bb-207">**项**</span><span class="sxs-lookup"><span data-stu-id="525bb-207">**Item**</span></span>|<span data-ttu-id="525bb-208">**说明**</span><span class="sxs-lookup"><span data-stu-id="525bb-208">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="525bb-209">正在同步的自定义场解决方案</span><span class="sxs-lookup"><span data-stu-id="525bb-209">Synchronizing custom farm solutions</span></span>  <br/> |<span data-ttu-id="525bb-p116">理想情况下，恢复场的配置与生产服务器场相同。你可以与顾问或合作伙伴合作，评估是否复制了自定义服务器场解决方案，以及是否制定了将两个环境保持同步的流程。</span><span class="sxs-lookup"><span data-stu-id="525bb-p116">Ideally, the recovery farm configuration is identical to the production farm. You can work with a consultant or partner to evaluate whether custom farm solutions are replicated and whether the process is in place for keeping the two environments synchronized.</span></span>  <br/> |
|<span data-ttu-id="525bb-212">到内部部署数据源的连接</span><span class="sxs-lookup"><span data-stu-id="525bb-212">Connections to data sources on-premises</span></span>  <br/> |<span data-ttu-id="525bb-213">将连接复制到后端数据系统可能并不实用，例如备份域控制器 (BDC) 连接和搜索内容源。</span><span class="sxs-lookup"><span data-stu-id="525bb-213">It might not be practical to replicate connections to back-end data systems, such as backup domain controller (BDC) connections and search content sources.</span></span>  <br/> |
|<span data-ttu-id="525bb-214">搜索还原方案</span><span class="sxs-lookup"><span data-stu-id="525bb-214">Search restore scenarios</span></span>  <br/> |<span data-ttu-id="525bb-p117">由于企业搜索部署通常非常独特且复杂，从数据库还原搜索需要更大的投资。你可以与顾问或合作伙伴合作，以确定并实施贵组织可能需要的搜索还原方案。</span><span class="sxs-lookup"><span data-stu-id="525bb-p117">Because enterprise search deployments tend to be fairly unique and complex, restoring search from databases requires a greater investment. You can work with a consultant or partner to identify and implement search restore scenarios that your organization might require.</span></span>  <br/> |
   
<span data-ttu-id="525bb-217">本文中提供的指南假定已设计和部署内部部署服务器场。</span><span class="sxs-lookup"><span data-stu-id="525bb-217">The guidance provided in this article assumes that the on-premises farm is already designed and deployed.</span></span>
  
## <a name="detailed-architecture"></a><span data-ttu-id="525bb-218">详细体系结构</span><span class="sxs-lookup"><span data-stu-id="525bb-218">Detailed architecture</span></span>
<span data-ttu-id="525bb-219"><a name="arch"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-219"><a name="arch"> </a></span></span>

<span data-ttu-id="525bb-220">理想情况下，Azure 中的恢复服务器场配置与内部部署服务器场相同，其中包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="525bb-220">Ideally, the recovery farm configuration in Azure is identical to the production farm on-premises, including the following:</span></span>
  
- <span data-ttu-id="525bb-221">服务器角色的表示形式相同</span><span class="sxs-lookup"><span data-stu-id="525bb-221">The same representation of server roles</span></span>
    
- <span data-ttu-id="525bb-222">自定义配置相同</span><span class="sxs-lookup"><span data-stu-id="525bb-222">The same configuration of customizations</span></span>
    
- <span data-ttu-id="525bb-223">搜索组件的配置相同</span><span class="sxs-lookup"><span data-stu-id="525bb-223">The same configuration of search components</span></span>
    
<span data-ttu-id="525bb-p118">Azure 中的环境可以是生产服务器场的较小版本。如果你计划在故障转移后向外扩展恢复场，必须对每种类型的服务器进行初始表示。</span><span class="sxs-lookup"><span data-stu-id="525bb-p118">The environment in Azure can be a smaller version of the production farm. If you plan to scale out the recovery farm after failover, it's important that each type of server role be initially represented.</span></span>
  
<span data-ttu-id="525bb-p119">某些配置可能无法在故障转移环境中复制。请务必测试故障转移过程和环境，确保故障转移服务器场提供预期的服务级别。</span><span class="sxs-lookup"><span data-stu-id="525bb-p119">Some configurations might not be practical to replicate in the failover environment. Be sure to test the failover procedures and environment to help ensure that the failover farm provides the expected service level.</span></span>
  
<span data-ttu-id="525bb-p120">此解决方案不会规定 SharePoint 服务器场的特定拓扑。此解决方案的焦点是将 Azure 用于故障转移服务器场，并在两个环境之间实施日志传送和 DFSR。</span><span class="sxs-lookup"><span data-stu-id="525bb-p120">This solution doesn't prescribe a specific topology for a SharePoint farm. The focus of this solution is to use Azure for the failover farm and to implement log shipping and DFSR between the two environments.</span></span>
  
### <a name="warm-standby-environments"></a><span data-ttu-id="525bb-230">温备用环境</span><span class="sxs-lookup"><span data-stu-id="525bb-230">Warm standby environments</span></span>

<span data-ttu-id="525bb-p121">在温备用环境中，Azure 环境中的所有虚拟机均正常运行。环境已准备就绪，可用于故障转移练习或事件。</span><span class="sxs-lookup"><span data-stu-id="525bb-p121">In a warm standby environment, all virtual machines in the Azure environment are running. The environment is ready for a failover exercise or event.</span></span>
  
<span data-ttu-id="525bb-233">下图说明了从内部部署 SharePoint 服务器场到基于 Azure 的 SharePoint 服务器场（配置为温备用环境）的灾难恢复解决方案。</span><span class="sxs-lookup"><span data-stu-id="525bb-233">The following figure illustrates a disaster recovery solution from an on-premises SharePoint farm to an Azure-based SharePoint farm that is configured as a warm standby environment.</span></span>
  
<span data-ttu-id="525bb-234">**图：生产场和温备用状态恢复场的拓扑和主要元素**</span><span class="sxs-lookup"><span data-stu-id="525bb-234">**Figure: Topology and key elements of a production farm and a warm standby recovery farm**</span></span>

![SharePoint 服务器场和温备用状态恢复场的拓扑](images/AZarch_AZWarmStndby.png)
  
<span data-ttu-id="525bb-236">在此图中：</span><span class="sxs-lookup"><span data-stu-id="525bb-236">In this diagram:</span></span>
  
- <span data-ttu-id="525bb-237">两个环境并排显示：内部部署 SharePoint 服务器场和 Azure 中的温备用服务器场。</span><span class="sxs-lookup"><span data-stu-id="525bb-237">Two environments are illustrated side by side: the on-premises SharePoint farm and the warm standby farm in Azure.</span></span>
    
- <span data-ttu-id="525bb-238">每个环境包含一个文件共享。</span><span class="sxs-lookup"><span data-stu-id="525bb-238">Each environment includes a file share.</span></span>
    
- <span data-ttu-id="525bb-p122">每个服务器场包含四层。为实现高可用性，每一层包含两台服务器或为特定角色配置得相同的虚拟机，如前端服务、分布式缓存、后端服务和数据库。在此图中，调用特定的组件并不重要。两个服务器场的配置相同。</span><span class="sxs-lookup"><span data-stu-id="525bb-p122">Each farm includes four tiers. To achieve high availability, each tier includes two servers or virtual machines that are configured identically for a specific role, such as front-end services, distributed cache, back-end services, and databases. It isn't important in this illustration to call out specific components. The two farms are configured identically.</span></span>
    
- <span data-ttu-id="525bb-p123">第四层是数据库层。日志传送用于将日志从本地环境中的辅助数据库服务器复制到同一环境中的文件共享。</span><span class="sxs-lookup"><span data-stu-id="525bb-p123">The fourth tier is the database tier. Log shipping is used to copy logs from the secondary database server in the on-premises environment to the file share in the same environment.</span></span>
    
- <span data-ttu-id="525bb-245">DFSR 将本地环境中的文件共享复制到 Azure 环境中的文件共享</span><span class="sxs-lookup"><span data-stu-id="525bb-245">DFSR copies files from the file share in the on-premises environment to the file share in the Azure environment.</span></span>
    
- <span data-ttu-id="525bb-246">日志传送将日志从 Azure 环境中的文件共享中继到恢复环境中 SQL Server AlwaysOn 可用性组的主副本。</span><span class="sxs-lookup"><span data-stu-id="525bb-246">Log shipping replays the logs from the file share in the Azure environment to the primary replica in the SQL Server AlwaysOn availability group in the recovery environment.</span></span>
    
### <a name="cold-standby-environments"></a><span data-ttu-id="525bb-247">冷备用环境</span><span class="sxs-lookup"><span data-stu-id="525bb-247">Cold standby environments</span></span>

<span data-ttu-id="525bb-p124">在冷备用环境中，大部分 SharePoint 服务器场虚拟机都可以关闭。（建议有时启动虚拟机，例如每两周或一次或一个月一次，以便每个虚拟机可与域同步。）Azure 恢复环境中的下列虚拟机必须保持运行状态，以确保日志传送和 DFSR 持续运行：</span><span class="sxs-lookup"><span data-stu-id="525bb-p124">In a cold standby environment, most of the SharePoint farm virtual machines can be shut down. (We recommend occasionally starting the virtual machines, such as every two weeks or once a month, so that each virtual machine can sync with the domain.) The following virtual machines in the Azure recovery environment must remain running to help ensure continuous operations of log shipping and DFSR:</span></span>
  
- <span data-ttu-id="525bb-250">文件共享</span><span class="sxs-lookup"><span data-stu-id="525bb-250">The file share</span></span>
    
- <span data-ttu-id="525bb-251">主数据库服务器</span><span class="sxs-lookup"><span data-stu-id="525bb-251">The primary database server</span></span>
    
- <span data-ttu-id="525bb-252">至少一个运行 Windows Server Active Directory 域服务和 DNS 的虚拟机</span><span class="sxs-lookup"><span data-stu-id="525bb-252">At least one virtual machine running Windows Server Active Directory Domain Services and DNS</span></span>
    
<span data-ttu-id="525bb-p125">下图显示了文件共享虚拟机和主 SharePoint 数据库虚拟机正在运行的 Azure 故障转移环境。所有其他 SharePoint 虚拟机都已停止。运行 Windows Server Active Directory 和 DNS 的虚拟机不会显示。</span><span class="sxs-lookup"><span data-stu-id="525bb-p125">The following figure shows an Azure failover environment in which the file share virtual machine and the primary SharePoint database virtual machine are running. All other SharePoint virtual machines are stopped. The virtual machine that is running Windows Server Active Directory and DNS is not shown.</span></span>
  
<span data-ttu-id="525bb-256">**图：包含运行的虚拟机的冷备用恢复场**</span><span class="sxs-lookup"><span data-stu-id="525bb-256">**Figure: Cold standby recovery farm with running virtual machines**</span></span>

![Azure 中 SharePoint 冷备用状态解决方案的元素](images/AZarch_AZColdStndby.png)
  
<span data-ttu-id="525bb-258">故障转移到冷备用环境之后，所有虚拟机都将启动，必须配置实现数据库服务器高可用性的方法，例如 SQL Server AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="525bb-258">After failover to a cold standby environment, all virtual machines are started, and the method to achieve high availability of the database servers must be configured, such as SQL Server AlwaysOn availability groups.</span></span>
  
<span data-ttu-id="525bb-259">如果实施了多个存储组（数据库分布在多个 SQL Server 高可用性集之间），则每个存储组的主数据库都必须处于运行状态以接受与其存储组关联的日志。</span><span class="sxs-lookup"><span data-stu-id="525bb-259">If multiple storage groups are implemented (databases are spread across more than one SQL Server high availability set), the primary database for each storage group must be running to accept the logs associated with its storage group.</span></span>
  
### <a name="skills-and-experience"></a><span data-ttu-id="525bb-260">技能和经验</span><span class="sxs-lookup"><span data-stu-id="525bb-260">Skills and experience</span></span>

<span data-ttu-id="525bb-p126">此灾难恢复解决方案中使用了多种技术。要确保这些技术按预期交互，内部部署和 Azure 环境中的每个组件都必须正确安装和配置。我们建议设置此解决方案的用户或团队具有下列文章中所述技术的丰富工作知识和动手技能：</span><span class="sxs-lookup"><span data-stu-id="525bb-p126">Multiple technologies are used in this disaster recovery solution. To help ensure that these technologies interact as expected, each component in the on-premises and Azure environment must be installed and configured correctly. We recommend that the person or team who sets up this solution have a strong working knowledge of and hands-on skills with the technologies described in the following articles:</span></span>
  
- [<span data-ttu-id="525bb-264">分布式文件系统 (DFS) 复制服务</span><span class="sxs-lookup"><span data-stu-id="525bb-264">Distributed File System (DFS) Replication Services</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [<span data-ttu-id="525bb-265">Windows Server 故障转移群集 (WSFC) 与 SQL Server</span><span class="sxs-lookup"><span data-stu-id="525bb-265">Windows Server Failover Clustering (WSFC) with SQL Server</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [<span data-ttu-id="525bb-266">AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="525bb-266">AlwaysOn Availability Groups (SQL Server)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [<span data-ttu-id="525bb-267">SQL Server 数据库的备份和还原</span><span class="sxs-lookup"><span data-stu-id="525bb-267">Back Up and Restore of SQL Server Databases</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [<span data-ttu-id="525bb-268">SharePoint Server 2013 安装和服务器场部署</span><span class="sxs-lookup"><span data-stu-id="525bb-268">SharePoint Server 2013 installation and farm deployment</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [<span data-ttu-id="525bb-269">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="525bb-269">Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
<span data-ttu-id="525bb-p127">最后，我们建议使用脚本编程技能，你可以用于将与这些技术相关的任务自动化。可以使用可用的用户界面完成此解决方案中所述的所有任务。但是，手动方法可能非常耗时且容易出现错误，并会交付不一致的结果。</span><span class="sxs-lookup"><span data-stu-id="525bb-p127">Finally, we recommend scripting skills that you can use to automate tasks associated with these technologies. It's possible to use the available user interfaces to complete all the tasks described in this solution. However, a manual approach can be time consuming and error prone and delivers inconsistent results.</span></span>
  
<span data-ttu-id="525bb-p128">除了 Windows PowerShell 之外，还有用于 SQL Server、SharePoint Server 和 Azure 的 Windows PowerShell 库。不要忘记 T-SQL，它还可以帮助减少配置和维护灾难恢复环境所需的时间。</span><span class="sxs-lookup"><span data-stu-id="525bb-p128">In addition to Windows PowerShell, there are also Windows PowerShell libraries for SQL Server, SharePoint Server, and Azure. Don't forget T-SQL, which can also help reduce the time to configure and maintain your disaster-recovery environment.</span></span>
  
## <a name="disaster-recovery-roadmap"></a><span data-ttu-id="525bb-275">灾难恢复路线图</span><span class="sxs-lookup"><span data-stu-id="525bb-275">Disaster recovery roadmap</span></span>
<span data-ttu-id="525bb-276"><a name="RDmap"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-276"><a name="RDmap"> </a></span></span>

![SharePoint 灾难恢复路线图的可视化表示。](images/Azure_DRroadmap.png)
  
<span data-ttu-id="525bb-278">此路线图假定你已经在生产中部署了 SharePoint Server 2013 服务器场。</span><span class="sxs-lookup"><span data-stu-id="525bb-278">This roadmap assumes that you already have a SharePoint Server 2013 farm deployed in production.</span></span>
  
<span data-ttu-id="525bb-279">**表：灾难恢复路线图**</span><span class="sxs-lookup"><span data-stu-id="525bb-279">**Table: Roadmap for disaster recovery**</span></span>

|<span data-ttu-id="525bb-280">**阶段**</span><span class="sxs-lookup"><span data-stu-id="525bb-280">**Phase**</span></span>|<span data-ttu-id="525bb-281">**说明**</span><span class="sxs-lookup"><span data-stu-id="525bb-281">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="525bb-282">阶段 1</span><span class="sxs-lookup"><span data-stu-id="525bb-282">Phase 1</span></span>  <br/> |<span data-ttu-id="525bb-283">设计灾难恢复环境。</span><span class="sxs-lookup"><span data-stu-id="525bb-283">Design the disaster recovery environment.</span></span>  <br/> |
|<span data-ttu-id="525bb-284">阶段 2</span><span class="sxs-lookup"><span data-stu-id="525bb-284">Phase 2</span></span>  <br/> |<span data-ttu-id="525bb-285">创建 Azure 虚拟网络和 VPN 连接。</span><span class="sxs-lookup"><span data-stu-id="525bb-285">Create the Azure virtual network and VPN connection.</span></span>  <br/> |
|<span data-ttu-id="525bb-286">阶段 3</span><span class="sxs-lookup"><span data-stu-id="525bb-286">Phase 3</span></span>  <br/> |<span data-ttu-id="525bb-287">将 Windows Active Directory 和域名服务部署到 Azure 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="525bb-287">Deploy Windows Active Directory and Domain Name Services to the Azure virtual network.</span></span>  <br/> |
|<span data-ttu-id="525bb-288">阶段 4</span><span class="sxs-lookup"><span data-stu-id="525bb-288">Phase 4</span></span>  <br/> |<span data-ttu-id="525bb-289">将 SharePoint 恢复场部署到 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="525bb-289">Deploy the SharePoint recovery farm in Azure.</span></span>  <br/> |
|<span data-ttu-id="525bb-290">阶段 5</span><span class="sxs-lookup"><span data-stu-id="525bb-290">Phase 5</span></span>  <br/> |<span data-ttu-id="525bb-291">设置场之间的 DFSR。</span><span class="sxs-lookup"><span data-stu-id="525bb-291">Set up DFSR between the farms.</span></span>  <br/> |
|<span data-ttu-id="525bb-292">阶段 6</span><span class="sxs-lookup"><span data-stu-id="525bb-292">Phase 6</span></span>  <br/> |<span data-ttu-id="525bb-293">设置到恢复场的日志传送。</span><span class="sxs-lookup"><span data-stu-id="525bb-293">Set up log shipping to the recovery farm.</span></span>  <br/> |
|<span data-ttu-id="525bb-294">阶段 7</span><span class="sxs-lookup"><span data-stu-id="525bb-294">Phase 7</span></span>  <br/> | <span data-ttu-id="525bb-p129">验证故障转移和恢复解决方案，其中包括以下过程和技术：</span><span class="sxs-lookup"><span data-stu-id="525bb-p129">Validate failover and recovery solutions. This includes the following procedures and technologies:</span></span> <br/>  <span data-ttu-id="525bb-297">停止日志传送。</span><span class="sxs-lookup"><span data-stu-id="525bb-297">Stop log shipping.</span></span> <br/>  <span data-ttu-id="525bb-298">将备份还原。</span><span class="sxs-lookup"><span data-stu-id="525bb-298">Restore the backups.</span></span> <br/>  <span data-ttu-id="525bb-299">对内容爬网。</span><span class="sxs-lookup"><span data-stu-id="525bb-299">Crawl content.</span></span> <br/>  <span data-ttu-id="525bb-300">恢复服务。</span><span class="sxs-lookup"><span data-stu-id="525bb-300">Recover services.</span></span> <br/>  <span data-ttu-id="525bb-301">管理 DNS 记录。</span><span class="sxs-lookup"><span data-stu-id="525bb-301">Manage DNS records.</span></span> <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a><span data-ttu-id="525bb-302">阶段 1：设计灾难恢复环境</span><span class="sxs-lookup"><span data-stu-id="525bb-302">Phase 1: Design the disaster recovery environment</span></span>
<span data-ttu-id="525bb-303"><a name="Phase1"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-303"><a name="Phase1"> </a></span></span>

<span data-ttu-id="525bb-p130">使用 [SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md)中的指导设计灾难恢复环境，包括 SharePoint 恢复场。你可以按照 [Azure 中的 SharePoint 灾难恢复解决方案](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio 文件中的图开始设计过程。我们建议你先设计整个环境，然后开始在 Azure 环境中执行任何工作。</span><span class="sxs-lookup"><span data-stu-id="525bb-p130">Use the guidance in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) to design the disaster-recovery environment, including the SharePoint recovery farm. You can use the graphics in the[SharePoint Disaster Recovery Solution in Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio file to start the design process. We recommend that you design the entire environment before beginning any work in the Azure environment.</span></span>
  
<span data-ttu-id="525bb-307">除了 [SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md)中提供的虚拟网络、VPN 连接、Active Directory 和 SharePoint 服务器场设计指导外，请务必将文件共享角色添加到 Azure 环境。</span><span class="sxs-lookup"><span data-stu-id="525bb-307">In addition to the guidance provided in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) for designing the virtual network, VPN connection, Active Directory, and SharePoint farm, be sure to add a file share role to the Azure environment.</span></span>
  
<span data-ttu-id="525bb-p131">要在灾难恢复解决方案中支持日志传送，应将文件共享虚拟机添加到数据库角色驻留的子网。文件共享还充当 SQL Server AlwaysOn 可用性组多数节点的第三个节点。对于使用 SQL Server AlwaysOn 可用性组的标准 SharePoint 服务器场，这是建议配置。</span><span class="sxs-lookup"><span data-stu-id="525bb-p131">To support log shipping in a disaster-recovery solution, a file share virtual machine is added to the subnet where the database roles reside. The file share also serves as the third node of a Node Majority for the SQL Server AlwaysOn availability group. This is the recommended configuration for a standard SharePoint farm that uses SQL Server AlwaysOn availability groups.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="525bb-p132">必须查看使数据库参与 SQL Server AlwaysOn 可用性组的先决条件。有关详细信息，请参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议](https://go.microsoft.com/fwlink/p/?LinkId=510870)。</span><span class="sxs-lookup"><span data-stu-id="525bb-p132">It is important to review the prerequisites for a database to participate in a SQL Server AlwaysOn availability group. For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870).</span></span> 
  
<span data-ttu-id="525bb-313">**图：用于灾难恢复解决方案的文件服务器的放置**</span><span class="sxs-lookup"><span data-stu-id="525bb-313">**Figure: Placement of a file server used for a disaster recovery solution**</span></span>

![显示添加到包含 SharePoint 数据库服务器角色的同一云服务的文件共享虚拟机。](images/AZenv_FSforDFSRandWSFC.png)
  
<span data-ttu-id="525bb-p133">在此图中，文件共享虚拟机将添加到 Azure 中包含数据库服务器角色的相同子网中。请勿将文件共享虚拟机添加到具有其他服务器角色的可用性集，例如 SQL Server 角色。</span><span class="sxs-lookup"><span data-stu-id="525bb-p133">In this diagram, a file share virtual machine is added to the same subnet in Azure that contains the database server roles. Do not add the file share virtual machine to an availability set with other server roles, such as the SQL Server roles.</span></span>
  
<span data-ttu-id="525bb-p134">如果你关注日志的高可用性，请考虑采取其他方法，即[使用 Azure Blob 存储服务进行 SQL Server 备份和还原](https://go.microsoft.com/fwlink/p/?LinkId=393113)。这是 Azure 中的新增功能，可将日志直接保存到 Blob 存储 URL。此解决方案不包括有关使用此功能的指导。</span><span class="sxs-lookup"><span data-stu-id="525bb-p134">If you are concerned about the high availability of the logs, consider taking a different approach by using [SQL Server backup and restore with Azure Blob Storage Service](https://go.microsoft.com/fwlink/p/?LinkId=393113). This is a new feature in Azure that saves logs directly to a blob storage URL. This solution does not include guidance about using this feature.</span></span>
  
<span data-ttu-id="525bb-p135">在设计恢复场时，请牢记，成功的灾难恢复环境能够准确反映你想要恢复的生产服务器场。恢复场的大小不是恢复场设计、部署和测试中最重要的因素。恢复场规模因组织而异，具体取决于组织的需求。在出现短暂中断时，它可能会使用向下伸缩的服务器场，或者直到性能和容量需求要求你扩展服务器场。</span><span class="sxs-lookup"><span data-stu-id="525bb-p135">When you design the recovery farm, keep in mind that a successful disaster recovery environment accurately reflects the production farm that you want to recover. The size of the recovery farm is not the most important thing in the recovery farm's design, deployment, and testing. Farm scale varies from organization to organization based on business requirements. It might be possible to use a scaled-down farm for a short outage or until performance and capacity demands require you to scale the farm.</span></span>
  
<span data-ttu-id="525bb-p136">将恢复场尽量配置得与生产服务器场相同，以便其满足服务级别协议 (SLA) 要求并提供支持业务所需的功能。当你设计灾难恢复环境时，还需审核生产环境的变更管理过程。我们建议你按与生产环境相同的间隔更新恢复环境，以将变更管理过程扩展到恢复环境。作为变更管理过程的一部分，我们建议你维护一张详细的服务器场配置、应用程序和用户清单。</span><span class="sxs-lookup"><span data-stu-id="525bb-p136">Configure the recovery farm as identically as possible to the production farm so that it meets your service level agreement (SLA) requirements and provides the functionality that you need to support your business. When you design the disaster recovery environment, also look at your change management process for your production environment. We recommend that you extend the change management process to the recovery environment by updating the recovery environment at the same interval as the production environment. As part of the change management process, we recommend maintaining a detailed inventory of your farm configuration, applications, and users.</span></span> 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a><span data-ttu-id="525bb-328">阶段 2：创建 Azure 虚拟网络和 VPN 连接</span><span class="sxs-lookup"><span data-stu-id="525bb-328">Phase 2: Create the Azure virtual network and VPN connection</span></span>
<span data-ttu-id="525bb-329"><a name="Phase2"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-329"><a name="Phase2"> </a></span></span>

<span data-ttu-id="525bb-p137">[将本地网络连接到 Microsoft Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) 介绍如何在 Azure 中规划和部署虚拟网络以及如何创建 VPN 连接。请按照相应主题中的指导完成下列过程：</span><span class="sxs-lookup"><span data-stu-id="525bb-p137">[Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) shows you how to plan and deploy the virtual network in Azure and how to create the VPN connection. Follow the guidance in the topic to complete the following procedures:</span></span>
  
- <span data-ttu-id="525bb-332">规划虚拟网络的专用 IP 地址空间。</span><span class="sxs-lookup"><span data-stu-id="525bb-332">Plan the private IP address space of the Virtual Network.</span></span>
    
- <span data-ttu-id="525bb-333">规划虚拟网络的路由基础结构更改。</span><span class="sxs-lookup"><span data-stu-id="525bb-333">Plan the routing infrastructure changes for the Virtual Network.</span></span>
    
- <span data-ttu-id="525bb-334">规划发送到本地 VPN 设备以及从本地 VPN 设备发出的流量的防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="525bb-334">Plan firewall rules for traffic to and from the on-premises VPN device.</span></span>
    
- <span data-ttu-id="525bb-335">在 Azure 中创建跨部署虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="525bb-335">Create the cross-premises virtual network in Azure.</span></span>
    
- <span data-ttu-id="525bb-336">配置本地网络和虚拟网络之间的路由。</span><span class="sxs-lookup"><span data-stu-id="525bb-336">Configure routing between your on-premises network and the Virtual Network.</span></span>
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a><span data-ttu-id="525bb-337">阶段 3：将 Active Directory 和域名服务部署到 Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="525bb-337">Phase 3: Deploy Active Directory and Domain Name Services to the Azure virtual network</span></span>
<span data-ttu-id="525bb-338"><a name="Phase3"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-338"><a name="Phase3"> </a></span></span>

<span data-ttu-id="525bb-339">此阶段包括将 Windows Server Active Directory 和 DNS 部署到混合方案中的 虚拟网络，如 [SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md)中所述以及下图中所示。</span><span class="sxs-lookup"><span data-stu-id="525bb-339">This phase includes deploying both Windows Server Active Directory and DNS to the Virtual Network in a hybrid scenario as described in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) and as illustrated in the following figure.</span></span>
  
<span data-ttu-id="525bb-340">**图：混合 Active Directory 域配置**</span><span class="sxs-lookup"><span data-stu-id="525bb-340">**Figure: Hybrid Active Directory domain configuration**</span></span>

![部署到 Azure 虚拟网络和 SharePoint 场子网的 STwo 虚拟机是域控制器和 DNS 服务器的副本](images/AZarch_HyADdomainConfig.png)
  
<span data-ttu-id="525bb-p138">在此图中，将两个虚拟机部署到相同的子网中。这两个虚拟机分别托管两个角色：Active Directory 和 DNS。</span><span class="sxs-lookup"><span data-stu-id="525bb-p138">In the illustration, two virtual machines are deployed to the same subnet. These virtual machines are each hosting two roles: Active Directory and DNS.</span></span>
  
<span data-ttu-id="525bb-p139">在 Azure 中部署 Active Directory 之前，阅读[在 Azure 虚拟机上部署 Windows Server Active Directory 的指南](https://go.microsoft.com/fwlink/p/?linkid=392681)。这些指南将帮助你确定你的解决方案是否需要不同的体系结构或不同的配置设置。</span><span class="sxs-lookup"><span data-stu-id="525bb-p139">Before deploying Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These guidelines help you determine whether you need a different architecture or different configuration settings for your solution.</span></span>
  
<span data-ttu-id="525bb-346">有关在 Azure 中设置域控制器的详细指导，请参阅[在 Azure 虚拟网络中安装副本 Active Directory 域控制器](https://go.microsoft.com/fwlink/p/?LinkId=392687)。</span><span class="sxs-lookup"><span data-stu-id="525bb-346">For detailed guidance on setting up a domain controller in Azure, see [Install a Replica Active Directory Domain Controller in Azure Virtual Networks](https://go.microsoft.com/fwlink/p/?LinkId=392687).</span></span>
  
<span data-ttu-id="525bb-p140">在此阶段之前，你没有向虚拟网络部署虚拟机。用于承载 Active Directory 和 DNS 的虚拟机可能不是你的解决方案需要的最大虚拟机。在部署这些虚拟机之前，首先创建你计划在虚拟网络中使用的最大虚拟机。这有助于确保你的解决方案在 Azure 中被标记为允许你需要的最大大小。目前不需要配置此虚拟机。只需进行创建，然后放到一旁。如果不这样做，你稍后在尝试创建更大的虚拟机时可能会受到限制，编写本文时此问题尚未解决。</span><span class="sxs-lookup"><span data-stu-id="525bb-p140">Before this phase, you didn't deploy virtual machines to the Virtual Network. The virtual machines for hosting Active Directory and DNS are likely not the largest virtual machines you need for the solution. Before you deploy these virtual machines, first create the largest virtual machine that you plan to use in your Virtual Network. This helps ensure that your solution lands on a tag in Azure that allows the largest size you need. You do not need to configure this virtual machine at this time. Simply create it, and set it aside. If you do not do this, you might run into a limitation when you try to create larger virtual machines later, which was an issue at the time this article was written.</span></span> 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a><span data-ttu-id="525bb-354">阶段 4：在 Azure 中部署 SharePoint 恢复场</span><span class="sxs-lookup"><span data-stu-id="525bb-354">Phase 4: Deploy the SharePoint recovery farm in Azure</span></span>
<span data-ttu-id="525bb-355"><a name="Phase4"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-355"><a name="Phase4"> </a></span></span>

<span data-ttu-id="525bb-p141">根据你的设计规划，在 虚拟网络 中部署 SharePoint 服务器场。在 Azure 中部署 SharePoint 角色之前，查看[在 Azure 基础结构服务上规划 SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=400984) 对你有一定的帮助。</span><span class="sxs-lookup"><span data-stu-id="525bb-p141">Deploy the SharePoint farm in your Virtual Network according to your design plans. It might be helpful to review [Planning for SharePoint 2013 on Azure Infrastructure Services](https://go.microsoft.com/fwlink/p/?LinkId=400984) before you deploy SharePoint roles in Azure.</span></span>
  
<span data-ttu-id="525bb-358">考虑在构建概念证明环境时了解到的以下做法：</span><span class="sxs-lookup"><span data-stu-id="525bb-358">Consider the following practices that we learned by building our proof of concept environment:</span></span>
  
- <span data-ttu-id="525bb-359">通过使用 Azure 门户或 PowerShell 创建虚拟机。</span><span class="sxs-lookup"><span data-stu-id="525bb-359">Create virtual machines by using the Azure portal or PowerShell.</span></span>
    
- <span data-ttu-id="525bb-p142">Azure 和 Hyper-V 不支持动态内存。请确保在你的性能和容量规划中考虑到了这一点。</span><span class="sxs-lookup"><span data-stu-id="525bb-p142">Azure and Hyper-V do not support dynamic memory. Be sure this is factored into your performance and capacity plans.</span></span>
    
- <span data-ttu-id="525bb-p143">通过 Azure 界面重新启动虚拟机，而不是在虚拟机登录时。使用 Azure 界面会更顺利，并且更易于预测。</span><span class="sxs-lookup"><span data-stu-id="525bb-p143">Restart virtual machines through the Azure interface, not from the virtual machine logon itself. Using the Azure interface works better and is more predictable.</span></span>
    
- <span data-ttu-id="525bb-p144">如果你想关闭某个虚拟机以节约成本，请使用 Azure 界面。如果你在虚拟机登录时关闭，费用仍会累计。</span><span class="sxs-lookup"><span data-stu-id="525bb-p144">If you want to shut down a virtual machine to save costs, use the Azure interface. If you shut down from the virtual machine logon, charges continue to accrue.</span></span>
    
- <span data-ttu-id="525bb-366">使用虚拟机的命名约定。</span><span class="sxs-lookup"><span data-stu-id="525bb-366">Use a naming convention for the virtual machines.</span></span>
    
- <span data-ttu-id="525bb-367">注意虚拟机部署在哪个数据中心位置。</span><span class="sxs-lookup"><span data-stu-id="525bb-367">Pay attention to which datacenter location the virtual machines are being deployed.</span></span>
    
- <span data-ttu-id="525bb-368">SharePoint 角色不支持 Azure 中的自动缩放功能。</span><span class="sxs-lookup"><span data-stu-id="525bb-368">The automatic scaling feature in Azure is not supported for SharePoint roles.</span></span>
    
- <span data-ttu-id="525bb-369">请勿在将要还原的服务器场中配置项目，例如网站集。</span><span class="sxs-lookup"><span data-stu-id="525bb-369">Do not configure items in the farm that will be restored, such as site collections.</span></span> 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a><span data-ttu-id="525bb-370">阶段 5：设置场之间的 DFSR</span><span class="sxs-lookup"><span data-stu-id="525bb-370">Phase 5: Set up DFSR between the farms</span></span>
<span data-ttu-id="525bb-371"><a name="Phase5"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-371"><a name="Phase5"> </a></span></span>

<span data-ttu-id="525bb-p145">要使用 DFSR 设置文件复制，请使用 DNS Management 管理单元。但是在 DFSR 设置之前，请登录到你的内部部署文件服务器和 Azure 文件服务器，并在 Windows 中启用服务。</span><span class="sxs-lookup"><span data-stu-id="525bb-p145">To set up file replication by using DFSR, use the DNS Management snap-in. However, before the DFSR setup, log on to your on-premises file server and Azure file server and enable the service in Windows.</span></span>
  
<span data-ttu-id="525bb-374">从服务器管理器仪表板中，完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="525bb-374">From the Server Manager Dashboard, complete the following steps:</span></span>
  
- <span data-ttu-id="525bb-375">配置本地服务器。</span><span class="sxs-lookup"><span data-stu-id="525bb-375">Configure the local server.</span></span>
    
- <span data-ttu-id="525bb-376">启动"添加角色和功能向导"。</span><span class="sxs-lookup"><span data-stu-id="525bb-376">Start the **Add Roles and Features Wizard**.</span></span>
    
- <span data-ttu-id="525bb-377">打开"文件和存储服务"节点。</span><span class="sxs-lookup"><span data-stu-id="525bb-377">Open the **File and Storage Services** node.</span></span>
    
- <span data-ttu-id="525bb-378">选择"DFS 命名空间"和"DFS 复制"。</span><span class="sxs-lookup"><span data-stu-id="525bb-378">Select **DFS Namespaces** and **DFS replication**.</span></span>
    
- <span data-ttu-id="525bb-379">单击"下一步"完成向导步骤。</span><span class="sxs-lookup"><span data-stu-id="525bb-379">Click **Next** to finish the wizard steps.</span></span>
    
<span data-ttu-id="525bb-380">下表提供了指向 DFSR 参考文章和博客文章的链接。</span><span class="sxs-lookup"><span data-stu-id="525bb-380">The following table provides links to DFSR reference articles and blog posts.</span></span>
  
<span data-ttu-id="525bb-381">**表：DFSR 的参考文章**</span><span class="sxs-lookup"><span data-stu-id="525bb-381">**Table: Reference articles for DFSR**</span></span>

|<span data-ttu-id="525bb-382">**标题**</span><span class="sxs-lookup"><span data-stu-id="525bb-382">**Title**</span></span>|<span data-ttu-id="525bb-383">**说明**</span><span class="sxs-lookup"><span data-stu-id="525bb-383">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="525bb-384">复制</span><span class="sxs-lookup"><span data-stu-id="525bb-384">Replication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |<span data-ttu-id="525bb-385">DFS 管理 TechNet 主题，包含复制链接</span><span class="sxs-lookup"><span data-stu-id="525bb-385">DFS Management TechNet topic with links for replication</span></span>  <br/> |
|[<span data-ttu-id="525bb-386">DFS 复制：生存指南</span><span class="sxs-lookup"><span data-stu-id="525bb-386">DFS Replication: Survival Guide</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |<span data-ttu-id="525bb-387">Wiki，包含 DFS 信息的链接</span><span class="sxs-lookup"><span data-stu-id="525bb-387">Wiki with links to DFS information</span></span>  <br/> |
|[<span data-ttu-id="525bb-388">DFS 复制：常见问题</span><span class="sxs-lookup"><span data-stu-id="525bb-388">DFS Replication: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |<span data-ttu-id="525bb-389">DFS 复制 TechNet 主题</span><span class="sxs-lookup"><span data-stu-id="525bb-389">DFS Replication TechNet topic</span></span>  <br/> |
|[<span data-ttu-id="525bb-390">Jose Barreto 的博客</span><span class="sxs-lookup"><span data-stu-id="525bb-390">Jose Barreto's Blog</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |<span data-ttu-id="525bb-391">由 Microsoft 文件服务器团队首席项目经理撰写的博客</span><span class="sxs-lookup"><span data-stu-id="525bb-391">Blog written by a Principal Program Manager on the File Server team at Microsoft</span></span>  <br/> |
|[<span data-ttu-id="525bb-392">Microsoft 存储团队 - 文件柜博客</span><span class="sxs-lookup"><span data-stu-id="525bb-392">The Storage Team at Microsoft - File Cabinet Blog</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |<span data-ttu-id="525bb-393">关于 Windows Server 中的文件服务和存储功能的博客</span><span class="sxs-lookup"><span data-stu-id="525bb-393">Blog about file services and storage features in Windows Server</span></span>  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a><span data-ttu-id="525bb-394">阶段 6：设置到恢复场的日志传送</span><span class="sxs-lookup"><span data-stu-id="525bb-394">Phase 6: Set up log shipping to the recovery farm</span></span>
<span data-ttu-id="525bb-395"><a name="Phase6"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-395"><a name="Phase6"> </a></span></span>

<span data-ttu-id="525bb-p146">日志传送是在此环境中设置灾难恢复的关键组件。你可以使用日志传送，将数据库的事务日志文件从主数据库服务器实例自动传送到辅助数据库服务器实例。要设置日志传送，请参阅[Configure log shipping in SharePoint 2013](http://technet.microsoft.com/library/482aeb81-e2aa-419f-a269-5b349a6c4721.aspx)。</span><span class="sxs-lookup"><span data-stu-id="525bb-p146">Log shipping is the critical component for setting up disaster recovery in this environment. You can use log shipping to automatically send transaction log files for databases from a primary database server instance to a secondary database server instance. To set up log shipping, see [Configure log shipping in SharePoint 2013](http://technet.microsoft.com/library/482aeb81-e2aa-419f-a269-5b349a6c4721.aspx).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="525bb-p147">SharePoint Server 中的日志传送支持仅限于特定数据库。有关详细信息，请参阅 [SharePoint 数据库的受支持的高可用性和灾难恢复选项 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121)。</span><span class="sxs-lookup"><span data-stu-id="525bb-p147">Log shipping support in SharePoint Server is limited to certain databases. For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121).</span></span> 
  
## <a name="phase-7-validate-failover-and-recovery"></a><span data-ttu-id="525bb-401">阶段 7：验证故障转移和恢复</span><span class="sxs-lookup"><span data-stu-id="525bb-401">Phase 7: Validate failover and recovery</span></span>
<span data-ttu-id="525bb-402"><a name="Phase7"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-402"><a name="Phase7"> </a></span></span>

<span data-ttu-id="525bb-p148">最后这一阶段的目的是验证灾难恢复解决方案按计划运行。为此，请创建一个故障转移事件，关闭生产服务器场并启动恢复场以进行替换。你可以手动或使用脚本启动故障转移方案。</span><span class="sxs-lookup"><span data-stu-id="525bb-p148">The goal of this final phase is to verify that the disaster recovery solution works as planned. To do this, create a failover event that shuts down the production farm and starts up the recovery farm as a replacement. You can start a failover scenario manually or by using scripts.</span></span>
  
<span data-ttu-id="525bb-p149">第一步是停止对服务器场服务或内容的传入用户请求。你可以通过禁用 DNS 条目或关闭前端 Web 服务器来执行此操作。服务器场关闭后，你可以故障转移到恢复场。</span><span class="sxs-lookup"><span data-stu-id="525bb-p149">The first step is to stop incoming user requests for farm services or content. You can do this by disabling DNS entries or by shutting down the front-end web servers. After the farm is "down," you can fail over to the recovery farm.</span></span>
  
### <a name="stop-log-shipping"></a><span data-ttu-id="525bb-409">停止日志传送</span><span class="sxs-lookup"><span data-stu-id="525bb-409">Stop log shipping</span></span>

<span data-ttu-id="525bb-p150">你必须在服务器场恢复之前停止日志传送。首先在 Azure 中的辅助服务器上停止日志传送，然后在内部部署主服务器上停止日志传送。使用以下脚本，首先在辅助服务器上，然后在主服务器上停止日志传送。脚本中的数据库名称可能不同，具体取决于你的环境。</span><span class="sxs-lookup"><span data-stu-id="525bb-p150">You must stop log shipping before farm recovery. Stop log shipping on the secondary server in Azure first, and then stop it on the primary server on-premises. Use the following script to stop log shipping on the secondary server first and then on the primary server. The database names in the script might be different, depending on your environment.</span></span>
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a><span data-ttu-id="525bb-414">将备份还原</span><span class="sxs-lookup"><span data-stu-id="525bb-414">Restore the backups</span></span>

<span data-ttu-id="525bb-p151">备份必须按其创建的顺序还原。在还原特定事务日志备份之前，你必须首先在不回滚未提交的事务的情况下，还原下列之前的备份（即，使用  `WITH NORECOVERY`）：</span><span class="sxs-lookup"><span data-stu-id="525bb-p151">Backups must be restored in the order in which they were created. Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions (that is, by using  `WITH NORECOVERY`):</span></span>
  
- <span data-ttu-id="525bb-p152">完整的数据库备份和最新的差异备份 - 还原在执行特定事务日志备份之前创建的备份（如果存在）。在最新的完整或差异数据库备份创建之前，数据库使用完整恢复模型或大容量日志恢复模型。</span><span class="sxs-lookup"><span data-stu-id="525bb-p152">The full database backup and the last differential backup - Restore these backups, if any exist, taken before the particular transaction log backup. Before the most recent full or differential database backup was created, the database was using the full recovery model or bulk-logged recovery model.</span></span>
    
- <span data-ttu-id="525bb-p153">所有事务日志备份 - 还原在执行完整数据库备份或差异备份（如果还原其中一个）之后，执行特定事务日志备份之前创建的备份。日志备份必须按其创建顺序应用，日志链中没有任何间隔。</span><span class="sxs-lookup"><span data-stu-id="525bb-p153">All transaction log backups - Restore any transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup. Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.</span></span>
    
<span data-ttu-id="525bb-p154">要恢复辅助服务器上的内容数据库以便由网站呈现，请在恢复之前移除所有数据库连接。要还原数据库，请运行以下 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="525bb-p154">To recover the content database on the secondary server so that the sites render, remove all database connections before recovery. To restore the database, run the following SQL statement.</span></span>
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> <span data-ttu-id="525bb-p155">明确使用 T-SQL 时，在每个 RESTORE 语句中指定 **WITH NORECOVERY** 或 **WITH RECOVERY** 以消除歧义这在编写脚本时非常重要。还原完整和差异备份后，可以在 SQL Server Management Studio 中还原事务日志。此外，由于日志传送已停止，内容数据库处于备用状态，因为你必须将状态更改为完全访问。</span><span class="sxs-lookup"><span data-stu-id="525bb-p155">When you use T-SQL explicitly, specify either **WITH NORECOVERY** or **WITH RECOVERY** in every RESTORE statement to eliminate ambiguity—this is very important when writing scripts. After the full and differential backups are restored, the transaction logs can be restored in SQL Server Management Studio. Also, because log shipping is already stopped, the content database is in a standby state, so you must change the state to full access.</span></span>
  
<span data-ttu-id="525bb-p156">在 SQL Server Management Studio 中，右键单击“WSS_Content”**** 数据库，依次指向“任务”**** > “还原”****，再单击“事务日志”****（如果还没有还原完整备份，则不可用）。有关详细信息，请参阅[还原事务日志备份 (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778)。</span><span class="sxs-lookup"><span data-stu-id="525bb-p156">In SQL Server Management Studio, right-click the **WSS_Content** database, point to **Tasks** > **Restore**, and then click **Transaction Log** (if you have not restored the full backup, this is not available). For more information, see[Restore a Transaction Log Backup (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).</span></span>
  
### <a name="crawl-the-content-source"></a><span data-ttu-id="525bb-428">对内容源进行爬网</span><span class="sxs-lookup"><span data-stu-id="525bb-428">Crawl the content source</span></span>

<span data-ttu-id="525bb-p157">你必须为每个内容源启动完整爬网以还原 Search Service。请注意，你会丢失内部部署服务器场的部分分析信息，例如搜索建议。在启动完整爬网之前，请使用 Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** 并指定日志传送和复制的搜索管理数据库 **Search_Service__DB_<GUID>**。此 cmdlet 将提供搜索配置、架构、托管属性、规则和源，并创建一组默认的其他组件。</span><span class="sxs-lookup"><span data-stu-id="525bb-p157">You must start a full crawl for each content source to restore the Search Service. Note that you lose some analytics information from the on-premises farm, such as search recommendations. Before you start the full crawls, use the Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** and specify the log-shipped and replicated Search Administration database, **Search_Service__DB_<GUID>**. This cmdlet gives the search configuration, schema, managed properties, rules, and sources and creates a default set of the other components.</span></span>
  
<span data-ttu-id="525bb-433">要启动完全爬网，请完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="525bb-433">To start a full crawl, complete the following steps:</span></span>
  
1. <span data-ttu-id="525bb-434">在 SharePoint 2013 管理中心中，转到"应用程序管理">"服务应用程序">"管理服务应用程序"，然后单击你要爬网的 Search Service 应用程序。</span><span class="sxs-lookup"><span data-stu-id="525bb-434">In the SharePoint 2013 Central Administration, go to **Application Management** > **Service Applications** > **Manage service applications**, and then click the Search Service application that you want to crawl.</span></span>
    
2. <span data-ttu-id="525bb-435">在"搜索管理"页上，单击"内容源"，指向你需要的内容源，单击箭头，然后单击"启动完整爬网"。</span><span class="sxs-lookup"><span data-stu-id="525bb-435">On the **Search Administration** page, click **Content Sources**, point to the content source that you want, click the arrow, and then click **Start Full Crawl**.</span></span>
    
### <a name="recover-farm-services"></a><span data-ttu-id="525bb-436">恢复服务器场服务</span><span class="sxs-lookup"><span data-stu-id="525bb-436">Recover farm services</span></span>
<span data-ttu-id="525bb-437"><a name="Reco"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-437"><a name="Reco"> </a></span></span>

<span data-ttu-id="525bb-438">下表显示如何恢复已对数据库进行日志传送的服务、具有数据库但不建议使用日志传送进行还原的服务，以及没有数据库的服务。</span><span class="sxs-lookup"><span data-stu-id="525bb-438">The following table shows how to recover services that have log-shipped databases, the services that have databases but are not recommended to restore with log shipping, and the services that do not have databases.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="525bb-439">将内部部署 SharePoint 数据库还原到 Azure 环境中将不会恢复任何尚未手动安装在 Azure 中的 SharePoint 服务。</span><span class="sxs-lookup"><span data-stu-id="525bb-439">Restoring an on-premises SharePoint database into the Azure environment will not recover any SharePoint services that you did not already install in Azure manually.</span></span> 
  
<span data-ttu-id="525bb-440">**表：服务应用程序数据库引用**</span><span class="sxs-lookup"><span data-stu-id="525bb-440">**Table: Service application database reference**</span></span>

|<span data-ttu-id="525bb-441">**从已进行日志传送的数据库还原这些服务**</span><span class="sxs-lookup"><span data-stu-id="525bb-441">**Restore these services from log-shipped databases**</span></span>|<span data-ttu-id="525bb-442">**这些服务具有数据库，但我们建议你直接启动这些服务，无需还原其数据库**</span><span class="sxs-lookup"><span data-stu-id="525bb-442">**These services have databases, but we recommend that you start these services without restoring their databases**</span></span>|<span data-ttu-id="525bb-443">**这些服务不在数据库中存储任何数据；请在故障转移后启动这些服务**</span><span class="sxs-lookup"><span data-stu-id="525bb-443">**These services do not store data in databases; start these services after failover**</span></span>|
|:-----|:-----|:-----|
| <span data-ttu-id="525bb-444">机器翻译服务</span><span class="sxs-lookup"><span data-stu-id="525bb-444">Machine Translation Service</span></span> <br/>  <span data-ttu-id="525bb-445">Managed Metadata Service</span><span class="sxs-lookup"><span data-stu-id="525bb-445">Managed Metadata Service</span></span> <br/>  <span data-ttu-id="525bb-446">Secure Store Service</span><span class="sxs-lookup"><span data-stu-id="525bb-446">Secure Store Service</span></span> <br/>  <span data-ttu-id="525bb-p158">User Profile。（仅支持配置文件和社交标签数据库。不支持同步数据库。）</span><span class="sxs-lookup"><span data-stu-id="525bb-p158">User Profile. (Only the Profile and Social Tagging databases are supported. The Synchronization database is not supported.)</span></span> <br/>  <span data-ttu-id="525bb-450">Microsoft SharePoint Foundation Subscription Settings Service</span><span class="sxs-lookup"><span data-stu-id="525bb-450">Microsoft SharePoint Foundation Subscription Settings Service</span></span> <br/> | <span data-ttu-id="525bb-451">Usage and Health Data Collection</span><span class="sxs-lookup"><span data-stu-id="525bb-451">Usage and Health Data Collection</span></span> <br/>  <span data-ttu-id="525bb-452">State service</span><span class="sxs-lookup"><span data-stu-id="525bb-452">State service</span></span> <br/>  <span data-ttu-id="525bb-453">Word Automation</span><span class="sxs-lookup"><span data-stu-id="525bb-453">Word automation</span></span> <br/> | <span data-ttu-id="525bb-454">Excel Services</span><span class="sxs-lookup"><span data-stu-id="525bb-454">Excel Services</span></span> <br/>  <span data-ttu-id="525bb-455">PerformancePoint Services</span><span class="sxs-lookup"><span data-stu-id="525bb-455">PerformancePoint Services</span></span> <br/>  <span data-ttu-id="525bb-456">PowerPoint 转换</span><span class="sxs-lookup"><span data-stu-id="525bb-456">PowerPoint Conversion</span></span> <br/>  <span data-ttu-id="525bb-457">Visio Graphics Service</span><span class="sxs-lookup"><span data-stu-id="525bb-457">Visio Graphics Service</span></span> <br/>  <span data-ttu-id="525bb-458">工作管理</span><span class="sxs-lookup"><span data-stu-id="525bb-458">Work Management</span></span> <br/> |
   
<span data-ttu-id="525bb-459">以下示例演示如何从数据库中还原 Managed Metadata Service。</span><span class="sxs-lookup"><span data-stu-id="525bb-459">The following example shows how to restore the Managed Metadata service from a database.</span></span>
  
<span data-ttu-id="525bb-p159">需使用现有的Managed_Metadata_DB数据库。此数据库已进行日志传送，但辅助服务器场上没有活动的服务应用程序，因此需要在服务应用程序就位后进行连接。</span><span class="sxs-lookup"><span data-stu-id="525bb-p159">This uses the existing Managed_Metadata_DB database. This database is log shipped, but there is no active service application on the secondary farm, so it needs to be connected after the service application is in place.</span></span>
  
<span data-ttu-id="525bb-462">首先，使用  `New-SPMetadataServiceApplication`，并使用已还原数据库的名称指定  `DatabaseName` 开关。</span><span class="sxs-lookup"><span data-stu-id="525bb-462">First, use  `New-SPMetadataServiceApplication`, and specify the  `DatabaseName` switch with the name of the restored database.</span></span>
  
<span data-ttu-id="525bb-463">接下来，在辅助服务器上配置新的 Managed Metadata Service 应用程序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="525bb-463">Next, configure the new Managed Metadata Service Application on the secondary server, as follows:</span></span>
  
- <span data-ttu-id="525bb-464">名称：Managed Metadata Service</span><span class="sxs-lookup"><span data-stu-id="525bb-464">Name: Managed Metadata Service</span></span>
    
- <span data-ttu-id="525bb-465">数据库服务器：传送的事务日志中的数据库名称</span><span class="sxs-lookup"><span data-stu-id="525bb-465">Database server: The database name from the shipped transaction log</span></span>
    
- <span data-ttu-id="525bb-466">数据库名称：Managed_Metadata_DB</span><span class="sxs-lookup"><span data-stu-id="525bb-466">Database name: Managed_Metadata_DB</span></span>
    
- <span data-ttu-id="525bb-467">应用程序池：SharePoint 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="525bb-467">Application pool: SharePoint Service Applications</span></span> 
    
### <a name="manage-dns-records"></a><span data-ttu-id="525bb-468">管理 DNS 记录</span><span class="sxs-lookup"><span data-stu-id="525bb-468">Manage DNS records</span></span>
<span data-ttu-id="525bb-469"><a name="DNS"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-469"><a name="DNS"> </a></span></span>

<span data-ttu-id="525bb-470">你必须手动创建 DNS 记录以指向你的 SharePoint 服务器场。</span><span class="sxs-lookup"><span data-stu-id="525bb-470">You must manually create DNS records to point to your SharePoint farm.</span></span>
  
<span data-ttu-id="525bb-p160">在你具有多个前端 Web 服务器的大多数情况下，利用 Windows Server 2012 中的网络负载平衡功能或硬件负载平衡器在服务器场中的 Web 前端服务器之间分发请求是明智的。网络负载平衡还可以在一个 Web 前端服务器出现故障时将请求分发到其他服务器，从而减少风险。</span><span class="sxs-lookup"><span data-stu-id="525bb-p160">In most cases where you have multiple front-end web servers, it makes sense to take advantage of the Network Load Balancing feature in Windows Server 2012 or a hardware load balancer to distribute requests among the web-front-end servers in your farm. Network load balancing can also help reduce risk by distributing requests to the other servers if one of your web-front-end servers fails.</span></span> 
  
<span data-ttu-id="525bb-p161">通常情况下，当你设置网络负载平衡时，将向群集分配单个 IP 地址。然后你在 DNS 提供程序中为指向群集的网络创建 DNS 主机。（在此项目中，我们将 DNS 服务器放置在 Azure 中，确保在出现内部部署数据中心故障时能够恢复。）例如，你可以在 DNS 管理器的 Active Directory 中创建指向负载平衡群集的 IP 地址的 DNS 记录（例如，称为  `http://sharepoint.contoso.com`）。</span><span class="sxs-lookup"><span data-stu-id="525bb-p161">Typically, when you set up network load balancing, your cluster is assigned a single IP address. You then create a DNS host record in the DNS provider for your network that points to the cluster. (For this project, we put a DNS server in Azure for resiliency in case of an on-premises datacenter failure.) For instance, you can create a DNS record, in DNS Manager in Active Directory, for example, called  `http://sharepoint.contoso.com`, that points to the IP address for your load-balanced cluster.</span></span>
  
<span data-ttu-id="525bb-p162">若要从外部访问 SharePoint 场，可以在外部 DNS 服务器上创建主机记录，且 URL 与客户端在 Intranet 上使用的指向防火墙中外部 IP 地址的 URL（例如，http://sharepoint.contoso.com)）相同。（在此示例中，最佳做法是设置拆分 DNS，让内部 DNS 服务器对 contoso.com 有控制权，并将请求直接路由到 SharePoint 场群集，而不是将 DNS 请求路由到外部 DNS 服务器。）然后，可以将外部 IP 地址映射到本地群集的内部 IP 地址，以便客户端能够找到所需的资源。</span><span class="sxs-lookup"><span data-stu-id="525bb-p162">For external access to your SharePoint farm, you can create a host record on an external DNS server with the same URL that clients use on your intranet (for example, http://sharepoint.contoso.com) that points to an external IP address in your firewall. (A best practice, using this example, is to set up split DNS so that the internal DNS server is authoritative for contoso.com and routes requests directly to the SharePoint farm cluster, rather than routing DNS requests to your external DNS server.) You can then map the external IP address to the internal IP address of your on-premises cluster so that clients find the resources they are looking for.</span></span>
  
<span data-ttu-id="525bb-478">接下来，将介绍几种不同的灾难恢复应用场景：</span><span class="sxs-lookup"><span data-stu-id="525bb-478">From here, you might run into a couple of different disaster-recovery scenarios:</span></span>
  
 <span data-ttu-id="525bb-p163">**示例场景：由于内部部署 SharePoint 服务器场中的硬件故障，内部部署 SharePoint 服务器场不可用。** 这种情况下，在你完成故障转移到 Azure SharePoint 服务器场的步骤后，你可以在恢复 SharePoint 服务器场的 Web 前端服务器上配置网络负载平衡，就像在内部部署服务器场中一样。然后你可以将内部 DNS 提供程序中的主机记录重定向为指向恢复场的群集 IP 地址。请注意，可能需要一些时间才会刷新客户端上的缓存 DNS 记录并使其指向恢复场。</span><span class="sxs-lookup"><span data-stu-id="525bb-p163">**Example scenario: The on-premises SharePoint farm is unavailable because of hardware failure in the on-premises SharePoint farm.** In this case, after you have completed the steps for failover to the Azure SharePoint farm, you can configure network load balancing on the recovery SharePoint farm's web-front-end servers, the same way you did with the on-premises farm. You can then redirect the host record in your internal DNS provider to point to the recovery farm's cluster IP address. Note that it can take some time before cached DNS records on clients are refreshed and point to the recovery farm.</span></span>
  
 <span data-ttu-id="525bb-p164">**示例场景：内部部署数据中心会完全中断。** 此场景可能是由于自然灾害所致，例如火灾或水灾。这种情况下，对于企业来说，可能希望有一个辅助数据中心承载在另一个区域，还有具有自己的目录服务和 DNS 的 Azure 子网。与前一个灾难场景中一样，你可以将内部和外部 DNS 记录重定向为指向 Azure SharePoint 服务器场。同样，记下该 DNS 记录传播可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="525bb-p164">**Example scenario: The on-premises datacenter is lost completely.** This scenario might occur due to a natural disaster, such as a fire or flood. In this case, for an enterprise, you would likely have a secondary datacenter hosted in another region as well as your Azure subnet that has its own directory services and DNS. As in the previous disaster scenario, you can redirect your internal and external DNS records to point to the Azure SharePoint farm. Again, take note that DNS-record propagation can take some time.</span></span>
  
<span data-ttu-id="525bb-p165">如果使用的是主机命名网站集，根据[主机命名网站集体系结构和部署 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393120) 中的建议，可以让 SharePoint 场中的同一 Web 应用程序托管多个网站集，分别具有唯一 DNS 名称（例如，http://sales.contoso.com 和 http://marketing.contoso.com)）。在这种情况下，可以为每个网站集创建指向群集 IP 地址的 DNS 记录。在请求到达 SharePoint Web 前端服务器后，它们就会着手将各个请求路由到相应的网站集。</span><span class="sxs-lookup"><span data-stu-id="525bb-p165">If you are using host-named site collections, as recommended in [Host-named site collection architecture and deployment (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393120), you might have several site collections hosted by the same web application in your SharePoint farm, with unique DNS names (for example, http://sales.contoso.com and http://marketing.contoso.com). In this case, you can create DNS records for each site collection that point to your cluster IP address. After a request reaches your SharePoint web-front-end servers, they handle routing each request to the appropriate site collection.</span></span>
  
## <a name="microsoft-proof-of-concept-environment"></a><span data-ttu-id="525bb-491">Microsoft 概念证明环境</span><span class="sxs-lookup"><span data-stu-id="525bb-491">Microsoft proof-of-concept environment</span></span>
<span data-ttu-id="525bb-492"><a name="POC"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-492"><a name="POC"> </a></span></span>

<span data-ttu-id="525bb-p166">我们为此解决方案设计了概念证明环境并进行了测试。我们的测试环境的设计目标是部署和恢复已在客户环境中找到的 SharePoint 服务器场。我们进行了几种假设，但我们始终牢记，服务器场需提供所有现成功能，而无需进行任何自定义。我们使用现场和产品团队的最佳实践指南设计拓扑，确保其高可用性。</span><span class="sxs-lookup"><span data-stu-id="525bb-p166">We designed and tested a proof-of-concept environment for this solution. The design goal for our test environment was to deploy and recover a SharePoint farm that we might find in a customer environment. We made several assumptions, but we knew that the farm needed to provide all of the out-of-the-box functionality without any customizations. The topology was designed for high availability by using best practice guidance from the field and product group.</span></span>
  
<span data-ttu-id="525bb-497">下表列出了我们为内部部署测试环境创建和配置的 Hyper-V 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="525bb-497">The following table describes the Hyper-V virtual machines that we created and configured for the on-premises test environment.</span></span>
  
<span data-ttu-id="525bb-498">**表：用于内部部署测试的虚拟机**</span><span class="sxs-lookup"><span data-stu-id="525bb-498">**Table: Virtual machines for on-premises test**</span></span>

|<span data-ttu-id="525bb-499">**服务器名称。**</span><span class="sxs-lookup"><span data-stu-id="525bb-499">**Server name**</span></span>|<span data-ttu-id="525bb-500">**角色**</span><span class="sxs-lookup"><span data-stu-id="525bb-500">**Role**</span></span>|<span data-ttu-id="525bb-501">**配置**</span><span class="sxs-lookup"><span data-stu-id="525bb-501">**Configuration**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="525bb-502">DC1</span><span class="sxs-lookup"><span data-stu-id="525bb-502">DC1</span></span>  <br/> |<span data-ttu-id="525bb-503">具有 Active Directory 的域控制器。</span><span class="sxs-lookup"><span data-stu-id="525bb-503">Domain controller with Active Directory.</span></span>  <br/> |<span data-ttu-id="525bb-504">两个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-504">Two processors</span></span>  <br/> <span data-ttu-id="525bb-505">从 512 MB 到 4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-505">From 512 MB through 4 GB of RAM</span></span>  <br/> <span data-ttu-id="525bb-506">1 x 127-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-506">1 x 127-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="525bb-507">RRAS</span><span class="sxs-lookup"><span data-stu-id="525bb-507">RRAS</span></span>  <br/> |<span data-ttu-id="525bb-508">配置为路由和远程访问服务 (RRAS) 角色的服务器。</span><span class="sxs-lookup"><span data-stu-id="525bb-508">Server configured with the Routing and Remote Access Service (RRAS) role.</span></span>  <br/> |<span data-ttu-id="525bb-509">两个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-509">Two processors</span></span>  <br/> <span data-ttu-id="525bb-510">2-8 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-510">2-8 GB of RAM</span></span>  <br/> <span data-ttu-id="525bb-511">1 x 127-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-511">1 x 127-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="525bb-512">FS1</span><span class="sxs-lookup"><span data-stu-id="525bb-512">FS1</span></span>  <br/> |<span data-ttu-id="525bb-513">具有备份共享和 DFSR 终结点的文件服务器。</span><span class="sxs-lookup"><span data-stu-id="525bb-513">File server with shares for backups and an end point for DFSR.</span></span>  <br/> |<span data-ttu-id="525bb-514">四个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-514">Four processors</span></span>  <br/> <span data-ttu-id="525bb-515">2-12 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-515">2-12 GB of RAM</span></span>  <br/> <span data-ttu-id="525bb-516">1 x 127-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-516">1 x 127-GB hard disk</span></span>  <br/> <span data-ttu-id="525bb-517">1 x 1-TB 硬盘 (SAN)</span><span class="sxs-lookup"><span data-stu-id="525bb-517">1 x 1-TB hard disk (SAN)</span></span>  <br/> <span data-ttu-id="525bb-518">1 x 750-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-518">1 x 750-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="525bb-519">SP-WFE1、SP-WFE2</span><span class="sxs-lookup"><span data-stu-id="525bb-519">SP-WFE1, SP-WFE2</span></span>  <br/> |<span data-ttu-id="525bb-520">前端 Web 服务器。</span><span class="sxs-lookup"><span data-stu-id="525bb-520">Front-end web servers.</span></span>  <br/> |<span data-ttu-id="525bb-521">四个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-521">Four processors</span></span>  <br/> <span data-ttu-id="525bb-522">16 GB RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-522">16 GB of RAM</span></span>  <br/> |
|<span data-ttu-id="525bb-523">SP-APP1、SP-APP2、SP-APP3</span><span class="sxs-lookup"><span data-stu-id="525bb-523">SP-APP1, SP-APP2, SP-APP3</span></span>  <br/> |<span data-ttu-id="525bb-524">应用程序服务器。</span><span class="sxs-lookup"><span data-stu-id="525bb-524">Application servers.</span></span>  <br/> |<span data-ttu-id="525bb-525">四个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-525">Four processors</span></span>  <br/> <span data-ttu-id="525bb-526">2-16 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-526">2-16 GB of RAM</span></span>  <br/> |
|<span data-ttu-id="525bb-527">SP-SQL-HA1、SP-SQL-HA2</span><span class="sxs-lookup"><span data-stu-id="525bb-527">SP-SQL-HA1, SP-SQL-HA2</span></span>  <br/> |<span data-ttu-id="525bb-p167">数据库服务器，配置了 SQL Server 2012 AlwaysOn 可用性组以提供高可用性。此配置使用 SP-SQL-HA1 和 SP-SQL-HA2 作为主副本和辅助副本。</span><span class="sxs-lookup"><span data-stu-id="525bb-p167">Database servers, configured with SQL Server 2012 AlwaysOn availability groups to provide high availability. This configuration uses SP-SQL-HA1 and SP-SQL-HA2 as the primary and secondary replicas.</span></span>  <br/> |<span data-ttu-id="525bb-530">四个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-530">Four processors</span></span>  <br/> <span data-ttu-id="525bb-531">2-16 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-531">2-16 GB of RAM</span></span>  <br/> |
   
<span data-ttu-id="525bb-532">下表介绍了我们为内部部署测试环境的前端 Web 服务器和应用程序服务器而创建和配置的 Hyper-V 虚拟机的驱动器配置。</span><span class="sxs-lookup"><span data-stu-id="525bb-532">The following table describes drive configurations for the Hyper-V virtual machines that we created and configured for the front-end web and application servers for the on-premises test environment.</span></span>
  
<span data-ttu-id="525bb-533">**表：用于内部部署测试的前端 Web 服务器和应用程序服务器的虚拟机驱动器要求**</span><span class="sxs-lookup"><span data-stu-id="525bb-533">**Table: Virtual machine drive requirements for the Front End Web and Application servers for the on-premises test**</span></span>

|<span data-ttu-id="525bb-534">**驱动器号**</span><span class="sxs-lookup"><span data-stu-id="525bb-534">**Drive letter**</span></span>|<span data-ttu-id="525bb-535">**尺寸**</span><span class="sxs-lookup"><span data-stu-id="525bb-535">**Size**</span></span>|<span data-ttu-id="525bb-536">**目录名称**</span><span class="sxs-lookup"><span data-stu-id="525bb-536">**Directory name**</span></span>|<span data-ttu-id="525bb-537">**路径**</span><span class="sxs-lookup"><span data-stu-id="525bb-537">**Path**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="525bb-538">C</span><span class="sxs-lookup"><span data-stu-id="525bb-538">C</span></span>  <br/> |<span data-ttu-id="525bb-539">80</span><span class="sxs-lookup"><span data-stu-id="525bb-539">80</span></span>  <br/> |<span data-ttu-id="525bb-540">系统驱动器</span><span class="sxs-lookup"><span data-stu-id="525bb-540">System drive</span></span>  <br/> |<span data-ttu-id="525bb-541"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\</span><span class="sxs-lookup"><span data-stu-id="525bb-541"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\</span></span>  <br/> |
|<span data-ttu-id="525bb-542">E</span><span class="sxs-lookup"><span data-stu-id="525bb-542">E</span></span>  <br/> |<span data-ttu-id="525bb-543">80</span><span class="sxs-lookup"><span data-stu-id="525bb-543">80</span></span>  <br/> |<span data-ttu-id="525bb-544">日志驱动器 (40 GB)</span><span class="sxs-lookup"><span data-stu-id="525bb-544">Log drive (40 GB)</span></span>  <br/> |<span data-ttu-id="525bb-545"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span><span class="sxs-lookup"><span data-stu-id="525bb-545"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="525bb-546">F</span><span class="sxs-lookup"><span data-stu-id="525bb-546">F</span></span>  <br/> |<span data-ttu-id="525bb-547">80</span><span class="sxs-lookup"><span data-stu-id="525bb-547">80</span></span>  <br/> |<span data-ttu-id="525bb-548">页面 (36 GB)</span><span class="sxs-lookup"><span data-stu-id="525bb-548">Page (36 GB)</span></span>  <br/> |<span data-ttu-id="525bb-549"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL\\DATA</span><span class="sxs-lookup"><span data-stu-id="525bb-549"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL\\DATA</span></span>  <br/> |
   
<span data-ttu-id="525bb-p168">下表介绍了创建和配置作为内部部署数据库服务器的 Hyper-V 虚拟机的驱动器配置。在"数据库引擎配置"页上，访问"数据目录"选项卡以设置并确认下表中所示的设置。</span><span class="sxs-lookup"><span data-stu-id="525bb-p168">The following table describes drive configurations for the Hyper-V virtual machines created and configured to serve as the on-premises database servers. On the **Database Engine Configuration** page, access the **Data Directories** tab to set and confirm the settings shown in the following table.</span></span>
  
<span data-ttu-id="525bb-552">**表：用于内部部署测试的数据库服务器的虚拟机驱动器要求**</span><span class="sxs-lookup"><span data-stu-id="525bb-552">**Table: Virtual machine drive requirements for the database server for the on-premises test**</span></span>

|<span data-ttu-id="525bb-553">**驱动器号**</span><span class="sxs-lookup"><span data-stu-id="525bb-553">**Drive letter**</span></span>|<span data-ttu-id="525bb-554">**尺寸**</span><span class="sxs-lookup"><span data-stu-id="525bb-554">**Size**</span></span>|<span data-ttu-id="525bb-555">**目录名称**</span><span class="sxs-lookup"><span data-stu-id="525bb-555">**Directory name**</span></span>|<span data-ttu-id="525bb-556">**路径**</span><span class="sxs-lookup"><span data-stu-id="525bb-556">**Path**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="525bb-557">C</span><span class="sxs-lookup"><span data-stu-id="525bb-557">C</span></span>  <br/> |<span data-ttu-id="525bb-558">80</span><span class="sxs-lookup"><span data-stu-id="525bb-558">80</span></span>  <br/> |<span data-ttu-id="525bb-559">数据根目录</span><span class="sxs-lookup"><span data-stu-id="525bb-559">Data root directory</span></span>  <br/> |<span data-ttu-id="525bb-560"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\</span><span class="sxs-lookup"><span data-stu-id="525bb-560"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\</span></span>  <br/> |
|<span data-ttu-id="525bb-561">E</span><span class="sxs-lookup"><span data-stu-id="525bb-561">E</span></span>  <br/> |<span data-ttu-id="525bb-562">500</span><span class="sxs-lookup"><span data-stu-id="525bb-562">500</span></span>  <br/> |<span data-ttu-id="525bb-563">用户数据库目录</span><span class="sxs-lookup"><span data-stu-id="525bb-563">User database directory</span></span>  <br/> |<span data-ttu-id="525bb-564"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span><span class="sxs-lookup"><span data-stu-id="525bb-564"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="525bb-565">F</span><span class="sxs-lookup"><span data-stu-id="525bb-565">F</span></span>  <br/> |<span data-ttu-id="525bb-566">500</span><span class="sxs-lookup"><span data-stu-id="525bb-566">500</span></span>  <br/> |<span data-ttu-id="525bb-567">用户数据库日志目录</span><span class="sxs-lookup"><span data-stu-id="525bb-567">User database log directory</span></span>  <br/> |<span data-ttu-id="525bb-568"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span><span class="sxs-lookup"><span data-stu-id="525bb-568"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="525bb-569">G</span><span class="sxs-lookup"><span data-stu-id="525bb-569">G</span></span>  <br/> |<span data-ttu-id="525bb-570">500</span><span class="sxs-lookup"><span data-stu-id="525bb-570">500</span></span>  <br/> |<span data-ttu-id="525bb-571">临时数据库目录</span><span class="sxs-lookup"><span data-stu-id="525bb-571">Temp DB directory</span></span>  <br/> |<span data-ttu-id="525bb-572"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span><span class="sxs-lookup"><span data-stu-id="525bb-572"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="525bb-573">H</span><span class="sxs-lookup"><span data-stu-id="525bb-573">H</span></span>  <br/> |<span data-ttu-id="525bb-574">500</span><span class="sxs-lookup"><span data-stu-id="525bb-574">500</span></span>  <br/> |<span data-ttu-id="525bb-575">临时数据库日志目录</span><span class="sxs-lookup"><span data-stu-id="525bb-575">Temp DB log directory</span></span>  <br/> |<span data-ttu-id="525bb-576"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span><span class="sxs-lookup"><span data-stu-id="525bb-576"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
   
### <a name="setting-up-the-test-environment"></a><span data-ttu-id="525bb-577">设置测试环境</span><span class="sxs-lookup"><span data-stu-id="525bb-577">Setting up the test environment</span></span>

<span data-ttu-id="525bb-p169">在不同的部署阶段，测试团队通常首先构建内部部署基础结构，然后构建相应的 Azure 环境。这反映了内部生产服务器场已在运行的常规真实案例。更为重要的是，你应该了解当前生产工作负载、容量和典型性能。除了构建可以满足业务需求的灾难恢复模型外，你还应该调整恢复场服务器的大小以交付最低级别的服务。在冷备用或温备用环境中，恢复场通常小于生产服务器场。恢复场稳定并且投入生产之后，服务器场可以向上和向外扩展以满足工作负载要求。</span><span class="sxs-lookup"><span data-stu-id="525bb-p169">During the different deployment phases, the test team typically worked on the on-premises architecture first and then on the corresponding Azure environment. This reflects the general real-world cases where in-house production farms are already running. What is even more important is that you should know the current production workload, capacity, and typical performance. In addition to building a disaster recovery model that can meet business requirements, you should size the recovery farm servers to deliver a minimum level of service. In a cold or warm standby environment, a recovery farm is typically smaller than a production farm. After the recovery farm is stable and in production, the farm can be scaled up and out to meet workload requirements.</span></span>
  
<span data-ttu-id="525bb-584">我们分三个阶段来部署测试环境：</span><span class="sxs-lookup"><span data-stu-id="525bb-584">We deployed our test environment in the following three phases:</span></span>
  
- <span data-ttu-id="525bb-585">设置混合基础结构</span><span class="sxs-lookup"><span data-stu-id="525bb-585">Set up the hybrid infrastructure</span></span>
    
- <span data-ttu-id="525bb-586">设置服务器</span><span class="sxs-lookup"><span data-stu-id="525bb-586">Provision the servers</span></span>
    
- <span data-ttu-id="525bb-587">部署 SharePoint 服务器场</span><span class="sxs-lookup"><span data-stu-id="525bb-587">Deploy the SharePoint farms</span></span>
    
#### <a name="set-up-the-hybrid-infrastructure"></a><span data-ttu-id="525bb-588">设置混合基础结构</span><span class="sxs-lookup"><span data-stu-id="525bb-588">Set up the hybrid infrastructure</span></span>

<span data-ttu-id="525bb-p170">此阶段涉及设置内部部署服务器场的域环境以及 Azure 中的恢复场。除了与配置 Active Directory 相关的普通任务之外，测试团队还在两个环境之间实施了一个路由解决方案和 VPN 连接。</span><span class="sxs-lookup"><span data-stu-id="525bb-p170">This phase involved setting up a domain environment for the on-premises farm and for the recovery farm in Azure. In addition to the normal tasks associated with configuring Active Directory, the test team implemented a routing solution and a VPN connection between the two environments.</span></span>
  
#### <a name="provision-the-servers"></a><span data-ttu-id="525bb-591">设置服务器</span><span class="sxs-lookup"><span data-stu-id="525bb-591">Provision the servers</span></span>

<span data-ttu-id="525bb-p171">除了场服务器之外，还必须为域控制器设置服务器，并配置处理 RRAS 以及站点间 VPN 的服务器。为 DFSR 服务设置两个文件服务器，为测试人员设置多个客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="525bb-p171">In addition to the farm servers, it was necessary to provision servers for the domain controllers and configure a server to handle RRAS as well as the site-to-site VPN. Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.</span></span>
  
#### <a name="deploy-the-sharepoint-farms"></a><span data-ttu-id="525bb-594">部署 SharePoint 服务器场</span><span class="sxs-lookup"><span data-stu-id="525bb-594">Deploy the SharePoint farms</span></span>

<span data-ttu-id="525bb-p172">SharePoint 服务器场分两个阶段部署，以便在必要时简化环境稳定化和故障排除。在第一个阶段中，每个服务器场部署在拓扑每一层最低数量的服务器上，以支持所需功能。</span><span class="sxs-lookup"><span data-stu-id="525bb-p172">The SharePoint farms were deployed in two stages in order to simplify environment stabilization and troubleshooting, if required. During the first stage, each farm was deployed on the minimum number of servers for each tier of the topology to support the required functionality.</span></span>
  
<span data-ttu-id="525bb-p173">我们在创建 SharePoint 2013 服务器之前创建安装了 SQL Server 的数据库服务器。因为这是一个新部署，我们在部署 SharePoint 之前创建了可用性组。我们根据 MCS 最佳实践指南创建了三个组。</span><span class="sxs-lookup"><span data-stu-id="525bb-p173">We created the database servers with SQL Server installed before creating the SharePoint 2013 servers. Because this was a new deployment, we created the availability groups before deploying SharePoint. We created three groups based on MCS best practice guidance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="525bb-p174">创建占位符数据库，以便你可以在执行 SharePoint 安装之前创建可用性组。有关详细信息，请参阅[为 SharePoint 2013 配置 SQL Server 2012 AlwaysOn 可用性组](https://go.microsoft.com/fwlink/p/?LinkId=517626)</span><span class="sxs-lookup"><span data-stu-id="525bb-p174">Create placeholder databases so that you can create availability groups before the SharePoint installation. For more information, see [Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)</span></span>
  
<span data-ttu-id="525bb-602">我们创建了服务器场并按以下顺序加入其他服务器：</span><span class="sxs-lookup"><span data-stu-id="525bb-602">We created the farm and joined additional servers in the following order:</span></span>
  
- <span data-ttu-id="525bb-603">设置 SP-SQL-HA1 和 SP-SQL-HA2。</span><span class="sxs-lookup"><span data-stu-id="525bb-603">Provision SP-SQL-HA1 and SP-SQL-HA2.</span></span>
    
- <span data-ttu-id="525bb-604">为服务器场配置 AlwaysOn 并创建三个可用性组。</span><span class="sxs-lookup"><span data-stu-id="525bb-604">Configure AlwaysOn and create the three availability groups for the farm.</span></span> 
    
- <span data-ttu-id="525bb-605">将 SP-APP1 设置为承载管理中心。</span><span class="sxs-lookup"><span data-stu-id="525bb-605">Provision SP-APP1 to host Central Administration.</span></span>
    
- <span data-ttu-id="525bb-606">将 SP-WFE1 和 SP-WFE2 设置为承载分布式缓存。</span><span class="sxs-lookup"><span data-stu-id="525bb-606">Provision SP-WFE1 and SP-WFE2 to host the distributed cache.</span></span> 
    
<span data-ttu-id="525bb-p175">在命令行运行 **psconfig.exe** 时，我们使用了 _skipRegisterAsDistributedCachehost_ 参数。有关详细信息，请参阅[在 SharePoint 中规划源和分布式缓存服务 (SharePoint Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=270985)。</span><span class="sxs-lookup"><span data-stu-id="525bb-p175">We used the  _skipRegisterAsDistributedCachehost_ parameter when we ran **psconfig.exe** at the command line. For more information, see[Plan for feeds and the Distributed Cache service in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?linkid=270985).</span></span> 
  
<span data-ttu-id="525bb-609">在恢复环境中重复以下步骤：</span><span class="sxs-lookup"><span data-stu-id="525bb-609">We repeated the following steps in the recovery environment:</span></span>
  
- <span data-ttu-id="525bb-610">设置 AZ-SQL-HA1 和 AZ-SQL-HA2。</span><span class="sxs-lookup"><span data-stu-id="525bb-610">Provision AZ-SQL-HA1 and AZ-SQL-HA2.</span></span>
    
- <span data-ttu-id="525bb-611">为服务器场配置 AlwaysOn 并创建三个可用性组。</span><span class="sxs-lookup"><span data-stu-id="525bb-611">Configure AlwaysOn and create the three availability groups for the farm.</span></span>
    
- <span data-ttu-id="525bb-612">将 AZ-APP1 设置为承载管理中心。</span><span class="sxs-lookup"><span data-stu-id="525bb-612">Provision AZ-APP1 to host Central Administration.</span></span>
    
- <span data-ttu-id="525bb-613">将 AZ-WFE1 和 AZ-WFE2 设置为承载分布式缓存。</span><span class="sxs-lookup"><span data-stu-id="525bb-613">Provision AZ-WFE1 and AZ-WFE2 to host the distributed cache.</span></span>
    
<span data-ttu-id="525bb-p176">配置分布式缓存并添加测试用户和测试内容后，我们开始部署的第二个阶段。此阶段需要向外扩展各层并将场服务器配置为支持服务器场体系结构中所述的高可用性拓扑。</span><span class="sxs-lookup"><span data-stu-id="525bb-p176">After we configured the distributed cache and added test users and test content, we started stage two of the deployment. This required scaling out the tiers and configuring the farm servers to support the high-availability topology described in the farm architecture.</span></span>
  
<span data-ttu-id="525bb-616">下表介绍了我们为恢复场设置的虚拟机、子网和可用性集。</span><span class="sxs-lookup"><span data-stu-id="525bb-616">The following table describes the virtual machines, subnets, and availability sets we set up for our recovery farm.</span></span>
  
<span data-ttu-id="525bb-617">**表：恢复场基础结构**</span><span class="sxs-lookup"><span data-stu-id="525bb-617">**Table: Recovery farm infrastructure**</span></span>

|<span data-ttu-id="525bb-618">**服务器名称。**</span><span class="sxs-lookup"><span data-stu-id="525bb-618">**Server name**</span></span>|<span data-ttu-id="525bb-619">**角色**</span><span class="sxs-lookup"><span data-stu-id="525bb-619">**Role**</span></span>|<span data-ttu-id="525bb-620">**配置**</span><span class="sxs-lookup"><span data-stu-id="525bb-620">**Configuration**</span></span>|<span data-ttu-id="525bb-621">**子网**</span><span class="sxs-lookup"><span data-stu-id="525bb-621">**Subnet**</span></span>|<span data-ttu-id="525bb-622">**可用性集**</span><span class="sxs-lookup"><span data-stu-id="525bb-622">**Availability set**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="525bb-623">spDRAD</span><span class="sxs-lookup"><span data-stu-id="525bb-623">spDRAD</span></span>  <br/> |<span data-ttu-id="525bb-624">具有 Active Directory 的域控制器</span><span class="sxs-lookup"><span data-stu-id="525bb-624">Domain controller with Active Directory</span></span>  <br/> |<span data-ttu-id="525bb-625">两个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-625">Two processors</span></span>  <br/> <span data-ttu-id="525bb-626">从 512 MB 到 4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-626">From 512 MB through 4 GB of RAM</span></span>  <br/> <span data-ttu-id="525bb-627">1 x 127-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-627">1 x 127-GB hard disk</span></span>  <br/> |<span data-ttu-id="525bb-628">sp-ADservers</span><span class="sxs-lookup"><span data-stu-id="525bb-628">sp-ADservers</span></span>  <br/> ||
|<span data-ttu-id="525bb-629">AZ-SP-FS</span><span class="sxs-lookup"><span data-stu-id="525bb-629">AZ-SP-FS</span></span>  <br/> |<span data-ttu-id="525bb-630">具有备份共享和 DFSR 终结点的文件服务器</span><span class="sxs-lookup"><span data-stu-id="525bb-630">File server with shares for backups and an endpoint for DFSR</span></span>  <br/> | <span data-ttu-id="525bb-631">A5 配置：</span><span class="sxs-lookup"><span data-stu-id="525bb-631">A5 configuration:</span></span> <br/>  <span data-ttu-id="525bb-632">两个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-632">Two processors</span></span> <br/>  <span data-ttu-id="525bb-633">14 GB RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-633">14 GB of RAM</span></span> <br/>  <span data-ttu-id="525bb-634">1 x 127-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-634">1 x 127-GB hard disk</span></span> <br/>  <span data-ttu-id="525bb-635">1 x 135-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-635">1 x 135-GB hard disk</span></span> <br/>  <span data-ttu-id="525bb-636">1 x 127-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-636">1 x 127-GB hard disk</span></span> <br/>  <span data-ttu-id="525bb-637">1 x 150-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-637">1 x 150-GB hard disk</span></span> <br/> |<span data-ttu-id="525bb-638">sp-databaseservers</span><span class="sxs-lookup"><span data-stu-id="525bb-638">sp-databaseservers</span></span>  <br/> |<span data-ttu-id="525bb-639">DATA_SET</span><span class="sxs-lookup"><span data-stu-id="525bb-639">DATA_SET</span></span>  <br/> |
|<span data-ttu-id="525bb-640">AZ-WFE1、AZ -WFE2</span><span class="sxs-lookup"><span data-stu-id="525bb-640">AZ-WFE1, AZ -WFE2</span></span>  <br/> |<span data-ttu-id="525bb-641">前端 Web 服务器</span><span class="sxs-lookup"><span data-stu-id="525bb-641">Front End Web servers</span></span>  <br/> | <span data-ttu-id="525bb-642">A5 配置：</span><span class="sxs-lookup"><span data-stu-id="525bb-642">A5 configuration:</span></span> <br/>  <span data-ttu-id="525bb-643">两个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-643">Two processors</span></span> <br/>  <span data-ttu-id="525bb-644">14 GB RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-644">14 GB of RAM</span></span> <br/>  <span data-ttu-id="525bb-645">1 x 127-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-645">1 x 127-GB hard disk</span></span> <br/> |<span data-ttu-id="525bb-646">sp-webservers</span><span class="sxs-lookup"><span data-stu-id="525bb-646">sp-webservers</span></span>  <br/> |<span data-ttu-id="525bb-647">WFE_SET</span><span class="sxs-lookup"><span data-stu-id="525bb-647">WFE_SET</span></span>  <br/> |
|<span data-ttu-id="525bb-648">AZ -APP1、AZ -APP2、AZ -APP3</span><span class="sxs-lookup"><span data-stu-id="525bb-648">AZ -APP1, AZ -APP2, AZ -APP3</span></span>  <br/> |<span data-ttu-id="525bb-649">应用程序服务器</span><span class="sxs-lookup"><span data-stu-id="525bb-649">Application servers</span></span>  <br/> | <span data-ttu-id="525bb-650">A5 配置：</span><span class="sxs-lookup"><span data-stu-id="525bb-650">A5 configuration:</span></span> <br/>  <span data-ttu-id="525bb-651">两个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-651">Two processors</span></span> <br/>  <span data-ttu-id="525bb-652">14 GB RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-652">14 GB of RAM</span></span> <br/>  <span data-ttu-id="525bb-653">1 x 127-GB 硬盘</span><span class="sxs-lookup"><span data-stu-id="525bb-653">1 x 127-GB hard disk</span></span> <br/> |<span data-ttu-id="525bb-654">sp-applicationservers</span><span class="sxs-lookup"><span data-stu-id="525bb-654">sp-applicationservers</span></span>  <br/> |<span data-ttu-id="525bb-655">APP_SET</span><span class="sxs-lookup"><span data-stu-id="525bb-655">APP_SET</span></span>  <br/> |
|<span data-ttu-id="525bb-656">AZ -SQL-HA1、AZ -SQL-HA2</span><span class="sxs-lookup"><span data-stu-id="525bb-656">AZ -SQL-HA1, AZ -SQL-HA2</span></span>  <br/> |<span data-ttu-id="525bb-657">数据库服务器以及 AlwaysOn 可用性组的主副本和辅助副本</span><span class="sxs-lookup"><span data-stu-id="525bb-657">Database servers and primary and secondary replicas for AlwaysOn availability groups</span></span>  <br/> | <span data-ttu-id="525bb-658">A5 配置：</span><span class="sxs-lookup"><span data-stu-id="525bb-658">A5 configuration:</span></span> <br/>  <span data-ttu-id="525bb-659">两个处理器</span><span class="sxs-lookup"><span data-stu-id="525bb-659">Two processors</span></span> <br/>  <span data-ttu-id="525bb-660">14 GB RAM</span><span class="sxs-lookup"><span data-stu-id="525bb-660">14 GB of RAM</span></span> <br/> |<span data-ttu-id="525bb-661">sp-databaseservers</span><span class="sxs-lookup"><span data-stu-id="525bb-661">sp-databaseservers</span></span>  <br/> |<span data-ttu-id="525bb-662">DATA_SET</span><span class="sxs-lookup"><span data-stu-id="525bb-662">DATA_SET</span></span>  <br/> |
   
### <a name="operations"></a><span data-ttu-id="525bb-663">操作</span><span class="sxs-lookup"><span data-stu-id="525bb-663">Operations</span></span>

<span data-ttu-id="525bb-664">测试团队将服务器场环境稳定下来并完成功能测试之后，即开始配置内部部署恢复环境所需的下列操作任务：</span><span class="sxs-lookup"><span data-stu-id="525bb-664">After the test team stabilized the farm environments and completed functional testing, they started the following operations tasks required to configure the on-premises recovery environment:</span></span>
  
- <span data-ttu-id="525bb-665">配置完整备份和差异备份。</span><span class="sxs-lookup"><span data-stu-id="525bb-665">Configure full and differential backups.</span></span>
    
- <span data-ttu-id="525bb-666">在负责在内部部署环境和 Azure 环境之间传输事务日志的文件服务器上配置 DFSR。</span><span class="sxs-lookup"><span data-stu-id="525bb-666">Configure DFSR on the file servers that transfer transaction logs between the on-premises environment and the Azure environment.</span></span>
    
- <span data-ttu-id="525bb-667">在主数据库服务器上配置日志传送。</span><span class="sxs-lookup"><span data-stu-id="525bb-667">Configure log shipping on the primary database server.</span></span>
    
- <span data-ttu-id="525bb-p177">根据需要稳定和验证日志传送并进行故障排除。这包括标识和记录可能导致网络延迟等问题的任何行为，这些行为可能导致日志传送或 DFSR 文件同步失败。</span><span class="sxs-lookup"><span data-stu-id="525bb-p177">Stabilize, validate, and troubleshoot log shipping, as required. This included identifying and documenting any behavior that might cause issues, such as network latency, which would cause log shipping or DFSR file synchronization failures.</span></span>
    
### <a name="databases"></a><span data-ttu-id="525bb-670">数据库</span><span class="sxs-lookup"><span data-stu-id="525bb-670">Databases</span></span>

<span data-ttu-id="525bb-671">我们的故障转移测试涉及以下数据库：</span><span class="sxs-lookup"><span data-stu-id="525bb-671">Our failover tests involved the following databases:</span></span> 
  
- <span data-ttu-id="525bb-672">WSS_Content</span><span class="sxs-lookup"><span data-stu-id="525bb-672">WSS_Content</span></span>
    
- <span data-ttu-id="525bb-673">ManagedMetadata</span><span class="sxs-lookup"><span data-stu-id="525bb-673">ManagedMetadata</span></span>
    
- <span data-ttu-id="525bb-674">配置文件数据库</span><span class="sxs-lookup"><span data-stu-id="525bb-674">Profile DB</span></span>
    
- <span data-ttu-id="525bb-675">同步数据库</span><span class="sxs-lookup"><span data-stu-id="525bb-675">Sync DB</span></span>
    
- <span data-ttu-id="525bb-676">社交数据库</span><span class="sxs-lookup"><span data-stu-id="525bb-676">Social DB</span></span>
    
- <span data-ttu-id="525bb-677">内容类型集线器（用于专用内容类型联合集线器的数据库）</span><span class="sxs-lookup"><span data-stu-id="525bb-677">Content Type Hub (a database for a dedicated Content Type Syndication Hub)</span></span>
    
## <a name="troubleshooting-tips"></a><span data-ttu-id="525bb-678">疑难解答提示</span><span class="sxs-lookup"><span data-stu-id="525bb-678">Troubleshooting tips</span></span>
<span data-ttu-id="525bb-679"><a name="Troubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-679"><a name="Troubleshooting"> </a></span></span>

<span data-ttu-id="525bb-680">本节介绍在测试过程中遇到的问题及其解决方案。</span><span class="sxs-lookup"><span data-stu-id="525bb-680">The section explains the problems we encountered during our testing and their solutions.</span></span> 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a><span data-ttu-id="525bb-681">使用术语库管理工具导致了错误："托管元数据存储或连接当前不可用。"</span><span class="sxs-lookup"><span data-stu-id="525bb-681">Using the Term Store Management Tool caused the error, "The Managed Metadata Store or Connection is currently not available."</span></span>

<span data-ttu-id="525bb-682">确保 Web 应用程序使用的应用程序池帐户具有读取术语库的权限。</span><span class="sxs-lookup"><span data-stu-id="525bb-682">Ensure that the application pool account used by the web application has the Read Access to Term Store permission.</span></span>
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a><span data-ttu-id="525bb-683">自定义术语集在网站集中不可用</span><span class="sxs-lookup"><span data-stu-id="525bb-683">Custom term sets are not available in the site collection</span></span>

<span data-ttu-id="525bb-p178">检查内容网站集和内容类型集线器之间是否缺少服务应用程序关联。此外，在"Managed Metadata - <网站集名称> 连接"属性屏幕中，确保此选项已启用："此服务应用程序是栏特定的术语集的默认存储位置。"</span><span class="sxs-lookup"><span data-stu-id="525bb-p178">Check for a missing service application association between your content site collection and your content type hub. In addition, under the **Managed Metadata - <site collection name> Connection** properties screen, make sure this option is enabled: **This service application is the default storage location for column specific term sets.**</span></span>
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a><span data-ttu-id="525bb-686">Get-ADForest Windows PowerShell 命令会生成错误："术语'Get-ADForest'未识别为 cmdlet、函数、脚本文件或可运行程序的名称。"</span><span class="sxs-lookup"><span data-stu-id="525bb-686">The Get-ADForest Windows PowerShell command generates the error, "The term 'Get-ADForest' is not recognized as the name of a cmdlet, function, script file, or operable program."</span></span>

<span data-ttu-id="525bb-p179">设置用户配置文件时，需要 Active Directory 林名称。在“添加角色和功能”向导中，确保已启用用于 Windows PowerShell 的 Active Directory 模块（依次转到“远程服务器管理工具”>“角色管理工具”>“AD DS 和 AD LDS 工具”**** 部分下）。此外，先运行以下命令，再使用 **Get-ADForest**，以确保已加载软件依赖项。</span><span class="sxs-lookup"><span data-stu-id="525bb-p179">When setting up user profiles, you need the Active Directory forest name. In the Add Roles and Features Wizard, ensure that you have enabled the Active Directory Module for Windows PowerShell (under the **Remote Server Administration Tools>Role Administration Tools>AD DS and AD LDS Tools** section). In addition, run the following commands before using **Get-ADForest** to help ensure that your software dependencies are loaded.</span></span>
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwaysonhealth-xevent-session-on-server-name"></a><span data-ttu-id="525bb-690">在"<服务器名称>"上启动"AlwaysOn_health"XEvent 会话时可用性组创建失败</span><span class="sxs-lookup"><span data-stu-id="525bb-690">Availability group creation fails at Starting the 'AlwaysOn_health' XEvent session on '<server name>'</span></span>

<span data-ttu-id="525bb-691">确保故障转移群集中的两个节点已启动，没有暂停或停止。</span><span class="sxs-lookup"><span data-stu-id="525bb-691">Ensure that both nodes of your failover cluster are in the Status "Up" and not "Paused" or "Stopped".</span></span> 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a><span data-ttu-id="525bb-692">SQL Server 日志传送作业失败，并显示尝试连接到文件共享时出现访问拒绝错误</span><span class="sxs-lookup"><span data-stu-id="525bb-692">SQL Server log shipping job fails with access denied error trying to connect to the file share</span></span>

<span data-ttu-id="525bb-693">确保你的 SQL Server Agent 在网络凭据而不是默认凭据下运行。</span><span class="sxs-lookup"><span data-stu-id="525bb-693">Ensure that your SQL Server Agent is running under network credentials, instead of the default credentials.</span></span>
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a><span data-ttu-id="525bb-694">SQL Server 日志传送作业指示成功，但未复制任何文件</span><span class="sxs-lookup"><span data-stu-id="525bb-694">SQL Server log shipping job indicates success, but no files are copied</span></span>

<span data-ttu-id="525bb-p180">发生这种情况是因为可用性组的默认备份首选项是"首选辅助"。确保你是从可用性组的辅助服务器而不是主服务器运行日志传送作业，否则，作业将失败且无提示。</span><span class="sxs-lookup"><span data-stu-id="525bb-p180">This happens because the default backup preference for an availability group is **Prefer Secondary**. Ensure that you run the log shipping job from the secondary server for the availability group instead of the primary; otherwise, the job will fail silently.</span></span> 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a><span data-ttu-id="525bb-697">Managed Metadata Service（或其他 SharePoint 服务）在安装后无法自动启动</span><span class="sxs-lookup"><span data-stu-id="525bb-697">Managed Metadata service (or other SharePoint service) fails to start automatically after installation</span></span>

<span data-ttu-id="525bb-p181">服务可能需要几分钟才能启动，具体取决于你的 SharePoint Server 的性能和当前负载。手动单击服务的“启动”**** 按钮，留出足够的时间让服务器启动，并时常刷新一下服务器上的服务屏幕以监视其状态。如果服务仍处于停止状态，启用 SharePoint 诊断日志记录，再次尝试启动服务，然后检查日志中是否包含错误。有关详细信息，请参阅[在 SharePoint 2013 中配置诊断日志记录](https://go.microsoft.com/fwlink/p/?LinkId=510884)</span><span class="sxs-lookup"><span data-stu-id="525bb-p181">Services might take several minutes to start, depending on the performance and current load of your SharePoint Server. Manually click **Start** for the service and provide adequate time for startup while occasionally refreshing the Services on Server screen to monitor its status. In case the service remains stopped, enable SharePoint diagnostic logging, attempt to start the service again, and then check the log for errors. For more information, see[Configure diagnostic logging in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=510884)</span></span>
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a><span data-ttu-id="525bb-702">将 DNS 更改为 Azure 故障转移环境之后，客户端浏览器继续使用 SharePoint 网站的旧 IP 地址</span><span class="sxs-lookup"><span data-stu-id="525bb-702">After changing DNS to the Azure failover environment, client browsers continue to use the old IP address for the SharePoint site</span></span>

<span data-ttu-id="525bb-p182">你的 DNS 更改可能不会立即对所有客户端可见。在测试客户端上，从提升的命令提示符处执行以下命令，并再次尝试访问该网站。</span><span class="sxs-lookup"><span data-stu-id="525bb-p182">Your DNS change might not be visible to all clients immediately. On a test client, perform the following command from an elevated command prompt and attempt to access the site again.</span></span>
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a><span data-ttu-id="525bb-705">其他资源</span><span class="sxs-lookup"><span data-stu-id="525bb-705">Additional resources</span></span>
<span data-ttu-id="525bb-706"><a name="Troubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-706"><a name="Troubleshooting"> </a></span></span>

[<span data-ttu-id="525bb-707">SharePoint 数据库的受支持的高可用性和灾难恢复选项 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="525bb-707">Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393121)
  
[<span data-ttu-id="525bb-708">为 SharePoint 2013 配置 SQL Server 2012 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="525bb-708">Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a><span data-ttu-id="525bb-709">另请参阅</span><span class="sxs-lookup"><span data-stu-id="525bb-709">See Also</span></span>

<span data-ttu-id="525bb-710"><a name="Troubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="525bb-710"><a name="Troubleshooting"> </a></span></span>

[<span data-ttu-id="525bb-711">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="525bb-711">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



