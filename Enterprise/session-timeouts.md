---
title: Office 365 的会话超时
ms.author: tracyp
author: MSFTTracyP
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
ms.collection:
- M365-security-compliance
description: 会话超时用于在 Office 365 客户端应用程序中平衡 securtiy 和轻松访问。
ms.openlocfilehash: 05e0ddbfb569f476986567e55bbf93428125b3af
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372879"
---
# <a name="session-timeouts-for-office-365"></a>Office 365 的会话超时

会话生存期是 Office 365 的身份验证的重要部分, 并且是平衡安全性的重要组成部分以及用户提示其凭据的提示次数。
  
## <a name="session-times-for-office-365-services"></a>Office 365 服务的会话时间

当用户在任何 Office 365 web 应用或移动应用程序中进行身份验证时, 将建立一个会话。 在会话期间, 用户不需要重新进行身份验证。 当用户处于非活动状态、关闭浏览器或选项卡时, 或者当用户的身份验证令牌过期时, 例如在重置其密码时, 会话可能会过期。 Office 365 服务具有不同的会话超时, 以与每个服务的典型用途相对应。
  
下表列出了 Office 365 服务的会话生存期:
  
|**Office 365 服务**|**会话超时**|
|:-----|:-----|
|Office 365 管理中心  <br/> |系统将要求你为管理中心每隔8小时提供凭据。  <br/> |
|SharePoint Online  <br/> |只要用户选择 "**让我进入登录**状态", 5 天的非活动状态。 如果用户在24小时或更长时间后再次访问 SharePoint Online, 则超时值将重置为5天。  <br/> |
|Outlook Web App  <br/> |6小时。  <br/> 您可以使用[set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet 中的_ActivityBasedAuthenticationTimeoutInterval_参数更改此值。  <br/> |
|Azure Active Directory  <br/> (由启用新式验证的 Office 2013 Windows 客户端使用)  <br/> | 新式验证使用访问令牌和刷新令牌向用户授予使用 Azure Active Directory 的 Office 365 资源的访问权限。 访问令牌是在成功进行身份验证后提供的 JSON Web 令牌, 有效期为1小时。 此外, 还提供刷新令牌的生存期较长。 当访问令牌过期时, Office 客户端将使用有效的刷新令牌获取新的访问令牌。 如果用户的初始身份验证仍然有效, 则 exchange 将成功。  <br/>  刷新令牌有效期为90天, 且持续使用, 它们在被吊销前可有效。  <br/>  刷新令牌可能会因以下几个事件而无效:  <br/>  用户的密码自发出刷新令牌后已更改。  <br/>  管理员可以应用条件访问策略, 该策略将限制对用户尝试访问的资源的访问。  <br/> |
|适用于 Android、iOS 和 Windows 10 的 SharePoint 和 OneDrive 移动应用  <br/> |访问令牌的默认生存时间为1小时。 刷新令牌的默认最大非活动时间为90天。  <br/> [了解有关令牌和如何配置令牌生存期的详细信息](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> 若要撤销刷新令牌, 可以重置用户的 Office 365 密码  <br/> |
|使用 Office 365 登录的 Yammer  <br/> |浏览器的生存期。 如果用户关闭浏览器并在新浏览器中访问 Yammer, Yammer 将使用 Office 365 重新对其进行身份验证。 如果用户使用的是缓存 cookie 的第三方浏览器, 则在重新打开浏览器时, 可能不需要重新进行身份验证。  <br/> > [!NOTE]> 这仅对使用 Yammer 的 Office 365 登录的网络有效。           |
   

