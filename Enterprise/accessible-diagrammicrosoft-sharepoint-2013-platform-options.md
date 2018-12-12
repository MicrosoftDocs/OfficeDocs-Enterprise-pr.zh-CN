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
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504315"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>可访问的图 - Microsoft SharePoint 2013 平台选项

**摘要：** 这篇文章是图名为 Microsoft SharePoint 2013 平台选项的辅助功能的文本版本。
  
哪些业务决策者 (Bdm) 和架构师需要了解有关 Office 365、 Microsoft Azure 和内部部署。 
  
此海报有两个部分： 
  
- 四种不同的部署的 SharePoint 2013 的比较： SharePoint 中 Office 365，SharePoint 2013、 Azure，和内部部署的 SharePoint 2013 在内部部署 Office 365 的混合。 
    
- 三个典型的工作负载，将移动到 Azure 的说明。 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>SharePoint 2013 平台的四种不同部署比较

比较提供了每个部署选项的信息，与以下方面相关： 
  
- 不同的部署功能的概述 
    
- 每种部署类型最适用于什么  
    
- 许可要求 
    
- 需执行的体系结构任务  
    
- IT 专业人员的实施职责  
    
### <a name="overview"></a>概述

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013 年

获得效率和优化用 Office 365 的多组织计划的成本。 
  
随附的图表显示 SharePoint Online Azure Active Directory 租户，其帐户名和密码的内部部署 Active Directory 环境和 Azure Active Directory 租户之间进行同步。 
  
功能说明： 
  
- 软件即服务 (SaaS)。 
    
- 丰富功能集始终保持最新。  
    
- 包括 Azure Active Directory 租户 （可以与其他应用程序使用）。 
    
- 目录集成包括帐户名和密码的内部部署 Active Directory 环境和 Azure Active Directory 租户之间进行同步。 
    
- 如果需要单一登录 (SSO)，可实施 Active Directory 联合身份验证服务 (AD FS)。   
    
- 通过由加密和身份验证访问的 Internet 的客户端通信（端口 443）。  
    
- 将数据迁移限制为可以通过 Internet 上载的内容。  
    
- 自定义项：Office 和 SharePoint 应用程序、SharePoint Designer 2013。  
    
#### <a name="hybrid-with-office-365"></a>与 Office 365 的混合

结合内部部署的 SharePoint 2013 Office 365 的好处。 
  
伴随的图显示了使用 Business Connectivity Services (BCS) 连接到内部部署 SharePoint Server 2013 场与 SharePoint Online 的 Office 365。 
  
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
  
伴随的图显示了 Azure，包含两个云服务、 SharePoint 2013 服务器场，以及使用 DNS 通过 Internet 连接到用户或连接到 VPN 隧道通过内部部署 Active Directory 的 Windows 服务器活动目录。 
  
这些功能包括：  
  
-  Azure 是承载 SharePoint 2013 群所需的基础结构和应用程序服务提供了一个平台。
    
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

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013 年

- 安全的外部共享和协作。（独特的功能！）  
    
- Intranet — 工作组网站、“我的网站”和内部协作。  
    
- 云中的文件存储和版本控制。  
    
- 面向公众的基本网站。  
    
与 Office 365 专门订阅计划的附加功能： 
  
- 专用于您的组织，且不与任何其他组织共享的 Microsoft 数据中心设备。   
    
- 所有客户环境都驻留在物理上分离的网络中。  
    
- 通过 IPsec 安全 VPN 或客户拥有的私人连接的客户端通信。可以选择双重身份验证。  
    
- ITAR 支持计划。  
    
#### <a name="hybrid-with-office-365"></a>与 Office 365 的混合

- 用于外部共享和协作而不是设置外部网环境中使用 Office 365。 
    
- 将“我的网站”(OneDrive for Business) 移动到云，使用户更易于远程访问文件。   
    
- Office 365 中启动新的工作组站点。 
    
- 与内部 BCS SharePoint 环境中集成 Office 365 站点。 
    
#### <a name="azure"></a>Azure

- 互联网网站的 SharePoint — — 公共对称的站点。利用 Azure 广告客户帐户和身份验证。 
    
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
    
- 与第三方组件取决于硬件和软件 Azure 的基础结构服务不支持旧式解决方案。 
    
- 隐私限制来防止同步的 Active Directory 帐户使用 Azure Active Directory （Office 365 的要求）。 
    
- 希望保持对整个平台和解决方案的控制的组织。 
    
### <a name="license-requirements"></a>许可要求

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013 年

订阅模型。无需其他许可证。  
  
#### <a name="hybrid-with-office-365"></a>与 Office 365 的混合

- Office 365  订阅模型。无需其他许可证。 
    
- 本地 — 所有本地许可证均适用。 
    
#### <a name="azure"></a>Azure

-  Azure 订阅 （包括服务器操作系统）
    
- SQL Server 
    
- SharePoint 2013 服务器许可证 
    
- SharePoint 2013 客户端访问许可证 
    
#### <a name="on-premises"></a>本地

- 服务器操作系统 
    
- SQL Server 
    
- SharePoint 2013 服务器许可证 
    
- SharePoint 2013 客户端访问许可证 
    
### <a name="architecture-tasks"></a>体系结构任务

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013 年

- 规划和设计目录集成。两个选项。这两个选项可以部署在内部或在 Azure 中: （需要一台 64 位服务器） 的密码同步。SSO （需要 AD FS 和多个服务器）。 
    
- 确保通过防火墙、代理服务器、网关以及跨 WAN 链接的网络容量和可用性。 
    
- 获取第三方 SSL 证书，提供 Office 365 服务/产品的企业安全性。 
    
- 规划租户名称，设计站点集体系结构和监管。  
    
