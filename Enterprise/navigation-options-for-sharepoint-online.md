---
title: SharePoint Online 的导航选项
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: 本文介绍如何通过使用经典发布中托管的导航或搜索驱动的导航 SharePoint online 改进页面加载时间。
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539800"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="3708c-103">SharePoint Online 的导航选项</span><span class="sxs-lookup"><span data-stu-id="3708c-103">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="3708c-104">本文介绍如何通过使用经典发布中托管的导航或搜索驱动的导航 SharePoint online 改进页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="3708c-104">This article describes how to improve page load times for SharePoint Online by using managed navigation or search-driven navigation in Classic publishing.</span></span>
  
<span data-ttu-id="3708c-105">带有启用的经典发布 SharePoint Online 的具有两个导航区域;全局导航和当前导航。</span><span class="sxs-lookup"><span data-stu-id="3708c-105">SharePoint Online with classic publishing enabled has two navigation areas; Global Navigation and Current Navigation.</span></span>
  
<span data-ttu-id="3708c-106">全局导航当前导航时侧或依赖于语言配置和使用的母版页的上下文中左/右导航是顶部导航菜单。</span><span class="sxs-lookup"><span data-stu-id="3708c-106">Global navigation is the top navigation menu while Current Navigation is the side or in-context left/right navigation dependent on the language configuration and master page utilized.</span></span>
  
<span data-ttu-id="3708c-107">导航可以带来负面影响整个门户的性能，因为它通常配置为门户级使用，因为这是任何 SharePoint 网站的重要组成部分。</span><span class="sxs-lookup"><span data-stu-id="3708c-107">Navigation can negatively impact performance for the entire Portal as it is often configured for portal-wide use and as such is an important element of any SharePoint site.</span></span>
  
<span data-ttu-id="3708c-108">结构导航不是 SharePoint Online 中的建议的导航选项，如它为安全修整的内部部署拓扑结构设计和此设计使过多的服务器的呼叫时使用它会影响性能。</span><span class="sxs-lookup"><span data-stu-id="3708c-108">Structural navigation is not the recommended navigation option in SharePoint Online as it was designed for an On-premise topology with security trimming and this design causes excessive server calls and impacts performance when it is used.</span></span>
  
<span data-ttu-id="3708c-p101">在现代设计已更改的现代的 SharePoint 网站的引入已简化扁平的网站层次结构。这简化与消除了对导航相关的性能问题简化层次结构的导航。</span><span class="sxs-lookup"><span data-stu-id="3708c-p101">That design has changed with the introduction of Modern SharePoint sites where Modern has a simplified flattened site hierarchy. This has simplified navigation with a simplified hierarchy that has eliminated performance issues related to navigation.</span></span>
  
<span data-ttu-id="3708c-p102">有两个主即开导航选项在 SharePoint 以及第三个、 自定义的搜索驱动的方法。此外，第四个和非常流行选项是如何构建自定义导航提供程序。请有关自定义导航提供程序的指南，查看[SharePoint Online 的门户导航解决方案](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation)。</span><span class="sxs-lookup"><span data-stu-id="3708c-p102">There are two main out-of-the-box navigation options in SharePoint as well as a third, custom, search-driven approach. Alternatively, a fourth and fairly popular option is to build a Custom Navigation Provider. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) for guidance on a Custom navigation provider.</span></span> 
  
<span data-ttu-id="3708c-114">每个选项具有优点和缺点，如下表中所述。</span><span class="sxs-lookup"><span data-stu-id="3708c-114">Each option has pros and cons as outlined in the following table.</span></span>
  
