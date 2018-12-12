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
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503045"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="98679-103">可访问的图 - Microsoft Azure for SharePoint 2013 中的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="98679-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="98679-104">**摘要：** 这篇文章是图为 SharePoint 2013 名 Microsoft Azure 中的 Internet 站点的辅助功能的文本版本。</span><span class="sxs-lookup"><span data-stu-id="98679-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="98679-p101">此海报介绍并演示了面向公众的 Internet 网站如何从针对客户帐户的云弹性和 Azure AD 中受益。有六个不同的方案描述了 Internet 网站如何从 Azure 中受益： </span><span class="sxs-lookup"><span data-stu-id="98679-p101">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts. There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="98679-107">设计服务器场拓扑并调整其大小。 </span><span class="sxs-lookup"><span data-stu-id="98679-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="98679-108">针对 Azure 进行微调。 </span><span class="sxs-lookup"><span data-stu-id="98679-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="98679-109">选择 Active Directory 模型。 </span><span class="sxs-lookup"><span data-stu-id="98679-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="98679-110">设计身份管理、区域和身份验证。 </span><span class="sxs-lookup"><span data-stu-id="98679-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="98679-111">为跨网站发布设计网站和 URL。 </span><span class="sxs-lookup"><span data-stu-id="98679-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="98679-112">设计 Azure 环境。 </span><span class="sxs-lookup"><span data-stu-id="98679-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="98679-113">设计服务器场拓扑并调整其大小</span><span class="sxs-lookup"><span data-stu-id="98679-113">Design and size the farm topology</span></span>

<span data-ttu-id="98679-114">使用 SharePoint 2013 在 TechNet 上的拓扑结构、 容量和性能指南设计服务器场拓扑结构。</span><span class="sxs-lookup"><span data-stu-id="98679-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="98679-115">确保您设计的服务器场满足容量和性能目标。 </span><span class="sxs-lookup"><span data-stu-id="98679-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="98679-116">示例：中等 Internet 网站场（每秒约 85 个页面视图）</span><span class="sxs-lookup"><span data-stu-id="98679-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="98679-117">此服务器场提供了容错功能的 SharePoint 2013 搜索服务器场拓扑结构优化的 corpus 3,400,000 项。</span><span class="sxs-lookup"><span data-stu-id="98679-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="98679-118">示例场处理 100-200 每秒，具体取决于所选语言的文档，它接纳每秒第二个和 100 查询每 85 页视图。</span><span class="sxs-lookup"><span data-stu-id="98679-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="98679-119">随附的图显示了具有三类服务器的中型 Internet 网站： </span><span class="sxs-lookup"><span data-stu-id="98679-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="98679-120">Web 服务器</span><span class="sxs-lookup"><span data-stu-id="98679-120">Web servers</span></span> 
    
- <span data-ttu-id="98679-121">应用程序服务器</span><span class="sxs-lookup"><span data-stu-id="98679-121">Application servers</span></span> 
    
- <span data-ttu-id="98679-122">数据库服务器</span><span class="sxs-lookup"><span data-stu-id="98679-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="98679-123">Web 服务器</span><span class="sxs-lookup"><span data-stu-id="98679-123">Web servers</span></span>

<span data-ttu-id="98679-p102">在 Web 服务器部分，有三台 Web 服务器，即主机 A、主机 B 和主机 C。每台 Web 服务器均包含分布式缓存、用户配置文件、托管元数据和查询处理功能。每台服务器中还包含一个索引分区副本。  </span><span class="sxs-lookup"><span data-stu-id="98679-p102">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities. They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="98679-126">要进行横向扩展，请添加一台具有相同功能的额外 Web 服务器，该服务器允许每秒多查看 28 页。 </span><span class="sxs-lookup"><span data-stu-id="98679-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="98679-127">应用程序服务器</span><span class="sxs-lookup"><span data-stu-id="98679-127">Application servers</span></span>

