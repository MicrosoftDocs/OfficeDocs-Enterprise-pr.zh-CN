---
title: 针对 Microsoft 云产品/服务的订阅、许可证、帐户和租户
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
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 摘要：了解 Microsoft 云产品/服务中组织、订阅、许可证、用户帐户和租户的关系。
ms.openlocfilehash: 889dbc376d3eb90af46bb281715ba391d7ee7712
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2018
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="d25c5-103">针对 Microsoft 云产品/服务的订阅、许可证、帐户和租户</span><span class="sxs-lookup"><span data-stu-id="d25c5-103">Subscriptions, licenses, accounts, and tenants for Microsoft’s cloud offerings</span></span>

 <span data-ttu-id="d25c5-104">**摘要：** 了解 Microsoft 云产品/服务中组织、订阅、许可证、用户帐户和租户的关系。</span><span class="sxs-lookup"><span data-stu-id="d25c5-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft’s cloud offerings.</span></span>
  
<span data-ttu-id="d25c5-105">为确保跨其云产品/服务使用一致的身份和帐单，Microsoft 提供了组织、订阅、许可证和用户帐户的层次结构。</span><span class="sxs-lookup"><span data-stu-id="d25c5-105">Microsoft provides a hierarchy  of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="d25c5-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="d25c5-106">Microsoft Office 365</span></span>
    
    <span data-ttu-id="d25c5-107">有关详细信息，请参阅[商业版计划和定价](https://products.office.com/business/compare-office-365-for-business-plans)。</span><span class="sxs-lookup"><span data-stu-id="d25c5-107">See [business plans and pricinghttps://products.office.com/business/compare-office-365-for-business-plans](https://products.office.com/business/compare-office-365-for-business-plans) for more information.</span></span>
    
- <span data-ttu-id="d25c5-108">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="d25c5-108">Microsoft Azure</span></span>
    
    <span data-ttu-id="d25c5-109">有关详细信息，请参阅 [Azure 定价](https://azure.microsoft.com/pricing/)。</span><span class="sxs-lookup"><span data-stu-id="d25c5-109">See [Azure pricinghttps://azure.microsoft.com/pricing/](https://azure.microsoft.com/pricing/) for more information.</span></span>
    
- <span data-ttu-id="d25c5-110">Microsoft Intune 和企业移动性 + 安全性 (EMS)</span><span class="sxs-lookup"><span data-stu-id="d25c5-110">Microsoft Intune and the Enterprise Mobility Suite (EMS) </span></span>
    
    <span data-ttu-id="d25c5-111">有关详细信息，请参阅 [Intune 定价](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)。</span><span class="sxs-lookup"><span data-stu-id="d25c5-111">See [Intune pricinghttps://www.microsoft.com/en-us/cloud-platform/microsoft-intune-pricing](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) for more information.</span></span>
    
- <span data-ttu-id="d25c5-112">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="d25c5-112">Microsoft Dynamics 365</span></span>
    
    <span data-ttu-id="d25c5-113">有关详细信息，请参阅 [Dynamics 365 定价](https://dynamics.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="d25c5-113">See [Dynamics 365 pricinghttps://www.microsoft.com/en-us/dynamics/dynamics-365](https://dynamics.microsoft.com/) for more information.</span></span>
    
## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="d25c5-114">层次结构的元素</span><span class="sxs-lookup"><span data-stu-id="d25c5-114">Elements of the hierarchy</span></span>

<span data-ttu-id="d25c5-115">以下是层次结构的元素：</span><span class="sxs-lookup"><span data-stu-id="d25c5-115">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="d25c5-116">组织</span><span class="sxs-lookup"><span data-stu-id="d25c5-116">Organization</span></span>

<span data-ttu-id="d25c5-117">组织表示使用 Microsoft 云服务的业务实体，通常由公用域名系统 (DNS) 域名标识，例如 contoso.com。组织是订阅的容器。</span><span class="sxs-lookup"><span data-stu-id="d25c5-117">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by a public Domain Name System (DNS) domain name such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="d25c5-118">订阅</span><span class="sxs-lookup"><span data-stu-id="d25c5-118">Subscriptions</span></span>

<span data-ttu-id="d25c5-p101">订阅是与 Microsoft 就使用一个或多个 Microsoft 云平台或服务签订的协议，其费用基于每个用户许可证费或云资源的使用量进行累计。Microsoft 基于软件即服务 (SaaS) 的云服务（Office 365、Intune/EMS 和 Dynamics 365）按用户收取许可证费用。Microsoft 的平台即服务 (PaaS) 和基础设施即服务 (IaaS) 云服务 (Azure) 根据云资源使用量收取费用。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p101">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption. Microsoft’s Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees. Microsoft’s Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
  
<span data-ttu-id="d25c5-p102">你也可以使用试用版订阅，此订阅会在一定时间后或使用费用后过期。你可以将试用版订阅转换为付费订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p102">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="d25c5-p103">组织可订阅多个 Micrososft 云服务，图 1 显示了一个示例。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p103">Organizations can have multiple subscriptions for Microsoft’s cloud offerings. Figure 1 shows an example.</span></span>
  
<span data-ttu-id="d25c5-126">**图 1：组织的多个订阅示例**</span><span class="sxs-lookup"><span data-stu-id="d25c5-126">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![组织订阅多个 Micrososft 云服务的示例。](images/Subscriptions/Subscriptions_Fig1.png)

  
<span data-ttu-id="d25c5-128">图 1 显示了一个组织，其具有多个 Office 365 订阅、一个 Intune 订阅、一个 Dynamics 365 订阅以及多个 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-128">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>
  
### <a name="licenses"></a><span data-ttu-id="d25c5-129">许可证</span><span class="sxs-lookup"><span data-stu-id="d25c5-129">Licenses</span></span>

<span data-ttu-id="d25c5-p104">对于 Microsoft 的 SaaS 云服务，一个许可证允许一个特定用户帐户使用云产品的服务。作为订阅的一部分，会按月收取你固定的费用。管理员将许可证分配给订阅中的各个用户帐户。对于图 2 中的示例，Contoso 公司订阅了具有 100 个许可证的 Office 365 企业版 E5，可使最多 100 个单个用户帐户使用企业版 E5 的功能和服务。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p104">For Microsoft’s SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering. You are charged a fixed monthly fee as part of your subscription. Administrators assign licenses to individual user accounts in the subscription. For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="d25c5-134">**图 2：组织基于 SaaS 的订阅内的许可证**</span><span class="sxs-lookup"><span data-stu-id="d25c5-134">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Microsoft 基于 SaaS 的云服务订阅中的多个许可证示例。](images/Subscriptions/Subscriptions_Fig2.png)
  
<span data-ttu-id="d25c5-136">对于基于 Azure PaaS 的云服务，软件许可证是服务定价的一部分。</span><span class="sxs-lookup"><span data-stu-id="d25c5-136">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="d25c5-p105">对于基于 Azure IaaS 的虚拟机，使用在虚拟机映像上安装的软件或应用程序可能需要其他许可证。某些虚拟机映像安装了授权版软件，并且成本包括在服务器的每分钟费率中。例如，SQL Server 2014 和 SQL Server 2016 的虚拟机映像。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p105">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="d25c5-p106">某些虚拟机映像安装了试用版应用程序，在试用期过后需要其他软件应用程序许可证。例如，SharePoint Server 2016 试用版虚拟机映像包括预安装的试用版 SharePoint Server 2016。若要在试用版过期后继续使用 SharePoint Server 2016，你必须从 Microsoft 购买 SharePoint Server 2016 许可证和客户端许可证。这些费用与 Azure 订阅是分开的，而运行虚拟机的每分钟费率仍然适用。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p106">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trail expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="d25c5-144">用户帐户</span><span class="sxs-lookup"><span data-stu-id="d25c5-144">User accounts</span></span>

<span data-ttu-id="d25c5-p107">所有 Microsoft 云服务的用户帐户均存储在 Active Directory (AD) 租户中，其中包含用户帐户和组。通过使用基于 Windows 服务器的服务 Azure AD Connect，Azure AD 租户可与你现有的 Windows Server AD 帐户同步。这叫做目录同步 (DirSync)。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p107">User accounts for all of Microsoft’s cloud offerings are stored in an Azure Active Directory (AD) tenant, which contains user accounts and groups. An Azure AD tenant can be synchronized with your existing Windows Server AD accounts using Azure AD Connect, a Windows server-based service. This is known as directory synchronization (DirSync).</span></span>
  
<span data-ttu-id="d25c5-148">图 3 显示了某个组织使用包含组织帐户的常见 Azure AD 租户进行多个订阅的示例。</span><span class="sxs-lookup"><span data-stu-id="d25c5-148">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="d25c5-149">**图 3：组织使用同一 Azure AD 租户进行的多个订阅**</span><span class="sxs-lookup"><span data-stu-id="d25c5-149">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![组织使用同一个 Azure AD 租户进行多个订阅的示例。](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="d25c5-151">租户</span><span class="sxs-lookup"><span data-stu-id="d25c5-151">Tenants</span></span>

<span data-ttu-id="d25c5-p108">对于 SaaS 云服务，租户是承载提供云服务的服务器的区域位置。例如，Contoso 公司选择欧洲地区为其巴黎总部的 15,000 名工作人员托管其 Office 365、EMS 和 Dynamics 365 租户。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p108">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="d25c5-p109">Azure PaaS 服务和在 Azure IaaS 中托管的基于虚拟机的工作负荷可以在世界范围内的任何 Azure 数据中心拥有租户。在创建 Azure PaaS 应用或服务或 IaaS 工作负荷的元素时，应指定 Azure 数据中心（称为位置）。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p109">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="d25c5-p110">Azure AD 租户是包含帐户和组的 Azure AD 的特定实例。Office 365、Dynamics 365 或 Intune/EMS 的付费或试用版订阅包括免费的 Azure AD 租户。此 Azure AD 租户不包括其他 Azure 服务，且与 Azure 试用版或付费订阅不同。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p110">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="d25c5-159">层次结构的摘要</span><span class="sxs-lookup"><span data-stu-id="d25c5-159">Summary of the hierarchy</span></span>

<span data-ttu-id="d25c5-160">以下是快速回顾：</span><span class="sxs-lookup"><span data-stu-id="d25c5-160">Here is a quick recap:</span></span>
  
- <span data-ttu-id="d25c5-161">组织可进行多个订阅</span><span class="sxs-lookup"><span data-stu-id="d25c5-161">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="d25c5-162">订阅可具有多个许可证</span><span class="sxs-lookup"><span data-stu-id="d25c5-162">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="d25c5-163">许可证可分配给各个用户帐户</span><span class="sxs-lookup"><span data-stu-id="d25c5-163">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="d25c5-164">用户帐户存储在 Azure AD 租户中</span><span class="sxs-lookup"><span data-stu-id="d25c5-164">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="d25c5-165">此处为一个有关组织、订阅、许可证和用户帐户关系的示例。</span><span class="sxs-lookup"><span data-stu-id="d25c5-165">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="d25c5-166">该组织由其公共域名识别。</span><span class="sxs-lookup"><span data-stu-id="d25c5-166">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="d25c5-167">具有用户许可证的 Office 365 企业版 E3 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-167">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="d25c5-168">具有用户许可证的 Office 365 企业版 E5 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-168">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="d25c5-169">具有用户许可证的 EMS 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-169">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="d25c5-170">具有用户许可证的 Dynamics 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-170">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="d25c5-171">多个 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-171">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="d25c5-172">常见 Azure AD 租户中的组织的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d25c5-172">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="d25c5-p111">多个 Microsoft 云服务订阅可使用同一 Azure AD 租户作为通用标识提供程序。包含本地 Windows Server AD 的同步帐户的中心 Azure AD 租户可为组织提供基于云的标识即服务 (IDaaS)。如图 4 中所示。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p111">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider. A central Azure AD tenant that contains the synchronized accounts of your on-premises Windows Server AD provides cloud-based Identity as a Service (IDaaS) for your organization. This is shown in Figure 4.</span></span>
  
<span data-ttu-id="d25c5-176">**图 4：适用于组织的同步本地帐户和 IDaaS**</span><span class="sxs-lookup"><span data-stu-id="d25c5-176">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![适用于组织的标识即服务 (IaaS) IDaaS。](images/Subscriptions/Subscriptions_Fig4.png)
  
<span data-ttu-id="d25c5-p112">图 4 显示了如何将常见的 Azure AD 租户用于 Microsoft 的 SaaS 云产品、Azure PaaS 应用以及 Azure IaaS 中使用 Azure AD 域服务的虚拟机。Azure AD Connect 将本地 Windows Server AD 林与 Azure AD 租户同步。</span><span class="sxs-lookup"><span data-stu-id="d25c5-p112">Figure 4 shows how a common Azure AD tenant is utilized by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="d25c5-180">有关 Microsoft 云产品/服务中标识集成的详细信息，请参阅[面向企业架构师的 Microsoft 云标识](https://aka.ms/cloudarchidentity)。</span><span class="sxs-lookup"><span data-stu-id="d25c5-180">For more information about identity integration across Microsoft’s cloud offerings, see [Microsoft Cloud Identity for Enterprise Architectshttps://aka.ms/cloudarchidentity](https://aka.ms/cloudarchidentity).</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="d25c5-181">合并多个 Microsoft 云服务的订阅</span><span class="sxs-lookup"><span data-stu-id="d25c5-181">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="d25c5-182">下表介绍了如果已经订阅一种类型的云服务（标签在第一列下），而要添加其他云服务的订阅（跨列），如何合并多个 Microsoft 服务。</span><span class="sxs-lookup"><span data-stu-id="d25c5-182">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="d25c5-183">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="d25c5-183">**Office 365**</span></span>|<span data-ttu-id="d25c5-184">**Azure**</span><span class="sxs-lookup"><span data-stu-id="d25c5-184">**Azure**</span></span>|<span data-ttu-id="d25c5-185">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="d25c5-185">**Intune/EMS**</span></span>|<span data-ttu-id="d25c5-186">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="d25c5-186">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="d25c5-187">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="d25c5-187">**Office 365**</span></span> <br/> |<span data-ttu-id="d25c5-188">NA</span><span class="sxs-lookup"><span data-stu-id="d25c5-188">NA</span></span>  <br/> |<span data-ttu-id="d25c5-189">从 Azure 门户向你的组织添加 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-189">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="d25c5-190">从 Office 365 门户向你的组织添加 Intune/EMS 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-190">You add an Intune/EMS subscription to your organization from the Office 365 portal.</span></span>  <br/> |<span data-ttu-id="d25c5-191">从 Office 365 门户向你的组织添加 Dynamics 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-191">You add a Dynamics 365 subscription to your organization from the Office 365 portal.</span></span>  <br/> |
|<span data-ttu-id="d25c5-192">**Azure**</span><span class="sxs-lookup"><span data-stu-id="d25c5-192">**Azure**</span></span> <br/> |<span data-ttu-id="d25c5-193">向你的组织添加 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-193">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d25c5-194">NA</span><span class="sxs-lookup"><span data-stu-id="d25c5-194">NA</span></span>  <br/> |<span data-ttu-id="d25c5-195">向你的组织添加 Intune/EMS 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-195">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d25c5-196">向你的组织添加 Dynamics 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-196">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="d25c5-197">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="d25c5-197">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="d25c5-198">向你的组织添加 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-198">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d25c5-199">从 Azure 门户向你的组织添加 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-199">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="d25c5-200">NA</span><span class="sxs-lookup"><span data-stu-id="d25c5-200">NA</span></span>  <br/> |<span data-ttu-id="d25c5-201">向你的组织添加 Dynamics 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-201">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="d25c5-202">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="d25c5-202">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="d25c5-203">向你的组织添加 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-203">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d25c5-204">从 Azure 门户向你的组织添加 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-204">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="d25c5-205">向你的组织添加 Intune/EMS 订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-205">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="d25c5-206">NA</span><span class="sxs-lookup"><span data-stu-id="d25c5-206">NA</span></span>  <br/> |
   
<span data-ttu-id="d25c5-207">为组织添加基于 Microsoft SaaS 的服务订阅的简便方法是通过 Office 365 Admin 中心来完成：</span><span class="sxs-lookup"><span data-stu-id="d25c5-207">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the Office 365 Admin center:</span></span>
  
1. <span data-ttu-id="d25c5-208">使用你的全局管理员帐户登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com))，然后单击“管理员”****。</span><span class="sxs-lookup"><span data-stu-id="d25c5-208">Sign in to the Office 365 portal ( https://portal.office.com https://portal.office.com ) with your global administrator account, and then click Admin.</span></span>
    
2. <span data-ttu-id="d25c5-209">从“管理中心”**** 主页的左侧导航栏，依次单击“帐单”**** 和“购买服务”****。</span><span class="sxs-lookup"><span data-stu-id="d25c5-209">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="d25c5-210">在“购买服务”**** 页上，购买你的新订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-210">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="d25c5-211">Office 365 管理中心将 Office 365 订阅的组织和 Azure AD 租户分配到基于 SaaS 的云产品的新订阅。</span><span class="sxs-lookup"><span data-stu-id="d25c5-211">The Office 365 Admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="d25c5-212">使用与你的 Office 365 订阅相同的组织和 Azure AD 租户添加 Azure 订阅：</span><span class="sxs-lookup"><span data-stu-id="d25c5-212">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="d25c5-213">使用 Office 365 全局管理员帐户登录到 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="d25c5-213">Sign in to the Azure portal ( https://portal.azure.com https://portal.azure.com ) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="d25c5-214">在左侧导航栏中，单击“订阅”****，然后单击“添加”****。</span><span class="sxs-lookup"><span data-stu-id="d25c5-214">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="d25c5-215">在“添加订阅”**** 页上，选择一项服务并完成付款信息和协议。</span><span class="sxs-lookup"><span data-stu-id="d25c5-215">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="d25c5-216">如果分别购买 Azure 和 Office 365 订阅并且希望从 Azure 订阅访问 Office 365 Azure AD 租户，请参阅[将 Office 365 租户与 Azure 订阅关联](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription)中的说明。</span><span class="sxs-lookup"><span data-stu-id="d25c5-216">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Associate an Office 365 tenant with an Azure subscriptionhttps://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d25c5-217">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d25c5-217">See Also</span></span>

[<span data-ttu-id="d25c5-218">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="d25c5-218">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="d25c5-219">云应用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="d25c5-219">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="d25c5-220">SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型</span><span class="sxs-lookup"><span data-stu-id="d25c5-220">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="d25c5-221">混合解决方案</span><span class="sxs-lookup"><span data-stu-id="d25c5-221">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="d25c5-222">Contoso Corporation 的订阅、许可证和用户帐户</span><span class="sxs-lookup"><span data-stu-id="d25c5-222">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



