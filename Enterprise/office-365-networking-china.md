---
title: 适用于中国用户的 Microsoft 365 全局租户性能优化
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
search.appverid: MET150
f1.keywords:
- NOCSH
description: 本文提供了针对全球 Microsoft 365 租户的中国用户优化网络性能的指南。
ms.openlocfilehash: e5d74bdae23545c1e7c65fae44010a8c5a3829e3
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997802"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>适用于中国用户的 Microsoft 365 全局租户性能优化

>[!IMPORTANT]
>本指南特定于在**中国中的企业 Microsoft 365 用户**连接到**全局 microsoft 365 租户**的使用方案。 本**指南不适用于**由世纪互联运营的 Office 365 中的租户。

对于具有全球 Microsoft 365 租户和中国中的公司状态的企业，基于中国的用户的 Microsoft 365 客户端性能可能会因与中国电讯 Internet 体系结构独有的因素而变得复杂。

中国 Isp 已对全球公共 Internet 的受管制近海连接，该连接可通过易于访问的外围设备的网络拥塞的高级别。 此拥塞为进出中国的所有 Internet 流量创建数据包丢失和延迟。

![Microsoft 365 流量-未优化](media/O365-networking/China-O365-unoptimized.png)

数据包丢失和延迟对网络服务的性能造成不利影响，尤其是需要大型数据交换的服务（如大型文件传输）或需要近似的实时性能（音频和视频应用程序）。

本主题的目标是提供缓解 Microsoft 365 服务上的中国交叉边框网络拥塞影响的最佳做法。 本主题不解决其他常见的最后一个性能问题，例如，由于在中国运营商的复杂路由而导致的高数据包延迟的问题。

## <a name="corporate-network-best-practices"></a>公司网络最佳实践

许多具有全球 Microsoft 365 租户和中国用户的企业已实施专用网络，以在中国办公室位置和世界各地的近海位置之间执行公司网络通信。 这些企业可以利用此网络基础结构来避免跨边框网络拥塞，并在中国优化其 Microsoft 365 服务性能。

>[!IMPORTANT]
>与所有专用 WAN 实现一样，您应始终咨询您的国家和/或地区的法规要求，以确保您的网络配置符合合规性要求。

第一步，在[Microsoft 365 的网络规划和性能优化](https://aka.ms/tune)中遵循我们的基准网络指导，这一点至关重要。 如果可能，主要目标应是避免从中国 Internet 访问全球 Microsoft 365 服务。

- 利用现有的专用网络在中国的公共 Internet 上的中国办公室网络和近海位置之间传送 Microsoft 365 网络通信。 在中国之外的任何位置几乎都可以提供明显的好处。 网络管理员可以通过与[Microsoft 全局网络](https://docs.microsoft.com/azure/networking/microsoft-global-network)的低延迟互连的区域中的附近进一步进行优化。 中国香港、日本和韩国是示例。
- 通过 VPN 连接配置用户设备以访问企业网络，以允许 Microsoft 365 流量传输企业网络的专用近海链接。 确保 VPN 客户端未配置为使用拆分隧道，或者用户设备配置为忽略 Microsoft 365 流量的拆分隧道。
- 将您的网络配置为在您的专用近海链接中路由所有 Microsoft 365 流量。 如果您必须最大限度地减少专用链路上的流量，则可以选择仅在 "**优化**" 类别中路由终结点，并允许请求**允许**和**默认**终结点传输 Internet。 这样可以将经过优化的流量限制为对高延迟和数据包丢失最敏感的关键服务，从而提高性能并最大限度地减少带宽消耗。
- 如果可能，请将 UDP （而不是 TCP）用于实时媒体流流量，例如针对团队的。 UDP 提供了比 TCP 更好的实时媒体流性能。

有关如何有选择地路由 Microsoft 365 流量的信息，请参阅[管理 Office 365 终结点](managing-office-365-endpoints.md)。 有关所有全球 Office 365 Url 和 IP 地址的列表，请参阅[Office 365 url 和 ip 地址范围](urls-and-ip-address-ranges.md)。

![Microsoft 365 流量优化](media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>用户最佳实践

在与企业网络无连接的情况下，在中华人民共和国中连接到全球 Microsoft 365 租户（如住宅、咖啡店、旅馆和分支机构）的用户可能会遇到较差的网络性能，因为其设备和 Microsoft 365 之间的通信必须传输中国拥塞的交叉边界网络电路。

如果不能选择对公司网络中的交叉边框专用网络和/或 VPN 进行访问，则可以通过培训基于中国的用户来遵循这些最佳做法，从而缓解每用户性能问题。

- 利用支持缓存的丰富 Office 客户端（例如，Outlook、团队、OneDrive 等），并避免基于 web 的客户端。 Office 客户端缓存和脱机访问功能可以显著降低网络拥塞和延迟的影响。
- 如果你的 Microsoft 365 租户已配置_音频会议_功能，则团队用户可以通过公用电话交换网（PSTN）加入会议。 有关详细信息，请参阅[Office 365 中的音频会议](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365)。
- 如果用户遇到网络性能问题，他们应向 IT 部门报告故障排除问题，并在怀疑 Microsoft 365 服务出现问题时升级到 Microsoft 支持部门。 并非所有问题都是由交叉边界的网络性能引起的。

Microsoft 不断努力改进 Microsoft 365 用户体验，并通过网络体系结构和特征的最广泛的可能范围来提高客户端的性能。 访问[Office 365 技术社区](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General)以启动或加入对话、查找资源并提交功能请求和建议。

## <a name="related-topics"></a>相关主题

[Microsoft 365 网络计划和性能优化](https://aka.ms/tune)

[Microsoft 365 网络连接原则](office-365-network-connectivity-principles.md)

[管理 Office 365 终结点](managing-office-365-endpoints.md)

[Office 365 URL 和 IP 地址范围](urls-and-ip-address-ranges.md)

[Microsoft 全局网络](https://docs.microsoft.com/azure/networking/microsoft-global-network)
