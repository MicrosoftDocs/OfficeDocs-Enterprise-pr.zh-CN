---
title: "可访问的图 - Microsoft Office Server 产品的网络集成"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: "本文是名为“Microsoft Office Server 产品的网络集成”的图的可访问文本版本。"
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="79d74-103">可访问的图 - Microsoft Office Server 产品的网络集成</span><span class="sxs-lookup"><span data-stu-id="79d74-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="79d74-104">**摘要：**这篇文章是图名为网络集成的 Microsoft Office 服务器产品辅助功能的文本版本。</span><span class="sxs-lookup"><span data-stu-id="79d74-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="79d74-p101">本宣传海报提供了网络环境，包括 Lync Server 2013、 SharePoint 2013 和 Exchange Server 2013年常规图。它还演示了以下网络元素的这些产品共有： 远程和内部访问、 身份验证、 客户端通讯，以及通过共享设备的路由通信。</span><span class="sxs-lookup"><span data-stu-id="79d74-p101">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013. It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="79d74-107">Lync、Exchange、SharePoint Server 和 Office Web Apps 的高级概念</span><span class="sxs-lookup"><span data-stu-id="79d74-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="79d74-108">关于设计</span><span class="sxs-lookup"><span data-stu-id="79d74-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="79d74-109">简化的网络设计</span><span class="sxs-lookup"><span data-stu-id="79d74-109">Streamlined network design</span></span>

<span data-ttu-id="79d74-p102">这种拓扑说明了内部网络部署 SharePoint 2013、 Exchange Server 2013 和 Lync Server 2013。它还演示如何使用 Microsoft 的基于云的服务，Exchange 在线保护，从互联网提供的简单邮件传输协议 (SMTP) 的入站通信的垃圾邮件和恶意软件保护。</span><span class="sxs-lookup"><span data-stu-id="79d74-p102">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013. It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="79d74-p103">此网络设计已简化为最低要求的网络功能集。此设计不会考虑部分组织可能需要的附加安全或基础结构功能。  </span><span class="sxs-lookup"><span data-stu-id="79d74-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="79d74-114">此图： </span><span class="sxs-lookup"><span data-stu-id="79d74-114">This diagram:</span></span> 
  
- <span data-ttu-id="79d74-115">提供了一个示例网络拓扑，其中说明了通过网关路由器的入站和出站通信，以及到相应的 SharePoint、Exchange 和 Lync 服务器层的客户会话通信（外部和内部）的负载平衡。  </span><span class="sxs-lookup"><span data-stu-id="79d74-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="79d74-116">显示了可选远程访问服务器，例如第三方 VPN 网关或 DirectAccess 服务器，用于为漫游或远程员工提供安全通信的用途。 </span><span class="sxs-lookup"><span data-stu-id="79d74-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="79d74-117">详细介绍了从客户端到每个平台服务器层的 SharePoint、Exchange 和 Lync 通信。 </span><span class="sxs-lookup"><span data-stu-id="79d74-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="79d74-118">基于客户（例如合作伙伴或员工）或所用的身份验证方法识别远程或内部访问连接的类型。 </span><span class="sxs-lookup"><span data-stu-id="79d74-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="79d74-119">冲破 SharePoint 和 Exchange，Lync 平台识别的前端、 应用程序、 数据库和其他级别的必需的服务器角色。</span><span class="sxs-lookup"><span data-stu-id="79d74-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="79d74-p104">此处用于 SharePoint、Lync 和 Exchange 的体系结构未建议实施这些平台的首选方式。它只是提供一个示例，拓扑因具体的网络要求和安全注意事项而异。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="79d74-122">网关路由器</span><span class="sxs-lookup"><span data-stu-id="79d74-122">Gateway router</span></span>

