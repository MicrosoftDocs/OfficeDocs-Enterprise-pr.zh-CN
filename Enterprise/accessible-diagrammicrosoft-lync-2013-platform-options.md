---
title: 可访问的图 - Microsoft Lync 2013 平台选项
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: 本文是名为 Microsoft Exchange 2013 平台选项的图的可访问文本版本，您可在技术图表中找到此图。
ms.openlocfilehash: 4a660df4bfacad2a00f5d9fbb5e1b668840e3b9f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487782"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>可访问的图 - Microsoft Lync 2013 平台选项

**摘要：** 本文是[技术图表](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)中的“Microsoft Lync 2013 平台选项”图表的可访问文本版本。
  
本海报介绍哪些业务决策者 (BDM) 和架构师需要了解 Lync Online (Office 365) 和 Lync Server 部署，其中包含以下内容：
  
- 四个不同的部署选项比较：Lync Online (Office 365)、Lync Online/Server 混合、Lync Server 和提供程序承载的 Lync Server。 
    
- 部署 Lync 2013 的两个示例方案。
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>Lync 2013 平台的四种不同部署比较

比较提供了每个部署选项的信息，包括以下方面： 
  
- 不同的部署功能的概述
    
- 实施每个部署选项的优点
    
- 许可要求
    
- 所需的体系结构任务
    
- IT 专业人员对实施每个部署选项的职责
    
### <a name="overview"></a>概述

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

使用 Office 365 多租户计划提高效率并优化成本。
  
随附的图显示了具有 Azure Active Directory 租户的 Lync Online，它可在本地 Active Directory 域服务 (AD DS) 环境和 Azure Active Directory 租户之间同步帐户名称和密码。 
  
功能描述：
  
- 软件即服务 (SaaS)。
    
- 始终保持最新的丰富功能集。
    
- 包括用于联机帐户的 Azure Active Directory 租户（可用于其他应用程序）。 
    
- 目录集成包括同步本地 Active Directory 域服务 (AD DS) 环境和 Azure Active Directory 租户之间的帐户名称和密码。
    
- 如果需要单一登录 (SSO)，可实施 Active Directory 联合身份验证服务 (AD FS)。 
    
- 通过 Internet 的客户端通信将会加密并进行身份验证。
    
- 对于传统电话设备和公共交换电话网络 (PSTN)，连接通过第三方提供程序实现。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server 混合（拆分域）

您可以将 Office 365 的优势与 Lync 2013 的本地部署相结合。
  
随附的图中显示具有 Lync Online 的 Office 365，其中部分用户位于本地，部分用户处于联机状态。此外还显示了部署在本地的边缘服务器。
  
功能描述：
  
- 部分用户位于本地，部分用户处于联机状态，但用户共享同一个 SIP 域（例如 contoso.com）。
    
- 利用您现有的 Lync Server 2013 基础结构，包括到 PSTN 的连接。
    
- 当用户不需要 PSTN 时轻松添加新的 Lync Online 用户。
    
- 按照您的安排，在一段时间后从 Lync 本地迁移到 Lync Online。
    
- 与其他 Office 365 应用程序集成，包括 Exchange Online 和 SharePoint Online。
    
#### <a name="lync-server"></a>Lync Server

在该部署中，您掌控一切。随附的图显示了具有本地 Active Directory 域服务 (AD DS) 环境的 Lync Server 基础结构，其中用户位于本地。
  
功能描述：
  
- 容量规划和大小。
    
- 服务器购置和设置。 
    
- 部署。
    
- 横向扩展、修补和操作。  
    
- 备份数据。
    
- 维护故障转移和灾难恢复。
    
- 将您的 Lync Server 2013 基础结构连接到 PSTN。
    
- 与现有电话设备集成，如专用分组交换机 (PBX)。
    
#### <a name="provider-hosted-lync-server"></a>提供商承载的 Lync Server

