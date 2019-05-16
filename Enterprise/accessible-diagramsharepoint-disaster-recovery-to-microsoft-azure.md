---
title: 可访问的图表 - SharePoint 灾难恢复到 Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: 本文是名为“SharePoint 灾难恢复到 Microsoft Azure”的图的可访问文本版本。
ms.openlocfilehash: d7df0f44dd4e7f0cbb8580029991bc9280892afb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068518"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>可访问的图表 - SharePoint 灾难恢复到 Microsoft Azure

**摘要:** 本文是名为 "SharePoint 灾难恢复到 Microsoft Azure" 的图表的可访问文本版本。
  
此海报提供了用于在 Azure 中构建恢复环境的体系结构的示例。  
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>具有 Azure 恢复环境的本地环境

此图显示了使用 Azure 进行恢复的本地环境的生产环境使用的体系结构示例。  
  
### <a name="on-premises-production-environment"></a>本地生产环境

随附的图显示了在服务器场中具有四个服务器层级的真实生产环境。  
  
#### <a name="tier-1"></a>第 1 层

有两台服务器用于前端服务和查询处理。有一个索引分区提供两台服务器的副本。  
  
#### <a name="tier-2"></a>第 2 层

有两台服务器用于该层的分布式缓存。  
  
#### <a name="tier-3"></a>第 3 层

该层有三台服务器。每台服务器提供以下服务：  
  
- 后端服务  
    
- Admin 
    
- 工作流管理器 
    
- 爬网 
    
- 内容处理 
    
- 分析 
    
#### <a name="tier-4"></a>第 4 层

该层有两台服务器。两台服务器均具有三个可用性组，如下所示：  
  
- 可用性组 #1 提供搜索功能。  
    
- 可用性组 #2 提供内容、配置和服务应用程序。  
    
- 可用性组 #3 提供内容。  
    
该层还有一台文件共享服务器。第 4 层服务器使用日志传送与此服务器通信。该服务器反过来又会通过分布式文件系统复制 (DFSR) 与 Azure 热待机恢复环境中的文件共享服务器通信，如下面一节中所述。  
  
### <a name="azure-recovery-environment"></a>Azure 恢复环境

#### <a name="warm-standby-environment-running-virtual-machines"></a>运行虚拟机的热备用环境

随附的图显示了在 Azure 恢复环境中完全复制的本地环境。此环境中的文件共享服务器通过 DFSR 链接到本地环境。DFSR 将日志通过文件共享服务器从生产环境传输到恢复环境。  
  
### <a name="overview"></a>概述

本地 SharePoint 2013 场的灾难恢复环境可以托管在 Azure 中。 
  
-   Azure 基础结构服务提供辅助的数据中心。 
    
- 仅为您使用的资源付费。 
    
- 发生灾难后可将小型恢复服务器场向外扩展，以满足规模和容量目标。  
    
Azure 中的恢复服务器场配置得尽可能与生产内部部署服务器场相同。  
  
- 服务器角色的表示形式相同。 
    
- 自定义配置相同。  
    
- 搜索功能的配置相同（可以是小型的生产服务器）。  
    
日志传送和 DFSR 用于将数据库备份和事务日志复制到 Azure 服务器场。  
  
- DFSR 用于将日志从生产环境传输到恢复环境。在 WAN 方案中，DFSR 比将日志直接传输到 Azure 中的辅助服务器更有效。 
    
- 日志重放到基于 Azure 的 SQL Server 计算机。  
    
- 进行日志传送的数据库不会连接到服务器场，直到执行恢复操作。 
    
故障转移过程：  
  
1. 停止日志传送。 
    
2. 停止接受到主服务器场通信。 
    
3. 重播最后的事务日志。 
    
4. 将内容数据库附加到服务器场。 
    
5. 启动完全爬网。 
    
6. 从复制的服务数据库中还原服务应用程序。 
    
此解决方案提供的恢复目标包括：  
  
- 网站和内容 
    
- 搜索（重新爬网，无搜索历史记录）  
    
- 服务
    
Microsoft 咨询服务或合作伙伴可以解决的其他事项：  
  
- 正在同步的自定义场解决方案 
    
- 到本地数据源的连接（Business Data Connectivity (BDC) 和搜索内容源）  
    
