---
title: "为 Microsoft Azure PaaS 设计网络"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "摘要： 了解如何优化你的网络以便访问 Microsoft Azure PaaS。"
ms.openlocfilehash: d63a7a20d4648b0044a24ea86ad4e9125779a027
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-azure-paas"></a>为 Microsoft Azure PaaS 设计网络

 **摘要：** 了解如何优化你的网络以便访问 Microsoft Azure PaaS。
  
优化 Azure PaaS 应用网络需要有足够的 Internet 带宽，可能还会要求网络流量跨多个站点或应用分布。
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a>计划将组织 PaaS 应用程序驻留在 Azure 中的步骤

在此处插入章节正文。
  
1. 经过[公共元素的 Microsoft 云连接](common-elements-of-microsoft-cloud-connectivity.md)中的**步骤来准备您网络上的 Microsoft 云服务**部分。
    
2. 优化您的互联网带宽使用步骤 2-4 的设计[网络，对于 Microsoft SaaS](designing-networking-for-microsoft-saas.md)的**步骤来准备您的 Microsoft SaaS 服务的网络**部分。
    
3. 确定是否需要到 Azure 的 ExpressRoute 连接。
    
4. 对于基于 Web 的工作负载，确定是否需要 Azure 应用程序网关。
    
5. 要使流量分布到不同数据中心内的不同终结点，请确定是否需要 Azure 流量管理器。
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a>组织 PaaS 应用程序的 Internet 带宽

在 Azure PaaS 中托管的组织应用程序要求 Intranet 用户具有 Internet 带宽。有两个选项：
  
- **选项 1：** 使用现有的管道，管道已针对 Internet 通信进行了优化，拥有处理峰值负载的容量。请参阅[为 Microsoft SaaS 设计网络](designing-networking-for-microsoft-saas.md)，了解 Internet 边缘、客户端使用情况和 IT 操作注意事项。
    
- **选项 2：** 如果要求高带宽或低延迟，请使用 ExpressRoute 到 Azure 的连接。
    
**图 1：用于连接 Azure PaaS 服务的连接选项**

![图 1：Azure PaaS 服务的连接选项](images/Network_Poster/PaaS1.png)
  
图 1 显示了通过 Internet 管道或 ExpressRoute 连接到 Azure PaaS 服务的内部部署网络。
  
## <a name="azure-application-gateway"></a>Azure 应用程序网关

应用程序级路由和负载平衡服务，使你可以在 Azure 中为 Web 应用、云服务和虚拟机创建一个可扩展、高可用性的 Web 前端。 
  
**图 2：Azure 应用程序网关**

![图 2：Azure 应用程序网关服务](images/Network_Poster/PaaS2.png)
  
图 2 显示了 Azure 应用程序网关，并展示如何将来自 Internet 的用户请求传送到 Azure Web 应用、云服务或虚拟机。
  
应用程序网关当前支持以下项的第 7 层应用程序传送：
  
- HTTP 负载平衡
    
- 基于 cookie 的会话关联
    
- SSL 卸载
    
有关详细信息，请参阅[应用程序网关](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)。
  
## <a name="azure-traffic-manager"></a>Azure 流量管理器

将流量分布到不同的终结点，此过程可以包括位于不同的数据中心或外部终结点的云服务或 Azure Web 应用。
  
流量管理器使用以下路由方法：
  
- **故障转移：** 终结点位于相同或不同的 Azure 数据中心内，你想要对所有流量使用主终结点，但在主终结点或备份终结点不可用的情况下提供了备份。
    
- **轮循机制：** 你想要将负载分布在同一个或不同数据中心的一组终结点上。
    
- **性能：** 终结点位于不同的地理位置，你想要请求客户端使用延迟最低且距离"最近"的终结点。
    
下例显示了三个地理位置分散的 Web 应用。
  
**图 3：Azure 流量管理器**

![图 3：Azure 流量管理器](images/Network_Poster/PaaS3.png)
  
图 3 显示了流量管理器用来将请求传送到在美国、欧洲和亚洲的三个不同 Azure Web 应用的基本过程。在本例中：
  
1. 网站 URL 的用户 DNS 查询定向到 Azure 流量管理器，流量管理器基于性能路由方法返回区域 Web 应用的名称。
    
2. 用户启动与欧洲区域 Web 应用之间的流量。
    
有关详细信息，请参阅[通信量管理器](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)。
  
## <a name="see-also"></a>See Also

[面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)



