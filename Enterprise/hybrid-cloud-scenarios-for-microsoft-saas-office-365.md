---
title: Microsoft SaaS (Office 365) 的混合云方案
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
description: 摘要： 了解混合体系结构和方案的 Microsoft 的 saas 与基于云产品 (Office 365)。
ms.openlocfilehash: 53187d53b55eedf1fca4f0b98e34accf454c67df
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915587"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="41b44-103">适用于 Microsoft SaaS (Office 365) 的混合云方案</span><span class="sxs-lookup"><span data-stu-id="41b44-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="41b44-104">**摘要：** 了解混合体系结构和方案的 Microsoft 的 saas 与基于云产品 (Office 365)。</span><span class="sxs-lookup"><span data-stu-id="41b44-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="41b44-105">将 Exchange、SharePoint，或 Skype for Business 本地部署与其在 Office 365 中的对等项结合使用，作为云迁移或长期集成策略的一部分。</span><span class="sxs-lookup"><span data-stu-id="41b44-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="41b44-106">Microsoft SaaS 混合方案体系结构</span><span class="sxs-lookup"><span data-stu-id="41b44-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="41b44-107">图 1 显示了适用于 Office 365 的基于 Microsoft SaaS 的混合方案的体系结构。</span><span class="sxs-lookup"><span data-stu-id="41b44-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="41b44-108">**图 1：适用于 Office 365 的基于 Microsoft SaaS 的混合方案**</span><span class="sxs-lookup"><span data-stu-id="41b44-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![适用于 Office 365 的基于 Microsoft SaaS 的混合方案](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="41b44-110">针对体系结构的每一层：</span><span class="sxs-lookup"><span data-stu-id="41b44-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="41b44-111">应用和方案</span><span class="sxs-lookup"><span data-stu-id="41b44-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="41b44-112">有多种基于 SaaS 的混合方案，围绕 Office 服务器产品及其对应的 Office 365：</span><span class="sxs-lookup"><span data-stu-id="41b44-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="41b44-113">与 Exchange Online 结合使用的 Exchange Server（Exchange Server 混合）</span><span class="sxs-lookup"><span data-stu-id="41b44-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="41b44-114">与 Skype for Business Online 结合使用的 Skype for Business Server 和新的 Cloud PBX 以及云连接器版本方案</span><span class="sxs-lookup"><span data-stu-id="41b44-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="41b44-115">与 SharePoint Online 结合使用的 SharePoint Server 2016 或 SharePoint Server 2013（多个方案）</span><span class="sxs-lookup"><span data-stu-id="41b44-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="41b44-116">还有采用本地 Skype for Business Server 的 Exchange Online，一个跨产品的混合方案。</span><span class="sxs-lookup"><span data-stu-id="41b44-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="41b44-117">标识</span><span class="sxs-lookup"><span data-stu-id="41b44-117">Identity</span></span>
    
    <span data-ttu-id="41b44-p101">可以包含与本地 Windows Sever AD 进行同步的目录同步。或者，可以配置 Azure AD 来与第三方标识提供程序进行联合。</span><span class="sxs-lookup"><span data-stu-id="41b44-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="41b44-120">网络</span><span class="sxs-lookup"><span data-stu-id="41b44-120">Network</span></span>
    
    <span data-ttu-id="41b44-121">由现有的 Internet 管道或通过 Office 365 或 Dynamics 365 的 Microsoft 对等建立的 ExpressRoute 连接组成。</span><span class="sxs-lookup"><span data-stu-id="41b44-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="41b44-122">本地</span><span class="sxs-lookup"><span data-stu-id="41b44-122">On-premises</span></span>
    
    <span data-ttu-id="41b44-p102">可由现有的适用于 Exchange、SharePoint 和 Skype for Business 的服务器组成，应将其更新到最新版本。可以将它们与对应的 Office 365 相结合以实现混合方案。</span><span class="sxs-lookup"><span data-stu-id="41b44-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="41b44-125">设置你自己的 [Office 365 dev/test environment](office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="41b44-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="41b44-126">Skype for Business 2015 混合</span><span class="sxs-lookup"><span data-stu-id="41b44-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="41b44-p103">业务 2015年混合的 Skype 可以将现有的本地部署与 Skype 业务 online 结合起来。某些用户都驻留在内部部署和一些用户都驻留 online，但用户共享相同的会话初始协议 (SIP) 域，如 contoso.com。您可以使用此混合配置迁移从内部部署到 Office 365 随时间推移，在您的日程安排。此外可以与 Exchange Online 集成业务 2015年的 Skype。</span><span class="sxs-lookup"><span data-stu-id="41b44-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="41b44-131">**图 2：Skype for Business 2015 混合配置**</span><span class="sxs-lookup"><span data-stu-id="41b44-131">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![Skype for Business 2015 混合配置](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="41b44-133">图 2 显示了包含业务 2015年前端池和边缘服务器与 Skype 业务 online 在 Office 365 中的本地 Skype Skype 业务 2015年混合配置。</span><span class="sxs-lookup"><span data-stu-id="41b44-133">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="41b44-134">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="41b44-134">For more information, see:</span></span>
  
- [<span data-ttu-id="41b44-135">规划业务服务器 Skype 和 Skype 业务 online 之间的混合连接性</span><span class="sxs-lookup"><span data-stu-id="41b44-135">Plan hybrid connectivity between Skype for Business Server and Skype for Business Online</span></span>](https://technet.microsoft.com/library/jj205403.aspx)
    
- [<span data-ttu-id="41b44-136">支持的混合配置的 Skype 业务服务器 2015</span><span class="sxs-lookup"><span data-stu-id="41b44-136">Supported hybrid configurations for Skype for Business Server 2015</span></span>](https://technet.microsoft.com/library/jj945633.aspx)
    
- [<span data-ttu-id="41b44-137">Skype 业务混合</span><span class="sxs-lookup"><span data-stu-id="41b44-137">Skype for Business Hybrid</span></span>](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="41b44-138">使用 Skype for Business Server 的云 PBX</span><span class="sxs-lookup"><span data-stu-id="41b44-138">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="41b44-139">借助使用 Skype for Business Server 的云 PBX，可以将现有的 Skype for Business Server 本地部署转换为具有本地公用电话交换网 (PSTN) 连接的拓扑。 </span><span class="sxs-lookup"><span data-stu-id="41b44-139">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="41b44-140">**图 3：使用 Skype for Business Server 的云 PBX**</span><span class="sxs-lookup"><span data-stu-id="41b44-140">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![使用 Skype for Business Server 的云 PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="41b44-142">图 3 显示了云 PBX 与 Skype 的业务服务器配置中，包含本地现有的 PBX 或电信网关、 Skype 业务服务器和 PSTN 连接到 Office 365，其中包括 Skype for Business 中 Microsoft 云 PBX联机。</span><span class="sxs-lookup"><span data-stu-id="41b44-142">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="41b44-143">组织中处于云中的用户能够接收来自 Microsoft 云的专用交换机 (PBX) 服务，包括信号和语音邮件，但 PSTN 连接（拨号音）通过来自本地 Skype for Business Server 部署的企业语音提供。</span><span class="sxs-lookup"><span data-stu-id="41b44-143">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="41b44-p104">这是混合配置的一个很好的示例，借助混合配置，可以逐渐迁移到基于云的服务。开始将其移动到 Skype for Business Online 时，可以保留用户的语音功能。可以按照自己的节奏移动用户，要了解的一点是，无论用户身在何处，其语音功能将继续保留。 </span><span class="sxs-lookup"><span data-stu-id="41b44-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="41b44-147">有关详细信息，请参阅[规划 Skype 业务服务器和 Skype 业务 Online 或 Lync Server 2013 之间的混合连接性](https://technet.microsoft.com/library/jj205403.aspx)。</span><span class="sxs-lookup"><span data-stu-id="41b44-147">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span></span>
  
<span data-ttu-id="41b44-148">如果还没有现有的 Lync Server 或 Skype for Business Server 部署，可以使用 Skype for Business 云连接器版本，一组通过云 PBX 实现本地 PSTN 连接的封装的虚拟机 (VM)。</span><span class="sxs-lookup"><span data-stu-id="41b44-148">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="41b44-149">有关详细信息，请参阅[规划商务云连接器版的 Skype](https://technet.microsoft.com/library/mt605227.aspx)。</span><span class="sxs-lookup"><span data-stu-id="41b44-149">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="41b44-150">SharePoint 混合</span><span class="sxs-lookup"><span data-stu-id="41b44-150">SharePoint Hybrid</span></span>

<span data-ttu-id="41b44-151">SharePoint 混合将 Office 365 中的 SharePoint Online 与本地 SharePoint 场结合使用，实现两全其美的连接体验。</span><span class="sxs-lookup"><span data-stu-id="41b44-151">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="41b44-152">**图 4：SharePoint 混合配置**</span><span class="sxs-lookup"><span data-stu-id="41b44-152">**Figure 4: The SharePoint hybrid configuration**</span></span>

![SharePoint 混合配置](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="41b44-154">图 4 显示了包含与 Office 365 中 SharePoint Online 进行通信的本地 SharePoint 场的 SharePoint 混合配置。</span><span class="sxs-lookup"><span data-stu-id="41b44-154">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="41b44-155">SharePoint 混合方案：</span><span class="sxs-lookup"><span data-stu-id="41b44-155">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="41b44-156">混合 OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="41b44-156">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="41b44-157">混合工作组网站</span><span class="sxs-lookup"><span data-stu-id="41b44-157">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [<span data-ttu-id="41b44-158">混合 Extranet B2B</span><span class="sxs-lookup"><span data-stu-id="41b44-158">Hybrid Extranet B2B</span></span>](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [<span data-ttu-id="41b44-159">混合搜索</span><span class="sxs-lookup"><span data-stu-id="41b44-159">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [<span data-ttu-id="41b44-160">混合配置文件</span><span class="sxs-lookup"><span data-stu-id="41b44-160">Hybrid profiles</span></span>](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [<span data-ttu-id="41b44-161">混合选取器</span><span class="sxs-lookup"><span data-stu-id="41b44-161">Hybrid Picker</span></span>](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    <span data-ttu-id="41b44-162">使用自动进行混合配置的向导可轻松启用混合方案，可从 Office 365 的 SharePoint Online 管理中心执行此操作。</span><span class="sxs-lookup"><span data-stu-id="41b44-162">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="41b44-163">可扩展的混合应用启动器</span><span class="sxs-lookup"><span data-stu-id="41b44-163">Extensible hybrid app launcher</span></span>](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    <span data-ttu-id="41b44-164">允许用户在本地 SharePoint 场页面内查看和使用 Office 365 视频以及开发应用和体验。</span><span class="sxs-lookup"><span data-stu-id="41b44-164">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="41b44-165">除了可扩展的混合应用启动器，所有这些 SharePoint 混合方案均可供 SharePoint 2016 和 SharePoint 2013 用户使用。</span><span class="sxs-lookup"><span data-stu-id="41b44-165">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="41b44-166">有关详细信息，请参阅[SharePoint 混合](http://hybrid.office.com/sharepoint/)。</span><span class="sxs-lookup"><span data-stu-id="41b44-166">For more information, see [SharePoint Hybrid](http://hybrid.office.com/sharepoint/).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="41b44-167">Exchange Server 2016 混合</span><span class="sxs-lookup"><span data-stu-id="41b44-167">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="41b44-168">使用 Exchange Server 2016 混合，可以为在线用户实现 Office 365 中 Exchange Online 的权益，同时本地用户可以继续使用现有的 Exchange Server 基础结构。 </span><span class="sxs-lookup"><span data-stu-id="41b44-168">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="41b44-169">**图 5：Exchange 2016 混合配置**</span><span class="sxs-lookup"><span data-stu-id="41b44-169">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Exchange 2016 混合配置](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="41b44-171">图 5 显示了包含与 Exchange Online Protection 和 Office 365 中的邮箱进行通信的内部部署 Exchange 邮箱服务器的 Exchange 2016 混合配置。</span><span class="sxs-lookup"><span data-stu-id="41b44-171">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="41b44-172">一些用户具有本地电子邮件服务器，而一些用户使用 Exchange Online，但所有用户都共享相同的电子邮件地址空间。 </span><span class="sxs-lookup"><span data-stu-id="41b44-172">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="41b44-173">此混合配置：</span><span class="sxs-lookup"><span data-stu-id="41b44-173">This hybrid configuration:</span></span>
  
- <span data-ttu-id="41b44-174">利用现有的 Exchange Server 基础结构，同时按照日程安排，在一段时间内迁移到 Exchange Online。


</span><span class="sxs-lookup"><span data-stu-id="41b44-174">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="41b44-175">允许你支持远程站点，而无需投资分支办事处基础结构。</span><span class="sxs-lookup"><span data-stu-id="41b44-175">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="41b44-176">可以在 Office 365 中通过 Exchange Online Protection 路由传入的 Internet 电子邮件。</span><span class="sxs-lookup"><span data-stu-id="41b44-176">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="41b44-177">满足需要将数据维护在本地中的具有分公司的跨国企业的需求。</span><span class="sxs-lookup"><span data-stu-id="41b44-177">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="41b44-178">还可以为与其他 Microsoft Office 365 应用程序（包括 Skype for Business Online 和 SharePoint Online）集成此混合配置。</span><span class="sxs-lookup"><span data-stu-id="41b44-178">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="41b44-179">有关详细信息，请参阅[Exchange Server 混合部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)和[Exchange 混合部署](http://hybrid.office.com/exchange/)。</span><span class="sxs-lookup"><span data-stu-id="41b44-179">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and [Exchange Hybrid](http://hybrid.office.com/exchange/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="41b44-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41b44-180">See Also</span></span>

[<span data-ttu-id="41b44-181">面向企业架构师的 Microsoft 混合云</span><span class="sxs-lookup"><span data-stu-id="41b44-181">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="41b44-182">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="41b44-182">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="41b44-183">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="41b44-183">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