- 针对 SharePoint Online 规划自定义项、解决方案和应用程序。  
    
- 如果您要通过使用 Internet 协议 6 (IPv6) 连接到 Office 365 的决定。这是不常见的。 
    
#### <a name="hybrid-with-office-365"></a>与 Office 365 的混合

除 Office 365 和本地环境的任务以外，还需： 
  
- 确定所需的功能集成数量，并选择混合拓扑。参阅此模型海报：我应使用哪个混合拓扑？  
    
- 确定将使用哪个代理服务器设备（如果需要）。  
    
#### <a name="azure"></a>Azure

设计 Azure 的网络环境： 
  
- 在 Azure，包括子网内的虚拟网络。 
    
- 域环境及与本地服务器的集成。  
    
- IP 地址和 DNS。  
    
- 地缘组和存储帐户。  
    
设计在 Azure 中的 SharePoint 环境中： 
  
- SharePoint 场拓扑和逻辑体系结构。  
    
-  Azure 可用性设置和更新域。
    
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

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013 年

- 确保用户工作站满足 Office 365 提供客户端系统必备组件。 
    
- 实施目录集成计划。 
    
- 规划和实施内部和外部 DNS 记录和路由。 
    
- 配置代理服务器或防火墙进行 Office 365 IP 地址和 URL 的要求。 
    
- 创建并分配权限给网站集。  
    
- 针对 SharePoint Online 实施自定义项、解决方案和应用程序。  
    
- 监控网络可用性并识别可能的瓶颈。  
    
#### <a name="hybrid-with-office-365"></a>与 Office 365 的混合

除 Office 365 和本地环境的任务以外，还需： 
  
- 配置代理服务器设备（如果需要）。 
    
- 配置混合标识管理基础结构：两个环境之间的 SSO 和服务器间身份验证。  
    
- 配置选定功能的集成：Search、BCS、Duet Enterprise Online。  
    
#### <a name="azure"></a>Azure

部署和管理的 Azure 和 SharePoint 环境： 
  
- 实施和管理 Azure 的网络环境。 
    
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
    
## <a name="three-typical-workloads-to-move-to-azure"></a>三个典型的工作负载，将移动到 Azure

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 加在 Azure 中的目录组件

更快地部署 Office 365 Azure 中的目录集成组件是，因为它可以部署虚拟机需求。 
  
#### <a name="directory-synchronization-server-only"></a>仅限目录同步服务器。

而不是部署 64 位目录同步服务器在您的内部环境，而是设置 Azure 中的虚拟机。 
  
随附的图表显示 SharePoint Online Azure Active Directory 租户，其帐户名和密码的内部部署 Active Directory 环境和 Azure Active Directory 租户之间进行同步。 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>目录同步 + AD FS

此选项允许您添加到您的内部部署基础结构硬件支持 Office 365 联合标识 (SSO)。如果内部部署 Active Directory 环境不可用，它还提供可恢复性。 
  
- 目录集成组件驻留在 Azure。 
    
- AD FS 到 Azure 中的 AD FS 代理服务器通过互联网发布。 
    
- 由 AD FS 服务器和代理服务器部署在 Azure 处理客户端身份验证通信，从任意位置，连接的用户。 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>面向公众的互联网网站和 Azure 广告客户身份验证

利用能够容易地进行扩展的需求放在 Azure 的 Internet 站点。使用 Azure AD 存储客户帐户。 
  
#### <a name="azure-advantages-for-internet-sites"></a>Azure 的互联网网站的优点

- 通过根据场使用情况增加或减少虚拟机数量，从而仅针对所需资源付费。  
    
- 添加深入报告和 Web 分析。 
    
- 重点关注开发出色的网站，而不是构建基础结构。 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD 提供云服务的管理和访问控制功能。功能包括目录数据和一套核心标识服务，包括用户登录进程、 身份验证服务和 AD FS 的云存储。附带 Azure AD 身份服务轻松地集成与内部部署 Active Directory 部署和全面支持第三方身份提供程序。 
  
伴随图表显示区域和重要的面向 Internet 站点的身份验证的配置。该图显示了 Azure 活动目录租户，其中包含了两个区域在 Azure 上 SharePoint 服务器场： 
  
- 与网络外的匿名和经过身份验证的访客和客户进行交互的 Internet 区域  
    
- 包含用于爬网的 NTLM 和 Windows 身份验证的默认区域，通过 VPN 隧道与本地 Active Directory 部署交互。   
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>内部部署服务器场加 Azure 中的灾难恢复

选择一种灾难恢复选项满足您的业务要求。Azure 提供入门级的公司开始使用灾难恢复选项和高级选项具有高的弹性需求的企业。 
  
#### <a name="cold-standby"></a>冷备用

- 场完全生成的但虚拟机都已停止。（您付钱让他们只能在运行时 ！） 
    
- 维护环境包括偶尔启动虚拟机，以及修补、更新和验证环境。 
    
- 启动完整环境发生灾难时。 
    
#### <a name="warm-standby"></a>温备用

- 包括已设置并正在运行的小场。   
    
- 此场可以在发生故障转移时立即为用户进行处理。   
    
- 迅速横向扩展场，以服务于所有用户。  
    
#### <a name="hot-standby"></a>热备用

设置一个完全大小的服务器场，且以备用状态运行。 
  
伴随图显示内部场相互作用在 Azure 上 SharePoint 灾难恢复环境。内部数据库使用 SQL Server 日志传送通过 VPN 隧道访问 SharePoint 灾难恢复环境，其中包括两个包含 SharePoint 数据库、 两个 Web 前端服务器和两个 SharePoint 的 SQL 数据库服务器应用程序服务器。 
  

