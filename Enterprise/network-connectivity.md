---
title: 与 Office 365 的网络连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 旨在使世界各地的客户，能够连接到使用连接到 internet 的服务。随着服务的发展，安全性、 性能和 Office 365 的可靠性得到改进基于上使用 internet 建立连接到服务的客户。
ms.openlocfilehash: b72b0a4584542e4c8673c7cf009c66aa97c6b81c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539776"
---
# <a name="network-connectivity-to-office-365"></a>与 Office 365 的网络连接

Office 365 旨在使世界各地的客户，能够连接到使用连接到 internet 的服务。随着服务的发展，安全性、 性能和 Office 365 的可靠性得到改进基于上使用 internet 建立连接到服务的客户。
  
规划使用 Office 365 的客户应评估其现有和预测的 internet 连接需要作为部署项目的一部分。对于企业类部署可靠且适当地调整 internet 连接是使用 Office 365 功能和方案的关键组成部分。
  
可以通过许多不同的人员和取决于您的规模和首选项的组织执行网络评估。评估网络范围根据其中您是在您的部署过程中也可能不同。为了帮助您更好地了解计执行网络评估，我们已生成的网络评估指南可帮助您了解对您可用的选项。此评估会确定哪些步骤和资源需要添加到部署项目，以使您能够成功采用 Office 365。
  
全面网络评估，如[Skype Operations Framework](https://www.skypeoperationsframework.com/)这些规定可以将提供的实现详细信息以及网络设计挑战可能的解决方案。大多数网络评估将指示网络连接到 Office 365 可容纳与[次要配置或设计更改](https://aka.ms/manageo365endpoints)现有的网络和 internet 出口基础结构。

一些评估将指示网络连接到 Office 365 需要其他投资的网络组件。例如，投资 WAN 带宽或优化路由的基础结构，以支持 internet 连接到 Office 365 中。有时评估将指示受法规或性能要求方案如[Skype 业务联机媒体质量的](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)网络连接到 Office 365。投资的 internet 连接基础结构、 路由优化和专用的直接连接可能会导致这些其他要求。
  
> [!NOTE]
> Microsoft 更改 Microsoft Peering 路由域的 Azure ExpressRoute 经过审阅的方式。启动 2017 年 7 月 31，所有 Azure ExpressRoute 客户可以都启用 Microsoft Peering Azure 管理控制台中直接或通过 PowerShell 自定义。启用后 Microsoft Peering，任何客户可以创建路由筛选器以接收 BGP 路由广告 Dynamics 365 客户服务应用程序 （以前称为，CRM Online）。客户需要为 Office 365 的 Azure ExpressRoute 必须从 Microsoft 获取审阅，他们可以针对 Office 365 中创建路由筛选器之前。请联系您的 Microsoft 帐户团队，若要了解有关如何启用 Office 365 ExpressRoute 审阅请求。尝试 Office 365 中创建路由筛选器的未经授权的订阅将收到[错误消息](https://support.microsoft.com/kb/3181709)。
  
规划 Office 365 您网络评估时要考虑的要点：
  
- Office 365 是运行公用 internet 上安全、 可靠、 高性能服务。我们继续以增强服务的以下方面的投资。所有 Office 365 服务都可通过 internet 连接。

- 我们在不断优化的核心的 Office 365 方面，例如可用性，全局访问，以及 internet 的性能基于连接。例如，许多 Office 365 服务利用扩展边缘节点面向 internet 的一组。此边缘网络提供最佳的邻近度和即将通过 internet 连接的性能。

- 在考虑使用 Office 365 的任何如 Skype 的业务 Online 语音、 视频或会议功能包括的服务时，客户必须完成的端到端网络评估并满足要求使用我们 Skype 操作框架。这些客户将有若干选项，以满足云连接，包括 ExpressRoute 的特定要求。

有，请查看 Microsoft 的案例研究[的 Microsoft Office 365 的优化网络性能](https://msdn.microsoft.com/en-us/library/mt450488.aspx)。如果您是要评估 Office 365 并不确保位置开始网络评估或已发现网络设计难题，您需要帮助克服，请与您的 Microsoft 帐户团队一起工作。
  
此外，阅读[Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)了解用于安全地管理 Office 365 流量和获取最佳性能的连接原则。本文将帮助您了解有关安全地优化 Office 365 网络连接的最新指南。
  
这是一个简短的链接，您可以使用回来： [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>另请参阅

[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 终结点常见问题](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Office 365 网络和性能优化](network-planning-and-performance.md)
  
[适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md)
  
[ExpressRoute for Office 365 路由](routing-with-expressroute.md)
  
[ExpressRoute for Office 365 网络规划](network-planning-with-expressroute.md)
  
[使用 Office 365 方案 (preview) 中 ExpressRoute BGP 社区 （英文）](bgp-communities-in-expressroute.md)
  
[媒体质量和 Skype 中的网络连接性能 for Business 联机](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)
