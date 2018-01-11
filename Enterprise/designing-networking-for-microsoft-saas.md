---
title: "为 Microsoft SaaS 设计网络"
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "摘要： 了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。"
ms.openlocfilehash: 970d27e50e06f4d872de67589295c490aaa6e0e7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="c31e1-103">为 Microsoft SaaS 设计网络</span><span class="sxs-lookup"><span data-stu-id="c31e1-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="c31e1-104">**摘要：** 了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="c31e1-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="c31e1-105">优化你的 Microsoft SaaS 服务网络需要认真分析 Internet 边缘、你的客户端设备和典型的 IT 运营状况。</span><span class="sxs-lookup"><span data-stu-id="c31e1-105">Optimizing your network for Microsoft SaaS services requires careful analysis of your Internet edge, your client devices, and typical IT operations.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="c31e1-106">为 Microsoft SaaS 服务准备网络的步骤</span><span class="sxs-lookup"><span data-stu-id="c31e1-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="c31e1-107">按照这些步骤执行操作，为 Microsoft SaaS 服务优化你的网络：</span><span class="sxs-lookup"><span data-stu-id="c31e1-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="c31e1-108">完成 [Microsoft 云连接的常见元素](common-elements-of-microsoft-cloud-connectivity.md)中的**为 Microsoft 云服务准备网络的步骤**部分。</span><span class="sxs-lookup"><span data-stu-id="c31e1-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="c31e1-109">使用代理服务器建议为 Microsoft SaaS 服务优化你的 Internet 出口。</span><span class="sxs-lookup"><span data-stu-id="c31e1-109">Optimize your Internet egress for Microsoft SaaS services using the proxy server recommendations.</span></span>
    
3. <span data-ttu-id="c31e1-110">使用邻近度和位置建议优化 Internet 吞吐量。</span><span class="sxs-lookup"><span data-stu-id="c31e1-110">Optimize your Internet throughput using the proximity and location recommendations.</span></span>
    
4. <span data-ttu-id="c31e1-111">使用客户端使用注意事项优化客户端计算机以及它们所在的 Intranet 的性能。</span><span class="sxs-lookup"><span data-stu-id="c31e1-111">Optimize the performance of your client computers and the intranet on which they are located using the client usage considerations.</span></span>
    
5. <span data-ttu-id="c31e1-112">根据需要，使用 IT 操作注意事项优化数据迁移和同步的性能。</span><span class="sxs-lookup"><span data-stu-id="c31e1-112">As needed, optimize the performance of data migrations and synchronization using the IT operations considerations.</span></span>
    
## <a name="internet-edge-considerations"></a><span data-ttu-id="c31e1-113">有关 Internet 边缘的注意事项</span><span class="sxs-lookup"><span data-stu-id="c31e1-113">Internet edge considerations</span></span>

<span data-ttu-id="c31e1-114">下面是优化你的 Internet 边缘和 Microsoft SaaS 服务吞吐量的一些注意事项。</span><span class="sxs-lookup"><span data-stu-id="c31e1-114">Here are some things to consider optimize your Internet edge and throughput to Microsoft SaaS services.</span></span>
  
<span data-ttu-id="c31e1-115">**图 1：Microsoft SaaS 服务的连接选项**</span><span class="sxs-lookup"><span data-stu-id="c31e1-115">**Figure 1: Connection options for Microsoft SaaS services**</span></span>

![图 1：Microsoft SaaS 服务的连接选项](images/Network_Poster/SaaS1.png)
  
<span data-ttu-id="c31e1-117">图 1 显示了通过 Internet 管道或 ExpressRoute 连接到 Microsoft SaaS 服务的本地网络。</span><span class="sxs-lookup"><span data-stu-id="c31e1-117">Figure 1 shows an on-premises network connecting to Microsoft SaaS services over an Internet pipe or ExpressRoute.</span></span>
  
