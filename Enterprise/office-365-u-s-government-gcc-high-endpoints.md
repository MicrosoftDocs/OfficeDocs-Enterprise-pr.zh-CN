---
title: Office 365 美国政府版（GCC）高终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/16/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: 如果您的组织使用 Office 365 并限制网络中的计算机连接到 Internet，则在下面将找到应包含在出站允许列表中的终结点（Fqdn、端口、Url、IPv4 和 IPv6 地址范围），以确保您的计算机可以成功使用 Office 365。
hideEdit: true
ms.openlocfilehash: 288e7140701b698979fa7e054d367d36fddb887d
ms.sourcegitcommit: f2a4b77c8c3932beb1a78bf2f5bf793fefb3fa49
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/16/2020
ms.locfileid: "44747382"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 美国政府版（GCC）高终结点

 *适用于： Office 365 管理员*

**摘要：** Office 365 要求连接到 Internet。 下面的终结点对于使用 Office 365 美国政府版高计划的客户应是可访问的。
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Office 365 终结点：**[全球（包括 GCC）](urls-and-ip-address-ranges.md) | [由世纪互联运营的 Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)  | [Office 365 美国政府版 DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 美国政府版 GCC High* |
  
|||
|:-----|:-----|
|**上次更新时间：** 06/16/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [更改日志订阅](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**下载：** [JSON 格式](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)的完整列表 <br/> |

 从[管理 Office 365 终结点](managing-office-365-endpoints.md)开始，了解我们关于使用此数据管理网络连接的建议。 终结点数据在每月开始时更新，并在30天内发布新的 IP 地址和 Url，并在处于活动状态之前发布。 这样一来，在需要新的连接之前，尚不具有自动更新的客户即可完成其过程。 如果需要，还可以更新终结点，以解决支持升级、安全事件或其他立即运行的要求。 以下页面上显示的数据都是从基于 REST 的 web 服务生成的。 如果使用脚本或网络设备访问此数据，则应直接转到[Web 服务](office-365-ip-web-service.md)。

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

显示的数据列是：

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**：如果终结点设置通过 Azure ExpressRoute （使用 Office 365 路由前缀）支持，则为 **"是"** 。 包含路由前缀的 BGP 社区与所列的服务区域对齐。 当 ER 为 "**否**" 时，这意味着此终结点集不支持 ExpressRoute。 但是，不应假定在 ER 为**no**时没有为终结点集播发任何路由。 如果您计划使用 Azure AD Connect，请阅读[特殊注意事项部分](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government)，以确保您具有适当的 Azure ad connect 配置。

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

关于此表的注释：

- 安全与合规中心（SCC）提供对适用于 Office 365 的 Azure ExpressRoute 的支持。 这同样适用于通过 SCC 公开的许多功能，如报告、审核、高级电子数据展示、统一 DLP 和数据管理。 两种特定功能（PST 导入和电子数据展示导出）目前不支持仅具有 Office 365 路由筛选器的 Azure ExpressRoute，因为它们依赖于 Azure Blob 存储。 若要使用这些功能，您需要使用任何支持的 Azure 连接选项（包括 Internet 连接或具有 Azure 公用路由筛选器的 Azure ExpressRoute）以独立方式连接到 Azure Blob 存储。 您必须评估这两个功能的建立此类连接。 Office 365 信息保护团队了解此限制，并积极努力为 Office 365 提供对 Azure ExpressRoute 的支持，这些功能仅限于 Office 365 的路由筛选器。

- Microsoft 365 应用程序的其他可选终结点未列出，并且用户无需为企业应用程序启动 Microsoft 365 应用程序和编辑文档。 可选的终结点托管在 Microsoft 数据中心中，不会处理、传输或存储客户数据。 建议将指向这些终结点的用户连接定向到默认 Internet 出局外围。

