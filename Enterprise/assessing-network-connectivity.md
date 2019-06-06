---
title: 评估 Office 365 网络连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
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
ms.openlocfilehash: 3ea80ddccaf9fabbe158a10f0af1d35dbf3a9889
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "34724822"
---
# <a name="assessing-office-365-network-connectivity"></a><span data-ttu-id="12fc9-104">评估 Office 365 网络连接</span><span class="sxs-lookup"><span data-stu-id="12fc9-104">Assessing Office 365 network connectivity</span></span>

<span data-ttu-id="12fc9-105">Office 365 旨在让世界各地的客户能够使用 internet 连接连接到服务。</span><span class="sxs-lookup"><span data-stu-id="12fc9-105">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection.</span></span> <span data-ttu-id="12fc9-106">随着服务的演变, Office 365 的安全性、性能和可靠性根据使用 internet 的客户建立与服务的连接而得到改进。</span><span class="sxs-lookup"><span data-stu-id="12fc9-106">As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="12fc9-107">计划使用 Office 365 的客户应评估其现有和预测的 internet 连接需要作为部署项目的一部分。</span><span class="sxs-lookup"><span data-stu-id="12fc9-107">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project.</span></span> <span data-ttu-id="12fc9-108">对于企业级部署, 可靠性和适当调整的 internet 连接性是使用 Office 365 功能和方案的关键部分。</span><span class="sxs-lookup"><span data-stu-id="12fc9-108">For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="12fc9-109">根据您的大小和偏好, 许多不同的人员和组织可以执行网络评估。</span><span class="sxs-lookup"><span data-stu-id="12fc9-109">Network evaluations can be performed by many different people and organizations depending on your size and preferences.</span></span> <span data-ttu-id="12fc9-110">评估的网络范围也可能因您在部署过程中所处的位置而异。</span><span class="sxs-lookup"><span data-stu-id="12fc9-110">The network scope of the assessment can also vary depending on where you're at in your deployment process.</span></span> <span data-ttu-id="12fc9-111">为了帮助您更好地了解执行网络评估所需的内容, 我们生成了一个网络评估指南, 帮助您了解可用的选项。</span><span class="sxs-lookup"><span data-stu-id="12fc9-111">To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you.</span></span> <span data-ttu-id="12fc9-112">此评估将确定要将哪些步骤和资源添加到部署项目, 以使您能够成功采用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="12fc9-112">This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="12fc9-113">像[Skype 运营框架](https://www.skypeoperationsframework.com/)中规定的那样, 全面的网络评估将提供可能的解决方案, 以实现网络设计难题以及实现详细信息。</span><span class="sxs-lookup"><span data-stu-id="12fc9-113">A comprehensive network assessment, like those prescribed in the [Skype Operations Framework](https://www.skypeoperationsframework.com/) will provide possible solutions to networking design challenges along with implementation details.</span></span> <span data-ttu-id="12fc9-114">大多数网络评估将指示到 Office 365 的网络连接可适应现有网络和 internet 出口基础结构的[次要配置或设计更改](https://aka.ms/manageo365endpoints)。</span><span class="sxs-lookup"><span data-stu-id="12fc9-114">Most network assessments will indicate network connectivity to Office 365 can be accommodated with [minor configuration or design changes](https://aka.ms/manageo365endpoints) to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="12fc9-115">某些评估将指示到 Office 365 的网络连接需要在网络组件中进行额外的投资。</span><span class="sxs-lookup"><span data-stu-id="12fc9-115">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components.</span></span> <span data-ttu-id="12fc9-116">例如, WAN 带宽或优化的路由基础结构中的投资, 以支持到 Office 365 的 internet 连接。</span><span class="sxs-lookup"><span data-stu-id="12fc9-116">For example, investments in WAN bandwidth or optimized routing infrastructure to support internet connectivity to Office 365.</span></span> <span data-ttu-id="12fc9-117">有时, 评估会指示与 Office 365 的网络连接受法规或对[Skype for Business Online 媒体质量](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)等场景的性能要求的影响。</span><span class="sxs-lookup"><span data-stu-id="12fc9-117">Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span> <span data-ttu-id="12fc9-118">这些额外要求可能会导致 internet 连接基础结构、路由优化和专用直接连接的投资。</span><span class="sxs-lookup"><span data-stu-id="12fc9-118">These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>
  
