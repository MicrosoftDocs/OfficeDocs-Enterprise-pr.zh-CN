---
title: 将 Office 365 许可证分配给用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 介绍如何将 Office 365 许可证单独或基于组成员身份分配给用户帐户。
ms.openlocfilehash: 0f258ef9240239ebdfa695e8c5b214484cfb4db1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164597"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="d2d17-103">将 Office 365 许可证分配给用户帐户</span><span class="sxs-lookup"><span data-stu-id="d2d17-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="d2d17-104">对于仅限云的标识模型, 可以在创建用户帐户时将 Office 365 许可证分配给这些帐户, 具体取决于您创建它们的方式。</span><span class="sxs-lookup"><span data-stu-id="d2d17-104">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="d2d17-105">对于混合标识模型, 当首次同步 Active Directory 域服务 (AD DS) 用户帐户时, 不会自动为其分配 Office 365 许可证。</span><span class="sxs-lookup"><span data-stu-id="d2d17-105">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="d2d17-106">在这两种情况下, 都必须将许可证分配给用户帐户, 以便您的用户可以访问 Office 365 服务, 例如电子邮件和 Microsoft 团队。</span><span class="sxs-lookup"><span data-stu-id="d2d17-106">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="d2d17-107">您可以通过组成员身份单独或自动将许可证分配给用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d2d17-107">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="d2d17-108">若要将 Office 365 许可证分配给单个用户帐户, 您可以使用:</span><span class="sxs-lookup"><span data-stu-id="d2d17-108">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="d2d17-109">Microsoft 365 管理中心</span><span class="sxs-lookup"><span data-stu-id="d2d17-109">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="d2d17-110">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2d17-110">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="d2d17-111">有关自动许可证分配, 请参阅[AZURE AD 中的基于组的许可](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="d2d17-111">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d2d17-112">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d2d17-112">Next steps</span></span>

<span data-ttu-id="d2d17-113">使用已分配了许可证的完整用户帐户集, 您现在可以:</span><span class="sxs-lookup"><span data-stu-id="d2d17-113">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="d2d17-114">部署客户端软件, 如 Office 365 专业增强版</span><span class="sxs-lookup"><span data-stu-id="d2d17-114">Deploy client software, such as Office 365 ProPlus</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [<span data-ttu-id="d2d17-115">配置移动设备管理</span><span class="sxs-lookup"><span data-stu-id="d2d17-115">Configure mobile device management</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="d2d17-116">配置服务和应用程序</span><span class="sxs-lookup"><span data-stu-id="d2d17-116">Configure services and applications</span></span>](configure-services-and-applications.md)
