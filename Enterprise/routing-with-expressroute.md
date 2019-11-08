---
title: 通过适用于 Office 365 的 ExpressRoute 进行路由
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/14/2017
audience: ITPro
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
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: 若要使用 Azure ExpressRoute 正确了解到 Office 365 的路由流量，您需要对核心 ExpressRoute 路由要求和 ExpressRoute 电路和路由域进行牢固的抓住。 这些指南展示了使用适用于 Office 365 客户将依赖的 ExpressRoute 的基础知识。
ms.openlocfilehash: 6388180613e8abc3e83cfa0c40e84690cfae4543
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031577"
---
# <a name="routing-with-expressroute-for-office-365"></a>通过适用于 Office 365 的 ExpressRoute 进行路由

若要使用 Azure ExpressRoute 正确了解到 Office 365 的路由流量，您需要对核心[ExpressRoute 路由要求](https://azure.microsoft.com/documentation/articles/expressroute-routing/)和[ExpressRoute 电路和路由域](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)进行牢固的抓住。 这些指南展示了使用适用于 Office 365 客户将依赖的 ExpressRoute 的基础知识。
  
您需要了解的以上文章中的一些关键事项包括：
  
- ExpressRoute 电路不会映射到特定的物理基础结构，而是由 Microsoft 和对等提供商在单个对等位置建立的逻辑连接。

- ExpressRoute 电路与客户的键之间存在1:1 映射关系。

- 每个电路都可以支持2个独立的对等关系（Azure 专用对等关系和 Microsoft 对等关系）;Office 365 要求 Microsoft 对等。

- 每个电路都具有在所有对等关系之间共享的固定带宽。

- 任何公用 IPv4 地址和作为 ExpressRoute 电路的公共 AS 号码都必须由您拥有，或由地址范围的所有者以独占方式分配给您。

- 虚拟 ExpressRoute 电路在全局范围内是冗余的，将遵循标准 BGP 路由惯例。 这就是为什么我们在主动/主动配置中为提供商的每个出口推荐两个物理电路。

有关支持服务、成本和配置详细信息的详细信息，请参阅[FAQ 页面](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。 有关提供 Microsoft 对等支持的连接提供程序列表的信息，请参阅[ExpressRoute 位置一文](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。 我们还在频道9上记录了10部分[Azure ExpressRoute For Office 365 培训](https://channel9.msdn.com/series/aer)系列，以帮助更全面地解释这些概念。
  
## <a name="ensuring-route-symmetry"></a>确保路由对称

在 Internet 和 ExpressRoute 上均可访问 Office 365 前端服务器。 当两个服务器都可用时，这些服务器将更愿意路由回本地，而不是 ExpressRoute 回路。 因此，如果你的网络中的流量首选通过 Internet 线路路由，则可能会出现路由不受对称性的情况。 非对称路由是一个问题，因为执行有状态数据包检查的设备可以阻止遵循与出站数据包不同的其他路径的返回流量。
  
无论您是通过 Internet 还是 ExpressRoute 启动到 Office 365 的连接，源都必须是可公开路由的地址。 由于许多客户直接与 Microsoft 进行了直接沟通，因此，在客户之间可以进行重复的专用地址是不可行的。
  
在以下情况下，将启动从 Office 365 到本地网络的通信。 为了简化网络设计，我们建议通过 Internet 路径路由它们。
  
- SMTP 服务（例如从 Exchange Online 租户发送到本地主机或从 SharePoint Online 发送到 SharePoint Online 邮件的邮件）到本地主机。 SMTP 协议在 Microsoft 网络中的使用更为广泛，而不是通过 expressroute 电路共享的路由前缀和在 ExpressRoute 上公布的本地 SMTP 服务器将导致这些其他服务失败。

- 用于登录的密码验证期间的 ADFS。

- [Exchange Server 混合部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。

- [SharePoint 联合混合搜索](https://technet.microsoft.com/library/dn197174.aspx)。

- [SharePoint 混合 BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [Skype](https://technet.microsoft.com/library/jj205403.aspx) for business 混合和/或[skype for business 联盟](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype For Business 云连接器](https://technet.microsoft.com/library/mt605227.aspx )。

为了让 Microsoft 为这些双向流量流路由回网络，必须与 Microsoft 共享本地设备的 BGP 路由。 将路由前缀公布到基于 ExpressRoute 的 Microsoft 时，应遵循以下最佳做法：

1) 不要将相同的公用 IP 地址路由前缀公布到公用 Internet 和 ExpressRoute 上。 强烈建议通过 ExpressRoute 向 Microsoft 传递的 IP BGP 路由前缀播发来自未公布到 internet 的范围。 如果由于可用 IP 地址空间无法实现此目的，则必须确保在 ExpressRoute 上公布更具体的范围，而不是任何 internet 电路。

2) 每个 ExpressRoute 电路使用单独的 NAT IP 池，并将其与 internet 电路分开。

3) 请注意，播发到 Microsoft 的任何路由都会从 Microsoft 网络中的任何服务器中获取网络流量，而不仅仅是通过 ExpressRoute 将其路由到网络的路由。 仅向服务器的播发路由，在这些服务器上定义路由方案并充分理解您的团队。 在网络中的每个的多个 ExpressRoute 电路中公布单独的 IP 地址路由前缀。 
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>确定通过 ExpressRoute 路由的应用程序和功能

当您使用 Microsoft 对等路由域配置对等关系并获得相应访问权限时，您将能够看到通过 ExpressRoute 提供的所有 PaaS 和 SaaS 服务。 为 ExpressRoute 设计的 Office 365 服务可使用[BGP 社区](https://aka.ms/bgpexpressroute365)或[路由筛选器](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)进行管理。
  
其他应用程序（如 Office 365 视频）是 Office 365 应用程序;但是，Office 365 视频由三个不同的组件、门户、流服务和内容传递网络组成。 门户位于 SharePoint Online 中，流服务在 Azure 媒体服务中，内容传递网络在 Azure CDN 中。 下表概述了这些组件。
  
| |
|**组件**|**基础应用程序**|**包含在 SharePoint Online BGP 社区中？**|**使用**|
|:-----|:-----|:-----|:-----|
|Office 365 视频门户  <br/> |SharePoint Online  <br/> |是  <br/> |配置、上传  <br/> |
|Office 365 视频流服务  <br/> |Azure 媒体服务  <br/> |否  <br/> |在从 CDN 中无法使用视频的情况下使用的流式处理服务  <br/> |
|Office 365 视频内容传送网络  <br/> |Azure CDN  <br/> |否  <br/> |视频下载/流的主要来源。 [了解有关 Office 365 视频网络的详细信息](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e)。  <br/> |

每个使用 Microsoft 对等项提供的 Office 365 功能在[office 365 终结点文章](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)中按应用程序类型和 FQDN 列出。 在表中使用 FQDN 的原因是允许客户使用 PAC 文件或其他代理配置来管理流量，请参阅我们的指南来[管理 Office 365 终结点](https://aka.ms/manageo365endpoints)，以获取示例 PAC 文件。
  
在某些情况下，我们使用了一个通配符域，其中一个或多个子系统以不同于较高级别通配符域的方式播发。 如果通配符代表的服务器的列表很长，而这些服务器都公布到 ExpressRoute 和 Internet，则通常会发生这种情况，而一小部分目标只会公布到 Internet 或反向。 请参阅以下表格，了解二者之间的差异。
  
此表显示同时播发到 internet 和 Azure ExpressRoute 的通配符 Fqdn 以及仅播发到 internet 的子 Fqdn。

|**向 ExpressRoute 和 Internet 电路播发的通配符域**|**仅向 Internet 线路播发的子 FQDN**|
|:-----|:-----|
|\*。 microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*。 officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

PAC 文件通常用于将向 ExpressRoute 播发的终结点的网络请求直接发送到该线路，并向代理发送所有其他网络请求。 如果你配置的 PAC 文件与此类似，请按以下顺序撰写 PAC 文件：
  
1. 将上表中第二列的子 Fqdn 包括在 PAC 文件的顶部，向代理发送流量。 我们已为您构建了一个示例 PAC 文件，以供您在有关[管理 Office 365 终结点](https://aka.ms/manageexpressroute365)的文章中使用。

2. 在第一节的下一节中，将所有标记为 "已播发" 的 Fqdn 包括在[本文](https://aka.ms/o365endpoints)中，将流量直接发送到您的 ExpressRoute 电路。

3. 在这两个条目的下方包含任何其他网络终结点或规则，并向代理发送流量。

此表显示仅在与 Azure ExpressRoute 和 Internet 电路一起公布的子 Fqdn 旁公布到 Internet 电路的通配符域。 对于上面的 PAC 文件，下表的第二列中的 Fqdn 被列为在所引用的链接中公布到 ExpressRoute，这意味着将它们包含在文件中的第二组条目中。

|**仅播发到 Internet 线路的通配符域**|**在 ExpressRoute 和 Internet 电路中公布的次 FQDN**|
|:-----|:-----|
|\*。 office.com  <br/> |\*。 outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*。 office.net  <br/> |agent.office.net  <br/> |
|\*。 office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*。 outlook.com  <br/> |\*。 protection.outlook.com  <br/> \*。 mail.protection.outlook.com  <br/> 自动发现\<-\>outlook.com  <br/> |
|\*。 windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>通过 Internet 和 ExpressRoute 路由 Office 365 流量

若要路由到您选择的 Office 365 应用程序，您需要确定一些关键因素。
  
1. 应用程序所需的带宽量。 抽样现有使用是在组织中确定这一点的唯一可靠方法。

2. 你希望网络流量从哪些传出位置留下你的网络。 您应计划最大限度地减少与 Office 365 的连接的网络延迟，因为这会影响性能。 由于 Skype for Business 使用实时语音和视频，因此尤其容易受到较差的网络延迟。

3. 如果您希望所有或一部分网络位置都利用 ExpressRoute。

4. 您选择的网络提供商提供了 ExpressRoute 的位置。

在您确定这些问题的答案后，您可以预配符合带宽和位置需求的 ExpressRoute 电路。 有关网络规划帮助的更多详细信息，请参阅[Office 365 网络优化指南](https://aka.ms/tune)和[案例研究，了解 Microsoft 如何处理网络性能规划](https://aka.ms/tunemsit)。
  
### <a name="example-1-single-geographic-location"></a>示例1：单个地理位置
  
本示例是一个名为 Trey Research 的虚构公司的方案，其中包含一个地理位置。
  
Trey research 中的员工只允许连接到 internet 上的服务和网站，安全部门明确允许在公司网络和其 ISP 之间的出站代理对。
  
Trey Research 计划使用 Azure ExpressRoute for Office 365，并认识到某些流量（如发送到内容传递网络的流量）将无法通过 ExpressRoute for Office 365 连接进行路由。 由于所有流量在默认情况下已路由到代理设备，因此这些请求将继续正常工作。 Trey Research 确定它们可以满足 Azure ExpressRoute 路由要求后，它们将继续创建电路，配置路由，并将新的 ExpressRoute 线路链接到虚拟网络。 基础 Azure ExpressRoute 配置准备就绪后，Trey Research 将使用[我们发布的 #2 PAC 文件](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)，通过直接 ExpressRoute for Office 365 连接路由流量，并通过客户特定数据路由流量。
  
如下图所示，Trey Research 能够满足通过使用路由和出站代理配置更改的组合来通过 internet 路由 Office 365 通信的要求以及通过 ExpressRoute 的流量的子集。
  
1. 使用[#2 PAC 文件，我们发布这些文件](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)，通过单独的 internet 出局点为 Office 365 路由流量。

2. 将客户端配置为向 Trey research 的代理提供默认路由。

在此示例方案中，Trey Research 使用出站代理设备。 同样，不使用 Azure ExpressRoute for Office 365 的客户可能想要使用此技术来根据检查流量（针对众所周知的高容量终结点）的成本路由流量。
  
Exchange Online、SharePoint Online 和 Skype for business Online 的最大卷 Fqdn 如下：
  
![ExpressRoute 客户边缘网络](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com、outlook.office.com

- \<\>租户-sharepoint.com \<，租户-name\>-my.sharepoint.com， \<租户-名称\>-\<应用\>。 sharepoint.com

- \*.Lync.com 以及非 TCP 流量的 IP 范围

- \*broadcast.officeapps.live.com、 \*excel.officeapps.live.com、 \*onenote.officeapps.live.com、 \*powerpoint.officeapps.live.com、 \*view.officeapps.live.com、 \*visio.officeapps.live.com、 \*word-edit.officeapps.live.com、 \*word-view.officeapps.live.com、office.live.com

详细了解如何[在 Windows 8 中部署和管理代理设置](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx)，以及如何[确保你的代理不会限制 Office 365](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx)。
  
使用单一 ExpressRoute 电路，Trey Research 没有高可用性。 在事件 Trey 的为 ExpressRoute 连接提供服务的冗余边缘设备对发生故障时，没有其他要故障转移到的 ExpressRoute 电路。 这将在 predicament 中将 Trey 研究保留为故障转移到 internet 需要手动重新配置，在某些情况下还需要新 IP 地址。 如果 Trey 要添加高可用性，最简单的解决方案是为每个位置添加额外的 ExpressRoute 电路，并以主动/主动方式配置电路。
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>具有多个位置的 Office 365 的路由 ExpressRoute

最后一个方案是，通过 ExpressRoute 路由 Office 365 通信是更复杂的路由体系结构的基础。 无论位置的数量、存在这些位置的洲数量、ExpressRoute 电路的数量、ExpressRoute 电路的数量，也都可以将某些流量路由到 Internet，并且需要一些通过 ExpressRoute 的流量。
  
对于在多个地理位置具有多个位置的客户，必须回答的其他问题包括：
  
1. 您是否需要在每个位置都需要一个 ExpressRoute 电路？ 如果您使用的是 Skype for Business Online 或关注 SharePoint Online 或 Exchange Online 的延迟敏感度，则每个位置都建议使用主动/主动 ExpressRoute 电路的冗余对。 有关详细信息，请参阅 Skype for Business 媒体质量和网络连接指南。

2. 如果某个 ExpressRoute 电路在特定区域中不可用，应如何路由 Office 365 发送的通信？

3. 在具有多个小位置的网络的情况下，整合流量的首选方法是什么？

每种方法都有一个独特的难题，需要你评估你自己的网络以及 Microsoft 提供的选项。

|**方面**|**要评估的网络组件**|
|:-----|:-----|
|多个位置中的电路  <br/> |我们建议在主动/主动方式中至少配置两个电路。  <br/> 必须比较成本、延迟和带宽需求。  <br/> 使用 BGP 路由开销、PAC 文件和 NAT 管理使用多个线路的路由。  <br/> |
|从不含 ExpressRoute 电路的位置进行路由  <br/> |我们建议向发起 Office 365 请求的人附近提供出口和 DNS 解析。  <br/> DNS 转发可用于允许远程办公室发现适当的终结点。  <br/> 远程办公室中的客户端必须具有可提供对 ExpressRoute 电路的访问权限的路由。  <br/> |
|小型 office 整合  <br/> |应仔细比较可用带宽和数据使用情况。  <br/> |

> [!NOTE]
> 如果路由可用，则 Microsoft 将首选通过 internet 进行 ExpressRoute，而无需考虑物理位置。
  
每个必须考虑的事项都必须考虑每个唯一的网络。 下面是一个示例。
  
### <a name="example-2-multi-geographic-locations"></a>示例2：多地理位置
  
此示例是一个名为 Humongous insurance 保险业且具有多个地理位置的假想公司的方案。
  
Humongous insurance 保险业在地理位置分散在世界各地的办公室。 他们希望实现适用于 Office 365 的 Azure ExpressRoute，以在直接网络连接上保持 Office 365 的大部分流量。 Humongous insurance 保险业还在两个其他洲拥有办事处。 如果 ExpressRoute 不可行的远程办公室中的员工需要路由回一个或两个主要设施，以使用 ExpressRoute 连接。
  
指导原则是尽可能快地获取指向 Microsoft 数据中心的 Office 365 目标流量。 在此示例中，Humongous insurance 保险业必须决定其远程办公室是否应通过 Internet 路由以尽快访问 Microsoft 数据中心，或者如果其远程办公室应通过内部网络路由以获取 Microsoft数据中心通过 ExpressRoute 连接的速度尽可能快。
  
Microsoft 的数据中心、网络和应用程序体系结构旨在采用全局不同的通信，并以尽可能最有效的方式提供服务。 这是世界上最大的网络之一。 对于那些在超过必需的客户网络中保留的 Office 365 的请求将无法利用此体系结构。
  
在 Humongous insurance 保险业的情况下，它们应根据要在 ExpressRoute 中使用的应用程序继续进行。 例如，如果他们是 Skype for business Online 客户，或者计划在连接到外部 Skype for Business Online 会议时利用 ExpressRoute 连接，则 Skype for Business Online 媒体质量和网络中建议的设计连接指南是为第三个位置设置额外的 ExpressRoute 电路。 从网络的角度来看，这可能更昂贵;但是，在将来自一个洲的请求传送给 Microsoft 数据中心之前，可能会在 Skype for Business Online 会议和通信中导致较差或不可用的体验。
  
如果 Humongous insurance 保险业未使用或未计划以任何方式使用 Skype for Business Online，则使用 ExpressRoute 连接将 Office 365 的目标网络流量路由回带有 ExpressRoute 连接的洲可能会导致不必要的延迟或 TCP拥塞. 在这两种情况下，建议在本地站点将 Internet 目标流量路由到 Internet，以便充分利用 Office 365 所依赖的内容传递网络。
  
![ExpressRoute 多地理位置](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
当 Humongous insurance 保险业规划多地理位置策略时，在电路大小、电路数量、故障转移等方面有很多需要考虑的事项。
  
在具有多个区域（尝试使用电路）的单个位置中，Humongous insurance 保险希望确保从远程办公室连接到 Office 365 的连接到最接近总部的 Office 365 数据中心并由其接收总部位置。 为此，Humongous insurance 保险单将实现 DNS 转发，以减少与与总部 internet 出口点最接近的 Office 365 环境建立适当连接所需的往返行程次数和 DNS 查找。 这将阻止客户端解析本地前端服务器，并确保要连接到的前端服务器位于总部附近，而 Humongous insurance 保险业与 Microsoft 之间具有相同的联系。 您还可以学习为[域名分配条件转发器](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx)。
  
在这种情况下，来自远程办公室的流量将解析北美的 Office 365 前端基础结构，并利用 Office 365 根据 Office 365 应用程序的体系结构连接后端服务器。 例如，Exchange Online 将终止北美的连接，而这些前端服务器将连接到租户驻留的后端邮箱服务器。 所有服务都有一个广泛分布的前门服务，由单播和任意广播目标组成。
  
如果 Humongous insurance 具有多个洲的主要办公室，建议每个地区至少有两个活动/活动电路，以减少对 Skype for Business Online 等敏感应用程序的延迟。 如果所有办公室都在单个洲或不使用实时协作，则有一个合并或分散的出局点是客户特定的决策。 如果有多个电路可用，BGP 路由将确保故障转移是否会有任何单个线路不可用。
  
了解有关示例[路由配置](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/)和[https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/)的详细信息。
  
## <a name="selective-routing-with-expressroute"></a>使用 ExpressRoute 进行选择性路由

由于各种原因，可能需要选择性路由，如测试、将 ExpressRoute 推出到部分用户。 客户可以使用各种工具有选择地路由通过 ExpressRoute 的 Office 365 网络通信：
  
1. **路由筛选/隔离**-允许通过 ExpressRoute 将到 Office 365 的 BGP 路由到子网或路由器的子集。 按客户网络分段或物理办公地点有选择地路由。 这是对 Office 365 的 ExpressRoute 的交错部署的常见情况，在 BGP 设备上进行配置。

2. **PAC 文件/url** -将 Office 365 的目标网络流量定向到特定的 fqdn 以在特定路径上路由。 此方法按[PAC 文件部署](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)所标识的客户端计算机进行选择性路由。

3. **路由筛选** - [路由筛选器](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)是一种通过 Microsoft 对等功能使用受支持的服务子集的方法。

4. **Bgp 社区**-基于[bgp 社区标记](https://aka.ms/bgpexpressroute365)的筛选使客户能够确定哪些 Office 365 应用程序将通过 ExpressRoute 以及将通过 internet 进行遍历。

以下是可以用于返回的简短链接：[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>相关主题

[评估 Office 365 网络连接](assessing-network-connectivity.md)
  
[适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)
  
[ExpressRoute for Office 365 网络计划](network-planning-with-expressroute.md)
  
[实现 ExpressRoute for Office 365](implementing-expressroute.md)
  
[Skype for Business Online 中的媒体质量和网络连接性能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[优化 Skype for Business Online 网络](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype for Business Online 中的 ExpressRoute 和 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 的呼叫流](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[在 ExpressRoute for Office 365 方案中使用 BGP 社区](bgp-communities-in-expressroute.md)
  
[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)
  
[Office 365 性能疑难解答计划](performance-troubleshooting-plan.md)
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 网络和性能优化](network-planning-and-performance.md)
