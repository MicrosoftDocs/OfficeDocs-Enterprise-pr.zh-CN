---
title: Office 365 中的 NAT 支持
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 本文提供了有关如何通过使用 NAT 对组织中的每个 IP 地址使用的客户端数的详细信息。
ms.openlocfilehash: f5914efb8042076e3ae7cad0d5fcb1f7eb97c12a
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606768"
---
# <a name="nat-support-with-office-365"></a>Office 365 中的 NAT 支持

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

以前，建议使用每个 IP 地址连接到 Office 365 的 Exchange 客户端的最大数量大约为每个网络端口2000个客户端。
  
## <a name="why-use-nat"></a>为什么要使用 NAT？

通过使用 NAT，企业网络中的数以千计的人员可以 "共享" 几个可公开路由的 IP 地址。
  
大多数公司网络使用专用 (RFC1918) IP 地址空间。 专用地址空间由 Internet 分配的号码颁发机构 (IANA) 并专门用于不直接路由到全球 Internet 的网络。
  
若要在专用 IP 地址空间上提供对设备的 Internet 访问，组织可以使用网关技术（如防火墙和代理），提供网络地址转换 (NAT) 或端口地址转换 (PAT) services。 这些网关使从内部设备到 Internet 的流量 (包括 Office 365) 似乎来自一个或多个可公开路由的 IP 地址。 来自内部设备的每个出站连接都会转换为公共 IP 地址上的其他源 TCP 端口。 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>为什么您需要将这么多的连接同时打开到 Office 365？

如果存在外接程序、共享日历、邮箱等 ) ，Outlook 可能会打开八个或更多的连接 (的情况。 由于基于 Windows 的 NAT 设备上最多可提供64000个端口，因此在端口耗尽之前，IP 地址最多可以有8000个用户。 请注意，如果客户使用的是基于非 Windows 操作系统的 NAT 设备，则可用端口总数取决于所使用的 NAT 设备或软件。 在这种情况下，最大端口数可能小于64000。 端口的可用性也受其他因素（如 Windows 限制4000端口以供其自己使用）的影响，这会将可用端口的总数减少到60000。 可能存在其他可能同时连接的应用程序（如 Internet Explorer），需要额外的端口。
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>使用 Office 365 计算单个公共 IP 地址后的最大受支持设备数

若要确定单个公共 IP 地址后的最大设备数，应监视网络流量以确定每个客户端的峰值端口使用率。 此外，使用峰值因子应用于端口使用 (最低 4) 。 
  
 **使用以下公式计算每个 IP 地址支持的设备数：**
  
单个公共 IP 地址后的最大受支持设备数 = (64000-受限端口) / (峰值端口消耗 + 峰值因子) 
  
 **例如，如果满足以下条件：**
  
- **受限端口：** 针对操作系统的4000

- **峰值端口消耗：** 每个设备6个

- **峰值因子：** 4

然后，单个公共 IP 地址后的最大受支持设备数 = (64000-4000) / (6 + 4) = 6000
  
在 Microsoft Office Outlook 2007 的9月2011版更新中包含 Office 365 承载包，或 Microsoft Outlook 2010 的11月2011或更高版本的更新中，从 Outlook (Office Outlook 2007 with Service Pack 2 和 Outlook 2010) 到 Exchange 的连接数可以少到2个。 您需要考虑不同的操作系统、用户行为等，以确定您的网络在高峰期所需的最小和最大端口数。
  
如果要支持单个公用 IP 地址后面的更多设备，请按照概述的步骤来评估可支持的最大设备数：
  
监视网络流量以确定每个客户端的峰值端口使用率。 应收集以下数据：
  
- 从多个位置
    
- 从多个设备
    
- 多次
    
使用上述公式可计算在其环境中可支持的每个 IP 地址的最大用户数。
  
有多种方法可以在其他公用 IP 地址之间分发客户端负载。 可用策略取决于企业网关解决方案的功能。 最简单的解决方案是对用户地址空间进行分段，并对每个网关静态 "分配" 多个 IP 地址。 许多网关设备提供的另一种方法是能够使用 IP 地址池。 地址池的优势在于，随着用户群的增长，更有可能在更大的程度上增加和减少需求调整。
  
## <a name="see-also"></a>另请参阅

[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 终结点 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
