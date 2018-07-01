---
title: Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: 摘要：使用 SharePoint Server 2013 的 Internet 站点得益于托管在 Azure 基础结构服务中。本文提供了用于设计和实现此解决方案的资源。
ms.openlocfilehash: a2444cdf98e861530131d55ae80fc661f730ba57
ms.sourcegitcommit: 9f57825b10f20e3813732372541128ef187d52c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "20161785"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="edf70-104">Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="edf70-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="edf70-p102">**摘要：** 使用 SharePoint Server 2013 的 Internet 站点得益于托管在 Azure 基础结构服务中。本文提供了用于设计和实现此解决方案的资源。</span><span class="sxs-lookup"><span data-stu-id="edf70-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="edf70-107">将 Azure 基础结构服务用于 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="edf70-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="edf70-p103">Microsoft Azure 提供了托管基于 SharePoint Server 2013 的 Internet 站点的极具吸引力的选项。优点包括：</span><span class="sxs-lookup"><span data-stu-id="edf70-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="edf70-110">重点关注开发出色的网站，而不是构建基础结构。</span><span class="sxs-lookup"><span data-stu-id="edf70-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="edf70-111">根据需求灵活地伸缩解决方案。</span><span class="sxs-lookup"><span data-stu-id="edf70-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="edf70-112">仅支付你需要和使用的资源。</span><span class="sxs-lookup"><span data-stu-id="edf70-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="edf70-113">利用客户帐户的 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="edf70-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="edf70-114">添加当前在 Office 365 中不可用的功能，例如深入报告和分析。</span><span class="sxs-lookup"><span data-stu-id="edf70-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="edf70-115">资源</span><span class="sxs-lookup"><span data-stu-id="edf70-115">Resources</span></span>

<span data-ttu-id="edf70-116">以下技术插图和文章提供了有关如何使用 SharePoint Server 2013 在 Azure 中设计和实施 Internet 站点的信息。</span><span class="sxs-lookup"><span data-stu-id="edf70-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="edf70-117">**Resource**</span><span class="sxs-lookup"><span data-stu-id="edf70-117">**Resource**</span></span>|<span data-ttu-id="edf70-118">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="edf70-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="edf70-119">**Azure** 中的 SharePoint Server 2013 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="edf70-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="edf70-120">[![使用 SharePoint 的 Azure 中的 Internet 网站图像](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="edf70-120">[![Image of Internet sites in Azure using SharePoint](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="edf70-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552) \| [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="edf70-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="edf70-122">此体系结构模型概述了 Azure 中适用于 Internet 站点的关键设计活动和建议的体系结构选择。</span><span class="sxs-lookup"><span data-stu-id="edf70-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="edf70-123">**设计示例：适用于 SharePoint Server 2013 的 Azure 中的 Internet 站点**</span><span class="sxs-lookup"><span data-stu-id="edf70-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="edf70-124">[![设计示例图：Microsoft Azure for SharePoint 2013 中的 Internet 站点](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="edf70-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="edf70-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="edf70-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="edf70-126">将此设计示例作为你自己的体系结构的起点。</span><span class="sxs-lookup"><span data-stu-id="edf70-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="edf70-127">**[SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="edf70-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="edf70-128">本文介绍如何设计用于托管 SharePoint 解决方案的 Azure 体系结构。</span><span class="sxs-lookup"><span data-stu-id="edf70-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

   
<span data-ttu-id="edf70-129">**参加讨论**</span><span class="sxs-lookup"><span data-stu-id="edf70-129">**Join the discussion**</span></span>

|<span data-ttu-id="edf70-130">**联系我们**</span><span class="sxs-lookup"><span data-stu-id="edf70-130">**Contact us**</span></span>|<span data-ttu-id="edf70-131">**说明**</span><span class="sxs-lookup"><span data-stu-id="edf70-131">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="edf70-132">**你需要什么样的解决方案？**</span><span class="sxs-lookup"><span data-stu-id="edf70-132">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="edf70-p104">我们正在创建跨越多个 Microsoft 云平台和服务的云采用内容。请告诉我们你对云采用内容的想法，或者发送电子邮件至 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 请求获取特定内容。</span><span class="sxs-lookup"><span data-stu-id="edf70-p104">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="edf70-135">**加入云采用讨论**</span><span class="sxs-lookup"><span data-stu-id="edf70-135">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="edf70-p105">如果热衷于基于云的解决方案，请考虑加入云采用咨询委员会 (CAAB)，与充满活力的更大规模社区保持联络，Microsoft 内容开发人员、行业专家和全球各地的客户都已参与其中。若要加入，请将自己添加为 Microsoft 技术社区的[云采用咨询委员会 (CAAB) 空间](https://aka.ms/caab)成员，并迅速向我们 ([CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)) 发送电子邮件。任何人都可以阅读 [CAAB 博客](https://blogs.technet.com/b/solutions_advisory_board/)上与社区相关的内容。不过，CAAB 成员可获邀参加私人网络研讨会，了解新的云采用资源和解决方案。</span><span class="sxs-lookup"><span data-stu-id="edf70-p105">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="edf70-140">**获取您在此处看到的图片**</span><span class="sxs-lookup"><span data-stu-id="edf70-140">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="edf70-p106">若要获取本文中图片的可编辑副本，请告诉我们，我们非常乐意发送副本。请通过电子邮件方式将请求（包括图片的 URL 和标题）发送到 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。</span><span class="sxs-lookup"><span data-stu-id="edf70-p106">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="edf70-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="edf70-143">See Also</span></span>

[<span data-ttu-id="edf70-144">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="edf70-144">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



