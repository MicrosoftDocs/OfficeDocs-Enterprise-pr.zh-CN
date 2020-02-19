---
title: Microsoft 365 管理中心中的网络性能建议（预览）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 管理中心中的网络性能建议概述（预览）
ms.openlocfilehash: d944814effc62956d5047bad1f3088d0919793ee
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106259"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Microsoft 365 管理中心中的网络性能建议（预览）

Microsoft 365 管理中心中的网络性能页面显示了企业客户的网络洞察力和网络分数。 网络洞察力是专门推荐的网络体系结构设计更改，用于改进与 Office 365 的网络连接相关的用户体验和网络分数显示网络连接如何影响用户体验，以使不同的用户位置网络连接。 使用具有多个办公室位置的 Office 365 的企业和不重要的网络外围体系结构可以在最初加入 Office 365 的过程中受益，或修复使用情况发现的网络性能问题增量. 对于使用 Office 365 的小型企业或已具有简单且直接的网络连接的企业，这通常是不必要的。 具有500个以上的用户和多个办公地点的企业有望获益最多。

>[!IMPORTANT]
>网络性能建议、Microsoft 365 管理中心中的真知灼见和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Office 365 租户。

## <a name="enterprise-network-connectivity-challenges"></a>企业网络连接难题

![客户网络到云](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

许多企业都具有网络外围配置，这些配置随着时间的推移而逐渐发展，主要旨在适应员工 Internet 网站访问，其中大多数网站都不是预先知道的，不受信任。 这些未知网站的受攻击和必要的重点是避免恶意软件和钓鱼攻击。 此网络配置策略虽然有助于安全目的，但会导致 Office 365 用户性能和用户体验下降。 企业可以改进用户体验，但还可以通过使用 Microsoft 365 管理中心网络性能功能，通过遵循[Office 365 连接原则](https://aka.ms/pnc)继续保护其环境。 此功能有助于实现与 Office 365 连接原则相适应的网络体系结构设计，并应导致针对 Office 365 连接的优化网络性能。

## <a name="how-we-can-solve-these-challenges"></a>我们可以如何解决这些难题

有时，Microsoft 需要调查大型企业客户的 Office 365 的网络性能问题，并且这些问题通常有与客户网络出口基础结构相关的根本原因。 当发现客户网络外围问题的常见根源时，我们会设法确定确定它的简单测试指标。 具有确定特定问题的度量阈值的测试非常有用，因为我们可以在任何位置测试相同的指标，告知是否存在此根本原因，并将其共享为与管理员的网络洞察力。 一些网络见解只表示需要进一步调查的问题。 一种网络洞察力，其中我们有足够的测试来显示解决根本原因的特定修正操作，作为建议的操作列出。 这些基于预先确定的阈值的网络洞察力比一般的最佳做法建议更有价值，因为您不必询问是否应用某种最佳实践，并且将导致显著的用户体验改善.

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理中心中的网络性能概述

Microsoft 提供了多个支持 Office 365 操作的 Office 桌面和 web 客户端的现有网络度量。 这些度量现在用于提供网络体系结构设计见解和网络性能分数，这些分数显示在 Microsoft 365 管理中心的网络性能页面中。

与网络度量相关联的近似位置信息可以识别客户端设备所在的城市。 这用于显示客户的办公室位置和网络度量，以提供该办公室位置的网络见解。 每个位置的网络得分显示颜色，每个位置的用户相对数量由圆的大小表示。 "概述" 页还显示了客户的网络分数作为所有办公地点的加权平均值。

## <a name="specific-office-location-network-performance-summary-and-insights"></a>特定的办公室位置网络性能摘要和见解

选择 "office 位置" 将打开 "特定位置的摘要" 页。 我们将显示从该办公室位置的度量中标识的网络传出的详细信息。

"Office 位置摘要" 页还会显示位置网络分数、网络分数历史记录、此位置与同一城市中的其他客户的比较，以及客户可以执行的特定见解和建议的列表。改进其网络连接。 同一个城市中的客户之间的比较取决于所有客户都具有对网络服务提供商、电信基础结构和附近 Microsoft 网络状态点的同等访问权限的预期。

"Office 位置" 页上的 "详细信息" 选项卡显示了用于提供任何见解、建议和网络分数的具体测量结果。 提供此信息是为了让网络工程师能够验证其环境中的任何约束或细节方面的建议和因素。
对于希望提高 office 位置和建议的准确性的客户，我们允许输入更具体的信息。 这是通过编辑发现的位置信息来实现的，并且可以减少可用于网络度量的位置信息中固有的近似值。

## <a name="faq"></a>常见问题解答

### <a name="what-is-office-365-service-front-door"></a>什么是 Office 365 服务前盖？

Office 365 service 前门是 Microsoft 全球网络中的一个入口点，Office 客户端和服务终止其网络连接。 为实现到 Office 365 的最佳网络连接，建议您的网络连接在您所在城市或地铁的最接近的 Office 365 前向外端终止。
注意： Office 365 service 前向在 Azure marketplace 中提供了与 "Azure 前门服务" 产品的直接关系。

### <a name="what-is-an-optimal-office-365-service-front-door"></a>什么是最佳的 Office 365 服务的前盖？

最佳的 Office 365 服务前盖是最接近你的网络出口（通常在你所在的城市或大都市区域中）的一门。 使用 Office 365 网络性能工具来确定正在使用的 Office 365 服务的前盖和最佳服务前盖的位置。 如果该工具确定你的使用中的前向门是最佳的，则表示你正在以最佳方式连接到 Microsoft 的全球网络。

### <a name="what-is-an-internet-egress-location"></a>Internet 出口的位置是什么？

Internet 出局位置是网络流量退出企业网络并连接到 Internet 的位置。 这也被标识为您拥有网络地址转换（NAT）设备且通常与 Internet 服务提供商（ISP）进行连接的位置。 如果你发现您的位置和 internet 出局位置之间的距离很长，则这可能会发现重要的 WAN backhaul。

## <a name="related-topics"></a>相关主题

[Office 365 网络性能见解（预览）](office-365-network-mac-perf-insights.md)

[Office 365 网络评估（预览）](office-365-network-mac-perf-score.md)

[M365 管理中心中的 Office 365 网络载入工具（预览）](office-365-network-mac-perf-onboarding-tool.md)
