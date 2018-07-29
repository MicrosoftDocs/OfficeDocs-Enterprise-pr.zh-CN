---
title: Project Server 2007 停止提供支持路线图
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
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
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: 在 2017 年 10 月 10，支持结束 Project Server 2007、 Project Portfolio Server 和 Project 2007。使用本文现在规划您的升级。
ms.openlocfilehash: 5b2fb194d4819b5427cb2844a5189b2b03753800
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169894"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project Server 2007 停止提供支持路线图

支持在 2017，正在结束 Office 2007 服务器和应用程序，您需要考虑的迁移计划。如果您当前正在使用 Project Server 2007，请注意，且这些其他相关的产品将具有以下支持的结束日期：
  
|**产品**|**支持日期的末尾**|
|:-----|:-----|
|Project Server 2007  <br/> |2017 年 10 月 10 日  <br/> |
|Project Portfolio Server 2007  <br/> |2017 年 10 月 10 日  <br/> |
|Project 2007 标准  <br/> |2017 年 10 月 10 日  <br/> |
|Project 2007 Professional  <br/> |2017 年 10 月 10 日  <br/> |
   
有关 Office 2007 服务器达到退休的详细信息，请参阅[从 Office 2007 服务器和客户端产品升级](upgrade-from-office-2007-servers-and-products.md)。
  
## <a name="what-does-end-of-support-mean"></a>支持平均值内容的末尾？

Project Server，如几乎在所有 Microsoft 产品，具有支持生命周期期间我们提供的新功能、 bug 修复、 安全修补程序，等等。此生命周期通常会持续 10 年中的产品的初始发布日期和此生命周期的结束称为产品的结束的支持。由于 Project Server 2007 达到其结束的支持上 2017 年 10 月 10，将不再提供 Microsoft:
  
- 可能出现的问题的技术支持。
    
- Bug 修复的问题的发现以及可能影响的稳定性和服务器的可用性。
    
- 安全漏洞的发现和可能使该服务器安全轻易地受到修补程序。
    
- 更新所在的时区。
    
Project Server 2007 安装将继续此日期之后运行。但是，由于上面列出的更改，强烈建议您迁移从 Project Server 2007 尽快。
  
## <a name="what-are-my-options"></a>我的选项是什么？

如果您使用 Project Server 2007，您需要了解您迁移选项，它们是：
  
- 将迁移到 Project Online
    
- 将迁移到新的本地版本的 Project Server (最好是 Project Server 2016)。
    
|**为什么我想要迁移到 Project Online**|**为什么我想要迁移到 Project Server 2016**|
|:-----|:-----|
| 我已移动的用户。  <br/>  要迁移的成本是更大的问题 （硬件、 软件、 时间和精力实现等）。  <br/>  迁移后，若要维护我的环境的成本是更大的问题 （例如，自动更新，保证正常运行时间等。）。  <br/> | 业务规则限制我操作系统我在云中的业务。  <br/>  我为我的环境需要更新的控件。  <br/> |
   
> [!NOTE]
> 有关从 Office 2007 服务器的选项的详细信息，请参阅[资源以帮助您升级从 Office 2007 的服务器和客户端](upgrade-from-office-2007-servers-and-products.md)。请注意，Project Server 不支持混合配置相 Project Server 和 Project Online 不能共享相同的资源库。 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2007"></a>您需要进行规划从 Project Server 2007 迁移时做出的重要注意事项

您需要从 Project Server 2007 迁移规划时应考虑以下：
  