|<span data-ttu-id="3708c-115">**结构导航**</span><span class="sxs-lookup"><span data-stu-id="3708c-115">**Structural navigation**</span></span>|<span data-ttu-id="3708c-116">**托管导航**</span><span class="sxs-lookup"><span data-stu-id="3708c-116">**Managed navigation**</span></span>|<span data-ttu-id="3708c-117">**搜索驱动的导航**</span><span class="sxs-lookup"><span data-stu-id="3708c-117">**Search-driven navigation**</span></span>||<span data-ttu-id="3708c-118">**自定义导航提供程序**</span><span class="sxs-lookup"><span data-stu-id="3708c-118">**Custom Navigation Provider**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
| <span data-ttu-id="3708c-119">优点：</span><span class="sxs-lookup"><span data-stu-id="3708c-119">Pros:</span></span>  <br/>  <span data-ttu-id="3708c-120">易于配置</span><span class="sxs-lookup"><span data-stu-id="3708c-120">Easy to configure</span></span>  <br/>  <span data-ttu-id="3708c-121">安全修整</span><span class="sxs-lookup"><span data-stu-id="3708c-121">Security-trimmed</span></span>  <br/>  <span data-ttu-id="3708c-122">当添加网站时自动更新</span><span class="sxs-lookup"><span data-stu-id="3708c-122">Automatically updates as sites are added</span></span>  <br/> | <span data-ttu-id="3708c-123">优点：</span><span class="sxs-lookup"><span data-stu-id="3708c-123">Pros:</span></span>  <br/>  <span data-ttu-id="3708c-124">易于维护</span><span class="sxs-lookup"><span data-stu-id="3708c-124">Easy to maintain</span></span>  <br/>  <span data-ttu-id="3708c-125">建议使用该选项</span><span class="sxs-lookup"><span data-stu-id="3708c-125">Recommended option</span></span>  <br/> | <span data-ttu-id="3708c-126">优点：</span><span class="sxs-lookup"><span data-stu-id="3708c-126">Pros:</span></span>  <br/>  <span data-ttu-id="3708c-127">安全修整</span><span class="sxs-lookup"><span data-stu-id="3708c-127">Security-trimmed</span></span>  <br/>  <span data-ttu-id="3708c-128">当添加网站时自动更新</span><span class="sxs-lookup"><span data-stu-id="3708c-128">Automatically updates as sites are added</span></span>  <br/>  <span data-ttu-id="3708c-129">加载时间快，本地缓存的导航结构</span><span class="sxs-lookup"><span data-stu-id="3708c-129">Fast loading time and locally cached navigation structure</span></span>  <br/> || <span data-ttu-id="3708c-130">优点：</span><span class="sxs-lookup"><span data-stu-id="3708c-130">Pros:</span></span>  <br/>    <br/>  <span data-ttu-id="3708c-131">更多选项 / 选项可用</span><span class="sxs-lookup"><span data-stu-id="3708c-131">Wider choice / options available</span></span>  <br/>  <span data-ttu-id="3708c-132">Fast 加载缓存时正确使用</span><span class="sxs-lookup"><span data-stu-id="3708c-132">Fast loading when caching is used correctly</span></span>  <br/> |
| <span data-ttu-id="3708c-133">缺点：</span><span class="sxs-lookup"><span data-stu-id="3708c-133">Cons:</span></span>  <br/> <span data-ttu-id="3708c-134">**不建议**</span><span class="sxs-lookup"><span data-stu-id="3708c-134">**Not recommended**</span></span> <br/> <span data-ttu-id="3708c-135">**对性能产生影响**</span><span class="sxs-lookup"><span data-stu-id="3708c-135">**Impacts performance**</span></span> <br/> | <span data-ttu-id="3708c-136">缺点：</span><span class="sxs-lookup"><span data-stu-id="3708c-136">Cons:</span></span>  <br/>  <span data-ttu-id="3708c-137">不会自动更新以反映网站结构</span><span class="sxs-lookup"><span data-stu-id="3708c-137">Not automatically updated to reflect site structure</span></span>  <br/>  <span data-ttu-id="3708c-138">如果启用了安全修整对性能产生影响</span><span class="sxs-lookup"><span data-stu-id="3708c-138">Impacts performance if security trimming is enabled</span></span>  <br/> | <span data-ttu-id="3708c-139">缺点：</span><span class="sxs-lookup"><span data-stu-id="3708c-139">Cons:</span></span>  <br/>  <span data-ttu-id="3708c-140">不能轻松地对网站排序</span><span class="sxs-lookup"><span data-stu-id="3708c-140">No ability to easily order sites</span></span>  <br/>  <span data-ttu-id="3708c-141">需要对母版页进行自定义（需要具备技术技能）</span><span class="sxs-lookup"><span data-stu-id="3708c-141">Requires customization of the master page (technical skills required)</span></span>  <br/> || <span data-ttu-id="3708c-142">缺点：</span><span class="sxs-lookup"><span data-stu-id="3708c-142">Cons:</span></span>  <br/>  <span data-ttu-id="3708c-143">自定义开发，则需要</span><span class="sxs-lookup"><span data-stu-id="3708c-143">Custom development is required</span></span>  <br/>  <span data-ttu-id="3708c-144">外部数据源缓存存储所需 / 例如 Azure</span><span class="sxs-lookup"><span data-stu-id="3708c-144">External data source / cache stored is needed e.g. Azure</span></span>  <br/> |
   
