---
title: "为个人数据构建分类架构"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- GDPR
- Strat_O365_Enterprise
ms.assetid: 
description: "确定组织是否使用标签作为 GDPR 计划的一部分。"
ms.openlocfilehash: ee3c01cd4fd99fcc62bbde445eeb3018bb05f586
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="architect-a-classification-schema-for-personal-data"></a><span data-ttu-id="0594b-103">为个人数据构建分类架构</span><span class="sxs-lookup"><span data-stu-id="0594b-103">Architect a classification schema for personal data</span></span>

<span data-ttu-id="0594b-p101">本系列之前的文章重点介绍使用敏感信息类型识别符合 GDPR 的个人数据。敏感信息类型是一种分类形式。这可能是你需要的所有分类。但是，许多组织使用标签执行更广泛的数据管理策略。通过本主题来决定你是否也要使用标签作为 GDPR 计划的一部分。如果想要这样做，本主题提供了一些指导和示例。</span><span class="sxs-lookup"><span data-stu-id="0594b-p101">Previous articles in this series focus on using sensitive information types to identify personal data that is subject to GDPR. Sensitive information types are a form of classification. This might be all the classification you need. However, many organizations implement a broader data governance strategy using labels. Use this topic to decide if you also want to implement labels as part of your GDPR plan. If you do, this topic provides some guidance and examples.</span></span>

<span data-ttu-id="0594b-p102">注意：定义组织的分类架构和配置策略、标签和条件需要认真计划和精心准备。重要的是认识到这并不是一个 IT 驱动的流程。请务必与你的法律和合规团队协作，为组织的数据开发适当的分类和标签架构。</span><span class="sxs-lookup"><span data-stu-id="0594b-p102">Note: Defining a classification schema for an organization and configuring policies, labels, and conditions requires careful planning and preparation. It is important to realize that this is not an IT driven process. Be sure to work with your legal and compliance team to develop an appropriate classification and labeling schema for your organization’s data.</span></span>

## <a name="decide-if-you-are-using-labels-in-addition-to-sensitive-data-types"></a><span data-ttu-id="0594b-113">决定是否使用除敏感数据类型外的标签</span><span class="sxs-lookup"><span data-stu-id="0594b-113">Decide if you are using labels in addition to sensitive data types</span></span>

<span data-ttu-id="0594b-p103">可以在 Office 365 中为个人信息采用两种分类方法中的一种。这两种方法都可用于 GDPR 保护。如果决定仅使用敏感信息类型进行分类，可跳过本主题的剩余部分。</span><span class="sxs-lookup"><span data-stu-id="0594b-p103">You can take one of two approaches for classification in Office 365 for personal information. Either of these can be used for GDPR protection. If decide to use only sensitive information types for classification, you can skip the rest of this topic.</span></span>

<span data-ttu-id="0594b-117">选择下列选项之一。</span><span class="sxs-lookup"><span data-stu-id="0594b-117">Choose one of the following options</span></span>

### <a name="option-1-use-only-office-365-sensitive-information-types"></a><span data-ttu-id="0594b-118">选项 1：仅使用 Office 365 敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="0594b-118">Option 1: Use only Office 365 sensitive information types</span></span>

-   <span data-ttu-id="0594b-119">敏感信息类型可以有效地识别和保护符合 GDPR 和其他类型规定的个人数据。</span><span class="sxs-lookup"><span data-stu-id="0594b-119">Sensitive information types work well to identify and protect personal data subject to GDPR and other types of regulations.</span></span>

-   <span data-ttu-id="0594b-120">如果你的组织尚未使用或计划使用标签执行更广泛的数据管理计划，这些类型会更易于使用。</span><span class="sxs-lookup"><span data-stu-id="0594b-120">These are simpler to use if your organization doesn’t already have or plan to implement a broader data governance plan using labels.</span></span>

-   <span data-ttu-id="0594b-121">这些类型适用于 DLP 规则（Office 标签也是如此）。</span><span class="sxs-lookup"><span data-stu-id="0594b-121">These work with DLP rules (so do Office labels).</span></span>

