---
title: 管理 Office 365 终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/21/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 一些企业网络限制对通用 internet 位置的访问，或者包括大量 backhaul 或网络流量的处理。 为了确保这些网络上的计算机可以访问 Office 365，网络和代理管理员需要管理组成 Office 365 终结点列表的 Fqdn、Url 和 IP 地址的列表。 需要将它们添加到直接路由、代理旁路、和/或防火墙规则和 PAC 文件中，以确保网络请求能够到达 Office 365。
ms.openlocfilehash: fb0f6640ee9de07bb92b9093a94bb7e4fd111a54
ms.sourcegitcommit: e70808dccc1622d18b1cc5e1e4babd4238112838
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "40744506"
---
# <a name="managing-office-365-endpoints"></a>管理 Office 365 终结点

如果大多数企业组织具有多个办事处位置和一个连接 WAN，则需要为 Office 365 网络连接配置配置。 您可以通过防火墙直接发送所有受信任的 Office 365 网络请求，从而绕过所有其他数据包级别检查或处理，从而优化您的网络。 这可降低延迟和外围容量要求。 确定 Office 365 网络流量是为用户提供最佳性能的第一步。 有关 Office 365 网络连接的详细信息，请参阅[office 365 网络连接原则](office-365-network-connectivity-principles.md)。

Microsoft 建议使用[office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)访问 office 365 网络终结点，并对其进行更改。

无论您管理重要的 Office 365 网络通信的方式如何，Office 365 都需要 Internet 连接。 在[不包括在 Office 365 IP 地址和 URL Web 服务中的其他终结点](additional-office365-ip-addresses-and-urls.md)处列出了需要连接的其他网络终结点。

使用 Office 365 网络终结点的方式取决于企业组织网络的体系结构。 本文概述了企业网络体系结构可以与 Office 365 IP 地址和 Url 集成的几种方法。 选择要信任的网络请求的最简单方法是，在每个办公室位置使用支持自动 Office 365 配置的 SDWAN 设备。

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN 用于本地分支出口重要的 Office 365 网络流量

在每个分支办公室位置，您可以提供一个 SDWAN 设备，该设备配置为将 Office 365 的流量配置为将终结点的类别优化、优化并允许类别直接发送到 Microsoft 的网络。 其他网络流量包括本地数据中心流量、常规 Internet 网站流量和到 Office 365 的流量。默认类别终结点将发送到具有更大网络外围的其他位置。

Microsoft 正在与 SDWAN 提供商合作，以启用自动配置。 有关详细信息，请参阅[Office 365 网络合作伙伴计划](office-365-networking-partner-program.md)。

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>使用 PAC 文件进行重要的 Office 365 通信的直接路由

使用 PAC 或 WPAD 文件管理与 Office 365 关联但没有 IP 地址的网络请求。 通过代理或外围设备发送的典型网络请求会增加延迟。 虽然 SSL 中断和检查会造成最大延迟，但其他服务（如代理身份验证和信誉查找）可能会导致性能下降和用户体验不良。 此外，这些外围网络设备需要足够的容量来处理所有的网络连接请求。 我们建议绕过您的代理或检查设备进行直接的 Office 365 网络请求。
  
