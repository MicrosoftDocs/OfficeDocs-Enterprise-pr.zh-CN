---
title: Office 365 租户间协作
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: 了解 Office 365 协作方式跨租户和组织。
ms.openlocfilehash: ec844f78a0ae31469c2ca92c5cb97d965bdb3508
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219882"
---
# <a name="office-365-inter-tenant-collaboration"></a>Office 365 租户间协作

本文介绍几种方法可以两个 Office 365 租户之间进行协作。它适用于 Office 365 管理员。
  
假设两个组织，Fabrikam 和 Contoso，每个具有 Office 365 业务租户，他们希望将多个项目; 协同工作其中一些有限的时间运行，其中一些正在进行。如何 Fabrikam 和 Contoso 启用其人和团队更有效地协作跨其不同的 Office 365 租户以安全方式？与 Azure Active Directory B2B 协作结合使用的 office 365 中，提供了几个选项。本文介绍 Fabrikam 和 Contoso 可以考虑的几个主要方案。
  
Office 365 租户间协作选项包括一个中心位置用于文件和对话，共享日历、 使用 IM、 音频/视频呼叫的沟通和保护访问资源和应用程序。使用下表选择解决方案，并了解详细信息。
  
## <a name="exchange-online-collaboration-options"></a>Exchange Online 协作选项

