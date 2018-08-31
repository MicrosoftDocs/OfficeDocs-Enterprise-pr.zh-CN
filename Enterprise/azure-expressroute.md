---
title: 适用于 Office 365 的 Azure ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: 了解如何使用 Office 365 使用 Azure ExpressRoute 以及如何规划如果您用于 Office 365 部署 Azure ExpressRoute 都需要网络实施项目。
ms.openlocfilehash: 5a82576b541e27c70bca490ff8dfe887ee879c83
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539570"
---
# <a name="azure-expressroute-for-office-365"></a><span data-ttu-id="86f95-103">适用于 Office 365 的 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="86f95-103">Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="86f95-p101">了解如何使用 Office 365 使用 Azure ExpressRoute 以及如何规划如果您用于 Office 365 部署 Azure ExpressRoute 都需要网络实施项目。在 Azure 中运行的基础结构和平台服务将通常受益寻址网络体系结构和性能注意事项。在这些情况下，我们建议对 Azure ExpressRoute。作为像已生成 Office 365 和 Dynamics 365 通过 Internet 访问安全可靠地服务产品的软件。因此，我们只建议 ExpressRoute 在特定情况下这些应用程序。您可以阅读有关 Internet 性能和安全性以及当您可能需要 for Office 365 的 Azure ExpressRoute 考虑[网络连接到 Office 365](network-connectivity.md)一文中。</span><span class="sxs-lookup"><span data-stu-id="86f95-p101">Learn how Azure ExpressRoute is used with Office 365 and how to plan the network implementation project that will be required if you are deploying Azure ExpressRoute for use with Office 365. Infrastructure and platform services running in Azure will often benefit by addressing network architecture and performance considerations. We recommend ExpressRoute for Azure in these cases. Software as a Service offerings like Office 365 and Dynamics 365 have been built to be accessed securely and reliably via the Internet. Accordingly, we only recommend ExpressRoute for these applications in specific scenarios. You can read about Internet performance and security and when you might consider Azure ExpressRoute for Office 365 in the article [Network connectivity to Office 365](network-connectivity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="86f95-p102">启动 2017 年 7 月 31，您可以直接从 Azure 管理控制台或使用 PowerShell 启用 Microsoft Peering。启用 Microsoft Peering 后，您可以创建路由筛选器以接收特定 BGP 路由广告。您将需要授权 Office 365 创建筛选器，并可以随时创建 Dynamics 365 客户服务应用程序 （以前称为，CRM Online） 筛选器。有关获取授权，以创建 Office 365 路由筛选器的过程与您的 Microsoft 帐户团队。尝试 Office 365 中创建路由筛选器的未经授权的订阅将收到[错误消息](https://support.microsoft.com/kb/3181709)</span><span class="sxs-lookup"><span data-stu-id="86f95-p102">Starting July 31st, 2017, you can enable Microsoft Peering directly from the Azure Administrative console or using PowerShell. After enabling Microsoft Peering, you can create route filters to receive specific BGP route advertisements. You'll need authorization to create filters for Office 365 and can create Dynamics 365 Customer Engagement applications (formerly known as CRM Online) filters at any time. Talk to your Microsoft Account team about the process to obtain authorization to create Office 365 route filters. Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709)</span></span>

<span data-ttu-id="86f95-p103">为所选的 Office 365 网络流量，现在可以添加直接网络连接到 Office 365。Azure ExpressRoute 提供直接连接，可预测的性能，并附带了 Microsoft 网络组件的运行时间 SLA 的 99.95%。您仍将通过 Azure ExpressRoute 不支持的服务需要 internet 连接。</span><span class="sxs-lookup"><span data-stu-id="86f95-p103">You can now add a direct network connection to Office 365 for selected Office 365 network traffic. Azure ExpressRoute offers a direct connection, predictable performance, and comes with an uptime SLA of 99.95% for the Microsoft networking components. You'll still require an internet connection for services that aren't supported over Azure ExpressRoute.</span></span>

## <a name="planning-azure-expressroute-for-office-365"></a><span data-ttu-id="86f95-118">规划 Office 365 的 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="86f95-118">Planning Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="86f95-p104">除了 internet 连接，您可以选择通过提供可预测性和 Microsoft 网络组件 99.95%运行时间 SLA 的直接连接路由其 Office 365 网络流量的子集。Azure ExpressRoute 您提供此专用的网络连接到 Office 365 和其他 Microsoft 云服务。</span><span class="sxs-lookup"><span data-stu-id="86f95-p104">In addition to internet connectivity, you may choose to route a subset of their Office 365 network traffic over a direct connection that offers predictability and a 99.95% uptime SLA for the Microsoft networking components. Azure ExpressRoute provides you with this dedicated network connection to Office 365 and other Microsoft cloud services.</span></span>

