---
title: "Contoso Corporation 概述"
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
ms.assetid: 1de16e29-ac2e-40b5-bf13-9301a51e16a8
description: "摘要： 了解 Contoso 公司业务以及其世界各地办事处的分层的结构。"
ms.openlocfilehash: 6243f6d6e5c08342cae7650d0b4e75de27ed3527
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="overview-of-the-contoso-corporation"></a>Contoso Corporation 概述

 **摘要：**了解 Contoso 公司业务以及其世界各地办事处的分层的结构。
  
Contoso Corporation 是一家总部位于法国巴黎的全球性企业。它是一家集制造、销售和支持为一体的大型组织，提供 100,000 多种产品。  
  
## <a name="the-contoso-corporation"></a>Contoso Corporation

Contoso 的全球公司设有办事处，在下列位置：
  
**图 1: Contoso 在世界各地的办事处**

![Contoso Corporation 在世界各地的办事处](images/Contoso_Poster/Contoso_WW_Org.png)

  
图 1 显示了在巴黎的总部办公室和在各大洲的区域中心和分支办事处。
  
Contoso 在世界各地的办事处按照三层设计。
  
- 总部
    
    Contoso 公司总部是上的数十个建筑物的管理、 工程和制造设施与巴黎郊外一个大企业园区。Contoso 的数据中心和网络宣传的所有都存放在巴黎总部。
    
    总部拥有 15,000 名工作人员。
    
- 区域中心
    
    区域中心办事处拥有 60% 的销售和支持人员，为世界上的特定区域服务。每个区域中心都通过高带宽的 WAN 链接连接到巴黎总部。  
    
    每个区域中心平均拥有 2,000 名工作人员。
    
- 分支办事处
    
    卫星办公室包含 80%的销售和技术支持人员为 Contoso 在主要城市或子地区的客户提供物理和现场出席。每个卫星办公室连接到具有高带宽的 WAN 链接的区域中枢。
    
    每个分支办事处平均拥有 250 名工作人员。
    
25%的 Contoso 的劳动力仅移动，与区域性中心和附属机构中仅移动工作人员的百分比也较高。仅移动工作人员提供更好的支持是 Contoso 重要的业务目标。
  
## <a name="elements-of-contosos-implementation-of-the-microsoft-cloud"></a>元素的 Microsoft Contoso 的实现的云

Contoso 的 IT 架构师确定了下列元素时采用微软云产品的规划。
  
- 网络
    
    网络包括连接到 Microsoft 的云服务和足够的带宽来进行在峰值负载下的性能。某些连接将会通过本地互联网连接和一些将在 Contoso 的专用网络基础结构。
    
    有关详细信息，请参阅[Microsoft 云网络企业架构师的](microsoft-cloud-networking-for-enterprise-architects.md)海报。
   
- 标识
    
    Contoso 其内部标识提供程序使用 Windows 服务器 AD 林，而且还与第三方提供商，为客户和合作伙伴建立联盟。Contoso 必须利用的内部一套微软的云服务的帐户。为客户和合作伙伴对基于云的应用程序的访问必须利用第三方身份提供程序。
    
    有关详细信息，请参阅[Microsoft 企业架构师的云标识](microsoft-cloud-identity-for-enterprise-architects.md)标牌。
    
- 安全
    
    基于云的标识和数据的安全性必须包括数据保护、管理权限管理、威胁感知及数据治理和安全策略的实施。
    
    有关详细信息，请参阅[Microsoft 企业架构师的云安全](http://aka.ms/cloudarchsecurity)海报。
    
- 管理
    
    管理基于云的应用和 SaaS 工作负载需要具备维护设置、数据、帐户、策略和权限并监视持续运行状况与性能的能力。现有的服务器管理工具将用于管理 Azure IaaS 中的虚拟机。
    
## <a name="see-also"></a>See Also

[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)
 


