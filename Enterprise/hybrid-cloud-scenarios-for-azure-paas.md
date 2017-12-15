---
title: "Azure PaaS 的混合云方案"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "摘要： 了解在 Azure 中基于 Microsoft 平台即服务 (PaaS) 云产品的混合体系结构和方案。"
ms.openlocfilehash: f6d7d1c9ca04c0b7bbaa020a771cf84734e5d385
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="bc7b4-103">Azure PaaS 的混合云方案</span><span class="sxs-lookup"><span data-stu-id="bc7b4-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="bc7b4-104">**摘要：** 了解在 Azure 中基于 Microsoft 平台即服务 (PaaS) 云产品的混合体系结构和方案。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="bc7b4-105">将本地数据或计算资源与在 Azure PaaS 中运行的新的或已转换的应用程序结合使用，可以充分利用云的性能、可靠性和规模，为移动用户提供更好的支持。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="bc7b4-106">Azure PaaS 混合方案体系结构</span><span class="sxs-lookup"><span data-stu-id="bc7b4-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="bc7b4-107">图 1 显示了适用于 Azure 的 基于 Microsoft PaaS 的混合方案的体系结构。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="bc7b4-108">**图 1：Azure 中基于 Microsoft PaaS 的混合方案**</span><span class="sxs-lookup"><span data-stu-id="bc7b4-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Azure 中基于 Microsoft PaaS 的混合方案](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS.png)
  
<span data-ttu-id="bc7b4-110">针对体系结构的每一层：</span><span class="sxs-lookup"><span data-stu-id="bc7b4-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="bc7b4-111">应用和方案</span><span class="sxs-lookup"><span data-stu-id="bc7b4-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="bc7b4-112">混合 PaaS 应用程序在 Azure 中运行，并使用本地计算或存储资源。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="bc7b4-113">标识</span><span class="sxs-lookup"><span data-stu-id="bc7b4-113">Identity</span></span>
    
    <span data-ttu-id="bc7b4-114">由目录同步或与第三方标识提供程序的联合组成。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="bc7b4-115">网络</span><span class="sxs-lookup"><span data-stu-id="bc7b4-115">Network</span></span>
    
    <span data-ttu-id="bc7b4-p101">由现有的 Internet 管道或通过到 Azure PaaS 的公共对等建立的 ExpressRoute 连接组成。必须包括 Azure PaaS 应用程序访问本地计算或存储资源的方法。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="bc7b4-118">本地</span><span class="sxs-lookup"><span data-stu-id="bc7b4-118">On-premises</span></span>
    
    <span data-ttu-id="bc7b4-119">由标识和安全基础结构及现有的业务线 (LOB) 应用程序或数据库服务器组成，Azure PaaS 应用程序可以对其进行安全访问。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="bc7b4-120">Azure PaaS 混合应用程序</span><span class="sxs-lookup"><span data-stu-id="bc7b4-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="bc7b4-121">图 2 显示了在 Azure 中运行的混合应用程序的配置。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="bc7b4-122">**图 2：基于 Azure PaaS 的混合应用程序**</span><span class="sxs-lookup"><span data-stu-id="bc7b4-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![基于 Azure PaaS 的混合应用程序](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps.png)
  
<span data-ttu-id="bc7b4-p102">在图 2 中，本地网络在服务器上承载存储或应用程序以及包含代理服务器的 DMZ。它通过 Internet 或使用 ExpressRoute 连接来连接到 Azure PaaS 服务。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="bc7b4-126">组织可以通过以下方式使其计算或存储资源对 Azure PaaS 混合应用程序可用：</span><span class="sxs-lookup"><span data-stu-id="bc7b4-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="bc7b4-127">托管 DMZ 中服务器上的资源。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="bc7b4-128">在 DMZ 中托管反向代理服务器，这将允许对位于本地的资源执行经身份验证的请求、入站请求和基于 HTTPS 的请求。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="bc7b4-129">Azure 应用可以使用以下程序提供的凭据：</span><span class="sxs-lookup"><span data-stu-id="bc7b4-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="bc7b4-130">Azure AD，它可以与本地标识提供程序（如 Windows Server AD）同步。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="bc7b4-131">第三方标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="bc7b4-132">示例 Azure PaaS 混合应用程序</span><span class="sxs-lookup"><span data-stu-id="bc7b4-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="bc7b4-133">图 3 显示了在 Azure 中运行的混合应用程序的示例。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="bc7b4-134">**图 3：基于 Azure PaaS 的混合应用程序示例**</span><span class="sxs-lookup"><span data-stu-id="bc7b4-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![基于 Azure PaaS 的混合应用程序示例](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_Ex.png)
  
