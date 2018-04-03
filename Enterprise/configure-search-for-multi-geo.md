---
title: 管理多个地理环境
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解有关如何在多个地理环境中配置搜索。
ms.openlocfilehash: 0c5c8eaa981c31151c70507da54587a7269f98f5
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a>配置搜索业务多地区的 OneDrive

组织可以在多地区 SharePoint 联机 (SPO) 环境中，有一个 Office 365 的租户，但将 SharePoint 内容存储在多个地理位置的一个中心位置以及一个或多个卫星地理位置。

每个地理位置都有其自己的搜索索引和搜索中心。当用户搜索时，查询按扇形展开对所有索引，并返回的结果进行合并。

例如，在一个地理位置的用户可以搜索内容存储在另一个地理位置，或只限于在不同地理位置的 SharePoint 网站上的内容。如果用户有权访问此内容，则搜索将显示结果。

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>其中多地理环境中搜索客户端工作？

这些客户端可以从所有地理位置返回结果：

-   OneDrive for Business

-   Delve

-   SharePoint 主页

-   搜索中心

-   使用 SharePoint 搜索 API 的自定义搜索应用程序

### <a name="onedrive-for-business"></a>OneDrive for Business

只要多地理环境已设置，在 OneDrive 中搜索的用户从所有地理位置得到的结果。

### <a name="delve"></a>Delve

只要多地理环境已设置，在 Delve 中搜索的用户从所有地理位置得到的结果。

Delve 将源和配置文件卡只显示在**中心**位置存储的文件的预览。对于卫星地理位置中存储的文件，该文件类型的图标显示。

### <a name="the-sharepoint-home-page"></a>SharePoint 主页

只要多地理环境具有设置，用户将看到新闻，最近和已跟随从其 SharePoint 主页上的多个地理位置的站点。如果他们使用 SharePoint 主页上的搜索框，它们只能从搜索索引位于地理位置 SPHome 得到的结果。

### <a name="the-search-center"></a>搜索中心

