---
title: Office 365 Germany 终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 如果您的组织使用 Office 365，并限制在您的网络的计算机连接到 Internet，下面将找到的终结点 （Fqdn、 端口、 Url 和 IPv4 和 IPv6 地址范围） 应包含在您出站的允许列表，以确保您计算机可以成功使用 Office 365。
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539526"
---
# <a name="office-365-germany-endpoints"></a><span data-ttu-id="9d25b-103">Office 365 Germany 终结点</span><span class="sxs-lookup"><span data-stu-id="9d25b-103">Office 365 Germany endpoints</span></span>

 <span data-ttu-id="9d25b-104">*应用于： Office 365 管理*</span><span class="sxs-lookup"><span data-stu-id="9d25b-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="9d25b-p101">**摘要：** Office 365 要求连接到 Internet。下面的终结点应该为客户使用**Office 365 德国**计划仅可访问。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p101">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using **Office 365 Germany** plans only.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9d25b-p102">Microsoft 正在开发基于 REST 的 web 服务的 IP 地址和此页上的 FQDN 条目。此新服务将帮助您配置和更新网络外围设备，如防火墙和代理服务器。您可以下载的终结点、 列表或特定更改的当前版本的列表。XML 文档、 RSS 源，和 IP 地址和 FQDN 条目，此页上的，则最终将替换此服务。若要试用此新的服务，请转到[Web 服务](managing-office-365-endpoints.md#webservice)。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document, RSS feed, and the IP address and FQDN entries on this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span> 
  
 <span data-ttu-id="9d25b-112">**Office 365 终结点：**[全球 （包括 GCC）](urls-and-ip-address-ranges.md)  |  [Office 365 由 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 德国* | [Office 365 美国政府 DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 美国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md)  |</span><span class="sxs-lookup"><span data-stu-id="9d25b-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="9d25b-113">**上次更新时间：** 7/2/2018- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [到 Office 365 德国终结点的更改的列表](office-365-germany-endpoints-change-log.md)</span><span class="sxs-lookup"><span data-stu-id="9d25b-113">**Last updated:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [List of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md)</span></span>||

<span data-ttu-id="9d25b-p103">从[管理 Office 365 终结点](managing-office-365-endpoints.md)开始了解我们的建议用于管理网络连接使用该数据。终结点数据更新新的 IP 地址和 Url 发布前处于活动状态的 30 天内每月的开头。这样不尚未具有自动更新完成其流程之前不需要新连接的客户。如果无需对地址支持升级、 安全事件或其他即时操作要求，还可能月份内更新终结点。始终可引用[的更改到 Office 365 德国终结点列表](office-365-germany-endpoints-change-log.md)。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. You can always refer to the [list of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md).</span></span>

<span data-ttu-id="9d25b-p104">所有生成的基于 REST 的 web 服务从下面此页面上显示的数据。如果您使用脚本或网络设备进行访问这些数据，您应直接转到[Web 服务](managing-office-365-endpoints.md#webservice)中。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p104">The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="9d25b-p105">终结点数据下面列出了从用户的计算机连接到 Office 365 的要求。它不包括来自 Microsoft 客户网络、 有时称为的混合或入站的网络连接到的网络连接。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="9d25b-p106">终结点分为四个服务区域。可以为独立连接选择的第三个服务区域。第四个服务区域是常见的相关性 （称为 Microsoft 365 常见和 Office Online），并且必须始终具有网络连接。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="9d25b-126">数据列显示如下：</span><span class="sxs-lookup"><span data-stu-id="9d25b-126">Data columns shown are:</span></span>

- <span data-ttu-id="9d25b-p107">**ID**： 的行，也称为终结点设置的 ID 号。此 ID 是由终结点设置的 web 服务返回的相同。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="9d25b-p108">**类别**： 显示终结点设置是否属于"优化"、"允许"或"Default"。您可以了解有关这些类别和指南管理它们在[http://aka.ms/pnc](http://aka.ms/pnc)。此列还列出了哪些终结点组所需具有网络连接。对于其不需要有网络连接的终结点集，我们提供此字段，以指示哪项功能将会丢失，如果阻止终结点设置中的注释。如果您不包括整个服务区域，列出所需的终结点集不需要连接。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="9d25b-p109">**紧急**： 这是**** 如果终结点设置通过 Azure ExpressRoute 支持 Office 365 路由前缀。BGP 社区包含所示的路由前缀与服务区域列出对齐。时紧急为**否**，这意味着，ExpressRoute 不支持此终结点设置。但是，它不应假定不路由将公布为终结点集其中紧急为**否**。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="9d25b-p110">**地址**： 列出的 Fqdn 或通配符域名和终结点设置的 IP 地址范围。请注意，IP 地址范围是 CIDR 格式可能包含指定的网络中的许多单个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="9d25b-p111">**端口**： 列出了结合地址以形成网络终结点的 TCP 或 UDP 端口。您可能会注意到 IP 地址范围中的有些重复在没有列出不同的端口。</span><span class="sxs-lookup"><span data-stu-id="9d25b-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

