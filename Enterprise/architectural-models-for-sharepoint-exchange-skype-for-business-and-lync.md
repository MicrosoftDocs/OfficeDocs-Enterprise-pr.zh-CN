---
title: SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: 摘要：获取介绍 SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型、部署和平台选项的 IT 海报。
ms.openlocfilehash: 9e6e4f2b32bb2e5b39f8891d8acddc0699cdbf8d
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102560"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型

这些 IT 海报介绍了 SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型和部署选项，并提供了在 Microsoft Azure 中部署 SharePoint 的设计信息。
  
借助 Microsoft 365，你可以将用户熟悉的协作和通信服务作为基于云的服务来提供。 有一些例外情况，无论是在本地部署还是使用 Microsoft 365，用户体验均保持不变。 此统一的用户体现使得决定在何处放置每个工作负荷以及在何处提出问题变得简单直接，例如：
  
- 如何确定选择哪个平台选项用于各个工作负载？
    
- 将任何服务保留在内部部署是否有意义？
    
- 混合部署合适的方案是什么样的？
    
- Microsoft Azure 如何适应图片？
    
- Azure 中的 Office 服务器工作负载所支持的配置是什么？
    
> [!TIP]
> Most of the posters on this page are available in multiple languages, including Chinese, English, French, German, Italian, Japanese, Korean, Portuguese, Russian, and Spanish. To download a poster in one of these languages, click the **More languages** link for that poster.
  
