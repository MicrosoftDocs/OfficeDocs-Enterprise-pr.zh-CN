---
title: "向 Office 365 中的个人数据应用标签"
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
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "了解如何使用 Office 标签作为 GDPR 保护计划的一部分。"
ms.openlocfilehash: be09afa8efa19d48d6bed2ad818adbcaf2aafcda
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="apply-labels-to-personal-data-in-office-365"></a><span data-ttu-id="89efe-103">向 Office 365 中的个人数据应用标签</span><span class="sxs-lookup"><span data-stu-id="89efe-103">Apply labels to personal data in Office 365</span></span>

 <span data-ttu-id="89efe-p101">如果要使用 Office 标签作为 GDPR 保护计划的一部分，可使用此主题。现在可在 Office 365 安全与合规中心及 Azure 信息保护中创建标签。随着时间的推移，这些技术将整合为统一的标记和分类体验，届时将可以获得更多功能。</span><span class="sxs-lookup"><span data-stu-id="89efe-p101">Use this topic if you are using Office labels as part of your GDPR protection plan. Today labels can be created in the Office 365 Security & Compliance Center and in Azure Information Protection. Over time these technologies will converge into a unified labeling and classification experience and you will be able to achieve even more.</span></span>

<span data-ttu-id="89efe-p102">若要使用标签保护 Office 365 中的个人数据，Microsoft 建议从 Office 标签开始。可以使用高级数据管理，根据敏感信息类型或其他条件自动应用标签。可以结合使用 Office 标签和数据丢失防护来应用保护。还可以将标签与电子数据展示和内容搜索结合使用。即将可以同时将标签和敏感信息类型与 Cloud App Security 结合使用，用于监视位于其他 SaaS 应用中的个人数据。</span><span class="sxs-lookup"><span data-stu-id="89efe-p102">If you are using labels for protection of personal data in Office 365, Microsoft recommends you start with Office labels. You can use Advanced Data Governance to automatically apply labels based on sensitive information types or other criteria. You can use Office labels with data loss prevention to apply protection. You can also use labels with eDiscovery and Content Search. You’ll soon be able to use both labels and sensitive information types with Cloud App Security to monitor personal data that resides in other SaaS apps.</span></span>

<span data-ttu-id="89efe-p103">目前，建议将 Azure 信息保护标签用于向本地和其他云服务及提供程序中的文件应用标签。同时还建议将它们用于 Office 365 中需要进行 Azure 权限管理 (Azure RMS) 加密以实现数据保护的文件，例如商业机密文件。</span><span class="sxs-lookup"><span data-stu-id="89efe-p103">Azure Information Protection labels are currently recommended for applying labels to files on premises and in other cloud services and providers. These are also recommended for files in Office 365 that require Azure Rights Management (Azure RMS) encryption for data protection, such as trade secret files.</span></span>

<span data-ttu-id="89efe-p104">目前对于 Office 365 中包含受 GDPR 制约的数据的文件，不建议使用 Azure 信息保护来应用 Azure RMS 加密。Office 365 服务目前无法读取 RMS 加密的文件。因此该服务无法查找这些文件中的敏感数据。</span><span class="sxs-lookup"><span data-stu-id="89efe-p104">At this time, using Azure Information Protection to apply Azure RMS encryption is not recommended for files in Office 365 with data that is subject to the GDPR. Office 365 services currently cannot read into RMS-encrypted files. Therefore, the service can’t find sensitive data in these files.</span></span>

<span data-ttu-id="89efe-p105">Azure 信息保护标签可应用于 Exchange Online 中的邮件，并且这些标签将与 Office 365 数据丢失防护协作。即将推出统一的分类和标记引擎，届时可以将相同的标签用于电子邮件和文件，包括自动标记和保护传输中的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="89efe-p105">Azure Information Protection labels can be applied to mail in Exchange Online and these labels work with Office 365 data loss prevention. Coming soon with the unified classification and labeling engine you will be able to use the same labels for email and files, including automatically labeling and protecting email in transit.</span></span>

