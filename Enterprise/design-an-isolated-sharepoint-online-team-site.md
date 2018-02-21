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
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: "摘要： 单步执行独立在线 SharePoint 工作组网站的设计过程。"
ms.openlocfilehash: efd55ce780cf2951bfafd31215201459965c0e78
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="1173c-103">设计独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="1173c-103">Design an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="1173c-104">**摘要：**单步执行独立在线 SharePoint 工作组网站的设计过程。</span><span class="sxs-lookup"><span data-stu-id="1173c-104">**Summary:** Step through the design process for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="1173c-105">本文将引导您通过创建独立的在线 SharePoint 工作组网站之前必须进行的关键设计决策。</span><span class="sxs-lookup"><span data-stu-id="1173c-105">This article takes you through the key design decisions you must make before creating an isolated SharePoint Online team site.</span></span>
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a><span data-ttu-id="1173c-106">第 1 阶段： 确定您的 SharePoint 组和权限级别</span><span class="sxs-lookup"><span data-stu-id="1173c-106">Phase 1: Determine your SharePoint groups and permission levels</span></span>

<span data-ttu-id="1173c-107">默认情况下每个 SharePoint Online 团队站点创建与下面的 SharePoint 组：</span><span class="sxs-lookup"><span data-stu-id="1173c-107">Every SharePoint Online team site by default is created with the following SharePoint groups:</span></span>
  
- <span data-ttu-id="1173c-108">\<站点名称 > 成员</span><span class="sxs-lookup"><span data-stu-id="1173c-108">\<site name> Members</span></span>
    
- <span data-ttu-id="1173c-109">\<站点名称 > 访问者</span><span class="sxs-lookup"><span data-stu-id="1173c-109">\<site name> Visitors</span></span>
    
- <span data-ttu-id="1173c-110">\<站点名称 > 所有者</span><span class="sxs-lookup"><span data-stu-id="1173c-110">\<site name> Owners</span></span>
    
<span data-ttu-id="1173c-111">这些组是独立于 Office 365 和 Azure 活动目录 (AD) 组，分配资源权限的网站的基础。</span><span class="sxs-lookup"><span data-stu-id="1173c-111">These groups are separate from Office 365 and Azure Active Directory (AD) groups and are the basis for assigning permissions for the resources of the site.</span></span>
  
<span data-ttu-id="1173c-p101">确定站点中的 sharepoint 用户组的成员可以执行哪些操作的特定的权限集是某个权限级别。默认情况下，SharePoint Online 工作组站点有三个权限级别： 编辑、 读取和完全控制。下表显示了默认关联以及 SharePoint 组分配的权限级别：</span><span class="sxs-lookup"><span data-stu-id="1173c-p101">The set of specific permissions that determines what a member of a SharePoint group can do in a site is a permission level. There are three permission levels by default for a SharePoint Online team site: Edit, Read, and Full control. The following table shows the default correlation of SharePoint groups and assigned permission levels:</span></span>
  
|<span data-ttu-id="1173c-115">**SharePoint 组**</span><span class="sxs-lookup"><span data-stu-id="1173c-115">**SharePoint group**</span></span>|<span data-ttu-id="1173c-116">**权限级别**</span><span class="sxs-lookup"><span data-stu-id="1173c-116">**Permission level**</span></span>|
|:-----|:-----|
|<span data-ttu-id="1173c-117">\<站点名称 > 成员</span><span class="sxs-lookup"><span data-stu-id="1173c-117">\<site name> Members</span></span>  <br/> |<span data-ttu-id="1173c-118">编辑</span><span class="sxs-lookup"><span data-stu-id="1173c-118">Edit</span></span>  <br/> |
|<span data-ttu-id="1173c-119">\<站点名称 > 访问者</span><span class="sxs-lookup"><span data-stu-id="1173c-119">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="1173c-120">读取</span><span class="sxs-lookup"><span data-stu-id="1173c-120">Read</span></span>  <br/> |
|<span data-ttu-id="1173c-121">\<站点名称 > 所有者</span><span class="sxs-lookup"><span data-stu-id="1173c-121">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="1173c-122">完全控制</span><span class="sxs-lookup"><span data-stu-id="1173c-122">Full control</span></span>  <br/> |
   
 <span data-ttu-id="1173c-p102">**最佳做法：**您可以创建其他 SharePoint 组和权限级别。但是，我们建议使用独立的 SharePoint Online 网站默认 SharePoint 用户组和权限级别。</span><span class="sxs-lookup"><span data-stu-id="1173c-p102">**Best practice:** You can create additional SharePoint groups and permission levels. However, we recommend using the default SharePoint groups and permission levels for your isolated SharePoint Online site.</span></span>
  
