---
title: 与 SharePoint Online 中使用内容交付网络
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 摘要： 本文介绍内容交付网络 (Cdn) 以及如何使用它们来提高 SharePoint Online 的性能。
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539644"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>与 SharePoint Online 中使用内容交付网络

 **摘要：** 本文介绍内容交付网络 (Cdn) 以及如何使用它们来提高 SharePoint Online 的性能。 
  
在当今的 web 开发社区、 有许多常见库 （例如 JavaScript 和 CSS 文件） 可能包括在 SharePoint 解决方案中。许多种由 Microsoft 在其 ASP CDN 上承载。这意味着您可以从这些分布式服务器引用这些库，并允许 internet 的内置 DNS 路由系统以查找用户的最接近服务器。本文中的示例演示如何从 SharePoint Online 与 ASP CDN 服务器下载受欢迎的库 jQuery 之间的时间差异是非常重要。用户还可能已经缓存在本地计算机上，以便它们没有要下载文件的 CDN 版本。这可以是如果有用户从承载您的 SharePoint Online 网站的数据中心分布式世界各地和远很重要。
  
为 SharePoint Online 创建页面时，您的用户和 SharePoint Online 实例的位置之间的物理距离可能会影响延迟。对于网站承载在一个大洲，而世界另一端的用户需要访问其内容的全球性组织来说，这一点尤其重要。CDN 有助于缓解这种情况，因为它在更靠近最终用户的不同位置承载某些流行的 Web 资产。
  
由于 CDN 是承载相同文件的服务器的全球网络，存储在 CDN 上的文件的 Internet URL 将由客户端计算机解析，以便由距离用户最近的服务器提供该文件。执行此操作大大降低了网络往返引起的延迟。
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>为全球受众承载 SharePoint Online 网站的挑战

SharePoint Online 网站承载在与您注册 Office 365 时选择的位置（由用户指定）相对的数据中心。例如，如果您的网站位于美国的服务器上，但您有用户从东亚地区访问网站，延迟问题可能由数据必须通过光缆传输的距离引起。
  
Microsoft 的 Cdn 的全球网络上已承载多个静态文件使用的默认 SharePoint 用户界面。这将提高段时间内的性能。但是，如果您使用任何受欢迎的 JavaScript 和 CSS 资产 （如;JQuery、 Modernizr、 引导或 ASP.NET Ajax） 您可以通过使用免费提供的 Cdn 提高这些文件的加载时间。
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>使用 CDN 改进下载速度的优点

使用 Cdn 可以提高各种原因的页面加载时间。一个原因是，可能比到 SharePoint Online 实例之间的距离短 CDN 和用户之间的距离。这些网络高度分布式，旨在还具有非常高可用性和响应时间。另一个原因是，如果您使用的 CSS 文件的常用库、 与 CDN 一起使用，用户可能已经缓存的库和它们甚至不需要根本下载。
  
以下屏幕快照说明如何使用 Cdn 的优点。以下屏幕截图是从 Internet Explorer 11 开发人员工具的**网络**选项卡。以下屏幕截图显示欢迎库 jQuery 延迟。要显示此屏幕中，在 Internet Explorer 中，按**f12 键**，然后选择**网络**选项卡，其中包含 Wi-fi 图标表示。 
  
![F12 网络的屏幕截图](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
此屏幕截图显示了上载到母版页样式库上的 SharePoint Online 网站本身的库。上载库所花的时间为 1.51 秒。
  
![加载时间为 1.51 秒的屏幕截图](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
第二个的屏幕截图显示了由 Microsoft 提供的相同文件 CDN。该时间延迟是围绕 496 毫秒。这是一大改进，并显示整个秒生产关闭下载页面内容的总时间。
  
![加载时间为 469 毫秒的屏幕截图](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>将 CDN 与 SharePoint Server 2013 结合使用

使用 Cdn 仅在 SharePoint Online 的上下文中有意义，应避免使用 SharePoint Server 2013 中使用。这是因为周围地理位置的优点的所有不保留 true 如果服务器是位于的本地或地理位置仍然关闭。此外，如果没有网络连接到服务器承载位置，然后网站可以使用未连接到 Internet 并因此无法检索 CDN 文件。否则，您应使用 CDN，如果没有一个可用且您的网站需要稳定的库和文件。
  
## <a name="popular-cdns-and-how-to-use-them"></a>常用的 CDN 及其使用方法

Microsoft 的 Ajax CDN 提供最常用的库，包括 jQuery （以及所有其其他库） 的 ASP.NET Ajax、 引导、 Knockout.js 及更多。
  
若要将这些脚本包含在您的项目中，只需将对这些公开可用的库的任何引用替换为对 CDN 地址的引用，而不是将其包含在项目本身。例如，使用以下代码可链接到 jQuery：
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

有关 Cdn 的详细信息，请参阅[内容交付网络](content-delivery-networks.md)。
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>有关与 SharePoint 结合使用 Cdn 的其他主题

[Office 365 CDN 中的托管客户端 web 部件](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

