---
title: 使组织为部署 Office 365 企业版做好准备
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: 如果你已选择退出 FastTrack 部署, 并且在基本部署步骤中找不到所需的内容, 则可以从这里开始。
ms.openlocfilehash: 90cf7cda7070c626579389f8122cdc438d88abe0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067538"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>使组织为部署 Office 365 企业版做好准备

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>为 Office 365 做好准备需要做什么？

大多数组织不需要执行任何操作来准备 Office 365。 它是 web 上的应用程序, 用户可以在拥有帐户时立即使用它。 其他组织具有更多的位置、安全实践或其他要求, 以创建更多规划的需求。 对于企业级组织, 请遵循下面的检查表项目以开始使用 Office 365。
  
如果设置 Office 365 时需要帮助，[FastTrack](https://fasttrack.microsoft.com/office) 是部署 Office 365 的最简单方法，还可以登录并使用 [Office 365 服务的部署顾问](deployment-advisors-for-office-365.md)。
  
|**选择一个或多个开始操作:**||
|:-----|:-----|
| [Office 的系统要求](https://products.office.com/office-system-requirements) |-Microsoft Office Professional、Office 365、Office 365 专业增强版, 以及每个适用于 Windows、Mac、iOS 和 Android 的 Office 应用程序都有特定的系统要求。 确保硬件和软件满足最低系统要求。|
|**大多数**客户将其本地目录连接到 Office 365。 通过[在网络上安装和运行 IdFix,](https://www.microsoft.com/download/details.aspx?id=36832)获取目录准备开始。 <br> 使用[AAD Connect advisor](https://aka.ms/aadconnectpwsync)和[Azure AD Premium set up 指南](https://aka.ms/aadpguidance)获取自定义设置指南。 <br> |-对目录进行自动检查以[验证用户的帐户是否正确同步](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e)。 <br> -建议对目录对象和提供的更改, 以自动执行更改。 <br> - 有关[使用 IdFix 工具的更多详细信息](prepare-directory-attributes-for-synch-with-idfix.md)。 |
|**阅读**我们的[网络性能指南](https://aka.ms/tune)并使用我们的工具, 以确保您具有必要的连接和性能配置, 以便为用户提供最佳体验。  <br> | -确保你可以连接到 Office 365, 如果你筛选或扫描出站流量, 你将需要了解[管理 Office 365 终结点](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a)对你的组织的意义。  <br>  - 为 Office 365 电路[建模和测试网络容量](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132)或移动到[Azure ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) , 以获得可预测性更好的体验。   |
|**将**我们的[规划清单](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0)用作构建您自己的部署计划的起点。  <br> | 深入了解可能的领域, 您需要规划指向参考或操作方法信息的链接以帮助您进行规划。 |
|**使用** [Exchange Server 大型项目脚本](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6)查找可能太大而无法迁移的邮件项目。  <br> | -使用 Exchange Web 服务模拟、访问、扫描邮箱以查找您指定的文件大小, 并将结果转储到 CSV 文件中。 阅读[有关如何使用该脚本的详细说明](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx)。 |
|**** 充分利用[Microsoft 部署专家](https://go.microsoft.com/fwlink/?LinkId=517115), 这些专家可帮助你规划帮助每个人开始使用新的服务和应用程序。  <br> 使用[Office 365 服务的部署向导](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2)来获取自定义设置指南。  <br> | -"加入中心" 直接与客户和合作伙伴组织配合使用。 立即为他们打电话。 |
|**使用** [Office 365 "成功中心" 中的模板和资源](https://www.microsoft.com/fasttrack/resources)与组织中的人员共享您的部署和加入计划。  <br> | -在过渡到 Office 365 的前后与所有人通信非常关键。  <br> -使用我们的模板、指南和讲义来改进你的通信。 |
|**阅读**文章 " [Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)", 了解用于安全管理 Office 365 流量和获得最佳性能的连接原则。  <br> | -本文将帮助您了解有关安全优化 Office 365 网络连接的最新指南。 |
   
需要更多资源来帮助您将 Office 365 集成到更广泛的云策略中吗？ 下面是[Microsoft 云 IT 体系结构资源](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources)。
  
## <a name="want-to-talk-with-support"></a>想要与支持人员交谈吗？

我们在这里为你提供帮助,[请与](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)业务产品支持部门联系。
