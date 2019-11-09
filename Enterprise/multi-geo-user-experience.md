---
title: 多地理位置环境中的用户体验
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
ms.custom: ''
localization_priority: Priority
description: 了解多地理位置环境中的 SharePoint、OneDrive 和 Exchange 用户体验。
ms.openlocfilehash: ca6c27b29eae84a245c6fe22fd6ba928b79a975d
ms.sourcegitcommit: 5fe1c9be652222d6956c7dad5949ddcf0bd27041
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2019
ms.locfileid: "38076236"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>多地理位置环境中的用户体验

下面是用户将在 OneDrive 多地理位置配置中看到的内容：

## <a name="exchange-mailbox"></a>Exchange 邮箱

用户的 Exchange 邮箱预配到首选数据位置，并在 PDL 更改后自动重新定位。 用户通常可以在多地理位置环境中使用 Outlook 和 Outlook 网页版，用户体验没有变化。

## <a name="hub-sites"></a>中心网站

SharePoint 中心网站增强了员工的内容发现和参与能力，同时还能完整、一致地表示项目、部门或地区。 在多地理位置环境中，附属位置中的网站可以与中心网站轻松关联，无论中心网站的地理位置如何。 用户可以通过一种搜索体验，跨中心网站搜索并获取结果，无论网站的地理位置如何。

## <a name="office-365-app-launcher"></a>Office 365 应用启动器

应用启动器可感知多地理位置，并将每个磁贴定向到工作负荷的相应地理位置。 SharePoint 和 OneDrive 磁贴将用户指向与用户的已预配地理位置对应的位置。 也就是说，用户在中心位置有 OneDrive，用户的 SharePoint 磁贴会将他们指向中心位置中的 SP 主页，但组网站会在与用户 PDL 对应的位置中进行预配。 

## <a name="office-applications"></a>Office 应用程序

Word、Excel 和 PowerPoint 等 Office 应用会在每个用户登录时，自动为用户检测正确的 OneDrive for Business 地理位置。 用户无需输入 OneDrive 或 SharePoint 网站的地理位置专用 URL。

## <a name="onedrive-for-business-sync-client"></a>OneDrive for Business 同步客户端

OneDrive for Business 同步客户端（版本 17.3.6943.0625 及更高版本）将自动为用户检测正确的 OneDrive for Business 地理位置。 同步客户端支持包括，能够同步基于组的网站，无论它们的地理位置如何。 请注意，多地理位置不支持 Groove 同步客户端。 

## <a name="onedrive-for-business-location"></a>OneDrive for Business 位置

用户将在其首选数据位置预配 OneDrive for Business。如果用户导航到包含不正确的地理位置的 OneDrive URL（例如来自先前地理位置的书签），则会将其自动重定向到相应地理位置的 OneDrive。

## <a name="onedrive-ios-and-android"></a>OneDrive iOS 和 Android 

OneDrive iOS 和 Android 移动应用将向你显示你的 OneDrive 文件和与你共享的文件，无论你的地理位置如何。从 OneDrive 移动应用搜索将显示来自所有地理位置的相关结果。请下载这些应用的最新版本。

有关详细信息，请参阅使用 [iOS 上的 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) 和[使用适用于 Android 的 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)。

## <a name="onedrive-mobile-client"></a>OneDrive 移动客户端 

OneDrive 移动客户端可感知多地理位置，并显示来自所有地理位置的相关内容和结果。

## <a name="search"></a>搜索

每个地理位置都有其自己的搜索索引和搜索中心。当用户搜索时，查询将发送到所有地理位置，并将返回的结果合并，然后进行排名，以便用户获得统一的结果。用户将获取来自所有地理位置的结果，而不管他们自己的地理位置如何。有关详情，请参阅[配置 OneDrive for Business 多地理位置的搜索](configure-search-for-multi-geo.md)。

支持下列搜索客户端：

-   OneDrive for Business

-   Delve

-   SharePoint 主页

-   搜索中心

-   使用 SharePoint 搜索 API 的自定义搜索应用程序

## <a name="sharepoint-home"></a>SharePoint 主页 

在 SharePoint 多地理位置中，SharePoint 主页托管在用户的驻留位置中，具体取决于 OneDrive for Business 位置。 例如，如果用户在欧洲附属位置中托管 OneDrive，SharePoint 主页将从欧洲呈现。 SharePoint 主页包括与用户相关的所有内容，无论它们的地理位置如何。 

**关注的网站、网站新闻、最近访问的网站、经常访问的网站和推荐网站**

只要用户有权访问上述内容，就会看到所有这些组件，无论内容托管地理位置如何。 

**“特别推荐”链接**

管理员可以酌情将 SharePoint 主页中的“特别推荐”链接配置为各个地理位置。 这样一来，管理员可以在每个地区的 SP 主页中提供适合此地区用户的“特别推荐”链接。 

## <a name="sharepoint-mobile-client"></a>SharePoint 移动客户端 

SharePoint 移动客户端可感知多地理位置，并显示来自所有地理位置的相关内容和结果。

## <a name="sharing"></a>共享

“人员选取器”体验面向所有用户，无论他们的地理位置如何。 这样，一个用户可以与同一地理位置或租户内其他任何地理位置中的其他用户共享。 来自不同地理位置的内容会显示在用户 OneDrive for Business 的“与我共享的内容”**** 视图中，并且可以通过单一登录体验进行访问，无论托管地理位置如何。

## <a name="teams-experience"></a>Teams 体验

团队可感知多地理位置。 用户可看到 OneDrive 文件和最近查看的文件，无论他们的地理位置如何。 “@提及”适用于所有地理位置中的用户。

## <a name="user-profiles"></a>用户个人资料

用户配置文件信息在用户的地理位置中进行管控。选择用户时，你将被定向到用户的相应地理位置，从中你将看到他们的完整配置文件详情。

如果 Delve 已关闭，你将看到 SharePoint 中的经典配置文件体验，该体验无法感知多地理位置。


