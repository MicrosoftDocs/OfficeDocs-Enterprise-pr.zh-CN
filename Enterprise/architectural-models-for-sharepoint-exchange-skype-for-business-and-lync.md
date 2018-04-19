---
title: SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/11/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
description: 摘要： 获取描述体系结构模型、 部署和平台选项 SharePoint、 交换、 Skype 业务和 Lync IT 海报。
ms.openlocfilehash: ac3ba3f8a0786ec28c9aa6099f288811802bd92d
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型

 **摘要：**获取描述体系结构模型、 部署和平台选项 SharePoint、 交换、 Skype 业务和 Lync IT 海报。
  
这些 IT 海报介绍了 SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型和部署选项，并提供了在 Microsoft Azure 中部署 SharePoint 的设计信息。
  
使用 Office 365 可以提供您的用户是熟悉作为基于云服务的协作和通信服务。少数例外情况之外，用户体验不变是否是维护内部部署或使用 Office 365。这种统一的用户体验就不太容易决定在何处放置每个工作负载，如引发的问题：
  
- 如何确定选择哪个平台选项用于各个工作负载？
    
- 将任何服务保留在内部部署是否有意义？
    
- 混合部署合适的方案是什么样的？
    
- Microsoft Azure 图片中如何适应？
    
- Azure 中的 Office 服务器工作负载所支持的配置是什么？
    
> [!TIP]
> 此页上的大多数海报都有多个语言版本，包括中文、英语、法语、德语、意大利语、日语、朝鲜语、葡萄牙语、俄语和西班牙语。若要下载其中一种语言的海报，请单击相应海报的**更多语言**链接。
  
请将你的想法告诉我们！向我们 ([cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com)) 发送电子邮件。 
  
此页面链接到下列海报：
  
