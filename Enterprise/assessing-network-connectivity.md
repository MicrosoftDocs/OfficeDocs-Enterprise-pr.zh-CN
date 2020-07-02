---
title: 评估 Microsoft 365 网络连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Microsoft 365 旨在让世界各地的客户能够使用 internet 连接连接到服务。 随着服务的演变，Microsoft 365 的安全性、性能和可靠性将根据使用 internet 的客户建立与服务的连接而得到改进。
ms.openlocfilehash: 0ccf729dc8eddfd99ffc0b70c8ab56e31451be88
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997956"
---
# <a name="assessing-microsoft-365-network-connectivity"></a>评估 Microsoft 365 网络连接

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

Microsoft 365 旨在让世界各地的客户能够使用 internet 连接连接到服务。 随着服务的演变，Microsoft 365 的安全性、性能和可靠性将根据使用 internet 的客户建立与服务的连接而得到改进。
  
计划使用 Microsoft 365 的客户应评估其现有和预测的 internet 连接需要作为部署项目的一部分。 对于企业级部署，可靠性和适当调整的 internet 连接性是使用 Microsoft 365 功能和方案的关键部分。
  
根据您的大小和偏好，许多不同的人员和组织可以执行网络评估。 评估的网络范围也可能因您在部署过程中所处的位置而异。 为了帮助您更好地了解执行网络评估所需的内容，我们生成了一个网络评估指南，帮助您了解可用的选项。 此评估将确定在部署项目中需要添加哪些步骤和资源，以使您能够成功采用 Microsoft 365。
  
全面的网络评估将提供可能的解决方案，以实现网络设计难题以及实现详细信息。 一些网络评估将显示，与 Microsoft 365 的最佳网络连接可适应现有网络和 internet 出口基础结构的次要配置或设计更改。

某些评估将指示到 Microsoft 365 的网络连接需要在网络组件中进行额外的投资。 例如，跨分支机构和多个地理区域的企业网络可能需要在 SD WAN 解决方案或优化的路由基础结构中进行投资，以支持到 Microsoft 365 的 internet 连接。 有时，评估会指示与 Microsoft 365 的网络连接受法规或性能要求对诸如[Skype for Business Online media 质量](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)等方案的影响。 这些额外要求可能会导致 internet 连接基础结构、路由优化和专用直接连接的投资。

帮助您评估网络的一些资源：

