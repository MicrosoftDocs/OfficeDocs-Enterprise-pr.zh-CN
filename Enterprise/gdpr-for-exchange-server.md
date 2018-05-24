---
title: 用于 Exchange Server 的 GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解如何解决本地 Exchange Server 中的 GDPR 要求。
ms.openlocfilehash: cf6d670134bd4aab60b97cd9f55e69a21ce06b19
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-exchange-server"></a>用于 Exchange Server 的 GDPR

作为保护个人信息的一部分，我们建议如下：

-   使用 Exchange Server 中的[保留标记和策略](https://technet.microsoft.com/library/dd297955(v=exchg.160).aspx)以实施电子邮件生命周期策略。

-   部署[信息权限管理](https://technet.microsoft.com/library/dd638140(v=exchg.160).aspx)以限制谁可以访问存储在 Exchange Server 中的信息。

-   在服务器上启用 [BitLocker 加密](https://blogs.technet.microsoft.com/exchange/2015/10/20/enabling-bitlocker-on-exchange-servers/)。

## <a name="identifying-in-scope-content"></a>标识范围内的内容

Exchange 为最终用户生成的内容使用两个主存储库：邮箱和公用文件夹。存储在单个用户邮箱中的内容与该用户唯一关联，并表示其在 Exchange 中的默认存储库。存储在用户邮箱中的数据包括使用 Outlook、Outlook 网页版（以前称为 Outlook Web App）、Exchange ActiveSync、Skype for Business 客户端以及使用 POP、IMAP 或 Exchange Web 服务 (EWS) 连接到 Exchange 服务器的其他第三方工具创建的内容。这些项目的例子包括：邮件、日历项目（会议和约会）、联系人、笔记和任务。删除单个用户的邮箱会删除由用户在其邮箱上下文中生成或直接发送给用户的内容。可以使用 Exchange 管理中心 (EAC) 或 Exchange 命令行管理程序中的 [Remove-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/remove-mailbox?view=exchange-ps) cmdlet 删除用户邮箱。\
注意：如果使用此选项，应该谨慎使用 Remove-Mailbox cmdlet 中的 Permanent 参数，因为数据将无法恢复。

Exchange 还提供共享邮箱，允许一个或多个用户具有发送和接收存储在公共邮箱中的内容的访问权限。共享邮箱是与单个帐户无关的唯一实体。相反，多个用户被授予访问权限以发送、接收和查看共享邮箱中的电子邮件内容。共享邮箱使用 Exchange 管理中心和用于管理常规用户邮箱的相同 cmdlet 进行管理。如果你需要从邮箱中删除单个邮件，则可以根据 Exchange 的版本使用不同的选项。在 Exchange Server 2010 和 2013 中，可以使用带有 DeleteContent 参数的 [Search-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/search-mailbox?view=exchange-ps) cmdlet 标识并删除邮箱中的邮件。在 Exchange Server 2016 及更高版本中，需要使用 [New-ComplianceSearch](https://technet.microsoft.com/library/ff459253(v=exchg.160).aspx) 功能。

公用文件夹是与特定用户无关的共享存储实施。相反，授予用户访问公用文件夹以生成内容的权限。公用文件夹的实际实施因 Exchange 版本而异（Exchange Server 2010 使用与 Exchange Server 2013 及更高版本不同的实施）。存在有限的工具来管理公用文件夹中的内容。客户端工具（例如 Outlook）是用来管理公用文件夹内容的主要机制。有用于管理公用文件夹对象的 cmdlet，但不用于管理公用文件夹中的单个内容项。可能需要利用 Exchange Web 服务 (EWS) 或其他第三方工具的自定义脚本来管理单个公用文件夹项目。

主要要求可能是管理个人用户邮箱内容。通过经常用于管理邮箱的基于图形或 cmdlet 的工具可以轻松解决此需求。如果需要跨多个邮箱或多种类型的资源处理内容，[电子数据展示](https://technet.microsoft.com/library/dd298021(v=exchg.160).aspx)是 Exchange 中用于识别范围内内容的首选机制。

## <a name="deleted-item-retention"></a>已删除项目的保留时间

从邮箱中删除单个邮件或项目（而不是整个邮箱或公用文件夹资源本身）时，将根据邮箱数据库或公用文件夹数据库的 DeletedItemRetention 参数值以可恢复的形式保留内容。默认值为 14 天，但此值可由 Exchange 管理员配置。

## <a name="removing-soft-deleted-and-disconnected-mailboxes"></a>删除软删除和断开连接的邮箱

如果禁用、删除或在数据库之间移动 Exchange 邮箱（例如作为负载平衡的一部分），邮箱将根据操作置于禁用、软删除或断开状态。当邮箱处于任何一种状态时，Exchange 会根据邮箱数据库上指定的 MailboxRetention 参数的当前值维护邮箱（包括其内容）。默认值为 30 天，但此值可由 Exchange 管理员配置。可以使用 [Remove-StoreMailbox](https://docs.microsoft.com/powershell/module/exchange/mailbox-databases-and-servers/remove-storemailbox?view=exchange-ps) cmdlet 强制 Exchange 在保留期自然到期之前永久删除（清除）与邮箱关联的所有数据。

> [!IMPORTANT]
> 请谨慎使用 Remove-StoreMailbox cmdlet，因为它会导致目标邮箱的数据丢失且不可恢复。 

## <a name="on-prem-to-cloud-migrations"></a>本地到云的迁移

在将数据从 Exchange Server 迁移到 Exchange Online 时，迁移的数据可能会继续以 Exchange 管理员可恢复的形式驻留在本地源 Exchange Server 上。默认情况下，这些数据将在 30 天内自动从数据库中删除（请参阅上面的“删除软删除和断开连接的邮箱”部分）。

## <a name="automatic-data-collection-reported-to-microsoft-by-exchange-server"></a>自动数据收集由 Exchange Server 报告给 Microsoft

部署在本地环境中的 Exchange Server 不会向 Microsoft 提供任何类型的自动报告或最终用户数据捕获。在 Windows 操作系统中启用了 Watson 故障转储报告的 Exchange Server 在生成故障报告时可能会收到有限的内存内容。