在该部署中，您的提供商掌控一切。随附的图显示了提供商的网络，其中包括他们的服务器和设备以及到本地环境的连接。
  
功能描述：
  
- 容量规划和大小。
    
- 服务器购置和设置。 
    
- 部署。
    
- 横向扩展、修补和操作。  
    
- 备份数据。
    
- 维护故障转移和灾难恢复。
    
- 与现有电话设备集成，如专用分组交换机 (PBX)。
    
- 此外，提供商还可以：
    
  - 在自己的网络中安装他们的服务器和设备，并连接到您的内部部署（实线）。
    
  - 在本地安装他们的服务器（虚线）。
    
### <a name="benefits-of-implementing-each-deployment-option"></a>实现每个部署选项的优点

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- 本地服务器或服务器软件没有运营负担。
    
- Lync Server 2013 作为基于云的服务的通信功能。
    
- Lync 状态、即时消息、音频和视频呼叫、丰富的在线会议和一系列 Web 会议功能。
    
- 用于地理分散的组织或主要为移动状态的员工。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server 混合（拆分域）

- 对远程用户使用 Lync Online，并与业务合作伙伴集成。
    
- 加速从 Lync 本地到 Lync Online 的迁移。
    
- 无需使用分支办公室设备即可支持远程站点。
    
- 轻松增加对新业务收购的 Lync 支持。
    
#### <a name="lync-server"></a>Lync Server

- 私有云解决方案。
    
- 高度自定义的解决方案。
    
- 具有第三方组件的旧版解决方案，而这些组件依赖于不受 Lync Online 支持的硬件和软件。
    
- 阻止 AD DS 帐户与 Office 365 同步的隐私限制。
    
- 希望保持对整个平台和解决方案的控制的组织。
    
- Lync Enterprise Voice 取代 PBX。
    
#### <a name="provider-hosted-lync-server"></a>提供商承载的 Lync Server

- 需要 Lync Server 功能，但希望外包其部署和维护的组织。
    
- 基于提供商的解决方案
    
- 高度自定义的解决方案。
    
- 具有第三方组件的旧版解决方案，而这些组件依赖于不受 Lync Online 支持的硬件和软件。
    
- Lync Enterprise Voice 取代 PBX。
    
### <a name="license-requirements"></a>许可要求

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

订阅模型。
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server 混合（拆分域）

- Office 365  订阅模型。无需其他许可证。 
    
- 本地 — 所有本地许可证均适用。 
    
#### <a name="lync-server"></a>Lync Server

- 服务器操作系统
    
- SQL Server
    
- Lync 2013 Server 许可证
    
- Lync 2013 客户端访问许可证
    
#### <a name="provider-hosted-lync-server"></a>提供商承载的 Lync Server

成本基于与 Lync 解决方案提供商签订的协议。
  
### <a name="architecture-tasks"></a>体系结构任务

本节列出了每个部署选项的体系结构任务。
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- 规划和设计目录同步。
    
- 确保通过防火墙、代理服务器、网关以及跨 WAN 链接的网络容量和可用性。
    
- 获取第三方 SSL 证书，提供 Office 365 服务/产品的企业安全性。
    
- 决定是否要使用 Internet 协议版本 6 (IPv6) 连接到 Office 365。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server 混合（拆分域）

除 Office 365 和本地环境的任务以外，还需：
  
- 确定您希望在 Exchange Server 和 SharePoint 的本地版本和联机版本中使用多少功能集成。
    
- 确定对于 Office 365 的请求将使用哪个代理服务器设备（如果需要）。
    
#### <a name="lync-server"></a>Lync Server

在现有本地环境中设计 Lync 环境：
  
- 中央和分支办公室的 Lync 拓扑。
    
- 服务器硬件，包括虚拟化。
    
- 与 Active Directory 域服务 (AD DS) 和 DNS 集成。
    
- Lync 服务器池的负载平衡。
    
- 故障转移和灾难恢复。
    
