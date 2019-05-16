---
title: 使用特定 PDL 创建 Office 365 组
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何在多地理位置环境中使用指定的首选数据位置创建 Office 365 组。
ms.openlocfilehash: fb512478d69502eafd633b552d1db2acbec43ef4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069998"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>使用特定 PDL 创建 Office 365 组

当多地理位置环境中的用户创建 Office 365 组时，组首选数据位置将自动设置为用户的该位置。 如果需要使用特定 PDL 创建组，你可以使用 Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet 执行该操作。 执行此操作时，将在指定 PDL 中设置组邮箱以及与该组相关联的 SharePoint 站点。

你必须是全局管理员或 SharePoint Online 或 Exchange Online 管理员才能执行此操作。

若要使用指定的 PDL 创建 Office 365 组，请连接到 Exchange Online PowerShell，并传递包含地理位置代码的 *-MailBoxRegion* 参数。

例如： 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![New-UnifiedGroup PowerShell cmdlet 及语法的屏幕截图](media/multi-geo-new-group-with-pdl-powershell.png)

请注意，SharePoint 组站点设置是按需进行的。 将在组所有者或成员首次试图访问站点时对其进行设置。

## <a name="geo-location-codes"></a>地理位置代码

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>另请参阅

[连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)