|**共享目标**|**管理操作**|**操作方法信息**|
|:-----|:-----|:-----|
|与其他 Office 365 组织共享日历  <br/> |管理员可以设置不同的日历访问级别在 Exchange Online 以允许企业能够与其他人合作与其他企业并让用户共享的计划 （忙/闲信息）  <br/> |[Exchange Online 中的共享](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Exchange Online 中的组织关系](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [在 Exchange Online 中创建组织关系](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [修改和 Exchange Online 中的组织关系](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [在 Exchange Online 中删除组织关系](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [与外部用户共享日历](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|控制用户与组织外部的人员共享他们的日历的方式  <br/> |管理员将共享策略应用于用户邮箱，以控制谁可以与共享其和授予的访问级别  <br/> |[共享 Exchange Online 中的策略](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Exchange Online 中创建共享策略](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [将共享策略应用于 Exchange Online 中的邮箱](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [修改、 禁用或删除 Exchange Online 中的共享策略](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|配置安全电子邮件通道和控制与合作伙伴组织的邮件流  <br/> |管理员创建连接器应用于邮件交换与服务提供商或合作伙伴组织的安全性。连接器以及允许域名限制强制加密通过传输层安全性 (TLS) 或 IP 地址的范围从合作伙伴发送电子邮件。  <br/> |[Exchange Online 如何使用 TLS 保护 Office 365 中的电子邮件连接](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Exchange Online 中的远程域](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [设置用于与合作伙伴组织的安全邮件流连接器](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Exchange Online 和 Office 365 邮件流最佳做法（概述）](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online 和 OneDrive for Business 协作选项

|**共享目标**|**管理操作**|**操作方法信息**|
|:-----|:-----|:-----|
|与外部用户共享网站和文档  <br/> |管理员配置租户，请在共享或网站集级别的 Microsoft 帐户身份验证、 工作或学校帐户经过身份验证或来宾帐户  <br/> |[管理你的 SharePoint Online 环境的外部共享](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [受限的域中的共享 Office 365 SharePoint Online 和 OneDrive for Business](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [SharePoint Online 用作企业到企业 (B2B) extranet 解决方案](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|跟踪和控制针对最终用户的外部共享  <br/> |OneDrive for Business 文件所有者和 SharePoint Online 最终用户配置网站和文档共享并建立通知来跟踪共享  <br/> |[配置通知的 OneDrive for Business 的外部共享](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [在 Office 365 中共享 SharePoint 文件或文件夹](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype 的业务协作选项

|**共享目标**|**管理操作**|**操作方法信息**|
|:-----|:-----|:-----|
|与其他适用于业务用户的 Skype Skype 的业务 Online IM、 呼叫和状态  <br/> |管理员可以启用 IM 业务联机用户其 Skype、 进行音频/视频呼叫，并查看与其他 Office 365 租户中的用户的状态。  <br/> |[允许用户连接外部 Skype for Business 用户](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype 的业务 Online IM、 呼叫和与 Skype （使用者） 用户的状态  <br/> |管理员可以启用 IM 业务联机用户其 Skype、 发起呼叫，并查看与 Skype （使用者） 用户的状态。  <br/> |[让业务用户的 Skype 添加 Skype 联系人](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Azure AD B2B 协作选项

|**共享目标**|**管理操作**|**操作方法信息**|
|:-----|:-----|:-----|
|Azure AD B2B 协作-通过向组织的目录中的某个组中添加外部用户共享的内容  <br/> |一个 Office 365 租户的全局管理员可以邀请其他 Office 365 租户加入其目录中的人员将这些外部用户添加到某个组，并向内容，例如 SharePoint 网站和库组授予访问权限。  <br/> |[Azure AD B2B 协作预览是什么？](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure AD B2B： 新的更新易如反掌跨业务协作](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Office 365 外部共享和 Azure Active Directory B2B 协作](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Azure Active Directory B2B 协作 API 和自定义](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD 和标识显示： Azure AD B2B 协作 （企业到企业](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Office 365 协作选项

|**共享目标**|**管理操作**|**操作方法信息**|
|:-----|:-----|:-----|
|Office 365 组-电子邮件、 日历、 OneNote 和在中心位置共享的文件  <br/> |在业务 Essentials、 企业高级版、 教育和企业版 E1、 E3 和 E5 计划支持组。一个 Office 365 租户中的人员可以创建组，并邀请其他 Office 365 租户中作为来宾用户的人员。也适用于 Dynamics CRM。  <br/> |[了解 Office 365 组](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Office 365 组中的来宾访问](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [部署 Office 365 组](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Yammer 协作选项

|**共享目标**|**管理操作**|**操作方法信息**|
|:-----|:-----|:-----|
|Yammer-企业社交媒体通过的协作  <br/> |除非 Yammer 管理员禁用能够创建外部组，则用户可以创建外部通过对话，能够 like 和按照帖子、 共享文件、 聊天联机协作 Yammer 中的组。  <br/> |[在 Yammer 中创建和管理外部组](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>团队协作选项

|**共享目标**|**管理操作**|**操作方法信息**|
|:-----|:-----|:-----|
|与组织外部的用户在团队协作  <br/> |邀请的 Office 365 租户的全局管理员需要启用团队中的外部协作。全局管理员和团队所有者现在都将能够邀请任何人与在工作组中进行协作的电子邮件地址。  <br/> 管理员还可以管理和编辑来宾其租户中已存在。  <br/> |[授权来宾访问](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [团队中打开或关闭来宾访问](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [使用 PowerShell 来宾访问控制](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [来宾访问清单](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [查看来宾用户](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [编辑来宾用户信息](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|团队所有者可以邀请和管理来宾其团队中的协作方式。  <br/> |团队所有者具有上来宾可以在其团队内执行的操作的其他控件。  <br/> |[添加来宾](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [将来宾添加到团队](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [管理团队中的来宾访问](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [了解谁处于团队或通道](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|从其他租户的来宾可以查看团队中的内容，并与其他成员协作  <br/> |无。  <br/> |[来宾访问体验](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Power BI 协作选项

|**共享目标**|**管理操作**|**操作方法信息**|
|:-----|:-----|:-----|
|Power BI 使外部来宾用户可以使用通过链接共享的内容。这使组织中的用户以安全方式组织分配内容。<br/> | Power BI 管理员可以控制用户是否可以邀请外部用户可以查看组织内的内容。 <br/> |[分发外部来宾用户与 Azure AD B2B Power BI 内容](https://docs.microsoft.com/en-us/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>点要注意的有关 Office 365 租户间协作

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>共享的用户帐户、 许可证、 订阅和存储

每个组织维护其自己的用户帐户、 标识、 安全组、 订阅、 许可证和存储。人员使用的协作功能在 Office 365 中共享策略和安全设置以及提供对所需的信息，同时保持控制公司资产的访问。
  
- **用户帐户：** 无法共享帐户和帐户不能复制之间的租户或分区的本地 Active Directory 目录服务中。 
    
- **许可证&amp;订阅：** 在 Office 365 中，从许可计划许可 （也称为的 Sku 或 Office 365 计划） 向用户授予访问这些计划为定义的 Office 365 服务。 
    
- **存储：** 在 Office 365 计划的 SharePoint Online 软件边界和限制的单独管理从邮箱存储限制。设置和使用 Exchange Online 邮箱存储限制。在这两种方案中不能跨租户共享存储。 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>我们可以跨 Office 365 租户共享域命名空间？

不。虚拟域，如 fabrikam.com 或 tailspintoys.com，可以仅关联和时用于一个租户。每个租户必须具有自己的命名空间;不能在租户之间共享 UPN、 SMTP 和 SIP 命名空间。
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>混合组件和 Office 365 租户间协作呢？

内部部署混合组件，如 Exchange 组织和 Azure AD 连接，无法跨多个租户拆分。
  