<span data-ttu-id="1173c-125">以下是默认 SharePoint 用户组和权限级别。</span><span class="sxs-lookup"><span data-stu-id="1173c-125">Here are the default SharePoint groups and permission levels.</span></span>
  
![SharePoint Online 网站的默认 SharePoint 组和权限级别。](images/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a><span data-ttu-id="1173c-127">阶段 2： 与访问组为用户分配权限</span><span class="sxs-lookup"><span data-stu-id="1173c-127">Phase 2: Assign permissions to users with access groups</span></span>

<span data-ttu-id="1173c-p103">加上他们的用户帐户，或者用户帐户是其成员，SharePoint 组 Office 365 或 Azure AD 组，可以为用户分配权限。添加后，Office 365 的用户帐户，或者直接或间接通过 Office 365 或 Azure AD 组中的成员资格，具有与 SharePoint 组关联的权限级别。</span><span class="sxs-lookup"><span data-stu-id="1173c-p103">You can assign permissions to users by adding their user account, or an Office 365 or Azure AD group of which the user account is a member, to the SharePoint groups. Once added, the Office 365 user accounts, either directly or indirectly via membership in an Office 365 or Azure AD group, are assigned the permission level associated with the SharePoint group.</span></span>
  
<span data-ttu-id="1173c-130">使用默认 SharePoint 组作为示例：</span><span class="sxs-lookup"><span data-stu-id="1173c-130">Using the default SharePoint groups as an example:</span></span>
  
- <span data-ttu-id="1173c-131">成员**\<网站名称 > 成员**SharePoint 组可以包含用户帐户和组，分配**编辑**权限级别</span><span class="sxs-lookup"><span data-stu-id="1173c-131">Members of the **\<site name> Members** SharePoint group, which can include both user accounts and groups, are assigned the **Edit** permission level</span></span>
    
- <span data-ttu-id="1173c-132">成员**\<网站名称 > 访问者**SharePoint 组，其中可以包括用户帐户和组，请指派**读取**权限级别</span><span class="sxs-lookup"><span data-stu-id="1173c-132">Members of the **\<site name> Visitors** SharePoint group, which can include both user accounts and groups, are assigned the **Read** permission level</span></span>
    
- <span data-ttu-id="1173c-133">成员**\<网站名称 > 所有者**SharePoint 组可以包含用户帐户和组，分配**完全控制**权限级别</span><span class="sxs-lookup"><span data-stu-id="1173c-133">Members of the **\<site name> Owners** SharePoint group, which can include both user accounts and groups, are assigned the **Full control** permission level</span></span>
    
 <span data-ttu-id="1173c-p104">**最佳做法：**尽管您可以管理各个用户帐户的权限，我们建议使用一个 Azure AD 组，访问组，而是称为。这简化了通过访问组中的成员身份的权限的管理，而不是管理用户列表的每个 SharePoint 组帐户。</span><span class="sxs-lookup"><span data-stu-id="1173c-p104">**Best practice:** Although you can manage permissions through individual user accounts, we recommend that you use a single Azure AD group, known as an access group, instead. This simplifies the management of permissions through membership in the access group, rather than managing the list of user accounts for each SharePoint group.</span></span>
  
<span data-ttu-id="1173c-p105">对于 Office 365 的 azure AD 组是不同于 Office 365 组。Azure AD 组出现在办公室管理其**类型**设置为**安全**中心并不具有电子邮件地址。可以在中管理 azure AD 组：</span><span class="sxs-lookup"><span data-stu-id="1173c-p105">Azure AD groups for Office 365 are different than Office 365 groups. Azure AD groups appear in the Office Admin center with their **Type** set to **Security** and do not have an email address. Azure AD groups can be managed within:</span></span>
  
- <span data-ttu-id="1173c-139">Windows 服务器活动目录 (AD)</span><span class="sxs-lookup"><span data-stu-id="1173c-139">Windows Server Active Directory (AD)</span></span>
    
    <span data-ttu-id="1173c-p106">这是已在内部部署 Windows 服务器 AD 基础结构中创建和同步到您的 Office 365 订购的组。在办公室管理的中心，这些组具有**与活动目录 Synched****状态**。</span><span class="sxs-lookup"><span data-stu-id="1173c-p106">These are groups that have been created in your on-premises Windows Server AD infrastructure and synchronized to your Office 365 subscription. In the Office Admin center, these groups have a **Status** of **Synched with active directory**.</span></span>
    
- <span data-ttu-id="1173c-142">Office 365</span><span class="sxs-lookup"><span data-stu-id="1173c-142">Office 365</span></span>
    
    <span data-ttu-id="1173c-p107">这些都是使用 Office 管理中心、 Azure 门户或 Microsoft PowerShell 创建的组。在办公室管理的中心，这些组具有**状态**的**云**。</span><span class="sxs-lookup"><span data-stu-id="1173c-p107">These are groups that have been created using either the Office Admin center, the Azure portal, or Microsoft PowerShell. In the Office Admin center, these groups have a **Status** of **Cloud**.</span></span>
    
 <span data-ttu-id="1173c-145">**最佳做法：**如果使用的 Windows Server 广告场所和您的用户和组管理与 Windows 服务器 AD 与您的 Office 365 提供订阅同步执行。</span><span class="sxs-lookup"><span data-stu-id="1173c-145">**Best practice:** If you are using Windows Server AD on-premises and synchronizing with your Office 365 subscription, perform your user and group management with Windows Server AD.</span></span>
  
<span data-ttu-id="1173c-146">对于独立 SharePoint Online 团队站点，建议使用的组结构如下所示：</span><span class="sxs-lookup"><span data-stu-id="1173c-146">For isolated SharePoint Online team sites, the recommended group structure looks like this:</span></span>
  
|<span data-ttu-id="1173c-147">**SharePoint 组**</span><span class="sxs-lookup"><span data-stu-id="1173c-147">**SharePoint group**</span></span>|<span data-ttu-id="1173c-148">**Azure 基于 AD 的访问组**</span><span class="sxs-lookup"><span data-stu-id="1173c-148">**Azure AD-based access group**</span></span>|<span data-ttu-id="1173c-149">**权限级别**</span><span class="sxs-lookup"><span data-stu-id="1173c-149">**Permission level**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="1173c-150">\<站点名称 > 成员</span><span class="sxs-lookup"><span data-stu-id="1173c-150">\<site name> Members</span></span>  <br/> |<span data-ttu-id="1173c-151">\<站点名称 > 成员</span><span class="sxs-lookup"><span data-stu-id="1173c-151">\<site name> Members</span></span>  <br/> |<span data-ttu-id="1173c-152">编辑</span><span class="sxs-lookup"><span data-stu-id="1173c-152">Edit</span></span>  <br/> |
|<span data-ttu-id="1173c-153">\<站点名称 > 访问者</span><span class="sxs-lookup"><span data-stu-id="1173c-153">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="1173c-154">\<站点名称 > 观众</span><span class="sxs-lookup"><span data-stu-id="1173c-154">\<site name> Viewers</span></span>  <br/> |<span data-ttu-id="1173c-155">读取</span><span class="sxs-lookup"><span data-stu-id="1173c-155">Read</span></span>  <br/> |
|<span data-ttu-id="1173c-156">\<站点名称 > 所有者</span><span class="sxs-lookup"><span data-stu-id="1173c-156">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="1173c-157">\<站点名称 > 管理员</span><span class="sxs-lookup"><span data-stu-id="1173c-157">\<site name> Admins</span></span>  <br/> |<span data-ttu-id="1173c-158">完全控制</span><span class="sxs-lookup"><span data-stu-id="1173c-158">Full control</span></span>  <br/> |
   
 <span data-ttu-id="1173c-p108">**最佳做法：**虽然您可以使用 Office 365 或 Azure AD 组为 SharePoint 组的成员，我们建议您使用 Azure AD 组。Azure AD 组，通过 Windows 服务器 AD 或 Office 365 管理为您提供了更大的灵活性，可以使用嵌套的组来分配权限。</span><span class="sxs-lookup"><span data-stu-id="1173c-p108">**Best practice:** Although you can use either Office 365 or Azure AD groups as members of SharePoint groups, we recommend that you use Azure AD groups. Azure AD groups, managed either through Windows Server AD or Office 365, give you more flexibility to use nested groups to assign permissions.</span></span>
  
<span data-ttu-id="1173c-161">以下是默认网站配置为使用 Azure 基于 AD 的访问组。</span><span class="sxs-lookup"><span data-stu-id="1173c-161">Here are the default SharePoint groups configured to use Azure AD-based access groups.</span></span>
  
![将访问组用作默认 SharePoint Online 网站用户组的成员。](images/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
<span data-ttu-id="1173c-163">在设计时访问三个组，请记住以下：</span><span class="sxs-lookup"><span data-stu-id="1173c-163">When designing the three access groups, keep the following in mind:</span></span>
  
- <span data-ttu-id="1173c-164">应中的只有少数成员**\<网站名称 > 管理员**对应于少数几个管理团队网站的 SharePoint Online 管理员的访问组。</span><span class="sxs-lookup"><span data-stu-id="1173c-164">There should be only a few members in the **\<site name> Admins** access group, corresponding to a small number of SharePoint Online administrators who are managing the team site.</span></span>
    
- <span data-ttu-id="1173c-p109">网站成员的大多数都是在**\<网站名称 > 成员**或**\<网站名称 > 查看器**访问组。因为网站中的成员**\<网站名称 > 成员**访问组已删除或修改网站中的资源时，应仔细考虑其成员资格的能力。当有疑问时，添加为网站成员**\<网站名称 > 查看**的访问组。</span><span class="sxs-lookup"><span data-stu-id="1173c-p109">Most of your site members are in the **\<site name> Members** or **\<site name> Viewers** access groups. Because site members in the **\<site name> Members** access group have the ability to delete or modify resources in the site, carefully consider its membership. When in doubt, add the site member to the **\<site name> Viewers** access group.</span></span>
    
<span data-ttu-id="1173c-168">下面是示例的 SharePoint 组和独立网站名为 ProjectX 的访问组。</span><span class="sxs-lookup"><span data-stu-id="1173c-168">Here is an example of the SharePoint groups and access groups for an isolated site named ProjectX.</span></span>
  
![对名为 ProjectX 的 SharePoint Online 网站使用访问组的示例。](images/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a><span data-ttu-id="1173c-170">阶段 3： 使用嵌套 Azure AD 组</span><span class="sxs-lookup"><span data-stu-id="1173c-170">Phase 3: Use nested Azure AD groups</span></span>

<span data-ttu-id="1173c-p110">局限于一小部分人的项目，Azure 基于 AD 的访问组添加到网站的 SharePoint 组的单个级别适合大多数情况。但是，如果您有大量的人以及这些人已的成员建立了 Azure AD 组，您可以更轻松地分配 SharePoint 权限通过使用嵌套的组中或包含其他组作为其成员的组。</span><span class="sxs-lookup"><span data-stu-id="1173c-p110">For a project confined to a small number of people, a single level of Azure AD-based access groups added to the SharePoint groups of the site will fit most scenarios. However, if you have a large number of people and those people are already members of established Azure AD groups, you can more easily assign SharePoint permissions by using nested groups, or groups that contain other groups as members.</span></span>
  
<span data-ttu-id="1173c-p111">例如，您希望创建独立的 SharePoint 在线的团队站点的销售、 市场营销、 工程、 法律、 高级管理人员之间的协作和支持部门，这些部门已经自己与高级管理人员的用户帐户的组成员资格。而不是为新网站成员创建一个新组并将所有单个执行用户帐户放在它，放入新组中的每个部门的现有行政组。</span><span class="sxs-lookup"><span data-stu-id="1173c-p111">For example, you want to create an isolated SharePoint online team site for collaboration among the executives of the sales, marketing, engineering, legal, and support departments and those departments already their own groups with executive user account membership. Rather than creating a new group for the new site members and placing all the individual executive user accounts in it, put the existing executive groups for each department in the new group.</span></span>
  
 <span data-ttu-id="1173c-p112">如果您要共享的 Office 365 订阅多个组织之间，组织一个独立网站用户组成员资格的单级可能变得难以管理由于庞大数量的用户帐户。在这种情况下，可以使用嵌套的每个组织的 Azure AD 组，包含在其组织内的组管理权限。</span><span class="sxs-lookup"><span data-stu-id="1173c-p112">If you are sharing an Office 365 subscription between multiple organizations, a single level of group membership for an isolated site for an organization might become difficult to manage due to the sheer number of user accounts. In this case, you can use nested Azure AD groups for each organization that contain the groups within their organizations to manage the permissions.</span></span>
  
<span data-ttu-id="1173c-177">若要使用嵌套 Azure AD 组：</span><span class="sxs-lookup"><span data-stu-id="1173c-177">To use nested Azure AD groups:</span></span>
  
1. <span data-ttu-id="1173c-178">标识或创建将包含用户帐户，并添加适当的用户帐户作为其成员的 Azure AD 组。</span><span class="sxs-lookup"><span data-stu-id="1173c-178">Identify or create the Azure AD groups that will contain user accounts and add the appropriate user accounts as members.</span></span>
    
2. <span data-ttu-id="1173c-179">创建将包含其他 Azure AD 组并且将这些组作为成员添加容器 Azure 基于 AD 的访问组。</span><span class="sxs-lookup"><span data-stu-id="1173c-179">Create the container Azure AD-based access group that will contain the other Azure AD groups and add those groups as members.</span></span>
    
3.  <span data-ttu-id="1173c-180">对于适当的容器访问组的访问级别，确定 SharePoint 组和相应的权限级别。</span><span class="sxs-lookup"><span data-stu-id="1173c-180">For the appropriate level of access for the container access group, identify the SharePoint group and corresponding permission level.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1173c-181">您不能使用 Office 365 的嵌套的组。</span><span class="sxs-lookup"><span data-stu-id="1173c-181">You cannot use nested Office 365 groups.</span></span> 
  
<span data-ttu-id="1173c-182">这是一种嵌套的 Azure AD 组 ProjectX 成员访问组。</span><span class="sxs-lookup"><span data-stu-id="1173c-182">Here is an example of nested Azure AD groups for the ProjectX member access group.</span></span>
  
![对 ProjectX 网站的成员访问组使用嵌套访问组的示例。](images/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
<span data-ttu-id="1173c-184">因为研究、 工程和项目中的用户帐户的所有潜在顾客团队都应是网站成员，很容易将它们的 Azure AD 组添加到 ProjectX 成员访问组。</span><span class="sxs-lookup"><span data-stu-id="1173c-184">Because all of the user accounts in the Research, Engineering, and Project leads teams are intended to be site members, it is easier to add their Azure AD groups to the ProjectX Members access group.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="1173c-185">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1173c-185">Next step</span></span>

<span data-ttu-id="1173c-186">当您准备创建和配置生产中一个独立的网站时，请参见[部署独立的在线 SharePoint 工作组网站](deploy-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="1173c-186">When you are ready to create and configure an isolated site in production, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1173c-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1173c-187">See Also</span></span>

[<span data-ttu-id="1173c-188">SharePoint Online 的独立的团队站点</span><span class="sxs-lookup"><span data-stu-id="1173c-188">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="1173c-189">管理独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="1173c-189">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="1173c-190">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="1173c-190">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="1173c-191">部署独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="1173c-191">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



