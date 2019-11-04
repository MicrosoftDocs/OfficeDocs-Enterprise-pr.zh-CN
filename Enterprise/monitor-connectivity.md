---
title: 监视 Office 365 连接性
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: 部署 Office 365 后，可以使用下面的一些工具和技术保持 Office 36 5 连接。需要了解官方服务运行状况和连续性指南以及在慢速网络中使用 Office 365 的最佳做法。还需要获取 Office 365 管理员应用程序并为“Office 365 商业版 - 管理帮助”添加书签。
ms.openlocfilehash: 385aef73173ea6bab421fae6d10622d7a8fe3c80
ms.sourcegitcommit: 9c39ba0c21fbe86343f825bb589a108ec5f176bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2019
ms.locfileid: "37931690"
---
# <a name="monitor-office-365-connectivity"></a><span data-ttu-id="06d80-105">监视 Office 365 连接性</span><span class="sxs-lookup"><span data-stu-id="06d80-105">Monitor Office 365 connectivity</span></span>

<span data-ttu-id="06d80-p102">部署 Office 365 后，可以使用下面的一些工具和技术保持 Office 36 5 连接。需要了解官方[服务运行状况和连续性](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity)指南以及[在慢速网络中使用 Office 365 的最佳做法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。还需要获取 [Office 365 管理员应用程序](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)并为 [Office 365 商业版 - 管理帮助](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)添加书签。</span><span class="sxs-lookup"><span data-stu-id="06d80-p102">Once you've deployed Office 365, you can maintain Office 365 connectivity using some of the tools and techniques below. You'll want to understand the official [Service Health and Continuity](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) guidelines as well as our [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). You'll also want to grab the [Office 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Office 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-office-365-connectivity"></a><span data-ttu-id="06d80-109">监视 Office 365 连接性</span><span class="sxs-lookup"><span data-stu-id="06d80-109">Monitoring Office 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="06d80-110">**获得有关新 Office 365 终结点的通知**</span><span class="sxs-lookup"><span data-stu-id="06d80-110">**Getting notified of new Office 365 endpoints**</span></span> <br/> |<span data-ttu-id="06d80-p103">如果你要[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)，并且需要在我们发布新终结点时收到通知，可以使用自己喜欢的 RSS 阅读器订阅我们的 RSS 源。下面介绍了如何[通过 Outlook 进行订阅](https://go.microsoft.com/fwlink/p/?LinkId=532416)，或者，可以设置[通过电子邮件向你发送 RSS 源更新](https://go.microsoft.com/fwlink/p/?LinkId=532417)。</span><span class="sxs-lookup"><span data-stu-id="06d80-p103">If you're [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader. Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span></span><br/> |
|<span data-ttu-id="06d80-113">**使用 System Center 监视 Office 365**</span><span class="sxs-lookup"><span data-stu-id="06d80-113">**Use System Center to Monitor Office 365**</span></span> <br/> |<span data-ttu-id="06d80-p104">如果你使用的是 Microsoft System Center，可以下载[适用于 Office 365 的 System Center 管理包](https://www.microsoft.com/download/details.aspx?id=43708)，以便立即开始监视 Office 365。有关详细指导，请参阅管理包操作指南或此博客文章：[使用 System Center Operations Manager 监视 Office365](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span><span class="sxs-lookup"><span data-stu-id="06d80-p104">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Office 365 today. For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="06d80-116">**监视 Azure ExpressRoute 运行状况**</span><span class="sxs-lookup"><span data-stu-id="06d80-116">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="06d80-117">如果使用适用于 Office 365 的 Azure ExpressRoute 连接到 Office 365，则需要确保同时使用 Office 365 服务运行状况仪表板以及 Azure [通过 Azure 资源运行状况减少故障排除时间](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span><span class="sxs-lookup"><span data-stu-id="06d80-117">If you are connecting to Office 365 using Azure ExpressRoute for Office 365, you'll want to ensure that you're using both the Office 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="06d80-118">**将 Azure AD Connect Health 与 AD FS 一起使用**</span><span class="sxs-lookup"><span data-stu-id="06d80-118">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="06d80-119">如果你使用 AD FS 进行 Office 365 单一登录，则需要开始[使用 Azure AD Connect Health 监视 AD FS 基础结构](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)。</span><span class="sxs-lookup"><span data-stu-id="06d80-119">If you're using AD FS for Single Sign-On with Office 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="06d80-120">**以编程方式监视 Office 365**</span><span class="sxs-lookup"><span data-stu-id="06d80-120">**Programmatically monitor Office 365**</span></span> <br/> |<span data-ttu-id="06d80-121">请参阅有关 [Office 365 管理 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) 的指南。</span><span class="sxs-lookup"><span data-stu-id="06d80-121">Refer to our guidance on the [Office 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="06d80-122">以下是可以用于返回的简短链接：[hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="06d80-122">Here's a short link you can use to come back: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="06d80-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06d80-123">See also</span></span>

[<span data-ttu-id="06d80-124">配置 Office 365 企业版服务和应用程序</span><span class="sxs-lookup"><span data-stu-id="06d80-124">Configure Office 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="06d80-125">使组织为部署 Office 365 企业版做好准备</span><span class="sxs-lookup"><span data-stu-id="06d80-125">Get your organization ready for Office 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="06d80-126">Office 365 的网络规划和性能优化</span><span class="sxs-lookup"><span data-stu-id="06d80-126">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="06d80-127">Office 365 与本地环境的集成</span><span class="sxs-lookup"><span data-stu-id="06d80-127">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="06d80-128">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="06d80-128">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
