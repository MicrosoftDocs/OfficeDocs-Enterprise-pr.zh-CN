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
# <a name="design-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="8af49-103">设计独立 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="8af49-103">Design an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="8af49-104">**摘要：** 通过独立的 SharePoint Online 团队网站的设计过程的步骤。</span><span class="sxs-lookup"><span data-stu-id="8af49-104">**Summary:** Step through the design process for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="8af49-105">本文指导您创建独立的 SharePoint Online 团队网站之前必须做出的关键设计决策。</span><span class="sxs-lookup"><span data-stu-id="8af49-105">This article takes you through the key design decisions you must make before creating an isolated SharePoint Online team site.</span></span>
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a><span data-ttu-id="8af49-106">阶段 1： 确定您的 SharePoint 组和权限级别</span><span class="sxs-lookup"><span data-stu-id="8af49-106">Phase 1: Determine your SharePoint groups and permission levels</span></span>

<span data-ttu-id="8af49-107">默认情况下每个 SharePoint Online 团队网站创建的以下 SharePoint 组：</span><span class="sxs-lookup"><span data-stu-id="8af49-107">Every SharePoint Online team site by default is created with the following SharePoint groups:</span></span>
  
- <span data-ttu-id="8af49-108">\<网站名称 > 成员</span><span class="sxs-lookup"><span data-stu-id="8af49-108">\<site name> Members</span></span>
    
- <span data-ttu-id="8af49-109">\<网站名称 > 访问者</span><span class="sxs-lookup"><span data-stu-id="8af49-109">\<site name> Visitors</span></span>
    
- <span data-ttu-id="8af49-110">\<网站名称 > 所有者</span><span class="sxs-lookup"><span data-stu-id="8af49-110">\<site name> Owners</span></span>
    
<span data-ttu-id="8af49-111">这些组是独立于 Office 365 和 Azure Active Directory (AD) 的组，分配的资源的网站的权限的基础。</span><span class="sxs-lookup"><span data-stu-id="8af49-111">These groups are separate from Office 365 and Azure Active Directory (AD) groups and are the basis for assigning permissions for the resources of the site.</span></span>
  
<span data-ttu-id="8af49-p101">确定网站中 SharePoint 组的成员可以执行哪些操作的特定权限集是一个权限级别。默认情况下，SharePoint Online 团队网站有三个权限级别： 编辑、 读取和完全控制。下表显示默认相关的 SharePoint 组和分配的权限级别：</span><span class="sxs-lookup"><span data-stu-id="8af49-p101">The set of specific permissions that determines what a member of a SharePoint group can do in a site is a permission level. There are three permission levels by default for a SharePoint Online team site: Edit, Read, and Full control. The following table shows the default correlation of SharePoint groups and assigned permission levels:</span></span>
  
|<span data-ttu-id="8af49-115">**SharePoint 组**</span><span class="sxs-lookup"><span data-stu-id="8af49-115">**SharePoint group**</span></span>|<span data-ttu-id="8af49-116">**权限级别**</span><span class="sxs-lookup"><span data-stu-id="8af49-116">**Permission level**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8af49-117">\<网站名称 > 成员</span><span class="sxs-lookup"><span data-stu-id="8af49-117">\<site name> Members</span></span>  <br/> |<span data-ttu-id="8af49-118">编辑</span><span class="sxs-lookup"><span data-stu-id="8af49-118">Edit</span></span>  <br/> |
|<span data-ttu-id="8af49-119">\<网站名称 > 访问者</span><span class="sxs-lookup"><span data-stu-id="8af49-119">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="8af49-120">读取</span><span class="sxs-lookup"><span data-stu-id="8af49-120">Read</span></span>  <br/> |
|<span data-ttu-id="8af49-121">\<网站名称 > 所有者</span><span class="sxs-lookup"><span data-stu-id="8af49-121">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="8af49-122">完全控制</span><span class="sxs-lookup"><span data-stu-id="8af49-122">Full control</span></span>  <br/> |
   
 <span data-ttu-id="8af49-p102">**最佳实践：** 您可以创建附加 SharePoint 组和权限级别。但是，我们建议您独立的 SharePoint Online 网站使用的默认 SharePoint 组和权限级别。</span><span class="sxs-lookup"><span data-stu-id="8af49-p102">**Best practice:** You can create additional SharePoint groups and permission levels. However, we recommend using the default SharePoint groups and permission levels for your isolated SharePoint Online site.</span></span>
  
