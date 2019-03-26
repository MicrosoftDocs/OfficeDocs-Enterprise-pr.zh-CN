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
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="e27ff-103">保护 Office 365 全局管理员帐户</span><span class="sxs-lookup"><span data-stu-id="e27ff-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="e27ff-104">**摘要:** 根据全局管理员帐户的危害, 保护 Office 365 订阅免受攻击。</span><span class="sxs-lookup"><span data-stu-id="e27ff-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="e27ff-105">office 365 订阅的安全违规 (包括信息收集和网络钓鱼攻击) 通常是通过威胁 office 365 全局管理员帐户的凭据来实现的。</span><span class="sxs-lookup"><span data-stu-id="e27ff-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="e27ff-106">云中的安全性是您和 Microsoft 之间的合作关系:</span><span class="sxs-lookup"><span data-stu-id="e27ff-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="e27ff-107">Microsoft 云服务是基于信任和安全性的基础建立的。</span><span class="sxs-lookup"><span data-stu-id="e27ff-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="e27ff-108">Microsoft 为您提供安全控件和功能, 以帮助保护您的数据和应用程序。</span><span class="sxs-lookup"><span data-stu-id="e27ff-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="e27ff-109">你拥有自己的数据和标识, 并负责保护它们、本地资源的安全性以及你控制的云组件的安全性。</span><span class="sxs-lookup"><span data-stu-id="e27ff-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="e27ff-110">Microsoft 提供的功能可帮助保护你的组织, 但只有在你使用它们时才有效。</span><span class="sxs-lookup"><span data-stu-id="e27ff-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="e27ff-111">如果不使用它们, 可能会受到攻击。</span><span class="sxs-lookup"><span data-stu-id="e27ff-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="e27ff-112">为了保护您的全局管理员帐户, Microsoft 在这里为您提供详细说明, 以帮助你执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="e27ff-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="e27ff-113">创建专用的 Office 365 全局管理员帐户, 并仅在必要时使用它们。</span><span class="sxs-lookup"><span data-stu-id="e27ff-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="e27ff-114">为你的专用 Office 365 全局管理员帐户配置多重身份验证, 并使用最强的辅助身份验证形式。</span><span class="sxs-lookup"><span data-stu-id="e27ff-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="e27ff-115">启用和配置 Office 365 云应用安全性, 以监视可疑的全局管理员帐户活动。</span><span class="sxs-lookup"><span data-stu-id="e27ff-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="e27ff-116">虽然本文重点介绍了全局管理员帐户, 但您还应考虑是否有其他帐户访问订阅中的数据, 如电子数据展示管理员或安全性或合规性等范围广泛的权限。管理员帐户应以相同的方式进行保护。</span><span class="sxs-lookup"><span data-stu-id="e27ff-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="e27ff-117">步骤 1.</span><span class="sxs-lookup"><span data-stu-id="e27ff-117">Step 1.</span></span> <span data-ttu-id="e27ff-118">创建专用的 Office 365 全局管理员帐户, 并仅在必要时使用</span><span class="sxs-lookup"><span data-stu-id="e27ff-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="e27ff-119">与需要全局管理员权限的用户帐户分配角色相比, 管理任务相对较少。</span><span class="sxs-lookup"><span data-stu-id="e27ff-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="e27ff-120">因此, 请执行以下步骤, 而不是使用已分配有全局管理员角色的日常用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e27ff-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="e27ff-121">确定已分配全局管理员角色的用户帐户集。</span><span class="sxs-lookup"><span data-stu-id="e27ff-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="e27ff-122">可以在 Microsoft Azure Active Directory Module for Windows PowerShell 命令提示符下使用以下命令执行此操作:</span><span class="sxs-lookup"><span data-stu-id="e27ff-122">You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="e27ff-123">使用已分配有全局管理员角色的用户帐户登录到 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="e27ff-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="e27ff-124">至少创建一个最多5个专用全局管理员用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e27ff-124">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="e27ff-125">**使用强密码, 长度至少为12个字符。**</span><span class="sxs-lookup"><span data-stu-id="e27ff-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="e27ff-126">有关详细信息, 请参阅[创建强密码](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="e27ff-127">将新帐户的密码存储在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="e27ff-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="e27ff-128">将全局管理员角色分配给每个新的专用全局管理员用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e27ff-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="e27ff-129">注销 Office 365。</span><span class="sxs-lookup"><span data-stu-id="e27ff-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="e27ff-130">使用新的专用全局管理员用户帐户之一进行登录。</span><span class="sxs-lookup"><span data-stu-id="e27ff-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="e27ff-131">对于从第1步中为其分配了全局管理员角色的每个现有用户帐户:</span><span class="sxs-lookup"><span data-stu-id="e27ff-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="e27ff-132">删除全局管理员角色。</span><span class="sxs-lookup"><span data-stu-id="e27ff-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="e27ff-133">将管理员角色分配给适合该用户的工作职能和责任的帐户。</span><span class="sxs-lookup"><span data-stu-id="e27ff-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="e27ff-134">有关 office 365 中的各种管理员角色的详细信息, 请参阅[关于 office 365 管理员角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-134">For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="e27ff-135">注销 Office 365。</span><span class="sxs-lookup"><span data-stu-id="e27ff-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="e27ff-136">结果应为:</span><span class="sxs-lookup"><span data-stu-id="e27ff-136">The result should be:</span></span>
  
- <span data-ttu-id="e27ff-137">订阅中唯一具有全局管理员角色的用户帐户是一组新的专用全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="e27ff-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="e27ff-138">使用以下 PowerShell 命令对此进行验证:</span><span class="sxs-lookup"><span data-stu-id="e27ff-138">Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="e27ff-139">所有管理订阅的其他日常用户帐户分配有与其工作职责相关联的管理员角色。</span><span class="sxs-lookup"><span data-stu-id="e27ff-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="e27ff-140">从现在起, 您只需使用专用全局管理员帐户, 即可为需要全局管理员权限的任务进行登录。</span><span class="sxs-lookup"><span data-stu-id="e27ff-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="e27ff-141">所有其他 Office 365 的管理都必须通过向用户帐户分配其他管理角色来完成。</span><span class="sxs-lookup"><span data-stu-id="e27ff-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e27ff-142">是, 这需要其他步骤以注销你的日常用户帐户, 并使用专用全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="e27ff-142">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="e27ff-143">但这只需要偶尔执行全局管理员操作。</span><span class="sxs-lookup"><span data-stu-id="e27ff-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="e27ff-144">请考虑在全局管理员帐户泄露之后恢复 Office 365 订阅需要执行更多步骤。</span><span class="sxs-lookup"><span data-stu-id="e27ff-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="e27ff-145">步骤 2.</span><span class="sxs-lookup"><span data-stu-id="e27ff-145">Step 2.</span></span> <span data-ttu-id="e27ff-146">为你的专用 Office 365 全局管理员帐户配置多重身份验证, 并使用最强的辅助身份验证形式</span><span class="sxs-lookup"><span data-stu-id="e27ff-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="e27ff-147">全局管理员帐户的多重身份验证 (MFA) 需要除帐户名称和密码之外的其他信息。</span><span class="sxs-lookup"><span data-stu-id="e27ff-147">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password.</span></span> <span data-ttu-id="e27ff-148">Office 365 支持以下验证方法:</span><span class="sxs-lookup"><span data-stu-id="e27ff-148">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="e27ff-149">电话联络</span><span class="sxs-lookup"><span data-stu-id="e27ff-149">A phone call</span></span>
    
- <span data-ttu-id="e27ff-150">随机生成的密码</span><span class="sxs-lookup"><span data-stu-id="e27ff-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="e27ff-151">智能卡（虚拟或物理）</span><span class="sxs-lookup"><span data-stu-id="e27ff-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="e27ff-152">生物识别设备</span><span class="sxs-lookup"><span data-stu-id="e27ff-152">A biometric device</span></span>
    
<span data-ttu-id="e27ff-153">如果您是一款仅使用在云中存储用户帐户的小型企业 (云标识模型), 请使用以下步骤配置使用电话呼叫或发送到智能手机的短信验证代码的 MFA:</span><span class="sxs-lookup"><span data-stu-id="e27ff-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="e27ff-154">[启用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="e27ff-155">为[Office 365 设置2步验证](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14), 以将电话呼叫或短信的每个专用全局管理员帐户配置为验证方法。</span><span class="sxs-lookup"><span data-stu-id="e27ff-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="e27ff-156">如果您是更大的组织, 并且使用的是 Office 365 混合标识模型, 则可以使用更多的验证选项。</span><span class="sxs-lookup"><span data-stu-id="e27ff-156">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="e27ff-157">如果已为安全基础结构设置了更强的辅助身份验证方法, 请执行以下步骤:</span><span class="sxs-lookup"><span data-stu-id="e27ff-157">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="e27ff-158">[启用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="e27ff-159">为[Office 365 设置2步验证](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14), 为每个专用全局管理员帐户配置相应的验证方法。</span><span class="sxs-lookup"><span data-stu-id="e27ff-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="e27ff-160">如果所需的更强验证方法的安全基础结构未就绪且无法正常运行, 则强烈建议使用电话呼叫或短信将专用全局管理员帐户配置为使用 MFA。以临时安全措施的形式为全局管理员帐户发送到智能手机的验证代码。</span><span class="sxs-lookup"><span data-stu-id="e27ff-160">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="e27ff-161">请勿离开专用全局管理员帐户, 而不会通过 MFA 提供额外的保护。</span><span class="sxs-lookup"><span data-stu-id="e27ff-161">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="e27ff-162">有关详细信息，请参阅 [Office 365 部署的多重身份验证计划](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="e27ff-163">若要使用 MFA 和 PowerShell 连接到 Office 365 服务, 请参阅[本文](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="e27ff-164">步骤 3.</span><span class="sxs-lookup"><span data-stu-id="e27ff-164">Step 3.</span></span> <span data-ttu-id="e27ff-165">监视可疑的全局管理员帐户活动</span><span class="sxs-lookup"><span data-stu-id="e27ff-165">Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="e27ff-166">Office 365 云应用安全性允许您创建策略, 以便在订阅中向您通知可疑行为。</span><span class="sxs-lookup"><span data-stu-id="e27ff-166">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription.</span></span> <span data-ttu-id="e27ff-167">云应用安全性内置于 Office 365 E5 中, 但也可作为单独的服务提供。</span><span class="sxs-lookup"><span data-stu-id="e27ff-167">Cloud App Security is built into Office 365 E5, but is also available as a separate service.</span></span> <span data-ttu-id="e27ff-168">例如, 如果没有 Office 365 E5, 可以为分配了全局管理员、安全管理员和合规性管理员角色的用户帐户购买单独的云应用安全许可证。</span><span class="sxs-lookup"><span data-stu-id="e27ff-168">For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="e27ff-169">如果您的 Office 365 订阅中有云应用安全性, 请按照以下步骤操作:</span><span class="sxs-lookup"><span data-stu-id="e27ff-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="e27ff-170">使用分配了安全管理员或合规性管理员角色的帐户登录 Microsoft 365 管理中心。</span><span class="sxs-lookup"><span data-stu-id="e27ff-170">Sign into the Microsoft 365 admin center with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="e27ff-171">[启用 Office 365 云应用安全](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="e27ff-172">查看[Office 365 Cloud App Security 中的异常检测策略](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6), 以通过电子邮件将特权管理活动的反常模式进行通知。</span><span class="sxs-lookup"><span data-stu-id="e27ff-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="e27ff-173">若要将用户帐户添加到安全管理员角色, 请使用专用全局管理员帐户和 MFA[连接到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) , 填写用户帐户的用户主体名称, 然后运行以下命令:</span><span class="sxs-lookup"><span data-stu-id="e27ff-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="e27ff-174">若要将用户帐户添加到合规性管理员角色, 请填写用户帐户的用户主体名称, 然后运行以下命令:</span><span class="sxs-lookup"><span data-stu-id="e27ff-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="e27ff-175">针对企业组织的其他保护</span><span class="sxs-lookup"><span data-stu-id="e27ff-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="e27ff-176">在步骤1-3 之后, 使用这些其他方法, 以确保全局管理员帐户以及使用它执行的配置尽可能安全。</span><span class="sxs-lookup"><span data-stu-id="e27ff-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="e27ff-177">特权访问工作站 (PAW)</span><span class="sxs-lookup"><span data-stu-id="e27ff-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="e27ff-178">若要确保高特权任务的执行尽可能安全, 请使用 PAW。</span><span class="sxs-lookup"><span data-stu-id="e27ff-178">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW.</span></span> <span data-ttu-id="e27ff-179">PAW 是一台专用计算机, 仅用于敏感配置任务, 如需要全局管理员帐户的 Office 365 配置。</span><span class="sxs-lookup"><span data-stu-id="e27ff-179">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="e27ff-180">由于此计算机不会每天用于 internet 浏览或电子邮件, 因此它会更好地受到 internet 攻击和威胁的保护。</span><span class="sxs-lookup"><span data-stu-id="e27ff-180">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="e27ff-181">有关如何设置 PAW 的说明, 请参阅[http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="e27ff-182">Azure AD 特权标识管理 (PIM)</span><span class="sxs-lookup"><span data-stu-id="e27ff-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="e27ff-183">您可以使用 Azure AD PIM 在需要时实时分配全局管理员角色, 而不是将全局管理员帐户永久分配给全局管理员角色, 而无需为全局管理员角色分配全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="e27ff-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="e27ff-184">只有全局管理员帐户成为永久管理员, 才会成为符合条件的管理员。</span><span class="sxs-lookup"><span data-stu-id="e27ff-184">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="e27ff-185">全局管理员角色处于非活动状态, 直到有人需要它。</span><span class="sxs-lookup"><span data-stu-id="e27ff-185">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="e27ff-186">然后, 完成激活过程, 将全局管理员角色添加到全局管理员帐户中的预先确定的一段时间。</span><span class="sxs-lookup"><span data-stu-id="e27ff-186">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="e27ff-187">当时间过期时, PIM 将从全局管理员帐户中删除全局管理员角色。</span><span class="sxs-lookup"><span data-stu-id="e27ff-187">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="e27ff-188">使用 PIM 和此过程可大大减少全局管理员帐户易受恶意用户攻击和使用的时间量。</span><span class="sxs-lookup"><span data-stu-id="e27ff-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="e27ff-189">有关详细信息, 请参阅[Configure Azure AD 特权 Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e27ff-190">PIM 可与 Azure Active Directory Premium P2 (包含在企业移动性 + 安全性 (EMS) E5 中) 一起使用, 也可以为全局管理员帐户购买单独的许可证。</span><span class="sxs-lookup"><span data-stu-id="e27ff-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="e27ff-191">适用于 Office 365 日志记录的安全信息和事件管理 (SIEM) 软件</span><span class="sxs-lookup"><span data-stu-id="e27ff-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="e27ff-192">在服务器上运行的 SIEM 软件对应用程序和网络硬件创建的安全警报和事件执行实时分析。</span><span class="sxs-lookup"><span data-stu-id="e27ff-192">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="e27ff-193">若要允许您的 SIEM 服务器在其分析和报告功能中包含 Office 365 安全警报和事件, 请将它们集成到您的 SIEM 系统中:</span><span class="sxs-lookup"><span data-stu-id="e27ff-193">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="e27ff-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="e27ff-194">Azure AD</span></span>
    
    <span data-ttu-id="e27ff-195">有关详细信息, 请参阅[将日志从 Azure 资源集成到 SIEM 系统](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="e27ff-196">Office 365 云应用安全</span><span class="sxs-lookup"><span data-stu-id="e27ff-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="e27ff-197">有关详细信息, 请参阅[将 SIEM server 与 Office 365 云应用安全集成](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="e27ff-198">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e27ff-198">Next step</span></span>

<span data-ttu-id="e27ff-199">请参阅[适用于 Office 365 的安全性最佳实践](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)。</span><span class="sxs-lookup"><span data-stu-id="e27ff-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