![Office 365 标签和 Azure 信息保护标签](Media/Apply-labels-to-personal-data-in-Office-365-image1.png)

<span data-ttu-id="89efe-120">在此图中：</span><span class="sxs-lookup"><span data-stu-id="89efe-120">In the illustration:</span></span>

-   <span data-ttu-id="89efe-121">将 Office 365 标签用于 SharePoint Online 和 OneDrive for Business 中的个人数据和高度监管的商业机密文件。</span><span class="sxs-lookup"><span data-stu-id="89efe-121">Use Office 365 labels for personal data and for highly regulated & trade secret files in SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="89efe-122">将 Azure 信息保护 (AIP) 标签用于高度监管的商业机密文件、Exchange Online  电子邮件、其他 SaaS 服务中的文件、本地数据中心中的文件及其他云提供程序中的文件。</span><span class="sxs-lookup"><span data-stu-id="89efe-122">Use Azure Information Protection (AIP) labels for highly regulated & trade secret files, Exchange Online email, files in other SaaS services, files in on-premises datacenters, and files in other cloud providers.</span></span>

-   <span data-ttu-id="89efe-123">即将实现：两种标签类型将整合为统一的分类和标记体验。</span><span class="sxs-lookup"><span data-stu-id="89efe-123">Coming soon: both types of labels will converge into a unified classification and labeling experience.</span></span>

## <a name="use-office-labels-and-sensitive-information-types-across-microsoft-365-for-information-protection"></a><span data-ttu-id="89efe-124">使用 Microsoft 365 中的 Office 标签和敏感信息类型进行信息保护</span><span class="sxs-lookup"><span data-stu-id="89efe-124">Use Office labels and sensitive information types across Microsoft 365 for information protection</span></span>

<span data-ttu-id="89efe-125">下图显示了如何将 Office 标签和敏感信息类型用于标签策略、数据丢失防护策略和 Cloud App Security 策略。</span><span class="sxs-lookup"><span data-stu-id="89efe-125">The following illustration shows how Office labels and sensitive information types can be used in label policies, data loss prevention policies, and with Cloud App Security policies.</span></span>

![Office 标签和敏感信息类型](Media/Apply-labels-to-personal-data-in-Office-365-image2.png)

