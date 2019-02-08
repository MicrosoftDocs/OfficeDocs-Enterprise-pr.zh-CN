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
ms.openlocfilehash: 41168643fb8867017865860624c8b436460fa0b8
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897515"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="250b0-103">保护 Office 365 全局管理员帐户</span><span class="sxs-lookup"><span data-stu-id="250b0-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="250b0-104">**摘要：** Office 365 订阅防止攻击基于全局管理员帐户的威胁。</span><span class="sxs-lookup"><span data-stu-id="250b0-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="250b0-p101">安全违规的 Office 365 订阅，包括网络信息和网络钓鱼攻击，通常通过会损害 Office 365 全局管理员帐户的凭据。在云中的安全性是您与 Microsoft 之间的关系：</span><span class="sxs-lookup"><span data-stu-id="250b0-p101">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account. Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="250b0-p102">信任和安全的基础上构建 Microsoft 云服务。Microsoft 提供了安全控制和功能，以帮助您保护您的数据和应用程序。</span><span class="sxs-lookup"><span data-stu-id="250b0-p102">Microsoft cloud services are built on a foundation of trust and security. Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="250b0-109">您拥有您的数据和标识和保护、 您的本地资源的安全性和云组件您控制的安全性的责任。</span><span class="sxs-lookup"><span data-stu-id="250b0-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="250b0-p103">Microsoft 提供的功能来帮助保护您的组织，但它们是使用它们时才有效。如果不使用它们，您可能会受到攻击。若要保护您的全局管理员帐户，Microsoft 在此处以帮助您进行详细说明：</span><span class="sxs-lookup"><span data-stu-id="250b0-p103">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them. If you do not use them, you may be vulnerable to attack. To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="250b0-113">创建专用的 Office 365 全局管理员帐户，使用它们仅在必要时。</span><span class="sxs-lookup"><span data-stu-id="250b0-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="250b0-114">配置为专用 Office 365 全局管理员帐户的多因素身份验证并使用最强大的辅助身份验证形式。</span><span class="sxs-lookup"><span data-stu-id="250b0-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="250b0-115">启用和配置 Office 365 云应用程序安全性监视的可疑的全局管理员帐户活动。</span><span class="sxs-lookup"><span data-stu-id="250b0-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="250b0-116">尽管本文重点介绍全局管理员帐户，您还应考虑是否其他帐户访问您的订阅，如电子数据展示管理员或安全性或合规性中的数据的全面权限管理员帐户应保护相同的方式。</span><span class="sxs-lookup"><span data-stu-id="250b0-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="250b0-p104">步骤 1。创建专用的 Office 365 全局管理员帐户，并使用它们仅在必要时</span><span class="sxs-lookup"><span data-stu-id="250b0-p104">Step 1. Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="250b0-p105">有相对较少的管理任务，如将角色分配给需要全局管理员权限的用户帐户。因此，而不是使用已分配的全局管理员角色的日常的用户帐户，请执行以下步骤操作：</span><span class="sxs-lookup"><span data-stu-id="250b0-p105">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges. Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="250b0-p106">确定用户帐户已分配的全局管理员角色的组。可以使用此命令在 Microsoft Azure Active Directory 模块用于 Windows PowerShell 命令提示符处执行此操作：</span><span class="sxs-lookup"><span data-stu-id="250b0-p106">Determine the set of user accounts that have been assigned the global admin role. You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="250b0-123">登录到 Office 365 订阅已分配的全局管理员角色的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="250b0-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="250b0-p107">创建至少一个和第五个最多专用全局管理员用户帐户。**使用强密码至少 12 字符长。** 有关详细信息，请参阅[Create 强密码](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。将新帐户的密码存储在安全位置。</span><span class="sxs-lookup"><span data-stu-id="250b0-p107">Create at least one and up to a maximum of five dedicated global administrator user accounts. **Use strong passwords at least 12 characters long.** See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information. Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="250b0-128">将全局管理员角色分配给每个新的专用的全局管理员用户帐户。</span><span class="sxs-lookup"><span data-stu-id="250b0-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="250b0-129">注销 Office 365。</span><span class="sxs-lookup"><span data-stu-id="250b0-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="250b0-130">使用一个新的专用的全局管理员用户帐户登录。</span><span class="sxs-lookup"><span data-stu-id="250b0-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="250b0-131">对于具有已分配的全局管理员角色步骤 1 中每个现有用户帐户：</span><span class="sxs-lookup"><span data-stu-id="250b0-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="250b0-132">删除全局管理员角色。</span><span class="sxs-lookup"><span data-stu-id="250b0-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="250b0-p108">管理角色分配适用于该用户的作业函数和责任的帐户。有关 Office 365 中的各种管理员角色的详细信息，请参阅[有关 Office 365 管理员角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。</span><span class="sxs-lookup"><span data-stu-id="250b0-p108">Assign admin roles to the account that are appropriate to that user's job function and responsibility. For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="250b0-135">注销 Office 365。</span><span class="sxs-lookup"><span data-stu-id="250b0-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="250b0-136">结果应：</span><span class="sxs-lookup"><span data-stu-id="250b0-136">The result should be:</span></span>
  
- <span data-ttu-id="250b0-p109">您的订阅中的具有全局管理员角色的唯一用户帐户是一组新的专用的全局管理员帐户。使用以下 PowerShell 命令进行验证：</span><span class="sxs-lookup"><span data-stu-id="250b0-p109">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts. Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="250b0-139">所有管理订阅的其他日常用户帐户分配有与其工作职责相关联的管理员角色。</span><span class="sxs-lookup"><span data-stu-id="250b0-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="250b0-p110">从此时起，您使用登录的专用的全局管理员帐户只为需要全局管理员权限的任务。通过将其他管理角色分配给用户帐户，必须完成所有其他 Office 365 管理。</span><span class="sxs-lookup"><span data-stu-id="250b0-p110">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges. All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="250b0-p111">是，这需要额外的步骤，为您的日常的用户帐户注销并使用专用的全局管理员帐户登录。但这只需进行偶尔全局管理员操作。请考虑的全局管理员帐户违反需要更多的步骤后恢复 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="250b0-p111">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account. But this only needs to be done occasionally for global administrator operations. Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="250b0-p112">步骤 2。配置为专用 Office 365 全局管理员帐户的多因素身份验证和使用最强大的辅助身份验证形式</span><span class="sxs-lookup"><span data-stu-id="250b0-p112">Step 2. Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="250b0-p113">全局管理员帐户的多因素身份验证 (MFA) 需要的帐户名和密码之外的其他信息。Office 365 支持这些验证方法：</span><span class="sxs-lookup"><span data-stu-id="250b0-p113">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password. Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="250b0-149">电话联络</span><span class="sxs-lookup"><span data-stu-id="250b0-149">A phone call</span></span>
    
- <span data-ttu-id="250b0-150">随机生成的密码</span><span class="sxs-lookup"><span data-stu-id="250b0-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="250b0-151">智能卡（虚拟或物理）</span><span class="sxs-lookup"><span data-stu-id="250b0-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="250b0-152">生物识别设备</span><span class="sxs-lookup"><span data-stu-id="250b0-152">A biometric device</span></span>
    
<span data-ttu-id="250b0-153">如果您的小型企业中使用的仅在云中 （云标识模型） 中存储的用户帐户，请使用以下步骤配置 MFA 使用电话呼叫或文本消息验证代码发送到智能电话：</span><span class="sxs-lookup"><span data-stu-id="250b0-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="250b0-154">[允许 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。</span><span class="sxs-lookup"><span data-stu-id="250b0-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="250b0-155">[设置 Office 365 的 2 步骤验证](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)配置每个相同的验证方法的专用电话呼叫或短信的全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="250b0-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="250b0-p114">如果您是较大组织正在使用 Office 365 混合的标识模型，您有更多的验证选项。如果您已有的安全基础结构就地更强的辅助身份验证方法，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="250b0-p114">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options. If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="250b0-158">[允许 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。</span><span class="sxs-lookup"><span data-stu-id="250b0-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="250b0-159">[设置 Office 365 的 2 步骤验证](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)to 配置每台专用的全局管理员帐户适当的验证方法。</span><span class="sxs-lookup"><span data-stu-id="250b0-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="250b0-p115">如果所需的更强验证方法的安全基础结构不完毕并正常运行的 Office 365 MFA，我们强烈建议您配置专用的全局管理员帐户与 MFA 使用电话呼叫或短信验证代码发送到智能电话的全局管理员帐户作为临时安全措施。不要在专用的全局管理员帐户不提供通过 MFA 的其他保护。</span><span class="sxs-lookup"><span data-stu-id="250b0-p115">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure. Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="250b0-162">有关详细信息，请参阅 [Office 365 部署的多重身份验证计划](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)。</span><span class="sxs-lookup"><span data-stu-id="250b0-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="250b0-163">若要连接到 PowerShell MFA 与 Office 365 服务，请参阅[这篇文章](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)。</span><span class="sxs-lookup"><span data-stu-id="250b0-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="250b0-p116">步骤 3。可疑的全局管理员帐户活动的监视器</span><span class="sxs-lookup"><span data-stu-id="250b0-p116">Step 3. Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="250b0-p117">Office 365 云应用程序安全性，可以创建策略，以通知您在您的订阅的可疑行为。云应用程序安全性中内置了 Office 365 E5，但也可作为单独的服务。例如，如果您没有 Office 365 E5，您可以购买全局管理员、 安全管理员和合规性管理员角色分配的用户帐户的各个云应用程序安全性的许可证。</span><span class="sxs-lookup"><span data-stu-id="250b0-p117">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription. Cloud App Security is built into Office 365 E5, but is also available as a separate service. For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="250b0-169">如果您有 Office 365 订阅中的云应用程序安全性，使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="250b0-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="250b0-170">登录到 Office 365 门户分配的安全管理员或合规性管理员角色的帐户。</span><span class="sxs-lookup"><span data-stu-id="250b0-170">Sign into the Office 365 portal with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="250b0-171">[打开 Office 365 云应用程序安全性](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)。</span><span class="sxs-lookup"><span data-stu-id="250b0-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="250b0-172">查看您的[Office 365 云应用程序安全性的异常检测策略](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6)通过特权管理活动的异常模式的电子邮件通知您。</span><span class="sxs-lookup"><span data-stu-id="250b0-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="250b0-173">若要添加到安全管理员角色的用户帐户，使用专用的全局管理员帐户和 MFA，[连接到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3)中的用户帐户的用户主体名称填充，然后运行这些命令：</span><span class="sxs-lookup"><span data-stu-id="250b0-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="250b0-174">若要添加到合规性管理员角色的用户帐户，填写的用户帐户的用户主体名称，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="250b0-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="250b0-175">对于企业版组织的其他保护</span><span class="sxs-lookup"><span data-stu-id="250b0-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="250b0-176">步骤 1-3，使用这些其他方法来确保您的全局管理员帐户，并使用其执行的配置后，可以尽可能安全。</span><span class="sxs-lookup"><span data-stu-id="250b0-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="250b0-177">授权的访问工作站 （爪）</span><span class="sxs-lookup"><span data-stu-id="250b0-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="250b0-p118">若要确保高特权任务执行尽可能安全，请使用爪。爪是仅用于敏感的配置任务，如需要全局管理员帐户的 Office 365 配置一台专用的计算机。此计算机的 Internet 浏览或电子邮件未使用每日，因为它更好地受到从 Internet 攻击和威胁。</span><span class="sxs-lookup"><span data-stu-id="250b0-p118">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW. A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account. Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="250b0-181">有关如何设置爪说明，请参阅[http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)。</span><span class="sxs-lookup"><span data-stu-id="250b0-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="250b0-182">Azure AD 权限身份管理 (PIM)</span><span class="sxs-lookup"><span data-stu-id="250b0-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="250b0-183">而不是具有永久分配全局管理员角色全局管理员帐户，您可以使用 Azure AD PIM 需要时启用按需、 实时中分配的全局管理员角色。</span><span class="sxs-lookup"><span data-stu-id="250b0-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="250b0-p119">而不是您要永久管理全局管理员帐户，它们将成为合格的管理员。全局管理员角色处于非活动状态，直到有人需要它。然后完成激活过程预先确定的一段时间添加到的全局管理员帐户的全局管理员角色。时间过后，PIM 从全局管理员帐户中删除全局管理员角色。</span><span class="sxs-lookup"><span data-stu-id="250b0-p119">Instead of your global administrator accounts being a permanent admin, they become eligible administrators. The global administrator role is inactive until someone needs it. You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time. When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="250b0-188">使用 PIM，此过程会显著缩短的全局管理员帐户受到攻击和恶意用户所使用的时间量。</span><span class="sxs-lookup"><span data-stu-id="250b0-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="250b0-189">有关详细信息，请参阅[配置 Azure AD 特权 Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。</span><span class="sxs-lookup"><span data-stu-id="250b0-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="250b0-190">PIM 可用与 Azure Active Directory Premium P2，后者包含企业移动 + 安全 (EMS) E5，或您可以购买多个单许可证的全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="250b0-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="250b0-191">Office 365 日志记录的安全信息和事件管理 (SIEM) 软件</span><span class="sxs-lookup"><span data-stu-id="250b0-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="250b0-p120">在服务器上运行的 SIEM 软件将执行安全警报和创建的应用程序和网络硬件事件的实时分析。若要允许 SIEM 服务器与其分析和报告功能中包括的 Office 365 安全通知和事件，集成这些 SIEM 系统中：</span><span class="sxs-lookup"><span data-stu-id="250b0-p120">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware. To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="250b0-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="250b0-194">Azure AD</span></span>
    
    <span data-ttu-id="250b0-195">有关详细信息，请参阅[Azure 资源到 SIEM 系统集成日志](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)。</span><span class="sxs-lookup"><span data-stu-id="250b0-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="250b0-196">Office 365 云应用安全</span><span class="sxs-lookup"><span data-stu-id="250b0-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="250b0-197">有关详细信息，请参阅[SIEM 服务器与 Office 365 云应用程序安全性集成](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)。</span><span class="sxs-lookup"><span data-stu-id="250b0-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="250b0-198">后续步骤</span><span class="sxs-lookup"><span data-stu-id="250b0-198">Next step</span></span>

<span data-ttu-id="250b0-199">请参阅[Office 365 的安全性最佳实践](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)。</span><span class="sxs-lookup"><span data-stu-id="250b0-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

