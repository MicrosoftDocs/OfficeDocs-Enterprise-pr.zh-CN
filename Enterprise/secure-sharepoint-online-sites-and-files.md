---
title: "SharePoint Online 网站和文件保护"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "摘要： 为保护 SharePoint Online Office 365 中的文件的配置建议。"
ms.openlocfilehash: 336dd4114e7853319fede88f9f3ea5aa613b2081
ms.sourcegitcommit: 4a347cfb16405d5213b28f332d80e244fca0fb8f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/18/2017
---
# <a name="secure-sharepoint-online-sites-and-files"></a><span data-ttu-id="0f8fa-103">SharePoint Online 网站和文件保护</span><span class="sxs-lookup"><span data-stu-id="0f8fa-103">Secure SharePoint Online sites and files</span></span>

 <span data-ttu-id="0f8fa-104">**摘要：**为保护 SharePoint Online Office 365 中的文件的配置建议。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-104">**Summary:** Configuration recommendations for protecting files in SharePoint Online and Office 365.</span></span>
  
<span data-ttu-id="0f8fa-p101">本文提供了有关配置 SharePoint Online 的工作组站点和平衡安全而且易于协作的文件保护的建议。本文定义了四种不同配置，最开放的共享策略与组织内的公用网站开始。每个其他配置表示一个有意义的步骤组成的保护，但能够访问和协作资源减少到相关集的用户。这些建议作为起点并调整配置以满足您组织的需要。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p101">This article provides recommendations for configuring SharePoint Online team sites and file protection that balances security with ease of collaboration. This article defines four different configurations, starting with a public site within your organization with the most open sharing policies. Each additional configuration represents a meaningful step up in protection, but the ability to access and collaborate on resources is reduced to the relevant set of users. Use these recommendations as a starting point and adjust the configurations to meet the needs of your organization.</span></span> 
  
<span data-ttu-id="0f8fa-109">这篇文章中的配置符合 Microsoft 对三个层次的数据、 身份和设备的保护的建议：</span><span class="sxs-lookup"><span data-stu-id="0f8fa-109">The configurations in this article align with Microsoft's recommendations for three tiers of protection for data, identities, and devices:</span></span>
  
- <span data-ttu-id="0f8fa-110">基线的保护</span><span class="sxs-lookup"><span data-stu-id="0f8fa-110">Baseline protection</span></span>
    
- <span data-ttu-id="0f8fa-111">写保护</span><span class="sxs-lookup"><span data-stu-id="0f8fa-111">Sensitive protection</span></span>
    
- <span data-ttu-id="0f8fa-112">高度机密的保护</span><span class="sxs-lookup"><span data-stu-id="0f8fa-112">Highly confidential protection</span></span>
    
<span data-ttu-id="0f8fa-113">有关这些层和建议的每一层的功能的详细信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-113">For more information about these tiers and capabilities recommended for each tier, see the following resources.</span></span> 
  
