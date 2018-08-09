---
title: 集成的应用程序和 Office 365 管理员的 Azure AD
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 3/5/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: 了解如何 O365 集成的应用程序注册，并在 Azure AD 中管理
ms.openlocfilehash: 666bfca5c2621d25f13dff7c5753c5ef47591b68
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "22213104"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>集成的应用程序和 Office 365 管理员的 Azure AD

还有其他管理集成应用于刚[打开集成应用程序打开或关闭](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)的程序。随着的 Office 365 REST Api，用户可以授予应用程序访问其 Office 365 数据，如邮件、 日历、 联系人、 用户、 组、 文件和文件夹。默认情况下，用户需要单独授予对每个应用程序的权限，但这不会扩展如果您想要授权一次在全局管理员级别应用程序和应用程序启动器通过整个组织推出它。若要执行此操作，您必须在 Azure AD 中注册应用程序。有一些您需要在 Azure AD 中注册应用程序，您应了解的一些背景信息可帮助您管理 Office 365 组织中的应用程序之前执行的步骤。本文旨在帮助您访问这些资源。
  
## <a name="azure-ad-resources-for-office-365-admins"></a>对于 Office 365 管理员的 azure AD 资源

您必须执行这两个过程，您可以在 Azure AD 中管理 Office 365 应用程序之前。
  
|**先决条件**|**注释**|
|:-----|:-----|
|[注册免费的 Azure Active Directory 订阅](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |每个付费的 Office 365 订阅到 Azure Active Directory 附带免费订阅。您可以使用 Azure AD 管理您的应用程序和创建和管理用户和组帐户。若要激活此订阅并访问 Azure 管理门户，您必须完成一次性注册过程。然后，您可以转到 Azure AD 从 Office 365 管理中心。  <br/> |
|[打开或关闭集成的应用程序](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |您必须启用集成的应用程序用户允许第三方应用程序访问其 Office 365 的信息和您在 Azure AD 中注册的应用程序。例如，当有人使用第三方应用程序，该应用程序可能会让权限访问其日历和 onedrive for Business 文件夹的文件进行编辑。  <br/> |
   
管理 Office 365 应用程序要求在 Azure AD 中具有的应用程序的知识。这些文章可帮助您所需的背景。
  
|**背景文章**|**注释**|
|:-----|:-----|
|[满足 Office 365 应用程序启动器](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |如果您熟悉应用程序启动程序，您可能想知道它是什么以及如何使用它。应用程序启动器旨在帮助您从任意位置向应用程序获取 Office 365 中。  <br/> |
|[添加、 更新和删除应用程序](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |本主题演示如何添加、 更新或在 Azure Active Directory 中删除应用程序。您将了解有关可与 Azure AD 集成的应用程序的不同类型以及如何配置您的应用程序以访问其他资源，如 web Api，等等。  <br/> |
|[具有显示在 Office 365 应用程序启动器应用程序](https://go.microsoft.com/fwlink/?LinkId=617138)。  <br/> |使用户更轻松地查找和访问其应用程序的 Office 365 中的应用程序启动器。本文介绍您作为开发人员可以获取应用程序以显示在用户的应用程序启动器和还为其提供使用其 Office 365 凭据的单一登录 (SSO) 体验的方式。  <br/> |
|[Office 365 Api 平台概述](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Office 365 Api 可让您提供对客户的 Office 365 数据，包括最关注的内容的访问 — 其邮件、 日历、 联系人、 用户和组、 文件和文件夹。本文说明了 Office 365 应用程序，Azure AD 之间的关系中没有很好的关系图和应用程序访问的数据。  <br/> |
|[将在 Azure Active Directory 中的应用程序集成](https://go.microsoft.com/fwlink/?LinkId=617141) <br/> | 了解如何注册您的应用程序、 了解概念注册的应用程序，并了解有关的品牌准则多租户应用程序与 Azure Active Directory 集成的应用程序。  <br/> |
|[Azure Active Directory 集成教程](https://go.microsoft.com/fwlink/?LinkId=617144) <br/> |这些教程的目标是用于向您表明如何配置第三方 saas 与应用程序的 Azure AD SSO。  <br/> |
|[Azure AD 身份验证方案](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD 简化面向开发人员的身份验证，从而作为服务，标识提供支持的行业标准协议，如 OAuth 2.0 和 OpenID 连接，以及打开源库的不同的平台，可帮助您快速开始编码。本文档有助于您了解各种方案 Azure AD 支持，演示如何入门。  <br/> |
|[应用程序访问](https://go.microsoft.com/fwlink/?LinkId=617146) <br/> |Azure AD 将启用许多今天的流行软件作为服务 (SaaS) 应用程序; 的轻松集成它提供了标识和访问管理，它提供了用户访问面板，其中他们能够发现他们有哪些应用程序访问，且这些用户可以使用 SSO 访问其应用程序。本文为您提供了使您能够了解有关 Azure AD 应用程序 access 增强功能以及如何可以参与与它们相关资源的链接。  <br/> |
|[添加或删除 Office 365 应用程序启动程序的图块数为单位](https://support.office.com/article/0b71362d-ce56-4d21-9b2f-bdb750a82b81) <br/> |您可以快速访问每天使用通过添加或删除在 Office 365 应用程序启动器应用程序的应用程序。  <br/> |
   

