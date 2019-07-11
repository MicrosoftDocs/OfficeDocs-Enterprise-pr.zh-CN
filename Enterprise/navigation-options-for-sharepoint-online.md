---
title: SharePoint Online 的导航选项
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: 本文介绍 SharePoint Online 中启用了 SharePoint 发布的导航选项网站。 导航的选择和配置会显著影响 SharePoint Online 中的网站的性能和可伸缩性。
ms.openlocfilehash: b3194009d21f60093ec80cb2e138df34df60e22e
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616855"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="7fd14-104">SharePoint Online 的导航选项</span><span class="sxs-lookup"><span data-stu-id="7fd14-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="7fd14-105">本文介绍 SharePoint Online 中启用了 SharePoint 发布的导航选项网站。</span><span class="sxs-lookup"><span data-stu-id="7fd14-105">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="7fd14-106">导航的选择和配置会显著影响 SharePoint Online 中的网站的性能和可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="7fd14-106">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="7fd14-107">概述</span><span class="sxs-lookup"><span data-stu-id="7fd14-107">Overview</span></span>

<span data-ttu-id="7fd14-108">导航提供程序配置会显著影响整个网站的性能, 并且必须仔细考虑选择一个导航提供程序和配置, 以便有效地扩展以满足 SharePoint 网站的要求。</span><span class="sxs-lookup"><span data-stu-id="7fd14-108">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="7fd14-109">有两个现成的导航提供程序, 以及自定义导航实现。</span><span class="sxs-lookup"><span data-stu-id="7fd14-109">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="7fd14-110">建议使用第一个选项 "[**托管 (元数据) 导航**](#using-managed-navigation-and-metadata-in-sharepoint-online)", 这是 SharePoint Online 中的默认选项之一;但是, 建议禁用安全修整, 除非需要。</span><span class="sxs-lookup"><span data-stu-id="7fd14-110">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="7fd14-111">将安全修整启用为此导航提供程序的默认安全设置;但是, 许多网站不需要安全修整的开销, 因为导航元素通常对网站的所有用户都是一致的。</span><span class="sxs-lookup"><span data-stu-id="7fd14-111">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="7fd14-112">使用建议的配置禁用安全修整后, 此导航提供程序不需要枚举网站结构, 且高度可扩展, 性能影响可接受。</span><span class="sxs-lookup"><span data-stu-id="7fd14-112">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="7fd14-113">第二个选项是[**结构导航**](#using-structural-navigation-in-sharepoint-online),**在 SHAREPOINT Online 中不是一个推荐的导航选项**。</span><span class="sxs-lookup"><span data-stu-id="7fd14-113">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**.</span></span> <span data-ttu-id="7fd14-114">此导航提供程序是为本地拓扑设计的, 在 SharePoint Online 中支持有限。</span><span class="sxs-lookup"><span data-stu-id="7fd14-114">This navigation provider was designed for an on-premises topology has limited support in SharePoint Online.</span></span> <span data-ttu-id="7fd14-115">虽然它提供了一些额外的功能集, 而不是其他导航选项, 但这些功能 (包括安全修整和网站结构枚举) 的成本是过多的服务器调用, 并且会在使用时影响可伸缩性和性能。</span><span class="sxs-lookup"><span data-stu-id="7fd14-115">While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used.</span></span> <span data-ttu-id="7fd14-116">使用占用过多资源的结构化导航的网站可能会受到限制。</span><span class="sxs-lookup"><span data-stu-id="7fd14-116">Sites using structured navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="7fd14-117">除了现成的导航提供程序之外, 许多客户还成功实现了替代的自定义导航实现。</span><span class="sxs-lookup"><span data-stu-id="7fd14-117">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="7fd14-118">自定义导航实现的一个常见类涵盖了用于存储导航节点的本地缓存的客户端呈现的设计模式。</span><span class="sxs-lookup"><span data-stu-id="7fd14-118">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span> <span data-ttu-id="7fd14-119">(请参阅本文中的**[搜索驱动的客户端脚本](#using-search-driven-client-side-scripting)**。)</span><span class="sxs-lookup"><span data-stu-id="7fd14-119">(See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="7fd14-120">这些导航提供程序具有以下几个主要优势:</span><span class="sxs-lookup"><span data-stu-id="7fd14-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="7fd14-121">它们通常适用于响应页面设计。</span><span class="sxs-lookup"><span data-stu-id="7fd14-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="7fd14-122">它们的可伸缩性和性能极高, 因为它们在呈现时无需资源成本 (并在超时后在后台进行刷新)。</span><span class="sxs-lookup"><span data-stu-id="7fd14-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="7fd14-123">这些导航提供程序可以使用各种策略检索导航数据, 范围从简单静态配置到各种动态数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="7fd14-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="7fd14-124">数据提供程序的一个示例是使用**搜索驱动的导航**, 这样可以灵活地枚举导航节点和有效处理安全修整。</span><span class="sxs-lookup"><span data-stu-id="7fd14-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="7fd14-125">有其他常用选项可用于生成**自定义导航提供程序**。</span><span class="sxs-lookup"><span data-stu-id="7fd14-125">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="7fd14-126">请查看[SharePoint Online 门户导航解决方案](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation), 以获取有关构建自定义导航提供程序的详细指南。</span><span class="sxs-lookup"><span data-stu-id="7fd14-126">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="7fd14-127">SharePoint Online 导航选项的优点和缺点</span><span class="sxs-lookup"><span data-stu-id="7fd14-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="7fd14-128">下表总结了每个选项的优点和缺点。</span><span class="sxs-lookup"><span data-stu-id="7fd14-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="7fd14-129">托管导航</span><span class="sxs-lookup"><span data-stu-id="7fd14-129">Managed navigation</span></span>  |<span data-ttu-id="7fd14-130">结构导航</span><span class="sxs-lookup"><span data-stu-id="7fd14-130">Structural navigation</span></span>  |<span data-ttu-id="7fd14-131">搜索驱动的导航</span><span class="sxs-lookup"><span data-stu-id="7fd14-131">Search-driven navigation</span></span>  |<span data-ttu-id="7fd14-132">自定义导航提供程序</span><span class="sxs-lookup"><span data-stu-id="7fd14-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="7fd14-133">供</span><span class="sxs-lookup"><span data-stu-id="7fd14-133">Pros:</span></span><br/><br/><span data-ttu-id="7fd14-134">易于维护</span><span class="sxs-lookup"><span data-stu-id="7fd14-134">Easy to maintain</span></span><br/><span data-ttu-id="7fd14-135">推荐选项</span><span class="sxs-lookup"><span data-stu-id="7fd14-135">Recommended option</span></span><br/>     |<span data-ttu-id="7fd14-136">供</span><span class="sxs-lookup"><span data-stu-id="7fd14-136">Pros:</span></span><br/><br/><span data-ttu-id="7fd14-137">易于配置</span><span class="sxs-lookup"><span data-stu-id="7fd14-137">Easy to configure</span></span><br/><span data-ttu-id="7fd14-138">安全修整</span><span class="sxs-lookup"><span data-stu-id="7fd14-138">Security trimmed</span></span><br/><span data-ttu-id="7fd14-139">添加内容时自动更新</span><span class="sxs-lookup"><span data-stu-id="7fd14-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="7fd14-140">供</span><span class="sxs-lookup"><span data-stu-id="7fd14-140">Pros:</span></span><br/><br/><span data-ttu-id="7fd14-141">安全修整</span><span class="sxs-lookup"><span data-stu-id="7fd14-141">Security trimmed</span></span><br/><span data-ttu-id="7fd14-142">添加网站时自动更新</span><span class="sxs-lookup"><span data-stu-id="7fd14-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="7fd14-143">快速加载时间和本地缓存导航结构</span><span class="sxs-lookup"><span data-stu-id="7fd14-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="7fd14-144">供</span><span class="sxs-lookup"><span data-stu-id="7fd14-144">Pros:</span></span><br/><br/><span data-ttu-id="7fd14-145">可用选项的更宽选择</span><span class="sxs-lookup"><span data-stu-id="7fd14-145">Wider choice of options available</span></span><br/><span data-ttu-id="7fd14-146">正确使用缓存时的快速加载</span><span class="sxs-lookup"><span data-stu-id="7fd14-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="7fd14-147">许多选项在使用快速响应页面设计时非常有效</span><span class="sxs-lookup"><span data-stu-id="7fd14-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="7fd14-148">消耗</span><span class="sxs-lookup"><span data-stu-id="7fd14-148">Cons:</span></span><br/><br/><span data-ttu-id="7fd14-149">不会自动更新以反映网站结构</span><span class="sxs-lookup"><span data-stu-id="7fd14-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="7fd14-150">如果启用了安全修整, 则会影响性能</span><span class="sxs-lookup"><span data-stu-id="7fd14-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="7fd14-151">消耗</span><span class="sxs-lookup"><span data-stu-id="7fd14-151">Cons:</span></span><br/><br/><span data-ttu-id="7fd14-152">**不建议**</span><span class="sxs-lookup"><span data-stu-id="7fd14-152">**Not recommended**</span></span><br/><span data-ttu-id="7fd14-153">**影响性能和可伸缩性**</span><span class="sxs-lookup"><span data-stu-id="7fd14-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="7fd14-154">**受限制的主题**</span><span class="sxs-lookup"><span data-stu-id="7fd14-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="7fd14-155">消耗</span><span class="sxs-lookup"><span data-stu-id="7fd14-155">Cons:</span></span><br/><br/><span data-ttu-id="7fd14-156">无法轻松订购网站</span><span class="sxs-lookup"><span data-stu-id="7fd14-156">No ability to easily order sites</span></span><br/><span data-ttu-id="7fd14-157">需要自定义母版页 (需要技术技能)</span><span class="sxs-lookup"><span data-stu-id="7fd14-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="7fd14-158">消耗</span><span class="sxs-lookup"><span data-stu-id="7fd14-158">Cons:</span></span><br/><br/><span data-ttu-id="7fd14-159">需要进行自定义开发</span><span class="sxs-lookup"><span data-stu-id="7fd14-159">Custom development is required</span></span><br/><span data-ttu-id="7fd14-160">需要存储外部数据源/缓存, 例如 Azure</span><span class="sxs-lookup"><span data-stu-id="7fd14-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="7fd14-161">最适合您的网站的选项取决于您的网站要求和您的技术能力。</span><span class="sxs-lookup"><span data-stu-id="7fd14-161">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="7fd14-162">如果您需要一个可扩展的现成导航提供程序, 则禁用安全修整的托管导航是一个非常不错的选择。</span><span class="sxs-lookup"><span data-stu-id="7fd14-162">If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span>

<span data-ttu-id="7fd14-163">托管导航选项可通过配置进行维护, 不涉及代码自定义文件, 并且比结构导航快得多。</span><span class="sxs-lookup"><span data-stu-id="7fd14-163">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation.</span></span> <span data-ttu-id="7fd14-164">如果您需要安全修整并且能够使用自定义母版页, 并且组织中有一些功能来维护在 SharePoint Online 的默认母版页中可能发生的更改, 则搜索驱动的选项可能会产生更好的效果用户体验。</span><span class="sxs-lookup"><span data-stu-id="7fd14-164">If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience.</span></span> <span data-ttu-id="7fd14-165">如果您具有更复杂的要求, 则自定义导航提供程序可能是正确的选择。</span><span class="sxs-lookup"><span data-stu-id="7fd14-165">If you have more complex requirements, then a custom navigation provider may be the right choice.</span></span> <span data-ttu-id="7fd14-166">不建议使用结构导航。</span><span class="sxs-lookup"><span data-stu-id="7fd14-166">Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="7fd14-167">最后, 请务必注意, SharePoint 正在为新式 SharePoint 网站体系结构添加更多导航提供程序和功能, 以利用更平展的网站层次结构和包含 SharePoint 中心网站的中心辐射型模型。</span><span class="sxs-lookup"><span data-stu-id="7fd14-167">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites.</span></span> <span data-ttu-id="7fd14-168">这允许实现许多不需要使用 SharePoint 发布功能的方案, 并且这些导航配置针对 SharePoint Online 中的可伸缩性和延迟进行了优化。</span><span class="sxs-lookup"><span data-stu-id="7fd14-168">This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online.</span></span> <span data-ttu-id="7fd14-169">请注意, 应用相同的原则-将 SharePoint 发布网站的整体结构简化为更简单的结构, 通常也有助于整体性能和规模的扩展。</span><span class="sxs-lookup"><span data-stu-id="7fd14-169">Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well.</span></span> <span data-ttu-id="7fd14-170">这意味着, 它不是拥有数百个网站 (子网站) 的单个网站集, 更好的方法是拥有很少子网站 (子网站) 的多个网站集。</span><span class="sxs-lookup"><span data-stu-id="7fd14-170">What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="7fd14-171">在 SharePoint Online 中使用托管导航和元数据</span><span class="sxs-lookup"><span data-stu-id="7fd14-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="7fd14-172">托管导航是另一个现成的选项, 您可以使用它来重新创建大部分与结构导航相同的功能。</span><span class="sxs-lookup"><span data-stu-id="7fd14-172">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="7fd14-173">可将托管元数据配置为启用或禁用安全修整。</span><span class="sxs-lookup"><span data-stu-id="7fd14-173">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="7fd14-174">在禁用安全修整的情况下进行配置时, 托管导航相当高效, 因为它会加载具有固定数量的服务器调用的所有导航链接。</span><span class="sxs-lookup"><span data-stu-id="7fd14-174">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="7fd14-175">但是, 启用安全修整会对托管导航的一些优势产生否定, 客户可以选择浏览其中一个自定义导航解决方案, 以实现最佳性能和可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="7fd14-175">Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="7fd14-176">许多网站不需要安全修整, 因为导航结构通常对网站的所有用户都是一致的。</span><span class="sxs-lookup"><span data-stu-id="7fd14-176">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="7fd14-177">如果禁用安全修整并向导航添加了一个不是所有用户都有权访问的链接, 则该链接仍将显示, 但会导致访问被拒绝消息。</span><span class="sxs-lookup"><span data-stu-id="7fd14-177">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="7fd14-178">对内容的意外访问没有风险。</span><span class="sxs-lookup"><span data-stu-id="7fd14-178">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="7fd14-179">如何实现托管导航和结果</span><span class="sxs-lookup"><span data-stu-id="7fd14-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="7fd14-180">有关托管导航的详细信息, 请参阅 Docs.Microsoft.com 的几篇文章, 例如, 请参阅[SharePoint Server 中的托管导航概述](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)。</span><span class="sxs-lookup"><span data-stu-id="7fd14-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="7fd14-181">为了实现托管导航, 请使用与网站的导航结构相对应的 Url 设置术语。</span><span class="sxs-lookup"><span data-stu-id="7fd14-181">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site.</span></span> <span data-ttu-id="7fd14-182">在许多情况下, 甚至可以手动 curated 托管导航以替换结构导航。</span><span class="sxs-lookup"><span data-stu-id="7fd14-182">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="7fd14-183">例如：</span><span class="sxs-lookup"><span data-stu-id="7fd14-183">For example:</span></span>

![SharePoint Online 网站结构](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="7fd14-185">下面的示例展示了使用托管导航的复杂导航的性能。</span><span class="sxs-lookup"><span data-stu-id="7fd14-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![使用托管导航的复杂导航的性能](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="7fd14-187">与结构导航方法相比, 使用托管导航可一致地提高性能。</span><span class="sxs-lookup"><span data-stu-id="7fd14-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="7fd14-188">在 SharePoint Online 中使用结构导航</span><span class="sxs-lookup"><span data-stu-id="7fd14-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="7fd14-189">这是默认情况下使用的现成导航, 它是最简单的解决方案, 但这是一种昂贵的性能平衡。</span><span class="sxs-lookup"><span data-stu-id="7fd14-189">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off.</span></span> <span data-ttu-id="7fd14-190">它不需要任何自定义设置, 非技术性用户也可以轻松地添加项目、隐藏项目以及从 "设置" 页面管理导航。</span><span class="sxs-lookup"><span data-stu-id="7fd14-190">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="7fd14-191">这也适用于托管导航, 因此建议使用托管导航, 因为也可以轻松地管理和控制这些功能, 并提高性能。</span><span class="sxs-lookup"><span data-stu-id="7fd14-191">This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![选择了 "显示子网站" 的结构导航](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="7fd14-193">在 SharePoint Online 中打开结构导航</span><span class="sxs-lookup"><span data-stu-id="7fd14-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="7fd14-194">演示如何在结构化导航和 "显示子网站" 选项处于打开状态的标准 SharePoint Online 解决方案中进行性能。</span><span class="sxs-lookup"><span data-stu-id="7fd14-194">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on.</span></span> <span data-ttu-id="7fd14-195">下面是在 "页面**网站设置** \> "**导航**中找到的设置的屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="7fd14-195">Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![显示子网站的屏幕截图](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="7fd14-197">在 SharePoint Online 中分析结构导航性能</span><span class="sxs-lookup"><span data-stu-id="7fd14-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="7fd14-198">若要分析 SharePoint 页面的性能, 请使用 Internet Explorer 中的 F12 开发人员工具的 "**网络**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7fd14-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![显示 F12 开发工具“网络”选项卡的屏幕截图](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="7fd14-200">在 "**网络**" 选项卡上, 单击要加载的 .aspx 页面, 然后单击 "**详细信息**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7fd14-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="7fd14-201">![显示详细信息选项卡的屏幕截图](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="7fd14-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="7fd14-202">单击 "**响应头**"。</span><span class="sxs-lookup"><span data-stu-id="7fd14-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="7fd14-203">![“详细信息”选项卡的屏幕截图](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="7fd14-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="7fd14-204">SharePoint 在其响应标头中返回一些有用的诊断信息。</span><span class="sxs-lookup"><span data-stu-id="7fd14-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="7fd14-205">最有用的信息片段之一是**SPRequestDuration** , 这是在服务器上处理请求所需时间的值 (以毫秒为单位)。</span><span class="sxs-lookup"><span data-stu-id="7fd14-205">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> <span data-ttu-id="7fd14-206">在以下屏幕截图中, 将取消选中结构导航的**子网站**。</span><span class="sxs-lookup"><span data-stu-id="7fd14-206">In the following screenshot **show subsites** is unchecked for the structural navigation.</span></span> <span data-ttu-id="7fd14-207">这意味着全局导航中只有 "网站集" 链接:</span><span class="sxs-lookup"><span data-stu-id="7fd14-207">This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="7fd14-208">![显示加载时间为请求持续时间的屏幕截图](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="7fd14-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="7fd14-209">**SPRequestDuration**项的值为245毫秒。</span><span class="sxs-lookup"><span data-stu-id="7fd14-209">The **SPRequestDuration** key has a value of 245 milliseconds.</span></span> <span data-ttu-id="7fd14-210">这表示返回请求所花的时间。</span><span class="sxs-lookup"><span data-stu-id="7fd14-210">This represents the time it took to return the request.</span></span> <span data-ttu-id="7fd14-211">由于网站上只有一个导航项, 因此这是在不进行大量导航的情况下, SharePoint Online 执行方式的一个很好的基准。</span><span class="sxs-lookup"><span data-stu-id="7fd14-211">Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation.</span></span> <span data-ttu-id="7fd14-212">下一个屏幕截图显示了如何将子网站中的添加影响此项。</span><span class="sxs-lookup"><span data-stu-id="7fd14-212">The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="7fd14-213">![显示请求持续时间为 2502 毫秒的屏幕截图](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="7fd14-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="7fd14-214">添加子网站会显著增加为此相对简单的示例网站返回页面请求所需的时间。</span><span class="sxs-lookup"><span data-stu-id="7fd14-214">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site.</span></span> <span data-ttu-id="7fd14-215">复杂的网站层次结构 (包括导航中的页面) 和其他配置和拓扑选项可能会显著增加此影响。</span><span class="sxs-lookup"><span data-stu-id="7fd14-215">Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="7fd14-216">使用搜索驱动的客户端脚本</span><span class="sxs-lookup"><span data-stu-id="7fd14-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="7fd14-217">使用搜索可以利用连续爬网在后台中构建的索引。</span><span class="sxs-lookup"><span data-stu-id="7fd14-217">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="7fd14-218">搜索结果从搜索索引中提取, 结果将进行安全修整。</span><span class="sxs-lookup"><span data-stu-id="7fd14-218">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="7fd14-219">当需要安全修整时, 这通常比现成的导航提供程序更快。</span><span class="sxs-lookup"><span data-stu-id="7fd14-219">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="7fd14-220">使用搜索结构导航, 尤其是在您有复杂的网站结构时, 将会显著加快页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="7fd14-220">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="7fd14-221">此优先于托管导航的主要优势是, 您可以从安全修整中获益。</span><span class="sxs-lookup"><span data-stu-id="7fd14-221">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="7fd14-222">此方法涉及到创建自定义母版页并将现成的导航代码替换为自定义 HTML。</span><span class="sxs-lookup"><span data-stu-id="7fd14-222">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="7fd14-223">按照以下示例中概述的此过程操作, 以替换文件`seattle.html`中的导航代码。</span><span class="sxs-lookup"><span data-stu-id="7fd14-223">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="7fd14-224">在此示例中, 将打开`seattle.html`文件, 并将整个元素`id=”DeltaTopNavigation”`替换为自定义 HTML 代码。</span><span class="sxs-lookup"><span data-stu-id="7fd14-224">In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="7fd14-225">示例: 将现成的导航代码替换为母版页</span><span class="sxs-lookup"><span data-stu-id="7fd14-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="7fd14-226">导航到 "网站设置" 页。</span><span class="sxs-lookup"><span data-stu-id="7fd14-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="7fd14-227">通过单击 "**母版页**" 打开母版页样式库。</span><span class="sxs-lookup"><span data-stu-id="7fd14-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="7fd14-228">从这里, 您可以在库中导航并下载该`seattle.master`文件。</span><span class="sxs-lookup"><span data-stu-id="7fd14-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="7fd14-229">使用文本编辑器编辑代码, 并删除以下屏幕截图中的代码块。</span><span class="sxs-lookup"><span data-stu-id="7fd14-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![删除显示的代码块](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="7fd14-231">删除`<SharePoint:AjaxDelta id=”DeltaTopNavigation”>`和`<\SharePoint:AjaxDelta>`标记之间的代码, 并将其替换为以下代码段:</span><span class="sxs-lookup"><span data-stu-id="7fd14-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

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
6. <span data-ttu-id="7fd14-232">使用网站集中加载图像的链接替换开头的加载图像定位标记中的 URL。</span><span class="sxs-lookup"><span data-stu-id="7fd14-232">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="7fd14-233">进行更改后, 请重命名该文件, 然后将其上传到母版页样式库。</span><span class="sxs-lookup"><span data-stu-id="7fd14-233">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="7fd14-234">这将生成一个新的 .master 文件。</span><span class="sxs-lookup"><span data-stu-id="7fd14-234">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="7fd14-235">此 HTML 是由 JavaScript 代码返回的搜索结果将填充的基本标记。</span><span class="sxs-lookup"><span data-stu-id="7fd14-235">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="7fd14-236">您需要编辑代码以更改 var root = "网站集 URL" 的值, 如以下代码段所示:</span><span class="sxs-lookup"><span data-stu-id="7fd14-236">You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="7fd14-237">将结果分配给 self. 节点数组, 并使用使用 linq 将输出分配给数组 self 层次结构的对象生成层次结构。</span><span class="sxs-lookup"><span data-stu-id="7fd14-237">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="7fd14-238">此数组是绑定到 HTML 的对象。</span><span class="sxs-lookup"><span data-stu-id="7fd14-238">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="7fd14-239">这是通过将 self 对象传递给 applyBinding () 函数在 toggleView () 函数中完成的。</span><span class="sxs-lookup"><span data-stu-id="7fd14-239">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="7fd14-240">然后, 这会将层次结构数组绑定到以下 HTML:</span><span class="sxs-lookup"><span data-stu-id="7fd14-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="7fd14-241">和的事件处理程序将被添加到顶级导航中, 以处理在`addEventsToElements()`函数中完成的子网站下拉菜单。 `mouseexit` `mouseenter`</span><span class="sxs-lookup"><span data-stu-id="7fd14-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="7fd14-242">在复杂的导航示例中, 没有本地缓存的新页面加载将显示服务器上所用的时间已从基准结构导航中减少, 以获取与托管导航方法类似的结果。</span><span class="sxs-lookup"><span data-stu-id="7fd14-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="7fd14-243">有关 JavaScript 文件 .。。</span><span class="sxs-lookup"><span data-stu-id="7fd14-243">About the JavaScript file...</span></span>

<span data-ttu-id="7fd14-244">整个 JavaScript 文件如下所示:</span><span class="sxs-lookup"><span data-stu-id="7fd14-244">The entire JavaScript file is as follows:</span></span>

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

<span data-ttu-id="7fd14-245">若要汇总上面的`jQuery $(document).ready`函数中显示的`viewModel object`代码, 则表示已创建, `loadNavigationNodes()`然后调用该对象上的函数。</span><span class="sxs-lookup"><span data-stu-id="7fd14-245">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="7fd14-246">此函数会加载以前在客户端浏览器的 HTML5 本地存储中存储的导航层次结构, 或者调用该`queryRemoteInterface()`函数。</span><span class="sxs-lookup"><span data-stu-id="7fd14-246">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="7fd14-247">`QueryRemoteInterface()`生成一个请求, 并`getRequest()`将该函数与脚本中先前定义的查询参数一起使用, 然后从服务器返回数据。</span><span class="sxs-lookup"><span data-stu-id="7fd14-247">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="7fd14-248">此数据实质上是网站集中所有网站的数组, 这些网站表示为具有各种属性的数据传输对象。</span><span class="sxs-lookup"><span data-stu-id="7fd14-248">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="7fd14-249">然后, 将此数据解析为之前定义`SPO.Models.NavigationNode`的对象, `Knockout.js`这些对象使用创建可观察到的属性以供将值绑定到我们之前定义的 HTML 中的数据。</span><span class="sxs-lookup"><span data-stu-id="7fd14-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="7fd14-250">然后, 将这些对象放入结果数组中。</span><span class="sxs-lookup"><span data-stu-id="7fd14-250">The objects are then put into a results array.</span></span> <span data-ttu-id="7fd14-251">使用挖空将此数组解析为 JSON, 并将其存储在本地浏览器存储中, 以改进将来页面加载的性能。</span><span class="sxs-lookup"><span data-stu-id="7fd14-251">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="7fd14-252">此方法的优点</span><span class="sxs-lookup"><span data-stu-id="7fd14-252">Benefits of this approach</span></span>

<span data-ttu-id="7fd14-253">[此方法](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)的一个主要优点是, 通过使用 HTML5 本地存储, 在下次加载页面时, 将为用户本地存储导航。</span><span class="sxs-lookup"><span data-stu-id="7fd14-253">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="7fd14-254">我们从使用搜索 API 进行结构导航中获得重大性能改进;但是, 它需要一些技术功能来执行和自定义此功能。</span><span class="sxs-lookup"><span data-stu-id="7fd14-254">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="7fd14-255">在[示例实现](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)中, 网站的排序方式与开箱即用的结构导航相同;字母顺序。</span><span class="sxs-lookup"><span data-stu-id="7fd14-255">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="7fd14-256">如果您想要与此订单有偏离之处, 则开发和维护会更复杂。</span><span class="sxs-lookup"><span data-stu-id="7fd14-256">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="7fd14-257">此外, 此方法还需要您从受支持的母版页中偏离。</span><span class="sxs-lookup"><span data-stu-id="7fd14-257">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="7fd14-258">如果不维护自定义母版页, 则网站将错过 Microsoft 对母版页所做的更新和改进。</span><span class="sxs-lookup"><span data-stu-id="7fd14-258">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="7fd14-259">[上面的代码](#about-the-javascript-file)具有以下依赖项:</span><span class="sxs-lookup"><span data-stu-id="7fd14-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="7fd14-260">jQueryhttp://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="7fd14-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="7fd14-261">KnockoutJS -http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="7fd14-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="7fd14-262">http://linqjs.codeplex.com/Linq 或 github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="7fd14-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="7fd14-263">当前版本的 LinqJS 不包含在上面的代码中使用的 ByHierarchy 方法, 将断开导航代码。</span><span class="sxs-lookup"><span data-stu-id="7fd14-263">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="7fd14-264">若要解决此问题, 请将以下方法添加到行`Flatten: function ()`之前的 Linq 文件中。</span><span class="sxs-lookup"><span data-stu-id="7fd14-264">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

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
  
## <a name="related-topics"></a><span data-ttu-id="7fd14-265">相关主题</span><span class="sxs-lookup"><span data-stu-id="7fd14-265">Related topics</span></span>

[<span data-ttu-id="7fd14-266">SharePoint Server 中的托管导航概述</span><span class="sxs-lookup"><span data-stu-id="7fd14-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

