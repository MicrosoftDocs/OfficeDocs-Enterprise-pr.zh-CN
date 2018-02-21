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
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="6d491-103">保护敏感和高度机密的资产的 SharePoint Online 工作组站点</span><span class="sxs-lookup"><span data-stu-id="6d491-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="6d491-104">**摘要：**如何实现 Contoso 敏感保护和高度机密 SharePoint Online 团队更容易，然而安全，协作的行政人员和其研究中心的网站。</span><span class="sxs-lookup"><span data-stu-id="6d491-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers.</span></span>
  
<span data-ttu-id="6d491-p101">Contoso 行政领导想要使用 Office 365 并将他们的文件存储在一个位置进行协作，而不考虑管理人员可能。同样，Contoso 的研究部门 — — 与巴黎、 莫斯科、 纽约、 北京，以及班加罗尔的部门 — — 想要在团队之间过渡到云，用户更容易访问和更开放的协作及其内部数字资产。</span><span class="sxs-lookup"><span data-stu-id="6d491-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="6d491-p102">但是，在这两种情况下，对这些资源的访问必须限于人员有权查看或更改它们，与由 IT 人员管理网站的日常权限的子集。此外，即使某些资源被有意或无意中分布，它们必须加密而且具有权限，以防止那些无权访问要查看或更改它们的内容。</span><span class="sxs-lookup"><span data-stu-id="6d491-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="6d491-109">在 Contoso 的安全和 SharePoint 管理员的 IT 部门决定使用敏感保护和高度机密的 SharePoint Online 工作组站点，如图 1 所示。</span><span class="sxs-lookup"><span data-stu-id="6d491-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="6d491-110">**图 1： 比较敏感的保护和高度机密的在线 SharePoint 工作组网站**</span><span class="sxs-lookup"><span data-stu-id="6d491-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![敏感保护和高度机密的 SharePoint Online 团队网站](images/Contoso_Poster/SP_Solution.png)
  
<span data-ttu-id="6d491-112">Contoso 使用这些步骤来为他们的执行官们和研究小组创建 SharePoint Online 的安全团队站点：</span><span class="sxs-lookup"><span data-stu-id="6d491-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="6d491-113">创建一个**执行官**敏感 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="6d491-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="6d491-114">新工作组网站具有完全控制权限级别的所有者具有编辑 SharePoint 权限级别和少量 SharePoint 管理员帐户的成员作为人员使用现有的 Azure 活动目录 (AD) 组。</span><span class="sxs-lookup"><span data-stu-id="6d491-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="6d491-115">将执行官的文件迁移</span><span class="sxs-lookup"><span data-stu-id="6d491-115">Migrate executives files</span></span>
    
    <span data-ttu-id="6d491-116">将现有的内部行政文件和文件夹移动到新执行官 SharePoint Online 的工作组网站。</span><span class="sxs-lookup"><span data-stu-id="6d491-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="6d491-117">创建**研究**高度机密在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="6d491-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="6d491-p103">新的团队站点使用现有 Azure 广告研究团队组作为具有完全控制权限级别的所有者具有编辑权限级别和少量 SharePoint 管理员帐户的成员。AIP 标签分配研究文件确保对它们进行加密，并只有研究组的成员可以打开它们。</span><span class="sxs-lookup"><span data-stu-id="6d491-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="6d491-120">研究文件迁移</span><span class="sxs-lookup"><span data-stu-id="6d491-120">Migrate research files</span></span>
    
    <span data-ttu-id="6d491-121">移动现有研究小组内部的文件和文件夹到新研究 SharePoint Online 工作组站点。</span><span class="sxs-lookup"><span data-stu-id="6d491-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="6d491-p104">结果是两个由安全和 SharePoint 管理员紧密控制其访问权限的协作站点。使用高度机密的 AIP 的标签的文件，即使分发外部研究工作组站点，它们都将被加密，只能打开由研究小组的成员。</span><span class="sxs-lookup"><span data-stu-id="6d491-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="6d491-124">有关详细信息，请参阅[安全 SharePoint Online 网站和文件](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)。</span><span class="sxs-lookup"><span data-stu-id="6d491-124">For more information, see [Secure SharePoint Online sites and files](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span></span>
  
 <span data-ttu-id="6d491-125">若要设置此功能演示、 概念证明或开发/测试，请参见[安全 SharePoint Online 网站的开发/测试环境](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)。</span><span class="sxs-lookup"><span data-stu-id="6d491-125">To set this up for demonstration, proof-of-concept, or dev/test, see [Secure SharePoint Online sites in a dev/test environment](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6d491-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d491-126">See Also</span></span>

[<span data-ttu-id="6d491-127">Contoso Corporation 的企业方案</span><span class="sxs-lookup"><span data-stu-id="6d491-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="6d491-128">Microsoft 云中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="6d491-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="6d491-129">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="6d491-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="6d491-130">Stretch Database</span><span class="sxs-lookup"><span data-stu-id="6d491-130">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="6d491-131">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="6d491-131">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




