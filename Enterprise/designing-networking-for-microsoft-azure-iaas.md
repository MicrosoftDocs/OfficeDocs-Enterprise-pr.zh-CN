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
# <a name="designing-networking-for-microsoft-azure-iaas"></a>为 Microsoft Azure IaaS 设计网络

 **摘要：** 了解如何设计优化的网络的 Microsoft Azure IaaS 中的工作负荷。
  
若要优化托管在 Azure IaaS 中的 IT 工作负载的网络，需要了解 Azure 虚拟网络 (VNet)、地址空间、路由、DNS 和负载平衡等相关知识。
  
## <a name="planning-steps-for-any-vnet"></a>任何 VNet 的规划步骤

对于任何类型的 VNet，请执行以下步骤。
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a>步骤 1：为 Microsoft 云服务准备 Intranet。

完成 [Microsoft 云连接的常见元素](common-elements-of-microsoft-cloud-connectivity.md)中的**为 Microsoft 云服务准备网络的步骤**部分。
  
### <a name="step-2-optimize-your-internet-bandwidth"></a>步骤 2：优化 Internet 带宽。

按照[设计 Microsoft SaaS 网络](designing-networking-for-microsoft-saas.md)中的**为 Microsoft SaaS 服务准备网络的步骤**部分的第 2-4 步操作，优化 Internet 带宽。
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a>步骤 3：确定 VNet 的类型（仅限云或跨界部署）。

仅限云 VNet 没有到本地网络的连接。下面是一个示例。
  
**图 1：仅限云 VNet**

