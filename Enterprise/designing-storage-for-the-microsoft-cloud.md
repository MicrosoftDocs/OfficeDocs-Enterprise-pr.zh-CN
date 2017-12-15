---
title: "设计 Microsoft 云存储"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "摘要： 了解您为何需要云存储，查看的 Microsoft 的云存储选项和密钥存储方案的列表。"
ms.openlocfilehash: 3501f6a39498276d02fe4178f701a06dfb6a3e93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="30ca0-103">设计 Microsoft 云存储</span><span class="sxs-lookup"><span data-stu-id="30ca0-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="30ca0-104">**摘要：**了解您为何需要云存储，查看的 Microsoft 的云存储选项和密钥存储方案的列表。</span><span class="sxs-lookup"><span data-stu-id="30ca0-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="30ca0-105">与 Microsoft 云服务集成存储到范围广泛的服务和云平台选项使您可以访问。</span><span class="sxs-lookup"><span data-stu-id="30ca0-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="30ca0-106">为什么云存储？</span><span class="sxs-lookup"><span data-stu-id="30ca0-106">Why cloud storage?</span></span>

<span data-ttu-id="30ca0-107">有两种使用云存储的主要原因。</span><span class="sxs-lookup"><span data-stu-id="30ca0-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="30ca0-108">推向市场的速度：</span><span class="sxs-lookup"><span data-stu-id="30ca0-108">Speed to market:</span></span>
    
  - <span data-ttu-id="30ca0-109">更快地配置为具有高可用性和灾难恢复能力的</span><span class="sxs-lookup"><span data-stu-id="30ca0-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="30ca0-110">购买任何存储硬件</span><span class="sxs-lookup"><span data-stu-id="30ca0-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="30ca0-111">由 Microsoft 的云服务提供的内置管道</span><span class="sxs-lookup"><span data-stu-id="30ca0-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="30ca0-112">可从任何地方在世界上</span><span class="sxs-lookup"><span data-stu-id="30ca0-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="30ca0-113">更低的成本来维护：</span><span class="sxs-lookup"><span data-stu-id="30ca0-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="30ca0-114">若要缩放向上和向下的存储需求的弹性</span><span class="sxs-lookup"><span data-stu-id="30ca0-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="30ca0-115">没有存储硬件维护或迁移</span><span class="sxs-lookup"><span data-stu-id="30ca0-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="30ca0-116">Microsoft 为您内置的管道工，维护和改善基础结构</span><span class="sxs-lookup"><span data-stu-id="30ca0-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="30ca0-117">在市场上进行了持续改进的最佳存储安全</span><span class="sxs-lookup"><span data-stu-id="30ca0-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="30ca0-118">Microsoft 云存储选项</span><span class="sxs-lookup"><span data-stu-id="30ca0-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="30ca0-119">为帮助您理解云存储选项范围广泛，我们使用一个构造类比。</span><span class="sxs-lookup"><span data-stu-id="30ca0-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="30ca0-120">中移动已准备好</span><span class="sxs-lookup"><span data-stu-id="30ca0-120">Move-in ready</span></span>

<span data-ttu-id="30ca0-p101">使用这些预组包的解决方案捆绑在一起，与现有的服务。使用立即和最小配置。</span><span class="sxs-lookup"><span data-stu-id="30ca0-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="30ca0-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="30ca0-123">Office 365</span></span>
    
- <span data-ttu-id="30ca0-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="30ca0-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="30ca0-125">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="30ca0-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="30ca0-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="30ca0-126">Dynamics 365</span></span>
    
- <span data-ttu-id="30ca0-127">Visual Studio 团队服务</span><span class="sxs-lookup"><span data-stu-id="30ca0-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="30ca0-128">Azure 站点恢复</span><span class="sxs-lookup"><span data-stu-id="30ca0-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="30ca0-129">Yammer 站点共享</span><span class="sxs-lookup"><span data-stu-id="30ca0-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="30ca0-130">Azure 的备份</span><span class="sxs-lookup"><span data-stu-id="30ca0-130">Azure Backup</span></span>
    
<span data-ttu-id="30ca0-131">其中的每个细节云存储选项，请参阅[移动中的准备](move-in-ready.md)。</span><span class="sxs-lookup"><span data-stu-id="30ca0-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="30ca0-132">一些所需的程序集</span><span class="sxs-lookup"><span data-stu-id="30ca0-132">Some assembly required</span></span>

<span data-ttu-id="30ca0-133">作为起点与其他配置存储解决方案或自定义合适的编码使用现有的服务。</span><span class="sxs-lookup"><span data-stu-id="30ca0-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="30ca0-134">Azure 内容交付网络</span><span class="sxs-lookup"><span data-stu-id="30ca0-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="30ca0-135">Azure 媒体服务</span><span class="sxs-lookup"><span data-stu-id="30ca0-135">Azure Media Services</span></span>
    
- <span data-ttu-id="30ca0-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="30ca0-136">HdInsight</span></span>
    
