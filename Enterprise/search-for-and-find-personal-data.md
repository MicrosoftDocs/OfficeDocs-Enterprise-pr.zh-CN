---
title: "搜索和查找个人数据"
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
description: "了解如何在 Office 365 中搜索和查找个人数据。"
ms.openlocfilehash: f19aed534fe2bb4154edc31f0d1b0c82afcc1f04
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="search-for-and-find-personal-data"></a>搜索和查找个人数据

个人数据在 GDPR 中的定义非常宽泛，即指属于欧盟 (EU) 居民的已确定身份的或可识别的自然人的任何相关数据。

第 4 条 – 定义

> “个人数据”表示已确定身份的或可识别的自然人（“数据主体”）的任何相关信息；可识别的自然人是指可被直接或间接识别出的自然人，尤其是通过参考姓名、证件号码、位置数据、网络标识等标识，或通过参考特定于该自然人的身体、生理、基因、精神、经济、文化或社会标识的一个或多个因素进行识别；

本文演示了如何查找存储在 SharePoint Online 和 OneDrive for Business（其中包含所有 Office 365 组和 Microsoft Teams 的网站）中的个人数据。

查找符合 GDPR 的个人数据依赖于使用 Office 365 中的敏感信息类型。这些类型定义了自动进程识别特定信息类型（例如卫生服务号码和信用卡号码等）的方式。目前，无法以静态方式使用它们在 Exchange 邮箱中查找数据。但是，可以将敏感信息类型与数据丢失防护策略结合使用，处于传输状态时在邮件中查找个人数据。

因此，虽然当前不能以静态方式使用内容搜索在 Exchange Online 邮箱中查找个人数据，但是可以使用针对 GDPR 策展的敏感信息类型，在通过电子邮件发送个人信息时查找和保护个人信息。

## <a name="use-content-search-to-find-personal-data"></a>使用内容搜索查找个人数据

Microsoft 建议分三个阶段在 Office 365 中查找个人数据。本主题的剩余部分介绍了每个阶段的相关指南。

<table>
<thead>
<tr class="header">
<th align="left"><strong>步骤</strong></th>
<th align="left"><strong>说明</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>1. 搜索敏感信息类型</p></td>
<td align="left"><p>首先使用敏感信息类型查找个人数据。为每种敏感信息类型创建内容搜索查询。运行查询并分析结果。</p>
必要时，向查询添加参数，以减少误报： <li>计数范围</li>
    <li>置信区间</li>
    <li>用于更为复杂的查询的其他属性或运算符</li>
<p>必要时，修改敏感信息类型，以提高组织的准确性：</p>
<p><li>直接在 XML 中调整可信度。</li></p>
<p><li>添加关键字。</li></p>
<p><li>调整关键字的邻近度要求。</li></p></td>
</tr>
<tr class="even">
<td align="left"><p>2. 使用关键字查询语言 (KQL) 查找环境中的其他个人数据</p></td>
<td align="left"><p>如果要查找的数据不包含在敏感信息类型中，可以使用 KQL 查询语言生成自定义查询。</p>
<p>测试搜索结果，并调整 KQL 查询字符串，直至获得所需的结果。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3. 使用 KQL 查询创建新的自定义敏感信息类型</p></td>
<td align="left">在优化 KQL 查询以查找目标数据后，使用这些查询创建新的自定义敏感信息类型。然后可以在 DLP 策略和其他工具及其他 KQL 查询中结合使用这些自定义敏感信息类型和内容搜索。</td>
</tr>
</tbody>
</table>

即将提供的功能 — 将可在安全与合规中心的新用户界面中创建和修改敏感信息类型。可以动态查看匹配结果，并根据自己的需求微调敏感信息类型。

## <a name="search-for-sensitive-information-types-using-content-search"></a>使用内容搜索功能搜索敏感信息类型

首先使用 Office 365 所包含的敏感信息类型搜索个人数据。这些类型已列在安全与合规中心的“分类”下。

本主题附带适用于欧盟公民的最新敏感信息类型列表。可以从这些类型入手。时常查看安全与合规中心是否有新的添加项，从而帮助实现 GDPR 符合性。

