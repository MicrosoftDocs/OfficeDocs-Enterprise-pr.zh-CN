---
title: Microsoft 365 多地理位置计划
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: 了解 Microsoft 365 多地理位置、多地理位置的工作原理，以及什么地理位置可用于数据存储。
ms.openlocfilehash: 8f06c43b9a622e06959ab12fa0e055c8653ca61c
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052455"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Microsoft 365 多地理位置计划

本指南面向跨国公司 (MNC) 的管理员，他们根据公司的经营情况，做好将 Microsoft 365 租户扩大到其他地理位置的准备，以满足数据驻留需求。

在多地理位置配置中，Microsoft 365 租户由一个中心位置以及一个或多个附属位置组成。 这是一个跨多个地理位置的租户。 租户信息（包括地理位置）是在 Azure Active Directory (Azure AD) 中进行管控。

下面是一些关键的多地理位置术语，有助于了解此配置的基本概念：

-   **租户** - 组织在 Microsoft 365 中的表示形式，通常有一个或多个关联域（例如，https://contoso.sharepoint.com)）。 

-   **地理位置** - Microsoft 365 租户中可用于托管数据的地理位置。

-   **附属位置** - Microsoft 365 租户中已配置用于托管数据的其他地理位置。 多地理位置租户跨多个地理位置（例如，北美和欧洲）。

-   **首选数据位置 (PDL)** - 存储各个用户的 Exchange 和 OneDrive 数据的地理位置。 这可以由管理员设置为已为租户配置的任何地理位置。 请注意，如果你更改已有 OneDrive 网站的用户的 PDL，用户的 OneDrive 数据不会自动移到新地理位置。 有关详细信息，请参阅[将 OneDrive 库移到其他地理位置](move-onedrive-between-geo-locations.md)。 如果用户有 Exchange 邮箱，邮箱会自动移到新首选数据位置。

启用多地理位置需要四个关键步骤：

1.  与你的帐户团队协作，_在 Microsoft 365 服务计划中添加多地理位置功能_。

2.  选择需要的附属位置并将其添加到租户。

3.  将用户的首选数据位置设置为所需的附属位置。 为用户预配的新 OneDrive 网站或 Exchange 邮箱会预配到用户的 PDL。

4.  根据需要，将用户的现有 OneDrive 网站从中心位置迁移到首选数据位置。 （Exchange 邮箱在你设置用户的 PDL 时自动迁移。）

若要详细了解如何执行每一步，请参阅[配置 Microsoft 365 多地理位置](multi-geo-tenant-configuration.md)。

> [!IMPORTANT]
> 请注意，Microsoft 365 多地理位置旨在满足数据驻留需求，而不是优化性能。 若要了解 Microsoft 365 性能优化，请参阅 [Microsoft 365 的网络计划和性能调整](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)，或与支持群组联系。

可以将下列任何地理位置配置为，可托管 OneDrive 和 SharePoint 网站以及 Exchange 邮箱的附属位置。 计划使用多地理位置时，列出要添加到 Microsoft 365 租户的位置。 建议从一个或两个附属位置入手，然后根据需要逐渐扩大到更多地理位置。

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Microsoft 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.

## <a name="best-practices"></a>最佳做法

建议在 Microsoft 365 中创建测试用户，以进行一些初始测试。 让生产用户上手使用 Microsoft 365 多地理位置前，你将使用此用户执行一些测试和验证步骤。

使用测试用户完成测试后，选择一个试点组（可能来自 IT 部门），作为首个在新地理位置使用 OneDrive 和 Exchange 的组。 对于此第一个组，选择尚未拥有 OneDrive 的用户。 建议此初始组的用户数不超过五人，然后遵循批量推出方法逐渐扩大。

Each user should have a *preferred data location* (PDL) set so that Microsoft 365 can determine in which geo location to provision their OneDrive. The user's preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location.

Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You'll need this list for the configuration procedures.

如果用户是从本地 Active Directory 系统同步到 Azure Active Directory，你必须将首选数据位置设置为 Active Directory 属性，并使用 Azure Active Directory Connect 同步它。 无法使用 Azure AD PowerShell 直接为同步用户配置首选数据位置。 [Azure Active Directory Connect 同步：配置 Microsoft 365 资源的首选数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)中介绍了在 Active Directory 中设置并同步 PDL 的步骤。

The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.

请阅读[多地理位置环境中的用户体验](multi-geo-user-experience.md)，详细了解最终用户在多地理位置环境中的体验。

要详细了解 Microsoft 365 多地理位置租户中的 Teams 体验，请参阅 [Microsoft 365 OneDrive 和 SharePoint Online 支持多地理位置的租户中的 Teams 体验](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo)。

若要开始配置 Microsoft 365 多地理位置，请参阅[配置 Microsoft 365 多地理位置](multi-geo-tenant-configuration.md)。

完成配置后，记得根据需要[迁移用户的 OneDrive 库](move-onedrive-between-geo-locations.md)，以便让用户从首选数据位置工作。
