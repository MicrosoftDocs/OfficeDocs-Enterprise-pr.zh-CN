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
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="2c906-103">多地理位置环境中的用户体验</span><span class="sxs-lookup"><span data-stu-id="2c906-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="2c906-104">下面是你的用户将在 OneDrive 多地理位置配置中看到的内容：</span><span class="sxs-lookup"><span data-stu-id="2c906-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="2c906-105">用户的 OneDrive for Business 位置</span><span class="sxs-lookup"><span data-stu-id="2c906-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="2c906-p101">用户将在其首选数据位置预配 OneDrive for Business。如果用户导航到包含不正确的地理位置的 OneDrive URL（例如来自先前地理位置的书签），则会将其自动重定向到相应地理位置的 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="2c906-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="2c906-108">共享</span><span class="sxs-lookup"><span data-stu-id="2c906-108">Sharing</span></span>

<span data-ttu-id="2c906-p102">人员选取器体验显示所有用户，无论他们的地理位置如何。这允许用户与同一地理位置或任何其他租户的地理位置中的另一个用户共享。不同地理位置的内容将显示在用户的 OneDrive for Business 的“与我共享”\*\*\*\* 视图中，而且无论其托管在哪个地理位置，都可以通过单一登录体验进行访问。</span><span class="sxs-lookup"><span data-stu-id="2c906-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="2c906-112">Office 应用程序</span><span class="sxs-lookup"><span data-stu-id="2c906-112">Office applications</span></span>

<span data-ttu-id="2c906-p103">Word、Excel 和 PowerPoint 等 Office 应用程序会在每个用户登录时自动为其检测正确的 OneDrive for Business 地理位置。用户无需输入其 OneDrive 特定于地理位置的 URL。</span><span class="sxs-lookup"><span data-stu-id="2c906-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="2c906-115">OneDrive for Business 同步客户端</span><span class="sxs-lookup"><span data-stu-id="2c906-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="2c906-116">OneDrive for Business 同步客户端（版本 17.3.6943.0625 及更高版本）将自动为用户检测正确的 OneDrive for Business 地理位置。</span><span class="sxs-lookup"><span data-stu-id="2c906-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="2c906-117">Office 365 应用启动器</span><span class="sxs-lookup"><span data-stu-id="2c906-117">Office 365 app launcher</span></span>

<span data-ttu-id="2c906-p104">该应用启动器可感知多地理位置，并将每个磁贴定向到工作负载的相应地理位置。OneDrive 磁贴指向托管用户的 OneDrive 库的正确地理位置，而 SharePoint 磁贴会将所有用户指向中心位置，因为团队网站仍托管在那里。</span><span class="sxs-lookup"><span data-stu-id="2c906-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="2c906-120">Delve 用户配置文件</span><span class="sxs-lookup"><span data-stu-id="2c906-120">Delve User profiles</span></span>

<span data-ttu-id="2c906-p105">用户配置文件信息在用户的地理位置中进行管控。选择用户时，你将被定向到用户的相应地理位置，从中你将看到他们的完整配置文件详情。</span><span class="sxs-lookup"><span data-stu-id="2c906-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="2c906-123">如果 Delve 已关闭，你将看到 SharePoint 中的经典配置文件体验，该体验无法感知多地理位置。</span><span class="sxs-lookup"><span data-stu-id="2c906-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="2c906-124">Delve</span><span class="sxs-lookup"><span data-stu-id="2c906-124">Delve</span></span>

<span data-ttu-id="2c906-125">对于位于附属实例中的 Office 365 用户，支持 Delve 多地理位置，但也存在限制，Delve 不会链接到其他区域的用户撰写的 SharePoint 博客文章，只会链接到其 SharePoint 博客网站。</span><span class="sxs-lookup"><span data-stu-id="2c906-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="2c906-126">搜索</span><span class="sxs-lookup"><span data-stu-id="2c906-126">Search</span></span>

<span data-ttu-id="2c906-p106">每个地理位置都有其自己的搜索索引和搜索中心。当用户搜索时，查询将发送到所有地理位置，并将返回的结果合并，然后进行排名，以便用户获得统一的结果。用户将获取来自所有地理位置的结果，而不管他们自己的地理位置如何。有关详情，请参阅[配置 OneDrive for Business 多地理位置的搜索](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="2c906-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="2c906-131">支持下列搜索客户端：</span><span class="sxs-lookup"><span data-stu-id="2c906-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="2c906-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="2c906-132">OneDrive for Business</span></span>

-   <span data-ttu-id="2c906-133">Delve</span><span class="sxs-lookup"><span data-stu-id="2c906-133">Delve</span></span>

-   <span data-ttu-id="2c906-134">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="2c906-134">SharePoint Home</span></span>

-   <span data-ttu-id="2c906-135">搜索中心</span><span class="sxs-lookup"><span data-stu-id="2c906-135">The Search Center</span></span>

-   <span data-ttu-id="2c906-136">使用 SharePoint 搜索 API 的自定义搜索应用程序</span><span class="sxs-lookup"><span data-stu-id="2c906-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="2c906-137">OneDrive iOS 和 Android</span><span class="sxs-lookup"><span data-stu-id="2c906-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="2c906-p107">OneDrive iOS 和 Android 移动应用将向你显示你的 OneDrive 文件和与你共享的文件，无论你的地理位置如何。从 OneDrive 移动应用搜索将显示来自所有地理位置的相关结果。请下载这些应用的最新版本。</span><span class="sxs-lookup"><span data-stu-id="2c906-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="2c906-141">有关详细信息，请参阅使用 [iOS 上的 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) 和[使用适用于 Android 的 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)。</span><span class="sxs-lookup"><span data-stu-id="2c906-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="2c906-142">Teams 体验</span><span class="sxs-lookup"><span data-stu-id="2c906-142">Teams Experience</span></span>

<span data-ttu-id="2c906-p108">Teams 可感知多地理位置。无论用户的地理位置如何，都会显示 OneDrive 文件和最近查看的文件。@ 提到与所有地理位置的用户协作的工作。</span><span class="sxs-lookup"><span data-stu-id="2c906-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
