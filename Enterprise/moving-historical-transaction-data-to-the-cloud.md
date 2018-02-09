---
title: "将历史交易记录数据迁移到云"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: "摘要： Contoso 如何实施 SQL Server Stretch Database，以减少其本地数据存储需求并降低日常运行成本。"
ms.openlocfilehash: 9d8d51aa1bc7a304d1148111aedd54916d9e8052
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a>将历史交易记录数据迁移到云

 **摘要：** Contoso 如何实施 SQL Server Stretch Database，以减少其本地数据存储需求并降低日常运行成本。
  
Contoso 的企业存储系统存储了大量历史交易数据，用于遵守监管要求，以及市场研究和支出趋势 BI 分析。Contoso 还需要从磁带还原存档的数据，这是一个耗时的过程。Contoso 的企业存储系统中的硬件已接近其使用寿命，更换该硬件成本将非常昂贵。 
  
作为缩减本地数据中心的业务需求的一部分，由于具有 Stretch Database 混合功能并可与 Azure 无缝集成，Contoso 选择升级到 SQL Server 2016。Stretch Database 允许 Contoso 将其表中的原始数据从本地移动到云存储，从而释放本地磁盘空间并减少维护工作。经常访问的数据和原始数据都在同一个表中，并且始终可供应用程序及其用户使用，也可用于维护（如备份和还原）。图 1 显示了 Stretch Database。
  
**图 1：SQL Server Stretch Database**

![SQL Server Stretch Database 作为混合数据解决方案](images/Contoso_Poster/StretchDB01.png)
  
图 1 显示了 SQL 客户端如何向运行 SQL Server 2016 的服务器发送 T-SQL 查询，该服务将它们转发到 Azure PaaS 中的 Azure SQL Stretch Database。
  
有关详细信息，请参阅 [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)。
  
Contoso 使用这些步骤将其历史数据移动到云：
  
1. 分析数据库
    
    对要移动到云的数据库中的表执行分析，并修复所有问题。新的 Stretch Database 顾问向他们提供了其对 SQL Server 2016 中所有功能期望的全面概述，包括哪些表具有可延伸的原始数据。
    
2. 升级
    
    将巴黎总部数据中心中的现有 SQL 服务器更新为 SQL Server 2016。
    
3. 将原始数据迁移到云
    
    通过使用 SQL Management Studio，他们确定了要延伸的数据库和要迁移到 Azure 中 Stretch Database 的实例的表。随着时间的推移，在后台，SQL Server 2016 将历史数据移动到 Azure 中的 Stretch Database。
    
下面是在巴黎总部运行 SQL Server 2016 的一个服务器的最终配置。
  
**图 2：对 Contoso 的数据中心中的服务器使用 Stretch Database**

![Contoso SQL Server Stretch Database 配置，用于运行 SQL Server 的单个计算机](images/Contoso_Poster/StretchDB02.png)

  
图 2 显示了对 Contoso 数据中心中的应用程序服务器的用户查询如何成为可传递到 Azure PaaS 中的 Azure SQL Stretch Database 的 SQL 查询。
  
用户通过现有应用和查询访问数据。访问策略保持不变。直接操作，无需执行磁带备份。维护包括备份和还原经常访问的数据。
  
实施 Stretch Database 后，Contoso：
  
- 将其本地数据存储需求降低了 85%。
    
- 使得企业存储系统更新和对磁带存档的依赖不再是必要条件。
    
- 显著减少每日运行成本。
    
## <a name="see-also"></a>另请参阅

[Contoso Corporation 的企业方案](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)




