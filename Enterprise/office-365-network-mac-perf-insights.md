---
title: Office 365 网络性能见解（预览）
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
description: Office 365 网络性能见解（预览）
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106265"
---
# <a name="office-365-network-performance-insights-preview"></a>Office 365 网络性能见解（预览）

Microsoft 365 管理中心网络性能页面显示了 Office 365 网络见解，可帮助为你的办公室位置设计网络外围。 每个办公地点可能会显示五个特定的网络见解。

>[!IMPORTANT]
>网络性能建议、Microsoft 365 管理中心中的真知灼见和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Office 365 租户。

## <a name="backhauled-network-egress"></a>Backhauled 网络出口

从用户到网络传出的距离大于500英里（800公里），预计会影响性能。 建议对用户更接近的本地出口。

这表明办公室位置和网络出局之间的距离超过500英里。 办公室位置由模糊的客户端计算机位置标识，并且网络出口位置通过使用反向 IP 地址到 location 数据库来标识。 如果在计算机上禁用了 Windows 定位服务，则办公室位置可能不准确。 如果反向 IP 地址数据库信息不准确，则网络传出位置可能不准确。

此洞察力的详细信息包括办公地点、网络出口位置以及它们之间的距离。

为此，我们建议将网络出口离办公室位置更近，以便连接可以最适合在 Internet 上的 Microsoft 网络中和到 Office 365 服务的前端。 由于 Microsoft 会在将来对用户的网络出口进行关闭，因此 Microsoft 会在将来更好地扩展状态和 Office 365 服务前端的网络数据点。

在某些摘要视图中，这种洞察力缩写为 "出局"。

## <a name="better-performance-detected-for-customers-near-you"></a>为附近的客户检测到更好的性能

由于大都市区域中的大量客户的性能高于组织在此办公室位置的性能。

这就是与此办公室所在地在同一个城市中的 Office 365 客户的聚合性能。

![相对网络性能](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

我们在更好的性能存储桶中计算同一城市中的 Office 365 客户的百分比。 如果大于10%，则显示网络洞察力。

在某些摘要视图中，这种洞察力缩写为 "对等方"。

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>使用非最佳 Exchange Online 服务前门

用户未连接到最佳的 Office 365 服务前盖，这会影响性能。

我们列出了适用于办公室所在地城市的 Exchange Online 服务前盖，且具有出色的性能。 如果当前测试显示使用 Exchange Online 服务的前向不在此列表中，则我们称之为 "建议"。

使用非最佳 Exchange Online 服务前盖可能是由于网络 backhaul 在公司网络出口前，在这种情况下，我们建议本地和直接网络出口。 也可能是由于使用远程 DNS 递归冲突解决服务器而导致的，在这种情况下，我们建议您将 DNS 递归解析器服务器与网络出口对齐。

在某些摘要视图中，这种洞察力缩写为 "传送"。

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a>使用非最佳的 SharePoint Online 服务前盖

用户未连接到最接近的 SharePoint Online 服务前向门。 这预计会影响性能。

我们确定测试客户端连接到的 SharePoint Online 服务前向门。 然后，对于办公室所在地的城市，我们会将其与该城市的预期 SharePoint Online 服务前门进行比较。 如果不匹配，则建议这样做。

在某些摘要视图中，这种洞察力缩写为 "Afd"。

## <a name="low-download-speed-from-sharepoint-front-door"></a>SharePoint 前门的低下载速度

检测到的子最佳网络下载速度会影响从 OneDrive for Business 加载文档所需的时间。

用户可以从 SharePoint Online 和 OneDrive for business 服务前向前端获取的下载速度以每秒兆字节（MBps）为单位。 如果此值小于 1 MBps，则提供此洞察力。

若要提高用户可以获得带宽的下载速度，可能需要增加。 或者，在办公室地点的用户计算机与 SharePoint Online service 前门之间可能存在网络拥塞。 这有时称为 congestive 丢失，它限制了用户可以使用的下载速度，即使有足够的带宽可用。

在某些摘要视图中，这种洞察力缩写为 "吞吐量"。

## <a name="related-topics"></a>相关主题

[Microsoft 365 管理中心中的网络性能建议（预览）](office-365-network-mac-perf-overview.md)

[Office 365 网络评估（预览）](office-365-network-mac-perf-score.md)

[M365 管理中心中的 Office 365 网络载入工具（预览）](office-365-network-mac-perf-onboarding-tool.md)
