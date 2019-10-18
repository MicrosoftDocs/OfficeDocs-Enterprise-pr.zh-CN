---
title: 多地理位置环境中的用户体验
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解多地理位置环境中的 SharePoint、OneDrive 和 Exchange 用户体验。
ms.openlocfilehash: d8be4376b551242a372c44e62020ff78823f4dba
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069908"
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="9ccef-103">多地理位置环境中的用户体验</span><span class="sxs-lookup"><span data-stu-id="9ccef-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="9ccef-104">下面是用户将在 OneDrive 多地理位置配置中看到的内容：</span><span class="sxs-lookup"><span data-stu-id="9ccef-104">Here's what your users will see in a OneDrive Multi-Geo configuration:</span></span>

## <a name="exchange-mailbox"></a><span data-ttu-id="9ccef-105">Exchange 邮箱</span><span class="sxs-lookup"><span data-stu-id="9ccef-105">Exchange mailbox</span></span>

<span data-ttu-id="9ccef-106">用户的 Exchange 邮箱预配到首选数据位置，并在 PDL 更改后自动重新定位。</span><span class="sxs-lookup"><span data-stu-id="9ccef-106">A user's Exchange mailbox is provisioned to their preferred data location, and is automatically relocated if their PDL changes.</span></span> <span data-ttu-id="9ccef-107">用户通常可以在多地理位置环境中使用 Outlook 和 Outlook 网页版，用户体验没有变化。</span><span class="sxs-lookup"><span data-stu-id="9ccef-107">Users can use Outlook and Outlook on the web normally with no change in user experience in a multi-geo environment.</span></span>

## <a name="hub-sites"></a><span data-ttu-id="9ccef-108">中心网站</span><span class="sxs-lookup"><span data-stu-id="9ccef-108">Hub sites</span></span>

<span data-ttu-id="9ccef-109">SharePoint 中心网站增强了员工的内容发现和参与能力，同时还能完整、一致地表示项目、部门或地区。</span><span class="sxs-lookup"><span data-stu-id="9ccef-109">SharePoint Hub sites enhances the discovery and engagement with content for employees, while creating a complete and consistent representation of projects, departments or regions.</span></span> <span data-ttu-id="9ccef-110">在多地理位置环境中，附属位置中的网站可以与中心网站轻松关联，无论中心网站的地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="9ccef-110">In a multi-geo environment, sites from satellite locations can easily be associated with a hub site regardless the hub site's geo location.</span></span> <span data-ttu-id="9ccef-111">用户可以通过一种搜索体验，跨中心网站搜索并获取结果，无论网站的地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="9ccef-111">Users can search and get results across the hub through a single search experience, regardless of the geo location of the sites.</span></span>

## <a name="office-365-app-launcher"></a><span data-ttu-id="9ccef-112">Office 365 应用启动器</span><span class="sxs-lookup"><span data-stu-id="9ccef-112">Office 365 app launcher</span></span>

<span data-ttu-id="9ccef-113">应用启动器可感知多地理位置，并将每个磁贴定向到工作负荷的相应地理位置。</span><span class="sxs-lookup"><span data-stu-id="9ccef-113">The app launcher is multi-geo aware and will direct each tile to the appropriate geo location of the workload.</span></span> <span data-ttu-id="9ccef-114">SharePoint 和 OneDrive 磁贴将用户指向与用户的已预配地理位置对应的位置。</span><span class="sxs-lookup"><span data-stu-id="9ccef-114">The SharePoint and OneDrive tiles will point the user to the location corresponding to the user's provisioned geo location.</span></span> <span data-ttu-id="9ccef-115">也就是说，用户在中心位置有 OneDrive，用户的 SharePoint 磁贴会将他们指向中心位置中的 SP 主页，但组网站会在与用户 PDL 对应的位置中进行预配。</span><span class="sxs-lookup"><span data-stu-id="9ccef-115">This means that is the user has a OneDrive in the central location, their SharePoint tile will point them to SP Home in the central location but their group site will be provisioned in the location corresponding to their PDL.</span></span> 

## <a name="office-applications"></a><span data-ttu-id="9ccef-116">Office 应用程序</span><span class="sxs-lookup"><span data-stu-id="9ccef-116">Office applications</span></span>

<span data-ttu-id="9ccef-117">Word、Excel 和 PowerPoint 等 Office 应用会在每个用户登录时，自动为用户检测正确的 OneDrive for Business 地理位置。</span><span class="sxs-lookup"><span data-stu-id="9ccef-117">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in.</span></span> <span data-ttu-id="9ccef-118">用户无需输入 OneDrive 或 SharePoint 网站的地理位置专用 URL。</span><span class="sxs-lookup"><span data-stu-id="9ccef-118">Users do not need to enter the geo-specific URL for their OneDrive or SharePoint sites.</span></span>

