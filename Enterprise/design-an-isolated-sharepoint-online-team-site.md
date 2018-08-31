---
title: 设计独立 SharePoint Online 团队网站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: 摘要： 通过独立的 SharePoint Online 团队网站的设计过程的步骤。
ms.openlocfilehash: 4807b7cef0a401901eb5abec3d683ca67b2193db
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914837"
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a>设计独立 SharePoint Online 团队网站

 **摘要：** 通过独立的 SharePoint Online 团队网站的设计过程的步骤。
  
本文指导您创建独立的 SharePoint Online 团队网站之前必须做出的关键设计决策。
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a>阶段 1： 确定您的 SharePoint 组和权限级别

默认情况下每个 SharePoint Online 团队网站创建的以下 SharePoint 组：
  
- \<网站名称 > 成员
    
- \<网站名称 > 访问者
    
- \<网站名称 > 所有者
    
这些组是独立于 Office 365 和 Azure Active Directory (AD) 的组，分配的资源的网站的权限的基础。
  
确定网站中 SharePoint 组的成员可以执行哪些操作的特定权限集是一个权限级别。默认情况下，SharePoint Online 团队网站有三个权限级别： 编辑、 读取和完全控制。下表显示默认相关的 SharePoint 组和分配的权限级别：
  
|**SharePoint 组**|**权限级别**|
|:-----|:-----|
|\<网站名称 > 成员  <br/> |编辑  <br/> |
|\<网站名称 > 访问者  <br/> |读取  <br/> |
|\<网站名称 > 所有者  <br/> |完全控制  <br/> |
   
 **最佳实践：** 您可以创建附加 SharePoint 组和权限级别。但是，我们建议您独立的 SharePoint Online 网站使用的默认 SharePoint 组和权限级别。
  
以下是默认 SharePoint 组和权限级别。
  
