---
title: Contoso Corporation 的网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: 摘要： 了解 Contoso 网络基础结构以及它如何为优化访问与 Microsoft 的云产品使用 ExpressRoute。
ms.openlocfilehash: 89d4182d8a5ef44f936977ec51cc002b51f4b379
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915217"
---
# <a name="networking-for-the-contoso-corporation"></a>Contoso Corporation 的网络

 **摘要：** 了解 Contoso 网络基础结构以及它如何为优化访问与 Microsoft 的云产品使用 ExpressRoute。
  
采用云之间的基础结构，Contoso 的网络工程师意识到的网络到基于云的服务旅行的通信方式根本性转变。而不是仅优化到内部部署服务器和数据中心的通信，必须对优化通信到 Internet 边缘通过 Internet 支付等于注意。
  
## <a name="contosos-networking-infrastructure"></a>Contoso 的网络基础结构

Contoso 具有以下网络基础结构，如图 1 所示。
  
**图 1：Contoso 的 WAN 基础结构**

![链接总部、区域中心和分支办事处的 Contoso WAN 基础结构](media/Contoso-Poster/Contoso-WW-Net.png)
  
图 1 显示 Contoso 在全球的办事处以及他们之间的区域办事处和分支办事处 WAN 链接组。
  
其他网络元素如下：
  
- 本地网络
    
    WAN 链接连接到地区办事处和给附属的分支和集线器传输配置办事处的地区办事处巴黎总部。内每个办公室，路由器到主机或在使用专用 IP 地址空间的子网无线访问点提供流量。
    
- Internet 连接
    
    每个办事处有其自己的 Internet 连接通过代理服务器。这通常作为 WAN 链接到本地 ISP 还提供公共 IP 地址的代理服务器。
    
- Internet 展示
    
    Contoso 拥有 contoso.com 公共域名。Contoso 公共网站订购产品是一套巴黎所高校中连接到 Internet 的数据中心中的服务器。Contoso 使用 / 24 Internet 上的公用 IP 地址范围。
    
## <a name="contosos-app-infrastructure"></a>Contoso 的应用程序基础结构

针对以下情况，Contoso 构建了其应用程序和服务器基础结构：




  
**图 2：Contoso 内部应用程序的基础结构**

![Contoso 内部应用程序的基础结构](media/Contoso-Poster/App-Infra.png)
  
- 分支办事处使用本地缓存服务器存储经常访问的文档和内部网站。
    
- 
区域中心将区域应用程序服务器用于区域办事处和分支办事处。这些服务器与巴黎总部的服务器同步。
    
- 巴黎园区拥有的数据中心包含为整个组织提供服务的集中式应用程序服务器。
    
对于分支办事处或区域中心办事处的用户，员工所需资源的 60% 可由分支办事处和区域中心办事处服务器提供。其他 40% 的资源请求则必须通过 WAN 链接到巴黎园区。
  
## <a name="contosos-network-analysis"></a>Contoso 的网络分析

下面是分析的在他们的网络上适应不同类别的 Microsoft 云服务所需的更改的 Contoso 的结果：
  
|**Saas 与云产品： Office 365、 EMS 和 Dynamics 365**|**Azure PaaS： 移动应用程序**|**Azure IaaS： 基于服务器的工作负荷**|
|:-----|:-----|:-----|
|用户能成功利用 SaaS 服务，要依赖于高可用性和高性能的 Internet 连接或直接到 Microsoft 云服务的连接。
  <br/> 对于移动用户，假定他们当前的 Internet 访问权限足够。
  <br/> 对于 Contoso intranet 上的用户，必须分析并针对到 Internet 的吞吐量和到 Microsoft 的欧洲数据中心托管 Office 365、 EMS 和 Dynamics 365 租户的往返时间优化每个办公室。  <br/> |为更好地支持移动工作人员，旧版应用和一些文件共享站点被修改并部署成了 Azure PaaS 应用。为获得最佳性能，Contoso 计划在全球的多个 Azure 数据中心部署新应用。Azure 流量管理器将客户端应用请求发送到最近的托管应用的 Azure 数据中心，无论它们源自移动用户还是办事处的计算机。  <br/>   

