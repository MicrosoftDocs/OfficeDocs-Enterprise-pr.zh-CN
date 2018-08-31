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
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online 的导航选项

本文介绍如何通过使用经典发布中托管的导航或搜索驱动的导航 SharePoint online 改进页面加载时间。
  
带有启用的经典发布 SharePoint Online 的具有两个导航区域;全局导航和当前导航。
  
全局导航当前导航时侧或依赖于语言配置和使用的母版页的上下文中左/右导航是顶部导航菜单。
  
导航可以带来负面影响整个门户的性能，因为它通常配置为门户级使用，因为这是任何 SharePoint 网站的重要组成部分。
  
结构导航不是 SharePoint Online 中的建议的导航选项，如它为安全修整的内部部署拓扑结构设计和此设计使过多的服务器的呼叫时使用它会影响性能。
  
在现代设计已更改的现代的 SharePoint 网站的引入已简化扁平的网站层次结构。这简化与消除了对导航相关的性能问题简化层次结构的导航。
  
有两个主即开导航选项在 SharePoint 以及第三个、 自定义的搜索驱动的方法。此外，第四个和非常流行选项是如何构建自定义导航提供程序。请有关自定义导航提供程序的指南，查看[SharePoint Online 的门户导航解决方案](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation)。 
  
每个选项具有优点和缺点，如下表中所述。
  
|**结构导航**|**托管导航**|**搜索驱动的导航**||**自定义导航提供程序**|
|:-----|:-----|:-----|:-----|:-----|
| 优点：  <br/>  易于配置  <br/>  安全修整  <br/>  当添加网站时自动更新  <br/> | 优点：  <br/>  易于维护  <br/>  建议使用该选项  <br/> | 优点：  <br/>  安全修整  <br/>  当添加网站时自动更新  <br/>  加载时间快，本地缓存的导航结构  <br/> || 优点：  <br/>    <br/>  更多选项 / 选项可用  <br/>  Fast 加载缓存时正确使用  <br/> |
| 缺点：  <br/> **不建议** <br/> **对性能产生影响** <br/> | 缺点：  <br/>  不会自动更新以反映网站结构  <br/>  如果启用了安全修整对性能产生影响  <br/> | 缺点：  <br/>  不能轻松地对网站排序  <br/>  需要对母版页进行自定义（需要具备技术技能）  <br/> || 缺点：  <br/>  自定义开发，则需要  <br/>  外部数据源缓存存储所需 / 例如 Azure  <br/> |
   
最适合您的网站的选项将取决于您的网站要求和您的技术功能。如果您便于使用自定义母版页，并维护更改可能出现的默认母版页中的 SharePoint Online 的组织中有一些功能，搜索驱动选项将产生最佳用户体验。如果您希望简单介于即开结构导航和搜索，然后托管的导航是一个很好的选项。可以通过维护托管的导航选项配置，不涉及代码自定义文件，并且比即开结构导航显著速度更快。
  
简化类似现代经典门户的总体结构，有助于总体性能和规模以及。这意味着，而不是让单个网站集与数百/数千个站点 （子网站），更好的方法是拥有大量具有很少的子网站 （子网站） 的网站集。
  
这提供服务中的其他扩展选项、 可避免投入一个大的数据库的所有内容和最终将允许为导航和更重要的是安全的灵活性。
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>在 SharePoint Online 中使用结构导航

这是默认情况下使用开的导航和是最简单的解决方案，但此类具有高性能权衡。它不需要任何自定义和非技术用户可以方便地添加项目、 隐藏项目，请从设置页管理导航。这是但是也托管导航，因此建议同时使用托管导航的可以为 true，则是轻松地管理和控制以及。
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>在 SharePoint Online 中启用结构导航

为了说明如何使用结构导航和显示 SharePoint Online 标准解决方案中的性能子网站选项打开。下面屏幕快照，在**网站设置**页上找到的设置\>**导航**。
  