<span data-ttu-id="c31e1-118">下面是优化代理服务器的一些建议：</span><span class="sxs-lookup"><span data-stu-id="c31e1-118">Here are some recommendations to optimize your proxy server:</span></span>
  
- <span data-ttu-id="c31e1-119">使用 WPAD、PAC 或 GPO 配置 Web 客户端</span><span class="sxs-lookup"><span data-stu-id="c31e1-119">Configure web clients using WPAD, PAC, or GPO</span></span>
    
- <span data-ttu-id="c31e1-120">不要使用 SSL 拦截</span><span class="sxs-lookup"><span data-stu-id="c31e1-120">Don't use SSL interception</span></span>
    
- <span data-ttu-id="c31e1-121">使用 PAC 文件绕过 Microsoft SaaS 服务 DNS 名称的代理</span><span class="sxs-lookup"><span data-stu-id="c31e1-121">Use a PAC file to bypass the proxy for Microsoft SaaS service DNS names</span></span>
    
- <span data-ttu-id="c31e1-122">允许 CRL/OCSP 验证流量</span><span class="sxs-lookup"><span data-stu-id="c31e1-122">Allow traffic for CRL/OCSP verification</span></span>
    
<span data-ttu-id="c31e1-123">以下是需要检查的一些代理服务器瓶颈问题：</span><span class="sxs-lookup"><span data-stu-id="c31e1-123">Here are some proxy server bottlenecks to check:</span></span>
  
- <span data-ttu-id="c31e1-124">没有足够的持久连接 (Outlook)</span><span class="sxs-lookup"><span data-stu-id="c31e1-124">Insufficient persistent connections (Outlook)</span></span>
    
- <span data-ttu-id="c31e1-125">容量不足</span><span class="sxs-lookup"><span data-stu-id="c31e1-125">Insufficient capacity</span></span>
    
- <span data-ttu-id="c31e1-126">执行关闭网络评估</span><span class="sxs-lookup"><span data-stu-id="c31e1-126">Doing off-network evaluation</span></span>
    
- <span data-ttu-id="c31e1-127">要求身份验证</span><span class="sxs-lookup"><span data-stu-id="c31e1-127">Requiring authentication</span></span>
    
- <span data-ttu-id="c31e1-128">不支持 UDP 流量 (Skype for Business)</span><span class="sxs-lookup"><span data-stu-id="c31e1-128">No support for UDP traffic (Skype for Business)</span></span>
    
<span data-ttu-id="c31e1-129">这里是一些有关邻近度和位置的建议：</span><span class="sxs-lookup"><span data-stu-id="c31e1-129">Here are some proximity and location recommendations:</span></span>
  
- <span data-ttu-id="c31e1-130">不要通过专用 WAN 传送 Internet 流量</span><span class="sxs-lookup"><span data-stu-id="c31e1-130">Don't route your Internet traffic over the private WAN</span></span>
    
- <span data-ttu-id="c31e1-131">对区域外用户使用区域内 DNS 和 Internet 流量</span><span class="sxs-lookup"><span data-stu-id="c31e1-131">Use in-region DNS and Internet traffic flow for out-of-region users</span></span>
    
- <span data-ttu-id="c31e1-132">结合使用 ExpressRoute 与 Azure 服务以实现 Office 365 的高带宽和并发连接</span><span class="sxs-lookup"><span data-stu-id="c31e1-132">Use ExpressRoute for high bandwidth to Office 365 and concurrent connectivity with Azure services</span></span>
    
<span data-ttu-id="c31e1-133">以下是 Office 365 流量所需的出站端口：</span><span class="sxs-lookup"><span data-stu-id="c31e1-133">Here are the outbound ports needed for Office 365 traffic:</span></span>
  
- <span data-ttu-id="c31e1-134">TCP 80（用于 CRL/OCSP 检查）</span><span class="sxs-lookup"><span data-stu-id="c31e1-134">TCP 80 (for CRL/OCSP checks)</span></span>
    
