---
title: "Contoso Corporation 的订阅、许可证和用户帐户"
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
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "摘要： 了解 Contoso 的云订阅、 许可证、 用户帐户和承租人的结构。"
ms.openlocfilehash: 6e62fbbc0f52019e5d233fc73992b000952344f5
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a>Contoso Corporation 的订阅、许可证和用户帐户

 **摘要：**了解 Contoso 的云订阅、 许可证、 用户帐户和承租人的结构。
  
为了确保所有云产品对标识和账单的一致使用，Microsoft 提供组织/订阅/许可证/用户帐户层次结构：
  
- 组织
    
    使用 Microsoft 云产品的业务实体通常由公用 DNS 域名标识，例如 contoso.com。
    
- 订阅
    
    对于 Microsoft SaaS 云服务 （Office 365、 Intune/EMS 和 Dynamics 365），订阅是特定产品和购买的一套用户许可证。对于 Azure，订阅允许组织使用的云服务的帐单。
    
- 许可证
    
    对于 Microsoft SaaS 云产品，许可证允许特定的用户帐户以使用云服务。Azure，软件许可证天生到服务定价，但在某些情况下，您将需要购买额外的软件许可证。
    
- 用户帐户
    
    用户帐户存储在 Azure AD 租户中，并且可以从本地标识提供程序（如 Windows Server AD）进行同步。
    
## <a name="contosos-structure"></a>Contoso 的结构

Contoso 已确定组织及其订阅、许可证、帐户和租户的以下结构：
  
**图 1: Contoso 的组织、 订阅、 许可、 用户帐户和承租人**

![Contoso 的组织、订阅、许可证、用户帐户和租户](images/Contoso_Poster/Subscriptions.png)
  
图 1 显示 Contoso 组织如何包含多个订阅并和包含与 contoso.com Windows Server AD 林同步的用户帐户的常见 Azure AD 租户关联。
  
- **组织**Contoso 公司由其公共域名称 contoso.com 标识。
    
  - **订阅和许可证**Contoso 公司正在使用下列：
    
  - Office 365 企业 E3 产品 5000 许可证
    
  - 具有 200 个许可证的 Office 365 企业版 E5 产品
    
  - EMS 拥有 5000 许可证产品
    
  - 100 份许可证 Dynamics 365 的产品
    
  - 基于区域的多个 Azure 订阅
    
  - **用户帐户**常见的 Azure AD 租户包含用户帐户的列表和组由所有 Contoso 的订阅，但开发/测试 Azure 的订阅。
    
对于 Contoso 租户：
  
- 对于 SaaS 云产品，租户为房屋提供云服务的服务器的区域位置。Contoso 选择承载其 Office 365、 EMS 和 Dynamics 365 承租人的欧洲地区。 
    
- Azure PaaS 服务和应用程序以及 IaaS IT 工作负荷可以具有任何 Azure 数据中心内的租户遍及世界各地。Azure AD 租户是 Azure 广告包含的帐户和组的特定实例。
    
- 包含同步的帐户为 Contoso Windows 服务器 AD 林常见 Azure AD 租户提供 IDaaS 跨 Microsoft 的云服务。
    
有关详细信息，请参阅[预订、 许可证、 帐户和微软的云服务的租户](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)。
  
## <a name="contosos-azure-subscriptions"></a>Contoso 的 Azure 订阅

图 2 显示了 Contoso 的 Azure 订阅层次结构设计：
  
**图 2: Contoso 的结构对 Azure 订阅**

![Contoso 的 Azure 订阅结构](images/Contoso_Poster/Subscriptions_Nested.png)
  
- Contoso 位于顶部，基于其与 Microsoft 的企业协议。
    
- 有一组对应于基于 Contoso 的 Windows 服务器 AD 林中的域 Contoso 公司在世界各地，在不同地区的帐户。
    
- 在每个区域中，有一个或多个订阅根据地区的开发、 测试和生产部署的需要。
    
每个 Azure 订阅可以与单个 Azure AD 租户相关联，该租户包含用于 Azure 服务身份验证和授权的用户帐户和组。生产订阅使用常见的 Contoso Azure AD 租户。
  
## <a name="see-also"></a>See Also

[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)




