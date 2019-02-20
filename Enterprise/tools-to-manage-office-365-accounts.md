---
title: 用于管理 Office 365 帐户的工具
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: '了解用于管理 Office 365 用户的工具, 以及您可以使用的工具取决于管理用户身份的方式。 '
ms.openlocfilehash: e13b6a998aa6de433d85ef3be60f08703eb914d4
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085381"
---
# <a name="tools-to-manage-office-365-accounts"></a>用于管理 Office 365 帐户的工具

您可以通过几种不同的方式管理 Office 365 用户, 具体取决于您的配置。您可以在 Office 365 管理中心、Windows PowerShell、本地目录或 Azure Active directory 管理门户中管理用户。 

在购买 Office 365 后, 可以立即使用管理中心和 Windows PowerShell 来管理帐户。管理云标识组织中的每个人都有单独的用户 ID 和密码 (适用于 Office 365)。如果要与您的本地基础结构集成, 并让用户帐户与 Office 365 同步, 可以使用 Azure Active Directory Connect 来提供标识同步, 或者提供密码同步 (可选), 或完全单一登录功能。
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>规划将管理用户帐户的位置和方式

如何管理用户帐户的位置和方式取决于您要用于 Office 365 的标识模型。这两个整体模型是云身份验证和联合身份验证。
  
### <a name="cloud-authentication"></a>云身份验证

- [Office 365 Identity](about-office-365-identity.md) -在 Office 365 管理中心中创建和管理用户, 您还可以使用 Windows PowerShell 或 Azure Active Directory 管理您的用户。
- [带有无缝单一登录的密码哈希同步](about-office-365-identity.md)-为 Azure AD 中的本地目录对象启用身份验证的最简单方法。使用密码哈希同步 (PHS), 您可以将内部部署 Active Directory 用户帐户对象与 Office 365 同步并在本地管理您的用户。 
- [带有无缝单一登录的传递身份验证](about-office-365-identity.md)-使用在一个或多个本地服务器上运行的软件代理, 为 Azure AD 身份验证服务提供简单的密码验证, 以直接通过您的用户身份验证用户内部部署 Active Directory。 
    
### <a name="federated-authentication"></a>联合身份验证

- [Office 365 标识](about-office-365-identity.md)-主要针对具有更复杂的身份验证要求的大型企业组织, 本地目录对象与 Office 365 同步, 并且用户帐户在本地进行管理。 
- [第三方身份验证和标识提供程序](about-office-365-identity.md)-内部部署目录对象可能会同步到 Office 365, 并且云资源访问主要由第三方标识提供程序 (IdP) 进行管理。 
    
## <a name="managing-accounts"></a>管理帐户

在决定您的组织创建和管理帐户的方式时, 请考虑以下事项:
  
- 目录同步软件需要安装在本地环境中的服务器上, 以连接 Office 365 和本地目录之间的标识。
- 任何目录同步选项 (包括 SSO 选项) 都需要您的本地目录属性满足标准。在目录中使用哪些属性以及需要清除的内容 (如果有) 的具体说明,[准备通过目录同步将用户预配到 Office 365](prepare-for-directory-synchronization.md)。有关如何使用 IdFix 自动执行目录清理的说明, 请参阅[安装和运行 Office 365 IdFix 工具](install-and-run-idfix.md)。 
    
## <a name="plan-how-you-are-going-to-create-office-365-accounts"></a>规划如何创建 Office 365 帐户
下表列出了不同的帐户管理工具:
    
|**选项**|**备注**|
|:-----|:-----|
|**Office 365 admin center** | - [将用户逐个或批量添加到 Office 365-管理员帮助](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> -提供一个简单的 web 界面来添加和更改用户帐户。 <br> -如果启用目录同步 (可以设置 location 和许可证分配), 则不能使用更改用户。 <br> -不能与 SSO 选项一起使用。 <br> |
|**Windows PowerShell** | - [使用 Windows PowerShell 管理 Office 365](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> -允许您使用 Windows PowerShell 脚本在批量用户中添加用户。 <br> -可用于将位置和许可证分配给帐户, 而不考虑帐户的创建方式。 <br> |
|**批量导入** | - [同时将多个用户添加到 Office 365-管理员帮助](add-several-users-at-the-same-time.md) <br> -允许您导入 CSV 文件以将一组用户添加到 Office 365。 <br> -不能与 SSO 选项一起使用。 <br> |
|**Azure Active Directory** | -你获取 Office 365 订阅的免费版本的 Azure Active Directory。-您可以执行云用户的自助密码重置等功能, 并使用免费版本自定义登录和访问面板页。<br> -若要获取增强的功能, 您可以升级到基本版本或高级版。有关支持的功能的列表, 请参阅[Azure Active Directory 版本](https://go.microsoft.com/fwlink/p/?LinkId=698465)。<br> |
|**目录同步** | - [将本地标识与 Azure Active Directory 集成](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> -如果使用或不使用密码同步进行目录同步, 请将[Azure AD Connect 与 express 设置结合](https://go.microsoft.com/fwlink/p/?LinkID=698537)使用。  <br>  -对于多林和 SSO 选项, 请使用[自定义安装的 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。 <br> -提供启用 SSO 所需的基础结构。 <br> -许多混合方案 (暂存迁移、混合 Exchange) 都是必需的 <br> -从本地目录同步安全组和启用邮件的组。 <br> |
   
无论您打算如何将用户帐户添加到 Office 365, 您都需要管理多个帐户功能, 例如分配许可证、指定位置等。这些功能可以从 office 365 管理中心进行长期管理, 也可以[使用 office 365 PowerShell 创建用户帐户](https://go.microsoft.com/fwlink/p/?LinkId=717083)。
    
如果选择通过 Office 365 管理中心添加和管理所有用户, 您将指定位置, 并在创建 Office 365 帐户时分配许可证。因此, 不需要进行大量规划。
    
> [!IMPORTANT]
> 在 Office 365 中创建帐户, 而不分配许可证 (例如为 SharePoint Online) 意味着帐户所有者可以查看 Office 365 门户, 但不能访问公司订阅中的任何服务。分配位置和许可证后, 帐户将复制到您分配的服务或服务。用户可以登录到其帐户并使用您分配给他们的服务。