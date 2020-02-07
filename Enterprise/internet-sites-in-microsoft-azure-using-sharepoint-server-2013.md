---
title: Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: 摘要：使用 SharePoint Server 2013 的 Internet 站点得益于托管在 Azure 基础结构服务中。本文提供了用于设计和实现此解决方案的资源。
ms.openlocfilehash: 7791da6954aea49b9292967fe32311c529bedc69
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41845093"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="a766b-104">Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="a766b-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="a766b-p102">**摘要：** 使用 SharePoint Server 2013 的 Internet 站点得益于托管在 Azure 基础结构服务中。本文提供了用于设计和实现此解决方案的资源。</span><span class="sxs-lookup"><span data-stu-id="a766b-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="a766b-107">将 Azure 基础结构服务用于 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="a766b-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="a766b-p103">Microsoft Azure 提供了托管基于 SharePoint Server 2013 的 Internet 站点的极具吸引力的选项。优点包括：</span><span class="sxs-lookup"><span data-stu-id="a766b-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="a766b-110">重点关注开发出色的网站，而不是构建基础结构。</span><span class="sxs-lookup"><span data-stu-id="a766b-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="a766b-111">根据需求灵活地伸缩解决方案。</span><span class="sxs-lookup"><span data-stu-id="a766b-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="a766b-112">仅支付你需要和使用的资源。</span><span class="sxs-lookup"><span data-stu-id="a766b-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="a766b-113">利用客户帐户的 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="a766b-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="a766b-114">添加当前在 Office 365 中不可用的功能，例如深入报告和分析。</span><span class="sxs-lookup"><span data-stu-id="a766b-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="a766b-115">资源</span><span class="sxs-lookup"><span data-stu-id="a766b-115">Resources</span></span>

<span data-ttu-id="a766b-116">以下技术插图和文章提供了有关如何使用 SharePoint Server 2013 在 Azure 中设计和实施 Internet 站点的信息。</span><span class="sxs-lookup"><span data-stu-id="a766b-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="a766b-117">**Resource**</span><span class="sxs-lookup"><span data-stu-id="a766b-117">**Resource**</span></span>|<span data-ttu-id="a766b-118">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="a766b-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a766b-119">**Azure** 中的 SharePoint Server 2013 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="a766b-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="a766b-120">[![使用 SharePoint 的 Azure 中的 Internet 网站图像](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="a766b-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="a766b-121">[](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| PDF [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="a766b-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="a766b-122">此体系结构模型概述了 Azure 中适用于 Internet 站点的关键设计活动和建议的体系结构选择。</span><span class="sxs-lookup"><span data-stu-id="a766b-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="a766b-123">**设计示例：适用于 SharePoint Server 2013 的 Azure 中的 Internet 站点**</span><span class="sxs-lookup"><span data-stu-id="a766b-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="a766b-124">[![设计示例图：Microsoft Azure for SharePoint 2013 中的 Internet 站点](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="a766b-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="a766b-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="a766b-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="a766b-126">将此设计示例作为你自己的体系结构的起点。</span><span class="sxs-lookup"><span data-stu-id="a766b-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="a766b-127">**[SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="a766b-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="a766b-128">本文介绍如何设计用于托管 SharePoint 解决方案的 Azure 体系结构。</span><span class="sxs-lookup"><span data-stu-id="a766b-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

## <a name="see-also"></a><span data-ttu-id="a766b-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a766b-129">See Also</span></span>

[<span data-ttu-id="a766b-130">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="a766b-130">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



