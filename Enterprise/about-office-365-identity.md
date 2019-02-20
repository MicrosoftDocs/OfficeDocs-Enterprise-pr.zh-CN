---
title: 了解 Office 365 标识和 Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: 了解如何在 Office 365 中管理用户标识。
ms.openlocfilehash: 0b0dd133979a5f94f7f8322c532c61fd24719359
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085421"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>了解 Office 365 标识和 Azure Active Directory

Office 365 使用基于云的用户标识和身份验证服务 azure Active Directory (azure AD) 管理用户。选择是否在内部部署组织和 Office 365 之间配置标识管理是早期决定, 这是云基础结构的基础知识之一。由于稍后更改此配置可能很困难, 因此请仔细考虑这些选项以确定最适合您的组织需求的功能。您可以从 Office 365 中的两个主要身份验证模型中进行选择, 以设置和管理用户帐户;**云身份验证**和**联合身份验证**。
  
务必仔细考虑使用哪些身份验证和标识模型来启动和运行。考虑实施和维护每个身份验证和标识选项的时间、现有复杂性和成本。这些因素对于每个组织都是不同的;您应了解标识选项的关键概念, 以帮助您选择要用于部署的身份验证和标识模型。
  
## <a name="cloud-authentication"></a>云身份验证

根据您在本地有或没有现有 Active Directory 环境的情况, 您可以使用多个选项来管理使用 Office 365 的用户的身份验证和标识服务。
  
### <a name="cloud-only"></a>仅限云

使用仅限云的模型, 可以在 Office 365 中管理用户帐户。不需要本地服务器;Azure AD 将全部在云中进行处理。您可以在 Office 365 管理中心中创建和管理用户, 也可以使用 Windows powershell [cmdlet](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell)和标识和身份验证在云中由 Azure AD 完全处理。通常情况下, 仅云模型是一个好的选择: 
  
- 您没有其他本地用户目录。
    
- 您有一个非常复杂的本地目录, 只是想避免工作与它集成。
    
- 您有一个现有的本地目录, 但您想要运行 Office 365 的试用版或试验版。稍后, 当您准备好连接到本地目录时, 您可以将云用户与本地用户进行匹配。
    
若要开始使用云标识, 请参阅[设置 Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)。
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>使用无缝单一登录的密码哈希同步

为 Azure AD 中的本地目录对象启用身份验证的最简单方法。使用密码哈希同步 (PHS), 您可以将内部部署 Active Directory 用户帐户对象与 Office 365 同步并在本地管理您的用户。用户密码的哈希将从本地 Active Directory 同步到 Azure AD, 以便用户在本地和在云中具有相同的密码。更改密码或在本地重置密码时, 新的密码哈希将同步到 Azure AD, 以便您的用户始终可以对云资源和本地资源使用相同的密码。从不以明文形式将密码发送到 azure ad 或以明文形式存储在 azure ad 中。Azure AD 的一些高级功能 (如标识保护) 需要 PHS, 而不管选择了哪种身份验证方法。通过无缝单一登录, 用户在其公司设备上并连接到公司网络时, 将自动登录到 Azure AD。
  
了解有关[选择 "密码哈希同步](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) [" 和 "无缝单一登录"](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)的详细信息。
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>带有无缝单一登录的传递身份验证

使用在一个或多个本地服务器上运行的软件代理为 Azure AD 身份验证服务提供简单的密码验证, 以直接使用本地 Active Directory 验证用户。通过传递身份验证 (PTA), 您可以将内部部署 Active Directory 用户帐户对象与 Office 365 同步并在本地管理您的用户。允许你的用户使用其内部部署帐户和密码登录到本地和 Office 365 资源和应用程序。此配置将直接对本地 Active Directory 验证用户密码, 而不会将密码哈希发送到 Office 365。具有安全要求的公司立即强制实施本地用户帐户状态、密码策略和登录时间将使用此身份验证方法。通过无缝单一登录, 用户在其公司设备上并连接到公司网络时, 将自动登录到 Azure AD。
  
了解有关[选择传递身份验证](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)和[无缝单一登录](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)的详细信息。
  
## <a name="federated-authentication-options"></a>联合身份验证选项

如果您在本地有一个现有的 Active Directory 环境, 则可以使用联合身份验证来管理 office 365 中用户的身份验证和标识服务, 从而将 Office 365 集成到您的目录中。
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>使用 Active Directory 联合身份验证服务 (AD FS) 的联合身份

主要针对具有更复杂的身份验证要求的大型企业组织, 本地目录对象与 Office 365 同步, 并且用户帐户在本地进行管理。使用 AD FS 时, 用户在本地和在云中具有相同的密码, 且无需再次登录才能使用 Office 365。此联合身份验证模型可以提供其他身份验证要求, 例如基于智能卡的身份验证或第三方多重身份验证, 通常在组织具有身份验证要求时需要这些要求Azure AD 本身不受支持。
  
了解有关[选择与 AD FS 联合身份的](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)详细信息。
  
### <a name="third-party-authentication-and-identity-providers"></a>第三方身份验证和标识提供程序

内部部署目录对象可能会同步到 Office 365, 并且云资源访问主要由第三方标识提供程序 (IdP) 进行管理。如果您的组织使用第三方联合解决方案, 则可以使用适用于 Office 365 的解决方案配置登录, 前提是第三方联合解决方案与 Azure AD 兼容。
  
了解有关[Azure AD 联合身份验证兼容性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)的详细信息。
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>使用 Office 365 配置标识和身份验证

使用[azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)简化了你的本地目录与 Office 365 和 Azure ad 的集成。Azure AD connect 是连接目录的最佳方式, 并且是 Microsoft 对组织将其用户同步到云的建议。
  
您还可以使用 azure ad 顾问: [azure ad Connect advisor](https://aka.ms/aadconnectpwsync)、 [AD FS 部署顾问](https://aka.ms/adfsguidance)和[azure AD Premium 设置指南](https://aka.ms/aadpguidance)。
  
## <a name="video-training"></a>视频培训

有关详细信息, 请参阅视频课程[Office 365: 使用 Azure AD Connect 管理标识](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)(通过 LinkedIn 学习)。
