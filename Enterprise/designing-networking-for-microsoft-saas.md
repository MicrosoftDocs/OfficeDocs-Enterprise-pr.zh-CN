---
title: "为 Microsoft SaaS 设计网络"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "摘要： 了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。"
ms.openlocfilehash: 432789d03f5208a379dc2ab4f17f38f95223e10d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-saas"></a>为 Microsoft SaaS 设计网络

 **摘要：** 了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。
  
优化你的 Microsoft SaaS 服务网络需要认真分析 Internet 边缘、你的客户端设备和典型的 IT 运营状况。
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>为 Microsoft SaaS 服务准备网络的步骤

按照这些步骤执行操作，为 Microsoft SaaS 服务优化你的网络：
  
1. 经过[公共元素的 Microsoft 云连接](common-elements-of-microsoft-cloud-connectivity.md)中的**步骤来准备您网络上的 Microsoft 云服务**部分。
    
2. 使用代理服务器建议为 Microsoft SaaS 服务优化你的 Internet 出口。
    
3. 使用邻近度和位置建议优化 Internet 吞吐量。
    
4. 使用客户端使用注意事项优化客户端计算机以及它们所在的 Intranet 的性能。
    
5. 根据需要，使用 IT 操作注意事项优化数据迁移和同步的性能。
    
## <a name="internet-edge-considerations"></a>有关 Internet 边缘的注意事项

下面是优化你的 Internet 边缘和 Microsoft SaaS 服务吞吐量的一些注意事项。
  
**图 1：Microsoft SaaS 服务的连接选项**

![图 1：Microsoft SaaS 服务的连接选项](images/Network_Poster/SaaS1.png)
  
图 1 显示了通过 Internet 管道或 ExpressRoute 连接到 Microsoft SaaS 服务的本地网络。
  
下面是优化代理服务器的一些建议：
  
- 使用 WPAD、PAC 或 GPO 配置 Web 客户端
    
- 不要使用 SSL 拦截
    
- 使用 PAC 文件绕过 Microsoft SaaS 服务 DNS 名称的代理
    
- 允许 CRL/OCSP 验证流量
    
以下是需要检查的一些代理服务器瓶颈问题：
  
- 没有足够的持久连接 (Outlook)
    
- 容量不足
    
- 执行关闭网络评估
    
- 要求身份验证
    
- 不支持 UDP 流量 (Skype for Business)
    
这里是一些有关邻近度和位置的建议：
  
- 不要通过专用 WAN 传送 Internet 流量
    
- 对区域外用户使用区域内 DNS 和 Internet 流量
    
- 结合使用 ExpressRoute 与 Azure 服务以实现 Office 365 的高带宽和并发连接
    
以下是 Office 365 流量所需的出站端口：
  
- TCP 80（用于 CRL/OCSP 检查）
    
- TCP 443
    
- UDP 3478
    
- TCP 5223
    
- TCP 50000-59999
    
- UDP 50000-59999
    
## <a name="client-usage-considerations"></a>客户端使用注意事项

首先，配置你的客户端将使用的一套服务，例如：
  
- Azure Active Directory
    
- Office 365
    
  - Office 客户端应用
    
  - SharePoint Online
    
  - Exchange Online
    
  - Skype for Business
    
- Microsoft Intune
    
- Dynamics 365
    
对于你的客户端计算机，请确定下列因素：
  
- 任何时间（一天中的某个时间、季节性、使用高峰和低谷）的最大数量
    
- 高峰期所需的总带宽
    
- Internet 出口设备的延迟
    
- 原产地与数据中心归置地
    
对于每种类型的客户端（PC、智能电话、平板电脑），确保当前：
  
- 操作系统
    
- Internet 浏览器
    
- TCP/IP 堆栈
    
- 网络硬件
    
- 网络硬件的操作系统驱动程序
    
- 安装了更新和修补程序
    
此外，还要优化 Intranet 连接吞吐量（有线、无线或 VPN）。
  
有关详细信息，请参阅[与 Office 365 的 NAT 支持](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)。
  
有关使用适用于 Office 365 的 ExpressRoute，请参阅[适用于 Office 365 的 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)。
  
若要优化你的 Intranet 性能，请执行以下操作：
  
- 使用工具来衡量到 Internet 边缘设备（PsPing、Ping、Tracert、TraceTCP、网络监视器）的往返时间 (RTT)
    
- 使用流协议执行出口路径分析
    
- 对中间设备（年限、健康状况等）进行分析
    
有关详细信息，请参阅 [PsPing 工具](https://technet.microsoft.com/sysinternals/jj729731.aspx)。
  
## <a name="it-operations-considerations"></a>IT 操作的注意事项

下面是在 Microsoft SaaS 服务中运行 IT 工作负载时需要注意的一些事项。
  
### <a name="one-time-migrations"></a>一次性迁移

一次性迁移的示例包括基于云的应用程序或归档存储的批量数据传输。
  
若要优化你的网络以执行一次性迁移，请执行以下操作：
  
- 避免高峰期使用网络和计算机修补时间
    
- 应在尝试实际迁移前创建基线和执行测试、评估网络运行状况并解决问题
    
- 进行事后总结供以后迁移时参考
    
### <a name="ongoing-synchronizations"></a>持续同步

持续同步的示例有目录信息、设置或文件。
  
要优化你的网络以执行持续同步，请执行以下操作：
  
- 确保网络带宽监控系统已到位，解决或消除收集的错误
    
- 使用带宽监控结果来确定是否需要进行网络更改（向上/向外扩展、新电路或添加设备）
    
有关详细信息，请参阅：
  
- [Office 365 的网络和迁移规划](https://aka.ms/tune)
    
- [Office 365 性能管理 Microsoft Virtual Academy 课程](https://aka.ms/o365perf)
    
- [面向 Office 365 的 ExpressRoute](https://aka.ms/expressrouteoffice365)
    
## <a name="see-also"></a>See Also

[面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



