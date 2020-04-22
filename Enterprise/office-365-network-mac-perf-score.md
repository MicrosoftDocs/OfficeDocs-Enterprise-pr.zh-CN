---
title: Microsoft 365 网络评估（预览）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 网络评估（预览）
ms.openlocfilehash: 3554c86b94e6b24cf82231da640b7e010fe07c11
ms.sourcegitcommit: 07ab7d300c8df8b1665cfe569efc506b00915d23
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2020
ms.locfileid: "43612892"
---
# <a name="microsoft-365-network-assessment-preview"></a><span data-ttu-id="69ba2-103">Microsoft 365 网络评估（预览）</span><span class="sxs-lookup"><span data-stu-id="69ba2-103">Microsoft 365 network assessment (preview)</span></span>

<span data-ttu-id="69ba2-104">在 Microsoft 365 管理中心与 Microsoft 365 页面的连接中，**网络评估**将许多网络性能指标的聚合提取到企业网络运行状况的快照中，用点值从 1-100 中表示。</span><span class="sxs-lookup"><span data-stu-id="69ba2-104">In the Microsoft 365 Admin Center's Connectivity to Microsoft 365 page, **network assessments** distill an aggregate of many network performance metrics into a snapshot of your enterprise network health, represented by a points value from 1 - 100.</span></span> <span data-ttu-id="69ba2-105">网络评估的作用范围为整个租户和每个地理位置，用户将从该位置连接到你的租户，从而为 Microsoft 365 管理员提供一种简单的方法来即时了解企业网络运行状况的 gestalt，并快速深入到任何全球办公地点的详细报告。</span><span class="sxs-lookup"><span data-stu-id="69ba2-105">Network assessments are scoped to both the entire tenant and for each geographic location from which users connect to your tenant, providing Microsoft 365 administrators with an easy way to instantly grasp a gestalt of the enterprise's network health and quickly drill down into a detailed report for any global office location.</span></span>

<span data-ttu-id="69ba2-106">网络评估点值是在查看时进行实时编译的延迟、带宽、下载速度和连接质量指标的平均度量。</span><span class="sxs-lookup"><span data-stu-id="69ba2-106">The network assessment points value is an average measurement of latency, bandwidth, download speed and connection quality metrics compiled live at the time they are viewed.</span></span> <span data-ttu-id="69ba2-107">Microsoft 拥有的网络的性能指标将从这些度量中排除，以确保评估结果明确且特定于企业网络。</span><span class="sxs-lookup"><span data-stu-id="69ba2-107">Performance metrics for Microsoft-owned networks are excluded from these measurements to ensure that assessment results are unambiguous and specific to the corporate network.</span></span>

