---
title: 在卫星定位中启用 SharePoint 多地理位置功能
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: 在卫星定位中启用 SharePoint 多地理位置功能。
ms.openlocfilehash: e920aae90326e9635204675d6872340f7808143c
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "41973944"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a><span data-ttu-id="2d44b-103">在卫星定位中启用 SharePoint 多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="2d44b-103">Enabling SharePoint Multi-Geo in your satellite geo location</span></span>

<span data-ttu-id="2d44b-104">本文面向 2019 年 3 月 27 日正式发布 SharePoint 多地理位置功能**以前**已创建多地理位置卫星位置且未在其卫星地理位置启用 SharePoint 多地理位置的全局或 SharePoint 管理员。</span><span class="sxs-lookup"><span data-stu-id="2d44b-104">This article is for Global or SharePoint administrators who have created a Multi-Geo satellite location **before** SharePoint Multi-Geo capabilities became generally available on March 27, 2019, and who have not enabled SharePoint Multi-Geo in their satellite geo location(s).</span></span> 

>[!Note]
><span data-ttu-id="2d44b-105">如果已在 **3 月 27 日后**添加新的地理位置，则无需执行这些说明，因为新的地理位置已针对 OneDrive 和 SharePoint 多地理位置启用。</span><span class="sxs-lookup"><span data-stu-id="2d44b-105">If you have added a new geo location **after March 27th**, you do not need to perform these instructions, as your new geo location will already be enabled for OneDrive and SharePoint Multi-Geo.</span></span>

<span data-ttu-id="2d44b-106">通过这些说明，可以在卫星位置启用 SharePoint，因此多地理位置卫星用户可以利用 O365 中的 OneDrive 和 SharePoint 多地理位置功能。</span><span class="sxs-lookup"><span data-stu-id="2d44b-106">These instructions will allow you to enable SharePoint in your satellite location, so your Multi-Geo satellite users can take advantage of both OneDrive and SharePoint Multi-Geo capabilities in O365.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="2d44b-107">请注意这是单向启用。</span><span class="sxs-lookup"><span data-stu-id="2d44b-107">Please note that this is a one way enablement.</span></span> <span data-ttu-id="2d44b-108">设置 SPO 模式后，则不能将租户还原到仅 OneDrive 多地理位置模式，除非向支持人员上报。</span><span class="sxs-lookup"><span data-stu-id="2d44b-108">Once you set SPO mode, you will not be able to revert your tenant to OneDrive only Multi-Geo mode without an escalation with support.</span></span> 

## <a name="to-set-a-geo-location-into-spo-mode"></a><span data-ttu-id="2d44b-109">要将地理位置设置为 SPO 模式</span><span class="sxs-lookup"><span data-stu-id="2d44b-109">To set a geo location into SPO Mode</span></span>

<span data-ttu-id="2d44b-110">要将地理位置设置为 SPO 模式，请连接到要在 SPO 模式中设置的地理位置：</span><span class="sxs-lookup"><span data-stu-id="2d44b-110">To set a geo location into SPO mode, connect to the geo location you want to set in SPO Mode:</span></span>

1.  <span data-ttu-id="2d44b-111">打开 SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="2d44b-111">Open your SharePoint Online Management Shell</span></span> 
2.  <span data-ttu-id="2d44b-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span><span class="sxs-lookup"><span data-stu-id="2d44b-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span></span>
3.  <span data-ttu-id="2d44b-113">Set-SPOMultiGeoExperience</span><span class="sxs-lookup"><span data-stu-id="2d44b-113">Set-SPOMultiGeoExperience</span></span></br></br>
<span data-ttu-id="2d44b-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="2d44b-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span></span>
4.  <span data-ttu-id="2d44b-115">此操作通常需要约一小时，在此期间，我们会在服务中执行多种发布返回，并重新戳记你的租户。</span><span class="sxs-lookup"><span data-stu-id="2d44b-115">This operation usually takes about an hour while we perform various publish backs in the service and re-stamp your tenant.</span></span> <span data-ttu-id="2d44b-116">至少 1 小时后，请执行 Get-SPOMultiGeoExperience。</span><span class="sxs-lookup"><span data-stu-id="2d44b-116">After at least 1 hour, please perform a Get-SPOMultiGeoExperience.</span></span>  <span data-ttu-id="2d44b-117">这将显示此地理位置是否在 SPO 模式下。</span><span class="sxs-lookup"><span data-stu-id="2d44b-117">This will show you whether this geo location is in SPO mode.</span></span></br></br>
<span data-ttu-id="2d44b-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="2d44b-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span></span>

 
 
 
>[!Note]
><span data-ttu-id="2d44b-119">服务中的某些缓存每 24 小时更新一次，因此在最多 24 小时内，卫星地理位置可能间歇地表现出就像仍在 ODB 模式下的行为。</span><span class="sxs-lookup"><span data-stu-id="2d44b-119">Certain caches in the service update every 24 hours, so it is possible that for a period of up to 24 hours, your satellite geo may intermittently behave as if it was still in ODB mode.</span></span> <span data-ttu-id="2d44b-120">这不会导致任何技术问题。</span><span class="sxs-lookup"><span data-stu-id="2d44b-120">This does not cause any technical issues.</span></span> 
 
<span data-ttu-id="2d44b-121">有关 SharePoint 多地理位置的更多信息，请参阅 [aka.ms/sharepointmultigeo](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span><span class="sxs-lookup"><span data-stu-id="2d44b-121">For additional information regarding SharePoint Multi-Geo, please refer to [aka.ms/sharepointmultigeo](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span></span>


