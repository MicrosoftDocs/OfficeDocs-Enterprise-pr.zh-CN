---
title: Microsoft SaaS (Office 365) 的混合云方案
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 摘要： 了解混合体系结构和方案的 Microsoft 的 saas 与基于云产品 (Office 365)。
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123409"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="f9c45-103">适用于 Microsoft SaaS (Office 365) 的混合云方案</span><span class="sxs-lookup"><span data-stu-id="f9c45-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="f9c45-104">**摘要：** 了解混合体系结构和方案的 Microsoft 的 saas 与基于云产品 (Office 365)。</span><span class="sxs-lookup"><span data-stu-id="f9c45-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="f9c45-105">将 Exchange、SharePoint，或 Skype for Business 本地部署与其在 Office 365 中的对等项结合使用，作为云迁移或长期集成策略的一部分。</span><span class="sxs-lookup"><span data-stu-id="f9c45-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="f9c45-106">Microsoft SaaS 混合方案体系结构</span><span class="sxs-lookup"><span data-stu-id="f9c45-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="f9c45-107">图 1 显示了适用于 Office 365 的基于 Microsoft SaaS 的混合方案的体系结构。</span><span class="sxs-lookup"><span data-stu-id="f9c45-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="f9c45-108">**图 1：适用于 Office 365 的基于 Microsoft SaaS 的混合方案**</span><span class="sxs-lookup"><span data-stu-id="f9c45-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![适用于 Office 365 的基于 Microsoft SaaS 的混合方案](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="f9c45-110">针对体系结构的每一层：</span><span class="sxs-lookup"><span data-stu-id="f9c45-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="f9c45-111">应用和方案</span><span class="sxs-lookup"><span data-stu-id="f9c45-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="f9c45-112">有多种基于 SaaS 的混合方案，围绕 Office 服务器产品及其对应的 Office 365：</span><span class="sxs-lookup"><span data-stu-id="f9c45-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="f9c45-113">与 Exchange Online 结合使用的 Exchange Server（Exchange Server 混合）</span><span class="sxs-lookup"><span data-stu-id="f9c45-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="f9c45-114">与 Skype for Business Online 结合使用的 Skype for Business Server 和新的 Cloud PBX 以及云连接器版本方案</span><span class="sxs-lookup"><span data-stu-id="f9c45-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="f9c45-115">与 SharePoint Online （多个方案） 结合使用 SharePoint Server 2019、 SharePoint Server 2016 或 SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="f9c45-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="f9c45-116">还有采用本地 Skype for Business Server 的 Exchange Online，一个跨产品的混合方案。</span><span class="sxs-lookup"><span data-stu-id="f9c45-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="f9c45-117">标识</span><span class="sxs-lookup"><span data-stu-id="f9c45-117">Identity</span></span>
    
    <span data-ttu-id="f9c45-p101">可以包含与本地 Windows Sever AD 进行同步的目录同步。或者，可以配置 Azure AD 来与第三方标识提供程序进行联合。</span><span class="sxs-lookup"><span data-stu-id="f9c45-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="f9c45-120">网络</span><span class="sxs-lookup"><span data-stu-id="f9c45-120">Network</span></span>
    
    <span data-ttu-id="f9c45-121">由现有的 Internet 管道或通过 Office 365 或 Dynamics 365 的 Microsoft 对等建立的 ExpressRoute 连接组成。</span><span class="sxs-lookup"><span data-stu-id="f9c45-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="f9c45-122">本地</span><span class="sxs-lookup"><span data-stu-id="f9c45-122">On-premises</span></span>
    
    <span data-ttu-id="f9c45-p102">可由现有的适用于 Exchange、SharePoint 和 Skype for Business 的服务器组成，应将其更新到最新版本。可以将它们与对应的 Office 365 相结合以实现混合方案。</span><span class="sxs-lookup"><span data-stu-id="f9c45-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="f9c45-125">设置 Office 365 开发/测试环境，请参阅[Office 365 测试实验室指南](cloud-adoption-test-lab-guides-tlgs.md)。</span><span class="sxs-lookup"><span data-stu-id="f9c45-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="f9c45-126">Skype 业务混合</span><span class="sxs-lookup"><span data-stu-id="f9c45-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="f9c45-p103">Skype 业务混合允许您业务 online 结合使用 Skype 现有的本地部署。某些用户都驻留在内部部署和一些用户都驻留 online，但用户共享相同的会话初始协议 (SIP) 域，如 contoso.com。您可以使用此混合配置迁移从内部部署到 Office 365 随时间推移，在您的日程安排。此外可以与[Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)集成 for Business 的 Skype。</span><span class="sxs-lookup"><span data-stu-id="f9c45-p103">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="f9c45-131">**图 2： 业务混合配置 Skype**</span><span class="sxs-lookup"><span data-stu-id="f9c45-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![Skype 业务混合配置](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="f9c45-133">图 2 显示了包含业务前端池和边缘服务器与 Skype 业务 online 在 Office 365 中的本地 Skype Skype 业务混合配置。</span><span class="sxs-lookup"><span data-stu-id="f9c45-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="f9c45-134">有关详细信息，请参阅[规划 Skype 业务服务器和 Skype 业务 online 之间的混合连接性](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)。</span><span class="sxs-lookup"><span data-stu-id="f9c45-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="f9c45-135">使用 Skype for Business Server 的云 PBX</span><span class="sxs-lookup"><span data-stu-id="f9c45-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="f9c45-136">云业务服务器 Skype 具有 PBX 可以业务服务器的本地部署到拓扑现有 Skype 转换为本地公共公用电话交换网 (PSTN) 连接。</span><span class="sxs-lookup"><span data-stu-id="f9c45-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="f9c45-137">**图 3：使用 Skype for Business Server 的云 PBX**</span><span class="sxs-lookup"><span data-stu-id="f9c45-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![使用 Skype for Business Server 的云 PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="f9c45-139">图 3 显示了云 PBX 与 Skype 的业务服务器配置中，包含本地现有的 PBX 或电信网关、 Skype 业务服务器和 PSTN 连接到 Office 365，其中包括 Skype for Business 中 Microsoft 云 PBX联机。</span><span class="sxs-lookup"><span data-stu-id="f9c45-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="f9c45-140">组织中处于云中的用户能够接收来自 Microsoft 云的专用交换机 (PBX) 服务，包括信号和语音邮件，但 PSTN 连接（拨号音）通过来自本地 Skype for Business Server 部署的企业语音提供。</span><span class="sxs-lookup"><span data-stu-id="f9c45-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="f9c45-p104">这是混合配置的允许您逐步迁移到基于云的服务极好的示例。在您开始业务 online 将其移至 Skype，您可以保留用户的语音功能。在自己的进度，了解其语音功能将继续无专家那里可以移动用户他们所驻留。</span><span class="sxs-lookup"><span data-stu-id="f9c45-p104">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="f9c45-144">有关详细信息，请参阅[规划 Skype 业务服务器和 Skype 业务 online 之间的混合连接性](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)。</span><span class="sxs-lookup"><span data-stu-id="f9c45-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="f9c45-145">如果还没有现有的 Lync Server 或 Skype for Business Server 部署，可以使用 Skype for Business 云连接器版本，一组通过云 PBX 实现本地 PSTN 连接的封装的虚拟机 (VM)。</span><span class="sxs-lookup"><span data-stu-id="f9c45-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="f9c45-146">有关详细信息，请参阅[规划商务云连接器版的 Skype](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)。</span><span class="sxs-lookup"><span data-stu-id="f9c45-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="f9c45-147">SharePoint 混合</span><span class="sxs-lookup"><span data-stu-id="f9c45-147">SharePoint Hybrid</span></span>

<span data-ttu-id="f9c45-148">SharePoint 混合将 Office 365 中的 SharePoint Online 与本地 SharePoint 场结合使用，实现两全其美的连接体验。</span><span class="sxs-lookup"><span data-stu-id="f9c45-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="f9c45-149">**图 4：SharePoint 混合配置**</span><span class="sxs-lookup"><span data-stu-id="f9c45-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![SharePoint 混合配置](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="f9c45-151">图 4 显示了包含与 Office 365 中 SharePoint Online 进行通信的本地 SharePoint 场的 SharePoint 混合配置。</span><span class="sxs-lookup"><span data-stu-id="f9c45-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="f9c45-152">SharePoint 混合方案：</span><span class="sxs-lookup"><span data-stu-id="f9c45-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="f9c45-153">混合 OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="f9c45-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="f9c45-154">混合 Extranet B2B</span><span class="sxs-lookup"><span data-stu-id="f9c45-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="f9c45-155">混合搜索</span><span class="sxs-lookup"><span data-stu-id="f9c45-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="f9c45-156">混合配置文件</span><span class="sxs-lookup"><span data-stu-id="f9c45-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="f9c45-157">混合选取器</span><span class="sxs-lookup"><span data-stu-id="f9c45-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="f9c45-158">使用自动进行混合配置的向导可轻松启用混合方案，可从 Office 365 的 SharePoint Online 管理中心执行此操作。</span><span class="sxs-lookup"><span data-stu-id="f9c45-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="f9c45-159">可扩展的混合应用启动器</span><span class="sxs-lookup"><span data-stu-id="f9c45-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="f9c45-160">允许用户在本地 SharePoint 场页面内查看和使用 Office 365 视频以及开发应用和体验。</span><span class="sxs-lookup"><span data-stu-id="f9c45-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="f9c45-161">除了可扩展的混合应用启动器，所有这些 SharePoint 混合方案均可供 SharePoint 2016 和 SharePoint 2013 用户使用。</span><span class="sxs-lookup"><span data-stu-id="f9c45-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="f9c45-162">Exchange Server 2016 混合</span><span class="sxs-lookup"><span data-stu-id="f9c45-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="f9c45-163">使用 Exchange Server 2016 混合，可以为在线用户实现 Office 365 中 Exchange Online 的权益，同时本地用户可以继续使用现有的 Exchange Server 基础结构。 </span><span class="sxs-lookup"><span data-stu-id="f9c45-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="f9c45-164">**图 5：Exchange 2016 混合配置**</span><span class="sxs-lookup"><span data-stu-id="f9c45-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Exchange 2016 混合配置](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="f9c45-166">图 5 显示了包含与 Exchange Online Protection 和 Office 365 中的邮箱进行通信的内部部署 Exchange 邮箱服务器的 Exchange 2016 混合配置。</span><span class="sxs-lookup"><span data-stu-id="f9c45-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="f9c45-167">一些用户具有本地电子邮件服务器，而一些用户使用 Exchange Online，但所有用户都共享相同的电子邮件地址空间。 </span><span class="sxs-lookup"><span data-stu-id="f9c45-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="f9c45-168">此混合配置：</span><span class="sxs-lookup"><span data-stu-id="f9c45-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="f9c45-169">利用现有的 Exchange Server 基础结构，同时按照日程安排，在一段时间内迁移到 Exchange Online。


</span><span class="sxs-lookup"><span data-stu-id="f9c45-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="f9c45-170">允许你支持远程站点，而无需投资分支办事处基础结构。</span><span class="sxs-lookup"><span data-stu-id="f9c45-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="f9c45-171">可以在 Office 365 中通过 Exchange Online Protection 路由传入的 Internet 电子邮件。</span><span class="sxs-lookup"><span data-stu-id="f9c45-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="f9c45-172">满足需要将数据维护在本地中的具有分公司的跨国企业的需求。</span><span class="sxs-lookup"><span data-stu-id="f9c45-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="f9c45-173">还可以为与其他 Microsoft Office 365 应用程序（包括 Skype for Business Online 和 SharePoint Online）集成此混合配置。</span><span class="sxs-lookup"><span data-stu-id="f9c45-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="f9c45-174">有关详细信息，请参阅[Exchange Server 混合部署](https://docs.microsoft.com/exchange/exchange-hybrid)。</span><span class="sxs-lookup"><span data-stu-id="f9c45-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f9c45-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9c45-175">See Also</span></span>

[<span data-ttu-id="f9c45-176">面向企业架构师的 Microsoft 混合云</span><span class="sxs-lookup"><span data-stu-id="f9c45-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="f9c45-177">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="f9c45-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

