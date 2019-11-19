---
title: Microsoft 云 IT 体系结构资源
ms.author: bcarter
author: brendacarter
manager: laurawi
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 28986107-e2fb-4116-bfdd-f66d751a7c16
search.appverid:
- MET150
description: 摘要：了解 Microsoft 标识、安全性、网络和混合的核心云体系结构概念。查看使用 Microsoft 云时保护文件、标识和设备的指导建议。了解如何使用 Windows 10 和 Office 专业增强版部署新式安全桌面。
ms.openlocfilehash: c8817e0a6f0eda0dafec56475a3fb3e6a5a8627f
ms.sourcegitcommit: 23c8781d1a2b0472612c3a2cb6e5d13edb03e236
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "38702253"
---
# <a name="microsoft-cloud-it-architecture-resources"></a>Microsoft 云 IT 体系结构资源

 **摘要：** 了解 Microsoft 标识、安全性、网络和混合的核心云体系结构概念。查看使用 Microsoft 云时保护文件、标识和设备的指导建议。了解如何使用 Windows 10 和 Office 专业增强版部署新式安全桌面。
  
这些体系结构工具和海报提供有关 Microsoft 云服务的信息，其中包括 Office 365、Windows 10、Microsoft Intune、Microsoft Dynamics 365 以及本地混合和云解决方案。IT 决策者和架构师可以使用这些资源来确定其工作负载的理想解决方案，并做出有关核心基础结构组件的决策，如标识和安全性。 
  
