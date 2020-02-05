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
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Office 365 IP 地址和 URL Web 服务可帮助你更好地识别和区分 Office 365 网络流量，以便更轻松地评估、配置和及时了解最新变更。
ms.openlocfilehash: 0a12b4dda9e4c931a34797aa2fc59803b97ddd36
ms.sourcegitcommit: 226989f5a6a252e67debf7613bf13aa679a43f92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "41721923"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="bda06-103">Office 365 IP 地址和 URL Web 服务</span><span class="sxs-lookup"><span data-stu-id="bda06-103">Office 365 IP Address and URL web service</span></span>

<span data-ttu-id="bda06-104">Office 365 IP 地址和 URL Web 服务可帮助你更好地识别和区分 Office 365 网络流量，以便更轻松地评估、配置和及时了解最新变更。</span><span class="sxs-lookup"><span data-stu-id="bda06-104">The Office 365 IP Address and URL web service helps you better identify and differentiate Office 365 network traffic, making it easier for you to evaluate, configure, and stay up to date with changes.</span></span> <span data-ttu-id="bda06-105">此基于 REST 的 Web 服务将取代自 2018 年 10 月 2 日开始逐步停止使用的旧版 XML 可下载文件。</span><span class="sxs-lookup"><span data-stu-id="bda06-105">This REST-based web service replaces the previous XML downloadable files, which were phased out on October 2, 2018.</span></span>

<span data-ttu-id="bda06-106">作为客户或网络外围设备供应商，你可以针对 Office 365 IP 地址和 FQDN 条目构建 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="bda06-106">As a customer or a network perimeter device vendor, you can build against the web service for Office 365 IP address and FQDN entries.</span></span> <span data-ttu-id="bda06-107">你可以使用以下 URL 直接访问 Web 浏览器中的数据：</span><span class="sxs-lookup"><span data-stu-id="bda06-107">You can access the data directly in a web browser using these URLs:</span></span>

