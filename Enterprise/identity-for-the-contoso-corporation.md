---
title: Contoso Corporation 的标识
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
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: 摘要： 了解如何 Contoso 利用 IDaaS 提供地理位置分布和冗余其用户身份验证。
ms.openlocfilehash: 25e708147bda51fa8f8b4d0ea5e83eb4a9cd10b0
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915437"
---
# <a name="identity-for-the-contoso-corporation"></a>Contoso Corporation 的标识

 **摘要：** 了解如何 Contoso 利用 IDaaS 并提供地理上分散和冗余其用户身份验证。
  
Microsoft 提供的跨其云产品作为 (IDaaS) 的服务标识。采用云之间的基础结构，Contoso 的 IDaaS 解决方案必须利用其本地标识提供程序，包括使用其现有的受信任的第三方身份提供程序的联合身份验证。
  
## <a name="contosos-windows-server-ad-forest"></a>Contoso 的 Windows Server AD 林

Contoso 借助七个域将单个 Windows Server Active Directory (AD) 林用于 contoso.com，每个域对应世界上的一个地区。总部、区域中心办事处和分支办事处包含用于本地身份验证和授权的域控制器。

  
**图 1：全球的 Contoso 林和域**

![Contoso 在世界范围的 Windows Server AD 林和域](media/Contoso-Poster/Contoso-WW-ID.png)
  
图 1 显示 Contoso 林和世界各地包含区域中心的区域性域。
  
Contoso 想要在 contoso.com 林中使用帐户和组来对其基于云的应用和工作负载进行身份验证和授权。
  
## <a name="contosos-federated-authentication-infrastructure"></a>Contoso 的联合身份验证基础结构

Contoso 允许：
 



  
- 客户使用 Microsoft、Facebook 或 Google Mail 帐户登录其公共网站。
    
- 供应商和合作伙伴使用 LinkedIn、Salesforce 或 Google Mail 帐户登录合作伙伴 Extranet。
    
**图 2：Contoso 对客户和合作伙伴的联合身份验证支持**

![Contoso 的现有基础结构对客户和合作伙伴的联合身份验证的支持](media/Contoso-Poster/Federated-ID.png)
  
图 2 显示包含一个公共网站、一个合作伙伴 Extranet 和一组 AD FS 服务器的 Contoso DMZ。DMZ 已连接至包含客户和合作伙伴与 Internet 服务的 Internet。
  
DMZ 中的 Active Directory 联合身份验证服务 (AD FS) 服务器对客户凭据进行身份验证以访问公共网站，并对合作伙伴凭据进行身份验证以访问合作伙伴 Extranet。
  
当 Contoso 转换到 Azure Web App 和合作伙伴 extranet Dynamics 365 到其公共网站时，他们希望继续使用这些第三方身份提供程序其客户和合作伙伴。这将通过配置 Contoso Azure AD 租户和这些第三方身份提供程序之间的联盟。
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a>Contoso 的 Windows Server AD 林目录同步

Contoso 已部署 Azure AD 连接工具在其巴黎数据中心中的服务器群集。Azure AD 连接将与 Azure AD 租户 Contoso 的 Office 365、 EMS、 Dynamics 365 和 Azure 订阅由共享同步到 contoso.com Windows Server AD 林的更改。有关订阅、 许可证、 用户帐户和租户的详细信息，请参阅[订阅、 许可证和 Contoso Corporation 的用户帐户](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)。
  
**图 3：Contoso 的目录同步基础结构**

![Contoso 的目录同步基础结构](media/Contoso-Poster/DirSync.png)
  
图 3 显示运行 Azure AD Connect、将 Contoso Windows Server AD 林与 Azure AD 租户同步的服务器群集
  
Contoso 已配置联合身份验证，Contoso 的工作者提供单一登录。当用户具有已登录到 contoso.com Windows Server AD 林的访问 Microsoft SaaS 或 PaaS 云资源时，它们将不会提示输入密码。
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a>Contoso 身份验证流量的地理分布情况

为了更好地支持其移动和远程工作人员，Contoso 已在其区域办事处中部署了数个身份验证服务器集。此基础结构分散负载，并在对用户凭据进行身份验证以访问使用常见的 Azure AD 租户的 Microsoft 云产品时提供冗余和更高的性能。

  
为分散身份验证请求的负载，Contoso 已通过使用性能路由方法的配置文件来配置 Azure 流量管理器，该方法将身份验证客户端引入区域上最近的身份验证服务器集。  
  
**图 4：Contoso 区域办事处身份验证流量的地理分布情况**

![Contoso 区域办事处身份验证流量的地理分布情况](media/Contoso-Poster/Auth-GeoDist.png)
  
图 4 显示区域办事处的客户端计算机层、Azure 流量管理器和身份验证服务器。每个区域办事处都使用 Web 代理和 AD FS 服务器来通过 Windows Server AD 域控制器对用户凭据进行身份验证。
  
身份验证过程示例：
  
1. 客户端计算机启动与欧洲 Office 365 租赁中某个网页（如 sharepoint.contoso.com）的通信。



    
2. Office 365 发回发送身份验证证明的请求。该请求包含联系身份验证的 URL。
    
3. 客户端计算机尝试将 URL 中的 DNS 名称解析为 IP 地址。
    
4. Azure 流量管理器通过最接近客户端计算机的区域办事处的 Web 应用程序代理服务器的 IP 地址来接收 DNS 查询并响应客户端计算机。
    
5.   客户端计算机向 Web 应用程序代理服务器发送身份验证请求，代理服务器会将此请求转发到 AD FS 服务器。




    
6. AD FS 服务器从客户端计算机请求用户凭据。
    
7. 客户端计算机发送用户凭据，而不提示用户。
    
8. AD FS 服务器使用区域办事处中的 Windows Server AD 域控制器来验证凭据，并向客户端计算机返回安全令牌。
    
9. 客户端计算机向 Office 365 发送安全令牌。
    
10. 成功验证之后，Office 365 缓存安全令牌并向客户端计算机发送在步骤 1 中请求的网页。
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a>Azure IaaS 中总部身份验证基础结构的冗余

为了给包含 15,000 名工作人员的巴黎总部的远程和移动工作人员提供冗余，Contoso 已在 Azure IaaS 中部署第二组应用程序代理和 AD FS 服务器。

  
**图 5：Azure IaaS 中的冗余身份验证基础结构**

![Azure IaaS 中巴黎总部的冗余身份验证基础结构](media/Contoso-Poster/Paris-Auth-Redun.png)
  
图 5 显示 DMZ 中的 Web 代理和 AD FS 服务器，以及跨界 Azure 虚拟网络中一个额外的 Web 代理和 AD FS 服务器组。
  
当总部 DMZ 中的主要身份验证服务器不可用时，IT 人员就切换到部署在 Azure IaaS 中的冗余组。来自巴黎办事处计算机的后续身份验证请求使用 Azure IaaS 中的组，直到对可用性问题进行修正。
  
若要进行来回切换，Contoso 需要更新巴黎区域的 Azure 流量管理器配置文件，来为 Web 应用程序代理使用一组不同的 IP 地址：
  
- DMZ 身份验证服务器可用时，请使用 DMZ 中服务器的 IP 地址。

    
- DMZ 身份验证服务器不可用时，请使用 Azure IaaS 中服务器的 IP 地址。
    
## <a name="see-also"></a>See Also

[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[面向企业架构师的 Microsoft 云标识](http://aka.ms/cloudarchidentity)
  
[Office 365 的标识和设备保护](http://aka.ms/o365protect_device)
  
[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



