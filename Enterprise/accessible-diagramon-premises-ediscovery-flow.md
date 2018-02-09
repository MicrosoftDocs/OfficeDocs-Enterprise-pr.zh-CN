---
title: "可访问的图 - 内部部署电子数据展示流程"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "本文是名为“本地电子数据展示流程”的图的可访问文本版本。"
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>可访问的图 - 内部部署电子数据展示流程

**摘要：**这篇文章是名为内部 eDiscovery 流图的辅助功能的文本版本。
  
此海报提供了关于跨服务器产品的体系结构和数据流的详细信息。 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>跨 SharePoint、Exchange、Lync 和文件共享

该图显示用户发送访问两个服务器场、 SharePoint 2013 企业应用程序服务器场，以及 SharePoint 2013 服务场的查询。SharePoint 2013 服务场与 SharePoint 2013 内容场，Exchange Server 2013 （这与 Lync 2013），以及 Windows 文件共享。 
  
电子数据展示流程列表介绍了数据流以及电子数据展示查询操作跨 SharePoint、Exchange、Lync 和文件共享发生的顺序。  
  
首先详细介绍了电子数据展示流程列表，后面详细介绍了图中所示的功能。  
  
### <a name="ediscovery-flow-list"></a>电子数据展示流程列表

此列表中所述的每个步骤的编号与图中所示的步骤对应。本文档后面会详细地介绍此图。  
  
1. eDiscovery 情况下创建、 管理、 和 eDiscovery 中心 (EDC) 中使用。EDC 是 SharePoint 2013 网站集。这是在其中定义用例、 标识源进行跟踪、 发出查询、 查询结果被审核，和放置或删除内容的保留。 
    
2. EDiscovery 查询或操作，如保留、 ReleaseHold，或者 GetStatus，被转给从 EDC 在企业应用程序服务器场搜索服务应用程序 (SSA) 代理。SSA 代理然后将中继到该服务的应用程序服务器场中的 SSA 的通信。在此示例中，该请求是"CONTOSO"SharePoint 内容群中放置任何内容候文件名中。 
    
3. 如果请求是查询案例，则 SSA 会参考搜索索引。然后，通过 EDC 将电子数据展示查询结果集返回给用户。  
    
4. 如果该请求的操作，例如位置保留或 ReleaseHold，则该操作写入 SSA 管理数据库中的 Actions_Table。在此示例中，与"CONTOSO"SharePoint 内容服务器场中的所有内容的保留请求写入 Actions_Table。 
    
5. 内容场电子数据展示就地保留计时器作业将定期唤醒并生成挂起操作的请求，且将状态更新通过 SSA 代理发送至 SSA。  
    
6. 挂起操作的查询被中继到中央 SSA，向 Action_Table 咨询所有挂起的操作内容的场。内容服务器场就地封存计时器作业也会发送状态更新的对象和操作已收到，该写入到 ActionsTable。 
    
7. 与"CONTOSO"SharePoint 2013 内容服务器场中的名称中的任何内容为挂起的请求是由 SSA 发送到内容服务器场中的 eDiscovery 就地封存计时器作业。 
    
8. EDiscovery 就地保存计时器作业"CONTOSO 网站"和"CONTOSO 内容"上的保存的位置。 
    
9. 电子数据展示就地保留计时器作业将定期在企业应用程序场中运行，以检查发现操作的状态，并更新状态。  
    
10. 状态查询通过企业应用程序场 SSA 代理中继到 SharePoint Services 场 SSA。  
    
11. SSA 检索 Actions 表中的状态，并将其返回到将状态更新推送到 EDC 的企业应用程序场中的计时器作业。  
    
12. 当 eDiscovery 用户搜索 （或执行某一动作） 对于交换源，例如邮箱或归档的 Lync 内容，中央 SSA 使用查询 Web 服务交换的交换 Web 服务 (EWS) 代理。Exchange 已自己搜索和 eDiscovery 的基础结构和内部管理 eDiscovery 的所有调用。 
    
13. Exchange Web 服务将电子数据展示搜索结果响应给 SSA，或将基于查询的保留的状态请求响应给 SSA，而这又将中继到 EDC。  
    
#### <a name="prerequisites"></a>先决条件

- 必须配置 SharePoint 企业级搜索，内容源（SharePoint 和 Windows 文件共享）上的搜索爬网将成功且所有内容源都在索引中。  
    
- 必须在 SharePoint Services 场和 Exchange 之间，以及 Exchange 和 Lync 之间配置服务器间信任和身份验证。  
    
### <a name="description-of-components-in-the-diagram"></a>图中所示组件的说明

