---
title: Office 365 网络评估（预览）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 网络评估（预览）
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106258"
---
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="8bc47-103">Office 365 网络评估（预览）</span><span class="sxs-lookup"><span data-stu-id="8bc47-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="8bc47-104">Office 365 网络评估表明了客户网络连接的相对用户体验的影响。</span><span class="sxs-lookup"><span data-stu-id="8bc47-104">The Office 365 network assessment indicates the relative user experience impact from customer network connectivity.</span></span> <span data-ttu-id="8bc47-105">任何 Microsoft 拥有的网络连接的影响将排除在此之外，以使客户能够优化他们负责的网络设计。</span><span class="sxs-lookup"><span data-stu-id="8bc47-105">The impact of any Microsoft owned network connectivity is excluded from this to enable customers to optimize network designs for which they are responsible.</span></span>

<span data-ttu-id="8bc47-106">它是从影响关键 Office 365 工作负荷中的用户体验的度量计算出来的，并显示为范围为0到100的百分比。</span><span class="sxs-lookup"><span data-stu-id="8bc47-106">It is calculated from measurements that impact user experience in key Office 365 workloads and shown as a percentage with a range of 0 to 100.</span></span>

<span data-ttu-id="8bc47-107">较低的网络分数表示 Office 365 客户端在连接或剩余用户响应时遇到严重问题。</span><span class="sxs-lookup"><span data-stu-id="8bc47-107">A very low network score suggests that Office 365 clients will have significant problems connecting or remaining user responsive.</span></span> <span data-ttu-id="8bc47-108">分数为80% 表示网络连接，您不应预计收到有关 Office 365 用户体验的用户抱怨，因为网络性能。</span><span class="sxs-lookup"><span data-stu-id="8bc47-108">A score of 80% represents network connectivity where you should not expect to receive user complaints about your Office 365 user experience due to your network performance.</span></span> <span data-ttu-id="8bc47-109">随着网络连接的改进，此分数将随用户体验的增加而增加。</span><span class="sxs-lookup"><span data-stu-id="8bc47-109">As network connectivity improvements are made, this score will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="8bc47-110">网络性能建议、Microsoft 365 管理中心中的真知灼见和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Office 365 租户。</span><span class="sxs-lookup"><span data-stu-id="8bc47-110">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="8bc47-111">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="8bc47-111">Exchange Online</span></span>

<span data-ttu-id="8bc47-112">对于 Exchange Online，衡量来自客户端计算机到 Exchange 前端服务器的 TCP 延迟。</span><span class="sxs-lookup"><span data-stu-id="8bc47-112">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="8bc47-113">这可能会受到网络通过客户 LAN 和 WAN 传输的距离的影响。</span><span class="sxs-lookup"><span data-stu-id="8bc47-113">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="8bc47-114">它还可能受到网络中间设备或服务的影响，这些服务会延迟连接或导致发送数据包。</span><span class="sxs-lookup"><span data-stu-id="8bc47-114">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="8bc47-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8bc47-115">SharePoint Online</span></span>

<span data-ttu-id="8bc47-116">对于 SharePoint Online，可以对用户访问文档的下载速度进行衡量。</span><span class="sxs-lookup"><span data-stu-id="8bc47-116">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="8bc47-117">这可能受客户端计算机和 Microsoft 网络之间网络线路上的可用带宽的影响。</span><span class="sxs-lookup"><span data-stu-id="8bc47-117">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="8bc47-118">通常，在复杂网络设备的瓶颈或较差的 Wlan 区域中存在的网络拥塞也会受到影响。</span><span class="sxs-lookup"><span data-stu-id="8bc47-118">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="8bc47-119">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8bc47-119">Microsoft Teams</span></span>

<span data-ttu-id="8bc47-120">对于 Microsoft 团队，网络质量是指 UDP 延迟、UDP 抖动和 UDP 数据包丢失。</span><span class="sxs-lookup"><span data-stu-id="8bc47-120">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="8bc47-121">UDP 可用于 Microsoft 团队的呼叫和会议音频和视频媒体连接。</span><span class="sxs-lookup"><span data-stu-id="8bc47-121">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="8bc47-122">这可能受到与延迟和下载速度相同的因素的影响，除了网络的 UDP 支持中的连接间隙之外，因为 UDP 是分别配置为更常见的 TCP 协议。</span><span class="sxs-lookup"><span data-stu-id="8bc47-122">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="tenant-network-score-and-office-location-network-score"></a><span data-ttu-id="8bc47-123">租户网络分数和办公室位置网络分数</span><span class="sxs-lookup"><span data-stu-id="8bc47-123">Tenant network score and office location network score</span></span>

<span data-ttu-id="8bc47-124">网络分数用于衡量在 Microsoft 网络中办公室位置的网络外围的设计。</span><span class="sxs-lookup"><span data-stu-id="8bc47-124">A network score measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="8bc47-125">对网络周边的改进最好是在每个办公室位置完成，或者在网络连接聚合的位置进行改进，这可能会影响多个位置。</span><span class="sxs-lookup"><span data-stu-id="8bc47-125">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>
<span data-ttu-id="8bc47-126">我们为 "网络性能概述" 页面上的整个 Office 365 租户显示网络分数，在该位置的 "摘要" 页面上显示每个检测到的 office 位置的特定网络分数。</span><span class="sxs-lookup"><span data-stu-id="8bc47-126">We show a network score for the whole Office 365 tenant on the network performance overview page and a specific network score for each detected office location on that location’s summary page.</span></span>

## <a name="network-score-panel"></a><span data-ttu-id="8bc47-127">网络排名面板</span><span class="sxs-lookup"><span data-stu-id="8bc47-127">Network score panel</span></span>

<span data-ttu-id="8bc47-128">每个网络分数无论是针对租户还是针对特定的办公室位置，都会显示一个面板，其中包含有关分数的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8bc47-128">Each network score whether for the tenant or for a specific office location shows a panel with details about the score.</span></span> <span data-ttu-id="8bc47-129">此面板显示分数的条形图，以百分比表示，并作为每个组件工作负荷的总分数，包括仅收到度量数据的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="8bc47-129">This panel shows a bar chart of the score both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="8bc47-130">对于 "办公室位置网络分数"，我们还会显示基准，即报告与您的办公室位置的数据位于同一城市的所有 Office 365 客户端的中值。</span><span class="sxs-lookup"><span data-stu-id="8bc47-130">For an office location network score we also show a benchmark which is the median of all Office 365 clients that reported data in the same City as your office location.</span></span>

<span data-ttu-id="8bc47-131">面板中的分数细分显示了每个组件工作负荷的分数。</span><span class="sxs-lookup"><span data-stu-id="8bc47-131">The score breakdown in the panel shows the score for each of the component workloads.</span></span>

<span data-ttu-id="8bc47-132">分数历史记录显示了得分和基准的过去30天。</span><span class="sxs-lookup"><span data-stu-id="8bc47-132">The score history shows the past 30 days of the score and the benchmark.</span></span>

## <a name="related-topics"></a><span data-ttu-id="8bc47-133">相关主题</span><span class="sxs-lookup"><span data-stu-id="8bc47-133">Related topics</span></span>

[<span data-ttu-id="8bc47-134">Microsoft 365 管理中心中的网络性能建议（预览）</span><span class="sxs-lookup"><span data-stu-id="8bc47-134">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="8bc47-135">Office 365 网络性能见解（预览）</span><span class="sxs-lookup"><span data-stu-id="8bc47-135">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="8bc47-136">M365 管理中心中的 Office 365 网络载入工具（预览）</span><span class="sxs-lookup"><span data-stu-id="8bc47-136">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
