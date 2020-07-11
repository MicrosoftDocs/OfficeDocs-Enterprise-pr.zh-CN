---
title: 高可用性联合身份验证阶段1配置 Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 摘要：配置 Microsoft Azure 基础结构以托管 Microsoft 365 的高可用性联合身份验证。
ms.openlocfilehash: 5b0eed42076a79af52566868c8e6134c48fd847f
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102540"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="03b23-103">高可用性联合身份验证阶段 1：配置 Azure</span><span class="sxs-lookup"><span data-stu-id="03b23-103">High availability federated authentication Phase 1: Configure Azure</span></span>

<span data-ttu-id="03b23-104">在此阶段中，将在 Azure 中创建资源组、虚拟网络 (VNet) 和可用性集，这些集将承载第2阶段、3步和第4阶段的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="03b23-104">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4.</span></span> <span data-ttu-id="03b23-105">必须先完成此阶段，然后才能进入[第2阶段：配置域控制器](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="03b23-105">You must complete this phase before moving on to [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="03b23-106">有关所有阶段，请参阅[在 Azure 中为 Microsoft 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="03b23-106">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="03b23-107">必须使用以下基本组件预配 Azure：</span><span class="sxs-lookup"><span data-stu-id="03b23-107">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="03b23-108">资源组</span><span class="sxs-lookup"><span data-stu-id="03b23-108">Resource groups</span></span>
    
- <span data-ttu-id="03b23-109">包含用于托管 Azure 虚拟机的子网的跨界 Azure 虚拟网络 (VNet) </span><span class="sxs-lookup"><span data-stu-id="03b23-109">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="03b23-110">执行子网隔离的网络安全组</span><span class="sxs-lookup"><span data-stu-id="03b23-110">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="03b23-111">可用性集</span><span class="sxs-lookup"><span data-stu-id="03b23-111">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="03b23-112">配置 Azure 组件</span><span class="sxs-lookup"><span data-stu-id="03b23-112">Configure Azure components</span></span>

<span data-ttu-id="03b23-113">开始配置 Azure 组件之前，请填写下表。</span><span class="sxs-lookup"><span data-stu-id="03b23-113">Before you begin configuring Azure components, fill in the following tables.</span></span> <span data-ttu-id="03b23-114">为了帮助你完成配置 Azure 的过程，请打印此部分并记下所需的信息，或将此部分复制到文档中进行填写。</span><span class="sxs-lookup"><span data-stu-id="03b23-114">To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in.</span></span> <span data-ttu-id="03b23-115">对于 VNet 的设置，请填写表 V。</span><span class="sxs-lookup"><span data-stu-id="03b23-115">For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="03b23-116">**项**</span><span class="sxs-lookup"><span data-stu-id="03b23-116">**Item**</span></span>|<span data-ttu-id="03b23-117">**配置设置**</span><span class="sxs-lookup"><span data-stu-id="03b23-117">**Configuration setting**</span></span>|<span data-ttu-id="03b23-118">**说明**</span><span class="sxs-lookup"><span data-stu-id="03b23-118">**Description**</span></span>|<span data-ttu-id="03b23-119">**值**</span><span class="sxs-lookup"><span data-stu-id="03b23-119">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="03b23-120">1.</span><span class="sxs-lookup"><span data-stu-id="03b23-120">1.</span></span>  <br/> |<span data-ttu-id="03b23-121">VNet 名称</span><span class="sxs-lookup"><span data-stu-id="03b23-121">VNet name</span></span>  <br/> |<span data-ttu-id="03b23-122">要分配给 VNet (示例 FedAuthNet) 的名称。</span><span class="sxs-lookup"><span data-stu-id="03b23-122">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-124">2.</span><span class="sxs-lookup"><span data-stu-id="03b23-124">2.</span></span>  <br/> |<span data-ttu-id="03b23-125">VNet 位置</span><span class="sxs-lookup"><span data-stu-id="03b23-125">VNet location</span></span>  <br/> |<span data-ttu-id="03b23-126">将包含虚拟网络的区域 Azure 数据中心。</span><span class="sxs-lookup"><span data-stu-id="03b23-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-128">3.</span><span class="sxs-lookup"><span data-stu-id="03b23-128">3.</span></span>  <br/> |<span data-ttu-id="03b23-129">VPN 设备 IP 地址</span><span class="sxs-lookup"><span data-stu-id="03b23-129">VPN device IP address</span></span>  <br/> |<span data-ttu-id="03b23-130">Internet 上 VPN 设备接口的公共 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-130">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-132">4.</span><span class="sxs-lookup"><span data-stu-id="03b23-132">4.</span></span>  <br/> |<span data-ttu-id="03b23-133">VNet 地址空间</span><span class="sxs-lookup"><span data-stu-id="03b23-133">VNet address space</span></span>  <br/> |<span data-ttu-id="03b23-134">The address space for the virtual network.</span><span class="sxs-lookup"><span data-stu-id="03b23-134">The address space for the virtual network.</span></span> <span data-ttu-id="03b23-135">Work with your IT department to determine this address space.</span><span class="sxs-lookup"><span data-stu-id="03b23-135">Work with your IT department to determine this address space.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-137">5.</span><span class="sxs-lookup"><span data-stu-id="03b23-137">5.</span></span>  <br/> |<span data-ttu-id="03b23-138">IPsec 共享的密钥</span><span class="sxs-lookup"><span data-stu-id="03b23-138">IPsec shared key</span></span>  <br/> |<span data-ttu-id="03b23-139">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection.</span><span class="sxs-lookup"><span data-stu-id="03b23-139">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection.</span></span> <span data-ttu-id="03b23-140">Work with your IT or security department to determine this key value.</span><span class="sxs-lookup"><span data-stu-id="03b23-140">Work with your IT or security department to determine this key value.</span></span> <span data-ttu-id="03b23-141">Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="03b23-141">Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="03b23-143">**表 V：跨部署虚拟网络配置**</span><span class="sxs-lookup"><span data-stu-id="03b23-143">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="03b23-144">Next, fill in Table S for the subnets of this solution.</span><span class="sxs-lookup"><span data-stu-id="03b23-144">Next, fill in Table S for the subnets of this solution.</span></span> <span data-ttu-id="03b23-145">All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format.</span><span class="sxs-lookup"><span data-stu-id="03b23-145">All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format.</span></span> <span data-ttu-id="03b23-146">An example is 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="03b23-146">An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="03b23-147">对于前三个子网，请根据虚拟网络地址空间指定一个名称和一个 IP 地址空间。</span><span class="sxs-lookup"><span data-stu-id="03b23-147">For the first three subnets, specify a name and a single IP address space based on the virtual network address space.</span></span> <span data-ttu-id="03b23-148">对于网关子网，请使用以下内容确定具有/27 前缀长度) 的27位地址空间 (。具有以下各项的 Azure 网关子网。</span><span class="sxs-lookup"><span data-stu-id="03b23-148">For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="03b23-149">将 VNet 地址空间的可变位设置为 1，直到用于网关子网的位，然后将剩余位设置为 0。</span><span class="sxs-lookup"><span data-stu-id="03b23-149">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="03b23-150">将生成位转换为十进制并表示为一个地址空间，其中将前缀长度设置为网关子网的大小。</span><span class="sxs-lookup"><span data-stu-id="03b23-150">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="03b23-151">有关为您执行此计算的 PowerShell 命令块和 c # 或 Python 控制台应用程序，请参阅[Azure 网关子网的地址空间计算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。</span><span class="sxs-lookup"><span data-stu-id="03b23-151">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="03b23-152">与 IT 部门协作以确定这些虚拟网络地址空间中的地址空间。</span><span class="sxs-lookup"><span data-stu-id="03b23-152">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="03b23-153">**项**</span><span class="sxs-lookup"><span data-stu-id="03b23-153">**Item**</span></span>|<span data-ttu-id="03b23-154">**子网名称**</span><span class="sxs-lookup"><span data-stu-id="03b23-154">**Subnet name**</span></span>|<span data-ttu-id="03b23-155">**子网地址空间**</span><span class="sxs-lookup"><span data-stu-id="03b23-155">**Subnet address space**</span></span>|<span data-ttu-id="03b23-156">**用途**</span><span class="sxs-lookup"><span data-stu-id="03b23-156">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="03b23-157">1.</span><span class="sxs-lookup"><span data-stu-id="03b23-157">1.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="03b23-160">Active Directory 域服务 (AD DS) 域控制器和目录同步服务器虚拟机 (Vm) 使用的子网。</span><span class="sxs-lookup"><span data-stu-id="03b23-160">The subnet used by the Active Directory Domain Services (AD DS) domain controller and directory synchronization server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="03b23-161">2.</span><span class="sxs-lookup"><span data-stu-id="03b23-161">2.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="03b23-164">AD FS Vm 使用的子网。</span><span class="sxs-lookup"><span data-stu-id="03b23-164">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="03b23-165">3.</span><span class="sxs-lookup"><span data-stu-id="03b23-165">3.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="03b23-168">Web 应用程序代理虚拟机使用的子网。</span><span class="sxs-lookup"><span data-stu-id="03b23-168">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="03b23-169">4.</span><span class="sxs-lookup"><span data-stu-id="03b23-169">4.</span></span>  <br/> |<span data-ttu-id="03b23-170">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="03b23-170">GatewaySubnet</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="03b23-172">Azure 网关虚拟机使用的子网。</span><span class="sxs-lookup"><span data-stu-id="03b23-172">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="03b23-173">**表 S：虚拟网络中的子网**</span><span class="sxs-lookup"><span data-stu-id="03b23-173">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="03b23-174">下一步，针对分配给虚拟机和负载平衡器实例的静态 IP 地址填写表 I。</span><span class="sxs-lookup"><span data-stu-id="03b23-174">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="03b23-175">**项目**</span><span class="sxs-lookup"><span data-stu-id="03b23-175">**Item**</span></span>|<span data-ttu-id="03b23-176">**用途**</span><span class="sxs-lookup"><span data-stu-id="03b23-176">**Purpose**</span></span>|<span data-ttu-id="03b23-177">**子网的 IP 地址**</span><span class="sxs-lookup"><span data-stu-id="03b23-177">**IP address on the subnet**</span></span>|<span data-ttu-id="03b23-178">**值**</span><span class="sxs-lookup"><span data-stu-id="03b23-178">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="03b23-179">1.</span><span class="sxs-lookup"><span data-stu-id="03b23-179">1.</span></span>  <br/> |<span data-ttu-id="03b23-180">第一个域控制器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="03b23-180">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="03b23-181">在表 S 的项目 1 中定义的子网地址空间的第四个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-181">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-183">2.</span><span class="sxs-lookup"><span data-stu-id="03b23-183">2.</span></span>  <br/> |<span data-ttu-id="03b23-184">第二个域控制器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="03b23-184">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="03b23-185">在表 S 的项目 1 中定义的子网地址空间的第五个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-185">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-187">3.</span><span class="sxs-lookup"><span data-stu-id="03b23-187">3.</span></span>  <br/> |<span data-ttu-id="03b23-188">目录同步服务器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="03b23-188">Static IP address of the directory synchronization server</span></span>  <br/> |<span data-ttu-id="03b23-189">在表 S 的项目1中定义的子网地址空间的第六个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-189">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-191">4.</span><span class="sxs-lookup"><span data-stu-id="03b23-191">4.</span></span>  <br/> |<span data-ttu-id="03b23-192">AD FS 服务器的内部负载平衡器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="03b23-192">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="03b23-193">在表 S 的项目 2 中定义的子网地址空间的第四个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-193">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-195">5.</span><span class="sxs-lookup"><span data-stu-id="03b23-195">5.</span></span>  <br/> |<span data-ttu-id="03b23-196">第一个 AD FS 服务器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="03b23-196">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="03b23-197">在表 S 的项目 2 中定义的子网地址空间的第五个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-197">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-199">6.</span><span class="sxs-lookup"><span data-stu-id="03b23-199">6.</span></span>  <br/> |<span data-ttu-id="03b23-200">第二个 AD FS 服务器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="03b23-200">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="03b23-201">在表 S 的项目 2 中定义的子网地址空间的第六个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-201">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-203">7.</span><span class="sxs-lookup"><span data-stu-id="03b23-203">7.</span></span>  <br/> |<span data-ttu-id="03b23-204">第一个 web 应用程序代理服务器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="03b23-204">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="03b23-205">在表 S 的项目 3 中定义的子网地址空间的第四个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-205">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-207">8.</span><span class="sxs-lookup"><span data-stu-id="03b23-207">8.</span></span>  <br/> |<span data-ttu-id="03b23-208">第二个 web 应用程序代理服务器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="03b23-208">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="03b23-209">在表 S 的项目 3 中定义的子网地址空间的第五个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-209">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="03b23-211">**表 I：虚拟网络中的静态 IP 地址**</span><span class="sxs-lookup"><span data-stu-id="03b23-211">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="03b23-212">对于您希望在最初设置虚拟网络中的域控制器时使用的本地网络中的两个服务器 (DNS) 服务器的两个域名系统，请填写表 D。与 IT 部门合作以确定此列表。</span><span class="sxs-lookup"><span data-stu-id="03b23-212">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="03b23-213">**项**</span><span class="sxs-lookup"><span data-stu-id="03b23-213">**Item**</span></span>|<span data-ttu-id="03b23-214">**DNS 服务器的友好名称**</span><span class="sxs-lookup"><span data-stu-id="03b23-214">**DNS server friendly name**</span></span>|<span data-ttu-id="03b23-215">**DNS 服务器的 IP 地址**</span><span class="sxs-lookup"><span data-stu-id="03b23-215">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="03b23-216">1.</span><span class="sxs-lookup"><span data-stu-id="03b23-216">1.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-219">2.</span><span class="sxs-lookup"><span data-stu-id="03b23-219">2.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="03b23-222">**表 D：本地 DNS 服务器**</span><span class="sxs-lookup"><span data-stu-id="03b23-222">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="03b23-223">若要在整个站点到站点 VPN 连接中将数据包从跨界网络路由到组织网络，您必须使用本地网络配置虚拟网络，该本地网络的地址空间列表 (在您组织的内部部署网络中的所有可访问位置的 CIDR 表示法) 中。</span><span class="sxs-lookup"><span data-stu-id="03b23-223">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that has a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network.</span></span> <span data-ttu-id="03b23-224">定义本地网络的地址空间列表必须是唯一的，并且不得与用于其他虚拟网络或其他本地网络的地址空间重叠。</span><span class="sxs-lookup"><span data-stu-id="03b23-224">The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="03b23-225">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more.</span><span class="sxs-lookup"><span data-stu-id="03b23-225">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more.</span></span> <span data-ttu-id="03b23-226">Work with your IT department to determine this list of address spaces.</span><span class="sxs-lookup"><span data-stu-id="03b23-226">Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="03b23-227">**项**</span><span class="sxs-lookup"><span data-stu-id="03b23-227">**Item**</span></span>|<span data-ttu-id="03b23-228">**本地网络地址空间**</span><span class="sxs-lookup"><span data-stu-id="03b23-228">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="03b23-229">1.</span><span class="sxs-lookup"><span data-stu-id="03b23-229">1.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-231">2.</span><span class="sxs-lookup"><span data-stu-id="03b23-231">2.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-233">3.</span><span class="sxs-lookup"><span data-stu-id="03b23-233">3.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="03b23-235">**表 L：本地网络的地址前缀**</span><span class="sxs-lookup"><span data-stu-id="03b23-235">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="03b23-236">现在，让我们开始构建 Azure 基础结构以托管适用于 Microsoft 365 的联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="03b23-236">Now let's begin building the Azure infrastructure to host your federated authentication for Microsoft 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="03b23-237">[!注意] 下面的命令集使用最新版 Azure PowerShell。</span><span class="sxs-lookup"><span data-stu-id="03b23-237">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="03b23-238">请参阅[Azure PowerShell 入门](https://docs.microsoft.com/powershell/azure/get-started-azureps)。</span><span class="sxs-lookup"><span data-stu-id="03b23-238">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="03b23-239">首先，启动 Azure PowerShell 提示符并登录到你的帐户。</span><span class="sxs-lookup"><span data-stu-id="03b23-239">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```powershell
Connect-AzAccount
```

> [!TIP]
> <span data-ttu-id="03b23-240">若要基于自定义设置生成可随时运行的 PowerShell 命令块，请使用此[Microsoft Excel 配置工作簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx)。</span><span class="sxs-lookup"><span data-stu-id="03b23-240">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span></span> 

<span data-ttu-id="03b23-241">使用以下命令获得订阅名称。</span><span class="sxs-lookup"><span data-stu-id="03b23-241">Get your subscription name using the following command.</span></span>
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="03b23-242">对于较旧版本的 Azure PowerShell，请改为使用此命令。</span><span class="sxs-lookup"><span data-stu-id="03b23-242">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="03b23-243">设置 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="03b23-243">Set your Azure subscription.</span></span> <span data-ttu-id="03b23-244">使用正确的名称替换引号内的所有内容（包括 \< and > 字符）。</span><span class="sxs-lookup"><span data-stu-id="03b23-244">Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="03b23-245">接下来，创建新的资源组。</span><span class="sxs-lookup"><span data-stu-id="03b23-245">Next, create the new resource groups.</span></span> <span data-ttu-id="03b23-246">要确定唯一的一组资源组名称，请使用此命令列出现有的资源组。</span><span class="sxs-lookup"><span data-stu-id="03b23-246">To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="03b23-247">为一组唯一资源组名称填写下表。</span><span class="sxs-lookup"><span data-stu-id="03b23-247">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="03b23-248">**项目**</span><span class="sxs-lookup"><span data-stu-id="03b23-248">**Item**</span></span>|<span data-ttu-id="03b23-249">**资源组名称**</span><span class="sxs-lookup"><span data-stu-id="03b23-249">**Resource group name**</span></span>|<span data-ttu-id="03b23-250">**用途**</span><span class="sxs-lookup"><span data-stu-id="03b23-250">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="03b23-251">1.</span><span class="sxs-lookup"><span data-stu-id="03b23-251">1.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="03b23-253">域控制器</span><span class="sxs-lookup"><span data-stu-id="03b23-253">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="03b23-254">2.</span><span class="sxs-lookup"><span data-stu-id="03b23-254">2.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="03b23-256">AD FS 服务器</span><span class="sxs-lookup"><span data-stu-id="03b23-256">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="03b23-257">3.</span><span class="sxs-lookup"><span data-stu-id="03b23-257">3.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="03b23-259">Web 应用程序代理服务器</span><span class="sxs-lookup"><span data-stu-id="03b23-259">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="03b23-260">4.</span><span class="sxs-lookup"><span data-stu-id="03b23-260">4.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="03b23-262">基础结构元素</span><span class="sxs-lookup"><span data-stu-id="03b23-262">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="03b23-263">**表 R：资源组**</span><span class="sxs-lookup"><span data-stu-id="03b23-263">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="03b23-264">使用这些命令创建新的资源组。</span><span class="sxs-lookup"><span data-stu-id="03b23-264">Create your new resource groups with these commands.</span></span>
  
```powershell
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="03b23-265">接下来，创建 Azure 虚拟网络及其子网。</span><span class="sxs-lookup"><span data-stu-id="03b23-265">Next, you create the Azure virtual network and its subnets.</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="03b23-266">接下来，为每个具有虚拟机的子网创建网络安全组。</span><span class="sxs-lookup"><span data-stu-id="03b23-266">Next, you create network security groups for each subnet that has virtual machines.</span></span> <span data-ttu-id="03b23-267">若要执行子网隔离，可以添加规则，指定允许或拒绝进入子网的网络安全组的特定类型流量。</span><span class="sxs-lookup"><span data-stu-id="03b23-267">To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```powershell
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

<span data-ttu-id="03b23-268">下一步，请使用这些命令来创建站点间 VPN 连接的网关。</span><span class="sxs-lookup"><span data-stu-id="03b23-268">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="03b23-269">各个用户的联合身份验证不依赖任何本地资源。</span><span class="sxs-lookup"><span data-stu-id="03b23-269">Federated authentication of individual users does not rely on any on-premises resources.</span></span> <span data-ttu-id="03b23-270">但是，如果此站点到站点 VPN 连接变得不可用，VNet 中的域控制器将不会收到在本地 Active Directory 域服务中进行的用户帐户和组的更新。</span><span class="sxs-lookup"><span data-stu-id="03b23-270">However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services.</span></span> <span data-ttu-id="03b23-271">若要确保不会发生这种情况，可以为站点到站点 VPN 连接配置高可用性。</span><span class="sxs-lookup"><span data-stu-id="03b23-271">To ensure this does not happen, you can configure high availability for your site-to-site VPN connection.</span></span> <span data-ttu-id="03b23-272">有关详细信息，请参阅[高可用性跨界连接与 VNet 到 VNet 连接](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="03b23-272">For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="03b23-273">接下来，从此命令的显示内容中，记录用于虚拟网络的 Azure VPN 网关的公用 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-273">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="03b23-274">Next, configure your on-premises VPN device to connect to the Azure VPN gateway.</span><span class="sxs-lookup"><span data-stu-id="03b23-274">Next, configure your on-premises VPN device to connect to the Azure VPN gateway.</span></span> <span data-ttu-id="03b23-275">For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="03b23-275">For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="03b23-276">若要配置本地 VPN 设备，需要以下各项：</span><span class="sxs-lookup"><span data-stu-id="03b23-276">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="03b23-277">Azure VPN 网关的公用 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="03b23-277">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="03b23-278">站点到站点 VPN 连接的 IPsec 预共享密钥（表 V - 第 5 项 - 值列）。</span><span class="sxs-lookup"><span data-stu-id="03b23-278">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="03b23-279">Next, ensure that the address space of the virtual network is reachable from your on-premises network.</span><span class="sxs-lookup"><span data-stu-id="03b23-279">Next, ensure that the address space of the virtual network is reachable from your on-premises network.</span></span> <span data-ttu-id="03b23-280">This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network.</span><span class="sxs-lookup"><span data-stu-id="03b23-280">This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network.</span></span> <span data-ttu-id="03b23-281">Work with your IT department to determine how to do this.</span><span class="sxs-lookup"><span data-stu-id="03b23-281">Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="03b23-282">接下来，定义三个可用性集的名称。</span><span class="sxs-lookup"><span data-stu-id="03b23-282">Next, define the names of three availability sets.</span></span> <span data-ttu-id="03b23-283">填写表 A。</span><span class="sxs-lookup"><span data-stu-id="03b23-283">Fill out Table A.</span></span> 
  
|<span data-ttu-id="03b23-284">**项目**</span><span class="sxs-lookup"><span data-stu-id="03b23-284">**Item**</span></span>|<span data-ttu-id="03b23-285">**用途**</span><span class="sxs-lookup"><span data-stu-id="03b23-285">**Purpose**</span></span>|<span data-ttu-id="03b23-286">**可用性集的名称**</span><span class="sxs-lookup"><span data-stu-id="03b23-286">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="03b23-287">1.</span><span class="sxs-lookup"><span data-stu-id="03b23-287">1.</span></span>  <br/> |<span data-ttu-id="03b23-288">域控制器</span><span class="sxs-lookup"><span data-stu-id="03b23-288">Domain controllers</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-290">2.</span><span class="sxs-lookup"><span data-stu-id="03b23-290">2.</span></span>  <br/> |<span data-ttu-id="03b23-291">AD FS 服务器</span><span class="sxs-lookup"><span data-stu-id="03b23-291">AD FS servers</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="03b23-293">3.</span><span class="sxs-lookup"><span data-stu-id="03b23-293">3.</span></span>  <br/> |<span data-ttu-id="03b23-294">Web 应用程序代理服务器</span><span class="sxs-lookup"><span data-stu-id="03b23-294">Web application proxy servers</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="03b23-296">**表 A：可用性集**</span><span class="sxs-lookup"><span data-stu-id="03b23-296">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="03b23-297">在第 2、3 和 4 阶段中创建虚拟机时，将需要这些名称。</span><span class="sxs-lookup"><span data-stu-id="03b23-297">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="03b23-298">使用这些 Azure PowerShell 命令创建新的可用性集。</span><span class="sxs-lookup"><span data-stu-id="03b23-298">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```powershell
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

<span data-ttu-id="03b23-299">这是该阶段成功完成后生成的配置。</span><span class="sxs-lookup"><span data-stu-id="03b23-299">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="03b23-300">**第1阶段：适用于 Microsoft 365 的高可用性联合身份验证的 Azure 基础结构**</span><span class="sxs-lookup"><span data-stu-id="03b23-300">**Phase 1: The Azure infrastructure for high availability federated authentication for Microsoft 365**</span></span>

![使用 Azure 基础结构的 Azure 中的高可用性 Microsoft 365 联合身份验证的第1阶段](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="03b23-302">后续步骤</span><span class="sxs-lookup"><span data-stu-id="03b23-302">Next step</span></span>

<span data-ttu-id="03b23-303">使用[阶段2：配置域控制器](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)以继续配置此工作负载。</span><span class="sxs-lookup"><span data-stu-id="03b23-303">Use [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="03b23-304">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03b23-304">See Also</span></span>

[<span data-ttu-id="03b23-305">在 Azure 中为 Microsoft 365 部署高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="03b23-305">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="03b23-306">Microsoft 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="03b23-306">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="03b23-307">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="03b23-307">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)

[<span data-ttu-id="03b23-308">了解 Microsoft 365 标识和 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="03b23-308">Understanding Microsoft 365 identity and Azure Active Directory</span></span>](about-office-365-identity.md)


