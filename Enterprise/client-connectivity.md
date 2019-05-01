---
title: 客户端连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: '摘要: 介绍了客户端计算机如何连接到 Office 365 租户, 具体取决于客户端计算机和 Office 365 租户数据中心的位置。'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490556"
---
# <a name="client-connectivity"></a>客户端连接

 **摘要:** 介绍了客户端计算机如何连接到 Office 365 租户, 具体取决于客户端计算机和 Office 365 租户数据中心的位置。
  
Office 365 位于世界各地的 Microsoft 数据中心, 可帮助保持服务正常运行, 即使一个区域中存在重大问题 (例如地震或断电) 也是如此。 当您连接到 Office 365 租户时, 客户端连接将定向到承载租户的相应数据中心。 确定租户的托管位置的规则是由与 Microsoft 的协议定义的。 确定客户端从该数据中心位置获取数据的方式取决于您所使用的服务的体系结构的规则。
  
例如, 当您登录到 Office 365 门户时, 通常是连接到客户端的最接近的数据中心, 然后根据您下一步使用的服务进行定向。 如果你启动电子邮件, 则显示 UI 的初始连接可能仍来自最近的数据中心, 但在最近的数据中心和你的租户所在的数据中心之间可能会打开第二个连接, 以向你显示阅读的电子邮件中的内容。 Microsoft 在世界上十大网络中的一种是快速快速实现数据中心到数据中心连接的操作。
  
阅读本文后, 您很可能了解为什么我们不提供每个数据中心的[Office 365 url 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2), 它们只是相互互联且相互依赖以使这一点成为可行的。
  
如果您使用的是适用于 office 365 的 Azure ExpressRoute, 在大多数情况下, 连接将通过与 Office 365 的专用连接 (而不是此处介绍的公用连接) 进行。 有关客户端连接方式的原则仍是准确的。 了解有关[Office 365 的 Azure ExpressRoute 的](azure-expressroute.md)详细信息。
  
有关 skype for business 网络请求的更多详细信息, 请阅读[skype for business Online 中的文章媒体质量和网络连接性能](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)。

