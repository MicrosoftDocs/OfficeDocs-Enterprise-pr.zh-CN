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
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>可访问的图 - 设计示例：Microsoft Azure for SharePoint 2013 中的 Internet 站点

**摘要：** 这篇文章是设计 sample 图的辅助功能的文本版本： 在 SharePoint 2013 的 Microsoft Azure 中的 Internet 站点。
  
本设计示例用作 Azure 使用 SharePoint 2013 在面向 Internet 的网站的起始点。
  
本宣传海报演示如何设计 SharePoint 2013 的以下方面：
  
- 用户
    
- 区域和身份验证
    
- 服务器场
    
- 管理网站
    
- 服务
    
- 应用程序池和 Web 应用程序
    
- 网站集
    
- 网站
    
- 内容数据库
    
- 区域和 URL
    
## <a name="users-zones-and-authentication"></a>用户、区域和身份验证

此设计中有四种类型的用户帐户。每种帐户类型与一个用于访问的站点和使用特定身份验证类型的区域相关联。  
  
- 匿名的客户 — — 匿名客户通过网站如 http://www.contoso.com 具有访问权限。他们使用的区域是"Internet 区域 / 匿名"，它使用匿名身份验证。
    
- 经过身份验证的客户 — — 已验证身份的客户通过网站如 https://secure.contoso.com 具有访问权限。他们使用的区域是"外联网区域 / SAML"，它使用 Azure Active Directory 使用 SAML 验证。
    
- 网站作者和开发人员 — — 通过网站 http://authoring.contoso.com:8000 或 http://www.contoso.com:8000 等网站作者和开发人员可以访问。他们使用的区域是"默认区域 / Windows 集成"，它使用 Active Directory 域服务 (AD DS)。
    
- 搜索爬网帐户 — — 这种搜索爬网帐户能够通过 http://authoring.contoso.com:8000 或 http://www.contoso.com:8000 等网站访问。它使用的区域是"默认区域 / Windows 集成"，它与 Windows NTLM 身份验证使用 AD DS。
    
## <a name="server-farm"></a>服务器场

用户通过 Azure 访问服务器场。服务器场中包含一个或多个 Web 服务器。
  
## <a name="administration-site"></a>管理网站

管理网站包含多个应用程序服务器，它们使用 Web 应用程序管理中心站点与应用程序池（此示例中为应用程序池 1）进行通信。管理中心网站提供对组织内的网站集的访问权限。
  
管理网站还包含 SQL 数据库服务器，这是安装了 SQL Server 的数据库服务器，且配置为支持 SQL 群集、镜像或 AlwaysOn（AlwaysOn 仅适用于 SQL Server 2012）。
  
## <a name="services"></a>服务

此设计示例显示了 Internet 信息服务 (IIS) 网站、SharePoint Web 服务。SharePoint Web 服务包含具有三项服务（User Profile、Search 和 Managed Metadata）的应用程序池（应用程序池 2）。
  
Internet 站点的服务说明：
  
> 托管元数据 — — 一定要选择**此服务应用程序已列的特定术语集的默认存储位置**。
    
> App Management — 在 Azure 中面向公众的 Internet 站点中，不建议使用应用程序。
    
## <a name="application-pools-and-web-applications"></a>应用程序池和 Web 应用程序

Azure 中的默认组显示应用程序池 3，其中包含一个名为“Contoso Sites”的 Web 应用程序。此基于路径的网站集位于 http://internal:8000。
  
## <a name="site-collections-and-sites"></a>网站集和网站

应用程序池中的网站集包括：
  
- 用于爬网的主机命名的网站集 1（示例位置 http://authoring.contoso.com:8000）
    
- 用于查询的主机命名的网站集 2（示例位置 http://www.contoso.com、https://secure.contoso.com、http://www.contoso.com:8000）
    
- 用于查询的主机命名的网站集 3（示例位置 http://assets.contoso.com、https://secureassets.contoso.com、http://assets.contoso.com:8000）
    
## <a name="content-databases"></a>内容数据库

该示例演示了两个内容数据库。一个是用于爬网的网站集 1 (http://authoring.contoso.com:8000)。另一个是用于查询的两个网站集 2 和 3（http://www.contoso.com、https://secure.contoso.com、http://www.contoso.com:8000 或 http://assets.contoso.com、https://secureassets.contoso.com、http://assets.contoso.com:8000）。
  
## <a name="zones-and-urls"></a>区域和 URL

此示例显示具有不同用户帐户使用的相关负载平衡 URL 的三个区域。  
  
第一个区域和 URL 列表与网站集 1 相关，其中包含以下信息：
  
- 用户的站点作者
    
- 区域的默认值
    
- 负载平衡 URL-http://authoring.contoso.com:8000
    
第二个区域和 URL 列表具有三个不同区域中三种不同类型的用户。它与网站集 2 相关，其中包含以下信息：
  
第一个区域：
  
- 用户的站点作者
    
- 区域的默认值
    
- 负载平衡 URL-http://www.contoso.com:8000
    
第二个区域：
  
- 用户的匿名客户
    
- 区域-互联网
    
- 负载平衡的 URL-http://www.contoso.com
    
第三个区域：
  
- 用户经过身份验证的客户
    
- 区域的外部网
    
- 负载平衡的 URL-https://secure.contoso.com
    
第三个区域和 URL 列表具有三个不同区域中三种不同类型的用户。它与网站集 3 相关，其中包含以下信息：
  
第一个区域：
  
- 用户的站点作者
    
- 区域-互联网
    
- 负载平衡 URL-http://assets.contoso.com:8000
    
第二个区域：
  
- 用户的匿名客户
    
- 区域-互联网
    
- 负载平衡的 URL-http://assets.contoso.com
    
第三个区域：
  
- 用户经过身份验证的客户
    
- 区域的外部网
    
- 负载平衡的 URL-http://secureassets.contoso.com
    

