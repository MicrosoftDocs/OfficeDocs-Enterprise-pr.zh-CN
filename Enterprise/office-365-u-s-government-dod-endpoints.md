---
title: Office 365 美国政府 DoD 终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
description: 摘要： Office 365 要求连接到 Internet。下面的终结点应该为客户使用 Office 365 美国政府 DoD 计划仅可访问。
hideEdit: true
ms.openlocfilehash: 3faca62176b1467829f0333b76a57ce0d5124a96
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539548"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 美国政府 DoD 终结点

*应用于： Office 365 管理*

 **摘要：** Office 365 要求连接到 Internet。下面的终结点应该为客户使用 Office 365 美国政府 DoD 计划仅可访问。
  
> [!NOTE]
> Microsoft 正在开发基于 REST 的 web 服务的 IP 地址和此页上的 FQDN 条目。此新服务将帮助您配置和更新网络外围设备，如防火墙和代理服务器。您可以下载的终结点、 列表或特定更改的当前版本的列表。XML 文档、 RSS 源，和 IP 地址和 FQDN 条目，此页上的，则最终将替换此服务。若要试用此新的服务，请转到[Web 服务](managing-office-365-endpoints.md#webservice)。
  
 **Office 365 终结点：**[全球 （包括 GCC）](urls-and-ip-address-ranges.md) |  [Office 365 由 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 德国](office-365-germany-endpoints.md) | *Office 365 美国政府 DoD* | [Office 365 美国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**上次更新时间：** 8/1/2018- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [更改日志订阅](https://aka.ms/dodendpointrss) <br/> |**下载：** 以[XML 格式](https://aka.ms/usdodendpoints)的完整列表 <br/> |
   
 从[管理 Office 365 终结点](managing-office-365-endpoints.md)开始了解我们的建议用于管理网络连接使用该数据。终结点数据更新新的 IP 地址和 Url 发布前处于活动状态的 30 天内每月的开头。这样不尚未具有自动更新完成其流程之前不需要新连接的客户。如果无需对地址支持升级、 安全事件或其他即时操作要求，还可能月份内更新终结点。所有生成的基于 REST 的 web 服务从下面此页面上显示的数据。如果您使用脚本或网络设备进行访问这些数据，您应直接转到[Web 服务](managing-office-365-endpoints.md#webservice)中。

终结点数据下面列出了从用户的计算机连接到 Office 365 的要求。它不包括来自 Microsoft 客户网络、 有时称为的混合或入站的网络连接到的网络连接。

终结点分为四个服务区域。可以为独立连接选择的第三个服务区域。第四个服务区域是常见的相关性 （称为 Microsoft 365 常见和 Office Online），并且必须始终具有网络连接。

数据列显示如下：

- **ID**： 的行，也称为终结点设置的 ID 号。此 ID 是由终结点设置的 web 服务返回的相同。

- **类别**： 显示终结点设置是否属于"优化"、"允许"或"Default"。您可以了解有关这些类别和指南管理它们在[http://aka.ms/pnc](http://aka.ms/pnc)。此列还列出了哪些终结点组所需具有网络连接。对于其不需要有网络连接的终结点集，我们提供此字段，以指示哪项功能将会丢失，如果阻止终结点设置中的注释。如果您不包括整个服务区域，列出所需的终结点集不需要连接。

- **紧急**： 这是**** 如果终结点设置通过 Azure ExpressRoute 支持 Office 365 路由前缀。BGP 社区包含所示的路由前缀与服务区域列出对齐。时紧急为**否**，这意味着，ExpressRoute 不支持此终结点设置。但是，它不应假定不路由将公布为终结点集其中紧急为**否**。如果您计划使用 Azure AD 连接，读取要确保您具有适当的[特殊注意事项部分](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud)Azure AD 连接配置。

- **地址**： 列出的 Fqdn 或通配符域名和终结点设置的 IP 地址范围。请注意，IP 地址范围是 CIDR 格式可能包含指定的网络中的许多单个 IP 地址。
 
- **端口**： 列出了结合地址以形成网络终结点的 TCP 或 UDP 端口。您可能会注意到 IP 地址范围中的有些重复在没有列出不同的端口。
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
关于此表的注释：

- 安全性和合规性中心 (SCC) 提供的 Azure ExpressRoute for Office 365 的支持。这同样适用的许多功能，如报告、 审核、 高级电子数据展示、 统一 DLP 和数据管理 SCC 通过公开。两个特定功能，PST 导入和电子数据展示导出，当前不支持 Azure ExpressRoute 与仅 Office 365 路由筛选器由于其依赖 Azure Blob 存储。若要使用这些功能，您需要单独连接到使用任何支持的 Azure 连接选项，其中包括与 Azure 公共路由筛选器的 Internet 连接或 Azure ExpressRoute Azure Blob 存储。您需要评估建立这种连接这两个这些功能。Office 365 信息保护团队了解此限制和主动使用支持的 Azure ExpressRoute for Office 365 作为有限置于的这些功能的 Office 365 路由筛选器。

- 有其他可选的终结点的 Office 365 ProPlus 未列出，并且不需要对用户启动 Office 365 ProPlus 应用程序和编辑文档。可选的终结点承载在 Microsoft 数据中心和不要处理、 传输，或存储客户数据。建议的用户连接到这些终结点被定向到默认 Internet 出口外围。
