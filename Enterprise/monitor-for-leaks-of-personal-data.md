---
title: "监视个人数据泄露"
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
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "了解可用于监视个人数据泄露的三种工具。"
ms.openlocfilehash: 04f5346a9c6554b75e9f360233c942907b826447
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="monitor-for-leaks-of-personal-data"></a>监视个人数据泄露

有许多工具可用于监视个人数据的使用和传输。本主题介绍了三种十分有用的工具。

![用于监视个人数据的使用和传输的工具](Media/Monitor-for-leaks-of-personal-data-image1.png)

在此图中：

-   从 SharePoint Online、OneDrive for Business 和传输中的电子邮件中用于监视个人数据的 Office 365 数据丢失防护报告着手。它们提供了有关监视个人数据的最为详细的内容。然而，这些报告并未包括 Office 365 中的所有服务。

-   接下来，使用警报策略和 Office 365 审核日志监视 Office 365 服务中的活动。设置持续监视或搜索审核日志以调查事件。Office 365 审核日志适用于 Office 365 服务：Sway、PowerBI、电子数据展示、Dynamics 365、Microsoft Flow、Microsoft Teams、管理员活动、OneDrive for Business、SharePoint Online、传输中的邮件和静态邮箱。Skype 对话包含在静态邮箱中。

-   最后，使用 Microsoft Cloud App Security 监视其他 SaaS 提供程序中具有敏感数据的文件。即将推出一项可以将 Azure 信息保护和 Office 中的 Office 365 敏感信息类型和统一标签与 Cloud App Security 配合使用的功能。可以设置应用到所有 SaaS 应用或特定应用（如 Box）的策略。Cloud App Security 不会发现 Exchange Online 中的文件（包括附加到电子邮件的文件）。

## <a name="office-365-data-loss-prevention-reports"></a>Office 365 数据丢失防护报告

创建数据丢失防护 (DLP) 策略后，你会希望验证这些策略是否按预期运行，以及是否有助于保持符合性。借助于 Office 365 中的 DLP 报告，可以快速查看 DLP 策略匹配项、重写或误报的数量；了解它们是否随着时间的推移呈上升或下降趋势；以不同的方式筛选报告；并且通过选择图形某个直线上的某个点来查看其他详细信息。

可以使用 DLP 报告实现以下目的：

-   重点关注特定的时间段，并了解峰值和发展趋势的原因。

-   发现违反您组织的 DLP 策略的业务流程。

-   了解 DLP 策略的任何业务影响。

-   查看用户在通过重写策略或报告误报解析策略提示时提交的理由。

-   通过显示该策略的匹配结果，验证该策略是否遵守特定 DLP 策略。

-   在详细信息窗格中查看与您的 DLP 策略相匹配的含敏感数据的文件列表。

此外，当你在测试模式下运行 DLP 策略时，可以使用 DLP 报告对其进行微调。

DLP 报告位于安全与合规中心内。导航至“报告”\>“查看报告”，在“数据丢失防护 (DLP)”下，转到“DLP 策略和规则匹配项”或“DLP 误报和重写”。

