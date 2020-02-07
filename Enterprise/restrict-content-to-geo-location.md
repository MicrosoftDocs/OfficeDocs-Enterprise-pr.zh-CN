---
title: 将 SharePoint 网站内容限制到某个地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何将 SharePoint 站点限制到多地理位置环境中的指定地理位置。
ms.openlocfilehash: b8716eb0ad2d9292a0d52638f827dcc7665d027a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41845013"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a><span data-ttu-id="c0c51-103">将 SharePoint 网站内容限制到某个地理位置</span><span class="sxs-lookup"><span data-stu-id="c0c51-103">Restrict SharePoint site content to a geo location</span></span>

<span data-ttu-id="c0c51-104">在某些情况下，你可能会选择通过以下方式将某个站点及其文件内容强制保留在（在其中创建了站点的）地理位置中：防止转移站点，或者防止将站点的文件内容缓存在另一个地理位置中。</span><span class="sxs-lookup"><span data-stu-id="c0c51-104">Under some circumstances you may choose to enforce a site and its file content to remain in the geo location where the site was created, either by preventing the site from being moved or by preventing the caching of the site's file content in another geo location.</span></span>

<span data-ttu-id="c0c51-105">可使用 **RestrictedToGeo** 参数通过 [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="c0c51-105">You can do this by using the [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet with the **RestrictedToGeo** parameter.</span></span> <span data-ttu-id="c0c51-106">此参数的默认值为 NULL，但你可以将其更改为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="c0c51-106">This parameter has a default value of NULL, but you can change it to one of the following:</span></span>

|<span data-ttu-id="c0c51-107">限制</span><span class="sxs-lookup"><span data-stu-id="c0c51-107">Restriction</span></span>|<span data-ttu-id="c0c51-108">说明</span><span class="sxs-lookup"><span data-stu-id="c0c51-108">Description</span></span>|
|:----------|:----------|
|<span data-ttu-id="c0c51-109">NoRestriction</span><span class="sxs-lookup"><span data-stu-id="c0c51-109">NoRestriction</span></span>|<span data-ttu-id="c0c51-110">可将站点转移到另一个地理位置。</span><span class="sxs-lookup"><span data-stu-id="c0c51-110">The site can be moved to another geo location.</span></span>|
|<span data-ttu-id="c0c51-111">BlockMoveOnly</span><span class="sxs-lookup"><span data-stu-id="c0c51-111">BlockMoveOnly</span></span>|<span data-ttu-id="c0c51-112">无法将站点转移到另一个地理位置，但可将站点内容缓存在其他地理位置中。</span><span class="sxs-lookup"><span data-stu-id="c0c51-112">Site cannot be moved to another geo location, but site content can be cached in other geo locations.</span></span>|
|<span data-ttu-id="c0c51-113">BlockFull</span><span class="sxs-lookup"><span data-stu-id="c0c51-113">BlockFull</span></span>|<span data-ttu-id="c0c51-114">无法将站点转移到另一个地理位置，并且不会在其他地理位置中缓存完整文件内容。</span><span class="sxs-lookup"><span data-stu-id="c0c51-114">Site cannot be moved to another geo location, and full file content is not cached in other geo locations.</span></span> <span data-ttu-id="c0c51-115">文件的标题（从内容中获取）、文件名和文件的其他属性仍可缓存在其他地理位置中。</span><span class="sxs-lookup"><span data-stu-id="c0c51-115">Files' title (harvested from the content), file name, and other properties of the file can still be cached in other geo-locations.</span></span><br><span data-ttu-id="c0c51-116">将该参数配置为 BlockFull 之前存储在站点中的内容可能继续缓存在其他地理位置中。</span><span class="sxs-lookup"><span data-stu-id="c0c51-116">Content stored in the site before it was configured to BlockFull, may continue to be cached in other geo locations.</span></span>|

<span data-ttu-id="c0c51-117">使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="c0c51-117">Use the following syntax:</span></span>

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

<span data-ttu-id="c0c51-118">例如：</span><span class="sxs-lookup"><span data-stu-id="c0c51-118">For example:</span></span>

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
