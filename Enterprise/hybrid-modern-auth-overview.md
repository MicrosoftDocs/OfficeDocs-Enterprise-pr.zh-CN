---
title: 混合现代身份验证概述和使用内部部署 Skype 使用的业务和 Exchange 服务器的先决条件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 8/27/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: 现代身份验证是一种身份管理提供更安全的用户身份验证和授权的方法。它是可用于业务服务器本地和 Exchange server 内部部署，以及业务混合的拆分域 Skype 的 Skype 的混合部署。此文章链接到相关文档有关先决条件，安装程序/禁用现代身份验证，以及某些相关的客户端 （如 Outlook 和 Skype 客户端） 信息。
ms.openlocfilehash: 3d510c6d3e9f8ff885279dc008eeefb5d1014639
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240587"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a><span data-ttu-id="bb48e-106">混合现代身份验证概述和使用内部部署 Skype 使用的业务和 Exchange 服务器的先决条件</span><span class="sxs-lookup"><span data-stu-id="bb48e-106">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>

<span data-ttu-id="bb48e-p102">现代身份验证是一种身份管理提供更安全的用户身份验证和授权的方法。适用于 Office 365 混合部署的 Skype 的业务服务器本地和 Exchange server 内部部署，以及，业务混合的拆分域 Skype 它。此文章链接到相关文档有关先决条件，安装程序/禁用现代身份验证，以及某些相关的客户端 （如 Outlook 和 Skype 客户端） 信息。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p102">Modern Authentication is a method of identity management that offers more secure user authentication and authorization. It's available for Office 365 hybrid deployments of Skype for Business server on-premises and Exchange server on-premises, as well as, split-domain Skype for Business hybrids. This article links to related docs about prerequisites, setup/disabling Modern Authentication, and to some of the related client (ex. Outlook and Skype clients) information.</span></span> 
  
