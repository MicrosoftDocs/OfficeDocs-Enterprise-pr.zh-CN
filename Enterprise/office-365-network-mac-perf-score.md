---
title: Microsoft 365 网络评估（预览）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 网络评估（预览）
ms.openlocfilehash: 2ee18f50e841982e8f677964d2e7e57d95a209d8
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185743"
---
# <a name="microsoft-365-network-assessment-preview"></a>Microsoft 365 网络评估（预览）

在 Microsoft 365 管理中心与 Microsoft 365 页面的连接中，**网络评估**将许多网络性能指标的聚合提取到企业网络运行状况的快照中，用点值从 1-100 中表示。 网络评估的作用范围为整个租户和每个地理位置，用户将从该位置连接到你的租户，从而为 Microsoft 365 管理员提供一种简单的方法来即时了解企业网络运行状况的 gestalt，并快速深入到任何全球办公地点的详细报告。

网络评估点值是在查看时进行实时编译的延迟、带宽、下载速度和连接质量指标的平均度量。 Microsoft 拥有的网络的性能指标将从这些度量中排除，以确保评估结果明确且特定于企业网络。

![网络评估价值](Media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

非常低的网络评估价值表明 Microsoft 365 客户端将在连接到租户或维护响应前的用户体验时遇到严重问题，而较高的值表示配置正确的网络，且持续的性能问题很少。 80% 的值表示一个正常的基准，即您不应预期收到有关 Microsoft 365 连接或由于网络性能导致的响应的定期用户意见。 由于进行了重复的网络连接改进，因此此值将随用户体验的增加而增加。

>[!IMPORTANT]
>网络洞察力、Microsoft 365 管理中心中的性能建议和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Microsoft 365 租户。

## <a name="network-assessment-panel"></a>网络评估面板

每个网络评估（无论是属于租户还是特定办公室位置）都将显示一个面板，其中包含有关评估的详细信息。 此面板显示评估的条形图，以百分比表示，并作为每个组件工作负荷的总积分，包括仅收到度量数据的工作负荷。 对于 office 位置网络评估，我们还显示基准，即报告与您的办公室位置的数据位于同一个城市中的所有 Microsoft 365 客户端的中值。

![示例网络评估值](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

面板中的**评估细目**显示了每个组件工作负荷的评估。

**评估历史记录**显示了最近30天的评估和基准。

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>租户网络评估和 office 位置网络评估

网络评估可衡量办公室的网络外围位置到 Microsoft 网络的设计。 对网络周边的改进最好是在每个办公室位置完成，或者在网络连接聚合的位置进行改进，这可能会影响多个位置。

我们在 "网络性能概述" 页上显示整个 Microsoft 365 租户的网络评估值，并在该位置的 "摘要" 页面上显示每个检测到的 office 位置的特定值。

## <a name="exchange-online"></a>Exchange Online

对于 Exchange Online，衡量来自客户端计算机到 Exchange 前端服务器的 TCP 延迟。 这可能会受到网络通过客户 LAN 和 WAN 传输的距离的影响。 它还可能受到网络中间设备或服务的影响，这些服务会延迟连接或导致发送数据包。

## <a name="sharepoint-online"></a>SharePoint Online

对于 SharePoint Online，可以对用户访问文档的下载速度进行衡量。 这可能受客户端计算机和 Microsoft 网络之间网络线路上的可用带宽的影响。 通常，在复杂网络设备的瓶颈或较差的 Wlan 区域中存在的网络拥塞也会受到影响。

## <a name="microsoft-teams"></a>Microsoft Teams

对于 Microsoft 团队，网络质量是指 UDP 延迟、UDP 抖动和 UDP 数据包丢失。 UDP 可用于 Microsoft 团队的呼叫和会议音频和视频媒体连接。 这可能受到与延迟和下载速度相同的因素的影响，除了网络的 UDP 支持中的连接间隙之外，因为 UDP 是分别配置为更常见的 TCP 协议。

## <a name="related-topics"></a>相关主题

[Microsoft 365 管理中心中的网络性能建议（预览）](office-365-network-mac-perf-overview.md)

[Microsoft 365 网络性能见解（预览）](office-365-network-mac-perf-insights.md)

[M365 管理中心中的 Microsoft 365 网络载入工具（预览）](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 网络连接位置服务（预览）](office-365-network-mac-location-services.md)
