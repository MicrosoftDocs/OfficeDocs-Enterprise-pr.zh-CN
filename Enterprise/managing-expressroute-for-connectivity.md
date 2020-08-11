---
title: 管理 ExpressRoute for Office 365 的连接性
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: 了解如何管理适用于 Office 365 的 ExpressRoute，包括要配置的常见区域，如前缀筛选、安全性和合规性。
ms.openlocfilehash: f62731b9f2fcfcb47504d2f73e9b8874980c4c7e
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606328"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>管理 ExpressRoute for Office 365 的连接性

适用于 Office 365 的 ExpressRoute 提供了备用的路由路径，以达到多个 Office 365 服务，而无需向 internet 传出传出流量。 虽然仍然需要 internet 连接到 Office 365，但 Microsoft 通过 BGP 向网络公布的特定路由使直接 ExpressRoute 电路成为首选，除非网络中存在其他配置。 您可能需要配置用于管理此路由的三个常见方面，包括前缀筛选、安全性和合规性。
  
> [!NOTE]
> Microsoft 更改了 Microsoft 对等路由域对 Azure ExpressRoute 的审查方式。 从2017年7月31日起，所有 Azure ExpressRoute 客户都可以直接从 Azure 管理控制台或通过 PowerShell 启用 Microsoft 对等。 启用 Microsoft 对等关系后，任何客户都可以创建路由筛选器以接收 Dynamics 365 客户参与应用程序的 BGP 路由播发 (以前称为 CRM Online) 。 需要 Azure ExpressRoute for Office 365 的客户必须先从 Microsoft 获取评审，然后才能为 Office 365 创建路由筛选器。 请联系你的 Microsoft 帐户团队以了解如何请求评审以启用 Office 365 ExpressRoute。 尝试为 Office 365 创建路由筛选器的未授权订阅将收到[错误消息](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>前缀筛选

Microsoft 建议客户接受从 Microsoft 播发的所有 BGP 路由，提供的路由经过严格的审核和验证过程将消除对添加的审查的任何好处。 ExpressRoute 本身提供了建议的控件，如 IP 前缀所有权、完整性和扩展-客户端上没有入站路由筛选。
  
如果需要在 ExpressRoute 公共对等之间进行额外的路由所有权验证，则可以针对所有表示[Microsoft 公共 IP 范围](https://www.microsoft.com/download/details.aspx?id=53602)的 IPv4 和 IPv6 IP 前缀列表检查播发的路由。 这些范围涵盖完整的 Microsoft 地址空间并不经常更改，提供了要筛选的一组可靠的范围，同时还为关注非 Microsoft 拥有的路由泄漏到其环境中的客户提供了额外的保护。 如果发生更改，则会在每个月的第一月中进行更改，并且页面的 "**详细信息**" 部分中的版本号在每次更新文件时都会发生变化。
  
为避免使用[Office 365 url 和 IP 地址范围](https://aka.ms/o365endpoints)以生成前缀筛选器列表的原因有很多。 其中包括以下内容：
  
- Office 365 IP 前缀经常会经历大量更改。

- Office 365 Url 和 IP 地址范围旨在管理防火墙允许列表和代理基础结构，而不是路由。

- Office 365 Url 和 IP 地址范围不包含可能在您的 ExpressRoute 连接范围内的其他 Microsoft 服务。

|**选项**|**复杂度**|**更改控件**|
|:-----|:-----|:-----|
|接受所有 Microsoft 路由  <br/> |**低：** 客户依靠 Microsoft 控件来确保所有路由都正确拥有。  <br/> |无  <br/> |
|筛选 Microsoft 拥有的 supernets  <br/> |**中：** 客户实施汇总的前缀筛选器列表，仅允许 Microsoft 拥有的路由。  <br/> |客户必须确保在路由筛选器中反映不常用的更新。  <br/> |
|筛选器 Office 365 IP 范围  <br/> [!CAUTION] 不推荐 |**高：** 客户根据定义的 Office 365 IP 前缀筛选路由。  <br/> |客户必须实施针对每月更新的可靠的更改管理过程。  <br/> [!CAUTION] 此解决方案需要进行大量的日常更改。 未按时实现的更改可能会导致服务中断。   |

使用 Azure ExpressRoute 连接到 Office 365 基于特定 IP 子网的 BGP 播发，这些子网代表部署 Office 365 终结点的网络。 由于 Office 365 的全局特性和组成 Office 365 的服务的数量，客户通常需要在其网络上管理他们接受的广告。 如果你担心向你的环境中播发的前缀数，则[BGP 社区](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)功能允许你将播发筛选为一组特定的 Office 365 服务。 此功能现在处于预览阶段。
  
无论您如何管理来自 Microsoft 的 BGP 路由广告，与仅通过 internet 电路连接到 Office 365 相比，Office 365 服务之间将不会有任何特殊的公开。 无论客户用来连接到 Office 365 的电路类型如何，Microsoft 保持相同的安全性、合规性和性能级别。
  
### <a name="security"></a>安全性

Microsoft 建议您维护您自己的网络和安全外围控制，以实现与 ExpressRoute 公共和 Microsoft 对等的连接，其中包括与 Office 365 服务的连接。 应将从你的网络到 Microsoft 网络的出站网络请求以及从 Microsoft 网络到你的网络的入站网络请求设置安全控制。
  
#### <a name="outbound-from-customer-to-microsoft"></a>从客户到 Microsoft 的出站
  
当计算机连接到 Office 365 时，它们将连接到同一组终结点，而不管是否通过 internet 或 ExpressRoute 电路建立连接。 无论使用哪种电路，Microsoft 建议您将 Office 365 服务视为比通用 internet 目标更受信任。 您的出站安全控制措施应重点放在端口和协议上，以减少暴露和最大限度地减少日常维护。 " [Office 365 终结点](https://aka.ms/o365endpoints)参考" 一文中提供了所需的端口信息。
  
对于添加的控件，可以在代理基础结构中使用 FQDN 级别筛选来限制或检查针对 internet 或 Office 365 的部分或所有网络请求。 将 Fqdn 列表维护为已发布功能，Office 365 产品的演变需要对发布的[Office 365 终结点](https://aka.ms/o365endpoints)进行更强大的更改管理和更改跟踪。
  
> [!CAUTION]
> Microsoft 建议您不要仅依靠 IP 前缀来管理到 Office 365 的出站安全性。

|**选项**|**复杂度**|**更改控件**|
|:-----|:-----|:-----|
|无限制  <br/> |**低：** 客户可以对 Microsoft 进行无限制的出站访问。  <br/> |无  <br/> |
|端口限制  <br/> |**低：** 客户通过预期的端口限制对 Microsoft 的出站访问。  <br/> |偶尔.  <br/> |
|FQDN 限制  <br/> |**高：** 客户根据已发布的 Fqdn 限制对 Office 365 的出站访问。  <br/> |每月更改。  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>从 Microsoft 到客户的入站
  
有几种可选方案需要 Microsoft 启动与网络的连接。
  
- 用于登录的密码验证期间的 ADFS。

- [Exchange Server 混合部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。

- 从 Exchange Online 租户发送到本地主机的邮件。

- SharePoint Online 邮件从 SharePoint Online 发送到本地主机。

- [SharePoint 联合混合搜索](https://technet.microsoft.com/library/dn197174.aspx)。

- [SharePoint 混合 BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [Skype](https://technet.microsoft.com/library/jj205403.aspx) for business 混合和/或[skype for business 联盟](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype For Business 云连接器](https://technet.microsoft.com/library/mt605227.aspx )。

Microsoft 建议您通过 internet 电路接受这些连接，而不是您的 ExpressRoute 电路，以降低复杂性。 如果合规性或性能需求规定必须通过 ExpressRoute 线路接受这些入站连接，则建议使用防火墙或反向代理来限定已接受的连接的范围。 您可以使用[Office 365 终结点](https://aka.ms/o365endpoints)来确定正确的 FQDN 和 IP 前缀。
  
### <a name="compliance"></a>合规性

我们不依赖为任何合规性控制使用的路由路径。 无论您是通过 ExpressRoute 还是 internet 电路连接到 Office 365 服务，我们的合规性控制措施不会更改。 应查看 Office 365 的不同合规性和安全认证级别，以确定满足组织需求的最佳选择。
  
以下是可以用于返回的简短链接：[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>相关主题

[内容分发网络](content-delivery-networks.md)
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)（Azure ExpressRoute for Office 365 培训）
