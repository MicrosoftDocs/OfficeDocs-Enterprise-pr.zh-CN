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
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="09c8e-103">可访问的图 - 内部部署电子数据展示流程</span><span class="sxs-lookup"><span data-stu-id="09c8e-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="09c8e-104">**摘要：**这篇文章是名为内部 eDiscovery 流图的辅助功能的文本版本。</span><span class="sxs-lookup"><span data-stu-id="09c8e-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="09c8e-105">此海报提供了关于跨服务器产品的体系结构和数据流的详细信息。</span><span class="sxs-lookup"><span data-stu-id="09c8e-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="09c8e-106">跨 SharePoint、Exchange、Lync 和文件共享</span><span class="sxs-lookup"><span data-stu-id="09c8e-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="09c8e-p101">该图显示用户发送访问两个服务器场、 SharePoint 2013 企业应用程序服务器场，以及 SharePoint 2013 服务场的查询。SharePoint 2013 服务场与 SharePoint 2013 内容场，Exchange Server 2013 （这与 Lync 2013），以及 Windows 文件共享。</span><span class="sxs-lookup"><span data-stu-id="09c8e-p101">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm. The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="09c8e-109">电子数据展示流程列表介绍了数据流以及电子数据展示查询操作跨 SharePoint、Exchange、Lync 和文件共享发生的顺序。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="09c8e-110">首先详细介绍了电子数据展示流程列表，后面详细介绍了图中所示的功能。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="09c8e-111">电子数据展示流程列表</span><span class="sxs-lookup"><span data-stu-id="09c8e-111">eDiscovery Flow List</span></span>

<span data-ttu-id="09c8e-p102">此列表中所述的每个步骤的编号与图中所示的步骤对应。本文档后面会详细地介绍此图。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="09c8e-p103">eDiscovery 情况下创建、 管理、 和 eDiscovery 中心 (EDC) 中使用。EDC 是 SharePoint 2013 网站集。这是在其中定义用例、 标识源进行跟踪、 发出查询、 查询结果被审核，和放置或删除内容的保留。</span><span class="sxs-lookup"><span data-stu-id="09c8e-p103">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC). The EDC is a SharePoint 2013 site collection. This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="09c8e-p104">EDiscovery 查询或操作，如保留、 ReleaseHold，或者 GetStatus，被转给从 EDC 在企业应用程序服务器场搜索服务应用程序 (SSA) 代理。SSA 代理然后将中继到该服务的应用程序服务器场中的 SSA 的通信。在此示例中，该请求是"CONTOSO"SharePoint 内容群中放置任何内容候文件名中。</span><span class="sxs-lookup"><span data-stu-id="09c8e-p104">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm. The SSA proxy then relays the traffic to the SSA in the Services App Farm. In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="09c8e-p105">如果请求是查询案例，则 SSA 会参考搜索索引。然后，通过 EDC 将电子数据展示查询结果集返回给用户。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="09c8e-p106">如果该请求的操作，例如位置保留或 ReleaseHold，则该操作写入 SSA 管理数据库中的 Actions_Table。在此示例中，与"CONTOSO"SharePoint 内容服务器场中的所有内容的保留请求写入 Actions_Table。</span><span class="sxs-lookup"><span data-stu-id="09c8e-p106">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database. In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="09c8e-124">内容场电子数据展示就地保留计时器作业将定期唤醒并生成挂起操作的请求，且将状态更新通过 SSA 代理发送至 SSA。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="09c8e-p107">挂起操作的查询被中继到中央 SSA，向 Action_Table 咨询所有挂起的操作内容的场。内容服务器场就地封存计时器作业也会发送状态更新的对象和操作已收到，该写入到 ActionsTable。</span><span class="sxs-lookup"><span data-stu-id="09c8e-p107">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm. The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="09c8e-127">与"CONTOSO"SharePoint 2013 内容服务器场中的名称中的任何内容为挂起的请求是由 SSA 发送到内容服务器场中的 eDiscovery 就地封存计时器作业。</span><span class="sxs-lookup"><span data-stu-id="09c8e-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="09c8e-128">EDiscovery 就地保存计时器作业"CONTOSO 网站"和"CONTOSO 内容"上的保存的位置。</span><span class="sxs-lookup"><span data-stu-id="09c8e-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="09c8e-129">电子数据展示就地保留计时器作业将定期在企业应用程序场中运行，以检查发现操作的状态，并更新状态。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="09c8e-130">状态查询通过企业应用程序场 SSA 代理中继到 SharePoint Services 场 SSA。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="09c8e-131">SSA 检索 Actions 表中的状态，并将其返回到将状态更新推送到 EDC 的企业应用程序场中的计时器作业。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="09c8e-p108">当 eDiscovery 用户搜索 （或执行某一动作） 对于交换源，例如邮箱或归档的 Lync 内容，中央 SSA 使用查询 Web 服务交换的交换 Web 服务 (EWS) 代理。Exchange 已自己搜索和 eDiscovery 的基础结构和内部管理 eDiscovery 的所有调用。</span><span class="sxs-lookup"><span data-stu-id="09c8e-p108">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services. Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="09c8e-134">Exchange Web 服务将电子数据展示搜索结果响应给 SSA，或将基于查询的保留的状态请求响应给 SSA，而这又将中继到 EDC。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="09c8e-135">先决条件</span><span class="sxs-lookup"><span data-stu-id="09c8e-135">Prerequisites</span></span>

