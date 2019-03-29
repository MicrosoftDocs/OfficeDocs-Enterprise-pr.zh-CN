---
title: 添加或删除地理位置管理员
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: 了解如何在 Office 365 多地理位置中添加或删除地理位置管理员。
ms.openlocfilehash: 28af776f3afe4e3cc666817eb2d5faff846aa1af
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931661"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a>在 Office 365 多地理位置中添加或删除地理位置管理员

可以为租户中的每个地理位置配置单独的管理员。 这些管理员将有权访问特定于其地理位置的 SharePoint Online 和 OneDrive 设置。

某些服务（例如术语库）通过中心位置管理并复制到附属位置。 中心位置的地理位置管理员有权访问这些服务，而附属位置的地理位置管理员则无权访问。

全局管理员和 SharePoint Online 管理员仍然有权访问中心位置和所有附属位置中的设置。

## <a name="configuring-geo-administrators"></a>配置地理位置管理员

配置地理位置管理员需要 SharePoint Online PowerShell 模块。

使用 [Connect SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) 连接到想在其中添加地理位置管理员的地理位置的管理中心（例如，Connect SPOService  https://ContosoEUR-admin.sharepoint.com.)

若要查看某个位置的现有地理位置管理员，请运行 `Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>添加用户作为地址位置管理员

若要添加用户作为地理位置管理员，请运行 `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

若要将用户作为某个位置的地理位置管理员删除，请运行  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>添加组作为地理位置管理员

可以添加安全组或启用邮件的安全组作为地理位置管理员。（不支持通讯组和 Office 365 组。）

若要添加组作为地理位置管理员，请运行 `Add-SPOGeoAdministrator -GroupAlias <alias>`

若要将组作为地理位置管理员删除，请运行 `Remove-SPOGeoAdministrator -GroupAlias <alias>`

请注意，并非所有安全组都有组别名。 如果要添加没有别名的安全组，请运行 [Get-MsolGroup](https://docs.microsoft.com/zh-CN/powershell/module/msonline/get-msolgroup) 来检索组列表，找到安全组的对象 ID，然后运行：

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

若要使用对象 ID 删除组，请运行 `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="see-also"></a>另请参阅

[Add-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[为安全组设置别名 (MailNickName)](https://docs.microsoft.com/zh-CN/powershell/module/azuread/set-azureadgroup)