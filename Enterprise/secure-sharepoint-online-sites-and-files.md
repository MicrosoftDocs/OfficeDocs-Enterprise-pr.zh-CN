---
title: 保护 SharePoint Online 网站和文件
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: 摘要：用于保护 SharePoint Online 和 Office 365 中文件的配置建议。
ms.openlocfilehash: 5ee7ce0f5d52076ec27a3478a39b998a96e0e270
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915077"
---
# <a name="secure-sharepoint-online-sites-and-files"></a><span data-ttu-id="0a52c-103">保护 SharePoint Online 网站和文件</span><span class="sxs-lookup"><span data-stu-id="0a52c-103">Secure SharePoint Online sites and files</span></span>

 <span data-ttu-id="0a52c-104">**摘要：** 用于保护 SharePoint Online 和 Office 365 中的文件的配置建议。</span><span class="sxs-lookup"><span data-stu-id="0a52c-104">**Summary:** Configuration recommendations for protecting files in SharePoint Online and Office 365.</span></span>
  
<span data-ttu-id="0a52c-p101">本文就如何配置 SharePoint Online 团队网站并在平衡安全性与易于协作的同时如何进行文件保护方面提供了相关建议。本文定义了四个不同的配置，首先是具有最开放共享策略的组织内的公共网站。每个额外配置均表示一个有意义的保护设置，但对资源的访问和协作被限定为一组相关用户。以这些建议为出发点，并调整配置以满足组织的需要。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p101">This article provides recommendations for configuring SharePoint Online team sites and file protection that balances security with ease of collaboration. This article defines four different configurations, starting with a public site within your organization with the most open sharing policies. Each additional configuration represents a meaningful step up in protection, but the ability to access and collaborate on resources is reduced to the relevant set of users. Use these recommendations as a starting point and adjust the configurations to meet the needs of your organization.</span></span> 
  
<span data-ttu-id="0a52c-109">本文中的配置符合 Microsoft 针对数据、标识和设备的三层保护的建议：</span><span class="sxs-lookup"><span data-stu-id="0a52c-109">The configurations in this article align with Microsoft's recommendations for three tiers of protection for data, identities, and devices:</span></span>
  
- <span data-ttu-id="0a52c-110">基线保护</span><span class="sxs-lookup"><span data-stu-id="0a52c-110">Baseline protection</span></span>
    
- <span data-ttu-id="0a52c-111">敏感保护</span><span class="sxs-lookup"><span data-stu-id="0a52c-111">Sensitive protection</span></span>
    
- <span data-ttu-id="0a52c-112">高度机密保护</span><span class="sxs-lookup"><span data-stu-id="0a52c-112">Highly confidential protection</span></span>
    
<span data-ttu-id="0a52c-113">有关这些保护层以及针对每层建议的功能的详细信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="0a52c-113">For more information about these tiers and capabilities recommended for each tier, see the following resources.</span></span> 
  