- **获取来自 Microsoft 合作伙伴的帮助**-从 Project Server 2007 升级会很困难，并需要大量的准备和计划。如果未安装和配置 Project Server 2007 最初是，它可以是特别具挑战性。幸运的是，有 Microsoft 合作伙伴就可以开始执行此操作的工作，无论您计划迁移到 Project Server 2016 或 Project Online。您可以搜索 Microsoft 合作伙伴来帮助您迁移对[Microsoft 合作伙伴中心](https://go.microsoft.com/fwlink/p/?linkid=841249)。可以通过搜索*金色项目和项目组合管理*该术语提升的专业知识项目中的所有 Microsoft 合作伙伴的列表。 
    
- **规划自定义项**-请注意，许多具有使用 Project Server 2007 环境中的自定义项可能无法运行迁移到 Project Server 2016 或 Project Online 时。有之间版本，以及所需的操作系统、 数据库服务器和客户端 web 浏览器支持以使用新版本的 Project Server 体系结构中的大区别。有关如何测试或重新生成自定义项，根据需要在新环境中的位置中具有计划。规划升级还将验证向前移动时，是否确实需要的特定自定义项的好机会。[创建升级到 SharePoint 2013 期间的当前自定义的计划](https://go.microsoft.com/fwlink/p/?linkid=842061)已评估和规划您的当前自定义设置升级时某些绝佳一般信息。 
    
- **时间和等待时间**-规划、 执行和测试升级将需要大量的时间和精力，尤其是要升级到 Project Server 2016。例如，如果要从 Project Server 2007 迁移到 Project Server 2016，您将首先需要从 Project Server 2007 迁移到 Project Server 2010，然后检查数据，并将迁移到每个后续版本时，然后执行相同的操作。您可能希望与 Microsoft 合作伙伴进行比较的它将花费的其执行的操作，并在什么成本其估计与您的成本。 
    
## <a name="migrate-to-project-online"></a>将迁移到 Project Online

如果您选择从 Project Server 2007 迁移到 Project Online，您可以执行以下手动迁移项目计划数据：
  
1. 保存到 Project Server 2003 中的项目计划。MPP 格式。
    
2. 使用 Project Professional 2013、 Project Professional 2016 或 Project Online 桌面客户端，打开每个.mpp 文件，然后保存并将其发布到 Project Online。
    
Project Online 中手动创建 PWA 配置 （例如，重新创建任何所需的自定义域或企业日历）。Microsoft 合作伙伴还可以帮助您与此。
  
关键资源：
  
|**资源**|**说明**|
|:-----|:-----|
|[Project Online 入门](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |如何安装和使用 Project Online。  <br/> |
|[Project Online 服务说明](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |有关可供您的不同 Project Online 计划的信息。  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>迁移到新的本地版本的 Project Server

尽管我们强烈相信，您可以通过迁移到 Project Online 中实现的最佳值和用户体验，我们还了解一些组织需要在内部部署环境中保留项目数据。如果您选择保留项目数据在本地，您可以将您的 Project Server 2007 环境迁移到 Project Server 2010、 Project Server 2013 或 Project Server 2016。
  
我们建议，如果不能迁移到 Project Online 迁移到 Project Server 2016。Project Server 2016 包含所有的功能和改进包括与早期版本的 Project Server 和它最为匹配具有 Project Online 的体验 （尽管某些功能仅在 Project Online 中可用）。
  
完成每个迁移之后，您应该检查数据以确保它已成功迁移。
  
> [!NOTE]
> 如果您正在考虑仅迁移到 Project Server 2010，如果您仅限于内部部署解决方案，务必注意，它仅有几年以上的左的支持。Project Server 2010 Service Pack 2 是支持日期结束 10/13/2020。有关支持的日期结束的详细信息，请参阅[Microsoft 产品生命周期策略](https://go.microsoft.com/fwlink/p/?linkid=842066)。 
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>如何向 Project Server 2016 迁移？

Project Server 2007 和 Project Server 2016 的体系结构区别阻止直接的迁移路径。这意味着，您需要将 Project Server 2007 数据迁移到 Project Server 的下一个后续版本，直到升级到 Project Server 2016。
  
您需要执行以下操作来升级到 Project Server 2016:
  
1. 从 Project Server 2007 到 Project Server 2010 迁移步骤 1:。
    
2. 步骤 2： 从项目服务 2010年到 Project Server 2013 迁移。
    
3. 从 Project Server 2013 到 Project Server 2016 迁移步骤 3:。
    
完成每个迁移之后，您应该检查数据以确保它已成功迁移。
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>从 Project Server 2007 到 Project Server 2010 迁移步骤 1:

您需要执行的操作从 Project Server 2007 升级到 Project Server 2010 全面了解，请参阅 TechNet 上的[升级到 Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812)内容集。 
  
关键资源：
  
|**资源**|**说明**|
|:-----|:-----|
|[Project Server 2010 升级概述](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |获取了解您需要执行的操作从 Project Server 2007 升级到 Project Server 2010。  <br/> |
|[规划升级到 Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |查看规划您需要进行从 Project Server 2007 升级到 Project Server 2010，包括系统要求时的注意事项。  <br/> |
   
#### <a name="how-do-i-upgrade"></a>如何升级？

[升级到 Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812)内容集合中，可以找到有关如何升级的详细信息时, 非常重要了解有两种不同方法，您可以使用升级： 
  
- **的数据库附加升级：** 此方法仅升级您的环境，以及不的配置设置的内容。如果您要从 Office Project Server 2007 仅支持 32 位服务器操作系统的硬件上部署升级，则需要。有两种类型的数据库附加升级方法： 
    
  - **数据库附加完整升级**-迁移存储在 Office Project Server 2007 数据库中的项目数据以及存储在 SharePoint 内容数据库的 Microsoft Project Web App (PWA) 网站数据。 
    
  - **数据库附加核心升级**-迁移存储在 Project Server 数据库中的项目数据。 
    
- **就地升级**： 在现有硬件上，按固定顺序升级的服务器场和服务器场上的所有内容的配置数据。当您在开始就地升级过程时，安装所需的整个服务器场脱机和网站和 Microsoft Project Web App 网站不可用，直到升级完成后，安装程序然后重新启动服务器。在开始就地升级之后，您无法暂停升级或回滚到以前的版本。强烈建议以使您的生产环境的镜像的图像并执行就地升级到此环境中，并不是您的生产环境。 
    
其他资源：
  
- [SuperFlow Microsoft Project Server 2010 升级](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [从 Project Server 2007 到 Project Server 2010 的迁移](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [Project Web App Web 部件的升级注意事项](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [项目软件开发工具包 (SDK)](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>步骤 2： 迁移到 Project Server 2013

后迁移到 Project Server 2010 和验证您的数据已成功迁移下, 一步是将数据迁移到 Project Server 2013。
  
全面了解您需要执行的操作从 Project Server 2010 升级到 Project Server 2013，请参阅 TechNet 上的[升级到 Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822)内容集。 
  
关键资源：
  
|**资源**|**说明**|
|:-----|:-----|
|[概述 Project Server 2013 升级过程](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |获取所需执行的操作从 Project Server 2010 升级到 Project Server 2013 了解。  <br/> |
|[Plan to upgrade to Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |查看规划您需要进行从 Project Server 2010 升级到 Project Server 2013，包括系统要求时的注意事项。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>有关升级到该版本须知

[What's new in Project Server 2013 升级](https://go.microsoft.com/fwlink/p/?linkid=841824)告诉您对于此版本，最重要的正在升级的一些重要更改： 
  
- 没有任何就地升级到 Project Server 2013。数据库附加方法是从 Project Server 2010 升级到 Project Server 2013 的唯一受支持的方法。
    
- 升级过程不仅将 Project Server 2010 数据转换为 Project Server 2013 格式，但还将合并为单个 Project Web App 数据库四个 Project Server 2010 数据库。
    
- 更改为基于声明的身份验证从早期版本 SharePoint Server 2013 和 Project Server 2013。您将需要进行升级如果要使用经典身份验证时的注意事项。有关详细信息，请参阅[从经典模式为 SharePoint 2013 中基于声明的身份验证的迁移](https://go.microsoft.com/fwlink/p/?linkid=841825)。
    
其他资源：
  
- [升级到 Project Server 2013 的流程概述](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [升级数据库和 Project Web App 网站集 (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server 升级流程图](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [出色的数据库合并，8 个简单步骤的 Project Server 2010 到 2013年迁移](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>步骤 3： 迁移到 Project Server 2016

后迁移到 Project Server 2013 和验证您的数据已成功迁移下, 一步是将数据迁移到 Project Server 2016。
  
您需要执行的操作从 Project Server 2013 升级到 Project Server 2016 全面了解，请参阅 TechNet 上设置升级到 Project Server 2016 内容。
  
关键资源：
  
|**资源**|**说明**|
|:-----|:-----|
|[Project Server 2016 升级流程概述](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |获取所需执行的操作从 Project Server 2013 升级到 Project Server 2016 了解。  <br/> |
|[规划升级到 Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |查看规划您需要进行从 Project Server 2013 升级到 Project Server 2016，包括时的注意事项。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>有关升级到该版本须知

[您需要了解的有关 Project Server 2016 事项升级](https://go.microsoft.com/fwlink/p/?linkid=841827)向您介绍一些重要更改 upgrade for 此版本中，其中包括： 
  
- 创建 Project Server 2016 环境将向其迁移 Project Server 2013 数据时，请注意： SharePoint Server 2016 中包含的 Project Server 2016 安装文件。有关详细信息，请参阅[部署 Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829)。
    
- 资源计划中 Project Server 2016 弃用。Project Server 2013 资源计划将迁移到 Project Server 2016 和 Project Online 中的资源服务。请参阅[概述： 资源服务](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870)的详细信息。 
    
## <a name="migrate-from-portfolio-server-2007"></a>从 Portfolio Server 2007 迁移

Project Portfolio Server 2007 所用 Project Server 2007 项目组合策略、 确定优先级和优化。此版本之后不创建任何其他版本的 Project Portfolio Server。但是，Project Server 2016 和高级版本的 Project Online 中提供了项目组合管理功能。不能从 Project Portfolio Server 2007 的数据迁移到。例如，业务驱动因素的数据将需要重新创建。
  
其他资源：
  
- [Project Online 服务说明](https://go.microsoft.com/fwlink/p/?linkid=841280)： 请参阅 Project Server 2016 和 Project Online Premium 中包含的项目组合管理功能。
    
- [Microsoft Office Project Portfolio Server 2007 迁移指南](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>相关主题

[SharePoint Server 2007 结束的支持路线图](sharepoint-2007-end-of-support.md)
  
[资源可帮助您升级从 Office 2007 的服务器和客户端](upgrade-from-office-2007-servers-and-products.md)
  

