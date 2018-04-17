---
title: 为个人数据构建分类架构
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
description: 确定组织是否使用标签作为 GDPR 计划的一部分。
ms.openlocfilehash: 5a462c6e63c72d76fe11d1a41df02cc2bc6f249d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="architect-a-classification-schema-for-personal-data"></a>为个人数据构建分类架构

本系列之前的文章重点介绍使用敏感信息类型识别符合 GDPR 的个人数据。敏感信息类型是一种分类形式。这可能是你需要的所有分类。但是，许多组织使用标签执行更广泛的数据管理策略。通过本主题来决定你是否也要使用标签作为 GDPR 计划的一部分。如果想要这样做，本主题提供了一些指导和示例。

注意：定义组织的分类架构和配置策略、标签和条件需要认真计划和精心准备。重要的是认识到这并不是一个 IT 驱动的流程。请务必与你的法律和合规团队协作，为组织的数据开发适当的分类和标签架构。

## <a name="decide-if-you-are-using-labels-in-addition-to-sensitive-data-types"></a>决定是否使用除敏感数据类型外的标签

可以在 Office 365 中为个人信息采用两种分类方法中的一种。这两种方法都可用于 GDPR 保护。如果决定仅使用敏感信息类型进行分类，可跳过本主题的剩余部分。

选择下列选项之一。

### <a name="option-1-use-only-office-365-sensitive-information-types"></a>选项 1：仅使用 Office 365 敏感信息类型

-   敏感信息类型可以有效地识别和保护符合 GDPR 和其他类型规定的个人数据。

-   如果你的组织尚未使用或计划使用标签执行更广泛的数据管理计划，这些类型会更易于使用。

-   这些类型适用于 DLP 规则（Office 标签也是如此）。

-   今后，这些类型将可用于 Cloud App Security，因此可以检测其他 SaaS 应用中的敏感信息。

### <a name="option-2-use-sensitive-information-types--office-labels"></a>选项 2：使用敏感信息类型 + Office 标签

-   将需要敏感信息类型将标签自动应用到符合 GDPR 的个人数据，因此，这些敏感信息类型是先决条件。

-   使用 Office 标签，可将符合 GDPR 的个人数据加入组织的更广泛数据管理计划。

-   今后，Office 标签将与 Azure 信息保护标签整合为统一的分类和标记引擎。

## <a name="develop-a-label-schema-that-includes-personal-data"></a>开发包含个人数据的标签架构

在使用技术功能应用标签和保护之前，首先在组织中定义分类架构。组织可能已具有分类架构，这样添加个人数据就会更加轻松。本主题包含一个示例分类架构。如有需要，可以从它入手。

### <a name="getting-started"></a>开始使用

首先决定要使用的标签数量和名称。执行此活动无需担心要使用的技术和应用标签的方式。在整个组织内普遍应用此架构，其中包括驻留在本地和其他云服务中的数据。

### <a name="recommendations"></a>建议 

设计和执行策略、标签和条件时，请考虑以下这些建议：

-   使用现有分类架构（如果有）— 许多组织已在使用某种形式的数据分类。仔细评估现有标签架构，如果可能，则直接使用。使用可被最终用户识别的常用标签将更易于采用。

-   从默认策略和标签开始 — 所有解决方案都具有一套预定义策略和标签。针对组织法律和业务要求对其进行仔细评估，并考虑使用它们来代替新建策略和标签。

-   从较小的数量着手 — 实际上，对可创建的标签数量没有限制。但是，较大数量的标签和子标签将对采用情况产生负面影响。选择过多常常意味着根本没有选择。

-   使用场景和用例 — 确定组织内的常见用例，并使用自 GDPR 派生的场景验证预想的标签和分配配置是否确实能起作用。

-   质疑对新标签的每个请求，每个场景或用例是否确实需要新标签，是否可以使用已有的标签？将标签数量保持为最小值可提高采用度。

-   将子标签用于关键部门，某些部门将具有需要特定标签的特定需求。将这些标签作为子标签定义到现有标签，并考虑使用被分配到用户组的范围策略而非全局策略。

-   考虑范围策略，以用户子集为目标的策略可以防止“标签过载”。范围策略可促使将角色或部门特定的（子）标签仅分配给为该特定部门工作的员工。

-   使用具有意义的标签名称，不建议使用专门术语、标准或缩写词作为标签名称。尝试使用能够引起最终用户共鸣的名称以提高采用度。与其使用 PII、PCI、HIPAA、LBI、MBI 和 HBI 等标签，不如考虑使用非业务、公开、常规、机密和高度机密等名称。

