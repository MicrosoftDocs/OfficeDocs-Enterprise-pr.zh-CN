---
title: 可访问的图-Microsoft Azure for SharePoint 2013 中的设计示例 Internet 网站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
f1.keywords:
- NOCSH
description: 本文是名为“设计示例：Microsoft Azure for SharePoint 2013 中的 Internet 站点”的图的可访问文本版本。
ms.openlocfilehash: b3669304fee6b7a89bc5d1bde96c39c496122d48
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843793"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="c6b4c-103">可访问的图 - 设计示例：Microsoft Azure for SharePoint 2013 中的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="c6b4c-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="c6b4c-104">**摘要：** 本文是名为 "设计示例： Microsoft Azure for SharePoint 2013 中的 Internet 站点" 图表的可访问文本版本。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="c6b4c-105">使用此设计示例作为 Azure 中使用 SharePoint 2013 的面向 Internet 的网站的起始点。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="c6b4c-106">此海报显示了如何设计 SharePoint 2013 的以下方面的示例：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="c6b4c-107">用户</span><span class="sxs-lookup"><span data-stu-id="c6b4c-107">Users</span></span>
    
- <span data-ttu-id="c6b4c-108">区域和身份验证</span><span class="sxs-lookup"><span data-stu-id="c6b4c-108">Zones and authentication</span></span>
    
- <span data-ttu-id="c6b4c-109">服务器场</span><span class="sxs-lookup"><span data-stu-id="c6b4c-109">Server farm</span></span>
    
- <span data-ttu-id="c6b4c-110">管理网站</span><span class="sxs-lookup"><span data-stu-id="c6b4c-110">Administration site</span></span>
    
- <span data-ttu-id="c6b4c-111">服务</span><span class="sxs-lookup"><span data-stu-id="c6b4c-111">Services</span></span>
    
- <span data-ttu-id="c6b4c-112">应用程序池和 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="c6b4c-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="c6b4c-113">网站集</span><span class="sxs-lookup"><span data-stu-id="c6b4c-113">Site collections</span></span>
    
- <span data-ttu-id="c6b4c-114">站点</span><span class="sxs-lookup"><span data-stu-id="c6b4c-114">Sites</span></span>
    
- <span data-ttu-id="c6b4c-115">内容数据库</span><span class="sxs-lookup"><span data-stu-id="c6b4c-115">Content databases</span></span>
    
- <span data-ttu-id="c6b4c-116">区域和 URL</span><span class="sxs-lookup"><span data-stu-id="c6b4c-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="c6b4c-117">用户、区域和身份验证</span><span class="sxs-lookup"><span data-stu-id="c6b4c-117">Users, zones and authentication</span></span>

<span data-ttu-id="c6b4c-p101">此设计中有四种类型的用户帐户。每种帐户类型与一个用于访问的站点和使用特定身份验证类型的区域相关联。 </span><span class="sxs-lookup"><span data-stu-id="c6b4c-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="c6b4c-120">匿名客户—匿名客户可以通过网站访问，如https://www.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-120">Anonymous customers — Anonymous customers have access through a site such as https://www.contoso.com.</span></span> <span data-ttu-id="c6b4c-121">它们使用的区域是 "Internet 区域/匿名"，它使用匿名身份验证。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-121">The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="c6b4c-122">经过身份验证的客户—经过身份验证的客户可以https://secure.contoso.com通过网站访问，如。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-122">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com.</span></span> <span data-ttu-id="c6b4c-123">它们所使用的区域是 "Extranet 区域/SAML"，它将 Azure Active Directory 与 SAML 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-123">The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="c6b4c-124">网站作者和开发人员-网站作者和开发人员可以通过网站（ https://authoring.contoso.com:8000如https://www.contoso.com:8000或）访问网站。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-124">Site authors and developers — Site authors and developers have access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="c6b4c-125">它们使用的区域是使用 Active Directory 域服务（AD DS）的 "默认区域/Windows 集成"。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-125">The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="c6b4c-126">搜索爬网帐户-搜索爬网帐户可以通过网站（如https://authoring.contoso.com:8000或https://www.contoso.com:8000）访问。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-126">Search Crawl Account — The search crawl account has access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="c6b4c-127">它使用的区域是 "默认区域/Windows 集成"，它将 AD DS 与 Windows NTLM 身份验证结合使用。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-127">The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="c6b4c-128">服务器场</span><span class="sxs-lookup"><span data-stu-id="c6b4c-128">Server farm</span></span>

