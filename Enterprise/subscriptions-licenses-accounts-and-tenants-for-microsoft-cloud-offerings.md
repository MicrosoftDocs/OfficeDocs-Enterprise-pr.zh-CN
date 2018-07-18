---
title: 针对 Microsoft 云产品/服务的订阅、许可证、帐户和租户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/12/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 摘要：了解 Microsoft 云产品/服务中组织、订阅、许可证、用户帐户和租户的关系。
ms.openlocfilehash: 53d2f7f32402d8c05d22c0661a0f625c756da6d4
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319213"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>针对 Microsoft 云产品/服务的订阅、许可证、帐户和租户

 **摘要：** 了解 Microsoft 云产品/服务中组织、订阅、许可证、用户帐户和租户的关系。
  
为确保跨其云产品/服务使用一致的身份和帐单，Microsoft 提供了组织、订阅、许可证和用户帐户的层次结构。
  
- Microsoft Office 365
    
    有关详细信息，请参阅[商业版计划和定价](https://products.office.com/business/compare-office-365-for-business-plans)。
    
- Microsoft Azure
    
    有关详细信息，请参阅 [Azure 定价](https://azure.microsoft.com/pricing/)。
    
- Microsoft Intune 和企业移动性 + 安全性 (EMS)
    
    有关详细信息，请参阅 [Intune 定价](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)。
    
- Microsoft Dynamics 365
    
    有关详细信息，请参阅 [Dynamics 365 定价](https://dynamics.microsoft.com/)。
    
## <a name="elements-of-the-hierarchy"></a>层次结构的元素

以下是层次结构的元素：
  
### <a name="organization"></a>组织

组织表示使用 Microsoft 云产品/服务的业务实体，通常由一个或多个公共域名系统 (DNS) 域名（如 contoso.com）标识。组织是订阅的容器。
  
### <a name="subscriptions"></a>订阅

订阅是与 Microsoft 就使用一个或多个 Microsoft 云平台或服务签订的协议，其费用基于每个用户许可证费或云资源的使用量进行累计。Microsoft 基于软件即服务 (SaaS) 的云服务（Office 365、Intune/EMS 和 Dynamics 365）按用户收取许可证费用。Microsoft 的平台即服务 (PaaS) 和基础设施即服务 (IaaS) 云服务 (Azure) 根据云资源使用量收取费用。
  
你也可以使用试用版订阅，此订阅会在一定时间后或使用费用后过期。你可以将试用版订阅转换为付费订阅。
  
组织可订阅多个 Micrososft 云服务，图 1 显示了一个示例。
  
**图 1：组织的多个订阅示例**

![组织订阅多个 Micrososft 云服务的示例。](images/Subscriptions/Subscriptions_Fig1.png)

  
图 1 显示了一个组织，其具有多个 Office 365 订阅、一个 Intune 订阅、一个 Dynamics 365 订阅以及多个 Azure 订阅。
  
### <a name="licenses"></a>许可证

对于 Microsoft 的 SaaS 云服务，一个许可证允许一个特定用户帐户使用云产品的服务。作为订阅的一部分，会按月收取你固定的费用。管理员将许可证分配给订阅中的各个用户帐户。对于图 2 中的示例，Contoso 公司订阅了具有 100 个许可证的 Office 365 企业版 E5，可使最多 100 个单个用户帐户使用企业版 E5 的功能和服务。
  
**图 2：组织基于 SaaS 的订阅内的许可证**

![Microsoft 基于 SaaS 的云服务订阅中的多个许可证示例。](images/Subscriptions/Subscriptions_Fig2.png)
  
对于基于 Azure PaaS 的云服务，软件许可证是服务定价的一部分。
  
对于基于 Azure IaaS 的虚拟机，使用在虚拟机映像上安装的软件或应用程序可能需要其他许可证。某些虚拟机映像安装了授权版软件，并且成本包括在服务器的每分钟费率中。例如，SQL Server 2014 和 SQL Server 2016 的虚拟机映像。 
  
某些虚拟机映像安装了试用版应用程序，在试用期过后需要其他软件应用程序许可证。例如，SharePoint Server 2016 试用版虚拟机映像包括预安装的试用版 SharePoint Server 2016。若要在试用版过期后继续使用 SharePoint Server 2016，你必须从 Microsoft 购买 SharePoint Server 2016 许可证和客户端许可证。这些费用与 Azure 订阅是分开的，而运行虚拟机的每分钟费率仍然适用。
  
### <a name="user-accounts"></a>用户帐户

所有 Microsoft 云服务的用户帐户均存储在 Active Directory (AD) 租户中，其中包含用户帐户和组。通过使用基于 Windows 服务器的服务 Azure AD Connect，Azure AD 租户可与你现有的 Windows Server AD 帐户同步。这叫做目录同步 (DirSync)。
  
图 3 显示了某个组织使用包含组织帐户的常见 Azure AD 租户进行多个订阅的示例。
  
**图 3：组织使用同一 Azure AD 租户进行的多个订阅**

![组织使用同一个 Azure AD 租户进行多个订阅的示例。](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a>租户

对于 SaaS 云服务，租户是承载提供云服务的服务器的区域位置。例如，Contoso 公司选择欧洲地区为其巴黎总部的 15,000 名工作人员托管其 Office 365、EMS 和 Dynamics 365 租户。
  
Azure PaaS 服务和在 Azure IaaS 中托管的基于虚拟机的工作负荷可以在世界范围内的任何 Azure 数据中心拥有租户。在创建 Azure PaaS 应用或服务或 IaaS 工作负荷的元素时，应指定 Azure 数据中心（称为位置）。
  
Azure AD 租户是包含帐户和组的 Azure AD 的特定实例。Office 365、Dynamics 365 或 Intune/EMS 的付费或试用版订阅包括免费的 Azure AD 租户。此 Azure AD 租户不包括其他 Azure 服务，且与 Azure 试用版或付费订阅不同。
  
### <a name="summary-of-the-hierarchy"></a>层次结构的摘要

以下是快速回顾：
  
- 组织可进行多个订阅
    
  - 订阅可具有多个许可证
    
  - 许可证可分配给各个用户帐户
    
  - 用户帐户存储在 Azure AD 租户中
    
此处为一个有关组织、订阅、许可证和用户帐户关系的示例。
  
- 该组织由其公共域名识别。
    
  - 具有用户许可证的 Office 365 企业版 E3 订阅。
    
    具有用户许可证的 Office 365 企业版 E5 订阅。
    
    具有用户许可证的 EMS 订阅。
    
    具有用户许可证的 Dynamics 365 订阅。
    
    多个 Azure 订阅。
    
  - 常见 Azure AD 租户中的组织的用户帐户。
    
多个 Microsoft 云服务订阅可使用同一 Azure AD 租户作为通用标识提供程序。包含本地 Windows Server AD 的同步帐户的中心 Azure AD 租户可为组织提供基于云的标识即服务 (IDaaS)。如图 4 中所示。
  
**图 4：适用于组织的同步本地帐户和 IDaaS**

![适用于组织的标识即服务 (IaaS) IDaaS。](images/Subscriptions/Subscriptions_Fig4.png)
  
图 4 显示了如何将常见的 Azure AD 租户用于 Microsoft 的 SaaS 云产品、Azure PaaS 应用以及 Azure IaaS 中使用 Azure AD 域服务的虚拟机。Azure AD Connect 将本地 Windows Server AD 林与 Azure AD 租户同步。
  
有关 Microsoft 云产品/服务中标识集成的详细信息，请参阅[面向企业架构师的 Microsoft 云标识](https://aka.ms/cloudarchidentity)。
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>合并多个 Microsoft 云服务的订阅

下表介绍了如果已经订阅一种类型的云服务（标签在第一列下），而要添加其他云服务的订阅（跨列），如何合并多个 Microsoft 服务。
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |NA  <br/> |从 Azure 门户向你的组织添加 Azure 订阅。  <br/> |从 Office 365 门户向你的组织添加 Intune/EMS 订阅。  <br/> |从 Office 365 门户向你的组织添加 Dynamics 365 订阅。  <br/> |
|**Azure** <br/> |向你的组织添加 Office 365 订阅。  <br/> |NA  <br/> |向你的组织添加 Intune/EMS 订阅。  <br/> |向你的组织添加 Dynamics 365 订阅。  <br/> |
|**Intune/EMS** <br/> |向你的组织添加 Office 365 订阅。  <br/> |从 Azure 门户向你的组织添加 Azure 订阅。  <br/> |NA  <br/> |向你的组织添加 Dynamics 365 订阅。  <br/> |
|**Dynamics 365** <br/> |向你的组织添加 Office 365 订阅。  <br/> |从 Azure 门户向你的组织添加 Azure 订阅。  <br/> |向你的组织添加 Intune/EMS 订阅。  <br/> |NA  <br/> |
   
为组织添加基于 Microsoft SaaS 的服务订阅的简便方法是通过 Office 365 Admin 中心来完成：
  
1. 使用你的全局管理员帐户登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com))，然后单击“管理员”****。
    
2. 从“管理中心”**** 主页的左侧导航栏，依次单击“帐单”**** 和“购买服务”****。
    
3. 在“购买服务”**** 页上，购买你的新订阅。
    
Office 365 管理中心将 Office 365 订阅的组织和 Azure AD 租户分配到基于 SaaS 的云产品的新订阅。
  
使用与你的 Office 365 订阅相同的组织和 Azure AD 租户添加 Azure 订阅：
  
1. 使用 Office 365 全局管理员帐户登录到 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))。
    
2. 在左侧导航栏中，单击“订阅”****，然后单击“添加”****。
    
3. 在“添加订阅”**** 页上，选择一项服务并完成付款信息和协议。
    
如果分别购买 Azure 和 Office 365 订阅并且希望从 Azure 订阅访问 Office 365 Azure AD 租户，请参阅[将 Office 365 租户与 Azure 订阅关联](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription)中的说明。
  
## <a name="see-also"></a>另请参阅

[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
  
[云应用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合解决方案](hybrid-solutions.md)
  
[Contoso Corporation 的订阅、许可证和用户帐户](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



