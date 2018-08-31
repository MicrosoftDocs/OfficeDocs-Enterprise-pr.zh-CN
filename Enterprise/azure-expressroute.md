---
title: 适用于 Office 365 的 Azure ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
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
description: 了解如何使用 Office 365 使用 Azure ExpressRoute 以及如何规划如果您用于 Office 365 部署 Azure ExpressRoute 都需要网络实施项目。
ms.openlocfilehash: 5a82576b541e27c70bca490ff8dfe887ee879c83
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539570"
---
# <a name="azure-expressroute-for-office-365"></a>适用于 Office 365 的 Azure ExpressRoute

了解如何使用 Office 365 使用 Azure ExpressRoute 以及如何规划如果您用于 Office 365 部署 Azure ExpressRoute 都需要网络实施项目。在 Azure 中运行的基础结构和平台服务将通常受益寻址网络体系结构和性能注意事项。在这些情况下，我们建议对 Azure ExpressRoute。作为像已生成 Office 365 和 Dynamics 365 通过 Internet 访问安全可靠地服务产品的软件。因此，我们只建议 ExpressRoute 在特定情况下这些应用程序。您可以阅读有关 Internet 性能和安全性以及当您可能需要 for Office 365 的 Azure ExpressRoute 考虑[网络连接到 Office 365](network-connectivity.md)一文中。

