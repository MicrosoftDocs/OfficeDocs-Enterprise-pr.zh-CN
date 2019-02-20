---
title: Office 365 IdFix 事务日志
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: 提供了一个示例, 并介绍了 Office 365 IdFix 事务日志的命名约定和默认日志级别。
ms.openlocfilehash: c652f8dcbc23a6f0165d894ce6317443db72ceee
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085061"
---
# <a name="office-365-idfix-transaction-log"></a><span data-ttu-id="b1e07-103">Office 365 IdFix 事务日志</span><span class="sxs-lookup"><span data-stu-id="b1e07-103">Office 365 IdFix transaction log</span></span>

<span data-ttu-id="b1e07-104">提供了一个示例, 并介绍了 Office 365 IdFix 事务日志的命名约定和默认日志级别。</span><span class="sxs-lookup"><span data-stu-id="b1e07-104">Provides an example and describes the naming convention and default log level of the Office 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="b1e07-105">IdFix 事务日志位置</span><span class="sxs-lookup"><span data-stu-id="b1e07-105">IdFix transaction log location</span></span>

<span data-ttu-id="b1e07-p101">每次单击 IdFix 中的 "**应用**" 并将更改应用于 Active Directory 林时, Office 365 IdFix 工具都会创建一个新的事务日志。事务日志保存在您安装 IdFix 的同一文件夹中。默认情况下, 此文件夹为 C:\Deployment Tools\IDFix。事务日志文件名使用日期和时间戳格式, 例如, 详细 6-1-2018 6-17-22 pm 表示在2018年6月1日 (6:17:22 PM) 生成的文件。详细说明日志记录级别。</span><span class="sxs-lookup"><span data-stu-id="b1e07-p101">The Office 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest. The transaction log is saved in the same folder where you installed IdFix. By default, this folder is C:\Deployment Tools\IDFix. The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM. Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="b1e07-111">IdFix 事务日志的日志记录级别</span><span class="sxs-lookup"><span data-stu-id="b1e07-111">IdFix transaction log logging level</span></span>

<span data-ttu-id="b1e07-p102">事务日志文件名中的 verbose 一词指示文件中的日志记录级别。Verbose 意味着日志中捕获的最大信息量。这是默认的日志记录级别。此时，您无法更改日志记录级别。</span><span class="sxs-lookup"><span data-stu-id="b1e07-p102">The word verbose in the transaction log file name indicates the level of logging in the file. Verbose means that the maximum amount of information is captured in the log. This is the default logging level. At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="b1e07-116">IdFix 事务日志格式</span><span class="sxs-lookup"><span data-stu-id="b1e07-116">IdFix transaction log format</span></span>

<span data-ttu-id="b1e07-117">IdFix 将每个**更新**操作的结果写入事务日志, 如以下示例所示:</span><span class="sxs-lookup"><span data-stu-id="b1e07-117">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE

```