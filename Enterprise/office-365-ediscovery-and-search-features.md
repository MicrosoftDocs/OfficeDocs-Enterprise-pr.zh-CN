---
title: Microsoft 365 电子数据展示和搜索功能概述
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
f1.keywords:
- NOCSH
description: Microsoft 365 中的电子数据展示功能和其他搜索功能的概述，用于审核使用和透明度。
ms.openlocfilehash: f4c401bf81767eb9111e6e8ca508cc3ee87152db
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906185"
---
# <a name="microsoft-365-ediscovery-and-search-features-overview"></a>Microsoft 365 电子数据展示和搜索功能概述 

## <a name="ediscovery"></a>电子数据展示

电子数据展示功能为管理员、合规专员和其他授权用户提供了单一位置，以在 Microsoft 365 用户活动中进行全面调查。 具有相应权限的安全主管对内容执行搜索和就地保留。 搜索结果与从内容搜索中获取的结果相同，只是为任何应用的保留创建电子数据展示事例。 来自电子数据展示搜索的结果将针对安全性进行加密，并且您可以使用[高级电子数据展示](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20)分析导出的数据。

## <a name="content-search"></a>内容搜索

[内容搜索](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a)是一个电子数据展示搜索工具，它通过以前的电子数据展示搜索工具提供改进的扩展和性能功能。 您可以使用内容搜索来搜索邮箱、公用文件夹、SharePoint Online 网站和 OneDrive for business 位置。 内容搜索支持大型搜索。 对可以搜索的邮箱数和网站数没有限制。 同时也没有对同时运行的搜索数量的限制。 运行搜索后，内容源的数量和估计的搜索结果数将显示在 "搜索" 页上的 "详细信息" 窗格中。 您可以预览结果，也可以将其导出到本地计算机。 如果您的组织拥有 Microsoft 365 E5 订阅，则可以使用[microsoft 365 高级电子数据展示](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20)的强大分析功能来准备要分析的[结果](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a#prepare)。

## <a name="audit-log-search"></a>审核日志搜索

除了在 Microsoft 365 组织中跟踪更改之外，您还可以查看审核报告和导出审核日志。 一旦将审核启用为 Microsoft 365 租户，用户和管理活动将记录在事件日志中并使其可供搜索。 例如，您可以使用邮箱审核日志记录来跟踪邮箱所有者之外的用户对邮箱执行的操作。 合规性监察官可以对特定用户活动使用搜索和筛选功能。 例如，确定查看或下载特定文档的用户，如果管理员已执行用户管理活动，或查看在过去的90天内租户配置中的更改。 搜索结果包含有关用户或管理员执行的特定活动的有价值的取证信息。 有关在 Microsoft 365 中记录的用户和管理活动的说明，请参阅[搜索审核日志](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance)。

SharePoint Online 和 OneDrive for business 中的事件在发生30分钟的时间内显示在日志中。 来自 Exchange Online 的事件出现在发生的24小时内的审核日志中。 来自 Azure AD 的登录事件在发生几分钟内可用，并且来自 Azure AD 的其他目录事件在发生24小时内可用。 您可以在审核日志搜索结果中导出通风口以供进一步分析。 从单个审核日志搜索中，最多可以导出50000个条目。 若要导出此限制的更多条目，请减少日期范围或运行多个审核日志搜索。

下表详细介绍了活动报告中显示的一些信息。 有关每个 Microsoft 365 工作负荷收集的属性的详细信息，请参阅[审核日志中的详细属性](https://docs.microsoft.com/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log)。

| 属性 | 说明 |
|----------------|----------------------------------------------------------------------------------------------------------------------|
| 日期 | 事件的日期和时间 |
| 用户 | 执行操作的用户 |
| ClientIP | 记录活动时使用的设备的 IPv4 或 IPv6 地址。 |
| CreationTime | 用户执行活动时的日期和时间（采用协调通用时间（UTC））。 |
| EventSource | 标识发生的事件。 可能的值为 SharePoint 和 ObjectModel。 |
| ID | 报告条目的 ID。 ID 唯一标识报告条目。 |
| 操作 | 用户或活动的名称，对应于在 "此用户活动的显示结果" 中选择的值。 |
| OrganizationId | 发生事件的组织的 Microsoft 365 服务的 GUID。 |
| UserAgent | 浏览器提供的有关用户浏览器的信息。 |
| UserId | 执行操作（在 Operation 属性中指定）导致记录记录的用户。 |
| UserType | 执行操作的用户的类型。 以下值指示用户类型。 |
|  | 0表示常规用户。 |
|  | 2表示 Microsoft 365 组织中的管理员。 |
|  | 3表示 Microsoft 数据中心管理员或数据中心系统帐户。 |
| Workload | 发生活动的 Microsoft 365 服务。 此属性的可能值为： |
|  | Exchange Online |
|  | SharePoint Online |
|  | OneDrive for Business |
|  | Azure Active Directory 报告 |

有关搜索 Microsoft 365 审核日志的详细步骤，请参阅[在 Security & 合规性中心中搜索审核日志](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance)。

## <a name="search-unified-audit-log"></a>搜索统一审核日志

使用审核日志搜索功能搜索统一审核日志。 Microsoft 365 还提供了使用远程 PowerShell 搜索此日志的功能。 Exchange Online PowerShell 中的[UnifiedAuditLog cmdlet](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/Search-UnifiedAuditLog?view=exchange-ps)用于搜索与来自 Exchange Online、SharePoint Online、OneDrive for Business 和 Azure AD 的用户操作相关的事件的统一审核日志。 

您可以搜索指定日期范围内的所有事件，也可以根据特定条件（如特定操作、执行操作的用户或目标对象）筛选结果。 管理员最多可以使用三个同时运行的 Exchange Online PowerShell 会话拆分大量的日期范围搜索。