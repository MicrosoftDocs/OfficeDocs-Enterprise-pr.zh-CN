---
title: Office 365 URL 和 IP 地址范围
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/06/2020
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
ms.openlocfilehash: 4ca6009acad273f165655f8f9200c0215484aa14
ms.sourcegitcommit: b2767740251b257bb5e66d056731c6c9e7f2677d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2020
ms.locfileid: "46596928"
---
# <a name="office-365-urls-and-ip-address-ranges"></a><span data-ttu-id="3176a-104">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="3176a-104">Office 365 URLs and IP address ranges</span></span>

<span data-ttu-id="3176a-p102">Office 365 需要连接到 Internet。对于使用 Office 365 计划（包括政府社区云 (GCC)）的客户，应该可以访问以下终结点。</span><span class="sxs-lookup"><span data-stu-id="3176a-p102">Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).</span></span>
  
<span data-ttu-id="3176a-107">*Office 365 全球 (+GCC)* | [由世纪互联运营的 Office 365](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 美国政府版 DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 美国政府版 GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span><span class="sxs-lookup"><span data-stu-id="3176a-107">*Office 365 Worldwide (+GCC)* | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span></span>

||||
|:-----|:-----|:-----|
|<span data-ttu-id="3176a-108">**上次更新时间：** 08/06/2020 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [更改日志订阅](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="3176a-108">**Last updated:** 08/06/2020 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span> <br/> |<span data-ttu-id="3176a-109">**下载：** 一个 [JSON 格式](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)列表中的所有必需和可选目标。</span><span class="sxs-lookup"><span data-stu-id="3176a-109">**Download:** all required and optional destinations in one [JSON formatted](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) list.</span></span>  <br/> | <span data-ttu-id="3176a-110">**使用：** 代理 [PAC 文件](managing-office-365-endpoints.md#pacfiles)</span><span class="sxs-lookup"><span data-stu-id="3176a-110">**Use:** our proxy [PAC files](managing-office-365-endpoints.md#pacfiles)</span></span> <br/> |

 <span data-ttu-id="3176a-p103">从[管理 Office 365 终结点](managing-office-365-endpoints.md)开始了解我们使用此数据管理网络连接的建议。终结点数据在每月月初更新，并在生效前 30 天发布新的 IP 地址和 URL。这允许尚未进行自动更新的客户在需要新连接之前完成其过程。如果需要解决支持提升、安全事件或其他即时操作要求，终结点也可以在月内更新。以下页面上显示的数据全部由基于 REST 的 Web 服务生成。如果使用脚本或网络设备访问此数据，应直接转到 [Web 服务](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="3176a-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.</span></span>

<span data-ttu-id="3176a-p104">下面的终结点数据列出了从用户计算机到 Office 365 的连接要求。它不包括从 Microsoft 到客户网络的网络连接（有时称为混合或入站网络连接）。有关详细信息，请参阅“[其他终结点](additional-office365-ip-addresses-and-urls.md)”。</span><span class="sxs-lookup"><span data-stu-id="3176a-p104">Endpoint data below lists requirements for connectivity from a user's machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections. See [Additional endpoints](additional-office365-ip-addresses-and-urls.md) for more information.</span></span>

<span data-ttu-id="3176a-p105">终结点分为四个服务区域。可以独立选择前三个服务区域进行连接。第四个服务区域是一个常见的依赖项（称为 Microsoft 365 Common 和 Office），并且必须始终具有网络连接。</span><span class="sxs-lookup"><span data-stu-id="3176a-p105">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.</span></span>

<span data-ttu-id="3176a-123">显示的数据列是：</span><span class="sxs-lookup"><span data-stu-id="3176a-123">Data columns shown are:</span></span>

- <span data-ttu-id="3176a-p106">**ID**：行的 ID 号，也称为终结点集。此 ID 与终结点集的 Web 服务返回的 ID 相同。</span><span class="sxs-lookup"><span data-stu-id="3176a-p106">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="3176a-p107">**类别**：显示端点集是分类为“优化”、“允许”还是“默认”。若要了解这些类别及其管理指南，可以访问[新 Office 365 端点类别](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#new-office-365-endpoint-categories)。此列还列出了哪些端点集必须有网络连接。对于不需要有网络连接的端点集，我们在此字段中提供了备注，以指明在端点集被阻止时会缺少什么功能。若要排除整个服务区域，则列出的必须有网络连接的端点集不需要连接。</span><span class="sxs-lookup"><span data-stu-id="3176a-p107">**Category**: Shows whether the endpoint set is categorized as "Optimize", "Allow", or "Default". You can read about these categories and guidance for management of them at [New Office 365 endpoint categories](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#new-office-365-endpoint-categories). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="3176a-p108">**ER**：如果使用带有 Office 365 路由前缀的 Azure ExpressRoute 支持终结点集，则为**是**。包含所显示的路由前缀的 BGP 社区与列出的服务区域一致。当 ER 为**否**时，这意味着此终结点集不支持 ExpressRoute。但是，不应假设没有为 ER 为 **否**的终结点集播发路由。</span><span class="sxs-lookup"><span data-stu-id="3176a-p108">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="3176a-p109">**地址**：列出终结点集的 FQDN 或通配符域名以及 IP 地址范围。请注意，IP 地址范围采用 CIDR 格式，并且可能包含指定网络中的许多单独 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3176a-p109">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="3176a-p110">**端口**：列出与地址合并以形成网络终结点的 TCP 或 UDP 端口。你会注意到 IP 地址范围中存在一些重复，其中列出了不同的端口。</span><span class="sxs-lookup"><span data-stu-id="3176a-p110">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
><span data-ttu-id="3176a-139">有关 Yammer IP 地址和 URL 的建议，请参阅[此博客文章](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592)。</span><span class="sxs-lookup"><span data-stu-id="3176a-139">For recommendations on Yammer IP addresses and URLs, see [this blog post](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592).</span></span>
>

## <a name="related-topics"></a><span data-ttu-id="3176a-140">相关主题</span><span class="sxs-lookup"><span data-stu-id="3176a-140">Related Topics</span></span>

[<span data-ttu-id="3176a-141">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="3176a-141">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="3176a-142">排查 Office 365 连接故障</span><span class="sxs-lookup"><span data-stu-id="3176a-142">Troubleshooting Office 365 connectivity</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[<span data-ttu-id="3176a-143">客户端连接</span><span class="sxs-lookup"><span data-stu-id="3176a-143">Client connectivity</span></span>](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[<span data-ttu-id="3176a-144">内容分发网络</span><span class="sxs-lookup"><span data-stu-id="3176a-144">Content delivery networks</span></span>](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[<span data-ttu-id="3176a-145">Microsoft Azure 数据中心 IP 范围</span><span class="sxs-lookup"><span data-stu-id="3176a-145">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="3176a-146">Microsoft 公共 IP 空间</span><span class="sxs-lookup"><span data-stu-id="3176a-146">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
