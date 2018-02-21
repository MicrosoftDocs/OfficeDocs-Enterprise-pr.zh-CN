---
title: "保护 SharePoint Online 网站和文件"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "摘要： 为保护 SharePoint Online Office 365 中的文件的配置建议。"
ms.openlocfilehash: 035c3e69a430269b382ab032387a44cc3cbbbfd6
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a><span data-ttu-id="36bb3-103">保护 SharePoint Online 网站和文件</span><span class="sxs-lookup"><span data-stu-id="36bb3-103">Secure SharePoint Online sites and files</span></span>

 <span data-ttu-id="36bb3-104">**摘要：**为保护 SharePoint Online Office 365 中的文件的配置建议。</span><span class="sxs-lookup"><span data-stu-id="36bb3-104">**Summary:** Configuration recommendations for protecting files in SharePoint Online and Office 365.</span></span>
  
<span data-ttu-id="36bb3-p101">本文提供了有关配置 SharePoint Online 的工作组站点和平衡安全而且易于协作的文件保护的建议。本文定义了四种不同配置，最开放的共享策略与组织内的公用网站开始。每个其他配置表示一个有意义的步骤组成的保护，但能够访问和协作资源减少到相关集的用户。这些建议作为起点并调整配置以满足您组织的需要。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p101">This article provides recommendations for configuring SharePoint Online team sites and file protection that balances security with ease of collaboration. This article defines four different configurations, starting with a public site within your organization with the most open sharing policies. Each additional configuration represents a meaningful step up in protection, but the ability to access and collaborate on resources is reduced to the relevant set of users. Use these recommendations as a starting point and adjust the configurations to meet the needs of your organization.</span></span> 
  
<span data-ttu-id="36bb3-109">本文中的配置符合 Microsoft 针对数据、标识和设备的三层保护的建议：</span><span class="sxs-lookup"><span data-stu-id="36bb3-109">The configurations in this article align with Microsoft's recommendations for three tiers of protection for data, identities, and devices:</span></span>
  
- <span data-ttu-id="36bb3-110">基线保护</span><span class="sxs-lookup"><span data-stu-id="36bb3-110">Baseline protection</span></span>
    
- <span data-ttu-id="36bb3-111">敏感保护</span><span class="sxs-lookup"><span data-stu-id="36bb3-111">Sensitive protection</span></span>
    
- <span data-ttu-id="36bb3-112">高度机密保护</span><span class="sxs-lookup"><span data-stu-id="36bb3-112">Highly confidential protection</span></span>
    
<span data-ttu-id="36bb3-113">有关这些保护层以及针对每层建议的功能的详细信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="36bb3-113">For more information about these tiers and capabilities recommended for each tier, see the following resources.</span></span> 
  