-   <span data-ttu-id="0594b-122">今后，这些类型将可用于 Cloud App Security，因此可以检测其他 SaaS 应用中的敏感信息。</span><span class="sxs-lookup"><span data-stu-id="0594b-122">In the future these will work with Cloud App Security so you can detect sensitive information in other SaaS apps.</span></span>

### <a name="option-2-use-sensitive-information-types--office-labels"></a><span data-ttu-id="0594b-123">选项 2：使用敏感信息类型 + Office 标签</span><span class="sxs-lookup"><span data-stu-id="0594b-123">Option 2: Use sensitive information types + Office labels</span></span>

-   <span data-ttu-id="0594b-124">将需要敏感信息类型将标签自动应用到符合 GDPR 的个人数据，因此，这些敏感信息类型是先决条件。</span><span class="sxs-lookup"><span data-stu-id="0594b-124">You’ll need sensitive information types to automatically apply labels to personal data that is subject to GDPR, so these are a prerequisite.</span></span>

-   <span data-ttu-id="0594b-125">使用 Office 标签，可将符合 GDPR 的个人数据加入组织的更广泛数据管理计划。</span><span class="sxs-lookup"><span data-stu-id="0594b-125">Using Office labels allows you to include personal data that is subject to GDPR into a broader data governance plan for your organization.</span></span>

-   <span data-ttu-id="0594b-126">今后，Office 标签将与 Azure 信息保护标签整合为统一的分类和标记引擎。</span><span class="sxs-lookup"><span data-stu-id="0594b-126">Later, Office labels will converge with Azure Information Protection labels into a unified classification and labeling engine.</span></span>

## <a name="develop-a-label-schema-that-includes-personal-data"></a><span data-ttu-id="0594b-127">开发包含个人数据的标签架构</span><span class="sxs-lookup"><span data-stu-id="0594b-127">Develop a label schema that includes personal data</span></span>

<span data-ttu-id="0594b-p104">在使用技术功能应用标签和保护之前，首先在组织中定义分类架构。组织可能已具有分类架构，这样添加个人数据就会更加轻松。本主题包含一个示例分类架构。如有需要，可以从它入手。</span><span class="sxs-lookup"><span data-stu-id="0594b-p104">Before using technical capabilities to apply labels and protection, first work across your organization to define a classification schema. Your organization might already have a classification schema, which makes it easier to add personal data. This topic includes an example classification schema. You can use this as a starting point, if needed.</span></span>

### <a name="getting-started"></a><span data-ttu-id="0594b-132">开始使用</span><span class="sxs-lookup"><span data-stu-id="0594b-132">Getting started</span></span>

<span data-ttu-id="0594b-p105">首先决定要使用的标签数量和名称。执行此活动无需担心要使用的技术和应用标签的方式。在整个组织内普遍应用此架构，其中包括驻留在本地和其他云服务中的数据。</span><span class="sxs-lookup"><span data-stu-id="0594b-p105">Begin by deciding on the number and names of labels to implement. Do this activity without worrying about which technology to use and how labels will be applied. Apply this schema universally throughout your organization, including data that resides on premises and in other cloud services.</span></span>

### <a name="recommendations"></a><span data-ttu-id="0594b-136">建议</span><span class="sxs-lookup"><span data-stu-id="0594b-136">Recommendations</span></span> 

<span data-ttu-id="0594b-137">设计和执行策略、标签和条件时，请考虑以下这些建议：</span><span class="sxs-lookup"><span data-stu-id="0594b-137">When designing and implementing policies, labels and conditions, consider following these recommendations:</span></span>

-   <span data-ttu-id="0594b-p106">使用现有分类架构（如果有）— 许多组织已在使用某种形式的数据分类。仔细评估现有标签架构，如果可能，则直接使用。使用可被最终用户识别的常用标签将更易于采用。</span><span class="sxs-lookup"><span data-stu-id="0594b-p106">Use existing classification schema (if any) — Many organizations already are using data classification in some form. Carefully evaluate the existing label schema and if possible use it as is. Using familiar labels that are recognizable to the end-user will drive adoption.</span></span>

-   <span data-ttu-id="0594b-p107">从默认策略和标签开始 — 所有解决方案都具有一套预定义策略和标签。针对组织法律和业务要求对其进行仔细评估，并考虑使用它们来代替新建策略和标签。</span><span class="sxs-lookup"><span data-stu-id="0594b-p107">Start with default policies and labels — All solutions come with a set of predefined policies and labels. Carefully evaluate these against the organizations legal and business requirements and consider using them instead of creating new ones.</span></span>

