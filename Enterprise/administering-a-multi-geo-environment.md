---
title: 管理多地理位置环境
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 学习如何在多地理位置环境中管理 SharePoint 和 OneDrive 服务。
ms.openlocfilehash: 12da695b44c5102c985a8d64960b1d20e092c8cd
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2018
ms.locfileid: "21550055"
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="e4fdb-103">管理多地理位置环境</span><span class="sxs-lookup"><span data-stu-id="e4fdb-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="e4fdb-104">下面介绍 OneDrive 和 SharePoint 服务在多地理位置环境中的工作方式。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="e4fdb-105">OneDrive 管理员体验</span><span class="sxs-lookup"><span data-stu-id="e4fdb-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="e4fdb-p101">[OneDrive 管理中心](https://admin.onedrive.com)的左侧导航栏中有一个“地理位置”**** 选项卡，其中包含地理位置地图，你可在其中查看和管理地理位置。使用此页面可添加或删除租户的地理位置。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="e4fdb-108">分类</span><span class="sxs-lookup"><span data-stu-id="e4fdb-108">Taxonomy</span></span>

<span data-ttu-id="e4fdb-p102">对于跨多地理位置的企业托管元数据，我们支持统一[分类](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)，同时将主数据托管在公司的中心位置。建议从中心位置管理全局分类，并只在附属地理位置的分类中添加特定于位置的术语。全局分类术语将同步到附属地理位置。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="e4fdb-112">共享</span><span class="sxs-lookup"><span data-stu-id="e4fdb-112">Sharing</span></span>

<span data-ttu-id="e4fdb-p103">管理员可以为他们的每个位置设置共享策略并对其进行管理。每个地理位置的 OneDrive 网站只会接受相应地理位置特定的共享设置。（例如，可以将[外部共享](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)用于中心位置，但不可用于附属位置，反之亦然。）请注意，共享设置不允许配置地理位置之间的共享限制。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. (For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo-locations.</span></span>

<span data-ttu-id="e4fdb-p104">对于 OneDrive 多地理位置，必须在每个地理位置管理你的共享设置，因为这些设置在租户之间不同步。要管理共享，请访问 [OneDrive 管理中心共享设置](https://admin.onedrive.com/?v=SharingSettings)页。默认情况下，每个附属位置中的任何人都可以使用外部共享。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-p104">For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant. To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="e4fdb-119">用户配置文件应用程序</span><span class="sxs-lookup"><span data-stu-id="e4fdb-119">User Profile Application</span></span>

<span data-ttu-id="e4fdb-p105">每个地理位置都有一个[用户配置文件应用程序](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)。每个用户的配置文件信息都托管在其地理位置中，并可供该地理位置的管理员使用。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="e4fdb-p106">如果你有自定义配置文件属性，建议跨地区使用同一配置文件架构并在所有地理位置或所需的位置填充自定义配置文件属性。有关如何以编程方式填充用户配置文件数据的指导，请参阅[批量用户配置文件更新 API](https://docs.microsoft.com/zh-CN/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span><span class="sxs-lookup"><span data-stu-id="e4fdb-p106">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed. For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/zh-CN/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="e4fdb-124">BCS、安全存储、应用</span><span class="sxs-lookup"><span data-stu-id="e4fdb-124">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="e4fdb-125">BCS、安全存储和应用都具有单独的地理位置实例，因此，SharePoint Online 管理员应从希望在其中显示服务的每个地理位置实例中管理和配置这些服务。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-125">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="e4fdb-126">安全与合规管理中心</span><span class="sxs-lookup"><span data-stu-id="e4fdb-126">Security and Compliance Admin Center</span></span>

<span data-ttu-id="e4fdb-127">还有一个多地理位置租户的中央合规中心：[Office 365 安全与合规中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-127">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="e4fdb-128">信息保护 (IP) 数据丢失防护 (DLP) 策略</span><span class="sxs-lookup"><span data-stu-id="e4fdb-128">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="e4fdb-p107">可以在安全与合规中心为 OneDrive for Business 设置 IP DLP 策略，根据需要将策略范围设置为整个租户或适用用户。例如，如果希望选择适用于附属位置中 OneDrive 用户的策略，请选择将策略应用到特定 OneDrive 并输入用户的 OneDrive URL。有关创建 DLP 策略的常规指导，请参阅[数据丢失防护策略概述](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-p107">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="e4fdb-132">DLP 策略将基于每个地理位置的适用性自动同步。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-132">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="e4fdb-133">在 UI 中，无法为地理位置中的所有用户实施信息保护和数据丢失防护策略，你必须为策略选择适用的 OneDrive 帐户，或将策略全局应用于所有 OneDrive 帐户。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-133">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="e4fdb-134">电子数据展示</span><span class="sxs-lookup"><span data-stu-id="e4fdb-134">eDiscovery</span></span> 

<span data-ttu-id="e4fdb-p108">默认情况下，多地理位置租户的电子数据展示管理者或管理员只能在该租户所在的中心位置实施电子数据展示。若要支持在附属位置实施电子数据展示，可通过 PowerShell 获取一个名为“Region”的新合规性安全筛选器参数。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-p108">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="e4fdb-137">Office 365 全局管理员必须分配电子数据展示管理者权限，以允许其他人员执行电子数据展示，并在其适用的合规性安全筛选器中分配“Region”参数，以便将要进行电子数据展示的区域指定为附属位置，否则，不会对该附属位置执行任何电子数据展示。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-137">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="e4fdb-p109">当为特定地理位置设置电子数据展示管理者或管理员角色时，电子数据展示管理者或管理员将只能对位于该地理区域的 SharePoint 网站和 OneDrive 网站执行电子数据展示搜索操作。如果电子数据展示管理者或管理员尝试搜索指定区域以外的 SharePoint 或 OneDrive 网站，将不返回任何结果。此外，当某个区域的电子数据展示管理者或管理员触发导出时，数据将导出到该地区的 Azure 实例。通过禁止跨受控界限导出内容，将有助于组织保持合规性。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-p109">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="e4fdb-142">如果需要电子数据展示管理者搜索多个 SharePoint 区域，将需要为电子数据展示管理者创建另一个用户帐户，以指定 OneDrive 或 SharePoint 网站所在的备用区域。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-142">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e4fdb-143"><strong>支持多地理位置的地理位置</strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-143"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="e4fdb-144"><strong>SharePoint 导出数据的电子数据展示将会在此 Azure Blob 数据位置中...</strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-144"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e4fdb-145"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-145"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="e4fdb-146">东南亚或东亚数据中心</span><span class="sxs-lookup"><span data-stu-id="e4fdb-146">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e4fdb-147"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-147"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="e4fdb-148">东南亚或东亚数据中心</span><span class="sxs-lookup"><span data-stu-id="e4fdb-148">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e4fdb-149"><strong>CAN</strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-149"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="e4fdb-150">美国数据中心</span><span class="sxs-lookup"><span data-stu-id="e4fdb-150">US datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e4fdb-151"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-151"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="e4fdb-152">欧洲数据中心</span><span class="sxs-lookup"><span data-stu-id="e4fdb-152">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e4fdb-153"><strong>FRA</strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-153"><strong>FRA</strong></span></span></td>
<td align="left"><span data-ttu-id="e4fdb-154">欧洲数据中心</span><span class="sxs-lookup"><span data-stu-id="e4fdb-154">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e4fdb-155"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-155"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="e4fdb-156">欧洲数据中心</span><span class="sxs-lookup"><span data-stu-id="e4fdb-156">Europe datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e4fdb-157"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-157"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="e4fdb-158">东南亚或东亚数据中心</span><span class="sxs-lookup"><span data-stu-id="e4fdb-158">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e4fdb-159"><strong>JPN </strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-159"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="e4fdb-160">东南亚或东亚数据中心</span><span class="sxs-lookup"><span data-stu-id="e4fdb-160">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e4fdb-161"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="e4fdb-161"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="e4fdb-162">美国数据中心</span><span class="sxs-lookup"><span data-stu-id="e4fdb-162">US datacenters</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="e4fdb-163">针对区域设置合规性安全筛选器：</span><span class="sxs-lookup"><span data-stu-id="e4fdb-163">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="e4fdb-164">打开 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4fdb-164">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="e4fdb-165">输入</span><span class="sxs-lookup"><span data-stu-id="e4fdb-165">Enter</span></span>  
    <span data-ttu-id="e4fdb-166">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="e4fdb-166">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="e4fdb-167">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="e4fdb-167">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="e4fdb-168">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="e4fdb-168">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="e4fdb-169">例如：**New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="e4fdb-169">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="e4fdb-170">请参阅 [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) 一文了解其他参数和语法</span><span class="sxs-lookup"><span data-stu-id="e4fdb-170">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="e4fdb-171">审核日志搜索</span><span class="sxs-lookup"><span data-stu-id="e4fdb-171">Audit log search</span></span>

<span data-ttu-id="e4fdb-p110">所有地理位置的统一[审核日志](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)均可从 Office 365 审核日志搜索页找到。你可以查看跨地理位置的所有审核日志条目，例如，NAM 和 EUR 地理位置用户的活动将显示在一个组织视图中，然后你可以应用现有筛选器，查看特定用户的活动。</span><span class="sxs-lookup"><span data-stu-id="e4fdb-p110">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
