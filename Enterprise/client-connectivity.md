---
title: 客户端连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 摘要：介绍了客户端计算机如何根据客户端计算机和 Office 365 租户数据中心的位置连接到 Office 365 租户。
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223034"
---
# <a name="client-connectivity"></a><span data-ttu-id="d0936-103">客户端连接</span><span class="sxs-lookup"><span data-stu-id="d0936-103">Client connectivity</span></span>

 <span data-ttu-id="d0936-104">**摘要：** 介绍了客户端计算机如何根据客户端计算机和 Office 365 租户数据中心的位置连接到 Office 365 租户。</span><span class="sxs-lookup"><span data-stu-id="d0936-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="d0936-p101">Office 365 驻留在世界各地的 Microsoft 数据中心帮助保留设置的服务和运行即使一个区域，如地震或停电中没有重大问题。当您连接到 Office 365 租户时，客户端连接将被定向到适当的数据中心到承载您的租户。由您与 Microsoft 的协议定义确定可以承载您的租户的规则。确定您的客户端如何获取该数据中心位置中的数据的规则取决于您正在使用的服务的体系结构。</span><span class="sxs-lookup"><span data-stu-id="d0936-p101">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage. When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted. The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft. The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="d0936-p102">例如，当您在登录到 Office 365 门户，您通常连接到最接近数据中心到客户端，然后定向根据服务使用下一步。如果您启动电子邮件，以显示用户界面的初始连接可能仍来自最近的数据中心，但第二个连接可能打开最近的数据中心之间的数据中心，您的租户所在的位置显示您什么是电子邮件在您阅读。Microsoft 运行世界上导致非常快速数据中心到 datacenter 连接 fast 顶部的十个网络之一。</span><span class="sxs-lookup"><span data-stu-id="d0936-p102">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next. If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read. Microsoft operates one of the top ten networks in the world resulting in incredibly fast datacenter-to-datacenter connections fast.</span></span>
  
<span data-ttu-id="d0936-112">阅读此文章后，您可能会明白为什么我们不提供[Office 365 Url 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)每个数据中心，它们只是太相互连接和依赖相互进行的可行。</span><span class="sxs-lookup"><span data-stu-id="d0936-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="d0936-p103">如果使用的 Office 365 的 Azure ExpressRoute，在大多数情况下您连接将转通过专用连接到 Office 365 而不是公共此处描述的连接。有关如何客户端连接的原则准确。了解有关[Office 365 的 Azure ExpressRoute](azure-expressroute.md)。</span><span class="sxs-lookup"><span data-stu-id="d0936-p103">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here. The principles about how clients connect are still accurate. Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="d0936-116">有关业务网络请求 Skype 的深入，阅读文章[媒体质量和 Skype 业务 online 中的网络连接性能](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)。</span><span class="sxs-lookup"><span data-stu-id="d0936-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="d0936-117">本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="d0936-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="d0936-p104">我们需要谨慎以使其安全和专用我们数据中心中管理客户数据。[信任中心](https://go.microsoft.com/fwlink/?LinkID=397383)中包含有关管理隐私我们采取的步骤的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d0936-p104">We take great care to manage customer data so it's secure and private in our datacenters. Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="d0936-120">连接到最接近数据中心</span><span class="sxs-lookup"><span data-stu-id="d0936-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="d0936-p105">这是最常见类型的连接，并使用 Office 365 门户和 Exchange Online。在此情况下，当客户端尝试连接到 Office 365，其计算机的 DNS 查询确定其计算机来自的世界区域和 Office 365 将请求重定向到最近的数据中心。</span><span class="sxs-lookup"><span data-stu-id="d0936-p105">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online. In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="d0936-123">连接到门户停止在最近的数据中心，并在客户端计算机将显示有关从该位置的客户端的租户的信息。</span><span class="sxs-lookup"><span data-stu-id="d0936-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="d0936-p106">Exchange Online 转步骤进一步。一旦客户端计算机连接到最近的数据中心，该数据中心中的 Exchange 服务器连接到数据中心租户所在实际中所示*原理这工作部分*下方。Exchange Online 中最近的数据中心然后代理服务器到邮箱服务器从客户端计算机请求。这加快客户端计算机的体验通过移动繁重的检索电子邮件和日历项目与 Microsoft 网络。</span><span class="sxs-lookup"><span data-stu-id="d0936-p106">Exchange Online goes a step further. Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below. The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server. This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="d0936-128">这如何工作的标准云产品？</span><span class="sxs-lookup"><span data-stu-id="d0936-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="d0936-p107">此连接过程是标准对于高流量，高价值 web 应用程序类似于 Office 365。在此部分中，我们大纲，说明在进程中的步骤。当客户端计算机不是作为租户的同一区域中时，查找得多不同，具体取决于客户端连接到的服务连接。</span><span class="sxs-lookup"><span data-stu-id="d0936-p107">This connection process is standard for high traffic, high value web applications like Office 365. In this section, we outline and illustrate the steps in the process. When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="d0936-p108">此图说明了在北美租户中使用标准的 Office 365 产品的客户。在此方案中，发出请求的人移动到欧洲，从该位置使用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="d0936-p108">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America. In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="d0936-134">客户端计算机请求本地 DNS 服务器提供与 Office 365 关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d0936-135">客户端计算机的本地 DNS 服务器请求 Microsoft DNS 服务器提供与 Office 365 关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d0936-136">Microsoft 的 DNS 服务器返回 （根据客户端的 DNS 服务器的位置），该区域的服务器的名称和客户端计算机重复步骤 1 和 2 来获得区域的 Office 365 数据中心的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="d0936-137">客户端计算机连接到区域数据中心 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="d0936-138">Exchange Online 服务器建立到客户租户所在的活动数据中心的连接。</span><span class="sxs-lookup"><span data-stu-id="d0936-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![最近的区域数据中心](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="d0936-140">Sovereign 此工作是如何云产品的？</span><span class="sxs-lookup"><span data-stu-id="d0936-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="d0936-p109">此连接是 sovereign 云产品，例如 Office 365 由 21 Vianet 略有不同。与 Office 365 的 sovereign 实例中租户，将接受门户进行连接的最接近的 Office 365 服务器是租户所在的 sovereign 区域内的服务器。同样，访问 SharePoint Online 我们 sovereign 云或标准产品中的客户将被导向租户所在的前端服务器。请参阅连接到下面的活动数据中心。</span><span class="sxs-lookup"><span data-stu-id="d0936-p109">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet. With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides. Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides. See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="d0936-145">客户端计算机请求本地 DNS 服务器提供与 Office 365 关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d0936-146">客户端计算机的本地 DNS 服务器请求 Microsoft DNS 服务器提供与 Office 365 关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d0936-147">Microsoft 的 DNS 服务器返回 （根据客户端的 DNS 服务器的位置），该区域的服务器的名称和客户端计算机重复步骤 1 和 2 来获得区域的 Office 365 数据中心的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="d0936-148">客户端计算机连接到区域数据中心 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="d0936-149">Exchange Online 服务器建立到客户租户所在的活动数据中心的连接。</span><span class="sxs-lookup"><span data-stu-id="d0936-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![最近的区域美国数据中心](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="d0936-151">连接到活动数据中心</span><span class="sxs-lookup"><span data-stu-id="d0936-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="d0936-p110">连接到活动数据中心专为粗数据传输工作负荷和当前使用 SharePoint Online。在此情况下，当客户端尝试连接到 Office 365 时其浏览器将重定向到活动数据中心其 SharePoint Online 租户。</span><span class="sxs-lookup"><span data-stu-id="d0936-p110">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online. In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="d0936-154">其工作方式如何？</span><span class="sxs-lookup"><span data-stu-id="d0936-154">How does this work?</span></span>

