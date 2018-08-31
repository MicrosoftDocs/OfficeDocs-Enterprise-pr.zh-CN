---
title: Office 365 中的 NAT 支持
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 摘要：提供了有关如何使用网络地址转换 (NAT)，估算对组织内每个 IP 地址可以使用的客户端正确数量的详细信息。
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539516"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="d1c71-103">Office 365 中的 NAT 支持</span><span class="sxs-lookup"><span data-stu-id="d1c71-103">NAT support with Office 365</span></span>

 <span data-ttu-id="d1c71-104">**摘要：** 提供了有关如何使用网络地址转换 (NAT)，估算对组织内每个 IP 地址可以使用的客户端正确数量的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d1c71-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="d1c71-105">以前，指南建议您应使用每个 IP 地址连接到 Office 365 的 Exchange 客户端的最大数量的每个网络端口大约 2,000 个客户端。</span><span class="sxs-lookup"><span data-stu-id="d1c71-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="d1c71-106">为什么要使用 NAT？</span><span class="sxs-lookup"><span data-stu-id="d1c71-106">Why use NAT?</span></span>

<span data-ttu-id="d1c71-107">通过使用 NAT，成千上万的人就企业网络可以"共享"一些公开可路由的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d1c71-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="d1c71-p101">大多数公司网络使用专用 (RFC1918) IP 地址空间。专用地址空间由 Internet 号码分配机构 (IANA) 分配，仅用于不与全局 Internet 直接路由的网络。</span><span class="sxs-lookup"><span data-stu-id="d1c71-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="d1c71-p102">若要在专用的 IP 地址空间提供 Internet 访问设备，组织使用网关技术，如防火墙和提供网络地址转换 (NAT) 或端口地址转换 (PAT) 服务的代理。这些网关进行从内部的通信设备 （包括 Office 365） Internet 显示来自一个或多个公共可路由的 IP 地址。内部设备从每个出站连接将转换到公共 IP 地址上的不同源 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="d1c71-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="d1c71-113">为什么需要有很多连接到 Office 365 同时打开？</span><span class="sxs-lookup"><span data-stu-id="d1c71-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="d1c71-p103">Outlook 会打开 8 个或更多连接（有外接程序、共享日历、邮箱等的情况）。由于基于 Windows 的 NAT 设备上最多提供 64,000 个端口，因此在端口耗尽之前，一个 IP 地址后面最多可有 8,000 个用户。请注意，如果客户将非基于 Windows 操作系统的设备用于 NAT，则可用端口总数依赖于使用的 NAT 设备或软件。在这种情况下，最大端口数可能小于 64,000。端口可用性还受其他因素影响，例如 Windows 限制 4,000 个端口供其自用，于是可用端口总数减少到 60,000。还有其他同时连接的应用程序（例如 Internet Explorer）需要额外的端口。</span><span class="sxs-lookup"><span data-stu-id="d1c71-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="d1c71-119">计算最多支持的设备与 Office 365 单一公共 IP 地址</span><span class="sxs-lookup"><span data-stu-id="d1c71-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="d1c71-p104">若要确定的单个公用 IP 地址的设备的最大数量，您应监视网络流量，以确定每个客户端的峰值端口消耗。此外，峰值因子应使用的端口使用情况 (最小 4)。</span><span class="sxs-lookup"><span data-stu-id="d1c71-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="d1c71-122">**使用以下公式计算每个 IP 地址的受支持设备数：**</span><span class="sxs-lookup"><span data-stu-id="d1c71-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="d1c71-123">最多支持单个公用 IP 地址的设备数 = (64,000-受限制的端口) / （峰值端口使用 + 峰值因子）</span><span class="sxs-lookup"><span data-stu-id="d1c71-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="d1c71-124">**例如，下面是，则返回 true:**</span><span class="sxs-lookup"><span data-stu-id="d1c71-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="d1c71-125">**受限制的端口：** 4000 用于操作系统</span><span class="sxs-lookup"><span data-stu-id="d1c71-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="d1c71-126">每个设备的**峰值端口消耗：** 6</span><span class="sxs-lookup"><span data-stu-id="d1c71-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="d1c71-127">**峰值因子：** 4</span><span class="sxs-lookup"><span data-stu-id="d1c71-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="d1c71-128">然后，支持单个公用 IP 地址的设备的最大 = (64,000 4000) / （6 + 4） = 6,000</span><span class="sxs-lookup"><span data-stu-id="d1c71-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="d1c71-p105">Office 365 承载包，从 Microsoft Office Outlook 2007，2011 年 9 月或 Microsoft Outlook 2010 的 2011 年 11 月更新或更高版本的更新，从 Outlook (这两个 Office Outlook 2007 与服务的连接数中包含的发行版Pack 2 和 Outlook 2010 中) 到 Exchange 可以少至 2。您需要的不同操作系统用户行为，等等来确定最小和最大网络将需要在高峰期的端口数。</span><span class="sxs-lookup"><span data-stu-id="d1c71-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="d1c71-131">如果您想要支持单个公用 IP 地址后面的多个设备，请按照列出评估的可支持的设备的最大数量的步骤操作：</span><span class="sxs-lookup"><span data-stu-id="d1c71-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="d1c71-p106">监控网络流量，以确定每个客户端的峰值端口消耗。您应收集此数据：</span><span class="sxs-lookup"><span data-stu-id="d1c71-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="d1c71-134">从多个位置</span><span class="sxs-lookup"><span data-stu-id="d1c71-134">From multiple locations</span></span>
    
- <span data-ttu-id="d1c71-135">从多个设备</span><span class="sxs-lookup"><span data-stu-id="d1c71-135">From multiple devices</span></span>
    
- <span data-ttu-id="d1c71-136">多次</span><span class="sxs-lookup"><span data-stu-id="d1c71-136">At multiple times</span></span>
    
<span data-ttu-id="d1c71-137">使用上述公式计算用户环境中可支持的每个 IP 地址的最大用户数。</span><span class="sxs-lookup"><span data-stu-id="d1c71-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="d1c71-p107">有用于将客户端负载分散其他公共 IP 地址的各种方法。可用的策略取决于企业的网关解决方案的功能。最简单的解决方案是分隔您用户的地址空间和静态"分配"IP 地址数为每个网关。多个网关设备提供的另一种选择是使用池的 IP 地址的功能。地址池的好处是它不更加动态而且不太可能需要调整，随着用户群。</span><span class="sxs-lookup"><span data-stu-id="d1c71-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d1c71-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1c71-143">See also</span></span>

[<span data-ttu-id="d1c71-144">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="d1c71-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="d1c71-145">Office 365 终结点常见问题</span><span class="sxs-lookup"><span data-stu-id="d1c71-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