<span data-ttu-id="98679-p103">在应用程序服务器部分，有三台应用程序服务器，即主机 D、主机 E 和主机 F。主机 D 包含爬网、管理、分析和内容处理组件。主机 E 包含爬网、管理和内容处理组件。主机 F 包含爬网和内容处理组件。 </span><span class="sxs-lookup"><span data-stu-id="98679-p103">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components. Host E contains Crawl, Admin, and Content processing components. Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="98679-131">要进行横向扩展，添加一台带有爬网组件和内容处理组件的应用程序服务器，从而每秒多处理 40 个文档。 </span><span class="sxs-lookup"><span data-stu-id="98679-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="98679-132">数据库服务器</span><span class="sxs-lookup"><span data-stu-id="98679-132">Database servers</span></span>

<span data-ttu-id="98679-133">在数据库服务器部分，有两台服务器，即主机 G 和主机 H。数据库服务器位于成对主机中以实现容错。 </span><span class="sxs-lookup"><span data-stu-id="98679-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="98679-p104">主机 G 包含所有 SharePoint 数据库，包括搜索管理数据库、链接数据库、两个爬网数据库、分析数据库和所有其他 SharePoint 数据库。主机 H 包含所有 SharePoint 数据库，包括使用 SQL 群集、镜像或 SQL Server 2012 AlwaysOn 的所有数据库的冗余副本。 </span><span class="sxs-lookup"><span data-stu-id="98679-p104">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases. Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="98679-136">针对 Azure 进行微调</span><span class="sxs-lookup"><span data-stu-id="98679-136">Fine-tune for Azure</span></span>

<span data-ttu-id="98679-p105">SharePoint 服务器场可能需要在 Azure 平台中针对可用性集进行优化。要确保所有组件的高可用性，请确保服务器角色的配置均相同。</span><span class="sxs-lookup"><span data-stu-id="98679-p105">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform. To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="98679-139">在图中的示例拓扑中： </span><span class="sxs-lookup"><span data-stu-id="98679-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="98679-140">Web 服务器和数据库服务器的配置相同。 </span><span class="sxs-lookup"><span data-stu-id="98679-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="98679-p106">三台应用程序服务器的配置不相同。这些服务器角色需要针对 Azure 中的可用性集进行优化。</span><span class="sxs-lookup"><span data-stu-id="98679-p106">The three application servers are not identically configured. These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="98679-143">之前</span><span class="sxs-lookup"><span data-stu-id="98679-143">Before</span></span>

<span data-ttu-id="98679-p107">图中的顶部显示了在针对 Azure 中的可用性集进行优化之前的 SharePoint 服务器场。图中三台主机应用程序服务器的配置不相同。组件的数量取决于服务器场的性能和容量目标。三台服务器的配置如下所示： </span><span class="sxs-lookup"><span data-stu-id="98679-p107">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure. In the diagram, the three host application servers are not identically configured. The number of components is determined by the performance and capacity targets for the farm. The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="98679-148">主机 D 应用程序服务器配置了爬网、管理、分析和内容处理角色。 </span><span class="sxs-lookup"><span data-stu-id="98679-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="98679-149">主机 E 应用程序服务器配置了爬网、管理和内容处理角色。 </span><span class="sxs-lookup"><span data-stu-id="98679-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="98679-150">主机 F 应用程序服务器配置了爬网和内容处理角色。 </span><span class="sxs-lookup"><span data-stu-id="98679-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="98679-151">之后</span><span class="sxs-lookup"><span data-stu-id="98679-151">After</span></span>

<span data-ttu-id="98679-p108">图中的这一部分显示在 Azure 的 SharePoint 场后它已被微调的可用性设置。Azure 的适应这种体系结构，我们将在所有三个服务器之间复制的四个组件。这增加了超出所需的性能和容量的组件数。代价是，这种设计可以确保高可用性在 Azure 平台中的所有四个组件的这些三个虚拟机分配到可用性组时。</span><span class="sxs-lookup"><span data-stu-id="98679-p108">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="98679-156">三台服务器均配置为全部具有爬网、管理、分析和内容处理角色。 </span><span class="sxs-lookup"><span data-stu-id="98679-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="98679-157">选择 Active Directory 模型</span><span class="sxs-lookup"><span data-stu-id="98679-157">Choose the Active Directory model</span></span>

