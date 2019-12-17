---
title: 保护 Office 365 全局管理员帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
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
description: 保护对 Office 365 订阅的全局管理员访问权限。
ms.openlocfilehash: 293044fc508c89b5e08234aa62633c6c4490ba6d
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072204"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>保护 Office 365 全局管理员帐户

*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*

Office 365 订阅的安全违规（包括信息收集和网络钓鱼攻击）通常是通过威胁 Office 365 全局管理员帐户的凭据来实现的。 云中的安全性是您和 Microsoft 之间的合作关系：
  
- Microsoft 云服务是基于信任和安全性的基础建立的。 Microsoft 为您提供安全控件和功能，以帮助保护您的数据和应用程序。
    
- 你拥有自己的数据和标识，并负责保护它们、本地资源的安全性以及你控制的云组件的安全性。
    
Microsoft 提供的功能可帮助保护你的组织，但只有在你使用它们时才有效。 如果不使用它们，可能会受到攻击。 为了保护您的全局管理员帐户，Microsoft 在这里为您提供详细说明，以帮助你执行以下操作：
  
1. 创建专用的 Office 365 全局管理员帐户，并仅在必要时使用它们。
    
2. 为你的专用 Office 365 全局管理员帐户配置多重身份验证，并使用最强的辅助身份验证形式。
    
> [!NOTE]
> 虽然本文重点介绍全局管理员帐户，但您应考虑是否有其他帐户使用广域权限访问订阅中的数据，例如电子数据展示管理员或安全性或合规性管理员帐户应以相同的方式进行保护。 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>第 1 步： 创建专用的 Office 365 全局管理员帐户，并仅在必要时使用

与需要全局管理员权限的用户帐户分配角色相比，管理任务相对较少。 因此，请执行以下步骤，而不是使用已分配有全局管理员角色的日常用户帐户。
  
1. 确定已分配全局管理员角色的用户帐户集。 您可以使用 Azure Active （Azure AD） Directory PowerShell for Graph 命令执行此操作：
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. 使用已分配有全局管理员角色的用户帐户登录到 Office 365 订阅。
    
