---
title: 保护 Office 365 全局管理员帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: 使用以下三个步骤保护对 Office 365 订阅的全局管理员访问。
ms.openlocfilehash: 23d47ec1f5fc4126113dd69e1ac6400d003ca41f
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573916"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>保护 Office 365 全局管理员帐户

 **摘要:** 根据全局管理员帐户的危害, 保护 Office 365 订阅免受攻击。 
  
office 365 订阅的安全违规 (包括信息收集和网络钓鱼攻击) 通常是通过威胁 office 365 全局管理员帐户的凭据来实现的。 云中的安全性是您和 Microsoft 之间的合作关系:
  
- Microsoft 云服务是基于信任和安全性的基础建立的。 Microsoft 为您提供安全控件和功能, 以帮助保护您的数据和应用程序。
    
- 你拥有自己的数据和标识, 并负责保护它们、本地资源的安全性以及你控制的云组件的安全性。
    
Microsoft 提供的功能可帮助保护你的组织, 但只有在你使用它们时才有效。 如果不使用它们, 可能会受到攻击。 为了保护您的全局管理员帐户, Microsoft 在这里为您提供详细说明, 以帮助你执行以下操作:
  
1. 创建专用的 Office 365 全局管理员帐户, 并仅在必要时使用它们。
    
2. 为你的专用 Office 365 全局管理员帐户配置多重身份验证, 并使用最强的辅助身份验证形式。
    
3. 启用和配置 Office 365 云应用安全性, 以监视可疑的全局管理员帐户活动。
    
> [!NOTE]
> 虽然本文重点介绍了全局管理员帐户, 但您还应考虑是否有其他帐户访问订阅中的数据, 如电子数据展示管理员或安全性或合规性等范围广泛的权限。管理员帐户应以相同的方式进行保护。 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>步骤 1. 创建专用的 Office 365 全局管理员帐户, 并仅在必要时使用

与需要全局管理员权限的用户帐户分配角色相比, 管理任务相对较少。 因此, 请执行以下步骤, 而不是使用已分配有全局管理员角色的日常用户帐户。
  
1. 确定已分配全局管理员角色的用户帐户集。 可以在 Microsoft Azure Active Directory Module for Windows PowerShell 命令提示符下使用以下命令执行此操作:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. 使用已分配有全局管理员角色的用户帐户登录到 Office 365 订阅。
    
