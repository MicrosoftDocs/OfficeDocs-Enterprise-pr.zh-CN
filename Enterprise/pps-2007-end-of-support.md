---
title: PerformancePoint Server 2007 停止提供支持路线图
ms.author: deniseb
author: denisebmsft
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- PSV120
- PDD140
- MET150
ms.assetid: 89d9feee-2285-419c-8c14-0f7f583536e0
f1.keywords:
- NOCSH
description: PerformancePoint Server 2007、ProClarity 和 SharePoint Server 2007 已到达支持的结束。 阅读本文以规划您的 BI 解决方案升级。
ms.openlocfilehash: 89f13a9fba91195c8e3ecfcdaaebb52a27307eef
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844093"
---
# <a name="performancepoint-server-2007-end-of-support-roadmap"></a>PerformancePoint Server 2007 停止提供支持路线图

*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*

Office 2007 服务器和应用程序已达到其支持的结尾，包括您可能在商业智能（BI）解决方案中使用的服务器和应用程序。 下表列出了受影响的 BI 应用程序：
  
|**Microsoft BI 应用程序**|**日期支持结束**|
|:-----|:-----|
|ProClarity Analytics Server 6.3 Service Pack 3  <br/> ProClarity Desktop Professional 6。3  <br/> ProClarity SharePoint Viewer 6。3  <br/> |2017 年 7 月 11 日  <br/> |
|SharePoint Server 2007 Service Pack 3  <br/> |2017 年 10 月 10 日  <br/> |
|PerformancePoint Server 2007 Service Pack 3  <br/> |2018 年 1 月 9 日  <br/> |
   
有关详细信息，请参阅可[帮助您从 Office 2007 服务器和客户端升级的资源](upgrade-from-office-2007-servers-and-products.md)。
  
## <a name="what-does-end-of-support-mean"></a>支持终止的含义是什么？

Microsoft 产品（例如 PerformancePoint Server 2007 SP3、ProClarity 软件和 SharePoint Server 2007 SP3）都具有支持生命周期，在此期间，Microsoft 提供了新的功能、缺陷修补程序和安全更新。 产品的生命周期通常是从产品初始发布之日起10年后，而该生命周期的结束时间也称为产品的支持终止。 由于 ProClarity、PerformancePoint Server 和 SharePoint Server 2007 已达到其支持的结束时间，Microsoft 将不再提供：
  
- 可能出现的问题的技术支持
    
- 针对已发现且可能影响服务器稳定性和可用性的问题的 Bug 修补程序
    
- 针对发现的漏洞的安全修补程序，可能导致服务器或应用程序易受安全破坏
    
- 时区更新
    
您安装的 ProClarity、SharePoint Server 2007 SP3 和 PerformancePoint Server 2007 SP3 仍将继续运行，即使支持已结束。 但是，强烈建议您尽快从这些应用程序迁移。
  
## <a name="what-are-my-options"></a>我的选项是什么？

通过这些 BI 应用程序来实现支持的结束，这是查看选项和准备升级计划的良好时间。 自2007起对 Microsoft BI 应用程序进行了大量更改，并且有几个选项需要考虑，如下表所示：
  
