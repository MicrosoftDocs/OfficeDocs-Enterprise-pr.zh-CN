---
title: 一些所需的程序集
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
ms.assetid: ccf1b8b3-0d50-4c66-b314-f480245fad5e
description: 摘要： 大致集可用于创建自定义存储解决方案的云存储选项的详细信息。
ms.openlocfilehash: 2c80b0cdf0829e80a7916133ee51a45c91b96efa
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915517"
---
# <a name="some-assembly-required"></a>一些所需的程序集

 **摘要：** 获取一组由云的详细信息可用于创建自定义存储解决方案的存储选项。
  
"一些所需的程序集"存储解决方案：
  
- 作为起点的现有服务用于存储解决方案。
    
- 需要一些配置或编码。
    
- 可以自定义以满足您的需求。
    
以下各节介绍了每个"一些所需的程序集"存储解决方案的详细信息。
  
## <a name="azure-content-delivery-network"></a>Azure 内容交付网络

### <a name="features"></a>功能

- 高级和实际时间分析
    
- 针对 DDoS 可靠的安全性
    
- 获取内容自动从 Azure 网站或 Azure 云服务后设置集成
    
- 与 Akamai 新合作关系
    
- 可以处理突然流量峰值和过重
    
### <a name="common-uses"></a>常见用途

- 音频、 视频、 应用程序、 图像和其他文件更快、 更可靠地向客户分发使用其最接近的服务器
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
- 管理视频
    
### <a name="resources"></a>资源

