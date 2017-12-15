---
title: "Contoso Corporation 的标识"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: "摘要： 了解 Contoso 如何利用 IDaaS 和提供地理分布和冗余针对其用户的身份验证。"
ms.openlocfilehash: a0de29ac7e73216e04fe02c680f2557e9f402883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="identity-for-the-contoso-corporation"></a>Contoso Corporation 的标识

 **摘要：**了解如何 Contoso 利用 IDaaS 并提供地理分布和冗余针对其用户的身份验证。
  
Microsoft 提供的标识作为服务 (IDaaS) 在其云产品。采用含云基础结构，Contoso 的 IDaaS 解决方案必须利用其内部标识提供程序，包括其现有的受信任的第三方身份提供程序与联合身份验证。
  
## <a name="contosos-windows-server-ad-forest"></a>Contoso 的 Windows 服务器 AD 林

Contoso contoso.com 与七个域，一个用于世界的每个区域使用单个 Windows 服务器活动目录 (AD) 林。总部、 区域中心办事处和卫星办公室包含域控制器的本地身份验证和授权。
  
**图 1: Contoso 的林和域全球**

![Contoso 在世界范围的 Windows Server AD 林和域](images/Contoso_Poster/Contoso_WW_ID.png)
  
图 1 显示 Contoso 林和世界各地包含区域中心的区域性域。
  
Contoso 想要在 contoso.com 林中使用帐户和组来对其基于云的应用和工作负载进行身份验证和授权。
  
## <a name="contosos-federated-authentication-infrastructure"></a>Contoso 的联合身份验证基础结构

Contoso 允许：
  
- 客户使用 Microsoft、Facebook 或 Google Mail 帐户登录其公共网站。
    
- 供应商和合作伙伴使用 LinkedIn、Salesforce 或 Google Mail 帐户登录合作伙伴 Extranet。
    
**图 2: Contoso 的为客户和合作伙伴的联合身份验证支持**

![Contoso 的现有基础结构对客户和合作伙伴的联合身份验证的支持](images/Contoso_Poster/Federated_ID.png)
  
图 2 显示包含一个公共网站、一个合作伙伴 Extranet 和一组 AD FS 服务器的 Contoso DMZ。DMZ 已连接至包含客户和合作伙伴与 Internet 服务的 Internet。
  
DMZ 中的 Active Directory 联合身份验证服务 (AD FS) 服务器对客户凭据进行身份验证以访问公共网站，并对合作伙伴凭据进行身份验证以访问合作伙伴 Extranet。
  
在 Contoso 过渡到 Azure Web 应用程序和合作伙伴与 Dynamics 365 网其公共网站上，他们希望继续使用这些第三方身份提供商为其客户和合作伙伴。这将通过配置 Contoso Azure AD 承租人与这些第三方身份提供商之间的联盟。
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a>Contoso 的 Windows 服务器 AD 林中的目录同步

Contoso 已部署在其巴黎的数据中心的服务器群集上的 Azure AD 连接工具。Azure AD 连接同步共享 Contoso 的 Office 365、 EMS、 Dynamics 365 和 Azure 订阅的 Azure AD 租户 contoso.com Windows 服务器 AD 林中的更改。有关预订、 许可证、 用户帐户和承租人的详细信息，请参阅[预订、 许可证和 Contoso 公司的用户帐户](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)。
  
**图 3: Contoso 的目录同步基础结构**

![Contoso 的目录同步基础结构](images/Contoso_Poster/DirSync.png)
  
图 3 显示运行 Azure AD Connect、将 Contoso Windows Server AD 林与 Azure AD 租户同步的服务器群集
  
Contoso 已配置联合身份验证，它提供了单一登录，Contoso 的工作人员。当有已经登录到 contoso.com Windows 服务器 AD 林中的用户访问 Microsoft SaaS 或 PaaS 云资源时，它们将不会提示输入密码。
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a>Contoso 身份验证流量的地理分布情况

为了更好地支持其移动和远程员工队伍，Contoso 已部署了其区域办事处中的身份验证服务器的设置。此基础结构分散负载并进行身份验证的用户凭据访问 Microsoft 云服务使用常见的 Azure AD 租户时提供冗余和更高的性能。
  
为分散身份验证请求的负载，Contoso 已通过使用性能路由方法的配置文件来配置 Azure 流量管理器，该方法将身份验证客户端引入区域上最近的身份验证服务器集。  
  
**图 4： 身份验证通信的区域办事处的地理位置分布**

![Contoso 区域办事处身份验证流量的地理分布情况](images/Contoso_Poster/Auth_GeoDist.png)
  
图 4 显示区域办事处的客户端计算机层、Azure 流量管理器和身份验证服务器。每个区域办事处都使用 Web 代理和 AD FS 服务器来通过 Windows Server AD 域控制器对用户凭据进行身份验证。
  
身份验证过程示例：
  
1. 客户端计算机启动通信与网页中 Office 365 租赁在欧洲 （如 sharepoint.contoso.com)。
    
2. Office 365 发回发送身份验证证明的请求。该请求包含联系身份验证的 URL。
    
3. 客户端计算机尝试将 URL 中的 DNS 名称解析为 IP 地址。
    
4. Azure 流量管理器通过最接近客户端计算机的区域办事处的 Web 应用程序代理服务器的 IP 地址来接收 DNS 查询并响应客户端计算机。
    
5.  客户端计算机发送到向 AD FS 服务器转发请求的 web 应用程序代理服务器的身份验证请求。
    
6. AD FS 服务器从客户端计算机请求用户凭据。
    
7. 客户端计算机发送用户凭据，而不提示用户。
    
8. AD FS 服务器使用区域办事处中的 Windows Server AD 域控制器来验证凭据，并向客户端计算机返回安全令牌。
    
9. 客户端计算机向 Office 365 发送安全令牌。
    
10. 成功验证之后，Office 365 缓存安全令牌并向客户端计算机发送在步骤 1 中请求的网页。
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a>Azure IaaS 中总部身份验证基础结构的冗余

要包含 15000 工人的巴黎总部远程和移动工作者提供冗余，Contoso 已部署应用程序代理和在 Azure IaaS 的 AD FS 服务器的第二组。
  
**图 5： 在 Azure IaaS 的冗余身份验证基础结构**

![Azure IaaS 中巴黎总部的冗余身份验证基础结构](images/Contoso_Poster/Paris_Auth_Redun.png)
  
图 5 显示 DMZ 中的 Web 代理和 AD FS 服务器，以及跨界 Azure 虚拟网络中一个额外的 Web 代理和 AD FS 服务器组。
  
当总部 DMZ 中的主要身份验证服务器不可用时，IT 人员就切换到部署在 Azure IaaS 中的冗余组。来自巴黎办事处计算机的后续身份验证请求使用 Azure IaaS 中的组，直到对可用性问题进行修正。
  
若要进行来回切换，Contoso 需要更新巴黎区域的 Azure 流量管理器配置文件，来为 Web 应用程序代理使用一组不同的 IP 地址：
  
- DMZ 身份验证服务器可用时，请在 DMZ 中使用服务器的 IP 的地址。
    
- DMZ 身份验证服务器不可用时，请使用 Azure IaaS 中服务器的 IP 地址。
    
## <a name="see-also"></a>See Also

[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[企业架构师的 Microsoft 云标识](http://aka.ms/cloudarchidentity)
  
[标识和 Office 365 的设备保护](http://aka.ms/o365protect_device)
  
[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



