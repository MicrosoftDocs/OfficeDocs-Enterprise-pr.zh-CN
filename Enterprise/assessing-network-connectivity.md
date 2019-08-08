---
title: 评估 Office 365 网络连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/7/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 旨在让世界各地的客户能够使用 internet 连接连接到服务。 随着服务的演变, Office 365 的安全性、性能和可靠性根据使用 internet 的客户建立与服务的连接而得到改进。
ms.openlocfilehash: 884c4c0d510de55da4125a3e3b80b4bd869ec697
ms.sourcegitcommit: c207aafc126a495e700552796ed89da3de254910
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2019
ms.locfileid: "36233422"
---
# <a name="assessing-office-365-network-connectivity"></a><span data-ttu-id="5ee42-104">评估 Office 365 网络连接</span><span class="sxs-lookup"><span data-stu-id="5ee42-104">Assessing Office 365 network connectivity</span></span>

<span data-ttu-id="5ee42-105">Office 365 旨在让世界各地的客户能够使用 internet 连接连接到服务。</span><span class="sxs-lookup"><span data-stu-id="5ee42-105">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection.</span></span> <span data-ttu-id="5ee42-106">随着服务的演变, Office 365 的安全性、性能和可靠性根据使用 internet 的客户建立与服务的连接而得到改进。</span><span class="sxs-lookup"><span data-stu-id="5ee42-106">As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="5ee42-107">计划使用 Office 365 的客户应评估其现有和预测的 internet 连接需要作为部署项目的一部分。</span><span class="sxs-lookup"><span data-stu-id="5ee42-107">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project.</span></span> <span data-ttu-id="5ee42-108">对于企业级部署, 可靠性和适当调整的 internet 连接性是使用 Office 365 功能和方案的关键部分。</span><span class="sxs-lookup"><span data-stu-id="5ee42-108">For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="5ee42-109">根据您的大小和偏好, 许多不同的人员和组织可以执行网络评估。</span><span class="sxs-lookup"><span data-stu-id="5ee42-109">Network evaluations can be performed by many different people and organizations depending on your size and preferences.</span></span> <span data-ttu-id="5ee42-110">评估的网络范围也可能因您在部署过程中所处的位置而异。</span><span class="sxs-lookup"><span data-stu-id="5ee42-110">The network scope of the assessment can also vary depending on where you're at in your deployment process.</span></span> <span data-ttu-id="5ee42-111">为了帮助您更好地了解执行网络评估所需的内容, 我们生成了一个网络评估指南, 帮助您了解可用的选项。</span><span class="sxs-lookup"><span data-stu-id="5ee42-111">To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you.</span></span> <span data-ttu-id="5ee42-112">此评估将确定要将哪些步骤和资源添加到部署项目, 以使您能够成功采用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="5ee42-112">This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="5ee42-113">全面的网络评估将提供可能的解决方案, 以实现网络设计难题以及实现详细信息。</span><span class="sxs-lookup"><span data-stu-id="5ee42-113">A comprehensive network assessment will provide possible solutions to networking design challenges along with implementation details.</span></span> <span data-ttu-id="5ee42-114">一些网络评估将显示, 与 Office 365 的最佳网络连接可适应现有网络和 internet 出口基础结构的次要配置或设计更改。</span><span class="sxs-lookup"><span data-stu-id="5ee42-114">Some network assessments will show that optimal network connectivity to Office 365 can be accommodated with minor configuration or design changes to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="5ee42-115">某些评估将指示到 Office 365 的网络连接需要在网络组件中进行额外的投资。</span><span class="sxs-lookup"><span data-stu-id="5ee42-115">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components.</span></span> <span data-ttu-id="5ee42-116">例如, 跨分支机构和多个地理区域的企业网络可能需要在 SD WAN 解决方案或优化的路由基础结构中进行投资, 以支持到 Office 365 的 internet 连接。</span><span class="sxs-lookup"><span data-stu-id="5ee42-116">For example, enterprise networks that span branch offices and multiple geographic regions may require investments in SD-WAN solutions or optimized routing infrastructure to support internet connectivity to Office 365.</span></span> <span data-ttu-id="5ee42-117">有时, 评估会指示与 Office 365 的网络连接受法规或对[Skype for Business Online 媒体质量](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)等场景的性能要求的影响。</span><span class="sxs-lookup"><span data-stu-id="5ee42-117">Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span> <span data-ttu-id="5ee42-118">这些额外要求可能会导致 internet 连接基础结构、路由优化和专用直接连接的投资。</span><span class="sxs-lookup"><span data-stu-id="5ee42-118">These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>

