---
title: 在 multgeo 环境中的用户体验
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解多地理环境中的 SharePoint 和 OneDrive 的用户体验。
ms.openlocfilehash: 42e384d3e93ca3f5a06a8ee07a37b10e21477038
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>在多个地理环境中的用户体验

下面是您的用户将看到在 OneDrive 多地区配置：

#### <a name="users-onedrive-for-business-location"></a>营业地点的用户的 OneDrive

用户将拥有其业务在其首选的数据位置设置为 OneDrive。如果用户导航到包含不正确的地理位置 （例如，从地理位置上一书签） OneDrive URL 时，它们将自动重定向到适当的地理位置在 OneDrive。

#### <a name="sharing"></a>共享

人员选取器体验向所有用户都显示无论其地理位置如何。这允许用户在其同一地区或任何其他租户的地理位置，与其他用户共享。来自不同的地理位置会显示在**与我共享**视图中为业务用户的 OneDrive 和可以使用单点登录体验，而不考虑哪些地理位置位于访问的内容。

#### <a name="office-applications"></a>Office 应用程序

登录时，office 应用程序如 Word 和 Excel 中，PowerPoint 将自动检测业务地理位置的每个用户正确的 OneDrive。用户不需要输入其 OneDrive 的地区特定 URL。

#### <a name="onedrive-for-business-sync-client"></a>OneDrive 业务同步客户端

为业务同步客户端 OneDrive (版本 17.3.6943.0625 或更高版本) 将自动检测正确的 OneDrive 为业务用户的地理位置。

#### <a name="office-365-app-launcher"></a>Office 365 应用启动器

应用程序启动程序多地理感知，将定向到适当的地理位置的工作负载的每个图块。OneDrive 图块指向承载用户的 OneDrive 库位置，虽然 SharePoint 图块将指向所有用户的中心位置，如仍那里托管团队站点的正确的地理位置。

#### <a name="delve-user-profiles"></a>深入用户配置文件

用户配置文件信息被掌握在用户的地理位置。当选择用户，您将重定向到适当的地理位置对于用户，您看他们完整的配置文件的详细信息。

如果 Delve 被关闭，您将看到在 SharePoint 中，遇到不知道多地理经典配置文件。

#### <a name="delve"></a>Delve

对于 Office 365 提供用户在卫星情况，深入多地区支持，Delve 没有链接到 SharePoint 博客文章编写的其他地区，只有在对 SharePoint 博客站点的用户限制。

#### <a name="search"></a>搜索

每个地理位置都有其自己的搜索索引和搜索中心。当用户搜索时，查询被发送到所有的地理位置，并返回的结果被合并，并且然后排名使用户可以通过统一的结果。从所有的地理位置，而不考虑自己的地理位置，用户可以得到结果。有关详细信息，请参阅[配置搜索 OneDrive 业务多的地区](configure-search-for-multi-geo.md)。

支持下列搜索客户端：

-   OneDrive for Business

-   Delve

-   SharePoint 主页

-   搜索中心

-   使用 SharePoint 搜索 API 的自定义搜索应用程序

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS 和 Android 

OneDrive iOS 和 Android 的移动应用程序将向您展示您的 OneDrive 文件和不管其地理位置与您共享的文件。从 OneDrive 的移动应用程序的搜索将显示来自所有地理位置相关的结果。请下载最新版本的这些应用程序。

有关详细信息，请参阅使用[OneDrive 在 iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)和[Android 的使用 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) 。

#### <a name="teams-experience"></a>团队的经验

团队是多地理意识。而不考虑用户的地理位置显示 OneDrive 文件和最近查看过的文件。@ 提及所有地理位置的用户使用。
