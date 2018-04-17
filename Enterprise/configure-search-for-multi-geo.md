---
title: 配置搜索业务多地区的 OneDrive
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解有关如何在多个地理环境中配置搜索。
ms.openlocfilehash: 5cf155c2c5bd2e27a54d84c4d5411e5b1afce568
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="49b42-103">配置搜索业务多地区的 OneDrive</span><span class="sxs-lookup"><span data-stu-id="49b42-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="49b42-104">组织可以在多地区 SharePoint 联机 (SPO) 环境中，有一个 Office 365 的租户，但将 SharePoint 内容存储在多个地理位置的一个中心位置以及一个或多个卫星地理位置。</span><span class="sxs-lookup"><span data-stu-id="49b42-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="49b42-p101">每个地理位置都有其自己的搜索索引和搜索中心。当用户搜索时，查询按扇形展开对所有索引，并返回的结果进行合并。</span><span class="sxs-lookup"><span data-stu-id="49b42-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="49b42-p102">例如，在一个地理位置的用户可以搜索内容存储在另一个地理位置，或只限于在不同地理位置的 SharePoint 网站上的内容。如果用户有权访问此内容，则搜索将显示结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="49b42-109">其中多地理环境中搜索客户端工作？</span><span class="sxs-lookup"><span data-stu-id="49b42-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="49b42-110">这些客户端可以从所有地理位置返回结果：</span><span class="sxs-lookup"><span data-stu-id="49b42-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="49b42-111">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="49b42-111">OneDrive for Business</span></span>

-   <span data-ttu-id="49b42-112">Delve</span><span class="sxs-lookup"><span data-stu-id="49b42-112">Delve</span></span>

-   <span data-ttu-id="49b42-113">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="49b42-113">The SharePoint home page</span></span>

-   <span data-ttu-id="49b42-114">搜索中心</span><span class="sxs-lookup"><span data-stu-id="49b42-114">The Search Center</span></span>

-   <span data-ttu-id="49b42-115">使用 SharePoint 搜索 API 的自定义搜索应用程序</span><span class="sxs-lookup"><span data-stu-id="49b42-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="49b42-116">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="49b42-116">OneDrive for Business</span></span>

<span data-ttu-id="49b42-117">只要多地理环境已设置，在 OneDrive 中搜索的用户从所有地理位置得到的结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="49b42-118">Delve</span><span class="sxs-lookup"><span data-stu-id="49b42-118">Delve</span></span>

<span data-ttu-id="49b42-119">只要多地理环境已设置，在 Delve 中搜索的用户从所有地理位置得到的结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="49b42-p103">Delve 将源和配置文件卡只显示在**中心**位置存储的文件的预览。对于卫星地理位置中存储的文件，该文件类型的图标显示。</span><span class="sxs-lookup"><span data-stu-id="49b42-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="49b42-122">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="49b42-122">The SharePoint home page</span></span>

<span data-ttu-id="49b42-p104">只要多地理环境具有设置，用户将看到新闻，最近和已跟随从其 SharePoint 主页上的多个地理位置的站点。如果他们在 SharePoint 的主页上使用的搜索框，它们将从多个地理位置获得合并的结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="49b42-125">搜索中心</span><span class="sxs-lookup"><span data-stu-id="49b42-125">The Search Center</span></span>

