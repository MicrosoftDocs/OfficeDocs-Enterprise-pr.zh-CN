---
title: 添加或删除地区管理员
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解如何添加或删除在 OneDrive 地区管理员业务多的地区。
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="34504-103">添加或删除 OneDrive Busniess 多-地理地区管理员</span><span class="sxs-lookup"><span data-stu-id="34504-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="34504-p101">您可以配置单独的管理员必须在您组织中的每个地理位置。这些管理员将有权访问特定于其地理位置的 SharePoint Online 和 OneDrive 设置。</span><span class="sxs-lookup"><span data-stu-id="34504-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="34504-p102">某些服务-例如词库的是从中心位置管理和复制到分支机构。中心位置的地区管理员有权访问这些，而 geo 卫星位置的管理员不。</span><span class="sxs-lookup"><span data-stu-id="34504-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="34504-108">全局管理员和 SharePoint Online 管理员继续在所有地理位置无法访问设置。</span><span class="sxs-lookup"><span data-stu-id="34504-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="34504-109">配置地区管理员</span><span class="sxs-lookup"><span data-stu-id="34504-109">Configuring geo administrators</span></span>

<span data-ttu-id="34504-110">地区管理员配置需要 SharePoint 在线 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="34504-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="34504-111">使用[连接 SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)连接到管理员中心的地理位置，您要在其中添加地理联系管理员。（例如，连接 SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="34504-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="34504-112">若要将用户添加为 geo 管理，运行`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="34504-112">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="34504-113">若要查看某个位置的现有地区管理员，请运行`Get-SPOGeoAdministrators`</span><span class="sxs-lookup"><span data-stu-id="34504-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrators`</span></span>

<span data-ttu-id="34504-114">若要删除作为 Geo 管理位置的用户，运行`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="34504-114">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

## <a name="see-also"></a><span data-ttu-id="34504-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34504-115">See Also</span></span>

[<span data-ttu-id="34504-116">添加 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="34504-116">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="34504-117">获得 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="34504-117">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="34504-118">删除 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="34504-118">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)