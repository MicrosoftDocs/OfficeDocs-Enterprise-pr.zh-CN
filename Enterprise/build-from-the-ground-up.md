---
title: 从零开始构建
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
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: 摘要： 获取对云组的详细信息可用于创建您自己的存储服务或解决方案的存储构建基块。
ms.openlocfilehash: 8ef5d7a99c4e82d9a4fc3eb281a4af505887b792
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915677"
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="8e846-103">从零开始构建</span><span class="sxs-lookup"><span data-stu-id="8e846-103">Build from the ground up</span></span>

 <span data-ttu-id="8e846-104">**摘要：** 获取一组由云的详细信息可用于创建您自己的存储服务或解决方案的存储构建基块。</span><span class="sxs-lookup"><span data-stu-id="8e846-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="8e846-105">"从头开始"存储解决方案：</span><span class="sxs-lookup"><span data-stu-id="8e846-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="8e846-106">允许您从头开始创建您自己的存储解决方案。</span><span class="sxs-lookup"><span data-stu-id="8e846-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="8e846-107">需要在使用 REST Api 的编程。</span><span class="sxs-lookup"><span data-stu-id="8e846-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="8e846-108">提供最佳的自定义和灵活性。</span><span class="sxs-lookup"><span data-stu-id="8e846-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="8e846-109">以下各节介绍了每个"从头开始"的存储选项的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8e846-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="8e846-110">Azure 存储 （文件）</span><span class="sxs-lookup"><span data-stu-id="8e846-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="8e846-111">功能</span><span class="sxs-lookup"><span data-stu-id="8e846-111">Features</span></span>

- <span data-ttu-id="8e846-112">可更轻松地移动到云的旧应用程序</span><span class="sxs-lookup"><span data-stu-id="8e846-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="8e846-113">首选的新应用程序的 blob 存储</span><span class="sxs-lookup"><span data-stu-id="8e846-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="8e846-114">可以从 Azure 虚拟机装入</span><span class="sxs-lookup"><span data-stu-id="8e846-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="8e846-115">可以安装在本地与 SMB 3.0</span><span class="sxs-lookup"><span data-stu-id="8e846-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="8e846-116">适用于 Linux 和 Windows</span><span class="sxs-lookup"><span data-stu-id="8e846-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="8e846-117">不支持 Azure 基于 AD 的身份验证或 Acl （Azure 存储帐户关键字提供身份验证和授权的访问的文件共享）</span><span class="sxs-lookup"><span data-stu-id="8e846-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="8e846-118">常见用途</span><span class="sxs-lookup"><span data-stu-id="8e846-118">Common uses</span></span>

- <span data-ttu-id="8e846-119">迁移到云中的旧版应用程序依赖文件共享</span><span class="sxs-lookup"><span data-stu-id="8e846-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="8e846-120">共享开发和测试工具</span><span class="sxs-lookup"><span data-stu-id="8e846-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="8e846-121">分布式应用程序可以存储日志，诊断数据和崩溃转储</span><span class="sxs-lookup"><span data-stu-id="8e846-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="8e846-122">密钥存储方案</span><span class="sxs-lookup"><span data-stu-id="8e846-122">Key storage scenarios</span></span>

- <span data-ttu-id="8e846-123">备份文件</span><span class="sxs-lookup"><span data-stu-id="8e846-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="8e846-124">资源</span><span class="sxs-lookup"><span data-stu-id="8e846-124">Resources</span></span>

<span data-ttu-id="8e846-125">其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dn166972.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8e846-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="8e846-126">成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="8e846-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="8e846-127">Azure 存储 (blob)</span><span class="sxs-lookup"><span data-stu-id="8e846-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="8e846-128">功能</span><span class="sxs-lookup"><span data-stu-id="8e846-128">Features</span></span>

