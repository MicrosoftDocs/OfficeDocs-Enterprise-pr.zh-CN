---
title: 添加或删除地理位置管理员
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解如何在添加或移除地理管理员 OneDrive for Business 多-地理位置。
ms.openlocfilehash: 4e8c8bec148d5a4e7e55ffa2b08a49cd2ea6aa0a
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849808"
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="9b4b2-103">在添加或移除地理管理员 OneDrive for Busniess 多-地理位置</span><span class="sxs-lookup"><span data-stu-id="9b4b2-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="9b4b2-p101">您可以配置已在您的租户中每个地理位置的单独管理员。这些管理员将有权访问特定于其地理位置的 SharePoint Online 和 OneDrive 设置。</span><span class="sxs-lookup"><span data-stu-id="9b4b2-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="9b4b2-p102">某些服务的术语库-例如是从中心位置管理，并复制到附属位置。中心位置地理管理员有权访问这些而附属位置的地理位置 admins 不。</span><span class="sxs-lookup"><span data-stu-id="9b4b2-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="9b4b2-108">全局管理员和 SharePoint Online 管理员继续有权访问的中心位置和附属的所有位置中的设置。</span><span class="sxs-lookup"><span data-stu-id="9b4b2-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="9b4b2-109">配置地理管理员</span><span class="sxs-lookup"><span data-stu-id="9b4b2-109">Configuring geo administrators</span></span>

<span data-ttu-id="9b4b2-110">配置地理管理员需要 SharePoint Online PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="9b4b2-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="9b4b2-111">[Connect-sposervice](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)用于连接到管理中心的地理位置想要添加地理位置管理员。（例如，Connect-sposervicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="9b4b2-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="9b4b2-112">若要查看位置的现有的地理位置管理员，请运行`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="9b4b2-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="9b4b2-113">添加用户作为地理位置管理</span><span class="sxs-lookup"><span data-stu-id="9b4b2-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="9b4b2-114">若要将用户添加为地理位置管理，运行`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="9b4b2-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="9b4b2-115">若要作为位置的地理位置管理删除用户，请运行`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="9b4b2-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="9b4b2-116">将组添加为地理位置管理</span><span class="sxs-lookup"><span data-stu-id="9b4b2-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="9b4b2-117">您可以将安全组或已启用邮件的安全组添加为地理位置管理员。（通讯组和 Office 365 组不支持。）</span><span class="sxs-lookup"><span data-stu-id="9b4b2-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="9b4b2-118">若要将组添加为地理管理员，运行`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="9b4b2-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="9b4b2-119">若要删除的地理位置管理员为一组，请运行`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="9b4b2-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="9b4b2-p103">请注意，不是所有安全组的组别名。如果您想要添加安全组不具有别名，运行[Get MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup)检索组的列表，找到您的安全组 ObjectID，然后运行：</span><span class="sxs-lookup"><span data-stu-id="9b4b2-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="9b4b2-122">若要使用 ObjectID 删除组，请运行`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="9b4b2-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a><span data-ttu-id="9b4b2-123">访问特定的地理位置在管理中心</span><span class="sxs-lookup"><span data-stu-id="9b4b2-123">Accessing the admin center for a specific geo-location</span></span>

<span data-ttu-id="9b4b2-124">若要管理其地理位置的 OneDrive 设置，管理员必须访问 OneDrive 管理中心，直接使用下面的 URL 格式：</span><span class="sxs-lookup"><span data-stu-id="9b4b2-124">To administer OneDrive settings for their geo location, admins must access the OneDrive admin center directly using the following URL format:</span></span>

<span data-ttu-id="9b4b2-125">https://admin.onedrive.com/?geo=<*地理位置*></span><span class="sxs-lookup"><span data-stu-id="9b4b2-125">https://admin.onedrive.com/?geo=<*geo*></span></span>

<span data-ttu-id="9b4b2-126">例如，加拿大 OneDrive 管理中心位于： https://admin.onedrive.com/?geo=CAN。</span><span class="sxs-lookup"><span data-stu-id="9b4b2-126">For example, the OneDrive admin center for Canada is located at: https://admin.onedrive.com/?geo=CAN.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b4b2-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b4b2-127">See Also</span></span>

[<span data-ttu-id="9b4b2-128">添加 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="9b4b2-128">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="9b4b2-129">Get SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="9b4b2-129">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="9b4b2-130">删除 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="9b4b2-130">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="9b4b2-131">设置安全组的别名 (MailNickName)</span><span class="sxs-lookup"><span data-stu-id="9b4b2-131">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)