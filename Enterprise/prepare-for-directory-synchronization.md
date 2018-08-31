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
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 介绍如何准备以设置到 Office 365 的用户使用目录同步和使用此方法的长期优势。
ms.openlocfilehash: 78636fd3ec7aaaac8fa06ba8a0f2c37d76d1b045
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539798"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>准备通过目录同步到 Office 365 来设置用户

设置目录同步的用户需要更多的规划和准备比只需管理您直接在 Office 365 中的工作或学校的帐户。其他规划和准备任务所需确保您的本地 Active Directory 同步正确到 Azure Active Directory。添加到您的组织优点包括：
  
- 减少了组织中的管理程序
- （可选） 启用单一登录方案
- 在 Office 365 中自动执行帐户的更改
    
有关使用目录同步的优点的详细信息，请参阅[目录同步路线图]( https://go.microsoft.com/fwlink/p/?LinkId=525398)和[了解 Office 365 标识和 Azure Active Directory](about-office-365-identity.md)。
  
若要确定您的组织的最佳方案，请查看[目录集成工具比较](https://go.microsoft.com/fwlink/p/?LinkId=525320)。
  
## <a name="directory-cleanup-tasks"></a>目录清理任务

在开始同步您的目录之前，您需要清理您的目录。
  
查看还[属性同步到 Azure Active Directory 的 Azure AD 连接](https://go.microsoft.com/fwlink/p/?LinkId=746480)。
  
> [!IMPORTANT]
> 如果您不执行目录清理同步之前，，可以显著负面影响的部署过程。它可能需要数天，或几周内，通过目录同步，确定错误，以及重新同步周期。 
  
在您的本地目录中，完成以下清理任务：
  
1. 确保每个将分配有 Office 365 服务的用户都在 **proxyAddresses** 属性中具有有效的唯一电子邮件地址。 
    
2. 删除 **proxyAddresses** 属性中所有重复的值。 
    
3.  如果可能，请确保每个用户都将分配给 Office 365 服务产品的用户的**用户**对象中具有**userPrincipalName**属性的有效且唯一值。为了最佳同步体验，请确保在本地 Active Directory UPN 与云 UPN 匹配。如果用户不具有**userPrincipalName**属性的值，**用户**对象必须包含**sAMAccountName**属性的有效且唯一值。**UserPrincipalName**属性中删除任何重复值。 
    
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

您的本地目录和 Office 365 之间的成功的目录同步需要您的本地目录属性正确准备好。例如，您需要确保在与 Office 365 环境同步的某些属性中不使用的特定字符。意外的字符不会导致目录同步失败，但可能返回一条警告。无效字符将导致目录同步失败。
  
如果您的 Active Directory 用户的一些具有一个或多个重复属性，也将失败目录同步。每个用户必须拥有唯一的属性。
  
下面列出了您需要准备的属性：
  
 **注意：** 您还可以使用[IdFix 工具](install-and-run-idfix.md)以使此过程容易得多。 
  
- **displayName**
    
  - 如果该属性存在于用户对象中，它会与 Office 365 进行同步。
  - 如果此属性在用户对象中，就必须有一个对应它的值。也就是说，该属性不能为空。
  - 最大字符数：256
    
- **givenName **
    
  - 如果该属性在用户对象中，它会与 Office 365 同步，但 Office 365 并不需要或使用它。
  - 最大字符数：64
    
- **邮件**
    
  - 在目录中，属性值必须是唯一的。
    
    > [!NOTE]
    > 如果有重复值，将同步的第一个用户的值。后续的用户不会出现在 Office 365。您必须修改 Office 365 中的值或修改同时为这两个用户在 Office 365 中显示的顺序中的本地目录中的值。 
  
- **mailNickname**（Exchange 别名） 
    
  - 属性值不能以句点 （.） 开头。
  - 在目录中，属性值必须是唯一的。
    
- **proxyAddresses **
    
  - 多值属性
  - 每个值的最大字符数：256
  - 属性值不能包含空格。
  - 在目录中，属性值必须是唯一的。
  - 无效字符： \< \> （);, [ ] "
    
    请注意无效字符，用于关注类型分隔符的字符和":"，以便允许 SMTP:User@contso.com，但不是 SMTP:user:M@contoso.com。
    
    > [!IMPORTANT]
    > 所有简单邮件传输协议 (SMTP) 地址都应符合电子邮件消息标准。如果存在重复或不需要的地址，请参阅帮助主题[Exchange 中删除重复的和不必要的代理地址](https://go.microsoft.com/fwlink/?LinkId=293860)。 
  
- **sAMAccountName**
    
  - 最大字符数：20
  - 在目录中，属性值必须是唯一的。
  - 无效字符: [\"|，/: \< \> + =;？\* ]
  - 如果用户具有无效 **sAMAccountName** 属性，但具有有效 **userPrincipalName** 属性，则在 Office 365 中创建用户帐户。 
  - 如果**sAMAccountName**和**userprincipalname 属性**均无效，则必须更新本地 Active Directory **userPrincipalName**属性。 
    
- **sn**（姓氏） 
    
  - 如果该属性在用户对象中，它会与 Office 365 同步，但 Office 365 并不需要或使用它。
    
- **targetAddress**
    
    需要填充用户的**targetAddress**属性 (例如，SMTP:tom@contoso.com) 必须出现在 Office 365 GAL。在第三方消息迁移方案中，这将需要为内部部署目录的 Office 365 架构扩展。Office 365 架构扩展还将添加其他有用的属性，用于管理 Office 365 对象使用目录同步工具从内部部署目录进行填充。例如，将添加**msExchHideFromAddressLists**属性来管理隐藏的邮箱或通讯组。 
   
  - 最大字符数：256
  - 属性值不能包含空格。
  - 在目录中，属性值必须是唯一的。
  - 无效字符: \ \< \> （);, [ ] "
  - 所有简单邮件传输协议 (SMTP) 地址都应符合电子邮件消息标准。
    
- **userPrincipalName**
    
  - **UserPrincipalName**属性必须是格式为 Internet 风格登录用户名后跟 at 符号 (@) 和域名： 例如，user@contoso.com。所有简单邮件传输协议 (SMTP) 地址都应符合电子邮件消息标准。
  - **userPrincipalName** 属性的最大字符数是 113。允许在 at 符号 (@) 的前后使用一定数量的字符，如下所示： 
  - at 符号 (@) 前用户名的最大字符数：64
  - at 符号 (@) 后域名的最大字符数：48
  - 无效字符: \ % &amp; \* + / =？{ } |\< \> ( ) ;: , [ ] "
  - Umlaut 也是无效的字符。
  - 每个**userPrincipalName**值中都需要 @ 符。 
  - @ 符在每个 **userPrincipalName** 值中不能作为第一个字符。 
  - 用户名不能以句点 （.）、 & 符号结尾 (&amp;)、 空格或 at 符号 (@)。
  - 用户名中不能包含任何空格。
  - 必须使用可路由域;例如，不能使用本地域或内部域。
  - Unicode 将转换为下划线字符。
  - 在目录中，**userPrincipalName** 不能包含任何重复值。 
    
## <a name="prepare-the-userprincipalname-attribute"></a>准备 userPrincipalName 属性

Active Directory 旨在允许组织使用**sAMAccountName**或**userPrincipalName**登录到您的目录中的最终用户。同样，最终用户可以使用其工作的用户主体名称 (UPN) 登录到 Office 365 或学校帐户。目录同步将尝试使用位于您的本地目录中的同一 UPN 在 Azure Active Directory 中创建新用户。UPN 的格式与电子邮件地址。 

在 Office 365 UPN 是用于生成的电子邮件地址的默认属性。可以轻松获取**userPrincipalName** (内部部署和 Azure Active Directory 中) 和**proxyAddresses**设置为不同的值中的主电子邮件地址。时被设置为不同的值可以是为管理员和最终用户的混乱。 
  
最好对齐这些属性，以减少了混淆情况。以满足要求的单一登录与 Active Directory 联合身份验证服务 (AD FS) 2.0，您需要确保在 Azure Active Directory 和您的本地 Active Directory 中的 Upn 匹配项，并使用有效的域命名空间。
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>向 AD DS 添加备用 UPN 后缀

您可能需要添加备用 UPN 后缀，以将用户的企业凭据与 Office 365 环境相关联。UPN 后缀属于右侧的 UPN @ 符。字母、 数字、 阶段、 短划线，和下划线，但没有其他类型的字符，可以包含用于单一登录的 Upn。
  
有关如何向 Active Directory 添加备用 UPN 后缀的详细信息，请参阅[准备进行目录同步]( https://go.microsoft.com/fwlink/p/?LinkId=525430)。
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>匹配的内部部署 UPN 与 Office 365 UPN

如果您已经设置了目录同步，Office 365 的用户的 UPN 可能不匹配的本地目录服务中定义的用户的内部部署 UPN。用户已分配了许可证的之前已验证域时会发生该错误。若要解决此问题，使用[PowerShell 修复重复 UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730)更新以确保 Office 365 UPN 匹配的公司的用户名和域的用户的 UPN。如果您要更新的本地目录服务中的 UPN，并且想要其 identity 为 Azure Active Directory 同步，您需要进行更改本地之前在 Office 365 中删除用户的许可证。 
  
请参阅[如何准备进行目录同步非可路由域 （如.local 域）](prepare-a-non-routable-domain-for-directory-synchronization.md)。
  
## <a name="directory-integration-tools"></a>目录集成工具

目录同步的目录对象 （用户、 组和联系人） 的本地 Active Directory 环境中到 Office 365 的目录基础结构，Azure Active Directory 同步。可用工具和其功能的列表，请参阅[目录集成工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)。推荐的工具是[Microsoft Azure Active Directory 连接](https://go.microsoft.com/fwlink/p/?LinkID=510956)。Azure Active Directory 连接的详细信息，请参阅[将您的本地标识与 Azure Active Directory 集成](https://go.microsoft.com/fwlink/p/?LinkId=527969)。
  
当用户帐户与 Office 365 目录同步的第一次时，它们标记为未激活。他们无法发送或接收电子邮件、 和它们不使用订阅许可证。时便可以分配给特定用户的 Office 365 订阅，必须选择并激活这些由[分配给为企业的 Office 365 中的用户的许可证](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。
  
您还可以使用[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)将许可证分配。自动化解决方案，请参阅[如何使用 PowerShell 将许可证自动分配给您的 Office 365 用户](https://go.microsoft.com/fwlink/p?LinkID=329805)。