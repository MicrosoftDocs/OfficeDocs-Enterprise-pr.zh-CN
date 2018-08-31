---
title: ExpressRoute for Office 365 网络规划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: Office 365 ExpressRoute 提供之间的第 3 层连接网络和 Microsoft 数据中心。电路使用 Office 365 的前端服务器的边框网关协议 (BGP) 路由的广告。从内部部署的设备的角度来看，当他们需要选择正确的 TCP/IP 路径到 Office 365 Azure ExpressRoute 被看作到 Internet 的替代项。
ms.openlocfilehash: 79cad16a619f048d1ba98b6058127f901211344d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539782"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>ExpressRoute for Office 365 网络规划

Office 365 ExpressRoute 提供之间的第 3 层连接网络和 Microsoft 数据中心。电路使用 Office 365 的前端服务器的边框网关协议 (BGP) 路由的广告。从内部部署的设备的角度来看，当他们需要选择正确的 TCP/IP 路径到 Office 365 Azure ExpressRoute 被看作到 Internet 的替代项。
  
Azure ExpressRoute 将直接路径添加到一组特定的受支持的功能和由 Microsoft 数据中心内的 Office 365 服务器提供的服务。Azure ExpressRoute 不替换 Internet 连接到 Microsoft 数据中心或基本 Internet 服务，如域名解析。Azure ExpressRoute 和 Internet 电路应安全和冗余。
  
下表重点介绍以下几点差异的 internet 和上下文中的 Office 365 的 Azure ExpressRoute 连接。

