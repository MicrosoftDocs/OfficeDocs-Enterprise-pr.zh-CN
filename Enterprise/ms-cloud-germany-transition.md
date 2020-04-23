---
title: 从德国 Microsoft 云迁移到新的德国数据中心区域内的 Office 365 服务
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 摘要：了解如何从德国 Microsoft 云迁移到新的德国数据中心区域内的 Office 365 服务
ms.openlocfilehash: 7e9ba9135d024be5c12d6ca19b55ec68588d9ab4
ms.sourcegitcommit: cf92870078d971ae8e36b75bd35f4b8f36ec7a50
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "43772143"
---
# <a name="migration-from-microsoft-cloud-germany-microsoft-cloud-deutschland-to-office-365-services-in-the-new-german-datacenter-regions"></a>从德国 Microsoft 云迁移到新的德国数据中心区域内的 Office 365 服务


>[!Note]
>本文仅适用于符合条件的 德国 Microsoft 云客户。
>

## <a name="cloud-service-offerings-in-germany"></a>在德国提供的云服务

2018 年 8 月，我们宣布计划在新的德国云区域中提供完整的 Microsoft 云（Azure、Office 365、Dynamics 365 和 Power Platform），目的是更好地实现客户的数字化转型。 2019 年 8 月，我们宣布已启动在德国开放新的云区域的流程。 我们宣布在 8 月推出 Azure，在 12 月推出 Office 365。  预计在 2020 年第 1 季度提供 Dynamics 365 和 Power Platform。  

新区域提供更高的灵活性、最新的智能云服务、到我们的全球云网络的完整连接，以及在德国驻留客户数据的服务，旨在应对德国客户不断增长的需求。

## <a name="moving-to-the-new-german-regions"></a>移到新的德国区域

