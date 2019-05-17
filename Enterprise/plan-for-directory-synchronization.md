---
title: Office 365 的混合标识和目录同步
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
description: 介绍与 Office 365、Active Directory 域服务清理和 Azure Active Directory Connect 工具的目录同步。
ms.openlocfilehash: 31fcd8baaccabf5d3f4f0cf47c7573c43f7cd40b
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102483"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a>Office 365 的混合标识和目录同步

根据业务需求和技术要求, 混合身份模型和目录同步对于采用 Office 365 的企业客户来说是最常见的选择。 目录同步允许您在 Active Directory 域服务 (AD DS) 中管理标识, 对用户帐户、组和联系人的所有更新将同步到 Office 365 订阅的 Azure Active Directory (Azure AD) 租户。


>[!Note]
>首次同步 AD DS 用户帐户时, 不会自动为其分配 Office 365 许可证, 也不能访问 Office 365 服务 (如电子邮件)。 您必须将许可证分配给这些用户帐户, 可以单独或动态地通过组成员资格。
>

## <a name="authentication-for-hybrid-identity"></a>混合标识的身份验证

使用混合标识模型时, 有两种类型的身份验证:

- 托管身份验证

  Azure AD 通过使用本地存储的哈希版本来处理身份验证过程, 或将凭据发送到内部部署 AD DS 要进行身份验证的本地软件代理。

- 联合身份验证

  Azure AD 重定向请求身份验证的客户端计算机, 以联系另一个标识提供程序。

### <a name="managed-authentication"></a>托管身份验证

有两种类型的托管身份验证:

- 密码哈希同步 (PHS)

  Azure AD 执行身份验证本身。

- 直通身份验证 (PTA)

  Azure AD 具有 AD DS 执行身份验证。


#### <a name="password-hash-synchronization"></a>密码哈希同步

使用密码哈希同步 (PHS), 您可以将 AD DS 用户帐户与 Office 365 同步并在本地管理您的用户。 用户密码的哈希将从你的 AD DS 同步到 Azure AD, 以便用户在本地和在云中具有相同的密码。 这是在 Azure AD 中为 AD DS 标识启用身份验证的最简单方法。 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

更改密码或在本地重置密码时, 新的密码哈希将同步到 Azure AD, 以便您的用户始终可以对云资源和本地资源使用相同的密码。 用户密码永远不会发送到 Azure AD 或以明文形式存储在 Azure AD 中。 Azure AD 的一些高级功能 (如标识保护) 需要 PHS, 而不管选择了哪种身份验证方法。
  
请参阅[选择 PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)以了解详细信息。
  
#### <a name="pass-through-authentication"></a>传递身份验证

传递身份验证 (PTA) 使用在一个或多个本地服务器上运行的软件代理为 Azure AD 身份验证服务提供简单的密码验证, 以通过 AD DS 直接验证用户。 通过传递身份验证 (PTA), 您可以将 AD DS 用户帐户与 Office 365 同步并在本地管理用户。 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

PTA 允许您的用户使用其内部部署帐户和密码登录到本地和 Office 365 资源和应用程序。 此配置将直接对本地 AD DS 验证用户密码, 而无需在 Azure AD 中存储密码哈希。 

PTA 也适用于具有安全要求的组织, 以立即强制实施本地用户帐户状态、密码策略和登录时间。 
  
请参阅[选择 PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)以了解详细信息。
  
### <a name="federated-authentication"></a>联合身份验证

联合身份验证主要针对具有更复杂的身份验证要求的大型企业组织。 AD DS 标识与 Office 365 同步, 并且用户帐户在本地进行管理。 使用联合身份验证, 用户在本地和在云中具有相同的密码, 且无需再次登录才能使用 Office 365。 

联合身份验证可支持其他身份验证要求 (如基于智能卡的身份验证或第三方多重身份验证), 通常在组织具有身份验证要求时不提供由 Azure AD 本机支持。
 
若要了解详细信息, 请参阅[选择联合身份验证](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)。
  
