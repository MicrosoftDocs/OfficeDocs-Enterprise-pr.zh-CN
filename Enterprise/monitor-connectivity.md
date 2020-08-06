---
title: 监视 Microsoft 365 连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: 部署 Microsoft 365 后，可以使用下面的一些工具和技术来维护 Microsoft 365 连接。你将需要了解官方服务运行状况和连续性准则以及我们在慢速网络上使用 Microsoft 365 的最佳做法。
ms.openlocfilehash: aa47ff76f70e48285c6ca5f21ffdf30f1db52521
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571005"
---
# <a name="monitor-microsoft-365-connectivity"></a><span data-ttu-id="8bbcc-104">监视 Microsoft 365 连接</span><span class="sxs-lookup"><span data-stu-id="8bbcc-104">Monitor Microsoft 365 connectivity</span></span>

<span data-ttu-id="8bbcc-105">部署 Microsoft 365 后，可以使用下面的一些工具和技术来维护 Microsoft 365 连接。</span><span class="sxs-lookup"><span data-stu-id="8bbcc-105">Once you've deployed Microsoft 365, you can maintain Microsoft 365 connectivity using some of the tools and techniques below.</span></span> <span data-ttu-id="8bbcc-106">你将需要了解官方[服务运行状况和连续性](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity)准则以及我们[在慢速网络上使用 Microsoft 365 的最佳做法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。</span><span class="sxs-lookup"><span data-stu-id="8bbcc-106">You'll want to understand the official [Service Health and Continuity](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) guidelines as well as our [Best practices for using Microsoft 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166).</span></span> <span data-ttu-id="8bbcc-107">你还需要获取[microsoft 365 管理应用](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)并[为 microsoft 365 For Business-管理员帮助](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)添加书签。</span><span class="sxs-lookup"><span data-stu-id="8bbcc-107">You'll also want to grab the [Microsoft 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Microsoft 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-microsoft-365-connectivity"></a><span data-ttu-id="8bbcc-108">监视 Microsoft 365 连接</span><span class="sxs-lookup"><span data-stu-id="8bbcc-108">Monitoring Microsoft 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="8bbcc-109">**收到新的 Microsoft 365 终结点通知**</span><span class="sxs-lookup"><span data-stu-id="8bbcc-109">**Getting notified of new Microsoft 365 endpoints**</span></span> <br/> |<span data-ttu-id="8bbcc-110">如果你正在[管理 Microsoft 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)，则需要在发布新终结点时接收通知，你可以使用你喜爱的 rss 阅读器订阅我们的 rss 源。</span><span class="sxs-lookup"><span data-stu-id="8bbcc-110">If you're [Managing Microsoft 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader.</span></span> <span data-ttu-id="8bbcc-111">下面介绍如何[通过 Outlook 进行订阅](https://go.microsoft.com/fwlink/p/?LinkId=532416)，或者您可以通过[电子邮件将 rss 源更新到您](https://go.microsoft.com/fwlink/p/?LinkId=532417)。</span><span class="sxs-lookup"><span data-stu-id="8bbcc-111">Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>  <br/> |
|<span data-ttu-id="8bbcc-112">**使用 System Center 监视 Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="8bbcc-112">**Use System Center to Monitor Microsoft 365**</span></span> <br/> |<span data-ttu-id="8bbcc-113">如果使用的是 Microsoft System Center，可以下载适用于[Office 365 的 System Center 管理包](https://www.microsoft.com/download/details.aspx?id=43708)，以便立即开始监视 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="8bbcc-113">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Microsoft 365 today.</span></span> <span data-ttu-id="8bbcc-114">有关更多详细指导，请参阅管理包操作指南或此博客文章[Office365 使用 System 中心 Operations Manager 进行监视](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span><span class="sxs-lookup"><span data-stu-id="8bbcc-114">For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="8bbcc-115">**监视 Azure ExpressRoute 运行状况**</span><span class="sxs-lookup"><span data-stu-id="8bbcc-115">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="8bbcc-116">如果使用 Azure ExpressRoute for Microsoft 365 连接到 Microsoft 365，您需要确保使用的是 Microsoft 365 服务运行状况仪表板以及 azure[资源运行状况降低故障排除时间](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span><span class="sxs-lookup"><span data-stu-id="8bbcc-116">If you are connecting to Microsoft 365 using Azure ExpressRoute for Microsoft 365, you'll want to ensure that you're using both the Microsoft 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="8bbcc-117">**将 Azure AD Connect Health 与 AD FS 一起使用**</span><span class="sxs-lookup"><span data-stu-id="8bbcc-117">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="8bbcc-118">如果要使用 AD FS 进行单一登录（使用 Microsoft 365），则需要开始[使用 AZURE AD Connect Health 来监视 AD fs 基础结构](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)。</span><span class="sxs-lookup"><span data-stu-id="8bbcc-118">If you're using AD FS for Single Sign-On with Microsoft 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="8bbcc-119">**以编程方式监视 Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="8bbcc-119">**Programmatically monitor Microsoft 365**</span></span> <br/> |<span data-ttu-id="8bbcc-120">请参阅我们关于[Microsoft 365 管理 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)的指导。</span><span class="sxs-lookup"><span data-stu-id="8bbcc-120">Refer to our guidance on the [Microsoft 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="8bbcc-121">以下是可以用于返回的简短链接：[https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="8bbcc-121">Here's a short link you can use to come back: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8bbcc-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8bbcc-122">See also</span></span>

[<span data-ttu-id="8bbcc-123">配置 Microsoft 365 企业版服务和应用程序</span><span class="sxs-lookup"><span data-stu-id="8bbcc-123">Configure Microsoft 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="8bbcc-124">为你的组织准备好 Microsoft 365 企业版</span><span class="sxs-lookup"><span data-stu-id="8bbcc-124">Get your organization ready for Microsoft 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="8bbcc-125">Microsoft 365 网络计划和性能优化</span><span class="sxs-lookup"><span data-stu-id="8bbcc-125">Network planning and performance tuning for Microsoft 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="8bbcc-126">Microsoft 365 与本地环境的集成</span><span class="sxs-lookup"><span data-stu-id="8bbcc-126">Microsoft 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="8bbcc-127">管理 Microsoft 365 终结点</span><span class="sxs-lookup"><span data-stu-id="8bbcc-127">Managing Microsoft 365 endpoints</span></span>](managing-office-365-endpoints.md)
