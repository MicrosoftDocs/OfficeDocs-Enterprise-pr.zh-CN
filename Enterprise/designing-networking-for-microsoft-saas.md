---
title: 为 Microsoft SaaS 设计网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 摘要：了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。
ms.openlocfilehash: 695e3255bf1afcb5314985caccb15ead410d93f6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067768"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="ad5f1-103">为 Microsoft SaaS 设计网络</span><span class="sxs-lookup"><span data-stu-id="ad5f1-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="ad5f1-104">**摘要：** 了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="ad5f1-105">若要为 Microsoft SaaS 服务优化网络，需要将内部和边缘设备配置为把各种类别的流量路由至 Microsoft SaaS 服务。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="ad5f1-106">为 Microsoft SaaS 服务准备网络的步骤</span><span class="sxs-lookup"><span data-stu-id="ad5f1-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="ad5f1-107">按照这些步骤执行操作，为 Microsoft SaaS 服务优化你的网络：</span><span class="sxs-lookup"><span data-stu-id="ad5f1-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="ad5f1-108">完成 [Microsoft 云连接的常见元素](common-elements-of-microsoft-cloud-connectivity.md)中的**为 Microsoft 云服务准备网络的步骤**部分。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="ad5f1-109">向每个办公室添加 Internet 连接。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="ad5f1-110">确保所有 Internet 连接的 Isp 都使用具有本地 IP 地址的 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="ad5f1-111">检查您的网络回流, 中间目标 (如基于云的安全服务), 并在可能的情况下将其删除。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="ad5f1-112">将您的边缘设备配置为绕过优化和允许 Microsoft SaaS 流量类别的处理。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="ad5f1-113">优化到 Microsoft SaaS 服务的流量</span><span class="sxs-lookup"><span data-stu-id="ad5f1-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="ad5f1-114">Microsoft SaaS 流量有三种类别:</span><span class="sxs-lookup"><span data-stu-id="ad5f1-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="ad5f1-115">优化</span><span class="sxs-lookup"><span data-stu-id="ad5f1-115">Optimize</span></span>

  <span data-ttu-id="ad5f1-116">与每个 Microsoft SaaS 服务的连接所必需, 表示 Microsoft SaaS 带宽、连接数和数据量的 75%。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="ad5f1-117">允许</span><span class="sxs-lookup"><span data-stu-id="ad5f1-117">Allow</span></span>

  <span data-ttu-id="ad5f1-118">需要连接到特定的 Microsoft SaaS 服务和功能, 但不像 "优化" 类别中的那样对网络性能和延迟敏感。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="ad5f1-119">默认</span><span class="sxs-lookup"><span data-stu-id="ad5f1-119">Default</span></span>

  <span data-ttu-id="ad5f1-120">表示不需要进行任何优化的 Microsoft SaaS 服务和依赖项。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-120">Represent Microsoft SaaS services and dependencies that do not require any optimization.</span></span> <span data-ttu-id="ad5f1-121">您可以处理默认类别通信, 如正常的 Internet 流量。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-121">You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="ad5f1-122">**图 1: 适用于所有办公室的 Microsoft SaaS 流量的建议配置**</span><span class="sxs-lookup"><span data-stu-id="ad5f1-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![图 1: 适用于所有办公室的 Microsoft SaaS 流量的建议配置](media/Network-Poster/SaaS1.png)

<span data-ttu-id="ad5f1-124">图1显示了所有办事处的推荐配置, 包括分支机构和区域或中心, 其中:</span><span class="sxs-lookup"><span data-stu-id="ad5f1-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="ad5f1-125">**默认**类别和常规 Internet 流量路由到具有代理服务器和其他边缘设备的办公室, 以针对基于 Internet 的安全风险提供保护。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="ad5f1-126">**优化**并**允许**将类别流量直接转发到离包含连接用户的 office 最近的 Microsoft 网络前端的边缘, 而不是代理服务器和其他边缘设备。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="ad5f1-127">分支机构中软件定义的广域网络 (SD-WAN) 设备可单独进行通信, 以便:</span><span class="sxs-lookup"><span data-stu-id="ad5f1-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="ad5f1-128">**默认**类别和常规 Internet 流量通过 WAN 骨干转到中央或区域办公室。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="ad5f1-129">**优化**和**允许**类别通信转到提供本地 Internet 连接的 ISP。</span><span class="sxs-lookup"><span data-stu-id="ad5f1-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="ad5f1-130">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="ad5f1-130">For more information, see:</span></span>
  
- [<span data-ttu-id="ad5f1-131">网络连接原则</span><span class="sxs-lookup"><span data-stu-id="ad5f1-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="ad5f1-132">Office 365 的网络和迁移规划</span><span class="sxs-lookup"><span data-stu-id="ad5f1-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="ad5f1-133">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ad5f1-133">Next step</span></span>

[<span data-ttu-id="ad5f1-134">为 Microsoft Azure PaaS 设计网络</span><span class="sxs-lookup"><span data-stu-id="ad5f1-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="ad5f1-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad5f1-135">See also</span></span>

[<span data-ttu-id="ad5f1-136">面向企业架构师的 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="ad5f1-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="ad5f1-137">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="ad5f1-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

