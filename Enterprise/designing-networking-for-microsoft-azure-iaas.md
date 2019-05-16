---
title: 为 Microsoft Azure IaaS 设计网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: '摘要: 了解如何在 Microsoft Azure IaaS 中设计工作负荷的优化网络。'
ms.openlocfilehash: b06564c8a86c59dac4ac9a5380cd88cf9d045974
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068128"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="e2258-103">为 Microsoft Azure IaaS 设计网络</span><span class="sxs-lookup"><span data-stu-id="e2258-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="e2258-104">**摘要:** 了解如何在 Microsoft Azure IaaS 中设计工作负荷的优化网络。</span><span class="sxs-lookup"><span data-stu-id="e2258-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="e2258-105">若要优化 Azure IaaS 中承载的 IT 工作负载的网络, 需要了解 Azure 虚拟网络 (Vnet)、地址空间、路由、DNS 和负载平衡。</span><span class="sxs-lookup"><span data-stu-id="e2258-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="e2258-106">针对任何 VNet 的规划步骤</span><span class="sxs-lookup"><span data-stu-id="e2258-106">Planning steps for any VNet</span></span>

<span data-ttu-id="e2258-107">对任何类型的 VNet 执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="e2258-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="e2258-108">步骤 1: 为 Microsoft 云服务准备 intranet。</span><span class="sxs-lookup"><span data-stu-id="e2258-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="e2258-109">完成 [Microsoft 云连接的常见元素](common-elements-of-microsoft-cloud-connectivity.md)中的**为 Microsoft 云服务准备网络的步骤**部分。</span><span class="sxs-lookup"><span data-stu-id="e2258-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="e2258-110">步骤 2: 优化 Internet 带宽。</span><span class="sxs-lookup"><span data-stu-id="e2258-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="e2258-111">按照[设计 Microsoft SaaS 网络](designing-networking-for-microsoft-saas.md)中的**为 Microsoft SaaS 服务准备网络的步骤**部分的第 2-4 步操作，优化 Internet 带宽。</span><span class="sxs-lookup"><span data-stu-id="e2258-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="e2258-112">步骤 3: 确定 VNet 的类型 (仅限云或跨界部署)。</span><span class="sxs-lookup"><span data-stu-id="e2258-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="e2258-113">仅限云的 VNet 与本地网络无连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-113">A cloud-only VNet has no connection to an on-premises network.</span></span> <span data-ttu-id="e2258-114">例如：</span><span class="sxs-lookup"><span data-stu-id="e2258-114">Here is an example.</span></span>
  
<span data-ttu-id="e2258-115">**图 1: 仅限云的 VNet**</span><span class="sxs-lookup"><span data-stu-id="e2258-115">**Figure 1: A cloud-only VNet**</span></span>

