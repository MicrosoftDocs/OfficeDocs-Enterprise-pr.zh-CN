---
title: M365 管理中心中的 Office 365 网络载入工具（预览）
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
description: M365 管理中心中的 Office 365 网络载入工具（预览）
ms.openlocfilehash: 7ead201d78c1a6ce971c6ff09d4be9c0d2c76be6
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106260"
---
# <a name="office-365-network-onboarding-tool-in-the-m365-admin-center-preview"></a><span data-ttu-id="d1afe-103">M365 管理中心中的 Office 365 网络载入工具（预览）</span><span class="sxs-lookup"><span data-stu-id="d1afe-103">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>

<span data-ttu-id="d1afe-104">Office 365 网络载入工具位于<https://connectivity.office.com>。</span><span class="sxs-lookup"><span data-stu-id="d1afe-104">The Office 365 network onboarding tool is located at <https://connectivity.office.com>.</span></span> <span data-ttu-id="d1afe-105">它是一个辅助工具，可用于**运行状况 | 的 Microsoft 365 管理中心内的网络洞察力和网络积分信息。网络性能**菜单。</span><span class="sxs-lookup"><span data-stu-id="d1afe-105">It is an adjunct tool to the network insights and network score information available in the Microsoft 365 Admin Center under the **Health | Network Performance** menu.</span></span>

<span data-ttu-id="d1afe-106">Microsoft 365 管理中心的网络洞察力基于 Office 365 租户的产品度量。</span><span class="sxs-lookup"><span data-stu-id="d1afe-106">The network insights in the Microsoft 365 Admin Center are based on in-product measurements for your Office 365 tenant.</span></span> <span data-ttu-id="d1afe-107">相比之下，Office 365 网络载入工具中的网络洞察力在该工具中本地运行。</span><span class="sxs-lookup"><span data-stu-id="d1afe-107">In comparison, the network insights from the Office 365 network onboarding tool are run locally in the tool.</span></span> <span data-ttu-id="d1afe-108">可以在产品中完成的测试是有限的，并且可以通过在用户的本地运行测试来收集更多数据，从而获得更深入的见解。</span><span class="sxs-lookup"><span data-stu-id="d1afe-108">Testing that can be done in-product is limited and by running tests local to the user more data can be gathered resulting in deeper insights.</span></span> <span data-ttu-id="d1afe-109">请考虑，Microsoft 365 管理中心中的网络见解将显示在特定办公地点使用 Office 365 的网络问题。</span><span class="sxs-lookup"><span data-stu-id="d1afe-109">Consider then that the network insights in the Microsoft 365 Admin Center will show that there is a networking problem for use of Office 365 at a specific office location.</span></span> <span data-ttu-id="d1afe-110">Office 365 网络载入工具可帮助确定问题的根本原因，从而导致建议的网络性能改进操作。</span><span class="sxs-lookup"><span data-stu-id="d1afe-110">The Office 365 network onboarding tool can help to identify the root cause of that problem leading to a recommended network performance improvement action.</span></span>

<span data-ttu-id="d1afe-111">我们建议将这些信息结合使用，以便可以在 Microsoft 365 管理中心中对每个办公室位置评估网络质量状态，并在部署基于 Office 365 网络载入工具的测试之后找到更多的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d1afe-111">We recommend that these be used together where networking quality status can be assessed for each office location in the Microsoft 365 Admin Center and more specifics can be found after deployment of testing based on the Office 365 network onboarding tool.</span></span>

>[!IMPORTANT]
><span data-ttu-id="d1afe-112">网络性能建议、Microsoft 365 管理中心中的真知灼见和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Office 365 租户。</span><span class="sxs-lookup"><span data-stu-id="d1afe-112">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="the-advanced-tests-client-application"></a><span data-ttu-id="d1afe-113">高级测试客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="d1afe-113">The advanced tests client application</span></span>

<span data-ttu-id="d1afe-114">Office 365 网络载入工具有两个组成部分。</span><span class="sxs-lookup"><span data-stu-id="d1afe-114">There are two parts to the Office 365 network onboarding tool.</span></span> <span data-ttu-id="d1afe-115">网站<https://connectivity.office.com>有一个可下载的 Windows 客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="d1afe-115">There is the web site <https://connectivity.office.com> and there is a downloadable Windows client application.</span></span> <span data-ttu-id="d1afe-116">可下载的客户端运行高级网络连接测试，大多数测试都需要运行此测试。</span><span class="sxs-lookup"><span data-stu-id="d1afe-116">The downloadable client runs advanced network connectivity tests and most of the tests require this to be run.</span></span>