多地理环境设置后，每个搜索中心从他们自己的地理位置会继续为只显示搜索结果。管理员必须[更改每个搜索中心的设置](#_Set_up_a_1)，以从所有地理位置得到的结果。随后，在搜索中心中搜索的用户从所有地理位置得到的结果。

### <a name="custom-search-applications"></a>自定义搜索应用程序

同往常一样，自定义搜索应用程序搜索索引通过使用现有的 SharePoint 搜索 REST Api 交互。若要从所有，或部分地理位置获得的结果，应用程序必须[调用 API 并包括新的多地理查询参数](#_Get_custom_search)在请求中。这会触发对所有地理位置查询出风扇。

### <a name="whats-different-about-search-in-a-multi-geo-environment"></a>关于搜索多地理环境中的不同是什么？

某些搜索功能，您可能很熟悉，在多个地理环境中的工作方式不同。

<table>
<thead>
<tr class="header">
<th align="left"><strong>功能</strong></th>
<th align="left"><strong>它是如何工作的</strong></th>
<th align="left"><strong>解决方法</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">升级的结果</td>
<td align="left">您可以使用不同级别的升级结果创建查询规则： 为整个租户、 网站集或网站。在多个地理环境中，定义<strong>租户</strong>级别提升的结果，如果您想要升级到<strong>所有</strong>地理位置搜索中心的结果。如果您<strong>只</strong>希望升级导致搜索中心网站集或网站的地理位置，定义<strong>站点集合</strong>或<strong>站点</strong>级别的结果。</td>
<td align="left">如果您不需要每个地理位置，例如不同的规则适合旅行，不同的升级的结果建议定义提升在组织级别的结果。</td>
</tr>
<tr class="even">
<td align="left">精简搜索将</td>
<td align="left">搜索返回精简将所有租户的地理位置，然后将它们聚合。聚合是尽心尽力，意味着精简计数可能不 100%准确。对于大多数搜索驱动方案，此准确性就足够了。</td>
<td align="left">对于搜索驱动的应用程序依赖于精选完整性，查询每个地理位置独立而无需使用多个 Geo 扇出。</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">多地区搜索不支持动态桶数字精简将。</td>
<td align="left">对于数字的精简将使用<a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">"Discretize"参数</a>。</td>
</tr>
<tr class="even">
<td align="left">文档 Id</td>
<td align="left">如果正在开发一个搜索驱动应用程序依赖于文档 Id，注意多地理环境中的文档 Id 不唯一跨地理位置，它们是唯一每个地理位置。</td>
<td align="left">我们已添加标识地理位置的列。使用此列来实现唯一性。这列被命名为"GeoLocationSource"。</td>
</tr>
<tr class="odd">
<td align="left">结果数</td>
<td align="left">搜索结果页面中显示合并的结果的地理位置，但不能超过 500 的结果页。</td>
<td align="left"></td>
</tr>
</tbody>
</table>

### <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>什么不支持多个地理环境中搜索？

在多个地理环境中不支持某些您可能非常熟悉，在搜索功能。

<table>
<thead>
<tr class="header">
<th align="left"><strong>搜索功能</strong></th>
<th align="left"><strong>备注</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">仅限应用程序身份验证</td>
<td align="left">仅限应用程序身份验证 （从服务的访问特权） 不支持在多个地区搜索。</td>
</tr>
<tr class="even">
<td align="left">来宾用户</td>
<td align="left">来宾用户只能从地理位置，他们要从搜索得到的结果。</td>
</tr>
</tbody>
</table>

### <a name="how-does-search-work-in-a-multi-geo-environment"></a>如何搜索工作多地理环境中？

**所有**的搜索客户端使用现有 SharePoint 搜索 REST Api 进行交互与搜索索引。

<table>
<thead>
<tr class="header">
<th align="left"><p><img src="media/configure-search-for-multi-geo_image1.png" /></p>
<p>图 1： 搜索跨三个地理位置与租户</p></th>
<th align="left"><p>搜索客户端调用搜索 REST 端点查询属性 EnableMultiGeoSearch = true。</p>
<p>查询被发送到组织中的所有地理位置。</p>
<p>从每个地理位置的搜索结果将合并和排名。</p>
<p>客户端获取统一的搜索结果。</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>多地区搜索工作通过调用每个 geo 中的每个搜索终结点。执行远程转到请求的并行，但对合并发生，我们等待答复之前，我们可以进行合并慢腿。这意味着多个地区带来额外延迟的搜索体验。 <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span> 
###获取搜索中心显示来自所有地理位置的结果

每个搜索中心有几个行业，您必须单独设置每个垂直。

1.  请确保您执行这些步骤具有编辑搜索结果页面和搜索结果 Web 部件的权限的帐户。

2.  导航到搜索结果页面 （请参见[列表](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213)的搜索结果页面）

3.  选择要设置，单击右上角，**设置**齿轮图标，然后单击**编辑页面**的垂直。

> ![](media/configure-search-for-multi-geo_image2.png)
>
> 在编辑模式下打开搜索结果页。

1.  在搜索结果 Web 部件中，将鼠标指针移动到上面，右上角的 Web 部件中，单击箭头，然后单击在菜单上的**编辑 Web 部件**。 ![](media/configure-search-for-multi-geo_image3.png)

> 在功能区中打开搜索结果 Web 部件工具窗格页面右上角。

1.  在 Web 部件工具窗格的**设置**部分中的**结果控制设置**，请在下，选择**显示多个地区的结果**，得到的搜索结果 Web 部件以显示来自所有地理位置的结果。

2.  单击**确定**以保存所做的更改并关闭 Web 部件工具窗格。

3.  检查主菜单的页面选项卡上单击**签入**到搜索结果 Web 部件所做的更改。

4.  使用页面顶部的注释中提供的链接发布所做的更改。

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
### <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>获取自定义搜索应用程序，以显示来自所有或某些地理位置的结果

自定义搜索应用程序通过使用 SharePoint 搜索 REST API 的请求指定查询参数来获得从所有，或部分，地理位置的结果。根据查询的参数中，查询是按扇形展开到所有的地理位置，或某些地理位置。例如，如果只需要查询地理位置即可找到相关信息的一个子集，您可以控制仅这些出风扇。如果请求成功，SharePoint 搜索 REST API 将返回的响应数据。

### <a name="query-parameters"></a>查询参数

**EnableMultiGeoSearch** -这是一个布尔值，指定是否查询应能按扇形展开到其他地理位置的多个地区组织的索引。将其设置为**true**以扇出查询。**假**以不扇出查询。默认值为**false**。如果不使用该参数，则查询**不**按扇形展开到其他地理位置。如果不是多个地区的环境中使用该参数，将忽略该参数。

**客户端类型**-这是一个字符串。输入每个搜索应用程序的一个唯一的客户机名称。如果不使用该参数，则查询**不**按扇形展开到其他地理位置。

**MultiGeoSearchConfiguration** -这是一个可选的列表，该列表的哪个地区在多个地理位置租户以扇出为****EnableMultiGeoSearch**情况**的查询。如果未包含此参数，或将其保留为空，该查询将按扇形展开到所有地理位置。对于每个地理位置，以 JSON 格式输入以下各项：

<table>
<thead>
<tr class="header">
<th align="left">项目</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">数据位置</td>
<td align="left">地理位置，例如名称。</td>
</tr>
<tr class="even">
<td align="left">终结点</td>
<td align="left">终结点来连接，例如https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">源 Id</td>
<td align="left">结果源，例如 B81EAB55-3140 的 4312-B0F4-9459D1B4FFEE 的 GUID。</td>
</tr>
</tbody>
</table>

如果省略数据位置或终结点，或者重复的数据的位置，则请求就会失败。[您可以获取有关租户的地理位置，通过使用 Microsoft Graph 的终结点信息](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery)。

### <a name="response-data"></a>响应数据

**MultiGeoSearchStatus** – 这是一个 SharePoint 搜索 API 对请求的响应中返回的属性。属性的值是一个字符串，并给出了 SharePoint 搜索 API 返回的结果有关的下列信息：

<table>
<thead>
<tr class="header">
<th align="left">值</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">完全</td>
<td align="left">地理位置完全从<strong>所有</strong>的结果。</td>
</tr>
<tr class="even">
<td align="left">部分</td>
<td align="left">从一个或多个地理位置的部分结果。结果是由于暂时性错误而不完整的。</td>
</tr>
<tr class="odd">
<td align="left">无</td>
<td align="left">查询不多地理查询，不按扇形展开到其他地理位置。</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>使用的 REST 服务查询

使用 GET 请求，可以在 URL 中指定查询参数。POST 请求，使用 JavaScript 对象符号 (JSON) 格式在正文中传递的查询参数。

#### <a name="request-headers"></a>请求标头

<table>
<thead>
<tr class="header">
<th align="left">名称</th>
<th align="left">值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Content-Type</td>
<td align="left">应用程序/json; odata = 详细</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>按扇形展开到**所有**地理位置的示例 GET 请求

https://\<租户\>/\_api/搜索/query?querytext = 属性 sharepoint' = 'EnableMultiGeoSearch:true' 和客户端类型 =' 我\_客户端\_id

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>示例的 GET 请求以**某些**地理位置到扇出

https:// <tenant>/_api/search/query?querytext = 站点和客户端类型 = 'my_client_id' 和属性 ='EnableMultiGeoSearch:true、 MultiGeoSearchConfiguration: [{数据位置\:"名称"\,端点\:"https\:contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{数据位置\:"可以"\,端点\:"https\://contosoCAN.sharepoint-df.com"}]

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>按扇形展开到**所有**地理位置的示例 POST 请求

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>按扇形展开到**一些**地理位置的示例 POST 请求


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

### <a name="query-using-csom"></a>使用 CSOM 查询

下面是按扇形展开到**所有**地理位置的示例 CSOM 查询：

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;