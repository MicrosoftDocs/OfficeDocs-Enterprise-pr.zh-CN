---
title: 适用于中国用户的 Office 365 全局租户性能优化
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/13/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
f1.keywords:
- NOCSH
description: 本文提供了针对全球 Office 365 租户的中国用户优化网络性能的指南。
ms.openlocfilehash: 33e475dfbf4accf306a099542cf8cf2f22ff23a5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106266"
---
# <a name="office-365-global-tenant-performance-optimization-for-china-users"></a><span data-ttu-id="016b8-103">适用于中国用户的 Office 365 全局租户性能优化</span><span class="sxs-lookup"><span data-stu-id="016b8-103">Office 365 global tenant performance optimization for China users</span></span>

>[!IMPORTANT]
><span data-ttu-id="016b8-104">本指南特定于使用**位于中国的企业办公室365用户**连接到**全球 Office 365 租户**的使用方案。</span><span class="sxs-lookup"><span data-stu-id="016b8-104">This guidance is specific to usage scenarios in which **enterprise Office 365 users located in China** connect to a **global Office 365 tenant**.</span></span> <span data-ttu-id="016b8-105">本**指南不适用于**由世纪互联运营的 Office 365 中的租户。</span><span class="sxs-lookup"><span data-stu-id="016b8-105">This guidance does **not** apply to tenants in Office 365 operated by 21Vianet.</span></span>

<span data-ttu-id="016b8-106">对于具有全球 Office 365 租户和中国中的公司状态的企业，基于中国的用户的 Office 365 客户端性能可能会因与中国电讯 Internet 体系结构独有的因素而变得复杂。</span><span class="sxs-lookup"><span data-stu-id="016b8-106">For enterprises with global Office 365 tenants and a corporate presence in China, Office 365 client performance for China-based users can be complicated by factors unique to China Telco's Internet architecture.</span></span>

<span data-ttu-id="016b8-107">中国 Isp 已对全球公共 Internet 的受管制近海连接，该连接可通过易于访问的外围设备的网络拥塞的高级别。</span><span class="sxs-lookup"><span data-stu-id="016b8-107">China ISPs have regulated offshore connections to the global public Internet that go through perimeter devices which are prone to high-levels of cross-border network congestion.</span></span> <span data-ttu-id="016b8-108">此拥塞为进出中国的所有 Internet 流量创建数据包丢失和延迟。</span><span class="sxs-lookup"><span data-stu-id="016b8-108">This congestion creates packet loss and latency for all Internet traffic going into and out of China.</span></span>

![Office 365 流量-未优化](media/O365-networking/China-O365-unoptimized.png)

<span data-ttu-id="016b8-110">数据包丢失和延迟对网络服务的性能造成不利影响，尤其是需要大型数据交换的服务（如大型文件传输）或需要近似的实时性能（音频和视频应用程序）。</span><span class="sxs-lookup"><span data-stu-id="016b8-110">Packet loss and latency is detrimental to the performance of network services, especially services that require large data exchanges (such as large file transfers) or requiring near real-time performance (audio and video applications).</span></span>

<span data-ttu-id="016b8-111">本主题的目标是提供缓解 Office 365 服务上的中国交叉边框网络拥塞影响的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="016b8-111">The goal of this topic is to provide best practices for mitigating the impact of China cross-border network congestion on Office 365 services.</span></span> <span data-ttu-id="016b8-112">本主题不解决其他常见的最后一个性能问题，例如，由于在中国运营商的复杂路由而导致的高数据包延迟的问题。</span><span class="sxs-lookup"><span data-stu-id="016b8-112">This topic does not address other common last-mile performance issues such as issues of high packet latency due to complex routing within China carriers.</span></span>

## <a name="corporate-network-best-practices"></a><span data-ttu-id="016b8-113">公司网络最佳实践</span><span class="sxs-lookup"><span data-stu-id="016b8-113">Corporate network best practices</span></span>

<span data-ttu-id="016b8-114">许多具有全球 Office 365 租户和中国用户的企业已实施专用网络，以在中国办公室位置和世界各地的近海位置之间执行公司网络通信。</span><span class="sxs-lookup"><span data-stu-id="016b8-114">Many enterprises with global Office 365 tenants and users in China have implemented private networks that carry corporate network traffic between China office locations and offshore locations around the world.</span></span> <span data-ttu-id="016b8-115">这些企业可以利用此网络基础结构避免跨边框网络拥塞，并在中国优化其 Office 365 服务性能。</span><span class="sxs-lookup"><span data-stu-id="016b8-115">These enterprises can leverage this network infrastructure to avoid cross-border network congestion and optimize their Office 365 service performance in China.</span></span>

