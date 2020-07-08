---
title: 实现 Office 365 的 VPN 拆分隧道
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/15/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: 如何实现 Office 365 的 VPN 拆分隧道
ms.openlocfilehash: 86b38761568888f0d1a2b5423c6e03e388a207ba
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052485"
---
# <a name="implementing-vpn-split-tunneling-for-office-365"></a>实现 Office 365 的 VPN 拆分隧道

>[!NOTE]
>本主题是一组针对远程用户的 Office 365 优化的主题的一部分。
>- 有关使用 VPN 拆分隧道为远程用户优化 Office 365 连接的概述，请参阅[概述： Office 365 的 VPN 拆分隧道](office-365-vpn-split-tunnel.md)。
>- 有关为中国用户优化 Office 365 全球租户性能的详细信息，请参阅[面向中国用户的 Office 365 性能优化](office-365-networking-china.md)。

多年来，企业一直在使用 VPN 来支持用户的远程体验。 虽然核心工作负载保持在本地，但通过公司网络上的数据中心路由的远程客户端的 VPN 是供远程用户访问公司资源的主要方法。 为保证这些连接的安全性，企业将沿 VPN 路径构建网络安全解决方案层。 这样做是为了保护内部基础结构和保护外部网站的移动浏览，方法是将流量重新路由到 VPN，然后通过本地 Internet 外围设备路由出去。 Vpn、网络外围和关联的安全基础结构通常专门针对定义的流量进行构建和扩展，这通常是从企业网络中启动的大多数连接，并且其中的大部分在内部网络边界内。

在相当长的一段时间内，只要远程用户的并发规模适中且遍历 VPN 的流量较低，那么所有来自远程用户设备的连接都被路由回本地网络的 VPN 模型（这称为**强制隧道**）基本上是可持续的。  一些客户甚至在他们的应用从企业外围转移到公共 SaaS 云之后，仍继续将 VPN 强制隧道用作现状， Office 365 就是一个很好的例子。

将强制隧道 VPN 用于连接分布式和性能敏感云应用程序是非常不理想的，但是这种负面影响可能已经被一些企业所接受，从而从安全的角度维持现状。 下面是此场景的一个示例图：

![拆分隧道 VPN 配置](media/vpn-split-tunneling/vpn-ent-challenge.png)

这个问题多年来一直在加剧，许多客户报告了网络流量模式的重大转变。 用于保持内部部署的流量现在将连接到外部云终结点。 许多 Microsoft 客户报告，以前大约 80% 的网络流量都来自内部（上图中用虚线表示）。 到 2020 年，随着他们将主要的工作负载转移到云上，这一数字现在约为 20% 或更低，这些趋势在其他企业中并不罕见。 随着时间的推移和云历程的发展，上述模型变得愈加累赘且不可持续，这使得组织在迁移到以云为中心的世界时的敏捷度受到影响。

全球 COVID-19 危机升级了此问题，需要立即修正。 确保员工安全的需要对企业 IT 部门提出了前所未有的要求，要求他们支持大规模在家办公的工作效率。 Microsoft Office 365 非常适合帮助客户满足这一需求，但在家中工作的用户的高并发性将生成大量的 Office 365 流量，如果通过强制隧道 VPN 和本地网络外围路由，则会导致快速饱和并运行 VPN 基础结构的容量不足。 在这一新的现实中，使用 VPN 访问 Office 365 不再只是一项性能障碍，而是一个硬留言板，不仅影响 Office 365，而且还需要依赖 VPN 才能运行的关键业务操作。

