---
title: 可访问的图 - Microsoft Exchange 2013 平台选项
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: 本文是名为 Microsoft Exchange 2013 平台选项的图的可访问文本版本，您可在技术图表中找到此图。
ms.openlocfilehash: ddf215544b811257e6d43f212784a3a1e5aac7b0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068588"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>可访问的图 - Microsoft Exchange 2013 平台选项

**摘要：** 本文是[技术图表](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)中的“Microsoft Exchange 2013 平台选项”图表的可访问文本版本。
  
本海报介绍哪些业务决策者 (BDM) 和架构师需要了解 Exchange Online 与 Exchange Server 部署，其中包含以下内容： 
  
- Exchange 2013 的四个可用平台选项的比较: Exchange Online (Office 365)、Exchange 混合、Exchange Server 本地和提供商托管的 Exchange。 
    
- 描述 Exchange 2013 中的三项新功能或更新功能。 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>Exchange 2013 平台的四种不同部署比较

比较提供了每个部署选项的信息，包括以下方面： 
  
- 不同的部署功能的概述 
    
- 实施每个部署选项的优点 
    
- 许可要求 
    
- 所需的体系结构任务 
    
- IT 专业人员对实施每个部署选项的职责 
    
### <a name="overview"></a>概述

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

使用 Office 365 可提高效率并降低成本。
  
随附的图显示了具有 Azure Active Directory 租户的 Exchange Online, 该租户可同步内部部署 Active Directory 域服务 (AD DS) 环境和 Azure Active Directory 租户之间的帐户名称和密码。 Active Directory 联合身份验证服务 (AD FS) 是单一登录的必要条件。 
  
功能描述：
  
- 服务器和服务器软件的操作由 Microsoft 负责。
    
- 作为基于云的服务的 Exchange Server 2013 的丰富功能集。
    
- 始终与最新功能保持最新。
    
- 包含 Exchange Online Protection (EOP) 以提供反垃圾邮件/反恶意软件保护。
    
- 通过 99.9% 服务级别协议 (SLA) 实现的内置高可用性。
    
- 目录同步, 包括本地 Active Directory 域服务 (AD DS) 和 Azure Active Directory 租户之间的密码。 Active Directory 联合身份验证服务 (AD FS) 是单一登录的必要条件。
    
#### <a name="exchange-hybrid"></a>Exchange 混合

您可以利用 Office 365 的优势, 同时维护本地 Exchange Server。
  
随附的图显示了 Office 365 Exchange Online, 其中某些用户驻留在本地, 并且某些用户是在线托管的。 它还显示了在内部部署 Active Directory 域服务 (AD DS) 环境和 Azure Active Directory 租户之间同步帐户名称和密码的 Azure Active Directory 租户。
  
功能描述：
  
- 部分用户位于内部部署中，部分用户处于联机状态，且用户共享同一个电子邮件地址空间。
    
- 利用现有的 Exchange Server 基础结构。
    
- 按照您的安排，在一段时间后从 Exchange 内部部署迁移到 Exchange Online。
    
- 与其他 Office 365 应用程序集成, 包括 Lync Online 和 SharePoint Online。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 内部部署

您可以设计和管理自己的 Exchange Server 2013 基础结构。
  
随附的图显示了具有内部部署 Active Directory 域服务 (AD DS) 环境的 Exchange Server 基础结构，其中用户位于内部部署中。
  
功能描述：
  
- 对配置最大程度的控制和自定义。
    
- 无需在负载平衡层维护会话相关性。
    
- 使用数据库可用性组 (DAG) 的简单的高可用性和站点恢复。
    
- 托管可用性，可帮助您保持出色的用户体验。
    
- 利用现有的硬件和存储基础结构。
    
#### <a name="provider-hosted-exchange"></a>提供商承载的 Exchange

您可以将 Exchange Server 工作量外包给 Exchange Server 解决方案提供商。
  
随附的图显示了由提供商运行和维护的 Exchange Server 环境。
  
功能描述：
  
- 服务器和服务器软件的操作由提供商负责。
    
