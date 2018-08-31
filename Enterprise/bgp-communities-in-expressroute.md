---
title: 使用 Office 365 方案中 ExpressRoute BGP 社区 （英文）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
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
description: 连接到 Office 365 使用 Azure ExpressRoute 基于特定的 IP 子网表示其中部署 Office 365 终结点的网络 BGP 广告。Office 365 和构成 Office 365 服务的数目的全局性质，由于客户常常需要管理他们的网络的参与者接受广告。减少的 IP 子网;称为这篇文章，以与 BGP 网络管理术语，对齐的其余部分 IP 前缀为客户提供以下最终目标：
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539556"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>使用 Office 365 方案中 ExpressRoute BGP 社区 （英文）

连接到 Office 365 使用 Azure ExpressRoute 基于特定的 IP 子网表示其中部署 Office 365 终结点的网络 BGP 广告。Office 365 和构成 Office 365 服务的数目的全局性质，由于客户常常需要管理他们的网络的参与者接受广告。减少的 IP 子网;称为这篇文章，以与 BGP 网络管理术语，对齐的其余部分 IP 前缀为客户提供以下最终目标：
  
- **管理接受号码播发的 IP 前缀**-客户拥有内部网络基础结构或仅支持进行有限的数量的 IP 前缀的网络运营商和客户拥有网络运营商的费用接受前缀上方进行有限数量将用来计算的前缀已公布到他们的网络的总数，选择最适合于 ExpressRoute 哪些 Office 365 应用程序。

- **管理 Azure ExpressRoute 电路所需的带宽量**-客户可能需要以控制与 Internet 路径的 ExpressRoute 路径带宽信封的 Office 365 服务。这样，客户可以保留 ExpressRoute 带宽，如 for Business 的 Skype 的特定应用程序并通过 Internet 路径路由的剩余的 Office 365 应用程序。

若要帮助客户解决这些目标，用服务特定 BGP 社区值，如下面的示例所示标记通过 ExpressRoute 公布的 Office 365 IP 前缀。
  
> [!NOTE]
> 您应产生预期关联与其他应用程序中的社区值包含一些网络流量。这是作为共享的服务与数据中心提供服务的全局软件的预期的行为。其中可能与上述两个目标，管理前缀计数和/或记住的带宽，这已被最小。

