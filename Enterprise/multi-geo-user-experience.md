---
title: 在 multgeo 环境中的用户体验
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解多地理环境中的 SharePoint 和 OneDrive 的用户体验。
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="390ed-103">在多个地理环境中的用户体验</span><span class="sxs-lookup"><span data-stu-id="390ed-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="390ed-104">下面是您的用户将看到在 OneDrive 多地区配置：</span><span class="sxs-lookup"><span data-stu-id="390ed-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="390ed-105">营业地点的用户的 OneDrive</span><span class="sxs-lookup"><span data-stu-id="390ed-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="390ed-p101">用户将拥有其业务在其首选的数据位置设置为 OneDrive。如果用户导航到包含不正确的地理位置 （例如，从地理位置上一书签） OneDrive URL 时，它们将自动重定向到适当的地理位置在 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="390ed-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="390ed-108">共享</span><span class="sxs-lookup"><span data-stu-id="390ed-108">Sharing</span></span>

<span data-ttu-id="390ed-p102">人员选取器体验向所有用户都显示无论其地理位置如何。这允许用户在其同一地区或任何其他租户的地理位置，与其他用户共享。来自不同的地理位置会显示在**与我共享**视图中为业务用户的 OneDrive 和可以使用单点登录体验，而不考虑哪些地理位置位于访问的内容。</span><span class="sxs-lookup"><span data-stu-id="390ed-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="390ed-112">Office 应用程序</span><span class="sxs-lookup"><span data-stu-id="390ed-112">Office applications</span></span>

<span data-ttu-id="390ed-p103">登录时，office 应用程序如 Word 和 Excel 中，PowerPoint 将自动检测业务地理位置的每个用户正确的 OneDrive。用户不需要输入其 OneDrive 的地区特定 URL。</span><span class="sxs-lookup"><span data-stu-id="390ed-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="390ed-115">OneDrive 业务同步客户端</span><span class="sxs-lookup"><span data-stu-id="390ed-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="390ed-116">为业务同步客户端 OneDrive (版本 17.3.6943.0625 或更高版本) 将自动检测正确的 OneDrive 为业务用户的地理位置。</span><span class="sxs-lookup"><span data-stu-id="390ed-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="390ed-117">Office 365 应用启动器</span><span class="sxs-lookup"><span data-stu-id="390ed-117">Office 365 app launcher</span></span>

<span data-ttu-id="390ed-p104">应用程序启动程序多地理感知，将定向到适当的地理位置的工作负载的每个图块。OneDrive 图块指向承载用户的 OneDrive 库位置，虽然 SharePoint 图块将指向所有用户的中心位置，如仍那里托管团队站点的正确的地理位置。</span><span class="sxs-lookup"><span data-stu-id="390ed-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="390ed-120">深入用户配置文件</span><span class="sxs-lookup"><span data-stu-id="390ed-120">Delve User profiles</span></span>

<span data-ttu-id="390ed-p105">用户配置文件信息被掌握在用户的地理位置。当选择用户，您将重定向到适当的地理位置对于用户，您看他们完整的配置文件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="390ed-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="390ed-123">如果 Delve 被关闭，您将看到在 SharePoint 中，遇到不知道多地理经典配置文件。</span><span class="sxs-lookup"><span data-stu-id="390ed-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="390ed-124">Delve</span><span class="sxs-lookup"><span data-stu-id="390ed-124">Delve</span></span>

<span data-ttu-id="390ed-125">对于 Office 365 提供用户在卫星情况，深入多地区支持，Delve 没有链接到 SharePoint 博客文章编写的其他地区，只有在对 SharePoint 博客站点的用户限制。</span><span class="sxs-lookup"><span data-stu-id="390ed-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="390ed-126">搜索</span><span class="sxs-lookup"><span data-stu-id="390ed-126">Search</span></span>

<span data-ttu-id="390ed-p106">每个地理位置都有其自己的搜索索引和搜索中心。当用户搜索时，查询被发送到所有的地理位置，并返回的结果被合并，并且然后排名使用户可以通过统一的结果。从所有的地理位置，而不考虑自己的地理位置，用户可以得到结果。有关详细信息，请参阅[配置搜索 OneDrive 业务多的地区](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="390ed-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="390ed-131">支持下列搜索客户端：</span><span class="sxs-lookup"><span data-stu-id="390ed-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="390ed-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="390ed-132">OneDrive for Business</span></span>

-   <span data-ttu-id="390ed-133">Delve</span><span class="sxs-lookup"><span data-stu-id="390ed-133">Delve</span></span>

-   <span data-ttu-id="390ed-134">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="390ed-134">SharePoint Home</span></span>

-   <span data-ttu-id="390ed-135">搜索中心</span><span class="sxs-lookup"><span data-stu-id="390ed-135">The Search Center</span></span>

-   <span data-ttu-id="390ed-136">使用 SharePoint 搜索 API 的自定义搜索应用程序</span><span class="sxs-lookup"><span data-stu-id="390ed-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="390ed-137">OneDrive iOS 和 Android</span><span class="sxs-lookup"><span data-stu-id="390ed-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="390ed-p107">OneDrive iOS 和 Android 的移动应用程序将向您展示您的 OneDrive 文件和不管其地理位置与您共享的文件。从 OneDrive 的移动应用程序的搜索将显示来自所有地理位置相关的结果。请下载最新版本的这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="390ed-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="390ed-141">有关详细信息，请参阅使用[OneDrive 在 iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)和[Android 的使用 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) 。</span><span class="sxs-lookup"><span data-stu-id="390ed-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="390ed-142">团队的经验</span><span class="sxs-lookup"><span data-stu-id="390ed-142">Teams Experience</span></span>

<span data-ttu-id="390ed-p108">团队是多地理意识。而不考虑用户的地理位置显示 OneDrive 文件和最近查看过的文件。@ 提及所有地理位置的用户使用。</span><span class="sxs-lookup"><span data-stu-id="390ed-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