- Exchange Server 基础结构的规划、大小调整、比例缩放和维护均委托给提供商。
    
- 服务维护由提供商负责。
    
- Exchange 功能集仅限于提供商部署的软件版本。
    
### <a name="benefits-of-implementing-each-deployment-option"></a>实现每个部署选项的优点

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

此部署选项最适合于：
  
- 希望降低内部部署 Exchange 的运营成本的组织。
    
- 计划利用其他 Office 365 产品的组织, 如 SharePoint Online 和 Lync Online。
    
#### <a name="exchange-hybrid"></a>Exchange 混合

此部署选项最适合于：
  
- 加速从 Exchange 内部部署到 Exchange Online 的迁移。
    
- 支持远程站点，而无需投资分支机构基础结构。
    
- 需要将数据维护在内部部署中的具有分公司的跨国企业。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 内部部署

此部署选项最适合于：
  
- 高度自定义的解决方案。
    
- 具有第三方组件的旧版解决方案，而这些组件依赖于不受 Exchange Online 支持的硬件和软件。
    
- 受数据管理法规限制需要将数据维护在内部部署中的组织。
    
- 希望保持对整个平台和解决方案的控制的组织。
    
#### <a name="provider-hosted-exchange"></a>提供商承载的 Exchange

此部署选项最适合于：
  
- 需要 Exchange Server 功能，但希望外包其部署和维护的组织。
    
- 需要个性化支持选项的组织。
    
- 自定义解决方案，以及与提供商提供的自定义应用程序集成。
    
- 具有第三方组件的旧版解决方案，而这些组件依赖于不受 Exchange Online 支持的硬件和软件。
    
### <a name="license-requirements"></a>许可要求

下表详细说明了每个部署选项的许可要求。
  
|**部署选项**|**许可要求**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |订阅模型  <br/> |
|Exchange 混合  <br/> | Office 365-订阅模型 <br/>  本地-所有本地许可证均适用 (审查本地的交换服务器的许可证) <br/>  混合服务器许可证* <br/> |
|Exchange Server 内部部署  <br/> | 服务器操作系统 <br/>  Exchange 2013 服务器许可证 <br/>  Exchange 2013 客户端访问许可证 <br/> |
|提供商承载的 Exchange  <br/> |成本基于与提供商签订的协议  <br/> |
   
### <a name="architecture-tasks"></a>体系结构任务

本节列出了每个部署选项的体系结构任务。
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- 规划和设计目录同步。
    
- 确保通过防火墙、代理服务器、网关以及跨 WAN 链接的网络容量和连接。
    
#### <a name="exchange-hybrid"></a>Exchange 混合

除了 Office 365 和本地环境的体系结构任务之外:
  
- 决定是否提供单一登录体验。
    
- 决定是通过内部部署组织还是通过 Exchange Online Protection 路由入站 Internet 邮件。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 内部部署

- 设计 Exchange 拓扑。
    
- 规划服务器硬件的容量。
    
- 设计邮件路由拓扑。
    
- 设计客户端访问服务器的负载平衡。
    
- 使用数据库可用性组规划高可用性。
    
#### <a name="provider-hosted-exchange"></a>提供商承载的 Exchange

确保通过防火墙、代理服务器、网关以及跨 WAN 链接的网络容量和可用性对您的提供商可用。
  
### <a name="it-pro-responsibilities"></a>IT 专业人员的职责

本节列出了 IT 专业人员对每个部署选项的职责。
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- 实施目录同步计划。
    
- 规划和实施内部和外部 DNS 记录和路由。
    
- 为 Office 365 IP 地址和 URL 要求配置代理服务器或防火墙。
    
- 管理用户帐户和 Exchange Online 设置。
    
#### <a name="exchange-hybrid"></a>Exchange 混合

除了针对 Office 365 和本地环境的 IT 专业人员责任之外:
  
- 配置 Active Directory 联合身份验证服务 (AD FS) 以实现单一登录（如果需要）。
    
- 配置 exchange 证书以用于在 Exchange 2013 服务器和 Office 365 之间进行安全通信。
    