<!--**[Microsoft's Enterprise Cloud Roadmap](microsoft-cloud-it-architecture-resources.md#roadmap)** (Sway) -->
    
- **[面向企业架构师的 Microsoft 云系列](microsoft-cloud-it-architecture-resources.md#cloudarch)** 
    <!-- [Microsoft Cloud Services and Platform Options](microsoft-cloud-it-architecture-resources.md#platformoptions) -->
    - [面向企业架构师的 Microsoft 云标识](microsoft-cloud-it-architecture-resources.md#identity)
    - [面向企业架构师的 Microsoft 云安全性](microsoft-cloud-it-architecture-resources.md#security)
    - [面向企业架构师的 Microsoft 云网络](microsoft-cloud-it-architecture-resources.md#networking)
    - [面向企业架构师的 Microsoft 混合云](microsoft-cloud-it-architecture-resources.md#hybrid)
    - [常见攻击和保护组织的 Microsoft 功能](#common-attacks-and-microsoft-capabilities-that-protect-your-organization)
    - [Microsoft 365 企业版底层基础结构](#m365foundationinfra)
    - [Microsoft 云租户到租户迁移的体系结构方法](#architecture-approaches-for-microsoft-cloud-tenant-to-tenant-migrations)
    
- **[Microsoft 365 企业版解决方案系列](microsoft-cloud-it-architecture-resources.md#BKMK_o365solutions)**：
    - [面向 IT 架构师的 Microsoft 365 中的 Microsoft Teams 和相关生产力服务](#microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects)
    - [面向 IT 架构师的 Microsoft 365 中的组](#groups-in-microsoft-365-for-it-architects)
    - [Office 365 的标识和设备保护](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    - [Office 365 中的文件保护解决方案](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    - [符合 GDPR 的 Office 365 信息保护](#office-365-information-protection-for-gdpr)
    - [Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南](#microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations)
    - [Microsoft 电话解决方案](#microsoft-telephony-solutions) 
    - [通过 Microsoft 部署新式安全桌面](microsoft-cloud-it-architecture-resources.md#msd)
    
请将你的想法告诉我们！向我们 ([cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com)) 发送电子邮件。 

<!--
<a name="roadmap"></a>
## Microsoft's Enterprise Cloud Roadmap

See the posters, icon sets, community venues, and other resources that describe the industry's most complete cloud solution.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumbnail for Enterprise Cloud Roadmap](media/c8b293b9-5992-4d29-b579-a6bbbd59d8d6.png)          ](https://aka.ms/cloudarchitecture) <br/> [Microsoft's Enterprise Cloud Roadmap](https://aka.ms/cloudarchitecture) (https://aka.ms/cloudarchitecture) <br/> |Swipe through this Sway experience for the resources that describe the industry's most complete cloud solution.  <br/> |
-->
  
<a name="cloudarch"></a>
##面向企业架构师的 Microsoft 云系列

这些云体系结构海报提供有关 Microsoft 云服务的信息，其中包括 Office 365、Azure Active Directory、Microsoft Intune、Microsoft Dynamics CRM Online 以及本地混合和云解决方案。IT 决策者和架构师可以使用这些资源来确定其工作负载的理想解决方案，并做出有关核心基础结构组件的决策，如标识和安全性。

<!--  
<a name="platformoptions"></a>
### Microsoft Cloud Services and Platform Options

Learn key differences between Microsoft cloud services and platform offerings. Find the best fit for your solution.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumb image of cloud architecture model with service options](media/ff5c74e2-afc6-40c1-9292-cc4cb128cdd1.png)          ](https://www.microsoft.com/download/details.aspx?id=54432) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=524731)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=524732)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=54432) <br/> | This model describes: <ul><li>  Software as a Service (SaaS) offerings, including Office 365 </li><li>  Platform as a Service (PaaS) features in Microsoft Azure </li><li>  Infrastructure as a Service (IaaS) features in Microsoft Azure </li><li>  Private cloud datacenter capabilities using Windows Server and System Center </li><li>  Learn how Microsoft's own IT department is migrating to these cloud services and building its hybrid cloud. </li></ul><br/>|
-->

   
<a name="identity"></a>
###面向企业架构师的 Microsoft 云标识

关于使用 Microsoft 云服务和平台为组织设计标识，IT 架构师需要了解的信息。
  
|**项**|**说明**|
|:-----|:-----|
|[![Microsoft 云标识模型的缩略图](media/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png)          ](https://www.microsoft.com/download/details.aspx?id=54431) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586)  \| [Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd)           \| [更多语言](https://www.microsoft.com/download/details.aspx?id=54431) <br/> | 此模型包含： <ul><li>Microsoft 云标识简介 </li><li>Azure AD IDaaS 功能 </li><li>将本地 Active Directory 域服务帐户与 Microsoft Azure Active Directory 集成 </li><li>将目录组件放入 Azure </li><li>Azure IaaS 中适用于工作负载的域服务选项 </li></ul><br/>|
   
<a name="security"></a>
### <a name="microsoft-cloud-security-for-enterprise-architects"></a>面向企业架构师的 Microsoft 云安全性

关于 Microsoft 云服务和平台的安全性，IT 架构师需要了解的信息。
  
|**项**|**说明**|
|:-----|:-----|
|[![Microsoft 云安全模型的缩略图](media/5dc26f80-8888-4572-8ed9-a120d711e0f0.png)          ](https://www.microsoft.com/download/details.aspx?id=48121) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842070)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=842071)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=48121) <br/> | 此模型包含： <ul><li>Microsoft 在提供安全服务和平台方面的作用</li><li>客户在降低安全风险上肩负的责任</li><li>顶级安全认证 </li><li>Microsoft 咨询服务提供的安全产品/服务 </ul><br/>|
   
<a name="networking"></a>
### <a name="microsoft-cloud-networking-for-enterprise-architects"></a>面向企业架构师的 Microsoft 云网络

关于 Microsoft 云服务和平台的网络，IT 架构师需要了解的信息。
  
|**项**|**说明**|
|:-----|:-----|
|[![Microsoft 云网络连接模型的缩略图](media/95e8ab6a-b4d0-4836-acc1-b0b77ebf46e6.png)          ](https://www.microsoft.com/download/details.aspx?id=54425) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842073)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=842074)           \| [更多语言](https://www.microsoft.com/download/details.aspx?id=54425) <br/> | 此模型包含： <ul><li> 发展你的云连接网络 </li><li> Microsoft 云连接的常见元素 </li><li> 面向 Microsoft 云连接的 ExpressRoute </li><li> 为 Microsoft SaaS、Azure PaaS 和 Azure IaaS 设计网络 </li></ul><br/>  <br/>|
   
<a name="hybrid"></a>
### <a name="microsoft-hybrid-cloud-for-enterprise-architects"></a>面向企业架构师的 Microsoft 混合云

关于 Microsoft 服务和平台的混合云，IT 架构师需要了解的信息。
  
|**项**|**说明**|
|:-----|:-----|
|[![Microsoft 混合云模型的缩略图](media/9989c71e-f6a0-4dbe-906c-43e67b3ce537.png)          ](https://www.microsoft.com/download/details.aspx?id=54424) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842082)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=842083)           \| [更多语言](https://www.microsoft.com/download/details.aspx?id=54424) <br/> | 此模型包含： <ul><li> Microsoft 的云产品（SaaS、Azure PaaS 和 Azure IaaS）及它们的常用元素 </li><li> Microsoft 云产品的混合云体系结构 </li><li> Microsoft SaaS (Office 365)、Azure PaaS 和 Azure IaaS 的混合云方案 </li></ul><br/>|
   
<a name="attacks"></a>
### <a name="common-attacks-and-microsoft-capabilities-that-protect-your-organization"></a>常见攻击和保护组织的 Microsoft 功能
了解最常见的网络攻击以及 Microsoft 在攻击的每个阶段如何帮助组织。 

|**项**|**说明**|
|:-----|:-----|
|[![常见攻击海报缩略图。](media/common%20attacks-thumb3.png)](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.pdf) <br/> [PDF](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.pdf) \| [Visio](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.vsdx) <br/> | 该海报展示了常见攻击的路径，并说明了哪些功能有助于在攻击的每个阶段阻止攻击者。 <br/>|

<a name="m365foundationinfra"></a>
### <a name="microsoft-365-enterprise-foundation-infrastructure"></a>Microsoft 365 企业版底层基础结构

快速了解 Microsoft 365 Enterprise 的[底层基础结构](https://docs.microsoft.com/microsoft-365/enterprise/deploy-foundation-infrastructure)以开始部署。
  
|**Item**|**说明**|
|:-----|:-----|
|[![Microsoft 365 企业版底层基础结构海报缩略图图像](media/Microsoft365EnterpriseFoundInfra-thumb.png)](https://aka.ms/m365efoundinfraposter) <br/> [联机查看](https://aka.ms/m365efoundinfraposter) \| [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/deploy-foundation-infrastructure/Microsoft365EnterpriseFoundInfra.pdf) <br/> | 此海报概述了底层基础结构的各个阶段，包括目标、功能和工具、设计决策、配置结果、载入及持续监视和更新。 <br/>| 

### <a name="architecture-approaches-for-microsoft-cloud-tenant-to-tenant-migrations"></a>Microsoft 云租户到租户迁移的体系结构方法 
本系列主题阐述了合并、收购、剥离和其他可能会导致你迁移到新云租户的方案的几种体系结构方法。 这些主题提供了有关规划的起点指南。

|**Item**|**说明**|
|:-----|:-----|
|[![Teams 逻辑体系结构海报缩略图](downloads/msft-tenant-to-tenant-migration-thumb.png)](downloads/Microsoft-365-tenant-to-tenant-migration.pdf) <br/> [PDF](downloads/Microsoft-365-tenant-to-tenant-migration.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/Microsoft-365-tenant-to-tenant-migration.vsdx)     |此模型包含： <ul><li>商业方案到体系结构方法的映射</li><li>设计注意事项</li><li>单事件迁移流</li><li>分阶段迁移流</li><li>租户移动或拆分流</li></ul>|

<a name="BKMK_o365solutions"></a>
## <a name="microsoft-365-enterprise-solution-series"></a>Microsoft 365 企业版解决方案系列

Microsoft 365 企业版解决方案系列介绍了如何实现 Microsoft 365 功能，尤其是其中一些跨技术的功能。

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>面向 IT 架构师的 Microsoft 365 中的 Microsoft Teams 和相关生产力服务
Microsoft 365 中生产力服务的逻辑体系结构，以 Microsoft Teams 为主导。

|**项**|**说明**|
|:-----|:-----|
|[![Teams 逻辑体系结构海报缩略图](downloads/msft-teams-logical-architecture-thumb.png)](downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)     |Microsoft 提供了一系列生产力服务，这些服务协同工作，提供数据治理、安全性和符合性相关功能的协作体验。 <br/> <br/>此系列图示展示了企业架构师生产力服务的逻辑体系结构，以 Microsoft Teams 为主导。|


### <a name="groups-in-microsoft-365-for-it-architects"></a>面向 IT 架构师的 Microsoft 365 中的组
对于 Microsoft 365 中的组，IT 架构师需要了解的信息

|**项**|**说明**|
|:-----|:-----|
|[![组信息图的缩略图](downloads/msft-m365-groups-architecture-thumb.png)](downloads/msft-m365-groups.pdf) <br/> [PDF](downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) |这些图示详细介绍了不同类型的组，如何创建和管理这些组，以及一些治理建议。|

   
<a name="BKMK_O365IDP"></a>
### <a name="identity-and-device-protection-for-office-365"></a>Office 365 的标识和设备保护

用于保护访问 Office 365 设备、其他 SaaS 服务以及使用 Azure AD 应用代理发布的本地应用的标识和设备的推荐功能。
  
|**项**|**说明**|
|:-----|:-----|
|[![模型海报：Office 365 和其他 SaaS 应用的标识和设备保护](media/c1cfb31b-5150-45ff-b46c-3a237e9f5581.png)          ](https://www.microsoft.com/download/details.aspx?id=55032) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=841656)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=55032) <br/> |请务必在数据、标识和设备中使用一致的保护级别。本文档介绍可与保护标识和设备功能相媲美的功能的详细信息。  <br/> |
   
<a name="BKMK_O365fileprotect"></a>
### <a name="file-protection-solutions-in-office-365"></a>Office 365 中的文件保护解决方案

在 Office 365 中基于三种不同的敏感度级别来保护文件的推荐功能。
  
|**项**|**说明**|
|:-----|:-----|
|[![Office 365 中文件保护解决方案迷你海报集缩略图](media/24be68b5-d852-4fdb-94ad-94491a19edd8.png)          ](https://www.microsoft.com/download/details.aspx?id=55523) <br/> [PDF](https://go.microsoft.com/fwlink/?linkid=2004320)  \| [Visio](https://download.microsoft.com/download/7/8/9/789645A5-BD10-4541-BC33-F8D1EFF5E911/MSFT_cloud_architecture_O365%20file%20protection.vsdx) <br/> |请务必在数据、标识和设备中使用一致的保护级别。本文档介绍可与保护 Office 365 中的文件功能相媲美的功能的详细信息。  <br/> |
   

### <a name="office-365-information-protection-for-gdpr"></a>针对 GDPR 的 Office 365 信息保护

针对发现、分类、保护和监视个人数据的指导性建议。该解决方案以一般数据保护条例 (GDPR) 为例，但用户可以采用同一流程实现对许多其他条例的符合性。

|**项目**|**说明**|
|:-----|:-----|
|![符合 GDPR 的 Office 365 信息保护缩略图](media/o365infoprotectforgdpr-thumb.png)  <br/> [PDF](https://download.microsoft.com/download/E/C/D/ECD5A339-EF10-4420-B3A9-99098884D716/MSFT_Cloud_architecture_information%20protection%20for%20GDPR.pdf) \| [Visio](https://download.microsoft.com/download/E/C/D/ECD5A339-EF10-4420-B3A9-99098884D716/MSFT_Cloud_architecture_information%20protection%20for%20GDPR.vsdx)    |若要以文章格式查看此内容，请参阅[符合 GDPR 的 Office 365 信息保护](https://docs.microsoft.com/Office365/SecurityCompliance/office-365-information-protection-for-gdpr)。      |

### <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a>Microsoft 针对政治宣传活动、非营利组织和其他敏捷型组织的安全指南 

本指南介绍了如何实现安全的云环境。该解决方案指南可供任何组织使用。并且对带有 BYOD 访问权限和来宾帐户的敏捷型组织提供了更多帮助。可使用本指南作为设计自己环境的起点。


|**项目**|**描述**|
|:-----|:-----|
|**Microsoft 针对政治宣传活动的安全指南** <br/> [![迷你海报集的缩略图。](media/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf) <br/> [PDF](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf)  \| [Visio](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.vsdx) <br/> |本指南以政治宣传活动的组织为例，可将本指南用作任何环境的起点。  <br/> |
|**Microsoft 针对非营利组织的安全指南** <br/> [![可下载文件的缩略图](media/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf) <br/> [PDF](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf)  \| [Visio](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.vsdx) <br/> |本指南经过略微修订，适用于非盈利组织。例如，引入了 Office 365 非盈利组织版计划。该技术指南与政治宣传活动解决方案指南相同。  <br/> |

本指南包括测试实验室指南。有关详细信息，请参阅 [Microsoft 针对政治宣传活动、非营利组织和其他敏捷型组织的安全指南](https://docs.microsoft.com/Office365/SecurityCompliance/microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o)。

### <a name="microsoft-telephony-solutions"></a>Microsoft 电话解决方案

当你开始在 Microsoft 云中使用 Teams 时，Microsoft 支持多种选项。此海报可帮助你确定哪种 Microsoft 电话解决方案（云端的电话系统或本地企业语音）适合你组织中的用户，以及你的组织如何连接到公用电话交换网 (PSTN)。

![Microsoft 电话服务解决方案海报缩略图](media/microsoft-telephony-solutions-thumb.png) <br/>
[PDF](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.pdf) | [Visio](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.vsdx) 

有关详细信息，请参阅此海报文章：[Microsoft 电话解决方案](https://docs.microsoft.com/SkypeForBusiness/hybrid/msft-telephony-solutions)。
  
<a name="msd"></a>
### <a name="deploy-a-modern-and-secure-desktop-with-microsoft"></a>通过 Microsoft 部署新式安全桌面

关于在 Windows 10 上部署和管理 Office 365 专业增强版更新，IT 架构师需要了解的信息。
  
|**项**|**说明**|
|:-----|:-----|
|[![通过 Microsoft 模型部署新式安全桌面的缩略图](media/321dd59c-d992-4c7a-a7b6-c23a783858bd.png)          ](https://www.microsoft.com/download/details.aspx?id=55987) <br/> [PDF](https://download.microsoft.com/download/4/E/9/4E90E227-770A-41D1-99FE-925A64D81A55/MSFT_modern_secure_desktop.pdf)  \| [Visio](https://download.microsoft.com/download/4/E/9/4E90E227-770A-41D1-99FE-925A64D81A55/MSFT_modern_secure_desktop.vsdx) <br/> | 此模型包含： <ul><li>  从 Microsoft 云部署 Windows 10 和 Office 专业增强版 </li><li>  使用 System Center Configuration Manager 部署 Windows 10 和 Office 365 专业增强版 </li><li>  从 Microsoft 云管理 Windows 10 和 Office 专业增强版的更新 </li><li>  使用 System Center Configuration Manager 管理 Windows 10 和 Office 365 专业增强版的更新 </li><li>  Windows 10 现成的其他保护功能 </li></ul><br/> |
   
## <a name="see-also"></a>另请参阅

[SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[安全解决方案](security-solutions.md)
  
[混合解决方案](hybrid-solutions.md)

