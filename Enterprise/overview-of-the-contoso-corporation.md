---
title: Contoso Corporation 概述
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
ms.assetid: 1de16e29-ac2e-40b5-bf13-9301a51e16a8
description: 摘要： 了解作为商业和其世界各地的办事处的分层的结构 Contoso Corporation。
ms.openlocfilehash: 30a6dd23271fbbd5599053b934e6a1af9dc14d12
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2018
---
# <a name="overview-of-the-contoso-corporation"></a>Contoso Corporation 概述

 **摘要：** 了解业务和其世界各地的办事处的分层的结构为 Contoso Corporation。
  
Contoso Corporation 是一家总部位于法国巴黎的全球性企业。它是一家集制造、销售和支持为一体的大型组织，提供 100,000 多种产品。  
  
## <a name="the-contoso-corporation"></a>Contoso Corporation

Contoso 的全球组织拥有多少个办事处位于以下位置：
  
**图 1: Contoso 在世界各地的办事处**

![Contoso Corporation 在世界各地的办事处](images/Contoso_Poster/Contoso_WW_Org.png)

  
图 1 显示了在巴黎的总部办公室和在各大洲的区域中心和分支办事处。
  
Contoso 的世界各地的办事处按照三层设计。
  
- 总部
    
    Contoso 公司总部是在具有大量的管理、 工程和制造设施建筑物巴黎郊外大型企业所高校。所有 Contoso 的数据中心和 Internet 展示都存放在巴黎总部。
    
    总部拥有 15,000 名工作人员。
    
- 区域中心
    
    区域中心办事处拥有 60% 的销售和支持人员，为世界上的特定区域服务。每个区域中心都通过高带宽的 WAN 链接连接到巴黎总部。  
    
    每个区域中心平均拥有 2,000 名工作人员。
    
- 分支办事处
    
    分支办事处包含 80%销售和支持人员提供的主要城市或子区域中的 Contoso 客户的物理和现场状态。每个分支办公室连接到的高带宽 WAN 链接与区域集线器。
    
    每个分支办事处平均拥有 250 名工作人员。
    
25%的 Contoso 员工是移动状态，更高版本中的区域集线器和分支办事处仅移动工作者的百分比。仅移动工作者提供更好的支持是 Contoso 重要的业务目标。
  
## <a name="elements-of-contosos-implementation-of-the-microsoft-cloud"></a>Contoso 的实现的 Microsoft 元素云

Contoso IT 架构师规划采用 Microsoft 的云产品时确定以下元素。
  
- 网络
    
    网络包括连接到 Microsoft 云服务和足够带宽，要在峰值负载下的性能。某些连接将通过本地 Internet 连接，一些将 Contoso 的专用网络基础结构中。
    
    有关详细信息，请参阅[Microsoft 云网络的企业架构师](microsoft-cloud-networking-for-enterprise-architects.md)海报。
   
- 标识
    
    Contoso 使用其内部身份提供程序的 Windows Server AD 林，而且还与第三方提供程序为客户和合作伙伴建立联盟。Contoso 必须利用 Microsoft 的云服务的帐户的内部集。基于云的应用程序访问的客户和合作伙伴必须利用第三方身份提供程序。
    
    有关详细信息，请参阅[Microsoft 云标识企业架构师](microsoft-cloud-it-architecture-resources.md#identity)海报。
    
- 安全
    
    基于云的标识和数据的安全性必须包括数据保护、管理权限管理、威胁感知及数据治理和安全策略的实施。
    
    有关详细信息，请参阅[Microsoft 云 Security for 企业架构师](http://aka.ms/cloudarchsecurity)海报。
    
- 管理
    
    管理基于云的应用和 SaaS 工作负载需要具备维护设置、数据、帐户、策略和权限并监视持续运行状况与性能的能力。现有的服务器管理工具将用于管理 Azure IaaS 中的虚拟机。
    
## <a name="see-also"></a>See Also

[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)
 


