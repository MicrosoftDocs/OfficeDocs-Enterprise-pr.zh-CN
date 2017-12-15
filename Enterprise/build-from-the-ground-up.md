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
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "摘要： 获取详细信息集的云存储，可用于创建您自己的存储服务或解决方案的构建基块。"
ms.openlocfilehash: 18aa8cb7fa0dda05302a88487dcc69bdbcb174d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="build-from-the-ground-up"></a>从零开始构建

 **摘要：**获取详细信息集的云存储，可用于创建您自己的存储服务或解决方案的构建基块。
  
"生成从零开始"的存储解决方案：
  
- 允许您从头开始创建您自己的存储解决方案。 
    
- 需要在使用 REST Api 的编程。
    
- 提供最佳的自定义功能和灵活性。
    
以下各节描述了每个"从头生成"存储选项的详细信息。
  
## <a name="azure-storage-files"></a>Azure 存储 （文件）

### <a name="features"></a>功能

- 便于更方便地移动到云的旧式应用程序
    
- 新的应用程序首选的 blob 存储
    
- 可以装载从 Azure 的虚拟机
    
- 可以装载内部使用 SMB 3.0
    
- 与 Linux 和 Windows 的工作原理
    
- 不支持基于 AD 的 Azure 身份验证或 Acl （Azure 存储帐户密钥提供身份验证和授权的访问的文件共享）
    
### <a name="common-uses"></a>常见用途

- 迁移到云的旧式应用程序依赖于文件共享
    
- 共享开发和测试工具
    
- 分布式应用程序可以存储日志，诊断数据，并崩溃转储
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 备份文件
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dn166972.aspx)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="azure-storage-blobs"></a>Azure 存储 (blob)

### <a name="features"></a>功能

- 每个存储帐户可以容纳多达 500 TB （一个订阅可以有多个存储帐户）
    
- 帐户存储被组织成容器，其中可以具有应用于它们的安全性，可以包含 blob
    
- 块 blob 则适合流式传输和存储云对象达 200GB 的大小
    
- 适合页面 blob 表示 PaaS 磁盘并支持随机写入，达 1TB 的大小
    
- 追加 blob 则适合追加操作，达 195 GB
    
- 高级存储提供了更快通过 SSD 存储 IOPS
    
### <a name="common-uses"></a>常见用途

- 备份的文件、 计算机、 数据库和设备的图像和文本的 web 应用程序
    
- 云应用程序的配置数据
    
- 大数据，例如，日志和其他大型的数据集
    
- Azure 使用 blob 为自己服务，如 HDInsight 和虚拟机的磁盘存储
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179376.aspx)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="azure-storage-queues"></a>Azure 存储 （队列）

### <a name="features"></a>功能

- 存储帐户可以包含任意数量的队列
    
- 队列可以包含任意数量的消息 （直到存储帐户已满）
    
- 队列消息是自动在七天后删除如果不检索和删除应用程序
    
- 消息可能会多达 64 KB 的大小
    
- 在存储帐户级别安全
    
- 旨在传递控制消息，不是原始数据的队列
    
### <a name="common-uses"></a>常见用途

- 创建异步处理的工作的积压
    
- 处理日志消息
    
- 将应用程序中分离出来
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 分发的事件
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179353.aspx)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="azure-storage-tables"></a>Azure 存储 （表）

### <a name="features"></a>功能

- 最适合于半结构化数据集
    
- 通常更低的成本比传统的 SQL
    
- 如果查询键，如果查询值降低速度非常快
    
- 可以扩展;任意数量的表的存储帐户的限制
    
- 通过 REST API，有限的 oData 协议，.NET 访问
    
- 必须进行序列化的值
    
### <a name="common-uses"></a>常见用途

- 对于 web 应用程序的用户数据
    
- 通讯簿
    
- 设备信息
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179463.aspx)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="microsoft-azure-storage-recommendations"></a>Microsoft Azure 存储建议

在设计使用 Azure 存储您定制的存储解决方案时，请牢记以下：
  
- 利用更大的可扩展性，为增加大小 (> 100 TB) 或更大的吞吐量 （每秒 5000 > 操作） 的多个存储的帐户。
    
- 设计用于添加更多存储帐户作为配置的更改，而不是代码更改的能力。
    
- 请仔细选择表存储，以实现所需的比例，在插入和查询性能方面的分区函数。
    
- 选择短的列名的表的元数据 （属性名称） 的属性存储在带内 （列名称也计入 1 MB 的最大行大小之前）。
    
- 在可能的情况下，批处理存储操作。
    
- 主动缓存到分布式缓存配置数据库中的信息。
    
- 如果应用程序的性能或可靠性取决于某些段可用的数据缓存中时，您的应用程序应预先填充缓存之前拒绝传入的请求。
    
- 分区的数据在垂直方向 （按表） 或横向 （跨多个 shards 线段表） 来跨多个数据库的负载。
    
## <a name="see-also"></a>See Also

[企业架构师的 Microsoft 云存储](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



