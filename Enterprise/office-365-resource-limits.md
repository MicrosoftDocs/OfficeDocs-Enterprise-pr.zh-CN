---
title: Office 365 资源限制
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
description: 摘要：有关 Office 365 中各种应用程序的资源限制的信息。
ms.openlocfilehash: 112d910ae724ad01629aaef5a8e2e1756ceb8ecf
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844313"
---
# <a name="resource-limits"></a>资源限制

使用配额（限制）和限制来强制实施资源限制。 Azure Active Directory 和单独的 Office 365 服务使用两者。 在添加新功能时，限制因服务而异并随时间而变化。 有关各种服务的当前限制的详细信息，请参阅下列主题：

- [Azure Active Directory 服务限制和限制](https://msdn.microsoft.com/library/azure/dn764971.aspx)
- [Exchange Online 限制](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [Exchange Online Protection 限制](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [SharePoint Online 软件边界和限制](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [Skype for Business 限制](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [Yammer REST API 和速率限制](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Sway 中的文件大小限制](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

除了这些限制之外，在整个 Azure Active Directory 和 Office 365 中使用了多个限制机制。 如果 Microsoft 数据中心中的网络资源针对使用服务的广泛客户进行了优化，则服务中的限制尤为重要。 限制机制包括：

- Azure Active Directory 和 Office 365 功能用户级别限制，它限制单个用户可以执行的事务或并发呼叫（按脚本或代码）的数量。
- 在创建租户时，会为每个租户分配一个默认的 PowerShell 限制策略。 这些设置会影响其他项目，如一台管理员可打开的最大并发 PowerShell 会话数。
- 每个 Exchange Online 客户都有一个默认的 Exchange Web 服务（EWS）策略，该策略针对 EWS 客户端操作进行了优化，并具有适用于所有 Outlook 客户端的限制。
