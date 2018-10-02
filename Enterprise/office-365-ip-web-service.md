---
title: Office 365 IP 地址和 URL Web 服务
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/4/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: 为了帮助你更好地标识和区分 Office 365 网络流量，我们推出了一项用于发布 Office 365 终结点的新 Web 服务，以方便你更轻松地评估、配置并掌握最新变更。这项新 Web 服务取代了目前可用的 XML 可下载文件。
ms.openlocfilehash: 2b5763b9f8f08f2cc619331dac70743474a8515b
ms.sourcegitcommit: d67e73f6cdc1e8d220d90a239e23e218f24528d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/21/2018
ms.locfileid: "24961821"
---
# <a name="office-365-ip-address-and-url-web-service"></a>**Office 365 IP 地址和 URL Web 服务**

为了帮助你更好地标识和区分 Office 365 网络流量，我们推出了一项用于发布 Office 365 终结点的新 Web 服务，以方便你更轻松地评估、配置并掌握最新变更。这项新 Web 服务取代了目前可用的 XML 可下载文件。XML 格式计划将于 2018 年 10 月 2 日起逐步淘汰。

作为客户或外围网络设备供应商，你可以构建基于 REST 的新 Web 服务，用于 Office 365 IP 地址和 FQDN 条目。可使用这些 URL 直接在 Web 浏览器中访问数据。