<span data-ttu-id="d1afe-117">您可以从网站运行高级客户端测试，它会在运行时将结果重新填充到网页中。</span><span class="sxs-lookup"><span data-stu-id="d1afe-117">You can run the advanced client test from the web site, and it will populate results back into the web page as it runs.</span></span>

![O365 网络载入工具示例测试结果](Media/m365-mac-perf/m365-mac-perf-onboarding-tool-tests.png)

## <a name="user-office-location"></a><span data-ttu-id="d1afe-119">用户办公室位置</span><span class="sxs-lookup"><span data-stu-id="d1afe-119">User office location</span></span>

<span data-ttu-id="d1afe-120">用户办公室的位置是从用户 web 浏览器中检测到的。</span><span class="sxs-lookup"><span data-stu-id="d1afe-120">The user office location is detected from the users web browser.</span></span> <span data-ttu-id="d1afe-121">它用于标识与企业网络周边的特定部分之间的网络距离。</span><span class="sxs-lookup"><span data-stu-id="d1afe-121">It is used to identify network distances to specific parts of the enterprise network perimeter.</span></span>

<span data-ttu-id="d1afe-122">用户办公室位置显示在地图视图中。</span><span class="sxs-lookup"><span data-stu-id="d1afe-122">The user office location is shown on the map view.</span></span>

## <a name="distance-to-the-network-egress-location"></a><span data-ttu-id="d1afe-123">到网络传出位置的距离</span><span class="sxs-lookup"><span data-stu-id="d1afe-123">Distance to the network egress location</span></span>

<span data-ttu-id="d1afe-124">我们在服务器端标识网络出口 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d1afe-124">We identify the network egress IP Address on the server side.</span></span> <span data-ttu-id="d1afe-125">位置数据库用于查找网络出口的大概位置，并确定从该位置到办公室位置的距离。</span><span class="sxs-lookup"><span data-stu-id="d1afe-125">Location databases are used to look up the approximate location for the network egress and determine the distance from that location to the office location.</span></span> <span data-ttu-id="d1afe-126">如果距离大于500英里（800公里），这将显示为网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-126">This is shown as a network insight if the distance is greater than 500 miles (800 kilometers).</span></span>

<span data-ttu-id="d1afe-127">网络出局位置显示在地图视图中，并连接到用户办公室位置，以指示企业 WAN 中的网络 backhaul。</span><span class="sxs-lookup"><span data-stu-id="d1afe-127">The network egress location is shown on the map view and connected to the user office location indicating the network backhaul inside of the enterprise WAN.</span></span>

<span data-ttu-id="d1afe-128">从网络传出 IP 地址查找的位置可能不准确，这将导致此测试产生错误结果。</span><span class="sxs-lookup"><span data-stu-id="d1afe-128">The location looked up from the network egress IP Address may not be accurate and this would lead to a false result from this test.</span></span> <span data-ttu-id="d1afe-129">若要验证是否为特定 IP 地址出现此错误，可以使用可公开访问的网络 IP 地址位置网站。</span><span class="sxs-lookup"><span data-stu-id="d1afe-129">To validate if this error is occurring for a specific IP Address you can use publicly accessible network IP Address location web sites.</span></span>

<span data-ttu-id="d1afe-130">建议将本地和直接的网络出口从用户办公室位置实施到 Internet，Office 365 网络连接。</span><span class="sxs-lookup"><span data-stu-id="d1afe-130">Implementing local and direct network egress from user office locations to the Internet is recommended for Office 365 network connectivity.</span></span> <span data-ttu-id="d1afe-131">对本地和直接出口的改进是解决此网络洞察力的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="d1afe-131">Improvements to local and direct egress are the best way to address this network insight.</span></span>

## <a name="exchange-online-service-front-door"></a><span data-ttu-id="d1afe-132">Exchange Online 服务前盖</span><span class="sxs-lookup"><span data-stu-id="d1afe-132">Exchange Online service front door</span></span>

