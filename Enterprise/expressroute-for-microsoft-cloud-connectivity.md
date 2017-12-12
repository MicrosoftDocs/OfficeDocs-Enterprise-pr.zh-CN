---
title: "面向 Microsoft 云连接的 ExpressRoute"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 1/10/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: "摘要： 了解 ExpressRoute 如何帮助你更快、更可靠地与 Microsoft 云服务和平台相连接。"
---

# 面向 Microsoft 云连接的 ExpressRoute

 **摘要：** 了解 ExpressRoute 如何帮助你更快、更可靠地与 Microsoft 云服务和平台相连接。
  
ExpressRoute 提供了到 Microsoft 云的单独、专用、高吞吐量的网络连接。
  
## ExpressRoute 到 Microsoft 云

下面是在没有 ExpressRoute 连接的情况下到 Microsoft 云的网络路径。
  
**图 1：没有 ExpressRoute 的网络路径**

![图 1：没有 ExpressRoute 的网络路径](images/27796846-3b0a-4bbc-8b39-22552d037fba.png)
  
图 1 显示内部部署网络与 Microsoft 云之间的典型路径。内部部署网络边缘通过到 ISP 的 WAN 链接连接到 Internet。然后，流量流经 Internet 到达 Microsoft 云的边缘。Microsoft 云内的云产品包括 Office 365、Microsoft Azure、Microsoft Intune 和 Dynamics 365。组织的用户可以位于内部部署网络或 Internet。
  
如果没有 ExpressRoute 连接，你唯一可以控制的到 Microsoft 云的流量路径部分（并且与服务提供商有关系）是内部部署网络边缘与 ISP 之间的链接。 
  
受限于中断、流量拥塞和恶意用户监视，ISP 与 Microsoft 云边缘之间的路径是 Internet 中尽力而为的传送系统。
  
Internet 中的用户，例如漫游或远程用户，通过 Internet 将他们的流量发送到 Microsoft 云。
  
以下是在有 ExpressRoute 连接的情况下到 Microsoft 云的网络路径。
  
**图 2：有 ExpressRoute 的网络路径**

![图 2：有 ExpressRoute 的网络路径](images/a22eccb1-e3d2-4c69-a751-6539ffc0d8c2.png)
  
图 2 显示了两个网络路径。到 Microsoft Intune 的流量与普通 Internet 流量的路径相同。Office 365、Microsoft Azure 和 Dynamics 365 的流量经过 ExpressRoute 连接，这是内部部署网络边缘与 Microsoft 云边缘之间的专用路径。
  
如果有 ExpressRoute 连接，你现在可以通过与服务提供商之间的关系控制从你的边缘到 Microsoft 云边缘的整个流量路径。此连接能提供可预知的性能和正常运行时间达 99.9% 的 SLA。
  
基于服务提供商到 Office 365、Azure 和 Dynamics 365 服务的连接，现在可以依靠可预测的吞吐量和延迟。目前不支持 ExpressRoute 到 Microsoft Intune 的连接。
  
通过 ExpressRoute 连接发送的流量不再受限于 Internet 中断、流量拥塞和监视。
  
Internet 中的用户，例如漫游或远程用户，仍通过 Internet 将他们的流量发送到 Microsoft 云。在 Azure IaaS 中托管的业务应用程序 Intranet 线的流量是一个例外情况，此类流量是通过到内部部署网络的远程访问连接的 ExpressRoute 连接发送的。
  
即使有 ExpressRoute 连接，一些流量仍然通过 Internet 发送，例如 DNS 查询、证书吊销列表检查和内容交付网络 (CDN) 请求。
  
有关详细信息，请参阅下列更多资源：
  
