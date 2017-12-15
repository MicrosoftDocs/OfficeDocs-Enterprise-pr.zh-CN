---
title: "在 Microsoft Azure 中部署 Office 365 目录同步 (DirSync)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: "摘要： 在 Azure 同步您的内部目录和 Office 365 订购的 Azure AD 租户之间的帐户中的虚拟机上部署 Azure AD 连接 （目录同步）。"
ms.openlocfilehash: c6ee337c49092ac5d2b3d30a54fc33b3f3e2bb58
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure"></a><span data-ttu-id="139ac-103">在 Microsoft Azure 中部署 Office 365 目录同步 (DirSync)</span><span class="sxs-lookup"><span data-stu-id="139ac-103">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>

 <span data-ttu-id="139ac-104">**摘要：**在 Azure 同步您的内部目录和 Office 365 订购的 Azure AD 租户之间的帐户中的虚拟机上部署 Azure AD 连接 （目录同步）。</span><span class="sxs-lookup"><span data-stu-id="139ac-104">**Summary:** Deploy Azure AD Connect (DirSync) on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="139ac-p101">Azure 的活动目录 (AD) 连接 （以前称为目录同步工具、 目录同步工具或 DirSync.exe 工具） 是基于服务器的应用程序，它在加入域的服务器上安装同步您的本地 Windows 服务器活动目录用户定向到 Office 365 订购的 Azure Active Directory 租户。您可以在本地服务器上，安装 Azure AD 连接但您也可以安装它在 Azure 中的虚拟机上，原因如下：</span><span class="sxs-lookup"><span data-stu-id="139ac-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for the following reasons:</span></span>
  
- <span data-ttu-id="139ac-107">您可以更快地设置和配置基于云的服务器，使服务更快地提供给用户使用。</span><span class="sxs-lookup"><span data-stu-id="139ac-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="139ac-108">Azure 提供更好的网站可用性，事半功倍。</span><span class="sxs-lookup"><span data-stu-id="139ac-108">Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="139ac-109">可以减少组织中内部部署服务器的数量。</span><span class="sxs-lookup"><span data-stu-id="139ac-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="139ac-p102">此解决方案要求您的内部网络和 Azure 虚拟网络之间的连接。有关详细信息，请参阅[连接到 Microsoft Azure 虚拟网络的内部网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="139ac-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="139ac-p103">本文介绍了单个域中采用单目录林同步。Azure AD 连接与 Office 365 同步活动目录林中的所有 Windows 服务器 AD 域。如果您有多个活动目录林与 Office 365 进行同步，请参阅[使用单点登录方案多林目录同步](https://go.microsoft.com/fwlink/p/?LinkId=393091)。</span><span class="sxs-lookup"><span data-stu-id="139ac-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="139ac-p104">Office 365 的目录服务使用 Azure 活动目录 (AD Azure)。Office 365 订阅包括 Azure AD 租户。此租户还可以用于对您的组织的标识，与其他云的工作负载，在 Azure 中包括其他 SaaS 应用程序和应用程序的管理。</span><span class="sxs-lookup"><span data-stu-id="139ac-p104">Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="139ac-118">在 Azure 中部署 Office 365 目录同步的概述</span><span class="sxs-lookup"><span data-stu-id="139ac-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>
<span data-ttu-id="139ac-119"><a name="Overview"> </a></span><span class="sxs-lookup"><span data-stu-id="139ac-119"></span></span>

<span data-ttu-id="139ac-120">下图显示了 Azure AD 连接在同步到 anOffice 365 订阅内部 Windows 服务器 AD 林中的 Azure (DirSync server) 中的虚拟机上运行。</span><span class="sxs-lookup"><span data-stu-id="139ac-120">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the DirSync server) that synchronizes an on-premises Windows Server AD forest to anOffice 365 subscription.</span></span>
  
![Azure 中的虚拟机上的 Azure AD Connect 工具使用流量流将本地帐户同步到 Office 365 订阅的 Azure AD 租户](images/CP_DirSyncOverview.png)
  
