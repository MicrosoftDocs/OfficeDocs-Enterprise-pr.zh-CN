---
title: "向 Office 365 中的个人数据应用保护"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- GDPR
- Strat_O365_Enterprise
ms.assetid: 
description: "了解如何使用 DLP 策略保护 Office 365 中的个人数据。"
ms.openlocfilehash: e3ecb020a569cbf2cdcf50b4aead5cedf962b4d9
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="apply-protection-to-personal-data-in-office-365"></a>向 Office 365 中的个人数据应用保护

对 Office 365 中的个人信息的保护包括使用数据丢失防护功能。借助 Office 365 安全与合规中心中的数据丢失防护 (DLP) 策略，可以识别、监视和自动保护 Office 365 内的敏感信息。

本主题介绍了如何使用 DLP 保护个人数据。本主题还列出了可用于实现 GDPR 符合性的其他保护功能，其中包括在 SharePoint 库中设置权限及使用设备访问策略。

## <a name="apply-protection-using-data-loss-prevention-in-office-365"></a>在 Office 365 中使用数据丢失防护应用保护

借助 DLP，可以：

-   识别许多位置中的敏感信息。

-   防止意外共享敏感信息。

-   帮助用户了解如何保持符合性，同时不会中断工作流。

-   查看显示符合组织 DLP 策略的内容的 DLP 报告。

