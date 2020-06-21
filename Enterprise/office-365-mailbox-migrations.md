---
title: Microsoft 365 邮箱迁移
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
description: 用于 Microsoft 365 邮箱迁移的 cmdlet 的简短摘要。
ms.openlocfilehash: 4c53737f4047df0751c4216b57d772bd6fe8acad
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774897"
---
# <a name="microsoft-365-mailbox-migrations"></a>Microsoft 365 邮箱迁移

通过基于 Exchange 的混合部署，客户可以选择将本地 Exchange 邮箱移动到[Exchange online](https://docs.microsoft.com/Exchange/exchange-online)组织，或将 exchange Online 邮箱移动到[exchange 内部部署](https://docs.microsoft.com/Exchange/exchange-server)组织。 在内部部署组织和 Exchange Online 组织之间移动邮箱时使用迁移批处理。

客户可以使用以下 cmdlet 查看有关邮箱迁移的统计信息和其他信息：

- [Get-moverequeststatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequestStatistics?view=exchange-ps)：提供用户邮箱的默认统计信息，其中包括状态、邮箱大小、存档邮箱大小和完成百分比。
- [Get 邮箱](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-Mailbox?view=exchange-ps
)：提供组织中的邮箱对象和属性的摘要列表。
- "[获取-收件人](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient?view=exchange-ps)：" 提供现有的已启用邮件的对象（如邮箱、邮件用户、联系人和通讯组）的列表。
- [New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequest?view=exchange-ps)：提供正在进行的邮箱迁移的详细状态。
- [Get-migrationuser](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUser?view=exchange-ps)：提供有关邮箱移动和迁移用户的信息。
- [New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationBatch?view=exchange-ps)：提供有关当前迁移批处理的状态信息。
- [Get-migrationuserstatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUserStatistics?view=exchange-ps)：提供有关特定用户的迁移状态的详细信息。
- [Get-mailboxstatistics](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-MailboxStatistics?view=exchange-ps)：提供有关邮箱的信息，如大小、邮件数以及上次访问时间。

有关 cmdlet 的详细信息，请参阅[Exchange Online 中的移动和迁移 cmdlet](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps)。
