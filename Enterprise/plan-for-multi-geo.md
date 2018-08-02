---
title: 规划 OneDrive for Business 多地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解 OneDrive for Business 多地理位置、多地理位置的工作方式，以及哪些地理位置可用于数据存储。
ms.openlocfilehash: 26dc9d1b0f0f78e1740088036be4b77bea3ce176
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2018
ms.locfileid: "21549983"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="0c7f7-103">规划 OneDrive for Business 多地理位置</span><span class="sxs-lookup"><span data-stu-id="0c7f7-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="0c7f7-104">本指南主要面向跨国合公司 (MNC) 的管理员，帮助他们根据公司的经营情况准备将 SharePoint Online 租户扩展到其他地区，以满足数据驻留需求。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="0c7f7-p101">在 OneDrive 多地理位置配置中，Office 365 租户由中心位置（也称为默认位置）以及一个或多个附属地理位置组成。这是一个横跨多个地理位置的单个租户。在 OneDrive 多地理位置中，你的租户信息（包括地理位置）在 Azure Active Directory (AAD) 中进行管控。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="0c7f7-108">下面是一些关键的多地理位置术语，可以帮助你了解配置的基本概念：</span><span class="sxs-lookup"><span data-stu-id="0c7f7-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="0c7f7-109">**租户** - Office 365 云中组织的表示形式，其通常具有一个或多个与之关联的域，例如，http://contoso.sharepoint.com)。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="0c7f7-p102">**地理位置** – 托管租户数据的地理位置。多地理位置租户跨多个地理位置，例如，北美和欧洲。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="0c7f7-112">**允许数据位置 (ADL)** – 租户已配置为托管 OneDrive 和 SharePoint 数据的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="0c7f7-p103">**首选数据位置 (PDL)** – 其中存储单个用户 OneDrive 数据的地理位置。这可由管理员设置为任何一个已为租户配置的允许数据位置。注意，如果更改了已具有 OneDrive 站点的用户的 PDL，则其 OneDrive 数据不会自动移动到新的地理位置。请参阅[将 OneDrive 库移动到其他地理位置](move-onedrive-between-geo-locations.md)，了解更多信息。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="0c7f7-117">启用多地理位置需要四个关键步骤：</span><span class="sxs-lookup"><span data-stu-id="0c7f7-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="0c7f7-118">与你的帐户团队协作，_在 Office 365 服务计划中添加多地理位置功能_。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="0c7f7-119">选择需要的附属地理位置并将其添加到租户。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="0c7f7-p104">将用户的首选数据位置设置为所需的附属地理位置。在为用户预配新的 OneDrive 站点时，会将该位置预配到其 PDL。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="0c7f7-122">根据需要，将用户的现有 OneDrive 站点从起始点位置迁移到首选的数据位置。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="0c7f7-123">请参阅[配置 OneDrive for Business 多地理位置](multi-geo-tenant-configuration.md)，了解有关每个步骤的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c7f7-p105">注意，Office 365 的多地理功能不是专为性能优化情况而设计的，它们主要是为了满足数据驻留需求。有关 Office 365 性能优化的信息，请参阅[针对 Office 365 的网络规划和性能优化](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)，或联系支持小组。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="0c7f7-p106">你可以将任何以下地理位置配置为可托管 OneDrive 文件的附属地理位置。规划多地理位置时，创建一个想要向 Office 365 租户添加的位置列表。我们建议从一个或两个附属位置开始，然后根据需要逐渐扩展到更多的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="0c7f7-129"><strong>位置</strong></span><span class="sxs-lookup"><span data-stu-id="0c7f7-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="0c7f7-130"><strong>代码</strong></span><span class="sxs-lookup"><span data-stu-id="0c7f7-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="0c7f7-131">亚太地区</span><span class="sxs-lookup"><span data-stu-id="0c7f7-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="0c7f7-132">APC</span><span class="sxs-lookup"><span data-stu-id="0c7f7-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0c7f7-133">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="0c7f7-133">Australia</span></span></td>
<td align="left"><span data-ttu-id="0c7f7-134">AUS</span><span class="sxs-lookup"><span data-stu-id="0c7f7-134">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0c7f7-135">加拿大</span><span class="sxs-lookup"><span data-stu-id="0c7f7-135">Canada</span></span></td>
<td align="left"><span data-ttu-id="0c7f7-136">CAN</span><span class="sxs-lookup"><span data-stu-id="0c7f7-136">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0c7f7-137">欧洲/中东/非洲</span><span class="sxs-lookup"><span data-stu-id="0c7f7-137">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="0c7f7-138">EUR</span><span class="sxs-lookup"><span data-stu-id="0c7f7-138">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0c7f7-139">法国</span><span class="sxs-lookup"><span data-stu-id="0c7f7-139">France</span></span></td>
<td align="left"><span data-ttu-id="0c7f7-140">FRA</span><span class="sxs-lookup"><span data-stu-id="0c7f7-140">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0c7f7-141">日本</span><span class="sxs-lookup"><span data-stu-id="0c7f7-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="0c7f7-142">JPN</span><span class="sxs-lookup"><span data-stu-id="0c7f7-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0c7f7-143">韩国</span><span class="sxs-lookup"><span data-stu-id="0c7f7-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="0c7f7-144">KOR</span><span class="sxs-lookup"><span data-stu-id="0c7f7-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0c7f7-145">北美</span><span class="sxs-lookup"><span data-stu-id="0c7f7-145">North America</span></span></td>
<td align="left"><span data-ttu-id="0c7f7-146">NAM</span><span class="sxs-lookup"><span data-stu-id="0c7f7-146">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0c7f7-147">英国</span><span class="sxs-lookup"><span data-stu-id="0c7f7-147">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="0c7f7-148">GBR</span><span class="sxs-lookup"><span data-stu-id="0c7f7-148">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="0c7f7-149">即将新增的地理位置：</span><span class="sxs-lookup"><span data-stu-id="0c7f7-149">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="0c7f7-150">印度</span><span class="sxs-lookup"><span data-stu-id="0c7f7-150">India</span></span>

