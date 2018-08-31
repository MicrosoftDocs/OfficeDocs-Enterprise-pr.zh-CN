---
title: SharePoint online 中使用页诊断工具
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
ms.assetid: dbab2593-dc6a-40f7-adfe-031b9baa620f
description: 使用 SharePoint 工具页诊断 SharePoint online 分析经典页面针对建议的最佳实践。
ms.openlocfilehash: 6bfe26900426b30b9f0ad0746b0c1840e122dc82
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539774"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>SharePoint online 中使用页诊断工具

本文介绍如何使用页诊断工具分析您的经典发布网页和网页上经典工作组网站，针对**SharePoint Online**中的建议做法的子集。 
  
没有启用的发布的工作组网站无法使 Cdn 的使用，但所有剩余的规则都适用。发布添加额外开销，因此不要打开发布，只需以获取 CDN 的功能，如它会产生负面影响页面加载时间。
  
> [!IMPORTANT]
> 如工具在设计上可查看 SharePoint 网站页，将会对文档库或系统页面不运行页诊断工具。*Allitems.aspx*页是系统页。如果试图在系统上运行该工具，则会收到一条消息，读取，"此应用程序应仅运行在 SharePoint 页面。">![必须在 SharePoint 页面上运行](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)
  
> 这不是在工具错误，如评估库或 system 页中没有值。请导航到非系统 SharePoint 页面使用的工具。该工具应该想要提供反馈有关请单击关于选项卡并按照[提供反馈链接](https://go.microsoft.com/fwlink/?linkid=874109)。 
  
## <a name="how-to-use-the-page-diagnostic-tool"></a>如何使用页诊断工具
<a name="useit"> </a>

1. 使用 Chrome 浏览器，直接打开[链接到该工具](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)或[Chrome 浏览器 web 存储](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint)中打开搜索和安装浏览器扩展。 
    
    请查看用户隐私策略存储中的说明页上提供。
    
    时添加到您的浏览器的工具，您将看到以下权限注意。
    
    ![部件版式存储权限](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)
  
    此通知是就地中，因为页面可能包含从外部 SharePoint 具体取决于 web 部件和自定义项在页上的位置的内容。这意味着，该工具将读取的请求和响应时单击开始按钮和仅为活动的 SharePoint 选项卡运行该工具。该信息本地捕获按 web 浏览器，并且可供您通过导出到 JSON 工具中的链接。**不发送到或由 Microsoft 捕获的信息。**
    
    > [!IMPORTANT]
    > Microsoft 不会读取的数据或访问，网站和我们不会捕获任何个人信息、 网站或下载具有此工具的信息。工具记录的唯一信息是租户的名称，规则计数和是否支持日志记录选项利用过时运行该工具。此信息适用于 Microsoft 来分析通过我们的客户经验正在什么难题，以确保不被误用支持日志记录功能。
  
Microsoft 隐私策略可访问[此处](https://go.microsoft.com/fwlink/p/?linkid=857875)应包含该工具。 
  
    The "Export to JSON" functionality in the tool is also why the "Manage your downloads" permission is needed. Please follow your Company's own Privacy guidelines before sharing the JSON file outside of your Company as it contains the URL's and they fall within PII (Personally Identifiable Information).
    
2. （可选）如果您想要在部件版式 incognito 模式下使用此工具，导航到该扩展名，然后单击"incognito 中允许"。
    
3. 向 SharePoint 经典发布页面在 SharePoint Online 您想要查看的导航。
    
    > [!IMPORTANT]
    > 我们已允许"延迟加载"中的项目页面; 例如：因此，**不会自动停止工具**。您希望停止集合，您可以单击**停止**。（这是设计，以设法满足所有页面负载方案） 
  
单击**停止**之前，请确保网络跟踪数据已完成。否则，您将具有部分跟踪。 
  
另外，该工具将浏览器扩展，并且打开多个选项卡或 windows 将只允许一次运行该工具的一个活动实例。这是在浏览器的扩展限制。 
  
4. 单击扩展徽标 ![SharePoint 徽标的页诊断](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) 加载该工具，并将显示与以下扩展弹出式窗口： 
    
    ![页诊断工具弹出窗口](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)
  
    启动和停止操作 follow 当您单击页上将重新加载的开始和集合的基本概念将开始。
    
5. 第一个链接是**有关**链接并将提供的一般指导，有关包含链接的工具的详细信息回到本文。它还包括直接链接到 SharePoint 性能建议、 第三方通知和某个选项以提供有关该工具的反馈。 
    
6. 查看**关联 ID、 SPRequestDuration SPIISLatency** **、 页面加载时间和 URL**信息。（本节仅供参考，可用于几个目的。） 
    
  - 使用 Microsoft 的支持团队，因为它允许他们提取其他诊断数据时， **CorrelationID**是一个重要的元素。 
    
  - **SPRequestDuration**是所需处理页上的服务器时间。如果此时间太长，它不一定意味着服务器已执行格式错误，但可以还反映的呼叫数，并加载推送由页面到服务器例如结构导航，大图像、 大量 API 调用无法所有参与到更长时间服务器时间. 
    
  - **SPIISLatency**是以毫秒为单位接收请求加载网页时，Web 前端服务器上所需的时间。这是延迟，若要开始处理页上的指示符，不包括响应的 web 应用程序所需的时间。 
    
  - **页面加载时间**是记录的时间响应已接收和阅读浏览器请求的时间从页面的时间。任何其他时间受计算机和浏览器加载花费的时间的性能影响。 
    
  - **URL** （统一资源定位器） 是当前页的 web 地址。 
    
7. **诊断选项卡**将列出规则和如果任何这些标有红色![跨](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)，然后在上标识的问题。
    
    如果您单击它时为红色，每个规则均具有自己的"详细信息"链接。这样，就会为该规则和如何修正问题后面的详细信息。
    
    ![诊断红色-打开的规则](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)
  
1. 检查运行作为标准用户
  
检查页性能不应执行作为登录时的服务帐户、 管理员或网站集管理员即帐户使用提升的权限。其他脚本和功能加载专门针对这些类型的帐户，然后将不会提供页面性能的则返回 true 表示形式。
    
2. 检查请求的 sharepoint
  
如的重载的页面不会感到性能不佳，应限制的数据和向服务器发出的请求量。此检查验证对 SharePoint 进行的请求数，并将建议时请求超过 6 请求。应缓存，因此不调用为每个页面负载大多数请求。缓存应设置并利用至少 15 分钟，以减少调用每个用户的页面的量。这是常见的问题，在大多数情况下数据仅更改每日但页上检查并提取数据的每个用户，这通常是不必要的每一页的每次。
    
3. 检查使用 Cdn
  
内容交付网络提供了由 Microsoft 和引用的以下是 SharePoint Online 内容交付网络。有多种类型以及不同的 CDN 服务，如 SharePoint Cdn 和 Cdn Azure 中的可用。[使用以下指南](https://go.microsoft.com/fwlink/?linkid=873250)。
    
4. 检查大图像大小
  
通过利用更好的 web 类型，如 PNG，应针对 web 优化图像。图像呈现形式还应利用，可在 SharePoint 中直接。图像 / 大于 100 kb 将突出显示的图像呈现形式，没有为 web 进行优化。[使用以下指南优化的图像](https://go.microsoft.com/fwlink/?linkid=873251)。
    
5. 检查结构导航
  
用于 SharePoint 内部部署其中无法使用对象缓存最初设计结构的导航。结构导航不建议用于在 SharePoint Online 中使用，并应改为托管导航或自定义提供程序。[使用以下指南优化导航的。](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. 检查 CBQ web 部件 (CBQ-内容查询 web 部件)
  
内容查询 web 部件生成高 SQL 负载为每个用户遍历在每个页面负载的查询中的所有项目。与不同的本地安装，没有可用于限制所需填充此 web 部件的查询数高速缓存。此类 CBQ 执行速度很慢，影响整个页面性能这正是应不使用它。请为内容查询 web 部件的替代工具，使用内容搜索 web 部件 (CSWP)。[使用以下指南与内容搜索 web 部件](https://go.microsoft.com/fwlink/?linkid=873245)。
    
8. **网络跟踪选项卡**提供 *** 有关要生成页以及接收响应的请求的详细信息。每个请求和响应的性能的颜色编码基于其会影响整个页面性能即绿色\<500ms，黄色 500 毫秒和红色\>毫秒。 
    
    此选项卡上没有导出到 JSON 选项应您要下载共享的请求和响应的详细信息。
    
    > [!IMPORTANT]
    > 悬停在要查看的完整 URL 缩短 URL。 
  
    ![网络跟踪](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)
  
    在此图像红色是页本身和会始终显示一个红色除非页面加载\<毫秒 （即 1 秒）。
    
    在某些情况下*将有任何时间或颜色指示器由于项目已由浏览器缓存*。若要正确测试这一点，打开的页面和清除浏览器缓存，然后单击**开始**，将强制"冷"页加载和的初始页面加载，则返回 true 反射。这应然后比较到"暖"页面加载，这还将有助于确定哪些项目缓存在页面上。 
    
9. 如果您希望与您的开发人员或支持人员共享这些详细信息然后您可以按照上述图像中单击"导出到 JSON"并，将下载结果。请注意，然后可以使用 JSON 文件查看器打开该文件。
    
    > [!IMPORTANT]
    > 这些结果将包含的 URL，因此包含 PII （个人身份信息） 和分发这些信息之前，应遵循您公司的准则。 
  
10. 我们已包括直接在性能支持案例上使用时仅应利用**Microsoft 支持级别功能**。利用此功能将向您使用时不带我们的支持团队提供任何好处。实际上会更加速度显著变慢执行页上，并可能的服务"误用"被视为继续的使用的功能。其他信息添加到服务中的日志记录工具中使用此功能时，没有其他信息。 
    
    没有变化是可见之处在于您已启用，并通过，将会显著降低页性能将通知您 2 到 3 次同时启用的速度较慢的性能。只有将相关的特定页面和该活动会话。因此，应谨慎使用这和仅在积极参与我们的支持团队。
    
    若要启用该功能，请打开工具并使用 ALT-Shift-L，然后将显示"启用日志记录支持级别"。单击复选框，然后单击启动重新加载网页并生成分析的支持的详细日志记录。
    
    ![启用的支持选项](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
    这一重要元素是 CorrelationID，如支持团队将然后，使用该号码提取所需的信息。请复制 CorrelationID 并向支持提供的因为它们无法执行所需的工作，而不完整的 id。
    

