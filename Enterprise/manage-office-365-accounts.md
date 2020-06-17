---
title: 用于管理 Office 365 帐户的工具
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
description: '了解用于管理 Office 365 用户的工具，以及您可以使用的工具取决于管理用户身份的方式。 '
ms.openlocfilehash: 90e79eaf9cd90a539cf1c454509bff7d659b8b35
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735780"
---
# <a name="tools-to-manage-office-365-accounts"></a><span data-ttu-id="442c2-103">用于管理 Office 365 帐户的工具</span><span class="sxs-lookup"><span data-stu-id="442c2-103">Tools to manage Office 365 accounts</span></span>

<span data-ttu-id="442c2-104">您可以通过几种不同的方式管理 Office 365 用户，具体取决于您的配置。</span><span class="sxs-lookup"><span data-stu-id="442c2-104">You can manage Office 365 users in several different ways, depending on your configuration.</span></span> <span data-ttu-id="442c2-105">你可以在[Microsoft 365 管理中心](https://admin.microsoft.com)、Windows PowerShell、本地目录或 Azure Active directory 管理门户中管理用户。</span><span class="sxs-lookup"><span data-stu-id="442c2-105">You can manage users in the [Microsoft 365 admin center](https://admin.microsoft.com), Windows PowerShell, your on-premises directory, or in Azure Active Directory admin portal.</span></span> <span data-ttu-id="442c2-106">在购买 Office 365 后，可以立即使用管理中心和 Windows PowerShell 来管理帐户。</span><span class="sxs-lookup"><span data-stu-id="442c2-106">As soon as you purchase Office 365, the admin center and Windows PowerShell can be used to manage accounts.</span></span> <span data-ttu-id="442c2-107">管理云标识组织中的每个人都有单独的用户 ID 和密码（适用于 Office 365）。</span><span class="sxs-lookup"><span data-stu-id="442c2-107">When managing cloud identities every person in your organization has a separate user ID and password for Office 365.</span></span> <span data-ttu-id="442c2-108">如果要与您的本地基础结构集成并将用户帐户与 Office 365 同步，可以使用 Azure Active Directory Connect 来提供标识同步，以及提供密码同步（可选）或完整的单一登录功能。</span><span class="sxs-lookup"><span data-stu-id="442c2-108">If you want to integrate with your on-premises infrastructure and have user accounts synchronized with Office 365, you can use Azure Active Directory Connect to provide synchronization of identities and optionally provide password synchronization, or full single sign-on functionality.</span></span>
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a><span data-ttu-id="442c2-109">规划将管理用户帐户的位置和方式</span><span class="sxs-lookup"><span data-stu-id="442c2-109">Plan for where and how you will manage your user accounts</span></span>

<span data-ttu-id="442c2-110">如何管理用户帐户的位置和方式取决于您要用于 Office 365 的标识模型。</span><span class="sxs-lookup"><span data-stu-id="442c2-110">Where and how you can manage your user accounts depends on the identity model you want to use for your Office 365.</span></span> <span data-ttu-id="442c2-111">这两个整体模型是云身份验证和联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="442c2-111">The two overall models are cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="442c2-112">云身份验证</span><span class="sxs-lookup"><span data-stu-id="442c2-112">Cloud authentication</span></span>

- <span data-ttu-id="442c2-113">云身份验证-创建和管理用户在管理中心中，您还可以使用 Windows PowerShell 或 Azure Active Directory 管理用户。</span><span class="sxs-lookup"><span data-stu-id="442c2-113">Cloud authentication - create and manage users in the admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span> 
    
- <span data-ttu-id="442c2-114">带有无缝单一登录的密码哈希同步-为 Azure AD 中的本地目录对象启用身份验证的最简单方法。</span><span class="sxs-lookup"><span data-stu-id="442c2-114">Password hash sync with seamless single sign-on - The simplest way to enable authentication for on-premises directory objects in Azure AD.</span></span> <span data-ttu-id="442c2-115">使用密码哈希同步（PHS），您可以将内部部署 Active Directory 用户帐户对象与 Office 365 同步并在本地管理您的用户。</span><span class="sxs-lookup"><span data-stu-id="442c2-115">With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span> 
    
- <span data-ttu-id="442c2-116">带有无缝单一登录的传递身份验证-使用在一个或多个本地服务器上运行的软件代理，为 Azure AD 身份验证服务提供简单的密码验证，以直接使用本地 Active Directory 验证用户。</span><span class="sxs-lookup"><span data-stu-id="442c2-116">Pass-through authentication with seamless single sign-on - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span> 
    
### <a name="federated-authentication"></a><span data-ttu-id="442c2-117">联合身份验证</span><span class="sxs-lookup"><span data-stu-id="442c2-117">Federated authentication</span></span>

- <span data-ttu-id="442c2-118">联合身份验证选项-主要针对具有更复杂的身份验证要求的大型企业组织，本地目录对象与 Office 365 同步，并且用户帐户在本地进行管理。</span><span class="sxs-lookup"><span data-stu-id="442c2-118">Federated authentication options - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span> 
    
- <span data-ttu-id="442c2-119">[第三方身份验证和标识提供程序](about-office-365-identity.md)-内部部署目录对象可能会同步到 Office 365，并且云资源访问主要由第三方标识提供程序（IdP）进行管理。</span><span class="sxs-lookup"><span data-stu-id="442c2-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> 
    
## <a name="managing-accounts"></a><span data-ttu-id="442c2-120">管理帐户</span><span class="sxs-lookup"><span data-stu-id="442c2-120">Managing Accounts</span></span>

<span data-ttu-id="442c2-121">在决定您的组织创建和管理帐户的方式时，请考虑以下事项：</span><span class="sxs-lookup"><span data-stu-id="442c2-121">When deciding which way your organization will create and manage accounts, consider the following:</span></span>
  
- <span data-ttu-id="442c2-122">目录同步软件需要安装在本地环境中的服务器上，以连接 Office 365 和本地目录之间的标识。</span><span class="sxs-lookup"><span data-stu-id="442c2-122">The directory synchronization software needs to be installed on servers within your on-premises environment to connect the identities between Office 365 and your on-premises directory.</span></span>
    
- <span data-ttu-id="442c2-123">任何目录同步选项（包括 SSO 选项）都需要您的本地目录属性满足标准。</span><span class="sxs-lookup"><span data-stu-id="442c2-123">Any directory synchronization option, including SSO options, requires your on-premises directory attributes meet standards.</span></span> <span data-ttu-id="442c2-124">在目录中使用哪些属性以及需要清除的内容（如果有）的具体说明，[准备通过目录同步将用户预配到 Office 365](prepare-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="442c2-124">The specifics of what attributes are used in your directory and what cleanup (if any) is needed are described in [Prepare to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md).</span></span> <span data-ttu-id="442c2-125">有关如何使用 IdFix 自动执行目录清理的说明，请参阅[下载并运行 Office 365 IdFix 工具](install-and-run-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="442c2-125">See [Download and run the Office 365 IdFix tool](install-and-run-idfix.md) for instruction on how to use IdFix to automate directory cleanup.</span></span> 
    
- <span data-ttu-id="442c2-126">规划如何创建 Office 365 帐户。</span><span class="sxs-lookup"><span data-stu-id="442c2-126">Plan how you are going to create Office 365 accounts.</span></span>
    
    <span data-ttu-id="442c2-127">下表列出了不同的帐户管理工具。</span><span class="sxs-lookup"><span data-stu-id="442c2-127">The following table lists the different account management tools.</span></span>
    
|<span data-ttu-id="442c2-128">**选项**</span><span class="sxs-lookup"><span data-stu-id="442c2-128">**Option**</span></span>|<span data-ttu-id="442c2-129">**备注**</span><span class="sxs-lookup"><span data-stu-id="442c2-129">**Notes**</span></span>|
|:-----|:-----|
|<span data-ttu-id="442c2-130">管理中心</span><span class="sxs-lookup"><span data-stu-id="442c2-130">Admin center</span></span>  <br/> |[<span data-ttu-id="442c2-131">将用户逐个或批量添加到 Office 365-管理员帮助</span><span class="sxs-lookup"><span data-stu-id="442c2-131">Add users individually or in bulk to Office 365 - Admin Help</span></span>](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  <span data-ttu-id="442c2-132">提供一个简单的 web 界面来添加和更改用户帐户。</span><span class="sxs-lookup"><span data-stu-id="442c2-132">Provides a simple web interface to add and change user accounts.</span></span>  <br/>  <span data-ttu-id="442c2-133">如果启用目录同步（可以设置位置和许可证分配），则不能使用更改用户。</span><span class="sxs-lookup"><span data-stu-id="442c2-133">Can't be used to change users if directory synchronization is enabled (location and license assignment can be set).</span></span>  <br/>  <span data-ttu-id="442c2-134">不能与 SSO 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="442c2-134">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="442c2-135">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="442c2-135">Windows PowerShell</span></span>  <br/> |[<span data-ttu-id="442c2-136">使用 Windows PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="442c2-136">Manage Office 365 with Windows PowerShell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  <span data-ttu-id="442c2-137">允许您使用 Windows PowerShell 脚本在批量用户中添加用户。</span><span class="sxs-lookup"><span data-stu-id="442c2-137">Allows you to add users in bulk users by using a Windows PowerShell script.</span></span>  <br/>  <span data-ttu-id="442c2-138">可用于将位置和许可证分配给帐户，而不考虑帐户的创建方式。</span><span class="sxs-lookup"><span data-stu-id="442c2-138">Can be used to assign location and licenses to accounts, regardless of how the accounts are created.</span></span>  <br/> |
|<span data-ttu-id="442c2-139">批量导入</span><span class="sxs-lookup"><span data-stu-id="442c2-139">Bulk import</span></span>  <br/> |[<span data-ttu-id="442c2-140">同时向 Office 365 添加多个用户 - 管理员帮助</span><span class="sxs-lookup"><span data-stu-id="442c2-140">Add several users at the same time to Office 365 - Admin Help</span></span>](add-several-users-at-the-same-time.md) <br/>  <span data-ttu-id="442c2-141">允许您导入 CSV 文件以将一组用户添加到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="442c2-141">Allows you to import a CSV file to add a group of users to Office 365.</span></span>  <br/>  <span data-ttu-id="442c2-142">不能与 SSO 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="442c2-142">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="442c2-143">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="442c2-143">Azure Active Directory</span></span>  <br/> |<span data-ttu-id="442c2-144">你可以使用 Office 365 订阅获取 Azure Active Directory 的免费版本。</span><span class="sxs-lookup"><span data-stu-id="442c2-144">You get a free edition of Azure Active Directory with your Office 365 subscription.</span></span> <span data-ttu-id="442c2-145">您可以为云用户执行自助密码重置等功能，并使用免费版本自定义登录和访问面板页。</span><span class="sxs-lookup"><span data-stu-id="442c2-145">You can perform functions like self-service password reset for cloud users, and customization of the Sign-in and Access Panel pages by using the free edition.</span></span> <span data-ttu-id="442c2-146">若要获取增强的功能，您可以升级到基本版本或高级版。</span><span class="sxs-lookup"><span data-stu-id="442c2-146">To get enhanced functionality, you can upgrade to either the basic edition, or the premium edition.</span></span> <span data-ttu-id="442c2-147">有关支持的功能的列表，请参阅[Azure Active Directory 版本](https://go.microsoft.com/fwlink/p/?LinkId=698465)。</span><span class="sxs-lookup"><span data-stu-id="442c2-147">See [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) for the list of supported features.</span></span>  <br/> |
|<span data-ttu-id="442c2-148">目录同步</span><span class="sxs-lookup"><span data-stu-id="442c2-148">Directory synchronization</span></span>  <br/> |[<span data-ttu-id="442c2-149">将本地标识与 Azure Active Directory 集成</span><span class="sxs-lookup"><span data-stu-id="442c2-149">Integrating your on-premises identities with Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  <span data-ttu-id="442c2-150">对于使用或不使用密码同步进行目录同步，请将[AZURE AD Connect 与 express 设置结合](https://go.microsoft.com/fwlink/p/?LinkID=698537)使用。</span><span class="sxs-lookup"><span data-stu-id="442c2-150">For directory synchronization with or without password synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>  <br/>  <span data-ttu-id="442c2-151">对于多个林和 SSO 选项，请使用[自定义安装的 AZURE AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="442c2-151">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>  <br/>  <span data-ttu-id="442c2-152">提供启用 SSO 所需的基础结构。</span><span class="sxs-lookup"><span data-stu-id="442c2-152">Provides the infrastructure that's necessary to enable SSO.</span></span>  <br/>  <span data-ttu-id="442c2-153">对于很多混合方案是必需的：</span><span class="sxs-lookup"><span data-stu-id="442c2-153">Required for many hybrid scenarios:</span></span>  <br/>  <span data-ttu-id="442c2-154">暂存迁移</span><span class="sxs-lookup"><span data-stu-id="442c2-154">Staged migration</span></span>  <br/>  <span data-ttu-id="442c2-155">混合 Exchange</span><span class="sxs-lookup"><span data-stu-id="442c2-155">Hybrid Exchange</span></span>  <br/>  <span data-ttu-id="442c2-156">将本地目录中的安全和已启用邮件的组同步。</span><span class="sxs-lookup"><span data-stu-id="442c2-156">Synchronizes security and mail-enabled groups from your on-premises directory.</span></span>  <br/> |
   
- <span data-ttu-id="442c2-157">无论您打算如何将用户帐户添加到 Office 365，您都需要管理多个帐户功能，例如分配许可证、指定位置等。</span><span class="sxs-lookup"><span data-stu-id="442c2-157">Regardless of how you intend to add the user accounts to Office 365, you need to manage several account features, such as assigning licenses, specifying location, and so on.</span></span> <span data-ttu-id="442c2-158">可以从管理中心管理这些功能，也可以[使用 Office 365 PowerShell 来创建用户帐户](https://go.microsoft.com/fwlink/p/?LinkId=717083)。</span><span class="sxs-lookup"><span data-stu-id="442c2-158">These features can be managed long-term from the admin center or you can also [create user accounts with Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).</span></span>
    
    <span data-ttu-id="442c2-159">如果选择通过管理中心添加和管理所有用户，您将指定位置，并在创建 Office 365 帐户的同时分配许可证。</span><span class="sxs-lookup"><span data-stu-id="442c2-159">If you choose to add and manage all your users through the admin center, you will specify the location and assign licenses at the same time as creating the Office 365 account.</span></span> <span data-ttu-id="442c2-160">因此，不需要进行大量规划。</span><span class="sxs-lookup"><span data-stu-id="442c2-160">As a result, not much planning is required.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="442c2-161">在 Office 365 中创建帐户，而不分配许可证（例如为 SharePoint Online）意味着帐户所有者可以查看 Microsoft 365 管理中心，但不能访问公司订阅中的任何服务。</span><span class="sxs-lookup"><span data-stu-id="442c2-161">Creating accounts in Office 365 without assigning a license (to SharePoint Online, for example) means that the account owner can view the Microsoft 365 admin center but can't access any of the services within your company's subscription.</span></span> <span data-ttu-id="442c2-162">分配位置和许可证后，帐户将复制到您分配的服务或服务。</span><span class="sxs-lookup"><span data-stu-id="442c2-162">After you assign a location and the license, the account is replicated to the service or services that you assigned.</span></span> <span data-ttu-id="442c2-163">用户可以登录到其帐户并使用您分配给他们的服务。</span><span class="sxs-lookup"><span data-stu-id="442c2-163">The user can sign in to their account and use the services that you assigned to them.</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="442c2-164">后续步骤</span><span class="sxs-lookup"><span data-stu-id="442c2-164">Next steps</span></span>

[<span data-ttu-id="442c2-165">Office 365 与本地环境的集成</span><span class="sxs-lookup"><span data-stu-id="442c2-165">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
## <a name="see-also"></a><span data-ttu-id="442c2-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="442c2-166">See Also</span></span>

[<span data-ttu-id="442c2-167">在 Office 365 中管理用户帐户</span><span class="sxs-lookup"><span data-stu-id="442c2-167">Manage user accounts in Office 365</span></span>](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

