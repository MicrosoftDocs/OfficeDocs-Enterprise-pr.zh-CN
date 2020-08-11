---
title: 将 SharePoint 网站内容限制到某个地理位置
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: 在本文中，您将了解如何将 SharePoint 网站限制为多地理位置环境中的指定地理位置。
ms.openlocfilehash: 7f0147d803fe4dbc6aa444a5e5014884c0f00beb
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606148"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>将 SharePoint 网站内容限制到某个地理位置

在某些情况下，你可能会选择通过以下方式将某个站点及其文件内容强制保留在（在其中创建了站点的）地理位置中：防止转移站点，或者防止将站点的文件内容缓存在另一个地理位置中。

可使用 **RestrictedToGeo** 参数通过 [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet 来执行此操作。 此参数的默认值为 NULL，但你可以将其更改为以下值之一：

|限制|说明|
|:----------|:----------|
|NoRestriction|可将站点转移到另一个地理位置。|
|BlockMoveOnly|无法将站点转移到另一个地理位置，但可将站点内容缓存在其他地理位置中。|
|BlockFull|无法将站点转移到另一个地理位置，并且不会在其他地理位置中缓存完整文件内容。 文件的标题（从内容中获取）、文件名和文件的其他属性仍可缓存在其他地理位置中。<br>将该参数配置为 BlockFull 之前存储在站点中的内容可能继续缓存在其他地理位置中。|

使用以下语法：

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

例如：

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
