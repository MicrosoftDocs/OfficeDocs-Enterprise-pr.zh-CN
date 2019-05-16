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
# <a name="designing-networking-for-microsoft-azure-iaas"></a>为 Microsoft Azure IaaS 设计网络

 **摘要:** 了解如何在 Microsoft Azure IaaS 中设计工作负荷的优化网络。
  
若要优化 Azure IaaS 中承载的 IT 工作负载的网络, 需要了解 Azure 虚拟网络 (Vnet)、地址空间、路由、DNS 和负载平衡。
  
## <a name="planning-steps-for-any-vnet"></a>针对任何 VNet 的规划步骤

对任何类型的 VNet 执行以下步骤。
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a>步骤 1: 为 Microsoft 云服务准备 intranet。

完成 [Microsoft 云连接的常见元素](common-elements-of-microsoft-cloud-connectivity.md)中的**为 Microsoft 云服务准备网络的步骤**部分。
  
### <a name="step-2-optimize-your-internet-bandwidth"></a>步骤 2: 优化 Internet 带宽。

按照[设计 Microsoft SaaS 网络](designing-networking-for-microsoft-saas.md)中的**为 Microsoft SaaS 服务准备网络的步骤**部分的第 2-4 步操作，优化 Internet 带宽。
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a>步骤 3: 确定 VNet 的类型 (仅限云或跨界部署)。

仅限云的 VNet 与本地网络无连接。 例如：
  
**图 1: 仅限云的 VNet**