![显示子网站的屏幕截图](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>分析 SharePoint Online 中的结构导航性能

若要分析 SharePoint 页面的性能，请使用 Internet Explorer 中的 F12 开发人员工具的“网络”**** 选项卡。 
  
![显示 F12 开发工具“网络”选项卡的屏幕截图](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
在“网络”**** 选项卡，单击正在加载的 .aspx 页面，然后单击“详细信息”**** 选项卡。 
  
![显示详细信息选项卡的屏幕截图](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
单击“响应头”****。
  
![“详细信息”选项卡的屏幕截图](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
SharePoint 在其响应标头中返回一些有用的诊断信息。其中最有用的信息之一是 **SPRequestDuration**，这是请求在服务器上处理所需的时间，以毫秒为单位。 
  
以下屏幕截图**显示子网站**中是结构导航取消选中。这意味着在全局导航中存在仅网站集的链接： 
  
![显示加载时间为请求持续时间的屏幕截图](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
**SPRequestDuration**键的值为 245 毫秒。这表示返回请求所花的时间。由于在网站上只有一个导航项，这是如何 SharePoint Online 执行大流量的导航不好基准。下一步的屏幕截图显示了如何在子网站中添加影响此项。 
  
![显示请求持续时间为 2502 毫秒的屏幕截图](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
添加子网站显著增加了返回页面请求所用的时间。
  
使用常规的结构化的导航的优点是，您可以轻松地组织顺序、 隐藏网站，添加页面、 结果安全修整，并且您不解调器从支持母版页在 SharePoint Online 中使用。
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a>使用 SharePoint Online 中的托管导航和托管元数据

托管导航是另一个可用来重新创建与结构导航相同类型的功能的开箱即用选项。
  
使用托管元数据的好处是速度快得多检索比使用查询的内容来构建网站导航的数据。虽然更快地没有方法对安全修整结果，以便用户没有访问权限给定的网站，如果链接仍会显示，但将导致错误消息。
  
 **如何实现托管导航和结果**
  
有一些文章 TechNet 上有关托管导航的详细信息，例如，请参阅[Overview of SharePoint Server 2013 中托管导航](https://go.microsoft.com/fwlink/?LinkId=708689)。
  
要实现托管导航，您需要具有术语库管理员权限。通过使用与网站集结构相匹配的 URL 设置术语，可以使用托管导航取代结构导航。例如：
  
![Subsite1 示例的屏幕截图](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
下面的示例显示使用托管导航的复杂导航的性能。
  
![SPRequestDuration 示例的屏幕截图](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
与通过查询结构导航方法的内容相比，一致地使用托管导航会提高性能。
  
## <a name="using-search-driven-client-side-scripting"></a>使用搜索驱动的客户端脚本

通过搜索，您可以利用使用连续爬网在后台建立的索引。这意味着没有大量的内容查询。搜索结果将从搜索索引中提取，结果将进行安全修整。这比使用常规内容查询更快。使用搜索进行结构导航将大大减少页面加载时间，尤其是当您具有复杂的网站结构时。与托管导航相比，其主要优点是您将从安全修整中受益。
  
此方法涉及创建自定义母版页以及将开箱即用的导航代码替换为自定义 HTML。按照此过程来替换文件 seattle.html 中的导航代码。
  
本示例中，将打开 seattle.html 文件，并将整个元素**id ="DeltaTopNavigation"** 替换为自定义 HTML 代码。 
  
 **示例：替换母版页中开箱即用的导航代码**
  
1. 导航到“网站设置”**** 页面。 
    
2. 单击“母版页”**** 打开母版页样式库。
    
3. 从这里，您可以导航整个库并下载文件 **seattle.master**。
    
4. 使用文本编辑器编辑代码，并删除下面的屏幕截图中的代码块。
    
    ![要删除的 DeltaTopNavigation 代码的屏幕截图](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. 删除之间的代码\<SharePoint:AjaxDelta id ="DeltaTopNavigation"\>和\<\SharePoint:AjaxDelta\>标签，并将其替换为以下代码段：
    
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

6. 替换中加载的 URL 图像开头，网站集加载图像的链接的定位标记。所做的更改后，重命名该文件，然后将其上载到母版页样式库。这会生成新的.master 文件。
    
7. 此 HTML 是将使用从 JavaScript 代码返回的搜索结果填充的基本标记。您将需要编辑下面的代码更改的值`var root = "site collection URL"`如以下代码段中所示： 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

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

     $("li.level1").mouseover （函数 （） { 
  
var 位置 = $(this).position();
  
$(this).find("ul.level2").css ({宽度： 100，左： position.left + 10，top: 50});
    
     }) 
  
.mouseout （函数 （） {
  
$(this).find("ul.level2").css ({左侧：-99999，顶部： 0});
  
});
  
$("li.level2").mouseover （函数 （） {
  
var 位置 = $(this).position();
  
console.log(JSON.stringify(position));
  
$(this).find("ul.level3").css ({宽度： 100，左： position.left + 95，top: position.top});
    
     }) 
  
.mouseout （函数 （） {
  
$(this).find("ul.level3").css ({左侧：-99999，顶部： 0});
  
});
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. 接下来，结果将分配给 **[self.nodes]** 数组和层次结构构建利用使用 linq.js 将输出分配给数组 **[self.heirarchy]** 对象。此数组是绑定到 HTML 的对象。这是通过将自我对象传递给 **[ko.applyBinding()]** 函数完成 **[toggleView()]** 函数中。然后，这会导致要绑定到以下 HTML 的层次结构数组： 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    最后的事件处理程序 **[mouseenter]** 和 **[mouseexit]** 被添加到其完成 **[addEventsToElements()]** 函数中处理的子网站下拉列表菜单的顶级导航。 
    
    屏幕截图下方中，可以看到的导航的结果：
    
    ![导航结果的屏幕截图](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    在我们复杂的导航示例中，没有本地缓存的全新页面加载显示服务器上所用的时间已从基准结构导航大大减少，以获取与托管导航方法类似的结果。
    
    ![SPRequestDuration 301 的屏幕截图](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    这种方法的一个主要优点是通过使用 HTML5 本地存储，导航存储在本地，以便用户在下次加载页面时使用。
    
通过使用搜索 API 进行结构导航，我们实现了较大的性能改进；但是，它需要具备技术能力来执行和自定义此功能。在示例实现中，站点按与开箱即用结构导航一样的顺序排列，即按字母顺序。如果您想要偏离此顺序，开发和维护过程将更加复杂。此外，此方法还要求您偏离受支持的母版页。如果未维护自定义母版页，您的网站将会遗漏 Microsoft 对母版页所做的更新和改进。
  
上面的代码具有以下依赖项：
  
- jQuery-[http://jquery.com/](http://jquery.com/)
    
- KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)
    
- Linq.js- [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/)，或[github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)
    
当前版本的 LinqJS 不包含上面的代码中使用 ByHierarchy 方法，并将中断导航代码。若要解决此问题，请将以下方法添加到行之前 Linq.js 文件"采取恢复： 函数 （）"。
  
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


