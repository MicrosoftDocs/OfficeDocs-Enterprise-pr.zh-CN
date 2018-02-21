---
title: "从零开始构建"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "摘要： 获取详细信息集的云存储，可用于创建您自己的存储服务或解决方案的构建基块。"
ms.openlocfilehash: be7ea3e7526115f1a983ec89f2afeb5d130daee1
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="df35c-103">从零开始构建</span><span class="sxs-lookup"><span data-stu-id="df35c-103">Build from the ground up</span></span>

 <span data-ttu-id="df35c-104">**摘要：**获取详细信息集的云存储，可用于创建您自己的存储服务或解决方案的构建基块。</span><span class="sxs-lookup"><span data-stu-id="df35c-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="df35c-105">"生成从零开始"的存储解决方案：</span><span class="sxs-lookup"><span data-stu-id="df35c-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="df35c-106">允许您从头开始创建您自己的存储解决方案。</span><span class="sxs-lookup"><span data-stu-id="df35c-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="df35c-107">需要在使用 REST Api 的编程。</span><span class="sxs-lookup"><span data-stu-id="df35c-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="df35c-108">提供最佳的自定义功能和灵活性。</span><span class="sxs-lookup"><span data-stu-id="df35c-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="df35c-109">以下各节描述了每个"从头生成"存储选项的详细信息。</span><span class="sxs-lookup"><span data-stu-id="df35c-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="df35c-110">Azure 存储 （文件）</span><span class="sxs-lookup"><span data-stu-id="df35c-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="df35c-111">功能</span><span class="sxs-lookup"><span data-stu-id="df35c-111">Features</span></span>

- <span data-ttu-id="df35c-112">便于更方便地移动到云的旧式应用程序</span><span class="sxs-lookup"><span data-stu-id="df35c-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="df35c-113">新的应用程序首选的 blob 存储</span><span class="sxs-lookup"><span data-stu-id="df35c-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="df35c-114">可以装载从 Azure 的虚拟机</span><span class="sxs-lookup"><span data-stu-id="df35c-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="df35c-115">可以装载内部使用 SMB 3.0</span><span class="sxs-lookup"><span data-stu-id="df35c-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="df35c-116">与 Linux 和 Windows 的工作原理</span><span class="sxs-lookup"><span data-stu-id="df35c-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="df35c-117">不支持基于 AD 的 Azure 身份验证或 Acl （Azure 存储帐户密钥提供身份验证和授权的访问的文件共享）</span><span class="sxs-lookup"><span data-stu-id="df35c-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="df35c-118">常见用途</span><span class="sxs-lookup"><span data-stu-id="df35c-118">Common uses</span></span>

- <span data-ttu-id="df35c-119">迁移到云的旧式应用程序依赖于文件共享</span><span class="sxs-lookup"><span data-stu-id="df35c-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="df35c-120">共享开发和测试工具</span><span class="sxs-lookup"><span data-stu-id="df35c-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="df35c-121">分布式应用程序可以存储日志，诊断数据，并崩溃转储</span><span class="sxs-lookup"><span data-stu-id="df35c-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="df35c-122">密钥存储方案</span><span class="sxs-lookup"><span data-stu-id="df35c-122">Key storage scenarios</span></span>

- <span data-ttu-id="df35c-123">备份文件</span><span class="sxs-lookup"><span data-stu-id="df35c-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="df35c-124">资源</span><span class="sxs-lookup"><span data-stu-id="df35c-124">Resources</span></span>

<span data-ttu-id="df35c-125">有关其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dn166972.aspx)。</span><span class="sxs-lookup"><span data-stu-id="df35c-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="df35c-126">成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="df35c-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="df35c-127">Azure 存储 (blob)</span><span class="sxs-lookup"><span data-stu-id="df35c-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="df35c-128">功能</span><span class="sxs-lookup"><span data-stu-id="df35c-128">Features</span></span>

