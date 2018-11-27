---
title: 与 Office 365 的 Azure 集成
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Office 365 订阅包括订阅 Azure AD。将 Office 365 与 Azure AD 集成，如果您希望与您的本地环境密码同步还是单一登录。
ms.openlocfilehash: 8b7af5ba8d5106900384369a3e6548af40f9e201
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674416"
---
# <a name="azure-integration-with-office-365"></a>与 Office 365 的 Azure 集成

Office 365 使用 Azure Active Directory (Azure AD) 来管理用户标识后台。Office 365 订阅包括免费订阅 Azure AD，以便您可以与 Azure AD 集成 Office 365，如果您想要同步密码或与您的本地环境的单一登录设置。您还可以购买高级的功能，以更好地管理您的帐户。
  
Azure 还提供其他一些功能，如管理集成的应用程序，可用于扩展和自定义 Office 365 订阅。
  
您可以使用 Azure AD 部署顾问以获得指导式安装和配置体验：
 - [Azure AD 连接顾问](https://aka.ms/aadconnectpwsync)
 - [AD FS 部署顾问](https://aka.ms/adfsguidance)
 - [Azure RMS 部署向导](https://aka.ms/azuremsguidance)
 - [Azure AD Premium 安装指南](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Azure AD 版本和 Office 365 标识管理

如果您具有付费的 Office 365 订阅，您还可以免费订阅 Azure AD。Azure AD 可用于创建和管理用户和组帐户。若要激活此订阅您必须完成一次性注册。此后，您可以从您的 Office 365 管理门户访问 Azure AD。有关说明，请参阅[注册免费 Azure AD 订阅](https://go.microsoft.com/fwlink/p/?LinkId=617127)。 
  
> [!TIP]
> 注册免费的 Azure AD 订阅附带到 Office 365 订阅到按照上方的说明。不直接转到 azure.microsoft.com 注册或您将结尾独立于您免费一个用于 Office 365 的 Microsoft Azure 试用版或付费订阅。 
  
与免费订阅可以与内部部署目录同步，设置单一登录，并将与多个软件同步作为服务应用程序，如销售队伍、 收存箱及更多。
  
如果您希望 AD DS 的增强的功能、 双向同步和其他管理功能，则可以将免费订阅升级为付费的 premium 订阅。有关详细信息，请参阅[Azure Active Directory 版本](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)。
  
有关 Office 365 和 Azure AD 的详细信息，请参阅[了解 Office 365 标识和 Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)。
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>扩展 Office 365 租户的功能

|**功能**|**说明**|
|:-----|:-----|
|集成的应用程序  <br/> |您可以授予各个应用程序访问 Office 365 数据，如邮件、 日历、 联系人、 用户、 组、 文件和文件夹。您还可以授权全局管理员级别这些应用程序，并使其可供整个公司使用 Azure AD 中注册应用程序。有关详细信息，请参阅[集成的应用程序和 Office 365 管理员的 Azure AD](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)。<br/> 另请参阅[Azure AD 应用程序库和单点登录](https://go.microsoft.com/fwlink/p/?LinkId=698604)。  <br/> |
|PowerApps  <br/> | 电源应用程序是重点相关应用程序可以连接到现有数据源，如 SharePoint 列表的移动设备和其他数据应用程序。有关详细信息，请参阅[创建有关 SharePoint Online 中的列表 PowerApp](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)和[PowerApps 页](https://powerapps.microsoft.com/)。<br/> |
   
有关 Microsoft 云和 Office 365 的其他资源，请参阅以下资源：
  
- [面向企业架构师的 Microsoft 云标识](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [在 Microsoft Azure 中部署 Office 365 目录同步 (DirSync)](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

了解详细信息[集成的应用程序和 Office 365 管理员的 Azure AD](integrated-apps-and-azure-ads.md)和[Azure AD 应用程序库和单点登录](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)。

### <a name="power-apps"></a>电源应用程序
电源应用程序是重点相关应用程序可以连接到现有数据源，如 SharePoint 列表的移动设备和其他数据应用程序。有关详细信息，请参阅[创建有关 SharePoint Online 中的列表 PowerApp](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)和[PowerApps 页](https://powerapps.microsoft.com/)。