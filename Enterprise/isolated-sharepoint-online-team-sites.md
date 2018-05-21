---
title: 单独的 SharePoint Online 团队网站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: 摘要：了解有关单独的 SharePoint Online 团队网站的用法。
ms.openlocfilehash: 86aa5fb9fa4d4eb2f76e1e32a6fcd8bda7b29b76
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2018
---
# <a name="isolated-sharepoint-online-team-sites"></a><span data-ttu-id="97e1b-103">单独的 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="97e1b-103">Isolated SharePoint Online team sites</span></span>

 <span data-ttu-id="97e1b-104">**摘要：** 了解有关单独的 SharePoint Online 团队网站的用法。</span><span class="sxs-lookup"><span data-stu-id="97e1b-104">**Summary:** Learn about the uses for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="97e1b-p101">SharePoint Online 团队网站是在 Microsoft Office 365 中为笔记、文档、文章、日历和其他资源协作快速创建专属空间的一种简单方法。SharePoint Online 团队网站基于 Office 365 组，它具有一个简化的管理模型，允许与一组私有组成员或整个组织展开开放式协作。默认 SharePoint Online 团队网站允许 Office 365 组的成员邀请其他用户并控制权限设置。</span><span class="sxs-lookup"><span data-stu-id="97e1b-p101">SharePoint Online team sites are an easy way to quickly create a space for collaboration of notes, documents, articles, a calendar, and other resources in Microsoft Office 365. SharePoint Online team sites are based on an Office 365 group and have a simplified administration model to allow open collaboration with a private set of group members or the entire organization. A default SharePoint Online team site allows members of the Office 365 group to invite other users and control permissions settings.</span></span>
  
<span data-ttu-id="97e1b-p102">但是，在某些情况下，你想要创建用于协作的 SharePoint Online 团队网站，其权限通过组成员身份和仅由 SharePoint 管理员负责管理的 SharePoint Online 权限级别进行紧密控制。我们称之为单独网站，它独立于正在协作、查看其内容或管理网站的用户组。对于以下情况，你可能需要一个单独的网站：</span><span class="sxs-lookup"><span data-stu-id="97e1b-p102">However, in some cases, you want to create a SharePoint Online team site for collaboration where the permissions of that site are more tightly controlled through group membership and SharePoint Online permission levels, which are only managed by SharePoint administrators. We call this an isolated site, which is isolated to the set of users that are either collaborating, viewing its contents, or administering the site. You might need an isolated site for the following:</span></span>
  
- <span data-ttu-id="97e1b-111">组织内的一个机密项目。</span><span class="sxs-lookup"><span data-stu-id="97e1b-111">A secret project within your organization.</span></span>
    
- <span data-ttu-id="97e1b-112">对于组织高度敏感或宝贵的知识产权的位置。</span><span class="sxs-lookup"><span data-stu-id="97e1b-112">The location for highly-sensitive or valuable intellectual property for your organization.</span></span>
    
- <span data-ttu-id="97e1b-113">组织所采取的法律行动的资源或组织受约束的资源。</span><span class="sxs-lookup"><span data-stu-id="97e1b-113">The resources for a legal action taken by your organization or that to which it is being subjected.</span></span>
    
- <span data-ttu-id="97e1b-114">在具有某些重叠的多个组织之间共享 Office 365 订阅，但大多数情况下都作为单独业务实体存在。</span><span class="sxs-lookup"><span data-stu-id="97e1b-114">To share an Office 365 subscription between multiple organizations that have some overlap, but for the most part exist as separate business entities.</span></span>
    
<span data-ttu-id="97e1b-115">下面是单独网站的要求：</span><span class="sxs-lookup"><span data-stu-id="97e1b-115">Here are the requirements of an isolated site:</span></span>
  
- <span data-ttu-id="97e1b-116">只有 SharePoint Online 管理员可以执行网站管理，其中包括访问网站和配置自定义权限的组成员身份。</span><span class="sxs-lookup"><span data-stu-id="97e1b-116">Only SharePoint Online administrators can perform site administration, which includes group membership for access to the site and configuring custom permissions.</span></span>
    