另请参阅下文：[敏感信息类型列表及每种类型可查找的内容](https://support.office.com/zh-CN/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b)。

敏感信息类型定义了自动进程识别特定信息类型的方式，例如银行帐号、卫生服务号码和信用卡号码等。敏感信息类型也可称为条件。敏感信息类型通过正则表达式或函数可以识别的模式定义。此外，关键字和校验和等确凿的证据可用于识别敏感信息类型。可信度和邻近度也会在评估过程中使用。

目前，不能以静态方式使用敏感信息类型在邮箱中查找数据。

### <a name="using-content-search-with-sensitive-information-types"></a>结合使用内容搜索和敏感信息类型

<table>
<thead>
<tr class="header">
<th align="left"><strong>步骤</strong></th>
<th align="left"><strong>详细信息</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd"><td align="left"><p>转到安全与合规中心的“内容搜索”</p></td>
<td align="left"><p>在安全与合规中心的左侧窗格中，单击“搜索和调查”****&gt;****“内容搜索”。</p>
<p>请参阅<a href="https://support.office.com/en-us/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a">在 Office 365 安全与合规中心运行内容搜索</a>。</p></td>
</tr>
<tr class="even">
<td align="left"><p>为每种敏感信息类型创建新的搜索项</p></td>
<td align="left"><p>使用以下语法：</p>
<blockquote>
<p>SensitiveType:”&lt;类型&gt;”</p>
</blockquote>
<p>例如：</p>
<blockquote>
<p>SensitiveType:&quot;法国护照号码&quot;</p>
</blockquote>
<p>将搜索范围限定为 SharePoint（包括 OneDrive for Business）。确保语法准确无误，没有多余的空格或拼写错误。</p>
<p>请参阅<a href="https://support.office.com/zh-CN/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836">创建查询以查找存储在站点上的敏感数据</a>。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>查看各个搜索的结果</p></td>
<td align="left"><p>查看是否存在以下类型的问题，确定查询准确性是否符合目标：</p>
<p><li>许多误报</li></p>
<p><li>缺少已知的数据实例</li></p>
<p>请参阅<a href="https://support.office.com/en-us/article/Export-Content-Search-results-from-the-Office-365-Security-Compliance-Center-ed48d448-3714-4c42-85f5-10f75f6a4278">从 Office 365 安全与合规中心导出内容搜索结果</a>。</p>
<p>注意：如果使用的是 Mozilla Firefox 或 Chrome，可能需要先使用 Internet Explorer 或 Edge 下载报告，才能安装所需的加载项。</p></td>
</tr>
</tbody>
</table>

## <a name="sensitive-information-types-for-eu-citizen-data"></a>欧盟公民数据的敏感信息类型

从以下敏感信息类型入手。即将推出适用于欧盟国家/地区的个人数据的更多敏感信息类型。

> 比利时国家号码
>
> 信用卡号码
>
> 克罗地亚身份证号码
>
> 克罗地亚个人标识 (OIB) 号码
>
> 捷克国民身份证号码
>
> 丹麦个人识别号
>
> 欧盟借记卡号码
>
> 芬兰国家/地区身份证号码
>
> 芬兰护照号码
>
> 法国驾驶证号码
>
> 法国国家/地区身份证 (CNI)
>
> 法国护照号码
>
> 法国社会保险号码 (INSEE)
>
> 德国驾驶证号码
>
> 德国身份证号码
>
> 德国护照号码
>
> 希腊国民身份证
>
> 国际银行帐号 (IBAN)
>
> IP 地址
>
> 爱尔兰个人公共服务 (PPS) 号
>
> 意大利驾驶证号码
>
> 荷兰公民服务 (BSN) 号码
>
> 挪威标识号
>
> 波兰身份证
>
> 波兰国家/地区身份证号码 (PESEL)
>
> 波兰护照
>
> 葡萄牙公民卡号
>
> 西班牙社会保险号码 (SSN)
>
> 瑞典国家/地区身份证号码
>
> 瑞典护照号码
>
> 英国驾驶证号码
>
> 英国选民名册号码
>
> 英国国家卫生服务号码
>
> 英国国家保险号码 (NINO)
>
> 美国/英国护照号码

## <a name="add-parameters-to-a-sensitive-information-type-query-to-hone-the-results"></a>向敏感信息类型查询添加参数以筛选出结果

可以向敏感信息类型查询添加以下参数：

-   计数范围 — 定义敏感信息在文档中出现多少次之后，才将该文档包含在查询结果中。

-   置信区间 — 已检测到的敏感类型实际匹配的置信水平，例如 85 (85%)。

语法：

-   SensitiveType:”\<类型\>|\<计数范围\>|\<置信区间\>”

示例：

-   SensitiveType:“Credit Card Number|5”（只返回正好包含五个信用卡号码的文档）

-   SensitiveType:“Credit Card Number|\*|85..”（置信区间为 85 % 或更高）

注意：“SensitiveType”区分大小写，但查询的其余部分不区分大小写。

此外，还可以使用属性和运算符来说明如何优化查询。有关详细信息和示例，请参阅[创建查询以查找存储在站点上的敏感数据](https://support.office.com/zh-CN/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836)。
