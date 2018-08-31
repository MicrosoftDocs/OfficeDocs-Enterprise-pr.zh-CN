---
title: 管理 ExpressRoute for Office 365 连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Office 365 ExpressRoute 提供备用的路由路径，无须所有通信出口到 internet 访问许多 Office 365 服务。虽然仍需要 internet 连接到 Office 365，但 Microsoft 向您的网络通过 BGP 公布的特定路由进行直接 ExpressRoute 电路首选除非有网络中的其他配置。要配置管理此路由包含的三个公共区域前缀筛选、 安全性和合规性。
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539592"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>管理 ExpressRoute for Office 365 连接

Office 365 ExpressRoute 提供备用的路由路径，无须所有通信出口到 internet 访问许多 Office 365 服务。虽然仍需要 internet 连接到 Office 365，但 Microsoft 向您的网络通过 BGP 公布的特定路由进行直接 ExpressRoute 电路首选除非有网络中的其他配置。要配置管理此路由包含的三个公共区域前缀筛选、 安全性和合规性。
  
> [!NOTE]
> Microsoft 更改 Microsoft Peering 路由域的 Azure ExpressRoute 经过审阅的方式。启动 2017 年 7 月 31，所有 Azure ExpressRoute 客户可以都启用 Microsoft Peering Azure 管理控制台中直接或通过 PowerShell 自定义。启用后 Microsoft Peering，任何客户可以创建路由筛选器以接收 BGP 路由广告 Dynamics 365 客户服务应用程序 （以前称为，CRM Online）。客户需要为 Office 365 的 Azure ExpressRoute 必须从 Microsoft 获取审阅，他们可以针对 Office 365 中创建路由筛选器之前。请联系您的 Microsoft 帐户团队，若要了解有关如何启用 Office 365 ExpressRoute 审阅请求。尝试 Office 365 中创建路由筛选器的未经授权的订阅将收到[错误消息](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>前缀筛选

Microsoft 建议客户接受所有 BGP 路由，如 microsoft 播发、 提供的路由经过严格的检查和验证过程，将删除添加了煜 ・ ｣ ｡ 任何好处。ExpressRoute 本身提供建议的控件，如 IP 前缀所有权、 完整性和规模-与任何筛选在客户端的入站路由。
  
如果您需要路由所有权的其他验证跨 ExpressRoute 公共对等，您可以检查根据表示[Microsoft 的公共 IP 范围](https://www.microsoft.com/download/details.aspx?id=53602)的所有 IPv4 和 IPv6 IP 前缀的列表的播发的路由。这些区域将覆盖完整的 Microsoft 地址空间和更改不频繁，提供了可靠范围进行筛选的组，还为那些担心非 Microsoft 拥有路由到泄漏的客户提供了其他保护其环境。在事件发生更改时，将所做的月 1 日和每次更新该文件时，将更改页上的**详细信息**部分的版本号。
  
有多种原因，以避免使用[Office 365 Url 和 IP 地址范围](https://aka.ms/o365endpoints)的用于生成前缀筛选器列表。其中包括：
  
- Office 365 IP 前缀经过大量经常更改。

- 针对管理防火墙设计范围的 Office 365 Url 和 IP 地址允许列表和代理基础结构，不路由。

- Office 365 Url 和 IP 地址范围不包括 ミ ミ 动 ExpressRoute 连接范围其他 Microsoft 服务。

| |
|**选项**|**复杂度**|**更改控件**|
|:-----|:-----|:-----|
|接受所有 Microsoft 路由  <br/> |**低：** 客户依赖于 Microsoft 控件，以确保正确拥有的所有路由。  <br/> |无  <br/> |
|筛选器 Microsoft 拥有 supernets  <br/> |**中等：** 客户可实现汇总的前缀筛选器列表，以允许仅 Microsoft 拥有路由。  <br/> |客户必须确保非频繁更新会反映在路由筛选器。  <br/> |
|筛选 Office 365 IP 范围  <br/> [!CAUTION] 不建议
|**高：** 客户的筛选器基于定义的 Office 365 IP 前缀的路由。  <br/> |客户必须实现的每月更新稳固更改管理过程。  <br/> [!CAUTION]此解决方案要求重大持续更改。在时间很可能会导致服务中断中未实施的更改。   |

连接到 Office 365 使用 Azure ExpressRoute 基于特定的 IP 子网表示其中部署 Office 365 终结点的网络 BGP 广告。Office 365 和数组成 Office 365 服务的全局性质，由于客户常常需要管理他们的网络的参与者接受广告。如果您担心与公布到您的环境的前缀的号码， [BGP 社区](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)功能允许您筛选公布到一组特定的 Office 365 服务。此功能现在处于预览。
  
无论您管理来自 Microsoft BGP 路由广告的方式，不会获得 Office 365 服务与表达 internet 电路通过连接到 Office 365 相比任何特殊的风险。Microsoft 保留同一安全、 遵从性和性能级别而不考虑电路客户使用连接到 Office 365 的类型。
  
### <a name="security"></a>安全性

Microsoft 建议您保持自己网络和安全的外围控件的连接将与公用 ExpressRoute 和对等 Microsoft，其中包括与 Office 365 服务的连接。安全控件应在的网络请求的差旅出站从您的网络到 Microsoft 的网络，以及从 Microsoft 的网络将到您的网络的入站邮件。
  
#### <a name="outbound-from-customer-to-microsoft"></a>向 Microsoft 客户从出站
  
当计算机连接到 Office 365 时，它们将连接到一组相同的终结点而不考虑是否通过 internet 或 ExpressRoute 电路建立连接。使正在使用的电路，无论 Microsoft 建议您将 Office 365 服务，视为泛型 internet 目标比更受信任。出站安全控件应关注的端口和协议以减少暴露和最小化日常维护。[Office 365 终结点](https://aka.ms/o365endpoints)参考 （英文） 一文中提供所需的端口信息。
  
对于添加的控件，您可以使用在您的代理服务器基础结构中筛选的 FQDN 级别限制或检查发往 internet 或 Office 365 的一些或全部网络请求。维护的 Fqdn 列表，如发布功能和 Office 365 产品发展需要更稳固的变更管理和跟踪更改到已发布的[Office 365 终结点](https://aka.ms/o365endpoints)。
  
> [!CAUTION]
> Microsoft 建议您不要依靠 IP 前缀管理到 Office 365 出站安全。

|**选项**|**复杂度**|**更改控件**|
|:-----|:-----|:-----|
|无限制  <br/> |**低：** 客户允许不受限制出站访问 Microsoft。  <br/> |无  <br/> |
|端口限制  <br/> |**低：** 客户将出站访问限制为 Microsoft 的预期的端口。  <br/> |不常用。  <br/> |
|FQDN 限制  <br/> |**高：** 客户限制对 Office 365 基于的已发布 Fqdn 的出站的访问。  <br/> |每月的更改。  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>从 Microsoft 将到客户的入站邮件
  
有几种需要 Microsoft 启动连接到网络的可选方案。
  
- 在登录的密码验证过程的 ADFS。

- [Exchange Server 混合部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。

- 到的本地主机邮件从 Exchange Online 租户。

- 从 SharePoint Online，SharePoint Online 邮件发送到的本地主机。

- [SharePoint 联合混合搜索](https://technet.microsoft.com/library/dn197174.aspx)。

- [SharePoint 混合 BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [Skype 业务混合](https://technet.microsoft.com/en-us/library/jj205403.aspx)和/或[业务联盟的 Skype](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype 商业云连接器](https://technet.microsoft.com/library/mt605227.aspx )。

Microsoft 建议您接受这些连接通过 internet 电路而不是您 ExpressRoute 电路以减少复杂性。如果您的合规性或性能需要规定必须通过 ExpressRoute 电路接受这些入站的连接，建议使用防火墙或反向代理范围接受的连接。您可以使用[Office 365 终结点](https://aka.ms/o365endpoints)决定的右 Fqdn 和 IP 前缀。
  
### <a name="compliance"></a>合规性

我们不依赖的任何我们合规性控件使用的路由路径。无论是否您通过连接到 Office 365 服务 ExpressRoute 或 internet 电路，我们合规性控件都不会更改。您应当查看不同的遵从性和 Office 365 明白满足您组织需求的最佳选择安全证书级别。
  
这是一个简短的链接，您可以使用回来：[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>相关主题

[内容传递网络](content-delivery-networks.md)
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)（Azure ExpressRoute for Office 365 培训）
