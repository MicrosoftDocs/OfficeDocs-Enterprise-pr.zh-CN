---
title: 容量规划和负载测试 SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: 本文介绍如何在不执行传统负载测试的情况下部署到 SharePoint Online，因为这是不允许的。
ms.openlocfilehash: d082dbd93f9724080118f5e387713dc374e50643
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004605"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="93e11-103">容量规划和负载测试 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="93e11-103">Capacity planning and load testing SharePoint Online</span></span>
<span data-ttu-id="93e11-104">本文介绍了如何在不进行传统负载测试的情况下部署到 SharePoint Online，因为 SharePoint Online 不允许进行负载测试。</span><span class="sxs-lookup"><span data-stu-id="93e11-104">This article describes how you can deploy to SharePoint Online without traditional load testing, since load-testing is not permitted on SharePoint Online.</span></span> <span data-ttu-id="93e11-105">SharePoint Online 是云服务，服务中负载的负载功能、运行状况和总体平衡由 Microsoft 进行管理。</span><span class="sxs-lookup"><span data-stu-id="93e11-105">SharePoint Online is a cloud service and the load capabilities, health and overall balance of load in the service is managed by Microsoft.</span></span>
  
<span data-ttu-id="93e11-106">确保网站启动成功的最佳方法是遵循在[规划门户启动](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)时的规划中突出显示的基本原则、做法和建议。</span><span class="sxs-lookup"><span data-stu-id="93e11-106">The best approach to ensuring the success of launching your site is to follow basic principles, practices and recommendations which are highlighted in the [plan your portal launch roll-out](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out).</span></span>

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a><span data-ttu-id="93e11-107">SharePoint Online 执行容量规划的概述</span><span class="sxs-lookup"><span data-stu-id="93e11-107">Overview of how SharePoint Online performs Capacity planning</span></span> 
<span data-ttu-id="93e11-108">在本地部署中，SharePoint Online 的主要好处之一是云的弹性，以及针对分布式区域中用户的优化。</span><span class="sxs-lookup"><span data-stu-id="93e11-108">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud as well as optimizations for users in distributed regions.</span></span> <span data-ttu-id="93e11-109">我们将大型环境设置为每天为数百万个用户提供服务，因此我们必须通过平衡和扩展服务器场有效地处理容量。</span><span class="sxs-lookup"><span data-stu-id="93e11-109">Our large scale environment is set up to service millions of users on a daily basis, so it is important that we handle capacity effectively by balancing and expanding farms.</span></span>
  
<span data-ttu-id="93e11-110">虽然在任何一个服务器场中的任何一个租户的增长通常不可预测，但累积的请求总数可随时间推移而预测。</span><span class="sxs-lookup"><span data-stu-id="93e11-110">While the growth is often unpredictable for any one tenant in any one farm, the aggregated sum of requests is predictable over time.</span></span> <span data-ttu-id="93e11-111">通过确定 SharePoint Online 中的增长趋势，我们可以规划未来的扩展。</span><span class="sxs-lookup"><span data-stu-id="93e11-111">By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="93e11-112">为了高效地使用容量并处理意外增长，在任何服务器场中，我们都具有跟踪和监控服务的各种元素的自动化。</span><span class="sxs-lookup"><span data-stu-id="93e11-112">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks and monitors various elements of the service.</span></span> <span data-ttu-id="93e11-113">使用多个指标，其中一个主要指标是 CPU 负载，可用作扩展前端服务器的信号。</span><span class="sxs-lookup"><span data-stu-id="93e11-113">Multiple metrics are utilized, with one of the main ones being CPU load, which is used as a signal to scale-up front end servers.</span></span> <span data-ttu-id="93e11-114">此外，我们还建议采用[分阶段/浪潮方法](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)，因为 SQL 环境将根据时间的负载和增长进行扩展，并且按照这些阶段和波形可实现该负载和增长的正确分布。</span><span class="sxs-lookup"><span data-stu-id="93e11-114">Additionally to this we recommend a [phased / wave approach](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out), as SQL environments will scale according to load and growth over time, and following the phases and waves allows for the correct distribution of that load and growth.</span></span> 

