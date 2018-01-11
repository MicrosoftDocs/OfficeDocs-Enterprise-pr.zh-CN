---
title: "Microsoft SaaS (Office 365) 的混合云方案"
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
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "摘要： 了解混合的体系结构和方案，Microsoft 的基于 SaaS 的云服务 (Office 365)。"
ms.openlocfilehash: 63126d694817f8323494e584f1f497a1a732c678
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Microsoft SaaS (Office 365) 的混合云方案

 **摘要：**了解混合的体系结构和方案，Microsoft 的基于 SaaS 的云服务 (Office 365)。
  
将 Exchange、SharePoint，或 Skype for Business 本地部署与其在 Office 365 中的对等项结合使用，作为云迁移或长期集成策略的一部分。
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Microsoft SaaS 混合方案体系结构

图 1 显示了适用于 Office 365 的基于 Microsoft SaaS 的混合方案的体系结构。
  
**图 1: Microsoft Office 365 提供基于 SaaS 的混合方案**

![适用于 Office 365 的基于 Microsoft SaaS 的混合方案](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
针对体系结构的每一层：
  
- 应用和方案
    
    有多种基于 SaaS 的混合方案，围绕 Office 服务器产品及其对应的 Office 365：
    
  - 与 Exchange Online 结合使用的 Exchange Server（Exchange Server 混合）
    
  - 与 Skype for Business Online 结合使用的 Skype for Business Server 和新的 Cloud PBX 以及云连接器版本方案
    
  - 与 SharePoint Online 结合使用的 SharePoint Server 2016 或 SharePoint Server 2013（多个方案）
    
    还有采用本地 Skype for Business Server 的 Exchange Online，一个跨产品的混合方案。
    
- 标识
    
    可以包含与本地 Windows Sever AD 进行同步的目录同步。或者，可以配置 Azure AD 来与第三方标识提供程序进行联合。
    
- 网络
    
    由现有的 Internet 管道或通过 Office 365 或 Dynamics 365 的 Microsoft 对等建立的 ExpressRoute 连接组成。
    
- 本地
    
    可由现有的适用于 Exchange、SharePoint 和 Skype for Business 的服务器组成，应将其更新到最新版本。可以将它们与对应的 Office 365 相结合以实现混合方案。
    
设置您自己的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)。
  
## <a name="skype-for-business-2015-hybrid"></a>Skype for Business 2015 混合

企业 2015年混合的 Skype 允许您在线业务合并现有内部部署与 Skype。一些用户是穴内部部署和某些用户托管联机，但用户共享同一个会话启动协议 (SIP) 域，如 contoso.com。这种混合配置可用于迁移从内部到 Office 365 随着时间的推移在日程上。此外可以使用 Exchange 联机集成业务 2015年的 Skype。
  
**Skype 业务 2015年混合配置图 2:**

![Skype for Business 2015 混合配置](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
图 2 显示了对于业务 2015年混合配置，Skype 包含内部 Skype 业务 2015年前端池和边缘服务器与通信 Skype 的在线 Office 365 中的业务。
  
有关详细信息，请参阅：
  
- [规划业务服务器的 Skype 和 Skype 的在线业务之间的混合连接](https://technet.microsoft.com/library/jj205403.aspx)
    
- [受支持的混合配置的 Skype 业务服务器 2015](https://technet.microsoft.com/library/jj945633.aspx)
    
- [Skype 业务混合的](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>使用 Skype for Business Server 的云 PBX

借助使用 Skype for Business Server 的云 PBX，可以将现有的 Skype for Business Server 本地部署转换为具有本地公用电话交换网 (PSTN) 连接的拓扑。  
  
**图 3： 云 PBX 与 Skype 业务服务器**

![使用 Skype for Business Server 的云 PBX](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
图 3 显示了业务服务器配置，包含内部现有的 PBX 或电信网关、 业务服务器，Skype 和 PSTN 连接到 Microsoft 云 PBX 在 Office 365 提供，其中包括业务的 Skype 与 Skype 云 PBX联机。
  
组织中处于云中的用户能够接收来自 Microsoft 云的专用交换机 (PBX) 服务，包括信号和语音邮件，但 PSTN 连接（拨号音）通过来自本地 Skype for Business Server 部署的企业语音提供。
  
这是混合配置的一个很好的示例，借助混合配置，可以逐渐迁移到基于云的服务。开始将其移动到 Skype for Business Online 时，可以保留用户的语音功能。可以按照自己的节奏移动用户，要了解的一点是，无论用户身在何处，其语音功能将继续保留。  
  
有关详细信息，请参阅[规划业务服务器和 Skype 的在线业务或 Lync Server 2013 Skype 之间的混合连接](https://technet.microsoft.com/library/jj205403.aspx)。
  
如果还没有现有的 Lync Server 或 Skype for Business Server 部署，可以使用 Skype for Business 云连接器版本，一组通过云 PBX 实现本地 PSTN 连接的封装的虚拟机 (VM)。
  
有关详细信息，请参阅[规划业务云连接器版 Skype](https://technet.microsoft.com/library/mt605227.aspx)。
  
## <a name="sharepoint-hybrid"></a>SharePoint 混合

SharePoint 混合将 Office 365 中的 SharePoint Online 与本地 SharePoint 场结合使用，实现两全其美的连接体验。
  
**图 4: SharePoint 混合配置**

![SharePoint 混合配置](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
图 4 显示了包含与 SharePoint Online Office 365 中通信内部部署 SharePoint 场的 SharePoint 混合配置。
  
SharePoint 混合方案：
  
- [业务有关的混合 OneDrive](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [混合工作组网站](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [混合网 B2B](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [混合搜索](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [混合配置](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [混合选择器](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    使用自动进行混合配置的向导可轻松启用混合方案，可从 Office 365 的 SharePoint Online 管理中心执行此操作。
    
- [可扩展的混合应用程序启动程序](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    允许用户在本地 SharePoint 场页面内查看和使用 Office 365 视频以及开发应用和体验。
    
除了可扩展的混合应用启动器，所有这些 SharePoint 混合方案均可供 SharePoint 2016 和 SharePoint 2013 用户使用。
  
有关详细信息，请参阅[SharePoint 混合](http://hybrid.office.com/sharepoint/)。
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 混合

使用 Exchange Server 2016 混合，可以为在线用户实现 Office 365 中 Exchange Online 的权益，同时本地用户可以继续使用现有的 Exchange Server 基础结构。  
  
**图 5： 交换 2016年混合配置**

![Exchange 2016 混合配置](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
图 5 显示了包含内部 Exchange 邮箱服务器与 Exchange 在线保护和 Office 365 中的邮箱进行通信的交换 2016年混合配置。
  
一些用户具有本地电子邮件服务器，而一些用户使用 Exchange Online，但所有用户都共享相同的电子邮件地址空间。  
  
此混合配置：
  
- 利用现有的 Exchange Server 基础结构，而不迁移到 Exchange Online 随着时间的推移在日程上。
    
- 允许你支持远程站点，而无需投资分支办事处基础结构。
    
- 可以在 Office 365 中通过 Exchange Online Protection 路由传入的 Internet 电子邮件。
    
- 满足需要将数据维护在本地中的具有分公司的跨国企业的需求。
    
还可以为与其他 Microsoft Office 365 应用程序（包括 Skype for Business Online 和 SharePoint Online）集成此混合配置。
  
有关详细信息，请参阅[Exchange Server 混合部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)和[交换混合](http://hybrid.office.com/exchange/)。
  
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 混合云](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



