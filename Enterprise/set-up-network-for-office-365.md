---
title: 为 Microsoft 365 设置你的网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 摘要：请参阅以下文章以了解适用于 Microsoft 365 的网络。
ms.openlocfilehash: 4c414d8cbf597af9165e991a71e5d6a6a330e33a
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735651"
---
# <a name="set-up-your-network-for-microsoft-365"></a>为 Microsoft 365 设置你的网络

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection. 

使用以下文章来理解它们之间的关键区别，并修改你的边缘设备、客户端计算机和内部网络，以为本地用户获得最佳性能。

## <a name="how-microsoft-365-networking-works"></a>Microsoft 365 网络的工作原理

请参阅以下文章，了解 Microsoft 365 的连接概述：

- [Microsoft 365 网络连接概述](office-365-networking-overview.md)
- [Microsoft 365 网络连接原则](office-365-network-connectivity-principles.md)
- [评估 Microsoft 365 网络连接](assessing-network-connectivity.md)

有关增强性能的建议，请参阅[适用于 Microsoft 365 的网络规划和性能调整](network-planning-and-performance.md)。

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>支持将 Microsoft 365 网络作为网络设备供应商

If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions. 

## <a name="office-365-endpoints"></a>Office 365 端点

端点是 Internet 上 Office 365 流量的目的 IP 地址、DNS 域名和 URL 的集合。 

To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.

有关详细信息，请参阅[管理 Office 365 端点](managing-office-365-endpoints.md)。

There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.

|||
|:-------|:-----|
| [全球端点](urls-and-ip-address-ranges.md) | 针对全球 Office 365 订阅的端点，其中包括美国政府社区云 (GCC) 订阅。 |
| [美国政府 DoD 端点](office-365-u-s-government-dod-endpoints.md) | 针对美国国防部 (DoD) 订阅的端点。 |
| [美国政府 GCC 高端点](office-365-u-s-government-gcc-high-endpoints.md) | 针对美国政府社区云高（GCC 高）订阅的端点。 |
| [由世纪互联运营的 Office 365 端点](urls-and-ip-address-ranges-21vianet.md) | 由世纪互联运营的 Office 365 的端点，旨在满足中国境内对 Office 365 的需求。 |
| [Office 365 Germany 端点](office-365-germany-endpoints.md) | 为德国、欧盟 (EU) 和欧洲自由贸易协会 (EFTA) 中监管最严格的客户在欧洲建立的独立云的端点。 |
|||

若要自动获取 Office 365 云的最新端点列表，请参阅 [Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)。

有关额外的端点，请参阅以下文章：

- [Web 服务中未包含的其他端点](additional-office365-ip-addresses-and-urls.md)
- [Office 2016 for Mac 中的网络请求](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Microsoft 365 网络的其他主题

请参阅以下文章，了解 Microsoft 365 网络中的专门主题：

- [内容传递网络](content-delivery-networks.md)
- [Office 365 服务中的 IPv6 支持](ipv6-support.md)
- [Office 365 的 NAT 支持](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a>适用于 Microsoft 365 的 ExpressRoute

请参阅以下文章，了解适用于 Office 365 的 ExpressRoute 的流量使用：

- [适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md)
- [实现 ExpressRoute for Office 365](implementing-expressroute.md)
- [ExpressRoute for Office 365 网络计划](network-planning-with-expressroute.md)
- [通过适用于 Office 365 的 ExpressRoute 进行路由](routing-with-expressroute.md)