- [<span data-ttu-id="36bb3-114">Office 365 的标识和设备保护</span><span class="sxs-lookup"><span data-stu-id="36bb3-114">Identity and Device Protection for Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [<span data-ttu-id="36bb3-115">Office 365 中的文件保护解决方案</span><span class="sxs-lookup"><span data-stu-id="36bb3-115">File Protection Solutions in Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a><span data-ttu-id="36bb3-116">功能概述</span><span class="sxs-lookup"><span data-stu-id="36bb3-116">Capability overview</span></span>

<span data-ttu-id="36bb3-p102">针对各种 Office 365 功能的 SharePoint Online 团队网站绘制的建议。 对于高度机密的网站，建议使用 Azure 信息保护。 这包括在企业移动性 + 安全性 (EMS) 中。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p102">Recommendations for SharePoint Online team sites draw on a variety of Office 365 capabilities. For highly confidential sites, Azure Information Protection is recommended. This is included in Enterprise Mobility + Security (EMS).</span></span> 
  
<span data-ttu-id="36bb3-120">下图显示了四个 SharePoint Online 的团队站点的建议的配置。</span><span class="sxs-lookup"><span data-stu-id="36bb3-120">The following illustration shows the recommended configurations for four SharePoint Online team sites.</span></span>
  
![适用于 SharePoint 网站的推荐配置](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
<span data-ttu-id="36bb3-122">如图所示：</span><span class="sxs-lookup"><span data-stu-id="36bb3-122">As illustrated:</span></span>
  
- <span data-ttu-id="36bb3-p103">基线保护包含针对 SharePoint Online 团队网站的两个选项 - 公共网站和专用网站。 组织中的任何人均可发现和访问公共网站。 只有网站成员可以发现和访问专用网站。 这两个网站配置均允许组外共享。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p103">Baseline protection includes two options for SharePoint Online team sites — a public site and private site. Public sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the site. Both of these site configurations allow for sharing outside the group.</span></span> 
    
- <span data-ttu-id="36bb3-127">敏感保护和高度机密的保护的网站是专用网站，只有特定组的成员才具有相关访问权限。</span><span class="sxs-lookup"><span data-stu-id="36bb3-127">Sites for sensitive and highly confidential protection are private sites with access limited only to members of specific groups.</span></span>
    
- <span data-ttu-id="36bb3-p104">Office 365 标签提供根据所需保护级别对数据进行分类的方法。 每个 SharePoint Online 团队网站均被配置为使用网站的默认标签自动标记文档库中的文件。 与四个网站配置相对应，此示例中的标签分别为内部公开、专用、敏感和高度机密。 用户可以更改标签，但此配置可确保所有文件均接收默认的标签。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p104">Office 365 labels provide a way to classify data with a needed protection level. Each of the SharePoint Online team sites are configured to automatically label files in document libraries with a default label for the site. Corresponding to the four site configurations, the labels in this example are Internal Public, Private, Sensitive, and Highly Confidential. Users can change the labels, but this configuration ensures all files receive a default label.</span></span>
    
- <span data-ttu-id="36bb3-132">为敏感和高度机密 Office 365 标签配置数据丢失防护 (DLP)，在其试图向组织外部发送这些类型的文件时警告或阻止用户。</span><span class="sxs-lookup"><span data-stu-id="36bb3-132">Data loss prevention (DLP) policies are configured for the Sensitive and Highly Confidential Office 365 labels to either warn or prevent users when they attempt to send these types of files outside the organization.</span></span>
    
- <span data-ttu-id="36bb3-133">对于配置有高度机密保护的网站，Azure 信息保护将对文件进行加密，并授予相应权限。</span><span class="sxs-lookup"><span data-stu-id="36bb3-133">For sites configured with highly confidential protection, Azure Information Protection encrypts and grants permissions for files.</span></span>
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a><span data-ttu-id="36bb3-134">SharePoint Online 和 OneDrive for Business 的租户范围内设置</span><span class="sxs-lookup"><span data-stu-id="36bb3-134">Tenant-wide settings for SharePoint Online and OneDrive for Business</span></span>

<span data-ttu-id="36bb3-p105">SharePoint Online 和 OneDrive for Business 包括影响所有网站和用户的租户范围内设置。 其中一些设置也可在网站级别进行调整，使其更具有（而不是更不具有）限制性。 本部分讨论影响安全性和协作的租户范围内设置。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p105">SharePoint Online and OneDrive for Business include tenant-wide settings that affect all sites and users. Some of these settings can also be adjusted at the site level to be more restrictive (but not less). This section discusses tenant-wide settings that affect security and collaboration.</span></span> 
  
### <a name="sharing"></a><span data-ttu-id="36bb3-138">共享</span><span class="sxs-lookup"><span data-stu-id="36bb3-138">Sharing</span></span>

<span data-ttu-id="36bb3-139">对于此解决方案，建议使用以下租户范围内设置：</span><span class="sxs-lookup"><span data-stu-id="36bb3-139">For this solution, we recommend the following tenant-wide settings:</span></span>
  
- <span data-ttu-id="36bb3-140">保留允许所有与所有帐户类型共享（包括匿名共享）的默认共享策略。</span><span class="sxs-lookup"><span data-stu-id="36bb3-140">Keep the default sharing policy that allows all sharing with all account types, including anonymous sharing.</span></span>
    
- <span data-ttu-id="36bb3-141">如果需要，请将匿名链接设置为过期。</span><span class="sxs-lookup"><span data-stu-id="36bb3-141">Set anonymous links to expire, if desired.</span></span>
    
- <span data-ttu-id="36bb3-p106">将共享的默认链接类型更改为“内部”。 这有助于防止数据意外泄露到组织外部。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p106">Change the default link type for sharing to Internal. This helps prevent accidental data leakage outside your organization.</span></span>
    
<span data-ttu-id="36bb3-p107">虽然允许外部共享可能看起来有悖常理，但相较于通过电子邮件发送文件，此方法可更好地控制文件共享。 SharePoint Online 和 Outlook 彼此协作，提供安全的文件协作。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p107">While it might seem counterintuitive to allow external sharing, this approach provides more control over file sharing compared to sending files in email. SharePoint Online and Outlook work together to provide secure collaboration on files.</span></span> 
  
- <span data-ttu-id="36bb3-146">默认情况下，Outlook 共享文件链接，而不是通过电子邮件发送文件。</span><span class="sxs-lookup"><span data-stu-id="36bb3-146">By default, Outlook shares a link to a file instead of sending the file in email.</span></span> 
    
- <span data-ttu-id="36bb3-147">SharePoint Online 和业务的 OneDrive 可以轻松与正在组织内外的参与者共享文件的链接</span><span class="sxs-lookup"><span data-stu-id="36bb3-147">SharePoint Online and OneDrive for Business make it easy to share links to files with contributors who are both inside and outside your organization</span></span>
    
<span data-ttu-id="36bb3-p108">用户还可进行控制，帮助管理外部共享。 例如，你能够：</span><span class="sxs-lookup"><span data-stu-id="36bb3-p108">You also have controls to help govern external sharing. For example, you can:</span></span>
  
- <span data-ttu-id="36bb3-150">禁用匿名来宾链接。</span><span class="sxs-lookup"><span data-stu-id="36bb3-150">Disable an anonymous guest link.</span></span>
    
- <span data-ttu-id="36bb3-151">撤销用户对网站的访问权限。</span><span class="sxs-lookup"><span data-stu-id="36bb3-151">Revoke user access to a site.</span></span>
    
- <span data-ttu-id="36bb3-152">查看谁有权访问特定网站或文档。</span><span class="sxs-lookup"><span data-stu-id="36bb3-152">See who has access to a specific site or document.</span></span>
    
- <span data-ttu-id="36bb3-153">将匿名共享链接设置为过期（租户设置）。</span><span class="sxs-lookup"><span data-stu-id="36bb3-153">Set anonymous sharing links to expire (tenant setting).</span></span>
    
- <span data-ttu-id="36bb3-154">限制可与之共享的组织外部用户（租户设置）。</span><span class="sxs-lookup"><span data-stu-id="36bb3-154">Limit who can share outside your organization (tenant setting).</span></span>
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a><span data-ttu-id="36bb3-155">配合使用外部共享与数据丢失预防 (DLP)</span><span class="sxs-lookup"><span data-stu-id="36bb3-155">Use external sharing together with data loss prevention (DLP)</span></span>

<span data-ttu-id="36bb3-p109">如果您不允许外部共享时，与业务用户需要了解备用工具和方法。Microsoft 建议您将合并外部共享与 DLP 策略来保护敏感和高度机密文件。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p109">If you don't allow external sharing, users with a business need will find alternate tools and methods. Microsoft recommends you combine external sharing with DLP policies to protect sensitive and highly confidential files.</span></span>
  
### <a name="device-access-settings"></a><span data-ttu-id="36bb3-158">设备访问设置</span><span class="sxs-lookup"><span data-stu-id="36bb3-158">Device access settings</span></span>

<span data-ttu-id="36bb3-p110">SharePoint Online 和 OneDrive 的业务设备访问设置使您可以确定是否限制为仅限于浏览器访问 （不能下载文件），或访问被阻止。这些设置目前在第一版，并且应用租户范围。即将是在站点级别配置设备访问策略的能力。对于本解决方案，建议不使用应用组织范围内的设备访问设置。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p110">Device access settings for SharePoint Online and OneDrive for Business let you determine whether access is limited to browser only (files can't be downloaded) or if access is blocked. These settings are currently in First Release and apply tenant-wide. Coming soon is the ability to configure device access policies at the site level. For this solution, we recommend not using device access settings that apply tenant-wide.</span></span>
  
<span data-ttu-id="36bb3-163">要使用处于首次发布状态的设备访问设置，请参阅：[在 Office 365 中设置标准发布或首次发布选项](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)。</span><span class="sxs-lookup"><span data-stu-id="36bb3-163">To use device access settings while these are in first release: [Set up the Standard or First Release Options in Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).</span></span>
  
### <a name="onedrive-for-business"></a><span data-ttu-id="36bb3-164">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="36bb3-164">OneDrive for Business</span></span>

<span data-ttu-id="36bb3-p111">访问这些设置，确定是否要更改 OneDrive for Business 网站的默认设置。 目前，共享和设备访问设置与 SharePoint Online 管理中心重复，并适用于这两个环境。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p111">Visit these settings to decide if you want to change the default settings for OneDrive for Business sites. Currently, the sharing and device access settings are duplicated from the SharePoint Online admin center and apply to both environments.</span></span>
  
## <a name="sharepoint-team-site-configuration"></a><span data-ttu-id="36bb3-167">SharePoint 团队网站配置</span><span class="sxs-lookup"><span data-stu-id="36bb3-167">SharePoint team site configuration</span></span>

<span data-ttu-id="36bb3-p112">下表总结了本文前面所述的每个团队网站的配置。 使用这些配置作为起点建议并调整网站类型和配置，以满足组织的需求。 不是每个组织都需要每种类型的网站。 只有少许组织需要高度机密的保护。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p112">The following table summarizes the configuration for each of the team sites described earlier in this article. Use these configurations as starting point recommendations and adjust the site types and configurations to meet the needs of your organization. Not every organization needs every type of site. Only a small number of organizations require highly confidential protection.</span></span>
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||<span data-ttu-id="36bb3-172">**基线保护 #1**</span><span class="sxs-lookup"><span data-stu-id="36bb3-172">**Baseline protection #1**</span></span> <br/> |<span data-ttu-id="36bb3-173">**基线保护 #2**</span><span class="sxs-lookup"><span data-stu-id="36bb3-173">**Baseline protection #2**</span></span> <br/> |<span data-ttu-id="36bb3-174">**敏感保护**</span><span class="sxs-lookup"><span data-stu-id="36bb3-174">**Sensitive protection**</span></span> <br/> |<span data-ttu-id="36bb3-175">**高度机密**</span><span class="sxs-lookup"><span data-stu-id="36bb3-175">**Highly confidential**</span></span> <br/> |
|<span data-ttu-id="36bb3-176">描述</span><span class="sxs-lookup"><span data-stu-id="36bb3-176">Description</span></span>  <br/> |<span data-ttu-id="36bb3-177">组织内的开放式发现和协作。</span><span class="sxs-lookup"><span data-stu-id="36bb3-177">Open discovery and collaboration within the organization.</span></span>  <br/> |<span data-ttu-id="36bb3-178">允许在组外部共享的专用网站和组。</span><span class="sxs-lookup"><span data-stu-id="36bb3-178">Private site and group with sharing allowed outside the group.</span></span>  <br/> |<span data-ttu-id="36bb3-p113">独立网站，该网站中的访问级别由特定组中的成员身份进行定义。 仅允许网站成员进行共享。 DLP 在用户试图向组织外发送文件时警告用户。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p113">Isolated site, in which levels of access are defined by membership in specific groups. Sharing is only allowed to members of the site. DLP warns users when attempting to send files outside the organization.</span></span>  <br/> |<span data-ttu-id="36bb3-p114">启用 Azure 信息保护的独立网站和文件及权限。 DLP 阻止用户向组织外发送文件。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p114">Isolated site + file encryption and permissions with Azure Information Protection. DLP prevents users from sending files outside the organization.</span></span>  <br/> |
|<span data-ttu-id="36bb3-184">专用或公用团队网站</span><span class="sxs-lookup"><span data-stu-id="36bb3-184">Private or public team site</span></span>  <br/> |<span data-ttu-id="36bb3-185">公用</span><span class="sxs-lookup"><span data-stu-id="36bb3-185">Public</span></span>  <br/> |<span data-ttu-id="36bb3-186">Private</span><span class="sxs-lookup"><span data-stu-id="36bb3-186">Private</span></span>  <br/> |<span data-ttu-id="36bb3-187">Private</span><span class="sxs-lookup"><span data-stu-id="36bb3-187">Private</span></span>  <br/> |<span data-ttu-id="36bb3-188">Private</span><span class="sxs-lookup"><span data-stu-id="36bb3-188">Private</span></span>  <br/> |
|<span data-ttu-id="36bb3-189">谁可以访问？</span><span class="sxs-lookup"><span data-stu-id="36bb3-189">Who has access?</span></span>  <br/> |<span data-ttu-id="36bb3-190">组织中的任何人，包括 B2B 用户和来宾用户。</span><span class="sxs-lookup"><span data-stu-id="36bb3-190">Everybody in the organization, including B2B users and guest users.</span></span>  <br/> |<span data-ttu-id="36bb3-p115">仅限网站成员。 其他人可以请求访问。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p115">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="36bb3-p116">仅限网站成员。 其他人可以请求访问。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p116">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="36bb3-p117">仅限成员。 其他人无法请求访问。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p117">Members only. Others cannot request access.</span></span>  <br/> |
|<span data-ttu-id="36bb3-197">网站级共享控制</span><span class="sxs-lookup"><span data-stu-id="36bb3-197">Site-level sharing controls</span></span>  <br/> |<span data-ttu-id="36bb3-p118">允许与任何人共享。 默认设置。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p118">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="36bb3-p119">允许与任何人共享。 默认设置。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p119">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="36bb3-202">成员无法共享对网站的访问权限。</span><span class="sxs-lookup"><span data-stu-id="36bb3-202">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="36bb3-203">非成员可以请求访问该网站，但需要由网站管理员对这些请求进行寻址。</span><span class="sxs-lookup"><span data-stu-id="36bb3-203">Non-members can request access to the site, but these requests need to be addressed by a site administrator.</span></span>  <br/> |<span data-ttu-id="36bb3-204">成员无法共享对网站的访问权限。</span><span class="sxs-lookup"><span data-stu-id="36bb3-204">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="36bb3-205">非成员无法请求访问网站或内容。</span><span class="sxs-lookup"><span data-stu-id="36bb3-205">Non-members cannot request access to the site or contents.</span></span>  <br/> |
|<span data-ttu-id="36bb3-206">网站级别的设备访问控制</span><span class="sxs-lookup"><span data-stu-id="36bb3-206">Site-level device access controls</span></span>  <br/> |<span data-ttu-id="36bb3-207">无任何额外控制。</span><span class="sxs-lookup"><span data-stu-id="36bb3-207">No additional controls.</span></span>  <br/> |<span data-ttu-id="36bb3-208">无任何额外控制。</span><span class="sxs-lookup"><span data-stu-id="36bb3-208">No additional controls.</span></span>  <br/> |<span data-ttu-id="36bb3-p120">即将推出网站级别控制，可防止用户将文件下载到不符合或未加入域的设备。 使所有其他设备仅限浏览器访问。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p120">Site-level controls are coming soon, which prevents users from downloading files to non-compliant or non-domain joined devices. This allows browser-only access from all other devices.</span></span>  <br/> |<span data-ttu-id="36bb3-211">即将推出网站级别控制，可阻止将文件下载到不符合或未加入域的设备。</span><span class="sxs-lookup"><span data-stu-id="36bb3-211">Site-level controls are coming soon, which blocks downloading of files to non-compliant or non-domain joined devices.</span></span>  <br/> |
|<span data-ttu-id="36bb3-212">Office 365 标签</span><span class="sxs-lookup"><span data-stu-id="36bb3-212">Office 365 labels</span></span>  <br/> |<span data-ttu-id="36bb3-213">内部公用</span><span class="sxs-lookup"><span data-stu-id="36bb3-213">Internal Public</span></span>  <br/> |<span data-ttu-id="36bb3-214">Private</span><span class="sxs-lookup"><span data-stu-id="36bb3-214">Private</span></span>  <br/> |<span data-ttu-id="36bb3-215">敏感</span><span class="sxs-lookup"><span data-stu-id="36bb3-215">Sensitive</span></span>  <br/> |<span data-ttu-id="36bb3-216">高度机密</span><span class="sxs-lookup"><span data-stu-id="36bb3-216">Highly Confidential</span></span>  <br/> |
|<span data-ttu-id="36bb3-217">DLP 策略</span><span class="sxs-lookup"><span data-stu-id="36bb3-217">DLP policies</span></span>  <br/> |||<span data-ttu-id="36bb3-218">在用户向组织外发送标记为“敏感”的文件时进行警告。</span><span class="sxs-lookup"><span data-stu-id="36bb3-218">Warn users when sending files that are labeled as Sensitive outside the organization.</span></span>  <br/> <span data-ttu-id="36bb3-219">要阻止外部共享敏感数据类型，如信用卡号或其他个人数据，可以针对这些数据类型（包括所配置的自定义数据类型）配置其他 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="36bb3-219">To block external sharing of sensitive data types, such as credit card numbers or other personal data, you can configure additional DLP policies for these data types (including custom data types you configure).</span></span>  <br/> |<span data-ttu-id="36bb3-p121">阻止用户向组织外发送标记为“高度机密”的文件。 允许用户通过提供他们与之共享的对象等理由来替代此行为。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p121">Block users from sending files that are labeled as highly confidential outside organization. Allow users to override this by providing justification, including who they are sharing the file with.</span></span>  <br/> |
|<span data-ttu-id="36bb3-222">Azure 信息保护</span><span class="sxs-lookup"><span data-stu-id="36bb3-222">Azure Information Protection</span></span>  <br/> ||||<span data-ttu-id="36bb3-p122">使用 Azure 信息保护自动加密并授予其权限的文件。它们泄漏的情况下，这种保护传输的文件。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p122">Use Azure Information Protection to automatically encrypt and grant permissions to files. This protection travels with the files in case they are leaked.</span></span>  <br/> <span data-ttu-id="36bb3-p123">Office 365 无法读取使用 Azure 信息保护加密的文件。此外，DLP 策略只能处理的元数据 （包括标签），但不是包括这些文件 （例如，信用卡号文件内） 的内容。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p123">Office 365 cannot read files encrypted with Azure Information Protection. Additionally, DLP policies can only work with the metadata (including labels) but not the contents of these files (such as credit card numbers within files).</span></span>  <br/> |
   
<span data-ttu-id="36bb3-p124">若要部署此解决方案中的 SharePoint Online 小组站点的四种不同类型的步骤，请参阅[部署 SharePoint Online 网站的三个层次的保护](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)。创建开发/测试环境的步骤，请参阅[安全 SharePoint Online 网站的开发/测试环境](secure-sharepoint-online-sites-in-a-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p124">For the steps to deploy the four different types of SharePoint Online team sites in this solution, see [Deploy SharePoint Online sites for three tiers of protection](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). For the steps to create a dev/test environment, see [Secure SharePoint Online sites in a dev/test environment](secure-sharepoint-online-sites-in-a-dev-test-environment.md).</span></span> 
  
## <a name="office-365-classification-and-labels"></a><span data-ttu-id="36bb3-229">Office 365 分类和标签</span><span class="sxs-lookup"><span data-stu-id="36bb3-229">Office 365 classification and labels</span></span>

<span data-ttu-id="36bb3-p125">环境中的敏感数据，建议使用 Office 365 标签。在您配置和发布 Office 365 标签：</span><span class="sxs-lookup"><span data-stu-id="36bb3-p125">Using Office 365 labels is recommended for environments with sensitive data. After you configure and publish Office 365 labels:</span></span>
  
- <span data-ttu-id="36bb3-232">可以应用于在线 SharePoint 的工作组网站中的文档库的默认标签以便该库中的所有文档的默认标签。</span><span class="sxs-lookup"><span data-stu-id="36bb3-232">You can apply a default label to a document library in a SharePoint Online team site, so that all documents in that library get the default label.</span></span> 
    
- <span data-ttu-id="36bb3-233">您可以将标签应用于内容自动匹配特定条件。</span><span class="sxs-lookup"><span data-stu-id="36bb3-233">You can apply labels to content automatically if it matches specific conditions.</span></span>
    
- <span data-ttu-id="36bb3-234">您可以应用基于 Office 365 提供标签的 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="36bb3-234">You can apply DLP policies that are based on Office 365 labels.</span></span>
    
- <span data-ttu-id="36bb3-p126">您组织中的人员可以应用标签手动内容在 web 上的 Outlook 中 2010年及更高版本的 Outlook，OneDrive 业务、 SharePoint Online 和 Office 365 的组。用户通常非常清楚地知道什么类型的内容他们正在使用，因此可以对其进行分类和应用适当的 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p126">People in your organization can apply a label manually to content in Outlook on the web, Outlook 2010 and later, OneDrive for Business, SharePoint Online, and Office 365 groups. Users often know best what type of content they're working with, so they can classify it and have the appropriate DLP policy applied.</span></span>
    
![适用于 SharePoint 网站的推荐配置](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
<span data-ttu-id="36bb3-238">如图所示，此解决方案包括创建以下标签：</span><span class="sxs-lookup"><span data-stu-id="36bb3-238">As illustrated, this solution includes creating the following labels:</span></span>
  
- <span data-ttu-id="36bb3-239">高度机密</span><span class="sxs-lookup"><span data-stu-id="36bb3-239">Highly Confidential</span></span>
    
- <span data-ttu-id="36bb3-240">敏感</span><span class="sxs-lookup"><span data-stu-id="36bb3-240">Sensitive</span></span>
    
- <span data-ttu-id="36bb3-241">Private</span><span class="sxs-lookup"><span data-stu-id="36bb3-241">Private</span></span>
    
- <span data-ttu-id="36bb3-242">内部公用</span><span class="sxs-lookup"><span data-stu-id="36bb3-242">Internal Public</span></span>
    
<span data-ttu-id="36bb3-p127">这些标签映射到图中的推荐的网站和本文中前面的图表。本解决方案建议配置 DLP 策略有助于防止文件标记为敏感和高度机密的泄露。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p127">These labels are mapped to the recommended sites in the illustrations and charts earlier in this article. This solution recommends configuring DLP policies to help prevent the leakage of files labeled as Sensitive and Highly Confidential.</span></span>
  
<span data-ttu-id="36bb3-245">有关如何配置此解决方案中的 Office 365 标签和 DLP 策略的步骤，请参阅[使用 Office 365 标签和 DLP 保护 SharePoint Online 文件](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)。</span><span class="sxs-lookup"><span data-stu-id="36bb3-245">For the steps to configure Office 365 labels and DLP policies in this solution, see [Protect SharePoint Online files with Office 365 labels and DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).</span></span>
  
## <a name="azure-information-protection"></a><span data-ttu-id="36bb3-246">Azure 信息保护</span><span class="sxs-lookup"><span data-stu-id="36bb3-246">Azure Information Protection</span></span>

<span data-ttu-id="36bb3-p128">使用 Azure 信息保护应用标签和与文件如影随形的保护。 对于此解决方案，建议使用作用域内 Azure 信息保护策略和“高度机密”标签的子标签来加密需要最高级别安全性保护的文件并授予相应权限。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p128">Use Azure Information Protection to apply labels and protections that follow the files wherever they go. For this solution, we recommend you use a scoped Azure Information Protection policy and a sub-label of the Highly Confidential label to encrypt and grant permissions to files that need to be protected with the highest level of security.</span></span> 
  
<span data-ttu-id="36bb3-p129">请注意，将 Azure 信息保护加密应用于 Office 365 中存储的文件时，该服务无法处理这些文件的内容。 共同创作、电子数据展示、搜索、Delve 和其他协作功能将无法正常使用。 DLP 策略只适用于元数据（包括 Office 365 标签），但并不适用于这些文件的内容（如文件内的信用卡号）。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p129">Be aware that when Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. DLP policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
  
![Azure 信息保护是在 Azure 中进行配置，标签显示在客户端工具栏中](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
<span data-ttu-id="36bb3-253">如图所示：</span><span class="sxs-lookup"><span data-stu-id="36bb3-253">As illustrated:</span></span>
  
- <span data-ttu-id="36bb3-p130">在 Microsoft Azure 门户配置了 Azure 的信息保护策略和标签。建议配置的指定了作用域的 Azure 的信息保护策略的子标签。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p130">You configure Azure Information Protection policies and labels in the Microsoft Azure portal. Configuring a sub-label of a scoped Azure Information Protection policy is recommended.</span></span>
    
- <span data-ttu-id="36bb3-256">Azure 的信息保护标签显示了作为 Office 应用程序中的**信息保护**栏。</span><span class="sxs-lookup"><span data-stu-id="36bb3-256">Azure Information Protection labels show up as an **Information protection** bar in Office applications.</span></span>
    
### <a name="adding-permissions-for-external-users"></a><span data-ttu-id="36bb3-257">添加外部用户的权限</span><span class="sxs-lookup"><span data-stu-id="36bb3-257">Adding permissions for external users</span></span>

<span data-ttu-id="36bb3-p131">有两种方法可以授予外部用户访问 Azure 的信息保护受保护的文件。在这两个这种情况下，外部用户必须拥有 Azure 的广告帐户。如果外部用户不能使用 Azure AD 的组织的成员，他们可以获取的 Azure 的广告帐户作为个人利用该注册页面： [https://aka.ms/aip-signup](https://aka.ms/aip-signup)。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p131">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>
  
- <span data-ttu-id="36bb3-261">将外部用户添加到用于配置的标签保护 Azure AD 组</span><span class="sxs-lookup"><span data-stu-id="36bb3-261">Add external users to an Azure AD group that is used to configure protection for a label</span></span>
    
     <span data-ttu-id="36bb3-p132">您将需要首先为您的目录中的 B2B 用户添加帐户。它可以需要几个小时的[组成员身份缓存的 Azure 权限管理](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)。使用此方法，将权限授予设有标签 （即使文件保护到 Azure AD 组添加用户之前） 的所有现有文件。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p132">You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group membership caching by Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>
    
- <span data-ttu-id="36bb3-265">外部用户将直接添加到标签保护</span><span class="sxs-lookup"><span data-stu-id="36bb3-265">Add external users directly to the label protection</span></span>
    
     <span data-ttu-id="36bb3-p133">可以从组织 (例如 Fabrikam.com)，（例如组织内部财务组） Azure AD 组或单个用户添加的所有用户。例如，您可以添加标签保护外部团队的管理机构。使用此方法，只对外部实体添加到保护后，保护带标签的文件授予权限。</span><span class="sxs-lookup"><span data-stu-id="36bb3-p133">You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>
    
### <a name="deploying-and-using-azure-information-protection"></a><span data-ttu-id="36bb3-269">部署并使用 Azure 信息保护</span><span class="sxs-lookup"><span data-stu-id="36bb3-269">Deploying and using Azure Information Protection</span></span>

<span data-ttu-id="36bb3-270">有关配置此解决方案中的 Azure 信息保护的步骤，请参阅[使用 Azure 信息保护来保护 SharePoint Online 文件](protect-sharepoint-online-files-with-azure-information-protection.md)。</span><span class="sxs-lookup"><span data-stu-id="36bb3-270">For the steps to configure Azure Information Protection in this solution, see [Protect SharePoint Online files with Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="36bb3-271">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36bb3-271">See Also</span></span>

[<span data-ttu-id="36bb3-272">为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南</span><span class="sxs-lookup"><span data-stu-id="36bb3-272">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="36bb3-273">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="36bb3-273">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="36bb3-274">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="36bb3-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="36bb3-275">开发/测试环境中保护 SharePoint Online 站点</span><span class="sxs-lookup"><span data-stu-id="36bb3-275">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



