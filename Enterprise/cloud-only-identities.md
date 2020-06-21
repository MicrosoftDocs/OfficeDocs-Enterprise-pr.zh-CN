---
title: Microsoft 365 仅限云身份标识
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/09/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 介绍如何在 Microsoft 365 订阅使用仅云标识时创建用户和组。
ms.openlocfilehash: f510d82186e9a44c20bd20f1c7b5a7a44c8b765b
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774827"
---
# <a name="microsoft-365-cloud-only-identity"></a><span data-ttu-id="75d29-103">Microsoft 365 仅限云身份标识</span><span class="sxs-lookup"><span data-stu-id="75d29-103">Microsoft 365 cloud-only identity</span></span>

<span data-ttu-id="75d29-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="75d29-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="75d29-105">对于仅限云的标识，所有用户、组和联系人都存储在 Microsoft 365 订阅的 Azure Active Directory （Azure AD）租户中。</span><span class="sxs-lookup"><span data-stu-id="75d29-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="75d29-106">下面是仅限云身份的基本组件。</span><span class="sxs-lookup"><span data-stu-id="75d29-106">Here are the basic components of cloud-only identity.</span></span>
 
![仅限云标识的基本组件](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="75d29-108">可以通过多种方式对组织中的用户及其用户帐户进行分类。</span><span class="sxs-lookup"><span data-stu-id="75d29-108">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="75d29-109">例如，一些是员工，且具有永久状态。</span><span class="sxs-lookup"><span data-stu-id="75d29-109">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="75d29-110">有些是具有临时状态的供应商、承包商或合作伙伴。</span><span class="sxs-lookup"><span data-stu-id="75d29-110">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="75d29-111">有些外部用户没有用户帐户，但仍必须被授予对特定服务和资源的访问权限，以支持交互和协作。</span><span class="sxs-lookup"><span data-stu-id="75d29-111">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="75d29-112">例如：</span><span class="sxs-lookup"><span data-stu-id="75d29-112">For example:</span></span>

- <span data-ttu-id="75d29-113">租户帐户表示组织中许可访问云服务的用户。</span><span class="sxs-lookup"><span data-stu-id="75d29-113">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="75d29-114">企业到企业 (B2B) 帐户表示组织外部邀请加入协作的用户。</span><span class="sxs-lookup"><span data-stu-id="75d29-114">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration</span></span>

<span data-ttu-id="75d29-115">对组织中的用户类型进行分组。</span><span class="sxs-lookup"><span data-stu-id="75d29-115">Take stock of the types of users in your organization.</span></span> <span data-ttu-id="75d29-116">分组是什么？</span><span class="sxs-lookup"><span data-stu-id="75d29-116">What are the groupings?</span></span> <span data-ttu-id="75d29-117">例如，您可以将用户按高级功能或目标分组到您的组织。</span><span class="sxs-lookup"><span data-stu-id="75d29-117">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="75d29-118">Additionally, some cloud services can be shared with users outside your organization without any user accounts.</span><span class="sxs-lookup"><span data-stu-id="75d29-118">Additionally, some cloud services can be shared with users outside your organization without any user accounts.</span></span> <span data-ttu-id="75d29-119">You'll need to identify these groups of users as well.</span><span class="sxs-lookup"><span data-stu-id="75d29-119">You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="75d29-120">您可以使用 Azure AD 中的组来实现多种目的，从而简化云环境的管理。</span><span class="sxs-lookup"><span data-stu-id="75d29-120">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="75d29-121">例如，使用 Azure AD 组，您可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="75d29-121">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="75d29-122">使用基于组的许可将 Microsoft 365 的许可证立即分配给您的用户帐户，然后在将其添加为成员时自动。</span><span class="sxs-lookup"><span data-stu-id="75d29-122">Use group-based licensing to assign licenses for Microsoft 365 to your user accounts automatically as soon as they are added as members.</span></span>
- <span data-ttu-id="75d29-123">根据用户帐户属性（如部门名称）动态地向特定组添加用户帐户。</span><span class="sxs-lookup"><span data-stu-id="75d29-123">Add user accounts to specific groups dynamically based on user account attributes, such as department name.</span></span>
- <span data-ttu-id="75d29-124">自动为用户预配软件服务（SaaS）应用程序，并使用多重身份验证（MFA）和其他条件访问规则来保护对这些应用程序的访问。</span><span class="sxs-lookup"><span data-stu-id="75d29-124">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication (MFA) and other Conditional Access rules.</span></span>
- <span data-ttu-id="75d29-125">为 SharePoint Online 团队网站设置权限和访问权限级别。</span><span class="sxs-lookup"><span data-stu-id="75d29-125">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="75d29-126">创建新***用户***时使用的是：</span><span class="sxs-lookup"><span data-stu-id="75d29-126">You create new ***users*** with:</span></span>

- [<span data-ttu-id="75d29-127">Microsoft 365 管理员中心</span><span class="sxs-lookup"><span data-stu-id="75d29-127">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="75d29-128">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="75d29-128">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="75d29-129">您可以使用以下内容创建新***组***：</span><span class="sxs-lookup"><span data-stu-id="75d29-129">You create new ***groups*** with:</span></span>

- [<span data-ttu-id="75d29-130">Microsoft 365 管理员中心</span><span class="sxs-lookup"><span data-stu-id="75d29-130">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="75d29-131">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="75d29-131">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identity"></a><span data-ttu-id="75d29-132">仅限云标识的下一步</span><span class="sxs-lookup"><span data-stu-id="75d29-132">Next step for cloud-only identity</span></span>

[<span data-ttu-id="75d29-133">向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="75d29-133">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
