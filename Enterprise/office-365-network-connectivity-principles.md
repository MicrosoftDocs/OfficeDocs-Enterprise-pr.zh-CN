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
search.appverid: MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
description: 规划 Office 365 网络连接网络之前，务必了解用于安全地管理 Office 365 流量和获取最佳性能的连接原则。本文将帮助您了解有关安全地优化 Office 365 网络连接的最新指南。
ms.openlocfilehash: be41162833a7442ac65af1e973a00923841fca6b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539697"
---
# <a name="office-365-network-connectivity-principles"></a>Office 365 网络连接原则

规划 Office 365 网络连接网络之前，务必了解用于安全地管理 Office 365 流量和获取最佳性能的连接原则。本文将帮助您了解有关安全地优化 Office 365 网络连接的最新指南。
  
传统的企业网络主要用于为用户提供访问应用程序和强外围安全承载在公司客户数据中心中的数据。传统模型假定用户将访问应用程序和数据从内部企业网络外围，，通过从分支机构的 WAN 链接或远程通过 VPN 连接。 
  
Saas 与应用程序，如 Office 365 的移动服务和外部网络外围数据的一些组合。未优化，用户和 saas 与应用程序之间的流量受到延迟引入的检查数据包来、 网络 hairpins、 可以防止由于无意连接到遥远终结点和其他因素。您可以确保最佳的 Office 365 性能和可靠性理解和实现关键优化指南。
  
在本文中，您将了解有关：
  
