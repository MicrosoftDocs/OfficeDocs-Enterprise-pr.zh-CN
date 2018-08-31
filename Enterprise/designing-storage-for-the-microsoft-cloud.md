---
title: 设计用于 Microsoft 云的存储
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: 摘要： 了解您为何需要云存储，并查看 Microsoft 云存储选项和密钥存储方案的列表。
ms.openlocfilehash: d96992d63115095dd6a1b7277886d0a4bb2bc02f
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915227"
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="bf6b1-103">设计用于 Microsoft 云的存储</span><span class="sxs-lookup"><span data-stu-id="bf6b1-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="bf6b1-104">**摘要：** 了解您为何需要云存储和查看 Microsoft 云存储选项和密钥存储方案的列表。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="bf6b1-105">将您的存储与 Microsoft 云服务集成到各种服务和云平台选项使您可以访问。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="bf6b1-106">为什么云存储？</span><span class="sxs-lookup"><span data-stu-id="bf6b1-106">Why cloud storage?</span></span>

<span data-ttu-id="bf6b1-107">有两个主要原因使用云存储。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="bf6b1-108">上市速度：</span><span class="sxs-lookup"><span data-stu-id="bf6b1-108">Speed to market:</span></span>
    
  - <span data-ttu-id="bf6b1-109">更快地配置高可用性和灾难恢复</span><span class="sxs-lookup"><span data-stu-id="bf6b1-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="bf6b1-110">若要购买没有存储硬件</span><span class="sxs-lookup"><span data-stu-id="bf6b1-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="bf6b1-111">Microsoft 云服务所提供的内置管道</span><span class="sxs-lookup"><span data-stu-id="bf6b1-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="bf6b1-112">可从在世界各地</span><span class="sxs-lookup"><span data-stu-id="bf6b1-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="bf6b1-113">若要维护的降低成本：</span><span class="sxs-lookup"><span data-stu-id="bf6b1-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="bf6b1-114">弹性扩展上下存储要求</span><span class="sxs-lookup"><span data-stu-id="bf6b1-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="bf6b1-115">没有存储硬件维护或迁移</span><span class="sxs-lookup"><span data-stu-id="bf6b1-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="bf6b1-116">Microsoft 是您内置管道工维护和改善基础结构</span><span class="sxs-lookup"><span data-stu-id="bf6b1-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="bf6b1-117">与持续改进市场中的最佳存储安全</span><span class="sxs-lookup"><span data-stu-id="bf6b1-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="bf6b1-118">Microsoft 云存储选项</span><span class="sxs-lookup"><span data-stu-id="bf6b1-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="bf6b1-119">若要帮助您了解各种云存储选项，我们使用构造葡萄形状。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="bf6b1-120">移入已准备就绪</span><span class="sxs-lookup"><span data-stu-id="bf6b1-120">Move-in ready</span></span>

<span data-ttu-id="bf6b1-p101">与现有服务使用这些捆绑在一起的预先打包的解决方案。使用立即和最小配置。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="bf6b1-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="bf6b1-123">Office 365</span></span>
    
- <span data-ttu-id="bf6b1-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="bf6b1-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="bf6b1-125">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="bf6b1-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="bf6b1-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="bf6b1-126">Dynamics 365</span></span>
    
- <span data-ttu-id="bf6b1-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="bf6b1-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="bf6b1-128">Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="bf6b1-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="bf6b1-129">Yammer 共享网站</span><span class="sxs-lookup"><span data-stu-id="bf6b1-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="bf6b1-130">Azure 备份</span><span class="sxs-lookup"><span data-stu-id="bf6b1-130">Azure Backup</span></span>
    
<span data-ttu-id="bf6b1-131">每个的详细信息云存储选项，请参阅[Move 中准备](move-in-ready.md)。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="bf6b1-132">一些所需的程序集</span><span class="sxs-lookup"><span data-stu-id="bf6b1-132">Some assembly required</span></span>

<span data-ttu-id="bf6b1-133">使用作为起点与其他配置存储解决方案或编码的自定义调整现有的服务。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="bf6b1-134">Azure 内容交付网络</span><span class="sxs-lookup"><span data-stu-id="bf6b1-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="bf6b1-135">Azure 媒体服务</span><span class="sxs-lookup"><span data-stu-id="bf6b1-135">Azure Media Services</span></span>
    
- <span data-ttu-id="bf6b1-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="bf6b1-136">HdInsight</span></span>
    
