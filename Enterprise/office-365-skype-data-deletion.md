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
ms.openlocfilehash: e6b0c6b29b43ad07ace8797c1d62240c72110163
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067228"
---
# <a name="skype-for-business-data-deletion-in-office-365"></a><span data-ttu-id="df7b5-103">Office 365 中的 Skype for Business 数据删除</span><span class="sxs-lookup"><span data-stu-id="df7b5-103">Skype for Business Data Deletion in Office 365</span></span>

<span data-ttu-id="df7b5-104">Skype for Business 在会议中提供对等即时消息、多方即时消息和内容上载活动的存档。</span><span class="sxs-lookup"><span data-stu-id="df7b5-104">Skype for Business provides archiving of peer-to-peer instant messages, multiparty instant messages, and content upload activities in meetings.</span></span> <span data-ttu-id="df7b5-105">存档功能需要 Exchange 并由用户的 Exchange 邮箱就地保留属性控制，这将对电子邮件和 Skype for business 内容进行存档。</span><span class="sxs-lookup"><span data-stu-id="df7b5-105">The archiving capability requires Exchange and is controlled by the user's Exchange mailbox In-Place Hold attribute, which archives both email and Skype for Business contents.</span></span>

<span data-ttu-id="df7b5-106">Skype for Business 中的所有存档均被视为 "用户级存档"，因为您可以为一个或多个特定用户或用户组创建、配置和应用针对这些用户的用户级存档策略，为其中一个或多个特定用户启用或禁用该存档。</span><span class="sxs-lookup"><span data-stu-id="df7b5-106">All archiving in Skype for Business is considered "user-level archiving" because you enable or disable it for one or more specific users or groups of users by creating, configuring, and applying a user-level archiving policy for those users.</span></span> <span data-ttu-id="df7b5-107">在 Skype for Business 管理中心内，不能直接控制存档设置。</span><span class="sxs-lookup"><span data-stu-id="df7b5-107">There is no direct control of archiving settings from within the Skype for Business admin center.</span></span>

<span data-ttu-id="df7b5-108">在 Skype for Business 中不存档以下类型的内容：</span><span class="sxs-lookup"><span data-stu-id="df7b5-108">The following types of content are not archived in Skype for Business:</span></span> 
- <span data-ttu-id="df7b5-109">对等文件传输</span><span class="sxs-lookup"><span data-stu-id="df7b5-109">Peer-to-peer file transfers</span></span>
- <span data-ttu-id="df7b5-110">对等即时消息和会议的音频/视频</span><span class="sxs-lookup"><span data-stu-id="df7b5-110">Audio/video for peer-to-peer instant messages and conferences</span></span>
- <span data-ttu-id="df7b5-111">对等即时消息和会议的应用程序共享</span><span class="sxs-lookup"><span data-stu-id="df7b5-111">Application sharing for peer-to-peer instant messages and conferences</span></span>
- <span data-ttu-id="df7b5-112">会议注释</span><span class="sxs-lookup"><span data-stu-id="df7b5-112">Conferencing annotations</span></span> 

