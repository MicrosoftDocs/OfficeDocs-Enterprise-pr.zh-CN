---
title: SharePoint Online 中的缩小和捆绑
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/1/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: 本文介绍如何将缩小和捆绑技术与 Web Essentials 结合使用，以减少 HTTP 请求数，并减少在 SharePoint Online 中加载页面所需的时间。
ms.openlocfilehash: 3303ea49a1308e4ad7b3139547c20b4351fc84b5
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031307"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>SharePoint Online 中的缩小和捆绑

本文介绍如何将缩小和捆绑技术与 Web Essentials 结合使用，以减少 HTTP 请求数，并减少在 SharePoint Online 中加载页面所需的时间。
  
自定义您的网站时，您可以将大量额外文件添加到服务器以支持自定义。 添加额外的 JavaScript、CSS 和图像会增加对服务器的 HTTP 请求数，进而增加显示网页所需的时间。 如果有多个相同类型的文件，则可以捆绑这些文件以提高下载这些文件的速度。
  
对于 JavaScript 和 CSS 文件，您还可以使用一种名为缩小的方法，通过删除空格和其他不必要的字符，可以减小文件的总大小。
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>使用 Web Essentials 缩小和捆绑 JavaScript 和 CSS 文件

您可以使用第三方软件（如 Web Essentials）捆绑 CSS 和 JavaScript 文件。
  
> [!IMPORTANT]
> Web Essentials 是基于第三方的开放源代码的基于社区的项目。 本软件是对 Visual Studio 2012 和 Visual Studio 2013 的扩展，Microsoft 不支持该软件。 若要下载 Web Essentials，请访问网站[https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)。 
  
Web Essentials 提供了两种形式的捆绑：
  
- . 捆绑：用于 CSS 和 JavaScript 文件
    
- sprite：图像（仅在 Visual Studio 2013 中可用）
    
如果具有在自定义母版页中引用的一些品牌元素的现有功能，则可以使用 Web Essentials，例如：
  
![自定义母版页中的品牌元素的屏幕截图](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **在 Web Essentials 中创建 TE000127218 和 CSS 捆绑包**
  
1. 在 Visual Studio 中，在 "解决方案资源管理器" 中，选择要包含在捆绑包中的文件。
    
2. 右键单击所选文件，然后从上下文菜单中选择 " **Web Essentials** \> **创建 JavaScript 捆绑文件**"。 例如： 
    
    ![显示 Web Essentials 菜单选项的屏幕截图](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>查看捆绑 JavaScript 和 CSS 文件的结果

创建 JavaScript 和 CSS 捆绑包时，Web Essentials 将创建一个名为食谱文件的 XML 文件，用于标识 JavaScript 和 CSS 文件以及其他一些配置信息： 
  
![JavaScript 和 CSS 脚本文件的屏幕截图](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
此外，如果在捆绑绑定食谱中将缩小标志设置为 true，则文件的大小以及捆绑在一起会减小。 这意味着已创建可在母版页中引用的新的缩小版本的 JavaScript 文件。
  
![最小化标志设置为 true 的屏幕截图](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
从网站加载页面时，可以使用 web 浏览器（如 Internet Explorer 11）中的开发人员工具来查看发送到服务器的请求数以及每个文件加载所需的时间。
  
下图是在缩小之前加载 JavaScript 和 CSS 文件的结果。
  
![显示正在下载的 80 项的屏幕截图](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
将 CSS 和 JavaScript 文件捆绑在一起后，每个文件74丢弃的请求数与要单独下载的原始文件相比仅要长一些：
  
![显示正在下载的 74 项的屏幕截图](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
捆绑之后，JavaScript 捆绑文件将从815KB 显著减少到365KB：
  
![显示下载大小减小的屏幕截图](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>通过创建图像子画面捆绑图像

与捆绑 JavaScript 和 CSS 文件的方式类似，您可以将许多小图标和其他常见图像组合到一个较大的 sprite 表中，然后使用 CSS 来显示各个图像。 用户的 web 浏览器只下载一次动画工作表，然后将其缓存在本地计算机上，而不是下载每个单独的图像。 这可通过减少与 web 服务器的下载和往返次数来提高页面加载性能。
  
 **在 Web Essentials 中创建图像子画面**
  
1. 在 Visual Studio 中，在 "解决方案资源管理器" 中，选择要包含在捆绑包中的文件。
    
2. 右键单击所选文件，然后从上下文菜单中选择 " **Web Essentials** \> **创建图像子画面**"。 例如： 
    
    ![显示如何创建图像子画面的屏幕截图](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. 选择用于保存 sprite 文件的位置。 Sprite 文件是一个 XML 文件，用于描述 sprite 中的设置和文件。 下图显示了 sprite PNG 文件及其对应的 sprite XML 文件的示例。
    
    ![子画面文件的屏幕截图](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![子画面 XML 文件的屏幕截图](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