<span data-ttu-id="c6b4c-p106">用户通过 Azure 访问服务器场。服务器场中包含一个或多个 Web 服务器。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-p106">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="c6b4c-131">管理网站</span><span class="sxs-lookup"><span data-stu-id="c6b4c-131">Administration site</span></span>

<span data-ttu-id="c6b4c-p107">管理网站包含多个应用程序服务器，它们使用 Web 应用程序管理中心站点与应用程序池（此示例中为应用程序池 1）进行通信。管理中心网站提供对组织内的网站集的访问权限。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-p107">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="c6b4c-134">管理网站还包含 SQL 数据库服务器，这是安装了 SQL Server 的数据库服务器，且配置为支持 SQL 群集、镜像或 AlwaysOn（AlwaysOn 仅适用于 SQL Server 2012）。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-134">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="c6b4c-135">服务</span><span class="sxs-lookup"><span data-stu-id="c6b4c-135">Services</span></span>

<span data-ttu-id="c6b4c-p108">此设计示例显示了 Internet 信息服务 (IIS) 网站、SharePoint Web 服务。SharePoint Web 服务包含具有三项服务（User Profile、Search 和 Managed Metadata）的应用程序池（应用程序池 2）。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-p108">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="c6b4c-138">Internet 站点的服务说明：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-138">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="c6b4c-139">Managed Metadata — 请务必选择“此服务应用程序是列特定的术语集的默认存储位置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-139">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="c6b4c-140">App Management — 在 Azure 中面向公众的 Internet 站点中，不建议使用应用程序。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-140">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="c6b4c-141">应用程序池和 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="c6b4c-141">Application pools and web applications</span></span>

<span data-ttu-id="c6b4c-142">Azure 中的默认组显示应用程序池 3，其中包含一个名为“Contoso Sites”的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-142">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites.</span></span> <span data-ttu-id="c6b4c-143">此基于路径的网站集位于https://internal:8000。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-143">This path-based site collection is located at https://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="c6b4c-144">网站集和网站</span><span class="sxs-lookup"><span data-stu-id="c6b4c-144">Site collections and sites</span></span>

<span data-ttu-id="c6b4c-145">应用程序池中的网站集包括：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-145">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="c6b4c-146">用于爬网的以主机命名的网站集1（示例位置https://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="c6b4c-146">Host-named site collection 1 for crawling (example location https://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="c6b4c-147">用于查询的以主机命名的网站集2（ https://www.contoso.com示例https://secure.contoso.com位置、https://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="c6b4c-147">Host-named site collection 2 for queries (sample locations https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="c6b4c-148">用于查询的以主机命名的网站集3（ https://assets.contoso.com示例https://secureassets.contoso.com位置、https://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="c6b4c-148">Host-named site collection 3 for queries (sample locations https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="c6b4c-149">内容数据库</span><span class="sxs-lookup"><span data-stu-id="c6b4c-149">Content databases</span></span>