## <a name="meeting-content-retention"></a><span data-ttu-id="df7b5-113">会议内容保留期</span><span class="sxs-lookup"><span data-stu-id="df7b5-113">Meeting Content Retention</span></span>
<span data-ttu-id="df7b5-114">使用 Skype for Business 的客户可以将内容作为附件（如 PowerPoint 演示文稿、OneNote 文件和其他文件）上传到 Skype for Business 会议。</span><span class="sxs-lookup"><span data-stu-id="df7b5-114">Customers using Skype for Business can upload content to a Skype for Business meeting as attachments, such as PowerPoint presentations, OneNote files, and other files.</span></span> <span data-ttu-id="df7b5-115">上载到会议的内容的保留期如下所示：</span><span class="sxs-lookup"><span data-stu-id="df7b5-115">The retention period for content that has been uploaded to a meeting is as follows:</span></span>
- <span data-ttu-id="df7b5-116">**一次性会议**内容将保留一段时间，从最后一人离开会议的15天开始。</span><span class="sxs-lookup"><span data-stu-id="df7b5-116">**One-time meeting** - Content is retained for 15 days starting from when the last person leaves the meeting.</span></span>
- <span data-ttu-id="df7b5-117">**定期会议**-在最后一人离开会议的最后一个会话后的15天内保留内容。</span><span class="sxs-lookup"><span data-stu-id="df7b5-117">**Recurring meeting** - Content is retained for 15 days after the last person leaves the last session of the meeting.</span></span> <span data-ttu-id="df7b5-118">如果某人在 15 天内加入同一会议会话，则重置保留计时器。</span><span class="sxs-lookup"><span data-stu-id="df7b5-118">The retention timer resets if someone joins the same meeting session within 15 days.</span></span> <span data-ttu-id="df7b5-119">例如，假设某个 Skype for Business 会议安排在一年的每周进行一次，并在第一个实例中将文件上传到会议。</span><span class="sxs-lookup"><span data-stu-id="df7b5-119">For example, assume a Skype for Business meeting is scheduled to occur on a weekly basis for one year, and a file is uploaded to the meeting during the first instance.</span></span> <span data-ttu-id="df7b5-120">如果每周至少有一个人加入会议会话，该文件将保留在整个年的 Skype for Business Online 服务器中，此外，在最后一个用户离开该系列的最后一次会议后15天。</span><span class="sxs-lookup"><span data-stu-id="df7b5-120">If at least one person joins the meeting session every week, the file is retained in Skype for Business Online servers for the entire year plus 15 days after the last person leaves the last meeting of the series.</span></span>
- <span data-ttu-id="df7b5-121">会议结束时间后，**立即开会会议**-内容将保留8小时。</span><span class="sxs-lookup"><span data-stu-id="df7b5-121">**Meet Now meeting** - Content is retained for 8 hours after the meeting end time.</span></span>

> [!NOTE]
> <span data-ttu-id="df7b5-122">如果用户未获授权或已禁用（例如，如果**msRTCSIP-msrtcsip-userenabled**设置为*False*），然后重新授权或重新启用，则不会保留会议内容。</span><span class="sxs-lookup"><span data-stu-id="df7b5-122">If a user is unlicensed or disabled (e.g., if **msRTCSIP-userenabled** is set to *False*), and is then re-licensed or reenabled, meeting content is not retained.</span></span>

## <a name="meeting-expiration"></a><span data-ttu-id="df7b5-123">会议过期</span><span class="sxs-lookup"><span data-stu-id="df7b5-123">Meeting Expiration</span></span>
<span data-ttu-id="df7b5-124">用户可以在会议结束后访问某个特定的会议，但取决于以下过期时间：</span><span class="sxs-lookup"><span data-stu-id="df7b5-124">Users can access a specific meeting after the meeting has ended, subject to the following expiration time periods:</span></span>
- <span data-ttu-id="df7b5-125">**一次性会议**会议将在安排的会议结束时间后14天过期。</span><span class="sxs-lookup"><span data-stu-id="df7b5-125">**One-time meeting** - Meeting expires 14 days after the scheduled meeting end time.</span></span>
- <span data-ttu-id="df7b5-126">**带有结束日期的定期会议**-会议在上次会议发生的计划结束时间后14天过期。</span><span class="sxs-lookup"><span data-stu-id="df7b5-126">**Recurring meeting with end date** - Meeting expires 14 days after the scheduled end time of the last meeting occurrence.</span></span>
- <span data-ttu-id="df7b5-127">"**立即开会" 会议**-会议在8小时后过期。</span><span class="sxs-lookup"><span data-stu-id="df7b5-127">**Meet Now meeting** - Meeting expires after 8 hours.</span></span>

## <a name="whiteboard-collaboration"></a><span data-ttu-id="df7b5-128">白板协作</span><span class="sxs-lookup"><span data-stu-id="df7b5-128">Whiteboard Collaboration</span></span>
<span data-ttu-id="df7b5-129">所有参与者都将看到在白板上所做的注释。</span><span class="sxs-lookup"><span data-stu-id="df7b5-129">Annotations made on whiteboards will be seen by all participants.</span></span> <span data-ttu-id="df7b5-130">保存白板时，白板和所有批注将存储在 Skype for Business 服务器上，并且将根据管理员设置的会议内容过期策略保留在服务器上。</span><span class="sxs-lookup"><span data-stu-id="df7b5-130">When saving a whiteboard, the whiteboard and all annotations will be stored on a Skype for Business server, and it will be retained on the server according to meeting content expiration policies set by the administrator.</span></span>

