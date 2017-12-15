---
title: "设计独立的在线 SharePoint 工作组网站"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: "摘要： 单步执行独立在线 SharePoint 工作组网站的设计过程。"
ms.openlocfilehash: 343872ef7a41b40a87454da27ddccc4530ffe2eb
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a>设计独立的在线 SharePoint 工作组网站

 **摘要：**单步执行独立在线 SharePoint 工作组网站的设计过程。
  
本文将引导您通过创建独立的在线 SharePoint 工作组网站之前必须进行的关键设计决策。
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a>第 1 阶段： 确定您的 SharePoint 组和权限级别

默认情况下每个 SharePoint Online 团队站点创建与下面的 SharePoint 组：
  
- \<站点名称 > 成员
    
- \<站点名称 > 访问者
    
- \<站点名称 > 所有者
    
这些组是独立于 Office 365 和 Azure 活动目录 (AD) 组，分配资源权限的网站的基础。
  
确定站点中的 sharepoint 用户组的成员可以执行哪些操作的特定的权限集是某个权限级别。默认情况下，SharePoint Online 工作组站点有三个权限级别： 编辑、 读取和完全控制。下表显示了默认关联以及 SharePoint 组分配的权限级别：
  
|**SharePoint 组**|**权限级别**|
|:-----|:-----|
|\<站点名称 > 成员  <br/> |编辑  <br/> |
|\<站点名称 > 访问者  <br/> |读取  <br/> |
|\<站点名称 > 所有者  <br/> |完全控制  <br/> |
   
 **最佳做法：**您可以创建其他 SharePoint 组和权限级别。但是，我们建议使用独立的 SharePoint Online 网站默认 SharePoint 用户组和权限级别。
  
以下是默认 SharePoint 用户组和权限级别。
  
