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
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872263"
---
# <a name="designing-networking-for-microsoft-saas"></a>为 Microsoft SaaS 设计网络

 **摘要：** 了解如何优化网络以便访问 Microsoft SaaS 服务，包括 Office 365、Microsoft Intune 和 Dynamics 365。
  
优化您的 Microsoft saas 与服务的网络要求配置内部和边缘设备，可将不同类别的流量路由到 Microsoft SaaS 服务。
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>为 Microsoft SaaS 服务准备网络的步骤

按照这些步骤执行操作，为 Microsoft SaaS 服务优化你的网络：
  
1. 完成 [Microsoft 云连接的常见元素](common-elements-of-microsoft-cloud-connectivity.md)中的**为 Microsoft 云服务准备网络的步骤**部分。
    
2. 添加到每个办事处 Internet 连接。
    
3. 确保所有 Internet 连接的 Isp 与本地 IP 地址使用 DNS 服务器。
    
4. 检查您的网络 hairpins、 基于云的安全服务，如中间目标，并将其删除如果可能。
    
5. 配置边缘设备以绕过优化的处理，允许类别的 Microsoft SaaS 流量。

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>优化与 Microsoft 的 saas 与服务的流量    

有三种类别的 Microsoft SaaS 流量：

- 优化

  所需的连接到每个 Microsoft SaaS 服务和表示超过 75%的 Microsoft SaaS 带宽、 连接和数据量。

- 允许

  所需的连接到特定 Microsoft SaaS services，和功能，但不为敏感网络性能和优化类别中的与延迟。

- 默认

  表示 Microsoft SaaS 服务和不需要任何优化的依赖关系。可以将像普通 Internet 通信的默认类别通信。


**图 1： 建议使用的所有办事处的 Microsoft SaaS 流量的配置**

![图 1： 建议使用的所有办事处的 Microsoft SaaS 流量的配置](media/Network-Poster/SaaS1.png)

图 1 显示了所有办公室，包括分支机构和区域或管理中心的在其中的建议的配置：

- **默认**类别和常规 Internet 流量路由到代理服务器和其他边缘设备来提供针对基于 Internet 的安全风险保护的办公室。
- **优化**和**允许**类别通信转发到最靠近 office 包含连接的用户，绕过代理服务器和其他边缘设备的 Microsoft 网络前端边缘直接。

分支机构中的软件定义广域网 (SD WAN) 的网络设备将流量分开，以便： 

- **默认**类别和常规前往通过 WAN 主干中央或区域 office Internet 通信。 
- **优化**和**允许**类别流量转到 ISP 提供本地 Internet 连接。
  
有关详细信息，请参阅：
  
- [网络连接原则](https://aka.ms/expressrouteoffice365)

- [Office 365 的网络和迁移规划](https://aka.ms/tune)
    
## <a name="next-step"></a>后续步骤

[为 Microsoft Azure PaaS 设计网络](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 云网络](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

