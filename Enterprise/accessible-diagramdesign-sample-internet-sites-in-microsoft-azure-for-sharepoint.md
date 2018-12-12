---
title: 可以访问关系图的设计样本在 SharePoint 2013 的 Microsoft Azure 中的 Internet 站点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 本文是名为“设计示例：Microsoft Azure for SharePoint 2013 中的 Internet 站点”的图的可访问文本版本。
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
ms.locfileid: "17502755"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="b0a1e-103">可访问的图 - 设计示例：Microsoft Azure for SharePoint 2013 中的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="b0a1e-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="b0a1e-104">**摘要：** 这篇文章是设计 sample 图的辅助功能的文本版本： 在 SharePoint 2013 的 Microsoft Azure 中的 Internet 站点。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="b0a1e-105">本设计示例用作 Azure 使用 SharePoint 2013 在面向 Internet 的网站的起始点。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="b0a1e-106">本宣传海报演示如何设计 SharePoint 2013 的以下方面：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="b0a1e-107">用户</span><span class="sxs-lookup"><span data-stu-id="b0a1e-107">Users</span></span>
    
- <span data-ttu-id="b0a1e-108">区域和身份验证</span><span class="sxs-lookup"><span data-stu-id="b0a1e-108">Zones and authentication</span></span>
    
- <span data-ttu-id="b0a1e-109">服务器场</span><span class="sxs-lookup"><span data-stu-id="b0a1e-109">Server farm</span></span>
    
- <span data-ttu-id="b0a1e-110">管理网站</span><span class="sxs-lookup"><span data-stu-id="b0a1e-110">Administration site</span></span>
    
- <span data-ttu-id="b0a1e-111">服务</span><span class="sxs-lookup"><span data-stu-id="b0a1e-111">Services</span></span>
    
- <span data-ttu-id="b0a1e-112">应用程序池和 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="b0a1e-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="b0a1e-113">网站集</span><span class="sxs-lookup"><span data-stu-id="b0a1e-113">Site collections</span></span>
    
- <span data-ttu-id="b0a1e-114">网站</span><span class="sxs-lookup"><span data-stu-id="b0a1e-114">Sites</span></span>
    
- <span data-ttu-id="b0a1e-115">内容数据库</span><span class="sxs-lookup"><span data-stu-id="b0a1e-115">Content databases</span></span>
    
- <span data-ttu-id="b0a1e-116">区域和 URL</span><span class="sxs-lookup"><span data-stu-id="b0a1e-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="b0a1e-117">用户、区域和身份验证</span><span class="sxs-lookup"><span data-stu-id="b0a1e-117">Users, zones and authentication</span></span>

<span data-ttu-id="b0a1e-p101">此设计中有四种类型的用户帐户。每种帐户类型与一个用于访问的站点和使用特定身份验证类型的区域相关联。 </span><span class="sxs-lookup"><span data-stu-id="b0a1e-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="b0a1e-120">匿名的客户 — — 匿名客户通过网站如 http://www.contoso.com 具有访问权限。他们使用的区域是"Internet 区域 / 匿名"，它使用匿名身份验证。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com. The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="b0a1e-121">经过身份验证的客户 — — 已验证身份的客户通过网站如 https://secure.contoso.com 具有访问权限。他们使用的区域是"外联网区域 / SAML"，它使用 Azure Active Directory 使用 SAML 验证。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-121">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com. The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="b0a1e-p102">网站作者和开发人员 — — 通过网站 http://authoring.contoso.com:8000 或 http://www.contoso.com:8000 等网站作者和开发人员可以访问。他们使用的区域是"默认区域 / Windows 集成"，它使用 Active Directory 域服务 (AD DS)。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-p102">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="b0a1e-p103">搜索爬网帐户 — — 这种搜索爬网帐户能够通过 http://authoring.contoso.com:8000 或 http://www.contoso.com:8000 等网站访问。它使用的区域是"默认区域 / Windows 集成"，它与 Windows NTLM 身份验证使用 AD DS。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-p103">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="b0a1e-126">服务器场</span><span class="sxs-lookup"><span data-stu-id="b0a1e-126">Server farm</span></span>