- [<span data-ttu-id="0f8fa-114">标识和 Office 365 的设备保护</span><span class="sxs-lookup"><span data-stu-id="0f8fa-114">Identity and Device Protection for Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [<span data-ttu-id="0f8fa-115">Office 365 中的文件保护解决方案</span><span class="sxs-lookup"><span data-stu-id="0f8fa-115">File Protection Solutions in Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a><span data-ttu-id="0f8fa-116">功能概述</span><span class="sxs-lookup"><span data-stu-id="0f8fa-116">Capability overview</span></span>

<span data-ttu-id="0f8fa-p102">SharePoint Online 团队站点的建议依靠各种 Office 365 提供功能。对于高度机密的站点，建议使用 Azure 的信息保护。这将包括在企业移动 + 安全 (EMS)。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p102">Recommendations for SharePoint Online team sites draw on a variety of Office 365 capabilities. For highly confidential sites, Azure Information Protection is recommended. This is included in Enterprise Mobility + Security (EMS).</span></span> 
  
<span data-ttu-id="0f8fa-120">下图显示了四个 SharePoint Online 的团队站点的建议的配置。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-120">The following illustration shows the recommended configurations for four SharePoint Online team sites.</span></span>
  
![适用于 SharePoint 网站的推荐配置](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
<span data-ttu-id="0f8fa-122">图所示：</span><span class="sxs-lookup"><span data-stu-id="0f8fa-122">As illustrated:</span></span>
  
- <span data-ttu-id="0f8fa-p103">基线保护包括 SharePoint Online 团队站点的两个选项 — — 一个公共站点和专用站点。公共网站可以发现，并由组织中的任何人访问。只能发现和访问网站的成员的专用网站。同时这些站点配置允许共享组之外。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p103">Baseline protection includes two options for SharePoint Online team sites — a public site and private site. Public sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the site. Both of these site configurations allow for sharing outside the group.</span></span> 
    
- <span data-ttu-id="0f8fa-127">敏感和高度机密保护的站点都是与访问仅限于特定组的成员的专用站点。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-127">Sites for sensitive and highly confidential protection are private sites with access limited only to members of specific groups.</span></span>
    
- <span data-ttu-id="0f8fa-p104">Office 365 标签提供所需的保护级别的数据进行分类的方法。每个 SharePoint Online 的团队站点都配置为自动标签文件与默认标签的文档库中的网站。对应于四个站点配置，在此示例中的标志是内部公共、 私人、 敏感、 和高度机密。用户可以更改的标签，但这种配置可确保所有文件都获得一个默认标签。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p104">Office 365 labels provide a way to classify data with a needed protection level. Each of the SharePoint Online team sites are configured to automatically label files in document libraries with a default label for the site. Corresponding to the four site configurations, the labels in this example are Internal Public, Private, Sensitive, and Highly Confidential. Users can change the labels, but this configuration ensures all files receive a default label.</span></span>
    
- <span data-ttu-id="0f8fa-132">数据丢失防护 (DLP) 策略配置的敏感和高度机密的 Office 365 的标签警告或阻止用户在尝试发送这些类型的组织外部文件时。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-132">Data loss prevention (DLP) policies are configured for the Sensitive and Highly Confidential Office 365 labels to either warn or prevent users when they attempt to send these types of files outside the organization.</span></span>
    
- <span data-ttu-id="0f8fa-133">对于站点配置了高度机密的保护，Azure 信息保护进行加密和授予权限的文件。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-133">For sites configured with highly confidential protection, Azure Information Protection encrypts and grants permissions for files.</span></span>
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a><span data-ttu-id="0f8fa-134">SharePoint Online 和业务的 OneDrive 的租户范围设置</span><span class="sxs-lookup"><span data-stu-id="0f8fa-134">Tenant-wide settings for SharePoint Online and OneDrive for Business</span></span>

<span data-ttu-id="0f8fa-p105">SharePoint Online 和业务的 OneDrive 包括租户范围影响到所有站点和用户的设置。其中的某些设置也可以在网站级别为限制性更强 （但不是更少） 来调整。本部分讨论了影响安全和协作的租户范围设置。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p105">SharePoint Online and OneDrive for Business include tenant-wide settings that affect all sites and users. Some of these settings can also be adjusted at the site level to be more restrictive (but not less). This section discusses tenant-wide settings that affect security and collaboration.</span></span> 
  
### <a name="sharing"></a><span data-ttu-id="0f8fa-138">共享</span><span class="sxs-lookup"><span data-stu-id="0f8fa-138">Sharing</span></span>

<span data-ttu-id="0f8fa-139">对于本解决方案，我们建议以下的租户范围设置：</span><span class="sxs-lookup"><span data-stu-id="0f8fa-139">For this solution, we recommend the following tenant-wide settings:</span></span>
  
- <span data-ttu-id="0f8fa-140">保持默认的共享策略，允许与所有帐户类型，包括匿名共享的所有共享。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-140">Keep the default sharing policy that allows all sharing with all account types, including anonymous sharing.</span></span>
    
- <span data-ttu-id="0f8fa-141">如果需要，请设置过期，匿名的链接。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-141">Set anonymous links to expire, if desired.</span></span>
    
- <span data-ttu-id="0f8fa-p106">更改到内部共享的默认链接类型。这有助于防止数据意外泄漏，在您的组织之外。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p106">Change the default link type for sharing to Internal. This helps prevent accidental data leakage outside your organization.</span></span>
    
<span data-ttu-id="0f8fa-p107">虽然这可能看起来有悖常理，允许外部共享，这种方法提供了更好地控制文件共享到电子邮件中发送的文件进行比较。SharePoint Online 和 Outlook 协同工作以提供关于文件的安全协作。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p107">While it might seem counterintuitive to allow external sharing, this approach provides more control over file sharing compared to sending files in email. SharePoint Online and Outlook work together to provide secure collaboration on files.</span></span> 
  
- <span data-ttu-id="0f8fa-146">默认情况下，Outlook 共享文件，而是通过电子邮件发送该文件的链接。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-146">By default, Outlook shares a link to a file instead of sending the file in email.</span></span> 
    
- <span data-ttu-id="0f8fa-147">SharePoint Online 和业务的 OneDrive 可以轻松与正在组织内外的参与者共享文件的链接</span><span class="sxs-lookup"><span data-stu-id="0f8fa-147">SharePoint Online and OneDrive for Business make it easy to share links to files with contributors who are both inside and outside your organization</span></span>
    
<span data-ttu-id="0f8fa-p108">您还可以控制可帮助管理外部共享。例如，您可以：</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p108">You also have controls to help govern external sharing. For example, you can:</span></span>
  
- <span data-ttu-id="0f8fa-150">禁用匿名来宾链接。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-150">Disable an anonymous guest link.</span></span>
    
- <span data-ttu-id="0f8fa-151">吊销用户对站点的访问。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-151">Revoke user access to a site.</span></span>
    
- <span data-ttu-id="0f8fa-152">谁有权访问特定的网站或文档，请参阅。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-152">See who has access to a specific site or document.</span></span>
    
- <span data-ttu-id="0f8fa-153">设置匿名共享链接过期 （租户设置）。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-153">Set anonymous sharing links to expire (tenant setting).</span></span>
    
- <span data-ttu-id="0f8fa-154">可以共享外部组织 （租户设置） 的限制。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-154">Limit who can share outside your organization (tenant setting).</span></span>
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a><span data-ttu-id="0f8fa-155">使用外部数据丢失防护 (DLP) 和共享</span><span class="sxs-lookup"><span data-stu-id="0f8fa-155">Use external sharing together with data loss prevention (DLP)</span></span>

<span data-ttu-id="0f8fa-p109">如果您不允许外部共享时，与业务用户需要了解备用工具和方法。Microsoft 建议您将合并外部共享与 DLP 策略来保护敏感和高度机密文件。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p109">If you don't allow external sharing, users with a business need will find alternate tools and methods. Microsoft recommends you combine external sharing with DLP policies to protect sensitive and highly confidential files.</span></span>
  
### <a name="device-access-settings"></a><span data-ttu-id="0f8fa-158">设备访问设置</span><span class="sxs-lookup"><span data-stu-id="0f8fa-158">Device access settings</span></span>

<span data-ttu-id="0f8fa-p110">SharePoint Online 和 OneDrive 的业务设备访问设置使您可以确定是否限制为仅限于浏览器访问 （不能下载文件），或访问被阻止。这些设置目前在第一版，并且应用租户范围。即将是在站点级别配置设备访问策略的能力。对于本解决方案，建议不使用应用组织范围内的设备访问设置。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p110">Device access settings for SharePoint Online and OneDrive for Business let you determine whether access is limited to browser only (files can't be downloaded) or if access is blocked. These settings are currently in First Release and apply tenant-wide. Coming soon is the ability to configure device access policies at the site level. For this solution, we recommend not using device access settings that apply tenant-wide.</span></span>
  
<span data-ttu-id="0f8fa-163">要使用设备访问设置，而这些在第一个版本是：[设置标准或 Office 365 中的第一个发布选项](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-163">To use device access settings while these are in first release: [Set up the Standard or First Release Options in Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).</span></span>
  
### <a name="onedrive-for-business"></a><span data-ttu-id="0f8fa-164">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="0f8fa-164">OneDrive for Business</span></span>

<span data-ttu-id="0f8fa-p111">请访问这些设置，以决定是否要更改业务网站的默认设置为 OneDrive。目前，共享和设备访问权限设置 SharePoint Online 管理中心从复制，并应用于这两种环境。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p111">Visit these settings to decide if you want to change the default settings for OneDrive for Business sites. Currently, the sharing and device access settings are duplicated from the SharePoint Online admin center and apply to both environments.</span></span>
  
## <a name="sharepoint-team-site-configuration"></a><span data-ttu-id="0f8fa-167">SharePoint 工作组网站配置</span><span class="sxs-lookup"><span data-stu-id="0f8fa-167">SharePoint team site configuration</span></span>

<span data-ttu-id="0f8fa-p112">下表总结了每个团队站点在本文的前面部分中描述的配置。作为起始点建议使用这些配置和调整以满足组织的需要的网站类型和配置。不是每个组织都需要每种类型的网站。只有较少的组织需要高度机密的保护。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p112">The following table summarizes the configuration for each of the team sites described earlier in this article. Use these configurations as starting point recommendations and adjust the site types and configurations to meet the needs of your organization. Not every organization needs every type of site. Only a small number of organizations require highly confidential protection.</span></span>
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||<span data-ttu-id="0f8fa-172">**基线保护 #1**</span><span class="sxs-lookup"><span data-stu-id="0f8fa-172">**Baseline protection #1**</span></span> <br/> |<span data-ttu-id="0f8fa-173">**基线保护 #2**</span><span class="sxs-lookup"><span data-stu-id="0f8fa-173">**Baseline protection #2**</span></span> <br/> |<span data-ttu-id="0f8fa-174">**写保护**</span><span class="sxs-lookup"><span data-stu-id="0f8fa-174">**Sensitive protection**</span></span> <br/> |<span data-ttu-id="0f8fa-175">**高度机密**</span><span class="sxs-lookup"><span data-stu-id="0f8fa-175">**Highly confidential**</span></span> <br/> |
|<span data-ttu-id="0f8fa-176">说明</span><span class="sxs-lookup"><span data-stu-id="0f8fa-176">Description</span></span>  <br/> |<span data-ttu-id="0f8fa-177">打开搜索和组织内的协作。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-177">Open discovery and collaboration within the organization.</span></span>  <br/> |<span data-ttu-id="0f8fa-178">组与组外允许共享和专用网站。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-178">Private site and group with sharing allowed outside the group.</span></span>  <br/> |<span data-ttu-id="0f8fa-p113">独立的网站，在其中定义的访问级别的特定组中的成员资格。只允许对网站的成员共享。DLP 将尝试发送在组织外部文件时警告用户。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p113">Isolated site, in which levels of access are defined by membership in specific groups. Sharing is only allowed to members of the site. DLP warns users when attempting to send files outside the organization.</span></span>  <br/> |<span data-ttu-id="0f8fa-p114">独立的网站 + 文件加密和权限 Azure 的信息保护。DLP 可防止用户发送该组织以外的文件。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p114">Isolated site + file encryption and permissions with Azure Information Protection. DLP prevents users from sending files outside the organization.</span></span>  <br/> |
|<span data-ttu-id="0f8fa-184">私有或公共的工作组站点</span><span class="sxs-lookup"><span data-stu-id="0f8fa-184">Private or public team site</span></span>  <br/> |<span data-ttu-id="0f8fa-185">公用的</span><span class="sxs-lookup"><span data-stu-id="0f8fa-185">Public</span></span>  <br/> |<span data-ttu-id="0f8fa-186">专用</span><span class="sxs-lookup"><span data-stu-id="0f8fa-186">Private</span></span>  <br/> |<span data-ttu-id="0f8fa-187">专用</span><span class="sxs-lookup"><span data-stu-id="0f8fa-187">Private</span></span>  <br/> |<span data-ttu-id="0f8fa-188">专用</span><span class="sxs-lookup"><span data-stu-id="0f8fa-188">Private</span></span>  <br/> |
|<span data-ttu-id="0f8fa-189">谁可以访问？</span><span class="sxs-lookup"><span data-stu-id="0f8fa-189">Who has access?</span></span>  <br/> |<span data-ttu-id="0f8fa-190">每个人在组织中，包括 B2B 用户和来宾用户。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-190">Everybody in the organization, including B2B users and guest users.</span></span>  <br/> |<span data-ttu-id="0f8fa-p115">只有网站的成员。其他人可以请求访问权限。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p115">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="0f8fa-p116">只有网站的成员。其他人可以请求访问权限。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p116">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="0f8fa-p117">仅限成员。其他人不能请求访问权限。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p117">Members only. Others cannot request access.</span></span>  <br/> |
|<span data-ttu-id="0f8fa-197">站点级共享控制</span><span class="sxs-lookup"><span data-stu-id="0f8fa-197">Site-level sharing controls</span></span>  <br/> |<span data-ttu-id="0f8fa-p118">与任何人共享允许。默认设置。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p118">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="0f8fa-p119">与任何人共享允许。默认设置。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p119">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="0f8fa-202">成员不能共享访问该网站。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-202">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="0f8fa-203">非成员可以请求访问该网站，但这些请求必须由网站管理员受到重视。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-203">Non-members can request access to the site, but these requests need to be addressed by a site administrator.</span></span>  <br/> |<span data-ttu-id="0f8fa-204">成员不能共享访问该网站。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-204">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="0f8fa-205">非成员不能请求访问的站点或内容。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-205">Non-members cannot request access to the site or contents.</span></span>  <br/> |
|<span data-ttu-id="0f8fa-206">站点级设备的访问控制</span><span class="sxs-lookup"><span data-stu-id="0f8fa-206">Site-level device access controls</span></span>  <br/> |<span data-ttu-id="0f8fa-207">没有其他的控件。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-207">No additional controls.</span></span>  <br/> |<span data-ttu-id="0f8fa-208">没有其他的控件。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-208">No additional controls.</span></span>  <br/> |<span data-ttu-id="0f8fa-p120">网站级别控制即将推出，这将使用户将文件下载到不符合标准或非域联接的设备。这样，来自所有其他设备只能在浏览器的访问。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p120">Site-level controls are coming soon, which prevents users from downloading files to non-compliant or non-domain joined devices. This allows browser-only access from all other devices.</span></span>  <br/> |<span data-ttu-id="0f8fa-211">网站级别控制即将推出，这将阻止下载到不符合标准或非域联接的设备文件。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-211">Site-level controls are coming soon, which blocks downloading of files to non-compliant or non-domain joined devices.</span></span>  <br/> |
|<span data-ttu-id="0f8fa-212">Office 365 标签</span><span class="sxs-lookup"><span data-stu-id="0f8fa-212">Office 365 labels</span></span>  <br/> |<span data-ttu-id="0f8fa-213">内部公众</span><span class="sxs-lookup"><span data-stu-id="0f8fa-213">Internal Public</span></span>  <br/> |<span data-ttu-id="0f8fa-214">专用</span><span class="sxs-lookup"><span data-stu-id="0f8fa-214">Private</span></span>  <br/> |<span data-ttu-id="0f8fa-215">敏感</span><span class="sxs-lookup"><span data-stu-id="0f8fa-215">Sensitive</span></span>  <br/> |<span data-ttu-id="0f8fa-216">高度机密</span><span class="sxs-lookup"><span data-stu-id="0f8fa-216">Highly Confidential</span></span>  <br/> |
|<span data-ttu-id="0f8fa-217">DLP 策略</span><span class="sxs-lookup"><span data-stu-id="0f8fa-217">DLP policies</span></span>  <br/> |||<span data-ttu-id="0f8fa-218">在组织外部发送为敏感的标有时警告用户。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-218">Warn users when sending files that are labeled as Sensitive outside the organization.</span></span>  <br/> <span data-ttu-id="0f8fa-219">阻止外部共享敏感数据类型，如信用卡号码或其他个人数据，您可以配置其他 DLP 策略用于这些数据类型 （包括自定义的数据类型，您将配置）。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-219">To block external sharing of sensitive data types, such as credit card numbers or other personal data, you can configure additional DLP policies for these data types (including custom data types you configure).</span></span>  <br/> |<span data-ttu-id="0f8fa-p121">阻止用户发送标记为组织外部为高度机密的文件。允许用户通过提供理由，包括那些它们共享的文件重写。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p121">Block users from sending files that are labeled as highly confidential outside organization. Allow users to override this by providing justification, including who they are sharing the file with.</span></span>  <br/> |
|<span data-ttu-id="0f8fa-222">Azure 信息保护</span><span class="sxs-lookup"><span data-stu-id="0f8fa-222">Azure Information Protection</span></span>  <br/> ||||<span data-ttu-id="0f8fa-p122">使用 Azure 信息保护自动加密并授予其权限的文件。它们泄漏的情况下，这种保护传输的文件。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p122">Use Azure Information Protection to automatically encrypt and grant permissions to files. This protection travels with the files in case they are leaked.</span></span>  <br/> <span data-ttu-id="0f8fa-p123">Office 365 无法读取使用 Azure 信息保护加密的文件。此外，DLP 策略只能处理的元数据 （包括标签），但不是包括这些文件 （例如，信用卡号文件内） 的内容。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p123">Office 365 cannot read files encrypted with Azure Information Protection. Additionally, DLP policies can only work with the metadata (including labels) but not the contents of these files (such as credit card numbers within files).</span></span>  <br/> |
   
<span data-ttu-id="0f8fa-p124">若要部署此解决方案中的 SharePoint Online 小组站点的四种不同类型的步骤，请参阅[部署 SharePoint Online 网站的三个层次的保护](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)。创建开发/测试环境的步骤，请参阅[安全 SharePoint Online 网站的开发/测试环境](secure-sharepoint-online-sites-in-a-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p124">For the steps to deploy the four different types of SharePoint Online team sites in this solution, see [Deploy SharePoint Online sites for three tiers of protection](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). For the steps to create a dev/test environment, see [Secure SharePoint Online sites in a dev/test environment](secure-sharepoint-online-sites-in-a-dev-test-environment.md).</span></span> 
  
## <a name="office-365-classification-and-labels"></a><span data-ttu-id="0f8fa-229">Office 365 分类和标签</span><span class="sxs-lookup"><span data-stu-id="0f8fa-229">Office 365 classification and labels</span></span>

<span data-ttu-id="0f8fa-p125">环境中的敏感数据，建议使用 Office 365 标签。在您配置和发布 Office 365 标签：</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p125">Using Office 365 labels is recommended for environments with sensitive data. After you configure and publish Office 365 labels:</span></span>
  
- <span data-ttu-id="0f8fa-232">可以应用于在线 SharePoint 的工作组网站中的文档库的默认标签以便该库中的所有文档的默认标签。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-232">You can apply a default label to a document library in a SharePoint Online team site, so that all documents in that library get the default label.</span></span> 
    
- <span data-ttu-id="0f8fa-233">您可以将标签应用于内容自动匹配特定条件。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-233">You can apply labels to content automatically if it matches specific conditions.</span></span>
    
- <span data-ttu-id="0f8fa-234">您可以应用基于 Office 365 提供标签的 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-234">You can apply DLP policies that are based on Office 365 labels.</span></span>
    
- <span data-ttu-id="0f8fa-p126">您组织中的人员可以应用标签手动内容在 web 上的 Outlook 中 2010年及更高版本的 Outlook，OneDrive 业务、 SharePoint Online 和 Office 365 的组。用户通常非常清楚地知道什么类型的内容他们正在使用，因此可以对其进行分类和应用适当的 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p126">People in your organization can apply a label manually to content in Outlook on the web, Outlook 2010 and later, OneDrive for Business, SharePoint Online, and Office 365 groups. Users often know best what type of content they're working with, so they can classify it and have the appropriate DLP policy applied.</span></span>
    
![适用于 SharePoint 网站的推荐配置](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
<span data-ttu-id="0f8fa-238">如所示，这一解决方案包括创建以下标签：</span><span class="sxs-lookup"><span data-stu-id="0f8fa-238">As illustrated, this solution includes creating the following labels:</span></span>
  
- <span data-ttu-id="0f8fa-239">高度机密</span><span class="sxs-lookup"><span data-stu-id="0f8fa-239">Highly Confidential</span></span>
    
- <span data-ttu-id="0f8fa-240">敏感</span><span class="sxs-lookup"><span data-stu-id="0f8fa-240">Sensitive</span></span>
    
- <span data-ttu-id="0f8fa-241">专用</span><span class="sxs-lookup"><span data-stu-id="0f8fa-241">Private</span></span>
    
- <span data-ttu-id="0f8fa-242">内部公众</span><span class="sxs-lookup"><span data-stu-id="0f8fa-242">Internal Public</span></span>
    
<span data-ttu-id="0f8fa-p127">这些标签映射到图中的推荐的网站和本文中前面的图表。本解决方案建议配置 DLP 策略有助于防止文件标记为敏感和高度机密的泄露。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p127">These labels are mapped to the recommended sites in the illustrations and charts earlier in this article. This solution recommends configuring DLP policies to help prevent the leakage of files labeled as Sensitive and Highly Confidential.</span></span>
  
<span data-ttu-id="0f8fa-245">在此解决方案中配置 Office 365 标签和 DLP 策略的步骤，请参阅[Office 365 标签和 DLP 与保护 SharePoint Online 文件](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-245">For the steps to configure Office 365 labels and DLP policies in this solution, see [Protect SharePoint Online files with Office 365 labels and DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).</span></span>
  
## <a name="azure-information-protection"></a><span data-ttu-id="0f8fa-246">Azure 信息保护</span><span class="sxs-lookup"><span data-stu-id="0f8fa-246">Azure Information Protection</span></span>

<span data-ttu-id="0f8fa-p128">使用 Azure 信息保护应用标签和按照文件，无论它们的保护。对于本解决方案，我们建议使用的指定了作用域的 Azure 的信息保护策略和高度机密的标签的子标签进行加密和授权需要使用安全的最高级别保护的文件。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p128">Use Azure Information Protection to apply labels and protections that follow the files wherever they go. For this solution, we recommend you use a scoped Azure Information Protection policy and a sub-label of the Highly Confidential label to encrypt and grant permissions to files that need to be protected with the highest level of security.</span></span> 
  
<span data-ttu-id="0f8fa-p129">请注意当 Azure 信息保护加密应用于存储在 Office 365 中的文件时，此服务无法处理这些文件的内容。共同创作、 eDiscovery、 搜索、 Delve 和其他协作功能不起作用。DLP 策略只能处理的元数据 （包括 Office 365 的标签），但不是包括这些文件 （例如，信用卡号文件内） 的内容。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p129">Be aware that when Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. DLP policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
  
![Azure 信息保护是在 Azure 中进行配置，标签显示在客户端工具栏中](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
<span data-ttu-id="0f8fa-253">图所示：</span><span class="sxs-lookup"><span data-stu-id="0f8fa-253">As illustrated:</span></span>
  
- <span data-ttu-id="0f8fa-p130">在 Microsoft Azure 门户配置了 Azure 的信息保护策略和标签。建议配置的指定了作用域的 Azure 的信息保护策略的子标签。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p130">You configure Azure Information Protection policies and labels in the Microsoft Azure portal. Configuring a sub-label of a scoped Azure Information Protection policy is recommended.</span></span>
    
- <span data-ttu-id="0f8fa-256">Azure 的信息保护标签显示了作为 Office 应用程序中的**信息保护**栏。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-256">Azure Information Protection labels show up as an **Information protection** bar in Office applications.</span></span>
    
### <a name="adding-permissions-for-external-users"></a><span data-ttu-id="0f8fa-257">添加外部的用户的权限</span><span class="sxs-lookup"><span data-stu-id="0f8fa-257">Adding permissions for external users</span></span>

<span data-ttu-id="0f8fa-p131">有两种方法可以授予外部用户访问 Azure 的信息保护受保护的文件。在这两个这种情况下，外部用户必须拥有 Azure 的广告帐户。如果外部用户不能使用 Azure AD 的组织的成员，他们可以获取的 Azure 的广告帐户作为个人利用该注册页面： [https://aka.ms/aip-signup](https://aka.ms/aip-signup)。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p131">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>
  
- <span data-ttu-id="0f8fa-261">将外部用户添加到用于配置的标签保护 Azure AD 组</span><span class="sxs-lookup"><span data-stu-id="0f8fa-261">Add external users to an Azure AD group that is used to configure protection for a label</span></span>
    
     <span data-ttu-id="0f8fa-p132">您将需要首先为您的目录中的 B2B 用户添加帐户。它可以需要几个小时的[组成员身份缓存的 Azure 权限管理](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)。使用此方法，将权限授予设有标签 （即使文件保护到 Azure AD 组添加用户之前） 的所有现有文件。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p132">You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group membership caching by Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>
    
- <span data-ttu-id="0f8fa-265">外部用户将直接添加到标签保护</span><span class="sxs-lookup"><span data-stu-id="0f8fa-265">Add external users directly to the label protection</span></span>
    
     <span data-ttu-id="0f8fa-p133">可以从组织 (例如 Fabrikam.com)，（例如组织内部财务组） Azure AD 组或单个用户添加的所有用户。例如，您可以添加标签保护外部团队的管理机构。使用此方法，只对外部实体添加到保护后，保护带标签的文件授予权限。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-p133">You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>
    
### <a name="deploying-and-using-azure-information-protection"></a><span data-ttu-id="0f8fa-269">部署和使用 Azure 的信息保护</span><span class="sxs-lookup"><span data-stu-id="0f8fa-269">Deploying and using Azure Information Protection</span></span>

<span data-ttu-id="0f8fa-270">将 Azure 信息保护配置此解决方案中的步骤，请参阅[保护 SharePoint Online Azure 的信息保护的文件](protect-sharepoint-online-files-with-azure-information-protection.md)。</span><span class="sxs-lookup"><span data-stu-id="0f8fa-270">For the steps to configure Azure Information Protection in this solution, see [Protect SharePoint Online files with Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0f8fa-271">See Also</span><span class="sxs-lookup"><span data-stu-id="0f8fa-271">See Also</span></span>

[<span data-ttu-id="0f8fa-272">为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南</span><span class="sxs-lookup"><span data-stu-id="0f8fa-272">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="0f8fa-273">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="0f8fa-273">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="0f8fa-274">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="0f8fa-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="0f8fa-275">开发/测试环境中的安全 SharePoint Online 网站</span><span class="sxs-lookup"><span data-stu-id="0f8fa-275">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



