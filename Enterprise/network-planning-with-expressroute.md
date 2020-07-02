---
title: 使用适用于 Office 365 的 ExpressRoute 进行网络规划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: 适用于 Office 365 的 ExpressRoute 在网络和 Microsoft 数据中心之间提供第3层连接。 电路使用 Office 365 前端服务器的边界网关协议（BGP）路由播发。 从本地设备的角度来看，当他们需要选择到 Office 365 的正确 TCP/IP 路径时，Azure ExpressRoute 被视为是 Internet 的替代方法。
ms.openlocfilehash: 56115e366d8f9b0bf7b4b893801ebca5d216c570
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998527"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>使用适用于 Office 365 的 ExpressRoute 进行网络规划

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

适用于 Office 365 的 ExpressRoute 在网络和 Microsoft 数据中心之间提供第3层连接。 电路使用 Office 365 前端服务器的边界网关协议（BGP）路由播发。 从本地设备的角度来看，当他们需要选择到 Office 365 的正确 TCP/IP 路径时，Azure ExpressRoute 被视为是 Internet 的替代方法。
  
Azure ExpressRoute 添加了指向由 Microsoft 数据中心内的 Office 365 服务器提供的一组特定支持的功能和服务的直接路径。 Azure ExpressRoute 不会将 Internet 连接替换为 Microsoft 数据中心或基本 Internet 服务（如域名解析）。 Azure ExpressRoute 和你的 Internet 电路应受到保护和冗余。
  
下表重点介绍了 Office 365 上下文中的 internet 和 Azure ExpressRoute 连接之间的一些差异。

