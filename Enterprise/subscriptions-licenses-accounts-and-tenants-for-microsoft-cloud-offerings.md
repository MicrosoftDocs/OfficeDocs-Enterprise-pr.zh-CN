---
title: 针对 Microsoft 云产品/服务的订阅、许可证、帐户和租户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/25/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
ms.custom:
- seo-marvel-apr2020
- Ent_Architecture
description: 了解 Microsoft 云服务的组织、订阅、许可证、用户帐户和租户的关系。
ms.openlocfilehash: 7546d4b24c66946e287aa51deb2d1f1896045322
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603664"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="77851-103">针对 Microsoft 云产品/服务的订阅、许可证、帐户和租户</span><span class="sxs-lookup"><span data-stu-id="77851-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

<span data-ttu-id="77851-104">为确保跨其云产品/服务使用一致的身份和帐单，Microsoft 提供了组织、订阅、许可证和用户帐户的层次结构：</span><span class="sxs-lookup"><span data-stu-id="77851-104">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="77851-105">Microsoft 365 和 Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="77851-105">Microsoft 365 and Microsoft Office 365</span></span>
- <span data-ttu-id="77851-106">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="77851-106">Microsoft Azure</span></span>
- <span data-ttu-id="77851-107">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="77851-107">Microsoft Dynamics 365</span></span>

## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="77851-108">层次结构的元素</span><span class="sxs-lookup"><span data-stu-id="77851-108">Elements of the hierarchy</span></span>

<span data-ttu-id="77851-109">以下是层次结构的元素：</span><span class="sxs-lookup"><span data-stu-id="77851-109">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="77851-110">组织</span><span class="sxs-lookup"><span data-stu-id="77851-110">Organization</span></span>

<span data-ttu-id="77851-p101">组织表示使用 Microsoft 云产品/服务的业务实体，通常由一个或多个公共域名系统 (DNS) 域名（如 contoso.com）标识。组织是订阅的容器。</span><span class="sxs-lookup"><span data-stu-id="77851-p101">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="77851-113">订阅</span><span class="sxs-lookup"><span data-stu-id="77851-113">Subscriptions</span></span>

<span data-ttu-id="77851-114">订阅是与 Microsoft 就使用一个或多个 Microsoft 云平台或服务签订的协议，其费用基于每个用户许可证费用或云资源使用累计。</span><span class="sxs-lookup"><span data-stu-id="77851-114">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.</span></span> 

- <span data-ttu-id="77851-115">Microsoft 基于软件即服务 (SaaS) 的云服务（Microsoft 365 和 Dynamics 365）按用户收取许可证费用。</span><span class="sxs-lookup"><span data-stu-id="77851-115">Microsoft's Software as a Service (SaaS)-based cloud offerings (Microsoft 365 and Dynamics 365) charge per-user license fees.</span></span> 
- <span data-ttu-id="77851-116">Microsoft 的平台即服务 (PaaS) 和基础设施即服务 (IaaS) 云服务 (Azure) 根据云资源使用量收取费用。</span><span class="sxs-lookup"><span data-stu-id="77851-116">Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
 
<span data-ttu-id="77851-p102">你也可以使用试用版订阅，此订阅会在一定时间后或使用费用后过期。你可以将试用版订阅转换为付费订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-p102">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="77851-119">组织可订阅多个 Micrososft 云服务。</span><span class="sxs-lookup"><span data-stu-id="77851-119">Organizations can have multiple subscriptions for Microsoft's cloud offerings.</span></span> <span data-ttu-id="77851-120">图 1 显示了一个组织，它具有多个 Microsoft 365 订阅、一个 Dynamics 365 订阅以及多个 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-120">Figure 1 shows a single organization that has multiple Microsoft 365 subscriptions, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>