> [!NOTE]
> <span data-ttu-id="12fc9-119">需要 Microsoft 授权才能使用适用于 Office 365 的 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="12fc9-119">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="12fc9-120">Microsoft 会检查每个客户请求, 并且仅在客户的规章要求要求直接连接时, 才会授权使用适用于 Office 365 的 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="12fc9-120">Microsoft reviews every customer request and only authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="12fc9-121">如果您有这样的要求, 请提供指向您所解释的法规的文本摘录和 web 链接, 这意味着在从[Office 365 请求的 ExpressRoute For Office 请求](https://aka.ms/O365ERReview)中需要直接连接才能开始 Microsoft 评审。</span><span class="sxs-lookup"><span data-stu-id="12fc9-121">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="12fc9-122">尝试为 Office 365 创建路由筛选器的未授权订阅将收到一[条错误消息](https://support.microsoft.com/kb/3181709)。</span><span class="sxs-lookup"><span data-stu-id="12fc9-122">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="12fc9-123">规划 Office 365 的网络评估时需要考虑的关键要点:</span><span class="sxs-lookup"><span data-stu-id="12fc9-123">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="12fc9-124">Office 365 是一种通过公共 internet 运行的安全、可靠、高性能的服务。</span><span class="sxs-lookup"><span data-stu-id="12fc9-124">Office 365 is a secure, reliable, high performance service that runs over the public internet.</span></span> <span data-ttu-id="12fc9-125">我们将继续投资, 以增强服务的这些方面。</span><span class="sxs-lookup"><span data-stu-id="12fc9-125">We continue to invest to enhance these aspects of the service.</span></span> <span data-ttu-id="12fc9-126">所有 Office 365 服务均可通过 internet 连接获得。</span><span class="sxs-lookup"><span data-stu-id="12fc9-126">All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="12fc9-127">我们将不断优化 Office 365 的核心方面, 如可用性、全局覆盖和基于 internet 的连接的性能。</span><span class="sxs-lookup"><span data-stu-id="12fc9-127">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity.</span></span> <span data-ttu-id="12fc9-128">例如, 许多 Office 365 服务利用一组扩展的面向 internet 的边缘节点。</span><span class="sxs-lookup"><span data-stu-id="12fc9-128">For example, many Office 365 services leverage an expanding set of internet facing edge nodes.</span></span> <span data-ttu-id="12fc9-129">此边缘网络为通过 internet 的连接提供最佳的邻近度和性能。</span><span class="sxs-lookup"><span data-stu-id="12fc9-129">This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="12fc9-130">在考虑将 Office 365 用于任何包括的服务 (如 Skype for Business Online 语音、视频或会议功能) 时, 客户必须完成端到端网络评估, 并使用我们的 Skype 运营框架满足要求。</span><span class="sxs-lookup"><span data-stu-id="12fc9-130">When considering using Office 365 for any of the included services such as Skype for Business Online voice, video, or meeting capabilities, customers must complete an end to end network assessment and meet requirements using our Skype Operations Framework.</span></span> <span data-ttu-id="12fc9-131">这些客户将有几个选项可满足云连接的特定要求, 包括 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="12fc9-131">These customers will have several options to meet specific requirements for cloud connectivity, including ExpressRoute.</span></span>

<span data-ttu-id="12fc9-132">查看 Microsoft [Office 365 优化网络性能的](https://msdn.microsoft.com/en-us/library/mt450488.aspx)microsoft 个案研究。</span><span class="sxs-lookup"><span data-stu-id="12fc9-132">Have a look at Microsoft's case study [Optimizing network performance for Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx).</span></span> <span data-ttu-id="12fc9-133">如果您正在评估 Office 365, 并且不确定从哪里开始进行网络评估, 或者发现您需要帮助解决的网络设计难题, 请与你的 Microsoft 帐户团队合作。</span><span class="sxs-lookup"><span data-stu-id="12fc9-133">If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>
  
<span data-ttu-id="12fc9-134">此外, 请阅读[office 365 网络连接原则](https://aka.ms/o365networkingprinciples), 了解用于安全管理 Office 365 流量和获得最佳性能的连接原则。</span><span class="sxs-lookup"><span data-stu-id="12fc9-134">Also, read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> <span data-ttu-id="12fc9-135">本文将帮助您了解有关安全优化 Office 365 网络连接的最新指南。</span><span class="sxs-lookup"><span data-stu-id="12fc9-135">This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span>

## <a name="the-office-365-network-onboarding-tool"></a><span data-ttu-id="12fc9-136">Office 365 网络载入工具</span><span class="sxs-lookup"><span data-stu-id="12fc9-136">The Office 365 Network Onboarding tool</span></span>

<span data-ttu-id="12fc9-137">您可以使用[Office 365 网络载入工具](https://aka.ms/netonboard)(新的概念证明 (POC) 工具) 运行基本的连接测试, 这些测试提供有关可在给定用户位置和 Office 365 之间进行的网络连接改进的具体指导。</span><span class="sxs-lookup"><span data-stu-id="12fc9-137">You can use the [Office 365 Network Onboarding tool](https://aka.ms/netonboard), a new proof of concept (POC) tool, to run basic connectivity tests that provide specific guidance about networking connectivity improvements that can be made between a given user location and Office 365.</span></span>

<span data-ttu-id="12fc9-138">网络载入工具执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="12fc9-138">The Network Onboarding tool does the following:</span></span>

- <span data-ttu-id="12fc9-139">检测您的位置, 也可以指定要测试的位置</span><span class="sxs-lookup"><span data-stu-id="12fc9-139">Detects your location, or you can specify a location to test</span></span>
- <span data-ttu-id="12fc9-140">检查网络出口的位置</span><span class="sxs-lookup"><span data-stu-id="12fc9-140">Checks the location of your network egress</span></span>
- <span data-ttu-id="12fc9-141">测试最近的 Office 365 服务前盖的网络路径</span><span class="sxs-lookup"><span data-stu-id="12fc9-141">Tests the network path to the nearest Office 365 service front door</span></span>

<span data-ttu-id="12fc9-142">该工具将显示以下信息:</span><span class="sxs-lookup"><span data-stu-id="12fc9-142">The tool displays the following information:</span></span>

- <span data-ttu-id="12fc9-143">"结果和影响" 选项卡</span><span class="sxs-lookup"><span data-stu-id="12fc9-143">Results and impact tab</span></span>
  - <span data-ttu-id="12fc9-144">正在使用的服务前盖地图上的位置</span><span class="sxs-lookup"><span data-stu-id="12fc9-144">The location on a map of the in-use service front door</span></span>
  - <span data-ttu-id="12fc9-145">其他服务前盖地图上的位置, 可提供最佳连接能力</span><span class="sxs-lookup"><span data-stu-id="12fc9-145">The location on a map of other service front doors that would provide optimal connectivity</span></span>
  - <span data-ttu-id="12fc9-146">与附近的其他 Office 365 客户相比的相对性能</span><span class="sxs-lookup"><span data-stu-id="12fc9-146">Relative performance compared to other Office 365 customers near you</span></span>
- <span data-ttu-id="12fc9-147">详细信息和解决方案选项卡</span><span class="sxs-lookup"><span data-stu-id="12fc9-147">Details and solutions tab</span></span>
  - <span data-ttu-id="12fc9-148">按城市和国家/地区的用户位置</span><span class="sxs-lookup"><span data-stu-id="12fc9-148">User location by city and country</span></span>
  - <span data-ttu-id="12fc9-149">按城市、州和国家/地区的网络出口位置</span><span class="sxs-lookup"><span data-stu-id="12fc9-149">Network egress location by city, state and country</span></span>
  - <span data-ttu-id="12fc9-150">用户进入网络传出距离</span><span class="sxs-lookup"><span data-stu-id="12fc9-150">User to network egress distance</span></span>
  - <span data-ttu-id="12fc9-151">Office 365 Exchange Online 服务前盖位置</span><span class="sxs-lookup"><span data-stu-id="12fc9-151">Office 365 Exchange Online service front door location</span></span>
  - <span data-ttu-id="12fc9-152">用户位置的最佳 Office 365 Exchange Online 服务前端门 (s)</span><span class="sxs-lookup"><span data-stu-id="12fc9-152">Optimal Office 365 Exchange Online service front door(s) for user location</span></span>
  - <span data-ttu-id="12fc9-153">使用更好的性能的大都市区域内的客户</span><span class="sxs-lookup"><span data-stu-id="12fc9-153">Customers in your metro area with better performance</span></span>

<span data-ttu-id="12fc9-154">您可以阅读有关 Office 365 网络载入工具版本的信息, 并在[Office 365 网络性能工具 POC 版本](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102)博客文章中提供反馈。</span><span class="sxs-lookup"><span data-stu-id="12fc9-154">You can read about the Office 365 Network Onboarding tool release and provide feedback at the [Office 365 Network Performance tool POC release](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102) blog post.</span></span> <span data-ttu-id="12fc9-155">有关此工具的未来更新和其他 Office 365 网络更新的信息将发布到[Office 365 网络](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)博客。</span><span class="sxs-lookup"><span data-stu-id="12fc9-155">Information about future updates to this tool and other Office 365 networking updates will be posted to the [Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) blog.</span></span>
  
<span data-ttu-id="12fc9-156">以下是可用于返回的简短链接: [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="12fc9-156">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="12fc9-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12fc9-157">See also</span></span>

[<span data-ttu-id="12fc9-158">Office 365 网络连接概述</span><span class="sxs-lookup"><span data-stu-id="12fc9-158">Office 365 Network Connectivity Overview</span></span>](office-365-networking-overview.md)

[<span data-ttu-id="12fc9-159">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="12fc9-159">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)

[<span data-ttu-id="12fc9-160">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="12fc9-160">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="12fc9-161">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="12fc9-161">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="12fc9-162">Office 365 IP 地址和 URL Web 服务</span><span class="sxs-lookup"><span data-stu-id="12fc9-162">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="12fc9-163">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="12fc9-163">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