- <span data-ttu-id="30ca0-137">Azure 的 Redis 高速缓存</span><span class="sxs-lookup"><span data-stu-id="30ca0-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="30ca0-138">Azure SQL 数据库</span><span class="sxs-lookup"><span data-stu-id="30ca0-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="30ca0-139">SQL Server 在 Azure 的 VM</span><span class="sxs-lookup"><span data-stu-id="30ca0-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="30ca0-140">Azure 宇宙 DB</span><span class="sxs-lookup"><span data-stu-id="30ca0-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="30ca0-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="30ca0-141">StorSimple</span></span>
    
- <span data-ttu-id="30ca0-142">SQL azure 数据仓库</span><span class="sxs-lookup"><span data-stu-id="30ca0-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="30ca0-143">Azure 数据湖存储区</span><span class="sxs-lookup"><span data-stu-id="30ca0-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="30ca0-144">每个云存储选项的详细信息，请参阅[所需的某些程序集](some-assembly-required.md)。</span><span class="sxs-lookup"><span data-stu-id="30ca0-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="30ca0-145">从零开始构建</span><span class="sxs-lookup"><span data-stu-id="30ca0-145">Build from the ground up</span></span>

<span data-ttu-id="30ca0-146">这些存储构建基块，以及编码，用于从头开始创建您自己的应用程序或存储解决方案。</span><span class="sxs-lookup"><span data-stu-id="30ca0-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="30ca0-147">Azure 存储 （文件）</span><span class="sxs-lookup"><span data-stu-id="30ca0-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="30ca0-148">Azure 存储 (blob)</span><span class="sxs-lookup"><span data-stu-id="30ca0-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="30ca0-149">Azure 存储 （队列）</span><span class="sxs-lookup"><span data-stu-id="30ca0-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="30ca0-150">Azure 存储 （表）</span><span class="sxs-lookup"><span data-stu-id="30ca0-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="30ca0-151">每个云存储选项的详细信息，请参阅[从头开始了](build-from-the-ground-up.md)。</span><span class="sxs-lookup"><span data-stu-id="30ca0-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="30ca0-152">密钥存储方案</span><span class="sxs-lookup"><span data-stu-id="30ca0-152">Key storage scenarios</span></span>

<span data-ttu-id="30ca0-153">下面是需要基于云存储的关键方案：</span><span class="sxs-lookup"><span data-stu-id="30ca0-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="30ca0-154">缓存数据</span><span class="sxs-lookup"><span data-stu-id="30ca0-154">Cache data</span></span>
    
    <span data-ttu-id="30ca0-155">对常用的数据访问速度通过将它存储在高速缓存中。</span><span class="sxs-lookup"><span data-stu-id="30ca0-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="30ca0-156">与团队成员协作</span><span class="sxs-lookup"><span data-stu-id="30ca0-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="30ca0-157">若要允许访问云存储中的数据的多个用户授予权限。</span><span class="sxs-lookup"><span data-stu-id="30ca0-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="30ca0-158">管理数据</span><span class="sxs-lookup"><span data-stu-id="30ca0-158">Manage data</span></span>
    
    <span data-ttu-id="30ca0-159">存储、 移动或删除内部或外部的大容量数据。</span><span class="sxs-lookup"><span data-stu-id="30ca0-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="30ca0-160">管理源代码</span><span class="sxs-lookup"><span data-stu-id="30ca0-160">Manage source code</span></span>
    
    <span data-ttu-id="30ca0-161">上载、 协作并在云中运行应用程序的代码文件。</span><span class="sxs-lookup"><span data-stu-id="30ca0-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="30ca0-162">备份文件</span><span class="sxs-lookup"><span data-stu-id="30ca0-162">Backup files</span></span>
    
    <span data-ttu-id="30ca0-163">将异地内部或外部数据的副本存储在云的多个位置。</span><span class="sxs-lookup"><span data-stu-id="30ca0-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="30ca0-164">发布公司的通信</span><span class="sxs-lookup"><span data-stu-id="30ca0-164">Publish company communications</span></span>
    
    <span data-ttu-id="30ca0-165">创建出版物的内部或外部邮件的单个点。</span><span class="sxs-lookup"><span data-stu-id="30ca0-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="30ca0-166">分发数以百万计的事件</span><span class="sxs-lookup"><span data-stu-id="30ca0-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="30ca0-167">创建网站、 应用程序和设备的遥测接收存储。</span><span class="sxs-lookup"><span data-stu-id="30ca0-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="30ca0-168">管理/服务于视频</span><span class="sxs-lookup"><span data-stu-id="30ca0-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="30ca0-169">存储并向客户或组织用户提供视频内容。</span><span class="sxs-lookup"><span data-stu-id="30ca0-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="30ca0-170">后续步骤</span><span class="sxs-lookup"><span data-stu-id="30ca0-170">Next step</span></span>

<span data-ttu-id="30ca0-171">查看[准备搬入](move-in-ready.md)云存储选项。</span><span class="sxs-lookup"><span data-stu-id="30ca0-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="30ca0-172">See Also</span><span class="sxs-lookup"><span data-stu-id="30ca0-172">See Also</span></span>

[<span data-ttu-id="30ca0-173">企业架构师的 Microsoft 云存储</span><span class="sxs-lookup"><span data-stu-id="30ca0-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="30ca0-174">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="30ca0-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="30ca0-175">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="30ca0-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


