---
title: 添加或删除地理位置管理员
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords:
- NOCSH
description: 是否需要为每个地理位置配置单独的管理员？ 了解如何在 Microsoft 365 多地理位置中添加或删除地理位置管理员。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b69ff352ae0e5ceb55200e0ed034e278808cdc9f
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605818"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a><span data-ttu-id="dc66d-104">在 Microsoft 365 多地理位置中添加或删除地理位置管理员。</span><span class="sxs-lookup"><span data-stu-id="dc66d-104">Add or remove a geo administrator in Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="dc66d-105">可以为租户中的每个地理位置配置单独的管理员。</span><span class="sxs-lookup"><span data-stu-id="dc66d-105">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="dc66d-106">这些管理员将有权访问特定于其地理位置的 SharePoint Online 和 OneDrive 设置。</span><span class="sxs-lookup"><span data-stu-id="dc66d-106">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="dc66d-107">某些服务（例如术语库）通过中心位置管理并复制到附属位置。</span><span class="sxs-lookup"><span data-stu-id="dc66d-107">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="dc66d-108">中心位置的地理位置管理员有权访问这些服务，而附属位置的地理位置管理员则无权访问。</span><span class="sxs-lookup"><span data-stu-id="dc66d-108">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="dc66d-109">全局管理员和 SharePoint Online 管理员仍然有权访问中心位置和所有附属位置中的设置。</span><span class="sxs-lookup"><span data-stu-id="dc66d-109">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="dc66d-110">配置地理位置管理员</span><span class="sxs-lookup"><span data-stu-id="dc66d-110">Configuring geo administrators</span></span>

<span data-ttu-id="dc66d-111">配置地理位置管理员需要 SharePoint Online PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="dc66d-111">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="dc66d-112">使用 [Connect SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) 连接到想在其中添加地理位置管理员的地理位置的管理中心（例如，Connect SPOService  https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="dc66d-112">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="dc66d-113">若要查看某个位置的现有地理位置管理员，请运行 `Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="dc66d-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="dc66d-114">添加用户作为地址位置管理员</span><span class="sxs-lookup"><span data-stu-id="dc66d-114">Adding a user as a geo admin</span></span>

<span data-ttu-id="dc66d-115">若要添加用户作为地理位置管理员，请运行 `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="dc66d-115">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="dc66d-116">若要将用户作为某个位置的地理位置管理员删除，请运行  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="dc66d-116">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="dc66d-117">添加组作为地理位置管理员</span><span class="sxs-lookup"><span data-stu-id="dc66d-117">Adding a group as a geo admin</span></span>

<span data-ttu-id="dc66d-118">可以添加安全组或启用邮件的安全组作为地理位置管理员。（不支持通讯组和 Microsoft 365 组。）</span><span class="sxs-lookup"><span data-stu-id="dc66d-118">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Microsoft 365 Groups are not supported.)</span></span>

<span data-ttu-id="dc66d-119">若要添加组作为地理位置管理员，请运行 `Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="dc66d-119">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="dc66d-120">若要将组作为地理位置管理员删除，请运行 `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="dc66d-120">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="dc66d-121">请注意，并非所有安全组都有组别名。</span><span class="sxs-lookup"><span data-stu-id="dc66d-121">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="dc66d-122">如果要添加没有别名的安全组，请运行 [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) 来检索组列表，找到安全组的对象 ID，然后运行：</span><span class="sxs-lookup"><span data-stu-id="dc66d-122">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="dc66d-123">若要使用对象 ID 删除组，请运行 `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="dc66d-123">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="related-topics"></a><span data-ttu-id="dc66d-124">相关主题</span><span class="sxs-lookup"><span data-stu-id="dc66d-124">Related topics</span></span>

[<span data-ttu-id="dc66d-125">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="dc66d-125">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="dc66d-126">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="dc66d-126">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="dc66d-127">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="dc66d-127">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="dc66d-128">为安全组设置别名 (MailNickName)</span><span class="sxs-lookup"><span data-stu-id="dc66d-128">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)