<span data-ttu-id="79d74-p105">对于此拓扑，网关路由器位于网络的边缘并路由发送到 Intranet 以及从中发出的所有传入和传出通信。或者，也可能存在其他组件，可弥补网关路由器和所示负载平衡器之间的差距，例如多层防火墙。此拓扑仅表示众多网络部署方式之一。在此配置中，网关配置了访问控制列表 (ACL)，以允许路由器接口上基于 IP 的特定传入和传出通信。还可以在网络中的其他设备（例如防火墙）上执行 ACL、高级检测或网络地址转换 (NAT)。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="79d74-128">负载平衡器和反向代理设备</span><span class="sxs-lookup"><span data-stu-id="79d74-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="79d74-p106">您可以使用硬件或软件的负载平衡解决方案重定向通信段包括 SharePoint 前端 web 服务器和 Exchange 客户端访问服务器 (CASs) 的。在某些情况下是因为它可以通过使用请求，例如 cookie 或标头中的信息更好地执行有关持久性要求使用第 7 层基于硬件的负载平衡器的最佳。但是，因素，如成本和提高的利用率，这种解决方案的工作负载可能适用于您的特定需求。请考虑下列几点跨 SharePoint 和 Exchange，Lync 负载平衡：</span><span class="sxs-lookup"><span data-stu-id="79d74-p106">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers. However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs. Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="79d74-p107">SharePoint 的 SharePoint 2013 的您不需要启用关联的前端 web 服务器。通常情况下，这将用于创建粘滞会话并避免了多个来自客户端的每个前端 web 服务器的身份验证请求。在 SharePoint 2013 新的分布式缓存服务存储并在 SharePoint 服务器场的 web 服务器之间分布的登录令牌。</span><span class="sxs-lookup"><span data-stu-id="79d74-p107">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers. Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server. The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="79d74-p108">交换的交换 2013，CA 角色设计为使用第 4 层负载平衡，分发请求在传输层。这可以显著降低负载平衡器的利用率和工作负荷。</span><span class="sxs-lookup"><span data-stu-id="79d74-p108">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer. This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="79d74-p109">Lync-Lync 池的会话启动协议 (SIP) 通信建议使用域名系统 (DNS) 的负载平衡。硬件负载平衡 (HLB) 是必需的 Lync Web (HTTPS) 通信。</span><span class="sxs-lookup"><span data-stu-id="79d74-p109">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools. Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="79d74-140">远程访问选项</span><span class="sxs-lookup"><span data-stu-id="79d74-140">Remote access options</span></span>

