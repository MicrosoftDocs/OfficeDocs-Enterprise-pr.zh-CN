---
title: 可访问的图 - Microsoft Office Server 产品的网络集成
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
description: 本文是名为“Microsoft Office Server 产品的网络集成”的图的可访问文本版本。
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487767"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>可访问的图 - Microsoft Office Server 产品的网络集成

**摘要:** 本文是名为 "Microsoft Office Server 产品的网络集成" 的图表的可访问文本版本。
  
此海报提供了包含 Lync Server 2013、SharePoint 2013 和 Exchange Server 2013 的网络环境的一般说明。 它还演示了这些产品通用的网络元素：远程和内部访问、身份验证、客户端通信以及通过共享设备路由流量。 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Lync、Exchange、SharePoint Server 和 Office Web Apps 的高级概念

### <a name="about-the-design"></a>关于设计

#### <a name="streamlined-network-design"></a>简化的网络设计

此拓扑说明了 SharePoint 2013、Exchange Server 2013 和 Lync server 2013 的本地网络部署。 它还演示了如何使用基于云的 Microsoft 服务 Exchange Online Protection，该服务为从 Internet 发送的入站简单邮件传输协议 (SMTP) 通信提供垃圾邮件和恶意软件保护。 
  
此网络设计已简化为最低要求的网络功能集。此设计不会考虑部分组织可能需要的附加安全或基础结构功能。   
  
此图：  
  
- 提供了一个示例网络拓扑，其中说明了通过网关路由器的入站和出站通信，以及到相应的 SharePoint、Exchange 和 Lync 服务器层的客户会话通信（外部和内部）的负载平衡。   
    
- 显示了可选远程访问服务器，例如第三方 VPN 网关或 DirectAccess 服务器，用于为漫游或远程员工提供安全通信的用途。  
    
- 详细介绍了从客户端到每个平台服务器层的 SharePoint、Exchange 和 Lync 通信。  
    
- 基于客户（例如合作伙伴或员工）或所用的身份验证方法识别远程或内部访问连接的类型。 
    
- 按所需的服务器角色分解 SharePoint、Exchange 和 Lync 平台，以识别前端、应用程序、数据库和其他级别。 
    
此处用于 SharePoint、Lync 和 Exchange 的体系结构未建议实施这些平台的首选方式。它只是提供一个示例，拓扑因具体的网络要求和安全注意事项而异。  
  
#### <a name="gateway-router"></a>网关路由器

对于此拓扑，网关路由器位于网络的边缘并路由发送到 Intranet 以及从中发出的所有传入和传出通信。或者，也可能存在其他组件，可弥补网关路由器和所示负载平衡器之间的差距，例如多层防火墙。此拓扑仅表示众多网络部署方式之一。在此配置中，网关配置了访问控制列表 (ACL)，以允许路由器接口上基于 IP 的特定传入和传出通信。还可以在网络中的其他设备（例如防火墙）上执行 ACL、高级检测或网络地址转换 (NAT)。  
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>负载平衡器和反向代理设备

您可以使用硬件或软件负载平衡解决方案重定向各个分段的通信，包括 SharePoint 前端 Web 服务器和 Exchange 客户端访问服务器 (CAS)。 在某些情况下, 最好将基于第7层硬件的负载平衡器用于持续性要求, 因为它可以通过使用请求中的信息 (如 cookie 或标头) 来更好地运行。 但是，此类解决方案中的成本、提升的利用率和工作负载等因素可能不是您的特定需求所需要的。 对于跨 SharePoint、Exchange 和 Lync 的负载平衡，请考虑以下几点： 
  
- sharepoint-对于 sharepoint 2013, 无需为前端 web 服务器启用相关性。 通常，这将用于创建粘滞会话并避免每个前端 Web 服务器收到来自客户端的多个身份验证请求。 sharepoint 2013 中的新分布式缓存服务在 sharepoint 服务器场的 web 服务器上存储和分发登录令牌。 
    
- exchange In exchange 2013, CAS 角色旨在使用第4层负载平衡, 在传输层分发请求。 这可以大大降低负载平衡器的利用率和工作负载。 
    
