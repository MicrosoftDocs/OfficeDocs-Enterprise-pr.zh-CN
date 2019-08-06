---
title: 实现适用于 Office 365 的 ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: 适用于 Office 365 的 ExpressRoute 提供了到多个面向 internet 的 Office 365 服务的备用路由路径。 适用于 Office 365 的 ExpressRoute 体系结构基于 Office 365 服务的广告公共 IP 前缀, 这些前缀已在 Internet 上可通过 Internet 访问, 以便随后将这些 IP 前缀再分发到你的网络。 通过 ExpressRoute, 可以有效地通过 internet 和 ExpressRoute 为许多 Office 365 服务启用几种不同的路由路径。 你的网络上的路由状态可能会对你的内部网络拓扑的设计进行重大更改。
ms.openlocfilehash: 3e3171c3058b485ef644af3f1d33a9f80c71345c
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "34722721"
---
# <a name="implementing-expressroute-for-office-365"></a>实现适用于 Office 365 的 ExpressRoute

适用于 Office 365 的 ExpressRoute 提供了到多个面向 internet 的 Office 365 服务的备用路由路径。 适用于 Office 365 的 ExpressRoute 体系结构基于 Office 365 服务的广告公共 IP 前缀, 这些前缀已在 Internet 上可通过 Internet 访问, 以便随后将这些 IP 前缀再分发到你的网络。 通过 ExpressRoute, 可以有效地通过 internet 和 ExpressRoute 为许多 Office 365 服务启用几种不同的路由路径。 你的网络上的路由状态可能会对你的内部网络拓扑的设计进行重大更改。
  
 **状态:** 完整指南 v2
  
您必须仔细规划您的 ExpressRoute for Office 365 实施, 以适应具有通过将路由插入到核心网络和 internet 的专用线路提供的网络复杂性。 如果您和您的团队不在本指南中执行详细的规划和测试, 则在启用 ExpressRoute 电路时, 会有一个高风险, 导致连接到 Office 365 服务的连接间歇或总丢失。
  
若要成功实施, 您需要分析基础结构要求, 了解详细的网络评估和设计, 仔细规划部署并以暂存和控制的方式, 并构建详细的验证和测试计划。 对于大型的分布式环境, 在几个月内查看实现情况并不常见。 本指南旨在帮助您提前进行规划。
  
大型成功部署可能需要六个月进行规划, 并且通常包含来自组织中的许多方面的团队成员, 包括网络、防火墙和代理服务器管理员、Office 365 管理员、安全性、最终用户支持、项目管理和执行赞助。 您在规划过程中的投资将降低您在宕机或复杂且成本高昂的故障排除方面遇到部署故障的可能性。
  
在启动本实施指南之前, 我们期望完成以下先决条件。
  
1. 你已完成网络评估, 以确定是否建议并批准 ExpressRoute。

