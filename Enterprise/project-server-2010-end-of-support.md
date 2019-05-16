---
title: Project Server 2010 终止支持路线图
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: 在2020年10月13日, Project Server 2010 的支持结束。 现在可以使用本文规划升级。
ms.openlocfilehash: 1c8e6eab592e2974c334367e7931395e867ad97e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071038"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project Server 2010 结束支持路线图

在2010中, Office 2010 服务器和应用程序的支持结束, 您需要考虑迁移计划。 如果您当前使用的是 Project Server 2010, 请注意, 它和这些其他相关产品将具有以下支持日期的结尾:
  
|**Product**|**支持结束日期**|
|:-----|:-----|
|Project Server 2010  <br/> |2020年10月13日  <br/> |
|Project Portfolio Server 2010  <br/> |2020年10月13日  <br/> |
|Project 2010 Standard  <br/> |2020年10月13日  <br/> |
|Project 2010 专业版  <br/> |2020年10月13日  <br/> |
   
有关 Office 2010 服务器即将退休的详细信息, 请参阅[从 Office 2010 服务器和客户端产品升级](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office)。
  
## <a name="what-does-end-of-support-mean"></a>支持终止的含义是什么？

与几乎所有 Microsoft 产品一样, Project Server 都具有支持生命周期, 在此期间我们提供了新的功能、缺陷修补程序、安全修补程序等。 此生命周期通常是从产品初始发布之日起10年的时间, 而此生命周期的结束时间也称为产品的支持终止的期限。 由于 Project Server 2010 在2020年10月10日已达到其支持的结束时间, Microsoft 将不再提供:
  
- 可能出现的问题的技术支持。
    
- 针对所发现的问题的 Bug 修复, 并且可能会影响服务器的稳定性和可用性。
    
- 针对发现的漏洞的安全修补程序, 并且可能会使服务器容易受到安全破坏。
    
- 时区更新。
    
在此日期之后, Project Server 2010 的安装将继续运行。 但是, 由于上面列出了所做的更改, 强烈建议您尽快从 Project Server 2010 迁移。
  
## <a name="what-are-my-options"></a>我的选项是什么？

如果使用的是 Project Server 2010, 您需要浏览迁移选项, 其中包括:
  
- 迁移到 Project Online
    
- 迁移到 Project Server 的较新的本地版本 (最好是 Project Server 2019)。
    
|**为什么我更喜欢迁移到 Project Online**|**为什么我更喜欢迁移到 Project Server 2019**|
|:-----|:-----|
| 我有移动用户。  <br/>  迁移成本是一个很大的顾虑 (硬件、软件、时间和实施工作, 等等)。  <br/>  迁移后, 维护我的环境所需的成本是一个非常重要的问题 (例如, 自动更新、保证的正常运行时间等)。  <br/> | 业务规则限制我在云中运行我的业务。  <br/>  我需要控制环境的更新。  <br/> |
   
> [!NOTE]
> 有关从 Office 2010 服务器移动的选项的详细信息, 请参阅可[帮助您从 office 2010 服务器和客户端进行升级的资源](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)。 请注意, Project Server 不支持混合配置, 因为 Project Server 和 Project Online 无法共享同一个资源池。 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>在计划从 Project Server 2010 迁移时需要注意的重要事项

在计划从 Project Server 2010 迁移时, 需要考虑以下事项:
  
