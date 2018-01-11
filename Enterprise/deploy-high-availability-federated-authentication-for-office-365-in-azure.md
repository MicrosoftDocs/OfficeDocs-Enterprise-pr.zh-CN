---
title: "在 Azure 中部署 Office 365 的高可用性联合身份验证"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: "摘要：在 Microsoft Azure 中为 Office 365 订阅配置高可用性联合身份验证。"
ms.openlocfilehash: 111e52531e45e54b8ce53c3f530e9c9d273f24fc
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="5b073-103">在 Azure 中部署 Office 365 的高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="5b073-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

 <span data-ttu-id="5b073-104">**摘要：**在 Microsoft Azure 中为 Office 365 订阅配置高可用性联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="5b073-104">**Summary:** Configure high availability federated authentication for your Office 365 subscription in Microsoft Azure.</span></span>
  
<span data-ttu-id="5b073-105">这篇文章包含指向特定内容的链接，即通过这些虚拟机在 Azure 基础结构服务中为 Microsoft Office 365 部署高可用性联合身份验证的分步说明：</span><span class="sxs-lookup"><span data-stu-id="5b073-105">This article contains links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="5b073-106">两个 Web 应用程序代理服务器</span><span class="sxs-lookup"><span data-stu-id="5b073-106">Two web application proxy servers</span></span>
    
- <span data-ttu-id="5b073-107">两个 Active Directory 联合身份验证服务 (AD FS) 服务器</span><span class="sxs-lookup"><span data-stu-id="5b073-107">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="5b073-108">两个副本域控制器</span><span class="sxs-lookup"><span data-stu-id="5b073-108">Two replica domain controllers</span></span>
    