- <span data-ttu-id="df35c-129">每个存储帐户可以容纳多达 500 TB （一个订阅可以有多个存储帐户）</span><span class="sxs-lookup"><span data-stu-id="df35c-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="df35c-130">帐户存储被组织成容器，其中可以具有应用于它们的安全性，可以包含 blob</span><span class="sxs-lookup"><span data-stu-id="df35c-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="df35c-131">块 blob 则适合流式传输和存储云对象达 200GB 的大小</span><span class="sxs-lookup"><span data-stu-id="df35c-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="df35c-132">适合页面 blob 表示 PaaS 磁盘并支持随机写入，达 1TB 的大小</span><span class="sxs-lookup"><span data-stu-id="df35c-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="df35c-133">追加 blob 则适合追加操作，达 195 GB</span><span class="sxs-lookup"><span data-stu-id="df35c-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="df35c-134">高级存储提供了更快通过 SSD 存储 IOPS</span><span class="sxs-lookup"><span data-stu-id="df35c-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="df35c-135">常见用途</span><span class="sxs-lookup"><span data-stu-id="df35c-135">Common uses</span></span>

- <span data-ttu-id="df35c-136">备份的文件、 计算机、 数据库和设备的图像和文本的 web 应用程序</span><span class="sxs-lookup"><span data-stu-id="df35c-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="df35c-137">云应用程序的配置数据</span><span class="sxs-lookup"><span data-stu-id="df35c-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="df35c-138">大数据，例如，日志和其他大型的数据集</span><span class="sxs-lookup"><span data-stu-id="df35c-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="df35c-139">Azure 使用 blob 为自己服务，如 HDInsight 和虚拟机的磁盘存储</span><span class="sxs-lookup"><span data-stu-id="df35c-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="df35c-140">密钥存储方案</span><span class="sxs-lookup"><span data-stu-id="df35c-140">Key storage scenarios</span></span>

- <span data-ttu-id="df35c-141">管理数据</span><span class="sxs-lookup"><span data-stu-id="df35c-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="df35c-142">资源</span><span class="sxs-lookup"><span data-stu-id="df35c-142">Resources</span></span>

<span data-ttu-id="df35c-143">有关其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179376.aspx)。</span><span class="sxs-lookup"><span data-stu-id="df35c-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="df35c-144">成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="df35c-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="df35c-145">Azure 存储 （队列）</span><span class="sxs-lookup"><span data-stu-id="df35c-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="df35c-146">功能</span><span class="sxs-lookup"><span data-stu-id="df35c-146">Features</span></span>

- <span data-ttu-id="df35c-147">存储帐户可以包含任意数量的队列</span><span class="sxs-lookup"><span data-stu-id="df35c-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="df35c-148">队列可以包含任意数量的消息 （直到存储帐户已满）</span><span class="sxs-lookup"><span data-stu-id="df35c-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="df35c-149">队列消息是自动在七天后删除如果不检索和删除应用程序</span><span class="sxs-lookup"><span data-stu-id="df35c-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="df35c-150">消息可能会多达 64 KB 的大小</span><span class="sxs-lookup"><span data-stu-id="df35c-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="df35c-151">在存储帐户级别安全</span><span class="sxs-lookup"><span data-stu-id="df35c-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="df35c-152">旨在传递控制消息，不是原始数据的队列</span><span class="sxs-lookup"><span data-stu-id="df35c-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="df35c-153">常见用途</span><span class="sxs-lookup"><span data-stu-id="df35c-153">Common uses</span></span>

- <span data-ttu-id="df35c-154">创建异步处理的工作的积压</span><span class="sxs-lookup"><span data-stu-id="df35c-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="df35c-155">处理日志消息</span><span class="sxs-lookup"><span data-stu-id="df35c-155">Processing log messages</span></span>
    
- <span data-ttu-id="df35c-156">将应用程序中分离出来</span><span class="sxs-lookup"><span data-stu-id="df35c-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="df35c-157">密钥存储方案</span><span class="sxs-lookup"><span data-stu-id="df35c-157">Key storage scenarios</span></span>

- <span data-ttu-id="df35c-158">分发的事件</span><span class="sxs-lookup"><span data-stu-id="df35c-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="df35c-159">资源</span><span class="sxs-lookup"><span data-stu-id="df35c-159">Resources</span></span>

<span data-ttu-id="df35c-160">有关其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179353.aspx)。</span><span class="sxs-lookup"><span data-stu-id="df35c-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="df35c-161">成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="df35c-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="df35c-162">Azure 存储 （表）</span><span class="sxs-lookup"><span data-stu-id="df35c-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="df35c-163">功能</span><span class="sxs-lookup"><span data-stu-id="df35c-163">Features</span></span>

