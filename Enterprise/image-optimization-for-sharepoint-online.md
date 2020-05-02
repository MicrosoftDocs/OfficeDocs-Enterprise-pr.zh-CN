---
title: SharePoint Online 经典发布网站的图像优化
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
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
search.appverid:
- SPO160
- MET150
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: 了解如何使用格式副本和子画面提高 SharePoint Online 经典发布网站上的图像性能。
ms.openlocfilehash: 240c8240f8dec8ca24f9d231e319d35abc175c7f
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004575"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a>SharePoint Online 经典发布网站的图像优化

网页的加载速度取决于呈现页面所需的所有组件的总大小，包括图像、HTML、JavaScript 和 CSS。 图像是使网站更具吸引力的一种极好的方式，但其大小可能会影响性能。 通过使用压缩和调整大小以及使用子画面优化图像，可以偏移超大型图像的效果。 使用 SharePoint 图像呈现形式，可以上传一个大图像，并显示图像的各个部分，以允许重用而不是重新加载图像。

>[!NOTE]
>本主题适用于 SharePoint Online 经典发布网站，而不是新式门户网站。 有关 SharePoint Online 新式门户网站中的图像优化的信息，请参阅[在 Sharepoint online 新式门户页面中优化图像](modern-image-optimization.md)。
  
## <a name="using-sprites-to-speed-up-image-loading"></a>使用子画面加快图像加载速度

|||
|:-----|:-----|
| 图像子画面包含许多较小的图像。 使用 CSS 选择复合图像的一部分，以在页面的特定部分显示绝对定位。 通常情况下，您可以在页面上移动单个图像，而不是加载多个图像，并使该图像的一小部分在显示给最终用户的 sprite 图像所需部分的小窗口中可见。 SharePoint Online 使用子画面在 sprite spcommon 中显示其各种图标。  <br/>  这里讲述的内容：  <br/>  图像压缩  <br/>  图像优化  <br/>  SharePoint 图像呈现形式  <br/> |![Spcommon 的屏幕截图](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
这样可以提高性能，因为只需下载一幅图像而不是多个图像，然后再缓存并重新使用该图像。 即使图像未保持缓存，通过使用单个图像（而不是多个图像），此方法也可减少对服务器的 HTTP 请求总数，从而减少页面加载时间。 这实际上是一种图像绑定形式。 如果图像不经常更改（如上面提供的 SharePoint 示例中所示），这是一项非常有用的技术。 您可以使用[Web Essentials](https://vswebessentials.com/)（一种基于第三方的开放源代码的基于社区的项目）在 Microsoft Visual Studio 中轻松实现此目的。 有关详细信息，请参阅[SharePoint Online 中的缩小和捆绑](https://go.microsoft.com/fwlink/?LinkId=708698)。
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a>使用图像压缩和优化以加快页面加载速度

图像压缩和优化是为了减小在您的网站上使用的图像的文件大小。 通常情况下，减小图像大小的最佳方法是将图像大小调整为在网站上查看的最大尺寸。 如果图像大于查看的大小，则没有意义。 使用图像编辑器确保图像的尺寸是正确的，这是一种减小页面大小的快速而简单的方法。
  
图像大小正确后，下一步是优化这些图像的压缩。 有多种工具可用于压缩和优化，包括照片库和第三方工具。 要进行压缩的关键是，尽量减小文件大小，而不会丢失最终用户的任何可辨识的质量。 请确保在高清晰度显示中测试压缩文件，以确保它们仍显示良好。
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>使用 SharePoint 图像呈现方式加快页面下载速度

图像呈现形式是 SharePoint Online 中的一项功能，允许您根据预定义的图像尺寸提供不同版本的图像。 当网站上的 CSS 修复了用户生成的图像内容或图像尺寸（如宽度和高度）时，这一点尤其重要。 即使图像是通过 CSS 修复的，仍会加载完整的分辨率图像。 在这种情况下，可以使用图像呈现形式来减少文件大小。
  
> [!NOTE]
> 仅当启用发布时，才可使用 SharePoint 的呈现形式。 你可以在 "设置\> " 网站设置\>下启用发布\> "管理网站功能" SharePoint Server 发布。 否则，此选项将不会显示。
  
通过获取定义的最小尺寸（宽度或高度），然后调整图像大小，以便根据锁定纵横比自动调整其他尺寸的大小，从而使图像呈现形式的大小调整正常。 默认情况下，它会将图像从中心裁剪到剩余的尺寸。 例如，如果您定义100px 宽和50px 的一个格式副本，并且原始图像为1000px 宽且800px 高，则将调整其大小，以便800px 维度现在为50px，而1000px 维度（"now 62.5 px"）将从图像的中心进行裁剪。
  
这些步骤相对简单，但要使用呈现形式的图像，在添加图像之前，必须在 SharePoint 网站上的呈现形式。 此外，还需要启用 SharePoint Server 发布基础结构（网站集级别）和 SharePoint Server 发布（网站级别）功能。
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a>添加图像呈现形式以加快页面加载速度
  
1. 确认执行此过程的用户帐户至少具有对网站集的首要网站的 "设计" 权限，并且该网站发布到网页。

2. 在 web 浏览器中，转到发布网站集的首要网站。

3. 选择"设置"图标。

4. 在 "**网站设置**" 页上的 "**外观**" 部分中，您将看到内置的图像呈现形式。

    您可以使用 "现成" 格式副本或选择 "**图像呈现形式**" 来创建一个新的。

    ![图像呈现形式的屏幕截图](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. 在“图像呈现形式”**** 页上，选择“添加新项”****。

    ![添加新项目的屏幕截图](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. 在"新建图像呈现形式"页上的"名称"框中，为呈现形式输入名称。

7. 在"宽度"和"高度"文本框中，输入呈现形式的宽度和高度（以像素为单位），然后选择"保存"。

    ![图像再现名称的屏幕截图](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a>使用图像呈现形式的自定义裁剪

默认情况下，图像呈现形式在图像中心生成。 您可以调整单个图像的图像呈现形式，具体方法是裁剪要使用的图像部分。 您可以按每个节目逐个对图像进行裁剪。 裁剪图像可通过使用 SharePoint 的 blob 缓存为每个节目创建一个版本的图像，从而加快页面加载速度。 通过这种方式，服务器负载会降低，因为仅调整了图像大小一次，然后准备将其提供给最终用户多次。 有关如何裁剪图像呈现形式的详细信息，请参阅[裁剪图像呈现形式](https://go.microsoft.com/fwlink/p/?LinkId=525626)。
  

