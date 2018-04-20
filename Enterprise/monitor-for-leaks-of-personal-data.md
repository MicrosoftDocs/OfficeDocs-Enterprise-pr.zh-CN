---
title: 监视个人数据泄露
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
description: 了解可用于监视个人数据泄露的三种工具。
ms.openlocfilehash: 4f7e9b35f7e2da5254e98a9f1cf97d6a5e9e1a73
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="monitor-for-leaks-of-personal-data"></a><span data-ttu-id="bc5a6-103">监视个人数据泄露</span><span class="sxs-lookup"><span data-stu-id="bc5a6-103">Monitor for leaks of personal data</span></span>

<span data-ttu-id="bc5a6-p101">有许多工具可用于监视个人数据的使用和传输。本主题介绍了三种十分有用的工具。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p101">There are many tools that can be used to monitor the use and transport of personal data. This topic describes three tools that work well.</span></span>

![用于监视个人数据的使用和传输的工具](Media/Monitor-for-leaks-of-personal-data-image1.png)

<span data-ttu-id="bc5a6-107">在此图中：</span><span class="sxs-lookup"><span data-stu-id="bc5a6-107">In the illustration:</span></span>

-   <span data-ttu-id="bc5a6-p102">从 SharePoint Online、OneDrive for Business 和传输中的电子邮件中用于监视个人数据的 Office 365 数据丢失防护报告着手。它们提供了有关监视个人数据的最为详细的内容。然而，这些报告并未包括 Office 365 中的所有服务。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p102">Start with Office 365 data loss prevention reports for monitoring personal data in SharePoint Online, OneDrive for Business, and email in transit. These provide the greatest level of detail for monitoring personal data. However, these reports don’t include all services in Office 365.</span></span>

-   <span data-ttu-id="bc5a6-p103">接下来，使用警报策略和 Office 365 审核日志监视 Office 365 服务中的活动。设置持续监视或搜索审核日志以调查事件。Office 365 审核日志适用于 Office 365 服务：Sway、PowerBI、电子数据展示、Dynamics 365、Microsoft Flow、Microsoft Teams、管理员活动、OneDrive for Business、SharePoint Online、传输中的邮件和静态邮箱。Skype 对话包含在静态邮箱中。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p103">Next, use alert policies and the Office 365 audit log to monitor activity across Office 365 services. Setup ongoing monitoring or search the audit log to investigate an incident. The Office 365 audit log works across Office 365 services — Sway, PowerBI, eDiscovery, Dynamics 365, Microsoft Flow, Microsoft Teams, Admin activity, OneDrive for Business, SharePoint Online, mail in transit, and mailboxes at rest. Skype conversations are included in mailboxes at rest.</span></span>

-   <span data-ttu-id="bc5a6-p104">最后，使用 Microsoft Cloud App Security 监视其他 SaaS 提供程序中具有敏感数据的文件。即将推出一项可以将 Azure 信息保护和 Office 中的 Office 365 敏感信息类型和统一标签与 Cloud App Security 配合使用的功能。可以设置应用到所有 SaaS 应用或特定应用（如 Box）的策略。Cloud App Security 不会发现 Exchange Online 中的文件（包括附加到电子邮件的文件）。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p104">Finally, Use Microsoft Cloud App Security to monitor files with sensitive data in other SaaS providers. Coming soon is the ability to use Office 365 sensitive information types and unified labels across Azure Information Protection and Office with Cloud App Security. You can setup policies that apply to all of your SaaS apps or specific apps (like Box). Cloud App Security doesn’t discover files in Exchange Online, including files attached to email.</span></span>

## <a name="office-365-data-loss-prevention-reports"></a><span data-ttu-id="bc5a6-119">Office 365 数据丢失防护报告</span><span class="sxs-lookup"><span data-stu-id="bc5a6-119">Office 365 data loss prevention reports</span></span>