-   <span data-ttu-id="0594b-p108">从较小的数量着手 — 实际上，对可创建的标签数量没有限制。但是，较大数量的标签和子标签将对采用情况产生负面影响。选择过多常常意味着根本没有选择。</span><span class="sxs-lookup"><span data-stu-id="0594b-p108">Start small — There is virtually no limit to the number of labels that can be created. However, large numbers of labels and sub-labels will negatively impact the adoption. Too many choices often means no choice at all.</span></span>

-   <span data-ttu-id="0594b-146">使用场景和用例 — 确定组织内的常见用例，并使用自 GDPR 派生的场景验证预想的标签和分配配置是否确实能起作用。</span><span class="sxs-lookup"><span data-stu-id="0594b-146">Use scenarios and use cases — Identify common use cases within the organization and use scenarios derived from the GDPR to verify if the envisioned label and classification configuration will work in practice.</span></span>

-   <span data-ttu-id="0594b-p109">质疑对新标签的每个请求，每个场景或用例是否确实需要新标签，是否可以使用已有的标签？将标签数量保持为最小值可提高采用度。</span><span class="sxs-lookup"><span data-stu-id="0594b-p109">Question every request for a new label, does every scenario or use case really need a new label or can we use what we already have? Keeping the number of labels to a minimum improves adoption.</span></span>

-   <span data-ttu-id="0594b-p110">将子标签用于关键部门，某些部门将具有需要特定标签的特定需求。将这些标签作为子标签定义到现有标签，并考虑使用被分配到用户组的范围策略而非全局策略。</span><span class="sxs-lookup"><span data-stu-id="0594b-p110">Use sub-labels for key departments, some departments will have specific needs that require specific labels. Define these labels as sub-labels to an existing label and consider using scoped policies that are assigned to user groups instead of globally.</span></span>

-   <span data-ttu-id="0594b-p111">考虑范围策略，以用户子集为目标的策略可以防止“标签过载”。范围策略可促使将角色或部门特定的（子）标签仅分配给为该特定部门工作的员工。</span><span class="sxs-lookup"><span data-stu-id="0594b-p111">Consider scoped policies, polices targeted at subsets of users will prevent "label overload". A scoped policy enables assigning role or department specific (sub-)labels to just employees that work for that specific department.</span></span>

-   <span data-ttu-id="0594b-p112">使用具有意义的标签名称，不建议使用专门术语、标准或缩写词作为标签名称。尝试使用能够引起最终用户共鸣的名称以提高采用度。与其使用 PII、PCI、HIPAA、LBI、MBI 和 HBI 等标签，不如考虑使用非业务、公开、常规、机密和高度机密等名称。</span><span class="sxs-lookup"><span data-stu-id="0594b-p112">Use meaningful label names, it is recommended not to use jargon, standards or acronyms as label names. Try to use names that resonate with the end user to improve adoption. Instead of using labels like PII, PCI, HIPAA, LBI, MBI and HBI consider names like Non-Business, Public, General, Confidential and Highly Confidential.</span></span>