- 从**Microsoft 合作伙伴获取帮助**-从 Project Server 2010 升级可能是一项挑战, 需要进行大量准备和规划。 如果你不是最初安装和配置 Project Server 2010 的方法, 则可能尤其有挑战性。 幸运的是, 有 Microsoft 合作伙伴您可以转到执行此操作的用户, 无论您是否计划迁移到 Project Server 2019 或 Project Online。 你可以搜索 Microsoft 合作伙伴以帮助你在[Microsoft 合作伙伴中心](https://go.microsoft.com/fwlink/p/?linkid=841249)上进行迁移。 您可以通过搜索 "*黄金" 金牌项目和项目组合管理*, 来获取 Project 中具有专业技能的所有 Microsoft 合作伙伴的列表。 
    
- **规划自定义**-请注意, 当迁移到 project server 2019 或 project Online 时, 在 project server 2010 环境中使用的许多自定义设置可能不起作用。 在不同版本之间的 Project Server 体系结构以及所需的操作系统、数据库服务器和客户端 web 浏览器之间存在很大差异, 支持使用较新版本。 制定了如何根据需要在新环境中测试或重建自定义项的计划。 规划升级也是一种很好的机会来验证是否在您向前移动时确实需要特定的自定义。 [在升级到 SharePoint 2013 过程中创建当前自定义项计划在升级过程中](https://go.microsoft.com/fwlink/p/?linkid=842061), 有关评估和规划当前自定义项的一些极好的常规信息。 
    
- **时间和耐心**升级规划、执行和测试将需要很长时间和精力, 尤其是在升级到 Project Server 2019 时。 例如, 如果要从 Project Server 2010 迁移到 Project Server 2019, 则首先需要从 Project Server 2010 迁移到 Project Server 2013, 然后检查数据, 然后在迁移到每个后续版本时执行相同的操作 (Project服务器 2016, 然后是 Project Server 2019)。 您可能需要与 Microsoft 合作伙伴核实, 以将您的估计成本与估计成本的估计值进行比较, 并估计他们需要多长时间才能完成的成本。 
    
## <a name="migrate-to-project-online"></a>迁移到 Project Online

如果选择从 Project Server 2010 迁移到 Project Online, 则可以执行以下操作来手动迁移项目计划数据:
  
1. 将项目计划从 Project Server 2010 保存到。MPP 格式。
    
2. 使用 Project Professional 2016、Project Professional 2019 或 Project Online 桌面客户端, 打开每个 mpp 文件, 然后将其保存并发布到 Project Online。
    
您可以在 Project Online 中手动创建 PWA 配置 (例如, 重新创建任何所需的自定义字段或企业日历)。 Microsoft 合作伙伴还可以帮助你做到这一点。
  
主要资源:
  
|**Resource**|**说明**|
|:-----|:-----|
|[Project Online 入门](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |如何设置和使用 Project Online。  <br/> |
|[Project Online 服务说明](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |有关可供您使用的不同 Project Online 计划的信息。  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>迁移到 Project Server 的更新的本地版本

虽然我们强烈相信您可以通过迁移到 Project Online 来实现最佳价值和用户体验, 但我们还了解一些组织需要将项目数据保留在本地环境中。 如果选择将您的项目数据保留在本地, 则可以将 Project Server 2010 环境迁移到 Project Server 2013、Project Server 2016 或 Project Server 2019。
  
如果不能迁移到 Project Online, 建议您迁移到 Project Server 2019。 Project Server 2019 包括早期版本的 Project Server 中包含的功能和改进功能, 与 Project Online 可用的体验最为匹配 (尽管某些功能仅在 Project Online 中可用)。
  
完成每个迁移后, 应检查数据以确保其已成功迁移。
  
> [!NOTE]
> 如果您仅考虑迁移到 Project Server 2013 (如果您仅迁移到本地解决方案), 请务必注意, 它只会有几年的支持。 Project Server 2013 Service Pack 2 结束支持日期为10/13/2023。 有关支持日期结束的详细信息, 请参阅[Microsoft 产品生命周期策略](https://go.microsoft.com/fwlink/p/?linkid=842066)。 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>如何迁移到 Project Server 2019？

Project Server 2010 与 Project Server 2019 之间的体系结构差异可防止直接迁移路径。 这意味着, 在升级到 Project Server 2019 之前, 您需要将 Project Server 2010 数据迁移到 Project Server 的下一个连续版本。
  
您将需要执行以下操作以升级到 Project Server 2019:
  
1. 步骤 1: 将数据从 Project Server 2010 迁移到 Project Server 2013。
    
2. 步骤 2: 将数据从 Project 服务2013迁移到 Project Server 2016。
    
3. 步骤 3: 将数据从 Project Server 2016 迁移到 Project Server 2019。
    
完成每个迁移后, 应检查数据以确保其已成功迁移。
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>步骤 1: 迁移到 Project Server 2013

将 Project Server 2010 数据迁移到 Project Server 2019 的第一步是先迁移到 Project Server 2013。 
  
若要全面了解从 Project Server 2010 升级到 Project Server 2013 时需要执行的操作, 请参阅 TechNet 上的[升级到 Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822)内容集。 
  
主要资源:
  
|**Resource**|**说明**|
|:-----|:-----|
|[Project Server 2013 升级过程概述](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |了解从 Project Server 2010 升级到 Project Server 2013 时需要执行的操作的简要概述。  <br/> |
|[计划升级到 Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |查看从 Project Server 2010 升级到 Project Server 2013 时需要做出的规划注意事项, 包括系统要求。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>升级到此版本需要了解的事项

[Project Server 2013 中的新增功能升级](https://go.microsoft.com/fwlink/p/?linkid=841824)将告诉你在此版本中升级的一些重要更改, 最明显的是: 
  
- 没有到 Project Server 2013 的就地升级。 数据库附加方法是从 Project Server 2010 升级到 Project Server 2013 的唯一受支持的方法。
    
- 升级过程不仅会将 Project Server 2010 数据转换为 Project Server 2013 格式, 还会将四个 Project Server 2010 数据库合并到一个 Project Web App 数据库。
    
- SharePoint Server 2013 和 Project Server 2013 都更改为以前版本中基于声明的身份验证。 如果使用的是经典身份验证, 则需要进行升级时的注意事项。 有关详细信息，请参阅[在 SharePoint 2013 中从经典模式身份验证迁移到基于声明的身份验证](https://go.microsoft.com/fwlink/p/?linkid=841825)。
    
其他资源：
  
- [Project Server 2013 升级过程概述](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [升级数据库和 Project Web App 网站集 (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server 升级过程关系图](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [在8个简单的步骤中执行大量数据库整合 (Project Server 2010 至2013迁移)](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>步骤2迁移到 Project Server 2016

迁移到 Project Server 2013 并验证数据是否已成功迁移之后, 下一步是将数据迁移到 Project Server 2016。
  
若要全面了解从 Project Server 2013 升级到 Project Server 2016 时需要执行的操作, 请参阅[upgrade To Project server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) content set。
  
主要资源:
  
|**Resource**|**说明**|
|:-----|:-----|
|[Project Server 2016 升级流程概述](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |了解从 Project Server 2013 升级到 Project Server 2016 时需要执行的操作的简要概述。  <br/> |
|[规划升级到 Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |查看从 Project Server 2013 升级到 Project Server 2016 时需要做出的规划注意事项。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>升级到此版本需要了解的事项

[您需要了解的有关 Project Server 2016 升级的相关内容](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow)会告诉您对此版本的升级有一些重要更改, 其中包括: 
  
- 当您创建要将 Project server 2013 数据迁移到的 Project Server 2016 环境时, 请注意, Project Server 2016 安装文件包含在 SharePoint Server 2016 中。 有关详细信息, 请参阅[Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829)。
    
- 资源计划在 Project Server 2016 中已被弃用。 您的 Project Server 2013 资源计划将迁移到 Project Server 2016 和 Project Online 中的资源预订。 有关详细信息, 请参阅[概述: 资源预订](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870)。 
    
### <a name="step-3-migrate-to-project-server-2019"></a>步骤3迁移到 Project Server 2019

迁移到 Project Server 2016 并验证数据是否已成功迁移之后, 下一步是将数据迁移到 Project Server 2019。
  
若要全面了解从 Project Server 2016 升级到 Project Server 2019 时需要执行的操作, 请参阅[upgrade To Project server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) content set。
  
主要资源:
  
|**Resource**|**说明**|
|:-----|:-----|
|[Project Server 2019 升级过程概述](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |了解从 Project Server 2013 升级到 Project Server 2016 时需要执行的操作的简要概述。  <br/> |
|[规划升级到 Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |查看从 Project Server 2016 升级到 Project Server 2019 时需要做出的规划注意事项。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>升级到此版本需要了解的事项

[您需要了解的有关 Project Server 2019 升级的相关内容](https://go.microsoft.com/fwlink/p/?linkid=841827)会告诉您对此版本的升级有一些重要更改, 其中包括: 
  
- 升级过程会将您的数据从 Project Server 2016 数据库迁移到 SharePoint Server 2019 内容数据库。  Project Server 2019 不需要很长时间创建它在 SharePoint Server 服务器场中拥有 Project Server 数据库。

- 升级后, 请注意 Project Web App 中的几项更改。  有关这些内容的说明, 请参阅[Project Server 2019 中的新增功能](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges)。


## <a name="migrate-from-portfolio-server-2010"></a>从项目组合服务器2010迁移

项目组合服务器2010与 Project Server 2010 结合使用, 以实现项目组合策略、优先顺序和优化。 在此版本之后, 不会创建任何其他版本的 Project 项目组合服务器。 但是, 项目组合管理功能在后续 Project Server 版本和 Project Online 的 Premium 版本中可用。 无法将 Project 项目组合服务器2010中的数据迁移到其中一个。 将需要重新创建业务驱动因素等数据。
  
其他资源:
  
- [Project Online 服务说明](https://go.microsoft.com/fwlink/p/?linkid=841280): 请参阅 project Server 2016 和 Project Online 高级版中包含的项目组合管理功能。
    
- [Microsoft Office Project 项目组合服务器2010迁移指南](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>相关主题

[从 SharePoint 2010 升级](upgrade-from-sharepoint-2010.md)
  
[可帮助您从 Office 2010 服务器和客户端进行升级的资源](upgrade-from-office-2010-servers-and-products.md)
  

