---
title: 可访问的图 - Microsoft Azure for SharePoint 2013 中的 Internet 站点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: 本文是名为“Microsoft Azure for SharePoint 2013 中的 Internet 网站”的图的可访问文本版本。
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487688"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>可访问的图 - Microsoft Azure for SharePoint 2013 中的 Internet 站点

**摘要:** 本文是 Microsoft Azure for SharePoint 2013 中名为 Internet 站点的图表的可访问文本版本。
  
此海报介绍并演示了面向公众的 Internet 网站如何从针对客户帐户的云弹性和 Azure AD 中受益。有六个不同的方案描述了 Internet 网站如何从 Azure 中受益：  
  
- 设计服务器场拓扑并调整其大小。  
    
- 针对 Azure 进行微调。  
    
- 选择 Active Directory 模型。  
    
- 设计身份管理、区域和身份验证。  
    
- 为跨网站发布设计网站和 URL。  
    
- 设计 Azure 环境。  
    
## <a name="design-and-size-the-farm-topology"></a>设计服务器场拓扑并调整其大小

在 TechNet 上使用 SharePoint 2013 的拓扑、容量和性能指南来设计服务器场拓扑。 
  
确保您设计的服务器场满足容量和性能目标。  
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>示例：中等 Internet 网站场（每秒约 85 个页面视图）

此服务器场提供了容错的 SharePoint 2013 搜索服务器场拓扑, 该拓扑是针对包含3400000项的文档集进行优化的。 
  
示例服务器场每秒处理100-200 个文档, 具体取决于语言, 并且每秒有85个页面视图, 每秒100个查询。 
  
随附的图显示了具有三类服务器的中型 Internet 网站：  
  
- Web 服务器 
    
- 应用程序服务器 
    
- 数据库服务器 
    
#### <a name="web-servers"></a>Web 服务器

在 Web 服务器部分，有三台 Web 服务器，即主机 A、主机 B 和主机 C。每台 Web 服务器均包含分布式缓存、用户配置文件、托管元数据和查询处理功能。每台服务器中还包含一个索引分区副本。   
  
要进行横向扩展，请添加一台具有相同功能的额外 Web 服务器，该服务器允许每秒多查看 28 页。  
  
#### <a name="application-servers"></a>应用程序服务器

在应用程序服务器部分，有三台应用程序服务器，即主机 D、主机 E 和主机 F。主机 D 包含爬网、管理、分析和内容处理组件。主机 E 包含爬网、管理和内容处理组件。主机 F 包含爬网和内容处理组件。  
  
要进行横向扩展，添加一台带有爬网组件和内容处理组件的应用程序服务器，从而每秒多处理 40 个文档。  
  
#### <a name="database-servers"></a>数据库服务器

在数据库服务器部分，有两台服务器，即主机 G 和主机 H。数据库服务器位于成对主机中以实现容错。  
  
主机 G 包含所有 SharePoint 数据库，包括搜索管理数据库、链接数据库、两个爬网数据库、分析数据库和所有其他 SharePoint 数据库。主机 H 包含所有 SharePoint 数据库，包括使用 SQL 群集、镜像或 SQL Server 2012 AlwaysOn 的所有数据库的冗余副本。  
  
## <a name="fine-tune-for-azure"></a>针对 Azure 进行微调

SharePoint 服务器场可能需要在 Azure 平台中针对可用性集进行优化。要确保所有组件的高可用性，请确保服务器角色的配置均相同。 
  
在图中的示例拓扑中：  
  
- Web 服务器和数据库服务器的配置相同。  
    
- 三台应用程序服务器的配置不相同。这些服务器角色需要针对 Azure 中的可用性集进行优化。 
    
### <a name="before"></a>Before

图中的顶部显示了在针对 Azure 中的可用性集进行优化之前的 SharePoint 服务器场。图中三台主机应用程序服务器的配置不相同。组件的数量取决于服务器场的性能和容量目标。三台服务器的配置如下所示：  
  
- 主机 D 应用程序服务器配置了爬网、管理、分析和内容处理角色。  
    
- 主机 E 应用程序服务器配置了爬网、管理和内容处理角色。  
    
- 主机 F 应用程序服务器配置了爬网和内容处理角色。  
    
### <a name="after"></a>段后

图中的此部分显示已针对 Azure 中的可用性集进行微调后的 SharePoint 服务器场。 要调整 Azure 的此体系结构，我们将在所有三个服务器之间复制这四个组件。 这将增加除性能和容量所需组件以外的组件数量。 权衡点是当将这三个虚拟机分配至某个可用性集时，此设计确保了 Azure 平台中所有四个组件的高可用性。 
  
三台服务器均配置为全部具有爬网、管理、分析和内容处理角色。  
  
## <a name="choose-the-active-directory-model"></a>选择 Active Directory 模型

所有 SharePoint 解决方案都需要 Windows Active Directory 域服务 (AD DS)。目前，Azure 中的 SharePoint 解决方案具有两个选项。   
  
- 选项 1: 专用域-您可以将专用域和独立域部署到 Azure 以支持 SharePoint 场。 这是面向公众的 Internet 站点的最佳选择。 
    
- 选项 2: 通过站点到站点 VPN 连接扩展本地域。 当您通过站点到站点 VPN 连接扩展内部部署域时，用户将访问 SharePoint 服务器场，就像它在内部部署中承载一样。 您可以利用您现有的 Active Directory 和 DNS 实现。 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>身份管理、区域和身份验证的设计

### <a name="design-for-accounts-and-authentication"></a>帐户和身份验证的设计

确定帐户的管理方式以及将要使用的身份验证类型。  
  
#### <a name="accounts-for-site-developers-and-authors"></a>网站开发人员和作者的帐户

