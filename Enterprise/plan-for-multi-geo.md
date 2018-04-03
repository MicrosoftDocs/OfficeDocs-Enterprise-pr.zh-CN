---
title: OneDrive 计划的业务多地区
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解 OneDrive 的业务多地区、 多地区的工作原理，以及哪些地理位置都可用于数据存储。
ms.openlocfilehash: 22ba0f4ebc3fb3c4e11bc0386a1479fa6a889ad8
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="907f4-103">OneDrive 计划的业务多地区</span><span class="sxs-lookup"><span data-stu-id="907f4-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="907f4-104">本指南适用于多国公司 (MNCs) 准备将其扩展到其他地区公司的存在，以满足数据派驻要求按照其 SharePoint Online 租户的管理员。</span><span class="sxs-lookup"><span data-stu-id="907f4-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="907f4-p101">在 OneDrive 多地区配置中，Office 365 租户组成一个集中的位置 （也称为默认位置） 和一个或多个卫星地理位置。这是跨多个地理位置跨越单个租户。OneDrive 多的地区，在您组织的信息，包括地理位置被掌握在 Azure 活动目录 (AAD)。</span><span class="sxs-lookup"><span data-stu-id="907f4-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="907f4-108">以下是一些关键的多地理术语来帮助您了解配置的基本概念：</span><span class="sxs-lookup"><span data-stu-id="907f4-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="907f4-109">**租户**— Office 365 云通常具有与其关联的一个或多个域中的组织表示形式 (例如， http://contoso.sharepoint.com)。</span><span class="sxs-lookup"><span data-stu-id="907f4-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="907f4-p102">**地理位置**--租户的数据所在的地理位置。多地区承租人跨越多个地理位置，例如，北美和欧洲。</span><span class="sxs-lookup"><span data-stu-id="907f4-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="907f4-112">**允许数据位置 (ADL)** – 为您的租户已配置主机 OneDrive 和 SharePoint 数据的地理位置。</span><span class="sxs-lookup"><span data-stu-id="907f4-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="907f4-p103">**首选数据位置 (PDL)** – 存储单个用户的 OneDrive 数据的地理位置。这可以由管理员允许数据位置的租户已配置的任何设置。请注意，是否您更改为已有的 OneDrive 网站的用户 PDL，其 OneDrive 不自动移动数据到新的地理位置。有关详细信息，请参阅[移动到不同的地理位置的 OneDrive 库](move-onedrive-between-geo-locations.md)。</span><span class="sxs-lookup"><span data-stu-id="907f4-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="907f4-117">启用多地区需要四个关键步骤：</span><span class="sxs-lookup"><span data-stu-id="907f4-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="907f4-118">使用您的帐户小组要添加_Office 365 中的多个地区功能_服务计划。</span><span class="sxs-lookup"><span data-stu-id="907f4-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="907f4-119">选择您所需的卫星地理位置并将其添加到您的租户。</span><span class="sxs-lookup"><span data-stu-id="907f4-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="907f4-p104">将您的用户首选的数据位置设置为所需的卫星地理位置。当用户配置新的 OneDrive 站点时，它被调配给他们 PDL。</span><span class="sxs-lookup"><span data-stu-id="907f4-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="907f4-122">它们的首选的数据位置根据需要向主址位置迁移用户现有的 OneDrive 网站。</span><span class="sxs-lookup"><span data-stu-id="907f4-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="907f4-123">有关上述每个步骤的详细信息，请参阅[配置 OneDrive 业务多的地区](multi-geo-tenant-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="907f4-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="907f4-p105">请注意，Office 365 的多地区功能不适用于性能优化的情况下，它们被设计为满足派驻的数据要求。Office 365 的性能优化的相关信息，请参阅[网络规划和性能调优对于 Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)或联系您的支持小组。</span><span class="sxs-lookup"><span data-stu-id="907f4-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="907f4-p106">您可以配置任何以下位置是卫星 OneDrive 文件可以驻留的地理位置。在多个地区的规划，请您想要添加到 Office 365 租户的位置的列表。我们建议以一个或两个卫星位置开始，然后逐渐扩大到更多的地理位置，如果需要。</span><span class="sxs-lookup"><span data-stu-id="907f4-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="907f4-129"><strong>位置</strong></span><span class="sxs-lookup"><span data-stu-id="907f4-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="907f4-130"><strong>代码</strong></span><span class="sxs-lookup"><span data-stu-id="907f4-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="907f4-131">亚太</span><span class="sxs-lookup"><span data-stu-id="907f4-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="907f4-132">APC 公司</span><span class="sxs-lookup"><span data-stu-id="907f4-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="907f4-133">欧洲 / 中东 / 非洲</span><span class="sxs-lookup"><span data-stu-id="907f4-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="907f4-134">欧元</span><span class="sxs-lookup"><span data-stu-id="907f4-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="907f4-135">北美洲</span><span class="sxs-lookup"><span data-stu-id="907f4-135">North America</span></span></td>
<td align="left"><span data-ttu-id="907f4-136">名称</span><span class="sxs-lookup"><span data-stu-id="907f4-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="907f4-137">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="907f4-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="907f4-138">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="907f4-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="907f4-139">加拿大</span><span class="sxs-lookup"><span data-stu-id="907f4-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="907f4-140">可以</span><span class="sxs-lookup"><span data-stu-id="907f4-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="907f4-141">日本</span><span class="sxs-lookup"><span data-stu-id="907f4-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="907f4-142">日文</span><span class="sxs-lookup"><span data-stu-id="907f4-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="907f4-143">韩国</span><span class="sxs-lookup"><span data-stu-id="907f4-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="907f4-144">韩文</span><span class="sxs-lookup"><span data-stu-id="907f4-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="907f4-145">英国</span><span class="sxs-lookup"><span data-stu-id="907f4-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="907f4-146">GBR</span><span class="sxs-lookup"><span data-stu-id="907f4-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="907f4-147">即将到来的地理位置：</span><span class="sxs-lookup"><span data-stu-id="907f4-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="907f4-148">法国</span><span class="sxs-lookup"><span data-stu-id="907f4-148">France</span></span>
- <span data-ttu-id="907f4-149">印度</span><span class="sxs-lookup"><span data-stu-id="907f4-149">India</span></span>

<span data-ttu-id="907f4-p107">配置多个地区时，应考虑合并时迁移到 Office 365 内部部署基础结构的机会。例如，如果可以在新加坡和马来西亚的内部部署服务器场，然后您可以合并它们到 APC 的附属位置，提供数据派驻需求允许您可以做到这一点。</span><span class="sxs-lookup"><span data-stu-id="907f4-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="907f4-152">最佳做法</span><span class="sxs-lookup"><span data-stu-id="907f4-152">Best practices</span></span>

<span data-ttu-id="907f4-p108">我们建议您在 Office 365 执行一些初始测试创建一个测试用户。我们将引导您完成一些测试和验证的步骤与该用户在继续操作之前到板载生产用户到此 OneDrive 多地理特征。</span><span class="sxs-lookup"><span data-stu-id="907f4-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="907f4-p109">一旦完成测试，测试用户，选择一个试验组 – 可能是从您的 IT 部门--是第一次使用 OneDrive 的一个新的地理位置。第一组中，选择用户还没有 OneDrive。我们建议在此第一组不超过五个人，并逐渐展开下一批的推广的做法。</span><span class="sxs-lookup"><span data-stu-id="907f4-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="907f4-p110">每个用户应有设置的*首选的数据位置*(PDL) 以便 Office 365 可以确定在提供其 OneDrive 的地理位置。用户的首选的数据位置必须匹配选定的卫星位置或您的位置中心之一。PDL 字段不是必需的而我们建议为所有用户设置 PDL。将基于多地理逻辑的中心位置在调配的 PDL 没有权限的用户工作负载。</span><span class="sxs-lookup"><span data-stu-id="907f4-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="907f4-p111">创建您的用户的列表，包括其用户主体名称 (UPN) 和适当的首选的数据位置的位置代码。首先，包括测试用户和初始实验组。您需要此列表的配置过程。</span><span class="sxs-lookup"><span data-stu-id="907f4-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="907f4-p112">如果您的用户从内部活动目录 (AD) 系统同步到 Azure 活动目录 (AAD) 的则必须通过使用 Azure 活动目录连接设置同步用户的首选的数据位置。您不能直接配置使用 Azure AD PowerShell 的同步用户的首选的数据位置。在 AD 中设置 PDL 并对其进行同步的步骤中介绍了[Azure 活动目录连接同步： 配置 Office 365 提供资源的首选的数据位置](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="907f4-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="907f4-p113">管理的多个地区租户可以不同于非地理多租户，尽可能多的 SharePoint 和 OneDrive 设置和服务意识多地区。我们建议您查看[管理多地理环境](administering-a-multi-geo-environment.md)之前继续您的配置。</span><span class="sxs-lookup"><span data-stu-id="907f4-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="907f4-170">多地理环境中的最终用户的体验有关的详细信息，请阅读[用户体验在 multgeo 环境中](multi-geo-user-experience.md)。</span><span class="sxs-lookup"><span data-stu-id="907f4-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="907f4-171">要开始配置 OneDrive 业务多的地区，请参阅[配置 OneDrive 业务多的地区](multi-geo-tenant-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="907f4-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="907f4-172">完成配置后，请记住[迁移用户的 OneDrive 库](move-onedrive-between-geo-locations.md)到根据需要获取用户从其首选的数据位置工作。</span><span class="sxs-lookup"><span data-stu-id="907f4-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