<span data-ttu-id="bc5a6-p105">创建数据丢失防护 (DLP) 策略后，你会希望验证这些策略是否按预期运行，以及是否有助于保持符合性。借助于 Office 365 中的 DLP 报告，可以快速查看 DLP 策略匹配项、重写或误报的数量；了解它们是否随着时间的推移呈上升或下降趋势；以不同的方式筛选报告；并且通过选择图形某个直线上的某个点来查看其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p105">After you create your data loss prevention (DLP) policies, you’ll want to verify that they’re working as you intended and helping you to stay compliant. With the DLP reports in Office 365, you can quickly view the number of DLP policy matches, overrides, or false positives; see whether they’re trending up or down over time; filter the report in different ways; and view additional details by selecting a point on a line on the graph.</span></span>

<span data-ttu-id="bc5a6-122">可以使用 DLP 报告实现以下目的：</span><span class="sxs-lookup"><span data-stu-id="bc5a6-122">You can use the DLP reports to:</span></span>

-   <span data-ttu-id="bc5a6-123">重点关注特定的时间段，并了解峰值和发展趋势的原因。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-123">Focus on specific time periods and understand the reasons for spikes and trends.</span></span>

-   <span data-ttu-id="bc5a6-124">发现违反您组织的 DLP 策略的业务流程。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-124">Discover business processes that violate your organization’s DLP policies.</span></span>

-   <span data-ttu-id="bc5a6-125">了解 DLP 策略的任何业务影响。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-125">Understand any business impact of the DLP policies.</span></span>

-   <span data-ttu-id="bc5a6-126">查看用户在通过重写策略或报告误报解析策略提示时提交的理由。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-126">View the justifications submitted by users when they resolve a policy tip by overriding the policy or reporting a false positive.</span></span>

-   <span data-ttu-id="bc5a6-127">通过显示该策略的匹配结果，验证该策略是否遵守特定 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-127">Verify compliance with a specific DLP policy by showing any matches for that policy.</span></span>

-   <span data-ttu-id="bc5a6-128">在详细信息窗格中查看与您的 DLP 策略相匹配的含敏感数据的文件列表。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-128">View a list of files with sensitive data that matches your DLP policies in the details pane.</span></span>

<span data-ttu-id="bc5a6-129">此外，当你在测试模式下运行 DLP 策略时，可以使用 DLP 报告对其进行微调。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-129">In addition, you can use the DLP reports to fine tune your DLP policies as you run them in test mode.</span></span>

<span data-ttu-id="bc5a6-p106">DLP 报告位于安全与合规中心内。导航至“报告”\>“查看报告”，在“数据丢失防护 (DLP)”下，转到“DLP 策略和规则匹配项”或“DLP 误报和重写”。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p106">DLP reports are in Security and Compliance center. Navigate to Reports \> View reports. Under Data loss prevention (DLP), go to either DLP policy and rule matches or DLP false positives and overrides.</span></span>

