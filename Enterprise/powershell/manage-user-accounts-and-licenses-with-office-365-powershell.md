---
title: 使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: 摘要：了解如何使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组。
ms.openlocfilehash: 26da0d13ecc9c14be4abe059943bd91d88126f1e
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230408"
---
# <a name="manage-microsoft-365-user-accounts-licenses-and-groups-with-powershell"></a><span data-ttu-id="5511c-103">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="5511c-103">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>

<span data-ttu-id="5511c-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="5511c-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="5511c-105">任何 Microsoft 365 管理员的主要任务之一就是管理用户帐户、许可证和组。</span><span class="sxs-lookup"><span data-stu-id="5511c-105">One of the primary tasks of any Microsoft 365 administrator is managing user accounts, licenses, and groups.</span></span> <span data-ttu-id="5511c-106">虽然您可以在 Microsoft 365 管理中心中完成这些任务的大部分方面，但其他任务的 PowerShell 更快、更轻松。</span><span class="sxs-lookup"><span data-stu-id="5511c-106">Although you can accomplish most aspects of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with PowerShell.</span></span> 

<span data-ttu-id="5511c-107">有关详细信息，请参阅这些主题。</span><span class="sxs-lookup"><span data-stu-id="5511c-107">For more information, see these topics.</span></span>

## <a name="user-accounts"></a><span data-ttu-id="5511c-108">用户帐户</span><span class="sxs-lookup"><span data-stu-id="5511c-108">User accounts</span></span>

- [<span data-ttu-id="5511c-109">创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="5511c-109">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="5511c-110">查看用户帐户</span><span class="sxs-lookup"><span data-stu-id="5511c-110">View user accounts</span></span>](view-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="5511c-111">配置用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="5511c-111">Configure user account properties</span></span>](configure-user-account-properties-with-office-365-powershell.md)
- [<span data-ttu-id="5511c-112">向用户帐户分配角色</span><span class="sxs-lookup"><span data-stu-id="5511c-112">Assign roles to user accounts</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="5511c-113">删除和还原用户帐户</span><span class="sxs-lookup"><span data-stu-id="5511c-113">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="5511c-114">阻止用户帐户</span><span class="sxs-lookup"><span data-stu-id="5511c-114">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)

## <a name="licenses-and-services"></a><span data-ttu-id="5511c-115">许可证和服务</span><span class="sxs-lookup"><span data-stu-id="5511c-115">Licenses and services</span></span>
- [<span data-ttu-id="5511c-116">查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="5511c-116">View licenses and services</span></span>](view-licenses-and-services-with-office-365-powershell.md)
- [<span data-ttu-id="5511c-117">查看已授权和未授权用户</span><span class="sxs-lookup"><span data-stu-id="5511c-117">View licensed and unlicensed users</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="5511c-118">向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="5511c-118">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="5511c-119">查看帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="5511c-119">View account license and service details</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="5511c-120">禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="5511c-120">Disable access to services</span></span>](disable-access-to-services-with-office-365-powershell.md)
  - [<span data-ttu-id="5511c-121">禁止访问 Sway</span><span class="sxs-lookup"><span data-stu-id="5511c-121">Disable access to Sway</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  - [<span data-ttu-id="5511c-122">在分配用户许可证时禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="5511c-122">Disable access to services while assigning user licenses</span></span>](disable-access-to-services-while-assigning-user-licenses.md)
- [<span data-ttu-id="5511c-123">删除用户帐户的许可证</span><span class="sxs-lookup"><span data-stu-id="5511c-123">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)

## <a name="groups"></a><span data-ttu-id="5511c-124">组</span><span class="sxs-lookup"><span data-stu-id="5511c-124">Groups</span></span>
- [<span data-ttu-id="5511c-125">维护组成员身份</span><span class="sxs-lookup"><span data-stu-id="5511c-125">Maintain group membership</span></span>](maintain-group-membership-with-office-365-powershell.md)
- [<span data-ttu-id="5511c-126">管理 Microsoft 365 组</span><span class="sxs-lookup"><span data-stu-id="5511c-126">Manage Microsoft 365 groups</span></span>](manage-office-365-groups-with-powershell.md)

