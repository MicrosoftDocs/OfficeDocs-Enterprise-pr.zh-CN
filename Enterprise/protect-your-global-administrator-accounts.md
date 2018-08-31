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
description: 保护向这三个步骤与 Office 365 订阅的全局管理员访问权限。
ms.openlocfilehash: 7260e903ea007735c87ab8aa826e3b97e7bd28c1
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539786"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>保护 Office 365 全局管理员帐户

 **摘要：** Office 365 订阅防止攻击基于全局管理员帐户的威胁。 
  
安全违规的 Office 365 订阅，包括网络信息和网络钓鱼攻击，通常通过会损害 Office 365 全局管理员帐户的凭据。在云中的安全性是您与 Microsoft 之间的关系：
  
- 信任和安全的基础上构建 Microsoft 云服务。Microsoft 提供了安全控制和功能，以帮助您保护您的数据和应用程序。
    
- 您拥有您的数据和标识和保护、 您的本地资源的安全性和云组件您控制的安全性的责任。
    
Microsoft 提供的功能来帮助保护您的组织，但它们是使用它们时才有效。如果不使用它们，您可能会受到攻击。若要保护您的全局管理员帐户，Microsoft 在此处以帮助您进行详细说明：
  
1. 创建专用的 Office 365 全局管理员帐户，使用它们仅在必要时。
    
2. 配置为专用 Office 365 全局管理员帐户的多因素身份验证并使用最强大的辅助身份验证形式。
    
3. 启用和配置 Office 365 云应用程序安全性监视的可疑的全局管理员帐户活动。
    
> [!NOTE]
> 尽管本文重点介绍全局管理员帐户，您还应考虑是否其他帐户访问您的订阅，如电子数据展示管理员或安全性或合规性中的数据的全面权限管理员帐户应保护相同的方式。 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>步骤 1。创建专用的 Office 365 全局管理员帐户，并使用它们仅在必要时

有相对较少的管理任务，如将角色分配给需要全局管理员权限的用户帐户。因此，而不是使用已分配的全局管理员角色的日常的用户帐户，请执行以下步骤操作：
  
1. 确定用户帐户已分配的全局管理员角色的组。可以使用此命令在 Microsoft Azure Active Directory 模块用于 Windows PowerShell 命令提示符处执行此操作：
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. 登录到 Office 365 订阅已分配的全局管理员角色的用户帐户。
    
