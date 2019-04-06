---
title: 规划 Office 365 的目录同步
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
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
description: 介绍与 Office 365、active directory 清理和 Azure Active directory Connect 工具的目录同步。
ms.openlocfilehash: 1a7c63f699c51c829aaab5b70cb6a1a203bca3be
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001825"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a><span data-ttu-id="8ef26-103">规划 Office 365 的目录同步</span><span class="sxs-lookup"><span data-stu-id="8ef26-103">Plan for directory synchronization for Office 365</span></span>

<span data-ttu-id="8ef26-104">根据业务需求和技术要求, 目录同步对于要迁移到 Office 365 的企业客户来说是最常见的设置选择。</span><span class="sxs-lookup"><span data-stu-id="8ef26-104">Depending on business need and technical requirements, directory synchronization is the most common provisioning choice for enterprise customers who are moving to Office 365.</span></span> <span data-ttu-id="8ef26-105">目录同步允许在本地 Active Directory 中管理标识, 并且对该标识的所有更新将同步到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="8ef26-105">Directory synchronization allows identities to be managed in the on-premises Active Directory and all updates to that identity are synchronized to Office 365.</span></span>
  
<span data-ttu-id="8ef26-106">在规划目录同步的实施 (包括目录准备) 以及 Azure Active directory 的要求和功能时, 有几个要记住的事项。</span><span class="sxs-lookup"><span data-stu-id="8ef26-106">There are a couple of things to keep in mind when you plan an implementation of directory synchronization, including directory preparation, and the requirements and functionality of the Azure Active Directory.</span></span> <span data-ttu-id="8ef26-107">目录准备涵盖了很多几个方面。</span><span class="sxs-lookup"><span data-stu-id="8ef26-107">Directory preparation covers quite a few areas.</span></span> <span data-ttu-id="8ef26-108">它们包括属性更新、审核和规划域控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="8ef26-108">They include attribute updates, auditing, and planning domain controller placement.</span></span> <span data-ttu-id="8ef26-109">规划要求和功能包括确定所需的权限、规划多林/目录方案、容量规划和双向同步。</span><span class="sxs-lookup"><span data-stu-id="8ef26-109">Planning requirements and functionality includes determining the permissions that are required, planning for multi-forest/directory scenarios, capacity planning, and two-way synchronization.</span></span>
  
## <a name="office-365-identity-models"></a><span data-ttu-id="8ef26-110">Office 365 标识模型</span><span class="sxs-lookup"><span data-stu-id="8ef26-110">Office 365 identity models</span></span>

<span data-ttu-id="8ef26-111">Office 365 使用两种主要身份验证和标识模型: 云身份验证和联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="8ef26-111">Office 365 uses two main authentication and identity models: cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="8ef26-112">云身份验证</span><span class="sxs-lookup"><span data-stu-id="8ef26-112">Cloud authentication</span></span>