<span data-ttu-id="c6b4c-150">该示例演示了两个内容数据库。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-150">The example shows two content databases.</span></span> <span data-ttu-id="c6b4c-151">一个用于用于爬网的网站集1（https://authoring.contoso.com:8000)。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-151">One is for the site collection 1 used for crawling (https://authoring.contoso.com:8000).</span></span> <span data-ttu-id="c6b4c-152">另一种是用于查询的两个网站集2和3（https://www.contoso.com、 https://secure.contoso.com https://www.contoso.com:8000、、或https://assets.contoso.com https://secureassets.contoso.com） https://assets.contoso.com:8000)。</span><span class="sxs-lookup"><span data-stu-id="c6b4c-152">The other is for the two site collections 2 and 3 used for queries (https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000, or https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="c6b4c-153">区域和 URL</span><span class="sxs-lookup"><span data-stu-id="c6b4c-153">Zones and URLs</span></span>

<span data-ttu-id="c6b4c-154">此示例显示具有不同用户帐户使用的相关负载平衡 URL 的三个区域。 </span><span class="sxs-lookup"><span data-stu-id="c6b4c-154">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="c6b4c-155">第一个区域和 URL 列表与网站集 1 相关，其中包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-155">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="c6b4c-156">用户-网站作者</span><span class="sxs-lookup"><span data-stu-id="c6b4c-156">Users - Site authors</span></span>
    
- <span data-ttu-id="c6b4c-157">区域-默认</span><span class="sxs-lookup"><span data-stu-id="c6b4c-157">Zone - Default</span></span>
    
- <span data-ttu-id="c6b4c-158">负载平衡的 URL-https://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="c6b4c-158">Load-balanced URL - https://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="c6b4c-p111">第二个区域和 URL 列表具有三个不同区域中三种不同类型的用户。它与网站集 2 相关，其中包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-p111">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="c6b4c-161">第一个区域：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-161">First zone:</span></span>
  
- <span data-ttu-id="c6b4c-162">用户-网站作者</span><span class="sxs-lookup"><span data-stu-id="c6b4c-162">Users - Site authors</span></span>
    
- <span data-ttu-id="c6b4c-163">区域-默认</span><span class="sxs-lookup"><span data-stu-id="c6b4c-163">Zone - Default</span></span>
    
- <span data-ttu-id="c6b4c-164">负载平衡的 URL-https://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="c6b4c-164">Load-balanced URL - https://www.contoso.com:8000</span></span>
    
<span data-ttu-id="c6b4c-165">第二个区域：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-165">Second zone:</span></span>
  
- <span data-ttu-id="c6b4c-166">用户-匿名客户</span><span class="sxs-lookup"><span data-stu-id="c6b4c-166">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="c6b4c-167">区域-Internet</span><span class="sxs-lookup"><span data-stu-id="c6b4c-167">Zone - Internet</span></span>
    
- <span data-ttu-id="c6b4c-168">负载平衡的 URL-https://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="c6b4c-168">Load-balanced URL - https://www.contoso.com</span></span>
    
<span data-ttu-id="c6b4c-169">第三个区域：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-169">Third zone:</span></span>
  
- <span data-ttu-id="c6b4c-170">用户身份验证客户</span><span class="sxs-lookup"><span data-stu-id="c6b4c-170">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="c6b4c-171">区域-Extranet</span><span class="sxs-lookup"><span data-stu-id="c6b4c-171">Zone - Extranet</span></span>
    
- <span data-ttu-id="c6b4c-172">负载平衡的 URL-https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="c6b4c-172">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="c6b4c-p112">第三个区域和 URL 列表具有三个不同区域中三种不同类型的用户。它与网站集 3 相关，其中包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-p112">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="c6b4c-175">第一个区域：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-175">First zone:</span></span>
  
- <span data-ttu-id="c6b4c-176">用户-网站作者</span><span class="sxs-lookup"><span data-stu-id="c6b4c-176">Users - Site authors</span></span>
    
- <span data-ttu-id="c6b4c-177">区域-Internet</span><span class="sxs-lookup"><span data-stu-id="c6b4c-177">Zone - Internet</span></span>
    
- <span data-ttu-id="c6b4c-178">负载平衡的 URL-https://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="c6b4c-178">Load-balanced URL - https://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="c6b4c-179">第二个区域：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-179">Second zone:</span></span>
  
- <span data-ttu-id="c6b4c-180">用户-匿名客户</span><span class="sxs-lookup"><span data-stu-id="c6b4c-180">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="c6b4c-181">区域-Internet</span><span class="sxs-lookup"><span data-stu-id="c6b4c-181">Zone - Internet</span></span>
    
- <span data-ttu-id="c6b4c-182">负载平衡的 URL-https://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="c6b4c-182">Load-balanced URL - https://assets.contoso.com</span></span>
    
<span data-ttu-id="c6b4c-183">第三个区域：</span><span class="sxs-lookup"><span data-stu-id="c6b4c-183">Third zone:</span></span>
  
- <span data-ttu-id="c6b4c-184">用户身份验证客户</span><span class="sxs-lookup"><span data-stu-id="c6b4c-184">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="c6b4c-185">区域-Extranet</span><span class="sxs-lookup"><span data-stu-id="c6b4c-185">Zone - Extranet</span></span>
    
- <span data-ttu-id="c6b4c-186">负载平衡的 URL-https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="c6b4c-186">Load-balanced URL - https://secureassets.contoso.com</span></span>
    

