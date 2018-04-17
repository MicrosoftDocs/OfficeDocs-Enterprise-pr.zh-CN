---
title: SharePoint Online 的独立的团队站点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: 摘要： 了解独立 SharePoint Online 的团队站点的使用。
ms.openlocfilehash: 358bb16c01c51a76da6557091dacca75e317bf92
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="isolated-sharepoint-online-team-sites"></a><span data-ttu-id="b7219-103">SharePoint Online 的独立的团队站点</span><span class="sxs-lookup"><span data-stu-id="b7219-103">Isolated SharePoint Online team sites</span></span>

 <span data-ttu-id="b7219-104">**摘要：**了解有关用于独立在线 SharePoint 工作组网站的信息。</span><span class="sxs-lookup"><span data-stu-id="b7219-104">**Summary:** Learn about the uses for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="b7219-p101">SharePoint Online 工作组站点是在 Microsoft Office 365 中快速创建协作空间注释、 文档、 文章、 日历和其他资源的简便方法。SharePoint Online 工作组网站基于 Office 365 组并且具有简化的管理模型以允许打开协作与专用组的组成员或整个组织。默认 SharePoint Online 工作组站点允许组成员的 Office 365 可以邀请其他用户并控制权限设置。</span><span class="sxs-lookup"><span data-stu-id="b7219-p101">SharePoint Online team sites are an easy way to quickly create a space for collaboration of notes, documents, articles, a calendar, and other resources in Microsoft Office 365. SharePoint Online team sites are based on an Office 365 group and have a simplified administration model to allow open collaboration with a private set of group members or the entire organization. A default SharePoint Online team site allows members of the Office 365 group to invite other users and control permissions settings.</span></span>
  
<span data-ttu-id="b7219-p102">但是，在某些情况下，您希望创建 SharePoint Online 团队用于协作的站点，该站点的权限更严格控制通过组成员资格和 SharePoint Online 的权限级别，仅由 SharePoint管理员。我们可以称之为独立的站点，即独立于协作，查看其内容，或管理网站用户组。您可能需要一个独立的网站以下：</span><span class="sxs-lookup"><span data-stu-id="b7219-p102">However, in some cases, you want to create a SharePoint Online team site for collaboration where the permissions of that site are more tightly controlled through group membership and SharePoint Online permission levels, which are only managed by SharePoint administrators. We call this an isolated site, which is isolated to the set of users that are either collaborating, viewing its contents, or administering the site. You might need an isolated site for the following:</span></span>
  
- <span data-ttu-id="b7219-111">组织内的秘密项目。</span><span class="sxs-lookup"><span data-stu-id="b7219-111">A secret project within your organization.</span></span>
    
- <span data-ttu-id="b7219-112">用于高度敏感或重要知识产权组织的位置。</span><span class="sxs-lookup"><span data-stu-id="b7219-112">The location for highly-sensitive or valuable intellectual property for your organization.</span></span>
    
- <span data-ttu-id="b7219-113">由您的组织或正在进行，采取法律行动的资源。</span><span class="sxs-lookup"><span data-stu-id="b7219-113">The resources for a legal action taken by your organization or that to which it is being subjected.</span></span>
    
- <span data-ttu-id="b7219-114">若要共享的 Office 365 订阅之间有一些重叠，但在大多数情况下作为单独的业务实体存在的多个组织。</span><span class="sxs-lookup"><span data-stu-id="b7219-114">To share an Office 365 subscription between multiple organizations that have some overlap, but for the most part exist as separate business entities.</span></span>
    
<span data-ttu-id="b7219-115">以下是独立网站的需求：</span><span class="sxs-lookup"><span data-stu-id="b7219-115">Here are the requirements of an isolated site:</span></span>
  
- <span data-ttu-id="b7219-116">只有 SharePoint Online 管理员可以执行网站管理，其中包括访问站点和配置的自定义权限的组成员身份。</span><span class="sxs-lookup"><span data-stu-id="b7219-116">Only SharePoint Online administrators can perform site administration, which includes group membership for access to the site and configuring custom permissions.</span></span>
    
- <span data-ttu-id="b7219-117">网站的成员不能邀请到工作组站点的其他成员。</span><span class="sxs-lookup"><span data-stu-id="b7219-117">Members of the site cannot invite other members to the team site.</span></span>
    
- <span data-ttu-id="b7219-p103">不是独立的网站的成员的用户不能请求访问该网站。他们将接收到访问拒绝网页，当用户尝试访问任何站点相关联的 URL。</span><span class="sxs-lookup"><span data-stu-id="b7219-p103">Users who are not members of the isolated site cannot request access to the site. They will receive an access denied web page when they attempt to access any URL associated with the site.</span></span>
    
<span data-ttu-id="b7219-p104">需要集中式的访问控制和 SharePoint Online 管理员自定义权限的代价是网站随着时间的推移继续保持独立。例如，当前成员不能、 有意或无意，邀请或配置自定义权限的其他用户在 Office 365 订阅者不应为此网站的成员。</span><span class="sxs-lookup"><span data-stu-id="b7219-p104">The tradeoff of requiring centralized access control and custom permissions by SharePoint Online administrators is that the site remains isolated over time. For example, current members cannot, either intentionally or accidentally, invite or configure custom permissions for other users within the Office 365 subscription who should not be members of the site.</span></span>
  
<span data-ttu-id="b7219-122">独立的网站都可用于与其他功能，如：</span><span class="sxs-lookup"><span data-stu-id="b7219-122">An isolated site can be used with other features, such as:</span></span>
  
- <span data-ttu-id="b7219-123">信息权限管理，以确保该站点上的资源保持不加密，即使本地下载和上载到另一个可供整个组织的网站。</span><span class="sxs-lookup"><span data-stu-id="b7219-123">Information Rights Management to ensure that the resources on the site remain encrypted, even if they are downloaded locally and uploaded to another site that is available to the entire organization.</span></span>
    
- <span data-ttu-id="b7219-124">若要禁止用户发送电子邮件中的文件，如资源的网站，数据丢失防范。</span><span class="sxs-lookup"><span data-stu-id="b7219-124">Data loss prevention to prevent users from sending the resources of the site, such as files, in email.</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="b7219-125">后续步骤</span><span class="sxs-lookup"><span data-stu-id="b7219-125">Next steps</span></span>

<span data-ttu-id="b7219-126">若要尝试出独立的 SharePoint Online 工作组网站中试用订阅，请参见[独立 SharePoint Online 团队站点开发/测试环境](isolated-sharepoint-online-team-site-dev-test-environment.md)中的分步说明。</span><span class="sxs-lookup"><span data-stu-id="b7219-126">To try out an isolated SharePoint Online team site in a trial subscription, see the step-by-step instructions in [Isolated SharePoint Online team site dev/test environment](isolated-sharepoint-online-team-site-dev-test-environment.md).</span></span>
  
<span data-ttu-id="b7219-127">当您准备部署在生产环境中的独立的 SharePoint Online 工作组网站时，请参阅[设计独立的在线 SharePoint 工作组网站](design-an-isolated-sharepoint-online-team-site.md)中的分步设计考虑事项。</span><span class="sxs-lookup"><span data-stu-id="b7219-127">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b7219-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7219-128">See Also</span></span>

[<span data-ttu-id="b7219-129">设计独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="b7219-129">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="b7219-130">管理独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="b7219-130">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="b7219-131">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="b7219-131">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="b7219-132">部署独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="b7219-132">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)


