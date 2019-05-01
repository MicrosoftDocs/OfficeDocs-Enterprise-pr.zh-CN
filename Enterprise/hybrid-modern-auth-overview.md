---
title: 混合新式身份验证概述和在本地 Skype for business 和 Exchange 服务器上使用它的先决条件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: ''
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: 新式身份验证是标识管理的一种方法, 可提供更安全的用户身份验证和授权。 它可用于本地的 skype for business server 本地和 Exchange server 的混合部署, 以及拆分域 Skype for business 混合。 本文链接到有关先决条件、设置/禁用新式身份验证和一些相关客户端的相关文档 (如 Outlook 和 Skype 客户端) 信息。
ms.openlocfilehash: d8d06a3e2d178f68bcb130228ed1834f4eb878f8
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491398"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a><span data-ttu-id="dd0ab-106">混合新式身份验证概述和在本地 Skype for business 和 Exchange 服务器上使用它的先决条件</span><span class="sxs-lookup"><span data-stu-id="dd0ab-106">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>

<span data-ttu-id="dd0ab-107">新式身份验证是标识管理的一种方法, 可提供更安全的用户身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-107">Modern Authentication is a method of identity management that offers more secure user authentication and authorization.</span></span> <span data-ttu-id="dd0ab-108">它适用于 skype for business server 本地和 Exchange server 本地部署的 Office 365 混合部署, 以及拆分域 Skype for business 混合部署。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-108">It's available for Office 365 hybrid deployments of Skype for Business server on-premises and Exchange server on-premises, as well as, split-domain Skype for Business hybrids.</span></span> <span data-ttu-id="dd0ab-109">本文链接到有关先决条件、设置/禁用新式身份验证和一些相关客户端的相关文档 (如</span><span class="sxs-lookup"><span data-stu-id="dd0ab-109">This article links to related docs about prerequisites, setup/disabling Modern Authentication, and to some of the related client (ex.</span></span> <span data-ttu-id="dd0ab-110">Outlook 和 Skype 客户端) 信息。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-110">Outlook and Skype clients) information.</span></span> 
  
