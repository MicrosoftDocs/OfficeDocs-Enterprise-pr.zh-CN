---
title: 可访问的图 - Microsoft SharePoint 2013 平台选项
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: 本文是名为“Microsoft SharePoint 2013 平台选项”的图的可访问文本版本。
ms.openlocfilehash: 1f0d2bf4e74c7e1d28aaa27c6f88dac04f02b4a9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487818"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>可访问的图 - Microsoft SharePoint 2013 平台选项

**摘要:** 本文是名为 Microsoft SharePoint 2013 平台选项的图表的可访问文本版本。
  
业务决策者 (bdm) 和架构师需要了解 Office 365、Microsoft Azure 和本地部署。 
  
此海报有两个部分： 
  
- sharepoint 2013 的四种不同部署的比较: office 365 中的 sharepoint、office 365 的混合, 以及 sharepoint 的本地部署 sharepoint 2013、Azure 和本地部署的 sharepoint 2013。 
    
- 对要移动到 Azure 的三个典型工作负荷的说明。 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>SharePoint 2013 平台的四种不同部署比较

比较提供了每个部署选项的信息，与以下方面相关： 
  
- 不同的部署功能的概述 
    
- 每种部署类型最适用于什么  
    
- 许可要求 
    
- 需执行的体系结构任务  
    
- IT 专业人员的实施职责  
    
### <a name="overview"></a>概述

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

使用 Office 365 多租户计划提高效率并优化成本。 
  
随附的图显示了具有 Azure active directory 租户的 SharePoint Online, 这将同步本地 Active directory 环境和 Azure Active directory 租户之间的帐户名称和密码。 
  
功能说明： 
  
- 软件即服务 (SaaS)。 
    
- 丰富功能集始终保持最新。  
    
- 包含 Azure Active Directory 租户 (可用于其他应用程序)。 
    
- 目录集成包括在本地 Active directory 环境和 Azure Active directory 租户之间同步帐户名称和密码。 
    
- 如果需要单一登录 (SSO)，可实施 Active Directory 联合身份验证服务 (AD FS)。   
    
- 通过由加密和身份验证访问的 Internet 的客户端通信（端口 443）。  
    
- 将数据迁移限制为可以通过 Internet 上载的内容。  
    
- 自定义项：Office 和 SharePoint 应用程序、SharePoint Designer 2013。  
    
#### <a name="hybrid-with-office-365"></a>与 Office 365 的混合

将 Office 365 的优势与 SharePoint 2013 的本地部署结合使用。 
  
随附的图显示了使用 Business Connectivity Services (BCS) 连接到本地 sharepoint Server 2013 场的 Office 365 with sharepoint Online。 
  
选择要集成下列哪一项功能：  
  
SharePoint 搜索 
  
- 用户可以看到两个环境的搜索结果。   
    
- Extranet 用户可以使用本地 Active Directory 帐户远程登录，并使用所有可用的混合功能。  
    
BCS
  
从 SharePoint Online：用户可以执行读取和写入操作。BCS 服务连接到本地 SharePoint Server 2013 场。在本地场配置的 BCS 服务充当连接到本地 OData 服务终结点的中介。   
  
Duet Enterprise Online 
  
从 SharePoint Online，用户可以对本地 SAP 系统执行读取和写入操作。  
  
#### <a name="azure"></a>Azure

保留对平台和功能的完全控制权的同时利用云的优势。   
  
随附的图显示了 Azure, 其中包含两个云服务、一个 SharePoint 2013 服务器场和 Windows Server Active directory, 并通过 Internet 连接到用户或通过 VPN 隧道连接到本地 Active directory。 
  
这些功能包括：  
  
-  Azure 是一个平台, 可提供托管 SharePoint 2013 服务器场所需的基础结构和应用程序服务。
    
- 基础结构服务。 
    
- SQL Server 和 SharePoint 的最佳本地云平台。  
    
