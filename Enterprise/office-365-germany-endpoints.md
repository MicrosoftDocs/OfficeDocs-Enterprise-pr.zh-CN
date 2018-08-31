---
title: Office 365 Germany 终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 如果您的组织使用 Office 365，并限制在您的网络的计算机连接到 Internet，下面将找到的终结点 （Fqdn、 端口、 Url 和 IPv4 和 IPv6 地址范围） 应包含在您出站的允许列表，以确保您计算机可以成功使用 Office 365。
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539526"
---
# <a name="office-365-germany-endpoints"></a>Office 365 Germany 终结点

 *应用于： Office 365 管理*

**摘要：** Office 365 要求连接到 Internet。下面的终结点应该为客户使用**Office 365 德国**计划仅可访问。
  
> [!NOTE]
> Microsoft 正在开发基于 REST 的 web 服务的 IP 地址和此页上的 FQDN 条目。此新服务将帮助您配置和更新网络外围设备，如防火墙和代理服务器。您可以下载的终结点、 列表或特定更改的当前版本的列表。XML 文档、 RSS 源，和 IP 地址和 FQDN 条目，此页上的，则最终将替换此服务。若要试用此新的服务，请转到[Web 服务](managing-office-365-endpoints.md#webservice)。 
  
 **Office 365 终结点：**[全球 （包括 GCC）](urls-and-ip-address-ranges.md)  |  [Office 365 由 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 德国* | [Office 365 美国政府 DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 美国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**上次更新时间：** 7/2/2018- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [到 Office 365 德国终结点的更改的列表](office-365-germany-endpoints-change-log.md)||

从[管理 Office 365 终结点](managing-office-365-endpoints.md)开始了解我们的建议用于管理网络连接使用该数据。终结点数据更新新的 IP 地址和 Url 发布前处于活动状态的 30 天内每月的开头。这样不尚未具有自动更新完成其流程之前不需要新连接的客户。如果无需对地址支持升级、 安全事件或其他即时操作要求，还可能月份内更新终结点。始终可引用[的更改到 Office 365 德国终结点列表](office-365-germany-endpoints-change-log.md)。

所有生成的基于 REST 的 web 服务从下面此页面上显示的数据。如果您使用脚本或网络设备进行访问这些数据，您应直接转到[Web 服务](managing-office-365-endpoints.md#webservice)中。

终结点数据下面列出了从用户的计算机连接到 Office 365 的要求。它不包括来自 Microsoft 客户网络、 有时称为的混合或入站的网络连接到的网络连接。

终结点分为四个服务区域。可以为独立连接选择的第三个服务区域。第四个服务区域是常见的相关性 （称为 Microsoft 365 常见和 Office Online），并且必须始终具有网络连接。

数据列显示如下：

- **ID**： 的行，也称为终结点设置的 ID 号。此 ID 是由终结点设置的 web 服务返回的相同。

- **类别**： 显示终结点设置是否属于"优化"、"允许"或"Default"。您可以了解有关这些类别和指南管理它们在[http://aka.ms/pnc](http://aka.ms/pnc)。此列还列出了哪些终结点组所需具有网络连接。对于其不需要有网络连接的终结点集，我们提供此字段，以指示哪项功能将会丢失，如果阻止终结点设置中的注释。如果您不包括整个服务区域，列出所需的终结点集不需要连接。

- **紧急**： 这是**** 如果终结点设置通过 Azure ExpressRoute 支持 Office 365 路由前缀。BGP 社区包含所示的路由前缀与服务区域列出对齐。时紧急为**否**，这意味着，ExpressRoute 不支持此终结点设置。但是，它不应假定不路由将公布为终结点集其中紧急为**否**。

- **地址**： 列出的 Fqdn 或通配符域名和终结点设置的 IP 地址范围。请注意，IP 地址范围是 CIDR 格式可能包含指定的网络中的许多单个 IP 地址。
 
- **端口**： 列出了结合地址以形成网络终结点的 TCP 或 UDP 端口。您可能会注意到 IP 地址范围中的有些重复在没有列出不同的端口。

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