#### <a name="provider-hosted-lync-server"></a>提供商承载的 Lync Server

- 对于基于云的安装，确定到服务提供商网络的连接。
    
- 对于本地安装，确定提供商的 Lync 服务器在网络中的位置。
    
- 对于两种类型的安装，确定 AD DS 与您的 PBX 设备的集成。
    
### <a name="it-pro-responsibilities"></a>IT 专业人员的职责

本节列出了 IT 专业人员对每个部署选项的职责。
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

部署和管理 Lync Online (Office 365)：
  
- 实施目录同步计划。
    
- 规划和实施内部和外部 DNS 记录和路由。
    
- 针对 Office 365 IP 地址和 URL 要求配置代理或防火墙。
    
- 管理用户帐户和 Lync Online 设置。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/Server 混合（拆分域）

除 Office 365 和本地环境的任务以外，还需：
  
- 配置代理服务器设备（如果需要）。
    
- 配置与 Exchange Server 和 SharePoint 的本地版本和联机版本的功能集成。
    
#### <a name="lync-server"></a>Lync Server

在本地环境中部署和管理 Lync Server：
  
- 设置服务器。
    
- 部署 Lync 拓扑。
    
- 更新 Lync 服务器。
    
- 按需要根据使用率添加或删除拓扑服务器。
    
- 实施故障转移和灾难恢复环境。
    
#### <a name="provider-hosted-lync-server"></a>提供商承载的 Lync Server

与提供商合作以：
  
- 将 Lync Server 集成到您的网络中。
    
- 将 Lync Server 与其他 Microsoft 产品或自定义解决方案集成。
    
- 监控提供商服务级别协议 (SLA) 的遵守情况。
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>部署 Lync 2013 的两个示例方案

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Microsoft Azure 中的目录同步组件

根据需要部署虚拟机的能力使得在 Azure 中部署 Office 365 目录同步组件更加快捷。
  
随附的图显示了具有 Azure Active Directory 租户的 Lync Online，它可在本地 Active Directory 环境和 Azure Active Directory 租户之间同步帐户名称和密码。
  
 **仅限目录同步服务器**。不在本地环境中部署 64 位目录同步，而应通过 Internet 在 Azure 中配置虚拟机。
  
 **目录同步 + AD FS**。此选项使您可以支持 Office 365 联合身份 (SSO)，而无需将硬件添加到内部部署基础架构。如果本地 Active Directory 环境不可用，它还可以提供复原。此选项的功能包括：
  
- 目录集成组件作为 Azure 虚拟机运行。
    
- 通过作为 Azure 虚拟机运行的 AD FS 代理将 AD FS 发布到 Internet。
    
- 对于从任何位置连接的用户，客户端身份验证通信由部署为 Azure 虚拟机的 AD FS 服务器和代理处理。
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Office 365 中与 Exchange 和 SharePoint 的 Lync 集成

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Lync Server with Exchange Online 和 SharePoint Online

随附的图显示了连接到本地 Lync Server 2013 服务器场的 Office 365 with Exchange Online 和 SharePoint Online。
  
此部署的优势使您能够：
  
- 使用 Lync Server 2013 的完整功能集。
    
- 利用现有的本地电话设备，例如 PBX。
    
- 将 Exchange Online 用于电子邮件，减轻本地电子邮件服务器和存储的负担。
    
- 将 SharePoint Online 用于协作，减轻维护本地 SharePoint 服务器的负担。
    
- 使用 Lync、Exchange 和 SharePoint 集成功能，包括 Office 365 中的统一消息 (UM)。
    
#### <a name="exchange-server-with-lync-online"></a>Exchange Server with Lync Online

随附的图显示了连接到本地 Exchange Server 服务器场的 Office 365 with Lync Online。
  
此部署的优势使您能够：
  
- 利用现有的 Exchange 基础结构。
    
- 将 Lync Online 用于状态、即时消息和会议功能。
    

