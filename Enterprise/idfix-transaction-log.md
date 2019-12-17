---
title: Office 365 IdFix 事务日志
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: 提供了一个示例，并介绍了 Office 365 IdFix 事务日志的命名约定和默认日志级别。
ms.openlocfilehash: af1ce72760d9a94438eeead50474094ca0e3a2bd
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072164"
---
# <a name="office-365-idfix-transaction-log"></a>Office 365 IdFix 事务日志

*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*

提供了一个示例，并介绍了 Office 365 IdFix 事务日志的命名约定和默认日志级别。
  
## <a name="idfix-transaction-log-location"></a>IdFix 事务日志位置

每次单击 IdFix 中的 "**应用**" 并将更改应用于 Active Directory 林时，Office 365 IdFix 工具都会创建一个新的事务日志。 事务日志保存在您安装 IdFix 的同一文件夹中。 默认情况下，此文件夹为 C:\Deployment Tools\IDFix。 事务日志文件名使用日期和时间戳格式，例如，详细 6-1-2018 6-17-22 PM 表示在 2018 PM 的6:17:22 年6月1日生成的文件。 详细指示日志记录级别。 
  
## <a name="idfix-transaction-log-logging-level"></a>IdFix 事务日志日志记录级别

事务日志文件名中的 "详细说明" 一词表示在文件中的日志记录级别。 Verbose 表示日志中捕获的信息的最大数量。 这是默认的日志记录级别。 此时，您无法更改日志记录级别。
  
## <a name="idfix-transaction-log-format"></a>IdFix 事务日志格式

IdFix 将每个**更新**操作的结果写入事务日志，如以下示例所示：
  
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