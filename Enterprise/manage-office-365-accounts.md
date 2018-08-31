---
title: 用于管理 Office 365 帐户的工具
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/3/2018
ms.audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: '了解哪些工具用于管理 Office 365 用户，以及如何您可以使用什么取决于您如何管理用户标识。 '
ms.openlocfilehash: 24a7dd72603b881ea0810d0712900bc78dc34a81
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539543"
---
# <a name="tools-to-manage-office-365-accounts"></a>用于管理 Office 365 帐户的工具

您可以管理 Office 365 用户几种不同方法，具体取决于您的配置。您可以管理 Office 365 管理中心中，Windows PowerShell 中，您的本地目录中，或在 Azure Active Directory 管理门户中的用户。只要您购买 Office 365 时，可以使用管理中心和 Windows PowerShell，管理帐户。管理云身份时在组织中的每个人都适用于 Office 365 具有单独的用户 ID 和密码。如果您希望与您的内部部署基础结构集成并让用户帐户与 Office 365 同步，您可以使用 Azure Active Directory 连接提供标识的同步和 （可选） 提供密码同步或完整单一登录功能。
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>规划在何处以及如何管理用户帐户

位置和方式可以管理您的用户帐户取决于您想要使用的 Office 365 的标识模型。两个总体模型是云身份验证和联合身份验证。
  
### <a name="cloud-authentication"></a>云身份验证

- [云身份验证](about-office-365-identity.md#cloud-authentication)-创建和管理 Office 365 管理中心中的用户，您也可以使用 Windows PowerShell 或 Azure Active Directory 管理您的用户。 
    
- [与无缝单一登录的密码哈希同步](about-office-365-identity.md)-启用内部部署目录对象在 Azure AD 身份验证的最简单方式。使用密码哈希同步 (PHS)，您可以将您的本地 Active Directory 用户帐户对象与 Office 365 同步和管理用户内部部署。 
    
- [传递身份验证与无缝单一登录](about-office-365-identity.md)-提供用于 Azure AD 身份验证服务使用一个或多个本地服务器上运行的软件代理程序验证直接与用户简单密码验证您内部部署 Active Directory。 
    
### <a name="federated-authentication"></a>联合身份验证

- [联合身份验证选项](about-office-365-identity.md#federated-authentication-options)-主要用于身份验证要求更复杂的大型企业组织的内部部署目录对象与 Office 365 同步和用户帐户是本地托管。 
    
- [第三方身份验证和标识提供程序](about-office-365-identity.md)的内部部署目录对象可能同步到 Office 365 和云资源访问主要第三方身份提供程序 (IdP) 进行管理。 
    
## <a name="managing-accounts"></a>管理帐户

决定您的组织将创建和管理帐户的方式时, 考虑以下事项：
  
- 需要连接 Office 365 和内部部署目录之间标识您的本地环境中的服务器上安装目录同步软件。
    
- 任何目录同步选项，包括 SSO 选项要求您的本地目录属性符合标准。在您的目录中使用哪些属性和哪些清理 （如果有） 所需的详细说明如何[准备通过目录同步到 Office 365 设置用户](prepare-for-directory-synchronization.md)所述。有关如何使用 IdFix 自动化目录清理的说明，请参阅[安装和运行 Office 365 IdFix 工具](install-and-run-idfix.md)。 
    
- 规划如何要创建 Office 365 帐户。
    
    下表列出了不同的帐户管理工具。
    
|**选项**|**备注**|
|:-----|:-----|
|Office 365 管理中心  <br/> |[将用户添加单独或批量到 Office 365-管理帮助](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  提供简单的 web 界面来添加和更改用户帐户。  <br/>  不能用来更改用户，如果启用了目录同步 （可以设置位置和许可证分配）。  <br/>  不能与 SSO 选项一起使用。  <br/> |
|Windows PowerShell  <br/> |[使用 Windows PowerShell 管理 Office 365](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  可以使用 Windows PowerShell 脚本批量用户中添加用户。  <br/>  可用于位置和许可证分配到帐户，而不考虑如何创建帐户。  <br/> |
|批量导入  <br/> |[同时向 Office 365 添加多个用户 - 管理员帮助](add-several-users-at-the-same-time.md) <br/>  允许您导入 CSV 文件的用户组添加到 Office 365。  <br/>  不能与 SSO 选项一起使用。  <br/> |
|Azure Active Directory  <br/> |使用 Office 365 订阅获取免费版本的 Azure Active Directory。您可以执行类似自助服务密码重置的云用户和自定义的登录和访问面板的页面使用的免费版本的功能。若要获得增强的功能，您可以升级到的基本版本，或者 premium edition。有关受支持的功能的列表，请参阅[Azure Active Directory 版本](https://go.microsoft.com/fwlink/p/?LinkId=698465)。<br/> |
|目录同步  <br/> |[将与 Azure Active Directory 集成的本地标识](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  使用或不密码同步的目录同步，使用[使用 express 设置 Azure AD 连接](https://go.microsoft.com/fwlink/p/?LinkID=698537)。  <br/>  对于多个林和 SSO 选项，使用[自定义安装的 Azure AD 连接](https://go.microsoft.com/fwlink/p/?LinkId=698430)。  <br/>  提供启用 SSO 所需的基础结构。  <br/>  所需的许多混合方案：  <br/>  暂存迁移  <br/>  混合 Exchange  <br/>  从内部部署目录同步安全组和已启用邮件组。  <br/> |
   
- 无论您打算如何添加到 Office 365 的用户帐户，您需要管理多个帐户功能，如分配许可证，指定位置，等等。这些功能可以管理长期从 Office 365 管理中心，或者您还可以[创建与 Office 365 PowerShell 中的用户帐户](https://go.microsoft.com/fwlink/p/?LinkId=717083)。
    
    如果您选择添加和管理您通过 Office 365 管理中心内的所有用户，您将指定的位置，并作为创建的 Office 365 帐户同时分配许可证。因此，不多规划，则需要。
    
    > [!IMPORTANT]
    > Office 365 中创建帐户没有将许可证分配 (to SharePoint Online，例如) 意味着帐户所有者可以查看 Office 365 门户但不是能访问任何内贵公司的订阅的服务。位置和许可证分配后，该帐户将被复制到的服务或您为其分配的服务。用户可以登录到其帐户，并使用分配给它们的服务。 
  
## <a name="next-steps"></a>后续步骤

[Office 365 与内部部署环境的集成](office-365-integration.md)
  
## <a name="see-also"></a>另请参阅

[管理 Office 365 中的用户帐户](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

