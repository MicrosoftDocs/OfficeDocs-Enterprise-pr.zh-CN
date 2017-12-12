---
title: "混合云概述"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/31/2016
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: "摘要： 了解 Microsoft 混合云的定义和元素。"
---

# 混合云概述

 **摘要：** 了解 Microsoft 混合云的定义和元素。
  
混合云使用本地网络和云中的计算或存储资源。可以使用混合云作为路径，以将业务及其 IT 需求迁移到云中，或将云平台和服务与现有的本地基础结构集成来作为整体 IT 策略的一部分。
  
## Microsoft 混合云

Microsoft 混合云是一组将 Microsoft 云平台与本地组件结合使用的业务方案，如： 
  
- 从本地 SharePoint 场中的内容和 Office 365 的 SharePoint Online 中的内容获取搜索结果。
    
- 在查询本地数据存储的 Azure 中运行的移动应用。
    
- 在 Azure 虚拟机上运行的 Intranet IT 工作负荷。
    
**图 1：Microsoft 混合云的组件**

![Microsoft 混合云的组件](images/65dfb1c6-26be-45c2-ab3d-6d1cd4a0f823.png)
  
图 1 显示跨 Internet 或 ExpressRoute 连接提供的 Microsoft 混合云组件，从本地网络到 Office 365、Azure 平台即服务 (PaaS) 和 Azure 基础结构即服务 (IaaS) 均包含在内。
  
因为 Microsoft 拥有市场中最完整的云解决方案（包括软件即服务 (SaaS)、Paas 和 laas），你可以：
  
- 将工作负荷和应用程序迁移到云时，利用现有的本地投资。
    
- 例如，当法规或策略不允许将特定的数据或工作负荷转移到云时，可将混合云方案纳入长期 IT 计划。
    
- 创建包含多个 Microsoft 云服务和平台的其他混合方案。
    
混合云方案与 Microsoft 云服务方案因平台不同而异。
  
- SaaS
    
    Microsoft SaaS 服务包括 Office 365、Microsoft Intune 和 Microsoft Dynamics 365。采用 Microsoft SaaS 的混合云方案将这些服务与本地服务或应用程序相结合。例如，在 Office 365 中运行的 Exchange Online 可以与部署在本地的 Skype for Business 2015 集成。
    
- Azure PaaS
    
    Microsoft Azure PaaS 服务允许你创建基于云的应用程序。采用 Microsoft PaaS 服务的混合云方案将 Azure PaaS 应用与本地资源或应用程序相结合。例如，Azure PaaS 应用可以安全地查询本地数据存储，以获取向移动应用用户进行显示所需的信息。
    
- Azure IaaS
    
    借助 Azure IaaS 服务，可以在云中生成并运行基于服务器的 IT 工作负荷，而不是在本地数据中心内。采用 Azure IaaS 服务的混合云方案通常由在虚拟机上运行的 IT 工作负荷组成，该虚拟机以透明方式连接到本地网络。本地用户不会注意到这一差异。
    
## 混合云的元素

在通过 Microsoft 云平台和服务规划和实施混合云方案时，必须考虑以下元素。
  
- 网络
    
    混合云方案的网络包括到 Microsoft 云平台和服务的连接，以及可在峰值负载下保持性能的足够带宽。有关详细信息，请参阅 [面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)。
    
- 标识
    
    SaaS 和 Azure PaaS 混合方案的标识可以包括作为通用标识提供程序的 Azure AD，它可以与本地 Windows Server AD 同步，或与 Windows Sever AD 或其他标识提供程序联盟。还可以将本地标识基础结构扩展到 Azure IaaS。有关详细信息，请参阅 [企业级结构设计版的 Microsoft 云标识](microsoft-cloud-identity-for-enterprise-architects.md)。
    
- 安全性
    
    混合云方案的安全性包括保护和管理标识、数据保护、管理权限管理、威胁感知和治理及安全策略的实施。有关详细信息，请参阅[面向企业架构师的 Microsoft 云安全性](https://technet.microsoft.com/library/dn919927.aspx#security)。
    
- 管理
    
    混合云方案的管理包括维护设置、数据、帐户、策略和权限以及监视正在进行的方案元素的运行状况及其性能的能力。也可使用相同的工具集（如 Systems Management Server）来管理 Azure IaaS 中的虚拟机。
    
## See Also

#### 

[面向企业架构师的 Microsoft 混合云](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
#### 

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)

