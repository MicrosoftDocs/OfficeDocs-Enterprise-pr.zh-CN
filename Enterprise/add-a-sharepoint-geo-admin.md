---
title: 添加或删除地理位置管理员
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: 了解如何在 Office 365 多地理位置中添加或删除地理位置管理员。
ms.openlocfilehash: d10340b7fe42016710ec953f5b45110e9ea8b901
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030566"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a><span data-ttu-id="1e842-103">在 Office 365 多地理位置中添加或删除地理位置管理员</span><span class="sxs-lookup"><span data-stu-id="1e842-103">Add or remove a geo administrator in Office 365 Multi-Geo</span></span>

<span data-ttu-id="1e842-104">可以为租户中的每个地理位置配置单独的管理员。</span><span class="sxs-lookup"><span data-stu-id="1e842-104">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="1e842-105">这些管理员将有权访问特定于其地理位置的 SharePoint Online 和 OneDrive 设置。</span><span class="sxs-lookup"><span data-stu-id="1e842-105">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="1e842-106">某些服务（例如术语库）通过中心位置管理并复制到附属位置。</span><span class="sxs-lookup"><span data-stu-id="1e842-106">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="1e842-107">中心位置的地理位置管理员有权访问这些服务，而附属位置的地理位置管理员则无权访问。</span><span class="sxs-lookup"><span data-stu-id="1e842-107">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="1e842-108">全局管理员和 SharePoint Online 管理员仍然有权访问中心位置和所有附属位置中的设置。</span><span class="sxs-lookup"><span data-stu-id="1e842-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="1e842-109">配置地理位置管理员</span><span class="sxs-lookup"><span data-stu-id="1e842-109">Configuring geo administrators</span></span>

<span data-ttu-id="1e842-110">配置地理位置管理员需要 SharePoint Online PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="1e842-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="1e842-111">使用 [Connect SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) 连接到想在其中添加地理位置管理员的地理位置的管理中心（例如，Connect SPOService  https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="1e842-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="1e842-112">若要查看某个位置的现有地理位置管理员，请运行 `Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="1e842-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="1e842-113">添加用户作为地址位置管理员</span><span class="sxs-lookup"><span data-stu-id="1e842-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="1e842-114">若要添加用户作为地理位置管理员，请运行 `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="1e842-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="1e842-115">若要将用户作为某个位置的地理位置管理员删除，请运行  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="1e842-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="1e842-116">添加组作为地理位置管理员</span><span class="sxs-lookup"><span data-stu-id="1e842-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="1e842-117">可以添加安全组或启用邮件的安全组作为地理位置管理员。（不支持通讯组和 Office 365 组。）</span><span class="sxs-lookup"><span data-stu-id="1e842-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="1e842-118">若要添加组作为地理位置管理员，请运行 `Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="1e842-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="1e842-119">若要将组作为地理位置管理员删除，请运行 `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="1e842-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="1e842-120">请注意，并非所有安全组都有组别名。</span><span class="sxs-lookup"><span data-stu-id="1e842-120">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="1e842-121">如果要添加没有别名的安全组，请运行 [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) 来检索组列表，找到安全组的对象 ID，然后运行：</span><span class="sxs-lookup"><span data-stu-id="1e842-121">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="1e842-122">若要使用对象 ID 删除组，请运行 `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="1e842-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="1e842-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e842-123">See Also</span></span>

[<span data-ttu-id="1e842-124">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="1e842-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="1e842-125">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="1e842-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="1e842-126">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="1e842-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="1e842-127">为安全组设置别名 (MailNickName)</span><span class="sxs-lookup"><span data-stu-id="1e842-127">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)