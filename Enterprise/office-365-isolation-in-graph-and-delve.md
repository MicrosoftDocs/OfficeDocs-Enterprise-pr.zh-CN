---
title: Microsoft Graph 和 Delve 中的 microsoft 365 租户隔离
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 在本文中，我们将介绍 Microsoft 365 租户隔离在 Office Graph 和 Delve 中的工作原理的说明。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 285f910362628f52c379fcf535da7d0b1365383a
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605594"
---
# <a name="microsoft-365-tenant-isolation-in-the-microsoft-graph-and-delve"></a>Microsoft Graph 和 Delve 中的 microsoft 365 租户隔离

## <a name="tenant-isolation-in-the-microsoft-graph"></a>Microsoft Graph 中的租户隔离

Microsoft 365 服务中的[Microsoft Graph](https://developer.microsoft.com/graph)模型活动，包括 Exchange Online、SharePoint Online、Yammer、Skype for Business、Azure Active Directory 等，以及外部服务（如其他 Microsoft 服务或第三方服务）中的活动。 Microsoft Graph 组件在整个 Microsoft 365 中使用。 Microsoft Graph 表示内容和活动的集合，以及在整个 Office 套件中发生的关系。 它使用先进的机器学习技术将用户连接到相关内容、对话和用户周围的人员。 例如，SharePoint Online 中的租户索引具有用于为 Delve 查询提供服务的 Microsoft Graph 索引，SharePoint Online 中的分析处理引擎用于存储信号和计算见解，Exchange Online 将每个用户的收件人缓存计算为租户分析中的输入。

Microsoft Graph 包含有关企业对象的信息，例如人员和文档，以及这些对象之间的关系和交互。 关系和交互表示为*边缘*。 Microsoft Graph 是由租户分段的，因此，边缘只能存在于同一租赁中的*节点*之间。 *节点*是具有统一资源标识符 (URI) 、节点类型、访问控制列表以及包含*元数据*和边缘的一组 facet 的实体。 每个节点都有关联的元数据和边缘，它们按常见知识模型中的*facet*排列。 *元数据*是存储在节点上的命名属性，可用于在 Microsoft Graph 中进行搜索、筛选或分析。 *Facet*是节点上的元数据和边缘的逻辑集合。 每个 facet 描述节点的一个方面。 

Microsoft Graph 不会将所有数据都引入单个存储库;相反，它存储有关位于其他位置的数据的元数据和关系。 Microsoft Graph 由多个数据存储和处理组件组成：

- 租户图形存储为高效分析提供了批量存储优化。
- 活动内容缓存可提供对主动节点和边缘的随机访问，以推动用户体验。
- 输入路由器会将组件的内部和外部更改通知给租户图形。

每个工作负荷内的分析推断与租户范围内的计算相关的见解，并将其推送到租户图。 租户中的所有活动的租户分析原因，以在行为模式中生成见解。 例如，Exchange Online 计算每个用户的收件人缓存，并对每个用户的邮箱的有效原因进行分析。 这些每用户分析在每个人上生成一组*RecipientCache 边缘*，这些边缘又被推入租户图。 这将使尽可能多的分析处理保持尽可能接近的源数据。

## <a name="tenant-isolation-in-delve"></a>Delve 中的租户隔离

如前所述，Microsoft Graph 可帮助用户发现和协作处理其企业中的当前活动，并为跨工作负载和超过 Microsoft 365 的内容和活动提供分析的原因提供了以实体为中心的平台。 Delve 是 Microsoft Graph 所支持的第一种体验。
Delve 是 Microsoft 365 web 体验，它通过 Microsoft Graph 将内容从 Microsoft 365 和 Yammer Enterprise 显示为 Microsoft 365 用户。 Web 体验将数据显示为不同的板，每个板都有一定的主题，如*周围的趋势分析*或*由我修改的*。 每个板都包含多个文档卡片，这些卡片显示摘要文本和文档中的图片。 智能卡使用户可以执行以下操作：打开文档或文档的 Yammer 页面。 Microsoft 365 租户中的每个人都有一个页面，其中显示了此人最相关的文档，以及可以调用 Exchange Online 或 Skype for Business 以与此人交互的图标。 由于 Delve 基于 Microsoft Graph API，因此它受该 API 基于租户的隔离的约束。