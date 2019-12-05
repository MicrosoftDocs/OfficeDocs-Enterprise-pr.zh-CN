---
title: 准备将目录同步到 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 介绍如何准备使用目录同步将用户预配到 Office 365，以及使用此方法的长期好处。
ms.openlocfilehash: 4b602be99239d1e66b149929bd73142252f6cba6
ms.sourcegitcommit: 19e306dcc32f32387202f799d5f7ef82bae926b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2019
ms.locfileid: "39825184"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a>准备将目录同步到 Office 365

*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*

您的组织的混合标识和目录同步的好处包括：
  
- 减少组织中的管理程序
- （可选）启用单一登录方案
- 自动完成 Office 365 中的帐户更改
    
有关使用目录同步的优势的详细信息，请参阅[directory 同步路线图]( https://go.microsoft.com/fwlink/p/?LinkId=525398)和[Office 365 的混合标识](plan-for-directory-synchronization.md)。

但是，目录同步需要进行规划和准备，以确保您的 Active Directory 域服务（AD DS）同步到 Office 365 订阅的 Azure Active Directory （Azure AD）租户，其中至少有错误。 

请按照以下步骤操作，以获得最佳效果。
  
## <a name="1-directory-cleanup-tasks"></a>1. 目录清理任务

在将 AD DS 同步到 Azure AD 租户之前，需要清理 AD DS。

> [!IMPORTANT]
> 如果在同步之前不执行 AD DS 清理，则部署过程可能会产生严重的负面影响。 可能需要数天甚至数周才能完成目录同步的循环、识别错误和重新同步。 
  
在 AD DS 中，为将分配 Office 365 许可证的每个用户帐户完成以下清理任务：
  
1. 确保**proxyAddresses**属性中有一个有效且唯一的电子邮件地址。 
  
2. 删除**proxyAddresses**属性中的任何重复值。 
    
3.  如果可能，请确保用户的**用户**对象中的**userPrincipalName**属性具有有效且唯一的值。 为了获得最佳同步体验，请确保 AD DS UPN 与 Azure AD UPN 相匹配。 如果用户不具有**userPrincipalName**属性的值，则**user**对象必须包含**sAMAccountName**属性的有效且唯一的值。 删除**userPrincipalName**属性中的任何重复值。 
    
4. 若要优化全局地址列表（GAL）的使用，请确保 AD DS 用户帐户的以下属性中的信息正确：
    
  - givenName
  - surname
  - displayName
  - 职务
  - 部门
  - 办公室
  - 办公室电话
  - 移动电话
  - 传真号码
  - 街道地址
  - 城市
  - 省/自治区/直辖市
  - 邮政编码
  - 国家或地区
    
## <a name="2-directory-object-and-attribute-preparation"></a>2. 目录对象和属性准备

AD DS 和 Office 365 之间的成功目录同步要求已正确准备 AD DS 属性。 例如，您需要确保在与 Office 365 环境同步的某些属性中不使用特定的字符。 意外字符不会导致目录同步失败，但可能会返回警告。 无效字符将导致目录同步失败。
  
如果某些 AD DS 用户具有一个或多个重复的属性，则目录同步也会失败。 每个用户都必须具有唯一的属性。
  
您需要准备的属性如下所示：
  
- **displayName**
    
  - 如果该属性存在于用户对象中，它将与 Office 365 同步。
  - 如果此属性存在于 user 对象中，则它必须具有值。 也就是说，属性不得为空。
  - 最大字符数：256
    
- **givenName**
    
  - 如果该属性存在于用户对象中，它将与 Office 365 同步，但 Office 365 不需要或使用它。
  - 最大字符数：64
    
- **mail**
    
  - 属性值在目录中必须是唯一的。
    
    > [!NOTE]
    > 如果存在重复值，则将同步第一个值为的用户。 随后的用户将不会出现在 Office 365 中。 您必须修改 Office 365 中的值或修改 AD DS 中的两个值，以使两个用户都显示在 Office 365 中。 
  
- **mailNickname** （Exchange 别名） 
    
  - 属性值不能以句点（.）开头。
  - 属性值在目录中必须是唯一的。
  
    > [!NOTE]
    > 同步名称中的下划线（"_"）表示此属性的原始值包含无效字符。 原始值可以包含字母、数字和字符！、#、$、%、&、'、 \*、+、-、/、=、？、^、_、'、{、|、} 和 ~。 有关此属性的详细信息，请参阅[Exchange alias 属性](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps)。
    >
      
- **proxyAddresses**
    
  - 多值属性
  - 每个值的最大字符数：256
  - 属性值不能包含空格。
  - 属性值在目录中必须是唯一的。
  - 无效字符： \< \> （）;, [ ] " '
    
    请注意，无效字符适用于类型分隔符后面的字符和 "："，因此允许 SMTP:User@contso.com，但 SMTP:user:M@contoso.com 不是。
    
    > [!IMPORTANT]
    > 所有简单邮件传输协议（SMTP）地址都应遵守电子邮件邮件传递标准。 如果存在重复或不需要的地址，请参阅帮助主题[删除 Exchange 中的重复和不需要的代理地址](https://go.microsoft.com/fwlink/?LinkId=293860)。 
  
- **sAMAccountName**
    
  - 最大字符数：20
  - 属性值在目录中必须是唯一的。
  - 无效字符： [\ "|，/： \< \> + =;？ \* ']
  - 如果用户具有无效的**sAMAccountName**属性，但具有有效的**userPrincipalName**属性，则会在 Office 365 中创建该用户帐户。 
  - 如果**sAMAccountName**和**userPrincipalName**都无效，则必须更新 AD DS **userPrincipalName**属性。 
    
- **sn** （姓） 
    
  - 如果该属性存在于用户对象中，它将与 Office 365 同步，但 Office 365 不需要或使用它。
    
- **targetAddress**
    
    需要为用户填充的**targetAddress**属性（例如，SMTP:tom@contoso.com）必须出现在 OFFICE 365 GAL 中。 在第三方邮件迁移方案中，这将需要用于 AD DS 的 Office 365 架构扩展。 Office 365 架构扩展还将添加其他有用的属性来管理 Office 365 对象，这些对象是通过使用 AD DS 中的目录同步工具填充的。 例如，将添加用于管理隐藏邮箱或通讯组的**msExchHideFromAddressLists**属性。 
   
  - 最大字符数：256
  - 属性值不能包含空格。
  - 属性值在目录中必须是唯一的。
  - 无效字符： \ \< \> （）;, [ ] "
  - 所有简单邮件传输协议（SMTP）地址都应遵守电子邮件邮件传递标准。
    
- **userPrincipalName**
    
  - **UserPrincipalName**属性必须为 Internet 样式的登录格式，其中用户名后跟 "at" 符号（@）和域名：例如，user@contoso.com。 所有简单邮件传输协议（SMTP）地址都应遵守电子邮件邮件传递标准。
  - **UserPrincipalName**属性的最大字符数为113。 在 at 符号（@）的前面和后面允许使用特定数量的字符，如下所示： 
  - 位于 at 符号（@）前面的用户名的最大字符数（@）：64
  - At 符号（@）后面的域名的最大字符数：48
  - 无效字符： \% &amp; \* +/=？ { } | \< \> ( ) ; : , [ ] " '
  - 元音变音符也是一个无效字符。
  - 每个**userPrincipalName**值中都需要 @ 字符。 
  - @ 符在每个 **userPrincipalName** 值中不能作为第一个字符。 
  - 用户名不能以句点（.）、与号（&amp;）、空格或 at 符号（@）结尾。
  - 用户名不能包含任何空格。
  - 必须使用可路由的域;例如，不能使用本地或内部域。
  - Unicode 将转换为下划线字符。
  - **userPrincipalName**不能包含目录中的任何重复值。 

请参阅使用[IdFix 工具准备目录属性](prepare-directory-attributes-for-synch-with-idfix.md)，以使用 IdFix 工具识别 AD DS 的属性中的错误。
    
## <a name="3-prepare-the-userprincipalname-attribute"></a>3. 准备 userPrincipalName 属性

Active Directory 旨在允许组织中的最终用户使用**sAMAccountName**或**userPrincipalName**登录到您的目录。 同样，最终用户可以使用其工作或学校帐户的用户主体名称（UPN）登录 Office 365。 目录同步尝试使用 AD DS 中的同一个 UPN 在 Azure Active Directory 中创建新用户。 UPN 的格式类似于电子邮件地址。 

在 Office 365 中，UPN 是用于生成电子邮件地址的默认属性。 可以轻松获取**userPrincipalName** （在 ad DS 和 Azure AD 中）和**proxyAddresses**中的主电子邮件地址设置为不同的值。 当它们设置为不同的值时，管理员和最终用户可能会感到困惑。 
  
最好对齐这些属性以减少混淆。 若要满足单一登录与 Active Directory 联合身份验证服务（AD FS）2.0 的要求，您需要确保 Azure Active Directory 和 AD DS 中的 Upn 匹配且使用有效的域命名空间。
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. 向 AD DS 添加备用 UPN 后缀

您可能需要添加其他 UPN 后缀以将用户的公司凭据与 Office 365 环境相关联。 UPN 后缀是 @ 字符右侧的 UPN 的一部分。 用于单一登录的 UPN 可能包含字母、数字、句点、短划线和下划线，但不包含任何其他类型的字符。
  
有关如何将其他 UPN 后缀添加到 Active Directory 的详细信息，请参阅[Prepare for Directory 同步]( https://go.microsoft.com/fwlink/p/?LinkId=525430)。
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a>5. 将 AD DS UPN 与 Office 365 UPN 匹配

如果已设置目录同步，则用户的 Office 365 UPN 可能与 AD DS 中定义的用户的 AD DS UPN 不匹配。 如果在验证域前已为用户分配了许可证，则可能发生这种情况。 若要解决此问题，请使用[PowerShell 修复重复的 upn](https://go.microsoft.com/fwlink/p/?LinkId=396730)以更新用户的 upn，以确保 OFFICE 365 UPN 与公司用户名和域相匹配。 如果要在 AD DS 中更新 UPN，并希望它与 Azure Active Directory 标识同步，则需要先删除 Office 365 中的用户许可证，然后再在 AD DS 中进行更改。 
  
另请参阅[如何为目录同步准备不可路由的域（例如，本地域）](prepare-a-non-routable-domain-for-directory-synchronization.md)。


## <a name="next-steps"></a>后续步骤

请参阅[使用 IdFix 工具准备目录属性](prepare-directory-attributes-for-synch-with-idfix.md)，以帮助您在目录同步之前更正 AD DS 的属性中的错误。

如果更正了使用 IdFix 工具识别的所有属性错误，并已完成上面的步骤1到步骤5，请参阅[设置目录同步](set-up-directory-synchronization.md)。