|**网络规划的差异**|**Internet 网络连接**|**ExpressRoute 网络连接**|
|:-----|:-----|:-----|
| 访问所需的 internet 服务，包括：  <br/>  DNS 名称解析  <br/>  证书吊销验证  <br/>  内容传递网络  <br/> |是  <br/> |向 Microsoft 请求拥有 DNS 和/或 CDN 基础结构可能使用 ExpressRoute 网络。  <br/> |
| 访问 Office 365 服务，包括：  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype for Business Online  <br/>  Office Online  <br/>  Office 365 门户和身份验证  <br/> |是，所有应用程序和功能  <br/> |是的[特定应用程序和功能](https://aka.ms/o365endpoints) <br/> |
|在部署外围安全。  <br/> |是  <br/> |是  <br/> |
|规划高可用性。  <br/> |故障转移到备用 internet 网络连接  <br/> |故障转移到的备用 ExpressRoute 连接  <br/> |
|与可预测的网络配置文件的直接连接。  <br/> |否  <br/> |是  <br/> |
|IPv6 连接。  <br/> |是  <br/> |是  <br/> |

展开标题下方的规划指南的更多网络。我们还录制 10 部分的公开跳水更深入地介绍[有关 Office 365 培训 Azure ExpressRoute](https://channel9.msdn.com/series/aer)系列。

## <a name="existing-azure-expressroute-customers"></a>现有的 Azure ExpressRoute 客户

如果您正在使用现有的 Azure ExpressRoute 电路，并且想要通过此电路添加 Office 365 连接，您应查看电路、 出口位置和大小电路以确保它们将满足您的 Office 365 使用的数量。大多数客户需要额外带宽，并且许多需要其他电路。
  
若要通过您现有的 Azure ExpressRoute 电路到 Office 365 的访问，请[配置路由筛选器](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)以确保 Office 365 服务进行访问。
  
Azure ExpressRoute 订阅是以中心，含义订阅与客户的客户。作为客户，您可以有多个 Azure ExpressRoute 电路，并可以通过这些电路访问许多 Microsoft 云资源。例如，您可以选择访问 Azure 通过冗余 Azure ExpressRoute 电路一对承载虚拟机的 Office 365 测试租户和 Office 365 生产租户。
  
此表列出了可以选择在电路通过实现的对等关系的两种类型。

|**对等关系**|**Azure 专用**|**Microsoft**|
|:-----|:-----|:-----|
|**服务** <br/> |IaaS: Azure 虚拟机  <br/> |PaaS: Azure 公共服务  <br/> Saas 与： Office 365  <br/> Saas 与： Dynamics 365  <br/> |
|连接初始 *** <br/> |客户-Microsoft  <br/> Microsoft 向客户  <br/> |客户-Microsoft  <br/> Microsoft 向客户  <br/> |
|**QoS 支持** <br/> |没有 QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup>QoS 此时仅支持业务 Skype。
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>规划 Azure ExpressRoute 带宽

每个 Office 365 客户在每个位置，它们是与 Office 365 每个应用程序，如使用内部部署或混合设备和网络的安全配置的其他因素活动具有独特的带宽需求，具体取决于的人数。
  
具有太小带宽将导致拥塞现象，重新传输的数据和不可预测的延迟。具有太多带宽将导致不必要的成本。在现有的网络带宽通常称为方面的可用空间量电路百分比。无 10%空间将可能导致拥塞，通常具有 80%空间意味着不必要的成本。典型的空间目标分配是 20%到 50%。
  
若要找到适当级别，最好机制是带宽的测试您现有的网络消耗。这是唯一的方法，则返回 true 命中的使用率，需要为每个网络配置和应用程序中唯一的一些方法。当测量您需要注意消耗的总带宽、 延迟和 TCP 拥塞了解您的网络需求。
  
一次您已包括所有网络应用程序，包括不同的配置文件的组织中的人员以确定实际使用，一小组试点 Office 365 预计的基准和两个度量值用于估计量您将需要为每个办事处的带宽。如果有任何延迟或您在测试中发现的 TCP 拥塞问题，您可能需要将出口接近移动到使用 Office 365 的人员或删除密集型网络，例如 SSL 解密/检查扫描。
  
我们建议使用网络处理哪些类型的建议的所有适用于 ExpressRoute 和 Internet 电路。同样适用于我们[性能优化网站](https://aka.ms/tune)上的指南的其余部分。
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>将安全控件的 Office 365 方案应用于 Azure ExpressRoute

保护 Azure ExpressRoute 连接开头保护 Internet 连接相同的准则。许多客户选择部署网络和外围控件沿其本地网络连接到 Office 365 和其他 Microsoft 云 ExpressRoute 路径。这些控件可能包括防火墙、 应用程序代理、 数据泄露，入侵检测、 入侵防御系统等。在许多情况下客户将控件的不同级别应用于从本地转到 Microsoft，而不从 Microsoft 转到客户的本地网络，而不是从本地转到常规启动通信量启动通信量启动的通信Internet 目标。
  
下面是与您选择部署[ExpressRoute connectivity 模型](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models)集成安全性的几个示例。

|**ExpressRoute 集成选项**|**网络安全外围模型**|
|:-----|:-----|
|在云交换中归置  <br/> |安装新或利用现有的安全/外围基础架构，其中建立 ExpressRoute 连接共同位置功能。  <br/> 利用共同位置实用程序仅仅是用于路由 interconnect 用途和后距离连接到本地安全/外围基础结构中的共同位置设施。  <br/> |
|点对点以太网  <br/> |终止中现有的本地安全/外围基础结构位置的点对点 ExpressRoute 连接。  <br/> 安装到 ExpressRoute 路径特定新安全/外围基础结构和终止的点对点连接。  <br/> |
|任意到任意 IPVPN  <br/> |利用现有的本地安全/外围基础结构到 Office 365 连接用于 ExpressRoute IPVPN 出口的所有位置。  <br/> 用于对 ExpressRoute 的 Office 365 到特定的内部部署位置 IPVPN 指定用作安全/外围发夹。  <br/> |

某些服务提供商还提供托管的安全外围功能与 Azure ExpressRoute 他们集成的解决方案的一部分。
  
在考虑为 ExpressRoute 用于 Office 365 连接的网络/安全外围选项的拓扑位置时，以下是其他注意事项
  
- 深度和类型网络/安全控件可能产生的性能和可伸缩性的 Office 365 用户体验的影响。

- 出站 (在-部署-\>Microsoft) 和入站 (Microsoft-\>本地) [如果启用] 流可能具有不同的要求。它们可能不同于出站到常规 Internet 目标。

- 是否通过 Office 365 ExpressRoute 或通过 Internet 路由流量，端口/协议和所需的 IP 子网的 office 365 要求都是相同的。

- 客户网络/安全控件的拓扑布置确定最终用户和 Office 365 服务之间的端到端网络，并且可以具有对网络延迟和拥塞的重大影响。

- 建议的 Office 365 设计用于带有 ExpressRoute 其安全/外围拓扑，按照冗余、 高可用性和灾难恢复的最佳实践的客户。

下面是与上面讨论的外围安全模型之间的比较不同的 Azure ExpressRoute 连接选项的 Woodgrove 银行的一个示例。
  
### <a name="example-1-securing-azure-expressroute"></a>示例 1： 保护 Azure ExpressRoute
  
Woodgrove 银行正在考虑部署 Azure ExpressRoute 以及规划的最佳体系结构[与 Office 365 ExpressRoute 路由](routing-with-expressroute.md)之后和之后使用上述指南以了解带宽要求，它们确定用于保护其外围的最佳方法。
  
Woodgrove，具有多个大洲中的位置的多个国家/地区组织的安全必须跨越所有外围环境。Woodgrove 的最佳连接选项是与服务的每个大陆中其员工需要在全球范围内的多个对等位置的多点连接。每个大陆包含冗余 Azure ExpressRoute 电路内洲和安全必须跨越所有这些。
  
Woodgrove 的现有基础结构可靠，并且可以处理其他工作，因此，Woodgrove 银行能够利用其 Azure ExpressRoute 和 internet 外围安全的基础结构。如果这不是这种情况，无法选择 Woodgrove 购买其他设备进行了补充其现有的设备或处理不同类型的连接。
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>高可用性和故障转移与 Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

我们建议设置从 ExpressRoute 与每个出口到 ExpressRoute 供应商的至少两个活动的电路。这是最常见的地方我们客户看到失败，您可以通过设置主动/主动 ExpressRoute 电路一对轻松地避免。因为许多 Office 365 服务仅可通过 Internet，我们还建议至少两个主动/主动 Internet 电路。
  
内部网络的出口点是许多其他设备和关键作用的人员如何感知可用性的电路。连接方案这些部分不涵盖 ExpressRoute 或 Office 365 服务级别协议，但它们在关键作用的端到端服务可用性中播放您的组织中的人员的角度。
  
关注的人员使用和运行 Office 365 中，如果的任何一个组件故障会影响人们的体验使用服务、 查找的方式来限制受影响的人员的总百分比。如果操作复杂的故障转移模式，考虑恢复很长时间人们的体验并查找哪些内容简单和自动故障转移模式。
  
外部网络、 Office 365、 ExpressRoute，和 ExpressRoute 提供程序，所有具有不同的可用性级别。
  
### <a name="service-availability"></a>服务可用性
  
- Office 365 服务将涵盖定义完善的[服务级别协议](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)，其中包括单个服务正常运行时间和可用性的指标。Office 365 可以维护此类高服务可用性级别是无缝地使用全局 Microsoft 网络许多 Microsoft 数据中心之间的故障转移的各个组件的原因之一。此故障转移的数据中心和网络从扩展到多个 Internet 出口点，并启用使用服务的人员的角度来看从无缝故障转移。

- ExpressRoute[提供 99.9%可用性 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) Microsoft 网络边缘和 ExpressRoute 提供商或合作伙伴基础结构之间的单个专用电路。这些服务级别于 ExpressRoute 电路级别的冗余的 Microsoft 设备和在每个对等位置的网络提供程序设备之间的[两个独立于互连](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)组成。

### <a name="provider-availability"></a>提供程序可用性
  
- 在您 ExpressRoute 提供商或合作伙伴处停止 Microsoft 的服务级别安排。这也是您可以选择将影响您的可用性级别的第一个位置。外围网络和在每个 Microsoft 对等位置的提供程序连接之间紧密应评估体系结构、 可用性和恢复能力 ExpressRoute 提供商提供的特征。请特别注意冗余、 对等设备提供的运营商 WAN 电路的逻辑和物理方面和任何其他值添加如 NAT 服务或托管的防火墙服务。

### <a name="designing-your-availability-plan"></a>设计您的可用性计划
  
我们强烈建议您规划和 Office 365 到您的端到端连接方案设计高可用性和恢复能力。设计应包括;
  
- 没有单点故障，包括 Internet 和 ExpressRoute 电路。

- 受影响的人员的数目和持续时间的影响的最预期失败模式，最小化。

- 优化从最预期失败模式的简单、 可重复的和自动恢复过程。

- 支持网络流量和冗余的路径，而不会大大降低通过功能的完整的需求。

连接方案应为到 Office 365 的多个独立并处于活动状态的网络路径优化网络拓扑。这将产生一个拓扑，以便仅适合在单独的设备或设备级别冗余比更好地端到端可用性。
  
> [!TIP]
> 如果您的用户分布在多个大洲或地理区域以及每个位置连接到单个 ExpressRoute 电路所在的单一本地位置冗余 WAN 电路通过您的用户将体验小于端到端服务可用性包括连接到最接近的对等的不同区域的独立 ExpressRoute 电路网络拓扑设计比位置。
  
我们建议设置与每个电路连接到与不同地理对等位置的至少两个 ExpressRoute 电路。应设置用户将使用 ExpressRoute 连接 for Office 365 服务的每个区域的电路此活动-活动的对。这将允许每个区域来影响如数据中心的主要位置或对等位置的灾难恢复期间保持连接。将其配置为主动/主动允许最终用户通信分布于多个网络路径。这会减少人员在设备或网络设备停机期间受影响的范围。
  
我们不建议使用 Internet 作为备份单个 ExpressRoute 电路。
  
### <a name="example-2-failover-and-high-availability"></a>示例 2： 故障转移和高可用性
  
Woodgrove 银行的多个地理设计都经过路由、 带宽、 安全性、 回顾，并且现在必须经过高可用性审阅。Woodgrove 认为有关作为介绍三种类别; 的高可用性恢复能力、 可靠性和冗余。
  
恢复能力允许 Woodgrove 快速从故障恢复。可靠性允许 Woodgrove 提供一致的结果在系统中。冗余允许 Woodgrove 的基础结构的一个或多个镜像实例之间移动。
  
每个边缘配置内, Woodgrove 具有冗余防火墙、 代理和 ID。北美，Woodgrove 都有其达拉斯数据中心中的一个边缘配置和其弗吉尼亚数据中心中的另一个边缘配置。在每个位置的冗余设备提供了到该位置的恢复能力。
  
基于几项主要原则构建在 Woodgrove 银行网络配置：
  
- 每个地理区域中有多个 Azure ExpressRoute 电路。

- 区域内的每个电路可以支持所有该区域中的网络流量。

- 路由将明确首选一项或可用性，位置，根据其他路径，依此类推。

- Azure ExpressRoute 电路之间进行故障转移自动发生无需其他配置或所需的 Woodgrove 的操作。

- Internet 电路之间进行故障转移自动发生无需其他配置或所需的 Woodgrove 的操作。

在此配置中，在物理和虚拟级别冗余 Woodgrove 银行是能够为本地恢复能力、 区域的恢复能力和全局恢复能力提供可靠的方式。Woodgrove 选择出现在评估每个区域，以及进行故障转移到 internet 的可能性单个 Azure ExpressRoute 电路此配置。
  
如果 Woodgrove 无法每个地区具有多个 Azure ExpressRoute 电路，路由到亚太地区中的 Azure ExpressRoute 电路源自北美的通信将添加不可接受级别的延迟和所需的 DNS 转发器配置增加复杂性。
  
利用备份配置为 internet 不建议。这将中断 Woodgrove 的可靠性原则，以此来使用连接不一致的体验。此外，手动配置都需要考虑 BGP 广告已配置的故障转移、 NAT 配置、 DNS 配置，和代理配置。这添加故障转移复杂性增加恢复的时间和减小其能够诊断和疑难解答所涉及的步骤。
  
仍有有关如何规划和实现流量管理或 Azure ExpressRoute 问题？我们[网络和性能指南](https://aka.ms/tune)或[Azure ExpressRoute 常见问题](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)的其余部分读取。
  
## <a name="working-with-azure-expressroute-providers"></a>使用 Azure ExpressRoute 提供程序
<a name="BKMK_high-availability"> </a>

选择基于您带宽、 延迟、 安全性和高可用性规划您电路的位置。一旦您知道您想要放置的最佳位置电路[查看当前区域的提供程序的列表](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。
  
使用您的提供程序或提供程序以选择最佳的连接选项，点对点的多点或托管。请记住，您可以混合和只要带宽和其他冗余组件支持您的路由和高可用性设计匹配连接选项。
  
这是一个简短的链接，您可以使用回来：[https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>相关主题
<a name="BKMK_high-availability"> </a>

[与 Office 365 的网络连接](network-connectivity.md)
  
[适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)
  
[ExpressRoute for Office 365 路由](routing-with-expressroute.md)
  
[实现 ExpressRoute for Office 365](implementing-expressroute.md)
  
[使用 Office 365 方案 (preview) 中 ExpressRoute BGP 社区 （英文）](bgp-communities-in-expressroute.md)
  
[媒体质量和 Skype 中的网络连接性能 for Business 联机](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[为业务 Online 的 Skype 优化您的网络](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute 和 Skype for Business Online 中的 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 呼叫流](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的性能疑难解答计划](performance-troubleshooting-plan.md)
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 网络和性能优化](network-planning-and-performance.md)
  
[Office 365 终结点常见问题](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
