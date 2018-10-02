---
title: Office 365 的 OneDrive 和 SharePoint Online 中的多地理位置功能
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: 使用 OneDrive 和 SharePoint Online 中的多地理位置功能将 Office 365 的状态扩展到多个地理位置区域。
ms.openlocfilehash: c6648dc8a0b225105e408fc082f6bb4d1a1b4930
ms.sourcegitcommit: 2f138e0733266ab4b179bbe882c734500118dde1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "24012732"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="2e3e0-103">Office 365 的 OneDrive 和 SharePoint Online 中的多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="2e3e0-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="2e3e0-p101">借助 OneDrive 和 SharePoint Online 中的多地理位置功能，你的组织可以将其 Office 365 的存在范围扩展到现有租户内的多个地理区域和/或国家/地区。请联系你的 Microsoft 帐户团队，为你的跨国公司注册 OneDrive for Business 多地理位置。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="2e3e0-106">通过 OneDrive 多地理位置，你可以在选择的地理位置中预配和存储静态数据，以满足数据驻留要求，与此同时，开启面向员工的现代生产力体验的全球推广。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="2e3e0-107">下面说明了多地理位置功能如何让你的组织受益：</span><span class="sxs-lookup"><span data-stu-id="2e3e0-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="2e3e0-108">使用跨多个地理位置的单个 Office 365 租户作为一个全球互联组织运营。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="2e3e0-109">通过在指定的地理位置内创建和托管静态数据，满足数据驻留要求。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="2e3e0-110">为附属地理位置的用户提供与中心位置用户享受的同等现代生产力体验。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="2e3e0-111">允许用户在其角色更改时在各地理位置之间移动，同时保持其内容访问的完整。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="2e3e0-112">定制每个地理位置的共享策略和每个网站的数据丢失防护策略。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="2e3e0-113">指定每个地理位置的电子数据展示管理器并允许根据地理位置定制管理案例。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="2e3e0-114">为其他地理位置选择唯一的 URL 命名空间（例如 ContosoEUR.sharepoint.com）。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="2e3e0-115">将你区域的本地数据整合到 Office 365 多地理位置租户。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="2e3e0-p102">在多地理位置配置中，Office 365 租户由中心位置（也称为默认位置）和一个或多个附属地理位置组成。多地理位置的关键概念是单个租户将跨越多个地理位置。在多地理位置租户中，有关地理位置、组和用户信息的信息在 Azure Active Directory (AAD) 中进行管控。由于你的租户信息被集中管控并同步到每个地理位置，因此，涉及你公司任何人的共享和经验都包含全球意识。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

## <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="2e3e0-120">视频：Office 365 多地理位置简介</span><span class="sxs-lookup"><span data-stu-id="2e3e0-120">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="2e3e0-121">通过简单的三步获取多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="2e3e0-121">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="2e3e0-122">配置多地理位置非常简单：</span><span class="sxs-lookup"><span data-stu-id="2e3e0-122">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="2e3e0-p103">与帐户团队协作，_在 Office 365 服务计划中添加多地理位置功能_。他们将指导你添加所需数量的许可证。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="2e3e0-125">添加附属位置。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-125">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="2e3e0-126">配置相应位置的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-126">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="2e3e0-127">多地理位置状态和可用性</span><span class="sxs-lookup"><span data-stu-id="2e3e0-127">Multi-Geo status and availability</span></span>

<span data-ttu-id="2e3e0-128">目前在以下这些地区和国家提供 OneDrive 多地理位置：</span><span class="sxs-lookup"><span data-stu-id="2e3e0-128">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="2e3e0-129">亚太地区</span><span class="sxs-lookup"><span data-stu-id="2e3e0-129">Asia-Pacific</span></span>
    
- <span data-ttu-id="2e3e0-130">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="2e3e0-130">Australia</span></span>
    
- <span data-ttu-id="2e3e0-131">加拿大</span><span class="sxs-lookup"><span data-stu-id="2e3e0-131">Canada</span></span>
    
- <span data-ttu-id="2e3e0-132">欧盟 (EMEA)</span><span class="sxs-lookup"><span data-stu-id="2e3e0-132">European Union (EMEA)</span></span>

- <span data-ttu-id="2e3e0-133">法国</span><span class="sxs-lookup"><span data-stu-id="2e3e0-133">France</span></span>
    
- <span data-ttu-id="2e3e0-134">日本</span><span class="sxs-lookup"><span data-stu-id="2e3e0-134">Japan</span></span>
    
- <span data-ttu-id="2e3e0-135">英国</span><span class="sxs-lookup"><span data-stu-id="2e3e0-135">United Kingdom</span></span>
    
- <span data-ttu-id="2e3e0-136">美国（北美）</span><span class="sxs-lookup"><span data-stu-id="2e3e0-136">United States (North America)</span></span>
    
- <span data-ttu-id="2e3e0-137">韩国</span><span class="sxs-lookup"><span data-stu-id="2e3e0-137">Korea</span></span>
      
<span data-ttu-id="2e3e0-138">即将新增的地理位置：</span><span class="sxs-lookup"><span data-stu-id="2e3e0-138">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="2e3e0-139">印度</span><span class="sxs-lookup"><span data-stu-id="2e3e0-139">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="2e3e0-140">入门</span><span class="sxs-lookup"><span data-stu-id="2e3e0-140">Getting started</span></span>

<span data-ttu-id="2e3e0-p104">要开始使用 OneDrive for Business 多地理位置，第一步是[规划 OneDrive for Business 多地理位置环境](plan-for-multi-geo.md)。接下来，[了解如何管理多地理位置环境](administering-a-multi-geo-environment.md)，以及[用户将如何体验多地理位置环境](multi-geo-user-experience.md)。当准备好设置 OneDrive for Business 多地理位置时，[为租户配置多地理位置](multi-geo-tenant-configuration.md)，然后[将所有现有 OneDrive 站点移动到新地理位置](move-onedrive-between-geo-locations.md)，并[设置搜索](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="2e3e0-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