多年来，Microsoft 一直与客户和更广泛的行业紧密协作，从我们自己的服务中为这些问题提供有效的新式解决方案，并与行业最佳做法保持一致。 Office 365 服务的[连接原则](https://aka.ms/pnc)旨在高效地为远程用户工作，同时仍允许组织保持安全性并控制其连接。 还可以通过有限的工作非常快速地实现这些解决方案，但对上述问题有着重大的积极影响。

Microsoft 建议的优化远程工作者连接策略主要是通过几个简单的步骤快速缓解传统方法的问题，并提供高性能。 这些步骤将针对绕过瓶颈 VPN 服务器的少量定义的终结点调整旧版 VPN 方法。 可在不同的层应用等效的或甚至是更高级的安全模型，而无需在公司网络出口保护所有流量。 在大多数情况下，可以在数小时内有效实现此功能，然后可根据需要以及时间允许的情况下扩展到其他工作负载。

## <a name="common-vpn-scenarios"></a>常见 VPN 方案

在下面的列表中，你将看到企业环境中最常见的 VPN 方案。 大多数客户通常运行模型 1（VPN 强制隧道）。 本部分将帮助您快速且安全地切换到**模式 2**，这在相对较少的情况下能够实现，并且对网络性能和用户体验具有巨大优势。

| **模型** | **说明** |
| --- | --- |
| [1. VPN 强制隧道](#1-vpn-forced-tunnel) | 100% 的流量进入 VPN 隧道，包括内部部署、Internet 和所有 O365/M365 |
| [2. VPN 强制隧道（有几个例外）](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) | 默认情况下使用 VPN 隧道（默认路由指向 VPN），有几个最重要的豁免场景允许直接访问 |
| [3. VPN 强制隧道（有多个例外）](#3-vpn-forced-tunnel-with-broad-exceptions) | 默认情况下使用 VPN 隧道（默认路由指向 VPN），有多个允许直接访问的例外情况（如所有 Office 365、所有 Salesforce、所有 Zoom） |
| [4. VPN 选择性隧道](#4-vpn-selective-tunnel) | VPN 隧道仅用于基于企业的服务。 默认路由（Internet 和所有基于 Internet 的服务）直接转网。 |
| [5. 无 VPN](#5-no-vpn) | #2 的变体，而不是旧版 VPN，所有公司网络服务都通过新式安全方法（如 Zscaler ZPA、Azure Active Directory （Azure AD） Proxy/MCAS 等）进行发布。 |

### <a name="1-vpn-forced-tunnel"></a>1. VPN 强制隧道

这是大多数企业客户最常用的入门方案。 使用强制 VPN，这意味着将100% 的流量定向到公司网络，而不考虑终结点驻留在企业网络中的事实。 然后，任何外部 (Internet) 限制流量（如 Office 365 或 Internet 浏览）都会从本地安全设备（如代理）中回流。 在目前近 100% 的用户都在远程工作的情况下，这种模式会因此给 VPN 基础结构带来极高的负载，很可能会显著降低所有公司流量的性能，从而在危机时刻影响企业的高效运营。

![VPN 强制隧道模型 1](media/vpn-split-tunneling/vpn-model-1.png)

### <a name="2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions"></a>2. VPN 强制隧道（有几个受信任的异常）

对于企业来说，此模型效率更高，因为它允许在此示例中绕过 VPN 隧道并直接转到 Office 365 服务的少数受控制和定义的终结点，这些终结点的负载和延迟非常高，且速度更高。 这显著提高了已卸载服务的性能，同时还减少了 VPN 基础结构上的负载，从而允许仍需要 it 能够在更低的资源争用下运行的元素。 本文是此模型的主要重点，因为它允许简单、定义的操作能够非常快地执行大量的积极结果。

![拆分隧道 VPN 模型 2](media/vpn-split-tunneling/vpn-model-2.png)

### <a name="3-vpn-forced-tunnel-with-broad-exceptions"></a>3. VPN 强制隧道（有多个例外）

第三个模型扩展了模型2的作用域，而不只是直接发送一小组定义的终结点，而是直接向受信任的服务（如 Office 365 和 SalesForce）发送所有流量。 这可进一步减少公司 VPN 基础结构的负载，并提高已定义服务的性能。 由于此模型可能需要更多的时间来评估和实现的可行性，因此在将模型2成功就绪后，可能会在以后反复采取此步骤。

![拆分隧道 VPN 模型 3](media/vpn-split-tunneling/vpn-model-3.png)

### <a name="4-vpn-selective-tunnel"></a>4. VPN 选择性隧道

此模型与第三个模型相反，因为只有标识为具有公司 IP 地址的流量才通过 VPN 隧道发送，因此 Internet 路径是其他所有流量的默认路由。 此模型要求组织能够很好地适应[零信任](https://www.microsoft.com/security/zero-trust?rtc=1)路径，以便能够安全地实现此模型。 应注意的是，此模型或某些变体可能随着时间的推移而成为必要的默认模型，因为越来越多的服务将从公司网络移动到云中。 Microsoft 在内部使用此模型；有关 Microsoft 实现 VPN 拆分隧道的更多信息，请参阅[运行 VPN：Microsoft 如何让远程工作人员互联](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)。

![拆分隧道 VPN 模型 4](media/vpn-split-tunneling/vpn-model-4.png)

### <a name="5-no-vpn"></a>5. 无 VPN

第二个型号的高级版本，通过新式安全措施或 SDWAN 解决方案（如 Azure AD 代理、MCAS、Zscaler ZPA 等）发布任何内部服务。

![拆分隧道 VPN 模型 5](media/vpn-split-tunneling/vpn-model-5.png)

## <a name="implement-vpn-split-tunneling"></a>实现 VPN 拆分隧道

在本节中，你将在[常见 VPN 方案](#common-vpn-scenarios)部分找到将 VPN 客户端体系结构从 _VPN 强制隧道_迁移到 _VPN 强制隧道（有几个受信任的异常）_、[VPN 拆分隧道模型 #2](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) 所需的简单步骤。

下图显示了建议的 VPN 拆分隧道解决方案的工作原理：

![拆分隧道 VPN 解决方案详细信息](media/vpn-split-tunneling/vpn-split-detail.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. 标识要优化的终结点

在 [Office 365 URL 和 IP 地址范围](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)主题中，Microsoft 明确标识需优化的关键终结点，并将其分类为“优化”****。 目前，只有四个 URL 和二十个 IP 子网需要优化。 这一小组的终结点约占 Office 365 服务流量的 70% - 80%，包括延迟敏感终结点（如 Teams 媒体终结点）。 实质上，这是我们需要特别关注的流量，也是将对传统网络路径和 VPN 基础结构施加难以置信压力的流量。

此类别中的 URL 具有以下特征：

- 为 Microsoft 拥有和托管的终结点，托管在 Microsoft 基础结构上
- 提供了 IP
- 低更改率，预计仍保持较小数量（目前有 20 个 IP 子网）
- 带宽和/或延迟敏感
- 可在服务中提供所需的安全元素，而不是在网络上内联
- 约占 Office 365 服务流量的 70-80%

>[!NOTE]
>Microsoft 已经承诺至少在 **2020 年 6 月 30 日**前挂起对 Office 365“优化”**** 终结点的更改，以便客户专注于其他挑战，而不是在最初实施后维护终结点白名单。 本文将进行更新，以反映未来的任何更改。

有关 Office 365 终结点及其分类和管理方式的详细信息，请参阅[管理 Office 365 终结点](managing-office-365-endpoints.md)一文。

#### <a name="optimize-urls"></a>优化 URL

可在下表找到当前的优化 URL。 在大多数情况下，只需在[浏览器 PAC 文件](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic)中使用 URL 终结点，其中终结点被配置为直接发送，而不是发送到代理。

| 优化 URL | 端口/协议 | 用途 |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | 这是 Outlook 用于连接到其 Exchange Online Server 并具有较高带宽使用率和连接计数的主要 URL 之一。 以下联机功能需要低网络延迟：即时搜索、其他邮箱日历、忙/闲查找、管理规则和通知、Exchange Online 存档和电子邮件传出发件箱。 |
| <https://outlook.office.com> | TCP 443 | 此 URL 供 Outlook Online Web 访问用于连接到 Exchange Online Server，并且对网络延迟非常敏感。 使用 SharePoint Online 上传和下载大型文件尤其需要连接。 |
| https:// \<tenant\> 。 sharepoint.com | TCP 443 | 这是 SharePoint Online 的主要 URL，并且具有较高的带宽使用率。 |
| https:// \<tenant\> -my.sharepoint.com | TCP 443 | 这是 OneDrive for business 的主要 URL，具有较高的带宽使用率，并且可能会产生来自 OneDrive for Business 同步工具的高连接计数。 |
| Teams 媒体 IP（无 URL） | UDP 3478、3479、3480 和 3481 | 中继发现分配和实时流量（3478）、音频（3479）、视频（3480）和视频屏幕共享（3481）。 这些是用于 Skype for Business 和 Microsoft 团队媒体流量（呼叫、会议等）的终结点。 当 Microsoft Teams 客户端建立呼叫时，将提供大多数终结点（并包含在为该服务列出的所需 IP 内）。 若要获得最佳媒体质量，需要使用 UDP 协议。   |

在上面的示例中，应将**租户**替换为 Office 365 租户名称。 例如，**contoso.onmicrosoft.com** 将使用 _contoso.sharepoint.com_ 和 _constoso-my.sharepoint.com_。

#### <a name="optimize-ip-address-ranges"></a>优化 IP 地址范围

在写入这些终结点对应的 IP 范围时，如下所示。 **强烈**建议使用[如本例所示的脚本](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category)，[Office 365 IP 和 URL Web 服务](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)或 [URL/IP 页](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)，以便在应用配置时检查是否有任何更新，并定期制定相应的策略。

```
104.146.128.0/17
13.107.128.0/22
13.107.136.0/22
13.107.18.10/31
13.107.6.152/31
13.107.64.0/18
131.253.33.215/32
132.245.0.0/16
150.171.32.0/22
150.171.40.0/22
191.234.140.0/22
204.79.197.215/32
23.103.160.0/20
40.104.0.0/15
40.108.128.0/17
40.96.0.0/13
52.104.0.0/14
52.112.0.0/14
52.96.0.0/14
52.120.0.0/14
```

### <a name="2-optimize-access-to-these-endpoints-via-the-vpn"></a>2. 通过 VPN 优化对这些终结点的访问

我们已确定这些关键终结点，现在需要将其从 VPN 隧道移出，并允许它们使用用户的本地 Internet 连接直接连接到服务。 完成此操作的方式将因使用的 VPN 产品和计算机平台而异，但大多数 VPN 解决方案将允许简单配置策略来应用此逻辑。 有关 VPN 平台特定的拆分隧道指南，请参阅[常见 VPN 平台的操作指南](#howto-guides-for-common-vpn-platforms)。

如果要手动测试解决方案，可执行以下 PowerShell 示例，以在路由表级别模拟解决方案。 本例将每个 Teams 媒体 IP 子网的路由添加到路由表中。 可以在之前和之后测试 Teams 媒体性能，并观察指定终结点路由的差异。

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>示例：将 Teams 媒体 IP 子网添加到路由表

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

在上面的脚本中，_$intIndex_ 是连接到 Internet 的接口索引（可通过在 PowerShell 中运行 **get-netadapter** 找到；查找 _ifIndex_ 的值），_$gateway_ 是该接口的默认网关（可通过在命令提示符中运行 **ipconfig** 或在 PowerShell 中运行 **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway).NextHop** 找到）。

添加路由后，可通过在命令提示符或 PowerShell 中运行 **route print** 来确认路由表是否正确。 输出应包含添加的路由，显示接口索引（本例为 _22_）和该接口的网关（本例为 _192.168.1.1_）：

![路由打印输出](media/vpn-split-tunneling/vpn-route-print.png)

若要在“优化”类别中添加**所有**当前 IP 地址范围的路由，可使用以下脚本变体查询 [Office 365 IP 和 URL Web 服务](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)，以获取当前优化 IP 子网集合并将其添加到路由表。

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>示例：将所有优化子网添加到路由表

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
# Query the web service for IPs in the Optimize category
$ep = Invoke-RestMethod ("https://endpoints.office.com/endpoints/worldwide?clientrequestid=" + ([GUID]::NewGuid()).Guid)
# Output only IPv4 Optimize IPs to $optimizeIps
$destPrefix = $ep | where {$_.category -eq "Optimize"} | Select-Object -ExpandProperty ips | Where-Object { $_ -like '*.*' }
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

如果无意中添加了错误参数的路由，或者只是希望还原所做的更改，则可以使用以下命令删除刚添加的路由：

```powershell
foreach ($prefix in $destPrefix) {Remove-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

<!--- remmed until we add more reliable interface selection logic
#### Example script to add Teams Media subnets to the route table

```powershell
$adapter = get-netadapter | ? {$_.Status -eq "Up"}
$adapterIndex = $adapter.ifIndex
$gateway = (Get-NetIPConfiguration | Foreach IPv4DefaultGateway).NextHop

$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18"
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```
-->

应配置 VPN 客户端，以便**优化** IP 的流量以此方式路由。 这样，流量可以利用本地 Microsoft 资源（例如，Office 365 服务前端）（如[Azure 前端](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/)）等本地 Microsoft 资源，将 office 365 服务和连接终结点提供给你的用户尽可能接近的用户。 这使我们能够向全球各地的用户提供极高的性能级别，并充分利用 [Microsoft 的世界级全球网络](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)，这种情况极可能在用户直接出口的几毫秒内发生。

## <a name="configuring-and-securing-teams-media-traffic"></a>配置和保护 Teams 媒体流量

一些管理员可能需要更详细的信息，了解如何在使用拆分隧道模型的 Teams 中进行呼叫流操作，以及如何保护连接。

### <a name="configuration"></a>配置

对于通话和会议，只要所需的针对 Teams 媒体的优化 IP 子网在路由表中，那么当 Teams 调用 _GetBestRoute_ 方法来确定应将哪个接口用于特定目标时，将为上面列出的 Microsoft IP 块中的 Microsoft 目标返回本地接口。

某些 VPN 客户端软件允许基于 URL 进行路由操作。 但是，Teams 媒体流量没有与之关联的 URL，因此必须使用 IP 子网来控制此流量路由。

在某些情况下（通常与 Teams 客户端配置无关），即使有正确的路由，媒体流量仍会遍历 VPN 隧道。 如果遇到这种情况，只需使用防火墙规则来阻止 Teams IP 子网或端口使用 VPN。

>[!IMPORTANT]
>为了确保在所有 VPN 方案中通过所需的方法路由团队媒体流量，请确保用户运行的是 Microsoft 团队客户端版本**1.3.00.13565**或更高版本。 此版本包括客户端检测可用网络路径的方式方面的改进。

信号流量通过 HTTPS 执行，而不是作为媒体流量敏感的延迟，在 URL/ip 数据中标记为 "**允许**"，因此可以在需要时通过 VPN 客户端进行安全路由。

### <a name="security"></a>安全性

避免拆分隧道的一个常见理由是这样做不太安全，也就是说， 任何不通过 VPN 隧道的流量都将无法从应用到 VPN 隧道的任何加密方案中受益，因此安全性较低。

对此的主要反对意见是，媒体流量已经通过_安全实时传输协议 (SRTP)_ 进行了加密，该协议是实时传输协议 (RTP) 的一个配置文件，它为 RTP 流量提供保密性、身份验证和重播攻击保护。 SRTP 本身依赖于随机生成的会话密钥，该密钥通过 TLS 安全信令通道进行交换。 [本安全指南](https://docs.microsoft.com/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online)中详细介绍了这一点，但主要部分是媒体加密。

媒体流量是使用 SRTP 加密的，SRTP 使用安全随机数生成器生成的会话密钥，并使用信令 TLS 通道进行交换。 此外，在中介服务器和其内部下一个跃点之间的双向媒体也使用 SRTP 进行加密。

Skype for Business Online 生成用户名/密码，可用于通过_围绕 NAT 使用中继遍历 (TURN)_ 来安全访问媒体中继。 媒体中继通过 TLS 安全 SIP 信道交换用户名/密码。 值得注意的是，即使可使用 VPN 隧道将客户端连接到公司网络，但当流量离开公司网络以访问服务时，仍需以其 SRTP 形式流动。

有关 Teams 如何减少常见安全问题（如语音或 _NAT 的会话遍历实用工具 (STUN)_ 放大攻击）的信息，可[参阅本文](https://docs.microsoft.com/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c)。

还可以阅读有关远程工作场景中的新式安全控制：[安全专业人员和 IT 人员在当前独特的远程工作场景中实现新式安全控制的替代方法（Microsoft 安全团队博客）](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

## <a name="testing"></a>测试

策略准备就绪后，应确认其是否按预期工作。 可通过多种方法来测试路径是否已正确设置为使用本地 Internet 连接：

- 运行[Microsoft 365 连接测试](https://aka.ms/netonboard)，该测试将为您运行连接测试，包括如上所示的跟踪路由。 此外，还应将 VPN 测试中的添加到此工具，此外还应提供其他见解。

- 对于拆分隧道范围内的终结点的简单 tracert，应显示所采用的路径，例如：

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  然后，您应该看到通过本地 ISP 向此终结点提供的路径，该终结点应解析为我们为拆分隧道配置的团队范围内的 IP。

- 以使用 Wireshark 之类的工具进行网络捕获为例。 在呼叫期间筛选 UDP，应看到流量流向 Teams **优化**范围中的 IP。 如果 VPN 隧道正用于此流量，则跟踪中将不会显示媒体流量。

### <a name="additional-support-logs"></a>其他支持日志

如果需要更多数据来排除故障，或正在请求 Microsoft 支持部门的协助，获取以下信息可帮助你加快查找解决方案。 Microsoft 支持的**TSS 基于 WINDOWS CMD 的通用故障排除脚本工具集**可帮助您以简单的方式收集相关日志。 可在以下网址找到所使用的工具和说明：<https://aka.ms/TssTools.>

## <a name="howto-guides-for-common-vpn-platforms"></a>适用于常见 VPN 平台的操作指南

本节提供了一些链接，这些链接提供了实现 Office 365 流量（来自该领域中最常见的合作伙伴）的拆分隧道的详细指南。 我们将在其他指南推出时添加这些指南。

- **Windows 10 VPN 客户端**：[使用本机 Windows 10 VPN 客户端优化面向远程工作者的 Office 365 流量](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco Anyconnect**：[优化 Office365 的 Anyconnect 拆分隧道](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect**：[通过 VPN 拆分隧道排除访问路由优化 Office 365 流量](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**：[使用 BIG-IP APM 通过 VPN 优化远程访问 Office 365 流量](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Citrix 网关**：[优化 Office365 Citrix 网关 VPN 拆分隧道](https://docs.citrix.com/en-us/citrix-gateway/13/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**：[VPN 隧道：如何配置拆分隧道以排除 Office365 应用程序](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **检查点 VPN**：[如何为 Office 365 和其他 SaaS 应用程序配置拆分隧道](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="faq"></a>常见问题

Microsoft 安全团队已发布概括了安全专家的主要方式的[文章](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)，以及在当今独特的远程工作方案中，可以实现新式安全控制。 此外，下面是有关此主题的一些常见客户问题和解答。

### <a name="how-do-i-stop-users-accessing-other-tenants-i-do-not-trust-where-they-could-exfiltrate-data"></a>我如何阻止用户访问我不信任的其他租户（他们可能会泄漏数据）？

答案是[称为租户限制的功能](https://docs.microsoft.com/azure/active-directory/manage-apps/tenant-restrictions)。 身份验证流量不大，对延迟也不是特别敏感，因此可通过 VPN 解决方案发送到应用此功能的本地代理。 在此处维护受信任租户的允许列表，如果客户端尝试获取不受信任的租户的令牌，代理将只拒绝该请求。 如果租户受信任，则在用户具有正确的凭据和权限的情况下，令牌可供访问。

因此，即使用户可以通过 TCP/UDP 连接到上述标记为“优化”的终结点，但若没有有效的令牌来访问所涉及的租户，他们也无法登录和访问/移动任何数据。

### <a name="does-this-model-allow-access-to-consumer-services-such-as-personal-onedrive-accounts"></a>此模型是否允许访问诸如个人 OneDrive 帐户之类的使用者服务？

否，Office 365 终结点不同于使用者服务（以 Onedrive.live.com 为例），因此拆分隧道将不允许用户直接访问使用者服务。 流向使用方终结点的流量将继续使用 VPN 隧道，并且现有策略将继续生效。

### <a name="how-do-i-apply-dlp-and-protect-my-sensitive-data-when-the-traffic-no-longer-flows-through-my-on-premises-solution"></a>如果流量不再流经本地解决方案，我该如何应用 DLP 并保护我的敏感数据？

为帮助防止意外泄露敏感信息，Office 365 提供了一组丰富的[内置工具](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies?view=o365-worldwide)。 可使用 Teams 和 SharePoint 的内置 [DLP 功能](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies?view=o365-worldwide)来检测未恰当存储或共享的敏感信息。 如果远程工作策略的一部分涉及到自己的设备（BYOD）策略，则可以使用[基于应用的条件访问](https://docs.microsoft.com/azure/active-directory/conditional-access/app-based-conditional-access)来防止将敏感数据下载到用户的个人设备

### <a name="how-do-i-evaluate-and-maintain-control-of-the-users-authentication-when-they-are-connecting-directly"></a>如何在用户直接连接时评估和保留用户身份验证的控制权？

除了问题 1 中提到的租户限制功能之外，还可以应用[条件访问策略](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)来动态评估身份验证请求的风险并做出相应的反应。 Microsoft 建议在一段时间内实现[零信任模型](https://www.microsoft.com/security/zero-trust?rtc=1)，我们可以使用 Azure AD 条件访问策略在移动和以云为中心的世界保持控制。 可使用条件访问策略对身份验证请求是否成功作出实时决策，具体取决于以下诸多因素：

- 设备，设备是否已知/受信任/已加入域？
- IP – 身份验证请求是否来自已知公司 IP 地址？ 或者来自不信任的国家/地区？
- 应用程序 – 用户是否有权使用此应用程序？

然后，我们可以根据这些策略触发批准、触发 MFA 或阻止身份验证等策略。

### <a name="how-do-i-protect-against-viruses-and-malware"></a>如何防范病毒和恶意软件？

同样，Office 365 为服务自身各层中标记为“优化”的终结点提供了保护，[本文档对此进行了概述](https://docs.microsoft.com/office365/Enterprise/office-365-malware-and-ransomware-protection)。 正如前面所述，在服务中提供这些安全元素的效率要高得多，而不是使用可能不完全理解协议/流量的设备来尝试并进行此操作。默认情况下，SharePoint Online 自动扫描已知恶意软件的[文件上载](https://docs.microsoft.com/microsoft-365/security/office-365-security/virus-detection-in-spo?view=o365-worldwide)

对于上面列出的 Exchange 终结点，[Exchange Online Protection](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) 和 [Office 365 高级威胁防护](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)在为访问服务的流量提供安全方面做得很好。

### <a name="can-i-send-more-than-just-the-optimize-traffic-direct"></a>除了优化流量外，我是否可以直接发送更多流量？

应优先考虑标记为**优化**的终结点，因为这些终结点将为低级别的工作提供最大好处。 但是，如果需要，允许服务使用已标记的终结点，并为可在需要时使用的终结点提供 IPs。

此外，还有许多供应商提供了称为安全 web 网关的基于云的代理/安全解决方案，这些解决方案为常规 web 浏览提供了中心安全、控制和公司策略应用程序。 如果从基于云的位置向用户提供安全的 Internet 访问权限，则这些解决方案在云第一世界中可以很好地运行。 这将消除通过 VPN/公司网络执行回流以便正常浏览流量的需要，同时仍允许中央安全控制。

然而，即使就地使用这些解决方案，Microsoft 仍强烈建议将标记为“优化”的 Office 365 流量直接发送到服务。

有关允许直接访问 Azure 虚拟网络的指南，请参阅[使用 Azure VPN 网关点到站点进行远程工作](https://docs.microsoft.com/azure/vpn-gateway/work-remotely-support)一文。

### <a name="why-is-port-80-required-is-traffic-sent-in-the-clear"></a>为什么需要端口 80？ 流量是否明文发送？

端口 80 仅用于重定向到端口 443 会话之类的操作，不会通过端口 80 发送或访问任何客户数据。 [此文](https://docs.microsoft.com/microsoft-365/compliance/encryption?view=o365-worldwide)概述了 Office 365 中传输和静止数据的加密，[这篇文章](https://docs.microsoft.com/microsoftteams/microsoft-teams-online-call-flows#types-of-traffic)则概述了如何使用 SRTP 来保护 Teams 媒体流量。

### <a name="does-this-advice-apply-to-users-in-china-using-a-worldwide-instance-of-office-365"></a>此建议是否适用于使用 Office 365 全球实例的中国用户？

**否**，不适用。 在上述建议中，要注意连接到 Office 365 全球实例的中国用户。 由于该区域会经常出现跨境网络拥挤现象，因此直接 Internet 出口性能可能会有变化。 该区域中的大多数客户都使用 VPN 将流量引入公司网络，并利用其经授权的 MPLS 专线或类似于通过优化路径的国家/地区之外的出口。 [面向中国用户的 Office 365 性能优化](office-365-networking-china.md)一文对此进行了进一步的概述。

## <a name="related-topics"></a>相关主题

[概述：Office 365 的 VPN 拆分隧道](office-365-vpn-split-tunnel.md)

[面向中国用户的 Office 365 性能优化](office-365-networking-china.md)

[安全专业人员和 IT 人员在当前独特的远程工作场景中实现新式安全控制的替代方法（Microsoft 安全团队博客）](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[增强 Microsoft 的 VPN 性能：使用 Windows 10 VPN 配置文件以允许自动打开连接](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[运行 VPN：Microsoft 如何让远程工作人员互联](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Office 365 网络连接原则](office-365-network-connectivity-principles.md)

[评估 Office 365 网络连接](assessing-network-connectivity.md)

[Office 365 网络和性能优化](network-planning-and-performance.md)