|**如果您使用的是 .。。**|**浏览这些选项 .。。**|**请记住这一点 .。。**|
|:-----|:-----|:-----|
| PerformancePoint Server 2007 监视&amp;分析功能，包括：  <br/><br/>  PerformancePoint 监控服务器  <br/><br/>  PerformancePoint 仪表板设计器  <br/><br/>  SharePoint Services 的仪表板查看器（用于呈现 PerformancePoint 仪表板、记分卡和报表）  <br/> |**Excel 在浏览器中**（在云中或本地）的 excel。 有关概述，请参阅[BI 功能在 Excel 和 Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) <br/><br/> **POWER BI** （在云中或本地）。 有关概述，请参阅[什么是 POWER BI？](https://go.microsoft.com/fwlink/?linkid=841341) <br/><br/> **SQL Server Reporting Services** （本地）。 有关概述，请参阅[SQL Server Reporting Services （SSRS）：创建、部署和管理移动和分页报告](https://go.microsoft.com/fwlink/?linkid=841342) <br/><br/> **PerformancePoint Services** （本地）。 有关概述，请参阅[什么是针对 PerformancePoint Services 的新增功能（SharePoint Server 2010）](https://go.microsoft.com/fwlink/?linkid=841343) <br/> |Excel 可用作联机（基于云）解决方案或本地解决方案。 Excel 的功能可以满足许多报告和仪表板需求。  <br/><br/> Power BI 可用作联机或本地解决方案。 Power BI 不包括在 Office 365 中，但你可以开始使用 Power BI 免费版，然后根据你的数据使用和业务需求升级到 Power BI Pro。 <br/> <br/> Reporting Services 和 PerformancePoint Services 都是本地解决方案。  <br/><br/> PerformancePoint Services 在 SharePoint Server 2010、SharePoint Server 2013 和 SharePoint Server 2016 中可用。 <br/> <br/> PerformancePoint Server 2007 中提供的某些功能和报告类型在 Excel、Power BI、Reporting Services 或 PerformancePoint Services 中不可用。 你将需要查看可用的功能，以确定满足你的业务需求的最佳解决方案。  <br/> |
| ProClarity 软件，包括： <br/> <br/>  ProClarity Desktop Professional  <br/> <br/> ProClarity Analytics Server  <br/> <br/> ProClarity SharePoint Viewer  <br/> |**与 Microsoft 合作伙伴合作**，确定最符合您的需求的解决方案。 访问[Microsoft 合作伙伴中心](https://go.microsoft.com/fwlink/?linkid=841249) <br/><br/> 您还可以考虑在浏览器、Power BI、SQL Server Reporting Services 或 PerformancePoint Services 中使用 excel 和 Excel。  <br/> |其他 Microsoft 产品（包括 Excel、Power BI、Reporting Services 和 PerformancePoint Services）中提供了在 ProClarity 软件中可用的几种（但并非全部）的特性和功能。  <br/> |
|SharePoint Server 2007 Kpi （也称为 MOSS Kpi）  <br/> |Excel **Services 的 excel**。 有关概述，请参阅[excel 和 Excel Services 中的商业智能（SharePoint Server 2013）](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |使用 SharePoint Server 2007 创建的 MOSS Kpi 可在 SharePoint Server 2010、SharePoint Server 2013 和 SharePoint Server 2016 中使用。但是，不能创建新的 MOSS Kpi。  <br/> |
|Excel 2007  <br/> |**Excel** （在云中或本地）。 有关概述，请参阅[BI 功能在 Excel 和 Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) <br/><br/> **POWER BI** （在云中或本地）。 有关概述，请参阅[什么是 POWER BI？](https://go.microsoft.com/fwlink/?linkid=841341) <br/> |Excel 和 Power BI 都为你的组织提供基于云的解决方案和内部部署解决方案，并支持多种数据源。  <br/> |
   
### <a name="what-if-i-need-help-selecting-a-solution"></a>如果我需要有关选择解决方案的帮助，该怎么办？

由于提供了很多 BI 选项，因此最好确定哪个选项是最佳选择。 我们提供了可帮助你的在线指南。 请参阅[选择 Microsoft 商业智能（BI）工具以进行分析和报告](https://go.microsoft.com/fwlink/?linkid=839877)。
  
### <a name="what-happens-if-i-dont-upgrade-now"></a>如果现在不升级，会发生什么情况？

你可以选择现在不升级。 现有的服务器和应用程序将继续运行。 但是，在支持结束后，你将不会收到任何进一步的更新-包括安全更新。 如果你的服务器应用程序出现问题，你将无法从 Microsoft 技术支持获得帮助。
  
## <a name="how-do-i-plan-my-upgrade"></a>如何规划升级？

在您研究了升级选项之后，下一步是准备升级计划。 以下各节包含可帮助您规划解决方案的其他资源的信息和链接。 在 Microsoft BI 应用程序中，有四个主要选项，包括在云或内部部署中使用的两种方法，以及两个仅本地解决方案的选项：
  
|**选项**|**在云中还是内部部署？**|
|:-----|:-----|
|[Excel](#excel-with-sharepoint-server-on-premises) <br/> |两者都有  <br/> |
|[Power BI](#use-power-bi-in-the-cloud-or on-premises) <br/> |两者都有  <br/> |
|[Reporting Services](#use-reporting-services-on-premises) <br/> |仅本地  <br/> |
|[PerformancePoint 服务](#use-performancepoint-services-on-premises) <br/> |仅本地  <br/> |
   
### <a name="use-excel-in-the-cloud-or-on-premises"></a>使用 Excel （在云中或本地）

使用 Excel （也称为 "Excel Services"）在 SharePoint Server 中，用户可以在浏览器窗口中查看和使用工作簿，即使其计算机上未安装 Excel 也是如此。 您可以使用 Excel 创建报表、记分卡和仪表板，然后使用 Excel 在浏览器中与其他人共享工作簿，无论您是使用 SharePoint Online 作为 Office 365 的一部分还是本地 SharePoint Server。 此外，您还可以使用存储在本地或在云中的数据，这使您能够使用多种数据源。
  
下表比较了使用 Excel 与 Office 365 结合使用 Excel 和 SharePoint Server 的主要优势，并提供了以下附加信息。
  
|**[使用 Office 365 的 Excel （在云中）](#excel-with-office-365-in-the-cloud)**|**[Excel 与 SharePoint Server （本地）](#excel-with-sharepoint-server-on-premises)**|
|:-----|:-----|
|**您将获得最新版本的 Excel**。 使用 Office 365，你可以获得最新版本的 Excel，其中包括功能强大的新图表类型、快速轻松地创建图表和表格以及支持更多数据源的功能。 <br/> <br/> **安装更简单**。 Excel 包含在 Office 365 for business 中，因此不会对你的部件进行繁重的提升。 注册并登录，你将能够更快、更高效地运行，而不是升级你的本地服务器。 <br/> <br/> **用户可以随时随地访问他们的工作簿**。 用户可以使用其计算机、智能手机和平板电脑，从任何位置安全地查看工作簿。 <br/> <br/> **还有更多**！ 查看[Excel 和 Office 365 中的 BI 功能](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) <br/> |**管理全局设置**。 作为 SharePoint 管理员，您可以指定全局设置，如安全性、负载平衡、会话管理、工作簿缓存和外部数据连接。 <br/> <br/> **可以将 Excel services 与 PerformancePoint services 结合使用**。 您可以将 Excel Services 和 PerformancePoint Services 配置为 SharePoint Server 安装的一部分，并在 PerformancePoint 仪表板中包括 Excel Services 报表。 <br/> <br/> **还有更多**！ 请参阅[在 excel 和 Excel Services 中的商业智能（SharePoint Server 2013）](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |
   
#### <a name="excel-with-office-365-in-the-cloud"></a>使用 Office 365 的 Excel （在云中）

如果您转到 Office 365，您将拥有最新的服务和应用程序，包括 Excel 2016。 PerformancePoint Services 在 Office 365 中不可用，因此你将使用 Excel 工作簿或其他报表替换 PerformancePoint 仪表板内容。 好消息是，Excel 2016 具有大量新图表类型，在 Excel 中创建令人耳目一新的仪表板比以往更轻松。 同时，还会定期添加新功能。 若要了解详细信息，请参阅[Excel 2016 For Windows 中的新增功能](https://support.office.com/article/5fdb9208-ff33-45b6-9e08-1f5cdb3a6c73.aspx)。
  
当您购买50个座位或更多的 Office 365 时，Microsoft FastTrack 团队可以帮助您进行设置。 若要了解详细信息，请访问[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365/office-365)。
  
#### <a name="excel-with-sharepoint-server-on-premises"></a>Excel 与 SharePoint Server （本地）

如果升级到较新版本的 SharePoint，则可以使用 excel Services 或浏览器中的 Excel，如下所示：
  
- SharePoint Server 2010 中的 Excel Services
    
- SharePoint Server 2013 中的 Excel Services
    
- Excel （它是 Office Online Server 的一部分）独立于 SharePoint Server 2016 安装
    
您还可以在新版本的 SharePoint Server 中配置 PerformancePoint Services，并将其与 Excel 一起使用。
  
若要了解有关你的 SharePoint 升级选项的详细信息，请参阅[Sharepoint Server 2007 end of Support 路线图](sharepoint-2007-end-of-support.md)。
  
若要了解有关 Excel Services 的详细信息，请参阅[Excel services 概述（SharePoint Server 2010）](https://go.microsoft.com/fwlink/?linkid=841362)。
  
### <a name="use-power-bi-in-the-cloud-or-on-premises"></a>使用 Power BI （在云中或内部部署中）

Power BI 是一套用于分析数据和共享见解的业务分析工具。 使用 Power BI，可以使用内部部署或联机数据源创建交互式报告和仪表板。 用户可以使用其计算机或移动设备查看和使用报告和仪表板。
  
Power BI 不包括在 Office 365 或 SharePoint Server 中，但是一个单独的服务，其中包括 Power BI Desktop、Power BI 网关和 Power BI 服务。 Power BI 还与 SharePoint Online 集成。 你可以免费开始使用 Power BI，并根据你的数据使用情况和业务需求升级到 Power BI Pro。 若要了解详细信息，请参阅[什么是 POWER BI？](https://go.microsoft.com/fwlink/?linkid=841341)
  
### <a name="use-reporting-services-on-premises"></a>使用 Reporting Services （本地）

SQL Server Reporting Services 提供了一个强大的报告解决方案，以及在本机模式或 SharePoint 集成模式下安装和配置 Reporting Services 的功能。 您可以使用多个工具（包括报表设计器、报表生成器和 Power View）创作报表。 使用最新版本的 SQL Server，您还可以使用 SQL Server 移动报表发布服务器来提供可扩展到任何屏幕大小的报告，从而使您的组织能够在其移动设备上使用报告。 若要了解详细信息，请参阅[SQL Server Reporting Services （SSRS）：创建、部署和管理移动和分页报告](https://go.microsoft.com/fwlink/?linkid=841342)。
  
### <a name="use-performancepoint-services-on-premises"></a>使用 PerformancePoint Services （本地）

如你所知，PerformancePoint Server 2007 是独立于 SharePoint Server 2007 购买的。 从 SharePoint Server 2010 开始，PerformancePoint Services 是 SharePoint Server 中的服务应用程序。 这意味着，您不必购买单独的服务器许可证或硬件即可使用 PerformancePoint Services。
  
若要从 PerformancePoint Server 2007 移动到 PerformancePoint Services，请移动到 SharePoint Server 的更新版本，并配置 PerformancePoint Services。 您要移动到的 SharePoint Server 版本将确定是否可以将现有仪表板内容从 PerformancePoint Server 2007 导入到 PerformancePoint Services。
  
- 如果您正在升级到 SharePoint Server 2010，则可以将 PerformancePoint 仪表板内容从 PerformancePoint Server 2007 导入 SharePoint Server 2010 中的 PerformancePoint Services。 若要了解如何工作的详细信息，请参阅[导入向导：将 PerformancePoint Server 2007 内容重设为 SharePoint server 2010](https://go.microsoft.com/fwlink/?linkid=838873)。
    
- 如果您正在迁移到 SharePoint Server 2013 或 SharePoint Server 2016，则很可能需要创建新的仪表板内容（数据源、报表、记分卡和仪表板页面）。
    
若要开始了解 PerformancePoint Services 升级计划，请参阅以下资源：
  
1. [SharePoint Server 2007 结束支持路线图](sharepoint-2007-end-of-support.md)
    
2. 当您知道要移动到的 SharePoint 版本时，请参阅 PerformancePoint Services 的相应文章：
    
  - [规划 PerformancePoint Services （SharePoint Server 2010）](https://go.microsoft.com/fwlink/?linkid=841363)
    
  - [SharePoint Server 2013 中的 PerformancePoint Services 概述](https://go.microsoft.com/fwlink/?linkid=841551)
    
  - [SharePoint Server 2016 中的 PerformancePoint Services 概述](https://go.microsoft.com/fwlink/?linkid=874704)
    
当您升级到 PerformancePoint Services 时，您将喜欢几个新的功能和增强功能。 PerformancePoint Services 提供改进的记分卡、新的可视化项（如分解树）和 KPI 详细信息报表以及更多的图表类型、更好的时间智能筛选功能以及改进的可访问性合规性。 若要了解详细信息，请参阅[What's new For PerformancePoint Services （SharePoint Server 2010）](https://go.microsoft.com/fwlink/?linkid=841343)。
  
## <a name="where-can-i-get-help-with-my-upgrade"></a>在哪里可以获取有关升级的帮助？

无论是本地升级还是迁移到 Office 365，我们都建议使用 Microsoft 合作伙伴。 合格的合作伙伴可帮助您确定最能满足您的业务需求的解决方案，并协助您的部署。 访问[Microsoft 合作伙伴中心](https://go.microsoft.com/fwlink/?linkid=841249)，并使用搜索筛选器查找解决方案提供商。
  
## <a name="related-topics"></a>相关主题

[可帮助您从 Office 2007 服务器和客户端进行升级的资源](upgrade-from-office-2007-servers-and-products.md)
  
[Office 退休组（Microsoft 技术社区）](https://go.microsoft.com/fwlink/?linkid=842065)


  

