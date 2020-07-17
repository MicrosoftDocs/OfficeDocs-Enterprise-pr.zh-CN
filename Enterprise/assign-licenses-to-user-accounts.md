---
title: 将 Microsoft 365 许可证分配给用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
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
description: 介绍如何将 Microsoft 365 许可证单独或基于组成员身份分配给用户帐户。
ms.openlocfilehash: f28b9a6367cec2f67b664db2d43ba55b9cf19638
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735930"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a><span data-ttu-id="1f1b8-103">将 Microsoft 365 许可证分配给用户帐户</span><span class="sxs-lookup"><span data-stu-id="1f1b8-103">Assign Microsoft 365 licenses to user accounts</span></span>

<span data-ttu-id="1f1b8-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="1f1b8-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="1f1b8-105">对于仅限云的标识模型，可以根据创建的方式将 Microsoft 365 许可证分配给用户帐户，具体取决于您的创建方式。</span><span class="sxs-lookup"><span data-stu-id="1f1b8-105">For the cloud-only identity model, you can assign Microsoft 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="1f1b8-106">对于混合标识模型，当首次同步 Active Directory 域服务（AD DS）用户帐户时，不会自动为其分配 Microsoft 365 许可证。</span><span class="sxs-lookup"><span data-stu-id="1f1b8-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned a Microsoft 365 license.</span></span> <span data-ttu-id="1f1b8-107">必须先使用用户位置配置每个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="1f1b8-107">You must first configure each user account with a user location.</span></span>

<span data-ttu-id="1f1b8-108">在这两种情况下，都必须将许可证分配给用户帐户，以便您的用户可以访问 Microsoft 365 服务，例如电子邮件和 Microsoft 团队。</span><span class="sxs-lookup"><span data-stu-id="1f1b8-108">In either case, you must assign a license to user accounts so your users can access Microsoft 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="1f1b8-109">您可以通过组成员身份单独或自动将许可证分配给用户帐户。</span><span class="sxs-lookup"><span data-stu-id="1f1b8-109">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="1f1b8-110">若要将 Microsoft 365 许可证分配给单个用户帐户，您可以使用：</span><span class="sxs-lookup"><span data-stu-id="1f1b8-110">To assign Microsoft 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="1f1b8-111">Microsoft 365 管理员中心</span><span class="sxs-lookup"><span data-stu-id="1f1b8-111">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)
- [<span data-ttu-id="1f1b8-112">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f1b8-112">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="1f1b8-113">有关自动许可证分配，请参阅[AZURE AD 中的基于组的许可](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="1f1b8-113">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f1b8-114">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1f1b8-114">Next steps</span></span>

<span data-ttu-id="1f1b8-115">使用已分配了许可证的完整用户帐户集，您现在可以：</span><span class="sxs-lookup"><span data-stu-id="1f1b8-115">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="1f1b8-116">实施安全性</span><span class="sxs-lookup"><span data-stu-id="1f1b8-116">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="1f1b8-117">部署客户端软件，例如 Microsoft 365 应用程序</span><span class="sxs-lookup"><span data-stu-id="1f1b8-117">Deploy client software, such as Microsoft 365 Apps</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [<span data-ttu-id="1f1b8-118">在 Microsoft 365 中设置移动设备管理</span><span class="sxs-lookup"><span data-stu-id="1f1b8-118">Set up Mobile Device Management in Microsoft 365</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="1f1b8-119">配置服务和应用程序</span><span class="sxs-lookup"><span data-stu-id="1f1b8-119">Configure services and applications</span></span>](configure-services-and-applications.md)