<span data-ttu-id="79d74-p110">有多个选项可以为 Internet 上的合作伙伴发布 Intranet 资源，或者为远程或漫游员工提供安全远程访问。例如反向代理、DirectAccess 和第三方 VPN 网关。本节稍后讨论的远程访问解决方案可能会用于本地部署中的 SharePoint、Lync 和 Exchange，或者用于这些服务器的任意组合。但是，某些远程选项可能不适用于特定的解决方案。  </span><span class="sxs-lookup"><span data-stu-id="79d74-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="79d74-p111">反向代理服务器的反向代理服务器支持通信进行加密，如安全套接字层 (SSL)，并且内部网应用程序和 web 资源，您就可以将发布与经过身份验证的用户和合作伙伴在 Internet 上。例如，Microsoft 最前沿统一访问网关 (UAG)。许多硬件负载平衡器还支持反向代理服务器的功能。但是，有的使用基于您的需要和要求，如通信隔离、 安全性分布和性能优化的独立解决方案仍然有效方案。</span><span class="sxs-lookup"><span data-stu-id="79d74-p111">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet. An example is Microsoft Forefront Unified Access Gateway (UAG). Many hardware load balancers also support reverse proxy functionality. However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="79d74-149">反向代理的优点和注意事项： </span><span class="sxs-lookup"><span data-stu-id="79d74-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="79d74-150">为访问 Intranet 资源的合作伙伴或用户提供经过身份验证的安全访问（使用客户端和反向代理服务器之间的 SSL (TCP 443)）。 </span><span class="sxs-lookup"><span data-stu-id="79d74-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="79d74-p112">对于 Exchange，使用反向代理（例如 Forefront UAG）的优势之一就是在访问 Exchange 客户端访问服务器之前预先进行身份验证。使用 Outlook Web Access (OWA) 等已发布应用程序的远程访问用户可以在进入内部网络之前，使用基本、NTLM 或 Kerberos 方法进行身份验证。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="79d74-153">对于 Exchange 和 SharePoint，Forefront UAG 等解决方案可以终止 SSL 连接，并在提供单一证书管理点时减少 Intranet 资源服务器的负载。 </span><span class="sxs-lookup"><span data-stu-id="79d74-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="79d74-p113">Lync，对于 Web (HTTPS) 通信都要通过客户端通信的反向代理服务器 (TCP 443)。反向代理服务器代理服务器 HTTPS 连接 Lync Web 服务、 交换 CAS 和 Office Web 应用程序。Lync Server 2013 UAG 不支持。</span><span class="sxs-lookup"><span data-stu-id="79d74-p113">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication. The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps. Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="79d74-p114">DirectAccess-依赖网际协议安全 (IPsec) 进行身份验证和加密 DirectAccess 客户端和服务器之间的通信的远程访问技术。而无需启动连接 DirectAccess 提供漫游和远程员工同时访问互联网和内联网的资源。</span><span class="sxs-lookup"><span data-stu-id="79d74-p114">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server. DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="79d74-159">关于 DirectAccess 要考虑的事项： </span><span class="sxs-lookup"><span data-stu-id="79d74-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="79d74-160">DirectAccess 在 DirectAccess 客户端和服务器之间使用 IPsec 保护的通信（协议 50/51 和 UDP 500）。 </span><span class="sxs-lookup"><span data-stu-id="79d74-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="79d74-161">适用于 Windows Server 2012 和 Windows 8 的 DirectAccess 不需要部署公钥基础结构 (PKI) 来实现服务器和客户端身份验证。 </span><span class="sxs-lookup"><span data-stu-id="79d74-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="79d74-162">我们建议您不要使用 Lync Server 2013 DirectAccess 由于 IPsec 加密和解密与相关的音频和视频的滞后时间问题。</span><span class="sxs-lookup"><span data-stu-id="79d74-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="79d74-p115">VPN 网关的典型 VPN 网关提供远程访问连接的远程访问客户端计算机逻辑上投影到通过隧道和用户启动连接的 intranet。可以使用 Windows Server 2012 或几种第三方解决方案中统一远程访问漫游或远程员工提供安全的访问企业内部网。Lync 不建议使用 VPN。远程 Lync 通信应使用边缘服务器和拆分隧道。</span><span class="sxs-lookup"><span data-stu-id="79d74-p115">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection. You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees. VPN is not recommended for Lync. Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="79d74-167">域名系统 (DNS) 的注意事项</span><span class="sxs-lookup"><span data-stu-id="79d74-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="79d74-168">您需要规划 DNS 记录集，允许 Internet 和 Intranet 用户将 DNS 名称解析为相应的 IP 地址。 </span><span class="sxs-lookup"><span data-stu-id="79d74-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="79d74-169">对于基于 Internet 的合作伙伴和漫游或远程员工，在 Internet DNS 服务器中注册的 DNS 记录可根据需要解析为与网关路由器、Lync 边缘服务器、负载平衡器上的虚拟 IP 地址 (VIP) 集以及 DirectAccess 或 VPN 网关对应的公共 IP 地址集。 </span><span class="sxs-lookup"><span data-stu-id="79d74-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="79d74-170">对于基于 Intranet 的用户，在 Intranet DNS 服务器中注册的 DNS 记录可在负载平衡器上解析为虚拟 IP 地址 (VIP) 集以访问 SharePoint、Lync 和 Exchange 资源。 </span><span class="sxs-lookup"><span data-stu-id="79d74-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="79d74-p116">对于与 Intranet DNS 命名空间对应的名称，DirectAccess 客户端使用 Intranet DNS 服务器，否则使用 Internet DNS 服务器。要简化 DirectAccess 的操作，请考虑使用拆分 DNS 实施，它对基于 Intranet 和 Internet 的名称使用不同 DNS 命名空间。例如，对 Internet 命名空间使用 contoso.com，对 Intranet 命名空间使用 corp.contoso.com。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="79d74-p117">Exchange 使用拆分 DNS 模型，即对于公共路由的通信和公司网络，其主机到 IP 的解析不相同。您至少需要具有 OWA 的 DNS 记录、自动发现、客户端通信的 ActiveSync URL 和入站邮件的 MX 记录。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="79d74-176">如果您使用 Exchange Online Protection (EOP)，您的 MX 记录将指向该服务，而不是您的 Exchange 服务器场。 </span><span class="sxs-lookup"><span data-stu-id="79d74-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="79d74-177">对于 Exchange，您需要公共 DNS 中的所有权证明 TXT 记录以及联合组织 ID 才能设置联合共享。 </span><span class="sxs-lookup"><span data-stu-id="79d74-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="79d74-178">当远程访问 VPN 连接处于活动状态时，远程访问 VPN 客户端可以设置为仅使用 Intranet DNS 服务器。 </span><span class="sxs-lookup"><span data-stu-id="79d74-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="79d74-179">图示说明</span><span class="sxs-lookup"><span data-stu-id="79d74-179">Diagram Description</span></span>

