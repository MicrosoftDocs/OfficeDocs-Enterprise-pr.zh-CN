---
title: 在 ExpressRoute for Office 365 方案中使用 BGP 社区
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: '使用 Azure ExpressRoute 连接到 Office 365 基于特定 IP 子网的 BGP 播发, 这些子网代表部署 Office 365 终结点的网络。 由于 Office 365 的全球性质以及构成 Office 365 的服务的数量, 客户通常需要在其网络上管理他们接受的广告。 减少 IP 子网的数量;在本文的其余部分中称为 IP 前缀, 以与 BGP 网络管理术语保持一致, 为客户提供以下最终目标:'
ms.openlocfilehash: 37fef66aeccc0fcd2102463384ebc2341b9c37e8
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782342"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>在 ExpressRoute for Office 365 方案中使用 BGP 社区

使用 Azure ExpressRoute 连接到 Office 365 基于特定 IP 子网的 BGP 播发, 这些子网代表部署 Office 365 终结点的网络。 由于 Office 365 的全球性质以及构成 Office 365 的服务的数量, 客户通常需要在其网络上管理他们接受的广告。 减少 IP 子网的数量;在本文的其余部分中称为 IP 前缀, 以与 BGP 网络管理术语保持一致, 为客户提供以下最终目标:
  
- **管理已接收的已接受的 ip 前缀数**—具有内部网络基础结构或网络运营商的客户, 这些前缀仅支持有限数量的 ip 前缀和网络运营商为接受前缀付费的客户。在有限的号码上, 需要评估已公布给其网络的前缀总数, 并选择最适合于 ExpressRoute 的 Office 365 应用程序。

- **管理 Azure ExpressRoute 电路上所需的带宽量**-客户可能希望通过 ExpressRoute 路径和 Internet 路径控制 Office 365 服务的带宽信封。 这样, 客户可以为特定的应用程序 (如 Skype for Business) 预留 ExpressRoute 带宽, 并通过 Internet 路径路由其余的 Office 365 应用程序。

为了帮助客户实现这些目标, 通过 ExpressRoute 播发的 Office 365 IP 前缀使用服务特定的 BGP 团体值进行标记, 如下面的示例所示。
  
> [!NOTE]
> 应预计与其他应用程序关联的一些网络流量将包含在社区值中。 这是全球软件的预期行为, 即使用共享服务和数据中心提供的服务。 在可能的情况下, 这两个目标已最小化, 可管理前缀计数和/或带宽。