- <span data-ttu-id="8e846-129">每个存储帐户可以保留达 500 TB （有一个订阅可以有多个存储帐户）</span><span class="sxs-lookup"><span data-stu-id="8e846-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="8e846-130">存储帐户组织到容器中，这可以应用于它们的安全，并且可以包含 blob</span><span class="sxs-lookup"><span data-stu-id="8e846-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="8e846-131">阻止 blob 优化的流式传输和存储云对象的大小为 200 GB</span><span class="sxs-lookup"><span data-stu-id="8e846-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="8e846-132">代表 PaaS 磁盘的优化页面 blob 和支持随机写入达 1 TB 的大小</span><span class="sxs-lookup"><span data-stu-id="8e846-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="8e846-133">追加针对优化 blob 追加操作，为 195 GB</span><span class="sxs-lookup"><span data-stu-id="8e846-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="8e846-134">Premium 存储提供通过 SSD 存储的速度更快 IOPS</span><span class="sxs-lookup"><span data-stu-id="8e846-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="8e846-135">常见用途</span><span class="sxs-lookup"><span data-stu-id="8e846-135">Common uses</span></span>

- <span data-ttu-id="8e846-136">文件、 计算机、 数据库和设备图像和文本的 web 应用程序的备份</span><span class="sxs-lookup"><span data-stu-id="8e846-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="8e846-137">云应用程序的配置数据</span><span class="sxs-lookup"><span data-stu-id="8e846-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="8e846-138">大数据，如日志和其他大型数据集</span><span class="sxs-lookup"><span data-stu-id="8e846-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="8e846-139">Azure 使用 blob 存储其自己的服务，例如 HDInsight 和虚拟机的磁盘</span><span class="sxs-lookup"><span data-stu-id="8e846-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="8e846-140">密钥存储方案</span><span class="sxs-lookup"><span data-stu-id="8e846-140">Key storage scenarios</span></span>

- <span data-ttu-id="8e846-141">管理数据</span><span class="sxs-lookup"><span data-stu-id="8e846-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="8e846-142">资源</span><span class="sxs-lookup"><span data-stu-id="8e846-142">Resources</span></span>

<span data-ttu-id="8e846-143">其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179376.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8e846-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="8e846-144">成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="8e846-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="8e846-145">Azure 存储 （队列）</span><span class="sxs-lookup"><span data-stu-id="8e846-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="8e846-146">功能</span><span class="sxs-lookup"><span data-stu-id="8e846-146">Features</span></span>

- <span data-ttu-id="8e846-147">存储帐户可以包含任意数量的队列</span><span class="sxs-lookup"><span data-stu-id="8e846-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="8e846-148">队列可包含任意数量的邮件 （直到存储帐户已满）</span><span class="sxs-lookup"><span data-stu-id="8e846-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="8e846-149">队列消息被自动七天后删除如果未检索并删除应用程序</span><span class="sxs-lookup"><span data-stu-id="8e846-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="8e846-150">邮件可能最多为 64 KB 的大小</span><span class="sxs-lookup"><span data-stu-id="8e846-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="8e846-151">安全帐户存储级别</span><span class="sxs-lookup"><span data-stu-id="8e846-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="8e846-152">队列旨在传递控制消息，而不是原始数据</span><span class="sxs-lookup"><span data-stu-id="8e846-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="8e846-153">常见用途</span><span class="sxs-lookup"><span data-stu-id="8e846-153">Common uses</span></span>

- <span data-ttu-id="8e846-154">创建工作积压以异步处理</span><span class="sxs-lookup"><span data-stu-id="8e846-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="8e846-155">处理日志消息</span><span class="sxs-lookup"><span data-stu-id="8e846-155">Processing log messages</span></span>
    
- <span data-ttu-id="8e846-156">使应用程序分离</span><span class="sxs-lookup"><span data-stu-id="8e846-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="8e846-157">密钥存储方案</span><span class="sxs-lookup"><span data-stu-id="8e846-157">Key storage scenarios</span></span>

- <span data-ttu-id="8e846-158">分发事件</span><span class="sxs-lookup"><span data-stu-id="8e846-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="8e846-159">资源</span><span class="sxs-lookup"><span data-stu-id="8e846-159">Resources</span></span>

<span data-ttu-id="8e846-160">其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179353.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8e846-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="8e846-161">成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="8e846-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="8e846-162">Azure 存储 （表）</span><span class="sxs-lookup"><span data-stu-id="8e846-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="8e846-163">功能</span><span class="sxs-lookup"><span data-stu-id="8e846-163">Features</span></span>

