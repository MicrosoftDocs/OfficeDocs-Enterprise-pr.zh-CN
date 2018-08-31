---
title: 管理 ExpressRoute for Office 365 连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Office 365 ExpressRoute 提供备用的路由路径，无须所有通信出口到 internet 访问许多 Office 365 服务。虽然仍需要 internet 连接到 Office 365，但 Microsoft 向您的网络通过 BGP 公布的特定路由进行直接 ExpressRoute 电路首选除非有网络中的其他配置。要配置管理此路由包含的三个公共区域前缀筛选、 安全性和合规性。
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539592"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a><span data-ttu-id="d37fe-105">管理 ExpressRoute for Office 365 连接</span><span class="sxs-lookup"><span data-stu-id="d37fe-105">Managing ExpressRoute for Office 365 connectivity</span></span>

<span data-ttu-id="d37fe-p102">Office 365 ExpressRoute 提供备用的路由路径，无须所有通信出口到 internet 访问许多 Office 365 服务。虽然仍需要 internet 连接到 Office 365，但 Microsoft 向您的网络通过 BGP 公布的特定路由进行直接 ExpressRoute 电路首选除非有网络中的其他配置。要配置管理此路由包含的三个公共区域前缀筛选、 安全性和合规性。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p102">ExpressRoute for Office 365 offers an alternative routing path to reach many Office 365 services without needing all traffic to egress to the internet. Although the internet connection to Office 365 is still needed, the specific routes that Microsoft advertises through BGP to your network make the direct ExpressRoute circuit preferred unless there are other configurations in your network. The three common areas you may want to configure to manage this routing include prefix filtering, security, and compliance.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d37fe-p103">Microsoft 更改 Microsoft Peering 路由域的 Azure ExpressRoute 经过审阅的方式。启动 2017 年 7 月 31，所有 Azure ExpressRoute 客户可以都启用 Microsoft Peering Azure 管理控制台中直接或通过 PowerShell 自定义。启用后 Microsoft Peering，任何客户可以创建路由筛选器以接收 BGP 路由广告 Dynamics 365 客户服务应用程序 （以前称为，CRM Online）。客户需要为 Office 365 的 Azure ExpressRoute 必须从 Microsoft 获取审阅，他们可以针对 Office 365 中创建路由筛选器之前。请联系您的 Microsoft 帐户团队，若要了解有关如何启用 Office 365 ExpressRoute 审阅请求。尝试 Office 365 中创建路由筛选器的未经授权的订阅将收到[错误消息](https://support.microsoft.com/kb/3181709)</span><span class="sxs-lookup"><span data-stu-id="d37fe-p103">Microsoft changed how the Microsoft Peering routing domain is reviewed for Azure ExpressRoute. Starting July 31st, 2017, all Azure ExpressRoute customers can enable Microsoft Peering directly from the Azure Administrative console or via PowerShell. After enabling Microsoft Peering, any customer can create route filters to receive BGP route advertisements for Dynamics 365 Customer Engagement applications (Formerly known as CRM Online). Customers needing Azure ExpressRoute for Office 365 must obtain review from Microsoft before they can create route filters for Office 365. Please contact your Microsoft Account team to learn about how to request a review for enabling Office 365 ExpressRoute. Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709)</span></span>
  
## <a name="prefix-filtering"></a><span data-ttu-id="d37fe-115">前缀筛选</span><span class="sxs-lookup"><span data-stu-id="d37fe-115">Prefix filtering</span></span>

<span data-ttu-id="d37fe-p104">Microsoft 建议客户接受所有 BGP 路由，如 microsoft 播发、 提供的路由经过严格的检查和验证过程，将删除添加了煜 ・ ｣ ｡ 任何好处。ExpressRoute 本身提供建议的控件，如 IP 前缀所有权、 完整性和规模-与任何筛选在客户端的入站路由。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p104">Microsoft recommends that customers accept all BGP routes as advertised from Microsoft, the routes provided undergo a rigorous review and validation process removing any benefits to added scrutiny. ExpressRoute natively offers the recommended controls such as IP prefix ownership, integrity, and scale - with no inbound route filtering on the customer side.</span></span>
  
<span data-ttu-id="d37fe-p105">如果您需要路由所有权的其他验证跨 ExpressRoute 公共对等，您可以检查根据表示[Microsoft 的公共 IP 范围](https://www.microsoft.com/download/details.aspx?id=53602)的所有 IPv4 和 IPv6 IP 前缀的列表的播发的路由。这些区域将覆盖完整的 Microsoft 地址空间和更改不频繁，提供了可靠范围进行筛选的组，还为那些担心非 Microsoft 拥有路由到泄漏的客户提供了其他保护其环境。在事件发生更改时，将所做的月 1 日和每次更新该文件时，将更改页上的**详细信息**部分的版本号。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p105">If you require additional validation of route ownership across ExpressRoute public peering, you can check the advertised routes against the list of all IPv4 and IPv6 IP prefixes that represent [Microsoft's public IP ranges](https://www.microsoft.com/download/details.aspx?id=53602). These ranges cover the full Microsoft address space and change infrequently, providing a reliable set of ranges to filter against that also provides additional protection to customers who are concerned about non-Microsoft owned routes leaking into their environment. In the event there is a change, it will be made on the 1st of the month and the version number in the **details** section of the page will change every time the file is updated.</span></span>
  
<span data-ttu-id="d37fe-p106">有多种原因，以避免使用[Office 365 Url 和 IP 地址范围](https://aka.ms/o365endpoints)的用于生成前缀筛选器列表。其中包括：</span><span class="sxs-lookup"><span data-stu-id="d37fe-p106">There are a number of reasons to avoid the use of the [Office 365 URLs and IP address ranges](https://aka.ms/o365endpoints) for generating prefix filter lists. Including the following:</span></span>
  
- <span data-ttu-id="d37fe-123">Office 365 IP 前缀经过大量经常更改。</span><span class="sxs-lookup"><span data-stu-id="d37fe-123">The Office 365 IP prefixes undergo lots of changes on a frequent basis.</span></span>

- <span data-ttu-id="d37fe-124">针对管理防火墙设计范围的 Office 365 Url 和 IP 地址允许列表和代理基础结构，不路由。</span><span class="sxs-lookup"><span data-stu-id="d37fe-124">The Office 365 URLs and IP address ranges are designed for managing firewall allow lists and Proxy infrastructure, not routing.</span></span>

- <span data-ttu-id="d37fe-125">Office 365 Url 和 IP 地址范围不包括 ミ ミ 动 ExpressRoute 连接范围其他 Microsoft 服务。</span><span class="sxs-lookup"><span data-stu-id="d37fe-125">The Office 365 URLs and IP address ranges do not cover other Microsoft services that may be in scope for your ExpressRoute connections.</span></span>

<span data-ttu-id="d37fe-126">| |</span><span class="sxs-lookup"><span data-stu-id="d37fe-126"></span></span>
|<span data-ttu-id="d37fe-127">**选项**</span><span class="sxs-lookup"><span data-stu-id="d37fe-127">**Option**</span></span>|<span data-ttu-id="d37fe-128">**复杂度**</span><span class="sxs-lookup"><span data-stu-id="d37fe-128">**Complexity**</span></span>|<span data-ttu-id="d37fe-129">**更改控件**</span><span class="sxs-lookup"><span data-stu-id="d37fe-129">**Change Control**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d37fe-130">接受所有 Microsoft 路由</span><span class="sxs-lookup"><span data-stu-id="d37fe-130">Accept all Microsoft routes</span></span>  <br/> |<span data-ttu-id="d37fe-131">**低：** 客户依赖于 Microsoft 控件，以确保正确拥有的所有路由。</span><span class="sxs-lookup"><span data-stu-id="d37fe-131">**Low:** Customer relies upon Microsoft controls to ensure all routes are properly owned.</span></span>  <br/> |<span data-ttu-id="d37fe-132">无</span><span class="sxs-lookup"><span data-stu-id="d37fe-132">None</span></span>  <br/> |
|<span data-ttu-id="d37fe-133">筛选器 Microsoft 拥有 supernets</span><span class="sxs-lookup"><span data-stu-id="d37fe-133">Filter Microsoft owned supernets</span></span>  <br/> |<span data-ttu-id="d37fe-134">**中等：** 客户可实现汇总的前缀筛选器列表，以允许仅 Microsoft 拥有路由。</span><span class="sxs-lookup"><span data-stu-id="d37fe-134">**Medium:** Customer implements summarized prefix filter lists to allow only Microsoft owned routes.</span></span>  <br/> |<span data-ttu-id="d37fe-135">客户必须确保非频繁更新会反映在路由筛选器。</span><span class="sxs-lookup"><span data-stu-id="d37fe-135">Customers must ensure the infrequent updates are reflected in route filters.</span></span>  <br/> |
|<span data-ttu-id="d37fe-136">筛选 Office 365 IP 范围</span><span class="sxs-lookup"><span data-stu-id="d37fe-136">Filter Office 365 IP ranges</span></span>  <br/> [!CAUTION] <span data-ttu-id="d37fe-137">不建议</span><span class="sxs-lookup"><span data-stu-id="d37fe-137">Not-Recommended</span></span>
|<span data-ttu-id="d37fe-138">**高：** 客户的筛选器基于定义的 Office 365 IP 前缀的路由。</span><span class="sxs-lookup"><span data-stu-id="d37fe-138">**High:** Customer filters routes based on defined Office 365 IP prefixes.</span></span>  <br/> |<span data-ttu-id="d37fe-139">客户必须实现的每月更新稳固更改管理过程。</span><span class="sxs-lookup"><span data-stu-id="d37fe-139">Customers must implement a robust change management process for the monthly updates.</span></span>  <br/> [!CAUTION]<span data-ttu-id="d37fe-p107">此解决方案要求重大持续更改。在时间很可能会导致服务中断中未实施的更改。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p107"> This solution requires significant on-going changes. Changes not implemented in time will likely result in a service outage.</span></span>   |

<span data-ttu-id="d37fe-p108">连接到 Office 365 使用 Azure ExpressRoute 基于特定的 IP 子网表示其中部署 Office 365 终结点的网络 BGP 广告。Office 365 和数组成 Office 365 服务的全局性质，由于客户常常需要管理他们的网络的参与者接受广告。如果您担心与公布到您的环境的前缀的号码， [BGP 社区](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)功能允许您筛选公布到一组特定的 Office 365 服务。此功能现在处于预览。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p108">Connecting to Office 365 using Azure ExpressRoute is based on BGP advertisements of specific IP subnets that represent networks where Office 365 endpoints are deployed. Due to the global nature of Office 365 and the number of services that make up Office 365, customers often have a need to manage the advertisements they accept on their network. If you're concerned with number of prefixes advertised into your environment, the [BGP community](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) feature allows you to filter the advertisements to a specific set of Office 365 services. This feature is now in preview.</span></span>
  
<span data-ttu-id="d37fe-p109">无论您管理来自 Microsoft BGP 路由广告的方式，不会获得 Office 365 服务与表达 internet 电路通过连接到 Office 365 相比任何特殊的风险。Microsoft 保留同一安全、 遵从性和性能级别而不考虑电路客户使用连接到 Office 365 的类型。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p109">Regardless of how you manage the BGP route advertisements coming from Microsoft, you won't gain any special exposure to Office 365 services when compared to connecting to Office 365 over an internet circuit alone. Microsoft maintains the same security, compliance, and performance levels regardless of the type of circuit a customer uses to connect to Office 365.</span></span>
  
### <a name="security"></a><span data-ttu-id="d37fe-148">安全性</span><span class="sxs-lookup"><span data-stu-id="d37fe-148">Security</span></span>

<span data-ttu-id="d37fe-p110">Microsoft 建议您保持自己网络和安全的外围控件的连接将与公用 ExpressRoute 和对等 Microsoft，其中包括与 Office 365 服务的连接。安全控件应在的网络请求的差旅出站从您的网络到 Microsoft 的网络，以及从 Microsoft 的网络将到您的网络的入站邮件。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p110">Microsoft recommends that you maintain your own network and security perimeter controls for connections going to and from ExpressRoute public and Microsoft peering, which includes connections to and from Office 365 services. Security controls should be in place for network requests that travel outbound from your network to Microsoft's network as well as inbound from Microsoft's network to your network.</span></span>
  
#### <a name="outbound-from-customer-to-microsoft"></a><span data-ttu-id="d37fe-151">向 Microsoft 客户从出站</span><span class="sxs-lookup"><span data-stu-id="d37fe-151">Outbound from Customer to Microsoft</span></span>
  
<span data-ttu-id="d37fe-p111">当计算机连接到 Office 365 时，它们将连接到一组相同的终结点而不考虑是否通过 internet 或 ExpressRoute 电路建立连接。使正在使用的电路，无论 Microsoft 建议您将 Office 365 服务，视为泛型 internet 目标比更受信任。出站安全控件应关注的端口和协议以减少暴露和最小化日常维护。[Office 365 终结点](https://aka.ms/o365endpoints)参考 （英文） 一文中提供所需的端口信息。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p111">When computers connect to Office 365, they connect to the same set of endpoints regardless of whether the connection is made over an internet or ExpressRoute circuit. Regardless of the circuit being used, Microsoft recommends that you treat Office 365 services as more trusted than generic internet destinations. Your outbound security controls should focus on the ports and protocols to reduce exposure and minimize ongoing maintenance. The required port information is available in the [Office 365 endpoints](https://aka.ms/o365endpoints) reference article.</span></span>
  
<span data-ttu-id="d37fe-p112">对于添加的控件，您可以使用在您的代理服务器基础结构中筛选的 FQDN 级别限制或检查发往 internet 或 Office 365 的一些或全部网络请求。维护的 Fqdn 列表，如发布功能和 Office 365 产品发展需要更稳固的变更管理和跟踪更改到已发布的[Office 365 终结点](https://aka.ms/o365endpoints)。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p112">For added controls, you can use FQDN level filtering within your proxy infrastructure to restrict or inspect some or all network requests destined for the internet or Office 365. Maintaining the list of FQDNs as features are released and the Office 365 offerings evolve requires more robust change management and tracking of changes to the published [Office 365 endpoints](https://aka.ms/o365endpoints).</span></span>
  
> [!CAUTION]
> <span data-ttu-id="d37fe-158">Microsoft 建议您不要依靠 IP 前缀管理到 Office 365 出站安全。</span><span class="sxs-lookup"><span data-stu-id="d37fe-158">Microsoft recommends you don't rely solely on IP prefixes to manage outbound security to Office 365.</span></span>

|<span data-ttu-id="d37fe-159">**选项**</span><span class="sxs-lookup"><span data-stu-id="d37fe-159">**Option**</span></span>|<span data-ttu-id="d37fe-160">**复杂度**</span><span class="sxs-lookup"><span data-stu-id="d37fe-160">**Complexity**</span></span>|<span data-ttu-id="d37fe-161">**更改控件**</span><span class="sxs-lookup"><span data-stu-id="d37fe-161">**Change Control**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d37fe-162">无限制</span><span class="sxs-lookup"><span data-stu-id="d37fe-162">No restrictions</span></span>  <br/> |<span data-ttu-id="d37fe-163">**低：** 客户允许不受限制出站访问 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="d37fe-163">**Low:** Customer allows unrestricted outbound access to Microsoft.</span></span>  <br/> |<span data-ttu-id="d37fe-164">无</span><span class="sxs-lookup"><span data-stu-id="d37fe-164">None</span></span>  <br/> |
|<span data-ttu-id="d37fe-165">端口限制</span><span class="sxs-lookup"><span data-stu-id="d37fe-165">Port restrictions</span></span>  <br/> |<span data-ttu-id="d37fe-166">**低：** 客户将出站访问限制为 Microsoft 的预期的端口。</span><span class="sxs-lookup"><span data-stu-id="d37fe-166">**Low:** Customer restricts outbound access to Microsoft by the expected ports.</span></span>  <br/> |<span data-ttu-id="d37fe-167">不常用。</span><span class="sxs-lookup"><span data-stu-id="d37fe-167">Infrequent.</span></span>  <br/> |
|<span data-ttu-id="d37fe-168">FQDN 限制</span><span class="sxs-lookup"><span data-stu-id="d37fe-168">FQDN restrictions</span></span>  <br/> |<span data-ttu-id="d37fe-169">**高：** 客户限制对 Office 365 基于的已发布 Fqdn 的出站的访问。</span><span class="sxs-lookup"><span data-stu-id="d37fe-169">**High:** Customer restricts outbound access to Office 365 based on the published FQDNs.</span></span>  <br/> |<span data-ttu-id="d37fe-170">每月的更改。</span><span class="sxs-lookup"><span data-stu-id="d37fe-170">Monthly changes.</span></span>  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a><span data-ttu-id="d37fe-171">从 Microsoft 将到客户的入站邮件</span><span class="sxs-lookup"><span data-stu-id="d37fe-171">Inbound from Microsoft to Customer</span></span>
  
<span data-ttu-id="d37fe-172">有几种需要 Microsoft 启动连接到网络的可选方案。</span><span class="sxs-lookup"><span data-stu-id="d37fe-172">There are several optional scenarios that require Microsoft to initiate connections to your network.</span></span>
  
- <span data-ttu-id="d37fe-173">在登录的密码验证过程的 ADFS。</span><span class="sxs-lookup"><span data-stu-id="d37fe-173">ADFS during password validation for sign-in.</span></span>

- <span data-ttu-id="d37fe-174">[Exchange Server 混合部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d37fe-174">[Exchange Server Hybrid deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).</span></span>

- <span data-ttu-id="d37fe-175">到的本地主机邮件从 Exchange Online 租户。</span><span class="sxs-lookup"><span data-stu-id="d37fe-175">Mail from an Exchange Online tenant to an on-premises host.</span></span>

- <span data-ttu-id="d37fe-176">从 SharePoint Online，SharePoint Online 邮件发送到的本地主机。</span><span class="sxs-lookup"><span data-stu-id="d37fe-176">SharePoint Online Mail send from SharePoint Online to an on-premises host.</span></span>

- <span data-ttu-id="d37fe-177">[SharePoint 联合混合搜索](https://technet.microsoft.com/library/dn197174.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d37fe-177">[SharePoint federated hybrid search](https://technet.microsoft.com/library/dn197174.aspx).</span></span>

- <span data-ttu-id="d37fe-178">[SharePoint 混合 BCS](https://technet.microsoft.com/library/dn197239.aspx )。</span><span class="sxs-lookup"><span data-stu-id="d37fe-178">[SharePoint hybrid BCS](https://technet.microsoft.com/library/dn197239.aspx ).</span></span>

- <span data-ttu-id="d37fe-179">[Skype 业务混合](https://technet.microsoft.com/en-us/library/jj205403.aspx)和/或[业务联盟的 Skype](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d37fe-179">[Skype for Business hybrid](https://technet.microsoft.com/en-us/library/jj205403.aspx) and/or [Skype for Business federation](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).</span></span>

- <span data-ttu-id="d37fe-180">[Skype 商业云连接器](https://technet.microsoft.com/library/mt605227.aspx )。</span><span class="sxs-lookup"><span data-stu-id="d37fe-180">[Skype for Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).</span></span>

<span data-ttu-id="d37fe-p113">Microsoft 建议您接受这些连接通过 internet 电路而不是您 ExpressRoute 电路以减少复杂性。如果您的合规性或性能需要规定必须通过 ExpressRoute 电路接受这些入站的连接，建议使用防火墙或反向代理范围接受的连接。您可以使用[Office 365 终结点](https://aka.ms/o365endpoints)决定的右 Fqdn 和 IP 前缀。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p113">Microsoft recommends that you accept these connections over your internet circuit instead of your ExpressRoute circuit to reduce complexity. If your compliance or performance needs dictate these inbound connections must be accepted over an ExpressRoute circuit, using a firewall or reverse proxy to scope the accepted connections is recommended. You can use the [Office 365 endpoints](https://aka.ms/o365endpoints) to figure out the right FQDNs and IP prefixes.</span></span>
  
### <a name="compliance"></a><span data-ttu-id="d37fe-184">合规性</span><span class="sxs-lookup"><span data-stu-id="d37fe-184">Compliance</span></span>

<span data-ttu-id="d37fe-p114">我们不依赖的任何我们合规性控件使用的路由路径。无论是否您通过连接到 Office 365 服务 ExpressRoute 或 internet 电路，我们合规性控件都不会更改。您应当查看不同的遵从性和 Office 365 明白满足您组织需求的最佳选择安全证书级别。</span><span class="sxs-lookup"><span data-stu-id="d37fe-p114">We don't rely on the routing path you use for any of our compliance controls. Regardless of whether you connect to Office 365 services over an ExpressRoute or internet circuit, our compliance controls won't change. You should review the different compliance and security certification levels for Office 365 to figure out the best choice for meeting your organization's needs.</span></span>
  
<span data-ttu-id="d37fe-188">这是一个简短的链接，您可以使用回来：[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)</span><span class="sxs-lookup"><span data-stu-id="d37fe-188">Here's a short link you can use to come back: [https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="d37fe-189">相关主题</span><span class="sxs-lookup"><span data-stu-id="d37fe-189">Related Topics</span></span>

[<span data-ttu-id="d37fe-190">内容传递网络</span><span class="sxs-lookup"><span data-stu-id="d37fe-190">Content delivery networks</span></span>](content-delivery-networks.md)
  
[<span data-ttu-id="d37fe-191">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="d37fe-191">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="d37fe-192">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="d37fe-192">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
<span data-ttu-id="d37fe-193">[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)（Azure ExpressRoute for Office 365 培训）</span><span class="sxs-lookup"><span data-stu-id="d37fe-193">[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)</span></span>