#### <a name="third-party-authentication-and-identity-providers"></a>第三方身份验证和标识提供程序

内部部署目录对象可能会同步到 Office 365, 并且云资源访问主要由第三方标识提供程序 (IdP) 进行管理。 如果您的组织使用第三方联合解决方案, 则可以使用适用于 Office 365 的解决方案配置登录, 前提是第三方联合解决方案与 Azure AD 兼容。
  
若要了解详细信息, 请参阅[AZURE AD 联合身份验证兼容性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)。
  
## <a name="ad-ds-cleanup"></a>AD DS 清理

为了帮助确保通过使用同步无缝转换到 Office 365, 您必须在开始 Office 365 目录同步部署之前准备 AD DS 林。
  
在[Office 365 中设置目录同步](set-up-directory-synchronization.md)时, 其中一个步骤是[下载并运行 IdFix 工具](install-and-run-idfix.md)。 您可以使用 IdFix 工具来帮助[清理目录](prepare-directory-attributes-for-synch-with-idfix.md)。
  
目录清理应侧重于以下任务:

- 删除重复的**proxyAddress**和**userPrincipalName**属性。
- 使用有效的**userprincipalname**属性更新空白和无效的**userprincipalname**属性。
- 删除**givenName**、姓 ( **Sn** )、 **sAMAccountName**、 **displayName**、 **mail**、 **proxyAddresses**、 **mailNickname**和**userPrincipalName**中的无效和可疑字符诸如. 有关准备属性的详细信息, 请参阅[由 Azure Active Directory 同步工具同步的属性列表](https://go.microsoft.com/fwlink/p/?LinkId=396719)。

    > [!NOTE]
    > 这些属性与 Azure AD Connect 同步的属性相同。 
  
## <a name="multi-forest-deployment-considerations"></a>多林部署注意事项

对于多个林和 SSO 选项, 请使用[自定义安装的 AZURE AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。
  
如果您的组织具有多个林进行身份验证 (登录林), 我们强烈建议您执行以下操作:
  
- **请考虑合并你的林。** 通常情况下, 维护多个林需要更多的开销。 除非您的组织具有规定单独林需求的安全约束, 否则请考虑简化您的本地环境。
- **仅在主登录林中使用。** 请考虑仅将 Office 365 部署到主登录林中, 以实现 Office 365 的初始部署。 

如果不能合并多林 AD DS 部署或使用其他目录服务来管理标识, 则可以将它们与 Microsoft 或合作伙伴的帮助进行同步。
  
有关详细信息, 请参阅[具有单一登录方案的多林目录同步](https://go.microsoft.com/fwlink/p/?LinkId=525321)。
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>依赖于目录同步的功能
  
以下特性和功能需要目录同步:
  
- Azure AD 无缝单一登录 (SSO)
- Skype 共存
- Exchange 混合部署, 包括:
  - 内部部署 Exchange 环境与 Office 365 之间的完全共享全局地址列表 (GAL)。
  - 同步不同邮件系统中的 GAL 信息。
  - 在 Office 365 服务产品中添加和删除用户的功能。 这要求：
  - 双向同步必须在目录同步安装过程中进行配置。 默认情况下, 目录同步工具仅将目录信息写入云。 配置双向同步时, 您可以启用写回功能, 以便从云中复制有限数量的对象属性, 然后将它们写回到本地 AD DS。 写回也称为 Exchange 混合模式。 
  - 内部部署 Exchange 混合部署
  - 能够将一些用户邮箱移动到 Office 365, 同时保留本地用户邮箱。
  - 安全发件人和阻止内部的发件人将复制到 Office 365。
  - 基本委托和代表发送电子邮件功能。
  - 您具有集成的本地智能卡或多重身份验证解决方案。
- 对照片、缩略图、会议室和安全组进行同步

## <a name="next-step"></a>后续步骤

准备好部署混合标识时, 请参阅[prepare to 预配用户](prepare-for-directory-synchronization.md)。
  