- [<span data-ttu-id="dd0ab-111">什么是新式身份验证？</span><span class="sxs-lookup"><span data-stu-id="dd0ab-111">What is Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [<span data-ttu-id="dd0ab-112">使用新式验证时有哪些变化？</span><span class="sxs-lookup"><span data-stu-id="dd0ab-112">What changes when I use Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [<span data-ttu-id="dd0ab-113">检查您的本地环境的新式身份验证状态</span><span class="sxs-lookup"><span data-stu-id="dd0ab-113">Check the Modern Authentication status of your on-premises environment</span></span>](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [<span data-ttu-id="dd0ab-114">您是否满足新式身份验证先决条件？</span><span class="sxs-lookup"><span data-stu-id="dd0ab-114">Do you meet Modern Authentication prerequisites?</span></span>](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [<span data-ttu-id="dd0ab-115">在开始之前, 我还需要了解哪些信息？</span><span class="sxs-lookup"><span data-stu-id="dd0ab-115">What else do I need to know before I begin?</span></span>](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [<span data-ttu-id="dd0ab-116">新式身份验证 url 列表</span><span class="sxs-lookup"><span data-stu-id="dd0ab-116">List of Modern Authentication URLs</span></span>](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a><span data-ttu-id="dd0ab-117">什么是新式身份验证？</span><span class="sxs-lookup"><span data-stu-id="dd0ab-117">What is Modern Authentication?</span></span>
<span data-ttu-id="dd0ab-118"><a name="BKMK_WhatisModAuth"> </a></span><span class="sxs-lookup"><span data-stu-id="dd0ab-118"></span></span>

<span data-ttu-id="dd0ab-119">在谈论客户端 (例如, 便携式计算机或电话) 和服务器之间的通信时, Microsoft 将使用短语 "新式身份验证"。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-119">When talking about communication between a client (for example, your laptop or your phone) and a server, Microsoft uses the phrase 'Modern authentication'.</span></span>
  
<span data-ttu-id="dd0ab-120">新式身份验证是一种用于身份验证和授权方法组合的伞术语, 以及一些依赖您可能已经熟悉的访问策略的安全措施。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-120">Modern authentication is an umbrella term for a combination of authentication and authorization methods, as well as some security measures that rely on access policies that you may already be familiar with.</span></span> <span data-ttu-id="dd0ab-121">这包括：</span><span class="sxs-lookup"><span data-stu-id="dd0ab-121">It includes:</span></span>
  
- <span data-ttu-id="dd0ab-122">**身份验证方法**: 多因素身份验证;基于客户端证书的身份验证;和 Active Directory 身份验证库 ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx))。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-122">**Authentication methods**: Multi-factor Authentication; Client Certificate-based authentication; and the Active Directory Authentication Library ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx)).</span></span>
    
- <span data-ttu-id="dd0ab-123">**授权方法**: Microsoft 的开放授权 (OAuth) 实现。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-123">**Authorization methods**: Microsoft's implementation of Open Authorization (OAuth).</span></span> 
    
- <span data-ttu-id="dd0ab-124">**条件访问策略**: 移动应用程序管理 (MAM) 和 Azure Active Directory 条件访问。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-124">**Conditional access policies**: Mobile Application Management (MAM) and Azure Active Directory Conditional Access.</span></span> 
    
<span data-ttu-id="dd0ab-125">使用新式验证管理用户标识, 可以让管理员在保护资源和提供更安全的身份管理方法以实现本地 (exchange 和 Skype for business) 时使用多种不同的工具, exchange 混合和 Skype for business 混合/拆分域方案。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-125">Managing user identities with Modern Authentication gives administrators many different tools to use when it comes to securing resources and offers more secure methods of identity management to both on-premises (Exchange and Skype for Business), Exchange hybrid, and Skype for Business hybrid/split-domain scenarios.</span></span>
  
<span data-ttu-id="dd0ab-126">请注意, 因为 skype for business 与 exchange 密切合作, 所以 skype for business 客户端用户将看到的登录行为将受 Exchange 新式验证状态的影响。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-126">Be aware that because Skype for Business works closely with Exchange, the login behaviour Skype for Business client users will see will be effected by the Modern Authentication status of Exchange.</span></span> <span data-ttu-id="dd0ab-127">如果你拥有 Skype for business 拆分域混合, 也会应用此项。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-127">This will also apply if you have a Skype for Business split-domain hybrid.</span></span> <span data-ttu-id="dd0ab-128">此外, 支持使用新式验证的 Skype for business 混合类型通常称为 "拆分域" (在拆分域中, 您同时具有 skype for business Online 和 skype for business 本地, 并且用户同时驻留在这两个位置)。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-128">Also, the type of Skype for Business Hybrid that supports the use of Modern Authentication is often called a 'split-domain' (in a split-domain, you have both Skype for Business Online and Skype for Business on-prem, and users are homed in both locations).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="dd0ab-129">您是否知道, 从2017年8月起, 包括 Skype for business online 和 Exchange online 的所有新的 Office 365 租户都将默认启用新式身份验证？</span><span class="sxs-lookup"><span data-stu-id="dd0ab-129">Did you know that, as of August of 2017, all new Office 365 tenants that include Skype for Business online and Exchange online will have Modern Authentication enabled by default?</span></span> <span data-ttu-id="dd0ab-130">预先存在的租户在其默认 MA 状态中不会发生更改, 但所有新租户都会自动支持您在上面列出的一组已扩展的标识功能。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-130">Pre-existing tenants won't have a change in their default MA state, but all new tenants automatically support the expanded set of identity features you see listed above.</span></span> <span data-ttu-id="dd0ab-131">若要查看适用于 skype for business online 的 MA 状态, 可以使用具有全局管理员凭据的 skype for business online PowerShell。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-131">To check your MA status for Skype for Business online, you can use Skype for Business online PowerShell with Global Admin credentials.</span></span> <span data-ttu-id="dd0ab-132">运行`Get-CsOAuthConfiguration`以检查-ClientADALAuthOverride 的输出。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-132">Run `Get-CsOAuthConfiguration` to check the output of -ClientADALAuthOverride.</span></span> <span data-ttu-id="dd0ab-133">如果-ClientADALAuthOverride 为 "允许", 新式验证已打开。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-133">If -ClientADALAuthOverride is 'Allowed' your Modern Authentication is on.</span></span> 
  
## <a name="what-changes-when-i-use-modern-authentication"></a><span data-ttu-id="dd0ab-134">使用新式验证时有哪些变化？</span><span class="sxs-lookup"><span data-stu-id="dd0ab-134">What changes when I use Modern Authentication?</span></span>
<span data-ttu-id="dd0ab-135"><a name="BKMK_WhatChanges"> </a></span><span class="sxs-lookup"><span data-stu-id="dd0ab-135"></span></span>

<span data-ttu-id="dd0ab-136">将新式验证与本地 Skype for business 或 Exchange server 一起使用时, 仍对本地用户进行*身份*验证, 但*授权*他们访问资源 (如文件或电子邮件) 的情景也会发生变化。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-136">When using Modern Authentication with on-premises Skype for Business or Exchange server, you're still  *authenticating*  users on-premises, but the story of  *authorizing*  their access to resources (like files or emails) changes.</span></span> <span data-ttu-id="dd0ab-137">这就是为什么新式验证是客户端和服务器通信的原因, 在 evoSTS 中配置 MA 结果时所执行的步骤 (Azure AD 使用的安全令牌服务) 被设置为 Skype for business 和本地 Exchange server 的身份验证服务器。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-137">This is why, though Modern Authentication is about client and server communication, the steps taken during configuring MA result in evoSTS (a Security Token Service used by Azure AD) being set as Auth Server for Skype for Business and Exchange server on-premises.</span></span> 
  
<span data-ttu-id="dd0ab-138">对 evoSTS 的更改允许您的内部部署服务器利用 OAuth (令牌颁发) 来授权客户端, 还允许您的本地使用云中常见的安全方法 (如多重身份验证)。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-138">The change to evoSTS allows your on-premises servers to take advantage of OAuth (token issuance) for authorizing your clients, and also lets your on-premises use security methods common in the cloud (like Multi-factor Authentication).</span></span> <span data-ttu-id="dd0ab-139">此外, evoSTS 还会发出令牌, 使用户可以请求访问资源, 而无需在请求中提供其密码。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-139">Additionally, the evoSTS issues tokens that allow users to request access to resources without supplying their password as part of the request.</span></span> <span data-ttu-id="dd0ab-140">无论您的用户驻留在何处 (联机或本地), 无论哪个位置承载所需的资源, EvoSTS 将成为在配置新式身份验证后授权用户和客户端的核心。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-140">No matter where your users are homed (of online or on-premises), and no matter which location hosts the needed resource, EvoSTS will become the core of authorizing users and clients once Modern Authentication is configured.</span></span>
  
<span data-ttu-id="dd0ab-141">下面的示例展示了我的意思。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-141">Here's an example of what I mean.</span></span> <span data-ttu-id="dd0ab-142">如果 Skype for business 客户端需要访问 Exchange server 以代表用户获取日历信息, 则它使用 Active Directory 身份验证库 (ADAL) 执行此操作。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-142">If Skype for Business client needs to access Exchange server to get calendar information on behalf of a user, it uses the Active Directory Authentication Library (ADAL) to do so.</span></span> <span data-ttu-id="dd0ab-143">ADAL 是一个代码库, 旨在使用 OAuth 安全令牌使目录中的安全资源对客户端应用程序可用。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-143">ADAL is a code library designed to make secured resources in your directory available to client applications using OAuth security tokens.</span></span> <span data-ttu-id="dd0ab-144">ADAL 与 OAuth 配合使用, 以验证声明和交换令牌 (而不是密码), 以授予用户对资源的访问权限。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-144">ADAL works with OAuth to verify claims and to exchange tokens (rather than passwords), to grant a user access to a resource.</span></span> <span data-ttu-id="dd0ab-145">过去, 事务中的颁发机构 (如此类) —知道如何验证用户声明并发出所需令牌的服务器可能是本地的安全令牌服务, 甚至是 Active Directory 联合身份验证服务。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-145">In the past, the authority in a transaction like this one -- the server that knows how to validate user claims and issue the needed tokens -- might have been a Security Token Service on-premises, or even Active Directory Federation Services.</span></span> <span data-ttu-id="dd0ab-146">但是, 新式验证在云中将此颁发机构与 azure Active Directory (azure AD) 集中在一起。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-146">However, Modern Authentication centralizes that authority with Azure Active Directory (Azure AD) in the Cloud.</span></span>
  
<span data-ttu-id="dd0ab-147">这也意味着, 尽管您的 Exchange server 和 Skype for business 环境可能完全位于本地, 但授权服务器将处于联机状态, 并且您的本地环境必须能够创建和维护与您的办公室的连接365在云中订阅 (以及你的订阅用作其目录的 Azure Active Directory 实例)。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-147">This also means that even though your Exchange server and Skype for Business environments may be entirely on-premises, the authorizing server will be online, and your on-premises environment must have the ability to create and maintain a connection to your Office 365 subscription in the Cloud (and the Azure Active Directory instance that your subscription uses as its directory).</span></span>
  
<span data-ttu-id="dd0ab-148">不会发生什么变化？</span><span class="sxs-lookup"><span data-stu-id="dd0ab-148">What doesn't change?</span></span> <span data-ttu-id="dd0ab-149">无论你是处于拆分域混合还是使用 Skype for business 和本地 Exchange server, 所有用户都必须先*在本地*进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-149">Whether you're in a split-domain hybrid or using Skype for Business and Exchange server on-premises, all users must first authenticate  *on-premises*  .</span></span> <span data-ttu-id="dd0ab-150">在新式验证的混合实施中, Lyncdiscovery 和自动发现指向您的本地服务器。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-150">In a hybrid implementation of Modern Authentication, Lyncdiscovery and Autodiscovery point to your on-premises server.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="dd0ab-151">如果需要了解 MA 支持的特定 Skype for business 拓扑, 请[在此处记录](https://technet.microsoft.com/en-us/library/mt803262.aspx)。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-151">If you need to know the specific Skype for Business topologies supported with MA, that's [documented right here](https://technet.microsoft.com/en-us/library/mt803262.aspx).</span></span>
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a><span data-ttu-id="dd0ab-152">检查您的本地环境的新式身份验证状态</span><span class="sxs-lookup"><span data-stu-id="dd0ab-152">Check the Modern Authentication status of your on-premises environment</span></span>
<span data-ttu-id="dd0ab-153"><a name="BKMK_CheckStatus"> </a></span><span class="sxs-lookup"><span data-stu-id="dd0ab-153"></span></span>

<span data-ttu-id="dd0ab-154">由于新式验证会更改服务利用 OAuth/S2S 时使用的授权服务器, 你需要了解你的 Skype for business 和 Exchange 环境的新式身份验证是处于打开还是关闭状态。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-154">Because Modern Authentication changes the authorization server used when services leverage OAuth/S2S, you need to know if Modern Authentication is On or Off for your Skype for Business and Exchange environment.</span></span> <span data-ttu-id="dd0ab-155">您可以通过在 PowerShell 中运行`Get-CSOAuthConfiguration`命令, 在内部部署上检查 Exchange 或 Skype for business 服务器上的状态。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-155">You can check the status on your Exchange or Skype for Business servers, on premises, by running the `Get-CSOAuthConfiguration` command in PowerShell.</span></span> <span data-ttu-id="dd0ab-156">如果该命令返回空的 "OAuthServers" 属性, 则会禁用新式验证。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-156">If the command returns an empty 'OAuthServers' property, then Modern Authentication is disabled.</span></span>
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a><span data-ttu-id="dd0ab-157">您是否满足新式身份验证先决条件？</span><span class="sxs-lookup"><span data-stu-id="dd0ab-157">Do you meet Modern Authentication prerequisites?</span></span>

<span data-ttu-id="dd0ab-158">请先验证并检查列表中的这些项, 然后再继续操作:</span><span class="sxs-lookup"><span data-stu-id="dd0ab-158">Verify and check these items off your list before you continue:</span></span>
  
- <span data-ttu-id="dd0ab-159">**Skype for business 特定**</span><span class="sxs-lookup"><span data-stu-id="dd0ab-159">**Skype for Business specific**</span></span>
    
  - <span data-ttu-id="dd0ab-160">所有服务器都必须具有 SFB Server 2015 CU5 或更高版本</span><span class="sxs-lookup"><span data-stu-id="dd0ab-160">All servers must have SFB Server 2015 CU5 or later</span></span>
    
  - <span data-ttu-id="dd0ab-161">**异常**留存分支设备 (SBA) 可以在当前版本上 (基于 Lync 2013)</span><span class="sxs-lookup"><span data-stu-id="dd0ab-161">**Exception** - Survivability Branch Appliance (SBA) can be on the current version (based on Lync 2013)</span></span> 
    
  - <span data-ttu-id="dd0ab-162">您的 SIP 域作为 Office 365 中的联合域添加</span><span class="sxs-lookup"><span data-stu-id="dd0ab-162">Your SIP domain is added as a Federated domain in Office 365</span></span>
    
  - <span data-ttu-id="dd0ab-163">所有 SFB 前端必须具有到 internet 的出站连接, 在[office 125 url 和 IP 的 "Microsoft 365 通用和 Office Online" 部分的行56和365中列出了 office 365 身份验证 url (tcp 443) 和知名证书根 crl (tcp 80)地址范围](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-163">All SFB Front Ends must have connections outbound to the internet, to Office 365 Authentication URLs (TCP 443) and well known certificate root CRLs (TCP 80) listed in Rows 56 and 125 of the 'Microsoft 365 Common and Office Online' section of [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
- <span data-ttu-id="dd0ab-164">**混合 Office 365 环境中的 Skype for business 本地部署**</span><span class="sxs-lookup"><span data-stu-id="dd0ab-164">**Skype for Business on-premises in a hybrid Office 365 environment**</span></span>
  - <span data-ttu-id="dd0ab-165">一个 skype for business server 2019 部署, 其中包含运行 skype for business Server 2019 的所有服务器。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-165">A Skype for Business Server 2019 deployment with all servers running Skype for Business Server 2019.</span></span>
  
  - <span data-ttu-id="dd0ab-166">一个 skype for business server 2015 部署, 其中包含运行 skype for business Server 2015 的所有服务器。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-166">A Skype for Business Server 2015 deployment with all servers running Skype for Business Server 2015.</span></span>
  
  - <span data-ttu-id="dd0ab-167">一种部署, 其最多包含两个不同的服务器版本, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="dd0ab-167">A deployment with a maximum of two different server versions as listed below:</span></span>
  
     - <span data-ttu-id="dd0ab-168">Skype for business server 2015 和 skype for business server 2019</span><span class="sxs-lookup"><span data-stu-id="dd0ab-168">Skype for Business Server 2015 and Skype for Business Server 2019</span></span>
     
  - <span data-ttu-id="dd0ab-169">所有 Skype for business 服务器都必须安装最新的 cummulative 更新, 请参阅[Skype for business Server updates](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates)以查找和管理所有可用更新。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-169">All Skype for Business servers must have the latest cummulative updates installed, see [Skype for Business Server updates](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) to find and manage all available updates.</span></span>
  - <span data-ttu-id="dd0ab-170">混合环境中没有 Lync Server 2010 或2013。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-170">There is no Lync Server 2010 or 2013 in the hybrid environment.</span></span>
    
 <span data-ttu-id="dd0ab-171">**注释**如果 Skype for business 前端服务器使用代理服务器进行 Internet 访问, 则必须在每个前端的 web.config 文件的配置部分中输入所使用的代理服务器 IP 和端口号。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-171">**Note** If your Skype for Business front-end servers use a proxy server for Internet access, the proxy server IP and Port number used must be entered in the configuration section of the web.config file for each front end.</span></span> 
  
- <span data-ttu-id="dd0ab-172">C:\Program Files\Skype for Business Server 2015 \ Web Components\Web ticket\int\web.config</span><span class="sxs-lookup"><span data-stu-id="dd0ab-172">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config</span></span>
    
- <span data-ttu-id="dd0ab-173">C:\Program Files\Skype for Business Server 2015 \ Web Components\Web ticket\ext\web.config</span><span class="sxs-lookup"><span data-stu-id="dd0ab-173">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config</span></span>
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> <span data-ttu-id="dd0ab-174">请务必订阅[Office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)的 RSS 源, 以了解所需 url 的最新列表。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-174">Be sure to subscribe to the RSS feed for [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) to stay current with the latest listings of required URLs.</span></span> 
  
- <span data-ttu-id="dd0ab-175">**特定于 Exchange Server**</span><span class="sxs-lookup"><span data-stu-id="dd0ab-175">**Exchange Server specific**</span></span>
    
  - <span data-ttu-id="dd0ab-176">您使用的是 exchange server 2013 CU19 和 up, 或者是 exchange server 2016 CU8 和 up。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-176">You're using either Exchange server 2013 CU19 and up, or Exchange server 2016 CU8 and up.</span></span>
    
  - <span data-ttu-id="dd0ab-177">环境中没有 Exchange server 2010。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-177">There is no Exchange server 2010 in the environment.</span></span>
    
  - <span data-ttu-id="dd0ab-178">未配置 SSL 卸载。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-178">SSL Offloading is not configured.</span></span> <span data-ttu-id="dd0ab-179">支持 SSL 终止和重新加密。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-179">SSL termination and re-encryption is supported.</span></span>
    
  - <span data-ttu-id="dd0ab-180">在您的环境使用代理服务器基础结构以允许服务器连接到 Internet 时, 请确保所有 Exchange 服务器都在[InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx)属性中定义了代理服务器。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-180">In the event your environment utilizes a proxy server infrastructure to allow servers to connect to the Internet, be sure all Exchange servers have the proxy server defined in the [InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) property.</span></span>
  
- <span data-ttu-id="dd0ab-181">**混合 Office 365 环境中的本地 Exchange Server**</span><span class="sxs-lookup"><span data-stu-id="dd0ab-181">**Exchange Server on-premises in a hybrid Office 365 environment**</span></span>

  - <span data-ttu-id="dd0ab-182">如果使用的是 Exchange server 2013, 则必须至少有一台服务器安装了邮箱和客户端访问服务器角色。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-182">If you are using Exchange server 2013, At least one server must have the Mailbox and Client Access server roles installed.</span></span> <span data-ttu-id="dd0ab-183">虽然可以在单独的服务器上安装邮箱和客户端访问角色, 但强烈建议您在每台服务器上安装这两个角色, 以提供更高的可靠性和改进的性能。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-183">While it is possible to install the Mailbox and Client Access roles on separate servers, we strongly recommend that you install both roles on each server to provide additional reliability and improved performance.</span></span>
  
  - <span data-ttu-id="dd0ab-184">如果您使用的是 Exchange server 2016 或更高版本, 则必须至少有一台服务器安装了邮箱服务器角色。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-184">If you are using Exchange server 2016 or later version, at least one server must have the Mailbox server role installed.</span></span>
  
  - <span data-ttu-id="dd0ab-185">混合环境中没有 Exchange server 2007 或2010。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-185">There is no Exchange server 2007 or 2010 in the Hybrid environment.</span></span>
  
  - <span data-ttu-id="dd0ab-186">所有 Exchange 服务器都必须安装最新的 cummulative 更新, 请参阅将[Exchange 升级到最新累积更新](https://docs.microsoft.com/en-us/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019)以查找和管理所有可用更新。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-186">All Exchange servers must have the latest cummulative updates installed, see [Upgrade Exchange to the latest Cumulative Updates](https://docs.microsoft.com/en-us/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) to find and manage all available updates.</span></span>
    
- <span data-ttu-id="dd0ab-187">**Exchange 客户端和协议要求**</span><span class="sxs-lookup"><span data-stu-id="dd0ab-187">**Exchange client and protocol requirements**</span></span>
  
  - <span data-ttu-id="dd0ab-188">以下客户端支持新式身份验证:</span><span class="sxs-lookup"><span data-stu-id="dd0ab-188">The following clients support modern authentication:</span></span>

  |<span data-ttu-id="dd0ab-189">**客户端**</span><span class="sxs-lookup"><span data-stu-id="dd0ab-189">**Clients**</span></span>|<span data-ttu-id="dd0ab-190">**主要协议**</span><span class="sxs-lookup"><span data-stu-id="dd0ab-190">**Primary Protocol**</span></span>|<span data-ttu-id="dd0ab-191">**Notes**</span><span class="sxs-lookup"><span data-stu-id="dd0ab-191">**Notes**</span></span>|
  |:-----|:-----|:-----|
  |<span data-ttu-id="dd0ab-192">Outlook 2013 和 Outlook 2016</span><span class="sxs-lookup"><span data-stu-id="dd0ab-192">Outlook 2013 and Outlook 2016</span></span>  <br/> |<span data-ttu-id="dd0ab-193">MAPI over HTTP</span><span class="sxs-lookup"><span data-stu-id="dd0ab-193">MAPI over HTTP</span></span>  <br/> |<span data-ttu-id="dd0ab-194">必须在 Exchange 中启用 MAPI over HTTP, 才能将新式验证用于这些客户端 (通常为 Exchange 2013 Service Pack 1 及更高版本启用或设置为启用);有关详细信息, 请参阅[office 2013 和 office 2016 客户端应用的新式身份验证的工作方式](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-194">MAPI over HTTP must be enabled within Exchange in order to leverage modern authentication with these clients (usually enabled or True for new installs of Exchange 2013 Service Pack 1 and above); for more information see [How modern authentication works for Office 2013 and Office 2016 client apps](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).</span></span>  <br/> <span data-ttu-id="dd0ab-195">确保您运行的是所需的最低版本的 Outlook;[有关使用 Windows Installer (MSI) 的 Outlook 版本,](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)请参阅最新更新。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-195">Ensure you are running the minimum required build of Outlook; see [Latest updates for versions of Outlook that use Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).</span></span>  <br/> |
  |<span data-ttu-id="dd0ab-196">Outlook 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="dd0ab-196">Outlook 2016 for Mac</span></span>  <br/> |<span data-ttu-id="dd0ab-197">Exchange Web 服务</span><span class="sxs-lookup"><span data-stu-id="dd0ab-197">Exchange Web Services</span></span>  <br/> |  <br/> |
  |<span data-ttu-id="dd0ab-198">Outlook for iOS 和 Outlook for Android</span><span class="sxs-lookup"><span data-stu-id="dd0ab-198">Outlook for iOS and Android</span></span>  <br/> |  <br/> |<span data-ttu-id="dd0ab-199">有关详细信息, 请参阅[结合使用混合新式身份验证和 Outlook for iOS 和 Outlook for Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-199">See [Using hybrid Modern Authentication with Outlook for iOS and Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) for more information.</span></span>  <br/> |
  |<span data-ttu-id="dd0ab-200">Exchange ActiveSync 客户端 (例如, iOS11 邮件)</span><span class="sxs-lookup"><span data-stu-id="dd0ab-200">Exchange ActiveSync clients (e.g., iOS11 Mail)</span></span>  <br/> |<span data-ttu-id="dd0ab-201">Exchange ActiveSync</span><span class="sxs-lookup"><span data-stu-id="dd0ab-201">Exchange ActiveSync</span></span>  <br/> |<span data-ttu-id="dd0ab-202">对于支持新式身份验证的 Exchange ActiveSync 客户端, 必须重新创建配置文件, 才能从基本身份验证切换到新式身份验证。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-202">For Exchange ActiveSync clients that support modern authentication, you must recreate the profile in order to switch from basic authentication to modern authentication.</span></span>  <br/> |

- <span data-ttu-id="dd0ab-203">**一般先决条件**</span><span class="sxs-lookup"><span data-stu-id="dd0ab-203">**General prerequisites**</span></span>
    
  - <span data-ttu-id="dd0ab-204">如果使用 ADFS, 则应具有 Windows 2012 R2 ADFS 3.0 和更高版本的联合身份验证</span><span class="sxs-lookup"><span data-stu-id="dd0ab-204">If you use ADFS, you should have Windows 2012 R2 ADFS 3.0 and above for federation</span></span>
    
  - <span data-ttu-id="dd0ab-205">您的身份配置是 AAD 连接支持的任何类型 (例如, 密码哈希同步、传递身份验证、Office 365 支持的本地 STS 等)。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-205">Your identity configurations are any of the types supported by AAD Connect (such as password hash sync, pass-through authentication, on-premises STS supported by Office 365, et cetera.)</span></span>
    
  - <span data-ttu-id="dd0ab-206">您配置了 AAD 连接并在用户进行复制和同步时运行正常。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-206">You have AAD Connect configured and functioning for user replication and sync.</span></span>
    
  - <span data-ttu-id="dd0ab-207">您已验证是否使用 Exchange 经典混合拓扑模式在本地和 Office 365 环境中配置混合。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-207">You have verified that hybrid is configured using Exchange Classic Hybrid Topology mode between your on-premises and Office 365 environment.</span></span> <span data-ttu-id="dd0ab-208">Exchange 混合的官方支持声明说, 您必须具有当前 cu 或当前 cu-1。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-208">Official support statement for Exchange hybrid says you must have either current CU or current CU - 1.</span></span>
    
    > [!Note]
    > <span data-ttu-id="dd0ab-209">[混合代理](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)不支持混合新式身份验证。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-209">Hybrid Modern Authentication is not supported with the [Hybrid Agent](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent).</span></span>
    
  - <span data-ttu-id="dd0ab-210">确保本地测试用户和在 Office 365 中托管的混合测试用户可以登录到 skype for business 桌面客户端 (如果要将新式验证用于 skype) 和 Microsoft Outlook (如果需要, 则使用新式验证Exchange)。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-210">Make sure both an on-premises test user, as well as a hybrid test user homed in Office 365, can login to the Skype for Business desktop client (if you want to use Modern Authentication with Skype) and Microsoft Outlook (if you want so use Modern Authentication with Exchange).</span></span>
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a><span data-ttu-id="dd0ab-211">在开始之前, 我还需要了解哪些信息？</span><span class="sxs-lookup"><span data-stu-id="dd0ab-211">What else do I need to know before I begin?</span></span>
<span data-ttu-id="dd0ab-212"><a name="BKMK_Whatelse"> </a></span><span class="sxs-lookup"><span data-stu-id="dd0ab-212"></span></span>

1. <span data-ttu-id="dd0ab-213">内部部署服务器的所有方案都涉及在本地设置新式身份验证 (事实上, 对于 Skype for business, 存在受支持拓扑的列表), 以便负责身份验证和授权的服务器位于 Microsoft 云中 (AAD 的安全令牌服务 (称为 "evoSTS"), 并更新 Azure Active Directory (AAD), 以了解您的本地安装的 Skype for business 或 Exchange 所使用的 url 或命名空间。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-213">All the scenarios for on-premises servers involve setting up Modern Authentication on-premises (in fact, for Skype for Business there is a list of Supported topologies) so that the server responsible for authentication and authorization is in the Microsoft Cloud (AAD's security token service, called 'evoSTS'), and updating Azure Active Directory (AAD) about the URLs or namespaces used by your on-premises installation of either Skype for Business or Exchange.</span></span> <span data-ttu-id="dd0ab-214">因此, 内部部署服务器采用 Microsoft 云依赖关系。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-214">Therefore, on-premises servers take on a Microsoft Cloud dependency.</span></span> <span data-ttu-id="dd0ab-215">采取此操作可能会被视为配置 "混合身份验证"。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-215">Taking this action could be considered configuring 'hybrid auth'.</span></span>
    
2. <span data-ttu-id="dd0ab-216">本文链接到的其他人将帮助您选择受支持的新式身份验证拓扑 (仅对 Skype for business 是必需的) 以及概述了安装步骤的操作方法文章或为 Exchange 本地部署禁用新式身份验证的步骤。和 Skype for business 内部部署。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-216">This article links out to others that will help you choose supported Modern Authentication topologies (necessary only for Skype for Business), and how-to articles that outline the setup steps, or steps to disable Modern Authentication, for Exchange on-premises and Skype for Business on-premises.</span></span> <span data-ttu-id="dd0ab-217">如果您需要在您的服务器环境中使用新式验证的总部, 请在浏览器中 Favourite 此页面。</span><span class="sxs-lookup"><span data-stu-id="dd0ab-217">Favourite this page in your browser if you're going to need a home-base for using Modern Authentication in your server environment.</span></span>
    
## <a name="list-of-modern-authentication-urls"></a><span data-ttu-id="dd0ab-218">新式身份验证 url 列表</span><span class="sxs-lookup"><span data-stu-id="dd0ab-218">List of Modern Authentication URLs</span></span>
<span data-ttu-id="dd0ab-219"><a name="BKMK_URLListforMA"> </a></span><span class="sxs-lookup"><span data-stu-id="dd0ab-219"></span></span>

- [<span data-ttu-id="dd0ab-220">如何将 Exchange Server 本地配置为使用新式验证</span><span class="sxs-lookup"><span data-stu-id="dd0ab-220">How to configure Exchange Server on-premises to use Modern Authentication</span></span>](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="dd0ab-221">新式验证支持的 Skype for business 拓扑</span><span class="sxs-lookup"><span data-stu-id="dd0ab-221">Skype for Business topologies supported with Modern Authentication</span></span>](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [<span data-ttu-id="dd0ab-222">如何配置 Skype for business 本地以使用新式验证</span><span class="sxs-lookup"><span data-stu-id="dd0ab-222">How to configure Skype for Business on-premises to use Modern Authentication</span></span>](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="dd0ab-223">从 Skype for Business 和 Exchange 删除或禁用混合新式验证</span><span class="sxs-lookup"><span data-stu-id="dd0ab-223">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