- <span data-ttu-id="c31e1-135">TCP 443</span><span class="sxs-lookup"><span data-stu-id="c31e1-135">TCP 443</span></span>
    
- <span data-ttu-id="c31e1-136">UDP 3478</span><span class="sxs-lookup"><span data-stu-id="c31e1-136">UDP 3478</span></span>
    
- <span data-ttu-id="c31e1-137">TCP 5223</span><span class="sxs-lookup"><span data-stu-id="c31e1-137">TCP 5223</span></span>
    
- <span data-ttu-id="c31e1-138">TCP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="c31e1-138">TCP 50000-59999</span></span>
    
- <span data-ttu-id="c31e1-139">UDP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="c31e1-139">UDP 50000-59999</span></span>
    
## <a name="client-usage-considerations"></a><span data-ttu-id="c31e1-140">客户端使用注意事项</span><span class="sxs-lookup"><span data-stu-id="c31e1-140">Client usage considerations</span></span>

<span data-ttu-id="c31e1-141">首先，配置你的客户端将使用的一套服务，例如：</span><span class="sxs-lookup"><span data-stu-id="c31e1-141">First, configure the set of services that your clients will be using, such as:</span></span>
  
- <span data-ttu-id="c31e1-142">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c31e1-142">Azure Active Directory</span></span>
    
- <span data-ttu-id="c31e1-143">Office 365</span><span class="sxs-lookup"><span data-stu-id="c31e1-143">Office 365</span></span>
    
  - <span data-ttu-id="c31e1-144">Office 客户端应用</span><span class="sxs-lookup"><span data-stu-id="c31e1-144">Office client apps</span></span>
    
  - <span data-ttu-id="c31e1-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c31e1-145">SharePoint Online</span></span>
    
  - <span data-ttu-id="c31e1-146">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c31e1-146">Exchange Online</span></span>
    
  - <span data-ttu-id="c31e1-147">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="c31e1-147">Skype for Business</span></span>
    
- <span data-ttu-id="c31e1-148">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="c31e1-148">Microsoft Intune</span></span>
    
- <span data-ttu-id="c31e1-149">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c31e1-149">Dynamics 365</span></span>
    
<span data-ttu-id="c31e1-150">对于你的客户端计算机，请确定下列因素：</span><span class="sxs-lookup"><span data-stu-id="c31e1-150">For your client computers, determine the following:</span></span>
  
- <span data-ttu-id="c31e1-151">任何时间（一天中的某个时间、季节性、使用高峰和低谷）的最大数量</span><span class="sxs-lookup"><span data-stu-id="c31e1-151">Maximum number at any one time (time of day, seasonal, peaks and troughs in usage)</span></span>
    
- <span data-ttu-id="c31e1-152">高峰期所需的总带宽</span><span class="sxs-lookup"><span data-stu-id="c31e1-152">Total bandwidth needed for peaks</span></span>
    
- <span data-ttu-id="c31e1-153">Internet 出口设备的延迟</span><span class="sxs-lookup"><span data-stu-id="c31e1-153">Latency to the Internet egress device</span></span>
    
- <span data-ttu-id="c31e1-154">原产地与数据中心归置地</span><span class="sxs-lookup"><span data-stu-id="c31e1-154">Country of origin vs. country of datacenter co-location</span></span>
    
<span data-ttu-id="c31e1-155">对于每种类型的客户端（PC、智能电话、平板电脑），确保当前：</span><span class="sxs-lookup"><span data-stu-id="c31e1-155">For each type of client (PC, smartphone, tablet), ensure the current:</span></span>
  
- <span data-ttu-id="c31e1-156">操作系统</span><span class="sxs-lookup"><span data-stu-id="c31e1-156">Operating system</span></span>
    