- [<span data-ttu-id="bb48e-111">什么是现代身份验证？</span><span class="sxs-lookup"><span data-stu-id="bb48e-111">What is Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [<span data-ttu-id="bb48e-112">有哪些变化时使用现代身份验证？</span><span class="sxs-lookup"><span data-stu-id="bb48e-112">What changes when I use Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [<span data-ttu-id="bb48e-113">检查本地环境的现代身份验证状态</span><span class="sxs-lookup"><span data-stu-id="bb48e-113">Check the Modern Authentication status of your on-premises environment</span></span>](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [<span data-ttu-id="bb48e-114">您是否满足现代身份验证系统必备组件？</span><span class="sxs-lookup"><span data-stu-id="bb48e-114">Do you meet Modern Authentication prerequisites?</span></span>](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [<span data-ttu-id="bb48e-115">了解在开始之前需要些什么？</span><span class="sxs-lookup"><span data-stu-id="bb48e-115">What else do I need to know before I begin?</span></span>](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [<span data-ttu-id="bb48e-116">现代身份验证 Url 的列表</span><span class="sxs-lookup"><span data-stu-id="bb48e-116">List of Modern Authentication URLs</span></span>](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a><span data-ttu-id="bb48e-117">什么是现代身份验证？</span><span class="sxs-lookup"><span data-stu-id="bb48e-117">What is Modern Authentication?</span></span>
<span data-ttu-id="bb48e-118"><a name="BKMK_WhatisModAuth"> </a></span><span class="sxs-lookup"><span data-stu-id="bb48e-118"></span></span>

<span data-ttu-id="bb48e-119">当谈 （例如，便携式计算机或电话） 的客户端和服务器之间的通信，Microsoft 将使用短语现代身份验证。</span><span class="sxs-lookup"><span data-stu-id="bb48e-119">When talking about communication between a client (for example, your laptop or your phone) and a server, Microsoft uses the phrase 'Modern authentication'.</span></span>
  
<span data-ttu-id="bb48e-p103">现代身份验证是身份验证和授权方法，以及您可能已经熟悉的访问策略所依赖的一些安全措施的组合的总括性术语。它包括：</span><span class="sxs-lookup"><span data-stu-id="bb48e-p103">Modern authentication is an umbrella term for a combination of authentication and authorization methods, as well as some security measures that rely on access policies that you may already be familiar with. It includes:</span></span>
  
- <span data-ttu-id="bb48e-122">**身份验证方法**： 多因素身份验证;客户端基于证书的身份验证;和 Active Directory 身份验证库 ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx))。</span><span class="sxs-lookup"><span data-stu-id="bb48e-122">**Authentication methods**: Multi-factor Authentication; Client Certificate-based authentication; and the Active Directory Authentication Library ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx)).</span></span>
    
- <span data-ttu-id="bb48e-123">**授权方法**： Open Authorization (OAuth) Microsoft 的实现。</span><span class="sxs-lookup"><span data-stu-id="bb48e-123">**Authorization methods**: Microsoft's implementation of Open Authorization (OAuth).</span></span> 
    
- <span data-ttu-id="bb48e-124">**条件访问策略**： 移动应用程序管理 (MAM) 和 Azure Active Directory 条件访问。</span><span class="sxs-lookup"><span data-stu-id="bb48e-124">**Conditional access policies**: Mobile Application Management (MAM) and Azure Active Directory Conditional Access.</span></span> 
    
<span data-ttu-id="bb48e-125">管理现代身份验证的用户标识为管理员提供了许多不同的工具来使用方面保护资源和提供更安全的身份管理这两个内部部署 （Exchange 和 for Business 的 Skype） 方法时，Exchange 混合和 Skype 业务混合/拆分域方案。</span><span class="sxs-lookup"><span data-stu-id="bb48e-125">Managing user identities with Modern Authentication gives administrators many different tools to use when it comes to securing resources and offers more secure methods of identity management to both on-premises (Exchange and Skype for Business), Exchange hybrid, and Skype for Business hybrid/split-domain scenarios.</span></span>
  
<span data-ttu-id="bb48e-p104">请注意，因为与 Exchange 紧密合作 for Business 的 Skype，用户会看到的业务客户端的登录行为 Skype 将会影响 Exchange 的现代身份验证状态。如果您有业务拆分域混合 Skype，也将应用此问题。此外，支持使用现代身份验证的业务混合的 Skype 的类型通常称为拆分域 （拆分域中具有业务 online Skype 和 Skype 的业务上-prem，并且用户都驻留在两个位置）。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p104">Be aware that because Skype for Business works closely with Exchange, the login behaviour Skype for Business client users will see will be effected by the Modern Authentication status of Exchange. This will also apply if you have a Skype for Business split-domain hybrid. Also, the type of Skype for Business Hybrid that supports the use of Modern Authentication is often called a 'split-domain' (in a split-domain, you have both Skype for Business Online and Skype for Business on-prem, and users are homed in both locations).</span></span>
  
 <span data-ttu-id="bb48e-p105">**重要**您知道，从 2017 年 8 月，所有新的 Office 365 租户，包括 for Business 的 Skype online 和 Exchange online 会默认启用的现代身份验证吗？事先租户都不会有更改，在其默认 MA 状态，但新的所有租户自动都支持的扩展您看到上面列出的标识功能集。若要联机检查 for Business 的 Skype MA 状态，您可以用于 Skype 业务 online PowerShell 中使用全局管理员凭据。运行 Get-csoauthconfiguration 检查-ClientADALAuthOverride 的输出。如果-ClientADALAuthOverride 允许您现代的身份验证已打开。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p105">**Important** Did you know that, as of August of 2017, all new Office 365 tenants that include Skype for Business online and Exchange online will have Modern Authentication enabled by default? Pre-existing tenants won't have a change in their default MA state, but all new tenants automatically support the expanded set of identity features you see listed above. To check your MA status for Skype for Business online, you can use Skype for Business online PowerShell with Global Admin credentials. Run ' Get-CsOAuthConfiguration' to check the output of -ClientADALAuthOverride. If -ClientADALAuthOverride is 'Allowed' your Modern Authentication is on.</span></span> 
  
## <a name="what-changes-when-i-use-modern-authentication"></a><span data-ttu-id="bb48e-134">有哪些变化时使用现代身份验证？</span><span class="sxs-lookup"><span data-stu-id="bb48e-134">What changes when I use Modern Authentication?</span></span>
<span data-ttu-id="bb48e-135"><a name="BKMK_WhatChanges"> </a></span><span class="sxs-lookup"><span data-stu-id="bb48e-135"></span></span>

<span data-ttu-id="bb48e-p106">当业务或 Exchange 服务器，使用内部部署 Skype 现代身份验证，您仍*进行身份验证*的用户内部部署，但的*授权*案例资源 （如文件或电子邮件） 更改其访问。尽管现代身份验证，客户端和服务器的通信，evoSTS （安全令牌服务使用的 Azure AD） 中的 configuring MA 结果期间所采取的步骤，这是原因，正在将设置身份验证服务器为 Skype 的业务和 Exchange server 内部部署。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p106">When using Modern Authentication with on-premises Skype for Business or Exchange server, you're still  *authenticating*  users on-premises, but the story of  *authorizing*  their access to resources (like files or emails) changes. This is why, though Modern Authentication is about client and server communication, the steps taken during configuring MA result in evoSTS (a Security Token Service used by Azure AD) being set as Auth Server for Skype for Business and Exchange server on-premises.</span></span> 
  
<span data-ttu-id="bb48e-p107">对 evoSTS 的更改允许在本地服务器的授权客户端，充分利用 OAuth （令牌颁发），并还允许在云中 （如多因素身份验证） 常见您的本地使用安全方法。此外，evoSTS 颁发令牌，允许用户请求资源的访问权限，而无需为请求的一部分提供自己的密码。无论您的用户位于 (的联机或本地)，和哪些位置承载所需的资源，无论 EvoSTS 将成为现代身份验证的配置后，授权用户和客户端的核心。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p107">The change to evoSTS allows your on-premises servers to take advantage of OAuth (token issuance) for authorizing your clients, and also lets your on-premises use security methods common in the cloud (like Multi-factor Authentication). Additionally, the evoSTS issues tokens that allow users to request access to resources without supplying their password as part of the request. No matter where your users are homed (of online or on-premises), and no matter which location hosts the needed resource, EvoSTS will become the core of authorizing users and clients once Modern Authentication is configured.</span></span>
  
<span data-ttu-id="bb48e-p108">下面是一个示例的含义。如果需要访问 Exchange 服务器获取代表用户的日历信息 Skype 业务客户端，它使用 Active Directory 身份验证库 (ADAL) 时才这样。ADAL 代码库旨在使您目录中的受保护的资源可使用 OAuth 安全令牌的客户端应用程序。ADAL 适用于 OAuth 验证声明和 exchange 令牌 （而不是密码），以授予用户对资源的访问。过去，类似如下-知道如何验证用户声明和问题所需的令牌的服务器-事务中的证书颁发机构可能已安全令牌服务内部部署或甚至 Active Directory 联合身份验证服务。但是，现代身份验证集中化与云中的 Azure Active Directory (Azure AD) 的证书颁发机构。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p108">Here's an example of what I mean. If Skype for Business client needs to access Exchange server to get calendar information on behalf of a user, it uses the Active Directory Authentication Library (ADAL) to do so. ADAL is a code library designed to make secured resources in your directory available to client applications using OAuth security tokens. ADAL works with OAuth to verify claims and to exchange tokens (rather than passwords), to grant a user access to a resource. In the past, the authority in a transaction like this one -- the server that knows how to validate user claims and issue the needed tokens -- might have been a Security Token Service on-premises, or even Active Directory Federation Services. However, Modern Authentication centralizes that authority with Azure Active Directory (Azure AD) in the Cloud.</span></span>
  
<span data-ttu-id="bb48e-147">这也意味着，即使您的 Exchange server 和 Skype 的业务环境可能完全内部部署、 授权服务器将处于联机状态，并且您的内部部署环境必须能够创建和维护与您的办公室的连接在云中 （和您的订阅用作其目录的 Azure Active Directory 实例） 的 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="bb48e-147">This also means that even though your Exchange server and Skype for Business environments may be entirely on-premises, the authorizing server will be online, and your on-premises environment must have the ability to create and maintain a connection to your Office 365 subscription in the Cloud (and the Azure Active Directory instance that your subscription uses as its directory).</span></span>
  
<span data-ttu-id="bb48e-p109">什么也不会更改？无论您是在拆分域混合或 Skype 用于业务和 Exchange server 内部部署中，所有用户首先必须进行身份都验证*内部部署*。在现代的身份验证的混合实现，Lyncdiscovery 和自动发现是指向您的本地服务器。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p109">What doesn't change? Whether you're in a split-domain hybrid or using Skype for Business and Exchange server on-premises, all users must first authenticate  *on-premises*  . In a hybrid implementation of Modern Authentication, Lyncdiscovery and Autodiscovery point to your on-premises server.</span></span> 
  
 <span data-ttu-id="bb48e-151">**重要**如果您需要知道业务拓扑支持 MA 的特定 Skype，这是[记录此处](https://technet.microsoft.com/en-us/library/mt803262.aspx)。</span><span class="sxs-lookup"><span data-stu-id="bb48e-151">**Important** If you need to know the specific Skype for Business topologies supported with MA, that's [documented right here](https://technet.microsoft.com/en-us/library/mt803262.aspx).</span></span>
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a><span data-ttu-id="bb48e-152">检查本地环境的现代身份验证状态</span><span class="sxs-lookup"><span data-stu-id="bb48e-152">Check the Modern Authentication status of your on-premises environment</span></span>
<span data-ttu-id="bb48e-153"><a name="BKMK_CheckStatus"> </a></span><span class="sxs-lookup"><span data-stu-id="bb48e-153"></span></span>

<span data-ttu-id="bb48e-p110">因为现代身份验证更改时服务利用 OAuth/S2S 使用授权服务器，您需要知道现代身份验证的业务和 Exchange 环境您 Skype 是否是打开还是关闭。您可以通过在 PowerShell 中运行 Get-csoauthconfiguration 命令检查业务服务器，内部部署 Exchange 或 Skype 上的状态。如果该命令将返回 OAuthServers 属性为空，则会禁用现代身份验证。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p110">Because Modern Authentication changes the authorization server used when services leverage OAuth/S2S, you need to know if Modern Authentication is On or Off for your Skype for Business and Exchange environment. You can check the status on your Exchange or Skype for Business servers, on premises, by running the Get-CSOAuthConfiguration command in PowerShell. If the command returns an empty ' OAuthServers' property, then Modern Authentication is disabled.</span></span>
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a><span data-ttu-id="bb48e-157">您是否满足现代身份验证系统必备组件？</span><span class="sxs-lookup"><span data-stu-id="bb48e-157">Do you meet Modern Authentication prerequisites?</span></span>

<span data-ttu-id="bb48e-158">验证并继续之前检查这些项目关闭您的列表：</span><span class="sxs-lookup"><span data-stu-id="bb48e-158">Verify and check these items off your list before you continue:</span></span>
  
- <span data-ttu-id="bb48e-159">**特定于业务的 Skype**</span><span class="sxs-lookup"><span data-stu-id="bb48e-159">**Skype for Business specific**</span></span>
    
  - <span data-ttu-id="bb48e-160">所有服务器都必须都具有 SFB 服务器 2015 CU5 或更高版本</span><span class="sxs-lookup"><span data-stu-id="bb48e-160">All servers must have SFB Server 2015 CU5 or later</span></span>
    
  - <span data-ttu-id="bb48e-161">**异常**-生存能力 Branch Appliance (SBA) 可以位于当前版本 （基于 Lync 2013）</span><span class="sxs-lookup"><span data-stu-id="bb48e-161">**Exception** - Survivability Branch Appliance (SBA) can be on the current version (based on Lync 2013)</span></span> 
    
  - <span data-ttu-id="bb48e-162">您的 SIP 域添加作为 Office 365 中的联盟域</span><span class="sxs-lookup"><span data-stu-id="bb48e-162">Your SIP domain is added as a Federated domain in Office 365</span></span>
    
  - <span data-ttu-id="bb48e-163">所有 SFB 前端必须都能够连接到 internet、 to Office 365 身份验证 Url (TCP 443) 和已知证书根 Crl (TCP 80) 出站行 1 和 2 的[Office 365 Url 和 IP 的 Office 365 身份验证和标识部分中列出地址范围](https://www.bing.com/search?q=%22Office+365+URLs+and+IP+address+ranges%22&amp;src=IE-SearchBox&amp;FORM=IESR3N&amp;redir=5&amp;itrid=96B6C7422F9F4019B37C1B7FDAF8831E)。</span><span class="sxs-lookup"><span data-stu-id="bb48e-163">All SFB Front Ends must have connections outbound to the internet, to Office 365 Authentication URLs (TCP 443) and well known certificate root CRLs (TCP 80) listed in Rows 1 and 2 of the 'Office 365 authentication and identity' section of [Office 365 URLs and IP address ranges](https://www.bing.com/search?q=%22Office+365+URLs+and+IP+address+ranges%22&amp;src=IE-SearchBox&amp;FORM=IESR3N&amp;redir=5&amp;itrid=96B6C7422F9F4019B37C1B7FDAF8831E).</span></span>
    
 <span data-ttu-id="bb48e-164">**注释**如果您 Skype 业务前端服务器使用代理服务器访问 Internet，必须在每个前端的 web.config 文件的配置部分中输入使用的代理服务器 IP 和端口号。</span><span class="sxs-lookup"><span data-stu-id="bb48e-164">**Note** If your Skype for Business front-end servers use a proxy server for Internet access, the proxy server IP and Port number used must be entered in the configuration section of the web.config file for each front end.</span></span> 
  
- <span data-ttu-id="bb48e-165">Business Server 2015\Web Components\Web ticket\int\web.config 的 c:\program files\Skype</span><span class="sxs-lookup"><span data-stu-id="bb48e-165">c:\program files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config</span></span>
    
- <span data-ttu-id="bb48e-166">Business Server 2015\Web Components\Web ticket\ext\web.config 的 c:\program files\Skype</span><span class="sxs-lookup"><span data-stu-id="bb48e-166">c:\program files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config</span></span>
    
- <span data-ttu-id="bb48e-167">\</system.identityModel.services\></span><span class="sxs-lookup"><span data-stu-id="bb48e-167">\</system.identityModel.services\></span></span>
    
     <span data-ttu-id="bb48e-168">\<system.net\></span><span class="sxs-lookup"><span data-stu-id="bb48e-168">\<system.net\></span></span> 
    
     <span data-ttu-id="bb48e-169">\<请参见\></span><span class="sxs-lookup"><span data-stu-id="bb48e-169">\<defaultProxy\></span></span> 
    
     <span data-ttu-id="bb48e-170">\<代理</span><span class="sxs-lookup"><span data-stu-id="bb48e-170">\<proxy</span></span> 
    
     <span data-ttu-id="bb48e-171">proxyaddress ="http://192.168.100.60:8080"</span><span class="sxs-lookup"><span data-stu-id="bb48e-171">proxyaddress="http://192.168.100.60:8080"</span></span> 
    
     <span data-ttu-id="bb48e-172">bypassonlocal ="true"</span><span class="sxs-lookup"><span data-stu-id="bb48e-172">bypassonlocal="true"</span></span> 
    
     /\> 
    
     <span data-ttu-id="bb48e-173">\</defaultProxy\></span><span class="sxs-lookup"><span data-stu-id="bb48e-173">\</defaultProxy\></span></span> 
    
     <span data-ttu-id="bb48e-174">\</system.net\></span><span class="sxs-lookup"><span data-stu-id="bb48e-174">\</system.net\></span></span> 
    
    <span data-ttu-id="bb48e-175">\</configuration\></span><span class="sxs-lookup"><span data-stu-id="bb48e-175">\</configuration\></span></span>
    
 <span data-ttu-id="bb48e-176">**重要**请务必订阅 RSS 源获取有关[Office 365 Url 和 IP 地址范围](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)可保持最新列表的所需的 Url。</span><span class="sxs-lookup"><span data-stu-id="bb48e-176">**Important** Be sure to subscribe to the RSS feed for [Office 365 URLs and IP address ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to stay current with the latest listings of required URLs.</span></span> 
  
- <span data-ttu-id="bb48e-177">**Exchange Server 特定**</span><span class="sxs-lookup"><span data-stu-id="bb48e-177">**Exchange Server specific**</span></span>
    
  - <span data-ttu-id="bb48e-178">您将任一 Exchange server 2013 CU19 向上，或 Exchange server 2016 CU8 和设置。</span><span class="sxs-lookup"><span data-stu-id="bb48e-178">You're using either Exchange server 2013 CU19 and up, or Exchange server 2016 CU8 and up.</span></span>
    
  - <span data-ttu-id="bb48e-179">没有任何环境中的 Exchange server 2010。</span><span class="sxs-lookup"><span data-stu-id="bb48e-179">There is no Exchange server 2010 in the environment.</span></span>
    
  - <span data-ttu-id="bb48e-p111">未配置 SSL 卸载。支持 SSL 终止并重新加密。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p111">SSL Offloading is not configured. SSL termination and re-encryption is supported.</span></span>
    
  - <span data-ttu-id="bb48e-182">在事件环境使用代理服务器基础结构，若要允许服务器连接到 Internet，确保所有 Exchange 服务器都具有[InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx)属性中定义的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="bb48e-182">In the event your environment utilizes a proxy server infrastructure to allow servers to connect to the Internet, be sure all Exchange servers have the proxy server defined in the [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) property.</span></span>
    
- <span data-ttu-id="bb48e-183">**Exchange 客户端和协议要求**</span><span class="sxs-lookup"><span data-stu-id="bb48e-183">**Exchange client and protocol requirements**</span></span>
  
  - <span data-ttu-id="bb48e-184">以下客户端支持现代身份验证：</span><span class="sxs-lookup"><span data-stu-id="bb48e-184">The following clients support modern authentication:</span></span>

  |<span data-ttu-id="bb48e-185">**客户端**</span><span class="sxs-lookup"><span data-stu-id="bb48e-185">**Clients**</span></span>|<span data-ttu-id="bb48e-186">**主要协议**</span><span class="sxs-lookup"><span data-stu-id="bb48e-186">**Primary Protocol**</span></span>|<span data-ttu-id="bb48e-187">**备注**</span><span class="sxs-lookup"><span data-stu-id="bb48e-187">**Notes**</span></span>|
  |:-----|:-----|:-----|
  |<span data-ttu-id="bb48e-188">Outlook 2013 和 Outlook 2016</span><span class="sxs-lookup"><span data-stu-id="bb48e-188">Outlook 2013 and Outlook 2016</span></span>  <br/> |<span data-ttu-id="bb48e-189">MAPI over HTTP</span><span class="sxs-lookup"><span data-stu-id="bb48e-189">MAPI over HTTP</span></span>  <br/> |<span data-ttu-id="bb48e-190">MAPI over HTTP 必须启用 Exchange 中才能将现代身份验证与这些客户端 （通常启用或 True 新安装的 Exchange 2013 Service Pack 1）; 结合使用有关详细信息，请参阅[如何现代身份验证适用于 Office 2013 和 Office 2016 客户端应用程序](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)。</span><span class="sxs-lookup"><span data-stu-id="bb48e-190">MAPI over HTTP must be enabled within Exchange in order to leverage modern authentication with these clients (usually enabled or True for new installs of Exchange 2013 Service Pack 1 and above); for more information see [How modern authentication works for Office 2013 and Office 2016 client apps](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).</span></span>  <br/> <span data-ttu-id="bb48e-191">确保您正在运行的 Outlook; 最小必需的生成请参阅[最新版本的使用 Windows Installer (MSI) 的 Outlook 更新](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)。</span><span class="sxs-lookup"><span data-stu-id="bb48e-191">Ensure you are running the minimum required build of Outlook; see [Latest updates for versions of Outlook that use Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).</span></span>  <br/> |
  |<span data-ttu-id="bb48e-192">Outlook 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="bb48e-192">Outlook 2016 for Mac</span></span>  <br/> |<span data-ttu-id="bb48e-193">Exchange Web 服务</span><span class="sxs-lookup"><span data-stu-id="bb48e-193">Exchange Web Services</span></span>  <br/> |  <br/> |
  |<span data-ttu-id="bb48e-194">ITPro_R4_Stub_79</span><span class="sxs-lookup"><span data-stu-id="bb48e-194">Outlook for iOS and Android</span></span>  <br/> |  <br/> |<span data-ttu-id="bb48e-195">有关详细信息，请参阅[使用 hybrid 现代 Authentication with Outlook for iOS 和 Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 。</span><span class="sxs-lookup"><span data-stu-id="bb48e-195">See [Using hybrid Modern Authentication with Outlook for iOS and Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) for more information.</span></span>  <br/> |
  |<span data-ttu-id="bb48e-196">Exchange ActiveSync 客户端 （例如，iOS11 邮件）</span><span class="sxs-lookup"><span data-stu-id="bb48e-196">Exchange ActiveSync clients (e.g., iOS11 Mail)</span></span>  <br/> |<span data-ttu-id="bb48e-197">Exchange ActiveSync</span><span class="sxs-lookup"><span data-stu-id="bb48e-197">Exchange ActiveSync</span></span>  <br/> |<span data-ttu-id="bb48e-198">对于支持现代身份验证的 Exchange ActiveSync 客户端，必须以从基本身份验证切换到现代身份验证重新创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="bb48e-198">For Exchange ActiveSync clients that support modern authentication, you must recreate the profile in order to switch from basic authentication to modern authentication.</span></span>  <br/> |

- <span data-ttu-id="bb48e-199">**常规系统必备组件**</span><span class="sxs-lookup"><span data-stu-id="bb48e-199">**General prerequisites**</span></span>
    
  - <span data-ttu-id="bb48e-200">如果您使用 ADFS，您应具有 Windows 2012 R2 ADFS 3.0 及以上的联合身份验证</span><span class="sxs-lookup"><span data-stu-id="bb48e-200">If you use ADFS, you should have Windows 2012 R2 ADFS 3.0 and above for federation</span></span>
    
  - <span data-ttu-id="bb48e-201">标识配置的任何支持 AAD 连接的类型 (如密码哈希同步，传递身份验证，内部部署 STS 支持的 Office 365，et cetera。)</span><span class="sxs-lookup"><span data-stu-id="bb48e-201">Your identity configurations are any of the types supported by AAD Connect (such as password hash sync, pass-through authentication, on-premises STS supported by Office 365, et cetera.)</span></span>
    
  - <span data-ttu-id="bb48e-202">您必须 AAD 连接配置和用户复制和同步正常工作。</span><span class="sxs-lookup"><span data-stu-id="bb48e-202">You have AAD Connect configured and functioning for user replication and sync.</span></span>
    
  - <span data-ttu-id="bb48e-203">您已验证的混合使用您在本地和 Office 365 之间：</span><span class="sxs-lookup"><span data-stu-id="bb48e-203">You have verified that hybrid is working between your on-premises and Office 365:</span></span>
    
  - <span data-ttu-id="bb48e-204">Exchange 混合部署的正式支持语句指出您必须具有当前 CU 或当前 CU-1。</span><span class="sxs-lookup"><span data-stu-id="bb48e-204">Official support statement for Exchange hybrid says you must have either current CU or current CU - 1.</span></span>
    
  - <span data-ttu-id="bb48e-205">确保同时进行内部部署测试用户，以及混合测试用户驻留在 Office 365 中，可以登录到业务桌面客户端 （如果您想要使用与 Skype 的现代的身份验证） Skype 和 Microsoft Outlook （如果需要，以便使用现代身份验证Exchange)。</span><span class="sxs-lookup"><span data-stu-id="bb48e-205">Make sure both an on-premises test user, as well as a hybrid test user homed in Office 365, can login to the Skype for Business desktop client (if you want to use Modern Authentication with Skype) and Microsoft Outlook (if you want so use Modern Authentication with Exchange).</span></span>
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a><span data-ttu-id="bb48e-206">了解在开始之前需要些什么？</span><span class="sxs-lookup"><span data-stu-id="bb48e-206">What else do I need to know before I begin?</span></span>
<span data-ttu-id="bb48e-207"><a name="BKMK_Whatelse"> </a></span><span class="sxs-lookup"><span data-stu-id="bb48e-207"></span></span>

1. <span data-ttu-id="bb48e-p112">在本地服务器的所有方案都涉及现代身份验证本地设置 （实际上的 Skype for Business 没有受支持的拓扑的列表） 以便负责身份验证和授权的服务器处于 Microsoft 云 （AAD 的安全令牌服务，名为 evoSTS），并更新 Azure Active Directory (AAD) 有关的 Url 或本地安装的任一 Skype 适用于商务或 Exchange 使用的命名空间。因此，在本地服务器承担 Microsoft 云依赖关系。执行此操作无法视为配置混合身份验证。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p112">All the scenarios for on-premises servers involve setting up Modern Authentication on-premises (in fact, for Skype for Business there is a list of Supported topologies) so that the server responsible for authentication and authorization is in the Microsoft Cloud (AAD's security token service, called 'evoSTS'), and updating Azure Active Directory (AAD) about the URLs or namespaces used by your on-premises installation of either Skype for Business or Exchange. Therefore, on-premises servers take on a Microsoft Cloud dependency. Taking this action could be considered configuring 'hybrid auth'.</span></span>
    
2. <span data-ttu-id="bb48e-p113">此文章链接出到其他人将帮助您选择的支持 （仅对业务的 Skype 有必要），现代的身份验证拓扑和操作方法文章的大纲安装步骤，或步骤禁用现代的身份验证的 Exchange 内部部署和 for Business 的 Skype 本地。收藏此页面在浏览器中如果您将需要主页库 server 环境中使用现代的身份验证。</span><span class="sxs-lookup"><span data-stu-id="bb48e-p113">This article links out to others that will help you choose supported Modern Authentication topologies (necessary only for Skype for Business), and how-to articles that outline the setup steps, or steps to disable Modern Authentication, for Exchange on-premises and Skype for Business on-premises. Favourite this page in your browser if you're going to need a home-base for using Modern Authentication in your server environment.</span></span>
    
## <a name="list-of-modern-authentication-urls"></a><span data-ttu-id="bb48e-213">现代身份验证 Url 的列表</span><span class="sxs-lookup"><span data-stu-id="bb48e-213">List of Modern Authentication URLs</span></span>
<span data-ttu-id="bb48e-214"><a name="BKMK_URLListforMA"> </a></span><span class="sxs-lookup"><span data-stu-id="bb48e-214"></span></span>

- [<span data-ttu-id="bb48e-215">如何配置 Exchange Server 内部部署用于现代身份验证</span><span class="sxs-lookup"><span data-stu-id="bb48e-215">How to configure Exchange Server on-premises to use Modern Authentication</span></span>](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="bb48e-216">Skype 的业务拓扑支持现代身份验证</span><span class="sxs-lookup"><span data-stu-id="bb48e-216">Skype for Business topologies supported with Modern Authentication</span></span>](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [<span data-ttu-id="bb48e-217">如何配置用于业务本地的 Skype 用于现代身份验证</span><span class="sxs-lookup"><span data-stu-id="bb48e-217">How to configure Skype for Business on-premises to use Modern Authentication</span></span>](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="bb48e-218">从 Skype for Business 和 Exchange 删除或禁用混合新式验证</span><span class="sxs-lookup"><span data-stu-id="bb48e-218">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