<span data-ttu-id="89efe-127">为便于访问，下表提供了上图中的相同示例。</span><span class="sxs-lookup"><span data-stu-id="89efe-127">For accessibility, the following table provides the same examples in the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="89efe-128"><strong>分类元素</strong></span><span class="sxs-lookup"><span data-stu-id="89efe-128"><strong>Classification elements</strong></span></span></th>
<th align="left"><span data-ttu-id="89efe-129"><strong>标签策略 — 2 个示例</strong></span><span class="sxs-lookup"><span data-stu-id="89efe-129"><strong>Label policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="89efe-130"><strong>数据丢失防护策略 — 2 个示例</strong></span><span class="sxs-lookup"><span data-stu-id="89efe-130"><strong>Data loss prevention policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="89efe-131"><strong>适用于所有 SaaS 应用的 Cloud App Security 策略 — 1 个示例</strong></span><span class="sxs-lookup"><span data-stu-id="89efe-131"><strong>Cloud App Security policies for all SaaS apps — 1 example</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="89efe-p106">Office 标签。示例：个人、公用、客户数据、HR 数据、机密、高度机密</span><span class="sxs-lookup"><span data-stu-id="89efe-p106">Office labels. Examples: Personal, Public, Customer data, HR data, Confidential, Highly confidential</span></span></td>
<td align="left"><p><span data-ttu-id="89efe-p107">自动将此标签 . . .</span><span class="sxs-lookup"><span data-stu-id="89efe-p107">Auto apply this label . . .</span></span></p>
<p><span data-ttu-id="89efe-137">客户数据</span><span class="sxs-lookup"><span data-stu-id="89efe-137">Customer data</span></span></p>
<p><span data-ttu-id="89efe-p108">. . . 应用于与这些敏感信息类型匹配的文档 . . .</span><span class="sxs-lookup"><span data-stu-id="89efe-p108">. . . to documents that match these sensitive information types . . .</span></span></p>
<p><span data-ttu-id="89efe-144">&lt;敏感信息类型示例列表&gt;</span><span class="sxs-lookup"><span data-stu-id="89efe-144">&lt;list of example sensitive information types&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="89efe-p109">将此保护 . . .</span><span class="sxs-lookup"><span data-stu-id="89efe-p109">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="89efe-148">&lt;定义保护&gt;</span><span class="sxs-lookup"><span data-stu-id="89efe-148">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="89efe-p110">. . . 应用于带此标签的文档 . . .</span><span class="sxs-lookup"><span data-stu-id="89efe-p110">. . . to documents with this label . . .</span></span></p>
<p><span data-ttu-id="89efe-155">客户数据</span><span class="sxs-lookup"><span data-stu-id="89efe-155">Customer data</span></span></p></td>
<td align="left"><p><span data-ttu-id="89efe-p111">在以下情况下发出警报：当批准的 SaaS 应用中的带这些属性的文件 . . .</span><span class="sxs-lookup"><span data-stu-id="89efe-p111">Alert when files with these attributes . . .</span></span></p>
<p><span data-ttu-id="89efe-159">&lt;预定义的 PII 属性或自定义表达式&gt;</span><span class="sxs-lookup"><span data-stu-id="89efe-159">&lt;predefined PII attribute -or- custom expression&gt;</span></span></p>
<p><span data-ttu-id="89efe-p112">. . . 被共享到组织外部时</span><span class="sxs-lookup"><span data-stu-id="89efe-p112">. . . in any sanctioned SaaS app are shared outside the organization</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="89efe-p113">敏感信息类型示例：比利时国家/地区号码、信用卡号、克罗地亚身份证号、芬兰国家/地区身份证号码</span><span class="sxs-lookup"><span data-stu-id="89efe-p113">Sensitive information types. Examples: Belgium National Number, Credit Card Number, Croatia Identity Cart Number, Finland National ID</span></span></td>
<td align="left"><p><span data-ttu-id="89efe-p114">发布这些标签，以便用户手动将 . . .</span><span class="sxs-lookup"><span data-stu-id="89efe-p114">Publish these labels for users to manually apply . . .</span></span></p>
<p><span data-ttu-id="89efe-169">&lt;选择标签&gt;</span><span class="sxs-lookup"><span data-stu-id="89efe-169">&lt;select labels&gt;</span></span></p>
<p><span data-ttu-id="89efe-p115">. . . 应用于这些位置 . . .</span><span class="sxs-lookup"><span data-stu-id="89efe-p115">. . . to these locations . . .</span></span></p>
<p><span data-ttu-id="89efe-176">&lt;所有位置或选择特定位置&gt;</span><span class="sxs-lookup"><span data-stu-id="89efe-176">&lt;all locations or choose specific locations&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="89efe-p116">将此保护 . . .</span><span class="sxs-lookup"><span data-stu-id="89efe-p116">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="89efe-180">&lt;定义保护&gt;</span><span class="sxs-lookup"><span data-stu-id="89efe-180">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="89efe-p117">. . . 应用于与这些敏感信息类型匹配的文档&gt;</span><span class="sxs-lookup"><span data-stu-id="89efe-p117">. . . to documents that match these sensitive information types&gt;</span></span></p></td>
<td align="left"><span data-ttu-id="89efe-185">注意：Cloud App Security 中即将推出的属性包括 Office 365 敏感信息类型和 Office 365 及 Azure 信息保护中的统一标签。</span><span class="sxs-lookup"><span data-stu-id="89efe-185">Note: Attributes coming soon to Cloud App Security include Office 365 sensitive information types and Unified labels across Office 365 and Azure Information Protection.</span></span></td>
</tr>
</tbody>
</table>

