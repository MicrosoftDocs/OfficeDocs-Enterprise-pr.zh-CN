---
title: Microsoft 365 防御拒绝服务攻击的核心原则
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Microsoft 如何在防御拒绝服务（DoS）攻击的同时，利用其核心原则、检测和缓解措施。
ms.openlocfilehash: 70e1f47e373f85bf2f4eb4d631672e293bae2bb6
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998406"
---
# <a name="core-principles-of-defense-against-denial-of-service-attacks"></a><span data-ttu-id="a6d21-103">防御拒绝服务攻击的核心原则</span><span class="sxs-lookup"><span data-stu-id="a6d21-103">Core Principles of Defense Against Denial-of-Service Attacks</span></span>

<span data-ttu-id="a6d21-104">防御基于网络的 DoS 攻击时的三个核心原则是吸收、检测和缓解。</span><span class="sxs-lookup"><span data-stu-id="a6d21-104">The three core principles when defending against network-based DoS attacks are Absorption, Detection, and Mitigation.</span></span> <span data-ttu-id="a6d21-105">在检测之前全部发生，并在缓解之前发生检测。</span><span class="sxs-lookup"><span data-stu-id="a6d21-105">Absorption happens before detection, and detection happens before mitigation.</span></span> <span data-ttu-id="a6d21-106">吸收是抵御 DoS 攻击的最佳防御能力。</span><span class="sxs-lookup"><span data-stu-id="a6d21-106">Absorption is the best defense against a DoS attack.</span></span> <span data-ttu-id="a6d21-107">如果无法检测到攻击，则无法缓解攻击。</span><span class="sxs-lookup"><span data-stu-id="a6d21-107">If the attack can't be detected, it can't be mitigated.</span></span> <span data-ttu-id="a6d21-108">但是，如果甚至无法吸收最小的 DoS 攻击，则服务的运行时间将不足以检测到攻击。</span><span class="sxs-lookup"><span data-stu-id="a6d21-108">But if even the smallest DoS attack can't be absorbed, then services aren't going to survive long enough for the attack to be detected.</span></span>

<span data-ttu-id="a6d21-109">对于大多数组织来说，购买多余的容量来吸收 DoS 攻击并不可行，因为这需要在技术和技术方面有相当大的投资。</span><span class="sxs-lookup"><span data-stu-id="a6d21-109">It is not economically feasible for most organizations to purchase excess capacity to absorb DoS attacks, as this requires a considerable investment in technology and technical skills.</span></span> <span data-ttu-id="a6d21-110">这将重点介绍使用 Microsoft 云服务的安全优势之一。</span><span class="sxs-lookup"><span data-stu-id="a6d21-110">This highlights one of the security benefits of using Microsoft cloud services.</span></span> <span data-ttu-id="a6d21-111">Microsoft 服务的巨大规模将以经济高效的方式为云客户提供强大的网络保护。</span><span class="sxs-lookup"><span data-stu-id="a6d21-111">The sheer scale of Microsoft services provides strong network protection to cloud customers in a cost-effective manner.</span></span> <span data-ttu-id="a6d21-112">甚至在规模较大的情况下，在吸收、检测和缓解之间必须有平衡。</span><span class="sxs-lookup"><span data-stu-id="a6d21-112">But even at a large scale, there must be a balance between absorption, detection, and mitigation.</span></span> <span data-ttu-id="a6d21-113">为了找出这种平衡，Microsoft 会研究攻击增长率，以估计 Microsoft 需要吸收多少内容。</span><span class="sxs-lookup"><span data-stu-id="a6d21-113">To find that balance, Microsoft studies attack growth rates to estimate how much Microsoft needs to absorb.</span></span>

<span data-ttu-id="a6d21-114">检测是一种 cat 和鼠标游戏。</span><span class="sxs-lookup"><span data-stu-id="a6d21-114">Detection is a cat-and-mouse game.</span></span> <span data-ttu-id="a6d21-115">您必须不断寻找用户受到攻击的新方法，并尝试击败您的系统。</span><span class="sxs-lookup"><span data-stu-id="a6d21-115">You must constantly look for new ways people are attack and try to defeat your systems.</span></span> <span data-ttu-id="a6d21-116">检测-> 缓解-> 检测-> 缓解等，是永久永久状态，持续无限期。</span><span class="sxs-lookup"><span data-stu-id="a6d21-116">Detect -> Mitigate -> Detect -> Mitigate, etc., is a perpetual, persistent state that continues indefinitely.</span></span>