- lync 池的会话初始协议 (SIP) 流量建议使用 Lync 域名系统 (DNS) 负载平衡。 Lync Web (HTTPS) 通信需要硬件负载平衡 (HLB)。 
    
### <a name="remote-access-options"></a>远程访问选项

有多个选项可以为 Internet 上的合作伙伴发布 Intranet 资源，或者为远程或漫游员工提供安全远程访问。例如反向代理、DirectAccess 和第三方 VPN 网关。本节稍后讨论的远程访问解决方案可能会用于本地部署中的 SharePoint、Lync 和 Exchange，或者用于这些服务器的任意组合。但是，某些远程选项可能不适用于特定的解决方案。   
  
反向代理-反向代理支持流量加密 (如安全套接字层 (SSL)), 您可以使用它将 intranet 应用程序和 web 资源发布到 Internet 上的经过身份验证的用户和合作伙伴。 例如 Microsoft Forefront 统一访问网关 (UAG)。 许多硬件负载平衡器也支持反向代理功能。 但是, 仍有适用于使用独立解决方案的有效方案, 具体取决于您的需求和要求, 例如流量隔离、安全 compartmentalization 和性能优化。 
  
反向代理的优点和注意事项： 
  
- 为访问 Intranet 资源的合作伙伴或用户提供经过身份验证的安全访问（使用客户端和反向代理服务器之间的 SSL (TCP 443)）。  
    
- 对于 Exchange，使用反向代理（例如 Forefront UAG）的优势之一就是在访问 Exchange 客户端访问服务器之前预先进行身份验证。使用 Outlook Web Access (OWA) 等已发布应用程序的远程访问用户可以在进入内部网络之前，使用基本、NTLM 或 Kerberos 方法进行身份验证。  
    
- 对于 Exchange 和 SharePoint，Forefront UAG 等解决方案可以终止 SSL 连接，并在提供单一证书管理点时减少 Intranet 资源服务器的负载。  
    
- 对于 Lync，Web (HTTPS) 通信通过反向代理 (TCP 443) 进行客户端通信。 反向代理可代理到 Lync Web 服务、Exchange CAS 和 Office Web Apps 的 HTTPS 连接。 Lync Server 2013 不支持 UAG。 
    
DirectAccess-依靠 Internet 协议安全性 (IPsec) 进行身份验证和在 DirectAccess 客户端与服务器之间加密流量的远程访问技术。 DirectAccess 无需启动连接，即可为漫游和远程员工提供对 Internet 和 Intranet 资源的同时访问。 
  
关于 DirectAccess 要考虑的事项：  
  
- DirectAccess 在 DirectAccess 客户端和服务器之间使用 IPsec 保护的通信（协议 50/51 和 UDP 500）。  
    
- 适用于 Windows Server 2012 和 Windows 8 的 DirectAccess 不需要部署公钥基础结构 (PKI) 来实现服务器和客户端身份验证。  
    
- 我们建议您不要将 DirectAccess 与 Lync Server 2013 结合使用, 因为与 IPsec 加密和解密相关的音频和视频延迟问题。 
    
    vpn 网关-典型的 vpn 网关提供远程访问客户端计算机通过通过隧道和用户启动的连接在逻辑上投影到 intranet 的远程访问连接。 您可以在 Windows Server 2012 或多个第三方解决方案中使用统一远程访问，为漫游或远程员工提供对 Intranet 的安全访问。 Lync 不建议使用 VPN。 远程 Lync 通信应使用边缘服务器和拆分隧道。 
    
### <a name="domain-name-system-dns-considerations"></a>域名系统 (DNS) 的注意事项

您需要规划 DNS 记录集，允许 Internet 和 Intranet 用户将 DNS 名称解析为相应的 IP 地址。  
  
- 对于基于 Internet 的合作伙伴和漫游或远程员工，在 Internet DNS 服务器中注册的 DNS 记录可根据需要解析为与网关路由器、Lync 边缘服务器、负载平衡器上的虚拟 IP 地址 (VIP) 集以及 DirectAccess 或 VPN 网关对应的公共 IP 地址集。  
    
- 对于基于 Intranet 的用户，在 Intranet DNS 服务器中注册的 DNS 记录可在负载平衡器上解析为虚拟 IP 地址 (VIP) 集以访问 SharePoint、Lync 和 Exchange 资源。  
    
