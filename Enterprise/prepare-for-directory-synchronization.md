---
title: 准备通过目录同步到 Office 365 来设置用户
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
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
description: 介绍如何准备使用目录同步将用户预配到 Office 365, 以及使用此方法的长期好处。
ms.openlocfilehash: af402950b3681285898d0d87b897d363a693bf98
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085101"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>准备通过目录同步到 Office 365 来设置用户

与在 Office 365 中直接管理工作或学校帐户相比, 使用目录同步设置用户需要进行更多的规划和准备。需要执行其他规划和准备任务, 以确保您的内部部署 active directory 正确同步到 Azure Active directory。为您的组织增加的好处包括:
  
- 减少了组织中的管理程序
- (可选) 启用单一登录方案
- 在 Office 365 中自动执行帐户的更改
    
有关使用目录同步的优势的详细信息, 请参阅[目录同步路线图]( https://go.microsoft.com/fwlink/p/?LinkId=525398)和[了解 Office 365 标识和 Azure Active directory](about-office-365-identity.md)。
  
若要确定哪种方案最适合您的组织, 请查看[目录集成工具比较](https://go.microsoft.com/fwlink/p/?LinkId=525320)。
  
## <a name="directory-cleanup-tasks"></a>目录清理任务

在开始同步您的目录之前, 需要清理您的目录。
  
另请查看[azure AD Connect 同步到 azure Active Directory 的属性](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)。
  
> [!IMPORTANT]
> 如果在同步之前不执行目录清理, 则部署过程可能会产生严重的负面影响。可能需要数天甚至数周才能完成目录同步的循环、识别错误和重新同步。 
  
在您的本地目录中, 完成以下清理任务:
  
1. 确保每个将分配有 Office 365 服务的用户都在 **proxyAddresses** 属性中具有有效的唯一电子邮件地址。 
    
2. 删除 **proxyAddresses** 属性中所有重复的值。 
    
3.  如果可能, 请确保将为其分配 Office 365 服务的每个用户都具有用户**用户**对象中的**userPrincipalName**属性的有效且唯一的值。为了获得最佳同步体验, 请确保本地 Active Directory UPN 与云 UPN 相匹配。如果用户不具有**userPrincipalName**属性的值, 则**user**对象必须包含**sAMAccountName**属性的有效且唯一的值。删除**userPrincipalName**属性中的任何重复值。 
    
4. 为了更好地使用全局地址列表 (GAL)，请确保下列属性中的信息正确：
    
  - givenName 
  - 姓氏
  - displayName
  - 职务
  - 部门
  - 办公室
  - 办公室电话
  - 移动电话
  - 传真号码
  - 街道地址
  - 城市
  - 省/市/自治区
  - 邮政编码
  - 国家或地区
    
## <a name="directory-object-and-attribute-preparation"></a>目录对象和属性的准备

您的本地目录和 Office 365 之间的成功目录同步要求您的本地目录属性已正确准备就绪。例如, 您需要确保在与 Office 365 环境同步的某些属性中不使用特定的字符。意外字符不会导致目录同步失败, 但可能会返回警告。无效字符将导致目录同步失败。
  
如果某些 Active Directory 用户具有一个或多个重复的属性, 则目录同步也会失败。每个用户都必须具有唯一的属性。
  
您需要准备的属性如下所示:
  
 **注意:** 您还可以使用[IdFix 工具](install-and-run-idfix.md), 使此过程变得更加轻松。 
  
- **displayName**
    
  - 如果该属性存在于用户对象中，它会与 Office 365 进行同步。
  - 如果此属性在用户对象中，就必须有一个对应它的值。也就是说，该属性不能为空。
  - 最大字符数：256
    
- **givenName **
    
  - 如果该属性在用户对象中，它会与 Office 365 同步，但 Office 365 并不需要或使用它。
  - 最大字符数：64
    
- **mail**
    
  - 在目录中，属性值必须是唯一的。
    
    > [!NOTE]
    > 如果存在重复值, 则将同步第一个值为的用户。随后的用户将不会出现在 Office 365 中。您必须修改 office 365 中的值, 或修改本地目录中的两个值, 以使两个用户都显示在 office 365 中。 
  
- **mailNickname**（Exchange 别名） 
    
  - 属性值不能以句点 (.) 开头。
  - 在目录中，属性值必须是唯一的。
    
- **proxyAddresses **
    
  - 多值属性
  - 每个值的最大字符数：256
  - 属性值不能包含空格。
  - 在目录中，属性值必须是唯一的。
  - 无效字符: \< \> ();, [ ] "
    
    请注意, 无效字符适用于类型分隔符后面的字符和 ":", 因此允许 SMTP:User@contso.com, 但 SMTP:user:M@contoso.com 不是。
    
    > [!IMPORTANT]
    > 所有简单邮件传输协议 (SMTP) 地址都应遵守电子邮件邮件传递标准。如果存在重复或不需要的地址, 请参阅帮助主题[删除 Exchange 中的重复和不需要的代理地址](https://go.microsoft.com/fwlink/?LinkId=293860)。 
  
- **sAMAccountName**
    
  - 最大字符数：20
  - 在目录中，属性值必须是唯一的。
  - 无效字符: [\ "|,/: \< \> + =;？\* ]
  - 如果用户具有无效 **sAMAccountName** 属性，但具有有效 **userPrincipalName** 属性，则在 Office 365 中创建用户帐户。 
  - 如果**sAMAccountName**和**userPrincipalName**都无效, 则必须更新内部部署 Active Directory **userPrincipalName**属性。 
    
- **sn**（姓氏） 
    
  - 如果该属性在用户对象中，它会与 Office 365 同步，但 Office 365 并不需要或使用它。
    
- **targetAddress**
    
    需要为用户填充的**targetAddress**属性 (例如, SMTP:tom@contoso.com) 必须出现在 Office 365 GAL 中。在第三方邮件迁移方案中, 这将需要本地目录的 Office 365 架构扩展。office 365 架构扩展还将添加其他有用的属性来管理 Office 365 对象, 这些对象是使用本地目录中的目录同步工具填充的。例如, 将添加用于管理隐藏邮箱或通讯组的**msExchHideFromAddressLists**属性。 
   
  - 最大字符数：256
  - 属性值不能包含空格。
  - 在目录中，属性值必须是唯一的。
  - 无效字符: \ \< \> ();, [ ] "
  - 所有简单邮件传输协议 (SMTP) 地址都应符合电子邮件消息标准。
    
- **userPrincipalName**
    
  - **userPrincipalName**属性必须为 Internet 样式的登录格式, 其中用户名后跟 "at" 符号 (@) 和域名: 例如, user@contoso.com。所有简单邮件传输协议 (SMTP) 地址都应遵守电子邮件邮件传递标准。
  - **userPrincipalName** 属性的最大字符数是 113。允许在 at 符号 (@) 的前后使用一定数量的字符，如下所示： 
  - at 符号 (@) 前用户名的最大字符数：64
  - at 符号 (@) 后域名的最大字符数：48
  - 无效字符: \% &amp; \* +/=？{ } |\< \> ( ) ;: , [ ] "
  - 元音变音符也是一个无效字符。
  - 每个**userPrincipalName**值中都需要 @ 字符。 
  - @ 符在每个 **userPrincipalName** 值中不能作为第一个字符。 
  - 用户名不能以句点 (.)、与号 (&amp;)、空格或 at 符号 (@) 结尾。
  - 用户名中不能包含任何空格。
  - 必须使用可路由的域;例如, 不能使用本地或内部域。
  - Unicode 将转换为下划线字符。
  - 在目录中，**userPrincipalName** 不能包含任何重复值。 
    
## <a name="prepare-the-userprincipalname-attribute"></a>准备 userPrincipalName 属性

Active Directory 旨在允许组织中的最终用户使用**sAMAccountName**或**userPrincipalName**登录到您的目录。同样, 最终用户可以使用其工作或学校帐户的用户主体名称 (UPN) 登录 Office 365。目录同步尝试使用本地目录中的同一 UPN 在 Azure Active Directory 中创建新用户。UPN 的格式类似于电子邮件地址。 

在 Office 365 中, UPN 是用于生成电子邮件地址的默认属性。很容易获取**userPrincipalName** (内部部署和 Azure Active Directory 中) 和**proxyAddresses**中的主电子邮件地址设置为不同的值。当它们设置为不同的值时, 管理员和最终用户可能会感到困惑。 
  
最好对齐这些属性以减少混淆。若要满足使用 Active Directory 联合身份验证服务 (AD FS) 2.0 的单一登录要求, 您需要确保 Azure active directory 和内部部署 Active directory 中的 upn 匹配, 并且使用的是有效的域命名空间。
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>向 AD DS 添加备用 UPN 后缀

您可能需要添加其他 UPN 后缀以将用户的公司凭据与 Office 365 环境相关联。upn 后缀是 upn 在 @ 字符右侧的部分。用于单一登录的 upn 可以包含字母、数字、句点、短划线和下划线, 但不能包含其他类型的字符。
  
有关如何将其他 UPN 后缀添加到 Active Directory 的详细信息, 请参阅[Prepare for Directory 同步]( https://go.microsoft.com/fwlink/p/?LinkId=525430)。
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>将本地 UPN 与 Office 365 UPN 匹配

如果已设置目录同步, 则用户的 Office 365 upn 可能与本地目录服务中定义的用户本地 upn 不匹配。在对域进行验证之前分配了许可证时, 可能会发生这种情况。若要解决此问题, 请使用[PowerShell 修复重复的 upn](https://go.microsoft.com/fwlink/p/?LinkId=396730)以更新用户的 upn, 以确保 Office 365 UPN 与公司用户名和域相匹配。如果要在本地目录服务中更新 UPN, 并希望它与 Azure Active directory 标识同步, 则需要先删除 Office 365 中的用户许可证, 然后再进行本地更改。 
  
另请参阅[如何为目录同步准备不可路由的域 (例如, 本地域)](prepare-a-non-routable-domain-for-directory-synchronization.md)。
  
## <a name="directory-integration-tools"></a>目录集成工具

目录同步是将目录对象 (用户、组和联系人) 从本地 Active directory 环境同步到 Office 365 目录基础结构 (Azure Active directory)。有关可用工具及其功能的列表, 请参阅[目录集成工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)。推荐的工具是[Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956)。有关 azure active directory Connect 的详细信息, 请参阅[将本地标识与 Azure active directory 集成](https://go.microsoft.com/fwlink/p/?LinkId=527969)。
  
当用户帐户首次与 Office 365 目录同步时, 它们将被标记为 "未激活"。他们不能发送或接收电子邮件, 也不会使用订阅许可证。当您准备好将 office 365 订阅分配给特定用户时, 您必须通过向[Office 365 for business 中的用户分配许可证](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)来选择并激活这些订阅。
  
您还可以使用[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)分配许可证。有关自动解决方案, 请参阅[如何使用 PowerShell 自动将许可证分配给 Office 365 用户](https://go.microsoft.com/fwlink/p?LinkID=329805)。