## <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="9ccef-119">OneDrive for Business 同步客户端</span><span class="sxs-lookup"><span data-stu-id="9ccef-119">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="9ccef-120">OneDrive for Business 同步客户端（版本 17.3.6943.0625 及更高版本）将自动为用户检测正确的 OneDrive for Business 地理位置。</span><span class="sxs-lookup"><span data-stu-id="9ccef-120">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span> <span data-ttu-id="9ccef-121">同步客户端支持包括，能够同步基于组的网站，无论它们的地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="9ccef-121">Synch client support includes the ability to sync groups-based sites regardless of their geo location.</span></span> <span data-ttu-id="9ccef-122">请注意，多地理位置不支持 Groove 同步客户端。</span><span class="sxs-lookup"><span data-stu-id="9ccef-122">Note that the Groove sync client is not supported for multi-geo.</span></span> 

## <a name="onedrive-for-business-location"></a><span data-ttu-id="9ccef-123">OneDrive for Business 位置</span><span class="sxs-lookup"><span data-stu-id="9ccef-123">OneDrive for Business location</span></span>

<span data-ttu-id="9ccef-p106">用户将在其首选数据位置预配 OneDrive for Business。如果用户导航到包含不正确的地理位置的 OneDrive URL（例如来自先前地理位置的书签），则会将其自动重定向到相应地理位置的 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="9ccef-p106">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo location (such as a bookmark from a previous geo location), they are automatically redirected to the OneDrive in the appropriate geo location.</span></span>

## <a name="onedrive-ios-and-android"></a><span data-ttu-id="9ccef-126">OneDrive iOS 和 Android</span><span class="sxs-lookup"><span data-stu-id="9ccef-126">OneDrive iOS and Android</span></span> 

<span data-ttu-id="9ccef-p107">OneDrive iOS 和 Android 移动应用将向你显示你的 OneDrive 文件和与你共享的文件，无论你的地理位置如何。从 OneDrive 移动应用搜索将显示来自所有地理位置的相关结果。请下载这些应用的最新版本。</span><span class="sxs-lookup"><span data-stu-id="9ccef-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="9ccef-130">有关详细信息，请参阅使用 [iOS 上的 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) 和[使用适用于 Android 的 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)。</span><span class="sxs-lookup"><span data-stu-id="9ccef-130">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

## <a name="onedrive-mobile-client"></a><span data-ttu-id="9ccef-131">OneDrive 移动客户端</span><span class="sxs-lookup"><span data-stu-id="9ccef-131">OneDrive Mobile Client</span></span> 

<span data-ttu-id="9ccef-132">OneDrive 移动客户端可感知多地理位置，并显示来自所有地理位置的相关内容和结果。</span><span class="sxs-lookup"><span data-stu-id="9ccef-132">The OneDrive Mobile Client is multi-geo aware and will display pertinent content and results from all geo locations.</span></span>

## <a name="search"></a><span data-ttu-id="9ccef-133">搜索</span><span class="sxs-lookup"><span data-stu-id="9ccef-133">Search</span></span>

