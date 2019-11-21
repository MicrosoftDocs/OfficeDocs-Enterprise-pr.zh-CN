---
title: 设置 Office 365 网络
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
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 摘要：请参阅以下文章，了解如何设置 Office 365 网络。
ms.openlocfilehash: 725c2470644206045a40816fad3643b83d6c8ea6
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747411"
---
# <a name="set-up-your-network-for-office-365"></a>设置 Office 365 网络

*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*

Office 365 载入的一个重要部分是要确保将网络和 Internet 连接设置为支持优化访问。配置可访问全球软件即服务 (SaaS) 云的本地网络与配置针对本地数据中心和中心 Internet 连接流量进行优化的传统网络是不一样的。 

使用以下文章来理解它们之间的关键区别，并修改你的边缘设备、客户端计算机和内部网络，以为本地用户获得最佳性能。

## <a name="how-office-365-networking-works"></a>Office 365 网络工作原理

请参阅以下文章，概括了解 Office 365 连接：

- [Office 365 网络连接概述](office-365-networking-overview.md)
- [Office 365 网络连接原则](office-365-network-connectivity-principles.md)
- [评估 Office 365 网络连接](assessing-network-connectivity.md)

有关增强性能的建议，请参阅 [Office 365 网络计划和性能优化](network-planning-and-performance.md)。

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a>以网络设备供应商身份支持 Office 365 网络

如果你是网络设备供应商，请加入 [Office 365 网络合作伙伴计划](office-365-networking-partner-program.md)。加入该计划即可在你的产品和解决方案中构建 Office 365 网络连接原则。 

## <a name="office-365-endpoints"></a>Office 365 端点

端点是 Internet 上 Office 365 流量的目的 IP 地址、DNS 域名和 URL 的集合。 

若要优化基于 Office 365 云的服务的性能，需要使用你的客户端浏览器和边缘网络中的设备对某些端点进行特殊处理。这些设备包括防火墙设备、SSL 中断与检查设备、数据包检查设备以及数据丢失防护系统。

有关详细信息，请参阅[管理 Office 365 端点](managing-office-365-endpoints.md)。

目前有五个不同的 Office 365 云。此表将转到每个端点的列表。

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


## <a name="additional-topics-for-office-365-networking"></a>Office 365 网络的其他主题

请参阅以下文章，了解 Office 365 网络中的特定主题：

- [内容传递网络](content-delivery-networks.md)
- [Office 365 服务中的 IPv6 支持](ipv6-support.md)
- [Office 365 的 NAT 支持](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a>适用于 Office 365 的 ExpressRoute

请参阅以下文章，了解适用于 Office 365 的 ExpressRoute 的流量使用：

- [适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md)
- [实现 ExpressRoute for Office 365](implementing-expressroute.md)
- [ExpressRoute for Office 365 网络计划](network-planning-with-expressroute.md)
- [通过适用于 Office 365 的 ExpressRoute 进行路由](routing-with-expressroute.md)
