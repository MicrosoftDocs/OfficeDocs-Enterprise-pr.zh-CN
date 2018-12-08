---
title: 规划 OneDrive for Business 多地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解 OneDrive for Business 多地理位置、多地理位置的工作方式，以及哪些地理位置可用于数据存储。
ms.openlocfilehash: de856bdeb0c0f1ca8e718439ddb98d738843bc5a
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200715"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>规划 OneDrive for Business 多地理位置

本指南主要面向跨国合公司 (MNC) 的管理员，帮助他们根据公司的经营情况准备将 SharePoint Online 租户扩展到其他地区，以满足数据驻留需求。

在 OneDrive 多地理位置配置中，Office 365 租户由中心位置以及一个或多个附属地理位置组成。这是一个横跨多个地理位置的单个租户。在 OneDrive 多地理位置中，你的租户信息（包括地理位置）在 Azure Active Directory (AAD) 中进行管控。 

下面是一些关键的多地理位置术语，可以帮助你了解配置的基本概念：

-   **租户** - Office 365 云中组织的表示形式，其通常具有一个或多个与之关联的域，例如，http://contoso.sharepoint.com)。 

-   **地理位置** – 可用于托管 Office 365 租户中数据的地理位置。

-   **附属位置** – 已配置的用于托管 Office 365 租户中数据的地理位置。多地理位置租户跨多个地理位置，例如，北美和欧洲。

-   **首选数据位置 (PDL)** – 其中存储单个用户 OneDrive 数据的地理位置。这可由管理员设置为任何一个已为租户配置的允许数据位置。注意，如果更改了已具有 OneDrive 站点的用户的 PDL，则其 OneDrive 数据不会自动移动到新的地理位置。请参阅[将 OneDrive 库移动到其他地理位置](move-onedrive-between-geo-locations.md)，了解更多信息。

启用多地理位置需要四个关键步骤：

1.  与你的帐户团队协作，_在 Office 365 服务计划中添加多地理位置功能_。

2.  选择需要的附属位置并将其添加到租户。

3.  将用户的首选数据位置设置为所需的附属位置。在为用户预配新的 OneDrive 站点时，会将该位置预配到其 PDL。

4.  根据需要，将用户的现有 OneDrive 站点从中心位置迁移到首选的数据位置。

请参阅[配置 OneDrive for Business 多地理位置](multi-geo-tenant-configuration.md)，了解有关每个步骤的详细信息。

> [!IMPORTANT]
> 注意，Office 365 多地理位置不是专为性能优化情况而设计的，它主要是为了满足数据驻留需求。有关 Office 365 性能优化的信息，请参阅[针对 Office 365 的网络规划和性能优化](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)，或联系支持小组。

你可以将任何以下地理位置配置为可托管 OneDrive 文件的附属位置。规划多地理位置时，创建一个想要向 Office 365 租户添加的位置列表。我们建议从一个或两个附属位置开始，然后根据需要逐渐扩展到更多的地理位置。

<table>
<thead>
<tr class="header">
<th align="left"><strong>位置</strong></th>
<th align="left"><strong>代码</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">亚太地区</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">澳大利亚</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">加拿大</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">欧洲/中东/非洲</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">法国</td>
<td align="left">FRA</td>
</tr>
<tr class="odd">
<td align="left">印度</td>
<td align="left">IND</td>
</tr>
<tr class="odd">
<td align="left">日本</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">韩国</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">北美</td>
<td align="left">NAM</td>
</tr>
<tr class="odd">
<td align="left">英国</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

配置多地理位置时，请考虑借此机会在迁移到 Office 365 时合并本地基础结构。例如，如果你在新加坡和马来西亚有本地服务器场，则可以将它们合并到 APC 附属位置，前提是数据驻留要求允许你执行此操作。

## <a name="best-practices"></a>最佳做法

我们建议在 Office 365 中创建一个测试用户，进行一些初始测试。在将生产用户载入 OneDrive 多地理位置时，我们将使用此用户进行一些测试和验证步骤。

在使用测试用户完成测试后，选择一个试点组（可能来自 IT 部门）作为首个在新地理位置使用 OneDrive 的用户。对于此首个小组，请选择尚未拥有 OneDrive 的用户。我们建议这个初始小组的人数不超过 5 个，然后逐渐扩大，最终再批量推广。

每个用户都应设置“首选数据位置”**(PDL)，以便 Office 365 可以确定在哪个地理位置预配 OneDrive。用户的首选数据位置必须与所选卫星位置或中心位置相匹配。虽然 PDL 字段不是强制性的，但我们建议为所有用户设置一个 PDL。没有 PDL 的用户的工作负载将在中央位置进行预配。   

创建一个用户列表，并包含他们的用户主体名称 (UPN) 和相应首选数据位置的位置代码。首先包含你的测试用户和初始试点组。在配置过程中你将需要使用这个列表。

如果你的用户从本地 Active Directory 系统同步到 Azure Active Directory，则必须使用 Azure Active Directory Connect 为同步的用户设置首选数据位置。你不能使用 Azure AD PowerShell 直接为同步用户配置首选数据位置。在 AD 中设置 PDL 并对其进行同步的步骤，请参阅 [Azure Active Directory Connect 同步：为 Office 365 资源配置首选数据位置](https://docs.microsoft.com/zh-CN/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。

多地理位置租户的管理可能与非多地理位置租户不同，因为许多 SharePoint 和 OneDrive 设置和服务都具有多地理位置意识。我们建议你在继续配置之前先查看[管理多地理位置环境](administering-a-multi-geo-environment.md)。

请阅读[多地理位置环境中的用户体验](multi-geo-user-experience.md)，详细了解关于最终用户在多地理位置环境中的体验。

要开始配置 OneDrive for Business 多地理位置，请参阅[配置 OneDrive for Business 多地理位置](multi-geo-tenant-configuration.md)。

完成配置后，记得根据需要[迁移用户的 OneDrive 库](move-onedrive-between-geo-locations.md)，以便让用户从首选数据位置工作。
