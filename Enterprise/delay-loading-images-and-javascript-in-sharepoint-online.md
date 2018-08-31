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
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="95d64-103">在 SharePoint Online 中延迟加载图像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="95d64-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="95d64-104">本文介绍如何使用 JavaScript 延迟加载图像，也可以通过等待后页面加载加载之前的非重要 JavaScript 降低 SharePoint Online 页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="95d64-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="95d64-p101">图像可能对 SharePoint Online 的页面加载速度产生负面影响。默认情况下，现在的大多数 Internet 浏览器在加载 HTML 页面时会预先获取图像。如果图像未显示在屏幕上，这可能会导致不必要的页面加载变缓，除非用户向下滚动页面。图像可能阻止浏览器加载页面的可见部分。若要解决此问题，可以使用 JavaScript 跳过首先加载图像。此外，加载非基本 JavaScript 也会减慢 SharePoint 页面的加载速度。本主题介绍了一些方法，您可以用来通过 SharePoint Online 中的 JavaScript 改进页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="95d64-p101">Images can negatively affect page load speeds on SharePoint Online. By default, most modern Internet browsers pre-fetch images when loading an HTML page. This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down. The images can block the browser from loading the visible part of the page. To work around this problem, you can use JavaScript to skip loading the images first. Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too. This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="95d64-112">通过使用 JavaScript 延迟 SharePoint Online 页面的图像加载来改进页面加载时间</span><span class="sxs-lookup"><span data-stu-id="95d64-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="95d64-p102">您可以使用 JavaScript 阻止 web 浏览器从预获取图像。这加快整个文档呈现。若要执行此操作删除中的 src 属性的值\<img\>标记并如将替换为 data 属性中的文件的路径： 数据 src。例如：</span><span class="sxs-lookup"><span data-stu-id="95d64-p102">You can use JavaScript to prevent a web browser from pre-fetching images. This speeds up overall document rendering. To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="95d64-p103">使用此方法，通过浏览器不立即下载图像。如果图像已在视，JavaScript 告知浏览器从 data 属性中检索的 URL 并将其插入作为 src 属性的值。当用户滚动仅加载图像和谈到视图。</span><span class="sxs-lookup"><span data-stu-id="95d64-p103">By using this method, the browser doesn't download the images immediately. If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute. The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="95d64-119">要使所有这些发生，您将需要使用 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="95d64-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="95d64-120">在文本文件中，将 **isElementInViewport()** 函数定义为检查元素是否是浏览器中对用户可见的部分。</span><span class="sxs-lookup"><span data-stu-id="95d64-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
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

<span data-ttu-id="95d64-p104">接下来，使用 **loadItemsInView()** 函数中的 **isElementInViewport()**。**loadItemsInView()** 函数将加载具有 data-src 属性的值的所有图像，前提是它们位于对用户可见的浏览器部分。将以下函数添加到文本文件中：</span><span class="sxs-lookup"><span data-stu-id="95d64-p104">Next, use **isElementInViewport()** in the **loadItemsInView()** function. The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user. Add the following function to the text file:</span></span> 
  
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

<span data-ttu-id="95d64-p105">最后，从 **window.onscroll()** 中调用 **loadItemsInView()**，如下面的示例中所示。这样可以确保在用户需要时加载观察窗中的的任何图像，但在用户需要之前不会加载。将以下内容添加到文本文件中：</span><span class="sxs-lookup"><span data-stu-id="95d64-p105">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example. This ensures that any images that are in the viewport are loaded as the user needs them, but not before. Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="95d64-p106">对于 SharePoint Online，您需要将以下函数附加到滚动事件 #s4-workspace \<div\>标记。这是因为窗口事件被重写以确保功能区，保持连接到页面顶部。</span><span class="sxs-lookup"><span data-stu-id="95d64-p106">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag. This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="95d64-129">将文本文件另存为扩展名为 .js 的 JavaScript 文件，例如 delayLoadImages.js。</span><span class="sxs-lookup"><span data-stu-id="95d64-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="95d64-p107">一旦编写 delayLoadImages.js 完后，您可以将文件的内容添加到 SharePoint Online 中的母版页。通过将脚本链接添加到母版页中的页眉执行此操作。在母版页中后，JavaScript 将应用到使用该主控形状的页面布局的 SharePoint Online 网站中的所有页面。或者，如果您打算仅使用此网站的一页上，使用脚本编辑器 Web 部件将 JavaScript 嵌入到页。请参阅下列主题的详细信息：</span><span class="sxs-lookup"><span data-stu-id="95d64-p107">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online. You do this by adding a script link to the header in the master page. Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout. Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page. See these topics for more information:</span></span>
  
- [<span data-ttu-id="95d64-135">如何： 将母版页应用到 SharePoint 2013 中的网站</span><span class="sxs-lookup"><span data-stu-id="95d64-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="95d64-136">如何： 在 SharePoint 2013 中创建页面布局</span><span class="sxs-lookup"><span data-stu-id="95d64-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="95d64-137">**示例：从 SharePoint Online 中的母版页引用 JavaScript delayLoadImages.js 文件**</span><span class="sxs-lookup"><span data-stu-id="95d64-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="95d64-p108">要实现此操作，您还需要引用母版页中的 jQuery。在以下示例中，您可以看到在初始页面加载时仅加载了一个图像，但页面上有多个图像。</span><span class="sxs-lookup"><span data-stu-id="95d64-p108">In order for this to work, you also need to reference jQuery in the master page. In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![显示在页面上加载一个图像的屏幕截图](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="95d64-141">下面的屏幕截图显示其余图像在滚动到视线中之后下载。</span><span class="sxs-lookup"><span data-stu-id="95d64-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![显示在页面上加载多个图像的屏幕截图](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="95d64-p109">使用 JavaScript 延迟图像加载是提高性能的有效技术，但是，如果将此技术应用到公共网站，则搜索引擎将不能以定期爬网所形成图像的相同方式对图像进行爬网。因为图像本身上的元数据在加载页面之前并非真正存在，这可能影响搜索引擎上的排名。搜索引擎爬网程序只能读取 HTML，因此不会将图像视为页面上的内容。图像是用于在搜索结果中对页面排名的因素之一。解决此问题的一种方法是为您的图像使用介绍性文本。</span><span class="sxs-lookup"><span data-stu-id="95d64-p109">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image. This can affect rankings on search engines because metadata on the image itself is not really there until the page loads. Search engine crawlers only read the HTML and therefore will not see the images as content on the page. Images are one of the factors used to rank pages in search results. One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="95d64-148">GitHub 代码示例：注入 JavaScript 以提高性能</span><span class="sxs-lookup"><span data-stu-id="95d64-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="95d64-149">请不要错过上[JavaScript 注入](https://go.microsoft.com/fwlink/p/?LinkId=524759)GitHub 中提供的文章和代码示例。</span><span class="sxs-lookup"><span data-stu-id="95d64-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="95d64-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95d64-150">See also</span></span>

[<span data-ttu-id="95d64-151">Office 2013 和 Office 365 ProPlus 中支持的浏览器</span><span class="sxs-lookup"><span data-stu-id="95d64-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="95d64-152">如何： 将母版页应用到 SharePoint 2013 中的网站</span><span class="sxs-lookup"><span data-stu-id="95d64-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="95d64-153">如何： 在 SharePoint 2013 中创建页面布局</span><span class="sxs-lookup"><span data-stu-id="95d64-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

