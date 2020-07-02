---
title: 有关连接到 Office 365 服务的网络设备的计划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 摘要：介绍用于连接到 Office 365 的网络容量、WAN 加速器和负载平衡设备的注意事项。
ms.openlocfilehash: 5015a146f92a32bd0200088517b6673ae00f8f64
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998631"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>有关连接到 Office 365 服务的网络设备的计划

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*
  
一些网络硬件可能对受支持的并发会话数量有限制。 对于拥有多于2000个用户的组织，我们建议他们监视其网络设备，以确保他们能够处理额外的 Office 365 服务流量。 简单网络管理协议（SNMP）监控软件可帮助您执行此操作。

||
|:-----|
| 本文是[Office 365 的网络规划和性能调整](https://aka.ms/tune)的一部分。|

内部部署传出 Internet 代理设置还会影响到适用于客户端应用程序的 Office 365 服务的连接。 您还必须将网络代理设备配置为允许与 Microsoft 云服务 Url 和应用程序建立连接。 每个组织都不同。 若要了解 Microsoft 如何管理此过程以及我们预配的带宽量，请[阅读案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。
  
以下 Skype for Business 帮助文章包含有关 Skype for Business 设置的详细信息：
  
- [对适用于管理员的 Skype for business Online 登录错误进行故障排除](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [无法连接到 Skype for business，或某些功能不起作用，因为本地防火墙阻止了连接](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> 虽然这些设置中的许多都是 Skype for Business，但有关网络配置的一般指导对所有 Office 365 服务都很有用。
  
## <a name="determining-network-capacity"></a>确定网络容量

连接上存在的每个网络设备都具有其容量限制。 这些设备包括客户端和服务器网络适配器、路由器、交换机和与之互连的集线器。 足够的网络容量意味着它们都没有饱和。 监视网络活动是有助于确保所有网络设备上的实际负载小于其最大容量的关键。 网络容量影响代理设备性能。
  
在大多数情况下，Internet 连接带宽设置流量限制。 高峰时段的性能较低可能是由于 Internet 链接使用过多而导致的。 这种情况也适用于分支机构应用场景，其中分支机构代理服务器计算机通过低速广域网（WAN）链接连接到分支总部的代理设备。
  
若要测试网络容量，请在代理网络接口上监视网络活动。 如果它的网络接口的最大带宽超过75%，请考虑增加不充分的网络基础结构的带宽。 或者，考虑使用高级功能，例如 HTTP 压缩。
  
## <a name="wan-accelerators"></a>WAN 加速器

如果您的组织使用广域网络（WAN）加速代理设备，则在访问 Office 365 服务时可能会遇到问题。 你可能需要优化你的网络设备或设备，以确保你的用户在访问 Office 365 时具有一致的体验。 例如，Office 365 服务对某些 Office 365 内容和 TCP 标头进行加密。 你的设备可能无法处理此类流量。
  
阅读我们关于将[WAN 优化控制器或流量/检查设备与 Office 365 结合使用的](https://support.microsoft.com/kb/2690045)支持声明。
  
## <a name="hardware-and-software-load-balancing-devices"></a>硬件和软件负载平衡设备

您的组织需要使用硬件负载平衡器（HLB）或网络负载平衡（NLB）解决方案将请求分发到 Active Directory 联合身份验证服务（AD FS）服务器和/或 Exchange 混合服务器。 负载平衡设备控制到内部部署服务器的网络通信。 在帮助确保单一登录和 Exchange 混合部署的可用性方面，这些服务器至关重要。
  
我们提供了一个内置在 Windows Server 中的基于软件的 NLB 解决方案。 Office 365 支持此解决方案以实现负载平衡。
  
## <a name="firewalls-and-proxies"></a>防火墙和代理

有关配置防火墙和代理以连接到 Office 365 的更多详细信息，请阅读[管理 office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、[评估 office 365 网络连接](assessing-network-connectivity.md)和[office 365 终结点常见问题解答](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)以了解有关设备和电路选择的详细信息。
  
## <a name="see-also"></a>另请参阅

[Office 365 服务的安装指南](setup-guides-for-office-365.md)

[Microsoft 365 企业版概述](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