<span data-ttu-id="b0a1e-p104">用户通过 Azure 访问服务器场。服务器场中包含一个或多个 Web 服务器。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-p104">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="b0a1e-129">管理网站</span><span class="sxs-lookup"><span data-stu-id="b0a1e-129">Administration site</span></span>

<span data-ttu-id="b0a1e-p105">管理网站包含多个应用程序服务器，它们使用 Web 应用程序管理中心站点与应用程序池（此示例中为应用程序池 1）进行通信。管理中心网站提供对组织内的网站集的访问权限。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-p105">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="b0a1e-132">管理网站还包含 SQL 数据库服务器，这是安装了 SQL Server 的数据库服务器，且配置为支持 SQL 群集、镜像或 AlwaysOn（AlwaysOn 仅适用于 SQL Server 2012）。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-132">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="b0a1e-133">服务</span><span class="sxs-lookup"><span data-stu-id="b0a1e-133">Services</span></span>

<span data-ttu-id="b0a1e-p106">此设计示例显示了 Internet 信息服务 (IIS) 网站、SharePoint Web 服务。SharePoint Web 服务包含具有三项服务（User Profile、Search 和 Managed Metadata）的应用程序池（应用程序池 2）。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-p106">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="b0a1e-136">Internet 站点的服务说明：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-136">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="b0a1e-137">托管元数据 — — 一定要选择**此服务应用程序已列的特定术语集的默认存储位置**。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-137">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="b0a1e-138">App Management — 在 Azure 中面向公众的 Internet 站点中，不建议使用应用程序。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-138">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="b0a1e-139">应用程序池和 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="b0a1e-139">Application pools and web applications</span></span>

<span data-ttu-id="b0a1e-p107">Azure 中的默认组显示应用程序池 3，其中包含一个名为“Contoso Sites”的 Web 应用程序。此基于路径的网站集位于 http://internal:8000。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-p107">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites. This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="b0a1e-142">网站集和网站</span><span class="sxs-lookup"><span data-stu-id="b0a1e-142">Site collections and sites</span></span>

<span data-ttu-id="b0a1e-143">应用程序池中的网站集包括：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-143">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="b0a1e-144">用于爬网的主机命名的网站集 1（示例位置 http://authoring.contoso.com:8000）</span><span class="sxs-lookup"><span data-stu-id="b0a1e-144">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="b0a1e-145">用于查询的主机命名的网站集 2（示例位置 http://www.contoso.com、https://secure.contoso.com、http://www.contoso.com:8000）</span><span class="sxs-lookup"><span data-stu-id="b0a1e-145">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="b0a1e-146">用于查询的主机命名的网站集 3（示例位置 http://assets.contoso.com、https://secureassets.contoso.com、http://assets.contoso.com:8000）</span><span class="sxs-lookup"><span data-stu-id="b0a1e-146">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="b0a1e-147">内容数据库</span><span class="sxs-lookup"><span data-stu-id="b0a1e-147">Content databases</span></span>