<span data-ttu-id="98679-p109">所有 SharePoint 解决方案都需要 Windows Active Directory 域服务 (AD DS)。目前，Azure 中的 SharePoint 解决方案具有两个选项。  </span><span class="sxs-lookup"><span data-stu-id="98679-p109">All SharePoint solutions require Windows Active Directory Domain Services (AD DS). At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="98679-p110">选项 1： 专用的域 — — 您可以部署到 Azure 支持 SharePoint 场专门和独立的域。这是一个不错的选择，为面向公众的 Internet 站点。</span><span class="sxs-lookup"><span data-stu-id="98679-p110">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm. This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="98679-p111">选项 2： 扩展通过站点到站点 VPN 连接的内部域。扩展的内部域通过站点到站点 VPN 连接时，用户会访问 SharePoint 场当作承载的内部部署。您可以利用您的现有活动目录和 DNS 实现。</span><span class="sxs-lookup"><span data-stu-id="98679-p111">Option 2: Extend the on-premises domain through a site-to-site VPN connection. When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises. You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="98679-165">身份管理、区域和身份验证的设计</span><span class="sxs-lookup"><span data-stu-id="98679-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="98679-166">帐户和身份验证的设计</span><span class="sxs-lookup"><span data-stu-id="98679-166">Design for accounts and authentication</span></span>

<span data-ttu-id="98679-167">确定帐户的管理方式以及将要使用的身份验证类型。 </span><span class="sxs-lookup"><span data-stu-id="98679-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="98679-168">网站开发人员和作者的帐户</span><span class="sxs-lookup"><span data-stu-id="98679-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="98679-169">将帐户添加到 Azure 中的域。 </span><span class="sxs-lookup"><span data-stu-id="98679-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="98679-170">在本地使用 Active Directory 联合身份验证服务 (AD FS) 将内部帐户联合到 Azure 中的域。 </span><span class="sxs-lookup"><span data-stu-id="98679-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="98679-171">如果设计中包含站点到站点 VPN 连接，使用内部帐户。 </span><span class="sxs-lookup"><span data-stu-id="98679-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="98679-172">客户的帐户</span><span class="sxs-lookup"><span data-stu-id="98679-172">Accounts for customers</span></span>

- <span data-ttu-id="98679-173">使用 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="98679-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="98679-174">使用基于 SAML 的不同提供程序。 </span><span class="sxs-lookup"><span data-stu-id="98679-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="98679-175">区域的设计</span><span class="sxs-lookup"><span data-stu-id="98679-175">Design for zones</span></span>

<span data-ttu-id="98679-176">在 SharePoint 2013 中，应将身份管理纳入区域和身份验证配置的考虑范围。 </span><span class="sxs-lookup"><span data-stu-id="98679-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="98679-177">该设计将客户帐户与所有其他帐户明确区分开来。 </span><span class="sxs-lookup"><span data-stu-id="98679-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="98679-178">如果您希望客户帐户被视为与作者和站点开发人员的内部帐户完全不同，请使用该设计。 </span><span class="sxs-lookup"><span data-stu-id="98679-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="98679-179">使用该设计，您可以使用区域策略来限制某个 Web 应用程序内的客户操作。 </span><span class="sxs-lookup"><span data-stu-id="98679-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="98679-180">该设计将对客户帐户和内部帐户产生不同的  URL。 </span><span class="sxs-lookup"><span data-stu-id="98679-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="98679-181">在此示例中：</span><span class="sxs-lookup"><span data-stu-id="98679-181">In this example:</span></span> 
  
- <span data-ttu-id="98679-182">为内部帐户配置默认区域。</span><span class="sxs-lookup"><span data-stu-id="98679-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="98679-p112">配置 Extranet 区域以获得客户通过身份验证后的访问权限。对客户帐户使用 Azure Active Directory (AD)，或者使用基于 SAML 的其他提供程序。 </span><span class="sxs-lookup"><span data-stu-id="98679-p112">Configure the extranet zone for customer authenticated access. Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="98679-185">配置 Internet 区域以进行匿名访问。</span><span class="sxs-lookup"><span data-stu-id="98679-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="98679-186">不要使用所有已通过身份验证的用户被配置为使用默认区域的两个区域设计。</span><span class="sxs-lookup"><span data-stu-id="98679-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="98679-187">随附的图显示了将内部帐户和客户帐户区分开来的三区域设计。  </span><span class="sxs-lookup"><span data-stu-id="98679-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="98679-p113">访问者和客户访问 SharePoint 2013 场内 Azure AD 租户通过 web 应用程序在两个区域之一。包括两个区域：</span><span class="sxs-lookup"><span data-stu-id="98679-p113">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones. The two zones include:</span></span> 
  