- 计算资源无需提交，几乎即刻可用。  
    
- 关注应用程序，而非数据中心和基础结构。  
    
- 廉价的开发和测试环境。  
    
- 可从 Internet 访问 SharePoint 解决方案，也可仅通过站点到站点 VPN 隧道从公司环境访问 SharePoint 解决方案。  
    
- 不限制自定义项。  
    
#### <a name="on-premises"></a>本地

您拥有一切。   
  
随附的图显示了具有与所有数据库和专用应用程序服务器通信以进行搜索的 Web 服务器、应用程序服务器和 Active Directory 的本地环境。  
  
这些功能包括：  
  
- 容量规划和大小调整。 
    
- 服务器购置和设置。  
    
- 部署。 
    
- 横向扩展、修补和操作。   
    
- 备份数据。 
    
- 维护灾难恢复环境。 
    
- 不限制自定义项。  
    
### <a name="deployment-type-is-best-for---"></a>部署类型最适用于. . .

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

- 安全的外部共享和协作。（独特的功能！）  
    
- Intranet — 工作组网站、“我的网站”和内部协作。  
    
- 云中的文件存储和版本控制。  
    
- 面向公众的基本网站。  
    
Office 365 专用订阅计划的附加功能: 
  
- 专用于您的组织，且不与任何其他组织共享的 Microsoft 数据中心设备。   
    
- 所有客户环境都驻留在物理上分离的网络中。  
    
- 通过 IPsec 安全 VPN 或客户拥有的私人连接的客户端通信。可以选择双重身份验证。  
    
- ITAR 支持计划。  
    
#### <a name="hybrid-with-office-365"></a>与 Office 365 的混合

- 使用 Office 365 进行外部共享和协作, 而不是设置 extranet 环境。 
    
- 将“我的网站”(OneDrive for Business) 移动到云，使用户更易于远程访问文件。   
    
- 在 Office 365 中启动新的团队网站。 
    
- 将 Office 365 网站与本地 BCS SharePoint 环境集成。 
    
#### <a name="azure"></a>Azure

- Internet 网站的 SharePoint — 面向公众的网站。 充分利用 Azure AD 进行客户帐户和身份验证。 
    
- 开发人员、测试和暂存环境 — 快速设置整个环境和取消整个环境的设置。  
    
- 混合应用程序 — 跨越数据中心和云的应用程序。  
    
- 灾难恢复环境 — 从灾难中快速恢复。仅对使用的部分付费。  
    
- 要求深入报告或审核的场。  
    
- Web 分析。 
    
- 静止状态时的数据加密（在 SQL 数据库中加密数据）。  
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>静止状态时的数据加密（在 SQL 数据库中加密数据）

- 国家/地区内场（要求将数据驻留在管辖范围内时）。  
    
- 必须驻留在 BI 数据旁边的复杂 BI 解决方法。  
    
- 私有云解决方案。  
    
- 高度自定义的解决方案。 
    
- 具有第三方组件的旧版解决方案, 这些组件依赖于 Azure 基础结构服务不支持的硬件和软件。 
    
- 防止 active directory 帐户与 Azure active directory 同步的隐私限制 (Office 365 的要求)。 
    
- 希望保持对整个平台和解决方案的控制的组织。 
    
### <a name="license-requirements"></a>许可要求

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

订阅模型。 无需其他许可证。 
  
#### <a name="hybrid-with-office-365"></a>与 Office 365 的混合

- Office 365  订阅模型。无需其他许可证。 
    
- 本地 — 所有本地许可证均适用。 
    
#### <a name="azure"></a>Azure

-  Azure 订阅 (包括服务器操作系统)
    
- SQL Server 
    
- SharePoint 2013 服务器许可证 
    
- SharePoint 2013 客户端访问许可证 
    
#### <a name="on-premises"></a>本地

- 服务器操作系统 
    
- SQL Server 
    
