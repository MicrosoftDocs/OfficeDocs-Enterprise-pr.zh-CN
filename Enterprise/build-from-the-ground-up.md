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
# <a name="build-from-the-ground-up"></a>从零开始构建

 **摘要：** 获取一组由云的详细信息可用于创建您自己的存储服务或解决方案的存储构建基块。
  
"从头开始"存储解决方案：
  
- 允许您从头开始创建您自己的存储解决方案。 
    
- 需要在使用 REST Api 的编程。
    
- 提供最佳的自定义和灵活性。
    
以下各节介绍了每个"从头开始"的存储选项的详细信息。
  
## <a name="azure-storage-files"></a>Azure 存储 （文件）

### <a name="features"></a>功能

- 可更轻松地移动到云的旧应用程序
    
- 首选的新应用程序的 blob 存储
    
- 可以从 Azure 虚拟机装入
    
- 可以安装在本地与 SMB 3.0
    
- 适用于 Linux 和 Windows
    
- 不支持 Azure 基于 AD 的身份验证或 Acl （Azure 存储帐户关键字提供身份验证和授权的访问的文件共享）
    
### <a name="common-uses"></a>常见用途

- 迁移到云中的旧版应用程序依赖文件共享
    
- 共享开发和测试工具
    
- 分布式应用程序可以存储日志，诊断数据和崩溃转储
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 备份文件
    
### <a name="resources"></a>资源

其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dn166972.aspx)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="azure-storage-blobs"></a>Azure 存储 (blob)

### <a name="features"></a>功能

- 每个存储帐户可以保留达 500 TB （有一个订阅可以有多个存储帐户）
    
- 存储帐户组织到容器中，这可以应用于它们的安全，并且可以包含 blob
    
- 阻止 blob 优化的流式传输和存储云对象的大小为 200 GB
    
- 代表 PaaS 磁盘的优化页面 blob 和支持随机写入达 1 TB 的大小
    
- 追加针对优化 blob 追加操作，为 195 GB
    
- Premium 存储提供通过 SSD 存储的速度更快 IOPS
    
### <a name="common-uses"></a>常见用途

- 文件、 计算机、 数据库和设备图像和文本的 web 应用程序的备份
    
- 云应用程序的配置数据
    
- 大数据，如日志和其他大型数据集
    
- Azure 使用 blob 存储其自己的服务，例如 HDInsight 和虚拟机的磁盘
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179376.aspx)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="azure-storage-queues"></a>Azure 存储 （队列）

### <a name="features"></a>功能

- 存储帐户可以包含任意数量的队列
    
- 队列可包含任意数量的邮件 （直到存储帐户已满）
    
- 队列消息被自动七天后删除如果未检索并删除应用程序
    
- 邮件可能最多为 64 KB 的大小
    
- 安全帐户存储级别
    
- 队列旨在传递控制消息，而不是原始数据
    
### <a name="common-uses"></a>常见用途

- 创建工作积压以异步处理
    
- 处理日志消息
    
- 使应用程序分离
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 分发事件
    
### <a name="resources"></a>资源

其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179353.aspx)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="azure-storage-tables"></a>Azure 存储 （表）

### <a name="features"></a>功能

- 最适合半结构化数据集
    
- 通常低于传统的 SQL 成本
    
- 如果查询对于键，如果查询值降低非常快
    
- 高度可伸缩;任意数量的最多的存储帐户限制表
    
- 可通过 REST API，有限的 oData 协议，.NET 访问
    
- 必须序列化值
    
### <a name="common-uses"></a>常见用途

- Web 应用程序的的用户数据
    
- 通讯簿
    
- 设备信息
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

其他信息，请单击[此处](https://msdn.microsoft.com/library/azure/dd179463.aspx)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="microsoft-azure-storage-recommendations"></a>Microsoft Azure 存储建议

在设计与 Azure 存储自定义存储解决方案时，请牢记以下事项：
  
- 利用多个存储帐户更大的可伸缩性，为增加大小 (> 100 TB) 或更大的吞吐量 （每秒 > 5,000 个操作）。
    
- 设计添加其他存储帐户作为配置更改，而不是代码变更的能力。
    
- 请仔细选择表存储，以实现所需的比例插入和查询性能方面的分区函数。
    
- 选择表属性作为元数据 （属性名称） 的简短的列名称是存储的带内 （的列名称进行计数达到最大行大小为 1 MB）。
    
- 如果可能，批处理存储到的操作。
    
- 主动缓存到分布式缓存的配置数据库中的信息。
    
- 如果依赖于在缓存中无可用的数据的某些一段应用程序的性能和可靠性，您的应用程序应拒绝的传入请求，直到缓存预填充。
    
- 分区的数据在垂直方向 （通过表） 或水平 （跨多个 shards 段表） 以跨多个数据库负载。
    
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 云存储](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



