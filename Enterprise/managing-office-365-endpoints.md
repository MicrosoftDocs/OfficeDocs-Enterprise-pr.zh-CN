---
title: 管理 Office 365 终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/22/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 有些企业网络限制到泛型 internet 位置的访问或包括大量将或网络流量的处理。若要确保像这些可以访问 Office 365，网络和代理管理员需要管理的 Fqdn，Url、 列表和 IP 地址的网络上的计算机组成的 Office 365 终结点列表。要添加到直接路由、 代理绕过和/或防火墙规则和 PAC 文件，以确保网络请求是能够访问 Office 365 这些需要。
ms.openlocfilehash: 480d2fa1b55507187f9150d02907849178a451b5
ms.sourcegitcommit: d93f7a51e8cdefdfc9933cdf1f9e413b013bb367
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "25719016"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="92074-105">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="92074-105">Managing Office 365 endpoints</span></span>

<span data-ttu-id="92074-p102">具有多个 office 位置和 WAN 连接的大多数企业组织需要需要配置的 Office 365 网络连接。您可以通过发送所有受信任的 Office 365 网络请求直接通过防火墙、 绕过所有其他数据包级别检查或处理优化您的网络。这会减少延迟和外围容量要求。确定 Office 365 网络流量是提供最佳性能，为您的用户的第一步。有关 Office 365 网络连接的详细信息，请参阅[Office 365 网络连接原则](office-365-network-connectivity-principles.md)</span><span class="sxs-lookup"><span data-stu-id="92074-p102">Most enterprise organizations that have multiple office locations and a connecting WAN will need to need configuration for Office 365 network connectivity. You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces latency and your perimeter capacity requirements. Identifying Office 365 network traffic is the first step in providing optimal performance for your users. For more information about Office 365 network connectivity, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md)</span></span>

<span data-ttu-id="92074-111">Microsoft 建议您访问 Office 365 网络终结点和对其使用[Office 365 IP 地址和 Web 服务 URL](office-365-ip-web-service.md)的更改</span><span class="sxs-lookup"><span data-stu-id="92074-111">Microsoft recommends you access the Office 365 network endpoints and changes to them using the [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md)</span></span>

<span data-ttu-id="92074-p103">无论您管理重要的 Office 365 网络流量的方式，Office 365 需要 Internet 连接。不需要连接其他网络终结点都列在[的 Office 365 IP 地址和 URL Web 服务中不包含的其他终结点](additional-office365-ip-addresses-and-urls.md)</span><span class="sxs-lookup"><span data-stu-id="92074-p103">Regardless of how you manage vital Office 365 network traffic, Office 365 requires Internet connectivity. Other network endpoints where connectivity is required are listed at [Additional endpoints not included in the Office 365 IP Address and URL Web service](additional-office365-ip-addresses-and-urls.md)</span></span>

<span data-ttu-id="92074-p104">您如何使用 Office 365 网络终结点将取决于您的企业组织网络体系结构。本文概述了几种企业网络体系结构可以与 Office 365 IP 地址和 Url 集成的方式。选择要信任的网络请求的最简单方式是使用支持自动在每个办公地点的 Office 365 配置的 SDWAN 设备。</span><span class="sxs-lookup"><span data-stu-id="92074-p104">How you use the Office 365 network endpoints will depend on your enterprise organization network architecture. This article outlines several ways that enterprise network architectures can integrate with Office 365 IP addresses and URLs. The easiest way to choose which network requests to trust is to use SDWAN devices that support automated Office 365 configuration at each of your office locations.</span></span> 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a><span data-ttu-id="92074-117">重要 Office 365 网络流量的本地分支出口的 SDWAN</span><span class="sxs-lookup"><span data-stu-id="92074-117">SDWAN for local branch egress of vital Office 365 network traffic</span></span>

