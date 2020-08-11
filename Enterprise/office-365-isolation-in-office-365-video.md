---
title: Office 365 视频中的租户隔离
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
description: 在本文中，我们将介绍租户隔离如何将每个租户的存储视频分别保留在 Office 365 视频中的说明。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dc341241308a9e54dae2894587ef0fb6b5db0148
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605574"
---
# <a name="tenant-isolation-in-office-365-video"></a>Office 365 视频中的租户隔离

> [!NOTE]
> Office 365 视频将替换为 Microsoft Stream。 若要详细了解将智能添加到视频协作的新企业视频服务并了解当前 Microsoft 365 视频客户的过渡计划，请参阅[Office 365 视频转换为 Microsoft Stream 概述](https://docs.microsoft.com/stream/migrate-from-office-365)。

## <a name="introduction"></a>简介

Azure 存储用于存储多个 Office 365 服务（包括 Office 365 视频和 Sway）的数据。 Azure 存储包括 Blob 存储，它是一个用于存储非结构化数据的高可缩放、基于 REST 的云对象存储。 Azure 存储使用简单的访问控制模型;每个 Azure 订阅都可以创建一个或多个存储帐户。 每个存储帐户都有一个密钥，用于控制对该存储帐户中的所有数据的访问。 这支持存储与应用程序相关联的典型方案，这些应用程序可以完全控制其关联的数据;例如，Sway 将内容存储在 Azure 存储中。 Sway 的所有客户内容都存储在共享的 Azure 存储帐户中。 每个用户的内容都位于 Azure 存储中的 blob 的单独目录树中。

管理对客户环境的访问的系统 (例如，Azure 门户、SMAPI 等 ) 在由 Microsoft 运营的 Azure 应用程序中隔离。 这将在逻辑上将客户访问基础结构与客户应用程序和存储层分开。

## <a name="tenant-isolation-in-office-365-video"></a>Office 365 视频中的租户隔离

[Office 365 视频](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)是一个企业门户，它为组织提供了用于发布、共享和发现视频内容的高度安全的组织范围的目标。 在 Office 365 视频中，每个租户的视频在所有位置中保持独立和加密，并且仅对对组织视频具有访问权限和权限的经过身份验证的用户可用。 Office 365 视频使用多种技术来实现此目的：

- SharePoint Online 用于存储视频文件和元数据 (视频标题、说明等 ) 。 它还提供了安全性和合规性层 (，包括身份验证) 和搜索功能。
- Azure 媒体服务提供代码转换、自适应流式处理、安全传递 (使用 AES 加密) 和缩略图功能。

[Azure 媒体服务](https://azure.microsoft.com/services/media-services/)是一种平台即服务，用于在云中启用端到端媒体工作流。 该平台提供 REST API，用于上载、编码 (使用 PlayReady) ，以及通过世界各地的 Azure 数据中心传递媒体。

所有上载的 Office 365 视频通过 HTTPS 进行。 在上载视频文件时，会将其存储在 SharePoint Online 中，并将该文件的副本通过加密通道发送到 Azure 媒体服务。 Azure 媒体服务将视频 transcodes 为多种格式，这些格式已针对观看体验 (例如移动、低带宽、高带宽等 ) 进行了优化。 这些文件以及上载过程中获取的原始文件都存储在 Azure Blob 存储中。 使用每个 MPEG 通用加密打包算法的 AES 128 加密文件 (或早期 PlayReady 版本) 进行播放，并在将 AES 256 存储加密存储在 Azure Blob 存储中时对这些文件进行加密。  (使用 Azure 媒体服务客户端 SDK，客户可以控制使用哪些加密。 例如，客户可以在将其上载到 Azure Blob 存储之前，将 (AES 256) 的 Azure 媒体服务存储加密应用于高价值的媒体资产。 ) 

Azure 媒体服务还会生成视频的缩略图，它会通过加密通道将其连同缩略图元数据一起传输到 SharePoint Online。