3. 创建至少一个和第五个最多专用全局管理员用户帐户。**使用强密码至少 12 字符长。** 有关详细信息，请参阅[Create 强密码](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。将新帐户的密码存储在安全位置。 
    
4. 将全局管理员角色分配给每个新的专用的全局管理员用户帐户。
    
5. 注销 Office 365。
    
6. 使用一个新的专用的全局管理员用户帐户登录。
    
7. 对于具有已分配的全局管理员角色步骤 1 中每个现有用户帐户：
    
  - 删除全局管理员角色。
    
  - 管理角色分配适用于该用户的作业函数和责任的帐户。有关 Office 365 中的各种管理员角色的详细信息，请参阅[有关 Office 365 管理员角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。
    
8. 注销 Office 365。
    
结果应：
  
- 您的订阅中的具有全局管理员角色的唯一用户帐户是一组新的专用的全局管理员帐户。使用以下 PowerShell 命令进行验证：
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- 所有管理订阅的其他日常用户帐户分配有与其工作职责相关联的管理员角色。
    
从此时起，您使用登录的专用的全局管理员帐户只为需要全局管理员权限的任务。通过将其他管理角色分配给用户帐户，必须完成所有其他 Office 365 管理。
  
> [!NOTE]
> 是，这需要额外的步骤，为您的日常的用户帐户注销并使用专用的全局管理员帐户登录。但这只需进行偶尔全局管理员操作。请考虑的全局管理员帐户违反需要更多的步骤后恢复 Office 365 订阅。 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>步骤 2。配置为专用 Office 365 全局管理员帐户的多因素身份验证和使用最强大的辅助身份验证形式

全局管理员帐户的多因素身份验证 (MFA) 需要的帐户名和密码之外的其他信息。Office 365 支持这些验证方法：
  
- 电话呼叫
    
- 随机生成的密码
    
- 智能卡 （虚拟或物理）
    
- 生物特征设备
    
如果您的小型企业中使用的仅在云中 （云标识模型） 中存储的用户帐户，请使用以下步骤配置 MFA 使用电话呼叫或文本消息验证代码发送到智能电话：
  
1. [允许 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。
    
2. [设置 Office 365 的 2 步骤验证](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)配置每个相同的验证方法的专用电话呼叫或短信的全局管理员帐户。 
    
如果您是较大组织正在使用 Office 365 混合的标识模型，您有更多的验证选项。如果您已有的安全基础结构就地更强的辅助身份验证方法，请使用以下步骤：
  
1. [允许 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。
    
2. [设置 Office 365 的 2 步骤验证](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)to 配置每台专用的全局管理员帐户适当的验证方法。 
    
如果所需的更强验证方法的安全基础结构不完毕并正常运行的 Office 365 MFA，我们强烈建议您配置专用的全局管理员帐户与 MFA 使用电话呼叫或短信验证代码发送到智能电话的全局管理员帐户作为临时安全措施。不要在专用的全局管理员帐户不提供通过 MFA 的其他保护。
  
有关详细信息，请参阅 [Office 365 部署的多重身份验证计划](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)。
  
若要连接到 PowerShell MFA 与 Office 365 服务，请参阅[这篇文章](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)。
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>步骤 3。可疑的全局管理员帐户活动的监视器

Office 365 云应用程序安全性允许您创建策略，通知您在您的订阅的可疑行为。云应用程序安全性中内置了 Office 365 E5，但也可作为单独的服务。例如，如果您没有 Office 365 E5，您可以购买全局管理员、 安全管理员和合规性管理员角色分配的用户帐户的各个云应用程序安全性的许可证。
  
如果您有 Office 365 订阅中的云应用程序安全性，使用以下步骤：
  
1. 登录到 Office 365 门户分配的安全管理员或合规性管理员角色的帐户。
    
2. [打开 Office 365 云应用程序安全性](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)。
    
3. 查看您的[Office 365 云应用程序安全性的异常检测策略](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6)通过特权管理活动的异常模式的电子邮件通知您。 
    
若要添加到安全管理员角色的用户帐户，使用专用的全局管理员帐户和 MFA，[连接到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3)中的用户帐户的用户主体名称填充，然后运行这些命令： 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

若要添加到合规性管理员角色的用户帐户，填写的用户帐户的用户主体名称，然后运行以下命令：
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>对于企业版组织的其他保护

步骤 1-3，使用这些其他方法来确保您的全局管理员帐户，并使用其执行的配置后，可以尽可能安全。
  
### <a name="privileged-access-workstation-paw"></a>授权的访问工作站 （爪）

若要确保高特权任务执行尽可能安全，请使用爪。爪是仅用于敏感的配置任务，如需要全局管理员帐户的 Office 365 配置一台专用的计算机。此计算机的 Internet 浏览或电子邮件未使用每日，因为它更好地受到从 Internet 攻击和威胁。
  
有关如何设置爪说明，请参阅[http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)。
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Azure AD 权限身份管理 (PIM)

而不是具有永久分配全局管理员角色全局管理员帐户，您可以使用 Azure AD PIM 需要时启用按需、 实时中分配的全局管理员角色。
  
而不是您要永久管理全局管理员帐户，它们将成为合格的管理员。全局管理员角色处于非活动状态，直到有人需要它。然后完成激活过程预先确定的一段时间添加到的全局管理员帐户的全局管理员角色。时间过后，PIM 从全局管理员帐户中删除全局管理员角色。
  
使用 PIM，此过程会显著缩短的全局管理员帐户受到攻击和恶意用户所使用的时间量。
  
有关详细信息，请参阅[配置 Azure AD 特权 Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。
  
> [!NOTE]
> PIM 可用与 Azure Active Directory Premium P2，后者包含企业移动 + 安全 (EMS) E5，或您可以购买多个单许可证的全局管理员帐户。 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Office 365 日志记录的安全信息和事件管理 (SIEM) 软件

在服务器上运行的 SIEM 软件将执行安全警报和创建的应用程序和网络硬件事件的实时分析。若要允许 SIEM 服务器与其分析和报告功能中包括的 Office 365 安全通知和事件，集成这些 SIEM 系统中：
  
- Azure AD
    
    有关详细信息，请参阅[Azure 资源到 SIEM 系统集成日志](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)。
    
- Office 365 云应用安全
    
    有关详细信息，请参阅[SIEM 服务器与 Office 365 云应用程序安全性集成](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)。
    
## <a name="next-step"></a>后续步骤

请参阅[Office 365 的安全性最佳实践](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)。
  