- <span data-ttu-id="bf6b1-137">Azure Redis 缓存</span><span class="sxs-lookup"><span data-stu-id="bf6b1-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="bf6b1-138">Azure SQL 数据库</span><span class="sxs-lookup"><span data-stu-id="bf6b1-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="bf6b1-139">在 Azure 虚拟机上的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="bf6b1-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="bf6b1-140">Azure 宇宙 DB</span><span class="sxs-lookup"><span data-stu-id="bf6b1-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="bf6b1-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="bf6b1-141">StorSimple</span></span>
    
- <span data-ttu-id="bf6b1-142">Azure SQL 数据仓库</span><span class="sxs-lookup"><span data-stu-id="bf6b1-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="bf6b1-143">Azure 数据湖泊存储区</span><span class="sxs-lookup"><span data-stu-id="bf6b1-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="bf6b1-144">每个云存储选项的详细信息，请参阅[所需的某些程序集](some-assembly-required.md)。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="bf6b1-145">从零开始构建</span><span class="sxs-lookup"><span data-stu-id="bf6b1-145">Build from the ground up</span></span>

<span data-ttu-id="bf6b1-146">存储这些构建基块，编码，以及用于从头开始创建您自己的存储解决方案或应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="bf6b1-147">Azure 存储 （文件）</span><span class="sxs-lookup"><span data-stu-id="bf6b1-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="bf6b1-148">Azure 存储 (blob)</span><span class="sxs-lookup"><span data-stu-id="bf6b1-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="bf6b1-149">Azure 存储 （队列）</span><span class="sxs-lookup"><span data-stu-id="bf6b1-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="bf6b1-150">Azure 存储 （表）</span><span class="sxs-lookup"><span data-stu-id="bf6b1-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="bf6b1-151">有关每个云存储选项的详细信息，请参阅[从头开始安装](build-from-the-ground-up.md)。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="bf6b1-152">密钥存储方案</span><span class="sxs-lookup"><span data-stu-id="bf6b1-152">Key storage scenarios</span></span>

<span data-ttu-id="bf6b1-153">下面是需要基于云的存储的主要方案：</span><span class="sxs-lookup"><span data-stu-id="bf6b1-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="bf6b1-154">缓存数据</span><span class="sxs-lookup"><span data-stu-id="bf6b1-154">Cache data</span></span>
    
    <span data-ttu-id="bf6b1-155">通过将其存储在高速缓存中访问速度到常用数据。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="bf6b1-156">与团队成员协作</span><span class="sxs-lookup"><span data-stu-id="bf6b1-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="bf6b1-157">为多个用户允许云存储中的数据访问授予权限。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="bf6b1-158">管理数据</span><span class="sxs-lookup"><span data-stu-id="bf6b1-158">Manage data</span></span>
    
    <span data-ttu-id="bf6b1-159">存储、 移动或删除内部或外部批量数据。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="bf6b1-160">管理源代码的步骤</span><span class="sxs-lookup"><span data-stu-id="bf6b1-160">Manage source code</span></span>
    
    <span data-ttu-id="bf6b1-161">上载、 协作和云中的运行应用程序代码文件。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="bf6b1-162">备份文件</span><span class="sxs-lookup"><span data-stu-id="bf6b1-162">Backup files</span></span>
    
    <span data-ttu-id="bf6b1-163">在多个云位置中存储内部或外部数据的非现场的副本。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="bf6b1-164">发布公司通信</span><span class="sxs-lookup"><span data-stu-id="bf6b1-164">Publish company communications</span></span>
    
    <span data-ttu-id="bf6b1-165">创建单个内部或外部的邮件的出版物的点。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="bf6b1-166">分发数百万事件</span><span class="sxs-lookup"><span data-stu-id="bf6b1-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="bf6b1-167">从网站、 应用程序和设备中创建遥测引入的存储。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="bf6b1-168">管理/服务视频</span><span class="sxs-lookup"><span data-stu-id="bf6b1-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="bf6b1-169">存储和向客户或组织用户提供视频内容。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="bf6b1-170">后续步骤</span><span class="sxs-lookup"><span data-stu-id="bf6b1-170">Next step</span></span>

<span data-ttu-id="bf6b1-171">查看[移入准备](move-in-ready.md)云存储选项。</span><span class="sxs-lookup"><span data-stu-id="bf6b1-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bf6b1-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf6b1-172">See Also</span></span>

[<span data-ttu-id="bf6b1-173">面向企业架构师的 Microsoft 云存储</span><span class="sxs-lookup"><span data-stu-id="bf6b1-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="bf6b1-174">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="bf6b1-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="bf6b1-175">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="bf6b1-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


