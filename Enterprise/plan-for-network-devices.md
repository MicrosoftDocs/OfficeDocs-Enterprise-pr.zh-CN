---
title: 有关连接到 Office 365 服务的网络设备的计划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 摘要：介绍用于连接到 Office 365 的网络容量、WAN 加速器和负载平衡设备的注意事项。
ms.openlocfilehash: 066d2b07c10009ced1935086ee8d80720bd397ca
ms.sourcegitcommit: 2e6fadb5b2b16619ad141b6293d3466460720cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2019
ms.locfileid: "37428098"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="6b14d-103">有关连接到 Office 365 服务的网络设备的计划</span><span class="sxs-lookup"><span data-stu-id="6b14d-103">Plan for network devices that connect to Office 365 services</span></span>

<span data-ttu-id="6b14d-104">*本文适用于 Office 365 企业版和 Microsoft 365 企业版*</span><span class="sxs-lookup"><span data-stu-id="6b14d-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise*</span></span>
  
<span data-ttu-id="6b14d-105">**摘要**：介绍用于连接到 Office 365 的网络容量、WAN 加速器和负载平衡设备的注意事项。</span><span class="sxs-lookup"><span data-stu-id="6b14d-105">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>

<span data-ttu-id="6b14d-106">一些网络硬件可能对受支持的并发会话数量有限制。</span><span class="sxs-lookup"><span data-stu-id="6b14d-106">Some network hardware may have limitations on the number of concurrent sessions that are supported.</span></span> <span data-ttu-id="6b14d-107">对于拥有多于2000个用户的组织，我们建议他们监视其网络设备，以确保他们能够处理额外的 Office 365 服务流量。</span><span class="sxs-lookup"><span data-stu-id="6b14d-107">For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic.</span></span> <span data-ttu-id="6b14d-108">简单网络管理协议（SNMP）监控软件可帮助您执行此操作。</span><span class="sxs-lookup"><span data-stu-id="6b14d-108">Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="6b14d-109">本文是[Office 365 的网络规划和性能调整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="6b14d-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="6b14d-110">内部部署传出 Internet 代理设置还会影响到适用于客户端应用程序的 Office 365 服务的连接。</span><span class="sxs-lookup"><span data-stu-id="6b14d-110">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications.</span></span> <span data-ttu-id="6b14d-111">您还必须将网络代理设备配置为允许与 Microsoft 云服务 Url 和应用程序建立连接。</span><span class="sxs-lookup"><span data-stu-id="6b14d-111">You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications.</span></span> <span data-ttu-id="6b14d-112">每个组织都不同。</span><span class="sxs-lookup"><span data-stu-id="6b14d-112">Every organization is different.</span></span> <span data-ttu-id="6b14d-113">若要了解 Microsoft 如何管理此过程以及我们预配的带宽量，请[阅读案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。</span><span class="sxs-lookup"><span data-stu-id="6b14d-113">To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="6b14d-114">以下 Skype for Business 帮助文章包含有关 Skype for Business 设置的详细信息：</span><span class="sxs-lookup"><span data-stu-id="6b14d-114">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="6b14d-115">对适用于管理员的 Skype for business Online 登录错误进行故障排除</span><span class="sxs-lookup"><span data-stu-id="6b14d-115">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="6b14d-116">无法连接到 Skype for business，或某些功能不起作用，因为本地防火墙阻止了连接</span><span class="sxs-lookup"><span data-stu-id="6b14d-116">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="6b14d-117">虽然这些设置中的许多都是 Skype for Business，但有关网络配置的一般指导对所有 Office 365 服务都很有用。</span><span class="sxs-lookup"><span data-stu-id="6b14d-117">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="6b14d-118">确定网络容量</span><span class="sxs-lookup"><span data-stu-id="6b14d-118">Determining Network Capacity</span></span>

<span data-ttu-id="6b14d-119">连接上存在的每个网络设备都具有其容量限制。</span><span class="sxs-lookup"><span data-stu-id="6b14d-119">Every network device that exists on a connection has its capacity limit.</span></span> <span data-ttu-id="6b14d-120">这些设备包括客户端和服务器网络适配器、路由器、交换机和与之互连的集线器。</span><span class="sxs-lookup"><span data-stu-id="6b14d-120">These devices include the client and server network adapters, routers, switches, and hubs that interconnect them.</span></span> <span data-ttu-id="6b14d-121">足够的网络容量意味着它们都没有饱和。</span><span class="sxs-lookup"><span data-stu-id="6b14d-121">Adequate network capacity means that none of them are saturated.</span></span> <span data-ttu-id="6b14d-122">监视网络活动是有助于确保所有网络设备上的实际负载小于其最大容量的关键。</span><span class="sxs-lookup"><span data-stu-id="6b14d-122">Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity.</span></span> <span data-ttu-id="6b14d-123">网络容量影响代理设备性能。</span><span class="sxs-lookup"><span data-stu-id="6b14d-123">Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="6b14d-124">在大多数情况下，Internet 连接带宽设置流量限制。</span><span class="sxs-lookup"><span data-stu-id="6b14d-124">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic.</span></span> <span data-ttu-id="6b14d-125">高峰时段的性能较低可能是由于 Internet 链接使用过多而导致的。</span><span class="sxs-lookup"><span data-stu-id="6b14d-125">Weak performance during peak traffic hours is probably caused by excessive use of the Internet link.</span></span> <span data-ttu-id="6b14d-126">这种情况也适用于分支机构应用场景，其中分支机构代理服务器计算机通过低速广域网（WAN）链接连接到分支总部的代理设备。</span><span class="sxs-lookup"><span data-stu-id="6b14d-126">This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="6b14d-127">若要测试网络容量，请在代理网络接口上监视网络活动。</span><span class="sxs-lookup"><span data-stu-id="6b14d-127">To test network capacity, monitor the network activity on the proxy network interface.</span></span> <span data-ttu-id="6b14d-128">如果它的网络接口的最大带宽超过 75%，请考虑增加不充分的网络基础结构的带宽。</span><span class="sxs-lookup"><span data-stu-id="6b14d-128">If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate.</span></span> <span data-ttu-id="6b14d-129">或者，考虑使用高级功能，例如 HTTP 压缩。</span><span class="sxs-lookup"><span data-stu-id="6b14d-129">Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="6b14d-130">WAN 加速器</span><span class="sxs-lookup"><span data-stu-id="6b14d-130">WAN Accelerators</span></span>

<span data-ttu-id="6b14d-131">如果您的组织使用广域网络（WAN）加速代理设备，则在访问 Office 365 服务时可能会遇到问题。</span><span class="sxs-lookup"><span data-stu-id="6b14d-131">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services.</span></span> <span data-ttu-id="6b14d-132">你可能需要优化你的网络设备或设备，以确保你的用户在访问 Office 365 时具有一致的体验。</span><span class="sxs-lookup"><span data-stu-id="6b14d-132">You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365.</span></span> <span data-ttu-id="6b14d-133">例如，Office 365 服务对某些 Office 365 内容和 TCP 标头进行加密。</span><span class="sxs-lookup"><span data-stu-id="6b14d-133">For example, Office 365 services encrypt some Office 365 content and the TCP header.</span></span> <span data-ttu-id="6b14d-134">你的设备可能无法处理此类流量。</span><span class="sxs-lookup"><span data-stu-id="6b14d-134">Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="6b14d-135">阅读我们关于将[WAN 优化控制器或流量/检查设备与 Office 365 结合使用的](https://support.microsoft.com/kb/2690045)支持声明。</span><span class="sxs-lookup"><span data-stu-id="6b14d-135">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="6b14d-136">硬件和软件负载平衡设备</span><span class="sxs-lookup"><span data-stu-id="6b14d-136">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="6b14d-137">您的组织需要使用硬件负载平衡器（HLB）或网络负载平衡（NLB）解决方案将请求分发到 Active Directory 联合身份验证服务（AD FS）服务器和/或 Exchange 混合服务器。</span><span class="sxs-lookup"><span data-stu-id="6b14d-137">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers.</span></span> <span data-ttu-id="6b14d-138">负载平衡设备控制到内部部署服务器的网络通信。</span><span class="sxs-lookup"><span data-stu-id="6b14d-138">Load-balancing devices control the network traffic to the on-premises servers.</span></span> <span data-ttu-id="6b14d-139">在帮助确保单一登录和 Exchange 混合部署的可用性方面，这些服务器至关重要。</span><span class="sxs-lookup"><span data-stu-id="6b14d-139">These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="6b14d-140">我们提供了一个内置在 Windows Server 中的基于软件的 NLB 解决方案。</span><span class="sxs-lookup"><span data-stu-id="6b14d-140">We provide a software-based NLB solution built into Windows Server.</span></span> <span data-ttu-id="6b14d-141">Office 365 支持此解决方案以实现负载平衡。</span><span class="sxs-lookup"><span data-stu-id="6b14d-141">Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="6b14d-142">防火墙和代理</span><span class="sxs-lookup"><span data-stu-id="6b14d-142">Firewalls and proxies</span></span>

<span data-ttu-id="6b14d-143">有关配置防火墙和代理以连接到 Office 365 的更多详细信息，请阅读[管理 office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、[评估 office 365 网络连接](assessing-network-connectivity.md)和[office 365 终结点常见问题解答](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)以了解有关设备和电路的详细信息选框.</span><span class="sxs-lookup"><span data-stu-id="6b14d-143">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Assessing Office 365 network connectivity](assessing-network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6b14d-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b14d-144">See also</span></span>

[<span data-ttu-id="6b14d-145">Office 365 服务的部署顾问</span><span class="sxs-lookup"><span data-stu-id="6b14d-145">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)

[<span data-ttu-id="6b14d-146">Microsoft 365 企业版概述</span><span class="sxs-lookup"><span data-stu-id="6b14d-146">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
