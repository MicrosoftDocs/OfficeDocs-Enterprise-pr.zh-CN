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
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>添加或删除 OneDrive Busniess 多-地理地区管理员

您可以配置单独的管理员必须在您组织中的每个地理位置。这些管理员将有权访问特定于其地理位置的 SharePoint Online 和 OneDrive 设置。

某些服务-例如词库的是从中心位置管理和复制到分支机构。中心位置的地区管理员有权访问这些，而 geo 卫星位置的管理员不。

全局管理员和 SharePoint Online 管理员继续在所有地理位置无法访问设置。

## <a name="configuring-geo-administrators"></a>配置地区管理员

地区管理员配置需要 SharePoint 在线 PowerShell 模块。

使用[连接 SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)连接到管理员中心的地理位置，您要在其中添加地理联系管理员。（例如，连接 SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

若要将用户添加为 geo 管理，运行`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

若要查看某个位置的现有地区管理员，请运行`Get-SPOGeoAdministrators`

若要删除作为 Geo 管理位置的用户，运行`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

## <a name="see-also"></a>另请参阅

[添加 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[获得 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[删除 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)