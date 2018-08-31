---
title: ExpressRoute for Office 365 路由
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/7/2017
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
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: 要正确了解到 Office 365 使用 Azure ExpressRoute 路由流量，您将需要严格掌握的核心 ExpressRoute 路由要求的 ExpressRoute 电路和路由域。这些排放使用 ExpressRoute 将依赖于 Office 365 客户的基础知识。
ms.openlocfilehash: e80ce78c0b229881349a4d02c7708fb9509748a9
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539580"
---
# <a name="routing-with-expressroute-for-office-365"></a>ExpressRoute for Office 365 路由

要正确了解到 Office 365 使用 Azure ExpressRoute 路由流量，您将需要严格理解核心[ExpressRoute 路由要求](https://azure.microsoft.com/documentation/articles/expressroute-routing/)以及[ExpressRoute 电路和路由域](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)。这些排放使用 ExpressRoute 将依赖于 Office 365 客户的基础知识。
  
一些您需要了解的上述文章中的键项包括：
  
- ExpressRoute 电路未映射到特定的物理基础结构，但逻辑 Microsoft 和替您对等提供商在单个对等位置进行连接。

- 没有一对一映射 ExpressRoute 电路之间客户的键。

- 每个电路可以支持多达 3 独立对等关系 （Azure 公共对等、 Azure 专用的对等和 Microsoft 对等）;Office 365 需要 Microsoft 对等。

- 每个电路具有跨所有对等关系共享固定的带宽。

- 任何公共 IPv4 地址和公共为将使用的号码的 ExpressRoute 电路必须验证为归，或以独占方式向您分配所有者的地址范围。

- 虚拟 ExpressRoute 电路为冗余全局，并且将按照标准 BGP 路由做法。这是我们为何建议出口每两个物理电路到您主动/主动配置中的提供程序。

请参阅[常见问题页](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)的多个服务支持的信息、 成本和配置的详细信息。在连接提供程序提供 Microsoft 对等支持的列表，请参阅[ExpressRoute 位置文章](https://azure.microsoft.com/documentation/articles/expressroute-locations/)的信息。我们还录制可帮助更全面地介绍的概念第 9 频道上一个 10 部分[Azure ExpressRoute 有关 Office 365 培训](https://channel9.msdn.com/series/aer)系列。
  
## <a name="ensuring-route-symmetry"></a>确保路由对称

Office 365 前端服务器可访问 Internet 和 ExpressRoute 上。这些服务器将愿意路由通过 ExpressRoute 电路时都可用。由于这是路由不对称的可能性过程，如果您的网络流量倾向于通过 Internet 电路路由。非对称路由会出现问题，因为执行状态数据包检查设备可以阻止返回通信的出站数据包关注以外的其他路径。
  
无论是否通过 Internet 或 ExpressRoute 启动连接到 Office 365，源必须为公共可路由的地址。对等直接与 Microsoft 的许多客户，与具有专用地址其中重复客户之间可能不可行。
  
下面的这些的方案将其中启动与本地网络从 Office 365 的通信。若要简化您的网络设计，我们建议路由这些通过 Internet 路径。
  
- 在登录的密码验证过程的 ADFS。

- [Exchange Server 混合部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。

- 从 Exchange Online 租户的邮件到的本地主机正在

- 从 SharePoint Online，SharePoint Online 邮件发送到的本地主机。

- [SharePoint 联合混合搜索](https://technet.microsoft.com/library/dn197174.aspx)。

- [SharePoint 混合 BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [Skype 业务混合](https://technet.microsoft.com/en-us/library/jj205403.aspx)和/或[业务联盟的 Skype](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype 商业云连接器](https://technet.microsoft.com/library/mt605227.aspx )。

对于 Microsoft 以路由至您的网络的这些双向通信流后，必须与 Microsoft 共享 BGP 路由到内部部署的设备。
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>确定哪些应用程序和功能通过 ExpressRoute 路由

当您配置使用 Microsoft 的对等路由域的对等关系，并批准的适当的访问权限时，您将能够看到通过 ExpressRoute 可用的所有 PaaS 和 SaaS 服务。可以通过[BGP 社区](https://aka.ms/bgpexpressroute365)或[路由筛选器](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)管理 Office 365 服务为 ExpressRoute 设计。
  
Office 365 视频，如其他应用程序是 Office 365 应用程序;但是，Office 365 视频组成三个不同的组件、 门户、 流式服务和内容交付网络。门户驻留在 SharePoint Online，流式服务生活 Azure 媒体服务内和内容交付网络内 Azure CDN 它们。下表概括了这些组件。
  
| |
|**组件**|**基础应用程序**|**SharePoint Online BGP 社区中包括？**|**使用**|
|:-----|:-----|:-----|:-----|
|Office 365 视频门户  <br/> |SharePoint Online  <br/> |是  <br/> |配置、 上载  <br/> |
|Office 365 视频流服务  <br/> |Azure 媒体服务  <br/> |否  <br/> |在事件视频不可 CDN 中所使用的传输服务  <br/> |
|Office 365 视频内容交付网络  <br/> |Azure CDN  <br/> |否  <br/> |主要来源的视频下载/流。[详细了解 Office 365 视频网络](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e)。<br/> |

可使用 Microsoft 对等的 Office 365 功能的每个[Office 365 终结点文章](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)中列出的应用程序类型和 FQDN。表中使用的 FQDN 的原因是允许客户使用 PAC 文件或其他代理服务器配置管理通信，请参阅[管理 Office 365 终结点](https://aka.ms/manageo365endpoints)例如 PAC 文件我们指南。
  
在某些情况下，我们使用一个或多个 sub Fqdn 将不同的高级别通配符域公布的通配符域。这通常发生在通配符代表长所有公布到 ExpressRoute 和 Internet 时小型子集中的目标仅播发到 Internet 或相反的服务器的列表。请参阅以下表格以了解差异在何处。
  
此表格显示通配符公布的 Fqdn 到 internet 并 Azure ExpressRoute 旁公布到 internet 仅 sub Fqdn。

|**通配符域播发到 ExpressRoute 和 Internet 电路**|**Sub FQDN 播发到 Internet 电路仅**|
|:-----|:-----|
|\*。 microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*。 officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

PAC 文件通常用于将网络请求发送到 ExpressRoute 播发直接向电路终结点和到您的代理服务器的所有其他网络请求。如果您正在配置 PAC 文件如下所示，撰写按以下顺序您 PAC 文件：
  
1. 发送达到您的代理服务器的流量您 PAC 文件顶部上表中包括从第二列的 sub Fqdn。我们已经建立您可以使用我们在[管理 Office 365 终结点](https://aka.ms/manageexpressroute365)上一文中的示例 PAC 文件。

2. 包括所有 Fqdn 标记下方的第一节，[本文](https://aka.ms/o365endpoints)中播发到 ExpressRoute 流量直接发送到 ExpressRoute 电路。

3. 包含任何其他网络终结点或下面这些两个条目，发送达到您的代理服务器的流量的规则。

此表格显示到 Internet 电路仅旁播发到 Azure ExpressRoute sub Fqdn 和 Internet 电路公布的通配符域。上方，两列中的 Fqdn 您 PAC 文件下表列出了为被播发到链接引用，这意味着它们将包含在文件中条目的第二个组的 ExpressRoute。

|**通配符域播发到 Internet 电路仅**|**Sub FQDN 播发到 ExpressRoute 和 Internet 电路**|
|:-----|:-----|
|\*。 office.com  <br/> |\*。 outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*。 office.net  <br/> |agent.office.net  <br/> |
|\*。 office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*。 outlook.com  <br/> |\*。 protection.outlook.com  <br/> \*。 mail.protection.outlook.com  <br/> 自动发现-\<租户\>。 outlook.com  <br/> |
|\*。 windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>通过 Internet 和 ExpressRoute 路由 Office 365 通信

若要将路由到 Office 365 您选择您的应用程序需要确定数的关键因素。
  
1. 应用程序将需要多少带宽。采样现有使用率是您的组织中的 determining 这仅可靠方法。

2. 所需的网络流量对哪些出口位置保留您的网络。您应规划最小化连接到 Office 365 的网络延迟，因为这将对性能的影响。因为 Skype for Business 使用实时语音和视频很特别容易较差的网络延迟的影响。

3. 如果希望所有或您的网络位置来利用 ExpressRoute 的子集。

4. 哪些位置选的网络提供商提供从 ExpressRoute。

一旦您确定这些问题的解答，可以设置 ExpressRoute 电路符合的带宽和位置需求。有关更多网络规划帮助，请参阅[优化指南的 Office 365 网络](https://aka.ms/tune)和[上如何 Microsoft 句柄网络性能规划的案例研究](https://aka.ms/tunemsit)。
  
### <a name="example-1-single-geographic-location"></a>示例 1： 单一的地理位置
  
本示例为虚构的公司名为 Trey Research 拥有一个地理位置的方案。
  
在 Trey Research 的员工只能连接到的服务和安全部门明确允许 sit 企业网络和其 ISP 之间的出站代理的对 internet 上的网站。
  
Trey research 一计划用于 Office 365 的 Azure ExpressRoute 和识别，如内容交付网络的通信一些通信不能通过 Office 365 连接 ExpressRoute 路由。所有通信默认情况下的已路由到代理设备，因为这些请求将继续照常工作。Trey Research 确定它们可以满足 Azure ExpressRoute 路由要求后，它们将继续创建电路，配置路由，并将新的 ExpressRoute 电路链接到虚拟网络。位置的基本 Azure ExpressRoute 配置后，Trey Research 使用[#2 PAC 文件，我们将发布](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)到路由流量与客户特定数据通过直接 ExpressRoute 的 Office 365 连接。
  
下图中所示，Trey Research 是能够满足要求将通过 ExpressRoute 路由和出站代理配置更改结合使用 Office 365 通信路由通过 internet 和流量的子集。
  
1. Office 365 的 Azure ExpressRoute 使用[#2 PAC 文件，我们将发布](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)到路由流量通过单独的 internet 出口点。

2. 客户端都配置了达到 Trey Research 的代理的默认路由。

此示例方案，在 Trey Research 使用出站代理设备。同样，客户不使用 Office 365 的 Azure ExpressRoute 可能需要使用此技术路由流量基于检查已知的较大终结点的通信的成本。
  
最大容量的 Exchange Online、 SharePoint Online 和 Skype 业务 online Fqdn 如下所示：
  
![ExpressRoute 客户边缘网络](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com、 outlook.office.com

- \<租户-name\>。 sharepoint.com，\<租户名称\>-my.sharepoint.com，\<租户名称\>-\<应用程序\>。 sharepoint.com

- \*.Lync.com 以及非 TCP 通信的 IP 范围

- \*broadcast.officeapps.live.com， \*excel.officeapps.live.com， \*onenote.officeapps.live.com， \*powerpoint.officeapps.live.com， \*view.officeapps.live.com， \*visio.officeapps.live.com， \*word-edit.officeapps.live.com \*word view.officeapps.live.com、 office.live.com

详细了解如何[部署和管理代理设置，在 Windows 8](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx)和[确保 Office 365 不会限制您的代理](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx)。
  
使用单个 ExpressRoute 电路，Trey Research 的没有高可用性。在事件的处理的 ExpressRoute 连接的边缘设备 Trey 的冗余对发生故障，是不故障转移到其他 ExpressRoute 电路。故障转移到 internet 将需要手动重新配置和新的 IP 地址在某些情况下，此值保留在 predicament Trey Research。如果 Trey 想要添加的高可用性，最简单的解决方案是添加的每个位置的其他 ExpressRoute 电路和主动/主动方式配置电路。
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Office 365 具有多个位置的路由 ExpressRoute

最后一个方案中，通过 ExpressRoute 路由 Office 365 通信是甚至更复杂的路由体系结构的基础。无论位置数、 数这些位置所在的大洲、 数个 ExpressRoute 电路等等，将需要能够通过 ExpressRoute 一些通信路由到 Internet 和一些流量。
  
具有多个地理区域中的多个位置的客户必须回答的其他问题包括：
  
1. 是否需要中每个位置 ExpressRoute 电路？如果您对业务联机使用 Skype 或 SharePoint Online 或 Exchange Online 的延迟敏感度担心，主动/主动 ExpressRoute 电路冗余对建议在每个位置。请参阅业务媒体质量和网络的详细信息的连接指南 Skype。

2. 如果在特定区域 ExpressRoute 电路不可用，如何应发送到 Office 365 流量路由？

3. 对于具有多个小型位置的网络整合通信的首选的方法是什么？

每个提供一个唯一的质询，需要评估您自己的网络，以及可由 Microsoft 提供的选项。

|**注意事项**|**用于计算的网络组件**|
|:-----|:-----|
|在多个位置的电路  <br/> |建议至少两个电路主动/主动方式配置。  <br/> 成本、 延迟和带宽需求必须进行比较。  <br/> 使用 BGP 路由成本、 PAC 文件和 NAT 管理使用多个电路路由。  <br/> |
|从位置不 ExpressRoute 电路路由  <br/> |我们建议出口和 DNS 解析为接近启动 Office 365 的请求的人员。  <br/> DNS 转接可用于允许远程办公室发现相应的端点。  <br/> 远程 office 中的客户端必须具有可提供对 ExpressRoute 电路的访问的路由。  <br/> |
|小型办公整合  <br/> |应仔细比较可用带宽和数据使用情况。  <br/> |

> [!NOTE]
> Microsoft 将通过 internet 首选 ExpressRoute，如果路由可用无论物理位置。
  
每个这些注意事项必须考虑到每个唯一的网络。下面是一个示例。
  
### <a name="example-2-multi-geographic-locations"></a>示例 2： 多个地理位置
  
本示例为虚构的公司调用 Humongous 保险拥有多个地理位置的方案。
  
与世界各地的办事处地理位置分散 humongous 保险。他们要实现保留其 Office 365 通信大部分直接网络连接的 Office 365 的 Azure ExpressRoute。Humongous 保险还具有两个其他洲办公室。远程 office 不可行 ExpressRoute 中的员工需要路由回一个或两个主要的设施，以使用 ExpressRoute 连接。
  
指导原则是尽快获取到 Microsoft 数据中心的 Office 365 发往流量。本示例中，Humongous 保险必须决定其远程办公室应将通过 Internet 或其远程办公室应将通过获取 microsoft 内部网络路由快速获取到 Microsoft 数据中心通过任何连接路由通过 ExpressRoute 连接的数据中心尽可能快。
  
Microsoft 的数据中心、 网络和应用程序体系结构旨在执行全局分散的通信和服务它们可能最有效的方式。这是一个世界上的最大网络。保持不必要的时候客户网络的请求发送到 Office 365 将无法利用此体系结构。
  
在 Humongous 保险的情况下，它们应根据他们想要通过 ExpressRoute 使用的应用程序将继续。例如，如果他们正在 for Business Skype Online 客户，或计划利用 ExpressRoute 连接，连接到外部 Skype 业务联机会议，建议在业务联机媒体质量和网络 Skype 中使用的设计时连接指南是设置为第三个位置其他 ExpressRoute 电路。这可能是较昂贵从网络角度;不过，请求路由从一个洲到另一个之前向 Microsoft 数据中心提供可能会导致出现差或不可用体验期间 Skype 业务联机会议和通信。
  
如果 Humongous 保险不使用或不打算利用 Skype 业务 online 以任何方式，返回到与连接可能 ExpressRoute 洲路由发送到 Office 365 网络流量可行上述可能会导致不必要的延迟或 TCP拥塞。在这两种情况下，路由到 Internet 上的本地网站的目标位置是的流量建议利用内容传递网络的 Office 365 的 Internet 上依赖于。
  
![ExpressRoute 多 geography](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Humongous 保险规划其多 geography 策略时，有大量和需要考虑事项周围大小电路，数电路，故障转移，以此类推。
  
在一个位置使用多个地区尝试使用在电路 ExpressRoute，与 Humongous 保险想要确保已发送到最近的总部的 Office 365 数据中心并接收从远程位置连接到 Office 365总部位置。若要执行此操作，Humongous 保险实现 DNS 转接，以减少往返行程和建立与 Office 365 环境接近总部 internet 出口点的相应连接所需的 DNS 查找的数量。这阻止客户端解析本地前端服务器，并确保联系人连接到前端服务器总部其中 Humongous 保险对等与 Microsoft 附近。您还可以了解到[分配条件转发器域名的名称](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx)。
  
在此方案中，来自远程 office 通信将解决 North America 中的 Office 365 前端基础结构，并利用 Office 365 连接到 Office 365 应用程序的体系结构根据后端服务器。例如，Exchange Online 将终止 North America 中的连接和任何租户驻留位置，这些前端服务器将连接到后端邮箱服务器。所有服务都有广泛分布式的前盖服务组成单播和任意广播目标。
  
如果 Humongous 在多个大洲中具有主要办公室，每个地区的两个主动/主动电路至少，建议使用，以减少延迟的业务 online 敏感如 Skype 的应用程序。如果所有办公室中单个洲，或没有使用实时协作，使合并或分布式出口点是客户特定的决策。当多个电路可用时，BGP 路由将确保故障转移应任何单个电路变得不可用。
  
了解有关示例[路由配置](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/)的详细信息和[https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/)。
  
## <a name="selective-routing-with-expressroute"></a>选择性使用 ExpressRoute 路由

使用 ExpressRoute 选择性路由可能需要的原因，如测试各种向的一部分用户推出 ExpressRoute。有选择性地将 Office 365 网络流量路由通过 ExpressRoute 客户可以使用各种工具：
  
1. **筛选的路由/分离**-允许 BGP 路由到 Office 365 ExpressRoute 转移到您的子网或路由器的子集。这有选择地传送客户网段或物理办公地点。这是常见的 Office 365 ExpressRoute 范围内的分阶段部署并配置 BGP 设备上。

2. **PAC 文件/Url** -用于 Office 365 发送到特定的 Fqdn 上一条具体路径, 路由的网络流量。这有选择地将路由由客户端计算机[PAC 文件部署](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)由标识。

3. **路由筛选** - [路由筛选器](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)是一种方式使用支持的服务，通过 Microsoft 对等的子集。

4. **BGP 社区**-筛选基于[BGP 社区标记](https://aka.ms/bgpexpressroute365)允许客户确定哪些 Office 365 应用程序区域将遍历 ExpressRoute 和该区域将遍历 internet。

这是一个简短的链接，您可以使用回来：[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>相关主题

[与 Office 365 的网络连接](network-connectivity.md)
  
[适用于 Office 365 的 Azure ExpressRoute](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)
  
[ExpressRoute for Office 365 网络规划](network-planning-with-expressroute.md)
  
[实现 ExpressRoute for Office 365](implementing-expressroute.md)
  
[媒体质量和 Skype 中的网络连接性能 for Business 联机](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[为业务 Online 的 Skype 优化您的网络](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute 和 Skype for Business Online 中的 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 呼叫流](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[使用 Office 365 方案中 ExpressRoute BGP 社区 （英文）](bgp-communities-in-expressroute.md)
  
[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的性能疑难解答计划](performance-troubleshooting-plan.md)
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 网络和性能优化](network-planning-and-performance.md)
