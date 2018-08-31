---
title: 了解 Office 365 标识和 Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: 了解如何在 Office 365 中管理用户标识。
ms.openlocfilehash: 0fb6e77aef4495b2284256c13cb21320e6292746
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914977"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>了解 Office 365 标识和 Azure Active Directory

Office 365 使用的基于云的用户标识和身份验证服务 Azure Active Directory (Azure AD) 来管理用户。选择您的内部部署组织和 Office 365 之间配置标识管理早期的决策，是一种云基础结构的基础。由于更改了此配置稍后可能会变得比较困难，仔细考虑选项以确定哪些适合于组织的需要。您可以从 Office 365 中设置和管理用户帐户; 中的两个主要的身份验证模型**云身份验证**和**联合身份验证**。
  
很重要仔细考虑哪这些身份验证和标识模型，用于启动和运行。考虑时间、 现有复杂性和成本实施和维护每个身份验证和标识选项。这些因素是不同的每个组织;您应了解您想要用于您的部署标识选项以帮助您选择的身份验证和标识模型的主要概念。
  
## <a name="cloud-authentication"></a>云身份验证

根据如果您具有或没有现有 Active Directory 环境内部部署，您可以通过多种方式来管理为与 Office 365 用户的身份验证和标识服务。
  
### <a name="cloud-only"></a>仅限云

仅使用云的模型，您可以管理您只在 Office 365 中的用户帐户。不在本地服务器所需;它是所有处理在云中的 Azure AD。创建和管理 Office 365 管理中心中的用户或使用 Windows PowerShell [PowerShell cmdlet](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell)和标识和身份验证处理完全在云中的 Azure AD。仅使用云的模型通常很好的选项如果： 
  
- 您有任何其他内部部署用户目录。
    
- 具有非常复杂的本地目录并且只是要避免工作与其集成。
    
- 您具有现有的内部部署目录，但您想要运行的试用版或 Office 365 试点。更高版本，您可以匹配到内部部署用户的云用户时即可连接到您的本地目录。
    
若要开始使用云身份，请参阅[设置为企业的 Office 365](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)。
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>与无缝单一登录的密码哈希同步

启用内部部署目录对象在 Azure AD 身份验证的最简单方法。使用密码哈希同步 (PHS)，您可以将您的本地 Active Directory 用户帐户对象与 Office 365 同步和管理用户内部部署。用户密码哈希同步从您的本地 Active Directory 到 Azure AD 以便用户具有相同密码内部部署和云中。当密码更改，或重置为本地时，新密码哈希同步到 Azure AD 以便用户可以始终使用相同的密码的云资源和本地资源。从不发送到 Azure AD 或存储在 Azure AD 以明文形式密码。Azure AD，如标识保护的某些高级功能需要的 PHS 无论哪些选择身份验证方法。与无缝单一登录，用户将自动登录到 Azure AD 他们在其企业设备并连接到企业网络。
  
了解有关[选择密码哈希同步](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)和[无缝单一登录](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)的详细信息。
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>传递身份验证与无缝单一登录

提供使用一个或多个本地服务器上运行的软件代理来验证直接与您的本地 Active Directory 用户的 Azure AD 身份验证服务的简单密码验证。使用传递身份验证 (PTA)，您可以与 Office 365 同步的本地 Active Directory 用户帐户对象和管理用户内部部署。允许用户登录到同时在本地和 Office 365 资源和应用程序使用其内部部署帐户和密码。此配置验证直接针对您的本地 Active Directory 用户的密码，而不发送到 Office 365 密码哈希值。立即强制在本地用户帐户的安全要求的公司状态，密码策略和登录时间会使用此身份验证方法。与无缝单一登录，用户将自动登录到 Azure AD 他们在其企业设备并连接到企业网络。
  
了解有关[选择传递身份验证](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)和[无缝单一登录](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)的详细信息。
  
## <a name="federated-authentication-options"></a>联合身份验证选项

如果您具有现有 Active Directory 环境内部部署，您可以通过使用联合身份验证来管理 Office 365 中的用户的身份验证和标识服务与您的目录集成 Office 365。
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>使用 Active Directory 联合身份验证服务 (AD FS) 联合的身份

身份验证要求更复杂的大型企业组织，主要用于本地目录对象与 Office 365 同步和用户帐户是本地托管。使用 AD FS 用户具有相同密码内部部署和云中和不必再次登录以使用 Office 365。此联合身份验证模型可以提供额外的身份验证要求，例如基于智能卡身份验证或第三方多因素身份验证，且通常时必需组织具有身份验证要求本身并非支持 Azure AD。
  
了解有关[选择 with AD FS 联合的身份](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)。
  
### <a name="third-party-authentication-and-identity-providers"></a>第三方身份验证和标识提供程序

内部部署目录对象可能同步到 Office 365 和云资源访问主要由第三方身份提供程序 (IdP)。如果您的组织使用第三方联合身份验证解决方案，您可以配置单一登录与该将解决方案 for Office 365，前提是第三方联合身份验证解决方案是否与 Azure AD 兼容。
  
了解有关[Azure AD 联盟兼容性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)的详细信息。
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>与 Office 365 配置标识和身份验证

将内部部署目录集成与 Office 365 和 Azure AD 已得到简化了[Azure AD 连接](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。Azure AD 连接是连接您的目录的最佳方式，并且是同步到云用户组织的 Microsoft 的建议。
  
您还可以使用 Azure AD 顾问： [Azure AD 连接顾问](https://aka.ms/aadconnectpwsync)、 [AD FS 部署顾问](https://aka.ms/adfsguidance)和[Azure AD Premium 安装指南](https://aka.ms/aadpguidance)。
  
## <a name="video-training"></a>视频培训

有关详细信息，请参阅视频课程[Office 365： 管理标识使用 Azure AD 连接](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)，进入您的 LinkedIn 学习。
