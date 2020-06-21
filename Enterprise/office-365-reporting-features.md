---
title: Microsoft 365 报告功能
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-analytics
f1.keywords:
- NOCSH
description: Microsoft 365 中报告功能的说明。
ms.openlocfilehash: 1b8a75504712a46faa8b6fff8dfe20f3f3c6cf79
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774457"
---
# <a name="microsoft-365-reporting-features"></a>Microsoft 365 报告功能 

Microsoft 365 中的报告功能提供了 Azure Active Directory （Azure AD）、Exchange Online、设备管理、监管审核和数据丢失防护（DLP）的各种审核报告。 这些报告与 Microsoft 365 活动报告不同，彼此独立。

## <a name="microsoft-365-reports-dashboard"></a>Microsoft 365 报告仪表板

Microsoft 365 管理中心预览中的 "报告" 仪表板显示跨 Microsoft 365 的使用情况活动。 Microsoft 365 全局管理员或 Exchange Online、SharePoint Online 或 Skype for Business 管理员可以详细了解该服务的使用情况。 例如，特定 Microsoft 365 服务中的用户数、已为企业激活 Microsoft 365 应用程序的用户数（以前称为 Office 365 专业增强版）以及邮件在组织中的流动量。 报告可用于最近7、30、90和180天。

可以使用以下报告：