<span data-ttu-id="3708c-p103">最适合您的网站的选项将取决于您的网站要求和您的技术功能。如果您便于使用自定义母版页，并维护更改可能出现的默认母版页中的 SharePoint Online 的组织中有一些功能，搜索驱动选项将产生最佳用户体验。如果您希望简单介于即开结构导航和搜索，然后托管的导航是一个很好的选项。可以通过维护托管的导航选项配置，不涉及代码自定义文件，并且比即开结构导航显著速度更快。</span><span class="sxs-lookup"><span data-stu-id="3708c-p103">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the search-driven option will produce the best user experience. If you want a simple middle ground between the out-of-the-box structural navigation and search, then the managed navigation is a very good option. The managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than the out-of-the-box structural navigation.</span></span>
  
<span data-ttu-id="3708c-p104">简化类似现代经典门户的总体结构，有助于总体性能和规模以及。这意味着，而不是让单个网站集与数百/数千个站点 （子网站），更好的方法是拥有大量具有很少的子网站 （子网站） 的网站集。</span><span class="sxs-lookup"><span data-stu-id="3708c-p104">Simplifying the overall structure of your Classic Portal much like Modern, helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds / thousands of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>
  
<span data-ttu-id="3708c-151">这提供服务中的其他扩展选项、 可避免投入一个大的数据库的所有内容和最终将允许为导航和更重要的是安全的灵活性。</span><span class="sxs-lookup"><span data-stu-id="3708c-151">This provides additional scaling options in the service, avoids putting all content into one big database and ultimately allows greater flexibility for navigation and more importantly security.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="3708c-152">在 SharePoint Online 中使用结构导航</span><span class="sxs-lookup"><span data-stu-id="3708c-152">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="3708c-p105">这是默认情况下使用开的导航和是最简单的解决方案，但此类具有高性能权衡。它不需要任何自定义和非技术用户可以方便地添加项目、 隐藏项目，请从设置页管理导航。这是但是也托管导航，因此建议同时使用托管导航的可以为 true，则是轻松地管理和控制以及。</span><span class="sxs-lookup"><span data-stu-id="3708c-p105">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well.</span></span>
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="3708c-156">在 SharePoint Online 中启用结构导航</span><span class="sxs-lookup"><span data-stu-id="3708c-156">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="3708c-p106">为了说明如何使用结构导航和显示 SharePoint Online 标准解决方案中的性能子网站选项打开。下面屏幕快照，在**网站设置**页上找到的设置\>**导航**。</span><span class="sxs-lookup"><span data-stu-id="3708c-p106">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screen shot settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![显示子网站的屏幕截图](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="3708c-160">分析 SharePoint Online 中的结构导航性能</span><span class="sxs-lookup"><span data-stu-id="3708c-160">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="3708c-161">若要分析 SharePoint 页面的性能，请使用 Internet Explorer 中的 F12 开发人员工具的“网络”**** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="3708c-161">To analyze the performance of a SharePoint page use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![显示 F12 开发工具“网络”选项卡的屏幕截图](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
<span data-ttu-id="3708c-163">在“网络”**** 选项卡，单击正在加载的 .aspx 页面，然后单击“详细信息”**** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="3708c-163">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span> 
  
![显示详细信息选项卡的屏幕截图](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
<span data-ttu-id="3708c-165">单击“响应头”****。</span><span class="sxs-lookup"><span data-stu-id="3708c-165">Click **Response headers**.</span></span>
  
![“详细信息”选项卡的屏幕截图](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
<span data-ttu-id="3708c-p107">SharePoint 在其响应标头中返回一些有用的诊断信息。其中最有用的信息之一是 **SPRequestDuration**，这是请求在服务器上处理所需的时间，以毫秒为单位。</span><span class="sxs-lookup"><span data-stu-id="3708c-p107">SharePoint returns some useful diagnostic information in its response headers. One of the most useful is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> 
  
<span data-ttu-id="3708c-p108">以下屏幕截图**显示子网站**中是结构导航取消选中。这意味着在全局导航中存在仅网站集的链接：</span><span class="sxs-lookup"><span data-stu-id="3708c-p108">In the following screen shot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span> 
  
![显示加载时间为请求持续时间的屏幕截图](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
<span data-ttu-id="3708c-p109">**SPRequestDuration**键的值为 245 毫秒。这表示返回请求所花的时间。由于在网站上只有一个导航项，这是如何 SharePoint Online 执行大流量的导航不好基准。下一步的屏幕截图显示了如何在子网站中添加影响此项。</span><span class="sxs-lookup"><span data-stu-id="3708c-p109">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span> 
  
![显示请求持续时间为 2502 毫秒的屏幕截图](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
<span data-ttu-id="3708c-177">添加子网站显著增加了返回页面请求所用的时间。</span><span class="sxs-lookup"><span data-stu-id="3708c-177">Adding the subsites has significantly increased the time it takes to return the page request.</span></span>
  
<span data-ttu-id="3708c-178">使用常规的结构化的导航的优点是，您可以轻松地组织顺序、 隐藏网站，添加页面、 结果安全修整，并且您不解调器从支持母版页在 SharePoint Online 中使用。</span><span class="sxs-lookup"><span data-stu-id="3708c-178">The advantages of using the regular structured navigation is that you can easily organize the order, hide sites, add pages, the results are security-trimmed, and you are not deviating from the supported master pages used in SharePoint Online.</span></span>
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a><span data-ttu-id="3708c-179">使用 SharePoint Online 中的托管导航和托管元数据</span><span class="sxs-lookup"><span data-stu-id="3708c-179">Using managed navigation and managed metadata in SharePoint Online</span></span>

<span data-ttu-id="3708c-180">托管导航是另一个可用来重新创建与结构导航相同类型的功能的开箱即用选项。</span><span class="sxs-lookup"><span data-stu-id="3708c-180">Managed navigation is another out-of-the-box option that you can use to recreate the same sort of functionality as structural navigation.</span></span>
  
<span data-ttu-id="3708c-p110">使用托管元数据的好处是速度快得多检索比使用查询的内容来构建网站导航的数据。虽然更快地没有方法对安全修整结果，以便用户没有访问权限给定的网站，如果链接仍会显示，但将导致错误消息。</span><span class="sxs-lookup"><span data-stu-id="3708c-p110">The advantage of using managed metadata is that it is much faster to retrieve the data than using content by query to build the site navigation. Although it is much faster there is no way to security trim the results so if a user doesn't have access to a given site, the link will still show but will lead to an error message.</span></span>
  
 <span data-ttu-id="3708c-183">**如何实现托管导航和结果**</span><span class="sxs-lookup"><span data-stu-id="3708c-183">**How to implement managed navigation and the results**</span></span>
  
<span data-ttu-id="3708c-184">有一些文章 TechNet 上有关托管导航的详细信息，例如，请参阅[Overview of SharePoint Server 2013 中托管导航](https://go.microsoft.com/fwlink/?LinkId=708689)。</span><span class="sxs-lookup"><span data-stu-id="3708c-184">There are several articles on TechNet about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span></span>
  
<span data-ttu-id="3708c-p111">要实现托管导航，您需要具有术语库管理员权限。通过使用与网站集结构相匹配的 URL 设置术语，可以使用托管导航取代结构导航。例如：</span><span class="sxs-lookup"><span data-stu-id="3708c-p111">In order to implement managed navigation, you need to have term store administrator permissions. By setting up terms with URLs that match the structure of a site collection, managed navigation can be used to replace structural navigation. For example:</span></span>
  
![Subsite1 示例的屏幕截图](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
<span data-ttu-id="3708c-189">下面的示例显示使用托管导航的复杂导航的性能。</span><span class="sxs-lookup"><span data-stu-id="3708c-189">The following example shows the performance of the complex navigation using managed navigation.</span></span>
  
![SPRequestDuration 示例的屏幕截图](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
<span data-ttu-id="3708c-191">与通过查询结构导航方法的内容相比，一致地使用托管导航会提高性能。</span><span class="sxs-lookup"><span data-stu-id="3708c-191">Using managed navigation consistently improves performance compared to the content by query structural navigation approach.</span></span>
  
## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="3708c-192">使用搜索驱动的客户端脚本</span><span class="sxs-lookup"><span data-stu-id="3708c-192">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="3708c-p112">通过搜索，您可以利用使用连续爬网在后台建立的索引。这意味着没有大量的内容查询。搜索结果将从搜索索引中提取，结果将进行安全修整。这比使用常规内容查询更快。使用搜索进行结构导航将大大减少页面加载时间，尤其是当您具有复杂的网站结构时。与托管导航相比，其主要优点是您将从安全修整中受益。</span><span class="sxs-lookup"><span data-stu-id="3708c-p112">Using search you can leverage the indexes that are built up in the background using continuous crawl. This means there are no heavy content queries. The search results are pulled from the search index and the results are security-trimmed. This is faster than using regular content queries. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>
  
<span data-ttu-id="3708c-p113">此方法涉及创建自定义母版页以及将开箱即用的导航代码替换为自定义 HTML。按照此过程来替换文件 seattle.html 中的导航代码。</span><span class="sxs-lookup"><span data-stu-id="3708c-p113">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure to replace the navigation code in the file seattle.html.</span></span>
  
<span data-ttu-id="3708c-201">本示例中，将打开 seattle.html 文件，并将整个元素**id ="DeltaTopNavigation"** 替换为自定义 HTML 代码。</span><span class="sxs-lookup"><span data-stu-id="3708c-201">In this example, you will open the seattle.html file and replace the whole element **id="DeltaTopNavigation"** with the custom HTML code.</span></span> 
  
 <span data-ttu-id="3708c-202">**示例：替换母版页中开箱即用的导航代码**</span><span class="sxs-lookup"><span data-stu-id="3708c-202">**Example: To replace the out-of-the-box navigation code in a master page**</span></span>
  
1. <span data-ttu-id="3708c-203">导航到“网站设置”**** 页面。</span><span class="sxs-lookup"><span data-stu-id="3708c-203">Navigate to the **Site Settings** page.</span></span> 
    
2. <span data-ttu-id="3708c-204">单击“母版页”**** 打开母版页样式库。</span><span class="sxs-lookup"><span data-stu-id="3708c-204">Open the master page gallery by clicking **Master Pages**.</span></span>
    
3. <span data-ttu-id="3708c-205">从这里，您可以导航整个库并下载文件 **seattle.master**。</span><span class="sxs-lookup"><span data-stu-id="3708c-205">From here you can navigate through the library and download the file **seattle.master**.</span></span>
    
4. <span data-ttu-id="3708c-206">使用文本编辑器编辑代码，并删除下面的屏幕截图中的代码块。</span><span class="sxs-lookup"><span data-stu-id="3708c-206">Edit the code using a text editor and delete the code block in the following screen shot.</span></span>
    
    ![要删除的 DeltaTopNavigation 代码的屏幕截图](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. <span data-ttu-id="3708c-208">删除之间的代码\<SharePoint:AjaxDelta id ="DeltaTopNavigation"\>和\<\SharePoint:AjaxDelta\>标签，并将其替换为以下代码段：</span><span class="sxs-lookup"><span data-stu-id="3708c-208">Remove the code between the \<SharePoint:AjaxDelta id="DeltaTopNavigation"\> and \<\SharePoint:AjaxDelta\> tags and replace it with the following snippet:</span></span>
    
  ```
  <div id="loading">
    <!--Replace with path to loading image.-->
    <div style="background-image: url(''); height: 22px; width: 22px; ">
    </div>
  </div>
  <!-- Main Content-->
  <div id="navContainer" style="display:none">
      <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
          <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
              <span class="menu-item-text" data-bind="text: item.Title">
              </span>
          </a>
          <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
              <li class="static dynamic-children level1">
                  <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
                 
                   <!-- ko if: children.length > 0-->
                      <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                          <span class="menu-item-text" data-bind="text: item.Title">
                          </span>
                      </span>
                  <!-- /ko -->
                  <!-- ko if: children.length == 0-->   
                      <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                          <span class="menu-item-text" data-bind="text: item.Title">
                          </span>
                      </span>
                  <!-- /ko -->   
                  </a>
                 
                  <!-- ko if: children.length > 0-->                                                       
                  <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                      <li class="dynamic level2">
                          <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
           
            <!-- ko if: children.length > 0-->
            <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
             <span class="menu-item-text" data-bind="text: item.Title">
             </span>
            </span>
             <!-- /ko -->
            <!-- ko if: children.length == 0-->
            <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
             <span class="menu-item-text" data-bind="text: item.Title">
             </span>
            </span>                 
            <!-- /ko -->   
                          </a>
            <!-- ko if: children.length > 0-->
           <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
            <li class="dynamic level3">
             <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
              <span class="menu-item-text" data-bind="text: item.Title">
              </span>
             </a>
            </li>
           </ul>
             <!-- /ko -->
                      </li>
                  </ul>
                  <!-- /ko -->
              </li>
          </ul>
      </div>
  </div>
  ```

6. <span data-ttu-id="3708c-p114">替换中加载的 URL 图像开头，网站集加载图像的链接的定位标记。所做的更改后，重命名该文件，然后将其上载到母版页样式库。这会生成新的.master 文件。</span><span class="sxs-lookup"><span data-stu-id="3708c-p114">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span>
    
7. <span data-ttu-id="3708c-p115">此 HTML 是将使用从 JavaScript 代码返回的搜索结果填充的基本标记。您将需要编辑下面的代码更改的值`var root = "site collection URL"`如以下代码段中所示：</span><span class="sxs-lookup"><span data-stu-id="3708c-p115">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the following code to change the value for the  `var root = "site collection URL"` as demonstrated in the following snippet:</span></span> 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

    <span data-ttu-id="3708c-214">整个 JavaScript 文件如下所示：</span><span class="sxs-lookup"><span data-stu-id="3708c-214">The entire JavaScript file is as follows:</span></span>
    
  ```
  //Models and Namespaces
  var SPOCustom = SPOCustom || {};
  SPOCustom.Models = SPOCustom.Models || {}
  SPOCustom.Models.NavigationNode = function () {
      this.Url = ko.observable("");
      this.Title = ko.observable("");
      this.Parent = ko.observable("");
  };
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  var baseUrl = root + "/_api/search/query?querytext=";
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
  var baseRequest = {
      url: "",
      type: ""
  };
  //Parses a local object from JSON search result.
  function getNavigationFromDto(dto) {
      var item = new SPOCustom.Models.NavigationNode();
      if (dto != undefined) {
          var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');
          if (webTemplate != "APP") {
              item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
              item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
              item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
          }
      }
      return item;
  }
  function getSearchResultsValue(results, key) {
      for (i = 0; i < results.length; i++) {
          if (results[i].Key == key) {
              return results[i].Value;
          }
      }
      return null;
  }
  //Parse a local object from the serialized cache.
  function getNavigationFromCache(dto) {
      var item = new SPOCustom.Models.NavigationNode();
      if (dto != undefined) {
          item.Title(dto.Title);
          item.Url(dto.Url);
          item.Parent(dto.Parent);
      }
      return item;
  }
  /* create a new OData request for JSON response */
  function getRequest(endpoint) {
      var request = baseRequest;
      request.type = "GET";
      request.url = endpoint;
      request.headers = { ACCEPT: "application/json;odata=verbose" };
      return request;
  };
  /* Navigation Module*/
  function NavigationViewModel() {
      "use strict";
      var self = this;
      self.nodes = ko.observableArray([]);
      self.hierarchy = ko.observableArray([]);;
      self.loadNavigatioNodes = function () {
          //Check local storage for cached navigation datasource.
          var fromStorage = localStorage["nodesCache"];
          if (false) {
              var cachedNodes = JSON.parse(localStorage["nodesCache"]);
              if (cachedNodes &amp;&amp; timeStamp) {
                  //Check for cache expiration. Currently set to 3 hrs.
                  var now = new Date();
                  var diff = now.getTime() - timeStamp;
                  if (Math.round(diff / (1000 * 60 * 60)) < 3) {
                      //return from cache.
                      var cacheResults = [];
                      $.each(cachedNodes, function (i, item) {
                          var nodeitem = getNavigationFromCache(item, true);
                          cacheResults.push(nodeitem);
                      });
                      self.buildHierarchy(cacheResults);
                      self.toggleView();
                      addEventsToElements();
                      return;
                  }
              }
          }
          //No cache hit, REST call required.
          self.queryRemoteInterface();
      };
      //Executes a REST call and builds the navigation hierarchy.
      self.queryRemoteInterface = function () {
          var oDataRequest = getRequest(query);
          $.ajax(oDataRequest).done(function (data) {
              var results = [];
              $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {
                  if (i == 0) {
                      //Add root element.
                      var rootItem = new SPOCustom.Models.NavigationNode();
                      rootItem.Title("Root");
                      rootItem.Url(root);
                      rootItem.Parent(null);
                      results.push(rootItem);
                  }
                  var navItem = getNavigationFromDto(item);
                  results.push(navItem);
              });
              //Add to local cache
              localStorage["nodesCache"] = ko.toJSON(results);
              localStorage["nodesCachedAt"] = new Date().getTime();
              self.nodes(results);
              if (self.nodes().length > 0) {
                  var unsortedArray = self.nodes();
                  var sortedArray = unsortedArray.sort(self.sortObjectsInArray);
                  self.buildHierarchy(sortedArray);
                  self.toggleView();
                  addEventsToElements();
              }
          }).fail(function () {
              //Handle error here!!
              $("#loading").hide();
              $("#error").show();
          });
      };
      self.toggleView = function () {
          var navContainer = document.getElementById("navContainer");
          ko.applyBindings(self, navContainer);
          $("#loading").hide();
          $("#navContainer").show();
      };
      //Uses linq.js to build the navigation tree.
      self.buildHierarchy = function (enumerable) {
          self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
              return d.Parent() == null;
          }, function (parent, child) {
              if (parent.Url() == null || child.Parent() == null)
                  return false;
              return parent.Url().toUpperCase() == child.Parent().toUpperCase();
          }).ToArray());
          self.sortChildren(self.hierarchy()[0]);
      };
      self.sortChildren = function (parent) {
          // sjip processing if no children
          if (!parent || !parent.children || parent.children.length === 0) {
              return;
          }
          parent.children = parent.children.sort(self.sortObjectsInArray2);
          for (var i = 0; i < parent.children.length; i++) {
              var elem = parent.children[i];
              if (elem.children &amp;&amp; elem.children.length > 0) {
                  self.sortChildren(elem);
              }
          }
      };
      // ByHierarchy method breaks the sorting in chrome and firefix 
      // we need to resort  as ascending
      self.sortObjectsInArray2 = function (a, b) {
          if (a.item.Title() > b.item.Title())
              return 1;
          if (a.item.Title() < b.item.Title())
              return -1;
          return 0;
      };
      self.sortObjectsInArray = function (a, b) {
          if (a.Title() > b.Title())
              return -1;
          if (a.Title() < b.Title())
              return 1;
          return 0;
      }
  }
  //Loads the navigation on load and binds the event handlers for mouse interaction.
  function InitCustomNav() {
      var viewModel = new NavigationViewModel();
      viewModel.loadNavigatioNodes();
  }
  function addEventsToElements() {
      //events.
  
  ```

     <span data-ttu-id="3708c-215">$("li.level1").mouseover （函数 （） {</span><span class="sxs-lookup"><span data-stu-id="3708c-215">$("li.level1").mouseover(function () {</span></span> 
  
<span data-ttu-id="3708c-216">var 位置 = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="3708c-216">var position = $(this).position();</span></span>
  
<span data-ttu-id="3708c-217">$(this).find("ul.level2").css ({宽度： 100，左： position.left + 10，top: 50});</span><span class="sxs-lookup"><span data-stu-id="3708c-217">$(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });</span></span>
    
     }) 
  
<span data-ttu-id="3708c-218">.mouseout （函数 （） {</span><span class="sxs-lookup"><span data-stu-id="3708c-218">.mouseout(function () {</span></span>
  
<span data-ttu-id="3708c-219">$(this).find("ul.level2").css ({左侧：-99999，顶部： 0});</span><span class="sxs-lookup"><span data-stu-id="3708c-219">$(this).find("ul.level2").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="3708c-220">});</span><span class="sxs-lookup"><span data-stu-id="3708c-220"></span></span>
  
<span data-ttu-id="3708c-221">$("li.level2").mouseover （函数 （） {</span><span class="sxs-lookup"><span data-stu-id="3708c-221">$("li.level2").mouseover(function () {</span></span>
  
<span data-ttu-id="3708c-222">var 位置 = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="3708c-222">var position = $(this).position();</span></span>
  
<span data-ttu-id="3708c-223">console.log(JSON.stringify(position));</span><span class="sxs-lookup"><span data-stu-id="3708c-223">console.log(JSON.stringify(position));</span></span>
  
<span data-ttu-id="3708c-224">$(this).find("ul.level3").css ({宽度： 100，左： position.left + 95，top: position.top});</span><span class="sxs-lookup"><span data-stu-id="3708c-224">$(this).find("ul.level3").css({ width: 100, left: position.left + 95, top: position.top});</span></span>
    
     }) 
  
<span data-ttu-id="3708c-225">.mouseout （函数 （） {</span><span class="sxs-lookup"><span data-stu-id="3708c-225">.mouseout(function () {</span></span>
  
<span data-ttu-id="3708c-226">$(this).find("ul.level3").css ({左侧：-99999，顶部： 0});</span><span class="sxs-lookup"><span data-stu-id="3708c-226">$(this).find("ul.level3").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="3708c-227">});</span><span class="sxs-lookup"><span data-stu-id="3708c-227"></span></span>
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. <span data-ttu-id="3708c-p116">接下来，结果将分配给 **[self.nodes]** 数组和层次结构构建利用使用 linq.js 将输出分配给数组 **[self.heirarchy]** 对象。此数组是绑定到 HTML 的对象。这是通过将自我对象传递给 **[ko.applyBinding()]** 函数完成 **[toggleView()]** 函数中。然后，这会导致要绑定到以下 HTML 的层次结构数组：</span><span class="sxs-lookup"><span data-stu-id="3708c-p116">Next, the results are assigned to the **[self.nodes]** array and a hierarchy is built out of the objects using linq.js assigning the output to an array **[self.heirarchy]**. This array is the object that is bound to the HTML. This is done in the **[toggleView()]** function by passing the self object to the **[ko.applyBinding()]** function. This then causes the hierarchy array to be bound to the following HTML:</span></span> 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    <span data-ttu-id="3708c-232">最后的事件处理程序 **[mouseenter]** 和 **[mouseexit]** 被添加到其完成 **[addEventsToElements()]** 函数中处理的子网站下拉列表菜单的顶级导航。</span><span class="sxs-lookup"><span data-stu-id="3708c-232">Finally, the event handlers for **[mouseenter]** and **[mouseexit]** are added to the top-level navigation to handle the subsite drop-down menus which is done in the **[addEventsToElements()]** function.</span></span> 
    
    <span data-ttu-id="3708c-233">屏幕截图下方中，可以看到的导航的结果：</span><span class="sxs-lookup"><span data-stu-id="3708c-233">The results of the navigation can be seen in the screen shot below:</span></span>
    
    ![导航结果的屏幕截图](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    <span data-ttu-id="3708c-235">在我们复杂的导航示例中，没有本地缓存的全新页面加载显示服务器上所用的时间已从基准结构导航大大减少，以获取与托管导航方法类似的结果。</span><span class="sxs-lookup"><span data-stu-id="3708c-235">In our complex navigation example a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>
    
    ![SPRequestDuration 301 的屏幕截图](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    <span data-ttu-id="3708c-237">这种方法的一个主要优点是通过使用 HTML5 本地存储，导航存储在本地，以便用户在下次加载页面时使用。</span><span class="sxs-lookup"><span data-stu-id="3708c-237">One major benefit of this approach is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span>
    
<span data-ttu-id="3708c-p117">通过使用搜索 API 进行结构导航，我们实现了较大的性能改进；但是，它需要具备技术能力来执行和自定义此功能。在示例实现中，站点按与开箱即用结构导航一样的顺序排列，即按字母顺序。如果您想要偏离此顺序，开发和维护过程将更加复杂。此外，此方法还要求您偏离受支持的母版页。如果未维护自定义母版页，您的网站将会遗漏 Microsoft 对母版页所做的更新和改进。</span><span class="sxs-lookup"><span data-stu-id="3708c-p117">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality. In the example implementation, the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>
  
<span data-ttu-id="3708c-243">上面的代码具有以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="3708c-243">The above code has the following dependencies:</span></span>
  
- <span data-ttu-id="3708c-244">jQuery-[http://jquery.com/](http://jquery.com/)</span><span class="sxs-lookup"><span data-stu-id="3708c-244">jQuery - [http://jquery.com/](http://jquery.com/)</span></span>
    
- <span data-ttu-id="3708c-245">KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)</span><span class="sxs-lookup"><span data-stu-id="3708c-245">KnockoutJS - [http://knockoutjs.com/](http://knockoutjs.com/)</span></span>
    
- <span data-ttu-id="3708c-246">Linq.js- [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/)，或[github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span><span class="sxs-lookup"><span data-stu-id="3708c-246">Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), or [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span></span>
    
<span data-ttu-id="3708c-p118">当前版本的 LinqJS 不包含上面的代码中使用 ByHierarchy 方法，并将中断导航代码。若要解决此问题，请将以下方法添加到行之前 Linq.js 文件"采取恢复： 函数 （）"。</span><span class="sxs-lookup"><span data-stu-id="3708c-p118">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line "Flatten: function ()".</span></span>
  
```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;
    return new Enumerable(function() {
         var enumerator;
         var index = 0;
        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };
        return new IEnumerator(
        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```