- <span data-ttu-id="98679-190">区域：针对匿名用户的 Internet </span><span class="sxs-lookup"><span data-stu-id="98679-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="98679-191">区域：针对经过身份验证的用户的 Extranet </span><span class="sxs-lookup"><span data-stu-id="98679-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="98679-p114">在通过 VPN 隧道连接到 Azure AD 的本地环境中，具有内部帐户的用户从 AD DS 和 AD FS 访问 Azure Active Directory 租户。默认区域提供 Windows 身份验证 (NTLM)。 </span><span class="sxs-lookup"><span data-stu-id="98679-p114">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD. The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="98679-194">用于连接到 Azure AD 的设计</span><span class="sxs-lookup"><span data-stu-id="98679-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="98679-p115">Azure AD 提供云服务的身份管理和访问控制功能，包括对目录数据的基于云的存储和核心身份服务集，其中包括用户登录过程、身份验证服务和 AD FS。Azure AD 中包括的身份服务可以轻松地与本地 AD DS 部署集成，并且完成第三方身份提供程序。</span><span class="sxs-lookup"><span data-stu-id="98679-p115">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="98679-198">随附的图显示了以下方案： </span><span class="sxs-lookup"><span data-stu-id="98679-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="98679-199">当与 Azure Active Directory 集成 SharePoint 2013，Azure 访问控制服务 (ACS) 将有两个目的：</span><span class="sxs-lookup"><span data-stu-id="98679-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="98679-p116"> Azure AD 使用 SAML 2.0，SharePoint 仅适用于 SAML 1.1。ACS 了解这两种格式，并充当在 SharePoint 和 Azure AD 之间转换令牌格式的中介。   </span><span class="sxs-lookup"><span data-stu-id="98679-p116">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1. ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="98679-202">对于此 SAML 方案，ACS 取代了身份提供程序安全令牌服务 (IP-STS)。 </span><span class="sxs-lookup"><span data-stu-id="98679-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="98679-203">有关详细信息，请参阅 TechNet 库中的“使用 SharePoint 2013 配置 Azure AD”。 </span><span class="sxs-lookup"><span data-stu-id="98679-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="98679-204">设计用于跨网站发布的网站和 URL</span><span class="sxs-lookup"><span data-stu-id="98679-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="98679-205">对于发布方案，建议使用单 Web 应用程序设计。 </span><span class="sxs-lookup"><span data-stu-id="98679-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="98679-206">创作和发布网站位于同一个 Web 应用程序中。 </span><span class="sxs-lookup"><span data-stu-id="98679-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="98679-207">跨网站发布用于发布资产。 </span><span class="sxs-lookup"><span data-stu-id="98679-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="98679-208">使用基于路径和主机命名的网站集。</span><span class="sxs-lookup"><span data-stu-id="98679-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="98679-p117">根网站集是必备条件。将此网站创建为基于路径的网站。  </span><span class="sxs-lookup"><span data-stu-id="98679-p117">A root site collection is a requirement. Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="98679-211">将所有其他网站集创建为主机命名的网站集。 </span><span class="sxs-lookup"><span data-stu-id="98679-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="98679-212">Web 应用程序和根网站 URL </span><span class="sxs-lookup"><span data-stu-id="98679-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="98679-p118">对 Web 应用程序 URL 使用内部名称 SharePoint 使用本地计算机名称作为默认名称，除非指定了其他名称。您可以使用保留用于内部网络环境的域名称。  </span><span class="sxs-lookup"><span data-stu-id="98679-p118">Use an internal name for the web application URL. SharePoint uses the local machine name as the default name unless a different name is specified. You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="98679-p119">创建 Web 应用程序时，SharePoint 会指定一个非标准端口号。使用此端口号，而非端口 80 或端口 443。或者使用不同的非标准端口号。 </span><span class="sxs-lookup"><span data-stu-id="98679-p119">SharePoint assigns a nonstandard port number when the web application is created. Use this port number instead of port 80 or port 443. Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="98679-219">对根网站集（基于路径的网站集）使用相同的名称和端口号。 </span><span class="sxs-lookup"><span data-stu-id="98679-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="98679-p120">随附的图显示了应用程序池服务，例如使用 Web 应用程序与网站集交互的 Search。所示网站集包括： </span><span class="sxs-lookup"><span data-stu-id="98679-p120">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications. The site collections shown include:</span></span> 
  
