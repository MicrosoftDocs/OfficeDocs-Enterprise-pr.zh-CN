---
title: SharePoint Online 的导航选项
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: 本文介绍与 SharePoint 发布 SharePoint Online 中启用导航选项网站。选择和配置导航显著影响性能和可伸缩性的 SharePoint Online 中的网站。
ms.openlocfilehash: 5a190ca643c20b6644ca1eecdac2a4a2e281a09e
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547174"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="c444d-104">SharePoint Online 的导航选项</span><span class="sxs-lookup"><span data-stu-id="c444d-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="c444d-p102">本文介绍与 SharePoint 发布 SharePoint Online 中启用导航选项网站。选择和配置导航显著影响性能和可伸缩性的 SharePoint Online 中的网站。</span><span class="sxs-lookup"><span data-stu-id="c444d-p102">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online. The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="c444d-107">概述</span><span class="sxs-lookup"><span data-stu-id="c444d-107">Overview</span></span>

<span data-ttu-id="c444d-p103">导航提供程序配置显著影响整个网站的性能和必须采取仔细考虑选取的导航提供程序和有效地调整您的 SharePoint 网站的要求的配置。有两个开的导航提供程序，以及自定义导航实现。</span><span class="sxs-lookup"><span data-stu-id="c444d-p103">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site. There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="c444d-p104">第一个选项[**（元数据） 的托管导航**](#using-managed-navigation-and-metadata-in-sharepoint-online)，建议，并且是在 SharePoint Online; 默认选项之一但是，我们建议除非必需的情况下禁用安全修整。作为通过默认安全设置的此导航提供程序; 启用安全修整但是，多个网站不需要安全修整自从导航元素通常都是一致的网站的所有用户的开销。若要禁用安全修整推荐配置，此导航提供程序不需要枚举网站结构，是高度可扩展的可接受的性能影响。</span><span class="sxs-lookup"><span data-stu-id="c444d-p104">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required. Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site. With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="c444d-p105">第二个选项，[**结构导航**](#using-structural-navigation-in-sharepoint-online)，**是 SharePoint Online 中的建议的导航选项**。此导航提供程序的 SharePoint Online 中的支持有限的内部部署拓扑结构设计。虽然它提供了一些其他的一组与其他导航选项的功能，这些功能，包括安全修整和网站结构枚举时，因服务器调用影响的可伸缩性和性能的成本使用它。使用 structed 导航的使用过多的资源的网站可能会受到限制。</span><span class="sxs-lookup"><span data-stu-id="c444d-p105">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**. This navigation provider was designed for an on-premises topology has limited support in SharePoint Online. While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used. Sites using structed navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="c444d-p106">除了开的导航提供程序，许多客户已成功实现替代的自定义导航实现。一个公共类的自定义导航实现坚信存储的导航节点的本地缓存的客户端呈现的设计模式。（请参阅**[搜索驱动客户端脚本编写](#using-search-driven-client-side-scripting)** 这篇文章中。）</span><span class="sxs-lookup"><span data-stu-id="c444d-p106">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations. One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes. (See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="c444d-120">这些导航提供程序有两种关键优势：</span><span class="sxs-lookup"><span data-stu-id="c444d-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="c444d-121">他们通常很好地使用响应页面设计。</span><span class="sxs-lookup"><span data-stu-id="c444d-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="c444d-122">它们是极大可伸缩性和性能，因为它们可能造成没有资源成本 （和刷新后超时在后台）。</span><span class="sxs-lookup"><span data-stu-id="c444d-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="c444d-123">这些导航提供程序可以检索使用各种策略，从到各种动态数据提供程序的简单静态配置导航数据。</span><span class="sxs-lookup"><span data-stu-id="c444d-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="c444d-124">数据提供程序的示例是使用**搜索驱动的导航**，从而枚举导航节点和处理安全修整高效的灵活性。</span><span class="sxs-lookup"><span data-stu-id="c444d-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="c444d-p107">有其他受欢迎的选项，以构建**自定义导航提供程序**。请有关更多有关构建自定义导航提供程序的指南，查看[SharePoint Online 的门户导航解决方案](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)。</span><span class="sxs-lookup"><span data-stu-id="c444d-p107">There are other popular options to build **Custom navigation providers**. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="c444d-127">专业人员和 SharePoint Online 的缺点导航选项</span><span class="sxs-lookup"><span data-stu-id="c444d-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="c444d-128">下表总结了每个选项的优缺点。</span><span class="sxs-lookup"><span data-stu-id="c444d-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="c444d-129">托管导航</span><span class="sxs-lookup"><span data-stu-id="c444d-129">Managed navigation</span></span>  |<span data-ttu-id="c444d-130">结构导航</span><span class="sxs-lookup"><span data-stu-id="c444d-130">Structural navigation</span></span>  |<span data-ttu-id="c444d-131">搜索驱动的导航</span><span class="sxs-lookup"><span data-stu-id="c444d-131">Search-driven navigation</span></span>  |<span data-ttu-id="c444d-132">自定义导航提供程序</span><span class="sxs-lookup"><span data-stu-id="c444d-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="c444d-133">优点：</span><span class="sxs-lookup"><span data-stu-id="c444d-133">Pros:</span></span><br/><br/><span data-ttu-id="c444d-134">易于维护</span><span class="sxs-lookup"><span data-stu-id="c444d-134">Easy to maintain</span></span><br/><span data-ttu-id="c444d-135">建议使用该选项</span><span class="sxs-lookup"><span data-stu-id="c444d-135">Recommended option</span></span><br/>     |<span data-ttu-id="c444d-136">优点：</span><span class="sxs-lookup"><span data-stu-id="c444d-136">Pros:</span></span><br/><br/><span data-ttu-id="c444d-137">易于配置</span><span class="sxs-lookup"><span data-stu-id="c444d-137">Easy to configure</span></span><br/><span data-ttu-id="c444d-138">安全修整</span><span class="sxs-lookup"><span data-stu-id="c444d-138">Security trimmed</span></span><br/><span data-ttu-id="c444d-139">添加内容将自动更新</span><span class="sxs-lookup"><span data-stu-id="c444d-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="c444d-140">优点：</span><span class="sxs-lookup"><span data-stu-id="c444d-140">Pros:</span></span><br/><br/><span data-ttu-id="c444d-141">安全修整</span><span class="sxs-lookup"><span data-stu-id="c444d-141">Security trimmed</span></span><br/><span data-ttu-id="c444d-142">当添加网站时自动更新</span><span class="sxs-lookup"><span data-stu-id="c444d-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="c444d-143">加载时间快，本地缓存的导航结构</span><span class="sxs-lookup"><span data-stu-id="c444d-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="c444d-144">优点：</span><span class="sxs-lookup"><span data-stu-id="c444d-144">Pros:</span></span><br/><br/><span data-ttu-id="c444d-145">更广泛的可用选项选择</span><span class="sxs-lookup"><span data-stu-id="c444d-145">Wider choice of options available</span></span><br/><span data-ttu-id="c444d-146">Fast 加载缓存时正确使用</span><span class="sxs-lookup"><span data-stu-id="c444d-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="c444d-147">多个选项很好地响应页面设计</span><span class="sxs-lookup"><span data-stu-id="c444d-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="c444d-148">缺点：</span><span class="sxs-lookup"><span data-stu-id="c444d-148">Cons:</span></span><br/><br/><span data-ttu-id="c444d-149">不会自动更新以反映网站结构</span><span class="sxs-lookup"><span data-stu-id="c444d-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="c444d-150">如果启用了安全修整对性能产生影响</span><span class="sxs-lookup"><span data-stu-id="c444d-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="c444d-151">缺点：</span><span class="sxs-lookup"><span data-stu-id="c444d-151">Cons:</span></span><br/><br/><span data-ttu-id="c444d-152">**不建议**</span><span class="sxs-lookup"><span data-stu-id="c444d-152">**Not recommended**</span></span><br/><span data-ttu-id="c444d-153">**影响性能和可伸缩性**</span><span class="sxs-lookup"><span data-stu-id="c444d-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="c444d-154">**受限制**</span><span class="sxs-lookup"><span data-stu-id="c444d-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="c444d-155">缺点：</span><span class="sxs-lookup"><span data-stu-id="c444d-155">Cons:</span></span><br/><br/><span data-ttu-id="c444d-156">不能轻松地对网站排序</span><span class="sxs-lookup"><span data-stu-id="c444d-156">No ability to easily order sites</span></span><br/><span data-ttu-id="c444d-157">需要对母版页进行自定义（需要具备技术技能）</span><span class="sxs-lookup"><span data-stu-id="c444d-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="c444d-158">缺点：</span><span class="sxs-lookup"><span data-stu-id="c444d-158">Cons:</span></span><br/><br/><span data-ttu-id="c444d-159">自定义开发，则需要</span><span class="sxs-lookup"><span data-stu-id="c444d-159">Custom development is required</span></span><br/><span data-ttu-id="c444d-160">外部数据源缓存存储所需 / 例如 Azure</span><span class="sxs-lookup"><span data-stu-id="c444d-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="c444d-p108">最适合您的网站的选项将取决于您的网站要求和您的技术功能。如果您希望可扩展开的导航提供程序，然后托管导航与禁用的安全修整是一个很好的选项。</span><span class="sxs-lookup"><span data-stu-id="c444d-p108">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span> 

<span data-ttu-id="c444d-p109">可以通过维护托管导航选项配置，不涉及代码自定义文件，并且会显著比结构的导航。如果需要安全修整和便于使用自定义母版页并维护更改可能出现的默认母版页中的 SharePoint Online 的组织中有一些功能，通过然后搜索驱动选项可能会产生更佳用户体验。如果您有更复杂的要求，自定义导航提供程序可能是正确的选择。不建议结构的导航。</span><span class="sxs-lookup"><span data-stu-id="c444d-p109">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation. If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience. If you have more complex requirements, then a custom navigation provider may be the right choice. Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="c444d-p110">最后，务必要注意 SharePoint 正在添加其他导航提供程序和功能利用多扁平的网站层次结构和使用 SharePoint 中心网站的中心辐射型模型的现代 SharePoint 网站体系结构。这将允许多个要实现的方案不需要使用 SharePoint 发布功能，并且这些导航配置经过优化以可伸缩性和 SharePoint Online 中的延迟。请注意，通常应用相同的原则-简化逼真的内容的结构，SharePoint 发布网站的总体结构的总体绩效有助于和以及缩放。这意味着，而不是让数以百计的网站 （子网站） 与单个网站集，更好的方法是有大量的网站集具有很少的子网站 （子网站）。</span><span class="sxs-lookup"><span data-stu-id="c444d-p110">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites. This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online. Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="c444d-171">在 SharePoint Online 中使用托管的导航和元数据</span><span class="sxs-lookup"><span data-stu-id="c444d-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="c444d-p111">托管的导航是功能的另一个开的选项，您可以使用重新创建大部分结构导航相同。可以配置托管元数据进行安全修整启用或禁用。配置与禁用的安全修整，托管的导航时非常高效加载所有的常量服务器呼叫数的导航链接。启用安全修整，但是，不具备的某些托管导航的优点和客户可以选择浏览以获得最佳性能和可伸缩性的自定义导航解决方案之一。</span><span class="sxs-lookup"><span data-stu-id="c444d-p111">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation. Managed metadata can be configured to have security trimming enabled or disabled. When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls. Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="c444d-p112">多个网站的导航结构通常是一致的网站的所有用户，不需要安全修整。如果禁用安全修整的链接添加到并非所有用户都有权访问的导航以及链接仍会显示，但将导致拒绝访问的消息。没有可以防止由于无意访问内容无风险。</span><span class="sxs-lookup"><span data-stu-id="c444d-p112">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site. If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message. There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="c444d-179">如何实现托管导航和结果</span><span class="sxs-lookup"><span data-stu-id="c444d-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="c444d-180">有一些文章 Docs.Microsoft.com 上有关托管导航的详细信息，例如，请参阅[Overview of SharePoint Server 中的托管导航](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)。</span><span class="sxs-lookup"><span data-stu-id="c444d-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="c444d-p113">为了实现托管的导航，您设置条款 Url 与对应的网站的导航结构。托管的导航可以甚至是手动 curated 替换在许多情况下的结构化导航。例如：</span><span class="sxs-lookup"><span data-stu-id="c444d-p113">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site. Managed navigation can even be manually curated to replace structural navigation in many cases. For example:</span></span>

![SharePoint Online 网站结构](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="c444d-185">下面的示例显示使用托管导航的复杂导航的性能。</span><span class="sxs-lookup"><span data-stu-id="c444d-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![使用托管的导航的复杂导航的性能](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="c444d-187">始终使用托管的导航可以提高性能与结构导航方法相比。</span><span class="sxs-lookup"><span data-stu-id="c444d-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="c444d-188">在 SharePoint Online 中使用结构导航</span><span class="sxs-lookup"><span data-stu-id="c444d-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="c444d-p114">这是默认情况下使用开的导航和是最简单的解决方案，但此类具有高性能权衡。它不需要任何自定义和非技术用户可以方便地添加项目、 隐藏项目，请从设置页管理导航。这是，但是也可以还方便地管理和控制以及与托管导航，因此建议使用托管导航作为 true 改进性能。</span><span class="sxs-lookup"><span data-stu-id="c444d-p114">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![具有选中显示子网站的结构导航](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="c444d-193">在 SharePoint Online 中启用结构导航</span><span class="sxs-lookup"><span data-stu-id="c444d-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="c444d-p115">为了说明如何使用结构导航和显示 SharePoint Online 标准解决方案中的性能子网站选项打开。下面是在**网站设置**页上找到的设置的屏幕截图\>**导航**。</span><span class="sxs-lookup"><span data-stu-id="c444d-p115">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![显示子网站的屏幕截图](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="c444d-197">分析 SharePoint Online 中的结构导航性能</span><span class="sxs-lookup"><span data-stu-id="c444d-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="c444d-198">若要分析 SharePoint 页的性能，请在 Internet Explorer 中使用 F12 开发人员工具的**网络**选项的卡。</span><span class="sxs-lookup"><span data-stu-id="c444d-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![显示 F12 开发工具“网络”选项卡的屏幕截图](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="c444d-200">在“网络”\*\*\*\* 选项卡，单击正在加载的 .aspx 页面，然后单击“详细信息”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c444d-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="c444d-201">![显示详细信息选项卡的屏幕截图](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="c444d-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="c444d-202">单击“响应头”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c444d-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="c444d-203">![“详细信息”选项卡的屏幕截图](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="c444d-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="c444d-204">SharePoint 返回其响应标头中的一些有用的诊断信息。</span><span class="sxs-lookup"><span data-stu-id="c444d-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="c444d-p116">信息的最有用部分之一是**SPRequestDuration**值，以毫秒为单位的时间长度请求处理所用的服务器上。在下面的屏幕快照**显示子网站**未选中的结构的导航。这意味着在全局导航中存在仅网站集的链接：</span><span class="sxs-lookup"><span data-stu-id="c444d-p116">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server. In the following screenshot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="c444d-208">![显示加载时间为请求持续时间的屏幕截图](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="c444d-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="c444d-p117">**SPRequestDuration**键的值为 245 毫秒。这表示返回请求所花的时间。由于在网站上只有一个导航项，这是如何 SharePoint Online 执行大流量的导航不好基准。下一步的屏幕截图显示了如何在子网站中添加影响此项。</span><span class="sxs-lookup"><span data-stu-id="c444d-p117">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="c444d-213">![显示请求持续时间为 2502 毫秒的屏幕截图](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="c444d-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="c444d-p118">添加子网站显著增加返回此相对简单示例网站页请求所花费的时间。复杂的网站层次结构，包括配置和其他拓扑选项页面导航窗格中，可以显著增加此影响进一步。</span><span class="sxs-lookup"><span data-stu-id="c444d-p118">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site. Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="c444d-216">使用搜索驱动的客户端脚本</span><span class="sxs-lookup"><span data-stu-id="c444d-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="c444d-p119">使用搜索，您可以利用使用连续爬网在后台建立索引。搜索结果来自搜索索引，并且的结果是安全修整。需要安全修整时，这是通常比开的导航提供程序。使用搜索结构导航，尤其是具有一个复杂的网站结构中，将加快页面加载时间显著。此通过托管导航的主要优点是受益于安全修整。</span><span class="sxs-lookup"><span data-stu-id="c444d-p119">Using search you can leverage the indexes that are built up in the background using continuous crawl. The search results are pulled from the search index and the results are security-trimmed. This is generally faster than out-of-the-box navigation providers when security trimming is required. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="c444d-p120">此方法包括创建自定义母版页和即开导航代码替换为自定义 HTML。按照此过程，按照下面的示例以替换该文件中的导航代码`seattle.html`。在此示例中，您将打开`seattle.html`文件并将整个元素`id=”DeltaTopNavigation”`与自定义 HTML 代码。</span><span class="sxs-lookup"><span data-stu-id="c444d-p120">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`. In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="c444d-225">示例： 母版页中的即开导航代码替换</span><span class="sxs-lookup"><span data-stu-id="c444d-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="c444d-226">导航到“网站设置”页面。</span><span class="sxs-lookup"><span data-stu-id="c444d-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="c444d-227">单击“母版页”\*\*\*\* 打开母版页样式库。</span><span class="sxs-lookup"><span data-stu-id="c444d-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="c444d-228">从此处导航库和下载文件`seattle.master`。</span><span class="sxs-lookup"><span data-stu-id="c444d-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="c444d-229">使用文本编辑器编辑代码，并删除下面的屏幕截图中的代码块。</span><span class="sxs-lookup"><span data-stu-id="c444d-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![删除所示的代码块](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="c444d-231">删除之间的代码`<SharePoint:AjaxDelta id=”DeltaTopNavigation”>`和`<\SharePoint:AjaxDelta>`标签，并将其替换为以下代码段：</span><span class="sxs-lookup"><span data-stu-id="c444d-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

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
<br/>
6. <span data-ttu-id="c444d-p121">替换中加载的 URL 图像开头，网站集加载图像的链接的定位标记。所做的更改后，重命名该文件，然后将其上载到母版页样式库。这会生成新的.master 文件。</span><span class="sxs-lookup"><span data-stu-id="c444d-p121">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="c444d-p122">此 HTML 是将使用从 JavaScript 代码返回的搜索结果填充的基本标记。您将需要编辑来更改 var 根的值的代码 ="网站集 URL"，如以下代码段中所示：</span><span class="sxs-lookup"><span data-stu-id="c444d-p122">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="c444d-p123">结果将分配给 self.nodes 数组和层次结构构建利用使用 linq.js 将输出分配给数组 self.hierarchy 对象。此数组是绑定到 HTML 的对象。这是通过将自我对象传递给 ko.applyBinding() 函数完成 toggleView() 函数中。</span><span class="sxs-lookup"><span data-stu-id="c444d-p123">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy. This array is the object that is bound to the HTML. This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="c444d-240">然后，这会导致要绑定到以下 HTML 的层次结构数组：</span><span class="sxs-lookup"><span data-stu-id="c444d-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="c444d-241">事件处理程序`mouseenter`和`mouseexit`添加到用于处理的子网站下拉列表菜单是完成中的顶级导航`addEventsToElements()`函数。</span><span class="sxs-lookup"><span data-stu-id="c444d-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="c444d-242">在我们复杂导航的示例，一个全新页面负载而无需从基准结构导航，若要获取的托管的导航方法类似结果已减少服务器上所用的时间本地缓存显示。</span><span class="sxs-lookup"><span data-stu-id="c444d-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="c444d-243">有关 JavaScript 文件...</span><span class="sxs-lookup"><span data-stu-id="c444d-243">About the JavaScript file...</span></span>

<span data-ttu-id="c444d-244">整个 JavaScript 文件如下所示：</span><span class="sxs-lookup"><span data-stu-id="c444d-244">The entire JavaScript file is as follows:</span></span>

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
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

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

            if (cachedNodes && timeStamp) {
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

            if (elem.children && elem.children.length > 0) {
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
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

<span data-ttu-id="c444d-p124">汇总中上述代码`jQuery $(document).ready`函数没有`viewModel object`创建然后`loadNavigationNodes()`调用该对象上的函数。此函数可以加载以前生成的导航层次结构存储在客户端浏览器的 HTML5 本地存储区或其调用函数`queryRemoteInterface()`。</span><span class="sxs-lookup"><span data-stu-id="c444d-p124">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="c444d-p125">`QueryRemoteInterface()`生成请求使用`getRequest()`，查询参数的函数之前在脚本中定义，然后从服务器返回数据。此数据是本质上一个数组作为数据传输对象处理各种属性所表示的网站集合中的所有网站。</span><span class="sxs-lookup"><span data-stu-id="c444d-p125">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="c444d-249">然后分析此数据到以前定义`SPO.Models.NavigationNode`对象使用`Knockout.js`创建数据绑定到我们之前定义的 HTML 的值用于可观察的属性。</span><span class="sxs-lookup"><span data-stu-id="c444d-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="c444d-p126">对象然后置于结果数组。分析到 JSON 使用 Knockout 和存储在将来的页面加载性能改进的本地浏览器存储在此数组。</span><span class="sxs-lookup"><span data-stu-id="c444d-p126">The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="c444d-252">此方法的优点</span><span class="sxs-lookup"><span data-stu-id="c444d-252">Benefits of this approach</span></span>

<span data-ttu-id="c444d-p127">[此方法](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)的一个主要好处是，通过使用 HTML5 本地存储，导航存储在本地用户的下次它们加载页。我们获得主要性能改进的结构导航; 使用 API 中的搜索但是，计一些技术的功能，能够执行和自定义此功能。</span><span class="sxs-lookup"><span data-stu-id="c444d-p127">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page. We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="c444d-p128">在[实现示例](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)中，网站进行排序的框结构导航; 相同的方式按字母顺序排列顺序。如果您想要偏离此顺序，它将为可进行更为复杂开发和维护。此外，通过此方法需要偏离受支持的母版页。如果不保留自定义母版页，您的网站会错过了解的更新和 Microsoft 向母版页的改进。</span><span class="sxs-lookup"><span data-stu-id="c444d-p128">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="c444d-259">[代码之上](#about-the-javascript-file)具有以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="c444d-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="c444d-260">jQuery-http://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="c444d-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="c444d-261">KnockoutJS-http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="c444d-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="c444d-262">Linq.js- http://linqjs.codeplex.com/，或 github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="c444d-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="c444d-p129">当前版本的 LinqJS 不包含上面的代码中使用 ByHierarchy 方法，并将中断导航代码。若要解决此问题，请将以下方法添加到行之前 Linq.js 文件`Flatten: function ()`。</span><span class="sxs-lookup"><span data-stu-id="c444d-p129">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

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
  
## <a name="related-topics"></a><span data-ttu-id="c444d-265">相关主题</span><span class="sxs-lookup"><span data-stu-id="c444d-265">Related topics</span></span>

[<span data-ttu-id="c444d-266">SharePoint Server 中的托管导航概述</span><span class="sxs-lookup"><span data-stu-id="c444d-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