Let us know what you think! Send us email at [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
此页面链接到下列海报：
  
- **体系结构模型海报** 可以使用这些资源确定 SharePoint 2016 和 Skype for Business 2015 的理想平台和配置。
    
  - [Microsoft 2016 SharePoint 体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [SharePoint Server 2016 数据库](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Microsoft Skype for Business 2015 体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **平台选项海报** 可使用这些资源确定 SharePoint 2013、Exchange 2013 和Lync 2013 的理想平台和配置。
    
  - [SharePoint 2013 平台选项](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Exchange 2013 平台选项](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Lync 2013 平台选项](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **Azure 解决方案海报中的 SharePoint Server 2013** 可以使用 IT 海报确定 Azure 基础结构服务中 SharePoint Server 2013 工作负载的设计和配置。
    
  - [Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [设计示例：Microsoft Azure 中的 SharePoint 2013 Internet 站点](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [SharePoint 灾难恢复到 Microsoft Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>体系结构模型海报

These new IT posters for SharePoint 2016 and Skype for Business 2015 provide a way to compare the various deployment methods in an easy-to-print format. Each poster provides a list of all the configurations or platform options available and gives you the following information for each option:
  
- **概述** 平台的简短摘要，包括概念图。
    
- **最适用于** 非常适用于特定平台的常见方案。
    
- **许可要求** 部署所需的许可证。
    
- **体系结构任务** 架构师需要做出的决定。
    
- **IT 专业人员任务或职责** IT 员工需履行的日常职责。
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Microsoft SharePoint 2016 体系结构模型

|**项**|**说明**|
|:-----|:-----|
|[![SharePoint 2016 体系结构模型海报缩略图](media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| [Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | 此 IT 海报介绍了业务决策者和解决方案架构师需要了解的 SharePoint Online、Microsoft Azure 和 SharePoint 本地配置。 <br/><br/> - **SharePoint Online (SaaS)** – 通过服务型软件 (SaaS) 订阅模型使用 SharePoint。 <br/> - **SharePoint 混合** – 按你自己的步调将 SharePoint 网站和应用移到云。 <br/> - **SharePoint in Azure (IaaS)** - You extend your on-premises environment into Microsoft Azure and deploy SharePoint 2016 Servers there. (This is recommended for High Availability/Disaster Recovery and dev/test environments.) <br/> - **SharePoint 本地部署** – 规划、部署、维护和自定义你维护的数据中心中的 SharePoint 环境。 <br/> |
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>SharePoint Server 2016 数据库

|**项**|**说明**|
|:-----|:-----|
|[![SharePoint Server 2016 数据库海报的缩略图](media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| [Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | This IT poster is a quick reference guide for SharePoint Server 2016 databases. Each database has the following details: <br/><br/> - 大小 <br/> - 扩展指南 <br/> - I/O 模式 <br/> - 要求： <br/><br/>  The first page has the SharePoint system databases and the service applications that have multiple databases. The second page shows all of the service applications that have single databases. <br/><br/>  有关 SharePoint Server 2016 数据库的详细信息，请参阅 [SharePoint Server 2016 中的数据库类型和说明](https://docs.microsoft.com/SharePoint/technical-reference/database-types-and-descriptions) <br/> |
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Microsoft Skype for Business 2015 体系结构模型

|**项**|**说明**|
|:-----|:-----|
|[![Skype for Business 体系结构模型海报缩略图](media/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| [Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |本海报介绍了业务决策制定者和解决方案架构师需要了解的 Skype for Business Online、本地、混合、云 PBX 及与 Exchange 和 SharePoint 配置的集成。 <br/><br/> 它旨在使 IT 专业受众了解使用 Skype for Business Online 和 Skype for Business 本地可以利用的不同的基本体系结构模型。 <br/><br/>Start with whichever configuration best suits your organization's needs and future plans. Consider and use others as needed. For example, you might want to consider integration with Exchange and SharePoint or a solution that takes advantage of Microsoft's Cloud PBX offering.  <br/> |
   
## <a name="platform-options-posters"></a>平台选项海报

These IT posters for SharePoint 2013, Exchange 2013, and Lync 2013 provide a way to compare the various deployment methods at a single glance in a large poster format. Each poster provides a list of all the configurations or platform options available and gives you the following information for each option:
  
- **概述** 平台的简短摘要，包括概念图。
    
- **最适用于** 非常适用于特定平台的常见方案。
    
- **许可要求** 部署所需的许可证。
    
- **体系结构任务** 架构师需要做出的决定。
    
- **IT 专业人员任务或职责** IT 员工需履行的日常职责。
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>SharePoint 2013 平台选项

****

|**项**|**说明**|
|:-----|:-----|
|[![SharePoint 2013 平台选项的缩略图](media/SP-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |对于业务决策者 (BDM) 和架构师，此模型显示 SharePoint 2013、Microsoft 365 中的 SharePoint、与 Microsoft 365 的本地混合、Azure 和仅本地部署的平台选项。 它包括每个体系结构的概述、建议、许可证要求以及每个平台的架构师和 IT 专业人员任务列表。 突出显示了 Azure 上的几种 SharePoint 解决方案。 <br/> |
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Exchange 2013 平台选项

****

|**项**|**说明**|
|:-----|:-----|
|[![Exchange 平台选项的缩略图](media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |对于 BDM 和架构师，此模型介绍了可用的 Exchange 2013 平台选项。 客户可以从使用 Microsoft 365 的 Exchange Online、混合 Exchange、Exchange Server 本地和托管 Exchange 中进行选择。 此海报包括每个体系结构选项的详细信息，包括每个选项最理想的方案、许可证要求和 IT 专业人员职责。 <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Lync 2013 平台选项

****

|**项**|**说明**|
|:-----|:-----|
|[![Lync 平台选项的缩略图](media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |对于 BDM 和架构师，此模型介绍了可用的 Lync 2013 平台选项。 客户可以从使用 Microsoft 365 的 Lync Online、混合 Lync、Lync Server 内部部署和托管 Lync 中进行选择。 IT 海报包括每个体系结构选项的详细信息，包括每个选项最理想的方案、许可证要求和 IT 专业人员职责。  <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>Azure 解决方案中的 SharePoint 海报

这些 IT 海报以大型海报形式说明了使用 SharePoint Server 2013 的基于 Azure 的解决方案。
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点

****

|**项**|**说明**|
|:-----|:-----|
|[![使用 SharePoint 的 Azure 中的 Internet 网站图像](media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |此海报概述了在 Azure 中构建面向 Internet 的网站时所涉及的关键设计活动和推荐体系结构。  <br/><br/> 有关详细信息，请参阅以下文章：  <br/><br/> - [Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [用于 SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="DesignSampleInternetSites"> </a>
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>设计示例：Microsoft Azure 中的 SharePoint 2013 Internet 站点

****

|**项**|**说明**|
|:-----|:-----|
|[![设计示例图像：Microsoft Azure for SharePoint 2013 中的 Internet 站点](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |从此设计示例入手，在 Azure 中使用 SharePoint Server 2013 构建你自己的面向 Internet 的网站。 <br/><br/> 有关详细信息，请参阅以下文章：  <br/><br/> - [Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [用于 SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>SharePoint 灾难恢复到 Microsoft Azure

****

|**项**|**说明**|
|:-----|:-----|
|[![到 Azure 的 SharePoint 灾难恢复过程](media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| [更多语言](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |此 IT 海报显示 Azure 中的灾难恢复环境的体系结构原则。 <br/><br/> 有关详细信息，请参阅以下文章：  <br/><br/> - [Microsoft Azure 中的 SharePoint Server 2013 灾难恢复](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [用于 SharePoint 2013 的 Microsoft Azure 体系结构](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
## <a name="see-also"></a>另请参阅

[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.yml)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
  
[Microsoft 365 企业版测试实验室指南](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)
  
[混合解决方案](hybrid-solutions.md)

