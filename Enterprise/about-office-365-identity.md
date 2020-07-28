---
title: Microsoft 365 标识模型和 Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 06/09/2020
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: 了解如何在 Microsoft 365 中管理用户标识。
ms.openlocfilehash: 418d5841a55e6a0da2ccb098c6b41e5a247c9552
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433613"
---
# <a name="microsoft-365-identity-models-and-azure-active-directory"></a>Microsoft 365 标识模型和 Azure Active Directory

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

Microsoft 365 使用 Azure Active Directory （Azure AD），这是 Microsoft 365 订阅附带的基于云的用户标识和身份验证服务，用于管理 Microsoft 365 的身份和身份验证。 正确配置您的身份基础结构对于管理您的组织的 Microsoft 365 用户访问和权限至关重要。

开始之前，请观看此视频，以获取 Microsoft 365 身份模型和身份验证的概述。

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

您的第一次规划选择是 Microsoft 365 身份模型。

## <a name="microsoft-365-identity-models"></a>Microsoft 365 标识模型

若要规划用户帐户，首先需要了解 Microsoft 365 中的两个标识模型。 您可以仅在云中维护组织的标识，也可以维护内部部署 Active Directory 域服务（AD DS）标识，并在用户访问 Microsoft 365 云服务时使用它们进行身份验证。  

下面是两种类型的标识及其最佳优势。

| | 仅限云标识 | 混合标识 |
|:-------|:-----|:-----|
| **定义** | 用户帐户仅存在于适用于 Microsoft 365 订阅的 Azure AD 租户中。 | 用户帐户存在于 AD DS 中，并且副本也位于 Microsoft 365 订阅的 Azure AD 租户中。 Azure AD 中的用户帐户可能还包含已散列的 AD DS 用户帐户密码的哈希版本。 |
| **Microsoft 365 如何对用户凭据进行身份验证** | Microsoft 365 订阅的 Azure AD 租户将使用云标识帐户执行身份验证。 | Microsoft 365 订阅的 Azure AD 租户可以处理身份验证过程，也可以将用户重定向到另一个标识提供程序。 |
| **最适用于** | 不具有或不需要本地 AD DS 的组织。 | 使用 AD DS 或其他标识提供程序的组织。 |
| **最大好处** | 易于使用。 无需额外的目录工具或服务器。 | 在访问本地或基于云的资源时，用户可以使用相同的凭据。 |
||||

## <a name="cloud-only-identity"></a>仅限云标识

仅限云的标识使用仅存在于 Azure AD 中的用户帐户。 云标识通常由没有本地服务器或不使用 AD DS 来管理本地标识的小型组织使用。 

下面是仅限云身份的基本组件。
 
![仅限云标识的基本组件](./media/about-office-365-identity/cloud-only-identity.png)

内部部署和远程（联机）用户使用其 Azure AD 用户帐户和密码来访问 Microsoft 365 云服务。 Azure AD 根据其存储用户帐户和密码对用户凭据进行身份验证。

### <a name="administration"></a>管理
由于用户帐户仅存储在 Azure AD 中，因此可使用[Microsoft 365 管理中心](https://admin.microsoft.com)和[Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-user-accounts-and-licenses-with-office-365-powershell)等工具管理云标识。 

## <a name="hybrid-identity"></a>混合标识

混合标识使用源自内部部署 AD DS 的帐户，并在 Microsoft 365 订阅的 Azure AD 租户中拥有副本。 但是，大多数更改仅以单向方式流动。 对 AD DS 用户帐户所做的更改将同步到其在 Azure AD 中的副本。 但是，在 Azure AD 中对基于云的帐户所做的更改（例如，新用户帐户）不会与 AD DS 同步。

Azure AD Connect 提供了持续的帐户同步。 它在本地服务器上运行，检查 AD DS 中的更改，并将这些更改转发到 Azure AD。 Azure AD Connect 提供了筛选要同步的帐户以及是否同步用户密码的哈希版本（称为密码哈希同步（PHS））的功能。

在实现混合标识时，内部部署 AD DS 是帐户信息的权威源。 这意味着您在内部部署中经常执行管理任务，这些任务随后将同步到 Azure AD。 

下面是混合标识的组件。

![混合标识的组件](./media/about-office-365-identity/hybrid-identity.png)

Azure AD 租户具有 AD DS 帐户的副本。 在此配置中，本地用户和远程用户都在访问 Microsoft 365 云服务，并针对 Azure AD 进行身份验证。

>[!Note]
>始终需要使用 Azure AD Connect 为混合标识同步用户帐户。 您需要在 Azure AD 中同步用户帐户，才能执行许可证分配和组管理、配置权限以及其他涉及用户帐户的管理任务。
>

### <a name="administration"></a>管理

由于原始和权威用户帐户存储在内部部署 AD DS 中，因此，可以使用与 AD DS 相同的工具（如 Active Directory 用户和计算机工具）管理您的标识。 

您不使用 microsoft 365 管理中心或 PowerShell for Microsoft 365 管理 Azure AD 中的同步用户帐户。

## <a name="next-step"></a>后续步骤

如果您需要仅限云的标识模型，请参阅[仅限云标识](cloud-only-identities.md)。

如果需要混合标识模型，请参阅[混合标识](plan-for-directory-synchronization.md)。


## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版概述](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
