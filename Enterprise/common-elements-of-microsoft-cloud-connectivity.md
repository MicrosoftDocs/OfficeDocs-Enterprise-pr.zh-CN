---
title: "Microsoft 云连接的公共元素"
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
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "摘要： 了解网络基础结构的常见元素，以及如何准备你的网络。"
---

# Microsoft 云连接的公共元素

 **摘要：** 了解网络基础结构的常见元素，以及如何准备你的网络。
  
将你的网络与 Microsoft 云进行集成可提供对范围更为广泛的服务的最佳访问。
  
## 为 Microsoft 云服务准备网络的步骤
<a name="steps"> </a>

对于你的内部部署网络：
  
1. 分析客户端计算机，并针对网络硬件、软件驱动程序、协议设置和 Internet 浏览器进行优化。
    
2. 分析你的内部部署网络，了解到 Internet 边缘设备的流量延迟和最佳路由。
    
3. 分析 Internet 边缘设备的容量和性能，并进行优化以提高流量级别。
    
对于 Internet 连接：
  
1. 分析 Internet 边缘设备（如外部防火墙）与你连接到的 Microsoft 云服务的区域位置之间的延迟。
    
2. 分析当前 Internet 连接的容量和利用率，并在需要时增加容量。或者，添加 ExpressRoute 连接。
    
## Microsoft 云连接选项
<a name="steps"> </a>

使用现有的 Internet 管道或到 Office 365、Azure 和 Dynamics 365 的 ExpressRoute 连接。
  
**图 1：Microsoft 云连接选项**

![图 1：Microsoft 云连接选项](images/594b3a80-2c32-4402-bdee-e85cd25c0b2f.png)
  
图 1 显示内部部署网络如何使用其现有的 Internet 管道或 ExpressRoute 连接到 Microsoft 云服务。Internet 管道表示 DMZ，并且可以具有下列组件：
  
- **内部防火墙：** 受信任的网络与不受信的网络任之间的屏障。执行流量筛选（基于规则）和监视。
    
- **外部工作负载：** 网站或其他工作负载供 Internet 上的外部用户使用。
    
- **代理服务器：** 代表 Intranet 用户发出的对 Web 内容的服务请求。反向代理服务器允许未经请求的入站请求。
    
- **外部防火墙：** 允许出站流量和指定的入站流量。可以执行地址转换。
    
- **到 ISP 的 WAN 连接：** 到 ISP 的基于载波的连接，与 Internet 对等，可以实现连接和传送。
    
## 对所有 Microsoft 云服务通用的网络区域
<a name="steps"> </a>

采用 Microsoft 的任何云服务时，必须将这些网络区域考虑在内。
  
- **Intranet 性能：** 如果不优化 Intranet（其中包括客户端计算机），基于 Internet 的资源的性能就会受损。
    
- **边缘设备：** 网络边缘的设备用作出口点，可以包括网络地址转换器 (NAT)、代理服务器（包括反向代理服务器）、防火墙、入侵检测设备或这些项的组合。
    
- **Internet 连接：** 到 ISP 和 Internet 的 WAN 连接应具有足够的容量来处理峰值负载。你也可以使用 ExpressRoute 连接。
    
- **Internet DNS：** A、AAAA、CNAME、MX、PTR 和其他记录，可以查找 Microsoft 云或你在云中托管的服务。例如，可能需要你在 Azure PaaS 中托管的应用程序的 CNAME 记录。
    
## See Also
<a name="steps"> </a>

#### 

[面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
#### 

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)

