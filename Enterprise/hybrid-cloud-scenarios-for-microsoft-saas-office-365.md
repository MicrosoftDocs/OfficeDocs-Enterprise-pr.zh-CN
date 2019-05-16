---
title: Microsoft SaaS (Office 365) 的混合云方案
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: '摘要: 了解 Microsoft 基于 SaaS 的云产品的混合体系结构和方案 (Office 365)。'
ms.openlocfilehash: 84092fe419ab31fca7763f434e328eb855d46835
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067218"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>适用于 Microsoft SaaS (Office 365) 的混合云方案

 **摘要:** 了解 Microsoft 基于 SaaS 的云产品的混合体系结构和方案 (Office 365)。
  
将 Exchange、SharePoint，或 Skype for Business 本地部署与其在 Office 365 中的对等项结合使用，作为云迁移或长期集成策略的一部分。
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Microsoft SaaS 混合方案体系结构

图 1 显示了适用于 Office 365 的基于 Microsoft SaaS 的混合方案的体系结构。
  
**图 1：适用于 Office 365 的基于 Microsoft SaaS 的混合方案**

![适用于 Office 365 的基于 Microsoft SaaS 的混合方案](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
针对体系结构的每一层：
  
- 应用和方案
    
    有多种基于 SaaS 的混合方案，围绕 Office 服务器产品及其对应的 Office 365：
    
  - 与 Exchange Online 结合使用的 Exchange Server（Exchange Server 混合）
    
  - 与 Skype for Business Online 结合使用的 Skype for Business Server 和新的 Cloud PBX 以及云连接器版本方案
    
  - SharePoint Server 2019、SharePoint Server 2016 或 SharePoint Server 2013 与 SharePoint Online 结合使用 (多个方案)
    
    还有采用本地 Skype for Business Server 的 Exchange Online，一个跨产品的混合方案。
    
- 标识
    
    可以包含与您的内部部署 Active Directory 域服务 (AD DS) 的目录同步。 或者，可以配置 Azure AD 来与第三方标识提供程序进行联合。
    
- 网络
    
    由现有的 Internet 管道或通过 Office 365 或 Dynamics 365 的 Microsoft 对等建立的 ExpressRoute 连接组成。
    
- 本地
    
    可由现有的适用于 Exchange、SharePoint 和 Skype for Business 的服务器组成，应将其更新到最新版本。可以将它们与对应的 Office 365 相结合以实现混合方案。
    
设置您自己的 Office 365 开发/测试环境, 请参阅[office 365 测试实验室指南](cloud-adoption-test-lab-guides-tlgs.md)。
  
## <a name="skype-for-business-hybrid"></a>Skype for Business 混合

Skype for Business 混合允许你将现有的本地部署与 Skype for Business Online 结合使用。 部分用户位于本地，部分用户处于联机状态，但用户共享同一个 会话初始协议 (SIP) 域，例如 contoso.com。 按照日程安排，可以在一段时间内使用此混合配置从本地迁移到 Office 365。 Skype for Business 也可以与[Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)集成。
  
**图 2: Skype for Business 混合配置**

![Skype for Business 混合配置](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
图2显示了 Skype for Business 混合配置, 其中包括与 Office 365 中的 Skype for business Online 通信的本地 Skype for business 前端池和边缘服务器。
  
有关详细信息, 请参阅[规划 skype For Business Server 和 skype For Business Online 之间的混合连接](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)。
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>使用 Skype for Business Server 的云 PBX

使用具有 Skype for Business Server 的云 PBX, 可以将现有的 Skype for Business Server 本地部署转换为具有本地公共交换电话网络 (PSTN) 连接的拓扑。 
  
**图 3：使用 Skype for Business Server 的云 PBX**

![使用 Skype for Business Server 的云 PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
图3显示了具有 Skype for Business Server 配置的云 PBX, 其中包括本地现有 PBX 或电信网关、Skype for Business Server 以及连接到 Office 365 中的 Microsoft 云 PBX 的 PSTN, 其中包括 Skype for Business隐私声明.
  
组织中处于云中的用户能够接收来自 Microsoft 云的专用交换机 (PBX) 服务，包括信号和语音邮件，但 PSTN 连接（拨号音）通过来自本地 Skype for Business Server 部署的企业语音提供。
  
这是允许您逐步迁移到基于云的服务的混合配置的一个很好的示例。 开始将其移动到 Skype for Business Online 时，可以保留用户的语音功能。 可以按照自己的节奏移动用户，要了解的一点是，无论用户身在何处，其语音功能将继续保留。 
  
有关详细信息, 请参阅[规划 skype For Business Server 和 skype For Business Online 之间的混合连接](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)。
  
如果还没有现有的 Lync Server 或 Skype for Business Server 部署，可以使用 Skype for Business 云连接器版本，一组通过云 PBX 实现本地 PSTN 连接的封装的虚拟机 (VM)。
  
有关详细信息, 请参阅[Plan For Skype For Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)。

  
## <a name="sharepoint-hybrid"></a>SharePoint 混合

SharePoint 混合将 Office 365 中的 SharePoint Online 与本地 SharePoint 场结合使用，实现两全其美的连接体验。
  
**图 4：SharePoint 混合配置**

![SharePoint 混合配置](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
图4显示了 SharePoint 混合配置, 其中包括与 Office 365 中的 SharePoint Online 进行通信的本地 SharePoint 场。
  
SharePoint 混合方案：
  
- [混合 OneDrive for Business](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [混合 Extranet B2B](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [混合搜索](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [混合配置文件](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [混合选取器](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    使用自动进行混合配置的向导可轻松启用混合方案，可从 Office 365 的 SharePoint Online 管理中心执行此操作。
    
- [可扩展的混合应用启动器](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    允许用户在本地 SharePoint 场页面内查看和使用 Office 365 视频以及开发应用和体验。
    
除了可扩展的混合应用启动器，所有这些 SharePoint 混合方案均可供 SharePoint 2016 和 SharePoint 2013 用户使用。
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 混合

使用 Exchange Server 2016 混合，可以为在线用户实现 Office 365 中 Exchange Online 的权益，同时本地用户可以继续使用现有的 Exchange Server 基础结构。  
  
**图 5：Exchange 2016 混合配置**

![Exchange 2016 混合配置](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
图5显示了 Exchange 2016 混合配置, 其中包括与 Office 365 中的 Exchange Online Protection 和邮箱进行通信的本地 Exchange 邮箱服务器。
  
一些用户具有本地电子邮件服务器，而一些用户使用 Exchange Online，但所有用户都共享相同的电子邮件地址空间。  
  
此混合配置：
  
- 利用现有的 Exchange Server 基础结构，同时按照日程安排，在一段时间内迁移到 Exchange Online。
    
- 允许你支持远程站点，而无需投资分支办事处基础结构。
    
- 可以在 Office 365 中通过 Exchange Online Protection 路由传入的 Internet 电子邮件。
    
- 满足需要将数据维护在本地中的具有分公司的跨国企业的需求。
    
还可以为与其他 Microsoft Office 365 应用程序（包括 Skype for Business Online 和 SharePoint Online）集成此混合配置。
  
有关详细信息, 请参阅[Exchange Server 混合部署](https://docs.microsoft.com/exchange/exchange-hybrid)。
  
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 混合云](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

