---
title: "为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南"
ms.author: bcarter
author: bcarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: "摘要： 规划和实施指南变化无常的组织具有威胁增加的配置文件。"
ms.openlocfilehash: 632cb63877e159f18707dbf68eb7733082319654
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="0ace4-103">为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南</span><span class="sxs-lookup"><span data-stu-id="0ace4-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="0ace4-104">**摘要：**规划和实施指南变化无常的组织具有威胁增加的配置文件。</span><span class="sxs-lookup"><span data-stu-id="0ace4-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="0ace4-p101">如果您的组织是敏捷，具有较小的 IT 团队，并且威胁档案文件是高于平均，本指南旨在为您。此解决方案演示如何快速生成具有不可或缺的云服务，包括从一开始的安全控制的环境。本指南包含说明性安全建议防止移动设备数据、 标识、 电子邮件、 和访问。</span><span class="sxs-lookup"><span data-stu-id="0ace4-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="0ace4-108">安全解决方案指南</span><span class="sxs-lookup"><span data-stu-id="0ace4-108">Security solution guidance</span></span>

<span data-ttu-id="0ace4-p102">本指南介绍了如何实现安全的云环境。解决方案指南可供任何组织的影响。它包括 BYOD 访问和来宾帐户的敏捷组织的更多帮助。设计您自己的环境，可以作为起始点使用本指南。在[CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com)，我们欢迎您的反馈意见。</span><span class="sxs-lookup"><span data-stu-id="0ace4-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="0ace4-114">**项**</span><span class="sxs-lookup"><span data-stu-id="0ace4-114">**Item**</span></span> <br/> |<span data-ttu-id="0ace4-115">**说明**</span><span class="sxs-lookup"><span data-stu-id="0ace4-115">**Description**</span></span> <br/> |
|<span data-ttu-id="0ace4-116">**政治运动的 Microsoft 安全指南**</span><span class="sxs-lookup"><span data-stu-id="0ace4-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="0ace4-117">[![设置最小海报的拇指钉子。](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="0ace4-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="0ace4-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="0ace4-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span></span>| [<span data-ttu-id="0ace4-119">Visio</span><span class="sxs-lookup"><span data-stu-id="0ace4-119">Visio</span></span>](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx) <br/> |<span data-ttu-id="0ace4-p103">本指南使用作为示例的政治运动组织。本指南用作任何环境的起始点。</span><span class="sxs-lookup"><span data-stu-id="0ace4-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="0ace4-122">**非营利组织的 Microsoft 安全指南**</span><span class="sxs-lookup"><span data-stu-id="0ace4-122">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="0ace4-123">[![可下载文件的 Thumnail 图像](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="0ace4-123">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="0ace4-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="0ace4-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span></span>| [<span data-ttu-id="0ace4-125">Visio</span><span class="sxs-lookup"><span data-stu-id="0ace4-125">Visio</span></span>](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx) <br/> |<span data-ttu-id="0ace4-p104">对于非盈利组织，稍微修改一下本指南。例如，该文件引用 Office 365 非盈利计划。技术指导是政治市场解决方案指南相同。</span><span class="sxs-lookup"><span data-stu-id="0ace4-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="0ace4-129">测试实验室指南</span><span class="sxs-lookup"><span data-stu-id="0ace4-129">Test Lab Guides</span></span>

<span data-ttu-id="0ace4-130">若要创建此解决方案的开发/测试环境，使用下面的测试实验室指南：</span><span class="sxs-lookup"><span data-stu-id="0ace4-130">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="0ace4-131">配置组和用户对于政治市场开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="0ace4-131">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="0ace4-132">创建 Office 365 和 EMS 试用订阅，再创建的组和用户代表的政治活动。</span><span class="sxs-lookup"><span data-stu-id="0ace4-132">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="0ace4-133">在政治运动的开发/测试环境中创建工作组网站</span><span class="sxs-lookup"><span data-stu-id="0ace4-133">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="0ace4-134">创建内部、 专用、 敏感、 和高度机密级别的安全四个 SharePoint Online 的工作组网站。</span><span class="sxs-lookup"><span data-stu-id="0ace4-134">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="0ace4-135">用于演示或概念验证附加的安全功能，请参阅[Office 365 测试实验室指南](http://aka.ms/o365tlgs)。</span><span class="sxs-lookup"><span data-stu-id="0ace4-135">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0ace4-136">See Also</span><span class="sxs-lookup"><span data-stu-id="0ace4-136">See Also</span></span>

[<span data-ttu-id="0ace4-137">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="0ace4-137">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="0ace4-138">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="0ace4-138">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="0ace4-139">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="0ace4-139">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