<span data-ttu-id="d0936-p111">当其他区域的客户端计算机连接到 SharePoint Online 时，则会将连接重定向至活动的 SharePoint Online 数据中心。在此方案中，客户使用服务的功能，从而门户剩余本地连接和定向到活动数据中心的 SharePoint Online 连接的标准。</span><span class="sxs-lookup"><span data-stu-id="d0936-p111">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter. In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="d0936-157">客户端计算机请求本地 DNS 服务器提供与 Office 365 关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d0936-158">客户端计算机的本地 DNS 服务器请求 Microsoft DNS 服务器提供与 Office 365 关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d0936-159">Microsoft 的 DNS 服务器返回 （根据客户端的 Office 365 租户的位置），活动 SharePoint Online 数据中心的服务器名称和客户端计算机重复步骤 1 和 2 来获得的活动 Office 365 数据中心的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="d0936-160">客户端计算机连接到活动数据中心 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-160">The client computer connects to the active datacenter IP address.</span></span>

![活动的美国数据中心](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="d0936-162">通过虚拟专用网络 (VPN) 连接</span><span class="sxs-lookup"><span data-stu-id="d0936-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="d0936-p112">此类型的连接适用仅虚拟专用网络 (VPN) 使用客户端计算机。Office 365 行为不只需更改事实上，因为使用了 VPN，但 Vpn 通常用于控制客户端计算机降级体验中建立连接到 Office 365 和通常结果的方式，因此它非常重要覆盖。</span><span class="sxs-lookup"><span data-stu-id="d0936-p112">This type of connection applies only when a virtual private network (VPN) is used by client computers. In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="d0936-165">其工作方式如何？</span><span class="sxs-lookup"><span data-stu-id="d0936-165">How does this work?</span></span>

<span data-ttu-id="d0936-p113">当客户端计算机建立到公司办公不同区域中的 VPN 连接时，而不是在客户端计算机的位置的 DNS 服务器使用的 office 上的 DNS 服务器。在大多数情况下，此额外通过 VPN 连接将降低了 Office 365 体验。为最终用户尽可能接近服务客户连接到优化 Office 365 服务。许多服务利用 Azure 边缘网络、 内容传递网络和 Microsoft 网络上可靠网络容量，如接近客户端计算机进行 for Office 365 服务的网络请求时提供最佳的用户体验尽可能。</span><span class="sxs-lookup"><span data-stu-id="d0936-p113">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location. In most cases, this extra connection over the VPN will degrade the Office 365 experience. The Office 365 services are optimized to service customer connections as close to the end user as possible. Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="d0936-170">客户端计算机请求 VPN DNS 服务器提供与 Office 365 关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="d0936-171">客户端计算机的 VPN DNS 服务器请求 Microsoft DNS 服务器提供与 Office 365 关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="d0936-172">Microsoft 的 DNS 服务器返回 （基于位置的 VPN DNS 服务器） 的区域服务器名称，并在客户端计算机重复步骤 1 和 2 来获取区域的 Office 365 数据中心的 IP 地址信息。</span><span class="sxs-lookup"><span data-stu-id="d0936-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="d0936-173">客户端计算机连接到数据中心在公司办公室，它们建立 VPN 连接与最接近的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d0936-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![VPN 数据中心连接](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="d0936-175">这是一个简短的链接，您可以使用回来：[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="d0936-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d0936-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0936-176">See also</span></span>

[<span data-ttu-id="d0936-177">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="d0936-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="d0936-178">与 Office 365 的网络连接</span><span class="sxs-lookup"><span data-stu-id="d0936-178">Network connectivity to Office 365</span></span>](network-connectivity.md)
