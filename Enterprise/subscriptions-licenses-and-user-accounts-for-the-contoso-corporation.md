---
title: "Contoso Corporation 的订阅、许可证和用户帐户"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "摘要： 了解 Contoso 的云订阅、 许可证、 用户帐户和承租人的结构。"
ms.openlocfilehash: 6e62fbbc0f52019e5d233fc73992b000952344f5
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="07c57-103">Contoso Corporation 的订阅、许可证和用户帐户</span><span class="sxs-lookup"><span data-stu-id="07c57-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="07c57-104">**摘要：**了解 Contoso 的云订阅、 许可证、 用户帐户和承租人的结构。</span><span class="sxs-lookup"><span data-stu-id="07c57-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="07c57-105">为了确保所有云产品对标识和账单的一致使用，Microsoft 提供组织/订阅/许可证/用户帐户层次结构：</span><span class="sxs-lookup"><span data-stu-id="07c57-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="07c57-106">组织</span><span class="sxs-lookup"><span data-stu-id="07c57-106">Organization</span></span>
    
    <span data-ttu-id="07c57-107">使用 Microsoft 云产品的业务实体通常由公用 DNS 域名标识，例如 contoso.com。</span><span class="sxs-lookup"><span data-stu-id="07c57-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="07c57-108">订阅</span><span class="sxs-lookup"><span data-stu-id="07c57-108">Subscriptions</span></span>
    
    <span data-ttu-id="07c57-p101">对于 Microsoft SaaS 云服务 （Office 365、 Intune/EMS 和 Dynamics 365），订阅是特定产品和购买的一套用户许可证。对于 Azure，订阅允许组织使用的云服务的帐单。</span><span class="sxs-lookup"><span data-stu-id="07c57-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="07c57-111">许可证</span><span class="sxs-lookup"><span data-stu-id="07c57-111">Licenses</span></span>
    
    <span data-ttu-id="07c57-p102">对于 Microsoft SaaS 云产品，许可证允许特定的用户帐户以使用云服务。Azure，软件许可证天生到服务定价，但在某些情况下，您将需要购买额外的软件许可证。</span><span class="sxs-lookup"><span data-stu-id="07c57-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="07c57-114">用户帐户</span><span class="sxs-lookup"><span data-stu-id="07c57-114">User accounts</span></span>
    
    <span data-ttu-id="07c57-115">用户帐户存储在 Azure AD 租户中，并且可以从本地标识提供程序（如 Windows Server AD）进行同步。</span><span class="sxs-lookup"><span data-stu-id="07c57-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="07c57-116">Contoso 的结构</span><span class="sxs-lookup"><span data-stu-id="07c57-116">Contoso's structure</span></span>

<span data-ttu-id="07c57-117">Contoso 已确定组织及其订阅、许可证、帐户和租户的以下结构：</span><span class="sxs-lookup"><span data-stu-id="07c57-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="07c57-118">**图 1: Contoso 的组织、 订阅、 许可、 用户帐户和承租人**</span><span class="sxs-lookup"><span data-stu-id="07c57-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Contoso 的组织、订阅、许可证、用户帐户和租户](images/Contoso_Poster/Subscriptions.png)
  
<span data-ttu-id="07c57-120">图 1 显示 Contoso 组织如何包含多个订阅并和包含与 contoso.com Windows Server AD 林同步的用户帐户的常见 Azure AD 租户关联。</span><span class="sxs-lookup"><span data-stu-id="07c57-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="07c57-121">**组织**Contoso 公司由其公共域名称 contoso.com 标识。</span><span class="sxs-lookup"><span data-stu-id="07c57-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="07c57-122">**订阅和许可证**Contoso 公司正在使用下列：</span><span class="sxs-lookup"><span data-stu-id="07c57-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="07c57-123">Office 365 企业 E3 产品 5000 许可证</span><span class="sxs-lookup"><span data-stu-id="07c57-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="07c57-124">具有 200 个许可证的 Office 365 企业版 E5 产品</span><span class="sxs-lookup"><span data-stu-id="07c57-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="07c57-125">EMS 拥有 5000 许可证产品</span><span class="sxs-lookup"><span data-stu-id="07c57-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="07c57-126">100 份许可证 Dynamics 365 的产品</span><span class="sxs-lookup"><span data-stu-id="07c57-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="07c57-127">基于区域的多个 Azure 订阅</span><span class="sxs-lookup"><span data-stu-id="07c57-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="07c57-128">**用户帐户**常见的 Azure AD 租户包含用户帐户的列表和组由所有 Contoso 的订阅，但开发/测试 Azure 的订阅。</span><span class="sxs-lookup"><span data-stu-id="07c57-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="07c57-129">对于 Contoso 租户：</span><span class="sxs-lookup"><span data-stu-id="07c57-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="07c57-p103">对于 SaaS 云产品，租户为房屋提供云服务的服务器的区域位置。Contoso 选择承载其 Office 365、 EMS 和 Dynamics 365 承租人的欧洲地区。</span><span class="sxs-lookup"><span data-stu-id="07c57-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="07c57-p104">Azure PaaS 服务和应用程序以及 IaaS IT 工作负荷可以具有任何 Azure 数据中心内的租户遍及世界各地。Azure AD 租户是 Azure 广告包含的帐户和组的特定实例。</span><span class="sxs-lookup"><span data-stu-id="07c57-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="07c57-134">包含同步的帐户为 Contoso Windows 服务器 AD 林常见 Azure AD 租户提供 IDaaS 跨 Microsoft 的云服务。</span><span class="sxs-lookup"><span data-stu-id="07c57-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="07c57-135">有关详细信息，请参阅[预订、 许可证、 帐户和微软的云服务的租户](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)。</span><span class="sxs-lookup"><span data-stu-id="07c57-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="07c57-136">Contoso 的 Azure 订阅</span><span class="sxs-lookup"><span data-stu-id="07c57-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="07c57-137">图 2 显示了 Contoso 的 Azure 订阅层次结构设计：</span><span class="sxs-lookup"><span data-stu-id="07c57-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="07c57-138">**图 2: Contoso 的结构对 Azure 订阅**</span><span class="sxs-lookup"><span data-stu-id="07c57-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Contoso 的 Azure 订阅结构](images/Contoso_Poster/Subscriptions_Nested.png)
  
- <span data-ttu-id="07c57-140">Contoso 位于顶部，基于其与 Microsoft 的企业协议。</span><span class="sxs-lookup"><span data-stu-id="07c57-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="07c57-141">有一组对应于基于 Contoso 的 Windows 服务器 AD 林中的域 Contoso 公司在世界各地，在不同地区的帐户。</span><span class="sxs-lookup"><span data-stu-id="07c57-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="07c57-142">在每个区域中，有一个或多个订阅根据地区的开发、 测试和生产部署的需要。</span><span class="sxs-lookup"><span data-stu-id="07c57-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="07c57-p105">每个 Azure 订阅可以与单个 Azure AD 租户相关联，该租户包含用于 Azure 服务身份验证和授权的用户帐户和组。生产订阅使用常见的 Contoso Azure AD 租户。</span><span class="sxs-lookup"><span data-stu-id="07c57-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="07c57-145">See Also</span><span class="sxs-lookup"><span data-stu-id="07c57-145">See Also</span></span>

[<span data-ttu-id="07c57-146">Microsoft 云中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="07c57-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="07c57-147">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="07c57-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="07c57-148">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="07c57-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




