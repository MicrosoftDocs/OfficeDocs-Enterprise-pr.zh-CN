---
title: 在 SharePoint Online 中使用内容交付网络
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: '摘要: 本文介绍了内容传递网络 (Cdn), 以及如何使用它们来提高 SharePoint Online 性能。'
ms.openlocfilehash: 24b12ae60a8c089d8e32d2609957e8b0e3420510
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070578"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>在 SharePoint Online 中使用内容交付网络

 **摘要:** 本文介绍了内容传递网络 (Cdn), 以及如何使用它们提高 SharePoint Online 性能。 
  
在当今的 web 开发社区中, 您的 SharePoint 解决方案中可能包含许多常见库 (如 JavaScript 和 CSS 文件)。 其中许多由 Microsoft 在其 ASP CDN 上托管。 这意味着可以从这些分布式服务器中引用这些库, 并允许 internet 的内置 DNS 路由系统找到最接近您的用户的服务器。 本文中的示例演示从 SharePoint Online 服务器和 ASP CDN 下载受欢迎的库 jQuery 之间的时间差非常重要。 用户还可能已将 CDN 版本缓存在本地计算机上, 因此无需下载该文件。 如果您的用户在全球范围内以及在承载 SharePoint Online 网站的数据中心之外分布, 则这可能非常重要。
  
为 SharePoint Online 创建页面时, 延迟可能会受到用户与 SharePoint Online 实例的位置之间的物理距离的影响。 对于具有全局状态的组织来说, 这一点尤其重要, 即在全球的用户访问其内容时, 网站可能会托管在一个洲上。 Cdn 通过在与最终用户更近的不同位置承载某些常见的 web 资产来帮助缓解此情况。
  
由于 CDN 是托管相同文件的全球服务器网络, 因此客户端计算机会对存储在 Cdn 上的文件的 Internet Url 进行解释, 以便最接近用户的服务器可以为该文件提供服务。 执行此操作可大大减少网络往返行程导致的延迟。
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>为全球受众托管 SharePoint Online 网站的挑战

SharePoint Online 网站的承载位置与您在使用 Office 365 注册时所选的位置 (由用户指定) 相关的数据中心。 例如, 如果您的网站在美国的服务器上, 并且您有用户从东亚地区访问网站, 则可能由于数据与光纤光缆之间的距离的距离而导致出现延迟问题。
  
默认 SharePoint 用户界面使用的许多静态文件已托管在 Microsoft 的 Cdn 的全球网络中。 这将随着时间的推移改进性能。 但是, 如果您使用任何流行的 JavaScript 和 CSS 资产 (例如,JQuery、Modernizr、引导或 ASP.NET Ajax) 可以使用自由可用的 Cdn 来改进这些文件的加载时间。
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>使用 Cdn 提高下载速度的优势

由于各种原因, 使用 Cdn 可提高页面加载时间。 一个原因是 CDN 和用户之间的距离可能短于与 SharePoint Online 实例的距离。 这些网络是高度分布式的, 也旨在提高可用性和响应时间。 另一个原因是, 如果您使用的是常用的 CSS 文件库和 CDN, 则用户可能已缓存库, 甚至根本不需要下载它。
  
下面的屏幕截图展示了使用 Cdn 的优势。 这些屏幕截图来自 Internet Explorer 11 开发人员工具中的 "**网络**" 选项卡。 这些屏幕截图显示热门库 jQuery 的延迟。 若要弹出此屏幕, 请在 Internet Explorer 中, 按**F12**键并选择 "**网络**" 选项卡, 该选项卡 symbolized 带有 wi-fi 图标。 
  
![F12 网络的屏幕截图](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
此屏幕截图显示了上载到 SharePoint Online 网站上的母版页样式库的库。 上载库所需的时间为1.51 秒。
  
![加载时间为 1.51 秒的屏幕截图](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
第二个屏幕截图显示了由 Microsoft 的 CDN 提供的相同文件。 这次延迟约为496毫秒。 这是一项较大的改进, 显示整秒的时间是 shaved, 以下载页面内容的总时间。
  
![加载时间为 469 毫秒的屏幕截图](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>将 Cdn 与 SharePoint Server 2013 结合使用

使用 Cdn 仅在 SharePoint Online 上下文中有意义, 应避免使用 SharePoint Server 2013。 这是因为, 如果服务器位于本地或地理位置, 则与地理位置有关的所有优势都不成立。 此外, 如果与托管的服务器之间存在网络连接, 则可以在没有 Internet 连接的情况下使用网站, 因此无法检索 CDN 文件。 否则, 如果您的网站所需的库和文件有一个可用且稳定的功能, 则应使用 CDN。
  
## <a name="popular-cdns-and-how-to-use-them"></a>热门 Cdn 以及如何使用它们

Microsoft 的 Ajax CDN 可提供大多数热门库, 包括 jQuery (及其所有其他库)、ASP.NET Ajax、引导、挖空等。
  
若要将这些脚本包含在项目中, 只需将对这些公开的可用库的任何引用替换为对 CDN 地址的引用, 而不是将其包含在项目本身中。 例如, 使用以下代码链接到 jQuery:
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

有关 Cdn 的详细信息, 请参阅[Content 传递网络](content-delivery-networks.md)。
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>有关将 Cdn 与 SharePoint 结合使用的更多主题

[从 Office 365 CDN 承载客户端 web 部件](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

