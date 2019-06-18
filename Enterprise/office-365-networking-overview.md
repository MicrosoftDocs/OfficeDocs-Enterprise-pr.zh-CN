---
title: Office 365 网络连接概述
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: 讨论为什么网络优化对 SaaS 服务非常重要, Office 365 网络的目标, 以及 SaaS 如何从其他工作负载中获得不同的网络。
ms.openlocfilehash: e1ae446d7a69d0fab83e7dd4aa253bd1120e6c08
ms.sourcegitcommit: 99bf8739dfe1842c71154ed9548ebdd013c7e59e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2019
ms.locfileid: "35017282"
---
# <a name="office-365-network-connectivity-overview"></a>Office 365 网络连接概述

Office 365 是分布式软件即服务 (SaaS) 云, 它通过一组不同的微服务和应用程序提供工作效率和协作方案。 Office 365 的客户端组件 (如 Outlook、Word 和 PowerPoint) 在用户计算机上运行, 并连接到在 Microsoft 数据中心中运行的 Office 365 的其他组件。 确定 Office 365 最终用户体验质量的最重要因素是网络可靠性和 Office 365 客户端与 Office 365 服务前盖之间的低延迟。

在本文中, 您将了解 Office 365 网络的目标, 以及为什么 Office 365 网络需要不同的优化方法来优化常规 Internet 流量。

## <a name="office-365-networking-goals"></a>Office 365 网络目标

Office 365 网络的最终目标是通过在客户端和最接近的 Office 365 终结点之间启用限制性最少的访问来优化最终用户体验。 最终用户体验的质量与用户正在使用的应用程序的性能和响应直接相关。 例如, Microsoft 团队依赖较低的延迟, 以便用户电话呼叫、会议和共享屏幕协作免费, 并且 Outlook 依靠强大的网络连接实现即时搜索功能, 从而利用服务器端索引和 AI能力.

网络设计中的主要目标是将客户端计算机的往返时间 (RTT) 从客户端计算机减少到 Microsoft 全局网络, 从而将所有 Microsoft 的数据中心互连到低延迟的 microsoft 公共网络骨干, 从而最大限度地减少延迟, 高可用性云应用程序入口点分布在世界各地。 你可以在[Microsoft 如何构建其快速可靠的全局网络](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)中了解有关 Microsoft 全球网络的详细信息。

优化 Office 365 网络性能不需要太复杂。 您可以通过遵循以下几个关键原则获取最佳性能:

- 确定 Office 365 网络流量
- 允许从用户连接到 Office 365 的每个位置将 Office 365 网络流量的本地分支出口到 internet
- 允许 Office 365 流量绕过代理和数据包检查设备

有关 Office 365 网络连接原则的详细信息, 请参阅[office 365 网络连接原则](office-365-network-connectivity-principles.md)。

## <a name="traditional-network-architectures-and-saas"></a>传统网络体系结构和 SaaS

传统的网络体系结构针对客户端/服务器工作负载的原则旨在假定客户端和终结点之间的通信不会延伸到公司网络外围之外。 此外, 在许多企业网络中, 所有出站 Internet 连接都在企业网络中, 并从中心位置外出。

在传统网络体系结构中, 常规 Internet 流量的较高延迟是维护网络外围安全所必需的, 并且 Internet 流量的性能优化通常涉及升级或扩展网络出局点的设备。 但是, 此方法并不能满足针对 SaaS 服务 (如 Office 365) 的最佳网络性能要求。

## <a name="identifying-office-365-network-traffic"></a>识别 Office 365 网络流量

我们可以更轻松地识别 Office 365 网络流量, 并简化管理网络标识的过程。