- 对于与 Intranet DNS 命名空间对应的名称，DirectAccess 客户端使用 Intranet DNS 服务器，否则使用 Internet DNS 服务器。要简化 DirectAccess 的操作，请考虑使用拆分 DNS 实施，它对基于 Intranet 和 Internet 的名称使用不同 DNS 命名空间。例如，对 Internet 命名空间使用 contoso.com，对 Intranet 命名空间使用 corp.contoso.com。  
    
- Exchange 使用拆分 DNS 模型，即对于公共路由的通信和公司网络，其主机到 IP 的解析不相同。您至少需要具有 OWA 的 DNS 记录、自动发现、客户端通信的 ActiveSync URL 和入站邮件的 MX 记录。  
    
- 如果您使用 Exchange Online Protection (EOP)，您的 MX 记录将指向该服务，而不是您的 Exchange 服务器场。  
    
- 对于 Exchange，您需要公共 DNS 中的所有权证明 TXT 记录以及联合组织 ID 才能设置联合共享。  
    
- 当远程访问 VPN 连接处于活动状态时，远程访问 VPN 客户端可以设置为仅使用 Intranet DNS 服务器。  
    
### <a name="diagram-description"></a>图示说明

此图提供了一个示例网络拓扑，其中说明了通过网关路由器的入站和出站通信，以及到相应的 SharePoint、Exchange 和 Lync 服务器层的客户端会话通信（外部和内部）的负载平衡。此图的说明分为两个部分：  
  
- 图中所示组件的说明  
    
- 说明通信如何通过组件传送到 SharePoint、Exchange、Lync 和 Office Web Apps 服务器层。  
    
#### <a name="description-of-components-shown-in-the-diagram"></a>图中所示组件的说明

#### <a name="user-types"></a>用户类型

有四种不同类型的用户，三种位于网络和云服务外，一种为内部用户，包括：  
  
- 合作伙伴公司（企业对企业）-外部  
    
- 个人合作伙伴（SharePoint 和匿名 (Lync)）-外部  
    
- 漫游和远程员工-外部  
    
- 内部员工 
    
#### <a name="cloud-based-email-traffic"></a>基于云的电子邮件通信

对于基于 SMTP（Internet 邮件主机或 Exchange Online Protection）的电子邮件通信，存在一个基于云的组件。  
  
#### <a name="authentication-for-external-access"></a>外部访问的身份验证

对于每种用户类型，Lync、SharePoint 和 Exchange 均有一系列特定的身份验证过程。本文档后面会更详细地介绍。  
  
#### <a name="gateway-router-with-acls"></a>ACL 的网关路由器

网关路由器位于网络的边缘并路由发送到 Intranet 以及从中发出的所有传入和传出通信。  
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Lync 和 SharePoint 的远程访问服务器

此拓扑包括 Lync 边缘服务器和 SharePoint VPN 网关或 DirectAccess 服务器。  
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>负载平衡器和反向代理设备

您可以使用硬件或软件负载平衡解决方案重定向各个分段的通信，包括 SharePoint 前端 Web 服务器和 Exchange 客户端访问服务器 (CAS)。此拓扑显示负载平衡器中的 Lync VIP、SharePoint VIP 和 Exchange VIP 组件。  
  
#### <a name="servers"></a>Servers

有四台服务器: Lync、SharePoint、Exchange 和 Office Web Apps Server。 每个服务器可以有三个层级：前端客户端访问层、应用程序层和数据库/存储层。
  
#### <a name="front-end-client-access-tier"></a>前端客户端访问层

该层在全部四个服务器上均具有组件：  
  
- Lync 池（前端）。该图显示两个 Lync 数据库。  
    
- SharePoint 前端和分布式缓存。该图显示三个 SharePoint 数据库。   
    
- Exchange CAS。该图显示两个 Exchange 数据库。  
    
- Office Web Apps Server。该图显示两个 Office Web Apps 数据库。  
    
#### <a name="application-tier"></a>应用程序层

该层仅在 SharePoint 服务器上具有组件：  
  