- 作为其[office 365 体系结构](office-365-network-connectivity-principles.md#BKMK_Architecture)适用于客户连接到云
- 更新的[Office 365 连接原则](office-365-network-connectivity-principles.md#BKMK_Principles)和优化网络流量和最终用户体验策略
- [Office 365 终结点 web 服务](office-365-network-connectivity-principles.md#BKMK_WebSvc)，它允许网络管理员使用网络优化中使用的终结点的结构化的列表
- [新的 Office 365 终结点类别](office-365-network-connectivity-principles.md#BKMK_Categories)和优化指南
- [比较终结点安全网络外围安全](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Office 365 流量的[增量优化](office-365-network-connectivity-principles.md#BKMK_IncOpt)选项

## <a name="office-365-architecture"></a>Office 365 体系结构
<a name="BKMK_Architecture"> </a>

Office 365 是提供通过多种多样微服务和应用程序，如业务 online，Microsoft Exchange Online 中，SharePoint Online Skype 的工作效率和协作方案分布式的软件作为-服务 (SaaS) 云团队、 Exchange Online Protection、 Office Online 和多个其他人。虽然特定的 Office 365 应用程序可能具有其独特功能，如它适用于客户网络和连接到云，它们都共享一些关键主体、 目标和体系结构模式。这些主体和连接的体系结构模式是典型的许多其他 saas 与云和同时正在有很大不同的平台作为服务和基础结构作为服务云朵，如 Microsoft 的典型部署模型Azure。
  
Office 365 （即通常丢失或错误地解释了网络规划人员通过） 的最重要的体系结构功能之一是它是一个真正的全球化的分布式的服务，用户如何连接到它的上下文中。需要了解的客户数据存储在云中，其中县目标 Office 365 租户的位置，但与 Office 365 的用户体验不涉及直接连接到包含数据的磁盘。与 Office 365 （包括性能、 可靠性和其他重要的质量特征） 的用户体验涉及通过向外扩展跨数百 Microsoft 位置全球高度分布式的服务前盖连接。在大多数情况下，最佳用户体验被通过允许用户请求路由到最接近的 Office 365 服务入口点客户网络，而不被通过一个中心位置或区域中的出口点连接到 Office 365。
  
对于大多数客户，Office 365 用户分布在多个位置。若要获得最佳结果，本文档中概述的原则应看从向外扩展 （不向上） 的角度来说，将重点放在优化连接到最近的点的 Microsoft 全局网络中的状态，而不地理Office 365 租户的位置。实际上，这意味着即使 Office 365 租户数据可能存储在一个特定的地理位置，该租户的 Office 365 体验保持分布式和中可能存在非常关闭 （网络） 接近租户具有每个最终用户位置.
  
## <a name="office-365-connectivity-principles"></a>Office 365 连接原则
<a name="BKMK_Principles"> </a>

Microsoft 建议以下原则以获得最佳的 Office 365 连接性和性能。使用这些 Office 365 连接原则来管理您的通信和连接到 Office 365 时获得最佳性能。
  
应为网络设计中的主要目标从您的网络到 Microsoft 全局网络中，Microsoft 的公用网络中枢的互连所有 Microsoft 数据中心的低延迟以减少延迟通过减少的往返时间 (RTT)和云应用程序在全球范围内的入口点。您可以了解有关在[Microsoft 如何构建其快速且可靠的全局网络](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)的 Microsoft 全局网络的详细信息。
  
### <a name="identify-and-differentiate-office-365-traffic"></a>确定并区分 Office 365 通信量
<a name="BKMK_P1"> </a>

![确定 Office 365 流量](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
确定 Office 365 网络流量是能够将该流量与通用 Internet 绑定网络流量区分开来的第一步。通过实现的方法，如网络路由优化、 防火墙规则、 浏览器代理设置和绕过特定终结点的网络检查设备的组合，可以优化 office 365 连接。
  
以前的 Office 365 优化指南划分为两个类别，**所需**和**可选**的 Office 365 终结点。添加了终结点，以支持新的 Office 365 服务和功能，如我们已重新组织了 Office 365 终结点到三个类别：**优化**、**允许**和**默认值**。每个类别的准则应用于在类别中，进行优化易于理解和实现的所有终结点。 
  
Office 365 终结点类别和优化方法的详细信息，请参阅[新的 Office 365 终结点类别](office-365-network-connectivity-principles.md#BKMK_Categories)部分。
  
Microsoft 现在作为 web 服务发布所有 Office 365 终结点，并提供有关如何充分利用此数据指导。如何获取并使用 Office 365 终结点的详细信息，请参阅文章[Office 365 Url 和 IP 地址范围](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US)。
  
### <a name="egress-network-connections-locally"></a>本地出口网络连接
<a name="BKMK_P2"> </a>

![本地出口网络连接](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
本地 DNS 和 Internet 出口是入口的一点的至关重要是入口的一点的减少连接延迟和确保用户连接所做的最接近到 Office 365 服务点。在复杂的网络拓扑中，务必一起实现本地 DNS 和本地 Internet 出口。有关 Office 365 将客户端连接路由到最接近的入口点的方式的详细信息，请参阅文章[客户端连接](https://support.office.com/en-us/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)。
  
之前的云服务，例如 Office 365 一起工作，最终用户 Internet 连接的网络体系结构设计因素是相对简单。当在全球分布 Internet 服务和网站时，企业出口点和任何给定的目标终结点之间的延迟是很大程度上地理距离的函数。
  
在传统网络体系结构，所有出站的 Internet 连接遍历企业网络和出口从一个中心位置。随着 Microsoft 云服务具有成熟，分布式的面向 Internet 的网络体系结构变得很关键支持延迟敏感云服务。Microsoft 全球网络旨在容纳延迟要求使用分布式服务前盖基础结构，动态全局入口点的结构，可将云服务的传入连接路由到最接近的入口点。这是为了减少"最后一个英里"的长度为 Microsoft 云客户通过有效地缩短客户和云之间的路由。
  
企业 Wan 通常旨在出口到 Internet，通常通过一个或多个代理服务器之前检查中央公司总部将网络流量。下图说明了此类的网络拓扑。
  
![传统的企业网络模型](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
由于 Office 365 运行 Microsoft 全局网络，其中包括世界各地的前端服务器，通常会接近用户的位置的前端服务器。通过提供本地 Internet 出口以及配置内部 DNS 服务器提供 Office 365 终结点的本地名称解析，发送到 Office 365 的网络流量可以连接到 Office 365 尽可能地向用户的前端服务器。下图显示了一个允许用户从主办公室、 分支机构和远程位置连接到最接近的 Office 365 入口点执行的最短的路由的网络拓扑的示例。
  
![使用区域出口点的 WAN 网络模型](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
缩短的网络路径到 Office 365 入口点，这样可以提高连接性能和最终用户体验中 Office 365 中，可以还有助于降低将来对 Office 365 性能的网络体系结构更改的影响和可靠性。
  
同时，DNS 请求会带来延迟，如果响应的 DNS 服务器远或忙碌。通过设置分支机构中的本地 DNS 服务器，并确保它们正确配置为缓存 DNS 记录，可以减少名称解析延迟。
  
时区域出口可以适用于 Office 365，最佳 connectivity 模型将始终提供在用户的位置，而不考虑此位于企业网络或远程位置，如 home、 酒店或咖啡馆网络出口和机场。下图中表示此本地直接出口模型。
  
![本地出口网络体系结构](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
已采用 Office 365 的企业可以通过确保到 Office 365 的用户连接到最接近的 Microsoft 全局网络项采取的最短的可能路由充分利用 Microsoft 全球网络分布式服务前盖体系结构点。本地出口网络体系结构允许 Office 365 流量路由通过最接近出口，无论用户来达到此目的。
  
本地出口体系结构通过传统模型具有以下优点：
  
- 通过 Office 365 的最佳性能优化路由长度。动态，最终用户连接将路由到最接近的 Office 365 入口点由分布式服务前盖基础结构。
- 本地出口，从而减少了企业网络基础结构上的负载。
- 利用客户端终结点安全性和云安全功能保护两端的连接。

### <a name="avoid-network-hairpins"></a>避免网络 hairpins
<a name="BKMK_P3"> </a>

![避免 hairpins](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
作为一般法则，用户和最接近的 Office 365 终结点之间的最短、 最直接路由将提供最佳性能。WAN 或 VPN 通信绑定的特定目标首先定向到另一个中间位置 （如安全堆栈，云访问代理的基于云的 web 网关），时发生网络发夹引入延迟和潜在重定向到遥远终结点。网络 hairpins 也可能是由路由/对等效率低下或不够理想 （远程） 的 DNS 查找并且导致的。
  
若要确保 Office 365 连接不存在网络 hairpins 甚至在本地出口的情况下，检查是否用于提供用户位置的 Internet 出口建立直接对等关系中的 Microsoft 全局网络 ISP 关闭到该位置的邻近度。您可能还希望配置出站路由直接发送受信任的 Office 365 流量，而不是代理或隧道通过第三方云或基于云的网络安全供应商的处理 Internet 绑定流量。Office 365 终结点的本地 DNS 名称解析有助于确保，除了直接路由的最接近的 Office 365 入口点所使用的用户连接。
  
如果您使用基于云的网络或 Office 365 通信的安全服务，确保计算 hairpinning 效果并了解其对 Office 365 性能的影响。这可以通过检查的数量和通过其通信转发到数您分支机构和 Microsoft 全球网络对等点，质量的对等网络关系关系中的服务提供程序位置的位置您的 ISP 和 Microsoft，以及 backhauling 服务提供程序基础结构中的性能影响服务提供商。
  
由于大量的分布式与 Office 365 入口点和邻近受最终用户的位置，路由到任何第三方网络或安全提供程序的 Office 365 通信可以负面影响 Office 365 连接如果没有提供商网络为获得最佳的 Office 365 对等配置。
  
### <a name="bypass-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>绕过代理服务器、 流量检查设备和重复的安全技术
<a name="BKMK_P4"> </a>

![绕过代理服务器、 流量检查设备和重复的安全技术](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
企业客户应查看其网络安全性和专为 Office 365 的风险缩减方法绑定流量，使用 Office 365 安全功能来减少及其依赖触犯式、 性能影响和昂贵的网络安全Office 365 网络流量的技术。
  
大多数企业网络强制 Internet 通信使用如代理、 SSL 检查、 数据包检查和数据丢失防护系统技术的网络安全。这些技术提供的通用 Internet 请求的重要风险缓解时，但可以显著减少性能、 可伸缩性和应用到 Office 365 终结点时的最终用户体验质量。
  
#### <a name="office-365-endpoints-web-service"></a>Office 365 终结点 web 服务
<a name="BKMK_WebSvc"> </a>

Office 365 管理员可以使用的脚本或使用结构化的 Office 365 终结点的终结点列表的 REST 调用 web 服务和更新的外围防火墙配置和其他网络设备。这将确保 Office 365 绑定的流量为标识，进行适当处理并从网络流量泛型和通常未知的 Internet 网站绑定以不同的方式管理。有关如何使用 Office 365 终结点的详细信息 web 服务，请参阅文章[Office 365 Url 和 IP 地址范围](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US)。
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC （代理自动配置） 脚本
<a name="BKMK_WebSvc"> </a>

Office 365 管理员可以创建可发送到用户计算机上通过 WPAD 或 GPO 的 PAC （代理自动配置） 脚本。PAC 脚本可用于绕过 WAN 或 VPN 用户从 Office 365 请求允许 Office 365 通信使用直接 Internet 连接，而不遍历企业网络的代理。
  
#### <a name="office-365-security-features"></a>Office 365 安全功能
<a name="BKMK_WebSvc"> </a>

Microsoft 是有关数据中心安全、 运营的安全性和解决 Office 365 服务器和网络终结点，它们表示降低风险透明的。Office 365 的内置安全性功能均可用，减少网络安全风险，如数据丢失防护、 防病毒、 多因素身份验证，客户锁定框、 高级威胁保护、 Office 365 威胁智能、 Office 365 安全分数、 Exchange Online Protection 和网络 DDOS 安全。
  
有关 Microsoft 数据中心和全局网络的安全性的详细信息，请参阅[Microsoft 信任中心](https://www.microsoft.com/en-us/trustcenter/security)。
  
## <a name="new-office-365-endpoint-categories"></a>新的 Office 365 终结点类别
<a name="BKMK_Categories"> </a>

Office 365 终结点表示一套各种的网络地址和子网。终结点可能 Url 的 IP 地址或 IP 范围，并与特定 TCP/UDP 端口列出了一些终结点。Url 可*account.office.net* ，如的 FQDN 或通配符 URL like * \*。 office365.com*。
  
> [!NOTE]
> 到 Office 365 租户数据的位置不直接相关的网络中的 Office 365 终结点的位置。因此，客户应查看作为分布式和全局服务的 Office 365，并不应尝试阻止网络连接到 Office 365 终结点基于地理条件。
  
在用于管理 Office 365 流量我们以前指南，终结点已组织分为两类，**所需**和**可选**。许多客户所面临的难题中对齐的完整列表的 Office 365 Url 和 IP 地址的同一个网络优化应用程序和每个类别中的终结点所需的服务，具体取决于重要程度不同优化。 
  
在新模型中，终结点被隔离到三个类别中，**优化**、**所需**和**默认值**，以实现最佳性能改进的焦点网络优化工作何处上提供基于优先级的透视和投资回报。终结点中根据网络质量、 卷和性能信封的方案和易于实现有效的用户体验的敏感度上述类别合并。建议的优化可以应用到给定类别中的所有终结点的方式相同。
  
- **优化**终结点所需的连接到每个 Office 365 服务和占的 Office 365 带宽、 连接和数据量的 75%。这些终结点表示最敏感网络性能、 延迟和可用性的 Office 365 方案。在 Microsoft 数据中心中承载的所有终结点。应到此类别中的终结点的变化率低于其他两个类别中的终结点得多。此类别包括一非常小 （大约为大约 10) 的 Url 和一组定义的 IP 子网专用于核心 Office 365 工作负载，例如 Exchange Online、 SharePoint Online、 Skype 业务 Online 和 Microsoft 团队的键。

    定义良好的关键终结点的紧缩的列表可帮助您规划和实现这些目标更快、 更轻松的高价值网络优化。

    *优化*终结点的示例包括*https://outlook.office365.com*， *https://\<租户\>。 sharepoint.com*和*https://\<租户\>-my.sharepoint.com* 。

    优化方法包括：

  - 绕过或白名单*优化*终结点的网络设备和执行通信截取、 SSL 解密、 深入数据包检查和内容筛选的服务。
  - 绕过的本地代理设备和通常用于常规 Internet 浏览的基于云的代理服务。
  - 设置为完全信任由网络基础结构和外围 systems 这些终结点的评估版的优先级。
  - 确定优先级减少或的 WAN backhauling 消除并如接近尽可能的用户/分支机构加快直接分布式的 Internet 基于出口这些终结点。
  - 通过实现拆分隧道加快直接连接到 VPN 用户这些云终结点。
  - 确保 DNS 名称解析返回的 IP 地址匹配这些终结点的路由出口路径。
  - 设置优先级到最接近 Internet 对等点 Microsoft 全球网络路由直接、 最小延迟 SD WAN 集成这些终结点。

- **允许**终结点所需的连接到特定的 Office 365 服务和功能，但不是为敏感网络性能和*优化*类别中的与延迟。从带宽和连接计数的角度看这些终结点的总网络占用也是显著较小的。这些终结点到 Office 365 专用和承载在 Microsoft 数据中心。它们表示广泛的 Office 365 微服务和及其依赖项 （大约为大约 100 名 Url)，需要更改的速度比*优化*类别中。此类别中的所有终结点是定义专用的 IP 子网与相关联。

    *允许*终结点的网络优化可以提高 Office 365 的用户体验，但某些客户可以选择范围详细这些优化窄大程度地减少对其网络的更改。

    *允许*终结点的示例包括*https://\*。 protection.outlook.com*和*https://accounts.accesscontrol.windows.net*。

    优化方法包括：

  - 绕过或白名单*允许*终结点的网络设备和执行通信截取、 SSL 解密、 深入数据包检查和内容筛选的服务。
  - 设置为完全信任由网络基础结构和外围 systems 这些终结点的评估版的优先级。
  - 确定优先级减少或的 WAN backhauling 消除并如接近尽可能的用户/分支机构加快直接分布式的 Internet 基于出口这些终结点。
  - 确保 DNS 名称解析返回的 IP 地址匹配这些终结点的路由出口路径。
  - 设置优先级到最接近 Internet 对等点 Microsoft 全球网络路由直接、 最小延迟 SD WAN 集成这些终结点。

- **默认**终结点表示 Office 365 服务以及不需要任何优化，并可以被视为由客户网络普通 Internet 绑定流量的依赖关系。请注意，此类别中的部分端点可能未承载在 Microsoft 数据中心中。示例包括*https://odc.officeapps.live.com*和*https://appexsin.stb.s-msn.com*。

有关 Office 365 网络优化技术的详细信息，请参阅文章[管理 Office 365 终结点](https://support.office.com/en-us/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview)。
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>比较终结点安全网络外围安全
<a name="BKMK_SecurityComparison"> </a>

传统网络安全的目标是强化企业网络外围免受入侵和恶意攻击。如果组织采用 Office 365，一些网络服务和数据被部分或完全迁移到云中。如才任何基本更改为网络体系结构，此过程需要考虑新兴因素的网络安全的重新计算：
  
- 云服务采用，如网络服务和数据之间的本地数据中心和云，分发和外围安全不再是适合自己的。
- 远程用户连接到企业资源的本地数据中心在和中不受控制的位置，如家庭、 酒店或和咖啡馆从云。
- 专门的安全功能逐渐内置云服务和可能会进行了补充或替换现有的安全系统。

Microsoft 提供范围的 Office 365 安全功能和为采用可以帮助您确保数据和网络安全的 Office 365 的安全性最佳实践的说明性指导。以下建议的最佳实践：
  
- **使用多因素身份验证 (MFA)** MFA 通过要求用户确认电话呼叫、 短信或其智能电话上正确输入自己的密码后应用程序通知向强密码策略额外的保护程序。

- **使用 Office 365 云应用程序安全性**设置策略，以跟踪异常活动，并对其执行操作。设置与 Office 365 云应用程序安全性的通知，以便管理员可以查看异常或 risky 用户活动，如下载大量数据，多失败尝试登录时，或者连接从未知或危险 IP 地址。

- **配置数据丢失防护 (DLP)** DLP 允许您确定敏感数据，并创建策略，以防止用户无意或有意共享数据。DLP 适用于跨 Office 365，以便用户可以保持兼容不中断其工作流的情况包括 Exchange Online、 SharePoint Online 和 OneDrive。

- **使用客户密码箱**作为 Office 365 管理员，您可以使用客户密码箱控制 Microsoft 支持工程师帮助会话期间访问您的数据的方式。在其中工程师需要访问数据以排除和修复问题的情况下，客户密码箱允许您批准或拒绝访问请求。

- **使用 Office 365 安全分数**安全 Score 是一个安全分析工具，建议您可以以进一步降低风险。安全分数查看您的 Office 365 设置和活动，并对它们进行比较到由 Microsoft 建立一个比较基准。您将获取基于您在与最佳安全做法如何对齐的分数。

增强的安全性的整体方法应包括以下注意事项：
  
- 从达到通过应用的基于云的终结点安全性和 Office 客户端的安全功能的外围安全 shift 强调。
  - 到数据中心缩小安全外围
  - 启用对用户设备内部办公室或远程位置的等效信任
  - 重点关注保护数据的位置和用户位置
  - 托管的用户机具有更高信任终结点安全
- 不将重点放在外围仅全面，管理所有信息安全性
  - 重新定义 WAN 和外围网络安全构建通过允许受信任的流量以绕过安全设备和分隔非托管的来宾 Wi-fi 网络设备。
  - 减少了企业 WAN 边缘的网络安全要求
  - 降低某些网络外围安全设备如防火墙仍是必需的但是加载
  - 确保本地出口的 Office 365 流量
- 可在[增量优化](office-365-network-connectivity-principles.md#BKMK_IncOpt)部分所述的增量解决改进。某些优化技术可提供更好成本/收益率，具体取决于网络体系结构，，应该选择优化，使最适合您的组织。

Office 365 安全性和遵从性的详细信息，请参阅文章[Overview of 安全性和 Office 365 中的合规性](https://support.office.com/en-us/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US)。
  
## <a name="incremental-optimization"></a>增量优化
<a name="BKMK_IncOpt"> </a>

我们已本文前面的 SaaS 表示理想的网络连接模型，但对于许多大型组织，与过去复杂网络体系结构，它将不可行直接使所有这些更改。在此部分中，我们将讨论的大量有助于提高 Office 365 性能和可靠性的增量更改。
  
将用于优化 Office 365 通信的方法将取决于您的网络拓扑和已实施的网络设备。使用很多位置和复杂的网络安全做法的大型企业需要开发大部分或全部时较小的组织可能仅在[Office 365 连接原则](office-365-network-connectivity-principles.md#BKMK_Principles)部分中，列出的原则包括的策略需要考虑一个或两个。
  
您可以为一个增量过程，主动优化连续应用每种方法。下表列出了按顺序对延迟和可靠性及其影响最大数量的用户的主要优化方法。
  
|**优化方法**|**说明**|**影响**|
|:-----|:-----|:-----|
|本地 DNS 解析和 Internet 出口  <br/> |设置每个位置中的本地 DNS 服务器，并确保到 Internet 尽可能接近到用户的位置的 Office 365 连接出口。  <br/> | 减少延迟  <br/>  提高可靠地连接到最接近的 Office 365 入口点  <br/> |
|添加区域出口点  <br/> |如果企业网络中有多个位置，但只有一个出口点，添加区域出口点，以便用户能够连接到最接近的 Office 365 入口点。  <br/> | 减少延迟  <br/>  提高可靠地连接到最接近的 Office 365 入口点  <br/> |
|绕过代理服务器和检查设备  <br/> |使用 Office 365 请求直接发送到出口点的 PAC 文件配置浏览器。  <br/> 配置边缘路由器和防火墙以允许不检查 Office 365 流量。  <br/> | 减少延迟  <br/>  减少网络设备上的负载  <br/> |
|启用直接连接的 VPN 用户  <br/> |VPN 用户启用 Office 365 连接将通过实现拆分隧道的直接从用户的网络，而不是通过 VPN 隧道的连接。  <br/> | 减少延迟  <br/>  提高可靠地连接到最接近的 Office 365 入口点  <br/> |
|将传统 WAN 迁移到 SD WAN  <br/> |SD Wan （软件定义广域网） 简化 WAN 管理，并通过传统 WAN 路由器替换虚拟装置，类似于虚拟化计算资源使用虚拟机 (Vm) 来提高性能。  <br/> | 提高性能和可管理性的 WAN 通信  <br/>  减少网络设备上的负载  <br/> |