[Powershell 库 PacFile](https://www.powershellgallery.com/packages/Get-PacFile)是一个 PowerShell 脚本，可从 OFFICE 365 IP 地址和 URL Web 服务读取最新的网络终结点，并创建示例 PAC 文件。 您可以修改脚本，使其与现有 PAC 文件管理集成。

![通过防火墙和代理连接到 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**图 1-简单的企业网络外围环境**

PAC 文件部署到图1中的点1的 web 浏览器。 将 PAC 文件用于直接传出重要的 Office 365 网络通信时，还需要允许连接到网络外围防火墙上这些 Url 后面的 IP 地址。 为此，可通过获取 PAC 文件中指定的相同 Office 365 终结点类别的 IP 地址，并根据这些地址创建防火墙 Acl 来实现。 防火墙是图1中的点3。

另外，如果选择仅对优化类别终结点执行直接路由，则发送到代理服务器的任何必需的允许类别终结点都需要在代理服务器中列出，以绕过进一步处理。 例如，SSL 中断和检查和代理身份验证与 "优化" 和 "允许" 类别终结点不兼容。 代理服务器是图1中的第2点。

通用配置是允许，而无需处理来自代理服务器的所有出站通信，以获取命中代理服务器的 Office 365 网络流量的目标 IP 地址。 有关与 SSL 中断和检查有关的问题的信息，请参阅[使用第三方网络设备或解决方案在 Office 365 流量](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)中。

PacFile 脚本将生成两种类型的 PAC 文件。

|**类型**|**说明**|
|:-----|:-----|
|**1** <br/> |Send 将终结点流量直接和其他所有内容一起优化到代理服务器。 <br/> |
|**双面** <br/> |发送优化并允许将终结点通信直接和其他所有内容发送到代理服务器。 此类型还可用于将所有受支持的 ExpressRoute 的 Office 365 流量发送到 ExpressRoute 网段，并将其他所有内容发送到代理服务器。 <br/> |

下面是调用 PowerShell 脚本的一个简单示例：

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

您可以传递给脚本的参数有很多：

|**参数**|**说明**|
|:-----|:-----|
|**ClientRequestId** <br/> |这是必需的，它是传递给 web 服务的 GUID，表示进行呼叫的客户端计算机。 <br/> |
|**实例** <br/> |默认为 "全球" 的 Office 365 服务实例。 也传递到 web 服务。 <br/> |
|**TenantName** <br/> |Office 365 租户名称。 传递到 web 服务，并在某些 Office 365 Url 中用作可替换参数。 <br/> |
|**类型** <br/> |要生成的代理 PAC 文件的类型。 <br/> |

以下是使用其他参数调用 PowerShell 脚本的另一个示例：

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Office 365 网络流量的代理服务器绕过处理

如果 PAC 文件不用于直接出站通信，您仍希望通过配置代理服务器绕过网络外围处理。 一些代理服务器供应商已启用自动配置，如[Office 365 网络合作伙伴计划](office-365-networking-partner-program.md)中所述。

如果您手动执行此操作，则需要从 Office 365 IP 地址和 URL Web 服务中获取 "优化" 和 "允许" 终结点类别数据，并将代理服务器配置为绕过对这些数据的处理。 一定要避免 "优化" 和 "允许" 类别终结点的 SSL 中断和检查和代理身份验证。
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Office 365 IP 地址和 Url 的更改管理

除了为网络外围选择适当的配置之外，对于 Office 365 终结点采用更改管理过程也非常关键。 这些终结点定期发生更改，如果不管理更改，则在添加新的 IP 地址或 URL 后，最终用户可能会受到阻止或性能较差。

对 Office 365 IP 地址和 Url 的更改通常在每个月的最后一天发布。 有时，由于操作、支持或安全要求，将在该计划之外发布更改。

如果发布的更改需要你执行操作，因为添加了 IP 地址或 URL，则应预计在发布更改时收到30天通知，直到该终结点上有 Office 365 服务。 尽管我们将此通知时段作为目标，但由于运营、支持或安全要求，可能并不总是可能。 不需要立即操作来维护连接的更改（如删除的 IP 地址或 Url 或不太重要的更改）不包括提前通知。 无论提供什么通知，我们都会列出每次更改的预期服务活动日期。

### <a name="change-notification-using-the-web-service"></a>使用 Web 服务更改通知

您可以使用 Office 365 IP 地址和 URL Web 服务获取更改通知。 我们建议您每小时调用 **/version** web 方法，以检查用于连接到 Office 365 的终结点的版本。 如果与您使用的版本相比，此版本发生了更改，则应从 **/endpoints** web 方法获取最新的终结点数据，并根据需要从 **/changes** web 方法中获取差异。 如果您找到的版本没有任何更改，则无需调用 **/endpoints**或 **/changes** web 方法。

有关详细信息，请参阅[Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)。

### <a name="change-notification-using-rss-feeds"></a>使用 RSS 源更改通知

Office 365 IP 地址和 URL Web 服务提供了可在 Outlook 中订阅的 RSS 源。 有关 IP 地址和 Url 的每个 Office 365 服务实例特定页面上的 RSS Url 的链接。 有关详细信息，请参阅[Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)。

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>使用 Microsoft 流更改通知和审批审阅

我们了解您可能仍需要手动处理每个月对网络终结点所做的更改。 您可以使用 Microsoft 流创建通过电子邮件通知您的流，也可以选择在 Office 365 网络终结点发生更改时对更改运行审批过程。 完成审阅后，可以让流自动将更改通过电子邮件发送到您的防火墙和代理服务器管理团队。

有关 Microsoft 流示例和模板的信息，请参阅[使用 Microsoft Flow 接收有关 Office 365 IP 地址和 url 的更改的电子邮件](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)。
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 网络终结点常见问题解答

有关 Office 365 连接的常见问题的管理员问题：
  
### <a name="how-do-i-submit-a-question"></a>如何提交问题？

单击底部的链接，以指示该文章是否有帮助，并提交任何其他问题。 我们将通过最常问的方式监视反馈并更新此处的问题。
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>如何确定租户的位置？

 **租户位置**最好是使用我们的[数据中心地图](https://aka.ms/datamaps)来确定的。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>我是否与 Microsoft 进行了适当的沟通？

 对**等位置**有更详细的介绍[与 Microsoft 的对等](https://www.microsoft.com/peering)。
  
在全球范围内有超过2500个 ISP 对等关系和70点，从你的网络转到我们的状态应是无缝的。 如果花几分钟时间来确保你的 ISP 的对等关系最具最佳，[下面将](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)为我们的网络提供良好而不好的对等操作的几个示例。
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>我看到 "已发布" 列表中没有对 IP 地址的网络请求，是否需要提供对它们的访问权限？

我们只提供了应直接路由到的 Office 365 服务器的 IP 地址。 这不是你将看到的网络请求的所有 IP 地址的完整列表。 你将看到对 Microsoft 和第三方拥有的、未发布的 IP 地址的网络请求。 这些 IP 地址以动态方式生成或管理，以在发生更改时阻止及时通知。 如果你的防火墙无法根据这些网络请求的 Fqdn 允许访问，请使用 PAC 或 WPAD 文件管理请求。
  
若要了解有关详细信息，请参阅与 Office 365 关联的 IP。
  
1. 检查 IP 地址是否包含在使用 CIDR 计算器的较大的已发布区域中，例如，对于[IPv4](https://www.ipaddressguide.com/cidr)或 [IPv6]https://www.ipaddressguide.com/ipv6-cidr)。
2. 查看合作伙伴是否拥有[whois 查询](https://dnsquery.org/)的 IP。 如果是 Microsoft 所拥有的，则它可能是内部合作伙伴。
3. 检查证书在浏览器中使用*HTTPS://\<IP_ADDRESS\> *连接到 IP 地址，检查证书上列出的域以了解与 IP 地址关联的域。 如果它是 Microsoft 拥有的 IP 地址，而不是 Office 365 IP 地址列表，则该 IP 地址可能与 Microsoft CDN （如*MSOCDN.NET*或另一个 microsoft 域）相关联，而不会发布 IP 信息。 如果您在证书中找到的域是我们声明列出 IP 地址的域，请告诉我们。

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>某些 Office 365 Url 指向 CNAME 记录，而不是 DNS 中的记录。 如何处理 CNAME 记录？

客户端计算机需要 DNS A 或 AAAA 记录，其中包含一个或多个连接到云服务的 IP 地址。 Office 365 中包含的某些 Url 显示 CNAME 记录，而不是 A 或 AAAA 记录。 这些 CNAME 记录是中间的，并且可能会有多个链。 它们将始终解析为 IP 地址的 A 或 AAAA 记录。 例如，请考虑以下系列的 DNS 记录，这些记录最终解析为 IP 地址_IP_1_：

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

这些 CNAME 重定向是 DNS 的正常部分，对客户端计算机是透明的，并且对代理服务器是透明的。 它们用于负载平衡、内容传递网络、高可用性和服务事件缓解。 Microsoft 不会发布中间 CNAME 记录，它们可能会随时更改，并且您无需在代理服务器中将其配置为允许。

代理服务器验证上述示例中的初始 URL 是否为 serviceA.office.com，并且此 URL 将包含在 Office 365 发布中。 代理服务器请求将该 URL 的 DNS 解析为 IP 地址，并将收到返回 IP_1。 它不验证中间 CNAME 重定向记录。

不建议使用基于间接 Office 365 Fqdn 的硬编码配置或白名单，不受 Microsoft 支持，并且已知会导致客户连接问题。 在启用了 DNS 递归的情况下，可以通过 DNS 条件转发（作用域为直接使用的 Office 365 Fqdn）来解决在 CNAME 重定向上阻止的 DNS 解决方案或以其他方式解析 Office 365 DNS 条目的错误。 许多第三方网络外围产品在其配置中使用[office 365 IP 地址和 URL Web 服务](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)，以本机方式集成建议的 Office 365 终结点白名单。

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>为什么在 Microsoft 域名中看到名称，如 nsatc.net 或 akadns.net？

Office 365 和其他 Microsoft 服务使用几种第三方服务（如 Akamai 和 MarkMonitor）来改进 Office 365 体验。 为了让你能够获得最佳体验，我们可能会在将来更改这些服务。 第三方域可以承载内容（如 CDN），也可以托管服务，例如地理流量管理服务。 当前使用的某些服务包括：
  
当您看到包含* \*. nsatc.net*的请求时， [MarkMonitor](https://www.markmonitor.com/)正在使用中。 此服务提供了域名称保护和监控，以防止恶意行为。
  
当您看到* \*exacttarget.com*的请求时， [ExactTarget](https://www.marketingcloud.com/)正在使用中。 此服务提供电子邮件链接管理，并针对恶意行为进行监控。
  
当您看到包含下列 Fqdn 之一的请求时，将使用[Akamai](https://www.akamai.com/) 。 此服务提供地理位置 DNS 和内容传递网络服务。
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

<a name="bkmk_thirdparty"> </a>
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>我必须具有 Office 365 的最小连接能力

由于 Office 365 是一套在 internet 上运行的服务，因此可靠性和可用性承诺基于许多可用的标准 internet 服务。 例如，诸如 DNS、CRL 和 Cdn 等标准 internet 服务必须能够使用 Office 365，就像它们必须可访问的那样，才能使用最新式的 internet 服务。

Office 365 套件分为主要的服务领域。 可以有选择地为连接启用这些功能，并且有一个公共区域，它们是所有的依赖项，并且始终是必需的。

|**服务区域**|**说明**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online 和 Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online 和 OneDrive for Business <br/> |
|**Skype for Business Online 和 Microsoft Teams** <br/> |Skype for Business 和 Microsoft 团队 <br/> |
|**常见** <br/> |Office 365 Pro Plus、Office in 浏览器、Azure AD 和其他常见网络终结点 <br/> |

除了基本 internet 服务之外，还提供了仅用于集成功能的第三方服务。 虽然这些功能是集成所必需的，但它们在 Office 365 终结点文章中被标记为可选，这意味着当终结点不可访问时，服务的核心功能将继续正常运行。 所需的任何网络终结点都将具有所需的属性设置为 true。 任何可选的网络终结点都将把必需的属性设置为 false，notes 属性将详细介绍在连接被阻止时应会出现的缺少的功能。
  
如果您尝试使用 Office 365，并且查找第三方服务无法访问，则需要[确保通过代理和防火墙允许在本文中标记为 "必需" 或 "可选" 的所有 fqdn](urls-and-ip-address-ranges.md)。
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>如何阻止对 Microsoft 的使用者服务的访问？

限制对我们的使用者服务的访问权限应由您自己承担。 阻止使用者服务的唯一可靠方法是限制对*Login.live.com* FQDN 的访问。 此 FQDN 由广泛的一组服务使用，包括非消费者服务（如 MSDN、TechNet 和其他服务）。 此 FQDN 也由 Microsoft 支持的安全文件交换程序使用，并且必须转移文件以促进 Microsoft 产品的故障排除。  限制对此 FQDN 的访问可能会导致需要为与这些服务关联的网络请求包含规则例外。
  
请记住，仅阻止对 Microsoft 消费者服务的访问不会阻止网络中的用户使用 Office 365 租户或其他服务 exfiltrate 信息。
  
## <a name="related-topics"></a>相关主题

[Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)

[Microsoft Azure 数据中心 IP 范围](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公共 IP 空间](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune 的网络基础结构要求](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute 和 Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL 和 IP 地址范围](urls-and-ip-address-ranges.md)
  
[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)
  
[Office 365 网络连接原则](office-365-network-connectivity-principles.md)