有关详细信息，请参阅[数据丢失防护策略概述](https://support.office.com/zh-CN/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)。

![用于创建数据丢失防护策略的选项](Media/Apply-protection-to-personal-data-in-Office-365-image1.png)

此图显示了用于创建 DLP 策略的选项。

-   选择要应用的保护。保护功能可以是：

    -   针对用户的策略提示

    -   针对管理员的电子邮件报告

    -   防止外部和/或内部共享

-   选择应用保护的条件。向包含此内容类型的文档应用保护：可以将策略配置为使用敏感信息类型和/或标签。

### <a name="using-dlp-for-gdpr-compliance"></a>使用 DLP 实现 GDPR 符合性

Office 365 DLP 的主要用途之一是识别出 Office 365 环境中与欧盟数据主体相关的个人数据。Office 365 DLP 可以告知合规性团队 SharePoint Online 和 OneDrive for Business 中存储的个人信息位于何处，或者用户何时发送了包含个人信息的电子邮件。当员工使用与欧盟居民有关的个人信息时，DLP 还可以为他们提供策略提示。

环境中存储的欧盟居民数据位于何处，以及允许员工对其进行哪些处理，对这些感知度的培养和提高代表使用 Office 365 DLP 进行的信息保护级别。通常，已具有此信息类型访问权限的员工需要该访问权限来执行其日常工作。强制执行 DLP 策略有助于遵循 GDPR，此方式可以不限制访问权限。

但是，若要遵循 GDPR，通常会涉及到从法律和信息安全角度对组织进行风险评估、对所存储的个人信息的类型及所在位置进行识别，以及是否有存储和处理该信息的正当理由。基于该评估实现策略来保护组织并遵循 GDPR 的过程可能需要删除员工对包含欧盟数据主体个人信息的文档的访问权限。如需进一步的保护，可配置其他 DLP 保护。

下表列出了使用 DLP 增强保护的三个配置项。第一个配置项（感知度）可用作针对 GDPR 的保护的起点和最低级别。

### <a name="example-protection-levels-that-can-be-configured-with-dlp-policies-and-used-for-gdpr-compliance"></a>可使用 DLP 策略配置的用于实现 GDPR 符合性的保护级别示例

<table>
<thead>
<tr class="header">
<th align="left"><strong>保护级别</strong></th>
<th align="left"><strong>对包含与欧盟数据主体相关个人信息的文档的 DLP 配置</strong></th>
<th align="left"><strong>优势和风险</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">感知度</td>
<td align="left"><p>在 SharePoint Online 和 OneDrive for Business 中的文档内发现此数据时，向合规性团队发送电子邮件通知。</p>
<p>在员工访问包含此数据的文档时，在 SharePoint 和 OneDrive for Business 中自定义策略提示并向员工显示相应的提示。</p>
<p>此数据被共享时，进行检测和报告。</p></td>
<td align="left"><p>提高合规性团队及员工对该数据存储位置的感知度。</p>
<p>指导员工学习用于处理包含该数据的文档的公司策略。</p>
<p>无法防止员工对该数据进行内部或外部共享。</p>
<p>可以查看 DLP 报告以获取共享数据，从而决定是否需要增强保护。</p></td>
</tr>
<tr class="even">
<td align="left">阻止外部共享</td>
<td align="left"><p>在将 SharePoint Online 和 OneDrive for Business 中包含该数据的文档内容与外部用户共享后，限制访问该内容。</p>
<p>防止向外部收件人发送附带包含该数据的文档的电子邮件。</p>
<p>此数据被共享时，进行检测和报告。</p></td>
<td align="left"><p>防止对该数据进行外部共享。同时允许员工在内部使用该数据。</p>
<p>可以查看 DLP 报告来获取内部共享数据，从而决定是否需要增强保护。</p></td>
</tr>
<tr class="odd">
<td align="left">阻止内部和外部共享</td>
<td align="left"><p>在对 SharePoint Online 和 OneDrive for Business 中包含该数据的文档进行内部或外部共享后，限制访问该内容。</p>
<p>防止向内部和外部收件人发送包含该数据的电子邮件。</p></td>
<td align="left"><p>防止对该数据进行内部和外部共享。</p>
<p>员工可能无法完成需要使用该数据的任务。</p>
<p>可以查看 DLP 报告以获取内部或外部共享数据，从而决定是否需要进行最终用户培训。</p></td>
</tr>
</tbody>
</table>

注意：在某些情况下，随着保护级别的提高，用户访问信息的能力会下降，进而可能会对用户的效率或完成日常任务的能力产生潜在的影响。通过实施可对员工产生影响的策略提高保护级别通常会与最终用户培训双管齐下，指导用户学习新的安全策略和流程，帮助他们在更加安全的环境中继续保持高效率。

### <a name="example-dlp-policy-for-gdpr--awareness"></a>针对 GDPR 的 DLP 策略示例 — 感知度 

名称：对受 GDPR 制约的个人数据的感知度

说明：向员工显示策略提示、在 SharePoint Online 和 OneDrive for Business 中的文档内发现该数据时通知合规性团队，在该数据在组织外部共享时进行检测和报告。

<table>
<thead>
<tr class="header">
<th align="left"><strong>控制</strong></th>
<th align="left"><strong>设置</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">选择要保护的信息</td>
<td align="left">选择自定义策略模板。</td>
</tr>
<tr class="even">
<td align="left">位置</td>
<td align="left">Office 365 中的所有位置</td>
</tr>
<tr class="odd">
<td align="left">查找所包含的内容</td>
<td align="left">单击“编辑”，然后添加为环境策展的所有敏感信息类型。</td>
</tr>
<tr class="even">
<td align="left">共享此内容时进行检测</td>
<td align="left">选中此框，然后选择“与组织外部人员”。</td>
</tr>
<tr class="odd">
<td align="left">当内容符合策略设置时通知用户</td>
<td align="left"><p>选中此框（“向用户显示策略提示并向他们发送电子邮件通知。”）</p>
<p>单击“自定义提示和电子邮件”，然后针对所在的环境进行更新。请参阅下文中的默认通知：<a href="https://support.office.com/en-us/article/Send-email-notifications-and-show-policy-tips-for-DLP-policies-87496bc5-9601-4473-8021-cb05c71369c1?ui=en-US&amp;rs=en-US&amp;ad=US">发送电子邮件通知并显示 DLP 策略的策略提示</a>。</p></td>
</tr>
<tr class="even">
<td align="left">共享特定数量的敏感信息时进行检测</td>
<td align="left"><p>“被共享的内容包含: 至少 ____ 个同种敏感信息类型的实例时进行检测” — 将其设置为 1。</p>
<p>“在电子邮件中发送事件报告” — 选中此框。单击“选择要在报告中包含的内容及收件人”。务必添加合规性团队。</p>
<p>“限制可以访问此内容及可覆盖此策略的人员” — 取消选中此复选框，允许接收关于敏感信息的通知，不阻止用户访问该信息。</p></td>
</tr>
</tbody>
</table>

所有位置包括：

-   SharePoint Online

-   OneDrive for Business 帐户

-   Exchange 邮箱

由于内容搜索当前不允许通过电子邮件检测敏感信息类型，因此请考虑使用各个策略中的敏感信息类型的子集为 Exchange 创建单独的策略，并监视这些策略的执行情况。

## <a name="additional-protection-you-can-apply-to-protect-personal-data-in-office-365"></a>可以应用于保护 Office 365 中的个人数据的其他保护

敏感信息类型、标签和数据丢失防护策略有助于识别包含特定数据的文档，并应用保护。但是，这些保护以针对数据访问权限设置了适当的权限、用户拥有的帐户未被攻击及设备正常运行为基础。

下图详细说明了为保护个人数据访问可以应用的其他保护。

![用于保护个人数据访问的其他保护](Media/Apply-protection-to-personal-data-in-Office-365-image2.png)

为便于访问，下表提供了上图中的相同信息。

<table>
<thead>
<tr class="header">
<th align="left"><strong>保护范围</strong></th>
<th align="left"><strong>功能</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">文档和电子邮件级别的保护（包括传输中的邮件，但当前不包括静态邮箱）</td>
<td align="left"><p>敏感信息类型</p>
<p>Office 标签</p>
<p>数据丢失防护策略</p>
<p>适用于电子邮件的 Office 365 邮件加密</p></td>
</tr>
<tr class="even">
<td align="left">网站和库级别的保护（包括 SharePoint Online 和 OneDrive for Business 网站）</td>
<td align="left"><p>SharePoint Online 和 OneDrive for Business 网站和库的权限</p>
<p>适用于 SharePoint Online 和 OneDrive for Business 的外部共享策略（网站级别）</p>
<p>网站级别的设备访问策略</p></td>
</tr>
<tr class="odd">
<td align="left">服务访问保护（包括对 Office 365 中的所有服务的访问）</td>
<td align="left"><p>企业移动性 + 安全性 (EMS) 套件中的标识和设备访问保护</p>
<p>特权访问管理</p>
<p>Windows 10 安全功能</p></td>
</tr>
</tbody>
</table>

本文的剩余部分详细介绍了上述各个保护类别。

### <a name="capabilities-that-are-ok-to-use-with-gdpr"></a>适用于 GDPR 的功能

可以在针对 GDPR 符合性配置的环境中使用下列功能。这些功能不是 GDPR 符合性所必需的，但是可以使用它们，并且不会对发现、保护、监视和报告与 GDPR 符合性有关数据的功能产生不良影响。

客户密钥 — 允许客户始终控制用于加密 Office 365 内的静态数据的加密密钥。建议仅为具有管理自身加密密钥管理需求的客户启用此功能。

客户密码箱 — 使用客户密码箱可以控制 Microsoft 支持工程师访问你的数据的方式，在必要时根据具体情况解决技术问题。可以控制是否向支持工程师提供数据访问权限。为每个请求提供了到期时间。

## <a name="site-and-library-level-protection"></a>网站和库级别的保护

### <a name="permissions-for-sharepoint-and-onedrive-for-business-libraries"></a>SharePoint 和 OneDrive for Business 库的权限

使用 SharePoint 中的权限提供或限制用户对网站或其内容的访问权限。向默认的 SharePoint 组中添加单个用户或 Azure Active Directory 组。或者，创建自定义组并进行更细化的控制。

![从“完全控制”到“仅查看”的权限级别](Media/Apply-protection-to-personal-data-in-Office-365-image3.png)

此图绘制了从“完全控制”到“仅查看”的权限级别。下表包含相同的信息。

<table>
<thead>
<tr class="header">
<th align="left"><strong>完全控制</strong></th>
<th align="left"><strong>设计</strong></th>
<th align="left"><strong>编辑</strong></th>
<th align="left"><strong>参与</strong></th>
<th align="left"><strong>读取</strong></th>
<th align="left"><strong>仅查看</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left">参与 + 审核和自定义</td>
<td align="left">参与 + 添加、编辑和删除列表（不只是列表项）</td>
<td align="left">查看、添加、更新、删除列表项和文档</td>
<td align="left">查看和下载</td>
<td align="left">查看，不能下载</td>
</tr>
</tbody>
</table>

详细信息：

-   [了解 SharePoint 中的权限级别](https://support.office.com/zh-CN/article/Understanding-permission-levels-in-SharePoint-87ecbb0e-6550-491a-8826-c075e4859848)

-   [了解 SharePoint 组](https://support.office.com/zh-CN/article/Understanding-SharePoint-groups-94d9b261-161e-4ace-829e-eca1c8cd2eb8)

### <a name="external-sharing-policies-for-sharepoint-and-onedrive-for-business-libraries"></a>适用于 SharePoint 和 OneDrive for Business 库的外部共享策略

许多组织允许进行外部共享，以便支持协作。查看租户范围的设置是如何配置的。然后查看对包含个人数据的网站的外部共享设置。

外部用户是指已邀请其访问你的 SharePoint Online 网站和文档，但不具备你的 SharePoint Online 或 Microsoft Office 365 订阅的许可证的组织外部人员。

外部共享策略适用于 SharePoint Online 和 OneDrive for Business。

-   必须是 SharePoint Online 管理员才能配置共享策略。

-   必须是网站所有者或具有完全控制权限才能与外部用户共享网站或文档。

下表总结了可以配置的控制。

<table>
<thead>
<tr class="header">
<th align="left"><strong>控制类别</strong></th>
<th align="left"><strong>选项</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">共享类型</td>
<td align="left"><p>不允许在组织外部共享（可以为单个网站集设置）</p>
<p>仅允许向经过身份验证的外部用户共享（允许向新的此类用户共享，或仅限于现有的此类用户，可以为单个网站集设置）*</p>
<p>允许通过匿名访问链接向外部用户共享（可以为单个网站集设置）</p>
<p>使用域限制外部共享（允许或拒绝列表）</p>
<p>选择默认的链接类型（匿名、公司可共享或受限）</p>
</td>
</tr>
<tr class="even">
<td align="left">外部用户可以执行的操作</td>
<td align="left"><p>阻止外部用户共享不属于他们的文件、文件夹、网站</p>
<p>要求外部用户使用接收邀请的同一帐户来接受共享邀请</p></td>
</tr>
<tr class="odd">
<td align="left">通知</td>
<td align="left"><p>目前仅在 OneDrive for Business 中可用。以下情况发生时通知所有者：</p>
- <p>用户邀请其他外部用户访问共享文件</p>
- <p>外部用户接受访问文件的邀请</p>
- <p>创建或更改了匿名访问链接</p></td>
</tr>
</tbody>
</table>

详细信息：

-   [管理 SharePoint Online 环境的外部共享](https://support.office.com/en-us/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&rs=en-US&ad=US)

-   [与组织外部的用户共享站点或文档](https://support.office.com/zh-CN/article/Share-sites-or-documents-with-people-outside-your-organization-80e49744-e30f-44db-8d51-16661b1d4232)

### <a name="site-level-device-access-policies"></a>网站级别的设备访问策略

可通过 SharePoint Online 和 OneDrive for Business 配置网站级别的设备访问策略。由此可为包含敏感数据的网站配置更多保护功能。

若要配置网站级别的设备访问策略，请务必将这些策略与租户级别的策略以及已在 Azure Active Directory、Intune 和 Intune 应用管理中配置的访问策略进行协调。

SharePoint 和 OneDrive for Business 的设备访问策略需要支持 Azure Active Directory 和 Microsoft Intune 中的策略，具体取决于正在实现的方案。下表总结了可以通过设备访问策略实现的目标，并说明了哪些产品需要支持策略。

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">仅允许来自指定 IP 地址位置的访问</th>
<th align="left">阻止用户将文件下载到未加入域的设备</th>
<th align="left">阻止在未加入域的设备上进行的访问</th>
<th align="left">阻止用户将文件下载到不符合的设备</th>
<th align="left">阻止在不符合的设备上进行的访问</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">SharePoint 管理中心</td>
<td align="left">是</td>
<td align="left">是</td>
<td align="left">是</td>
<td align="left">是</td>
<td align="left">是</td>
</tr>
<tr class="even">
<td align="left">Azure Active Directory</td>
<td align="left"></td>
<td align="left">是</td>
<td align="left">是</td>
<td align="left">是</td>
<td align="left">是</td>
</tr>
<tr class="odd">
<td align="left">Microsoft Intune</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left">是</td>
<td align="left">是</td>
</tr>
</tbody>
</table>

详细信息：[SharePoint Online 管理中心：控制来自非托管设备的访问](https://support.office.com/en-us/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622?ui=en-US&rs=en-US&ad=US)。

## <a name="service-access-protection-for-identities-and-devices"></a>对标识和设备的服务访问保护

Microsoft 建议为访问服务的标识和设备配置保护。用于保护 Office 365 服务访问的功能也可用于保护对其他 SaaS 服务、PaaS 服务甚至是其他云提供程序中的应用的访问。

对标识和设备的访问保护提供了基准保护，确保标识不被攻击、设备安全且在设备上访问的组织数据已隔离并受到保护。

有关入门建议和配置指南，请参阅 [Microsoft 针对政治宣传活动、非营利组织和其他敏捷型组织的安全指南](https://docs.microsoft.com/zh-CN/microsoft-365-enterprise/microsoft-security-guidance)。

对于使用 AD FS 的混合标识环境，请参阅[建议的安全策略和配置](https://docs.microsoft.com/zh-CN/microsoft-365-enterprise/microsoft-security-guidance)。

下图说明了云服务（SaaS、PaaS）、帐户类型（租户域帐户与 B2B 帐户）和服务访问功能之间的关联。请务必注意哪些功能可用于 B2B 帐户。

![云服务、帐户类型和访问功能](Media/Apply-protection-to-personal-data-in-Office-365-image4.png)

为便于访问，本节的剩余部分对此图进行了说明。

### <a name="cloud-services"></a>云服务

Azure Active Directory 提供对任意云服务的标识访问权限，包括非 Microsoft 提供程序（如 Amazon Web Services）。此图显示了 Office 365、“其他 SaaS 应用”和“PaaS 应用”。箭头从 Azure Active Directory 指向上述各个服务，表示 Azure Active Directory 可用于对上述所有应用类型的身份验证。

### <a name="types-of-accounts"></a>帐户类型

租户域帐户是指添加到租户并直接管理的帐户。B2B 帐户是指你邀请与之进行协作的组织外部的用户的帐户。它们可以是其他 Office 365 帐户、其他组织帐户或使用者帐户（例如 Gmail）。此图显示了 Azure Active Directory 内的这两种帐户类型。

### <a name="capabilities"></a>功能

下表中的功能可保护标识和设备。此表说明了哪些功能还可用于 B2B 帐户，与此图类似。

<table>
<thead>
<tr class="header">
<th align="left"><strong>功能</strong></th>
<th align="left"><strong>用于租户域帐户</strong></th>
<th align="left"><strong>用于 Azure B2B 帐户（没有其他许可）</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">多重身份验证和条件访问</td>
<td align="left">是</td>
<td align="left">是</td>
</tr>
<tr class="even">
<td align="left">Azure AD Identity Protection</td>
<td align="left">是</td>
<td align="left">是</td>
</tr>
<tr class="odd">
<td align="left">Azure AD Privileged Identity Management</td>
<td align="left">是</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">移动应用管理 (MAM)</td>
<td align="left">是</td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left">设备注册和管理</td>
<td align="left">是</td>
<td align="left">只有一个组织可以管理设备</td>
</tr>
<tr class="even">
<td align="left">Windows 10 安全功能（基于设备符合性的条件访问需要进行设备管理）</td>
<td align="left">是</td>
<td align="left">是</td>
</tr>
</tbody>
</table>

可以向 B2B 帐户添加许可证，为这些用户提供其他功能，从而在必要时保护对环境中的个人数据的访问。