- <span data-ttu-id="97e1b-117">网站成员不能邀请其他成员到团队网站。</span><span class="sxs-lookup"><span data-stu-id="97e1b-117">Members of the site cannot invite other members to the team site.</span></span>
    
- <span data-ttu-id="97e1b-p103">不是单独网站成员的用户不能请求对该网站的访问。当他们尝试访问与该网站相关联的任何 URL 时，将会收到拒绝访问网页的消息。</span><span class="sxs-lookup"><span data-stu-id="97e1b-p103">Users who are not members of the isolated site cannot request access to the site. They will receive an access denied web page when they attempt to access any URL associated with the site.</span></span>
    
<span data-ttu-id="97e1b-p104">通过 SharePoint Online 管理员要求进行集中式访问控制和自定义权限的折衷方案是，随着时间的推移，该网站仍然保持独立。例如，当前成员不能以有意或无意的方式在 Office 365 订阅中邀请不是该网站成员的其他用户或为其配置自定义权限。</span><span class="sxs-lookup"><span data-stu-id="97e1b-p104">The tradeoff of requiring centralized access control and custom permissions by SharePoint Online administrators is that the site remains isolated over time. For example, current members cannot, either intentionally or accidentally, invite or configure custom permissions for other users within the Office 365 subscription who should not be members of the site.</span></span>
  
<span data-ttu-id="97e1b-122">单独网站可以与其他功能结合使用，例如：</span><span class="sxs-lookup"><span data-stu-id="97e1b-122">An isolated site can be used with other features, such as:</span></span>
  
- <span data-ttu-id="97e1b-123">信息权限管理，用于确保网站上的资源保持加密，即使在本地下载资源并将其上传到在整个组织中可用的其他站点。</span><span class="sxs-lookup"><span data-stu-id="97e1b-123">Information Rights Management to ensure that the resources on the site remain encrypted, even if they are downloaded locally and uploaded to another site that is available to the entire organization.</span></span>
    
- <span data-ttu-id="97e1b-124">数据丢失防护，用于防止用户发送该网站的资源（如文件、电子邮件）。</span><span class="sxs-lookup"><span data-stu-id="97e1b-124">Data loss prevention to prevent users from sending the resources of the site, such as files, in email.</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="97e1b-125">后续步骤</span><span class="sxs-lookup"><span data-stu-id="97e1b-125">Next steps</span></span>

<span data-ttu-id="97e1b-126">若要在试用版订阅中尝试创建单独的 SharePoint Online 团队网站，请参阅[单独的 SharePoint Online 团队网站开发/测试环境](isolated-sharepoint-online-team-site-dev-test-environment.md)中的分步说明。</span><span class="sxs-lookup"><span data-stu-id="97e1b-126">To try out an isolated SharePoint Online team site in a trial subscription, see the step-by-step instructions in [Isolated SharePoint Online team site dev/test environment](isolated-sharepoint-online-team-site-dev-test-environment.md).</span></span>
  
<span data-ttu-id="97e1b-127">当准备好在生产中部署单独的 SharePoint Online 团队网站后，请参阅[设计单独的 SharePoint Online 团队网站](design-an-isolated-sharepoint-online-team-site.md)中的分步设计注意事项。</span><span class="sxs-lookup"><span data-stu-id="97e1b-127">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="97e1b-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97e1b-128">See Also</span></span>

<span data-ttu-id="97e1b-129">[设计单独的 SharePoint Online 团队网站](design-an-isolated-sharepoint-online-team-site.md)</span><span class="sxs-lookup"><span data-stu-id="97e1b-129">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
[<span data-ttu-id="97e1b-130">管理单独的 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="97e1b-130">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="97e1b-131">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="97e1b-131">Security solutions</span></span>](security-solutions.md)

<span data-ttu-id="97e1b-132">[部署单独的 SharePoint Online 团队网站](deploy-an-isolated-sharepoint-online-team-site.md)</span><span class="sxs-lookup"><span data-stu-id="97e1b-132">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>


