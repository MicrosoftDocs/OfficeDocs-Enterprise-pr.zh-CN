---
title: 与 Office 365 的网络连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2018
ms.audience: ITPro
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
description: Office 365 旨在使世界各地的客户，能够连接到使用连接到 internet 的服务。随着服务的发展，安全性、 性能和 Office 365 的可靠性得到改进基于上使用 internet 建立连接到服务的客户。
ms.openlocfilehash: b72b0a4584542e4c8673c7cf009c66aa97c6b81c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539776"
---
# <a name="network-connectivity-to-office-365"></a><span data-ttu-id="944b1-104">与 Office 365 的网络连接</span><span class="sxs-lookup"><span data-stu-id="944b1-104">Network connectivity to Office 365</span></span>

<span data-ttu-id="944b1-p102">Office 365 旨在使世界各地的客户，能够连接到使用连接到 internet 的服务。随着服务的发展，安全性、 性能和 Office 365 的可靠性得到改进基于上使用 internet 建立连接到服务的客户。</span><span class="sxs-lookup"><span data-stu-id="944b1-p102">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection. As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="944b1-p103">规划使用 Office 365 的客户应评估其现有和预测的 internet 连接需要作为部署项目的一部分。对于企业类部署可靠且适当地调整 internet 连接是使用 Office 365 功能和方案的关键组成部分。</span><span class="sxs-lookup"><span data-stu-id="944b1-p103">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project. For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="944b1-p104">可以通过许多不同的人员和取决于您的规模和首选项的组织执行网络评估。评估网络范围根据其中您是在您的部署过程中也可能不同。为了帮助您更好地了解计执行网络评估，我们已生成的网络评估指南可帮助您了解对您可用的选项。此评估会确定哪些步骤和资源需要添加到部署项目，以使您能够成功采用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="944b1-p104">Network evaluations can be performed by many different people and organizations depending on your size and preferences. The network scope of the assessment can also vary depending on where you're at in your deployment process. To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you. This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="944b1-p105">全面网络评估，如[Skype Operations Framework](https://www.skypeoperationsframework.com/)这些规定可以将提供的实现详细信息以及网络设计挑战可能的解决方案。大多数网络评估将指示网络连接到 Office 365 可容纳与[次要配置或设计更改](https://aka.ms/manageo365endpoints)现有的网络和 internet 出口基础结构。</span><span class="sxs-lookup"><span data-stu-id="944b1-p105">A comprehensive network assessment, like those prescribed inn the [Skype Operations Framework](https://www.skypeoperationsframework.com/) will provide possible solutions to networking design challenges along with implementation details. Most network assessments will indicate network connectivity to Office 365 can be accommodated with [minor configuration or design changes](https://aka.ms/manageo365endpoints) to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="944b1-p106">一些评估将指示网络连接到 Office 365 需要其他投资的网络组件。例如，投资 WAN 带宽或优化路由的基础结构，以支持 internet 连接到 Office 365 中。有时评估将指示受法规或性能要求方案如[Skype 业务联机媒体质量的](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)网络连接到 Office 365。投资的 internet 连接基础结构、 路由优化和专用的直接连接可能会导致这些其他要求。</span><span class="sxs-lookup"><span data-stu-id="944b1-p106">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components. For example, investments in WAN bandwidth or optimized routing infrastructure to support internet connectivity to Office 365. Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>
  
