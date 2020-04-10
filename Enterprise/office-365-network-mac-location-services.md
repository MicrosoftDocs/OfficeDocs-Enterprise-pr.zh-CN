---
title: Microsoft 365 网络连接位置服务（预览）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 网络连接位置服务（预览）
ms.openlocfilehash: 13ca35afe4bd375482a9fc924801e240c361bb6b
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185723"
---
# <a name="microsoft-365-network-connectivity-location-services-preview"></a>Microsoft 365 网络连接位置服务（预览）

Microsoft 365 管理中心现在显示**网络见解和性能建议**，它们是从 Microsoft 365 租户收集的实时性能指标，仅供租户中的管理用户查看。 组织网络连接是基于每个办公地点在 Internet 上通过网络出口位置设计的。 Microsoft 365 客户端连接使用该路由，然后通过 Internet 连接到 Microsoft 服务前端服务器。 确定办公室位置是能够显示这些网络见解的关键所在。

## <a name="location-in-network-measurements"></a>网络中的位置度量

组织的管理员可以选择要在此功能使用的网络度量中包含的位置。 这将启用每个办公室所在城市的自动发现功能。 位置信息不是精确的，并且会被300m 并按城市分类。 在 Windows 设备上捕获位置时，它将在工具栏中显示**位置使用中**的图标，管理员可能希望向用户通知这一点。 在此处理过程中，将该位置视为组织办公室位置，而不是某个人或设备的位置。 可以在这些发现的办公室位置城市中显示网络见解。 如果需要更精确的建议，管理员可以输入特定的办公室位置地址，而网络见解将聚合到这些地址。 办公室位置的聚合不能超过300米。

## <a name="location-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理中心中的位置

在 Microsoft 365 管理中心，Bing 地图控件用于显示组织办公室位置的位置，并显示选定的办公室位置的网络外围拓扑。 当管理员添加了 office 位置的特定地址详细信息时，Bing 地图也可用于建议地址以使数据输入更容易。

## <a name="terms-of-use"></a>使用条款

通过 Bing 地图提供的任何内容（包括 geocodes）只能在提供该内容的产品内使用。 客户使用 Microsoft 365 管理中心位置服务功能（按 Bing 地图提供<https://go.microsoft.com/?linkid=9710837>支持）受_必应 Bing 地图最终用户使用条款_的制约， _Microsoft 隐私声明_中提供了可供使用的<https://go.microsoft.com/fwlink/?LinkID=248686.>

此功能（通过 Bing 地图提供）也受**此处技术**支持。 必应 Bing 地图如何利用此处技术提供的位置服务由<https://legal.here.com/en-gb/terms>中提供的_以下技术服务条款_进行管理。
