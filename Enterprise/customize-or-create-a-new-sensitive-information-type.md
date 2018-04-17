---
title: 自定义或新建敏感信息类型
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
description: 了解如何修改或新建针对 GDPR 的 Office 365 敏感信息类型。
ms.openlocfilehash: 17158dc3de7672e57ff84bc1dab24e844a15f43b
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="customize-or-create-a-new-sensitive-information-type"></a>自定义或新建敏感信息类型

本文提供了三个示例，说明如何修改或新建针对 GDPR 的 Office 365 敏感信息类型。

-   修改现有的敏感信息类型 — 欧盟借记卡号

-   新建敏感信息类型 — 电子邮件地址

-   使用示例 XML 文件新建敏感信息类型 — Contoso 客户编号

另请参阅：

-   [创建自定义敏感信息类型](https://support.office.com/zh-CN/article/Create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30)

-   [自定义内置敏感信息类型](https://support.office.com/zh-CN/article/Customize-a-built-in-sensitive-information-type-2164ce3d-4d64-4283-b6b1-b81fbe835e8e)

## <a name="modify-a-sensitive-information-type-to-improve-accuracy"></a>修改敏感信息类型以提高准确性

使用敏感信息类型通过内容搜索来搜索个人数据时，如果未返回预期结果，或者查询返回的误报过多，请考虑修改敏感信息类型，使其更适用于自己的环境。

创建或自定义敏感信息类型的最佳做法是基于现有的类型新建敏感信息类型，并为其提供一个唯一的名称和标识符。例如，如果要调整“欧盟借记卡号”敏感信息类型的参数，可以将该规则的副本命名为“欧盟借记卡增强版”，方便与原始名称进行区分。

在新的敏感信息类型中，仅修改为提高其准确性而需更改的值。完成后，上传新的敏感信息类型，创建新的 DLP 规则（或修改现有的规则），以便使用刚添加的新敏感信息类型。修改敏感信息类型的准确性可能需要反复试验，因此请保留原始类型的副本，这样以后如有必要，则可重新修改它。

自定义敏感信息类型：

1.  导出包含 Office 365 中的内置敏感信息类型的现有 Microsoft 规则包。

2.  将此 XML 文件重命名，在自己喜爱的 XML 编辑器中打开它。

3.  隔离相应的敏感信息类型，并删除所有其他的类型。

4.  使用 PowerShell 为正在修改的敏感信息类型生成两个新的 GUID。

5.  修改 ID 和其他基本元素，使此敏感信息类型成为唯一的类型（此过程包括将两个 GUID 替换为已生成的新 GUID）。

6.  微调匹配要求以提高准确性。

    1.  邻近性修改 — 修改字符模式邻近性，以扩大或缩小必须要围绕该敏感信息类型在其中查找关键字的范围。

    2.  关键字修改 — 向 \<Keywords\> 元素之一添加关键字，为敏感信息类型提供要搜索的更为具体的佐证，以便指示与此规则相匹配。或删除导致误报的关键字。

    3.  置信度修改 — 修改指示和报告匹配前敏感信息类型必须与定义中指定的条件达到的匹配置信度。

7.  上传新的敏感信息类型。

8.  重新对内容进行爬网，找出敏感信息。请参阅[手动请求对网站进行爬网和重新编制其索引](https://support.office.com/zh-CN/article/Manually-request-crawling-and-re-indexing-of-a-site-a-library-or-a-list-9AFA977D-39DE-4321-B4CA-8C7C7E6D264E)。

## <a name="example-modify-the-eu-debit-card-number-sensitive-information-type"></a>示例：修改“欧盟借记卡号”敏感信息类型

提高 DLP 规则在任意系统中的准确性需要在示例数据集上进行测试，并且可能需要通过反复修改和测试来进行微调。此示例演示了为提高准确性而对“欧盟借记卡号”敏感信息类型进行的修改。

在本示例中，搜索欧盟借记卡号时，该卡号的定义已严格定义为使用复杂模式且经过校验和验证的 16 位数字。由于此敏感信息类型的字符串定义，我们无法改变此模式。但我们可以做出以下调整，从而提高 Office 365 DLP 在 Office 365 内查找此敏感信息类型所使用的方式的准确性。

### <a name="proximity-modification"></a>邻近度修改

通过修改 \<Entity\> 元素中的 patternProximity 值（从 300 个字符修改为 150 个字符）来缩小范围。这表示佐证（关键字）必须较接近敏感信息类型才能指示与此规则相匹配。

\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\>

### <a name="keyword-modifications"></a>关键字修改

一些关键字可能会导致误报。因此可能需要删除关键字。以下是本示例的关键字：

\<Keyword id="Keyword\_card\_terms\_dict"\>

\<Group\>

\<Term\>corporate card\</Term\>

\<Term\>organization card\</Term\>

\<Term\>acct nbr\</Term\>

\<Term\>acct num\</Term\>

\<Term\>acct no\</Term\>

…

\</Group\>

\</Keyword\>

### <a name="confidence-modifications"></a>置信度修改

如果从定义中删除关键字，通常是想通过减小此值来调整找到该敏感信息类型的置信度。欧盟借记卡号类型的默认级别为 85。

\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\>

\<Pattern confidenceLevel="85"\>

…

\</Pattern\>

\</Entity\>

## <a name="create-a-new-custom-sensitive-information-type"></a>创建新的自定义敏感信息类型

若要创建新的自定义敏感信息类型，可以首先使用内容搜索完成以下操作：

-   优化 KQL 查询

-   查看哪些关键字最有用

使用上述结果创建新的敏感信息类型。然后针对环境优化新的敏感信息类型。

注意：即将推出大量适用于欧盟国家/地区的个人数据的新敏感信息类型。如需创建新的敏感信息类型，请首先将目标定位到所在环境的自定义数据。

### <a name="step-1--use-kql-queries-and-key-words-to-find-additional-data-in-your-environment"></a>步骤 1 — 使用 KQL 查询和关键字查找环境中的其他数据

可能需要创建其他查询来查找受 GDPR 制约的个人数据。内容搜索使用关键字查询语言 (KQL) 来查找数据。如果仅使用 KQL 而不使用敏感信息类型，大部分敏感数据都无法被准确地检测到。因此，此时的目标是使用内容搜索测试和优化 KQL 字符串，然后使用它们创建和微调新的敏感信息类型，进而提高准确性。

使用以下资源通过 KQL 构建和优化查询：

-   [关键字查询语言 (KQL) 语法参考 (DMC)](https://docs.microsoft.com/zh-CN/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

-   [在 Office 365 安全与合规中心运行内容搜索](https://support.office.com/zh-CN/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) 

内容搜索提供了可帮助开发 KQL 查询和敏感信息类型的其他资源 — 关键字。为什么要使用关键字列表？因为这样可以获取显示与各个关键字相匹配的项目数的统计信息。该信息有助于快速找到最有效（及最无效）的关键字。有关搜索统计信息的详细信息，请参阅[查看内容搜索结果的关键字统计信息](https://support.office.com/zh-CN/article/View-keyword-statistics-for-Content-Search-results-9701a024-c52e-43f0-b545-9a53478aec04)。

所创建的搜索查询中各行上的关键字通过 OR 运算符连接。也可以在行中使用关键字短语（用括号括起来）。

有关详细信息，请参阅[内容搜索的关键字查询和搜索条件](https://support.office.com/zh-CN/article/Keyword-queries-and-search-conditions-for-Content-Search-c4639c2e-7223-4302-8e0d-b6e10f1c3be3)。

### <a name="exampleusing-content-search-to-identify-email-addresses"></a>示例 — 使用内容搜索找出电子邮件地址

电子邮件地址被视为与数据主体相关的敏感信息。该简单示例演示了内容搜索如何发挥作用。

不能同时使用 KQL 和关键字。单独使用这些工具来筛选出查询，并确定可能会对敏感信息类型有帮助的关键字。

### <a name="kql-query"></a>KQL 查询

(^|\\b)([a-zA-Z0-9\_\\-\\.]+)@([a-zA-Z0-9\_\\-\\.]+)\\.([a-zA-Z]{2,5})($|\\b)

注意：

-   可以使用 NEAR 和 ONEAR 进行邻近度搜索。

-   但是，KQL 不支持含 Regex 类的查询（例如：IdRef="Regex\_email\_address"）

### <a name="keywords"></a>关键字

在单独的行上输入各个关键字。关键字示例：

-   email address

-   mail

-   contact

-   sender

-   recipient

-   cc

-   bcc

在本示例中可能会发现，关键字并非必要，并且会生成许多误报结果。

### <a name="step-2--create-a-new-custom-sensitive-information-type"></a>步骤 2 — 创建新的自定义敏感信息类型

使用 KQL 查询和关键字找出敏感信息后，使用它们创建新的自定义敏感信息类型。在许多情况下，需要敏感信息类型达到一定的复杂度才能获得所需的准确度。然后可以在 DLP 策略和其他工具及其他 KQL 查询中结合使用这些自定义敏感信息类型和内容搜索。

最佳做法是基于现有的类型创建新的敏感信息类型。请使用本文前面部分所述的同一过程。

### <a name="example--create-a-new-sensitive-information-for-email-addresses"></a>示例 — 为电子邮件地址创建新的敏感信息 

我们将继续以电子邮件地址为例，因为它比较简单。下表详细说明了要获取新电子邮件敏感信息类型建议进行的修改。

<table>
<thead>
<tr class="header">
<th align="left"><strong>步骤</strong></th>
<th align="left"><strong>修改</strong></th>
<th align="left"><strong>XML 语法示例</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left">设置 IdRef 属性
<p>在 &lt;Entity&gt; 元素中，修改 &lt;IdMatch&gt; 元素，使其 idRef 属性为 = 唯一值。该值将指向一个元素，此元素定义了用于查找电子邮件地址的正则表达式。</p></td>
<td align="left">IdRef=&quot;Regex_email_address&quot;</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left"><p>邻近度属性</p>
<p>最初我们会将 &lt;Entity&gt; 元素中的 patternProximity 值设置为 300。</p></td>
<td align="left">patternsProximity=&quot;300&quot;</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left"><p>置信度</p>
<p>将 recommendedConfidence 属性设置为可表示找到准确匹配项的可能性的值。这可能需要使用具有代表性的数据集进行测试才能获得准确的结果。最初设置时，将此值设置为 75。</p></td>
<td align="left"><p>recommendedConfidence=&quot;75&quot;&gt;</p>
<p>前三个元素组合生成的 XML 如下所示：</p>
<p>&lt;Entity id=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;</p>
<p>&lt;Pattern confidenceLevel=&quot;75&quot;&gt;</p>
<p>&lt;IdMatch idRef=&quot;Regex_email_address&quot; /&gt;</p>
<p>&lt;Any minMatches=&quot;1&quot;&gt;</p>
<p>&lt;Match idRef=&quot;Keyword_email_terms&quot; /&gt;</p>
<p>&lt;/Any&gt;</p>
<p>&lt;/Pattern&gt;</p>
<p>&lt;/Entity&gt;</p></td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left"><p>Regex 元素</p>
<p>在定义用于找出电子邮件地址的正则表达式的 &lt;Entity&gt; 元素下面（紧随其后）添加新的 &lt;Regex&gt; 元素。</p></td>
<td align="left">&lt;Regex id=&quot;Regex_email_address&quot;&gt;(^|\b)([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})($|\b)&lt;/Regex&gt;</td>
</tr>
<tr class="odd">
<td align="left">5</td>
<td align="left"><p>关键字</p>
<p>在定义与电子邮件相关的关键字列表的 &lt;Regex&gt; 元素下添加新的 &lt;Keyword&gt; 元素。确保 &lt;Keyword&gt; 元素的 ID 值与 &lt;Entity&gt;&lt;Pattern&gt; 元素中的 &lt;Match idRef&gt; 值相匹配。必要时，可以继续添加自己的关键字。</p>
<p>电子邮件敏感信息类型可能并没有必要包含关键字。以下列内容为例。</p></td>
<td align="left"><p>&lt;Keyword id=&quot;Keyword_email_terms&quot;&gt;</p>
<p>&lt;Group&gt;</p>
<p>&lt;Term&gt;email&lt;/Term&gt;</p>
<p>&lt;Term&gt;email address&lt;/Term&gt;</p>
<p>&lt;Term&gt;contact&lt;/Term&gt;</p>
<p>&lt;/Group&gt;</p>
<p>&lt;/Keyword&gt;</p></td>
</tr>
<tr class="even">
<td align="left">6</td>
<td align="left"><p>LocalizedStrings 元素</p>
<p>在 &lt;LocalizedStrings&gt;&lt;Resource&gt; 元素中，确保具有可标识敏感信息类型的唯一名称。</p></td>
<td align="left"><p>&lt;LocalizedStrings&gt;</p>
<p>&lt;Resource idRef=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot;&gt;</p>
<p>&lt;Name default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Email Address&lt;/Name&gt;</p>
<p>&lt;Description default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Detects email addresses.&lt;/Description&gt;</p>
<p>&lt;/Resource&gt;</p>
<p>&lt;/LocalizedStrings&gt;</p></td>
</tr>
</tbody>
</table>

## <a name="create-a-new-sensitive-information-type-with-example-powershell-and-xml-file--contoso-customer-number"></a>使用示例 PowerShell 和 XML 文件新建敏感信息类型 — Contoso 客户编号

Contoso 使用 Contoso 客户编号 (CCN) 标识其客户数据库中的各个客户。一个 CCN 由以下分类组成：

-   两个表示创建记录的年份的数字。Contoso 创立于 2002年；因此，可能的最早的值为 02。

-   三个表示创建记录的合作伙伴机构的数字。可能的机构值的范围为 000 到 999。

-   一个表示业务线的字母字符。可能的值为 a-z，且应区分大小写。

-   四位数的序列号。可能的序列号值的范围为 0000 到 9999。

CCN 示例：

> 15080P9562
>
> 14040O1119
>
> 15020J8317
>
> 14050E2330
>
> 16050E2166
>
> 17040O1118

在内部通信、外部通信、文档等内容中，Contoso 通常使用 CCN 指代客户。他们想要创建一种自定义敏感信息类型来检测 Office 365 中使用的 CCN，以便对这种个人数据形式的使用应用保护。

### <a name="create-a-new-sensitive-information-type-for-contoso-customer-number"></a>为 Contoso 客户编号创建新的敏感信息类型

<table>
<thead>
<tr class="header">
<th align="left"><strong>步骤</strong></th>
<th align="left"><strong>操作</strong></th>
<th align="left"><strong>结果</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left">Contoso 使用 PowerShell 和内容搜索来查找与 CCN 示例集匹配的文档。</td>
<td align="left">

<p>#连接到 Office 365 安全与合规中心</p>
<p>$adminUser = &quot;alland@contoso.com&quot;</p>
<p>Connect-IPPSSession -UserPrincipalName $adminUser</p>
<p>#创建并开始搜索示例数据</p>
<p>$searchName = &quot;Sample Customer Information Search&quot;</p>
<p>$searchQuery = &quot;15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118&quot;</p>
<p>New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery</p>
<p>Start-ComplianceSearch -Identity $searchName</p>
</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left">Contoso 分析结果。每次使用 CCN 时，都使用了 EU 格式的日期，此外，还在 300 个字符的邻近范围内使用了下列关键字之一。</td>
<td align="left">customer number、customer no、customer #、customer#、Contoso customer</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left">Contoso 生成了以下正则表达式 (RegEx) 模式来识别 CCN。</td>
<td align="left">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left">Contoso 生成了以下正则表达式 (RegEx) 模式来识别由各个子公司使用的格式的 EU 日期。</td>
<td align="left">
````xml
(0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?|‌ feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|‌ apr(ile|il)?|abr(il)?|avril|may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|‌ oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?|nov(ember|iembre|embre|embro)?|dec(ember)?|‌ dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}
````
</td>
</tr>
<tr class="odd">
<td align="left">5</td>
<td align="left">Contoso 使用 PowerShell 生成三个唯一的 GUID。</td>
<td align="left"><p>#为 RulePack ID、发布者 ID 和实体 ID 生成唯一的 GUID</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p></td>
</tr>
<tr class="even">
<td align="left">6</td>
<td align="left">Contoso 为其敏感项目类型规则定义以下参数。</td>
<td align="left"><p>名称：Contoso 客户编号 (CCN)</p>
<p>说明：用于查找其他关键字和 EU 格式日期的 Contoso 客户编号 (CCN)</p></td>
</tr>
<tr class="odd">
<td align="left">7</td>
<td align="left">Contoso 为新的敏感信息类型创建 XML 文件，用于检测 Contoso 客户编号 (CCN)，并将此内容保存到本地文件系统的 C:\Scripts\ContosoCCN.xml 中，且使用 UTF-8 编码。</td>
<td align="left">请参阅此表下方的 XML 文件。</td>
</tr>
<tr class="even">
<td align="left">8</td>
<td align="left">Contoso 使用以下 PowerShell 创建自定义敏感信息类型。</td>
<td align="left"><p>#连接到 Office 365 安全与合规中心</p>
<p>$adminUser = &quot;alland@contoso.com&quot;</p>
<p>Connect-IPPSSession -UserPrincipalName $adminUser</p>
<p>#创建新的敏感信息类型</p>
<p>New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path &quot;C:\Scripts\ContosoCCN.xml&quot; -Encoding Byte -ReadCount 0)</p></td>
</tr>
</tbody>
</table>

### <a name="example-xml-file-for-the-new-sensitive-information-type-step-7"></a>新敏感信息类型的示例 XML 文件（步骤 7）
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
