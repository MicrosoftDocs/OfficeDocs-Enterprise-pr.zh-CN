---
title: 管理 Microsoft 365 帐户的工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 了解要使用的工具以及如何管理 Microsoft 365 帐户。
ms.openlocfilehash: ffaedb2997a342a4194471c496b41eca054aa301
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606338"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a><span data-ttu-id="0c3f6-103">管理 Microsoft 365 帐户的工具</span><span class="sxs-lookup"><span data-stu-id="0c3f6-103">Tools to manage Microsoft 365 accounts</span></span>

<span data-ttu-id="0c3f6-104">您可以通过几种不同的方式管理 Microsoft 365 用户，具体取决于您的配置。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-104">You can manage Microsoft 365 users in several different ways, depending on your configuration.</span></span> <span data-ttu-id="0c3f6-105">您可以在[Microsoft 365 管理中心](https://admin.microsoft.com)、Windows PowerShell、Active Directory 域服务 (AD DS) 或 Azure Active Directory (azure AD) 管理门户中管理用户。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-105">You can manage users in the [Microsoft 365 admin center](https://admin.microsoft.com), Windows PowerShell, in Active Directory Domain Services (AD DS), or in the Azure Active Directory (Azure AD) admin portal.</span></span> 

<span data-ttu-id="0c3f6-106">一旦购买 Microsoft 365，管理员中心和 Windows PowerShell 便可用于管理帐户。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-106">As soon as you purchase Microsoft 365, the admin center and Windows PowerShell can be used to manage accounts.</span></span> <span data-ttu-id="0c3f6-107">管理云身份时，组织中的每个人都具有单独的用户 ID 和密码（适用于 Microsoft 365）。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-107">When managing cloud identities, every person in your organization has a separate user ID and password for Microsoft 365.</span></span> <span data-ttu-id="0c3f6-108">如果要与您的本地基础结构集成，并让用户帐户与 Microsoft 365 同步，可以使用 Azure AD Connect 为单一登录功能提供标识和密码同步。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-108">If you want to integrate with your on-premises infrastructure and have user accounts synchronized with Microsoft 365, you can use Azure AD Connect to provide synchronization of identities and passwords for single sign-on functionality.</span></span>
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a><span data-ttu-id="0c3f6-109">规划将管理用户帐户的位置和方式</span><span class="sxs-lookup"><span data-stu-id="0c3f6-109">Plan for where and how you will manage your user accounts</span></span>

<span data-ttu-id="0c3f6-110">如何管理用户帐户的位置和方式取决于要用于 Microsoft 365 的标识模型。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-110">Where and how you can manage your user accounts depends on the identity model you want to use for your Microsoft 365.</span></span> <span data-ttu-id="0c3f6-111">这两个整体模型是云身份验证和联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-111">The two overall models are cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="0c3f6-112">云身份验证</span><span class="sxs-lookup"><span data-stu-id="0c3f6-112">Cloud authentication</span></span>

- <span data-ttu-id="0c3f6-113">云身份验证-在 Microsoft 365 管理中心中创建和管理用户。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-113">Cloud authentication - Create and manage users in the Microsoft 365 admin center.</span></span> <span data-ttu-id="0c3f6-114">您还可以使用 Windows PowerShell 或 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-114">You can also use Windows PowerShell or Azure AD .</span></span> 
    
- <span data-ttu-id="0c3f6-115">使用无缝单一登录 (PHS) 的密码哈希同步-为 Azure AD 中的 AD DS 对象启用身份验证的最简单方法。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-115">Password hash sync (PHS) with seamless single sign-on - The simplest way to enable authentication for AD DS objects in Azure AD.</span></span> <span data-ttu-id="0c3f6-116">使用 PHS，您可以将 AD DS 用户帐户对象与 Microsoft 365 同步并在本地管理您的用户。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-116">With PHS, you synchronize your AD DS user account objects with Microsoft 365 and manage your users on-premises.</span></span> 
    
- <span data-ttu-id="0c3f6-117">传递身份验证 (PTA) 带有无缝的单一登录-提供了使用在一个或多个本地服务器上运行的软件代理直接使用您的 AD DS 验证用户的 Azure AD 身份验证服务的简单密码验证。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-117">Pass-through authentication (PTA) with seamless single sign-on - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> 
    
### <a name="federated-authentication"></a><span data-ttu-id="0c3f6-118">联合身份验证</span><span class="sxs-lookup"><span data-stu-id="0c3f6-118">Federated authentication</span></span>

- <span data-ttu-id="0c3f6-119">联合身份验证选项-主要针对具有更复杂的身份验证要求的大型企业组织，AD DS 对象与 Microsoft 365 同步，并且用户帐户在本地进行管理。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-119">Federated authentication options - Primarily for large enterprise organizations with more complex authentication requirements, AD DS objects are synchronized with Microsoft 365 and users accounts are managed on-premises.</span></span> 
    
- <span data-ttu-id="0c3f6-120">[第三方身份验证和标识提供程序](about-office-365-identity.md)-AD DS 对象可能会同步到 Microsoft 365，云资源访问主要由第三方标识提供程序 (IDP) 进行管理。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-120">[Third-party authentication and identity providers](about-office-365-identity.md) - AD DS objects may be synchronized to Microsoft 365 and cloud resource access is primarily managed by a third-party identity provider (IDP).</span></span> 
    
## <a name="managing-accounts"></a><span data-ttu-id="0c3f6-121">管理帐户</span><span class="sxs-lookup"><span data-stu-id="0c3f6-121">Managing Accounts</span></span>

<span data-ttu-id="0c3f6-122">在决定您的组织创建和管理帐户的方式时，请考虑以下要求：</span><span class="sxs-lookup"><span data-stu-id="0c3f6-122">When deciding which way your organization will create and manage accounts, consider the following requirements:</span></span>
  
- <span data-ttu-id="0c3f6-123">目录同步软件需要安装在本地环境中的服务器上，以连接 Microsoft 365 和 AD DS 之间的标识。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-123">The directory synchronization software needs to be installed on servers within your on-premises environment to connect the identities between Microsoft 365 and your AD DS.</span></span>
    
- <span data-ttu-id="0c3f6-124">任何目录同步选项（包括 SSO 选项）都需要 AD DS 属性满足标准。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-124">Any directory synchronization option, including SSO options, requires your AD DS attributes meet standards.</span></span> <span data-ttu-id="0c3f6-125">在目录中使用哪些属性以及哪些清除 (（如果需要任何) ）的说明在[准备通过目录同步将用户预配到 Microsoft 365](prepare-for-directory-synchronization.md)时，将对其进行说明。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-125">The specifics of what attributes are used in your directory and what cleanup (if any) is needed are described in [Prepare to provision users through directory synchronization to Microsoft 365](prepare-for-directory-synchronization.md).</span></span> 
    
- <span data-ttu-id="0c3f6-126">规划如何创建 Microsoft 365 帐户。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-126">Plan how you are going to create Microsoft 365 accounts.</span></span>
    
    <span data-ttu-id="0c3f6-127">下表列出了不同的帐户管理工具。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-127">The following table lists the different account management tools.</span></span>
    
|<span data-ttu-id="0c3f6-128">**选项**</span><span class="sxs-lookup"><span data-stu-id="0c3f6-128">**Option**</span></span>|<span data-ttu-id="0c3f6-129">**注意**</span><span class="sxs-lookup"><span data-stu-id="0c3f6-129">**Notes**</span></span>|
|:-----|:-----|
|<span data-ttu-id="0c3f6-130">管理中心</span><span class="sxs-lookup"><span data-stu-id="0c3f6-130">Admin center</span></span>  <br/> |[<span data-ttu-id="0c3f6-131">单独或批量添加用户</span><span class="sxs-lookup"><span data-stu-id="0c3f6-131">Add users individually or in bulk</span></span>](https://docs.microsoft.com/microsoft-365/admin/add-users/add-users) <br/>  <span data-ttu-id="0c3f6-132">提供一个简单的 web 界面来添加和更改用户帐户。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-132">Provides a simple web interface to add and change user accounts.</span></span>  <br/>  <span data-ttu-id="0c3f6-133">如果启用了目录同步，则无法用于更改用户 (位置和许可证分配可以设置) 。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-133">Can't be used to change users if directory synchronization is enabled (location and license assignment can be set).</span></span>  <br/>  <span data-ttu-id="0c3f6-134">不能与 SSO 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-134">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="0c3f6-135">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c3f6-135">Windows PowerShell</span></span>  <br/> |[<span data-ttu-id="0c3f6-136">使用 Windows PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="0c3f6-136">Manage Microsoft 365 with Windows PowerShell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  <span data-ttu-id="0c3f6-137">允许您使用 Windows PowerShell 脚本在批量用户中添加用户。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-137">Allows you to add users in bulk users by using a Windows PowerShell script.</span></span>  <br/>  <span data-ttu-id="0c3f6-138">可用于将位置和许可证分配给帐户，而不考虑帐户的创建方式。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-138">Can be used to assign location and licenses to accounts, regardless of how the accounts are created.</span></span>  <br/> |
|<span data-ttu-id="0c3f6-139">批量导入</span><span class="sxs-lookup"><span data-stu-id="0c3f6-139">Bulk import</span></span>  <br/> |[<span data-ttu-id="0c3f6-140">同时添加多个用户</span><span class="sxs-lookup"><span data-stu-id="0c3f6-140">Add several users at the same time</span></span>](add-several-users-at-the-same-time.md) <br/>  <span data-ttu-id="0c3f6-141">允许您导入 CSV 文件以将一组用户添加到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-141">Allows you to import a CSV file to add a group of users to Microsoft 365.</span></span>  <br/>  <span data-ttu-id="0c3f6-142">不能与 SSO 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-142">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="0c3f6-143">Azure AD</span><span class="sxs-lookup"><span data-stu-id="0c3f6-143">Azure AD</span></span>  <br/> |<span data-ttu-id="0c3f6-144">你可以使用 Microsoft 365 订阅获取 Azure AD 的免费版本。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-144">You get a free edition of Azure AD with your Microsoft 365 subscription.</span></span> <span data-ttu-id="0c3f6-145">您可以为云用户执行自助密码重置等功能，并使用免费版本自定义登录和访问面板页。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-145">You can perform functions like self-service password reset for cloud users, and customization of the Sign-in and Access Panel pages by using the free edition.</span></span> <span data-ttu-id="0c3f6-146">若要获取增强的功能，您可以升级到基本版本、Azure AD 高级 P1 或 Azure AD Premium P2。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-146">To get enhanced functionality, you can upgrade to the basic edition, Azure AD Premium P1, or Azure AD Premium P2.</span></span> <span data-ttu-id="0c3f6-147">有关支持的功能的列表，请参阅[AZURE AD 版本](https://go.microsoft.com/fwlink/p/?LinkId=698465)。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-147">See [Azure AD editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) for the list of supported features.</span></span>  <br/> |
|<span data-ttu-id="0c3f6-148">目录同步</span><span class="sxs-lookup"><span data-stu-id="0c3f6-148">Directory synchronization</span></span>  <br/> |[<span data-ttu-id="0c3f6-149">将本地标识与 Azure AD 集成</span><span class="sxs-lookup"><span data-stu-id="0c3f6-149">Integrating your on-premises identities with Azure AD</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  <span data-ttu-id="0c3f6-150">对于使用或不使用密码同步进行目录同步，请将[AZURE AD Connect 与 express 设置结合](https://go.microsoft.com/fwlink/p/?LinkID=698537)使用。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-150">For directory synchronization with or without password synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>  <br/>  <span data-ttu-id="0c3f6-151">对于多个林和 SSO 选项，请使用[自定义安装的 AZURE AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-151">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>  <br/>  <span data-ttu-id="0c3f6-152">提供启用 SSO 所需的基础结构。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-152">Provides the infrastructure that's necessary to enable SSO.</span></span>  <br/>  <span data-ttu-id="0c3f6-153">对于很多混合方案是必需的：</span><span class="sxs-lookup"><span data-stu-id="0c3f6-153">Required for many hybrid scenarios:</span></span>  <br/>  <span data-ttu-id="0c3f6-154">暂存迁移</span><span class="sxs-lookup"><span data-stu-id="0c3f6-154">Staged migration</span></span>  <br/>  <span data-ttu-id="0c3f6-155">混合 Exchange</span><span class="sxs-lookup"><span data-stu-id="0c3f6-155">Hybrid Exchange</span></span>  <br/>  <span data-ttu-id="0c3f6-156">从 AD DS 同步安全和启用邮件的组。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-156">Synchronizes security and mail-enabled groups from your AD DS.</span></span>  <br/> |
   
- <span data-ttu-id="0c3f6-157">无论您打算如何将用户帐户添加到 Microsoft 365，您都需要管理多个帐户功能，例如分配许可证、指定位置等。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-157">Regardless of how you intend to add the user accounts to Microsoft 365, you need to manage several account features, such as assigning licenses, specifying location, and so on.</span></span> <span data-ttu-id="0c3f6-158">可以从管理中心管理这些功能，也可以[使用 PowerShell 创建用户帐户](https://go.microsoft.com/fwlink/p/?LinkId=717083)。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-158">These features can be managed long-term from the admin center or you can also [create user accounts with PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).</span></span>
    
    <span data-ttu-id="0c3f6-159">如果选择通过管理中心添加和管理所有用户，您将指定位置，并在创建 Microsoft 365 帐户的同时分配许可证。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-159">If you choose to add and manage all your users through the admin center, you will specify the location and assign licenses at the same time as creating the Microsoft 365 account.</span></span> <span data-ttu-id="0c3f6-160">因此，不需要进行大量规划。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-160">As a result, not much planning is required.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="0c3f6-161">在 Microsoft 365 中创建帐户，而不向 SharePoint Online 分配许可证 (，例如) 意味着帐户所有者可以查看 Microsoft 365 中心，但不能访问公司订阅中的任何服务。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-161">Creating accounts in Microsoft 365 without assigning a license (to SharePoint Online, for example) means that the account owner can view the Microsoft 365 center but can't access any of the services within your company's subscription.</span></span> <span data-ttu-id="0c3f6-162">分配位置和许可证后，帐户将复制到您分配的服务或服务。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-162">After you assign a location and the license, the account is replicated to the service or services that you assigned.</span></span> <span data-ttu-id="0c3f6-163">用户可以登录到其帐户并使用您分配给他们的服务。</span><span class="sxs-lookup"><span data-stu-id="0c3f6-163">The user can sign in to their account and use the services that you assigned to them.</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="0c3f6-164">后续步骤</span><span class="sxs-lookup"><span data-stu-id="0c3f6-164">Next steps</span></span>

[<span data-ttu-id="0c3f6-165">Microsoft 365 与本地环境的集成</span><span class="sxs-lookup"><span data-stu-id="0c3f6-165">Microsoft 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
## <a name="see-also"></a><span data-ttu-id="0c3f6-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c3f6-166">See Also</span></span>

[<span data-ttu-id="0c3f6-167">在 Microsoft 365 中管理用户和组</span><span class="sxs-lookup"><span data-stu-id="0c3f6-167">Manage users and groups in Microsoft 365</span></span>](https://docs.microsoft.com/microsoft-365/admin/add-users)
  
