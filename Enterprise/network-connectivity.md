---
title: Office 365 的网络连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
audience: ITPro
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
description: Office 365 旨在让世界各地的客户能够使用 internet 连接连接到服务。 随着服务的演变, Office 365 的安全性、性能和可靠性根据使用 internet 的客户建立与服务的连接而得到改进。
ms.openlocfilehash: 4510cb073c0fde64abc4ee796a55d7ef32662f8c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069868"
---
# <a name="network-connectivity-to-office-365"></a>Office 365 的网络连接

Office 365 旨在让世界各地的客户能够使用 internet 连接连接到服务。 随着服务的演变, Office 365 的安全性、性能和可靠性根据使用 internet 的客户建立与服务的连接而得到改进。
  
计划使用 Office 365 的客户应评估其现有和预测的 internet 连接需要作为部署项目的一部分。 对于企业级部署, 可靠性和适当调整的 internet 连接性是使用 Office 365 功能和方案的关键部分。
  
根据您的大小和偏好, 许多不同的人员和组织可以执行网络评估。 评估的网络范围也可能因您在部署过程中所处的位置而异。 为了帮助您更好地了解执行网络评估所需的内容, 我们生成了一个网络评估指南, 帮助您了解可用的选项。 此评估将确定要将哪些步骤和资源添加到部署项目, 以使您能够成功采用 Office 365。
  
像[Skype 运营框架](https://www.skypeoperationsframework.com/)中规定的那样, 全面的网络评估将提供可能的解决方案, 以实现网络设计难题以及实现详细信息。 大多数网络评估将指示到 Office 365 的网络连接可适应现有网络和 internet 出口基础结构的[次要配置或设计更改](https://aka.ms/manageo365endpoints)。

某些评估将指示到 Office 365 的网络连接需要在网络组件中进行额外的投资。 例如, WAN 带宽或优化的路由基础结构中的投资, 以支持到 Office 365 的 internet 连接。 有时, 评估会指示与 Office 365 的网络连接受法规或对[Skype for Business Online 媒体质量](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)等场景的性能要求的影响。 这些额外要求可能会导致 internet 连接基础结构、路由优化和专用直接连接的投资。
  
> [!NOTE]
> 需要 Microsoft 授权才能使用适用于 Office 365 的 ExpressRoute。 Microsoft 会检查每个客户请求, 并且仅在客户的规章要求要求直接连接时, 才会授权使用适用于 Office 365 的 ExpressRoute。 如果您有这样的要求, 请提供指向您所解释的法规的文本摘录和 web 链接, 这意味着在从[Office 365 请求的 ExpressRoute For Office 请求](https://aka.ms/O365ERReview)中需要直接连接才能开始 Microsoft 评审。 尝试为 Office 365 创建路由筛选器的未授权订阅将收到一[条错误消息](https://support.microsoft.com/kb/3181709)。
  
规划 Office 365 的网络评估时需要考虑的关键要点:
  
- Office 365 是一种通过公共 internet 运行的安全、可靠、高性能的服务。 我们将继续投资, 以增强服务的这些方面。 所有 Office 365 服务均可通过 internet 连接获得。

- 我们将不断优化 Office 365 的核心方面, 如可用性、全局覆盖和基于 internet 的连接的性能。 例如, 许多 Office 365 服务利用一组扩展的面向 internet 的边缘节点。 此边缘网络为通过 internet 的连接提供最佳的邻近度和性能。

- 在考虑将 Office 365 用于任何包括的服务 (如 Skype for Business Online 语音、视频或会议功能) 时, 客户必须完成端到端网络评估, 并使用我们的 Skype 运营框架满足要求。 这些客户将有几个选项可满足云连接的特定要求, 包括 ExpressRoute。

查看 Microsoft [Office 365 优化网络性能的](https://msdn.microsoft.com/en-us/library/mt450488.aspx)microsoft 个案研究。 如果您正在评估 Office 365, 并且不确定从哪里开始进行网络评估, 或者发现您需要帮助解决的网络设计难题, 请与你的 Microsoft 帐户团队合作。
  
此外, 请阅读[office 365 网络连接原则](https://aka.ms/o365networkingprinciples), 了解用于安全管理 Office 365 流量和获得最佳性能的连接原则。 本文将帮助您了解有关安全优化 Office 365 网络连接的最新指南。
  
以下是可用于返回的简短链接: [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>另请参阅

[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 终结点 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Office 365 网络和性能优化](network-planning-and-performance.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[使用 ExpressRoute for Office 365 路由](routing-with-expressroute.md)
  
[ExpressRoute for Office 365 网络计划](network-planning-with-expressroute.md)
  
[在 ExpressRoute for Office 365 场景中使用 BGP 社区 (预览)](bgp-communities-in-expressroute.md)
  
[Skype for Business Online 中的媒体质量和网络连接性能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)
