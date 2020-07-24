---
title: Office 365 URL 和 IP 地址范围
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 摘要：Office 365 需要连接到 Internet。对于使用 Office 365 计划（包括政府社区云 (GCC)）的客户，应该可以访问以下终结点。
hideEdit: true
ms.openlocfilehash: 1df2420812cd6ba0fbec619a4a280874c3d9fc9b
ms.sourcegitcommit: c1a1b028195342affe0f3367db4e79c42429582a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "45387695"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>Office 365 URL 和 IP 地址范围

Office 365 需要连接到 Internet。对于使用 Office 365 计划（包括政府社区云 (GCC)）的客户，应该可以访问以下终结点。
  
*Office 365 全球 (+GCC)* | [由世纪互联运营的 Office 365](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 美国政府版 DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 美国政府版 GCC High](office-365-u-s-government-gcc-high-endpoints.md) |

||||
|:-----|:-----|:-----|
|**上次更新时间：** 2020/07/09 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [更改日志订阅](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**下载：** 一个 [JSON 格式](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)列表中的所有必需和可选目标。  <br/> | **使用：** 代理 [PAC 文件](managing-office-365-endpoints.md#pacfiles) <br/> |

 从[管理 Office 365 终结点](managing-office-365-endpoints.md)开始了解我们使用此数据管理网络连接的建议。终结点数据在每月月初更新，并在生效前 30 天发布新的 IP 地址和 URL。这允许尚未进行自动更新的客户在需要新连接之前完成其过程。如果需要解决支持提升、安全事件或其他即时操作要求，终结点也可以在月内更新。以下页面上显示的数据全部由基于 REST 的 Web 服务生成。如果使用脚本或网络设备访问此数据，应直接转到 [Web 服务](office-365-ip-web-service.md)。

下面的终结点数据列出了从用户计算机到 Office 365 的连接要求。它不包括从 Microsoft 到客户网络的网络连接（有时称为混合或入站网络连接）。有关详细信息，请参阅“[其他终结点](additional-office365-ip-addresses-and-urls.md)”。

终结点分为四个服务区域。可以独立选择前三个服务区域进行连接。第四个服务区域是一个常见的依赖项（称为 Microsoft 365 Common 和 Office），并且必须始终具有网络连接。

显示的数据列是：

- **ID**：行的 ID 号，也称为终结点集。此 ID 与终结点集的 Web 服务返回的 ID 相同。

- **类别**：显示端点集是分类为“优化”、“允许”还是“默认”。若要了解这些类别及其管理指南，可以访问[新 Office 365 端点类别](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#new-office-365-endpoint-categories)。此列还列出了哪些端点集必须有网络连接。对于不需要有网络连接的端点集，我们在此字段中提供了备注，以指明在端点集被阻止时会缺少什么功能。若要排除整个服务区域，则列出的必须有网络连接的端点集不需要连接。

- **ER**：如果使用带有 Office 365 路由前缀的 Azure ExpressRoute 支持终结点集，则为**是**。包含所显示的路由前缀的 BGP 社区与列出的服务区域一致。当 ER 为**否**时，这意味着此终结点集不支持 ExpressRoute。但是，不应假设没有为 ER 为 **否**的终结点集播发路由。

- **地址**：列出终结点集的 FQDN 或通配符域名以及 IP 地址范围。请注意，IP 地址范围采用 CIDR 格式，并且可能包含指定网络中的许多单独 IP 地址。
 
- **端口**：列出与地址合并以形成网络终结点的 TCP 或 UDP 端口。你会注意到 IP 地址范围中存在一些重复，其中列出了不同的端口。

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
>有关 Yammer IP 地址和 URL 的建议，请参阅[此博客文章](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592)。
>

## <a name="related-topics"></a>相关主题

[管理 Office 365 终结点](managing-office-365-endpoints.md)
  
[排查 Office 365 连接故障](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[客户端连接](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[内容分发网络](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure 数据中心 IP 范围](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公共 IP 空间](https://www.microsoft.com/download/details.aspx?id=53602)
