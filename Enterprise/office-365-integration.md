---
title: Office 365 与本地环境的集成
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: 了解如何将 Office 365 与您的现有目录服务集成。
ms.openlocfilehash: 1fa044a0a9db0d8422239cf301fea21a2c3d47e9
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069738"
---
# <a name="office-365-integration-with-on-premises-environments"></a><span data-ttu-id="3aeec-103">Office 365 与本地环境的集成</span><span class="sxs-lookup"><span data-stu-id="3aeec-103">Office 365 integration with on-premises environments</span></span>

<span data-ttu-id="3aeec-104">您可以将 Office 365 与您现有的目录服务以及 Exchange Server、Skype for Business Server 2015 或 SharePoint Server 2013 的本地安装集成。</span><span class="sxs-lookup"><span data-stu-id="3aeec-104">You can integrate Office 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server 2013.</span></span>
  
 - <span data-ttu-id="3aeec-105">当您与目录服务集成时, 您可以同步和管理这两个环境的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="3aeec-105">When you integrate with directory services, you can synchronize and manage user accounts for both environments.</span></span> <span data-ttu-id="3aeec-106">您还可以添加密码哈希同步或单一登录 (SSO), 以便用户可以使用其本地凭据登录到这两个环境。</span><span class="sxs-lookup"><span data-stu-id="3aeec-106">You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="3aeec-107">当您与本地服务器产品集成时, 将创建混合环境。</span><span class="sxs-lookup"><span data-stu-id="3aeec-107">When you integrate with on-premises server products, you create a hybrid environment.</span></span> <span data-ttu-id="3aeec-108">当您将用户或信息迁移到 Office 365 时, 混合环境可帮助您, 也可以继续在本地使用某些用户或某些信息以及在云中使用一些信息。</span><span class="sxs-lookup"><span data-stu-id="3aeec-108">A hybrid environment can help as you migrate users or information to Office 365, or you can continue to have some users or some information on-premises and some in the cloud.</span></span> <span data-ttu-id="3aeec-109">有关混合环境的详细信息, 请参阅[Office 365 混合云解决方案概述](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)。</span><span class="sxs-lookup"><span data-stu-id="3aeec-109">For more information about hybrid environments, see [Office 365 hybrid cloud solutions overview](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).</span></span>

