---
title: Office 365 中的管理访问控制
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 摘要： Office 365 的管理访问控制和数据分类概述。
ms.openlocfilehash: e8cc470c617deea7435841f276b772b0a8ef17a3
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067259"
---
# <a name="administrative-access-controls-in-office-365"></a><span data-ttu-id="62c37-103">Office 365 中的管理访问控制</span><span class="sxs-lookup"><span data-stu-id="62c37-103">Administrative Access Controls in Office 365</span></span> 

<span data-ttu-id="62c37-104">Microsoft 已在系统和控件中进行了大量投资，以自动化大多数 Office 365 操作，同时有意限制 Microsoft 对客户内容的访问权限。</span><span class="sxs-lookup"><span data-stu-id="62c37-104">Microsoft has invested heavily in systems and controls that automate most Office 365 operations while intentionally limiting access to customer content by Microsoft.</span></span> <span data-ttu-id="62c37-105">人类控制服务，软件运行服务。</span><span class="sxs-lookup"><span data-stu-id="62c37-105">Humans govern the service, and software operates the service.</span></span> <span data-ttu-id="62c37-106">这使 Microsoft 能够在规模扩展时管理 Office 365，并管理对客户内容的内部威胁的风险。</span><span class="sxs-lookup"><span data-stu-id="62c37-106">This enables Microsoft to manage Office 365 at scale and manage the risks of internal threats to customer content.</span></span>

<span data-ttu-id="62c37-107">By default, Microsoft engineers have zero standing administrative privileges and zero standing access to customer content in Office 365.</span><span class="sxs-lookup"><span data-stu-id="62c37-107">By default, Microsoft engineers have zero standing administrative privileges and zero standing access to customer content in Office 365.</span></span> <span data-ttu-id="62c37-108">Microsoft 工程师可在有限的时间段中对客户的内容进行有限的审核和安全访问。</span><span class="sxs-lookup"><span data-stu-id="62c37-108">A Microsoft engineer can have limited, audited, and secured access to a customer's content for a limited amount of time.</span></span> <span data-ttu-id="62c37-109">只有在服务操作必要时才进行访问，并且仅当由 Microsoft 高级管理的成员批准时才能访问。</span><span class="sxs-lookup"><span data-stu-id="62c37-109">Access is only when necessary for service operations and only when approved by a member of Microsoft senior management.</span></span> <span data-ttu-id="62c37-110">对于客户密码箱许可的客户，客户将提供对 Office 365 上托管内容的访问审批。</span><span class="sxs-lookup"><span data-stu-id="62c37-110">For Customer Lockbox licensed customers, the customer provides access approval to their content hosted on Office 365.</span></span>

<span data-ttu-id="62c37-111">Microsoft 使用多种形式的云传递提供了在线服务：</span><span class="sxs-lookup"><span data-stu-id="62c37-111">Microsoft provides online services using multiple forms of cloud delivery:</span></span>

