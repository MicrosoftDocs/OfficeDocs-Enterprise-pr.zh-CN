---
title: 多地理位置环境中的用户体验
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解多地理位置环境中的 SharePoint 和 OneDrive 用户体验。
ms.openlocfilehash: 951efb636ce00f59393f624687d44a406fcf3fc0
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849828"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>多地理位置环境中的用户体验

下面是你的用户将在 OneDrive 多地理位置配置中看到的内容：

#### <a name="users-onedrive-for-business-location"></a>用户的 OneDrive for Business 位置

用户将在其首选数据位置预配 OneDrive for Business。如果用户导航到包含不正确的地理位置的 OneDrive URL（例如来自先前地理位置的书签），则会将其自动重定向到相应地理位置的 OneDrive。

#### <a name="sharing"></a>共享

人员选取器体验显示所有用户，无论他们的地理位置如何。这允许用户与同一地理位置或任何其他租户的地理位置中的另一个用户共享。不同地理位置的内容将显示在用户的 OneDrive for Business 的“与我共享”**** 视图中，而且无论其托管在哪个地理位置，都可以通过单一登录体验进行访问。

#### <a name="office-applications"></a>Office 应用程序

Word、Excel 和 PowerPoint 等 Office 应用程序会在每个用户登录时自动为其检测正确的 OneDrive for Business 地理位置。用户无需输入其 OneDrive 特定于地理位置的 URL。

#### <a name="onedrive-for-business-sync-client"></a>OneDrive for Business 同步客户端

OneDrive for Business 同步客户端（版本 17.3.6943.0625 及更高版本）将自动为用户检测正确的 OneDrive for Business 地理位置。

#### <a name="office-365-app-launcher"></a>Office 365 应用启动器

该应用启动器可感知多地理位置，并将每个磁贴定向到工作负载的相应地理位置。OneDrive 磁贴指向托管用户的 OneDrive 库的正确地理位置，而 SharePoint 磁贴会将所有用户指向中心位置，因为团队网站仍托管在那里。

#### <a name="delve-user-profiles"></a>Delve 用户配置文件

用户配置文件信息在用户的地理位置中进行管控。选择用户时，你将被定向到用户的相应地理位置，从中你将看到他们的完整配置文件详情。

如果 Delve 已关闭，你将看到 SharePoint 中的经典配置文件体验，该体验无法感知多地理位置。

#### <a name="delve"></a>Delve

对于位于附属实例中的 Office 365 用户，支持 Delve 多地理位置，但也存在限制，Delve 不会链接到其他区域的用户撰写的 SharePoint 博客文章，只会链接到其 SharePoint 博客网站。

#### <a name="search"></a>搜索

每个地理位置都有其自己的搜索索引和搜索中心。当用户搜索时，查询将发送到所有地理位置，并将返回的结果合并，然后进行排名，以便用户获得统一的结果。用户将获取来自所有地理位置的结果，而不管他们自己的地理位置如何。有关详情，请参阅[配置 OneDrive for Business 多地理位置的搜索](configure-search-for-multi-geo.md)。

支持下列搜索客户端：

-   OneDrive for Business

-   Delve

-   SharePoint 主页

-   搜索中心

-   使用 SharePoint 搜索 API 的自定义搜索应用程序

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS 和 Android 

OneDrive iOS 和 Android 移动应用将向你显示你的 OneDrive 文件和与你共享的文件，无论你的地理位置如何。从 OneDrive 移动应用搜索将显示来自所有地理位置的相关结果。请下载这些应用的最新版本。

有关详细信息，请参阅使用 [iOS 上的 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) 和[使用适用于 Android 的 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)。

#### <a name="teams-experience"></a>Teams 体验

Teams 可感知多地理位置。无论用户的地理位置如何，都会显示 OneDrive 文件和最近查看的文件。@ 提到与所有地理位置的用户协作的工作。