- SharePoint 2013 服务器许可证 
    
- SharePoint 2013 客户端访问许可证 
    
### <a name="architecture-tasks"></a>体系结构任务

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

- 规划和设计目录集成。 两个选项。 这两个选项都可以在本地部署或在 Azure 中部署: 密码同步 (需要 1 64 位服务器)。 SSO（需要 AD FS 和多个服务器）。 
    
- 确保通过防火墙、代理服务器、网关以及跨 WAN 链接的网络容量和连接。 
    
- 获取第三方 SSL 证书，提供 Office 365 服务/产品的企业安全性。 
    
- 规划租户名称，设计站点集体系结构和监管。  
    
- 针对 SharePoint Online 规划自定义项、解决方案和应用程序。  
    
- 决定是否要使用 Internet 协议 6 (IPv6) 连接到 Office 365。 这并不常见。 
    
#### <a name="hybrid-with-office-365"></a>与 Office 365 的混合

除 Office 365 和本地环境的任务以外，还需： 
  
- 确定所需的功能集成数量，并选择混合拓扑。参阅此模型海报：我应使用哪个混合拓扑？  
    
- 确定将使用哪个代理服务器设备（如果需要）。  
    
#### <a name="azure"></a>Azure

设计 Azure 网络环境: 
  
- Azure 中的虚拟网络, 包括子网。 
    
- 域环境及与本地服务器的集成。  
    
- IP 地址和 DNS。  
    
- 地缘组和存储帐户。  
    
在 Azure 中设计 SharePoint 环境: 
  
- SharePoint 场拓扑和逻辑体系结构。  
    
-  Azure 可用性集和更新域。
    
- 虚拟机大小。   
    
- 负载平衡的终结点。  
    
- 公共访问的外部终结点（如果需要）。   
    
- 灾难恢复环境。  
    
#### <a name="on-premises"></a>本地

在现有本地环境中设计 SharePoint 环境：  
  
- SharePoint 场拓扑和逻辑体系结构。  
    
- 服务器硬件。 
    
- 虚拟环境（如已使用）。  
    
- 负载平衡。 
    
- 与 AD DS 和 DNS 集成。   
    
- 灾难恢复环境。  
    
### <a name="it-pro-responsibilities"></a>IT 专业人员的职责

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

- 确保用户工作站满足 Office 365 客户端的先决条件。 
    
- 实施目录集成计划。 
    
- 规划和实施内部和外部 DNS 记录和路由。 
    
- 为 Office 365 IP 地址和 URL 要求配置代理或防火墙。 
    
- 创建并分配权限给网站集。  
    
- 针对 SharePoint Online 实施自定义项、解决方案和应用程序。  
    
- 监控网络可用性并识别可能的瓶颈。  
    
#### <a name="hybrid-with-office-365"></a>与 Office 365 的混合

除 Office 365 和本地环境的任务以外，还需： 
  
- 配置代理服务器设备（如果需要）。 
    
- 配置混合标识管理基础结构：两个环境之间的 SSO 和服务器间身份验证。  
    
- 配置选定功能的集成：Search、BCS、Duet Enterprise Online。  
    
#### <a name="azure"></a>Azure

部署和管理 Azure 和 SharePoint 环境: 
  
- 实施和管理 Azure 网络环境。 
    
- 部署 SharePoint 环境。 
    
- 更新 SharePoint 场服务器。  
    
- 按需要根据场使用率添加或关闭虚拟机。  
    
- 根据需要增加或减少虚拟机大小。  
    
- 备份 SharePoint 环境。 
    
- 实施灾难恢复环境和协议。  
    
#### <a name="on-premises"></a>本地

在本地环境中部署和管理 SharePoint：  
  
- 设置服务器。 
    
- 部署 SharePoint 环境。 
    
- 更新 SharePoint 场服务器。  
    
- 按需要根据场使用率添加或删除场服务器。  
    