## <a name="defending-against-dos-attacks"></a><span data-ttu-id="a6d21-117">防御 DoS 攻击</span><span class="sxs-lookup"><span data-stu-id="a6d21-117">Defending Against DoS Attacks</span></span>

<span data-ttu-id="a6d21-118">若要成功抵御 DoS 攻击，早期检测是必不可少的。</span><span class="sxs-lookup"><span data-stu-id="a6d21-118">To successfully defend against a DoS attack, early detection is essential.</span></span> <span data-ttu-id="a6d21-119">通过在系统被淹没之前检测攻击，defenders 可以执行响应计划。</span><span class="sxs-lookup"><span data-stu-id="a6d21-119">By detecting an attack before the system is overwhelmed, defenders can execute a response plan.</span></span>

<span data-ttu-id="a6d21-120">下面的公式有助于估计 DoS 攻击的影响时间：</span><span class="sxs-lookup"><span data-stu-id="a6d21-120">The following formula helps approximate the time to impact of a DoS attack:</span></span>

   <span data-ttu-id="a6d21-121">**最大容量（以字节/秒为单位）/增长速率（以字节/秒为单位） = 影响时间（秒）**</span><span class="sxs-lookup"><span data-stu-id="a6d21-121">**Maximum Capacity (in bytes/sec) / Growth Rate (in bytes/sec) = Time to Impact (in sec)**</span></span>

<span data-ttu-id="a6d21-122">如果检测时间发生在时间影响之后，则 DoS 攻击可能会成功。</span><span class="sxs-lookup"><span data-stu-id="a6d21-122">If the time-to-detection occurs after time-to-impact, it is likely the DoS attack will be successful.</span></span> <span data-ttu-id="a6d21-123">如果检测时间在影响时间之前发生，则在使用缓解策略时，攻击服务应保持在线并可访问。</span><span class="sxs-lookup"><span data-stu-id="a6d21-123">If the time-to-detection occurs before time-to-impact, the attacked services should remain online and accessible if mitigation strategies are used.</span></span> <span data-ttu-id="a6d21-124">因此，防御 DoS 攻击只需要执行以下两项操作：</span><span class="sxs-lookup"><span data-stu-id="a6d21-124">Thus, there are only two things that can be done to defend against DoS attacks:</span></span>

- <span data-ttu-id="a6d21-125">增加容量以提升最大容量的上限（进而提供更多的时间来检测攻击）;和</span><span class="sxs-lookup"><span data-stu-id="a6d21-125">Increase capacity to raise the ceiling of maximum capacity (which in turn provides more time to detect an attack); or</span></span>
- <span data-ttu-id="a6d21-126">缩短要检测的时间。</span><span class="sxs-lookup"><span data-stu-id="a6d21-126">Decrease the time to detect.</span></span>

<span data-ttu-id="a6d21-127">增加的容量有直接的财政影响。</span><span class="sxs-lookup"><span data-stu-id="a6d21-127">Increasing capacity has a direct fiscal impact.</span></span> <span data-ttu-id="a6d21-128">Microsoft 建议客户至少开发最基本的容量，以确保其可经受一定级别的 DoS 攻击。</span><span class="sxs-lookup"><span data-stu-id="a6d21-128">Microsoft recommends that customers develop at least basic absorption capacity to ensure that they can survive some level of DoS attack.</span></span> <span data-ttu-id="a6d21-129">实际的最大产量因客户而异，因为每个客户都有其自己的针对暴露、风险和财务 outlay 的阈值。</span><span class="sxs-lookup"><span data-stu-id="a6d21-129">The actual absorption capacity varies from customer to customer, as each customer has their own thresholds for exposure, risk, and financial outlay.</span></span> <span data-ttu-id="a6d21-130">出于经济方面的原因，在研究和时间缩短检测时间的方法方面的投资通常是最经济高效的防御措施。</span><span class="sxs-lookup"><span data-stu-id="a6d21-130">For economic reasons, investments in research and time for ways to decrease time-to-detection are usually the most cost-effective defense.</span></span>
