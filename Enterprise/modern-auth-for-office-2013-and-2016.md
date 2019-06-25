---
title: 适用于 Office 2013 和 Office 2016 客户端应用的新式验证工作原理
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: 了解 Office 365 新式验证在 Office 2013 和2016客户端应用中的工作方式不同。
ms.openlocfilehash: 25646c014fc9ff11926c0091209a3419fad811d6
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203621"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>适用于 Office 2013 和 Office 2016 客户端应用的新式验证工作原理

阅读本文, 了解 Office 2013 和 Office 2016 客户端应用程序如何根据 Office 365 租户 (适用于 Exchange Online、SharePoint Online 和 Skype for Business Online) 上的身份验证配置使用新式身份验证功能。

> [!NOTE]
> 旧版客户端应用 (例如 Office 2010 和 Office for Mac 2011) 不支持新式身份验证, 只能与基本身份验证一起使用。

## <a name="availability-of-modern-authentication-for-office-365-services"></a>Office 365 服务的新式验证的可用性

对于 Office 365 服务, 新式验证的默认状态为:
  
- 默认**** 情况下, 启用 Exchange Online。 请参阅[在 Exchange Online 中启用或禁用新式验证](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662)以将其关闭或打开。 
    
- 默认**** 情况下, 启用 SharePoint Online。 
    
- 默认**** 情况下, 启用 Skype For business Online。 请参阅[为新式身份验证启用 Skype For Business Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)以将其关闭或打开。
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Office 客户端应用程序的登录行为

默认情况下, Office 2013 客户端应用支持旧版身份验证。 旧版是指它们支持 Microsoft Online 登录助手或基本身份验证。 为了让这些客户端使用新式身份验证功能, Windows 客户端已设置注册表项。 有关说明, 请参阅[在 Windows 设备上为 Office 2013 启用新式验证](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910)。
  
阅读[如何将新式验证 (ADAL) 与 skype For business 结合使用](https://go.microsoft.com/fwlink/p/?LinkId=785431), 了解如何使用 skype for business。 
  
默认情况下, Office 2016 客户端支持新式身份验证, 客户端无需执行任何操作即可使用这些新流。 但是, 需要显式操作才能使用旧版身份验证。
  
单击以下链接, 查看 office 2013 和 Office 2016 客户端身份验证如何与 Office 365 服务配合使用, 具体取决于是否启用新式身份验证。
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

下表介绍了 Office 2013 或 Office 2016 客户端应用程序在使用或不使用新式身份验证连接到 Exchange Online 时的身份验证行为。
  
|Office 客户端应用程序版本 * * * *|存在注册表项？ * * * *|上的新式身份验证？ * * * *|为租户启用新式身份验证的身份验证行为 (默认) * * * *|为租户 * * * * 禁用新式身份验证的身份验证行为|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否, 或 EnableADAL = 1  <br/> |是  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用基本身份验证。 当租户未启用时, 服务器将拒绝新式身份验证。  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用基本身份验证。 当租户未启用时, 服务器将拒绝新式身份验证。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用基本身份验证。 当租户未启用时, 服务器将拒绝新式身份验证。  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用基本身份验证。 当租户未启用时, 服务器将拒绝新式身份验证。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 0  <br/> |否  <br/> |基本身份验证  <br/> |基本身份验证  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |基本身份验证  <br/> |基本身份验证  <br/> |
|Office 2013  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用基本身份验证。 当租户未启用时, 服务器将拒绝新式身份验证。  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用基本身份验证。 当租户未启用时, 服务器将拒绝新式身份验证。  <br/> |
   
<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

下表介绍了 Office 2013 或 Office 2016 客户端应用程序在使用或不使用新式身份验证连接到 SharePoint Online 时的身份验证行为。
  
|Office 客户端应用程序版本 * * * *|存在注册表项？ * * * *|上的新式身份验证？ * * * *|为租户启用新式身份验证的身份验证行为 (默认) * * * *|为租户 * * * * 禁用新式身份验证的身份验证行为|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否, 或 EnableADAL = 1  <br/> |是  <br/> |仅限新式验证。  <br/> |连接失败。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |仅限新式验证。  <br/> |连接失败。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 0  <br/> |否  <br/> |仅 Microsoft Online 登录助手。  <br/> |仅 Microsoft Online 登录助手。  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |仅 Microsoft Online 登录助手。  <br/> |仅 Microsoft Online 登录助手。  <br/> |
|Office 2013  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |仅限新式验证。  <br/> |连接失败。  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business Online
<a name="BK_SFBO"> </a>

下表介绍了在使用或不使用新式身份验证连接到 Skype for business Online 时, Office 2013 或 Office 2016 客户端应用程序的身份验证行为。
  
|Office 客户端应用程序版本 * * * *|存在注册表项？ * * * *|上的新式身份验证？ * * * *|为租户 * * * * 启用新式身份验证的身份验证行为|为租户禁用新式身份验证的身份验证行为 (默认值) * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否, 或 EnableADAL = 1  <br/> |是  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用 Microsoft Online 登录助手。 当未启用 Skype for business Online 租户时, 服务器将拒绝新式身份验证。  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用 Microsoft Online 登录助手。 当未启用 Skype for business Online 租户时, 服务器将拒绝新式身份验证。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用 Microsoft Online 登录助手。 当未启用 Skype for business Online 租户时, 服务器将拒绝新式身份验证。  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用 Microsoft Online 登录助手。 当未启用 Skype for business Online 租户时, 服务器将拒绝新式身份验证。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 0  <br/> |否  <br/> |仅 Microsoft Online 登录助手。  <br/> |仅 Microsoft Online 登录助手。  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |仅 Microsoft Online 登录助手。  <br/> |仅 Microsoft Online 登录助手。  <br/> |
|Office 2013  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |首先尝试新式验证。 如果服务器拒绝新式身份验证连接, 则使用 Microsoft Online 登录助手。 当未启用 Skype for business Online 租户时, 服务器将拒绝新式身份验证。  <br/> |仅 Microsoft Online 登录助手。  <br/> |
   
## <a name="see-also"></a>另请参阅

[在 Windows 设备上为 Office 2013 启用新式验证](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[规划 Office 365 部署的多重身份验证 (针对 Office 365 管理员)](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[使用2步验证登录 Office 365 (针对最终用户)](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)
