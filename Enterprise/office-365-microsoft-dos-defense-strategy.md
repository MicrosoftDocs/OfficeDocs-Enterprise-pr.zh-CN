---
title: Microsoft 365 DoS 防护策略
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 在本文中，您可以找到针对拒绝服务 (DoS) 攻击的 Microsoft 防护策略的概述。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 242ec7a6fed574a0e5aa767ab31c28fc33b28e88
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605534"
---
# <a name="microsoft-365-denial-of-service-defense-strategy"></a>Microsoft 365 拒绝服务防护策略

Microsoft 针对基于网络的拒绝服务的策略防御 (DoS) 攻击因规模和全球占用量而独特。 此扩展使 Microsoft 能够利用策略和技术（组织、提供商或客户组织）可以与之相匹配。 DoS 策略的基础是我们的全球状态。 Microsoft 与 Internet 提供商（对等提供商） (公共和私有) ，以及世界各地的专用公司。 这为 Microsoft 提供了很大的 Internet 状态，使 Microsoft 能够吸收跨大型 surface 区域的攻击。

由于这种独特的特点，Microsoft 使用不同于大型企业使用的检测和缓解过程。 该策略基于多个网络边缘的检测和全局分布式缓解的分离。 许多企业使用第三方解决方案来检测和缓解边缘的攻击。 随着 Microsoft 的边缘容量增长，它会清楚对单个或特定边缘的任何攻击的重要性。 由于这种独特的配置，Microsoft 将检测和缓解组件分开。 Microsoft 部署多层检测系统，以检测更接近其饱和点的攻击，同时在边缘维护全局缓解。 此策略可确保我们可以同时处理多个并发攻击。

Microsoft 对 DoS 攻击所采用的最有效和低成本的防护之一是减少服务攻击面。 不需要的流量会在网络边缘断开，而无需对数据进行直接分析、处理和清理。

在与公用网络的接口上，Microsoft 使用专用安全设备进行防火墙、网络地址转换和 IP 筛选功能。 Microsoft 还使用全局同等成本多路径 (ECMP) 路由。 全局 ECMP 路由是一个网络框架，可确保有多个用于访问服务的全局路径。 使用这些多路径，针对服务的攻击仅限于攻击源自的地区。 其他区域应受到此攻击的影响，因为最终用户将使用其他路径到达这些区域中的服务。 Microsoft 还开发了内部 DoS 关联和检测系统，它们使用流数据、性能指标和其他信息。 这是 Microsoft Azure 中的超大型云服务，它将分析从 Microsoft 网络和服务上的各个点收集的数据。 跨工作负载 DoS 事件响应团队确定团队中的角色和职责、升级条件以及用于参与各种团队和事件处理的协议。 这些解决方案针对 DoS 攻击提供了基于网络的保护。

最后，基于云的工作负载根据其协议和带宽使用情况配置优化的阈值，以唯一保护该工作负载。
