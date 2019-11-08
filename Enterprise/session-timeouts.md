---
title: Office 365 的会话超时
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
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
ms.collection:
- M365-security-compliance
description: 会话超时用于在 Office 365 客户端应用程序中平衡安全性和轻松访问。
ms.openlocfilehash: e39d578f0a5f193691724e3b3a0c42db0ad1011b
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030917"
---
# <a name="session-timeouts-for-office-365"></a><span data-ttu-id="67192-103">Office 365 的会话超时</span><span class="sxs-lookup"><span data-stu-id="67192-103">Session timeouts for Office 365</span></span>

<span data-ttu-id="67192-104">会话生存期是 Office 365 的身份验证的重要部分，并且是平衡安全性的重要组成部分以及用户提示其凭据的提示次数。</span><span class="sxs-lookup"><span data-stu-id="67192-104">Session lifetimes are an important part of authentication for Office 365 and are an important component in balancing security and the number of times users are prompted for their credentials.</span></span>
  
## <a name="session-times-for-office-365-services"></a><span data-ttu-id="67192-105">Office 365 服务的会话时间</span><span class="sxs-lookup"><span data-stu-id="67192-105">Session times for Office 365 services</span></span>

<span data-ttu-id="67192-106">当用户在任何 Office 365 web 应用或移动应用程序中进行身份验证时，将建立一个会话。</span><span class="sxs-lookup"><span data-stu-id="67192-106">When users authenticate in any of the Office 365 web apps or mobile apps, a session is established.</span></span> <span data-ttu-id="67192-107">在会话期间，用户不需要重新进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="67192-107">For the duration of the session, users won't need to re-authenticate.</span></span> <span data-ttu-id="67192-108">当用户处于非活动状态、关闭浏览器或选项卡时，或者当用户的身份验证令牌过期时，例如在重置其密码时，会话可能会过期。</span><span class="sxs-lookup"><span data-stu-id="67192-108">Sessions can expire when users are inactive, when they close the browser or tab, or when their authentication token expires for other reasons such as when their password has been reset.</span></span> <span data-ttu-id="67192-109">Office 365 服务具有不同的会话超时，以与每个服务的典型用途相对应。</span><span class="sxs-lookup"><span data-stu-id="67192-109">The Office 365 services have different session timeouts to correspond with the typical use of each service.</span></span>
  
<span data-ttu-id="67192-110">下表列出了 Office 365 服务的会话生存期：</span><span class="sxs-lookup"><span data-stu-id="67192-110">The following table lists the session lifetimes for Office 365 services:</span></span>
  