<span data-ttu-id="8ef26-113">[云标识](about-office-365-identity.md)-在[Microsoft 365 管理中心](https://admin.microsoft.com)中创建和管理用户, 您还可以使用 Windows PowerShell 或 Azure Active Directory 管理您的用户。</span><span class="sxs-lookup"><span data-stu-id="8ef26-113">[Cloud identity](about-office-365-identity.md) - create and manage users in the [Microsoft 365 admin center](https://admin.microsoft.com), you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span>
  
<span data-ttu-id="8ef26-114">[带有无缝单一登录的密码哈希同步](about-office-365-identity.md)-为 Azure AD 中的本地目录对象启用身份验证的最简单方法。</span><span class="sxs-lookup"><span data-stu-id="8ef26-114">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD.</span></span> <span data-ttu-id="8ef26-115">使用密码哈希同步 (PHS), 您可以将内部部署 Active Directory 用户帐户对象与 Office 365 同步并在本地管理您的用户。</span><span class="sxs-lookup"><span data-stu-id="8ef26-115">With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span>
  
<span data-ttu-id="8ef26-116">[带有无缝单一登录的传递身份验证](about-office-365-identity.md)-使用在一个或多个本地服务器上运行的软件代理, 为 Azure AD 身份验证服务提供简单的密码验证, 以直接通过您的用户身份验证用户内部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="8ef26-116">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="8ef26-117">联合身份验证</span><span class="sxs-lookup"><span data-stu-id="8ef26-117">Federated authentication</span></span>

<span data-ttu-id="8ef26-118">[联合身份与 Active Directory 联合身份验证服务 AD FS](about-office-365-identity.md)主要针对具有更复杂的身份验证要求的大型企业组织, 本地目录对象与 Office 365 同步, 用户帐户本地托管。</span><span class="sxs-lookup"><span data-stu-id="8ef26-118">[Federated identity with Active Directory Federation Services AD FS](about-office-365-identity.md) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span>
  
<span data-ttu-id="8ef26-119">[第三方身份验证和标识提供程序](about-office-365-identity.md)-内部部署目录对象可能会同步到 Office 365, 并且云资源访问主要由第三方标识提供程序 (IdP) 进行管理。</span><span class="sxs-lookup"><span data-stu-id="8ef26-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span>
  
## <a name="active-directory-cleanup"></a><span data-ttu-id="8ef26-120">Active Directory 清理</span><span class="sxs-lookup"><span data-stu-id="8ef26-120">Active Directory Cleanup</span></span>

<span data-ttu-id="8ef26-121">为了帮助确保通过使用同步实现无缝转换到 office 365, 我们强烈建议您在开始 Office 365 目录同步部署之前准备 Active Directory 林。</span><span class="sxs-lookup"><span data-stu-id="8ef26-121">To help ensure a seamless transition to Office 365 by using synchronization, we highly recommend that you prepare your Active Directory forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="8ef26-122">在[Office 365 中设置目录同步](set-up-directory-synchronization.md)时, 其中一个步骤是[下载并运行 IdFix 工具](install-and-run-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="8ef26-122">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="8ef26-123">您可以使用 IdFix 工具来帮助[清理目录](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="8ef26-123">You can use the IdFix tool to help with the [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="8ef26-124">目录清理应侧重于以下任务:</span><span class="sxs-lookup"><span data-stu-id="8ef26-124">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="8ef26-125">删除重复的**proxyAddress**和**userPrincipalName**属性。</span><span class="sxs-lookup"><span data-stu-id="8ef26-125">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="8ef26-126">使用有效的**userprincipalname**属性更新空白和无效的**userprincipalname**属性。</span><span class="sxs-lookup"><span data-stu-id="8ef26-126">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="8ef26-127">删除**givenName**、姓 ( **sn** )、 **sAMAccountName**、 **displayName**、 **mail**、 **proxyAddresses**、 **mailNickname**和**userPrincipalName**中的无效和可疑字符诸如.</span><span class="sxs-lookup"><span data-stu-id="8ef26-127">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="8ef26-128">有关准备属性的详细信息, 请参阅[由 Azure Active Directory 同步工具同步的属性列表](https://go.microsoft.com/fwlink/p/?LinkId=396719)。</span><span class="sxs-lookup"><span data-stu-id="8ef26-128">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="8ef26-129">这些属性与 Azure AD 连接同步的属性相同。</span><span class="sxs-lookup"><span data-stu-id="8ef26-129">These are the same attributes that Azure AD Connect syncs.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="8ef26-130">多林部署注意事项</span><span class="sxs-lookup"><span data-stu-id="8ef26-130">Multi-forest Deployment Considerations</span></span>

<span data-ttu-id="8ef26-131">对于多个林和 SSO 选项, 请使用[自定义安装的 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="8ef26-131">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="8ef26-132">如果您的组织具有多个林进行身份验证 (登录林), 我们强烈建议您执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="8ef26-132">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="8ef26-133">**评估合并林。**</span><span class="sxs-lookup"><span data-stu-id="8ef26-133">**Evaluate consolidating your forests.**</span></span> <span data-ttu-id="8ef26-134">通常情况下, 维护多个林需要更多的开销。</span><span class="sxs-lookup"><span data-stu-id="8ef26-134">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="8ef26-135">除非您的组织具有规定单独林需求的安全约束, 否则请考虑简化您的本地环境。</span><span class="sxs-lookup"><span data-stu-id="8ef26-135">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="8ef26-136">**仅在主登录林中使用。**</span><span class="sxs-lookup"><span data-stu-id="8ef26-136">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="8ef26-137">请考虑仅将 office 365 部署到主登录林中, 以实现 office 365 的初始部署。</span><span class="sxs-lookup"><span data-stu-id="8ef26-137">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="8ef26-138">如果不能合并多林 Active Directory 部署或使用其他目录服务来管理标识, 则可以将它们与 Microsoft 或合作伙伴的帮助进行同步。</span><span class="sxs-lookup"><span data-stu-id="8ef26-138">If you can't consolidate your multi-forest Active Directory deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="8ef26-139">有关详细信息, 请参阅[具有单一登录方案的多林目录同步](https://go.microsoft.com/fwlink/p/?LinkId=525321)。</span><span class="sxs-lookup"><span data-stu-id="8ef26-139">For more information, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="8ef26-140">目录集成工具</span><span class="sxs-lookup"><span data-stu-id="8ef26-140">Directory integration tools</span></span>

<span data-ttu-id="8ef26-141">目录同步是将目录对象 (用户、组和联系人) 从本地 Active directory 环境同步到 Office 365 目录基础结构。</span><span class="sxs-lookup"><span data-stu-id="8ef26-141">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure.</span></span> <span data-ttu-id="8ef26-142">有关可用工具及其功能的列表, 请参阅[目录集成工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)。</span><span class="sxs-lookup"><span data-stu-id="8ef26-142">See [directory integration tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality.</span></span> <span data-ttu-id="8ef26-143">建议使用的工具是[Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323)。</span><span class="sxs-lookup"><span data-stu-id="8ef26-143">The recommended tool to use is [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).</span></span>
  
<span data-ttu-id="8ef26-144">当用户帐户首次与 Office 365 目录同步时, 它们会被标记为非激活。</span><span class="sxs-lookup"><span data-stu-id="8ef26-144">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as non-activated.</span></span> <span data-ttu-id="8ef26-145">他们不能发送或接收电子邮件, 也不会使用订阅许可证。</span><span class="sxs-lookup"><span data-stu-id="8ef26-145">They cannot send or receive email, and they don't consume subscription licenses.</span></span> <span data-ttu-id="8ef26-146">当您准备将 Office 365 订阅分配给特定用户时, 您必须通过分配有效的许可证来选择并激活这些订阅。</span><span class="sxs-lookup"><span data-stu-id="8ef26-146">When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by assigning a valid license.</span></span>
  
<span data-ttu-id="8ef26-147">以下特性和功能需要目录同步:</span><span class="sxs-lookup"><span data-stu-id="8ef26-147">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="8ef26-148">SSO</span><span class="sxs-lookup"><span data-stu-id="8ef26-148">SSO</span></span>
- <span data-ttu-id="8ef26-149">Skype 共存</span><span class="sxs-lookup"><span data-stu-id="8ef26-149">Skype coexistence</span></span>
- <span data-ttu-id="8ef26-150">Exchange 混合部署, 包括:</span><span class="sxs-lookup"><span data-stu-id="8ef26-150">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="8ef26-151">内部部署 Exchange 环境与 Office 365 之间的完全共享全局地址列表 (GAL)。</span><span class="sxs-lookup"><span data-stu-id="8ef26-151">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="8ef26-152">同步不同邮件系统中的 GAL 信息。</span><span class="sxs-lookup"><span data-stu-id="8ef26-152">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="8ef26-153">在 Office 365 服务产品中添加和删除用户的功能。</span><span class="sxs-lookup"><span data-stu-id="8ef26-153">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="8ef26-154">这要求：</span><span class="sxs-lookup"><span data-stu-id="8ef26-154">This requires the following:</span></span>
  - <span data-ttu-id="8ef26-155">双向同步必须在目录同步安装过程中进行配置。</span><span class="sxs-lookup"><span data-stu-id="8ef26-155">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="8ef26-156">默认情况下, 目录同步工具仅将目录信息写入云。</span><span class="sxs-lookup"><span data-stu-id="8ef26-156">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="8ef26-157">配置双向同步时, 可启用写回功能, 以便从云中复制有限数量的对象属性, 然后将这些属性重新写入本地 Active Directory 中。</span><span class="sxs-lookup"><span data-stu-id="8ef26-157">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local Active Directory.</span></span> <span data-ttu-id="8ef26-158">写回也称为 Exchange 混合模式。</span><span class="sxs-lookup"><span data-stu-id="8ef26-158">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="8ef26-159">内部部署 Exchange 混合部署</span><span class="sxs-lookup"><span data-stu-id="8ef26-159">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="8ef26-160">能够将一些用户邮箱移动到 Office 365, 同时保留本地用户邮箱。</span><span class="sxs-lookup"><span data-stu-id="8ef26-160">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="8ef26-161">安全发件人和阻止内部的发件人将复制到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="8ef26-161">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="8ef26-162">基本委托和代表发送电子邮件功能。</span><span class="sxs-lookup"><span data-stu-id="8ef26-162">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="8ef26-163">您具有集成的本地智能卡或多重身份验证解决方案。</span><span class="sxs-lookup"><span data-stu-id="8ef26-163">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="8ef26-164">对照片、缩略图、会议室和安全组进行同步</span><span class="sxs-lookup"><span data-stu-id="8ef26-164">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>