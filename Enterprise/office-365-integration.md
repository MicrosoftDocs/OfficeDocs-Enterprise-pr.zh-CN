---
title: Office 365 与内部部署环境的集成
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: 了解如何将 Office 365 与您现有的目录服务集成。
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539694"
---
# <a name="office-365-integration-with-on-premises-environments"></a><span data-ttu-id="e53a7-103">Office 365 与内部部署环境的集成</span><span class="sxs-lookup"><span data-stu-id="e53a7-103">Office 365 integration with on-premises environments</span></span>

<span data-ttu-id="e53a7-104">可以将 Office 365 与您现有的目录服务和内部部署安装 Exchange Server、 Skype 集成业务服务器 2015年或 SharePoint Server 2013。</span><span class="sxs-lookup"><span data-stu-id="e53a7-104">You can integrate Office 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server 2013.</span></span>
  
 - <span data-ttu-id="e53a7-p101">当您将与目录服务集成时，您可以同步并管理这两种环境的用户帐户。您还可以添加密码哈希同步或单一登录 (SSO) 使用户可以登录到这两种环境与内部部署凭据。</span><span class="sxs-lookup"><span data-stu-id="e53a7-p101">When you integrate with directory services, you can synchronize and manage user accounts for both environments. You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="e53a7-p102">当您将与内部部署服务器产品集成时，您将创建混合环境。混合环境可帮助您迁移到 Office 365 用户或信息或您可以继续有一些用户或一些信息内部部署和云中的一些。有关混合环境的详细信息，请参阅[Office 365 的混合云解决方案概述](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)。</span><span class="sxs-lookup"><span data-stu-id="e53a7-p102">When you integrate with on-premises server products, you create a hybrid environment. A hybrid environment can help as you migrate users or information to Office 365, or you can continue to have some users or some information on-premises and some in the cloud. For more information about hybrid environments, see [Office 365 hybrid cloud solutions overview](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).</span></span>