- <span data-ttu-id="98679-222">基于路径的网站集，位于 http://internal:8000（根网站）。 </span><span class="sxs-lookup"><span data-stu-id="98679-222">Path-based site collection located at http://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="98679-223">爬网：基于主机的网站集，位于以下类似地址：https://authoring.contoso.com:8000。 </span><span class="sxs-lookup"><span data-stu-id="98679-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="98679-224">查询：两个单独的主机命名网站集，位于以下类似地址： </span><span class="sxs-lookup"><span data-stu-id="98679-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - <span data-ttu-id="98679-225">http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="98679-225">http://www.contoso.com</span></span> 
    
  - <span data-ttu-id="98679-226">https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="98679-226">https://secure.contoso.com</span></span> 
    
  - <span data-ttu-id="98679-227">http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="98679-227">http://www.contoso.com:8000</span></span> 
    
  - <span data-ttu-id="98679-228">http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="98679-228">http://assets.contoso.com</span></span> 
    
  - <span data-ttu-id="98679-229">https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="98679-229">https://secureassets.contoso.com</span></span> 
    
  - <span data-ttu-id="98679-230">http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="98679-230">http://assets.contoso.com:8000</span></span> 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="98679-231">设计 Azure 环境</span><span class="sxs-lookup"><span data-stu-id="98679-231">Design the Azure environment</span></span>

<span data-ttu-id="98679-232">此示例体系结构包含以下元素： </span><span class="sxs-lookup"><span data-stu-id="98679-232">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="98679-233">站点到站点 VPN 连接是可选的，可将本地 Windows AD DS 和 DNS 环境扩展到 Azure 中的虚拟网络。 </span><span class="sxs-lookup"><span data-stu-id="98679-233">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="98679-234">可以选择使用 Azure 中的专用域来支持 SharePoint 服务器场。 </span><span class="sxs-lookup"><span data-stu-id="98679-234">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="98679-235">服务器基于角色跨 Azure 云服务拆分。 </span><span class="sxs-lookup"><span data-stu-id="98679-235">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="98679-236">可用性集可确保相同配置的服务器角色的高可用性。  </span><span class="sxs-lookup"><span data-stu-id="98679-236">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="98679-237">有关详细信息，请参阅 TechNet 上的以下文章：SharePoint 解决方案的 Azure 体系结构。 </span><span class="sxs-lookup"><span data-stu-id="98679-237">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="98679-238">随附的图显示了连接到 Azure 虚拟网络的本地环境示例。   </span><span class="sxs-lookup"><span data-stu-id="98679-238">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="98679-239">本地环境中包括以下组件，这是 Azure 环境的可选元素： </span><span class="sxs-lookup"><span data-stu-id="98679-239">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="98679-240">Windows Server 2012 RRAS </span><span class="sxs-lookup"><span data-stu-id="98679-240">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="98679-241">AD DS</span><span class="sxs-lookup"><span data-stu-id="98679-241">AD DS</span></span> 
    
- <span data-ttu-id="98679-242">Windows Server 和 AD DS 到活动 VPN 网关子网的 VPN 网关。 </span><span class="sxs-lookup"><span data-stu-id="98679-242">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="98679-243">Azure 虚拟网络环境包括以下组件： </span><span class="sxs-lookup"><span data-stu-id="98679-243">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="98679-244">活动 VPN 网关子网（如果适用，可能与本地环境重叠） </span><span class="sxs-lookup"><span data-stu-id="98679-244">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="98679-245">包括 AD DS 和 DNS 可用性集（两台服务器）的云服务 </span><span class="sxs-lookup"><span data-stu-id="98679-245">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="98679-246">包括前端服务器可用性集（三台 SharePoint 服务器）和应用程序服务器可用性集（三台 SharePoint 服务器）的云服务 </span><span class="sxs-lookup"><span data-stu-id="98679-246">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="98679-247">包含两个数据库可用性集的云服务 </span><span class="sxs-lookup"><span data-stu-id="98679-247">Cloud service that contains two database availability sets</span></span> 
    

