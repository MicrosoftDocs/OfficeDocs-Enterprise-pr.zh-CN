---
title: 将历史交易记录数据迁移到云
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: 摘要： Contoso 如何实施 SQL Server Stretch Database，以减少其本地数据存储需求并降低日常运行成本。
ms.openlocfilehash: 791b5d4f14ba7246221cf9b459c31c9ba1b54099
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915717"
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a><span data-ttu-id="3d75b-103">将历史交易记录数据迁移到云</span><span class="sxs-lookup"><span data-stu-id="3d75b-103">Moving historical transaction data to the cloud</span></span>

 <span data-ttu-id="3d75b-104">**摘要：** Contoso 如何实施 SQL Server Stretch Database，以减少其本地数据存储需求并降低日常运行成本。</span><span class="sxs-lookup"><span data-stu-id="3d75b-104">**Summary:** How Contoso implemented SQL Server stretch database to reduce its on-premises data storage needs and daily running costs.</span></span>
  
<span data-ttu-id="3d75b-p101">Contoso 的企业存储系统存储了大量历史交易数据，用于遵守监管要求，以及市场研究和支出趋势 BI 分析。Contoso 还需要从磁带还原存档的数据，这是一个耗时的过程。Contoso 的企业存储系统中的硬件已接近其使用寿命，更换该硬件成本将非常昂贵。</span><span class="sxs-lookup"><span data-stu-id="3d75b-p101">Contoso's enterprise storage system stores a large amount of historical transaction data for adherence with regulatory requirements and for marketing research and BI analysis of spending trends. Contoso also needs to restore archived data from magnetic tape, a time-intensive process. The hardware in Contoso's enterprise storage system was nearing its end of life and replacing it would be very expensive.</span></span> 
  
<span data-ttu-id="3d75b-p102">作为缩减本地数据中心的业务需求的一部分，由于具有 Stretch Database 混合功能并可与 Azure 无缝集成，Contoso 选择升级到 SQL Server 2016。Stretch Database 允许 Contoso 将其表中的原始数据从本地移动到云存储，从而释放本地磁盘空间并减少维护工作。经常访问的数据和原始数据都在同一个表中，并且始终可供应用程序及其用户使用，也可用于维护（如备份和还原）。图 1 显示了 Stretch Database。</span><span class="sxs-lookup"><span data-stu-id="3d75b-p102">As part of its business need to scale down its on-premises datacenters, Contoso chose to upgrade to SQL Server 2016 because of the Stretch Database hybrid feature and its seamless integration with Azure. Stretch Database allows Contoso to move the cold data in its tables from on-premises to cloud storage, freeing up local disk space and reducing maintenance. Both hot and cold data are in the same tables and are always available to applications and their users and for maintenance, such as backups and restores. Figure 1 shows Stretch Database.</span></span>
  
<span data-ttu-id="3d75b-112">**图 1：SQL Server Stretch Database**</span><span class="sxs-lookup"><span data-stu-id="3d75b-112">**Figure 1: SQL Server Stretch Database**</span></span>

![SQL Server Stretch Database 作为混合数据解决方案](media/Contoso-Poster/StretchDB01.png)
  
<span data-ttu-id="3d75b-114">图 1 显示了 SQL 客户端如何向运行 SQL Server 2016 的服务器发送 T-SQL 查询，该服务将它们转发到 Azure PaaS 中的 Azure SQL Stretch Database。</span><span class="sxs-lookup"><span data-stu-id="3d75b-114">Figure 1 shows how a SQL client sends T-SQL queries to a server running SQL Server 2016, which forwards them to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="3d75b-115">有关详细信息，请参阅 [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)。</span><span class="sxs-lookup"><span data-stu-id="3d75b-115">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
<span data-ttu-id="3d75b-116">Contoso 使用这些步骤将其历史数据移动到云：</span><span class="sxs-lookup"><span data-stu-id="3d75b-116">Contoso used these steps to move their historical data to the cloud:</span></span>
  
1. <span data-ttu-id="3d75b-117">分析数据库</span><span class="sxs-lookup"><span data-stu-id="3d75b-117">Analyze databases</span></span>
    
    <span data-ttu-id="3d75b-p103">对要移动到云的数据库中的表执行分析，并修复所有问题。新的 Stretch Database 顾问向他们提供了其对 SQL Server 2016 中所有功能期望的全面概述，包括哪些表具有可延伸的原始数据。</span><span class="sxs-lookup"><span data-stu-id="3d75b-p103">Performed an analysis of the tables in the databases that they intended to move to the cloud and fixed any issues. The new Stretch Database Advisor gave them a full overview of what they can expect from all features in SQL Server 2016, including which tables have cold data that could be stretched.</span></span>
    
