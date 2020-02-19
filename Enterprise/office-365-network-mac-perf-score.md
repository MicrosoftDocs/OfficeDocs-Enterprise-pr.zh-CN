---
title: Office 365 网络评估（预览）
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
description: Office 365 网络评估（预览）
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106258"
---
# <a name="office-365-network-assessment-preview"></a>Office 365 网络评估（预览）

Office 365 网络评估表明了客户网络连接的相对用户体验的影响。 任何 Microsoft 拥有的网络连接的影响将排除在此之外，以使客户能够优化他们负责的网络设计。

它是从影响关键 Office 365 工作负荷中的用户体验的度量计算出来的，并显示为范围为0到100的百分比。

较低的网络分数表示 Office 365 客户端在连接或剩余用户响应时遇到严重问题。 分数为80% 表示网络连接，您不应预计收到有关 Office 365 用户体验的用户抱怨，因为网络性能。 随着网络连接的改进，此分数将随用户体验的增加而增加。

>[!IMPORTANT]
>网络性能建议、Microsoft 365 管理中心中的真知灼见和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Office 365 租户。

## <a name="exchange-online"></a>Exchange Online

对于 Exchange Online，衡量来自客户端计算机到 Exchange 前端服务器的 TCP 延迟。 这可能会受到网络通过客户 LAN 和 WAN 传输的距离的影响。 它还可能受到网络中间设备或服务的影响，这些服务会延迟连接或导致发送数据包。

## <a name="sharepoint-online"></a>SharePoint Online

对于 SharePoint Online，可以对用户访问文档的下载速度进行衡量。 这可能受客户端计算机和 Microsoft 网络之间网络线路上的可用带宽的影响。 通常，在复杂网络设备的瓶颈或较差的 Wlan 区域中存在的网络拥塞也会受到影响。

## <a name="microsoft-teams"></a>Microsoft Teams

对于 Microsoft 团队，网络质量是指 UDP 延迟、UDP 抖动和 UDP 数据包丢失。 UDP 可用于 Microsoft 团队的呼叫和会议音频和视频媒体连接。 这可能受到与延迟和下载速度相同的因素的影响，除了网络的 UDP 支持中的连接间隙之外，因为 UDP 是分别配置为更常见的 TCP 协议。

## <a name="tenant-network-score-and-office-location-network-score"></a>租户网络分数和办公室位置网络分数

网络分数用于衡量在 Microsoft 网络中办公室位置的网络外围的设计。 对网络周边的改进最好是在每个办公室位置完成，或者在网络连接聚合的位置进行改进，这可能会影响多个位置。
我们为 "网络性能概述" 页面上的整个 Office 365 租户显示网络分数，在该位置的 "摘要" 页面上显示每个检测到的 office 位置的特定网络分数。

## <a name="network-score-panel"></a>网络排名面板

每个网络分数无论是针对租户还是针对特定的办公室位置，都会显示一个面板，其中包含有关分数的详细信息。 此面板显示分数的条形图，以百分比表示，并作为每个组件工作负荷的总分数，包括仅收到度量数据的工作负荷。 对于 "办公室位置网络分数"，我们还会显示基准，即报告与您的办公室位置的数据位于同一城市的所有 Office 365 客户端的中值。

面板中的分数细分显示了每个组件工作负荷的分数。

分数历史记录显示了得分和基准的过去30天。

## <a name="related-topics"></a>相关主题

[Microsoft 365 管理中心中的网络性能建议（预览）](office-365-network-mac-perf-overview.md)

[Office 365 网络性能见解（预览）](office-365-network-mac-perf-insights.md)

[M365 管理中心中的 Office 365 网络载入工具（预览）](office-365-network-mac-perf-onboarding-tool.md)
