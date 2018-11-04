---
title: 有关连接到 Office 365 服务的网络设备的计划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
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
description: 摘要：介绍了网络容量的考虑因素、WAN 加速器和用于连接到 Office 365 的负载平衡设备。
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933119"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="094e8-103">有关连接到 Office 365 服务的网络设备的计划</span><span class="sxs-lookup"><span data-stu-id="094e8-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="094e8-104">**摘要**：介绍了网络容量的考虑因素、WAN 加速器和用于连接到 Office 365 的负载平衡设备。</span><span class="sxs-lookup"><span data-stu-id="094e8-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="094e8-p101">一些网络硬件可能有支持的并发会话的数目的限制。对于具有超过 2,000 个用户的组织，我们建议它们监视其网络设备，以确保它们是能够处理更多的 Office 365 服务通信。简单网络管理协议 (SNMP) 监控软件可以帮助您执行此操作。</span><span class="sxs-lookup"><span data-stu-id="094e8-p101">Some network hardware may have limitations on the number of concurrent sessions that are supported. For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic. Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="094e8-108">本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="094e8-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="094e8-p102">在本地传出 Internet 代理设置也会影响到您的客户端应用程序的 Office 365 服务的连接。您还必须配置网络代理设备以允许 Microsoft 云服务 Url 和应用程序的连接。每个组织为不同。若要了解有关 Microsoft 如何管理此过程和带宽量我们设置，[读取案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。</span><span class="sxs-lookup"><span data-stu-id="094e8-p102">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications. You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications. Every organization is different. To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="094e8-113">业务帮助文章的以下 Skype 具有 Skype 业务设置的详细信息：</span><span class="sxs-lookup"><span data-stu-id="094e8-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="094e8-114">管理员 Skype 业务 Online 登录错误疑难解答</span><span class="sxs-lookup"><span data-stu-id="094e8-114">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="094e8-115">无法连接到业务的 Skype 或某些功能执行操作不起作用，因为本地防火墙阻止连接</span><span class="sxs-lookup"><span data-stu-id="094e8-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="094e8-116">尽管其中许多设置业务特定的 Skype，网络配置的一般指南可用于所有 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="094e8-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="094e8-117">确定网络容量</span><span class="sxs-lookup"><span data-stu-id="094e8-117">Determining Network Capacity</span></span>

<span data-ttu-id="094e8-p103">连接上存在的每个网络设备都有容量限制。其中包括客户端和服务器网络适配器、路由器、交换机以及将其互连的集线器。足够的网络容量意味着这些网络设备都未饱和。监视网络活动有助于确保所有网络设备上的实际负载小于其最大容量。网络容量影响代理设备性能。</span><span class="sxs-lookup"><span data-stu-id="094e8-p103">Every network device that exists on a connection has its capacity limit. These devices include the client and server network adapters, routers, switches, and hubs that interconnect them. Adequate network capacity means that none of them are saturated. Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity. Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="094e8-p104">在大多数情况下，Internet 连接带宽设置流量量的限制。在高峰时段流量性能不佳可能是由 Internet 链接的过度使用导致的。这种情况下也适用于分支办公室方案，其中分支办公室代理服务器计算机连接到分支的总部的代理设备慢速广域网 (WAN) 链接。</span><span class="sxs-lookup"><span data-stu-id="094e8-p104">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic. Weak performance during peak traffic hours is probably caused by excessive use of the Internet link. This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="094e8-p105">若要测试在网络容量，监视在代理服务器网络接口的网络活动。如果它为 75%以上的任何网络接口的最大带宽，请考虑增加的带宽不足的网络基础结构。或者，请考虑使用高级的功能，例如 HTTP 压缩。</span><span class="sxs-lookup"><span data-stu-id="094e8-p105">To test network capacity, monitor the network activity on the proxy network interface. If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate. Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="094e8-129">WAN 加速器</span><span class="sxs-lookup"><span data-stu-id="094e8-129">WAN Accelerators</span></span>

<span data-ttu-id="094e8-p106">如果您的组织使用广域网 (wan) 加速代理设备，访问 Office 365 服务时可能遇到的问题。您可能需要优化您的网络设备或设备，以确保您的用户访问 Office 365 时具有一致的体验。例如，Office 365 服务加密某些 Office 365 内容和 TCP 标头。您的设备可能不能处理这种类型的通信。</span><span class="sxs-lookup"><span data-stu-id="094e8-p106">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services. You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365. For example, Office 365 services encrypt some Office 365 content and the TCP header. Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="094e8-134">阅读有关[使用 WAN 优化控制器或与 Office 365 的通信/检查设备](https://support.microsoft.com/kb/2690045)我们支持语句。</span><span class="sxs-lookup"><span data-stu-id="094e8-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="094e8-135">硬件和软件负载平衡设备</span><span class="sxs-lookup"><span data-stu-id="094e8-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="094e8-p107">您的组织需要使用硬件负载平衡器 (HLB) 或网络负载平衡 (NLB) 解决方案将请求分发到 Active Directory 联合身份验证服务 (AD FS) 服务器和/或 Exchange 混合服务器。负载平衡设备控制传到内部部署服务器的网络流量。这些服务器有助于确保单一登录和 Exchange 混合部署的可用性。</span><span class="sxs-lookup"><span data-stu-id="094e8-p107">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers. Load-balancing devices control the network traffic to the on-premises servers. These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="094e8-p108">我们提供了 Windows Server 中内置的基于软件的 NLB 解决方案。Office 365 支持此解决方案以实现负载平衡。</span><span class="sxs-lookup"><span data-stu-id="094e8-p108">We provide a software-based NLB solution built into Windows Server. Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="094e8-141">防火墙和代理</span><span class="sxs-lookup"><span data-stu-id="094e8-141">Firewalls and proxies</span></span>

<span data-ttu-id="094e8-142">有关配置防火墙和代理，以连接到 Office 365，读取[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、[网络连接到 Office 365](network-connectivity.md)和[Office 365 终结点常见问题](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)，以详细了解如何设备和电路所选内容的详细信息。</span><span class="sxs-lookup"><span data-stu-id="094e8-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="094e8-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="094e8-143">See also</span></span>

[<span data-ttu-id="094e8-144">Office 365 服务的部署顾问</span><span class="sxs-lookup"><span data-stu-id="094e8-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