- <span data-ttu-id="c31e1-157">Internet 浏览器</span><span class="sxs-lookup"><span data-stu-id="c31e1-157">Internet browser</span></span>
    
- <span data-ttu-id="c31e1-158">TCP/IP 堆栈</span><span class="sxs-lookup"><span data-stu-id="c31e1-158">TCP/IP stack</span></span>
    
- <span data-ttu-id="c31e1-159">网络硬件</span><span class="sxs-lookup"><span data-stu-id="c31e1-159">Network hardware</span></span>
    
- <span data-ttu-id="c31e1-160">网络硬件的操作系统驱动程序</span><span class="sxs-lookup"><span data-stu-id="c31e1-160">OS drivers for network hardware</span></span>
    
- <span data-ttu-id="c31e1-161">安装了更新和修补程序</span><span class="sxs-lookup"><span data-stu-id="c31e1-161">Updates and patches are installed</span></span>
    
<span data-ttu-id="c31e1-162">此外，还要优化 Intranet 连接吞吐量（有线、无线或 VPN）。</span><span class="sxs-lookup"><span data-stu-id="c31e1-162">Additionally, optimize intranet connection throughput (wired, wireless, or VPN).</span></span>
  
<span data-ttu-id="c31e1-163">有关详细信息，请参阅[与 Office 365 的 NAT 支持]((https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9))。</span><span class="sxs-lookup"><span data-stu-id="c31e1-163">For more information, see [NAT support with Office 365]((https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)).</span></span>
  
<span data-ttu-id="c31e1-164">有关使用适用于 Office 365 的 ExpressRoute，请参阅[适用于 Office 365 的 ExpressRoute]((https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd))。</span><span class="sxs-lookup"><span data-stu-id="c31e1-164">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365]((https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)).</span></span>
  
<span data-ttu-id="c31e1-165">若要优化你的 Intranet 性能，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c31e1-165">To optimize your intranet performance, do the following:</span></span>
  
