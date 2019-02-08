---
title: 高可用性联合身份验证阶段 1 配置 Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 摘要：配置 Microsoft Azure 基础结构以托管 Office 365 的高可用性联合身份验证。
ms.openlocfilehash: bbaefffb6bfa55d9af11e08c2011c7333cefe46e
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897475"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="f720b-103">高可用性联合身份验证阶段 1:配置 Azure</span><span class="sxs-lookup"><span data-stu-id="f720b-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="f720b-104">**摘要：** 配置 Microsoft Azure 基础结构以托管 Office 365 的高可用性联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="f720b-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="f720b-p101">在此阶段中，您将创建的资源组、 阶段 2、 3 和 4 中将承载虚拟机的 Azure 中的虚拟网络 (VNet) 和可用性集。您必须完成之后才能接着到此阶段[高可用性联合身份验证第 2 阶段： 配置域控制器](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。为所有阶段，请参阅[在 Azure 中的 Office 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="f720b-p101">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="f720b-108">Azure 必须设置与这些基本组件：</span><span class="sxs-lookup"><span data-stu-id="f720b-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="f720b-109">资源组</span><span class="sxs-lookup"><span data-stu-id="f720b-109">Resource groups</span></span>
    
- <span data-ttu-id="f720b-110">使用子网托管 Azure 虚拟机的跨界 Azure 虚拟网络 (VNet)</span><span class="sxs-lookup"><span data-stu-id="f720b-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="f720b-111">执行子网隔离的网络安全组</span><span class="sxs-lookup"><span data-stu-id="f720b-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="f720b-112">可用性集</span><span class="sxs-lookup"><span data-stu-id="f720b-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="f720b-113">配置 Azure 组件</span><span class="sxs-lookup"><span data-stu-id="f720b-113">Configure Azure components</span></span>

