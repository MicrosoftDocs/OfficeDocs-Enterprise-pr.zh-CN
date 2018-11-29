---
title: 为 Microsoft Azure IaaS 设计网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 摘要： 了解如何设计优化的网络的 Microsoft Azure IaaS 中的工作负荷。
ms.openlocfilehash: d13c1d4b985c633b8336dc33253e1350a54b5a39
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872333"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="5a23f-103">为 Microsoft Azure IaaS 设计网络</span><span class="sxs-lookup"><span data-stu-id="5a23f-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="5a23f-104">**摘要：** 了解如何设计优化的网络的 Microsoft Azure IaaS 中的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="5a23f-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="5a23f-105">若要优化托管在 Azure IaaS 中的 IT 工作负载的网络，需要了解 Azure 虚拟网络 (VNet)、地址空间、路由、DNS 和负载平衡等相关知识。</span><span class="sxs-lookup"><span data-stu-id="5a23f-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="5a23f-106">任何 VNet 的规划步骤</span><span class="sxs-lookup"><span data-stu-id="5a23f-106">Planning steps for any VNet</span></span>

<span data-ttu-id="5a23f-107">对于任何类型的 VNet，请执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="5a23f-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="5a23f-108">步骤 1：为 Microsoft 云服务准备 Intranet。</span><span class="sxs-lookup"><span data-stu-id="5a23f-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="5a23f-109">完成 [Microsoft 云连接的常见元素](common-elements-of-microsoft-cloud-connectivity.md)中的**为 Microsoft 云服务准备网络的步骤**部分。</span><span class="sxs-lookup"><span data-stu-id="5a23f-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="5a23f-110">步骤 2：优化 Internet 带宽。</span><span class="sxs-lookup"><span data-stu-id="5a23f-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="5a23f-111">按照[设计 Microsoft SaaS 网络](designing-networking-for-microsoft-saas.md)中的**为 Microsoft SaaS 服务准备网络的步骤**部分的第 2-4 步操作，优化 Internet 带宽。</span><span class="sxs-lookup"><span data-stu-id="5a23f-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="5a23f-112">步骤 3：确定 VNet 的类型（仅限云或跨界部署）。</span><span class="sxs-lookup"><span data-stu-id="5a23f-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="5a23f-p101">仅限云 VNet 没有到本地网络的连接。下面是一个示例。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="5a23f-115">**图 1：仅限云 VNet**</span><span class="sxs-lookup"><span data-stu-id="5a23f-115">**Figure 1: A cloud-only VNet**</span></span>

