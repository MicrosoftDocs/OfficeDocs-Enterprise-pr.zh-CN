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
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a><span data-ttu-id="2c0c3-103">SharePoint online 中使用页诊断工具</span><span class="sxs-lookup"><span data-stu-id="2c0c3-103">Use the Page Diagnostics tool for SharePoint Online</span></span>

<span data-ttu-id="2c0c3-104">本文介绍如何使用页诊断工具分析您的经典发布网页和网页上经典工作组网站，针对**SharePoint Online**中的建议做法的子集。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-104">This article describes how you can use the Page Diagnostic tool to analyze your classic publishing pages and pages on classic team sites, against a subset of recommended practices in **SharePoint Online**.</span></span> 
  
<span data-ttu-id="2c0c3-p101">没有启用的发布的工作组网站无法使 Cdn 的使用，但所有剩余的规则都适用。发布添加额外开销，因此不要打开发布，只需以获取 CDN 的功能，如它会产生负面影响页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p101">Team sites that don't have Publishing enabled cannot make use of CDNs but all of the remaining rules are applicable. Publishing adds additional overhead so do not turn on Publishing just to get the CDN functionality as it will negatively impact page load times.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="2c0c3-p102">如工具在设计上可查看 SharePoint 网站页，将会对文档库或系统页面不运行页诊断工具。*Allitems.aspx*页是系统页。如果试图在系统上运行该工具，则会收到一条消息，读取，"此应用程序应仅运行在 SharePoint 页面。">![必须在 SharePoint 页面上运行](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p102">The Page Diagnostics tool will not run against document libraries or system pages, as the tool is designed to review SharePoint site pages. An  *allitems.aspx*  page is a system page. If you attempt to run the tool on a system page, you will get a message that reads, "This application should only be run on SharePoint pages." > ![Must run on a  SharePoint page](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)</span></span>
  