<span data-ttu-id="b0a1e-p108">该示例演示了两个内容数据库。一个是用于爬网的网站集 1 (http://authoring.contoso.com:8000)。另一个是用于查询的两个网站集 2 和 3（http://www.contoso.com、https://secure.contoso.com、http://www.contoso.com:8000 或 http://assets.contoso.com、https://secureassets.contoso.com、http://assets.contoso.com:8000）。</span><span class="sxs-lookup"><span data-stu-id="b0a1e-p108">The example shows two content databases. One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000). The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="b0a1e-151">区域和 URL</span><span class="sxs-lookup"><span data-stu-id="b0a1e-151">Zones and URLs</span></span>

<span data-ttu-id="b0a1e-152">此示例显示具有不同用户帐户使用的相关负载平衡 URL 的三个区域。 </span><span class="sxs-lookup"><span data-stu-id="b0a1e-152">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="b0a1e-153">第一个区域和 URL 列表与网站集 1 相关，其中包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-153">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="b0a1e-154">用户的站点作者</span><span class="sxs-lookup"><span data-stu-id="b0a1e-154">Users - Site authors</span></span>
    
- <span data-ttu-id="b0a1e-155">区域的默认值</span><span class="sxs-lookup"><span data-stu-id="b0a1e-155">Zone - Default</span></span>
    
- <span data-ttu-id="b0a1e-156">负载平衡 URL-http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="b0a1e-156">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="b0a1e-p109">第二个区域和 URL 列表具有三个不同区域中三种不同类型的用户。它与网站集 2 相关，其中包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-p109">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="b0a1e-159">第一个区域：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-159">First zone:</span></span>
  
- <span data-ttu-id="b0a1e-160">用户的站点作者</span><span class="sxs-lookup"><span data-stu-id="b0a1e-160">Users - Site authors</span></span>
    
- <span data-ttu-id="b0a1e-161">区域的默认值</span><span class="sxs-lookup"><span data-stu-id="b0a1e-161">Zone - Default</span></span>
    
- <span data-ttu-id="b0a1e-162">负载平衡 URL-http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="b0a1e-162">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="b0a1e-163">第二个区域：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-163">Second zone:</span></span>
  
- <span data-ttu-id="b0a1e-164">用户的匿名客户</span><span class="sxs-lookup"><span data-stu-id="b0a1e-164">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="b0a1e-165">区域-互联网</span><span class="sxs-lookup"><span data-stu-id="b0a1e-165">Zone - Internet</span></span>
    
- <span data-ttu-id="b0a1e-166">负载平衡的 URL-http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b0a1e-166">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="b0a1e-167">第三个区域：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-167">Third zone:</span></span>
  
- <span data-ttu-id="b0a1e-168">用户经过身份验证的客户</span><span class="sxs-lookup"><span data-stu-id="b0a1e-168">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="b0a1e-169">区域的外部网</span><span class="sxs-lookup"><span data-stu-id="b0a1e-169">Zone - Extranet</span></span>
    
- <span data-ttu-id="b0a1e-170">负载平衡的 URL-https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b0a1e-170">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="b0a1e-p110">第三个区域和 URL 列表具有三个不同区域中三种不同类型的用户。它与网站集 3 相关，其中包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-p110">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="b0a1e-173">第一个区域：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-173">First zone:</span></span>
  
- <span data-ttu-id="b0a1e-174">用户的站点作者</span><span class="sxs-lookup"><span data-stu-id="b0a1e-174">Users - Site authors</span></span>
    
- <span data-ttu-id="b0a1e-175">区域-互联网</span><span class="sxs-lookup"><span data-stu-id="b0a1e-175">Zone - Internet</span></span>
    
- <span data-ttu-id="b0a1e-176">负载平衡 URL-http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="b0a1e-176">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="b0a1e-177">第二个区域：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-177">Second zone:</span></span>
  
- <span data-ttu-id="b0a1e-178">用户的匿名客户</span><span class="sxs-lookup"><span data-stu-id="b0a1e-178">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="b0a1e-179">区域-互联网</span><span class="sxs-lookup"><span data-stu-id="b0a1e-179">Zone - Internet</span></span>
    
- <span data-ttu-id="b0a1e-180">负载平衡的 URL-http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b0a1e-180">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="b0a1e-181">第三个区域：</span><span class="sxs-lookup"><span data-stu-id="b0a1e-181">Third zone:</span></span>
  
- <span data-ttu-id="b0a1e-182">用户经过身份验证的客户</span><span class="sxs-lookup"><span data-stu-id="b0a1e-182">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="b0a1e-183">区域的外部网</span><span class="sxs-lookup"><span data-stu-id="b0a1e-183">Zone - Extranet</span></span>
    
- <span data-ttu-id="b0a1e-184">负载平衡的 URL-http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="b0a1e-184">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

