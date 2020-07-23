---
title: 在 Microsoft Azure 中部署 Microsoft 365 目录同步
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 摘要：在 Azure 中的虚拟机上部署 Azure AD Connect，以在本地目录和 Microsoft 365 订阅的 Azure AD 租户之间同步帐户。
ms.openlocfilehash: bd1b973c60576002f110a909c0022b27f4595b81
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229968"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="e339e-103">在 Microsoft Azure 中部署 Microsoft 365 目录同步</span><span class="sxs-lookup"><span data-stu-id="e339e-103">Deploy Microsoft 365 Directory Synchronization in Microsoft Azure</span></span>

<span data-ttu-id="e339e-104">Azure Active Directory （Azure AD） Connect （以前称为目录同步工具、目录同步工具或 DirSync.exe 工具）是在加入域的服务器上安装的应用程序，用于将内部部署 Active Directory 域服务（AD DS）用户与 Microsoft 365 订阅的 Azure AD 租户同步。</span><span class="sxs-lookup"><span data-stu-id="e339e-104">Azure Active Directory (Azure AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is an application that you install on a domain-joined server to synchronize your on-premises Active Directory Domain Services (AD DS) users to the Azure AD tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="e339e-105">Microsoft 365 使用 Azure AD 获取其目录服务。</span><span class="sxs-lookup"><span data-stu-id="e339e-105">Microsoft 365 uses Azure AD for its directory service.</span></span> <span data-ttu-id="e339e-106">你的 Microsoft 365 订阅包括 Azure AD 租户。</span><span class="sxs-lookup"><span data-stu-id="e339e-106">Your Microsoft 365 subscription includes an Azure AD tenant.</span></span> <span data-ttu-id="e339e-107">此租户还可用于将组织的身份与其他云工作负载（包括 Azure 中的其他 SaaS 应用程序和应用程序）的管理进行管理。</span><span class="sxs-lookup"><span data-stu-id="e339e-107">This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span>

<span data-ttu-id="e339e-108">可以在本地服务器上安装 Azure AD Connect，但也可以将其安装在 Azure 中的虚拟机上，具体原因如下：</span><span class="sxs-lookup"><span data-stu-id="e339e-108">You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for these reasons:</span></span>
  
- <span data-ttu-id="e339e-109">可以更快地预配和配置基于云的服务器，使服务更快地提供给用户使用。</span><span class="sxs-lookup"><span data-stu-id="e339e-109">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
- <span data-ttu-id="e339e-110">Azure 可以更轻松地提供更好的网站可用性。</span><span class="sxs-lookup"><span data-stu-id="e339e-110">Azure offers better site availability with less effort.</span></span>
- <span data-ttu-id="e339e-111">可以减少组织中本地服务器的数量。</span><span class="sxs-lookup"><span data-stu-id="e339e-111">You can reduce the number of on-premises servers in your organization.</span></span>

<span data-ttu-id="e339e-p102">此解决方案要求在本地网络和 Azure 虚拟网络之间建立连接。有关详细信息，请参阅[将本地网络连接到 Microsoft Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="e339e-p102">This solution requires connectivity between your on-premises network and your Azure virtual network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="e339e-114">本文介绍了单个林中单个域的同步。</span><span class="sxs-lookup"><span data-stu-id="e339e-114">This article describes synchronization of a single domain in a single forest.</span></span> <span data-ttu-id="e339e-115">Azure AD Connect 将 Active Directory 林中的所有 AD DS 域与 Microsoft 365 同步。</span><span class="sxs-lookup"><span data-stu-id="e339e-115">Azure AD Connect synchronizes all AD DS domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="e339e-116">如果您有多个 Active Directory 林与 Microsoft 365 同步，请参阅[具有单一登录方案的多林目录同步](https://go.microsoft.com/fwlink/p/?LinkId=393091)。</span><span class="sxs-lookup"><span data-stu-id="e339e-116">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a><span data-ttu-id="e339e-117">在 Azure 中部署 Microsoft 365 目录同步的概述</span><span class="sxs-lookup"><span data-stu-id="e339e-117">Overview of deploying Microsoft 365 directory synchronization in Azure</span></span>

<span data-ttu-id="e339e-118">下图显示了在 Azure 中运行的 Azure AD Connect （目录同步服务器），该虚拟机将本地 AD DS 林同步到 Microsoft 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="e339e-118">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises AD DS forest to a Microsoft 365 subscription.</span></span>
  
![Azure 中的虚拟机上的 azure AD Connect 工具将本地帐户同步到 Microsoft 365 订阅的 Azure AD 租户以及流量流](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="e339e-p104">图中有两个通过站点间 VPN 或 ExpressRoute 连接进行连接的网络：一个是 AD DS 域控制器所在的本地网络，另外一个是带有目录同步服务器的 Azure 虚拟网络，目录同步服务器是一个运行 [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) 的虚拟机。有两个主要通信流源自目录同步服务器：</span><span class="sxs-lookup"><span data-stu-id="e339e-p104">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="e339e-123">Azure AD Connect 查询本地网络上的域控制器以获取对帐户和密码的更改。</span><span class="sxs-lookup"><span data-stu-id="e339e-123">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
-  <span data-ttu-id="e339e-124">Azure AD Connect 将对帐户和密码所做的更改发送到 Microsoft 365 订阅的 Azure AD 实例。</span><span class="sxs-lookup"><span data-stu-id="e339e-124">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Microsoft 365 subscription.</span></span> <span data-ttu-id="e339e-125">由于目录同步服务器位于本地网络的扩展部分，因此将通过内部部署网络的代理服务器发送这些更改。</span><span class="sxs-lookup"><span data-stu-id="e339e-125">Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="e339e-126">本解决方案说明单个 Active Directory 林中单个 Active Directory 域的同步。</span><span class="sxs-lookup"><span data-stu-id="e339e-126">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest.</span></span> <span data-ttu-id="e339e-127">Azure AD Connect 将 Active Directory 林中的所有 Active Directory 域与 Microsoft 365 同步。</span><span class="sxs-lookup"><span data-stu-id="e339e-127">Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="e339e-128">如果您有多个 Active Directory 林与 Microsoft 365 同步，请参阅[具有单一登录方案的多林目录同步](https://go.microsoft.com/fwlink/p/?LinkId=393091)。</span><span class="sxs-lookup"><span data-stu-id="e339e-128">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="e339e-129">部署此解决方案时有两个主要步骤：</span><span class="sxs-lookup"><span data-stu-id="e339e-129">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="e339e-p107">创建 Azure 虚拟网络和建立到本地网络的站点间 VPN 连接。有关详细信息，请参阅[将本地网络连接到 Microsoft Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="e339e-p107">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="e339e-132">在 Azure 中加入域的虚拟机上安装[AZURE AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) ，然后将本地 AD DS 同步到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="e339e-132">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises AD DS to Microsoft 365.</span></span> <span data-ttu-id="e339e-133">这包括：</span><span class="sxs-lookup"><span data-stu-id="e339e-133">This involves:</span></span>
    
    <span data-ttu-id="e339e-134">创建 Azure 虚拟机以运行 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="e339e-134">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="e339e-135">安装和配置 [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)。</span><span class="sxs-lookup"><span data-stu-id="e339e-135">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="e339e-136">配置 Azure AD Connect 需要 Azure AD 管理员帐户和 AD DS 企业管理员帐户的凭据（用户名和密码）。</span><span class="sxs-lookup"><span data-stu-id="e339e-136">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a AD DS enterprise administrator account.</span></span> <span data-ttu-id="e339e-137">Azure AD Connect 立即运行，并在持续的基础上将本地 AD DS 林同步到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="e339e-137">Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises AD DS forest to Microsoft 365.</span></span>
    
<span data-ttu-id="e339e-138">在生产中部署此解决方案之前，可以使用[模拟企业基准配置](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise)中的说明将此配置设置为概念证明、演示或试验。</span><span class="sxs-lookup"><span data-stu-id="e339e-138">Before you deploy this solution in production, you can use the instructions in [The simulated enterprise base configuration](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="e339e-139">Azure AD Connect 配置完成后，它不会保存 AD DS 企业管理员帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="e339e-139">When Azure AD Connect configuration completes, it does not save the AD DS enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="e339e-140">此解决方案介绍了如何将单个 AD DS 林同步到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="e339e-140">This solution describes synchronizing a single AD DS forest to Microsoft 365.</span></span> <span data-ttu-id="e339e-141">本文中讨论的拓扑只是表示实现此解决方案的一种方法。</span><span class="sxs-lookup"><span data-stu-id="e339e-141">The topology discussed in this article represents only one way to implement this solution.</span></span> <span data-ttu-id="e339e-142">您的组织的拓扑可能因您的独特网络要求和安全注意事项而异。</span><span class="sxs-lookup"><span data-stu-id="e339e-142">Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a><span data-ttu-id="e339e-143">在 Azure 中规划托管 Microsoft 365 的目录同步服务器</span><span class="sxs-lookup"><span data-stu-id="e339e-143">Plan for hosting a directory sync server for Microsoft 365 in Azure</span></span>
<span data-ttu-id="e339e-144"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="e339e-144"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="e339e-145">先决条件</span><span class="sxs-lookup"><span data-stu-id="e339e-145">Prerequisites</span></span>

<span data-ttu-id="e339e-146">开始操作之前，请查看此解决方案的以下先决条件。</span><span class="sxs-lookup"><span data-stu-id="e339e-146">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="e339e-147">查阅[规划你的 Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network)中有关规划的内容。</span><span class="sxs-lookup"><span data-stu-id="e339e-147">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="e339e-148">确保满足配置 Azure 虚拟网络的所有[先决条件](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="e339e-148">Ensure that you meet all [Prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="e339e-149">拥有包含 Active Directory 集成功能的 Microsoft 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="e339e-149">Have a Microsoft 365 subscription that includes the Active Directory integration feature.</span></span> <span data-ttu-id="e339e-150">有关 Microsoft 365 订阅的信息，请转到[microsoft 365 订阅页面](https://products.office.com/compare-all-microsoft-office-products?tab=2)。</span><span class="sxs-lookup"><span data-stu-id="e339e-150">For information about Microsoft 365 subscriptions, go to the [Microsoft 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="e339e-151">设置一个运行 Azure AD Connect 的 Azure 虚拟机以将本地 AD DS 林与 Microsoft 365 同步。</span><span class="sxs-lookup"><span data-stu-id="e339e-151">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises AD DS forest with Microsoft 365.</span></span>
    
    <span data-ttu-id="e339e-152">必须具有 AD DS 企业管理员帐户和 Azure AD 管理员帐户的凭据（名称和密码）。</span><span class="sxs-lookup"><span data-stu-id="e339e-152">You must have the credentials (names and passwords) for a AD DS enterprise administrator account and an Azure AD Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="e339e-153">解决方案体系结构设计假设</span><span class="sxs-lookup"><span data-stu-id="e339e-153">Solution architecture design assumptions</span></span>

<span data-ttu-id="e339e-154">下面列出了此解决方案需做出的设计选择。</span><span class="sxs-lookup"><span data-stu-id="e339e-154">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="e339e-p112">此解决方案使用具有站点间 VPN 连接的单个 Azure 虚拟网络。Azure 虚拟网络托管包含一个服务器（即运行 Azure AD Connect 的目录同步服务器）的单个子网。</span><span class="sxs-lookup"><span data-stu-id="e339e-p112">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="e339e-157">在本地网络中，存在域控制器和 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="e339e-157">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="e339e-p113">Azure AD Connect 执行密码哈希同步而不是单一登录。你无需部署 Active Directory 联合身份验证服务 (AD FS) 基础结构。要了解有关密码哈希同步和单一登录选项的详细信息，请参阅[为 Azure Active Directory 混合标识解决方案选择正确的身份验证方法](https://aka.ms/auth-options)。</span><span class="sxs-lookup"><span data-stu-id="e339e-p113">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](https://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="e339e-p114">下面是在环境中部署此解决方案时可能会考虑的一些其他设计选项：</span><span class="sxs-lookup"><span data-stu-id="e339e-p114">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="e339e-163">如果现有的 Azure 虚拟网络中已有 DNS 服务器，请确定是否希望目录同步服务器取代本地网络的 DNS 服务器将其用于名称解析。</span><span class="sxs-lookup"><span data-stu-id="e339e-163">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="e339e-p115">如果现有的 Azure 虚拟网络中存在域控制器，请确定配置 Active Directory 站点和服务是否为更好的选择。目录同步服务器可以用 Azure 虚拟网络中的域控制器查询帐户和密码的更改，而不是使用本地网络上的域控制器。</span><span class="sxs-lookup"><span data-stu-id="e339e-p115">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="e339e-166">部署路线图</span><span class="sxs-lookup"><span data-stu-id="e339e-166">Deployment roadmap</span></span>

<span data-ttu-id="e339e-167">在 Azure 的虚拟机上部署 Azure AD Connect 的过程包含三个阶段：</span><span class="sxs-lookup"><span data-stu-id="e339e-167">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="e339e-168">阶段 1：创建和配置 Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="e339e-168">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="e339e-169">阶段 2：创建和配置 Azure 虚拟机</span><span class="sxs-lookup"><span data-stu-id="e339e-169">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="e339e-170">阶段 3：安装和配置 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="e339e-170">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="e339e-171">部署后，还必须为 Microsoft 365 中的新用户帐户分配位置和许可证。</span><span class="sxs-lookup"><span data-stu-id="e339e-171">After deployment, you must also assign locations and licenses for the new user accounts in Microsoft 365.</span></span>


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="e339e-172">第 1 阶段：创建和配置 Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="e339e-172">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="e339e-173">要创建和配置 Azure 虚拟网络，请完成[将本地网络连接到 Microsoft Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)部署路线图中的[阶段 1：准备你的本地网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network)和[阶段 2：在 Azure 中创建跨界虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure)。</span><span class="sxs-lookup"><span data-stu-id="e339e-173">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="e339e-174">这是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="e339e-174">This is your resulting configuration.</span></span>
  
![Azure 中托管的 Microsoft 365 的目录同步服务器的第1阶段](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="e339e-176">该图显示了通过站点间 VPN 或 ExpressRoute 连接来连接到 Azure 虚拟网络的本地网络。</span><span class="sxs-lookup"><span data-stu-id="e339e-176">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="e339e-177">阶段 2：创建和配置 Azure 虚拟机</span><span class="sxs-lookup"><span data-stu-id="e339e-177">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="e339e-p116">按照[在 Azure 门户中创建第一个 Windows 虚拟机](https://go.microsoft.com/fwlink/p/?LinkId=393098)中的说明在 Azure 中创建虚拟机。使用以下设置：</span><span class="sxs-lookup"><span data-stu-id="e339e-p116">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="e339e-p117">在“**基本信息**”窗格中，选择与虚拟网络相同的订阅、位置和资源组。在安全的位置记录用户名和密码。你稍后将需要使用这些以连接到虚拟机。</span><span class="sxs-lookup"><span data-stu-id="e339e-p117">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="e339e-183">在“选择大小”\*\*\*\* 窗格中，请选择“A2 标准”\*\*\*\* 大小。</span><span class="sxs-lookup"><span data-stu-id="e339e-183">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="e339e-p118">在“设置”\*\*\*\* 窗格的“存储”\*\*\*\* 部分中，选择“标准”\*\*\*\* 存储类型。在“网络”\*\*\*\* 部分中，选择虚拟网络的名称和托管目录同步服务器（不是 GatewaySubnet）的子网。其他所有设置都保留默认值。</span><span class="sxs-lookup"><span data-stu-id="e339e-p118">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="e339e-187">通过检查内部 DNS 验证目录同步服务器是否正确使用 DNS，以确保为具有其 IP 地址的虚拟机添加地址 (A) 记录。</span><span class="sxs-lookup"><span data-stu-id="e339e-187">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="e339e-p119">按照[连接到虚拟机并登录](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)中的说明，使用远程桌面连接来连接到目录同步服务器。登录后，将虚拟机加入到本地 AD DS 域。</span><span class="sxs-lookup"><span data-stu-id="e339e-p119">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises AD DS domain.</span></span>
  
<span data-ttu-id="e339e-p120">若要使用 Azure AD Connect 访问 Internet 资源，必须将目录同步服务器配置为使用本地网络的代理服务器。有关要执行的其他配置步骤，应与网络管理员联系。</span><span class="sxs-lookup"><span data-stu-id="e339e-p120">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="e339e-192">这是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="e339e-192">This is your resulting configuration.</span></span>
  
![Azure 中托管的 Microsoft 365 的目录同步服务器的第2阶段](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="e339e-194">该图显示跨界 Azure 虚拟网络中的目录同步服务器虚拟机。</span><span class="sxs-lookup"><span data-stu-id="e339e-194">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="e339e-195">阶段 3：安装和配置 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="e339e-195">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="e339e-196">请完成以下过程：</span><span class="sxs-lookup"><span data-stu-id="e339e-196">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="e339e-p121">通过远程桌面连接，使用具有本地管理员特权的 AD DS 域帐户连接到目录同步服务器。请参阅[连接到虚拟机并登录](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)。</span><span class="sxs-lookup"><span data-stu-id="e339e-p121">Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon).</span></span>
    
2. <span data-ttu-id="e339e-199">在目录同步服务器中，打开 "[为 Microsoft 365 文章设置目录同步](set-up-directory-synchronization.md)"，并按照有关使用密码哈希同步进行目录同步的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e339e-199">From the directory sync server, open the [Set up directory synchronization for Microsoft 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="e339e-p122">安装程序将在本地用户组织单位 (OU) 中创建 **AAD_xxxxxxxxxxxx** 帐户。请勿移动或删除该帐户，否则同步将失败。</span><span class="sxs-lookup"><span data-stu-id="e339e-p122">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="e339e-202">这是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="e339e-202">This is your resulting configuration.</span></span>
  
![Azure 中托管的 Microsoft 365 的目录同步服务器的第3阶段](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="e339e-204">该图显示跨界 Azure 虚拟网络中具有 Azure AD Connect 的目录同步服务器。</span><span class="sxs-lookup"><span data-stu-id="e339e-204">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a><span data-ttu-id="e339e-205">将位置和许可证分配给 Microsoft 365 中的用户</span><span class="sxs-lookup"><span data-stu-id="e339e-205">Assign locations and licenses to users in Microsoft 365</span></span>

<span data-ttu-id="e339e-206">Azure AD Connect 从本地 AD DS 向 Microsoft 365 订阅添加帐户，但为了使用户能够登录到 Microsoft 365 并使用其服务，必须使用位置和许可证配置帐户。</span><span class="sxs-lookup"><span data-stu-id="e339e-206">Azure AD Connect adds accounts to your Microsoft 365 subscription from the on-premises AD DS, but in order for users to sign in to Microsoft 365 and use its services, the accounts must be configured with a location and licenses.</span></span> <span data-ttu-id="e339e-207">使用下列步骤为适当的用户帐户添加位置和激活许可证：</span><span class="sxs-lookup"><span data-stu-id="e339e-207">Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="e339e-208">登录到[Microsoft 365 管理中心](https://admin.microsoft.com)，然后单击 "**管理**"。</span><span class="sxs-lookup"><span data-stu-id="e339e-208">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="e339e-209">在左侧导航栏中，单击“用户”>“活动用户”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e339e-209">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="e339e-210">在用户帐户列表中，选中你想要激活的用户旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="e339e-210">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="e339e-211">在用户页面上，单击“产品许可证”\*\*\*\* 的“编辑”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e339e-211">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="e339e-212">在“产品许可证”\*\*\*\* 页上，为“位置”\*\*\*\* 选择一个用户位置，然后为用户启用合适的许可证。</span><span class="sxs-lookup"><span data-stu-id="e339e-212">On the **Product licenses** page, select a location for the user for **Location**, and then enable the appropriate licenses for the user.</span></span>
    
6. <span data-ttu-id="e339e-213">完成后，单击“保存”\*\*\*\*，然后单击“关闭”\*\*\*\* 两次。</span><span class="sxs-lookup"><span data-stu-id="e339e-213">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="e339e-214">对于其他用户，请返回步骤 3。</span><span class="sxs-lookup"><span data-stu-id="e339e-214">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e339e-215">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e339e-215">See also</span></span>

[<span data-ttu-id="e339e-216">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="e339e-216">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)
  
[<span data-ttu-id="e339e-217">将本地网络连接到 Microsoft Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="e339e-217">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="e339e-218">下载 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="e339e-218">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="e339e-219">为 Microsoft 365 设置目录同步</span><span class="sxs-lookup"><span data-stu-id="e339e-219">Set up directory synchronization for Microsoft 365</span></span>](set-up-directory-synchronization.md)
  