3. 至少创建一个最多5个专用全局管理员用户帐户。 **使用强密码，长度至少为12个字符。** 有关详细信息，请参阅[创建强密码](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。 将新帐户的密码存储在安全的位置。 
    
4. 将全局管理员角色分配给每个新的专用全局管理员用户帐户。
    
5. 注销 Office 365。
    
6. 使用新的专用全局管理员用户帐户之一进行登录。
    
7. 对于从第1步中为其分配了全局管理员角色的每个现有用户帐户：
    
  - 删除全局管理员角色。
    
  - 将管理员角色分配给适合该用户的工作职能和责任的帐户。 有关 Office 365 中的各种管理员角色的详细信息，请参阅[关于管理员角色](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles)。
    
8. 注销 Office 365。
    
结果应为：
  
- 订阅中唯一具备全局管理员角色的用户帐户是一组新的专用全局管理员帐户。 使用以下 PowerShell 命令对此进行验证：
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- 所有管理订阅的其他日常用户帐户分配有与其工作职责相关联的管理员角色。
    
从现在起，您只需使用专用全局管理员帐户，即可为需要全局管理员权限的任务进行登录。 所有其他 Office 365 的管理都必须通过向用户帐户分配其他管理角色来完成。
  
> [!NOTE]
> 这需要额外的步骤才能注销为您的日常用户帐户，并使用专用全局管理员帐户登录。 但这只需要偶尔执行全局管理员操作。 请考虑在全局管理员帐户泄露之后恢复 Office 365 订阅需要执行更多步骤。
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>第 2 步： 为你的专用 Office 365 全局管理员帐户配置多重身份验证，并使用最强的辅助身份验证形式

多因素身份验证（MFA）需要除帐户名称和密码之外的其他信息。 Office 365 支持以下验证方法：
  
- 电话联络
    
- 随机生成的密码
    
- 智能卡（虚拟或物理）
    
- 生物识别设备
    
如果你是一位仅使用在云中存储的用户帐户的小型企业（仅限云身份验证模型），请使用以下步骤配置使用电话呼叫或发送到智能手机的短信验证代码的 MFA：
  
1. [设置 MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)。
    
2. 为[Office 365 设置2步验证](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)，以将电话呼叫或短信的每个专用全局管理员帐户配置为验证方法。 
    
如果您是更大的组织，并且使用的是 Office 365 混合标识模型，则可以使用更多的验证选项。 如果已为安全基础结构设置了更强的辅助身份验证方法，请执行以下步骤：
  
1. [设置 MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)。
    
2. 为[Office 365 设置2步验证](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)，为每个专用全局管理员帐户配置相应的验证方法。 
    
如果所需的更强验证方法的安全基础结构未就绪且无法正常运行，则强烈建议使用电话呼叫或短信将专用全局管理员帐户配置为使用 MFA 365。以临时安全措施的形式为全局管理员帐户发送到智能手机的验证代码。 请勿离开专用全局管理员帐户，而不会通过 MFA 提供额外的保护。
  
有关详细信息，请参阅 [Office 365 部署的多重身份验证计划](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan)。
  
若要连接到具有 MFA 和 PowerShell 的 Office 365 服务，请参阅以下文章：

- [适用于用户帐户、组和许可证的 Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-by-using-mfa)
- [SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [Skype for Business Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a>针对企业组织的其他保护

步骤1和2之后，使用这些其他方法，以确保全局管理员帐户以及使用它执行的配置尽可能安全。
  
### <a name="privileged-access-workstation"></a>特权访问工作站

若要确保高特权任务的执行尽可能安全，请使用特权访问工作站（PAW）。 PAW 是一台专用计算机，仅用于敏感配置任务，如需要全局管理员帐户的 Office 365 配置。 由于此计算机不会每天用于 Internet 浏览或电子邮件，因此它会更好地受到 Internet 攻击和威胁的保护。
  
有关如何设置 PAW 的说明，请参阅[https://aka.ms/cyberpaw](https://aka.ms/cyberpaw)。
  
### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

无需将全局管理员帐户永久分配给全局管理员角色，您可以使用 Azure AD 特权标识管理（PIM）启用全局管理员角色的按需实时分配需要.
  
只有全局管理员帐户成为永久管理员，才会成为符合条件的管理员。 全局管理员角色处于非活动状态，直到有人需要它。 然后，完成激活过程，将全局管理员角色添加到全局管理员帐户中的预先确定的一段时间。 当时间过期时，PIM 将从全局管理员帐户中删除全局管理员角色。
  
使用 PIM 和此过程可大大减少全局管理员帐户易受恶意用户攻击和使用的时间量。
  
有关详细信息，请参阅[AZURE AD 特权标识管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。
  
> [!NOTE]
> PIM 可用于 Azure AD Premium P2，它包含在 Microsoft 365 企业版 E5 或企业移动性 + 安全性（EMS） E5 中，也可以为全局管理员帐户购买单独的许可证。 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>适用于 Office 365 日志记录的安全信息和事件管理（SIEM）软件

在服务器上运行的 SIEM 软件对应用程序和网络硬件创建的安全警报和事件执行实时分析。 若要允许您的 SIEM 服务器在其分析和报告功能中包含 Office 365 安全警报和事件，请将 Azure AD 集成到您的 SEIM 中。 请参阅[Azure 日志集成简介](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)。

## <a name="next-step"></a>后续步骤

如果您正在为 Office 365 订阅设置标识，请参阅：

- [仅限云的](cloud-only-identities.md)标识（如果使用仅限云标识）
- 如果使用的是混合标识，则[准备进行目录同步](prepare-for-directory-synchronization.md)

  
## <a name="see-also"></a>另请参阅

[Office 365 安全路线图](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)。
