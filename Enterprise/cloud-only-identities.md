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
# <a name="microsoft-365-cloud-only-identity"></a>Microsoft 365 仅限云身份标识

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

对于仅限云的标识，所有用户、组和联系人都存储在 Microsoft 365 订阅的 Azure Active Directory （Azure AD）租户中。 下面是仅限云身份的基本组件。
 
![仅限云标识的基本组件](./media/about-office-365-identity/cloud-only-identity.png)

可以通过多种方式对组织中的用户及其用户帐户进行分类。 例如，一些是员工，且具有永久状态。 有些是具有临时状态的供应商、承包商或合作伙伴。 有些外部用户没有用户帐户，但仍必须被授予对特定服务和资源的访问权限，以支持交互和协作。 例如：

- 租户帐户表示组织中许可访问云服务的用户。

- 企业到企业 (B2B) 帐户表示组织外部邀请加入协作的用户。

对组织中的用户类型进行分组。 分组是什么？ 例如，您可以将用户按高级功能或目标分组到您的组织。

此外，可以将某些云服务与组织外部没有任何用户帐户的用户共享，而且你还需要标识这些用户组。

您可以使用 Azure AD 中的组来实现多种目的，从而简化云环境的管理。 例如，使用 Azure AD 组，您可以执行以下操作：

- 使用基于组的许可将 Microsoft 365 的许可证立即分配给您的用户帐户，然后在将其添加为成员时自动。
- 根据用户帐户属性（如部门名称）动态地向特定组添加用户帐户。
- 自动为用户预配软件服务（SaaS）应用程序，并使用多重身份验证（MFA）和其他条件访问规则来保护对这些应用程序的访问。
- 为 SharePoint Online 团队网站设置权限和访问权限级别。

创建新***用户***时使用的是：

- [Microsoft 365 管理员中心](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

您可以使用以下内容创建新***组***：

- [Microsoft 365 管理员中心](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identity"></a>仅限云标识的下一步

[向用户帐户分配许可证](assign-licenses-to-user-accounts.md)