- **体系结构建模海报**这些资源可用于确定您的理想平台和配置 SharePoint 2016 和业务 2015年的 Skype。
    
  - [Microsoft SharePoint 2016 体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [Office 365 中的 OneDrive 的多地区预览](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#MultiGeoO365ODB)
    
  - [SharePoint 服务器 2016年数据库](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Microsoft Skype 业务 2015年体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **平台选项海报**这些资源可用于确定您的理想平台和配置 SharePoint 2013、 交换 2013年和 Lync 2013。
    
  - [SharePoint 2013 平台选项](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [交换 2013年平台选项](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Lync 2013 平台选项](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **在 Azure 解决方案海报中的 SharePoint Server 2013**这些 IT 海报可用于确定的设计和配置 SharePoint Server 2013 Azure 的基础结构服务中的工作负载。
    
  - [在使用 SharePoint Server 2013 Microsoft Azure 中的 Internet 站点](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [设计示例： 在 SharePoint 2013 的 Microsoft Azure 中的 Internet 站点](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [对 Microsoft Azure 的 SharePoint 灾难恢复](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>体系结构模型海报

这些 SharePoint 2016 和 Skype for Business 2015 的新 IT 海报，提供了一种以轻松打印形式比较各种部署方法的方式。每张海报都提供了所有配置或平台的可用选项列表，并针对每个选项提供了以下信息：
  
- **概述**平台，包括概念图的简要总结。
    
- **最适用于**最适合于特定平台的常见方案。
    
- **许可证要求**部署所需的许可证。
    
- **体系结构的任务**作为架构师，您需要决定。
    
- **IT 专业人员的任务或职责**您的 IT 员工需要规划日常职责。
    
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Microsoft 2016 SharePoint 体系结构模型
<a name="SP2016_ArchModel"> </a>

|**项目**|**说明**|
|:-----|:-----|
|[![SharePoint 体系结构模型 2016年海报的缩略图](images/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> ![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| ![参阅包含其他语言版本的页面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多语言](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | 此 IT 海报介绍了业务决策者和解决方案架构师需要了解的 SharePoint Online、Microsoft Azure 和 SharePoint 本地配置。 <br/><br/> - **SharePoint Online (SaaS)** -通过软件即服务 (SaaS) 订阅模型使用 SharePoint。 <br/> - **SharePoint 混合**-将您的 SharePoint 网站和应用程序移到云以自己的速度。 <br/> - **在 Azure (IaaS) 的 SharePoint**的扩展 Microsoft Azure 到内部部署环境并那里部署 SharePoint 2016 服务器。（这被推荐的高可用性/灾难恢复和开发/测试环境。）<br/> - **SharePoint 场所**的规划、 部署、 维护和自定义 SharePoint 环境中维护您的数据中心。 <br/> |
   
### <a name="multi-geo-preview-for-onedrive-in-office-365"></a>Office 365 中的 OneDrive 的多地区预览
<a name="MultiGeoO365ODB"> </a>

|**项目**|**说明**|
|:-----|:-----|
|[![Office 365 模型中的多个地区 OneDrive](images/c6c1b7cd-7833-46fb-9eec-c12150c260d9.png)          ](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.pdf) <br/> ![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.pdf)  \| ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.vsdx) <br/> | 此海报是 Office 365，目前在预览中的多个地区 OneDrive 的一页概述。此模型包括：<br/><br/> 福利 <br/> -部署步骤 <br/> -配置示例 <br/><br/>  Office 365 中的 OneDrive 为多地区预览的详细信息，请单击[此处](https://aka.ms/onedrivemultigeo)。  <br/> |
   
### <a name="sharepoint-server-2016-databases"></a>SharePoint Server 2016 数据库
<a name="SP2016_Databases"> </a>

|**项目**|**说明**|
|:-----|:-----|
|[![SharePoint 服务器 2016年数据库海报的缩略图](images/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> ![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| ![参阅包含其他语言版本的页面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多语言](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | 此 IT 海报是 SharePoint Server 2016 数据库的快速参考指南。每个数据库都包含以下详细信息：<br/><br/> 大小 <br/> 调整指南 <br/> -I/O 模式 <br/> -要求 <br/><br/>  第一页包含 SharePoint 系统数据库和服务应用程序有多个数据库。第二页显示所有具有单个数据库的服务应用程序。<br/><br/>  有关 SharePoint 服务器 2016年数据库的详细信息，请参阅[数据库类型和说明在 SharePoint 服务器 2016](https://technet.microsoft.com/en-us/library/cc678868%28v=office.16%29.aspx) <br/> |
   
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Microsoft Skype for Business 2015 体系结构模型
<a name="SfB2015_ArchModel"> </a>

|**项目**|**说明**|
|:-----|:-----|
|[![业务体系结构模型海报为 Skype 的缩略图](images/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022) <br/> ![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| ![参阅包含其他语言版本的页面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多语言](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |本宣传海报介绍 Skype 业务在线的、 内部、 混合、 云 PBX，以及 Exchange 和 SharePoint 配置与的集成的业务决策制定者和解决方案架构师需要了解。 <br/><br/> 这被专为 IT 专业人员观众意识到通过 Skype 的在线业务，为企业内部部署 Skype 可消耗的不同基本体系结构模型。 <br/><br/>首先取决于哪种配置最适合您组织的需要和将来的计划。考虑，并根据需要使用其他人。例如，您可能需要考虑与 Exchange 和 SharePoint 或一个解决方案，它利用微软云 PBX 解决方案的集成。  <br/> |
   
## <a name="platform-options-posters"></a>平台选项海报

这些 SharePoint 2013、Exchange 2013 和 Lync 2013 的 IT 海报以大型海报形式提供了一种总体比较各种部署方法的方式。每张海报都提供了所有配置或平台的可用选项列表，并针对每个选项提供了以下信息：
  
- **概述**平台，包括概念图的简要总结。
    
- **最适用于**最适合于特定平台的常见方案。
    
- **许可证要求**部署所需的许可证。
    
- **体系结构的任务**作为架构师，您需要决定。
    
- **IT 专业人员的任务或职责**您的 IT 员工需要规划日常职责。
    
## <a name="sharepoint-2013-platform-options"></a>SharePoint 2013 平台选项
<a name="SP2013_Options"> </a>

****

|**项目**|**说明**|
|:-----|:-----|
|[![缩略图图像的 SharePoint 2013 平台选项](images/SP_PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332) <br/> ![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](http://go.microsoft.com/fwlink/p/?LinkId=324594)  \| ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| ![参阅包含其他语言版本的页面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多语言](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |为业务决策人员 (Bdm) 和架构师，此模型说明了 SharePoint 2013，Office 365 中的内部混合使用 Office 365、 Azure 和内部只部署 SharePoint 的平台选项。它包括概述每个体系结构、 建议、 许可的要求，以及架构师和 IT 专业人员为每个平台的任务的列表。在 Azure 上的多个 SharePoint 解决方案会突出显示。<br/><br/>本宣传海报的辅助功能的文本版本，请参阅[访问关系图-Microsoft SharePoint 2013 平台选项](accessible-diagrammicrosoft-sharepoint-2013-platform-options.md)。  <br/> |
   
## <a name="exchange-2013-platform-options"></a>Exchange 2013 平台选项
<a name="Exch2013_options"> </a>

****

|**项目**|**说明**|
|:-----|:-----|
|[![缩略图图像的交换平台选项](images/ITPro_Other_Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> ![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| ![参阅包含其他语言版本的页面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多语言](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |Bdm 和架构师，此模型描述 Exchange 2013 的可用平台选项。客户可以选择从 Exchange 联机，使用 Office 365，混合交换，部署 Exchange Server 和承载 Exchange。海报包括详细信息体系结构的每个选项，每个、 许可证要求和 IT 专业人员的职责包括最理想的方案。<br/><br/>本宣传海报的辅助功能的文本版本，请参阅[访问关系图-Microsoft Exchange 2013 平台选项](accessible-diagrammicrosoft-exchange-2013-platform-options.md)。  <br/> |
   
## <a name="lync-2013-platform-options"></a>Lync 2013 平台选项
<a name="Lync2013_Options"> </a>

****

|**项目**|**说明**|
|:-----|:-----|
|[![Lync 平台选项的缩略图](images/Lync_PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> ![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| ![参阅包含其他语言版本的页面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多语言](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |此模型面向 BDM 和架构师，说明了 Lync 2013 的可用平台选项。客户可以从使用 Office 365 的 Lync Online、混合 Lync、Lync Server 内部部署和托管 Lync 中进行选择。此 IT 海报包括每个体系结构选项的详细信息，包括每个选项最理想的方案、许可要求和 IT 专业人员的职责。  <br/> |
   
## <a name="sharepoint-in-azure-solutions-posters"></a>在 Azure 解决方案海报中的 SharePoint
<a name="Lync2013_Options"> </a>

这些 IT 海报展示大型海报格式使用 SharePoint Server 2013 的基于 Azure 的解决方案。
  
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点
<a name="Azure_sharepoint2013"> </a>

****

|**项目**|**说明**|
|:-----|:-----|
|[![使用 SharePoint 的 Azure 中的 Internet 网站图像](images/MS_AZ_SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> ![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| ![参阅包含其他语言版本的页面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多语言](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |本宣传海报简要介绍了设计的关键活动，并建议 Azure 中的面向 Internet 站点的体系结构选择。本宣传海报的辅助功能的文本版本，请参阅[访问关系图-SharePoint 2013 的 Microsoft Azure 中的 Internet 站点](accessible-diagraminternet-sites-in-microsoft-azure-for-sharepoint-2013.md)。<br/><br/> 有关详细信息，请参阅下列文章：  <br/><br/> - [在使用 SharePoint Server 2013 Microsoft Azure 中的 Internet 站点](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 的 Microsoft Azure 结构](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>设计示例：Microsoft Azure 中的 SharePoint 2013 Internet 站点
<a name="DesignSampleInternetSites"> </a>

****

|**项目**|**说明**|
|:-----|:-----|
|[![设计示例图：Microsoft Azure for SharePoint 2013 中的 Internet 站点](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> ![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| ![参阅包含其他语言版本的页面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多语言](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |此设计示例作为起始点用于在使用 SharePoint Server 2013 Azure 中自己体系结构面向 Internet 的网站。本宣传海报的辅助功能的文本版本，请参阅[访问关系图-设计示例： 在 SharePoint 2013 的 Microsoft Azure 中的互联网网站](accessible-diagramdesign-sample-internet-sites-in-microsoft-azure-for-sharepoint.md)。<br/><br/> 有关详细信息，请参阅下列文章：  <br/><br/> - [在使用 SharePoint Server 2013 Microsoft Azure 中的 Internet 站点](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 的 Microsoft Azure 结构](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>SharePoint 灾难恢复到 Microsoft Azure
<a name="sharepoint_recovery_Azure"> </a>

****

|**项目**|**说明**|
|:-----|:-----|
|[![SharePoint 到 Azure 的灾难恢复过程](images/SP_DR_Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> ![PDF 文件](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| ![Visio 文件](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| ![参阅包含其他语言版本的页面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多语言](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |此 IT 标牌说明了 Azure 中的灾难恢复环境的体系结构原则。本宣传海报的辅助功能的文本版本，请参阅[访问关系图-到 Microsoft Azure 的 SharePoint 灾难恢复](accessible-diagramsharepoint-disaster-recovery-to-microsoft-azure.md)。<br/><br/> 有关详细信息，请参阅下列文章：  <br/><br/> - [在 Microsoft Azure 中的 SharePoint 服务器 2013年灾难恢复](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [SharePoint 2013 的 Microsoft Azure 结构](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
## <a name="see-also"></a>概念

<a name="Lync2013_Options"> </a>

[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
  
[云应用测试实验室指南 (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)
  
[混合解决方案](hybrid-solutions.md)




