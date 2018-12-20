---
title: 如何将新式验证用于 Office 2013 和 Office 2016 客户端应用
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
ms.audience: Admin
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
description: 了解 Office 365 现代身份验证方式不同 Office 2013 和 2016年客户端应用程序。
ms.openlocfilehash: 2a5e218ca751f341e2a3a0ffd164f000ee503279
ms.sourcegitcommit: fd7a56f38ba2c2d2e7fcd6e165ec58b31be299d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "27378498"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>如何将新式验证用于 Office 2013 和 Office 2016 客户端应用

阅读本文以了解 Office 2013 和 Office 2016 客户端应用程序如何使用现代身份验证功能基于的身份验证配置 Office 365 租户上的 Exchange Online、 SharePoint Online 和 Skype 业务联机。
  
## <a name="availability-of-modern-authentication-for-office-365-services"></a>现代的 Office 365 服务的身份验证的可用性

对于 Office 365 服务，现代身份验证的默认状态是：
  
- **Exchange Online 的默认打开。** 请参阅[启用或禁用在 Exchange 在联机现代身份验证](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662)打开或关闭。 
    
- **默认情况下开启 SharePoint online。** 
    
- **打开 Skype 的业务 online 默认情况下。** 请参阅[启用 Business online 现代身份验证的 Skype](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)将其关闭或打开。
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Office 客户端应用程序的登录行为

Office 2013 客户端应用程序默认情况下支持旧的身份验证。旧意味着它们支持任一 Microsoft Online 登录助手或基本身份验证。为了使这些客户端使用现代身份验证功能，客户端有 Windows 已设置的注册表项。有关说明，请参阅[Office 2013 的 Windows 设备启用现代身份验证](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910)。
  
阅读[如何使用现代身份验证 (ADAL) 与 for Business 的 Skype](https://go.microsoft.com/fwlink/p/?LinkId=785431)来了解工作原理与 Skype 的业务。 
  
默认情况下，office 2016 客户端支持的现代身份验证和任何操作所需的客户端使用这些新的流程。但是，为使用旧的身份验证，需要进行显式操作。
  
单击以下链接以了解 Office 2013 和 Office 2016 客户端身份验证了 Office 365 服务，具体取决于开启现代身份验证的工作原理。
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

下表介绍 Office 2013 或 Office 2016 客户端应用程序的身份验证行为时使用或不现代身份验证连接到 Exchange Online。
  
|Office 客户端应用程序版本 ***|存在此参数的注册表项？ ***|在现代身份验证？ ***|现代身份验证的身份验证行为开启租户 （默认值） ***|现代身份验证的身份验证行为的租户 *** 关闭|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否，或 EnableADAL = 1  <br/> |是  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用基本身份验证。租户未启用时，服务器将拒绝现代身份验证。  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用基本身份验证。租户未启用时，服务器将拒绝现代身份验证。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用基本身份验证。租户未启用时，服务器将拒绝现代身份验证。  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用基本身份验证。租户未启用时，服务器将拒绝现代身份验证。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 0  <br/> |否  <br/> |基本身份验证  <br/> |基本身份验证  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |基本身份验证  <br/> |基本身份验证  <br/> |
|Office 2013  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用基本身份验证。租户未启用时，服务器将拒绝现代身份验证。  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用基本身份验证。租户未启用时，服务器将拒绝现代身份验证。  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

使用或不现代身份验证连接到 SharePoint Online 时下, 表介绍 Office 2013 或 Office 2016 客户端应用程序的身份验证行为。
  
|Office 客户端应用程序版本 ***|存在此参数的注册表项？ ***|在现代身份验证？ ***|现代身份验证的身份验证行为开启租户 （默认值） ***|现代身份验证的身份验证行为的租户 *** 关闭|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否，或 EnableADAL = 1  <br/> |是  <br/> |仅限现代身份验证。  <br/> |未能连接。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |仅限现代身份验证。  <br/> |未能连接。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 0  <br/> |否  <br/> |Microsoft Online 登录助手仅。  <br/> |Microsoft Online 登录助手仅。  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |Microsoft Online 登录助手仅。  <br/> |Microsoft Online 登录助手仅。  <br/> |
|Office 2013  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |仅限现代身份验证。  <br/> |未能连接。  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business Online
<a name="BK_SFBO"> </a>

下表介绍 Office 2013 或 Office 2016 客户端应用程序的身份验证行为，当他们连接到 Skype 业务 online 使用或不现代身份验证。
  
|Office 客户端应用程序版本 ***|存在此参数的注册表项？ ***|在现代身份验证？ ***|使用租户 *** 为打开的现代身份验证的身份验证行为|现代身份验证的身份验证行为租户 （默认值） 关闭 ***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否，或 EnableADAL = 1  <br/> |是  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用 Microsoft Online 登录助手。业务 Online 租户的 Skype 未启用时，服务器将拒绝现代身份验证。  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用 Microsoft Online 登录助手。业务 Online 租户的 Skype 未启用时，服务器将拒绝现代身份验证。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用 Microsoft Online 登录助手。业务 Online 租户的 Skype 未启用时，服务器将拒绝现代身份验证。  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用 Microsoft Online 登录助手。业务 Online 租户的 Skype 未启用时，服务器将拒绝现代身份验证。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 0  <br/> |否  <br/> |Microsoft Online 登录助手仅。  <br/> |Microsoft Online 登录助手仅。  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |Microsoft Online 登录助手仅。  <br/> |Microsoft Online 登录助手仅。  <br/> |
|Office 2013  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |首先尝试现代身份验证。如果服务器将拒绝现代身份验证连接，则使用 Microsoft Online 登录助手。业务 Online 租户的 Skype 未启用时，服务器将拒绝现代身份验证。  <br/> |Microsoft Online 登录助手仅。  <br/> |
   
## <a name="see-also"></a>另请参阅

[在 Windows 设备上启用适用于 Office 2013 的新式验证](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[规划多因素身份验证的 Office 365 部署 （适用于 Office 365 管理员）](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[使用 （面向最终用户） 的 2 步骤验证登录到 Office 365](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)