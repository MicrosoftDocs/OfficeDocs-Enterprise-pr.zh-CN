---
title: 为 Microsoft 365 设置你的网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 摘要：请参阅以下文章以了解适用于 Microsoft 365 的网络。
ms.openlocfilehash: b1497c214777e34ce4a85701ce6596f50e59910d
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592146"
---
# <a name="set-up-your-network-for-microsoft-365"></a><span data-ttu-id="5a5c1-103">为 Microsoft 365 设置你的网络</span><span class="sxs-lookup"><span data-stu-id="5a5c1-103">Set up your network for Microsoft 365</span></span>

<span data-ttu-id="5a5c1-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="5a5c1-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="5a5c1-p101">你的 Microsoft 365 加入的一个重要部分是确保设置了你的网络和 Internet 连接以实现优化的访问。配置您的本地网络以访问全局分布式软件即服务 (SaaS) 云不同于针对本地数据中心和中心 Internet 连接进行了优化的传统网络。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-p101">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span></span> 

<span data-ttu-id="5a5c1-107">使用以下文章来理解它们之间的关键区别，并修改你的边缘设备、客户端计算机和内部网络，以为本地用户获得最佳性能。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-107">Use these articles to understand the key differences and to modify your edge devices, client computers, and on-premises network to get the best performance for your on-premises users.</span></span>

## <a name="how-microsoft-365-networking-works"></a><span data-ttu-id="5a5c1-108">Microsoft 365 网络的工作原理</span><span class="sxs-lookup"><span data-stu-id="5a5c1-108">How Microsoft 365 networking works</span></span>

<span data-ttu-id="5a5c1-109">请参阅以下文章，了解 Microsoft 365 的连接概述：</span><span class="sxs-lookup"><span data-stu-id="5a5c1-109">See these articles for an overview of connectivity for Microsoft 365:</span></span>

- [<span data-ttu-id="5a5c1-110">Microsoft 365 网络连接概述</span><span class="sxs-lookup"><span data-stu-id="5a5c1-110">Microsoft 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="5a5c1-111">Microsoft 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="5a5c1-111">Microsoft 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="5a5c1-112">评估 Microsoft 365 网络连接</span><span class="sxs-lookup"><span data-stu-id="5a5c1-112">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="5a5c1-113">有关增强性能的建议，请参阅[适用于 Microsoft 365 的网络规划和性能调整](network-planning-and-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-113">For advice on enhancing performance, see [Network planning and performance tuning for Microsoft 365](network-planning-and-performance.md).</span></span>

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="5a5c1-114">支持将 Microsoft 365 网络作为网络设备供应商</span><span class="sxs-lookup"><span data-stu-id="5a5c1-114">Support Microsoft 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="5a5c1-p102">如果你是网络设备供应商，请加入 [Office 365 网络合作伙伴计划](office-365-networking-partner-program.md)。加入该计划即可在你的产品和解决方案中构建 Office 365 网络连接原则。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="5a5c1-117">Office 365 端点</span><span class="sxs-lookup"><span data-stu-id="5a5c1-117">Office 365 endpoints</span></span>

<span data-ttu-id="5a5c1-118">端点是 Internet 上 Office 365 流量的目的 IP 地址、DNS 域名和 URL 的集合。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="5a5c1-p103">若要优化基于 Office 365 云的服务的性能，需要使用你的客户端浏览器和边缘网络中的设备对某些端点进行特殊处理。这些设备包括防火墙设备、SSL 中断与检查设备、数据包检查设备以及数据丢失防护系统。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-p103">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="5a5c1-121">有关详细信息，请参阅[管理 Office 365 端点](managing-office-365-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="5a5c1-p104">目前有五个不同的 Office 365 云。此表将转到每个端点的列表。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="5a5c1-124">全球端点</span><span class="sxs-lookup"><span data-stu-id="5a5c1-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="5a5c1-125">针对全球 Office 365 订阅的端点，其中包括美国政府社区云 (GCC) 订阅。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="5a5c1-126">美国政府 DoD 端点</span><span class="sxs-lookup"><span data-stu-id="5a5c1-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="5a5c1-127">针对美国国防部 (DoD) 订阅的端点。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="5a5c1-128">美国政府 GCC 高端点</span><span class="sxs-lookup"><span data-stu-id="5a5c1-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="5a5c1-129">针对美国政府社区云高（GCC 高）订阅的端点。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="5a5c1-130">由世纪互联运营的 Office 365 端点</span><span class="sxs-lookup"><span data-stu-id="5a5c1-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="5a5c1-131">由世纪互联运营的 Office 365 的端点，旨在满足中国境内对 Office 365 的需求。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="5a5c1-132">Office 365 Germany 端点</span><span class="sxs-lookup"><span data-stu-id="5a5c1-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="5a5c1-133">为德国、欧盟 (EU) 和欧洲自由贸易协会 (EFTA) 中监管最严格的客户在欧洲建立的独立云的端点。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="5a5c1-134">若要自动获取 Office 365 云的最新端点列表，请参阅 [Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="5a5c1-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="5a5c1-135">有关额外的端点，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="5a5c1-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="5a5c1-136">Web 服务中未包含的其他端点</span><span class="sxs-lookup"><span data-stu-id="5a5c1-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="5a5c1-137">Office 2016 for Mac 中的网络请求</span><span class="sxs-lookup"><span data-stu-id="5a5c1-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a><span data-ttu-id="5a5c1-138">Microsoft 365 网络的其他主题</span><span class="sxs-lookup"><span data-stu-id="5a5c1-138">Additional topics for Microsoft 365 networking</span></span>

<span data-ttu-id="5a5c1-139">请参阅以下文章，了解 Microsoft 365 网络中的专门主题：</span><span class="sxs-lookup"><span data-stu-id="5a5c1-139">See these articles for specialized topics in Microsoft 365 networking:</span></span>

- [<span data-ttu-id="5a5c1-140">内容传递网络</span><span class="sxs-lookup"><span data-stu-id="5a5c1-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="5a5c1-141">Office 365 服务中的 IPv6 支持</span><span class="sxs-lookup"><span data-stu-id="5a5c1-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="5a5c1-142">Office 365 的 NAT 支持</span><span class="sxs-lookup"><span data-stu-id="5a5c1-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a><span data-ttu-id="5a5c1-143">适用于 Microsoft 365 的 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="5a5c1-143">ExpressRoute for Microsoft 365</span></span>

<span data-ttu-id="5a5c1-144">请参阅以下文章，了解适用于 Office 365 的 ExpressRoute 的流量使用：</span><span class="sxs-lookup"><span data-stu-id="5a5c1-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="5a5c1-145">适用于 Office 365 的 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="5a5c1-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="5a5c1-146">实现 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="5a5c1-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="5a5c1-147">ExpressRoute for Office 365 网络计划</span><span class="sxs-lookup"><span data-stu-id="5a5c1-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="5a5c1-148">通过适用于 Office 365 的 ExpressRoute 进行路由</span><span class="sxs-lookup"><span data-stu-id="5a5c1-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