## <a name="prioritize-auto-apply-label-policies"></a><span data-ttu-id="89efe-186">设置自动应用标签策略的优先级</span><span class="sxs-lookup"><span data-stu-id="89efe-186">Prioritize auto-apply label policies</span></span>

<span data-ttu-id="89efe-p118">对于受 GDPR 制约的个人数据，Microsoft 建议使用为环境策展的敏感信息类型自动应用标签。请务必精心设计和谨慎测试自动应用标签策略，以确保实现预期目标行为。</span><span class="sxs-lookup"><span data-stu-id="89efe-p118">For personal data that is subject to GDPR, Microsoft recommends auto-applying labels by using the sensitive information types you curated for your environment. It is important that auto-apply label policies are well designed and tested to ensure the intended behavior occurs.</span></span>

<span data-ttu-id="89efe-p119">创建自动应用策略的顺序以及用户是否也会应用这些标签，这两点会影响结果。因此，请务必认真规划策略的展示。以下是需要注意的事项。</span><span class="sxs-lookup"><span data-stu-id="89efe-p119">The order that auto-apply policies are created and whether users are also applying these labels affect the result. So, it is important to carefully plan the roll-out. Here’s what you need to know.</span></span>

### <a name="one-label-at-a-time"></a><span data-ttu-id="89efe-191">一次使用一个标签</span><span class="sxs-lookup"><span data-stu-id="89efe-191">One participant at a time (serial)</span></span>

<span data-ttu-id="89efe-192">对一个文档只能分配一个标签。</span><span class="sxs-lookup"><span data-stu-id="89efe-192">You can only assign one label to a document.</span></span>

### <a name="older-auto-apply-policies-win"></a><span data-ttu-id="89efe-193">旧的自动应用策略优先</span><span class="sxs-lookup"><span data-stu-id="89efe-193">Older auto-apply policies win</span></span>

<span data-ttu-id="89efe-p120">如果有多个分配自动应用标签的规则且内容符合多个规则的条件，将分配最旧的规则的标签。因此，配置标签策略前请务必先认真进行规划。如果组织需要更改标签策略的优先级，需要删除这些策略，然后重新创建策略。</span><span class="sxs-lookup"><span data-stu-id="89efe-p120">If there are multiple rules that assign an auto-apply label and content meets the conditions of multiple rules, the label for the oldest rule is assigned. For this reason, it is important to plan the label policies carefully before configuring them. If an organization requires a change to the priority of the label policies, they will need to delete and recreate them.</span></span>

### <a name="manual-user-applied-labels-trump-auto-applied-labels"></a><span data-ttu-id="89efe-197">用户手动应用的标签优先于自动应用的标签</span><span class="sxs-lookup"><span data-stu-id="89efe-197">Manual user-applied labels trump auto-applied labels</span></span>

<span data-ttu-id="89efe-p121">用户手动应用的标签优先于自动应用的标签。自动应用策略无法替换用户已应用的标签。用户可以替换自动应用的标签。</span><span class="sxs-lookup"><span data-stu-id="89efe-p121">Manual user applied labels trump auto-applied labels. Auto-apply policies cannot replace a label that is already applied by a user. Users can replace labels that are auto-applied.</span></span>

### <a name="auto-assigned-labels-can-be-updated"></a><span data-ttu-id="89efe-201">可以更新自动分配的标签</span><span class="sxs-lookup"><span data-stu-id="89efe-201">Auto-assigned labels can be updated</span></span>

