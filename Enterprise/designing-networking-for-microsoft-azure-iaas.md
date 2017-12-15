---
title: "为 Microsoft Azure IaaS 设计网络"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: "摘要： 了解如何设计用于在 Microsoft Azure IaaS 的工作负载优化的网络。"
ms.openlocfilehash: e4861de51f386af6e142debdafc64f655f010880
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="cc11d-103">为 Microsoft Azure IaaS 设计网络</span><span class="sxs-lookup"><span data-stu-id="cc11d-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="cc11d-104">**摘要：**了解如何设计用于在 Microsoft Azure IaaS 的工作负载优化的网络。</span><span class="sxs-lookup"><span data-stu-id="cc11d-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="cc11d-105">若要优化托管在 Azure IaaS 中的 IT 工作负载的网络，需要了解 Azure 虚拟网络 (VNet)、地址空间、路由、DNS 和负载平衡等相关知识。</span><span class="sxs-lookup"><span data-stu-id="cc11d-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="cc11d-106">任何 VNet 的规划步骤</span><span class="sxs-lookup"><span data-stu-id="cc11d-106">Planning steps for any VNet</span></span>

<span data-ttu-id="cc11d-107">对于任何类型的 VNet，请执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="cc11d-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="cc11d-108">步骤 1：为 Microsoft 云服务准备 Intranet。</span><span class="sxs-lookup"><span data-stu-id="cc11d-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="cc11d-109">经过[公共元素的 Microsoft 云连接](common-elements-of-microsoft-cloud-connectivity.md)中的**步骤来准备您网络上的 Microsoft 云服务**部分。</span><span class="sxs-lookup"><span data-stu-id="cc11d-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="cc11d-110">步骤 2：优化 Internet 带宽。</span><span class="sxs-lookup"><span data-stu-id="cc11d-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="cc11d-111">优化您的互联网带宽使用步骤 2-4 的设计[网络，对于 Microsoft SaaS](designing-networking-for-microsoft-saas.md)的**步骤来准备您的 Microsoft SaaS 服务的网络**部分。</span><span class="sxs-lookup"><span data-stu-id="cc11d-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="cc11d-112">步骤 3：确定 VNet 的类型（仅限云或跨界部署）。</span><span class="sxs-lookup"><span data-stu-id="cc11d-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="cc11d-p101">仅限云 VNet 没有到本地网络的连接。下面是一个示例。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="cc11d-115">**图 1: 仅云 VNet**</span><span class="sxs-lookup"><span data-stu-id="cc11d-115">**Figure 1: A cloud-only VNet**</span></span>