- 新类别的网络终结点, 用于将高度关键的网络流量与不受 Internet 延迟影响的网络流量区分开来。 在最关键的 "优化" 类别中, 只提供了少量 Url 和支持 IP 地址。
- 用于脚本使用情况的 Web 服务、Office 365 网络标识的直接设备配置和更改管理。 可以通过 web 服务或 RSS 格式, 或使用 Microsoft Flow 模板在电子邮件上获取更改。
- Microsoft 合作伙伴提供的[Office 365 网络合作伙伴计划](http://aka.ms/Office365NPP), 其中提供了遵循 Office 365 网络连接原则并具有简单配置的设备或服务。

## <a name="securing-office-365-connections"></a>保护 Office 365 连接

传统网络安全的目标是强化公司网络外围, 以防受到入侵和恶意攻击。 大多数企业网络使用代理服务器、防火墙、SSL 中断和检查、深度数据包检查和数据丢失防护系统等技术强制 Internet 流量的网络安全。 这些技术为常规 Internet 请求提供了重要风险缓解, 但在应用于 Office 365 终结点时, 可以显著降低性能、可伸缩性和最终用户体验的质量。

Office 365 通过专为 Office 365 功能和工作负载设计的内置安全和治理功能, 帮助满足您组织的内容安全性和数据使用合规性的需求。 有关 Office 365 安全性和合规性的详细信息, 请参阅[Office 365 安全指南](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap)。 有关在 Office 365 流量上执行高级处理的高级网络解决方案的 Microsoft 建议和支持位置的详细信息, 请参阅[在 office 365 流量上使用第三方网络设备或解决方案](https://support.microsoft.com/en-us/help/2690045)。

## <a name="why-is-office-365-networking-different"></a>为什么 Office 365 网络是不同的？

Office 365 设计为使用端点安全性和加密网络连接实现最佳性能, 从而减少了对外围安全强制实施的需求。 Office 365 数据中心位于世界各地, 服务旨在使用各种方法将客户端连接到最佳可用服务终结点。 由于用户数据和处理分布在许多 Microsoft 数据中心之间, 因此客户端计算机可以连接到的单个网络终结点。 事实上, Office 365 租户中的数据和服务由 Microsoft 全球网络进行动态优化, 以适应最终用户访问它们的地理位置。

当 Office 365 流量受到数据包检查和集中出站的制约时, 将会创建某些常见的性能问题:

- 高延迟可能会导致视频和音频流性能极差, 以及数据检索、搜索、实时协作、日历忙/闲信息、产品内容和其他服务的响应速度较慢
- 来自中心位置的附近连接破坏了 Office 365 全局网络的动态路由功能, 从而增加了延迟和往返时间
- 解密受 SSL 保护的 Office 365 网络流量并对其进行重新加密可能会导致协议错误并具有安全风险

通过允许客户端流量尽可能接近其地理位置来缩短 Office 365 入口点的网络路径, 可以提高连接性能和 Office 365 中的最终用户体验。 它还有助于降低对 Office 365 性能和可靠性的网络体系结构的未来更改的影响。 最佳连接模型是始终提供用户位置的网络出口, 无论是在公司网络上还是在远程位置 (例如, 家庭、旅馆、咖啡店和机场)。 一般 Internet 流量和基于 WAN 的企业网络流量将单独路由, 而不使用本地直接传出模型。 此本地直接出口模型在下图中表示。

![本地出口网络体系结构](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

本地出口体系结构对通过传统模型的 Office 365 网络通信有以下好处:
  
- 通过优化路由长度提供最佳的 Office 365 性能。 最终用户连接通过 Microsoft 全球网络的_分布式服务前端_基础结构动态路由到最接近的 Office 365 入口点, 然后将流量内部路由到 microsoft 的数据和服务终结点。超低延迟高可用性深光纤。
- 通过允许 Office 365 流量的本地出口 (绕过代理和流量检查设备) 降低了企业网络基础结构的负载。
- 通过利用客户端终结点安全性和云安全功能来保护两端的连接, 从而避免应用冗余网络安全技术。

> [!NOTE]
> _分布式服务前端_基础结构是 Microsoft 全球网络的高度可用且可扩展的网络边缘 (地理位置分散)。 它会终止最终用户连接, 并在 Microsoft 全局网络中有效地路由它们。 你可以在[Microsoft 如何构建其快速可靠的全局网络](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)中了解有关 Microsoft 全球网络的详细信息。

有关了解和应用 Office 365 网络连接原则的详细信息, 请参阅[office 365 网络连接原则](office-365-network-connectivity-principles.md)。

## <a name="conclusion"></a>总结

优化 Office 365 网络性能实际上是为了消除不必要的障碍。 通过将 Office 365 连接视为受信任的流量, 可以防止数据包检查和针对代理带宽的竞争引入延迟。 如果允许客户端计算机和 Office 365 终结点之间的本地连接, 则可以通过 Microsoft 全局网络动态路由通信。

## <a name="related-topics"></a>相关主题

[Office 365 网络连接原则](office-365-network-connectivity-principles.md)

[管理 Office 365 终结点](managing-office-365-endpoints.md)

[Office 365 URL 和 IP 地址范围](urls-and-ip-address-ranges.md)

[Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)

[评估 Office 365 网络连接](assessing-network-connectivity.md)

[Office 365 网络和性能优化](network-planning-and-performance.md)

[评估 Office 365 网络连接](assessing-network-connectivity.md)

[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)

[Office 365 性能疑难解答计划](performance-troubleshooting-plan.md)

[内容分发网络](content-delivery-networks.md)

[Office 365 网络载入工具](https://aka.ms/netonboard)

[Microsoft 如何构建其快速可靠的全局网络](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 网络博客](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
