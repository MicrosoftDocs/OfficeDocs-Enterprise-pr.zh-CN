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
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: '了解用于管理 Microsoft 365 用户的工具。 '
ms.openlocfilehash: 324a95e111812180cefffe98f2d7ec3c64e956b1
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230228"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a><span data-ttu-id="6eb25-103">管理 Microsoft 365 帐户的工具</span><span class="sxs-lookup"><span data-stu-id="6eb25-103">Tools to manage Microsoft 365 accounts</span></span>

<span data-ttu-id="6eb25-104">您可以通过几种不同的方式管理 Microsoft 365 用户，具体取决于您的配置。</span><span class="sxs-lookup"><span data-stu-id="6eb25-104">You can manage Microsoft 365 users in several different ways, depending on your configuration.</span></span> <span data-ttu-id="6eb25-105">你可以在[Microsoft 365 管理中心](https://admin.microsoft.com)、Windows PowerShell、Active Directory 域服务（AD DS）或 Azure Active Directory （azure ad）管理门户中管理用户。</span><span class="sxs-lookup"><span data-stu-id="6eb25-105">You can manage users in the [Microsoft 365 admin center](https://admin.microsoft.com), Windows PowerShell, in Active Directory Domain Services (AD DS), or in the Azure Active Directory (Azure AD) admin portal.</span></span> 

<span data-ttu-id="6eb25-106">一旦购买 Microsoft 365，管理员中心和 Windows PowerShell 便可用于管理帐户。</span><span class="sxs-lookup"><span data-stu-id="6eb25-106">As soon as you purchase Microsoft 365, the admin center and Windows PowerShell can be used to manage accounts.</span></span> <span data-ttu-id="6eb25-107">管理云身份时，组织中的每个人都具有单独的用户 ID 和密码（适用于 Microsoft 365）。</span><span class="sxs-lookup"><span data-stu-id="6eb25-107">When managing cloud identities, every person in your organization has a separate user ID and password for Microsoft 365.</span></span> <span data-ttu-id="6eb25-108">如果要与您的本地基础结构集成，并让用户帐户与 Microsoft 365 同步，可以使用 Azure AD Connect 为单一登录功能提供标识和密码同步。</span><span class="sxs-lookup"><span data-stu-id="6eb25-108">If you want to integrate with your on-premises infrastructure and have user accounts synchronized with Microsoft 365, you can use Azure AD Connect to provide synchronization of identities and passwords for single sign-on functionality.</span></span>
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a><span data-ttu-id="6eb25-109">规划将管理用户帐户的位置和方式</span><span class="sxs-lookup"><span data-stu-id="6eb25-109">Plan for where and how you will manage your user accounts</span></span>

<span data-ttu-id="6eb25-110">如何管理用户帐户的位置和方式取决于要用于 Microsoft 365 的标识模型。</span><span class="sxs-lookup"><span data-stu-id="6eb25-110">Where and how you can manage your user accounts depends on the identity model you want to use for your Microsoft 365.</span></span> <span data-ttu-id="6eb25-111">这两个整体模型是云身份验证和联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="6eb25-111">The two overall models are cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="6eb25-112">云身份验证</span><span class="sxs-lookup"><span data-stu-id="6eb25-112">Cloud authentication</span></span>

- <span data-ttu-id="6eb25-113">云身份验证-在 Microsoft 365 管理中心中创建和管理用户。</span><span class="sxs-lookup"><span data-stu-id="6eb25-113">Cloud authentication - Create and manage users in the Microsoft 365 admin center.</span></span> <span data-ttu-id="6eb25-114">您还可以使用 Windows PowerShell 或 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="6eb25-114">You can also use Windows PowerShell or Azure AD .</span></span> 
    
- <span data-ttu-id="6eb25-115">带有无缝单一登录的密码哈希同步（PHS）-为 Azure AD 中的 AD DS 对象启用身份验证的最简单方法。</span><span class="sxs-lookup"><span data-stu-id="6eb25-115">Password hash sync (PHS) with seamless single sign-on - The simplest way to enable authentication for AD DS objects in Azure AD.</span></span> <span data-ttu-id="6eb25-116">使用 PHS，您可以将 AD DS 用户帐户对象与 Microsoft 365 同步并在本地管理您的用户。</span><span class="sxs-lookup"><span data-stu-id="6eb25-116">With PHS, you synchronize your AD DS user account objects with Microsoft 365 and manage your users on-premises.</span></span> 
    
- <span data-ttu-id="6eb25-117">带有无缝单一登录的传递身份验证（PTA）-使用在一个或多个本地服务器上运行的软件代理在 Azure AD 身份验证服务中运行一个简单的密码验证，以通过 AD DS 直接验证用户。</span><span class="sxs-lookup"><span data-stu-id="6eb25-117">Pass-through authentication (PTA) with seamless single sign-on - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> 
    
### <a name="federated-authentication"></a><span data-ttu-id="6eb25-118">联合身份验证</span><span class="sxs-lookup"><span data-stu-id="6eb25-118">Federated authentication</span></span>

- <span data-ttu-id="6eb25-119">联合身份验证选项-主要针对具有更复杂的身份验证要求的大型企业组织，AD DS 对象与 Microsoft 365 同步，并且用户帐户在本地进行管理。</span><span class="sxs-lookup"><span data-stu-id="6eb25-119">Federated authentication options - Primarily for large enterprise organizations with more complex authentication requirements, AD DS objects are synchronized with Microsoft 365 and users accounts are managed on-premises.</span></span> 
    
- <span data-ttu-id="6eb25-120">[第三方身份验证和标识提供程序](about-office-365-identity.md)-AD DS 对象可能会同步到 Microsoft 365，并且云资源访问主要由第三方标识提供程序（IDP）进行管理。</span><span class="sxs-lookup"><span data-stu-id="6eb25-120">[Third-party authentication and identity providers](about-office-365-identity.md) - AD DS objects may be synchronized to Microsoft 365 and cloud resource access is primarily managed by a third-party identity provider (IDP).</span></span> 
    
## <a name="managing-accounts"></a><span data-ttu-id="6eb25-121">管理帐户</span><span class="sxs-lookup"><span data-stu-id="6eb25-121">Managing Accounts</span></span>

<span data-ttu-id="6eb25-122">在决定您的组织创建和管理帐户的方式时，请考虑以下要求：</span><span class="sxs-lookup"><span data-stu-id="6eb25-122">When deciding which way your organization will create and manage accounts, consider the following requirements:</span></span>
  
- <span data-ttu-id="6eb25-123">目录同步软件需要安装在本地环境中的服务器上，以连接 Microsoft 365 和 AD DS 之间的标识。</span><span class="sxs-lookup"><span data-stu-id="6eb25-123">The directory synchronization software needs to be installed on servers within your on-premises environment to connect the identities between Microsoft 365 and your AD DS.</span></span>
    
- <span data-ttu-id="6eb25-124">任何目录同步选项（包括 SSO 选项）都需要 AD DS 属性满足标准。</span><span class="sxs-lookup"><span data-stu-id="6eb25-124">Any directory synchronization option, including SSO options, requires your AD DS attributes meet standards.</span></span> <span data-ttu-id="6eb25-125">在目录中使用哪些属性以及需要清除的内容（如果有）的具体说明，[准备通过目录同步将用户预配到 Microsoft 365](prepare-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb25-125">The specifics of what attributes are used in your directory and what cleanup (if any) is needed are described in [Prepare to provision users through directory synchronization to Microsoft 365](prepare-for-directory-synchronization.md).</span></span> <span data-ttu-id="6eb25-126">有关如何使用 Id 修复来自动执行目录清理的说明，请参阅[下载并运行 Microsoft 365 Id 修补工具](install-and-run-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb25-126">See [Download and run the Microsoft 365 Id Fix tool](install-and-run-idfix.md) for instruction on how to use Id Fix to automate directory cleanup.</span></span> 
    
- <span data-ttu-id="6eb25-127">规划如何创建 Microsoft 365 帐户。</span><span class="sxs-lookup"><span data-stu-id="6eb25-127">Plan how you are going to create Microsoft 365 accounts.</span></span>
    
    <span data-ttu-id="6eb25-128">下表列出了不同的帐户管理工具。</span><span class="sxs-lookup"><span data-stu-id="6eb25-128">The following table lists the different account management tools.</span></span>
    
|<span data-ttu-id="6eb25-129">**选项**</span><span class="sxs-lookup"><span data-stu-id="6eb25-129">**Option**</span></span>|<span data-ttu-id="6eb25-130">**备注**</span><span class="sxs-lookup"><span data-stu-id="6eb25-130">**Notes**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6eb25-131">管理中心</span><span class="sxs-lookup"><span data-stu-id="6eb25-131">Admin center</span></span>  <br/> |[<span data-ttu-id="6eb25-132">单独或批量添加用户</span><span class="sxs-lookup"><span data-stu-id="6eb25-132">Add users individually or in bulk</span></span>](https://docs.microsoft.com/microsoft-365/admin/add-users/add-users) <br/>  <span data-ttu-id="6eb25-133">提供一个简单的 web 界面来添加和更改用户帐户。</span><span class="sxs-lookup"><span data-stu-id="6eb25-133">Provides a simple web interface to add and change user accounts.</span></span>  <br/>  <span data-ttu-id="6eb25-134">如果启用目录同步（可以设置位置和许可证分配），则不能使用更改用户。</span><span class="sxs-lookup"><span data-stu-id="6eb25-134">Can't be used to change users if directory synchronization is enabled (location and license assignment can be set).</span></span>  <br/>  <span data-ttu-id="6eb25-135">不能与 SSO 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="6eb25-135">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="6eb25-136">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6eb25-136">Windows PowerShell</span></span>  <br/> |[<span data-ttu-id="6eb25-137">使用 Windows PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="6eb25-137">Manage Microsoft 365 with Windows PowerShell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  <span data-ttu-id="6eb25-138">允许您使用 Windows PowerShell 脚本在批量用户中添加用户。</span><span class="sxs-lookup"><span data-stu-id="6eb25-138">Allows you to add users in bulk users by using a Windows PowerShell script.</span></span>  <br/>  <span data-ttu-id="6eb25-139">可用于将位置和许可证分配给帐户，而不考虑帐户的创建方式。</span><span class="sxs-lookup"><span data-stu-id="6eb25-139">Can be used to assign location and licenses to accounts, regardless of how the accounts are created.</span></span>  <br/> |
|<span data-ttu-id="6eb25-140">批量导入</span><span class="sxs-lookup"><span data-stu-id="6eb25-140">Bulk import</span></span>  <br/> |[<span data-ttu-id="6eb25-141">同时添加多个用户</span><span class="sxs-lookup"><span data-stu-id="6eb25-141">Add several users at the same time</span></span>](add-several-users-at-the-same-time.md) <br/>  <span data-ttu-id="6eb25-142">允许您导入 CSV 文件以将一组用户添加到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="6eb25-142">Allows you to import a CSV file to add a group of users to Microsoft 365.</span></span>  <br/>  <span data-ttu-id="6eb25-143">不能与 SSO 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="6eb25-143">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="6eb25-144">Azure AD</span><span class="sxs-lookup"><span data-stu-id="6eb25-144">Azure AD</span></span>  <br/> |<span data-ttu-id="6eb25-145">你可以使用 Microsoft 365 订阅获取 Azure AD 的免费版本。</span><span class="sxs-lookup"><span data-stu-id="6eb25-145">You get a free edition of Azure AD with your Microsoft 365 subscription.</span></span> <span data-ttu-id="6eb25-146">您可以为云用户执行自助密码重置等功能，并使用免费版本自定义登录和访问面板页。</span><span class="sxs-lookup"><span data-stu-id="6eb25-146">You can perform functions like self-service password reset for cloud users, and customization of the Sign-in and Access Panel pages by using the free edition.</span></span> <span data-ttu-id="6eb25-147">若要获取增强的功能，您可以升级到基本版本、Azure AD 高级 P1 或 Azure AD Premium P2。</span><span class="sxs-lookup"><span data-stu-id="6eb25-147">To get enhanced functionality, you can upgrade to the basic edition, Azure AD Premium P1, or Azure AD Premium P2.</span></span> <span data-ttu-id="6eb25-148">有关支持的功能的列表，请参阅[AZURE AD 版本](https://go.microsoft.com/fwlink/p/?LinkId=698465)。</span><span class="sxs-lookup"><span data-stu-id="6eb25-148">See [Azure AD editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) for the list of supported features.</span></span>  <br/> |
|<span data-ttu-id="6eb25-149">目录同步</span><span class="sxs-lookup"><span data-stu-id="6eb25-149">Directory synchronization</span></span>  <br/> |[<span data-ttu-id="6eb25-150">将本地标识与 Azure AD 集成</span><span class="sxs-lookup"><span data-stu-id="6eb25-150">Integrating your on-premises identities with Azure AD</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  <span data-ttu-id="6eb25-151">对于使用或不使用密码同步进行目录同步，请将[AZURE AD Connect 与 express 设置结合](https://go.microsoft.com/fwlink/p/?LinkID=698537)使用。</span><span class="sxs-lookup"><span data-stu-id="6eb25-151">For directory synchronization with or without password synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>  <br/>  <span data-ttu-id="6eb25-152">对于多个林和 SSO 选项，请使用[自定义安装的 AZURE AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="6eb25-152">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>  <br/>  <span data-ttu-id="6eb25-153">提供启用 SSO 所需的基础结构。</span><span class="sxs-lookup"><span data-stu-id="6eb25-153">Provides the infrastructure that's necessary to enable SSO.</span></span>  <br/>  <span data-ttu-id="6eb25-154">对于很多混合方案是必需的：</span><span class="sxs-lookup"><span data-stu-id="6eb25-154">Required for many hybrid scenarios:</span></span>  <br/>  <span data-ttu-id="6eb25-155">暂存迁移</span><span class="sxs-lookup"><span data-stu-id="6eb25-155">Staged migration</span></span>  <br/>  <span data-ttu-id="6eb25-156">混合 Exchange</span><span class="sxs-lookup"><span data-stu-id="6eb25-156">Hybrid Exchange</span></span>  <br/>  <span data-ttu-id="6eb25-157">从 AD DS 同步安全和启用邮件的组。</span><span class="sxs-lookup"><span data-stu-id="6eb25-157">Synchronizes security and mail-enabled groups from your AD DS.</span></span>  <br/> |
   
- <span data-ttu-id="6eb25-158">无论您打算如何将用户帐户添加到 Microsoft 365，您都需要管理多个帐户功能，例如分配许可证、指定位置等。</span><span class="sxs-lookup"><span data-stu-id="6eb25-158">Regardless of how you intend to add the user accounts to Microsoft 365, you need to manage several account features, such as assigning licenses, specifying location, and so on.</span></span> <span data-ttu-id="6eb25-159">可以从管理中心管理这些功能，也可以[使用 PowerShell 创建用户帐户](https://go.microsoft.com/fwlink/p/?LinkId=717083)。</span><span class="sxs-lookup"><span data-stu-id="6eb25-159">These features can be managed long-term from the admin center or you can also [create user accounts with PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).</span></span>
    
    <span data-ttu-id="6eb25-160">如果选择通过管理中心添加和管理所有用户，您将指定位置，并在创建 Microsoft 365 帐户的同时分配许可证。</span><span class="sxs-lookup"><span data-stu-id="6eb25-160">If you choose to add and manage all your users through the admin center, you will specify the location and assign licenses at the same time as creating the Microsoft 365 account.</span></span> <span data-ttu-id="6eb25-161">因此，不需要进行大量规划。</span><span class="sxs-lookup"><span data-stu-id="6eb25-161">As a result, not much planning is required.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="6eb25-162">在 Microsoft 365 中创建帐户而不分配许可证（例如为 SharePoint Online）意味着帐户所有者可以查看 Microsoft 365 管理中心，但不能访问公司订阅中的任何服务。</span><span class="sxs-lookup"><span data-stu-id="6eb25-162">Creating accounts in Microsoft 365 without assigning a license (to SharePoint Online, for example) means that the account owner can view the Microsoft 365 admin center but can't access any of the services within your company's subscription.</span></span> <span data-ttu-id="6eb25-163">分配位置和许可证后，帐户将复制到您分配的服务或服务。</span><span class="sxs-lookup"><span data-stu-id="6eb25-163">After you assign a location and the license, the account is replicated to the service or services that you assigned.</span></span> <span data-ttu-id="6eb25-164">用户可以登录到其帐户并使用您分配给他们的服务。</span><span class="sxs-lookup"><span data-stu-id="6eb25-164">The user can sign in to their account and use the services that you assigned to them.</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="6eb25-165">后续步骤</span><span class="sxs-lookup"><span data-stu-id="6eb25-165">Next steps</span></span>

[<span data-ttu-id="6eb25-166">Microsoft 365 与本地环境的集成</span><span class="sxs-lookup"><span data-stu-id="6eb25-166">Microsoft 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
## <a name="see-also"></a><span data-ttu-id="6eb25-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6eb25-167">See Also</span></span>

[<span data-ttu-id="6eb25-168">在 Microsoft 365 中管理用户和组</span><span class="sxs-lookup"><span data-stu-id="6eb25-168">Manage users and groups in Microsoft 365</span></span>](https://docs.microsoft.com/microsoft-365/admin/add-users)
  

