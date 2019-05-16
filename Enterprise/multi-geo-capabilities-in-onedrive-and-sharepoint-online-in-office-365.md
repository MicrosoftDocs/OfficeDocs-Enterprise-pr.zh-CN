---
title: OneDrive 和 SharePoint Online 中的多地理位置功能
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: 利用 OneDrive Online 中的多地理位置功能将 Office 365 的触及范围扩展到多个地理区域。
ms.openlocfilehash: 9f430c18150eb60975e0866ca318d90b78f19280
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069968"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>OneDrive 和 SharePoint Online 中的多地理位置功能

利用 OneDrive 和 SharePoint Online 中的多地理位置功能，可以控制在其中静态存储共享资源（比如 SharePoint 团队站点和 Office 365 组邮箱）的国家或地区。

每个用户、组邮箱和 SharePoint 站点都有一个首选数据位置 (PDL)，表示要在其中存储相关数据的地理位置。 可将用户的个人数据（Exchange 邮箱和 OneDrive）以及用户创建的任何 Office 365 组或 SharePoint 站点存储在指定地理位置，以满足数据驻留要求。 你可以[为每个地理位置指定不同的管理员](add-a-sharepoint-geo-admin.md)。

用户在使用 Office 365 服务（包括 Office 应用程序、OneDrive 和搜索）时将能获得无缝体验。 有关详细信息，请参阅[多地理位置环境中的用户体验](multi-geo-user-experience.md)。

## <a name="onedrive"></a>OneDrive

管理员可依据用户的 PDL 配置每个用户的 OneDrive，或[将其移至](move-onedrive-between-geo-locations.md)附属位置。 个人文件随后保留在该地理位置中，不过可以将这些文件与其他地理位置中的用户共享。

## <a name="sharepoint-sites-and-groups"></a>SharePoint 网站和组

可通过 SharePoint 管理中心管理多地理位置功能。 可在[相应的博客文章](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)中找到详细信息。

当用户创建 SharePoint 组连接的站点时，将使用他们的 PDL 来确定在其中创建站点及其关联组邮箱的地理位置。 （如果尚未设置用户的 PDL 值，或已将其设置为未配置为附属位置的地理位置，则会在中心位置创建站点和邮箱。）

除 Exchange、OneDrive 和 SharePoint 外的其他 Office 365 服务都不是多地理位置服务。 但是，通过这些服务创建的 Office 365 组带有创建者的 PDL 的印记，并将在对应的地理位置中设置其 Exchange 组邮箱和 SharePoint O365 组站点。 

## <a name="managing-the-multi-geo-environment"></a>管理多地理位置环境

多地理位置环境的设置和管理是通过 SharePoint 管理中心完成的。 

![SharePoint 管理中心中地理位置页面的屏幕截图](media/sharepoint-multi-geo-admin-center.png)

（诸如移动 SharePoint 站点或 OneDrive 站点的某些操作需要 Microsoft PowerShell。）

## <a name="see-also"></a>另请参阅

[SharePoint 和 Office 365 组中的多地理位置功能](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[管理多地理位置环境](administering-a-multi-geo-environment.md)

[多地理位置环境中的 SharePoint 存储配额](sharepoint-multi-geo-storage-quota.md)

[在多地理位置环境中管理 Exchange Online 邮箱](administering-exchange-online-multi-geo.md)
