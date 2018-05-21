---
title: 在 Microsoft Azure 中部署 Office 365 目录同步
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 摘要：在 Azure 虚拟机上部署 Azure AD Connect，以在本地目录和 Office 365 订阅的 Azure AD 租户之间同步帐户。
ms.openlocfilehash: c37fd1e31684590b0b564b3fed402b5c33c062a3
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2018
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="387a3-103">在 Microsoft Azure 中部署 Office 365 目录同步</span><span class="sxs-lookup"><span data-stu-id="387a3-103">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>

 <span data-ttu-id="387a3-104">**摘要：** 在 Azure 虚拟机上部署 Azure AD Connect，以在本地目录和 Office 365 订阅的 Azure AD 租户之间同步帐户。</span><span class="sxs-lookup"><span data-stu-id="387a3-104">**Summary:** Deploy Azure AD Connect (DirSync) on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="387a3-p101">Azure Active Directory (AD) Connect（旧称为“目录同步工具”或“DirSync.exe 工具”）是一款基于服务器的应用程序，可以将其安装在加入域的服务器上，以便将本地 Windows Server Active Directory 用户同步到 Office 365 订阅的 Azure Active Directory 租户。虽然可以在本地服务器上安装 Azure AD Connect，但也可以出于以下原因在 Azure 中的虚拟机上安装它：</span><span class="sxs-lookup"><span data-stu-id="387a3-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Windows_Azure for the following reasons:</span></span>
  
