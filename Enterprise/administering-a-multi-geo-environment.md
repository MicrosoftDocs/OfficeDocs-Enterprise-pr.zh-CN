---
title: 管理多个地理环境
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解有关管理 SharePoint 和 OneDrive 多地理环境中的服务。
ms.openlocfilehash: 5d423fedc25b6e58ee84a51b01eb3858e6f198bb
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="d8917-103">管理多个地理环境</span><span class="sxs-lookup"><span data-stu-id="d8917-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="d8917-104">下面我们来看 OneDrive 和 SharePoint 服务多地理环境中的工作方式。</span><span class="sxs-lookup"><span data-stu-id="d8917-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="d8917-105">OneDrive 管理员体验</span><span class="sxs-lookup"><span data-stu-id="d8917-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="d8917-p101">[OneDrive 管理中心](https://admin.onedrive.com)有**地理位置**选项卡在左边的导航功能地理位置映射，您可以查看和管理您的地理位置。使用此页面可添加或删除您组织的地理位置。</span><span class="sxs-lookup"><span data-stu-id="d8917-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="d8917-108">分类</span><span class="sxs-lookup"><span data-stu-id="d8917-108">Taxonomy</span></span>

<span data-ttu-id="d8917-p102">我们支持统一的[分类](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)企业托管元数据跨地理位置与主所驻留在您的公司的集中位置。我们建议您从中心位置管理您的全局分类，并仅将特定位置术语添加到卫星地理位置分类。全局分类条款将同步到附属的地理位置。</span><span class="sxs-lookup"><span data-stu-id="d8917-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="d8917-112">共享</span><span class="sxs-lookup"><span data-stu-id="d8917-112">Sharing</span></span>

<span data-ttu-id="d8917-p103">管理员可以设置并管理其位置的每个共享策略。在每个地理位置的 OneDrive 网站将履行只相应地区特定共享设置。例如，您可以允许[外部共享](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)有关您的中心位置，而不是您的附属位置，反之亦然。对于 OneDrive 多的地区，因为这些都不会同步跨租户必须管理共享设置在每个地理位置。</span><span class="sxs-lookup"><span data-stu-id="d8917-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa. For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant.</span></span>

