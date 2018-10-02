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
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="e1d85-104">**Office 365 IP 地址和 URL Web 服务**</span><span class="sxs-lookup"><span data-stu-id="e1d85-104">**Office 365 IP Address and URL Web service**</span></span>

<span data-ttu-id="e1d85-p102">为了帮助你更好地标识和区分 Office 365 网络流量，我们推出了一项用于发布 Office 365 终结点的新 Web 服务，以方便你更轻松地评估、配置并掌握最新变更。这项新 Web 服务取代了目前可用的 XML 可下载文件。XML 格式计划将于 2018 年 10 月 2 日起逐步淘汰。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="e1d85-p103">作为客户或外围网络设备供应商，你可以构建基于 REST 的新 Web 服务，用于 Office 365 IP 地址和 FQDN 条目。可使用这些 URL 直接在 Web 浏览器中访问数据。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="e1d85-110">若要获取最新版 Office 365 URL 和 IP 地址范围，请使用 [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="e1d85-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="e1d85-111">若要获取防火墙和代理服务器的 Office 365 URL 和 IP 地址范围页面的相关数据，请使用 [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="e1d85-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="e1d85-112">若要获取自 2018 年 7 月底这项 Web 服务首次推出以来的所有最新变更，请使用 [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="e1d85-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="e1d85-113">作为客户，你可以使用这项 Web 服务：</span><span class="sxs-lookup"><span data-stu-id="e1d85-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="e1d85-114">将 PowerShell 脚本更新为获取 Office 365 终结点数据，并修改网络设备的任何格式。</span><span class="sxs-lookup"><span data-stu-id="e1d85-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="e1d85-115">根据此类信息更新已部署到客户端计算机的 PAC 文件。</span><span class="sxs-lookup"><span data-stu-id="e1d85-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="e1d85-116">作为网络外围设备供应商，你可以使用这项 Web 服务：</span><span class="sxs-lookup"><span data-stu-id="e1d85-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="e1d85-117">创建并测试设备软件，以下载自动配置列表。</span><span class="sxs-lookup"><span data-stu-id="e1d85-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="e1d85-118">检查当前版本。</span><span class="sxs-lookup"><span data-stu-id="e1d85-118">Check for the current version.</span></span>
- <span data-ttu-id="e1d85-119">获取最新变更。</span><span class="sxs-lookup"><span data-stu-id="e1d85-119">Get the current changes.</span></span>

<span data-ttu-id="e1d85-120">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="e1d85-120">For additional information, see:</span></span>

- [<span data-ttu-id="e1d85-121">Office 365 技术社区论坛中的“公告”博客文章</span><span class="sxs-lookup"><span data-stu-id="e1d85-121">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="e1d85-122">Office 365 技术社区论坛中有关如何使用 Web 服务的提问</span><span class="sxs-lookup"><span data-stu-id="e1d85-122">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="e1d85-123">**通用参数**</span><span class="sxs-lookup"><span data-stu-id="e1d85-123">**Common parameters**</span></span>

<span data-ttu-id="e1d85-124">下面两个参数是所有 Web 服务方法的通用参数：</span><span class="sxs-lookup"><span data-stu-id="e1d85-124">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="e1d85-p104">**format=CSV | JSON** - 查询字符串参数。默认数据返回格式为 JSON。添加此可选参数，可以逗号分隔值 (CSV) 格式返回数据。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p104">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="e1d85-p105">**ClientRequestId** - 查询字符串参数。执行客户端关联必须要生成的 GUID。应为每台调用 Web 服务的计算机都生成 GUID。请勿使用下面示例中的 GUID，因为这项 Web 服务将来可能会屏蔽它们。GUID 格式为 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_，其中 x 表示十六进制数。若要生成 GUID，请运行 [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p105">**ClientRequestId** - Query string parameter. A required GUID that you generate for client association. You should generate a GUID for each machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="e1d85-134">**版本 Web 方法**</span><span class="sxs-lookup"><span data-stu-id="e1d85-134">**Version web method**</span></span>

<span data-ttu-id="e1d85-p106">Microsoft 在每月底更新 Office 365 IP 地址和 FQDN 条目，有时也会因运营或支持要求而不定期更新。每个已发布实例的数据都分配有版本号。借助版本 Web 方法，可以轮询每个 Office 365 服务实例的最新版本。建议每天或至多每小时检查一次版本。新版本应在每月初生成。有时，鉴于支持事件、安全性或其他运营要求，新版本还会在每月其他时间生成。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p106">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="e1d85-141">版本 Web 方法需要使用下面各个参数：</span><span class="sxs-lookup"><span data-stu-id="e1d85-141">There is one parameter for the version web method:</span></span>

- <span data-ttu-id="e1d85-p107">**AllVersions=true** - 查询字符串参数。默认返回最新版本。添加此可选参数，可请求获取所有已发布版本。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p107">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span>
- <span data-ttu-id="e1d85-p108">**Format=JSON** | **CSV** | **RSS** - 除了 JSON 和 CSV 格式以外，版本 Web 方法还支持 RSS。可将此参数与 allVersions=true 参数结合使用，以请求获取能用于 Outlook 或其他 RSS 阅读器的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p108">**Format=JSON** | **CSV** | **RSS** – In addition to the JSON and CSV formats, the version web method also supports RSS. You can use this along with the allVersions=true parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="e1d85-p109">**Instance** - 路由参数。此可选参数指定要返回哪个实例的版本。如果省略，将返回所有实例的版本。有效实例为 Worldwide、China、Germany、USGovDoD 和 USGovGCCHigh。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p109">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="e1d85-p110">版本 Web 方法的结果可以是一条记录，也可以是一组记录。每条记录均包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p110">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="e1d85-153">instance - Office 365 服务实例的短名称。</span><span class="sxs-lookup"><span data-stu-id="e1d85-153">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="e1d85-154">latest - 指定实例的终结点的最新版本。</span><span class="sxs-lookup"><span data-stu-id="e1d85-154">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="e1d85-p111">versions - 指定实例的所有旧版本列表。仅当 AllVersions 参数为 true 时，才包含此元素。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p111">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="e1d85-p112">可以使用 Microsoft Flow 来获取对 IP 地址和 URL 所做的更改的电子邮件通知。请参阅[使用 Microsoft Flow 接收对 Office 365 IP 地址和 URL 所做的更改的电子邮件](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p112">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="e1d85-159">**示例：**</span><span class="sxs-lookup"><span data-stu-id="e1d85-159">**Examples:**</span></span>

<span data-ttu-id="e1d85-160">示例 1 请求 URI：[https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="e1d85-160">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="e1d85-p113">此 URI 返回每个 Office 365 服务实例的最新版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
<span data-ttu-id="e1d85-p114">这些 URI 中 ClientRequestID 参数的 GUID 只是个例子。若要试用 Web 服务 URI，请生成你自己的 GUID。这项 Web 服务将来可能会屏蔽这些示例中的 GUID。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="e1d85-166">示例 2 请求 URI：[https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="e1d85-166">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="e1d85-p115">此 URI 返回指定 Office 365 服务实例的最新版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

<span data-ttu-id="e1d85-169">示例 3 请求 URI：[https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="e1d85-169">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="e1d85-p116">此 URI 显示 CSV 格式输出。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="e1d85-172">示例 4 请求 URI：[https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="e1d85-172">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="e1d85-p117">此 URI 显示 Office 365 全球服务实例的所有已发布旧版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="e1d85-175">示例 5 RSS 源 URI：[https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="e1d85-175">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="e1d85-p118">此 URI 显示已发布版本的 RSS 源，其中包含指向每个版本的变更列表的链接。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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

## <a name="endpoints-web-method"></a><span data-ttu-id="e1d85-178">**终结点 Web 方法**</span><span class="sxs-lookup"><span data-stu-id="e1d85-178">**Endpoints web method**</span></span>

<span data-ttu-id="e1d85-p119">终结点 Web 方法返回组成 Office 365 服务的 IP 地址范围和 URL 的所有记录。虽然来自终结点 Web 方法的最新数据应用于网络设备配置，但由于有附加事先通知，数据在发布后最多可缓存 30 天。终结点 Web 方法需要使用以下参数：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p119">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions. Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="e1d85-p120">**ServiceAreas** - 查询字符串参数。此参数指定服务区域的逗号分隔列表。有效项为 Common、Exchange、SharePoint 和 Skype。因为 Common 服务区域项是其他所有服务区域的先决条件，所以 Web 服务始终包含此项。如果你不添加此参数，将返回所有服务区域。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p120">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="e1d85-p121">**TenantName** - 查询字符串参数。此参数指定 Office 365 租户名称。这项 Web 服务获取你提供的名称，并将它插入包含租户名称的 URL 部分中。如果你未提供租户名称，这些 URL 部分包含的是通配符 (\*)。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p121">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="e1d85-p122">**NoIPv6** - 查询字符串参数。将此属性设置为 true，可从输出中排除 IPv6 地址（例如，你在网络中没有使用 IPv6 的话）。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p122">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="e1d85-p123">**Instance** - 路由参数。此必需参数指定要返回哪个实例的终结点。有效实例为 Worldwide、China、Germany、USGovDoD 和 USGovGCCHigh。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p123">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="e1d85-p124">终结点 Web 方法的结果是一组记录，每条记录均代表一个终结点集。每条记录均包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p124">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="e1d85-198">id - 终结点集的不可变 ID 号。</span><span class="sxs-lookup"><span data-stu-id="e1d85-198">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="e1d85-199">serviceArea - 所属的服务区域，有效项为 Common、Exchange、SharePoint 或 Skype。</span><span class="sxs-lookup"><span data-stu-id="e1d85-199">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="e1d85-p125">urls - 终结点集的 URL。此为包含 DNS 记录的 JSON 数组。若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p125">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="e1d85-p126">tcpPorts - 终结点集的 TCP 端口。所有端口元素都格式化为端口的逗号分隔列表，或用短划线字符 (-) 分隔的端口范围。端口适用于相应类别的特定终结点集中的所有 IP 地址和所有 URL。若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p126">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="e1d85-p127">udpPorts - 此终结点集中 IP 地址范围的 UDP 端口。若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p127">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="e1d85-p128">ips - 与此终结点关联的 IP 地址范围，设置为与列出的 TCP 或 UDP 端口关联。IP 地址范围的 JSON 数组。若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p128">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="e1d85-p129">category - 端点集的连接类别。有效值为 Optimize、Allow 和 Default。如果使用端点数据搜索某个类别的 IP 地址或 URL，查询可能会返回多个类别。出现这种情况的原因有多种。此时，你应该遵循针对最高优先级类别的建议。例如，如果既有 Optimize 类别又有 Allow 类别的端点，则应遵循针对 Optimize 的要求。必须提供。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p129">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span> 
- <span data-ttu-id="e1d85-219">expressRoute - True 或 False，表示此终结点集是否通过 ExpressRoute 进行路由。</span><span class="sxs-lookup"><span data-stu-id="e1d85-219">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="e1d85-p130">required - 如果此终结点集必须有连接才能支持 Office 365，则为 True。如果此终结点集是可选的，则为 false。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p130">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="e1d85-p131">notes - 对于可选终结点，此文本描述了无法在网络层访问此终结点集中 IP 地址或 URL 的情况下缺少的 Office 365 功能。若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p131">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="e1d85-224">示例：</span><span class="sxs-lookup"><span data-stu-id="e1d85-224">Examples:</span></span>

<span data-ttu-id="e1d85-225">示例 1 请求 URI：[https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="e1d85-225">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="e1d85-p132">此 URI 对全部工作负载获取 Office 365 全球实例的所有终结点。示例结果的输出摘录如下：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p132">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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

<span data-ttu-id="e1d85-228">此示例中不包含其他终结点集。</span><span class="sxs-lookup"><span data-stu-id="e1d85-228">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="e1d85-229">示例 2 请求 URI：[https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="e1d85-229">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="e1d85-230">此示例仅对 Exchange Online 和依赖项获取 Office 365 全球实例的终结点。</span><span class="sxs-lookup"><span data-stu-id="e1d85-230">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="e1d85-231">示例 2 的输出类似于示例 1，不同之处在于结果不包括 SharePoint Online 或 Skype for Business Online 终结点。</span><span class="sxs-lookup"><span data-stu-id="e1d85-231">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="e1d85-232">变更 Web 方法</span><span class="sxs-lookup"><span data-stu-id="e1d85-232">Changes web method</span></span>

<span data-ttu-id="e1d85-p133">变更 Web 方法返回已发布的最新更新。这通常是上月的 IP 地址范围和 URL 变更。要处理的最关键变更是添加新 URL 或 IP 地址，因为如果无法将 IP 地址添加到防火墙访问控制列表，或无法将 URL 添加到代理服务器跳过列表，可能会导致相应网络设备后的 Office 365 用户遇到服务中断。尽管有运营要求，但 _Add_ 操作会在添加前提前 30 天发出通知，以免发生此类服务中断。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p133">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="e1d85-237">变更 Web 方法需要使用以下参数：</span><span class="sxs-lookup"><span data-stu-id="e1d85-237">The parameter for the changes web method is:</span></span>

- <span data-ttu-id="e1d85-p134">**Version** - 必需的 URL 路由参数。此参数指定当前实现的版本，且要查看自这一版本起的变更。格式是 _YYYYMMDDNN_。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p134">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is _YYYYMMDDNN_.</span></span>

<span data-ttu-id="e1d85-p135">变更 Web 方法的结果是一组记录，每条记录均代表特定版本终结点中的变更。每条记录均包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p135">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="e1d85-243">id - 变更记录的不可变 ID。</span><span class="sxs-lookup"><span data-stu-id="e1d85-243">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="e1d85-p136">endpointSetId - 变更的终结点集记录的 ID。此为必需元素。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p136">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
- <span data-ttu-id="e1d85-p137">disposition - 此元素可以是两种变更之一（add 或 remove），描述了终结点集记录有何变更。此为必需元素。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p137">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record. Required.</span></span>
- <span data-ttu-id="e1d85-p138">version - 引入变更的已发布终结点集的版本。版本号格式为 _YYYYMMDDNN_，其中 NN 是必须在一天内发布多个版本时递增的自然数。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p138">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="e1d85-p139">previous - 详细说明终结点集中已变更元素的旧值的子结构。对于新添加的终结点集，不包含此元素。此元素包括 tcpPorts、udpPorts、ExpressRoute、category、required 和 notes。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p139">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="e1d85-p140">current - 详细说明终结点集中已变更元素的更新值的子结构。此元素包括 tcpPorts、udpPorts、ExpressRoute、category、required 和 notes。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p140">current - A substructure detailing updated values of changes elements on the endpoint set. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="e1d85-p141">add - 详细说明要添加到终结点集集合的项的子结构。如果没有要添加的项，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p141">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="e1d85-257">effectiveDate - 定义添加项在服务中的生效日期。</span><span class="sxs-lookup"><span data-stu-id="e1d85-257">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="e1d85-258">ips - 要添加到 ips 数组的项。</span><span class="sxs-lookup"><span data-stu-id="e1d85-258">ips - Items to be added to the ips array.</span></span>
  - <span data-ttu-id="e1d85-259">urls - 要添加到 urls 数组的项。</span><span class="sxs-lookup"><span data-stu-id="e1d85-259">urls- Items to be added to the urls array.</span></span>
- <span data-ttu-id="e1d85-p142">remove - 详细说明要从终结点集中删除的项的子结构。如果没有要删除的项，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p142">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
  - <span data-ttu-id="e1d85-262">ips - 要从 ips 数组中删除的项。</span><span class="sxs-lookup"><span data-stu-id="e1d85-262">ips - Items to be removed from the ips array.</span></span>
  - <span data-ttu-id="e1d85-263">urls - 要从 urls 数组中删除的项。</span><span class="sxs-lookup"><span data-stu-id="e1d85-263">urls- Items to be removed from the urls array.</span></span>

### <a name="examples"></a><span data-ttu-id="e1d85-264">**示例：**</span><span class="sxs-lookup"><span data-stu-id="e1d85-264">**Examples:**</span></span>

<span data-ttu-id="e1d85-265">示例 1 请求 URI：[https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="e1d85-265">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="e1d85-p143">这请求获取 Office 365 全球服务实例先前的所有变更。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p143">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="e1d85-268">示例 2 请求 URI：[https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="e1d85-268">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="e1d85-p144">这请求获取 Office 365 全球实例自指定版本起的变更。在此示例中，指定版本是最新版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p144">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="e1d85-272">**示例 PowerShell 脚本**</span><span class="sxs-lookup"><span data-stu-id="e1d85-272">**Example PowerShell Script**</span></span>

<span data-ttu-id="e1d85-p145">运行下面的 PowerShell 脚本，可确定是否需要对已更新数据执行操作。此脚本检查 Office 365 全球实例终结点的版本号。若有变更，它就会下载终结点，并筛选出 &quot;Allow&quot; 和 &quot;Optimize&quot; 类别终结点。它还会跨多个调用使用唯一 ClientRequestId，并将找到的最新版本保存到临时文件中。应每小时调用一次此脚本，以检查是否有版本更新。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p145">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the &quot;Allow&quot; and &quot;Optimize&quot; category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="e1d85-278">**示例 Python 脚本**</span><span class="sxs-lookup"><span data-stu-id="e1d85-278">**Example Python Script**</span></span>

<span data-ttu-id="e1d85-p146">运行下面的 Python 脚本（已使用 Windows 10 上的 Python 3.6.3 进行测试），可确定是否需要对已更新数据执行操作。此脚本检查 Office 365 全球实例终结点的版本号。若有变更，它就会下载终结点，并筛选出 _Allow_ 和 _Optimize_ 类别终结点。它还会跨多个调用使用唯一 ClientRequestId，并将找到的最新版本保存到临时文件中。应每小时调用一次此脚本，以检查是否有版本更新。</span><span class="sxs-lookup"><span data-stu-id="e1d85-p146">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="e1d85-284">**Web 服务接口版本控制**</span><span class="sxs-lookup"><span data-stu-id="e1d85-284">**Web Service interface versioning**</span></span>

<span data-ttu-id="e1d85-p147">日后可能需要更新这些 Web 服务方法的参数或结果。在这些 Web 服务的正式版本发布后，Microsoft 将做出合理的努力，以事先通知 Web 服务的实质性更新。如果认为更新必须变更使用 Web 服务的客户端，Microsoft 将在新版本发布后的至少十二 (12) 个月内保留旧版（上一版）Web 服务。在此期间未升级的客户可能无法访问 Web 服务及其方法。如果 Web 服务接口签名发生以下变更，客户必须确保 Web 服务的客户端能继续正常运行，而不出现错误：</span><span class="sxs-lookup"><span data-stu-id="e1d85-p147">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="e1d85-290">将新的可选参数添加到现有 Web 方法中，此参数既不必由旧客户端提供，也不会影响旧客户端收到的结果。</span><span class="sxs-lookup"><span data-stu-id="e1d85-290">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="e1d85-291">将响应 REST 项之一或其他列中的新命名特性添加到响应 CSV。</span><span class="sxs-lookup"><span data-stu-id="e1d85-291">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="e1d85-292">添加新 Web 方法，其使用旧客户端未调用的新名称。</span><span class="sxs-lookup"><span data-stu-id="e1d85-292">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="related-topics"></a><span data-ttu-id="e1d85-293">相关主题</span><span class="sxs-lookup"><span data-stu-id="e1d85-293">Related Topics</span></span>
  
[<span data-ttu-id="e1d85-294">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="e1d85-294">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="e1d85-295">Office 365 终结点 FAQ</span><span class="sxs-lookup"><span data-stu-id="e1d85-295">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="e1d85-296">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="e1d85-296">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="e1d85-297">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="e1d85-297">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="e1d85-298">与 Office 365 的网络连接</span><span class="sxs-lookup"><span data-stu-id="e1d85-298">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="e1d85-299">Skype for Business Online 中的媒体质量和网络连接性能</span><span class="sxs-lookup"><span data-stu-id="e1d85-299">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="e1d85-300">优化 Skype for Business Online 网络</span><span class="sxs-lookup"><span data-stu-id="e1d85-300">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="e1d85-301">使用基线和性能历史记录优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="e1d85-301">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="e1d85-302">Office 365 性能疑难解答计划</span><span class="sxs-lookup"><span data-stu-id="e1d85-302">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
