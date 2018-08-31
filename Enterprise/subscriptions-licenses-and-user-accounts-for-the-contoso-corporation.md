---
title: Contoso Corporation 的订阅、许可证和用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: 摘要： 了解 Contoso 的云订阅、 许可证、 用户帐户和租户的结构。
ms.openlocfilehash: cd196e0800f6a39973f4c5c82001ed3e9c330fee
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915507"
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a>Contoso Corporation 的订阅、许可证和用户帐户

 **摘要：** 了解 Contoso 的云订阅、 许可证、 用户帐户和租户的结构。
  
为了确保所有云产品对标识和账单的一致使用，Microsoft 提供组织/订阅/许可证/用户帐户层次结构：
  
- 组织
    
    使用 Microsoft 云产品的业务实体通常由公用 DNS 域名标识，例如 contoso.com。
    
- 订阅
    
    对于 Microsoft saas 与云产品 （Office 365 和 Intune/EMS Dynamics 365），订阅是特定产品及一系列用户许可证的购买。为 Azure 订阅允许帐单到组织的消耗的云服务。
    
- 许可证
    
    对于 Microsoft saas 与云产品许可证允许使用云服务的特定用户帐户。对 Azure，软件许可证是构建到服务定价，但在某些情况下，您将需要购买额外的软件许可证。
    
- 用户帐户
    
    用户帐户存储在 Azure AD 租户中，并且可以从本地标识提供程序（如 Windows Server AD）进行同步。
    
## <a name="contosos-structure"></a>Contoso 的结构

Contoso 已确定组织及其订阅、许可证、帐户和租户的以下结构：
  
**图 1：Contoso 的组织、订阅、许可证、用户帐户和租户**

![Contoso 的组织、订阅、许可证、用户帐户和租户](media/Contoso-Poster/Subscriptions.png)
  
图 1 显示 Contoso 组织如何包含多个订阅并和包含与 contoso.com Windows Server AD 林同步的用户帐户的常见 Azure AD 租户关联。
  
- **组织**由其公共域名 contoso.com 标识 Contoso Corporation。
    
  - **订阅和许可证**Contoso 公司正在使用以下：
    
  - 具有 5,000 许可证的 Office 365 企业版 E3 产品
    
  - 具有 200 个许可证的 Office 365 企业版 E5 产品
    
  - 具有 5,000 许可证的 EMS 产品
    
  - 具有 100 个许可证的 Dynamics 365 产品

    
  - 基于区域的多个 Azure 订阅
    
  - **用户帐户**常见的 Azure AD 租户包含用户帐户的列表和组使用的所有 Contoso 的订阅，除外开发/测试 Azure 订阅。
    
对于 Contoso 租户：
  
- 对于 SaaS 云产品，租户是托管提供云服务的服务器的区域位置。Contoso 选择欧洲区域来托管其 Office 365、EMS 和 Dynamics 365 租户。
  
    
- Azure PaaS 服务和应用程序和 IaaS IT 工作负荷可以跨世界上有任何 Azure 数据中心中的租户。Azure AD 租户是包含帐户和组的 Azure AD 的特定实例。
    
- 常见 Azure AD 租户包含 Contoso Windows Server AD 林的同步的帐户提供跨 Microsoft 云服务 IDaaS。
    
有关详细信息，请参阅[订阅、 许可证、 帐户和 Microsoft 云服务的租户](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)。
  
## <a name="contosos-azure-subscriptions"></a>Contoso 的 Azure 订阅

图 2 显示 Contoso 的 Azure 订阅的层次结构设计： 



  
**图 2：Contoso 的 Azure 订阅结构**

![Contoso 的 Azure 订阅结构](media/Contoso-Poster/Subscriptions-Nested.png)
  
- Contoso 位于顶部，基于其与 Microsoft 的企业协议。
    
- 有一套与基于 Contoso 的 Windows Server AD 林中的域 Contoso Corporation 的世界各地的不同区域对应的帐户。
    
- 内每个区域中，有一个或多个区域的开发、 测试和生产部署需求所基于的订阅。
    
每个 Azure 订阅可以与单个 Azure AD 租户相关联，该租户包含用于 Azure 服务身份验证和授权的用户帐户和组。生产订阅使用常见的 Contoso Azure AD 租户。
  
## <a name="see-also"></a>See Also

[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)