<span data-ttu-id="d1afe-133">以 Outlook 执行此功能的相同方式标识了 "使用中的 Exchange Online 服务前向门"，并将网络 TCP 延迟从用户办公室位置测量到它。</span><span class="sxs-lookup"><span data-stu-id="d1afe-133">The in-use Exchange Online service front door is identified in the same way that Outlook does this and we measure the network TCP latency from the user office location to it.</span></span> <span data-ttu-id="d1afe-134">将显示这些说明，并将与当前位置的建议最佳服务前盖列表进行比较，以供使用的 Exchange Online 服务前向。</span><span class="sxs-lookup"><span data-stu-id="d1afe-134">These are both shown and the in-use Exchange Online service front door is compared to the list of recommended optimal service front doors for the current location.</span></span> <span data-ttu-id="d1afe-135">如果使用非最佳 Exchange Online 服务前向门，这会显示为网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-135">This is shown as a network insight if a non-optimal Exchange Online service front door is in use.</span></span>

<span data-ttu-id="d1afe-136">使用非最佳 Exchange Online 服务前盖可能是由于网络 backhaul 在公司网络出口前，在这种情况下，我们建议本地和直接网络出口。</span><span class="sxs-lookup"><span data-stu-id="d1afe-136">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="d1afe-137">也可能是由于使用远程 DNS 递归冲突解决服务器而导致的，在这种情况下，我们建议您将 DNS 递归解析器服务器与网络出口对齐。</span><span class="sxs-lookup"><span data-stu-id="d1afe-137">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="d1afe-138">我们计算对 Exchange Online 服务前向门的 TCP 延迟的潜在改进。</span><span class="sxs-lookup"><span data-stu-id="d1afe-138">We calculate a potential improvement in TCP latency to the Exchange Online service front door.</span></span> <span data-ttu-id="d1afe-139">为此，请查看测试的用户办公室位置网络延迟，并将网络延迟从当前位置减去当前位置，再减去 closets Exchange Online service 前门。</span><span class="sxs-lookup"><span data-stu-id="d1afe-139">This is done by looking at the tested user office location network latency and subtracting the network latency from the current location to the closets Exchange Online service front door.</span></span> <span data-ttu-id="d1afe-140">不同之处表示潜在的改进机会。</span><span class="sxs-lookup"><span data-stu-id="d1afe-140">The difference represents the potential opportunity for improvement.</span></span>

## <a name="comparison-of-performance-of-customers-in-the-area"></a><span data-ttu-id="d1afe-141">区域中客户的性能比较</span><span class="sxs-lookup"><span data-stu-id="d1afe-141">Comparison of performance of customers in the area</span></span>

<span data-ttu-id="d1afe-142">与同一地铁区域中的其他 Office 365 客户相比，Exchange Online 服务前向的用户办公室位置的网络 TCP 延迟。</span><span class="sxs-lookup"><span data-stu-id="d1afe-142">The network TCP latency of the user office location to the Exchange Online service front door is compared to other Office 365 customers in the same metro area.</span></span> <span data-ttu-id="d1afe-143">如果在同一地铁区域中10% 或更多的客户具有更好的性能，则显示网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-143">A network insight is shown if 10% or more of customers in the same metro area have better performance.</span></span>

<span data-ttu-id="d1afe-144">根据城市中的所有用户都可以访问相同的电信基础结构和与 Internet 电路和 Microsoft 网络的邻近性，生成网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-144">This network insight is generated on the basis that all users in a city have access to the same telecommunications infrastructure and the same proximity to Internet circuits and Microsoft's network.</span></span>

## <a name="in-use-default-gateway"></a><span data-ttu-id="d1afe-145">使用默认网关</span><span class="sxs-lookup"><span data-stu-id="d1afe-145">In use default gateway</span></span>

<span data-ttu-id="d1afe-146">"使用中的默认网关" 是测试客户端为路由 TCP/IP 网络连接而配置的路由器。</span><span class="sxs-lookup"><span data-stu-id="d1afe-146">The in-use default gateway is the router that the test client has configured for routing TCP/IP network connections.</span></span>

<span data-ttu-id="d1afe-147">提供此功能仅用于提供信息，并不会影响网络的洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-147">This is provided for information only and does not contribute to any network insight.</span></span>