2. 您已选择 ExpressRoute 网络服务提供商。 查找有关[ExpressRoute 合作伙伴和对等位置](https://azure.microsoft.com/documentation/articles/expressroute-locations/)的详细信息。

3. 您已阅读并理解[expressroute 文档](https://azure.microsoft.com/documentation/services/expressroute/), 并且您的内部网络能够满足 expressroute 先决条件端到端。

4. 您的团队已阅读频道9上的所有公共指南[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)和[https://aka.ms/ert](https://aka.ms/ert)文档, 并对[Azure ExpressRoute for Office 365 培训](https://channel9.msdn.com/series/aer)系列进行了跟踪, 以了解关键技术详细信息, 包括:

      - SaaS 服务的 internet 依赖项。

      - 如何避免非对称路由和处理复杂路由。

      - 如何合并外围安全、可用性和应用程序级别的控制。

## <a name="begin-by-gathering-requirements"></a>通过收集要求开始
<a name="requirements"> </a>

首先, 确定您计划在组织中采用哪些功能和服务。 您需要确定将使用不同的 Office 365 服务的功能以及网络上的哪些位置将使用这些功能承载用户。 在应用场景目录中, 需要添加每个方案所需的网络属性;如入站和出站网络流量流, 以及 Office 365 终结点是否可通过 ExpressRoute 使用。
  
若要收集组织的要求:
  
- 编录组织使用的 Office 365 服务的入站和出站网络流量。 有关不同 Office 365 方案所需流的说明, 请参阅 Office 365 Url 和 IP 地址范围页面。

- 收集现有网络拓扑的文档, 其中显示了内部 WAN 主干和拓扑的详细信息、卫星站点的连接、最后一次英里用户连接、路由到网络外围出口点和代理服务。

  - 标识网络关系图上的入站服务终结点, Office 365 和其他 Microsoft 服务将连接到, 同时显示 internet 和建议的 ExpressRoute 连接路径。

  - 确定位置之间的所有地理位置用户位置和 WAN 连接, 以及哪些位置当前有传出到 internet 以及哪些位置被建议将传出到 ExpressRoute 对等位置。

  - 确定所有边缘设备 (如代理、防火墙等), 并将它们的关系编录为通过 Internet 和 ExpressRoute 传输的流。

  - 记录最终用户是否将通过直接路由或间接应用程序代理访问 Internet 和 ExpressRoute 流的 Office 365 服务。

- 将租户和 "满足我的位置" 位置添加到网络图中。

- 估计从主要用户位置到 Office 365 的预期和观测的网络性能和延迟特征。 请注意, Office 365 是一组全局的分布式服务, 用户将连接到可能不同于其租户位置的位置。 出于此原因, 建议使用 ExpressRoute 和 Internet 连接衡量和优化用户与 Microsoft 全局网络最接近的边缘之间的延迟。 您可以使用网络评估中的发现来帮助执行此任务。

- 列出公司网络安全性和需要使用新的 ExpressRoute 连接所需满足的高可用性要求。 例如, 在 Internet 出口或 ExpressRoute 电路故障发生时, 用户如何继续获取 Office 365 的访问权限。

- 记录哪个入站和出站 Office 365 网络流将使用 Internet 路径, 并将使用 ExpressRoute。 你的用户的地理位置的具体信息以及你的本地网络拓扑的详细信息可能要求计划不同于一个用户位置。

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>对出站和入站网络流量进行编目
<a name="trafficCatalog"> </a>

为了最大限度地减少路由和其他网络复杂性, 我们建议您仅将 ExpressRoute 用于 Office 365, 以实现由于法规要求或网络评估结果而需要通过专用连接的网络流量流。 此外, 我们建议你暂存 ExpressRoute 路由的范围, 并将出站和入站网络流量流作为实施项目的不同和不同阶段。 部署适用于 Office 365 的 ExpressRoute 仅供用户启动的出站网络流量流并在 Internet 中留下入站网络流量流, 可帮助控制拓扑复杂性和引入额外的非对称的风险增加路由可能性。
  
您的网络流量目录应包含您在本地网络和 Microsoft 之间拥有的所有入站和出站网络连接的列表。
  
- 出站网络流量流是从本地环境 (如内部客户端或服务器) 使用 Microsoft 服务的目标启动连接的任何场景。 这些连接可以直接连接到 Office 365 或间接, 例如当连接通过代理服务器、防火墙或指向 Office 365 的路径上的其他网络设备时。

- 入站网络流量流是从 Microsoft 云中启动到本地主机的连接的任何场景。 这些连接通常需要经过防火墙和其他安全基础结构, 客户安全策略需要针对外部发起的流。

阅读[通过使用 ExpressRoute For office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)的文章路由的 "**确保路由对称**" 部分, 以确定哪些服务将发送入站流量, 并在 Office 365 中查找标记**为 ExpressRoute for Office 365**的列["终结点](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)参考" 文章, 以确定连接信息的其余部分。
  
对于每个需要出站连接的服务, 您需要描述服务的计划连接, 包括网络路由、代理配置、数据包检查和带宽需求。
  
对于每个需要入站连接的服务, 您都需要一些其他信息。 Microsoft 云中的服务器将建立与您的本地网络的连接。 若要确保正确建立了连接, 您需要描述此连接的各个方面, 包括;将接受这些入站连接的服务的公共 DNS 条目、CIDR 格式的 IPv4 IP 地址、涉及的 ISP 设备以及如何处理这些连接的入站 NAT 或源 NAT。
  
无论是通过 internet 还是 ExpressRoute 连接入站连接, 以确保未引入非对称路由, 应查看入站连接。 在某些情况下, Office 365 服务启动入站连接的本地终结点可能还需要由其他 Microsoft 和非 Microsoft 服务访问。 为实现针对 Office 365 的这些服务的 ExpressRoute 路由不会中断其他方案, 这一点非常重要。 在许多情况下, 客户可能需要对内部网络 (如基于源的 NAT) 实施特定的更改, 以确保启用 ExpressRoute 后来自 Microsoft 的入站流仍保持对称。
  
下面的示例展示了所需的详细信息级别。 在这种情况下, Exchange 混合将通过 ExpressRoute 路由到内部部署系统。

|**Connection 属性**|**值**|
|:-----|:-----|
|**网络流量方向** <br/> |进货  <br/> |
|**服务** <br/> |Exchange 混合  <br/> |
|**公共 Office 365 终结点 (源)** <br/> |Exchange Online (IP 地址)  <br/> |
|**公共本地终结点 (目标)** <br/> |5.5.5.5  <br/> |
|**公用 (Internet) DNS 条目** <br/> |Autodiscover.contoso.com  <br/> |
|**此本地终结点是否适用于其他 (非 Office 365) Microsoft 服务** <br/> |否  <br/> |
|**Internet 上的用户/系统是否使用此本地终结点** <br/> |是  <br/> |
|**通过公用终结点发布的内部系统** <br/> |Exchange Server 客户端访问角色 (本地) 192.168.101、192.168.102、192.168.103  <br/> |
|**公共终结点的 IP 广告** <br/> |**到 Internet**: 5.5.0.0/16  <br/> **到 ExpressRoute**: 5.5.5.0/24  <br/> |
|**安全性/外围控件** <br/> |**Internet 路径**: DeviceID_002  <br/> **ExpressRoute 路径**: DeviceID_003  <br/> |
|**高可用性** <br/> |跨2地域冗余的主动/主动  <br/> ExpressRoute 电路-芝加哥和达拉斯  <br/> |
|**路径对称控制** <br/> |**方法**: 源 NAT  <br/> **Internet 路径**: 源 NAT 到192.168.5.5 的入站连接  <br/> |**ExpressRoute 路径**: 源 NAT 与 192.168.1.0 (芝加哥) 和 192.168.2.0 (达拉斯) 的连接  <br/> |

以下是仅出站的服务示例:

|**Connection 属性**|**值**|
|:-----|:-----|
|**网络流量方向** <br/> |出站  <br/> |
|**服务** <br/> |SharePoint Online  <br/> |
|**内部部署终结点 (源)** <br/> |用户工作站  <br/> |
|**公共 Office 365 终结点 (目标)** <br/> |SharePoint Online (IP 地址)  <br/> |
|**公用 (Internet) DNS 条目** <br/> |\*. sharepoint.com (以及其他 Fqdn)  <br/> |
|**CDN 检索** <br/> |cdn.sharepointonline.com (和其他 Fqdn)-由 CDN 提供程序维护的 IP 地址  <br/> |
|**正在使用的 IP 播发和 NAT** <br/> |**Internet 路径/源 NAT**: 1.1.1.0/24  <br/> **ExpressRoute 路径/源 NAT**: 1.1.2.0/24 (芝加哥) 和 1.1.3.0/24 (达拉斯)  <br/> |
|**Connectivity 方法** <br/> |**Internet**: via 第7层代理 (pac 文件)  <br/> **ExpressRoute**: 直接路由 (无代理)  <br/> |
|**安全性/外围控件** <br/> |**Internet 路径**: DeviceID_002  <br/> **ExpressRoute 路径**: DeviceID_003  <br/> |
|**高可用性** <br/> |**Internet 路径**: 冗余 internet 出口  <br/> **ExpressRoute 路径**: 跨2个地理位置冗余的 expressroute 电路的主动/主动热刷路线-芝加哥和达拉斯  <br/> |
|**路径对称控制** <br/> |**方法**: 源 NAT 用于所有连接  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>区域连接的网络拓扑设计
<a name="topology"> </a>

了解服务及其关联的网络流量流后, 可以创建一个包含这些新的连接要求的网络图, 并说明将对 Office 365 使用 ExpressRoute 所做的更改。 您的图表应包括:
  
1. 将从其访问 Office 365 和其他服务的所有用户位置。

2. 所有 internet 和 ExpressRoute 出口点。

3. 管理网络中和外部连接的所有出站和入站设备, 包括路由器、防火墙、应用程序代理服务器和入侵检测/预防。

4. 所有入站流量的内部目标, 例如接受来自 ADFS web 应用程序代理服务器的连接的内部 ADFS 服务器。

5. 将公布的所有 IP 子网的目录

6. 确定用户将从其访问 Office 365 的每个位置, 并列出将用于 ExpressRoute 的 "满足我" 的位置。

7. 内部网络拓扑的位置和部分, 在其中将接受、筛选出从 ExpressRoute 获知的 Microsoft IP 前缀并将其传播到。

8. 网络拓扑应说明每个网段的地理位置以及它如何通过 ExpressRoute 和/或 Internet 连接到 Microsoft 网络。

下图显示了用户将使用 Office 365 的每个位置以及入站和出站路由播发到 Office 365。
  
![ExpressRoute 区域地理位置会见](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
对于出站流量, 人员通过以下三种方式之一访问 Office 365:
  
1. 通过北美地区的 "满足我的人员" 为加州的人员。

2. 通过中国香港地区的 "我的好友" 位置, 为香港地区的人员。

3. 在孟加拉的人较少, 并且未预配 ExpressRoute 电路的情况下通过 internet。

![区域图的出站连接](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
同样, Office 365 中的入站网络流量通过以下三种方式之一返回:
  
1. 通过北美地区的 "满足我的人员" 为加州的人员。

2. 通过中国香港地区的 "我的好友" 位置, 为香港地区的人员。

3. 在孟加拉的人较少, 并且未预配 ExpressRoute 电路的情况下通过 internet。

![区域图的入站连接](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>确定适当的 "符合我的位置" 位置

将您的 ExpressRoute 电路连接到 Microsoft 网络的位置的 "满足我的存储位置" 选择 "满足我的地理位置", 受用户从其访问 Office 365 的位置影响。 作为 SaaS 服务, Office 365 不在 IaaS 或 PaaS 区域模型下按照与 Azure 相同的方式运行。 相反, Office 365 是一组分布式服务, 在其中用户可能需要连接到多个数据中心和地区的终结点, 这可能不一定在承载用户租户的同一位置或区域中。
  
这意味着在为 Office 365 选择 "满足我的 ExpressRoute 的用户定位-我的位置" 时, 您需要做的最重要的考虑事项是组织中的人员将从其进行连接。 最佳 Office 365 连接的一般建议是实现路由, 以便通过最短网络路径将对 Office 365 服务的用户请求传递到 Microsoft 网络中, 这通常也称为 "热刷" 路由。 例如, 如果大多数 Office 365 用户位于一个或两个位置, 则选择 "符合我的位置" 与这些用户的位置最接近的位置将创建最佳设计。 如果贵公司在许多不同的地区拥有大量用户群体, 则您可能需要考虑拥有多个 ExpressRoute 电路和 "满足我" 的位置。 对于你的一些用户位置, Microsoft 网络和 Office 365 中的最短/最佳路径可能不是通过内部 WAN 和 ExpressRoute 符合我的网络点, 而是通过 Internet。
  
通常情况下, 可以在与用户相对邻近的区域中选择多个 "符合我的位置"。 填写下表以指导你的决定。

|**加利福尼亚和纽约的计划的 ExpressRoute 符合我的新位置**||
|:-----|:-----|
|位置  <br/> |人数  <br/> |Internet 出口的预期延迟到 Microsoft 网络  <br/> |通过 ExpressRoute 对 Microsoft 网络的预期延迟  <br/> |
|Los Angeles  <br/> |10,000  <br/> |~ 15ms  <br/> |~ 10ms (经由硅谷)  <br/> |
|华盛顿 DC  <br/> |15,000  <br/> |~ 20 毫秒  <br/> |~ 10ms (通过纽约)  <br/> |
|州  <br/> |5,000  <br/> |~ 15ms  <br/> |~ 40ms (通过纽约)  <br/> |

在显示 Office 365 区域、ExpressRoute 网络服务提供商 "满足我的位置" 和 "按位置的人员数量" 的全局网络体系结构已开发好之后, 可以使用它来确定是否可以进行优化。 它还可以显示全局发夹网络连接, 在此连接中, 流量路由到远处的位置以获取 "满足我的位置" 位置。 如果发现了全局网络上的发夹, 则应在继续操作之前对其进行修正。 请找到另一个 "网上邻居" 位置, 或使用 "选择性 Internet" 的出站点以避免发夹。
  
第一个图表显示了北美有两个物理位置的客户示例。 您可以查看有关 "office 位置"、"Office 365 租户" 位置以及针对 ExpressRoute "满足我" 位置的几个选项的信息。 在此示例中, 客户根据两个原则选择了 "符合我的位置", 顺序如下:
  
1. 与组织中的人员最接近的距离。

2. 最接近于 Microsoft 数据中心的位置, 其中承载 Office 365。

![ExpressRoute 美国地理位置-我](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
第二个图显示了一个包含类似信息和决策制定的多国客户的示例, 这一点更深入地进一步扩展了此概念。 此客户在孟加拉国中有一个小型办公室, 只有十个人的一小团队致力于在区域中增长其占用量。 在金奈中有一个 "满足我的位置" 和一个在金奈中托管 Office 365 的 Microsoft 数据中心, 因此 "满足我的位置" 将有意义;但是, 对于10人来说, 额外电路的费用是繁重的。 在查看网络时, 您需要确定在网络中发送网络流量所涉及的延迟是否比花费资金来获得另一个 ExpressRoute 电路更有效。
  
或者, 当我们的网络流量通过 internet 发送到 Microsoft 网络时, 孟加拉的10名人员可能会遇到更好的性能, 因为在介绍的规划图和复制过程中, 他们会在其内部网络上进行路由如下.
  
![区域图的出站连接](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>创建适用于 Office 365 实施计划的 ExpressRoute
<a name="implementation"> </a>

您的实施计划应包括配置 ExpressRoute 的技术详细信息, 以及在网络上配置所有其他基础结构的详细信息, 如下所示。
  
- 规划在 ExpressRoute 和 Internet 之间分割的服务。

- 规划带宽、安全性、高可用性和故障转移。

- 设计入站和出站路由, 包括针对不同位置的正确路由路径优化

- 确定将向您的网络中播发的 ExpressRoute 路由的距离, 以及客户端选择 Internet 或 ExpressRoute 路径的机制是什么;例如, 直接路由或应用程序代理。

- 规划 DNS 记录更改, 包括[发件人策略框架](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx)条目。

- 规划 NAT 策略, 包括出站源 NAT 和入站源 NAT。

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>使用 internet 和 ExpressRoute 网络路径规划路由
<a name="paths"> </a>

- 对于初始部署, 建议使用 internet 的所有入站服务 (如入站电子邮件或混合连接)。

- 规划最终用户客户端局域网路由, 例如[配置 PAC/WPAD 文件](https://aka.ms/manageo365endpoints)、默认路由、代理服务器和 BGP 路由播发。

- 规划外围路由, 包括代理服务器、防火墙和云代理。

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>规划带宽、安全性、高可用性和故障转移
<a name="availability"> </a>

制定针对每个主要 Office 365 工作负载所需的带宽的计划。 分别估计 Exchange Online、SharePoint Online 和 Skype for Business Online 带宽要求。 您可以使用我们为 Exchange Online 和 Skype for Business 提供的估计计算器作为开始位置;但是, 必须具有用户配置文件和位置的代表性示例的试点测试, 才能充分了解组织的带宽需求。
  
添加在每个 internet 和 ExpressRoute 出口位置处理安全性的方式在您的计划中, 记住到 Office 365 的所有 ExpressRoute 连接使用公共对等连接, 但仍必须按照与外部连接的公司安全策略进行安全保护networks.
  
向计划中添加有关哪些人将受到哪种类型的中断影响的详细信息, 以及这些人员如何能够以最简单的方式在完全容量内执行其工作的详细信息。
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>在抖动、延迟、拥塞和余地上规划包含 Skype for Business 要求的带宽要求
  
Skype for Business Online 还具有特定的其他网络要求, 这些要求在[Skype for Business online 中的文章媒体质量和网络连接性能](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)中进行了详细介绍。
  
阅读[使用 ExpressRoute For Office 365 的网络规划](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)中的**Azure ExpressRoute 的 "带宽规划**" 一节。
  
当你的试点用户执行带宽评估时, 你可以使用我们的指南;[使用基线和性能历史记录的 Office 365 性能优化](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)。
  
#### <a name="plan-for-high-availability-requirements"></a>规划高可用性要求
  
创建高可用性计划以满足您的需求, 并将其合并到更新后的网络拓扑图中。 [使用适用于 Office 365 的 ExpressRoute 在网络规划](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)中**使用 Azure ExpressRoute 的高可用性和故障转移**阅读部分。
  
#### <a name="plan-for-network-security-requirements"></a>规划网络安全要求
  
创建符合网络安全要求的计划, 并将其合并到更新后的网络拓扑图中。 阅读[使用 ExpressRoute For office 365 在网络规划](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)中**将安全控制应用于 Azure 365 ExpressRoute**的一节。
  
### <a name="design-outbound-service-connectivity"></a>设计出站服务连接
<a name="outbound"> </a>

适用于 Office 365 的 ExpressRoute 具有可能不熟悉的*出站*网络要求。 具体来说, 将用户和网络与 Office 365 表示的 IP 地址, 并充当到 Microsoft 的出站网络连接的源终结点, 必须遵循下面概述的特定要求。
  
1. 终结点必须是公共 IP 地址, 它们已注册到您的公司或提供与您的 ExpressRoute 连接的运营商。

2. 必须将终结点播发到 Microsoft 并通过 ExpressRoute 验证/接受这些终结点。

3. 不得将终结点公布到具有相同或更多首选路由指标的 Internet。

4. 终结点不得用于连接到未通过 ExpressRoute 配置的 Microsoft 服务。

如果您的网络设计不符合这些要求, 则您的用户将遇到由于路由黑色 holing 或非对称路由而导致的 Office 365 和其他 Microsoft 服务连接故障的高风险。 当通过 ExpressRoute 路由对 Microsoft 服务的请求时, 将发生这种情况, 但响应通过 internet 路由回来, 反之亦然, 并且这些响应被状态网络设备 (如防火墙) 丢弃。
  
您可以用来满足上述要求的最常用方法是使用源 NAT, 它可以作为网络的一部分实现, 也可以由您的 ExpressRoute 运营商提供。 源 NAT 允许你从 ExpressRoute 中抽象出 internet 网络的详细信息和专用 IP 寻址, 以及结合使用正确的 IP 路由播发, 提供一种简单的机制来确保路径对称。 如果要使用特定于 ExpressRoute 对等位置的有状态网络设备, 则必须为每个 ExpressRoute 对等项实现单独的 NAT 池, 以确保路径对称。
  
阅读有关[EXPRESSROUTE NAT 要求](https://azure.microsoft.com/documentation/articles/expressroute-nat/)的详细信息。
  
将出站连接的更改添加到网络拓扑图中。
  
### <a name="design-inbound-service-connectivity"></a>设计入站服务连接
<a name="inbound"> </a>

大多数企业 Office 365 部署假定从 Office 365 到本地服务的某种形式的入站连接, 如 Exchange、SharePoint 和 Skype for Business 混合方案、邮箱迁移和使用 ADFS 的身份验证基本. 当 ExpressRoute 在本地网络和 Microsoft 之间启用了其他路由路径以实现出站连接时, 这些入站连接可能会因非对称路由而意外受到影响, 即使您打算让这些流继续使用 Internet。 建议使用下面介绍的一些预防措施, 以确保从 Office 365 到本地系统的基于 Internet 的入站流无任何影响。
  
若要最大限度地降低对入站网络流量流的非对称路由风险, 所有入站连接都应先使用源 NAT, 然后再将源 NAT 路由到网络段, 从而将可见性路由到 ExpressRoute。 如果允许传入连接到在没有源 NAT 的 ExpressRoute 中具有路由可见性的网段, 则从 Office 365 发出的请求将从 internet 进入, 但返回到 Office 365 的响应将优先于 ExpressRoute返回到 Microsoft 网络的网络路径, 从而导致不对称路由。
  
您可以考虑采用以下实现模式之一来满足此要求:
  
1. 先执行源 NAT, 然后再使用网络设备 (例如防火墙) 或从 Internet 到本地系统的路径上的负载平衡器将请求路由到内部网络。

2. 确保 ExpressRoute 路由不会传播到入站服务 (如前端服务器或反向代理系统) 的网络段, 以处理 Internet 连接。

在网络中显式记帐这些方案, 并通过 Internet 保留所有入站网络通信流有助于最大限度地减少非对称路由的部署和操作风险。
  
在某些情况下, 您可能会选择通过 ExpressRoute 连接来指示某些入站流量。 在这些情况下, 请考虑以下其他注意事项。
  
1. Office 365 只能面向使用公共 Ip 的本地终结点。 这意味着, 即使内部部署入站终结点仅向基于 ExpressRoute 的 Office 365 公开, 仍需要与之关联的公用 IP。

2. Office 365 服务为解决本地终结点而执行的所有 DNS 名称解析均使用公用 DNS 进行。 这意味着, 您必须将入站服务终结点 "FQDN" 注册到 Internet 上的 IP 映射。

3. 为了通过 ExpressRoute 接收入站网络连接, 必须将这些终结点的公共 IP 子网公布到基于 ExpressRoute 的 Microsoft。

4. 仔细评估这些入站网络流量流, 以确保按照贵公司的安全和网络策略对其应用正确的安全和网络控制。

5. 一旦将本地入站终结点通过 ExpressRoute 播发到 Microsoft, ExpressRoute 将有效地成为所有 Microsoft 服务 (包括 Office 365) 的首选路由路径。 这意味着这些终结点子网必须仅用于与 Office 365 服务通信, 而不能用于 Microsoft 网络上的其他服务。 否则, 您的设计将导致非对称路由, 来自其他 Microsoft 服务的入站连接更愿意路由入站传入的 ExpressRoute, 而返回路径将使用 Internet。

6. 如果 ExpressRoute 电路或 "满足我的位置" 断开, 则需要确保本地入站终结点仍可在单独的网络路径上接受请求。 这可能意味着通过多个 ExpressRoute 电路为这些终结点公布子网。

7. 我们建议通过 ExpressRoute 为进入网络的所有入站网络流量应用源 NAT, 尤其是当这些流量流经各种状态的网络设备 (如防火墙) 时。

8. 某些本地服务 (例如 ADFS 代理或 Exchange 自动发现) 可能会收到来自 Internet 的 Office 365 服务和用户的入站请求。 对于这些请求, Office 365 将针对与 Internet 上的用户请求相同的 FQDN。 允许从 internet 到这些本地终结点的入站用户连接, 同时强制 Office 365 连接使用 ExpressRoute, 这表示显著的路由复杂性。 由于操作方面的考虑, 我们不建议大多数客户通过 ExpressRoute 实施此类复杂方案。 此额外的开销包括, 管理非对称路由的风险, 并且将要求您仔细管理跨多个维度的路由广告和策略。

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>更新网络拓扑计划以显示如何避免非对称路由
<a name="asymmetric"> </a>

您希望避免使用非对称路由, 以确保组织中的人员能够无缝使用 Office 365 以及 internet 上的其他重要服务。 客户有两个常见配置导致了非对称路由。 现在我们来回顾一下你计划使用的网络配置, 并检查是否可以存在其中一个非对称路由方案。
  
首先, 我们将研究与以下网络图相关联的几种不同情况。 在此图中, 接收入站请求的所有服务器 (如 ADFS 或内部部署混合服务器) 都位于新的 Jersey 数据中心, 并将公布到 internet。
  
1. 虽然外围网络是安全的, 但没有可用于传入请求的源 NAT。

2. 新 Jersey 数据中心中的服务器可以同时查看 internet 和 ExpressRoute 路由。

![ExpressRoute 连接概述](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
我们还提供了有关如何修复这些问题的建议。
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>问题 1: 云到 Internet 上的本地连接
  
下图说明了网络配置在 internet 上不提供来自 Microsoft 云的入站请求的 NAT 时所采用的非对称网络路径。
  
1. 来自 Office 365 的入站请求从公用 DNS 检索本地终结点的 IP 地址, 并将该请求发送到您的外围网络。

2. 在这种错误配置中, 未配置源 NAT 或在外围网络中提供通信, 这会导致实际源 IP 地址用作返回目标。

  - 网络上的服务器通过任何可用的 ExpressRoute 网络连接将返回流量路由到 Office 365。

  - 结果是该流到 Office 365 的一个非对称路径, 导致连接中断。

![ExpressRoute Asymetric 路由问题1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>解决方案 1a: 源 NAT
  
仅将源 NAT 添加到入站请求可解析此配置错误的网络。 在此图中：
  
1. 传入请求继续通过新 Jersey 数据中心的外围网络进行输入。 此时间源 NAT 可用。

2. 来自服务器的响应将发往与源 NAT 关联的 IP, 而不是原始 IP 地址, 从而导致响应沿相同的网络路径返回。

![ExpressRoute Asymetric 路由解决方案1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>解决方案 1b: 路由范围
  
或者, 您可以选择不允许公布 ExpressRoute BGP 前缀, 从而删除这些计算机的备用网络路径。 在此图中：
  
1. 传入请求继续通过新 Jersey 数据中心的外围网络进行输入。 这次, 从 Microsoft 通过 ExpressRoute 电路播发的前缀对新的 Jersey 数据中心不可用。

2. 来自服务器的响应将路由回与原始 IP 地址关联的 IP 地址, 而不是唯一的路由, 从而导致响应沿同一个网络路径返回。

![ExpressRoute Asymetric 路由解决方案2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>问题 2: 云到基于 ExpressRoute 的本地连接
  
下图显示了在网络配置不为来自 ExpressRoute 的 Microsoft 云中的入站请求提供 NAT 时所采用的非对称网络路径。
  
1. 来自 Office 365 的入站请求从 DNS 检索 IP 地址, 并将请求发送到您的外围网络。

2. 在这种错误配置中, 未配置源 NAT 或在外围网络中提供通信, 这会导致实际源 IP 地址用作返回目标。

  - 网络上的计算机通过任何可用的 ExpressRoute 网络连接将返回流量路由到 Office 365。

  - 结果是与 Office 365 的非对称连接。

![ExpressRoute Asymetric 路由问题2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>解决方案 2: 源 NAT
  
仅将源 NAT 添加到入站请求可解析此配置错误的网络。 在此图中：
  
1. 传入请求继续通过纽约数据中心的外围网络进入。 此时间源 NAT 可用。

2. 来自服务器的响应将发往与源 NAT 关联的 IP, 而不是原始 IP 地址, 从而导致响应沿相同的网络路径返回。

![ExpressRoute Asymetric 路由解决方案3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>纸张验证网络设计是否具有对称路径

在这种情况下, 您需要验证您的实施计划为您将使用 Office 365 的不同方案提供路由对称的纸张。 当某人使用服务的不同功能时, 您将确定应采取的特定网络路由。 从本地网络和 WAN 路由, 到外围设备, 再到连接路径;ExpressRoute 或 internet, 以及与在线终结点的连接。
  
您需要为之前标识为您的组织将采用的服务的所有 Office 365 网络服务执行此操作。
  
这有助于本白皮书通过第二个人的路由进行审核。 向其解释: 每个网络跃点都应从其获取下一个路由, 并确保您熟悉路由路径。 请注意, ExpressRoute 将始终提供到 Microsoft 服务器 IP 地址的更多作用域路由, 从而使路由开销低于 Internet 默认路由。
  
### <a name="design-client-connectivity-configuration"></a>设计客户端连接配置
<a name="asymmetric"> </a>

![将 PAC 文件与 ExpressRoute 结合使用](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
如果要将代理服务器用于 internet 绑定的流量, 则需要调整任何 PAC 或客户端配置文件, 以确保网络中的客户端计算机正确配置为将所需的 ExpressRoute 流量发送到 Office 365, 而不会使用 transiting代理服务器以及其余的流量 (包括一些 Office 365 流量) 将发送到相关代理。 阅读有关[管理 Office 365 端点](https://aka.ms/manageo365endpoints)的指南, 以获取有关 PAC 文件的示例。
  
> [!NOTE]
> 终结点经常发生变化, 每周经常发生变化。 您只应根据您的组织采用的服务和功能进行更改, 以减少所需的更改次数, 以确保保持最新。 请密切注意 RSS 源中的**生效日期**, 在该 rss 源中宣布了所做的更改, 并保留了所有过去的更改, 已发布的 IP 地址可能不会公布, 也不会从播发中删除, 直到达到生效日期为止。
  
## <a name="build-your-deployment-and-testing-procedures"></a>生成部署和测试过程
<a name="testing"> </a>

你的实施计划应包括测试和回滚规划。 如果您的实施未按预期运行, 则计划应设计为在发现问题之前影响最少人数。 以下是您的计划应考虑的一些高级别原则。
  
1. 暂存网络分段和用户服务的加入, 以最大限度地减少中断。

2. 规划使用 traceroute 和 TCP 连接从单独的 internet 连接主机测试路由。

3. 最好是在具有测试 Office 365 租户的独立测试网络上完成入站和出站服务的测试。

      - 或者, 如果客户尚未使用 Office 365 或在试点中, 则可以在生产网络上执行测试。

      - 此外, 还可以在仅为测试和监控而留出的生产中断期间执行测试。

      - 或者, 可以通过检查每个第3层路由器节点上每个服务的路由来完成测试。 仅当由于缺少物理测试带来风险而不可能进行其他测试时, 才应使用此回退。

### <a name="build-your-deployment-procedures"></a>生成部署过程

您的部署过程应分步向几个阶段中的小组成员进行测试, 然后再将其部署到更大的用户组中。 下面介绍了几种暂存部署的 ExpressRoute 的方法。
  
1. 使用 Microsoft 对等互连设置 ExpressRoute, 并将路由播发转发到单个主机, 仅用于暂存测试目的。

2. 首先, 将到 ExpressRoute 网络的播发路由到单个网段, 并按网段或区域展开路由广告。

3. 如果是首次部署 Office 365, 请将 ExpressRoute 网络部署用作针对少数用户的试点。

4. 如果使用代理服务器, 则还可以配置一个测试 PAC 文件, 以便在添加更多之前将少量用户引导到使用测试和反馈进行 ExpressRoute。

您的实施计划应列出必须采取的每个部署过程, 或者需要用于部署网络配置的命令。 当网络中断时间到达时, 所做的所有更改都应来自在提前和同行评审的已编写的部署计划。 请参阅我们关于 ExpressRoute 的技术配置的指南。
  
- 如果已更改任何将继续发送电子邮件的本地服务器的 IP 地址, 则更新 SPF TXT 记录。

- 如果您更改了 IP 地址以适应新的 NAT 配置, 则更新本地服务器的任何 DNS 条目。

- 确保已订阅 Office 365 终结点通知的 RSS 源, 以维护任何路由或代理配置。

在您的 ExpressRoute 部署完成后, 应执行测试计划中的过程。 应记录每个过程的结果。 您必须包括在测试计划结果指示实施未成功的情况中回滚到原始生产环境的过程。
  
### <a name="build-your-test-procedures"></a>生成测试过程

您的测试过程应包括每个用于 Office 365 的出站和入站网络服务的测试, 这两个都将使用 ExpressRoute, 而不是将使用的。 这些过程应包括从每个唯一的网络位置 (包括公司 LAN 中不在本地的用户) 进行测试。
  
测试活动的一些示例包括以下几个。
  
1. 从你的本地路由器 Ping 到你的网络操作员路由器。

2. 验证您的本地路由器是否收到 "500 + Office 365" 和 "CRM Online IP 地址" 广告。

3. 验证您的入站和出站 NAT 在 ExpressRoute 和内部网络之间是否运行。

4. 验证从你的路由器播发到你的 NAT 的路由。

5. 验证 ExpressRoute 是否已接受你的播发前缀。

      - 使用以下 cmdlet 验证对等通告:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. 验证您的公共 NAT IP 范围不会通过任何其他 ExpressRoute 或公共 Internet 网络电路公布给 Microsoft, 除非它是更大范围的特定子集, 如前面的示例中所示。

7. ExpressRoute 电路配对, 验证两个 BGP 会话是否都在运行。

8. 在 NAT 内部设置单个主机, 并使用 ping、tracert 和 tcpping 测试通过新线路连接到主机 outlook.office365.com 的连接。 此外, 还可以在镜像端口上使用 Wireshark 或 Microsoft 网络监视器3.4 等工具, 以验证是否能够连接到与 outlook.office365.com 关联的 IP 地址。

9. 测试 Exchange Online 的应用程序级功能。

  - 测试 Outlook 能够连接到 Exchange Online 和发送/接收电子邮件。

  - 测试 Outlook 能够使用联机模式。

  - 测试智能手机连接和发送/接收功能。

10. 测试 SharePoint Online 的应用程序级功能

  - 测试 OneDrive for Business 同步客户端。

  - 测试 SharePoint Online web 访问。

11. 测试 Skype for Business 呼叫方案的应用程序级功能:

  - 作为已通过身份验证的用户加入会议呼叫 [由最终用户启动的邀请]。

  - 邀请用户加入会议呼叫 [从 MCU 发送邀请]。

  - 使用 Skype for Business web 应用程序作为匿名用户加入会议。

  - 从有线电脑连接、IP 电话和移动设备加入呼叫。

  - 呼叫联合用户 o 对 PSTN 验证的呼叫: 呼叫已完成, 呼叫质量是可接受的, 连接时间是可接受的。

  - 验证是否已为租户和联合用户的两个成员更新联系人的状态状态。

### <a name="common-problems"></a>常见问题

非对称路由是最常见的实施问题。 下面是要查找的一些常见来源:
  
- 在没有源 NAT 的情况下使用开放或单层的网络路由拓扑。

- 不使用 SNAT 通过 internet 和 ExpressRoute 连接路由到入站服务。

- 在广泛部署之前, 不在测试网络上测试 ExpressRoute 上的入站服务。

## <a name="deploying-expressroute-connectivity-through-your-network"></a>通过网络部署 ExpressRoute 连接
<a name="testing"> </a>

一次将部署转移到网络的一个网段, 从而逐步推出与网络的不同部分的连接, 并为每个新网络分段回滚的计划。 如果您的部署与 Office 365 部署保持一致, 请首先部署到 Office 365 试点用户并从那里进行扩展。
  
首先为你的测试, 然后用于生产:
  
- 运行部署步骤以启用 ExpressRoute。

- 测试您看到的网络路由是预期的。

- 对每个入站和出站服务执行测试。

- 如果发现任何问题, 则回滚。

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>使用测试网络段设置与 ExpressRoute 的测试连接

现在, 你已完成了纸上的计划, 是时候要按小规模测试。 在此测试中, 将在本地网络上建立一个与 Microsoft 对等测试子网的单一 ExpressRoute 连接。 您可以使用与 test 子网的连接配置一个[试用版 Office 365 租户](https://go.microsoft.com/fwlink/p/?LinkID=403802), 并在测试子网中包含将在生产中使用的所有出站和入站服务。 为测试网段设置 DNS 并建立所有入站和出站服务。 执行测试计划并确保您熟悉每个服务和路由传播的路由。
  
### <a name="execute-the-deployment-and-test-plans"></a>执行部署和测试计划

完成上述项目后, 请查看已完成的区域, 并确保您和您的团队在执行部署和测试计划之前已对其进行了查看。
  
- 网络更改所涉及的出站和入站服务的列表。

- 显示 internet 出口和 ExpressRoute "符合我" 位置的全局网络体系结构图。

- 演示用于每个部署的服务的不同网络路径的网络路由图。

- 包含实施更改和回滚的步骤的部署计划 (如果需要)。

- 测试每个 Office 365 和网络服务的测试计划。

- 已完成对入站和出站服务的生产路由的纸张验证。

- 包含可用性测试的测试网段中的已完成测试。

选择一个足够长的中断时段来运行整个部署计划和测试计划, 可在需要时进行故障排除和回滚的时间。
  
> [!CAUTION]
> 由于在 internet 和 ExpressRoute 上路由的复杂性质, 建议在此窗口中添加额外的缓冲时间, 以处理复杂路由故障排除。
  
### <a name="configure-qos-for-skype-for-business-online"></a>为 Skype for business Online 配置 QoS

若要获取 Skype for business Online 的语音和会议优势, 必须具备 QoS。 在确保 ExpressRoute 网络连接不会阻止任何其他 Office 365 服务访问之后, 可以配置 QoS。 在[Skype For Business Online 中的 ExpressRoute 和 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)一文中介绍了 QoS 的配置。
  
## <a name="troubleshooting-your-implementation"></a>实现疑难解答
<a name="troubleshooting"> </a>

要查找的第一个位置是实施计划中是否错过了此实施指南中的步骤？ 返回并运行进一步的小型网络测试 (如果可能) 以复制错误并在该处进行调试。
  
确定测试过程中哪些入站或出站服务失败。 明确获取每个失败的服务的 IP 地址和子网。 继续执行并浏览纸张上的网络拓扑图, 并验证路由。 特别验证 ExpressRoute 路由的播发位置, 如果可能, 请在中断过程中测试该路由 (如果有跟踪)。
  
对每个客户终结点运行带网络跟踪的 PSPing, 并评估源和目标 IP 地址以验证它们是否符合预期。 对在端口25上公开的任何邮件主机运行 telnet, 并验证 SNAT 是否在预期的情况中隐藏原始源 IP 地址。
  
请记住, 在使用 ExpressRoute 连接部署 Office 365 时, 您需要确保对 ExpressRoute 的网络配置进行了优化设计, 并且还优化了网络上的其他组件 (如客户端计算机)。 除了使用此规划指南对可能错过的步骤进行故障排除外, 我们还编写了[Office 365 的性能故障排除计划](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c)。
  
以下是可以用于返回的简短链接：[https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>相关主题

[评估 Office 365 网络连接](assessing-network-connectivity.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 路由](routing-with-expressroute.md)
  
[ExpressRoute for Office 365 网络计划](network-planning-with-expressroute.md)
  
[在 ExpressRoute for Office 365 场景中使用 BGP 社区 (预览)](bgp-communities-in-expressroute.md)
  
[Skype for Business Online 中的媒体质量和网络连接性能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[优化 Skype for Business Online 网络](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype for Business Online 中的 ExpressRoute 和 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 的呼叫流](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)
  
[Office 365 性能疑难解答计划](performance-troubleshooting-plan.md)
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 网络和性能优化](network-planning-and-performance.md)