> <span data-ttu-id="2c0c3-p103">这不是在工具错误，如评估库或 system 页中没有值。请导航到非系统 SharePoint 页面使用的工具。该工具应该想要提供反馈有关请单击关于选项卡并按照[提供反馈链接](https://go.microsoft.com/fwlink/?linkid=874109)。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p103">This is not an error in the tool as there is no value in assessing libraries or system pages. Please navigate to a non-system SharePoint page to use the tool. Should you wish to give feedback about the tool please click the About tab and follow the [give feedback link](https://go.microsoft.com/fwlink/?linkid=874109).</span></span> 
  
## <a name="how-to-use-the-page-diagnostic-tool"></a><span data-ttu-id="2c0c3-114">如何使用页诊断工具</span><span class="sxs-lookup"><span data-stu-id="2c0c3-114">How to use the Page Diagnostic tool</span></span>
<span data-ttu-id="2c0c3-115"><a name="useit"> </a></span><span class="sxs-lookup"><span data-stu-id="2c0c3-115"></span></span>

1. <span data-ttu-id="2c0c3-116">使用 Chrome 浏览器，直接打开[链接到该工具](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)或[Chrome 浏览器 web 存储](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint)中打开搜索和安装浏览器扩展。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-116">Using a Chrome browser, open the [link to the tool](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) directly or open the Search in the [Chrome Browser WebStore](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) and install the browser extension.</span></span> 
    
    <span data-ttu-id="2c0c3-117">请查看用户隐私策略存储中的说明页上提供。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-117">Please review the User Privacy Policy provided on the description page in the store.</span></span>
    
    <span data-ttu-id="2c0c3-118">时添加到您的浏览器的工具，您将看到以下权限注意。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-118">When adding the tool to your browser, you will see the following permissions notice.</span></span>
    
    ![部件版式存储权限](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)
  
    <span data-ttu-id="2c0c3-p104">此通知是就地中，因为页面可能包含从外部 SharePoint 具体取决于 web 部件和自定义项在页上的位置的内容。这意味着，该工具将读取的请求和响应时单击开始按钮和仅为活动的 SharePoint 选项卡运行该工具。该信息本地捕获按 web 浏览器，并且可供您通过导出到 JSON 工具中的链接。**不发送到或由 Microsoft 捕获的信息。**</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p104">This notice is in place because a page may contain content from locations outside of SharePoint depending on the webparts and customizations on the page. This means that the tool will read the requests and responses when the start button is clicked and only for the active SharePoint tab where the tool is running. That information is captured locally by the web browser and is available to you via the Export to JSON link in the tool. **The information is not sent to or captured by Microsoft.**</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="2c0c3-p105">Microsoft 不会读取的数据或访问，网站和我们不会捕获任何个人信息、 网站或下载具有此工具的信息。工具记录的唯一信息是租户的名称，规则计数和是否支持日志记录选项利用过时运行该工具。此信息适用于 Microsoft 来分析通过我们的客户经验正在什么难题，以确保不被误用支持日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p105">Microsoft does not read the data or websites you visit, and we do not capture any personal information, website or download information with this tool. The only information logged by the tool is the Tenant name, Rule count and whether the support logging option has been utilized when the tool is run. This information is for Microsoft to analyze what challenges are being experienced by our Customers and to ensure the Support logging capability is not being misused.</span></span>
  
<span data-ttu-id="2c0c3-127">Microsoft 隐私策略可访问[此处](https://go.microsoft.com/fwlink/p/?linkid=857875)应包含该工具。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-127">The tool respects the Microsoft Privacy policy accessible [here](https://go.microsoft.com/fwlink/p/?linkid=857875).</span></span> 
  
    The "Export to JSON" functionality in the tool is also why the "Manage your downloads" permission is needed. Please follow your Company's own Privacy guidelines before sharing the JSON file outside of your Company as it contains the URL's and they fall within PII (Personally Identifiable Information).
    
2. <span data-ttu-id="2c0c3-128">（可选）如果您想要在部件版式 incognito 模式下使用此工具，导航到该扩展名，然后单击"incognito 中允许"。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-128">(Optional) If you want to use the tool in Chrome incognito mode, navigate to the extension and click "allow in incognito".</span></span>
    
3. <span data-ttu-id="2c0c3-129">向 SharePoint 经典发布页面在 SharePoint Online 您想要查看的导航。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-129">Navigate to the SharePoint classic publishing page on SharePoint Online that you would like to review.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="2c0c3-p106">我们已允许"延迟加载"中的项目页面; 例如：因此，**不会自动停止工具**。您希望停止集合，您可以单击**停止**。（这是设计，以设法满足所有页面负载方案）</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p106">We have allowed for "delay loading" of items on pages; therefore, the **tool will not stop automatically**. Should you wish to stop collection, you can click **Stop**. (This is by design to cater for all page load scenarios)</span></span> 
  
<span data-ttu-id="2c0c3-p107">单击**停止**之前，请确保网络跟踪数据已完成。否则，您将具有部分跟踪。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p107">Before you click **Stop**, make sure that the network trace data is complete. Otherwise, you will have a partial trace.</span></span> 
  
<span data-ttu-id="2c0c3-p108">另外，该工具将浏览器扩展，并且打开多个选项卡或 windows 将只允许一次运行该工具的一个活动实例。这是在浏览器的扩展限制。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p108">Additionally, the tool is a Browser Extension, and opening multiple tabs or windows will only allow one active instance of the tool to be run at one time. This is a limitation of extensions in the browser.</span></span> 
  
4. <span data-ttu-id="2c0c3-137">单击扩展徽标</span><span class="sxs-lookup"><span data-stu-id="2c0c3-137">Click on the Extension logo</span></span> ![SharePoint 徽标的页诊断](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) <span data-ttu-id="2c0c3-139">加载该工具，并将显示与以下扩展弹出式窗口：</span><span class="sxs-lookup"><span data-stu-id="2c0c3-139">to load the tool and you will be presented with the following extension popup window:</span></span> 
    
    ![页诊断工具弹出窗口](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)
  
    <span data-ttu-id="2c0c3-141">启动和停止操作 follow 当您单击页上将重新加载的开始和集合的基本概念将开始。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-141">Start and stop operations follow the basic concept of when you click start the page will reload and collection will begin.</span></span>
    
5. <span data-ttu-id="2c0c3-p109">第一个链接是**有关**链接并将提供的一般指导，有关包含链接的工具的详细信息回到本文。它还包括直接链接到 SharePoint 性能建议、 第三方通知和某个选项以提供有关该工具的反馈。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p109">The first link is the **About** link and will provide general guidance and details regarding the tool including a link back to this article. It also includes a direct link to SharePoint Performance recommendations, a Third Party notice and an option to provide feedback about the tool.</span></span> 
    
6. <span data-ttu-id="2c0c3-p110">查看**关联 ID、 SPRequestDuration SPIISLatency** **、 页面加载时间和 URL**信息。（本节仅供参考，可用于几个目的。）</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p110">Review the **Correlation ID, SPRequestDuration, SPIISLatency** **, Page load time and URL** information. (This section is informational and can be used for a few purposes.)</span></span> 
    
  - <span data-ttu-id="2c0c3-146">使用 Microsoft 的支持团队，因为它允许他们提取其他诊断数据时， **CorrelationID**是一个重要的元素。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-146">**CorrelationID** is an important element when working with the Microsoft Support Teams as it allows them to pull additional diagnostic data.</span></span> 
    
  - <span data-ttu-id="2c0c3-p111">**SPRequestDuration**是所需处理页上的服务器时间。如果此时间太长，它不一定意味着服务器已执行格式错误，但可以还反映的呼叫数，并加载推送由页面到服务器例如结构导航，大图像、 大量 API 调用无法所有参与到更长时间服务器时间.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p111">**SPRequestDuration** is the server time taken to process the page. If this time is long, it does not necessarily mean that the server was performing badly but can also reflect the number of calls and load pushed by the page to the server e.g. Structural Navigation, large images, lots of API calls could all contribute to longer server time.</span></span> 
    
  - <span data-ttu-id="2c0c3-p112">**SPIISLatency**是以毫秒为单位接收请求加载网页时，Web 前端服务器上所需的时间。这是延迟，若要开始处理页上的指示符，不包括响应的 web 应用程序所需的时间。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p112">**SPIISLatency** is the time in milliseconds taken on the Web Front End Server when it receives the request to load the page. This is an indicator of latency to start processing the page and does not include the time taken for the web application to respond.</span></span> 
    
  - <span data-ttu-id="2c0c3-p113">**页面加载时间**是记录的时间响应已接收和阅读浏览器请求的时间从页面的时间。任何其他时间受计算机和浏览器加载花费的时间的性能影响。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p113">**Page load time** is the time recorded by the page from the time of the request to the time the response was received and read by the browser. Any additional time is affected by the performance of the computer and the time it takes for the browser to load.</span></span> 
    
  - <span data-ttu-id="2c0c3-153">**URL** （统一资源定位器） 是当前页的 web 地址。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-153">The **URL** (Uniform Resource Locator) is the web address of the current page.</span></span> 
    
7. <span data-ttu-id="2c0c3-154">**诊断选项卡**将列出规则和如果任何这些标有红色![跨](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)，然后在上标识的问题。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-154">The **Diagnostic tab** will list the rules and if any of them are marked with a red ![Cross](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), then there are issues identified on the page.</span></span>
    
    <span data-ttu-id="2c0c3-p114">如果您单击它时为红色，每个规则均具有自己的"详细信息"链接。这样，就会为该规则和如何修正问题后面的详细信息。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p114">Each rule has its own "more info" link if you click on it when it is red. That will take you to the details behind that rule and how to remediate the issue.</span></span>
    
    ![诊断红色-打开的规则](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)
  
1. <span data-ttu-id="2c0c3-158">检查运行作为标准用户</span><span class="sxs-lookup"><span data-stu-id="2c0c3-158">Check Running as Standard User</span></span>
  
<span data-ttu-id="2c0c3-p115">检查页性能不应执行作为登录时的服务帐户、 管理员或网站集管理员即帐户使用提升的权限。其他脚本和功能加载专门针对这些类型的帐户，然后将不会提供页面性能的则返回 true 表示形式。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p115">Checking page performance should not be performed when logged in as a Service Account, Administrator or Site Collection Administrator i.e. an account with elevated privileges. Additional scripts and functionality is loaded specifically for those types of accounts and will not provide a true representation of the page performance.</span></span>
    
2. <span data-ttu-id="2c0c3-161">检查请求的 sharepoint</span><span class="sxs-lookup"><span data-stu-id="2c0c3-161">Check Requests to SharePoint</span></span>
  
<span data-ttu-id="2c0c3-p116">如的重载的页面不会感到性能不佳，应限制的数据和向服务器发出的请求量。此检查验证对 SharePoint 进行的请求数，并将建议时请求超过 6 请求。应缓存，因此不调用为每个页面负载大多数请求。缓存应设置并利用至少 15 分钟，以减少调用每个用户的页面的量。这是常见的问题，在大多数情况下数据仅更改每日但页上检查并提取数据的每个用户，这通常是不必要的每一页的每次。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p116">The amount of data and requests made to the server should be limited as an overloaded page will experience poor performance. This check verifies the number of requests being made to SharePoint and will advise when the requests exceed 6 requests. Most requests should be cached and therefore not called for every page load. Cache should be setup and utilized for at least 15 minutes to reduce the amount of calls to a page by each and every User. This is a common problem and in most cases data only changes daily but the page checks and fetches data each time for each page for each user which is often unnecessary.</span></span>
    
3. <span data-ttu-id="2c0c3-167">检查使用 Cdn</span><span class="sxs-lookup"><span data-stu-id="2c0c3-167">Check using CDNs</span></span>
  
<span data-ttu-id="2c0c3-p117">内容交付网络提供了由 Microsoft 和引用的以下是 SharePoint Online 内容交付网络。有多种类型以及不同的 CDN 服务，如 SharePoint Cdn 和 Cdn Azure 中的可用。[使用以下指南](https://go.microsoft.com/fwlink/?linkid=873250)。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p117">Content Delivery networks have been provided by Microsoft and the ones referred to here are the SharePoint Online Content Delivery Networks. There are multiple types available as well as different CDN services like SharePoint CDNs and then CDNs in Azure. [Use the following guidance](https://go.microsoft.com/fwlink/?linkid=873250).</span></span>
    
4. <span data-ttu-id="2c0c3-171">检查大图像大小</span><span class="sxs-lookup"><span data-stu-id="2c0c3-171">Check for Large Image Sizes</span></span>
  
<span data-ttu-id="2c0c3-p118">通过利用更好的 web 类型，如 PNG，应针对 web 优化图像。图像呈现形式还应利用，可在 SharePoint 中直接。图像 / 大于 100 kb 将突出显示的图像呈现形式，没有为 web 进行优化。[使用以下指南优化的图像](https://go.microsoft.com/fwlink/?linkid=873251)。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p118">Images should be optimized for web by utilizing better web types like PNG. Image renditions should also be utilized and is available in SharePoint directly. Images / image renditions larger than 100kb will be highlighted as not optimized for web. [Use the following guidance for optimizing images](https://go.microsoft.com/fwlink/?linkid=873251).</span></span>
    
5. <span data-ttu-id="2c0c3-176">检查结构导航</span><span class="sxs-lookup"><span data-stu-id="2c0c3-176">Check for Structural Navigation</span></span>
  
<span data-ttu-id="2c0c3-p119">用于 SharePoint 内部部署其中无法使用对象缓存最初设计结构的导航。结构导航不建议用于在 SharePoint Online 中使用，并应改为托管导航或自定义提供程序。[使用以下指南优化导航的。](https://go.microsoft.com/fwlink/?linkid=873247)</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p119">Structural Navigation was originally designed for use in SharePoint on-Premises where object cache could be utilized. Structural Navigation is not recommended for use in SharePoint Online and should be changed to Managed Navigation or a Custom Provider. [Use the following guidance for optimizing navigation.](https://go.microsoft.com/fwlink/?linkid=873247)</span></span>
    
6. <span data-ttu-id="2c0c3-180">检查 CBQ web 部件 (CBQ-内容查询 web 部件)</span><span class="sxs-lookup"><span data-stu-id="2c0c3-180">Check for CBQ WebPart (CBQ - Content by Query WebPart)</span></span>
  
<span data-ttu-id="2c0c3-p120">内容查询 web 部件生成高 SQL 负载为每个用户遍历在每个页面负载的查询中的所有项目。与不同的本地安装，没有可用于限制所需填充此 web 部件的查询数高速缓存。此类 CBQ 执行速度很慢，影响整个页面性能这正是应不使用它。请为内容查询 web 部件的替代工具，使用内容搜索 web 部件 (CSWP)。[使用以下指南与内容搜索 web 部件](https://go.microsoft.com/fwlink/?linkid=873245)。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p120">The Content by Query WebPart generates a high SQL load as it traverses all items in the query for each and every page load, for each User. Unlike an on-Premises installation, there is no cache available to limit the number of queries needed to populate this WebPart. As such CBQ performs slowly and impacts overall page performance which is why it should not be utilized. Please use the Content Search WebPart (CSWP) as the replacement for the Content Query WebPart. [Use the following guidance related to the Content Search WebPart](https://go.microsoft.com/fwlink/?linkid=873245).</span></span>
    
8. <span data-ttu-id="2c0c3-p121">**网络跟踪选项卡**提供 \*\*\* 有关要生成页以及接收响应的请求的详细信息。每个请求和响应的性能的颜色编码基于其会影响整个页面性能即绿色\<500ms，黄色 500 毫秒和红色\>毫秒。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p121">The **Network Trace tab** provides **** detailed information about the requests to build the page as well as the responses received. The performance of each request and response are color coded based on their impact on the overall page performance i.e. Green \< 500ms, Yellow 500-1000ms and Red \> 1000ms.</span></span> 
    
    <span data-ttu-id="2c0c3-188">此选项卡上没有导出到 JSON 选项应您要下载共享的请求和响应的详细信息。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-188">On this tab there is an Export to JSON option should you wish to download and share the request and response details.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="2c0c3-189">悬停在要查看的完整 URL 缩短 URL。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-189">Hover over the shortened URL to view the complete URL.</span></span> 
  
    ![网络跟踪](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)
  
    <span data-ttu-id="2c0c3-191">在此图像红色是页本身和会始终显示一个红色除非页面加载\<毫秒 （即 1 秒）。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-191">In this image the Red is the page itself and that will always show red unless the page loads in \< 1000ms (i.e. 1 second).</span></span>
    
    <span data-ttu-id="2c0c3-p122">在某些情况下*将有任何时间或颜色指示器由于项目已由浏览器缓存*。若要正确测试这一点，打开的页面和清除浏览器缓存，然后单击**开始**，将强制"冷"页加载和的初始页面加载，则返回 true 反射。这应然后比较到"暖"页面加载，这还将有助于确定哪些项目缓存在页面上。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p122">In some cases  *there will be no time or color indicator because the items have already been cached by the browser*  . To test this correctly, open the page, clear browser cache, and then click **Start** as that will force a "cold" page load and be a true reflection of the initial page load. This should then be compared to the "warm" page load as that will also help determine what items are being cached on the page.</span></span> 
    
9. <span data-ttu-id="2c0c3-p123">如果您希望与您的开发人员或支持人员共享这些详细信息然后您可以按照上述图像中单击"导出到 JSON"并，将下载结果。请注意，然后可以使用 JSON 文件查看器打开该文件。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p123">If you wish to share these details or information with your developers or a Support person then you can click "Export to JSON" as per the above image and that will download the results. Please note that the file can then be opened using a JSON file viewer.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="2c0c3-197">这些结果将包含的 URL，因此包含 PII （个人身份信息） 和分发这些信息之前，应遵循您公司的准则。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-197">These results will contain the URL's and therefore contains PII (Personally Identifiable Information) and you should follow your Company guidelines before distributing that information.</span></span> 
  
10. <span data-ttu-id="2c0c3-p124">我们已包括直接在性能支持案例上使用时仅应利用**Microsoft 支持级别功能**。利用此功能将向您使用时不带我们的支持团队提供任何好处。实际上会更加速度显著变慢执行页上，并可能的服务"误用"被视为继续的使用的功能。其他信息添加到服务中的日志记录工具中使用此功能时，没有其他信息。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p124">We have included a **Microsoft Support level feature** that should only be utilized when working directly on a Support Case for performance. Utilizing this feature will provide no benefit to you when used without our Support team. It will in fact make the page perform significantly slower and continued use of the feature may be considered "misuse" of the service. There is no additional information when using this feature in the tool as the additional information is added to the logging in the service.</span></span> 
    
    <span data-ttu-id="2c0c3-p125">没有变化是可见之处在于您已启用，并通过，将会显著降低页性能将通知您 2 到 3 次同时启用的速度较慢的性能。只有将相关的特定页面和该活动会话。因此，应谨慎使用这和仅在积极参与我们的支持团队。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p125">No change is visible except that you will be notified that you have enabled it and your page performance will be significantly degraded by 2-3 times slower performance whilst that is enabled. It will only be relevant for the particular page and that active session. For this reason, this should be used sparingly and only when actively engaged with our Support Team.</span></span>
    
    <span data-ttu-id="2c0c3-p126">若要启用该功能，请打开工具并使用 ALT-Shift-L，然后将显示"启用日志记录支持级别"。单击复选框，然后单击启动重新加载网页并生成分析的支持的详细日志记录。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p126">To enable the feature please open the tool and use ALT-Shift-L which will then display "Enable support level logging". Click the checkbox and then click start to reload the page and generate verbose logging for Support to analyze.</span></span>
    
    ![启用的支持选项](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
    <span data-ttu-id="2c0c3-p127">这一重要元素是 CorrelationID，如支持团队将然后，使用该号码提取所需的信息。请复制 CorrelationID 并向支持提供的因为它们无法执行所需的工作，而不完整的 id。</span><span class="sxs-lookup"><span data-stu-id="2c0c3-p127">An important element for this is the CorrelationID as the Support team will then utilize that number to extract the information needed. Please copy the CorrelationID and provide that to Support as they cannot perform the required work without the complete ID.</span></span>
    

