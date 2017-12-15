---
title: "企业级结构设计版的 Microsoft 云标识"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- O365ITProTrain
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "摘要： 设计用于 Microsoft 云服务和平台的标识解决方案。"
ms.openlocfilehash: f581711345b043d61de503360d101fbcc09de82e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="microsoft-cloud-identity-for-enterprise-architects"></a><span data-ttu-id="72af2-103">企业级结构设计版的 Microsoft 云标识</span><span class="sxs-lookup"><span data-stu-id="72af2-103">Microsoft Cloud Identity for Enterprise Architects</span></span>

 <span data-ttu-id="72af2-104">**摘要：** 设计用于 Microsoft 云服务和平台的标识解决方案。</span><span class="sxs-lookup"><span data-stu-id="72af2-104">**Summary:** Design your identity solution for Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="72af2-p101">本文介绍 IT 架构师为使用 Microsoft 云服务和平台的组织设计标识所需要了解的内容。此外，您还可以使用 5 页海报的形式浏览本文，以文摘格式进行打印（也称为分类帐，11 x 17 或 A3)。</span><span class="sxs-lookup"><span data-stu-id="72af2-p101">This article describes what IT architects need to know about designing identity for organizations using Microsoft cloud services and platforms. You can also view this article as a 5-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="72af2-107">[![Microsoft 云标识模型的缩略图图像](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="72af2-107">[![Thumb image for Microsoft cloud identity model](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="72af2-108">![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![参阅包含其他语言版本的页面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多语言](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="72af2-108">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![See a page with versions in additional languages](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="72af2-109">此外可以查看所有[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)中的模型，然后通过刷卡[Microsoft 的企业云路线图： IT 决策者的资源](https://aka.ms/cloudarchitecture)。</span><span class="sxs-lookup"><span data-stu-id="72af2-109">You can also see all of the models in the [Microsoft Cloud IT architecture resources](microsoft-cloud-it-architecture-resources.md) and swipe through [Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture).</span></span>
  
> [!NOTE]
> <span data-ttu-id="72af2-p102">这篇文章反映了**企业架构师的 Microsoft 云标识**标牌的 2016 年 1 月版。它不包含 4 月 2016 年更改或更高版本的海报。</span><span class="sxs-lookup"><span data-stu-id="72af2-p102">This article reflects the January 2016 version of the **Microsoft cloud identity for enterprise architects** poster. It does not contain the changes for the April 2016 or later versions of the poster.</span></span>
  
## <a name="designing-identity-for-the-microsoft-cloud"></a><span data-ttu-id="72af2-112">设计用于 Microsoft 云的标识</span><span class="sxs-lookup"><span data-stu-id="72af2-112">Designing identity for the Microsoft cloud</span></span>

<span data-ttu-id="72af2-p103">通过将您的标识与 Microsoft 云进行集成，您将能够访问广泛的服务和云平台选项。有两个主要选项：</span><span class="sxs-lookup"><span data-stu-id="72af2-p103">Integrating your identities with the Microsoft cloud provides access to a broad range of services and cloud platform options. There are two main options:</span></span>
  
- <span data-ttu-id="72af2-p104">您可以与 Microsoft Azure Active Directory (AD) 集成。这涉及将您的本地帐户同步到 Azure AD，这是适用于 Microsoft 云的标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="72af2-p104">You can integrate with Microsoft Azure Active Directory (AD). This involves synchronizing your on-premises accounts to Azure AD, the identity provider for the Microsoft cloud.</span></span>
    
- <span data-ttu-id="72af2-117">您可以将您的本地 Active Directory 域服务 (AD DS) 环境扩展到在 Microsoft Azure 基础结构服务中运行的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="72af2-117">You can extend your on-premises Active Directory Domain Services (AD DS) environment to virtual machines running in Microsoft Azure infrastructure services.</span></span>
    
![在云中设计您的标识的选项](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 <span data-ttu-id="72af2-119">**图 1：用于在云中设计您的标识的选项**</span><span class="sxs-lookup"><span data-stu-id="72af2-119">**Figure 1: Options for designing your identities in the cloud**</span></span>
  
<span data-ttu-id="72af2-120">图 1 显示了 Azure AD 如何成为 Microsoft 服务型软件 (SaaS) 服务和 Azure 平台即服务 (PaaS) 应用程序的标识提供程序，以及业务线应用程序如何使用本地 AD DS。</span><span class="sxs-lookup"><span data-stu-id="72af2-120">Figure 1 shows how Azure AD is the identity provider for Microsoft Software as a Service (SaaS) services and Azure Platform as a Service (PaaS) applications and how line-of-business applications can use on-premises AD DS.</span></span> 
  
### <a name="azure-active-directory"></a><span data-ttu-id="72af2-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="72af2-121">Azure Active Directory</span></span>

<span data-ttu-id="72af2-p105">Microsoft Azure AD 是 Microsoft 云托管标识并且可以访问管理服务。它位于 Microsoft 云服务和平台的中心。通过与 Azure AD 进行集成，您将能够使用当前帐户和密码集访问所有 Microsoft SaaS 服务。该集成还为 Azure PaaS 应用程序提供基于云的标识。</span><span class="sxs-lookup"><span data-stu-id="72af2-p105">Microsoft Azure AD is the Microsoft cloud-hosted identity and access management service. It's at the center of Microsoft cloud services and platforms. Integrating with Azure AD provides access to all of the Microsoft SaaS services using your current set of accounts and passwords. That integration also provides cloud-based identity for Azure PaaS applications.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="72af2-126">Azure AD 不能替代企业组织或在 Azure 服务架构 (IaaS) 中运行的基于 Windows 的虚拟机对本地 AD DS 的需求。</span><span class="sxs-lookup"><span data-stu-id="72af2-126">Azure AD does not replace the need for AD DS on-premises for enterprise organizations or for Windows -based virtual machines running in Azure Infrastructure as a Service (IaaS).</span></span> 
  
<span data-ttu-id="72af2-127">有三个版本的 Azure AD:免费版、基本版和高级版。</span><span class="sxs-lookup"><span data-stu-id="72af2-127">There are three editions of Azure AD: Free, Basic, and Premium.</span></span> 
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="72af2-128">**免费**</span><span class="sxs-lookup"><span data-stu-id="72af2-128">**Free**</span></span> <br/> |<span data-ttu-id="72af2-129">**基本**</span><span class="sxs-lookup"><span data-stu-id="72af2-129">**Basic**</span></span> <br/> |<span data-ttu-id="72af2-130">**高级**</span><span class="sxs-lookup"><span data-stu-id="72af2-130">**Premium**</span></span> <br/> |
| <span data-ttu-id="72af2-131">管理用户帐户</span><span class="sxs-lookup"><span data-stu-id="72af2-131">Manage user accounts</span></span> <br/>  <span data-ttu-id="72af2-132">与本地目录同步</span><span class="sxs-lookup"><span data-stu-id="72af2-132">Synchronize with on-premises directories</span></span> <br/>  <span data-ttu-id="72af2-133">跨 Azure、Office 365 和数以千计的其他流行 SaaS 应用程序（如 Salesforce、Workday、Concur、DocuSign、Google Apps、Box、ServiceNow、Dropbox 等）单一登录</span><span class="sxs-lookup"><span data-stu-id="72af2-133">Single sign-on across Azure, Office 365, and thousands of other popular SaaS applications, such as Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more</span></span> <br/> | <span data-ttu-id="72af2-134">包括免费版的所有功能，外加：</span><span class="sxs-lookup"><span data-stu-id="72af2-134">Includes all of the abilities in the Free edition, plus:</span></span> <br/>  <span data-ttu-id="72af2-135">公司品牌</span><span class="sxs-lookup"><span data-stu-id="72af2-135">Company branding</span></span> <br/>  <span data-ttu-id="72af2-136">基于组的应用程序访问</span><span class="sxs-lookup"><span data-stu-id="72af2-136">Group-based application access</span></span> <br/>  <span data-ttu-id="72af2-137">自助服务密码重置</span><span class="sxs-lookup"><span data-stu-id="72af2-137">Self-service password reset</span></span> <br/>  <span data-ttu-id="72af2-138">99.9% 的企业 SLA</span><span class="sxs-lookup"><span data-stu-id="72af2-138">Enterprise SLA of 99.9%</span></span> <br/> | <span data-ttu-id="72af2-139">包括免费版和基本版的所有功能，外加:</span><span class="sxs-lookup"><span data-stu-id="72af2-139">Includes all of the features of the Free and Basic editions, plus:</span></span> <br/>  <span data-ttu-id="72af2-140">自助服务组管理</span><span class="sxs-lookup"><span data-stu-id="72af2-140">Self-service group management</span></span> <br/>  <span data-ttu-id="72af2-141">高级安全报告和警报</span><span class="sxs-lookup"><span data-stu-id="72af2-141">Advanced security reports and alerts</span></span> <br/>  <span data-ttu-id="72af2-142">多重身份验证</span><span class="sxs-lookup"><span data-stu-id="72af2-142">Multi-factor authentication</span></span> <br/>  <span data-ttu-id="72af2-143">通过回写到本地 AD DS 重置密码</span><span class="sxs-lookup"><span data-stu-id="72af2-143">Password reset with write-back to on-premises AD DS</span></span> <br/>  <span data-ttu-id="72af2-144">Azure AD Connect 工具双向同步</span><span class="sxs-lookup"><span data-stu-id="72af2-144">Azure AD Connect tool bidirectional synchronization</span></span> <br/>  <span data-ttu-id="72af2-145">Azure AD 应用程序代理</span><span class="sxs-lookup"><span data-stu-id="72af2-145">Azure AD Application Proxy</span></span> <br/>  <span data-ttu-id="72af2-146">Microsoft Forefront Identity Manager (MIM)</span><span class="sxs-lookup"><span data-stu-id="72af2-146">Microsoft Forefront Identity Manager (MIM)</span></span> <br/> |
   
<span data-ttu-id="72af2-147">有关这些版本的详细信息，请参阅 [Azure Active Directory 版本](https://go.microsoft.com/fwlink/p/?LinkId=524280)。</span><span class="sxs-lookup"><span data-stu-id="72af2-147">For more information about versions, see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
### <a name="option-1-integrate-with-azure-active-directory"></a><span data-ttu-id="72af2-148">选项 1：与 Azure Active Directory 集成</span><span class="sxs-lookup"><span data-stu-id="72af2-148">Option 1: Integrate with Azure Active Directory</span></span>

<span data-ttu-id="72af2-p106">大多数组织将一组标准对象和属性同步到他们的 Azure AD 租户。Azure AD Connect 工具在本地 AD DS 和 Azure AD 租户之间同步您的帐户。</span><span class="sxs-lookup"><span data-stu-id="72af2-p106">Most organizations synchronize a standard set of objects and attributes to their Azure AD tenant. The Azure AD Connect tool synchronizes your accounts between on-premises AD DS and an Azure AD tenant.</span></span>
  
![与 Azure AD 集成](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 <span data-ttu-id="72af2-152">**图 2：与 Azure AD 集成**</span><span class="sxs-lookup"><span data-stu-id="72af2-152">**Figure 2: Integrating with Azure AD**</span></span>
  
<span data-ttu-id="72af2-p107">图 2 显示了 Azure AD Connect 工具如何获取 AD DS 更改，并将这些更改发送到 Azure AD 租户。在这种情况下，Azure AD 租户是基本本地目录内容的云托管副本。</span><span class="sxs-lookup"><span data-stu-id="72af2-p107">Figure 2 shows how the Azure AD Connect tool obtains AD DS changes and sends them to your Azure AD tenant. In this case, your Azure AD tenant is a cloud-hosted duplicate of essential on-premises directory content.</span></span>
  
<span data-ttu-id="72af2-p108">许多组织使用 AD DS 作为其本地标识提供程序。您可以使用不同类型的本地标识提供程序（例如，使用 LDAP 的本地标识提供程序），并将它们同步到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="72af2-p108">Many organizations use AD DS as their on-premises identity provider. You can use a different type of identity provider on-premises (such as one that uses LDAP), and synchronize these to Azure AD.</span></span>
  
### <a name="option-2-extend-ad-ds-to-azure"></a><span data-ttu-id="72af2-157">选项 2：将 AD DS 扩展到 Azure</span><span class="sxs-lookup"><span data-stu-id="72af2-157">Option 2: Extend AD DS to Azure</span></span>

<span data-ttu-id="72af2-p109">将 AD DS 扩展到在 Azure 基础结构服务中运行的虚拟机这一操作支持一组与同步到 Azure AD 不同的解决方案和应用程序。有两种支持方式：</span><span class="sxs-lookup"><span data-stu-id="72af2-p109">Extending AD DS to virtual machines running in Azure infrastructure services supports a different set of solutions and applications compared to synchronization with Azure AD. Here are two:</span></span>
  
- <span data-ttu-id="72af2-160">支持基于云的解决方案，这些解决方案需要 NTLM 或 Kerberos 身份验证或加入 AD DS 域的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="72af2-160">Supports cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="72af2-161">为跨 Microsoft 云服务和平台的云服务和应用程序添加其他潜在的集成。</span><span class="sxs-lookup"><span data-stu-id="72af2-161">Adds additional integration potential for cloud services and applications across Microsoft cloud services and platforms.</span></span>
    
![将 AD DS 扩展到 Azure](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 <span data-ttu-id="72af2-163">**图 3：将 AD DS 扩展到 Azure**</span><span class="sxs-lookup"><span data-stu-id="72af2-163">**Figure 3: Extending AD DS to Azure**</span></span>
  
<span data-ttu-id="72af2-p110">图 3 显示了通过本地 VPN 设备和 Azure VPN 网关将 AD DS 域控制器连接到 Azure 虚拟网络。Azure 虚拟网络包含业务线应用程序及其自己的一组 AD DS 域控制器的服务器。</span><span class="sxs-lookup"><span data-stu-id="72af2-p110">Figure 3 shows an AD DS domain controller connected to an Azure virtual network through an on-premises VPN device and an Azure VPN gateway. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers.</span></span>
  
### <a name="more-information"></a><span data-ttu-id="72af2-166">详细信息</span><span class="sxs-lookup"><span data-stu-id="72af2-166">More Information</span></span>

- [<span data-ttu-id="72af2-167">通过 Office 365 同步目录简单易行</span><span class="sxs-lookup"><span data-stu-id="72af2-167">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="72af2-168">信息图：云标识和访问管理</span><span class="sxs-lookup"><span data-stu-id="72af2-168">Infographic: Cloud identity and access management</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [<span data-ttu-id="72af2-169">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="72af2-169">Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## <a name="integrate-your-on-premises-ad-ds-accounts-with-microsoft-azure-ad"></a><span data-ttu-id="72af2-170">使用 Microsoft Azure AD 集成您的本地 AD DS 帐户</span><span class="sxs-lookup"><span data-stu-id="72af2-170">Integrate your on-premises AD DS accounts with Microsoft Azure AD</span></span>

<span data-ttu-id="72af2-171">通过将您的本地 AD DS 帐户与 Azure AD 同步，您的用户可以使用他们的本地 AD DS 帐户访问以下内容：</span><span class="sxs-lookup"><span data-stu-id="72af2-171">By synchronizing your on-premises AD DS accounts with Azure AD, your users can use their on-premises AD DS accounts to access:</span></span>
  
- <span data-ttu-id="72af2-172">所有 Microsoft SaaS 服务（Office 365、Microsoft Intune 和 Dynamics CRM Online）</span><span class="sxs-lookup"><span data-stu-id="72af2-172">All of the Microsoft SaaS services (Office 365, Microsoft Intune, and Dynamics CRM Online)</span></span>
    
- <span data-ttu-id="72af2-173">在 Azure PaaS 中运行的应用程序</span><span class="sxs-lookup"><span data-stu-id="72af2-173">Your applications running in Azure PaaS</span></span>
    
<span data-ttu-id="72af2-174">配置此集成的方法有两种：</span><span class="sxs-lookup"><span data-stu-id="72af2-174">There are two ways to configure this integration:</span></span>
  
- <span data-ttu-id="72af2-175">目录和密码同步</span><span class="sxs-lookup"><span data-stu-id="72af2-175">Directory and password synchronization</span></span>
    
- <span data-ttu-id="72af2-176">联合身份验证和单一登录</span><span class="sxs-lookup"><span data-stu-id="72af2-176">Federation and single sign-on</span></span>
    
<span data-ttu-id="72af2-p111">从满足您需求的最简单选项入手。如果需要，您可以这些选项之间切换。</span><span class="sxs-lookup"><span data-stu-id="72af2-p111">Start with the simplest option that meets your needs. You can switch between these options, if needed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="72af2-179">不建议企业规模组织使用云专用帐户（即，不与您的本地 AD DS 集成）。</span><span class="sxs-lookup"><span data-stu-id="72af2-179">Using cloud-only accounts (not integrating with your on-premises AD DS) is not recommended for enterprise-scale organizations.</span></span> 
  
### <a name="directory-and-password-synchronization"></a><span data-ttu-id="72af2-180">目录和密码同步</span><span class="sxs-lookup"><span data-stu-id="72af2-180">Directory and password synchronization</span></span>

<span data-ttu-id="72af2-181">这是最简单的选项，仅需要一台运行 Azure AD Connect 工具的服务器。</span><span class="sxs-lookup"><span data-stu-id="72af2-181">This is the simplest option and requires only a server running the Azure AD Connect tool.</span></span> 
  
![目录和密码同步配置](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 <span data-ttu-id="72af2-183">**图 4：目录和密码同步配置**</span><span class="sxs-lookup"><span data-stu-id="72af2-183">**Figure 4: Directory and password synchronization configuration**</span></span>
  
<span data-ttu-id="72af2-p112">图 4 显示了带有 AD DS 域控制器的本地或私有云数据中心。运行 Azure AD Connect 工具的服务器会将帐户名称列表与 Azure AD 同步。</span><span class="sxs-lookup"><span data-stu-id="72af2-p112">Figure 4 shows an on-premises or private cloud datacenter with an AD DS domain controller. A server running the Azure AD Connect tool synchronizes the list of account names with Azure AD.</span></span>
  
<span data-ttu-id="72af2-186">使用此选项，您可以实现以下功能：</span><span class="sxs-lookup"><span data-stu-id="72af2-186">With this option:</span></span>
  
- <span data-ttu-id="72af2-p113">将用户帐户从您的本地 AD DS（或其他标识提供程序）同步到您的 Azure AD 租户。本地目录仍是帐户的权威来源，并且您可以从中管理所有帐户更改。</span><span class="sxs-lookup"><span data-stu-id="72af2-p113">User accounts are synchronized from your on-premises AD DS (or other identity provider) to your Azure AD tenant. The on-premises directory remains the authoritative source for accounts and you manage all account changes from there.</span></span>
    
- <span data-ttu-id="72af2-189">Azure AD 为基于 Microsoft SaaS 的服务和 Azure PaaS 应用程序执行所有的身份验证。</span><span class="sxs-lookup"><span data-stu-id="72af2-189">Azure AD performs all authentication for Microsoft SaaS-based services and Azure PaaS applications.</span></span>
    
- <span data-ttu-id="72af2-190">您还可以为多个 AD DS 林配置同步。</span><span class="sxs-lookup"><span data-stu-id="72af2-190">You can also configure synchronization for multiple AD DS forests.</span></span>
    
<span data-ttu-id="72af2-191">使用密码同步，您可以实现以下功能：</span><span class="sxs-lookup"><span data-stu-id="72af2-191">With password synchronization:</span></span>
  
- <span data-ttu-id="72af2-192">在用户访问云服务时将提示用户输入密码，该密码为他们访问本地资源所用的相同密码。</span><span class="sxs-lookup"><span data-stu-id="72af2-192">Users are prompted to enter a password when accessing cloud services, which is the same password that they use for on-premises resources.</span></span>
    
- <span data-ttu-id="72af2-p114">用户密码永远不会以明文形式发送到 Azure AD，而会使用密码的哈希形式。从加密的角度而言，对密码哈希进行解密或反向工程处理并获取明文密码是不可能的。</span><span class="sxs-lookup"><span data-stu-id="72af2-p114">User passwords are never sent as cleartext to Azure AD. Instead, a hash of the password is used. It is cryptographically impossible to decrypt or reverse-engineer the password hash and obtain the cleartext password.</span></span> 
    
<span data-ttu-id="72af2-196">使用多重身份验证 (MFA)，您可以实现以下功能：</span><span class="sxs-lookup"><span data-stu-id="72af2-196">With multi-factor authentication (MFA):</span></span>
  
- <span data-ttu-id="72af2-197">利用 Office 365 提供的基本 MFA 功能。</span><span class="sxs-lookup"><span data-stu-id="72af2-197">You can take advantage of basic MFA features offered with Office 365.</span></span>
    
- <span data-ttu-id="72af2-198">Azure PaaS 应用程序开发人员可以利用 Azure Multi-Factor Authentication 服务。</span><span class="sxs-lookup"><span data-stu-id="72af2-198">Azure PaaS application developers can take advantage of the Azure Multi-Factor Authentication service.</span></span>
    
<span data-ttu-id="72af2-199">目录同步不提供与本地 MFA 解决方案的集成。</span><span class="sxs-lookup"><span data-stu-id="72af2-199">Directory synchronization does not provide integration with on-premises MFA solutions.</span></span>
  
### <a name="federation-and-single-sign-on"></a><span data-ttu-id="72af2-200">联合身份验证和单一登录</span><span class="sxs-lookup"><span data-stu-id="72af2-200">Federation and single sign-on</span></span>

<span data-ttu-id="72af2-201">此选项需要其他服务器和基础架构。</span><span class="sxs-lookup"><span data-stu-id="72af2-201">This option requires additional servers and infrastructure.</span></span> 
  
![执行联合身份验证所需的服务器](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 <span data-ttu-id="72af2-203">**图 5： 执行联合身份验证所需的服务器**</span><span class="sxs-lookup"><span data-stu-id="72af2-203">**Figure 5: Servers needed for federated authentication**</span></span>
  
<span data-ttu-id="72af2-p115">图 5 显示了执行联合身份验证所需的组件集。Azure AD 联系 Web 应用程序代理，该代理将身份验证请求转发到 Active Directory 联合身份验证服务 (AD FS) 服务器，后者将请求转发到 AD DS 域控制器以进行评估和响应。运行 Azure AD Connect 工具的服务器会将帐户名称列表从 AD DS 同步到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="72af2-p115">Figure 5 shows the set of components for federated authentication. Azure AD contacts a web application proxy, which forwards the authentication request to an Active Directory Federation Services (AD FS) server, which forwards the request to an AD DS domain controller for evaluation and response. A server running the Azure AD Connect tool synchronizes the list of account names from AD DS to Azure AD.</span></span>
  
<span data-ttu-id="72af2-207">联合身份验证提供这些额外的企业级功能：</span><span class="sxs-lookup"><span data-stu-id="72af2-207">Federation provides these additional enterprise capabilities:</span></span>
  
- <span data-ttu-id="72af2-208">将发送到 Azure AD 的所有身份验证请求转发到本地标识提供程序，并通过 AD FS 对本地标识提供程序执行这些请求。</span><span class="sxs-lookup"><span data-stu-id="72af2-208">All authentication requests sent to Azure AD are forwarded to and performed against the on-premises identity provider through AD FS.</span></span>
    
- <span data-ttu-id="72af2-209">使用非 Microsoft 标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="72af2-209">Works with non-Microsoft identity providers.</span></span>
    
- <span data-ttu-id="72af2-210">密码哈希同步可作为联合登录的登录备份（例如，如果联合身份验证失败）。</span><span class="sxs-lookup"><span data-stu-id="72af2-210">Password hash synchronization can act as a sign-in backup for federated sign-in (for example, if the federated authentication fails).</span></span>
    
<span data-ttu-id="72af2-211">如果出现以下情况，则使用联合身份验证：</span><span class="sxs-lookup"><span data-stu-id="72af2-211">Use federation if:</span></span>
  
- <span data-ttu-id="72af2-p116">需要单一登录。使用单一登录，在访问云服务时，将不提示用户输入任何凭据（用户名或密码）。</span><span class="sxs-lookup"><span data-stu-id="72af2-p116">Single sign-on is required. With single sign-on, users are not prompted to enter any credentials (user name or password), when accessing a cloud service.</span></span>
    
- <span data-ttu-id="72af2-214">已部署 AD FS。</span><span class="sxs-lookup"><span data-stu-id="72af2-214">AD FS is already deployed.</span></span>
    
- <span data-ttu-id="72af2-215">使用第三方标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="72af2-215">You use a third-party identity provider.</span></span>
    
- <span data-ttu-id="72af2-216">使用 Forefront Identity Manager 2010 R2（不支持密码哈希同步）。</span><span class="sxs-lookup"><span data-stu-id="72af2-216">You use Forefront Identity Manager 2010 R2 (does not support password hash synchronization).</span></span>
    
- <span data-ttu-id="72af2-217">有本地集成的智能卡或其他 MFA 解决方案。</span><span class="sxs-lookup"><span data-stu-id="72af2-217">You have an on-premises integrated smart card or other MFA solution.</span></span>
    
- <span data-ttu-id="72af2-218">您需要登录审核和/或禁用帐户。</span><span class="sxs-lookup"><span data-stu-id="72af2-218">You require sign-in audit and/or disablement of accounts.</span></span>
    
- <span data-ttu-id="72af2-219">贵组织需要按网络位置或工作时间限制客户端登录。</span><span class="sxs-lookup"><span data-stu-id="72af2-219">Your organization requires client sign-in restrictions by network location or work hours.</span></span>
    
- <span data-ttu-id="72af2-220">您必须遵守联邦信息处理标准 (FIPS)。</span><span class="sxs-lookup"><span data-stu-id="72af2-220">You must comply with Federal Information Processing Standards (FIPS).</span></span>
    
<span data-ttu-id="72af2-221">联合身份验证需要在本地基础结构上进行更大的投资。</span><span class="sxs-lookup"><span data-stu-id="72af2-221">Federated authentication requires a greater investment in infrastructure on-premises.</span></span>
  
- <span data-ttu-id="72af2-p117">本地服务器必须可通过公司防火墙访问 Internet。Microsoft 建议使用在外围网络中部署的 Web 应用程序代理服务器。</span><span class="sxs-lookup"><span data-stu-id="72af2-p117">The on-premises servers must be Internet-accessible through a corporate firewall. Microsoft recommends the use of Web Application Proxy servers deployed in your perimeter network.</span></span>
    
- <span data-ttu-id="72af2-224">需要硬件和许可证，且要求 AD FS 服务器、AD FS 代理服务器或 Web 应用程序代理服务器、防火墙和负载平衡器处于运行状态。</span><span class="sxs-lookup"><span data-stu-id="72af2-224">Requires hardware, licenses, and operations for AD FS servers, AD FS proxy or Web Application Proxy servers, firewalls, and load balancers.</span></span> 
    
- <span data-ttu-id="72af2-225">可用性和性能对于确保用户能够访问 Office 365 和其他云应用程序非常重要。</span><span class="sxs-lookup"><span data-stu-id="72af2-225">Availability and performance are important to ensure users can access Office 365 and other cloud applications.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="72af2-226">详细信息</span><span class="sxs-lookup"><span data-stu-id="72af2-226">More Information</span></span>

- [<span data-ttu-id="72af2-227">通过 Office 365 同步目录简单易行</span><span class="sxs-lookup"><span data-stu-id="72af2-227">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="72af2-228">准备通过到 Office 365 的目录同步来设置用户</span><span class="sxs-lookup"><span data-stu-id="72af2-228">Prepare to provision users through directory synchronization to Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [<span data-ttu-id="72af2-229">适用于 Office 365 的 Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="72af2-229">Multi-Factor Authentication for Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [<span data-ttu-id="72af2-230">Azure Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="72af2-230">Azure Multi-Factor Authentication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [<span data-ttu-id="72af2-231">TechEd 2014：目录集成：创建一个包含 Active Directory 和 Azure Active Directory 的目录</span><span class="sxs-lookup"><span data-stu-id="72af2-231">TechEd 2014: Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## <a name="extend-ad-ds-to-azure"></a><span data-ttu-id="72af2-232">将 AD DS 扩展到 Azure</span><span class="sxs-lookup"><span data-stu-id="72af2-232">Extend AD DS to Azure</span></span>

<span data-ttu-id="72af2-233">将 AD DS 扩展到 Azure 是支持在 Azure 基础结构服务的虚拟机上运行业务线应用程序的第一步，提供以下功能:</span><span class="sxs-lookup"><span data-stu-id="72af2-233">Extending AD DS to Azure is the first step to support line-of-business applications running on virtual machines in Azure infrastructure services, which provides:</span></span>
  
- <span data-ttu-id="72af2-234">支持基于云的解决方案，这些解决方案需要 NTLM 或 Kerberos 身份验证或加入 AD DS 域的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="72af2-234">Support for cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="72af2-235">云服务和应用程序的其他潜在集成，并且可以随时添加集成。</span><span class="sxs-lookup"><span data-stu-id="72af2-235">Additional integration potential for cloud services and applications and can be added at any time.</span></span>
    
![将 AD DS 扩展到 Azure 虚拟网络](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 <span data-ttu-id="72af2-237">**图 6： 将 AD DS 扩展到 Azure 虚拟网络**</span><span class="sxs-lookup"><span data-stu-id="72af2-237">**Figure 6: Extending AD DS to an Azure virtual network**</span></span>
  
<span data-ttu-id="72af2-p118">图 6 显示了一个本地或私有云数据中心，其中 AD DS 已通过站点到站点 VPN 或 ExpressRoute 连接连接到 Azure 虚拟网络。Azure 虚拟网络包含业务线应用程序的服务器及其自己的一组 AD DS 域控制器。此配置是本地 AD DS 的混合部署，位于 Azure 基础结构服务中。它需要：</span><span class="sxs-lookup"><span data-stu-id="72af2-p118">Figure 6 shows an on-premises or private cloud datacenter with AD DS connected to an Azure virtual network with a site-to-site VPN or ExpressRoute connection. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers. This configuration is a hybrid deployment of AD DS on-premises and in Azure infrastructure services. It requires:</span></span>
  
- <span data-ttu-id="72af2-242">Azure 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="72af2-242">An Azure virtual network.</span></span>
    
- <span data-ttu-id="72af2-243">本地虚拟专用网络 (VPN) 设备或路由器与 Azure VPN 网关之间的连接。</span><span class="sxs-lookup"><span data-stu-id="72af2-243">A connection between an on-premises virtual private network (VPN) device or router and an Azure VPN gateway.</span></span>
    
- <span data-ttu-id="72af2-244">在虚拟网络中为虚拟机使用本地 IP 地址空间的一部分。</span><span class="sxs-lookup"><span data-stu-id="72af2-244">Using a portion of your on-premises IP address space for the virtual machines in the virtual network.</span></span>
    
- <span data-ttu-id="72af2-245">在指定为全局编录服务器的虚拟网络中部署一个或多个域控制器（通过 VPN 连接减少出口通信量）。</span><span class="sxs-lookup"><span data-stu-id="72af2-245">Deploying one or more domain controllers in the virtual network designated as global catalog servers (reduces egress traffic across the VPN connection).</span></span>
    
<span data-ttu-id="72af2-246">与和 Azure AD 同步相比，这一标识体系结构支持一组不同的解决方案和应用程序。</span><span class="sxs-lookup"><span data-stu-id="72af2-246">This identity architecture supports a different set of solutions and applications compared to synchronization with Azure AD.</span></span>
  
### <a name="on-premises-to-azure-connection-options"></a><span data-ttu-id="72af2-247">本地到 Azure 的连接选项</span><span class="sxs-lookup"><span data-stu-id="72af2-247">On-premises to Azure connection options</span></span>

<span data-ttu-id="72af2-248">若要将您的本地网络连接到 Azure 虚拟网络，您可以使用以下方式：</span><span class="sxs-lookup"><span data-stu-id="72af2-248">To connect your on-premises network to an Azure virtual network, you can use:</span></span>
  
- <span data-ttu-id="72af2-249">站点到站点 VPN 连接，此连接可以将 1-10 个站点（包括其他 Azure 虚拟网络）连接到单个 Azure 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="72af2-249">A site-to-site VPN connection, which can connect 1-10 sites (including other Azure virtual networks) to a single Azure virtual network.</span></span>
    
- <span data-ttu-id="72af2-p119">ExpressRoute，这是通过合作伙伴网络和数据中心服务提供商建立的一个到 Azure 的专用安全 WAN 链接。ExpressRoute 连接可以提供更高的可靠性、更高的带宽和更低的延迟时间。</span><span class="sxs-lookup"><span data-stu-id="72af2-p119">ExpressRoute, a private, secure WAN link to Azure through a partner network and datacenter services provider. ExpressRoute connections can offer increased reliability, higher bandwidth, and lower latencies.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="72af2-252">详细信息</span><span class="sxs-lookup"><span data-stu-id="72af2-252">More Information</span></span>

- [<span data-ttu-id="72af2-253">适用于虚拟网络的跨界连接</span><span class="sxs-lookup"><span data-stu-id="72af2-253">Cross-premises connectivity for virtual networks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [<span data-ttu-id="72af2-254">ExpressRoute 技术概述</span><span class="sxs-lookup"><span data-stu-id="72af2-254">ExpressRoute Technical Overview</span></span>](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [<span data-ttu-id="72af2-255">在 Azure 虚拟机上部署 Windows Server Active Directory 的准则</span><span class="sxs-lookup"><span data-stu-id="72af2-255">Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## <a name="integrate-your-applications-with-cloud-identities"></a><span data-ttu-id="72af2-256">将应用程序与云标识进行集成</span><span class="sxs-lookup"><span data-stu-id="72af2-256">Integrate your applications with cloud identities</span></span>

<span data-ttu-id="72af2-p120">当设计和开发在云中运行的应用程序时，您应力求实现身份验证过程用户体验的一致性，包括所需的凭据集。例如，在使用 Windows 凭据时，无论针对的是 Azure AD 还是扩展的 AD DS，都要确保用户可以快速进行验证并专注于他们的任务。</span><span class="sxs-lookup"><span data-stu-id="72af2-p120">When designing and developing applications that run in the cloud, you should aim for consistency of the user experience for the authentication process, including the set of required credentials. For example, when using Windows credentials, whether against Azure AD or an extended AD DS, ensure that users can quickly authenticate and focus on their tasks.</span></span>
  
![将应用程序与云标识进行集成](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 <span data-ttu-id="72af2-260">**图 7：将应用程序与云标识进行集成**</span><span class="sxs-lookup"><span data-stu-id="72af2-260">**Figure 7: Integrate your applications with cloud identities**</span></span>
  
<span data-ttu-id="72af2-261">图 7 显示了用于将应用程序与云标识进行集成的三个选项。</span><span class="sxs-lookup"><span data-stu-id="72af2-261">Figure 7 shows three options for integrating your application with cloud identities.</span></span>
  
1. <span data-ttu-id="72af2-262">通过 Azure AD 注册云托管的应用程序。</span><span class="sxs-lookup"><span data-stu-id="72af2-262">Register your cloud-hosted applications with Azure AD.</span></span>
    
    <span data-ttu-id="72af2-p121">请参阅 MSDN 文章[将应用程序与 Azure Active Directory 集成](https://go.microsoft.com/fwlink/p/?LinkId=524303)。这允许您使用 Azure AD 来验证对 PaaS 应用程序的访问，并允许用户或管理员授予对您的应用程序的权限以便代表他们访问来自其他云服务（如 Office 365）的内容。更多详细信息和代码示例可在 MSDN 文章 [Azure Active Directory 的身份验证方案](https://go.microsoft.com/fwlink/p/?LinkId=524304)上找到。</span><span class="sxs-lookup"><span data-stu-id="72af2-p121">See the MSDN article [Integrating Applications with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). This lets you use Azure AD to authenticate access to your PaaS application, as well as allowing users or administrators to grant rights to your application to access content on their behalf from other cloud services, such as Office 365. More details and code samples can be found in the MSDN article [Authentication Scenarios for Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span></span> 
    
2. <span data-ttu-id="72af2-266">需要以编程方式进行身份验证来获取受 AD SD、Windows Server 2012 R2 上的 AD SD 或 Azure AD 保护的应用程序的访问权限的应用程序可以使用：</span><span class="sxs-lookup"><span data-stu-id="72af2-266">Applications that require programmatic authentication to gain access to an application secured by AD SD, AD FS on Windows Server 2012 R2, or Azure AD can use:</span></span>
    
  - <span data-ttu-id="72af2-267">[Azure AD 图形 API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span><span class="sxs-lookup"><span data-stu-id="72af2-267">The [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span></span>
    
  - [<span data-ttu-id="72af2-268">Active Directory Authentication Library (ADAL)</span><span class="sxs-lookup"><span data-stu-id="72af2-268">Active Directory Authentication Library (ADAL)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=524297)
    
    <span data-ttu-id="72af2-p122">Azure AD 图形 API 支持 OAuth 和 OpenID Connect。它还适用于 PaaS 应用程序。</span><span class="sxs-lookup"><span data-stu-id="72af2-p122">The Azure AD Graph API supports OAuth and OpenID Connect. It also works with PaaS applications.</span></span>
    
3. <span data-ttu-id="72af2-p123">将在 Azure 虚拟网络的虚拟机上运行的本地应用程序或业务线应用程序配置为直接使用 Windows 身份验证（NTLM 或 Kerberos）。这是最佳的用户体验，需要为服务器应用程序开发人员进行的配置最少。</span><span class="sxs-lookup"><span data-stu-id="72af2-p123">Configure on-premises applications or line-of-business applications running on virtual machines in an Azure virtual network to use Windows authentication (NTLM or Kerberos) directly. This is the best experience for users and requires the least configuration for server application developers.</span></span>
    
### <a name="application-integration-example"></a><span data-ttu-id="72af2-273">应用程序集成示例</span><span class="sxs-lookup"><span data-stu-id="72af2-273">Application integration example</span></span>

<span data-ttu-id="72af2-p124">组织构建公开 REST 终结点的 ASP.NET 应用程序，其他应用程序可以通过此终结点获取最新的销售数据。使用 Azure AD 确保对该 REST 终结点的访问安全。在 ASP.NET 应用程序发送请求的数据之前，应用程序必须提供可以通过 Azure AD 进行身份验证的凭据。然后，组织中的其他开发人员可以编写他们自己的、使用 REST 终结点中销售数据的应用程序。</span><span class="sxs-lookup"><span data-stu-id="72af2-p124">An organization builds an ASP.NET application that exposes a REST endpoint where other applications can obtain the latest sales data. Access to that REST endpoint is secured with Azure AD. Applications must provide credentials that can be authenticated by Azure AD before the ASP.NET application sends the requested data. Other developers in the organization can then write their own applications that use the sales data from the REST endpoint.</span></span>
  
<span data-ttu-id="72af2-p125">若要对 Azure AD 进行身份验证并检索数据，ADAL 管理用户身份验证过程，并将访问令牌递交给应用程序，以便使用访问令牌来获取对销售数据的访问权限。ADAL 通过抽象大大降低了获取和分析令牌、OAuth 流和其他元素的复杂性。ADAL 是另一种迅速变化的技术解决方案，因此开发人员应在 NuGet 上查找最新版本。</span><span class="sxs-lookup"><span data-stu-id="72af2-p125">To authenticate to Azure AD and retrieve data, ADAL manages the user authentication process and hands the access token off to the application so it can be used to gain access to the sales data. ADAL abstracts out much of the complexity of obtaining and parsing tokens, OAuth flows, and other elements. ADAL is another technology solution that is rapidly changing so developers should look for the latest version on NuGet.</span></span>
  
## <a name="deploying-directory-components-in-azure"></a><span data-ttu-id="72af2-281">在 Azure 中部署目录组件</span><span class="sxs-lookup"><span data-stu-id="72af2-281">Deploying directory components in Azure</span></span>

<span data-ttu-id="72af2-p126">您可以在 Azure 虚拟网络而不是本地数据中心中部署目录组件，如用于密码同步或联合身份验证的服务器。考虑其优点，尤其是当您计划将 AD DS 扩展到 Azure 时。</span><span class="sxs-lookup"><span data-stu-id="72af2-p126">You can deploy directory components, such as servers for password synchronization or federated authentication, in an Azure virtual network rather than an on-premises datacenter. Consider its benefits, especially if you plan to extend AD DS into Azure.</span></span>
  
<span data-ttu-id="72af2-284">下面是可以置于 Azure 虚拟网络中的目录组件：</span><span class="sxs-lookup"><span data-stu-id="72af2-284">Here are the directory components that can be put in an Azure virtual network:</span></span>
  
- <span data-ttu-id="72af2-285">Azure AD Connect 工具</span><span class="sxs-lookup"><span data-stu-id="72af2-285">Azure AD Connect tool</span></span>
    
- <span data-ttu-id="72af2-286">联合身份验证组件</span><span class="sxs-lookup"><span data-stu-id="72af2-286">Federated authentication components</span></span>
    
- <span data-ttu-id="72af2-287">独立 AD DS 环境</span><span class="sxs-lookup"><span data-stu-id="72af2-287">A standalone AD DS environment</span></span>
    
### <a name="ad-connect-tool"></a><span data-ttu-id="72af2-288">AD Connect 工具</span><span class="sxs-lookup"><span data-stu-id="72af2-288">AD Connect tool</span></span>

<span data-ttu-id="72af2-p127">可以在 Azure 虚拟网络的云中托管的 Azure AD Connect 工具。考虑将此工作负载部署到 Azure 的以下这些优点：</span><span class="sxs-lookup"><span data-stu-id="72af2-p127">The Azure AD Connect tool can be hosted in the cloud on an Azure virtual network. Consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="72af2-291">有可能更快地进行设置，且操作成本更低</span><span class="sxs-lookup"><span data-stu-id="72af2-291">Potentially faster provisioning and lower cost of operations</span></span>
    
- <span data-ttu-id="72af2-292">增加了可用性</span><span class="sxs-lookup"><span data-stu-id="72af2-292">Increased availability</span></span>
    
![在 Azure 基础结构服务中运行 AD Connect 工具](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 <span data-ttu-id="72af2-294">**图 8：在 Azure 中运行的 AD Connect 工具**</span><span class="sxs-lookup"><span data-stu-id="72af2-294">**Figure 8: The AD Connect tool running in Azure**</span></span>
  
<span data-ttu-id="72af2-p128">图 8 显示了在 Azure 虚拟网络的虚拟机上运行的 AD Connect 工具，此工具查询本地 AD DS 域控制器的帐户更改，然后将这些更改发送到 Office 365。此解决方案适用于:</span><span class="sxs-lookup"><span data-stu-id="72af2-p128">Figure 8 shows the AD Connect tool running on a virtual machine in an Azure virtual network, which queries an on-premises AD DS domain controller for account changes and then sends those changes to Office 365. This solution works with:</span></span>
  
- <span data-ttu-id="72af2-297">Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="72af2-297">Office 365 services.</span></span>
    
- <span data-ttu-id="72af2-298">通过 Internet 提供的 Azure PaaS 应用程序。</span><span class="sxs-lookup"><span data-stu-id="72af2-298">Azure PaaS applications that are available over the Internet.</span></span>
    
- <span data-ttu-id="72af2-299">通过站点到站点 VPN 或 ExpressRoute 连接在本地环境中提供的 Azure 业务线应用程序。</span><span class="sxs-lookup"><span data-stu-id="72af2-299">Line-of-business applications in Azure that are available from on-premises environments through the site-to-site VPN or ExpressRoute connection.</span></span>
    
<span data-ttu-id="72af2-300">有关详细信息，请参阅[将您的本地标识与 Azure Active Directory 集成](https://go.microsoft.com/fwlink/p/?LinkId=524307)。</span><span class="sxs-lookup"><span data-stu-id="72af2-300">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="federated-authentication-infrastructure"></a><span data-ttu-id="72af2-301">联合身份验证基础结构</span><span class="sxs-lookup"><span data-stu-id="72af2-301">Federated authentication infrastructure</span></span>

<span data-ttu-id="72af2-302">如果您尚未部署本地 AD FS，考虑将此工作负载部署到 Azure 的以下这些优点：</span><span class="sxs-lookup"><span data-stu-id="72af2-302">If you haven't already deployed AD FS on-premises, consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="72af2-303">提供对云服务（没有本地依赖项）进行身份验证的自主权</span><span class="sxs-lookup"><span data-stu-id="72af2-303">Provides autonomy for authentication to cloud services (no on-premises dependencies)</span></span>
    
- <span data-ttu-id="72af2-304">减少本地托管的服务器和工具</span><span class="sxs-lookup"><span data-stu-id="72af2-304">Reduces servers and tools hosted on-premises</span></span>
    
- <span data-ttu-id="72af2-305">在两个节点的故障转移群集上使用站点到站点 VPN 网关连接到 Azure（新）</span><span class="sxs-lookup"><span data-stu-id="72af2-305">Uses a site-to-site VPN gateway on a two-node failover cluster to connect to Azure (new)</span></span>
    
- <span data-ttu-id="72af2-306">使用 ACL 以确保 Web 应用程序代理服务器仅与 AD FS 进行通信，而不是直接与域控制器或其他服务器通信</span><span class="sxs-lookup"><span data-stu-id="72af2-306">Uses ACLs to ensure that Web Application Proxy servers can only communicate with AD FS, not domain controllers or other servers directly</span></span>
    
![在 Azure 中部署您的联合身份验证基础结构](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 <span data-ttu-id="72af2-308">**图 9：在 Azure 中部署您的联合身份验证基础结构**</span><span class="sxs-lookup"><span data-stu-id="72af2-308">**Figure 9: Deploying your federated authentication infrastructure in Azure**</span></span>
  
<span data-ttu-id="72af2-p129">图 9 显示了复制 AD DS 信息的一组本地域控制器和 Azure 虚拟网络中的一组域控制器。在 Azure 虚拟网络中的服务器上运行的 Azure AD Connect 工具查询本地域控制器的更改，然后将这些更改发送到 Azure AD。将从 Microsoft SaaS 服务、Azure PaaS 应用程序和其他云应用程序到 Azure AD 的传入身份验证请求转发到外部负载平衡器，此平衡器将请求转发到一组 Web 应用程序代理服务器。Web 应用程序代理服务器将请求转发到内部负载平衡器，此平衡器将请求转发到一组 AD FS 服务器。然后，AD FS 服务器将请求转发到域控制器以验证发送凭据。</span><span class="sxs-lookup"><span data-stu-id="72af2-p129">Figure 9 shows a set of on-premises domain controllers replicating AD DS information with a set of domain controllers in an Azure virtual network. The Azure AD Connect tool running on a server in the Azure virtual network queries the local domain controllers for changes and then sends those changes to Azure AD. Incoming authentication requests to Azure AD from Microsoft SaaS services, Azure PaaS applications, and other cloud applications are forwarded to an external load balancer, which forwards the request to a set of Web Application Proxy servers. The Web Application Proxy servers forward the request to an internal load balancer, which forwards the request to a set of AD FS servers. The AD FS servers then forward the request to a domain controller to validate the send credentials.</span></span>
  
 <span data-ttu-id="72af2-314">此解决方案适用于:</span><span class="sxs-lookup"><span data-stu-id="72af2-314">This solution works with:</span></span>
  
- <span data-ttu-id="72af2-315">需要 Kerberos 的应用程序</span><span class="sxs-lookup"><span data-stu-id="72af2-315">Applications that require Kerberos</span></span>
    
- <span data-ttu-id="72af2-316">所有 Microsoft SaaS 服务</span><span class="sxs-lookup"><span data-stu-id="72af2-316">All of Microsoft's SaaS services</span></span>
    
- <span data-ttu-id="72af2-317">Azure 中面向 Internet 的应用程序</span><span class="sxs-lookup"><span data-stu-id="72af2-317">Applications in Azure that are Internet-facing</span></span>
    
- <span data-ttu-id="72af2-318">Azure IaaS 或 PaaS 中要求使用组织的一组 AD DS 帐户进行身份验证的应用程序</span><span class="sxs-lookup"><span data-stu-id="72af2-318">Applications in Azure IaaS or PaaS that require authentication with the set of accounts in your organization's AD DS</span></span>
    
<span data-ttu-id="72af2-319">有关详细信息，请参阅[将您的本地标识与 Azure Active Directory 集成](https://go.microsoft.com/fwlink/p/?LinkId=524307)。</span><span class="sxs-lookup"><span data-stu-id="72af2-319">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="standalone-ad-ds-environment-in-an-azure-virtual-network"></a><span data-ttu-id="72af2-320">Azure 虚拟网络中的独立 AD DS 环境</span><span class="sxs-lookup"><span data-stu-id="72af2-320">Standalone AD DS environment in an Azure virtual network</span></span>

<span data-ttu-id="72af2-p130">并非始终需要将云应用程序与本地环境集成。例如，Azure 虚拟网络中的独立 AD DS 域支持面向公众的应用程序，如 Internet 站点。</span><span class="sxs-lookup"><span data-stu-id="72af2-p130">You don't always need to integrate a cloud application with your on-premises environment. For example, a standalone AD DS domain in an Azure virtual network supports applications that are public-facing, such as Internet sites.</span></span>
  
![适用于基于服务器的应用程序的独立 AD DS 环境](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 <span data-ttu-id="72af2-324">**图 10：适用于基于服务器的应用程序的独立 AD DS 环境**</span><span class="sxs-lookup"><span data-stu-id="72af2-324">**Figure 10: A standalone AD DS environment for a server-based application**</span></span>
  
<span data-ttu-id="72af2-p131">图 10 显示了托管一组 AD DS 服务器，并且同时提供 AD DS 服务和 DNS 服务的 Azure 虚拟网络，以及一组托管应用程序的服务器。此解决方案适用于:</span><span class="sxs-lookup"><span data-stu-id="72af2-p131">Figure 10 shows an Azure virtual network hosting a set of AD DS servers, providing both AD DS and DNS services, with a set of servers that host an application. This solution works with:</span></span>
  
- <span data-ttu-id="72af2-327">面向 Internet 的 Web 站点和应用程序</span><span class="sxs-lookup"><span data-stu-id="72af2-327">Internet-facing web sites and applications</span></span>
    
- <span data-ttu-id="72af2-328">需要 NTLM 或 Kerberos 身份验证的应用程序</span><span class="sxs-lookup"><span data-stu-id="72af2-328">Applications that require NTLM or Kerberos authentication</span></span>
    
- <span data-ttu-id="72af2-329">在需要 AD DS 的基于 Windows 的服务器上运行的应用程序</span><span class="sxs-lookup"><span data-stu-id="72af2-329">Applications running on Windows-based servers that require AD DS</span></span>
    
<span data-ttu-id="72af2-330">有关详细信息，请参阅[将您的本地标识与 Azure Active Directory 集成](https://go.microsoft.com/fwlink/p/?LinkId=524307)。</span><span class="sxs-lookup"><span data-stu-id="72af2-330">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="72af2-331">See Also</span><span class="sxs-lookup"><span data-stu-id="72af2-331">See Also</span></span>

[<span data-ttu-id="72af2-332">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="72af2-332">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="72af2-333">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="72af2-333">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



