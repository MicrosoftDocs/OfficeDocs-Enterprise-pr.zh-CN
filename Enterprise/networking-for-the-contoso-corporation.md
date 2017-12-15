---
title: "Contoso Corporation 的网络"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: "摘要： 了解 Microsoft 混合云的定义和元素。"
ms.openlocfilehash: 115a4844d96c1d027fd63e7d91f02cbadeb975d9
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="networking-for-the-contoso-corporation"></a>Contoso Corporation 的网络

 **摘要：** 了解 Microsoft 混合云的定义和元素。
  
采用含云基础结构，Contoso 网络工程师认识到以网络通信为基于云的服务旅游方式的根本转变。而不是只优化内部部署服务器和数据中心的通信，篇幅必须支付到优化到 Internet 边缘和互联网之间的通信。
  
## <a name="contosos-networking-infrastructure"></a>Contoso 网络基础结构

Contoso 具有以下网络基础结构，如图 1 所示。
  
**图 1: Contoso 的 WAN 基础结构**

![链接总部、区域中心和分支办事处的 Contoso WAN 基础结构](images/Contoso_Poster/Contoso_WW_Net.png)
  
图 1 显示 Contoso 在全球的办事处以及他们之间的区域办事处和分支办事处 WAN 链接组。
  
其他网络元素如下：
  
- 本地网络
    
    WAN 链接连接到地区办事处和区域办事处设有分公司，在分散和集中配置到巴黎总部。内每个办公室，路由器将通信传递到主机或子网，使用专用的 IP 地址空间在无线访问点。
    
- Internet 连接
    
    每个办公室都有它自己的互联网连接通过代理服务器。这通常实现为 WAN 链接到本地 ISP 还提供代理服务器的公用 IP 地址。
    
- Internet 展示
    
    Contoso 拥有 contoso.com 公共域名。Contoso 公共 web 站点订购产品是一套在巴黎校园互联网连接数据中心中的服务器。Contoso 使用 / 24 上互联网的公用 IP 地址范围。
    
## <a name="contosos-app-infrastructure"></a>Contoso 的应用程序基础结构

Contoso 已构建以下为其应用程序和服务器基础架构：
  
**图 2: Contoso 的内部应用程序基础结构**

![Contoso 内部应用程序的基础结构](images/Contoso_Poster/App_Infra.png)
  
- 分支办事处使用本地缓存服务器存储经常访问的文档和内部网站。
    
- 区域性中心使用区域的区域的应用程序服务器和卫星办公室。这些服务器中的巴黎总部的服务器同步。
    
- 巴黎园区拥有的数据中心包含为整个组织提供服务的集中式应用程序服务器。
    
对于分支办事处或区域中心办事处的用户，员工所需资源的 60% 可由分支办事处和区域中心办事处服务器提供。其他 40% 的资源请求则必须通过 WAN 链接到巴黎园区。
  
## <a name="contosos-network-analysis"></a>Contoso 网络分析

以下是分析的可容纳不同类别的微软云服务在其网络上所需的更改 Contoso 结果：
  
|**SaaS 云产品： Office 365、 EMS 和 Dynamics 365**|**Azure 的 PaaS： 移动应用程序**|**Azure IaaS： 基于服务器的工作负载**|
|:-----|:-----|:-----|
|成功利用云的 SaaS 服务的用户依赖于高可用性和性能连接到 Internet，或直接向 Microsoft 云服务。  <br/> 对于移动用户，假定他们当前的互联网访问是足够的。  <br/> Contoso intranet 上的用户，必须分析并针对互联网吞吐量和微软欧洲数据中心承载 Office 365、 EMS 和 Dynamics 365 承租人对往返时间优化每个办公室。  <br/> |为更好地支持移动工作人员，旧版应用和一些文件共享站点被修改并部署成了 Azure PaaS 应用。为获得最佳性能，Contoso 计划在全球的多个 Azure 数据中心部署新应用。Azure 流量管理器将客户端应用请求发送到最近的托管应用的 Azure 数据中心，无论它们源自移动用户还是办事处的计算机。  <br/>  IT 部门需要添加到其网络的运行状况监视解决方案的 PaaS 应用程序性能和流量分布。 <br/> |要移动从巴黎校园数据中心一些旧式和存档服务器并根据需要进行季度末处理添加服务器，Contoso 计划使用 Azure 的基础结构服务中运行的虚拟机。  <br/> 必须为非重叠地址空间，布线和集成 DNS 设计包含这些服务器的 Azure 的虚拟网络。  <br/> IT 部门的网络管理和监视系统中必须包含这些新的服务器。  <br/> |
   