> [!NOTE]
> <span data-ttu-id="944b1-p107">Microsoft 更改 Microsoft Peering 路由域的 Azure ExpressRoute 经过审阅的方式。启动 2017 年 7 月 31，所有 Azure ExpressRoute 客户可以都启用 Microsoft Peering Azure 管理控制台中直接或通过 PowerShell 自定义。启用后 Microsoft Peering，任何客户可以创建路由筛选器以接收 BGP 路由广告 Dynamics 365 客户服务应用程序 （以前称为，CRM Online）。客户需要为 Office 365 的 Azure ExpressRoute 必须从 Microsoft 获取审阅，他们可以针对 Office 365 中创建路由筛选器之前。请联系您的 Microsoft 帐户团队，若要了解有关如何启用 Office 365 ExpressRoute 审阅请求。尝试 Office 365 中创建路由筛选器的未经授权的订阅将收到[错误消息](https://support.microsoft.com/kb/3181709)。</span><span class="sxs-lookup"><span data-stu-id="944b1-p107">Microsoft changed how the Microsoft Peering routing domain is reviewed for Azure ExpressRoute. Starting July 31st, 2017, all Azure ExpressRoute customers can enable Microsoft Peering directly from the Azure Administrative console or via PowerShell. After enabling Microsoft Peering, any customer can create route filters to receive BGP route advertisements for Dynamics 365 Customer Engagement applications (formerly known as CRM Online). Customers needing Azure ExpressRoute for Office 365 must obtain review from Microsoft before they can create route filters for Office 365. Please contact your Microsoft Account team to learn about how to request a review for enabling Office 365 ExpressRoute. Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="944b1-125">规划 Office 365 您网络评估时要考虑的要点：</span><span class="sxs-lookup"><span data-stu-id="944b1-125">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="944b1-p108">Office 365 是运行公用 internet 上安全、 可靠、 高性能服务。我们继续以增强服务的以下方面的投资。所有 Office 365 服务都可通过 internet 连接。</span><span class="sxs-lookup"><span data-stu-id="944b1-p108">Office 365 is a secure, reliable, high performance service that runs over the public internet. We continue to invest to enhance these aspects of the service. All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="944b1-p109">我们在不断优化的核心的 Office 365 方面，例如可用性，全局访问，以及 internet 的性能基于连接。例如，许多 Office 365 服务利用扩展边缘节点面向 internet 的一组。此边缘网络提供最佳的邻近度和即将通过 internet 连接的性能。</span><span class="sxs-lookup"><span data-stu-id="944b1-p109">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity. For example, many Office 365 services leverage an expanding set of internet facing edge nodes. This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="944b1-p110">在考虑使用 Office 365 的任何如 Skype 的业务 Online 语音、 视频或会议功能包括的服务时，客户必须完成的端到端网络评估并满足要求使用我们 Skype 操作框架。这些客户将有若干选项，以满足云连接，包括 ExpressRoute 的特定要求。</span><span class="sxs-lookup"><span data-stu-id="944b1-p110">When considering using Office 365 for any of the included services such as Skype for Business Online voice, video, or meeting capabilities, customers must complete an end to end network assessment and meet requirements using our Skype Operations Framework. These customers will have several options to meet specific requirements for cloud connectivity, including ExpressRoute.</span></span>

<span data-ttu-id="944b1-p111">有，请查看 Microsoft 的案例研究[的 Microsoft Office 365 的优化网络性能](https://msdn.microsoft.com/en-us/library/mt450488.aspx)。如果您是要评估 Office 365 并不确保位置开始网络评估或已发现网络设计难题，您需要帮助克服，请与您的 Microsoft 帐户团队一起工作。</span><span class="sxs-lookup"><span data-stu-id="944b1-p111">Have a look at Microsoft's case study [Optimizing network performance for Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>
  
<span data-ttu-id="944b1-p112">此外，阅读[Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)了解用于安全地管理 Office 365 流量和获取最佳性能的连接原则。本文将帮助您了解有关安全地优化 Office 365 网络连接的最新指南。</span><span class="sxs-lookup"><span data-stu-id="944b1-p112">Also, read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span>
  
<span data-ttu-id="944b1-138">这是一个简短的链接，您可以使用回来： [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="944b1-138">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="944b1-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="944b1-139">See also</span></span>

[<span data-ttu-id="944b1-140">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="944b1-140">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="944b1-141">Office 365 终结点常见问题</span><span class="sxs-lookup"><span data-stu-id="944b1-141">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[<span data-ttu-id="944b1-142">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="944b1-142">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="944b1-143">适用于 Office 365 的 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="944b1-143">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
  
[<span data-ttu-id="944b1-144">ExpressRoute for Office 365 路由</span><span class="sxs-lookup"><span data-stu-id="944b1-144">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
  
[<span data-ttu-id="944b1-145">ExpressRoute for Office 365 网络规划</span><span class="sxs-lookup"><span data-stu-id="944b1-145">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
  
[<span data-ttu-id="944b1-146">使用 Office 365 方案 (preview) 中 ExpressRoute BGP 社区 （英文）</span><span class="sxs-lookup"><span data-stu-id="944b1-146">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)
  
[<span data-ttu-id="944b1-147">媒体质量和 Skype 中的网络连接性能 for Business 联机</span><span class="sxs-lookup"><span data-stu-id="944b1-147">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="944b1-148">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="944b1-148">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="944b1-149">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="944b1-149">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
