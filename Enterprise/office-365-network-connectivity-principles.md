---
title: Office 365 网络连接原则
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/14/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
description: 在开始规划网络的 office 365 网络连接之前, 请务必了解安全管理 office 365 流量和获得最佳性能的连接原则。本文将帮助您了解有关安全优化 Office 365 网络连接的最新指南。
ms.openlocfilehash: 3dfb0732ff15c7d8f3c20ac659f94b8d807afa07
ms.sourcegitcommit: fd137a68c516379a9f09e06987e8d45d92de7ed6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/27/2019
ms.locfileid: "30303616"
---
# <a name="office-365-network-connectivity-principles"></a>Office 365 网络连接原则

在开始规划网络的 office 365 网络连接之前, 请务必了解安全管理 office 365 流量和获得最佳性能的连接原则。本文将帮助您了解有关安全优化 Office 365 网络连接的最新指南。
  
传统的企业网络主要用于向用户提供对公司运营数据中心内托管的应用程序和数据的访问, 具有强大的外围安全机制。传统模型假定用户将从公司网络外围、来自分支机构的 WAN 链接或通过 VPN 连接的远程访问应用程序和数据。 
  
采用 SaaS 应用程序 (如 Office 365) 会在网络外围之外移动一些服务和数据组合。如果不进行优化, 用户和 SaaS 应用程序之间的流量将受到数据包检查、网络回流、无意连接到地理位置较远的终结点和其他因素所引入的延迟的影响。您可以通过了解和实现关键优化准则来确保最佳的 Office 365 性能和可靠性。
  
在本文中, 您将了解以下内容:
  