- <span data-ttu-id="09c8e-136">必须配置 SharePoint 企业级搜索，内容源（SharePoint 和 Windows 文件共享）上的搜索爬网将成功且所有内容源都在索引中。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="09c8e-137">必须在 SharePoint Services 场和 Exchange 之间，以及 Exchange 和 Lync 之间配置服务器间信任和身份验证。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="09c8e-138">图中所示组件的说明</span><span class="sxs-lookup"><span data-stu-id="09c8e-138">Description of components in the diagram</span></span>

<span data-ttu-id="09c8e-p109">该图显示用户发送一个查询，它访问 SharePoint 2013 企业应用程序服务器场和 SharePoint 2013 服务场的两个服务器场。SharePoint Services 场与 SharePoint 2013 内容场，Exchange Server 2013 （哪些接口使用 Lync 2013），接口和 Windows 文件共享。</span><span class="sxs-lookup"><span data-stu-id="09c8e-p109">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm. The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="09c8e-141">SharePoint 2013 企业应用程序服务器场</span><span class="sxs-lookup"><span data-stu-id="09c8e-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="09c8e-142">SharePoint 服务器场 2013年企业应用程序包含以下组件：</span><span class="sxs-lookup"><span data-stu-id="09c8e-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="09c8e-143">EDC</span><span class="sxs-lookup"><span data-stu-id="09c8e-143">EDC</span></span>
    
- <span data-ttu-id="09c8e-144">SSA 代理 </span><span class="sxs-lookup"><span data-stu-id="09c8e-144">SSA proxy</span></span> 
    
- <span data-ttu-id="09c8e-145">计时器作业</span><span class="sxs-lookup"><span data-stu-id="09c8e-145">Timer job</span></span> 
    
<span data-ttu-id="09c8e-p110">用户在企业应用程序场中发送到 EDC 的查询或操作。将发生下列操作： </span><span class="sxs-lookup"><span data-stu-id="09c8e-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="09c8e-148">查询或操作发送到 SSA 代理。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="09c8e-p111">SSA 代理向企业应用程序场中的计时器作业发送状态查询或响应，它还会向 SharePoint 服务场中的 SSA 服务发送状态查询或响应。关于 SharePoint 服务场的一节中介绍了由此产生的操作。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="09c8e-151">当计时器作业接收到响应时，将把响应发送到 SSA 代理，然后发送到 EDC。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="09c8e-152">查询或操作的任何结果将发送到 EDC 中的用户。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="09c8e-153">SharePoint 2013 服务群</span><span class="sxs-lookup"><span data-stu-id="09c8e-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="09c8e-154">SharePoint 2013 服务场包含以下组件：</span><span class="sxs-lookup"><span data-stu-id="09c8e-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="09c8e-155">SSA 服务 </span><span class="sxs-lookup"><span data-stu-id="09c8e-155">SSA Service</span></span> 
    
- <span data-ttu-id="09c8e-156">搜索索引数据库 </span><span class="sxs-lookup"><span data-stu-id="09c8e-156">Search index database</span></span> 
    
- <span data-ttu-id="09c8e-p112">SSA admin_db 数据库。此数据库中的操作表包含： 容纳 GetStatus 保存版本</span><span class="sxs-lookup"><span data-stu-id="09c8e-p112">SSA admin_db database. The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="09c8e-159">EWS 代理 </span><span class="sxs-lookup"><span data-stu-id="09c8e-159">EWS proxy</span></span> 
    
