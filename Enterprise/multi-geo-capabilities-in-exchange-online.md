---
title: Exchange 多地理位置
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Normal
description: 了解 Exchange Online 中的多地理位置功能。
ms.openlocfilehash: 0c311c9a396fa6c9be7a839d19ff059c7ff287fd
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433843"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Exchange Online 中的多地理位置功能

在多地理位置环境中，可以基于每个用户选择 Exchange Online 邮箱内容（静态数据）的位置。

你可以通过以下方式将邮箱放置在卫星地理位置：

- 直接在卫星地理位置创建新的 Exchange Online 邮箱。

- 通过更改用户的首选数据位置，将现有 Exchange Online 邮箱移动到卫星地理位置。

- 将邮箱从内部部署 Exchange 组织直接挂载到卫星地理位置。

## <a name="mailbox-placement-and-moves"></a>邮箱放置和移动

Microsoft 完成必备的多地理位置配置步骤后，Exchange Online 将遵循 Azure AD 中用户对象的 **PreferredDataLocation** 属性。

Exchange Online 将 **PreferredDataLocation** 属性从 Azure AD 同步到 Exchange Online 目录服务中的 **MailboxRegion** 属性。 **MailboxRegion** 的值确定将放置用户邮箱和任何相关存档邮箱的地理位置。 无法将用户的主邮箱和存档邮箱配置为驻留在不同的地理位置。 每个用户对象只能配置一个地理位置。

- 在具有现有邮箱的用户上配置 **PreferredDataLocation** 时，邮箱将被放入重定位队列，并自动移动到指定的地理位置。

- 如果在没有现有邮箱的用户上配置 **PreferredDataLocation**，则在配置邮箱时，它将被配置到指定的地理位置。

- 如果用户上未指定 **PreferredDataLocation**，则在配置邮箱时，它将被配置在中心地理位置。

- 如果 **PreferredDataLocation** 代码不正确（例如，类型为 NAN 而不是 NAM），则邮箱将被配置在中心地理位置。

**注意**：多地理位置功能和 Skype for Business Online 区域性托管会议都使用用户对象上的 **PreferredDataLocation** 属性来定位服务。 如果在区域托管会议的用户对象上配置 **PreferredDataLocation** 值，则在 Microsoft 365 租户上启用多地理位置后，这些用户的邮箱将自动移动到指定的地理位置。

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Exchange Online 中多地理位置的功能限制

- Exchange 管理中心 (EAC) 中提供的安全性和合规性功能（例如，审核和电子数据展示）在多地理位置组织中不可用。 你需要改用 [Microsoft 365 安全与合规中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)来配置安全性和合规性功能。

- 当你将 Outlook for Mac 用户的邮箱移动到新的地理位置时，他们可能会暂时无法访问其在线存档文件夹。 当用户的主邮箱和存档邮箱位于不同的地理位置时，会出现这种情况，因为跨地理位置邮箱移动可能会在不同时间完成。

- 用户无法在 Web 上的 Outlook（以前称为 Outlook Web App 或 OWA）中跨地理位置共享*邮箱文件夹*。 例如，欧盟的用户无法使用 Web 上的 Outlook 打开位于美国的邮箱中的共享文件夹。 不过，Outlook 网页版用户可以使用单独的浏览器窗口打开不同地理位置中的*其他邮箱*，如[在 Outlook Web App 的单独浏览器窗口中打开其他人的邮箱](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)中所述。

  **注意**：Windows 上的 Outlook 支持跨地理位置邮箱文件夹共享。

- 多地理位置组织支持公用文件夹。 但是，公用文件夹必须保留在中心地理位置。 无法将公用文件夹移动到卫星地理位置。

- 在多地理位置环境中，不支持跨地理位置邮箱审核。 例如，如果为某用户分配了访问其他地理位置的共享邮箱的权限，此用户执行的邮箱操作不会记录在共享邮箱的邮箱审核日志中。 有关详细信息，请参阅[管理邮箱审核](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing?view=o365-worldwide)。
