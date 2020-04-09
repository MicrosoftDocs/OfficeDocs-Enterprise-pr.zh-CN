---
title: Microsoft 365 网络见解（预览）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 网络见解（预览）
ms.openlocfilehash: baab4716ace0b15df5878d21987c037372a2754e
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185753"
---
# <a name="microsoft-365-network-insights-preview"></a><span data-ttu-id="9f64a-103">Microsoft 365 网络见解（预览）</span><span class="sxs-lookup"><span data-stu-id="9f64a-103">Microsoft 365 Network Insights (preview)</span></span>

<span data-ttu-id="9f64a-104">**网络洞察力**是从 Microsoft 365 租户收集的实时性能指标，仅供租户中的管理用户查看。</span><span class="sxs-lookup"><span data-stu-id="9f64a-104">**Network insights** are live performance metrics collected from your Microsoft 365 tenant, and available to view only by administrative users in your tenant.</span></span> <span data-ttu-id="9f64a-105">Insights 显示在 Microsoft 365 管理中心的中<https://portal.microsoft.com/adminportal/home#/networkperformance>。</span><span class="sxs-lookup"><span data-stu-id="9f64a-105">Insights are displayed in the Microsoft 365 Admin Center at <https://portal.microsoft.com/adminportal/home#/networkperformance>.</span></span>

<span data-ttu-id="9f64a-106">Insights 旨在帮助为你的办公室位置设计网络外围。</span><span class="sxs-lookup"><span data-stu-id="9f64a-106">Insights are intended to help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="9f64a-107">每个真知灼见都提供有关用户访问你的租户的每个地理位置的特定常见问题的性能特征的实时详细信息。</span><span class="sxs-lookup"><span data-stu-id="9f64a-107">Each insight provides live details about the performance characteristics for a specific common issue for each geographic location where users are accessing your tenant.</span></span>

<span data-ttu-id="9f64a-108">可以为每个办公室位置显示五个特定的网络见解：</span><span class="sxs-lookup"><span data-stu-id="9f64a-108">There are five specific network insights that may be shown for each office location:</span></span>