## <a name="in-use-dns-servers"></a><span data-ttu-id="d1afe-148">在使用 DNS 服务器</span><span class="sxs-lookup"><span data-stu-id="d1afe-148">In use DNS server(s)</span></span>

<span data-ttu-id="d1afe-149">此示例显示在运行测试的客户端计算机上配置的 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="d1afe-149">This shows the DNS server configured on the client machine that ran the tests.</span></span> <span data-ttu-id="d1afe-150">它可能是 DNS 递归解析器服务器，但这并不常见。</span><span class="sxs-lookup"><span data-stu-id="d1afe-150">It might be a DNS Recursive Resolver server however this is uncommon.</span></span> <span data-ttu-id="d1afe-151">它更可能是缓存 DNS 结果并将任何未缓存的 DNS 请求转发到另一个 DNS 服务器的 DNS 转发器服务器。</span><span class="sxs-lookup"><span data-stu-id="d1afe-151">It is more likely to be a DNS forwarder server which caches DNS results and forwards any uncached DNS requests to another DNS server.</span></span>

<span data-ttu-id="d1afe-152">提供此功能仅用于提供信息，并不会影响网络的洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-152">This is provided for information only and does not contribute to any network insight.</span></span>

## <a name="identified-dns-recursive-resolver-server"></a><span data-ttu-id="d1afe-153">已标识 DNS 递归冲突解决服务器</span><span class="sxs-lookup"><span data-stu-id="d1afe-153">Identified DNS Recursive Resolver server</span></span>

<span data-ttu-id="d1afe-154">通过发出特定的 DNS 请求，然后向 DNS 名称服务器提供来自收到相同请求的 IP 地址，可以标识使用中的 DNS 递归冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="d1afe-154">The in-use DNS Recursive Resolver is identified by making a specific DNS request and then asking the DNS Name Server for the IP Address that it received the same request from.</span></span> <span data-ttu-id="d1afe-155">此 IP 地址是 DNS 递归解析程序，将在 IP 地址位置数据库中查找以找到该位置。</span><span class="sxs-lookup"><span data-stu-id="d1afe-155">This IP Address is the DNS Recursive Resolver and it will be looked up in IP Address location databases to find the location.</span></span> <span data-ttu-id="d1afe-156">然后计算从用户办公室位置到 DNS 递归解析服务器位置之间的距离。</span><span class="sxs-lookup"><span data-stu-id="d1afe-156">The distance from the user office location to the DNS Recursive Resolver server location is then calculated.</span></span> <span data-ttu-id="d1afe-157">如果距离大于500英里（800公里），这将显示为网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-157">This is shown as a network insight if the distance is greater than 500 miles (800 kilometers).</span></span>

<span data-ttu-id="d1afe-158">从网络传出 IP 地址查找的位置可能不准确，这将导致此测试产生错误结果。</span><span class="sxs-lookup"><span data-stu-id="d1afe-158">The location looked up from the network egress IP Address may not be accurate and this would lead to a false result from this test.</span></span> <span data-ttu-id="d1afe-159">若要验证是否为特定 IP 地址出现此错误，可以使用可公开访问的网络 IP 地址位置网站。</span><span class="sxs-lookup"><span data-stu-id="d1afe-159">To validate if this error is occurring for a specific IP Address you can use publicly accessible network IP Address location web sites.</span></span>

<span data-ttu-id="d1afe-160">此网络洞察力尤其会影响 Exchange Online 服务前盖的选择。</span><span class="sxs-lookup"><span data-stu-id="d1afe-160">This network insight will specifically impact the selection of the Exchange Online service front door.</span></span> <span data-ttu-id="d1afe-161">若要解决此深入了解，本地和直接网络出口应为先决条件，然后 DNS 递归解析器应位于该网络出口附近。</span><span class="sxs-lookup"><span data-stu-id="d1afe-161">To address this insight local and direct network egress should be a pre-requisite and then DNS Recursive Resolver should be located close to that network egress.</span></span>