- [电子邮件活动报告](https://support.office.com/article/Office-365-Reports-in-the-admin-center-preview--Email-activity-1cbe2c00-ca65-4fb9-9663-1bbfa58ebe44)
- [Microsoft Office 激活报告](https://support.office.com/article/Office-365-Reports-in-the-admin-center-preview--Microsoft-Office-activations-87c24ae2-82e0-4d1e-be01-c3bcc3f18c60)
- [SharePoint Online 网站使用率报告](https://support.office.com/article/Office-365-Reports-in-the-admin-center-preview--SharePoint-site-usage-4ecfb843-e5d5-464d-8bf6-7ed512a9b213)
- [OneDrive for Business 使用率报告](https://support.office.com/article/Office-365-Reports-in-the-Admin-Center-Preview--OneDrive-for-Business-usage-0de3b312-c4e8-4e4b-a02d-32b2f726a680)
- [Yammer 活动报告](https://support.office.com/article/View-the-Yammer-Activity-report-in-the-Office-365-admin-center-preview-c7c9f938-5b8e-4d52-b1a2-c7c32cb2312a)
- [Skype for Business 活动报告](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online-reporting/activity-report)
- [Skype for Business 对等活动报告](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online-reporting/peer-to-peer-activity-report)
- [Skype for Business 会议组织者报告](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online-reporting/conference-organizer-activity-report)
- [Skype for Business 会议参与者活动报告](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online-reporting/conference-participant-activity-report)

有关详细信息，请参阅[Microsoft 365 管理中心中的活动报告](https://support.office.com/article/activity-reports-in-the-office-365-admin-center-0d6dfb17-8582-4172-a9a9-aed798150263)。

## <a name="azure-ad-reports"></a>Azure AD 报告

Microsoft 365 使用 Azure AD 进行身份验证和身份管理。 Microsoft 365 管理员使用 Azure 生成的报告来标识不寻常的活动，并对其数据进行未经授权的访问。 您可以使用 Azure AD 中的访问和使用情况报告深入了解组织的目录完整性和安全性。 使用此信息，您可以确定和缓解可能的安全风险。

Azure AD 报告可以导出到 Microsoft Excel，并与 Microsoft 365 中的其他数据相关联。 例如，审核日志搜索的结果可以深入了解访问、身份验证和应用程序级别的活动。 Azure AD Premium 提供了高级异常和资源使用情况报告。 这些高级报告可帮助您改善安全状态，并通过应用有关设备访问和应用程序使用情况的分析来帮助您响应潜在的威胁。 有关详细信息，请参阅[Azure Active Directory 报告](https://docs.microsoft.com/azure/active-directory/reports-monitoring/overview-reports/)。

## <a name="exchange-online-audit-reports"></a>Exchange Online 审核报告

Exchange Online 审核报告包含有关邮箱访问和管理员对 Exchange Online 租户所做更改的详细信息。 使用邮箱审核，您可以使用下表中的任务运行报告和导出 Exchange Online 审核日志。

> [!NOTE]
> 您必须为每个邮箱启用邮箱审核日志记录，以便将审核的事件保存在该邮箱的审核日志中。 如果没有为邮箱启用邮箱审核日志记录，则该邮箱的事件将不会保存在审核日志中，并且不会显示在邮箱审核报告中。 有关详细信息，请参阅[启用邮箱审核](https://support.office.com/article/Enable-mailbox-auditing-in-Office-365-aaca8987-5b62-458b-9882-c28476a66918)。

| Task | 说明 |
|----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [运行非所有者邮箱访问报告](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report) | 显示除邮箱所有者之外的其他人访问的邮箱的列表。 此报告包含有关访问邮箱的人员、他们在邮箱中执行的操作以及操作是否成功的信息。 |
| [导出邮箱审核日志](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs) | 邮箱审核日志包含有关邮箱所有者之外的用户所执行的邮箱中的访问和操作的信息。 管理员可以指定邮箱以及日期范围来生成报告。 日志以 XML 形式导出，并附加到邮件，并发送给由管理员确定的特定用户。 |
| [运行管理员角色组报告](https://docs.microsoft.com/Office365/SecurityCompliance/eop/run-an-administrator-role-group-report-in-eop-eop) | 管理员角色组为用户分配管理权限。 这些权限允许用户执行管理任务，如重置密码、创建或修改邮箱以及将管理员权限分配给其他用户。 管理员角色组报告显示对角色组的更改，包括添加或删除成员。 |
| [查看管理员审核日志](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log) | 管理员审核日志报告列出了由 Exchange Online 中的管理员执行的所有创建、更新和删除功能。 日志条目提供了有关运行的 cmdlet、使用的参数、运行 cmdlet 的执行者以及受影响对象的信息。 |
| [邮箱内容搜索和保留](https://docs.microsoft.com/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) | 提供对邮箱的就地电子数据展示或就地保留设置所做的任何更改的详细信息。 |
| [导出管理员审核日志](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes) | 管理员审核日志记录了 Exchange Online 中的创建、更新和删除等特定管理操作。 将日志中的结果导出到 XML，管理员可以选择将此日志发送给一组用户。 |
| [运行预邮箱诉讼保留报告](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/per-mailbox-litigation-hold-report) | 提供有关邮箱上的诉讼保留设置的任何更改的详细信息。 |
| [查看和导出外部管理员审核日志](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-external-admin-audit-log) | 包含由外部管理员执行的操作的详细信息。 这些条目提供了有关运行的 cmdlet、所使用的参数以及在 Exchange Online 中创建、修改或删除对象的任何操作的信息。 |

## <a name="device-compliance-reports"></a>设备合规性报告

您可以使用 Microsoft 365 移动设备管理（MDM）管理和安全连接到订阅的移动设备。 用于访问工作电子邮件、日历、联系人和文档的移动设备在确保员工随时能够随时随地工作的过程中起着重要的作用。 保护组织的信息非常关键。 您可以使用 Microsoft 365 MDM 设置设备安全策略和访问规则。 如果丢失或被盗，还可以使用 Microsoft 365 MDM 来擦除移动设备。

MDM 合规性报告提供组织设置的用于保护访问 Microsoft 365 数据的移动设备的策略的概述。 此报告允许按符合性状态、报告的冲突、阻止的设备以及由于安全策略而擦除的设备来筛选设备。 有关详细信息，请参阅[适用于 Microsoft 365 的移动设备管理概述](https://support.microsoft.com/office/overview-of-mobile-device-management-mdm-for-microsoft-365-faa7d8e5-645d-4d59-839c-c8d4c1869e4a)。

## <a name="data-loss-prevention"></a>数据丢失防护

DLP 策略可帮助管理组织中信息的安全性和流动。 您可以设置策略以阻止对内容的访问、加密数据，或使用应用程序中的 DLP 策略提示通知用户策略和策略违规。 DLP 报告提供了有关策略和规则匹配数、覆盖和误报的见解。

您可以使用 Microsoft 365 管理中心来查看您的 DLP 策略检测到的邮件数量的相关信息。 DLP 报告提供了对发送和接收的邮件的策略和规则匹配的见解。 您还可以使用 Exchange 管理中心查看过去24小时内每个策略的匹配项、重写次数和误报数。 如果下载 Excel 报告，您可以查看更多详细信息，例如谁发送哪一封邮件，哪天，哪些策略匹配被触发。 有关详细信息，请参阅[查看有关 DLP 策略检测的报告](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/jj889415(v=exchg.150))。

## <a name="auditing-in-yammer-enterprise"></a>Yammer 企业版中的审核

Yammer Enterprise 为管理员提供了通过[yammer 数据导出 API](https://support.office.com/article/export-data-from-yammer-enterprise-b303d8f3-007d-4ad4-81f8-54fb1ecfb3f2)从其 yammer 网络导出用户活动数据的功能，或通过 yammer 网络管理页面手动导出的功能。 将日志导出的功能仅限于 Yammer 中的网络管理员。 （所有 Microsoft 365 全局管理员都是 Yammer 网络管理员。）

可导出以下数据：

| Filename | 说明 |
|----------------------------|-------------------------------------------------------------------------|
| Users.csv | 网络中的所有新的、挂起的和挂起的用户 |
| Messages.csv | 网络中的所有邮件 |
| Files.csv （元数据） | 元数据，如文件名、文件 API URL、上载 ID、上载位置等。 |
| Files.csv （原始文件） | 用户上载到 Yammer 中的原始文件的 Zip 文件 |
| Topics.csv | 在网络上创建的主题 |
| Pages.csv | 用户在网络中创建的页面（注释） |
| Admins.csv | 网络中所有已验证的管理员 |
| Networks.csv | 所有 Yammer 外部网络 |

Yammer Enterprise 数据也可通过 Microsoft 365 活动报告获得。 此外，Yammer 正在主动处理通过 Microsoft 365 管理活动 API 公开其他日志记录的功能，以及使用 Power BI 对数据的原因的功能。 有关这些功能的详细信息，请参阅[Office 路线图](https://fasttrack.microsoft.com/roadmap?filters=yammer)。
