---
title: "Microsoft 混合云方案的体系结构"
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
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "摘要： 了解 Microsoft 混合云产品的体系结构。"
ms.openlocfilehash: 33d98d88a10b18cdd357250f46c5414f1c1b6a75
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2018
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Microsoft 混合云方案的体系结构

 **摘要：** 了解 Microsoft 混合云产品的体系结构。
  
使用体系结构方法通过 Microsoft 云服务及平台来计划和实施混合云方案。
  
**图 1：Microsoft 混合云堆栈**

![Microsoft 混合云堆叠](images/Hybrid_Poster/Hybrid_Cloud_Stack.png)
  
图 1 显示了 Microsoft 混合云堆栈及其层，包括内部部署、网络、标识、应用程序和方案，以及云服务（Microsoft SaaS、Azure PaaS 和 Azure PaaS）的类别。
  
应用程序和方案层包含本模型中其他文章中详述的特定混合云方案。标识、网络和本地层可与云服务（SaaS、PaaS 或 PaaS）类别共用。
  
- 本地
    
    混合方案的本地基础结构可包括适用于 SharePoint、Exchange、Skype for Business 和业务线应用程序的服务器。它还可以包括数据存储（数据库、列表、文件）。如果没有 ExpressRoute 连接，必须允许通过反向代理或使服务器或数据可从 DMZ 或 Extranet 上访问来访问本地数据存储。
    
- 网络
    
    连接到 Microsoft 云平台和服务有两种选择：现有的 Internet 管道和 ExpressRoute。如果可预知的性能非常重要，请使用 ExpressRoute 连接。可以使用一个 ExpressRoute 连接直接连接到 Microsoft SaaS 服务（Office 365 和 Dynamics 365）、Azure PaaS 服务和 Azure IaaS 服务。
    
- 标识
    
    对于云标识基础结构，根据 Microsoft 云平台的不同有两种方式可选。对于 SaaS 和 Azure PaaS，将本地标识基础结构与 Azure AD 集成，或与本地标识基础结构或第三方标识提供程序联合。对于在 Azure 中运行的 VM，可以将本地标识基础结构（如 Windows Server AD）扩展到 VM 驻留的虚拟网络 (VNet)。
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>用于三阶段云应用流程的混合云方案

许多企业（包括 Microsoft 的企业）都使用三阶段方法来应用云。混合云方案可以在每个阶段发挥作用。
  
1. 将工作效率工作负荷移动到 SaaS
    
    对于当前位于或必须保持在本地的工作效率工作负荷，混合方案允许其与对应的云集成。
    
2. 在 Azure PaaS 中开发新的和现代应用程序
    
    Azure PaaS 混合应用程序可以安全地利用本地服务器或存储资源。
    
3. 将现有应用程序移动到 Azure IaaS
    
    对于提升转移以及内置云方案，在 Azure VM 上运行的基于服务器的应用程序提供了便利的预配和缩放功能。
    
## <a name="see-also"></a>另请参阅

[面向企业架构师的 Microsoft 混合云](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)



