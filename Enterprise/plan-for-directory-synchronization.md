---
title: Office 365 的目录同步计划
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: 介绍与 Office 365、 Active Directory 清理和 Azure Active Directory 连接工具的目录同步。
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539690"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Office 365 的目录同步计划
根据业务需求和技术要求，目录同步是最常见的企业用户移动到 Office 365 设置选项。目录同步允许在本地 Active Directory 中托管的标识和所有更新对身份都同步到 Office 365。
  
有几个规划实现目录同步，包括目录准备的要求和 Azure Active Directory 功能时，需要注意的事项。目录准备介绍了很多方面。其中包括属性更新，审核和规划域控制器的位置。要求和功能规划步骤包括确定所必需的规划 multiforest 目录方案、 容量规划和双向同步的权限。
  
## <a name="office-365-identity-models"></a>Office 365 标识模型
Office 365 使用两种主要的身份验证和标识模型： 云身份验证和联合身份验证。
  
### <a name="cloud-authentication"></a>云身份验证
[云身份](about-office-365-identity.md)-创建和管理 Office 365 管理中心中的用户，您也可以使用 Windows PowerShell 或 Azure Active Directory 管理您的用户。 
  
[与无缝单一登录的密码哈希同步](about-office-365-identity.md)-启用内部部署目录对象在 Azure AD 身份验证的最简单方式。使用密码哈希同步 (PHS)，您可以将您的本地 Active Directory 用户帐户对象与 Office 365 同步和管理用户内部部署。 
  
[传递身份验证与无缝单一登录](about-office-365-identity.md)-提供用于 Azure AD 身份验证服务使用一个或多个本地服务器上运行的软件代理程序验证直接与用户简单密码验证您内部部署 Active Directory。 
  
### <a name="federated-authentication"></a>联合身份验证
[使用 Active Directory 联合身份验证服务 AD FS 联合标识](about-office-365-identity.md)-主要用于身份验证要求更复杂的大型企业组织的内部部署目录对象与 Office 365 同步和用户帐户托管在内部部署。 
  
[第三方身份验证和标识提供程序](about-office-365-identity.md)的内部部署目录对象可能同步到 Office 365 和云资源访问主要第三方身份提供程序 (IdP) 进行管理。 
  
## <a name="active-directory-cleanup"></a>Active Directory 清除
为了帮助确保使用同步无缝转换到 Office 365，我们强烈建议您在开始 Office 365 目录同步部署之前准备 Active Directory 林。
  
当您[设置 Office 365 中目录同步](set-up-directory-synchronization.md)，步骤之一是[下载并运行 IdFix 工具](install-and-run-idfix.md)。您可以使用 IdFix 工具帮助[目录清理](prepare-directory-attributes-for-synch-with-idfix.md)。
  
目录清理应专注于以下任务：

- 删除重复的**proxyAddress**和**userPrincipalName**属性。
- 使用有效的 **userPrincipalName** 属性更新空的和无效的 **userPrincipalName** 属性。
- 删除无效和可疑字符中**givenName**、 姓 ( **sn** )、 **sAMAccountName**、 **displayName**、**邮件**、 **proxyAddresses**、 **mailNickname**和**userprincipalname 属性**属性。有关准备属性的详细信息，请参阅[Azure Active Directory 同步工具同步的属性列表](https://go.microsoft.com/fwlink/p/?LinkId=396719)。
    
    > [!NOTE]
    > 这些是 Azure AD 连接同步的相同属性。 
  
## <a name="multiforest-deployment-considerations"></a>多林部署注意事项
对于多个林和 SSO 选项，使用[自定义安装的 Azure AD 连接](https://go.microsoft.com/fwlink/p/?LinkId=698430)。
  
如果您的组织具有多个林的身份验证 （登录林），强烈建议如下：
  
- **评估合并您的林。** 一般情况下，没有所需维护多个林的更多开销。除非您的组织有规定需要单独的林中的安全约束，请考虑简化您的内部部署环境。
- **仅在主登录林中的使用。** 请考虑部署仅在您的主登录林的初始部署时的 Office 365 中的 Office 365。 
    
如果您不能合并多林 Active Directory 部署或要使用其他目录服务来管理标识，您可能能够同步这些 Microsoft 或合作伙伴的帮助。
  
有关详细信息，请参阅[单一登录方案的多林目录同步](https://go.microsoft.com/fwlink/p/?LinkId=525321)。
  
## <a name="directory-integration-tools"></a>目录集成工具
目录同步到 Office 365 的目录基础结构，从内部部署 Active Directory 环境是同步的目录对象 （用户、 组和联系人）。请参阅[目录集成工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)可用的工具和其功能的列表。推荐的工具，用于是[Azure Active Directory 连接](https://go.microsoft.com/fwlink/?LinkId=525323)。
  
当用户帐户与 Office 365 目录同步的第一次时，它们被标记为未激活。他们无法发送或接收电子邮件、 和它们不使用订阅许可证。已准备好分配给特定用户的 Office 365 订阅时，必须选择并分配的有效许可证激活。
  
目录同步时，需要以下特性和功能：
  
- SSO
    
- Lync 共存
    
- Exchange 混合部署，包括：
    
  - 您的本地 Exchange 环境与 Office 365 之间完全共享全局地址列表 (GAL)。
  - 同步不同邮件系统中的 GAL 信息。
  - 能够将用户添加到和删除 Office 365 服务产品的用户。以下要求：
  - 双向同步必须配置目录同步安装过程中。默认情况下，目录同步工具仅对云编写目录信息。配置双向同步时，您会启用写回功能，以便进行有限的数量的对象属性是从云中，复制，然后写它们回本地 Active Directory。写回也称为 Exchange 混合模式。 
  - 内部部署 Exchange 混合部署
  - 将一些用户邮箱移动到 Office 365，同时保持其他用户邮箱的本地功能。
  - 安全发件人和阻止发件人本地被复制到 Office 365。
  - 基本委托和代表发送电子邮件功能。
  - 您具有本地集成的智能卡或多重身份验证解决方案。
    
- 同步照片、 缩略图、 会议室和安全组