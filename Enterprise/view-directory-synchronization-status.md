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
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 了解如何停用目录同步。您还可以查看其状态。
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539841"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>在 Office 365 中查看目录同步状态
如果具有与 Azure AD 集成您的本地 Active Directory，通过将您的内部部署环境与 Office 365 同步，您还可以检查您同步的状态。
  
## <a name="view-directory-synchronization-status"></a>查看目录同步状态
- 登录到 Office 365 管理中心，并选择在主页上的**目录同步状态**。 
- 另外，您可以转到**用户** \> **活动用户**，并在**活动用户**页上选择**多个** \> **目录同步**。在**目录同步**窗格中，选择**转到目录同步管理**。
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>在管理目录同步页上的信息

下表列出了您可以在获得信息的功能。
  
如果使用目录同步问题，以及此页上列出错误。有关不同可能会遇到的错误的详细信息，请参阅[Office 365 中的标识目录同步错误](identify-directory-synchronization-errors.md)。
  
|**项**|**它为**|
|:-----|:-----|
|**验证域** | 拥有在 Office 365 租户，您必须验证您的域数。 |
|**未验证的域** | 已添加，但未验证的域。 |
|**启用目录同步** |True 或 False。指定是否已启用目录同步。 |
|**最新的目录同步** | 上次运行目录同步。如果将显示一条警告和链接到故障排除工具上次同步已超过三天。 |
|**启用密码同步** | True 或 False。指定您是否具有我们本地和 Office 365 租户之间的密码哈希同步。 |
|**最后一个密码同步** | 上次密码哈希同步运行。如果将显示一条警告和链接到故障排除工具上次同步已超过三天。 |
|**目录同步客户端版本** | 如果已释放新版本的 Azure AD 连接，包含下载链接。 |
|**IDFix 工具** | 下载到[IDFix](install-and-run-idfix.md)，您可用于检查您的本地 Active Directory 的工具的链接。 |
|**目录同步服务帐户** | 显示您的 Office 365 目录同步服务帐户的名称。 |