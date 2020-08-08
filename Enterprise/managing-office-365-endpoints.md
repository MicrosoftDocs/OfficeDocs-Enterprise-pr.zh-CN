---
title: 管理 Office 365 终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 1/24/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 一些企业网络限制对通用 Internet 位置的访问，或者包括大量的回程或网络流量处理。 为确保此类网络上的计算机能够访问 Office 365，网络和代理管理员需要管理 FQDN、URL、和 IP 地址列表（它们共同构成 Office 365 终结点列表）。 需要将它们添加到直接路由、代理旁路和/或防火墙规则和 PAC 文件，以确保网络请求能够访问 Office 365。
ms.openlocfilehash: 35f07538bd55386dc245286822eab9e14e70a3cf
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592156"
---
# <a name="managing-office-365-endpoints"></a>管理 Office 365 终结点

具有多个办公室位置和连接的 WAN 的大多数企业组织将需要配置 Office 365 网络连接。 绕过所有其他包级别检查或处理过程，直接通过防火墙发送所有 Office 365 可信网络请求可优化网络。 这样可减少延迟和外围容量要求。 识别 Office 365 网络流量是为用户提供最佳性能的第一步。 有关 Office 365 网络连接的详细信息，请参阅 [Office 365 网络连接原则](office-365-network-connectivity-principles.md)。

Microsoft 建议使用 [Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)访问 Office 365 网络终结点，并对其进行更改。

无论如何管理重要的 Office 365 网络流量，Office 365 都需要 Internet 连接。 [Office 365 IP 地址和 URL Web 服务中未包括的其他终结点](additional-office365-ip-addresses-and-urls.md)列出了需要连接的其他网络终结点。

如何使用 Office 365 网络终结点将取决于你的企业组织网络体系结构。 本文概述了企业网络体系结构可以与 Office 365 IP 地址和 URL 集成的几种方式。 选择要信任的网络请求的最简单方法是，在每个办公室位置使用支持自动 Office 365 配置的 SDWAN 设备。

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>用于重要 Office 365 网络流量的本地分支出口的 SDWAN

在每个分支机构位置，你都可以提供一个 SDWAN 设备，该设备配置为将 Office 365“优化”类别或“优化和允许”类别终结点的流量直接路由到 Microsoft 的网络。 其他网络流量（包括本地数据中心流量、常规 Internet 网站流量以及到 Office 365 默认类别终结点的流量）将发送到你具有更大网络外围的位置。

Microsoft 正在与 SD WAN 提供商合作以启用自动配置。 有关详细信息，请参阅 [Office 365 网络合作伙伴计划](office-365-networking-partner-program.md)。

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>使用 PAC 文件直接路由重要的 Office 365 流量

使用 PAC 或 WPAD 文件管理与 Office 365 关联但没有 IP 地址的网络请求。 通过代理或外围设备发送的网络请求通常会增加延迟。 虽然 SSL 中断和检查会带来最大的延迟，但是其他服务（例如代理身份验证和信誉查找）可能会导致性能下降和用户体验不佳。 此外，这些外围网络设备需要有足够的容量，才能处理所有网络连接请求。 建议绕过代理或检查设备直接发送 Office 365 网络请求。
  
[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) 是 PowerShell 脚本，它从 Office 365 IP 地址和 URL Web 服务读取最新网络终结点，并创建示例 PAC 文件。 可以修改脚本，使其与现有的 PAC 文件管理集成。

