---
title: Microsoft 365 的混合标识和目录同步
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 06/09/2020
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
description: 介绍与 Microsoft 365、Active Directory 域服务清理和 Azure Active Directory Connect 工具的目录同步。
ms.openlocfilehash: ef7af68a65e4799e7bffbe6edba4f2b237a4d8b4
ms.sourcegitcommit: ff1d21fe5eb8eba7a65d250aa37aadc8f503a10a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "44698959"
---
# <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="5d123-103">Microsoft 365 的混合标识和目录同步</span><span class="sxs-lookup"><span data-stu-id="5d123-103">Hybrid identity and directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="5d123-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="5d123-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="5d123-105">根据您的业务需求和技术要求，混合身份模型和目录同步对于采用 Microsoft 365 的企业客户来说是最常见的选择。</span><span class="sxs-lookup"><span data-stu-id="5d123-105">Depending on your business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Microsoft 365.</span></span> <span data-ttu-id="5d123-106">目录同步允许您在 Active Directory 域服务（AD DS）中管理标识，对用户帐户、组和联系人的所有更新将同步到 Microsoft 365 订阅的 Azure Active Directory （Azure AD）租户。</span><span class="sxs-lookup"><span data-stu-id="5d123-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="5d123-107">首次同步 AD DS 用户帐户时，不会自动为其分配 Microsoft 365 许可证，也不能访问 Microsoft 365 服务（如电子邮件）。</span><span class="sxs-lookup"><span data-stu-id="5d123-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Microsoft 365 license and cannot access Microsoft 365 services, such as email.</span></span> <span data-ttu-id="5d123-108">您必须先为其分配使用位置。</span><span class="sxs-lookup"><span data-stu-id="5d123-108">You must first assign them a usage location.</span></span> <span data-ttu-id="5d123-109">然后，通过组成员身份单独或动态地为这些用户帐户分配许可证。</span><span class="sxs-lookup"><span data-stu-id="5d123-109">Then, assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="5d123-110">混合标识的身份验证</span><span class="sxs-lookup"><span data-stu-id="5d123-110">Authentication for hybrid identity</span></span>

<span data-ttu-id="5d123-111">使用混合标识模型时，有两种类型的身份验证：</span><span class="sxs-lookup"><span data-stu-id="5d123-111">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="5d123-112">托管身份验证</span><span class="sxs-lookup"><span data-stu-id="5d123-112">Managed authentication</span></span>

  <span data-ttu-id="5d123-113">Azure AD 通过使用密码的本地存储哈希版本或将凭据发送到内部部署 AD DS 进行身份验证的本地软件代理来处理身份验证过程。</span><span class="sxs-lookup"><span data-stu-id="5d123-113">Azure AD handles the authentication process by using a locally-stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="5d123-114">联合身份验证</span><span class="sxs-lookup"><span data-stu-id="5d123-114">Federated authentication</span></span>

  <span data-ttu-id="5d123-115">Azure AD 将请求身份验证的客户端计算机重定向到另一个标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="5d123-115">Azure AD redirects the client computer requesting authentication to another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="5d123-116">托管身份验证</span><span class="sxs-lookup"><span data-stu-id="5d123-116">Managed authentication</span></span>

<span data-ttu-id="5d123-117">有两种类型的托管身份验证：</span><span class="sxs-lookup"><span data-stu-id="5d123-117">There are two types of managed authentication:</span></span>

- <span data-ttu-id="5d123-118">密码哈希同步（PHS）</span><span class="sxs-lookup"><span data-stu-id="5d123-118">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="5d123-119">Azure AD 执行身份验证本身。</span><span class="sxs-lookup"><span data-stu-id="5d123-119">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="5d123-120">直通身份验证 (PTA)</span><span class="sxs-lookup"><span data-stu-id="5d123-120">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="5d123-121">Azure AD 具有 AD DS 执行身份验证。</span><span class="sxs-lookup"><span data-stu-id="5d123-121">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization-phs"></a><span data-ttu-id="5d123-122">密码哈希同步（PHS）</span><span class="sxs-lookup"><span data-stu-id="5d123-122">Password hash synchronization (PHS)</span></span>

