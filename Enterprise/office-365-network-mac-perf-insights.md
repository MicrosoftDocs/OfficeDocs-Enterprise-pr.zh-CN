---
title: Microsoft 365 网络见解（预览）
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
description: Microsoft 365 网络见解（预览）
ms.openlocfilehash: baab4716ace0b15df5878d21987c037372a2754e
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185753"
---
# <a name="microsoft-365-network-insights-preview"></a>Microsoft 365 网络见解（预览）

**网络洞察力**是从 Microsoft 365 租户收集的实时性能指标，仅供租户中的管理用户查看。 Insights 显示在 Microsoft 365 管理中心的中<https://portal.microsoft.com/adminportal/home#/networkperformance>。

Insights 旨在帮助为你的办公室位置设计网络外围。 每个真知灼见都提供有关用户访问你的租户的每个地理位置的特定常见问题的性能特征的实时详细信息。

可以为每个办公室位置显示五个特定的网络见解：

- [Backhauled 网络出口](#backhauled-network-egress)
- [为附近的客户检测到更好的性能](#better-performance-detected-for-customers-near-you)
- [使用非最佳 Exchange Online 服务前门](#use-of-a-non-optimal-exchange-online-service-front-door)
- [使用非最佳 SharePoint Online 服务前盖](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [SharePoint 前门的低下载速度](#low-download-speed-from-sharepoint-front-door)

>[!IMPORTANT]
>网络洞察力、Microsoft 365 管理中心中的性能建议和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Microsoft 365 租户。

## <a name="backhauled-network-egress"></a>Backhauled 网络出口

如果网络 insights 服务检测到网络传出的给定用户位置的距离大于500英里（800公里），则会显示此洞察力，这表明 Microsoft 365 流量正 backhauled 为公共 Internet 边缘设备或代理。

在某些摘要视图中，这种洞察力缩写为 "出局"。

![Backhauled 网络出口](Media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a>应用场景

这表示办公室地点和网络出口之间的距离超过500英里（800公里）。 办公室位置由模糊的客户端计算机位置标识，并且网络出口位置通过使用反向 IP 地址到 location 数据库来标识。 如果在计算机上禁用了 Windows 定位服务，则办公室位置可能不准确。 如果反向 IP 地址数据库信息不准确，则网络传出位置可能不准确。

此洞察力的详细信息包括办公地点、位置总数的租户用户总数、当前网络传出位置、传出位置的相关性、位置和当前出口点之间的距离、第一次检测条件的日期以及解决条件的日期。

### <a name="what-should-i-do"></a>该怎么办？

为此，我们建议网络出口离办公室位置更近，以便连接可以最佳路由到 Microsoft 的全局网络和最接近的 Microsoft 365 服务前盖。 由于 Microsoft 会在将来对用户的网络出口进行关闭，因此 Microsoft 会在将来对状态和 Microsoft 365 服务前端展开网络点和 Microsoft 服务之前提供改进的性能。

有关如何解决此问题的详细信息，请参阅[Office 365 网络连接原则](office-365-network-connectivity-principles.md)中的[本地传出网络连接](office-365-network-connectivity-principles.md#egress-network-connections-locally)。

## <a name="better-performance-detected-for-customers-near-you"></a>为附近的客户检测到更好的性能

如果网络 insights 服务检测到您的地铁区域中的大量客户具有比在此办公室位置的组织中的用户更好的性能，则会显示此洞察力。

在某些摘要视图中，这种洞察力缩写为 "对等方"。

![相对网络性能](Media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a>应用场景

此真知灼见将检查与此办公室所在地在同一个城市中的 Microsoft 365 客户的聚合性能。 如果用户的平均延迟大于邻近租户平均延迟的10%，则会显示此洞察力。

### <a name="what-should-i-do"></a>该怎么办？

此条件的原因可能有多种，包括公司网络或 ISP 中的延迟、瓶颈或体系结构设计问题。 检查您的办公室网络和当前 Microsoft 365 前端之间路由中的每个跃点之间的延迟。 有关详细信息，请参阅[Office 365 网络连接原则](office-365-network-connectivity-principles.md)。

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>使用非最佳 Exchange Online 服务前门

如果网络 insights 服务检测到特定位置中的用户未连接到最佳 Exchange Online 服务前盖，将显示此洞察力。

在某些摘要视图中，这种洞察力缩写为 "传送"。

![非最佳前盖](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a>应用场景

我们列出了适用于办公室所在地城市的 Exchange Online 服务前盖，且具有出色的性能。 如果当前测试显示使用 Exchange Online 服务的前向不在此列表中，则我们称之为 "建议"。

### <a name="what-should-i-do"></a>该怎么办？

使用非最佳 Exchange Online 服务前盖可能是由于网络 backhaul 在公司网络出口前，在这种情况下，我们建议本地和直接网络出口。 也可能是由于使用远程 DNS 递归冲突解决服务器而导致的，在这种情况下，我们建议您将 DNS 递归解析器服务器与网络出口对齐。

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a>使用非最佳 SharePoint Online 服务前盖

如果网络 insights 服务检测到特定位置中的用户未连接到最近的 SharePoint Online 服务前向，将显示此洞察力。

在某些摘要视图中，这种洞察力缩写为 "Afd"。

![非最佳前盖](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a>应用场景

我们确定测试客户端连接到的 SharePoint Online 服务前向门。 然后，对于办公室所在地的城市，我们会将其与该城市的预期 SharePoint Online 服务前门进行比较。 如果不匹配，则建议这样做。

### <a name="what-should-i-do"></a>该怎么办？

使用非最佳的 SharePoint Online 服务前盖可能是由于网络 backhaul 在公司网络出口之前导致的，因此我们建议本地和直接网络出口。 也可能是由于使用远程 DNS 递归冲突解决服务器而导致的，在这种情况下，我们建议您将 DNS 递归解析器服务器与网络出口对齐。

## <a name="low-download-speed-from-sharepoint-front-door"></a>SharePoint 前门的低下载速度

如果网络 insights 服务检测到特定的办公室位置和 SharePoint Online 之间的带宽小于 1 MBps，则会显示此洞察力。

在某些摘要视图中，这种洞察力缩写为 "吞吐量"。

### <a name="what-does-this-mean"></a>应用场景

用户可以从 SharePoint Online 和 OneDrive for business 服务前向前端获取的下载速度以每秒兆字节（MBps）为单位。 如果此值小于 1 MBps，则提供此洞察力。

### <a name="what-should-i-do"></a>该怎么办？

为了提高下载速度，可能需要增加带宽。 或者，在办公室地点的用户计算机与 SharePoint Online service 前门之间可能存在网络拥塞。 这有时称为 congestive 丢失，它限制了用户可以使用的下载速度，即使有足够的带宽可用。

## <a name="china-user-optimal-network-egress"></a>中国用户最佳网络出口

如果组织的用户在连接到你的 Microsoft 365 租户的其他地理位置，则会显示此洞察力。 

### <a name="what-does-this-mean"></a>应用场景

如果您的组织具有专用 WAN 连接，我们建议您在中国的办公室位置配置网络 WAN 电路，在以下任一位置将网络出口到 Internet：

- 香港特别行政区
- 日本
- 中国台湾
- 韩国
- 新加坡
- 马来西亚

远离用户的 Internet 出口与这些位置相比会降低性能，而在中国的出口可能导致由于交叉边界拥塞导致的高延迟和连接问题。

### <a name="what-should-i-do"></a>该怎么办？

有关如何缓解与此洞察力相关的性能问题的详细信息，请参阅[适用于中国用户的 Office 365 全局租户性能优化](https://docs.microsoft.com/office365/enterprise/office-365-networking-china)。

## <a name="related-topics"></a>相关主题

[Microsoft 365 管理中心中的网络性能建议（预览）](office-365-network-mac-perf-overview.md)

[Microsoft 365 网络评估（预览）](office-365-network-mac-perf-score.md)

[M365 管理中心中的 Microsoft 365 网络载入工具（预览）](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 网络连接位置服务（预览）](office-365-network-mac-location-services.md)