![图 1: Azure 中的仅限云的虚拟网络](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
图1显示了仅限云 VNet 中的一组虚拟机。
  
跨界 VNet 具有通过 Azure 网关与本地网络的站点到站点 (S2S) VPN 或 ExpressRoute 连接。 例如：
  
**图 2: 跨界 VNet**

![图 2: Azure 中的跨界虚拟网络](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
图2显示了跨界 VNet 中连接到本地网络的一组虚拟机。
  
请参阅本文中[有关跨界 VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem)部分的其他规划步骤。
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a>步骤 4: 确定 VNet 的地址空间。

表1显示了不同类型的 Vnet 的地址空间。
  
|**VNet 类型**|**虚拟网络地址空间**|
|:-----|:-----|
|仅限云  <br/> |任意专用地址空间  <br/> |
|互连仅限云  <br/> |任意专用, 但不与其他连接的 Vnet 重叠  <br/> |
|跨界  <br/> |专用, 但不与内部部署重叠  <br/> |
|相互连接的跨界  <br/> |专用, 但不与内部部署和其他连接的 Vnet 重叠  <br/> |
   
 **表 1: Vnet 的类型及其相应的地址空间**
  
从子网的地址空间为虚拟机分配地址配置的方式为 DHCP:
  
- 地址/子网掩码
    
- 默认网关
    
- DNS 服务器 IP 地址
    
您还可以保留静态 IP 地址。
  
也可以单独或从包含云服务 (仅针对经典部署计算机) 为虚拟机分配公共 IP 地址。
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a>步骤 5: 确定 VNet 中的子网和分配给每个的地址空间。

VNet 中有两种类型的子网, 即网关子网和虚拟机托管子网。
  
**图 3: Azure 中的两种类型的子网**

![图 3: Azure 中的两种类型的子网](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
图3显示了包含具有 Azure 网关的网关子网和一组包含虚拟机的虚拟机托管子网的 VNet。
  
Azure 需要 azure 网关子网, 以托管 Azure 网关的两台虚拟机。 指定至少具有29位前缀长度的地址空间 (示例: 192.168.15.248/29)。 建议使用27位或更小的前缀长度, 尤其是在计划使用 ExpressRoute 时。
  
确定 Azure 网关子网的地址空间的最佳做法是:
  
1. 确定网关子网的大小。
    
2. 在 VNet 的地址空间中的可变位中, 将用于网关子网的位设置为 0, 并将其余的位设置为1。
    
3. 转换为十进制并表示为一个地址空间, 其前缀长度设置为网关子网的大小。
    
使用此方法时, 网关子网的地址空间始终处于 VNet 地址空间的最远的一端。
  
下面的示例展示了如何定义网关子网的地址前缀: VNet 的地址空间为 10.119.0.0/16。 组织最初将使用站点到站点 VPN 连接, 但最终会获得 ExpressRoute。 表2显示了确定网络前缀表示法 (也称为 CIDR) 中的网关子网地址前缀的步骤和结果。

以下是确定网关子网地址前缀的步骤和示例:

1. 确定网关子网的大小。 在我们的示例中, 我们选择/28。
2. 为网关子网位 (G) 将 VNet 地址空间 (b) 的变量部分中的位设置为 0, 否则为 1 (V)。 对于我们的示例, 我们使用的是 VNet 的 10.119.0.0/16 地址空间。
<br/>
<br/>10.119。 bbbbbbbb . bbbbbbbb
<br/>10.119。 VVVVVVVV . VVVVGGGG
<br/>10.119。 11111111。 11110000
<br/><br/>
3. 将步骤2中的结果转换为 "小数", 并将其表示为地址空间。 对于我们的示例, 为10.119。 11111111。 11110000为 10.119.255.240, 并使用步骤1中的前缀长度 (在示例中为 28), 生成的网关子网地址前缀是 10.119.255.240/28。
  
有关详细信息, 请参阅[Azure 网关子网的地址空间计算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。
  
虚拟机托管的子网是放置 Azure 虚拟机的地方, 可以根据典型的本地指导方针 (如应用程序的通用角色或应用程序或子网隔离) 执行此操作。
  
Azure 使用每个子网上的前3个地址。 因此, Azure 子网上的可能地址数是 2<sup>n</sup> -5, 其中 n 是主机位的数量。 表3显示了所需的虚拟机范围、所需的主机位数以及相应的子网大小。
  
|**需要虚拟机**|**主机位**|**子网大小**|
|:-----|:-----|:-----|
|1-3  <br/> |第三章  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |型  <br/> |/26  <br/> |
|60-123  <br/> |步  <br/> |/25  <br/> |
   
 **表 3: 虚拟机要求及其子网大小**
  
有关子网或 VNet 上的最大虚拟机数量的详细信息, 请参阅[网络限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。
  
有关详细信息, 请参阅[规划和设计 Azure 虚拟网络](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)。
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a>步骤 6: 确定要分配给 VNet 中的 Vm 的 DNS 服务器配置和 DNS 服务器的地址。

Azure 通过 DHCP 为虚拟机分配 DNS 服务器的地址。 DNS 服务器可以是:
  
- 由 Azure 提供: 提供本地名称注册以及本地和 Internet 名称解析
    
- 由你提供: 提供本地或 intranet 名称注册以及 intranet 或 Internet 名称解析
    
表4显示了每种类型的 VNet 的 DNS 服务器的不同配置。
    
|**VNet 类型**|**DNS 服务器**|
|:-----|:-----|
|仅限云  <br/> |Azure 为本地和 Internet 名称解析提供  <br/> 用于本地和 Internet 名称解析的 Azure 虚拟机 (DNS 转发)  <br/> |
|跨界  <br/> |本地, 用于本地和 intranet 名称解析  <br/> 用于本地和 intranet 名称解析的 Azure 虚拟机 (DNS 复制和转发)  <br/> |
   
 **表 4: 两种不同类型的 Vnet 的 DNS 服务器选项**
  
有关详细信息, 请参阅[vm 和角色实例的名称解析](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)。
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a>步骤 7: 确定负载平衡配置 (面向 Internet 或内部)。

在某些情况下, 您需要将传入流量分发到具有相同角色的一组服务器。 Azure IaaS 具有内置功能, 可用于对面向 Internet 和内部流量的负载执行此操作。
  
Azure 面向 Internet 的负载平衡将未经请求的传入流量从 Internet 随机分配给负载平衡集的成员。
  
**图 4: Azure 中的外部负载平衡器**

![图 4: Azure 中的外部负载平衡器](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
图4显示了 Azure 中的外部负载平衡器, 用于将入站 NAT 规则或终结点上的传入流量分配给负载平衡集内的一组虚拟机。
  
Azure 内部负载平衡将来自其他 Azure 虚拟机或 intranet 计算机的未经请求的传入流量随机分配给负载平衡集的成员。 
  
**图 5: Azure 中的内部负载平衡器**

![图 5: Azure 中的内部负载平衡器](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
图5显示了 Azure 中的内部负载平衡器, 用于将入站 NAT 规则或终结点上的传入流量分配给负载平衡集内的一组虚拟机。
  
有关详细信息, 请参阅[Azure 负载平衡器](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)。
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a>步骤 8: 确定虚拟设备和用户定义的路由的使用情况。

如果需要将流量转发到 VNet 中的虚拟设备, 则可能需要向子网中添加一个或多个用户定义的路由。
  
**图 6: Azure 中的虚拟设备和用户定义的路由**

![图 6: Azure 中的虚拟设备和用户定义的路由](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
图6显示了一个跨界 VNet 和一个用户定义的路由, 该路由分配给指向虚拟设备的虚拟机托管的子网。
  
有关详细信息, 请参阅[用户定义的路由和 IP 转发](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)。
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a>步骤 9: 确定 Internet 中的计算机连接到虚拟机的方式。

有多种方法可提供对 VNet 中的虚拟机的 Internet 访问, 包括从您的组织网络通过代理服务器或其他边缘设备进行访问。
  
表5列出了筛选或检查未经请求的传入流量的方法。
  
|**方法**|**部署模式**|
|:-----|:-----|
|1。在云服务上配置的终结点和 Acl  <br/> |风格  <br/> |
|2。网络安全组  <br/> |资源管理器和经典  <br/> |
|3。具有入站 NAT 规则的面向 Internet 的负载平衡器  <br/> |资源经理  <br/> |
|4。 Azure Marketplace 中的网络安全设备 (未显示)  <br/> |资源管理器和经典  <br/> |
   
 **表 5: 连接到虚拟机及其对应的 Azure 部署模型的方法**
  
**图 7: 通过 Internet 连接到 Azure 虚拟机**

![图 7: 通过 Internet 连接到 Azure 虚拟机](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
图7显示了连接到云服务中的虚拟机的连接到 Internet 的计算机, 使用终结点、使用网络安全组的子网上的虚拟机以及使用外部负载平衡器和入站 NAT 规则的子网上的虚拟机。
  
其他安全性的提供者为:
  
- 经过身份验证和加密的远程桌面和 SSH 连接。
    
- 经过身份验证和加密的远程 PowerShell 会话。
    
- IPsec 传输模式, 可用于端到端加密。
    
- Azure DDOS 保护, 有助于防止外部和内部攻击
    
有关详细信息, 请参阅[适用于企业架构师](https://aka.ms/cloudarchsecurity)和[Azure 网络安全性](https://azure.microsoft.com/blog/azure-network-security/)的 Microsoft 云安全性。
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a>步骤 10: 对于多个 Vnet, 确定 VNet 到 VNet 连接拓扑。

可以使用与用于连接组织站点的拓扑一样的拓扑来连接彼此的 Vnet。
  
菊花链配置连接系列中的 Vnet。
  
**图 8: Vnet 的菊花链配置**

![图 8: Azure 虚拟网络的菊花链配置](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
图8显示了使用菊花链配置在系列中连接的五个 Vnet。
  
分支和中心配置将多个 Vnet 连接到一组中央 Vnet, 它们本身相互连接。
  
**图 9: Vnet 的分支和中心配置**

![图 9: Azure 虚拟网络的分支和中心配置](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
图9显示了六个 Vnet, 两个 Vnet 是相互连接的集线器, 另外还有两个其他分支 Vnet。
  
完全网格配置将每个 VNet 相互连接。
  
**图 10: Vnet 的完整网格配置**

![图 10: Azure 虚拟网络的网格配置](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
图10显示了四个相互连接的 Vnet, 总共使用6个 VNet 到 VNet 连接。
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a>跨界 VNet 的规划步骤
<a name="cross_prem"> </a>

对跨界 VNet 执行以下步骤。
  
> [!TIP]
> 若要创建模拟的跨界开发/测试环境, 请参阅[Azure 中的模拟跨界虚拟网络](simulated-cross-premises-virtual-network-in-azure.md)。 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a>步骤 1: 确定与 VNet 的跨界连接 (S2S VPN 或 ExpressRoute)。

表6列出了不同类型的连接。
  
|**连接类型**|**用途**|
|:-----|:-----|
|站点到站点 (S2S) VPN  <br/> |将1-10 网站 (包括其他 Vnet) 连接到单个 VNet。  <br/> |
|ExpressRoute  <br/> |通过 Internet Exchange 提供商 (IXP) 或网络服务提供商 (NSP) 对 Azure 的专用安全链接。  <br/> |
|点到站点 (P2S) VPN  <br/> |将一台计算机连接到 VNet。  <br/> |
|VNet 对等或 VNet 到 VNet (V2V) VPN  <br/> |将 VNet 连接到另一个 VNet。  <br/> |
   
 **表 6: 跨界 Vnet 的连接类型**
  
有关最大连接数的详细信息, 请参阅[网络限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。
  
有关 VPN 设备的详细信息, 请参阅[用于站点到站点虚拟网络连接的 VPN 设备](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。
  
有关 VNet 对等的详细信息, 请参阅[VNet 对等](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)。
  
**图 11: 连接到跨界 VNet 的四种方式**

![图 11: 连接到跨界 Azure 虚拟网络的三种方法](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
图11显示了具有四种类型的连接的 VNet: 来自计算机的 P2S 连接、来自本地网络的 S2S VPN 连接、来自本地网络的 ExpressRoute 连接以及来自另一个 VNet 的 VNet 到 VNet 连接。 
  
您可以通过以下方式连接到 VNet 中的 Vm:
  
- 从你的本地网络或 Internet 管理 VNet Vm
    
- 来自你的本地网络的 IT 工作负载访问
    
- 通过其他 Vnet 的网络扩展
    
连接的安全性由以下项提供:
  
- P2S 使用安全套接字隧道协议 (SSTP) 
    
- S2S 和 VNet 到 VNet VPN 连接在 AES256 中使用 IPsec 隧道模式
    
- ExpressRoute 是一种专用 WAN 连接
    
有关详细信息, 请参阅[适用于企业架构师](https://aka.ms/cloudarchsecurity)和[Azure 网络安全性](https://azure.microsoft.com/blog/azure-network-security/)的 Microsoft 云安全性。
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a>步骤 2: 确定本地 VPN 设备或路由器。

本地 VPN 设备或路由器的行为如下:
  
- 一个 IPsec 对等方, 终止来自 Azure 网关的 S2S VPN 连接。
    
- 专用对等 ExpressRoute 连接的 BPG 对等方和终结点。
    
**图 12: 本地 VPN 路由器或设备**

![图 12: 本地 VPN 路由器或设备](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
图12显示了连接到本地 VPN 路由器或设备的跨界 VNet。
  
有关详细信息, 请参阅[关于 VPN 网关](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)。
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a>步骤 3: 将路由添加到 intranet 以使 VNet 的地址空间可访问。

从内部部署到 Vnet 的路由包括以下内容:
  
1. 指向你的 VPN 设备的 VNet 地址空间的路由。
    
2. 指向 VPN 设备上的 VNet 地址空间的路由, 指向 S2S VPN 或 ExpressRoute 连接
    
**图 13: 使 VNet 可以访问所需的本地路由**

![图 13: 使 Azure VNet 可访问所需的本地路由](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
图13显示了内部部署路由器以及表示 VNet 的地址空间的 VPN 路由器或设备所需的路由信息。
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a>步骤 4: 对于 ExpressRoute, 请规划与提供程序的新连接。

您可以通过三种不同的方式在本地网络和 Microsoft 云之间创建具有专用对等关系的 ExpressRoute 连接:
  
- 在云交换中归置
    
- 点到点以太网连接
    
- 任意对任意 (IP VPN) 网络
    
**图 14: 使用 ExpressRoute 连接到跨界 VNet**

![图 14: 使用 ExpressRoute 连接到跨界 Azure 虚拟网络](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
图14显示了跨界 VNet 和从本地路由器到 Microsoft Azure 的 ExpressRoute 连接。
  
有关详细信息，请参阅[面向 Microsoft 云连接的 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a>步骤 5: 确定 Azure 网关的本地网络地址空间。

若要从 VNet 路由到内部部署或其他 Vnet, Azure 会将流量转发到与分配给该网关的本地网络地址空间匹配的 Azure 网关之间。
  
**图 15: 跨界 VNet 的本地网络地址空间**

![图 15: 跨界 Azure 虚拟网络的本地网络地址空间](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
图15显示跨界 VNet 和 Azure 网关上的本地网络地址空间, 它表示在本地网络上可访问的地址空间。 
  
您可以通过以下方式定义本地网络地址空间:
  
- 选项 1: 当前所需或正在使用的地址空间的前缀列表 (添加新的子网时可能需要更新)。
    
- 选项 2: 整个本地地址空间 (仅在添加新地址空间时才需要更新)。
    
由于 Azure 网关不允许汇总路由, 因此必须为选项2定义本地网络地址空间, 以使其不包含 VNet 地址空间。
  
**图 16: VNet 地址空间创建的地址空间孔**

![图 16: 由虚拟网络地址空间创建的地址空间孔](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
图16显示了地址空间的表示形式, 以及根空间和 VNet 地址空间。
  
下面的示例为在 VNet 创建的地址空间 "洞" 周围定义本地网络地址空间的前缀:
  
- 组织在其本地网络中使用部分专用地址空间 (10.0.0。0/8、172.16.0。0/12 和 192.168.0。0/16)。 他们选择选项2和 10.100.100.0/24 作为 VNet 地址空间。
    
表7显示了为此示例定义本地网络地址空间的步骤和生成的前缀。
  
|**步骤**|**结果**|
|:-----|:-----|
|1。列出不是 VNet 地址空间的根空间的前缀。  <br/> |172.16.0。0/12 和 192.168.0。0/16  <br/> |
|2。在 VNet 地址空间中列出可变八进制数的非重叠前缀, 但不包括最后使用的八进制数。  <br/> |10.0.0。0/16、10.1.0.0/16 .。。10.99.0.0/16、10.101.0.0/16 .。。10.254.0.0/16、10.255.0.0/16 (255 前缀, 跳过 10.100.0.0/16)  <br/> |
|3。列出最近在使用的 VNet 地址空间的八位字节内的非重叠前缀。  <br/> |10.100.0.0/24、10.100.1.0/24 .。。10.100.99.0/24、10.100.101.0/24 .。。10.100.254.0/24, 10.100.0.255.0/24 (255 个前缀, 跳过 10.100.100.0/24)  <br/> |
   
 **表 7: 本地地址网络空间示例**
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a>步骤 6: 为托管在 Azure 中的 DNS 服务器的 DNS 复制配置内部部署 DNS 服务器。

若要确保本地计算机可以解析基于 Azure 的服务器的名称, 并且基于 Azure 的服务器可以解析本地计算机的名称, 请配置:
  
- VNet 中的 DNS 服务器转发到本地 DNS 服务器
    
- 本地和 VNet 中的 DNS 服务器之间的适当区域的 DNS 复制
    
**图 17: 跨界 VNet 中的 DNS 服务器的 DNS 复制和转发**

![图 17: 跨界 Azure 虚拟网络中 DNS 服务器的 DNS 复制和转发](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
图17显示了包含本地网络中的 DNS 服务器和 VNet 中的子网的跨界 VNet。 在两台 DNS 服务器之间配置了 DNS 复制和转发。
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a>步骤 7: 确定使用强制隧道。

Azure 子网的默认系统路由指向 Internet。 若要确保来自虚拟机的所有流量都通过跨界连接传输, 请创建一个路由表, 并使用默认路由, 将 Azure 网关用作其下一个跃点地址。 然后, 将路由表与子网相关联。 这称为强制隧道。 有关详细信息, 请参阅[配置强制隧道](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)。
  
**图 18: 跨界 VNet 的用户定义的路由和强制隧道**

![图 18: 跨界 Azure 虚拟网络的用户定义的路由和强制隧道](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
图18显示了一个跨界 VNet, 其中包含指向 Azure 网关的子网的用户定义路由。
  
## <a name="sharepoint-server-2016-farm-in-azure"></a>Azure 中的 SharePoint Server 2016 场
<a name="cross_prem"> </a>

托管在 Azure IaaS 中的 intranet IT 工作负载的一个示例是高可用性的多层 SharePoint Server 2016 场。
  
**图 19: Azure IaaS 中具有高可用性的 intranet SharePoint Server 2016 场**

![Azure IaaS 中的高可用性 SharePoint Server 2016 场](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
图19显示了在跨界 VNet 中部署的 SharePoint Server 2016 场的九个服务器, 该服务器场使用内部负载平衡器进行前端和数据层。 有关详细信息, 包括分步设计和部署说明, 请参阅[Microsoft Azure 中的 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)。
  
> [!TIP]
> 若要在模拟的跨界 VNet 中创建单个服务器的 SharePoint Server 2016 场, 请参阅[Azure 开发/测试环境中的 Intranet Sharepoint server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)。 
  
有关在跨界 Azure 虚拟网络中的虚拟机上部署的 IT 工作负载的其他示例, 请参阅[适用于 Azure IaaS 的混合云方案](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas)。
  
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)