>[!IMPORTANT]
><span data-ttu-id="016b8-116">与所有专用 WAN 实现一样，您应始终咨询您的国家和/或地区的法规要求，以确保您的网络配置符合合规性要求。</span><span class="sxs-lookup"><span data-stu-id="016b8-116">As with all private WAN implementations, you should always consult regulatory requirements for your country and/or region to ensure that your network configuration is in compliance.</span></span>

<span data-ttu-id="016b8-117">第一步，请务必遵循[针对 Office 365 的网络规划和性能优化](https://aka.ms/tune)中的基准网络指导。</span><span class="sxs-lookup"><span data-stu-id="016b8-117">As a first step, it is crucial that you follow our benchmark network guidance at [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span> <span data-ttu-id="016b8-118">如果可能，主要目标应是避免从中国的 Internet 访问全球 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="016b8-118">The primary goal should be to avoid accessing global Office 365 services from the Internet in China if possible.</span></span>

- <span data-ttu-id="016b8-119">利用现有的专用网络在中国的公共 Internet 上的中国办公室网络和近海位置之间携带 Office 365 网络通信。</span><span class="sxs-lookup"><span data-stu-id="016b8-119">Leverage your existing private network to carry Office 365 network traffic between China office networks and offshore locations that egress on the public Internet outside China.</span></span> <span data-ttu-id="016b8-120">在中国之外的任何位置几乎都可以提供明显的好处。</span><span class="sxs-lookup"><span data-stu-id="016b8-120">Almost any location outside China will provide a clear benefit.</span></span> <span data-ttu-id="016b8-121">网络管理员可以通过与[Microsoft 全局网络](https://docs.microsoft.com/azure/networking/microsoft-global-network)的低延迟互连的区域中的附近进一步进行优化。</span><span class="sxs-lookup"><span data-stu-id="016b8-121">Network administrators can further optimize by egressing in areas with low-latency interconnect with the [Microsoft global network](https://docs.microsoft.com/azure/networking/microsoft-global-network).</span></span> <span data-ttu-id="016b8-122">中国香港、日本和韩国是示例。</span><span class="sxs-lookup"><span data-stu-id="016b8-122">Hong Kong, Japan, and South Korea are examples.</span></span>
- <span data-ttu-id="016b8-123">通过 VPN 连接配置用户设备以访问企业网络，以允许 Office 365 流量传输企业网络的专用近海链接。</span><span class="sxs-lookup"><span data-stu-id="016b8-123">Configure user devices to access the corporate network over a VPN connection to allow Office 365 traffic to transit the corporate network's private offshore link.</span></span> <span data-ttu-id="016b8-124">确保 VPN 客户端未配置为使用拆分隧道，或者用户设备配置为忽略 Office 365 流量的拆分隧道。</span><span class="sxs-lookup"><span data-stu-id="016b8-124">Ensure that VPN clients are either not configured to use split tunneling, or that user devices are configured to ignore split tunneling for Office 365 traffic.</span></span>
- <span data-ttu-id="016b8-125">将您的网络配置为在您的专用近海链接中路由所有 Office 365 流量。</span><span class="sxs-lookup"><span data-stu-id="016b8-125">Configure your network to route all Office 365 traffic across your private offshore link.</span></span> <span data-ttu-id="016b8-126">如果您必须最大限度地减少专用链路上的流量，则可以选择仅在 "**优化**" 类别中路由终结点，并允许请求**允许**和**默认**终结点传输 Internet。</span><span class="sxs-lookup"><span data-stu-id="016b8-126">If you must minimize the volume of traffic on your private link, you can choose to only route endpoints in the **Optimize** category, and allow requests to **Allow** and **Default** endpoints to transit the Internet.</span></span> <span data-ttu-id="016b8-127">这样可以将经过优化的流量限制为对高延迟和数据包丢失最敏感的关键服务，从而提高性能并最大限度地减少带宽消耗。</span><span class="sxs-lookup"><span data-stu-id="016b8-127">This will improve performance and minimize bandwidth consumption by limiting optimized traffic to critical services that are most sensitive to high latency and packet loss.</span></span>
- <span data-ttu-id="016b8-128">如果可能，请将 UDP （而不是 TCP）用于实时媒体流流量，例如针对团队的。</span><span class="sxs-lookup"><span data-stu-id="016b8-128">If possible, use UDP instead of TCP for live media streaming traffic, such as for Teams.</span></span> <span data-ttu-id="016b8-129">UDP 提供了比 TCP 更好的实时媒体流性能。</span><span class="sxs-lookup"><span data-stu-id="016b8-129">UDP offers better live media streaming performance than TCP.</span></span>

<span data-ttu-id="016b8-130">有关如何选择性路由 Office 365 流量的信息，请参阅[管理 office 365 终结点](managing-office-365-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="016b8-130">For information about how to selectively route Office 365 traffic, see [Managing Office 365 endpoints](managing-office-365-endpoints.md).</span></span> <span data-ttu-id="016b8-131">有关所有全球 Office 365 Url 和 IP 地址的列表，请参阅[Office 365 url 和 ip 地址范围](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="016b8-131">For a list of all worldwide Office 365 URLs and IP addresses, see [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>

![Office 365 流量优化](media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a><span data-ttu-id="016b8-133">用户最佳实践</span><span class="sxs-lookup"><span data-stu-id="016b8-133">User best practices</span></span>

<span data-ttu-id="016b8-134">在与企业网络无连接的情况下，在中华人民共和国中连接到全球办公室365租户（如住宅、咖啡店、旅馆和分支机构）的用户可能会遇到较差的网络性能，因为其设备和 Office 之间的流量365必须传输中国拥塞的交叉边界网络电路。</span><span class="sxs-lookup"><span data-stu-id="016b8-134">Users in China who connect to global Office 365 tenants from remote locations such as homes, coffee shops, hotels and branch offices with no connection to enterprise networks can experience poor network performance because traffic between their devices and Office 365 must transit China's congested cross-border network circuits.</span></span>

<span data-ttu-id="016b8-135">如果不能选择对公司网络中的交叉边框专用网络和/或 VPN 进行访问，则可以通过培训基于中国的用户来遵循这些最佳做法，从而缓解每用户性能问题。</span><span class="sxs-lookup"><span data-stu-id="016b8-135">If cross-border private networks and/or VPN access into the corporate network are not an option, per-user performance issues can still be mitigated by training your China-based users to follow these best practices.</span></span>

- <span data-ttu-id="016b8-136">利用支持缓存的丰富 Office 客户端（例如，Outlook、团队、OneDrive 等），并避免基于 web 的客户端。</span><span class="sxs-lookup"><span data-stu-id="016b8-136">Utilize rich Office clients that support caching (e.g. Outlook, Teams, OneDrive, etc.), and avoid web-based clients.</span></span> <span data-ttu-id="016b8-137">Office 客户端缓存和脱机访问功能可以显著降低网络拥塞和延迟的影响。</span><span class="sxs-lookup"><span data-stu-id="016b8-137">Office client caching and offline access features can dramatically reduce the impact of network congestion and latency.</span></span>
- <span data-ttu-id="016b8-138">如果你的 Office 365 租户已配置_音频会议_功能，则团队用户可以通过公用电话交换网（PSTN）加入会议。</span><span class="sxs-lookup"><span data-stu-id="016b8-138">If your Office 365 tenant has been configured with the _Audio Conferencing_ feature, Teams users can join meetings via the public switched telephone network (PSTN).</span></span> <span data-ttu-id="016b8-139">有关详细信息，请参阅[Office 365 中的音频会议](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365)。</span><span class="sxs-lookup"><span data-stu-id="016b8-139">For more information, see [Audio Conferencing in Office 365](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365).</span></span>
- <span data-ttu-id="016b8-140">如果用户遇到网络性能问题，他们应向 IT 部门报告故障排除问题，并在怀疑 Office 365 服务出现问题时升级到 Microsoft 支持部门。</span><span class="sxs-lookup"><span data-stu-id="016b8-140">If users experience network performance issues, they should report to their IT department for troubleshooting, and escalate to Microsoft support if trouble with Office 365 services is suspected.</span></span> <span data-ttu-id="016b8-141">并非所有问题都是由交叉边界的网络性能引起的。</span><span class="sxs-lookup"><span data-stu-id="016b8-141">Not all issues are caused by cross-border network performance.</span></span>

<span data-ttu-id="016b8-142">Microsoft 不断努力改进 Office 365 用户体验，并通过网络体系结构和特征的最广泛的可能范围来改进客户端的性能。</span><span class="sxs-lookup"><span data-stu-id="016b8-142">Microsoft is continually working to improve the Office 365 user experience and the performance of clients over the widest possible range of network architectures and characteristics.</span></span> <span data-ttu-id="016b8-143">访问[Office 365 技术社区](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General)以启动或加入对话、查找资源并提交功能请求和建议。</span><span class="sxs-lookup"><span data-stu-id="016b8-143">Visit the [Office 365 Tech Community](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General) to start or join a conversation, find resources, and submit feature requests and suggestions.</span></span>

## <a name="related-topics"></a><span data-ttu-id="016b8-144">相关主题</span><span class="sxs-lookup"><span data-stu-id="016b8-144">Related topics</span></span>

[<span data-ttu-id="016b8-145">Office 365 的网络规划和性能优化</span><span class="sxs-lookup"><span data-stu-id="016b8-145">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="016b8-146">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="016b8-146">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="016b8-147">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="016b8-147">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="016b8-148">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="016b8-148">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="016b8-149">Microsoft 全局网络</span><span class="sxs-lookup"><span data-stu-id="016b8-149">Microsoft global network</span></span>](https://docs.microsoft.com/azure/networking/microsoft-global-network)