2. <span data-ttu-id="3d75b-120">升级</span><span class="sxs-lookup"><span data-stu-id="3d75b-120">Upgrade</span></span>
    
    <span data-ttu-id="3d75b-121">将巴黎总部数据中心中的现有 SQL 服务器更新为 SQL Server 2016。</span><span class="sxs-lookup"><span data-stu-id="3d75b-121">Updated existing SQL servers in the Paris headquarters datacenter to SQL Server 2016.</span></span>
    
3. <span data-ttu-id="3d75b-122">将原始数据迁移到云</span><span class="sxs-lookup"><span data-stu-id="3d75b-122">Migrate cold data to the cloud</span></span>
    
    <span data-ttu-id="3d75b-p104">通过使用 SQL Management Studio，他们确定了要延伸的数据库和要迁移到 Azure 中 Stretch Database 的实例的表。随着时间的推移，在后台，SQL Server 2016 将历史数据移动到 Azure 中的 Stretch Database。</span><span class="sxs-lookup"><span data-stu-id="3d75b-p104">Using SQL Management Studio, they identified the databases to stretch and the tables to migrate to instances of Stretch Database in Azure. Over time and in the background, SQL Server 2016 moved the historical data to stretch databases in Azure.</span></span>
    
<span data-ttu-id="3d75b-125">下面是在巴黎总部运行 SQL Server 2016 的一个服务器的最终配置。</span><span class="sxs-lookup"><span data-stu-id="3d75b-125">Here is the resulting configuration for one server running SQL Server 2016 in the Paris headquarters.</span></span>
  
<span data-ttu-id="3d75b-126">**图 2：对 Contoso 的数据中心中的服务器使用 Stretch Database**</span><span class="sxs-lookup"><span data-stu-id="3d75b-126">**Figure 2: Using Stretch Database for a server in Contoso's datacenter**</span></span>

![Contoso SQL Server Stretch Database 配置，用于运行 SQL Server 的单个计算机](media/Contoso-Poster/StretchDB02.png)

  
<span data-ttu-id="3d75b-128">图 2 显示了对 Contoso 数据中心中的应用程序服务器的用户查询如何成为可传递到 Azure PaaS 中的 Azure SQL Stretch Database 的 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="3d75b-128">Figure 2 shows how user queries to an application server in Contoso's datacenter become SQL queries that are passed to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="3d75b-p105">用户通过现有应用和查询访问数据。访问策略保持不变。直接操作，无需执行磁带备份。维护包括备份和还原经常访问的数据。</span><span class="sxs-lookup"><span data-stu-id="3d75b-p105">Users access the data through existing apps and queries. Access policies remain the same. Moving forward, there is no need for tape backups. Maintenance consists of backing up and restoring hot data.</span></span>
  
<span data-ttu-id="3d75b-133">实施 Stretch Database 后，Contoso：</span><span class="sxs-lookup"><span data-stu-id="3d75b-133">After implementing Stretch Database, Contoso:</span></span>
  
- <span data-ttu-id="3d75b-134">将其本地数据存储需求降低了 85%。</span><span class="sxs-lookup"><span data-stu-id="3d75b-134">Reduced its on-premises data storage needs by 85%.</span></span>
    
- <span data-ttu-id="3d75b-135">使得企业存储系统更新和对磁带存档的依赖不再是必要条件。</span><span class="sxs-lookup"><span data-stu-id="3d75b-135">Made the update of the enterprise storage system and reliance on magnetic tape archives unnecessary.</span></span>
    
- <span data-ttu-id="3d75b-136">显著减少每日运行成本。</span><span class="sxs-lookup"><span data-stu-id="3d75b-136">Reduced its daily running costs significantly.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="3d75b-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d75b-137">See Also</span></span>

[<span data-ttu-id="3d75b-138">Contoso Corporation 的企业方案</span><span class="sxs-lookup"><span data-stu-id="3d75b-138">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="3d75b-139">Microsoft 云中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="3d75b-139">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="3d75b-140">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="3d75b-140">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="3d75b-141">Stretch Database</span><span class="sxs-lookup"><span data-stu-id="3d75b-141">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="3d75b-142">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="3d75b-142">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