<span data-ttu-id="09c8e-160">当 SharePoint 企业应用程序场中的 SSA 代理向 SharePoint 服务场中的 SSA 发送状态查询时，将发生以下操作： </span><span class="sxs-lookup"><span data-stu-id="09c8e-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="09c8e-p113">如果请求是查询，则 SSA 会参考搜索索引。发现响应会返回到 SSA，然后通过 EDC 发送给用户。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="09c8e-163">如果请求是写入操作，SSA 服务将把写入操作发送到 SSA admin_db。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="09c8e-164">爬网和响应结果请求发给 SSA 从 SharePoint 2013 内容场和 SSA 与返回的响应。</span><span class="sxs-lookup"><span data-stu-id="09c8e-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="09c8e-165">爬网和相应的结果请求将从 SSA 发送到 Windows 文件共享，响应将返回到 SSA。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="09c8e-166">对未完成操作、响应或状态更新的查询将从 SSA 发送到 SharePoint 内容场中的 SSA 代理，响应将返回到 SSA。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="09c8e-167">Exchange 操作/状态请求从 SSA 发送到 EWS 代理，这会将 Exchange 查询操作/状态请求发送到 Exchange 2013 服务器上的 Exchange Web 服务中。  </span><span class="sxs-lookup"><span data-stu-id="09c8e-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="09c8e-168">状态查询/响应从 SSA 发送到 SSA admin_db，并返回到 SSA。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="09c8e-169">未完成操作查询/响应从 SSA 发送到 SSA admin_db，并返回到 SSA。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="09c8e-170">SharePoint 2013 内容服务器场</span><span class="sxs-lookup"><span data-stu-id="09c8e-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="09c8e-171">SharePoint 2013 内容场包含以下组件：</span><span class="sxs-lookup"><span data-stu-id="09c8e-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="09c8e-172">SSA 代理 </span><span class="sxs-lookup"><span data-stu-id="09c8e-172">SSA proxy</span></span> 
    
- <span data-ttu-id="09c8e-173">计时器作业</span><span class="sxs-lookup"><span data-stu-id="09c8e-173">Timer job</span></span> 
    
- <span data-ttu-id="09c8e-174">Contoso SharePoint 网站 </span><span class="sxs-lookup"><span data-stu-id="09c8e-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="09c8e-175">Contoso SharePoint 内容 </span><span class="sxs-lookup"><span data-stu-id="09c8e-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="09c8e-176">当 SharePoint 服务场中的 SSA 向 SharePoint 内容场中的 SSA 代理发送状态查询时，将发生以下操作： </span><span class="sxs-lookup"><span data-stu-id="09c8e-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="09c8e-177">SharePoint 内容场中的 SSA 代理向计时器作业发送未完成操作/状态响应的查询。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="09c8e-178">计时器作业向 Contoso SharePoint 网站发送一个检查 Contoso SharePoint 内容的请求。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="09c8e-179">对未完成操作/状态查询的响应从计时器作业发送到 SharePoint 内容场中的 SSA 代理，然后发送到 SharePoint 服务场中的 SSA 服务。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="09c8e-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="09c8e-180">Exchange 2013</span></span>

<span data-ttu-id="09c8e-181">Exchange 2013 服务器组件包含 Exchange Web 服务并提供以下功能： </span><span class="sxs-lookup"><span data-stu-id="09c8e-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="09c8e-182">服务器到服务器信任/OAuth SharePoint 2013 内容场和 Exchange 2013 之间处理。</span><span class="sxs-lookup"><span data-stu-id="09c8e-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="09c8e-183">服务器到服务器信任/OAuth 在 Exchange 2013 和 Lync 2013 之间处理。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="09c8e-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="09c8e-184">Lync 2013</span></span>

<span data-ttu-id="09c8e-185">Lync 2013 组件将 Lync 内容归档在 Exchange 2013 中。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="09c8e-186">Windows 文件共享</span><span class="sxs-lookup"><span data-stu-id="09c8e-186">Windows File Shares</span></span>

<span data-ttu-id="09c8e-187">Windows 文件共享组件提供对 SharePoint 服务场中 SSA 的爬网结果。 </span><span class="sxs-lookup"><span data-stu-id="09c8e-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="09c8e-188">图例</span><span class="sxs-lookup"><span data-stu-id="09c8e-188">Legend</span></span>

<span data-ttu-id="09c8e-189">此图的图例以图形的形式显示不同组件之间不同类型的通信，如图中不同颜色的线条所示： </span><span class="sxs-lookup"><span data-stu-id="09c8e-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="09c8e-190">亮蓝线： 查询/操作的 eDiscovery 查询或操作数据</span><span class="sxs-lookup"><span data-stu-id="09c8e-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="09c8e-191">橙色的线： eDisovery 响应-eDiscovery 查询响应数据</span><span class="sxs-lookup"><span data-stu-id="09c8e-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="09c8e-192">绿色线： 状态查询/响应的 eDiscovery 状态查询/响应数据</span><span class="sxs-lookup"><span data-stu-id="09c8e-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="09c8e-193">紫色线条： 交换行动中的状态请求-eDiscovery 请求交换通信的操作状态。</span><span class="sxs-lookup"><span data-stu-id="09c8e-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="09c8e-194">红线： 交换数据/状态响应-从交换 eDiscovery 查询或状态响应。</span><span class="sxs-lookup"><span data-stu-id="09c8e-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="09c8e-195">黑色虚线：服务器到服务器信任/OAuth </span><span class="sxs-lookup"><span data-stu-id="09c8e-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="09c8e-196">黑色实线：爬网/结果 </span><span class="sxs-lookup"><span data-stu-id="09c8e-196">Solid black line: Crawl/results</span></span> 
    