- [面向 Office 365 的 ExpressRoute](https://aka.ms/expressrouteoffice365)
    
- [ExpressRoute for Azure](https://azure.microsoft.com/services/expressroute/)（面向 Azure 的 ExpressRoute）
    
## 面向 Azure 的 ExpressRoute 的优点

下面是使用面向基于 Azure 的云服务的 ExpressRoute 的一些优点：
  
- **可预知的性能：** 通过到 Microsoft 云边缘的专用路径，你的性能不会受限于 Internet 提供商中断和 Internet 流量高峰。你可以确定并让提供商负责到 Microsoft 云的吞吐量和延迟 SLA。
    
- **流量的数据隐私：** 通过专用 ExpressRoute 连接发送的流量不会受限于恶意用户的 Internet 监视或数据包捕获和分析。这与使用基于多协议标签交换 (MPLS) 的 WAN 链接一样安全。
    
- **高吞吐量连接：** 由于 Exchange 提供商和网络服务提供商提供的广泛的 ExpressRoute 连接支持，你最多可以获得 Microsoft 云的 10 Gbps 链接。
    
- **降低某些配置的成本：** 虽然 ExpressRoute 连接花费额外的成本，但在某些情况下，与在组织的多个地点增加 Internet 容量相比，一次 ExpressRoute 连接花费的成本更低，可以为 Microsoft 云服务提供足够的吞吐量。
    
ExpressRoute 连接不能保证每一种配置的性能都会提高。通过低带宽 ExpressRoute 连接实现的性能比高带宽 Internet 连接低，在后一种情况下，与区域性 Microsoft 数据中心仅隔几个跃点。
  
有关使用适用于 Office 365 的 ExpressRoute，请参阅[适用于 Office 365 的 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)。
  
## ExpressRoute 连接模型

表 1 显示了用于 ExpressRoute 连接的三种主要连接模型。
  
|**在云交换中归置**|**点到点的以太网**|**任意对任意的 (IP VPN) 连接**|
|:-----|:-----|:-----|
|![ExpressRoute 连接模型：在云交换中归置](images/415cd5b2-2b5a-4aeb-8018-8af61d9f9ab6.png)|![ExpressRoute 连接模型：点到点的以太网](images/0582afa7-b46d-4da9-80ff-f0553ac93676.png)|![ExpressRoute 连接模型：任意对任意的 (IP VPN) 连接](images/2884618e-ff38-471a-a1e0-fd55483938e5.png)|
|如果你的数据中心与云交换共同位于某设施内，你可以通过归置提供程序的以太网交换订购到 Microsoft 云的虚拟交叉连接。  <br/> |如果你的数据中心位于你的场所，你可以使用点对点以太网链路连接到 Microsoft 云。  <br/> |如果你已使用 IP VPN (MPLS) 提供程序连接组织的站点，到 Microsoft 云的 ExpressRoute 连接可以用作专用 WAN 中的另一个位置。  <br/> |
   
 **表 1：ExpressRoute 连接模型**
  
## ExpressRoute 与 Microsoft 云服务的对等关系

一个 ExpressRoute 连接最多支持三个不同的边界网关协议 (BGP) 与 Microsoft 云不同部分的对等关系。BPG 使用对等关系建立信任和交换路由信息。
  
**图 3：单个 ExpressRoute 连接中的三个不同的 BGP 关系**

![图 3：单次 ExpressRoute 连接中的三个不同的 BGP 关系](images/f16e3eaf-9fd5-4513-9a15-dcf66f07756f.png)
  
图 3 显示了内部部署网络中的 ExpressRoute 连接。ExpressRoute 连接中包含三个逻辑对等关系。Microsoft 对等关系转到 Microsoft SaaS 服务，其中包括 Office 365 和 Dynamcs CRM Online。公共对等关系转到 Azure PaaS 服务。专用的对等关系转到 Azure IaaS 和承载虚拟机的虚拟网络网关。
  
Microsoft 对等 BGP 关系： 
  
- 是从 DMZ 中的某个路由器到 Office 365 和 Dynamics 365 服务的公用地址。 
    
- 支持双向启动的通信。
    
公共对等 BGP 关系：
  
- 是从 DMZ 中的某个路由器到 Azure 服务的公用 IP 地址。
    
- 仅支持从内部部署系统中单向启动的通信。对等关系不支持从 Azure PaaS 服务启动的通信。
    
专用的对等 BGP 关系：
  
- 是从组织网络边缘上的某个路由器到分配给 Azure VNets 的专用 IP 地址。
    
- 支持双向启动的通信。
    
- 是从组织网络到 Microsoft 云的扩展，配有内部一致的寻址和路由。
    
## 通过 ExpressRoute 的应用程序部署和流量的示例

流量如何流经 ExpressRoute 连接和在 Microsoft 云中传输，相当于来源与目标之间的路径跃点的路由，是一种应用程序的行为。下面是在 Azure 虚拟机上运行的应用程序的一个示例，它通过站点到站点 VPN 连接访问内部部署 SharePoint 场。
  
**图 4：Azure 虚拟机上的访问本地 SharePoint 场的应用程序**

![图 4：Azure 虚拟机上的访问本地 SharePoint 场的应用程序](images/293dbdb7-e8f6-4399-8fdd-b7e4d0b33e66.png)
  
图 4 显示了内部部署 SharePoint 场、内部部署网络和 Azure IaaS 中的虚拟网络之间的站点到站点 VPN 连接、作为 Azure IaaS 虚拟机运行的应用程序服务器，以及应用程序服务器和 SharePoint 场之间的流量。
  
应用程序使用内部部署 DNS 查找 SharePoint 场的 IP 地址，所有流量都要通过站点到站点 VPN 连接。
  
该组织将内部部署 SharePoint 场迁移到了 Office 365 中的 SharePoint Online 并部署了 ExpressRoute 连接。
  
**图 5：将本地 SharePoint 场移至 SharePoint Online**

![图 5：将本地 SharePoint 场迁移到 SharePoint Online](images/d2140875-5fd3-44ce-b863-e93ad8680038.png)
  
图 5 显示将带有对等关系的 ExpressRoute 连接添加到 Microsoft SaaS 和 Office 365 以及 Azure IaaS 中，其中包含虚拟网络上的应用程序服务器。SharePoint 内部部署场已迁移至 Office 365。
  
具有 Microsoft 和专用对等关系：
  
- 从 Azure 虚拟网络网关中，内部部署位置可通过 ExpressRoute 连接提供。
    
- 从 Office 365 订阅中，边缘设备的公用 IP 地址（如代理服务器）可通过 ExpressRoute 连接提供。
    
- 从内部部署网络边缘中，Azure VNet 的专用 IP 地址和 Office 365 的公用 IP 地址可通过 ExpressRoute 连接提供。
    
当应用程序访问 SharePoint Online 的 URL 时，它通过 ExpressRoute 连接将其流量转发到边缘的代理服务器。 
  
当代理服务器找到 SharePoint Online 的 IP 地址时，它将通过 ExpressRoute 连接转发回流量。响应流量通过反向路径。
  
**图 6：SharePoint 场迁移到 Office 365 中的 SharePoint Online 时的流量**

![图 6：SharePoint 场迁移到 Office 365 中的 SharePoint Online 时的流量](images/30623d29-a9e6-4d38-bb7a-683adcea3395.png)
  
图 6 显示了应用程序服务器和 Office 365 中的 SharePoint Online 之间的流量如何通过专用的对等关系从应用程序服务器流到内部部署网络边缘，然后通过 Microsoft 对等关系从边缘流到 Office 365。
  
其结果是出现 Hairpinning 模式，这是路由和应用程序行为导致的后果。
  
## ExpressRoute 和 Microsoft 云网络

ExpressRoute 连接具有两个不同的版本：ExpressRoute 和 ExpressRoute Premium。
  
### ExpressRoute

组织网络与 Microsoft 数据中心之间的流量的流动方式取决于下列各项：
  
- 你的位置。
    
- Microsoft 云对等位置（连接到 Microsoft 边缘的物理位置）。
    
- Microsoft 数据中心位置。
    
Microsoft 数据中心和云对等位置都连接到 Microsoft 云网络。
  
创建到 Microsoft 云对等位置的 ExpressRoute 连接时，将你连接到 Microsoft 云网络以及同一个洲的所有 Microsoft 数据中心位置。云对等位置和目标 Microsoft 数据中心之间的流量通过 Microsoft 云网络传送。
  
这可能会导致任意对任意连接模型的本地 Microsoft 数据中心的传送达不到最佳状态。
  
**图 7：使用单个 ExpressRoute 连接的地理位置分散的组织示例**

![图 7：使用单次 ExpressRoute 连接的地理位置分散的组织的示例](images/f0c19a74-d67c-42de-8b1a-a122729b4abb.png)
  
图 7 显示了具有两个位置的组织：美国西北部的位置 1 和东北部的位置 2。它们由任意对任意 WAN 提供程序连接。该组织还有到西海岸的 Microsoft 对等位置的 ExpressRoute 连接。来自东北部的位置 2 且发往东海岸数据中心的流量，必须一直流经组织的 WAN 直到西海岸、Microsoft 对等位置，然后通过 Microsoft 云网络流经全国，返回东海岸数据中心。
  
为实现最佳的传送，使用到区域性 Microsoft 云对等位置的多个 ExpressRoute 连接。 
  
**图 8：使用多个 ExpressRoute 连接实现到区域性数据中心的最佳传送**

![图 8：使用多个 ExpressRoute 连接实现到区域性数据中心的最佳传送](images/e6980050-48ee-41f7-9f81-7953e783ee1b.png)
  
图 8 显示了使用到本地 Microsoft 对等位置的两个 ExpressRoute 连接的同一组织，一个连接针对一个位置。在此配置中，来自东北部的位置 2 且发往东海岸数据中心的流量，会直接流至东海岸的对等位置、Microsoft 云网络，然后再到东海岸数据中心。
  
多个 ExpressRoute 连接可以：
  
- 提高本地 Microsoft 数据中心位置的性能。
    
- 在本地 ExpressRoute 连接不可用时提高 Microsoft 云的可用性。
    
这适用于在同一个洲的组织。但是，到该组织所在洲之外的 Microsoft 数据中心的流量将通过 Internet 传送。
  
对于通过 Microsoft 云网络的洲际流量，则必须使用 ExpressRoute Premium 连接。
  
### ExpressRoute Premium

对于分布在各洲的组织，你可以使用 ExpressRoute Premium。 
  
通过 ExpressRoute Premium，可以从任何洲的任何 Microsoft 对等位置到达任何洲的任何 Microsoft 数据中心。洲之间的流量通过 Microsoft 云网络传送。
  
通过多个 ExpressRoute Premium 连接，你可以：
  
- 提高洲本地 Microsoft 数据中心位置的性能。
    
- 在本地 ExpressRoute 连接不可用时提高全局 Microsoft 云的可用性。
    
基于 Office 365 的 ExpressRoute 连接需要 ExpressRoute Premium。但是，拥有 500 名或更多授权用户的企业不需要额外成本。
  
**图 9：全球范围内的 Microsoft 云网络**

![图 9：全球范围内的 Microsoft 云网络](images/c65c740a-f20c-4c77-b3b2-624b39ef0aa3.png)
  
图 9 显示了全球范围的 Microsoft 云网络的逻辑图，其中网络跨越世界各洲和区域以及它们之间的互连。每个洲都包含部分 Microsoft 云网络，全球企业从其区域中心办事处创建到本地 Microsoft 对等位置的 ExpressRoute Premium 连接。
  
对于区域办事处，适当的 Office 365 流量：
  
- 通过该洲内的 Microsoft 云网络传送至 Office 365 洲数据中心。
    
- 通过洲际 Microsoft 云网络传送至另一个洲的Office 365 数据中心。
    
有关详细信息，请参阅：
  
- [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer/)（Azure ExpressRoute for Office 365 培训）
    
- [Office 365 的网络规划和性能调整 365](https://aka.ms/tune)
    
- [Office 365 Performance Management](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)（Office 365 的性能管理）
    
## ExpressRoute 选项

你也可以将以下选项纳入到 ExpressRoute 部署中：
  
- **边缘的安全性：** 要实现通过 ExpressRoute 连接发送和接收的流量的高级安全性，如流量检查或入侵/恶意软件检测，请将安全装置放入 DMZ 内的流量路径下或 Intranet 边界。
    
- VM 的 Internet 流量 为防止 Azure VM 直接启动与 Internet 位置的流量，请将默认路由告知 Microsoft。Internet 流量通过 ExpressRoute 连接和内部部署代理服务器传送。从 Azure 虚拟机到 Azure PaaS 服务或 Office 365 的流量将通过 ExpressRoute 连接传送回去。
    
- **WAN 优化程序：** 你可以在跨界部署的 Azure 虚拟网络 (VNet) 的专用对等连接两端部署 WAN 优化程序。在 Azure VNet 内部，使用 Azure 市场的 WAN 优化网络设备和用户定义路由通过该设备传送流量。
    
- **服务质量：** 使用流量的 IPv4 标头中的差分服务代码点 (DSCP) 值将其标记为语音、视频/交互式或尽力传送。这对 Microsoft 对等关系以及 Skype for Business Online 流量尤为重要。
    
有关详细信息，请参阅下列更多资源：
  
- [面向 Office 365 的 ExpressRoute](https://aka.ms/expressrouteoffice365)
    
- [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer/)（Azure ExpressRoute for Office 365 培训）
    
- [ExpressRoute for Azure](https://azure.microsoft.com/services/expressroute/)（面向 Azure 的 ExpressRoute）
    
## See Also

#### 

[面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
#### 

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)