<span data-ttu-id="49b42-p105">多地理环境设置后，每个搜索中心从他们自己的地理位置会继续为只显示搜索结果。管理员必须[更改每个搜索中心的设置](#_Set_up_a_1)，以从所有地理位置得到的结果。随后，在搜索中心中搜索的用户从所有地理位置得到的结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="49b42-129">自定义搜索应用程序</span><span class="sxs-lookup"><span data-stu-id="49b42-129">Custom search applications</span></span>

<span data-ttu-id="49b42-p106">同往常一样，自定义搜索应用程序搜索索引通过使用现有的 SharePoint 搜索 REST Api 交互。若要从所有，或部分地理位置获得的结果，应用程序必须[调用 API 并包括新的多地理查询参数](#_Get_custom_search)在请求中。这会触发对所有地理位置查询出风扇。</span><span class="sxs-lookup"><span data-stu-id="49b42-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="49b42-133">关于搜索多地理环境中的不同是什么？</span><span class="sxs-lookup"><span data-stu-id="49b42-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="49b42-134">某些搜索功能，您可能很熟悉，在多个地理环境中的工作方式不同。</span><span class="sxs-lookup"><span data-stu-id="49b42-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="49b42-135"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="49b42-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="49b42-136"><strong>它是如何工作的</strong></span><span class="sxs-lookup"><span data-stu-id="49b42-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="49b42-137"><strong>解决方法</strong></span><span class="sxs-lookup"><span data-stu-id="49b42-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="49b42-138">升级的结果</span><span class="sxs-lookup"><span data-stu-id="49b42-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="49b42-p107">您可以使用不同级别的升级结果创建查询规则： 为整个租户、 网站集或网站。在多个地理环境中，定义<strong>租户</strong>级别提升的结果，如果您想要升级到<strong>所有</strong>地理位置搜索中心的结果。如果您<strong>只</strong>希望升级导致搜索中心网站集或网站的地理位置，定义<strong>站点集合</strong>或<strong>站点</strong>级别的结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="49b42-142">如果您不需要每个地理位置，例如不同的规则适合旅行，不同的升级的结果建议定义提升在组织级别的结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="49b42-143">精简搜索将</span><span class="sxs-lookup"><span data-stu-id="49b42-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="49b42-p108">搜索返回精简将所有租户的地理位置，然后将它们聚合。聚合是尽心尽力，意味着精简计数可能不 100%准确。对于大多数搜索驱动方案，此准确性就足够了。</span><span class="sxs-lookup"><span data-stu-id="49b42-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="49b42-147">对于搜索驱动的应用程序依赖于精选完整性，查询每个地理位置独立而无需使用多个 Geo 扇出。</span><span class="sxs-lookup"><span data-stu-id="49b42-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="49b42-148">多地区搜索不支持动态桶数字精简将。</span><span class="sxs-lookup"><span data-stu-id="49b42-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="49b42-149">对于数字的精简将使用<a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">"Discretize"参数</a>。</span><span class="sxs-lookup"><span data-stu-id="49b42-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="49b42-150">文档 Id</span><span class="sxs-lookup"><span data-stu-id="49b42-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="49b42-151">如果正在开发一个搜索驱动应用程序依赖于文档 Id，注意多地理环境中的文档 Id 不唯一跨地理位置，它们是唯一每个地理位置。</span><span class="sxs-lookup"><span data-stu-id="49b42-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="49b42-p109">我们已添加标识地理位置的列。使用此列来实现唯一性。这列被命名为"GeoLocationSource"。</span><span class="sxs-lookup"><span data-stu-id="49b42-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="49b42-155">结果数</span><span class="sxs-lookup"><span data-stu-id="49b42-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="49b42-156">搜索结果页面中显示合并的结果的地理位置，但不能超过 500 的结果页。</span><span class="sxs-lookup"><span data-stu-id="49b42-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="49b42-157">什么不支持多个地理环境中搜索？</span><span class="sxs-lookup"><span data-stu-id="49b42-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="49b42-158">在多个地理环境中不支持某些您可能非常熟悉，在搜索功能。</span><span class="sxs-lookup"><span data-stu-id="49b42-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="49b42-159"><strong>搜索功能</strong></span><span class="sxs-lookup"><span data-stu-id="49b42-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="49b42-160"><strong>备注</strong></span><span class="sxs-lookup"><span data-stu-id="49b42-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="49b42-161">仅限应用程序身份验证</span><span class="sxs-lookup"><span data-stu-id="49b42-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="49b42-162">仅限应用程序身份验证 （从服务的访问特权） 不支持在多个地区搜索。</span><span class="sxs-lookup"><span data-stu-id="49b42-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="49b42-163">来宾用户</span><span class="sxs-lookup"><span data-stu-id="49b42-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="49b42-164">来宾用户只能从地理位置，他们要从搜索得到的结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="49b42-165">如何搜索工作多地理环境中？</span><span class="sxs-lookup"><span data-stu-id="49b42-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="49b42-166">**所有**的搜索客户端使用现有 SharePoint 搜索 REST Api 进行交互与搜索索引。</span><span class="sxs-lookup"><span data-stu-id="49b42-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. <span data-ttu-id="49b42-167">搜索客户端调用搜索 REST 端点查询属性 EnableMultiGeoSearch = true。</span><span class="sxs-lookup"><span data-stu-id="49b42-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="49b42-168">查询被发送到组织中的所有地理位置。</span><span class="sxs-lookup"><span data-stu-id="49b42-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="49b42-169">从每个地理位置的搜索结果将合并和排名。</span><span class="sxs-lookup"><span data-stu-id="49b42-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="49b42-170">客户端获取统一的搜索结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-170">The client gets unified search results.</span></span>



<span data-ttu-id="49b42-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>请注意我们不合并搜索结果，直到我们已收到来自所有地理位置的结果。这意味着多地区搜索有额外延迟相比于只有一个地理位置与环境中的搜索。</span><span class="sxs-lookup"><span data-stu-id="49b42-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="49b42-173">获取搜索中心显示来自所有地理位置的结果</span><span class="sxs-lookup"><span data-stu-id="49b42-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="49b42-174">每个搜索中心有几个行业，您必须单独设置每个垂直。</span><span class="sxs-lookup"><span data-stu-id="49b42-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="49b42-175">请确保您执行这些步骤具有编辑搜索结果页面和搜索结果 Web 部件的权限的帐户。</span><span class="sxs-lookup"><span data-stu-id="49b42-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="49b42-176">导航到搜索结果页面 （请参见[列表](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213)的搜索结果页面）</span><span class="sxs-lookup"><span data-stu-id="49b42-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="49b42-p111">选择要设置，单击右上角，**设置**齿轮图标，然后单击**编辑页面**的垂直。在编辑模式下打开搜索结果页。</span><span class="sxs-lookup"><span data-stu-id="49b42-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo_image2.png)
1.  <span data-ttu-id="49b42-p112">在搜索结果 Web 部件中，将鼠标指针移动到上面，右上角的 Web 部件中，单击箭头，然后单击在菜单上的**编辑 Web 部件**。在功能区中打开搜索结果 Web 部件工具窗格页面右上角。![](media/configure-search-for-multi-geo_image3.png)</span><span class="sxs-lookup"><span data-stu-id="49b42-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo_image3.png)</span></span>

1.  <span data-ttu-id="49b42-181">在 Web 部件工具窗格的**设置**部分中的**结果控制设置**，请在下，选择**显示多个地区的结果**，得到的搜索结果 Web 部件以显示来自所有地理位置的结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="49b42-182">单击**确定**以保存所做的更改并关闭 Web 部件工具窗格。</span><span class="sxs-lookup"><span data-stu-id="49b42-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="49b42-183">检查主菜单的页面选项卡上单击**签入**到搜索结果 Web 部件所做的更改。</span><span class="sxs-lookup"><span data-stu-id="49b42-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="49b42-184">使用页面顶部的注释中提供的链接发布所做的更改。</span><span class="sxs-lookup"><span data-stu-id="49b42-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="49b42-185">获取自定义搜索应用程序，以显示来自所有或某些地理位置的结果</span><span class="sxs-lookup"><span data-stu-id="49b42-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="49b42-p113">自定义搜索应用程序通过使用 SharePoint 搜索 REST API 的请求指定查询参数来获得从所有，或部分，地理位置的结果。根据查询的参数中，查询是按扇形展开到所有的地理位置，或某些地理位置。例如，如果只需要查询地理位置即可找到相关信息的一个子集，您可以控制仅这些出风扇。如果请求成功，SharePoint 搜索 REST API 将返回的响应数据。</span><span class="sxs-lookup"><span data-stu-id="49b42-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="49b42-190">查询参数</span><span class="sxs-lookup"><span data-stu-id="49b42-190">Query parameters</span></span>

<span data-ttu-id="49b42-p114">EnableMultiGeoSearch-这是一个布尔值，指定是否查询应能按扇形展开到其他地理位置的多个地区组织的索引。将其设置为**true**以扇出查询。**假**以不扇出查询。默认值为**false**。如果不使用该参数，则查询**不**按扇形展开到其他地理位置。如果不是多个地区的环境中使用该参数，将忽略该参数。</span><span class="sxs-lookup"><span data-stu-id="49b42-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="49b42-p115">客户端类型-这是一个字符串。输入每个搜索应用程序的一个唯一的客户机名称。如果不使用该参数，则查询**不**按扇形展开到其他地理位置。</span><span class="sxs-lookup"><span data-stu-id="49b42-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="49b42-p116">MultiGeoSearchConfiguration-这是一个可选的列表，该列表的哪个地区在多个地理位置租户以扇出为****EnableMultiGeoSearch**情况**的查询。如果未包含此参数，或将其保留为空，该查询将按扇形展开到所有地理位置。对于每个地理位置，以 JSON 格式输入以下各项：</span><span class="sxs-lookup"><span data-stu-id="49b42-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="49b42-202">项目</span><span class="sxs-lookup"><span data-stu-id="49b42-202">Item</span></span></th>
<th align="left"><span data-ttu-id="49b42-203">说明</span><span class="sxs-lookup"><span data-stu-id="49b42-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="49b42-204">数据位置</span><span class="sxs-lookup"><span data-stu-id="49b42-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="49b42-205">地理位置，例如名称。</span><span class="sxs-lookup"><span data-stu-id="49b42-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="49b42-206">终结点</span><span class="sxs-lookup"><span data-stu-id="49b42-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="49b42-207">终结点来连接，例如https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="49b42-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="49b42-208">源 Id</span><span class="sxs-lookup"><span data-stu-id="49b42-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="49b42-209">结果源，例如 B81EAB55-3140 的 4312-B0F4-9459D1B4FFEE 的 GUID。</span><span class="sxs-lookup"><span data-stu-id="49b42-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="49b42-p117">如果省略数据位置或终结点，或者重复的数据的位置，则请求就会失败。[您可以获取有关租户的地理位置，通过使用 Microsoft Graph 的终结点信息](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery)。</span><span class="sxs-lookup"><span data-stu-id="49b42-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="49b42-212">响应数据</span><span class="sxs-lookup"><span data-stu-id="49b42-212">Response data</span></span>

<span data-ttu-id="49b42-p118">MultiGeoSearchStatus – 这是 SharePoint 搜索 API 对请求的响应中返回的属性。属性的值是一个字符串，并给出了 SharePoint 搜索 API 返回的结果有关的下列信息：</span><span class="sxs-lookup"><span data-stu-id="49b42-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="49b42-215">值</span><span class="sxs-lookup"><span data-stu-id="49b42-215">Value</span></span></th>
<th align="left"><span data-ttu-id="49b42-216">说明</span><span class="sxs-lookup"><span data-stu-id="49b42-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="49b42-217">完全</span><span class="sxs-lookup"><span data-stu-id="49b42-217">Full</span></span></td>
<td align="left"><span data-ttu-id="49b42-218">地理位置完全从<strong>所有</strong>的结果。</span><span class="sxs-lookup"><span data-stu-id="49b42-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="49b42-219">部分</span><span class="sxs-lookup"><span data-stu-id="49b42-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="49b42-p119">从一个或多个地理位置的部分结果。结果是由于暂时性错误而不完整的。</span><span class="sxs-lookup"><span data-stu-id="49b42-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="49b42-222">使用的 REST 服务查询</span><span class="sxs-lookup"><span data-stu-id="49b42-222">Query using the REST service</span></span>

<span data-ttu-id="49b42-p120">使用 GET 请求，可以在 URL 中指定查询参数。POST 请求，使用 JavaScript 对象符号 (JSON) 格式在正文中传递的查询参数。</span><span class="sxs-lookup"><span data-stu-id="49b42-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="49b42-225">请求标头</span><span class="sxs-lookup"><span data-stu-id="49b42-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="49b42-226">名称</span><span class="sxs-lookup"><span data-stu-id="49b42-226">Name</span></span></th>
<th align="left"><span data-ttu-id="49b42-227">值</span><span class="sxs-lookup"><span data-stu-id="49b42-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="49b42-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="49b42-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="49b42-229">应用程序/json; odata = 详细</span><span class="sxs-lookup"><span data-stu-id="49b42-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="49b42-230">按扇形展开到**所有**地理位置的示例 GET 请求</span><span class="sxs-lookup"><span data-stu-id="49b42-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="49b42-231">https://\<租户\>/\_api/搜索/query?querytext = 属性 sharepoint' = 'EnableMultiGeoSearch:true' 和客户端类型 =' 我\_客户端\_id</span><span class="sxs-lookup"><span data-stu-id="49b42-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="49b42-232">示例的 GET 请求以**某些**地理位置到扇出</span><span class="sxs-lookup"><span data-stu-id="49b42-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="49b42-233">https:// <tenant>/_api/search/query?querytext = 站点和客户端类型 = 'my_client_id' 和属性 ='EnableMultiGeoSearch:true、 MultiGeoSearchConfiguration: [{数据位置\:"名称"\,端点\:"https\:contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{数据位置\:"可以"\,端点\:"https\://contosoCAN.sharepoint-df.com"}]</span><span class="sxs-lookup"><span data-stu-id="49b42-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="49b42-234">按扇形展开到**所有**地理位置的示例 POST 请求</span><span class="sxs-lookup"><span data-stu-id="49b42-234">Sample POST request that’s fanned out to **all** geo locations</span></span>

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="49b42-235">按扇形展开到**一些**地理位置的示例 POST 请求</span><span class="sxs-lookup"><span data-stu-id="49b42-235">Sample POST request that’s fanned out to **some** geo locations</span></span>


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a><span data-ttu-id="49b42-236">使用 CSOM 查询</span><span class="sxs-lookup"><span data-stu-id="49b42-236">Query using CSOM</span></span>

<span data-ttu-id="49b42-237">下面是按扇形展开到**所有**地理位置的示例 CSOM 查询：</span><span class="sxs-lookup"><span data-stu-id="49b42-237">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