![图 1：Azure 中的云专用虚拟网络](images/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="cc11d-117">图 1 显示了仅限云 VNet 中的一组虚拟机。</span><span class="sxs-lookup"><span data-stu-id="cc11d-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="cc11d-p102">跨界 VNet 具有站点到站点 (S2S) VPN 或通过 Azure 网关实现的到本地网络的 ExpressRoute 连接。下面是一个示例。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="cc11d-120">**图 2： 跨部署 VNet**</span><span class="sxs-lookup"><span data-stu-id="cc11d-120">**Figure 2: A cross-premises VNet**</span></span>

![图 2：Azure 中的跨界虚拟网络](images/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="cc11d-122">图 2 显示了连接到本地网络的跨界 VNet 中的一组虚拟机。</span><span class="sxs-lookup"><span data-stu-id="cc11d-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="cc11d-123">请参阅其他[跨部署 VNet 的规划步骤](designing-networking-for-microsoft-azure-iaas.md#cross_prem)一节。</span><span class="sxs-lookup"><span data-stu-id="cc11d-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="cc11d-124">步骤 4：确定 VNet 的地址空间。</span><span class="sxs-lookup"><span data-stu-id="cc11d-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="cc11d-125">表 1 显示不同 VNet 类型的地址空间。</span><span class="sxs-lookup"><span data-stu-id="cc11d-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="cc11d-126">**VNet 的类型**</span><span class="sxs-lookup"><span data-stu-id="cc11d-126">**Type of VNet**</span></span>|<span data-ttu-id="cc11d-127">**虚拟网络地址空间**</span><span class="sxs-lookup"><span data-stu-id="cc11d-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cc11d-128">仅限云</span><span class="sxs-lookup"><span data-stu-id="cc11d-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="cc11d-129">任意专用地址空间</span><span class="sxs-lookup"><span data-stu-id="cc11d-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="cc11d-130">互连的仅限云类型</span><span class="sxs-lookup"><span data-stu-id="cc11d-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="cc11d-131">任意的私钥，但不是重叠与其他连接 VNets</span><span class="sxs-lookup"><span data-stu-id="cc11d-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="cc11d-132">跨界</span><span class="sxs-lookup"><span data-stu-id="cc11d-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="cc11d-133">专用类型，但不与本地 VNet 重叠</span><span class="sxs-lookup"><span data-stu-id="cc11d-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="cc11d-134">互连的跨界类型</span><span class="sxs-lookup"><span data-stu-id="cc11d-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="cc11d-135">专用类型，但不与本地或其他连接 VNet 重叠</span><span class="sxs-lookup"><span data-stu-id="cc11d-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="cc11d-136">**表 1: VNets 和其对应的地址空间类型**</span><span class="sxs-lookup"><span data-stu-id="cc11d-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="cc11d-137">DHCP 从子网的地址空间中为虚拟机分配地址配置。</span><span class="sxs-lookup"><span data-stu-id="cc11d-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="cc11d-138">地址/子网掩码</span><span class="sxs-lookup"><span data-stu-id="cc11d-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="cc11d-139">默认网关</span><span class="sxs-lookup"><span data-stu-id="cc11d-139">Default gateway</span></span>
    
- <span data-ttu-id="cc11d-140">DNS 服务器 IP 地址</span><span class="sxs-lookup"><span data-stu-id="cc11d-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="cc11d-141">你还可以保留静态的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="cc11d-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="cc11d-142">还可以单独或从包含云服务中为虚拟机分配公用 IP 地址（仅适用于典型的部署计算机）。</span><span class="sxs-lookup"><span data-stu-id="cc11d-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="cc11d-143">步骤 5：确定 VNet 中的子网及分配给每个子网的地址空间。</span><span class="sxs-lookup"><span data-stu-id="cc11d-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="cc11d-144">VNet 中有两种类型的子网：网关子网和虚拟机托管的子网。</span><span class="sxs-lookup"><span data-stu-id="cc11d-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="cc11d-145">**图 3: 两种类型的 Azure 中的子网**</span><span class="sxs-lookup"><span data-stu-id="cc11d-145">**Figure 3: The two types of subnets in Azure**</span></span>

![图 3：Azure 中两种类型的子网](images/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="cc11d-147">图 3 显示了包含网关子网（包含 Azure 网关）和一组虚拟机托管的子网（包含虚拟机）的 VNet。</span><span class="sxs-lookup"><span data-stu-id="cc11d-147">Figure 3 shows a VNet containing a gateway subnet that contains an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="cc11d-p103">Azure 需要 Azure 网关子网来托管 Azure 网关的两个虚拟机。指定前缀长度至少有 29 位的地址空间（例如：192.168.15.248/29）。尤其是在你计划使用 ExpressRoute 时，建议使用 28 位或更短的前缀长度。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p103">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway. Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29). A 28-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="cc11d-151">如下是用来确定 Azure 网关子网的地址空间的最佳实践：</span><span class="sxs-lookup"><span data-stu-id="cc11d-151">A best practice for determining the address space of the Azure gateway subnet is the following:</span></span>
  
1. <span data-ttu-id="cc11d-152">确定网关子网的大小。</span><span class="sxs-lookup"><span data-stu-id="cc11d-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="cc11d-153">在 VNet 地址空间的可变位中，将用于网关子网的位设置为 0，将剩余位设置为 1。</span><span class="sxs-lookup"><span data-stu-id="cc11d-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="cc11d-154">转换为十进制并表示为一个地址空间，其中将前缀长度设置为网关子网的大小。</span><span class="sxs-lookup"><span data-stu-id="cc11d-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="cc11d-155">使用此方法时，网关子网的地址空间始终位于 VNet 地址空间的最远端。</span><span class="sxs-lookup"><span data-stu-id="cc11d-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="cc11d-p104">下面是定义网关子网的地址前缀的一个示例：VNet 的地址空间是 10.119.0.0/16。该组织最初使用站点到站点的 VPN 连接，但最终采用了 ExpressRoute。表 2 显示了确定网络前缀符号（也称为 CIDR）中的网关子网地址前缀的步骤和结果。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="cc11d-159">下面是步骤和确定网关的子网的地址前缀的示例：</span><span class="sxs-lookup"><span data-stu-id="cc11d-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="cc11d-p105">网关网的大小决定。对于我们的示例中，我们选择了 /28。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p105">Decide on the size of the gateway subnet. For our example, we chose /28.</span></span>
2. <span data-ttu-id="cc11d-p106">位在中设置可变部分的 VNet 地址空间 (b) 为 0 的网关子网位 (G) 其他 1 (V)。对于我们的示例中，我们使用 10.119.0.0/16 地址空间为 VNet。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p106">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V). For our example, we are using the 10.119.0.0/16 address space for the VNet. </span></span><br/>
<br/><span data-ttu-id="cc11d-p107">10.119。 bbbbbbbb。bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="cc11d-p107">10.119. bbbbbbbb . bbbbbbbb </span></span><br/><span data-ttu-id="cc11d-p108">10.119。 VVVVVVVV。VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="cc11d-p108">10.119. VVVVVVVV . VVVVGGGG </span></span><br/><span data-ttu-id="cc11d-p109">10.119。 11111111。11110000</span><span class="sxs-lookup"><span data-stu-id="cc11d-p109">10.119. 11111111 . 11110000 </span></span><br/><br/>
3. <span data-ttu-id="cc11d-p110">在步骤 2 中的结果转换为十进制和明确作为地址空间。对于我们的示例中，10.119。11111111。11110000 是 10.119.255.240，并使用步骤 1，（在本示例中为 28 个） 中的前缀长度，得到的网关的子网地址前缀为 10.119.255.240/28。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p110">Convert the result from step 2 to decimal and express as an address space. For our example, 10.119. 11111111 . 11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="cc11d-177">[Azure 的网关的子网的地址空间计算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)的详细信息，请参见</span><span class="sxs-lookup"><span data-stu-id="cc11d-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="cc11d-178">虚拟机托管的子网用来放置 Azure 虚拟机，你可以根据典型的本地指南执行这一任务，例如公共角色、应用程序层或用于子网隔离。</span><span class="sxs-lookup"><span data-stu-id="cc11d-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="cc11d-p111">Azure 使用每个子网的前 3 个地址。因此，可能在 Azure 的子网的地址数为 2<sup>n</sup> -5，其中 n 是主机比特数。表 3 显示的需要，虚拟机的数量范围承载位需要并相应的子网大小。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p111">Azure uses the first 3 addresses on each subnet. Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits. Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="cc11d-182">**所需的虚拟机**</span><span class="sxs-lookup"><span data-stu-id="cc11d-182">**Virtual machines required**</span></span>|<span data-ttu-id="cc11d-183">**主机位**</span><span class="sxs-lookup"><span data-stu-id="cc11d-183">**Host bits**</span></span>|<span data-ttu-id="cc11d-184">**子网大小**</span><span class="sxs-lookup"><span data-stu-id="cc11d-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="cc11d-185">1-3</span><span class="sxs-lookup"><span data-stu-id="cc11d-185">1-3</span></span>  <br/> |<span data-ttu-id="cc11d-186">3</span><span class="sxs-lookup"><span data-stu-id="cc11d-186">3</span></span>  <br/> |<span data-ttu-id="cc11d-187">/29</span><span class="sxs-lookup"><span data-stu-id="cc11d-187">/29</span></span>  <br/> |
|<span data-ttu-id="cc11d-188">4-11</span><span class="sxs-lookup"><span data-stu-id="cc11d-188">4-11</span></span>  <br/> |<span data-ttu-id="cc11d-189">4</span><span class="sxs-lookup"><span data-stu-id="cc11d-189">4</span></span>  <br/> |<span data-ttu-id="cc11d-190">/28</span><span class="sxs-lookup"><span data-stu-id="cc11d-190">/28</span></span>  <br/> |
|<span data-ttu-id="cc11d-191">12-27</span><span class="sxs-lookup"><span data-stu-id="cc11d-191">12-27</span></span>  <br/> |<span data-ttu-id="cc11d-192">5</span><span class="sxs-lookup"><span data-stu-id="cc11d-192">5</span></span>  <br/> |<span data-ttu-id="cc11d-193">/27</span><span class="sxs-lookup"><span data-stu-id="cc11d-193">/27</span></span>  <br/> |
|<span data-ttu-id="cc11d-194">28-59</span><span class="sxs-lookup"><span data-stu-id="cc11d-194">28-59</span></span>  <br/> |<span data-ttu-id="cc11d-195">6</span><span class="sxs-lookup"><span data-stu-id="cc11d-195">6</span></span>  <br/> |<span data-ttu-id="cc11d-196">/26</span><span class="sxs-lookup"><span data-stu-id="cc11d-196">/26</span></span>  <br/> |
|<span data-ttu-id="cc11d-197">60-123</span><span class="sxs-lookup"><span data-stu-id="cc11d-197">60-123</span></span>  <br/> |<span data-ttu-id="cc11d-198">7</span><span class="sxs-lookup"><span data-stu-id="cc11d-198">7</span></span>  <br/> |<span data-ttu-id="cc11d-199">/25</span><span class="sxs-lookup"><span data-stu-id="cc11d-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="cc11d-200">**表 3： 虚拟机要求和它们的子网的大小**</span><span class="sxs-lookup"><span data-stu-id="cc11d-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="cc11d-201">有关子网或 VNet 上最大数量的虚拟机的详细信息，请参阅[网络限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="cc11d-202">有关详细信息，请参阅[规划和设计 Azure 的虚拟网络](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="cc11d-203">步骤 6：确定 VNet 中分配给 VM 的 DNS 服务器配置和DNS 服务器地址。</span><span class="sxs-lookup"><span data-stu-id="cc11d-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="cc11d-p112">Azure 根据 DHCP 为虚拟机分配 DNS 服务器的地址。DNS 服务器可以：</span><span class="sxs-lookup"><span data-stu-id="cc11d-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="cc11d-206">由 Azure 提供：提供本地名称注册及本地和 Internet 名称解析</span><span class="sxs-lookup"><span data-stu-id="cc11d-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="cc11d-207">由你提供：提供本地或 Intranet 名称注册及 Intranet 或 Internet 名称解析</span><span class="sxs-lookup"><span data-stu-id="cc11d-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="cc11d-208">表 4 显示了每种类型的 VNet 不同 DNS 服务器的配置。</span><span class="sxs-lookup"><span data-stu-id="cc11d-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="cc11d-209">**VNet 的类型**</span><span class="sxs-lookup"><span data-stu-id="cc11d-209">**Type of VNet**</span></span>|<span data-ttu-id="cc11d-210">**DNS 服务器**</span><span class="sxs-lookup"><span data-stu-id="cc11d-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cc11d-211">仅限云</span><span class="sxs-lookup"><span data-stu-id="cc11d-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="cc11d-212">由 Azure 提供，用于本地和 Internet 名称解析</span><span class="sxs-lookup"><span data-stu-id="cc11d-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="cc11d-213">Azure 虚拟机，用于本地和 Internet 名称解析（DNS 转发）</span><span class="sxs-lookup"><span data-stu-id="cc11d-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="cc11d-214">跨界</span><span class="sxs-lookup"><span data-stu-id="cc11d-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="cc11d-215">本地，用于本地和 Intranet 名称解析</span><span class="sxs-lookup"><span data-stu-id="cc11d-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="cc11d-216">Azure 虚拟机，用于本地和 Intranet 名称解析（DNS 复制和转发）</span><span class="sxs-lookup"><span data-stu-id="cc11d-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="cc11d-217">**表 4: VNets 的两种不同类型的 DNS 服务器选项**</span><span class="sxs-lookup"><span data-stu-id="cc11d-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="cc11d-218">有关详细信息，请参阅[虚拟机和角色实例的名称解析](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="cc11d-219">步骤 7：确定负载平衡配置（面向 Internet 或内部）。</span><span class="sxs-lookup"><span data-stu-id="cc11d-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="cc11d-p113">在某些情况下，你需要将传入流量分配给具有相同角色的一组服务器。对于面向 Internet 和内部流量负载，Azure IaaS 使用内置设备来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="cc11d-222">Azure 面向 Internet 的负载平衡功能将来自 Internet 的未经请求的传入流量随机分配给负载平衡集的成员。 </span><span class="sxs-lookup"><span data-stu-id="cc11d-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="cc11d-223">**图 4: 外部负载平衡器在 Azure 中**</span><span class="sxs-lookup"><span data-stu-id="cc11d-223">**Figure 4: An external load balancer in Azure**</span></span>

![图 4：Azure 中的外部负载平衡器](images/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="cc11d-225">图 4 显示分配站的 NAT 规则或一组虚拟机的负载平衡集中的终结点上的传入流量的 Azure 中的外部负载平衡器。</span><span class="sxs-lookup"><span data-stu-id="cc11d-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="cc11d-226">Azure 内部负载平衡功能将来自其他 Azure VM 或 Intranet 计算机的未经请求的传入流量随机分配给负载平衡集的成员。 </span><span class="sxs-lookup"><span data-stu-id="cc11d-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="cc11d-227">**图 5: 内部负载平衡器在 Azure 中**</span><span class="sxs-lookup"><span data-stu-id="cc11d-227">**Figure 5: An internal load balancer in Azure**</span></span>

![图 5：Azure 中的内部负载平衡器](images/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="cc11d-229">图 5 显示了在分发站的 NAT 规则或一组虚拟机的负载平衡集中的终结点上的传入通信的 Azure 中的内部负载平衡器。</span><span class="sxs-lookup"><span data-stu-id="cc11d-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="cc11d-230">有关详细信息，请参阅[Azure 负载平衡器](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="cc11d-231">步骤 8：确定使用虚拟设备和用户定义的路由。</span><span class="sxs-lookup"><span data-stu-id="cc11d-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="cc11d-232">如果需要将流量转发到你的 VNet 中的虚拟设备，你可能需要将一个或多个用户定义的路由添加到子网。</span><span class="sxs-lookup"><span data-stu-id="cc11d-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="cc11d-233">**图 6： 即用虚拟装置和用户定义 Azure 中的路由**</span><span class="sxs-lookup"><span data-stu-id="cc11d-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![图 6：Azure 中的虚拟装置和用户定义的路由](images/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="cc11d-235">图 6 显示了分配给虚拟机托管的子网的跨界 VNet 和用户定义的路由，其中子网指向虚拟设备。</span><span class="sxs-lookup"><span data-stu-id="cc11d-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="cc11d-236">有关详细信息，请参阅[用户定义的路由和 IP 转发](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="cc11d-237">步骤 9：确定 Internet 中的计算机如何连接到虚拟机。</span><span class="sxs-lookup"><span data-stu-id="cc11d-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="cc11d-238">有多种方式提供 Internet 访问 VNet 中的虚拟机的权限，这包括通过代理服务器或其他边缘服务从组织网络访问。</span><span class="sxs-lookup"><span data-stu-id="cc11d-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="cc11d-239">表 5 列出了筛选或检查未经请求的传入流量的方法。</span><span class="sxs-lookup"><span data-stu-id="cc11d-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="cc11d-240">**方法**</span><span class="sxs-lookup"><span data-stu-id="cc11d-240">**Method**</span></span>|<span data-ttu-id="cc11d-241">**部署模型**</span><span class="sxs-lookup"><span data-stu-id="cc11d-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cc11d-242">1.在云服务中配置的终结点和 ACL</span><span class="sxs-lookup"><span data-stu-id="cc11d-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="cc11d-243">经典</span><span class="sxs-lookup"><span data-stu-id="cc11d-243">Classic</span></span>  <br/> |
|<span data-ttu-id="cc11d-244">2.网络安全组</span><span class="sxs-lookup"><span data-stu-id="cc11d-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="cc11d-245">Resource Manager 和经典</span><span class="sxs-lookup"><span data-stu-id="cc11d-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="cc11d-246">3.面向 Internet 的负载平衡器，具有入站 NAT 规则</span><span class="sxs-lookup"><span data-stu-id="cc11d-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="cc11d-247">资源经理</span><span class="sxs-lookup"><span data-stu-id="cc11d-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="cc11d-248">4.网络在 Azure 中的安全装置</span><span class="sxs-lookup"><span data-stu-id="cc11d-248">4. Network security appliances in the Azure</span></span> 
 <span data-ttu-id="cc11d-249">市场 （未显示）</span><span class="sxs-lookup"><span data-stu-id="cc11d-249">Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="cc11d-250">Resource Manager 和经典</span><span class="sxs-lookup"><span data-stu-id="cc11d-250">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="cc11d-251">**表 5： 连接到虚拟机和其相应的 Azure 部署模型的方法**</span><span class="sxs-lookup"><span data-stu-id="cc11d-251">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="cc11d-252">**图 7： 通过 Internet 连接到 Azure 的虚拟机**</span><span class="sxs-lookup"><span data-stu-id="cc11d-252">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![图 7：通过 Internet 连接到 Azure 虚拟机](images/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="cc11d-254">图 7 显示已连接到 Internet 的计算机使用终结点连接到云服务中的虚拟机、使用网络安全组连接到子网中的虚拟机，以及使用外部负载平衡器和入站 NAT 规则连接到子网中的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="cc11d-254">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="cc11d-255">其他安全性通过以下项实现：</span><span class="sxs-lookup"><span data-stu-id="cc11d-255">Additional security is provided by:</span></span>
  
- <span data-ttu-id="cc11d-256">已验证并已加密的远程桌面和 SSH 连接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-256">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="cc11d-257">已验证并已加密的远程 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="cc11d-257">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="cc11d-258">可用于端到端加密的 IPsec 传输模式。</span><span class="sxs-lookup"><span data-stu-id="cc11d-258">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="cc11d-259">有助于防止外部和内部攻击的 Azure DDOS 保护</span><span class="sxs-lookup"><span data-stu-id="cc11d-259">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="cc11d-260">有关详细信息，请参阅[Microsoft 企业架构师的云安全](https://aka.ms/cloudarchsecurity)和[Azure 网络安全](https://azure.microsoft.com/blog/azure-network-security/)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-260">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="cc11d-261">步骤 10：为多个 VNet 确定 VNet 到 VNet 连接的拓扑。</span><span class="sxs-lookup"><span data-stu-id="cc11d-261">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="cc11d-262">可以使用类似于用来连接组织站点的拓扑将 VNet 彼此连接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-262">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="cc11d-263">菊花链配置以串联方式连接 VNet。</span><span class="sxs-lookup"><span data-stu-id="cc11d-263">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="cc11d-264">**图 8: 菊花链形式连接配置为 VNets 的**</span><span class="sxs-lookup"><span data-stu-id="cc11d-264">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![图 8：Azure 虚拟网络的菊花链配置](images/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="cc11d-266">图 8 显示了五个连接使用菊花链形式连接的配置在系列中的 VNets。</span><span class="sxs-lookup"><span data-stu-id="cc11d-266">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="cc11d-267">中心辐射型配置将多个 VNet 连接到一组本身已彼此连接的中心 VNet。</span><span class="sxs-lookup"><span data-stu-id="cc11d-267">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="cc11d-268">**图 9: 分散和集中配置 VNets**</span><span class="sxs-lookup"><span data-stu-id="cc11d-268">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![图 9：Azure 虚拟网络的中心辐射型配置](images/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="cc11d-270">图 9 显示六个 VNet，其中两个是彼此相连的中心 VNet，另外各有两个分支 VNet。</span><span class="sxs-lookup"><span data-stu-id="cc11d-270">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="cc11d-271">全网状配置使每个 VNet 相互连接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-271">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="cc11d-272">**图 10： 完全网状配置 VNets**</span><span class="sxs-lookup"><span data-stu-id="cc11d-272">**Figure 10: A full mesh configuration for VNets**</span></span>

![图 10：Azure 虚拟网络的网格配置](images/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="cc11d-274">图 10 显示了四个全都彼此相连的 VNet，共使用六个 VNet 到 VNet 的连接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-274">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="cc11d-275">跨界 VNet 的规划步骤</span><span class="sxs-lookup"><span data-stu-id="cc11d-275">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="cc11d-276"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="cc11d-276"></span></span>

<span data-ttu-id="cc11d-277">请按照以下针对跨界 VNet 的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="cc11d-277">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="cc11d-278">若要创建一个模拟的跨内部开发/测试环境，请参阅[Simulated 跨内部 Azure 中的虚拟网络](simulated-cross-premises-virtual-network-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-278">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="cc11d-279">步骤 1：确定与 VNet（S2S VPN 或 ExpressRoute）的跨界连接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-279">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="cc11d-280">表 6 列出了不同类型的连接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-280">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="cc11d-281">**连接类型**</span><span class="sxs-lookup"><span data-stu-id="cc11d-281">**Type of connection**</span></span>|<span data-ttu-id="cc11d-282">**用途**</span><span class="sxs-lookup"><span data-stu-id="cc11d-282">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cc11d-283">站点到站点 (S2S) VPN</span><span class="sxs-lookup"><span data-stu-id="cc11d-283">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="cc11d-284">连接到一个 VNet 的 1-10 站点 （包括其他 VNets）。</span><span class="sxs-lookup"><span data-stu-id="cc11d-284">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="cc11d-285">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="cc11d-285">ExpressRoute</span></span>  <br/> |<span data-ttu-id="cc11d-286">通过 Internet Exchange 提供程序 (IXP) 或网络服务提供商 (NSP) 提供的专用的安全链接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-286">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="cc11d-287">点到站点 (P2S) 的 VPN</span><span class="sxs-lookup"><span data-stu-id="cc11d-287">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="cc11d-288">将一台计算机连接到 VNet。</span><span class="sxs-lookup"><span data-stu-id="cc11d-288">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="cc11d-289">VNet 对等或 VNet 到 VNet (V2V) VPN </span><span class="sxs-lookup"><span data-stu-id="cc11d-289">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="cc11d-290">将一个 VNet 连接到另一个 VNet。</span><span class="sxs-lookup"><span data-stu-id="cc11d-290">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="cc11d-291">**表 6： 跨部署 VNets 的连接的类型**</span><span class="sxs-lookup"><span data-stu-id="cc11d-291">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="cc11d-292">最大连接数的详细信息，请参阅[网络限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-292">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="cc11d-293">VPN 设备的详细信息，请参阅[VPN 站点到站点虚拟网络连接的设备](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-293">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="cc11d-294">VNet 对等有关的详细信息，请参阅[VNet 对等](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-294">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="cc11d-295">**图 11: 四种方法连接到跨部署 VNet**</span><span class="sxs-lookup"><span data-stu-id="cc11d-295">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![图 11：连接到跨界 Azure 虚拟网络的三种方式](images/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="cc11d-297">图 11 显示的四种类型的连接与 VNet: P2S 连接从计算机、 从内部网络 S2S VPN 连接，从内部网络，连接到 ExpressRoute 和来自另一个 VNet 的 VNet 到 VNet 连接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-297">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="cc11d-298">你可以通过以下方式连接到 VNet 中的 VM：</span><span class="sxs-lookup"><span data-stu-id="cc11d-298">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="cc11d-299">来自本地网络或 Internet 的 VNet VM 管理</span><span class="sxs-lookup"><span data-stu-id="cc11d-299">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="cc11d-300">来自本地网络的 IT 工作负载访问</span><span class="sxs-lookup"><span data-stu-id="cc11d-300">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="cc11d-301">通过附加 VNet 的网络扩展</span><span class="sxs-lookup"><span data-stu-id="cc11d-301">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="cc11d-302">通过以下方式实现连接的安全性：</span><span class="sxs-lookup"><span data-stu-id="cc11d-302">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="cc11d-303">P2S 使用安全套接字隧道协议 (SSTP) </span><span class="sxs-lookup"><span data-stu-id="cc11d-303">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="cc11d-304">S2S 和 VNet 到 VNet VPN 连接都通过 AES256 使用 IPsec 隧道模式</span><span class="sxs-lookup"><span data-stu-id="cc11d-304">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="cc11d-305">ExpressRoute 是专用的 WAN 连接</span><span class="sxs-lookup"><span data-stu-id="cc11d-305">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="cc11d-306">有关详细信息，请参阅[Microsoft 企业架构师的云安全](https://aka.ms/cloudarchsecurity)和[Azure 网络安全](https://azure.microsoft.com/blog/azure-network-security/)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-306">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="cc11d-307">步骤 2：确定本地 VPN 设备或路由器。</span><span class="sxs-lookup"><span data-stu-id="cc11d-307">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="cc11d-308">本地 VPN 设备或路由器用作：</span><span class="sxs-lookup"><span data-stu-id="cc11d-308">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="cc11d-309">IPsec 对等方，终止来自 Azure 网关的 S2S VPN 连接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-309">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="cc11d-310">专用的对等 ExpressRoute 连接的 BPG 对等和终止点。</span><span class="sxs-lookup"><span data-stu-id="cc11d-310">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="cc11d-311">**图 12： 内部部署 VPN 路由器或设备**</span><span class="sxs-lookup"><span data-stu-id="cc11d-311">**Figure 12: The on-premises VPN router or device**</span></span>

![图 12：本地 VPN 路由器或设备](images/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="cc11d-313">图 12 显示连接到本地 VPN 路由器或设备的跨界 VNet。</span><span class="sxs-lookup"><span data-stu-id="cc11d-313">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="cc11d-314">有关详细信息，请参阅[关于 VPN 网关](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-314">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="cc11d-315">步骤 3： 将路由添加到 intranet 进行 VNet 的地址空间可到达。</span><span class="sxs-lookup"><span data-stu-id="cc11d-315">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="cc11d-316">从本地到 VNet 的路由包含以下部分：</span><span class="sxs-lookup"><span data-stu-id="cc11d-316">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="cc11d-317">指向你的 VPN 设备的 VNet 地址空间的路由。</span><span class="sxs-lookup"><span data-stu-id="cc11d-317">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="cc11d-318">你的 VPN 设备上的 VNet 地址空间跨 S2S VPN 或 ExpressRoute 连接指向的路由</span><span class="sxs-lookup"><span data-stu-id="cc11d-318">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="cc11d-319">**图 13： 内部路由需要进行 VNet 可以到达**</span><span class="sxs-lookup"><span data-stu-id="cc11d-319">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![图 13：使 Azure VNet 可以访问所需的本地路由](images/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="cc11d-321">图 13 显示了本地路由器和 VPN 路由器或设备所需的路由信息，VPN 路由器或设备表示 VNet 的地址空间。</span><span class="sxs-lookup"><span data-stu-id="cc11d-321">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="cc11d-322">步骤 4：对于 ExpressRoute，计划与你的提供程序的新连接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-322">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="cc11d-323">通过以下三种不同的方式，你可以利用本地网络与 Microsoft 云之间的专用对等创建 ExpressRoute 连接：</span><span class="sxs-lookup"><span data-stu-id="cc11d-323">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="cc11d-324">在云交换中归置</span><span class="sxs-lookup"><span data-stu-id="cc11d-324">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="cc11d-325">点到点以太网连接</span><span class="sxs-lookup"><span data-stu-id="cc11d-325">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="cc11d-326">任意对任意 (IP VPN) 的网络</span><span class="sxs-lookup"><span data-stu-id="cc11d-326">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="cc11d-327">**图 14： 使用 ExpressRoute 连接到跨部署 VNet**</span><span class="sxs-lookup"><span data-stu-id="cc11d-327">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![图 14：使用 ExpressRoute 连接到跨界 Azure 虚拟网络](images/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="cc11d-329">图 14 显示了跨界 VNet 以及从本地路由器到 Microsoft Azure 的 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="cc11d-329">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="cc11d-330">有关详细信息，请参阅[面向 Microsoft 云连接的 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-330">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="cc11d-331">步骤 5：确定 Azure 网关的本地网络地址空间。</span><span class="sxs-lookup"><span data-stu-id="cc11d-331">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="cc11d-332">对于从 VNet 到本地或其他 VNet 的路由，Azure 通过与分配给它的本地网络地址空间匹配的 Azure 网关转发流量。</span><span class="sxs-lookup"><span data-stu-id="cc11d-332">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="cc11d-333">**图 15: 本地网络的地址空间跨部署 VNet**</span><span class="sxs-lookup"><span data-stu-id="cc11d-333">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![图 15：跨界 Azure 虚拟网络的本地网络地址空间](images/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="cc11d-335">图 15 显示跨界 VNet 以及 Azure 网关中的本地网络地址空间，Azure 网关表示本地网络上可访问的地址空间。 </span><span class="sxs-lookup"><span data-stu-id="cc11d-335">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="cc11d-336">你可以按以下方式定义本地网络地址空间：</span><span class="sxs-lookup"><span data-stu-id="cc11d-336">You can define the Local Network address space in the following ways:</span></span>
  
- <span data-ttu-id="cc11d-337">选项 1：当前所需或正在使用的地址空间的前缀列表（当你添加新的子网时可能需要更新）。</span><span class="sxs-lookup"><span data-stu-id="cc11d-337">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="cc11d-338">选项 2：你的整个本地地址空间（仅当你添加新的地址空间时需要更新）。</span><span class="sxs-lookup"><span data-stu-id="cc11d-338">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="cc11d-339">由于 Azure 网关不允许汇总路由，你必须定义选项 2 中的本地网络地址空间，使其不包括 VNet 地址空间。</span><span class="sxs-lookup"><span data-stu-id="cc11d-339">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="cc11d-340">**图 16: 地址空间孔创建的 VNet 地址空间**</span><span class="sxs-lookup"><span data-stu-id="cc11d-340">**Figure 16: The address space hole created by the VNet address space**</span></span>

![图 16：虚拟网络地址空间创建的地址空间孔](images/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="cc11d-342">图 16 显示了地址空间的表示形式，其中具有根空间和 VNet 地址空间。</span><span class="sxs-lookup"><span data-stu-id="cc11d-342">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="cc11d-343">下面是定义前缀为"洞"，由 VNet 创建的地址空间周围的本地网络地址空间的一个示例：</span><span class="sxs-lookup"><span data-stu-id="cc11d-343">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="cc11d-p114">组织使用其本地网络中的专用地址空间（10.0.0.0/8、172.16.0.0/12 和 192.168.0.0/16）部分。他们选择选项 2 和 10.100.100.0/24 作为自己的 VNet 地址空间。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="cc11d-346">表 7 显示了定义此示例中的本地网络地址空间的步骤和生成前缀。</span><span class="sxs-lookup"><span data-stu-id="cc11d-346">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="cc11d-347">**步骤**</span><span class="sxs-lookup"><span data-stu-id="cc11d-347">**Step**</span></span>|<span data-ttu-id="cc11d-348">**结果**</span><span class="sxs-lookup"><span data-stu-id="cc11d-348">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cc11d-349">1.列出不属于 VNet 地址空间的根空间的前缀。</span><span class="sxs-lookup"><span data-stu-id="cc11d-349">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="cc11d-350">172.16.0.0/12 和 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="cc11d-350">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="cc11d-351">2.达列表变量的八位字节的非重叠前缀，但不是包括最后一次使用</span><span class="sxs-lookup"><span data-stu-id="cc11d-351">2. List the non-overlapping prefixes for variable octets up to but not including the last used</span></span> 
 <span data-ttu-id="cc11d-352">八位字节的 VNet 地址空间中。</span><span class="sxs-lookup"><span data-stu-id="cc11d-352">octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="cc11d-353">10.0.0.0/16、 10.1.0.0/16...10.99.0.0/16、 10.101.0.0/16...10.254.0.0/16，10.255.0.0/16 （255 前缀，跳过 10.100.0.0/16）</span><span class="sxs-lookup"><span data-stu-id="cc11d-353">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="cc11d-354">3.在非重叠前缀的列表</span><span class="sxs-lookup"><span data-stu-id="cc11d-354">3. List the non-overlapping prefixes within the</span></span> 
 <span data-ttu-id="cc11d-355">最后一次使用 VNet 地址空间的八位位组。</span><span class="sxs-lookup"><span data-stu-id="cc11d-355">last used octet of the VNet address space.</span></span>  <br/> <span data-ttu-id="cc11d-356">| 10.100.0.0/24、 10.100.1.0/24...10.100.99.0/24、 10.100.101.0/24...10.100.254.0/24，10.100.0.255.0/24 （255 前缀，跳过 10.100.100.0/24）</span><span class="sxs-lookup"><span data-stu-id="cc11d-356">|10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="cc11d-357">**表 7： 示例本地地址的网络空间**</span><span class="sxs-lookup"><span data-stu-id="cc11d-357">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="cc11d-358">步骤 6：通过在 Azure 中托管的 DNS 服务器配置 DNS 复制的本地 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="cc11d-358">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="cc11d-359">若要确保本地计算机可以解析基于 Azure 的服务器的名称，并且基于 Azure 的服务器可以解析本地计算机的名称，请配置：</span><span class="sxs-lookup"><span data-stu-id="cc11d-359">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="cc11d-360">你的 VNet 中的 DNS 服务器，以便转发到本地 DNS 服务器</span><span class="sxs-lookup"><span data-stu-id="cc11d-360">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="cc11d-361">本地和 VNet 中的 DNS 服务器之间相应区域的 DNS 复制</span><span class="sxs-lookup"><span data-stu-id="cc11d-361">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="cc11d-362">**图 17: DNS 复制和跨部署 VNet 中的 DNS 服务器的转发**</span><span class="sxs-lookup"><span data-stu-id="cc11d-362">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![图 17：跨界 Azure 虚拟网络中的 DNS 复制和 DNS 服务器转发](images/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="cc11d-p115">图 17 显示了跨界 VNet，其中 DNS 服务器位于本地网络和 VNet 中的子网中。已在这两个 DNS 服务器之间配置了 DNS 复制和转发。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="cc11d-366">步骤 7：确定使用强制隧道。</span><span class="sxs-lookup"><span data-stu-id="cc11d-366">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="cc11d-p116">Azure 的子网的默认系统路由指向 Internet。为了确保虚拟机的所有通信都穿越跨内部连接，创建作为其下一中继站地址使用 Azure 的网关的默认路由的路由表。然后将路由表与子网关联。这被称作为强制隧道。有关详细信息，请参阅[配置强制隧道](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p116">The default system route for Azure subnets points to the Internet. To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address. You then associate the route table with the subnet. This is known as forced tunneling. For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="cc11d-372">**图 18： 用户定义工艺路线和跨部署 VNet 的强制隧道**</span><span class="sxs-lookup"><span data-stu-id="cc11d-372">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![图 18：用户定义的路由和跨界 Azure 虚拟网络的强制隧道](images/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="cc11d-374">图 18 显示跨部署 VNet 用户定义指向 Azure 的网关的子网路由。</span><span class="sxs-lookup"><span data-stu-id="cc11d-374">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="cc11d-375">Azure 中的 SharePoint Server 2016 场</span><span class="sxs-lookup"><span data-stu-id="cc11d-375">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="cc11d-376"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="cc11d-376"></span></span>

<span data-ttu-id="cc11d-377">Azure IaaS 中托管 Intranet IT 工作负荷的一个示例就是高可用性、多层 SharePoint Server 2016 场，如图 19 中所示。</span><span class="sxs-lookup"><span data-stu-id="cc11d-377">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm, as shown in Figure 19.</span></span>
  
<span data-ttu-id="cc11d-378">**图 19: Azure IaaS 在一个高度可用的内联网 SharePoint 服务器 2016年场**</span><span class="sxs-lookup"><span data-stu-id="cc11d-378">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS 中具有高可用性的 SharePoint Server 2016 场](images/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="cc11d-p117">图 19 显示了部署在内部负载平衡器用于前端和数据层跨部署 VNet 的 SharePoint 服务器 2016年场的九个服务器。有关详细信息，包括分步设计和部署的说明，请参阅[Microsoft Azure 中的 SharePoint 服务器 2016年](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-p117">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers. For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span></span>
  
> [!TIP]
> <span data-ttu-id="cc11d-382">在模拟的跨本地 VNet 中创建单服务器 SharePoint 服务器 2016年场，看到[Intranet SharePoint 服务器 2016 Azure 开发/测试环境中](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-382">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span> 
  
<span data-ttu-id="cc11d-383">有关其他示例部署虚拟跨场所 Azure 中的虚拟机上的 IT 工作负荷的网络，请参阅[混合 Azure IaaS 云方案](https://technet.microsoft.com/library/mt750502.aspx)。</span><span class="sxs-lookup"><span data-stu-id="cc11d-383">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cc11d-384">See Also</span><span class="sxs-lookup"><span data-stu-id="cc11d-384">See Also</span></span>

<span data-ttu-id="cc11d-385"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="cc11d-385"></span></span>

[<span data-ttu-id="cc11d-386">面向企业架构师的 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="cc11d-386">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="cc11d-387">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="cc11d-387">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="cc11d-388">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="cc11d-388">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