<span data-ttu-id="77851-121">**图 1：组织的多个订阅示例**</span><span class="sxs-lookup"><span data-stu-id="77851-121">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![组织订阅多个 Micrososft 云服务的示例。](media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a><span data-ttu-id="77851-123">许可证</span><span class="sxs-lookup"><span data-stu-id="77851-123">Licenses</span></span>

<span data-ttu-id="77851-124">对于 Microsoft 的 SaaS 云服务，许可证允许特定用户帐户使用云产品的服务。</span><span class="sxs-lookup"><span data-stu-id="77851-124">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering.</span></span> <span data-ttu-id="77851-125">作为订阅的一部分，你可以每月支付固定的费用。</span><span class="sxs-lookup"><span data-stu-id="77851-125">You are charged a fixed monthly fee as part of your subscription.</span></span> <span data-ttu-id="77851-126">管理员将许可证分配给订阅中的各个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="77851-126">Administrators assign licenses to individual user accounts in the subscription.</span></span> <span data-ttu-id="77851-127">对于图 2 中的示例，Contoso 公司订阅了具有 100 个许可证的 Office 365 E5，允许最多 100 个单个用户帐户使用 Microsoft 365 E5 的功能和服务。</span><span class="sxs-lookup"><span data-stu-id="77851-127">For the example in Figure 2, the Contoso Corporation has a Microsoft 365 E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Microsoft 365 E5 features and services.</span></span>
  
<span data-ttu-id="77851-128">**图 2：组织基于 SaaS 的订阅内的许可证**</span><span class="sxs-lookup"><span data-stu-id="77851-128">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Microsoft 基于 SaaS 的云服务订阅中的多个许可证示例。](media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="77851-130">对于基于 Azure PaaS 的云服务，软件许可证是服务定价的一部分。</span><span class="sxs-lookup"><span data-stu-id="77851-130">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="77851-p105">对于基于 Azure IaaS 的虚拟机，使用在虚拟机映像上安装的软件或应用程序可能需要其他许可证。某些虚拟机映像安装了授权版软件，并且成本包括在服务器的每分钟费率中。例如，SQL Server 2014 和 SQL Server 2016 的虚拟机映像。</span><span class="sxs-lookup"><span data-stu-id="77851-p105">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="77851-p106">某些虚拟机映像安装了试用版应用程序，在试用期过后需要其他软件应用程序许可证。例如，SharePoint Server 2016 试用版虚拟机映像包括预安装的试用版 SharePoint Server 2016。若要在试用版过期后继续使用 SharePoint Server 2016，你必须从 Microsoft 购买 SharePoint Server 2016 许可证和客户端许可证。这些费用与 Azure 订阅是分开的，而运行虚拟机的每分钟费率仍然适用。</span><span class="sxs-lookup"><span data-stu-id="77851-p106">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="77851-138">用户帐户</span><span class="sxs-lookup"><span data-stu-id="77851-138">User accounts</span></span>

<span data-ttu-id="77851-139">所有 Microsoft 云服务的用户帐户均存储在 Active Directory (Azure AD) 租户中，其中包含用户帐户和组。</span><span class="sxs-lookup"><span data-stu-id="77851-139">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (Azure AD) tenant, which contains user accounts and groups.</span></span> <span data-ttu-id="77851-140">通过使用基于 Windows 服务器的服务 Azure AD Connect，Azure AD 租户可与你现有的 Active Directory 域服务 (AD DS) 帐户同步。</span><span class="sxs-lookup"><span data-stu-id="77851-140">An Azure AD tenant can be synchronized with your existing Active Directory Domain Services (AD DS) accounts using Azure AD Connect, a Windows server-based service.</span></span> <span data-ttu-id="77851-141">这叫做目录同步。</span><span class="sxs-lookup"><span data-stu-id="77851-141">This is known as directory synchronization.</span></span>
  
<span data-ttu-id="77851-142">图 3 显示了某个组织使用包含组织帐户的常见 Azure AD 租户进行多个订阅的示例。</span><span class="sxs-lookup"><span data-stu-id="77851-142">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="77851-143">**图 3：组织使用同一 Azure AD 租户进行的多个订阅**</span><span class="sxs-lookup"><span data-stu-id="77851-143">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![组织使用同一个 Azure AD 租户进行多个订阅的示例。](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="77851-145">租户</span><span class="sxs-lookup"><span data-stu-id="77851-145">Tenants</span></span>

<span data-ttu-id="77851-146">对于 SaaS 云服务，租户是承载提供云服务的服务器的区域位置。</span><span class="sxs-lookup"><span data-stu-id="77851-146">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services.</span></span> <span data-ttu-id="77851-147">例如，Contoso 公司选择欧洲地区为其巴黎总部的 15,000 名工作人员托管其 Microsoft 365、EMS 和 Dynamics 365 租户。</span><span class="sxs-lookup"><span data-stu-id="77851-147">For example, the Contoso Corporation chose the European region to host its Microsoft 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="77851-p109">Azure PaaS 服务和在 Azure IaaS 中托管的基于虚拟机的工作负荷可以在世界范围内的任何 Azure 数据中心拥有租户。在创建 Azure PaaS 应用或服务或 IaaS 工作负荷的元素时，应指定 Azure 数据中心（称为位置）。</span><span class="sxs-lookup"><span data-stu-id="77851-p109">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="77851-150">Azure AD 租户是包含帐户和组的 Azure AD 的特定实例。</span><span class="sxs-lookup"><span data-stu-id="77851-150">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span> <span data-ttu-id="77851-151">Microsoft 365 或 Dynamics 365 的付费或试用版订阅包括免费的 Azure AD 租户。</span><span class="sxs-lookup"><span data-stu-id="77851-151">Paid or trial subscriptions of Microsoft 365 or Dynamics 365 include a free Azure AD tenant.</span></span> <span data-ttu-id="77851-152">此 Azure AD 租户不包括其他 Azure 服务，且与 Azure 试用版或付费订阅不同。</span><span class="sxs-lookup"><span data-stu-id="77851-152">This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="77851-153">层次结构的摘要</span><span class="sxs-lookup"><span data-stu-id="77851-153">Summary of the hierarchy</span></span>

<span data-ttu-id="77851-154">以下是快速回顾：</span><span class="sxs-lookup"><span data-stu-id="77851-154">Here is a quick recap:</span></span>
  
- <span data-ttu-id="77851-155">组织可进行多个订阅</span><span class="sxs-lookup"><span data-stu-id="77851-155">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="77851-156">订阅可具有多个许可证</span><span class="sxs-lookup"><span data-stu-id="77851-156">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="77851-157">许可证可分配给各个用户帐户</span><span class="sxs-lookup"><span data-stu-id="77851-157">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="77851-158">用户帐户存储在 Azure AD 租户中</span><span class="sxs-lookup"><span data-stu-id="77851-158">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="77851-159">此处为一个有关组织、订阅、许可证和用户帐户关系的示例。</span><span class="sxs-lookup"><span data-stu-id="77851-159">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="77851-160">该组织由其公共域名识别。</span><span class="sxs-lookup"><span data-stu-id="77851-160">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="77851-161">带用户许可证的 Microsoft 365 E3 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-161">A Microsoft 365 E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="77851-162">带用户许可证的 Microsoft 365 E5 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-162">A Microsoft 365 E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="77851-163">具有用户许可证的 Dynamics 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-163">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="77851-164">多个 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-164">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="77851-165">常见 Azure AD 租户中的组织的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="77851-165">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="77851-166">多个 Microsoft 云服务订阅可使用同一 Azure AD 租户作为通用标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="77851-166">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider.</span></span> <span data-ttu-id="77851-167">包含本地 AD DS 的同步帐户的中心 Azure AD 租户可为组织提供基于云的标识即服务 (IDaaS)。</span><span class="sxs-lookup"><span data-stu-id="77851-167">A central Azure AD tenant that contains the synchronized accounts of your on-premises AD DS provides cloud-based Identity as a Service (IDaaS) for your organization.</span></span> 
  
<span data-ttu-id="77851-168">**图 4：适用于组织的同步本地帐户和 IDaaS**</span><span class="sxs-lookup"><span data-stu-id="77851-168">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![适用于组织的标识即服务 (IaaS) IDaaS。](media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="77851-p112">图 4 显示了如何将常见的 Azure AD 租户用于 Microsoft 的 SaaS 云产品、Azure PaaS 应用以及 Azure IaaS 中使用 Azure AD 域服务的虚拟机。Azure AD Connect 将本地 AD DS 林与 Azure AD 租户同步。</span><span class="sxs-lookup"><span data-stu-id="77851-p112">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="77851-172">合并多个 Microsoft 云服务的订阅</span><span class="sxs-lookup"><span data-stu-id="77851-172">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="77851-173">下表介绍了如果已经订阅一种类型的云服务（标签在第一列下），而要添加其他云服务的订阅（跨列），如何合并多个 Microsoft 服务。</span><span class="sxs-lookup"><span data-stu-id="77851-173">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="77851-174">**Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="77851-174">**Microsoft 365**</span></span>|<span data-ttu-id="77851-175">**Azure**</span><span class="sxs-lookup"><span data-stu-id="77851-175">**Azure**</span></span>|<span data-ttu-id="77851-176">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="77851-176">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="77851-177">**Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="77851-177">**Microsoft 365**</span></span> <br/> |<span data-ttu-id="77851-178">不适用</span><span class="sxs-lookup"><span data-stu-id="77851-178">NA</span></span>  <br/> |<span data-ttu-id="77851-179">从 Azure 门户向你的组织添加 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-179">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="77851-180">从 Microsoft 365 管理中心向你的组织添加 Dynamics 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-180">You add a Dynamics 365 subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |
|<span data-ttu-id="77851-181">**Azure**</span><span class="sxs-lookup"><span data-stu-id="77851-181">**Azure**</span></span> <br/> |<span data-ttu-id="77851-182">向你的组织添加 Microsoft 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-182">You add a Microsoft 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="77851-183">不适用</span><span class="sxs-lookup"><span data-stu-id="77851-183">NA</span></span>  <br/> |<span data-ttu-id="77851-184">向你的组织添加 Dynamics 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-184">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="77851-185">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="77851-185">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="77851-186">向你的组织添加 Microsoft 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-186">You add a Microsoft 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="77851-187">从 Azure 门户向你的组织添加 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-187">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="77851-188">不适用</span><span class="sxs-lookup"><span data-stu-id="77851-188">NA</span></span>  <br/> |
   
<span data-ttu-id="77851-189">为组织添加基于 Microsoft SaaS 的服务订阅的简便方法是通过管理中心来完成：</span><span class="sxs-lookup"><span data-stu-id="77851-189">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the admin center:</span></span>
  
1. <span data-ttu-id="77851-190">使用全局管理员帐户登录 Microsoft 365 管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com))。</span><span class="sxs-lookup"><span data-stu-id="77851-190">Sign in to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) with your global administrator account.</span></span>
    
