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
# <a name="session-timeouts-for-office-365"></a>Office 365 的会话超时

会话生存期是 Office 365 身份验证的重要组成部分，平衡安全性和次数，提示用户输入其凭据的重要组成部分。
  
## <a name="session-times-for-office-365-services"></a>Office 365 服务的会话时间

当用户在任何 Office 365 web 应用程序或移动应用程序进行身份验证时，建立会话。会话期间，用户不需要重新进行身份验证。当用户处于非活动状态，它们关闭浏览器或选项卡上，或其身份验证令牌其他原因已被重置其密码过期时，可以终止会话。Office 365 服务具有不同的会话超时，以与每个服务的典型用法对应。
  
下表列出了为 Office 365 服务的会话生存期：
  
|**Office 365 服务**|**会话超时**|
|:-----|:-----|
|Office 365 管理中心  <br/> |要求您提供凭据管理中心的每隔 8 小时。  <br/> |
|SharePoint Online  <br/> |5 天的非活动用户只要选择**使我保持登录**。如果用户访问 SharePoint Online 再次从以前登录过去 24 或几个小时后，超时值重置为 5 天。<br/> |
|Outlook Web App  <br/> |6 小时。  <br/> 使用[Set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet 中_ActivityBasedAuthenticationTimeoutInterval_参数，您可以更改此值。  <br/> |
|Azure Active Directory  <br/> （与已启用的现代身份验证一起使用的 Office 2013 Windows 客户端）  <br/> | 现代身份验证使用访问令牌和刷新令牌授予用户对使用 Azure Active Directory 的 Office 365 资源的访问。访问令牌是 JSON Web 令牌提供身份验证成功后，并且是有效 1 小时。此外提供了与较长的生存期刷新令牌。访问令牌过期后，Office 客户端使用有效刷新令牌获取新的访问令牌。此交换成功如果用户的初始身份验证，仍然有效。  <br/>  刷新令牌的有效期为 90 天，并且与连续使用，可以在有效，直到吊销。  <br/>  刷新令牌可以如失效由几个事件：  <br/>  用户的密码已更改后，刷新令牌颁发。  <br/>  管理员可以应用到用户尝试访问的资源限制访问其条件访问策略。  <br/> |
|SharePoint 和 OneDrive 移动应用程序 Android、 iOS 和 Windows 10  <br/> |访问令牌的默认生存时间为 1 小时。刷新令牌的默认最大不活动时间是 90 天。<br/> [了解有关令牌以及如何配置令牌生存期](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> 要取消刷新令牌，您可以重置用户的 Office 365 密码  <br/> |
|Yammer 与 Office 365 登录  <br/> |在浏览器的生存期。如果用户关闭浏览器，并在新浏览器中访问 Yammer，Yammer 重新将验证它们与 Office 365。如果用户使用第三方浏览器的缓存 cookie，它们可能不需要重新时其重新打开浏览器进行身份验证。<br/> > [!NOTE]> 这是仅供使用 Office 365 登录的 Yammer 网络。           |
   