- <span data-ttu-id="387a3-107">可以更快地预配和配置基于云的服务器，使服务更快地提供给用户使用。</span><span class="sxs-lookup"><span data-stu-id="387a3-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="387a3-108">Azure 可以更轻松地提供更好的网站可用性。</span><span class="sxs-lookup"><span data-stu-id="387a3-108">Windows_Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="387a3-109">可以减少组织中本地服务器的数量。</span><span class="sxs-lookup"><span data-stu-id="387a3-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="387a3-p102">此解决方案要求在本地网络和 Azure 虚拟网络之间建立连接。有关详细信息，请参阅[将本地网络连接到 Microsoft Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="387a3-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="387a3-p103">本文介绍了单个林中单个域的同步。Azure AD Connect 将 Active Directory 林中的所有 Windows Server AD 域与 Office 365 同步。如果你有多个 Active Directory 林要与 Office 365 同步，请参阅[使用单一登录的多林目录同步方案](https://go.microsoft.com/fwlink/p/?LinkId=393091)。</span><span class="sxs-lookup"><span data-stu-id="387a3-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Union_Lite_2nd, see  Multi-forest Directory Sync with Single Sign-On Scenario https://go.microsoft.com/fwlink/p/?LinkId=393091 .</span></span> 
  
> [!NOTE]
> <span data-ttu-id="387a3-p104">Office 365 对其目录服务使用 Azure Active Directory (Azure AD)。你的 Office 365 订阅包括 Azure AD 租户。该租户还可与其他云工作负载（其中包括其他 SaaS 应用程序和 Azure 中的应用）一起用于管理你的组织标识。</span><span class="sxs-lookup"><span data-stu-id="387a3-p104">Union_Lite_2nd uses WindowsAzureActiveDirectory (WindowsAzureAD_2nd)  for its directory service. Your Office 365 subscription includes an WindowsAzureAD_2nd tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Windows_Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="387a3-118">在 Azure 中部署 Office 365 目录同步的概述</span><span class="sxs-lookup"><span data-stu-id="387a3-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>
<span data-ttu-id="387a3-119"><a name="Overview"> </a></span><span class="sxs-lookup"><span data-stu-id="387a3-119"></span></span>

<span data-ttu-id="387a3-120">下图显示了在将本地 Windows Server AD 林同步到 Office 365 订阅的 Azure（目录同步服务器）中，在虚拟机上运行的 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="387a3-120">The following diagram shows Azure AD Connect running on a virtual machine in Windows_Azure (the DirSync server) that synchronizes and on-premises Windows Server AD forest to anUnion_Lite_2nd subscription.</span></span>
  
![Azure 中的虚拟机上的 Azure AD Connect 工具使用流量流将本地帐户同步到 Office 365 订阅的 Azure AD 租户](images/CP_DirSyncOverview.png)
  
<span data-ttu-id="387a3-p105">图中有两个通过站点间 VPN 或 ExpressRoute 连接进行连接的网络：一个是 Windows Server AD 域控制器所在的本地网络，另外一个是带有目录同步服务器的 Azure 虚拟网络，目录同步服务器是一个运行 [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) 的虚拟机。有两个主要通信流源自目录同步服务器：</span><span class="sxs-lookup"><span data-stu-id="387a3-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Windows_Azure virtual network with a DirSync server, a virtual machine running  Azure AD Connect https://www.microsoft.com/download/details.aspx?id=47594 . There are two main traffic flows originating from the DirSync server:</span></span>
  
-  <span data-ttu-id="387a3-125">Azure AD Connect 查询本地网络上的域控制器以获取对帐户和密码的更改。</span><span class="sxs-lookup"><span data-stu-id="387a3-125">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="387a3-p106">Azure AD Connect 将帐户和密码的更改发送到 Office 365 订阅的 Azure AD 实例。因为目录同步服务器处于你的本地网络中的扩展部分，这些更改会通过本地网络的代理服务器进行发送。</span><span class="sxs-lookup"><span data-stu-id="387a3-p106">Azure AD Connect sends the changes to accounts and passwords to the WindowsAzureAD_2nd instance of your Union_Lite_2nd subscription. Because the DirSync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network’s proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="387a3-p107">本解决方案描述单个 Active Directory 林中单个 Active Directory 域的同步。Azure AD Connect 将 Active Directory 林中的所有 Active Directory 域与 Office 365 同步。如果你有多个 Active Directory 林要与 Office 365 同步，请参阅[使用单一登录的多林目录同步方案](https://go.microsoft.com/fwlink/p/?LinkId=393091)。</span><span class="sxs-lookup"><span data-stu-id="387a3-p107">This article describes synchronization of a single domain in a single forest. The Azure AD Connect tool synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Union_Lite_2nd, see  Multi-forest Directory Sync with Single Sign-On Scenario http://go.microsoft.com/fwlink/p/?LinkId=393091 .</span></span> 
  
<span data-ttu-id="387a3-p108">在这两种情况下，在 Azure 虚拟机上运行的 Azure AD Connect 发出的流量会被转发到 Azure 中虚拟网络上的网关，然后再跨站点间 VPN 或 ExpressRoute 连接将流量转发到本地网络上的 VPN 网关设备。本地网络的路由基础结构接着会将流量转发到其目标，例如域控制器或代理服务器。</span><span class="sxs-lookup"><span data-stu-id="387a3-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Windows_Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="387a3-133">部署此解决方案时有两个主要步骤：</span><span class="sxs-lookup"><span data-stu-id="387a3-133">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="387a3-p109">创建 Azure 虚拟网络和建立到本地网络的站点间 VPN 连接。有关详细信息，请参阅[将本地网络连接到 Microsoft Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="387a3-p109">Create an Windows_Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see Connect an on-premises network to a Microsoft Azure Virtual Network.</span></span>
    
2. <span data-ttu-id="387a3-p110">在 Azure 中加入域的虚拟机上安装 [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)，然后将本地 Windows Server AD 同步到 Office 365。这包括：</span><span class="sxs-lookup"><span data-stu-id="387a3-p110">Install  Azure AD Connect https://www.microsoft.com/download/details.aspx?id=47594  on a domain-joined virtual machine in Windows_Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="387a3-138">创建 Azure 虚拟机以运行 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="387a3-138">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="387a3-139">安装和配置 [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)。</span><span class="sxs-lookup"><span data-stu-id="387a3-139">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="387a3-p111">要配置 Azure AD Connect，必须提供 Azure AD 管理员帐户和 Windows Server AD 企业管理员帐户的凭据（用户名和密码）。Azure AD Connect 会立即运行并且会不间断地将本地 Windows Server AD 林同步到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="387a3-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an WindowsAzureAD_2nd administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Union_Lite_2nd.</span></span>
    
<span data-ttu-id="387a3-142">在生产中部署此解决方案之前，使用 [针对 Office 365 开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)中的说明，将此配置设置为用于演示或实验的概念证明。</span><span class="sxs-lookup"><span data-stu-id="387a3-142">Before you deploy this solution in production, use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="387a3-143">Azure AD Connect 配置完成后，它不会保存 Windows Server AD 企业管理员帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="387a3-143">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="387a3-p112">此解决方案描述如何将单个 Windows Server AD 林同步到 Office 365。本文所讨论的拓扑只是表示实现此解决方案的一种方法。根据你的特殊网络要求和安全考虑事项，组织的拓扑可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="387a3-p112">This solution describes synchronizing a single Active Directory forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization’s topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="387a3-147">规划将 Office 365 的目录同步服务器托管在 Azure 中</span><span class="sxs-lookup"><span data-stu-id="387a3-147">Plan for hosting a DirSync server for Office 365 in Azure</span></span>
<span data-ttu-id="387a3-148"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="387a3-148"></span></span>

### <a name="prerequisites"></a><span data-ttu-id="387a3-149">先决条件</span><span class="sxs-lookup"><span data-stu-id="387a3-149">Prerequisites</span></span>

<span data-ttu-id="387a3-150">开始操作之前，请查看此解决方案的以下先决条件。</span><span class="sxs-lookup"><span data-stu-id="387a3-150">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="387a3-151">查阅[规划 Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)中有关规划的内容。</span><span class="sxs-lookup"><span data-stu-id="387a3-151">Review the related planning content in [Plan your Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span></span>
    
- <span data-ttu-id="387a3-152">确保满足配置 Azure 虚拟网络的所有[先决条件](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="387a3-152">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="387a3-p113">具有包含 Active Directory 集成功能的 Office 365 订阅。有关 Office 365 订阅的信息，请转到 [Office 365 订阅页面](https://go.microsoft.com/fwlink/p/?LinkId=394278)。</span><span class="sxs-lookup"><span data-stu-id="387a3-p113">Have an Union_Lite_2nd subscription that includes the Active Directory integration feature. For information about Union_Lite_2nd subscriptions, go to the  Office 365 subscription page https://go.microsoft.com/fwlink/p/?LinkId=394278 .</span></span>
    
- <span data-ttu-id="387a3-155">预配一个运行 Azure AD Connect 的 Azure 虚拟机，以便将本地 Windows Server AD 林与 Office 365 同步。</span><span class="sxs-lookup"><span data-stu-id="387a3-155">Provision one WindowsAzureVirtualMachine_1st that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Union_Lite_2nd.</span></span>
    
    <span data-ttu-id="387a3-156">必须具有 Windows Server AD 企业管理员帐户和 Azure Active Directory 管理员帐户的凭据（名称和密码）。</span><span class="sxs-lookup"><span data-stu-id="387a3-156">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Windows_Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="387a3-157">解决方案体系结构设计假设</span><span class="sxs-lookup"><span data-stu-id="387a3-157">Solution architecture design assumptions</span></span>

<span data-ttu-id="387a3-158">下面列出了此解决方案需做出的设计选择。</span><span class="sxs-lookup"><span data-stu-id="387a3-158">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="387a3-p114">此解决方案使用具有站点间 VPN 连接的单个 Azure 虚拟网络。Azure 虚拟网络托管包含一个服务器（即运行 Azure AD Connect 的目录同步服务器）的单个子网。</span><span class="sxs-lookup"><span data-stu-id="387a3-p114">This solution uses a single Windows_Azure virtual network with a site-to-site VPN connection. The Windows_Azure virtual network hosts a single subnet that contains one server, the DirSync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="387a3-161">在本地网络中，存在域控制器和 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="387a3-161">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="387a3-p115">Azure AD Connect 执行密码哈希同步而不是单一登录。你无需部署 Active Directory 联合身份验证服务 (AD FS) 基础结构。要了解有关密码哈希同步和单一登录选项的详细信息，请参阅[为 Azure Active Directory 混合标识解决方案选择正确的身份验证方法](http://aka.ms/auth-options)。</span><span class="sxs-lookup"><span data-stu-id="387a3-p115">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](http://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="387a3-p116">下面是在环境中部署此解决方案时可能会考虑的一些其他设计选项：</span><span class="sxs-lookup"><span data-stu-id="387a3-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="387a3-167">如果现有的 Azure 虚拟网络中已有 DNS 服务器，请确定是否希望目录同步服务器取代本地网络的 DNS 服务器将其用于名称解析。</span><span class="sxs-lookup"><span data-stu-id="387a3-167">If there are existing DNS servers in an existing Windows_Azure virtual network, determine whether you want your DirSync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="387a3-p117">如果现有的 Azure 虚拟网络中存在域控制器，请确定配置 Active Directory 站点和服务是否为更好的选择。目录同步服务器可以用 Azure 虚拟网络中的域控制器查询帐户和密码的更改，而不是使用本地网络上的域控制器。</span><span class="sxs-lookup"><span data-stu-id="387a3-p117">If there are domain controllers in an existing Windows_Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory synchronization server can query the domain controllers in the Windows_Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="387a3-170">部署路线图</span><span class="sxs-lookup"><span data-stu-id="387a3-170">Deployment roadmap</span></span>
<span data-ttu-id="387a3-171"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="387a3-171"></span></span>

<span data-ttu-id="387a3-172">在 Azure 的虚拟机上部署 Azure AD Connect 包含三个阶段：</span><span class="sxs-lookup"><span data-stu-id="387a3-172">Deploying Azure AD Connect on a virtual machine in  Windows_Azure consists of three phases:</span></span>
  
- <span data-ttu-id="387a3-173">阶段 1：创建和配置 Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="387a3-173">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="387a3-174">阶段 2：创建和配置 Azure 虚拟机</span><span class="sxs-lookup"><span data-stu-id="387a3-174">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="387a3-175">阶段 3：安装和配置 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="387a3-175">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="387a3-176">部署之后，还必须为 Office 365 中的新用户帐户分配位置和许可证。</span><span class="sxs-lookup"><span data-stu-id="387a3-176">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="387a3-177">[Azure 部署工具包中的目录同步服务器](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)包含构建此解决方案所需的全部 Azure PowerShell 块、Microsoft PowerPoint 和 Visio 格式的关系图，以及生成专为你的设置自定义的 Azure PowerShell 命令块的 Microsoft Excel 配置工作簿。</span><span class="sxs-lookup"><span data-stu-id="387a3-177">The  DirSync Server in Azure Deployment Kit https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded  contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="387a3-178">阶段 1：创建和配置 Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="387a3-178">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="387a3-179">要创建和配置 Azure 虚拟网络，请完成[将本地网络连接到 Microsoft Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)部署路线图中的[阶段 1：准备你的本地网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1)和[阶段 2：在 Azure 中创建跨界虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2)。</span><span class="sxs-lookup"><span data-stu-id="387a3-179">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="387a3-180">这是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="387a3-180">This is your resulting configuration.</span></span>
  
![托管于 Azure 中的 Office 365 的目录同步服务器阶段 1](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="387a3-182">该图显示了通过站点间 VPN 或 ExpressRoute 连接来连接到 Azure 虚拟网络的本地网络。</span><span class="sxs-lookup"><span data-stu-id="387a3-182">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="387a3-183">阶段 2：创建和配置 Azure 虚拟机</span><span class="sxs-lookup"><span data-stu-id="387a3-183">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="387a3-p118">按照[在 Azure 门户中创建第一个 Windows 虚拟机](https://go.microsoft.com/fwlink/p/?LinkId=393098)中的说明在 Azure 中创建虚拟机。使用以下设置：</span><span class="sxs-lookup"><span data-stu-id="387a3-p118">Create the virtual machine in Windows_Azure using the instructions  Create your first Windows virtual machine in the Azure portal https://go.microsoft.com/fwlink/p/?LinkId=393098 . Use the following settings:</span></span>
  
- <span data-ttu-id="387a3-p119">在“**基本信息**”窗格中，选择与虚拟网络相同的订阅、位置和资源组。在安全的位置记录用户名和密码。你稍后将需要使用这些以连接到虚拟机。</span><span class="sxs-lookup"><span data-stu-id="387a3-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="387a3-189">在“选择大小”**** 窗格中，请选择“A2 标准”**** 大小。</span><span class="sxs-lookup"><span data-stu-id="387a3-189">On the **Choose a size** pane, choose the **A2  Standard** size.</span></span>
    
- <span data-ttu-id="387a3-p120">在“设置”**** 窗格的“存储”**** 部分中，选择“标准”**** 存储类型。在“网络”**** 部分中，选择虚拟网络的名称和托管目录同步服务器（不是 GatewaySubnet）的子网。其他所有设置都保留默认值。</span><span class="sxs-lookup"><span data-stu-id="387a3-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type and the storage account set up with your virtual network. In the **Network** section, select the name of your virtual network and the subnet for hosting virtual machines (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="387a3-193">通过检查内部 DNS 验证目录同步服务器是否正确使用 DNS，以确保为具有其 IP 地址的虚拟机添加地址 (A) 记录。</span><span class="sxs-lookup"><span data-stu-id="387a3-193">Verify that your DirSync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="387a3-p121">按照[连接到虚拟机并登录](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)中的说明，使用远程桌面连接来连接到目录同步服务器。登录后，将虚拟机加入到本地 Windows Server AD 域。</span><span class="sxs-lookup"><span data-stu-id="387a3-p121">Use the instructions in [Connect to the virtual machine and sign onhttps://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the DirSync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="387a3-p122">若要使用 Azure AD Connect 访问 Internet 资源，必须将目录同步服务器配置为使用本地网络的代理服务器。有关要执行的其他配置步骤，应与网络管理员联系。</span><span class="sxs-lookup"><span data-stu-id="387a3-p122">For Azure AD Connect to gain access to Internet resources, you must configure the DirSync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="387a3-198">这是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="387a3-198">This is your resulting configuration.</span></span>
  
![托管于 Azure 中的 Office 365 的目录同步服务器阶段 2](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="387a3-200">该图显示跨界 Azure 虚拟网络中的目录同步服务器虚拟机。</span><span class="sxs-lookup"><span data-stu-id="387a3-200">This figure shows the DirSync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="387a3-201">阶段 3：安装和配置 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="387a3-201">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="387a3-202">请完成以下过程：</span><span class="sxs-lookup"><span data-stu-id="387a3-202">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="387a3-p123">通过远程桌面连接，使用具有本地管理员特权的 Windows Server AD 域帐户连接到目录同步服务器。请参阅[连接到虚拟机并登录](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)。</span><span class="sxs-lookup"><span data-stu-id="387a3-p123">Connect to the DirSync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign onhttps://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="387a3-205">从目录同步服务器，打开[在 Office 365 中设置目录同步](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)一文，并遵循使用密码哈希同步进行目录同步的说明。</span><span class="sxs-lookup"><span data-stu-id="387a3-205">From the DirSync server, open  the [Set up directory synchronization in Office 365https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) article and follow the directions for directory synchronization with password synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="387a3-p124">安装程序将在本地用户组织单位 (OU) 中创建 **AAD_xxxxxxxxxxxx** 帐户。请勿移动或删除该帐户，否则同步将失败。</span><span class="sxs-lookup"><span data-stu-id="387a3-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="387a3-208">这是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="387a3-208">This is your resulting configuration.</span></span>
  
![托管于 Azure 中的 Office 365 的目录同步服务器阶段 3](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="387a3-210">该图显示跨界 Azure 虚拟网络中具有 Azure AD Connect 的目录同步服务器。</span><span class="sxs-lookup"><span data-stu-id="387a3-210">This figure shows the DirSync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="387a3-211">将位置和许可证分配给 Office 365 中的用户</span><span class="sxs-lookup"><span data-stu-id="387a3-211">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="387a3-p125">Azure AD Connect 将帐户从本地 Windows Server AD 添加到 Office 365 订阅，但为了使用户能够登录到 Office 365 并使用它的服务，必须使用位置和许可证配置这些帐户。使用下列步骤为适当的用户帐户添加位置和激活许可证：</span><span class="sxs-lookup"><span data-stu-id="387a3-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="387a3-214">登录到 [Office 365 门户页](https://portal.office.com)，然后单击“管理员”****。</span><span class="sxs-lookup"><span data-stu-id="387a3-214">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="387a3-215">在左侧导航栏中，单击“用户”>“活动用户”****。</span><span class="sxs-lookup"><span data-stu-id="387a3-215">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="387a3-216">在用户帐户列表中，选中你想要激活的用户旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="387a3-216">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="387a3-217">在用户页面上，单击“产品许可证”**** 的“编辑”****。</span><span class="sxs-lookup"><span data-stu-id="387a3-217">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="387a3-218">在“产品许可证”**** 页面上，为用户选择“位置”****，然后为用户启用合适的许可证。</span><span class="sxs-lookup"><span data-stu-id="387a3-218">On the **Product licences** page, select a location for the user for **Location**, and then enable the  appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="387a3-219">完成后，单击“保存”****，然后单击“关闭”**** 两次。</span><span class="sxs-lookup"><span data-stu-id="387a3-219">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="387a3-220">对于其他用户，请返回步骤 3。</span><span class="sxs-lookup"><span data-stu-id="387a3-220">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="387a3-221">另请参阅</span><span class="sxs-lookup"><span data-stu-id="387a3-221">See Also</span></span>

<span data-ttu-id="387a3-222"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="387a3-222"></span></span>

[<span data-ttu-id="387a3-223">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="387a3-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="387a3-224">将本地网络连接到 Microsoft Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="387a3-224">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="387a3-225">下载 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="387a3-225">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="387a3-226">在 Office 365 中设置目录同步</span><span class="sxs-lookup"><span data-stu-id="387a3-226">Set up directory synchronization in Office 365</span></span>](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[<span data-ttu-id="387a3-227">Azure 部署工具包中的目录同步服务器</span><span class="sxs-lookup"><span data-stu-id="387a3-227">Directory Synchronization server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