- [<span data-ttu-id="0a52c-114">Office 365 的标识和设备保护</span><span class="sxs-lookup"><span data-stu-id="0a52c-114">Identity and Device Protection for Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [<span data-ttu-id="0a52c-115">Office 365 中的文件保护解决方案</span><span class="sxs-lookup"><span data-stu-id="0a52c-115">File Protection Solutions in Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a><span data-ttu-id="0a52c-116">功能概述</span><span class="sxs-lookup"><span data-stu-id="0a52c-116">Capability overview</span></span>

<span data-ttu-id="0a52c-p102">针对各种 Office 365 功能的 SharePoint Online 团队网站绘制的建议。 对于高度机密的网站，建议使用 Azure 信息保护。 这包括在企业移动性 + 安全性 (EMS) 中。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p102">Recommendations for SharePoint Online team sites draw on a variety of Office 365 capabilities. For highly confidential sites, Azure Information Protection is recommended. This is included in Enterprise Mobility + Security (EMS).</span></span> 
  
<span data-ttu-id="0a52c-120">下图显示了针对四个 SharePoint Online 团队网站的建议配置。</span><span class="sxs-lookup"><span data-stu-id="0a52c-120">The following illustration shows the recommended configurations for four SharePoint Online team sites.</span></span>

![适用于 SharePoint 网站的推荐配置](Media/SharePoint-site-configuration-v2.png)

<span data-ttu-id="0a52c-122">如图所示：</span><span class="sxs-lookup"><span data-stu-id="0a52c-122">As illustrated:</span></span>
  
- <span data-ttu-id="0a52c-p103">基线保护包含针对 SharePoint Online 团队网站的两个选项 - 公共网站和专用网站。 组织中的任何人均可发现和访问公共网站。 只有网站成员可以发现和访问专用网站。 这两个网站配置均允许组外共享。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p103">Baseline protection includes two options for SharePoint Online team sites — a public site and private site. Public sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the site. Both of these site configurations allow for sharing outside the group.</span></span> 
    
- <span data-ttu-id="0a52c-127">敏感保护和高度机密的保护的网站是专用网站，只有特定组的成员才具有相关访问权限。</span><span class="sxs-lookup"><span data-stu-id="0a52c-127">Sites for sensitive and highly confidential protection are private sites with access limited only to members of specific groups.</span></span>
    
- <span data-ttu-id="0a52c-p104">Office 365 标签提供根据所需保护级别对数据进行分类的方法。 每个 SharePoint Online 团队网站均被配置为使用网站的默认标签自动标记文档库中的文件。 与四个网站配置相对应，此示例中的标签分别为内部公开、专用、敏感和高度机密。 用户可以更改标签，但此配置可确保所有文件均接收默认的标签。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p104">Office 365 labels provide a way to classify data with a needed protection level. Each of the SharePoint Online team sites are configured to automatically label files in document libraries with a default label for the site. Corresponding to the four site configurations, the labels in this example are Internal Public, Private, Sensitive, and Highly Confidential. Users can change the labels, but this configuration ensures all files receive a default label.</span></span>
    
- <span data-ttu-id="0a52c-132">为敏感和高度机密 Office 365 标签配置数据丢失防护 (DLP)，在其试图向组织外部发送这些类型的文件时警告或阻止用户。</span><span class="sxs-lookup"><span data-stu-id="0a52c-132">Data loss prevention (DLP) policies are configured for the Sensitive and Highly Confidential Office 365 labels to either warn or prevent users when they attempt to send these types of files outside the organization.</span></span>
    
- <span data-ttu-id="0a52c-p105">如果方案需要，可以使用 Azure 信息保护来加密高度机密文件，并授予对此类文件的相应权限。不建议用于所有客户。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p105">If needed for your scenario, you can use Azure Information Protection to encrypt and grants permissions to files that are highly confidential. This is not recommended for all customers.</span></span>
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a><span data-ttu-id="0a52c-135">SharePoint Online 和 OneDrive for Business 的租户范围内设置</span><span class="sxs-lookup"><span data-stu-id="0a52c-135">Tenant-wide settings for SharePoint Online and OneDrive for Business</span></span>

<span data-ttu-id="0a52c-p106">SharePoint Online 和 OneDrive for Business 包括影响所有网站和用户的租户范围内设置。 其中一些设置也可在网站级别进行调整，使其更具有（而不是更不具有）限制性。 本部分讨论影响安全性和协作的租户范围内设置。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p106">SharePoint Online and OneDrive for Business include tenant-wide settings that affect all sites and users. Some of these settings can also be adjusted at the site level to be more restrictive (but not less). This section discusses tenant-wide settings that affect security and collaboration.</span></span> 
  
### <a name="sharing"></a><span data-ttu-id="0a52c-139">共享</span><span class="sxs-lookup"><span data-stu-id="0a52c-139">Sharing</span></span>

<span data-ttu-id="0a52c-140">对于此解决方案，建议使用以下租户范围内设置：</span><span class="sxs-lookup"><span data-stu-id="0a52c-140">For this solution, we recommend the following tenant-wide settings:</span></span>
  
- <span data-ttu-id="0a52c-141">保留允许所有与所有帐户类型共享（包括匿名共享）的默认共享策略。</span><span class="sxs-lookup"><span data-stu-id="0a52c-141">Keep the default sharing policy that allows all sharing with all account types, including anonymous sharing.</span></span>
    
- <span data-ttu-id="0a52c-142">如果需要，请将匿名链接设置为过期。</span><span class="sxs-lookup"><span data-stu-id="0a52c-142">Set anonymous links to expire, if desired.</span></span>
    
- <span data-ttu-id="0a52c-p107">将共享的默认链接类型更改为“内部”。 这有助于防止数据意外泄露到组织外部。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p107">Change the default link type for sharing to Internal. This helps prevent accidental data leakage outside your organization.</span></span>
    
<span data-ttu-id="0a52c-p108">虽然允许外部共享可能看起来有悖常理，但相较于通过电子邮件发送文件，此方法可更好地控制文件共享。 SharePoint Online 和 Outlook 彼此协作，提供安全的文件协作。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p108">While it might seem counterintuitive to allow external sharing, this approach provides more control over file sharing compared to sending files in email. SharePoint Online and Outlook work together to provide secure collaboration on files.</span></span> 
  
- <span data-ttu-id="0a52c-147">默认情况下，Outlook 共享文件链接，而不是通过电子邮件发送文件。</span><span class="sxs-lookup"><span data-stu-id="0a52c-147">By default, Outlook shares a link to a file instead of sending the file in email.</span></span> 
    
- <span data-ttu-id="0a52c-148">SharePoint Online 和 OneDrive for Business 可轻松实现与组织内外部的参与者共享文件链接</span><span class="sxs-lookup"><span data-stu-id="0a52c-148">SharePoint Online and OneDrive for Business make it easy to share links to files with contributors who are both inside and outside your organization</span></span>
    
<span data-ttu-id="0a52c-p109">用户还可进行控制，帮助管理外部共享。 例如，你能够：</span><span class="sxs-lookup"><span data-stu-id="0a52c-p109">You also have controls to help govern external sharing. For example, you can:</span></span>
  
- <span data-ttu-id="0a52c-151">禁用匿名来宾链接。</span><span class="sxs-lookup"><span data-stu-id="0a52c-151">Disable an anonymous guest link.</span></span>
    
- <span data-ttu-id="0a52c-152">撤销用户对网站的访问权限。</span><span class="sxs-lookup"><span data-stu-id="0a52c-152">Revoke user access to a site.</span></span>
    
- <span data-ttu-id="0a52c-153">查看谁有权访问特定网站或文档。</span><span class="sxs-lookup"><span data-stu-id="0a52c-153">See who has access to a specific site or document.</span></span>
    
- <span data-ttu-id="0a52c-154">将匿名共享链接设置为过期（租户设置）。</span><span class="sxs-lookup"><span data-stu-id="0a52c-154">Set anonymous sharing links to expire (tenant setting).</span></span>
    
- <span data-ttu-id="0a52c-155">限制可与之共享的组织外部用户（租户设置）。</span><span class="sxs-lookup"><span data-stu-id="0a52c-155">Limit who can share outside your organization (tenant setting).</span></span>
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a><span data-ttu-id="0a52c-156">配合使用外部共享与数据丢失预防 (DLP)</span><span class="sxs-lookup"><span data-stu-id="0a52c-156">Use external sharing together with data loss prevention (DLP)</span></span>

<span data-ttu-id="0a52c-p110">如果不允许外部共享，则有业务需求的用户需要寻找备用工具和方法。Microsoft 建议结合使用外部共享和 DLP 策略来保护敏感和高度机密的文件。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p110">If you don't allow external sharing, users with a business need will find alternate tools and methods. Microsoft recommends you combine external sharing with DLP policies to protect sensitive and highly confidential files.</span></span>
  
### <a name="device-access-settings"></a><span data-ttu-id="0a52c-159">设备访问设置</span><span class="sxs-lookup"><span data-stu-id="0a52c-159">Device access settings</span></span>

<span data-ttu-id="0a52c-p111">SharePoint Online 和 OneDrive for Business 的设备访问设置可确定是否已将访问权限限制为仅限浏览器（不能下载文件）或访问被阻止。这些设置当前处于首次发布状态，仅应用于租户范围。即将推出在网站级别配置设备访问策略的功能。对于此解决方案，建议不要使用应用于租户范围的设备访问设置。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p111">Device access settings for SharePoint Online and OneDrive for Business let you determine whether access is limited to browser only (files can't be downloaded) or if access is blocked. These settings are currently in First Release and apply tenant-wide. Coming soon is the ability to configure device access policies at the site level. For this solution, we recommend not using device access settings that apply tenant-wide.</span></span>
  
<span data-ttu-id="0a52c-164">要使用处于首次发布状态的设备访问设置，请参阅：[在 Office 365 中设置标准发布或首次发布选项](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)。</span><span class="sxs-lookup"><span data-stu-id="0a52c-164">To use device access settings while these are in first release: [Set up the Standard or First Release Options in Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).</span></span>
  
### <a name="onedrive-for-business"></a><span data-ttu-id="0a52c-165">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="0a52c-165">OneDrive for Business</span></span>

<span data-ttu-id="0a52c-p112">访问这些设置，确定是否要更改 OneDrive for Business 网站的默认设置。目前，共享和设备访问设置与 SharePoint Online 管理中心重复，并适用于这两个环境。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p112">Visit these settings to decide if you want to change the default settings for OneDrive for Business sites. Currently, the sharing and device access settings are duplicated from the SharePoint Online admin center and apply to both environments.</span></span>
  
## <a name="sharepoint-team-site-configuration"></a><span data-ttu-id="0a52c-168">SharePoint 团队网站配置</span><span class="sxs-lookup"><span data-stu-id="0a52c-168">SharePoint team site configuration</span></span>

<span data-ttu-id="0a52c-p113">下表总结了本文前面所述的每个团队网站的配置。使用这些配置作为起点建议并调整网站类型和配置，以满足组织的需求。不是每个组织都需要每种类型的网站。只有少许组织需要高度机密的保护。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p113">The following table summarizes the configuration for each of the team sites described earlier in this article. Use these configurations as starting point recommendations and adjust the site types and configurations to meet the needs of your organization. Not every organization needs every type of site. Only a small number of organizations require highly confidential protection.</span></span>
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||<span data-ttu-id="0a52c-173">**基线保护 #1**</span><span class="sxs-lookup"><span data-stu-id="0a52c-173">**Baseline protection #1**</span></span> <br/> |<span data-ttu-id="0a52c-174">**基线保护 #2**</span><span class="sxs-lookup"><span data-stu-id="0a52c-174">**Baseline protection #2**</span></span> <br/> |<span data-ttu-id="0a52c-175">**敏感保护**</span><span class="sxs-lookup"><span data-stu-id="0a52c-175">**Sensitive protection**</span></span> <br/> |<span data-ttu-id="0a52c-176">**高度机密**</span><span class="sxs-lookup"><span data-stu-id="0a52c-176">**Highly confidential**</span></span> <br/> |
|<span data-ttu-id="0a52c-177">描述</span><span class="sxs-lookup"><span data-stu-id="0a52c-177">Description</span></span>  <br/> |<span data-ttu-id="0a52c-178">组织内的开放式发现和协作。</span><span class="sxs-lookup"><span data-stu-id="0a52c-178">Open discovery and collaboration within the organization.</span></span>  <br/> |<span data-ttu-id="0a52c-179">允许在组外部共享的专用网站和组。</span><span class="sxs-lookup"><span data-stu-id="0a52c-179">Private site and group with sharing allowed outside the group.</span></span>  <br/> |<span data-ttu-id="0a52c-p114">独立网站，该网站中的访问级别由特定组中的成员身份进行定义。仅允许网站成员进行共享。DLP 在用户试图向组织外发送文件时警告用户。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p114">Isolated site, in which levels of access are defined by membership in specific groups. Sharing is only allowed to members of the site. DLP warns users when attempting to send files outside the organization.</span></span>  <br/> |<span data-ttu-id="0a52c-p115">启用 Azure 信息保护的独立网站和文件及权限。DLP 阻止用户向组织外发送文件。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p115">Isolated site + file encryption and permissions with Azure Information Protection. DLP prevents users from sending files outside the organization.</span></span>  <br/> |
|<span data-ttu-id="0a52c-185">专用或公用团队网站</span><span class="sxs-lookup"><span data-stu-id="0a52c-185">Private or public team site</span></span>  <br/> |<span data-ttu-id="0a52c-186">公用</span><span class="sxs-lookup"><span data-stu-id="0a52c-186">Public</span></span>  <br/> |<span data-ttu-id="0a52c-187">Private</span><span class="sxs-lookup"><span data-stu-id="0a52c-187">Private</span></span>  <br/> |<span data-ttu-id="0a52c-188">Private</span><span class="sxs-lookup"><span data-stu-id="0a52c-188">Private</span></span>  <br/> |<span data-ttu-id="0a52c-189">Private</span><span class="sxs-lookup"><span data-stu-id="0a52c-189">Private</span></span>  <br/> |
|<span data-ttu-id="0a52c-190">谁可以访问？</span><span class="sxs-lookup"><span data-stu-id="0a52c-190">Who has access?</span></span>  <br/> |<span data-ttu-id="0a52c-191">组织中的任何人，包括 B2B 用户和来宾用户。</span><span class="sxs-lookup"><span data-stu-id="0a52c-191">Everybody in the organization, including B2B users and guest users.</span></span>  <br/> |<span data-ttu-id="0a52c-p116">仅限网站成员。其他人可以请求访问。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p116">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="0a52c-p117">仅限网站成员。其他人可以请求访问。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p117">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="0a52c-p118">仅限成员。其他人无法请求访问。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p118">Members only. Others cannot request access.</span></span>  <br/> |
|<span data-ttu-id="0a52c-198">网站级共享控制</span><span class="sxs-lookup"><span data-stu-id="0a52c-198">Site-level sharing controls</span></span>  <br/> |<span data-ttu-id="0a52c-p119">允许与任何人共享。默认设置。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p119">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="0a52c-p120">允许与任何人共享。默认设置。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p120">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="0a52c-203">成员无法共享对网站的访问权限。</span><span class="sxs-lookup"><span data-stu-id="0a52c-203">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="0a52c-204">非成员可以请求访问该网站，但需要由网站管理员对这些请求进行寻址。</span><span class="sxs-lookup"><span data-stu-id="0a52c-204">Non-members can request access to the site, but these requests need to be addressed by a site administrator.</span></span>  <br/> |<span data-ttu-id="0a52c-205">成员无法共享对网站的访问权限。</span><span class="sxs-lookup"><span data-stu-id="0a52c-205">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="0a52c-206">非成员无法请求访问网站或内容。</span><span class="sxs-lookup"><span data-stu-id="0a52c-206">Non-members cannot request access to the site or contents.</span></span>  <br/> |
|<span data-ttu-id="0a52c-207">网站级别的设备访问控制</span><span class="sxs-lookup"><span data-stu-id="0a52c-207">Site-level device access controls</span></span>  <br/> |<span data-ttu-id="0a52c-208">无任何额外控制。</span><span class="sxs-lookup"><span data-stu-id="0a52c-208">No additional controls.</span></span>  <br/> |<span data-ttu-id="0a52c-209">无任何额外控制。</span><span class="sxs-lookup"><span data-stu-id="0a52c-209">No additional controls.</span></span>  <br/> |<span data-ttu-id="0a52c-p121">即将推出网站级别控制，可防止用户将文件下载到不符合或未加入域的设备。使所有其他设备仅限浏览器访问。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p121">Site-level controls are coming soon, which prevents users from downloading files to non-compliant or non-domain joined devices. This allows browser-only access from all other devices.</span></span>  <br/> |<span data-ttu-id="0a52c-212">即将推出网站级别控制，可阻止将文件下载到不符合或未加入域的设备。</span><span class="sxs-lookup"><span data-stu-id="0a52c-212">Site-level controls are coming soon, which blocks downloading of files to non-compliant or non-domain joined devices.</span></span>  <br/> |
|<span data-ttu-id="0a52c-213">Office 365 标签</span><span class="sxs-lookup"><span data-stu-id="0a52c-213">Office 365 labels</span></span>  <br/> |<span data-ttu-id="0a52c-214">内部公用</span><span class="sxs-lookup"><span data-stu-id="0a52c-214">Internal Public</span></span>  <br/> |<span data-ttu-id="0a52c-215">Private</span><span class="sxs-lookup"><span data-stu-id="0a52c-215">Private</span></span>  <br/> |<span data-ttu-id="0a52c-216">敏感</span><span class="sxs-lookup"><span data-stu-id="0a52c-216">Sensitive</span></span>  <br/> |<span data-ttu-id="0a52c-217">高度机密</span><span class="sxs-lookup"><span data-stu-id="0a52c-217">Highly Confidential</span></span>  <br/> |
|<span data-ttu-id="0a52c-218">DLP 策略</span><span class="sxs-lookup"><span data-stu-id="0a52c-218">DLP policies</span></span>  <br/> |||<span data-ttu-id="0a52c-219">在用户向组织外发送标记为“敏感”的文件时进行警告。</span><span class="sxs-lookup"><span data-stu-id="0a52c-219">Warn users when sending files that are labeled as Sensitive outside the organization.</span></span>  <br/> <span data-ttu-id="0a52c-220">要阻止外部共享敏感数据类型，如信用卡号或其他个人数据，可以针对这些数据类型（包括所配置的自定义数据类型）配置其他 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="0a52c-220">To block external sharing of sensitive data types, such as credit card numbers or other personal data, you can configure additional DLP policies for these data types (including custom data types you configure).</span></span>  <br/> |<span data-ttu-id="0a52c-p122">阻止用户向组织外发送标记为“高度机密”的文件。允许用户通过提供他们与之共享的对象等理由来替代此行为。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p122">Block users from sending files that are labeled as highly confidential outside organization. Allow users to override this by providing justification, including who they are sharing the file with.</span></span>  <br/> |
|<span data-ttu-id="0a52c-223">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="0a52c-223">Azure Information Protection</span></span>  <br/> ||||<span data-ttu-id="0a52c-p123">使用 Azure 信息保护可自动加密和授予对文件的权限。这种保护与文件一起传输以防内容泄露。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p123">Use Azure Information Protection to automatically encrypt and grant permissions to files. This protection travels with the files in case they are leaked.</span></span>  <br/> <span data-ttu-id="0a52c-p124">Office 365 无法读取使用 Azure 信息保护加密的文件。此外，DLP 策略只能与元数据（包括标签）一起使用，但并不能处理这些文件的内容（如文件内的信用卡号）。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p124">Office 365 cannot read files encrypted with Azure Information Protection. Additionally, DLP policies can only work with the metadata (including labels) but not the contents of these files (such as credit card numbers within files).</span></span>  <br/> |
   
<span data-ttu-id="0a52c-p125">有关在此解决方案中部署四种不同类型的 SharePoint Online 团队网站的步骤，请参阅[部署 SharePoint Online 网站以获得三层保护](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)。有关创建开发/测试环境的步骤，请参阅[在开发/测试环境中保护 SharePoint Online 网站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p125">For the steps to deploy the four different types of SharePoint Online team sites in this solution, see [Deploy SharePoint Online sites for three tiers of protection](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). For the steps to create a dev/test environment, see [Secure SharePoint Online sites in a dev/test environment](secure-sharepoint-online-sites-in-a-dev-test-environment.md).</span></span> 
  
## <a name="office-365-classification-and-labels"></a><span data-ttu-id="0a52c-230">Office 365 分类和标签</span><span class="sxs-lookup"><span data-stu-id="0a52c-230">Office 365 classification and labels</span></span>

<span data-ttu-id="0a52c-p126">建议对含敏感数据的环境使用 Office 365 标签。配置并发布 Office 365 标签后：</span><span class="sxs-lookup"><span data-stu-id="0a52c-p126">Using Office 365 labels is recommended for environments with sensitive data. After you configure and publish Office 365 labels:</span></span>
  
- <span data-ttu-id="0a52c-233">可以将默认标签应用于 SharePoint Online 团队网站中的文档库，以便该库中的所有文档都能获取默认标签。</span><span class="sxs-lookup"><span data-stu-id="0a52c-233">You can apply a default label to a document library in a SharePoint Online team site, so that all documents in that library get the default label.</span></span> 
    
- <span data-ttu-id="0a52c-234">只要标签与特定条件匹配，就可以将其自动应用到内容。</span><span class="sxs-lookup"><span data-stu-id="0a52c-234">You can apply labels to content automatically if it matches specific conditions.</span></span>
    
- <span data-ttu-id="0a52c-235">可以应用基于 Office 365 标签的 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="0a52c-235">You can apply DLP policies that are based on Office 365 labels.</span></span>
    
- <span data-ttu-id="0a52c-p127">组织中的用户可手动将标签应用于 Outlook 网页版、Outlook 2010 及更高版本、OneDrive for Business、SharePoint Online 以及 Office 365 组。用户通常都很了解他们处理的内容类型，以便可以对其进行分类并应用相应的 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p127">People in your organization can apply a label manually to content in Outlook on the web, Outlook 2010 and later, OneDrive for Business, SharePoint Online, and Office 365 groups. Users often know best what type of content they're working with, so they can classify it and have the appropriate DLP policy applied.</span></span>
    
![适用于 SharePoint 网站的推荐配置](media/7fed0126-ab4a-4480-922c-681970642339.png)
  
<span data-ttu-id="0a52c-239">如图所示，此解决方案包括创建以下标签：</span><span class="sxs-lookup"><span data-stu-id="0a52c-239">As illustrated, this solution includes creating the following labels:</span></span>
  
- <span data-ttu-id="0a52c-240">高度机密</span><span class="sxs-lookup"><span data-stu-id="0a52c-240">Highly Confidential</span></span>
    
- <span data-ttu-id="0a52c-241">敏感</span><span class="sxs-lookup"><span data-stu-id="0a52c-241">Sensitive</span></span>
    
- <span data-ttu-id="0a52c-242">Private</span><span class="sxs-lookup"><span data-stu-id="0a52c-242">Private</span></span>
    
- <span data-ttu-id="0a52c-243">内部公用</span><span class="sxs-lookup"><span data-stu-id="0a52c-243">Internal Public</span></span>
    
<span data-ttu-id="0a52c-p128">这些标签均映射到本文前述插图和图表中建议的网站。本解决方案建议配置 DLP 策略，以帮助防止泄露标记为“敏感”和“高度机密”的文件。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p128">These labels are mapped to the recommended sites in the illustrations and charts earlier in this article. This solution recommends configuring DLP policies to help prevent the leakage of files labeled as Sensitive and Highly Confidential.</span></span>
  
<span data-ttu-id="0a52c-246">有关如何配置此解决方案中的 Office 365 标签和 DLP 策略的步骤，请参阅[使用 Office 365 标签和 DLP 保护 SharePoint Online 文件](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)。</span><span class="sxs-lookup"><span data-stu-id="0a52c-246">For the steps to configure Office 365 labels and DLP policies in this solution, see [Protect SharePoint Online files with Office 365 labels and DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).</span></span>
  
## <a name="azure-information-protection"></a><span data-ttu-id="0a52c-247">Azure 信息保护</span><span class="sxs-lookup"><span data-stu-id="0a52c-247">Azure Information Protection</span></span>

<span data-ttu-id="0a52c-p129">如果安全方案需要，可以使用 Azure 信息保护来应用与文件一直如影随形的标签和保护。Azure 信息保护标签与 Office 365 标签不同。对于此解决方案，建议使用范围内 Azure 信息保护策略和“高度机密”标签的子标签，加密需要最高级安全保护的文件，并授予对此类文件的相应权限。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p129">If warranted for your security scenario, you can use Azure Information Protection to apply labels and protections that follow the files wherever they go. Azure Information Protection labels are different than Office 365 labels. For this solution, we recommend you use a scoped Azure Information Protection policy and a sub-label of the Highly Confidential label to encrypt and grant permissions to files that need to be protected with the highest level of security.</span></span> 
  
<span data-ttu-id="0a52c-p130">请注意，将 Azure 信息保护加密应用于 Office 365 中存储的文件时，该服务无法处理这些文件的内容。共同创作、电子数据展示、搜索、Delve 和其他协作功能将无法正常使用。 DLP 策略只适用于元数据（包括 Office 365 标签），但并不适用于这些文件的内容（如文件内的信用卡号）。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p130">Be aware that when Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. DLP policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
  
![Azure 信息保护在 Azure 中进行配置，标签显示在客户端工具栏中](media/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
<span data-ttu-id="0a52c-255">如图所示：</span><span class="sxs-lookup"><span data-stu-id="0a52c-255">As illustrated:</span></span>
  
- <span data-ttu-id="0a52c-p131">在 Microsoft Azure 门户中，配置 Azure 信息保护策略和标签。建议配置作用域内 Azure 信息保护策略的子标签。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p131">You configure Azure Information Protection policies and labels in the Microsoft Azure portal. Configuring a sub-label of a scoped Azure Information Protection policy is recommended.</span></span>
    
- <span data-ttu-id="0a52c-258">Azure 信息保护标签在 Office 应用程序中以“信息保护”**** 栏的形式显示。</span><span class="sxs-lookup"><span data-stu-id="0a52c-258">Azure Information Protection labels show up as an **Information protection** bar in Office applications.</span></span>
    
### <a name="adding-permissions-for-external-users"></a><span data-ttu-id="0a52c-259">添加外部用户的权限</span><span class="sxs-lookup"><span data-stu-id="0a52c-259">Adding permissions for external users</span></span>

<span data-ttu-id="0a52c-p132">可通过两种方式授予使用 Azure 信息保护进行保护的文件外部用户访问权限。在这两种情况下，外部用户均须具有 Azure AD 帐户。如果外部用户不是使用 Azure AD 的组织的成员，他们可以通过使用此注册页面以个人身份获得 Azure AD 帐户：[https://aka.ms/aip-signup](https://aka.ms/aip-signup)。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p132">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>
  
- <span data-ttu-id="0a52c-263">将外部用户添加到用于配置标签保护的 Azure AD 组</span><span class="sxs-lookup"><span data-stu-id="0a52c-263">Add external users to an Azure AD group that is used to configure protection for a label</span></span>
    
     <span data-ttu-id="0a52c-p133">你需要先将该帐户作为 B2B 用户添加到目录中。[通过 Azure 权限管理缓存组成员资格](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)可能需要几个小时的时间。使用此方法，可将权限授予使用标签保护的所有现有文件（甚至在将用户添加到 Azure AD 组之前受保护的文件）。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p133">You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group membership caching by Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>
    
- <span data-ttu-id="0a52c-267">将外部用户直接添加到标签保护</span><span class="sxs-lookup"><span data-stu-id="0a52c-267">Add external users directly to the label protection</span></span>
    
     <span data-ttu-id="0a52c-p134">你可以添加组织（例如 Fabrikam.com）、Azure AD 组（如组织内的财务组）中的所有用户或单个用户。例如，可以将监管机构的外部团队添加到标签保护中。使用此方法，可仅向在外部实体添加到保护后使用标签进行保护的文件授予权限。</span><span class="sxs-lookup"><span data-stu-id="0a52c-p134">You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>
    
### <a name="deploying-and-using-azure-information-protection"></a><span data-ttu-id="0a52c-271">部署并使用 Azure 信息保护</span><span class="sxs-lookup"><span data-stu-id="0a52c-271">Deploying and using Azure Information Protection</span></span>

<span data-ttu-id="0a52c-272">有关配置此解决方案中的 Azure 信息保护的步骤，请参阅[使用 Azure 信息保护来保护 SharePoint Online 文件](protect-sharepoint-online-files-with-azure-information-protection.md)。</span><span class="sxs-lookup"><span data-stu-id="0a52c-272">For the steps to configure Azure Information Protection in this solution, see [Protect SharePoint Online files with Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0a52c-273">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a52c-273">See Also</span></span>

[<span data-ttu-id="0a52c-274">Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南</span><span class="sxs-lookup"><span data-stu-id="0a52c-274">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="0a52c-275">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="0a52c-275">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="0a52c-276">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="0a52c-276">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="0a52c-277">在开发/测试环境中保护 SharePoint Online 网站</span><span class="sxs-lookup"><span data-stu-id="0a52c-277">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



