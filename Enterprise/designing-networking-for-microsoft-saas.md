---
title: 为 Microsoft SaaS 设计网络
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 摘要：了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487290"
---
# <a name="designing-networking-for-microsoft-saas"></a>为 Microsoft SaaS 设计网络

 **摘要：** 了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。
  
若要为 Microsoft SaaS 服务优化网络，需要将内部和边缘设备配置为把各种类别的流量路由至 Microsoft SaaS 服务。
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>为 Microsoft SaaS 服务准备网络的步骤

按照这些步骤执行操作，为 Microsoft SaaS 服务优化你的网络：
  
1. 完成 [Microsoft 云连接的常见元素](common-elements-of-microsoft-cloud-connectivity.md)中的**为 Microsoft 云服务准备网络的步骤**部分。
    
2. 向每个办公室添加 Internet 连接。
    
3. 确保所有 Internet 连接的 isp 都使用具有本地 IP 地址的 DNS 服务器。
    
4. 检查您的网络回流, 中间目标 (如基于云的安全服务), 并在可能的情况下将其删除。
    
5. 将您的边缘设备配置为绕过优化和允许 Microsoft SaaS 流量类别的处理。

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>优化到 Microsoft SaaS 服务的流量    

Microsoft SaaS 流量有三种类别:

- 优化

  与每个 microsoft saas 服务的连接所必需, 表示 microsoft saas 带宽、连接数和数据量的 75%。

- 允许

  需要连接到特定的 Microsoft SaaS 服务和功能, 但不像 "优化" 类别中的那样对网络性能和延迟敏感。

- 默认

  表示不需要进行任何优化的 Microsoft SaaS 服务和依赖项。 您可以处理默认类别通信, 如正常的 Internet 流量。


**图 1: 适用于所有办公室的 Microsoft SaaS 流量的建议配置**

![图 1: 适用于所有办公室的 Microsoft SaaS 流量的建议配置](media/Network-Poster/SaaS1.png)

图1显示了所有办事处的推荐配置, 包括分支机构和区域或中心, 其中:

- **默认**类别和常规 Internet 流量路由到具有代理服务器和其他边缘设备的办公室, 以针对基于 Internet 的安全风险提供保护。
- **优化**并**允许**将类别流量直接转发到离包含连接用户的 office 最近的 Microsoft 网络前端的边缘, 而不是代理服务器和其他边缘设备。

分支机构中软件定义的广域网络 (SD-WAN) 设备可单独进行通信, 以便: 

- **默认**类别和常规 Internet 流量通过 WAN 骨干转到中央或区域办公室。 
- **优化**和**允许**类别通信转到提供本地 Internet 连接的 ISP。
  
有关详细信息，请参阅：
  
- [网络连接原则](https://aka.ms/expressrouteoffice365)

- [Office 365 的网络和迁移规划](https://aka.ms/tune)
    
## <a name="next-step"></a>后续步骤

[为 Microsoft Azure PaaS 设计网络](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