## <a name="contosos-use-of-expressroute"></a>Contoso 的使用的 ExpressRoute

ExpressRoute 是从您所在的位置到 Microsoft 对等位置，将您的网络连接到 Microsoft 云网络的专用 WAN 连接。ExpressRoute 连接提供了可预知的性能和 99.9%正常运行时间 SLA。.
  
使用 ExpressRoute 连接时，系统会将您连接到 Microsoft 云网络，并在同一个洲所有 Microsoft 数据中心位置。在 Microsoft 云网络上执行了云对等位置和目标 Microsoft 数据中心之间的通信
  
**图 3: Microsoft 云网络全球**

![全球范围内的 Microsoft 云网络](images/Contoso_Poster/MS_WW_Cloud.png)
  
图 3 显示针对世界上不同区域的互联 Microsoft 云网络。
  
通过 ExpressRoute Premium，可以从任何洲的任何 Microsoft 对等位置到达任何洲的任何 Microsoft 数据中心。洲之间的流量通过 Microsoft 云网络传送。
  
根据当前和未来通信与微软云产品的分析，Contoso 已执行网络评估，并实现任意到任意的 （基于 MPLS 的） ExpressRoute 连接以访问具有私钥和公钥对等的 Azure 资源从巴黎总部在欧洲的 Microsoft 对等位置的关系。
  
此连接将为 Contoso 的 IT 部门提供：
  
- 管理分布式 Azure PaaS 应用的一致性能
    
    所有 Contoso 的应用程序开发人员和核心基础架构 IT 管理员正在巴黎校园。与 Azure PaaS 应用程序分发到世界各地不同的 Azure 数据中心，Contoso 需要一致的性能，从巴黎校园管理应用程序和存储资源，其中包括 TB 的文档。
    
- 具有管理 Azure IaaS 中服务器的一致性能
    
    Contoso 的数据中心管理员正在巴黎校园并且在 Azure 中部署的服务器是巴黎数据中心的扩展。对于旧式应用程序并归档存储访问和结束的季度处理，Contoso 需要一致到这些新服务器的性能。
    
## <a name="contosos-path-to-cloud-networking-readiness"></a>Contoso 的路径来云网络的准备工作

Contoso 使用以下步骤为 Microsoft 云网络做准备：
  
1. 优化员工计算机互联网接入
    
    检查每台计算机，确保安装了最新的 TCP/IP 堆栈、浏览器、NIC 驱动程序及安全性和操作系统更新。
    
2. 分析每个办事处的 Internet 连接利用率，并根据需要增加带宽
    
    每个办公室将分析当前互联网使用和 WAN 链路带宽运行 70%或以上的使用率将增加。
    
3. 分析 DMZ 系统在每个办公室以获得最佳性能
    
    分析防火墙、IDS 和 Internet 路径中的其他系统以获得最佳性能。代理服务器将根据需要更新或升级。
    
4. 为巴黎园区添加 ExpressRoute
    
    提供对 Azure 资源的一致访问权限以管理 Azure PaaS 和 IaaS 工作负载。
    
5. 为 Azure PaaS 应用创建和测试 Azure 流量管理器配置文件
    
    测试 Azure 流量管理器配置文件，该配置文件使用性能路由方法来获得将 Internet 流量分发到区域位置的体验。
    
6. Azure VNets 保留专用地址空间
    
    根据 Azure IaaS 中计划的短期和长期服务器数，为 Azure VNet 及其子网保留专用地址空间。
    
## <a name="see-also"></a>See Also

[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