<span data-ttu-id="3aeec-110">您还可以使用 Azure AD 顾问获取自定义设置指南:</span><span class="sxs-lookup"><span data-stu-id="3aeec-110">You can also use the Azure AD advisors for customized setup guidance:</span></span>
- [<span data-ttu-id="3aeec-111">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="3aeec-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="3aeec-112">AD FS 部署顾问</span><span class="sxs-lookup"><span data-stu-id="3aeec-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="3aeec-113">Azure RMS 部署向导</span><span class="sxs-lookup"><span data-stu-id="3aeec-113">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
- [<span data-ttu-id="3aeec-114">Azure AD Premium 设置指南</span><span class="sxs-lookup"><span data-stu-id="3aeec-114">Azure AD Premium setup guidance</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="3aeec-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="3aeec-115">Before you begin</span></span>
<span data-ttu-id="3aeec-116">在集成 Office 365 和本地环境之前, 还需要参加[office 365 的网络规划和性能调整](network-planning-and-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="3aeec-116">Before you integrate Office 365 and an on-premises environment, you also need to attend to [network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span> <span data-ttu-id="3aeec-117">您还需要了解 Office 365 中可用的[标识模型](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="3aeec-117">You will also want to understand the available [identity models](about-office-365-identity.md) in Office 365.</span></span> 

<span data-ttu-id="3aeec-118">有关可用于管理 Office 365 用户和帐户的工具列表, 请参阅[管理 office 365 用户帐户的位置](manage-office-365-accounts.md)。</span><span class="sxs-lookup"><span data-stu-id="3aeec-118">See [where to manage Office 365 user accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Office 365 users and accounts.</span></span> 
  
## <a name="integrate-office-365-with-directory-services"></a><span data-ttu-id="3aeec-119">将 Office 365 与目录服务集成</span><span class="sxs-lookup"><span data-stu-id="3aeec-119">Integrate Office 365 with directory services</span></span>
<span data-ttu-id="3aeec-120">如果您在本地目录中有现有的用户帐户, 则不需要在 Office 365 中重新创建所有这些帐户, 并且在环境之间引入差异或错误的风险。</span><span class="sxs-lookup"><span data-stu-id="3aeec-120">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Office 365 and risk introducing differences or errors between the environments.</span></span> <span data-ttu-id="3aeec-121">目录同步可帮助您在您的联机和本地环境中镜像这些帐户。</span><span class="sxs-lookup"><span data-stu-id="3aeec-121">Directory synchronization helps you mirror those accounts between your online and on-premises environments.</span></span> <span data-ttu-id="3aeec-122">通过目录同步, 用户不必记住每个环境的新信息, 也不必创建或更新帐户两次。</span><span class="sxs-lookup"><span data-stu-id="3aeec-122">With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice.</span></span> <span data-ttu-id="3aeec-123">您需要为[本地目录准备](prepare-for-directory-synchronization.md)目录同步, 您可以手动执行此操作, 也可以使用[IdFix 工具](install-and-run-idfix.md)(IdFix 工具仅适用于 Active directory)。</span><span class="sxs-lookup"><span data-stu-id="3aeec-123">You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory).</span></span> 
  
![使用目录同步将本地和联机用户帐户信息保持同步](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="3aeec-125">如果您希望用户能够使用他们的本地凭据登录到 Office 365, 您还可以配置 SSO。</span><span class="sxs-lookup"><span data-stu-id="3aeec-125">If you want users to be able to log on to Office 365 with their on-premises credentials, you can also configure SSO.</span></span> <span data-ttu-id="3aeec-126">使用 SSO, Office 365 配置为信任本地环境以进行用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="3aeec-126">With SSO, Office 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![使用单一登录, 在本地和联机环境中都可以使用相同的帐户。](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="3aeec-128">不同的用户帐户管理技术为用户提供了不同的体验, 如下表所示。</span><span class="sxs-lookup"><span data-stu-id="3aeec-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="3aeec-129">**具有或不具有密码哈希同步或传递身份验证的目录同步**</span><span class="sxs-lookup"><span data-stu-id="3aeec-129">**Directory synchronization with or without password hash synchronization or pass-through authentication**</span></span>
<span data-ttu-id="3aeec-130">用户使用其用户帐户 (域 \ 用户名) 登录到本地环境。</span><span class="sxs-lookup"><span data-stu-id="3aeec-130">A user logs on to their on-premises environment with their user account (domain\username).</span></span> <span data-ttu-id="3aeec-131">当他们转到 Office 365 时, 他们必须使用其工作或学校帐户 (user@domain.com) 重新登录。</span><span class="sxs-lookup"><span data-stu-id="3aeec-131">When they go to Office 365, they must log on again with their work or school account (user@domain.com).</span></span> <span data-ttu-id="3aeec-132">这两个环境中的用户名相同。</span><span class="sxs-lookup"><span data-stu-id="3aeec-132">The user name is the same in both environments.</span></span> <span data-ttu-id="3aeec-133">当您添加密码哈希同步或传递身份验证时, 用户在这两种环境中都具有相同的密码, 但在登录到 Office 365 时将不得不再次提供这些凭据。</span><span class="sxs-lookup"><span data-stu-id="3aeec-133">When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Office 365.</span></span> <span data-ttu-id="3aeec-134">使用密码哈希同步的目录同步是最常用的目录同步方案。</span><span class="sxs-lookup"><span data-stu-id="3aeec-134">Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="3aeec-135">若要设置目录同步, 请使用 Azure Active Directory Connect。</span><span class="sxs-lookup"><span data-stu-id="3aeec-135">To set up directory synchronization, use Azure Active Directory Connect.</span></span> <span data-ttu-id="3aeec-136">有关说明, 请参阅[设置 Office 365 的目录同步](set-up-directory-synchronization.md), 并[将 Azure AD Connect 与 Express 设置一起使用](https://go.microsoft.com/fwlink/p/?LinkId=698537)。</span><span class="sxs-lookup"><span data-stu-id="3aeec-136">For instructions, read [Set up directory synchronization for Office 365](set-up-directory-synchronization.md), and [Use Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="3aeec-137">了解有关[准备通过目录同步将用户预配到 Office 365](prepare-for-directory-synchronization.md)并将[本地标识与 Azure Active directory 集成](https://go.microsoft.com/fwlink/?LinkId=518101)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3aeec-137">Learn more about [preparing to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="3aeec-138">**使用 SSO 同步目录**</span><span class="sxs-lookup"><span data-stu-id="3aeec-138">**Directory synchronization with SSO**</span></span>
<span data-ttu-id="3aeec-139">用户使用其用户帐户登录到本地环境。</span><span class="sxs-lookup"><span data-stu-id="3aeec-139">A user logs on to their on-premises environment with their user account.</span></span> <span data-ttu-id="3aeec-140">当他们转到 Office 365 时, 它们要么是自动登录, 要么使用它们用于本地环境的相同凭据 (域 \ 用户名) 登录。</span><span class="sxs-lookup"><span data-stu-id="3aeec-140">When they go to Office 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="3aeec-141">若要设置 SSO, 您还可以使用 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="3aeec-141">To set up SSO you also use Azure AD Connect.</span></span> <span data-ttu-id="3aeec-142">有关说明, 请参阅[使用自定义设置的 AZURE AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430)。</span><span class="sxs-lookup"><span data-stu-id="3aeec-142">For instructions, read [Use Azure AD Connect with custom settings](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="3aeec-143">了解有关[Azure Active Directory 的应用程序访问和单一登录](https://go.microsoft.com/fwlink/p/?LinkId=698604)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3aeec-143">Learn more about [application access and single sign-on with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="3aeec-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3aeec-144">Azure AD Connect</span></span>
<span data-ttu-id="3aeec-145">Azure AD Connect 替代了较早版本的身份集成工具, 如 DirSync 和 Azure AD 同步。有关详细信息, 请参阅[将本地标识与 Azure Active Directory 集成](https://go.microsoft.com/fwlink/p/?LinkId=527969)。</span><span class="sxs-lookup"><span data-stu-id="3aeec-145">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span> <span data-ttu-id="3aeec-146">如果要从 Azure Active Directory 同步更新到 Azure AD Connect, 请参阅[升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。</span><span class="sxs-lookup"><span data-stu-id="3aeec-146">If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span> <span data-ttu-id="3aeec-147">请参阅[在 Microsoft Azure 中为 Office 365 目录同步 (DirSync)](https://go.microsoft.com/fwlink/?LinkId=517887)构建的解决方案体系结构。</span><span class="sxs-lookup"><span data-stu-id="3aeec-147">See a solution architecture built for [Office 365 Directory Synchronization (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>