![图 1：Azure 中的云专用虚拟网络](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
图 1 显示了仅限云 VNet 中的一组虚拟机。
  
跨界 VNet 具有站点到站点 (S2S) VPN 或通过 Azure 网关实现的到本地网络的 ExpressRoute 连接。下面是一个示例。
  
**图 2：跨界 VNet**

![图 2：Azure 中的跨界虚拟网络](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
图 2 显示了连接到本地网络的跨界 VNet 中的一组虚拟机。
  
其他信息，请参阅本文中的[跨界 VNet 的规划步骤](designing-networking-for-microsoft-azure-iaas.md#cross_prem)部分。
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a>步骤 4：确定 VNet 的地址空间。

表 1 显示不同 VNet 类型的地址空间。
  
|**VNet 类型**|**虚拟网络地址空间**|
|:-----|:-----|
|仅限云  <br/> |任意专用地址空间  <br/> |
|互连的仅限云类型  <br/> |任意专用，但不是重叠的与其他连接 VNets  <br/> |
|跨界  <br/> |专用类型，但不与本地 VNet 重叠  <br/> |
|互连的跨界类型  <br/> |专用类型，但不与本地或其他连接 VNet 重叠  <br/> |
   
 **表 1：VNet 类型及其对应的地址空间**
  
DHCP 从子网的地址空间中为虚拟机分配地址配置。
  
- 地址/子网掩码
    
- 默认网关
    
- DNS 服务器 IP 地址
    
你还可以保留静态的 IP 地址。
  
还可以单独或从包含云服务中为虚拟机分配公用 IP 地址（仅适用于典型的部署计算机）。
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a>步骤 5：确定 VNet 中的子网及分配给每个子网的地址空间。

VNet 中有两种类型的子网：网关子网和虚拟机托管的子网。
  
**图 3：Azure 中两种类型的子网**

![图 3：Azure 中两种类型的子网](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
图 3 显示了包含网关子网已 Azure 的网关及一系列包含虚拟机的虚拟机托管的子网 VNet。
  
Azure 需要 Azure 网关子网来托管 Azure 网关的两个虚拟机。指定前缀长度至少有 29 位的地址空间（例如：192.168.15.248/29）。尤其是在你计划使用 ExpressRoute 时，建议使用 28 位或更短的前缀长度。
  
用于确定 Azure 网关子网的地址空间最佳做法是：
  
1. 确定网关子网的大小。
    
2. 在 VNet 地址空间的可变位中，将用于网关子网的位设置为 0，将剩余位设置为 1。
    
3. 转换为十进制并表示为一个地址空间，其中将前缀长度设置为网关子网的大小。
    
使用此方法时，网关子网的地址空间始终位于 VNet 地址空间的最远端。
  
下面是定义网关子网的地址前缀的一个示例：VNet 的地址空间是 10.119.0.0/16。该组织最初使用站点到站点的 VPN 连接，但最终采用了 ExpressRoute。表 2 显示了确定网络前缀符号（也称为 CIDR）中的网关子网地址前缀的步骤和结果。

下面是步骤和示例确定的网关子网地址前缀：

1. 决定的网关子网的大小。对于我们的示例，我们选择 /28。
2. 位的部分中设置变量 VNet 地址空间 (b) 的网关的 0 到子网位 (G)，否则为 1 (V)。对于我们的示例，我们将使用 10.119.0.0/16 地址空间 VNet。<br/>
<br/>10.119。 bbbbbbbb。bbbbbbbb<br/>10.119。 VVVVVVVV。VVVVGGGG<br/>10.119。 11111111。11110000<br/><br/>
3. 步骤 2 中的结果转换为十进制和 express 作为地址空间。对于我们的示例，10.119。11111111。11110000 10.119.255.240，并使用步骤 1，(在本例中为 28) 中的前缀长度，生成的网关子网地址前缀都是 10.119.255.240/28。
  
有关详细信息，请参阅[Azure 网关子网的地址空间计算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。
  
虚拟机托管的子网用来放置 Azure 虚拟机，你可以根据典型的本地指南执行这一任务，例如公共角色、应用程序层或用于子网隔离。
  
Azure 上的每个子网使用的前 3 的地址。因此，可能在 Azure 子网上地址数是 2<sup>n</sup> -5，其中 n 是主机位的数字。表 3 显示的虚拟机所需的号码范围承载需要的二进制文件和相应的子网大小。
  
|**所需的虚拟机**|**主机位**|**子网大小**|
|:-----|:-----|:-----|
|1-3  <br/> |3   <br/> |/29  <br/> |
|4-11  <br/> |4   <br/> |/28  <br/> |
|12-27  <br/> |5   <br/> |/27  <br/> |
|28-59  <br/> |6   <br/> |/26  <br/> |
|60-123  <br/> |7   <br/> |/25  <br/> |
   
 **表 3：虚拟机要求及其子网大小**
  
有关虚拟机上的子网或 VNet 的最大量的详细信息，请参阅[网络限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。
  
有关详细信息，请参阅[规划和设计 Azure 虚拟网络](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)。
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a>步骤 6：确定 VNet 中分配给 VM 的 DNS 服务器配置和DNS 服务器地址。

Azure 根据 DHCP 为虚拟机分配 DNS 服务器的地址。DNS 服务器可以：
  
- 由 Azure 提供：提供本地名称注册及本地和 Internet 名称解析
    
- 由你提供：提供本地或 Intranet 名称注册及 Intranet 或 Internet 名称解析
    
表 4 显示了每种类型的 VNet 不同 DNS 服务器的配置。
    
|**VNet 类型**|**DNS 服务器**|
|:-----|:-----|
|仅限云  <br/> |由 Azure 提供，用于本地和 Internet 名称解析  <br/> Azure 虚拟机，用于本地和 Internet 名称解析（DNS 转发）  <br/> |
|跨界  <br/> |本地，用于本地和 Intranet 名称解析  <br/> Azure 虚拟机，用于本地和 Intranet 名称解析（DNS 复制和转发）  <br/> |
   
 **表 4：针对两种不同类型的 VNet 的 DNS 服务器选项**
  
有关详细信息，请参阅[虚拟机和角色实例的名称解析](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)。
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a>步骤 7：确定负载平衡配置（面向 Internet 或内部）。

在某些情况下，你需要将传入流量分配给具有相同角色的一组服务器。对于面向 Internet 和内部流量负载，Azure IaaS 使用内置设备来执行此操作。
  
Azure 面向 Internet 的负载平衡功能将来自 Internet 的未经请求的传入流量随机分配给负载平衡集的成员。 
  
**图 4：Azure 中的外部负载平衡器**

![图 4：Azure 中的外部负载平衡器](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
图 4 显示分发 NAT 的入站的规则或终结点，以一的负载平衡集中的虚拟机上的传入流量的 Azure 中的外部负载平衡器。
  
Azure 内部负载平衡功能将来自其他 Azure VM 或 Intranet 计算机的未经请求的传入流量随机分配给负载平衡集的成员。  
  
**图 5：Azure 中的内部负载平衡器**

![图 5：Azure 中的内部负载平衡器](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
图 5 显示分发 NAT 的入站的规则或终结点，以一的负载平衡集中的虚拟机上的传入流量的 Azure 中的内部负载平衡器。
  
有关详细信息，请参阅[Azure 负载平衡器](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)。
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a>步骤 8：确定使用虚拟设备和用户定义的路由。

如果需要将流量转发到你的 VNet 中的虚拟设备，你可能需要将一个或多个用户定义的路由添加到子网。
  
**图 6：Azure 中的虚拟设备和用户定义的路由**

![图 6：Azure 中的虚拟装置和用户定义的路由](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
图 6 显示了分配给虚拟机托管的子网的跨界 VNet 和用户定义的路由，其中子网指向虚拟设备。
  
有关详细信息，请参阅[用户定义的路由和 IP 转发](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)。
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a>步骤 9：确定 Internet 中的计算机如何连接到虚拟机。

有多种方式提供 Internet 访问 VNet 中的虚拟机的权限，这包括通过代理服务器或其他边缘服务从组织网络访问。
  
表 5 列出了筛选或检查未经请求的传入流量的方法。
  
|**方法**|**部署模型**|
|:-----|:-----|
|1.在云服务中配置的终结点和 ACL  <br/> |经典  <br/> |
|2.网络安全组  <br/> |Resource Manager 和经典  <br/> |
|3.面向 Internet 的负载平衡器，具有入站 NAT 规则  <br/> |资源经理  <br/> |
|4.网络安全设备中 Azure Marketplace （不显示）  <br/> |Resource Manager 和经典  <br/> |
   
 **表 5：连接到虚拟机的方法及其对应的 Azure 部署模型**
  
**图 7：通过 Internet 连接到 Azure 虚拟机**

![图 7：通过 Internet 连接到 Azure 虚拟机](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
图 7 显示已连接到 Internet 的计算机使用终结点连接到云服务中的虚拟机、使用网络安全组连接到子网中的虚拟机，以及使用外部负载平衡器和入站 NAT 规则连接到子网中的虚拟机。
  
其他安全性通过以下项实现：
  
- 已验证并已加密的远程桌面和 SSH 连接。
    
- 已验证并已加密的远程 PowerShell 会话。
    
- 可用于端到端加密的 IPsec 传输模式。
    
- 有助于防止外部和内部攻击的 Azure DDOS 保护
    
有关详细信息，请参阅[Microsoft 云安全的企业架构师](https://aka.ms/cloudarchsecurity)和[Azure 网络安全](https://azure.microsoft.com/blog/azure-network-security/)。
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a>步骤 10：为多个 VNet 确定 VNet 到 VNet 连接的拓扑。

可以使用类似于用来连接组织站点的拓扑将 VNet 彼此连接。
  
菊花链配置以串联方式连接 VNet。
  
**图 8：VNet 的菊花链配置**

![图 8：Azure 虚拟网络的菊花链配置](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
图 8 显示系列使用串接配置中连接的五个 VNets。
  
中心辐射型配置将多个 VNet 连接到一组本身已彼此连接的中心 VNet。
  
**图 9：VNet 的中心辐射型配置**

![图 9：Azure 虚拟网络的中心辐射型配置](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
图 9 显示六个 VNet，其中两个是彼此相连的中心 VNet，另外各有两个分支 VNet。
  
全网状配置使每个 VNet 相互连接。
  
**图 10：VNet 的全网状配置**

![图 10：Azure 虚拟网络的网格配置](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
图 10 显示了四个全都彼此相连的 VNet，共使用六个 VNet 到 VNet 的连接。
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a>跨界 VNet 的规划步骤
<a name="cross_prem"> </a>

请按照以下针对跨界 VNet 的步骤操作。
  
> [!TIP]
> 若要创建一个模拟的跨界开发/测试环境，请参阅 [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md)。 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a>步骤 1：确定与 VNet（S2S VPN 或 ExpressRoute）的跨界连接。

表 6 列出了不同类型的连接。
  
|**连接类型**|**用途**|
|:-----|:-----|
|站点到站点 (S2S) VPN  <br/> |连接到单个 VNet 1-10 网站 （包括其他 VNets）。  <br/> |
|ExpressRoute  <br/> |通过 Internet Exchange 提供程序 (IXP) 或网络服务提供商 (NSP) 提供的专用的安全链接。  <br/> |
|点到站点 (P2S) 的 VPN  <br/> |将一台计算机连接到 VNet。  <br/> |
|VNet 对等或 VNet 到 VNet (V2V) VPN   <br/> |将一个 VNet 连接到另一个 VNet。  <br/> |
   
 **表 6：跨内部 VNet 的连接类型**
  
最大连接数的详细信息，请参阅[网络限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。
  
有关 VPN 设备的详细信息，请参阅[站点到站点虚拟网络连接的 VPN 设备](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。
  
有关对等 VNet 的详细信息，请参阅[VNet 对等](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)。
  
**图 11：连接跨界 VNet 的四种方法**

![图 11：连接到跨界 Azure 虚拟网络的三种方式](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
图 11 显示四种类型的连接与 VNet： 从一台计算机的 P2S 连接、 从本地网络 S2S VPN 连接、 从本地网络，ExpressRoute 连接和从另一个 VNet VNet 到 VNet 连接。 
  
你可以通过以下方式连接到 VNet 中的 VM：
  
- 来自本地网络或 Internet 的 VNet VM 管理
    
- 来自本地网络的 IT 工作负载访问
    
- 通过附加 VNet 的网络扩展
    
通过以下方式实现连接的安全性：
  
- P2S 使用安全套接字隧道协议 (SSTP)  
    
- S2S 和 VNet 到 VNet VPN 连接都通过 AES256 使用 IPsec 隧道模式
    
- ExpressRoute 是专用的 WAN 连接
    
有关详细信息，请参阅[Microsoft 云安全的企业架构师](https://aka.ms/cloudarchsecurity)和[Azure 网络安全](https://azure.microsoft.com/blog/azure-network-security/)。
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a>步骤 2：确定本地 VPN 设备或路由器。

本地 VPN 设备或路由器用作：
  
- IPsec 对等方，终止来自 Azure 网关的 S2S VPN 连接。
    
- 专用的对等 ExpressRoute 连接的 BPG 对等和终止点。
    
**图 12：本地 VPN 路由器或设备**

![图 12：本地 VPN 路由器或设备](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
图 12 显示连接到本地 VPN 路由器或设备的跨界 VNet。
  
有关详细信息，请参阅[有关 VPN 网关](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)。
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a>步骤 3： 添加对进行 VNet 的地址空间可访问 intranet 路由。

从本地到 VNet 的路由包含以下部分：
  
1. 指向你的 VPN 设备的 VNet 地址空间的路由。
    
2. 你的 VPN 设备上的 VNet 地址空间跨 S2S VPN 或 ExpressRoute 连接指向的路由
    
**图 13：使 VNet 可以访问所需的本地路由**

![图 13：使 Azure VNet 可以访问所需的本地路由](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
图 13 显示了本地路由器和 VPN 路由器或设备所需的路由信息，VPN 路由器或设备表示 VNet 的地址空间。
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a>步骤 4：对于 ExpressRoute，计划与你的提供程序的新连接。

通过以下三种不同的方式，你可以利用本地网络与 Microsoft 云之间的专用对等创建 ExpressRoute 连接：
  
- 在云交换中归置
    
- 点到点以太网连接
    
- 任意对任意 (IP VPN) 的网络
    
**图 14：使用 ExpressRoute 连接到跨界 VNet**

![图 14：使用 ExpressRoute 连接到跨界 Azure 虚拟网络](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
图 14 显示了跨界 VNet 以及从本地路由器到 Microsoft Azure 的 ExpressRoute 连接。
  
有关详细信息，请参阅[面向 Microsoft 云连接的 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a>步骤 5：确定 Azure 网关的本地网络地址空间。

对于从 VNet 到本地或其他 VNet 的路由，Azure 通过与分配给它的本地网络地址空间匹配的 Azure 网关转发流量。
  
**图 15：跨界 VNet 的本地网络地址空间**

![图 15：跨界 Azure 虚拟网络的本地网络地址空间](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
图 15 显示跨界 VNet 以及 Azure 网关中的本地网络地址空间，Azure 网关表示本地网络上可访问的地址空间。  
  
您可以按以下方式定义的本地网络地址空间：
  
- 选项 1：当前所需或正在使用的地址空间的前缀列表（当你添加新的子网时可能需要更新）。
    
- 选项 2：你的整个本地地址空间（仅当你添加新的地址空间时需要更新）。
    
由于 Azure 网关不允许汇总路由，你必须定义选项 2 中的本地网络地址空间，使其不包括 VNet 地址空间。
  
**图 16：VNet 地址空间创建的地址空间孔**

![图 16：虚拟网络地址空间创建的地址空间孔](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
图 16 显示了地址空间的表示形式，其中具有根空间和 VNet 地址空间。
  
下面是一个示例定义地址空间"孔"由 VNet 周围的本地网络地址空间的前缀：
  
- 组织使用其本地网络中的专用地址空间（10.0.0.0/8、172.16.0.0/12 和 192.168.0.0/16）部分。他们选择选项 2 和 10.100.100.0/24 作为自己的 VNet 地址空间。
    
表 7 显示了定义此示例中的本地网络地址空间的步骤和生成前缀。
  
|**步骤**|**结果**|
|:-----|:-----|
|1.列出不属于 VNet 地址空间的根空间的前缀。  <br/> |172.16.0.0/12 和 192.168.0.0/16  <br/> |
|2.列出到变量八进制数，但不包括在 VNet 地址空间的最后一个使用的八进制的非重叠的前缀。  <br/> |10.0.0.0/16、 10.1.0.0/16...10.99.0.0/16、 10.101.0.0/16...10.254.0.0/16，10.255.0.0/16 （255 前缀，跳过 10.100.0.0/16）  <br/> |
|3.列表中的最后一个使用八进制 VNet 地址空间的非重叠的前缀。  <br/> |10.100.0.0/24、 10.100.1.0/24...10.100.99.0/24、 10.100.101.0/24...10.100.254.0/24，10.100.0.255.0/24 （255 前缀，跳过 10.100.100.0/24）  <br/> |
   
 **表 7：示例本地地址网络空间**
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a>步骤 6：通过在 Azure 中托管的 DNS 服务器配置 DNS 复制的本地 DNS 服务器。

若要确保本地计算机可以解析基于 Azure 的服务器的名称，并且基于 Azure 的服务器可以解析本地计算机的名称，请配置：
  
- 你的 VNet 中的 DNS 服务器，以便转发到本地 DNS 服务器
    
- 本地和 VNet 中的 DNS 服务器之间相应区域的 DNS 复制
    
**图 17：跨界 VNet 中的 DNS 服务器的 DNS 复制和转发**

![图 17：跨界 Azure 虚拟网络中的 DNS 复制和 DNS 服务器转发](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
图 17 显示了跨界 VNet，其中 DNS 服务器位于本地网络和 VNet 中的子网中。已在这两个 DNS 服务器之间配置了 DNS 复制和转发。
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a>步骤 7：确定使用强制隧道。

Azure 子网的默认系统路由指向 Internet。若要确保从虚拟机的所有通信都穿越跨界连接，请使用的默认路由的 Azure 网关用作其下一个跃点地址创建路由表。然后，您将在路由表关联与子网。这称为强制隧道。有关详细信息，请参阅[Configure 强制隧道](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)。
  
**图 18：用户定义的路由和跨界 VNet 的强制隧道**

![图 18：用户定义的路由和跨界 Azure 虚拟网络的强制隧道](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
图 18 显示跨界 VNet 与子网指向 Azure 网关的用户定义的路由。
  
## <a name="sharepoint-server-2016-farm-in-azure"></a>Azure 中的 SharePoint Server 2016 场
<a name="cross_prem"> </a>

Intranet Azure IaaS 中承载的 IT 工作负荷的示例是高可用性、 多层 SharePoint Server 2016 服务器场。
  
**图 19：Azure IaaS 中的高可用性 Intranet SharePoint Server 2016 场**

![Azure IaaS 中具有高可用性的 SharePoint Server 2016 场](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
图 19 显示了使用内部负载平衡器的前端和数据层跨界 VNet 中部署 SharePoint Server 2016 服务器场的九个服务器。有关详细信息，包括分步设计和部署的说明，请参阅[Microsoft Azure 中的 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)。
  
> [!TIP]
> 创建模拟的跨界 VNet 在单服务器 2016 SharePoint 服务器场，请参阅[Azure 的开发测试环境中的 Intranet SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)。 
  
有关其他示例中虚拟跨内部部署 Azure 虚拟机上部署的 IT 工作负荷的网络，请参阅[Azure IaaS 混合云方案](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas)。
  
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)