<span data-ttu-id="5d123-123">使用 PHS，您可以将 AD DS 用户帐户与 Microsoft 365 同步并在本地管理您的用户。</span><span class="sxs-lookup"><span data-stu-id="5d123-123">With PHS, you synchronize your AD DS user accounts with Microsoft 365 and manage your users on-premises.</span></span> <span data-ttu-id="5d123-124">用户密码的哈希将从你的 AD DS 同步到 Azure AD，以便用户在本地和在云中具有相同的密码。</span><span class="sxs-lookup"><span data-stu-id="5d123-124">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="5d123-125">这是在 Azure AD 中为 AD DS 标识启用身份验证的最简单方法。</span><span class="sxs-lookup"><span data-stu-id="5d123-125">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![密码哈希同步（PHS）](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="5d123-127">更改密码或在本地重置密码时，新的密码哈希将同步到 Azure AD，以便您的用户始终可以对云资源和本地资源使用相同的密码。</span><span class="sxs-lookup"><span data-stu-id="5d123-127">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="5d123-128">用户密码永远不会发送到 Azure AD 或以明文形式存储在 Azure AD 中。</span><span class="sxs-lookup"><span data-stu-id="5d123-128">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="5d123-129">Azure AD 的一些高级功能（如标识保护）需要 PHS，而不管选择了哪种身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="5d123-129">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="5d123-130">若要了解详细信息，请参阅[选择正确的身份验证方法](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn)。</span><span class="sxs-lookup"><span data-stu-id="5d123-130">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication-pta"></a><span data-ttu-id="5d123-131">直通身份验证 (PTA)</span><span class="sxs-lookup"><span data-stu-id="5d123-131">Pass-through authentication (PTA)</span></span>

<span data-ttu-id="5d123-132">PTA 提供了使用在一个或多个本地服务器上运行的软件代理直接通过 AD DS 验证用户的 Azure AD 身份验证服务的简单密码验证。</span><span class="sxs-lookup"><span data-stu-id="5d123-132">PTA provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="5d123-133">使用 PTA，您可以将 AD DS 用户帐户与 Microsoft 365 同步并在本地管理您的用户。</span><span class="sxs-lookup"><span data-stu-id="5d123-133">With PTA, you synchronize AD DS user accounts with Microsoft 365 and manage your users on-premises.</span></span> 

![直通身份验证 (PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="5d123-135">PTA 允许您的用户使用其内部部署帐户和密码登录到本地和 Microsoft 365 资源和应用程序。</span><span class="sxs-lookup"><span data-stu-id="5d123-135">PTA allows your users to sign in to both on-premises and Microsoft 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="5d123-136">此配置将直接对本地 AD DS 验证用户密码，而无需在 Azure AD 中存储密码哈希。</span><span class="sxs-lookup"><span data-stu-id="5d123-136">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="5d123-137">PTA 也适用于具有安全要求的组织，以立即强制实施本地用户帐户状态、密码策略和登录时间。</span><span class="sxs-lookup"><span data-stu-id="5d123-137">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="5d123-138">若要了解详细信息，请参阅[选择正确的身份验证方法](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn)。</span><span class="sxs-lookup"><span data-stu-id="5d123-138">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="5d123-139">联合身份验证</span><span class="sxs-lookup"><span data-stu-id="5d123-139">Federated authentication</span></span>

<span data-ttu-id="5d123-140">联合身份验证主要针对具有更复杂的身份验证要求的大型企业组织。</span><span class="sxs-lookup"><span data-stu-id="5d123-140">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="5d123-141">AD DS 标识与 Microsoft 365 同步，并且用户帐户在本地进行管理。</span><span class="sxs-lookup"><span data-stu-id="5d123-141">AD DS identities are synchronized with Microsoft 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="5d123-142">使用联合身份验证，用户在本地和在云中具有相同的密码，且无需再次登录才能使用 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="5d123-142">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Microsoft 365.</span></span> 

<span data-ttu-id="5d123-143">联合身份验证可支持其他身份验证要求（如基于智能卡的身份验证或第三方多重身份验证），通常需要在组织具有 Azure AD 本身不支持的身份验证要求时。</span><span class="sxs-lookup"><span data-stu-id="5d123-143">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="5d123-144">若要了解详细信息，请参阅[选择正确的身份验证方法](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn)。</span><span class="sxs-lookup"><span data-stu-id="5d123-144">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="5d123-145">第三方身份验证和标识提供程序</span><span class="sxs-lookup"><span data-stu-id="5d123-145">Third-party authentication and identity providers</span></span>

<span data-ttu-id="5d123-146">本地目录对象可能会同步到 Microsoft 365，并且云资源访问主要由第三方标识提供程序（IdP）进行管理。</span><span class="sxs-lookup"><span data-stu-id="5d123-146">On-premises directory objects may be synchronized to Microsoft 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="5d123-147">如果您的组织使用第三方联合解决方案，则可以使用适用于 Microsoft 365 的解决方案配置登录，前提是第三方联合解决方案与 Azure AD 兼容。</span><span class="sxs-lookup"><span data-stu-id="5d123-147">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Microsoft 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="5d123-148">若要了解详细信息，请参阅[AZURE AD 联合身份验证兼容性列表](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)。</span><span class="sxs-lookup"><span data-stu-id="5d123-148">See the [Azure AD federation compatibility list](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="5d123-149">AD DS 清理</span><span class="sxs-lookup"><span data-stu-id="5d123-149">AD DS Cleanup</span></span>

<span data-ttu-id="5d123-150">为了帮助确保通过使用同步无缝转换到 Microsoft 365，您必须在开始 Microsoft 365 目录同步部署之前准备 AD DS 林。</span><span class="sxs-lookup"><span data-stu-id="5d123-150">To help ensure a seamless transition to Microsoft 365 by using synchronization, you must prepare your AD DS forest before you begin your Microsoft 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="5d123-151">[设置目录同步](set-up-directory-synchronization.md)时，其中一个步骤是[下载并运行 IdFix 工具](install-and-run-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="5d123-151">When you [set up directory synchronization](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="5d123-152">您可以使用 IdFix 工具来帮助[清理目录](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="5d123-152">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="5d123-153">目录清理应侧重于以下任务：</span><span class="sxs-lookup"><span data-stu-id="5d123-153">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="5d123-154">删除重复的**proxyAddress**和**userPrincipalName**属性。</span><span class="sxs-lookup"><span data-stu-id="5d123-154">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="5d123-155">使用有效的**userprincipalname**属性更新空白和无效的**userprincipalname**属性。</span><span class="sxs-lookup"><span data-stu-id="5d123-155">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="5d123-156">删除**givenName**、姓（ **Sn** ）、 **sAMAccountName**、 **displayName**、 **mail**、 **proxyAddresses**、 **mailNickname**和**userPrincipalName**属性中的无效和可疑字符。</span><span class="sxs-lookup"><span data-stu-id="5d123-156">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="5d123-157">有关准备属性的详细信息，请参阅[由 Azure Active Directory 同步工具同步的属性列表](https://go.microsoft.com/fwlink/p/?LinkId=396719)。</span><span class="sxs-lookup"><span data-stu-id="5d123-157">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="5d123-158">这些属性与 Azure AD Connect 同步的属性相同。</span><span class="sxs-lookup"><span data-stu-id="5d123-158">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="5d123-159">多林部署注意事项</span><span class="sxs-lookup"><span data-stu-id="5d123-159">Multi-forest deployment considerations</span></span>

<span data-ttu-id="5d123-160">对于多个林和 SSO 选项，请使用[AZURE AD Connect 的自定义安装](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="5d123-160">For multiple forests and SSO options, use a [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="5d123-161">如果您的组织具有多个林进行身份验证（登录林），我们强烈建议您执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5d123-161">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="5d123-162">**请考虑合并你的林。**</span><span class="sxs-lookup"><span data-stu-id="5d123-162">**Consider consolidating your forests.**</span></span> <span data-ttu-id="5d123-163">通常情况下，维护多个林需要更多的开销。</span><span class="sxs-lookup"><span data-stu-id="5d123-163">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="5d123-164">除非您的组织具有规定单独林需求的安全约束，否则请考虑简化您的本地环境。</span><span class="sxs-lookup"><span data-stu-id="5d123-164">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="5d123-165">**仅在主登录林中使用。**</span><span class="sxs-lookup"><span data-stu-id="5d123-165">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="5d123-166">请考虑仅将 Microsoft 365 部署在你的主登录林中，以供 Microsoft 365 的初始部署。</span><span class="sxs-lookup"><span data-stu-id="5d123-166">Consider deploying Microsoft 365 only in your primary logon forest for your initial rollout of Microsoft 365.</span></span> 

<span data-ttu-id="5d123-167">如果不能合并多林 AD DS 部署或使用其他目录服务来管理标识，则可以将它们与 Microsoft 或合作伙伴的帮助进行同步。</span><span class="sxs-lookup"><span data-stu-id="5d123-167">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="5d123-168">有关详细信息，请参阅[AZURE AD Connect 的拓扑](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies)。</span><span class="sxs-lookup"><span data-stu-id="5d123-168">See [Topologies for Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="5d123-169">依赖于目录同步的功能</span><span class="sxs-lookup"><span data-stu-id="5d123-169">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="5d123-170">以下特性和功能需要目录同步：</span><span class="sxs-lookup"><span data-stu-id="5d123-170">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="5d123-171">Azure AD 无缝单一登录（SSO）</span><span class="sxs-lookup"><span data-stu-id="5d123-171">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="5d123-172">Skype 共存</span><span class="sxs-lookup"><span data-stu-id="5d123-172">Skype coexistence</span></span>
- <span data-ttu-id="5d123-173">Exchange 混合部署，包括：</span><span class="sxs-lookup"><span data-stu-id="5d123-173">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="5d123-174">内部部署 Exchange 环境与 Microsoft 365 之间的完全共享全局地址列表（GAL）。</span><span class="sxs-lookup"><span data-stu-id="5d123-174">Fully shared global address list (GAL) between your on-premises Exchange environment and Microsoft 365.</span></span>
  - <span data-ttu-id="5d123-175">同步不同邮件系统中的 GAL 信息。</span><span class="sxs-lookup"><span data-stu-id="5d123-175">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="5d123-176">在 Microsoft 365 服务产品中添加和删除用户的功能。</span><span class="sxs-lookup"><span data-stu-id="5d123-176">The ability to add users to and remove users from Microsoft 365 service offerings.</span></span> <span data-ttu-id="5d123-177">这要求：</span><span class="sxs-lookup"><span data-stu-id="5d123-177">This requires the following:</span></span>
  - <span data-ttu-id="5d123-178">双向同步必须在目录同步安装过程中进行配置。</span><span class="sxs-lookup"><span data-stu-id="5d123-178">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="5d123-179">默认情况下，目录同步工具仅将目录信息写入云。</span><span class="sxs-lookup"><span data-stu-id="5d123-179">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="5d123-180">配置双向同步时，您可以启用写回功能，以便从云中复制有限数量的对象属性，然后将它们写回到本地 AD DS。</span><span class="sxs-lookup"><span data-stu-id="5d123-180">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="5d123-181">写回也称为 Exchange 混合模式。</span><span class="sxs-lookup"><span data-stu-id="5d123-181">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="5d123-182">内部部署 Exchange 混合部署</span><span class="sxs-lookup"><span data-stu-id="5d123-182">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="5d123-183">能够将一些用户邮箱移动到 Microsoft 365，同时保留本地用户邮箱。</span><span class="sxs-lookup"><span data-stu-id="5d123-183">The ability to move some user mailboxes to Microsoft 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="5d123-184">安全发件人和阻止内部的发件人将复制到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="5d123-184">Safe senders and blocked senders on-premises are replicated to Microsoft 365.</span></span>
  - <span data-ttu-id="5d123-185">基本委托和代表发送电子邮件功能。</span><span class="sxs-lookup"><span data-stu-id="5d123-185">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="5d123-186">您具有集成的本地智能卡或多重身份验证解决方案。</span><span class="sxs-lookup"><span data-stu-id="5d123-186">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="5d123-187">对照片、缩略图、会议室和安全组进行同步</span><span class="sxs-lookup"><span data-stu-id="5d123-187">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="5d123-188">后续步骤</span><span class="sxs-lookup"><span data-stu-id="5d123-188">Next step</span></span>

<span data-ttu-id="5d123-189">准备好部署混合标识时，请参阅[prepare to 预配用户](prepare-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="5d123-189">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5d123-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d123-190">See also</span></span>

[<span data-ttu-id="5d123-191">Microsoft 365 企业版概述</span><span class="sxs-lookup"><span data-stu-id="5d123-191">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

