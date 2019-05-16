---
title: 规划 Office 365 的目录同步
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: 介绍与 Office 365、Active Directory 清理和 Azure Active Directory Connect 工具的目录同步。
ms.openlocfilehash: b1d48696195c572de3a87bc5acb0646fc4bd0f41
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069358"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>规划 Office 365 的目录同步

根据业务需求和技术要求, 目录同步对于要迁移到 Office 365 的企业客户来说是最常见的设置选择。 目录同步允许在本地 Active Directory 中管理标识, 并且对该标识的所有更新将同步到 Office 365。
  
在规划目录同步的实施 (包括目录准备) 以及 Azure Active Directory 的要求和功能时, 有几个要记住的事项。 目录准备涵盖了很多几个方面。 它们包括属性更新、审核和规划域控制器的位置。 规划要求和功能包括确定所需的权限、规划多林/目录方案、容量规划和双向同步。
  
## <a name="office-365-identity-models"></a>Office 365 标识模型

Office 365 使用两种主要身份验证和标识模型: 云身份验证和联合身份验证。
  
### <a name="cloud-authentication"></a>云身份验证

[云标识](about-office-365-identity.md)-在[Microsoft 365 管理中心](https://admin.microsoft.com)中创建和管理用户, 您还可以使用 Windows PowerShell 或 Azure Active Directory 管理您的用户。
  
[带有无缝单一登录的密码哈希同步](about-office-365-identity.md)-为 Azure AD 中的本地目录对象启用身份验证的最简单方法。 使用密码哈希同步 (PHS), 您可以将内部部署 Active Directory 用户帐户对象与 Office 365 同步并在本地管理您的用户。
  
[带有无缝单一登录的传递身份验证](about-office-365-identity.md)-使用在一个或多个本地服务器上运行的软件代理, 为 Azure AD 身份验证服务提供简单的密码验证, 以直接通过您的用户身份验证用户内部部署 Active Directory。
  
### <a name="federated-authentication"></a>联合身份验证

[联合身份与 Active Directory 联合身份验证服务 AD FS](about-office-365-identity.md)主要针对具有更复杂的身份验证要求的大型企业组织, 本地目录对象与 Office 365 同步, 用户帐户本地托管。
  
[第三方身份验证和标识提供程序](about-office-365-identity.md)-内部部署目录对象可能会同步到 Office 365, 并且云资源访问主要由第三方标识提供程序 (IdP) 进行管理。
  
## <a name="active-directory-cleanup"></a>Active Directory 清理

为了帮助确保通过使用同步实现无缝转换到 Office 365, 我们强烈建议您在开始 Office 365 目录同步部署之前准备 Active Directory 林。
  
在[Office 365 中设置目录同步](set-up-directory-synchronization.md)时, 其中一个步骤是[下载并运行 IdFix 工具](install-and-run-idfix.md)。 您可以使用 IdFix 工具来帮助[清理目录](prepare-directory-attributes-for-synch-with-idfix.md)。
  
目录清理应侧重于以下任务:

- 删除重复的**proxyAddress**和**userPrincipalName**属性。
- 使用有效的**userprincipalname**属性更新空白和无效的**userprincipalname**属性。
- 删除**givenName**、姓 ( **Sn** )、 **sAMAccountName**、 **displayName**、 **mail**、 **proxyAddresses**、 **mailNickname**和**userPrincipalName**中的无效和可疑字符诸如. 有关准备属性的详细信息, 请参阅[由 Azure Active Directory 同步工具同步的属性列表](https://go.microsoft.com/fwlink/p/?LinkId=396719)。

    > [!NOTE]
    > 这些属性与 Azure AD 连接同步的属性相同。 
  
## <a name="multi-forest-deployment-considerations"></a>多林部署注意事项

对于多个林和 SSO 选项, 请使用[自定义安装的 AZURE AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。
  
如果您的组织具有多个林进行身份验证 (登录林), 我们强烈建议您执行以下操作:
  
- **评估合并林。** 通常情况下, 维护多个林需要更多的开销。 除非您的组织具有规定单独林需求的安全约束, 否则请考虑简化您的本地环境。
- **仅在主登录林中使用。** 请考虑仅将 Office 365 部署到主登录林中, 以实现 Office 365 的初始部署。 

如果不能合并多林 Active Directory 部署或使用其他目录服务来管理标识, 则可以将它们与 Microsoft 或合作伙伴的帮助进行同步。
  
有关详细信息, 请参阅[具有单一登录方案的多林目录同步](https://go.microsoft.com/fwlink/p/?LinkId=525321)。
  
## <a name="directory-integration-tools"></a>目录集成工具

目录同步是将目录对象 (用户、组和联系人) 从本地 Active Directory 环境同步到 Office 365 目录基础结构。 有关可用工具及其功能的列表, 请参阅[目录集成工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)。 建议使用的工具是[Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323)。
  
当用户帐户首次与 Office 365 目录同步时, 它们会被标记为非激活。 他们不能发送或接收电子邮件, 也不会使用订阅许可证。 当您准备将 Office 365 订阅分配给特定用户时, 您必须通过分配有效的许可证来选择并激活这些订阅。
  
以下特性和功能需要目录同步:
  
- SSO
- Skype 共存
- Exchange 混合部署, 包括:
  - 内部部署 Exchange 环境与 Office 365 之间的完全共享全局地址列表 (GAL)。
  - 同步不同邮件系统中的 GAL 信息。
  - 在 Office 365 服务产品中添加和删除用户的功能。 这要求：
  - 双向同步必须在目录同步安装过程中进行配置。 默认情况下, 目录同步工具仅将目录信息写入云。 配置双向同步时, 可启用写回功能, 以便从云中复制有限数量的对象属性, 然后将这些属性重新写入本地 Active Directory 中。 写回也称为 Exchange 混合模式。 
  - 内部部署 Exchange 混合部署
  - 能够将一些用户邮箱移动到 Office 365, 同时保留本地用户邮箱。
  - 安全发件人和阻止内部的发件人将复制到 Office 365。
  - 基本委托和代表发送电子邮件功能。
  - 您具有集成的本地智能卡或多重身份验证解决方案。
- 对照片、缩略图、会议室和安全组进行同步