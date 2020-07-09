---
title: Office 365 内容传送网络（CDN）快速入门
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 内容传送网络（CDN）快速入门
ms.openlocfilehash: 4abaaa5545bc807c4da297c66fd9ad1fb188adc7
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "44561916"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Office 365 内容传送网络（CDN）快速入门

您可以使用内置的**Office 365 内容传递网络（CDN）** 来托管静态资产（图像、JavaScript、样式表、WOFF 文件），以便为您的 SharePoint Online 页面提供更好的性能。 Office 365 CDN 将静态资产缓存到距离请求这些资产的浏览器更近的位置，这样可以加快下载速度并减少延迟，进而提高性能。 此外，Office 365 CDN 使用 HTTP/2 协议改进了压缩和 HTTP 流水线功能。 Office 365 CDN 服务被归入 SharePoint Online 订阅。

有关更多详细信息指南，请参阅[使用 Office 365 内容传送网络（CDN）和 SharePoint Online](use-office-365-cdn-with-spo.md)。

>[!NOTE]
>Office 365 CDN 仅适用于生产（全球）云中的租户。 美国政府、中国和德国云中的租户目前不支持 Office 365 CDN。

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>使用 SharePoint 工具的页面诊断工具标识不在 CDN 中的项目

您可以使用 SharePoint 工具浏览器扩展的**页面诊断**功能，轻松列出可添加到 CDN 源的 sharepoint Online 页面中的资产。

**SharePoint 工具的页面诊断工具**是新 Microsoft Edge （ https://www.microsoft.com/edge) 和同时分析 SharePoint Online 新式门户和经典发布网站页面的 Chrome 浏览器）的浏览器扩展。 该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。 要安装和了解适用于 SharePoint 的页面诊断工具，请参阅[使用适用于 SharePoint Online 的页面诊断工具](https://aka.ms/perftool)。

当您在 SharePoint Online 页上运行 SharePoint 的页面诊断工具时，您可以单击 "**诊断测试**" 选项卡，以查看由 CDN 不承载的资产的列表。 这些资产将在标题**内容传递网络（CDN）检查**下列出，如下面的屏幕截图中所示。

![页面诊断](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>页面诊断工具仅适用于 SharePoint Online，无法用于 SharePoint 系统页面。

## <a name="cdn-overview"></a>CDN 概述

Office 365 CDN 旨在通过在高速全局网络中分布经常访问的对象（如图像和 javascript 文件）来优化用户的性能，从而减少页面加载时间，并以尽可能接近的方式向用户提供对承载对象的访问权限。 CDN 从称为 "_来源_" 的位置提取资产。 来源可以是可通过 URL 访问的 SharePoint 网站、文档库或文件夹。

Office 365 CDN 分为两种基本类型：

- **公用 CDN**旨在用于 JS （JavaScript）、CSS （样式表）、Web 字体文件（WOFF、WOFF2）和非专有图像（如公司徽标）。
- **专用 CDN**旨在用于图像（PNG、JPG、JPEG 等）。

您可以选择同时为您的组织提供公共来源或专用来源。 大多数组织将选择实现这两个的组合。 公用和专用选项都提供了类似的性能提升，但各自具有独特的特性和优势。 有关公用和专用 CDN 源的详细信息，请参阅[Choose 是否每个源应该是公共的还是专用](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)的。

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>如何使用默认配置启用公用和专用 CDN
在对租户 CDN 设置进行更改之前，应验证它是否符合组织的合规性、安全性和隐私策略。

有关更多详细的配置设置，或者如果您已启用 CDN 并想要添加其他位置（来源），请参阅[使用 SharePoint Online 命令行管理程序设置和配置 Office 365 CDN](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)一节

使用 SharePoint Online 命令行管理程序连接到你的租户：

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

若要使组织能够将公用源和专用源用于默认配置，请键入以下命令：

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

这些 cmdlet 的输出应该如下所示：

![SPOTenantCdnEnabled 的输出](media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>另请参阅

[使用 SharePoint Online 的页面诊断工具](https://aka.ms/perftool)

[结合使用 Office 365 内容分发网络和 SharePoint Online](use-office-365-cdn-with-spo.md)

[内容分发网络](https://aka.ms/o365cdns)

[Office 365 网络计划和性能优化](https://aka.ms/tune)

[SharePoint 性能系列-Office 365 CDN 视频系列](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