<span data-ttu-id="d8917-p104">若要管理共享访问[共享设置的 OneDrive 管理中心](https://admin.onedrive.com/?v=SharingSettings)页。默认情况下与任何人在每个卫星位置启用外部共享。</span><span class="sxs-lookup"><span data-stu-id="d8917-p104">To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="d8917-119">用户配置文件应用程序</span><span class="sxs-lookup"><span data-stu-id="d8917-119">User Profile Application</span></span>

<span data-ttu-id="d8917-p105">每个地理位置处于一个[用户配置文件应用程序](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)。在它们的地理位置和地理位置的管理员可以承载每个用户的配置文件信息。</span><span class="sxs-lookup"><span data-stu-id="d8917-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="d8917-122">如果您有自定义配置文件属性，那么建议您跨地区使用相同的配置文件架构并填充您的自定义配置文件属性可在所有地理位置或者在需要的地方。</span><span class="sxs-lookup"><span data-stu-id="d8917-122">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="d8917-123">BCS，安全的存储应用程序</span><span class="sxs-lookup"><span data-stu-id="d8917-123">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="d8917-124">BCS、 安全存储和应用程序所有具有独立的地理实例，因此 SharePoint Online 管理员应管理和配置这些服务与它们希望这些存在每个 geo 实例。</span><span class="sxs-lookup"><span data-stu-id="d8917-124">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="d8917-125">安全性和法规遵从性管理中心</span><span class="sxs-lookup"><span data-stu-id="d8917-125">Security and Compliance Admin Center</span></span>

<span data-ttu-id="d8917-126">没有一个中央法规遵从性中心多地区租户： [Office 365 安全和法规遵从性中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)。</span><span class="sxs-lookup"><span data-stu-id="d8917-126">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="d8917-127">信息 (IP) 的保护数据丢失防护 (DLP) 策略</span><span class="sxs-lookup"><span data-stu-id="d8917-127">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="d8917-p106">您可以设置 IP DLP 策略业务的 OneDrive 在安全性和法规遵从性中心，根据需要为整个组织或适用的用户范围的策略。例如： 如果您想要为用户选择策略 OneDrive 卫星位置，选择该选项可以将该策略应用于特定的 OneDrive，输入用户的 OneDrive url。[数据丢失防护策略概述](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)在创建 DLP 策略的一般指南，请参见</span><span class="sxs-lookup"><span data-stu-id="d8917-p106">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="d8917-131">DLP 策略将自动同步根据每个地理位置对其适用性。</span><span class="sxs-lookup"><span data-stu-id="d8917-131">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="d8917-132">在地理位置实现对所有用户的信息保护和数据丢失防护策略不在用户界面中可用的选项，而必须选择策略适用的 OneDrive 帐户或全局将策略应用到所有的 OneDrive 帐户。</span><span class="sxs-lookup"><span data-stu-id="d8917-132">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="d8917-133">电子数据展示</span><span class="sxs-lookup"><span data-stu-id="d8917-133">eDiscovery</span></span> 

<span data-ttu-id="d8917-p107">默认情况下，电子数据展示的经理或管理员的多个地区组织将能够执行 eDiscovery 仅在该组织的中心位置。为支持开展卫星位置的 eDiscovery 的能力，一个新的法规遵从性安全筛选器参数，称为"区域"可通过 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d8917-p107">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="d8917-136">Office 365 全局管理员必须将分配 eDiscovery 经理权限以允许其他用户执行 eDiscovery 和分配其适用的法规遵从性安全筛选来指定执行 eDiscovery 作为附属的区域中的"区域"参数位置，否则为没有 eDiscovery 执行的附属位置。</span><span class="sxs-lookup"><span data-stu-id="d8917-136">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="d8917-p108">当 eDiscovery 的经理或管理员角色设置为特定地理位置时，eDiscovery 的经理或管理员仅能执行 eDiscovery 搜索操作的 SharePoint 网站和地理位置的 OneDrive 站点。如果 eDiscovery 经理或管理员尝试搜索指定区域之外的 OneDrive 站点，则将不返回任何结果。此外，当区域经理或管理员 eDiscovery 触发一个导出，该地区的 Azure 实例导出数据。这可以帮助企业保持法规遵从性，从而不受控制的界限要导出的内容。</span><span class="sxs-lookup"><span data-stu-id="d8917-p108">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="d8917-141">如果有必要为 eDiscovery 经理在 SharePoint 中的多个区域进行搜索，需要为 eDiscovery 指定 OneDrive 或 SharePoint 网站的位置的备用区域服务控制管理器创建另一个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d8917-141">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d8917-142"><strong>多地区支持地理位置</strong></span><span class="sxs-lookup"><span data-stu-id="d8917-142"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="d8917-143"><strong>eDiscovery SharePoint 导出的数据将处于此 Azure Blob 数据的位置...</strong></span><span class="sxs-lookup"><span data-stu-id="d8917-143"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d8917-144"><strong>名称</strong></span><span class="sxs-lookup"><span data-stu-id="d8917-144"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="d8917-145">美国数据中心</span><span class="sxs-lookup"><span data-stu-id="d8917-145">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8917-146"><strong>欧元</strong></span><span class="sxs-lookup"><span data-stu-id="d8917-146"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="d8917-147">欧洲数据中心</span><span class="sxs-lookup"><span data-stu-id="d8917-147">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d8917-148"><strong>APC 公司</strong></span><span class="sxs-lookup"><span data-stu-id="d8917-148"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="d8917-149">东南方向或东亚太地区数据中心</span><span class="sxs-lookup"><span data-stu-id="d8917-149">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8917-150"><strong>可以</strong></span><span class="sxs-lookup"><span data-stu-id="d8917-150"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="d8917-151">美国数据中心</span><span class="sxs-lookup"><span data-stu-id="d8917-151">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d8917-152"><strong>澳大利亚</strong></span><span class="sxs-lookup"><span data-stu-id="d8917-152"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="d8917-153">东南方向或东亚太地区数据中心</span><span class="sxs-lookup"><span data-stu-id="d8917-153">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8917-154"><strong>韩文</strong></span><span class="sxs-lookup"><span data-stu-id="d8917-154"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="d8917-155">租户的默认数据位置</span><span class="sxs-lookup"><span data-stu-id="d8917-155">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d8917-156"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="d8917-156"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="d8917-157">欧洲数据中心</span><span class="sxs-lookup"><span data-stu-id="d8917-157">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8917-158"><strong>日文</strong></span><span class="sxs-lookup"><span data-stu-id="d8917-158"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="d8917-159">东南方向或东亚太地区数据中心</span><span class="sxs-lookup"><span data-stu-id="d8917-159">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="d8917-160">要为区域设置遵从安全筛选器：</span><span class="sxs-lookup"><span data-stu-id="d8917-160">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="d8917-161">打开 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8917-161">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="d8917-162">输入</span><span class="sxs-lookup"><span data-stu-id="d8917-162">Enter</span></span>  
    <span data-ttu-id="d8917-163">$s = New PSSession 配置名 Microsoft.Exchange-ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -$cred 凭据-基本身份验证 AllowRedirection-SessionOption (New PSSessionOption SkipCACheck-SkipCNCheck-SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="d8917-163">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="d8917-164">$ = 导入 PSSession $s AllowClobber</span><span class="sxs-lookup"><span data-stu-id="d8917-164">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="d8917-165">**新 ComplianceSecurityFilter****-操作**所有**-FilterName** EnterTheNameYouWantToAssign **-地区**EnterTheRegionParameter **-用户**EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="d8917-165">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="d8917-166">例如：**新 ComplianceSecurityFilter-操作**所有**-FilterName** NAMEDISCOVERYMANAGERS **-地区**名称**-用户**adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="d8917-166">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="d8917-167">请参阅附加的参数和语法的[新 ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx)文章</span><span class="sxs-lookup"><span data-stu-id="d8917-167">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="d8917-168">审核日志搜索</span><span class="sxs-lookup"><span data-stu-id="d8917-168">Audit log search</span></span>

<span data-ttu-id="d8917-p109">Office 365 审核日志搜索页面提供了统一[审核日志](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)的所有您的地理位置。您可以看到中的所有审核日志项跨 geo、 例如，名称和欧元地区用户的活动中将会显示一个组织视图，然后可以应用现有的筛选器以都查看特定用户的活动。</span><span class="sxs-lookup"><span data-stu-id="d8917-p109">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
