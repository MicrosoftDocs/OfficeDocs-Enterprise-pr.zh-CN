---
title: 保护 Office 365 全局管理员帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/04/2020
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
f1.keywords:
- NOCSH
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: 保护对 Office 365 订阅的全局管理员访问权限。
ms.openlocfilehash: 1ddd910a1515e11b6f57ac7581682d15eed31e5e
ms.sourcegitcommit: 7ed2eceb61615b4703ea817331e3ac6c64b27fc0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "44013405"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="c99a2-103">保护 Office 365 全局管理员帐户</span><span class="sxs-lookup"><span data-stu-id="c99a2-103">Protect your Office 365 global administrator accounts</span></span>

<span data-ttu-id="c99a2-104">*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="c99a2-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="c99a2-105">Office 365 订阅的安全违规（包括信息收集和网络钓鱼攻击）通常是通过威胁 Office 365 全局管理员帐户的凭据来实现的。</span><span class="sxs-lookup"><span data-stu-id="c99a2-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="c99a2-106">云中的安全性是您和 Microsoft 之间的合作关系：</span><span class="sxs-lookup"><span data-stu-id="c99a2-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="c99a2-107">Microsoft 云服务是基于信任和安全性的基础建立的。</span><span class="sxs-lookup"><span data-stu-id="c99a2-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="c99a2-108">Microsoft 为您提供安全控件和功能，以帮助保护您的数据和应用程序。</span><span class="sxs-lookup"><span data-stu-id="c99a2-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="c99a2-109">你拥有自己的数据和标识，并负责保护它们、本地资源的安全性以及你控制的云组件的安全性。</span><span class="sxs-lookup"><span data-stu-id="c99a2-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="c99a2-110">Microsoft 提供的功能可帮助保护你的组织，但只有在你使用它们时才有效。</span><span class="sxs-lookup"><span data-stu-id="c99a2-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="c99a2-111">如果不使用它们，可能会受到攻击。</span><span class="sxs-lookup"><span data-stu-id="c99a2-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="c99a2-112">为了保护您的全局管理员帐户，Microsoft 在这里为您提供详细说明，以帮助你执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c99a2-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="c99a2-113">创建专用的 Office 365 全局管理员帐户，并仅在必要时使用它们。</span><span class="sxs-lookup"><span data-stu-id="c99a2-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="c99a2-114">为你的专用 Office 365 全局管理员帐户配置多重身份验证，并使用最强的辅助身份验证形式。</span><span class="sxs-lookup"><span data-stu-id="c99a2-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
> [!注释]<span data-ttu-id="c99a2-115"> 尽管本文重点介绍了全局管理员帐户，但您应考虑是否需要以相同方式保护订阅中的数据（如电子数据展示管理员或安全或合规性管理员帐户）的其他帐户。</span><span class="sxs-lookup"><span data-stu-id="c99a2-115"> Although this article is focused on global administrator accounts, you should consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> <br > <span data-ttu-id="c99a2-116">全局管理员帐户可在不添加任何许可证的情况下创建。</span><span class="sxs-lookup"><span data-stu-id="c99a2-116">A global administrator account can be created without adding any licenses.</span></span>
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="c99a2-117">第 1 步：</span><span class="sxs-lookup"><span data-stu-id="c99a2-117">Step 1.</span></span> <span data-ttu-id="c99a2-118">创建专用的 Office 365 全局管理员帐户，并仅在必要时使用</span><span class="sxs-lookup"><span data-stu-id="c99a2-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="c99a2-119">与需要全局管理员权限的用户帐户分配角色相比，管理任务相对较少。</span><span class="sxs-lookup"><span data-stu-id="c99a2-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="c99a2-120">因此，请执行以下步骤，而不是使用已分配有全局管理员角色的日常用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c99a2-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="c99a2-121">确定已分配全局管理员角色的用户帐户集。</span><span class="sxs-lookup"><span data-stu-id="c99a2-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="c99a2-122">您可以使用 Azure Active （Azure AD） Directory PowerShell for Graph 命令执行此操作：</span><span class="sxs-lookup"><span data-stu-id="c99a2-122">You can do this with Azure Active (Azure AD) Directory PowerShell for Graph  command:</span></span>
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. <span data-ttu-id="c99a2-123">使用已分配有全局管理员角色的用户帐户登录到 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="c99a2-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="c99a2-124">最多可创建四个专用全局管理员用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c99a2-124">Create up to a maximum of four dedicated global administrator user accounts.</span></span> <span data-ttu-id="c99a2-125">**使用强密码，长度至少为12个字符。**</span><span class="sxs-lookup"><span data-stu-id="c99a2-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="c99a2-126">有关详细信息，请参阅[创建强密码](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。</span><span class="sxs-lookup"><span data-stu-id="c99a2-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="c99a2-127">将新帐户的密码存储在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="c99a2-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="c99a2-128">将全局管理员角色分配给每个新的专用全局管理员用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c99a2-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="c99a2-129">注销 Office 365。</span><span class="sxs-lookup"><span data-stu-id="c99a2-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="c99a2-130">使用新的专用全局管理员用户帐户之一进行登录。</span><span class="sxs-lookup"><span data-stu-id="c99a2-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="c99a2-131">对于从第1步中为其分配了全局管理员角色的每个现有用户帐户：</span><span class="sxs-lookup"><span data-stu-id="c99a2-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="c99a2-132">删除全局管理员角色。</span><span class="sxs-lookup"><span data-stu-id="c99a2-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="c99a2-133">将管理员角色分配给适合该用户的工作职能和责任的帐户。</span><span class="sxs-lookup"><span data-stu-id="c99a2-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="c99a2-134">有关 Office 365 中的各种管理员角色的详细信息，请参阅[关于管理员角色](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="c99a2-134">For more information about various admin roles in Office 365, see [About admin roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).</span></span>
    
8. <span data-ttu-id="c99a2-135">注销 Office 365。</span><span class="sxs-lookup"><span data-stu-id="c99a2-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="c99a2-136">结果应为：</span><span class="sxs-lookup"><span data-stu-id="c99a2-136">The result should be:</span></span>
  
- <span data-ttu-id="c99a2-137">订阅中唯一具备全局管理员角色的用户帐户是一组新的专用全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="c99a2-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="c99a2-138">使用以下 PowerShell 命令对此进行验证：</span><span class="sxs-lookup"><span data-stu-id="c99a2-138">Verify this with the following PowerShell command:</span></span>
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- <span data-ttu-id="c99a2-139">所有管理订阅的其他日常用户帐户分配有与其工作职责相关联的管理员角色。</span><span class="sxs-lookup"><span data-stu-id="c99a2-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="c99a2-140">从现在起，您只需使用专用全局管理员帐户，即可为需要全局管理员权限的任务进行登录。</span><span class="sxs-lookup"><span data-stu-id="c99a2-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="c99a2-141">所有其他 Office 365 的管理都必须通过向用户帐户分配其他管理角色来完成。</span><span class="sxs-lookup"><span data-stu-id="c99a2-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c99a2-142">这需要额外的步骤才能注销为您的日常用户帐户，并使用专用全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="c99a2-142">This does require additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="c99a2-143">但这只需要偶尔执行全局管理员操作。</span><span class="sxs-lookup"><span data-stu-id="c99a2-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="c99a2-144">请考虑在全局管理员帐户泄露之后恢复 Office 365 订阅需要执行更多步骤。</span><span class="sxs-lookup"><span data-stu-id="c99a2-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span>
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-additional-verification"></a><span data-ttu-id="c99a2-145">步骤 2.</span><span class="sxs-lookup"><span data-stu-id="c99a2-145">Step 2.</span></span> <span data-ttu-id="c99a2-146">为你的专用 Office 365 全局管理员帐户配置多重身份验证，并使用最强形式的额外验证</span><span class="sxs-lookup"><span data-stu-id="c99a2-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of additional verification</span></span>

<span data-ttu-id="c99a2-147">多因素身份验证（MFA）需要除帐户名称和密码之外的其他信息。</span><span class="sxs-lookup"><span data-stu-id="c99a2-147">Multi-factor authentication (MFA) requires additional information beyond the account name and password.</span></span> <span data-ttu-id="c99a2-148">Office 365 支持以下其他验证方法：</span><span class="sxs-lookup"><span data-stu-id="c99a2-148">Office 365 supports these additional verification methods:</span></span>
  
- <span data-ttu-id="c99a2-149">Microsoft Authenticator 应用</span><span class="sxs-lookup"><span data-stu-id="c99a2-149">The Microsoft Authenticator app</span></span>

- <span data-ttu-id="c99a2-150">电话联络</span><span class="sxs-lookup"><span data-stu-id="c99a2-150">A phone call</span></span>
    
- <span data-ttu-id="c99a2-151">通过短信发送的随机生成的验证代码</span><span class="sxs-lookup"><span data-stu-id="c99a2-151">A randomly generated verification code sent through a text message</span></span>
    
- <span data-ttu-id="c99a2-152">智能卡（虚拟或物理）</span><span class="sxs-lookup"><span data-stu-id="c99a2-152">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="c99a2-153">生物识别设备</span><span class="sxs-lookup"><span data-stu-id="c99a2-153">A biometric device</span></span>
    
<span data-ttu-id="c99a2-154">如果你是一位仅使用在云中存储的用户帐户的小型企业（仅限云身份验证模型），请使用以下步骤配置使用电话呼叫或发送到智能手机的短信验证代码的 MFA：</span><span class="sxs-lookup"><span data-stu-id="c99a2-154">If you are a small business that is using user accounts stored only in the cloud (the cloud-only identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="c99a2-155">[设置 MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)。</span><span class="sxs-lookup"><span data-stu-id="c99a2-155">[Set up MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="c99a2-156">为[Office 365 设置 MFA](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) ，以将电话呼叫或短信的每个专用全局管理员帐户配置为验证方法。</span><span class="sxs-lookup"><span data-stu-id="c99a2-156">[Set up MFA for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="c99a2-157">如果您是更大的组织，并且使用的是 Office 365 混合标识模型，则可以使用更多的验证选项。</span><span class="sxs-lookup"><span data-stu-id="c99a2-157">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="c99a2-158">如果已为安全基础结构设置了更强的辅助身份验证方法，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="c99a2-158">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="c99a2-159">[设置 MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)。</span><span class="sxs-lookup"><span data-stu-id="c99a2-159">[Set up MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="c99a2-160">为[Office 365 设置 MFA](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) ，为每个专用全局管理员帐户配置相应的验证方法。</span><span class="sxs-lookup"><span data-stu-id="c99a2-160">[Set up MFA for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="c99a2-161">如果所需的强验证方法的安全基础结构未就绪且无法在 Office 365 MFA 中运行，强烈建议使用电话呼叫或发送到智能手机的短信（作为临时安全措施），将专用全局管理员帐户配置为使用 MFA。</span><span class="sxs-lookup"><span data-stu-id="c99a2-161">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="c99a2-162">请勿离开专用全局管理员帐户，而不会通过 MFA 提供额外的保护。</span><span class="sxs-lookup"><span data-stu-id="c99a2-162">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="c99a2-163">有关详细信息，请参阅 [Office 365 部署的多重身份验证计划](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan)。</span><span class="sxs-lookup"><span data-stu-id="c99a2-163">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).</span></span>
  
<span data-ttu-id="c99a2-164">若要连接到具有 MFA 和 PowerShell 的 Office 365 服务，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="c99a2-164">To connect to Office 365 services with MFA and PowerShell, see these articles:</span></span>

- [<span data-ttu-id="c99a2-165">适用于用户帐户、组和许可证的 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c99a2-165">Office 365 PowerShell for user accounts, groups, and licenses</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [<span data-ttu-id="c99a2-166">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c99a2-166">Exchange Online</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-by-using-mfa)
- [<span data-ttu-id="c99a2-167">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c99a2-167">SharePoint Online</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [<span data-ttu-id="c99a2-168">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="c99a2-168">Skype for Business Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="c99a2-169">针对企业组织的其他保护</span><span class="sxs-lookup"><span data-stu-id="c99a2-169">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="c99a2-170">步骤1和2之后，使用这些其他方法，以确保全局管理员帐户以及使用它执行的配置尽可能安全。</span><span class="sxs-lookup"><span data-stu-id="c99a2-170">After steps 1 and 2, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation"></a><span data-ttu-id="c99a2-171">特权访问工作站</span><span class="sxs-lookup"><span data-stu-id="c99a2-171">Privileged access workstation</span></span>

<span data-ttu-id="c99a2-172">若要确保高特权任务的执行尽可能安全，请使用特权访问工作站（PAW）。</span><span class="sxs-lookup"><span data-stu-id="c99a2-172">To ensure that the execution of highly privileged tasks is as secure as possible, use a privileged access workstation (PAW).</span></span> <span data-ttu-id="c99a2-173">PAW 是一台专用计算机，仅用于敏感配置任务，如需要全局管理员帐户的 Office 365 配置。</span><span class="sxs-lookup"><span data-stu-id="c99a2-173">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="c99a2-174">由于此计算机不会每天用于 Internet 浏览或电子邮件，因此它会更好地受到 Internet 攻击和威胁的保护。</span><span class="sxs-lookup"><span data-stu-id="c99a2-174">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="c99a2-175">有关如何设置 PAW 的说明，请参阅[https://aka.ms/cyberpaw](https://aka.ms/cyberpaw)。</span><span class="sxs-lookup"><span data-stu-id="c99a2-175">For instructions on how to set up a PAW, see [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management"></a><span data-ttu-id="c99a2-176">Azure AD Privileged Identity Management</span><span class="sxs-lookup"><span data-stu-id="c99a2-176">Azure AD Privileged Identity Management</span></span>

<span data-ttu-id="c99a2-177">无需将全局管理员帐户永久分配给全局管理员角色，您可以使用 Azure AD 特权标识管理（PIM）按需实时分配全局管理员角色（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="c99a2-177">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD Privileged Identity Management (PIM) to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="c99a2-178">只有全局管理员帐户成为永久管理员，才会成为符合条件的管理员。</span><span class="sxs-lookup"><span data-stu-id="c99a2-178">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="c99a2-179">全局管理员角色处于非活动状态，直到有人需要它。</span><span class="sxs-lookup"><span data-stu-id="c99a2-179">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="c99a2-180">然后，完成激活过程，将全局管理员角色添加到全局管理员帐户中的预先确定的一段时间。</span><span class="sxs-lookup"><span data-stu-id="c99a2-180">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="c99a2-181">当时间过期时，PIM 将从全局管理员帐户中删除全局管理员角色。</span><span class="sxs-lookup"><span data-stu-id="c99a2-181">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="c99a2-182">使用 PIM 和此过程可大大减少全局管理员帐户易受恶意用户攻击和使用的时间量。</span><span class="sxs-lookup"><span data-stu-id="c99a2-182">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>

<span data-ttu-id="c99a2-183">PIM 可用于 Azure AD Premium P2，它包含在 Microsoft 365 企业版 E5 或企业移动性 + 安全性（EMS） E5 中，也可以为全局管理员帐户购买单独的许可证。</span><span class="sxs-lookup"><span data-stu-id="c99a2-183">PIM is available with Azure AD Premium P2, which is included with Microsoft 365 Enterprise E5 or Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span>
  
<span data-ttu-id="c99a2-184">有关详细信息，请参阅[AZURE AD 特权标识管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。</span><span class="sxs-lookup"><span data-stu-id="c99a2-184">For more information, see [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="c99a2-185">适用于 Office 365 日志记录的安全信息和事件管理（SIEM）软件</span><span class="sxs-lookup"><span data-stu-id="c99a2-185">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="c99a2-186">在服务器上运行的 SIEM 软件对应用程序和网络硬件创建的安全警报和事件执行实时分析。</span><span class="sxs-lookup"><span data-stu-id="c99a2-186">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="c99a2-187">若要允许您的 SIEM 服务器在其分析和报告功能中包含 Office 365 安全警报和事件，请将 Azure AD 集成到您的 SEIM 中。</span><span class="sxs-lookup"><span data-stu-id="c99a2-187">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate Azure AD into you SEIM.</span></span> <span data-ttu-id="c99a2-188">请参阅[Azure 日志集成简介](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)。</span><span class="sxs-lookup"><span data-stu-id="c99a2-188">See [Introduction to Azure Log Integration](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="c99a2-189">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c99a2-189">Next step</span></span>

<span data-ttu-id="c99a2-190">如果您正在为 Office 365 订阅设置标识，请参阅：</span><span class="sxs-lookup"><span data-stu-id="c99a2-190">If you're setting up identity for your Office 365 subscription, see:</span></span>

- <span data-ttu-id="c99a2-191">[仅限云的](cloud-only-identities.md)标识（如果使用仅限云标识）</span><span class="sxs-lookup"><span data-stu-id="c99a2-191">[Cloud-only identities](cloud-only-identities.md) if you're using cloud-only identity</span></span>
- <span data-ttu-id="c99a2-192">如果使用的是混合标识，则[准备进行目录同步](prepare-for-directory-synchronization.md)</span><span class="sxs-lookup"><span data-stu-id="c99a2-192">[Prepare for directory synchronization](prepare-for-directory-synchronization.md) if you're using hybrid identity</span></span>

  
## <a name="see-also"></a><span data-ttu-id="c99a2-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c99a2-193">See also</span></span>

<span data-ttu-id="c99a2-194">[Office 365 安全路线图](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)。</span><span class="sxs-lookup"><span data-stu-id="c99a2-194">[Office 365 security roadmap](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).</span></span>
