---
title: 适用于 Office 365 的 Azure ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: 了解如何将 azure expressroute 与 office 365 结合使用, 以及如何规划在部署 Azure expressroute 以用于 Office 365 时所需的网络实施项目。
ms.openlocfilehash: c8cff4ef85c4383ba04829cf3cf8da3a1bc36715
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490342"
---
# <a name="azure-expressroute-for-office-365"></a>适用于 Office 365 的 Azure ExpressRoute

了解如何将 azure expressroute 与 office 365 结合使用, 以及如何规划在部署 Azure expressroute 以用于 Office 365 时所需的网络实施项目。 在 Azure 中运行的基础结构和平台服务通常可解决网络体系结构和性能注意事项的好处。 在这些情况下, 我们建议为 Azure 提供 ExpressRoute。 作为服务产品 (如 Office 365 和 Dynamics 365) 构建为通过 Internet 安全可靠地访问。 您可以阅读有关 Internet 性能和安全性的信息, 以及在将[网络连接到 office 365](network-connectivity.md)中时, 您可能会考虑 office 365 的 Azure ExpressRoute。

> [!NOTE]
> 需要 Microsoft 授权才能使用适用于 Office 365 的 ExpressRoute。 当客户的法规要求要求直接连接时, Microsoft 会检查每个客户请求并授权 ExpressRoute for Office 365 的使用情况。 如果您有这样的要求, 请提供指向您所解释的法规的文本摘录和 web 链接, 这意味着在从[Office 365 请求的 ExpressRoute for Office 请求](https://aka.ms/O365ERReview)中需要直接连接才能开始 Microsoft 评审。 尝试为 Office 365 创建路由筛选器的未授权订阅将收到一[条错误消息](https://support.microsoft.com/kb/3181709)。 

现在, 您可以为选定的 office 365 网络流量添加到 office 365 的直接网络连接。 Azure ExpressRoute 提供了一个直接连接, 可预测的性能, 并附带了适用于 Microsoft 网络组件的 99.95% 的正常运行时间 SLA。 对于不受 Azure ExpressRoute 支持的服务, 您仍需要 internet 连接。

## <a name="planning-azure-expressroute-for-office-365"></a>规划适用于 Office 365 的 Azure ExpressRoute

除了 internet 连接之外, 还可以选择通过直接连接 (可预测性和 Microsoft 网络组件的 99.95% 正常运行时间 SLA) 将 Office 365 网络流量的子集路由。 Azure ExpressRoute 为你提供与 Office 365 和其他 Microsoft 云服务的专用网络连接。

无论您是否具有现有 MPLS WAN, 可以通过三种方式之一将 ExpressRoute 添加到网络体系结构中;通过受支持的云交换共同位置提供程序、以太网点到点连接提供程序或通过 MPLS 连接提供程序。 查看[您的区域中提供了哪些提供程序](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。 直接 ExpressRoute 连接将启用与在[其中包含 Office 365 服务](azure-expressroute.md#BKMK_WhatDoIGet)的应用程序的连接 (如下所示)。 所有其他应用程序和服务的网络流量将继续穿越 internet。

请考虑以下高级网络图表, 该图显示了通过 internet 连接到 microsoft 数据中心的典型 office 365 客户, 可访问所有 Microsoft 应用程序, 如 Office 365、Windows Update 和 TechNet。 客户使用类似的网络路径, 无论是从本地网络还是独立的 internet 连接进行连接。

![Office 365 网络连接](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

现在, 查看已更新的图表, 该图表描述了使用 internet 和 ExpressRoute 连接到 Office 365 的 Office 365 客户。 请注意, 某些连接 (如公用 DNS 和内容传递网络节点) 仍需要公共 internet 连接。 此外, 还请注意, 不位于其 ExpressRoute 连接建筑物中的客户用户通过 Internet 进行连接。

![使用 ExpressRoute 的 Office 365 连接](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

是否仍需要详细信息？ 了解如何[使用 azure expressroute for office 365 管理网络流量](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), 并了解如何为[office 365 配置 azure expressroute](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。 我们还在频道9上记录了10部分[Azure ExpressRoute for Office 365 培训](https://channel9.msdn.com/series/aer)系列, 以帮助更全面地解释这些概念。

([适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="what-office-365-services-are-included"></a>包含什么 Office 365 服务？
<a name="BKMK_WhatDoIGet"> </a>

下表列出了通过 ExpressRoute 支持的 Office 365 服务。 请查看 " [Office 365 终结点](https://aka.ms/o365endpoints)" 一文, 了解对这些应用程序的哪些网络请求需要 internet 连接。

|**包含的应用程序**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> Delve<sup>1</sup> <br/> |
|Skype for business Online<sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive for business<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|门户和共享<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD 连接<sup>1</sup> <br/> Office Online<sup>1</sup> <br/> |

<sup>1</sup>这些应用程序中的每个应用程序都具有不受 ExpressRoute 支持的 internet 连接要求, 请参阅[Office 365 终结点一文](https://aka.ms/o365endpoints)以了解详细信息。

适用于 office 365 的 ExpressRoute 不包含在 office 365 专业增强版客户端下载、内部部署标识提供程序登录和 office 365 (由 21 Vianet (在 21) 服务中) 的服务在中国。

([适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="implementing-expressroute-for-office-365"></a>实现适用于 Office 365 的 ExpressRoute

实施 ExpressRoute 需要参与网络和应用程序所有者, 并需要仔细规划以确定新的[网络路由体系结构](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、实现安全的带宽要求、高可用性等。 若要实现 ExpressRoute, 需要执行以下操作:

1. 全面了解 Office 365 连接规划中的需要 ExpressRoute 满足。 了解哪些应用程序将使用 internet 或 expressroute, 并在使用 internet 和 ExpressRoute for Office 365 流量的上下文中全面规划网络容量、安全性和高可用性需求。

2. 确定 internet 和 ExpressRoute 流量<sup>1</sup>的出口和对等位置。

3. 确定 internet 和 ExpressRoute 连接上所需的容量。

4. 制定了实施安全性和其他标准外围控制<sup>1</sup>的计划。

5. 具有有效的 Microsoft Azure 帐户以订阅 ExpressRoute。

6. 选择连接模型和[已批准的提供程序](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。 请注意, 客户可以选择多个连接模型或合作伙伴, 而合作伙伴不需要与现有网络提供程序相同。

7. 先验证部署, 然后再将流量定向到 ExpressRoute。

8. (可选)[实施 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)和评估区域扩展。

<sup>1</sup>重要的性能注意事项。 此处的决策可能会大大影响对诸如 Skype for business 等应用程序至关重要的延迟。

有关其他参考, 除了[ExpressRoute 文档](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)之外, 还应使用我们的[路由指南](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)。

若要购买适用于 Office 365 的 ExpressRoute, 您需要与一个或多个[已批准的提供商](https://azure.microsoft.com/documentation/articles/expressroute-locations/)合作, 以使用 ExpressRoute Premium 订阅设置所需的数量和大小电路。 没有其他许可证可从 Office 365 购买。

以下是可以用于返回的简短链接：[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

准备好注册适用于[Office 365 的 ExpressRoute](https://aka.ms/ert)吗？

([适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="related-topics"></a>相关主题

[与 Office 365 的网络连接](network-connectivity.md)

[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)

[使用 ExpressRoute for Office 365 路由](routing-with-expressroute.md)

[ExpressRoute for Office 365 网络计划](network-planning-with-expressroute.md)

[实现 ExpressRoute for Office 365](implementing-expressroute.md)

[在 ExpressRoute for Office 365 场景中使用 BGP 社区 (预览)](bgp-communities-in-expressroute.md)

[Skype for Business Online 中的媒体质量和网络连接性能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)

[Office 365 性能疑难解答计划](performance-troubleshooting-plan.md)

[Office 365 URL 和 IP 地址范围](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[Office 365 网络和性能优化](network-planning-and-performance.md)
