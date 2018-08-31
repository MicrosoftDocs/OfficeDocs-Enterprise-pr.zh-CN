---
title: Azure PaaS 的混合云方案
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
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 摘要： 了解在 Azure 中基于 Microsoft 平台即服务 (PaaS) 云产品的混合体系结构和方案。
ms.openlocfilehash: e60bc92eed45e5d29fe0be80320dee65b8325028
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915007"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Azure PaaS 的混合云方案

 **摘要：** 了解在 Azure 中基于 Microsoft 平台即服务 (PaaS) 云产品的混合体系结构和方案。
  
将本地数据或计算资源与在 Azure PaaS 中运行的新的或已转换的应用程序结合使用，可以充分利用云的性能、可靠性和规模，为移动用户提供更好的支持。 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Azure PaaS 混合方案体系结构

图 1 显示了适用于 Azure 的 基于 Microsoft PaaS 的混合方案的体系结构。
  
**图 1：Azure 中基于 Microsoft PaaS 的混合方案**

![Azure 中基于 Microsoft PaaS 的混合方案](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
针对体系结构的每一层：
  
- 应用和方案
    
    混合 PaaS 应用程序在 Azure 中运行，并使用本地计算或存储资源。
    
- 标识
    
    由目录同步或与第三方标识提供程序的联合组成。
    
- 网络
    
    由现有的 Internet 管道或通过到 Azure PaaS 的公共对等建立的 ExpressRoute 连接组成。必须包括 Azure PaaS 应用程序访问本地计算或存储资源的方法。
    
- 本地
    
    由标识和安全基础结构及现有的业务线 (LOB) 应用程序或数据库服务器组成，Azure PaaS 应用程序可以对其进行安全访问。
    
## <a name="azure-paas-hybrid-application"></a>Azure PaaS 混合应用程序

图 2 显示了在 Azure 中运行的混合应用程序的配置。
  
**图 2：基于 Azure PaaS 的混合应用程序**

![基于 Azure PaaS 的混合应用程序](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
在图 2 中，本地网络在服务器上承载存储或应用程序以及包含代理服务器的 DMZ。它通过 Internet 或使用 ExpressRoute 连接来连接到 Azure PaaS 服务。
  
组织可以通过以下方式使其计算或存储资源对 Azure PaaS 混合应用程序可用：
  
- 托管 DMZ 中服务器上的资源。
    
- 在 DMZ 中托管反向代理服务器，这将允许对位于本地的资源执行经身份验证的请求、入站请求和基于 HTTPS 的请求。
    
Azure 应用可以使用以下程序提供的凭据：
  
- Azure AD，它可以与本地标识提供程序（如 Windows Server AD）同步。
    
- 第三方标识提供程序。
    
### <a name="example-azure-paas-hybrid-application"></a>示例 Azure PaaS 混合应用程序

图 3 显示了在 Azure 中运行的混合应用程序的示例。
  
**图 3：基于 Azure PaaS 的混合应用程序示例**

![基于 Azure PaaS 的混合应用程序示例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
在图 3 中，本地网络承载 LOB 应用程序。Azure PaaS 承载自定义的移动应用。Internet 上的智能电话访问 Azure 中的自定义移动应用，它将数据请求发送到本地 LOB 应用程序。
  
本示例中的 Azure PaaS 混合应用程序是提供有关员工最新联系信息的自定义移动应用。端到端的混合方案由以下各项组成：
  
- 需要经验证的本地凭据才能运行的智能电话应用。
    
- 在 Azure PaaS 中运行的自定义移动应用，它根据用户智能电话应用的查询，请求有关特定员工的信息。
    
- DMZ 中的反向代理服务器，验证自定义移动应用，并将转发该请求。
    
- LOB 应用程序服务器场，根据用户帐户的权限，为联系人请求提供服务。
    
由于本地标识提供程序已与 Azure AD 同步，自定义移动应用和 LOB 应用都可以验证请求用户的帐户名称。
  
## <a name="stretch-database-with-sql-server-2016"></a>使用 SQL Server 2016 的 Stretch Database

Stretch Database 是 SQL Server 2016 的一项功能，它可以使你以透明的方式安全地将原始数据（如包含客户订单信息的大型表中已结束的业务数据）移动到 Azure 中的 SQL Stretch Database。
  
延伸后，SQL Server 实例、数据库或者甚至单个表中的内容会是 SQL Server 2016 服务器中的本地数据和 Azure 中远程数据的组合。SQL Server 2016 会自动将变得符合条件的伸展数据移动至 Azure。
  
图 4 显示了使用 SQL Server 2016 的 Stretch Database。
  
**图 4：使用 SQL Server 2016 的 Stretch Database**

![使用 SQL Server 2016 的 Stretch Database](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-SQL.png)
  
在图 4 中，本地网络承载一个服务器，该服务器运行配有小型本地数据库的 SQL Server 2016。Azure PaaS 承载 Azure SQL Server Stretch Database（包含扩展部分的数据库）的实例。从本地用户发送到本地 SQL 服务器的 T-SQL 查询已被安全转发到 Azure SQL Stretch Database，然后由该 Stretch Database 将结果返回给发出请求的用户。
  
 包含历史数据的用户查询以透明的方式转发到 Azure SQL Stretch Database。即使延伸表，也不需要对查询进行重新编写。
  
Stretch Database 提供经济高效的选项，用于历史数据的长期存储和透明访问。它还解决了表变大时出现的性能和可用性问题。
  
有关详细信息，请参阅 [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)。
  
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 混合云](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



