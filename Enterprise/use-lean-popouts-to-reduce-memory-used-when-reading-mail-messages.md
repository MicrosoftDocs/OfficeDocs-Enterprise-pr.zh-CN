---
title: 使用精益弹出内容减少阅读邮件时使用的内存
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: 本文包含有关使用精益弹出内容改进 web 上的 Outlook 中的邮件下载性能的信息。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e9ca2f90c8798c144f2763106c4c9ca9f57e9df1
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603604"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>使用精益弹出内容减少阅读邮件时使用的内存

本文包含有关在 web 上的 Outlook 中改进邮件下载性能的信息。 本文是 Office 365 项目的[网络规划和性能调整](https://aka.ms/tune)的一部分。
  
作为 Office 365 全局管理员，你可以将 web 上的 Outlook 配置为在 Microsoft Edge 或 Internet Explorer 中的特定电子邮件的较小、占用大量内存的版本中提供_精益弹出内容_。 当为 web 上的 Outlook 配置了精益弹出内容时，将加载服务器端呈现的组件以优化性能。
  
> [!NOTE]
> 从2018年3月起，精益弹出内容不适用于指定使用权限限制的邮件，如信息权限管理 (IRM) 。
  
这些功能将继续在主窗口中运行，但在精益弹出内容中不可用：
  
- Outlook 外接程序
  
- Skype for business 状态
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>为 Office 365 组织中的所有用户配置精益弹出内容
  
1. [使用远程 PowerShell 连接到 Exchange Online](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )。
  
2. 使用 LeanPopoutEnabled 参数运行[set-organizationconfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet，如下所示：

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  例如，若要为组织中的所有用户启用精益弹出内容，请执行以下操作：
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  若要为组织中的所有用户禁用精益弹出内容，请执行以下操作：

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