### <a name="example-classification-schema"></a>示例分类架构

<table>
<thead>
<tr class="header">
<th align="left"><strong>标签名称</strong></th>
<th align="left"><strong>说明</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">个人</td>
<td align="left">非业务数据，仅供个人使用。</td>
</tr>
<tr class="even">
<td align="left">公开</td>
<td align="left">专为公开使用准备和批准的业务数据。</td>
</tr>
<tr class="odd">
<td align="left">客户数据</td>
<td align="left">包含个人身份信息的业务数据。例如，信用卡卡号、银行账号和社会安全号码。</td>
</tr>
<tr class="even">
<td align="left">HR 数据</td>
<td align="left">有关 Contoso 员工的人力资源数据，如员工号码和薪资数据。</td>
</tr>
<tr class="odd">
<td align="left">机密</td>
<td align="left">与未经授权的人员共享可能导致业务损失的敏感业务数据。示例包括合同、安全报表、预测摘要和销售帐户数据。</td>
</tr>
<tr class="even">
<td align="left">高度机密</td>
<td align="left">与未经授权的人员共享会导致业务损失的非常敏感业务数据。示例包括员工和客户信息、密码、源代码和预先公布的财务报表。</td>
</tr>
</tbody>
</table>

## <a name="define-a-taxonomy-and-search-criteria-for-each-label"></a>定义每个标签的分类和搜索条件

为组织开发分类架构后，下一步是开发用于查找此数据的分类和搜索条件。对于个人数据，你已经通过识别敏感信息类型，已经自定义或新建环境的敏感信息类型完成了此项工作。

下表提供了组织的示例架构、分类和搜索条件。按照敏感级别从最不敏感到最敏感对标签进行排序，确保将匹配多个标签条件的数据分配到相应的标签。

注意：配置示例仅作演示之用，并不能作为部署指导或参考。

主要宗旨在于确保你为遵循 GDPR 符合性而进行的个人数据分类工作与整个组织的目标相契合。

### <a name="example-schema-taxonomy-and-search-criteria"></a>示例架构、分类和搜索条件

<table>
<thead>
<tr class="header">
<th align="left"><strong>标签</strong></th>
<th align="left"><strong>分类</strong></th>
<th align="left"><strong>方法</strong></th>
<th align="left"><strong>搜索语句</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">个人</td>
<td align="left">由最终用户手动标记为“个人”的文档。</td>
<td align="left">手动</td>
<td align="left">由最终用户手动标记为“个人”的文档。</td>
</tr>
<tr class="even">
<td align="left">公开</td>
<td align="left">包含区分大小写的短语“Approved for Public Release ##/####”（其中 # 表示任意数字）的文档。</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Approved for Public Release*</p>
<p>RegEx — (?i)(\bApproved for Public Release \d{2}\/\d{4}\b)</p></td>
</tr>
<tr class="odd">
<td align="left">客户数据</td>
<td align="left">欧盟公民数据的敏感信息类型。</td>
<td align="left">敏感信息类型</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">人力资源 — 员工数据</td>
<td align="left">包含采用 CONTOSO-9##### 格式（其中 # 表示任意数字）的区分大小写的员工 ID 的文档。</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — CONTOSO-9*</p>
<p>RegEx — (\bCONTOSO-9\d{5}\b)</p></td>
</tr>
<tr class="odd">
<td align="left">人力资源 — 薪资数据</td>
<td align="left">包含关键字（不区分大小写）“Contoso AND”或关键字（不区分大小写）“Salary OR Compensation”的文档</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Contoso AND (Salary OR Compensation)</p>
<p>RegEx — (\bCONTOSO-9\d{5}\b)</p></td>
</tr>
<tr class="even">
<td align="left">机密</td>
<td align="left">包含短语（不区分大小写）“Contoso Confidential”的文档。</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Contoso Confidential</p>
<p>RegEx — (?i)(\bContoso Confidential\b)</p></td>
</tr>
<tr class="odd">
<td align="left">高度机密</td>
<td align="left">包含短语（不区分大小写）“Contoso Secret”或“Secret-C####”（其中 # 表示任意数字）的文档。</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Contoso Secret OR Secret-C*</p>
<p>RegEx — (?i)(\bContoso Secret\b)|(\bSecret-C\d{4}\b)</p></td>
</tr>
</tbody>
</table>