## <a name="dns-lookup-of-exchange-online-front-end-server-and-sharepoint-online-front-end-server"></a><span data-ttu-id="d1afe-162">Exchange Online 前端服务器和 SharePoint Online 前端服务器的 DNS 查找</span><span class="sxs-lookup"><span data-stu-id="d1afe-162">DNS lookup of Exchange Online front end server and SharePoint Online front end server</span></span>

<span data-ttu-id="d1afe-163">这些将显示这两个 Office 365 工作负载的服务前向门的 DNS 记录。</span><span class="sxs-lookup"><span data-stu-id="d1afe-163">These show the DNS record for the service front door for these two Office 365 workloads.</span></span> <span data-ttu-id="d1afe-164">仅提供了这些信息，并且没有相关的网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-164">They are provided for information only and there is no associated network insight.</span></span>

## <a name="proxy-server-identification"></a><span data-ttu-id="d1afe-165">代理服务器标识</span><span class="sxs-lookup"><span data-stu-id="d1afe-165">Proxy server identification</span></span>

<span data-ttu-id="d1afe-166">我们标识在本地计算机上配置的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="d1afe-166">We identify proxy server(s) configured on the local machine.</span></span> <span data-ttu-id="d1afe-167">我们确定是否在网络路径中配置了这些配置以优化类别 Office 365 网络流量。</span><span class="sxs-lookup"><span data-stu-id="d1afe-167">We identify if any of these are configured in the network path for optimize category Office 365 network traffic.</span></span> <span data-ttu-id="d1afe-168">我们确定从用户办公室位置到代理服务器的距离。</span><span class="sxs-lookup"><span data-stu-id="d1afe-168">We identify the distance from the user office location to the proxy servers.</span></span> <span data-ttu-id="d1afe-169">先通过 ICMP ping 测试距离，如果此操作失败，我们使用 TCP ping 进行测试，如果失败，则在 IP 地址位置数据库中查找代理服务器 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d1afe-169">The distance is tested first by ICMP ping and if that fails we test with TCP ping and finally if that fails we look up the proxy server IP Address in an IP Address location database.</span></span> <span data-ttu-id="d1afe-170">如果代理服务器的距离远离用户办公室位置的500英里（800公里），我们将显示网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-170">We show a network insight if the proxy server is further than 500 miles (800 kilometers) away from the user office location.</span></span>

## <a name="media-quality-checks"></a><span data-ttu-id="d1afe-171">媒体质量检查</span><span class="sxs-lookup"><span data-stu-id="d1afe-171">Media quality checks</span></span>

<span data-ttu-id="d1afe-172">此测试将安装并运行 Skype for Business 网络评估工具并解释结果。</span><span class="sxs-lookup"><span data-stu-id="d1afe-172">This test installs and runs the Skype for Business network assessment tool and interprets the results.</span></span> <span data-ttu-id="d1afe-173">可以在[https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885)中找到该工具。</span><span class="sxs-lookup"><span data-stu-id="d1afe-173">The tool can be found at [https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885).</span></span>

<span data-ttu-id="d1afe-174">这些是由 Microsoft 团队音频和视频通话和会议功能使用的 UDP 协议测试。</span><span class="sxs-lookup"><span data-stu-id="d1afe-174">These are UDP protocol tests as is used by Microsoft Teams audio and video call and conferencing functionality.</span></span> <span data-ttu-id="d1afe-175">我们测试 UDP 数据包丢失、UDP 网络延迟、UDP 抖动和 UDP 数据包重新排序。</span><span class="sxs-lookup"><span data-stu-id="d1afe-175">We test for UDP packet loss, UDP network latency, UDP jitter, and UDP packet reorder.</span></span> <span data-ttu-id="d1afe-176">如果其中有任何超出允许的范围，则显示网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-176">A network insight is shown if any of these are over the allowable range.</span></span>

## <a name="tcp-connectivity-tests"></a><span data-ttu-id="d1afe-177">TCP 连接测试</span><span class="sxs-lookup"><span data-stu-id="d1afe-177">TCP Connectivity tests</span></span>