![SharePoint Online 网站的默认 SharePoint 组和权限级别。](images/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a>阶段 2： 与访问组为用户分配权限

加上他们的用户帐户，或者用户帐户是其成员，SharePoint 组 Office 365 或 Azure AD 组，可以为用户分配权限。添加后，Office 365 的用户帐户，或者直接或间接通过 Office 365 或 Azure AD 组中的成员资格，具有与 SharePoint 组关联的权限级别。
  
使用默认 SharePoint 组作为示例：
  
- 成员**\<网站名称 > 成员**SharePoint 组可以包含用户帐户和组，分配**编辑**权限级别
    
- 成员**\<网站名称 > 访问者**SharePoint 组，其中可以包括用户帐户和组，请指派**读取**权限级别
    
- 成员**\<网站名称 > 所有者**SharePoint 组可以包含用户帐户和组，分配**完全控制**权限级别
    
 **最佳做法：**尽管您可以管理各个用户帐户的权限，我们建议使用一个 Azure AD 组，访问组，而是称为。这简化了通过访问组中的成员身份的权限的管理，而不是管理用户列表的每个 SharePoint 组帐户。
  
对于 Office 365 的 azure AD 组是不同于 Office 365 组。Azure AD 组出现在办公室管理其**类型**设置为**安全**中心并不具有电子邮件地址。可以在中管理 azure AD 组：
  
- Windows 服务器活动目录 (AD)
    
    这是已在内部部署 Windows 服务器 AD 基础结构中创建和同步到您的 Office 365 订购的组。在办公室管理的中心，这些组具有**与活动目录 Synched****状态**。
    
- Office 365
    
    这些都是使用 Office 管理中心、 Azure 门户或 Microsoft PowerShell 创建的组。在办公室管理的中心，这些组具有**状态**的**云**。
    
 **最佳做法：**如果使用的 Windows Server 广告场所和您的用户和组管理与 Windows 服务器 AD 与您的 Office 365 提供订阅同步执行。
  
对于独立 SharePoint Online 团队站点，建议使用的组结构如下所示：
  
|**SharePoint 组**|**Azure 基于 AD 的访问组**|**权限级别**|
|:-----|:-----|:-----|
|\<站点名称 > 成员  <br/> |\<站点名称 > 成员  <br/> |编辑  <br/> |
|\<站点名称 > 访问者  <br/> |\<站点名称 > 观众  <br/> |读取  <br/> |
|\<站点名称 > 所有者  <br/> |\<站点名称 > 管理员  <br/> |完全控制  <br/> |
   
 **最佳做法：**虽然您可以使用 Office 365 或 Azure AD 组为 SharePoint 组的成员，我们建议您使用 Azure AD 组。Azure AD 组，通过 Windows 服务器 AD 或 Office 365 管理为您提供了更大的灵活性，可以使用嵌套的组来分配权限。
  
以下是默认网站配置为使用 Azure 基于 AD 的访问组。
  
![将访问组用作默认 SharePoint Online 网站用户组的成员。](images/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
在设计时访问三个组，请记住以下：
  
- 应中的只有少数成员**\<网站名称 > 管理员**对应于少数几个管理团队网站的 SharePoint Online 管理员的访问组。
    
- 网站成员的大多数都是在**\<网站名称 > 成员**或**\<网站名称 > 查看器**访问组。因为网站中的成员**\<网站名称 > 成员**访问组已删除或修改网站中的资源时，应仔细考虑其成员资格的能力。当有疑问时，添加为网站成员**\<网站名称 > 查看**的访问组。
    
下面是示例的 SharePoint 组和独立网站名为 ProjectX 的访问组。
  
![对名为 ProjectX 的 SharePoint Online 网站使用访问组的示例。](images/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a>阶段 3： 使用嵌套 Azure AD 组

局限于一小部分人的项目，Azure 基于 AD 的访问组添加到网站的 SharePoint 组的单个级别适合大多数情况。但是，如果您有大量的人以及这些人已的成员建立了 Azure AD 组，您可以更轻松地分配 SharePoint 权限通过使用嵌套的组中或包含其他组作为其成员的组。
  
例如，您希望创建独立的 SharePoint 在线的团队站点的销售、 市场营销、 工程、 法律、 高级管理人员之间的协作和支持部门，这些部门已经自己与高级管理人员的用户帐户的组成员资格。而不是为新网站成员创建一个新组并将所有单个执行用户帐户放在它，放入新组中的每个部门的现有行政组。
  
 如果您要共享的 Office 365 订阅多个组织之间，组织一个独立网站用户组成员资格的单级可能变得难以管理由于庞大数量的用户帐户。在这种情况下，可以使用嵌套的每个组织的 Azure AD 组，包含在其组织内的组管理权限。
  
若要使用嵌套 Azure AD 组：
  
1. 标识或创建将包含用户帐户，并添加适当的用户帐户作为其成员的 Azure AD 组。
    
2. 创建将包含其他 Azure AD 组并且将这些组作为成员添加容器 Azure 基于 AD 的访问组。
    
3.  对于适当的容器访问组的访问级别，确定 SharePoint 组和相应的权限级别。
    
> [!NOTE]
> 您不能使用 Office 365 的嵌套的组。 
  
这是一种嵌套的 Azure AD 组 ProjectX 成员访问组。
  
![对 ProjectX 网站的成员访问组使用嵌套访问组的示例。](images/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
因为研究、 工程和项目中的用户帐户的所有潜在顾客团队都应是网站成员，很容易将它们的 Azure AD 组添加到 ProjectX 成员访问组。
  
## <a name="next-step"></a>后续步骤

当您准备创建和配置生产中一个独立的网站时，请参见[部署独立的在线 SharePoint 工作组网站](deploy-an-isolated-sharepoint-online-team-site.md)。
  
## <a name="see-also"></a>See Also

[SharePoint Online 的独立的团队站点](isolated-sharepoint-online-team-sites.md)
  
[管理独立的在线 SharePoint 工作组网站](manage-an-isolated-sharepoint-online-team-site.md)
  
[安全解决方案](security-solutions.md)

[部署独立的在线 SharePoint 工作组网站](deploy-an-isolated-sharepoint-online-team-site.md)