### <a name="example-classification-schema"></a><span data-ttu-id="0594b-156">示例分类架构</span><span class="sxs-lookup"><span data-stu-id="0594b-156">Example classification schema</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="0594b-157"><strong>标签名称</strong></span><span class="sxs-lookup"><span data-stu-id="0594b-157"><strong>Label name</strong></span></span></th>
<th align="left"><span data-ttu-id="0594b-158"><strong>说明</strong></span><span class="sxs-lookup"><span data-stu-id="0594b-158"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="0594b-159">个人</span><span class="sxs-lookup"><span data-stu-id="0594b-159">Personal</span></span></td>
<td align="left"><span data-ttu-id="0594b-160">非业务数据，仅供个人使用。</span><span class="sxs-lookup"><span data-stu-id="0594b-160">Non-business data, for personal use only.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0594b-161">公开</span><span class="sxs-lookup"><span data-stu-id="0594b-161">Public</span></span></td>
<td align="left"><span data-ttu-id="0594b-162">专为公开使用准备和批准的业务数据。</span><span class="sxs-lookup"><span data-stu-id="0594b-162">Business data that is specifically prepared and approved for public consumption.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0594b-163">客户数据</span><span class="sxs-lookup"><span data-stu-id="0594b-163">Customer data</span></span></td>
<td align="left"><span data-ttu-id="0594b-p113">包含个人身份信息的业务数据。例如，信用卡卡号、银行账号和社会安全号码。</span><span class="sxs-lookup"><span data-stu-id="0594b-p113">Business data that contains personal identifiable information. Examples are credit card numbers, bank account numbers, and social security numbers.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0594b-166">HR 数据</span><span class="sxs-lookup"><span data-stu-id="0594b-166">HR data</span></span></td>
<td align="left"><span data-ttu-id="0594b-167">有关 Contoso 员工的人力资源数据，如员工号码和薪资数据。</span><span class="sxs-lookup"><span data-stu-id="0594b-167">Human Resource data about Contoso employees, such as employee number and salary data.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0594b-168">机密</span><span class="sxs-lookup"><span data-stu-id="0594b-168">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="0594b-p114">与未经授权的人员共享可能导致业务损失的敏感业务数据。示例包括合同、安全报表、预测摘要和销售帐户数据。</span><span class="sxs-lookup"><span data-stu-id="0594b-p114">Sensitive business data that could cause damage to the business if shared with unauthorized people. Examples include contracts, security reports, forecast summaries, and sales account data.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0594b-171">高度机密</span><span class="sxs-lookup"><span data-stu-id="0594b-171">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="0594b-p115">与未经授权的人员共享会导致业务损失的非常敏感业务数据。示例包括员工和客户信息、密码、源代码和预先公布的财务报表。</span><span class="sxs-lookup"><span data-stu-id="0594b-p115">Very sensitive business data that would cause damage to the business if it was shared with unauthorized people. Examples include employee and customer information, passwords, source code, and pre-announced financial reports.</span></span></td>
</tr>
</tbody>
</table>

## <a name="define-a-taxonomy-and-search-criteria-for-each-label"></a><span data-ttu-id="0594b-174">定义每个标签的分类和搜索条件</span><span class="sxs-lookup"><span data-stu-id="0594b-174">Define a taxonomy and search criteria for each label</span></span>

<span data-ttu-id="0594b-p116">为组织开发分类架构后，下一步是开发用于查找此数据的分类和搜索条件。对于个人数据，你已经通过识别敏感信息类型，已经自定义或新建环境的敏感信息类型完成了此项工作。</span><span class="sxs-lookup"><span data-stu-id="0594b-p116">After developing a classification schema for your organization, the next step is to develop the taxonomy and search criteria for finding this data. For personal data, you’ve already completed this work by identifying sensitive information types and also by customizing or creating new sensitive information types for your environment.</span></span>

<span data-ttu-id="0594b-p117">下表提供了组织的示例架构、分类和搜索条件。按照敏感级别从最不敏感到最敏感对标签进行排序，确保将匹配多个标签条件的数据分配到相应的标签。</span><span class="sxs-lookup"><span data-stu-id="0594b-p117">The following table provides an example schema, taxonomy, and search criteria for an organization. The labels are ordered by sensitivity level from least sensitive to most sensitive to ensure that data that matches multiple label conditions is assigned the appropriate label.</span></span>

<span data-ttu-id="0594b-179">注意：配置示例仅作演示之用，并不能作为部署指导或参考。</span><span class="sxs-lookup"><span data-stu-id="0594b-179">Note: The configuration example is provided for illustration only and is not intended as deployment guidance or reference.</span></span>

<span data-ttu-id="0594b-180">主要宗旨在于确保你为遵循 GDPR 符合性而进行的个人数据分类工作与整个组织的目标相契合。</span><span class="sxs-lookup"><span data-stu-id="0594b-180">The important takeaway is to ensure that the work you invest to classify personal data for GDPR compliance fits together with the objectives for your entire organization.</span></span>

