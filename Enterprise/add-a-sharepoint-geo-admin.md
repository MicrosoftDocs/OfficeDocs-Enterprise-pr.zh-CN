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
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>在添加或移除地理管理员 OneDrive for Busniess 多-地理位置

您可以配置已在您的租户中每个地理位置的单独管理员。这些管理员将有权访问特定于其地理位置的 SharePoint Online 和 OneDrive 设置。

某些服务的术语库-例如是从中心位置管理，并复制到附属位置。中心位置地理管理员有权访问这些而附属位置的地理位置 admins 不。

全局管理员和 SharePoint Online 管理员继续有权访问的中心位置和附属的所有位置中的设置。

## <a name="configuring-geo-administrators"></a>配置地理管理员

配置地理管理员需要 SharePoint Online PowerShell 模块。

[Connect-sposervice](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)用于连接到管理中心的地理位置想要添加地理位置管理员。（例如，Connect-sposervicehttps://ContosoEUR-admin.sharepoint.com.)

若要查看位置的现有的地理位置管理员，请运行`Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>添加用户作为地理位置管理

若要将用户添加为地理位置管理，运行`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

若要作为位置的地理位置管理删除用户，请运行`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>将组添加为地理位置管理

您可以将安全组或已启用邮件的安全组添加为地理位置管理员。（通讯组和 Office 365 组不支持。）

若要将组添加为地理管理员，运行`Add-SPOGeoAdministrator -GroupAlias <alias>`

若要删除的地理位置管理员为一组，请运行`Remove-SPOGeoAdministrator -GroupAlias <alias>`

请注意，不是所有安全组的组别名。如果您想要添加安全组不具有别名，运行[Get MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup)检索组的列表，找到您的安全组 ObjectID，然后运行：

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

若要使用 ObjectID 删除组，请运行`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a>访问特定的地理位置在管理中心

若要管理其地理位置的 OneDrive 设置，管理员必须访问 OneDrive 管理中心，直接使用下面的 URL 格式：

https://admin.onedrive.com/?geo=<*地理位置*>

例如，加拿大 OneDrive 管理中心位于： https://admin.onedrive.com/?geo=CAN。

## <a name="see-also"></a>另请参阅

[添加 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[删除 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[设置安全组的别名 (MailNickName)](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)