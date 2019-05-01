---
title: 可访问的图 - 内部部署电子数据展示流程
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
description: 本文是名为“本地电子数据展示流程”的图的可访问文本版本。
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487697"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>可访问的图 - 内部部署电子数据展示流程

**摘要:** 本文是名为本地电子数据展示流的图表的可访问文本版本。
  
此海报提供了关于跨服务器产品的体系结构和数据流的详细信息。 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>跨 SharePoint、Exchange、Lync 和文件共享

该图显示了一个用户, 该用户发送的查询可访问两个服务器场、一个 sharepoint 2013 企业应用程序场和一个 sharepoint 2013 服务场。 sharepoint 2013 服务场与 sharepoint 2013 内容场进行通信, Exchange Server 2013 (与 Lync 2013 通信) 和 Windows 文件共享。 
  
电子数据展示流程列表介绍了数据流以及电子数据展示查询操作跨 SharePoint、Exchange、Lync 和文件共享发生的顺序。  
  
首先详细介绍了电子数据展示流程列表，后面详细介绍了图中所示的功能。  
  
### <a name="ediscovery-flow-list"></a>电子数据展示流程列表

此列表中所述的每个步骤的编号与图中所示的步骤对应。本文档后面会详细地介绍此图。  
  
1. 在电子数据展示中心 (EDC) 中创建、管理和使用电子数据展示案例。 EDC 是 SharePoint 2013 网站集。 这是定义案例、识别要跟踪的源、发布查询、查看查询结果及放置或删除保留内容的地方。 
    
2. 电子数据展示查询或操作（如 Hold、ReleaseHold 或 GetStatus）在企业应用程序场中从 EDC 中继到 Search Service 应用程序 (SSA) 代理。 然后，SSA 代理将通信中继到服务应用程序场中的 SSA。 在此示例中, 请求将所有内容放在 SharePoint 内容场中, 保留文件名中的 "CONTOSO"。 
    
3. 如果请求是查询案例，则 SSA 会参考搜索索引。然后，通过 EDC 将电子数据展示查询结果集返回给用户。  
    
4. 如果请求是一个操作，如 Hold 或 ReleaseHold，则将该操作写入 SSA 管理数据库中的 Actions_Table。 在此示例中, 将 "CONTOSO" 的 SharePoint 内容场中的任何内容的保留请求写入 Actions_Table 中。 
    
5. 内容场电子数据展示就地保留计时器作业将定期唤醒并生成挂起操作的请求，且将状态更新通过 SSA 代理发送至 SSA。 
    
6. 将挂起操作的查询中继到中心 SSA，该中心 SSA 将参考内容场所有挂起操作的 Action_Table。 内容场就地保留计时器作业还将发送其收到的对象和操作的状态更新，这些内容都写入到 ActionsTable。 
    
7. 将 SharePoint 2013 内容场中名称为 "CONTOSO" 的任何内容的保留请求由 SSA 发送到内容服务器场中的电子数据展示就地保留计时器作业。 
    
8. 电子数据展示就地保留计时器作业将 "contoso Site" 和 "contoso content" 置于保留状态。 
    
9. 电子数据展示就地保留计时器作业将定期在企业应用程序场中运行，以检查发现操作的状态，并更新状态。  
    
10. 状态查询通过企业应用程序场 SSA 代理中继到 SharePoint Services 场 SSA。  
    
11. SSA 检索 Actions 表中的状态，并将其返回到将状态更新推送到 EDC 的企业应用程序场中的计时器作业。 
    
12. 电子数据展示用户在搜索 Exchange 源（如邮箱或存档的 Lync 内容）或对其执行某个操作时，中心 SSA 将使用 Exchange Web 服务 (EWS) 代理查询 Exchange Web 服务。 Exchange 具有其自身的搜索和电子数据展示基础结构，并管理内部所有的电子数据展示通话。 
    
13. Exchange Web 服务将电子数据展示搜索结果响应给 SSA，或将基于查询的保留的状态请求响应给 SSA，而这又将中继到 EDC。  
    
#### <a name="prerequisites"></a>先决条件

- 必须配置 SharePoint 企业级搜索，内容源（SharePoint 和 Windows 文件共享）上的搜索爬网将成功且所有内容源都在索引中。  
    