<span data-ttu-id="79d74-p118">此图提供了一个示例网络拓扑，其中说明了通过网关路由器的入站和出站通信，以及到相应的 SharePoint、Exchange 和 Lync 服务器层的客户端会话通信（外部和内部）的负载平衡。此图的说明分为两个部分： </span><span class="sxs-lookup"><span data-stu-id="79d74-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="79d74-182">图中所示组件的说明 </span><span class="sxs-lookup"><span data-stu-id="79d74-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="79d74-183">说明通信如何通过组件传送到 SharePoint、Exchange、Lync 和 Office Web Apps 服务器层。 </span><span class="sxs-lookup"><span data-stu-id="79d74-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="79d74-184">图中所示组件的说明 </span><span class="sxs-lookup"><span data-stu-id="79d74-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="79d74-185">用户类型</span><span class="sxs-lookup"><span data-stu-id="79d74-185">User types</span></span>

<span data-ttu-id="79d74-186">有四种不同类型的用户，三种位于网络和云服务外，一种为内部用户，包括： </span><span class="sxs-lookup"><span data-stu-id="79d74-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="79d74-187">合作伙伴公司（企业对企业）-外部 </span><span class="sxs-lookup"><span data-stu-id="79d74-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="79d74-188">个人合作伙伴（SharePoint 和匿名 (Lync)）-外部 </span><span class="sxs-lookup"><span data-stu-id="79d74-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="79d74-189">漫游和远程员工-外部 </span><span class="sxs-lookup"><span data-stu-id="79d74-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="79d74-190">内部员工</span><span class="sxs-lookup"><span data-stu-id="79d74-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="79d74-191">基于云的电子邮件通信</span><span class="sxs-lookup"><span data-stu-id="79d74-191">Cloud-based email traffic</span></span>

<span data-ttu-id="79d74-192">对于基于 SMTP（Internet 邮件主机或 Exchange Online Protection）的电子邮件通信，存在一个基于云的组件。 </span><span class="sxs-lookup"><span data-stu-id="79d74-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="79d74-193">外部访问的身份验证</span><span class="sxs-lookup"><span data-stu-id="79d74-193">Authentication for external access</span></span>

<span data-ttu-id="79d74-p119">对于每种用户类型，Lync、SharePoint 和 Exchange 均有一系列特定的身份验证过程。本文档后面会更详细地介绍。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="79d74-196">ACL 的网关路由器</span><span class="sxs-lookup"><span data-stu-id="79d74-196">Gateway router with ACLs</span></span>

