---
title: Office 365 IP 地址和 URL Web 服务
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/7/2019
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
ms.openlocfilehash: c87f297c6bc1fc4cf317db60d3fd2ef2e4b8443b
ms.sourcegitcommit: a35d23929bfbfd956ee853b5e828b36e2978bf36
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "33655786"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="6cc52-104">Office 365 IP 地址和 URL Web 服务</span><span class="sxs-lookup"><span data-stu-id="6cc52-104">Office 365 IP Address and URL Web service</span></span>

<span data-ttu-id="6cc52-p102">为了帮助你更好地标识和区分 Office 365 网络流量，我们推出了一项用于发布 Office 365 终结点的新 Web 服务，以方便你更轻松地评估、配置并掌握最新变更。这项新 Web 服务取代了目前可用的 XML 可下载文件。XML 格式计划将于 2018 年 10 月 2 日起逐步淘汰。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="6cc52-p103">作为客户或外围网络设备供应商，你可以构建基于 REST 的新 Web 服务，用于 Office 365 IP 地址和 FQDN 条目。可使用这些 URL 直接在 Web 浏览器中访问数据。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="6cc52-110">若要获取最新版 Office 365 URL 和 IP 地址范围，请使用 [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="6cc52-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="6cc52-111">若要获取防火墙和代理服务器的 Office 365 URL 和 IP 地址范围页面的相关数据，请使用 [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="6cc52-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="6cc52-112">若要获取自 2018 年 7 月底这项 Web 服务首次推出以来的所有最新变更，请使用 [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="6cc52-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="6cc52-113">作为客户，你可以使用这项 Web 服务：</span><span class="sxs-lookup"><span data-stu-id="6cc52-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="6cc52-114">将 PowerShell 脚本更新为获取 Office 365 终结点数据，并修改网络设备的任何格式。</span><span class="sxs-lookup"><span data-stu-id="6cc52-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="6cc52-115">根据此类信息更新已部署到客户端计算机的 PAC 文件。</span><span class="sxs-lookup"><span data-stu-id="6cc52-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="6cc52-116">作为网络外围设备供应商，你可以使用这项 Web 服务：</span><span class="sxs-lookup"><span data-stu-id="6cc52-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="6cc52-117">创建并测试设备软件，以下载自动配置列表。</span><span class="sxs-lookup"><span data-stu-id="6cc52-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="6cc52-118">检查当前版本。</span><span class="sxs-lookup"><span data-stu-id="6cc52-118">Check for the current version.</span></span>
- <span data-ttu-id="6cc52-119">获取最新变更。</span><span class="sxs-lookup"><span data-stu-id="6cc52-119">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="6cc52-120">如果正在使用 Azure ExpressRoute 连接到 Office 365，请查看[适用于 Office 365 的 Azure ExpressRoute](https://docs.microsoft.com/office365/enterprise/azure-expressroute) 以熟悉 Azure expressroute 支持的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="6cc52-120">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="6cc52-121">另请查看 [Office 365 URL 和 IP 地址范围](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)，以了解 Office 365 应用程序的哪些网络请求需要 Internet 连接。</span><span class="sxs-lookup"><span data-stu-id="6cc52-121">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="6cc52-122">这有助于更好地配置外围安全设备。</span><span class="sxs-lookup"><span data-stu-id="6cc52-122">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="6cc52-123">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="6cc52-123">For additional information, see:</span></span>

- [<span data-ttu-id="6cc52-124">Office 365 技术社区论坛中的“公告”博客文章</span><span class="sxs-lookup"><span data-stu-id="6cc52-124">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="6cc52-125">Office 365 技术社区论坛中有关如何使用 Web 服务的提问</span><span class="sxs-lookup"><span data-stu-id="6cc52-125">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="6cc52-126">通用参数</span><span class="sxs-lookup"><span data-stu-id="6cc52-126">Common parameters</span></span>

<span data-ttu-id="6cc52-127">下面两个参数是所有 Web 服务方法的通用参数：</span><span class="sxs-lookup"><span data-stu-id="6cc52-127">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="6cc52-128">**format=<JSON | CSV>** - 默认情况下，返回数据的格式为 JSON。</span><span class="sxs-lookup"><span data-stu-id="6cc52-128">**format=<JSON | CSV>** - By default, the returned data format is JSON.</span></span> <span data-ttu-id="6cc52-129">使用此可选参数返回采用逗号分隔值 (CSV) 格式的数据。</span><span class="sxs-lookup"><span data-stu-id="6cc52-129">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="6cc52-130">**ClientRequestId=\<guid>** - 为客户端关联生成的所需 GUID。</span><span class="sxs-lookup"><span data-stu-id="6cc52-130">**ClientRequestId=\<guid>** - A required GUID that you generate for client association.</span></span> <span data-ttu-id="6cc52-131">应为每台调用 Web 服务的计算机生成一个 GUID。</span><span class="sxs-lookup"><span data-stu-id="6cc52-131">You should generate a GUID for each machine that calls the web service.</span></span> <span data-ttu-id="6cc52-132">请勿使用以下示例中所示的 GUID，因为它们将来可能会被 Web 服务阻止。</span><span class="sxs-lookup"><span data-stu-id="6cc52-132">Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future.</span></span> <span data-ttu-id="6cc52-133">GUID 格式为 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_，其中 x 表示一个十六进制数字。</span><span class="sxs-lookup"><span data-stu-id="6cc52-133">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span> <span data-ttu-id="6cc52-134">若要生成 GUID，请使用 [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="6cc52-134">To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="6cc52-135">版本 Web 方法</span><span class="sxs-lookup"><span data-stu-id="6cc52-135">Version web method</span></span>

<span data-ttu-id="6cc52-p107">Microsoft 在每月底更新 Office 365 IP 地址和 FQDN 条目，有时也会因运营或支持要求而不定期更新。每个已发布实例的数据都分配有版本号。借助版本 Web 方法，可以轮询每个 Office 365 服务实例的最新版本。建议每天或至多每小时检查一次版本。新版本应在每月初生成。有时，鉴于支持事件、安全性或其他运营要求，新版本还会在每月其他时间生成。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p107">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="6cc52-142">版本 Web 服务的参数如下：</span><span class="sxs-lookup"><span data-stu-id="6cc52-142">Parameters for the version web method are:</span></span>

- <span data-ttu-id="6cc52-143">**AllVersions=<true | false>** - 默认情况下，返回的版本为最新的。</span><span class="sxs-lookup"><span data-stu-id="6cc52-143">**AllVersions=<true | false>** - By default, the version returned is the latest.</span></span> <span data-ttu-id="6cc52-144">包括此可选参数，以请求首次发布 Web 服务之后的所有已发布版本。</span><span class="sxs-lookup"><span data-stu-id="6cc52-144">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="6cc52-145">**Format=<JSON | CSV | RSS>** – 除了 JSON 和 CSV 格式，版本 Web 服务还支持 RSS。</span><span class="sxs-lookup"><span data-stu-id="6cc52-145">**Format=<JSON | CSV | RSS>** – In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="6cc52-146">可以结合使用此可选参数及 _AllVersions=true_ 参数，以请求可用于 Outlook 或其他 RSS 读取器的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="6cc52-146">You can use this optional parameter along with the _AllVersions=true_ parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="6cc52-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - 此可选参数用于指定返回其版本的实例。</span><span class="sxs-lookup"><span data-stu-id="6cc52-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="6cc52-148">如果圣罗，则会返回所有实例。</span><span class="sxs-lookup"><span data-stu-id="6cc52-148">If omitted, all instances are returned.</span></span> <span data-ttu-id="6cc52-149">有效实例包括：Worldwide、China、Germany、USGovDoD、USGovGCCHigh。</span><span class="sxs-lookup"><span data-stu-id="6cc52-149">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="6cc52-p111">版本 Web 方法不受速率限制，并且不会返回 429 HTTP 响应代码。版本 Web 方法的响应确实包括，建议将数据缓存 1 小时的缓存控制标头。版本 Web 方法的结果可以是一条记录，也可以是一组记录。每条记录都由以下元素构成：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p111">The version web method is not rate limited and does not ever return 429 HTTP Response Codes. The response to the version web method does include a cache-control header recommending caching of the data for 1 hour. The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="6cc52-154">instance - Office 365 服务实例的短名称。</span><span class="sxs-lookup"><span data-stu-id="6cc52-154">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="6cc52-155">latest - 指定实例的终结点的最新版本。</span><span class="sxs-lookup"><span data-stu-id="6cc52-155">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="6cc52-p112">versions - 指定实例的所有旧版本列表。仅当 AllVersions 参数为 true 时，才包含此元素。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p112">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="6cc52-p113">可以使用 Microsoft Flow 来获取对 IP 地址和 URL 所做的更改的电子邮件通知。请参阅[使用 Microsoft Flow 接收对 Office 365 IP 地址和 URL 所做的更改的电子邮件](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p113">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="6cc52-160">示例：</span><span class="sxs-lookup"><span data-stu-id="6cc52-160">Examples:</span></span>

<span data-ttu-id="6cc52-161">示例 1 请求 URI：[https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="6cc52-161">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="6cc52-p114">此 URI 返回每个 Office 365 服务实例的最新版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p114">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
> <span data-ttu-id="6cc52-p115">这些 URI 中 ClientRequestID 参数的 GUID 只是个例子。若要试用 Web 服务 URI，请生成你自己的 GUID。这项 Web 服务将来可能会屏蔽这些示例中的 GUID。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p115">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="6cc52-167">示例 2 请求 URI：[https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="6cc52-167">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="6cc52-p116">此 URI 返回指定 Office 365 服务实例的最新版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p116">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="6cc52-170">示例 3 请求 URI：[https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="6cc52-170">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="6cc52-p117">此 URI 显示 CSV 格式输出。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p117">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="6cc52-173">示例 4 请求 URI：[https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="6cc52-173">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="6cc52-p118">此 URI 显示 Office 365 全球服务实例的所有已发布旧版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p118">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="6cc52-176">示例 5 RSS 源 URI：[https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="6cc52-176">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="6cc52-p119">此 URI 显示已发布版本的 RSS 源，其中包含指向每个版本的变更列表的链接。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p119">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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
```

## <a name="endpoints-web-method"></a><span data-ttu-id="6cc52-179">终结点 Web 方法</span><span class="sxs-lookup"><span data-stu-id="6cc52-179">Endpoints web method</span></span>

<span data-ttu-id="6cc52-180">终结点 Web 方法可返回组成 Office 365 服务的 IP 地址范围和 URL 的所有记录。</span><span class="sxs-lookup"><span data-stu-id="6cc52-180">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="6cc52-181">尽管应使用最新的终结点 Web 方法数据来进行网络设备配置，但得益于添加功能中所提供的提前通知，数据在发布之后可以缓存长达 30 天。</span><span class="sxs-lookup"><span data-stu-id="6cc52-181">While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions.</span></span> <span data-ttu-id="6cc52-182">建议你仅在版本 Web 方法表示存在新的数据版本时才再次调用终结点 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="6cc52-182">We recommend you only call the endpoints web method again when the version web method indicates a new version of the data is available.</span></span>

<span data-ttu-id="6cc52-183">终结点 Web 方法的参数如下：</span><span class="sxs-lookup"><span data-stu-id="6cc52-183">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="6cc52-184">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - 以逗号分隔的服务区域列表。</span><span class="sxs-lookup"><span data-stu-id="6cc52-184">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - A comma-separated list of service areas.</span></span> <span data-ttu-id="6cc52-185">有效项为 _Common_、_Exchange_、_SharePoint_ 和 _Skype_。</span><span class="sxs-lookup"><span data-stu-id="6cc52-185">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="6cc52-186">Common 服务区域项为所有其他服务区域的先决条件，但是 Web fuwu 始终包括它们。</span><span class="sxs-lookup"><span data-stu-id="6cc52-186">Because Common service area items are a prerequisite for all other service areas, the web service will always include them.</span></span> <span data-ttu-id="6cc52-187">如果不包括此参数，则会返回所有服务区域。</span><span class="sxs-lookup"><span data-stu-id="6cc52-187">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="6cc52-188">**TenantName=<tenant_name>** - 你的 Office 365 租户名称。</span><span class="sxs-lookup"><span data-stu-id="6cc52-188">**TenantName=<tenant_name>** - Your Office 365 tenant name.</span></span> <span data-ttu-id="6cc52-189">Web 服务采用所提供的名称，并将其插入到包含租户名称的 URL 中。</span><span class="sxs-lookup"><span data-stu-id="6cc52-189">The web service takes your provided name and inserts it in parts of URLs that include the tenant name.</span></span> <span data-ttu-id="6cc52-190">如果未提供租户名称，则这些 URL 的部分具有通配符字符 (\*)。</span><span class="sxs-lookup"><span data-stu-id="6cc52-190">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="6cc52-191">**NoIPv6=<true | false>** - 将此属性设置为 true，可从输出中排除 IPv6 地址，例如，你在网络中没有使用 IPv6 的话。</span><span class="sxs-lookup"><span data-stu-id="6cc52-191">**NoIPv6=<true | false>** - Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="6cc52-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - 此必填参数用于指定返回其终结点的实例。</span><span class="sxs-lookup"><span data-stu-id="6cc52-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This required parameter specifies the instance to return the endpoints for.</span></span> <span data-ttu-id="6cc52-193">有效实例包括：_Worldwide_、_China_、_Germany_、_USGovDoD_ 和 _USGovGCCHigh_。</span><span class="sxs-lookup"><span data-stu-id="6cc52-193">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="6cc52-194">如果多次从相同客户端 IP 地址调用终结点 Web 方法，则可能会收到 HTTP 响应代码 429（请求过多）。</span><span class="sxs-lookup"><span data-stu-id="6cc52-194">If you call the endpoints web method a large number of times from the same client IP address, you may receive HTTP response code 429 (Too Many Requests).</span></span> <span data-ttu-id="6cc52-195">大部分用户不会看到此代码。</span><span class="sxs-lookup"><span data-stu-id="6cc52-195">Most people will never see this.</span></span> <span data-ttu-id="6cc52-196">如果收到此响应代码，请先等待 1 小时，然后再重复你的请求。</span><span class="sxs-lookup"><span data-stu-id="6cc52-196">If you get this response code, wait 1 hour before repeating your request.</span></span> <span data-ttu-id="6cc52-197">计划仅在版本 Web 方法表示存在新的可用版本时才调用终结点 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="6cc52-197">Plan to only call the endpoints web method when the version web method indicates there is a new version available.</span></span>

<span data-ttu-id="6cc52-p125">终结点 Web 方法的结果是一组记录，每条记录均代表一个终结点集。每条记录均包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p125">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="6cc52-200">id - 终结点集的不可变 ID 号。</span><span class="sxs-lookup"><span data-stu-id="6cc52-200">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="6cc52-201">serviceArea - 所属的服务区域，有效项为 Common、Exchange、SharePoint 或 Skype。</span><span class="sxs-lookup"><span data-stu-id="6cc52-201">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="6cc52-p126">urls - 终结点集的 URL。此为包含 DNS 记录的 JSON 数组。若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p126">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="6cc52-p127">tcpPorts - 终结点集的 TCP 端口。所有端口元素都格式化为端口的逗号分隔列表，或用短划线字符 (-) 分隔的端口范围。端口适用于相应类别的特定终结点集中的所有 IP 地址和所有 URL。若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p127">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="6cc52-p128">udpPorts - 此终结点集中 IP 地址范围的 UDP 端口。若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p128">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="6cc52-p129">ips - 与此终结点关联的 IP 地址范围，设置为与列出的 TCP 或 UDP 端口关联。IP 地址范围的 JSON 数组。若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p129">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="6cc52-p130">category - 端点集的连接类别。有效值为 Optimize、Allow 和 Default。如果使用端点数据搜索某个类别的 IP 地址或 URL，查询可能会返回多个类别。出现这种情况的原因有多种。此时，你应该遵循针对最高优先级类别的建议。例如，如果既有 Optimize 类别又有 Allow 类别的端点，则应遵循针对 Optimize 的要求。必须提供。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p130">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span>
- <span data-ttu-id="6cc52-221">expressRoute - True 或 False，表示此终结点集是否通过 ExpressRoute 进行路由。</span><span class="sxs-lookup"><span data-stu-id="6cc52-221">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="6cc52-p131">required - 如果此终结点集必须有连接才能支持 Office 365，则为 True。如果此终结点集是可选的，则为 false。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p131">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="6cc52-p132">notes - 对于可选终结点，此文本描述了无法在网络层访问此终结点集中 IP 地址或 URL 的情况下缺少的 Office 365 功能。若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p132">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="6cc52-226">示例：</span><span class="sxs-lookup"><span data-stu-id="6cc52-226">Examples:</span></span>

<span data-ttu-id="6cc52-227">示例 1 请求 URI：[https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="6cc52-227">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="6cc52-p133">此 URI 对全部工作负载获取 Office 365 全球实例的所有终结点。示例结果的输出摘录如下：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p133">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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

<span data-ttu-id="6cc52-230">此示例中不包含其他终结点集。</span><span class="sxs-lookup"><span data-stu-id="6cc52-230">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="6cc52-231">示例 2 请求 URI：[https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="6cc52-231">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="6cc52-232">此示例仅对 Exchange Online 和依赖项获取 Office 365 全球实例的终结点。</span><span class="sxs-lookup"><span data-stu-id="6cc52-232">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="6cc52-233">示例 2 的输出类似于示例 1，不同之处在于结果不包括 SharePoint Online 或 Skype for Business Online 终结点。</span><span class="sxs-lookup"><span data-stu-id="6cc52-233">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="6cc52-234">变更 Web 方法</span><span class="sxs-lookup"><span data-stu-id="6cc52-234">Changes web method</span></span>

<span data-ttu-id="6cc52-p134">变更 Web 方法返回已发布的最新更新。这通常是上月的 IP 地址范围和 URL 变更。要处理的最关键变更是添加新 URL 或 IP 地址，因为如果无法将 IP 地址添加到防火墙访问控制列表，或无法将 URL 添加到代理服务器跳过列表，可能会导致相应网络设备后的 Office 365 用户遇到服务中断。尽管有运营要求，但 _Add_ 操作会在添加前提前 30 天发出通知，以免发生此类服务中断。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p134">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="6cc52-239">变更 Web 方法需要使用以下必填参数：</span><span class="sxs-lookup"><span data-stu-id="6cc52-239">The required parameter for the changes web method is:</span></span>

- <span data-ttu-id="6cc52-240">**Version=\<YYYYMMDDNN>** - 所需的 URL 路由参数。</span><span class="sxs-lookup"><span data-stu-id="6cc52-240">**Version=\<YYYYMMDDNN>** - Required URL route parameter.</span></span> <span data-ttu-id="6cc52-241">此值应为当前实施的版本。</span><span class="sxs-lookup"><span data-stu-id="6cc52-241">This value should be the version that you have currently implemented.</span></span> <span data-ttu-id="6cc52-242">Web 服务应返回自该版本之后发生的变更。</span><span class="sxs-lookup"><span data-stu-id="6cc52-242">The web service will return the changes since that version.</span></span> <span data-ttu-id="6cc52-243">格式为 _YYYYMMDDNN_；如果需要在一天内发布多个版本，则 _NN_ 是一个递增的自然数，而 _00_ 表示给定日期的第一个更新。</span><span class="sxs-lookup"><span data-stu-id="6cc52-243">The format is _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day, with _00_ representing the first update for a given day.</span></span> <span data-ttu-id="6cc52-244">Web 服务要求 _version_ 参数恰好包含 10 位数。</span><span class="sxs-lookup"><span data-stu-id="6cc52-244">The web service requires this parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="6cc52-245">变更 Web 方法受速率限制，与终结点 Web 方法受限于速率一样。</span><span class="sxs-lookup"><span data-stu-id="6cc52-245">The changes web method is rate limited in the same way as the endpoints web method.</span></span> <span data-ttu-id="6cc52-246">如果收到 429 HTTP 响应代码，请先等待 1 小时，然后再重复你的请求。</span><span class="sxs-lookup"><span data-stu-id="6cc52-246">If you receive a 429 HTTP response code, wait 1 hour before repeating your request.</span></span>

<span data-ttu-id="6cc52-p137">变更 Web 方法的结果是一组记录，每条记录均代表特定版本终结点中的变更。每条记录均包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p137">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="6cc52-249">id - 变更记录的不可变 ID。</span><span class="sxs-lookup"><span data-stu-id="6cc52-249">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="6cc52-250">endpointSetId - 变更的终结点集记录的 ID。</span><span class="sxs-lookup"><span data-stu-id="6cc52-250">endpointSetId - The ID of the endpoint set record that is changed.</span></span>
- <span data-ttu-id="6cc52-251">disposition - 这可以是两种变更之一（add 或 remove），描述了终结点集记录有何变更。</span><span class="sxs-lookup"><span data-stu-id="6cc52-251">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record.</span></span>
- <span data-ttu-id="6cc52-p138">impact - 并非所有变更都对每个环境同样重要。此元素说明了相应更改对企业网络外围环境的预期影响。此属性仅包含在版本 **2018112800** 及更高版本的变更记录中。impact 选项包括：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p138">impact - Not all changes will be equally important to every environment. This describes the expected impact to an enterprise network perimeter environment as a result of this change. This attribute is included only in change records of version 2018112800 and later. Options for the impact are:</span></span>
  - <span data-ttu-id="6cc52-p139">AddedIp - IP 地址已添加到 Office 365，且很快就会对服务生效。这表示需要更改防火墙或其他第 3 层网络外围设备。如果你并没有在我们开始使用此元素之前添加它，可能会遇到故障。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p139">AddedIp – An IP Address was added to Office 365 and will be live on the service soon. This represents a change you need to take on a firewall or other layer 3 network perimeter device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="6cc52-259">AddedUrl – URL 已添加到 Office 365，且很快就会对服务生效。</span><span class="sxs-lookup"><span data-stu-id="6cc52-259">AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="6cc52-260">这表示需要更改代理服务器或 URL 分析网络外围设备。</span><span class="sxs-lookup"><span data-stu-id="6cc52-260">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="6cc52-261">如果你并没有在我们开始使用此元素之前添加它，可能会遇到故障。</span><span class="sxs-lookup"><span data-stu-id="6cc52-261">If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="6cc52-p141">AddedIpAndUrl - IP 地址和 URL 均已添加。这表示需要更改防火墙第 3 层设备、代理服务器或 URL 分析设备。如果你并没有在我们开始使用此元素之前添加它，可能会遇到故障。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p141">AddedIpAndUrl - Both an IP Address and a URL were added. This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="6cc52-p142">RemovedIpOrUrl - 从 Office 365 中至少删除了一个 IP 地址或 URL。应从外围设备中删除网络终结点，但此操作并无截止时间。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p142">RemovedIpOrUrl – At least one IP Address or URL was removed from Office 365. You should remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  - <span data-ttu-id="6cc52-p143">ChangedIsExpressRoute - ExpressRoute 支持属性已更改。如果使用 ExpressRoute，可能需要采取措施，具体视配置而定。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p143">ChangedIsExpressRoute – The ExpressRoute support attribute was changed. If you use ExpressRoute then you may need to take action depending on your configuration.</span></span>
  - <span data-ttu-id="6cc52-p144">MovedIpOrUrl - 在此终结点集和另一个终结点集之间迁移了 IP 地址或 URL。通常无需采取任何措施。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p144">MovedIpOrUrl – We moved an IP Address or Url between this endpoint set and another one. Generally no action is required.</span></span>
  - <span data-ttu-id="6cc52-p145">RemovedDuplicateIpOrUrl - 删除了重复的 IP 地址或 URL，但它仍是对 Office 365 发布的。通常无需采取任何措施。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p145">RemovedDuplicateIpOrUrl – We removed a duplicate IP Address or Url but it’s still published for Office 365. Generally no action is required.</span></span>
  - <span data-ttu-id="6cc52-273">OtherNonPriorityChanges - 更改了一些不如其他所有选项（如注释字段）重要的某内容</span><span class="sxs-lookup"><span data-stu-id="6cc52-273">OtherNonPriorityChanges – We changed something less critical than all of the other options like a note field</span></span>
- <span data-ttu-id="6cc52-p146">version - 引入变更的已发布终结点集的版本。版本号格式为 _YYYYMMDDNN_，其中 NN 是必须在一天内发布多个版本时递增的自然数。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p146">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="6cc52-276">previous - 详细说明终结点集上的旧变更元素值的子结构。</span><span class="sxs-lookup"><span data-stu-id="6cc52-276">previous - A substructure detailing previous values of changed elements on the endpoint set.</span></span> <span data-ttu-id="6cc52-277">对于新添加的终结点集，它们未包含在内。</span><span class="sxs-lookup"><span data-stu-id="6cc52-277">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="6cc52-278">包括 _ExpressRoute_、_serviceArea_、_category_、_required_、_tcpPorts_、_udpPorts_ 和 _notes_。</span><span class="sxs-lookup"><span data-stu-id="6cc52-278">Includes  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="6cc52-279">current - 详细说明终结点集上的更新变更元素值的子结构。</span><span class="sxs-lookup"><span data-stu-id="6cc52-279">current - A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="6cc52-280">包括 _ExpressRoute_、_serviceArea_、_category_、_required_、_tcpPorts_、_udpPorts_ 和 _notes_。</span><span class="sxs-lookup"><span data-stu-id="6cc52-280">Includes _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="6cc52-p149">add - 详细说明要添加到终结点集集合的项的子结构。如果没有要添加的项，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p149">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="6cc52-283">effectiveDate - 定义添加项在服务中的生效日期。</span><span class="sxs-lookup"><span data-stu-id="6cc52-283">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="6cc52-284">ips - 要添加到 _ips_ 数组的项。</span><span class="sxs-lookup"><span data-stu-id="6cc52-284">ips - Items to be added to the _ips_ array.</span></span>
  - <span data-ttu-id="6cc52-285">urls - 要添加到 _urls_ 数组的项。</span><span class="sxs-lookup"><span data-stu-id="6cc52-285">urls- Items to be added to the _urls_ array.</span></span>
- <span data-ttu-id="6cc52-286">remove - 详细说明要从终结点集中删除的项的子结构。</span><span class="sxs-lookup"><span data-stu-id="6cc52-286">remove - A substructure detailing items to be removed from the endpoint set.</span></span> <span data-ttu-id="6cc52-287">如果没有删除项，则省略。</span><span class="sxs-lookup"><span data-stu-id="6cc52-287">Omitted if there are no removals.</span></span>
  - <span data-ttu-id="6cc52-288">ips - 要从 _ips_ 数组中删除的项。</span><span class="sxs-lookup"><span data-stu-id="6cc52-288">ips - Items to be removed from the _ips_ array.</span></span>
  - <span data-ttu-id="6cc52-289">urls - 要从 _urls_ 数组中删除的项。</span><span class="sxs-lookup"><span data-stu-id="6cc52-289">urls- Items to be removed from the _urls_ array.</span></span>

### <a name="examples"></a><span data-ttu-id="6cc52-290">示例：</span><span class="sxs-lookup"><span data-stu-id="6cc52-290">Examples:</span></span>

<span data-ttu-id="6cc52-291">示例 1 请求 URI：[https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="6cc52-291">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="6cc52-p151">这请求获取 Office 365 全球服务实例先前的所有变更。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p151">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="6cc52-294">示例 2 请求 URI：[https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="6cc52-294">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="6cc52-p152">这请求获取 Office 365 全球实例自指定版本起的变更。在此示例中，指定版本是最新版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p152">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="6cc52-298">示例 PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="6cc52-298">Example PowerShell Script</span></span>

<span data-ttu-id="6cc52-299">你可以通过运行以下 PowerShell 脚本来查看是否需要为更新的数据采取操作。</span><span class="sxs-lookup"><span data-stu-id="6cc52-299">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="6cc52-300">此脚本将检查 Office 365 全球实例终结点的版本号。</span><span class="sxs-lookup"><span data-stu-id="6cc52-300">This script checks the version number for the Office 365 Worldwide instance endpoints.</span></span> <span data-ttu-id="6cc52-301">存在变更时，它将会下载终结点并筛选出“允许”和“优化”类别终结点。</span><span class="sxs-lookup"><span data-stu-id="6cc52-301">When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints.</span></span> <span data-ttu-id="6cc52-302">它还在多个调用中使用唯一的 _ClientRequestId_，并保存临时文件中出现的最新版本。</span><span class="sxs-lookup"><span data-stu-id="6cc52-302">It also uses a unique _ClientRequestId_ across multiple calls and saves the latest version found in a temporary file.</span></span> <span data-ttu-id="6cc52-303">应一小时调用一次此脚本，以检查是否存在版本更新。</span><span class="sxs-lookup"><span data-stu-id="6cc52-303">You should call this script once an hour to check for a version update.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="6cc52-304">示例 Python 脚本</span><span class="sxs-lookup"><span data-stu-id="6cc52-304">Example Python Script</span></span>

<span data-ttu-id="6cc52-p154">运行下面的 Python 脚本（已使用 Windows 10 上的 Python 3.6.3 进行测试），可确定是否需要对已更新数据执行操作。此脚本检查 Office 365 全球实例终结点的版本号。若有变更，它就会下载终结点，并筛选出 _Allow_ 和 _Optimize_ 类别终结点。它还会跨多个调用使用唯一 ClientRequestId，并将找到的最新版本保存到临时文件中。应每小时调用一次此脚本，以检查是否有版本更新。</span><span class="sxs-lookup"><span data-stu-id="6cc52-p154">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="6cc52-310">Web 服务接口版本控制</span><span class="sxs-lookup"><span data-stu-id="6cc52-310">Web Service interface versioning</span></span>

<span data-ttu-id="6cc52-p155">日后可能需要更新这些 Web 服务方法的参数或结果。在这些 Web 服务的正式版本发布后，Microsoft 将做出合理的努力，以事先通知 Web 服务的实质性更新。如果认为更新必须变更使用 Web 服务的客户端，Microsoft 将在新版本发布后的至少十二 (12) 个月内保留旧版（上一版）Web 服务。在此期间未升级的客户可能无法访问 Web 服务及其方法。如果 Web 服务接口签名发生以下变更，客户必须确保 Web 服务的客户端能继续正常运行，而不出现错误：</span><span class="sxs-lookup"><span data-stu-id="6cc52-p155">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="6cc52-316">将新的可选参数添加到现有 Web 方法中，此参数既不必由旧客户端提供，也不会影响旧客户端收到的结果。</span><span class="sxs-lookup"><span data-stu-id="6cc52-316">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="6cc52-317">将响应 REST 项之一或其他列中的新命名特性添加到响应 CSV。</span><span class="sxs-lookup"><span data-stu-id="6cc52-317">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="6cc52-318">添加新 Web 方法，其使用旧客户端未调用的新名称。</span><span class="sxs-lookup"><span data-stu-id="6cc52-318">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="office-365-endpoint-functions-module"></a><span data-ttu-id="6cc52-319">Office 365 终结点功能模块</span><span class="sxs-lookup"><span data-stu-id="6cc52-319">Office 365 Endpoint Functions Module</span></span>

<span data-ttu-id="6cc52-320">Microsoft 托管 REST 服务以获取最新的 Office 365 服务的 URL。</span><span class="sxs-lookup"><span data-stu-id="6cc52-320">Microsoft is hosting a REST Service to get the newest and latest URI for the Office 365 services.</span></span>  <span data-ttu-id="6cc52-321">若要能够将 URL 用作集合，可以结合使用此方法及一些有用的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6cc52-321">To be able to use the URI as a collection, you can use this module with a few helpful cmdlets.</span></span>

### <a name="calling-the-rest-service"></a><span data-ttu-id="6cc52-322">调用 REST 服务</span><span class="sxs-lookup"><span data-stu-id="6cc52-322">Calling the REST service</span></span>

<span data-ttu-id="6cc52-323">若要使用此模块，只需将模块文件 [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) 复制到硬盘上的某个位置并使用此命令直接将其导入：</span><span class="sxs-lookup"><span data-stu-id="6cc52-323">To use this module, simply copy the module file [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) somewhere on your hard disk and import it directly with this command:</span></span>

```powershell
    Import-Module O365EndpointFunctions.psm1
```

<span data-ttu-id="6cc52-324">导入此模块之后，你将能够调用 REST 服务。</span><span class="sxs-lookup"><span data-stu-id="6cc52-324">After you have imported the module, you will be able to call the REST service.</span></span> <span data-ttu-id="6cc52-325">这会将 URL 返回为集合，你可以在 PowerShell 中直接进行处理。</span><span class="sxs-lookup"><span data-stu-id="6cc52-325">This will return the URI as a collection that you can now process in PowerShell directly.</span></span> <span data-ttu-id="6cc52-326">必须输入 Office 365 租户的名称，如以下命令中所示：</span><span class="sxs-lookup"><span data-stu-id="6cc52-326">You must enter the name of your Office 365 tenant, as described in the following command:</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant]
```

#### <a name="parameters"></a><span data-ttu-id="6cc52-327">参数</span><span class="sxs-lookup"><span data-stu-id="6cc52-327">Parameters</span></span>

- <span data-ttu-id="6cc52-328">**tenantName** - Office 365 租户的名称。</span><span class="sxs-lookup"><span data-stu-id="6cc52-328">**tenantName** - The name of your Office 365 tenant.</span></span> <span data-ttu-id="6cc52-329">此参数为必填参数。</span><span class="sxs-lookup"><span data-stu-id="6cc52-329">This parameter is mandatory.</span></span>
- <span data-ttu-id="6cc52-330">**ForceLatest** - 此开关将强制 REST API 始终返回完整的最新 URL 列表。</span><span class="sxs-lookup"><span data-stu-id="6cc52-330">**ForceLatest** -This switch will force the REST API to always return the entire list of the latest URI.</span></span>
- <span data-ttu-id="6cc52-331">**IPv6** - 此开关也会返回 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="6cc52-331">**IPv6** -This switch will return the IPv6 addresses as well.</span></span> <span data-ttu-id="6cc52-332">默认情况下将仅返回 IPv4。</span><span class="sxs-lookup"><span data-stu-id="6cc52-332">As default only IPv4 will be returned.</span></span>

### <a name="examples"></a><span data-ttu-id="6cc52-333">示例</span><span class="sxs-lookup"><span data-stu-id="6cc52-333">Examples</span></span>

<span data-ttu-id="6cc52-334">返回使用 IPv6 地址的所有 URL 的完整列表</span><span class="sxs-lookup"><span data-stu-id="6cc52-334">Return the complete list of all URIs including the IPv6 addresses</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest -IPv6 | Format-Table -AutoSize
```

<span data-ttu-id="6cc52-335">仅返回 Exchange Online 服务的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="6cc52-335">Return only the IP addresses for Exchange Online Service</span></span>

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.serviceArea -eq "Exchange") -and ($_.protocol -eq "ip")}| Format-Table -AutoSize
```

### <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="6cc52-336">导出代理 PAC 文件</span><span class="sxs-lookup"><span data-stu-id="6cc52-336">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="6cc52-337">可以使用此模块创建代理 PAC 文件。</span><span class="sxs-lookup"><span data-stu-id="6cc52-337">You can use this module to create a Proxy PAC file.</span></span> <span data-ttu-id="6cc52-338">在此示例中，先获取终结点，然后筛选结果以选择 URL。</span><span class="sxs-lookup"><span data-stu-id="6cc52-338">In this example you first get the endpoints and filter the result to select the URLs.</span></span> <span data-ttu-id="6cc52-339">这些 URL 将进入要导入的管道。</span><span class="sxs-lookup"><span data-stu-id="6cc52-339">These URLs are piped to be exported.</span></span>  

```powershell
 Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.Protocol -eq "Url") -and (($_.Category -eq "Optimize") -or ($_.category -eq "Allow"))} | select uri -Unique | Export-O365ProxyPacFile
```

## <a name="related-topics"></a><span data-ttu-id="6cc52-340">相关主题</span><span class="sxs-lookup"><span data-stu-id="6cc52-340">Related Topics</span></span>
  
[<span data-ttu-id="6cc52-341">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="6cc52-341">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="6cc52-342">Office 365 终结点 FAQ</span><span class="sxs-lookup"><span data-stu-id="6cc52-342">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="6cc52-343">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="6cc52-343">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="6cc52-344">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="6cc52-344">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="6cc52-345">与 Office 365 的网络连接</span><span class="sxs-lookup"><span data-stu-id="6cc52-345">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="6cc52-346">Skype for Business Online 中的媒体质量和网络连接性能</span><span class="sxs-lookup"><span data-stu-id="6cc52-346">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="6cc52-347">优化 Skype for Business Online 网络</span><span class="sxs-lookup"><span data-stu-id="6cc52-347">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="6cc52-348">使用基线和性能历史记录优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="6cc52-348">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="6cc52-349">Office 365 性能疑难解答计划</span><span class="sxs-lookup"><span data-stu-id="6cc52-349">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
