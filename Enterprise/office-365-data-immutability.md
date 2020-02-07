---
title: Office 365 数据永久性
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
- M365-security-compliance
f1.keywords:
- NOCSH
description: 定义并解释 Office 365 中的数据永久性。
ms.openlocfilehash: 8e52d1be87bff163b2d1cfc9233de08861104681
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844513"
---
# <a name="immutability-in-office-365"></a>Office 365 中的永久性

法规遵从性、内部治理要求或诉讼风险要求组织将电子邮件和相关数据保存在可检测到的表单中。 系统中的所有数据都必须可检测到，且不能销毁或更改。 本行业标准术语是 "不可变性" 的。

传统的不可变性方法通常通过将电子邮件移动到单独的只读存储位置来实现。 虽然此类系统提供了保留邮箱项以供发现的目的，但它们通常会通过从习惯的日常工作流中删除保留的项目来影响用户体验。 对于 IT 专业人员，这种永久性方法需要对单独的服务器和存储基础结构进行部署和日常维护。 使用邮件系统外部的工具执行发现，并包括关联的部署和维护成本。

通过在 Office 365 及其服务中进行存档的就地保留和保留策略功能，可以保留和保留许多类的传入、内部和传出数据。 这包括：

- 入站和出站电子邮件通信
- 包含在电子邮件表单或共享联机文档中的书籍和记录
- 会议请求
- 早
- 即时消息
- 联机会议期间共享的文档
- Voicemails

此外，Microsoft 还开发了附加功能，通过与第三方数据捕获和管理解决方案集成，允许从其他来源[存档数据](https://support.office.com/article/Archiving-third-party-data-in-Office-365-0ce338d5-3666-4a18-86ab-c6910ff408cc)。 导入第三方数据后，可以将 Office 365 合规性功能应用于数据，包括：

- [诉讼保留](https://docs.microsoft.com/microsoft-365/compliance/create-a-litigation-hold)
- [就地电子数据展示和保留](https://docs.microsoft.com/microsoft-365/compliance/manage-legal-investigations)
- [合规性搜索](https://docs.microsoft.com/microsoft-365/compliance/search-for-content)
- [就地存档](https://docs.microsoft.com/microsoft-365/compliance/enable-archive-mailboxes)
- [邮箱审核](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing)
- [保留策略](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)

例如，当将邮箱置于诉讼保留状态时，将保留第三方数据。 您可以使用就地电子数据展示或合规性搜索来搜索第三方数据。 或者，您可以将存档和保留策略应用于第三方数据，就像 Microsoft 数据一样。 在 Office 365 中存档第三方数据可帮助您的组织遵守政府和法规策略。

Office 365 中的存档提供有价证券和 Exchange 委员会（SEC）规则17a-4 兼容的存储。 Office 365 保留使用就地保留策略和保留策略（包括保留锁定）以不可改写、不可擦除的格式收集的所有数据的永久文件。

具体来说：

- 使用以上所述的保留策略存储的所有记录将保留在普通用户的 purview 的专用存储区域中。 只有授权用户可以访问和搜索这些记录，但不能更改或清除它们。
- 每个项目的元数据包括用于计算保留期的时间戳。 在接收或创建新项目时应用时间戳，不能在元数据中对其进行修改或将其删除。
- Office 365 中的存档允许用户将不同的保留策略和保留操作组合在一起，以创建精确的保留策略。 这些策略定义保留项目的类型或位置以及保留时间。
- 保留锁定功能允许用户选择是否将策略设为限制性策略。 限制性策略禁止任何人能够删除、禁用或对保留策略进行任何更改。 这意味着，一旦启用了保留锁定，就不能禁用它，并且不会存在任何机制，在此过程中，可能会覆盖、修改、清除或删除保留策略所收集的现有保管人中的任何数据。保留期。 此外，保留锁设置的保留期可能不会缩短或减少。 但是，如果法律要求继续保留所存储的数据，则可能会延长此时间，如上文所述。 保留锁定可确保任何人（甚至不是管理员或具有特定控制访问权限的管理员）都可能会更改设置或覆盖或擦除已存储的数据，从而使 Office 365 中的存档与 SEC 2003 版本中提出的指导相结合规则17a-4。

若要了解 Office 365 如何帮助您满足法规义务（尤其是与规则17a-4 要求相关），请参阅本[白皮书](https://go.microsoft.com/fwlink/?linkid=830440)，其中包括 Exchange Online 存档、SharePoint Online、OneDrive for Business 和 Skype for business。 该白皮书还提供了对 Office 365 存档功能和功能的深入分析，以根据 SEC Rule 17a-4 中的每个要求，向管控客户演示 Office 365 存档如何使他们能够满足这些要求满足.