3. 至少创建一个最多5个专用全局管理员用户帐户。 **使用强密码, 长度至少为12个字符。** 有关详细信息, 请参阅[创建强密码](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。 将新帐户的密码存储在安全的位置。 
    
4. 将全局管理员角色分配给每个新的专用全局管理员用户帐户。
    
5. 注销 Office 365。
    
6. 使用新的专用全局管理员用户帐户之一进行登录。
    
7. 对于从第1步中为其分配了全局管理员角色的每个现有用户帐户:
    
  - 删除全局管理员角色。
    
  - 将管理员角色分配给适合该用户的工作职能和责任的帐户。 有关 office 365 中的各种管理员角色的详细信息, 请参阅[关于 office 365 管理员角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。
    
8. 注销 Office 365。
    
结果应为:
  
- 订阅中唯一具有全局管理员角色的用户帐户是一组新的专用全局管理员帐户。 使用以下 PowerShell 命令对此进行验证:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- 所有管理订阅的其他日常用户帐户分配有与其工作职责相关联的管理员角色。
    
从现在起, 您只需使用专用全局管理员帐户, 即可为需要全局管理员权限的任务进行登录。 所有其他 Office 365 的管理都必须通过向用户帐户分配其他管理角色来完成。
  
> [!NOTE]
> 是, 这需要其他步骤以注销你的日常用户帐户, 并使用专用全局管理员帐户登录。 但这只需要偶尔执行全局管理员操作。 请考虑在全局管理员帐户泄露之后恢复 Office 365 订阅需要执行更多步骤。 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>步骤 2. 为你的专用 Office 365 全局管理员帐户配置多重身份验证, 并使用最强的辅助身份验证形式

全局管理员帐户的多重身份验证 (MFA) 需要除帐户名称和密码之外的其他信息。 Office 365 支持以下验证方法:
  
- 电话联络
    
- 随机生成的密码
    
- 智能卡（虚拟或物理）
    
- 生物识别设备
    
如果您是一款仅使用在云中存储用户帐户的小型企业 (云标识模型), 请使用以下步骤配置使用电话呼叫或发送到智能手机的短信验证代码的 MFA:
  
1. [启用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。
    
2. 为[Office 365 设置2步验证](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14), 以将电话呼叫或短信的每个专用全局管理员帐户配置为验证方法。 
    
如果您是更大的组织, 并且使用的是 Office 365 混合标识模型, 则可以使用更多的验证选项。 如果已为安全基础结构设置了更强的辅助身份验证方法, 请执行以下步骤:
  
1. [启用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。
    
2. 为[Office 365 设置2步验证](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14), 为每个专用全局管理员帐户配置相应的验证方法。 
    
如果所需的更强验证方法的安全基础结构未就绪且无法正常运行, 则强烈建议使用电话呼叫或短信将专用全局管理员帐户配置为使用 MFA。以临时安全措施的形式为全局管理员帐户发送到智能手机的验证代码。 请勿离开专用全局管理员帐户, 而不会通过 MFA 提供额外的保护。
  
有关详细信息，请参阅 [Office 365 部署的多重身份验证计划](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)。
  
若要使用 MFA 和 PowerShell 连接到 Office 365 服务, 请参阅[本文](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)。
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>步骤 3. 监视可疑的全局管理员帐户活动

Office 365 云应用安全性允许您创建策略, 以便在订阅中向您通知可疑行为。 云应用安全性内置于 Office 365 E5 中, 但也可作为单独的服务提供。 例如, 如果没有 Office 365 E5, 可以为分配了全局管理员、安全管理员和合规性管理员角色的用户帐户购买单独的云应用安全许可证。
  
如果您的 Office 365 订阅中有云应用安全性, 请按照以下步骤操作:
  
1. 使用分配了安全管理员或合规性管理员角色的帐户登录 Microsoft 365 管理中心。
    
2. [启用 Office 365 云应用安全](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)。
    
3. 查看[Office 365 Cloud App Security 中的异常检测策略](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6), 以通过电子邮件将特权管理活动的反常模式进行通知。 
    
若要将用户帐户添加到安全管理员角色, 请使用专用全局管理员帐户和 MFA[连接到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) , 填写用户帐户的用户主体名称, 然后运行以下命令: 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

若要将用户帐户添加到合规性管理员角色, 请填写用户帐户的用户主体名称, 然后运行以下命令:
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>针对企业组织的其他保护

在步骤1-3 之后, 使用这些其他方法, 以确保全局管理员帐户以及使用它执行的配置尽可能安全。
  
### <a name="privileged-access-workstation-paw"></a>特权访问工作站 (PAW)

若要确保高特权任务的执行尽可能安全, 请使用 PAW。 PAW 是一台专用计算机, 仅用于敏感配置任务, 如需要全局管理员帐户的 Office 365 配置。 由于此计算机不会每天用于 internet 浏览或电子邮件, 因此它会更好地受到 internet 攻击和威胁的保护。
  
有关如何设置 PAW 的说明, 请参阅[http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)。
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Azure AD 特权标识管理 (PIM)

您可以使用 Azure AD PIM 在需要时实时分配全局管理员角色, 而不是将全局管理员帐户永久分配给全局管理员角色, 而无需为全局管理员角色分配全局管理员帐户。
  
只有全局管理员帐户成为永久管理员, 才会成为符合条件的管理员。 全局管理员角色处于非活动状态, 直到有人需要它。 然后, 完成激活过程, 将全局管理员角色添加到全局管理员帐户中的预先确定的一段时间。 当时间过期时, PIM 将从全局管理员帐户中删除全局管理员角色。
  
使用 PIM 和此过程可大大减少全局管理员帐户易受恶意用户攻击和使用的时间量。
  
有关详细信息, 请参阅[Configure Azure AD 特权 Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。
  
> [!NOTE]
> PIM 可与 Azure Active Directory Premium P2 (包含在企业移动性 + 安全性 (EMS) E5 中) 一起使用, 也可以为全局管理员帐户购买单独的许可证。 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>适用于 Office 365 日志记录的安全信息和事件管理 (SIEM) 软件

在服务器上运行的 SIEM 软件对应用程序和网络硬件创建的安全警报和事件执行实时分析。 若要允许您的 SIEM 服务器在其分析和报告功能中包含 Office 365 安全警报和事件, 请将它们集成到您的 SIEM 系统中:
  
- Azure AD
    
    有关详细信息, 请参阅[将日志从 Azure 资源集成到 SIEM 系统](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)。
    
- Office 365 云应用安全
    
    有关详细信息, 请参阅[将 SIEM server 与 Office 365 云应用安全集成](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)。
    
## <a name="next-step"></a>后续步骤

请参阅[适用于 Office 365 的安全性最佳实践](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)。
  