![网络评估价值](Media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

<span data-ttu-id="69ba2-109">非常低的网络评估价值表明 Microsoft 365 客户端将在连接到租户或维护响应前的用户体验时遇到严重问题，而较高的值表示配置正确的网络，且持续的性能问题很少。</span><span class="sxs-lookup"><span data-stu-id="69ba2-109">A very low network assessment value suggests that Microsoft 365 clients will have significant problems connecting to the tenant or maintaining a responsive user experience, while a high value indicates a properly configured network with few ongoing performance issues.</span></span> <span data-ttu-id="69ba2-110">80% 的值表示一个正常的基准，即您不应预期收到有关 Microsoft 365 连接或由于网络性能导致的响应的定期用户意见。</span><span class="sxs-lookup"><span data-stu-id="69ba2-110">A value of 80% represents a healthy baseline where you should not expect to receive regular user complaints about Microsoft 365 connectivity or responsiveness due to network performance.</span></span> <span data-ttu-id="69ba2-111">由于进行了重复的网络连接改进，因此此值将随用户体验的增加而增加。</span><span class="sxs-lookup"><span data-stu-id="69ba2-111">As iterative network connectivity improvements are made, this value will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="69ba2-112">网络洞察力、Microsoft 365 管理中心中的性能建议和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Microsoft 365 租户。</span><span class="sxs-lookup"><span data-stu-id="69ba2-112">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Microsoft 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="network-assessment-panel"></a><span data-ttu-id="69ba2-113">网络评估面板</span><span class="sxs-lookup"><span data-stu-id="69ba2-113">Network assessment panel</span></span>

<span data-ttu-id="69ba2-114">每个网络评估（无论是属于租户还是特定办公室位置）都将显示一个面板，其中包含有关评估的详细信息。</span><span class="sxs-lookup"><span data-stu-id="69ba2-114">Each network assessment, whether scoped to the tenant or to a specific office location, shows a panel with details about the assessment.</span></span> <span data-ttu-id="69ba2-115">此面板显示评估的条形图，以百分比表示，并作为每个组件工作负荷的总积分，包括仅收到度量数据的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="69ba2-115">This panel shows a bar chart of the assessment both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="69ba2-116">对于 office 位置网络评估，我们还显示基准，即报告与您的办公室位置的数据位于同一个城市中的所有 Microsoft 365 客户端的中值。</span><span class="sxs-lookup"><span data-stu-id="69ba2-116">For an office location network assessment, we also show a benchmark which is the median of all Microsoft 365 clients that reported data in the same city as your office location.</span></span>

![示例网络评估值](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

<span data-ttu-id="69ba2-118">面板中的**评估细目**显示了每个组件工作负荷的评估。</span><span class="sxs-lookup"><span data-stu-id="69ba2-118">The **Assessment breakdown** in the panel shows the assessment for each of the component workloads.</span></span>

<span data-ttu-id="69ba2-119">**评估历史记录**显示了最近30天的评估和基准。</span><span class="sxs-lookup"><span data-stu-id="69ba2-119">The **Assessment history** shows the past 30 days of the assessment and the benchmark.</span></span>

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a><span data-ttu-id="69ba2-120">租户网络评估和 office 位置网络评估</span><span class="sxs-lookup"><span data-stu-id="69ba2-120">Tenant network assessments and office location network assessments</span></span>

<span data-ttu-id="69ba2-121">网络评估可衡量办公室的网络外围位置到 Microsoft 网络的设计。</span><span class="sxs-lookup"><span data-stu-id="69ba2-121">A network assessment measures the design of the network perimeter of an office location to Microsoft's network.</span></span> <span data-ttu-id="69ba2-122">对网络周边的改进最好是在每个办公室位置完成，或者在网络连接聚合的位置进行改进，这可能会影响多个位置。</span><span class="sxs-lookup"><span data-stu-id="69ba2-122">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>

<span data-ttu-id="69ba2-123">我们在 "网络性能概述" 页上显示整个 Microsoft 365 租户的网络评估值，并在该位置的 "摘要" 页面上显示每个检测到的 office 位置的特定值。</span><span class="sxs-lookup"><span data-stu-id="69ba2-123">We show a network assessment value for the whole Microsoft 365 tenant on the network performance overview page and a specific value for each detected office location on that location's summary page.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="69ba2-124">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="69ba2-124">Exchange Online</span></span>

<span data-ttu-id="69ba2-125">对于 Exchange Online，衡量来自客户端计算机到 Exchange 前端服务器的 TCP 延迟。</span><span class="sxs-lookup"><span data-stu-id="69ba2-125">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="69ba2-126">这可能会受到网络通过客户 LAN 和 WAN 传输的距离的影响。</span><span class="sxs-lookup"><span data-stu-id="69ba2-126">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="69ba2-127">它还可能受到网络中间设备或服务的影响，这些服务会延迟连接或导致发送数据包。</span><span class="sxs-lookup"><span data-stu-id="69ba2-127">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="69ba2-128">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="69ba2-128">SharePoint Online</span></span>

<span data-ttu-id="69ba2-129">对于 SharePoint Online，可以对用户访问文档的下载速度进行衡量。</span><span class="sxs-lookup"><span data-stu-id="69ba2-129">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="69ba2-130">这可能受客户端计算机和 Microsoft 网络之间网络线路上的可用带宽的影响。</span><span class="sxs-lookup"><span data-stu-id="69ba2-130">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft's network.</span></span> <span data-ttu-id="69ba2-131">通常，在复杂网络设备的瓶颈或较差的 Wlan 区域中存在的网络拥塞也会受到影响。</span><span class="sxs-lookup"><span data-stu-id="69ba2-131">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="69ba2-132">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="69ba2-132">Microsoft Teams</span></span>

<span data-ttu-id="69ba2-133">对于 Microsoft 团队，网络质量是指 UDP 延迟、UDP 抖动和 UDP 数据包丢失。</span><span class="sxs-lookup"><span data-stu-id="69ba2-133">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="69ba2-134">UDP 可用于 Microsoft 团队的呼叫和会议音频和视频媒体连接。</span><span class="sxs-lookup"><span data-stu-id="69ba2-134">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="69ba2-135">这可能受到与延迟和下载速度相同的因素的影响，除了网络的 UDP 支持中的连接间隙之外，因为 UDP 是分别配置为更常见的 TCP 协议。</span><span class="sxs-lookup"><span data-stu-id="69ba2-135">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network's UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="related-topics"></a><span data-ttu-id="69ba2-136">相关主题</span><span class="sxs-lookup"><span data-stu-id="69ba2-136">Related topics</span></span>

[<span data-ttu-id="69ba2-137">Microsoft 365 管理中心中的网络性能建议（预览）</span><span class="sxs-lookup"><span data-stu-id="69ba2-137">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="69ba2-138">Microsoft 365 网络性能见解（预览）</span><span class="sxs-lookup"><span data-stu-id="69ba2-138">Microsoft 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="69ba2-139">M365 管理中心中的 Microsoft 365 连接测试（预览）</span><span class="sxs-lookup"><span data-stu-id="69ba2-139">Microsoft 365 connectivity test in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)

[<span data-ttu-id="69ba2-140">Microsoft 365 网络连接位置服务（预览）</span><span class="sxs-lookup"><span data-stu-id="69ba2-140">Microsoft 365 Network Connectivity Location Services (preview)</span></span>](office-365-network-mac-location-services.md)
