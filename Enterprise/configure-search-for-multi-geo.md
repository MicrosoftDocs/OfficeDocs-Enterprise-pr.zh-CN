---
title: 为 OneDrive for Business 多地理位置配置搜索
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何在多地理位置环境中配置搜索。
ms.openlocfilehash: 5ca2a35385ab2c246b78dc8811e8435bbdec25c7
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849908"
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="27bea-103">为 OneDrive for Business 多地理位置配置搜索</span><span class="sxs-lookup"><span data-stu-id="27bea-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="27bea-104">在 OneDrive for Business 多地理位置环境中，一个组织可以具有一个 Office 365 租户，但可在多个地理位置存储其 OneDrive 内容 - 一个中央位置和一个或多个附属位置。</span><span class="sxs-lookup"><span data-stu-id="27bea-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="27bea-p101">每个地理位置都有其各自的搜索索引和搜索中心。在用户搜索时，查询会扇出所有索引，并合并返回的结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="27bea-p102">例如，位于一个地理位置的用户可以搜索在另一个地理位置中存储的内容，也可以搜索只限不同地理位置的 SharePoint 网站内容。如果用户有访问此内容的权限，则搜索将显示结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="27bea-109">在多地理位置环境中可以运行哪些搜索客户端？</span><span class="sxs-lookup"><span data-stu-id="27bea-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="27bea-110">这些客户端可以返回来自所有地理位置的结果：</span><span class="sxs-lookup"><span data-stu-id="27bea-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="27bea-111">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="27bea-111">OneDrive for Business</span></span>

-   <span data-ttu-id="27bea-112">Delve</span><span class="sxs-lookup"><span data-stu-id="27bea-112">Delve</span></span>

-   <span data-ttu-id="27bea-113">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="27bea-113">The SharePoint home page</span></span>

-   <span data-ttu-id="27bea-114">搜索中心</span><span class="sxs-lookup"><span data-stu-id="27bea-114">The Search Center</span></span>

-   <span data-ttu-id="27bea-115">使用 SharePoint 搜索 API 的自定义搜索应用程序</span><span class="sxs-lookup"><span data-stu-id="27bea-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="27bea-116">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="27bea-116">OneDrive for Business</span></span>

<span data-ttu-id="27bea-117">多地理位置环境一旦设置，在 OneDrive 中搜索的用户即可获得来自所有地理位置的结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="27bea-118">Delve</span><span class="sxs-lookup"><span data-stu-id="27bea-118">Delve</span></span>

<span data-ttu-id="27bea-119">多地理位置环境一旦设置，在 Delve 中搜索的用户即可获得来自所有地理位置的结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="27bea-p103">Delve 源和个人资料卡片只能显示存储在**中央**位置中的文件预览。对于存储在附属位置的文件，将改为显示文件类型的图标。</span><span class="sxs-lookup"><span data-stu-id="27bea-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="27bea-122">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="27bea-122">The SharePoint home page</span></span>

<span data-ttu-id="27bea-p104">多地理位置环境一旦设置，用户即可在其 SharePoint 主页上看到来自多地理位置的资讯、最近访问和关注的网站。如果他们使用 SharePoint 主页上的搜索框，则他们将获得来自多地理位置的合并结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="27bea-125">搜索中心</span><span class="sxs-lookup"><span data-stu-id="27bea-125">The Search Center</span></span>

