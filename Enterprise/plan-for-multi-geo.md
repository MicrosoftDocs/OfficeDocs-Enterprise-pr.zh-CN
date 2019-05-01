---
title: 计划使用 Office 365 多地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解 Office 365 多地理位置、多地理位置的工作原理，以及什么地理位置可用于数据存储。
ms.openlocfilehash: 4f7905c55cbb926978a43d70300a70d451512f6f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491418"
---
# <a name="plan-for-office-365-multi-geo"></a>计划使用 Office 365 多地理位置

本指南面向跨国公司 (MNC) 的管理员，他们根据公司的经营情况，做好将 Office 365 租户扩大到其他地理位置的准备，以满足数据驻留需求。

在多地理位置配置中，Office 365 租户由一个中心位置以及一个或多个附属位置组成。 这是一个跨多个地理位置的租户。 租户信息（包括地理位置）是在 Azure Active Directory (AAD) 中进行管控。

下面是一些关键的多地理位置术语，有助于了解此配置的基本概念：

-   **租户** - 组织在 Office 365 中的表示形式，通常有一个或多个关联域（例如，http://contoso.sharepoint.com)）。 

-   **地理位置** - Office 365 租户中可用于托管数据的地理位置。

-   **附属位置** - Office 365 租户中已配置用于托管数据的其他地理位置。 多地理位置租户跨多个地理位置（例如，北美和欧洲）。

-   **首选数据位置 (PDL)** - 存储各个用户的 Exchange 和 OneDrive 数据的地理位置。 这可以由管理员设置为已为租户配置的任何地理位置。 请注意，如果你更改已有 OneDrive 网站的用户的 PDL，用户的 OneDrive 数据不会自动移到新地理位置。 有关详细信息，请参阅[将 OneDrive 库移到其他地理位置](move-onedrive-between-geo-locations.md)。 如果用户有 Exchange 邮箱，邮箱会自动移到新首选数据位置。

启用多地理位置需要四个关键步骤：

1.  与你的帐户团队协作，_在 Office 365 服务计划中添加多地理位置功能_。

2.  选择需要的附属位置并将其添加到租户。

3.  将用户的首选数据位置设置为所需的附属位置。 为用户预配的新 OneDrive 网站或 Exchange 邮箱会预配到用户的 PDL。

4.  根据需要，将用户的现有 OneDrive 网站从中心位置迁移到首选数据位置。 （Exchange 邮箱在你设置用户的 PDL 时自动迁移。）

若要详细了解如何执行每一步，请参阅[配置 Office 365 多地理位置](multi-geo-tenant-configuration.md)。

> [!IMPORTANT]
> 请注意，Office 365 多地理位置旨在满足数据驻留需求，而不是优化性能。 若要了解 Office 365 性能优化，请参阅 [Office 365 的网络计划和性能调整](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)，或与支持群组联系。

可以将下列任何地理位置配置为，可托管 OneDrive 和 SharePoint 网站以及 Exchange 邮箱的附属位置。 计划使用多地理位置时，列出要添加到 Office 365 租户的位置。 建议从一个或两个附属位置入手，然后根据需要逐渐扩大到更多地理位置。

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

配置多地理位置时，请考虑借此机会在迁移到 Office 365 时合并本地基础结构。例如，如果你在新加坡和马来西亚有本地服务器场，则可以将它们合并到 APC 附属位置，前提是数据驻留要求允许你执行此操作。

## <a name="best-practices"></a>最佳做法

建议在 Office 365 中创建测试用户，以进行一些初始测试。 让生产用户上手使用 Office 365 多地理位置前，你将使用此用户执行一些测试和验证步骤。

使用测试用户完成测试后，选择一个试点组（可能来自 IT 部门），作为首个在新地理位置使用 OneDrive 和 Exchange 的组。 对于此第一个组，选择尚未拥有 OneDrive 的用户。 建议此初始组的用户数不超过五人，然后遵循批量推出方法逐渐扩大。

每个用户都应设置“首选数据位置”**(PDL)，以便 Office 365 可以确定在哪个地理位置预配 OneDrive。用户的首选数据位置必须与所选卫星位置或中心位置相匹配。虽然 PDL 字段不是强制性的，但我们建议为所有用户设置一个 PDL。没有 PDL 的用户的工作负载将在中央位置进行预配。

创建一个用户列表，并包含他们的用户主体名称 (UPN) 和相应首选数据位置的位置代码。首先包含你的测试用户和初始试点组。在配置过程中你将需要使用这个列表。

如果用户是从本地 Active Directory 系统同步到 Azure Active Directory，你必须将首选数据位置设置为 Active Directory 属性，并使用 Azure Active Directory Connect 同步它。 无法使用 Azure AD PowerShell 直接为同步用户配置首选数据位置。 [Azure Active Directory Connect 同步：配置 Office 365 资源的首选数据位置](https://docs.microsoft.com/zh-CN/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)中介绍了在 Active Directory 中设置并同步 PDL 的步骤。

多地理位置租户的管理可能与非多地理位置租户不同，因为许多 SharePoint 和 OneDrive 设置和服务都具有多地理位置意识。我们建议你在继续配置之前先查看[管理多地理位置环境](administering-a-multi-geo-environment.md)。

请阅读[多地理位置环境中的用户体验](multi-geo-user-experience.md)，详细了解最终用户在多地理位置环境中的体验。

若要开始配置 Office 365 多地理位置，请参阅[配置 Office 365 多地理位置](multi-geo-tenant-configuration.md)。

完成配置后，记得根据需要[迁移用户的 OneDrive 库](move-onedrive-between-geo-locations.md)，以便让用户从首选数据位置工作。
