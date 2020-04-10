---
title: Microsoft 365 网络连接位置服务（预览）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 网络连接位置服务（预览）
ms.openlocfilehash: 13ca35afe4bd375482a9fc924801e240c361bb6b
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185723"
---
# <a name="microsoft-365-network-connectivity-location-services-preview"></a><span data-ttu-id="727c2-103">Microsoft 365 网络连接位置服务（预览）</span><span class="sxs-lookup"><span data-stu-id="727c2-103">Microsoft 365 Network Connectivity Location Services (preview)</span></span>

<span data-ttu-id="727c2-104">Microsoft 365 管理中心现在显示**网络见解和性能建议**，它们是从 Microsoft 365 租户收集的实时性能指标，仅供租户中的管理用户查看。</span><span class="sxs-lookup"><span data-stu-id="727c2-104">The Microsoft 365 Admin Center now shows **Network Insights and performance recommendations**, which are live performance metrics collected from your Microsoft 365 tenant and available to view only by administrative users in your tenant.</span></span> <span data-ttu-id="727c2-105">组织网络连接是基于每个办公地点在 Internet 上通过网络出口位置设计的。</span><span class="sxs-lookup"><span data-stu-id="727c2-105">Organizational network connectivity is designed per office location through a network egress location to the Internet.</span></span> <span data-ttu-id="727c2-106">Microsoft 365 客户端连接使用该路由，然后通过 Internet 连接到 Microsoft 服务前端服务器。</span><span class="sxs-lookup"><span data-stu-id="727c2-106">Microsoft 365 client connectivity uses that route and then across the Internet to Microsoft service front door servers.</span></span> <span data-ttu-id="727c2-107">确定办公室位置是能够显示这些网络见解的关键所在。</span><span class="sxs-lookup"><span data-stu-id="727c2-107">Identifying office locations is key to being able to show these network insights.</span></span>

## <a name="location-in-network-measurements"></a><span data-ttu-id="727c2-108">网络中的位置度量</span><span class="sxs-lookup"><span data-stu-id="727c2-108">Location in network measurements</span></span>

<span data-ttu-id="727c2-109">组织的管理员可以选择要在此功能使用的网络度量中包含的位置。</span><span class="sxs-lookup"><span data-stu-id="727c2-109">An organization's administrator can opt in for location to be included in the network measurements used by this feature.</span></span> <span data-ttu-id="727c2-110">这将启用每个办公室所在城市的自动发现功能。</span><span class="sxs-lookup"><span data-stu-id="727c2-110">This enables auto-discovery of the city where each office is located.</span></span> <span data-ttu-id="727c2-111">位置信息不是精确的，并且会被300m 并按城市分类。</span><span class="sxs-lookup"><span data-stu-id="727c2-111">Location information is not precise and is obfuscated to 300m and categorized by city.</span></span> <span data-ttu-id="727c2-112">在 Windows 设备上捕获位置时，它将在工具栏中显示**位置使用中**的图标，管理员可能希望向用户通知这一点。</span><span class="sxs-lookup"><span data-stu-id="727c2-112">At the time when location is captured on a Windows device it will show a **Location In-Use** icon in the tool tray and administrators may want to notify users of this.</span></span> <span data-ttu-id="727c2-113">在此处理过程中，将该位置视为组织办公室位置，而不是某个人或设备的位置。</span><span class="sxs-lookup"><span data-stu-id="727c2-113">With this processing, the location is treated as the organization office location and not the location of a person or a device.</span></span> <span data-ttu-id="727c2-114">可以在这些发现的办公室位置城市中显示网络见解。</span><span class="sxs-lookup"><span data-stu-id="727c2-114">Network insights can be shown at these discovered office location cities.</span></span> <span data-ttu-id="727c2-115">如果需要更精确的建议，管理员可以输入特定的办公室位置地址，而网络见解将聚合到这些地址。</span><span class="sxs-lookup"><span data-stu-id="727c2-115">If greater accuracy of recommendations is desired, an administrator can enter specific office location addresses and the network insights will be aggregated to those instead.</span></span> <span data-ttu-id="727c2-116">办公室位置的聚合不能超过300米。</span><span class="sxs-lookup"><span data-stu-id="727c2-116">Office locations cannot be aggregated more closely than 300 meters.</span></span>

## <a name="location-in-the-microsoft-365-admin-center"></a><span data-ttu-id="727c2-117">Microsoft 365 管理中心中的位置</span><span class="sxs-lookup"><span data-stu-id="727c2-117">Location in the Microsoft 365 Admin Center</span></span>

<span data-ttu-id="727c2-118">在 Microsoft 365 管理中心，Bing 地图控件用于显示组织办公室位置的位置，并显示选定的办公室位置的网络外围拓扑。</span><span class="sxs-lookup"><span data-stu-id="727c2-118">In the Microsoft 365 Admin Center, Bing map controls are used to show where organization office locations are and to show network perimeter topology for a selected office location.</span></span> <span data-ttu-id="727c2-119">当管理员添加了 office 位置的特定地址详细信息时，Bing 地图也可用于建议地址以使数据输入更容易。</span><span class="sxs-lookup"><span data-stu-id="727c2-119">When an administrator adds specific address details for office locations, Bing Maps is also used to suggest addresses to make data entry easier.</span></span>

## <a name="terms-of-use"></a><span data-ttu-id="727c2-120">使用条款</span><span class="sxs-lookup"><span data-stu-id="727c2-120">Terms of Use</span></span>

<span data-ttu-id="727c2-121">通过 Bing 地图提供的任何内容（包括 geocodes）只能在提供该内容的产品内使用。</span><span class="sxs-lookup"><span data-stu-id="727c2-121">Any content provided through Bing Maps, including geocodes, can only be used within the product through which the content is provided.</span></span> <span data-ttu-id="727c2-122">客户使用 Microsoft 365 管理中心位置服务功能（按 Bing 地图提供<https://go.microsoft.com/?linkid=9710837>支持）受_必应 Bing 地图最终用户使用条款_的制约， _Microsoft 隐私声明_中提供了可供使用的<https://go.microsoft.com/fwlink/?LinkID=248686.></span><span class="sxs-lookup"><span data-stu-id="727c2-122">Customer's use of the Microsoft 365 Admin Center Location Services feature, powered by Bing Maps, is governed by the _Bing Maps End User Terms of Use_ available at <https://go.microsoft.com/?linkid=9710837> and the _Microsoft Privacy Statement_ available at <https://go.microsoft.com/fwlink/?LinkID=248686.></span></span>

<span data-ttu-id="727c2-123">此功能（通过 Bing 地图提供）也受**此处技术**支持。</span><span class="sxs-lookup"><span data-stu-id="727c2-123">This feature, provided through Bing Maps, is also supported by **Here Technologies**.</span></span> <span data-ttu-id="727c2-124">必应 Bing 地图如何利用此处技术提供的位置服务由<https://legal.here.com/en-gb/terms>中提供的_以下技术服务条款_进行管理。</span><span class="sxs-lookup"><span data-stu-id="727c2-124">How Bing Maps leverages location services provided by Here Technologies is governed by the _Here Technologies Service Terms_ available at <https://legal.here.com/en-gb/terms>.</span></span>