<span data-ttu-id="0c7f7-p107">配置多地理位置时，请考虑借此机会在迁移到 Office 365 时合并本地基础结构。例如，如果你在新加坡和马来西亚有本地服务器场，则可以将它们合并到 APC 附属位置，前提是数据驻留要求允许你执行此操作。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="0c7f7-153">最佳做法</span><span class="sxs-lookup"><span data-stu-id="0c7f7-153">Best practices</span></span>

<span data-ttu-id="0c7f7-p108">我们建议在 Office 365 中创建一个测试用户，进行一些初始测试。在将 OneDrive 多地理位置功能载入生产用户时，我们将使用此用户进行一些测试和验证步骤。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="0c7f7-p109">在使用测试用户完成测试后，选择一个试点组（可能来自 IT 部门）作为首个在新地理位置使用 OneDrive 的用户。对于此首个小组，请选择尚未拥有 OneDrive 的用户。我们建议这个初始小组的人数不超过 5 个，然后逐渐扩大，最终再批量推广。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="0c7f7-p110">每个用户都应设置“首选数据位置”**(PDL)，以便 Office 365 可以确定在哪个地理位置预配 OneDrive。用户的首选数据位置必须与所选附属位置或中心位置相匹配。虽然 PDL 字段不是强制性的，但我们建议为所有用户设置一个 PDL。没有 PDL 的用户的工作负载将在中央位置基于多地理位置逻辑进行预配。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="0c7f7-p111">创建一个用户列表，并包含他们的用户主体名称 (UPN) 和相应首选数据位置的位置代码。首先包含你的测试用户和初始试点组。在配置过程中你将需要使用这个列表。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="0c7f7-p112">如果你的用户从本地 Active Directory (AD) 系统同步到 Azure Active Directory (AAD)，则必须使用 Azure Active Directory Connect 为同步的用户设置首选数据位置。你不能使用 Azure AD PowerShell 直接为同步用户配置首选数据位置。在 AD 中设置 PDL 并对其进行同步的步骤，请参阅 [Azure Active Directory Connect 同步：为 Office 365 资源配置首选数据位置](https://docs.microsoft.com/zh-CN/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/zh-CN/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="0c7f7-p113">多地理位置租户的管理可能与非多地理位置租户不同，因为许多 SharePoint 和 OneDrive 设置和服务都具有多地理位置意识。我们建议你在继续配置之前先查看[管理多地理位置环境](administering-a-multi-geo-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="0c7f7-171">请阅读[多地理位置环境中的用户体验](multi-geo-user-experience.md)，详细了解关于最终用户在多地理位置环境中的体验。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-171">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="0c7f7-172">要开始配置 OneDrive for Business 多地理位置，请参阅[配置 OneDrive for Business 多地理位置](multi-geo-tenant-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-172">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="0c7f7-173">完成配置后，记得根据需要[迁移用户的 OneDrive 库](move-onedrive-between-geo-locations.md)，以便让用户从首选数据位置工作。</span><span class="sxs-lookup"><span data-stu-id="0c7f7-173">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
