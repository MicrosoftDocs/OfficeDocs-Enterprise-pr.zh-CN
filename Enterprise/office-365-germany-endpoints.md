---
title: Office 365 Germany 终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 如果您的组织使用 Office 365 并限制网络中的计算机连接到 Internet，则在下面将找到应包含在出站允许列表中的终结点（Fqdn、端口、Url 以及 IPv4 和 IPv6 地址范围），以确保您的计算机可以成功使用 Office 365。
hideEdit: true
ms.openlocfilehash: 416565d862038362c152505a89d2c51bd48c465e
ms.sourcegitcommit: c1a1b028195342affe0f3367db4e79c42429582a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "45387725"
---
# <a name="office-365-germany-endpoints"></a><span data-ttu-id="b75d3-103">Office 365 Germany 终结点</span><span class="sxs-lookup"><span data-stu-id="b75d3-103">Office 365 Germany endpoints</span></span>

 <span data-ttu-id="b75d3-104">*适用于： Office 365 管理员*</span><span class="sxs-lookup"><span data-stu-id="b75d3-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="b75d3-105">Office 365 要求连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="b75d3-105">Office 365 requires connectivity to the Internet.</span></span> <span data-ttu-id="b75d3-106">下面的终结点应仅供使用**Office 365 德国**计划的客户访问。</span><span class="sxs-lookup"><span data-stu-id="b75d3-106">The endpoints below should be reachable for customers using **Office 365 Germany** plans only.</span></span>
  
 <span data-ttu-id="b75d3-107">**Office 365 终结点：**[全球（包括 GCC）](urls-and-ip-address-ranges.md)  | [由世纪互联运营的 Office 365](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 美国政府版 DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 美国政府版 GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span><span class="sxs-lookup"><span data-stu-id="b75d3-107">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="b75d3-108">**上次更新时间：** 2020/07/09 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [更改日志订阅](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="b75d3-108">**Last updated:** 07/09/2020 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span> |<span data-ttu-id="b75d3-109">**下载：** 一个 [JSON 格式](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)列表中的所有必需和可选目标。</span><span class="sxs-lookup"><span data-stu-id="b75d3-109">**Download:** all required and optional destinations in one [JSON formatted](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) list.</span></span>  <br/> |

<span data-ttu-id="b75d3-110">从[管理 Office 365 终结点](managing-office-365-endpoints.md)开始，了解我们关于使用此数据管理网络连接的建议。</span><span class="sxs-lookup"><span data-stu-id="b75d3-110">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data.</span></span> <span data-ttu-id="b75d3-111">终结点数据在每月开始时更新，并在30天内发布新的 IP 地址和 Url，并在处于活动状态之前发布。</span><span class="sxs-lookup"><span data-stu-id="b75d3-111">Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active.</span></span> <span data-ttu-id="b75d3-112">这样一来，在需要新的连接之前，尚不具有自动更新的客户即可完成其过程。</span><span class="sxs-lookup"><span data-stu-id="b75d3-112">This lets customers who do not yet have automated updates to complete their processes before new connectivity is required.</span></span> <span data-ttu-id="b75d3-113">如果需要，还可以更新终结点，以解决支持升级、安全事件或其他立即运行的要求。</span><span class="sxs-lookup"><span data-stu-id="b75d3-113">Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements.</span></span> <span data-ttu-id="b75d3-114">您始终可以引用[更改日志订阅](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="b75d3-114">You can always refer to the [change log subscription](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="b75d3-115">以下页面上显示的数据都是从基于 REST 的 web 服务生成的。</span><span class="sxs-lookup"><span data-stu-id="b75d3-115">The data shown on this page below is all generated from the REST-based web services.</span></span> <span data-ttu-id="b75d3-116">如果使用脚本或网络设备访问此数据，则应直接转到[Web 服务](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="b75d3-116">If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.</span></span>

<span data-ttu-id="b75d3-p104">下面的终结点数据列出了从用户计算机到 Office 365 的连接要求。它不包括从 Microsoft 到客户网络的网络连接（有时称为混合或入站网络连接）。</span><span class="sxs-lookup"><span data-stu-id="b75d3-p104">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="b75d3-p105">终结点分为四个服务区域。可以独立选择前三个服务区域进行连接。第四个服务区域是一个常见的依赖项（称为 Microsoft 365 Common 和 Office），并且必须始终具有网络连接。</span><span class="sxs-lookup"><span data-stu-id="b75d3-p105">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.</span></span>

<span data-ttu-id="b75d3-122">显示的数据列是：</span><span class="sxs-lookup"><span data-stu-id="b75d3-122">Data columns shown are:</span></span>

- <span data-ttu-id="b75d3-p106">**ID**：行的 ID 号，也称为终结点集。此 ID 与终结点集的 Web 服务返回的 ID 相同。</span><span class="sxs-lookup"><span data-stu-id="b75d3-p106">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="b75d3-p107">**类别**：显示终结点集是分类为“优化”、“允许”还是“默认”。可以在 [https://aka.ms/pnc](https://aka.ms/pnc) 上了解管理它们的这些类别和指南。此列还列出了哪些终结点集需要具有网络连接。对于不需要具有网络连接的终结点集，我们在此字段中提供备注，以指示在终结点集被阻止时将丢失哪些功能。如果要排除整个服务区域，则根据需要列出的终结点集不需要连接。</span><span class="sxs-lookup"><span data-stu-id="b75d3-p107">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="b75d3-p108">**ER**：如果使用带有 Office 365 路由前缀的 Azure ExpressRoute 支持终结点集，则为**是**。包含所显示的路由前缀的 BGP 社区与列出的服务区域一致。当 ER 为**否**时，这意味着此终结点集不支持 ExpressRoute。但是，不应假设没有为 ER 为 **否**的终结点集播发路由。</span><span class="sxs-lookup"><span data-stu-id="b75d3-p108">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="b75d3-p109">**地址**：列出终结点集的 FQDN 或通配符域名以及 IP 地址范围。请注意，IP 地址范围采用 CIDR 格式，并且可能包含指定网络中的许多单独 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b75d3-p109">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="b75d3-p110">**端口**：列出与地址合并以形成网络终结点的 TCP 或 UDP 端口。你会注意到 IP 地址范围中存在一些重复，其中列出了不同的端口。</span><span class="sxs-lookup"><span data-stu-id="b75d3-p110">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