- <span data-ttu-id="df35c-164">最适合于半结构化数据集</span><span class="sxs-lookup"><span data-stu-id="df35c-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="df35c-165">通常更低的成本比传统的 SQL</span><span class="sxs-lookup"><span data-stu-id="df35c-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="df35c-166">如果查询键，如果查询值降低速度非常快</span><span class="sxs-lookup"><span data-stu-id="df35c-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="df35c-167">可以扩展;任意数量的表的存储帐户的限制</span><span class="sxs-lookup"><span data-stu-id="df35c-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="df35c-168">通过 REST API，有限的 oData 协议，.NET 访问</span><span class="sxs-lookup"><span data-stu-id="df35c-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="df35c-169">必须进行序列化的值</span><span class="sxs-lookup"><span data-stu-id="df35c-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="df35c-170">常见用途</span><span class="sxs-lookup"><span data-stu-id="df35c-170">Common uses</span></span>

- <span data-ttu-id="df35c-171">对于 web 应用程序的用户数据</span><span class="sxs-lookup"><span data-stu-id="df35c-171">User data for web applications</span></span>
    
- <span data-ttu-id="df35c-172">通讯簿</span><span class="sxs-lookup"><span data-stu-id="df35c-172">Address books</span></span>
    
- <span data-ttu-id="df35c-173">设备信息</span><span class="sxs-lookup"><span data-stu-id="df35c-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="df35c-174">密钥存储方案</span><span class="sxs-lookup"><span data-stu-id="df35c-174">Key storage scenarios</span></span>

- <span data-ttu-id="df35c-175">管理数据</span><span class="sxs-lookup"><span data-stu-id="df35c-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="df35c-176">资源</span><span class="sxs-lookup"><span data-stu-id="df35c-176">Resources</span></span>

<span data-ttu-id="df35c-177">有关其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179463.aspx)。</span><span class="sxs-lookup"><span data-stu-id="df35c-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="df35c-178">成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="df35c-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="df35c-179">Microsoft Azure 存储建议</span><span class="sxs-lookup"><span data-stu-id="df35c-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="df35c-180">在设计使用 Azure 存储您定制的存储解决方案时，请牢记以下：</span><span class="sxs-lookup"><span data-stu-id="df35c-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="df35c-181">利用更大的可扩展性，为增加大小 (> 100 TB) 或更大的吞吐量 （每秒 5000 > 操作） 的多个存储的帐户。</span><span class="sxs-lookup"><span data-stu-id="df35c-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="df35c-182">设计用于添加更多存储帐户作为配置的更改，而不是代码更改的能力。</span><span class="sxs-lookup"><span data-stu-id="df35c-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="df35c-183">请仔细选择表存储，以实现所需的比例，在插入和查询性能方面的分区函数。</span><span class="sxs-lookup"><span data-stu-id="df35c-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="df35c-184">选择短的列名的表的元数据 （属性名称） 的属性存储在带内 （列名称也计入 1 MB 的最大行大小之前）。</span><span class="sxs-lookup"><span data-stu-id="df35c-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="df35c-185">在可能的情况下，批处理存储操作。</span><span class="sxs-lookup"><span data-stu-id="df35c-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="df35c-186">主动缓存到分布式缓存配置数据库中的信息。</span><span class="sxs-lookup"><span data-stu-id="df35c-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="df35c-187">如果应用程序的性能或可靠性取决于某些段可用的数据缓存中时，您的应用程序应预先填充缓存之前拒绝传入的请求。</span><span class="sxs-lookup"><span data-stu-id="df35c-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="df35c-188">分区的数据在垂直方向 （按表） 或横向 （跨多个 shards 线段表） 来跨多个数据库的负载。</span><span class="sxs-lookup"><span data-stu-id="df35c-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="df35c-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df35c-189">See Also</span></span>

[<span data-ttu-id="df35c-190">面向企业架构师的 Microsoft 云存储</span><span class="sxs-lookup"><span data-stu-id="df35c-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="df35c-191">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="df35c-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="df35c-192">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="df35c-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