<span data-ttu-id="8af49-125">以下是默认 SharePoint 组和权限级别。</span><span class="sxs-lookup"><span data-stu-id="8af49-125">Here are the default SharePoint groups and permission levels.</span></span>
  
![SharePoint Online 网站的默认 SharePoint 组和权限级别。](media/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a><span data-ttu-id="8af49-127">第 2 阶段： 向用户与访问组分配权限</span><span class="sxs-lookup"><span data-stu-id="8af49-127">Phase 2: Assign permissions to users with access groups</span></span>

<span data-ttu-id="8af49-p103">您可以通过添加用户帐户或 Office 365 或 Azure AD 组的用户帐户是 SharePoint 组的成员，向用户分配权限。添加完毕后，Office 365 用户帐户，或者直接或间接通过 Office 365 或 Azure AD 的组的成员，分配与该 SharePoint 组关联的权限级别。</span><span class="sxs-lookup"><span data-stu-id="8af49-p103">You can assign permissions to users by adding their user account, or an Office 365 or Azure AD group of which the user account is a member, to the SharePoint groups. Once added, the Office 365 user accounts, either directly or indirectly via membership in an Office 365 or Azure AD group, are assigned the permission level associated with the SharePoint group.</span></span>
  
<span data-ttu-id="8af49-130">使用默认 SharePoint 组作为示例：</span><span class="sxs-lookup"><span data-stu-id="8af49-130">Using the default SharePoint groups as an example:</span></span>
  
- <span data-ttu-id="8af49-131">成员的**\<网站名称 > 成员**SharePoint 组，其中可以包括用户帐户和组，已分配的**编辑**权限级别</span><span class="sxs-lookup"><span data-stu-id="8af49-131">Members of the **\<site name> Members** SharePoint group, which can include both user accounts and groups, are assigned the **Edit** permission level</span></span>
    
- <span data-ttu-id="8af49-132">成员的**\<网站名称 > 访问者**SharePoint 组，其中可以包括用户帐户和组，已分配**读取**权限级别</span><span class="sxs-lookup"><span data-stu-id="8af49-132">Members of the **\<site name> Visitors** SharePoint group, which can include both user accounts and groups, are assigned the **Read** permission level</span></span>
    
- <span data-ttu-id="8af49-133">成员的**\<网站名称 > 所有者**SharePoint 组，其中可以包括用户帐户和组，已分配**完全控制**权限级别</span><span class="sxs-lookup"><span data-stu-id="8af49-133">Members of the **\<site name> Owners** SharePoint group, which can include both user accounts and groups, are assigned the **Full control** permission level</span></span>
    
 <span data-ttu-id="8af49-p104">**最佳实践：** 尽管您可以管理通过单个用户帐户的权限，但我们建议您使用一个 Azure AD 组，而是称为访问组中。这简化了通过在访问组的成员身份的权限管理，而不是每个 SharePoint 组的管理列表的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="8af49-p104">**Best practice:** Although you can manage permissions through individual user accounts, we recommend that you use a single Azure AD group, known as an access group, instead. This simplifies the management of permissions through membership in the access group, rather than managing the list of user accounts for each SharePoint group.</span></span>
  
<span data-ttu-id="8af49-p105">Office 365 的 azure AD 组是不同于 Office 365 组。Azure AD 组出现在其**类型**设置为**安全**Office 管理中心，且没有电子邮件地址。可以在管理 azure AD 组：</span><span class="sxs-lookup"><span data-stu-id="8af49-p105">Azure AD groups for Office 365 are different than Office 365 groups. Azure AD groups appear in the Office Admin center with their **Type** set to **Security** and do not have an email address. Azure AD groups can be managed within:</span></span>
  
- <span data-ttu-id="8af49-139">Windows Server Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="8af49-139">Windows Server Active Directory (AD)</span></span>
    
    <span data-ttu-id="8af49-p106">这是已在您的本地 Windows Server AD 基础结构中创建并同步到 Office 365 订阅的组。在 Office 管理中心，这些组具有**与 active directory Synched****状态**。</span><span class="sxs-lookup"><span data-stu-id="8af49-p106">These are groups that have been created in your on-premises Windows Server AD infrastructure and synchronized to your Office 365 subscription. In the Office Admin center, these groups have a **Status** of **Synched with active directory**.</span></span>
    
- <span data-ttu-id="8af49-142">Office 365</span><span class="sxs-lookup"><span data-stu-id="8af49-142">Office 365</span></span>
    
    <span data-ttu-id="8af49-p107">这些是使用 Office 管理中心、 Azure 门户或 PowerShell 的 Microsoft 已创建的组。在 Office 管理中心，这些组具有**云****状态**。</span><span class="sxs-lookup"><span data-stu-id="8af49-p107">These are groups that have been created using either the Office Admin center, the Azure portal, or Microsoft PowerShell. In the Office Admin center, these groups have a **Status** of **Cloud**.</span></span>
    
 <span data-ttu-id="8af49-145">**最佳实践：** 如果您是使用 Windows Server AD 内部部署，并将与您的 Office 365 订阅同步，则执行您的用户和组管理与 Windows Server AD。</span><span class="sxs-lookup"><span data-stu-id="8af49-145">**Best practice:** If you are using Windows Server AD on-premises and synchronizing with your Office 365 subscription, perform your user and group management with Windows Server AD.</span></span>
  
<span data-ttu-id="8af49-146">对于独立 SharePoint Online 团队网站，建议的组结构如下所示：</span><span class="sxs-lookup"><span data-stu-id="8af49-146">For isolated SharePoint Online team sites, the recommended group structure looks like this:</span></span>
  
|<span data-ttu-id="8af49-147">**SharePoint 组**</span><span class="sxs-lookup"><span data-stu-id="8af49-147">**SharePoint group**</span></span>|<span data-ttu-id="8af49-148">**Azure 基于 AD 的访问组**</span><span class="sxs-lookup"><span data-stu-id="8af49-148">**Azure AD-based access group**</span></span>|<span data-ttu-id="8af49-149">**权限级别**</span><span class="sxs-lookup"><span data-stu-id="8af49-149">**Permission level**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8af49-150">\<网站名称 > 成员</span><span class="sxs-lookup"><span data-stu-id="8af49-150">\<site name> Members</span></span>  <br/> |<span data-ttu-id="8af49-151">\<网站名称 > 成员</span><span class="sxs-lookup"><span data-stu-id="8af49-151">\<site name> Members</span></span>  <br/> |<span data-ttu-id="8af49-152">编辑</span><span class="sxs-lookup"><span data-stu-id="8af49-152">Edit</span></span>  <br/> |
|<span data-ttu-id="8af49-153">\<网站名称 > 访问者</span><span class="sxs-lookup"><span data-stu-id="8af49-153">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="8af49-154">\<网站名称 > 查看器</span><span class="sxs-lookup"><span data-stu-id="8af49-154">\<site name> Viewers</span></span>  <br/> |<span data-ttu-id="8af49-155">读取</span><span class="sxs-lookup"><span data-stu-id="8af49-155">Read</span></span>  <br/> |
|<span data-ttu-id="8af49-156">\<网站名称 > 所有者</span><span class="sxs-lookup"><span data-stu-id="8af49-156">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="8af49-157">\<网站名称 > 管理员</span><span class="sxs-lookup"><span data-stu-id="8af49-157">\<site name> Admins</span></span>  <br/> |<span data-ttu-id="8af49-158">完全控制</span><span class="sxs-lookup"><span data-stu-id="8af49-158">Full control</span></span>  <br/> |
   
 <span data-ttu-id="8af49-p108">**最佳实践：** 为 SharePoint 组的成员，您可以使用 Office 365 或 Azure AD 的组，虽然我们建议您使用 Azure AD 组。Azure AD 组，托管通过 Windows Server AD 或 Office 365 中，为您提供了更灵活地使用嵌套的组分配权限。</span><span class="sxs-lookup"><span data-stu-id="8af49-p108">**Best practice:** Although you can use either Office 365 or Azure AD groups as members of SharePoint groups, we recommend that you use Azure AD groups. Azure AD groups, managed either through Windows Server AD or Office 365, give you more flexibility to use nested groups to assign permissions.</span></span>
  
<span data-ttu-id="8af49-161">以下是默认 SharePoint 组配置为使用 Azure 基于 AD 的访问组。</span><span class="sxs-lookup"><span data-stu-id="8af49-161">Here are the default SharePoint groups configured to use Azure AD-based access groups.</span></span>
  
![将访问组用作默认 SharePoint Online 网站用户组的成员。](media/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
<span data-ttu-id="8af49-163">在设计时的三个访问组，请牢记以下事项：</span><span class="sxs-lookup"><span data-stu-id="8af49-163">When designing the three access groups, keep the following in mind:</span></span>
  
- <span data-ttu-id="8af49-164">应只有少数成员在**\<网站名称 > Admins**访问组中，对应于正在管理工作组网站的 SharePoint Online 管理员一个小数字。</span><span class="sxs-lookup"><span data-stu-id="8af49-164">There should be only a few members in the **\<site name> Admins** access group, corresponding to a small number of SharePoint Online administrators who are managing the team site.</span></span>
    
- <span data-ttu-id="8af49-p109">大多数网站成员处于**\<网站名称 > 成员**或**\<网站名称 > 查看**访问组。因为网站中的成员**\<网站名称 > 成员**访问组能够删除或修改站点中的资源，请仔细考虑其成员资格。当有疑问时，将添加到的网站成员**\<网站名称 > 查看**访问组。</span><span class="sxs-lookup"><span data-stu-id="8af49-p109">Most of your site members are in the **\<site name> Members** or **\<site name> Viewers** access groups. Because site members in the **\<site name> Members** access group have the ability to delete or modify resources in the site, carefully consider its membership. When in doubt, add the site member to the **\<site name> Viewers** access group.</span></span>
    
<span data-ttu-id="8af49-168">下面是 SharePoint 组和名为 ProjectX 隔离网站的访问组的示例。</span><span class="sxs-lookup"><span data-stu-id="8af49-168">Here is an example of the SharePoint groups and access groups for an isolated site named ProjectX.</span></span>
  
![对名为 ProjectX 的 SharePoint Online 网站使用访问组的示例。](media/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a><span data-ttu-id="8af49-170">第 3 阶段： 使用嵌套 Azure AD 组</span><span class="sxs-lookup"><span data-stu-id="8af49-170">Phase 3: Use nested Azure AD groups</span></span>

<span data-ttu-id="8af49-p110">对于项目局限于少量的人员，Azure 基于 AD 的访问组添加到网站的 SharePoint 组中的一个级别将适合大多数的方案。但是，如果您有大量的人以及这些人已成员建立 Azure AD 组，您可以更轻松地分配 SharePoint 权限的方法使用嵌套的组或包含其他组作为成员的组。</span><span class="sxs-lookup"><span data-stu-id="8af49-p110">For a project confined to a small number of people, a single level of Azure AD-based access groups added to the SharePoint groups of the site will fit most scenarios. However, if you have a large number of people and those people are already members of established Azure AD groups, you can more easily assign SharePoint permissions by using nested groups, or groups that contain other groups as members.</span></span>
  
<span data-ttu-id="8af49-p111">例如，您想要创建销售、 市场营销、 工程、 法律管理人员之间的协作独立的 SharePoint online 团队网站和支持部门和这些部门已自己使用 executive 的用户帐户的组成员资格。而不是为新的网站成员创建新组并将所有的单个 executive 的用户帐户放置在它，将为每个部门的现有 executive 组置于新组。</span><span class="sxs-lookup"><span data-stu-id="8af49-p111">For example, you want to create an isolated SharePoint online team site for collaboration among the executives of the sales, marketing, engineering, legal, and support departments and those departments already their own groups with executive user account membership. Rather than creating a new group for the new site members and placing all the individual executive user accounts in it, put the existing executive groups for each department in the new group.</span></span>
  
 <span data-ttu-id="8af49-p112">如果您正在共享多个组织之间的 Office 365 订阅，用于组织的隔离网站用户组成员身份的单级可能成为由于的大量用户帐户管理变得比较困难。在这种情况下，您可以使用嵌套每个组织的 Azure AD 组，包含其组织中要管理的权限的组。</span><span class="sxs-lookup"><span data-stu-id="8af49-p112">If you are sharing an Office 365 subscription between multiple organizations, a single level of group membership for an isolated site for an organization might become difficult to manage due to the sheer number of user accounts. In this case, you can use nested Azure AD groups for each organization that contain the groups within their organizations to manage the permissions.</span></span>
  
<span data-ttu-id="8af49-177">使用嵌套 Azure AD 组：</span><span class="sxs-lookup"><span data-stu-id="8af49-177">To use nested Azure AD groups:</span></span>
  
1. <span data-ttu-id="8af49-178">识别或创建将包含用户帐户，并将相应的用户帐户添加为成员的 Azure AD 组。</span><span class="sxs-lookup"><span data-stu-id="8af49-178">Identify or create the Azure AD groups that will contain user accounts and add the appropriate user accounts as members.</span></span>
    
2. <span data-ttu-id="8af49-179">创建将包含其他 Azure AD 组并将这些组添加为成员的容器 Azure 基于 AD 的访问组。</span><span class="sxs-lookup"><span data-stu-id="8af49-179">Create the container Azure AD-based access group that will contain the other Azure AD groups and add those groups as members.</span></span>
    
3.  <span data-ttu-id="8af49-180">为相应的容器的访问组的访问级别，标识 SharePoint 组和相应的权限级别。</span><span class="sxs-lookup"><span data-stu-id="8af49-180">For the appropriate level of access for the container access group, identify the SharePoint group and corresponding permission level.</span></span>
    
> [!NOTE]
> <span data-ttu-id="8af49-181">不能使用嵌套的 Office 365 组。</span><span class="sxs-lookup"><span data-stu-id="8af49-181">You cannot use nested Office 365 groups.</span></span> 
  
<span data-ttu-id="8af49-182">下面是嵌套的 Azure AD 的示例组 ProjectX 成员访问组。</span><span class="sxs-lookup"><span data-stu-id="8af49-182">Here is an example of nested Azure AD groups for the ProjectX member access group.</span></span>
  
![对 ProjectX 网站的成员访问组使用嵌套访问组的示例。](media/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
<span data-ttu-id="8af49-184">由于中的所有用户帐户信息检索、 工程和 Project leads 团队旨在是网站成员，很方便地将其 Azure AD 组添加到 ProjectX 成员访问组。</span><span class="sxs-lookup"><span data-stu-id="8af49-184">Because all of the user accounts in the Research, Engineering, and Project leads teams are intended to be site members, it is easier to add their Azure AD groups to the ProjectX Members access group.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="8af49-185">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8af49-185">Next step</span></span>

<span data-ttu-id="8af49-186">当您准备创建和配置生产环境中的一个独立的网站时，请参阅[部署独立的 SharePoint Online 团队网站](deploy-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="8af49-186">When you are ready to create and configure an isolated site in production, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8af49-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8af49-187">See Also</span></span>

[<span data-ttu-id="8af49-188">独立 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="8af49-188">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="8af49-189">管理单独的 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="8af49-189">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="8af49-190">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="8af49-190">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="8af49-191">部署单独的 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="8af49-191">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