|<span data-ttu-id="67192-111">**Office 365 服务**</span><span class="sxs-lookup"><span data-stu-id="67192-111">**Office 365 service**</span></span>|<span data-ttu-id="67192-112">**会话超时**</span><span class="sxs-lookup"><span data-stu-id="67192-112">**Session timeout**</span></span>|
|:-----|:-----|
|<span data-ttu-id="67192-113">Microsoft 365 管理中心</span><span class="sxs-lookup"><span data-stu-id="67192-113">Microsoft 365 admin center</span></span>  <br/> |<span data-ttu-id="67192-114">系统将要求你为管理中心每隔8小时提供凭据。</span><span class="sxs-lookup"><span data-stu-id="67192-114">You are asked to provide credentials for the admin center every 8 hours.</span></span>  <br/> |
|<span data-ttu-id="67192-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="67192-115">SharePoint Online</span></span>  <br/> |<span data-ttu-id="67192-116">只要用户选择 "**让我进入登录**状态"，5天的非活动状态。</span><span class="sxs-lookup"><span data-stu-id="67192-116">5 days of inactivity as long as the users chooses **Keep me signed in**.</span></span> <span data-ttu-id="67192-117">如果用户在24小时或更长时间后再次访问 SharePoint Online，则超时值将重置为5天。</span><span class="sxs-lookup"><span data-stu-id="67192-117">If the user accesses SharePoint Online again after 24 or more hours have passed from the previous sign-in, the timeout value is reset to 5 days.</span></span>  <br/> |
|<span data-ttu-id="67192-118">Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="67192-118">Outlook Web App</span></span>  <br/> |<span data-ttu-id="67192-119">6小时。</span><span class="sxs-lookup"><span data-stu-id="67192-119">6 hours.</span></span>  <br/> <span data-ttu-id="67192-120">您可以使用[set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet 中的_ActivityBasedAuthenticationTimeoutInterval_参数更改此值。</span><span class="sxs-lookup"><span data-stu-id="67192-120">You can change this value by using the  _ActivityBasedAuthenticationTimeoutInterval_ parameter in the [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet.</span></span>  <br/> |
|<span data-ttu-id="67192-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="67192-121">Azure Active Directory</span></span>  <br/> <span data-ttu-id="67192-122">（由启用新式验证的 Office 2013 Windows 客户端使用）</span><span class="sxs-lookup"><span data-stu-id="67192-122">(Used by Office 2013 Windows clients with modern authentication enabled)</span></span>  <br/> | <span data-ttu-id="67192-123">新式验证使用访问令牌和刷新令牌向用户授予使用 Azure Active Directory 的 Office 365 资源的访问权限。</span><span class="sxs-lookup"><span data-stu-id="67192-123">Modern authentication uses access tokens and refresh tokens to grant user access to Office 365 resources using Azure Active Directory.</span></span> <span data-ttu-id="67192-124">访问令牌是在成功进行身份验证后提供的 JSON Web 令牌，有效期为1小时。</span><span class="sxs-lookup"><span data-stu-id="67192-124">An access token is a JSON Web Token provided after a successful authentication and is valid for 1 hour.</span></span> <span data-ttu-id="67192-125">此外，还提供刷新令牌的生存期较长。</span><span class="sxs-lookup"><span data-stu-id="67192-125">A refresh token with a longer lifetime is also provided.</span></span> <span data-ttu-id="67192-126">当访问令牌过期时，Office 客户端将使用有效的刷新令牌获取新的访问令牌。</span><span class="sxs-lookup"><span data-stu-id="67192-126">When access tokens expire, Office clients use a valid refresh token to obtain a new access token.</span></span> <span data-ttu-id="67192-127">如果用户的初始身份验证仍然有效，则 exchange 将成功。</span><span class="sxs-lookup"><span data-stu-id="67192-127">This exchange succeeds if the user's initial authentication is still valid.</span></span>  <br/>  <span data-ttu-id="67192-128">刷新令牌有效期为90天，且持续使用，它们在被吊销前可有效。</span><span class="sxs-lookup"><span data-stu-id="67192-128">Refresh tokens are valid for 90 days, and with continuous use, they can be valid until revoked.</span></span>  <br/>  <span data-ttu-id="67192-129">刷新令牌可能会因以下几个事件而无效：</span><span class="sxs-lookup"><span data-stu-id="67192-129">Refresh tokens can be invalidated by several events such as :</span></span>  <br/>  <span data-ttu-id="67192-130">用户的密码自发出刷新令牌后已更改。</span><span class="sxs-lookup"><span data-stu-id="67192-130">User's password has changed since the refresh token was issued.</span></span>  <br/>  <span data-ttu-id="67192-131">管理员可以应用条件访问策略，该策略将限制对用户尝试访问的资源的访问。</span><span class="sxs-lookup"><span data-stu-id="67192-131">An administrator can apply conditional access policies which restrict access to the resource the user is trying to access.</span></span>  <br/> |
|<span data-ttu-id="67192-132">适用于 Android、iOS 和 Windows 10 的 SharePoint 和 OneDrive 移动应用</span><span class="sxs-lookup"><span data-stu-id="67192-132">SharePoint and OneDrive mobile apps for Android, iOS, and Windows 10</span></span>  <br/> |<span data-ttu-id="67192-133">访问令牌的默认生存时间为1小时。</span><span class="sxs-lookup"><span data-stu-id="67192-133">The default lifetime for the access token is 1 hour.</span></span> <span data-ttu-id="67192-134">刷新令牌的默认最大非活动时间为90天。</span><span class="sxs-lookup"><span data-stu-id="67192-134">The default max inactive time of the refresh token is 90 days.</span></span>  <br/> [<span data-ttu-id="67192-135">了解有关令牌和如何配置令牌生存期的详细信息</span><span class="sxs-lookup"><span data-stu-id="67192-135">Learn more about tokens and how to configure token lifetimes</span></span>](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> <span data-ttu-id="67192-136">若要撤销刷新令牌，可以重置用户的 Office 365 密码</span><span class="sxs-lookup"><span data-stu-id="67192-136">To revoke the refresh token, you can reset the user's Office 365 password</span></span>  <br/> |
|<span data-ttu-id="67192-137">使用 Office 365 登录的 Yammer</span><span class="sxs-lookup"><span data-stu-id="67192-137">Yammer with Office 365 Sign-In</span></span>  <br/> |<span data-ttu-id="67192-138">浏览器的生存期。</span><span class="sxs-lookup"><span data-stu-id="67192-138">Lifetime of the browser.</span></span> <span data-ttu-id="67192-139">如果用户关闭浏览器并在新浏览器中访问 Yammer，Yammer 将使用 Office 365 重新对其进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="67192-139">If users close the browser and access Yammer in a new browser, Yammer will re-authenticate them with Office 365.</span></span> <span data-ttu-id="67192-140">如果用户使用的是缓存 cookie 的第三方浏览器，则在重新打开浏览器时，可能不需要重新进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="67192-140">If users use third-party browsers that cache cookies, they may not need to re-authenticate when they reopen the browser.</span></span>  <br/> <span data-ttu-id="67192-141">> [!NOTE]> 这仅对使用 Yammer 的 Office 365 登录的网络有效。</span><span class="sxs-lookup"><span data-stu-id="67192-141">> [!NOTE]> This is valid only for networks using Office 365 Sign-In for Yammer.</span></span>           |
   