- 适用于客户与云的连接的[Office 365 体系结构](office-365-network-connectivity-principles.md#BKMK_Architecture)
- 更新了用于优化网络流量和最终用户体验的[Office 365 连接原则](office-365-network-connectivity-principles.md#BKMK_Principles)和策略
- [Office 365 终结点 web 服务](office-365-network-connectivity-principles.md#BKMK_WebSvc), 该服务允许网络管理员使用在网络优化中使用的终结点的结构化列表
- [新的 Office 365 终结点类别](office-365-network-connectivity-principles.md#BKMK_Categories)和优化指南
- [将网络外围安全性与终结点安全性进行比较](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Office 365 流量的[增量优化](office-365-network-connectivity-principles.md#BKMK_IncOpt)选项

## <a name="office-365-architecture"></a>Office 365 体系结构
<a name="BKMK_Architecture"> </a>

Office 365 是分布式软件即服务 (SaaS) 云, 它通过多种微服务和应用程序 (如 Exchange online、SharePoint online、Skype for business Online、Microsoft) 提供工作效率和协作方案。团队、Exchange Online Protection、Office Online 和许多其他团队。虽然特定的 Office 365 应用程序可能会将其独特的功能应用于客户网络和与云的连接, 但它们都共享一些关键主体、目标和体系结构模式。这些适用于连接的这些主体和体系结构模式对于许多其他 SaaS 云来说是典型的, 同时与平台即服务和基础结构即服务云 (如 Microsoft) 的典型部署模型非常不同。Azure.
  
Office 365 的最重要的体系结构功能之一 (通常是网络规划者未错过或误解的) 是, 它是真正的全局分布式服务, 在用户连接到它的上下文中。目标 Office 365 租户的位置对于了解在云中存储客户数据的位置非常重要, 但 Office 365 的用户体验并不涉及直接连接到包含数据的磁盘。Office 365 中的用户体验 (包括性能、可靠性和其他重要质量特征) 涉及到跨全球数百个 Microsoft 地区扩展的高分布式服务前盖的连接性。在大多数情况下, 通过允许客户网络将用户请求路由到最近的 office 365 服务入口点来实现最佳用户体验, 而不是通过中心位置或区域中的传出点连接到 office 365。
  
对于大多数客户, Office 365 用户分布在多个位置。为获得最佳结果, 本文档中概述的原则应从向外扩展 (不向上扩展) 的角度来看, 重点是在将连接优化到 Microsoft 全局网络中的最近状态点, 而不是地理位置Office 365 租户的位置。实际上, 这意味着尽管 office 365 租户数据可能存储在特定的地理位置, 但该租户的 office 365 体验仍在分发中, 并且可以在非常接近 (网络) 的情况下在租户拥有的每个最终用户位置进行接近.
  
## <a name="office-365-connectivity-principles"></a>Office 365 连接原则
<a name="BKMK_Principles"> </a>

Microsoft 建议采用以下原则来实现最佳的 Office 365 连接和性能。使用这些 office 365 连接原则来管理流量, 并在连接到 Office 365 时获得最佳性能。
  
网络设计中的主要目标是通过将网络中的往返时间 (RTT) 减少到 microsoft 全局网络中来最大限度地减少延迟, microsoft 的公共网络骨干将所有 Microsoft 的数据中心与低延迟互连在一起和云应用程序入口点分布在世界各地。你可以在[microsoft 如何构建其快速可靠的全局网络](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)中了解有关 microsoft 全球网络的详细信息。
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-office-365-traffic"></a>识别和区分 Office 365 流量

![确定 Office 365 流量](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
若要能够区分来自通用 Internet 绑定网络流量的通信, 第一步是确定 Office 365 网络流量。可以通过实现网络路由优化、防火墙规则、浏览器代理设置以及针对特定终结点的网络检查设备旁路等方法的组合来优化 Office 365 连接。
  
以前的 office 365 优化指南将 Office 365 终结点分为两个类别, "**必需**" 和 "**可选**"。由于添加终结点以支持新的 Office 365 服务和功能, 我们已将 Office 365 终结点重新组织为三个类别:**优化**、**允许**和**默认**。每个类别的准则适用于类别中的所有终结点, 使优化更易于理解和实现。 
  
有关 Office 365 终结点类别和优化方法的详细信息, 请参阅 "[新建 Office 365 终结点类别](office-365-network-connectivity-principles.md#BKMK_Categories)" 部分。
  
Microsoft 现在将所有 Office 365 终结点作为 web 服务发布, 并提供有关如何使用此数据的最佳指南。有关如何提取和使用 office 365 终结点的详细信息, 请参阅文章: [office 365 url 和 IP 地址范围](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US)。
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>实现本地连接出口

![实现本地连接出口](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
在减少连接延迟和确保用户连接到 Office 365 服务的最接近入口点时, 本地 DNS 和 Internet 出口非常重要。在复杂的网络拓扑中, 一定要将本地 DNS 和本地 Internet 出口同时实现。有关 Office 365 如何将客户端连接路由到最近的入口点的详细信息, 请参阅[客户端连接](https://support.office.com/en-us/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)一文。
  
在云服务 (如 Office 365) 出现之前, 作为网络体系结构中设计因素的最终用户 Internet 连接相对简单。在全球范围内分布 Internet 服务和网站时, 公司传出点和任何给定目标终结点之间的延迟主要是地理距离的功能。
  
在传统网络体系结构中, 所有出站 Internet 连接都通过公司网络, 并从一个中心位置传出。随着 Microsoft 的云产品产品的成熟, 面向 Internet 的分布式网络体系结构已成为支持延迟敏感云服务的关键。Microsoft 全球网络旨在适应分布式服务前端基础结构的延迟要求, 这是全局入口点的动态结构, 用于将传入的云服务连接路由到最接近的入口点。这旨在通过有效缩短客户与云之间的路线来缩短 Microsoft 云客户的 "last 英里" 的长度。
  
企业 wan 通常用于将网络通信 backhaul 到中心公司总部, 以便在出口到 Internet 之前进行检查, 通常通过一个或多个代理服务器进行检查。下图说明了此类网络拓扑。
  
![传统企业网络模型](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
由于 Office 365 在 Microsoft 全球网络 (包括世界各地的前端服务器) 上运行, 因此通常会有前端服务器靠近用户的位置。通过提供本地 Internet 出口和配置内部 DNS 服务器以提供 office 365 终结点的本地名称解析, 为 office 365 发送的网络通信可以连接到 office 365 前端服务器, 尽可能地接近用户。下图显示了一个网络拓扑示例, 该网络拓扑允许从主办公室、分支机构和远程位置连接的用户遵循最短到最接近的 office 365 入口点的路由。
  
![区域出口点的 WAN 网络模型](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
以这种方式缩短到 office 365 入口点的网络路径可提高连接性能和 office 365 中的最终用户体验, 还有助于降低对 office 365 性能的未来更改对网络体系结构的影响和原因.
  
此外, 如果响应的 DNS 服务器繁忙或繁忙, 则 DNS 请求可能会导致延迟。您可以通过在分支位置设置本地 DNS 服务器并确保将其配置为适当地缓存 DNS 记录, 从而最大限度地减少名称解析延迟。
  
虽然区域出口可适用于 Office 365, 但最佳连接模型是始终提供用户位置的网络出口, 无论是在公司网络上还是在远程位置 (例如, 家庭、旅馆、咖啡店和等.此本地直接出口模型在下图中表示。
  
![本地出口网络体系结构](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
采用 Office 365 的企业可以利用 Microsoft 全球网络的分布式服务前端体系结构, 具体方法是确保与 Office 365 的用户连接采用最短的可能路由到最近的 Microsoft 全局网络条目鼠标.本地出局网络体系结构通过允许将 Office 365 流量路由到最近的传出而不考虑用户位置来实现这一点。
  
与传统模型相比, 本地出口体系结构具有以下优点:
  
- 通过优化路由长度提供最佳的 Office 365 性能。最终用户连接通过分布式服务前端基础结构动态路由到最接近的 Office 365 入口点。
- 通过允许本地出口降低公司网络基础结构的负载。
- 通过利用客户端终结点安全性和云安全功能来保护两端的连接。

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>避免网络发卡

![避免回流](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
作为一般经验法则, 用户与最接近的 Office 365 终结点之间最短、最直接的路由将提供最佳性能。当为特定目标绑定的 WAN 或 VPN 流量首先定向到另一个中间位置 (例如, 基于云的 web 网关的安全堆栈、云访问代理) 时, 将发生网络发夹, 引入延迟并可能重定向到地理位置较远的端点。网络回流也可能是由路由/对等低效率或不理想 (远程) DNS 查找引起的。
  
若要确保即使在本地出口的情况下, Office 365 连接不受网络回流, 请检查用于为用户位置提供 Internet 出口的 ISP 是否与关闭的 Microsoft 全局网络具有直接的对等关系与该位置的距离。您可能还希望将传出路由配置为直接发送受信任的 Office 365 通信, 而不是通过处理 Internet 绑定流量的第三方云或基于云的网络安全供应商进行代理或隧道操作。office 365 终结点的本地 DNS 名称解析有助于确保除了直接路由, 最接近的 Office 365 入口点也用于用户连接。
  
如果您将基于云的网络或安全服务用于 Office 365 流量, 请确保评估 hairpinning 效果并了解其对 office 365 性能的影响。为此, 可以检查通过以下方式将流量转发到的服务提供程序位置的数量和位置: 与分支机构的数量和 Microsoft 全局网络对等点的网络对等关系的质量您的 ISP 和 Microsoft 的服务提供商以及回程在服务提供程序基础结构中的性能影响。
  
由于 office 365 入口点和与最终用户邻近的大量分布式位置, 因此将 office 365 流量路由到任何第三方网络或安全提供商可能会对 office 365 连接产生不利影响 (如果提供程序网络不是配置为最佳的 Office 365 对等。
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>评估绕过代理、流量检查设备和重复的安全技术

![绕过代理、流量检查设备和重复的安全技术](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
企业客户应查看其网络安全和风险降低方法, 专门针对 Office 365 绑定的流量, 并使用 Office 365 安全功能来降低对入侵、性能影响和成本较高的网络安全的依赖适用于 Office 365 网络流量的技术。
  
大多数企业网络使用代理、SSL 检查、数据包检查和数据丢失防护系统等技术强制 Internet 流量的网络安全。这些技术为常规 Internet 请求提供了重要风险缓解, 但在应用于 Office 365 终结点时, 可以显著降低性能、可伸缩性和最终用户体验的质量。
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Office 365 终结点 web 服务

office 365 管理员可以使用脚本或 REST 调用从 Office 365 终结点 web 服务使用终结点的结构化列表, 并更新外围防火墙和其他网络设备的配置。这将确保为 Office 365 绑定的流量进行了标识, 并进行了适当的处理, 并与绑定到一般和通常未知 Internet 网站的网络流量进行了不同的管理。有关如何使用 office 365 终结点 web 服务的详细信息, 请参阅文章: [office 365 url 和 IP 地址范围](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US)。
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC (代理自动配置) 脚本
<a name="BKMK_WebSvc"> </a>

Office 365 管理员可以创建可通过 WPAD 或 GPO 传递给用户计算机的 PAC (代理自动配置) 脚本。PAC 脚本可用于绕过来自 WAN 或 VPN 用户的 office 365 请求的代理, 从而允许 office 365 通信使用直接 Internet 连接, 而不是遍历公司网络。
  
#### <a name="office-365-security-features"></a>Office 365 安全功能
<a name="BKMK_WebSvc"> </a>

Microsoft 对数据中心安全性、操作安全和围绕 Office 365 服务器及其所代表的网络终结点的风险降低透明。office 365 内置安全功能可用于减少网络安全风险, 例如数据丢失防护、反病毒、多重身份验证、客户锁定框、高级威胁防护、Office 365 威胁智能、office 365 安全分数、Exchange Online Protection 和网络 DDOS 安全性。
  
有关 microsoft 数据中心和全局网络安全性的详细信息, 请参阅[microsoft 信任中心](https://www.microsoft.com/en-us/trustcenter/security)。
  
## <a name="new-office-365-endpoint-categories"></a>新的 Office 365 终结点类别
<a name="BKMK_Categories"> </a>

Office 365 端点代表一组不同的网络地址和子网。终结点可以是 url、ip 地址或 ip 范围, 并且有些终结点是与特定 TCP/UDP 端口一起列出的。url 可以是 FQDN (如*account.office.net* ), 也可以是通配符 URL (如* \*office365.com*)。
  
> [!NOTE]
> 网络中的 office 365 终结点的位置并不直接与 Office 365 租户数据的位置相关。出于此原因, 客户应查看 office 365 作为分布式和全局服务, 不应尝试根据地理条件阻止与 Office 365 终结点的网络连接。
  
在我们关于管理 Office 365 流量的前一指南中, 终结点分为两类:**必需**和**可选**。每个类别中的终结点需要不同的优化, 具体取决于服务的关键程度, 而许多客户在论证对 Office 365 url 和 IP 地址的完整列表中的相同网络优化的应用程序时面临的挑战。 
  
在新模型中, 终结点分为三个类别: "**优化**"、"**允许**" 和 "**默认**", 提供基于优先级的数据透视, 以实现最佳性能改进和返回的重点关注的网络优化工作。投资回报。根据有效用户体验对应用场景的有效用户体验、容量和性能信封以及易于实现的敏感度, 在上述类别中整合终结点。对于给定类别中的所有终结点, 推荐的优化可以采用相同的方式。
  
- **优化**终结点是与每个 Office 365 服务的连接所必需的, 并表示超过 75% 的 office 365 带宽、连接和数据量。这些终结点代表最敏感网络性能、延迟和可用性的 Office 365 方案。所有终结点都托管在 Microsoft 数据中心中。此类别中的终结点的更改速率应小于其他两个类别中的终结点的大小。此类别包括一组非常小 (约为 ~ 10) 的密钥 url 和一组专用于核心 Office 365 工作负荷 (如 Exchange Online、SharePoint online、Skype for business Online 和 Microsoft 团队) 的已定义 IP 子网。

    明确定义的关键终结点的简明列表应有助于您更快、更轻松地规划和实现这些目标的高价值网络优化。

    *优化*终结点的示例*https://outlook.office365.com*包括*https://\<\>sharepoint.com*和*https://\<租户\>-my.sharepoint.com* 。

    优化方法包括:

  - 绕过或白名单可*优化*网络设备和服务上执行通信拦截、SSL 解密、深入数据包检查和内容筛选的终结点。
  - 绕过本地代理设备和通常用于常规 Internet 浏览的基于云的代理服务。
  - 将这些终结点的评估优先级设置为受网络基础结构和外围系统的完全信任。
  - 对 WAN 回程的降低或消除优先级进行优先级划分, 并为这些终结点提供尽可能接近用户/分支位置的直接分布式 Internet 出口。
  - 通过实现拆分隧道, 促进与 VPN 用户的这些云终结点的直接连接。
  - 确保由 DNS 名称解析返回的 IP 地址与这些终结点的路由传出路径相匹配。
  - 将这些终结点的优先级设置为 SD-WAN 集成, 以实现直接的最小延迟 (路由到 Microsoft 全局网络的最近 Internet 对等点)。

- **允许**终结点连接到特定的 Office 365 服务和功能, 但不像 "*优化*" 类别中的那样对网络性能和延迟敏感。这些终结点在带宽和连接计数方面的总体网络占用率也大大减小。这些终结点专门用于 Office 365, 并托管在 Microsoft 数据中心中。它们代表一组广泛的 Office 365 微服务及其依赖项 (顺序为 ~ 100 个 url), 并且预期以高于 "*优化*" 类别中的比率进行更改。并非此类别中的所有终结点都与定义的专用 IP 子网相关联。

    *允许*终结点的网络优化可以改进 Office 365 的用户体验, 但有些客户可能会选择将这些优化的作用范围更窄, 以最大限度地减少对其网络所做的更改。

    *允许*终结点的示例*包括\*https://* 和*https://accounts.accesscontrol.windows.net*protection.outlook.com。

    优化方法包括:

  - 旁路或白名单*允许*网络设备和服务上的终结点, 这些终结点可执行流量截取、SSL 解密、深入数据包检查和内容筛选。
  - 将这些终结点的评估优先级设置为受网络基础结构和外围系统的完全信任。
  - 对 WAN 回程的降低或消除优先级进行优先级划分, 并为这些终结点提供尽可能接近用户/分支位置的直接分布式 Internet 出口。
  - 确保由 DNS 名称解析返回的 IP 地址与这些终结点的路由传出路径相匹配。
  - 将这些终结点的优先级设置为 SD-WAN 集成, 以实现直接的最小延迟 (路由到 Microsoft 全局网络的最近 Internet 对等点)。

- **默认**终结点代表不需要进行任何优化的 Office 365 服务和依赖项, 并且可由客户网络作为正常的 Internet 绑定流量进行处理。请注意, 此类别中的某些终结点可能不会托管在 Microsoft 数据中心中。示例包括*https://odc.officeapps.live.com*和*https://appexsin.stb.s-msn.com*。

有关 Office 365 网络优化技术的详细信息, 请参阅[管理 Office 365 终结点](https://support.office.com/en-us/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview)一文。
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>将网络外围安全性与终结点安全性进行比较
<a name="BKMK_SecurityComparison"> </a>

传统网络安全的目标是强化公司网络外围, 以防受到入侵和恶意攻击。在组织采用 Office 365 时, 某些网络服务和数据将部分或完全迁移到云。与对网络体系结构的任何基本更改一样, 此过程需要重新评估需要考虑的新兴因素的网络安全:
  
- 随着云服务的采用, 网络服务和数据在内部部署数据中心和云之间分布, 而外围安全不再充分。
- 远程用户从内部部署数据中心和云中的公司资源中连接到不受控制的位置, 如住宅、旅馆和咖啡店。
- 专门构建的安全功能已越来越多地内置到云服务中, 并且可能会补充或替换现有的安全系统。

Microsoft 提供了各种 Office 365 安全功能, 并提供了用于确保 office 365 的数据和网络安全性的安全最佳做法的说明性指导。建议的最佳实践包括以下各项:
  
- **使用多重身份验证 (MFA)** 通过在正确输入密码后, 通过请求用户在智能手机上确认电话呼叫、短信或应用程序通知, MFA 向强密码策略添加了一层额外的保护。

- **使用 Office 365 云应用安全**设置策略以跟踪异常活动并对其执行操作。设置与 Office 365 云应用安全有关的通知, 以便管理员可以查看异常或风险的用户活动, 如下载大量数据、多个失败的登录尝试或来自未知或危险的 IP 地址的连接。

- **配置数据丢失防护 (DLP)** DLP 允许您标识敏感数据, 并创建有助于防止用户意外或有意地共享数据的策略。DLP 在 Office 365 中工作, 包括 Exchange online、SharePoint online 和 OneDrive, 以便您的用户在不中断其工作流的情况下保持合规性。

- **使用客户密码箱**作为 Office 365 管理员, 你可以使用客户密码箱控制 Microsoft 支持工程师在帮助会话过程中访问你的数据的方式。如果工程师需要访问数据以排查和解决问题, 客户密码箱允许您批准或拒绝访问请求。

- **使用 Office 365 安全分数**安全得分是一种安全分析工具, 它建议您可以执行哪些操作以进一步降低风险。安全分数查看 Office 365 设置和活动, 并将它们与 Microsoft 建立的基准进行比较。你将根据最佳安全实践的对齐方式获得分数。

增强安全性的一种整体方法应包括以下注意事项:
  
- 通过应用基于云和 Office 的客户端安全功能, 将重点从周边安全转到端点安全性。
  - 将安全外围环境缩减为数据中心
  - 为 office 内部或远程位置的用户设备启用等效信任
  - 重点保护数据位置和用户位置
  - 托管用户计算机具有更高的与终结点安全性的信任
- 管理所有信息安全 holistically, 而不只是集中在外围环境中
  - 通过允许受信任的流量绕过安全设备并将非托管设备分离到来宾 wlan 网络, 来重新定义 WAN 和构建外围网络安全性。
  - 降低企业 WAN 边缘的网络安全要求
  - 有些网络外围安全设备 (例如防火墙) 仍是必需的, 但负载降低了
  - 确保 Office 365 流量的本地出口
- 改进可以按照 "[增量优化](office-365-network-connectivity-principles.md#BKMK_IncOpt)" 一节中的说明以增量方式解决。根据您的网络体系结构, 一些优化技术可能会提供更好的成本/收益率, 并且应选择最适合您的组织的优化。

有关 office 365 安全性和合规性的详细信息, 请参阅文章[office 365 中的安全性和合规性概述](https://support.office.com/en-us/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US)。
  
## <a name="incremental-optimization"></a>增量优化
<a name="BKMK_IncOpt"> </a>

我们已经为本文前面的 SaaS 提供了理想的网络连接模型, 但对于许多具有传统复杂网络体系结构的大型组织, 直接进行所有这些更改并不可行。在本节中, 我们将讨论大量可帮助改进 Office 365 性能和可靠性的增量更改。
  
用于优化 Office 365 流量的方法将因网络拓扑和已实施的网络设备而异。具有多个位置和复杂网络安全实践的大型企业需要制定一种策略, 其中包括[Office 365 连接原则](office-365-network-connectivity-principles.md#BKMK_Principles)一节中列出的大部分或全部原则, 而小型组织可能仅需要考虑一两个。
  
您可以采用增量过程进行优化, 从而连续应用每个方法。下表列出了关键优化方法, 这些方法按对最大用户数的延迟和可靠性的影响顺序排列。
  
|**优化方法**|**说明**|**影响**|
|:-----|:-----|:-----|
|本地 DNS 解析和 Internet 出口  <br/> |在每个位置预配本地 DNS 服务器, 并确保 Office 365 连接可尽可能靠近用户位置的 Internet。  <br/> | 最小化延迟  <br/>  改进与最近的 Office 365 入口点的可靠连接  <br/> |
|添加区域出口积分  <br/> |如果您的企业网络有多个位置, 但只有一个出口点, 则添加区域出口点, 以使用户能够连接到最接近的 Office 365 入口点。  <br/> | 最小化延迟  <br/>  改进与最近的 Office 365 入口点的可靠连接  <br/> |
|绕过代理和检查设备  <br/> |使用将 Office 365 请求直接发送到出局点的 PAC 文件配置浏览器。  <br/> 配置边缘路由器和防火墙以允许不进行检查的 Office 365 流量。  <br/> | 最小化延迟  <br/>  减少网络设备上的负载  <br/> |
|为 VPN 用户启用直接连接  <br/> |对于 VPN 用户, 启用 Office 365 连接以直接从用户网络进行连接, 而不是通过实现拆分隧道的方式连接到 vpn 隧道。  <br/> | 最小化延迟  <br/>  改进与最近的 Office 365 入口点的可靠连接  <br/> |
|从传统 wan 迁移到 SD-WAN  <br/> |SD-wan (软件定义的广域网络) 简化了 wan 管理, 并通过将传统 WAN 路由器替换为虚拟设备来提高性能, 类似于使用虚拟机 (vm) 计算资源的虚拟化。  <br/> | 改进 WAN 流量的性能和可管理性  <br/>  减少网络设备上的负载  <br/> |
