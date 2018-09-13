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
ms.openlocfilehash: 08790dcee343e9e69bbaab149cce8a390470e7d6
ms.sourcegitcommit: 5731dce2440e5a7a261f6360e8e2e9639d339d4e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2018
ms.locfileid: "23957447"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online 的导航选项

本文介绍与 SharePoint 发布 SharePoint Online 中启用导航选项网站。选择和配置导航显著影响性能和可伸缩性的 SharePoint Online 中的网站。

## <a name="overview"></a>概述

导航提供程序配置显著影响整个网站的性能和必须采取仔细考虑选取的导航提供程序和有效地调整您的 SharePoint 网站的要求的配置。有两个开的导航提供程序，以及自定义导航实现。

第一个选项[**（元数据） 的托管导航**](#using-managed-navigation-and-metadata-in-sharepoint-online)，建议，并且是在 SharePoint Online; 默认选项之一但是，我们建议除非必需的情况下禁用安全修整。作为通过默认安全设置的此导航提供程序; 启用安全修整但是，多个网站不需要安全修整自从导航元素通常都是一致的网站的所有用户的开销。若要禁用安全修整推荐配置，此导航提供程序不需要枚举网站结构，是高度可扩展的可接受的性能影响。

第二个选项，[**结构导航**](#using-structural-navigation-in-sharepoint-online)，**是 SharePoint Online 中的建议的导航选项**。此导航提供程序的 SharePoint Online 中的支持有限的内部部署拓扑结构设计。虽然它提供了一些其他的一组与其他导航选项的功能，这些功能，包括安全修整和网站结构枚举时，因服务器调用影响的可伸缩性和性能的成本使用它。使用 structed 导航的使用过多的资源的网站可能会受到限制。

除了开的导航提供程序，许多客户已成功实现替代的自定义导航实现。一个公共类的自定义导航实现坚信存储的导航节点的本地缓存的客户端呈现的设计模式。（请参阅**[搜索驱动客户端脚本编写](#using-search-driven-client-side-scripting)** 这篇文章中。）

这些导航提供程序有两种关键优势： 
- 他们通常很好地使用响应页面设计。
- 它们是极大可伸缩性和性能，因为它们可能造成没有资源成本 （和刷新后超时在后台）。 
- 这些导航提供程序可以检索使用各种策略，从到各种动态数据提供程序的简单静态配置导航数据。 

数据提供程序的示例是使用**搜索驱动的导航**，从而枚举导航节点和处理安全修整高效的灵活性。 

有其他受欢迎的选项，以构建**自定义导航提供程序**。请有关更多有关构建自定义导航提供程序的指南，查看[SharePoint Online 的门户导航解决方案](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)。
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>专业人员和 SharePoint Online 的缺点导航选项

下表总结了每个选项的优缺点。 


|托管导航  |结构导航  |搜索驱动的导航  |自定义导航提供程序  |
|---------|---------|---------|---------|
|优点：<br/><br/>易于维护<br/>建议使用该选项<br/>     |优点：<br/><br/>易于配置<br/>安全修整<br/>添加内容将自动更新<br/>|优点：<br/><br/>安全修整<br/>当添加网站时自动更新<br/>加载时间快，本地缓存的导航结构<br/>|优点：<br/><br/>更广泛的可用选项选择<br/>Fast 加载缓存时正确使用<br/>多个选项很好地响应页面设计<br/>|
|缺点：<br/><br/>不会自动更新以反映网站结构<br/>如果启用了安全修整对性能产生影响<br/>|缺点：<br/><br/>**不建议**<br/>**影响性能和可伸缩性**<br/>**受限制**<br/>|缺点：<br/><br/>不能轻松地对网站排序<br/>需要对母版页进行自定义（需要具备技术技能）<br/>|缺点：<br/><br/>自定义开发，则需要<br/>外部数据源缓存存储所需 / 例如 Azure<br/>|

最适合您的网站的选项将取决于您的网站要求和您的技术功能。如果您希望可扩展开的导航提供程序，然后托管导航与禁用的安全修整是一个很好的选项。 

可以通过维护托管导航选项配置，不涉及代码自定义文件，并且会显著比结构的导航。如果需要安全修整和便于使用自定义母版页并维护更改可能出现的默认母版页中的 SharePoint Online 的组织中有一些功能，通过然后搜索驱动选项可能会产生更佳用户体验。如果您有更复杂的要求，自定义导航提供程序可能是正确的选择。不建议结构的导航。

最后，务必要注意 SharePoint 正在添加其他导航提供程序和功能利用多扁平的网站层次结构和使用 SharePoint 中心网站的中心辐射型模型的现代 SharePoint 网站体系结构。这将允许多个要实现的方案不需要使用 SharePoint 发布功能，并且这些导航配置经过优化以可伸缩性和 SharePoint Online 中的延迟。请注意，通常应用相同的原则-简化逼真的内容的结构，SharePoint 发布网站的总体结构的总体绩效有助于和以及缩放。这意味着，而不是让数以百计的网站 （子网站） 与单个网站集，更好的方法是有大量的网站集具有很少的子网站 （子网站）。


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>在 SharePoint Online 中使用托管的导航和元数据

托管的导航是功能的另一个开的选项，您可以使用重新创建大部分结构导航相同。可以配置托管元数据进行安全修整启用或禁用。配置与禁用的安全修整，托管的导航时非常高效加载所有的常量服务器呼叫数的导航链接。启用安全修整，但是，不具备的某些托管导航的优点和客户可以选择浏览以获得最佳性能和可伸缩性的自定义导航解决方案之一。

多个网站的导航结构通常是一致的网站的所有用户，不需要安全修整。如果禁用安全修整的链接添加到并非所有用户都有权访问的导航以及链接仍会显示，但将导致拒绝访问的消息。没有可以防止由于无意访问内容无风险。

### <a name="how-to-implement-managed-navigation-and-the-results"></a>如何实现托管导航和结果

有一些文章 Docs.Microsoft.com 上有关托管导航的详细信息，例如，请参阅[Overview of SharePoint Server 中的托管导航](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)。

为了实现托管的导航，您设置条款 Url 与对应的网站的导航结构。托管的导航可以甚至是手动 curated 替换在许多情况下的结构化导航。例如：

![SharePoint Online 网站结构](media/SPONavOptionsListOfSites.png)

下面的示例显示使用托管导航的复杂导航的性能。

![使用托管的导航的复杂导航的性能](media/SPONavOptionsComplexNavPerf.png)

始终使用托管的导航可以提高性能与结构导航方法相比。
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>在 SharePoint Online 中使用结构导航

这是默认情况下使用开的导航和是最简单的解决方案，但此类具有高性能权衡。它不需要任何自定义和非技术用户可以方便地添加项目、 隐藏项目，请从设置页管理导航。这是，但是也可以还方便地管理和控制以及与托管导航，因此建议使用托管导航作为 true 改进性能。

![具有选中显示子网站的结构导航](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>在 SharePoint Online 中启用结构导航

为了说明如何使用结构导航和显示 SharePoint Online 标准解决方案中的性能子网站选项打开。下面是在**网站设置**页上找到的设置的屏幕截图\>**导航**。
  
![显示子网站的屏幕截图](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>分析 SharePoint Online 中的结构导航性能

若要分析 SharePoint 页的性能，请在 Internet Explorer 中使用 F12 开发人员工具的**网络**选项的卡。 
  
![显示 F12 开发工具“网络”选项卡的屏幕截图](media/SPONavOptionsNetworks.png)
  
1. 在“网络”**** 选项卡，单击正在加载的 .aspx 页面，然后单击“详细信息”**** 选项卡。<br/> ![显示详细信息选项卡的屏幕截图](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. 单击“响应头”****。 <br/>![“详细信息”选项卡的屏幕截图](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint 返回其响应标头中的一些有用的诊断信息。 
3. 信息的最有用部分之一是**SPRequestDuration**值，以毫秒为单位的时间长度请求处理所用的服务器上。在下面的屏幕快照**显示子网站**未选中的结构的导航。这意味着在全局导航中存在仅网站集的链接：<br/>![显示加载时间为请求持续时间的屏幕截图](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. **SPRequestDuration**键的值为 245 毫秒。这表示返回请求所花的时间。由于在网站上只有一个导航项，这是如何 SharePoint Online 执行大流量的导航不好基准。下一步的屏幕截图显示了如何在子网站中添加影响此项。<br/>![显示请求持续时间为 2502 毫秒的屏幕截图](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
添加子网站显著增加返回此相对简单示例网站页请求所花费的时间。复杂的网站层次结构，包括配置和其他拓扑选项页面导航窗格中，可以显著增加此影响进一步。

## <a name="using-search-driven-client-side-scripting"></a>使用搜索驱动的客户端脚本

使用搜索，您可以利用使用连续爬网在后台建立索引。搜索结果来自搜索索引，并且的结果是安全修整。需要安全修整时，这是通常比开的导航提供程序。使用搜索结构导航，尤其是具有一个复杂的网站结构中，将加快页面加载时间显著。此通过托管导航的主要优点是受益于安全修整。

此方法包括创建自定义母版页和即开导航代码替换为自定义 HTML。按照此过程，按照下面的示例以替换该文件中的导航代码`seattle.html`。在此示例中，您将打开`seattle.html`文件并将整个元素`id=”DeltaTopNavigation”`与自定义 HTML 代码。

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>示例： 母版页中的即开导航代码替换

1.  导航到“网站设置”页面。
2.  单击“母版页”**** 打开母版页样式库。
3.  从此处导航库和下载文件`seattle.master`。
4.  使用文本编辑器编辑代码，并删除下面的屏幕截图中的代码块。<br/>![删除所示的代码块](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. 删除之间的代码`<SharePoint:AjaxDelta id=”DeltaTopNavigation”>`和`<\SharePoint:AjaxDelta>`标签，并将其替换为以下代码段：<br/>

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
6. 替换中加载的 URL 图像开头，网站集加载图像的链接的定位标记。所做的更改后，重命名该文件，然后将其上载到母版页样式库。这会生成新的.master 文件。<br/>
7. 此 HTML 是将使用从 JavaScript 代码返回的搜索结果填充的基本标记。您将需要编辑来更改 var 根的值的代码 ="网站集 URL"，如以下代码段中所示：<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. 结果将分配给 self.nodes 数组和层次结构构建利用使用 linq.js 将输出分配给数组 self.heirarchy 对象。此数组是绑定到 HTML 的对象。这是通过将自我对象传递给 ko.applyBinding() 函数完成 toggleView() 函数中。<br/>然后，这会导致要绑定到以下 HTML 的层次结构数组：<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

事件处理程序`mouseenter`和`mouseexit`添加到用于处理的子网站下拉列表菜单是完成中的顶级导航`addEventsToElements()`函数。

在我们复杂导航的示例，一个全新页面负载而无需从基准结构导航，若要获取的托管的导航方法类似结果已减少服务器上所用的时间本地缓存显示。

### <a name="about-the-javascript-file"></a>有关 JavaScript 文件...

整个 JavaScript 文件如下所示：

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

汇总中上述代码`jQuery $(document).ready`函数没有`viewModel object`创建然后`loadNavigationNodes()`调用该对象上的函数。此函数可以加载以前生成的导航层次结构存储在客户端浏览器的 HTML5 本地存储区或其调用函数`queryRemoteInterface()`。

`QueryRemoteInterface()`生成请求使用`getRequest()`，查询参数的函数之前在脚本中定义，然后从服务器返回数据。此数据是本质上一个数组作为数据传输对象处理各种属性所表示的网站集合中的所有网站。 

然后分析此数据到以前定义`SPO.Models.NavigationNode`对象使用`Knockout.js`创建数据绑定到我们之前定义的 HTML 的值用于可观察的属性。 

对象然后置于结果数组。分析到 JSON 使用 Knockout 和存储在将来的页面加载性能改进的本地浏览器存储在此数组。

### <a name="benefits-of-this-approach"></a>此方法的优点

[此方法](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)的一个主要好处是，通过使用 HTML5 本地存储，导航存储在本地用户的下次它们加载页。我们获得主要性能改进的结构导航; 使用 API 中的搜索但是，计一些技术的功能，能够执行和自定义此功能。 

在[实现示例](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)中，网站进行排序的框结构导航; 相同的方式按字母顺序排列顺序。如果您想要偏离此顺序，它将为可进行更为复杂开发和维护。此外，通过此方法需要偏离受支持的母版页。如果不保留自定义母版页，您的网站会错过了解的更新和 Microsoft 向母版页的改进。

[代码之上](#about-the-javascript-file)具有以下依赖项：

- jQuery-http://jquery.com/
- KnockoutJS-http://knockoutjs.com/
- Linq.js- http://linqjs.codeplex.com/，或 github.com/neuecc/linq.js

当前版本的 LinqJS 不包含上面的代码中使用 ByHierarchy 方法，并将中断导航代码。若要解决此问题，请将以下方法添加到行之前 Linq.js 文件`Flatten: function ()`。

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
  
## <a name="related-topics"></a>相关主题

[SharePoint Server 中的托管导航概述](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

