---
title: Office 365 的会话超时
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
description: 会话超时用于平衡 securtiy 和轻松访问 Office 365 客户端应用程序中。
ms.openlocfilehash: dda13f280149c969354ae1f0eac336f1d8ed23e7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539657"
---
# <a name="session-timeouts-for-office-365"></a><span data-ttu-id="c64b3-103">Office 365 的会话超时</span><span class="sxs-lookup"><span data-stu-id="c64b3-103">Session timeouts for Office 365</span></span>

<span data-ttu-id="c64b3-104">会话生存期是 Office 365 身份验证的重要组成部分，平衡安全性和次数，提示用户输入其凭据的重要组成部分。</span><span class="sxs-lookup"><span data-stu-id="c64b3-104">Session lifetimes are an important part of authentication for Office 365 and are an important component in balancing security and the number of times users are prompted for their credentials.</span></span>
  
## <a name="session-times-for-office-365-services"></a><span data-ttu-id="c64b3-105">Office 365 服务的会话时间</span><span class="sxs-lookup"><span data-stu-id="c64b3-105">Session times for Office 365 services</span></span>

<span data-ttu-id="c64b3-p101">当用户在任何 Office 365 web 应用程序或移动应用程序进行身份验证时，建立会话。会话期间，用户不需要重新进行身份验证。当用户处于非活动状态，它们关闭浏览器或选项卡上，或其身份验证令牌其他原因已被重置其密码过期时，可以终止会话。Office 365 服务具有不同的会话超时，以与每个服务的典型用法对应。</span><span class="sxs-lookup"><span data-stu-id="c64b3-p101">When users authenticate in any of the Office 365 web apps or mobile apps, a session is established. For the duration of the session, users won't need to re-authenticate. Sessions can expire when users are inactive, when they close the browser or tab, or when their authentication token expires for other reasons such as when their password has been reset. The Office 365 services have different session timeouts to correspond with the typical use of each service.</span></span>
  
<span data-ttu-id="c64b3-110">下表列出了为 Office 365 服务的会话生存期：</span><span class="sxs-lookup"><span data-stu-id="c64b3-110">The following table lists the session lifetimes for Office 365 services:</span></span>
  
