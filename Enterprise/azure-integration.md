---
title: Azure 与 Office 365 集成
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
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: 你的 Office 365 订阅包括 Azure AD 订阅。 如果要使用本地环境进行密码同步或单一登录, 请将 Office 365 与 Azure AD 集成。
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490138"
---
# <a name="azure-integration-with-office-365"></a>Azure 与 Office 365 集成

Office 365 使用 azure Active Directory (azure AD) 管理场景背后的用户身份。 Office 365 订阅包括对 azure ad 的免费订阅, 因此, 如果要同步密码或使用本地环境设置单一登录, 则可以将 office 365 与 azure ad 集成。 您还可以购买高级功能, 以便更好地管理帐户。
  
Azure 还提供其他功能 (如管理集成的应用程序), 您可以使用这些功能来扩展和自定义 Office 365 订阅。
  
您可以使用 Azure AD 部署顾问来实现引导式安装和配置体验:
 - [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync)
 - [AD FS 部署顾问](https://aka.ms/adfsguidance)
 - [Azure RMS 部署向导](https://aka.ms/azuremsguidance)
 - [Azure AD 高级设置指南](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Azure AD 版本和 Office 365 身份管理

如果你已付费订阅 Office 365, 你也可以免费订阅 Azure AD。 您可以使用 Azure AD 创建和管理用户和组帐户。 若要激活此订阅, 你必须完成一次性注册。 之后, 你可以从 Office 365 管理门户访问 Azure AD。 有关说明, 请参阅[注册免费的 Azure AD 订阅](https://go.microsoft.com/fwlink/p/?LinkId=617127)。 
  
> [!TIP]
> 按照上面的说明, 注册 Office 365 订阅随附的免费 Azure AD 订阅。 请勿直接转到 azure.microsoft.com 进行注册, 否则你将结束与 microsoft azure 的试用版或付费订阅 (与 Office 365 中的免费订阅分开)。 
  
使用免费订阅, 您可以与本地目录同步, 设置单一登录, 并与服务应用程序 (如 Salesforce、DropBox 和更多) 作为服务应用程序与多个软件同步。
  
如果需要增强的 AD DS 功能、双向同步和其他管理功能, 可以将免费订阅升级到付费的高级订阅。 有关详细信息, 请参阅[Azure Active Directory 版本](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)。
  
有关 office 365 和 azure AD 的详细信息, 请参阅[了解 office 365 标识和 azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)。
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>扩展 Office 365 租户的功能

|**功能**|**说明**|
|:-----|:-----|
|集成应用程序  <br/> |您可以向各个应用授予对您的 Office 365 数据 (如邮件、日历、联系人、用户、组、文件和文件夹) 的访问权限。 你还可以在全局管理员级别授权这些应用, 并通过在 Azure AD 中注册应用, 使其对你的整个公司可用。 有关详细信息, 请参阅[集成应用和适用于 Office 365 的 Azure AD 管理员](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)。  <br/> 另请参阅[Azure AD 应用程序库和单一登录](https://go.microsoft.com/fwlink/p/?LinkId=698604)。  <br/> |
|PowerApps  <br/> | Power apps 是可连接到现有数据源 (如 SharePoint 列表和其他数据应用程序) 的移动设备的重点应用程序。 有关详细信息, 请参阅[Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) 。  <br/> |
   
有关 Microsoft 云和 Office 365 的其他资源, 请参阅以下资源:
  
- [适用于企业架构师的 Microsoft 云标识](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [在 Microsoft Azure 中部署 Office 365 目录同步 (DirSync)](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

有关详细信息[, 请参阅集成应用和 azure ad for Office 365 管理员](integrated-apps-and-azure-ads.md)和[azure ad 应用程序库和单一登录](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)。

### <a name="power-apps"></a>Power Apps
Power apps 是可连接到现有数据源 (如 SharePoint 列表和其他数据应用程序) 的移动设备的重点应用程序。 有关详细信息, 请参阅[Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) 。