IT 部门将需要为其网络运行状况监视解决方案添加 PaaS 应用程序性能和流量分发。 <br/> |要将一些旧版和存档服务器从巴黎园区数据中心移出并根据需要添加服务器以进行季度末处理，Contoso 计划使用在 Azure 基础结构服务中运行的虚拟机。 

  <br/> 包含这些服务器的 Azure 虚拟网络必须为非重叠地址空间、路由和集成 DNS 进行设计。

  <br/> IT 部门的网络管理和监视系统中必须包含这些新的服务器。  <br/> |
   
## <a name="contosos-use-of-expressroute"></a>ExpressRoute Contoso 的使用

ExpressRoute 是从您的位置到您的网络连接到 Microsoft 云网络的 Microsoft 对等位置的专用 WAN 连接。ExpressRoute 连接提供可预测的性能和 99.9%正常运行时间 SLA。.
  
使用 ExpressRoute 连接时，系统会将您连接到 Microsoft 云网络和相同洲中的所有 Microsoft 数据中心位置。云对等位置和目标 Microsoft 数据中心之间的通信转移 Microsoft 云网络
  
**图 3：全球范围内的 Microsoft 云网络**

![全球范围内的 Microsoft 云网络](media/Contoso-Poster/MS-WW-Cloud.png)
  
图 3 显示针对世界上不同区域的互联 Microsoft 云网络。
  
通过 ExpressRoute Premium，可以从任何洲的任何 Microsoft 对等位置到达任何洲的任何 Microsoft 数据中心。洲之间的流量通过 Microsoft 云网络传送。
  
根据当前和将来流量 Microsoft 云服务的分析，Contoso 具有执行网络评估，并实现与私钥和公钥对等的 Azure 资源的访问权的任意到任意 （基于 MPLS） ExpressRoute 连接从 Microsoft 对等位置在欧洲巴黎总部的关系。
  
此连接将为 Contoso 的 IT 部门提供：
  
- 管理分布式 Azure PaaS 应用的一致性能
    
    所有的 Contoso 的应用程序开发人员和核心基础结构 IT 管理员是巴黎所高校中。使用 Azure PaaS 应用程序分发给不同世界各地的 Azure 数据中心，Contoso 需要从管理的应用程序以及其存储资源，从而包含的文档的 TB 巴黎校园一致的性能。
    
- 具有管理 Azure IaaS 中服务器的一致性能
    
    Contoso 的数据中心管理员位于巴黎校园和 Azure 中部署的服务器是巴黎数据中心的扩展。对于访问旧版应用程序和存档存储和结束的季度处理，Contoso 需要一致到这些新的服务器的性能。
    
## <a name="contosos-path-to-cloud-networking-readiness"></a>Contoso 的路径云网络准备情况

Contoso 使用以下步骤为 Microsoft 云网络做准备：
  
1. 优化用于 Internet 访问的员工计算机

    
    检查每台计算机，确保安装了最新的 TCP/IP 堆栈、浏览器、NIC 驱动程序及安全性和操作系统更新。
    
2. 分析每个办事处的 Internet 连接利用率，并根据需要增加带宽
    
    
如果在利用率达 70% 或以上的情况下运行，将分析每个办事处的当前 Internet 使用情况，并增加 WAN 链接带宽。
    
3. 分析每个办事处的 DMZ 系统以获得最佳性能

    
    分析防火墙、IDS 和 Internet 路径中的其他系统以获得最佳性能。代理服务器将根据需要更新或升级。
    
4. 为巴黎园区添加 ExpressRoute
    
    提供对 Azure 资源的一致访问权限以管理 Azure PaaS 和 IaaS 工作负载。
    
5. 为 Azure PaaS 应用创建和测试 Azure 流量管理器配置文件
    
    测试 Azure 流量管理器配置文件，该配置文件使用性能路由方法来获得将 Internet 流量分发到区域位置的体验。
    
6. 为 Azure VNet 保留专用地址空间

    
    根据 Azure IaaS 中计划的短期和长期服务器数，为 Azure VNet 及其子网保留专用地址空间。
    
## <a name="see-also"></a>See Also

[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