- <span data-ttu-id="62c37-112">**公共云：** 包括在北美、南美洲、欧洲、亚洲、澳大利亚等托管的 Office 365、Azure 和其他服务的多租户版本。</span><span class="sxs-lookup"><span data-stu-id="62c37-112">**Public Clouds:** Includes multi-tenant versions of Office 365, Azure, and other services hosted in North America, South America, Europe, Asia, Australia, etc.</span></span>
- <span data-ttu-id="62c37-113">**国家/地区云：** 包括美国以外的所有 sovereign 和第三方运营云（前面提到的云除外），例如中国（由世纪互联运营）的 Office 365 和德国的 Office 365 （由 Microsoft 使用，但在一个采用德语数据受托者的模型下）。德国电信，控制和监控 Microsoft 对客户数据和包含客户数据的系统的访问。</span><span class="sxs-lookup"><span data-stu-id="62c37-113">**National Clouds:** Includes all sovereign and third party-operated clouds outside of the United States (except ones noted previously), such as Office 365 in China (operated by 21Vianet), and Office 365 in Germany (operated by Microsoft, but under a model in which a German data trustee, Deutsche Telekom, controls and monitors Microsoft's access to Customer Data and systems that contain Customer Data).</span></span>
- <span data-ttu-id="62c37-114">**政府群：** 包含适用于美国政府客户的 Office 365 和 Azure 服务。</span><span class="sxs-lookup"><span data-stu-id="62c37-114">**Government Clouds:** Includes Office 365 and Azure services that are available to United States government customers.</span></span>

<span data-ttu-id="62c37-115">出于本文的目的，Office 365 服务包括：</span><span class="sxs-lookup"><span data-stu-id="62c37-115">For purposes of this article, Office 365 services include:</span></span>

- [<span data-ttu-id="62c37-116">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="62c37-116">Exchange Online</span></span>](https://docs.microsoft.com/Exchange/exchange-online)
- [<span data-ttu-id="62c37-117">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="62c37-117">Exchange Online Protection</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [<span data-ttu-id="62c37-118">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="62c37-118">SharePoint Online</span></span>](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [<span data-ttu-id="62c37-119">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="62c37-119">OneDrive for Business</span></span>](https://docs.microsoft.com/OneDrive/onedrive)
- [<span data-ttu-id="62c37-120">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="62c37-120">Skype for Business</span></span>](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [<span data-ttu-id="62c37-121">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="62c37-121">Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [<span data-ttu-id="62c37-122">Yammer</span><span class="sxs-lookup"><span data-stu-id="62c37-122">Yammer</span></span>](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a><span data-ttu-id="62c37-123">Office 365 访问控制</span><span class="sxs-lookup"><span data-stu-id="62c37-123">Office 365 Access Controls</span></span>

<span data-ttu-id="62c37-124">出于访问控制目的，Microsoft 将 Office 365 数据分类为客户数据或其他类型的数据。</span><span class="sxs-lookup"><span data-stu-id="62c37-124">For access control purposes, Microsoft categorizes Office 365 data as Customer data or other types of data.</span></span>

### <a name="customer-data"></a><span data-ttu-id="62c37-125">客户数据</span><span class="sxs-lookup"><span data-stu-id="62c37-125">Customer data</span></span>

<span data-ttu-id="62c37-126">客户数据是使用 Office 365 服务时代表客户提供或代表客户提供的所有数据。</span><span class="sxs-lookup"><span data-stu-id="62c37-126">Customer data is all data provided by or on behalf of a customer when using Office 365 services.</span></span> <span data-ttu-id="62c37-127">这是由 Office 365 用户直接创建或上载的客户内容，包括：</span><span class="sxs-lookup"><span data-stu-id="62c37-127">This is customer content directly created or uploaded by Office 365 users, including:</span></span>

- <span data-ttu-id="62c37-128">电子邮件</span><span class="sxs-lookup"><span data-stu-id="62c37-128">Emails</span></span>
- <span data-ttu-id="62c37-129">SharePoint Online 内容</span><span class="sxs-lookup"><span data-stu-id="62c37-129">SharePoint Online content</span></span>
- <span data-ttu-id="62c37-130">即时消息</span><span class="sxs-lookup"><span data-stu-id="62c37-130">Instant messages</span></span>
- <span data-ttu-id="62c37-131">日历项目</span><span class="sxs-lookup"><span data-stu-id="62c37-131">Calendar items</span></span>
- <span data-ttu-id="62c37-132">Documents</span><span class="sxs-lookup"><span data-stu-id="62c37-132">Documents</span></span>
- <span data-ttu-id="62c37-133">联系人</span><span class="sxs-lookup"><span data-stu-id="62c37-133">Contacts</span></span>
- <span data-ttu-id="62c37-134">最终用户身份信息（EUII）（对用户而言是唯一的，或对单个用户而言是 linkable 但不包含客户内容的数据）。</span><span class="sxs-lookup"><span data-stu-id="62c37-134">End-user identifiable information (EUII) (data that is unique to a user or that is linkable to an individual user but does not include customer content).</span></span>

### <a name="other-types-of-data"></a><span data-ttu-id="62c37-135">其他类型的数据</span><span class="sxs-lookup"><span data-stu-id="62c37-135">Other types of data</span></span>

<span data-ttu-id="62c37-136">其他类型的数据包括：</span><span class="sxs-lookup"><span data-stu-id="62c37-136">Other types of data include:</span></span>

- <span data-ttu-id="62c37-137">**帐户数据：** 包括管理数据（管理员在注册或购买服务时提供的信息）和付款数据（有关付款仪器的信息，如信用卡详细信息）。</span><span class="sxs-lookup"><span data-stu-id="62c37-137">**Account data:** Includes administrative data (information provided by administrators when they sign-up or purchase services), and payment data (information about payment instruments, such as credit card details).</span></span>
- <span data-ttu-id="62c37-138">**组织的可识别信息：** 包含用于标识租户、使用情况数据，而不是 linkable 给个人用户或包含在客户内容中的数据。</span><span class="sxs-lookup"><span data-stu-id="62c37-138">**Organizationally identifiable information:** Includes data used to identify a tenant, usage data, and not linkable to an individual user or included in customer content.</span></span>
- <span data-ttu-id="62c37-139">**系统元数据：** 包括包含配置设置、系统状态、Microsoft IP 地址和订阅和租户的技术信息的服务日志。</span><span class="sxs-lookup"><span data-stu-id="62c37-139">**System metadata:** Includes service logs that contain configuration settings, system status, Microsoft IP addresses, and technical information about subscriptions and tenants.</span></span>

<span data-ttu-id="62c37-140">Microsoft 已建立了访问控制机制，以确保没有人撤销对客户数据或访问控制数据的访问权限。</span><span class="sxs-lookup"><span data-stu-id="62c37-140">Microsoft has established access control mechanisms to ensure that no one has unapproved access to Customer Data or access control data.</span></span> <span data-ttu-id="62c37-141">访问控制数据管理对环境中其他类型的数据或函数的访问，包括对客户内容或 EUII、Microsoft 密码、安全证书和其他与身份验证相关的数据的访问。</span><span class="sxs-lookup"><span data-stu-id="62c37-141">Access control data manages access to other types of data or functions within the environment, including access to customer content or EUII, Microsoft passwords, security certificates, and other authentication-related data.</span></span> <span data-ttu-id="62c37-142">访问控制机制还可防止对 Office 365 生产环境进行未批准的物理、逻辑或远程访问。</span><span class="sxs-lookup"><span data-stu-id="62c37-142">Access control mechanisms also guard against unapproved physical, logical, or remote access to the Office 365 production environment.</span></span>

<span data-ttu-id="62c37-143">Microsoft 使用的 access 控件有三个类别，用于运行 Office 365：</span><span class="sxs-lookup"><span data-stu-id="62c37-143">There are three categories of access controls used by Microsoft for operating Office 365:</span></span>

- <span data-ttu-id="62c37-144">隔离控件</span><span class="sxs-lookup"><span data-stu-id="62c37-144">Isolation Controls</span></span>
- <span data-ttu-id="62c37-145">人员控制</span><span class="sxs-lookup"><span data-stu-id="62c37-145">Personnel Controls</span></span>
- <span data-ttu-id="62c37-146">技术控制</span><span class="sxs-lookup"><span data-stu-id="62c37-146">Technology Controls</span></span>

<span data-ttu-id="62c37-147">组合后，这些控件有助于防止和检测 Office 365 中的恶意操作。</span><span class="sxs-lookup"><span data-stu-id="62c37-147">When combined, these controls help prevent and detect malicious actions in Office 365.</span></span> <span data-ttu-id="62c37-148">除了 Microsoft 使用的隔离、人员和技术控件之外，还有第四个类别的控件：由客户实施的控件。</span><span class="sxs-lookup"><span data-stu-id="62c37-148">In addition to the isolation, personnel, and technology controls used by Microsoft, there is a fourth category of controls: those implemented by customers.</span></span>

<span data-ttu-id="62c37-149">Office 365 允许您以与在本地环境中管理数据的方式管理数据。</span><span class="sxs-lookup"><span data-stu-id="62c37-149">Office 365 allows you to manage data the same way data is managed in on-premises environments.</span></span> <span data-ttu-id="62c37-150">注册 Office 365 组织的人员将自动成为全局管理员。</span><span class="sxs-lookup"><span data-stu-id="62c37-150">The person who signs up an organization for Office 365 automatically becomes a global administrator.</span></span> <span data-ttu-id="62c37-151">全局管理员可以访问管理门户中的所有功能，并且可以：</span><span class="sxs-lookup"><span data-stu-id="62c37-151">The global admin has access to all features in Management Portals and can:</span></span>

- <span data-ttu-id="62c37-152">创建或编辑用户</span><span class="sxs-lookup"><span data-stu-id="62c37-152">Create or edit users</span></span>
- <span data-ttu-id="62c37-153">向其他人分配管理员角色</span><span class="sxs-lookup"><span data-stu-id="62c37-153">Assign admin roles to others</span></span>
- <span data-ttu-id="62c37-154">重置用户密码</span><span class="sxs-lookup"><span data-stu-id="62c37-154">Reset user passwords</span></span>
- <span data-ttu-id="62c37-155">管理用户许可证</span><span class="sxs-lookup"><span data-stu-id="62c37-155">Manage user licenses</span></span>
- <span data-ttu-id="62c37-156">管理域</span><span class="sxs-lookup"><span data-stu-id="62c37-156">Manage domains</span></span>
- <span data-ttu-id="62c37-157">批准客户密码箱请求</span><span class="sxs-lookup"><span data-stu-id="62c37-157">Approve Customer Lockbox requests</span></span>

<span data-ttu-id="62c37-158">建议每个组织至少配置两个管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="62c37-158">We recommend that each organization configure at least two admin accounts.</span></span> <span data-ttu-id="62c37-159">对于大型企业组织，我们建议专门的管理员帐户来提供不同的功能。</span><span class="sxs-lookup"><span data-stu-id="62c37-159">For large enterprise organizations, we recommend specialized admin accounts that serve different functions.</span></span>

<span data-ttu-id="62c37-160">有关分配管理员角色和权限的信息，请参阅[在 office 365 中分配管理员角色](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504)和[关于 Office 365 管理员角色](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D)。</span><span class="sxs-lookup"><span data-stu-id="62c37-160">For information about assigning admin roles and permissions, see [Assigning admin roles in Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) and [About Office 365 admin roles](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).</span></span>

## <a name="related-links"></a><span data-ttu-id="62c37-161">相关链接</span><span class="sxs-lookup"><span data-stu-id="62c37-161">Related Links</span></span>

- [<span data-ttu-id="62c37-162">隔离控件</span><span class="sxs-lookup"><span data-stu-id="62c37-162">Isolation Controls</span></span>](office-365-isolation-controls.md)
- [<span data-ttu-id="62c37-163">人员控制</span><span class="sxs-lookup"><span data-stu-id="62c37-163">Personnel Controls</span></span>](office-365-personnel-controls.md)
- [<span data-ttu-id="62c37-164">技术控制</span><span class="sxs-lookup"><span data-stu-id="62c37-164">Technology Controls</span></span>](office-365-technology-controls.md)
- [<span data-ttu-id="62c37-165">监视和审核访问控制</span><span class="sxs-lookup"><span data-stu-id="62c37-165">Monitoring and Auditing Access Controls</span></span>](office-365-monitoring-and-auditing-access-controls.md)
- [<span data-ttu-id="62c37-166">Yammer Enterprise访问控制</span><span class="sxs-lookup"><span data-stu-id="62c37-166">Yammer Enterprise Access Controls</span></span>](office-365-yammer-enterprise-access-controls.md)