---
title: Office 365 的目录同步计划
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: 介绍与 Office 365、 Active Directory 清理和 Azure Active Directory 连接工具的目录同步。
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539690"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a><span data-ttu-id="371b3-103">Office 365 的目录同步计划</span><span class="sxs-lookup"><span data-stu-id="371b3-103">Plan for directory synchronization for Office 365</span></span>
<span data-ttu-id="371b3-p101">根据业务需求和技术要求，目录同步是最常见的企业用户移动到 Office 365 设置选项。目录同步允许在本地 Active Directory 中托管的标识和所有更新对身份都同步到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="371b3-p101">Depending on business need and technical requirements, directory synchronization is the most common provisioning choice for enterprise customers who are moving to Office 365. Directory synchronization allows identities to be managed in the on-premises Active Directory and all updates to that identity are synchronized to Office 365 .</span></span>
  
<span data-ttu-id="371b3-p102">有几个规划实现目录同步，包括目录准备的要求和 Azure Active Directory 功能时，需要注意的事项。目录准备介绍了很多方面。其中包括属性更新，审核和规划域控制器的位置。要求和功能规划步骤包括确定所必需的规划 multiforest 目录方案、 容量规划和双向同步的权限。</span><span class="sxs-lookup"><span data-stu-id="371b3-p102">There are a couple of things to keep in mind when you plan an implementation of directory synchronization, including directory preparation, and the requirements and functionality of the Azure Active Directory. Directory preparation covers quite a few areas. They include attribute updates, auditing, and planning domain controller placement. Planning requirements and functionality includes determining the permissions that are required, planning for multiforest/directory scenarios, capacity planning, and two-way synchronization.</span></span>
  
## <a name="office-365-identity-models"></a><span data-ttu-id="371b3-110">Office 365 标识模型</span><span class="sxs-lookup"><span data-stu-id="371b3-110">Office 365 identity models</span></span>
<span data-ttu-id="371b3-111">Office 365 使用两种主要的身份验证和标识模型： 云身份验证和联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="371b3-111">Office 365 uses two main authentication and identity models: cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="371b3-112">云身份验证</span><span class="sxs-lookup"><span data-stu-id="371b3-112">Cloud authentication</span></span>
<span data-ttu-id="371b3-113">[云身份](about-office-365-identity.md)-创建和管理 Office 365 管理中心中的用户，您也可以使用 Windows PowerShell 或 Azure Active Directory 管理您的用户。</span><span class="sxs-lookup"><span data-stu-id="371b3-113">[Cloud identity](about-office-365-identity.md) - create and manage users in the Office 365 admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span> 
  
<span data-ttu-id="371b3-p103">[与无缝单一登录的密码哈希同步](about-office-365-identity.md)-启用内部部署目录对象在 Azure AD 身份验证的最简单方式。使用密码哈希同步 (PHS)，您可以将您的本地 Active Directory 用户帐户对象与 Office 365 同步和管理用户内部部署。</span><span class="sxs-lookup"><span data-stu-id="371b3-p103">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span> 
  
<span data-ttu-id="371b3-116">[传递身份验证与无缝单一登录](about-office-365-identity.md)-提供用于 Azure AD 身份验证服务使用一个或多个本地服务器上运行的软件代理程序验证直接与用户简单密码验证您内部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="371b3-116">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span> 
  
### <a name="federated-authentication"></a><span data-ttu-id="371b3-117">联合身份验证</span><span class="sxs-lookup"><span data-stu-id="371b3-117">Federated authentication</span></span>
<span data-ttu-id="371b3-118">[使用 Active Directory 联合身份验证服务 AD FS 联合标识](about-office-365-identity.md)-主要用于身份验证要求更复杂的大型企业组织的内部部署目录对象与 Office 365 同步和用户帐户托管在内部部署。</span><span class="sxs-lookup"><span data-stu-id="371b3-118">[Federated identity with Active Directory Federation Services AD FS](about-office-365-identity.md) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span> 
  