<span data-ttu-id="86f95-p105">无论是否具有现有的 MPLS WAN，ExpressRoute 可添加到您的网络体系结构中有三种方法;通过支持的云 exchange 共同位置提供程序，以太网点对点连接提供程序，或通过 MPLS 连接提供程序。请参阅什么的[提供程序是您所在的地区中可用](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。直接 ExpressRoute 连接将启用连接到应用程序中概述[什么 Office 365 服务都包含？](azure-expressroute.md#BKMK_WhatDoIGet)下方。所有其他应用程序和服务的网络流量将继续在 internet。</span><span class="sxs-lookup"><span data-stu-id="86f95-p105">Regardless of whether you have an existing MPLS WAN, ExpressRoute can be added to your network architecture in one of three ways; through a supported cloud exchange co-location provider, an Ethernet point-to-point connection provider, or through an MPLS connection provider. See what [providers are available in your region](https://azure.microsoft.com/documentation/articles/expressroute-locations/). The direct ExpressRoute connection will enable connectivity to the applications outlined in [What Office 365 services are included?](azure-expressroute.md#BKMK_WhatDoIGet) below. Network traffic for all other applications and services will continue to traverse the internet.</span></span>

<span data-ttu-id="86f95-p106">请考虑下的高级别网络图，其中显示典型 Office 365 客户通过 internet 访问 Office 365、 Windows Update 和 TechNet 等的所有 Microsoft 应用程序以连接到 Microsoft 数据中心。客户使用类似的网络路径，无论他们是否仅当连接从本地网络或从独立的 internet 连接。</span><span class="sxs-lookup"><span data-stu-id="86f95-p106">Consider the following high level network diagram which shows a typical Office 365 customer connecting to Microsoft's datacenters over the internet for access to all Microsoft applications such as Office 365, Windows Update, and TechNet. Customers use a similar network path regardless of whether they're connecting from an on-premises network or from an independent internet connection.</span></span>

![Office 365 网络连接](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

<span data-ttu-id="86f95-p107">现在查看描述了 Office 365 客户使用的 internet 和 ExpressRoute 连接到 Office 365 的更新图表。请注意，例如公共 DNS 和内容交付网络节点某些连接仍然需要公共 internet 连接。另请注意不位于其 ExpressRoute 连接的构建通过 Internet 进行连接的客户的用户。</span><span class="sxs-lookup"><span data-stu-id="86f95-p107">Now look at the updated diagram which depicts an Office 365 customer who uses both the internet and ExpressRoute to connect to Office 365. Notice that some connections such as Public DNS and Content Delivery Network nodes still require the public internet connection. Also notice the customer's users who are not located in their ExpressRoute connected building are connecting over the Internet.</span></span>

![Office 365 连接 ExpressRoute](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

<span data-ttu-id="86f95-p108">仍需要的详细信息？了解如何[管理您的网络流量与 Office 365 的 Azure ExpressRoute](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)并了解如何[配置 Office 365 的 Azure ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。我们还录制可帮助更全面地介绍的概念第 9 频道上一个 10 部分[Azure ExpressRoute 有关 Office 365 培训](https://channel9.msdn.com/series/aer)系列。</span><span class="sxs-lookup"><span data-stu-id="86f95-p108">Still want more information? Learn how to [manage your network traffic with Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) and learn how to [configure Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). We've also recorded a 10 part [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to help explain the concepts more thoroughly.</span></span>

<span data-ttu-id="86f95-135">([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="86f95-135">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="what-office-365-services-are-included"></a><span data-ttu-id="86f95-136">包含哪些 Office 365 服务？</span><span class="sxs-lookup"><span data-stu-id="86f95-136">What Office 365 services are included?</span></span>
<span data-ttu-id="86f95-137"><a name="BKMK_WhatDoIGet"> </a></span><span class="sxs-lookup"><span data-stu-id="86f95-137"></span></span>

<span data-ttu-id="86f95-p109">下表列出通过 ExpressRoute 支持的 Office 365 服务。请查看[Office 365 终结点文章](https://aka.ms/o365endpoints)了解这些应用程序的网络请求需要 internet 连接。</span><span class="sxs-lookup"><span data-stu-id="86f95-p109">The following table lists the Office 365 services that are supported over ExpressRoute. Please review the [Office 365 endpoints article](https://aka.ms/o365endpoints) to understand which network requests for these applications require internet connectivity.</span></span>

|<span data-ttu-id="86f95-140">**包括的应用程序**</span><span class="sxs-lookup"><span data-stu-id="86f95-140">**Applications included**</span></span>|
|:-----|
|<span data-ttu-id="86f95-141">Exchange Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-141">Exchange Online<sup>1</sup></span></span> <br/> <span data-ttu-id="86f95-142">Exchange Online Protection<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-142">Exchange Online Protection<sup>1</sup></span></span> <br/> <span data-ttu-id="86f95-143">深入<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-143">Delve<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="86f95-144">Skype 业务联机<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-144">Skype for Business Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="86f95-145">SharePoint Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-145">SharePoint Online<sup>1</sup></span></span> <br/> <span data-ttu-id="86f95-146">OneDrive for Business<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-146">OneDrive for Business<sup>1</sup></span></span> <br/> <span data-ttu-id="86f95-147">Project Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-147">Project Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="86f95-148">门户和共享的<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-148">Portal and shared<sup>1</sup></span></span> <br/> <span data-ttu-id="86f95-149">Azure Active Directory<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-149">Azure Active Directory<sup>1</sup></span></span> <br/> <span data-ttu-id="86f95-150">AAD 连接<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-150">AAD Connect<sup>1</sup></span></span> <br/> <span data-ttu-id="86f95-151">Office Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86f95-151">Office Online<sup>1</sup></span></span> <br/> |

<span data-ttu-id="86f95-152"><sup>1</sup>所有这些应用程序具有通过 ExpressRoute 不支持的 internet 连接要求，请参阅[Office 365 终结点文章](https://aka.ms/o365endpoints)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="86f95-152"><sup>1</sup>Each of these applications have internet connectivity requirements not supported over ExpressRoute, see the [Office 365 endpoints article](https://aka.ms/o365endpoints) for more information.</span></span>

<span data-ttu-id="86f95-153">不包含在 Office 365 ExpressRoute 服务是 Office 365 ProPlus 客户端下载、 本地标识提供程序注册，和在中国 （由 21 Vianet） 的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="86f95-153">The services that aren't included with ExpressRoute for Office 365 are Office 365 ProPlus client downloads, On-premises Identity Provider Sign-In, and Office 365 (operated by 21 Vianet) service in China.</span></span>

<span data-ttu-id="86f95-154">([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="86f95-154">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="86f95-155">实现 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="86f95-155">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="86f95-p110">实现 ExpressRoute 需要网络和应用程序所有者的参与，需要仔细规划以确定新[网络路由体系结构](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、 带宽要求，将安全实施，高可用性等等。若要实现 ExpressRoute，您将需要：</span><span class="sxs-lookup"><span data-stu-id="86f95-p110">Implementing ExpressRoute requires the involvement of network and application owners and requires careful planning to determine the new [network routing architecture](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bandwidth requirements, where security will be implemented, high availability, and so on. To implement ExpressRoute, you'll need to:</span></span>

1. <span data-ttu-id="86f95-p111">完全了解 ExpressRoute 满足 Office 365 连接计划中的需求。了解哪些应用程序将使用的 internet 或 ExpressRoute 和完全规划网络容量、 安全性和高可用性所需的 Office 365 中使用的 internet 和 ExpressRoute 上下文中通信。</span><span class="sxs-lookup"><span data-stu-id="86f95-p111">Fully understand the need ExpressRoute satisfies in your Office 365 connectivity planning. Understand what applications will use the internet or ExpressRoute and fully plan your network capacity, security, and high availability needs in the context of using both the internet and ExpressRoute for Office 365 traffic.</span></span>

2. <span data-ttu-id="86f95-160">确定出口和对等位置的 internet 和 ExpressRoute 流量<sup>1</sup>。</span><span class="sxs-lookup"><span data-stu-id="86f95-160">Determine the egress and peering locations for both internet and ExpressRoute traffic<sup>1</sup>.</span></span>

3. <span data-ttu-id="86f95-161">确定在 internet 和 ExpressRoute 连接上所需的容量。</span><span class="sxs-lookup"><span data-stu-id="86f95-161">Determine the capacity required on the internet and ExpressRoute connections.</span></span>

4. <span data-ttu-id="86f95-162">用于实现安全性和其他标准外围控件<sup>1</sup>就地具有计划。</span><span class="sxs-lookup"><span data-stu-id="86f95-162">Have a plan in place for implementing security and other standard perimeter controls<sup>1</sup>.</span></span>

5. <span data-ttu-id="86f95-163">具有有效的 Microsoft Azure 帐户以订阅 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="86f95-163">Have a valid Microsoft Azure account to subscribe to ExpressRoute.</span></span>

6. <span data-ttu-id="86f95-p112">选择连接模型和[批准提供程序](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。请记住，客户可以选择多个连接模型或合作伙伴和合作伙伴不需要与您现有的网络提供程序。</span><span class="sxs-lookup"><span data-stu-id="86f95-p112">Select a connectivity model and an [approved provider](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Keep in mind, customers can select multiple connectivity models or partners and the partner doesn't need to be the same as your existing network provider.</span></span>

7. <span data-ttu-id="86f95-166">验证前将流量定向到 ExpressRoute 的部署。</span><span class="sxs-lookup"><span data-stu-id="86f95-166">Validate deployment prior to directing traffic to ExpressRoute.</span></span>

8. <span data-ttu-id="86f95-167">（可选）[实现 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)和评估区域扩展。</span><span class="sxs-lookup"><span data-stu-id="86f95-167">Optionally [implement QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) and evaluate regional expansion.</span></span>

<span data-ttu-id="86f95-p113"><sup>1</sup>重要性能注意事项。此处决策可以显著影响这很关键的应用程序，如 for Business 的 Skype 的延迟。</span><span class="sxs-lookup"><span data-stu-id="86f95-p113"><sup>1</sup>Important performance considerations. Decisions here can dramatically impact latency which is a critical for applications such as Skype for Business.</span></span>

<span data-ttu-id="86f95-170">对于其他参考，使用我们除了[ExpressRoute 文档](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)的[传送指南](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)。</span><span class="sxs-lookup"><span data-stu-id="86f95-170">For additional references, use our [routing guide](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) in addition to the [ExpressRoute documentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).</span></span>

<span data-ttu-id="86f95-p114">要为 Office 365 购买 ExpressRoute，您将需要使用一个或多个[批准提供程序](https://azure.microsoft.com/documentation/articles/expressroute-locations/)设置的所需的数量和大小电路使用 ExpressRoute Premium 订阅。没有要从 Office 365 购买附加许可证。</span><span class="sxs-lookup"><span data-stu-id="86f95-p114">To purchase ExpressRoute for Office 365, you'll need to work with one or more [approved providers](https://azure.microsoft.com/documentation/articles/expressroute-locations/) to provision the desired number and size circuits with an ExpressRoute Premium subscription. There are no additional licenses to purchase from Office 365.</span></span>

<span data-ttu-id="86f95-173">这是一个简短的链接，您可以使用回来：[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span><span class="sxs-lookup"><span data-stu-id="86f95-173">Here's a short link you can use to come back: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span></span>

<span data-ttu-id="86f95-174">为注册[Office 365 ExpressRoute](https://aka.ms/ert)准备？</span><span class="sxs-lookup"><span data-stu-id="86f95-174">Ready to sign-up for [ExpressRoute for Office 365](https://aka.ms/ert)?</span></span>

<span data-ttu-id="86f95-175">([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="86f95-175">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="related-topics"></a><span data-ttu-id="86f95-176">相关主题</span><span class="sxs-lookup"><span data-stu-id="86f95-176">Related Topics</span></span>
<span data-ttu-id="86f95-177"><a name="BKMK_End"> </a></span><span class="sxs-lookup"><span data-stu-id="86f95-177"></span></span>

[<span data-ttu-id="86f95-178">与 Office 365 的网络连接</span><span class="sxs-lookup"><span data-stu-id="86f95-178">Network connectivity to Office 365</span></span>](network-connectivity.md)

[<span data-ttu-id="86f95-179">管理 ExpressRoute for Office 365 连接</span><span class="sxs-lookup"><span data-stu-id="86f95-179">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)

[<span data-ttu-id="86f95-180">ExpressRoute for Office 365 路由</span><span class="sxs-lookup"><span data-stu-id="86f95-180">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)

[<span data-ttu-id="86f95-181">ExpressRoute for Office 365 网络规划</span><span class="sxs-lookup"><span data-stu-id="86f95-181">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)

[<span data-ttu-id="86f95-182">实现 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="86f95-182">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)

[<span data-ttu-id="86f95-183">使用 Office 365 方案 (preview) 中 ExpressRoute BGP 社区 （英文）</span><span class="sxs-lookup"><span data-stu-id="86f95-183">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)

[<span data-ttu-id="86f95-184">媒体质量和 Skype 中的网络连接性能 for Business 联机</span><span class="sxs-lookup"><span data-stu-id="86f95-184">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[<span data-ttu-id="86f95-185">使用基线和性能历史记录优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="86f95-185">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="86f95-186">Office 365 的性能疑难解答计划</span><span class="sxs-lookup"><span data-stu-id="86f95-186">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="86f95-187">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="86f95-187">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[<span data-ttu-id="86f95-188">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="86f95-188">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
