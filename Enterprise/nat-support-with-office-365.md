---
title: Office 365 中的 NAT 支持
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 摘要：提供了有关如何使用网络地址转换 (NAT)，估算对组织内每个 IP 地址可以使用的客户端正确数量的详细信息。
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539516"
---
# <a name="nat-support-with-office-365"></a>Office 365 中的 NAT 支持

 **摘要：** 提供了有关如何使用网络地址转换 (NAT)，估算对组织内每个 IP 地址可以使用的客户端正确数量的详细信息。 
  
以前，指南建议您应使用每个 IP 地址连接到 Office 365 的 Exchange 客户端的最大数量的每个网络端口大约 2,000 个客户端。
  
## <a name="why-use-nat"></a>为什么要使用 NAT？

通过使用 NAT，成千上万的人就企业网络可以"共享"一些公开可路由的 IP 地址。
  
大多数公司网络使用专用 (RFC1918) IP 地址空间。专用地址空间由 Internet 号码分配机构 (IANA) 分配，仅用于不与全局 Internet 直接路由的网络。
  
若要在专用的 IP 地址空间提供 Internet 访问设备，组织使用网关技术，如防火墙和提供网络地址转换 (NAT) 或端口地址转换 (PAT) 服务的代理。这些网关进行从内部的通信设备 （包括 Office 365） Internet 显示来自一个或多个公共可路由的 IP 地址。内部设备从每个出站连接将转换到公共 IP 地址上的不同源 TCP 端口。 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>为什么需要有很多连接到 Office 365 同时打开？

Outlook 会打开 8 个或更多连接（有外接程序、共享日历、邮箱等的情况）。由于基于 Windows 的 NAT 设备上最多提供 64,000 个端口，因此在端口耗尽之前，一个 IP 地址后面最多可有 8,000 个用户。请注意，如果客户将非基于 Windows 操作系统的设备用于 NAT，则可用端口总数依赖于使用的 NAT 设备或软件。在这种情况下，最大端口数可能小于 64,000。端口可用性还受其他因素影响，例如 Windows 限制 4,000 个端口供其自用，于是可用端口总数减少到 60,000。还有其他同时连接的应用程序（例如 Internet Explorer）需要额外的端口。
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>计算最多支持的设备与 Office 365 单一公共 IP 地址

若要确定的单个公用 IP 地址的设备的最大数量，您应监视网络流量，以确定每个客户端的峰值端口消耗。此外，峰值因子应使用的端口使用情况 (最小 4)。 
  
 **使用以下公式计算每个 IP 地址的受支持设备数：**
  
最多支持单个公用 IP 地址的设备数 = (64,000-受限制的端口) / （峰值端口使用 + 峰值因子）
  
 **例如，下面是，则返回 true:**
  
- **受限制的端口：** 4000 用于操作系统 
    
- 每个设备的**峰值端口消耗：** 6 
    
- **峰值因子：** 4 
    
然后，支持单个公用 IP 地址的设备的最大 = (64,000 4000) / （6 + 4） = 6,000
  
Office 365 承载包，从 Microsoft Office Outlook 2007，2011 年 9 月或 Microsoft Outlook 2010 的 2011 年 11 月更新或更高版本的更新，从 Outlook (这两个 Office Outlook 2007 与服务的连接数中包含的发行版Pack 2 和 Outlook 2010 中) 到 Exchange 可以少至 2。您需要的不同操作系统用户行为，等等来确定最小和最大网络将需要在高峰期的端口数。
  
如果您想要支持单个公用 IP 地址后面的多个设备，请按照列出评估的可支持的设备的最大数量的步骤操作：
  
监控网络流量，以确定每个客户端的峰值端口消耗。您应收集此数据：
  
- 从多个位置
    
- 从多个设备
    
- 多次
    
使用上述公式计算用户环境中可支持的每个 IP 地址的最大用户数。
  
有用于将客户端负载分散其他公共 IP 地址的各种方法。可用的策略取决于企业的网关解决方案的功能。最简单的解决方案是分隔您用户的地址空间和静态"分配"IP 地址数为每个网关。多个网关设备提供的另一种选择是使用池的 IP 地址的功能。地址池的好处是它不更加动态而且不太可能需要调整，随着用户群。
  
## <a name="see-also"></a>另请参阅

[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 终结点常见问题](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

