---
title: "一些所需的程序集"
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
ms.assetid: ccf1b8b3-0d50-4c66-b314-f480245fad5e
description: "摘要： 获取组可用于创建定制的存储解决方案的云存储选项的详细信息。"
ms.openlocfilehash: bf6f7586b3a890cd25aba314e4892d5e2ac5bb34
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="some-assembly-required"></a>一些所需的程序集

 **摘要：**获取上的云组的详细信息可用于创建定制的存储解决方案的存储选项。
  
"某些程序集所需"的存储解决方案：
  
- 为您的存储解决方案作为起点使用现有的服务。
    
- 需要一些配置或编码。
    
- 可以自定义以满足您的需要。
    
以下各节描述了每个"某些程序集所需"的存储解决方案的详细信息。
  
## <a name="azure-content-delivery-network"></a>Azure 内容交付网络

### <a name="features"></a>功能

- 高级和实际时间的分析
    
- 可靠的安全性，防止 DDoS
    
- 获取内容自动从 Azure 网站或 Azure 云服务一旦设置集成
    
- Akamai 的新合作
    
- 可以处理通信量激增和繁重的负载
    
### <a name="common-uses"></a>常见用途

- 音频、 视频、 应用程序、 图像和其他文件速度更快、 更可靠地向客户分发使用是离他们最近的服务器
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
- 管理视频
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](https://azure.microsoft.com/services/cdn/)。
  
成本信息，请单击[此处](https://azure.microsoft.com/pricing/details/cdn/)。
  
## <a name="hdinsight"></a>HdInsight

### <a name="features"></a>功能

- Apache Hadoop 分发由云数据湖服务
    
- 扩展到 petabytes 即需即装
    
- 处理非结构化和半结构化数据在 Java、.NET，和更多的发展
    
- 跳过购买和维护硬件
    
- 使用云连接内部 Hadoop 群集
    
- 灵活地部署任意 Hadoop 项目通过自定义脚本 (例如 R Giraph，Solr)
    
### <a name="common-uses"></a>常见用途

- 数据分析工作负荷
    
- 内存中数据处理的框架，用于大数据 （触发）
    
- 实时流处理 （冲击）
    
- 大事务处理 (OLTP) 的非关系数据 (HBase)
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](https://azure.microsoft.com/services/hdinsight/)。
  
成本信息，请单击[此处](https://azure.microsoft.com/pricing/details/hdinsight/)。
  
## <a name="azure-sql-database"></a>Azure SQL 数据库

### <a name="features"></a>功能

- 优化以减少管理和成本
    
- 自动高可用性、 灾难恢复和升级
    
- 建议企业管理数百个或数千个 1 TB 大小的数据库
    
- 分片技术可以将数据拆分跨数据库的更高的存储
    
- 扩展数据库与 SQL Server 2016
    
### <a name="common-uses"></a>常见用途

- 新云设计应用程序使用关系数据
    
- 在示意性、 高度结构化的关系的数据集上的数据处理
    
- 空间数据或格式的数据类型
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="elastic-database"></a>弹性的数据库

几乎不受限制的资源的 SQL Azure 数据库时使用：
  
- 总数据量太大，无法适应单个数据库的约束。
    
- 整个工作负荷的事务吞吐量超过单个数据库的功能。
    
- 租户需要彼此，物理隔离，所以单独的数据库所需的每个租户。
    
- 一个数据库的不同部分需要驻留在不同的地理位置，为法规遵从性、 性能或地缘政治的原因。
    
垂直缩放，您可以更改 Azure 数据库性能级别/版或使用弹性数据库池。
  
![Azure SQL 数据库提供的垂直缩放比例。](images/Storage_Poster/CloudStor-VertScale.png)
  
水平缩放，您可以根据需要添加新的数据库。
  
![Azure SQL 数据库提供的水平缩放比例。](images/Storage_Poster/CloudStor-HorizScale.png)
  
单击[此处](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction)的详细信息。
  
### <a name="stretch-database-with-sql-server-2016"></a>使用 SQL Server 2016 的 Stretch Database

扩展数据库是 SQL Server 2016，可以透明地和安全地移动冷备用数据，如大表包含客户订单信息，到 Azure 中的 SQL 拉伸数据库中的已结束的业务数据的功能。拉伸，SQL Server 实例、 数据库或甚至单个表中的内容时，SQL Server 2016年服务器中的本地数据和远程数据在 Azure 中的组合。对于拉伸由 SQL Server 2016年自动移至 Azure 变得符合条件的数据。
  
![SQL Server 2016 中的 Stretch Database。](images/Storage_Poster/CloudStor-Stretch.png)
  
以透明方式将包含历史数据的用户查询转发到 Azure SQL Stretch Database。即使表已扩展，也无需重新写入这些查询。
  
Stretch Database 提供经济高效的选项，用于历史数据的长期存储和透明访问。它还解决了表变大时出现的性能和可用性问题。
  
单击[此处](https://msdn.microsoft.com/library/dn935011.aspx)的详细信息。
  
### <a name="resources"></a>资源

有关其他信息，请单击[此处](http://azure.microsoft.com/services/sql-database/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/sql-database/)。
  
## <a name="azure-cosmos-db"></a>Azure 宇宙 DB

### <a name="features"></a>功能

- 保证低延迟、 无限的、 弹性的比例，为存储和吞吐量达 99.99%的可用性 SLA
    
- 所有数据全局范围内都复制跨任意数量的区域与透明的故障切换和四个定义明确的一致性级别
    
- 自动索引您的所有数据，而无需架构或辅助索引
    
- 丰富的 SQL 和 JavaScript 的查询和多项事务
    
### <a name="common-uses"></a>常见用途

- IoT、 移动和社会
    
- 游戏
    
- 零售
    
- 内容管理
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="cosmos-db-vs-azure-tables-vs-azure-sql-database"></a>宇宙和 Azure 数据库表与 Azure SQL 数据库

宇宙 DB、 Azure 表存储和 SQL Azure 数据库的常用属性：
  
- 99.99 可用性 SLA
    
- 完全托管的数据库服务
    
- 通过 ISO 27001、 HIPAA 和符合欧盟模型子句
    
下表显示了 Azure 宇宙 DB、 Azure 表存储和 SQL Azure 数据库的常见属性。
  
![不常用属性：Cosmos DB 与Azure 表与Azure SQL 数据库](images/Storage_Poster/CloudStor-Table.png)
  
### <a name="resources"></a>资源

有关其他信息，请单击[此处](http://azure.microsoft.com/services/documentdb/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/documentdb/)。
  
## <a name="azure-media-services"></a>Azure 媒体服务

### <a name="features"></a>功能

- 实时和视频用比例的视频点播 (VOD) 交货
    
- 高可用编码和流式处理
    
- 支持快递、 iOS、 Android、 HTML5 和 Xbox
    
- Studio 认证 DRM 支持
    
- 蕴含丰富的内容
    
- 预集成的合作伙伴的广泛生态系统
    
### <a name="common-uses"></a>常见用途

- 编码、 存储和传输音频和视频在规模较大
    
- 实时流和 VOD
    
- 优化视频内容管理
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理视频
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](https://azure.microsoft.com/services/media-services/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/media-services/)。
  
## <a name="azure-redis-cache"></a>Azure 的 Redis 高速缓存

### <a name="features"></a>功能

- 安全、 专用 Redis 服务器的高可用性数据复制和由 Microsoft 管理的故障切换
    
- 建议用于需要高吞吐量的任何应用程序
    
- 可用大小达 530 GB 及以后 （包括津贴和自动分片）
    
- Redis 持久性仍然存在内存中缓存的数据到 Azure 存储
    
- Redis 群集，可以实现最大的规模和吞吐量
    
- 增强的安全性和网络隔离与 Azure 虚拟网络支持
    
### <a name="common-uses"></a>常见用途

- 在 Azure，如宇宙数据库和 SQL Azure 数据库中的任何存储服务中的数据的反向查找
    
- 从其他数据存储区的同步的内容
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 缓存数据
    
- 高吞吐量的应用程序的消息代理
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](http://azure.microsoft.com/services/cache/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/cache/)。
  
## <a name="sql-server-on-an-azure-vm"></a>SQL Server 在 Azure 的 VM

### <a name="features"></a>功能

- SQL Server 运行在 Azure 的虚拟机上安装的应用程序
    
- 使用库图像与 SQL Server 安装，或者让 SQL Server 许可证
    
### <a name="common-uses"></a>常见用途

- 管理应用程序的数据
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](http://azure.microsoft.com/services/virtual-machines/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/virtual-machines/)。
  
## <a name="storsimple"></a>StorSimple

### <a name="features"></a>功能

- 可扩展的企业混合 SAN 存储与 SSD 硬盘内部混合存储阵列中，与云存储解决方案的集成扩展
    
- 串联重复数据消除、 压缩、 自动分层，并加密非结构化和半结构化数据
    
- 自动化的异地数据保护使用云快照
    
- 有高效、 独立于位置的灾难恢复
    
- 企业数据与 StorSimple Azure 中的虚拟应用装置的数据移动
    
### <a name="common-uses"></a>常见用途

- 管理数据增长相关的文件共享、 档案和其他数据存储库
    
- 异地数据保护和灾难恢复的文件共享、 虚拟机、 SQL 和 SharePoint （使用远程 Blob 存储）
    
- 利用云快照克隆 Azure 中的数据，并增加业务灵活性
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
- 合作
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](http://azure.microsoft.com/services/storsimple/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storsimple/)。
  
## <a name="azure-sql-data-warehouse"></a>SQL azure 数据仓库

### <a name="features"></a>功能

- 可以扩展到多达 32 个并发查询 petabytes 的弹性数据仓库
    
- 管理大量结构化数据与快速分析动态增大和收缩以秒为单位计算
    
- 支持透明数据加密
    
- 备份的 7 天内每隔 8 小时
    
### <a name="common-uses"></a>常见用途

- 销售报表
    
- 使用率报告
    
- 大量的数据
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](https://azure.microsoft.com/services/sql-data-warehouse/)。
  
成本信息，请单击[此处](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)。
  
## <a name="azure-data-lake-store"></a>Azure 数据湖存储区

### <a name="features"></a>功能

- 对于大数据分析工作负荷超大规模存储库
    
- Hadoop 分布式文件系统的云
    
- 没有固定的限制文件大小
    
- 没有固定的限制帐户大小
    
- 以其本机格式的非结构化和结构化数据
    
- 巨大的吞吐量，从而提高分析性能
    
- 高耐用性、 可用性和可靠性 （99.9%企业级 SLA 和 24/7 支持）
    
- Azure Active Directory 访问控制
    
### <a name="common-uses"></a>常见用途

- 企业级存储库来存储每种类型的数据收集到一个位置
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

有关其他信息，请单击[此处](https://azure.microsoft.com/services/data-lake-store/)。
  
成本信息，请单击[此处](https://azure.microsoft.com/pricing/details/data-lake-store/)。
  
## <a name="next-step"></a>后续步骤

复查的[从头构建](build-from-the-ground-up.md)云存储选项。
  
## <a name="see-also"></a>See Also

[企业架构师的 Microsoft 云存储](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



