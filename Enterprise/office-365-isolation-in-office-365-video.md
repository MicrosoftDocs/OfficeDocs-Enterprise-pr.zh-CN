---
title: Office 365 中的 office 365 租户隔离视频
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
f1.keywords:
- NOCSH
description: 摘要： Office 365 视频中的租户隔离说明。
ms.openlocfilehash: c7fb97180fbe6c96d2849be7725958a788309558
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843652"
---
# <a name="tenant-isolation-in-office-365-video"></a>Office 365 视频中的租户隔离

> [!NOTE]
> Office 365 视频将替换为 Microsoft Stream。 若要详细了解向视频协作添加智能的新企业视频服务并了解当前 Office 365 视频客户的过渡计划，请参阅[从 Office 365 视频迁移到流](https://docs.microsoft.com/stream/)。

## <a name="introduction"></a>简介

Azure 存储用于存储多个 Office 365 服务（包括 Office 365 视频和 Sway）的数据。 Azure 存储包括 Blob 存储，它是一个用于存储非结构化数据的高可缩放、基于 REST 的云对象存储。 Azure 存储使用简单的访问控制模型;每个 Azure 订阅都可以创建一个或多个存储帐户。 每个存储帐户都有一个密钥，用于控制对该存储帐户中的所有数据的访问。 这支持存储与应用程序相关联的典型方案，这些应用程序可以完全控制其关联的数据;例如，Sway 将内容存储在 Azure 存储中。 Sway 的所有客户内容都存储在共享的 Azure 存储帐户中。 每个用户的内容都位于 Azure 存储中的 blob 的单独目录树中。

管理对客户环境的访问（例如，Azure 门户、SMAPI 等）的系统在由 Microsoft 运营的 Azure 应用程序中隔离。 这将在逻辑上将客户访问基础结构与客户应用程序和存储层分开。

## <a name="tenant-isolation-in-office-365-video"></a>Office 365 视频中的租户隔离

[Office 365 视频](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)是一个企业门户，它为组织提供了用于发布、共享和发现视频内容的高度安全的组织范围的目标。 在 Office 365 视频中，每个租户的视频在所有位置中保持独立和加密，并且仅对对组织视频具有访问权限和权限的经过身份验证的用户可用。 Office 365 视频使用多种技术来实现此目的：

- SharePoint Online 用于存储视频文件和元数据（视频标题、说明等）。 它还提供了安全性和合规性层（包括身份验证）和搜索功能。
- Azure 媒体服务提供了转码、自适应流、安全传递（使用 AES 加密）和缩略图功能。

[Azure 媒体服务](https://azure.microsoft.com/services/media-services/)是一种平台即服务，用于在云中启用端到端媒体工作流。 该平台提供了 REST API，用于上载、编码、加密（使用 PlayReady）以及通过全球的 Azure 数据中心传递媒体。

所有上载的 Office 365 视频通过 HTTPS 进行。 在上载视频文件时，会将其存储在 SharePoint Online 中，并将该文件的副本通过加密通道发送到 Azure 媒体服务。 Azure 媒体服务将视频 transcodes 为多种格式，这些格式针对查看体验（例如，移动、低带宽、高带宽等）进行了优化。 这些文件以及上载过程中获取的原始文件都存储在 Azure Blob 存储中。 这些文件128使用每个 MPEG 通用加密打包算法（或更早的 PlayReady 版本）进行播放，并在存储在 Azure Blob 存储中之前使用 AES 256 存储加密进行加密，从而对这些文件进行加密。 （使用 Azure 媒体服务客户端 SDK，客户可以控制使用哪些加密。 例如，在上载 it Azure Blob 存储之前，客户可以将 Azure 媒体服务存储加密（AES 256）应用到高价值媒体资产。

Azure 媒体服务还会生成视频的缩略图，它会通过加密通道将其连同缩略图元数据一起传输到 SharePoint Online。