<span data-ttu-id="93e11-115">容量不仅仅是在不断添加更多硬件，还与管理和控制容量以确保它为有效的加载请求提供服务相关。</span><span class="sxs-lookup"><span data-stu-id="93e11-115">Capacity is more than just about adding more hardware on a continuous basis but it also pertains to managing and controlling that capacity to ensure it is servicing valid load requests.</span></span> <span data-ttu-id="93e11-116">我们建议客户遵循建议的指南，以确保他们获得最佳体验。</span><span class="sxs-lookup"><span data-stu-id="93e11-116">We recommend that customers follow the recommended guidance to ensure they have the best experience.</span></span> <span data-ttu-id="93e11-117">这也意味着我们已经实施了限制模式和控制，以确保我们不允许在服务中执行 "滥用" 的行为。</span><span class="sxs-lookup"><span data-stu-id="93e11-117">It also means that we have throttling patterns and controls in place to ensure we do not allow "abusive" behavior in the service.</span></span> <span data-ttu-id="93e11-118">尽管并非所有 "错误" 行为是特意的，但我们确实必须确保我们限制该行为的影响。</span><span class="sxs-lookup"><span data-stu-id="93e11-118">Whilst not all "bad" behavior is intentional, we do have to ensure that we limit the effect of that behavior.</span></span> <span data-ttu-id="93e11-119">有关限制以及如何避免此限制的详细信息，请查看[如何避免受限制的指南](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)文章。</span><span class="sxs-lookup"><span data-stu-id="93e11-119">For further information on throttling and how to avoid it, review the [how to avoid being throttled guidance](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) article.</span></span>

## <a name="why-you-cannot-load-test-sharepoint-online"></a><span data-ttu-id="93e11-120">为什么您无法加载测试 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="93e11-120">Why you cannot load test SharePoint Online</span></span>
<span data-ttu-id="93e11-121">在本地环境中，负载测试用于验证扩展假设并最终发现服务器场的中断点;通过将其与负载进行饱和。</span><span class="sxs-lookup"><span data-stu-id="93e11-121">With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load.</span></span> 

<span data-ttu-id="93e11-122">通过 SharePoint Online，我们需要执行不同的操作，因为扩展相对于特定试探法进行了相对流动和调整、限制和控件负载。</span><span class="sxs-lookup"><span data-stu-id="93e11-122">With SharePoint Online we need to do things differently because the scale is relatively fluid and adjusts, throttles and controls load, based on certain heuristics.</span></span> <span data-ttu-id="93e11-123">作为大型规模的多租户环境，我们必须保护同一服务器场中的所有租户，因此我们将自动限制任何负载测试。</span><span class="sxs-lookup"><span data-stu-id="93e11-123">Being such a large scale multi-tenant environment, we must protect all tenants in the same farm, so we will automatically throttle any load tests.</span></span> <span data-ttu-id="93e11-124">如果您在尝试加载测试时除了受到限制之外，您还会收到 disappointing 和潜在的误导结果，因为您在测试期间测试的服务器场可能在测试时段内或在测试之后的几小时内发生扩展更改，因为在进行扩展和服务器场平衡操作的过程中将会不断进行。</span><span class="sxs-lookup"><span data-stu-id="93e11-124">If you do however attempt to load test, besides being throttled, you will receive disappointing and potentially misleading results because the farm you tested today will probably have had scale changes during the testing window or within hours after testing, as scale and farm balancing actions are performed on an on-going basis.</span></span>

<span data-ttu-id="93e11-125">而不是尝试将测试 SharePoint 作为服务进行加载，而是侧重于遵循建议的做法，并遵循[创建、启动和维护正常的门户](https://go.microsoft.com/fwlink/?linkid=2105838)指南。</span><span class="sxs-lookup"><span data-stu-id="93e11-125">Instead of trying to load test SharePoint as a service, rather focus on following the recommended practices and follow the [Creating, launching and maintaining a healthy portal](https://go.microsoft.com/fwlink/?linkid=2105838) guidance.</span></span>