<span data-ttu-id="f720b-p102">在开始配置 Azure 组件之前，请填充下表中。为了帮助您配置 Azure 的过程，打印本节并记下所需的信息或复制到文档的本部分并填写。VNet 的设置，填写表 V。</span><span class="sxs-lookup"><span data-stu-id="f720b-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="f720b-117">**项**</span><span class="sxs-lookup"><span data-stu-id="f720b-117">**Item**</span></span>|<span data-ttu-id="f720b-118">**配置设置**</span><span class="sxs-lookup"><span data-stu-id="f720b-118">**Configuration setting**</span></span>|<span data-ttu-id="f720b-119">**说明**</span><span class="sxs-lookup"><span data-stu-id="f720b-119">**Description**</span></span>|<span data-ttu-id="f720b-120">**值**</span><span class="sxs-lookup"><span data-stu-id="f720b-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="f720b-121">1.</span><span class="sxs-lookup"><span data-stu-id="f720b-121">1.</span></span>  <br/> |<span data-ttu-id="f720b-122">VNet 名称</span><span class="sxs-lookup"><span data-stu-id="f720b-122">VNet name</span></span>  <br/> |<span data-ttu-id="f720b-123">要分配给 VNet 的名称（示例 FedAuthNet）。</span><span class="sxs-lookup"><span data-stu-id="f720b-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-124">2.</span><span class="sxs-lookup"><span data-stu-id="f720b-124">2.</span></span>  <br/> |<span data-ttu-id="f720b-125">VNet 位置</span><span class="sxs-lookup"><span data-stu-id="f720b-125">VNet location</span></span>  <br/> |<span data-ttu-id="f720b-126">将包含虚拟网络的区域 Azure 数据中心。</span><span class="sxs-lookup"><span data-stu-id="f720b-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-127">3.</span><span class="sxs-lookup"><span data-stu-id="f720b-127">3.</span></span>  <br/> |<span data-ttu-id="f720b-128">VPN 设备 IP 地址</span><span class="sxs-lookup"><span data-stu-id="f720b-128">VPN device IP address</span></span>  <br/> |<span data-ttu-id="f720b-129">Internet 上 VPN 设备接口的公共 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-129">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-130">4.</span><span class="sxs-lookup"><span data-stu-id="f720b-130">4.</span></span>  <br/> |<span data-ttu-id="f720b-131">VNet 地址空间</span><span class="sxs-lookup"><span data-stu-id="f720b-131">VNet address space</span></span>  <br/> |<span data-ttu-id="f720b-p103">虚拟网络的地址空间。与 IT 部门协作，以确定该地址空间。</span><span class="sxs-lookup"><span data-stu-id="f720b-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-134">5.</span><span class="sxs-lookup"><span data-stu-id="f720b-134">5.</span></span>  <br/> |<span data-ttu-id="f720b-135">IPsec 共享的密钥</span><span class="sxs-lookup"><span data-stu-id="f720b-135">IPsec shared key</span></span>  <br/> |<span data-ttu-id="f720b-p104">一组 32 位字符的随机字母数字字符串，用于对站点间 VPN 连接的两端进行身份验证。与 IT 或安全部门协作来确定此密钥值。或者，请参阅[创建 IPsec 预共享密钥的随机字符串](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)。  </span><span class="sxs-lookup"><span data-stu-id="f720b-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="f720b-139">**表 V：跨部署虚拟网络配置**</span><span class="sxs-lookup"><span data-stu-id="f720b-139">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="f720b-p105">接下来，填写针对此解决方案的子网的表 S。所有地址空间应为无类别域际路由选择 (CIDR) 格式，也称为网络前缀格式。例如，10.24.64.0/20。</span><span class="sxs-lookup"><span data-stu-id="f720b-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="f720b-p106">对于前三个子网，请指定名称和基于虚拟网络地址空间的单个 IP 地址空间。对于网关子网，请通过以下过程为 Azure 网关子网确定 27 位地址空间（带有 /27 前缀长度）：</span><span class="sxs-lookup"><span data-stu-id="f720b-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="f720b-145">将 VNet 地址空间的可变位设置为 1，直到用于网关子网的位，然后将剩余位设置为 0。</span><span class="sxs-lookup"><span data-stu-id="f720b-145">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="f720b-146">将生成位转换为十进制并表示为一个地址空间，其中将前缀长度设置为网关子网的大小。</span><span class="sxs-lookup"><span data-stu-id="f720b-146">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="f720b-147">PowerShell 命令块和 C# 或 Python 控制台应用程序，为您执行此计算，请参阅[Azure 网关子网的地址空间计算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。</span><span class="sxs-lookup"><span data-stu-id="f720b-147">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="f720b-148">与 IT 部门协作以确定这些虚拟网络地址空间中的地址空间。</span><span class="sxs-lookup"><span data-stu-id="f720b-148">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="f720b-149">**项**</span><span class="sxs-lookup"><span data-stu-id="f720b-149">**Item**</span></span>|<span data-ttu-id="f720b-150">**子网名称**</span><span class="sxs-lookup"><span data-stu-id="f720b-150">**Subnet name**</span></span>|<span data-ttu-id="f720b-151">**子网地址空间**</span><span class="sxs-lookup"><span data-stu-id="f720b-151">**Subnet address space**</span></span>|<span data-ttu-id="f720b-152">**用途**</span><span class="sxs-lookup"><span data-stu-id="f720b-152">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="f720b-153">1.</span><span class="sxs-lookup"><span data-stu-id="f720b-153">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="f720b-154">Windows Server Active Directory (AD) 域控制器和目录同步服务器虚拟机 (VM) 使用的子网。</span><span class="sxs-lookup"><span data-stu-id="f720b-154">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="f720b-155">2.</span><span class="sxs-lookup"><span data-stu-id="f720b-155">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="f720b-156">AD FS VM 使用的子网。</span><span class="sxs-lookup"><span data-stu-id="f720b-156">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="f720b-157">3.</span><span class="sxs-lookup"><span data-stu-id="f720b-157">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="f720b-158">Web 应用程序代理 VM 使用的子网。</span><span class="sxs-lookup"><span data-stu-id="f720b-158">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="f720b-159">4.</span><span class="sxs-lookup"><span data-stu-id="f720b-159">4.</span></span>  <br/> |<span data-ttu-id="f720b-160">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="f720b-160">GatewaySubnet</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="f720b-161">Azure 网关 VM 使用的子网。</span><span class="sxs-lookup"><span data-stu-id="f720b-161">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="f720b-162">**表 S：虚拟网络中的子网**</span><span class="sxs-lookup"><span data-stu-id="f720b-162">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="f720b-163">下一步，针对分配给虚拟机和负载平衡器实例的静态 IP 地址填写表 I。</span><span class="sxs-lookup"><span data-stu-id="f720b-163">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="f720b-164">**项目**</span><span class="sxs-lookup"><span data-stu-id="f720b-164">**Item**</span></span>|<span data-ttu-id="f720b-165">**用途**</span><span class="sxs-lookup"><span data-stu-id="f720b-165">**Purpose**</span></span>|<span data-ttu-id="f720b-166">**子网的 IP 地址**</span><span class="sxs-lookup"><span data-stu-id="f720b-166">**IP address on the subnet**</span></span>|<span data-ttu-id="f720b-167">**值**</span><span class="sxs-lookup"><span data-stu-id="f720b-167">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="f720b-168">1.</span><span class="sxs-lookup"><span data-stu-id="f720b-168">1.</span></span>  <br/> |<span data-ttu-id="f720b-169">第一个域控制器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="f720b-169">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="f720b-170">在表 S 的项目 1 中定义的子网地址空间的第四个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-170">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-171">2.</span><span class="sxs-lookup"><span data-stu-id="f720b-171">2.</span></span>  <br/> |<span data-ttu-id="f720b-172">第二个域控制器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="f720b-172">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="f720b-173">在表 S 的项目 1 中定义的子网地址空间的第五个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-173">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-174">3.</span><span class="sxs-lookup"><span data-stu-id="f720b-174">3.</span></span>  <br/> |<span data-ttu-id="f720b-175">目录同步服务器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="f720b-175">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="f720b-176">在表 S 的第 1 项中定义的子网地址空间的第六个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-176">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-177">4.</span><span class="sxs-lookup"><span data-stu-id="f720b-177">4.</span></span>  <br/> |<span data-ttu-id="f720b-178">AD FS 服务器内部负载均衡器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="f720b-178">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="f720b-179">在表 S 的项目 2 中定义的子网地址空间的第四个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-179">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-180">5.</span><span class="sxs-lookup"><span data-stu-id="f720b-180">5.</span></span>  <br/> |<span data-ttu-id="f720b-181">第一个 AD FS 服务器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="f720b-181">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="f720b-182">在表 S 的项目 2 中定义的子网地址空间的第五个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-182">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-183">6.</span><span class="sxs-lookup"><span data-stu-id="f720b-183">6.</span></span>  <br/> |<span data-ttu-id="f720b-184">第二个 AD FS 服务器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="f720b-184">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="f720b-185">在表 S 的项目 2 中定义的子网地址空间的第六个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-185">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-186">7.</span><span class="sxs-lookup"><span data-stu-id="f720b-186">7.</span></span>  <br/> |<span data-ttu-id="f720b-187">第一个 Web 应用程序代理服务器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="f720b-187">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="f720b-188">在表 S 的项目 3 中定义的子网地址空间的第四个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-188">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-189">8.</span><span class="sxs-lookup"><span data-stu-id="f720b-189">8.</span></span>  <br/> |<span data-ttu-id="f720b-190">第二个 Web 应用程序代理服务器的静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="f720b-190">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="f720b-191">在表 S 的项目 3 中定义的子网地址空间的第五个可能的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-191">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="f720b-192">**表 I：虚拟网络中的静态 IP 地址**</span><span class="sxs-lookup"><span data-stu-id="f720b-192">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="f720b-193">对于本地网络中你最初在虚拟网络中设置域控制器时想要使用的两个域名系统 (DNS) 服务器，请填写表 D。与 IT 部门协作，以确定该列表。</span><span class="sxs-lookup"><span data-stu-id="f720b-193">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="f720b-194">**项**</span><span class="sxs-lookup"><span data-stu-id="f720b-194">**Item**</span></span>|<span data-ttu-id="f720b-195">**DNS 服务器的友好名称**</span><span class="sxs-lookup"><span data-stu-id="f720b-195">**DNS server friendly name**</span></span>|<span data-ttu-id="f720b-196">**DNS 服务器的 IP 地址**</span><span class="sxs-lookup"><span data-stu-id="f720b-196">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f720b-197">1.</span><span class="sxs-lookup"><span data-stu-id="f720b-197">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-198">2.</span><span class="sxs-lookup"><span data-stu-id="f720b-198">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="f720b-199">**表 D：本地 DNS 服务器**</span><span class="sxs-lookup"><span data-stu-id="f720b-199">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="f720b-p107">若要跨站点到站点 VPN 连接路由到您的组织的网络从跨界网络数据包，必须配置虚拟网络与包含列表的地址空间 （以 CIDR 表示） 的访问所有本地网络贵组织的本地网络上的位置。定义您的本地网络的地址空间的列表必须是唯一的并且必须使用用于其他虚拟网络或其他本地网络地址空间不重叠。</span><span class="sxs-lookup"><span data-stu-id="f720b-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that has a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="f720b-p108">对于本地网络地址空间集，请填写表 L。请注意已列出三个空白条目，但通常需要更多。与 IT 部门协作，以确定该地址空间列表。</span><span class="sxs-lookup"><span data-stu-id="f720b-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="f720b-204">**项**</span><span class="sxs-lookup"><span data-stu-id="f720b-204">**Item**</span></span>|<span data-ttu-id="f720b-205">**本地网络地址空间**</span><span class="sxs-lookup"><span data-stu-id="f720b-205">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f720b-206">1.</span><span class="sxs-lookup"><span data-stu-id="f720b-206">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-207">2.</span><span class="sxs-lookup"><span data-stu-id="f720b-207">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-208">3.</span><span class="sxs-lookup"><span data-stu-id="f720b-208">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="f720b-209">**表 L：本地网络的地址前缀**</span><span class="sxs-lookup"><span data-stu-id="f720b-209">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="f720b-210">现在让我们开始构建 Azure 基础结构来托管你的 Office 365 联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="f720b-210">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f720b-p109">下面的命令集使用最新版 Azure PowerShell。请参阅 [Azure PowerShell cmdlet 使用入门](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)</span><span class="sxs-lookup"><span data-stu-id="f720b-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="f720b-213">首先，启动 Azure PowerShell 提示符并登录到你的帐户。</span><span class="sxs-lookup"><span data-stu-id="f720b-213">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="f720b-214">对于所有这篇文章并生成即点即已准备 PowerShell 命令块，根据您的自定义设置 Microsoft Excel 配置工作簿中的 PowerShell 命令的文本文件，请参阅在 Azure 中的[for Office 365 联合身份验证部署工具包](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)。</span><span class="sxs-lookup"><span data-stu-id="f720b-214">For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="f720b-215">使用以下命令获得订阅名称。</span><span class="sxs-lookup"><span data-stu-id="f720b-215">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="f720b-216">为 Azure PowerShell 旧版本，而是使用此命令。</span><span class="sxs-lookup"><span data-stu-id="f720b-216">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="f720b-p110">设置 Azure 订阅。使用正确的名称替换引号内的所有内容（包括 \< 和 > 字符）。</span><span class="sxs-lookup"><span data-stu-id="f720b-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="f720b-p111">接下来，创建新的资源组。要确定唯一的一组资源组名称，请使用此命令列出现有的资源组。</span><span class="sxs-lookup"><span data-stu-id="f720b-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="f720b-221">为一组唯一资源组名称填写下表。</span><span class="sxs-lookup"><span data-stu-id="f720b-221">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="f720b-222">**项目**</span><span class="sxs-lookup"><span data-stu-id="f720b-222">**Item**</span></span>|<span data-ttu-id="f720b-223">**资源组名称**</span><span class="sxs-lookup"><span data-stu-id="f720b-223">**Resource group name**</span></span>|<span data-ttu-id="f720b-224">**用途**</span><span class="sxs-lookup"><span data-stu-id="f720b-224">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f720b-225">1.</span><span class="sxs-lookup"><span data-stu-id="f720b-225">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="f720b-226">域控制器</span><span class="sxs-lookup"><span data-stu-id="f720b-226">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="f720b-227">2.</span><span class="sxs-lookup"><span data-stu-id="f720b-227">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="f720b-228">AD FS 服务器</span><span class="sxs-lookup"><span data-stu-id="f720b-228">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="f720b-229">3.</span><span class="sxs-lookup"><span data-stu-id="f720b-229">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="f720b-230">Web 应用程序代理服务器</span><span class="sxs-lookup"><span data-stu-id="f720b-230">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="f720b-231">4.</span><span class="sxs-lookup"><span data-stu-id="f720b-231">4.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="f720b-232">基础结构元素</span><span class="sxs-lookup"><span data-stu-id="f720b-232">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="f720b-233">**表 R：资源组**</span><span class="sxs-lookup"><span data-stu-id="f720b-233">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="f720b-234">使用这些命令创建新的资源组。</span><span class="sxs-lookup"><span data-stu-id="f720b-234">Create your new resource groups with these commands.</span></span>
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="f720b-235">接下来，请创建 Azure 虚拟网络及其子网。</span><span class="sxs-lookup"><span data-stu-id="f720b-235">Next, you create the Azure virtual network and its subnets.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="f720b-p112">接下来，您创建网络具有虚拟机的每个子网的安全组。若要执行子网隔离，您可以添加流量允许或拒绝网络安全组的子网的特定类型的规则。</span><span class="sxs-lookup"><span data-stu-id="f720b-p112">Next, you create network security groups for each subnet that has virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```
# Create network security groups
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="f720b-238">下一步，请使用这些命令来创建站点间 VPN 连接的网关。</span><span class="sxs-lookup"><span data-stu-id="f720b-238">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="f720b-p113">联合身份验证的单个用户不依赖的任何本地资源。但是，如果此站点到站点 VPN 连接变得不可用，VNet 中的域控制器不会收到对用户帐户和组在内部部署 Windows Server AD 中所做的更新。若要确保这不会发生，可以为站点到站点 VPN 连接配置高可用性。有关详细信息，请参阅[高度可用跨内部部署和 VNet 到 VNet 连接](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="f720b-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="f720b-243">接下来，从此命令的显示内容中，记录用于虚拟网络的 Azure VPN 网关的公用 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-243">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="f720b-p114">接下来，请将本地 VPN 设备配置为连接到 Azure VPN 网关。有关详细信息，请参阅[配置 VPN 设备](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。</span><span class="sxs-lookup"><span data-stu-id="f720b-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="f720b-246">若要配置本地 VPN 设备，需要以下各项：</span><span class="sxs-lookup"><span data-stu-id="f720b-246">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="f720b-247">Azure VPN 网关的公用 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="f720b-247">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="f720b-248">站点到站点 VPN 连接的 IPsec 预共享密钥（表 V - 第 5 项 - 值列）。</span><span class="sxs-lookup"><span data-stu-id="f720b-248">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="f720b-p115">接下来，请确保虚拟网络的地址空间是可以从本地网络访问。这通常是通过以下操作完成：将对应于虚拟网络地址空间的路由添加到 VPN 设备中，然后将该路由公布到组织网络中其余的路由基础结构。与 IT 部门协作，以确定如何完成上述操作。</span><span class="sxs-lookup"><span data-stu-id="f720b-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="f720b-p116">接下来，定义三个可用性集的名称。填写表 A。</span><span class="sxs-lookup"><span data-stu-id="f720b-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="f720b-254">**项**</span><span class="sxs-lookup"><span data-stu-id="f720b-254">**Item**</span></span>|<span data-ttu-id="f720b-255">**用途**</span><span class="sxs-lookup"><span data-stu-id="f720b-255">**Purpose**</span></span>|<span data-ttu-id="f720b-256">**可用性集的名称**</span><span class="sxs-lookup"><span data-stu-id="f720b-256">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f720b-257">1.</span><span class="sxs-lookup"><span data-stu-id="f720b-257">1.</span></span>  <br/> |<span data-ttu-id="f720b-258">域控制器</span><span class="sxs-lookup"><span data-stu-id="f720b-258">Domain controllers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-259">2.</span><span class="sxs-lookup"><span data-stu-id="f720b-259">2.</span></span>  <br/> |<span data-ttu-id="f720b-260">AD FS 服务器</span><span class="sxs-lookup"><span data-stu-id="f720b-260">AD FS servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="f720b-261">3.</span><span class="sxs-lookup"><span data-stu-id="f720b-261">3.</span></span>  <br/> |<span data-ttu-id="f720b-262">Web 应用程序代理服务器</span><span class="sxs-lookup"><span data-stu-id="f720b-262">Web application proxy servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="f720b-263">**表 A：可用性集**</span><span class="sxs-lookup"><span data-stu-id="f720b-263">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="f720b-264">在第 2、3 和 4 阶段中创建虚拟机时，将需要这些名称。</span><span class="sxs-lookup"><span data-stu-id="f720b-264">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="f720b-265">通过这些 Azure PowerShell 命令创建新的可用性集。</span><span class="sxs-lookup"><span data-stu-id="f720b-265">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

<span data-ttu-id="f720b-266">这是该阶段成功完成后生成的配置。</span><span class="sxs-lookup"><span data-stu-id="f720b-266">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="f720b-267">**阶段 1：用于 Office 365 高可用性联合身份验证的 Azure 基础结构**</span><span class="sxs-lookup"><span data-stu-id="f720b-267">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![阶段 1：在包含 Azure 基础结构的 Azure 中配置高可用性 Office 365 联合身份验证](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="f720b-269">后续步骤</span><span class="sxs-lookup"><span data-stu-id="f720b-269">Next step</span></span>

<span data-ttu-id="f720b-270">使用 [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) 继续配置此工作负载。</span><span class="sxs-lookup"><span data-stu-id="f720b-270">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f720b-271">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f720b-271">See Also</span></span>

[<span data-ttu-id="f720b-272">在 Azure 中部署 Office 365 的高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="f720b-272">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="f720b-273">用于 Office 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="f720b-273">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="f720b-274">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="f720b-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="f720b-275">了解 Office 365 标识和 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="f720b-275">Understanding Office 365 identity and Azure Active Directory</span></span>](about-office-365-identity.md)


