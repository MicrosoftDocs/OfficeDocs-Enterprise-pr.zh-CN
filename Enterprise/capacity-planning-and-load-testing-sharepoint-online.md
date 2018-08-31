---
title: 容量规划和负载测试 SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: 本文介绍如何部署到 SharePoint Online 不执行传统负载测试，因为它不允许。
ms.openlocfilehash: 06649942f20dc18abfcae0e56df7e3ea56ed9165
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539805"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="17643-103">容量规划和负载测试 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="17643-103">Capacity planning and load testing SharePoint Online</span></span>

<span data-ttu-id="17643-104">本文介绍如何部署到 SharePoint Online 不执行传统负载测试，因为它不允许。</span><span class="sxs-lookup"><span data-stu-id="17643-104">This article describes how you can deploy to SharePoint Online without performing traditional load testing since it is not permitted.</span></span>
  
<span data-ttu-id="17643-105">尽管活动的负载测试在 SharePoint Online 是强烈建议您不要，还有其他的方法可以确保网站不会产生很差的用户体验时启动网站。</span><span class="sxs-lookup"><span data-stu-id="17643-105">Although active load testing on SharePoint Online is strongly discouraged, there are other ways you can make sure that a site will not produce a poor user experience when you launch the site.</span></span> 
  
<span data-ttu-id="17643-p101">使用 SharePoint Online，您不需要进行容量规划，如这是为您提供我们服务的一部分。内部部署环境与负载测试用于验证刻度假设和最终查找服务器场; 损坏点通过使其饱和负载。使用 SharePoint Online 我们需要以不同的方式执行操作。正在多租户环境，我们必须保护所有租户中同一个服务器场，因此我们将自动限制任何负载测试。这意味着您将收到失望和可能误导性的结果如果您尝试加载测试您的环境。</span><span class="sxs-lookup"><span data-stu-id="17643-p101">With SharePoint Online you don't have to do capacity planning, as this is done for you as part of our service offering. With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load. With SharePoint Online we need to do things differently. Being a multi-tenant environment, we have to protect all tenants in the same farm, so we will automatically throttle any load tests. This means you will receive disappointing and potentially misleading results if you attempt to load test your environment.</span></span>
  
<span data-ttu-id="17643-p102">通过内部部署 SharePoint online 的主要优势之一是在云中的弹性。我们大型环境设置到服务数百万个用户每天因此很重要，我们通过以下方式处理容量有效地自动扩展服务器场时需要。本文介绍了我们如何规划容量增长和规模在位置。本文还介绍为您要使用的不涉及负载测试的方法。</span><span class="sxs-lookup"><span data-stu-id="17643-p102">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud. Our large scale environment is set up to service millions of users on a daily basis so it is important that we handle capacity effectively by automatically expanding farms, as and when needed. This article explains how we plan for capacity growth and scale out in place. The article also covers approaches for you to use that don't involve load testing.</span></span>
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a><span data-ttu-id="17643-115">Office 365 如何预测负载和扩展容量</span><span class="sxs-lookup"><span data-stu-id="17643-115">How Office 365 predicts load and expands capacity</span></span>

<span data-ttu-id="17643-116">SharePoint Online 服务器容量管理工作是通过两种方法：</span><span class="sxs-lookup"><span data-stu-id="17643-116">SharePoint Online server capacity management work is done through two methods:</span></span>
  
- <span data-ttu-id="17643-117">容量预测</span><span class="sxs-lookup"><span data-stu-id="17643-117">Capacity forecasting</span></span>
    
- <span data-ttu-id="17643-118">单个服务器场上的负载平衡</span><span class="sxs-lookup"><span data-stu-id="17643-118">Load-balancing on single server farms</span></span>
    
<span data-ttu-id="17643-p103">与内部部署环境的预测 SharePoint Online 中的容量规划不同，我们将能够编译统计信息和图表任何给定的服务器组中的潜在要求。聚合请求可能类似于请求 （其中区域是 SharePoint 服务器场的一组） 的区域中增长行图所示：</span><span class="sxs-lookup"><span data-stu-id="17643-p103">Unlike planning for an on-premises environment, for capacity forecasting in SharePoint Online, we are able to compile statistics and graph potential requirements in any given server group. The aggregate demand might look something like the Requests in zone (where a zone is a group of SharePoint farms) growth line in the image below:</span></span>
  
