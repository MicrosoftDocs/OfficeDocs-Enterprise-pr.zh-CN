---
title: Office 365 的网络和迁移规划
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: 包含有关网络规划和测试的信息的链接和迁移到 Office 365。
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223054"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="4cfc7-103">Office 365 的网络和迁移规划</span><span class="sxs-lookup"><span data-stu-id="4cfc7-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="4cfc7-104">本文包含有关网络规划和测试的信息链接和迁移到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="4cfc7-105">在首次部署或迁移到 Office 365 之前，可以使用这些主题中的信息来估计您需要的带宽，然后测试和验证您是否具有足够的带宽来部署或迁移到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="4cfc7-106">本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![请参阅 Microsoft 云网络企业架构师海报](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="4cfc7-108">优化网络 for Office 365 和其他 Microsoft 云平台和服务的步骤，请参阅[Microsoft 云网络的企业架构师](https://aka.ms/cloudarchnetworking)海报。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="4cfc7-109">估计网络带宽要求</span><span class="sxs-lookup"><span data-stu-id="4cfc7-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="4cfc7-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="4cfc7-110"></span></span>

<span data-ttu-id="4cfc7-p101">使用 Office 365 可能会增加贵组织的 internet 电路的使用率。非常重要，以确定当前可用带宽量是否足以同时保持至少 20%完全部署 Office 365 之后处理估计的增加容量来处理繁忙的天数。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p101">Using Office 365 may increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="4cfc7-113">若要估计带宽，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="4cfc7-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="4cfc7-p102">评估客户端将使用每个 Internet 出口数。让我们多 terabit 网络中处理尽可能尽可能的连接。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p102">Assess the number of clients that will use each Internet egress. Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="4cfc7-p103">确定哪些 Office 365 服务和功能可供客户端使用。您可能必须具有不同的服务或使用情况配置文件的人员的组。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p103">Determine which Office 365 services and features will be available for clients to use. You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="4cfc7-p104">测量网络使用的客户端试点组。确保试点客户端所代表的不同的配置文件的组织，以及在不同地理位置中的人员。您可以跨检查您对我们旧计算器的结果的[Exchange](https://go.microsoft.com/fwlink/p/?LinkId=321550)和[for Business 的 Skype](https://go.microsoft.com/fwlink/p/?LinkId=321551)或[案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)我们我们自己的网络执行。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p104">Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations. You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="4cfc7-121">从试用组的度量值用于在整个组织的需求外推并重新测试对您的网络进行任何更改之前验证估计值。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="4cfc7-122">测试您现有的网络</span><span class="sxs-lookup"><span data-stu-id="4cfc7-122">Test your existing network</span></span>
<span data-ttu-id="4cfc7-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="4cfc7-123"></span></span>

 <span data-ttu-id="4cfc7-p105">**网络工具。** 测试和验证您的 Internet 带宽，以确定下载、 上载和延迟的约束。这些工具将帮助您确定您的网络迁移以及完全正在部署后的功能。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p105">**Network tools.** Test and validate your Internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="4cfc7-p106">[Microsoft 消息分析器](https://technet.microsoft.com/library/jj649776.aspx)： 消息分析器是有效的网络问题进行故障排除工具。消息分析器捕获、 显示，并分析基于协议消息通信和系统消息。消息分析器还可以导入、 合计并分析日志和跟踪文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="4cfc7-130">[Microsoft 远程连接分析器](https://go.microsoft.com/fwlink/p/?LinkId=517243)： Exchange Online 环境中测试连接。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="4cfc7-131">使用[Microsoft 支持和 Office 365 恢复助手](https://diagnostics.office.com/#/Download?env=SOC)修复 Outlook 和 Office 365 问题。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="4cfc7-132">Best practices for network planning and improving migration performance for Office 365</span><span class="sxs-lookup"><span data-stu-id="4cfc7-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="4cfc7-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="4cfc7-133"></span></span>

<span data-ttu-id="4cfc7-134">深入到这些最佳做法有关提高您的 Office 365 体验的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="4cfc7-p107">要开始立即帮助您的用户？有关使用 Office 365，包括 SharePoint Online、 Exchange Online 和 Lync Online，您的网络刚刚不共同完成时提示，请参阅[使用在低速网络中的 Office 365 的最佳实践](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。本文出链接到 TechNet 和 Support.office.com 上的内容加载优化您的 Office 365 体验，并包括有关自定义网页以及如何设置 Internet Explorer 设置获得最佳的 Office 365 体验的简单方法。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p107">Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="4cfc7-p108">阅读[Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)了解用于安全地管理 Office 365 流量和获取最佳性能的连接原则。本文将帮助您了解有关安全地优化 Office 365 网络连接的最新指南。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p108">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="4cfc7-p109">通过仔细管理 Windows 更新的计划来提高邮件迁移性能。可以更新成批客户端计算机，并确保迁移到 Office 365 以哪种网络带宽使用之前更新所有客户端计算机。有关详细信息，请参阅[手动更新和配置最新的更新的 Office 365 的桌面](https://support.microsoft.com/gp/office-2013-365-update)。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p109">Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="4cfc7-p110">Office 365 网络流量最佳执行时有视为受信任的 Internet 服务，并且允许绕过大部分传统筛选和扫描的某些组织将置于不受信任的 Internet 服务网络流量。这通常包括删除出站代理用户身份验证和检查数据包来，如处理，以及确保使用适当的网络地址转换 (NAT) 和足够的带宽容量来处理增加 internet 本地出口网络请求。配置网络以处理作为受信任的 Internet 服务网络上的 Office 365 的其他指导信息，请参阅[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p110">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="4cfc7-p111">确保[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。额外的流量转到 Office 365 结果中的出站代理服务器连接的增加，以及增加的安全流量通过 TLS/SSL。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p111">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="4cfc7-p112">如果您的出站代理需要用户身份验证可能会遇到低速连接性或功能损失。绕过的 Office 365 域的身份验证要求可以减少此开销。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p112">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="4cfc7-p113">如果您有大量的共享日历和邮箱，则可能会发现从 Outlook 到 Exchange 的连接数有所增加。例如，Outlook 客户端会为每个使用中的共享日历打开最多两个其他连接。在这种情况下，请确保出口代理可以处理这些连接，或者对 Outlook 不使用代理以连接到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p113">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="4cfc7-p114">确定的公共 IP 地址的受支持设备的最大数量以及如何跨多个 IP 地址负载平衡。有关详细信息，请参阅[Office 365 的 NAT 支持](nat-support-with-office-365.md)。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p114">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="4cfc7-p115">如果网络上，要检查的计算机的出站连接，绕过此筛选到 Office 365 域将以下措施改善连接性和性能。此外，绕过出站检查通常删除单个的 Internet 出口需要和允许的发往的 Office 365 网络请求的本地 Internet 出口。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p115">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="4cfc7-p116">某些客户发现内部网络设置可能会影响性能。设置最大传输单元 (MTU) 大小，如网络自动协商或自动检测和不够理想路由到 Internet 的查看常见位置。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-p116">Some customers find internal network settings may affect performance. Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="4cfc7-159">Office 365 的网络规划参考</span><span class="sxs-lookup"><span data-stu-id="4cfc7-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="4cfc7-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="4cfc7-160"></span></span>

<span data-ttu-id="4cfc7-161">这些主题包含 Office 365 网络引用的详细的信息。</span><span class="sxs-lookup"><span data-stu-id="4cfc7-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="4cfc7-162">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="4cfc7-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="4cfc7-163">客户端连接</span><span class="sxs-lookup"><span data-stu-id="4cfc7-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="4cfc7-164">内容传递网络</span><span class="sxs-lookup"><span data-stu-id="4cfc7-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="4cfc7-165">Office 365 的外部域名系统记录</span><span class="sxs-lookup"><span data-stu-id="4cfc7-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="4cfc7-166">Office 365 服务中的 IPv6 支持</span><span class="sxs-lookup"><span data-stu-id="4cfc7-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="4cfc7-167">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="4cfc7-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="4cfc7-168">Microsoft 虚拟学院： Office 365 性能管理</span><span class="sxs-lookup"><span data-stu-id="4cfc7-168">Microsoft Virtual Academy: Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [<span data-ttu-id="4cfc7-169">Office 365 视频网络经常常见问题 (FAQ)</span><span class="sxs-lookup"><span data-stu-id="4cfc7-169">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="4cfc7-170">有关连接到 Office 365 服务的网络设备的计划</span><span class="sxs-lookup"><span data-stu-id="4cfc7-170">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="4cfc7-171">Office 365 服务的部署顾问</span><span class="sxs-lookup"><span data-stu-id="4cfc7-171">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