|**服务**|**BGP 社区值**|**Notes**|
|:-----|:-----|:-----|
|汇票\*  <br/> |12076:5010  <br/> |包括 Exchange 和 EOP 服务\*  <br/> |
|sharepoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|skype for business\*  <br/> |12076:5030  <br/> |Skype for Business Online  <br/> |
|其他 Office 365 服务\*  <br/> |12076:5100  <br/> |包括 Azure Active Directory (身份验证和目录同步方案) 以及 Office 365 门户服务  <br/> |
|\*在 ExpressRoute 中包含的服务方案的范围记录在[Office 365 终结点](https://aka.ms/o365endpoints)文章中。  <br/> \*\*将来可能会添加其他服务和 BGP 社区值。 [查看 BGP 社区的当前列表](https://azure.microsoft.com/documentation/articles/expressroute-routing/)。  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>使用 BGP 社区最常见的方案是什么？

客户可以使用 BGP 社区来调节通过 Azure ExpressRoute 通过其网络接受的 IP 前缀组, 从而影响特定 Office 365 服务的总 IP 前缀计数和预期带宽信封。 应了解所有 Office 365 将需要 internet 绑定流量, 而不考虑使用 Azure ExpressRoute 或 BGP 社区, 这一点非常重要。 以下三种方案是此功能最常见的用法。
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>方案 1: 最大限度地减少 Office 365 IP 前缀的数目

Contoso Corporation 是一家50000个人公司, 目前使用 Office 365 for Exchange Online 和 SharePoint Online。 在查看 ExpressRoute 要求中, Contoso 确定了许多区域位置中的网络设备无法处理超过100个其他路由条目的路由表大小。 Contoso 检查了 ExpressRoute 对整套 Office 365 服务广告的 IP 前缀总数, 并最终表明它超过了100。 若要保持在100其他路由条目的下方, Contoso 将使用 ExpressRoute for Office 365 的使用限定为 SharePoint Online BGP 社区值 12076:5020, 通过 ExpressRoute Microsoft 对等项接收。

|**使用的 BGP 社区标记**|**通过 Azure ExpressRoute 路由的功能**|**需要 Internet 路由**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive for business  <br/> | DNS、CRL 和&amp; CDN 请求  <br/>  所有其他 Office 365 服务不是通过 Azure ExpressRoute 专门支持的  <br/>  所有其他 Microsoft 云服务  <br/>  Office 365 门户、Office 365 身份验证&amp; 、office 在浏览器中  <br/>  Exchange Online、Exchange Online Protection 和 Skype for Business Online  <br/> |

> [!NOTE]
> 若要为每个服务实现较低的前缀计数, 服务之间的重叠量最少将持续存在。 这是预期的行为。
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>方案 2: 对某些 Office 365 服务应用范围的 ExpressRoute 和内部带宽使用

Fabrikam Inc. (一个大型多国企业, 具有分布式异类网络) 是许多 Office 365 服务的订阅者, 包括:Exchange Online、SharePoint Online 和 Skype for Business Online。 Fabrikam 的内部路由基础结构可以在其路由表中处理数千个 IP 前缀;但是, Fabrikam 只需要为 Office 365 应用程序设置 ExpressRoute 和内部带宽, 这些应用程序对网络性能敏感, 并对所有其他 Office 365 应用程序使用其现有 Internet 带宽。
  
因此, Fabrikam 将其 Azure ExpressRoute 带宽限定为 Skype for business Online BGP 社区价值 12076:5030, 通过 ExpressRoute Microsoft 对等的 Microsoft 对等。 与 Office 365 关联的其余网络流量将继续使用 internet 出局点。

|**使用的 BGP 社区标记**|**通过 Azure ExpressRoute 路由的功能**|**需要 Internet 路由**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype SIP 信号、下载、语音、视频和桌面共享  <br/> | DNS、CRL 和&amp; CDN 请求  <br/>  所有其他 Office 365 服务不是通过 Azure ExpressRoute 专门支持的  <br/>  所有其他 Microsoft 云服务  <br/>  Office 365 门户、Office 365 身份验证&amp; 、office 在浏览器中  <br/>  Skype for Business 遥测、Skype 客户端快速提示、公用 IM 连接  <br/>  Exchange Online、Exchange Online Protection 和 SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>方案 3: 仅为 Office 365 服务限定 Azure ExpressRoute

Woodgrove Bank 是几个 Microsoft 云服务 (包括 Office 365) 的客户。 在评估其网络容量和消费版时, Woodgrove Bank 决定将 Azure ExpressRoute 部署为受支持的 Office 365 服务的首选路径。 路由表可支持整套 Office 365 IP 前缀, 以及它们预配的 Azure ExpressRoute 电路支持所有预计的带宽和延迟需求。
  
为了确保与 Microsoft 云服务 (而非 Office 365) 相关联的网络流量, Woodgrove Bank 将使用 ExpressRoute for Office 365 到所有使用 Office 365 的 IP 前缀 (针对特定 BGP 社区值、12076:5010、12076:5020、12076:5030)。12076:5100。

|**使用的 BGP 社区标记**|**通过 Azure ExpressRoute 路由的功能**|**需要 Internet 路由**|
|:-----|:-----|:-----|
|Exchange、Skype for Business、SharePoint 和&amp;其他服务  <br/> (12076:5010、12076:5020、12076:5030、12076:5100)  <br/> |Exchange Online &amp; Exchange online Protection  <br/> SharePoint Online &amp; OneDrive for business  <br/> Skype SIP 信号、下载、语音、视频和桌面共享  <br/> Office 365 门户、Office 365 身份验证&amp; 、office 在浏览器中  <br/> | DNS、CRL 和&amp; CDN 请求  <br/>  所有其他 Office 365 服务不是通过 Azure ExpressRoute 专门支持的  <br/>  所有其他 Microsoft 云服务  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>使用 BGP 社区的主要规划注意事项

选择利用 BGP 社区来影响如何通过客户网络来播发和传播 ExpressRoute 的客户应考虑考虑以下事项:
  
- 在网络设计中使用 BGP 社区时, 务必确保路由对称仍保持。 在某些情况下, BGP 社区的添加或删除可能会导致对称路由断开, 并且必须更新路由配置以重新建立对称路由。

- 使用 BGP 社区值对 Azure ExpressRoute 进行作用域是一个客户操作。 Microsoft 将公布与对等关系相关联的所有 IP 前缀, 而不考虑客户配置的任何作用域。

- Azure ExpressRoute 不支持基于客户分配的 BGP 社区在 Microsoft 网络上执行的任何操作。

- Office 365are 使用的 IP 前缀仅标记有服务特定 BGP 社区值, 不支持位置特定的 BGP 社区。 Office 365 服务在本质上是全局性的, 不支持基于租户的位置或 Office 365 云中的数据筛选前缀。 建议的方法是将网络配置为将用户的网络位置中的最短或最首选网络路径与 Microsoft 全局网络进行协调, 而不考虑 Office 365 服务的 IP 地址的物理位置。他们正在请求。

- 每个 BGP 团体值中包含的 IP 前缀代表一个子网, 其中包含与值关联的 Office 365 应用程序的 IP 地址。 在某些情况下, 多个 Office 365 应用程序具有子网中的 IP 地址, 从而导致 IP 前缀存在于多个团体值中。 这是预期的行为, 但很少是由于分配碎片而导致的行为, 不会影响前缀计数或带宽管理目标。 鼓励客户使用适用于 Office 365 的 BGP 社区以最大限度地减少影响时 "允许所需的操作" 方法, 而不是 "拒绝所需的"。

- 使用 BGP 社区不会更改基础网络连接要求或使用 Office 365 所需的配置。 需要访问 Office 365 的客户仍需要能够访问 Internet。

- 使用 BGP 社区确定 Azure ExpressRoute 的作用域仅影响您的内部网络可以通过 Microsoft 对等关系进行的路由。 您可能需要将其他应用程序级别的配置 (如使用 PAC 或 WPAD 配置) 与作用域路由结合使用。

- 除了使用 Microsoft 分配的 BGP 社区之外, 客户还可以选择将自己的 BGP 社区分配给通过 Azure ExpressRoute 获知的 Office 365 IP 前缀, 以影响内部路由。 一个常见的用例是为通过每个给定的 ExpressRoute 对等位置获知的所有路由分配一个基于位置的 BGP 社区, 然后使用客户网络中下游的信息将最短或最优先的网络路径协调为Microsoft 的网络。 将客户分配的 BGP 社区用于 Office 365 方案的使用超出了 Microsoft control 或 visibility 的范围。

以下是可用于返回的简短链接: [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365)。
  
## <a name="related-topics"></a>相关主题

[评估 Office 365 网络连接](assessing-network-connectivity.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 路由](routing-with-expressroute.md)
  
[ExpressRoute for Office 365 网络计划](network-planning-with-expressroute.md)
  
[Skype for Business Online 中的媒体质量和网络连接性能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype for Business Online 中的 ExpressRoute 和 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 的呼叫流](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[实现 ExpressRoute for Office 365](implementing-expressroute.md)
  
[对 BGP 社区的支持](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)
  
[Office 365 性能疑难解答计划](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)（Azure ExpressRoute for Office 365 培训）
