---
title: 在 Office 365 中查看目录同步状态
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 了解如何停用目录同步。您还可以查看其状态。
ms.openlocfilehash: 4803cbadd17dbc1ee23d019f39144ff1ffaefd9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085051"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>在 Office 365 中查看目录同步状态
如果已通过将本地环境与 Office 365 同步, 将本地 Active Directory 与 Azure AD 集成, 则还可以检查同步的状态。
  
## <a name="view-directory-synchronization-status"></a>查看目录同步状态
- 登录到 Office 365 管理中心, 并在主页上选择 " **DirSync Status** "。 
- 或者, 您可以转到**用户** \> **活动用户**, 并在 "**活动用户**" 页上选择 "**更多** \> **目录同步**"。在 "**目录同步**" 窗格中, 选择 "**转到 DirSync management**"。
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>"管理目录同步" 页上的信息

下表列出了可以在页面上获取相关信息的功能。
  
如果目录同步存在问题, 则还会在此页面上列出这些错误。有关可能遇到的不同错误的详细信息, 请参阅[识别 Office 365 中的目录同步错误](identify-directory-synchronization-errors.md)。
  
|**项目**|**它有何用途？**|
|:-----|:-----|
|**已验证域** | 您已对其进行验证的 Office 365 租户中的域的数量。 |
|**未验证域** | 已添加但未验证的域。 |
|**目录同步已启用** |True 或 False。指定是否已启用目录同步。 |
|**最新目录同步** | 上次运行目录同步的时间。如果上一次同步的时间已超过三天, 将显示一条警告和指向故障排除工具的链接。 |
|**启用密码同步** | True 或 False。指定在内部部署和 Office 365 租户之间是否有密码哈希同步。 |
|**上次密码同步** | 上次运行密码哈希同步的时间。如果上一次同步的时间已超过三天, 将显示一条警告和指向故障排除工具的链接。 |
|**目录同步客户端版本** | 如果已发布新版本的 Azure AD Connect, 则包含下载链接。 |
|**IDFix 工具** | 下载指向[IDFix](install-and-run-idfix.md)的链接, 可用于检查本地 Active Directory 的工具。 |
|**目录同步服务帐户** | 显示 Office 365 目录同步服务帐户的名称。 |