<span data-ttu-id="79d74-197">网关路由器位于网络的边缘并路由发送到 Intranet 以及从中发出的所有传入和传出通信。 </span><span class="sxs-lookup"><span data-stu-id="79d74-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="79d74-198">Lync 和 SharePoint 的远程访问服务器</span><span class="sxs-lookup"><span data-stu-id="79d74-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="79d74-199">此拓扑包括 Lync 边缘服务器和 SharePoint VPN 网关或 DirectAccess 服务器。 </span><span class="sxs-lookup"><span data-stu-id="79d74-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="79d74-200">负载平衡器和反向代理设备</span><span class="sxs-lookup"><span data-stu-id="79d74-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="79d74-p120">您可以使用硬件或软件负载平衡解决方案重定向各个分段的通信，包括 SharePoint 前端 Web 服务器和 Exchange 客户端访问服务器 (CAS)。此拓扑显示负载平衡器中的 Lync VIP、SharePoint VIP 和 Exchange VIP 组件。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="79d74-203">服务器</span><span class="sxs-lookup"><span data-stu-id="79d74-203">Servers</span></span>

<span data-ttu-id="79d74-p121">有四个服务器： Lync、 SharePoint、 交换和 Office Web 应用程序服务器。每个服务器可以有三个层次： 前端、 客户端访问层、 应用层和数据库中的存储层。</span><span class="sxs-lookup"><span data-stu-id="79d74-p121">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server. Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="79d74-206">前端客户端访问层</span><span class="sxs-lookup"><span data-stu-id="79d74-206">Front-end, client-access tier</span></span>

<span data-ttu-id="79d74-207">该层在全部四个服务器上均具有组件： </span><span class="sxs-lookup"><span data-stu-id="79d74-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="79d74-p122">Lync 池（前端）。该图显示两个 Lync 数据库。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="79d74-p123">SharePoint 前端和分布式缓存。该图显示三个 SharePoint 数据库。  </span><span class="sxs-lookup"><span data-stu-id="79d74-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="79d74-p124">Exchange CAS。该图显示两个 Exchange 数据库。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="79d74-p125">Office Web Apps Server。该图显示两个 Office Web Apps 数据库。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="79d74-216">应用程序层</span><span class="sxs-lookup"><span data-stu-id="79d74-216">Application tier</span></span>

<span data-ttu-id="79d74-217">该层仅在 SharePoint 服务器上具有组件： </span><span class="sxs-lookup"><span data-stu-id="79d74-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="79d74-p126">搜索（查询、索引、管理）。该图显示三个 SharePoint 数据库。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="79d74-p127">批处理。该图显示三个 SharePoint 数据库。  </span><span class="sxs-lookup"><span data-stu-id="79d74-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="79d74-222">数据库/存储层</span><span class="sxs-lookup"><span data-stu-id="79d74-222">Database/storage tier</span></span>

<span data-ttu-id="79d74-223">该层在 Lync、SharePoint 和 Exchange 服务器上具有组件： </span><span class="sxs-lookup"><span data-stu-id="79d74-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="79d74-p128">Lync 数据库（后端）。该图显示三个 Lync 数据库。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="79d74-p129">SharePoint 数据库。该图显示三个 SharePoint 数据库。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="79d74-p130">Exchange 邮箱服务器。该图显示两个 Exchange 邮箱数据库。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="79d74-230">每个 SharePoint 服务器角色上安装的组件有关的详细信息，请参阅[SharePoint 2013 的拓扑优化](https://aka.ms/Ma5cgk)。</span><span class="sxs-lookup"><span data-stu-id="79d74-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="79d74-231">说明通信如何通过组件传递到不同的服务器层</span><span class="sxs-lookup"><span data-stu-id="79d74-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="79d74-232">本节介绍用户请求如何通过网络拓扑传递。  </span><span class="sxs-lookup"><span data-stu-id="79d74-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="79d74-233">外部访问的身份验证和路由</span><span class="sxs-lookup"><span data-stu-id="79d74-233">Authentication and routing for external access</span></span>