|<span data-ttu-id="c64b3-111">**Office 365 服务**</span><span class="sxs-lookup"><span data-stu-id="c64b3-111">**Office 365 service**</span></span>|<span data-ttu-id="c64b3-112">**会话超时**</span><span class="sxs-lookup"><span data-stu-id="c64b3-112">**Session timeout**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c64b3-113">Office 365 管理中心</span><span class="sxs-lookup"><span data-stu-id="c64b3-113">Office 365 Admin center</span></span>  <br/> |<span data-ttu-id="c64b3-114">要求您提供凭据管理中心的每隔 8 小时。</span><span class="sxs-lookup"><span data-stu-id="c64b3-114">You are asked to provide credentials for the admin center every 8 hours.</span></span>  <br/> |
|<span data-ttu-id="c64b3-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c64b3-115">SharePoint Online</span></span>  <br/> |<span data-ttu-id="c64b3-p102">5 天的非活动用户只要选择**使我保持登录**。如果用户访问 SharePoint Online 再次从以前登录过去 24 或几个小时后，超时值重置为 5 天。</span><span class="sxs-lookup"><span data-stu-id="c64b3-p102">5 days of inactivity as long as the users chooses **Keep me signed in**. If the user accesses SharePoint Online again after 24 or more hours have passed from the previous sign-in, the timeout value is reset to 5 days.  </span></span><br/> |
|<span data-ttu-id="c64b3-118">Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="c64b3-118">Outlook Web App</span></span>  <br/> |<span data-ttu-id="c64b3-119">6 小时。</span><span class="sxs-lookup"><span data-stu-id="c64b3-119">6 hours.</span></span>  <br/> <span data-ttu-id="c64b3-120">使用[Set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet 中_ActivityBasedAuthenticationTimeoutInterval_参数，您可以更改此值。</span><span class="sxs-lookup"><span data-stu-id="c64b3-120">You can change this value by using the  _ActivityBasedAuthenticationTimeoutInterval_ parameter in the [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet.</span></span>  <br/> |
|<span data-ttu-id="c64b3-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c64b3-121">Azure Active Directory</span></span>  <br/> <span data-ttu-id="c64b3-122">（与已启用的现代身份验证一起使用的 Office 2013 Windows 客户端）</span><span class="sxs-lookup"><span data-stu-id="c64b3-122">(Used by Office 2013 Windows clients with modern authentication enabled)</span></span>  <br/> | <span data-ttu-id="c64b3-p103">现代身份验证使用访问令牌和刷新令牌授予用户对使用 Azure Active Directory 的 Office 365 资源的访问。访问令牌是 JSON Web 令牌提供身份验证成功后，并且是有效 1 小时。此外提供了与较长的生存期刷新令牌。访问令牌过期后，Office 客户端使用有效刷新令牌获取新的访问令牌。此交换成功如果用户的初始身份验证，仍然有效。</span><span class="sxs-lookup"><span data-stu-id="c64b3-p103">Modern authentication uses access tokens and refresh tokens to grant user access to Office 365 resources using Azure Active Directory. An access token is a JSON Web Token provided after a successful authentication and is valid for 1 hour. A refresh token with a longer lifetime is also provided. When access tokens expire, Office clients use a valid refresh token to obtain a new access token. This exchange succeeds if the user's initial authentication is still valid.</span></span>  <br/>  <span data-ttu-id="c64b3-128">刷新令牌的有效期为 90 天，并且与连续使用，可以在有效，直到吊销。</span><span class="sxs-lookup"><span data-stu-id="c64b3-128">Refresh tokens are valid for 90 days, and with continuous use, they can be valid until revoked.</span></span>  <br/>  <span data-ttu-id="c64b3-129">刷新令牌可以如失效由几个事件：</span><span class="sxs-lookup"><span data-stu-id="c64b3-129">Refresh tokens can be invalidated by several events such as :</span></span>  <br/>  <span data-ttu-id="c64b3-130">用户的密码已更改后，刷新令牌颁发。</span><span class="sxs-lookup"><span data-stu-id="c64b3-130">User's password has changed since the refresh token was issued.</span></span>  <br/>  <span data-ttu-id="c64b3-131">管理员可以应用到用户尝试访问的资源限制访问其条件访问策略。</span><span class="sxs-lookup"><span data-stu-id="c64b3-131">An administrator can apply conditional access policies which restrict access to the resource the user is trying to access.</span></span>  <br/> |
|<span data-ttu-id="c64b3-132">SharePoint 和 OneDrive 移动应用程序 Android、 iOS 和 Windows 10</span><span class="sxs-lookup"><span data-stu-id="c64b3-132">SharePoint and OneDrive mobile apps for Android, iOS, and Windows 10</span></span>  <br/> |<span data-ttu-id="c64b3-p104">访问令牌的默认生存时间为 1 小时。刷新令牌的默认最大不活动时间是 90 天。</span><span class="sxs-lookup"><span data-stu-id="c64b3-p104">The default lifetime for the access token is 1 hour. The default max inactive time of the refresh token is 90 days.  </span></span><br/> [<span data-ttu-id="c64b3-135">了解有关令牌以及如何配置令牌生存期</span><span class="sxs-lookup"><span data-stu-id="c64b3-135">Learn more about tokens and how to configure token lifetimes</span></span>](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> <span data-ttu-id="c64b3-136">要取消刷新令牌，您可以重置用户的 Office 365 密码</span><span class="sxs-lookup"><span data-stu-id="c64b3-136">To revoke the refresh token, you can reset the user's Office 365 password</span></span>  <br/> |
|<span data-ttu-id="c64b3-137">Yammer 与 Office 365 登录</span><span class="sxs-lookup"><span data-stu-id="c64b3-137">Yammer with Office 365 Sign-In</span></span>  <br/> |<span data-ttu-id="c64b3-p105">在浏览器的生存期。如果用户关闭浏览器，并在新浏览器中访问 Yammer，Yammer 重新将验证它们与 Office 365。如果用户使用第三方浏览器的缓存 cookie，它们可能不需要重新时其重新打开浏览器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c64b3-p105">Lifetime of the browser. If users close the browser and access Yammer in a new browser, Yammer will re-authenticate them with Office 365. If users use third-party browsers that cache cookies, they may not need to re-authenticate when they reopen the browser.  </span></span><br/> <span data-ttu-id="c64b3-141">> [!NOTE]> 这是仅供使用 Office 365 登录的 Yammer 网络。</span><span class="sxs-lookup"><span data-stu-id="c64b3-141">> [!NOTE]> This is valid only for networks using Office 365 Sign-In for Yammer.</span></span>           |
   

