---
title: OneDrive 计划的业务多地区
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解 OneDrive 的业务多地区、 多地区的工作原理，以及哪些地理位置都可用于数据存储。
ms.openlocfilehash: 22ba0f4ebc3fb3c4e11bc0386a1479fa6a889ad8
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>OneDrive 计划的业务多地区

本指南适用于多国公司 (MNCs) 准备将其扩展到其他地区公司的存在，以满足数据派驻要求按照其 SharePoint Online 租户的管理员。

在 OneDrive 多地区配置中，Office 365 租户组成一个集中的位置 （也称为默认位置） 和一个或多个卫星地理位置。这是跨多个地理位置跨越单个租户。OneDrive 多的地区，在您组织的信息，包括地理位置被掌握在 Azure 活动目录 (AAD)。 

以下是一些关键的多地理术语来帮助您了解配置的基本概念：

-   **租户**— Office 365 云通常具有与其关联的一个或多个域中的组织表示形式 (例如， http://contoso.sharepoint.com)。 

-   **地理位置**--租户的数据所在的地理位置。多地区承租人跨越多个地理位置，例如，北美和欧洲。

-   **允许数据位置 (ADL)** – 为您的租户已配置主机 OneDrive 和 SharePoint 数据的地理位置。

-   **首选数据位置 (PDL)** – 存储单个用户的 OneDrive 数据的地理位置。这可以由管理员允许数据位置的租户已配置的任何设置。请注意，是否您更改为已有的 OneDrive 网站的用户 PDL，其 OneDrive 不自动移动数据到新的地理位置。有关详细信息，请参阅[移动到不同的地理位置的 OneDrive 库](move-onedrive-between-geo-locations.md)。

启用多地区需要四个关键步骤：

1.  使用您的帐户小组要添加_Office 365 中的多个地区功能_服务计划。

2.  选择您所需的卫星地理位置并将其添加到您的租户。

3.  将您的用户首选的数据位置设置为所需的卫星地理位置。当用户配置新的 OneDrive 站点时，它被调配给他们 PDL。

4.  它们的首选的数据位置根据需要向主址位置迁移用户现有的 OneDrive 网站。

有关上述每个步骤的详细信息，请参阅[配置 OneDrive 业务多的地区](multi-geo-tenant-configuration.md)。

> [!IMPORTANT]
> 请注意，Office 365 的多地区功能不适用于性能优化的情况下，它们被设计为满足派驻的数据要求。Office 365 的性能优化的相关信息，请参阅[网络规划和性能调优对于 Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)或联系您的支持小组。

您可以配置任何以下位置是卫星 OneDrive 文件可以驻留的地理位置。在多个地区的规划，请您想要添加到 Office 365 租户的位置的列表。我们建议以一个或两个卫星位置开始，然后逐渐扩大到更多的地理位置，如果需要。

<table>
<thead>
<tr class="header">
<th align="left"><strong>位置</strong></th>
<th align="left"><strong>代码</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">亚太</td>
<td align="left">APC 公司</td>
</tr>
<tr class="even">
<td align="left">欧洲 / 中东 / 非洲</td>
<td align="left">欧元</td>
</tr>
<tr class="odd">
<td align="left">北美洲</td>
<td align="left">名称</td>
</tr>
<tr class="even">
<td align="left">澳大利亚</td>
<td align="left">澳大利亚</td>
</tr>
<tr class="odd">
<td align="left">加拿大</td>
<td align="left">可以</td>
</tr>
<tr class="odd">
<td align="left">日本</td>
<td align="left">日文</td>
</tr>
<tr class="even">
<td align="left">韩国</td>
<td align="left">韩文</td>
</tr>
<tr class="odd">
<td align="left">英国</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

即将到来的地理位置：
  
- 法国
- 印度

配置多个地区时，应考虑合并时迁移到 Office 365 内部部署基础结构的机会。例如，如果可以在新加坡和马来西亚的内部部署服务器场，然后您可以合并它们到 APC 的附属位置，提供数据派驻需求允许您可以做到这一点。

## <a name="best-practices"></a>最佳做法

我们建议您在 Office 365 执行一些初始测试创建一个测试用户。我们将引导您完成一些测试和验证的步骤与该用户在继续操作之前到板载生产用户到此 OneDrive 多地理特征。

一旦完成测试，测试用户，选择一个试验组 – 可能是从您的 IT 部门--是第一次使用 OneDrive 的一个新的地理位置。第一组中，选择用户还没有 OneDrive。我们建议在此第一组不超过五个人，并逐渐展开下一批的推广的做法。

每个用户应有设置的*首选的数据位置*(PDL) 以便 Office 365 可以确定在提供其 OneDrive 的地理位置。用户的首选的数据位置必须匹配选定的卫星位置或您的位置中心之一。PDL 字段不是必需的而我们建议为所有用户设置 PDL。将基于多地理逻辑的中心位置在调配的 PDL 没有权限的用户工作负载。   

创建您的用户的列表，包括其用户主体名称 (UPN) 和适当的首选的数据位置的位置代码。首先，包括测试用户和初始实验组。您需要此列表的配置过程。

如果您的用户从内部活动目录 (AD) 系统同步到 Azure 活动目录 (AAD) 的则必须通过使用 Azure 活动目录连接设置同步用户的首选的数据位置。您不能直接配置使用 Azure AD PowerShell 的同步用户的首选的数据位置。在 AD 中设置 PDL 并对其进行同步的步骤中介绍了[Azure 活动目录连接同步： 配置 Office 365 提供资源的首选的数据位置](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。

管理的多个地区租户可以不同于非地理多租户，尽可能多的 SharePoint 和 OneDrive 设置和服务意识多地区。我们建议您查看[管理多地理环境](administering-a-multi-geo-environment.md)之前继续您的配置。

多地理环境中的最终用户的体验有关的详细信息，请阅读[用户体验在 multgeo 环境中](multi-geo-user-experience.md)。

要开始配置 OneDrive 业务多的地区，请参阅[配置 OneDrive 业务多的地区](multi-geo-tenant-configuration.md)。

完成配置后，请记住[迁移用户的 OneDrive 库](move-onedrive-between-geo-locations.md)到根据需要获取用户从其首选的数据位置工作。