<span data-ttu-id="79d74-234">网络和云服务外有三种不同类型的客户端，包括： </span><span class="sxs-lookup"><span data-stu-id="79d74-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="79d74-235">合作伙伴公司（企业对企业）-外部 </span><span class="sxs-lookup"><span data-stu-id="79d74-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="79d74-236">个人合作伙伴（SharePoint 和匿名 (Lync)）-外部 </span><span class="sxs-lookup"><span data-stu-id="79d74-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="79d74-237">漫游和远程员工-外部 </span><span class="sxs-lookup"><span data-stu-id="79d74-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="79d74-238">每种外部用户类型的身份验证和路由过程分别如下所述。 </span><span class="sxs-lookup"><span data-stu-id="79d74-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="79d74-239">合作伙伴公司（企业对企业）(https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="79d74-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="79d74-p131">Lync：与其他组织建立联合信任，Skype 通过公共 IM 连接 (PIC) 与 AOL 建立联合信任。Lync 联合通信通过网关路由器依次传递到 Lync 边缘服务器、Lync VIP（负载平衡器/反向代理服务器）和 Lync Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="79d74-p132">SharePoint：使用 SAML 身份验证的受信任的合作伙伴标识提供程序。SharePoint 客户端通信通过网关路由器依次传递到 SharePoint VIP（负载平衡器/反向代理服务器）和 SharePoint Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="79d74-p133">Exchange：邮件通信使用相互身份验证 TLS，联合共享使用 SAML 身份验证。Exchange 客户端通信通过网关路由器依次传递到 Exchange VIP（负载平衡器/反向代理服务器）和 Exchange Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="79d74-246">SMTP 客户端通信通过网关路由器依次传递到 Exchange VIP（负载平衡器/反向代理服务器）和 Exchange Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="79d74-247">个人合作伙伴 (SharePoint) 和匿名 (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="79d74-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="79d74-p134">Lync：匿名用户只能加入员工组织的 Lync 会议。Lync 联合通信通过网关路由器依次传递到 Lync 边缘服务器、Lync VIP（负载平衡器/反向代理服务器）和 Lync Server。  </span><span class="sxs-lookup"><span data-stu-id="79d74-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="79d74-p135">SharePoint：使用 SAML 身份验证或基于表单的身份验证的受信任的合作伙伴标识提供程序。SharePoint 客户端通信通过网关路由器依次传递到 SharePoint VIP（负载平衡器/反向代理服务器）和 SharePoint Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="79d74-252">Exchange：不适用。</span><span class="sxs-lookup"><span data-stu-id="79d74-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="79d74-253">Lync Web 通信通过网关路由器依次传递到 Lync 边缘服务器、Lync VIP（负载平衡器/反向代理服务器）、硬件负载平衡器（HTTPS 通信需要）和 Lync Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="79d74-254">漫游和远程员工</span><span class="sxs-lookup"><span data-stu-id="79d74-254">Roaming and remote employees</span></span>

1. <span data-ttu-id="79d74-255">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-255">https://intranet.contoso.com</span></span> 
    
2. <span data-ttu-id="79d74-256">https://teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-256">https://teams.contoso.com</span></span> 
    
3. <span data-ttu-id="79d74-257">https://my.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-257">https://my.contoso.com</span></span>
    
4. <span data-ttu-id="79d74-258">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-258">https://partnerweb.contoso.com</span></span> 
    
5. <span data-ttu-id="79d74-259">https://mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="79d74-259">https://mail.contoso.com\*</span></span> 
    
6. <span data-ttu-id="79d74-260">https://dial.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="79d74-260">https://dial.contoso.com\*</span></span>
    
7. <span data-ttu-id="79d74-261">https://meet.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="79d74-261">https://meet.contoso.com\*</span></span>
    
* <span data-ttu-id="79d74-262">交换 URL 具有下列虚拟目录： 自动发现，ecp，EWS，Microsoft 的服务器-ActiveSync，OAB，owa，PowerShell</span><span class="sxs-lookup"><span data-stu-id="79d74-262">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="79d74-p136">Lync：TLS-DSK 或 NTLM 身份验证。Lync 客户端通信通过网关路由器依次传递到 Lync 边缘服务器、Lync VIP（负载平衡器/反向代理服务器）和 Lync Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="79d74-p137">SharePoint：Active Directory 域服务 (AD DS)、基于表单的身份验证或 SAML 身份验证。SharePoint 客户端通信通过 VPN 网关或 DirectAccess 服务器依次传递到 SharePoint VIP（负载平衡器/反向代理服务器）和 SharePoint Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="79d74-p138">Exchange：通过 SSL 的基本身份验证（ActiveSync、自动发现）、基于表单的身份验证 (OWA)。Exchange 客户端通信通过网关路由器依次传递到 Exchange VIP（负载平衡器/反向代理服务器）和 Exchange Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="79d74-269">Lync 客户端通信通过网关路由器依次传递到 Lync VIP（负载平衡器/反向代理服务器）、硬件负载平衡器（HTTPS 通信需要）和 Lync Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-269">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="79d74-270">内部访问的身份验证</span><span class="sxs-lookup"><span data-stu-id="79d74-270">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="79d74-271">内部员工</span><span class="sxs-lookup"><span data-stu-id="79d74-271">Internal employees</span></span>

> <span data-ttu-id="79d74-272">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-272">https://intranet.contoso.com</span></span> 
    
> <span data-ttu-id="79d74-273">https://teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-273">https://teams.contoso.com</span></span> 
    
> <span data-ttu-id="79d74-274">https://my.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-274">https://my.contoso.com</span></span>
    
> <span data-ttu-id="79d74-275">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-275">https://partnerweb.contoso.com</span></span>
    
> <span data-ttu-id="79d74-276">https://mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="79d74-276">https://mail.contoso.com\*</span></span> 
    
> <span data-ttu-id="79d74-277">https://dial.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-277">https://dial.contoso.com</span></span> 
    
> <span data-ttu-id="79d74-278">https://meet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-278">https://meet.contoso.com</span></span>
    
> <span data-ttu-id="79d74-279">https://admin.contoso.com</span><span class="sxs-lookup"><span data-stu-id="79d74-279">https://admin.contoso.com</span></span>
    
- <span data-ttu-id="79d74-p139">Lync：Kerberos、TLS-DSK 或 NTLM 身份验证。Lync 客户端通信依次传递到 Lync VIP（负载平衡器/反向代理服务器）和 Lync Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="79d74-p140">SharePoint：Active Directory 域服务 (AD DS)、基于表单的身份验证或 SAML 身份验证。SharePoint 客户端通信依次传递到 SharePoint VIP（负载平衡器/反向代理服务器）和 SharePoint Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="79d74-p141">Exchange：AD DS、基于表单的身份验证。Exchange 客户端通信依次传递到 Exchange VIP（负载平衡器/反向代理服务器）和 Exchange Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="79d74-286">Lync 客户端通信依次传递到 Lync VIP（负载平衡器/反向代理服务器）、硬件负载平衡器（HTTPS 通信需要）和 Lync Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-286">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="79d74-287">基于云的电子邮件通信</span><span class="sxs-lookup"><span data-stu-id="79d74-287">Cloud-based email traffic</span></span>

<span data-ttu-id="79d74-288">基于 SMTP 的电子邮件通讯的基于云的组件由 Internet 邮件主机或 Exchange 在线保护。</span><span class="sxs-lookup"><span data-stu-id="79d74-288">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="79d74-p142">这些组件使用 SMTP 在网络上移动电子邮件流量。通信通过网关路由器依次传递到 Exchange VIP（负载平衡器/反向代理服务器）和 Exchange Server。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="79d74-291">网络通信图例</span><span class="sxs-lookup"><span data-stu-id="79d74-291">Network traffic legend</span></span>

<span data-ttu-id="79d74-292">图例方框以图形的形式显示不同类型的通信，如图中不同颜色的线条所示： </span><span class="sxs-lookup"><span data-stu-id="79d74-292">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="79d74-293">绿色线： Lync SIP 通信</span><span class="sxs-lookup"><span data-stu-id="79d74-293">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="79d74-294">蓝色线条：Lync Web 通信 </span><span class="sxs-lookup"><span data-stu-id="79d74-294">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="79d74-295">紫色线条：SharePoint 客户端通信 </span><span class="sxs-lookup"><span data-stu-id="79d74-295">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="79d74-296">橙色线条：Exchange 客户端通信 </span><span class="sxs-lookup"><span data-stu-id="79d74-296">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="79d74-297">灰色线条：Exchange 内部部署和 Exchange Online Protection 之间的 Exchange 邮件服务器通信。 </span><span class="sxs-lookup"><span data-stu-id="79d74-297">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="79d74-298">不同类型的通信及其使用的端口也在图例方框中显示。 </span><span class="sxs-lookup"><span data-stu-id="79d74-298">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="79d74-299">Lync SIP 通信和 Lync Web 通信</span><span class="sxs-lookup"><span data-stu-id="79d74-299">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="79d74-300">Lync 边缘服务器对外部用户通信使用以下端口：  </span><span class="sxs-lookup"><span data-stu-id="79d74-300">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="79d74-301">信号处理/IM 通信 (SIP/SIMPLE)：TCP 端口 443（开放用于入站通信） </span><span class="sxs-lookup"><span data-stu-id="79d74-301">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="79d74-302">Web 会议通信 (PSOM)：TCP 端口 443（开放用于入站通信） </span><span class="sxs-lookup"><span data-stu-id="79d74-302">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="79d74-303">A/V 通信 (SRTP)：TCP 443、UDP 3478 和 TCP 50000-59999（可选，开放用于入站和出站通信） </span><span class="sxs-lookup"><span data-stu-id="79d74-303">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="79d74-304">Lync 边缘服务器对联合通信使用以下端口：  </span><span class="sxs-lookup"><span data-stu-id="79d74-304">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="79d74-305">TCP 端口 5061 (SIP)、5269 (XMPP)、443 和 UDP 3478 (SRTP)（开放用于入站和出站通信） </span><span class="sxs-lookup"><span data-stu-id="79d74-305">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="79d74-306">SharePoint 客户端通信</span><span class="sxs-lookup"><span data-stu-id="79d74-306">SharePoint client traffic</span></span>

<span data-ttu-id="79d74-p143">SharePoint 可以使用 TCP 端口 443 (SSL) 处理客户端和负载平衡器之间的加密通信。对于来自 Internet 的外部访问，必须为网关路由器（或外部防火墙）上的入站和出站通信打开此端口。 </span><span class="sxs-lookup"><span data-stu-id="79d74-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="79d74-309">Exchange 客户端通信和 Exchange 邮件服务器通信</span><span class="sxs-lookup"><span data-stu-id="79d74-309">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="79d74-p144">Exchange 使用 TCP 端口 25 (SMTP) 服务器到服务器通信。大多数客户端通信 （OWA、 动态同步、 自动发现、 Outlook 无处） 处理通过端口 443 (HTTPS)。如果您的 POP 或 IMAP 客户端，还使用端口 110 (POP3)、 995 (加密 POP3)、 143 (IMAP4)、 993 (加密 IMAP4) 和 587 (SMTP) 以支持这些客户端。</span><span class="sxs-lookup"><span data-stu-id="79d74-p144">Exchange uses TCP port 25 (SMTP) for server-to-server communications. Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS). If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="79d74-313">有关 Lync 网络通信的更多信息？</span><span class="sxs-lookup"><span data-stu-id="79d74-313">More on Lync network traffic?</span></span>

<span data-ttu-id="79d74-p145">了解 Lync Server 可以如何帮助您的组织提供即时消息、 web 会议、 共享应用程序和语音通信。有关详细信息，请参阅[Microsoft Lync 2013 协议工作负载海报](https://aka.ms/G5jzjo)。</span><span class="sxs-lookup"><span data-stu-id="79d74-p145">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication. For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="79d74-316">此海报中还包含用于访问此信息的 QR 代码。 </span><span class="sxs-lookup"><span data-stu-id="79d74-316">The poster also includes a QR code to access this information.</span></span> 
  