<span data-ttu-id="e53a7-110">您还可以使用 Azure AD 顾问的自定义安装程序指南：</span><span class="sxs-lookup"><span data-stu-id="e53a7-110">You can also use the Azure AD advisors for customized setup guidance:</span></span>
- [<span data-ttu-id="e53a7-111">Azure AD 连接顾问</span><span class="sxs-lookup"><span data-stu-id="e53a7-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="e53a7-112">AD FS 部署顾问</span><span class="sxs-lookup"><span data-stu-id="e53a7-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="e53a7-113">Azure RMS 部署向导</span><span class="sxs-lookup"><span data-stu-id="e53a7-113">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
- [<span data-ttu-id="e53a7-114">Azure AD Premium 安装指南</span><span class="sxs-lookup"><span data-stu-id="e53a7-114">Azure AD Premium setup guidance</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="e53a7-115">准备工作</span><span class="sxs-lookup"><span data-stu-id="e53a7-115">Before you begin</span></span>
<span data-ttu-id="e53a7-p103">集成 Office 365 和本地环境之前，您还需要为[网络规划和性能优化 Office 365](network-planning-and-performance.md)参加。您还需要了解 Office 365 中可用[的身份模型](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="e53a7-p103">Before you integrate Office 365 and an on-premises environment, you also need to attend to [network planning and performance tuning for Office 365](network-planning-and-performance.md). You will also want to understand the available [identity models](about-office-365-identity.md) in Office 365.</span></span> 

<span data-ttu-id="e53a7-118">请参阅[管理 Office 365 用户帐户其中](manage-office-365-accounts.md)工具可用于管理 Office 365 用户帐户和帐户的列表。</span><span class="sxs-lookup"><span data-stu-id="e53a7-118">See [where to manage Office 365 user accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Office 365 users and accounts.</span></span> 
  
## <a name="integrate-office-365-with-directory-services"></a><span data-ttu-id="e53a7-119">将 Office 365 与目录服务集成</span><span class="sxs-lookup"><span data-stu-id="e53a7-119">Integrate Office 365 with directory services</span></span>
<span data-ttu-id="e53a7-p104">如果已在内部部署目录中现有的用户帐户，您不希望重新创建的所有 Office 365 和简介差异内容还是环境之间的错误的风险中这些帐户。目录同步将帮助您镜像之间联机这些帐户和本地环境。通过目录同步，用户无需记住为每个环境中，新信息，您无需创建或更新帐户两次。您将需要目录同步[准备内部部署目录](prepare-for-directory-synchronization.md)，可以手动执行此操作，也可以使用[IdFix 工具](install-and-run-idfix.md)（IdFix 工具仅适用于与 Active Directory）。</span><span class="sxs-lookup"><span data-stu-id="e53a7-p104">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Office 365 and risk introducing differences or errors between the environments. Directory synchronization helps you mirror those accounts between your online and on-premises environments. With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice. You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory).</span></span> 
  
![使用目录同步将保留在本地和联机用户同步的帐户信息](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="e53a7-p105">如果您希望用户能够使用其内部部署凭据登录到 Office 365，您还可以配置 SSO。与 SSO 功能，Office 365 配置为信任进行用户身份验证的内部部署环境。</span><span class="sxs-lookup"><span data-stu-id="e53a7-p105">If you want users to be able to log on to Office 365 with their on-premises credentials, you can also configure SSO. With SSO, Office 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![使用单一登录，相同的帐户是在本地和联机环境中可用](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="e53a7-128">下表中所示，不同的用户帐户管理技术为您的用户提供不同的体验。</span><span class="sxs-lookup"><span data-stu-id="e53a7-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="e53a7-129">**使用或不密码哈希同步或传递身份验证目录同步**</span><span class="sxs-lookup"><span data-stu-id="e53a7-129">**Directory synchronization with or without password hash synchronization or pass-through authentication**</span></span>
<span data-ttu-id="e53a7-p106">用户登录到其内部部署环境与他们的用户帐户 （域 \ 用户名）。当他们转到 Office 365 时，他们必须再次使用登录其工作或学校帐户 (user@domain.com)。在这两个环境中相同的用户的用户名。当您添加密码哈希同步还是传递身份验证时，用户具有对于这两个环境，相同的密码，但必须重新提供这些凭据登录到 Office 365 时。使用密码哈希同步的目录同步是最常使用的目录同步方案。</span><span class="sxs-lookup"><span data-stu-id="e53a7-p106">A user logs on to their on-premises environment with their user account (domain\username). When they go to Office 365, they must log on again with their work or school account (user@domain.com). The user name is the same in both environments. When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Office 365. Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="e53a7-p107">若要设置目录同步，使用 Azure Active Directory 连接。有关说明，阅读[Set up Office 365 的目录同步](set-up-directory-synchronization.md)和[使用 Azure AD 连接使用 express 设置](https://go.microsoft.com/fwlink/p/?LinkId=698537)。</span><span class="sxs-lookup"><span data-stu-id="e53a7-p107">To set up directory synchronization, use Azure Active Directory Connect. For instructions, read [Set up directory synchronization for Office 365](set-up-directory-synchronization.md), and [Use Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="e53a7-137">详细了解如何[设置用户通过目录同步到 Office 365 准备](prepare-for-directory-synchronization.md)和[集成本地标识与 Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101)。</span><span class="sxs-lookup"><span data-stu-id="e53a7-137">Learn more about [preparing to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="e53a7-138">**与 SSO 的目录同步**</span><span class="sxs-lookup"><span data-stu-id="e53a7-138">**Directory synchronization with SSO**</span></span>
<span data-ttu-id="e53a7-p108">用户登录到其内部部署环境与他们的用户帐户。当他们转到 Office 365 时，它们可以自动登录，或使用用于其内部部署环境 （域 \ 用户名） 相同的凭据进行登录。</span><span class="sxs-lookup"><span data-stu-id="e53a7-p108">A user logs on to their on-premises environment with their user account. When they go to Office 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="e53a7-p109">若要设置 SSO 也使用 Azure AD 连接。有关说明，请阅读[使用 Azure AD 连接使用自定义设置](https://go.microsoft.com/fwlink/p/?LinkID=698430)。</span><span class="sxs-lookup"><span data-stu-id="e53a7-p109">To set up SSO you also use Azure AD Connect. For instructions, read [Use Azure AD Connect with custom settings](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="e53a7-143">了解[应用程序访问和使用 Azure Active Directory 单一登录](https://go.microsoft.com/fwlink/p/?LinkId=698604)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e53a7-143">Learn more about [application access and single sign-on with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="e53a7-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="e53a7-144">Azure AD Connect</span></span>
<span data-ttu-id="e53a7-p110">Azure AD 连接替换较旧版本的标识集成工具，例如目录同步和 Azure AD 同步。有关详细信息，请参阅[将您的本地标识与 Azure Active Directory 集成](https://go.microsoft.com/fwlink/p/?LinkId=527969)。如果您想要从 Azure Active Directory 同步更新到 Azure AD 连接，请参阅[的升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。请参阅[Microsoft Azure 中](https://go.microsoft.com/fwlink/?LinkId=517887)的 Office 365 目录同步 (DirSync) 构建的解决方案体系结构。</span><span class="sxs-lookup"><span data-stu-id="e53a7-p110">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240). See a solution architecture built for [Office 365 Directory Synchronization (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>