- [<span data-ttu-id="9f64a-109">Backhauled 网络出口</span><span class="sxs-lookup"><span data-stu-id="9f64a-109">Backhauled network egress</span></span>](#backhauled-network-egress)
- [<span data-ttu-id="9f64a-110">为附近的客户检测到更好的性能</span><span class="sxs-lookup"><span data-stu-id="9f64a-110">Better performance detected for customers near you</span></span>](#better-performance-detected-for-customers-near-you)
- [<span data-ttu-id="9f64a-111">使用非最佳 Exchange Online 服务前门</span><span class="sxs-lookup"><span data-stu-id="9f64a-111">Use of a non-optimal Exchange Online service front door</span></span>](#use-of-a-non-optimal-exchange-online-service-front-door)
- [<span data-ttu-id="9f64a-112">使用非最佳 SharePoint Online 服务前盖</span><span class="sxs-lookup"><span data-stu-id="9f64a-112">Use of a non-optimal SharePoint Online service front door</span></span>](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [<span data-ttu-id="9f64a-113">SharePoint 前门的低下载速度</span><span class="sxs-lookup"><span data-stu-id="9f64a-113">Low download speed from SharePoint front door</span></span>](#low-download-speed-from-sharepoint-front-door)

>[!IMPORTANT]
><span data-ttu-id="9f64a-114">网络洞察力、Microsoft 365 管理中心中的性能建议和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Microsoft 365 租户。</span><span class="sxs-lookup"><span data-stu-id="9f64a-114">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Microsoft 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="9f64a-115">Backhauled 网络出口</span><span class="sxs-lookup"><span data-stu-id="9f64a-115">Backhauled network egress</span></span>

<span data-ttu-id="9f64a-116">如果网络 insights 服务检测到网络传出的给定用户位置的距离大于500英里（800公里），则会显示此洞察力，这表明 Microsoft 365 流量正 backhauled 为公共 Internet 边缘设备或代理。</span><span class="sxs-lookup"><span data-stu-id="9f64a-116">This insight will be displayed if the network insights service detects that the distance from a given user location to the network egress is greater than 500 miles (800 kilometers), indicating that Microsoft 365 traffic is being backhauled to a common Internet edge device or proxy.</span></span>

<span data-ttu-id="9f64a-117">在某些摘要视图中，这种洞察力缩写为 "出局"。</span><span class="sxs-lookup"><span data-stu-id="9f64a-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

![Backhauled 网络出口](Media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="9f64a-119">应用场景</span><span class="sxs-lookup"><span data-stu-id="9f64a-119">What does this mean?</span></span>

<span data-ttu-id="9f64a-120">这表示办公室地点和网络出口之间的距离超过500英里（800公里）。</span><span class="sxs-lookup"><span data-stu-id="9f64a-120">This identifies that the distance between the office location and the network egress is more than 500 miles (800 kilometers).</span></span> <span data-ttu-id="9f64a-121">办公室位置由模糊的客户端计算机位置标识，并且网络出口位置通过使用反向 IP 地址到 location 数据库来标识。</span><span class="sxs-lookup"><span data-stu-id="9f64a-121">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="9f64a-122">如果在计算机上禁用了 Windows 定位服务，则办公室位置可能不准确。</span><span class="sxs-lookup"><span data-stu-id="9f64a-122">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="9f64a-123">如果反向 IP 地址数据库信息不准确，则网络传出位置可能不准确。</span><span class="sxs-lookup"><span data-stu-id="9f64a-123">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="9f64a-124">此洞察力的详细信息包括办公地点、位置总数的租户用户总数、当前网络传出位置、传出位置的相关性、位置和当前出口点之间的距离、第一次检测条件的日期以及解决条件的日期。</span><span class="sxs-lookup"><span data-stu-id="9f64a-124">Details for this insight include the office location, estimated percentage of total tenant user at the location, the current network egress location, relevance of the egress location, the distance between the location and the current egress point, the date the condition was first detected, and the date the condition was resolved.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="9f64a-125">该怎么办？</span><span class="sxs-lookup"><span data-stu-id="9f64a-125">What should I do?</span></span>

<span data-ttu-id="9f64a-126">为此，我们建议网络出口离办公室位置更近，以便连接可以最佳路由到 Microsoft 的全局网络和最接近的 Microsoft 365 服务前盖。</span><span class="sxs-lookup"><span data-stu-id="9f64a-126">For this insight, we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's global network and to the nearest Microsoft 365 service front door.</span></span> <span data-ttu-id="9f64a-127">由于 Microsoft 会在将来对用户的网络出口进行关闭，因此 Microsoft 会在将来对状态和 Microsoft 365 服务前端展开网络点和 Microsoft 服务之前提供改进的性能。</span><span class="sxs-lookup"><span data-stu-id="9f64a-127">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Microsoft 365 service front doors in the future.</span></span>

<span data-ttu-id="9f64a-128">有关如何解决此问题的详细信息，请参阅[Office 365 网络连接原则](office-365-network-connectivity-principles.md)中的[本地传出网络连接](office-365-network-connectivity-principles.md#egress-network-connections-locally)。</span><span class="sxs-lookup"><span data-stu-id="9f64a-128">For more information about how to resolve this issue, see [Egress network connections locally](office-365-network-connectivity-principles.md#egress-network-connections-locally) in [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="9f64a-129">为附近的客户检测到更好的性能</span><span class="sxs-lookup"><span data-stu-id="9f64a-129">Better performance detected for customers near you</span></span>

<span data-ttu-id="9f64a-130">如果网络 insights 服务检测到您的地铁区域中的大量客户具有比在此办公室位置的组织中的用户更好的性能，则会显示此洞察力。</span><span class="sxs-lookup"><span data-stu-id="9f64a-130">This insight will be displayed if the network insights service detects that a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="9f64a-131">在某些摘要视图中，这种洞察力缩写为 "对等方"。</span><span class="sxs-lookup"><span data-stu-id="9f64a-131">This insight is abbreviated as "Peers" in some summary views.</span></span>

![相对网络性能](Media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="9f64a-133">应用场景</span><span class="sxs-lookup"><span data-stu-id="9f64a-133">What does this mean?</span></span>

<span data-ttu-id="9f64a-134">此真知灼见将检查与此办公室所在地在同一个城市中的 Microsoft 365 客户的聚合性能。</span><span class="sxs-lookup"><span data-stu-id="9f64a-134">This insight examines the aggregate performance of Microsoft 365 customers in the same city as this office location.</span></span> <span data-ttu-id="9f64a-135">如果用户的平均延迟大于邻近租户平均延迟的10%，则会显示此洞察力。</span><span class="sxs-lookup"><span data-stu-id="9f64a-135">This insight is displayed if the average latency of your users is 10% greater than the average latency of neighboring tenants.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="9f64a-136">该怎么办？</span><span class="sxs-lookup"><span data-stu-id="9f64a-136">What should I do?</span></span>

<span data-ttu-id="9f64a-137">此条件的原因可能有多种，包括公司网络或 ISP 中的延迟、瓶颈或体系结构设计问题。</span><span class="sxs-lookup"><span data-stu-id="9f64a-137">There could be many reasons for this condition, including latency in your corporate network or ISP, bottlenecks, or architecture design issues.</span></span> <span data-ttu-id="9f64a-138">检查您的办公室网络和当前 Microsoft 365 前端之间路由中的每个跃点之间的延迟。</span><span class="sxs-lookup"><span data-stu-id="9f64a-138">Examine the latency between each hop in the route between your office network and the current Microsoft 365 front door.</span></span> <span data-ttu-id="9f64a-139">有关详细信息，请参阅[Office 365 网络连接原则](office-365-network-connectivity-principles.md)。</span><span class="sxs-lookup"><span data-stu-id="9f64a-139">For more information, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="9f64a-140">使用非最佳 Exchange Online 服务前门</span><span class="sxs-lookup"><span data-stu-id="9f64a-140">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="9f64a-141">如果网络 insights 服务检测到特定位置中的用户未连接到最佳 Exchange Online 服务前盖，将显示此洞察力。</span><span class="sxs-lookup"><span data-stu-id="9f64a-141">This insight will be displayed if the network insights service detects that users in a specific location are not connecting to an optimal Exchange Online service front door.</span></span>

<span data-ttu-id="9f64a-142">在某些摘要视图中，这种洞察力缩写为 "传送"。</span><span class="sxs-lookup"><span data-stu-id="9f64a-142">This insight is abbreviated as "Routing" in some summary views.</span></span>

![非最佳前盖](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="9f64a-144">应用场景</span><span class="sxs-lookup"><span data-stu-id="9f64a-144">What does this mean?</span></span>

<span data-ttu-id="9f64a-145">我们列出了适用于办公室所在地城市的 Exchange Online 服务前盖，且具有出色的性能。</span><span class="sxs-lookup"><span data-stu-id="9f64a-145">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="9f64a-146">如果当前测试显示使用 Exchange Online 服务的前向不在此列表中，则我们称之为 "建议"。</span><span class="sxs-lookup"><span data-stu-id="9f64a-146">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="9f64a-147">该怎么办？</span><span class="sxs-lookup"><span data-stu-id="9f64a-147">What should I do?</span></span>

<span data-ttu-id="9f64a-148">使用非最佳 Exchange Online 服务前盖可能是由于网络 backhaul 在公司网络出口前，在这种情况下，我们建议本地和直接网络出口。</span><span class="sxs-lookup"><span data-stu-id="9f64a-148">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="9f64a-149">也可能是由于使用远程 DNS 递归冲突解决服务器而导致的，在这种情况下，我们建议您将 DNS 递归解析器服务器与网络出口对齐。</span><span class="sxs-lookup"><span data-stu-id="9f64a-149">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="9f64a-150">使用非最佳 SharePoint Online 服务前盖</span><span class="sxs-lookup"><span data-stu-id="9f64a-150">Use of a non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="9f64a-151">如果网络 insights 服务检测到特定位置中的用户未连接到最近的 SharePoint Online 服务前向，将显示此洞察力。</span><span class="sxs-lookup"><span data-stu-id="9f64a-151">This insight will be displayed if the network insights service detects that users in a specific location are not connecting to the closest SharePoint Online service front door.</span></span>

<span data-ttu-id="9f64a-152">在某些摘要视图中，这种洞察力缩写为 "Afd"。</span><span class="sxs-lookup"><span data-stu-id="9f64a-152">This insight is abbreviated as "Afd" in some summary views.</span></span>

![非最佳前盖](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="9f64a-154">应用场景</span><span class="sxs-lookup"><span data-stu-id="9f64a-154">What does this mean?</span></span>

<span data-ttu-id="9f64a-155">我们确定测试客户端连接到的 SharePoint Online 服务前向门。</span><span class="sxs-lookup"><span data-stu-id="9f64a-155">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="9f64a-156">然后，对于办公室所在地的城市，我们会将其与该城市的预期 SharePoint Online 服务前门进行比较。</span><span class="sxs-lookup"><span data-stu-id="9f64a-156">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="9f64a-157">如果不匹配，则建议这样做。</span><span class="sxs-lookup"><span data-stu-id="9f64a-157">If it doesn't match, then we make this recommendation.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="9f64a-158">该怎么办？</span><span class="sxs-lookup"><span data-stu-id="9f64a-158">What should I do?</span></span>

<span data-ttu-id="9f64a-159">使用非最佳的 SharePoint Online 服务前盖可能是由于网络 backhaul 在公司网络出口之前导致的，因此我们建议本地和直接网络出口。</span><span class="sxs-lookup"><span data-stu-id="9f64a-159">Use of a non-optimal SharePoint Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="9f64a-160">也可能是由于使用远程 DNS 递归冲突解决服务器而导致的，在这种情况下，我们建议您将 DNS 递归解析器服务器与网络出口对齐。</span><span class="sxs-lookup"><span data-stu-id="9f64a-160">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="9f64a-161">SharePoint 前门的低下载速度</span><span class="sxs-lookup"><span data-stu-id="9f64a-161">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="9f64a-162">如果网络 insights 服务检测到特定的办公室位置和 SharePoint Online 之间的带宽小于 1 MBps，则会显示此洞察力。</span><span class="sxs-lookup"><span data-stu-id="9f64a-162">This insight will be displayed if the network insights service detects that bandwidth between the specific office location and SharePoint Online is less than 1 MBps.</span></span>

<span data-ttu-id="9f64a-163">在某些摘要视图中，这种洞察力缩写为 "吞吐量"。</span><span class="sxs-lookup"><span data-stu-id="9f64a-163">This insight is abbreviated as "Throughput" in some summary views.</span></span>

### <a name="what-does-this-mean"></a><span data-ttu-id="9f64a-164">应用场景</span><span class="sxs-lookup"><span data-stu-id="9f64a-164">What does this mean?</span></span>

<span data-ttu-id="9f64a-165">用户可以从 SharePoint Online 和 OneDrive for business 服务前向前端获取的下载速度以每秒兆字节（MBps）为单位。</span><span class="sxs-lookup"><span data-stu-id="9f64a-165">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="9f64a-166">如果此值小于 1 MBps，则提供此洞察力。</span><span class="sxs-lookup"><span data-stu-id="9f64a-166">If this value is less than 1 MBps then we provide this insight.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="9f64a-167">该怎么办？</span><span class="sxs-lookup"><span data-stu-id="9f64a-167">What should I do?</span></span>

<span data-ttu-id="9f64a-168">为了提高下载速度，可能需要增加带宽。</span><span class="sxs-lookup"><span data-stu-id="9f64a-168">To improve download speeds, bandwidth may need to be increased.</span></span> <span data-ttu-id="9f64a-169">或者，在办公室地点的用户计算机与 SharePoint Online service 前门之间可能存在网络拥塞。</span><span class="sxs-lookup"><span data-stu-id="9f64a-169">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="9f64a-170">这有时称为 congestive 丢失，它限制了用户可以使用的下载速度，即使有足够的带宽可用。</span><span class="sxs-lookup"><span data-stu-id="9f64a-170">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

## <a name="china-user-optimal-network-egress"></a><span data-ttu-id="9f64a-171">中国用户最佳网络出口</span><span class="sxs-lookup"><span data-stu-id="9f64a-171">China user optimal network egress</span></span>

<span data-ttu-id="9f64a-172">如果组织的用户在连接到你的 Microsoft 365 租户的其他地理位置，则会显示此洞察力。</span><span class="sxs-lookup"><span data-stu-id="9f64a-172">This insight will be displayed if your organization has users in China connecting to your Microsoft 365 tenant in other geographic locations.</span></span> 

### <a name="what-does-this-mean"></a><span data-ttu-id="9f64a-173">应用场景</span><span class="sxs-lookup"><span data-stu-id="9f64a-173">What does this mean?</span></span>

<span data-ttu-id="9f64a-174">如果您的组织具有专用 WAN 连接，我们建议您在中国的办公室位置配置网络 WAN 电路，在以下任一位置将网络出口到 Internet：</span><span class="sxs-lookup"><span data-stu-id="9f64a-174">If your organization has private WAN connectivity, we recommend configuring a network WAN circuit from your office locations in China that has network egress to the Internet in any of the following locations:</span></span>

- <span data-ttu-id="9f64a-175">香港特别行政区</span><span class="sxs-lookup"><span data-stu-id="9f64a-175">Hong Kong</span></span>
- <span data-ttu-id="9f64a-176">日本</span><span class="sxs-lookup"><span data-stu-id="9f64a-176">Japan</span></span>
- <span data-ttu-id="9f64a-177">中国台湾</span><span class="sxs-lookup"><span data-stu-id="9f64a-177">Taiwan</span></span>
- <span data-ttu-id="9f64a-178">韩国</span><span class="sxs-lookup"><span data-stu-id="9f64a-178">South Korea</span></span>
- <span data-ttu-id="9f64a-179">新加坡</span><span class="sxs-lookup"><span data-stu-id="9f64a-179">Singapore</span></span>
- <span data-ttu-id="9f64a-180">马来西亚</span><span class="sxs-lookup"><span data-stu-id="9f64a-180">Malaysia</span></span>

<span data-ttu-id="9f64a-181">远离用户的 Internet 出口与这些位置相比会降低性能，而在中国的出口可能导致由于交叉边界拥塞导致的高延迟和连接问题。</span><span class="sxs-lookup"><span data-stu-id="9f64a-181">Internet egress further away from users than these locations will reduce performance, and egress in China may cause high latency and connectivity issues due to cross-border congestion.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="9f64a-182">该怎么办？</span><span class="sxs-lookup"><span data-stu-id="9f64a-182">What should I do?</span></span>

<span data-ttu-id="9f64a-183">有关如何缓解与此洞察力相关的性能问题的详细信息，请参阅[适用于中国用户的 Office 365 全局租户性能优化](https://docs.microsoft.com/office365/enterprise/office-365-networking-china)。</span><span class="sxs-lookup"><span data-stu-id="9f64a-183">For more information about how to mitigate performance issues related to this insight, see [Office 365 global tenant performance optimization for China users](https://docs.microsoft.com/office365/enterprise/office-365-networking-china).</span></span>

## <a name="related-topics"></a><span data-ttu-id="9f64a-184">相关主题</span><span class="sxs-lookup"><span data-stu-id="9f64a-184">Related topics</span></span>

[<span data-ttu-id="9f64a-185">Microsoft 365 管理中心中的网络性能建议（预览）</span><span class="sxs-lookup"><span data-stu-id="9f64a-185">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="9f64a-186">Microsoft 365 网络评估（预览）</span><span class="sxs-lookup"><span data-stu-id="9f64a-186">Microsoft 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="9f64a-187">M365 管理中心中的 Microsoft 365 网络载入工具（预览）</span><span class="sxs-lookup"><span data-stu-id="9f64a-187">Microsoft 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)

[<span data-ttu-id="9f64a-188">Microsoft 365 网络连接位置服务（预览）</span><span class="sxs-lookup"><span data-stu-id="9f64a-188">Microsoft 365 Network Connectivity Location Services (preview)</span></span>](office-365-network-mac-location-services.md)