<span data-ttu-id="d1afe-178">我们测试从用户办公室位置到所有必需的 Office 365 网络终结点的 HTTP 连接。</span><span class="sxs-lookup"><span data-stu-id="d1afe-178">We test for HTTP connectivity from the user office location to all of the required Office 365 network endpoints.</span></span> <span data-ttu-id="d1afe-179">这些内容是在[https://aka.ms/o365ip](https://aka.ms/o365ip)中发布的。</span><span class="sxs-lookup"><span data-stu-id="d1afe-179">These are published at [https://aka.ms/o365ip](https://aka.ms/o365ip).</span></span> <span data-ttu-id="d1afe-180">对于任何不能连接到的必需网络终结点，都会显示网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-180">A network insight is shown for any required network endpoints which cannot be connected to.</span></span>

<span data-ttu-id="d1afe-181">连接 ay 由企业网络外围上的代理服务器、防火墙或其他网络安全设备阻止，或作为云代理使用。</span><span class="sxs-lookup"><span data-stu-id="d1afe-181">Connectivity ay be blocked by a proxy server, a firewall, or another network security device on the enterprise network perimeter or in use as a cloud proxy.</span></span>

## <a name="ssl-interception-tests"></a><span data-ttu-id="d1afe-182">SSL 侦听测试</span><span class="sxs-lookup"><span data-stu-id="d1afe-182">SSL interception tests</span></span>

<span data-ttu-id="d1afe-183">我们在 "优化" 或 "允许" 类别的 "优化" 或 "允许" 类别中的每个[https://aka.ms/o365ip](https://aka.ms/o365ip)所需 Office 365 网络终结点上测试 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="d1afe-183">We test the SSL certificate at each required Office 365 network endpoint that is in the optimize or allow category as defined at [https://aka.ms/o365ip](https://aka.ms/o365ip).</span></span> <span data-ttu-id="d1afe-184">如果有任何测试未找到 Microsoft SSL 证书，则已连接的加密网络必须已被中间网络设备截取。</span><span class="sxs-lookup"><span data-stu-id="d1afe-184">If any tests do not find a Microsoft SSL certificate, then the encrypted network connected must have been intercepted by an intermediary network device.</span></span> <span data-ttu-id="d1afe-185">网络洞察力显示在任何截获的加密网络终结点上。</span><span class="sxs-lookup"><span data-stu-id="d1afe-185">A network insight is shown on any intercepted encrypted network endpoints.</span></span>

<span data-ttu-id="d1afe-186">在找不到 Microsoft 提供的 SSL 证书的情况下，我们会显示该测试的 FQDN 以及正在使用的 SSL 证书所有者。</span><span class="sxs-lookup"><span data-stu-id="d1afe-186">Where an SSL certificate is found that isn't provided by Microsoft, we show the FQDN for the test and the in-use SSL certificate owner.</span></span> <span data-ttu-id="d1afe-187">此 SSL 证书所有者可能是代理服务器供应商，也可能是企业自签名证书。</span><span class="sxs-lookup"><span data-stu-id="d1afe-187">This SSL certificate owner may be a proxy server vendor, or it may be an enterprise self-signed certificate.</span></span>

## <a name="network-path-diagnostics"></a><span data-ttu-id="d1afe-188">网络路径诊断</span><span class="sxs-lookup"><span data-stu-id="d1afe-188">Network path diagnostics</span></span>

<span data-ttu-id="d1afe-189">本节显示了 ICMP traceroute 对 Exchange Online 服务前向门、SharePoint Online service 前门和 Microsoft 团队服务前盖的结果。</span><span class="sxs-lookup"><span data-stu-id="d1afe-189">This section shows the results of an ICMP traceroute to the Exchange Online service front door, the SharePoint Online service front door, and the Microsoft Teams service front door.</span></span> <span data-ttu-id="d1afe-190">仅提供此信息，没有相关的网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="d1afe-190">It is provided for information only and there is no associated network insight.</span></span>

## <a name="related-topics"></a><span data-ttu-id="d1afe-191">相关主题</span><span class="sxs-lookup"><span data-stu-id="d1afe-191">Related topics</span></span>

[<span data-ttu-id="d1afe-192">Microsoft 365 管理中心中的网络性能建议（预览）</span><span class="sxs-lookup"><span data-stu-id="d1afe-192">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="d1afe-193">Office 365 网络性能见解（预览）</span><span class="sxs-lookup"><span data-stu-id="d1afe-193">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="d1afe-194">Office 365 网络评估（预览）</span><span class="sxs-lookup"><span data-stu-id="d1afe-194">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)