- 搜索还原方案 
    
- 恢复时间目标 (RTO) 和恢复点目标 (RPO) 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>运行虚拟机的冷备用环境

冷备用环境需要更长时间启动，但成本更低  
  
- 服务器场已完全构建，但虚拟机在服务器场创建后已停止。当虚拟机运行时，您仅支付处理成本，但存储和网络数据传输成本也适用。  
    
- 如果发生灾难，服务器场中的所有虚拟机都将启动和修补。  
    
- 备份和事务日志将应用到服务器场数据库。  
    
以下列表介绍了冷备用环境的附加过程：  
  
- 定期打开虚拟机以进行修补、更新并验证环境。  
    
- 运行相应程序以刷新 DNS 和 IP 地址。  
    
- 在故障转移之后设置 SQL AlwaysOn。  
    
随附的图显示了虚拟机上的复制恢复环境。故障转移到冷备用环境后，所有虚拟机均已启动，且所有可用性组均已使用重放日志配置为提供数据库服务器。  
  
## <a name="sharepoint-recovery-environment-in-azure"></a>Azure 中的 SharePoint 恢复环境

设计和构建 Azure 中的故障转移环境  
  
- 在 Azure 中创建虚拟网络。 
    
- 通过站点间 VPN 连接，将内部部署网络与 Azure 中的虚拟网络相连接。此连接使用 Azure 中的动态网关。  
    
- 将一个或多个域控制器部署到 Azure 虚拟网络，并将其配置为与内部部署域一起使用。这些域控制器是目录服务器。  
    
- 调整 SharePoint 服务器场使其适用于云服务和可用性集。   
    
- 部署 SharePoint 服务器场加上一台文件服务器以承载文件共享。  
    
- 在本地环境和基于 Azure 的恢复环境之间设置日志传送和 DFSR。  
    
随附的图显示了具有下列功能的本地环境和 Azure 虚拟网络：  
  
### <a name="on-premises-environment"></a>内部部署环境

- Windows Server 2012 RRAS  
    
- Active Directory 服务器 
    
通过虚拟专用网络 (VPN) 网关与 Azure 虚拟网络的本地网络接口。  
  
### <a name="azure-virtual-network"></a>Azure 虚拟网络

与活动 VPN 网关子网的 VPN 网关接口。  
  
Azure 虚拟网络中具有三项云服务： 
  
- 第一项云服务具有两台具有可用性集的 Active Directory 和 DNS 服务器。  
    
- 第二项云服务有三个服务器组： 两台具有可用性集的分布式缓存服务器。 两台具有可用性集的前端服务器。 三台具有可用性集的后端服务器。
    
- 第三项云服务具有三台具有可用性集的数据库服务器。其中一台数据库服务器是用于日志传送的文件共享以及 SQL Server AlwaysOn 节点多数的第三个节点。  
    
### <a name="build-the-ad-ds-hybrid-environment"></a>构建 AD DS 混合环境

此解决方案的 AD DS 配置构成混合部署方案，其中 AD DS 一部分部署在本地，一部分部署在 Azure 虚拟机上。  
  
重要说明: 在 Azure 中部署 AD DS 之前, 请阅读在 Microsoft Azure 虚拟机 (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)) 上部署 Windows Server Active Directory 的指南。 
  
有关设计和部署 Active Directory 环境的完整指南, 请http://TechNet.microsoft.com参阅。 
  
此参考体系结构包括两个配置为域控制器的虚拟机。每个虚拟机配置如下：  
  
- 大小 — 小。  
    
- 操作系统 — Windows Server 2012。   
    
- 角色 — 指定 AD DS 域控制器为全局编录服务器。此配置可以减少通过 VPN 连接的出口通信量。在高变更速率的多域环境中，在内部部署中配置域控制器，使其不与 Azure 中的全局目录服务器同步。   
    
- 数据磁盘 — 将 AD DS 数据库、日志和 SYSVOL 放在 Azure 数据磁盘上。不要将它们放在操作系统磁盘或 Azure 提供的临时磁盘上。这一点很关键。 
    
- 角色 — 在域控制器上安装和配置 Windows DNS。 
    
- IP 地址 — 使用动态 IP 地址。这要求您创建一个 Azure 虚拟网络。  
    

