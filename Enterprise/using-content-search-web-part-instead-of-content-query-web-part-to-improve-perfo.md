---
title: 使用内容搜索 Web 部件而不内容查询 Web 部件在 SharePoint Online 中提高性能
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: 本文介绍如何通过将 SharePoint Server 2013 和 SharePoint Online 中的内容搜索 Web 部件替换为内容查询 Web 部件来提高性能。
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539851"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>使用内容搜索 Web 部件而不内容查询 Web 部件在 SharePoint Online 中提高性能

本文介绍如何通过将 SharePoint Server 2013 和 SharePoint Online 中的内容搜索 Web 部件替换为内容查询 Web 部件来提高性能。
  
SharePoint Server 2013 和 SharePoint Online 的最强大的新功能之一是内容搜索 Web 部件 (CSWP)。此 Web 部件使用搜索索引来快速检索其向用户显示的结果。使用内容搜索 Web 部件而不是内容查询 Web 部件 (CQWP) 在页面中来提高您的用户的性能。
  
通过内容查询 Web 部件中使用内容搜索 Web 部件始终将导致在 SharePoint Online 的长足页面加载性能。没有很少的其他配置，以获取正确的查询，但奖励提高的性能和 happier 用户。
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>比较获得而不内容查询 Web 部件中使用内容搜索 Web 部件的性能提升

下面的示例演示当您使用而不是为内容查询 Web 部件的内容搜索 Web 部件时可能会收到相对的性能提升。效果是更复杂的网站结构和非常广泛的内容查询明显。
  
此示例网站具有以下特征：
  
- 8 级别的子网站。
    
- 列出了使用自定义"果"内容类型。
    
- 在 Web 部件中，内容查询是广泛，返回与"果"的内容类型的所有项。
    
- 该示例仅 8 网站之间使用 50 个项。效果将会更多明显网站具有更多的内容。
    
下面是结果的内容查询 Web 部件的屏幕截图。
  
![显示 Web 部件的内容查询的图形](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
在 Internet Explorer 中，使用 F12 开发人员工具的**网络**选项卡查看在响应标头的详细信息。以下屏幕截图中, **SPRequestDuration**此页面负载的值为 924 毫秒。 
  
![显示请求持续时间为 924 的屏幕截图](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration**指示准备页面在服务器上完成的工时量。显著切换内容搜索 Web 部件内容查询 Web 部件可减少呈现页面的时间。相比之下，与等效的内容搜索 Web 部件页，返回相同的结果数其**SPRequestDuration**值的 106 毫秒此屏幕截图中所示： 
  
![显示请求持续时间为 106 的屏幕截图](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>在 SharePoint Online 添加内容搜索 Web 部件

添加内容搜索 Web 部件是非常类似于普通的内容查询 Web 部件。请参阅部分中[配置内容搜索 Web 部件在 SharePoint 中](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)的 *"添加内容搜索 Web 部件"* 。
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>创建内容搜索 Web 部件右侧的搜索查询

添加内容搜索 Web 部件后，您可以优化搜索，并返回所需的项目。有关如何执行此操作的详细说明，请参阅部分，在[配置内容搜索 Web 部件在 SharePoint 中](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)的 *"通过配置高级的查询内容搜索 Web 部件中显示内容"* 。
  
## <a name="query-building-and-testing-tool"></a>查询构建和测试工具

用于生成和测试复杂查询的工具，请参阅 Codeplex 上的[搜索查询工具](https://sp2013searchtool.codeplex.com/)。 
  

