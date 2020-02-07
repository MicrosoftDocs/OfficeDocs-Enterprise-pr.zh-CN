---
title: Office 365 的混合标识和目录同步
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: 介绍与 Office 365、Active Directory 域服务清理和 Azure Active Directory Connect 工具的目录同步。
ms.openlocfilehash: 5368fc00aafe66ed51af80c50aaf72ee5f939041
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841759"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a><span data-ttu-id="5fe66-103">Office 365 的混合标识和目录同步</span><span class="sxs-lookup"><span data-stu-id="5fe66-103">Hybrid identity and directory synchronization for Office 365</span></span>

<span data-ttu-id="5fe66-104">*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="5fe66-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="5fe66-105">根据业务需求和技术要求，混合身份模型和目录同步对于采用 Office 365 的企业客户来说是最常见的选择。</span><span class="sxs-lookup"><span data-stu-id="5fe66-105">Depending on business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Office 365.</span></span> <span data-ttu-id="5fe66-106">目录同步允许您在 Active Directory 域服务（AD DS）中管理标识，对用户帐户、组和联系人的所有更新将同步到 Office 365 订阅的 Azure Active Directory （Azure AD）租户。</span><span class="sxs-lookup"><span data-stu-id="5fe66-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="5fe66-107">首次同步 AD DS 用户帐户时，不会自动为其分配 Office 365 许可证，也不能访问 Office 365 服务（如电子邮件）。</span><span class="sxs-lookup"><span data-stu-id="5fe66-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license and cannot access Office 365 services, such as email.</span></span> <span data-ttu-id="5fe66-108">您必须将许可证分配给这些用户帐户，可以单独或动态地通过组成员资格。</span><span class="sxs-lookup"><span data-stu-id="5fe66-108">You must assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="5fe66-109">混合标识的身份验证</span><span class="sxs-lookup"><span data-stu-id="5fe66-109">Authentication for hybrid identity</span></span>

<span data-ttu-id="5fe66-110">使用混合标识模型时，有两种类型的身份验证：</span><span class="sxs-lookup"><span data-stu-id="5fe66-110">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="5fe66-111">托管身份验证</span><span class="sxs-lookup"><span data-stu-id="5fe66-111">Managed authentication</span></span>

  <span data-ttu-id="5fe66-112">Azure AD 通过使用本地存储的哈希版本来处理身份验证过程，或将凭据发送到内部部署 AD DS 要进行身份验证的本地软件代理。</span><span class="sxs-lookup"><span data-stu-id="5fe66-112">Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="5fe66-113">联合身份验证</span><span class="sxs-lookup"><span data-stu-id="5fe66-113">Federated authentication</span></span>

  <span data-ttu-id="5fe66-114">Azure AD 重定向请求身份验证的客户端计算机，以联系另一个标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="5fe66-114">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="5fe66-115">托管身份验证</span><span class="sxs-lookup"><span data-stu-id="5fe66-115">Managed authentication</span></span>

<span data-ttu-id="5fe66-116">有两种类型的托管身份验证：</span><span class="sxs-lookup"><span data-stu-id="5fe66-116">There are two types of managed authentication:</span></span>

- <span data-ttu-id="5fe66-117">密码哈希同步（PHS）</span><span class="sxs-lookup"><span data-stu-id="5fe66-117">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="5fe66-118">Azure AD 执行身份验证本身。</span><span class="sxs-lookup"><span data-stu-id="5fe66-118">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="5fe66-119">直通身份验证 (PTA)</span><span class="sxs-lookup"><span data-stu-id="5fe66-119">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="5fe66-120">Azure AD 具有 AD DS 执行身份验证。</span><span class="sxs-lookup"><span data-stu-id="5fe66-120">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization"></a><span data-ttu-id="5fe66-121">密码哈希同步</span><span class="sxs-lookup"><span data-stu-id="5fe66-121">Password hash synchronization</span></span>

