---
title: Office 365 IP 地址和 URL Web 服务
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/6/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Office 365 IP 地址和 URL Web 服务可帮助你更好地识别和区分 Office 365 网络流量，以便更轻松地评估、配置和及时了解最新变更。
ms.openlocfilehash: 7a1d882b6bc5e34e3d59cf4bade30a58a1c76d6f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843595"
---
# <a name="office-365-ip-address-and-url-web-service"></a>Office 365 IP 地址和 URL Web 服务

Office 365 IP 地址和 URL Web 服务可帮助你更好地识别和区分 Office 365 网络流量，以便更轻松地评估、配置和及时了解最新变更。 此基于 REST 的 Web 服务将取代自 2018 年 10 月 2 日开始逐步停止使用的旧版 XML 可下载文件。

作为客户或网络外围设备供应商，你可以针对 Office 365 IP 地址和 FQDN 条目构建 Web 服务。 你可以使用以下 URL 直接访问 Web 浏览器中的数据：

- 若要获取最新版 Office 365 URL 和 IP 地址范围，请使用 [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。
- 若要获取防火墙和代理服务器的 Office 365 URL 和 IP 地址范围页面的相关数据，请使用 [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。
- 若要获取自 2018 年 7 月这项 Web 服务首次推出以来的所有最新变更，请使用 [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。

作为客户，你可以使用这项 Web 服务：

- 将 PowerShell 脚本更新为获取 Office 365 终结点数据，并修改网络设备的任何格式。
- 根据此类信息更新已部署到客户端计算机的 PAC 文件。

作为网络外围设备供应商，你可以使用这项 Web 服务：

- 创建并测试设备软件，以下载自动配置列表。
- 检查当前版本。
- 获取最新变更。

> [!NOTE]
> 如果正在使用 Azure ExpressRoute 连接到 Office 365，请查看[适用于 Office 365 的 Azure ExpressRoute](https://docs.microsoft.com/office365/enterprise/azure-expressroute) 以熟悉 Azure expressroute 支持的 Office 365 服务。 另请查看 [Office 365 URL 和 IP 地址范围](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)，以了解 Office 365 应用程序的哪些网络请求需要 Internet 连接。 这有助于更好地配置外围安全设备。

有关详细信息，请参阅：

- [Office 365 技术社区论坛中的“公告”博客文章](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Office 365 技术社区论坛中有关如何使用 Web 服务的提问](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>通用参数

下面两个参数是所有 Web 服务方法的通用参数：

- **format=<JSON | CSV>** — 默认情况下，返回数据的格式为 JSON。 使用此可选参数返回采用逗号分隔值 (CSV) 格式的数据。
- **ClientRequestId=\<guid>** — 为客户端关联生成的所需 GUID。 为调用 Web 服务的每台计算机生成唯一的 GUID（此页面上包含的脚本将为你生成 GUID）。 请勿使用以下示例中所示的 GUID，因为它们将来可能会被 Web 服务阻止。 GUID 格式为 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_，其中 x 表示一个十六进制数字。

  若要生成 GUID，你可以使用 [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 命令，或使用[在线 GUID 生成器](https://www.guidgenerator.com/)等在线服务。

## <a name="version-web-method"></a>版本 Web 方法

Microsoft 会在每个月末更新 Office 365 IP 地址和 FQDN 条目。 出于支持事件、安全更新或其他操作要求，有时会发布带外更新。

我们为每个已发布实例的数据分配了版本号，你可以通过版本 Web 方法检查每个 Office 365 服务实例的最新版本。 我们建议每小时检查版本的次数不要超过一次。

版本 Web 服务的参数如下：

- **AllVersions=<true | false>** — 默认情况下，返回的版本为最新的。 包括此可选参数，以请求首次发布 Web 服务之后的所有已发布版本。
- **Format=<JSON | CSV | RSS>** — 除了 JSON 和 CSV 格式，版本 Web 服务还支持 RSS。 可以结合使用此可选参数及 _AllVersions=true_ 参数，以请求可用于 Outlook 或其他 RSS 读取器的 RSS 源。
- **Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — 此可选参数用于指定返回其版本的实例。 如果圣罗，则会返回所有实例。 有效实例包括：Worldwide、China、Germany、USGovDoD、USGovGCCHigh。

版本 Web 方法不受速率限制，并且决不会返回 429 HTTP 响应代码。 对版本 Web 方法的响应包括一个缓存控制标头，它建议将数据缓存 1 小时。 版本 Web 方法的结果可以是一条记录，也可以是一组记录。 每条记录均包含以下元素：

- instance — Office 365 服务实例的短名称。
- latest — 指定实例的终结点的最新版本。
- 版本 — 指定实例的所有旧版本的列表。 仅当 _AllVersions_ 参数为 true 时才包含此元素。

### <a name="examples"></a>示例：

示例 1 请求 URI：[https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此 URI 返回每个 Office 365 服务实例的最新版本。示例结果如下：

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> 这些 URI 中 ClientRequestID 参数的 GUID 只是个例子。若要试用 Web 服务 URI，请生成你自己的 GUID。这项 Web 服务将来可能会屏蔽这些示例中的 GUID。

示例 2 请求 URI：[https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此 URI 返回指定 Office 365 服务实例的最新版本。示例结果如下：

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

示例 3 请求 URI：[https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此 URI 显示 CSV 格式输出。示例结果如下：

```csv
instance,latest
Worldwide,2018063000
```

示例 4 请求 URI：[https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此 URI 显示 Office 365 全球服务实例的所有已发布旧版本。示例结果如下：

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

示例 5 RSS 源 URI：[https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)

此 URI 显示已发布版本的 RSS 源，其中包含指向每个版本的变更列表的链接。示例结果如下：

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="https://www.w3.org/2005/Atom">
<channel>
<link>https://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a>终结点 Web 方法

终结点 Web 方法可返回组成 Office 365 服务的 IP 地址范围和 URL 的所有记录。 应始终使用最新的终结点 Web 方法数据来进行网络设备配置。 Microsoft 会在发布新增内容前 30 天提前发出通知，以便你有时间更新访问控制列表和代理服务器跳过列表。 建议你仅在版本 Web 方法表示存在新的数据版本时才再次调用终结点 Web 方法。

终结点 Web 方法的参数如下：

- **ServiceAreas=<Common | Exchange | SharePoint | Skype>** — 以逗号分隔的服务区域列表。 有效项为 _Common_、_Exchange_、_SharePoint_ 和 _Skype_。 由于 _Common_ 服务区域项为所有其他服务区域的先决条件，因此 Web 服务始终包括它们。 如果不包括此参数，则会返回所有服务区域。
- **TenantName=<tenant_name>** — 你的 Office 365 租户名称。 Web 服务采用所提供的名称，并将其插入到包含租户名称的 URL 中。 如果未提供租户名称，则这些 URL 的部分具有通配符字符 (\*)。
- **NoIPv6=<true | false>** — 将此值设置为 _true_ 可从输出中排除 IPv6 地址（如果你未在网络中使用 IPv6）。
- **Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — 此必填参数用于指定从中返回终结点的实例。 有效实例包括：_Worldwide_、_China_、_Germany_、_USGovDoD_ 和 _USGovGCCHigh_。

如果从相同客户端 IP 地址调用终结点 Web 方法的次数过多，则可能会收到 HTTP 响应代码 _429（请求过多）_。 如果收到此响应代码，请先等待 1 小时，然后再重复你的请求，或者为该请求生成新的 GUID。 作为一般的最佳实践，仅在版本 Web 方法表示存在新的可用版本时才调用终结点 Web 方法。

终结点 Web 方法的结果是一组记录，每条记录均代表一个终结点集。 每条记录均包含以下元素：

- id — 终结点集的不可变 ID 号。
- serviceArea — 所属的服务区域：_Common_、_Exchange_、_SharePoint_ 或 _Skype_。
- urls — 终结点集的 URL。 此为包含 DNS 记录的 JSON 数组。 若为空白，将省略此元素。
- tcpPorts — 终结点集的 TCP 端口。 所有端口元素都格式化为端口的逗号分隔列表，或用短划线字符 (-) 分隔的端口范围。 端口适用于相应类别的特定终结点集中的所有 IP 地址和所有 URL。 若为空白，将省略此元素。
- udpPorts — 此终结点集中 IP 地址范围的 UDP 端口。 若为空白，将省略此元素。
- ips — 与此终结点关联的 IP 地址范围，设置为与列出的 TCP 或 UDP 端口关联。 IP 地址范围的 JSON 数组。 若为空白，将省略此元素。
- category — 终结点集的连接类别。 有效值为 _Optimize_、_Allow_ 和 _Default_。 如果搜索特定 IP 地址或 URL 类别的终结点 Web 方法输出，则查询可能会返回多个类别。 在这种情况下，请按照最高优先级类别的建议操作。 例如，如果终结点同时显示在 _Optimize_ 和 _Allow_ 中，则应该遵循 _Optimize_ 的要求。 必需项。
- expressRoute — 如果此终结点集通过 ExpressRoute 进行路由，则为 _True_，否则为 _False_。
- required — 如果此终结点集必须有连接才能支持 Office 365，则为 _True_。 如果此终结点集为可选，则为 _False_。
- notes — 对于可选终结点，此文本描述了无法在网络层访问此终结点集中的 IP 地址或 URL 的情况下不可用的 Office 365 功能。 若为空白，将省略此元素。

### <a name="examples"></a>示例：

示例 1 请求 URI：[https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此 URI 对全部工作负载获取 Office 365 全球实例的所有终结点。 示例结果的输出摘录如下：

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

请注意，此示例中的请求的完整输出将包含其他终结点集。

示例 2 请求 URI：[https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此示例仅对 Exchange Online 和依赖项获取 Office 365 全球实例的终结点。

示例 2 的输出类似于示例 1，不同之处在于结果不包括 SharePoint Online 或 Skype for Business Online 终结点。

## <a name="changes-web-method"></a>变更 Web 方法

变更 Web 方法返回已发布的最新更新。这通常是上月的 IP 地址范围和 URL 变更。

终结点数据的最重要变更是新 URL 或 IP 地址。 如果无法将 IP 地址添加到防火墙访问控制列表，或无法将 URL 添加到代理服务器跳过列表，可能会导致网络设备后的 Office 365 用户遇到服务中断。 尽管有运营要求，新的终结点将在其配置使用之日的前 30 天提前发布到 Web 服务，以便你有时间更新访问控制列表和代理服务器跳过列表。

变更 Web 方法需要使用以下必填参数：

- **Version=\<YYYYMMDDNN>** — 所需的 URL 路由参数。 此值为当前实施的版本。 Web 服务应返回自该版本之后发生的变更。 格式为 _YYYYMMDDNN_；如果需要在一天内发布多个版本，则 _NN_ 是一个递增的自然数，而 _00_ 表示给定日期的第一个更新。 Web 服务要求 _version_ 参数恰好包含 10 位数。

变更 Web 方法受速率限制，与终结点 Web 方法受限于速率一样。 如果收到 429 HTTP 响应代码，请先等待 1 小时，然后再重复你的请求，或者为该请求生成新的 GUID。

变更 Web 方法的结果是一组记录，每条记录均代表特定版本终结点中的变更。 每条记录均包含以下元素：

- id — 变更记录的不可变 ID。
- endpointSetId — 变更的终结点集记录的 ID。
- disposition — 描述了终结点集记录有何变更。 值包括 _change_、_add_ 或 _remove_。
- impact — 并非所有变更都对每个环境同样重要。 此元素说明了相应变更对企业网络外围环境的预期影响。 此属性仅包含在版本 **2018112800** 及更高版本的变更记录中。 impact 选项包括：— AddedIp – IP 地址已添加到 Office 365，且很快就会对服务生效。 这表示需要更改防火墙或其他第 3 层网络外围设备。 如果你并没有在我们开始使用此元素之前添加它，可能会遇到故障。
  — AddedUrl – URL 已添加到 Office 365，且很快就会对服务生效。 这表示需要更改代理服务器或 URL 分析网络外围设备。 如果你并没有在我们开始使用之前添加此 URL，可能会遇到故障。
  — AddedIpAndUrl — IP 地址和 URL 均已添加。 这表示需要更改防火墙第 3 层设备、代理服务器或 URL 分析设备。 如果你并没有在我们开始使用之前添加此 IP/URL，可能会遇到故障。
  — RemovedIpOrUrl – 从 Office 365 中至少删除了一个 IP 地址或 URL。 从外围设备中删除网络终结点，但此操作并无截止时间。
  — ChangedIsExpressRoute – ExpressRoute 支持属性已更改。 如果使用 ExpressRoute，可能需要采取措施，具体视配置而定。
  — MovedIpOrUrl – 在此终结点集和另一个终结点集之间迁移了 IP 地址或 URL。 通常无需采取任何措施。
  — RemovedDuplicateIpOrUrl – 删除了重复的 IP 地址或 URL，但它仍是对 Office 365 发布的。 通常无需采取任何措施。
  — OtherNonPriorityChanges – 更改了一些不如其他所有选项重要的内容，例如注释字段的内容。
- version — 引入变更的已发布终结点集的版本。 版本号格式为 _YYYYMMDDNN_，其中 _NN_ 是必须在一天内发布多个版本时递增的自然数。
- previous — 详细说明终结点集上的旧变更元素值的子结构。 对于新添加的终结点集，它们未包含在内。 包括 _ExpressRoute_、_serviceArea_、_category_、_required_、_tcpPorts_、_udpPorts_ 和 _notes_。
- current — 详细说明终结点集上的更新变更元素值的子结构。 包括 _ExpressRoute_、_serviceArea_、_category_、_required_、_tcpPorts_、_udpPorts_ 和 _notes_。
- add — 详细说明要添加到终结点集集合的项的子结构。 如果没有要添加的项，将省略此元素。
  — effectiveDate — 定义添加项在服务中的生效日期。
  — ips — 要添加到 _ips_ 数组的项。
  — urls — 要添加到 _urls_ 数组的项。
- remove — 详细说明要从终结点集中删除的项的子结构。 如果没有删除项，则省略。
  — ips — 要从 _ips_ 数组中删除的项。
  — urls — 要从 _urls_ 数组中删除的项。

### <a name="examples"></a>示例：

示例 1 请求 URI：[https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

这请求获取 Office 365 全球服务实例先前的所有变更。示例结果如下：

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

示例 2 请求 URI：[https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

这请求获取 Office 365 全球实例自指定版本起的变更。在此示例中，指定版本是最新版本。示例结果如下：

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>示例 PowerShell 脚本

你可以运行此 PowerShell 脚本来查看是否需要为更新的数据采取操作。 你可以将此脚本作为计划任务运行，以检查是否存在版本更新。 为了避免 Web 服务出现过多负载，每小时运行脚本的次数不要超过一次。

此脚本执行以下操作：

- 通过调用 Web 服务 REST API，检查 Office 365 全球实例终结点的版本号。
- 检查 _$Env:TEMP\O365_endpoints_latestversion.txt_ 中的当前版本文件。 全局变量 **$Env:TEMP** 的路径通常为 _C:\Users\\<username\>\AppData\Local\Temp_。
- 如果这是首次运行脚本，则脚本将返回当前版本以及所有当前 IP 地址和 URL，将终结点版本写入文件 _$Env:TEMP\O365_endpoints_latestversion.txt_，并将终结点数据输出写入文件 _$Env:TEMP\O365_endpoints_data.txt_。 可通过编辑以下行来修改输出文件的路径和/或名称：

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- 在后续每次执行脚本时，如果最新的 Web 服务版本与 _O365_endpoints_latestversion.txt_ 文件中的版本相同，则脚本将退出，而不进行任何更改。
- 如果最新的 Web 服务版本比 _O365_endpoints_latestversion.txt_ 文件中的版本更新，则该脚本将返回 **Allow** 和 **Optimize** 类别的终结点和筛选器，更新 _O365_endpoints_latestversion.txt_ 文件中的版本，并将更新的数据写入 _O365_endpoints_data.txt_ 文件。

该脚本将为在其上运行的计算机生成唯一的 _ClientRequestId_，并在多个调用中重复使用此 ID。 此 ID 存储在 _O365_endpoints_latestversion.txt_ 文件中。

### <a name="to-run-the-powershell-script"></a>运行 PowerShell 脚本

1. 复制脚本并在本地硬盘驱动器或脚本位置将其另存为 _Get-O365WebServiceUpdates.ps1_。
1. 在首选脚本编辑器（如 PowerShell ISE 或 VS Code）中执行脚本，或使用以下命令从 PowerShell 控制台执行：

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    不向脚本传递任何参数。

```powershell
<# Get-O365WebServiceUpdates.ps1
From https://aka.ms/ipurlws
v1.1 8/6/2019

DESCRIPTION
This script calls the REST API of the Office 365 IP and URL Web Service (Worldwide instance)
and checks to see if there has been a new update since the version stored in an existing
$Env:TEMP\O365_endpoints_latestversion.txt file in your user directory's temp folder
(usually C:\Users\<username>\AppData\Local\Temp).
If the file doesn't exist, or the latest version is newer than the current version in the
file, the script returns IPs and/or URLs that have been changed, added or removed in the latest
update and writes the new version and data to the output file $Env:TEMP\O365_endpoints_data.txt.

USAGE
Run as a scheduled task every 60 minutes.

PARAMETERS
n/a

PREREQUISITES
PS script execution policy: Bypass
PowerShell 3.0 or later
Does not require elevation
#>

#Requires -Version 3.0

# web service root URL
$ws = "https://endpoints.office.com"
# path where output files will be stored
$versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
$datapath = $Env:TEMP + "\O365_endpoints_data.txt"

# fetch client ID and version if version file exists; otherwise create new file and client ID
if (Test-Path $versionpath) {
    $content = Get-Content $versionpath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
    Write-Output ("Version file exists! Current version: " + $lastVersion)
}
else {
    Write-Output ("First run! Creating version file at " + $versionpath + ".")
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $versionpath
}

# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    # write the new version number to the version file
    @($clientRequestId, $version.latest) | Out-File $versionpath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    # URL results
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    # IPv4 results
    $flatIp4s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings contain dots
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        $ip4CustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ip4CustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip4CustomObjects
    }
    # IPv6 results
    $flatIp6s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv6 strings contain colons
        $ip6s = $ips | Where-Object { $_ -like '*:*' }
        $ip6CustomObjects = @()
        if ($endpointSet.category -in ("Optimize")) {
            $ip6CustomObjects = $ip6s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip6CustomObjects
    }

    # write output to screen
    Write-Output ("Client Request ID: " + $clientRequestId)
    Write-Output ("Last Version: " + $lastVersion)
    Write-Output ("New Version: " + $version.latest)
    Write-Output ""
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    Write-Output ("IP and URL data written to " + $datapath)

    # write output to data file
    Write-Output "Office 365 IP and UL Web Service data" | Out-File $datapath
    Write-Output "Worldwide instance" | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output ("Version: " + $version.latest) | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv4 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv6 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "URLs for Proxy Server" | Out-File $datapath -Append
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-File $datapath -Append
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date."
}
```

## <a name="example-python-script"></a>示例 Python 脚本

运行下面的 Python 脚本（已使用 Windows 10 上的 Python 3.6.3 进行测试），可确定是否需要对已更新数据执行操作。此脚本检查 Office 365 全球实例终结点的版本号。若有变更，它就会下载终结点，并筛选出 _Allow_ 和 _Optimize_ 类别终结点。它还会跨多个调用使用唯一 ClientRequestId，并将找到的最新版本保存到临时文件中。应每小时调用一次此脚本，以检查是否有版本更新。

```python
import json
import tempfile
from pathlib import Path
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = Path(tempfile.gettempdir() + '/endpoints_clientid_latestversion.txt')
# fetch client ID and version if data exists; otherwise create new file
if datapath.exists():
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>Web 服务接口版本控制

日后可能需要更新这些 Web 服务方法的参数或结果。 在这些 Web 服务的正式版本发布后，Microsoft 将做出合理的努力，以事先通知 Web 服务的实质性更新。 如果认为更新必须变更使用 Web 服务的客户端，Microsoft 将在新版本发布后的至少 12 个月内保留旧版（上一版）Web 服务。 在此期间未升级的客户可能无法访问 Web 服务及其方法。 如果 Web 服务接口签名发生以下变更，客户必须确保 Web 服务的客户端能继续正常运行，而不出现错误：

- 将新的可选参数添加到现有 Web 方法中，此参数既不必由旧客户端提供，也不会影响旧客户端收到的结果。
- 将响应 REST 项之一或其他列中的新命名特性添加到响应 CSV。
- 添加新 Web 方法，其使用旧客户端未调用的新名称。

## <a name="update-notifications"></a>更新通知

当 IP 地址和 URL 的变更发布到 Web 服务时，你可以使用几种不同的方法来获取电子邮件通知。

- 若要使用 Microsoft Flow 解决方案，请参阅[使用 Microsoft Flow 接收对 Office 365 IP 地址和 URL 所做的更改的电子邮件](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)。
- 若要使用 ARM 模板部署 Azure Logic App，请参阅 [Office 365 更新通知 (v1.1)](https://aka.ms/ipurlws-updates-template)。
- 若要使用 PowerShell 编写自己的通知脚本，请参阅 [Send-MailMessage](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage)。

## <a name="exporting-a-proxy-pac-file"></a>导出代理 PAC 文件

[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) 是 PowerShell 脚本，它从 Office 365 IP 地址和 URL Web 服务读取最新网络终结点，并创建示例 PAC 文件。 有关使用 Get-PacFile 的信息，请参阅[使用 PAC 文件进行至关重要的 Office 365 流量的直接路由](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic)。

## <a name="related-topics"></a>相关主题
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[管理 Office 365 终结点](managing-office-365-endpoints.md)
  
[Office 365 终结点 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Office 365 网络连接原则](office-365-network-connectivity-principles.md)

[Office 365 网络和性能优化](network-planning-and-performance.md)

[评估 Office 365 网络连接](assessing-network-connectivity.md)
  
[Skype for Business Online 中的媒体质量和网络连接性能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[优化 Skype for Business Online 网络](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)
  
[Office 365 性能疑难解答计划](performance-troubleshooting-plan.md)
