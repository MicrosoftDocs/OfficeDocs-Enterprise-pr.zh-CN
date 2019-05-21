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
# <a name="assign-office-365-licenses-to-user-accounts"></a>将 Office 365 许可证分配给用户帐户

对于仅限云的标识模型, 可以在创建用户帐户时将 Office 365 许可证分配给这些帐户, 具体取决于您创建它们的方式。

对于混合标识模型, 当首次同步 Active Directory 域服务 (AD DS) 用户帐户时, 不会自动为其分配 Office 365 许可证。

在这两种情况下, 都必须将许可证分配给用户帐户, 以便您的用户可以访问 Office 365 服务, 例如电子邮件和 Microsoft 团队。

您可以通过组成员身份单独或自动将许可证分配给用户帐户。

若要将 Office 365 许可证分配给单个用户帐户, 您可以使用:

- [Microsoft 365 管理中心](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

有关自动许可证分配, 请参阅[AZURE AD 中的基于组的许可](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)。

## <a name="next-steps"></a>后续步骤

使用已分配了许可证的完整用户帐户集, 您现在可以:

- [部署客户端软件, 如 Office 365 专业增强版](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [配置移动设备管理](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [配置服务和应用程序](configure-services-and-applications.md)