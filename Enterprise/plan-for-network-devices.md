---
title: 有关连接到 Office 365 服务的网络设备的计划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 摘要：介绍了网络容量的考虑因素、WAN 加速器和用于连接到 Office 365 的负载平衡设备。
ms.openlocfilehash: c384ba043e64ec83eda74b234937efaf72f29815
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223064"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>有关连接到 Office 365 服务的网络设备的计划

 **摘要**：介绍了网络容量的考虑因素、WAN 加速器和用于连接到 Office 365 的负载平衡设备。
  
一些网络硬件可能有支持的并发会话的数目的限制。对于具有超过 2,000 个用户的组织，我们建议它们监视其网络设备，以确保它们是能够处理更多的 Office 365 服务通信。简单网络管理协议 (SNMP) 监控软件可以帮助您执行此操作。

||
|:-----|
| 本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)的一部分。|

在本地传出 Internet 代理设置也会影响到您的客户端应用程序的 Office 365 服务的连接。您还必须配置网络代理设备以允许 Microsoft 云服务 Url 和应用程序的连接。每个组织为不同。若要了解有关 Microsoft 如何管理此过程和带宽量我们设置，[读取案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。
  
业务帮助文章的以下 Skype 具有 Skype 业务设置的详细信息：
  
- [疑难解答 Skype 业务登录错误 （管理员） （英文）](https://go.microsoft.com/fwlink/p/?LinkID=243624)

- [无法连接到业务的 Skype 或某些功能执行操作不起作用，因为本地防火墙阻止连接](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> 尽管其中许多设置业务特定的 Skype，网络配置的一般指南可用于所有 Office 365 服务。
  
## <a name="determining-network-capacity"></a>确定网络容量

连接上存在的每个网络设备都有容量限制。其中包括客户端和服务器网络适配器、路由器、交换机以及将其互连的集线器。足够的网络容量意味着这些网络设备都未饱和。监视网络活动有助于确保所有网络设备上的实际负载小于其最大容量。网络容量影响代理设备性能。
  
在大多数情况下，Internet 连接带宽设置流量量的限制。在高峰时段流量性能不佳可能是由 Internet 链接的过度使用导致的。这种情况下也适用于分支办公室方案，其中分支办公室代理服务器计算机连接到分支的总部的代理设备慢速广域网 (WAN) 链接。
  
若要测试在网络容量，监视在代理服务器网络接口的网络活动。如果它为 75%以上的任何网络接口的最大带宽，请考虑增加的带宽不足的网络基础结构。或者，请考虑使用高级的功能，例如 HTTP 压缩。
  
## <a name="wan-accelerators"></a>WAN 加速器

如果您的组织使用广域网 (wan) 加速代理设备，访问 Office 365 服务时可能遇到的问题。您可能需要优化您的网络设备或设备，以确保您的用户访问 Office 365 时具有一致的体验。例如，Office 365 服务加密某些 Office 365 内容和 TCP 标头。您的设备可能不能处理这种类型的通信。
  
阅读有关[使用 WAN 优化控制器或与 Office 365 的通信/检查设备](https://support.microsoft.com/kb/2690045)我们支持语句。
  
## <a name="hardware-and-software-load-balancing-devices"></a>硬件和软件负载平衡设备

您的组织需要使用硬件负载平衡器 (HLB) 或网络负载平衡 (NLB) 解决方案将请求分发到 Active Directory 联合身份验证服务 (AD FS) 服务器和/或 Exchange 混合服务器。负载平衡设备控制传到内部部署服务器的网络流量。这些服务器有助于确保单一登录和 Exchange 混合部署的可用性。
  
我们提供了 Windows Server 中内置的基于软件的 NLB 解决方案。Office 365 支持此解决方案以实现负载平衡。
  
## <a name="firewalls-and-proxies"></a>防火墙和代理

有关配置防火墙和代理，以连接到 Office 365，读取[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、[网络连接到 Office 365](network-connectivity.md)和[Office 365 终结点常见问题](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)，以详细了解如何设备和电路所选内容的详细信息。
  
## <a name="see-also"></a>另请参阅

[Office 365 服务的部署顾问](deployment-advisors-for-office-365.md)
