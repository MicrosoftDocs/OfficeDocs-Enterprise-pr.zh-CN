---
title: Office 365 中的 NAT 支持
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 摘要：提供了有关如何使用网络地址转换（NAT）对组织中的每个 IP 地址使用的客户端的正确数量的详细信息。
ms.openlocfilehash: 6140cf664a08701e9491c241d5754d51196e3922
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844563"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="cbfa3-103">Office 365 中的 NAT 支持</span><span class="sxs-lookup"><span data-stu-id="cbfa3-103">NAT support with Office 365</span></span>

<span data-ttu-id="cbfa3-104">*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="cbfa3-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="cbfa3-105">以前，建议使用每个 IP 地址连接到 Office 365 的 Exchange 客户端的最大数量大约为每个网络端口2000个客户端。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="cbfa3-106">为什么要使用 NAT？</span><span class="sxs-lookup"><span data-stu-id="cbfa3-106">Why use NAT?</span></span>

<span data-ttu-id="cbfa3-107">通过使用 NAT，企业网络中的数以千计的人员可以 "共享" 几个可公开路由的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="cbfa3-108">大多数公司网络使用专用（RFC1918） IP 地址空间。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-108">Most corporate networks use private (RFC1918) IP address space.</span></span> <span data-ttu-id="cbfa3-109">专用地址空间由 Internet 分配的号码颁发机构（IANA）分配，专门用于不直接路由到全球 Internet 的网络。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-109">Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="cbfa3-110">若要在专用 IP 地址空间上提供对设备的 Internet 访问，组织需要使用提供网络地址转换（NAT）或端口地址转换（PAT）服务的防火墙和代理等网关技术。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-110">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services.</span></span> <span data-ttu-id="cbfa3-111">这些网关使来自内部设备（包括 Office 365）的通信显示为来自一个或多个可公开路由的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-111">These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses.</span></span> <span data-ttu-id="cbfa3-112">来自内部设备的每个出站连接都会转换为公共 IP 地址上的其他源 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-112">Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="cbfa3-113">为什么您需要将这么多的连接同时打开到 Office 365？</span><span class="sxs-lookup"><span data-stu-id="cbfa3-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="cbfa3-114">Outlook 可能会打开八个或更多的连接（在有加载项、共享日历、邮箱等的情况下）。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-114">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.).</span></span> <span data-ttu-id="cbfa3-115">由于基于 Windows 的 NAT 设备上最多可提供64000个端口，因此在端口耗尽之前，IP 地址最多可以有8000个用户。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-115">Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted.</span></span> <span data-ttu-id="cbfa3-116">请注意，如果客户使用的是基于非 Windows 操作系统的 NAT 设备，则可用端口总数取决于所使用的 NAT 设备或软件。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-116">Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used.</span></span> <span data-ttu-id="cbfa3-117">在这种情况下，最大端口数可能小于64000。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-117">In this scenario, the maximum number of ports could be less than 64,000.</span></span> <span data-ttu-id="cbfa3-118">端口的可用性也受其他因素（如 Windows 限制4000端口以供其自己使用）的影响，这会将可用端口的总数减少到 60 000。可以同时连接的其他应用程序（如 Internet Explorer），需要额外的端口。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-118">Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="cbfa3-119">使用 Office 365 计算单个公共 IP 地址后的最大受支持设备数</span><span class="sxs-lookup"><span data-stu-id="cbfa3-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="cbfa3-120">若要确定单个公共 IP 地址后的最大设备数，应监视网络流量以确定每个客户端的峰值端口使用率。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-120">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="cbfa3-121">此外，应将峰值因子用于端口使用情况（最小值为4）。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-121">Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="cbfa3-122">**使用以下公式计算每个 IP 地址支持的设备数：**</span><span class="sxs-lookup"><span data-stu-id="cbfa3-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="cbfa3-123">单个公共 IP 地址后的最大受支持设备数 = （64000限制的端口）/（峰值端口消耗 + 峰值因子）</span><span class="sxs-lookup"><span data-stu-id="cbfa3-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="cbfa3-124">**例如，如果满足以下条件：**</span><span class="sxs-lookup"><span data-stu-id="cbfa3-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="cbfa3-125">**受限端口：** 针对操作系统的4000</span><span class="sxs-lookup"><span data-stu-id="cbfa3-125">**Restricted ports:** 4,000 for the operating system</span></span>