> [!NOTE]
> 启动 2017 年 7 月 31，您可以直接从 Azure 管理控制台或使用 PowerShell 启用 Microsoft Peering。启用 Microsoft Peering 后，您可以创建路由筛选器以接收特定 BGP 路由广告。您将需要授权 Office 365 创建筛选器，并可以随时创建 Dynamics 365 客户服务应用程序 （以前称为，CRM Online） 筛选器。有关获取授权，以创建 Office 365 路由筛选器的过程与您的 Microsoft 帐户团队。尝试 Office 365 中创建路由筛选器的未经授权的订阅将收到[错误消息](https://support.microsoft.com/kb/3181709)

为所选的 Office 365 网络流量，现在可以添加直接网络连接到 Office 365。Azure ExpressRoute 提供直接连接，可预测的性能，并附带了 Microsoft 网络组件的运行时间 SLA 的 99.95%。您仍将通过 Azure ExpressRoute 不支持的服务需要 internet 连接。

## <a name="planning-azure-expressroute-for-office-365"></a>规划 Office 365 的 Azure ExpressRoute

除了 internet 连接，您可以选择通过提供可预测性和 Microsoft 网络组件 99.95%运行时间 SLA 的直接连接路由其 Office 365 网络流量的子集。Azure ExpressRoute 您提供此专用的网络连接到 Office 365 和其他 Microsoft 云服务。

无论是否具有现有的 MPLS WAN，ExpressRoute 可添加到您的网络体系结构中有三种方法;通过支持的云 exchange 共同位置提供程序，以太网点对点连接提供程序，或通过 MPLS 连接提供程序。请参阅什么的[提供程序是您所在的地区中可用](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。直接 ExpressRoute 连接将启用连接到应用程序中概述[什么 Office 365 服务都包含？](azure-expressroute.md#BKMK_WhatDoIGet)下方。所有其他应用程序和服务的网络流量将继续在 internet。

请考虑下的高级别网络图，其中显示典型 Office 365 客户通过 internet 访问 Office 365、 Windows Update 和 TechNet 等的所有 Microsoft 应用程序以连接到 Microsoft 数据中心。客户使用类似的网络路径，无论他们是否仅当连接从本地网络或从独立的 internet 连接。

![Office 365 网络连接](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

现在查看描述了 Office 365 客户使用的 internet 和 ExpressRoute 连接到 Office 365 的更新图表。请注意，例如公共 DNS 和内容交付网络节点某些连接仍然需要公共 internet 连接。另请注意不位于其 ExpressRoute 连接的构建通过 Internet 进行连接的客户的用户。

![Office 365 连接 ExpressRoute](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

仍需要的详细信息？了解如何[管理您的网络流量与 Office 365 的 Azure ExpressRoute](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)并了解如何[配置 Office 365 的 Azure ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。我们还录制可帮助更全面地介绍的概念第 9 频道上一个 10 部分[Azure ExpressRoute 有关 Office 365 培训](https://channel9.msdn.com/series/aer)系列。

([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="what-office-365-services-are-included"></a>包含哪些 Office 365 服务？
<a name="BKMK_WhatDoIGet"> </a>

下表列出通过 ExpressRoute 支持的 Office 365 服务。请查看[Office 365 终结点文章](https://aka.ms/o365endpoints)了解这些应用程序的网络请求需要 internet 连接。

|**包括的应用程序**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> 深入<sup>1</sup> <br/> |
|Skype 业务联机<sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive for Business<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|门户和共享的<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD 连接<sup>1</sup> <br/> Office Online<sup>1</sup> <br/> |

<sup>1</sup>所有这些应用程序具有通过 ExpressRoute 不支持的 internet 连接要求，请参阅[Office 365 终结点文章](https://aka.ms/o365endpoints)的详细信息。

不包含在 Office 365 ExpressRoute 服务是 Office 365 ProPlus 客户端下载、 本地标识提供程序注册，和在中国 （由 21 Vianet） 的 Office 365 服务。

([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="implementing-expressroute-for-office-365"></a>实现 ExpressRoute for Office 365

实现 ExpressRoute 需要网络和应用程序所有者的参与，需要仔细规划以确定新[网络路由体系结构](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、 带宽要求，将安全实施，高可用性等等。若要实现 ExpressRoute，您将需要：

1. 完全了解 ExpressRoute 满足 Office 365 连接计划中的需求。了解哪些应用程序将使用的 internet 或 ExpressRoute 和完全规划网络容量、 安全性和高可用性所需的 Office 365 中使用的 internet 和 ExpressRoute 上下文中通信。

2. 确定出口和对等位置的 internet 和 ExpressRoute 流量<sup>1</sup>。

3. 确定在 internet 和 ExpressRoute 连接上所需的容量。

4. 用于实现安全性和其他标准外围控件<sup>1</sup>就地具有计划。

5. 具有有效的 Microsoft Azure 帐户以订阅 ExpressRoute。

6. 选择连接模型和[批准提供程序](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。请记住，客户可以选择多个连接模型或合作伙伴和合作伙伴不需要与您现有的网络提供程序。

7. 验证前将流量定向到 ExpressRoute 的部署。

8. （可选）[实现 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)和评估区域扩展。

<sup>1</sup>重要性能注意事项。此处决策可以显著影响这很关键的应用程序，如 for Business 的 Skype 的延迟。

对于其他参考，使用我们除了[ExpressRoute 文档](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)的[传送指南](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)。

要为 Office 365 购买 ExpressRoute，您将需要使用一个或多个[批准提供程序](https://azure.microsoft.com/documentation/articles/expressroute-locations/)设置的所需的数量和大小电路使用 ExpressRoute Premium 订阅。没有要从 Office 365 购买附加许可证。

这是一个简短的链接，您可以使用回来：[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

为注册[Office 365 ExpressRoute](https://aka.ms/ert)准备？

([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="related-topics"></a>相关主题
<a name="BKMK_End"> </a>

[与 Office 365 的网络连接](network-connectivity.md)

[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)

[ExpressRoute for Office 365 路由](routing-with-expressroute.md)

[ExpressRoute for Office 365 网络规划](network-planning-with-expressroute.md)

[实现 ExpressRoute for Office 365](implementing-expressroute.md)

[使用 Office 365 方案 (preview) 中 ExpressRoute BGP 社区 （英文）](bgp-communities-in-expressroute.md)

[媒体质量和 Skype 中的网络连接性能 for Business 联机](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)

[Office 365 的性能疑难解答计划](performance-troubleshooting-plan.md)

[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Office 365 网络和性能优化](network-planning-and-performance.md)