- 为所需的入站 Internet 邮件路径配置 DNS 记录。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 内部部署

- 配置 Exchange 服务的必要证书。
    
- 设置服务器。
    
- 实施 Exchange 邮件路由拓扑。
    
- 实施数据库可用性组。
    
- 更新和维护 Exchange 服务器。
    
- 按照利用情况，根据需要添加或删除服务器。
    
#### <a name="provider-hosted-exchange"></a>提供商承载的 Exchange

提供商的职责包括:
  
- 系统和服务维护。
    
- 功能的首次推出。
    
- 数据保护和灾难恢复。
    
IT 员工在您的组织中的职责包括创建和管理用户帐户。
  
#### <a name="more-information"></a>更多信息

若要了解有关 Exchange Online (Office 365) 的详细信息, 请参阅以下内容:
  
- [Exchange Online 服务说明](https://aka.ms/EXOSD)
    
- [TechNet 上的 Exchange Online 库](https://aka.ms/EXOTN)
    
- [Exchange Online 门户](https://aka.ms/EXO)
    
要了解有关 Exchange 混合的详细信息，请参阅以下内容：
  
- [Exchange 2013 混合部署](https://aka.ms/ExchangeHybrid)。 应注意, 混合服务器许可证仅在以下情况下是必需的: exchange 2010 组织 with Exchange 2013 混合服务器和 Exchange 2007 组织与 Exchange 2013 或 Exchange 2010 混合服务器。
    
- [Office 365 登录](https://aka.ms/HybridKey)
    
要了解有关 Exchange 内部部署的详细信息，请参阅以下内容：
  
- [TechNet 上的 Exchange Server 2013 库](https://aka.ms/Ex2013TN)
    
- [Exchange Server 2013 门户](https://aka.ms/Exchange2013)
    
- [Exchange Server 2013 体系结构](https://aka.ms/Ex2013SP1ArchPoster)
    
要了解有关提供商承载的 Exchange 的详细信息，请参阅以下内容：
  
[Exchange Server 2013 托管和多租户解决方案和指南](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Exchange 2013 中的三项新功能或更新功能的描述

### <a name="exchange-online-protection"></a>Exchange Online Protection

Exchange Online Protection (EOP) 提供跨全球数据中心网络部署的保护功能层，从而提供反垃圾邮件和反恶意软件保护。这可帮助您简化邮件环境的管理。EOP 包含在 Exchange Online 订阅中，但您也可以将其用于混合部署和内部部署。
  
随附的图显示了在全局网络中包含 EOP 层的 Exchange Online、Exchange 混合和 Exchange 内部部署的部署。
  
### <a name="exchange-server-deployment-assistant"></a>Exchange Server 部署助理

Exchange Server 部署助理是一个基于 web 的工具，它会询问您几个关于当前环境的问题，然后生成自定义分步检查表，以帮助您为不同类型的方案部署 Exchange Server。不论您是要从 Exchange 的之前版本迁移到 Exchange 2013 还是迁移到 Exchange Online，还是要规划混合基础结构，Exchange Server 部署助理都会针对您的方案创建一个自定义部署检查表。
  
随附的屏幕截图显示了使用 Exchange Server 部署助理创建的检查表示例。
  
### <a name="integration-with-lync-and-sharepoint"></a>与 Lync 和 SharePoint 集成

Exchange Server 2013 包括与 Lync Server 2013 和 SharePoint Server 2013 集成的许多功能。 这些产品将一起提供一整套丰富的功能并改进整个组织的协作。 
  
随附的图显示了服务器与服务器之间的身份验证海报并提供了海报的链接。 
  
- 存档、保留和电子数据展示
    
- 网站邮箱
    
- 统一联系人存储
    
- 高分辨率用户照片
    
- Outlook 和 Outlook Web App 中的 Lync 状态
    
- 服务器间身份验证
    
- Voicemail
    
- 会议录制
    
- Exchange 任务同步
    
随附的图显示了 Exchange Server 2013 SP1 体系结构海报, 并提供了海报的链接。
  

