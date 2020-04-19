---
title: 概述：Office 365 的 VPN 拆分隧道
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/3/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: 指导如何使用 Office 365 VPN 拆分隧道为远程用户优化 Office 365 连接。
ms.openlocfilehash: d8f8d4364804395cd10eceb1aa55422f01cbe079
ms.sourcegitcommit: 58aa8b2e89685490f849e0392d566b7bfb7b933e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547650"
---
# <a name="optimize-office-365-connectivity-for-remote-users-using-vpn-split-tunnelling"></a>使用 VPN 拆分隧道为远程用户优化 Office 365 连接
<!---
>[!NOTE]
>This topic is part of a set of topics that address Office 365 optimization for remote users.
>- For VPN split tunnel implementation guidance, see [Implementing VPN split tunnelling for Office 365](office-365-vpn-implement-split-tunnel.md).
>- For information about optimizing Office 365 worldwide tenant performance for users in China, see [Office 365 performance optimization for China users](office-365-networking-china.md).
-->

对于通过 VPN 将远程工作设备与公司网络或云基础结构连接的客户，Microsoft 建议关键 Office 365 场景 **Microsoft Teams**、**SharePoint Online** 和 **Exchange Online** 通过 _VPN 拆分隧道_配置进行路由。 作为在新型冠状病毒肺炎（COVID-19）危机等大规模在家办公事件中促使员工持续保证工作效率的一线战略，这一点尤其重要。

![拆分隧道 VPN 配置](media/vpn-split-tunnelling/vpn-model-2.png)

_图 1：将定义的 Office 365 异常直接发送到服务的 VPN 拆分隧道解决方案。所有其他流量都将遍历 VPN 隧道，而不考虑目标。_

这种方法的本质是，为企业提供一种简单的方法来降低 VPN 基础结构饱和的风险，并在尽可能短的时间内显著提高 Office 365 的性能。 将 VPN 客户端配置为允许最关键、高容量 Office 365 流量绕过 VPN 隧道将获得以下好处：

