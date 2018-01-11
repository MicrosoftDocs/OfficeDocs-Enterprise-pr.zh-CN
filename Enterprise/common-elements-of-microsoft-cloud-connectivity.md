---
title: "Microsoft 云连接的公共元素"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "摘要： 了解网络基础结构的常见元素，以及如何准备你的网络。"
ms.openlocfilehash: 9dffcae28283c9f8b8c219284554225645435e0a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="9da72-103">Microsoft 云连接的公共元素</span><span class="sxs-lookup"><span data-stu-id="9da72-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="9da72-104">**摘要：** 了解网络基础结构的常见元素，以及如何准备你的网络。</span><span class="sxs-lookup"><span data-stu-id="9da72-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="9da72-105">将你的网络与 Microsoft 云进行集成可提供对各种服务的最佳访问。</span><span class="sxs-lookup"><span data-stu-id="9da72-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="9da72-106">为 Microsoft 云服务准备网络的步骤</span><span class="sxs-lookup"><span data-stu-id="9da72-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="9da72-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="9da72-107"><a name="steps"> </a></span></span>

<span data-ttu-id="9da72-108">对于你的内部部署网络：</span><span class="sxs-lookup"><span data-stu-id="9da72-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="9da72-109">分析客户端计算机，并针对网络硬件、软件驱动程序、协议设置和 Internet 浏览器进行优化。</span><span class="sxs-lookup"><span data-stu-id="9da72-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="9da72-110">分析你的内部部署网络，了解到 Internet 边缘设备的流量延迟和最佳路由。</span><span class="sxs-lookup"><span data-stu-id="9da72-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="9da72-111">分析 Internet 边缘设备的容量和性能，并进行优化以提高流量级别。</span><span class="sxs-lookup"><span data-stu-id="9da72-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="9da72-112">对于 Internet 连接：</span><span class="sxs-lookup"><span data-stu-id="9da72-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="9da72-113">分析 Internet 边缘设备（如外部防火墙）与你连接到的 Microsoft 云服务的区域位置之间的延迟。</span><span class="sxs-lookup"><span data-stu-id="9da72-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="9da72-p101">分析当前 Internet 连接的容量和利用率，并在需要时增加容量。或者，添加 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="9da72-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="9da72-116">Microsoft 云连接选项</span><span class="sxs-lookup"><span data-stu-id="9da72-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="9da72-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="9da72-117"><a name="steps"> </a></span></span>

<span data-ttu-id="9da72-118">使用现有的 Internet 管道或到 Office 365、Azure 和 Dynamics 365 的 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="9da72-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="9da72-119">**图 1：Microsoft 云连接选项**</span><span class="sxs-lookup"><span data-stu-id="9da72-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![图 1：Microsoft 云连接选项](images/Network_Poster/CommonElements.png)

  
<span data-ttu-id="9da72-p102">图 1 显示内部部署网络如何使用其现有的 Internet 管道或 ExpressRoute 连接到 Microsoft 云服务。Internet 管道表示 DMZ，并且可以具有下列组件：</span><span class="sxs-lookup"><span data-stu-id="9da72-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="9da72-p103">**内部防火墙：** 受信任的网络与不受信的网络任之间的屏障。执行流量筛选（基于规则）和监视。</span><span class="sxs-lookup"><span data-stu-id="9da72-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="9da72-125">**外部工作负载：** 网站或其他工作负载供 Internet 上的外部用户使用。</span><span class="sxs-lookup"><span data-stu-id="9da72-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="9da72-p104">**代理服务器：** 代表 Intranet 用户发出的对 Web 内容的服务请求。反向代理服务器允许未经请求的入站请求。</span><span class="sxs-lookup"><span data-stu-id="9da72-p104">**Proxy server:** Services requests for web content on behalf of intranet users. A reverse proxy allows unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="9da72-p105">**外部防火墙：** 允许出站流量和指定的入站流量。可以执行地址转换。</span><span class="sxs-lookup"><span data-stu-id="9da72-p105">**External firewall:** Allows outbound traffic and specified inbound traffic. Can perform address translation.</span></span>
    
- <span data-ttu-id="9da72-130">**到 ISP 的 WAN 连接：** 到 ISP 的基于载波的连接，与 Internet 对等，可以实现连接和传送。</span><span class="sxs-lookup"><span data-stu-id="9da72-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="9da72-131">对所有 Microsoft 云服务通用的网络区域</span><span class="sxs-lookup"><span data-stu-id="9da72-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="9da72-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="9da72-132"><a name="steps"> </a></span></span>

<span data-ttu-id="9da72-133">采用 Microsoft 的任何云服务时，必须将这些网络区域考虑在内。</span><span class="sxs-lookup"><span data-stu-id="9da72-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="9da72-134">**Intranet 性能：** 如果不优化 Intranet（其中包括客户端计算机），基于 Internet 的资源的性能就会受损。</span><span class="sxs-lookup"><span data-stu-id="9da72-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="9da72-135">**边缘设备：** 网络边缘的设备用作出口点，可以包括网络地址转换器 (NAT)、代理服务器（包括反向代理服务器）、防火墙、入侵检测设备或这些项的组合。</span><span class="sxs-lookup"><span data-stu-id="9da72-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="9da72-p106">**Internet 连接：** 到 ISP 和 Internet 的 WAN 连接应具有足够的容量来处理峰值负载。你也可以使用 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="9da72-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="9da72-p107">**Internet DNS：** A、AAAA、CNAME、MX、PTR 和其他记录，可以查找 Microsoft 云或你在云中托管的服务。例如，可能需要你在 Azure PaaS 中托管的应用程序的 CNAME 记录。</span><span class="sxs-lookup"><span data-stu-id="9da72-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="9da72-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9da72-140">See Also</span></span>

<span data-ttu-id="9da72-141"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="9da72-141"><a name="steps"> </a></span></span>

[<span data-ttu-id="9da72-142">面向企业架构师的 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="9da72-142">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="9da72-143">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="9da72-143">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="9da72-144">[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)</span><span class="sxs-lookup"><span data-stu-id="9da72-144">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>


