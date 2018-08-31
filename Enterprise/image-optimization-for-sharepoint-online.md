---
title: SharePoint Online 的图像优化
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: 了解如何使用呈现和动画层提高您的 SharePoint Online 网站上的图像性能。
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539554"
---
# <a name="image-optimization-for-sharepoint-online"></a><span data-ttu-id="17b05-103">SharePoint Online 的图像优化</span><span class="sxs-lookup"><span data-stu-id="17b05-103">Image optimization for SharePoint Online</span></span>

<span data-ttu-id="17b05-p101">网页加载速度取决于呈现页面包括图像、 HTML、 JavaScript、 和 CSS 所需的所有组件的总计大小。图像的好方法使您的网站更具吸引力，但其大小会影响性能。通过优化您的图像压缩和调整大小，以及使用动画层，您可以偏移非常大的图像的效果。使用 SharePoint 图像呈现形式，可以上载单个大型图像，并显示这使它被重用而不是重新加载的图像部分。</span><span class="sxs-lookup"><span data-stu-id="17b05-p101">The loading speed of a webpage depends on the combined size of all the components required to render the page including images, HTML, JavaScript, and CSS. Images are a great way to make your site more appealing, but their size can affect performance. By optimizing your images with compression and resizing, and using sprites, you can offset the effects of very large images. Using SharePoint image renditions, you can upload a single large image, and display sections of the image allowing it to be reused rather than reloaded.</span></span>
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a><span data-ttu-id="17b05-108">使用子画面以加快 SharePoint Online 中的图像加载速度</span><span class="sxs-lookup"><span data-stu-id="17b05-108">Using sprites to speed up image loading in SharePoint Online</span></span>