- <span data-ttu-id="8e846-164">最适合半结构化数据集</span><span class="sxs-lookup"><span data-stu-id="8e846-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="8e846-165">通常低于传统的 SQL 成本</span><span class="sxs-lookup"><span data-stu-id="8e846-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="8e846-166">如果查询对于键，如果查询值降低非常快</span><span class="sxs-lookup"><span data-stu-id="8e846-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="8e846-167">高度可伸缩;任意数量的最多的存储帐户限制表</span><span class="sxs-lookup"><span data-stu-id="8e846-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="8e846-168">可通过 REST API，有限的 oData 协议，.NET 访问</span><span class="sxs-lookup"><span data-stu-id="8e846-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="8e846-169">必须序列化值</span><span class="sxs-lookup"><span data-stu-id="8e846-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="8e846-170">常见用途</span><span class="sxs-lookup"><span data-stu-id="8e846-170">Common uses</span></span>

- <span data-ttu-id="8e846-171">Web 应用程序的的用户数据</span><span class="sxs-lookup"><span data-stu-id="8e846-171">User data for web applications</span></span>
    
- <span data-ttu-id="8e846-172">通讯簿</span><span class="sxs-lookup"><span data-stu-id="8e846-172">Address books</span></span>
    
- <span data-ttu-id="8e846-173">设备信息</span><span class="sxs-lookup"><span data-stu-id="8e846-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="8e846-174">密钥存储方案</span><span class="sxs-lookup"><span data-stu-id="8e846-174">Key storage scenarios</span></span>

- <span data-ttu-id="8e846-175">管理数据</span><span class="sxs-lookup"><span data-stu-id="8e846-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="8e846-176">资源</span><span class="sxs-lookup"><span data-stu-id="8e846-176">Resources</span></span>

<span data-ttu-id="8e846-177">其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179463.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8e846-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="8e846-178">成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="8e846-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="8e846-179">Microsoft Azure 存储建议</span><span class="sxs-lookup"><span data-stu-id="8e846-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="8e846-180">在设计与 Azure 存储自定义存储解决方案时，请牢记以下事项：</span><span class="sxs-lookup"><span data-stu-id="8e846-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="8e846-181">利用多个存储帐户更大的可伸缩性，为增加大小 (> 100 TB) 或更大的吞吐量 （每秒 > 5,000 个操作）。</span><span class="sxs-lookup"><span data-stu-id="8e846-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="8e846-182">设计添加其他存储帐户作为配置更改，而不是代码变更的能力。</span><span class="sxs-lookup"><span data-stu-id="8e846-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="8e846-183">请仔细选择表存储，以实现所需的比例插入和查询性能方面的分区函数。</span><span class="sxs-lookup"><span data-stu-id="8e846-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="8e846-184">选择表属性作为元数据 （属性名称） 的简短的列名称是存储的带内 （的列名称进行计数达到最大行大小为 1 MB）。</span><span class="sxs-lookup"><span data-stu-id="8e846-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="8e846-185">如果可能，批处理存储到的操作。</span><span class="sxs-lookup"><span data-stu-id="8e846-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="8e846-186">主动缓存到分布式缓存的配置数据库中的信息。</span><span class="sxs-lookup"><span data-stu-id="8e846-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="8e846-187">如果依赖于在缓存中无可用的数据的某些一段应用程序的性能和可靠性，您的应用程序应拒绝的传入请求，直到缓存预填充。</span><span class="sxs-lookup"><span data-stu-id="8e846-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="8e846-188">分区的数据在垂直方向 （通过表） 或水平 （跨多个 shards 段表） 以跨多个数据库负载。</span><span class="sxs-lookup"><span data-stu-id="8e846-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="8e846-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e846-189">See Also</span></span>

[<span data-ttu-id="8e846-190">面向企业架构师的 Microsoft 云存储</span><span class="sxs-lookup"><span data-stu-id="8e846-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="8e846-191">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="8e846-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="8e846-192">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="8e846-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