<span data-ttu-id="5ee42-119">帮助您评估网络的一些资源:</span><span class="sxs-lookup"><span data-stu-id="5ee42-119">Some resources to help you assess your network:</span></span>

- <span data-ttu-id="5ee42-120">有关 Office 365 网络的概念性信息, 请参阅[Office 365 网络连接概述](office-365-networking-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5ee42-120">See [Office 365 network connectivity overview](office-365-networking-overview.md) for conceptual information about Office 365 networking.</span></span>
- <span data-ttu-id="5ee42-121">请参阅[Office 365 网络连接原则](https://aka.ms/o365networkingprinciples), 了解用于安全管理 Office 365 流量和获得最佳性能的连接原则。</span><span class="sxs-lookup"><span data-stu-id="5ee42-121">See [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span>
- <span data-ttu-id="5ee42-122">注册[Microsoft FastTrack](https://www.microsoft.com/en-us/fasttrack)以获取有关 Office 365 规划、设计和部署的引导式协助。</span><span class="sxs-lookup"><span data-stu-id="5ee42-122">Sign up for [Microsoft FastTrack](https://www.microsoft.com/en-us/fasttrack) for guided assistance with Office 365 planning, design and deployment.</span></span> 
- <span data-ttu-id="5ee42-123">请参阅下面的[Office 365 网络载入工具](assessing-network-connectivity.md#the-office-365-network-onboarding-tool)部分, 运行基本的连接测试, 这些测试提供有关可在给定用户位置和 Office 365 之间进行的网络连接改进的具体指导。</span><span class="sxs-lookup"><span data-stu-id="5ee42-123">See the [Office 365 Network Onboarding tool](assessing-network-connectivity.md#the-office-365-network-onboarding-tool) section below to run basic connectivity tests that provide specific guidance about networking connectivity improvements that can be made between a given user location and Office 365.</span></span>

> [!NOTE]
> <span data-ttu-id="5ee42-124">需要 Microsoft 授权才能使用适用于 Office 365 的 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="5ee42-124">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="5ee42-125">Microsoft 会检查每个客户请求, 并且仅在客户的规章要求要求直接连接时, 才会授权使用适用于 Office 365 的 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="5ee42-125">Microsoft reviews every customer request and only authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="5ee42-126">如果您有这样的要求, 请提供指向您所解释的法规的文本摘录和 web 链接, 这意味着在从[Office 365 请求的 ExpressRoute For Office 请求](https://aka.ms/O365ERReview)中需要直接连接才能开始 Microsoft 评审。</span><span class="sxs-lookup"><span data-stu-id="5ee42-126">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="5ee42-127">尝试为 Office 365 创建路由筛选器的未授权订阅将收到一[条错误消息](https://support.microsoft.com/kb/3181709)。</span><span class="sxs-lookup"><span data-stu-id="5ee42-127">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="5ee42-128">规划 Office 365 的网络评估时需要考虑的关键要点:</span><span class="sxs-lookup"><span data-stu-id="5ee42-128">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="5ee42-129">Office 365 是一种通过公共 internet 运行的安全、可靠、高性能的服务。</span><span class="sxs-lookup"><span data-stu-id="5ee42-129">Office 365 is a secure, reliable, high performance service that runs over the public internet.</span></span> <span data-ttu-id="5ee42-130">我们将继续投资, 以增强服务的这些方面。</span><span class="sxs-lookup"><span data-stu-id="5ee42-130">We continue to invest to enhance these aspects of the service.</span></span> <span data-ttu-id="5ee42-131">所有 Office 365 服务均可通过 internet 连接获得。</span><span class="sxs-lookup"><span data-stu-id="5ee42-131">All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="5ee42-132">我们将不断优化 Office 365 的核心方面, 如可用性、全局覆盖和基于 internet 的连接的性能。</span><span class="sxs-lookup"><span data-stu-id="5ee42-132">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity.</span></span> <span data-ttu-id="5ee42-133">例如, 许多 Office 365 服务利用一组扩展的面向 internet 的边缘节点。</span><span class="sxs-lookup"><span data-stu-id="5ee42-133">For example, many Office 365 services leverage an expanding set of internet facing edge nodes.</span></span> <span data-ttu-id="5ee42-134">此边缘网络为通过 internet 的连接提供最佳的邻近度和性能。</span><span class="sxs-lookup"><span data-stu-id="5ee42-134">This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="5ee42-135">在考虑将 Office 365 用于任何包括的服务 (如团队或 Skype for Business Online 语音、视频或会议功能) 时, 客户应完成端到端网络评估并使用 Microsoft 满足连接要求[FastTrack](https://www.microsoft.com/en-us/fasttrack)。</span><span class="sxs-lookup"><span data-stu-id="5ee42-135">When considering using Office 365 for any of the included services such as Teams or Skype for Business Online voice, video, or meeting capabilities, customers should complete an end to end network assessment and meet connectivity requirements using [Microsoft FastTrack](https://www.microsoft.com/en-us/fasttrack).</span></span>

<span data-ttu-id="5ee42-136">如果您正在评估 Office 365, 并且不确定从哪里开始进行网络评估, 或者发现您需要帮助解决的网络设计难题, 请与你的 Microsoft 帐户团队合作。</span><span class="sxs-lookup"><span data-stu-id="5ee42-136">If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>

## <a name="the-office-365-network-onboarding-tool"></a><span data-ttu-id="5ee42-137">Office 365 网络载入工具</span><span class="sxs-lookup"><span data-stu-id="5ee42-137">The Office 365 Network Onboarding tool</span></span>

<span data-ttu-id="5ee42-138">[Office 365 网络载入工具](https://aka.ms/netonboard)是一种概念证明 (POC) 网络评估工具, 可对 office 365 租户运行基本的连接测试, 并为最佳的 office 365 性能提供具体的网络设计建议。</span><span class="sxs-lookup"><span data-stu-id="5ee42-138">The [Office 365 Network Onboarding tool](https://aka.ms/netonboard) is a proof of concept (POC) network assessment tool that runs basic connectivity tests against your Office 365 tenant and makes specific network design recommendations for optimal Office 365 performance.</span></span> <span data-ttu-id="5ee42-139">该工具突出显示了常见的大型企业网络外围设计选项, 这些选项对于 Internet web 浏览很有用, 但会影响大型 SaaS 应用程序 (如 Office 365) 的性能。</span><span class="sxs-lookup"><span data-stu-id="5ee42-139">The tool highlights common large enterprise network perimeter design choices which are useful for Internet web browsing but impact the performance of large SaaS applications such as Office 365.</span></span>

<span data-ttu-id="5ee42-140">网络载入工具执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="5ee42-140">The Network Onboarding tool does the following:</span></span>

- <span data-ttu-id="5ee42-141">检测您的位置, 也可以指定要测试的位置</span><span class="sxs-lookup"><span data-stu-id="5ee42-141">Detects your location, or you can specify a location to test</span></span>
- <span data-ttu-id="5ee42-142">检查网络出口的位置</span><span class="sxs-lookup"><span data-stu-id="5ee42-142">Checks the location of your network egress</span></span>
- <span data-ttu-id="5ee42-143">测试最近的 Office 365 服务前盖的网络路径</span><span class="sxs-lookup"><span data-stu-id="5ee42-143">Tests the network path to the nearest Office 365 service front door</span></span>
- <span data-ttu-id="5ee42-144">使用可下载的 Windows 10 应用程序提供高级测试, 这些应用程序将提供与代理服务器、防火墙和 DNS 相关的外围网络设计建议。</span><span class="sxs-lookup"><span data-stu-id="5ee42-144">Provides advanced tests using a downloadable Windows 10 application that makes perimeter network design recommendations related to proxy servers, firewalls, and DNS.</span></span> <span data-ttu-id="5ee42-145">该工具还运行 Skype for business Online、Microsoft 团队、SharePoint Online 和 Exchange Online 的性能测试。</span><span class="sxs-lookup"><span data-stu-id="5ee42-145">The tool also runs performance tests for Skype for Business Online, Microsoft Teams, SharePoint Online and Exchange Online.</span></span>

<span data-ttu-id="5ee42-146">该工具包含两个组件: 一个用于收集基本连接信息的基于浏览器的 UI, 以及一个可运行高级测试并返回其他评估数据的可下载的 Windows 10 应用程序。</span><span class="sxs-lookup"><span data-stu-id="5ee42-146">The tool has two components: a browser-based UI that collects basic connectivity information, and a downloadable Windows 10 application that runs advanced tests and returns additional assessment data.</span></span>

<span data-ttu-id="5ee42-147">基于浏览器的工具显示以下信息:</span><span class="sxs-lookup"><span data-stu-id="5ee42-147">The browser-based tool displays the following information:</span></span>

- <span data-ttu-id="5ee42-148">"结果和影响" 选项卡</span><span class="sxs-lookup"><span data-stu-id="5ee42-148">Results and impact tab</span></span>
  - <span data-ttu-id="5ee42-149">正在使用的服务前盖地图上的位置</span><span class="sxs-lookup"><span data-stu-id="5ee42-149">The location on a map of the in-use service front door</span></span>
  - <span data-ttu-id="5ee42-150">其他服务前盖地图上的位置, 可提供最佳连接能力</span><span class="sxs-lookup"><span data-stu-id="5ee42-150">The location on a map of other service front doors that would provide optimal connectivity</span></span>
  - <span data-ttu-id="5ee42-151">与附近的其他 Office 365 客户相比的相对性能</span><span class="sxs-lookup"><span data-stu-id="5ee42-151">Relative performance compared to other Office 365 customers near you</span></span>
- <span data-ttu-id="5ee42-152">详细信息和解决方案选项卡</span><span class="sxs-lookup"><span data-stu-id="5ee42-152">Details and solutions tab</span></span>
  - <span data-ttu-id="5ee42-153">按城市和国家/地区的用户位置</span><span class="sxs-lookup"><span data-stu-id="5ee42-153">User location by city and country</span></span>
  - <span data-ttu-id="5ee42-154">按城市、州和国家/地区的网络出口位置</span><span class="sxs-lookup"><span data-stu-id="5ee42-154">Network egress location by city, state and country</span></span>
  - <span data-ttu-id="5ee42-155">用户进入网络传出距离</span><span class="sxs-lookup"><span data-stu-id="5ee42-155">User to network egress distance</span></span>
  - <span data-ttu-id="5ee42-156">Office 365 Exchange Online 服务前盖位置</span><span class="sxs-lookup"><span data-stu-id="5ee42-156">Office 365 Exchange Online service front door location</span></span>
  - <span data-ttu-id="5ee42-157">用户位置的最佳 Office 365 Exchange Online 服务前端门 (s)</span><span class="sxs-lookup"><span data-stu-id="5ee42-157">Optimal Office 365 Exchange Online service front door(s) for user location</span></span>
  - <span data-ttu-id="5ee42-158">使用更好的性能的大都市区域内的客户</span><span class="sxs-lookup"><span data-stu-id="5ee42-158">Customers in your metro area with better performance</span></span>

<span data-ttu-id="5ee42-159">高级测试下载应用程序提供以下附加信息:</span><span class="sxs-lookup"><span data-stu-id="5ee42-159">The Advanced Tests downloadable application provides the following additional information:</span></span>

- <span data-ttu-id="5ee42-160">"详细信息和解决方案" 选项卡 (追加)</span><span class="sxs-lookup"><span data-stu-id="5ee42-160">Details and solutions tab (appended)</span></span>
  - <span data-ttu-id="5ee42-161">用户的默认网关</span><span class="sxs-lookup"><span data-stu-id="5ee42-161">User's default gateway</span></span>
  - <span data-ttu-id="5ee42-162">客户端 DNS 服务器</span><span class="sxs-lookup"><span data-stu-id="5ee42-162">Client DNS Server</span></span>
  - <span data-ttu-id="5ee42-163">客户端 DNS 递归解析器</span><span class="sxs-lookup"><span data-stu-id="5ee42-163">Client DNS Recursive Resolver</span></span>
  - <span data-ttu-id="5ee42-164">Exchange Online DNS 服务器</span><span class="sxs-lookup"><span data-stu-id="5ee42-164">Exchange Online DNS server</span></span>
  - <span data-ttu-id="5ee42-165">SharePoint Online DNS 服务器</span><span class="sxs-lookup"><span data-stu-id="5ee42-165">SharePoint Online DNS server</span></span>
  - <span data-ttu-id="5ee42-166">代理服务器标识</span><span class="sxs-lookup"><span data-stu-id="5ee42-166">Proxy server identification</span></span>
  - <span data-ttu-id="5ee42-167">媒体连接检查</span><span class="sxs-lookup"><span data-stu-id="5ee42-167">Media connectivity check</span></span>
  - <span data-ttu-id="5ee42-168">媒体质量数据包丢失</span><span class="sxs-lookup"><span data-stu-id="5ee42-168">Media quality packet loss</span></span>
  - <span data-ttu-id="5ee42-169">媒体质量延迟</span><span class="sxs-lookup"><span data-stu-id="5ee42-169">Media quality latency</span></span>
  - <span data-ttu-id="5ee42-170">媒体质量抖动</span><span class="sxs-lookup"><span data-stu-id="5ee42-170">Media quality jitter</span></span>
  - <span data-ttu-id="5ee42-171">媒体质量数据包重新排序</span><span class="sxs-lookup"><span data-stu-id="5ee42-171">Media quality packet reorder</span></span>
- <span data-ttu-id="5ee42-172">对多个特定于功能的终结点的连接性测试</span><span class="sxs-lookup"><span data-stu-id="5ee42-172">Connectivity tests to multiple feature-specific endpoints</span></span>
- <span data-ttu-id="5ee42-173">包含适用于 Exchange Online、SharePoint Online 和团队服务的 tracert 和延迟数据的网络路径诊断</span><span class="sxs-lookup"><span data-stu-id="5ee42-173">Network path diagnostics that include tracert and latency data for the Exchange Online, SharePoint Online and Teams services</span></span>

<span data-ttu-id="5ee42-174">您可以阅读有关 Office 365 网络载入工具的信息, 并在[更新的 Office 365 网络载入工具 POC 中提供反馈, 其中包含新的网络设计建议](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130)博客文章。</span><span class="sxs-lookup"><span data-stu-id="5ee42-174">You can read about the Office 365 Network Onboarding tool and provide feedback at the [Updated Office 365 Network Onboarding Tool POC with new network design recommendations](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) blog post.</span></span> <span data-ttu-id="5ee42-175">有关此工具的未来更新和其他 Office 365 网络更新的信息将发布到[Office 365 网络](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)博客。</span><span class="sxs-lookup"><span data-stu-id="5ee42-175">Information about future updates to this tool and other Office 365 networking updates will be posted to the [Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) blog.</span></span>
  
<span data-ttu-id="5ee42-176">以下是可用于返回的简短链接: [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="5ee42-176">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5ee42-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ee42-177">See also</span></span>

[<span data-ttu-id="5ee42-178">Office 365 网络连接概述</span><span class="sxs-lookup"><span data-stu-id="5ee42-178">Office 365 Network Connectivity Overview</span></span>](office-365-networking-overview.md)

[<span data-ttu-id="5ee42-179">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="5ee42-179">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)

[<span data-ttu-id="5ee42-180">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="5ee42-180">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="5ee42-181">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="5ee42-181">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="5ee42-182">Office 365 IP 地址和 URL Web 服务</span><span class="sxs-lookup"><span data-stu-id="5ee42-182">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="5ee42-183">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="5ee42-183">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