<span data-ttu-id="139ac-p105">在图中，有两个网络连接的站点到站点 VPN 或 ExpressRoute 连接。没有，Windows 服务器 AD 域控制器位于和没有与目录同步服务器，这是虚拟机 Azure 虚拟网络内部网络运行[Azure AD 连接](https://www.microsoft.com/download/details.aspx?id=47594)。有来自目录同步服务器的两个主要的通信流：</span><span class="sxs-lookup"><span data-stu-id="139ac-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a DirSync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the DirSync server:</span></span>
  
-  <span data-ttu-id="139ac-125">Azure AD Connect 查询本地网络上的域控制器以获取对帐户和密码的更改。</span><span class="sxs-lookup"><span data-stu-id="139ac-125">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="139ac-p106">Azure AD 连接发送帐户和密码的 Office 365 订阅的 Azure AD 实例所做的更改。由于目录同步服务器位于内部网络的扩展部分，都在通过内部网络的代理服务器发送这些更改。</span><span class="sxs-lookup"><span data-stu-id="139ac-p106">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the DirSync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="139ac-p107">此解决方案说明单个 Active Directory 域，在一个单一的活动目录林同步。Azure AD 连接与 Office 365 同步活动目录林中的所有 Active Directory 域。如果您有多个活动目录林与 Office 365 进行同步，请参阅[使用单点登录方案多林目录同步](https://go.microsoft.com/fwlink/p/?LinkId=393091)。</span><span class="sxs-lookup"><span data-stu-id="139ac-p107">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="139ac-p108">在这两种情况下，源自 Azure Azure 的虚拟机上运行的 AD 连接的通信转发到 Azure，然后转发通讯通过站点到站点 VPN 或 ExpressRoute 连接到 VPN 网关设备的虚拟网络上的网关内部网络中。内部网络的路由结构然后转发到其目的地，如域控制器或代理服务器的通信。</span><span class="sxs-lookup"><span data-stu-id="139ac-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="139ac-133">部署此解决方案时有两个主要步骤：</span><span class="sxs-lookup"><span data-stu-id="139ac-133">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="139ac-p109">创建了一个 Azure 的虚拟网络，并建立站点到站点 VPN 连接到内部网络。有关详细信息，请参阅[连接到 Microsoft Azure 虚拟网络的内部网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="139ac-p109">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="139ac-p110">在 Azure，加入域的虚拟机上安装[Azure AD 连接](https://www.microsoft.com/download/details.aspx?id=47594)，然后在同步内部 Windows 服务器 AD 到 Office 365。这包括：</span><span class="sxs-lookup"><span data-stu-id="139ac-p110">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="139ac-138">创建运行 Azure AD 连接 Azure 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="139ac-138">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="139ac-139">安装和配置[Azure AD 连接](https://www.microsoft.com/download/details.aspx?id=47594)。</span><span class="sxs-lookup"><span data-stu-id="139ac-139">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="139ac-p111">配置 Azure AD 连接需要 Azure AD 管理员帐户和 Windows 服务器 AD 企业管理员帐户的凭据 （用户名和密码）。Azure AD 连接运行立即并持续同步到 Office 365 的内部部署 Windows 服务器 AD 林。</span><span class="sxs-lookup"><span data-stu-id="139ac-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="139ac-142">在部署此解决方案在生产环境中的之前，按照[您 Office 365 的开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)中的说明设置此配置作为概念，用于演示，或实验验证。</span><span class="sxs-lookup"><span data-stu-id="139ac-142">Before you deploy this solution in production, use the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="139ac-143">Azure AD Connect 配置完成后，它不会保存 Windows Server AD 企业管理员帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="139ac-143">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="139ac-p112">此解决方案说明同步单个 Windows 服务器 AD 林到 Office 365。本文中介绍的拓扑表示方法只有一种实现这一解决方案。您的组织的拓扑可能会不同，根据您独特的网络要求和安全注意事项。</span><span class="sxs-lookup"><span data-stu-id="139ac-p112">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-dirsync-server-for-office-365-in-azure"></a><span data-ttu-id="139ac-147">规划将 Office 365 的 DirSync 服务器托管在 Azure 中</span><span class="sxs-lookup"><span data-stu-id="139ac-147">Plan for hosting a DirSync server for Office 365 in Azure</span></span>
<span data-ttu-id="139ac-148"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="139ac-148"></span></span>

### <a name="prerequisites"></a><span data-ttu-id="139ac-149">先决条件</span><span class="sxs-lookup"><span data-stu-id="139ac-149">Prerequisites</span></span>

<span data-ttu-id="139ac-150">开始操作之前，请查看此解决方案的以下先决条件。</span><span class="sxs-lookup"><span data-stu-id="139ac-150">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="139ac-151">查看[计划 Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)中的相关规划内容。</span><span class="sxs-lookup"><span data-stu-id="139ac-151">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span></span>
    
- <span data-ttu-id="139ac-152">请确保您满足所有[先决条件](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites)Azure 的虚拟网络的配置。</span><span class="sxs-lookup"><span data-stu-id="139ac-152">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="139ac-p113">有包括 Active Directory 集成功能的 Office 365 订阅。有关 Office 365 的订阅信息，请转到[Office 365 订阅页面](https://go.microsoft.com/fwlink/p/?LinkId=394278)。</span><span class="sxs-lookup"><span data-stu-id="139ac-p113">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span></span>
    
- <span data-ttu-id="139ac-155">设置运行 Azure AD 连接与 Office 365 同步内部 Windows 服务器 AD 林中的一个 Azure 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="139ac-155">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="139ac-156">必须具有企业管理员帐户的 Windows 服务器 AD 和 Azure 活动目录管理员帐户的凭据 （名称和密码）。</span><span class="sxs-lookup"><span data-stu-id="139ac-156">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="139ac-157">解决方案体系结构设计假设</span><span class="sxs-lookup"><span data-stu-id="139ac-157">Solution architecture design assumptions</span></span>

<span data-ttu-id="139ac-158">下面列出了此解决方案需做出的设计选择。</span><span class="sxs-lookup"><span data-stu-id="139ac-158">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="139ac-p114">本解决方案使用一个 Azure 虚拟网络的站点到站点 VPN 连接。在 Azure 的虚拟网络承载一个子网，其中包含一台服务器、 运行 Azure AD 连接的目录同步服务器。</span><span class="sxs-lookup"><span data-stu-id="139ac-p114">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that contains one server, the DirSync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="139ac-161">在内部部署网络中，域控制器和 DNS 服务器存在。</span><span class="sxs-lookup"><span data-stu-id="139ac-161">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="139ac-p115">Azure AD 连接执行而不是单一登录的密码同步。不需要部署 Active Directory 联合身份验证服务 (AD FS）) 的基础结构。若要了解有关密码同步和单一登录选项的详细信息，请参阅[确定要使用哪个目录集成方案](https://go.microsoft.com/fwlink/p/?LinkId=393094)。</span><span class="sxs-lookup"><span data-stu-id="139ac-p115">Azure AD Connect performs password synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password synchronization and single sign-on options, see [Determine which directory integration scenario to use](https://go.microsoft.com/fwlink/p/?LinkId=393094).</span></span>
    
<span data-ttu-id="139ac-p116">下面是您在环境中部署此解决方案时可能会考虑的一些其他设计选项：</span><span class="sxs-lookup"><span data-stu-id="139ac-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="139ac-167">如果存在现有的 Azure 虚拟网络中的 DNS 服务器，请确定是否要使用它们来进行名称解析，而不是在内部网络上的 DNS 服务器的目录同步服务器。</span><span class="sxs-lookup"><span data-stu-id="139ac-167">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your DirSync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="139ac-p117">如果现有 Azure 虚拟网络中的域控制器，请确定是否配置 Active Directory 站点和服务可能会为您更好的选择。目录同步服务器可以查询 Azure 中的帐户和密码，而不是在内部网络上的域控制器的更改虚拟网络中的域控制器。</span><span class="sxs-lookup"><span data-stu-id="139ac-p117">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The DirSync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="139ac-170">部署路线图</span><span class="sxs-lookup"><span data-stu-id="139ac-170">Deployment roadmap</span></span>
<span data-ttu-id="139ac-171"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="139ac-171"></span></span>

<span data-ttu-id="139ac-172">部署在 Azure 中的虚拟机上的 Azure AD 连接的三个阶段包括：</span><span class="sxs-lookup"><span data-stu-id="139ac-172">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="139ac-173">阶段 1：创建和配置 Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="139ac-173">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="139ac-174">阶段 2：创建和配置 Azure 虚拟机</span><span class="sxs-lookup"><span data-stu-id="139ac-174">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="139ac-175">阶段 3：安装和配置 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="139ac-175">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="139ac-176">部署之后，还必须为 Office 365 中的新用户帐户分配位置和许可证。</span><span class="sxs-lookup"><span data-stu-id="139ac-176">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="139ac-177">[在 Azure 部署工具包中的目录同步服务器](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)包含所有的 Azure PowerShell 块来构建此解决方案、 Microsoft PowerPoint 和 Visio 格式中的关系图和生成 Azure PowerShell 的 Microsoft Excel 配置工作簿为您的设置自定义的命令块。</span><span class="sxs-lookup"><span data-stu-id="139ac-177">The [DirSync Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="139ac-178">阶段 1：创建和配置 Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="139ac-178">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="139ac-179">若要创建和配置的 Azure 的虚拟网络，完成[阶段 1： 准备您的内部网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1)和[第 2 阶段： 在 Azure 创建跨部署虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2)中部署路线图的[连接到内部网络Microsoft Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="139ac-179">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="139ac-180">这是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="139ac-180">This is your resulting configuration.</span></span>
  
![托管于 Azure 中的 Office 365 的 DirSync 服务器阶段 1](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="139ac-182">该图显示了通过站点到站点 VPN 或 ExpressRoute 连接来连接到 Azure 虚拟网络的本地网络。</span><span class="sxs-lookup"><span data-stu-id="139ac-182">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="139ac-183">阶段 2：创建和配置 Azure 虚拟机</span><span class="sxs-lookup"><span data-stu-id="139ac-183">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="139ac-p118">在 Azure 使用的说明[创建第一个 Windows 虚拟机在 Azure 的门户网站中](https://go.microsoft.com/fwlink/p/?LinkId=393098)创建虚拟机。使用以下设置：</span><span class="sxs-lookup"><span data-stu-id="139ac-p118">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="139ac-p119">上**基本操作**窗格中，选择相同的订阅、 位置和资源组作为虚拟网络。在安全的位置，记录用户名称和密码。您将需要使用这些以后连接到虚拟机。</span><span class="sxs-lookup"><span data-stu-id="139ac-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="139ac-189">在**选择大小**窗格中，选择**A2 标准**大小。</span><span class="sxs-lookup"><span data-stu-id="139ac-189">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="139ac-p120">在**设置**窗格中，在**存储**部分中选择**标准**的存储类型。在**网络**部分中，选择虚拟网络和子网的名称所在的目录同步服务器 (不是 GatewaySubnet)。将所有其他设置保留为其默认值。</span><span class="sxs-lookup"><span data-stu-id="139ac-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the DirSync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="139ac-193">通过检查内部 DNS 验证 DirSync 服务器是否正确使用 DNS，以确保为具有 IP 地址的虚拟机添加地址 (A) 记录。</span><span class="sxs-lookup"><span data-stu-id="139ac-193">Verify that your DirSync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="139ac-p121">使用中的说明[连接到虚拟机并登录](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)到远程桌面连接的目录同步服务器连接。登录后，加入本地 Windows 服务器 AD 域虚拟机。</span><span class="sxs-lookup"><span data-stu-id="139ac-p121">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the DirSync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="139ac-p122">若要使用 Azure AD Connect 访问 Internet 资源，必须将 DirSync 服务器配置为使用本地网络的代理服务器。有关要执行的其他配置步骤，你应与网络管理员联系。</span><span class="sxs-lookup"><span data-stu-id="139ac-p122">For Azure AD Connect to gain access to Internet resources, you must configure the DirSync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="139ac-198">这是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="139ac-198">This is your resulting configuration.</span></span>
  
![托管于 Azure 中的 Office 365 的 DirSync 服务器阶段 2](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="139ac-200">该图显示跨界 Azure 虚拟网络中的 DirSync 服务器虚拟机。</span><span class="sxs-lookup"><span data-stu-id="139ac-200">This figure shows the DirSync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="139ac-201">阶段 3：安装和配置 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="139ac-201">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="139ac-202">请完成以下过程：</span><span class="sxs-lookup"><span data-stu-id="139ac-202">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="139ac-p123">连接到远程桌面连接使用具有本地管理员权限的 Windows 服务器 AD 域帐户目录同步服务器。请参阅[连接到虚拟机并登录](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)。</span><span class="sxs-lookup"><span data-stu-id="139ac-p123">Connect to the DirSync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="139ac-205">从目录同步服务器，打开[设置目录同步在 Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)的文章并按照指导目录同步密码同步。</span><span class="sxs-lookup"><span data-stu-id="139ac-205">From the DirSync server, open the [Set up directory synchronization in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) article and follow the directions for directory synchronization with password synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="139ac-p124">安装程序会在本地用户的组织单位 (OU) 创建的**AAD_xxxxxxxxxxxx**帐户。不要移动或删除该帐户或同步将失败。</span><span class="sxs-lookup"><span data-stu-id="139ac-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="139ac-208">这是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="139ac-208">This is your resulting configuration.</span></span>
  
![托管于 Azure 中的 Office 365 的 DirSync 服务器阶段 3](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="139ac-210">该图显示跨界 Azure 虚拟网络中具有 Azure AD Connect 的 DirSync 服务器。</span><span class="sxs-lookup"><span data-stu-id="139ac-210">This figure shows the DirSync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="139ac-211">将位置和许可证分配给 Office 365 中的用户</span><span class="sxs-lookup"><span data-stu-id="139ac-211">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="139ac-p125">Azure AD Connect 将帐户从本地 Windows Server AD 添加到 Office 365 订阅，但为了使用户能够登录到 Office 365 并使用它的服务，必须使用位置和许可证配置这些帐户。使用下列步骤为适当的用户帐户添加位置和激活许可证：</span><span class="sxs-lookup"><span data-stu-id="139ac-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="139ac-214">[Office 365 门户页面](https://portal.office.com)时，登录，然后单击**管理**。</span><span class="sxs-lookup"><span data-stu-id="139ac-214">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="139ac-215">在左边的导航，请单击**用户 > 活动用户**。</span><span class="sxs-lookup"><span data-stu-id="139ac-215">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="139ac-216">在用户帐户列表中，选中你想要激活的用户旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="139ac-216">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="139ac-217">在用户的页面上，单击**产品**许可证的**编辑**。</span><span class="sxs-lookup"><span data-stu-id="139ac-217">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="139ac-218">在**产品许可**页中，选择**位置**，用户的位置，然后启用适当许可的用户。</span><span class="sxs-lookup"><span data-stu-id="139ac-218">On the **Product licences** page, select a location for the user for **Location**, and then enable the appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="139ac-219">完成后，单击**保存**，然后单击**关闭**两次。</span><span class="sxs-lookup"><span data-stu-id="139ac-219">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="139ac-220">对于其他用户，请返回步骤 3。</span><span class="sxs-lookup"><span data-stu-id="139ac-220">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="139ac-221">See Also</span><span class="sxs-lookup"><span data-stu-id="139ac-221">See Also</span></span>

<span data-ttu-id="139ac-222"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="139ac-222"></span></span>

[<span data-ttu-id="139ac-223">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="139ac-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="139ac-224">将内部网络连接到 Microsoft Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="139ac-224">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="139ac-225">下载 Azure AD 连接</span><span class="sxs-lookup"><span data-stu-id="139ac-225">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="139ac-226">Office 365 中的目录同步设置</span><span class="sxs-lookup"><span data-stu-id="139ac-226">Set up directory synchronization in Office 365</span></span>](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[<span data-ttu-id="139ac-227">在 Azure 部署工具包中的目录同步服务器</span><span class="sxs-lookup"><span data-stu-id="139ac-227">DirSync Server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



