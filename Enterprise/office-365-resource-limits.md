---
title: Microsoft 365 资源限制
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
f1.keywords:
- NOCSH
description: 在本文中，您可以找到有关 Microsoft 365 中各种应用程序的资源限制的信息。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4d2e7987620891ddeac2c4fa08aaeb203f001f57
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606298"
---
# <a name="resource-limits"></a>资源限制

使用配额来强制执行资源限制 (限制) 和限制。 Azure Active Directory (Azure AD) 和各个 Microsoft 365 服务使用这两者。 在添加新功能时，限制因服务而异并随时间而变化。 有关各种服务的当前限制的详细信息，请参阅下列主题：

- [Azure AD 服务限制和限制](https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits)
- [Exchange Online 限制](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [Exchange Online Protection 限制](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [SharePoint Online 软件边界和限制](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [Skype for Business 限制](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [Yammer REST API 和速率限制](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Sway 中的文件大小限制](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

除了这些限制之外，还需要在 Azure AD 和 Microsoft 365 中使用多个限制机制。 如果 Microsoft 数据中心中的网络资源针对使用服务的广泛客户进行了优化，则服务中的限制尤为重要。 限制机制包括：

- Azure AD 和 Microsoft 365 功能用户级别限制，它限制由单个用户可以执行的脚本或代码)  (的事务或并发调用的数量。
- 在创建租户时，会为每个租户分配一个默认的 PowerShell 限制策略。 这些设置会影响其他项目，如一台管理员可打开的最大并发 PowerShell 会话数。
- 每个 Exchange Online 客户都具有默认的 Exchange Web 服务 (EWS) 策略，该策略针对 EWS 客户端操作进行了优化，并且限制适用于所有 Outlook 客户端。