|||
|:-----|:-----|
| <span data-ttu-id="17b05-p102">图像画面包含多个较小的图像。使用 CSS 您选择绝对定位的页面的特定部分显示的复合图像的部件。一般情况下，您移动单个环绕而不是加载多个图像、 页面图像并将该图像的一小部分可见通过在其中显示动画层图像所需的部件的小窗口为最终用户。SharePoint Online 使用子画面画面 spcommon.png 中显示其各种图标。</span><span class="sxs-lookup"><span data-stu-id="17b05-p102">An image sprite contains many smaller images. Using CSS you select a part of the composite image to display on a particular part of the page with absolute positioning. Basically, you move a single image around the page instead of loading multiple images, and make a small part of that image visible through a small window where the required part of the sprite image is shown to the end user. SharePoint Online uses sprites to display its various icons in the sprite spcommon.png.</span></span>  <br/>  <span data-ttu-id="17b05-113">什么是此处介绍：</span><span class="sxs-lookup"><span data-stu-id="17b05-113">What's covered here:</span></span>  <br/>  <span data-ttu-id="17b05-114">图像压缩</span><span class="sxs-lookup"><span data-stu-id="17b05-114">Image compression</span></span>  <br/>  <span data-ttu-id="17b05-115">图像优化</span><span class="sxs-lookup"><span data-stu-id="17b05-115">Image optimization</span></span>  <br/>  <span data-ttu-id="17b05-116">SharePoint 图像呈现形式</span><span class="sxs-lookup"><span data-stu-id="17b05-116">SharePoint image renditions</span></span>  <br/> |![Spcommon 的屏幕截图](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
<span data-ttu-id="17b05-p103">这可以提高性能，因为下载而不是多个只有一个图像，然后缓存并重用该图像。即使图像不会保留缓存，通过单个图像而不是多个图像，此方法将减少页面加载时间的服务器到减少 HTTP 请求的总数。这真的是一种形式的图像捆绑。上面提供的 SharePoint 示例中所示，这是了如果图像不会更改经常，例如图标的非常有用的技术。您可以如何使用[Web Essentials](http://vswebessentials.com/)，第三方、 开放源代码、 社区基于项目在 Microsoft Visual Studio 中轻松地完成此任务。有关详细信息，请参阅[缩小和 SharePoint Online 中绑定](https://go.microsoft.com/fwlink/?LinkId=708698)。</span><span class="sxs-lookup"><span data-stu-id="17b05-p103">This can increase performance because you download only one image instead of several and then cache and reuse that image. Even if the image does not remain cached, by having a single image instead of multiple images, this method reduces the total number of HTTP requests to the server which will reduce page loading times. This is really a form of image bundling. This is a very useful technique if the images are not changing very often, for example, icons, as shown in the SharePoint example provided above. You can how to use [Web Essentials](http://vswebessentials.com/), a third-party, open-source, community-based project to achieve this easily in Microsoft Visual Studio. For more information, see [Minification and bundling in SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).</span></span>
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a><span data-ttu-id="17b05-124">使用图像压缩和优化以加快 SharePoint 中的页面加载速度</span><span class="sxs-lookup"><span data-stu-id="17b05-124">Using image compression and optimization to speed up page loading in SharePoint</span></span>

<span data-ttu-id="17b05-p104">图像压缩和优化用于降低在您的网站上使用的图像的文件大小。通常，减小图像大小的最佳方法是将图像调整到在网站上查看的最大尺寸。如果图像大于其将被查看的大小，则没有任何意义。使用图像编辑器确保图像尺寸正确是减少页面大小的快速、方便的方法。</span><span class="sxs-lookup"><span data-stu-id="17b05-p104">Image compression and optimization is about reducing the file size of the images you use on your site. Often, the best technique to reduce the size of an image is to resize the image to the maximum dimensions that it will be viewed on the site. There is no sense in having an image larger than it will ever be viewed. Making sure images are of the correct dimensions using an image editor is a quick and easy way to reduce the size of your page.</span></span>
  
<span data-ttu-id="17b05-p105">右大小图像后下, 一步是优化的这些图像压缩。没有可用于压缩和优化，包括照片库和第三方工具的各种工具。压缩的关键是文件的大小尽可能减少而不会明显的任何质量丢失面向最终用户。请确保测试以确保它们仍美观高清晰度显示屏上的压缩的文件。</span><span class="sxs-lookup"><span data-stu-id="17b05-p105">Once images are the right size, the next step is to optimize the compression of these images. There are various tools available to use for compression and optimization, including Photo Gallery and third-party tools. The key to compression is to reduce the file size as much as possible without losing any discernible quality for end users. Make sure you test your compressed files on a high-definition display to ensure they will still look good.</span></span>
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a><span data-ttu-id="17b05-133">使用 SharePoint 图像再现加快页面下载速度</span><span class="sxs-lookup"><span data-stu-id="17b05-133">Speed up page downloads by using SharePoint image renditions</span></span>

<span data-ttu-id="17b05-p106">图像呈现形式是中 SharePoint Online，从而可以提供基于预定义的图像维度的图像的不同版本的功能。没有用户生成图像内容或网站上的 CSS 已解决的图像如宽度和高度尺寸时，这一点尤其重要。即使图像所修复的 CSS 中，也仍然加载高分辨率图像。在这种情况下可以通过使用图像呈现形式减小文件大小。</span><span class="sxs-lookup"><span data-stu-id="17b05-p106">Image renditions are a feature in SharePoint Online that allows you to serve up different versions of images based on pre-defined image dimensions. This is especially important when there is user-generated image content or the image dimensions such as width and height are fixed by the CSS on the site. Even if an image is fixed by CSS, the full resolution image is still loaded. In this case the file size can be reduced by using image renditions.</span></span>
  
> [!NOTE]
> <span data-ttu-id="17b05-p107">启用了发布时仅适用于 SharePoint 呈现形式。您可以启用设置下的发布\>网站设置\>管理网站功能\>SharePoint Server 发布。否则，该选项将不会出现。</span><span class="sxs-lookup"><span data-stu-id="17b05-p107">Renditions are only available for SharePoint when publishing is enabled. You can enable publishing under Settings \> Site Settings \> Manage site features \> SharePoint Server Publishing. The option will not appear otherwise.</span></span> 
  
<span data-ttu-id="17b05-p108">调整图像再现大小的工作原理是，采用您定义的最小尺寸（宽度或高度），然后调整图像大小，以便其他尺寸根据锁定纵横比自动调整。默认情况下，它将从中心裁剪图像的剩余尺寸。例如，如果您定义的再现尺寸为 100 像素宽和 50 像素高，原始图像为 1000 像素宽和 800 像素高，它将重新调整，使 800 像素的高度现在为 50 像素，并从图像中心剪裁 1000 像素（现在为 62.5 像素）。</span><span class="sxs-lookup"><span data-stu-id="17b05-p108">The image rendition resizing works by taking the smallest dimension you define, either width or height, and then resizing the image so that the other dimension is automatically resized based on the locked aspect ratio. By default, it will crop the image from the center by the remaining dimensions. For example, if you define a rendition of 100px wide and 50px high and your original image is 1000px wide and 800px high, it will be resized so that the 800px dimension is now 50px and the 1000px dimension (now 62.5px) is cropped from the center of the image.</span></span>
  
<span data-ttu-id="17b05-p109">这些步骤相对比较简单，但要使图像使用呈现形式，在添加图像之前呈现形式需位于 SharePoint 网站上。此外，还需要已经启用 SharePoint Server 发布基础结构（网站集级别）和 SharePoint Server 发布（站点级别）功能。</span><span class="sxs-lookup"><span data-stu-id="17b05-p109">The steps are relatively simple but for images to use the renditions, the renditions need to be on the SharePoint site before you add the images. In addition, you also need to have the SharePoint Server Publishing Infrastructure (Site Collection Level) and SharePoint Server Publishing (Site Level) features turned on.</span></span>
  
 <span data-ttu-id="17b05-146">**添加图像呈现形式来加快页面加载**</span><span class="sxs-lookup"><span data-stu-id="17b05-146">**Add an image rendition to speed up page loading**</span></span>
  
1. <span data-ttu-id="17b05-147">请验证执行此过程的用户帐户，至少指向首要网站的网站集的设计权限网站正在发布到网页。</span><span class="sxs-lookup"><span data-stu-id="17b05-147">Verify that the user account that is performing this procedure has, at minimum, Design permissions to the top-level site of the site collection, and that the site is being published to a webpage.</span></span>
    
2. <span data-ttu-id="17b05-148">在 Web 浏览器中，转到发布网站集的顶级站点。</span><span class="sxs-lookup"><span data-stu-id="17b05-148">In a web browser, go to the top-level site of the publishing site collection.</span></span>
    
3. <span data-ttu-id="17b05-149">选择“设置”**** 图标。</span><span class="sxs-lookup"><span data-stu-id="17b05-149">Choose the **Settings** icon.</span></span> 
    
4. <span data-ttu-id="17b05-150">在“网站设置”**** 页面上的“外观和感觉”**** 部分中，您将看到内置图像呈现形式。</span><span class="sxs-lookup"><span data-stu-id="17b05-150">On the **Site Settings** page, in the **Look and Feel** section, you will see the built-in image renditions.</span></span> 
    
    <span data-ttu-id="17b05-151">您可以使用开箱即用的呈现形式，或选择“图像呈现形式”**** 创建一个新的。</span><span class="sxs-lookup"><span data-stu-id="17b05-151">You can use the out of the box renditions or choose **Image Renditions** to create a new one.</span></span> 
    
    ![图像呈现形式的屏幕截图](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. <span data-ttu-id="17b05-153">在“图像呈现形式”**** 页面上，选择“添加新项”****。</span><span class="sxs-lookup"><span data-stu-id="17b05-153">On the **Image Renditions** page, choose **Add new item**.</span></span>
    
    ![添加新项目的屏幕截图](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. <span data-ttu-id="17b05-155">在“新建图像呈现形式”**** 页面上的“名称”**** 框中，输入呈现形式的名称。</span><span class="sxs-lookup"><span data-stu-id="17b05-155">On the **New Image Rendition** page, in the **Name** box, enter a name for the rendition.</span></span> 
    
7. <span data-ttu-id="17b05-156">在“宽度”**** 和“高度”**** 文本框中，输入呈现形式的宽度和高度（以像素为单位），然后选择“保存”****。</span><span class="sxs-lookup"><span data-stu-id="17b05-156">In the **Width** and **Height** text boxes, enter the width and height, in pixels, of the rendition, and then choose **Save**.</span></span>
    
    ![图像再现名称的屏幕截图](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a><span data-ttu-id="17b05-158">在 SharePoint 中使用图像呈现形式进行自定义裁剪</span><span class="sxs-lookup"><span data-stu-id="17b05-158">Custom cropping with image renditions in SharePoint</span></span>

<span data-ttu-id="17b05-p110">默认情况下，从图像的中心生成图像呈现形式。您可以通过裁剪的图像的您想要使用的部分调整各个图像呈现的形式的图像。您可以裁剪上逐个，每呈现形式的图像。裁剪图像加快页面加载通过使用 SharePoint 的 blob 缓存创建的每个呈现形式的图像版本。因为图像只调整大小时一次，然后已准备好为最终用户提供服务多次，减少了这样的服务器负载。有关如何裁剪图像呈现形式的详细信息，请参阅[裁剪图像呈现形式](https://go.microsoft.com/fwlink/p/?LinkId=525626)。</span><span class="sxs-lookup"><span data-stu-id="17b05-p110">By default, an image rendition is generated from the center of the image. You can adjust the image rendition for individual images by cropping the portion of the image that you want to use. You can crop the images on an individual basis, per rendition. Cropping the images speeds up page loading by using SharePoint's blob cache to create a version of the image for each rendition. This way the server load is reduced because the image is only resized once and is then ready to serve to end users multiple times. For more information on how to crop an image rendition, see [Crop an image rendition](https://go.microsoft.com/fwlink/p/?LinkId=525626).</span></span>
  