- <span data-ttu-id="bda06-108">若要获取最新版 Office 365 URL 和 IP 地址范围，请使用 [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="bda06-108">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="bda06-109">若要获取防火墙和代理服务器的 Office 365 URL 和 IP 地址范围页面的相关数据，请使用 [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="bda06-109">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="bda06-110">若要获取自 2018 年 7 月这项 Web 服务首次推出以来的所有最新变更，请使用 [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="bda06-110">To get all the latest changes since July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="bda06-111">作为客户，你可以使用这项 Web 服务：</span><span class="sxs-lookup"><span data-stu-id="bda06-111">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="bda06-112">将 PowerShell 脚本更新为获取 Office 365 终结点数据，并修改网络设备的任何格式。</span><span class="sxs-lookup"><span data-stu-id="bda06-112">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="bda06-113">根据此类信息更新已部署到客户端计算机的 PAC 文件。</span><span class="sxs-lookup"><span data-stu-id="bda06-113">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="bda06-114">作为网络外围设备供应商，你可以使用这项 Web 服务：</span><span class="sxs-lookup"><span data-stu-id="bda06-114">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="bda06-115">创建并测试设备软件，以下载自动配置列表。</span><span class="sxs-lookup"><span data-stu-id="bda06-115">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="bda06-116">检查当前版本。</span><span class="sxs-lookup"><span data-stu-id="bda06-116">Check for the current version.</span></span>
- <span data-ttu-id="bda06-117">获取最新变更。</span><span class="sxs-lookup"><span data-stu-id="bda06-117">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="bda06-118">如果正在使用 Azure ExpressRoute 连接到 Office 365，请查看[适用于 Office 365 的 Azure ExpressRoute](https://docs.microsoft.com/office365/enterprise/azure-expressroute) 以熟悉 Azure expressroute 支持的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="bda06-118">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="bda06-119">另请查看 [Office 365 URL 和 IP 地址范围](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)，以了解 Office 365 应用程序的哪些网络请求需要 Internet 连接。</span><span class="sxs-lookup"><span data-stu-id="bda06-119">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="bda06-120">这有助于更好地配置外围安全设备。</span><span class="sxs-lookup"><span data-stu-id="bda06-120">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="bda06-121">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="bda06-121">For more information, see:</span></span>

- [<span data-ttu-id="bda06-122">Office 365 技术社区论坛中的“公告”博客文章</span><span class="sxs-lookup"><span data-stu-id="bda06-122">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="bda06-123">Office 365 技术社区论坛中有关如何使用 Web 服务的提问</span><span class="sxs-lookup"><span data-stu-id="bda06-123">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="bda06-124">通用参数</span><span class="sxs-lookup"><span data-stu-id="bda06-124">Common parameters</span></span>

<span data-ttu-id="bda06-125">下面两个参数是所有 Web 服务方法的通用参数：</span><span class="sxs-lookup"><span data-stu-id="bda06-125">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="bda06-126">**format=<JSON | CSV>** — 默认情况下，返回数据的格式为 JSON。</span><span class="sxs-lookup"><span data-stu-id="bda06-126">**format=<JSON | CSV>** — By default, the returned data format is JSON.</span></span> <span data-ttu-id="bda06-127">使用此可选参数返回采用逗号分隔值 (CSV) 格式的数据。</span><span class="sxs-lookup"><span data-stu-id="bda06-127">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="bda06-128">**ClientRequestId=\<guid>** — 为客户端关联生成的所需 GUID。</span><span class="sxs-lookup"><span data-stu-id="bda06-128">**ClientRequestId=\<guid>** — A required GUID that you generate for client association.</span></span> <span data-ttu-id="bda06-129">为调用 Web 服务的每台计算机生成唯一的 GUID（此页面上包含的脚本将为你生成 GUID）。</span><span class="sxs-lookup"><span data-stu-id="bda06-129">Generate a unique GUID for each machine that calls the web service (the scripts included on this page generate a GUID for you).</span></span> <span data-ttu-id="bda06-130">请勿使用以下示例中所示的 GUID，因为它们将来可能会被 Web 服务阻止。</span><span class="sxs-lookup"><span data-stu-id="bda06-130">Do not use the GUIDs shown in the following examples because they might be blocked by the web service in the future.</span></span> <span data-ttu-id="bda06-131">GUID 格式为 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_，其中 x 表示一个十六进制数字。</span><span class="sxs-lookup"><span data-stu-id="bda06-131">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span>

  <span data-ttu-id="bda06-132">若要生成 GUID，你可以使用 [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 命令，或使用[在线 GUID 生成器](https://www.guidgenerator.com/)等在线服务。</span><span class="sxs-lookup"><span data-stu-id="bda06-132">To generate a GUID, you can use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command, or use an online service such as [Online GUID Generator](https://www.guidgenerator.com/).</span></span>

## <a name="version-web-method"></a><span data-ttu-id="bda06-133">版本 Web 方法</span><span class="sxs-lookup"><span data-stu-id="bda06-133">Version web method</span></span>

<span data-ttu-id="bda06-134">Microsoft 会在每个月末更新 Office 365 IP 地址和 FQDN 条目。</span><span class="sxs-lookup"><span data-stu-id="bda06-134">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month.</span></span> <span data-ttu-id="bda06-135">出于支持事件、安全更新或其他操作要求，有时会发布带外更新。</span><span class="sxs-lookup"><span data-stu-id="bda06-135">Out-of-band updates are sometimes published due to support incidents, security updates or other operational requirements.</span></span>

<span data-ttu-id="bda06-136">我们为每个已发布实例的数据分配了版本号，你可以通过版本 Web 方法检查每个 Office 365 服务实例的最新版本。</span><span class="sxs-lookup"><span data-stu-id="bda06-136">The data for each published instance is assigned a version number, and the version web method enables you to check for the latest version of each Office 365 service instance.</span></span> <span data-ttu-id="bda06-137">我们建议每小时检查版本的次数不要超过一次。</span><span class="sxs-lookup"><span data-stu-id="bda06-137">We recommend that you check the version not more than once an hour.</span></span>

<span data-ttu-id="bda06-138">版本 Web 服务的参数如下：</span><span class="sxs-lookup"><span data-stu-id="bda06-138">Parameters for the version web method are:</span></span>

- <span data-ttu-id="bda06-139">**AllVersions=<true | false>** — 默认情况下，返回的版本为最新的。</span><span class="sxs-lookup"><span data-stu-id="bda06-139">**AllVersions=<true | false>** — By default, the version returned is the latest.</span></span> <span data-ttu-id="bda06-140">包括此可选参数，以请求首次发布 Web 服务之后的所有已发布版本。</span><span class="sxs-lookup"><span data-stu-id="bda06-140">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="bda06-141">**Format=<JSON | CSV | RSS>** — 除了 JSON 和 CSV 格式，版本 Web 服务还支持 RSS。</span><span class="sxs-lookup"><span data-stu-id="bda06-141">**Format=<JSON | CSV | RSS>** — In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="bda06-142">可以结合使用此可选参数及 _AllVersions=true_ 参数，以请求可用于 Outlook 或其他 RSS 读取器的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="bda06-142">You can use this optional parameter along with the _AllVersions=true_ parameter to request an RSS feed that can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="bda06-143">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — 此可选参数用于指定返回其版本的实例。</span><span class="sxs-lookup"><span data-stu-id="bda06-143">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="bda06-144">如果圣罗，则会返回所有实例。</span><span class="sxs-lookup"><span data-stu-id="bda06-144">If omitted, all instances are returned.</span></span> <span data-ttu-id="bda06-145">有效实例包括：Worldwide、China、Germany、USGovDoD、USGovGCCHigh。</span><span class="sxs-lookup"><span data-stu-id="bda06-145">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="bda06-146">版本 Web 方法不受速率限制，并且决不会返回 429 HTTP 响应代码。</span><span class="sxs-lookup"><span data-stu-id="bda06-146">The version web method is not rate limited and does not ever return 429 HTTP Response Codes.</span></span> <span data-ttu-id="bda06-147">对版本 Web 方法的响应包括一个缓存控制标头，它建议将数据缓存 1 小时。</span><span class="sxs-lookup"><span data-stu-id="bda06-147">The response to the version web method does include a cache-control header recommending caching of the data for 1 hour.</span></span> <span data-ttu-id="bda06-148">版本 Web 方法的结果可以是一条记录，也可以是一组记录。</span><span class="sxs-lookup"><span data-stu-id="bda06-148">The result from the version web method can be a single record or an array of records.</span></span> <span data-ttu-id="bda06-149">每条记录均包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="bda06-149">The elements of each record are:</span></span>

- <span data-ttu-id="bda06-150">instance — Office 365 服务实例的短名称。</span><span class="sxs-lookup"><span data-stu-id="bda06-150">instance — The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="bda06-151">latest — 指定实例的终结点的最新版本。</span><span class="sxs-lookup"><span data-stu-id="bda06-151">latest — The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="bda06-152">版本 — 指定实例的所有旧版本的列表。</span><span class="sxs-lookup"><span data-stu-id="bda06-152">versions — A list of all previous versions for the specified instance.</span></span> <span data-ttu-id="bda06-153">仅当 _AllVersions_ 参数为 true 时才包含此元素。</span><span class="sxs-lookup"><span data-stu-id="bda06-153">This element is only included if the _AllVersions_ parameter is true.</span></span>

### <a name="examples"></a><span data-ttu-id="bda06-154">示例：</span><span class="sxs-lookup"><span data-stu-id="bda06-154">Examples:</span></span>

<span data-ttu-id="bda06-155">示例 1 请求 URI：[https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bda06-155">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bda06-p113">此 URI 返回每个 Office 365 服务实例的最新版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="bda06-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
> <span data-ttu-id="bda06-p114">这些 URI 中 ClientRequestID 参数的 GUID 只是个例子。若要试用 Web 服务 URI，请生成你自己的 GUID。这项 Web 服务将来可能会屏蔽这些示例中的 GUID。</span><span class="sxs-lookup"><span data-stu-id="bda06-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="bda06-161">示例 2 请求 URI：[https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bda06-161">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bda06-p115">此 URI 返回指定 Office 365 服务实例的最新版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="bda06-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="bda06-164">示例 3 请求 URI：[https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bda06-164">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bda06-p116">此 URI 显示 CSV 格式输出。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="bda06-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="bda06-167">示例 4 请求 URI：[https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bda06-167">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bda06-p117">此 URI 显示 Office 365 全球服务实例的所有已发布旧版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="bda06-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="bda06-170">示例 5 RSS 源 URI：[https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="bda06-170">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="bda06-p118">此 URI 显示已发布版本的 RSS 源，其中包含指向每个版本的变更列表的链接。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="bda06-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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

## <a name="endpoints-web-method"></a><span data-ttu-id="bda06-173">终结点 Web 方法</span><span class="sxs-lookup"><span data-stu-id="bda06-173">Endpoints web method</span></span>

<span data-ttu-id="bda06-174">终结点 Web 方法可返回组成 Office 365 服务的 IP 地址范围和 URL 的所有记录。</span><span class="sxs-lookup"><span data-stu-id="bda06-174">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="bda06-175">应始终使用最新的终结点 Web 方法数据来进行网络设备配置。</span><span class="sxs-lookup"><span data-stu-id="bda06-175">The latest data from the endpoints web method should always be used for network device configuration.</span></span> <span data-ttu-id="bda06-176">Microsoft 会在发布新增内容前 30 天提前发出通知，以便你有时间更新访问控制列表和代理服务器跳过列表。</span><span class="sxs-lookup"><span data-stu-id="bda06-176">Microsoft provides advance notice 30 days prior to publishing new additions to give you time to update access control lists and proxy server bypass lists.</span></span> <span data-ttu-id="bda06-177">建议你仅在版本 Web 方法表示存在新的数据版本时才再次调用终结点 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="bda06-177">We recommend that you only call the endpoints web method again when the version web method indicates that a new version of the data is available.</span></span>

<span data-ttu-id="bda06-178">终结点 Web 方法的参数如下：</span><span class="sxs-lookup"><span data-stu-id="bda06-178">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="bda06-179">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** — 以逗号分隔的服务区域列表。</span><span class="sxs-lookup"><span data-stu-id="bda06-179">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** — A comma-separated list of service areas.</span></span> <span data-ttu-id="bda06-180">有效项为 _Common_、_Exchange_、_SharePoint_ 和 _Skype_。</span><span class="sxs-lookup"><span data-stu-id="bda06-180">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="bda06-181">由于 _Common_ 服务区域项为所有其他服务区域的先决条件，因此 Web 服务始终包括它们。</span><span class="sxs-lookup"><span data-stu-id="bda06-181">Because _Common_ service area items are a prerequisite for all other service areas, the web service always includes them.</span></span> <span data-ttu-id="bda06-182">如果不包括此参数，则会返回所有服务区域。</span><span class="sxs-lookup"><span data-stu-id="bda06-182">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="bda06-183">**TenantName=<tenant_name>** — 你的 Office 365 租户名称。</span><span class="sxs-lookup"><span data-stu-id="bda06-183">**TenantName=<tenant_name>** — Your Office 365 tenant name.</span></span> <span data-ttu-id="bda06-184">Web 服务采用所提供的名称，并将其插入到包含租户名称的 URL 中。</span><span class="sxs-lookup"><span data-stu-id="bda06-184">The web service takes your provided name and inserts it in parts of URLs that include the tenant name.</span></span> <span data-ttu-id="bda06-185">如果未提供租户名称，则这些 URL 的部分具有通配符字符 (\*)。</span><span class="sxs-lookup"><span data-stu-id="bda06-185">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="bda06-186">**NoIPv6=<true | false>** — 将此值设置为 _true_ 可从输出中排除 IPv6 地址（如果你未在网络中使用 IPv6）。</span><span class="sxs-lookup"><span data-stu-id="bda06-186">**NoIPv6=<true | false>** — Set the value to _true_ to exclude IPv6 addresses from the output if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="bda06-187">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — 此必填参数用于指定从中返回终结点的实例。</span><span class="sxs-lookup"><span data-stu-id="bda06-187">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — This required parameter specifies the instance from which to return the endpoints.</span></span> <span data-ttu-id="bda06-188">有效实例包括：_Worldwide_、_China_、_Germany_、_USGovDoD_ 和 _USGovGCCHigh_。</span><span class="sxs-lookup"><span data-stu-id="bda06-188">Valid instances are: _Worldwide_, _China_, _Germany_, _USGovDoD_, and _USGovGCCHigh_.</span></span>

<span data-ttu-id="bda06-189">如果从相同客户端 IP 地址调用终结点 Web 方法的次数过多，则可能会收到 HTTP 响应代码 _429（请求过多）_。</span><span class="sxs-lookup"><span data-stu-id="bda06-189">If you call the endpoints web method too many times from the same client IP address, you might receive HTTP response code _429 (Too Many Requests)_.</span></span> <span data-ttu-id="bda06-190">如果收到此响应代码，请先等待 1 小时，然后再重复你的请求，或者为该请求生成新的 GUID。</span><span class="sxs-lookup"><span data-stu-id="bda06-190">If you get this response code, wait 1 hour before repeating your request, or generate a new GUID for the request.</span></span> <span data-ttu-id="bda06-191">作为一般的最佳实践，仅在版本 Web 方法表示存在新的可用版本时才调用终结点 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="bda06-191">As a general best practice, only call the endpoints web method when the version web method indicates that a new version is available.</span></span>

<span data-ttu-id="bda06-192">终结点 Web 方法的结果是一组记录，每条记录均代表一个终结点集。</span><span class="sxs-lookup"><span data-stu-id="bda06-192">The result from the endpoints web method is an array of records in which each record represents a specific endpoint set.</span></span> <span data-ttu-id="bda06-193">每条记录均包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="bda06-193">The elements for each record are:</span></span>

- <span data-ttu-id="bda06-194">id — 终结点集的不可变 ID 号。</span><span class="sxs-lookup"><span data-stu-id="bda06-194">id — The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="bda06-195">serviceArea — 所属的服务区域：_Common_、_Exchange_、_SharePoint_ 或 _Skype_。</span><span class="sxs-lookup"><span data-stu-id="bda06-195">serviceArea — The service area that this is part of: _Common_, _Exchange_, _SharePoint_, or _Skype_.</span></span>
- <span data-ttu-id="bda06-196">urls — 终结点集的 URL。</span><span class="sxs-lookup"><span data-stu-id="bda06-196">urls — URLs for the endpoint set.</span></span> <span data-ttu-id="bda06-197">此为包含 DNS 记录的 JSON 数组。</span><span class="sxs-lookup"><span data-stu-id="bda06-197">A JSON array of DNS records.</span></span> <span data-ttu-id="bda06-198">若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="bda06-198">Omitted if blank.</span></span>
- <span data-ttu-id="bda06-199">tcpPorts — 终结点集的 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="bda06-199">tcpPorts — TCP ports for the endpoint set.</span></span> <span data-ttu-id="bda06-200">所有端口元素都格式化为端口的逗号分隔列表，或用短划线字符 (-) 分隔的端口范围。</span><span class="sxs-lookup"><span data-stu-id="bda06-200">All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-).</span></span> <span data-ttu-id="bda06-201">端口适用于相应类别的特定终结点集中的所有 IP 地址和所有 URL。</span><span class="sxs-lookup"><span data-stu-id="bda06-201">Ports apply to all IP addresses and all URLs in the endpoint set for a given category.</span></span> <span data-ttu-id="bda06-202">若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="bda06-202">Omitted if blank.</span></span>
- <span data-ttu-id="bda06-203">udpPorts — 此终结点集中 IP 地址范围的 UDP 端口。</span><span class="sxs-lookup"><span data-stu-id="bda06-203">udpPorts — UDP ports for the IP address ranges in this endpoint set.</span></span> <span data-ttu-id="bda06-204">若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="bda06-204">Omitted if blank.</span></span>
- <span data-ttu-id="bda06-205">ips — 与此终结点关联的 IP 地址范围，设置为与列出的 TCP 或 UDP 端口关联。</span><span class="sxs-lookup"><span data-stu-id="bda06-205">ips — The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports.</span></span> <span data-ttu-id="bda06-206">IP 地址范围的 JSON 数组。</span><span class="sxs-lookup"><span data-stu-id="bda06-206">A JSON array of IP address ranges.</span></span> <span data-ttu-id="bda06-207">若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="bda06-207">Omitted if blank.</span></span>
- <span data-ttu-id="bda06-208">category — 终结点集的连接类别。</span><span class="sxs-lookup"><span data-stu-id="bda06-208">category — The connectivity category for the endpoint set.</span></span> <span data-ttu-id="bda06-209">有效值为 _Optimize_、_Allow_ 和 _Default_。</span><span class="sxs-lookup"><span data-stu-id="bda06-209">Valid values are _Optimize_, _Allow_, and _Default_.</span></span> <span data-ttu-id="bda06-210">如果搜索特定 IP 地址或 URL 类别的终结点 Web 方法输出，则查询可能会返回多个类别。</span><span class="sxs-lookup"><span data-stu-id="bda06-210">If you search the endpoints web method output for the category of a specific IP address or URL, it is possible that your query will return multiple categories.</span></span> <span data-ttu-id="bda06-211">在这种情况下，请按照最高优先级类别的建议操作。</span><span class="sxs-lookup"><span data-stu-id="bda06-211">In such a case, follow the recommendation for the highest priority category.</span></span> <span data-ttu-id="bda06-212">例如，如果终结点同时显示在 _Optimize_ 和 _Allow_ 中，则应该遵循 _Optimize_ 的要求。</span><span class="sxs-lookup"><span data-stu-id="bda06-212">For example, if the endpoint appears in both _Optimize_ and _Allow_, you should follow the requirements for _Optimize_.</span></span> <span data-ttu-id="bda06-213">必需项。</span><span class="sxs-lookup"><span data-stu-id="bda06-213">Required.</span></span>
- <span data-ttu-id="bda06-214">expressRoute — 如果此终结点集通过 ExpressRoute 进行路由，则为 _True_，否则为 _False_。</span><span class="sxs-lookup"><span data-stu-id="bda06-214">expressRoute — _True_ if this endpoint set is routed over ExpressRoute, _False_ if not.</span></span>
- <span data-ttu-id="bda06-215">required — 如果此终结点集必须有连接才能支持 Office 365，则为 _True_。</span><span class="sxs-lookup"><span data-stu-id="bda06-215">required — _True_ if this endpoint set is required to have connectivity for Office 365 to be supported.</span></span> <span data-ttu-id="bda06-216">如果此终结点集为可选，则为 _False_。</span><span class="sxs-lookup"><span data-stu-id="bda06-216">_False_ if this endpoint set is optional.</span></span>
- <span data-ttu-id="bda06-217">notes — 对于可选终结点，此文本描述了无法在网络层访问此终结点集中的 IP 地址或 URL 的情况下不可用的 Office 365 功能。</span><span class="sxs-lookup"><span data-stu-id="bda06-217">notes — For optional endpoints, this text describes Office 365 functionality that would be unavailable if IP addresses or URLs in this endpoint set cannot be accessed at the network layer.</span></span> <span data-ttu-id="bda06-218">若为空白，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="bda06-218">Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="bda06-219">示例：</span><span class="sxs-lookup"><span data-stu-id="bda06-219">Examples:</span></span>

<span data-ttu-id="bda06-220">示例 1 请求 URI：[https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bda06-220">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bda06-221">此 URI 对全部工作负载获取 Office 365 全球实例的所有终结点。</span><span class="sxs-lookup"><span data-stu-id="bda06-221">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads.</span></span> <span data-ttu-id="bda06-222">示例结果的输出摘录如下：</span><span class="sxs-lookup"><span data-stu-id="bda06-222">Example result that shows an excerpt of the output:</span></span>

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

<span data-ttu-id="bda06-223">请注意，此示例中的请求的完整输出将包含其他终结点集。</span><span class="sxs-lookup"><span data-stu-id="bda06-223">Note that the full output of the request in this example would contain other endpoint sets.</span></span>

<span data-ttu-id="bda06-224">示例 2 请求 URI：[https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bda06-224">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bda06-225">此示例仅对 Exchange Online 和依赖项获取 Office 365 全球实例的终结点。</span><span class="sxs-lookup"><span data-stu-id="bda06-225">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="bda06-226">示例 2 的输出类似于示例 1，不同之处在于结果不包括 SharePoint Online 或 Skype for Business Online 终结点。</span><span class="sxs-lookup"><span data-stu-id="bda06-226">The output for example 2 is similar to example 1 except that the results would not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="bda06-227">变更 Web 方法</span><span class="sxs-lookup"><span data-stu-id="bda06-227">Changes web method</span></span>

<span data-ttu-id="bda06-228">变更 Web 方法返回已发布的最新更新。这通常是上月的 IP 地址范围和 URL 变更。</span><span class="sxs-lookup"><span data-stu-id="bda06-228">The changes web method returns the most recent updates that have been published, typically the previous month's changes to IP address ranges and URLs.</span></span>

<span data-ttu-id="bda06-229">终结点数据的最重要变更是新 URL 或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="bda06-229">The most critical changes to endpoints data are new URLs and IP addresses.</span></span> <span data-ttu-id="bda06-230">如果无法将 IP 地址添加到防火墙访问控制列表，或无法将 URL 添加到代理服务器跳过列表，可能会导致网络设备后的 Office 365 用户遇到服务中断。</span><span class="sxs-lookup"><span data-stu-id="bda06-230">Failure to add an IP address to a firewall access control list or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device.</span></span> <span data-ttu-id="bda06-231">尽管有运营要求，新的终结点将在其配置使用之日的前 30 天提前发布到 Web 服务，以便你有时间更新访问控制列表和代理服务器跳过列表。</span><span class="sxs-lookup"><span data-stu-id="bda06-231">Notwithstanding operational requirements, new endpoints are published to the web service 30 days in advance of the date the endpoints are provisioned for use to give you time to update access control lists and proxy server bypass lists.</span></span>

<span data-ttu-id="bda06-232">变更 Web 方法需要使用以下必填参数：</span><span class="sxs-lookup"><span data-stu-id="bda06-232">The required parameter for the changes web method is:</span></span>

- <span data-ttu-id="bda06-233">**Version=\<YYYYMMDDNN>** — 所需的 URL 路由参数。</span><span class="sxs-lookup"><span data-stu-id="bda06-233">**Version=\<YYYYMMDDNN>** — Required URL route parameter.</span></span> <span data-ttu-id="bda06-234">此值为当前实施的版本。</span><span class="sxs-lookup"><span data-stu-id="bda06-234">This value is the version that you have currently implemented.</span></span> <span data-ttu-id="bda06-235">Web 服务应返回自该版本之后发生的变更。</span><span class="sxs-lookup"><span data-stu-id="bda06-235">The web service will return the changes since that version.</span></span> <span data-ttu-id="bda06-236">格式为 _YYYYMMDDNN_；如果需要在一天内发布多个版本，则 _NN_ 是一个递增的自然数，而 _00_ 表示给定日期的第一个更新。</span><span class="sxs-lookup"><span data-stu-id="bda06-236">The format is _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day, with _00_ representing the first update for a given day.</span></span> <span data-ttu-id="bda06-237">Web 服务要求 _version_ 参数恰好包含 10 位数。</span><span class="sxs-lookup"><span data-stu-id="bda06-237">The web service requires the _version_ parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="bda06-238">变更 Web 方法受速率限制，与终结点 Web 方法受限于速率一样。</span><span class="sxs-lookup"><span data-stu-id="bda06-238">The changes web method is rate limited in the same way as the endpoints web method.</span></span> <span data-ttu-id="bda06-239">如果收到 429 HTTP 响应代码，请先等待 1 小时，然后再重复你的请求，或者为该请求生成新的 GUID。</span><span class="sxs-lookup"><span data-stu-id="bda06-239">If you receive a 429 HTTP response code, wait 1 hour before repeating your request or generate a new GUID for the request.</span></span>

<span data-ttu-id="bda06-240">变更 Web 方法的结果是一组记录，每条记录均代表特定版本终结点中的变更。</span><span class="sxs-lookup"><span data-stu-id="bda06-240">The result from the changes web method is an array of records in which each record represents a change in a specific version of the endpoints.</span></span> <span data-ttu-id="bda06-241">每条记录均包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="bda06-241">The elements for each record are:</span></span>

- <span data-ttu-id="bda06-242">id — 变更记录的不可变 ID。</span><span class="sxs-lookup"><span data-stu-id="bda06-242">id — The immutable id of the change record.</span></span>
- <span data-ttu-id="bda06-243">endpointSetId — 变更的终结点集记录的 ID。</span><span class="sxs-lookup"><span data-stu-id="bda06-243">endpointSetId — The ID of the endpoint set record that is changed.</span></span>
- <span data-ttu-id="bda06-244">disposition — 描述了终结点集记录有何变更。</span><span class="sxs-lookup"><span data-stu-id="bda06-244">disposition — Describes what the change did to the endpoint set record.</span></span> <span data-ttu-id="bda06-245">值包括 _change_、_add_ 或 _remove_。</span><span class="sxs-lookup"><span data-stu-id="bda06-245">Values are _change_, _add_, or _remove_.</span></span>
- <span data-ttu-id="bda06-246">impact — 并非所有变更都对每个环境同样重要。</span><span class="sxs-lookup"><span data-stu-id="bda06-246">impact — Not all changes will be equally important to every environment.</span></span> <span data-ttu-id="bda06-247">此元素说明了相应变更对企业网络外围环境的预期影响。</span><span class="sxs-lookup"><span data-stu-id="bda06-247">This element describes the expected impact to an enterprise network perimeter environment as a result of this change.</span></span> <span data-ttu-id="bda06-248">此属性仅包含在版本 **2018112800** 及更高版本的变更记录中。</span><span class="sxs-lookup"><span data-stu-id="bda06-248">This element is included only in change records of version **2018112800** and later.</span></span> <span data-ttu-id="bda06-249">impact 选项包括：— AddedIp – IP 地址已添加到 Office 365，且很快就会对服务生效。</span><span class="sxs-lookup"><span data-stu-id="bda06-249">Options for the impact are: — AddedIp – An IP address was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="bda06-250">这表示需要更改防火墙或其他第 3 层网络外围设备。</span><span class="sxs-lookup"><span data-stu-id="bda06-250">This represents a change you need to take on a firewall or other layer 3 network perimeter device.</span></span> <span data-ttu-id="bda06-251">如果你并没有在我们开始使用此元素之前添加它，可能会遇到故障。</span><span class="sxs-lookup"><span data-stu-id="bda06-251">If you don’t add this before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="bda06-252">— AddedUrl – URL 已添加到 Office 365，且很快就会对服务生效。</span><span class="sxs-lookup"><span data-stu-id="bda06-252">— AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="bda06-253">这表示需要更改代理服务器或 URL 分析网络外围设备。</span><span class="sxs-lookup"><span data-stu-id="bda06-253">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="bda06-254">如果你并没有在我们开始使用之前添加此 URL，可能会遇到故障。</span><span class="sxs-lookup"><span data-stu-id="bda06-254">If you don’t add this URL before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="bda06-255">— AddedIpAndUrl — IP 地址和 URL 均已添加。</span><span class="sxs-lookup"><span data-stu-id="bda06-255">— AddedIpAndUrl — Both an IP address and a URL were added.</span></span> <span data-ttu-id="bda06-256">这表示需要更改防火墙第 3 层设备、代理服务器或 URL 分析设备。</span><span class="sxs-lookup"><span data-stu-id="bda06-256">This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device.</span></span> <span data-ttu-id="bda06-257">如果你并没有在我们开始使用之前添加此 IP/URL，可能会遇到故障。</span><span class="sxs-lookup"><span data-stu-id="bda06-257">If you don’t add this IP/URL pair before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="bda06-258">— RemovedIpOrUrl – 从 Office 365 中至少删除了一个 IP 地址或 URL。</span><span class="sxs-lookup"><span data-stu-id="bda06-258">— RemovedIpOrUrl – At least one IP address or URL was removed from Office 365.</span></span> <span data-ttu-id="bda06-259">从外围设备中删除网络终结点，但此操作并无截止时间。</span><span class="sxs-lookup"><span data-stu-id="bda06-259">Remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  <span data-ttu-id="bda06-260">— ChangedIsExpressRoute – ExpressRoute 支持属性已更改。</span><span class="sxs-lookup"><span data-stu-id="bda06-260">— ChangedIsExpressRoute – The ExpressRoute support attribute was changed.</span></span> <span data-ttu-id="bda06-261">如果使用 ExpressRoute，可能需要采取措施，具体视配置而定。</span><span class="sxs-lookup"><span data-stu-id="bda06-261">If you use ExpressRoute, you might need to take action depending on your configuration.</span></span>
  <span data-ttu-id="bda06-262">— MovedIpOrUrl – 在此终结点集和另一个终结点集之间迁移了 IP 地址或 URL。</span><span class="sxs-lookup"><span data-stu-id="bda06-262">— MovedIpOrUrl – We moved an IP address or Url between this endpoint set and another one.</span></span> <span data-ttu-id="bda06-263">通常无需采取任何措施。</span><span class="sxs-lookup"><span data-stu-id="bda06-263">Generally no action is required.</span></span>
  <span data-ttu-id="bda06-264">— RemovedDuplicateIpOrUrl – 删除了重复的 IP 地址或 URL，但它仍是对 Office 365 发布的。</span><span class="sxs-lookup"><span data-stu-id="bda06-264">— RemovedDuplicateIpOrUrl – We removed a duplicate IP address or Url but it’s still published for Office 365.</span></span> <span data-ttu-id="bda06-265">通常无需采取任何措施。</span><span class="sxs-lookup"><span data-stu-id="bda06-265">Generally no action is required.</span></span>
  <span data-ttu-id="bda06-266">— OtherNonPriorityChanges – 更改了一些不如其他所有选项重要的内容，例如注释字段的内容。</span><span class="sxs-lookup"><span data-stu-id="bda06-266">— OtherNonPriorityChanges – We changed something less critical than all of the other options, such as the contents of a note field.</span></span>
- <span data-ttu-id="bda06-267">version — 引入变更的已发布终结点集的版本。</span><span class="sxs-lookup"><span data-stu-id="bda06-267">version — The version of the published endpoint set in which the change was introduced.</span></span> <span data-ttu-id="bda06-268">版本号格式为 _YYYYMMDDNN_，其中 _NN_ 是必须在一天内发布多个版本时递增的自然数。</span><span class="sxs-lookup"><span data-stu-id="bda06-268">Version numbers are of the format _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="bda06-269">previous — 详细说明终结点集上的旧变更元素值的子结构。</span><span class="sxs-lookup"><span data-stu-id="bda06-269">previous — A substructure detailing previous values of changed elements on the endpoint set.</span></span> <span data-ttu-id="bda06-270">对于新添加的终结点集，它们未包含在内。</span><span class="sxs-lookup"><span data-stu-id="bda06-270">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="bda06-271">包括 _ExpressRoute_、_serviceArea_、_category_、_required_、_tcpPorts_、_udpPorts_ 和 _notes_。</span><span class="sxs-lookup"><span data-stu-id="bda06-271">Includes  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="bda06-272">current — 详细说明终结点集上的更新变更元素值的子结构。</span><span class="sxs-lookup"><span data-stu-id="bda06-272">current — A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="bda06-273">包括 _ExpressRoute_、_serviceArea_、_category_、_required_、_tcpPorts_、_udpPorts_ 和 _notes_。</span><span class="sxs-lookup"><span data-stu-id="bda06-273">Includes _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="bda06-274">add — 详细说明要添加到终结点集集合的项的子结构。</span><span class="sxs-lookup"><span data-stu-id="bda06-274">add — A substructure detailing items to be added to endpoint set collections.</span></span> <span data-ttu-id="bda06-275">如果没有要添加的项，将省略此元素。</span><span class="sxs-lookup"><span data-stu-id="bda06-275">Omitted if there are no additions.</span></span>
  <span data-ttu-id="bda06-276">— effectiveDate — 定义添加项在服务中的生效日期。</span><span class="sxs-lookup"><span data-stu-id="bda06-276">— effectiveDate — Defines the data when the additions will be live in the service.</span></span>
  <span data-ttu-id="bda06-277">— ips — 要添加到 _ips_ 数组的项。</span><span class="sxs-lookup"><span data-stu-id="bda06-277">— ips — Items to be added to the _ips_ array.</span></span>
  <span data-ttu-id="bda06-278">— urls — 要添加到 _urls_ 数组的项。</span><span class="sxs-lookup"><span data-stu-id="bda06-278">— urls- Items to be added to the _urls_ array.</span></span>
- <span data-ttu-id="bda06-279">remove — 详细说明要从终结点集中删除的项的子结构。</span><span class="sxs-lookup"><span data-stu-id="bda06-279">remove — A substructure detailing items to be removed from the endpoint set.</span></span> <span data-ttu-id="bda06-280">如果没有删除项，则省略。</span><span class="sxs-lookup"><span data-stu-id="bda06-280">Omitted if there are no removals.</span></span>
  <span data-ttu-id="bda06-281">— ips — 要从 _ips_ 数组中删除的项。</span><span class="sxs-lookup"><span data-stu-id="bda06-281">— ips — Items to be removed from the _ips_ array.</span></span>
  <span data-ttu-id="bda06-282">— urls — 要从 _urls_ 数组中删除的项。</span><span class="sxs-lookup"><span data-stu-id="bda06-282">— urls- Items to be removed from the _urls_ array.</span></span>

### <a name="examples"></a><span data-ttu-id="bda06-283">示例：</span><span class="sxs-lookup"><span data-stu-id="bda06-283">Examples:</span></span>

<span data-ttu-id="bda06-284">示例 1 请求 URI：[https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bda06-284">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bda06-p144">这请求获取 Office 365 全球服务实例先前的所有变更。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="bda06-p144">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="bda06-287">示例 2 请求 URI：[https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bda06-287">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bda06-p145">这请求获取 Office 365 全球实例自指定版本起的变更。在此示例中，指定版本是最新版本。示例结果如下：</span><span class="sxs-lookup"><span data-stu-id="bda06-p145">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="bda06-291">示例 PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="bda06-291">Example PowerShell Script</span></span>

<span data-ttu-id="bda06-292">你可以运行此 PowerShell 脚本来查看是否需要为更新的数据采取操作。</span><span class="sxs-lookup"><span data-stu-id="bda06-292">You can run this PowerShell script to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="bda06-293">你可以将此脚本作为计划任务运行，以检查是否存在版本更新。</span><span class="sxs-lookup"><span data-stu-id="bda06-293">You can run this script as a scheduled task to check for a version update.</span></span> <span data-ttu-id="bda06-294">为了避免 Web 服务出现过多负载，每小时运行脚本的次数不要超过一次。</span><span class="sxs-lookup"><span data-stu-id="bda06-294">To avoid excessive load on the web service, try not to run the script more than once an hour.</span></span>

<span data-ttu-id="bda06-295">此脚本执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="bda06-295">The script does the following:</span></span>

- <span data-ttu-id="bda06-296">通过调用 Web 服务 REST API，检查 Office 365 全球实例终结点的版本号。</span><span class="sxs-lookup"><span data-stu-id="bda06-296">Checks the version number of the current Office 365 Worldwide instance endpoints by calling the web service REST API.</span></span>
- <span data-ttu-id="bda06-297">检查 _$Env:TEMP\O365_endpoints_latestversion.txt_ 中的当前版本文件。</span><span class="sxs-lookup"><span data-stu-id="bda06-297">Checks for a current version file at _$Env:TEMP\O365_endpoints_latestversion.txt_.</span></span> <span data-ttu-id="bda06-298">全局变量 **$Env:TEMP** 的路径通常为 _C:\Users\\<username\>\AppData\Local\Temp_。</span><span class="sxs-lookup"><span data-stu-id="bda06-298">The path of the global variable **$Env:TEMP** is usually _C:\Users\\<username\>\AppData\Local\Temp_.</span></span>
- <span data-ttu-id="bda06-299">如果这是首次运行脚本，则脚本将返回当前版本以及所有当前 IP 地址和 URL，将终结点版本写入文件 _$Env:TEMP\O365_endpoints_latestversion.txt_，并将终结点数据输出写入文件 _$Env:TEMP\O365_endpoints_data.txt_。</span><span class="sxs-lookup"><span data-stu-id="bda06-299">If this is the first time the script has been run, the script returns the current version and all current IP addresses and URLs, writes the endpoints version to the file _$Env:TEMP\O365_endpoints_latestversion.txt_ and the endpoints data output to the file _$Env:TEMP\O365_endpoints_data.txt_.</span></span> <span data-ttu-id="bda06-300">可通过编辑以下行来修改输出文件的路径和/或名称：</span><span class="sxs-lookup"><span data-stu-id="bda06-300">You can modify the path and/or name of the output file by editing these lines:</span></span>

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- <span data-ttu-id="bda06-301">在后续每次执行脚本时，如果最新的 Web 服务版本与 _O365_endpoints_latestversion.txt_ 文件中的版本相同，则脚本将退出，而不进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="bda06-301">On each subsequent execution of the script, if the latest web service version is identical to the version in the _O365_endpoints_latestversion.txt_ file, the script exits without making any changes.</span></span>
- <span data-ttu-id="bda06-302">如果最新的 Web 服务版本比 _O365_endpoints_latestversion.txt_ 文件中的版本更新，则该脚本将返回 **Allow** 和 **Optimize** 类别的终结点和筛选器，更新 _O365_endpoints_latestversion.txt_ 文件中的版本，并将更新的数据写入 _O365_endpoints_data.txt_ 文件。</span><span class="sxs-lookup"><span data-stu-id="bda06-302">When the latest web service version is newer than the version in the _O365_endpoints_latestversion.txt_ file, the script returns the endpoints and filters for the **Allow** and **Optimize** category endpoints, updates the version in the _O365_endpoints_latestversion.txt_ file, and writes the updated data to the _O365_endpoints_data.txt_ file.</span></span>

<span data-ttu-id="bda06-303">该脚本将为在其上运行的计算机生成唯一的 _ClientRequestId_，并在多个调用中重复使用此 ID。</span><span class="sxs-lookup"><span data-stu-id="bda06-303">The script generates a unique _ClientRequestId_ for the computer it is executed on, and reuses this ID across multiple calls.</span></span> <span data-ttu-id="bda06-304">此 ID 存储在 _O365_endpoints_latestversion.txt_ 文件中。</span><span class="sxs-lookup"><span data-stu-id="bda06-304">This ID is stored in the _O365_endpoints_latestversion.txt_ file.</span></span>

### <a name="to-run-the-powershell-script"></a><span data-ttu-id="bda06-305">运行 PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="bda06-305">To run the PowerShell script</span></span>

1. <span data-ttu-id="bda06-306">复制脚本并在本地硬盘驱动器或脚本位置将其另存为 _Get-O365WebServiceUpdates.ps1_。</span><span class="sxs-lookup"><span data-stu-id="bda06-306">Copy the script and save it to your local hard drive or script location as _Get-O365WebServiceUpdates.ps1_.</span></span>
1. <span data-ttu-id="bda06-307">在首选脚本编辑器（如 PowerShell ISE 或 VS Code）中执行脚本，或使用以下命令从 PowerShell 控制台执行：</span><span class="sxs-lookup"><span data-stu-id="bda06-307">Execute the script in your preferred script editor such as the PowerShell ISE or VS Code, or from a PowerShell console using the following command:</span></span>

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    <span data-ttu-id="bda06-308">不向脚本传递任何参数。</span><span class="sxs-lookup"><span data-stu-id="bda06-308">There are no parameters to pass to the script.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="bda06-309">示例 Python 脚本</span><span class="sxs-lookup"><span data-stu-id="bda06-309">Example Python Script</span></span>

<span data-ttu-id="bda06-p150">运行下面的 Python 脚本（已使用 Windows 10 上的 Python 3.6.3 进行测试），可确定是否需要对已更新数据执行操作。此脚本检查 Office 365 全球实例终结点的版本号。若有变更，它就会下载终结点，并筛选出 _Allow_ 和 _Optimize_ 类别终结点。它还会跨多个调用使用唯一 ClientRequestId，并将找到的最新版本保存到临时文件中。应每小时调用一次此脚本，以检查是否有版本更新。</span><span class="sxs-lookup"><span data-stu-id="bda06-p150">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="bda06-315">Web 服务接口版本控制</span><span class="sxs-lookup"><span data-stu-id="bda06-315">Web Service interface versioning</span></span>

<span data-ttu-id="bda06-316">日后可能需要更新这些 Web 服务方法的参数或结果。</span><span class="sxs-lookup"><span data-stu-id="bda06-316">Updates to the parameters or results for these web service methods may be required in the future.</span></span> <span data-ttu-id="bda06-317">在这些 Web 服务的正式版本发布后，Microsoft 将做出合理的努力，以事先通知 Web 服务的实质性更新。</span><span class="sxs-lookup"><span data-stu-id="bda06-317">After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service.</span></span> <span data-ttu-id="bda06-318">如果认为更新必须变更使用 Web 服务的客户端，Microsoft 将在新版本发布后的至少 12 个月内保留旧版（上一版）Web 服务。</span><span class="sxs-lookup"><span data-stu-id="bda06-318">When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least 12 months after the release of the new version.</span></span> <span data-ttu-id="bda06-319">在此期间未升级的客户可能无法访问 Web 服务及其方法。</span><span class="sxs-lookup"><span data-stu-id="bda06-319">Customers who do not upgrade during that time may be unable to access the web service and its methods.</span></span> <span data-ttu-id="bda06-320">如果 Web 服务接口签名发生以下变更，客户必须确保 Web 服务的客户端能继续正常运行，而不出现错误：</span><span class="sxs-lookup"><span data-stu-id="bda06-320">Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="bda06-321">将新的可选参数添加到现有 Web 方法中，此参数既不必由旧客户端提供，也不会影响旧客户端收到的结果。</span><span class="sxs-lookup"><span data-stu-id="bda06-321">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="bda06-322">将响应 REST 项之一或其他列中的新命名特性添加到响应 CSV。</span><span class="sxs-lookup"><span data-stu-id="bda06-322">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="bda06-323">添加新 Web 方法，其使用旧客户端未调用的新名称。</span><span class="sxs-lookup"><span data-stu-id="bda06-323">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="update-notifications"></a><span data-ttu-id="bda06-324">更新通知</span><span class="sxs-lookup"><span data-stu-id="bda06-324">Update notifications</span></span>

<span data-ttu-id="bda06-325">当 IP 地址和 URL 的变更发布到 Web 服务时，你可以使用几种不同的方法来获取电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="bda06-325">You can use a few different methods to get email notifications when changes to the IP addresses and URLs are published to the web service.</span></span>

- <span data-ttu-id="bda06-326">若要使用 Microsoft Flow 解决方案，请参阅[使用 Microsoft Flow 接收对 Office 365 IP 地址和 URL 所做的更改的电子邮件](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)。</span><span class="sxs-lookup"><span data-stu-id="bda06-326">To use a Microsoft Flow solution, see [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>
- <span data-ttu-id="bda06-327">若要使用 ARM 模板部署 Azure Logic App，请参阅 [Office 365 更新通知 (v1.1)](https://aka.ms/ipurlws-updates-template)。</span><span class="sxs-lookup"><span data-stu-id="bda06-327">To deploy an Azure Logic App using an ARM template, see [Office 365 Update Notification (v1.1)](https://aka.ms/ipurlws-updates-template).</span></span>
- <span data-ttu-id="bda06-328">若要使用 PowerShell 编写自己的通知脚本，请参阅 [Send-MailMessage](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage)。</span><span class="sxs-lookup"><span data-stu-id="bda06-328">To write your own notification script using PowerShell, see [Send-MailMessage](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage).</span></span>

## <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="bda06-329">导出代理 PAC 文件</span><span class="sxs-lookup"><span data-stu-id="bda06-329">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="bda06-330">[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) 是 PowerShell 脚本，它从 Office 365 IP 地址和 URL Web 服务读取最新网络终结点，并创建示例 PAC 文件。</span><span class="sxs-lookup"><span data-stu-id="bda06-330">[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the Office 365 IP Address and URL web service and creates a sample PAC file.</span></span> <span data-ttu-id="bda06-331">有关使用 Get-PacFile 的信息，请参阅[使用 PAC 文件进行至关重要的 Office 365 流量的直接路由](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic)。</span><span class="sxs-lookup"><span data-stu-id="bda06-331">For information on using Get-PacFile, see [Use a PAC file for direct routing of vital Office 365 traffic](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).</span></span>

## <a name="related-topics"></a><span data-ttu-id="bda06-332">相关主题</span><span class="sxs-lookup"><span data-stu-id="bda06-332">Related Topics</span></span>
  
[<span data-ttu-id="bda06-333">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="bda06-333">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[<span data-ttu-id="bda06-334">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="bda06-334">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="bda06-335">Office 365 终结点 FAQ</span><span class="sxs-lookup"><span data-stu-id="bda06-335">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="bda06-336">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="bda06-336">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="bda06-337">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="bda06-337">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="bda06-338">评估 Office 365 网络连接</span><span class="sxs-lookup"><span data-stu-id="bda06-338">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
[<span data-ttu-id="bda06-339">Skype for Business Online 中的媒体质量和网络连接性能</span><span class="sxs-lookup"><span data-stu-id="bda06-339">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="bda06-340">优化 Skype for Business Online 网络</span><span class="sxs-lookup"><span data-stu-id="bda06-340">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="bda06-341">使用基线和性能历史记录优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="bda06-341">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="bda06-342">Office 365 性能疑难解答计划</span><span class="sxs-lookup"><span data-stu-id="bda06-342">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
