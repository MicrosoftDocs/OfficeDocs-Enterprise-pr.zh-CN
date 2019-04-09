---
title: 在 Azure 中部署 Office 365 的高可用性联合身份验证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 摘要：在 Microsoft Azure 中为 Office 365 订阅配置高可用性联合身份验证。
ms.openlocfilehash: 9e671cabf2e9ca764f4948822da6aa0fb57ef5b5
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038046"
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a>在 Azure 中部署 Office 365 的高可用性联合身份验证

 **摘要：** 在 Microsoft Azure 中为 Office 365 订阅配置高可用性联合身份验证。
  
这篇文章包含指向特定内容的链接，即通过这些虚拟机在 Azure 基础结构服务中为 Microsoft Office 365 部署高可用性联合身份验证的分步说明：
  
- 两个 Web 应用程序代理服务器
    
- 两个 Active Directory 联合身份验证服务 (AD FS) 服务器
    
- 两个副本域控制器
    
- 一个运行 Azure AD Connect 的目录同步 (DirSync) 服务器
    
下面是包含每个服务器的占位符名称的配置。
  
**Azure 中 Office 365 基础结构的高可用性联合身份验证**

![Azure 中高可用性 Office 365 联合身份验证基础结构的最终配置](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
所有虚拟机都位于一个跨界 Azure 虚拟网络 (VNet) 中。 
  
> [!NOTE]
> 各个用户的联合身份验证不依赖任何本地资源。不过，如果跨界连接变得不可用，VNet 中的域控制器将无法接收本地 Active Directory 域服务 (AD DS) 中执行的用户帐户和组更新。若要确保此问题不会发生，可以为跨界连接配置高可用性设置。有关详细信息，请参阅[高可用性跨界连接与 VNet 到 VNet 连接](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
用于特定角色的每对虚拟机都位于自己的子网和可用性集中。
  
> [!NOTE]
> 由于此 VNet 连接到本地网络，所以此配置不包括管理子网上的跳转框或监视虚拟机。有关详细信息，请参阅 [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm)（运行用于 N 层体系结构的 Windows VM）。 
  
此配置的结果是，将对所有 Office 365 用户使用联合身份验证，即可以使用自己的 Windows Server Active Directory 凭据（而不是 Office 365 帐户）进行登录。联合身份验证基础结构使用冗余的一组服务器，它们更易于在 Azure 基础结构服务（而非本地边缘网络）中进行部署。
  
## <a name="bill-of-materials"></a>物料清单

此基线配置需要以下 Azure 服务和组件集：
  
- 七个虚拟机
    
- 一个具有四个子网的跨界虚拟网络
    
- 四个资源组
    
- 三个可用性集
    
- 一个 Azure 订阅
    
这里是针对此配置的虚拟机及其默认大小。
  
|**项**|**虚拟机说明**|**Azure 库图像**|**默认大小**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |第一个域控制器  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |第二个域控制器  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Azure AD Connect 服务器  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |第一个 AD FS 服务器  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |第二个 AD FS 服务器  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |第一个 Web 应用程序代理服务器  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |第二个 Web 应用程序代理服务器  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
若要计算此配置的估算成本，请参阅 [Azure 定价计算器](https://azure.microsoft.com/pricing/calculator/)
  
## <a name="phases-of-deployment"></a>部署阶段

在以下阶段部署此工作负载：
  
- [阶段 1：配置 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。创建资源组、存储帐户、可用性集和跨界虚拟网络。
    
- [阶段 2：配置域控制器](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。创建和配置副本 Active Directory 域服务 (AD DS) 域控制器和 DirSync 服务器。
    
- [阶段 3：配置 AD FS 服务器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)。创建和配置两个 AD FS 服务器。
    
- [阶段 4：配置 Web 应用程序代理](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。创建和配置两个 Web 应用程序代理服务器。
    
- [阶段 5：为 Office 365 配置联合身份验证](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)。为 Office 365 订阅配置联合身份验证。
    
这些文章提供了预定义的体系结构的规范分阶段指南，以便在 Azure 基础结构服务中为 Office 365 Azure 创建实用的高可用性联合身份验证。请注意下列事项：
  
- 如果你是有经验的 AD FS 实施者，则可以自由调整第 3 阶段和第 4 阶段的说明，构建最符合你需求的服务器集。
    
- 如果你已经拥有现有的 Azure 混合云部署以及现有的跨界虚拟网络，则可以随意调整或跳过第 1 阶段和第 2 阶段中的说明，并将 AD FS 和 Web 应用程序代理服务器置于相应的子网上。
    
若要构建开发/测试环境或此配置的概念证明，请参阅 [用于 Office 365 开发/测试环境的联合身份](federated-identity-for-your-office-365-dev-test-environment.md)。
  
## <a name="next-step"></a>后续步骤

使用 [高可用性联合身份验证阶段 1:配置 Azure](high-availability-federated-authentication-phase-1-configure-azure.md) 开始配置此工作负载。 
  
<!--
> [!TIP]
> For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
--> 

