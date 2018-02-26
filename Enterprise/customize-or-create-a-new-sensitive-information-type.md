---
title: "自定义或新建敏感信息类型"
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
description: "了解如何修改或新建针对 GDPR 的 Office 365 敏感信息类型。"
ms.openlocfilehash: 58bfce19d75a66fe36d3e61ec0b05bcca6913b85
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="customize-or-create-a-new-sensitive-information-type"></a><span data-ttu-id="52539-103">自定义或新建敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="52539-103">Customize or create a new sensitive information type</span></span>

<span data-ttu-id="52539-104">本文提供了三个示例，说明如何修改或新建针对 GDPR 的 Office 365 敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="52539-104">This article provides three examples to demonstrate how to modify or create new Office 365 sensitive information types for GDPR.</span></span>

-   <span data-ttu-id="52539-105">修改现有的敏感信息类型 — 欧盟借记卡号</span><span class="sxs-lookup"><span data-stu-id="52539-105">Modify an existing sensitive information type — EU Debit Card Number</span></span>

-   <span data-ttu-id="52539-106">新建敏感信息类型 — 电子邮件地址</span><span class="sxs-lookup"><span data-stu-id="52539-106">Create a new sensitive information type — email address</span></span>

-   <span data-ttu-id="52539-107">使用示例 XML 文件新建敏感信息类型 — Contoso 客户编号</span><span class="sxs-lookup"><span data-stu-id="52539-107">Create a new sensitive information type with example XML file — Contoso customer number</span></span>

<span data-ttu-id="52539-108">另请参阅：</span><span class="sxs-lookup"><span data-stu-id="52539-108">Also see:</span></span>