<span data-ttu-id="92074-p105">在每个分支机构位置，您可以提供配置路由流量的终结点或优化 Office 365 优化类别，并允许类别，直接向 Microsoft 的网络 SDWAN 设备。包括本地 datacenter 流量、 常规 Internet 网站流量和到 Office 365 默认类别终结点的流量其他网络流量发送给您有更大的网络外围的另一个位置。</span><span class="sxs-lookup"><span data-stu-id="92074-p105">At each branch office location, you can provide an SDWAN device that is configured to route traffic for Office 365 Optimize category of endpoints, or Optimize and Allow categories, directly to Microsoft's network. Other network traffic including on-premises datacenter traffic, general Internet web sites traffic, and traffic to Office 365 Default category endpoints is sent to another location where you have a more substantial network perimeter.</span></span>

<span data-ttu-id="92074-p106">Microsoft 正在与 SDWAN 提供程序，以启用自动的配置。有关详细信息，请参阅[Office 365 网络合作伙伴计划](office-365-networking-partner-program.md)。</span><span class="sxs-lookup"><span data-stu-id="92074-p106">Microsoft is working with SDWAN providers to enable automated configuration. For more information, see [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span>

<span data-ttu-id="92074-122"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="92074-122"></span></span>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a><span data-ttu-id="92074-123">用于 PAC 文件的重要的 Office 365 流量直接路由</span><span class="sxs-lookup"><span data-stu-id="92074-123">Use a PAC file for direct routing of vital Office 365 traffic</span></span>

<span data-ttu-id="92074-p107">使用 PAC 或 WPAD 文件管理网络请求与 Office 365 相关联，但不具有一个 IP 地址。通过代理服务器或外围设备发送的典型网络请求增加延迟。SSL 中断和检查创建的最大延迟，而其他服务如代理身份验证和声誉查找可能会导致性能不佳和错误的用户体验。此外，这些外围网络设备需要足够的容量来处理的所有网络连接请求。我们建议绕过代理服务器或检查设备的直接 Office 365 网络请求。</span><span class="sxs-lookup"><span data-stu-id="92074-p107">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address. Typical network requests that are sent through a proxy or perimeter device increase latency. While SSL Break and Inspect creates the largest latency, other services such as proxy authentication and reputation lookup can cause poor performance and a bad user experience. Additionally, these perimeter network devices need enough capacity to process all of the network connection requests. We recommend bypassing your proxy or inspection devices for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="92074-p108">[PowerShell 库 Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile)是从 Office 365 IP 地址和 URL Web 服务中读取的最新的网络终结点，并创建一个示例 PAC 文件的 PowerShell 脚本。您可以修改该脚本，以便它可以与您现有的 PAC 文件管理集成。</span><span class="sxs-lookup"><span data-stu-id="92074-p108">[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the Office 365 IP Address and URL Web service and creates a sample PAC file. You can modify the script so that it integrates with your existing PAC file management.</span></span> 

![通过防火墙和代理连接到 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

<span data-ttu-id="92074-132">**图 1-简单企业网络外围**</span><span class="sxs-lookup"><span data-stu-id="92074-132">**Figure 1 - Simple enterprise network perimeter**</span></span>

<span data-ttu-id="92074-p109">PAC 文件部署到 web 浏览器在图 1 中的点 1。使用重要的 Office 365 网络流量的直接出口 PAC 文件，还需要在网络外围防火墙上允许连接到这些 Url 后面的 IP 地址。这通过获取 PAC 文件中的指定相同 Office 365 终结点类别的 IP 地址和创建防火墙 Acl 基于这些地址。防火墙是图 1 中的点 3。</span><span class="sxs-lookup"><span data-stu-id="92074-p109">The PAC file is deployed to web browsers at point 1 in Figure 1. When using a PAC file for direct egress of vital Office 365 network traffic, you also need to allow connectivity to the IP addresses behind these URLs on your network perimeter firewall. This is done by fetching the IP addresses for the same Office 365 endpoint categories as specified in the PAC file and creating firewall ACLs based on those addresses. The firewall is point 3 in Figure 1.</span></span> 

<span data-ttu-id="92074-p110">单独如果您选择仅执行直接路由优化类别终结点发送到代理服务器的类别终结点时所需的代理服务器，以绕过进一步处理列出任何所需允许。例如，SSL 中断检查和代理身份验证与不兼容的优化和允许类别终结点。代理服务器就是图 1 中的点 2。</span><span class="sxs-lookup"><span data-stu-id="92074-p110">Separately if you choose to only do direct routing for the Optimize category endpoints, any required Allow category endpoints that you send to the proxy server will need to be listed in the proxy server to bypass further processing. For example, SSL break and Inspect and Proxy Authentication are incompatible with both the Optimize and Allow category endpoints. The proxy server is point 2 in Figure 1.</span></span>

<span data-ttu-id="92074-p111">常见配置是允许不处理来自点击代理服务器的 Office 365 网络流量的目标 IP 地址的代理服务器的所有出站通信。有关 SSL 中断和检查问题的信息，请参阅[使用第三方网络设备或在 Office 365 通信解决方案](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)。</span><span class="sxs-lookup"><span data-stu-id="92074-p111">The common configuration is to permit without processing all outbound traffic from the proxy server for the destination IP addresses for Office 365 network traffic that hits the proxy server. For information about issues with SSL Break and Inspect, see [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).</span></span>

<span data-ttu-id="92074-142">有两种类型的 Get PacFile 脚本将生成的 PAC 文件。</span><span class="sxs-lookup"><span data-stu-id="92074-142">There are two types of PAC files that the Get-PacFile script will generate.</span></span>

|<span data-ttu-id="92074-143">**类型**</span><span class="sxs-lookup"><span data-stu-id="92074-143">**Type**</span></span>|<span data-ttu-id="92074-144">**说明**</span><span class="sxs-lookup"><span data-stu-id="92074-144">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="92074-145">**1**</span><span class="sxs-lookup"><span data-stu-id="92074-145">**1**</span></span> <br/> |<span data-ttu-id="92074-146">将优化终结点流量直接和其他内容发送到的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="92074-146">Send Optimize endpoint traffic direct and everything else to the proxy server.</span></span> <br/> |
|<span data-ttu-id="92074-147">**2**</span><span class="sxs-lookup"><span data-stu-id="92074-147">**2**</span></span> <br/> |<span data-ttu-id="92074-p112">将优化和允许直接的终结点流量以及所有其他人发送到的代理服务器。此类型还可以用于发送所有支持 ExpressRoute ExpressRoute 网段的 Office 365 流量以及所有其他代理服务器。</span><span class="sxs-lookup"><span data-stu-id="92074-p112">Send Optimize and Allow endpoint traffic direct and everything else to the proxy server. This type can also be used to send all supported ExpressRoute for Office 365 traffic to ExpressRoute network segments and everything else to the proxy server.</span></span> <br/> |

<span data-ttu-id="92074-150">下面是调用 PowerShell 脚本的简单示例：</span><span class="sxs-lookup"><span data-stu-id="92074-150">Here's a simple example of calling the PowerShell script:</span></span>

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

<span data-ttu-id="92074-151">有许多参数可以传递给脚本：</span><span class="sxs-lookup"><span data-stu-id="92074-151">There are a number of parameters you can pass to the script:</span></span>

|<span data-ttu-id="92074-152">**参数**</span><span class="sxs-lookup"><span data-stu-id="92074-152">**Parameter**</span></span>|<span data-ttu-id="92074-153">**说明**</span><span class="sxs-lookup"><span data-stu-id="92074-153">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="92074-154">**ClientRequestId**</span><span class="sxs-lookup"><span data-stu-id="92074-154">**ClientRequestId**</span></span> <br/> |<span data-ttu-id="92074-155">这是必需的和 GUID 传递到 web 服务值，该值代表发起呼叫的客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="92074-155">This is required and is a GUID passed to the web service that represents the client machine making the call.</span></span> <br/> |
|<span data-ttu-id="92074-156">**Instance**</span><span class="sxs-lookup"><span data-stu-id="92074-156">**Instance**</span></span> <br/> |<span data-ttu-id="92074-p113">Office 365 服务实例，它默认为全球。也将传递到 web 服务。</span><span class="sxs-lookup"><span data-stu-id="92074-p113">The Office 365 service instance which defaults to Worldwide. Also passed to the web service.</span></span> <br/> |
|<span data-ttu-id="92074-159">**TenantName**</span><span class="sxs-lookup"><span data-stu-id="92074-159">**TenantName**</span></span> <br/> |<span data-ttu-id="92074-p114">您的 Office 365 租户名称。传递给 web 服务并用作某些 Office 365 Url 中的可替换参数。</span><span class="sxs-lookup"><span data-stu-id="92074-p114">Your Office 365 tenant name. Passed to the web service and used as a replaceable parameter in some Office 365 URLs.</span></span> <br/> |
|<span data-ttu-id="92074-162">**类型**</span><span class="sxs-lookup"><span data-stu-id="92074-162">**Type**</span></span> <br/> |<span data-ttu-id="92074-163">您想要生成的代理 PAC 文件类型。</span><span class="sxs-lookup"><span data-stu-id="92074-163">The type of the proxy PAC file that you want to generate.</span></span> <br/> |

<span data-ttu-id="92074-164">下面是调用带有其他参数的 PowerShell 脚本的另一个示例。</span><span class="sxs-lookup"><span data-stu-id="92074-164">Here's another example of calling the PowerShell script with additional parameters.</span></span>

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a><span data-ttu-id="92074-165">代理服务器绕过的 Office 365 网络流量的处理</span><span class="sxs-lookup"><span data-stu-id="92074-165">Proxy server bypass processing of Office 365 network traffic</span></span> 

<span data-ttu-id="92074-p115">其中 PAC 文件未用于直接出站流量，仍要绕过通过配置您的代理服务器的外围网络上的处理。[Office 365 网络合作伙伴计划](office-365-networking-partner-program.md)中所述，某些代理服务器供应商已启用此自动的配置。</span><span class="sxs-lookup"><span data-stu-id="92074-p115">Where PAC files are not used for direct outbound traffic, you still want to bypass processing on your network perimeter by configuring your proxy server. Some proxy server vendors have enabled automated configuration of this as described in the [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span> 

<span data-ttu-id="92074-p116">如果手动执行这需要获得优化和允许来自 Office 365 IP 地址和 URL Web 服务的终结点类别数据代理服务器配置为绕过处理这些。非常重要的优化避免 SSL 中断和检查和代理服务器身份验证并允许类别终结点。</span><span class="sxs-lookup"><span data-stu-id="92074-p116">If you are doing this manually you will need to obtain the Optimize and Allow endpoint category data from the Office 365 IP Address and URL Web Service and configure your proxy server to bypass processing for these. It is important to avoid SSL Break and Inspect and Proxy Authentication for the Optimize and Allow category endpoints.</span></span> 
  
<span data-ttu-id="92074-170"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="92074-170"></span></span>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a><span data-ttu-id="92074-171">变更管理 Office 365 IP 地址和 Url</span><span class="sxs-lookup"><span data-stu-id="92074-171">Change management for Office 365 IP addresses and URLs</span></span>

<span data-ttu-id="92074-p117">除了选择适当配置网络外围，很重要，采用更改管理过程的 Office 365 终结点。定期更改这些终结点，如果您不管理所做的更改，您可以结尾阻止用户或性能不佳后一个新的 IP 地址或 URL 添加。</span><span class="sxs-lookup"><span data-stu-id="92074-p117">In addition to selecting appropriate configuration for your network perimeter, it is critical that you adopt a change management process for Office 365 endpoints. These endpoints change regularly and if you do not manage the changes, you can end up with users blocked or with poor performance after a new IP address or URL is added.</span></span> 

<span data-ttu-id="92074-p118">每月的最后一天附近通常发布到 Office 365 IP 地址和 Url 的更改。有时发生的更改将发布该由于操作的计划、 支持或安全要求之外。</span><span class="sxs-lookup"><span data-stu-id="92074-p118">Changes to the Office 365 IP addresses and URLs are usually published near the last day of each month. Sometimes a change will be published outside of that schedule due to operational, support, or security requirements.</span></span>

<span data-ttu-id="92074-p119">发布更改时，需要执行操作，因为已添加的 IP 地址或 URL，您应该会收到 30 天通知从该终结点上的 Office 365 服务之前，我们发布更改的时间。虽然我们的目标此通知段，它始终可能不可能由于操作、 支持或安全要求。不需要立即操作维护连接，例如更改删除 IP 地址或 Url 或更少的重大更改，不包括提前通知。提供了哪些通知，则无论我们列出每次更改的预期的服务活动日期。</span><span class="sxs-lookup"><span data-stu-id="92074-p119">When a change is published that requires you to act because an IP address or URL was added, you should expect to receive 30 days notice from the time we publish the change until there is an Office 365 service on that endpoint. Although we aim for this notification period, it may not always be possible due to operational, support, or security requirements. Changes that do not require immediate action to maintain connectivity, such as removed IP addresses or URLs or less significant changes, do not include advance notification. Regardless of what notification is provided, we list the expected service active date for each change.</span></span>

### <a name="change-notification-using-the-web-service"></a><span data-ttu-id="92074-180">使用 Web 服务的更改通知</span><span class="sxs-lookup"><span data-stu-id="92074-180">Change notification using the Web Service</span></span>

<span data-ttu-id="92074-p120">您可以使用 Office 365 IP 地址和 URL Web 服务获取更改通知。我们建议您调用 **/version** web 方法每小时一次以检查要用于连接到 Office 365 的终结点的版本。如果已在使用中的版本相比，此版本发生更改，您应从 **/endpoints** web 方法获取最新的终结点数据和 （可选） 从 **/changes** web 方法获取差异。不需要调用 **/endpoints**或 **/changes** web 方法，如果已对您找到的版本的任何更改。</span><span class="sxs-lookup"><span data-stu-id="92074-p120">You can use the Office 365 IP Address and URL Web Service to get change notification. We recommend you call the **/version** web method once an hour to check the version of the endpoints that you are using to connect to Office 365. If this version changes when compared to the version that you have in use, then you should get the latest endpoint data from the **/endpoints** web method and optionally get the differences from the **/changes** web method. It is not necessary to call the **/endpoints** or **/changes** web methods if there has not been any change to the version you found.</span></span> 

<span data-ttu-id="92074-185">有关详细信息，请参阅[Office 365 IP 地址和 Web 服务 URL](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="92074-185">For more information, see [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-using-rss-feeds"></a><span data-ttu-id="92074-186">使用 RSS 源的更改通知</span><span class="sxs-lookup"><span data-stu-id="92074-186">Change notification using RSS feeds</span></span>

<span data-ttu-id="92074-p121">Office 365 IP 地址和 URL Web 服务提供了您可以在 Outlook 中订阅 RSS 源。有指向每个 IP 地址的 Office 365 服务实例特定页上的 RSS Url 和 Url。有关详细信息，请参阅[Office 365 IP 地址和 Web 服务 URL](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="92074-p121">The Office 365 IP Address and URL Web Service provides an RSS feed that you can subscribe to in Outlook. There are links to the RSS URLs on each of the Office 365 service instance-specific pages for the IP addresses and URLs. For more information, see [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a><span data-ttu-id="92074-190">更改通知和审批查看使用 Microsoft 流</span><span class="sxs-lookup"><span data-stu-id="92074-190">Change notification and approval review using Microsoft Flow</span></span>

<span data-ttu-id="92074-p122">我们知道您通过每个月的网络终结点更改可能仍然需要手动处理。Microsoft 流可用于创建通知您通过电子邮件并 （可选） 在运行更改审批过程，在 Office 365 网络终结点都发生更改时的流程。完成检查后，您可以自动电子邮件向防火墙和代理服务器管理团队的更改的流。</span><span class="sxs-lookup"><span data-stu-id="92074-p122">We understand that you might still require manual processing for network endpoint changes that come through each month. You can use Microsoft Flow to create a flow that notifies you by email and optionally runs an approval process for changes when Office 365 network endpoints have changes. Once review is completed, you can have the flow automatically email the changes to your firewall and proxy server management team.</span></span> 

<span data-ttu-id="92074-194">有关 Microsoft 流示例和模板的信息，请参阅[使用 Microsoft 流可以接收电子邮件的 Office 365 IP 地址和 Url 的更改](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)</span><span class="sxs-lookup"><span data-stu-id="92074-194">For information about a Microsoft Flow sample and template, see [Use Microsoft Flow to receive an email for changes to Office 365 IP addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)</span></span>
  
<span data-ttu-id="92074-195"><a name="FAQ"> </a></span><span class="sxs-lookup"><span data-stu-id="92074-195"></span></span>
## <a name="office-365-network-endpoints-faq"></a><span data-ttu-id="92074-196">Office 365 网络终结点常见问题</span><span class="sxs-lookup"><span data-stu-id="92074-196">Office 365 network endpoints FAQ</span></span>

<span data-ttu-id="92074-197">常见问题： 管理员有关 Office 365 连接问题：</span><span class="sxs-lookup"><span data-stu-id="92074-197">Frequently-asked administrator questions about Office 365 connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="92074-198">如何提交问题？</span><span class="sxs-lookup"><span data-stu-id="92074-198">How do I submit a question?</span></span>

<span data-ttu-id="92074-p123">单击位于底部以指示文章或不是非常有用的链接，并提交任何其他问题。我们监控反馈，使用最常见问题进行了更新此处的问题。</span><span class="sxs-lookup"><span data-stu-id="92074-p123">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="92074-201">如何确定我租户的位置？</span><span class="sxs-lookup"><span data-stu-id="92074-201">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="92074-202">使用我们的[数据中心映射](http://aka.ms/datamaps)最佳确定**租户位置**。</span><span class="sxs-lookup"><span data-stu-id="92074-202">**Tenant location** is best determined using our [datacenter map](http://aka.ms/datamaps).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="92074-203">我我对等适当地与 Microsoft？</span><span class="sxs-lookup"><span data-stu-id="92074-203">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="92074-204">[与 Microsoft 对等](https://www.microsoft.com/peering)更加详细地描述了**Peering 位置**。</span><span class="sxs-lookup"><span data-stu-id="92074-204">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="92074-p124">具有超过 2500 ISP 对等关系全局和 70 磅，从您的网络中获取与我们应该是状态的无缝。吧花几分钟，确保您的 ISP 的对等关系最最佳，[下面是一些示例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)的良好和不好对等 hand 利弊权衡到我们网络。</span><span class="sxs-lookup"><span data-stu-id="92074-p124">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="92074-207">我不在发布列表中查看网络请求到 IP 地址，我需要提供对这些访问吗？</span><span class="sxs-lookup"><span data-stu-id="92074-207">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="92074-208"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="92074-208"></span></span>

<span data-ttu-id="92074-p125">我们仅向您应与直接路由的 Office 365 服务器的 IP 地址。这不是您将看到网络请求的所有 IP 地址的完整列表。您将看到对 Microsoft 和第三方拥有、 未发布，IP 地址的网络请求。动态生成或托管方式的更改时，它们阻止及时通知这些 IP 地址。如果您的防火墙无法允许访问基于这些网络请求的 Fqdn，使用 PAC 或 WPAD 文件管理请求。</span><span class="sxs-lookup"><span data-stu-id="92074-p125">We only provide IP addresses for the Office 365 servers you should route directly to. This isn't a comprehensive list of all IP addresses you'll see network requests for. You will see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="92074-214">请参阅 IP 与 Office 365 上所需的详细信息？</span><span class="sxs-lookup"><span data-stu-id="92074-214">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="92074-215">检查使用[CIDR 计算器](http://jodies.de/ipcalc)的较大发布区域中是否包括 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="92074-215">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
2. <span data-ttu-id="92074-p126">请参阅合作伙伴是否拥有[whois 查询](https://dnsquery.org/)与 IP。如果是 Microsoft 拥有，可能为内部伙伴。</span><span class="sxs-lookup"><span data-stu-id="92074-p126">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
3. <span data-ttu-id="92074-p127">检查证书，在浏览器中连接到 IP 地址使用*HTTPS://\<ip 地址\>*，检查证书以了解哪些域将关联的 IP 地址上列出的域。如果它是 Microsoft 拥有 IP 地址，不在列表中的 Office 365 IP 地址，它是可能的 IP 地址是与 Microsoft CDN 如*MSOCDN.NET*或没有 IP 的已发布信息的另一个 Microsoft 域相关联。如果找到此证书的域是我们声明列出的 IP 地址，请让我们知道。</span><span class="sxs-lookup"><span data-stu-id="92074-p127">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span>

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="92074-221">为什么我看如 nsatc.net 或 akadns.net 中的 Microsoft 域名的名称？</span><span class="sxs-lookup"><span data-stu-id="92074-221">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="92074-222"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="92074-222"></span></span>

<span data-ttu-id="92074-p128">Office 365 和其他 Microsoft 服务使用多个第三方服务，如 Akamai 和 MarkMonitor 来提高 Office 365 体验。若要保留为您提供最佳体验，我们可以更改这些服务将来。这样，我们通常发布此问题的第三方拥有的域、 record 或 IP 地址的 CNAME 记录。第三方域可能承载内容，例如 CDN 或它们可能承载服务，如地理流量管理服务。当您看到这些第三方的连接时，正在重定向或参考，不从客户端的初始请求的窗体。有些客户需要确保这种形式的参考和重定向允许通过显式添加潜在 Fqdn 第三方服务的长列表可能使用。</span><span class="sxs-lookup"><span data-stu-id="92074-p128">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="92074-p129">在任何时候恕服务列表中。当前正在使用的服务的一些包括：</span><span class="sxs-lookup"><span data-stu-id="92074-p129">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="92074-p130">当您看到包括的请求时，正在使用[MarkMonitor](https://www.markmonitor.com/) \* \*。 nsatc.net\* 。此服务提供域名称保护和监控防御恶意行为。</span><span class="sxs-lookup"><span data-stu-id="92074-p130">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span>
  
<span data-ttu-id="92074-p131">当您看到对请求[ExactTarget](https://www.marketingcloud.com/)正在使用*\*。 exacttarget.com* 。此服务提供电子邮件链接管理和监视针对恶意行为。</span><span class="sxs-lookup"><span data-stu-id="92074-p131">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span>
  
<span data-ttu-id="92074-p132">当您看到包含以下 Fqdn 之一的请求， [Akamai](https://www.akamai.com/)正在使用中。此服务提供了地理 DNS 和内容交付网络服务。</span><span class="sxs-lookup"><span data-stu-id="92074-p132">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span>
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a><span data-ttu-id="92074-237">我必须具有的最小的连接可能适用于 Office 365</span><span class="sxs-lookup"><span data-stu-id="92074-237">I have to have the minimum connectivity possible for Office 365</span></span>
<span data-ttu-id="92074-238"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="92074-238"></span></span>

<span data-ttu-id="92074-p133">Office 365 是一套函数构建通过 internet 的服务、 可靠性和可用性承诺基于许多标准 internet 服务不可用。例如，如 DNS、 CRL 和 Cdn 的标准 internet 服务必须可访问以使用 Office 365，就像他们必须使用最先进的 internet 服务，可访问。</span><span class="sxs-lookup"><span data-stu-id="92074-p133">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>

<span data-ttu-id="92074-p134">在 Office 365 套件细分为主要服务领域。可以有选择地启用这些连接，并且没有公用区域，它是所有依赖项并始终是必需的。</span><span class="sxs-lookup"><span data-stu-id="92074-p134">The Office 365 suite is broken down into major service areas. These can be selectively enabled for connectivity and there is a Common area which is a dependency for all and is always required.</span></span>

|<span data-ttu-id="92074-243">**服务区域**</span><span class="sxs-lookup"><span data-stu-id="92074-243">**Service Area**</span></span>|<span data-ttu-id="92074-244">**说明**</span><span class="sxs-lookup"><span data-stu-id="92074-244">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="92074-245">**Exchange**</span><span class="sxs-lookup"><span data-stu-id="92074-245">**Exchange**</span></span> <br/> |<span data-ttu-id="92074-246">Exchange Online 和 Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="92074-246">Exchange Online and Exchange Online Protection</span></span> <br/> |
|<span data-ttu-id="92074-247">**SharePoint**</span><span class="sxs-lookup"><span data-stu-id="92074-247">**SharePoint**</span></span> <br/> |<span data-ttu-id="92074-248">SharePoint Online 和 OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="92074-248">SharePoint Online and OneDrive for Business</span></span> <br/> |
|<span data-ttu-id="92074-249">**Skype**</span><span class="sxs-lookup"><span data-stu-id="92074-249">**Skype**</span></span> <br/> |<span data-ttu-id="92074-250">商业和 Microsoft 团队的 Skype</span><span class="sxs-lookup"><span data-stu-id="92074-250">Skype for Business and Microsoft Teams</span></span> <br/> |
|<span data-ttu-id="92074-251">**常见**</span><span class="sxs-lookup"><span data-stu-id="92074-251">**Common**</span></span> <br/> |<span data-ttu-id="92074-252">Office 365 Pro Plus Office Online、 Azure AD 和其他公共网络终结点</span><span class="sxs-lookup"><span data-stu-id="92074-252">Office 365 Pro Plus, Office Online, Azure AD and other common network endpoints</span></span> <br/> |

<span data-ttu-id="92074-p135">除了基本 internet 服务，可以使用第三方服务仅用于将功能集成。虽然这些所需的集成，它们被标记为可选这意味着服务的核心功能仍可正常工作，如果终结点无法访问 Office 365 终结点文章中。任何网络终结点，需要它将具有所需属性设置为 true。这是可选的任何网络终结点将具有 required 的属性设置为 false，并且 notes 属性将详细介绍缺少的功能，则应产生预期如果阻止连接。</span><span class="sxs-lookup"><span data-stu-id="92074-p135">In addition to basic internet services, there are third-party services that are only used to integrate functionality. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible. Any network endpoint which is required will have the required attribute set to true. Any network endpoint which is optional will have the required attribute set to false and the notes attribute will detail the missing functionality you should expect if connectivity is blocked.</span></span>
  
<span data-ttu-id="92074-257">如果您正在尝试使用 Office 365 和第三方服务就不会访问发现您需要[确保所有标记必需或可选本文中的 Fqdn 允许通过代理和防火墙](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="92074-257">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="92074-258">如何阻止访问 Microsoft 的使用者服务？</span><span class="sxs-lookup"><span data-stu-id="92074-258">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="92074-259"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="92074-259"></span></span>

<span data-ttu-id="92074-p136">限制对我们的使用者服务访问应该执行需要您自担风险，阻止使用者服务仅可靠的方式是限制对*login.live.com* FQDN 的访问。广泛的服务，包括非消费服务，例如 MSDN、 TechNet 和其他人使用此 FQDN。限制对此 FQDN 访问可能会导致需要还包括与这些服务关联的网络请求规则例外情况。</span><span class="sxs-lookup"><span data-stu-id="92074-p136">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span>
  
<span data-ttu-id="92074-263">请记住，阻止访问单独的 Microsoft 客户服务不会阻止的人在您的网络到使用 Office 365 租户或其他服务的 exfiltrate 信息。</span><span class="sxs-lookup"><span data-stu-id="92074-263">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="92074-264">相关主题</span><span class="sxs-lookup"><span data-stu-id="92074-264">Related Topics</span></span>

[<span data-ttu-id="92074-265">Office 365 IP 地址和 URL Web 服务</span><span class="sxs-lookup"><span data-stu-id="92074-265">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="92074-266">Microsoft Azure 数据中心 IP 范围</span><span class="sxs-lookup"><span data-stu-id="92074-266">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="92074-267">Microsoft 公共 IP 空间</span><span class="sxs-lookup"><span data-stu-id="92074-267">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="92074-268">Microsoft Intune 的网络基础结构要求</span><span class="sxs-lookup"><span data-stu-id="92074-268">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="92074-269">Power BI 和 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="92074-269">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="92074-270">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="92074-270">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="92074-271">管理 ExpressRoute for Office 365 连接</span><span class="sxs-lookup"><span data-stu-id="92074-271">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="92074-272">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="92074-272">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