- 若要获取最新版 Office 365 URL 和 IP 地址范围，请使用 [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。
- 若要获取防火墙和代理服务器的 Office 365 URL 和 IP 地址范围页面的相关数据，请使用 [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。
- 若要获取自 2018 年 7 月底这项 Web 服务首次推出以来的所有最新变更，请使用 [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。

作为客户，你可以使用这项 Web 服务：

- 将 PowerShell 脚本更新为获取 Office 365 终结点数据，并修改网络设备的任何格式。
- 根据此类信息更新已部署到客户端计算机的 PAC 文件。

作为网络外围设备供应商，你可以使用这项 Web 服务：

- 创建并测试设备软件，以下载自动配置列表。
- 检查当前版本。
- 获取最新变更。

有关详细信息，请参阅：

- [Office 365 技术社区论坛中的“公告”博客文章](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Office 365 技术社区论坛中有关如何使用 Web 服务的提问](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>**通用参数**

下面两个参数是所有 Web 服务方法的通用参数：

- **format=CSV | JSON** - 查询字符串参数。默认数据返回格式为 JSON。添加此可选参数，可以逗号分隔值 (CSV) 格式返回数据。
- **ClientRequestId** - 查询字符串参数。执行客户端关联必须要生成的 GUID。应为每台调用 Web 服务的计算机都生成 GUID。请勿使用下面示例中的 GUID，因为这项 Web 服务将来可能会屏蔽它们。GUID 格式为 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_，其中 x 表示十六进制数。若要生成 GUID，请运行 [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 命令。

## <a name="version-web-method"></a>**版本 Web 方法**

Microsoft 在每月底更新 Office 365 IP 地址和 FQDN 条目，有时也会因运营或支持要求而不定期更新。每个已发布实例的数据都分配有版本号。借助版本 Web 方法，可以轮询每个 Office 365 服务实例的最新版本。建议每天或至多每小时检查一次版本。新版本应在每月初生成。有时，鉴于支持事件、安全性或其他运营要求，新版本还会在每月其他时间生成。

版本 Web 方法需要使用下面各个参数：

- **AllVersions=true** - 查询字符串参数。默认返回最新版本。添加此可选参数，可请求获取所有已发布版本。
- **Format=JSON** | **CSV** | **RSS** - 除了 JSON 和 CSV 格式以外，版本 Web 方法还支持 RSS。可将此参数与 allVersions=true 参数结合使用，以请求获取能用于 Outlook 或其他 RSS 阅读器的 RSS 源。
- **Instance** - 路由参数。此可选参数指定要返回哪个实例的版本。如果省略，将返回所有实例的版本。有效实例为 Worldwide、China、Germany、USGovDoD 和 USGovGCCHigh。

版本 Web 方法的结果可以是一条记录，也可以是一组记录。每条记录均包含以下元素：

- instance - Office 365 服务实例的短名称。
- latest - 指定实例的终结点的最新版本。
- versions - 指定实例的所有旧版本列表。仅当 AllVersions 参数为 true 时，才包含此元素。

可以使用 Microsoft Flow 来获取对 IP 地址和 URL 所做的更改的电子邮件通知。请参阅[使用 Microsoft Flow 接收对 Office 365 IP 地址和 URL 所做的更改的电子邮件](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)。

### <a name="examples"></a>**示例：**

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

[!IMPORTANT]
这些 URI 中 ClientRequestID 参数的 GUID 只是个例子。若要试用 Web 服务 URI，请生成你自己的 GUID。这项 Web 服务将来可能会屏蔽这些示例中的 GUID。

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
<rss version="2.0" xmlns:a10="http://www.w3.org/2005/Atom">
<channel>
<link>http://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
...
```

## <a name="endpoints-web-method"></a>**终结点 Web 方法**

终结点 Web 方法返回组成 Office 365 服务的 IP 地址范围和 URL 的所有记录。虽然来自终结点 Web 方法的最新数据应用于网络设备配置，但由于有附加事先通知，数据在发布后最多可缓存 30 天。终结点 Web 方法需要使用以下参数：

- **ServiceAreas** - 查询字符串参数。此参数指定服务区域的逗号分隔列表。有效项为 Common、Exchange、SharePoint 和 Skype。因为 Common 服务区域项是其他所有服务区域的先决条件，所以 Web 服务始终包含此项。如果你不添加此参数，将返回所有服务区域。
- **TenantName** - 查询字符串参数。此参数指定 Office 365 租户名称。这项 Web 服务获取你提供的名称，并将它插入包含租户名称的 URL 部分中。如果你未提供租户名称，这些 URL 部分包含的是通配符 (\*)。
- **NoIPv6** - 查询字符串参数。将此属性设置为 true，可从输出中排除 IPv6 地址（例如，你在网络中没有使用 IPv6 的话）。
- **Instance** - 路由参数。此必需参数指定要返回哪个实例的终结点。有效实例为 Worldwide、China、Germany、USGovDoD 和 USGovGCCHigh。

终结点 Web 方法的结果是一组记录，每条记录均代表一个终结点集。每条记录均包含以下元素：

- id - 终结点集的不可变 ID 号。
- serviceArea - 所属的服务区域，有效项为 Common、Exchange、SharePoint 或 Skype。
- urls - 终结点集的 URL。此为包含 DNS 记录的 JSON 数组。若为空白，将省略此元素。
- tcpPorts - 终结点集的 TCP 端口。所有端口元素都格式化为端口的逗号分隔列表，或用短划线字符 (-) 分隔的端口范围。端口适用于相应类别的特定终结点集中的所有 IP 地址和所有 URL。若为空白，将省略此元素。
- udpPorts - 此终结点集中 IP 地址范围的 UDP 端口。若为空白，将省略此元素。
- ips - 与此终结点关联的 IP 地址范围，设置为与列出的 TCP 或 UDP 端口关联。IP 地址范围的 JSON 数组。若为空白，将省略此元素。
- category - 端点集的连接类别。有效值为 Optimize、Allow 和 Default。如果使用端点数据搜索某个类别的 IP 地址或 URL，查询可能会返回多个类别。出现这种情况的原因有多种。此时，你应该遵循针对最高优先级类别的建议。例如，如果既有 Optimize 类别又有 Allow 类别的端点，则应遵循针对 Optimize 的要求。必须提供。 
- expressRoute - True 或 False，表示此终结点集是否通过 ExpressRoute 进行路由。
- required - 如果此终结点集必须有连接才能支持 Office 365，则为 True。如果此终结点集是可选的，则为 false。
- notes - 对于可选终结点，此文本描述了无法在网络层访问此终结点集中 IP 地址或 URL 的情况下缺少的 Office 365 功能。若为空白，将省略此元素。

### <a name="examples"></a>示例：

示例 1 请求 URI：[https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此 URI 对全部工作负载获取 Office 365 全球实例的所有终结点。示例结果的输出摘录如下：

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
...
```

此示例中不包含其他终结点集。

示例 2 请求 URI：[https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此示例仅对 Exchange Online 和依赖项获取 Office 365 全球实例的终结点。

示例 2 的输出类似于示例 1，不同之处在于结果不包括 SharePoint Online 或 Skype for Business Online 终结点。

## <a name="changes-web-method"></a>变更 Web 方法

变更 Web 方法返回已发布的最新更新。这通常是上月的 IP 地址范围和 URL 变更。要处理的最关键变更是添加新 URL 或 IP 地址，因为如果无法将 IP 地址添加到防火墙访问控制列表，或无法将 URL 添加到代理服务器跳过列表，可能会导致相应网络设备后的 Office 365 用户遇到服务中断。尽管有运营要求，但 _Add_ 操作会在添加前提前 30 天发出通知，以免发生此类服务中断。

变更 Web 方法需要使用以下参数：

- **Version** - 必需的 URL 路由参数。此参数指定当前实现的版本，且要查看自这一版本起的变更。格式是 _YYYYMMDDNN_。

变更 Web 方法的结果是一组记录，每条记录均代表特定版本终结点中的变更。每条记录均包含以下元素：

- id - 变更记录的不可变 ID。
- endpointSetId - 变更的终结点集记录的 ID。此为必需元素。
- disposition - 此元素可以是两种变更之一（add 或 remove），描述了终结点集记录有何变更。此为必需元素。
- version - 引入变更的已发布终结点集的版本。版本号格式为 _YYYYMMDDNN_，其中 NN 是必须在一天内发布多个版本时递增的自然数。
- previous - 详细说明终结点集中已变更元素的旧值的子结构。对于新添加的终结点集，不包含此元素。此元素包括 tcpPorts、udpPorts、ExpressRoute、category、required 和 notes。
- current - 详细说明终结点集中已变更元素的更新值的子结构。此元素包括 tcpPorts、udpPorts、ExpressRoute、category、required 和 notes。
- add - 详细说明要添加到终结点集集合的项的子结构。如果没有要添加的项，将省略此元素。
  - effectiveDate - 定义添加项在服务中的生效日期。
  - ips - 要添加到 ips 数组的项。
  - urls - 要添加到 urls 数组的项。
- remove - 详细说明要从终结点集中删除的项的子结构。如果没有要删除的项，将省略此元素。
  - ips - 要从 ips 数组中删除的项。
  - urls - 要从 urls 数组中删除的项。

### <a name="examples"></a>**示例：**

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
...
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

## <a name="example-powershell-script"></a>**示例 PowerShell 脚本**

运行下面的 PowerShell 脚本，可确定是否需要对已更新数据执行操作。此脚本检查 Office 365 全球实例终结点的版本号。若有变更，它就会下载终结点，并筛选出 &quot;Allow&quot; 和 &quot;Optimize&quot; 类别终结点。它还会跨多个调用使用唯一 ClientRequestId，并将找到的最新版本保存到临时文件中。应每小时调用一次此脚本，以检查是否有版本更新。

```powershell
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"

    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
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
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }

        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a>**示例 Python 脚本**

运行下面的 Python 脚本（已使用 Windows 10 上的 Python 3.6.3 进行测试），可确定是否需要对已更新数据执行操作。此脚本检查 Office 365 全球实例终结点的版本号。若有变更，它就会下载终结点，并筛选出 _Allow_ 和 _Optimize_ 类别终结点。它还会跨多个调用使用唯一 ClientRequestId，并将找到的最新版本保存到临时文件中。应每小时调用一次此脚本，以检查是否有版本更新。

```python
import json
import os
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
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
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

## <a name="web-service-interface-versioning"></a>**Web 服务接口版本控制**

日后可能需要更新这些 Web 服务方法的参数或结果。在这些 Web 服务的正式版本发布后，Microsoft 将做出合理的努力，以事先通知 Web 服务的实质性更新。如果认为更新必须变更使用 Web 服务的客户端，Microsoft 将在新版本发布后的至少十二 (12) 个月内保留旧版（上一版）Web 服务。在此期间未升级的客户可能无法访问 Web 服务及其方法。如果 Web 服务接口签名发生以下变更，客户必须确保 Web 服务的客户端能继续正常运行，而不出现错误：

- 将新的可选参数添加到现有 Web 方法中，此参数既不必由旧客户端提供，也不会影响旧客户端收到的结果。
- 将响应 REST 项之一或其他列中的新命名特性添加到响应 CSV。
- 添加新 Web 方法，其使用旧客户端未调用的新名称。

## <a name="related-topics"></a>相关主题
  
[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 终结点 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Office 365 网络连接原则](office-365-network-connectivity-principles.md)

[Office 365 网络和性能优化](network-planning-and-performance.md)

[与 Office 365 的网络连接](network-connectivity.md)
  
[Skype for Business Online 中的媒体质量和网络连接性能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[优化 Skype for Business Online 网络](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[使用基线和性能历史记录优化 Office 365 性能](performance-tuning-using-baselines-and-history.md)
  
[Office 365 性能疑难解答计划](performance-troubleshooting-plan.md)
