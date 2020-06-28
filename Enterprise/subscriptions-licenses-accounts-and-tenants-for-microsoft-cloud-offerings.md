---
title: 针对 Microsoft 云产品/服务的订阅、许可证、帐户和租户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/25/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 摘要：了解 Microsoft 云产品/服务中组织、订阅、许可证、用户帐户和租户的关系。
ms.openlocfilehash: 52857196f53a44196c96f60bd70564f5e3221b80
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906253"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>针对 Microsoft 云产品/服务的订阅、许可证、帐户和租户

为确保跨其云产品/服务使用一致的身份和帐单，Microsoft 提供了组织、订阅、许可证和用户帐户的层次结构。
  
- Microsoft 365 和 Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>层次结构的元素

以下是层次结构的元素：
  
### <a name="organization"></a>组织

An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.
  
### <a name="subscriptions"></a>订阅

订阅是与 Microsoft 就使用一个或多个 Microsoft 云平台或服务签订的协议，其费用基于每个用户许可证费用或云资源使用累计。 

- Microsoft 的软件即基于服务（SaaS）的云产品（Microsoft 365 和 Dynamics 365）收费每用户许可证费用。 
- Microsoft 的平台即服务 (PaaS) 和基础设施即服务 (IaaS) 云服务 (Azure) 根据云资源使用量收取费用。
 
You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.
  
组织可订阅多个 Micrososft 云服务。 图1显示了包含多个 Microsoft 365 订阅、Dynamics 365 订阅和多个 Azure 订阅的单个组织。

**图 1：组织的多个订阅示例**

![组织订阅多个 Micrososft 云服务的示例。](media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>许可证

对于 Microsoft 的 SaaS 云服务，许可证允许特定用户帐户使用云产品的服务。 作为订阅的一部分，你可以每月支付固定的费用。 管理员将许可证分配给订阅中的各个用户帐户。 在图2中的示例中，Contoso Corporation 拥有一个包含100许可证的 Microsoft 365 E5 订阅，这将允许最长可达100单个用户帐户以使用 Microsoft 365 E5 功能和服务。
  
**图 2：组织基于 SaaS 的订阅内的许可证**

![Microsoft 基于 SaaS 的云服务订阅中的多个许可证示例。](media/Subscriptions/Subscriptions-Fig2.png)
  
对于基于 Azure PaaS 的云服务，软件许可证是服务定价的一部分。
  
For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016. 
  
Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.
  
### <a name="user-accounts"></a>用户帐户

所有 Microsoft 云服务的用户帐户均存储在 Active Directory (Azure AD) 租户中，其中包含用户帐户和组。 通过使用基于 Windows 服务器的服务 Azure AD Connect，Azure AD 租户可与你现有的 Active Directory 域服务 (AD DS) 帐户同步。 这叫做目录同步。
  
图 3 显示了某个组织使用包含组织帐户的常见 Azure AD 租户进行多个订阅的示例。
  
**图 3：组织使用同一 Azure AD 租户进行的多个订阅**

![组织使用同一个 Azure AD 租户进行多个订阅的示例。](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>租户

对于 SaaS 云服务，租户是承载提供云服务的服务器的区域位置。 例如，Contoso Corporation 选择欧洲地区为其巴黎总部的15000工作者托管其 Microsoft 365、EMS 和 Dynamics 365 租户。
  
Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.
  
Azure AD 租户是包含帐户和组的 Azure AD 的特定实例。 Microsoft 365 或 Dynamics 365 的付费订阅或试用订阅包括免费的 Azure AD 租户。 此 Azure AD 租户不包括其他 Azure 服务，且与 Azure 试用版或付费订阅不同。
  
### <a name="summary-of-the-hierarchy"></a>层次结构的摘要

以下是快速回顾：
  
- 组织可进行多个订阅
    
  - 订阅可具有多个许可证
    
  - 许可证可分配给各个用户帐户
    
  - 用户帐户存储在 Azure AD 租户中
    
此处为一个有关组织、订阅、许可证和用户帐户关系的示例。
  
- 该组织由其公共域名识别。
    
  - 具有用户许可证的 Microsoft 365 E3 订阅。
    
    带有用户许可证的 Microsoft 365 E5 订阅。
    
    具有用户许可证的 Dynamics 365 订阅。
    
    多个 Azure 订阅。
    
  - 常见 Azure AD 租户中的组织的用户帐户。
    
多个 Microsoft 云服务订阅可使用同一 Azure AD 租户作为通用标识提供程序。 包含本地 AD DS 的同步帐户的中心 Azure AD 租户可为组织提供基于云的标识即服务 (IDaaS)。 
  
**图 4：适用于组织的同步本地帐户和 IDaaS**

![适用于组织的标识即服务 (IaaS) IDaaS。](media/Subscriptions/Subscriptions-Fig4.png)
  
Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>合并多个 Microsoft 云服务的订阅

下表介绍了如果已经订阅一种类型的云服务（标签在第一列下），而要添加其他云服务的订阅（跨列），如何合并多个 Microsoft 服务。
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |NA  <br/> |从 Azure 门户向你的组织添加 Azure 订阅。  <br/> |从 Microsoft 365 管理中心向你的组织添加 Dynamics 365 订阅。  <br/> |
|**Azure** <br/> |向你的组织添加 Microsoft 365 订阅。  <br/> |NA  <br/> |向你的组织添加 Dynamics 365 订阅。  <br/> |
|**Dynamics 365** <br/> |向你的组织添加 Microsoft 365 订阅。  <br/> |从 Azure 门户向你的组织添加 Azure 订阅。  <br/> |NA  <br/> |
   
为组织添加基于 Microsoft SaaS 的服务订阅的简便方法是通过管理中心来完成：
  
1. 使用全局管理员帐户登录 Microsoft 365 管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com))。
    
2. 从“管理中心”**** 主页的左侧导航栏，依次单击“帐单”**** 和“购买服务”****。
    
3. 在“购买服务”**** 页上，购买你的新订阅。
    
管理员中心将 Microsoft 365 订阅的组织和 Azure AD 租户分配给基于 SaaS 的云产品的新订阅。
  
若要添加与 Microsoft 365 订阅具有相同组织和 Azure AD 租户的 Azure 订阅，请执行以下操作：
  
1. [https://portal.azure.com](https://portal.azure.com)使用 Microsoft 365 全局管理员帐户登录到 Azure 门户（）。
    
2. 在左侧导航栏中，单击“订阅”****，然后单击“添加”****。
    
3. 在“添加订阅”**** 页上，选择一项服务并完成付款信息和协议。
    
如果你单独购买了 Azure 和 Microsoft 365 订阅，并且想要从 Azure 订阅访问 Microsoft 365 Azure AD 租户，请参阅[向 Azure Active Directory 租户添加现有 Azure 订阅](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)中的说明。
 
## <a name="see-also"></a>另请参阅

[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
  
[SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合解决方案](hybrid-solutions.md)

## <a name="next-step"></a>后续步骤

[评估 Microsoft 365 网络连接](assessing-network-connectivity.md)
  