### <a name="example-schema-taxonomy-and-search-criteria"></a><span data-ttu-id="0594b-181">示例架构、分类和搜索条件</span><span class="sxs-lookup"><span data-stu-id="0594b-181">Example schema, taxonomy, and search criteria</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="0594b-182"><strong>标签</strong></span><span class="sxs-lookup"><span data-stu-id="0594b-182"><strong>label</strong></span></span></th>
<th align="left"><span data-ttu-id="0594b-183"><strong>分类</strong></span><span class="sxs-lookup"><span data-stu-id="0594b-183"><strong>Taxonomy</strong></span></span></th>
<th align="left"><span data-ttu-id="0594b-184"><strong>方法</strong></span><span class="sxs-lookup"><span data-stu-id="0594b-184"><strong>method</strong></span></span></th>
<th align="left"><span data-ttu-id="0594b-185"><strong>搜索语句</strong></span><span class="sxs-lookup"><span data-stu-id="0594b-185"><strong>Search syntax</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="0594b-186">个人</span><span class="sxs-lookup"><span data-stu-id="0594b-186">Personal</span></span></td>
<td align="left"><span data-ttu-id="0594b-187">由最终用户手动标记为“个人”的文档。</span><span class="sxs-lookup"><span data-stu-id="0594b-187">Documents manually labelled personal by the end user.</span></span></td>
<td align="left"><span data-ttu-id="0594b-188">手动</span><span class="sxs-lookup"><span data-stu-id="0594b-188">Manual</span></span></td>
<td align="left"><span data-ttu-id="0594b-189">由最终用户手动标记为“个人”的文档。</span><span class="sxs-lookup"><span data-stu-id="0594b-189">Documents manually labelled personal by the end user.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0594b-190">公开</span><span class="sxs-lookup"><span data-stu-id="0594b-190">Public</span></span></td>
<td align="left"><span data-ttu-id="0594b-191">包含区分大小写的短语“Approved for Public Release ##/####”（其中 # 表示任意数字）的文档。</span><span class="sxs-lookup"><span data-stu-id="0594b-191">Documents containing the case insensitive phrase Approved for Public Release ##/#### where # represents any digit.</span></span></td>
<td align="left"><p><span data-ttu-id="0594b-192">KQL</span><span class="sxs-lookup"><span data-stu-id="0594b-192">KQL</span></span></p>
<p><span data-ttu-id="0594b-193">RegEx</span><span class="sxs-lookup"><span data-stu-id="0594b-193">Regex</span></span></p></td>
<td align="left"><p><span data-ttu-id="0594b-194">KQL — Approved for Public Release\*</span><span class="sxs-lookup"><span data-stu-id="0594b-194">KQL — Approved for Public Release\*</span></span></p>
<p><span data-ttu-id="0594b-195">RegEx — (?i)(\bApproved for Public Release \d{2}\/\d{4}\b)</span><span class="sxs-lookup"><span data-stu-id="0594b-195">RegEx — (?i)(\bApproved for Public Release \d{2}\/\d{4}\b)</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0594b-196">客户数据</span><span class="sxs-lookup"><span data-stu-id="0594b-196">Customer data</span></span></td>
<td align="left"><span data-ttu-id="0594b-197">欧盟公民数据的敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="0594b-197">Sensitive information types for EU citizen data.</span></span></td>
<td align="left"><span data-ttu-id="0594b-198">敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="0594b-198">Sensitive information types</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0594b-199">人力资源 — 员工数据</span><span class="sxs-lookup"><span data-stu-id="0594b-199">Human Resources — Employee Data</span></span></td>
<td align="left"><span data-ttu-id="0594b-200">包含采用 CONTOSO-9##### 格式（其中 # 表示任意数字）的区分大小写的员工 ID 的文档。</span><span class="sxs-lookup"><span data-stu-id="0594b-200">Documents that include the case sensitive employee id in the format CONTOSO-9##### where # represents any digit.</span></span></td>
<td align="left"><p><span data-ttu-id="0594b-201">KQL</span><span class="sxs-lookup"><span data-stu-id="0594b-201">KQL</span></span></p>
<p><span data-ttu-id="0594b-202">RegEx</span><span class="sxs-lookup"><span data-stu-id="0594b-202">Regex</span></span></p></td>
<td align="left"><p><span data-ttu-id="0594b-203">KQL — CONTOSO-9\*</span><span class="sxs-lookup"><span data-stu-id="0594b-203">KQL — CONTOSO-9\*</span></span></p>
<p><span data-ttu-id="0594b-204">RegEx — (\bCONTOSO-9\d{5}\b)</span><span class="sxs-lookup"><span data-stu-id="0594b-204">RegEx — (\bCONTOSO-9\d{5}\b)</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0594b-205">人力资源 — 薪资数据</span><span class="sxs-lookup"><span data-stu-id="0594b-205">Human Resources — Salary Data</span></span></td>
<td align="left"><span data-ttu-id="0594b-206">包含关键字（不区分大小写）“Contoso AND”或关键字（不区分大小写）“Salary OR Compensation”的文档</span><span class="sxs-lookup"><span data-stu-id="0594b-206">Documents that include the keyword (not case sensitive) Contoso AND either keyword (not case sensitive) Salary OR Compensation</span></span></td>
<td align="left"><p><span data-ttu-id="0594b-207">KQL</span><span class="sxs-lookup"><span data-stu-id="0594b-207">KQL</span></span></p>
<p><span data-ttu-id="0594b-208">RegEx</span><span class="sxs-lookup"><span data-stu-id="0594b-208">Regex</span></span></p></td>
<td align="left"><p><span data-ttu-id="0594b-209">KQL — Contoso AND (Salary OR Compensation)</span><span class="sxs-lookup"><span data-stu-id="0594b-209">KQL — Contoso AND (Salary OR Compensation)</span></span></p>
<p><span data-ttu-id="0594b-210">RegEx — (\bCONTOSO-9\d{5}\b)</span><span class="sxs-lookup"><span data-stu-id="0594b-210">RegEx — (\bCONTOSO-9\d{5}\b)</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0594b-211">机密</span><span class="sxs-lookup"><span data-stu-id="0594b-211">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="0594b-212">包含短语（不区分大小写）“Contoso Confidential”的文档。</span><span class="sxs-lookup"><span data-stu-id="0594b-212">Documents containing the phrase (not case sensitive) Contoso Confidential.</span></span></td>
<td align="left"><p><span data-ttu-id="0594b-213">KQL</span><span class="sxs-lookup"><span data-stu-id="0594b-213">KQL</span></span></p>
<p><span data-ttu-id="0594b-214">RegEx</span><span class="sxs-lookup"><span data-stu-id="0594b-214">Regex</span></span></p></td>
<td align="left"><p><span data-ttu-id="0594b-215">KQL — Contoso Confidential</span><span class="sxs-lookup"><span data-stu-id="0594b-215">KQL — Contoso Confidential</span></span></p>
<p><span data-ttu-id="0594b-216">RegEx — (?i)(\bContoso Confidential\b)</span><span class="sxs-lookup"><span data-stu-id="0594b-216">RegEx — (?i)(\bContoso Confidential\b)</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0594b-217">高度机密</span><span class="sxs-lookup"><span data-stu-id="0594b-217">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="0594b-218">包含短语（不区分大小写）“Contoso Secret”或“Secret-C####”（其中 # 表示任意数字）的文档。</span><span class="sxs-lookup"><span data-stu-id="0594b-218">Documents that include either pharase (case sensitive) Contoso Secret or Secret-C#### where # represents any digit.</span></span></td>
<td align="left"><p><span data-ttu-id="0594b-219">KQL</span><span class="sxs-lookup"><span data-stu-id="0594b-219">KQL</span></span></p>
<p><span data-ttu-id="0594b-220">RegEx</span><span class="sxs-lookup"><span data-stu-id="0594b-220">Regex</span></span></p></td>
<td align="left"><p><span data-ttu-id="0594b-221">KQL — Contoso Secret OR Secret-C\*</span><span class="sxs-lookup"><span data-stu-id="0594b-221">KQL — Contoso Secret OR Secret-C\*</span></span></p>
<p><span data-ttu-id="0594b-222">RegEx — (?i)(\bContoso Secret\b)|(\bSecret-C\d{4}\b)</span><span class="sxs-lookup"><span data-stu-id="0594b-222">RegEx — (?i)(\bContoso Secret\b)|(\bSecret-C\d{4}\b)</span></span></p></td>
</tr>
</tbody>
</table>