- <span data-ttu-id="cbfa3-126">**峰值端口消耗：** 每个设备6个</span><span class="sxs-lookup"><span data-stu-id="cbfa3-126">**Peak port consumption:** 6 per device</span></span>

- <span data-ttu-id="cbfa3-127">**峰值因子：** 4</span><span class="sxs-lookup"><span data-stu-id="cbfa3-127">**Peak factor:** 4</span></span>

<span data-ttu-id="cbfa3-128">然后，单个公共 IP 地址后的最大支持设备数 = （64000-4000）/（6 + 4） = 6000</span><span class="sxs-lookup"><span data-stu-id="cbfa3-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="cbfa3-129">发布 Office 365 托管包，包括在 Microsoft Office Outlook 2007 的9月2011更新中，或 Microsoft Outlook 2010 的 11 2011 月，或后续更新中，来自 Outlook 的连接数（两个 Office Outlook 2007 with ServicePack 2 和 Outlook 2010）到 Exchange 可以只是2个。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-129">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2.</span></span> <span data-ttu-id="cbfa3-130">您需要考虑不同的操作系统、用户行为等，以确定您的网络在高峰期所需的最小和最大端口数。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-130">You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="cbfa3-131">如果要支持单个公用 IP 地址后面的更多设备，请按照概述的步骤来评估可支持的最大设备数：</span><span class="sxs-lookup"><span data-stu-id="cbfa3-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="cbfa3-132">监视网络流量以确定每个客户端的峰值端口使用率。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-132">Monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="cbfa3-133">应收集以下数据：</span><span class="sxs-lookup"><span data-stu-id="cbfa3-133">You should collect this data:</span></span>
  
- <span data-ttu-id="cbfa3-134">从多个位置</span><span class="sxs-lookup"><span data-stu-id="cbfa3-134">From multiple locations</span></span>
    
- <span data-ttu-id="cbfa3-135">从多个设备</span><span class="sxs-lookup"><span data-stu-id="cbfa3-135">From multiple devices</span></span>
    
- <span data-ttu-id="cbfa3-136">多次</span><span class="sxs-lookup"><span data-stu-id="cbfa3-136">At multiple times</span></span>
    
<span data-ttu-id="cbfa3-137">使用上述公式可计算在其环境中可支持的每个 IP 地址的最大用户数。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="cbfa3-138">有多种方法可以在其他公用 IP 地址之间分发客户端负载。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-138">There are various methods for distributing client load across additional public IP addresses.</span></span> <span data-ttu-id="cbfa3-139">可用策略取决于企业网关解决方案的功能。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-139">Strategies available depend on the capabilities of the corporate gateway solution.</span></span> <span data-ttu-id="cbfa3-140">最简单的解决方案是对用户地址空间进行分段，并对每个网关静态 "分配" 多个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-140">The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway.</span></span> <span data-ttu-id="cbfa3-141">许多网关设备提供的另一种方法是能够使用 IP 地址池。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-141">Another alternative that many gateway devices offer is the ability to use a pool of IP addresses.</span></span> <span data-ttu-id="cbfa3-142">地址池的优势在于，随着用户群的增长，更有可能在更大的程度上增加和减少需求调整。</span><span class="sxs-lookup"><span data-stu-id="cbfa3-142">The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cbfa3-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cbfa3-143">See also</span></span>

[<span data-ttu-id="cbfa3-144">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="cbfa3-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="cbfa3-145">Office 365 终结点 FAQ</span><span class="sxs-lookup"><span data-stu-id="cbfa3-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