<span data-ttu-id="9ccef-p108">每个地理位置都有其自己的搜索索引和搜索中心。当用户搜索时，查询将发送到所有地理位置，并将返回的结果合并，然后进行排名，以便用户获得统一的结果。用户将获取来自所有地理位置的结果，而不管他们自己的地理位置如何。有关详情，请参阅[配置 OneDrive for Business 多地理位置的搜索](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="9ccef-p108">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="9ccef-138">支持下列搜索客户端：</span><span class="sxs-lookup"><span data-stu-id="9ccef-138">The following search clients are supported:</span></span>

-   <span data-ttu-id="9ccef-139">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="9ccef-139">OneDrive for Business</span></span>

-   <span data-ttu-id="9ccef-140">Delve</span><span class="sxs-lookup"><span data-stu-id="9ccef-140">Delve</span></span>

-   <span data-ttu-id="9ccef-141">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="9ccef-141">SharePoint Home</span></span>

-   <span data-ttu-id="9ccef-142">搜索中心</span><span class="sxs-lookup"><span data-stu-id="9ccef-142">The Search Center</span></span>

-   <span data-ttu-id="9ccef-143">使用 SharePoint 搜索 API 的自定义搜索应用程序</span><span class="sxs-lookup"><span data-stu-id="9ccef-143">Custom search applications that use the SharePoint Search API</span></span>

## <a name="sharepoint-home"></a><span data-ttu-id="9ccef-144">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="9ccef-144">SharePoint Home</span></span> 

<span data-ttu-id="9ccef-145">在 SharePoint 多地理位置中，SharePoint 主页托管在用户的驻留位置中，具体取决于 OneDrive for Business 位置。</span><span class="sxs-lookup"><span data-stu-id="9ccef-145">In SharePoint Multi-Geo your SharePoint home is hosted in the location where the user resides as determined by their OneDrive for business location.</span></span> <span data-ttu-id="9ccef-146">例如，如果用户在欧洲附属位置中托管 OneDrive，SharePoint 主页将从欧洲呈现。</span><span class="sxs-lookup"><span data-stu-id="9ccef-146">For example: if the user has their OneDrive hosted in an European satellite location, their SharePoint Home will be rendered from Europe.</span></span> <span data-ttu-id="9ccef-147">SharePoint 主页包括与用户相关的所有内容，无论它们的地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="9ccef-147">SharePoint home includes all content relevant to the user regardless of its geo location.</span></span> 

<span data-ttu-id="9ccef-148">**关注的网站、网站新闻、最近访问的网站、经常访问的网站和推荐网站**</span><span class="sxs-lookup"><span data-stu-id="9ccef-148">**Followed Sites, News from Sites, Recent Sites, Frequent Sites, and Suggested sites**</span></span>

<span data-ttu-id="9ccef-149">只要用户有权访问上述内容，就会看到所有这些组件，无论内容托管地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="9ccef-149">All of these components will show up for the user regardless of the geo location where the content is hosted, so long as the user has permissions to said content.</span></span> 

<span data-ttu-id="9ccef-150">**“特别推荐”链接**</span><span class="sxs-lookup"><span data-stu-id="9ccef-150">**Features Links**</span></span>

<span data-ttu-id="9ccef-151">管理员可以酌情将 SharePoint 主页中的“特别推荐”链接配置为各个地理位置。</span><span class="sxs-lookup"><span data-stu-id="9ccef-151">Admins may configure Featured links in SharePoint home as appropriate to each geo location.</span></span> <span data-ttu-id="9ccef-152">这样一来，管理员可以在每个地区的 SP 主页中提供适合此地区用户的“特别推荐”链接。</span><span class="sxs-lookup"><span data-stu-id="9ccef-152">This allows the admin to feature in the SP Home for each region the links that are appropriate for users in the region.</span></span> 

## <a name="sharepoint-mobile-client"></a><span data-ttu-id="9ccef-153">SharePoint 移动客户端</span><span class="sxs-lookup"><span data-stu-id="9ccef-153">SharePoint Mobile Client</span></span> 

<span data-ttu-id="9ccef-154">SharePoint 移动客户端可感知多地理位置，并显示来自所有地理位置的相关内容和结果。</span><span class="sxs-lookup"><span data-stu-id="9ccef-154">The SharePoint Mobile Client is multi-geo aware and will display pertinent content and results from all geo locations.</span></span>

## <a name="sharing"></a><span data-ttu-id="9ccef-155">共享</span><span class="sxs-lookup"><span data-stu-id="9ccef-155">Sharing</span></span>

<span data-ttu-id="9ccef-156">“人员选取器”体验面向所有用户，无论他们的地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="9ccef-156">The People Picker experience shows all users regardless of their geo location.</span></span> <span data-ttu-id="9ccef-157">这样，一个用户可以与同一地理位置或租户内其他任何地理位置中的其他用户共享。</span><span class="sxs-lookup"><span data-stu-id="9ccef-157">This allows a user to share with another user in their same geo or in any other of your tenant's geo locations.</span></span> <span data-ttu-id="9ccef-158">来自不同地理位置的内容会显示在用户 OneDrive for Business 的“与我共享的内容”\*\*\*\* 视图中，并且可以通过单一登录体验进行访问，无论托管地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="9ccef-158">Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single Sign-On experience regardless of which geo location it is hosted in.</span></span>

## <a name="teams-experience"></a><span data-ttu-id="9ccef-159">Teams 体验</span><span class="sxs-lookup"><span data-stu-id="9ccef-159">Teams Experience</span></span>

<span data-ttu-id="9ccef-160">团队可感知多地理位置。</span><span class="sxs-lookup"><span data-stu-id="9ccef-160">Teams is multi-geo aware.</span></span> <span data-ttu-id="9ccef-161">用户可看到 OneDrive 文件和最近查看的文件，无论他们的地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="9ccef-161">OneDrive files and recently viewed files are shown regardless of the user's geo location.</span></span> <span data-ttu-id="9ccef-162">“@提及”适用于所有地理位置中的用户。</span><span class="sxs-lookup"><span data-stu-id="9ccef-162">@ mentions work with users from all geo-locations.</span></span>

## <a name="user-profiles"></a><span data-ttu-id="9ccef-163">用户个人资料</span><span class="sxs-lookup"><span data-stu-id="9ccef-163">User profiles</span></span>

<span data-ttu-id="9ccef-p113">用户配置文件信息在用户的地理位置中进行管控。选择用户时，你将被定向到用户的相应地理位置，从中你将看到他们的完整配置文件详情。</span><span class="sxs-lookup"><span data-stu-id="9ccef-p113">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="9ccef-166">如果 Delve 已关闭，你将看到 SharePoint 中的经典配置文件体验，该体验无法感知多地理位置。</span><span class="sxs-lookup"><span data-stu-id="9ccef-166">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>


