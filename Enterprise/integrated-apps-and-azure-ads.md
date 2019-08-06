---
title: 适用于 Office 365 管理员的集成应用和 Azure AD
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: 了解如何在 Azure AD 中注册和管理 O365 集成应用程序
ms.openlocfilehash: c52b4beefaefd4a115c132c6f82e7f1d20564b46
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782522"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>适用于 Office 365 管理员的集成应用和 Azure AD

除了仅[打开或关闭集成应用](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)之外, 还可以管理集成的应用程序。 随着 Office 365 REST Api 的出现, 用户可以授予应用对其 Office 365 数据 (如邮件、日历、联系人、用户、组、文件和文件夹) 的访问权限。 默认情况下, 用户需要单独向每个应用程序授予权限, 但如果要在全局管理员级别对应用程序进行授权, 并通过应用启动器将其部署到整个组织, 则不能很好地进行扩展。 若要执行此操作, 必须在 Azure AD 中注册应用程序。 在 Azure AD 中注册应用程序之前需要执行一些步骤, 以及您应该知道哪些可帮助您在 Office 365 组织中管理应用程序的背景信息。 本文将向您指出这些资源。
  
## <a name="azure-ad-resources-for-office-365-admins"></a>适用于 Office 365 管理员的 Azure AD 资源

您必须先执行以下两个步骤, 然后才能在 Azure AD 中管理 Office 365 应用程序。
  
|**先决条件**|**Comments**|
|:-----|:-----|
|[注册免费的 Azure Active Directory 订阅](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |每个付费的 Office 365 订阅都附带了 Azure Active Directory 的免费订阅。 您可以使用 Azure AD 管理您的应用程序, 并创建和管理用户和组帐户。 若要激活此订阅并访问 Azure 管理门户, 您必须完成一次性注册过程。 之后, 你可以从 Microsoft 365 管理中心转到 Azure AD。  <br/> |
|[打开或关闭集成应用](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |您必须为您的用户启用集成应用程序, 以允许第三方应用访问其 Office 365 信息, 并让您在 Azure AD 中注册应用程序。 例如, 当某人使用第三方应用程序时, 该应用可能会请求权限来访问其日历, 并编辑 OneDrive for business 文件夹中的文件。  <br/> |
   
管理 Office 365 应用程序需要你了解 Azure AD 中的应用程序。 这些文章可帮助你为你提供所需的背景。
  
|**背景文章**|**Comments**|
|:-----|:-----|
|[满足 Office 365 应用启动器](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |如果你不熟悉应用启动器, 你可能会想知道它是什么以及如何使用它。 应用启动器旨在帮助你从 Office 365 中的任何位置访问你的应用程序。  <br/> |
|[添加、更新和删除应用程序](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |本主题介绍如何在 Azure Active Directory 中添加、更新或删除应用程序。 您将了解可以与 Azure AD 集成的不同类型的应用程序, 以及如何配置您的应用程序以访问其他资源, 如 web Api 等。  <br/> |
|将[您的应用程序显示在 Office 365 应用启动器中](https://go.microsoft.com/fwlink/?LinkId=617138)。  <br/> |Office 365 中的应用启动器, 使用户可以更轻松地查找和访问其应用程序。 本文介绍了您作为开发人员可以在用户的应用程序启动器中显示您的应用程序的方法, 同时还为他们提供使用 Office 365 凭据的单一登录 (SSO) 体验。  <br/> |
|[Office 365 API 平台概述](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |通过 Office 365 Api, 您可以提供对客户的 Office 365 数据的访问, 其中包括他们最关注的内容, 包括他们的邮件、日历、联系人、用户和组、文件和文件夹。 本文中有一个很棒的关系图, 说明了 Office 365 应用程序、Azure AD 和应用访问的数据之间的关系。  <br/> |
|[在 Azure Active Directory 中集成应用程序](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | 了解与 Azure Active Directory 集成的应用程序, 以及如何注册您的应用程序, 了解已注册应用程序背后的概念, 并了解多租户应用程序的品牌打造指南。  <br/> |
|[Azure Active Directory 集成教程](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |这些教程的目标是向您介绍如何为第三方 SaaS 应用程序配置 Azure AD SSO。  <br/> |
|[Azure AD 的身份验证场景](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD 通过提供标识作为一项服务来简化对开发人员的身份验证, 并支持对行业标准协议 (如 OAuth 2.0 和 OpenID Connect) 以及针对不同平台的开放源库, 以帮助您快速开始编码。 本文档可帮助您了解 Azure AD 支持的各种方案, 并说明如何开始。  <br/> |
|[应用程序访问](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD 能够轻松地与当今流行的许多软件作为服务 (SaaS) 应用程序集成;它提供了标识和访问管理, 并为用户提供了一个访问面板, 用户可在其中发现他们拥有的应用程序访问权限以及它们可以使用 SSO 访问其应用程序的位置。 本文为您提供了相关资源的链接, 这些资源使您能够详细了解 Azure AD 的应用程序访问增强功能, 以及如何参与这些增强。  <br/> |
|[个性化设置 Office 365 体验](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |您可以通过在 Office 365 应用启动器中添加或删除应用程序, 快速访问您每天使用的应用程序。  <br/> |
   