<span data-ttu-id="27bea-p105">多地理位置环境设置后，每个搜索中心将继续仅显示来自其各自地理位置的结果。管理员必须[更改每个搜索中心的设置](#_Set_up_a_1)，以获取来自所有地理位置的结果。之后，在搜索中心搜索的用户将获得来自所有地理位置的结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="27bea-129">自定义搜索应用程序</span><span class="sxs-lookup"><span data-stu-id="27bea-129">Custom search applications</span></span>

<span data-ttu-id="27bea-p106">同样，自定义搜索应用程序使用现有 SharePoint Search REST API 与搜索索引进行交互。若要获取来自所有（或部分）地理位置的结果，应用程序必须在请求中[调用 API 并包含新的多地理位置查询参数](#_Get_custom_search)。这将触发对所有地理位置的查询扇出。</span><span class="sxs-lookup"><span data-stu-id="27bea-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="27bea-133">在多地理位置环境中搜索有什么不同之处？</span><span class="sxs-lookup"><span data-stu-id="27bea-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="27bea-134">你所熟悉的某些搜索功能在多地理位置环境中的工作方式可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="27bea-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="27bea-135"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="27bea-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="27bea-136"><strong>功能的运行方式</strong></span><span class="sxs-lookup"><span data-stu-id="27bea-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="27bea-137"><strong>解决方法</strong></span><span class="sxs-lookup"><span data-stu-id="27bea-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="27bea-138">升级的结果</span><span class="sxs-lookup"><span data-stu-id="27bea-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="27bea-p107">你可以在不同级别使用升级的结果来创建查询规则：针对整个租户、针对网站集或针对网站。在多地理位置环境中，如果想要将结果升级到<strong>所有</strong>地理位置中的搜索中心，请在<strong></strong>“租户”级别定义升级的结果。如果<strong>只</strong>想在位于网站集或网站的地理位置中的搜索中心升级结果，请在“网站集”<strong></strong>或“网站”<strong></strong>级别定义结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="27bea-142">如果不需要对每个地理位置使用不同的升级结果（例如，在出差时使用不同的规则），我们建议在租户级别定义升级的结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="27bea-143">搜索精简</span><span class="sxs-lookup"><span data-stu-id="27bea-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="27bea-p108">搜索将返回来自租户的所有地理位置的精简内容，然后对其进行聚合。聚合是最佳做法，意味着精简计数可能并非 100% 准确。对于大部分搜索驱动的方案，此准确度已足够。 </span><span class="sxs-lookup"><span data-stu-id="27bea-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient. </span></span></td>
<td align="left"><span data-ttu-id="27bea-147">对于依赖于精简完整度的搜索驱动的应用程序，在不使用多地理位置扇出的情况下单独查询每个地理位置。</span><span class="sxs-lookup"><span data-stu-id="27bea-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="27bea-148">多地理位置搜索不支持数值精简的动态存储桶。</span><span class="sxs-lookup"><span data-stu-id="27bea-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="27bea-149">对于数值精简，请使用<a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize”参数</a>。</span><span class="sxs-lookup"><span data-stu-id="27bea-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="27bea-150">文档 ID</span><span class="sxs-lookup"><span data-stu-id="27bea-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="27bea-151">如果正在开发依赖于文档 ID 的搜索驱动的应用程序，请注意，多地理位置环境中的文档 ID 对所有地理位置来说并不是唯一的，它们只对每个地理位置来说是唯一的。</span><span class="sxs-lookup"><span data-stu-id="27bea-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="27bea-p109">我们已添加了标识地理位置的列。使用此列来实现唯一性。此列被称为“GeoLocationSource”。</span><span class="sxs-lookup"><span data-stu-id="27bea-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="27bea-155">结果数</span><span class="sxs-lookup"><span data-stu-id="27bea-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="27bea-156">搜索结果页将显示来自地理位置的组合结果，但该页显示的结果不能超过 500 个。</span><span class="sxs-lookup"><span data-stu-id="27bea-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="27bea-157">在多地理位置环境中不支持的搜索有哪些？</span><span class="sxs-lookup"><span data-stu-id="27bea-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="27bea-158">你所熟悉的某些搜索功能在多地理位置环境中可能不受支持。</span><span class="sxs-lookup"><span data-stu-id="27bea-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="27bea-159"><strong>搜索功能</strong></span><span class="sxs-lookup"><span data-stu-id="27bea-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="27bea-160"><strong>注意</strong></span><span class="sxs-lookup"><span data-stu-id="27bea-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="27bea-161">仅应用身份验证</span><span class="sxs-lookup"><span data-stu-id="27bea-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="27bea-162">在多地理位置搜索中不支持仅应用身份验证（来自服务的特权访问）。</span><span class="sxs-lookup"><span data-stu-id="27bea-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="27bea-163">来宾用户</span><span class="sxs-lookup"><span data-stu-id="27bea-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="27bea-164">来宾用户仅获得其搜索的地理位置中的结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="27bea-165">如何在多地理位置环境中进行搜索？</span><span class="sxs-lookup"><span data-stu-id="27bea-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="27bea-166">\*\*\*\* 所有搜索客户端均使用现有 SharePoint Search REST API 与搜索索引进行交互。</span><span class="sxs-lookup"><span data-stu-id="27bea-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<img src="media/configure-search-for-multi-geo-image1-1.png" />

1. <span data-ttu-id="27bea-167">搜索客户端使用查询属性 EnableMultiGeoSearch= true 来调用搜索 REST 终结点。</span><span class="sxs-lookup"><span data-stu-id="27bea-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="27bea-168">查询将被发送到租户中的所有地理位置。</span><span class="sxs-lookup"><span data-stu-id="27bea-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="27bea-169">将对来自每个地理位置的搜索结果进行合并和排名。</span><span class="sxs-lookup"><span data-stu-id="27bea-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="27bea-170">客户端将获得统一的搜索结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-170">The client gets unified search results.</span></span>



<span data-ttu-id="27bea-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>注意：在收到来自所有地理位置的结果前，我们不会合并搜索结果。这意味着，与在仅有一个地理位置的环境中的搜索相比，多地理位置搜索具有额外的延迟性。</span><span class="sxs-lookup"><span data-stu-id="27bea-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="27bea-173">获取搜索中心以显示来自所有地理位置的结果</span><span class="sxs-lookup"><span data-stu-id="27bea-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="27bea-174">每个搜索中心具有多个类别，必须单独设置每个类别。</span><span class="sxs-lookup"><span data-stu-id="27bea-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="27bea-175">请确保执行这些步骤所使用的帐户具有编辑搜索结果页和搜索结果 Web 部件的权限。</span><span class="sxs-lookup"><span data-stu-id="27bea-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="27bea-176">导航到搜索结果页（请参阅搜索结果页的[列表](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213)）</span><span class="sxs-lookup"><span data-stu-id="27bea-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="27bea-p111">选择要设置的类别，单击右上角的“设置”\*\*\*\* 齿轮图标，然后单击“编辑页面”\*\*\*\*。搜索结果页将在编辑模式下打开。</span><span class="sxs-lookup"><span data-stu-id="27bea-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo-image2.png)
1.  <span data-ttu-id="27bea-p112">在搜索结果 Web 部件中，将指针移至 Web 部件的右上角，单击箭头，然后单击菜单上的“编辑 Web 部件”\*\*\*\*。“搜索结果 Web 部件”工具窗格将在页面右上角的功能区下方打开。![](media/configure-search-for-multi-geo-image3.png)</span><span class="sxs-lookup"><span data-stu-id="27bea-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo-image3.png)</span></span>

1.  <span data-ttu-id="27bea-181">在 Web 部件工具窗格中的“设置”\*\*\*\* 部分，在“结果控制设置”\*\*\*\* 下，选择“显示多地理位置结果”\*\*\*\*，获取搜索结果 Web 部件，以显示来自所有地理位置的结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="27bea-182">单击“确定”\*\*\*\*，以保存更改并关闭 Web 部件工具窗格。</span><span class="sxs-lookup"><span data-stu-id="27bea-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="27bea-183">单击主菜单“页面”选项卡上的“签入”\*\*\*\*，查看对搜索结果 Web 部件所做的更改。</span><span class="sxs-lookup"><span data-stu-id="27bea-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="27bea-184">使用页面顶部的注释中提供的链接来发布更改。</span><span class="sxs-lookup"><span data-stu-id="27bea-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="27bea-185">获取自定义搜索应用程序，以显示来自所有（或部分）地理位置的结果</span><span class="sxs-lookup"><span data-stu-id="27bea-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="27bea-p113">自定义搜索应用程序通过指定对 SharePoint Search REST API 的请求的查询参数获取来自所有（或部分）地理位置的结果。根据查询参数，查询将被扇出到所有（或部分）地理位置。例如，如果只需要查询地理位置的子集来查找相关信息，可以控制仅扇出到这些子集。如果请求成功，则 SharePoint Search REST API 将返回响应数据。</span><span class="sxs-lookup"><span data-stu-id="27bea-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="27bea-190">查询参数</span><span class="sxs-lookup"><span data-stu-id="27bea-190">Query parameters</span></span>

<span data-ttu-id="27bea-p114">EnableMultiGeoSearch - 这是一个布尔值，指定是否应将查询扇出到多地理位置租户的其他地理位置的索引。将其设置为 **true** 可扇出查询；将其设置为 **false** 则不扇出查询。默认值为 **false**。如未包含此参数，则查询\*\*\*\* 不会被扇出到其他地理位置。如果在不是多地理位置的环境中使用该参数，则该参数将被忽略。</span><span class="sxs-lookup"><span data-stu-id="27bea-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="27bea-p115">ClientType - 这是一个字符串。为每个搜索应用程序输入唯一客户端名称。如果未包含此参数，则该查询不会\*\*\*\* 被扇出到其他地理位置。</span><span class="sxs-lookup"><span data-stu-id="27bea-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="27bea-p116">MultiGeoSearchConfiguration - 这是一个可选列表，显示当 **EnableMultiGeoSearch** 为 **true** 时在多地理位置租户中要将查询扇出到的地理位置。如果未包含此参数，或将其留空，则查询将被扇出到所有地理位置。对于每个地理位置，请使用 JSON 格式输入以下项：</span><span class="sxs-lookup"><span data-stu-id="27bea-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="27bea-202">Item</span><span class="sxs-lookup"><span data-stu-id="27bea-202">Item</span></span></th>
<th align="left"><span data-ttu-id="27bea-203">说明</span><span class="sxs-lookup"><span data-stu-id="27bea-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="27bea-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="27bea-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="27bea-205">地理位置，例如 NAM。</span><span class="sxs-lookup"><span data-stu-id="27bea-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="27bea-206">终结点</span><span class="sxs-lookup"><span data-stu-id="27bea-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="27bea-207">要连接到的终结点，例如 https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="27bea-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="27bea-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="27bea-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="27bea-209">结果源的 GUID，例如 B81EAB55-3140-4312-B0F4-9459D1B4FFEE。</span><span class="sxs-lookup"><span data-stu-id="27bea-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="27bea-p117">如果省略 DataLocation 或终结点，或如果 DataLocation 是重复的，则请求将会失败。[可以使用 Microsoft Graph 获取有关租户地理位置终结点的信息](https://docs.microsoft.com/zh-CN/sharepoint/dev/solution-guidance/multigeo-discovery)。</span><span class="sxs-lookup"><span data-stu-id="27bea-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/zh-CN/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="27bea-212">响应数据</span><span class="sxs-lookup"><span data-stu-id="27bea-212">Response data</span></span>

<span data-ttu-id="27bea-p118">MultiGeoSearchStatus - 这是 SharePoint Search API 响应请求返回的属性。该属性的值是一个字符串，提供有关 SharePoint Search API 所返回结果的以下信息：</span><span class="sxs-lookup"><span data-stu-id="27bea-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="27bea-215">值</span><span class="sxs-lookup"><span data-stu-id="27bea-215">Value</span></span></th>
<th align="left"><span data-ttu-id="27bea-216">说明</span><span class="sxs-lookup"><span data-stu-id="27bea-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="27bea-217">完整</span><span class="sxs-lookup"><span data-stu-id="27bea-217">Full</span></span></td>
<td align="left"><span data-ttu-id="27bea-218">来自所有<strong></strong>地理位置的完整结果。</span><span class="sxs-lookup"><span data-stu-id="27bea-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="27bea-219">部分</span><span class="sxs-lookup"><span data-stu-id="27bea-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="27bea-p119">来自一个或多个地理位置的部分结果。由于暂时性错误，该结果不完整。</span><span class="sxs-lookup"><span data-stu-id="27bea-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="27bea-222">使用 REST 服务查询</span><span class="sxs-lookup"><span data-stu-id="27bea-222">Query using the REST service</span></span>

<span data-ttu-id="27bea-p120">使用 GET 请求，指定 URL 中的查询参数。使用 POST 请求，在正文中以 JavaScript 对象表示法 (JSON) 格式传递查询参数。</span><span class="sxs-lookup"><span data-stu-id="27bea-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>


#### <a name="request-headers"></a><span data-ttu-id="27bea-225">请求标头</span><span class="sxs-lookup"><span data-stu-id="27bea-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="27bea-226">名称</span><span class="sxs-lookup"><span data-stu-id="27bea-226">Name</span></span></th>
<th align="left"><span data-ttu-id="27bea-227">值</span><span class="sxs-lookup"><span data-stu-id="27bea-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="27bea-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="27bea-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="27bea-229">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="27bea-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="27bea-230">扇出到所有\*\*\*\* 地理位置的示例 GET 请求</span><span class="sxs-lookup"><span data-stu-id="27bea-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="27bea-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span><span class="sxs-lookup"><span data-stu-id="27bea-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="27bea-232">扇出部分\*\*\*\* 地理位置的示例 GET 请求</span><span class="sxs-lookup"><span data-stu-id="27bea-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="27bea-233">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="27bea-233">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span></span>

> [!NOTE]
> <span data-ttu-id="27bea-p121">MultiGeoSearchConfiguration 属性的地理位置列表中的逗号和冒号前面有**反斜杠**字符。这是因为 GET 请求使用冒号将属性和逗号分隔为单独的属性参数。如果没有反斜杠作为转义字符，则系统会错误地解释 MultiGeoSearchConfiguration 属性。</span><span class="sxs-lookup"><span data-stu-id="27bea-p121">Commas and colons in the list of geo-locations for the MultiGeoSearchConfiguration property are preceded by the **backslash** character. This is because GET requests use colons to separate properties and commas to separate arguments of properties. Without the backslash as an escape character, the MultiGeoSearchConfiguration property is interpreted wrongly.</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="27bea-237">扇出到**所有**地理位置的示例 POST 请求</span><span class="sxs-lookup"><span data-stu-id="27bea-237">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="27bea-238">扇出到部分\*\*\*\* 地理位置的示例 POST 请求</span><span class="sxs-lookup"><span data-stu-id="27bea-238">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="27bea-239">使用 CSOM 查询</span><span class="sxs-lookup"><span data-stu-id="27bea-239">Query using CSOM</span></span>

<span data-ttu-id="27bea-240">以下是扇出到所有\*\*\*\* 地理位置的示例 CSOM 请求：</span><span class="sxs-lookup"><span data-stu-id="27bea-240">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