![显示预测容量的图表：预测](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
<span data-ttu-id="17643-p104">任何一个服务器场处于无法预料增长时, 是预测的聚合的区域中的请求总数。通过识别 SharePoint Online 中的增长趋势，我们可以计划以供将来扩展。</span><span class="sxs-lookup"><span data-stu-id="17643-p104">While the growth is unpredictable in any one farm, the aggregated sum of requests in a zone is predictable. By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="17643-p105">才能有效地使用容量和处理意外增长，任何服务器场，我们已跟踪前端负载并就地，调整，在需要时的自动化。我们使用如信号来扩展提前结束主要指标是 CPU 负载。我们的目标是使峰值 CPU 负载下 40%。这是为了有足够的缓冲区可承受意外的高峰。作为负载方法 40%的稳定状态，我们可以向服务器场添加前端。</span><span class="sxs-lookup"><span data-stu-id="17643-p105">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks front-end load and scales up in place, when needed. The main metric we use as a signal to scale up front ends is CPU load. Our goal is to keep peak CPU load under 40%. This is in order to have enough buffer to absorb unexpected spikes. As load approaches 40% in steady state, we add front ends to farms.</span></span>
  
![显示预测容量的图表：管理场](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
<span data-ttu-id="17643-130">其他服务器可以快速添加到服务器场，使用那些之前添加到通过预测的使用情况的区域。</span><span class="sxs-lookup"><span data-stu-id="17643-130">Additional servers can be quickly added to a farm, using those which have been previously added to the zone through the usage forecast.</span></span> 
  
## <a name="how-do-i-plan-for-a-site-launch"></a><span data-ttu-id="17643-131">如何规划网站启动？</span><span class="sxs-lookup"><span data-stu-id="17643-131">How do I plan for a site launch?</span></span>

<span data-ttu-id="17643-p106">您应产生预期的服务器场在其启动新网站将自动受监控，以便添加新的前端服务器，上面所述。因此，我们不需要新网站上市的任何通知。</span><span class="sxs-lookup"><span data-stu-id="17643-p106">You should expect that the farm on which your new site launches will automatically be monitored so that new front-end servers are added, as described above. For this reason, we don't need any notification for your new site launch.</span></span>
  
<span data-ttu-id="17643-134">关注 SharePoint Online 上的单个页面的其他最佳实践不太甚至 100,000 个用户对新网站启动将向服务器场产生任何影响。</span><span class="sxs-lookup"><span data-stu-id="17643-134">Following other best practices for a single page on SharePoint Online it is unlikely that a new site launch to even 100,000 users will have any impact to the farm.</span></span>
  
<span data-ttu-id="17643-p107">有几个策略来规划新的 SharePoint Online 网站的版本。下图中所示，通常是大大高于那些实际使用该网站的用户的邀请数量。此图显示了有关如何推出发行版的策略。此方法不仅有助于性能加载，而且还可帮助确定如何提高 SharePoint 网站的用户的大多数查看它之前。</span><span class="sxs-lookup"><span data-stu-id="17643-p107">There are a few strategies to plan for a release of a new SharePoint Online site. As shown in the following image, often the amount of users that are invited is significantly higher than those that actually use the site. This image shows a strategy about how to roll out a release. This method not only helps with performance loading but also can help identify ways to improve the SharePoint site before the large majority of the users see it.</span></span>
  
![显示受邀并且处于活动状态的用户的图形](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="17643-p108">在试验阶段，最好获得用户组织信任和知道将参与的反馈。这样就可以衡量系统的使用方式，以及如何执行它。</span><span class="sxs-lookup"><span data-stu-id="17643-p108">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged. This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="17643-p109">此后，开始推广随后; 中的所有用户获取反馈和定期查看性能。其缓慢简介系统和做出改进，如系统获取更多使用的优点。这样，我们能够随着网站分发给越来越多的用户负载增加到做出响应。</span><span class="sxs-lookup"><span data-stu-id="17643-p109">After this, begins a roll out to all users in waves; getting feedback and reviewing the performance regularly. This has the advantage of slowly introducing the system and making improvements as the system gets more use. This also allows us to react to the increased load as the site is rolled out to more and more users.</span></span>
  
<span data-ttu-id="17643-p110">最后，同时禁止负载测试，客户可能需要以设置到度量值的可用性与延迟服务定期 ping。这将确定其网站的基线。但是，这些必须保持低频率，以避免限制前面所述的问题。</span><span class="sxs-lookup"><span data-stu-id="17643-p110">Finally, while load tests are prohibited, customers may want to set up periodical pings to the service to measure availability and latency. This will identify a baseline for their site. However, these must be kept to low frequency to avoid throttling issues previously described.</span></span>
  