2. <span data-ttu-id="77851-191">从“管理中心”\*\*\*\* 主页的左侧导航栏，依次单击“帐单”\*\*\*\* 和“购买服务”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77851-191">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="77851-192">在“购买服务”\*\*\*\* 页上，购买你的新订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-192">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="77851-193">管理中心将 Microsoft 365 订阅的组织和 Azure AD 租户分配到基于 SaaS 的云产品的新订阅。</span><span class="sxs-lookup"><span data-stu-id="77851-193">The admin center assigns the organization and Azure AD tenant of your Microsoft 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="77851-194">使用与你的 Microsoft 365 订阅相同的组织和 Azure AD 租户添加 Azure 订阅：</span><span class="sxs-lookup"><span data-stu-id="77851-194">To add an Azure subscription with the same organization and Azure AD tenant as your Microsoft 365 subscription:</span></span>
  
1. <span data-ttu-id="77851-195">使用 Microsoft 365 全局管理员帐户登录到 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="77851-195">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Microsoft 365 global administrator account.</span></span>
    
2. <span data-ttu-id="77851-196">在左侧导航栏中，单击“订阅”\*\*\*\*，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77851-196">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="77851-197">在“添加订阅”\*\*\*\* 页上，选择一项服务并完成付款信息和协议。</span><span class="sxs-lookup"><span data-stu-id="77851-197">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="77851-198">如果分别购买 Azure 和Microsoft 365 订阅并且希望从 Azure 订阅访问 Microsoft 365 Azure AD 租户，请参阅[将现有 Azure 订阅添加到 Azure Active Directory 租户](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)中的说明。</span><span class="sxs-lookup"><span data-stu-id="77851-198">If you purchased Azure and Microsoft 365 subscriptions separately and want to access the Microsoft 365 Azure AD tenant from your Azure subscription, see the instructions in [Add an existing Azure subscription to your Azure Active Directory tenant](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="77851-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77851-199">See also</span></span>

[<span data-ttu-id="77851-200">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="77851-200">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="77851-201">SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型</span><span class="sxs-lookup"><span data-stu-id="77851-201">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="77851-202">混合解决方案</span><span class="sxs-lookup"><span data-stu-id="77851-202">Hybrid solutions</span></span>](hybrid-solutions.md)

## <a name="next-step"></a><span data-ttu-id="77851-203">后续步骤</span><span class="sxs-lookup"><span data-stu-id="77851-203">Next step</span></span>

[<span data-ttu-id="77851-204">评估 Microsoft 365 网络连接</span><span class="sxs-lookup"><span data-stu-id="77851-204">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
