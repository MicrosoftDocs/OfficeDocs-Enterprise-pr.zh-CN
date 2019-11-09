---
title: 管理多地理位置环境
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: 学习如何在多地理位置环境中管理 SharePoint 和 OneDrive 服务。
ms.openlocfilehash: 9d4d35505dc5b0d24dd5b2ada8ff1028b1d0d61b
ms.sourcegitcommit: 5fe1c9be652222d6956c7dad5949ddcf0bd27041
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2019
ms.locfileid: "38076136"
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="10af9-103">管理多地理位置环境</span><span class="sxs-lookup"><span data-stu-id="10af9-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="10af9-104">下文描述了 Office 365 服务在多地理位置环境中的工作方式。</span><span class="sxs-lookup"><span data-stu-id="10af9-104">Here's a look at how Office 365 services work in a multi-geo environment.</span></span>

## <a name="audit-log-search"></a><span data-ttu-id="10af9-105">审核日志搜索</span><span class="sxs-lookup"><span data-stu-id="10af9-105">Audit log search</span></span>

<span data-ttu-id="10af9-106">可以从 Office 365 审核日志搜索页中找到所有附属位置的统一[审核日志](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)。</span><span class="sxs-lookup"><span data-stu-id="10af9-106">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your satellite locations is available from the Office 365 audit log search page.</span></span> <span data-ttu-id="10af9-107">你可以查看跨地理位置的所有审核日志条目，例如，NAM 和 EUR 用户的活动将显示在一个组织视图中，然后你可以应用现有筛选器，查看特定用户的活动。</span><span class="sxs-lookup"><span data-stu-id="10af9-107">You can see all the audit log entries from across geo locations, for example, NAM & EUR users' activities will show up in one org view and then you can apply existing filters to see specific user's activities.</span></span>

## <a name="bcs-secure-store-apps"></a><span data-ttu-id="10af9-108">BCS、安全存储、应用</span><span class="sxs-lookup"><span data-stu-id="10af9-108">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="10af9-109">BCS、安全存储和应用在每个附属位置都具有单独的实例，因此，SharePoint Online 管理员应从每个附属位置单独管理和配置这些服务。</span><span class="sxs-lookup"><span data-stu-id="10af9-109">BCS, Secure Store, and Apps all have separate instances in each satellite location, therefore the SharePoint Online administrator should manage and configure these services separately from each satellite location.</span></span>

## <a name="ediscovery"></a><span data-ttu-id="10af9-110">电子数据展示</span><span class="sxs-lookup"><span data-stu-id="10af9-110">eDiscovery</span></span> 

