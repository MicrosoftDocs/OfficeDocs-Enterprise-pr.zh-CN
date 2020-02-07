---
title: 防御 Office 365 中的拒绝服务攻击
ms.author: robmazz
author: robmazz
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
description: 拒绝服务（DoS）攻击概述。
ms.openlocfilehash: 16378800fc7bb61b8f78e2c4c51eb7940cb45d17
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843585"
---
# <a name="defend-against-denial-of-service-attacks-in-office-365"></a><span data-ttu-id="17741-103">防御 Office 365 中的拒绝服务攻击</span><span class="sxs-lookup"><span data-stu-id="17741-103">Defend Against Denial-of-Service Attacks in Office 365</span></span>

## <a name="introduction"></a><span data-ttu-id="17741-104">简介</span><span class="sxs-lookup"><span data-stu-id="17741-104">Introduction</span></span>

<span data-ttu-id="17741-105">对于托管在超过100个数据中心的全球云基础结构中的200云服务，Microsoft 提供了一个可信赖的基础结构。</span><span class="sxs-lookup"><span data-stu-id="17741-105">Microsoft delivers a trustworthy infrastructure for more than 200 cloud services hosted in a global cloud infrastructure of more than 100 datacenters.</span></span> <span data-ttu-id="17741-106">具体包括：</span><span class="sxs-lookup"><span data-stu-id="17741-106">These include:</span></span>

- <span data-ttu-id="17741-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="17741-107">Microsoft Azure</span></span>
- <span data-ttu-id="17741-108">Microsoft Bing</span><span class="sxs-lookup"><span data-stu-id="17741-108">Microsoft Bing</span></span>
- <span data-ttu-id="17741-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="17741-109">Microsoft Dynamics 365</span></span>
- <span data-ttu-id="17741-110">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="17741-110">Microsoft Office 365</span></span>
- <span data-ttu-id="17741-111">Microsoft OneDrive</span><span class="sxs-lookup"><span data-stu-id="17741-111">Microsoft OneDrive</span></span>
- <span data-ttu-id="17741-112">Skype</span><span class="sxs-lookup"><span data-stu-id="17741-112">Skype</span></span>
- <span data-ttu-id="17741-113">Xbox Live</span><span class="sxs-lookup"><span data-stu-id="17741-113">Xbox Live</span></span>

<span data-ttu-id="17741-114">作为具有大量 Internet 状态以及提供云服务的显著 Internet 属性的全球组织，Microsoft 是黑客和其他恶意用户的一个大型、常见的目标。</span><span class="sxs-lookup"><span data-stu-id="17741-114">As a global organization with a significant Internet presence and many prominent Internet properties that provide cloud services, Microsoft is a large, common target for hackers and other malicious individuals.</span></span> <span data-ttu-id="17741-115">客户端和 Microsoft 云之间的网络通信层是恶意攻击的最大目标之一。</span><span class="sxs-lookup"><span data-stu-id="17741-115">The network communication layer between clients and the Microsoft Cloud is one of the biggest targets of malicious attacks.</span></span> <span data-ttu-id="17741-116">事实上，Microsoft 持续且永久地采用某种形式的基于网络的 cyberattack。</span><span class="sxs-lookup"><span data-stu-id="17741-116">In fact, Microsoft is continuously and persistently under some form of network-based cyberattack.</span></span> <span data-ttu-id="17741-117">根据这一点，Microsoft 使用纵深防御安全原则来保护其云服务和网络。</span><span class="sxs-lookup"><span data-stu-id="17741-117">In line with this, Microsoft uses defense-in-depth security principles to protect its cloud services and networks.</span></span> <span data-ttu-id="17741-118">如果没有可靠且持久的缓解系统防御这些攻击，Microsoft 的云服务将处于脱机状态，并且对客户不可用。</span><span class="sxs-lookup"><span data-stu-id="17741-118">Without reliable and persistent mitigation systems that defend against these attacks, Microsoft's cloud services would be offline and unavailable to customers.</span></span>

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a><span data-ttu-id="17741-119">拒绝服务攻击的定义和症状</span><span class="sxs-lookup"><span data-stu-id="17741-119">Definition and Symptoms of Denial-of-Service Attacks</span></span>