- 有关 Microsoft 365 网络的概念性信息，请参阅[Microsoft 365 网络连接概述](office-365-networking-overview.md)。
- 请参阅[Microsoft 365 网络连接原则](https://aka.ms/o365networkingprinciples)，了解用于安全管理 Microsoft 365 流量和获得最佳性能的连接原则。
- 注册[Microsoft FastTrack](https://www.microsoft.com/fasttrack)以获取 microsoft 365 规划、设计和部署的引导式协助。 
- 请参阅下面的[Microsoft 365 连接测试](assessing-network-connectivity.md#the-microsoft-365-connectivity-test)部分，运行基本的连接测试，这些测试提供有关可在给定用户位置和 Microsoft 365 之间进行的网络连接改进的具体指导。

> [!NOTE]
> 需要 Microsoft 授权才能使用适用于 Office 365 的 ExpressRoute。 Microsoft 会检查每个客户请求，并且仅在客户的规章要求要求直接连接时，才会授权使用适用于 Office 365 的 ExpressRoute。 如果您有这样的要求，请提供指向您所解释的法规的文本摘录和 web 链接，这意味着在从[Office 365 请求的 ExpressRoute For Office 请求](https://aka.ms/O365ERReview)中需要直接连接才能开始 Microsoft 评审。 尝试为 Office 365 创建路由筛选器的未授权订阅将收到一[条错误消息](https://support.microsoft.com/kb/3181709)。
  
规划 Microsoft 365 的网络评估时需要考虑的关键要点：
  
- Microsoft 365 是通过公共 internet 运行的安全、可靠、高性能的服务。 我们将继续投资，以增强服务的这些方面。 所有 Microsoft 365 服务均可通过 internet 连接获得。

- 我们正在不断优化 Microsoft 365 的核心方面，例如，基于 internet 的连接的可用性、全局覆盖和性能。 例如，许多 Microsoft 365 服务利用一组扩展的面向 internet 的边缘节点。 此边缘网络为通过 internet 的连接提供最佳的邻近度和性能。

- 在考虑将 Microsoft 365 用于任何包括的服务（如团队或 Skype for Business Online 语音、视频或会议功能）时，客户应完成端到端网络评估，并满足使用[Microsoft FastTrack](https://www.microsoft.com/fasttrack)的连接要求。

如果你正在评估 Microsoft 365，并且不确定从哪里开始进行网络评估，或者发现需要帮助解决的网络设计难题，请与你的 Microsoft 帐户团队合作。

## <a name="the-microsoft-365-connectivity-test"></a>Microsoft 365 连接测试

[Microsoft 365 连接测试](https://aka.ms/netonboard)是一种概念证明（POC）网络评估工具，可对你的 microsoft 365 租户运行基本的连接测试，并为最佳 Microsoft 365 性能提供特定的网络设计建议。 该工具突出显示了常见的大型企业网络外围设计选项，这些选项对 Internet web 浏览很有用，但会影响 Microsoft 365 等大型 SaaS 应用程序的性能。

网络载入工具执行以下操作：

- 检测您的位置，也可以指定要测试的位置
- 检查网络出口的位置
- 测试最近的 Microsoft 365 服务前盖的网络路径
- 使用可下载的 Windows 10 应用程序提供高级测试，这些应用程序将提供与代理服务器、防火墙和 DNS 相关的外围网络设计建议。 该工具还运行 Skype for business Online、Microsoft 团队、SharePoint Online 和 Exchange Online 的性能测试。

该工具包含两个组件：一个用于收集基本连接信息的基于浏览器的 UI，以及一个可运行高级测试并返回其他评估数据的可下载的 Windows 10 应用程序。

基于浏览器的工具显示以下信息：

- "结果和影响" 选项卡
  - 正在使用的服务前盖地图上的位置
  - 其他服务前盖地图上的位置，可提供最佳连接能力
  - 与附近的其他 Microsoft 365 客户相比的相对性能
- 详细信息和解决方案选项卡
  - 按城市和国家/地区的用户位置
  - 按城市、州和国家/地区的网络出口位置
  - 用户进入网络传出距离
  - Microsoft 365 Exchange Online 服务前盖位置
  - 适用于用户位置的最佳 Microsoft 365 Exchange Online 服务前端门（s）
  - 使用更好的性能的大都市区域内的客户

高级测试下载应用程序提供以下附加信息：

- "详细信息和解决方案" 选项卡（追加）
  - 用户的默认网关
  - 客户端 DNS 服务器
  - 客户端 DNS 递归解析器
  - Exchange Online DNS 服务器
  - SharePoint Online DNS 服务器
  - 代理服务器标识
  - 媒体连接检查
  - 媒体质量数据包丢失
  - 媒体质量延迟
  - 媒体质量抖动
  - 媒体质量数据包重新排序
- 对多个特定于功能的终结点的连接性测试
- 包含适用于 Exchange Online、SharePoint Online 和团队服务的 tracert 和延迟数据的网络路径诊断

您可以阅读 Microsoft 365 连接测试，并在[更新的 microsoft 365 连接测试 POC 中提供有关新的网络设计建议](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130)博客文章的反馈。 有关此工具的未来更新和其他 Microsoft 365 网络更新的信息将发布到[Office 365 网络](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)博客。
  
以下是可用于返回的简短链接： [ https://aka.ms/o365networkconnectivity 。](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>另请参阅

[Microsoft 365 网络连接概述](office-365-networking-overview.md)

[Microsoft 365 网络连接原则](https://aka.ms/o365networkingprinciples)

[管理 Office 365 终结点](managing-office-365-endpoints.md)

[Office 365 URL 和 IP 地址范围](urls-and-ip-address-ranges.md)

[Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)

[Microsoft 365 网络和性能优化](network-planning-and-performance.md)

[Microsoft 365 企业版概述](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