![通过防火墙和代理连接到 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**图 1 - 简单的企业网络外围**

该 PAC 文件部署到了图 1 中点 1 处的 Web 浏览器。 当使用 PAC 文件直接发送重要的 Office 365 网络流量时，还需要允许连接到网络外围防火墙上这些 URL 后面的 IP 地址。 通过获取 PAC 文件中指定的相同 Office 365 终结点类别的 IP 地址，并基于这些地址创建防火墙 ACL 来完成此操作。 防火墙是图 1 中的点 3。

另外，如果你选择仅对“优化”类别的终结点直接路由，则需要在代理服务器中列出你发送到代理服务器的所有必需的“允许”类别终结点，以绕过进一步处理。 例如，SSL 中断和检查以及代理身份验证与“优化和允许“类别终结点不兼容。 代理服务器是图 1 中的点 2。

常见配置是允许，而无需针对到达代理服务器的 Office 365 网络流量的目标 IP 地址处理来自代理服务器的所有出站流量。 有关 SSL 中断和检查的问题的详细信息，请参阅[使用有关 Office 365 流量的第三方网络设备或解决方案](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)。

PAC 文件脚本会生成两种类型的 PAC 文件。

| 类型 | 描述 |
|:-----|:-----|
|**1** <br/> |直接将“优化”终结点流量和其他流量发送到代理服务器。 <br/> |
|**2** <br/> |直接将“优化和允许”终结点流量和其他流量发送到代理服务器。 此类型还可以用于所有受支持的适用于 Office 365 的 ExpressRoute 流量发送到 ExpressRoute 网段，并将其他所有流量发送到代理服务器。 <br/> |

下面是调用 PowerShell 脚本的一个简单示例：

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

可向脚本传递许多参数：

| 参数 | 描述 |
|:-----|:-----|
|**ClientRequestId** <br/> |这是必需的，并且是传递给 Web 服务的 GUID，它代表进行呼叫的客户端计算机。 <br/> |
|**实例** <br/> |Office 365 服务实例，默认为“全球”。 也会传递到 Web 服务。 <br/> |
|**TenantName** <br/> |你的 Office 365 租户名称。 传递到 Web 服务并用作某些 Office 365 URL 中的可替换参数。 <br/> |
|**类型** <br/> |要生成的代理 PAC 文件的类型。 <br/> |

这是使用附加参数调用 PowerShell 脚本的另一个示例：

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>代理服务器绕过 Office 365 网络流量的处理

在 PAC 文件不用于直接出站通信的情况下，你仍然希望通过配置代理服务器来绕过网络外围上的处理。 如 [Office 365 网络合作伙伴计划](office-365-networking-partner-program.md)中所述，某些代理服务器供应商已启用此功能的自动配置。

如果手动执行此操作，则需要从 Office 365 IP 地址和 URL Web 服务获取“优化和允许”终结点类别的数据，并将你的代理服务器配置为绕过这些处理。 对于“优化和允许”类别的终结点，避免 SSL 中断以及检查和代理身份验证很重要。
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Office 365 IP 地址和 URL 的变更管理

除了为网络外围选择适当的配置外，对 Office 365 终结点采用变更管理流程也很重要。 这些终结点会定期更改，如果你不管理变更，则在添加新的 IP 地址或 URL 后，最终用户可能会被阻止或性能不佳。

对 Office 365 IP 地址和 URL 的更改通常在每个月最后一天前后发布。 有时，由于运营、支持或安全要求，可能会在时间表之外发布更改。

如果发布的更改由于添加了 IP 地址或 URL 而要求你采取行动，你将在我们发布更改之日起 30 天内收到通知，直到该终结点上有 Office 365 服务。 尽管我们的目标是实现此通知期，但由于操作、支持或安全性要求，可能并非总是如此。 不需要立即采取措施来保持连接性的更改（例如，删除的 IP 地址或 URL 或不太重要的更改）不包括提前通知。 无论提供什么通知，我们都会列出每次更改的预期服务启用日期。

### <a name="change-notification-using-the-web-service"></a>使用 Web 服务的更改通知

可使用 Office 365 IP 地址和 URL Web 服务获取更改通知。 我们建议你每小时调用一次 **/version ** Web 方法，以查看用于连接到 Office 365 的终结点的版本。 如果与使用的版本相比，该版本发生了变化，则应该从 **/endpoints** Web 方法获取最新的终结点数据，并可以选择从 **/changes** Web 方法获取差异。 如果找到的版本没有任何更改，则不必调用 **/endpoints** 或 **/changes** Web 方法。

有关详细信息，请参阅 [Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)。

### <a name="change-notification-using-rss-feeds"></a>使用 RSS 源的更改通知

Office 365 IP 地址和 URL Web 服务提供了一个 RSS 源，你可以在 Outlook 中进行订阅。 IP 地址和 URL 的每个特定于 Office 365 实例的页面上都有指向 RSS URL 的链接。 有关详细信息，请参阅 [Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)。

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>使用 Microsoft Flow 的更改通知和审批审查

我们理解，你可能仍需要手动处理每个月进行的网络终结点更改。 可以使用 Microsoft Flow 创建一个流程，该流程将通过电子邮件向你发送通知，并可以选择在 Office 365 网络终结点发生更改时为更改运行审批流程。 审核完成后，可以通过流程自动将更改通过电子邮件发送给防火墙和代理服务器管理团队。

有关 Microsoft Flow 示例和模板的信息，请参阅[使用 Microsoft Flow 接收关于 Office 365 IP 地址和 URL 的更改的电子邮件](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)。
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 网络终结点常见问题

管理员常问到的有关 Office 365 连接性的问题：
  
### <a name="how-do-i-submit-a-question"></a>如何提交问题？

请单击底部的链接，指出文章是否有帮助，也可以提交任何其他问题。 我们会检查反馈，并更新最常见的问题。
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>如何确定租户的位置？

 使用[数据中心地图](https://aka.ms/datamaps)是确定**租户位置**的最佳方式。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>我与 Microsoft 间的对等互连是否正确？

 在[与 Microsoft 对等互连](https://www.microsoft.com/peering)中详细描述了**对等位置**。
  
我们在全球拥有 2500 多个 ISP 对等关系和 70 个接入点，因此你的网络可无缝连接到我们的网络。 花几分钟时间确保你的 ISP 对等关系为最佳对等关系，这不会有什么坏处，[此处的几个示例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)展示了对等转接我们的网络时较顺利的情况和不太顺利的情况。
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>我发现发布列表中没有列出对 IP 地址的网络请求，我是否需要提供访问它们的权限？

我们只提供直接路由到 Office 365 服务器的 IP 地址。 这不是所有会出现网络请求的 IP 地址的完整列表。 你将看到发送给 Microsoft 和第三方自有的未发布 IP 地址的网络请求。 这些 IP 地址是动态生成的或管理的，发生更改时不会及时通知。 如果防火墙不允许基于 FQDN 访问这些网络请求，请使用 PAC 或 WPAD 文件来管理请求。
  
需要了解与 Office 365 关联的 IP 的详细信息？
  
1. 使用 CIDR 计算器检查该 IP 地址是否包含在较大的已发布范围内，如 [IPv4](https://www.ipaddressguide.com/cidr) 或 [IPv6](https://www.ipaddressguide.com/ipv6-cidr) 的 IP 地址。 例如，40.96.0.0/13 包括 IP 地址40.103.0.1，尽管40.96 与 40.103 不匹配。
2. 查看合作伙伴是否拥有含 [whois 查询](https://dnsquery.org/)的 IP。 如果该 IP 为 Microsoft 所有，则它可能是内部合作伙伴。 许多伙伴网络终结点被列为属于_默认_类别，其 IP 地址未发布。
3. 该 IP 地址可能不是 Office 365 的一部分或与其无从属关系。 Office 365 网络终结点发布不包括所有 Microsoft 网络终结点。
4. 查看证书，在浏览器中使用 *HTTPS://\<IP_ADDRESS\>* 连接到 IP 地址，查看证书中列出的域以了解与此 IP 地址关联的域。 如果 IP 地址属于 Microsoft，但不在 Office 365 IP 地址列表中，则该地址可能与 Microsoft CDN（如 *MSOCDN.NET*）或另一个不具有已发布 IP 信息的 Microsoft 域相关联。 如果发现证书上的域确实是我们宣称列出 IP 地址的域，请告知我们。

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>某些 Office 365 URL 指向 CNAME 记录，而不是 DNS 中的 A 记录。 我与 CNAME 记录有什么关系？

客户端计算机需要包含一个或多个 IP 地址的 DNS A 或 AAAA 记录才能连接到云服务。 Office 365 中包含的某些 URL 显示 CNAME 记录，而不是 A 或 AAAA 记录。 这些 CNAME 记录是中间记录，记录链中可能有多个此类记录。 它们最终将始终解析为 IP 地址的 A 或 AAAA 记录。 例如，考虑以下 DNS 记录系列，这些记录最终将解析为 IP 地址 _IP_1_：

```console
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

这些 CNAME 重定向是 DNS 的常规部分，对客户端计算机和代理服务器都是透明的。 它们用于负载平衡、内容交付网络、高可用性和服务事件缓解。 Microsoft 不会发布中间 CNAME 记录，它们随时可能更改，因此无需按照代理服务器中允许的内容对其进行配置。

代理服务器会验证初始 URL，在上面的示例中为 serviceA.office.com，并且此 URL 将包含在 Office 365 发布中。 代理服务器请求将该 URL 的 DNS 解析为 IP 地址，并将收到 IP_1。 它不会验证中间的 CNAME 重定向记录。

不建议使用基于间接 Office 365 FQDN 的硬编码配置或将其列入允许列表，Microsoft 不支持这种做法，并且已知会导致客户连接问题。 可以通过启用 DNS 递归的 DNS 条件转发（范围仅限于直接使用的 Office 365 FQDN）来解决阻止 CNAME 重定向或以其他方式错误解析 Office 365 DNS 条目的 DNS 解决方案。 许多第三方网络外围产品使用 [Office 365 IP 地址和 URL Web 服务](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)在其配置中本机集成推荐的 Office 365 终结点允许列表。

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>为什么会在 Microsoft 域名中看到 nsatc.net 或 akadns.net 等名称？

Office 365 和其他 Microsoft 服务使用几项第三方服务（如 Akamai 和 MarkMonitor）来改进 Office 365 体验。 为了尽可能提供最佳体验，我们以后可能会更改这些服务。 第三方域可能会托管 CDN 等内容，或者托管地理流量管理服务等服务。 目前正在使用的一些服务包括：
  
如果看到要求中包含 *\*.nsatc.net*，则表示正在使用 [MarkMonitor](https://www.markmonitor.com/)。 此服务提供域名称保护和监控功能，抵御恶意行为。
  
如果看到针对 *\*.exacttarget.com* 的请求，则表示正在使用 [ExactTarget](https://www.marketingcloud.com/)。 此服务提供电子邮件链接管理和监控功能，抵御恶意行为。
  
如果看到请求包括以下一种 FQDN，则表示正在使用 [Akamai](https://www.akamai.com/)。 此服务提供地理 DNS 和内容交付网络服务。
  
```console
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
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>我必须具有尽可能低的 Office 365 连接性

由于 Office 365 是一套构建以通过 Internet 运作的服务，其所承诺的可靠性和可用性以当前可用的许多标准 Internet 服务为基础。 例如，必须能访问 DNS、CRL 和 CDN 等标准 Internet 服务才能使用 Office 365，正如使用大多数现代 Internet 服务时也必须访问这些服务一样。

Office 365 套件分为几个主要服务区域。 可以有选择地启用这些服务区域以进行连接。此外还有一个公用区域，该区域与所有区域都有依赖关系，并且始终必需。

| 服务区域 | 描述 |
|:-----|:-----|
|**Exchange** <br/> |Exchange Online 和 Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online 和 OneDrive for Business <br/> |
|**Skype for Business Online 和 Microsoft Teams** <br/> |Skype for Business 和 Microsoft Teams <br/> |
|**常见** <br/> |Office 365 专业增强版、浏览器中的 Office、Azure AD 和其他常见网络终结点 <br/> |

除了基本的 Internet 服务外，还有一些仅用于集成功能的第三方服务。 尽管集成需要这些服务，但 Office 365 终结点文章中将它们标记为可选，这意味着如果终结点不可访问，该服务的核心功能仍可使用。 所需的任何网络终结点都会将 required 属性设置为 true。 任何可选的网络终结点都会将 required 属性设置为 false，并且 notes 属性将详细说明如果连接被阻止，你应该需要的缺失功能。
  
如果尝试使用 Office 365，但发现第三方服务不可访问，则要[确保本文中标记为“必需”或“可选”的所有 FQDN 均可通过代理和防火墙](urls-and-ip-address-ranges.md)。
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>如何阻止对 Microsoft 消费者服务的访问？

限制访问我们消费者服务的风险应该由你自己承担。 阻止消费者服务的唯一可靠方法是限制对 *login.live.com* FQDN 的访问。 此 FQDN 用于一组广泛的服务，包括 MSDN 和 TechNet 等非消费者服务。 Microsoft 支持的安全文件交换程序也使用此 FQDN，它是传输文件所必需的，便于对 Microsoft 产品进行故障排除。  如果限制访问此 FQDN，这可能导致还需包含与这些服务关联的网络请求的规则例外。
  
请记住，仅阻止访问 Microsoft 消费者服务并不能防止网络中的用户使用 Office 365 租户或其他服务泄露信息。

<a name="bkmk_IPOnlyFirewall"> </a>
### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>我的防火墙需要 IP 地址，并且无法处理 URL。 如何针对 Office 365 进行配置？

Office 365 不提供所有必需的网络终结点的 IP 地址。 有些仅作为 URL 提供，并且被归类为“默认”。 必须通过代理服务器允许使用默认类别中的 URL。 如果没有代理服务器，请查看如何配置对用户输入到 Web 浏览器地址栏中的 URL 的 Web 请求。用户也未提供 IP 地址。 未提供 IP 地址的 Office 365 默认类别 URL 应以相同的方式配置。

## <a name="related-topics"></a>相关主题

[Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)

[Microsoft Azure 数据中心 IP 范围](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公共 IP 空间](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune 的网络基础架构要求](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute 和 Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL 和 IP 地址范围](urls-and-ip-address-ranges.md)
  
[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)
  
[Office 365 网络连接原则](office-365-network-connectivity-principles.md)
