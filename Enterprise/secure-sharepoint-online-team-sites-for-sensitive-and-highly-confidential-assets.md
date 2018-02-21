---
title: "保护敏感和高度机密的资产的 SharePoint Online 工作组站点"
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
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "摘要： 如何 Contoso 变得更容易实现保护敏感和高度机密 SharePoint Online 的工作组站点，尚未安全、 高级管理人员的协作和其研究中心。"
ms.openlocfilehash: c615280d39117f68515fb13d4ba83428d73e4fd3
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a>保护敏感和高度机密的资产的 SharePoint Online 工作组站点

 **摘要：**如何实现 Contoso 敏感保护和高度机密 SharePoint Online 团队更容易，然而安全，协作的行政人员和其研究中心的网站。
  
Contoso 行政领导想要使用 Office 365 并将他们的文件存储在一个位置进行协作，而不考虑管理人员可能。同样，Contoso 的研究部门 — — 与巴黎、 莫斯科、 纽约、 北京，以及班加罗尔的部门 — — 想要在团队之间过渡到云，用户更容易访问和更开放的协作及其内部数字资产。
  
但是，在这两种情况下，对这些资源的访问必须限于人员有权查看或更改它们，与由 IT 人员管理网站的日常权限的子集。此外，即使某些资源被有意或无意中分布，它们必须加密而且具有权限，以防止那些无权访问要查看或更改它们的内容。
  
在 Contoso 的安全和 SharePoint 管理员的 IT 部门决定使用敏感保护和高度机密的 SharePoint Online 工作组站点，如图 1 所示。
  
**图 1： 比较敏感的保护和高度机密的在线 SharePoint 工作组网站**

![敏感保护和高度机密的 SharePoint Online 团队网站](images/Contoso_Poster/SP_Solution.png)
  
Contoso 使用这些步骤来为他们的执行官们和研究小组创建 SharePoint Online 的安全团队站点：
  
1. 创建一个**执行官**敏感 SharePoint Online 团队网站
    
    新工作组网站具有完全控制权限级别的所有者具有编辑 SharePoint 权限级别和少量 SharePoint 管理员帐户的成员作为人员使用现有的 Azure 活动目录 (AD) 组。
    
2. 将执行官的文件迁移
    
    将现有的内部行政文件和文件夹移动到新执行官 SharePoint Online 的工作组网站。
    
3. 创建**研究**高度机密在线 SharePoint 工作组网站
    
    新的团队站点使用现有 Azure 广告研究团队组作为具有完全控制权限级别的所有者具有编辑权限级别和少量 SharePoint 管理员帐户的成员。AIP 标签分配研究文件确保对它们进行加密，并只有研究组的成员可以打开它们。
    
4. 研究文件迁移
    
    移动现有研究小组内部的文件和文件夹到新研究 SharePoint Online 工作组站点。
    
结果是两个由安全和 SharePoint 管理员紧密控制其访问权限的协作站点。使用高度机密的 AIP 的标签的文件，即使分发外部研究工作组站点，它们都将被加密，只能打开由研究小组的成员。
  
有关详细信息，请参阅[安全 SharePoint Online 网站和文件](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)。
  
 若要设置此功能演示、 概念证明或开发/测试，请参见[安全 SharePoint Online 网站的开发/测试环境](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)。
  
## <a name="see-also"></a>另请参阅

[Contoso Corporation 的企业方案](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)




