---
title: Office 365 网络连接概述
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: 讨论网络优化为何重要 SaaS 服务，Office 365 网络的目标和如何 SaaS 需要从其他工作负荷的不同网络。
ms.openlocfilehash: ebd7410ec5fe421561543f1223e455377e99e625
ms.sourcegitcommit: 09985cb7894725289ef1fc8ddd90b569c285c09e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2018
ms.locfileid: "25002351"
---
# <a name="office-365-network-connectivity-overview"></a>Office 365 网络连接概述

Office 365 提供通过多种多样微服务和应用程序的工作效率和协作方案分布式的软件作为-服务 (SaaS) 云。如 Outlook、 Word 和 PowerPoint 的 Office 365 的客户端组件在用户计算机上运行并连接到 Microsoft 数据中心中运行 Office 365 的其他组件。确定 Office 365 最终用户体验质量最重要的因素是网络可靠性和 Office 365 客户端和 Office 365 服务前盖之间的低延迟。

本文中，您将了解 Office 365 网络、 目标和 Office 365 网络为什么需要比一般 Internet 通信优化的不同方法。

## <a name="office-365-networking-goals"></a>Office 365 网络目标

Office 365 网络的最终目标是最松散访问客户端之间的关系较好的 Office 365 终结点，从而优化的最终用户体验。最终用户体验质量直接与的性能和用户使用的应用程序的响应。例如，Microsoft 团队依赖低延迟，以便用户电话呼叫、 会议和共享的屏幕协作是小故障释放，并 Outlook 依赖利用服务器端索引和 AI 的即时搜索功能强大的网络连接能力功能。

网络设计中的主要目标应以减少延迟通过减少的往返时间 (RTT) 从客户端计算机与 Microsoft 全局网络，Microsoft 的公用网络中枢的互连所有 Microsoft 数据中心的低延迟在世界各地分布的高可用性云应用程序入口点。您可以了解有关在[Microsoft 如何构建其快速且可靠的全局网络](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)的 Microsoft 全局网络的详细信息。

优化 Office 365 网络性能不需要很复杂。通过以下几项主要原则，可获得最佳性能：

- 确定 Office 365 网络流量
- 到 internet 的 Office 365 网络流量的本地分支出口允许从每个用户连接到 Office 365 的位置的位置
- 允许 Office 365 流量以绕过代理服务器和数据包检查设备

Office 365 网络连接原则的详细信息，请参阅[Office 365 网络连接原则](office-365-network-connectivity-principles.md)。

## <a name="traditional-network-architectures-and-saas"></a>传统网络体系结构和 SaaS

客户端/服务器工作负荷的传统网络体系结构原则设计周围客户端和终结点之间的通信不会扩展外部企业网络外围假设。此外，在很多企业网络中，所有出站的 Internet 连接遍历企业网络和出口从一个中心位置。

在传统网络体系结构，更高延迟的一般 Internet 通信是必要权衡为了维护网络外围安全和 Internet 通信的性能优化通常需要升级或向外扩展在网络出口点的设备。但是，此方法不能解决 SaaS 服务，例如 Office 365 的理想的网络性能的要求。

## <a name="identifying-office-365-network-traffic"></a>确定 Office 365 网络流量

我们正在使其更轻松地识别 Office 365 网络通信，并使其更易于管理网络标识。