<span data-ttu-id="89efe-202">可以通过更加新的标签策略或通过更新现有策略来更新自动分配的标签。</span><span class="sxs-lookup"><span data-stu-id="89efe-202">Auto-assigned labels can be updated by either newer label policies or by updates to existing policies.</span></span>

<span data-ttu-id="89efe-203">确保使用标签的计划包括以下事项：</span><span class="sxs-lookup"><span data-stu-id="89efe-203">Be sure your plan for implementing labels includes:</span></span>

-   <span data-ttu-id="89efe-204">设置自动应用策略创建顺序的优先级。</span><span class="sxs-lookup"><span data-stu-id="89efe-204">Prioritizing the order that auto-apply policies are created.</span></span>

-   <span data-ttu-id="89efe-p122">预留足够的时间，以便可以在展示标签供用户手动应用前自动应用这些标签。标签应用于符合条件的所有内容最多可能需要 7 天。</span><span class="sxs-lookup"><span data-stu-id="89efe-p122">Allowing enough time for labels to be automatically applied before rolling these out for users to manually apply. It can take up to seven days for the labels to be applied to all content that matches the conditions.</span></span>

### <a name="example-priority-for-creating-the-auto-apply-policies"></a><span data-ttu-id="89efe-207">用于创建自动应用策略的优先级示例</span><span class="sxs-lookup"><span data-stu-id="89efe-207">Example priority for creating the auto-apply policies</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="89efe-208"><strong>标签</strong></span><span class="sxs-lookup"><span data-stu-id="89efe-208"><strong>Labels</strong></span></span></th>
<th align="left"><span data-ttu-id="89efe-209"><strong>创建自动应用策略的优先级顺序</strong></span><span class="sxs-lookup"><span data-stu-id="89efe-209"><strong>Priority order to create auto-apply policies</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="89efe-210">人力资源 — 员工数据</span><span class="sxs-lookup"><span data-stu-id="89efe-210">Human Resources — Employee Data</span></span></td>
<td align="left"><span data-ttu-id="89efe-211">1</span><span class="sxs-lookup"><span data-stu-id="89efe-211">1.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="89efe-212">客户数据</span><span class="sxs-lookup"><span data-stu-id="89efe-212">Customer Data</span></span></td>
<td align="left"><span data-ttu-id="89efe-213">2</span><span class="sxs-lookup"><span data-stu-id="89efe-213">2.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="89efe-214">高度机密</span><span class="sxs-lookup"><span data-stu-id="89efe-214">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="89efe-215">3</span><span class="sxs-lookup"><span data-stu-id="89efe-215">3.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="89efe-216">人力资源 — 薪资数据</span><span class="sxs-lookup"><span data-stu-id="89efe-216">Human Resources — Salary Data</span></span></td>
<td align="left"><span data-ttu-id="89efe-217">4</span><span class="sxs-lookup"><span data-stu-id="89efe-217">4.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="89efe-218">机密</span><span class="sxs-lookup"><span data-stu-id="89efe-218">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="89efe-219">5</span><span class="sxs-lookup"><span data-stu-id="89efe-219">5.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="89efe-220">公开</span><span class="sxs-lookup"><span data-stu-id="89efe-220">Public</span></span></td>
<td align="left"><span data-ttu-id="89efe-221">6</span><span class="sxs-lookup"><span data-stu-id="89efe-221">6.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="89efe-222">个人</span><span class="sxs-lookup"><span data-stu-id="89efe-222">Personal</span></span></td>
<td align="left"><span data-ttu-id="89efe-223">无自动应用策略</span><span class="sxs-lookup"><span data-stu-id="89efe-223">No auto-apply policy</span></span></td>
</tr>
</tbody>
</table>

## <a name="create-labels-and-auto-apply-label-policies"></a><span data-ttu-id="89efe-224">创建标签和自动应用标签策略</span><span class="sxs-lookup"><span data-stu-id="89efe-224">Create labels and auto-apply label policies</span></span>

