---
title: 为 Microsoft SaaS 设计网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 摘要：了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872263"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="ab8ab-103">为 Microsoft SaaS 设计网络</span><span class="sxs-lookup"><span data-stu-id="ab8ab-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="ab8ab-104">**摘要：** 了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="ab8ab-105">优化您的 Microsoft saas 与服务的网络要求配置内部和边缘设备，可将不同类别的流量路由到 Microsoft SaaS 服务。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="ab8ab-106">为 Microsoft SaaS 服务准备网络的步骤</span><span class="sxs-lookup"><span data-stu-id="ab8ab-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="ab8ab-107">按照这些步骤执行操作，为 Microsoft SaaS 服务优化你的网络：</span><span class="sxs-lookup"><span data-stu-id="ab8ab-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="ab8ab-108">完成 [Microsoft 云连接的常见元素](common-elements-of-microsoft-cloud-connectivity.md)中的**为 Microsoft 云服务准备网络的步骤**部分。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="ab8ab-109">添加到每个办事处 Internet 连接。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="ab8ab-110">确保所有 Internet 连接的 Isp 与本地 IP 地址使用 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="ab8ab-111">检查您的网络 hairpins、 基于云的安全服务，如中间目标，并将其删除如果可能。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="ab8ab-112">配置边缘设备以绕过优化的处理，允许类别的 Microsoft SaaS 流量。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="ab8ab-113">优化与 Microsoft 的 saas 与服务的流量</span><span class="sxs-lookup"><span data-stu-id="ab8ab-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="ab8ab-114">有三种类别的 Microsoft SaaS 流量：</span><span class="sxs-lookup"><span data-stu-id="ab8ab-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="ab8ab-115">优化</span><span class="sxs-lookup"><span data-stu-id="ab8ab-115">Optimize</span></span>

  <span data-ttu-id="ab8ab-116">所需的连接到每个 Microsoft SaaS 服务和表示超过 75%的 Microsoft SaaS 带宽、 连接和数据量。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="ab8ab-117">允许</span><span class="sxs-lookup"><span data-stu-id="ab8ab-117">Allow</span></span>

  <span data-ttu-id="ab8ab-118">所需的连接到特定 Microsoft SaaS services，和功能，但不为敏感网络性能和优化类别中的与延迟。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="ab8ab-119">默认</span><span class="sxs-lookup"><span data-stu-id="ab8ab-119">Default</span></span>

  <span data-ttu-id="ab8ab-p101">表示 Microsoft SaaS 服务和不需要任何优化的依赖关系。可以将像普通 Internet 通信的默认类别通信。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-p101">Represent Microsoft SaaS services and dependencies that do not require any optimization. You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="ab8ab-122">**图 1： 建议使用的所有办事处的 Microsoft SaaS 流量的配置**</span><span class="sxs-lookup"><span data-stu-id="ab8ab-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![图 1： 建议使用的所有办事处的 Microsoft SaaS 流量的配置](media/Network-Poster/SaaS1.png)

<span data-ttu-id="ab8ab-124">图 1 显示了所有办公室，包括分支机构和区域或管理中心的在其中的建议的配置：</span><span class="sxs-lookup"><span data-stu-id="ab8ab-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="ab8ab-125">**默认**类别和常规 Internet 流量路由到代理服务器和其他边缘设备来提供针对基于 Internet 的安全风险保护的办公室。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="ab8ab-126">**优化**和**允许**类别通信转发到最靠近 office 包含连接的用户，绕过代理服务器和其他边缘设备的 Microsoft 网络前端边缘直接。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="ab8ab-127">分支机构中的软件定义广域网 (SD WAN) 的网络设备将流量分开，以便：</span><span class="sxs-lookup"><span data-stu-id="ab8ab-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="ab8ab-128">**默认**类别和常规前往通过 WAN 主干中央或区域 office Internet 通信。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="ab8ab-129">**优化**和**允许**类别流量转到 ISP 提供本地 Internet 连接。</span><span class="sxs-lookup"><span data-stu-id="ab8ab-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="ab8ab-130">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="ab8ab-130">For more information, see:</span></span>
  
- [<span data-ttu-id="ab8ab-131">网络连接原则</span><span class="sxs-lookup"><span data-stu-id="ab8ab-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="ab8ab-132">Office 365 的网络和迁移规划</span><span class="sxs-lookup"><span data-stu-id="ab8ab-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="ab8ab-133">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ab8ab-133">Next step</span></span>

[<span data-ttu-id="ab8ab-134">为 Microsoft Azure PaaS 设计网络</span><span class="sxs-lookup"><span data-stu-id="ab8ab-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="ab8ab-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab8ab-135">See also</span></span>

[<span data-ttu-id="ab8ab-136">面向企业架构师的 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="ab8ab-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="ab8ab-137">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="ab8ab-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