<span data-ttu-id="bc5a6-133">有关详细信息，请参阅[查看数据丢失防护报告](https://support.office.com/zh-CN/article/View-the-reports-for-data-loss-prevention-41eb4324-c513-4fa5-91c8-8fbd8aaba83b)。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-133">For more information, see [View the reports for data loss prevention](https://support.office.com/zh-CN/article/View-the-reports-for-data-loss-prevention-41eb4324-c513-4fa5-91c8-8fbd8aaba83b).</span></span>

![显示 DLP 策略匹配项的报告](Media/Monitor-for-leaks-of-personal-data-image2.png)

## <a name="office-365-audit-log-and-alert-policies"></a><span data-ttu-id="bc5a6-135">Office 365 审核日志和警报策略</span><span class="sxs-lookup"><span data-stu-id="bc5a6-135">Office 365 audit log and alert policies</span></span>

<span data-ttu-id="bc5a6-136">Office 365 审核日志包含来自 Exchange Online、SharePoint Online、OneDrive for Business、Azure Active Directory、Microsoft Teams、Power BI、Sway 和其他 Office 365 服务的事件。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-136">The Office 365 audit log contains events from Exchange Online, SharePoint Online, OneDrive for Business, Azure Active Directory, Microsoft Teams, Power BI, Sway, and other Office 365 services.</span></span>

<span data-ttu-id="bc5a6-137">Office 365 安全与合规中心提供两种方法针对 Office 365 审核日志进行监视和报告：</span><span class="sxs-lookup"><span data-stu-id="bc5a6-137">The Office 365 Security and Compliance Center provides two ways to monitor and report against the Office 365 audit log:</span></span>

-   <span data-ttu-id="bc5a6-138">设置警报策略、查看警报和监视趋势：使用 Office 365 安全与合规中心中的新警报策略和警报仪表板工具。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-138">Setup alert policies, view alerts, and monitor trends — Use the new alert policy and alert dashboard tools in the Office 365 Security & Compliance Center.</span></span>

-   <span data-ttu-id="bc5a6-p107">直接搜索审核日志：搜索指定日期范围内的所有事件。也可以根据特定条件（如执行操作的用户、操作或目标对象）筛选结果。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p107">Search the audit log directly — Search for all events in a specified date rage. Or you can filter the results based on specific criteria, such as the user who performed the action, the action, or the target object.</span></span>

<span data-ttu-id="bc5a6-p108">信息安全和合规性团队可以使用这些工具主动审核 Office 365 服务中由最终用户和管理员执行的活动。当特定网站集上发生某些活动时（例如共享已知网站的内容以包含 GDPR 相关信息时），可以配置自动警报以发送电子邮件通知。此操作使这些团队可以跟进用户以确保遵守企业安全策略，或提供其他培训。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p108">Information security and compliance teams can use these tools to proactively review activities performed by both end users and administrators across Office 365 services. Automatic alerts can be configured to send email notifications when certain activities occur on specific site collections - for example when content is shared from sites known to contain GDPR related information. This allows those teams to follow up with users to ensure that corporate security policies are followed, or to provide additional training.</span></span>

<span data-ttu-id="bc5a6-p109">信息安全团队还可以搜索审核日志来调查可疑的数据泄露并确定根本原因和泄露的范围。此内置功能有助于遵守 GDPR 条款 33 和 34 的规定，其中要求在特定时间段内向 GDPR 监管机构和数据泄露的数据主体自身提供通知。通常建议在服务内仅将审核日志条目保留 90 天，而许多组织则要求将这些日志保留更长的时间。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p109">Information security teams can also search the audit log to investigate suspected data breaches and determine both root cause and the extent of the breach. This built in capability facilitates compliance with article 33 and 34 of the GDPR, which require notifications be provided to the GDPR supervisory authority and to the data subjects themselves of a data breach within a specific time period. Audit log entries are only retained for 90 days within the service - it is often recommended and many organizations required that these logs be retained for longer periods of time.</span></span>

<span data-ttu-id="bc5a6-p110">可以使用通过 Microsoft 管理活动 API 订阅到统一审核日志的解决方案，此解决方案按需存储日志条目并提供高级仪表板和警报。例如：[Microsoft Operations Management Suite (OMS)](https://docs.microsoft.com/zh-CN/azure/operations-management-suite/oms-solution-office-365)。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p110">Solutions are available which subscribe to the Unified Audit Logs through the Microsoft Management Activity API and can both store log entries as needed, and provide advanced dashboards and alerts. One example is [Microsoft Operations Management Suite (OMS)](https://docs.microsoft.com/zh-CN/azure/operations-management-suite/oms-solution-office-365).</span></span>

<span data-ttu-id="bc5a6-149">有关警报策略和搜索审核日志的更多信息：</span><span class="sxs-lookup"><span data-stu-id="bc5a6-149">More information about alert policies and searching the audit log:</span></span>

-   [<span data-ttu-id="bc5a6-150">Office 365 安全与合规中心的警报策略</span><span class="sxs-lookup"><span data-stu-id="bc5a6-150">Alert policies in the Office 365 Security & Compliance Center</span></span>](https://support.office.com/zh-CN/article/Alert-policies-in-the-Office-365-Security-Compliance-Center-8927B8B9-C5BC-45A8-A9F9-96C732E58264)

-   <span data-ttu-id="bc5a6-151">[在 Office 365 中搜索用户和管理员活动的审核日志](https://support.office.com/zh-CN/article/Search-the-audit-log-for-user-and-admin-activity-in-Office-365-57CA5138-0AE0-4D34-BD40-240441EF2FB6)（介绍）</span><span class="sxs-lookup"><span data-stu-id="bc5a6-151">[Search the audit log for user and admin activity in Office 365](https://support.office.com/zh-CN/article/Search-the-audit-log-for-user-and-admin-activity-in-Office-365-57CA5138-0AE0-4D34-BD40-240441EF2FB6) (introduction)</span></span>

-   [<span data-ttu-id="bc5a6-152">启用或禁用 Office 365 审核日志搜索</span><span class="sxs-lookup"><span data-stu-id="bc5a6-152">Turn Office 365 audit log search on or off</span></span>](https://support.office.com/zh-CN/article/Turn-Office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014)

-   <span data-ttu-id="bc5a6-153">
  [在 Office 365 安全与合规中心搜索审核日志](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&rs=en-US&ad=US)</span><span class="sxs-lookup"><span data-stu-id="bc5a6-153">[Search the audit log in the Office 365 Security & Compliance Center](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&rs=en-US&ad=US)</span></span>

-   <span data-ttu-id="bc5a6-154">
  [Search-UnifiedAuditLog](https://technet.microsoft.com/en-us/library/mt238501(v=exchg.160).aspx) (cmdlet)</span><span class="sxs-lookup"><span data-stu-id="bc5a6-154">[Search-UnifiedAuditLog](https://technet.microsoft.com/en-us/library/mt238501(v=exchg.160).aspx) (cmdlet)</span></span> 

-   [<span data-ttu-id="bc5a6-155">Office 365 审核日志中的属性详细信息</span><span class="sxs-lookup"><span data-stu-id="bc5a6-155">Detailed properties in the Office 365 audit log</span></span>](https://support.office.com/zh-CN/article/Detailed-properties-in-the-Office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)

## <a name="microsoft-cloud-app-security"></a><span data-ttu-id="bc5a6-156">Microsoft Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="bc5a6-156">Microsoft Cloud App Security</span></span>

<span data-ttu-id="bc5a6-157">Microsoft Cloud App Security 可帮助你跨网络发现使用中的其他 SaaS 应用、发送到这些应用的敏感数据以及从这些应用接收到的敏感数据。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-157">Microsoft Cloud App Security helps you discover other SaaS apps in use across your networks and sensitive data that is sent to and from these apps.</span></span>

<span data-ttu-id="bc5a6-p111">Microsoft Cloud App Security 是一项可为云应用提供深入了解、细化控制和增强型威胁防护的综合服务。它可以从所有设备的网络中识别出超过 15,000 个云应用程序，并提供风险评分以及持续的风险评估和分析。无需代理：从防火墙和代理收集信息，从而向用户提供云使用情况和影子 IT 的完整可见性和上下文。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p111">Microsoft Cloud App Security is a comprehensive service providing deep visibility, granular controls and enhanced threat protection for your cloud apps. It identifies more than 15,000 cloud applications in your network-from all devices-and provides risk scoring and ongoing risk assessment and analytics. No agents required: information is collected from your firewalls and proxies to give you complete visibility and context for cloud usage and shadow IT.</span></span>

<span data-ttu-id="bc5a6-p112">为了更好地了解云环境，Cloud App Security 调查功能深入了解批准的应用和托管的应用的所有活动、文件和帐户。用户可以获取有关文件级别的详细信息，并发现数据在云应用中传输的位置。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p112">To better understand your cloud environment, Cloud App Security investigate feature provides deep visibility into all activities, files and accounts for sanctioned and managed apps. You can gain detailed information on a file level and discover where data travels in the cloud apps.</span></span>

<span data-ttu-id="bc5a6-163">例如，下图说明了有助于符合 GDPR 的两个 Cloud App Security 策略。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-163">For examples, the following illustration demonstrates two Cloud App Security policies that can help with GDPR.</span></span>

![示例 Cloud App Security 策略](Media/Monitor-for-leaks-of-personal-data-image3.png)

<span data-ttu-id="bc5a6-165">如果选择的文件包含预定义的 PII 属性或自定义表达式，并且从选择的 SaaS 应用组织外部共享，那么第一个策略发出警报。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-165">The first policy alerts when files with a predefined PII attribute or custom expression that you choose is shared outside the organization from the SaaS apps that you choose.</span></span>

<span data-ttu-id="bc5a6-p113">第二个策略会阻止将文件下载到任何非托管设备。选择要查找的文件内的属性以及需要对其应用策略的 SaaS 应用。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p113">The second policy blocks downloads of files to any unmanaged device. You choose the attributes within the files to look for and the SaaS apps you want the policy to apply to.</span></span>

<span data-ttu-id="bc5a6-168">即将向 Cloud App Security 提供以下属性类型：</span><span class="sxs-lookup"><span data-stu-id="bc5a6-168">These attribute types are coming soon to Cloud App Security:</span></span>

-   <span data-ttu-id="bc5a6-169">Office 365 敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="bc5a6-169">Office 365 sensitive information types</span></span>

-   <span data-ttu-id="bc5a6-170">Office 365 和 Azure 信息保护中的统一标签</span><span class="sxs-lookup"><span data-stu-id="bc5a6-170">Unified labels across Office 365 and Azure Information Protection</span></span>

### <a name="cloud-app-security-dashboard"></a><span data-ttu-id="bc5a6-171">Cloud App Security 仪表板</span><span class="sxs-lookup"><span data-stu-id="bc5a6-171">Cloud App Security dashboard</span></span>

<span data-ttu-id="bc5a6-p114">如果尚未开始使用 Cloud App Security，请先启动它。Cloud App Security 的访问网址为 <https://portal.cloudappsecurity.com>。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p114">If you haven’t yet started to use Cloud App Security, begin by starting it up. To access Cloud App Security: <https://portal.cloudappsecurity.com>.</span></span>

<span data-ttu-id="bc5a6-p115">注意：开始使用 Cloud App Security 时或在分配标签前，请务必启用“自动扫描 Azure 信息保护分类标签的文件”（位于“常规”设置中）。设置完成后，在修改现有文件之前，Cloud App Security 不会再次对其进行扫描。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-p115">Note: Be sure to enable ‘Automatically scan files for Azure Information Protection classification labels’ (in General settings) when getting started with Cloud App Security or before you assign labels. After setup, Cloud App Security does not scan existing files again until they are modified.</span></span>

![显示有关警报信息的仪表板](Media/Monitor-for-leaks-of-personal-data-image4.png)

<span data-ttu-id="bc5a6-177">详细信息：</span><span class="sxs-lookup"><span data-stu-id="bc5a6-177">More information:</span></span>

-   [<span data-ttu-id="bc5a6-178">部署 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="bc5a6-178">Deploy Cloud App Security</span></span>](https://docs.microsoft.com/zh-CN/cloud-app-security/getting-started-with-cloud-app-security)

-   [<span data-ttu-id="bc5a6-179">有关 Microsoft Cloud App Security 的更多信息</span><span class="sxs-lookup"><span data-stu-id="bc5a6-179">More information about Microsoft Cloud App Security</span></span>](https://www.microsoft.com/zh-CN/cloud-platform/cloud-app-security)

-   [<span data-ttu-id="bc5a6-180">使用 Microsoft Cloud App Security 代理阻止下载敏感信息</span><span class="sxs-lookup"><span data-stu-id="bc5a6-180">Block downloads of sensitive information using the Microsoft Cloud App Security proxy</span></span>](https://docs.microsoft.com/zh-CN/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a><span data-ttu-id="bc5a6-181">用于检测个人数据共享的示例文件和活动策略</span><span class="sxs-lookup"><span data-stu-id="bc5a6-181">Example file and activity policies to detect sharing of personal data</span></span>

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a><span data-ttu-id="bc5a6-182">检测包含 PII 的文件共享 — 信用卡卡号</span><span class="sxs-lookup"><span data-stu-id="bc5a6-182">Detect sharing of files containing PII — Credit card number</span></span>

<span data-ttu-id="bc5a6-183">从批准的云应用共享包含信用卡卡号的文件时发出警报。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-183">Alert when a file containing a credit card number is shared from an approved cloud app.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="bc5a6-184"><strong>控制</strong></span><span class="sxs-lookup"><span data-stu-id="bc5a6-184"><strong>Control</strong></span></span></th>
<th align="left"><span data-ttu-id="bc5a6-185"><strong>设置</strong></span><span class="sxs-lookup"><span data-stu-id="bc5a6-185"><strong>Settings</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc5a6-186">策略类型</span><span class="sxs-lookup"><span data-stu-id="bc5a6-186">Policy type</span></span></td>
<td align="left"><span data-ttu-id="bc5a6-187">文件策略</span><span class="sxs-lookup"><span data-stu-id="bc5a6-187">File policy</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc5a6-188">策略模板</span><span class="sxs-lookup"><span data-stu-id="bc5a6-188">Policy template</span></span></td>
<td align="left"><span data-ttu-id="bc5a6-189">无模板</span><span class="sxs-lookup"><span data-stu-id="bc5a6-189">No template</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc5a6-190">策略严重性</span><span class="sxs-lookup"><span data-stu-id="bc5a6-190">Policy severity</span></span></td>
<td align="left"><span data-ttu-id="bc5a6-191">高</span><span class="sxs-lookup"><span data-stu-id="bc5a6-191">High</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc5a6-192">类别</span><span class="sxs-lookup"><span data-stu-id="bc5a6-192">Category</span></span></td>
<td align="left"><span data-ttu-id="bc5a6-193">DLP</span><span class="sxs-lookup"><span data-stu-id="bc5a6-193">DLP</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc5a6-194">筛选设置</span><span class="sxs-lookup"><span data-stu-id="bc5a6-194">Filter settings</span></span></td>
<td align="left"><p><span data-ttu-id="bc5a6-195">访问级别 = 公共 (Internet)，公共，外部</span><span class="sxs-lookup"><span data-stu-id="bc5a6-195">Access level = Public (Internet), Public, External</span></span></p>
<p><span data-ttu-id="bc5a6-196">应用 = &lt;选择应用&gt;（如果仅监视特定 SaaS 应用，则使用此设置）</span><span class="sxs-lookup"><span data-stu-id="bc5a6-196">App = &lt;select apps&gt; (use this setting if you want to limit monitoring to specific SaaS apps)</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc5a6-197">应用对象</span><span class="sxs-lookup"><span data-stu-id="bc5a6-197">Apply to</span></span></td>
<td align="left"><span data-ttu-id="bc5a6-198">所有文件、所有的所有者</span><span class="sxs-lookup"><span data-stu-id="bc5a6-198">All files, all owners</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc5a6-199">内容检查</span><span class="sxs-lookup"><span data-stu-id="bc5a6-199">Content inspection</span></span></td>
<td align="left"><p><span data-ttu-id="bc5a6-200">包括匹配当前表达式的文件：所有国家/地区：法国：信用卡卡号</span><span class="sxs-lookup"><span data-stu-id="bc5a6-200">Includes files that match a present expression: All countries: Finance: Credit card number</span></span></p>
<p><span data-ttu-id="bc5a6-201">无需相关上下文：未选中（匹配关键字和正则表达式）</span><span class="sxs-lookup"><span data-stu-id="bc5a6-201">Don’t require relevant context: unchecked (this will match keywords as well as regex)</span></span></p>
<p><span data-ttu-id="bc5a6-202">包括具有至少 1 个匹配项的文件</span><span class="sxs-lookup"><span data-stu-id="bc5a6-202">Includes files with at least 1 match</span></span></p>
<p><span data-ttu-id="bc5a6-203">取消屏蔽冲突的最后 4 个字符：已选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-203">Unmask the last 4 characters of the violation: checked</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc5a6-204">警报</span><span class="sxs-lookup"><span data-stu-id="bc5a6-204">Alerts</span></span></td>
<td align="left"><p><span data-ttu-id="bc5a6-205">为每个匹配文件创建警报：已选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-205">Create an alert for each matching file: checked</span></span></p>
<p><span data-ttu-id="bc5a6-206">每日警报限制：1000</span><span class="sxs-lookup"><span data-stu-id="bc5a6-206">Daily alert limit: 1000</span></span></p>
<p><span data-ttu-id="bc5a6-207">选择一个警报作为电子邮件：已选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-207">Select an alert as email: checked</span></span></p>
<p><span data-ttu-id="bc5a6-208">收件人：infosec@contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc5a6-208">To: infosec@contoso.com</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc5a6-209">治理</span><span class="sxs-lookup"><span data-stu-id="bc5a6-209">Governance</span></span></td>
<td align="left"><p><span data-ttu-id="bc5a6-210">Microsoft OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="bc5a6-210">Microsoft OneDrive for Business</span></span></p>
<p><span data-ttu-id="bc5a6-211">设为专用：选中“删除外部用户”</span><span class="sxs-lookup"><span data-stu-id="bc5a6-211">Make private: check Remove External Users</span></span></p>
<p><span data-ttu-id="bc5a6-212">所有其他设置：未选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-212">All other settings: unchecked</span></span></p>
<p><span data-ttu-id="bc5a6-213">Microsoft SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bc5a6-213">Microsoft SharePoint Online</span></span></p>
<p><span data-ttu-id="bc5a6-214">设为专用：选中“删除外部用户”</span><span class="sxs-lookup"><span data-stu-id="bc5a6-214">Make private: check Remove External Users</span></span></p>
<p><span data-ttu-id="bc5a6-215">所有其他设置：未选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-215">All other settings: unchecked</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="bc5a6-216">类似策略：</span><span class="sxs-lookup"><span data-stu-id="bc5a6-216">Similar policies:</span></span>

-   <span data-ttu-id="bc5a6-217">检测包含 PII 的文件共享 — 电子邮件地址</span><span class="sxs-lookup"><span data-stu-id="bc5a6-217">Detect sharing of Files containing PII - Email Address</span></span>

-   <span data-ttu-id="bc5a6-218">检测包含 PII 的文件共享 — 护照编号</span><span class="sxs-lookup"><span data-stu-id="bc5a6-218">Detect sharing of Files containing PII - Passport Number</span></span>

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a><span data-ttu-id="bc5a6-219">检测 Box 或 OneDrive for Business 中的客户或 HR 数据</span><span class="sxs-lookup"><span data-stu-id="bc5a6-219">Detect Customer or HR Data in Box or OneDrive for Business</span></span>

<span data-ttu-id="bc5a6-220">当标记为“客户数据”或“HR 数据”的文件上传至 OneDrive for Business 或 Box 时发出警报。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-220">Alert when a file labeled as Customer Data or HR Data is uploaded to OneDrive for Business or Box.</span></span>

<span data-ttu-id="bc5a6-221">注意：</span><span class="sxs-lookup"><span data-stu-id="bc5a6-221">Notes:</span></span>

-   <span data-ttu-id="bc5a6-222">Box 监视要求使用 API 连接器 SDK 配置连接器。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-222">Box monitoring requires a connector be configured using the API Connector SDK.</span></span>

-   <span data-ttu-id="bc5a6-223">此策略需要当前为个人预览版的功能。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-223">This policy requires capabilities that are currently in private preview.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="bc5a6-224"><strong>控制</strong></span><span class="sxs-lookup"><span data-stu-id="bc5a6-224"><strong>Control</strong></span></span></th>
<th align="left"><span data-ttu-id="bc5a6-225"><strong>设置</strong></span><span class="sxs-lookup"><span data-stu-id="bc5a6-225"><strong>Settings</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc5a6-226">策略类型</span><span class="sxs-lookup"><span data-stu-id="bc5a6-226">Policy type</span></span></td>
<td align="left"><span data-ttu-id="bc5a6-227">活动策略</span><span class="sxs-lookup"><span data-stu-id="bc5a6-227">Activity policy</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc5a6-228">策略模板</span><span class="sxs-lookup"><span data-stu-id="bc5a6-228">Policy template</span></span></td>
<td align="left"><span data-ttu-id="bc5a6-229">无模板</span><span class="sxs-lookup"><span data-stu-id="bc5a6-229">No template</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc5a6-230">策略严重性</span><span class="sxs-lookup"><span data-stu-id="bc5a6-230">Policy severity</span></span></td>
<td align="left"><span data-ttu-id="bc5a6-231">高</span><span class="sxs-lookup"><span data-stu-id="bc5a6-231">High</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc5a6-232">类别</span><span class="sxs-lookup"><span data-stu-id="bc5a6-232">Category</span></span></td>
<td align="left"><span data-ttu-id="bc5a6-233">共享控制</span><span class="sxs-lookup"><span data-stu-id="bc5a6-233">Sharing Control</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc5a6-234">作用对象</span><span class="sxs-lookup"><span data-stu-id="bc5a6-234">Act on</span></span></td>
<td align="left"><span data-ttu-id="bc5a6-235">单个活动</span><span class="sxs-lookup"><span data-stu-id="bc5a6-235">Single activity</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc5a6-236">筛选设置</span><span class="sxs-lookup"><span data-stu-id="bc5a6-236">Filter settings</span></span></td>
<td align="left"><p><span data-ttu-id="bc5a6-237">活动类型 = 上传文件</span><span class="sxs-lookup"><span data-stu-id="bc5a6-237">Activity type = Upload File</span></span></p>
<p><span data-ttu-id="bc5a6-238">应用 = Microsoft OneDrive for Business 和 Box</span><span class="sxs-lookup"><span data-stu-id="bc5a6-238">App = Microsoft OneDrive for Business and Box</span></span></p>
<p><span data-ttu-id="bc5a6-239">分类标签（目前为个人预览版）：Azure 信息保护 = 客户数据、人力资源—薪资数据、人力资源—员工数据</span><span class="sxs-lookup"><span data-stu-id="bc5a6-239">Classification Label (currently in private preview): Azure Information Protection = Customer Data, Human Resources—Salary Data, Human Resources—Employee Data</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc5a6-240">警报</span><span class="sxs-lookup"><span data-stu-id="bc5a6-240">Alerts</span></span></td>
<td align="left"><p><span data-ttu-id="bc5a6-241">创建警报：已选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-241">Create an alert: checked</span></span></p>
<p><span data-ttu-id="bc5a6-242">每日警报限制：1000</span><span class="sxs-lookup"><span data-stu-id="bc5a6-242">Daily alert limit: 1000</span></span></p>
<p><span data-ttu-id="bc5a6-243">选择一个警报作为电子邮件：已选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-243">Select an alert as email: checked</span></span></p>
<p><span data-ttu-id="bc5a6-244">收件人：infosec@contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc5a6-244">To: infosec@contoso.com</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc5a6-245">治理</span><span class="sxs-lookup"><span data-stu-id="bc5a6-245">Governance</span></span></td>
<td align="left"><p><span data-ttu-id="bc5a6-246">所有应用</span><span class="sxs-lookup"><span data-stu-id="bc5a6-246">All apps</span></span></p>
<p><span data-ttu-id="bc5a6-247">隔离用户：选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-247">Put user in quarantine: check</span></span></p>
<p><span data-ttu-id="bc5a6-248">所有其他设置：未选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-248">All other settings: unchecked</span></span></p>
<p><span data-ttu-id="bc5a6-249">Office 365</span><span class="sxs-lookup"><span data-stu-id="bc5a6-249">Office 365</span></span></p>
<p><span data-ttu-id="bc5a6-250">隔离用户：选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-250">Put user in quarantine: check</span></span></p>
<p><span data-ttu-id="bc5a6-251">所有其他设置：未选中</span><span class="sxs-lookup"><span data-stu-id="bc5a6-251">All other settings: unchecked</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="bc5a6-252">类似策略：</span><span class="sxs-lookup"><span data-stu-id="bc5a6-252">Similar policies:</span></span>

-   <span data-ttu-id="bc5a6-253">检测客户数据或 HR 数据的大量下载 — 如果在较短时间段内检测到单个用户正在下载大量包含客户数据或 HR 数据的文件，则发出警报。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-253">Detect large downloads of Customer data or HR Data — Alert when a large number of files containing customer data or HR data have been detected being downloaded by a single user within a short period of time.</span></span>

-   <span data-ttu-id="bc5a6-254">检测客户和 HR 数据共享 — 共享包含客户或 HR 数据的文件时发出警报。</span><span class="sxs-lookup"><span data-stu-id="bc5a6-254">Detect Sharing of Customer and HR Data — Alert when files containing Customer or HR Data are shared.</span></span>