- 备份 SharePoint 环境。 
    
- 实施灾难恢复环境和协议。  
    
## <a name="three-typical-workloads-to-move-to-azure"></a>移动到 Azure 的三个典型工作负载

### <a name="office-365-plus-directory-components-in-azure"></a>Azure 中的 Office 365 和目录组件

在 Azure 中部署 Office 365 目录集成组件的速度更快, 因为它可以按需部署虚拟机。 
  
#### <a name="directory-synchronization-server-only"></a>仅限目录同步服务器。

而不是在本地环境中部署64位目录同步服务器, 而是在 Azure 中设置虚拟机。 
  
随附的图显示了具有 Azure active directory 租户的 SharePoint Online, 这将同步本地 Active directory 环境和 Azure Active directory 租户之间的帐户名称和密码。 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>目录同步 + AD FS

此选项使您可以支持 Office 365 联合身份 (SSO)，而无需将硬件添加到内部部署基础架构。 如果本地 Active Directory 环境不可用，它还可以提供复原。 
  
- 目录集成组件驻留在 Azure 中。 
    
- ad fs 通过 Azure 中的 ad fs 代理发布到 Internet。 
    
- 对于从任何位置连接的用户, 客户端身份验证流量由在 Azure 上部署的 AD FS 服务器和代理进行处理。 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>面向公众的 Internet 站点和用于客户身份验证的 Azure AD

通过在 Azure 中放置 Internet 网站, 可以充分利用轻松扩展到需求的功能。 使用 Azure AD 存储客户帐户。 
  
#### <a name="azure-advantages-for-internet-sites"></a>Internet 站点的 Azure 优势

- 通过根据场使用情况增加或减少虚拟机数量，从而仅针对所需资源付费。  
    
- 添加深入报告和 Web 分析。 
    
- 重点关注开发出色的网站，而不是构建基础结构。 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD 为云服务提供了身份管理和访问控制功能。 功能包括目录数据的基于云的存储和一组核心标识服务, 包括用户登录过程、身份验证服务和 AD FS。 Azure AD 附带的标识服务可轻松地与本地 Active Directory 部署集成, 并完全支持第三方标识提供程序。 
  
随附的图显示了对于面向 Internet 的站点非常重要的区域和身份验证配置。 该图显示了 azure Active Directory 租户, 其中包含包含两个区域的 azure 上的 SharePoint 场: 
  
- 与网络外的匿名和经过身份验证的访客和客户进行交互的 Internet 区域  
    
- 包含用于爬网的 NTLM 和 Windows 身份验证的默认区域，通过 VPN 隧道与本地 Active Directory 部署交互。   
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>内部部署服务器场和 Azure 中的灾难恢复

选择与您的业务需求相符的灾难恢复选项。 Azure 为具有高恢复能力要求的企业开始使用灾难恢复和高级选项, 提供了入门级选项。 
  
#### <a name="cold-standby"></a>冷备用

- 服务器场已完全构建，但虚拟机已停止。 (仅在正在运行时付费!) 
    
- 维护环境包括偶尔启动虚拟机，以及修补、更新和验证环境。 
    
- 启动完整环境发生灾难时。 
    
#### <a name="warm-standby"></a>温备用

- 包括已设置并正在运行的小场。   
    
- 此场可以在发生故障转移时立即为用户进行处理。   
    
- 迅速横向扩展场，以服务于所有用户。  
    
#### <a name="hot-standby"></a>热备用

设置一个完全大小的服务器场，且以备用状态运行。 
  
随附的图显示了与 Azure 上的 SharePoint 灾难恢复环境交互的本地服务器场。 内部部署数据库使用 SQL Server 日志传送通过 VPN 隧道访问 SharePoint 灾难恢复环境，其中包括两台包含 SharePoint 数据库的 SQL 数据库服务器、两台 Web 前端服务器和两台 SharePoint 应用程序服务器。 
  