- 新类别的网络终结点的不受影响的 Internet 延迟网络流量从区分高度重要的网络通信。有刚才的几个 Url 和支持的最重要的"优化"类别中的 IP 地址。
- 脚本使用情况或直接设备配置和更改管理的 Office 365 网络标识用于 web 服务。更改可从 web 服务，或以 RSS 格式，或使用 Microsoft 流模板的电子邮件。
- [Office 365 网络合作伙伴计划](http://aka.ms/Office365NPP)与 Microsoft 合作伙伴提供设备或服务，请按照 Office 365 网络连接原则和具有简单的配置。

## <a name="securing-office-365-connections"></a>保护 Office 365 连接

传统网络安全的目标是强化企业网络外围免受入侵和恶意攻击。大多数企业网络强制实施网络安全的 Internet 通信使用代理服务器、 防火墙、 SSL 中断的技术，并检查，深度数据包检查和数据丢失防护系统。这些技术提供的通用 Internet 请求的重要风险缓解时，但可以显著减少性能、 可伸缩性和应用到 Office 365 终结点时的最终用户体验质量。

Office 365 帮助满足您组织需求的内容安全性和数据使用率遵守内置的安全和管理功能，专为 Office 365 功能和工作负荷设计。有关 Office 365 安全性和遵从性的详细信息，请参阅[Office 365 安全指南](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap)。有关 Microsoft 的建议以及支持位置对 Office 365 流量执行高级处理的高级的网络解决方案的详细信息，请参阅[使用第三方网络设备或在 Office 365 通信解决方案](https://support.microsoft.com/en-us/help/2690045)。

## <a name="why-is-office-365-networking-different"></a>Office 365 网络连接不同

Office 365 专为终结点的安全和加密的网络连接，可减少外围安全实施的最佳性能。Office 365 数据中心位于世界各地，该服务旨在用于客户端连接到最佳可用的服务终结点的各种方法。用户数据和处理许多 Microsoft 数据中心之间分布，因为机可以连接到哪些客户端没有单个网络终结点。实际上，数据和 Office 365 租户中的服务动态优化的 Microsoft 全局网络以适应从中被最终用户访问的地理位置。

Office 365 流量受制数据包检测和集中的外出时，将创建某些常见的性能问题：

- 高延迟可能导致极差的视频和音频流的性能和数据检索、 搜索、 实时协作、 日历忙/闲信息、 产品内内容和其他服务的响应速度慢
- Egressing 从中心位置破坏了动态路由功能的 Office 365 全局网络连接，增加延迟和往返时间
- 解密受 SSL 保护 Office 365 网络流量和重新加密会导致协议错误并且具有安全风险

客户端通信及其地理位置尽可能近出口，从而缩短 Office 365 入口点的网络路径可以提高连接 Office 365 中的性能和最终用户体验。它还有助于降低到在 Office 365 性能和可靠性的网络体系结构的未来更改的影响。获得最佳 connectivity 模型是始终提供在用户的位置，而不考虑此位于企业网络或远程位置，如 home、 酒店或、 咖啡馆和机场网络出口。一般 Internet 通信和 WAN 基于企业网络流量将单独路由和不使用本地直接出口模型。下图中表示此本地直接出口模型。

![本地出口网络体系结构](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

本地出口体系结构的优点如下的 Office 365 网络流量通过传统的模型：
  
- 通过 Office 365 的最佳性能优化路由长度。最终用户连接由 Microsoft 全球网络_分布式服务前盖_基础结构，动态路由到最接近的 Office 365 入口点，然后路由流量内部到数据和服务的终结点通过 Microsoft 的超低的延迟高可用性暗光纤。
- 对于 Office 365 流量，绕过代理服务器和流量检查设备的本地出口，从而减少了企业网络基础结构上的负载。
- 利用客户端终结点安全和云安全功能，避免冗余网络安全技术的应用程序保护两端的连接。

> [!NOTE]
> _分布式服务前盖_基础结构是具有地理上分散的位置的 Microsoft 全局网络的高可用性和可扩展性网络边缘。它终止最终用户的连接，并高效地将其路由 Microsoft 全球网络内。您可以了解有关在[Microsoft 如何构建其快速且可靠的全局网络](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)的 Microsoft 全局网络的详细信息。

了解并应用 Office 365 网络连接原则的详细信息，请参阅[Office 365 网络连接原则](office-365-network-connectivity-principles#office-365-connectivity-principles)。

## <a name="conclusion"></a>结束语

优化 Office 365 网络性能真正涉及删除不必要的障碍。通过将 Office 365 连接视为受信任流量，您可以防止数据包检测和代理带宽的竞争引入延迟。允许客户端计算机和 Office 365 终结点之间的本地连接启用动态路由通过 Microsoft 全局网络通信。

## <a name="related-topics"></a>相关主题

[Office 365 网络连接原则](office-365-network-connectivity-principles.md)

[Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)

[管理 Office 365 终结点](managing-office-365-endpoints.md)

[Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)

[与 Office 365 的网络连接](network-connectivity.md)

[Office 365 网络和性能优化](network-planning-and-performance.md)

[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)

[Office 365 的性能疑难解答计划](performance-troubleshooting-plan.md)

[Microsoft 如何构建其快速且可靠的全局网络](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