||
|:-----|
| 本文是[Office 365 的网络规划和性能调整](https://aka.ms/tune)的一部分。|

> [!NOTE]
> 我们非常重视管理客户数据, 因此它在我们的数据中心中是安全且保密的。 有关管理隐私所需步骤的详细信息包括在[信任中心](https://go.microsoft.com/fwlink/?LinkID=397383)中。
  
## <a name="connecting-to-the-nearest-datacenter"></a>连接到最接近的数据中心

这是最常见的连接类型, 由 Office 365 门户和 Exchange Online 使用。 在这种情况下, 当客户端尝试连接到 Office 365 时, 其计算机的 DNS 查询将确定其计算机的来源区域, 而 Office 365 会将请求重定向到最近的数据中心。
  
与门户的连接在最近的数据中心停止, 客户端计算机会在该位置显示有关客户端的租户的信息。
  
Exchange Online 将进一步执行操作。 将客户端计算机连接到最接近的数据中心后, 该数据中心内的 Exchange 服务器将连接到租户实际所在的数据中心, 如下面的 "*如何实现此操作" 部分*所示。 然后, 在最近的数据中心中的 Exchange Online 服务器将来自客户端计算机的请求代理到邮箱服务器。 这将通过将电子邮件和日历项目检索到 Microsoft 网络的大量提升来提高客户端计算机的体验速度。
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>这对标准云产品的功能有何作用？

此连接过程是高流量的标准, 高价值 web 应用程序 (如 Office 365)。 在本节中, 我们将概述并说明过程中的步骤。 当客户端计算机与租户不在同一区域中时, 连接的外观会有所不同, 具体取决于客户端连接到的服务。
  
 此图描述了使用标准 Office 365 产品和北美的租户的客户。 在这种情况下, 发出请求的人员将向欧洲旅行, 并从该位置使用 Office 365。
  
1. 客户端计算机将为与 Office 365 关联的 IP 地址请求本地 DNS 服务器。

2. 客户端计算机的本地 dns 服务器会向 Microsoft dns 服务器询问与 Office 365 关联的 IP 地址。

3. Microsoft 的 DNS 服务器返回区域服务器名称 (基于客户端的 DNS 服务器的位置), 客户端计算机重复步骤1和步骤 2, 以获取区域 Office 365 数据中心的 IP 地址。

4. 客户端计算机连接到区域数据中心 IP 地址。

5. Exchange Online 服务器将建立与客户租户驻留的活动数据中心的连接。

![最近的区域数据中心](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>如何使用 sovereign 云产品？

此连接在 sovereign 云产品 (如由 21 Vianet 运营的 Office 365) 中略有不同。 使用 office 365 的 sovereign 实例中的租户, 将接受门户连接的最近的 Office 365 服务器是租户驻留的 sovereign 区域内的服务器。 同样, 在我们的 sovereign 云或标准产品中访问 SharePoint Online 的客户将被定向到租户所在的前端服务器。 请参阅下面的连接到活动数据中心。
  
1. 客户端计算机将为与 Office 365 关联的 IP 地址请求本地 DNS 服务器。

2. 客户端计算机的本地 dns 服务器会向 Microsoft dns 服务器询问与 Office 365 关联的 IP 地址。

3. Microsoft 的 DNS 服务器返回区域服务器名称 (基于客户端的 DNS 服务器的位置), 客户端计算机重复步骤1和步骤 2, 以获取区域 Office 365 数据中心的 IP 地址。

4. 客户端计算机连接到区域数据中心 IP 地址。

5. Exchange Online 服务器将建立与客户租户驻留的活动数据中心的连接。

![最近的区域美国数据中心](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>连接到活动数据中心

连接到活动数据中心是为了进行更厚的数据传输工作负载, 目前由 SharePoint Online 使用。 在这种情况下, 当客户端尝试连接到 Office 365 时, 其浏览器会重定向到其 SharePoint Online 租户的活动数据中心。
  
## <a name="how-does-this-work"></a>这是如何工作的？

当客户端计算机从不同的区域连接到 SharePoint online 时, 该连接将重定向到活动的 SharePoint Online 数据中心。 在这种情况下, 客户使用的是标准产品, 导致门户连接保持在本地, 并且 SharePoint Online 连接将定向到活动数据中心。
  
1. 客户端计算机将为与 Office 365 关联的 IP 地址请求本地 DNS 服务器。

2. 客户端计算机的本地 dns 服务器会向 Microsoft dns 服务器询问与 Office 365 关联的 IP 地址。

3. Microsoft 的 DNS 服务器返回活动 SharePoint Online datacenter 的服务器名称 (基于客户端的 Office 365 租户的位置), 客户端计算机重复步骤1和步骤2以获取活动 Office 365 数据中心的 IP 地址。

4. 客户端计算机连接到活动数据中心 IP 地址。

![活动的美国数据中心](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>通过虚拟专用网络 (vpn) 连接

仅当客户端计算机使用虚拟专用网络 (VPN) 时, 此类型的连接才适用。 实际上, 由于使用了 VPN, Office 365 的行为不会发生更改, 但 vpn 通常用于控制客户端计算机如何建立到 Office 365 的连接, 并且通常会导致性能下降, 因此必须进行覆盖。
  
## <a name="how-does-this-work"></a>这是如何工作的？

当客户端计算机在不同区域建立与企业办公室的 VPN 连接时, 将使用该办公室中的 dns 服务器, 而不是客户端计算机位置的 dns 服务器。 在大多数情况下, 此额外的 VPN 连接会降低 Office 365 体验。 Office 365 服务已经过优化, 可尽可能接近最终用户的服务客户连接。 许多服务利用 Azure edge 网络、内容传递网络以及 Microsoft 网络上的可靠网络容量, 在对 Office 365 服务的网络请求在客户端计算机附近的接近时提供最佳的用户体验尽可能。
  
1. 客户端计算机会向 VPN DNS 服务器请求与 Office 365 关联的 IP 地址。

2. 客户端计算机的 VPN DNS 服务器会向 Microsoft DNS 服务器询问与 Office 365 关联的 IP 地址。

3. Microsoft 的 DNS 服务器返回区域服务器名称 (基于 VPN DNS 服务器的位置), 客户端计算机重复步骤1和步骤 2, 以获取区域 Office 365 数据中心的 IP 地址信息。

4. 客户端计算机连接到与公司办公室最接近的数据中心 IP 地址。它们与之建立了 VPN 连接。

![VPN 数据中心连接](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
以下是可以用于返回的简短链接：[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>另请参阅

[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[与 Office 365 的网络连接](network-connectivity.md)