- <span data-ttu-id="5b073-109">一个运行 Azure AD Connect 的目录同步 (DirSync) 服务器</span><span class="sxs-lookup"><span data-stu-id="5b073-109">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="5b073-110">下面是包含每个服务器的占位符名称的配置。</span><span class="sxs-lookup"><span data-stu-id="5b073-110">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="5b073-111">**Azure 中 Office 365 基础结构的高可用性联合身份验证**</span><span class="sxs-lookup"><span data-stu-id="5b073-111">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![Azure 中高可用性 Office 365 联合身份验证基础结构的最终配置](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="5b073-113">所有虚拟机都位于一个跨界 Azure 虚拟网络 (VNet) 中。</span><span class="sxs-lookup"><span data-stu-id="5b073-113">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="5b073-p101">各个用户的联合身份验证不依赖任何本地资源。不过，如果跨界连接变得不可用，VNet 中的域控制器将无法接收本地 Windows Server AD 中执行的用户帐户和组更新。若要确保此问题不会发生，可以为跨界连接配置高可用性设置。有关详细信息，请参阅[高可用性跨界连接与 VNet 到 VNet 连接](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="5b073-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="5b073-118">用于特定角色的每对虚拟机都位于自己的子网和可用性集中。</span><span class="sxs-lookup"><span data-stu-id="5b073-118">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5b073-p102">由于此 VNet 连接到本地网络，所以此配置不包括管理子网上的跳转框或监视虚拟机。有关详细信息，请参阅 [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm)（运行用于 N 层体系结构的 Windows VM）。</span><span class="sxs-lookup"><span data-stu-id="5b073-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="5b073-p103">此配置的结果是，将对所有 Office 365 用户使用联合身份验证，即可以使用自己的 Windows Server Active Directory 凭据（而不是 Office 365 帐户）进行登录。联合身份验证基础结构使用冗余的一组服务器，它们更易于在 Azure 基础结构服务（而非本地边缘网络）中进行部署。</span><span class="sxs-lookup"><span data-stu-id="5b073-p103">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account. The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="5b073-123">物料清单</span><span class="sxs-lookup"><span data-stu-id="5b073-123">Bill of materials</span></span>

<span data-ttu-id="5b073-124">此基线配置需要以下 Azure 服务和组件集：</span><span class="sxs-lookup"><span data-stu-id="5b073-124">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="5b073-125">七个虚拟机</span><span class="sxs-lookup"><span data-stu-id="5b073-125">Seven virtual machines</span></span>
    
- <span data-ttu-id="5b073-126">一个具有四个子网的跨界虚拟网络</span><span class="sxs-lookup"><span data-stu-id="5b073-126">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="5b073-127">四个资源组</span><span class="sxs-lookup"><span data-stu-id="5b073-127">Four resource groups</span></span>
    
- <span data-ttu-id="5b073-128">三个可用性集</span><span class="sxs-lookup"><span data-stu-id="5b073-128">Three availability sets</span></span>
    
- <span data-ttu-id="5b073-129">一个 Azure 订阅</span><span class="sxs-lookup"><span data-stu-id="5b073-129">One Azure subscription</span></span>
    
<span data-ttu-id="5b073-130">这里是针对此配置的虚拟机及其默认大小。</span><span class="sxs-lookup"><span data-stu-id="5b073-130">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="5b073-131">**项**</span><span class="sxs-lookup"><span data-stu-id="5b073-131">**Item**</span></span>|<span data-ttu-id="5b073-132">**虚拟机说明**</span><span class="sxs-lookup"><span data-stu-id="5b073-132">**Virtual machine description**</span></span>|<span data-ttu-id="5b073-133">**Azure 库图像**</span><span class="sxs-lookup"><span data-stu-id="5b073-133">**Azure gallery image**</span></span>|<span data-ttu-id="5b073-134">**默认大小**</span><span class="sxs-lookup"><span data-stu-id="5b073-134">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="5b073-135">1.</span><span class="sxs-lookup"><span data-stu-id="5b073-135">1.</span></span>  <br/> |<span data-ttu-id="5b073-136">第一个域控制器</span><span class="sxs-lookup"><span data-stu-id="5b073-136">First domain controller</span></span>  <br/> |<span data-ttu-id="5b073-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5b073-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5b073-138">D2</span><span class="sxs-lookup"><span data-stu-id="5b073-138">D2</span></span>  <br/> |
|<span data-ttu-id="5b073-139">2.</span><span class="sxs-lookup"><span data-stu-id="5b073-139">2.</span></span>  <br/> |<span data-ttu-id="5b073-140">第二个域控制器</span><span class="sxs-lookup"><span data-stu-id="5b073-140">Second domain controller</span></span>  <br/> |<span data-ttu-id="5b073-141">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5b073-141">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5b073-142">D2</span><span class="sxs-lookup"><span data-stu-id="5b073-142">D2</span></span>  <br/> |
|<span data-ttu-id="5b073-143">3.</span><span class="sxs-lookup"><span data-stu-id="5b073-143">3.</span></span>  <br/> |<span data-ttu-id="5b073-144">Azure AD Connect 服务器</span><span class="sxs-lookup"><span data-stu-id="5b073-144">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="5b073-145">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5b073-145">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5b073-146">D2</span><span class="sxs-lookup"><span data-stu-id="5b073-146">D2</span></span>  <br/> |
|<span data-ttu-id="5b073-147">4.</span><span class="sxs-lookup"><span data-stu-id="5b073-147">4.</span></span>  <br/> |<span data-ttu-id="5b073-148">第一个 AD FS 服务器</span><span class="sxs-lookup"><span data-stu-id="5b073-148">First AD FS server</span></span>  <br/> |<span data-ttu-id="5b073-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5b073-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5b073-150">D2</span><span class="sxs-lookup"><span data-stu-id="5b073-150">D2</span></span>  <br/> |
|<span data-ttu-id="5b073-151">5.</span><span class="sxs-lookup"><span data-stu-id="5b073-151">5.</span></span>  <br/> |<span data-ttu-id="5b073-152">第二个 AD FS 服务器</span><span class="sxs-lookup"><span data-stu-id="5b073-152">Second AD FS server</span></span>  <br/> |<span data-ttu-id="5b073-153">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5b073-153">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5b073-154">D2</span><span class="sxs-lookup"><span data-stu-id="5b073-154">D2</span></span>  <br/> |
|<span data-ttu-id="5b073-155">6.</span><span class="sxs-lookup"><span data-stu-id="5b073-155">6.</span></span>  <br/> |<span data-ttu-id="5b073-156">第一个 Web 应用程序代理服务器</span><span class="sxs-lookup"><span data-stu-id="5b073-156">First web application proxy server</span></span>  <br/> |<span data-ttu-id="5b073-157">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5b073-157">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5b073-158">D2</span><span class="sxs-lookup"><span data-stu-id="5b073-158">D2</span></span>  <br/> |
|<span data-ttu-id="5b073-159">7.</span><span class="sxs-lookup"><span data-stu-id="5b073-159">7.</span></span>  <br/> |<span data-ttu-id="5b073-160">第二个 Web 应用程序代理服务器</span><span class="sxs-lookup"><span data-stu-id="5b073-160">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="5b073-161">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5b073-161">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5b073-162">D2</span><span class="sxs-lookup"><span data-stu-id="5b073-162">D2</span></span>  <br/> |
   
<span data-ttu-id="5b073-163">若要计算此配置的估算成本，请参阅 [Azure 定价计算器](https://azure.microsoft.com/pricing/calculator/)</span><span class="sxs-lookup"><span data-stu-id="5b073-163">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="5b073-164">部署阶段</span><span class="sxs-lookup"><span data-stu-id="5b073-164">Phases of deployment</span></span>

<span data-ttu-id="5b073-165">在以下阶段部署此工作负载：</span><span class="sxs-lookup"><span data-stu-id="5b073-165">You deploy this workload in the following phases:</span></span>
  
<span data-ttu-id="5b073-166"><<<<<<< 头</span><span class="sxs-lookup"><span data-stu-id="5b073-166"><<<<<<< HEAD</span></span>
- <span data-ttu-id="5b073-p104">[高可用性联合身份验证阶段 1：配置 Azure](high-availability-federated-authentication-phase-1-configure-azure.md) - 创建资源组、存储帐户、可用性集和跨界虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="5b073-p104">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="5b073-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。创建和配置副本 Windows Server Active Directory (AD) 域控制器和目录同步服务器。</span><span class="sxs-lookup"><span data-stu-id="5b073-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="5b073-p106">[高可用性联合身份验证阶段 3：配置 AD FS 服务器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) - 创建和配置两个 AD FS 服务器。</span><span class="sxs-lookup"><span data-stu-id="5b073-p106">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="5b073-p107">[高可用性联合身份验证阶段 4：配置 Web 应用代理](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) - 创建和配置两个 Web 应用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="5b073-p107">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="5b073-p108">[高可用性联合身份验证阶段 5：为 Office 365 配置联合身份验证](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) - 为 Office 365 订阅配置联合身份验证。=======</span><span class="sxs-lookup"><span data-stu-id="5b073-p108">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription. =======</span></span>
- <span data-ttu-id="5b073-177">[高可用性联合身份验证阶段 1：配置 Azure](high-availability-federated-authentication-phase-1-configure-azure.md) - 创建资源组、存储帐户、可用性集和跨界虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="5b073-177">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md) - Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="5b073-178">[高可用性联合身份验证阶段 2：配置域控制器](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) - 创建和配置副本 Windows Server Active Directory (AD) 域控制器和 DirSync 服务器。</span><span class="sxs-lookup"><span data-stu-id="5b073-178">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) - Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="5b073-179">[高可用性联合身份验证阶段 3：配置 AD FS 服务器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) - 创建和配置两个 AD FS 服务器。</span><span class="sxs-lookup"><span data-stu-id="5b073-179">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) - Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="5b073-180">[高可用性联合身份验证阶段 4：配置 Web 应用代理](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) - 创建和配置两个 Web 应用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="5b073-180">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) - Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="5b073-181">[高可用性联合身份验证阶段 5：为 Office 365 配置联合身份验证](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) - 为 Office 365 订阅配置联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="5b073-181">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) - Configure federated authentication for your Office 365 subscription.</span></span>
>>>>>>> <span data-ttu-id="5b073-182">母版</span><span class="sxs-lookup"><span data-stu-id="5b073-182">master</span></span>
    