<span data-ttu-id="5fe66-122">使用密码哈希同步（PHS），您可以将 AD DS 用户帐户与 Office 365 同步并在本地管理您的用户。</span><span class="sxs-lookup"><span data-stu-id="5fe66-122">With password hash synchronization (PHS), you synchronize your AD DS user accounts with Office 365 and manage your users on-premises.</span></span> <span data-ttu-id="5fe66-123">用户密码的哈希将从你的 AD DS 同步到 Azure AD，以便用户在本地和在云中具有相同的密码。</span><span class="sxs-lookup"><span data-stu-id="5fe66-123">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="5fe66-124">这是在 Azure AD 中为 AD DS 标识启用身份验证的最简单方法。</span><span class="sxs-lookup"><span data-stu-id="5fe66-124">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![密码哈希同步（PHS）](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="5fe66-126">更改密码或在本地重置密码时，新的密码哈希将同步到 Azure AD，以便您的用户始终可以对云资源和本地资源使用相同的密码。</span><span class="sxs-lookup"><span data-stu-id="5fe66-126">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="5fe66-127">用户密码永远不会发送到 Azure AD 或以明文形式存储在 Azure AD 中。</span><span class="sxs-lookup"><span data-stu-id="5fe66-127">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="5fe66-128">Azure AD 的一些高级功能（如标识保护）需要 PHS，而不管选择了哪种身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="5fe66-128">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="5fe66-129">请参阅[选择 PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)以了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="5fe66-129">See [choosing PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication"></a><span data-ttu-id="5fe66-130">传递身份验证</span><span class="sxs-lookup"><span data-stu-id="5fe66-130">Pass-through authentication</span></span>

<span data-ttu-id="5fe66-131">传递身份验证（PTA）使用在一个或多个本地服务器上运行的软件代理为 Azure AD 身份验证服务提供简单的密码验证，以通过 AD DS 直接验证用户。</span><span class="sxs-lookup"><span data-stu-id="5fe66-131">Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="5fe66-132">通过传递身份验证（PTA），您可以将 AD DS 用户帐户与 Office 365 同步并在本地管理用户。</span><span class="sxs-lookup"><span data-stu-id="5fe66-132">With pass-through authentication (PTA), you synchronize AD DS user accounts with Office 365 and manage your users on-premises.</span></span> 

![直通身份验证 (PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="5fe66-134">PTA 允许您的用户使用其内部部署帐户和密码登录到本地和 Office 365 资源和应用程序。</span><span class="sxs-lookup"><span data-stu-id="5fe66-134">PTA allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="5fe66-135">此配置将直接对本地 AD DS 验证用户密码，而无需在 Azure AD 中存储密码哈希。</span><span class="sxs-lookup"><span data-stu-id="5fe66-135">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="5fe66-136">PTA 也适用于具有安全要求的组织，以立即强制实施本地用户帐户状态、密码策略和登录时间。</span><span class="sxs-lookup"><span data-stu-id="5fe66-136">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="5fe66-137">请参阅[选择 PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)以了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="5fe66-137">See [choosing PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="5fe66-138">联合身份验证</span><span class="sxs-lookup"><span data-stu-id="5fe66-138">Federated authentication</span></span>

<span data-ttu-id="5fe66-139">联合身份验证主要针对具有更复杂的身份验证要求的大型企业组织。</span><span class="sxs-lookup"><span data-stu-id="5fe66-139">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="5fe66-140">AD DS 标识与 Office 365 同步，并且用户帐户在本地进行管理。</span><span class="sxs-lookup"><span data-stu-id="5fe66-140">AD DS identities are synchronized with Office 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="5fe66-141">使用联合身份验证，用户在本地和在云中具有相同的密码，且无需再次登录才能使用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="5fe66-141">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365.</span></span> 

<span data-ttu-id="5fe66-142">联合身份验证可支持其他身份验证要求（如基于智能卡的身份验证或第三方多重身份验证），通常在组织具有身份验证要求时不提供由 Azure AD 本机支持。</span><span class="sxs-lookup"><span data-stu-id="5fe66-142">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="5fe66-143">若要了解详细信息，请参阅[选择联合身份验证](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)。</span><span class="sxs-lookup"><span data-stu-id="5fe66-143">See [choosing federated authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="5fe66-144">第三方身份验证和标识提供程序</span><span class="sxs-lookup"><span data-stu-id="5fe66-144">Third-party authentication and identity providers</span></span>

<span data-ttu-id="5fe66-145">内部部署目录对象可能会同步到 Office 365，并且云资源访问主要由第三方标识提供程序（IdP）进行管理。</span><span class="sxs-lookup"><span data-stu-id="5fe66-145">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="5fe66-146">如果您的组织使用第三方联合解决方案，则可以使用适用于 Office 365 的解决方案配置登录，前提是第三方联合解决方案与 Azure AD 兼容。</span><span class="sxs-lookup"><span data-stu-id="5fe66-146">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="5fe66-147">若要了解详细信息，请参阅[AZURE AD 联合身份验证兼容性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)。</span><span class="sxs-lookup"><span data-stu-id="5fe66-147">See [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="5fe66-148">AD DS 清理</span><span class="sxs-lookup"><span data-stu-id="5fe66-148">AD DS Cleanup</span></span>

<span data-ttu-id="5fe66-149">为了帮助确保通过使用同步无缝转换到 Office 365，您必须在开始 Office 365 目录同步部署之前准备 AD DS 林。</span><span class="sxs-lookup"><span data-stu-id="5fe66-149">To help ensure a seamless transition to Office 365 by using synchronization, you must prepare your AD DS forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="5fe66-150">在[Office 365 中设置目录同步](set-up-directory-synchronization.md)时，其中一个步骤是[下载并运行 IdFix 工具](install-and-run-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="5fe66-150">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="5fe66-151">您可以使用 IdFix 工具来帮助[清理目录](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="5fe66-151">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="5fe66-152">目录清理应侧重于以下任务：</span><span class="sxs-lookup"><span data-stu-id="5fe66-152">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="5fe66-153">删除重复的**proxyAddress**和**userPrincipalName**属性。</span><span class="sxs-lookup"><span data-stu-id="5fe66-153">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="5fe66-154">使用有效的**userprincipalname**属性更新空白和无效的**userprincipalname**属性。</span><span class="sxs-lookup"><span data-stu-id="5fe66-154">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="5fe66-155">删除**givenName**、姓（ **Sn** ）、 **sAMAccountName**、 **displayName**、 **mail**、 **proxyAddresses**、 **mailNickname**和**userPrincipalName**属性中的无效和可疑字符。</span><span class="sxs-lookup"><span data-stu-id="5fe66-155">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="5fe66-156">有关准备属性的详细信息，请参阅[由 Azure Active Directory 同步工具同步的属性列表](https://go.microsoft.com/fwlink/p/?LinkId=396719)。</span><span class="sxs-lookup"><span data-stu-id="5fe66-156">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="5fe66-157">这些属性与 Azure AD Connect 同步的属性相同。</span><span class="sxs-lookup"><span data-stu-id="5fe66-157">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="5fe66-158">多林部署注意事项</span><span class="sxs-lookup"><span data-stu-id="5fe66-158">Multi-forest deployment considerations</span></span>

<span data-ttu-id="5fe66-159">对于多个林和 SSO 选项，请使用[自定义安装的 AZURE AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="5fe66-159">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="5fe66-160">如果您的组织具有多个林进行身份验证（登录林），我们强烈建议您执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5fe66-160">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="5fe66-161">**请考虑合并你的林。**</span><span class="sxs-lookup"><span data-stu-id="5fe66-161">**Consider consolidating your forests.**</span></span> <span data-ttu-id="5fe66-162">通常情况下，维护多个林需要更多的开销。</span><span class="sxs-lookup"><span data-stu-id="5fe66-162">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="5fe66-163">除非您的组织具有规定单独林需求的安全约束，否则请考虑简化您的本地环境。</span><span class="sxs-lookup"><span data-stu-id="5fe66-163">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="5fe66-164">**仅在主登录林中使用。**</span><span class="sxs-lookup"><span data-stu-id="5fe66-164">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="5fe66-165">请考虑仅将 Office 365 部署到主登录林中，以实现 Office 365 的初始部署。</span><span class="sxs-lookup"><span data-stu-id="5fe66-165">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="5fe66-166">如果不能合并多林 AD DS 部署或使用其他目录服务来管理标识，则可以将它们与 Microsoft 或合作伙伴的帮助进行同步。</span><span class="sxs-lookup"><span data-stu-id="5fe66-166">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="5fe66-167">有关详细信息，请参阅[具有单一登录方案的多林目录同步](https://go.microsoft.com/fwlink/p/?LinkId=525321)。</span><span class="sxs-lookup"><span data-stu-id="5fe66-167">See [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="5fe66-168">依赖于目录同步的功能</span><span class="sxs-lookup"><span data-stu-id="5fe66-168">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="5fe66-169">以下特性和功能需要目录同步：</span><span class="sxs-lookup"><span data-stu-id="5fe66-169">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="5fe66-170">Azure AD 无缝单一登录（SSO）</span><span class="sxs-lookup"><span data-stu-id="5fe66-170">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="5fe66-171">Skype 共存</span><span class="sxs-lookup"><span data-stu-id="5fe66-171">Skype coexistence</span></span>
- <span data-ttu-id="5fe66-172">Exchange 混合部署，包括：</span><span class="sxs-lookup"><span data-stu-id="5fe66-172">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="5fe66-173">内部部署 Exchange 环境与 Office 365 之间的完全共享全局地址列表（GAL）。</span><span class="sxs-lookup"><span data-stu-id="5fe66-173">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="5fe66-174">同步不同邮件系统中的 GAL 信息。</span><span class="sxs-lookup"><span data-stu-id="5fe66-174">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="5fe66-175">在 Office 365 服务产品中添加和删除用户的功能。</span><span class="sxs-lookup"><span data-stu-id="5fe66-175">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="5fe66-176">这要求：</span><span class="sxs-lookup"><span data-stu-id="5fe66-176">This requires the following:</span></span>
  - <span data-ttu-id="5fe66-177">双向同步必须在目录同步安装过程中进行配置。</span><span class="sxs-lookup"><span data-stu-id="5fe66-177">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="5fe66-178">默认情况下，目录同步工具仅将目录信息写入云。</span><span class="sxs-lookup"><span data-stu-id="5fe66-178">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="5fe66-179">配置双向同步时，您可以启用写回功能，以便从云中复制有限数量的对象属性，然后将它们写回到本地 AD DS。</span><span class="sxs-lookup"><span data-stu-id="5fe66-179">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="5fe66-180">写回也称为 Exchange 混合模式。</span><span class="sxs-lookup"><span data-stu-id="5fe66-180">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="5fe66-181">内部部署 Exchange 混合部署</span><span class="sxs-lookup"><span data-stu-id="5fe66-181">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="5fe66-182">能够将一些用户邮箱移动到 Office 365，同时保留本地用户邮箱。</span><span class="sxs-lookup"><span data-stu-id="5fe66-182">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="5fe66-183">安全发件人和阻止内部的发件人将复制到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="5fe66-183">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="5fe66-184">基本委托和代表发送电子邮件功能。</span><span class="sxs-lookup"><span data-stu-id="5fe66-184">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="5fe66-185">您具有集成的本地智能卡或多重身份验证解决方案。</span><span class="sxs-lookup"><span data-stu-id="5fe66-185">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="5fe66-186">对照片、缩略图、会议室和安全组进行同步</span><span class="sxs-lookup"><span data-stu-id="5fe66-186">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="5fe66-187">后续步骤</span><span class="sxs-lookup"><span data-stu-id="5fe66-187">Next step</span></span>

<span data-ttu-id="5fe66-188">准备好部署混合标识时，请参阅[prepare to 预配用户](prepare-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="5fe66-188">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5fe66-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5fe66-189">See also</span></span>

[<span data-ttu-id="5fe66-190">Microsoft 365 企业版概述</span><span class="sxs-lookup"><span data-stu-id="5fe66-190">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

