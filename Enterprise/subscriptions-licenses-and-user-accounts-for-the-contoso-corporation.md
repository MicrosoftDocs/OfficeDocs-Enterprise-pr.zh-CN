---
title: Contoso Corporation 的订阅、许可证和用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: 摘要： 了解 Contoso 的云订阅、 许可证、 用户帐户和租户的结构。
ms.openlocfilehash: cd196e0800f6a39973f4c5c82001ed3e9c330fee
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915507"
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="f44bc-103">Contoso Corporation 的订阅、许可证和用户帐户</span><span class="sxs-lookup"><span data-stu-id="f44bc-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="f44bc-104">**摘要：** 了解 Contoso 的云订阅、 许可证、 用户帐户和租户的结构。</span><span class="sxs-lookup"><span data-stu-id="f44bc-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="f44bc-105">为了确保所有云产品对标识和账单的一致使用，Microsoft 提供组织/订阅/许可证/用户帐户层次结构：</span><span class="sxs-lookup"><span data-stu-id="f44bc-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="f44bc-106">组织</span><span class="sxs-lookup"><span data-stu-id="f44bc-106">Organization</span></span>
    
    <span data-ttu-id="f44bc-107">使用 Microsoft 云产品的业务实体通常由公用 DNS 域名标识，例如 contoso.com。</span><span class="sxs-lookup"><span data-stu-id="f44bc-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="f44bc-108">订阅</span><span class="sxs-lookup"><span data-stu-id="f44bc-108">Subscriptions</span></span>
    
    <span data-ttu-id="f44bc-p101">对于 Microsoft saas 与云产品 （Office 365 和 Intune/EMS Dynamics 365），订阅是特定产品及一系列用户许可证的购买。为 Azure 订阅允许帐单到组织的消耗的云服务。</span><span class="sxs-lookup"><span data-stu-id="f44bc-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="f44bc-111">许可证</span><span class="sxs-lookup"><span data-stu-id="f44bc-111">Licenses</span></span>
    
    <span data-ttu-id="f44bc-p102">对于 Microsoft saas 与云产品许可证允许使用云服务的特定用户帐户。对 Azure，软件许可证是构建到服务定价，但在某些情况下，您将需要购买额外的软件许可证。</span><span class="sxs-lookup"><span data-stu-id="f44bc-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="f44bc-114">用户帐户</span><span class="sxs-lookup"><span data-stu-id="f44bc-114">User accounts</span></span>
    
    <span data-ttu-id="f44bc-115">用户帐户存储在 Azure AD 租户中，并且可以从本地标识提供程序（如 Windows Server AD）进行同步。</span><span class="sxs-lookup"><span data-stu-id="f44bc-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="f44bc-116">Contoso 的结构</span><span class="sxs-lookup"><span data-stu-id="f44bc-116">Contoso's structure</span></span>

<span data-ttu-id="f44bc-117">Contoso 已确定组织及其订阅、许可证、帐户和租户的以下结构：</span><span class="sxs-lookup"><span data-stu-id="f44bc-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="f44bc-118">**图 1：Contoso 的组织、订阅、许可证、用户帐户和租户**</span><span class="sxs-lookup"><span data-stu-id="f44bc-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Contoso 的组织、订阅、许可证、用户帐户和租户](media/Contoso-Poster/Subscriptions.png)
  
<span data-ttu-id="f44bc-120">图 1 显示 Contoso 组织如何包含多个订阅并和包含与 contoso.com Windows Server AD 林同步的用户帐户的常见 Azure AD 租户关联。</span><span class="sxs-lookup"><span data-stu-id="f44bc-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="f44bc-121">**组织**由其公共域名 contoso.com 标识 Contoso Corporation。</span><span class="sxs-lookup"><span data-stu-id="f44bc-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="f44bc-122">**订阅和许可证**Contoso 公司正在使用以下：</span><span class="sxs-lookup"><span data-stu-id="f44bc-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="f44bc-123">具有 5,000 许可证的 Office 365 企业版 E3 产品</span><span class="sxs-lookup"><span data-stu-id="f44bc-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="f44bc-124">具有 200 个许可证的 Office 365 企业版 E5 产品</span><span class="sxs-lookup"><span data-stu-id="f44bc-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="f44bc-125">具有 5,000 许可证的 EMS 产品</span><span class="sxs-lookup"><span data-stu-id="f44bc-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="f44bc-126">具有 100 个许可证的 Dynamics 365 产品
</span><span class="sxs-lookup"><span data-stu-id="f44bc-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="f44bc-127">基于区域的多个 Azure 订阅</span><span class="sxs-lookup"><span data-stu-id="f44bc-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="f44bc-128">**用户帐户**常见的 Azure AD 租户包含用户帐户的列表和组使用的所有 Contoso 的订阅，除外开发/测试 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="f44bc-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="f44bc-129">对于 Contoso 租户：</span><span class="sxs-lookup"><span data-stu-id="f44bc-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="f44bc-p103">对于 SaaS 云产品，租户是托管提供云服务的服务器的区域位置。Contoso 选择欧洲区域来托管其 Office 365、EMS 和 Dynamics 365 租户。
 </span><span class="sxs-lookup"><span data-stu-id="f44bc-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="f44bc-p104">Azure PaaS 服务和应用程序和 IaaS IT 工作负荷可以跨世界上有任何 Azure 数据中心中的租户。Azure AD 租户是包含帐户和组的 Azure AD 的特定实例。</span><span class="sxs-lookup"><span data-stu-id="f44bc-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="f44bc-134">常见 Azure AD 租户包含 Contoso Windows Server AD 林的同步的帐户提供跨 Microsoft 云服务 IDaaS。</span><span class="sxs-lookup"><span data-stu-id="f44bc-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="f44bc-135">有关详细信息，请参阅[订阅、 许可证、 帐户和 Microsoft 云服务的租户](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)。</span><span class="sxs-lookup"><span data-stu-id="f44bc-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="f44bc-136">Contoso 的 Azure 订阅</span><span class="sxs-lookup"><span data-stu-id="f44bc-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="f44bc-137">图 2 显示 Contoso 的 Azure 订阅的层次结构设计： 


</span><span class="sxs-lookup"><span data-stu-id="f44bc-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="f44bc-138">**图 2：Contoso 的 Azure 订阅结构**</span><span class="sxs-lookup"><span data-stu-id="f44bc-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Contoso 的 Azure 订阅结构](media/Contoso-Poster/Subscriptions-Nested.png)
  
- <span data-ttu-id="f44bc-140">Contoso 位于顶部，基于其与 Microsoft 的企业协议。</span><span class="sxs-lookup"><span data-stu-id="f44bc-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="f44bc-141">有一套与基于 Contoso 的 Windows Server AD 林中的域 Contoso Corporation 的世界各地的不同区域对应的帐户。</span><span class="sxs-lookup"><span data-stu-id="f44bc-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="f44bc-142">内每个区域中，有一个或多个区域的开发、 测试和生产部署需求所基于的订阅。</span><span class="sxs-lookup"><span data-stu-id="f44bc-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="f44bc-p105">每个 Azure 订阅可以与单个 Azure AD 租户相关联，该租户包含用于 Azure 服务身份验证和授权的用户帐户和组。生产订阅使用常见的 Contoso Azure AD 租户。</span><span class="sxs-lookup"><span data-stu-id="f44bc-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f44bc-145">See Also</span><span class="sxs-lookup"><span data-stu-id="f44bc-145">See Also</span></span>

[<span data-ttu-id="f44bc-146">Microsoft 云中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="f44bc-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="f44bc-147">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="f44bc-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="f44bc-148">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="f44bc-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