- 将帐户添加到 Azure 中的域。  
    
- 在本地使用 Active Directory 联合身份验证服务 (AD FS) 将内部帐户联合到 Azure 中的域。  
    
- 如果设计中包含站点到站点 VPN 连接，使用内部帐户。  
    
#### <a name="accounts-for-customers"></a>客户的帐户

- 使用 Azure Active Directory。 
    
- 使用基于 SAML 的不同提供程序。  
    
### <a name="design-for-zones"></a>区域的设计

在 SharePoint 2013 中，应将身份管理纳入区域和身份验证配置的考虑范围。  
  
该设计将客户帐户与所有其他帐户明确区分开来。  
  
- 如果您希望客户帐户被视为与作者和站点开发人员的内部帐户完全不同，请使用该设计。  
    
- 使用该设计，您可以使用区域策略来限制某个 Web 应用程序内的客户操作。  
    
- 该设计将对客户帐户和内部帐户产生不同的  URL。  
    
在此示例中： 
  
- 为内部帐户配置默认区域。 
    
- 配置 Extranet 区域以获得客户通过身份验证后的访问权限。对客户帐户使用 Azure Active Directory (AD)，或者使用基于 SAML 的其他提供程序。  
    
- 配置 Internet 区域以进行匿名访问。 
    
请勿使用配置为使用默认区域的所有经过身份验证的用户的双区域设计。 
  
随附的图显示了将内部帐户和客户帐户区分开来的三区域设计。   
  
访问者和客户通过两个区域之一中的 web 应用程序访问 SharePoint 2013 场中的 Azure AD 租户。 两个区域包括： 
  
- 区域：针对匿名用户的 Internet  
    
- 区域：针对经过身份验证的用户的 Extranet  
    
在通过 VPN 隧道连接到 Azure AD 的本地环境中，具有内部帐户的用户从 AD DS 和 AD FS 访问 Azure Active Directory 租户。默认区域提供 Windows 身份验证 (NTLM)。  
  
### <a name="design-for-connecting-to-azure-ad"></a>用于连接到 Azure AD 的设计

 Azure AD 提供云服务的身份管理和访问控制功能，包括对目录数据的基于云的存储和核心身份服务集，其中包括用户登录过程、身份验证服务和 AD FS。Azure AD 中包括的身份服务可以轻松地与本地 AD DS 部署集成，并且完成第三方身份提供程序。
  
随附的图显示了以下方案：  
  
将 SharePoint 2013 与 Azure Active Directory 集成时, azure 访问控制服务 (ACS) 有两个用途: 
  
-   Azure AD 使用 SAML 2.0，SharePoint 仅适用于 SAML 1.1。ACS 了解这两种格式，并充当在 SharePoint 和 Azure AD 之间转换令牌格式的中介。   
    
- 对于此 SAML 方案，ACS 取代了身份提供程序安全令牌服务 (IP-STS)。  
    
有关详细信息，请参阅 TechNet 库中的“使用 SharePoint 2013 配置 Azure AD”。  
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>设计用于跨网站发布的网站和 URL

对于发布方案，建议使用单 Web 应用程序设计。  
  
- 创作和发布网站位于同一个 Web 应用程序中。  
    
- 跨网站发布用于发布资产。  
    
使用基于路径和主机命名的网站集。 
  
- 根网站集是必备条件。将此网站创建为基于路径的网站。   
    
- 将所有其他网站集创建为主机命名的网站集。  
    
Web 应用程序和根网站 URL  
  
- 对 Web 应用程序 URL 使用内部名称 SharePoint 使用本地计算机名称作为默认名称，除非指定了其他名称。您可以使用保留用于内部网络环境的域名称。   
    
- 创建 Web 应用程序时，SharePoint 会指定一个非标准端口号。使用此端口号，而非端口 80 或端口 443。或者使用不同的非标准端口号。  
    
- 对根网站集（基于路径的网站集）使用相同的名称和端口号。  
    
随附的图显示了应用程序池服务，例如使用 Web 应用程序与网站集交互的 Search。所示网站集包括：  
  
- 位于http://internal:8000 (根网站) 的基于路径的网站集。 
    
- 爬网: 位于地址 (如) https://authoring.contoso.com:8000上的以主机命名的网站集。 
    
- 查询：两个单独的主机命名网站集，位于以下类似地址：  
    
  - http://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>设计 Azure 环境

此示例体系结构包含以下元素：  
  
- 站点到站点 VPN 连接是可选的，可将本地 Windows AD DS 和 DNS 环境扩展到 Azure 中的虚拟网络。  
    
- 可以选择使用 Azure 中的专用域来支持 SharePoint 服务器场。  
    
- 服务器基于角色跨 Azure 云服务拆分。  
    
- 可用性集可确保相同配置的服务器角色的高可用性。   
    
有关详细信息，请参阅 TechNet 上的以下文章：SharePoint 解决方案的 Azure 体系结构。  
  
随附的图显示了连接到 Azure 虚拟网络的本地环境示例。    
  
本地环境中包括以下组件，这是 Azure 环境的可选元素：  
  
- Windows Server 2012 RRAS  
    
- AD DS 
    
- Windows Server 和 AD DS 到活动 VPN 网关子网的 VPN 网关。  
    
Azure 虚拟网络环境包括以下组件：  
  
- 活动 VPN 网关子网（如果适用，可能与本地环境重叠）  
    
- 包括 AD DS 和 DNS 可用性集（两台服务器）的云服务  
    
- 包括前端服务器可用性集（三台 SharePoint 服务器）和应用程序服务器可用性集（三台 SharePoint 服务器）的云服务  
    
- 包含两个数据库可用性集的云服务  
    