<span data-ttu-id="bc7b4-p103">在图 3 中，本地网络承载 LOB 应用程序。Azure PaaS 承载自定义的移动应用。Internet 上的智能电话访问 Azure 中的自定义移动应用，它将数据请求发送到本地 LOB 应用程序。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="bc7b4-p104">本示例中的 Azure PaaS 混合应用程序是提供有关员工最新联系信息的自定义移动应用。端到端的混合方案由以下各项组成：</span><span class="sxs-lookup"><span data-stu-id="bc7b4-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="bc7b4-141">需要经验证的本地凭据才能运行的智能电话应用。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="bc7b4-142">在 Azure PaaS 中运行的自定义移动应用，它根据用户智能电话应用的查询，请求有关特定员工的信息。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="bc7b4-143">DMZ 中的反向代理服务器，验证自定义移动应用，并将转发该请求。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="bc7b4-144">LOB 应用程序服务器场，根据用户帐户的权限，为联系人请求提供服务。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="bc7b4-145">由于本地标识提供程序已与 Azure AD 同步，自定义移动应用和 LOB 应用都可以验证请求用户的帐户名称。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="stretch-database-with-sql-server-2016"></a><span data-ttu-id="bc7b4-146">使用 SQL Server 2016 的 Stretch Database</span><span class="sxs-lookup"><span data-stu-id="bc7b4-146">Stretch Database with SQL Server 2016</span></span>

<span data-ttu-id="bc7b4-147">Stretch Database 是 SQL Server 2016 的一项功能，它可以使你以透明的方式安全地将原始数据（如包含客户订单信息的大型表中已结束的业务数据）移动到 Azure 中的 SQL Stretch Database。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-147">Stretch database is a feature of SQL Server 2016 that allows you to transparently and securely move cold data, such as closed business data in a large table that contains customer order information, to a SQL Stretch database in Azure.</span></span>
  
<span data-ttu-id="bc7b4-p105">延伸后，SQL Server 实例、数据库或者甚至单个表中的内容会是 SQL Server 2016 服务器中的本地数据和 Azure 中远程数据的组合。SQL Server 2016 会自动将变得符合条件的伸展数据移动至 Azure。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-p105">When stretched, the contents of a SQL Server instance, a database, or even a single table is the combination of local data in SQL Server 2016 server and remote data in Azure. Data that becomes eligible for stretch is automatically moved to Azure by SQL Server 2016.</span></span>
  
<span data-ttu-id="bc7b4-150">图 4 显示了使用 SQL Server 2016 的 Stretch Database。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-150">Figure 4 shows Stretch Database with SQL Server 2016.</span></span>
  
<span data-ttu-id="bc7b4-151">**图 4：使用 SQL Server 2016 的 Stretch Database**</span><span class="sxs-lookup"><span data-stu-id="bc7b4-151">**Figure 4: Stretch Database with SQL Server 2016**</span></span>

![使用 SQL Server 2016 的 Stretch Database](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_SQL.png)
  
<span data-ttu-id="bc7b4-p106">在图 4 中，本地网络承载一个服务器，该服务器运行配有小型本地数据库的 SQL Server 2016。Azure PaaS 承载 Azure SQL Server Stretch Database（包含扩展部分的数据库）的实例。从本地用户发送到本地 SQL 服务器的 T-SQL 查询已被安全转发到 Azure SQL Stretch Database，然后由该 Stretch Database 将结果返回给发出请求的用户。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-p106">In Figure 4, an on-premises network hosts a server running SQL Server 2016 with a small local database. Azure PaaS hosts an instance of Azure SQL Server Stretch Database with the stretched portion of the database. T-SQL queries from an on-premises user sent to the on-premises SQL server are securely forwarded to the Azure SQL Stretch Database, which returns the results to the requesting user.</span></span>
  
 <span data-ttu-id="bc7b4-p107">以透明方式将包含历史数据的用户查询转发到 Azure SQL Stretch Database。即使表已扩展，也无需重新写入这些查询。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-p107">User queries that include the historical data are transparently forwarded to Azure SQL Stretch database. The queries do not need to be re-written, even though the table is stretched.</span></span>
  
<span data-ttu-id="bc7b4-p108">Stretch Database 提供经济高效的选项，用于历史数据的长期存储和透明访问。它还解决了表变大时出现的性能和可用性问题。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-p108">Stretch database provides a cost-effective option for long-term storage and transparent access to historical data. It also solves performance and availability problems that arise when tables become very large.</span></span>
  
<span data-ttu-id="bc7b4-160">有关详细信息，请参阅 [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)。</span><span class="sxs-lookup"><span data-stu-id="bc7b4-160">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bc7b4-161">See Also</span><span class="sxs-lookup"><span data-stu-id="bc7b4-161">See Also</span></span>

[<span data-ttu-id="bc7b4-162">面向企业架构师的 Microsoft 混合云</span><span class="sxs-lookup"><span data-stu-id="bc7b4-162">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="bc7b4-163">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="bc7b4-163">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="bc7b4-164">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="bc7b4-164">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



