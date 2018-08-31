---
title: 保护 SharePoint Online 团队网站的高度机密敏感资产
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: 摘要： 如何 Contoso 更易于实现敏感保护和高度机密 SharePoint Online 团队网站，尚未安全、 协作的执行官且其研究中心。
ms.openlocfilehash: 23511e4156bb04e8bacf970913b00ed36e8ff9c8
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914857"
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a>保护 SharePoint Online 团队网站的高度机密敏感资产

 **摘要：** 如何实现的 Contoso 敏感保护和高度机密 SharePoint Online 团队网站的执行官和其研究中心更容易、 尚未安全协作。
  
Contoso executive 领导想要使用 Office 365，并将其文件存储在一个位置进行协作，无论主管可能。同样，Contoso 的研究部门 — 与部门中巴黎、 莫斯科，纽约、 北京和班加罗尔 — 要在团队之间转换到云中更轻松地访问和更多 open 协作其内部部署数字资产。
  
但是，在这两种情况，这些资源的访问权限必须限制为允许查看或更改它们与持续由 IT 人员管理网站的权限的人员的子集。此外，即使一些资源有意或无意中分发，他们必须加密并有权阻止那些没有访问权限，可以查看或更改其内容。
  
Contoso 中的安全和 SharePoint 管理员的 IT 部门决定使用敏感保护和高度机密 SharePoint Online 团队网站，如图 1 中所示。
  
**图 1： 比较的敏感保护和高度机密 SharePoint Online 团队网站**

![敏感保护和高度机密的 SharePoint Online 团队网站](media/Contoso-Poster/SP-Solution.png)
  
Contoso 使用以下步骤为其执行官和研究团队创建安全的 SharePoint Online 团队网站：
  
1. 创建**Executives**敏感 SharePoint Online 团队网站
    
    新的工作组网站作为为具有完全控制权限级别的所有者编辑 SharePoint 权限级别与 SharePoint 管理员帐户的组成员的执行官使用现有的 Azure Active Directory (AD) 组。
    
2. 迁移 executives 文件
    
    将现有的内部部署 executive 文件和文件夹移动到新的执行官 SharePoint Online 团队网站。
    
3. 创建**研究**高度机密 SharePoint Online 团队网站
    
    新的工作组网站使用现有的 Azure AD 研究团队组作为成员与编辑权限级别和一小组 SharePoint 管理员帐户为具有完全控制权限级别的所有者。分配研究文件 AIP 标签确保对它们进行加密和只有研究组的成员可以打开它们。
    
4. 迁移研究文件
    
    移动现有研究小组本地文件和文件夹到新的研究 SharePoint Online 团队网站。
    
结果是由安全性和 SharePoint 管理员严格控制其访问权限的两个协作网站。与高度机密 AIP 标签的文件，即使分发外研究工作组网站，它们已加密和只能打开由研究团队的成员。
  
有关详细信息，请参阅[安全 SharePoint Online 网站和文件](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)。
  
 若要设置此功能演示、 概念证明或开发/测试，请参阅[开发/测试环境中的安全 SharePoint Online 网站](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)。
  
## <a name="see-also"></a>另请参阅

[Contoso Corporation 的企业方案](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)




