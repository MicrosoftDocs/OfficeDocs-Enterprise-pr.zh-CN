---
title: 发展你的云连接网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: 摘要：了解采用云如何要求使用新的网络基础设施投资方法。
ms.openlocfilehash: 47d24a4f545cfae8a6bd1c507a61f48b6d26cc7d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067628"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>发展你的云连接网络

 **摘要：** 了解采用云如何要求使用新的网络基础设施投资方法。
  
云迁移更改公司网络内部和外部的通信量和通信性质。它还会影响降低安全风险的方法。
  
- 云之前
    
    大多数网络基础设施的投资都花在确保到本地数据中心的连接可用、可靠且性能卓越上。对于许多组织来说，Internet 连接对内部业务运营不是很重要。网络边界是避免安全隐患的主要防御措施。
    
- 云之后
    
    利用新的和已迁移的工作效率以及在云中运行的 IT 工作负载，基础设施投资从本地数据中心转向 Internet 连接，这一点现在对内部业务运营至关重要。由于标识和数据通过网络和连接点流向 Microsoft 云服务，联合连接从安全策略转向保护标识和数据。
    
网络基础设施投资从连接开始。其他投资取决于云服务的类别。
  
- **软件即服务 (SaaS)** Microsoft SaaS 服务包括 Office 365、Microsoft Intune 和 Microsoft Dynamics 365。用户能成功利用 SaaS 服务，要依赖于高可用性和高性能的 Internet 连接或直接到 Microsoft 云服务的连接。
    
    网络体系结构侧重于可靠、冗余的连接和足够的带宽。正在进行的投资包括性能监控和调优。
    
- **Azure 平台即服务 (PaaS)** 除了 Microsoft SaaS 服务的投资，多站点或地理位置上分散的 PaaS 应用程序可能需要构建 Azure 流量管理器来分配客户端流量。正在进行的投资包括性能和流量分布监控以及故障转移测试。
    
- **Azure 基础结构即服务 (IaaS)** 除了 Microsoft SaaS 和 PaaS 服务的投资，IaaS 中正在运行的 IT 工作负载要求设计和配置 Azure 虚拟网络，这些网络用于承载虚拟机、到虚拟机上运行的应用程序的安全连接、路由、IP 地址、DNS 以及负载平衡。正在进行的投资包括性能和安全监控以及疑难解答。

[Microsoft 365](https://www.microsoft.com/microsoft-365)是 Office 365、企业管理 + 安全性 (EMS) 和 Windows 10 的组合。 Microsoft 365 将多个 SaaS 和 Azure 服务与一个完整的智能解决方案结合在一起, 使每个人都能有创造性且安全地协同工作。
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>云中成功的网络投资领域

企业组织从采用系统的方法来优化 Intranet 中和到 Internet 的网络吞吐量中获益。你可能还会从 ExpressRoute 连接中获益。
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>优化 Intranet 到边缘网络的连接

多年来，许多组织已经优化了在内部数据中心中运行的应用程序的 Intranet 连接和性能。由于生产效率和 Microsoft 云中运行的 IT 工作负载，必须额外投资以确保连接的高可用性，还要确保边缘网络和 Intranet 用户之间的通信性能是最佳的。
  
### <a name="optimize-throughput-at-your-edge-network"></a>优化边缘网络的吞吐量

由于你更多的日常工作效率流量传输至云，你应该仔细检查边缘网络的一套系统，确保它们是最新的，可以提供高可用性并有足够的容量来满足峰值负载。
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>对于 Azure、Office 365，和 Dynamics 365 的高级 SLA，请使用 ExpressRoute

虽然你可以从边缘网络使用当前 Internet 连接, 但与 Microsoft 云服务的通信必须与进入 Internet 的其他 intranet 流量共享管道。 此外，到 Microsoft 云服务的流量还受限于 Internet 流量拥塞。
  
为了实现高级 SLA 和最佳性能，请使用 ExpressRoute，这是你的网络与 Azure、Office 365、Dynamics 365 或所有这三个系统之间的专用 WAN 连接。 
  
ExpressRoute 可以利用你现有的网络提供程序来提供专用连接。通过 ExpressRoute 连接的资源就好像它们位于你的 WAN 中一样，甚至对于地理位置分散的组织也是如此。
  
有关详细信息，请参阅[面向 Microsoft 云连接的 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。
  
## <a name="scope-of-network-investments"></a>网络投资的范围

网络投资的范围取决于云服务的类别。在 Microsoft 云中投资将最大限度地利用网络团队的投资。IaaS 服务的投资适用于所有投资领域。
  
|||||
|:-----|:-----|:-----|:-----|
|投资领域  <br/> |SaaS  <br/> |PaaS  <br/> |IaaS  <br/> |
|构建可靠、冗余且具有足够带宽的 Internet 连接  <br/> |应用  <br/> |应用  <br/> |应用  <br/> |
|监控和调整 Internet 吞吐量以提高性能  <br/> |应用  <br/> |应用  <br/> |应用  <br/> |
|解决 Internet 连接和吞吐量问题  <br/> |应用  <br/> |应用  <br/> |应用  <br/> |
|设计 Azure 流量管理器，对不同终结点的流量执行负载平衡  <br/> ||应用  <br/> |应用  <br/> |
|构建到 Azure 虚拟网络的可靠、冗余的高性能连接  <br/> |||应用  <br/> |
|设计到 Azure 虚拟机的安全连接  <br/> |||应用  <br/> |
|设计并实施本地位置和虚拟网络之间的路由  <br/> |||应用  <br/> |
|构建并实施内部和面向 Internet 的 IT 工作负载的负载平衡  <br/> |||应用  <br/> |
|解决虚拟机连接和吞吐量问题  <br/> |||应用  <br/> |
   
## <a name="next-step"></a>后续步骤

[Microsoft 云连接的公共元素](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)