其他信息，请单击[此处](https://azure.microsoft.com/services/cdn/)。
  
成本信息，请单击[此处](https://azure.microsoft.com/pricing/details/cdn/)。
  
## <a name="hdinsight"></a>HdInsight

### <a name="features"></a>功能

- Apache Hadoop 分发由云数据湖泊服务
    
- 扩展到按需型 petabytes
    
- 处理非结构化和半结构化数据 Java、.NET，等中的开发
    
- 跳过购买和维护硬件
    
- 使用云连接的本地 Hadoop 群集
    
- 灵活地部署通过自定义脚本 (例如 R，Giraph，Solr) 的任意 Hadoop 项目
    
### <a name="common-uses"></a>常见用途

- 数据分析工作负荷
    
- 内存中数据处理框架 big 数据 (Spark)
    
- 实时流处理 （风暴）
    
- 大型事务处理 (OLTP) 的非关系数据 (HBase)
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

其他信息，请单击[此处](https://azure.microsoft.com/services/hdinsight/)。
  
成本信息，请单击[此处](https://azure.microsoft.com/pricing/details/hdinsight/)。
  
## <a name="azure-sql-database"></a>Azure SQL 数据库

### <a name="features"></a>功能

- 优化以减少管理和成本
    
- 自动高可用性、 灾难恢复和升级
    
- 建议企业管理数百或数千个达 1 TB 的大小的数据库
    
- 分片技术可将数据分割数据库来增加存储
    
- 伸展数据库与 SQL Server 2016
    
### <a name="common-uses"></a>常见用途

- 新的云设计应用程序的关系数据
    
- 通过使用关系示意图、 高度结构化数据集的数据处理
    
- 空间数据或丰富的数据类型
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="elastic-database"></a>弹性数据库

几乎不受限制的资源的 Azure SQL 数据库时的使用：
  
- 太长而单个数据库的限制内的总数据量。
    
- 总体工作负荷的事务吞吐量超出单个数据库的功能。
    
- 租户需要从每个其他，物理隔离，因此每个租户需要单独的数据库。
    
- 数据库的不同部分需要驻留在不同地理区域的合规性、 性能或地缘政治原因。
    
使用垂直缩放比例，您可以更改 Azure 数据库性能级别/版或使用弹性数据库池。
  
![Azure SQL 数据库提供的垂直缩放比例。](media/Storage-Poster/CloudStor-VertScale.png)
  
水平缩放，您可以根据需要添加新数据库。
  
![Azure SQL 数据库提供的水平缩放比例。](media/Storage-Poster/CloudStor-HorizScale.png)
  
单击[此处](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction)的详细信息。
  
### <a name="stretch-database-with-sql-server-2016"></a>使用 SQL Server 2016 的 Stretch Database

拉伸数据库是一项功能允许您透明地实施且安全地移动冷备用数据，例如包含客户订单信息，在 Azure 中的 SQL 拉伸数据库大型表中的已关闭的业务数据的 SQL Server 2016。拉伸时, 的内容的 SQL Server 实例、 数据库，或者甚至是单个表是 SQL Server 2016 server 中的本地数据和 Azure 中的远程数据的组合。将成为合格的拉伸自动移动到 Azure SQL Server 2016 的数据。
  
![SQL Server 2016 中的 Stretch Database。](media/Storage-Poster/CloudStor-Stretch.png)
  
包含历史数据的用户查询以透明的方式转发到 Azure SQL Stretch Database。即使延伸表，也不需要对查询进行重新编写。
  
Stretch Database 提供经济高效的选项，用于历史数据的长期存储和透明访问。它还解决了表变大时出现的性能和可用性问题。
  
单击[此处](https://msdn.microsoft.com/library/dn935011.aspx)的详细信息。
  
### <a name="resources"></a>资源

其他信息，请单击[此处](http://azure.microsoft.com/services/sql-database/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/sql-database/)。
  
## <a name="azure-cosmos-db"></a>Azure 宇宙 DB

### <a name="features"></a>功能

- 保证低延迟、 99.99%可用性 SLA 无限可能、 弹性比例为存储和吞吐量
    
- 在任意数量的地区透明故障转移和四个定义完善的一致性级别全局复制所有数据
    
- 自动对所有数据而无需架构或辅助索引编制都索引
    
- 富 SQL 和 JavaScript 查询和多项事务
    
### <a name="common-uses"></a>常见用途

- IoT、 移动和社交
    
- 游戏
    
- 零售
    
- 内容管理
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="cosmos-db-vs-azure-tables-vs-azure-sql-database"></a>宇宙 DB 与 Azure 表与 Azure SQL 数据库

宇宙 DB、 Azure 表存储和 Azure SQL 数据库的常见属性：
  
- 99.99 可用性 SLA
    
- 完全托管的数据库服务
    
- ISO 27001、 HIPAA 和欧盟示范条款兼容
    
下表显示不常用的 Azure 宇宙 DB、 Azure 表存储和 Azure SQL Database 属性。
  
![不常用属性：Cosmos DB 与Azure 表与Azure SQL 数据库](media/Storage-Poster/CloudStor-Table.png)
  
### <a name="resources"></a>资源

其他信息，请单击[此处](http://azure.microsoft.com/services/documentdb/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/documentdb/)。
  
## <a name="azure-media-services"></a>Azure 媒体服务

### <a name="features"></a>功能

- Live 和使用扩展需求 (VOD) 传递视频
    
- 高可用性编码和流式处理
    
- 支持 Flash、 iOS、 Android、 HTML5 和 Xbox
    
- Studio 认证 DRM 支持
    
- 富内容蕴含
    
- 广泛预集成合作伙伴生态系统
    
### <a name="common-uses"></a>常见用途

- 编码、 存储和流音频和视频，网址为扩展
    
- 实时流式传输和 VOD
    
- 简化的视频内容管理
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理视频
    
### <a name="resources"></a>资源

其他信息，请单击[此处](https://azure.microsoft.com/services/media-services/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/media-services/)。
  
## <a name="azure-redis-cache"></a>Azure Redis 缓存

### <a name="features"></a>功能

- 安全、 专用 Redis 具有高可用性与数据复制和由 Microsoft 托管的故障转移服务器
    
- 建议在需要高吞吐量任何应用程序
    
- 中的可用大小为 530 GB 及 （带 Premium 自动分片）
    
- Redis 持久性仍然存在内存中缓存数据到 Azure 存储
    
- Redis 群集，可以实现最大的规模和吞吐量
    
- 使用 Azure 虚拟网络支持增强的安全性和网络隔离
    
### <a name="common-uses"></a>常见用途

- 反向查找 Azure，如宇宙 DB 和 Azure SQL 数据库中的任何存储服务中的数据
    
- 从其他数据存储同步的内容
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 缓存数据
    
- 高吞吐量应用程序的消息 broker
    
### <a name="resources"></a>资源

其他信息，请单击[此处](http://azure.microsoft.com/services/cache/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/cache/)。
  
## <a name="sql-server-on-an-azure-vm"></a>在 Azure 虚拟机上的 SQL Server

### <a name="features"></a>功能

- Azure 虚拟机上运行安装的应用程序的 SQL Server
    
- 使用带有 SQL Server 库图像安装或者让您自己的 SQL Server 许可证
    
### <a name="common-uses"></a>常见用途

- 管理应用程序的数据
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

其他信息，请单击[此处](http://azure.microsoft.com/services/virtual-machines/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/virtual-machines/)。
  
## <a name="storsimple"></a>StorSimple

### <a name="features"></a>功能

- 可扩展的企业混合 SAN 存储与 SSD HDD 的内部部署混合存储阵列，与云存储解决方案的集成扩展
    
- 内嵌消除、 压缩、 自动分层和非结构化的加密和半结构化数据
    
- 使用云快照自动的异地数据保护
    
- 有高效、 独立于位置的灾难恢复
    
- 与 Azure 中的 StorSimple 虚拟装置的企业数据的数据移动
    
### <a name="common-uses"></a>常见用途

- 管理数据增长与文件共享、 档案和其他数据存储库
    
- 非现场数据保护和灾难恢复的文件共享、 虚拟机、 SQL 和 SharePoint （使用远程 Blob 存储）
    
- 利用云快照克隆 Azure 中的数据并增加业务灵活性
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
- 协作
    
### <a name="resources"></a>资源

其他信息，请单击[此处](http://azure.microsoft.com/services/storsimple/)。
  
成本信息，请单击[此处](http://azure.microsoft.com/pricing/details/storsimple/)。
  
## <a name="azure-sql-data-warehouse"></a>Azure SQL 数据仓库

### <a name="features"></a>功能

- 弹性数据仓库，能够扩展到最多 32 并发查询 petabytes
    
- 管理大量 fast 结构化数据分析动态放大和缩小以秒为单位计算
    
- 支持透明数据加密
    
- 备份 7 天的每隔 8 小时
    
### <a name="common-uses"></a>常见用途

- 销售报表
    
- 使用率报告
    
- 大量数据
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

其他信息，请单击[此处](https://azure.microsoft.com/services/sql-data-warehouse/)。
  
成本信息，请单击[此处](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)。
  
## <a name="azure-data-lake-store"></a>Azure 数据湖泊存储区

### <a name="features"></a>功能

- 大数据分析工作负荷超大型存储库
    
- Hadoop 分布式文件系统针对云
    
- 没有固定的文件大小限制
    
- 没有固定的帐户大小限制
    
- 以本机格式的非结构化和非结构化数据
    
- 大规模吞吐量，从而提高性能分析
    
- 高持久性、 可用性和可靠性 （99.9%的企业级 SLA 和全天候支持）
    
- Azure Active Directory 访问控制
    
### <a name="common-uses"></a>常见用途

- 企业级存储库来存储每个类型的一个位置中收集数据
    
### <a name="key-storage-scenarios"></a>密钥存储方案

- 管理数据
    
### <a name="resources"></a>资源

其他信息，请单击[此处](https://azure.microsoft.com/services/data-lake-store/)。
  
成本信息，请单击[此处](https://azure.microsoft.com/pricing/details/data-lake-store/)。
  
## <a name="next-step"></a>后续步骤

查看[up 从头生成](build-from-the-ground-up.md)云存储选项。
  
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 云存储](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