<span data-ttu-id="10af9-111">默认情况下，电子数据展示管理员或多地理位置租户的管理员将只能在该租户的中心位置执行电子数据展示。</span><span class="sxs-lookup"><span data-stu-id="10af9-111">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant.</span></span> <span data-ttu-id="10af9-112">Office 365 全局管理员必须分配电子数据展示管理者权限，以允许其他人员执行电子数据展示，并在其适用的合规性安全筛选器中分配“Region”参数，以便将要进行电子数据展示的区域指定为附属位置，否则，不会对该附属位置执行任何电子数据展示。</span><span class="sxs-lookup"><span data-stu-id="10af9-112">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span> <span data-ttu-id="10af9-113">若要针对区域配置合规性安全筛选器，请参阅[配置 Office 365 多地理位置电子数据展示](multi-geo-ediscovery-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="10af9-113">To configure the Compliance Security Filter for a Region, see [Configure Office 365 Multi-Geo eDiscovery](multi-geo-ediscovery-configuration.md).</span></span>

## <a name="exchange-mailboxes"></a><span data-ttu-id="10af9-114">Exchange 邮箱</span><span class="sxs-lookup"><span data-stu-id="10af9-114">Exchange mailboxes</span></span>

<span data-ttu-id="10af9-115">如果更改了用户的 PDL，则会自动转移用户的 Exchange 邮箱。</span><span class="sxs-lookup"><span data-stu-id="10af9-115">Users' Exchange mailboxes are moved automatically if their PDL is changed.</span></span> <span data-ttu-id="10af9-116">创建新邮箱时，如果没有为用户的 PDL 设置值，则会将新邮箱预配到用户的 PDL 或中心位置。</span><span class="sxs-lookup"><span data-stu-id="10af9-116">When a new mailbox is created, it is provisioned to the user's PDL or to the central location if no value has been set for the user's PDL.</span></span>

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="10af9-117">信息保护 (IP) 数据丢失防护 (DLP) 策略</span><span class="sxs-lookup"><span data-stu-id="10af9-117">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="10af9-118">可以在“安全性和合规性”中心内为 OneDrive for Business、SharePoint 和 Exchange 设置 IP DLP 策略，并根据需要将策略的适用范围设置为整个租户或适用的用户。</span><span class="sxs-lookup"><span data-stu-id="10af9-118">You can set your IP DLP policies for OneDrive for Business, SharePoint, and Exchange in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users.</span></span> <span data-ttu-id="10af9-119">例如：如果你希望为附属位置中的某个用户选择策略，请选择将策略应用于特定 OneDrive，并输入用户的 OneDrive url。</span><span class="sxs-lookup"><span data-stu-id="10af9-119">For example: If you wish to select a policy for a user in a satellite location, select to apply the policy to a specific OneDrive and enter the user's OneDrive url.</span></span> <span data-ttu-id="10af9-120">有关创建 DLP 的一般指南，请参阅[数据丢失防护策略概述](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)。</span><span class="sxs-lookup"><span data-stu-id="10af9-120">See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="10af9-121">DLP 策略将基于每个地理位置的适用性自动同步。</span><span class="sxs-lookup"><span data-stu-id="10af9-121">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="10af9-122">在 UI 中，无法为地理位置中的所有用户实施信息保护和数据丢失防护策略，你必须为策略选择适用的帐户，或将策略全局应用于所有帐户。</span><span class="sxs-lookup"><span data-stu-id="10af9-122">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable accounts for the policy or apply the policy globally to all accounts.</span></span>

## <a name="microsoft-flow"></a><span data-ttu-id="10af9-123">Microsoft Flow</span><span class="sxs-lookup"><span data-stu-id="10af9-123">Microsoft Flow</span></span>

<span data-ttu-id="10af9-124">为附属位置创建的流程将使用位于租户的默认地理位置中的终结点。</span><span class="sxs-lookup"><span data-stu-id="10af9-124">Flows created for the satellite location will use the end point located in the default geo location for the tenant.</span></span>  <span data-ttu-id="10af9-125">Microsoft Flow 不是多地理位置服务。</span><span class="sxs-lookup"><span data-stu-id="10af9-125">Microsoft Flow is not a Multi-Geo service.</span></span> 

## <a name="microsoft-powerapps"></a><span data-ttu-id="10af9-126">Microsoft PowerApps</span><span class="sxs-lookup"><span data-stu-id="10af9-126">Microsoft PowerApps</span></span>

<span data-ttu-id="10af9-127">为附属位置创建的 PowerApp 将使用位于租户的中心位置中的终结点。</span><span class="sxs-lookup"><span data-stu-id="10af9-127">PowerApps created for the satellite location will use the end point located in the central location for the tenant.</span></span> <span data-ttu-id="10af9-128">Microsoft PowerApps 不是多地理位置服务。</span><span class="sxs-lookup"><span data-stu-id="10af9-128">Microsoft PowerApps is not a Multi-Geo service.</span></span> 

## <a name="onedrive-administrator-experience"></a><span data-ttu-id="10af9-129">OneDrive 管理员体验</span><span class="sxs-lookup"><span data-stu-id="10af9-129">OneDrive Administrator Experience</span></span>

<span data-ttu-id="10af9-p107">[OneDrive 管理中心](https://admin.onedrive.com)的左侧导航栏中有一个“地理位置”\*\*\*\* 选项卡，其中包含地理位置地图，你可在其中查看和管理地理位置。使用此页面可添加或删除租户的地理位置。</span><span class="sxs-lookup"><span data-stu-id="10af9-p107">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

## <a name="security-and-compliance-admin-center"></a><span data-ttu-id="10af9-132">安全与合规管理中心</span><span class="sxs-lookup"><span data-stu-id="10af9-132">Security and Compliance Admin Center</span></span>

<span data-ttu-id="10af9-133">还有一个多地理位置租户的中央合规中心：[Office 365 安全与合规中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)。</span><span class="sxs-lookup"><span data-stu-id="10af9-133">There is one central compliance center for a multi-geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

## <a name="sharepoint-storage-quota"></a><span data-ttu-id="10af9-134">SharePoint 存储配额</span><span class="sxs-lookup"><span data-stu-id="10af9-134">SharePoint storage quota</span></span>

<span data-ttu-id="10af9-135">默认情况下，多地理位置环境中的所有地理位置具有相同的可用租户存储配额。</span><span class="sxs-lookup"><span data-stu-id="10af9-135">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>  <span data-ttu-id="10af9-136">也可通过为特定地理位置分配特定配额来管理存储配额。</span><span class="sxs-lookup"><span data-stu-id="10af9-136">You can also manage the storage quota by allocating a specific quota for a particular geo location.</span></span> <span data-ttu-id="10af9-137">有关详细信息，请参阅 [多地理位置环境中的 SharePoint 存储配额](sharepoint-multi-geo-storage-quota.md)。</span><span class="sxs-lookup"><span data-stu-id="10af9-137">For more information, see [SharePoint storage quotas in multi-geo environments](sharepoint-multi-geo-storage-quota.md).</span></span>

## <a name="sharing"></a><span data-ttu-id="10af9-138">共享</span><span class="sxs-lookup"><span data-stu-id="10af9-138">Sharing</span></span>

<span data-ttu-id="10af9-139">管理员可以为他们的每个位置设置和管理共享策略。</span><span class="sxs-lookup"><span data-stu-id="10af9-139">Administrators can set and manage sharing policies for each of their locations.</span></span> <span data-ttu-id="10af9-140">每个地理位置中的 OneDrive 和 SharePoint 站点将只遵循对应的地理位置特定共享设置。</span><span class="sxs-lookup"><span data-stu-id="10af9-140">The OneDrive and SharePoint sites in each geo location will honor only the corresponding geo specific sharing settings.</span></span> <span data-ttu-id="10af9-141">（例如，你可以为中心位置允许[外部共享](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)，但不能为附属位置允许外部共享，反之亦然。）请注意，共享设置不允许配置地理位置之间的共享限制。</span><span class="sxs-lookup"><span data-stu-id="10af9-141">(For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo locations.</span></span>

## <a name="taxonomy"></a><span data-ttu-id="10af9-142">分类</span><span class="sxs-lookup"><span data-stu-id="10af9-142">Taxonomy</span></span>

<span data-ttu-id="10af9-143">我们支持跨地理位置为企业托管的元数据使用统一[分类](https://docs.microsoft.com/sharepoint/managed-metadata)，并将主分类托管在公司的中心位置中。</span><span class="sxs-lookup"><span data-stu-id="10af9-143">We support a unified [taxonomy](https://docs.microsoft.com/sharepoint/managed-metadata) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company.</span></span> <span data-ttu-id="10af9-144">我们建议你通过中心位置管理全局分类，并仅向附属位置分类中添加特定于位置的术语。</span><span class="sxs-lookup"><span data-stu-id="10af9-144">We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite location's Taxonomy.</span></span> <span data-ttu-id="10af9-145">全局分类术语将同步到附属位置。</span><span class="sxs-lookup"><span data-stu-id="10af9-145">Global taxonomy terms will synchronize to the satellite locations.</span></span>

<span data-ttu-id="10af9-146">有关附加详细信息及开发人员指南，请参阅[管理多地理位置租户中的元数据](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-managedmetadata)。</span><span class="sxs-lookup"><span data-stu-id="10af9-146">See [Manage metadata in a multi-geo tenant](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-managedmetadata) for additional details and for developer guidance.</span></span>

## <a name="user-profile-application"></a><span data-ttu-id="10af9-147">用户配置文件应用程序</span><span class="sxs-lookup"><span data-stu-id="10af9-147">User Profile Application</span></span>

<span data-ttu-id="10af9-148">每个地理位置都有一个[用户配置文件应用程序](https://docs.microsoft.com/sharepoint/manage-user-profiles)。</span><span class="sxs-lookup"><span data-stu-id="10af9-148">There is a [user profile application](https://docs.microsoft.com/sharepoint/manage-user-profiles) in each geo location.</span></span> <span data-ttu-id="10af9-149">每个用户的配置文件信息都托管在其地理位置中，并可供该地理位置的管理员使用。</span><span class="sxs-lookup"><span data-stu-id="10af9-149">Each user's profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="10af9-150">如果你有自定义配置文件属性，建议跨地区使用同一配置文件架构并在所有地理位置或所需的位置填充自定义配置文件属性。</span><span class="sxs-lookup"><span data-stu-id="10af9-150">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span> <span data-ttu-id="10af9-151">有关如何以编程方式填充用户配置文件数据的指导，请参阅[批量用户配置文件更新 API](https://docs.microsoft.com/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)。</span><span class="sxs-lookup"><span data-stu-id="10af9-151">For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).</span></span>

<span data-ttu-id="10af9-152">有关附加信息及开发人员指南，请参阅[在多地理位置租户中使用用户配置文件](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-userprofileexperience)。</span><span class="sxs-lookup"><span data-stu-id="10af9-152">See [Work with user profiles in a multi-geo tenant](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) for additional details and for developer guidance.</span></span>

## <a name="video-portal"></a><span data-ttu-id="10af9-153">视频门户</span><span class="sxs-lookup"><span data-stu-id="10af9-153">Video Portal</span></span>

<span data-ttu-id="10af9-154">在多地理位置租户中，O365 视频门户仅从默认地理位置中获取服务，所有用户都将重定向到该中心门户 url。</span><span class="sxs-lookup"><span data-stu-id="10af9-154">In a multi-geo tenant, the O365 Video Portal is served only from default geo and all users will be redirected to that central portal url.</span></span> <span data-ttu-id="10af9-155">因此，将根据你所在的中心位置使用适用于该地区的远程媒体服务 (RMS) ，如下所示。</span><span class="sxs-lookup"><span data-stu-id="10af9-155">Hence, the Remote Media Service (RMS) for that region will be used, as follows based on your central location.</span></span>

<span data-ttu-id="10af9-156">Stream 当前可在以下地区使用：</span><span class="sxs-lookup"><span data-stu-id="10af9-156">Stream is currently available in the following regions:</span></span>

- <span data-ttu-id="10af9-157">北美地区（托管在美国）</span><span class="sxs-lookup"><span data-stu-id="10af9-157">North America, hosted in the United States</span></span> 
- <span data-ttu-id="10af9-158">欧洲</span><span class="sxs-lookup"><span data-stu-id="10af9-158">Europe</span></span>
- <span data-ttu-id="10af9-159">亚太地区</span><span class="sxs-lookup"><span data-stu-id="10af9-159">Asia Pacific</span></span>

<span data-ttu-id="10af9-160">但是，Stream 尚不支持在以下目前支持 Office 365 视频的地区中使用，因此对于这些本地实例，我们将使用最近的受支持地区中的 RMS。</span><span class="sxs-lookup"><span data-stu-id="10af9-160">However, Stream is not yet available in the following regions that are currently supported for Office 365 Video, therefore for these local instances, we will use the RMS that is in the closest supported region.</span></span>

- <span data-ttu-id="10af9-161">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="10af9-161">Australia</span></span>
- <span data-ttu-id="10af9-162">加拿大</span><span class="sxs-lookup"><span data-stu-id="10af9-162">Canada</span></span>
- <span data-ttu-id="10af9-163">印度</span><span class="sxs-lookup"><span data-stu-id="10af9-163">India</span></span>
- <span data-ttu-id="10af9-164">英国</span><span class="sxs-lookup"><span data-stu-id="10af9-164">United Kingdom</span></span>
