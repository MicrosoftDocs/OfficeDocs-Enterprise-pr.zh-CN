---
title: 在 SharePoint Online 中延迟加载图像和 JavaScript
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: 本文介绍如何通过使用 JavaScript 来延迟加载图像以及在页面加载后等待加载非基本 JavaScript，从而减少 SharePoint Online 页面的加载时间。
ms.openlocfilehash: 86efb767e80927f7d3f5d8055676e6d99da4d667
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840559"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>在 SharePoint Online 中延迟加载图像和 JavaScript

本文介绍如何通过使用 JavaScript 来延迟加载图像以及在页面加载后等待加载非基本 JavaScript，从而减少 SharePoint Online 页面的加载时间。
  
图像会对 SharePoint Online 上的页面加载速度产生负面影响。 默认情况下，大多数新式 Internet 浏览器在加载 HTML 页面时预提取映像。 如果在用户向下滚动之前图像在屏幕上不可见，则这可能会导致页面的加载速度不必要。 图像可以阻止浏览器加载页面的可见部分。 若要解决此问题，可以使用 JavaScript 先跳过加载图像。 此外，加载非基本 JavaScript 也可能会减慢 SharePoint 页面上的加载时间。 本主题介绍可用于在 SharePoint Online 中使用 JavaScript 改进页面加载时间的一些方法。
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>通过使用 JavaScript 延迟 SharePoint Online 页面中的图像加载，提高页面加载时间

您可以使用 JavaScript 阻止 web 浏览器预先获取图像。 这将加快整体文档呈现速度。 若要执行此操作，请从\<img\>标记中删除 src 属性的值，并将其替换为 data 属性中的文件的路径，如 data-src。 例如：
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

通过使用此方法，浏览器不会立即下载图像。 如果图像已在视区中，JavaScript 会通知浏览器从数据属性中检索 URL，并将其作为 src 属性的值插入。 仅当用户滚动并进入视图中时，才会加载图像。
  
若要执行所有操作，需要使用 JavaScript。
  
在文本文件中，定义**isElementInViewport （）** 函数，以检查元素是否位于浏览器中对用户可见的部分。
  
```javascript
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

接下来，在**loadItemsInView （）** 函数中使用**isElementInViewport （）** 。 如果包含数据 src 属性值的所有图像位于用户可见的浏览器部分中，则**loadItemsInView （）** 函数将加载这些图像。 将以下函数添加到文本文件中：
  
```javascript
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

最后，在**onscroll （）** 中调用**loadItemsInView （）** ，如下面的示例所示。 这样可确保视区中的任何图像在用户需要时加载，但不会在之前加载。 将以下内容添加到文本文件中：
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

对于 SharePoint Online，需要将以下函数附加到 #s4-workspace \<div\>标记上的 scroll 事件。 这是因为窗口事件将被重写，以确保功能区仍附加在页面顶部。
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

将文本文件另存为带有扩展名 .js 的 JavaScript 文件，例如 Delayloadimages.js。
  
编写完 Delayloadimages.js 后，可以将文件的内容添加到 SharePoint Online 中的母版页。 为此，请将脚本链接添加到母版页中的标头。 在母版页中，JavaScript 将应用于使用该母版页布局的 SharePoint Online 网站中的所有页面。 或者，如果您打算仅在网站的一个页面上使用此项，请使用脚本编辑器 Web 部件将 JavaScript 嵌入到页面中。 有关详细信息，请参阅以下主题：
  
- [如何：向 SharePoint 2013 中的网站应用母版页](https://go.microsoft.com/fwlink/p/?LinkId=525627)

- [如何：在 SharePoint 2013 中创建页面布局](https://go.microsoft.com/fwlink/p/?LinkId=525628)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>示例：在 SharePoint Online 中引用母版页中的 JavaScript Delayloadimages.js 文件
  
若要使其正常工作，您还需要在母版页中引用 jQuery。 在下面的示例中，您可以在初始页面加载中看到仅加载了一个图像，但在页面上有多个。
  
![显示在页面上加载一个图像的屏幕截图](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
下面的屏幕截图显示了图像在滚动查看后下载的其余部分。
  
![显示在页面上加载多个图像的屏幕截图](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
延迟使用 JavaScript 加载图像可能是一种提高性能的有效技术;但是，如果在公共网站上应用了技术，搜索引擎将无法对图像进行爬网，这与对定期生成的图像进行爬网的方式相同。 这可能会影响搜索引擎上的排名，因为在页面加载之前，图像本身的元数据实际上并不在此处。 搜索引擎爬网程序仅读取 HTML，因此不会在页面上看到图像内容。 图像是用于对搜索结果中的页面进行排名的因素之一。 解决此种情况的一种方法是使用图像的介绍性文本。
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub 代码示例：注入 JavaScript 以提高性能

请勿错过 GitHub 上提供的[JavaScript 注入](https://go.microsoft.com/fwlink/p/?LinkId=524759)中的文章和代码示例。
  
## <a name="see-also"></a>另请参阅

[Office 2013 和 Office 365 专业增强版中支持的浏览器](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[如何：向 SharePoint 2013 中的网站应用母版页](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[如何：在 SharePoint 2013 中创建页面布局](https://go.microsoft.com/fwlink/p/?LinkId=525628)
