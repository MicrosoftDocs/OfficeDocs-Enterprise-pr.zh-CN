---
title: "Microsoft SaaS (Office 365) 的混合云方案"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "摘要： 了解混合的体系结构和方案，Microsoft 的基于 SaaS 的云服务 (Office 365)。"
ms.openlocfilehash: 63126d694817f8323494e584f1f497a1a732c678
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="23242-103">Microsoft SaaS (Office 365) 的混合云方案</span><span class="sxs-lookup"><span data-stu-id="23242-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="23242-104">**摘要：**了解混合的体系结构和方案，Microsoft 的基于 SaaS 的云服务 (Office 365)。</span><span class="sxs-lookup"><span data-stu-id="23242-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="23242-105">将 Exchange、SharePoint，或 Skype for Business 本地部署与其在 Office 365 中的对等项结合使用，作为云迁移或长期集成策略的一部分。</span><span class="sxs-lookup"><span data-stu-id="23242-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="23242-106">Microsoft SaaS 混合方案体系结构</span><span class="sxs-lookup"><span data-stu-id="23242-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="23242-107">图 1 显示了适用于 Office 365 的基于 Microsoft SaaS 的混合方案的体系结构。</span><span class="sxs-lookup"><span data-stu-id="23242-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="23242-108">**图 1: Microsoft Office 365 提供基于 SaaS 的混合方案**</span><span class="sxs-lookup"><span data-stu-id="23242-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![适用于 Office 365 的基于 Microsoft SaaS 的混合方案](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
<span data-ttu-id="23242-110">针对体系结构的每一层：</span><span class="sxs-lookup"><span data-stu-id="23242-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="23242-111">应用和方案</span><span class="sxs-lookup"><span data-stu-id="23242-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="23242-112">有多种基于 SaaS 的混合方案，围绕 Office 服务器产品及其对应的 Office 365：</span><span class="sxs-lookup"><span data-stu-id="23242-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="23242-113">与 Exchange Online 结合使用的 Exchange Server（Exchange Server 混合）</span><span class="sxs-lookup"><span data-stu-id="23242-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="23242-114">与 Skype for Business Online 结合使用的 Skype for Business Server 和新的 Cloud PBX 以及云连接器版本方案</span><span class="sxs-lookup"><span data-stu-id="23242-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="23242-115">与 SharePoint Online 结合使用的 SharePoint Server 2016 或 SharePoint Server 2013（多个方案）</span><span class="sxs-lookup"><span data-stu-id="23242-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="23242-116">还有采用本地 Skype for Business Server 的 Exchange Online，一个跨产品的混合方案。</span><span class="sxs-lookup"><span data-stu-id="23242-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="23242-117">标识</span><span class="sxs-lookup"><span data-stu-id="23242-117">Identity</span></span>
    
    <span data-ttu-id="23242-p101">可以包含与本地 Windows Sever AD 进行同步的目录同步。或者，可以配置 Azure AD 来与第三方标识提供程序进行联合。</span><span class="sxs-lookup"><span data-stu-id="23242-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="23242-120">网络</span><span class="sxs-lookup"><span data-stu-id="23242-120">Network</span></span>
    
    <span data-ttu-id="23242-121">由现有的 Internet 管道或通过 Office 365 或 Dynamics 365 的 Microsoft 对等建立的 ExpressRoute 连接组成。</span><span class="sxs-lookup"><span data-stu-id="23242-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="23242-122">本地</span><span class="sxs-lookup"><span data-stu-id="23242-122">On-premises</span></span>
    
    <span data-ttu-id="23242-p102">可由现有的适用于 Exchange、SharePoint 和 Skype for Business 的服务器组成，应将其更新到最新版本。可以将它们与对应的 Office 365 相结合以实现混合方案。</span><span class="sxs-lookup"><span data-stu-id="23242-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="23242-125">设置您自己的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="23242-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="23242-126">Skype for Business 2015 混合</span><span class="sxs-lookup"><span data-stu-id="23242-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="23242-p103">企业 2015年混合的 Skype 允许您在线业务合并现有内部部署与 Skype。一些用户是穴内部部署和某些用户托管联机，但用户共享同一个会话启动协议 (SIP) 域，如 contoso.com。这种混合配置可用于迁移从内部到 Office 365 随着时间的推移在日程上。此外可以使用 Exchange 联机集成业务 2015年的 Skype。</span><span class="sxs-lookup"><span data-stu-id="23242-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="23242-130">**Skype 业务 2015年混合配置图 2:**</span><span class="sxs-lookup"><span data-stu-id="23242-130">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![Skype for Business 2015 混合配置](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
<span data-ttu-id="23242-132">图 2 显示了对于业务 2015年混合配置，Skype 包含内部 Skype 业务 2015年前端池和边缘服务器与通信 Skype 的在线 Office 365 中的业务。</span><span class="sxs-lookup"><span data-stu-id="23242-132">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="23242-133">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="23242-133">For more information, see:</span></span>
  
- [<span data-ttu-id="23242-134">规划业务服务器的 Skype 和 Skype 的在线业务之间的混合连接</span><span class="sxs-lookup"><span data-stu-id="23242-134">Plan hybrid connectivity between Skype for Business Server and Skype for Business Online</span></span>](https://technet.microsoft.com/library/jj205403.aspx)
    
- [<span data-ttu-id="23242-135">受支持的混合配置的 Skype 业务服务器 2015</span><span class="sxs-lookup"><span data-stu-id="23242-135">Supported hybrid configurations for Skype for Business Server 2015</span></span>](https://technet.microsoft.com/library/jj945633.aspx)
    
- [<span data-ttu-id="23242-136">Skype 业务混合的</span><span class="sxs-lookup"><span data-stu-id="23242-136">Skype for Business Hybrid</span></span>](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="23242-137">使用 Skype for Business Server 的云 PBX</span><span class="sxs-lookup"><span data-stu-id="23242-137">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="23242-138">借助使用 Skype for Business Server 的云 PBX，可以将现有的 Skype for Business Server 本地部署转换为具有本地公用电话交换网 (PSTN) 连接的拓扑。 </span><span class="sxs-lookup"><span data-stu-id="23242-138">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="23242-139">**图 3： 云 PBX 与 Skype 业务服务器**</span><span class="sxs-lookup"><span data-stu-id="23242-139">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![使用 Skype for Business Server 的云 PBX](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
<span data-ttu-id="23242-141">图 3 显示了业务服务器配置，包含内部现有的 PBX 或电信网关、 业务服务器，Skype 和 PSTN 连接到 Microsoft 云 PBX 在 Office 365 提供，其中包括业务的 Skype 与 Skype 云 PBX联机。</span><span class="sxs-lookup"><span data-stu-id="23242-141">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="23242-142">组织中处于云中的用户能够接收来自 Microsoft 云的专用交换机 (PBX) 服务，包括信号和语音邮件，但 PSTN 连接（拨号音）通过来自本地 Skype for Business Server 部署的企业语音提供。</span><span class="sxs-lookup"><span data-stu-id="23242-142">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="23242-p104">这是混合配置的一个很好的示例，借助混合配置，可以逐渐迁移到基于云的服务。开始将其移动到 Skype for Business Online 时，可以保留用户的语音功能。可以按照自己的节奏移动用户，要了解的一点是，无论用户身在何处，其语音功能将继续保留。 </span><span class="sxs-lookup"><span data-stu-id="23242-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="23242-146">有关详细信息，请参阅[规划业务服务器和 Skype 的在线业务或 Lync Server 2013 Skype 之间的混合连接](https://technet.microsoft.com/library/jj205403.aspx)。</span><span class="sxs-lookup"><span data-stu-id="23242-146">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span></span>
  
<span data-ttu-id="23242-147">如果还没有现有的 Lync Server 或 Skype for Business Server 部署，可以使用 Skype for Business 云连接器版本，一组通过云 PBX 实现本地 PSTN 连接的封装的虚拟机 (VM)。</span><span class="sxs-lookup"><span data-stu-id="23242-147">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="23242-148">有关详细信息，请参阅[规划业务云连接器版 Skype](https://technet.microsoft.com/library/mt605227.aspx)。</span><span class="sxs-lookup"><span data-stu-id="23242-148">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="23242-149">SharePoint 混合</span><span class="sxs-lookup"><span data-stu-id="23242-149">SharePoint Hybrid</span></span>

<span data-ttu-id="23242-150">SharePoint 混合将 Office 365 中的 SharePoint Online 与本地 SharePoint 场结合使用，实现两全其美的连接体验。</span><span class="sxs-lookup"><span data-stu-id="23242-150">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="23242-151">**图 4: SharePoint 混合配置**</span><span class="sxs-lookup"><span data-stu-id="23242-151">**Figure 4: The SharePoint hybrid configuration**</span></span>

![SharePoint 混合配置](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
<span data-ttu-id="23242-153">图 4 显示了包含与 SharePoint Online Office 365 中通信内部部署 SharePoint 场的 SharePoint 混合配置。</span><span class="sxs-lookup"><span data-stu-id="23242-153">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="23242-154">SharePoint 混合方案：</span><span class="sxs-lookup"><span data-stu-id="23242-154">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="23242-155">业务有关的混合 OneDrive</span><span class="sxs-lookup"><span data-stu-id="23242-155">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="23242-156">混合工作组网站</span><span class="sxs-lookup"><span data-stu-id="23242-156">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [<span data-ttu-id="23242-157">混合网 B2B</span><span class="sxs-lookup"><span data-stu-id="23242-157">Hybrid Extranet B2B</span></span>](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [<span data-ttu-id="23242-158">混合搜索</span><span class="sxs-lookup"><span data-stu-id="23242-158">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [<span data-ttu-id="23242-159">混合配置</span><span class="sxs-lookup"><span data-stu-id="23242-159">Hybrid profiles</span></span>](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [<span data-ttu-id="23242-160">混合选择器</span><span class="sxs-lookup"><span data-stu-id="23242-160">Hybrid Picker</span></span>](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    <span data-ttu-id="23242-161">使用自动进行混合配置的向导可轻松启用混合方案，可从 Office 365 的 SharePoint Online 管理中心执行此操作。</span><span class="sxs-lookup"><span data-stu-id="23242-161">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="23242-162">可扩展的混合应用程序启动程序</span><span class="sxs-lookup"><span data-stu-id="23242-162">Extensible hybrid app launcher</span></span>](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    <span data-ttu-id="23242-163">允许用户在本地 SharePoint 场页面内查看和使用 Office 365 视频以及开发应用和体验。</span><span class="sxs-lookup"><span data-stu-id="23242-163">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="23242-164">除了可扩展的混合应用启动器，所有这些 SharePoint 混合方案均可供 SharePoint 2016 和 SharePoint 2013 用户使用。</span><span class="sxs-lookup"><span data-stu-id="23242-164">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="23242-165">有关详细信息，请参阅[SharePoint 混合](http://hybrid.office.com/sharepoint/)。</span><span class="sxs-lookup"><span data-stu-id="23242-165">For more information, see [SharePoint Hybrid](http://hybrid.office.com/sharepoint/).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="23242-166">Exchange Server 2016 混合</span><span class="sxs-lookup"><span data-stu-id="23242-166">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="23242-167">使用 Exchange Server 2016 混合，可以为在线用户实现 Office 365 中 Exchange Online 的权益，同时本地用户可以继续使用现有的 Exchange Server 基础结构。 </span><span class="sxs-lookup"><span data-stu-id="23242-167">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="23242-168">**图 5： 交换 2016年混合配置**</span><span class="sxs-lookup"><span data-stu-id="23242-168">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Exchange 2016 混合配置](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
<span data-ttu-id="23242-170">图 5 显示了包含内部 Exchange 邮箱服务器与 Exchange 在线保护和 Office 365 中的邮箱进行通信的交换 2016年混合配置。</span><span class="sxs-lookup"><span data-stu-id="23242-170">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="23242-171">一些用户具有本地电子邮件服务器，而一些用户使用 Exchange Online，但所有用户都共享相同的电子邮件地址空间。 </span><span class="sxs-lookup"><span data-stu-id="23242-171">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="23242-172">此混合配置：</span><span class="sxs-lookup"><span data-stu-id="23242-172">This hybrid configuration:</span></span>
  
- <span data-ttu-id="23242-173">利用现有的 Exchange Server 基础结构，而不迁移到 Exchange Online 随着时间的推移在日程上。</span><span class="sxs-lookup"><span data-stu-id="23242-173">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="23242-174">允许你支持远程站点，而无需投资分支办事处基础结构。</span><span class="sxs-lookup"><span data-stu-id="23242-174">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="23242-175">可以在 Office 365 中通过 Exchange Online Protection 路由传入的 Internet 电子邮件。</span><span class="sxs-lookup"><span data-stu-id="23242-175">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="23242-176">满足需要将数据维护在本地中的具有分公司的跨国企业的需求。</span><span class="sxs-lookup"><span data-stu-id="23242-176">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="23242-177">还可以为与其他 Microsoft Office 365 应用程序（包括 Skype for Business Online 和 SharePoint Online）集成此混合配置。</span><span class="sxs-lookup"><span data-stu-id="23242-177">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="23242-178">有关详细信息，请参阅[Exchange Server 混合部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)和[交换混合](http://hybrid.office.com/exchange/)。</span><span class="sxs-lookup"><span data-stu-id="23242-178">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and [Exchange Hybrid](http://hybrid.office.com/exchange/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="23242-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23242-179">See Also</span></span>

[<span data-ttu-id="23242-180">面向企业架构师的 Microsoft 混合云</span><span class="sxs-lookup"><span data-stu-id="23242-180">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="23242-181">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="23242-181">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="23242-182">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="23242-182">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



