---
title: Office 365 网络性能见解（预览）
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
description: Office 365 网络性能见解（预览）
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106265"
---
# <a name="office-365-network-performance-insights-preview"></a><span data-ttu-id="dffd2-103">Office 365 网络性能见解（预览）</span><span class="sxs-lookup"><span data-stu-id="dffd2-103">Office 365 network performance insights (preview)</span></span>

<span data-ttu-id="dffd2-104">Microsoft 365 管理中心网络性能页面显示了 Office 365 网络见解，可帮助为你的办公室位置设计网络外围。</span><span class="sxs-lookup"><span data-stu-id="dffd2-104">The Microsoft 365 Admin Center network performance pages show Office 365 network insights which can help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="dffd2-105">每个办公地点可能会显示五个特定的网络见解。</span><span class="sxs-lookup"><span data-stu-id="dffd2-105">There are five specific network insights that may be shown for each office location.</span></span>

>[!IMPORTANT]
><span data-ttu-id="dffd2-106">网络性能建议、Microsoft 365 管理中心中的真知灼见和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Office 365 租户。</span><span class="sxs-lookup"><span data-stu-id="dffd2-106">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="dffd2-107">Backhauled 网络出口</span><span class="sxs-lookup"><span data-stu-id="dffd2-107">Backhauled network egress</span></span>

<span data-ttu-id="dffd2-108">从用户到网络传出的距离大于500英里（800公里），预计会影响性能。</span><span class="sxs-lookup"><span data-stu-id="dffd2-108">The distance from the user location to the network egress is greater than 500 miles (800 kilometers) and this is expected to be impacting performance.</span></span> <span data-ttu-id="dffd2-109">建议对用户更接近的本地出口。</span><span class="sxs-lookup"><span data-stu-id="dffd2-109">Local egress closer to the user is recommended.</span></span>

<span data-ttu-id="dffd2-110">这表明办公室位置和网络出局之间的距离超过500英里。</span><span class="sxs-lookup"><span data-stu-id="dffd2-110">This identifies that the distance between the office location and the network egress is more than 500 miles.</span></span> <span data-ttu-id="dffd2-111">办公室位置由模糊的客户端计算机位置标识，并且网络出口位置通过使用反向 IP 地址到 location 数据库来标识。</span><span class="sxs-lookup"><span data-stu-id="dffd2-111">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="dffd2-112">如果在计算机上禁用了 Windows 定位服务，则办公室位置可能不准确。</span><span class="sxs-lookup"><span data-stu-id="dffd2-112">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="dffd2-113">如果反向 IP 地址数据库信息不准确，则网络传出位置可能不准确。</span><span class="sxs-lookup"><span data-stu-id="dffd2-113">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="dffd2-114">此洞察力的详细信息包括办公地点、网络出口位置以及它们之间的距离。</span><span class="sxs-lookup"><span data-stu-id="dffd2-114">Details for this insight include the office location, the network egress location, and the distance between them.</span></span>

<span data-ttu-id="dffd2-115">为此，我们建议将网络出口离办公室位置更近，以便连接可以最适合在 Internet 上的 Microsoft 网络中和到 Office 365 服务的前端。</span><span class="sxs-lookup"><span data-stu-id="dffd2-115">For this insight we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's network on the Internet and onto Office 365 service front doors.</span></span> <span data-ttu-id="dffd2-116">由于 Microsoft 会在将来对用户的网络出口进行关闭，因此 Microsoft 会在将来更好地扩展状态和 Office 365 服务前端的网络数据点。</span><span class="sxs-lookup"><span data-stu-id="dffd2-116">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="dffd2-117">在某些摘要视图中，这种洞察力缩写为 "出局"。</span><span class="sxs-lookup"><span data-stu-id="dffd2-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="dffd2-118">为附近的客户检测到更好的性能</span><span class="sxs-lookup"><span data-stu-id="dffd2-118">Better performance detected for customers near you</span></span>

<span data-ttu-id="dffd2-119">由于大都市区域中的大量客户的性能高于组织在此办公室位置的性能。</span><span class="sxs-lookup"><span data-stu-id="dffd2-119">Since a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="dffd2-120">这就是与此办公室所在地在同一个城市中的 Office 365 客户的聚合性能。</span><span class="sxs-lookup"><span data-stu-id="dffd2-120">This looks at the aggregate performance of Office 365 customers in the same city as this office location.</span></span>

