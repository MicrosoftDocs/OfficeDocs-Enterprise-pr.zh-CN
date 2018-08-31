---
title: 在 SharePoint Online 中延迟加载图像和 JavaScript
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: 本文介绍如何使用 JavaScript 延迟加载图像，也可以通过等待后页面加载加载之前的非重要 JavaScript 降低 SharePoint Online 页面加载时间。
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539769"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>在 SharePoint Online 中延迟加载图像和 JavaScript

本文介绍如何使用 JavaScript 延迟加载图像，也可以通过等待后页面加载加载之前的非重要 JavaScript 降低 SharePoint Online 页面加载时间。 
  
图像可能对 SharePoint Online 的页面加载速度产生负面影响。默认情况下，现在的大多数 Internet 浏览器在加载 HTML 页面时会预先获取图像。如果图像未显示在屏幕上，这可能会导致不必要的页面加载变缓，除非用户向下滚动页面。图像可能阻止浏览器加载页面的可见部分。若要解决此问题，可以使用 JavaScript 跳过首先加载图像。此外，加载非基本 JavaScript 也会减慢 SharePoint 页面的加载速度。本主题介绍了一些方法，您可以用来通过 SharePoint Online 中的 JavaScript 改进页面加载时间。 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>通过使用 JavaScript 延迟 SharePoint Online 页面的图像加载来改进页面加载时间

您可以使用 JavaScript 阻止 web 浏览器从预获取图像。这加快整个文档呈现。若要执行此操作删除中的 src 属性的值\<img\>标记并如将替换为 data 属性中的文件的路径： 数据 src。例如：
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

使用此方法，通过浏览器不立即下载图像。如果图像已在视，JavaScript 告知浏览器从 data 属性中检索的 URL 并将其插入作为 src 属性的值。当用户滚动仅加载图像和谈到视图。
  
要使所有这些发生，您将需要使用 JavaScript。
  
在文本文件中，将 **isElementInViewport()** 函数定义为检查元素是否是浏览器中对用户可见的部分。 
  
```
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth) 
  );
}

```

接下来，使用 **loadItemsInView()** 函数中的 **isElementInViewport()**。**loadItemsInView()** 函数将加载具有 data-src 属性的值的所有图像，前提是它们位于对用户可见的浏览器部分。将以下函数添加到文本文件中： 
  
```
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

最后，从 **window.onscroll()** 中调用 **loadItemsInView()**，如下面的示例中所示。这样可以确保在用户需要时加载观察窗中的的任何图像，但在用户需要之前不会加载。将以下内容添加到文本文件中： 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

对于 SharePoint Online，您需要将以下函数附加到滚动事件 #s4-workspace \<div\>标记。这是因为窗口事件被重写以确保功能区，保持连接到页面顶部。
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

将文本文件另存为扩展名为 .js 的 JavaScript 文件，例如 delayLoadImages.js。
  
一旦编写 delayLoadImages.js 完后，您可以将文件的内容添加到 SharePoint Online 中的母版页。通过将脚本链接添加到母版页中的页眉执行此操作。在母版页中后，JavaScript 将应用到使用该主控形状的页面布局的 SharePoint Online 网站中的所有页面。或者，如果您打算仅使用此网站的一页上，使用脚本编辑器 Web 部件将 JavaScript 嵌入到页。请参阅下列主题的详细信息：
  
- [如何： 将母版页应用到 SharePoint 2013 中的网站](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [如何： 在 SharePoint 2013 中创建页面布局](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 **示例：从 SharePoint Online 中的母版页引用 JavaScript delayLoadImages.js 文件**
  
要实现此操作，您还需要引用母版页中的 jQuery。在以下示例中，您可以看到在初始页面加载时仅加载了一个图像，但页面上有多个图像。
  
![显示在页面上加载一个图像的屏幕截图](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
下面的屏幕截图显示其余图像在滚动到视线中之后下载。
  
![显示在页面上加载多个图像的屏幕截图](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
使用 JavaScript 延迟图像加载是提高性能的有效技术，但是，如果将此技术应用到公共网站，则搜索引擎将不能以定期爬网所形成图像的相同方式对图像进行爬网。因为图像本身上的元数据在加载页面之前并非真正存在，这可能影响搜索引擎上的排名。搜索引擎爬网程序只能读取 HTML，因此不会将图像视为页面上的内容。图像是用于在搜索结果中对页面排名的因素之一。解决此问题的一种方法是为您的图像使用介绍性文本。
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub 代码示例：注入 JavaScript 以提高性能

请不要错过上[JavaScript 注入](https://go.microsoft.com/fwlink/p/?LinkId=524759)GitHub 中提供的文章和代码示例。 
  
## <a name="see-also"></a>另请参阅

[Office 2013 和 Office 365 ProPlus 中支持的浏览器](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[如何： 将母版页应用到 SharePoint 2013 中的网站](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[如何： 在 SharePoint 2013 中创建页面布局](https://go.microsoft.com/fwlink/p/?LinkId=525628)