有关详细信息，请参阅[查看数据丢失防护报告](https://support.office.com/zh-CN/article/View-the-reports-for-data-loss-prevention-41eb4324-c513-4fa5-91c8-8fbd8aaba83b)。

![显示 DLP 策略匹配项的报告](Media/Monitor-for-leaks-of-personal-data-image2.png)

## <a name="office-365-audit-log-and-alert-policies"></a>Office 365 审核日志和警报策略

Office 365 审核日志包含来自 Exchange Online、SharePoint Online、OneDrive for Business、Azure Active Directory、Microsoft Teams、Power BI、Sway 和其他 Office 365 服务的事件。

Office 365 安全与合规中心提供两种方法针对 Office 365 审核日志进行监视和报告：

-   设置警报策略、查看警报和监视趋势：使用 Office 365 安全与合规中心中的新警报策略和警报仪表板工具。

-   直接搜索审核日志：搜索指定日期范围内的所有事件。也可以根据特定条件（如执行操作的用户、操作或目标对象）筛选结果。

信息安全和合规性团队可以使用这些工具主动审核 Office 365 服务中由最终用户和管理员执行的活动。当特定网站集上发生某些活动时（例如共享已知网站的内容以包含 GDPR 相关信息时），可以配置自动警报以发送电子邮件通知。此操作使这些团队可以跟进用户以确保遵守企业安全策略，或提供其他培训。

信息安全团队还可以搜索审核日志来调查可疑的数据泄露并确定根本原因和泄露的范围。此内置功能有助于遵守 GDPR 条款 33 和 34 的规定，其中要求在特定时间段内向 GDPR 监管机构和数据泄露的数据主体自身提供通知。通常建议在服务内仅将审核日志条目保留 90 天，而许多组织则要求将这些日志保留更长的时间。

可以使用通过 Microsoft 管理活动 API 订阅到统一审核日志的解决方案，此解决方案按需存储日志条目并提供高级仪表板和警报。例如：[Microsoft Operations Management Suite (OMS)](https://docs.microsoft.com/zh-CN/azure/operations-management-suite/oms-solution-office-365)。

有关警报策略和搜索审核日志的更多信息：

-   [Office 365 安全与合规中心的警报策略](https://support.office.com/zh-CN/article/Alert-policies-in-the-Office-365-Security-Compliance-Center-8927B8B9-C5BC-45A8-A9F9-96C732E58264)

-   [在 Office 365 中搜索用户和管理员活动的审核日志](https://support.office.com/zh-CN/article/Search-the-audit-log-for-user-and-admin-activity-in-Office-365-57CA5138-0AE0-4D34-BD40-240441EF2FB6)（介绍）

-   [启用或禁用 Office 365 审核日志搜索](https://support.office.com/zh-CN/article/Turn-Office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014)

-   [在 Office 365 安全与合规中心搜索审核日志](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&rs=en-US&ad=US)

-   
  [Search-UnifiedAuditLog](https://technet.microsoft.com/en-us/library/mt238501(v=exchg.160).aspx) (cmdlet) 

-   [Office 365 审核日志中的属性详细信息](https://support.office.com/zh-CN/article/Detailed-properties-in-the-Office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

Microsoft Cloud App Security 可帮助你跨网络发现使用中的其他 SaaS 应用、发送到这些应用的敏感数据以及从这些应用接收到的敏感数据。

Microsoft Cloud App Security 是一项可为云应用提供深入了解、细化控制和增强型威胁防护的综合服务。它可以从所有设备的网络中识别出超过 15,000 个云应用程序，并提供风险评分以及持续的风险评估和分析。无需代理：从防火墙和代理收集信息，从而向用户提供云使用情况和影子 IT 的完整可见性和上下文。

为了更好地了解云环境，Cloud App Security 调查功能深入了解批准的应用和托管的应用的所有活动、文件和帐户。用户可以获取有关文件级别的详细信息，并发现数据在云应用中传输的位置。

例如，下图说明了有助于符合 GDPR 的两个 Cloud App Security 策略。

![示例 Cloud App Security 策略](Media/Monitor-for-leaks-of-personal-data-image3.png)

如果选择的文件包含预定义的 PII 属性或自定义表达式，并且从选择的 SaaS 应用组织外部共享，那么第一个策略发出警报。

第二个策略会阻止将文件下载到任何非托管设备。选择要查找的文件内的属性以及需要对其应用策略的 SaaS 应用。

即将向 Cloud App Security 提供以下属性类型：

-   Office 365 敏感信息类型

-   Office 365 和 Azure 信息保护中的统一标签

### <a name="cloud-app-security-dashboard"></a>Cloud App Security 仪表板

如果尚未开始使用 Cloud App Security，请从启动阶段着手。访问 Cloud App Security：<https://portal.cloudappsecurity.com>。

注意：开始使用 Cloud App Security 时或在分配标签前，请务必启用“自动扫描 Azure 信息保护分类标签的文件”（位于“常规”设置中）。设置完成后，在修改现有文件之前，Cloud App Security 不会再次对其进行扫描。

![显示有关警报信息的仪表板](Media/Monitor-for-leaks-of-personal-data-image4.png)

详细信息：

-   [部署 Cloud App Security](https://docs.microsoft.com/zh-CN/cloud-app-security/getting-started-with-cloud-app-security)

-   [有关 Microsoft Cloud App Security 的更多信息](https://www.microsoft.com/zh-CN/cloud-platform/cloud-app-security)

-   [使用 Microsoft Cloud App Security 代理阻止下载敏感信息](https://docs.microsoft.com/zh-CN/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a>用于检测个人数据共享的示例文件和活动策略

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a>检测包含 PII 的文件共享 — 信用卡卡号

从批准的云应用共享包含信用卡卡号的文件时发出警报。

<table>
<thead>
<tr class="header">
<th align="left"><strong>控制</strong></th>
<th align="left"><strong>设置</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">策略类型</td>
<td align="left">文件策略</td>
</tr>
<tr class="even">
<td align="left">策略模板</td>
<td align="left">无模板</td>
</tr>
<tr class="odd">
<td align="left">策略严重性</td>
<td align="left">高</td>
</tr>
<tr class="even">
<td align="left">类别</td>
<td align="left">DLP</td>
</tr>
<tr class="odd">
<td align="left">筛选设置</td>
<td align="left"><p>访问级别 = 公共 (Internet)，公共，外部</p>
<p>应用 = &lt;选择应用&gt;（如果仅监视特定 SaaS 应用，则使用此设置）</p></td>
</tr>
<tr class="even">
<td align="left">应用对象</td>
<td align="left">所有文件、所有的所有者</td>
</tr>
<tr class="odd">
<td align="left">内容检查</td>
<td align="left"><p>包括匹配当前表达式的文件：所有国家/地区：法国：信用卡卡号</p>
<p>无需相关上下文：未选中（匹配关键字和正则表达式）</p>
<p>包括具有至少 1 个匹配项的文件</p>
<p>取消屏蔽冲突的最后 4 个字符：已选中</p></td>
</tr>
<tr class="even">
<td align="left">警报</td>
<td align="left"><p>为每个匹配文件创建警报：已选中</p>
<p>每日警报限制：1000</p>
<p>选择一个警报作为电子邮件：已选中</p>
<p>收件人：infosec@contoso.com</p></td>
</tr>
<tr class="odd">
<td align="left">治理</td>
<td align="left"><p>Microsoft OneDrive for Business</p>
<p>设为专用：选中“删除外部用户”</p>
<p>所有其他设置：未选中</p>
<p>Microsoft SharePoint Online</p>
<p>设为专用：选中“删除外部用户”</p>
<p>所有其他设置：未选中</p></td>
</tr>
</tbody>
</table>

类似策略：

-   检测包含 PII 的文件共享 — 电子邮件地址

-   检测包含 PII 的文件共享 — 护照编号

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a>检测 Box 或 OneDrive for Business 中的客户或 HR 数据

当标记为“客户数据”或“HR 数据”的文件上传至 OneDrive for Business 或 Box 时发出警报。

注意：

-   Box 监视要求使用 API 连接器 SDK 配置连接器。

-   此策略需要当前为个人预览版的功能。

<table>
<thead>
<tr class="header">
<th align="left"><strong>控制</strong></th>
<th align="left"><strong>设置</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">策略类型</td>
<td align="left">活动策略</td>
</tr>
<tr class="even">
<td align="left">策略模板</td>
<td align="left">无模板</td>
</tr>
<tr class="odd">
<td align="left">策略严重性</td>
<td align="left">高</td>
</tr>
<tr class="even">
<td align="left">类别</td>
<td align="left">共享控制</td>
</tr>
<tr class="odd">
<td align="left">作用对象</td>
<td align="left">单个活动</td>
</tr>
<tr class="even">
<td align="left">筛选设置</td>
<td align="left"><p>活动类型 = 上传文件</p>
<p>应用 = Microsoft OneDrive for Business 和 Box</p>
<p>分类标签（目前为个人预览版）：Azure 信息保护 = 客户数据、人力资源—薪资数据、人力资源—员工数据</p></td>
</tr>
<tr class="odd">
<td align="left">警报</td>
<td align="left"><p>创建警报：已选中</p>
<p>每日警报限制：1000</p>
<p>选择一个警报作为电子邮件：已选中</p>
<p>收件人：infosec@contoso.com</p></td>
</tr>
<tr class="even">
<td align="left">治理</td>
<td align="left"><p>所有应用</p>
<p>隔离用户：选中</p>
<p>所有其他设置：未选中</p>
<p>Office 365</p>
<p>隔离用户：选中</p>
<p>所有其他设置：未选中</p></td>
</tr>
</tbody>
</table>

类似策略：

-   检测客户数据或 HR 数据的大量下载 — 如果在较短时间段内检测到单个用户正在下载大量包含客户数据或 HR 数据的文件，则发出警报。

-   检测客户和 HR 数据共享 — 共享包含客户或 HR 数据的文件时发出警报。