- <span data-ttu-id="c31e1-166">使用工具来衡量到 Internet 边缘设备（PsPing、Ping、Tracert、TraceTCP、网络监视器）的往返时间 (RTT)</span><span class="sxs-lookup"><span data-stu-id="c31e1-166">Use tools to gauge round trip times (RTTs) to your Internet edge devices (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span></span>
    
- <span data-ttu-id="c31e1-167">使用流协议执行出口路径分析</span><span class="sxs-lookup"><span data-stu-id="c31e1-167">Perform egress path analysis using flow protocols</span></span>
    
- <span data-ttu-id="c31e1-168">对中间设备（年限、健康状况等）进行分析</span><span class="sxs-lookup"><span data-stu-id="c31e1-168">Perform analysis of intermediate devices (age, health, etc.)</span></span>
    
<span data-ttu-id="c31e1-169">有关详细信息，请参阅 [PsPing 工具]((https://technet.microsoft.com/sysinternals/jj729731.aspx))。</span><span class="sxs-lookup"><span data-stu-id="c31e1-169">For more information, see the [PsPing tool]((https://technet.microsoft.com/sysinternals/jj729731.aspx)).</span></span>
  
## <a name="it-operations-considerations"></a><span data-ttu-id="c31e1-170">IT 操作的注意事项</span><span class="sxs-lookup"><span data-stu-id="c31e1-170">IT operations considerations</span></span>

<span data-ttu-id="c31e1-171">下面是在 Microsoft SaaS 服务中运行 IT 工作负载时需要注意的一些事项。</span><span class="sxs-lookup"><span data-stu-id="c31e1-171">Here are some things to consider when operating an IT workload in a Microsoft SaaS service.</span></span>
  
### <a name="one-time-migrations"></a><span data-ttu-id="c31e1-172">一次性迁移</span><span class="sxs-lookup"><span data-stu-id="c31e1-172">One-time migrations</span></span>

<span data-ttu-id="c31e1-173">一次性迁移的示例包括基于云的应用程序或归档存储的批量数据传输。</span><span class="sxs-lookup"><span data-stu-id="c31e1-173">Examples of one-time migrations are bulk data transfer for cloud-based applications or archival storage.</span></span>
  
<span data-ttu-id="c31e1-174">若要优化你的网络以执行一次性迁移，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c31e1-174">To optimize your network for on-time migrations:</span></span>
  
- <span data-ttu-id="c31e1-175">避免高峰期使用网络和计算机修补时间</span><span class="sxs-lookup"><span data-stu-id="c31e1-175">Avoid peak network usage and computer patching times</span></span>
    
- <span data-ttu-id="c31e1-176">应在尝试实际迁移前创建基线和执行测试、评估网络运行状况并解决问题</span><span class="sxs-lookup"><span data-stu-id="c31e1-176">Should be baselined and piloted, assess network health and resolve issues before attempting actual migration</span></span>
    
- <span data-ttu-id="c31e1-177">进行事后总结供以后迁移时参考</span><span class="sxs-lookup"><span data-stu-id="c31e1-177">Perform post-mortem for future migrations</span></span>
    
### <a name="ongoing-synchronizations"></a><span data-ttu-id="c31e1-178">持续同步</span><span class="sxs-lookup"><span data-stu-id="c31e1-178">Ongoing synchronizations</span></span>

<span data-ttu-id="c31e1-179">持续同步的示例有目录信息、设置或文件。</span><span class="sxs-lookup"><span data-stu-id="c31e1-179">Examples of ongoing synchronizations are directory information, settings, or files.</span></span>
  
<span data-ttu-id="c31e1-180">要优化你的网络以执行持续同步，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c31e1-180">To optimize your network for ongoing synchronizations:</span></span>
  
- <span data-ttu-id="c31e1-181">确保网络带宽监控系统已到位，解决或消除收集的错误</span><span class="sxs-lookup"><span data-stu-id="c31e1-181">Ensure that a network bandwidth monitoring system is in place, resolve or dismiss collected errors</span></span>
    
- <span data-ttu-id="c31e1-182">使用带宽监控结果来确定是否需要进行网络更改（向上/向外扩展、新电路或添加设备）</span><span class="sxs-lookup"><span data-stu-id="c31e1-182">Use bandwidth monitoring results to determine need for network changes (scale-up/out, new circuits, or adding devices)</span></span>
    
<span data-ttu-id="c31e1-183">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="c31e1-183">For more information, see:</span></span>
  
- <span data-ttu-id="c31e1-184">[Office 365 的网络和迁移规划]((https://aka.ms/tune))</span><span class="sxs-lookup"><span data-stu-id="c31e1-184">[Network and migration planning for Office 365]((https://aka.ms/tune))</span></span>
    
- <span data-ttu-id="c31e1-185">[Office 365 性能管理 Microsoft Virtual Academy 课程]((https://aka.ms/o365perf))</span><span class="sxs-lookup"><span data-stu-id="c31e1-185">[Office 365 Performance Management Microsoft Virtual Academy course]((https://aka.ms/o365perf))</span></span>
    
- <span data-ttu-id="c31e1-186">[面向 Office 365 的 ExpressRoute]((https://aka.ms/expressrouteoffice365))</span><span class="sxs-lookup"><span data-stu-id="c31e1-186">[ExpressRoute for Office 365]((https://aka.ms/expressrouteoffice365))</span></span>
    
## <a name="see-also"></a><span data-ttu-id="c31e1-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c31e1-187">See Also</span></span>

[<span data-ttu-id="c31e1-188">面向企业架构师的 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="c31e1-188">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="c31e1-189">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="c31e1-189">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="c31e1-190">[Microsoft 企业云路线图：IT 决策者的资源]((https://sway.com/FJ2xsyWtkJc2taRD))</span><span class="sxs-lookup"><span data-stu-id="c31e1-190">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))</span></span>