<span data-ttu-id="17741-120">攻击网络服务的一种方法是，创建多个针对服务主机的请求，以使网络和服务器严重遭受向合法用户授予服务的攻击。</span><span class="sxs-lookup"><span data-stu-id="17741-120">One way to attack network services is to create many requests against service hosts to overwhelm the network and servers to deny service to legitimate users.</span></span> <span data-ttu-id="17741-121">这称为拒绝服务（DoS）攻击。</span><span class="sxs-lookup"><span data-stu-id="17741-121">This is referred to as a denial-of-service (DoS) attack.</span></span> <span data-ttu-id="17741-122">当多个参与者、终结点和/或向量执行攻击时，它称为分布式拒绝服务（DDoS）攻击。</span><span class="sxs-lookup"><span data-stu-id="17741-122">When the attack is performed by multiple actors, endpoints, and/or vectors, it is referred to as a distributed denial-of-service (DDoS) attack.</span></span> <span data-ttu-id="17741-123">尽管方法、motives 和目标各不相同，但 DoS 和 DDoS 攻击通常都是为了防止 Internet 站点或服务正常运行，或者暂时或无限期。</span><span class="sxs-lookup"><span data-stu-id="17741-123">Although the means, motives, and targets vary, DoS and DDoS attacks generally consist of efforts to prevent an Internet site or service from functioning correctly or at all, either temporarily or indefinitely.</span></span>

<span data-ttu-id="17741-124">[美国计算机紧急就绪团队](https://www.us-cert.gov/)（美国-CERT）定义 DoS 攻击的症状，以包括：</span><span class="sxs-lookup"><span data-stu-id="17741-124">The [United States Computer Emergency Readiness Team](https://www.us-cert.gov/) (US-CERT) defines symptoms of DoS attacks to include:</span></span>

- <span data-ttu-id="17741-125">网络性能异常慢（打开文件或访问 Internet 站点时）</span><span class="sxs-lookup"><span data-stu-id="17741-125">Unusually slow network performance (when opening files or accessing Internet sites)</span></span>
- <span data-ttu-id="17741-126">网站不可用</span><span class="sxs-lookup"><span data-stu-id="17741-126">Unavailability of a Web site</span></span>
- <span data-ttu-id="17741-127">无法访问网站</span><span class="sxs-lookup"><span data-stu-id="17741-127">Inability to access a Web site</span></span>
- <span data-ttu-id="17741-128">收到的垃圾邮件大大增加</span><span class="sxs-lookup"><span data-stu-id="17741-128">Dramatic increase in received spam</span></span>
- <span data-ttu-id="17741-129">断开无线连接或有线 Internet 连接</span><span class="sxs-lookup"><span data-stu-id="17741-129">Disconnection of a wireless or wired Internet connection</span></span>
- <span data-ttu-id="17741-130">长期失去对 Web 或任何 Internet 服务的访问权限</span><span class="sxs-lookup"><span data-stu-id="17741-130">Long-term loss of access to the Web or any Internet services</span></span>

## <a name="related-topics"></a><span data-ttu-id="17741-131">相关主题</span><span class="sxs-lookup"><span data-stu-id="17741-131">Related Topics</span></span>

- [<span data-ttu-id="17741-132">防御拒绝服务攻击的核心原则</span><span class="sxs-lookup"><span data-stu-id="17741-132">Core Principles of Defense Against Denial-of-Service Attacks</span></span>](office-365-core-principles-of-defense-against-dos-attacks.md)
- [<span data-ttu-id="17741-133">Microsoft 的拒绝服务防御策略</span><span class="sxs-lookup"><span data-stu-id="17741-133">Microsoft's Denial-of-Service Defense Strategy</span></span>](office-365-microsoft-dos-defense-strategy.md)
- [<span data-ttu-id="17741-134">防御拒绝服务攻击的 Microsoft 云服务</span><span class="sxs-lookup"><span data-stu-id="17741-134">Defending Microsoft Cloud Services Against Denial-of-Service Attacks</span></span>](office-365-defending-cloud-services-against-dos-attacks.md)
