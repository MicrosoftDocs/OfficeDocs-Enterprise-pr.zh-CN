---
title: 了解 Office 365 标识和 Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: 了解如何在 Office 365 中管理用户标识。
ms.openlocfilehash: 14d1ec8a3ebc4620a72f831c0ec80253f7b3072c
ms.sourcegitcommit: dcb57859ad40090cf70586ac350472eb0fc8d9c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2018
ms.locfileid: "25639631"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a><span data-ttu-id="9d0b0-103">了解 Office 365 标识和 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="9d0b0-103">Understanding Office 365 identity and Azure Active Directory</span></span>

<span data-ttu-id="9d0b0-p101">Office 365 使用的基于云的用户标识和身份验证服务 Azure Active Directory (Azure AD) 来管理用户。选择您的内部部署组织和 Office 365 之间配置标识管理早期的决策，是一种云基础结构的基础。由于更改了此配置稍后可能会变得比较困难，仔细考虑选项以确定哪些适合于组织的需要。您可以从 Office 365 中设置和管理用户帐户; 中的两个主要的身份验证模型**云身份验证**和**联合身份验证**。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-p101">Office 365 uses the cloud-based user identity and authentication service Azure Active Directory (Azure AD) to manage users. Choosing if identity management is configured between your on-premises organization and Office 365 is an early decision that is one of the foundations of your cloud infrastructure. Because changing this configuration later can be difficult, carefully consider the options to determine what works best for the needs of your organization. You can choose from two main authentication models in Office 365 to set up and manage user accounts; **cloud authentication** and **federated authentication**.</span></span>
  
<span data-ttu-id="9d0b0-p102">很重要仔细考虑哪这些身份验证和标识模型，用于启动和运行。考虑时间、 现有复杂性和成本实施和维护每个身份验证和标识选项。这些因素是不同的每个组织;您应了解您想要用于您的部署标识选项以帮助您选择的身份验证和标识模型的主要概念。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-p102">It's important to carefully consider which of these authentication and identity models to use to get up and running. Think about the time, existing complexity, and cost to implement and maintain each of the authentication and identity options. These factors are different for every organization; and you should understand the key concepts for the identity options to help you choose the authentication and identity model you want to use for your deployment.</span></span>
  
## <a name="cloud-authentication"></a><span data-ttu-id="9d0b0-111">云身份验证</span><span class="sxs-lookup"><span data-stu-id="9d0b0-111">Cloud authentication</span></span>

<span data-ttu-id="9d0b0-112">根据如果您具有或没有现有 Active Directory 环境内部部署，您可以通过多种方式来管理为与 Office 365 用户的身份验证和标识服务。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-112">Depending if you have or don't have an existing Active Directory environment on-premises, you have several options to manage authentication and identity services for your users with Office 365.</span></span>
  
### <a name="cloud-only"></a><span data-ttu-id="9d0b0-113">仅限云</span><span class="sxs-lookup"><span data-stu-id="9d0b0-113">Cloud-only</span></span>

<span data-ttu-id="9d0b0-p103">仅使用云的模型，您可以管理您只在 Office 365 中的用户帐户。不在本地服务器所需;它是所有处理在云中的 Azure AD。创建和管理 Office 365 管理中心中的用户或使用 Windows PowerShell [PowerShell cmdlet](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell)和标识和身份验证处理完全在云中的 Azure AD。仅使用云的模型通常很好的选项如果：</span><span class="sxs-lookup"><span data-stu-id="9d0b0-p103">With the cloud-only model, you manage your user accounts in Office 365 only. No on-premises servers are required; it's all handled in the cloud by Azure AD. You create and manage users in the Office 365 admin center or by using Windows PowerShell [PowerShell cmdlets](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) and identity and authentication are handled completely in the cloud by Azure AD. The cloud-only model is typically a good choice if:</span></span> 
  
- <span data-ttu-id="9d0b0-118">您有任何其他内部部署用户目录。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-118">You have no other on-premises user directory.</span></span>
    