- 搜索（查询、索引、管理）。该图显示三个 SharePoint 数据库。  
    
- 批处理。该图显示三个 SharePoint 数据库。   
    
#### <a name="databasestorage-tier"></a>数据库/存储层

该层在 Lync、SharePoint 和 Exchange 服务器上具有组件：  
  
- Lync 数据库（后端）。该图显示三个 Lync 数据库。  
    
- SharePoint 数据库。该图显示三个 SharePoint 数据库。  
    
- Exchange 邮箱服务器。该图显示两个 Exchange 邮箱数据库。  
    
有关安装在每个 SharePoint 服务器角色上的组件的详细信息, 请参阅[精简拓扑 for sharepoint 2013](https://aka.ms/Ma5cgk)。 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>说明通信如何通过组件传递到不同的服务器层

本节介绍用户请求如何通过网络拓扑传递。   
  
#### <a name="authentication-and-routing-for-external-access"></a>外部访问的身份验证和路由

网络和云服务外有三种不同类型的客户端，包括：  
  
- 合作伙伴公司（企业对企业）-外部  
    
- 个人合作伙伴（SharePoint 和匿名 (Lync)）-外部  
    
- 漫游和远程员工-外部  
    
每种外部用户类型的身份验证和路由过程分别如下所述。  
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>合作伙伴公司 (企业对企业) (https://partnerweb.contoso.com)

- Lync：与其他组织建立联合信任，Skype 通过公共 IM 连接 (PIC) 与 AOL 建立联合信任。Lync 联合通信通过网关路由器依次传递到 Lync 边缘服务器、Lync VIP（负载平衡器/反向代理服务器）和 Lync Server。  
    
- SharePoint：使用 SAML 身份验证的受信任的合作伙伴标识提供程序。SharePoint 客户端通信通过网关路由器依次传递到 SharePoint VIP（负载平衡器/反向代理服务器）和 SharePoint Server。  
    
- Exchange：邮件通信使用相互身份验证 TLS，联合共享使用 SAML 身份验证。Exchange 客户端通信通过网关路由器依次传递到 Exchange VIP（负载平衡器/反向代理服务器）和 Exchange Server。  
    
- SMTP 客户端通信通过网关路由器依次传递到 Exchange VIP（负载平衡器/反向代理服务器）和 Exchange Server。  
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>单个合作伙伴 (SharePoint) 和匿名 (Lync) (https://partnerweb.contoso.com和https://meet.contoso.com)

- Lync：匿名用户只能加入员工组织的 Lync 会议。Lync 联合通信通过网关路由器依次传递到 Lync 边缘服务器、Lync VIP（负载平衡器/反向代理服务器）和 Lync Server。   
    
- SharePoint：使用 SAML 身份验证或基于表单的身份验证的受信任的合作伙伴标识提供程序。SharePoint 客户端通信通过网关路由器依次传递到 SharePoint VIP（负载平衡器/反向代理服务器）和 SharePoint Server。  
    
- Exchange：不适用。 
    
- Lync Web 通信通过网关路由器依次传递到 Lync 边缘服务器、Lync VIP（负载平衡器/反向代理服务器）、硬件负载平衡器（HTTPS 通信需要）和 Lync Server。  
    
#### <a name="roaming-and-remote-employees"></a>漫游和远程员工

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* Exchange URL 具有以下虚拟目录: 自动发现、ecp、EWS、Microsoft-服务器-ActiveSync、OAB、owa、PowerShell 
  
- Lync：TLS-DSK 或 NTLM 身份验证。Lync 客户端通信通过网关路由器依次传递到 Lync 边缘服务器、Lync VIP（负载平衡器/反向代理服务器）和 Lync Server。  
    
- SharePoint：Active Directory 域服务 (AD DS)、基于表单的身份验证或 SAML 身份验证。SharePoint 客户端通信通过 VPN 网关或 DirectAccess 服务器依次传递到 SharePoint VIP（负载平衡器/反向代理服务器）和 SharePoint Server。  
    
- Exchange：通过 SSL 的基本身份验证（ActiveSync、自动发现）、基于表单的身份验证 (OWA)。Exchange 客户端通信通过网关路由器依次传递到 Exchange VIP（负载平衡器/反向代理服务器）和 Exchange Server。  
    
- Lync 客户端通信通过网关路由器依次传递到 Lync VIP（负载平衡器/反向代理服务器）、硬件负载平衡器（HTTPS 通信需要）和 Lync Server。  
    
#### <a name="authentication-for-internal-access"></a>内部访问的身份验证

#### <a name="internal-employees"></a>内部员工

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- Lync：Kerberos、TLS-DSK 或 NTLM 身份验证。Lync 客户端通信依次传递到 Lync VIP（负载平衡器/反向代理服务器）和 Lync Server。  
    
- SharePoint：Active Directory 域服务 (AD DS)、基于表单的身份验证或 SAML 身份验证。SharePoint 客户端通信依次传递到 SharePoint VIP（负载平衡器/反向代理服务器）和 SharePoint Server。  
    
- Exchange：AD DS、基于表单的身份验证。Exchange 客户端通信依次传递到 Exchange VIP（负载平衡器/反向代理服务器）和 Exchange Server。  
    
- Lync 客户端通信依次传递到 Lync VIP（负载平衡器/反向代理服务器）、硬件负载平衡器（HTTPS 通信需要）和 Lync Server。  
    
#### <a name="cloud-based-email-traffic"></a>基于云的电子邮件通信

基于 SMTP 的电子邮件通信的基于云的组件由 Internet 邮件主机或 Exchange Online Protection 组成。
  
这些组件使用 SMTP 在网络上移动电子邮件流量。通信通过网关路由器依次传递到 Exchange VIP（负载平衡器/反向代理服务器）和 Exchange Server。  
  
### <a name="network-traffic-legend"></a>网络通信图例

图例方框以图形的形式显示不同类型的通信，如图中不同颜色的线条所示：  
  
- 绿色线条: Lync SIP 流量 
    
- 蓝色线条：Lync Web 通信  
    
- 紫色线条：SharePoint 客户端通信  
    
- 橙色线条：Exchange 客户端通信  
    
- 灰色线条：Exchange 内部部署和 Exchange Online Protection 之间的 Exchange 邮件服务器通信。  
    
不同类型的通信及其使用的端口也在图例方框中显示。  
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Lync SIP 通信和 Lync Web 通信

Lync 边缘服务器对外部用户通信使用以下端口：   
  
- 信号处理/IM 通信 (SIP/SIMPLE)：TCP 端口 443（开放用于入站通信）  
    
- Web 会议通信 (PSOM)：TCP 端口 443（开放用于入站通信）  
    
- A/V 通信 (SRTP)：TCP 443、UDP 3478 和 TCP 50000-59999（可选，开放用于入站和出站通信）  
    
Lync 边缘服务器对联合通信使用以下端口：   
  
- TCP 端口 5061 (SIP)、5269 (XMPP)、443 和 UDP 3478 (SRTP)（开放用于入站和出站通信）  
    
#### <a name="sharepoint-client-traffic"></a>SharePoint 客户端通信

SharePoint 可以使用 TCP 端口 443 (SSL) 处理客户端和负载平衡器之间的加密通信。对于来自 Internet 的外部访问，必须为网关路由器（或外部防火墙）上的入站和出站通信打开此端口。  
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Exchange 客户端通信和 Exchange 邮件服务器通信

Exchange 使用 TCP 端口 25 (SMTP) 处理服务器到服务器通信。 大部分客户端通信（OWA、ActiveSync、自动发现、Outlook 无处不在）均通过端口 443 (HTTPS) 进行处理。 如果您具有 POP 或 IMAP 客户端，则还会使用端口 110 (POP3)、995（加密 POP3）、143 (IMAP4)、993（加密 IMAP4）和 587 (SMTP) 来支持这些客户端。 
  
#### <a name="more-on-lync-network-traffic"></a>有关 Lync 网络通信的更多信息？

了解 Lync Server 如何帮助您的组织提供即时消息、Web 会议、应用程序共享和语音通信。 有关详细信息, 请参阅[Microsoft Lync Server 2013 协议工作负荷海报](https://aka.ms/G5jzjo)。 
  
此海报中还包含用于访问此信息的 QR 代码。 
  