该图显示用户发送一个查询，它访问 SharePoint 2013 企业应用程序服务器场和 SharePoint 2013 服务场的两个服务器场。SharePoint Services 场与 SharePoint 2013 内容场，Exchange Server 2013 （哪些接口使用 Lync 2013），接口和 Windows 文件共享。 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>SharePoint 2013 企业应用程序服务器场

SharePoint 服务器场 2013年企业应用程序包含以下组件： 
  
- EDC
    
- SSA 代理  
    
- 计时器作业 
    
用户在企业应用程序场中发送到 EDC 的查询或操作。将发生下列操作：  
  
- 查询或操作发送到 SSA 代理。  
    
- SSA 代理向企业应用程序场中的计时器作业发送状态查询或响应，它还会向 SharePoint 服务场中的 SSA 服务发送状态查询或响应。关于 SharePoint 服务场的一节中介绍了由此产生的操作。  
    
- 当计时器作业接收到响应时，将把响应发送到 SSA 代理，然后发送到 EDC。  
    
- 查询或操作的任何结果将发送到 EDC 中的用户。  
    
#### <a name="sharepoint-2013-services-farm"></a>SharePoint 2013 服务群

SharePoint 2013 服务场包含以下组件： 
  
- SSA 服务  
    
- 搜索索引数据库  
    
- SSA admin_db 数据库。此数据库中的操作表包含： 容纳 GetStatus 保存版本 
    
- EWS 代理  
    
当 SharePoint 企业应用程序场中的 SSA 代理向 SharePoint 服务场中的 SSA 发送状态查询时，将发生以下操作：  
  
- 如果请求是查询，则 SSA 会参考搜索索引。发现响应会返回到 SSA，然后通过 EDC 发送给用户。  
    
- 如果请求是写入操作，SSA 服务将把写入操作发送到 SSA admin_db。  
    
- 爬网和响应结果请求发给 SSA 从 SharePoint 2013 内容场和 SSA 与返回的响应。 
    
- 爬网和相应的结果请求将从 SSA 发送到 Windows 文件共享，响应将返回到 SSA。  
    
- 对未完成操作、响应或状态更新的查询将从 SSA 发送到 SharePoint 内容场中的 SSA 代理，响应将返回到 SSA。  
    
- Exchange 操作/状态请求从 SSA 发送到 EWS 代理，这会将 Exchange 查询操作/状态请求发送到 Exchange 2013 服务器上的 Exchange Web 服务中。   
    
- 状态查询/响应从 SSA 发送到 SSA admin_db，并返回到 SSA。  
    
- 未完成操作查询/响应从 SSA 发送到 SSA admin_db，并返回到 SSA。  
    
#### <a name="sharepoint-2013-content-farm"></a>SharePoint 2013 内容服务器场

SharePoint 2013 内容场包含以下组件： 
  
- SSA 代理  
    
- 计时器作业 
    
- Contoso SharePoint 网站  
    
- Contoso SharePoint 内容  
    
当 SharePoint 服务场中的 SSA 向 SharePoint 内容场中的 SSA 代理发送状态查询时，将发生以下操作：  
  
- SharePoint 内容场中的 SSA 代理向计时器作业发送未完成操作/状态响应的查询。  
    
- 计时器作业向 Contoso SharePoint 网站发送一个检查 Contoso SharePoint 内容的请求。  
    
- 对未完成操作/状态查询的响应从计时器作业发送到 SharePoint 内容场中的 SSA 代理，然后发送到 SharePoint 服务场中的 SSA 服务。  
    
#### <a name="exchange-2013"></a>Exchange 2013

Exchange 2013 服务器组件包含 Exchange Web 服务并提供以下功能：  
  
- 服务器到服务器信任/OAuth SharePoint 2013 内容场和 Exchange 2013 之间处理。 
    
- 服务器到服务器信任/OAuth 在 Exchange 2013 和 Lync 2013 之间处理。  
    
#### <a name="lync-2013"></a>Lync 2013

Lync 2013 组件将 Lync 内容归档在 Exchange 2013 中。  
  
#### <a name="windows-file-shares"></a>Windows 文件共享

Windows 文件共享组件提供对 SharePoint 服务场中 SSA 的爬网结果。  
  
### <a name="legend"></a>图例

此图的图例以图形的形式显示不同组件之间不同类型的通信，如图中不同颜色的线条所示：  
  
- 亮蓝线： 查询/操作的 eDiscovery 查询或操作数据 
    
- 橙色的线： eDisovery 响应-eDiscovery 查询响应数据 
    
- 绿色线： 状态查询/响应的 eDiscovery 状态查询/响应数据 
    
- 紫色线条： 交换行动中的状态请求-eDiscovery 请求交换通信的操作状态。 
    
- 红线： 交换数据/状态响应-从交换 eDiscovery 查询或状态响应。 
    
- 黑色虚线：服务器到服务器信任/OAuth  
    
- 黑色实线：爬网/结果  
    

