---
title: 使组织为部署 Office 365 企业版做好准备
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: 如果您已选择加入超出 FastTrack 部署并不会查找我们基本部署步骤中所需，这是从这里开始。
ms.openlocfilehash: bb522890880ec77969abe6e2559c3d0293aca372
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651196"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>使组织为部署 Office 365 企业版做好准备

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>您需要执行的操作做好 Office 365？

大多数组织不需要执行任何操作即可为 Office 365 准备。它是在 web 应用程序和人员能够使用它，只要他们拥有帐户。其他组织具有多个位置、 安全实践或创建需要更多的规划的其他要求。企业级组织，请按照下列有关 Office 365 入门清单项目。
  
如果设置 Office 365 时需要帮助，[FastTrack](https://fasttrack.microsoft.com/office) 是部署 Office 365 的最简单方法，还可以登录并使用 [Office 365 服务的部署顾问](deployment-advisors-for-office-365.md)。
  
|**选择一个或多开始：**||
|:-----|:-----|
| [Office 的系统要求](https://products.office.com/office-system-requirements) |-Microsoft Office Professional、 Office 365、 Office 365 ProPlus 和 Windows、 Mac、 iOS 和 Android 所有的每个 Office 应用程序具有特定的系统要求。确保您的硬件和软件满足的最低系统要求。|
|**大多数**客户连接到 Office 365 其内部部署目录。通过[安装并运行 IdFix 在您的网络](https://www.microsoft.com/download/details.aspx?id=36832)上的目录准备快速开始。<br> 使用[AAD 连接顾问](https://aka.ms/aadconnectpwsync)和[Azure AD Premium 设置指南](https://aka.ms/aadpguidance)获取自定义的设置的指南。 <br> |自动检查到 directory[验证人的帐户将正确同步](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e)。 <br> -更改建议对目录对象和即可自动为您所做的更改。 <br> - [使用 IdFix 工具的详细信息](prepare-directory-attributes-for-synch-with-idfix.md)。 |
|**阅读**我们的[网络性能指南](https://aka.ms/tune)和使用我们的工具，以确保您具有连接性和性能的配置所需人员提供最佳体验。  <br> | -确保您可以连接到 Office 365 中，如果您筛选或扫描出站通信，您需要了解哪些[管理 Office 365 终结点](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a)是指为您的组织。  <br>  - [模型并测试网络容量](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132)或移动到[Office 365 的 Azure ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)电路的更多可预测的体验。   |
|**使用**我们的[规划清单](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0)用作构建您自己的部署计划的起始位置。  <br> | -深入概述可能区域您需要规划并提供可帮助您规划的引用或操作方法信息的链接。 |
|**使用** [Exchange Server 大项目脚本](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6)以查找可能太大，迁移的邮件项目。  <br> | -使用 Exchange Web 服务模拟、 访问、 扫描指定，文件大小和转储 CSV 文件中的结果的邮箱。阅读[有关如何使用脚本的详细的说明](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx)。 |
|**充分**利用[Microsoft 部署专家](https://go.microsoft.com/fwlink/?LinkId=517115)可帮助您规划从帮助每个人开始使用新的服务和应用程序。  <br> 使用[部署向导 for Office 365 服务](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2)获取自定义的设置的指南。  <br> | 直接与客户和合作伙伴组织的工作方式-入职培训中心。为其提供呼叫今天。 |
|[模板和 Office 365 成功中心中的资源](https://www.microsoft.com/fasttrack/resources)共享您的部署和入职培训计划，请**使用**与您的组织中的人员。  <br> | -与所有人之前、 升级期间和转换到 Office 365 之后通信至关重要。  <br> -使用我们的模板、 指南和讲义来提高您的通信。 |
|**阅读**此文章[Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)了解用于安全地管理 Office 365 流量和获取最佳性能的连接原则。  <br> | -这篇文章将帮助您了解有关安全地优化 Office 365 网络连接的最新指南。 |
   
需要更多的资源可帮助您与您更广泛的云策略集成 Office 365？以下是[Microsoft 云 IT 体系结构的资源](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources)。
  
## <a name="want-to-talk-with-support"></a>要支持与讨论？

我们为了帮助，业务产品[与支持部门联系](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)。
