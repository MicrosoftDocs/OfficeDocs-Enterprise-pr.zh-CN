---
title: Office 365 与本地环境的集成
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2019
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: 了解如何将 Office 365 与您的现有目录服务集成。
ms.openlocfilehash: 36bbda95e96223c465d5bf5a2ec93e5514a38a17
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747158"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Office 365 与本地环境的集成

*本文适用于 Office 365 企业版和 Microsoft 365 企业版。*

您可以将 Office 365 与您现有的目录服务以及 Exchange Server、Skype for Business Server 2015 或 SharePoint Server 的本地安装集成在一起。
  
 - 当您与目录服务集成时，您可以同步和管理这两个环境的用户帐户。 您还可以添加密码哈希同步或单一登录（SSO），以便用户可以使用其本地凭据登录到这两个环境。
 - 当您与本地服务器产品集成时，将创建混合环境。 当您将用户或信息迁移到 Office 365 时，混合环境可帮助您，也可以继续在本地使用某些用户或某些信息以及在云中使用一些信息。 有关混合环境的详细信息，请参阅[混合云概述](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview)。

您还可以使用 Azure Active Directory （Azure AD）顾问获取自定义安装指南（您必须登录到 Office 365）：

- [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync)
- [AD FS 部署顾问](https://aka.ms/adfsguidance)
- [Azure AD Premium 设置指南](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>准备工作

在集成 Office 365 和本地环境之前，还需要参加[网络规划和性能调整](network-planning-and-performance.md)。 您还需要了解可用的[标识模型](about-office-365-identity.md)。 

若要了解可用于管理 Office 365 用户和帐户的工具列表，请参阅[管理 office 365 帐户的位置](manage-office-365-accounts.md)。 
  
## <a name="integrate-office-365-with-directory-services"></a>将 Office 365 与目录服务集成
如果您在本地目录中有现有的用户帐户，则不需要在 Office 365 中重新创建所有这些帐户，并且在环境之间引入差异或错误的风险。 目录同步可帮助您在您的联机和本地环境中镜像这些帐户。 通过目录同步，用户不必记住每个环境的新信息，也不必创建或更新帐户两次。 您需要为[本地目录准备](prepare-for-directory-synchronization.md)目录同步，您可以手动执行此操作，也可以使用[IdFix 工具](install-and-run-idfix.md)（IdFix 工具仅适用于 Active DIRECTORY 域服务 [AD DS]）。 
  
![使用目录同步将本地和联机用户帐户信息保持同步](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
如果您希望用户能够使用他们的本地凭据登录到 Office 365，您还可以配置 SSO。 使用 SSO，Office 365 配置为信任本地环境以进行用户身份验证。
  
![使用单一登录，在本地和联机环境中都可以使用相同的帐户。](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
不同的用户帐户管理技术为用户提供了不同的体验，如下表所示。
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>具有或不具有密码哈希同步或传递身份验证的目录同步

用户使用其用户帐户（域 \ 用户名）登录到本地环境。 当他们转到 Office 365 时，他们必须使用其工作或学校帐户（user@domain.com）重新登录。 这两个环境中的用户名相同。 当您添加密码哈希同步或传递身份验证时，用户在这两种环境中都具有相同的密码，但在登录到 Office 365 时将不得不再次提供这些凭据。 使用密码哈希同步的目录同步是最常用的目录同步方案。

若要设置目录同步，请使用 Azure Active Directory Connect。 有关说明，请参阅[设置 Office 365 的目录同步](set-up-directory-synchronization.md)和[使用快速设置的 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698537)。

了解有关[准备将目录同步到 Office 365](prepare-for-directory-synchronization.md)并将[本地标识与 Azure Active directory 集成](https://go.microsoft.com/fwlink/?LinkId=518101)的详细信息。

### <a name="directory-synchronization-with-sso"></a>使用 SSO 同步目录

用户使用其用户帐户登录到本地环境。 当他们转到 Office 365 时，它们要么是自动登录，要么使用它们用于本地环境的相同凭据（域 \ 用户名）登录。

若要设置 SSO，您还可以使用 Azure AD Connect。 有关说明，请参阅[AZURE AD Connect 的自定义安装](https://go.microsoft.com/fwlink/p/?LinkID=698430)。

了解有关[Azure Active Directory 中的单一登录应用程序](https://go.microsoft.com/fwlink/p/?LinkId=698604)的详细信息。

## <a name="azure-ad-connect"></a>Azure AD Connect

Azure AD Connect 替代了较早版本的身份集成工具，如 DirSync 和 Azure AD 同步。有关详细信息，请参阅[什么是使用 Azure Active Directory 的混合身份？](https://go.microsoft.com/fwlink/p/?LinkId=527969)。 如果要从 Azure Active Directory 同步更新到 Azure AD Connect，请参阅[升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。 

另请参阅[在 Microsoft Azure 中部署 Office 365 目录同步](https://go.microsoft.com/fwlink/?LinkId=517887)。

## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版概述](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