- 立即缓解企业 VPN 体系结构中大多数客户报告的影响 Office 365 用户体验的性能和网络容量问题的根本原因
  
  建议的解决方案专门针对 [Office 365 URL 和 IP 地址范围](https://aka.ms/o365ips)主题中分类为**优化**的 Office 365 服务终结点。 流向这些终结点的流量对延迟和带宽限制非常敏感，使其绕过 VPN 隧道可显著改善最终用户体验，并减少公司网络负载。 不构成大部分带宽或用户体验足迹的 Office 365 连接可继续通过 VPN 隧道和 Internet 捆绑的其他流量进行路由。 有关详细信息，请参阅 [VPN 拆分隧道策略](#the-vpn-split-tunnel-strategy)。

- 可由客户快速配置、测试和实施，无需其他基础结构或应用程序要求

  根据 VPN 平台和网络体系结构，实现可能只需几个小时。 有关详细信息，请参阅[实现 VPN 拆分隧道](office-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunnelling)。

- 通过不更改其他连接的路由方式（包括到 Internet 的流量）来保留客户 VPN 实现的安全状况

  建议的配置遵循 VPN 流量异常的**最低特权**原则，并允许客户实现拆分隧道 VPN，而不会将用户或基础结构暴露于额外的安全风险中。 直接路由到 Office 365 终结点的网络流量会进行加密，由 Office 客户端应用程序堆栈验证其完整性，且范围限定为专用于 Office 365 服务的 IP 地址，这些地址在应用程序和网络级别都进行了强化。 有关详细信息，请参阅[安全专业人员和 IT 人员在当前独特的远程工作场景中实现新式安全控制的替代方法（Microsoft 安全团队博客）](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)。

- 由大多数企业 VPN 平台在本地提供支持

  Microsoft 与制作商业版 VPN 解决方案的行业合作伙伴持续协作，帮助合作伙伴开发与以上建议一致的解决方案的目标指南和配置模板。 有关详细信息，请参阅[适用于常见 VPN 平台的操作指南](office-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms)。

>[!TIP]
>Microsoft 建议重点关注 Office 365 服务记录的专用 IP 范围上的拆分隧道 VPN 配置。 虽然 FQDN 或基于 AppID 的拆分隧道配置可能适用于某些 VPN 客户端平台，但可能不能完全涵盖关键 Office 365 场景，并且可能与基于 IP 的 VPN 路由规则相冲突。 因此，Microsoft 不建议使用 Office 365 FQDN 来配置拆分隧道 VPN。 使用 FQDN 配置在其他相关方案中可能非常有用，例如 .pac 文件自定义或实现代理绕过。

有关完整的实现指南，请参阅[实现 Office 365 的 VPN 拆分隧道](office-365-vpn-implement-split-tunnel.md)。

## <a name="the-vpn-split-tunnel-strategy"></a>VPN 拆分隧道策略

传统的公司网络通常旨在在预云环境中安全工作，其中最重要的数据、服务和应用程序在本地托管，并且与大多数用户一样直接连接到内部公司网络。 因此，网络基础结构是围绕这些元素构建的，分支机构通过_多协议标签切换 (MPLS)_ 网络连接到总部，而远程用户必须通过 VPN 连接到公司网络才能访问本地终结点和 Internet。 在此模型中，来自远程用户的所有流量都将遍历公司网络，并通过公共出口点路由到云服务。

![强制 VPN 配置](media/vpn-split-tunnelling/vpn-model-1.png)

_图 2：适用于远程用户的公共 VPN 解决方案，其中所有流量都会被强制流回公司网络，而无需考虑目标_

随着组织将数据和应用程序移动到云，此模型效率开始下降，因为它很快变得累赘、费用高昂且不可缩放，这严重影响了用户的网络性能和效率，并限制了组织适应不断变化的需求的能力。 许多 Microsoft 客户报告几年前 80% 的网络流量都是指向内部目标，但到 2020 年 80% 以上的流量都连接到一个基于云的外部资源。

COVID-19 危机加剧了此问题，需要立即为绝大多数组织提供解决方案。 许多客户发现强制 VPN 模型的缩放性或性能不足以实现 100% 的远程工作场景，例如这次危机所需的远程工作场景。 为使这些组织继续高效运作，需要快速提供解决方案。

对于 Office 365 服务，Microsoft 在为服务设计连接要求时已充分考虑到这一问题，可在其中非常简单快速地优化一组集中的、严格控制和相对静态的服务终结点，以便为访问服务的用户提供高性能，减少 VPN 基础结构的负担，使其能够被仍然需要它的流量使用。

Office 365 将 Office 365 所需的终结点分为三类：**优化**、**允许**和**默认**。 **优化**终结点是我们的重点，具有以下特征：

- 为 Microsoft 拥有和托管的终结点，托管在 Microsoft 基础结构上
- 提供了 IP
- 低更改率，预计仍保持较小数量（目前有 20 个 IP 子网）
- 高容量和/或延迟敏感
- 可在服务中提供所需的安全元素，而不是在网络上内联
- 约占 Office 365 服务流量的 70-80%

这组严格限定范围的终结点可以从强制 VPN 隧道中分离出来，并通过用户的本地接口安全直接地发送到 Office 365 服务。 这称为**拆分隧道**。

可在服务内的不同层针对这些终结点更高效地传递 DLP、AV 保护、身份验证和访问控制等安全元素。 由于我们还将大部分流量从 VPN 解决方案中转移出去，这将为仍然依赖于它的业务关键流量释放 VPN 容量。 在许多情况下，它还应消除通过冗长而昂贵的升级程序来应对这种新操作方式的需要。

![拆分隧道 VPN 配置](media/vpn-split-tunnelling/vpn-model-2.png)

_图 3：将定义的 Office 365 异常直接发送到服务的 VPN 拆分隧道解决方案。所有其他流量都将强制流回公司网络（无论目标如何）。_

从安全角度来看，Microsoft 提供了一系列安全功能，可用于提供类似甚至增强的安全性，而不是由本地安全堆栈通过内联检查提供的安全性。 Microsoft 安全团队的博客文章[安全专业人员和 IT 人员在当前独特的远程工作场景中实现新式安全控制的替代方法](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)对可用功能进行了清晰的总结，你将在本文找到更详细的指导。 有关 Microsoft 实现 VPN 拆分隧道的信息，还可以参阅[运行 VPN：Microsoft 如何让远程工作人员互联](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)。

在许多情况下，可在几个小时内完成此实现，以便快速解决在组织迅速转变到全面远程工作时面临的最紧迫的问题之一。 有关 VPN 拆分隧道的实现指南，请参阅[实现 Office 365 的 VPN 拆分隧道](office-365-vpn-implement-split-tunnel.md)。

>[!NOTE]
>Microsoft 已经承诺至少在 **2020 年 6 月 30 日**前挂起对 Office 365“优化”**** 终结点的更改，以便客户专注于其他挑战，而不是在最初实施后维护终结点白名单。

## <a name="related-topics"></a>相关主题

[实现 Office 365 的 VPN 拆分隧道](office-365-vpn-implement-split-tunnel.md)

[面向中国用户的 Office 365 性能优化](office-365-networking-china.md)

[安全专业人员和 IT 人员在当前独特的远程工作场景中实现新式安全控制的替代方法（Microsoft 安全团队博客）](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[增强 Microsoft 的 VPN 性能：使用 Windows 10 VPN 配置文件以允许自动打开连接](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[运行 VPN：Microsoft 如何让远程工作人员互联](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Office 365 网络连接原则](office-365-network-connectivity-principles.md)

[评估 Office 365 网络连接](assessing-network-connectivity.md)

[Office 365 网络载入工具](https://aka.ms/netonboard)
