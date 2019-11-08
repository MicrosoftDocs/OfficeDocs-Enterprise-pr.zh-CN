---
title: Office 365 Skype for Business 数据删除
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
description: Skype for Business 中的数据删除说明。
ms.openlocfilehash: 0c04ff898395a723ebadd792ea576fe10d440dae
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035729"
---
# <a name="skype-for-business-data-deletion-in-office-365"></a>Office 365 中的 Skype for Business 数据删除

Skype for Business 在会议中提供对等即时消息、多方即时消息和内容上载活动的存档。 存档功能需要 Exchange 并由用户的 Exchange 邮箱就地保留属性控制，这将对电子邮件和 Skype for business 内容进行存档。

Skype for Business 中的所有存档均被视为 "用户级存档"，因为您可以为一个或多个特定用户或用户组创建、配置和应用针对这些用户的用户级存档策略，为其中一个或多个特定用户启用或禁用该存档。 在 Skype for Business 管理中心内，不能直接控制存档设置。

在 Skype for Business 中不存档以下类型的内容：

- 对等文件传输
- 对等即时消息和会议的音频/视频
- 对等即时消息和会议的应用程序共享
- 会议注释 

## <a name="meeting-content-retention"></a>会议内容保留期

使用 Skype for Business 的客户可以将内容作为附件（如 PowerPoint 演示文稿、OneNote 文件和其他文件）上传到 Skype for Business 会议。 上载到会议的内容的保留期如下所示：

- **一次性会议**内容将保留一段时间，从最后一人离开会议的15天开始。
- **定期会议**-在最后一人离开会议的最后一个会话后的15天内保留内容。 如果某人在 15 天内加入同一会议会话，则重置保留计时器。 例如，假设某个 Skype for Business 会议安排在一年的每周进行一次，并在第一个实例中将文件上传到会议。 如果每周至少有一个人加入会议会话，该文件将保留在整个年的 Skype for Business Online 服务器中，此外，在最后一个用户离开该系列的最后一次会议后15天。
- 会议结束时间后，**立即开会会议**-内容将保留8小时。

> [!NOTE]
> 如果用户未获授权或已禁用（例如，如果**msRTCSIP-msrtcsip-userenabled**设置为*False*），然后重新授权或重新启用，则不会保留会议内容。

## <a name="meeting-expiration"></a>会议过期

用户可以在会议结束后访问某个特定的会议，但取决于以下过期时间：

- **一次性会议**会议将在安排的会议结束时间后14天过期。
- **带有结束日期的定期会议**-会议在上次会议发生的计划结束时间后14天过期。
- "**立即开会" 会议**-会议在8小时后过期。

## <a name="whiteboard-collaboration"></a>白板协作

所有参与者都将看到在白板上所做的注释。 保存白板时，白板和所有批注将存储在 Skype for Business 服务器上，并且将根据管理员设置的会议内容过期策略保留在服务器上。

## <a name="audio-test-service"></a>音频测试服务

在音频测试服务呼叫过程中，会记录你的语音的短（约5秒）示例。 根据录制的质量，你可以使用语音示例检查和/或验证 Skype for Business 呼叫的声音质量。 当音频测试服务呼叫结束时，语音示例将被删除。

## <a name="persistent-group-chat"></a>持久组聊天

持续组聊天存储组聊天对话的内容。 如果启用，管理员可以控制保留期、存储此信息的服务器、组内聊天历史记录是否出于合规性或其他目的进行存档，以及如何管理/修改聊天室上的任何属性。 具有不同角色的用户具有对持久化数据的不同访问权限，如下所示：

- 管理员可以从任何聊天室删除较旧的内容（例如，在特定日期之前发布的内容），以使数据库大小不会显著增长。 或者，他们可以删除或替换视为不适合给定聊天室的邮件（或认为不适合）。
- 最终用户（包括邮件作者）无法删除任何聊天室中的内容。
- 聊天室管理员可以禁用聊天室，但不能删除聊天室。 只有管理员才能在创建聊天室后删除该聊天室。