<span data-ttu-id="371b3-119">[第三方身份验证和标识提供程序](about-office-365-identity.md)的内部部署目录对象可能同步到 Office 365 和云资源访问主要第三方身份提供程序 (IdP) 进行管理。</span><span class="sxs-lookup"><span data-stu-id="371b3-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> 
  
## <a name="active-directory-cleanup"></a><span data-ttu-id="371b3-120">Active Directory 清除</span><span class="sxs-lookup"><span data-stu-id="371b3-120">Active Directory Cleanup</span></span>
<span data-ttu-id="371b3-121">为了帮助确保使用同步无缝转换到 Office 365，我们强烈建议您在开始 Office 365 目录同步部署之前准备 Active Directory 林。</span><span class="sxs-lookup"><span data-stu-id="371b3-121">To help ensure a seamless transition to Office 365 by using synchronization, we highly recommend that you prepare your Active Directory forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="371b3-p104">当您[设置 Office 365 中目录同步](set-up-directory-synchronization.md)，步骤之一是[下载并运行 IdFix 工具](install-and-run-idfix.md)。您可以使用 IdFix 工具帮助[目录清理](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="371b3-p104">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md). You can use the IdFix tool to help with the [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="371b3-124">目录清理应专注于以下任务：</span><span class="sxs-lookup"><span data-stu-id="371b3-124">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="371b3-125">删除重复的**proxyAddress**和**userPrincipalName**属性。</span><span class="sxs-lookup"><span data-stu-id="371b3-125">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="371b3-126">使用有效的 **userPrincipalName** 属性更新空的和无效的 **userPrincipalName** 属性。</span><span class="sxs-lookup"><span data-stu-id="371b3-126">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="371b3-p105">删除无效和可疑字符中**givenName**、 姓 ( **sn** )、 **sAMAccountName**、 **displayName**、**邮件**、 **proxyAddresses**、 **mailNickname**和**userprincipalname 属性**属性。有关准备属性的详细信息，请参阅[Azure Active Directory 同步工具同步的属性列表](https://go.microsoft.com/fwlink/p/?LinkId=396719)。</span><span class="sxs-lookup"><span data-stu-id="371b3-p105">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes. For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="371b3-129">这些是 Azure AD 连接同步的相同属性。</span><span class="sxs-lookup"><span data-stu-id="371b3-129">These are the same attributes that Azure AD Connect syncs.</span></span> 
  
## <a name="multiforest-deployment-considerations"></a><span data-ttu-id="371b3-130">多林部署注意事项</span><span class="sxs-lookup"><span data-stu-id="371b3-130">Multiforest Deployment Considerations</span></span>
<span data-ttu-id="371b3-131">对于多个林和 SSO 选项，使用[自定义安装的 Azure AD 连接](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="371b3-131">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="371b3-132">如果您的组织具有多个林的身份验证 （登录林），强烈建议如下：</span><span class="sxs-lookup"><span data-stu-id="371b3-132">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="371b3-p106">**评估合并您的林。** 一般情况下，没有所需维护多个林的更多开销。除非您的组织有规定需要单独的林中的安全约束，请考虑简化您的内部部署环境。</span><span class="sxs-lookup"><span data-stu-id="371b3-p106">**Evaluate consolidating your forests.** In general, there's more overhead required to maintain multiple forests. Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="371b3-p107">**仅在主登录林中的使用。** 请考虑部署仅在您的主登录林的初始部署时的 Office 365 中的 Office 365。</span><span class="sxs-lookup"><span data-stu-id="371b3-p107">**Use only in your primary logon forest.** Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 
    
<span data-ttu-id="371b3-138">如果您不能合并多林 Active Directory 部署或要使用其他目录服务来管理标识，您可能能够同步这些 Microsoft 或合作伙伴的帮助。</span><span class="sxs-lookup"><span data-stu-id="371b3-138">If you can't consolidate your multiforest Active Directory deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="371b3-139">有关详细信息，请参阅[单一登录方案的多林目录同步](https://go.microsoft.com/fwlink/p/?LinkId=525321)。</span><span class="sxs-lookup"><span data-stu-id="371b3-139">For more information, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="371b3-140">目录集成工具</span><span class="sxs-lookup"><span data-stu-id="371b3-140">Directory integration tools</span></span>
<span data-ttu-id="371b3-p108">目录同步到 Office 365 的目录基础结构，从内部部署 Active Directory 环境是同步的目录对象 （用户、 组和联系人）。请参阅[目录集成工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)可用的工具和其功能的列表。推荐的工具，用于是[Azure Active Directory 连接](https://go.microsoft.com/fwlink/?LinkId=525323)。</span><span class="sxs-lookup"><span data-stu-id="371b3-p108">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure. See [directory integration tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool to use is [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).</span></span>
  
<span data-ttu-id="371b3-p109">当用户帐户与 Office 365 目录同步的第一次时，它们被标记为未激活。他们无法发送或接收电子邮件、 和它们不使用订阅许可证。已准备好分配给特定用户的 Office 365 订阅时，必须选择并分配的有效许可证激活。</span><span class="sxs-lookup"><span data-stu-id="371b3-p109">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as non-activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by assigning a valid license.</span></span>
  
<span data-ttu-id="371b3-147">目录同步时，需要以下特性和功能：</span><span class="sxs-lookup"><span data-stu-id="371b3-147">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="371b3-148">SSO</span><span class="sxs-lookup"><span data-stu-id="371b3-148">SSO</span></span>
    
- <span data-ttu-id="371b3-149">Lync 共存</span><span class="sxs-lookup"><span data-stu-id="371b3-149">Lync coexistence</span></span>
    
- <span data-ttu-id="371b3-150">Exchange 混合部署，包括：</span><span class="sxs-lookup"><span data-stu-id="371b3-150">Exchange hybrid deployment, including:</span></span>
    
  - <span data-ttu-id="371b3-151">您的本地 Exchange 环境与 Office 365 之间完全共享全局地址列表 (GAL)。</span><span class="sxs-lookup"><span data-stu-id="371b3-151">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="371b3-152">同步不同邮件系统中的 GAL 信息。</span><span class="sxs-lookup"><span data-stu-id="371b3-152">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="371b3-p110">能够将用户添加到和删除 Office 365 服务产品的用户。以下要求：</span><span class="sxs-lookup"><span data-stu-id="371b3-p110">The ability to add users to and remove users from Office 365 service offerings. This requires the following:</span></span>
  - <span data-ttu-id="371b3-p111">双向同步必须配置目录同步安装过程中。默认情况下，目录同步工具仅对云编写目录信息。配置双向同步时，您会启用写回功能，以便进行有限的数量的对象属性是从云中，复制，然后写它们回本地 Active Directory。写回也称为 Exchange 混合模式。</span><span class="sxs-lookup"><span data-stu-id="371b3-p111">Two-way synchronization must be configured during directory synchronization setup. By default, directory synchronization tools write directory information only to the cloud. When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local Active Directory. Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="371b3-159">内部部署 Exchange 混合部署</span><span class="sxs-lookup"><span data-stu-id="371b3-159">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="371b3-160">将一些用户邮箱移动到 Office 365，同时保持其他用户邮箱的本地功能。</span><span class="sxs-lookup"><span data-stu-id="371b3-160">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="371b3-161">安全发件人和阻止发件人本地被复制到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="371b3-161">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="371b3-162">基本委托和代表发送电子邮件功能。</span><span class="sxs-lookup"><span data-stu-id="371b3-162">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="371b3-163">您具有本地集成的智能卡或多重身份验证解决方案。</span><span class="sxs-lookup"><span data-stu-id="371b3-163">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
    
- <span data-ttu-id="371b3-164">同步照片、 缩略图、 会议室和安全组</span><span class="sxs-lookup"><span data-stu-id="371b3-164">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>