-   [<span data-ttu-id="52539-109">创建自定义敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="52539-109">Create a custom sensitive information type</span></span>](https://support.office.com/zh-CN/article/Create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30)

-   [<span data-ttu-id="52539-110">自定义内置敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="52539-110">Customize a built-in sensitive information type </span></span>](https://support.office.com/zh-CN/article/Customize-a-built-in-sensitive-information-type-2164ce3d-4d64-4283-b6b1-b81fbe835e8e)

## <a name="modify-a-sensitive-information-type-to-improve-accuracy"></a><span data-ttu-id="52539-111">修改敏感信息类型以提高准确性</span><span class="sxs-lookup"><span data-stu-id="52539-111">Modify a sensitive information type to improve accuracy</span></span>

<span data-ttu-id="52539-112">使用敏感信息类型通过内容搜索来搜索个人数据时，如果未返回预期结果，或者查询返回的误报过多，请考虑修改敏感信息类型，使其更适用于自己的环境。</span><span class="sxs-lookup"><span data-stu-id="52539-112">If you’re using Content Search to search for personal data using sensitive information types and you’re not returning the expected results, or the query returns too many false positives, consider modifying the sensitive information type to work better with your environment.</span></span>

<span data-ttu-id="52539-p101">创建或自定义敏感信息类型的最佳做法是基于现有的类型新建敏感信息类型，并为其提供一个唯一的名称和标识符。例如，如果要调整“欧盟借记卡号”敏感信息类型的参数，可以将该规则的副本命名为“欧盟借记卡增强版”，方便与原始名称进行区分。</span><span class="sxs-lookup"><span data-stu-id="52539-p101">The best practice when creating or customizing a sensitive information type is to create a new sensitive information type based on an existing one, giving it a unique name and identifiers. For example, if you wish to adjust the parameters of the “EU Debit Card Number” sensitive information type, you could name your copy of that rule “EU Debit Card Enhanced” to distinguish it from the original.</span></span>

<span data-ttu-id="52539-p102">在新的敏感信息类型中，仅修改为提高其准确性而需更改的值。完成后，上传新的敏感信息类型，创建新的 DLP 规则（或修改现有的规则），以便使用刚添加的新敏感信息类型。修改敏感信息类型的准确性可能需要反复试验，因此请保留原始类型的副本，这样以后如有必要，则可重新修改它。</span><span class="sxs-lookup"><span data-stu-id="52539-p102">In your new sensitive information type, simply modify the values you wish to change to improve its accuracy. Once complete, upload your new sensitive information type and create a new DLP rule (or modify an existing one) to use the new sensitive information type you just added. Modifying the accuracy of sensitive information types might require some trial and error, so maintaining a copy of the original type allows you to fall back to it if required in the future.</span></span>

<span data-ttu-id="52539-118">自定义敏感信息类型：</span><span class="sxs-lookup"><span data-stu-id="52539-118">To customize a sensitive information type:</span></span>

1.  <span data-ttu-id="52539-119">导出包含 Office 365 中的内置敏感信息类型的现有 Microsoft 规则包。</span><span class="sxs-lookup"><span data-stu-id="52539-119">Export the existing Microsoft Rule Package of built in sensitive information types in Office 365.</span></span>

2.  <span data-ttu-id="52539-120">将此 XML 文件重命名，在自己喜爱的 XML 编辑器中打开它。</span><span class="sxs-lookup"><span data-stu-id="52539-120">Rename this XML file and open it in your favorite XML editor.</span></span>

3.  <span data-ttu-id="52539-121">隔离相应的敏感信息类型，并删除所有其他的类型。</span><span class="sxs-lookup"><span data-stu-id="52539-121">Isolate the sensitive information type and remove all others.</span></span>

4.  <span data-ttu-id="52539-122">使用 PowerShell 为正在修改的敏感信息类型生成两个新的 GUID。</span><span class="sxs-lookup"><span data-stu-id="52539-122">Use PowerShell to generate two new GUIDs for the sensitive information type you are modifying.</span></span>

5.  <span data-ttu-id="52539-123">修改 ID 和其他基本元素，使此敏感信息类型成为唯一的类型（此过程包括将两个 GUID 替换为已生成的新 GUID）。</span><span class="sxs-lookup"><span data-stu-id="52539-123">Modify the ID and other basic elements so the sensitive information type is unique (this includes replacing two GUIDs with the new ones you generated).</span></span>

6.  <span data-ttu-id="52539-124">微调匹配要求以提高准确性。</span><span class="sxs-lookup"><span data-stu-id="52539-124">Tune the match requirements to improve accuracy.</span></span>

    1.  <span data-ttu-id="52539-125">邻近性修改 — 修改字符模式邻近性，以扩大或缩小必须要围绕该敏感信息类型在其中查找关键字的范围。</span><span class="sxs-lookup"><span data-stu-id="52539-125">Proximity modifications — Modify the character pattern proximity to expand or shrink the window in which keywords must be found around the sensitive information type.</span></span>

    2.  <span data-ttu-id="52539-p103">关键字修改 — 向 \<Keywords\> 元素之一添加关键字，为敏感信息类型提供要搜索的更为具体的佐证，以便指示与此规则相匹配。或删除导致误报的关键字。</span><span class="sxs-lookup"><span data-stu-id="52539-p103">Keyword modifications — Add keywords to one of the \<Keywords\> element in order to provide our sensitive information type more specific corroborative evidence to search for in order to signal a match on this rule. Or remove keywords that are causing false positives.</span></span>

    3.  <span data-ttu-id="52539-128">置信度修改 — 修改指示和报告匹配前敏感信息类型必须与定义中指定的条件达到的匹配置信度。</span><span class="sxs-lookup"><span data-stu-id="52539-128">Confidence modifications — Modify the confidence with which the sensitive information type must match the criteria specified in its definition before a match is signaled and reported.</span></span>

7.  <span data-ttu-id="52539-129">上传新的敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="52539-129">Upload the new sensitive information type.</span></span>

8.  <span data-ttu-id="52539-p104">重新对内容进行爬网，找出敏感信息。请参阅[手动请求对网站进行爬网和重新编制其索引](https://support.office.com/zh-CN/article/Manually-request-crawling-and-re-indexing-of-a-site-a-library-or-a-list-9AFA977D-39DE-4321-B4CA-8C7C7E6D264E)。</span><span class="sxs-lookup"><span data-stu-id="52539-p104">Recrawl your content to identify the sensitive information. See [Manually request crawling and re-indexing of a site](https://support.office.com/zh-CN/article/Manually-request-crawling-and-re-indexing-of-a-site-a-library-or-a-list-9AFA977D-39DE-4321-B4CA-8C7C7E6D264E).</span></span>

## <a name="example-modify-the-eu-debit-card-number-sensitive-information-type"></a><span data-ttu-id="52539-132">示例：修改“欧盟借记卡号”敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="52539-132">Example: modify the ‘EU Debit Card Number’ sensitive information type</span></span>

<span data-ttu-id="52539-p105">提高 DLP 规则在任意系统中的准确性需要在示例数据集上进行测试，并且可能需要通过反复修改和测试来进行微调。此示例演示了为提高准确性而对“欧盟借记卡号”敏感信息类型进行的修改。</span><span class="sxs-lookup"><span data-stu-id="52539-p105">Improving the accuracy of DLP rules in any system requires testing against a sample data set, and may require fine tuning through repetitive modifications and tests. This example demonstrates modifications to the ‘EU Debit Card Number’ sensitive information type to improve its accuracy.</span></span>

<span data-ttu-id="52539-p106">在本示例中，搜索欧盟借记卡号时，该卡号的定义已严格定义为使用复杂模式且经过校验和验证的 16 位数字。由于此敏感信息类型的字符串定义，我们无法改变此模式。但我们可以做出以下调整，从而提高 Office 365 DLP 在 Office 365 内查找此敏感信息类型所使用的方式的准确性。</span><span class="sxs-lookup"><span data-stu-id="52539-p106">When searching for an EU Debit Card Number in our example, the definition of that number is strictly defined as 16 digits using a complex pattern, and being subject to the validation of a checksum. We cannot alter this pattern due to the string definition of this sensitive information type. However, we can make the following adjustments to improve the accuracy of how Office 365 DLP finds this sensitive information type within Office 365.</span></span>

### <a name="proximity-modification"></a><span data-ttu-id="52539-138">邻近度修改</span><span class="sxs-lookup"><span data-stu-id="52539-138">Proximity modification</span></span>

<span data-ttu-id="52539-p107">通过修改 \<Entity\> 元素中的 patternProximity 值（从 300 个字符修改为 150 个字符）来缩小范围。这表示佐证（关键字）必须较接近敏感信息类型才能指示与此规则相匹配。</span><span class="sxs-lookup"><span data-stu-id="52539-p107">We'll shrink the window by modifying the patternProximity value in our \<Entity\> element from 300 to 150 characters. This means that our corroborative evidence, or our keywords, must be closer to our sensitive information type in order to signal a match on this rule.</span></span>

<span data-ttu-id="52539-141">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span><span class="sxs-lookup"><span data-stu-id="52539-141">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span></span>

### <a name="keyword-modifications"></a><span data-ttu-id="52539-142">关键字修改</span><span class="sxs-lookup"><span data-stu-id="52539-142">Keyword modifications</span></span>

<span data-ttu-id="52539-p108">一些关键字可能会导致误报。因此可能需要删除关键字。以下是本示例的关键字：</span><span class="sxs-lookup"><span data-stu-id="52539-p108">Some keywords might cause false positives to occur. As a result you might want to remove keywords. Here are the keywords for this example::</span></span>

<span data-ttu-id="52539-146">\<Keyword id="Keyword\_card\_terms\_dict"\></span><span class="sxs-lookup"><span data-stu-id="52539-146">\<Keyword id="Keyword\_card\_terms\_dict"\></span></span>

<span data-ttu-id="52539-147">\<Group\></span><span class="sxs-lookup"><span data-stu-id="52539-147">group</span></span>

<span data-ttu-id="52539-148">\<Term\>corporate card\</Term\></span><span class="sxs-lookup"><span data-stu-id="52539-148">\<Term\>corporate card\</Term\></span></span>

<span data-ttu-id="52539-149">\<Term\>organization card\</Term\></span><span class="sxs-lookup"><span data-stu-id="52539-149">\<Term\>organization card\</Term\></span></span>

<span data-ttu-id="52539-150">\<Term\>acct nbr\</Term\></span><span class="sxs-lookup"><span data-stu-id="52539-150">\<Term\>acct nbr\</Term\></span></span>

<span data-ttu-id="52539-151">\<Term\>acct num\</Term\></span><span class="sxs-lookup"><span data-stu-id="52539-151">\<Term\>acct num\</Term\></span></span>

<span data-ttu-id="52539-152">\<Term\>acct no\</Term\></span><span class="sxs-lookup"><span data-stu-id="52539-152">\<Term\>acct no\</Term\></span></span>

<span data-ttu-id="52539-153">…</span><span class="sxs-lookup"><span data-stu-id="52539-153"></span></span>

<span data-ttu-id="52539-154">\</Group\></span><span class="sxs-lookup"><span data-stu-id="52539-154">group</span></span>

<span data-ttu-id="52539-155">\</Keyword\></span><span class="sxs-lookup"><span data-stu-id="52539-155">\</Keyword\></span></span>

### <a name="confidence-modifications"></a><span data-ttu-id="52539-156">置信度修改</span><span class="sxs-lookup"><span data-stu-id="52539-156">Confidence modifications</span></span>

<span data-ttu-id="52539-p109">如果从定义中删除关键字，通常是想通过减小此值来调整找到该敏感信息类型的置信度。欧盟借记卡号类型的默认级别为 85。</span><span class="sxs-lookup"><span data-stu-id="52539-p109">If you remove keywords from the definition, you would typically want to adjust how confident you are that this sensitive information type was found by lowering this value. The default level for EU Debit Card Number type is 85.</span></span>

<span data-ttu-id="52539-159">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span><span class="sxs-lookup"><span data-stu-id="52539-159">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span></span>

<span data-ttu-id="52539-160">\<Pattern confidenceLevel="85"\></span><span class="sxs-lookup"><span data-stu-id="52539-160">\<Pattern confidenceLevel="85"\></span></span>

<span data-ttu-id="52539-161">…</span><span class="sxs-lookup"><span data-stu-id="52539-161"></span></span>

<span data-ttu-id="52539-162">\</Pattern\></span><span class="sxs-lookup"><span data-stu-id="52539-162">pattern</span></span>

<span data-ttu-id="52539-163">\</Entity\></span><span class="sxs-lookup"><span data-stu-id="52539-163">entity</span></span>

## <a name="create-a-new-custom-sensitive-information-type"></a><span data-ttu-id="52539-164">创建新的自定义敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="52539-164">Create a new custom sensitive information type</span></span>

<span data-ttu-id="52539-165">若要创建新的自定义敏感信息类型，可以首先使用内容搜索完成以下操作：</span><span class="sxs-lookup"><span data-stu-id="52539-165">To create a new custom sensitive information type, start by using Content Search to:</span></span>

-   <span data-ttu-id="52539-166">优化 KQL 查询</span><span class="sxs-lookup"><span data-stu-id="52539-166">Optimize a KQL query</span></span>

-   <span data-ttu-id="52539-167">查看哪些关键字最有用</span><span class="sxs-lookup"><span data-stu-id="52539-167">See which keywords are most useful</span></span>

<span data-ttu-id="52539-p110">使用上述结果创建新的敏感信息类型。然后针对环境优化新的敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="52539-p110">Use these results to create a new sensitive information type. Then optimize the new sensitive information type for your environment.</span></span>

<span data-ttu-id="52539-p111">注意：即将推出大量适用于欧盟国家/地区的个人数据的新敏感信息类型。如需创建新的敏感信息类型，请首先将目标定位到所在环境的自定义数据。</span><span class="sxs-lookup"><span data-stu-id="52539-p111">Note: Many new sensitive information types are coming soon for personal data in EU countries. If you need to create new sensitive information types, begin by targeting data that is custom to your environment.</span></span>

### <a name="step-1--use-kql-queries-and-key-words-to-find-additional-data-in-your-environment"></a><span data-ttu-id="52539-172">步骤 1 — 使用 KQL 查询和关键字查找环境中的其他数据</span><span class="sxs-lookup"><span data-stu-id="52539-172">Step 1 — Use KQL queries and key words to find additional data in your environment</span></span>

<span data-ttu-id="52539-p112">可能需要创建其他查询来查找受 GDPR 制约的个人数据。内容搜索使用关键字查询语言 (KQL) 来查找数据。如果仅使用 KQL 而不使用敏感信息类型，大部分敏感数据都无法被准确地检测到。因此，此时的目标是使用内容搜索测试和优化 KQL 字符串，然后使用它们创建和微调新的敏感信息类型，进而提高准确性。</span><span class="sxs-lookup"><span data-stu-id="52539-p112">You might need to create additional queries to find personal data that is subject to GDPR. Content Search uses Keyword Query Language (KQL) to find data. Most sensitive data can’t be accurately detected using just KQL without sensitive information types. So the goal is to test and optimize KQL strings using Content Search and then use these to create and tune new sensitive information types where you can achieve even greater accuracy.</span></span>

<span data-ttu-id="52539-177">使用以下资源通过 KQL 构建和优化查询：</span><span class="sxs-lookup"><span data-stu-id="52539-177">Use these resources to formulate and optimize queries using KQL:</span></span>

-   [<span data-ttu-id="52539-178">关键字查询语言 (KQL) 语法参考 (DMC)</span><span class="sxs-lookup"><span data-stu-id="52539-178">Keyword Query Language (KQL) syntax reference (DMC)</span></span>](https://docs.microsoft.com/zh-CN/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

-   [<span data-ttu-id="52539-179">在 Office 365 安全与合规中心运行内容搜索</span><span class="sxs-lookup"><span data-stu-id="52539-179">Run a Content Search in the Office 365 Security &amp; Compliance Center</span></span>](https://support.office.com/zh-CN/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) 

<span data-ttu-id="52539-p113">内容搜索提供了可帮助开发 KQL 查询和敏感信息类型的其他资源 — 关键字。为什么要使用关键字列表？因为这样可以获取显示与各个关键字相匹配的项目数的统计信息。该信息有助于快速找到最有效（及最无效）的关键字。有关搜索统计信息的详细信息，请参阅[查看内容搜索结果的关键字统计信息](https://support.office.com/zh-CN/article/View-keyword-statistics-for-Content-Search-results-9701a024-c52e-43f0-b545-9a53478aec04)。</span><span class="sxs-lookup"><span data-stu-id="52539-p113">Content Search provides another resource to help you develop KQL queries and sensitive information types — keywords. Why use the keyword list? You can get statistics that show how many items match each keyword. This can help you quickly identify which keywords are the most (and least) effective. For more information about search statistics, see [View keyword statistics for Content Search results](https://support.office.com/zh-CN/article/View-keyword-statistics-for-Content-Search-results-9701a024-c52e-43f0-b545-9a53478aec04).</span></span>

<span data-ttu-id="52539-p114">所创建的搜索查询中各行上的关键字通过 OR 运算符连接。也可以在行中使用关键字短语（用括号括起来）。</span><span class="sxs-lookup"><span data-stu-id="52539-p114">Keywords on each row are connected by the OR operator in the search query that's created. You can also use a keyword phrase (surrounded by parentheses) in a row.</span></span>

<span data-ttu-id="52539-187">有关详细信息，请参阅[内容搜索的关键字查询和搜索条件](https://support.office.com/zh-CN/article/Keyword-queries-and-search-conditions-for-Content-Search-c4639c2e-7223-4302-8e0d-b6e10f1c3be3)。</span><span class="sxs-lookup"><span data-stu-id="52539-187">For more information about creating a search query and using conditions, see [Keyword queries for Content Search](https://support.office.com/zh-CN/article/Keyword-queries-and-search-conditions-for-Content-Search-c4639c2e-7223-4302-8e0d-b6e10f1c3be3).</span></span>

### <a name="exampleusing-content-search-to-identify-email-addresses"></a><span data-ttu-id="52539-188">示例 — 使用内容搜索找出电子邮件地址</span><span class="sxs-lookup"><span data-stu-id="52539-188">Example—Using Content Search to identify email addresses</span></span>

<span data-ttu-id="52539-p115">电子邮件地址被视为与数据主体相关的敏感信息。该简单示例演示了内容搜索如何发挥作用。</span><span class="sxs-lookup"><span data-stu-id="52539-p115">Email addresses are considered sensitive information related to data subjects. This is a simple example to demonstrate how Content Search can help.</span></span>

<span data-ttu-id="52539-p116">不能同时使用 KQL 和关键字。单独使用这些工具来筛选出查询，并确定可能会对敏感信息类型有帮助的关键字。</span><span class="sxs-lookup"><span data-stu-id="52539-p116">KQL and keywords can’t be used together. Use these tools separately to hone your query and determine keywords that might be useful in sensitive information types.</span></span>

### <a name="kql-query"></a><span data-ttu-id="52539-193">KQL 查询</span><span class="sxs-lookup"><span data-stu-id="52539-193">KQL query</span></span>

<span data-ttu-id="52539-194">(^|\\b)([a-zA-Z0-9\_\\-\\.]+)@([a-zA-Z0-9\_\\-\\.]+)\\.([a-zA-Z]{2,5})($|\\b)</span><span class="sxs-lookup"><span data-stu-id="52539-194">(^|\\b)([a-zA-Z0-9\_\\-\\.]+)@([a-zA-Z0-9\_\\-\\.]+)\\.([a-zA-Z]{2,5})($|\\b)</span></span>

<span data-ttu-id="52539-195">注意：</span><span class="sxs-lookup"><span data-stu-id="52539-195">Notes:</span></span>

-   <span data-ttu-id="52539-196">可以使用 NEAR 和 ONEAR 进行邻近度搜索。</span><span class="sxs-lookup"><span data-stu-id="52539-196">You can use NEAR and ONEAR for proximity searches.</span></span>

-   <span data-ttu-id="52539-197">但是，KQL 不支持含 Regex 类的查询（例如：IdRef="Regex\_email\_address"）</span><span class="sxs-lookup"><span data-stu-id="52539-197">Unfortunately, KQL doesn’t support queries with the Regex Class (ex: IdRef="Regex\_email\_address")</span></span>

### <a name="keywords"></a><span data-ttu-id="52539-198">关键字</span><span class="sxs-lookup"><span data-stu-id="52539-198">Keywords</span></span>

<span data-ttu-id="52539-p117">在单独的行上输入各个关键字。关键字示例：</span><span class="sxs-lookup"><span data-stu-id="52539-p117">Enter each keyword on a separate line. Example keywords:</span></span>

-   <span data-ttu-id="52539-201">email address</span><span class="sxs-lookup"><span data-stu-id="52539-201">Email address</span></span>

-   <span data-ttu-id="52539-202">mail</span><span class="sxs-lookup"><span data-stu-id="52539-202">mail</span></span>

-   <span data-ttu-id="52539-203">contact</span><span class="sxs-lookup"><span data-stu-id="52539-203">contact</span></span>

-   <span data-ttu-id="52539-204">sender</span><span class="sxs-lookup"><span data-stu-id="52539-204">Sender</span></span>

-   <span data-ttu-id="52539-205">recipient</span><span class="sxs-lookup"><span data-stu-id="52539-205">Recipient</span></span>

-   <span data-ttu-id="52539-206">cc</span><span class="sxs-lookup"><span data-stu-id="52539-206">Cc</span></span>

-   <span data-ttu-id="52539-207">bcc</span><span class="sxs-lookup"><span data-stu-id="52539-207">Bcc</span></span>

<span data-ttu-id="52539-208">在本示例中可能会发现，关键字并非必要，并且会生成许多误报结果。</span><span class="sxs-lookup"><span data-stu-id="52539-208">In this example, you might learn the keywords are not necessary and produce a lot of false positive results.</span></span>

### <a name="step-2--create-a-new-custom-sensitive-information-type"></a><span data-ttu-id="52539-209">步骤 2 — 创建新的自定义敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="52539-209">Step 2 — Create a new custom sensitive information type</span></span>

<span data-ttu-id="52539-p118">使用 KQL 查询和关键字找出敏感信息后，使用它们创建新的自定义敏感信息类型。在许多情况下，需要敏感信息类型达到一定的复杂度才能获得所需的准确度。然后可以在 DLP 策略和其他工具及其他 KQL 查询中结合使用这些自定义敏感信息类型和内容搜索。</span><span class="sxs-lookup"><span data-stu-id="52539-p118">After using KQL queries and keywords to identify sensitive information, use these to create new custom sensitive information types. In many cases, you’ll require the sophistication of sensitive information types to achieve the right level of accuracy. You can then use these custom sensitive information types with Content Search, in DLP policies and other tools, and within other KQL queries.</span></span>

<span data-ttu-id="52539-p119">最佳做法是基于现有的类型创建新的敏感信息类型。请使用本文前面部分所述的同一过程。</span><span class="sxs-lookup"><span data-stu-id="52539-p119">The best practice is to create a new sensitive information type based on an existing one. Use the same process described earlier in this article.</span></span>

### <a name="example--create-a-new-sensitive-information-for-email-addresses"></a><span data-ttu-id="52539-215">示例 — 为电子邮件地址创建新的敏感信息</span><span class="sxs-lookup"><span data-stu-id="52539-215">Example — Create a new sensitive information for email addresses</span></span> 

<span data-ttu-id="52539-p120">我们将继续以电子邮件地址为例，因为它比较简单。下表详细说明了要获取新电子邮件敏感信息类型建议进行的修改。</span><span class="sxs-lookup"><span data-stu-id="52539-p120">We’ll continue with the email address as an example because it’s simple. The following table details the modifications recommended for a new email sensitive information type.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="52539-218"><strong>步骤</strong></span><span class="sxs-lookup"><span data-stu-id="52539-218"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="52539-219"><strong>修改</strong></span><span class="sxs-lookup"><span data-stu-id="52539-219"><strong>Modification</strong></span></span></th>
<th align="left"><span data-ttu-id="52539-220"><strong>XML 语法示例</strong></span><span class="sxs-lookup"><span data-stu-id="52539-220"><strong>Example XML syntax</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="52539-221">1</span><span class="sxs-lookup"><span data-stu-id="52539-221">1.</span></span></td>
<td align="left"><span data-ttu-id="52539-222">设置 IdRef 属性</span><span class="sxs-lookup"><span data-stu-id="52539-222">Set the IdRef property</span></span>
<p><span data-ttu-id="52539-p121">在 &lt;Entity&gt; 元素中，修改 &lt;IdMatch&gt; 元素，使其 idRef 属性为 = 唯一值。该值将指向一个元素，此元素定义了用于查找电子邮件地址的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="52539-p121">Within the &lt;Entity&gt; element, modify the &lt;IdMatch&gt; element so that its idRef property is = to a unique value. This value will point to an element that defines our regular expression to find email addresses.</span></span></p></td>
<td align="left"><span data-ttu-id="52539-225">IdRef=&quot;Regex_email_address&quot;</span><span class="sxs-lookup"><span data-stu-id="52539-225">IdRef=&quot;Regex_email_address&quot;</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52539-226">2</span><span class="sxs-lookup"><span data-stu-id="52539-226">2.</span></span></td>
<td align="left"><p><span data-ttu-id="52539-227">邻近度属性</span><span class="sxs-lookup"><span data-stu-id="52539-227">Proximity attribute</span></span></p>
<p><span data-ttu-id="52539-228">最初我们会将 &lt;Entity&gt; 元素中的 patternProximity 值设置为 300。</span><span class="sxs-lookup"><span data-stu-id="52539-228">We'll start with a patternProximity value in our &lt;Entity&gt; element of 300.</span></span></p></td>
<td align="left"><span data-ttu-id="52539-229">patternsProximity=&quot;300&quot;</span><span class="sxs-lookup"><span data-stu-id="52539-229">patternsProximity=&quot;300&quot;</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="52539-230">3</span><span class="sxs-lookup"><span data-stu-id="52539-230">3.</span></span></td>
<td align="left"><p><span data-ttu-id="52539-231">置信度</span><span class="sxs-lookup"><span data-stu-id="52539-231">Confidence Level</span></span></p>
<p><span data-ttu-id="52539-p122">将 recommendedConfidence 属性设置为可表示找到准确匹配项的可能性的值。这可能需要使用具有代表性的数据集进行测试才能获得准确的结果。最初设置时，将此值设置为 75。</span><span class="sxs-lookup"><span data-stu-id="52539-p122">Set the recommendedConfidence property to a value you feel will represent the confidence of finding an accurate match. This will likely require testing with a representative data set to get an accurate result. As an initial setting, set this value to 75.</span></span></p></td>
<td align="left"><p><span data-ttu-id="52539-235">recommendedConfidence=&quot;75&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-235">recommendedConfidence=&quot;75&quot;&gt;</span></span></p>
<p><span data-ttu-id="52539-236">前三个元素组合生成的 XML 如下所示：</span><span class="sxs-lookup"><span data-stu-id="52539-236">The resulting XML for these first three elements combined looks like this:</span></span></p>
<p><span data-ttu-id="52539-237">&lt;Entity id=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-237">&lt;Entity id=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;</span></span></p>
<p><span data-ttu-id="52539-238">&lt;Pattern confidenceLevel=&quot;75&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-238">&lt;Pattern confidenceLevel=&quot;75&quot;&gt;</span></span></p>
<p><span data-ttu-id="52539-239">&lt;IdMatch idRef=&quot;Regex_email_address&quot; /&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-239">&lt;IdMatch idRef=&quot;Regex_email_address&quot; /&gt;</span></span></p>
<p><span data-ttu-id="52539-240">&lt;Any minMatches=&quot;1&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-240">&lt;Any minMatches=&quot;1&quot;&gt;</span></span></p>
<p><span data-ttu-id="52539-241">&lt;Match idRef=&quot;Keyword_email_terms&quot; /&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-241">&lt;Match idRef=&quot;Keyword_email_terms&quot; /&gt;</span></span></p>
<p><span data-ttu-id="52539-242">&lt;/Any&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-242">Any</span></span></p>
<p><span data-ttu-id="52539-243">&lt;/Pattern&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-243">pattern</span></span></p>
<p><span data-ttu-id="52539-244">&lt;/Entity&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-244">entity</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52539-245">4</span><span class="sxs-lookup"><span data-stu-id="52539-245">4.</span></span></td>
<td align="left"><p><span data-ttu-id="52539-246">Regex 元素</span><span class="sxs-lookup"><span data-stu-id="52539-246">Regex element</span></span></p>
<p><span data-ttu-id="52539-247">在定义用于找出电子邮件地址的正则表达式的 &lt;Entity&gt; 元素下面（紧随其后）添加新的 &lt;Regex&gt; 元素。</span><span class="sxs-lookup"><span data-stu-id="52539-247">Add a new &lt;Regex&gt; element immediately be below the &lt;Entity&gt; elements that defines the regular expression used to identify email addresses.</span></span></p></td>
<td align="left"><span data-ttu-id="52539-248">&lt;Regex id=&quot;Regex_email_address&quot;&gt;(^|\b)([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})($|\b)&lt;/Regex&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-248">&lt;Regex id=&quot;Regex_email_address&quot;&gt;(^|\b)([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})($|\b)&lt;/Regex&gt;</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="52539-249">5</span><span class="sxs-lookup"><span data-stu-id="52539-249">5.</span></span></td>
<td align="left"><p><span data-ttu-id="52539-250">关键字</span><span class="sxs-lookup"><span data-stu-id="52539-250">Keywords</span></span></p>
<p><span data-ttu-id="52539-p123">在定义与电子邮件相关的关键字列表的 &lt;Regex&gt; 元素下添加新的 &lt;Keyword&gt; 元素。确保 &lt;Keyword&gt; 元素的 ID 值与 &lt;Entity&gt;&lt;Pattern&gt; 元素中的 &lt;Match idRef&gt; 值相匹配。必要时，可以继续添加自己的关键字。</span><span class="sxs-lookup"><span data-stu-id="52539-p123">Add a new &lt;Keyword&gt; element below the &lt;Regex&gt; element that defines list of email address related keywords. Ensure that the id value for the &lt;Keyword&gt; element matches the &lt;Match idRef&gt; value in the &lt;Entity&gt;&lt;Pattern&gt; element. You may continue to add your own keywords if needed.</span></span></p>
<p><span data-ttu-id="52539-p124">电子邮件敏感信息类型可能并没有必要包含关键字。以下列内容为例。</span><span class="sxs-lookup"><span data-stu-id="52539-p124">Keywords are likely not necessary to include in an email sensitive information type. These are provided as an example.</span></span></p></td>
<td align="left"><p><span data-ttu-id="52539-256">&lt;Keyword id=&quot;Keyword_email_terms&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-256">&lt;Keyword id=&quot;Keyword_email_terms&quot;&gt;</span></span></p>
<p><span data-ttu-id="52539-257">&lt;Group&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-257">group</span></span></p>
<p><span data-ttu-id="52539-258">&lt;Term&gt;email&lt;/Term&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-258">&lt;Term&gt;email&lt;/Term&gt;</span></span></p>
<p><span data-ttu-id="52539-259">&lt;Term&gt;email address&lt;/Term&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-259">&lt;Term&gt;email address&lt;/Term&gt;</span></span></p>
<p><span data-ttu-id="52539-260">&lt;Term&gt;contact&lt;/Term&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-260">&lt;Term&gt;contact&lt;/Term&gt;</span></span></p>
<p><span data-ttu-id="52539-261">&lt;/Group&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-261">group</span></span></p>
<p><span data-ttu-id="52539-262">&lt;/Keyword&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-262">&lt;/Keyword&gt;</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52539-263">6</span><span class="sxs-lookup"><span data-stu-id="52539-263">6.</span></span></td>
<td align="left"><p><span data-ttu-id="52539-264">LocalizedStrings 元素</span><span class="sxs-lookup"><span data-stu-id="52539-264">LocalizedStrings element</span></span></p>
<p><span data-ttu-id="52539-265">在 &lt;LocalizedStrings&gt;&lt;Resource&gt; 元素中，确保具有可标识敏感信息类型的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="52539-265">In the &lt;LocalizedStrings&gt;&lt;Resource&gt; element ensure that you have a unique name that identifies your sensitive information type.</span></span></p></td>
<td align="left"><p><span data-ttu-id="52539-266">&lt;LocalizedStrings&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-266">&lt;LocalizedStrings&gt;</span></span></p>
<p><span data-ttu-id="52539-267">&lt;Resource idRef=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-267">&lt;Resource idRef=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot;&gt;</span></span></p>
<p><span data-ttu-id="52539-268">&lt;Name default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Email Address&lt;/Name&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-268">&lt;Name default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Email Address&lt;/Name&gt;</span></span></p>
<p><span data-ttu-id="52539-269">&lt;Description default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Detects email addresses.&lt;/Description&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-269">&lt;Description default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Detects email addresses.&lt;/Description&gt;</span></span></p>
<p><span data-ttu-id="52539-270">&lt;/Resource&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-270">&lt;Resource&gt;</span></span></p>
<p><span data-ttu-id="52539-271">&lt;/LocalizedStrings&gt;</span><span class="sxs-lookup"><span data-stu-id="52539-271">&lt;/LocalizedStrings&gt;</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="create-a-new-sensitive-information-type-with-example-powershell-and-xml-file--contoso-customer-number"></a><span data-ttu-id="52539-272">使用示例 PowerShell 和 XML 文件新建敏感信息类型 — Contoso 客户编号</span><span class="sxs-lookup"><span data-stu-id="52539-272">Create a new sensitive information type with example PowerShell and XML file — Contoso customer number</span></span>

<span data-ttu-id="52539-p125">Contoso 使用 Contoso 客户编号 (CCN) 标识其客户数据库中的各个客户。一个 CCN 由以下分类组成：</span><span class="sxs-lookup"><span data-stu-id="52539-p125">Contoso uses a Contoso Customer Number (CCN) to identify each customer in their customer database. A CCN consists of the following taxonomy:</span></span>

-   <span data-ttu-id="52539-p126">两个表示创建记录的年份的数字。Contoso 创立于 2002年；因此，可能的最早的值为 02。</span><span class="sxs-lookup"><span data-stu-id="52539-p126">Two digits to represent the year that the record was created. Contoso was founded in 2002; therefore, the earliest possible value would be 02.</span></span>

-   <span data-ttu-id="52539-p127">三个表示创建记录的合作伙伴机构的数字。可能的机构值的范围为 000 到 999。</span><span class="sxs-lookup"><span data-stu-id="52539-p127">Three digits to represent the partner agency that created the record. Possible agency values range from 000 to 999.</span></span>

-   <span data-ttu-id="52539-p128">一个表示业务线的字母字符。可能的值为 a-z，且应区分大小写。</span><span class="sxs-lookup"><span data-stu-id="52539-p128">An alpha character to represent the line of business. Possible values are a-z and should be case insensitive.</span></span>

-   <span data-ttu-id="52539-p129">四位数的序列号。可能的序列号值的范围为 0000 到 9999。</span><span class="sxs-lookup"><span data-stu-id="52539-p129">A four-digit serial number. Possible serial number values range from 0000 to 9999.</span></span>

<span data-ttu-id="52539-283">CCN 示例：</span><span class="sxs-lookup"><span data-stu-id="52539-283">Example CCNs:</span></span>

> <span data-ttu-id="52539-284">15080P9562</span><span class="sxs-lookup"><span data-stu-id="52539-284">15080P9562</span></span>
>
> <span data-ttu-id="52539-285">14040O1119</span><span class="sxs-lookup"><span data-stu-id="52539-285">14040O1119</span></span>
>
> <span data-ttu-id="52539-286">15020J8317</span><span class="sxs-lookup"><span data-stu-id="52539-286">15020J8317</span></span>
>
> <span data-ttu-id="52539-287">14050E2330</span><span class="sxs-lookup"><span data-stu-id="52539-287">14050E2330</span></span>
>
> <span data-ttu-id="52539-288">16050E2166</span><span class="sxs-lookup"><span data-stu-id="52539-288">16050E2166</span></span>
>
> <span data-ttu-id="52539-289">17040O1118</span><span class="sxs-lookup"><span data-stu-id="52539-289">17040O1118</span></span>

<span data-ttu-id="52539-290">在内部通信、外部通信、文档等内容中，Contoso 通常使用 CCN 指代客户。他们想要创建一种自定义敏感信息类型来检测 Office 365 中使用的 CCN，以便对这种个人数据形式的使用应用保护。</span><span class="sxs-lookup"><span data-stu-id="52539-290">Contoso always refers to customers by using a CCN in internal correspondence, external correspondence, documents, etc. They would like to create a custom sensitive information type to detect the use of CCN in Office 365 so that they may apply protection to the use of this form of personal data.</span></span>

### <a name="create-a-new-sensitive-information-type-for-contoso-customer-number"></a><span data-ttu-id="52539-291">为 Contoso 客户编号创建新的敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="52539-291">Create a new sensitive information type for Contoso customer number</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="52539-292"><strong>步骤</strong></span><span class="sxs-lookup"><span data-stu-id="52539-292"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="52539-293"><strong>操作</strong></span><span class="sxs-lookup"><span data-stu-id="52539-293"><strong>action</strong></span></span></th>
<th align="left"><span data-ttu-id="52539-294"><strong>结果</strong></span><span class="sxs-lookup"><span data-stu-id="52539-294"><strong>Result</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="52539-295">1</span><span class="sxs-lookup"><span data-stu-id="52539-295">1.</span></span></td>
<td align="left"><span data-ttu-id="52539-296">Contoso 使用 PowerShell 和内容搜索来查找与 CCN 示例集匹配的文档。</span><span class="sxs-lookup"><span data-stu-id="52539-296">Contoso uses PowerShell and Content Search to find documents that match an example set of CCNs.</span></span></td>
<td align="left">

<p><span data-ttu-id="52539-297">#连接到 Office 365 安全与合规中心</span><span class="sxs-lookup"><span data-stu-id="52539-297">#Connect to Office 365 Security &amp; Compliance Center</span></span></p>
<p><span data-ttu-id="52539-298">$adminUser = &quot;alland@contoso.com&quot;</span><span class="sxs-lookup"><span data-stu-id="52539-298">$adminUser = &quot;alland@contoso.com&quot;</span></span></p>
<p><span data-ttu-id="52539-299">Connect-IPPSSession -UserPrincipalName $adminUser</span><span class="sxs-lookup"><span data-stu-id="52539-299">Connect-IPPSSession -UserPrincipalName $adminUser</span></span></p>
<p><span data-ttu-id="52539-300">#创建并开始搜索示例数据</span><span class="sxs-lookup"><span data-stu-id="52539-300">#Create &amp; start search for sample data</span></span></p>
<p><span data-ttu-id="52539-301">$searchName = &quot;Sample Customer Information Search&quot;</span><span class="sxs-lookup"><span data-stu-id="52539-301">$searchName = &quot;Sample Customer Information Search&quot;</span></span></p>
<p><span data-ttu-id="52539-302">$searchQuery = &quot;15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118&quot;</span><span class="sxs-lookup"><span data-stu-id="52539-302">$searchQuery = &quot;15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118&quot;</span></span></p>
<p><span data-ttu-id="52539-303">New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery</span><span class="sxs-lookup"><span data-stu-id="52539-303">New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery</span></span></p>
<p><span data-ttu-id="52539-304">Start-ComplianceSearch -Identity $searchName</span><span class="sxs-lookup"><span data-stu-id="52539-304">Start-ComplianceSearch -Identity $searchName</span></span></p>
</td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52539-305">2</span><span class="sxs-lookup"><span data-stu-id="52539-305">2.</span></span></td>
<td align="left"><span data-ttu-id="52539-p130">Contoso 分析结果。每次使用 CCN 时，都使用了 EU 格式的日期，此外，还在 300 个字符的邻近范围内使用了下列关键字之一。</span><span class="sxs-lookup"><span data-stu-id="52539-p130">Contoso analyzes the results. Every time the CCN was used, an EU formatted date was used and one of these keywords were also used within a proximity of 300 characters.</span></span></td>
<td align="left"><span data-ttu-id="52539-308">customer number、customer no、customer #、customer#、Contoso customer</span><span class="sxs-lookup"><span data-stu-id="52539-308">customer number, customer no, customer #, customer#, Contoso customer</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="52539-309">3</span><span class="sxs-lookup"><span data-stu-id="52539-309">3.</span></span></td>
<td align="left"><span data-ttu-id="52539-310">Contoso 生成了以下正则表达式 (RegEx) 模式来识别 CCN。</span><span class="sxs-lookup"><span data-stu-id="52539-310">Contoso developed the following Regular Expression (RegEx) pattern to identify their CCN.</span></span></td>
<td align="left"><span data-ttu-id="52539-311">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</span><span class="sxs-lookup"><span data-stu-id="52539-311">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52539-312">4</span><span class="sxs-lookup"><span data-stu-id="52539-312">4.</span></span></td>
<td align="left"><span data-ttu-id="52539-313">Contoso 生成了以下正则表达式 (RegEx) 模式来识别由各个子公司使用的格式的 EU 日期。</span><span class="sxs-lookup"><span data-stu-id="52539-313">Contoso developed the following Regular Expression (RegEx) pattern to identify EU dates in the formats used by their various subsidiaries.</span></span></td>
<td align="left">
````xml
(0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?|‌ feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|‌ apr(ile|il)?|abr(il)?|avril|may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|‌ oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?|nov(ember|iembre|embre|embro)?|dec(ember)?|‌ dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}
````
</td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="52539-314">5</span><span class="sxs-lookup"><span data-stu-id="52539-314">5.</span></span></td>
<td align="left"><span data-ttu-id="52539-315">Contoso 使用 PowerShell 生成三个唯一的 GUID。</span><span class="sxs-lookup"><span data-stu-id="52539-315">Contoso uses PowerShell to generate three unique GUIDs.</span></span></td>
<td align="left"><p><span data-ttu-id="52539-316">#为 RulePack ID、发布者 ID 和实体 ID 生成唯一的 GUID</span><span class="sxs-lookup"><span data-stu-id="52539-316">#Generate a unique GUID for RulePack Id, Publisher Id, and Entity Id</span></span></p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52539-317">6</span><span class="sxs-lookup"><span data-stu-id="52539-317">6.</span></span></td>
<td align="left"><span data-ttu-id="52539-318">Contoso 为其敏感项目类型规则定义以下参数。</span><span class="sxs-lookup"><span data-stu-id="52539-318">Contoso defines the following parameters for their sensitive item type rule.</span></span></td>
<td align="left"><p><span data-ttu-id="52539-319">名称：Contoso 客户编号 (CCN)</span><span class="sxs-lookup"><span data-stu-id="52539-319">Name: Contoso Customer Number (CCN)</span></span></p>
<p><span data-ttu-id="52539-320">说明：用于查找其他关键字和 EU 格式日期的 Contoso 客户编号 (CCN)</span><span class="sxs-lookup"><span data-stu-id="52539-320">Description: Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="52539-321">7</span><span class="sxs-lookup"><span data-stu-id="52539-321">7.</span></span></td>
<td align="left"><span data-ttu-id="52539-322">Contoso 为新的敏感信息类型创建 XML 文件，用于检测 Contoso 客户编号 (CCN)，并将此内容保存到本地文件系统的 C:\Scripts\ContosoCCN.xml 中，且使用 UTF-8 编码。</span><span class="sxs-lookup"><span data-stu-id="52539-322">Contoso creates an XML file for a new sensitive information type to detect a Contoso Customer Number (CCN) and saves this to a local file system as C:\Scripts\ContosoCCN.xml in with UTF-8 encoding.</span></span></td>
<td align="left"><span data-ttu-id="52539-323">请参阅此表下方的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="52539-323">See the XML file below this table.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52539-324">8</span><span class="sxs-lookup"><span data-stu-id="52539-324">8%</span></span></td>
<td align="left"><span data-ttu-id="52539-325">Contoso 使用以下 PowerShell 创建自定义敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="52539-325">Contoso creates the custom sensitive information type with the following PowerShell.</span></span></td>
<td align="left"><p><span data-ttu-id="52539-326">#连接到 Office 365 安全与合规中心</span><span class="sxs-lookup"><span data-stu-id="52539-326">#Connect to Office 365 Security &amp; Compliance Center</span></span></p>
<p><span data-ttu-id="52539-327">$adminUser = &quot;alland@contoso.com&quot;</span><span class="sxs-lookup"><span data-stu-id="52539-327">$adminUser = &quot;alland@contoso.com&quot;</span></span></p>
<p><span data-ttu-id="52539-328">Connect-IPPSSession -UserPrincipalName $adminUser</span><span class="sxs-lookup"><span data-stu-id="52539-328">Connect-IPPSSession -UserPrincipalName $adminUser</span></span></p>
<p><span data-ttu-id="52539-329">#创建新的敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="52539-329">#Create new Sensitive Information Type</span></span></p>
<p><span data-ttu-id="52539-330">New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path &quot;C:\Scripts\ContosoCCN.xml&quot; -Encoding Byte -ReadCount 0)</span><span class="sxs-lookup"><span data-stu-id="52539-330">New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path &quot;C:\Scripts\ContosoCCN.xml&quot; -Encoding Byte -ReadCount 0)</span></span></p></td>
</tr>
</tbody>
</table>

### <a name="example-xml-file-for-the-new-sensitive-information-type-step-7"></a><span data-ttu-id="52539-331">新敏感信息类型的示例 XML 文件（步骤 7）</span><span class="sxs-lookup"><span data-stu-id="52539-331">Example XML file for the new sensitive information type (step 7)</span></span>
```xml
\<?xml version="1.0" encoding="utf-8"?\>

\<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce"\>

\<RulePack id="130ae63b-a91e-4a12-9e02-a90e36a83d7f"\>

\<Version major="1" minor="0" build="0" revision="0" /\>

\<Publisher id="47148982-defd-42a1-890a-7b9472099f1f" /\>

\<Details defaultLangCode="en"\>

\<LocalizedDetails langcode="en"\>

\<PublisherName\>Contoso Ltd.\</PublisherName\>

\<Name\>Contoso Rule Package\</Name\>

\<Description\>Defines Contoso's custom set of classification rules\</Description\>

\</LocalizedDetails\>

\</Details\>

\</RulePack\>

\<Rules\>

\<!-- Contoso Customer Number (CCN) --\>

\<Entity id="a91f9a2e-6cfc-4622-8c5d-954875aa5b2b" patternsProximity="300" recommendedConfidence="85"\>

\<Pattern confidenceLevel="85"\>

\<IdMatch idRef="Regex\_contoso\_ccn" /\>

\<Match idRef="Keyword\_contoso\_ccn" /\>

\<Match idRef="Regex\_eu\_date" /\>

\</Pattern\>

\</Entity\>

\<Regex id="Regex\_contoso\_ccn"\>[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}\</Regex\>

\<Keyword id="Keyword\_contoso\_ccn"\>

\<Group matchStyle="word"\>

\<Term caseSensitive="false"\>customer number\</Term\>

\<Term caseSensitive="false"\>customer no\</Term\>

\<Term caseSensitive="false"\>customer \#\</Term\>

\<Term caseSensitive="false"\>customer\#\</Term\>

\<Term caseSensitive="false"\>Contoso customer\</Term\>

\</Group\>

\</Keyword\>

\<Regex id="Regex\_eu\_date"\> (0?[1-9]|[12][0-9]|3[0-1])[\\/-](0?[1-9]|1[0-2]|j\\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?‌ |feb(ruary|ruari|rero|braio|ruar|br)?|f\\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\\x00e4rz|maart‌|apr(ile|il)?|abr(il)?|avril‌ |may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?‌ |nov(ember|iembre|embre|embro)?|dec(ember)?|dic(iembre|embre)?|dez(ember|embro)?|d\\x00e9c(embre)?)[ \\/-](19|20)?[0-9]{2}\</Regex\>

\<LocalizedStrings\>

\<Resource idRef="a91f9a2e-6cfc-4622-8c5d-954875aa5b2b"\>

\<Name default="true" langcode="en-us"\>Contoso Customer Number (CCN)\</Name\>

\<Description default="true" langcode="en-us"\>Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date\</Description\>

\</Resource\>

\</LocalizedStrings\>

\</Rules\>

\</RulePackage\>
```
