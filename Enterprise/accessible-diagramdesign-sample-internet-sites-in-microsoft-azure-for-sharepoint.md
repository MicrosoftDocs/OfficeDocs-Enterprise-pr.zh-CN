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
description: 本文是名为“设计示例：Microsoft Azure for SharePoint 2013 中的 Internet 站点”的图的可访问文本版本。
ms.openlocfilehash: 28cf28739c476638b5775d170508001f2a9730ed
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068793"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>可访问的图 - 设计示例：Microsoft Azure for SharePoint 2013 中的 Internet 站点

**摘要:** 本文是名为 "设计示例: Microsoft Azure for SharePoint 2013 中的 Internet 站点" 图表的可访问文本版本。
  
使用此设计示例作为 Azure 中使用 SharePoint 2013 的面向 Internet 的网站的起始点。
  
此海报显示了如何设计 SharePoint 2013 的以下方面的示例:
  
- 用户
    
- 区域和身份验证
    
- 服务器场
    
- 管理网站
    
- 服务
    
- 应用程序池和 Web 应用程序
    
- 网站集
    
- 站点
    
- 内容数据库
    
- 区域和 URL
    
## <a name="users-zones-and-authentication"></a>用户、区域和身份验证

此设计中有四种类型的用户帐户。每种帐户类型与一个用于访问的站点和使用特定身份验证类型的区域相关联。  
  
- 匿名客户—匿名客户可以通过网站访问, 如http://www.contoso.com。 它们使用的区域是 "Internet 区域/匿名", 它使用匿名身份验证。
    
- 经过身份验证的客户—经过身份验证的客户可以https://secure.contoso.com通过网站访问, 如。 它们所使用的区域是 "Extranet 区域/SAML", 它将 Azure Active Directory 与 SAML 身份验证结合使用。
    
- 网站作者和开发人员-网站作者和开发人员可以通过网站 ( http://authoring.contoso.com:8000如http://www.contoso.com:8000或) 访问网站。 它们使用的区域是使用 Active Directory 域服务 (AD DS) 的 "默认区域/Windows 集成"。
    
- 搜索爬网帐户-搜索爬网帐户可以通过网站 (如http://authoring.contoso.com:8000或http://www.contoso.com:8000) 访问。 它使用的区域是 "默认区域/Windows 集成", 它将 AD DS 与 Windows NTLM 身份验证结合使用。
    
## <a name="server-farm"></a>服务器场

用户通过 Azure 访问服务器场。服务器场中包含一个或多个 Web 服务器。
  
## <a name="administration-site"></a>管理网站

管理网站包含多个应用程序服务器，它们使用 Web 应用程序管理中心站点与应用程序池（此示例中为应用程序池 1）进行通信。管理中心网站提供对组织内的网站集的访问权限。
  
管理网站还包含 SQL 数据库服务器，这是安装了 SQL Server 的数据库服务器，且配置为支持 SQL 群集、镜像或 AlwaysOn（AlwaysOn 仅适用于 SQL Server 2012）。
  
## <a name="services"></a>服务

此设计示例显示了 Internet 信息服务 (IIS) 网站、SharePoint Web 服务。SharePoint Web 服务包含具有三项服务（User Profile、Search 和 Managed Metadata）的应用程序池（应用程序池 2）。
  
Internet 站点的服务说明：
  
> Managed Metadata — 请务必选择“此服务应用程序是列特定的术语集的默认存储位置”****。
    
> App Management — 在 Azure 中面向公众的 Internet 站点中，不建议使用应用程序。
    
## <a name="application-pools-and-web-applications"></a>应用程序池和 Web 应用程序

Azure 中的默认组显示应用程序池 3，其中包含一个名为“Contoso Sites”的 Web 应用程序。 此基于路径的网站集位于http://internal:8000。
  
## <a name="site-collections-and-sites"></a>网站集和网站

应用程序池中的网站集包括：
  
- 用于爬网的以主机命名的网站集 1 (示例位置http://authoring.contoso.com:8000)
    
- 用于查询的以主机命名的网站集 2 ( http://www.contoso.com示例https://secure.contoso.com位置、http://www.contoso.com:8000)
    
- 用于查询的以主机命名的网站集 3 ( http://assets.contoso.com示例https://secureassets.contoso.com位置、http://assets.contoso.com:8000)
    
## <a name="content-databases"></a>内容数据库

该示例演示了两个内容数据库。 一个用于用于爬网的网站集 1 (http://authoring.contoso.com:8000)。 另一种是用于查询的两个网站集2和 3 (http://www.contoso.com、 https://secure.contoso.com http://www.contoso.com:8000、、或http://assets.contoso.com https://secureassets.contoso.com) http://assets.contoso.com:8000)。
  
## <a name="zones-and-urls"></a>区域和 URL

此示例显示具有不同用户帐户使用的相关负载平衡 URL 的三个区域。  
  
第一个区域和 URL 列表与网站集 1 相关，其中包含以下信息：
  
- 用户-网站作者
    
- 区域-默认
    
- 负载平衡的 URL-http://authoring.contoso.com:8000
    
第二个区域和 URL 列表具有三个不同区域中三种不同类型的用户。它与网站集 2 相关，其中包含以下信息：
  
第一个区域：
  
- 用户-网站作者
    
- 区域-默认
    
- 负载平衡的 URL-http://www.contoso.com:8000
    
第二个区域：
  
- 用户-匿名客户
    
- 区域-Internet
    
- 负载平衡的 URL-http://www.contoso.com
    
第三个区域：
  
- 用户身份验证客户
    
- 区域-Extranet
    
- 负载平衡的 URL-https://secure.contoso.com
    
第三个区域和 URL 列表具有三个不同区域中三种不同类型的用户。它与网站集 3 相关，其中包含以下信息：
  
第一个区域：
  
- 用户-网站作者
    
- 区域-Internet
    
- 负载平衡的 URL-http://assets.contoso.com:8000
    
第二个区域：
  
- 用户-匿名客户
    
- 区域-Internet
    
- 负载平衡的 URL-http://assets.contoso.com
    
第三个区域：
  
- 用户身份验证客户
    
- 区域-Extranet
    
- 负载平衡的 URL-http://secureassets.contoso.com
    