![图 1：Azure 中的云专用虚拟网络](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="5a23f-117">图 1 显示了仅限云 VNet 中的一组虚拟机。</span><span class="sxs-lookup"><span data-stu-id="5a23f-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="5a23f-p102">跨界 VNet 具有站点到站点 (S2S) VPN 或通过 Azure 网关实现的到本地网络的 ExpressRoute 连接。下面是一个示例。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="5a23f-120">**图 2：跨界 VNet**</span><span class="sxs-lookup"><span data-stu-id="5a23f-120">**Figure 2: A cross-premises VNet**</span></span>

![图 2：Azure 中的跨界虚拟网络](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="5a23f-122">图 2 显示了连接到本地网络的跨界 VNet 中的一组虚拟机。</span><span class="sxs-lookup"><span data-stu-id="5a23f-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="5a23f-123">其他信息，请参阅本文中的[跨界 VNet 的规划步骤](designing-networking-for-microsoft-azure-iaas.md#cross_prem)部分。</span><span class="sxs-lookup"><span data-stu-id="5a23f-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="5a23f-124">步骤 4：确定 VNet 的地址空间。</span><span class="sxs-lookup"><span data-stu-id="5a23f-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="5a23f-125">表 1 显示不同 VNet 类型的地址空间。</span><span class="sxs-lookup"><span data-stu-id="5a23f-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="5a23f-126">**VNet 类型**</span><span class="sxs-lookup"><span data-stu-id="5a23f-126">**Type of VNet**</span></span>|<span data-ttu-id="5a23f-127">**虚拟网络地址空间**</span><span class="sxs-lookup"><span data-stu-id="5a23f-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5a23f-128">仅限云</span><span class="sxs-lookup"><span data-stu-id="5a23f-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="5a23f-129">任意专用地址空间</span><span class="sxs-lookup"><span data-stu-id="5a23f-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="5a23f-130">互连的仅限云类型</span><span class="sxs-lookup"><span data-stu-id="5a23f-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="5a23f-131">任意专用，但不是重叠的与其他连接 VNets</span><span class="sxs-lookup"><span data-stu-id="5a23f-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="5a23f-132">跨界</span><span class="sxs-lookup"><span data-stu-id="5a23f-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="5a23f-133">专用类型，但不与本地 VNet 重叠</span><span class="sxs-lookup"><span data-stu-id="5a23f-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="5a23f-134">互连的跨界类型</span><span class="sxs-lookup"><span data-stu-id="5a23f-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="5a23f-135">专用类型，但不与本地或其他连接 VNet 重叠</span><span class="sxs-lookup"><span data-stu-id="5a23f-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="5a23f-136">**表 1：VNet 类型及其对应的地址空间**</span><span class="sxs-lookup"><span data-stu-id="5a23f-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="5a23f-137">DHCP 从子网的地址空间中为虚拟机分配地址配置。</span><span class="sxs-lookup"><span data-stu-id="5a23f-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="5a23f-138">地址/子网掩码</span><span class="sxs-lookup"><span data-stu-id="5a23f-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="5a23f-139">默认网关</span><span class="sxs-lookup"><span data-stu-id="5a23f-139">Default gateway</span></span>
    
- <span data-ttu-id="5a23f-140">DNS 服务器 IP 地址</span><span class="sxs-lookup"><span data-stu-id="5a23f-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="5a23f-141">你还可以保留静态的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="5a23f-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="5a23f-142">还可以单独或从包含云服务中为虚拟机分配公用 IP 地址（仅适用于典型的部署计算机）。</span><span class="sxs-lookup"><span data-stu-id="5a23f-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="5a23f-143">步骤 5：确定 VNet 中的子网及分配给每个子网的地址空间。</span><span class="sxs-lookup"><span data-stu-id="5a23f-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="5a23f-144">VNet 中有两种类型的子网：网关子网和虚拟机托管的子网。</span><span class="sxs-lookup"><span data-stu-id="5a23f-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="5a23f-145">**图 3：Azure 中两种类型的子网**</span><span class="sxs-lookup"><span data-stu-id="5a23f-145">**Figure 3: The two types of subnets in Azure**</span></span>

![图 3：Azure 中两种类型的子网](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="5a23f-147">图 3 显示了包含网关子网已 Azure 的网关及一系列包含虚拟机的虚拟机托管的子网 VNet。</span><span class="sxs-lookup"><span data-stu-id="5a23f-147">Figure 3 shows a VNet containing a gateway subnet that has an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="5a23f-p103">Azure 需要 Azure 网关子网来托管 Azure 网关的两个虚拟机。指定前缀长度至少有 29 位的地址空间（例如：192.168.15.248/29）。尤其是在你计划使用 ExpressRoute 时，建议使用 28 位或更短的前缀长度。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p103">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway. Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29). A 28-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="5a23f-151">用于确定 Azure 网关子网的地址空间最佳做法是：</span><span class="sxs-lookup"><span data-stu-id="5a23f-151">A best practice for determining the address space of the Azure gateway subnet is:</span></span>
  
1. <span data-ttu-id="5a23f-152">确定网关子网的大小。</span><span class="sxs-lookup"><span data-stu-id="5a23f-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="5a23f-153">在 VNet 地址空间的可变位中，将用于网关子网的位设置为 0，将剩余位设置为 1。</span><span class="sxs-lookup"><span data-stu-id="5a23f-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="5a23f-154">转换为十进制并表示为一个地址空间，其中将前缀长度设置为网关子网的大小。</span><span class="sxs-lookup"><span data-stu-id="5a23f-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="5a23f-155">使用此方法时，网关子网的地址空间始终位于 VNet 地址空间的最远端。</span><span class="sxs-lookup"><span data-stu-id="5a23f-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="5a23f-p104">下面是定义网关子网的地址前缀的一个示例：VNet 的地址空间是 10.119.0.0/16。该组织最初使用站点到站点的 VPN 连接，但最终采用了 ExpressRoute。表 2 显示了确定网络前缀符号（也称为 CIDR）中的网关子网地址前缀的步骤和结果。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="5a23f-159">下面是步骤和示例确定的网关子网地址前缀：</span><span class="sxs-lookup"><span data-stu-id="5a23f-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="5a23f-p105">决定的网关子网的大小。对于我们的示例，我们选择 /28。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p105">Decide on the size of the gateway subnet. For our example, we chose /28.</span></span>
2. <span data-ttu-id="5a23f-p106">位的部分中设置变量 VNet 地址空间 (b) 的网关的 0 到子网位 (G)，否则为 1 (V)。对于我们的示例，我们将使用 10.119.0.0/16 地址空间 VNet。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p106">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V). For our example, we are using the 10.119.0.0/16 address space for the VNet. </span></span><br/>
<br/><span data-ttu-id="5a23f-p107">10.119。 bbbbbbbb。bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="5a23f-p107">10.119. bbbbbbbb . bbbbbbbb </span></span><br/><span data-ttu-id="5a23f-p108">10.119。 VVVVVVVV。VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="5a23f-p108">10.119. VVVVVVVV . VVVVGGGG </span></span><br/><span data-ttu-id="5a23f-p109">10.119。 11111111。11110000</span><span class="sxs-lookup"><span data-stu-id="5a23f-p109">10.119. 11111111 . 11110000 </span></span><br/><br/>
3. <span data-ttu-id="5a23f-p110">步骤 2 中的结果转换为十进制和 express 作为地址空间。对于我们的示例，10.119。11111111。11110000 10.119.255.240，并使用步骤 1，(在本例中为 28) 中的前缀长度，生成的网关子网地址前缀都是 10.119.255.240/28。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p110">Convert the result from step 2 to decimal and express as an address space. For our example, 10.119. 11111111 . 11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="5a23f-177">有关详细信息，请参阅[Azure 网关子网的地址空间计算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="5a23f-178">虚拟机托管的子网用来放置 Azure 虚拟机，你可以根据典型的本地指南执行这一任务，例如公共角色、应用程序层或用于子网隔离。</span><span class="sxs-lookup"><span data-stu-id="5a23f-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="5a23f-p111">Azure 上的每个子网使用的前 3 的地址。因此，可能在 Azure 子网上地址数是 2<sup>n</sup> -5，其中 n 是主机位的数字。表 3 显示的虚拟机所需的号码范围承载需要的二进制文件和相应的子网大小。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p111">Azure uses the first 3 addresses on each subnet. Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits. Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="5a23f-182">**所需的虚拟机**</span><span class="sxs-lookup"><span data-stu-id="5a23f-182">**Virtual machines required**</span></span>|<span data-ttu-id="5a23f-183">**主机位**</span><span class="sxs-lookup"><span data-stu-id="5a23f-183">**Host bits**</span></span>|<span data-ttu-id="5a23f-184">**子网大小**</span><span class="sxs-lookup"><span data-stu-id="5a23f-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="5a23f-185">1-3</span><span class="sxs-lookup"><span data-stu-id="5a23f-185">1-3</span></span>  <br/> |<span data-ttu-id="5a23f-186">3 </span><span class="sxs-lookup"><span data-stu-id="5a23f-186">3</span></span>  <br/> |<span data-ttu-id="5a23f-187">/29</span><span class="sxs-lookup"><span data-stu-id="5a23f-187">/29</span></span>  <br/> |
|<span data-ttu-id="5a23f-188">4-11</span><span class="sxs-lookup"><span data-stu-id="5a23f-188">4-11</span></span>  <br/> |<span data-ttu-id="5a23f-189">4 </span><span class="sxs-lookup"><span data-stu-id="5a23f-189">4</span></span>  <br/> |<span data-ttu-id="5a23f-190">/28</span><span class="sxs-lookup"><span data-stu-id="5a23f-190">/28</span></span>  <br/> |
|<span data-ttu-id="5a23f-191">12-27</span><span class="sxs-lookup"><span data-stu-id="5a23f-191">12-27</span></span>  <br/> |<span data-ttu-id="5a23f-192">5 </span><span class="sxs-lookup"><span data-stu-id="5a23f-192">5</span></span>  <br/> |<span data-ttu-id="5a23f-193">/27</span><span class="sxs-lookup"><span data-stu-id="5a23f-193">/27</span></span>  <br/> |
|<span data-ttu-id="5a23f-194">28-59</span><span class="sxs-lookup"><span data-stu-id="5a23f-194">28-59</span></span>  <br/> |<span data-ttu-id="5a23f-195">6 </span><span class="sxs-lookup"><span data-stu-id="5a23f-195">6</span></span>  <br/> |<span data-ttu-id="5a23f-196">/26</span><span class="sxs-lookup"><span data-stu-id="5a23f-196">/26</span></span>  <br/> |
|<span data-ttu-id="5a23f-197">60-123</span><span class="sxs-lookup"><span data-stu-id="5a23f-197">60-123</span></span>  <br/> |<span data-ttu-id="5a23f-198">7 </span><span class="sxs-lookup"><span data-stu-id="5a23f-198">7</span></span>  <br/> |<span data-ttu-id="5a23f-199">/25</span><span class="sxs-lookup"><span data-stu-id="5a23f-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="5a23f-200">**表 3：虚拟机要求及其子网大小**</span><span class="sxs-lookup"><span data-stu-id="5a23f-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="5a23f-201">有关虚拟机上的子网或 VNet 的最大量的详细信息，请参阅[网络限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="5a23f-202">有关详细信息，请参阅[规划和设计 Azure 虚拟网络](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="5a23f-203">步骤 6：确定 VNet 中分配给 VM 的 DNS 服务器配置和DNS 服务器地址。</span><span class="sxs-lookup"><span data-stu-id="5a23f-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="5a23f-p112">Azure 根据 DHCP 为虚拟机分配 DNS 服务器的地址。DNS 服务器可以：</span><span class="sxs-lookup"><span data-stu-id="5a23f-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="5a23f-206">由 Azure 提供：提供本地名称注册及本地和 Internet 名称解析</span><span class="sxs-lookup"><span data-stu-id="5a23f-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="5a23f-207">由你提供：提供本地或 Intranet 名称注册及 Intranet 或 Internet 名称解析</span><span class="sxs-lookup"><span data-stu-id="5a23f-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="5a23f-208">表 4 显示了每种类型的 VNet 不同 DNS 服务器的配置。</span><span class="sxs-lookup"><span data-stu-id="5a23f-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="5a23f-209">**VNet 类型**</span><span class="sxs-lookup"><span data-stu-id="5a23f-209">**Type of VNet**</span></span>|<span data-ttu-id="5a23f-210">**DNS 服务器**</span><span class="sxs-lookup"><span data-stu-id="5a23f-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5a23f-211">仅限云</span><span class="sxs-lookup"><span data-stu-id="5a23f-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="5a23f-212">由 Azure 提供，用于本地和 Internet 名称解析</span><span class="sxs-lookup"><span data-stu-id="5a23f-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="5a23f-213">Azure 虚拟机，用于本地和 Internet 名称解析（DNS 转发）</span><span class="sxs-lookup"><span data-stu-id="5a23f-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="5a23f-214">跨界</span><span class="sxs-lookup"><span data-stu-id="5a23f-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="5a23f-215">本地，用于本地和 Intranet 名称解析</span><span class="sxs-lookup"><span data-stu-id="5a23f-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="5a23f-216">Azure 虚拟机，用于本地和 Intranet 名称解析（DNS 复制和转发）</span><span class="sxs-lookup"><span data-stu-id="5a23f-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="5a23f-217">**表 4：针对两种不同类型的 VNet 的 DNS 服务器选项**</span><span class="sxs-lookup"><span data-stu-id="5a23f-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="5a23f-218">有关详细信息，请参阅[虚拟机和角色实例的名称解析](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="5a23f-219">步骤 7：确定负载平衡配置（面向 Internet 或内部）。</span><span class="sxs-lookup"><span data-stu-id="5a23f-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="5a23f-p113">在某些情况下，你需要将传入流量分配给具有相同角色的一组服务器。对于面向 Internet 和内部流量负载，Azure IaaS 使用内置设备来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="5a23f-222">Azure 面向 Internet 的负载平衡功能将来自 Internet 的未经请求的传入流量随机分配给负载平衡集的成员。 </span><span class="sxs-lookup"><span data-stu-id="5a23f-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="5a23f-223">**图 4：Azure 中的外部负载平衡器**</span><span class="sxs-lookup"><span data-stu-id="5a23f-223">**Figure 4: An external load balancer in Azure**</span></span>

![图 4：Azure 中的外部负载平衡器](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="5a23f-225">图 4 显示分发 NAT 的入站的规则或终结点，以一的负载平衡集中的虚拟机上的传入流量的 Azure 中的外部负载平衡器。</span><span class="sxs-lookup"><span data-stu-id="5a23f-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="5a23f-226">Azure 内部负载平衡功能将来自其他 Azure VM 或 Intranet 计算机的未经请求的传入流量随机分配给负载平衡集的成员。 </span><span class="sxs-lookup"><span data-stu-id="5a23f-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="5a23f-227">**图 5：Azure 中的内部负载平衡器**</span><span class="sxs-lookup"><span data-stu-id="5a23f-227">**Figure 5: An internal load balancer in Azure**</span></span>

![图 5：Azure 中的内部负载平衡器](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="5a23f-229">图 5 显示分发 NAT 的入站的规则或终结点，以一的负载平衡集中的虚拟机上的传入流量的 Azure 中的内部负载平衡器。</span><span class="sxs-lookup"><span data-stu-id="5a23f-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="5a23f-230">有关详细信息，请参阅[Azure 负载平衡器](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="5a23f-231">步骤 8：确定使用虚拟设备和用户定义的路由。</span><span class="sxs-lookup"><span data-stu-id="5a23f-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="5a23f-232">如果需要将流量转发到你的 VNet 中的虚拟设备，你可能需要将一个或多个用户定义的路由添加到子网。</span><span class="sxs-lookup"><span data-stu-id="5a23f-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="5a23f-233">**图 6：Azure 中的虚拟设备和用户定义的路由**</span><span class="sxs-lookup"><span data-stu-id="5a23f-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![图 6：Azure 中的虚拟装置和用户定义的路由](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="5a23f-235">图 6 显示了分配给虚拟机托管的子网的跨界 VNet 和用户定义的路由，其中子网指向虚拟设备。</span><span class="sxs-lookup"><span data-stu-id="5a23f-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="5a23f-236">有关详细信息，请参阅[用户定义的路由和 IP 转发](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="5a23f-237">步骤 9：确定 Internet 中的计算机如何连接到虚拟机。</span><span class="sxs-lookup"><span data-stu-id="5a23f-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="5a23f-238">有多种方式提供 Internet 访问 VNet 中的虚拟机的权限，这包括通过代理服务器或其他边缘服务从组织网络访问。</span><span class="sxs-lookup"><span data-stu-id="5a23f-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="5a23f-239">表 5 列出了筛选或检查未经请求的传入流量的方法。</span><span class="sxs-lookup"><span data-stu-id="5a23f-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="5a23f-240">**方法**</span><span class="sxs-lookup"><span data-stu-id="5a23f-240">**Method**</span></span>|<span data-ttu-id="5a23f-241">**部署模型**</span><span class="sxs-lookup"><span data-stu-id="5a23f-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5a23f-242">1.在云服务中配置的终结点和 ACL</span><span class="sxs-lookup"><span data-stu-id="5a23f-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="5a23f-243">经典</span><span class="sxs-lookup"><span data-stu-id="5a23f-243">Classic</span></span>  <br/> |
|<span data-ttu-id="5a23f-244">2.网络安全组</span><span class="sxs-lookup"><span data-stu-id="5a23f-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="5a23f-245">Resource Manager 和经典</span><span class="sxs-lookup"><span data-stu-id="5a23f-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="5a23f-246">3.面向 Internet 的负载平衡器，具有入站 NAT 规则</span><span class="sxs-lookup"><span data-stu-id="5a23f-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="5a23f-247">资源经理</span><span class="sxs-lookup"><span data-stu-id="5a23f-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="5a23f-248">4.网络安全设备中 Azure Marketplace （不显示）</span><span class="sxs-lookup"><span data-stu-id="5a23f-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="5a23f-249">Resource Manager 和经典</span><span class="sxs-lookup"><span data-stu-id="5a23f-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="5a23f-250">**表 5：连接到虚拟机的方法及其对应的 Azure 部署模型**</span><span class="sxs-lookup"><span data-stu-id="5a23f-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="5a23f-251">**图 7：通过 Internet 连接到 Azure 虚拟机**</span><span class="sxs-lookup"><span data-stu-id="5a23f-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![图 7：通过 Internet 连接到 Azure 虚拟机](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="5a23f-253">图 7 显示已连接到 Internet 的计算机使用终结点连接到云服务中的虚拟机、使用网络安全组连接到子网中的虚拟机，以及使用外部负载平衡器和入站 NAT 规则连接到子网中的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="5a23f-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="5a23f-254">其他安全性通过以下项实现：</span><span class="sxs-lookup"><span data-stu-id="5a23f-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="5a23f-255">已验证并已加密的远程桌面和 SSH 连接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="5a23f-256">已验证并已加密的远程 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="5a23f-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="5a23f-257">可用于端到端加密的 IPsec 传输模式。</span><span class="sxs-lookup"><span data-stu-id="5a23f-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="5a23f-258">有助于防止外部和内部攻击的 Azure DDOS 保护</span><span class="sxs-lookup"><span data-stu-id="5a23f-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="5a23f-259">有关详细信息，请参阅[Microsoft 云安全的企业架构师](https://aka.ms/cloudarchsecurity)和[Azure 网络安全](https://azure.microsoft.com/blog/azure-network-security/)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="5a23f-260">步骤 10：为多个 VNet 确定 VNet 到 VNet 连接的拓扑。</span><span class="sxs-lookup"><span data-stu-id="5a23f-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="5a23f-261">可以使用类似于用来连接组织站点的拓扑将 VNet 彼此连接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="5a23f-262">菊花链配置以串联方式连接 VNet。</span><span class="sxs-lookup"><span data-stu-id="5a23f-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="5a23f-263">**图 8：VNet 的菊花链配置**</span><span class="sxs-lookup"><span data-stu-id="5a23f-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![图 8：Azure 虚拟网络的菊花链配置](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="5a23f-265">图 8 显示系列使用串接配置中连接的五个 VNets。</span><span class="sxs-lookup"><span data-stu-id="5a23f-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="5a23f-266">中心辐射型配置将多个 VNet 连接到一组本身已彼此连接的中心 VNet。</span><span class="sxs-lookup"><span data-stu-id="5a23f-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="5a23f-267">**图 9：VNet 的中心辐射型配置**</span><span class="sxs-lookup"><span data-stu-id="5a23f-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![图 9：Azure 虚拟网络的中心辐射型配置](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="5a23f-269">图 9 显示六个 VNet，其中两个是彼此相连的中心 VNet，另外各有两个分支 VNet。</span><span class="sxs-lookup"><span data-stu-id="5a23f-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="5a23f-270">全网状配置使每个 VNet 相互连接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="5a23f-271">**图 10：VNet 的全网状配置**</span><span class="sxs-lookup"><span data-stu-id="5a23f-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![图 10：Azure 虚拟网络的网格配置](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="5a23f-273">图 10 显示了四个全都彼此相连的 VNet，共使用六个 VNet 到 VNet 的连接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="5a23f-274">跨界 VNet 的规划步骤</span><span class="sxs-lookup"><span data-stu-id="5a23f-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="5a23f-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="5a23f-275"></span></span>

<span data-ttu-id="5a23f-276">请按照以下针对跨界 VNet 的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="5a23f-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="5a23f-277">若要创建一个模拟的跨界开发/测试环境，请参阅 [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="5a23f-278">步骤 1：确定与 VNet（S2S VPN 或 ExpressRoute）的跨界连接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="5a23f-279">表 6 列出了不同类型的连接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="5a23f-280">**连接类型**</span><span class="sxs-lookup"><span data-stu-id="5a23f-280">**Type of connection**</span></span>|<span data-ttu-id="5a23f-281">**用途**</span><span class="sxs-lookup"><span data-stu-id="5a23f-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5a23f-282">站点到站点 (S2S) VPN</span><span class="sxs-lookup"><span data-stu-id="5a23f-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="5a23f-283">连接到单个 VNet 1-10 网站 （包括其他 VNets）。</span><span class="sxs-lookup"><span data-stu-id="5a23f-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="5a23f-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="5a23f-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="5a23f-285">通过 Internet Exchange 提供程序 (IXP) 或网络服务提供商 (NSP) 提供的专用的安全链接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="5a23f-286">点到站点 (P2S) 的 VPN</span><span class="sxs-lookup"><span data-stu-id="5a23f-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="5a23f-287">将一台计算机连接到 VNet。</span><span class="sxs-lookup"><span data-stu-id="5a23f-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="5a23f-288">VNet 对等或 VNet 到 VNet (V2V) VPN </span><span class="sxs-lookup"><span data-stu-id="5a23f-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="5a23f-289">将一个 VNet 连接到另一个 VNet。</span><span class="sxs-lookup"><span data-stu-id="5a23f-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="5a23f-290">**表 6：跨内部 VNet 的连接类型**</span><span class="sxs-lookup"><span data-stu-id="5a23f-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="5a23f-291">最大连接数的详细信息，请参阅[网络限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="5a23f-292">有关 VPN 设备的详细信息，请参阅[站点到站点虚拟网络连接的 VPN 设备](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="5a23f-293">有关对等 VNet 的详细信息，请参阅[VNet 对等](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="5a23f-294">**图 11：连接跨界 VNet 的四种方法**</span><span class="sxs-lookup"><span data-stu-id="5a23f-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![图 11：连接到跨界 Azure 虚拟网络的三种方式](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="5a23f-296">图 11 显示四种类型的连接与 VNet： 从一台计算机的 P2S 连接、 从本地网络 S2S VPN 连接、 从本地网络，ExpressRoute 连接和从另一个 VNet VNet 到 VNet 连接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="5a23f-297">你可以通过以下方式连接到 VNet 中的 VM：</span><span class="sxs-lookup"><span data-stu-id="5a23f-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="5a23f-298">来自本地网络或 Internet 的 VNet VM 管理</span><span class="sxs-lookup"><span data-stu-id="5a23f-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="5a23f-299">来自本地网络的 IT 工作负载访问</span><span class="sxs-lookup"><span data-stu-id="5a23f-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="5a23f-300">通过附加 VNet 的网络扩展</span><span class="sxs-lookup"><span data-stu-id="5a23f-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="5a23f-301">通过以下方式实现连接的安全性：</span><span class="sxs-lookup"><span data-stu-id="5a23f-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="5a23f-302">P2S 使用安全套接字隧道协议 (SSTP) </span><span class="sxs-lookup"><span data-stu-id="5a23f-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="5a23f-303">S2S 和 VNet 到 VNet VPN 连接都通过 AES256 使用 IPsec 隧道模式</span><span class="sxs-lookup"><span data-stu-id="5a23f-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="5a23f-304">ExpressRoute 是专用的 WAN 连接</span><span class="sxs-lookup"><span data-stu-id="5a23f-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="5a23f-305">有关详细信息，请参阅[Microsoft 云安全的企业架构师](https://aka.ms/cloudarchsecurity)和[Azure 网络安全](https://azure.microsoft.com/blog/azure-network-security/)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="5a23f-306">步骤 2：确定本地 VPN 设备或路由器。</span><span class="sxs-lookup"><span data-stu-id="5a23f-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="5a23f-307">本地 VPN 设备或路由器用作：</span><span class="sxs-lookup"><span data-stu-id="5a23f-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="5a23f-308">IPsec 对等方，终止来自 Azure 网关的 S2S VPN 连接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="5a23f-309">专用的对等 ExpressRoute 连接的 BPG 对等和终止点。</span><span class="sxs-lookup"><span data-stu-id="5a23f-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="5a23f-310">**图 12：本地 VPN 路由器或设备**</span><span class="sxs-lookup"><span data-stu-id="5a23f-310">**Figure 12: The on-premises VPN router or device**</span></span>

![图 12：本地 VPN 路由器或设备](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="5a23f-312">图 12 显示连接到本地 VPN 路由器或设备的跨界 VNet。</span><span class="sxs-lookup"><span data-stu-id="5a23f-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="5a23f-313">有关详细信息，请参阅[有关 VPN 网关](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="5a23f-314">步骤 3： 添加对进行 VNet 的地址空间可访问 intranet 路由。</span><span class="sxs-lookup"><span data-stu-id="5a23f-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="5a23f-315">从本地到 VNet 的路由包含以下部分：</span><span class="sxs-lookup"><span data-stu-id="5a23f-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="5a23f-316">指向你的 VPN 设备的 VNet 地址空间的路由。</span><span class="sxs-lookup"><span data-stu-id="5a23f-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="5a23f-317">你的 VPN 设备上的 VNet 地址空间跨 S2S VPN 或 ExpressRoute 连接指向的路由</span><span class="sxs-lookup"><span data-stu-id="5a23f-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="5a23f-318">**图 13：使 VNet 可以访问所需的本地路由**</span><span class="sxs-lookup"><span data-stu-id="5a23f-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![图 13：使 Azure VNet 可以访问所需的本地路由](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="5a23f-320">图 13 显示了本地路由器和 VPN 路由器或设备所需的路由信息，VPN 路由器或设备表示 VNet 的地址空间。</span><span class="sxs-lookup"><span data-stu-id="5a23f-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="5a23f-321">步骤 4：对于 ExpressRoute，计划与你的提供程序的新连接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="5a23f-322">通过以下三种不同的方式，你可以利用本地网络与 Microsoft 云之间的专用对等创建 ExpressRoute 连接：</span><span class="sxs-lookup"><span data-stu-id="5a23f-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="5a23f-323">在云交换中归置</span><span class="sxs-lookup"><span data-stu-id="5a23f-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="5a23f-324">点到点以太网连接</span><span class="sxs-lookup"><span data-stu-id="5a23f-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="5a23f-325">任意对任意 (IP VPN) 的网络</span><span class="sxs-lookup"><span data-stu-id="5a23f-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="5a23f-326">**图 14：使用 ExpressRoute 连接到跨界 VNet**</span><span class="sxs-lookup"><span data-stu-id="5a23f-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![图 14：使用 ExpressRoute 连接到跨界 Azure 虚拟网络](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="5a23f-328">图 14 显示了跨界 VNet 以及从本地路由器到 Microsoft Azure 的 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="5a23f-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="5a23f-329">有关详细信息，请参阅[面向 Microsoft 云连接的 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="5a23f-330">步骤 5：确定 Azure 网关的本地网络地址空间。</span><span class="sxs-lookup"><span data-stu-id="5a23f-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="5a23f-331">对于从 VNet 到本地或其他 VNet 的路由，Azure 通过与分配给它的本地网络地址空间匹配的 Azure 网关转发流量。</span><span class="sxs-lookup"><span data-stu-id="5a23f-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="5a23f-332">**图 15：跨界 VNet 的本地网络地址空间**</span><span class="sxs-lookup"><span data-stu-id="5a23f-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![图 15：跨界 Azure 虚拟网络的本地网络地址空间](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="5a23f-334">图 15 显示跨界 VNet 以及 Azure 网关中的本地网络地址空间，Azure 网关表示本地网络上可访问的地址空间。 </span><span class="sxs-lookup"><span data-stu-id="5a23f-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="5a23f-335">您可以按以下方式定义的本地网络地址空间：</span><span class="sxs-lookup"><span data-stu-id="5a23f-335">You can define the Local Network address space in these ways:</span></span>
  
- <span data-ttu-id="5a23f-336">选项 1：当前所需或正在使用的地址空间的前缀列表（当你添加新的子网时可能需要更新）。</span><span class="sxs-lookup"><span data-stu-id="5a23f-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="5a23f-337">选项 2：你的整个本地地址空间（仅当你添加新的地址空间时需要更新）。</span><span class="sxs-lookup"><span data-stu-id="5a23f-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="5a23f-338">由于 Azure 网关不允许汇总路由，你必须定义选项 2 中的本地网络地址空间，使其不包括 VNet 地址空间。</span><span class="sxs-lookup"><span data-stu-id="5a23f-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="5a23f-339">**图 16：VNet 地址空间创建的地址空间孔**</span><span class="sxs-lookup"><span data-stu-id="5a23f-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![图 16：虚拟网络地址空间创建的地址空间孔](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="5a23f-341">图 16 显示了地址空间的表示形式，其中具有根空间和 VNet 地址空间。</span><span class="sxs-lookup"><span data-stu-id="5a23f-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="5a23f-342">下面是一个示例定义地址空间"孔"由 VNet 周围的本地网络地址空间的前缀：</span><span class="sxs-lookup"><span data-stu-id="5a23f-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="5a23f-p114">组织使用其本地网络中的专用地址空间（10.0.0.0/8、172.16.0.0/12 和 192.168.0.0/16）部分。他们选择选项 2 和 10.100.100.0/24 作为自己的 VNet 地址空间。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="5a23f-345">表 7 显示了定义此示例中的本地网络地址空间的步骤和生成前缀。</span><span class="sxs-lookup"><span data-stu-id="5a23f-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="5a23f-346">**步骤**</span><span class="sxs-lookup"><span data-stu-id="5a23f-346">**Step**</span></span>|<span data-ttu-id="5a23f-347">**结果**</span><span class="sxs-lookup"><span data-stu-id="5a23f-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5a23f-348">1.列出不属于 VNet 地址空间的根空间的前缀。</span><span class="sxs-lookup"><span data-stu-id="5a23f-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="5a23f-349">172.16.0.0/12 和 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="5a23f-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="5a23f-350">2.列出到变量八进制数，但不包括在 VNet 地址空间的最后一个使用的八进制的非重叠的前缀。</span><span class="sxs-lookup"><span data-stu-id="5a23f-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="5a23f-351">10.0.0.0/16、 10.1.0.0/16...10.99.0.0/16、 10.101.0.0/16...10.254.0.0/16，10.255.0.0/16 （255 前缀，跳过 10.100.0.0/16）</span><span class="sxs-lookup"><span data-stu-id="5a23f-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="5a23f-352">3.列表中的最后一个使用八进制 VNet 地址空间的非重叠的前缀。</span><span class="sxs-lookup"><span data-stu-id="5a23f-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="5a23f-353">10.100.0.0/24、 10.100.1.0/24...10.100.99.0/24、 10.100.101.0/24...10.100.254.0/24，10.100.0.255.0/24 （255 前缀，跳过 10.100.100.0/24）</span><span class="sxs-lookup"><span data-stu-id="5a23f-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="5a23f-354">**表 7：示例本地地址网络空间**</span><span class="sxs-lookup"><span data-stu-id="5a23f-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="5a23f-355">步骤 6：通过在 Azure 中托管的 DNS 服务器配置 DNS 复制的本地 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="5a23f-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="5a23f-356">若要确保本地计算机可以解析基于 Azure 的服务器的名称，并且基于 Azure 的服务器可以解析本地计算机的名称，请配置：</span><span class="sxs-lookup"><span data-stu-id="5a23f-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="5a23f-357">你的 VNet 中的 DNS 服务器，以便转发到本地 DNS 服务器</span><span class="sxs-lookup"><span data-stu-id="5a23f-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="5a23f-358">本地和 VNet 中的 DNS 服务器之间相应区域的 DNS 复制</span><span class="sxs-lookup"><span data-stu-id="5a23f-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="5a23f-359">**图 17：跨界 VNet 中的 DNS 服务器的 DNS 复制和转发**</span><span class="sxs-lookup"><span data-stu-id="5a23f-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![图 17：跨界 Azure 虚拟网络中的 DNS 复制和 DNS 服务器转发](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="5a23f-p115">图 17 显示了跨界 VNet，其中 DNS 服务器位于本地网络和 VNet 中的子网中。已在这两个 DNS 服务器之间配置了 DNS 复制和转发。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="5a23f-363">步骤 7：确定使用强制隧道。</span><span class="sxs-lookup"><span data-stu-id="5a23f-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="5a23f-p116">Azure 子网的默认系统路由指向 Internet。若要确保从虚拟机的所有通信都穿越跨界连接，请使用的默认路由的 Azure 网关用作其下一个跃点地址创建路由表。然后，您将在路由表关联与子网。这称为强制隧道。有关详细信息，请参阅[Configure 强制隧道](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p116">The default system route for Azure subnets points to the Internet. To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address. You then associate the route table with the subnet. This is known as forced tunneling. For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="5a23f-369">**图 18：用户定义的路由和跨界 VNet 的强制隧道**</span><span class="sxs-lookup"><span data-stu-id="5a23f-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![图 18：用户定义的路由和跨界 Azure 虚拟网络的强制隧道](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="5a23f-371">图 18 显示跨界 VNet 与子网指向 Azure 网关的用户定义的路由。</span><span class="sxs-lookup"><span data-stu-id="5a23f-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="5a23f-372">Azure 中的 SharePoint Server 2016 场</span><span class="sxs-lookup"><span data-stu-id="5a23f-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="5a23f-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="5a23f-373"></span></span>

<span data-ttu-id="5a23f-374">Intranet Azure IaaS 中承载的 IT 工作负荷的示例是高可用性、 多层 SharePoint Server 2016 服务器场。</span><span class="sxs-lookup"><span data-stu-id="5a23f-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="5a23f-375">**图 19：Azure IaaS 中的高可用性 Intranet SharePoint Server 2016 场**</span><span class="sxs-lookup"><span data-stu-id="5a23f-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS 中具有高可用性的 SharePoint Server 2016 场](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="5a23f-p117">图 19 显示了使用内部负载平衡器的前端和数据层跨界 VNet 中部署 SharePoint Server 2016 服务器场的九个服务器。有关详细信息，包括分步设计和部署的说明，请参阅[Microsoft Azure 中的 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-p117">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers. For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span></span>
  
> [!TIP]
> <span data-ttu-id="5a23f-379">创建模拟的跨界 VNet 在单服务器 2016 SharePoint 服务器场，请参阅[Azure 的开发测试环境中的 Intranet SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span></span> 
  
<span data-ttu-id="5a23f-380">有关其他示例中虚拟跨内部部署 Azure 虚拟机上部署的 IT 工作负荷的网络，请参阅[Azure IaaS 混合云方案](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas)。</span><span class="sxs-lookup"><span data-stu-id="5a23f-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5a23f-381">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a23f-381">See also</span></span>

[<span data-ttu-id="5a23f-382">面向企业架构师的 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="5a23f-382">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="5a23f-383">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="5a23f-383">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