![SharePoint Online 网站的默认 SharePoint 组和权限级别。](media/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a>第 2 阶段： 向用户与访问组分配权限

您可以通过添加用户帐户或 Office 365 或 Azure AD 组的用户帐户是 SharePoint 组的成员，向用户分配权限。添加完毕后，Office 365 用户帐户，或者直接或间接通过 Office 365 或 Azure AD 的组的成员，分配与该 SharePoint 组关联的权限级别。
  
使用默认 SharePoint 组作为示例：
  
- 成员的**\<网站名称 > 成员**SharePoint 组，其中可以包括用户帐户和组，已分配的**编辑**权限级别
    
- 成员的**\<网站名称 > 访问者**SharePoint 组，其中可以包括用户帐户和组，已分配**读取**权限级别
    
- 成员的**\<网站名称 > 所有者**SharePoint 组，其中可以包括用户帐户和组，已分配**完全控制**权限级别
    
 **最佳实践：** 尽管您可以管理通过单个用户帐户的权限，但我们建议您使用一个 Azure AD 组，而是称为访问组中。这简化了通过在访问组的成员身份的权限管理，而不是每个 SharePoint 组的管理列表的用户帐户。
  
Office 365 的 azure AD 组是不同于 Office 365 组。Azure AD 组出现在其**类型**设置为**安全**Office 管理中心，且没有电子邮件地址。可以在管理 azure AD 组：
  
- Windows Server Active Directory (AD)
    
    这是已在您的本地 Windows Server AD 基础结构中创建并同步到 Office 365 订阅的组。在 Office 管理中心，这些组具有**与 active directory Synched****状态**。
    
- Office 365
    
    这些是使用 Office 管理中心、 Azure 门户或 PowerShell 的 Microsoft 已创建的组。在 Office 管理中心，这些组具有**云****状态**。
    
 **最佳实践：** 如果您是使用 Windows Server AD 内部部署，并将与您的 Office 365 订阅同步，则执行您的用户和组管理与 Windows Server AD。
  
对于独立 SharePoint Online 团队网站，建议的组结构如下所示：
  
|**SharePoint 组**|**Azure 基于 AD 的访问组**|**权限级别**|
|:-----|:-----|:-----|
|\<网站名称 > 成员  <br/> |\<网站名称 > 成员  <br/> |编辑  <br/> |
|\<网站名称 > 访问者  <br/> |\<网站名称 > 查看器  <br/> |读取  <br/> |
|\<网站名称 > 所有者  <br/> |\<网站名称 > 管理员  <br/> |完全控制  <br/> |
   
 **最佳实践：** 为 SharePoint 组的成员，您可以使用 Office 365 或 Azure AD 的组，虽然我们建议您使用 Azure AD 组。Azure AD 组，托管通过 Windows Server AD 或 Office 365 中，为您提供了更灵活地使用嵌套的组分配权限。
  
以下是默认 SharePoint 组配置为使用 Azure 基于 AD 的访问组。
  
![将访问组用作默认 SharePoint Online 网站用户组的成员。](media/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
在设计时的三个访问组，请牢记以下事项：
  
- 应只有少数成员在**\<网站名称 > Admins**访问组中，对应于正在管理工作组网站的 SharePoint Online 管理员一个小数字。
    
- 大多数网站成员处于**\<网站名称 > 成员**或**\<网站名称 > 查看**访问组。因为网站中的成员**\<网站名称 > 成员**访问组能够删除或修改站点中的资源，请仔细考虑其成员资格。当有疑问时，将添加到的网站成员**\<网站名称 > 查看**访问组。
    
下面是 SharePoint 组和名为 ProjectX 隔离网站的访问组的示例。
  
![对名为 ProjectX 的 SharePoint Online 网站使用访问组的示例。](media/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a>第 3 阶段： 使用嵌套 Azure AD 组

对于项目局限于少量的人员，Azure 基于 AD 的访问组添加到网站的 SharePoint 组中的一个级别将适合大多数的方案。但是，如果您有大量的人以及这些人已成员建立 Azure AD 组，您可以更轻松地分配 SharePoint 权限的方法使用嵌套的组或包含其他组作为成员的组。
  
例如，您想要创建销售、 市场营销、 工程、 法律管理人员之间的协作独立的 SharePoint online 团队网站和支持部门和这些部门已自己使用 executive 的用户帐户的组成员资格。而不是为新的网站成员创建新组并将所有的单个 executive 的用户帐户放置在它，将为每个部门的现有 executive 组置于新组。
  
 如果您正在共享多个组织之间的 Office 365 订阅，用于组织的隔离网站用户组成员身份的单级可能成为由于的大量用户帐户管理变得比较困难。在这种情况下，您可以使用嵌套每个组织的 Azure AD 组，包含其组织中要管理的权限的组。
  
使用嵌套 Azure AD 组：
  
1. 识别或创建将包含用户帐户，并将相应的用户帐户添加为成员的 Azure AD 组。
    
2. 创建将包含其他 Azure AD 组并将这些组添加为成员的容器 Azure 基于 AD 的访问组。
    
3.  为相应的容器的访问组的访问级别，标识 SharePoint 组和相应的权限级别。
    
> [!NOTE]
> 不能使用嵌套的 Office 365 组。 
  
下面是嵌套的 Azure AD 的示例组 ProjectX 成员访问组。
  
![对 ProjectX 网站的成员访问组使用嵌套访问组的示例。](media/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
由于中的所有用户帐户信息检索、 工程和 Project leads 团队旨在是网站成员，很方便地将其 Azure AD 组添加到 ProjectX 成员访问组。
  
## <a name="next-step"></a>后续步骤

当您准备创建和配置生产环境中的一个独立的网站时，请参阅[部署独立的 SharePoint Online 团队网站](deploy-an-isolated-sharepoint-online-team-site.md)。
  
## <a name="see-also"></a>另请参阅

[独立 SharePoint Online 团队网站](isolated-sharepoint-online-team-sites.md)
  
[管理单独的 SharePoint Online 团队网站](manage-an-isolated-sharepoint-online-team-site.md)
  
[安全解决方案](security-solutions.md)

[部署单独的 SharePoint Online 团队网站](deploy-an-isolated-sharepoint-online-team-site.md)