![相对网络性能](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

<span data-ttu-id="dffd2-122">我们在更好的性能存储桶中计算同一城市中的 Office 365 客户的百分比。</span><span class="sxs-lookup"><span data-stu-id="dffd2-122">We calculate the percentage of Office 365 customers in the same city in better performance buckets.</span></span> <span data-ttu-id="dffd2-123">如果大于10%，则显示网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="dffd2-123">If this number if 10% of more then we show the network insight.</span></span>

<span data-ttu-id="dffd2-124">在某些摘要视图中，这种洞察力缩写为 "对等方"。</span><span class="sxs-lookup"><span data-stu-id="dffd2-124">This insight is abbreviated as "Peers" in some summary views.</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="dffd2-125">使用非最佳 Exchange Online 服务前门</span><span class="sxs-lookup"><span data-stu-id="dffd2-125">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="dffd2-126">用户未连接到最佳的 Office 365 服务前盖，这会影响性能。</span><span class="sxs-lookup"><span data-stu-id="dffd2-126">The user is not connecting to an optimal Office 365 service front door and this is expected to be impacting performance.</span></span>

<span data-ttu-id="dffd2-127">我们列出了适用于办公室所在地城市的 Exchange Online 服务前盖，且具有出色的性能。</span><span class="sxs-lookup"><span data-stu-id="dffd2-127">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="dffd2-128">如果当前测试显示使用 Exchange Online 服务的前向不在此列表中，则我们称之为 "建议"。</span><span class="sxs-lookup"><span data-stu-id="dffd2-128">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

<span data-ttu-id="dffd2-129">使用非最佳 Exchange Online 服务前盖可能是由于网络 backhaul 在公司网络出口前，在这种情况下，我们建议本地和直接网络出口。</span><span class="sxs-lookup"><span data-stu-id="dffd2-129">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="dffd2-130">也可能是由于使用远程 DNS 递归冲突解决服务器而导致的，在这种情况下，我们建议您将 DNS 递归解析器服务器与网络出口对齐。</span><span class="sxs-lookup"><span data-stu-id="dffd2-130">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="dffd2-131">在某些摘要视图中，这种洞察力缩写为 "传送"。</span><span class="sxs-lookup"><span data-stu-id="dffd2-131">This insight is abbreviated as "Routing" in some summary views.</span></span>

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="dffd2-132">使用非最佳的 SharePoint Online 服务前盖</span><span class="sxs-lookup"><span data-stu-id="dffd2-132">Use of non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="dffd2-133">用户未连接到最接近的 SharePoint Online 服务前向门。</span><span class="sxs-lookup"><span data-stu-id="dffd2-133">The user is not connecting to the closest SharePoint Online service front door.</span></span> <span data-ttu-id="dffd2-134">这预计会影响性能。</span><span class="sxs-lookup"><span data-stu-id="dffd2-134">This is expected to be impacting performance.</span></span>

<span data-ttu-id="dffd2-135">我们确定测试客户端连接到的 SharePoint Online 服务前向门。</span><span class="sxs-lookup"><span data-stu-id="dffd2-135">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="dffd2-136">然后，对于办公室所在地的城市，我们会将其与该城市的预期 SharePoint Online 服务前门进行比较。</span><span class="sxs-lookup"><span data-stu-id="dffd2-136">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="dffd2-137">如果不匹配，则建议这样做。</span><span class="sxs-lookup"><span data-stu-id="dffd2-137">If it doesn't match, then we make this recommendation.</span></span>

<span data-ttu-id="dffd2-138">在某些摘要视图中，这种洞察力缩写为 "Afd"。</span><span class="sxs-lookup"><span data-stu-id="dffd2-138">This insight is abbreviated as "Afd" in some summary views.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="dffd2-139">SharePoint 前门的低下载速度</span><span class="sxs-lookup"><span data-stu-id="dffd2-139">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="dffd2-140">检测到的子最佳网络下载速度会影响从 OneDrive for Business 加载文档所需的时间。</span><span class="sxs-lookup"><span data-stu-id="dffd2-140">Sub optimal network download speed detected which impacts how long it takes to load documents from OneDrive for Business.</span></span>

<span data-ttu-id="dffd2-141">用户可以从 SharePoint Online 和 OneDrive for business 服务前向前端获取的下载速度以每秒兆字节（MBps）为单位。</span><span class="sxs-lookup"><span data-stu-id="dffd2-141">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="dffd2-142">如果此值小于 1 MBps，则提供此洞察力。</span><span class="sxs-lookup"><span data-stu-id="dffd2-142">If this value is less than 1 MBps then we provide this insight.</span></span>

<span data-ttu-id="dffd2-143">若要提高用户可以获得带宽的下载速度，可能需要增加。</span><span class="sxs-lookup"><span data-stu-id="dffd2-143">To improve download speed that a user can get bandwidth may need to be increased.</span></span> <span data-ttu-id="dffd2-144">或者，在办公室地点的用户计算机与 SharePoint Online service 前门之间可能存在网络拥塞。</span><span class="sxs-lookup"><span data-stu-id="dffd2-144">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="dffd2-145">这有时称为 congestive 丢失，它限制了用户可以使用的下载速度，即使有足够的带宽可用。</span><span class="sxs-lookup"><span data-stu-id="dffd2-145">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

<span data-ttu-id="dffd2-146">在某些摘要视图中，这种洞察力缩写为 "吞吐量"。</span><span class="sxs-lookup"><span data-stu-id="dffd2-146">This insight is abbreviated as "Throughput" in some summary views.</span></span>

## <a name="related-topics"></a><span data-ttu-id="dffd2-147">相关主题</span><span class="sxs-lookup"><span data-stu-id="dffd2-147">Related topics</span></span>

[<span data-ttu-id="dffd2-148">Microsoft 365 管理中心中的网络性能建议（预览）</span><span class="sxs-lookup"><span data-stu-id="dffd2-148">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="dffd2-149">Office 365 网络评估（预览）</span><span class="sxs-lookup"><span data-stu-id="dffd2-149">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="dffd2-150">M365 管理中心中的 Office 365 网络载入工具（预览）</span><span class="sxs-lookup"><span data-stu-id="dffd2-150">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
