---
title: Office 365 美国政府版（GCC）高终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/28/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: 如果您的组织使用 Office 365 并限制网络中的计算机连接到 Internet，则在下面将找到应包含在出站允许列表中的终结点（Fqdn、端口、Url、IPv4 和 IPv6 地址范围），以确保您的计算机可以成功使用 Office 365。
hideEdit: true
ms.openlocfilehash: f96aca7a7b4655df655228771d6319deb46408f9
ms.sourcegitcommit: b4514cd852093181dd4c27009a78aca3ca50d2e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2019
ms.locfileid: "38038271"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 美国政府版（GCC）高终结点

 *适用于： Office 365 管理员*

**摘要：** Office 365 要求连接到 Internet。 下面的终结点对于使用 Office 365 美国政府版高计划的客户应是可访问的。
  
> [!NOTE]
> Microsoft 针对此页上的 IP 地址和 FQDN 条目发布了基于 REST 的 Web 服务。这项新服务有助于配置和更新网络外围设备，如防火墙和代理服务器。可以下载终结点列表，无论是列表的当前版本，还是应用了特定更改的列表。这项服务会替换从此页面链接到的 XML 文档（已于 2018 年 10 月 2 日遭弃用）。若要试用这项新服务，请转到 [Web 服务](office-365-ip-web-service.md)。
  
 **Office 365 终结点：**[全球（包括 GCC）](urls-and-ip-address-ranges.md) | [由世纪互联运营的 Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)  | [Office 365 美国政府版 DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 美国政府版 GCC High* |
  
|||
|:-----|:-----|
|**上次更新时间：** 2019/10/28 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [更改日志订阅](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**下载：** [JSON 格式](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)的完整列表 <br/> |
   
 从[管理 Office 365 终结点](managing-office-365-endpoints.md)开始，了解我们关于使用此数据管理网络连接的建议。 终结点数据在每月开始时更新，并在30天内发布新的 IP 地址和 Url，并在处于活动状态之前发布。 这样一来，在需要新的连接之前，尚不具有自动更新的客户即可完成其过程。 如果需要，还可以更新终结点，以解决支持升级、安全事件或其他立即运行的要求。 以下页面上显示的数据都是从基于 REST 的 web 服务生成的。 如果使用脚本或网络设备访问此数据，则应直接转到[Web 服务](office-365-ip-web-service.md)。

下面的终结点数据列出了从用户计算机到 Office 365 的连接要求。它不包括从 Microsoft 到客户网络的网络连接（有时称为混合或入站网络连接）。

终结点分为四个服务区域。可以独立选择前三个服务区域进行连接。第四个服务区域是一个常见的依赖项（称为 Microsoft 365 Common 和 Office），并且必须始终具有网络连接。

显示的数据列是：

- **ID**：行的 ID 号，也称为终结点集。此 ID 与终结点集的 Web 服务返回的 ID 相同。

- **类别**：显示终结点集是分类为“优化”、“允许”还是“默认”。可以在 [https://aka.ms/pnc](https://aka.ms/pnc) 上了解管理它们的这些类别和指南。此列还列出了哪些终结点集需要具有网络连接。对于不需要具有网络连接的终结点集，我们在此字段中提供备注，以指示在终结点集被阻止时将丢失哪些功能。如果要排除整个服务区域，则根据需要列出的终结点集不需要连接。

- **ER**：如果终结点设置通过 Azure ExpressRoute （使用 Office 365 路由前缀）支持，则为 **"是"** 。 包含路由前缀的 BGP 社区与所列的服务区域对齐。 当 ER 为 "**否**" 时，这意味着此终结点集不支持 ExpressRoute。 但是，不应假定在 ER 为**no**时没有为终结点集播发任何路由。 如果您计划使用 Azure AD Connect，请阅读[特殊注意事项部分](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government)，以确保您具有适当的 Azure ad connect 配置。

- **地址**：列出终结点集的 FQDN 或通配符域名以及 IP 地址范围。请注意，IP 地址范围采用 CIDR 格式，并且可能包含指定网络中的许多单独 IP 地址。
 
- **端口**：列出与地址合并以形成网络终结点的 TCP 或 UDP 端口。你会注意到 IP 地址范围中存在一些重复，其中列出了不同的端口。
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

关于此表的注释：

- 安全与合规中心（SCC）提供对适用于 Office 365 的 Azure ExpressRoute 的支持。 这同样适用于通过 SCC 公开的许多功能，如报告、审核、高级电子数据展示、统一 DLP 和数据管理。 两种特定功能（PST 导入和电子数据展示导出）目前不支持仅具有 Office 365 路由筛选器的 Azure ExpressRoute，因为它们依赖于 Azure Blob 存储。 若要使用这些功能，您需要使用任何支持的 Azure 连接选项（包括 Internet 连接或具有 Azure 公用路由筛选器的 Azure ExpressRoute）以独立方式连接到 Azure Blob 存储。 您必须评估这两个功能的建立此类连接。 Office 365 信息保护团队了解此限制，并积极努力为 Office 365 提供对 Azure ExpressRoute 的支持，这些功能仅限于 Office 365 的路由筛选器。

- Office 365 专业增强版有其他可选终结点，这些终结点未列出，用户无需启动 Office 365 专业增强版应用程序和编辑文档。 可选的终结点托管在 Microsoft 数据中心中，不会处理、传输或存储客户数据。 建议将指向这些终结点的用户连接定向到默认 Internet 出局外围。

