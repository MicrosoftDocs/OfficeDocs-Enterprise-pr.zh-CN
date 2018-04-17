---
title: 在 OneDrive 和在线 Office 365 中的 SharePoint 多地区功能
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: 在 OneDrive 和 SharePoint Online 多地区功能的多个地理区域展开您 Office 365 的状态。
ms.openlocfilehash: 3f72158fe05aadfe8a08a5520bf65cd2d0aaa1c6
ms.sourcegitcommit: a81d08c7e8771cb2c232435971e3169d4f7428dc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="97151-103">在 OneDrive 和在线 Office 365 中的 SharePoint 多地区功能</span><span class="sxs-lookup"><span data-stu-id="97151-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="97151-p101">使用 OneDrive 和 SharePoint Online 中多地区功能，组织可以扩展到多个地理区域和/或国家/地区内您现有租户的其 Office 365 的存在。动身去找您的 Microsoft 客户小组注册多国家公司 OneDrive 业务多的地区。</span><span class="sxs-lookup"><span data-stu-id="97151-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="97151-106">与 OneDrive 多的地区，可以预置和存放的数据存储在您选择满足派驻的数据要求，地理位置和在同一时间为人员解锁您全球推出现代生产力的经验。</span><span class="sxs-lookup"><span data-stu-id="97151-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="97151-107">下面是多地区功能如何使您的组织受益：</span><span class="sxs-lookup"><span data-stu-id="97151-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="97151-108">作为一个全局连接组织运行单个 Office 365 承租人跨越多个地理位置的程序。</span><span class="sxs-lookup"><span data-stu-id="97151-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="97151-109">通过创建和承载内指定的地理位置静态数据满足数据派驻服务要求。</span><span class="sxs-lookup"><span data-stu-id="97151-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="97151-110">与享受的中心位置用户的同一现代生产效率经验使卫星用户。</span><span class="sxs-lookup"><span data-stu-id="97151-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="97151-111">使用户能够跨地理位置随着其角色的变化，而访问其内容保持不变。</span><span class="sxs-lookup"><span data-stu-id="97151-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="97151-112">调整每个地理位置您共享策略和每个站点的数据丢失防护策略。</span><span class="sxs-lookup"><span data-stu-id="97151-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="97151-113">指定每个地理位置的经理的 eDiscovery 并允许管理定制到地理位置的情况。</span><span class="sxs-lookup"><span data-stu-id="97151-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="97151-114">对于其他地理位置选择唯一的 URL 命名空间 (例如，ContosoEUR.sharepoint.com)。</span><span class="sxs-lookup"><span data-stu-id="97151-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="97151-115">将区域的内部部署数据整合到您的 Office 365 多地区租户。</span><span class="sxs-lookup"><span data-stu-id="97151-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="97151-p102">在多个地区配置中，Office 365 租户组成一个集中的位置 （也称为默认位置） 和一个或多个卫星地理位置。多个地区的关键概念是，单个组织将跨越一个跨多个地理位置。多地区承租人，在地理位置、 组和用户信息，信息被掌握在 Azure 活动目录 (AAD)。因为承租人信息是集中掌握，同步到每个地理位置共享和经验涉及从贵公司的任何人都将包含全局意识。</span><span class="sxs-lookup"><span data-stu-id="97151-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="97151-120">多地区租户配置示例</span><span class="sxs-lookup"><span data-stu-id="97151-120">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="97151-121">通过使用多地区租户，Contoso，北美地区的中心位置可以展开到卫星的 Contoso.com 单个组织伞下的在欧洲和澳大利亚地理位置。设置为欧洲及其首选的数据位置的用户将具有在欧洲他们 OneDrive，而其首选的数据位置为北美地区的用户都将具有其 OneDrive 在美国。</span><span class="sxs-lookup"><span data-stu-id="97151-121">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![世界，显示了 Contoso 的地理位置和其他可用的地理位置地图](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="97151-123">三个简单步骤中获得多个地理特征</span><span class="sxs-lookup"><span data-stu-id="97151-123">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="97151-124">配置多地理方法非常简单：</span><span class="sxs-lookup"><span data-stu-id="97151-124">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="97151-p103">使用您的帐户小组要添加_Office 365 中的多个地区功能_服务计划。他们将引导您添加需要的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="97151-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="97151-127">添加您的附属位置。</span><span class="sxs-lookup"><span data-stu-id="97151-127">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="97151-128">配置您的用户帐户的适当位置。</span><span class="sxs-lookup"><span data-stu-id="97151-128">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="97151-129">多地理状态和可用性</span><span class="sxs-lookup"><span data-stu-id="97151-129">Multi-Geo status and availability</span></span>

<span data-ttu-id="97151-130">OneDrive 多地区目前提供这些地区和国家/地区：</span><span class="sxs-lookup"><span data-stu-id="97151-130">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="97151-131">亚太</span><span class="sxs-lookup"><span data-stu-id="97151-131">Asia-Pacific</span></span>
    
- <span data-ttu-id="97151-132">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="97151-132">Australia</span></span>
    
- <span data-ttu-id="97151-133">加拿大</span><span class="sxs-lookup"><span data-stu-id="97151-133">Canada</span></span>
    
- <span data-ttu-id="97151-134">欧洲联盟 (EMEA)</span><span class="sxs-lookup"><span data-stu-id="97151-134">European Union (EMEA)</span></span>
    
- <span data-ttu-id="97151-135">日本</span><span class="sxs-lookup"><span data-stu-id="97151-135">Japan</span></span>
    
- <span data-ttu-id="97151-136">英国</span><span class="sxs-lookup"><span data-stu-id="97151-136">United Kingdom</span></span>
    
- <span data-ttu-id="97151-137">美国 （北美）</span><span class="sxs-lookup"><span data-stu-id="97151-137">United States (North America)</span></span>
    
- <span data-ttu-id="97151-138">韩国</span><span class="sxs-lookup"><span data-stu-id="97151-138">Korea</span></span>
      
<span data-ttu-id="97151-139">即将到来的地理位置：</span><span class="sxs-lookup"><span data-stu-id="97151-139">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="97151-140">法国</span><span class="sxs-lookup"><span data-stu-id="97151-140">France</span></span>
- <span data-ttu-id="97151-141">印度</span><span class="sxs-lookup"><span data-stu-id="97151-141">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="97151-142">开始使用</span><span class="sxs-lookup"><span data-stu-id="97151-142">Getting started</span></span>

<span data-ttu-id="97151-p104">若要开始使用 OneDrive 业务多的地区，第一步是[规划业务多地理环境为您 OneDrive](plan-for-multi-geo.md)。下一步，[了解有关管理多地理环境](administering-a-multi-geo-environment.md)和[您的用户会多地理环境](multi-geo-user-experience.md)。当您准备将 OneDrive 设置为业务多的地区，[配置您的多个地区的租户](multi-geo-tenant-configuration.md)，然后[移到其新的地理位置的任何现有 OneDrive 站点](move-onedrive-between-geo-locations.md)并[设置搜索](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="97151-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