<span data-ttu-id="5b073-p109">这些文章提供了预定义的体系结构的规范分阶段指南，以便在 Azure 基础结构服务中为 Office 365 Azure 创建实用的高可用性联合身份验证。请注意下列事项：</span><span class="sxs-lookup"><span data-stu-id="5b073-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="5b073-185">如果你是有经验的 AD FS 实施者，则可以自由调整第 3 阶段和第 4 阶段的说明，构建最符合你需求的服务器集。</span><span class="sxs-lookup"><span data-stu-id="5b073-185">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="5b073-186">如果你已经拥有现有的 Azure 混合云部署以及现有的跨界虚拟网络，则可以随意调整或跳过第 1 阶段和第 2 阶段中的说明，并将 AD FS 和 Web 应用程序代理服务器置于相应的子网上。</span><span class="sxs-lookup"><span data-stu-id="5b073-186">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="5b073-187">若要构建开发/测试环境或此配置的概念证明，请参阅 [用于 Office 365 开发/测试环境的联合身份](federated-identity-for-your-office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="5b073-187">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="5b073-188">后续步骤</span><span class="sxs-lookup"><span data-stu-id="5b073-188">Next step</span></span>

<span data-ttu-id="5b073-189">使用 [高可用性联合身份验证阶段 1:配置 Azure](high-availability-federated-authentication-phase-1-configure-azure.md) 开始配置此工作负载。</span><span class="sxs-lookup"><span data-stu-id="5b073-189">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
> [!TIP]
> <span data-ttu-id="5b073-190">有关可方便在 Azure 中更快速地部署 Office 365 高可用性联合身份验证的一组文件，请参阅 [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)（Azure 部署工具包中的 Office 365 联合身份验证）。</span><span class="sxs-lookup"><span data-stu-id="5b073-190">For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="5b073-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b073-191">See Also</span></span>

[<span data-ttu-id="5b073-192">用于 Office 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="5b073-192">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="5b073-193">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="5b073-193">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="5b073-194">Office 365 的联合标识</span><span class="sxs-lookup"><span data-stu-id="5b073-194">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