![图 1: Azure 中的仅限云的虚拟网络](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="e2258-117">图1显示了仅限云 VNet 中的一组虚拟机。</span><span class="sxs-lookup"><span data-stu-id="e2258-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="e2258-118">跨界 VNet 具有通过 Azure 网关与本地网络的站点到站点 (S2S) VPN 或 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-118">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway.</span></span> <span data-ttu-id="e2258-119">例如：</span><span class="sxs-lookup"><span data-stu-id="e2258-119">Here is an example.</span></span>
  
<span data-ttu-id="e2258-120">**图 2: 跨界 VNet**</span><span class="sxs-lookup"><span data-stu-id="e2258-120">**Figure 2: A cross-premises VNet**</span></span>

![图 2: Azure 中的跨界虚拟网络](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="e2258-122">图2显示了跨界 VNet 中连接到本地网络的一组虚拟机。</span><span class="sxs-lookup"><span data-stu-id="e2258-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="e2258-123">请参阅本文中[有关跨界 VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem)部分的其他规划步骤。</span><span class="sxs-lookup"><span data-stu-id="e2258-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="e2258-124">步骤 4: 确定 VNet 的地址空间。</span><span class="sxs-lookup"><span data-stu-id="e2258-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="e2258-125">表1显示了不同类型的 Vnet 的地址空间。</span><span class="sxs-lookup"><span data-stu-id="e2258-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="e2258-126">**VNet 类型**</span><span class="sxs-lookup"><span data-stu-id="e2258-126">**Type of VNet**</span></span>|<span data-ttu-id="e2258-127">**虚拟网络地址空间**</span><span class="sxs-lookup"><span data-stu-id="e2258-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e2258-128">仅限云</span><span class="sxs-lookup"><span data-stu-id="e2258-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="e2258-129">任意专用地址空间</span><span class="sxs-lookup"><span data-stu-id="e2258-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="e2258-130">互连仅限云</span><span class="sxs-lookup"><span data-stu-id="e2258-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="e2258-131">任意专用, 但不与其他连接的 Vnet 重叠</span><span class="sxs-lookup"><span data-stu-id="e2258-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="e2258-132">跨界</span><span class="sxs-lookup"><span data-stu-id="e2258-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="e2258-133">专用, 但不与内部部署重叠</span><span class="sxs-lookup"><span data-stu-id="e2258-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="e2258-134">相互连接的跨界</span><span class="sxs-lookup"><span data-stu-id="e2258-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="e2258-135">专用, 但不与内部部署和其他连接的 Vnet 重叠</span><span class="sxs-lookup"><span data-stu-id="e2258-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="e2258-136">**表 1: Vnet 的类型及其相应的地址空间**</span><span class="sxs-lookup"><span data-stu-id="e2258-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="e2258-137">从子网的地址空间为虚拟机分配地址配置的方式为 DHCP:</span><span class="sxs-lookup"><span data-stu-id="e2258-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="e2258-138">地址/子网掩码</span><span class="sxs-lookup"><span data-stu-id="e2258-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="e2258-139">默认网关</span><span class="sxs-lookup"><span data-stu-id="e2258-139">Default gateway</span></span>
    
- <span data-ttu-id="e2258-140">DNS 服务器 IP 地址</span><span class="sxs-lookup"><span data-stu-id="e2258-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="e2258-141">您还可以保留静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e2258-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="e2258-142">也可以单独或从包含云服务 (仅针对经典部署计算机) 为虚拟机分配公共 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e2258-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="e2258-143">步骤 5: 确定 VNet 中的子网和分配给每个的地址空间。</span><span class="sxs-lookup"><span data-stu-id="e2258-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="e2258-144">VNet 中有两种类型的子网, 即网关子网和虚拟机托管子网。</span><span class="sxs-lookup"><span data-stu-id="e2258-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="e2258-145">**图 3: Azure 中的两种类型的子网**</span><span class="sxs-lookup"><span data-stu-id="e2258-145">**Figure 3: The two types of subnets in Azure**</span></span>

![图 3: Azure 中的两种类型的子网](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="e2258-147">图3显示了包含具有 Azure 网关的网关子网和一组包含虚拟机的虚拟机托管子网的 VNet。</span><span class="sxs-lookup"><span data-stu-id="e2258-147">Figure 3 shows a VNet containing a gateway subnet that has an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="e2258-148">Azure 需要 azure 网关子网, 以托管 Azure 网关的两台虚拟机。</span><span class="sxs-lookup"><span data-stu-id="e2258-148">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway.</span></span> <span data-ttu-id="e2258-149">指定至少具有29位前缀长度的地址空间 (示例: 192.168.15.248/29)。</span><span class="sxs-lookup"><span data-stu-id="e2258-149">Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29).</span></span> <span data-ttu-id="e2258-150">建议使用27位或更小的前缀长度, 尤其是在计划使用 ExpressRoute 时。</span><span class="sxs-lookup"><span data-stu-id="e2258-150">A 27-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="e2258-151">确定 Azure 网关子网的地址空间的最佳做法是:</span><span class="sxs-lookup"><span data-stu-id="e2258-151">A best practice for determining the address space of the Azure gateway subnet is:</span></span>
  
1. <span data-ttu-id="e2258-152">确定网关子网的大小。</span><span class="sxs-lookup"><span data-stu-id="e2258-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="e2258-153">在 VNet 的地址空间中的可变位中, 将用于网关子网的位设置为 0, 并将其余的位设置为1。</span><span class="sxs-lookup"><span data-stu-id="e2258-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="e2258-154">转换为十进制并表示为一个地址空间, 其前缀长度设置为网关子网的大小。</span><span class="sxs-lookup"><span data-stu-id="e2258-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="e2258-155">使用此方法时, 网关子网的地址空间始终处于 VNet 地址空间的最远的一端。</span><span class="sxs-lookup"><span data-stu-id="e2258-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="e2258-156">下面的示例展示了如何定义网关子网的地址前缀: VNet 的地址空间为 10.119.0.0/16。</span><span class="sxs-lookup"><span data-stu-id="e2258-156">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16.</span></span> <span data-ttu-id="e2258-157">组织最初将使用站点到站点 VPN 连接, 但最终会获得 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="e2258-157">The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute.</span></span> <span data-ttu-id="e2258-158">表2显示了确定网络前缀表示法 (也称为 CIDR) 中的网关子网地址前缀的步骤和结果。</span><span class="sxs-lookup"><span data-stu-id="e2258-158">Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="e2258-159">以下是确定网关子网地址前缀的步骤和示例:</span><span class="sxs-lookup"><span data-stu-id="e2258-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="e2258-160">确定网关子网的大小。</span><span class="sxs-lookup"><span data-stu-id="e2258-160">Decide on the size of the gateway subnet.</span></span> <span data-ttu-id="e2258-161">在我们的示例中, 我们选择/28。</span><span class="sxs-lookup"><span data-stu-id="e2258-161">For our example, we chose /28.</span></span>
2. <span data-ttu-id="e2258-162">为网关子网位 (G) 将 VNet 地址空间 (b) 的变量部分中的位设置为 0, 否则为 1 (V)。</span><span class="sxs-lookup"><span data-stu-id="e2258-162">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V).</span></span> <span data-ttu-id="e2258-163">对于我们的示例, 我们使用的是 VNet 的 10.119.0.0/16 地址空间。</span><span class="sxs-lookup"><span data-stu-id="e2258-163">For our example, we are using the 10.119.0.0/16 address space for the VNet.</span></span>
<br/>
<br/><span data-ttu-id="e2258-164">10.119。</span><span class="sxs-lookup"><span data-stu-id="e2258-164">10.119.</span></span> <span data-ttu-id="e2258-165">bbbbbbbb .</span><span class="sxs-lookup"><span data-stu-id="e2258-165">bbbbbbbb .</span></span> <span data-ttu-id="e2258-166">bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="e2258-166">bbbbbbbb</span></span>
<br/><span data-ttu-id="e2258-167">10.119。</span><span class="sxs-lookup"><span data-stu-id="e2258-167">10.119.</span></span> <span data-ttu-id="e2258-168">VVVVVVVV .</span><span class="sxs-lookup"><span data-stu-id="e2258-168">VVVVVVVV .</span></span> <span data-ttu-id="e2258-169">VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="e2258-169">VVVVGGGG</span></span>
<br/><span data-ttu-id="e2258-170">10.119。</span><span class="sxs-lookup"><span data-stu-id="e2258-170">10.119.</span></span> <span data-ttu-id="e2258-171">11111111。</span><span class="sxs-lookup"><span data-stu-id="e2258-171">11111111 .</span></span> <span data-ttu-id="e2258-172">11110000</span><span class="sxs-lookup"><span data-stu-id="e2258-172">11110000</span></span>
<br/><br/>
3. <span data-ttu-id="e2258-173">将步骤2中的结果转换为 "小数", 并将其表示为地址空间。</span><span class="sxs-lookup"><span data-stu-id="e2258-173">Convert the result from step 2 to decimal and express as an address space.</span></span> <span data-ttu-id="e2258-174">对于我们的示例, 为10.119。</span><span class="sxs-lookup"><span data-stu-id="e2258-174">For our example, 10.119.</span></span> <span data-ttu-id="e2258-175">11111111。</span><span class="sxs-lookup"><span data-stu-id="e2258-175">11111111 .</span></span> <span data-ttu-id="e2258-176">11110000为 10.119.255.240, 并使用步骤1中的前缀长度 (在示例中为 28), 生成的网关子网地址前缀是 10.119.255.240/28。</span><span class="sxs-lookup"><span data-stu-id="e2258-176">11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="e2258-177">有关详细信息, 请参阅[Azure 网关子网的地址空间计算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。</span><span class="sxs-lookup"><span data-stu-id="e2258-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="e2258-178">虚拟机托管的子网是放置 Azure 虚拟机的地方, 可以根据典型的本地指导方针 (如应用程序的通用角色或应用程序或子网隔离) 执行此操作。</span><span class="sxs-lookup"><span data-stu-id="e2258-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="e2258-179">Azure 使用每个子网上的前3个地址。</span><span class="sxs-lookup"><span data-stu-id="e2258-179">Azure uses the first 3 addresses on each subnet.</span></span> <span data-ttu-id="e2258-180">因此, Azure 子网上的可能地址数是 2<sup>n</sup> -5, 其中 n 是主机位的数量。</span><span class="sxs-lookup"><span data-stu-id="e2258-180">Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits.</span></span> <span data-ttu-id="e2258-181">表3显示了所需的虚拟机范围、所需的主机位数以及相应的子网大小。</span><span class="sxs-lookup"><span data-stu-id="e2258-181">Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="e2258-182">**需要虚拟机**</span><span class="sxs-lookup"><span data-stu-id="e2258-182">**Virtual machines required**</span></span>|<span data-ttu-id="e2258-183">**主机位**</span><span class="sxs-lookup"><span data-stu-id="e2258-183">**Host bits**</span></span>|<span data-ttu-id="e2258-184">**子网大小**</span><span class="sxs-lookup"><span data-stu-id="e2258-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="e2258-185">1-3</span><span class="sxs-lookup"><span data-stu-id="e2258-185">1-3</span></span>  <br/> |<span data-ttu-id="e2258-186">第三章</span><span class="sxs-lookup"><span data-stu-id="e2258-186">3</span></span>  <br/> |<span data-ttu-id="e2258-187">/29</span><span class="sxs-lookup"><span data-stu-id="e2258-187">/29</span></span>  <br/> |
|<span data-ttu-id="e2258-188">4-11</span><span class="sxs-lookup"><span data-stu-id="e2258-188">4-11</span></span>  <br/> |<span data-ttu-id="e2258-189">4</span><span class="sxs-lookup"><span data-stu-id="e2258-189">4</span></span>  <br/> |<span data-ttu-id="e2258-190">/28</span><span class="sxs-lookup"><span data-stu-id="e2258-190">/28</span></span>  <br/> |
|<span data-ttu-id="e2258-191">12-27</span><span class="sxs-lookup"><span data-stu-id="e2258-191">12-27</span></span>  <br/> |<span data-ttu-id="e2258-192">5</span><span class="sxs-lookup"><span data-stu-id="e2258-192">5</span></span>  <br/> |<span data-ttu-id="e2258-193">/27</span><span class="sxs-lookup"><span data-stu-id="e2258-193">/27</span></span>  <br/> |
|<span data-ttu-id="e2258-194">28-59</span><span class="sxs-lookup"><span data-stu-id="e2258-194">28-59</span></span>  <br/> |<span data-ttu-id="e2258-195">型</span><span class="sxs-lookup"><span data-stu-id="e2258-195">6</span></span>  <br/> |<span data-ttu-id="e2258-196">/26</span><span class="sxs-lookup"><span data-stu-id="e2258-196">/26</span></span>  <br/> |
|<span data-ttu-id="e2258-197">60-123</span><span class="sxs-lookup"><span data-stu-id="e2258-197">60-123</span></span>  <br/> |<span data-ttu-id="e2258-198">步</span><span class="sxs-lookup"><span data-stu-id="e2258-198">7</span></span>  <br/> |<span data-ttu-id="e2258-199">/25</span><span class="sxs-lookup"><span data-stu-id="e2258-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="e2258-200">**表 3: 虚拟机要求及其子网大小**</span><span class="sxs-lookup"><span data-stu-id="e2258-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="e2258-201">有关子网或 VNet 上的最大虚拟机数量的详细信息, 请参阅[网络限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。</span><span class="sxs-lookup"><span data-stu-id="e2258-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="e2258-202">有关详细信息, 请参阅[规划和设计 Azure 虚拟网络](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)。</span><span class="sxs-lookup"><span data-stu-id="e2258-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="e2258-203">步骤 6: 确定要分配给 VNet 中的 Vm 的 DNS 服务器配置和 DNS 服务器的地址。</span><span class="sxs-lookup"><span data-stu-id="e2258-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="e2258-204">Azure 通过 DHCP 为虚拟机分配 DNS 服务器的地址。</span><span class="sxs-lookup"><span data-stu-id="e2258-204">Azure assigns virtual machines the addresses of DNS servers by DHCP.</span></span> <span data-ttu-id="e2258-205">DNS 服务器可以是:</span><span class="sxs-lookup"><span data-stu-id="e2258-205">DNS servers can be:</span></span>
  
- <span data-ttu-id="e2258-206">由 Azure 提供: 提供本地名称注册以及本地和 Internet 名称解析</span><span class="sxs-lookup"><span data-stu-id="e2258-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="e2258-207">由你提供: 提供本地或 intranet 名称注册以及 intranet 或 Internet 名称解析</span><span class="sxs-lookup"><span data-stu-id="e2258-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="e2258-208">表4显示了每种类型的 VNet 的 DNS 服务器的不同配置。</span><span class="sxs-lookup"><span data-stu-id="e2258-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="e2258-209">**VNet 类型**</span><span class="sxs-lookup"><span data-stu-id="e2258-209">**Type of VNet**</span></span>|<span data-ttu-id="e2258-210">**DNS 服务器**</span><span class="sxs-lookup"><span data-stu-id="e2258-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e2258-211">仅限云</span><span class="sxs-lookup"><span data-stu-id="e2258-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="e2258-212">Azure 为本地和 Internet 名称解析提供</span><span class="sxs-lookup"><span data-stu-id="e2258-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="e2258-213">用于本地和 Internet 名称解析的 Azure 虚拟机 (DNS 转发)</span><span class="sxs-lookup"><span data-stu-id="e2258-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="e2258-214">跨界</span><span class="sxs-lookup"><span data-stu-id="e2258-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="e2258-215">本地, 用于本地和 intranet 名称解析</span><span class="sxs-lookup"><span data-stu-id="e2258-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="e2258-216">用于本地和 intranet 名称解析的 Azure 虚拟机 (DNS 复制和转发)</span><span class="sxs-lookup"><span data-stu-id="e2258-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="e2258-217">**表 4: 两种不同类型的 Vnet 的 DNS 服务器选项**</span><span class="sxs-lookup"><span data-stu-id="e2258-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="e2258-218">有关详细信息, 请参阅[vm 和角色实例的名称解析](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)。</span><span class="sxs-lookup"><span data-stu-id="e2258-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="e2258-219">步骤 7: 确定负载平衡配置 (面向 Internet 或内部)。</span><span class="sxs-lookup"><span data-stu-id="e2258-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="e2258-220">在某些情况下, 您需要将传入流量分发到具有相同角色的一组服务器。</span><span class="sxs-lookup"><span data-stu-id="e2258-220">In some cases, you want to distribute incoming traffic to a set of servers that have the same role.</span></span> <span data-ttu-id="e2258-221">Azure IaaS 具有内置功能, 可用于对面向 Internet 和内部流量的负载执行此操作。</span><span class="sxs-lookup"><span data-stu-id="e2258-221">Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="e2258-222">Azure 面向 Internet 的负载平衡将未经请求的传入流量从 Internet 随机分配给负载平衡集的成员。</span><span class="sxs-lookup"><span data-stu-id="e2258-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="e2258-223">**图 4: Azure 中的外部负载平衡器**</span><span class="sxs-lookup"><span data-stu-id="e2258-223">**Figure 4: An external load balancer in Azure**</span></span>

![图 4: Azure 中的外部负载平衡器](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="e2258-225">图4显示了 Azure 中的外部负载平衡器, 用于将入站 NAT 规则或终结点上的传入流量分配给负载平衡集内的一组虚拟机。</span><span class="sxs-lookup"><span data-stu-id="e2258-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="e2258-226">Azure 内部负载平衡将来自其他 Azure 虚拟机或 intranet 计算机的未经请求的传入流量随机分配给负载平衡集的成员。</span><span class="sxs-lookup"><span data-stu-id="e2258-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="e2258-227">**图 5: Azure 中的内部负载平衡器**</span><span class="sxs-lookup"><span data-stu-id="e2258-227">**Figure 5: An internal load balancer in Azure**</span></span>

![图 5: Azure 中的内部负载平衡器](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="e2258-229">图5显示了 Azure 中的内部负载平衡器, 用于将入站 NAT 规则或终结点上的传入流量分配给负载平衡集内的一组虚拟机。</span><span class="sxs-lookup"><span data-stu-id="e2258-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="e2258-230">有关详细信息, 请参阅[Azure 负载平衡器](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)。</span><span class="sxs-lookup"><span data-stu-id="e2258-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="e2258-231">步骤 8: 确定虚拟设备和用户定义的路由的使用情况。</span><span class="sxs-lookup"><span data-stu-id="e2258-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="e2258-232">如果需要将流量转发到 VNet 中的虚拟设备, 则可能需要向子网中添加一个或多个用户定义的路由。</span><span class="sxs-lookup"><span data-stu-id="e2258-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="e2258-233">**图 6: Azure 中的虚拟设备和用户定义的路由**</span><span class="sxs-lookup"><span data-stu-id="e2258-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![图 6: Azure 中的虚拟设备和用户定义的路由](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="e2258-235">图6显示了一个跨界 VNet 和一个用户定义的路由, 该路由分配给指向虚拟设备的虚拟机托管的子网。</span><span class="sxs-lookup"><span data-stu-id="e2258-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="e2258-236">有关详细信息, 请参阅[用户定义的路由和 IP 转发](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)。</span><span class="sxs-lookup"><span data-stu-id="e2258-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="e2258-237">步骤 9: 确定 Internet 中的计算机连接到虚拟机的方式。</span><span class="sxs-lookup"><span data-stu-id="e2258-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="e2258-238">有多种方法可提供对 VNet 中的虚拟机的 Internet 访问, 包括从您的组织网络通过代理服务器或其他边缘设备进行访问。</span><span class="sxs-lookup"><span data-stu-id="e2258-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="e2258-239">表5列出了筛选或检查未经请求的传入流量的方法。</span><span class="sxs-lookup"><span data-stu-id="e2258-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="e2258-240">**方法**</span><span class="sxs-lookup"><span data-stu-id="e2258-240">**Method**</span></span>|<span data-ttu-id="e2258-241">**部署模式**</span><span class="sxs-lookup"><span data-stu-id="e2258-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e2258-242">1。在云服务上配置的终结点和 Acl</span><span class="sxs-lookup"><span data-stu-id="e2258-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="e2258-243">风格</span><span class="sxs-lookup"><span data-stu-id="e2258-243">Classic</span></span>  <br/> |
|<span data-ttu-id="e2258-244">2。网络安全组</span><span class="sxs-lookup"><span data-stu-id="e2258-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="e2258-245">资源管理器和经典</span><span class="sxs-lookup"><span data-stu-id="e2258-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="e2258-246">3。具有入站 NAT 规则的面向 Internet 的负载平衡器</span><span class="sxs-lookup"><span data-stu-id="e2258-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="e2258-247">资源经理</span><span class="sxs-lookup"><span data-stu-id="e2258-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="e2258-248">4。 Azure Marketplace 中的网络安全设备 (未显示)</span><span class="sxs-lookup"><span data-stu-id="e2258-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="e2258-249">资源管理器和经典</span><span class="sxs-lookup"><span data-stu-id="e2258-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="e2258-250">**表 5: 连接到虚拟机及其对应的 Azure 部署模型的方法**</span><span class="sxs-lookup"><span data-stu-id="e2258-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="e2258-251">**图 7: 通过 Internet 连接到 Azure 虚拟机**</span><span class="sxs-lookup"><span data-stu-id="e2258-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![图 7: 通过 Internet 连接到 Azure 虚拟机](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="e2258-253">图7显示了连接到云服务中的虚拟机的连接到 Internet 的计算机, 使用终结点、使用网络安全组的子网上的虚拟机以及使用外部负载平衡器和入站 NAT 规则的子网上的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="e2258-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="e2258-254">其他安全性的提供者为:</span><span class="sxs-lookup"><span data-stu-id="e2258-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="e2258-255">经过身份验证和加密的远程桌面和 SSH 连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="e2258-256">经过身份验证和加密的远程 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="e2258-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="e2258-257">IPsec 传输模式, 可用于端到端加密。</span><span class="sxs-lookup"><span data-stu-id="e2258-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="e2258-258">Azure DDOS 保护, 有助于防止外部和内部攻击</span><span class="sxs-lookup"><span data-stu-id="e2258-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="e2258-259">有关详细信息, 请参阅[适用于企业架构师](https://aka.ms/cloudarchsecurity)和[Azure 网络安全性](https://azure.microsoft.com/blog/azure-network-security/)的 Microsoft 云安全性。</span><span class="sxs-lookup"><span data-stu-id="e2258-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="e2258-260">步骤 10: 对于多个 Vnet, 确定 VNet 到 VNet 连接拓扑。</span><span class="sxs-lookup"><span data-stu-id="e2258-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="e2258-261">可以使用与用于连接组织站点的拓扑一样的拓扑来连接彼此的 Vnet。</span><span class="sxs-lookup"><span data-stu-id="e2258-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="e2258-262">菊花链配置连接系列中的 Vnet。</span><span class="sxs-lookup"><span data-stu-id="e2258-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="e2258-263">**图 8: Vnet 的菊花链配置**</span><span class="sxs-lookup"><span data-stu-id="e2258-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![图 8: Azure 虚拟网络的菊花链配置](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="e2258-265">图8显示了使用菊花链配置在系列中连接的五个 Vnet。</span><span class="sxs-lookup"><span data-stu-id="e2258-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="e2258-266">分支和中心配置将多个 Vnet 连接到一组中央 Vnet, 它们本身相互连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="e2258-267">**图 9: Vnet 的分支和中心配置**</span><span class="sxs-lookup"><span data-stu-id="e2258-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![图 9: Azure 虚拟网络的分支和中心配置](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="e2258-269">图9显示了六个 Vnet, 两个 Vnet 是相互连接的集线器, 另外还有两个其他分支 Vnet。</span><span class="sxs-lookup"><span data-stu-id="e2258-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="e2258-270">完全网格配置将每个 VNet 相互连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="e2258-271">**图 10: Vnet 的完整网格配置**</span><span class="sxs-lookup"><span data-stu-id="e2258-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![图 10: Azure 虚拟网络的网格配置](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="e2258-273">图10显示了四个相互连接的 Vnet, 总共使用6个 VNet 到 VNet 连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="e2258-274">跨界 VNet 的规划步骤</span><span class="sxs-lookup"><span data-stu-id="e2258-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="e2258-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="e2258-275"></span></span>

<span data-ttu-id="e2258-276">对跨界 VNet 执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="e2258-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="e2258-277">若要创建模拟的跨界开发/测试环境, 请参阅[Azure 中的模拟跨界虚拟网络](simulated-cross-premises-virtual-network-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="e2258-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="e2258-278">步骤 1: 确定与 VNet 的跨界连接 (S2S VPN 或 ExpressRoute)。</span><span class="sxs-lookup"><span data-stu-id="e2258-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="e2258-279">表6列出了不同类型的连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="e2258-280">**连接类型**</span><span class="sxs-lookup"><span data-stu-id="e2258-280">**Type of connection**</span></span>|<span data-ttu-id="e2258-281">**用途**</span><span class="sxs-lookup"><span data-stu-id="e2258-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e2258-282">站点到站点 (S2S) VPN</span><span class="sxs-lookup"><span data-stu-id="e2258-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="e2258-283">将1-10 网站 (包括其他 Vnet) 连接到单个 VNet。</span><span class="sxs-lookup"><span data-stu-id="e2258-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="e2258-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="e2258-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="e2258-285">通过 Internet Exchange 提供商 (IXP) 或网络服务提供商 (NSP) 对 Azure 的专用安全链接。</span><span class="sxs-lookup"><span data-stu-id="e2258-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="e2258-286">点到站点 (P2S) VPN</span><span class="sxs-lookup"><span data-stu-id="e2258-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="e2258-287">将一台计算机连接到 VNet。</span><span class="sxs-lookup"><span data-stu-id="e2258-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="e2258-288">VNet 对等或 VNet 到 VNet (V2V) VPN</span><span class="sxs-lookup"><span data-stu-id="e2258-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="e2258-289">将 VNet 连接到另一个 VNet。</span><span class="sxs-lookup"><span data-stu-id="e2258-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="e2258-290">**表 6: 跨界 Vnet 的连接类型**</span><span class="sxs-lookup"><span data-stu-id="e2258-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="e2258-291">有关最大连接数的详细信息, 请参阅[网络限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。</span><span class="sxs-lookup"><span data-stu-id="e2258-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="e2258-292">有关 VPN 设备的详细信息, 请参阅[用于站点到站点虚拟网络连接的 VPN 设备](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。</span><span class="sxs-lookup"><span data-stu-id="e2258-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="e2258-293">有关 VNet 对等的详细信息, 请参阅[VNet 对等](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)。</span><span class="sxs-lookup"><span data-stu-id="e2258-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="e2258-294">**图 11: 连接到跨界 VNet 的四种方式**</span><span class="sxs-lookup"><span data-stu-id="e2258-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![图 11: 连接到跨界 Azure 虚拟网络的三种方法](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="e2258-296">图11显示了具有四种类型的连接的 VNet: 来自计算机的 P2S 连接、来自本地网络的 S2S VPN 连接、来自本地网络的 ExpressRoute 连接以及来自另一个 VNet 的 VNet 到 VNet 连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="e2258-297">您可以通过以下方式连接到 VNet 中的 Vm:</span><span class="sxs-lookup"><span data-stu-id="e2258-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="e2258-298">从你的本地网络或 Internet 管理 VNet Vm</span><span class="sxs-lookup"><span data-stu-id="e2258-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="e2258-299">来自你的本地网络的 IT 工作负载访问</span><span class="sxs-lookup"><span data-stu-id="e2258-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="e2258-300">通过其他 Vnet 的网络扩展</span><span class="sxs-lookup"><span data-stu-id="e2258-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="e2258-301">连接的安全性由以下项提供:</span><span class="sxs-lookup"><span data-stu-id="e2258-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="e2258-302">P2S 使用安全套接字隧道协议 (SSTP)</span><span class="sxs-lookup"><span data-stu-id="e2258-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="e2258-303">S2S 和 VNet 到 VNet VPN 连接在 AES256 中使用 IPsec 隧道模式</span><span class="sxs-lookup"><span data-stu-id="e2258-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="e2258-304">ExpressRoute 是一种专用 WAN 连接</span><span class="sxs-lookup"><span data-stu-id="e2258-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="e2258-305">有关详细信息, 请参阅[适用于企业架构师](https://aka.ms/cloudarchsecurity)和[Azure 网络安全性](https://azure.microsoft.com/blog/azure-network-security/)的 Microsoft 云安全性。</span><span class="sxs-lookup"><span data-stu-id="e2258-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="e2258-306">步骤 2: 确定本地 VPN 设备或路由器。</span><span class="sxs-lookup"><span data-stu-id="e2258-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="e2258-307">本地 VPN 设备或路由器的行为如下:</span><span class="sxs-lookup"><span data-stu-id="e2258-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="e2258-308">一个 IPsec 对等方, 终止来自 Azure 网关的 S2S VPN 连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="e2258-309">专用对等 ExpressRoute 连接的 BPG 对等方和终结点。</span><span class="sxs-lookup"><span data-stu-id="e2258-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="e2258-310">**图 12: 本地 VPN 路由器或设备**</span><span class="sxs-lookup"><span data-stu-id="e2258-310">**Figure 12: The on-premises VPN router or device**</span></span>

![图 12: 本地 VPN 路由器或设备](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="e2258-312">图12显示了连接到本地 VPN 路由器或设备的跨界 VNet。</span><span class="sxs-lookup"><span data-stu-id="e2258-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="e2258-313">有关详细信息, 请参阅[关于 VPN 网关](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)。</span><span class="sxs-lookup"><span data-stu-id="e2258-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="e2258-314">步骤 3: 将路由添加到 intranet 以使 VNet 的地址空间可访问。</span><span class="sxs-lookup"><span data-stu-id="e2258-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="e2258-315">从内部部署到 Vnet 的路由包括以下内容:</span><span class="sxs-lookup"><span data-stu-id="e2258-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="e2258-316">指向你的 VPN 设备的 VNet 地址空间的路由。</span><span class="sxs-lookup"><span data-stu-id="e2258-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="e2258-317">指向 VPN 设备上的 VNet 地址空间的路由, 指向 S2S VPN 或 ExpressRoute 连接</span><span class="sxs-lookup"><span data-stu-id="e2258-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="e2258-318">**图 13: 使 VNet 可以访问所需的本地路由**</span><span class="sxs-lookup"><span data-stu-id="e2258-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![图 13: 使 Azure VNet 可访问所需的本地路由](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="e2258-320">图13显示了内部部署路由器以及表示 VNet 的地址空间的 VPN 路由器或设备所需的路由信息。</span><span class="sxs-lookup"><span data-stu-id="e2258-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="e2258-321">步骤 4: 对于 ExpressRoute, 请规划与提供程序的新连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="e2258-322">您可以通过三种不同的方式在本地网络和 Microsoft 云之间创建具有专用对等关系的 ExpressRoute 连接:</span><span class="sxs-lookup"><span data-stu-id="e2258-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="e2258-323">在云交换中归置</span><span class="sxs-lookup"><span data-stu-id="e2258-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="e2258-324">点到点以太网连接</span><span class="sxs-lookup"><span data-stu-id="e2258-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="e2258-325">任意对任意 (IP VPN) 网络</span><span class="sxs-lookup"><span data-stu-id="e2258-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="e2258-326">**图 14: 使用 ExpressRoute 连接到跨界 VNet**</span><span class="sxs-lookup"><span data-stu-id="e2258-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![图 14: 使用 ExpressRoute 连接到跨界 Azure 虚拟网络](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="e2258-328">图14显示了跨界 VNet 和从本地路由器到 Microsoft Azure 的 ExpressRoute 连接。</span><span class="sxs-lookup"><span data-stu-id="e2258-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="e2258-329">有关详细信息，请参阅[面向 Microsoft 云连接的 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="e2258-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="e2258-330">步骤 5: 确定 Azure 网关的本地网络地址空间。</span><span class="sxs-lookup"><span data-stu-id="e2258-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="e2258-331">若要从 VNet 路由到内部部署或其他 Vnet, Azure 会将流量转发到与分配给该网关的本地网络地址空间匹配的 Azure 网关之间。</span><span class="sxs-lookup"><span data-stu-id="e2258-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="e2258-332">**图 15: 跨界 VNet 的本地网络地址空间**</span><span class="sxs-lookup"><span data-stu-id="e2258-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![图 15: 跨界 Azure 虚拟网络的本地网络地址空间](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="e2258-334">图15显示跨界 VNet 和 Azure 网关上的本地网络地址空间, 它表示在本地网络上可访问的地址空间。</span><span class="sxs-lookup"><span data-stu-id="e2258-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="e2258-335">您可以通过以下方式定义本地网络地址空间:</span><span class="sxs-lookup"><span data-stu-id="e2258-335">You can define the Local Network address space in these ways:</span></span>
  
- <span data-ttu-id="e2258-336">选项 1: 当前所需或正在使用的地址空间的前缀列表 (添加新的子网时可能需要更新)。</span><span class="sxs-lookup"><span data-stu-id="e2258-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="e2258-337">选项 2: 整个本地地址空间 (仅在添加新地址空间时才需要更新)。</span><span class="sxs-lookup"><span data-stu-id="e2258-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="e2258-338">由于 Azure 网关不允许汇总路由, 因此必须为选项2定义本地网络地址空间, 以使其不包含 VNet 地址空间。</span><span class="sxs-lookup"><span data-stu-id="e2258-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="e2258-339">**图 16: VNet 地址空间创建的地址空间孔**</span><span class="sxs-lookup"><span data-stu-id="e2258-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![图 16: 由虚拟网络地址空间创建的地址空间孔](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="e2258-341">图16显示了地址空间的表示形式, 以及根空间和 VNet 地址空间。</span><span class="sxs-lookup"><span data-stu-id="e2258-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="e2258-342">下面的示例为在 VNet 创建的地址空间 "洞" 周围定义本地网络地址空间的前缀:</span><span class="sxs-lookup"><span data-stu-id="e2258-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="e2258-343">组织在其本地网络中使用部分专用地址空间 (10.0.0。0/8、172.16.0。0/12 和 192.168.0。0/16)。</span><span class="sxs-lookup"><span data-stu-id="e2258-343">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network.</span></span> <span data-ttu-id="e2258-344">他们选择选项2和 10.100.100.0/24 作为 VNet 地址空间。</span><span class="sxs-lookup"><span data-stu-id="e2258-344">They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="e2258-345">表7显示了为此示例定义本地网络地址空间的步骤和生成的前缀。</span><span class="sxs-lookup"><span data-stu-id="e2258-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="e2258-346">**步骤**</span><span class="sxs-lookup"><span data-stu-id="e2258-346">**Step**</span></span>|<span data-ttu-id="e2258-347">**结果**</span><span class="sxs-lookup"><span data-stu-id="e2258-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e2258-348">1。列出不是 VNet 地址空间的根空间的前缀。</span><span class="sxs-lookup"><span data-stu-id="e2258-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="e2258-349">172.16.0。0/12 和 192.168.0。0/16</span><span class="sxs-lookup"><span data-stu-id="e2258-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="e2258-350">2。在 VNet 地址空间中列出可变八进制数的非重叠前缀, 但不包括最后使用的八进制数。</span><span class="sxs-lookup"><span data-stu-id="e2258-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="e2258-351">10.0.0。0/16、10.1.0.0/16 .。。10.99.0.0/16、10.101.0.0/16 .。。10.254.0.0/16、10.255.0.0/16 (255 前缀, 跳过 10.100.0.0/16)</span><span class="sxs-lookup"><span data-stu-id="e2258-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="e2258-352">3。列出最近在使用的 VNet 地址空间的八位字节内的非重叠前缀。</span><span class="sxs-lookup"><span data-stu-id="e2258-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="e2258-353">10.100.0.0/24、10.100.1.0/24 .。。10.100.99.0/24、10.100.101.0/24 .。。10.100.254.0/24, 10.100.0.255.0/24 (255 个前缀, 跳过 10.100.100.0/24)</span><span class="sxs-lookup"><span data-stu-id="e2258-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="e2258-354">**表 7: 本地地址网络空间示例**</span><span class="sxs-lookup"><span data-stu-id="e2258-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="e2258-355">步骤 6: 为托管在 Azure 中的 DNS 服务器的 DNS 复制配置内部部署 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="e2258-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="e2258-356">若要确保本地计算机可以解析基于 Azure 的服务器的名称, 并且基于 Azure 的服务器可以解析本地计算机的名称, 请配置:</span><span class="sxs-lookup"><span data-stu-id="e2258-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="e2258-357">VNet 中的 DNS 服务器转发到本地 DNS 服务器</span><span class="sxs-lookup"><span data-stu-id="e2258-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="e2258-358">本地和 VNet 中的 DNS 服务器之间的适当区域的 DNS 复制</span><span class="sxs-lookup"><span data-stu-id="e2258-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="e2258-359">**图 17: 跨界 VNet 中的 DNS 服务器的 DNS 复制和转发**</span><span class="sxs-lookup"><span data-stu-id="e2258-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![图 17: 跨界 Azure 虚拟网络中 DNS 服务器的 DNS 复制和转发](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="e2258-361">图17显示了包含本地网络中的 DNS 服务器和 VNet 中的子网的跨界 VNet。</span><span class="sxs-lookup"><span data-stu-id="e2258-361">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet.</span></span> <span data-ttu-id="e2258-362">在两台 DNS 服务器之间配置了 DNS 复制和转发。</span><span class="sxs-lookup"><span data-stu-id="e2258-362">DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="e2258-363">步骤 7: 确定使用强制隧道。</span><span class="sxs-lookup"><span data-stu-id="e2258-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="e2258-364">Azure 子网的默认系统路由指向 Internet。</span><span class="sxs-lookup"><span data-stu-id="e2258-364">The default system route for Azure subnets points to the Internet.</span></span> <span data-ttu-id="e2258-365">若要确保来自虚拟机的所有流量都通过跨界连接传输, 请创建一个路由表, 并使用默认路由, 将 Azure 网关用作其下一个跃点地址。</span><span class="sxs-lookup"><span data-stu-id="e2258-365">To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address.</span></span> <span data-ttu-id="e2258-366">然后, 将路由表与子网相关联。</span><span class="sxs-lookup"><span data-stu-id="e2258-366">You then associate the route table with the subnet.</span></span> <span data-ttu-id="e2258-367">这称为强制隧道。</span><span class="sxs-lookup"><span data-stu-id="e2258-367">This is known as forced tunneling.</span></span> <span data-ttu-id="e2258-368">有关详细信息, 请参阅[配置强制隧道](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)。</span><span class="sxs-lookup"><span data-stu-id="e2258-368">For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="e2258-369">**图 18: 跨界 VNet 的用户定义的路由和强制隧道**</span><span class="sxs-lookup"><span data-stu-id="e2258-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![图 18: 跨界 Azure 虚拟网络的用户定义的路由和强制隧道](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="e2258-371">图18显示了一个跨界 VNet, 其中包含指向 Azure 网关的子网的用户定义路由。</span><span class="sxs-lookup"><span data-stu-id="e2258-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="e2258-372">Azure 中的 SharePoint Server 2016 场</span><span class="sxs-lookup"><span data-stu-id="e2258-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="e2258-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="e2258-373"></span></span>

<span data-ttu-id="e2258-374">托管在 Azure IaaS 中的 intranet IT 工作负载的一个示例是高可用性的多层 SharePoint Server 2016 场。</span><span class="sxs-lookup"><span data-stu-id="e2258-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="e2258-375">**图 19: Azure IaaS 中具有高可用性的 intranet SharePoint Server 2016 场**</span><span class="sxs-lookup"><span data-stu-id="e2258-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS 中的高可用性 SharePoint Server 2016 场](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="e2258-377">图19显示了在跨界 VNet 中部署的 SharePoint Server 2016 场的九个服务器, 该服务器场使用内部负载平衡器进行前端和数据层。</span><span class="sxs-lookup"><span data-stu-id="e2258-377">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers.</span></span> <span data-ttu-id="e2258-378">有关详细信息, 包括分步设计和部署说明, 请参阅[Microsoft Azure 中的 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)。</span><span class="sxs-lookup"><span data-stu-id="e2258-378">For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span></span>
  
> [!TIP]
> <span data-ttu-id="e2258-379">若要在模拟的跨界 VNet 中创建单个服务器的 SharePoint Server 2016 场, 请参阅[Azure 开发/测试环境中的 Intranet Sharepoint server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)。</span><span class="sxs-lookup"><span data-stu-id="e2258-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span></span> 
  
<span data-ttu-id="e2258-380">有关在跨界 Azure 虚拟网络中的虚拟机上部署的 IT 工作负载的其他示例, 请参阅[适用于 Azure IaaS 的混合云方案](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas)。</span><span class="sxs-lookup"><span data-stu-id="e2258-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e2258-381">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2258-381">See also</span></span>

[<span data-ttu-id="e2258-382">面向企业架构师的 Microsoft 云网络</span><span class="sxs-lookup"><span data-stu-id="e2258-382">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="e2258-383">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="e2258-383">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


