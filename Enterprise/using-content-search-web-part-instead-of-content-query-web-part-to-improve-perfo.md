---
title: 使用内容搜索 Web 部件而不是内容查询 Web 部件来提高 SharePoint Online 中的性能
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: 本文介绍如何通过将内容查询 Web 部件替换为 SharePoint Server 2013 和 SharePoint Online 中的内容搜索 Web 部件来提高性能。
ms.openlocfilehash: 590cd5f60dedf870d58d053b01e4e1b45469bfa4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070548"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>使用内容搜索 Web 部件而不是内容查询 Web 部件来提高 SharePoint Online 中的性能

本文介绍如何通过将内容查询 Web 部件替换为 SharePoint Server 2013 和 SharePoint Online 中的内容搜索 Web 部件来提高性能。
  
SharePoint Server 2013 和 SharePoint Online 的最强大的新增功能之一是内容搜索 Web 部件 (CSWP)。 此 Web 部件使用搜索索引快速检索向用户显示的结果。 使用内容搜索 Web 部件, 而不是页面中的内容查询 Web 部件 (CQWP) 来提高用户的性能。
  
在内容查询 Web 部件上使用内容搜索 Web 部件几乎总是能够在 SharePoint Online 上显著提高页面加载性能。 有一些额外的配置可实现正确的查询, 但回报的性能和用户感到高兴更高。
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>比较从使用内容搜索 Web 部件 (而不是内容查询 Web 部件) 获取的性能增益

下面的示例展示了使用内容搜索 Web 部件而不是内容查询 Web 部件时可能会收到的相对性能收益。 复杂的网站结构和非常广泛的内容查询效果更明显。
  
此示例网站具有以下特征:
  
- 8个子网站级别。
    
- 使用自定义 "水果" 内容类型的列表。
    
- 在 Web 部件中, 内容查询是广泛的, 返回内容类型为 "水果" 的所有项目。
    
- 该示例仅在8个网站中使用50个项目。 对于包含更多内容的网站, 效果会更明显。
    
下面是内容查询 Web 部件的结果的屏幕截图。
  
![显示 Web 部件的内容查询的图形](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
在 Internet Explorer 中, 使用 F12 开发人员工具的 "**网络**" 选项卡查看响应标头的详细信息。 在下面的屏幕截图中, 此页面加载的**SPRequestDuration**的值为924毫秒。 
  
![显示请求持续时间为 924 的屏幕截图](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration**指示在服务器上完成的准备页面的工作量。 通过查询 Web 部件切换内容通过搜索 Web 部件的内容, 可以大大减少呈现页面所需的时间。 相比之下, 具有等效内容搜索 Web 部件的页面, 返回相同数量的结果的**SPRequestDuration**值为106毫秒, 如以下屏幕截图所示: 
  
![显示请求持续时间为 106 的屏幕截图](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>在 SharePoint Online 中添加内容搜索 Web 部件

添加内容搜索 Web 部件与常规内容查询 Web 部件非常相似。 请参阅在[SharePoint 中配置内容搜索 Web 部件](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)中的 *"添加内容搜索 web 部件"* 一节。
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>为内容搜索 Web 部件创建正确的搜索查询

添加内容搜索 Web 部件后, 可以优化搜索并返回所需的项目。 有关如何执行此操作的详细说明, 请参阅在[SharePoint 中配置内容搜索 Web 部件](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)中的 *"通过在内容搜索 web 部件中配置高级查询来显示内容"* 一节。
  
## <a name="query-building-and-testing-tool"></a>查询生成和测试工具

有关生成和测试复杂查询的工具, 请参阅 Codeplex 上的[搜索查询工具](https://sp2013searchtool.codeplex.com/)。 
  