|**网络规划的区别**|**Internet 网络连接**|**ExpressRoute 网络连接**|
|:-----|:-----|:-----|
| 访问所需的 internet 服务，包括;  <br/>  DNS 名称解析  <br/>  证书吊销验证  <br/>  内容分发网络  <br/> |是  <br/> |对 Microsoft 拥有的 DNS 和/或 CDN 基础结构的请求可能使用 ExpressRoute 网络。  <br/> |
| 对 Office 365 服务的访问权限，包括;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype for Business Online  <br/>  浏览器中的 Office  <br/>  Office 365 门户和身份验证  <br/> |是，所有应用程序和功能  <br/> |是，[特定的应用程序和功能](https://aka.ms/o365endpoints) <br/> |
|外围环境的本地安全性。  <br/> |是  <br/> |是  <br/> |
|高可用性规划。  <br/> |故障转移到备用 internet 网络连接  <br/> |故障转移到备用 ExpressRoute 连接  <br/> |
|与可预测网络配置文件的直接连接。  <br/> |否  <br/> |可访问  <br/> |
|IPv6 连接。  <br/> |是  <br/> |是  <br/> |

若要详细了解网络规划指南，请展开下面的标题。 我们还记录了10部分[Azure ExpressRoute For Office 365 培训](https://channel9.msdn.com/series/aer)系列，dives 更深入。

## <a name="existing-azure-expressroute-customers"></a>现有 Azure ExpressRoute 客户

如果使用的是现有 Azure ExpressRoute 电路，并且想要通过此线路添加 Office 365 连接，应查看电路的数量、出局位置和大小，以确保它们满足你的 Office 365 使用的需求。 大多数客户需要额外的带宽，并且许多客户需要额外的电路。
  
若要通过现有 Azure ExpressRoute 线路启用对 Office 365 的访问，请[配置路由筛选器](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)以确保 Office 365 服务可供访问。
  
Azure ExpressRoute 订阅是以客户为中心的，这意味着订阅与客户关联。 作为客户，你可以拥有多个 Azure ExpressRoute 电路，并且可以通过这些电路访问多个 Microsoft 云资源。 例如，可以选择通过一对冗余 Azure ExpressRoute 电路访问 Azure 托管虚拟机、Office 365 测试租户和 Office 365 生产租户。
  
此表概述了可以选择通过线路实施的两种类型的对等关系。

|**对等关系**|**Azure 专用**|**Microsoft**|
|:-----|:-----|:-----|
|**服务** <br/> |IaaS： Azure 虚拟机  <br/> |PaaS： Azure 公共服务  <br/> SaaS： Office 365  <br/> SaaS： Dynamics 365  <br/> |
|连接启动 * * * * <br/> |客户到 Microsoft  <br/> Microsoft 到客户  <br/> |客户到 Microsoft  <br/> Microsoft 到客户  <br/> |
|**QoS 支持** <br/> |无 QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup>目前，QoS 仅支持 Skype for Business。
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Azure ExpressRoute 的带宽规划

每个 Office 365 客户都有独特的带宽需求，具体取决于每个位置的人员数量、每个 Office 365 应用程序的活动情况以及使用内部部署或混合设备和网络安全配置等其他因素。
  
带宽过小将导致拥塞、数据重新传输以及不可预测的延迟。 带宽过多将导致不必要的成本。 在现有网络上，带宽通常以百分比形式在电路上的可用空间量方面进行引用。 拥有10% 的空间很可能导致拥塞，并且具有80% 的余地通常意味着不必要的成本。 典型的余地目标分配是20% 到50%。
  
若要查找正确的带宽级别，最好的机制是测试现有网络消耗。 这是在每个网络配置和应用程序以独特的方式实现的真正的使用和需要的唯一方法。 在测量时，需要密切注意总带宽消耗、延迟和 TCP 拥塞，以了解你的网络需求。
  
拥有包含所有网络应用程序的估计基准后，使用包含组织中人员的不同配置文件的小组的试点 Office 365，以确定实际使用情况，并使用这两个度量估计每个办公室位置所需的带宽量。 如果在测试中发现任何延迟或 TCP 拥塞问题，则可能需要将传出的距离移至使用 Office 365 的人员，或删除大量网络扫描（如 SSL 解密/检查）。
  
我们建议的所有建议的网络处理类型适用于 ExpressRoute 和 Internet 电路。 对于我们的[性能调整网站](https://aka.ms/tune)的其余指南，情况也是如此。
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>将安全控制应用于 Office 365 方案的 Azure ExpressRoute

确保 Azure ExpressRoute 连接的安全与保护 Internet 连接的原理相同。 许多客户选择将网络和外围控制以及将其本地网络连接到 Office 365 和其他 Microsoft 云的 ExpressRoute 路径进行部署。 这些控件可能包括防火墙、应用程序代理、数据泄露预防、入侵检测、入侵防护系统等。 在许多情况下，客户将不同级别的控制应用于从内部部署转到 Microsoft 的通信，而不是从 Microsoft 发送到客户本地网络的流量，而是从内部部署转到常规 Internet 目标的流量。
  
下面的示例展示了将安全性与您选择部署的[ExpressRoute 连接模型](https://docs.microsoft.com/azure/expressroute/expressroute-connectivity-models)相集成的几个示例。

|**ExpressRoute 集成选项**|**网络安全外围模型**|
|:-----|:-----|
|在云交换中归置  <br/> |在建立 ExpressRoute 连接的归置设施中安装新的或利用现有的安全/外围基础结构。  <br/> 充分利用仅用于路由/互连目的的归置功能，以及从归置设备到内部部署安全/外围基础结构的后部通信连接。  <br/> |
|点到点以太网  <br/> |终止现有本地安全/外围基础结构位置中的点到点 ExpressRoute 连接。  <br/> 安装特定于 ExpressRoute 路径的新安全/外围基础结构，并在此处终止点到点的连接。  <br/> |
|任意对任意 IPVPN  <br/> |充分利用现有的本地安全/外围基础结构，使其进入 IPVPN 的所有位置，用于实现用于 ExpressRoute 的 Office 365 连接。  <br/> 发夹用于 Office 365 的 ExpressRoute 的 IPVPN 分配给指定为安全/外围的特定本地位置。  <br/> |

一些服务提供商还提供托管安全/外围功能作为使用 Azure ExpressRoute 的集成解决方案的一部分。
  
在考虑用于用于适用于用于使用适用于用于 ExpressRoute 的适用于 Office 365 连接的网络/安全外围选项的拓扑放置时，以下是其他注意事项
  
- 网络/安全控制的深度和类型可能影响 Office 365 用户体验的性能和可伸缩性。

- 出站（本地- \> microsoft）和入站（microsoft \> 本地） [如果已启用] 流可能具有不同的要求。 它们可能与常规 Internet 目标的出站不同。

- 对于端口/协议和必需的 IP 子网，Office 365 的要求与通过 ExpressRoute 为 Office 365 或通过 Internet 路由通信的情况相同。

- 客户网络/安全控制的拓扑放置决定了用户与 Office 365 服务之间的最终到端网络，并且可能会对网络延迟和拥塞产生重大影响。

- 鼓励客户根据冗余性、高可用性和灾难恢复的最佳做法，设计其安全/外围拓扑以与适用于 Office 365 的 ExpressRoute 结合使用。

下面是一个 Woodgrove Bank 示例，它将不同的 Azure ExpressRoute 连接选项与上面讨论的外围安全模型进行比较。
  
### <a name="example-1-securing-azure-expressroute"></a>示例1：保护 Azure ExpressRoute
  
Woodgrove Bank 正在考虑实现 Azure ExpressRoute，并在规划最佳体系结构以实现针对[Office 365 的 ExpressRoute 路由](routing-with-expressroute.md)，并在使用上述指导以了解带宽要求之后，确定用于保护其外围环境的最佳方法。
  
对于 Woodgrove （具有多个洲的多国组织），安全性必须跨越所有外围环境。 Woodgrove 的最佳连接选项是与全球各地的多个对等位置的多点连接，可满足每个洲的员工的需求。 每个洲在洲中包含冗余的 Azure ExpressRoute 电路，安全性必须涵盖所有这些电路。
  
Woodgrove 的现有基础结构是可靠的，并且可以处理额外的工作，因此，Woodgrove Bank 能够将基础结构用于其 Azure ExpressRoute 和 internet 外围安全性。 如果不是这样，Woodgrove 可以选择购买其他设备来补充其现有设备或处理不同类型的连接。
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Azure ExpressRoute 的高可用性和故障转移
<a name="BKMK_high-availability"> </a>

我们建议将每个传出的活动电路至少设置为 ExpressRoute 提供程序。 这是我们看到客户失败的最常见的地方，您可以通过设置一对主动/主动 ExpressRoute 电路来轻松地避免这一对。 我们还建议至少两个主动/主动 Internet 电路，因为许多 Office 365 服务仅在 Internet 上可用。
  
在网络的出局点内，还有许多其他设备和电路，它们在人们如何感觉可用性方面扮演着关键角色。 这些部分的连接方案不受 ExpressRoute 或 Office 365 Sla 的涵盖，但它们在端到端服务可用性方面起着重要作用，如组织中的人员所感知。
  
重点关注使用和操作 Office 365 的人员。如果任何一个组件的失败都会影响人员使用服务的体验，请查看限制受影响的人员总数百分比的方法。 如果故障转移模式在操作上很复杂，请考虑使用体验很长时间才能进行恢复，并查找操作简单且自动的故障转移模式。
  
在网络外部，Office 365、ExpressRoute 和 ExpressRoute 提供程序都具有不同级别的可用性。
  
### <a name="service-availability"></a>服务可用性
  
- Office 365 服务受明确定义的[服务级别协议](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)的涵盖，其中包括各个服务的正常运行时间和可用性指标。 Office 365 可以维护这样的高可用性级别的一个原因是，单个组件能够在多个 Microsoft 数据中心之间使用全局 Microsoft 网络无缝地进行故障转移。 此故障转移将从数据中心和网络扩展到多个 Internet 出局点，并通过使用该服务的人员的角度无缝地进行故障转移。

- ExpressRoute 在 Microsoft 网络边缘与 ExpressRoute 提供程序或合作伙伴基础结构之间的各个专用线路上[提供了99.9% 的可用性 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) 。 这些服务级别在 ExpressRoute 电路级别应用，这由每个对等位置中的冗余 Microsoft 设备和网络提供商设备之间的[两个独立互连](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)组成。

### <a name="provider-availability"></a>提供程序可用性
  
- Microsoft 的服务级别排列在你的 ExpressRoute 提供程序或合作伙伴处停止。 这也是可以做出影响可用性级别的选择的第一个位置。 您应仔细评估您的 ExpressRoute 提供商在每个 Microsoft 对等位置上的网络外围和提供程序连接之间提供的体系结构、可用性和恢复性特征。 请密切注意冗余和物理方面的冗余、对等设备、运营商提供的 WAN 电路以及任何其他价值添加服务（如 NAT 服务或托管防火墙）。

### <a name="designing-your-availability-plan"></a>正在设计可用性计划
  
强烈建议您规划和设计适用于 Office 365 的端到端连接方案的高可用性和弹性。 设计应包括;
  
- 无单点故障，包括 Internet 和 ExpressRoute 电路。

- 最大程度地减少受影响的人员数量和对最预期的故障模式造成的影响的持续时间。

- 从最预期的故障模式优化简单、可重复和自动恢复过程。

- 通过冗余路径支持网络流量和功能的全部需求，而不会显著降低。

连接方案应包含为 Office 365 的多个独立和主动网络路径优化的网络拓扑。 这将比仅针对单个设备或设备级别的冗余而优化的拓扑相比，提供了更好的端到端可用性。
  
> [!TIP]
> 如果您的用户分布在多个洲或地理位置，并且这些位置中的每个位置都将通过冗余 WAN 电路连接到单个 ExpressRoute 电路所在的单个内部部署位置，则您的用户将体验到端到端的服务可用性低于网络拓扑设计，其中包括将不同区域连接到最近的对等位置的独立 ExpressRoute 电路。
  
我们建议为每个电路至少预配两个与不同地理位置对等位置相连的 ExpressRoute 电路。 应为每个用户使用适用于 Office 365 服务的 ExpressRoute 连接的区域设置这一对主动-主动的电路。 这样一来，每个区域都可以在发生灾难时保持连接，以影响一个主要位置，如数据中心或对等位置。 将它们配置为主动/主动，可以跨多个网络路径分布最终用户通信。 这样可以减少设备或网络设备中断期间受影响的人员的范围。
  
我们建议您不要将单个 ExpressRoute 电路与 Internet 作为备份使用。
  
### <a name="example-2-failover-and-high-availability"></a>示例2：故障转移和高可用性
  
Woodgrove 银行的多地理位置设计已完成路由、带宽、安全性的审查，现在必须进行高可用性审查。 Woodgrove 认为有三种类别的高可用性;恢复能力、可靠性和冗余。
  
通过弹性，Woodgrove 可以快速从故障中恢复。 可靠性使 Woodgrove 能够在系统中提供一致的结果。 通过冗余，Woodgrove 可以在基础结构的一个或多个镜像实例之间移动。
  
在每个边缘配置中，Woodgrove 都有冗余的防火墙、代理和 ID。 对于北美，Woodgrove 在其达拉斯数据中心中有一个边缘配置，在其弗吉尼亚数据中心中有另一个边缘配置。 每个位置的冗余设备可为该位置提供恢复能力。
  
Woodgrove Bank 上的网络配置基于几个关键原则构建：
  
- 在每个地理区域内，有多个 Azure ExpressRoute 电路。

- 区域中的每个电路都可以支持该区域中的所有网络流量。

- 路由将明确考虑使用一个或另一个路径，具体取决于可用性、位置等。

- Azure ExpressRoute 电路之间的故障转移会自动发生，而 Woodgrove 不需要其他配置或操作。

- Internet 电路之间的故障转移会自动发生，而 Woodgrove 不需要其他配置或操作。

在此配置中，在物理和虚拟级具有冗余，Woodgrove Bank 能够以可靠的方式提供本地恢复能力、区域恢复能力和全局恢复能力。 Woodgrove 在评估每个地区的单个 Azure ExpressRoute 电路以及故障转移到 internet 的可能性之后选择此配置。
  
如果 Woodgrove 无法为每个地区提供多个 Azure ExpressRoute 电路，则将来自北美的流量路由到亚太地区的 Azure ExpressRoute 电路将添加不可接受的延迟级别和所需的 DNS 转发器配置增加了复杂性。
  
建议不要将 internet 用作备份配置。 这将中断 Woodgrove 的可靠性原则，从而导致使用连接时体验不一致。 此外，还需要手动配置，以确保已配置的 BGP 播发、NAT 配置、DNS 配置和代理配置的故障转移。 这种增加的故障转移复杂性增加了恢复时间并降低了其诊断和解决步骤所涉及步骤的能力。
  
是否仍有关于如何规划和实现流量管理或 Azure ExpressRoute 的问题？ 阅读我们的[网络和性能指南](https://aka.ms/tune)的其余部分或[Azure ExpressRoute 常见问题解答](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。
  
## <a name="working-with-azure-expressroute-providers"></a>使用 Azure ExpressRoute 提供程序
<a name="BKMK_high-availability"> </a>

根据带宽、延迟、安全性和高可用性规划选择你的电路的位置。 知道要放置电路的最佳位置之后，将[按地区查看当前的提供商列表](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。
  
与提供程序或提供程序配合使用，以选择最佳连接选项、点对点、多点或托管。 请记住，只要带宽和其他冗余组件支持您的路由和高可用性设计，您就可以混合和匹配连接选项。
  
以下是可以用于返回的简短链接：[https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>相关主题
<a name="BKMK_high-availability"> </a>

[评估 Office 365 网络连接](assessing-network-connectivity.md)
  
[适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 路由](routing-with-expressroute.md)
  
[实现 ExpressRoute for Office 365](implementing-expressroute.md)
  
[在 ExpressRoute for Office 365 场景中使用 BGP 社区（预览）](bgp-communities-in-expressroute.md)
  
[Skype for Business Online 中的媒体质量和网络连接性能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[优化 Skype for Business Online 网络](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype for Business Online 中的 ExpressRoute 和 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 的呼叫流](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)
  
[Office 365 性能疑难解答计划](performance-troubleshooting-plan.md)
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 网络和性能优化](network-planning-and-performance.md)
  
[Office 365 终结点 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