## <a name="audio-test-service"></a><span data-ttu-id="df7b5-131">音频测试服务</span><span class="sxs-lookup"><span data-stu-id="df7b5-131">Audio Test Service</span></span>
<span data-ttu-id="df7b5-132">在音频测试服务呼叫过程中，会记录你的语音的短（约5秒）示例。</span><span class="sxs-lookup"><span data-stu-id="df7b5-132">A short (approximately 5 seconds) sample of your voice is recorded during the Audio Test Service call.</span></span> <span data-ttu-id="df7b5-133">根据录制的质量，你可以使用语音示例检查和/或验证 Skype for Business 呼叫的声音质量。</span><span class="sxs-lookup"><span data-stu-id="df7b5-133">The voice sample is used by you to check and/or verify the sound quality of your Skype for Business call based on the quality of the recording.</span></span> <span data-ttu-id="df7b5-134">当音频测试服务呼叫结束时，语音示例将被删除。</span><span class="sxs-lookup"><span data-stu-id="df7b5-134">When the Audio Test Service call ends, the voice sample is deleted.</span></span>

## <a name="persistent-group-chat"></a><span data-ttu-id="df7b5-135">持久组聊天</span><span class="sxs-lookup"><span data-stu-id="df7b5-135">Persistent Group Chat</span></span>
<span data-ttu-id="df7b5-136">持续组聊天存储组聊天对话的内容。</span><span class="sxs-lookup"><span data-stu-id="df7b5-136">Persistent Group Chat stores the content of group chat conversations.</span></span> <span data-ttu-id="df7b5-137">如果启用，管理员可以控制保留期、存储此信息的服务器、组内聊天历史记录是否出于合规性或其他目的进行存档，以及如何管理/修改聊天室上的任何属性。</span><span class="sxs-lookup"><span data-stu-id="df7b5-137">If enabled, the administrator can control the retention period, the server on which this information is stored, if Group Chat history is archived for compliance or other purposes, and manage/modify any properties on a room.</span></span> <span data-ttu-id="df7b5-138">具有不同角色的用户具有对持久化数据的不同访问权限，如下所示：</span><span class="sxs-lookup"><span data-stu-id="df7b5-138">Users with different roles have different access to the persisted data, as follows:</span></span>
- <span data-ttu-id="df7b5-139">管理员可以从任何聊天室删除较旧的内容（例如，在特定日期之前发布的内容），以使数据库大小不会显著增长。</span><span class="sxs-lookup"><span data-stu-id="df7b5-139">Administrators can delete older content (for example, content posted before a certain date) from any chat room to keep the size of the database from growing greatly.</span></span> <span data-ttu-id="df7b5-140">或者，他们可以删除或替换视为不适合给定聊天室的邮件（或认为不适合）。</span><span class="sxs-lookup"><span data-stu-id="df7b5-140">Or, they can remove or replace messages considered inappropriate for a given chat room (or considered unsuitable).</span></span>
- <span data-ttu-id="df7b5-141">最终用户（包括邮件作者）无法删除任何聊天室中的内容。</span><span class="sxs-lookup"><span data-stu-id="df7b5-141">End-users, including message authors, cannot delete content from any chat room.</span></span>
- <span data-ttu-id="df7b5-142">聊天室管理员可以禁用聊天室，但不能删除聊天室。</span><span class="sxs-lookup"><span data-stu-id="df7b5-142">Chat room managers can disable rooms but cannot delete rooms.</span></span> <span data-ttu-id="df7b5-143">只有管理员才能在创建聊天室后删除该聊天室。</span><span class="sxs-lookup"><span data-stu-id="df7b5-143">Only administrators can delete a chat room after it is created.</span></span>