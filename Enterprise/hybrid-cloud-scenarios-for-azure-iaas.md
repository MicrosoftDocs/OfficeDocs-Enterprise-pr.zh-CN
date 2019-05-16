---
title: Azure IaaS 的混合云方案
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
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: '摘要: 了解 Microsoft 在 Azure 中基于服务 (IaaS) 的云产品的混合体系结构和方案。'
ms.openlocfilehash: 429af408ca3f21fe667b36cdb9767d3916a6b1a4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067348"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>适用于 Azure IaaS 的混合云方案

 **摘要:** 了解 Microsoft 在 Azure 中基于服务 (IaaS) 的云产品的混合体系结构和方案。
  
通过托管在跨内部 Azure 虚拟网络 (VNet) 中运行的 IT 工作负荷，将本地计算和标识基础结构扩展到云。  
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Azure IaaS 混合方案体系结构

图 1 显示了 Azure 中基于 Microsoft laaS 的混合方案的体系结构。
  
**图 1：Azure 中基于 Microsoft IaaS 的混合方案**

![Azure 中基于 Microsoft IaaS 的混合方案](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
针对体系结构的每一层：
  
- 应用和方案
    
    IT 工作负荷通常为多层的高可用性应用程序，由 Azure 虚拟机 (VM) 构成。
    
- 标识
    
    将标识服务器 (如 Active Directory 域服务 (AD DS) 域控制器) 添加到在 Azure Vnet 中运行以进行本地身份验证的服务器集。
    
- 网络
    
    使用通过 Internet 建立的站点到站点 VPN 连接，或使用通过到 Azure IaaS 的专用对等建立的 ExpressRoute 连接。
    
- 本地
    
    包含与在 Azure 中运行的标识服务器同步的标识服务器。此外还包含在 Azure 中运行的 VM 可访问的资源，如存储和系统管理基础结构。
    
## <a name="directory-synchronization-server-for-office-365"></a>Office 365 的目录同步服务器

从 Azure VNet 运行目录同步服务器 (如图2中所示), 是将您的计算和标识基础结构扩展到云的一个示例。
  
**图 2: Azure IaaS 中的 Office 365 的目录同步服务器**

![Azure IaaS 中的 Office 365 的目录同步服务器](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
在图2中, 本地网络承载 AD DS 基础结构, 并在其边缘使用代理服务器和路由器。 路由器通过站点到站点 VPN 或 ExpressRoute 连接与 Azure VNet 边缘的 Azure 网关连接。 在 VNet 中, 目录同步服务器运行 Azure AD Connect。
  
Office 365 的目录同步服务器将 AD DS 中的帐户列表与 Office 365 订阅的 Azure AD 租户同步。
  
目录同步服务器是一台运行 Azure AD Connect 的基于 Windows 的服务器。 为了加快资源调配或减少组织中的内部部署服务器数, 请在 Azure IaaS 中的虚拟网络 (VNet) 中部署目录同步服务器。
  
目录同步服务器轮询 AD DS 的更改, 然后将其与 Office 365 订阅进行同步。
  
有关详细信息, 请参阅[在 Microsoft Azure 中部署 Office 365 目录同步](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)。
  
## <a name="line-of-business-lob-application"></a>业务线 (LOB) 应用程序

图 3 显示了在 Azure IaaS 中运行的基于服务器的 LOB 应用程序的配置。
  
**图 3：Azure IaaS 中的 LOB 应用程序**

![Azure IaaS 中基于服务器的 LOB 应用程序](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
在图 3 中，本地网络托管标识基础结构和用户。它通过站点到站点 VPN 或 ExpressRoute 连接来连接到 Azure IaaS 网关。Azure IaaS 托管包含 LOB 应用程序服务器的虚拟网络。
  
可以创建在 Azure VM 上运行的 LOB 应用，它驻留在 Azure 数据中心的 Azure VNet 的子网（也称为位置）上。
  
因为实际上要将本地基础结构扩展到 Azure，则必须将唯一的专用地址空间分配给 VNet，并更新本地路由表，以确保对每个 VNet 的可访问性。
  
连接后，可通过远程桌面连接或使用系统管理软件对 VM 进行管理，就像对本地服务器进行管理一样。
  
通过配置公开的端口，移动或远程用户还可以从 Internet 对这些 VM 进行访问。
  
有关概念证明配置的信息，请参阅 [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md)。
  
以下为在 Azure VM 上托管的 LOB 应用的属性：
  
- 多层
    
    典型的 LOB 应用使用分层方法。服务器集提供标识、数据库处理、应用程序和逻辑处理以及前端 Web 服务器，以供员工或客户访问。  
    
- 高可用性
    
    典型的 LOB 应用通过在每一层中使用多个服务器来提供高可用性。Azure IaaS 为 Azure 可用集内的服务器提供高达 99.9% 的运行时间 SLA。  
    
- 负载分布
    
    若要在一个层的多个服务器之间分布网络流量负载，可以使用面向 Internet 的或内部的 Azure 负载均衡器。或者，可以使用 Azure 应用商店提供的专用负载均衡器应用程序。
    
- 安全性
    
    若要保护服务器避免接收来自 Internet 的未经请求的传入流量，可以使用 Azure 网络安全组。可以为单个虚拟机的子网或网络接口定义允许或拒绝的流量。
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Azure 中的 SharePoint Server 2016 场

Azure 中一个多层、高可用性 LOB 应用程序的示例是 SharePoint Server 2016 场，如图 4 中所示。
  
**图 4：Azure IaaS 中具有高可用性的 SharePoint Server 2016 场**

![Azure IaaS 中的高可用性 SharePoint Server 2016 场](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
在图 4 中，本地网络托管标识基础结构和用户。它通过站点到站点 VPN 或 ExpressRoute 连接来连接到 Azure IaaS 网关。Azure VNet 包含 SharePoint Server 2016 场的多个服务器，该场包括前端服务器的单独层、应用程序服务器，SQL Server 群集，以及域控制器。
  
此配置具有 Azure 中 LOB 应用程序的以下属性：  
  
- 层
    
    场中运行不同角色的服务器创建多个层，并且每一层都有其自己的子网。
    
- 高可用性
    
    通过在每一层中使用多个服务器，并将一层的所有服务器置于同一个可用性集中来实现高可用性。
    
- 负载分布
    
    内部 Azure 负载均衡器将传入客户端 Web 流量分布到前端服务器（WEB1 和 WEB2）以及分布到 SQL Server 群集（SQL1、SQL2 和 MN1）的侦听器 IP 地址。
    
- 安全性
    
    通过每个子网的网络安全组，可以配置允许的入站和出站流量。
    
按照此方法实现成功的应用：
  
1. 计算和试验
    
    请参阅[Microsoft azure 中的 Sharepoint server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) , 了解在 Azure 中运行 SharePoint server 2016 的好处。
    
    请参阅[在 Azure 开发/测试环境中使用 Intranet SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)构建模拟的开发/测试环境
    
2. 设计
    
    请参阅[在 azure 中设计 SharePoint Server 2016 场](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure)以逐步完成过程, 以确定承载服务器场及其设置的 Azure IaaS 网络、计算和存储元素的集合。
    
3. 部署
    
    请参阅在[Azure 中部署 SharePoint server 2016 WITH SQL Server AlwaysOn 可用性组](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in), 以通过五个阶段逐步完成高可用性服务器场的端到端配置。
    
## <a name="federated-identity-for-office-365-in-azure"></a>Azure 中适用于 Office 365 的联合身份

Azure 中的多层高可用性 LOB 应用程序的另一个示例是联合身份 (适用于 Office 365)。
  
**图 5: Azure IaaS 中适用于 Office 365 的高可用性联合身份基础结构**

![Azure 中的高可用性 Office 365 联合身份验证基础结构](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
在图5中, 本地网络承载标识基础结构和用户。 它通过站点到站点 VPN 或 ExpressRoute 连接来连接到 Azure IaaS 网关。 Azure VNet 包含 web 代理服务器、Active Directory 联合身份验证服务 (AD FS) 服务器和 Active Directory 域服务 (AD DS) 域控制器。
  
此配置具有 Azure 中 LOB 应用程序的以下属性： 
  
- **层:** Web 代理服务器、AD FS 服务器和 AD DS 域控制器都有层次。
    
- **负载分布:** 外部 Azure 负载平衡器将传入客户端身份验证请求分发到 web 代理, 并将内部 Azure 负载平衡器分发到 AD FS 服务器的身份验证请求。
    
按照此方法实现成功的应用：
  
1. 计算和试验
    
    请参阅[office 365 开发/测试环境的联合身份](federated-identity-for-your-office-365-dev-test-environment.md), 以生成用于 Office 365 的联合身份验证的模拟开发/测试环境。
    
2. 部署
    
    请参阅在[Azure 中部署适用于 Office 365 的高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md), 以通过五个阶段逐步完成高可用性 AD FS 基础结构的端到端配置。
    
    
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 混合云](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)