<span data-ttu-id="89efe-225">在安全与合规中心中创建标签和策略。</span><span class="sxs-lookup"><span data-stu-id="89efe-225">Create labels and policies in the Security & Compliance Center.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="89efe-226"><strong>步骤</strong></span><span class="sxs-lookup"><span data-stu-id="89efe-226"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="89efe-227"><strong>说明</strong></span><span class="sxs-lookup"><span data-stu-id="89efe-227"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="89efe-228">向合规性团队成员提供权限。</span><span class="sxs-lookup"><span data-stu-id="89efe-228">Give permissions to members of your compliance team.</span></span></p></td>
<td align="left"><p><span data-ttu-id="89efe-p123">创建标签的合规性团队成员需要使用安全与合规中心的权限。请转到安全与合规中心中的“权限”，然后修改符合性管理员组的成员。</span><span class="sxs-lookup"><span data-stu-id="89efe-p123">Members of your compliance team who will create labels need permissions to use the Security &amp; Compliance Center. Go to Permissions in Security and Compliance Center and modify the members of the Compliance Administrator group.</span></span></p>
<p><span data-ttu-id="89efe-231">请参阅<a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">向用户授予对 Office 365 安全与合规中心的访问权限</a>。</span><span class="sxs-lookup"><span data-stu-id="89efe-231">Give users access to the Office 365 Security & Compliance Center</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="89efe-232">创建 Office 标签。</span><span class="sxs-lookup"><span data-stu-id="89efe-232">Phase 3: Create Office 365 labels</span></span></p></td>
<td align="left"><span data-ttu-id="89efe-233">转到安全与合规中心中的“分类”，选择标签，然后为环境创建标签。</span><span class="sxs-lookup"><span data-stu-id="89efe-233">Go to Classifications in Security and Compliance Center, choose Labels, and create the labels for your environment.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="89efe-234">为标签创建自动应用策略。</span><span class="sxs-lookup"><span data-stu-id="89efe-234">Create auto-apply policies for labels.</span></span></p></td>
<td align="left"><span data-ttu-id="89efe-p124">转到安全与合规中心中的“分类”，选择“标签策略”，然后为自动应用标签创建策略。请务必按优先级顺序创建这些策略。</span><span class="sxs-lookup"><span data-stu-id="89efe-p124">Go to Classification in Security and Compliance Center, choose Label policies, and create the policies for auto-applying labels. Be sure to create these policies in the prioritized order.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="89efe-237">下图显示了如何为客户数据标签创建自动应用策略。</span><span class="sxs-lookup"><span data-stu-id="89efe-237">The following illustration shows how to create an auto-apply label for the Customer data label.</span></span>

![创建和应用客户数据标签](Media/Apply-labels-to-personal-data-in-Office-365-image3.png)

<span data-ttu-id="89efe-239">在此图中：</span><span class="sxs-lookup"><span data-stu-id="89efe-239">In the illustration:</span></span>

-   <span data-ttu-id="89efe-240">创建了“客户数据”标签。</span><span class="sxs-lookup"><span data-stu-id="89efe-240">The “Customer data” label is created.</span></span>

-   <span data-ttu-id="89efe-241">列出了针对 GDPR 的所需敏感信息类型：比利时国家/地区号码、信用卡号码、克罗地亚身份证号、芬兰国家/地区身份证号码。</span><span class="sxs-lookup"><span data-stu-id="89efe-241">The desired sensitive information types for GDPR are listed: Belgium National Number, Credit Card Number, Croatia Identity Card Number, Finland National ID.</span></span>

-   <span data-ttu-id="89efe-242">创建自动应用策略，将标签“客户数据”分配给包括添加到策略的敏感信息类型之一的任何文件。</span><span class="sxs-lookup"><span data-stu-id="89efe-242">Create an auto-apply policy assigns the label “Customer data” to any file that includes one of the sensitive information types that you add to the policy.</span></span>