现有德国 Microsoft 云客户现可开始迁移其 Office 365、Dynamics 365 Customer Engagement 和 ower Platform BI 客户。  首先要[选择采用 Microsoft 引导的迁移](https://aka.ms/office365germanymoveoptin)方法，迁移到新的德国数据中心区域。

对于选择采用 Microsoft 提出的方法的组织，预计在 2020 年进行迁移。 迁移后，核心客户数据和订阅会迁移到新的德国区域。 

下列服务将采用 Microsoft 提出的方法进行迁移：

- Azure Active Directory
- Exchange Online
- Exchange Online Protection
- SharePoint Online
- OneDrive for Business
- Skype for Business Online

从德国 Microsoft 云迁移到德国数据中心期间，现有 Skype for Business Online 客户将过渡到 Microsoft Teams。 有关详细信息，请参阅[开始 Microsoft Teams 升级](https://aka.ms/SkypeToTeams-Home)。

- Office 365 组
- Dynamics 365/Power Platform

有关迁移这些服务的先决条件及其影响，可参阅 [Dynamics 365 Customer Engagement](https://aka.ms/D365ceOptIn) 文章。

## <a name="how-to-prepare-for-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>如何做好准备以迁移到新的德国数据中心区域内的 Office 365 服务

首先是要通知 Microsoft，以便我们获得你的授权，可将你的订阅和数据从德国 Microsoft 云迁移到新的德国数据中心区域内的 Office 365 服务。  有关说明，请参阅[“选择加入”过程](ms-cloud-germany-migration-opt-in.md)。

- 所有正在迁移的客户都需要验证到全球 [Office 365 URL 和 IP 地址](urls-and-ip-address-ranges.md)（包括新的德国数据中心区域）的连接。
- 请查看 Office 365 平台服务说明，了解在完成到德国区域的迁移后哪些功能和服务可供你的组织使用。 
- 迁移将切换付费订阅。  我们无法迁移试用版订阅。

租户迁移以后端服务操作的形式执行，需要的客户互动程度最低。  在迁移过程中，消息中心将显示客户引导的所有其他任务和整体迁移状态。  例如，任务可能包括客户管理的 DNS 更新或 Exchange 混合客户的混合设置的重新配置。

## <a name="customer-experience-during-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>在迁移到新的德国数据中心区域内的 Office 365 服务期间的客户体验

租户迁移的目标是将对终端客户和管理员的影响降至最低。  但是，每个工作负载都有注意事项。  

### <a name="azure-active-directory"></a>Azure Active Directory

通过 Azure Active Directory (Azure AD) 重新定位，来自德国 Microsoft 云的 Office/Dynamics 订阅会过渡到德国区域中。 然后，组织会进行更新，以反映出新的全球服务订阅。 在简短的订阅转移过程中，将阻止更改订阅。

### <a name="exchange-online"></a>Exchange Online

Exchange Online 混合客户必须在过渡之前重新运行混合配置向导，对照德国 Microsoft 云更新本地配置，并在针对全球服务进行清理时重新执行 HCW。 对于具有自定义域的客户，可能需要其他 DNS 更新。

邮箱以后端进程的形式进行迁移，你组织中的用户在过渡期间可能位于德国 Microsoft 云中，也可能位于德国区域中，而且这些用户属于同一 Exchange 组织 (GAL)

### <a name="exchange-online-protection"></a>Exchange Online Protection

后端 Exchange Online Protection 功能会复制到新的德国区域

### <a name="sharepoint-online"></a>SharePoint Online

在将 SharePoint Online 迁移到德国区域之后，会重新生成数据索引。 在重建索引完成后，依赖搜索索引的功能可能会受到影响。

现有 sharepoint.de URL 会保留供已过渡的组织使用。

### <a name="onedrive-for-business"></a>OneDrive for Business

在将 OneDrive for Business 迁移到德国区域之后，会重新生成数据索引。 在重建索引完成后，依赖搜索索引的功能可能会受到影响。

### <a name="skype-for-business-online"></a>Skype for Business Online

现有 Skype for Business Online 客户将过渡到 Microsoft Teams。 有关详细信息，请参阅 [https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home)。


## <a name="key-differences-between-microsoft-cloud-germany-microsoft-cloud-deutschland-and-office-365-services-in-the-new-german-datacenter-regions"></a>德国 Microsoft 云与新的德国数据中心区域内的 Office 365 服务之间的主要区别


|| 德国 Microsoft 云 | 新的德国数据中心区域内的 Office 365 服务 |
|:-------|:-----|:-----|
| Microsoft 365 服务适用于只有一个 Office 365 租户的订阅 | 15 项服务（请参见 REF） | 29 项服务（请参见 REF） |
| 新增功能 | 不提供任何新功能。 | 新功能的可用性将与全球 Office 365 服务的保持一致。 |
| 数据受托人 | 是 | 否 |
| 与全球 Office 365 租户跨租户协作 | 否 | 是 |
| 客户数据驻留 | 客户数据将仅存储在德国数据中心。 | Microsoft 将在德国存储下列静态客户数据：Exchange Online 邮箱内容（电子邮件正文、日历项和电子邮件附件内容）、SharePoint Online 网站内容及该网站中存储的文件，以及上传到 OneDrive for Business 的文件。 |
| 适用条款 | [在线服务条款](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46)（带[补充条款](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64)） | [在线服务条款](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="frequently-asked-questions"></a>常见问题解答

### <a name="is-migration-required"></a>是否需要迁移？

Microsoft 准许客户免费将Office 365 租户从德国 Microsoft 云迁移到新的德国数据中心区域内的 Office 365 服务。  我们强烈建议你选择迁移到新的德国数据中心区域，但我们也将继续对德国 Microsoft 云区域提供必要的安全更新。  

新的德国数据中心区域内的 Office 365 服务还具有以下优势：

- 为 [Azure](https://azure.microsoft.com/pricing/calculator/)、[Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans)、[Dynamics 365 Customer Engagement](https://dynamics.microsoft.com/pricing/) 和 [Power BI](https://powerbi.microsoft.com/pricing/) 提供具有市场竞争力的定价。 
- 与 Microsoft 全球网络相连，提供数百个网络边缘网站、对等互连位置和出口点，以在全球任何位置提供可靠的用户体验。 
- 帮助你满足德国境内的当地客户数据驻留要求。 
- 提供我们具备完整功能的全球云服务/产品，包括服务的最新版本以及 Microsoft Teams 和 Office 365 多地理位置等新功能。 按 [Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central)、、[Office 365](https://products.office.com/zh-CN/where-is-your-data-located) 和 [Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability) 的区域比较产品。
- 提供完备功能、企业级安全性和全面的功能，帮助客户满足合规性和法规要求。 
- 可通过现有在线服务合同访问。

#### <a name="what-is-the-service-availability-between-the-different-office-365-cloud-service-offerings"></a>不同 Office 365 云服务方案中的服务可用性是什么？

德国 Microsoft 云服务方案提供下列 15 项服务。  未添加新服务至德国 Microsoft 云。

1. Exchange Online
2. 客户密码箱 (Exchange Online)
3. 组（新式组）
4. Delve 配置文件
5. Exchange Online Protection
6. 高级威胁防护 (ATP)
7. 高级电子数据展示
8. 高级数据管理
9. SharePoint Online
10. 客户密码箱 (SharePoint Online)
11. OneDrive for Business
12. Skype for Business
13. Word Online、Excel Online、PowerPoint, OneNote、Visio Online
14. Office 365 专业增强版
15. Outlook Mobile

目前，新的德国数据中心区域提供 29 项服务，是 Office 365 服务的一部分。  新功能和服务的可用性将持续与全球 Office 365 服务的保持一致。

1. Exchange Online
2. 客户密码箱 (Exchange Online)
3. 组（新式组）
4. Delve 配置文件
5. MyAnalytics
6. 工作区分析
7. Exchange Online Protection
8. 高级威胁防护 (ATP)
9. 高级电子数据展示
10. 高级安全管理
11. 信息权限管理
12. 高级数据管理
13. SharePoint Online
14. 客户密码箱 (SharePoint Online)
15. OneDrive for Business
16. Microsoft Stream
17. Skype for Business（迁移期间过渡到 Microsoft Teams）
18. 云 PBX
19. PSTN 会议
20. PSTN 呼叫
21. Microsoft Teams
22. 管理员报告/使用率报告
23. Word Online、Excel Online、PowerPoint、OneNote 和 Visio Online
24. 规划器
25. Sway
26. Office 365 专业增强版
27. Outlook Mobile
28. EMS E3（Azure Active Directory Premium P1 + Intune + 权限管理服务）
29. Yammer Online

### <a name="when-will-migration-happen"></a>何时将进行迁移？

#### <a name="azure"></a>Azure 

可立即开始将你的 Azure 资源[迁移](https://docs.microsoft.com/azure/germany/germany-migration-main)到另一区域。 如果你有带 Office 365、Dynamics 365 和/或 Power BI 的 Azure，请按照下述步骤操作。

#### <a name="office-365"></a>Office 365

立即[选择加入](https://aka.ms/office365germanymoveoptin)以执行 Microsoft 引导的迁移。 在我们准备好开始你的迁移时，我们将通过 Microsoft 365 管理中心内的[消息中心](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide)通知你。

#### <a name="dynamics-365-and-power-bi"></a>Dynamics 365 和 Power BI

对于 [Dynamics 365 Customer Engagement](https://aka.ms/D365ceOptIn) 和 [Power BI](https://aka.ms/pbioptin)，请立即选择执行 Microsoft 引导的迁移。 在我们准备好开始你的迁移时，我们将通过 Microsoft 365 管理中心内的[消息中心](https://docs.microsoft.com/office365/admin/manage/message-center?view=o365-worldwide)通知你。

### <a name="will-the-price-change-for-the-office-services-that-i-use"></a>我使用的 Office 服务的价格将出现变化吗？

是，Microsoft 全球云区域（包括新的数据中心区域）中的定价普遍更低。

### <a name="how-do-i-get-help-from-microsoft-to-migrate-to-a-new-region-or-answer-support-questions"></a>我可如何获取帮助，让 Microsoft 帮我迁移到新的区域或解答支持问题？

如有疑问，可通过下述方式联系我们，也可通过你的合作伙伴进行联系：

- 对于 Azure，可在 Azure 门户提交[新的支持请求](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest)。
- 对于 Office 365，可通过 [Microsoft 365 管理中心](https://portal.office.de/)的“需要帮助?”提交问题。
- 对于同时具备 Office 365 的 Dynamics 365 Customer Engagement 和 Power BI 客户，可通过 [Microsoft 365 管理中心](https://portal.office.de/)的“需要帮助?”提交问题。 有关 Dynamics 365 Customer Engagement 支持选项，可查看[此处](https://docs.microsoft.com/dynamics365/get-started/support/)。 有关 Power BI 支持选项，可查看[此处](https://powerbi.microsoft.com/support/)。

## <a name="more-information"></a>更多信息

- [德国 Microsoft 云迁移助手](https://aka.ms/germanymigrateassist)
- [如何选择加入迁移](https://aka.ms/office365germanymoveoptin)
- [Dynamics 365 迁移计划信息](https://aka.ms/D365ceOptIn)
- [Power BI 迁移计划信息](https://aka.ms/pbioptin)
- [Office 365 URL 和 IP 地址范围](https://aka.ms/o365endpoints)
- [Office 365 混合配置向导](https://aka.ms/HybridWizard)
- [开始 Microsoft Teams 升级](https://aka.ms/SkypeToTeams-Home)