- 必须在 SharePoint Services 场和 Exchange 之间，以及 Exchange 和 Lync 之间配置服务器间信任和身份验证。  
    
### <a name="description-of-components-in-the-diagram"></a>图中所示组件的说明

该图显示了一个用户发送查询, 该查询可访问两个服务器场、一个 sharepoint 2013 企业应用程序场和一个 sharepoint 2013 服务场。 sharepoint Services 场与 sharepoint 2013 内容场的接口, Exchange Server 2013 (与 Lync 2013 的接口) 和 Windows 文件共享。 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>SharePoint 2013 企业应用程序场

SharePoint 2013 企业版应用程序场包含以下组件: 
  
- EDC
    
- SSA 代理  
    
- 计时器作业 
    
用户在企业应用程序场中发送到 EDC 的查询或操作。将发生下列操作：  
  
- 查询或操作发送到 SSA 代理。  
    
- SSA 代理向企业应用程序场中的计时器作业发送状态查询或响应，它还会向 SharePoint 服务场中的 SSA 服务发送状态查询或响应。关于 SharePoint 服务场的一节中介绍了由此产生的操作。  
    
- 当计时器作业接收到响应时，将把响应发送到 SSA 代理，然后发送到 EDC。  
    
- 查询或操作的任何结果将发送到 EDC 中的用户。  
    
#### <a name="sharepoint-2013-services-farm"></a>SharePoint 2013 服务场

SharePoint 2013 服务场包含以下组件: 
  
- SSA 服务  
    
- 搜索索引数据库 
    
- SSA admin_db 数据库。 此数据库中的操作表包含： 保留释放保留 GetStatus 
    
- EWS 代理  
    
当 SharePoint 企业应用程序场中的 SSA 代理向 SharePoint 服务场中的 SSA 发送状态查询时，将发生以下操作：  
  
- 如果请求是查询，则 SSA 会参考搜索索引。发现响应会返回到 SSA，然后通过 EDC 发送给用户。  
    
- 如果请求是写入操作，SSA 服务将把写入操作发送到 SSA admin_db。  
    
- 爬网和响应结果请求将从 SSA 发送到 SharePoint 2013 内容场, 并向 SSA 返回响应。 
    
- 爬网和相应的结果请求将从 SSA 发送到 Windows 文件共享，响应将返回到 SSA。  
    
- 对未完成操作、响应或状态更新的查询将从 SSA 发送到 SharePoint 内容场中的 SSA 代理，响应将返回到 SSA。  
    
- Exchange 操作/状态请求从 SSA 发送到 EWS 代理，这会将 Exchange 查询操作/状态请求发送到 Exchange 2013 服务器上的 Exchange Web 服务中。   
    
- 状态查询/响应从 SSA 发送到 SSA admin_db，并返回到 SSA。  
    
- 未完成操作查询/响应从 SSA 发送到 SSA admin_db，并返回到 SSA。  
    
#### <a name="sharepoint-2013-content-farm"></a>SharePoint 2013 内容场

SharePoint 2013 内容场包含以下组件: 
  
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
  
- 服务器到服务器信任/OAuth 在 SharePoint 2013 内容场和 Exchange 2013 之间进行处理。 
    
- 服务器到服务器信任/OAuth 在 Exchange 2013 和 Lync 2013 之间处理。  
    
#### <a name="lync-2013"></a>Lync 2013

Lync 2013 组件将 Lync 内容归档在 Exchange 2013 中。  
  
#### <a name="windows-file-shares"></a>Windows 文件共享

Windows 文件共享组件提供对 SharePoint 服务场中 SSA 的爬网结果。  
  
### <a name="legend"></a>Legend

此图的图例以图形的形式显示不同组件之间不同类型的通信，如图中不同颜色的线条所示：  
  
- 浅蓝色线条: 查询/操作-电子数据展示查询或操作数据 
    
- 橙色线条: 展示响应-电子数据展示查询响应数据 
    
- 绿线: 状态查询/响应-电子数据展示状态查询/响应数据 
    
- 紫色线条: exchange 操作/状态请求-针对 Exchange 流量的操作状态的电子数据展示请求。 
    
- 红线: exchange 数据/状态响应-来自 Exchange 的电子数据展示查询或状态响应。 
    
- 黑色虚线：服务器到服务器信任/OAuth  
    
- 黑色实线：爬网/结果  
    