|**服务**|**BGP 社区值**|**备注**|
|:-----|:-----|:-----|
|exchange\*  <br/> |12076:5010  <br/> |包括 Exchange 和 EOP 服务\*  <br/> |
|sharepoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype 的业务\*  <br/> |12076:5030  <br/> |Skype for Business Online  <br/> |
|其他 Office 365 服务\*  <br/> |12076:5100  <br/> |Office 365 门户服务以及包含 Azure Active Directory （身份验证和目录同步方案）  <br/> |
|\*[Office 365 终结点](https://aka.ms/o365endpoints)一文中介绍了服务方案 ExpressRoute 中包含的范围。  <br/> \*\*可能将来添加其他服务和 BGP 社区值。[BGP 社区的当前列表，请参阅](https://azure.microsoft.com/documentation/articles/expressroute-routing/)。<br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>使用 BGP 社区的最常见方案有哪些？

客户可能使用 BGP 社区来控制接受通过 Azure ExpressRoute，因此影响的 IP 前缀的总计和预期的带宽信封的某些 Office 365 服务网络的 IP 前缀的组。务必要了解所有 Office 365 都需要 internet 绑定无论使用 Azure ExpressRoute 或 BGP 社区的流量。以下三种情形是此功能的最常见用途。
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>方案 1： 最小化的 Office 365 IP 前缀的数目

Contoso Corporation 是当前使用的 Exchange Online 和 SharePoint Online 的 Office 365 50,000 的员工的公司。在查看 ExpressRoute 要求 Contoso 确定其在许多区域位置的网络设备无法处理路由表大于 100 个其他路由条目。Contoso 审阅 IP 前缀 ExpressRoute 公布的整套 Office 365 服务，并结束它超出 100 的总数。要低于 100 个其他路由条目，Contoso 范围只是 SharePoint Online BGP 社区价值，12076:5020，通过 ExpressRoute Microsoft 对等接收到，将 ExpressRoute 用于 Office 365。

|**使用 BGP 社区标记**|**通过 Azure ExpressRoute 可路由的功能**|**所需的 Internet 路由**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online&amp;的 OneDrive for Business  <br/> | DNS、 CRL， &amp; CDN 请求  <br/>  未专门通过 Azure ExpressRoute 支持所有其他 Office 365 服务  <br/>  所有其他 Microsoft 云服务  <br/>  Office 365 门户、 Office 365 身份验证， &amp; Office Online  <br/>  Exchange Online、 Exchange Online Protection 和 Skype for Business 联机  <br/> |

> [!NOTE]
> 若要实现较低的前缀计数为每个服务，将保留少量的服务之间的重叠。这是预期的行为。
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>方案 2： 范围 ExpressRoute 和内部带宽使用到某些 Office 365 服务

Fabrikam Inc，分布式异构网络，大型跨国企业是包括; 的许多 Office 365 服务的订户Exchange Online、 SharePoint Online 和 Skype for Business 联机。Fabrikam 的内部路由基础结构可处理数千个用其路由表; IP 前缀但是，Fabrikam 只想要设置 ExpressRoute 和最敏感网络性能和所有其他 Office 365 应用程序使用其现有的 Internet 带宽的 Office 365 应用程序的内部带宽。
  
因此，Fabrikam 范围只 Skype 业务在线 BGP 社区值 12076:5030，通过 ExpressRoute Microsoft 对等接收其 Azure ExpressRoute 带宽。与 Office 365 关联的剩余网络流量继续使用 internet 出口点。

|**使用 BGP 社区标记**|**通过 Azure ExpressRoute 可路由的功能**|**所需的 Internet 路由**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype SIP 信号，下载，语音、 视频和桌面共享  <br/> | DNS、 CRL， &amp; CDN 请求  <br/>  未专门通过 Azure ExpressRoute 支持所有其他 Office 365 服务  <br/>  所有其他 Microsoft 云服务  <br/>  Office 365 门户、 Office 365 身份验证， &amp; Office Online  <br/>  Skype 业务遥测、 Skype 客户端的快速提示、 公共 IM 连接  <br/>  Exchange Online、 Exchange Online Protection 和 SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>方案 3： 范围 Azure ExpressRoute for Office 365 服务仅

Woodgrove 银行是包括 Office 365 的多个 Microsoft 云服务的客户。评估网络后容量和消耗 Woodgrove 银行决定部署 Azure ExpressRoute 为受支持的 Office 365 服务的首选路径。路由表可以支持整套 Office 365 IP 前缀，但这些设置 Azure ExpressRoute 电路支持所有计划的带宽和延迟需求。
  
以确保非 Office 365、 Woodgrove 银行范围的所有 IP 前缀，将 ExpressRoute 用于 Office 365 与 Microsoft 云服务相关联的网络通信标记与 Office 365 特定 BGP 社区值、 12076:5010、 12076:5020、 12076:5030，12076:5100。

|**使用 BGP 社区标记**|**通过 Azure ExpressRoute 可路由的功能**|**所需的 Internet 路由**|
|:-----|:-----|:-----|
|Exchange，Skype for Business，SharePoint、&amp;其他服务  <br/> （12076:5010 12076:5020、 12076:5030、 12076:5100）  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online&amp;的 OneDrive for Business  <br/> Skype SIP 信号，下载，语音、 视频和桌面共享  <br/> Office 365 门户、 Office 365 身份验证， &amp; Office Online  <br/> | DNS、 CRL， &amp; CDN 请求  <br/>  未专门通过 Azure ExpressRoute 支持所有其他 Office 365 服务  <br/>  所有其他 Microsoft 云服务  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>重要规划注意事项使用 BGP 社区 （英文）

选择要利用 BGP 社区可影响 ExpressRoute 播发和客户网络通过传播的方式的客户应考虑以下注意事项：
  
- 在很重要，以确保网络设计中使用 BGP 社区时仍保留路由对称。在某些情况下，添加或移除 BGP 社区的可以创建其中对称路由会断开，并且必须更新路由配置重新建立对称路由的情况。

- 使用 BGP 社区值范围 Azure ExpressRoute 是客户操作。Microsoft 将公布无论客户配置的作用域的对等关系与关联的所有 IP 前缀。

- Azure ExpressRoute 不支持基于客户分配 BGP 社区的 Microsoft 的网络上的任何操作。

- 使用 Office 365are IP 前缀仅标记为服务特定 BGP 社区值，不支持特定 BGP 社区的位置。Office 365 服务是全局的性质，筛选前缀基于租户的位置或不支持 Office 365 云中的数据。建议的方法是配置来协调最短的网络或从用户的 Microsoft 全局网络，而不考虑 Office 365 服务的 IP 地址的物理位置到网络位置的首选的网络路径他们正在请求。

- 包含每个 BGP 社区值中的 IP 前缀表示包含关联的值的 Office 365 应用程序的 IP 地址的子网。在某些情况下，多个 Office 365 应用程序具有导致 IP 前缀现有的多个社区值中一个子网内的 IP 地址。这是预期，尽管很少，由于分配碎片的行为和不会影响前缀计数或带宽管理目标。客户是建议用于"允许所需"而不是"拒绝不需要什么"方法时利用 BGP 社区 for Office 365 大程度地减少效果。

- 使用 BGP 社区不更改基础的网络连接要求或使用 Office 365 所需的配置。要访问 Office 365 客户会仍需要能够访问 Internet。

- 与 BGP 社区范围 Azure ExpressRoute 只会影响通过 Microsoft 对等关系可以看到您的内部网络的路由。您可能需要进行其他应用程序使用如 PAC 或 WPAD 配置的级别配置与范围路由结合使用。

- 除了使用 Microsoft 分配 BGP 社区，客户可以选择自己 BGP 社区分配 Office 365 IP 前缀教训通过 Azure ExpressRoute 改变内部路由。受欢迎的用例分配的通过每个对等位置，然后使用中的客户网络下游这些信息来协调最短的给定 ExpressRoute 获知的所有路由到基于位置 BGP 社区或最优先到的网络路径Microsoft 的网络。分配 BGP 社区 ExpressRoute 与 Office 365 方案使用的是客户的 Microsoft 控件的可见性范围之外。

这是一个简短的链接，您可以使用回来： [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365)。
  
## <a name="related-topics"></a>相关主题

[与 Office 365 的网络连接](network-connectivity.md)
  
[适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)
  
[ExpressRoute for Office 365 路由](routing-with-expressroute.md)
  
[ExpressRoute for Office 365 网络规划](network-planning-with-expressroute.md)
  
[媒体质量和 Skype 中的网络连接性能 for Business 联机](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute 和 Skype for Business Online 中的 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 呼叫流](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[实现 ExpressRoute for Office 365](implementing-expressroute.md)
  
[支持 BGP 社区 （英文）](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的性能疑难解答计划](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)（Azure ExpressRoute for Office 365 培训）