- <span data-ttu-id="9d0b0-119">具有非常复杂的本地目录并且只是要避免工作与其集成。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-119">You have a very complex on-premises directory and simply want to avoid the work to integrate with it.</span></span>
    
- <span data-ttu-id="9d0b0-p104">您具有现有的内部部署目录，但您想要运行的试用版或 Office 365 试点。更高版本，您可以匹配到内部部署用户的云用户时即可连接到您的本地目录。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-p104">You have an existing on-premises directory, but you want to run a trial or pilot of Office 365. Later, you can match the cloud users to on-premises users when you are ready to connect to your on-premises directory.</span></span>
    
<span data-ttu-id="9d0b0-122">若要开始使用云身份，请参阅[设置为企业的 Office 365](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-122">To get started with cloud identity, see [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).</span></span>
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a><span data-ttu-id="9d0b0-123">与无缝单一登录的密码哈希同步</span><span class="sxs-lookup"><span data-stu-id="9d0b0-123">Password hash sync with seamless single sign-on</span></span>

<span data-ttu-id="9d0b0-p105">启用内部部署目录对象在 Azure AD 身份验证的最简单方法。使用密码哈希同步 (PHS)，您可以将您的本地 Active Directory 用户帐户对象与 Office 365 同步和管理用户内部部署。用户密码哈希同步从您的本地 Active Directory 到 Azure AD 以便用户具有相同密码内部部署和云中。当密码更改，或重置为本地时，新密码哈希同步到 Azure AD 以便用户可以始终使用相同的密码的云资源和本地资源。从不发送到 Azure AD 或存储在 Azure AD 以明文形式密码。Azure AD，如标识保护的某些高级功能需要的 PHS 无论哪些选择身份验证方法。与无缝单一登录，用户将自动登录到 Azure AD 他们在其企业设备并连接到企业网络。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-p105">The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises. Hashes of user passwords are synchronized from your on-premises Active Directory to Azure AD so that the users have the same password on-premises and in the cloud. When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources. The passwords are never sent to Azure AD or stored in Azure AD in clear text. Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected. With seamless single sign-on, users are automatically signed in to Azure AD when they are on their corporate devices and connected to your corporate network.</span></span>
  
<span data-ttu-id="9d0b0-131">了解有关[选择密码哈希同步](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)和[无缝单一登录](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-131">Learn more about [choosing password hash sync](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) and [seamless single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).</span></span>
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a><span data-ttu-id="9d0b0-132">传递身份验证与无缝单一登录</span><span class="sxs-lookup"><span data-stu-id="9d0b0-132">Pass-through authentication with seamless single sign-on</span></span>

<span data-ttu-id="9d0b0-p106">提供使用一个或多个本地服务器上运行的软件代理来验证直接与您的本地 Active Directory 用户的 Azure AD 身份验证服务的简单密码验证。使用传递身份验证 (PTA)，您可以与 Office 365 同步的本地 Active Directory 用户帐户对象和管理用户内部部署。允许用户登录到同时在本地和 Office 365 资源和应用程序使用其内部部署帐户和密码。此配置而不发送到 Office 365 密码哈希验证直接针对您的本地 Active Directory 的用户密码。立即强制在本地用户帐户的安全要求的公司状态，密码策略和登录时间会使用此身份验证方法。与无缝单一登录，用户将自动登录到 Azure AD 他们在其企业设备并连接到企业网络。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-p106">Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory. With pass-through authentication (PTA), you synchronize on-premises Active Directory user account objects with Office 365 and manage your users on-premises. Allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password. This configuration validates users passwords directly against your on-premises Active Directory without sending password hashes to Office 365. Companies with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours would use this authentication method. With seamless single sign-on, users are automatically signed in to Azure AD when they are on their corporate devices and connected to your corporate network.</span></span>
  
<span data-ttu-id="9d0b0-139">了解有关[选择传递身份验证](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)和[无缝单一登录](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-139">Learn more about [choosing pass-through authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) and [seamless single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).</span></span>
  
## <a name="federated-authentication-options"></a><span data-ttu-id="9d0b0-140">联合身份验证选项</span><span class="sxs-lookup"><span data-stu-id="9d0b0-140">Federated authentication options</span></span>

<span data-ttu-id="9d0b0-141">如果您具有现有 Active Directory 环境内部部署，您可以通过使用联合身份验证来管理 Office 365 中的用户的身份验证和标识服务与您的目录集成 Office 365。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-141">If you have an existing Active Directory environment on-premises, you can integrate Office 365 with your directory by using federated authentication to manage authentication and identity services for your users in Office 365.</span></span>
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a><span data-ttu-id="9d0b0-142">使用 Active Directory 联合身份验证服务 (AD FS) 联合的身份</span><span class="sxs-lookup"><span data-stu-id="9d0b0-142">Federated identity with Active Directory Federation Services (AD FS)</span></span>

<span data-ttu-id="9d0b0-p107">身份验证要求更复杂的大型企业组织，主要用于本地目录对象与 Office 365 同步和用户帐户是本地托管。使用 AD FS 用户具有相同密码内部部署和云中和不必再次登录以使用 Office 365。此联合身份验证模型可以提供额外的身份验证要求，例如基于智能卡身份验证或第三方多因素身份验证，且通常时必需组织具有身份验证要求本身并非支持 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-p107">Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises. With AD FS, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365. This federated authentication model can provide additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
  
<span data-ttu-id="9d0b0-146">了解有关[选择 with AD FS 联合的身份](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-146">Learn more about [choosing federated identity with AD FS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).</span></span>
  
### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="9d0b0-147">第三方身份验证和标识提供程序</span><span class="sxs-lookup"><span data-stu-id="9d0b0-147">Third-party authentication and identity providers</span></span>

<span data-ttu-id="9d0b0-p108">内部部署目录对象可能同步到 Office 365 和云资源访问主要由第三方身份提供程序 (IdP)。如果您的组织使用第三方联合身份验证解决方案，您可以配置单一登录与该将解决方案 for Office 365，前提是第三方联合身份验证解决方案是否与 Azure AD 兼容。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-p108">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP). If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="9d0b0-150">了解有关[Azure AD 联盟兼容性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-150">Learn more about [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).</span></span>
  
## <a name="configuring-identity-and-authentication-with-office-365"></a><span data-ttu-id="9d0b0-151">与 Office 365 配置标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="9d0b0-151">Configuring identity and authentication with Office 365</span></span>

<span data-ttu-id="9d0b0-p109">将内部部署目录集成与 Office 365 和 Azure AD 已得到简化了[Azure AD 连接](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。Azure AD 连接是连接您的目录的最佳方式，并且是同步到云用户组织的 Microsoft 的建议。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-p109">Integrating your on-premises directories with Office 365 and Azure AD has been simplified with [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Azure AD Connect is the best way to connect your directories and is Microsoft's recommendation for organizations to sync their users to the cloud.</span></span>
  
<span data-ttu-id="9d0b0-154">您还可以使用 Azure AD 顾问： [Azure AD 连接顾问](https://aka.ms/aadconnectpwsync)、 [AD FS 部署顾问](https://aka.ms/adfsguidance)和[Azure AD Premium 安装指南](https://aka.ms/aadpguidance)。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-154">You can also use the Azure AD advisors: the [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync), the [AD FS deployment advisor](https://aka.ms/adfsguidance), and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance).</span></span>
  
## <a name="video-training"></a><span data-ttu-id="9d0b0-155">视频培训</span><span class="sxs-lookup"><span data-stu-id="9d0b0-155">Video training</span></span>

<span data-ttu-id="9d0b0-156">有关详细信息，请参阅视频课程[Office 365： 管理标识使用 Azure AD 连接](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)，进入您的 LinkedIn 学习。</span><span class="sxs-lookup"><span data-stu-id="9d0b0-156">For more information, see the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>
