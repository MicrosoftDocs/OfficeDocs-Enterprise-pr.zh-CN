---
title: 与 SharePoint Online 中使用 Office 365 内容交付网络
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: 介绍如何使用 Office 365 的内置内容交付网络 (CDN) 来加快您的 SharePoint Online 资产传递到您的所有用户，无论位于何处或访问您的内容的方式。
ms.openlocfilehash: fd118e8df404961e1c35c6297a788397f810d1a2
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "29547110"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a>与 SharePoint Online 中使用 Office 365 内容交付网络

您可以承载静态资产 Office 365 内容交付网络 (CDN) 中，以提供更好的性能的 SharePoint Online 网页。静态资产是不常改动，如图像、 视频和音频、 样式表、 字体和 JavaScript 文件的文件。CDN 工作为异地分布式缓存代理，方式是缓存静态资产接近浏览器请求它们。 
  
如果您已经熟悉 Cdn 工作的方式，您只需完成几个步骤，将它设置。本主题介绍如何。阅读有关 Office 365 CDN 和如何开始承载您的静态资产的信息。
  
 **在 Head 回[网络规划和性能优化 Office 365](https://aka.ms/tune)。**
  
## <a name="office-365-cdn-basics"></a>Office 365 CDN 基本知识

Office 365 CDN 是作为您的 SharePoint Online 订阅的一部分包含。您无需额外支付它。Office 365 提供支持两个专用和公共访问，并允许您在多个位置或来源主机静态资产。Office 365 CDN 不 Azure CDN 相同。如果需要有关为什么使用 CDN 或 CDN 的一般概念的详细信息，请参阅[内容交付网络](content-delivery-networks.md)。
  
## <a name="how-the-cdn-grants-access-to-end-users"></a>CDN 如何为最终用户授予访问权限

授予对 Office 365 CDN 中的静态资产的专用访问令牌由 SharePoint Online 生成。用户已有权访问的文件夹或指定原点的库将自动被授予令牌。SharePoint Online 不支持项目级权限的 CDN。
  
例如，对于文件位于`https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`，提供以下：
  
- 用户 1 有权访问 folder1 和 image1.jpg
    
- 2 用户不具有访问 folder1
    
- 用户 3 不具有访问 folder1，但是被授予访问 image1.jpg 通过 SharePoint Online 的显式权限
    
- 4 用户有权访问 folder1，但已被明确拒绝访问 image1.jpg
    
然后存在下列情况：
  
- 用户 1 和 4 时用户将能够通过 CDN 访问 image1.jpg。
    
- 2 用户和用户 3 将不能通过 CDN 访问 image1.jpg。
    
    但是，用户 3 仍可以访问资产 image1.jpg 直接通过 SharePoint Online 时用户 4 无法通过 SharePoint Online 访问资产。
    
## <a name="overview-of-working-with-the-office-365-cdn"></a>使用 Office 365 CDN 的概述

若要设置 Office 365 CDN，请按照下列基本步骤操作：
  
- CDN 部署规划：
    
  - 确定要在 Office 365 CDN 上承载的静态资产。有关如何使这些选项的详细信息，请参阅[内容交付网络](content-delivery-networks.md)。
    
  - [确定要用于存储您的资产](use-office-365-cdn-with-spo.md#CDNStoreAssets)。该位置是一个文件夹或 SharePoint 库，并调用来源。
    
  - 确定是否应公开或保密资产。执行此时您[选择每个来源是否应为公共或专用](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)。如果您希望，您可以在其中一些公共的多个来源和一些专用。
    
- [设置并使用 SharePoint Online Management Shell 配置 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNSetupinPShell)。完成此步骤后，您将具有：
    
  - 启用组织 CDN。
    
  - 添加您来源。标识为公共或专用的每个来源。
    
一次在完成安装，[管理 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage)段的时间： 
  
- 添加、 更新和删除资产
    
- 添加和删除来源
    
- 配置 CDN 策略
    
- 如有必要，禁用 Office 365 CDN
    
## <a name="determine-where-you-want-to-store-your-assets"></a>确定要用于存储您的资产

CDN 从称为原点位置提取您的资产。Office 365 的原点而言是 SharePoint 库或由 URL 可访问的文件夹。当您为您的组织指定来源，您可以非常灵活。例如，您可以指定多个来源，或要放入您的所有 CDN 资产的其中一个来源。您可以选择已为您的组织的公共或专用来源。大多数组织将选择实现的两个组合。
  
如果您定义数百来源，它将在处理请求所花费的时间可能产生负面影响。我们建议，如果您有超过 100 来源您可能需要重新考虑您的体系结构。
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a>选择每个来源是否应为公共或专用

标识来源，您可以指定是否应使其成为公共或专用。无论您选择哪个选项，Microsoft 会执行所有繁重，当谈到的 CDN 本身管理。此外，还可以更高版本，更改主意，设置 CDN 并标识您来源之后。
  
公用和专用选项提供性能改进，但每个具有唯一的属性和优点。
  
 **属性和托管中公共原点的资产的优点**
  
- 在公共原点中公开的资产进行匿名访问由每个人。
    
    > [!IMPORTANT]
    > 如果在您 CDN 识别公共的原点而言，应该从不将被视为对您的组织敏感公共原点或 SharePoint Online 的库中的资源。 
  
- 如果您从公共原点删除某项资产，资产可能继续提供最多 30 天从缓存;但是，我们将使 CDN 中的资源的链接无效 15 分钟内。
    
- 当主机中公共原点的样式表 （CSS 文件） 时，您可以使用代码中的相对路径和 Uri。这意味着您可以引用的背景图像和其他对象相对于调用它资产的位置的位置。
    
- 尽管您可以硬编码公共源的 URL，这样做，以便不建议。如果访问 CDN 变得不可用，URL 将自动解析为您的组织在 SharePoint Online 并可能导致断开的链接和其他错误的原因。
    
- 可供公共来源的默认文件类型是.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf 和.woff。您可以指定其他文件类型。
    
- 如果您希望，您可以配置要排除的已标识按您指定的网站分类资产的策略。例如，您可以选择要排除即使它们是允许的文件类型，并且位于公用原点标记为"confidential"或"受限"的所有资产。
    
 **属性和托管在专用的原点而言的资产的优点**
  
- 如果他们有权这样，用户仅可以从专用原点访问资产。阻止对这些资产的匿名访问。
    
- 如果专用原点中移除某项资产，可以继续资产以供最多为一个小时从缓存;但是，我们将使 CDN 中的资源的链接无效 15 分钟内。
    
- 默认文件类型都包括的专用的来源是.gif、.ico、.jpeg、.jpg、.js 和.png。您可以指定其他文件类型。
    
- 一样公共来源，您可以配置策略以排除资产已由网站分类指定即使使用通配符来包括文件夹或网站库内的所有资产的标识。
    
## <a name="default-office-365-cdn-origins"></a>默认 Office 365 CDN 来源

除非另外指定，否则 Office 365 设置某些默认来源，如果启用了 Office 365 CDN。如果您最初排除它们，您可以添加这些来源，完成安装之后。
  
默认专用来源：
  
- \*/userphoto.aspx
    
- \*/siteassets
    
默认公共来源：
  
- \*/masterpage
    
- \*/style 库

> [!NOTE]
> Clientsideassets 默认公共来源，以便如果必须公共 CDN 该时间之前，您将不会看到项自动添加，但如果以后创建已添加的 2017 年 12 月中，您将自动看到此更改。如果您想要阅读使用此 CDN 原点的示例，请参阅：[主机您从 Office 365 CDN （Hello World 第 4 部分） 的客户端 web 部件](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>设置和配置 Office 365 CDN 使用 SharePoint Online Management Shell

本主题中的过程要求您要用于连接到 SharePoint Online SharePoint Online Management Shell。有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。
  
完成这些步骤来设置和配置 Office 365 CDN，以承载您在 SharePoint Online 中的静态资产。
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a>若要启用您的组织使用 Office 365 CDN

使用**组 SPOTenantCdnEnabled** cmdlet 可让您的组织使用 Office 365 CDN。您可以让您的组织使用公共来源、 专用来源，或同时使用 CDN。您还可以配置 Office 365 CDN，以跳过的默认来源设置时启用它。本主题中所述稍后始终可以添加这些来源。 
  
在 SharePoint Online 的 Windows Powershell:
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

例如，若要启用您的组织使用 CDN 公用和专用来源，请键入以下命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

若要启用您的组织使用 CDN 公用和专用来源但跳过设置默认来源，请键入以下命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

若要启用您的组织使用 CDN 公共来源，请键入以下命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

若要启用您的组织使用 CDN 的专用来源，请键入以下命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

有关此 cmdlet 的详细信息，请参阅[设置 SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)。
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a>（可选）若要更改要在 Office 365 CDN 中包括的文件类型的列表
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> 使用**组 SPOTenantCdnPolicy** cmdlet 定义文件类型时，您会覆盖当前定义的列表。如果您想要向列表添加其他文件类型，该 cmdlet 首先使用以找出文件类型已允许和其包含新自以及列表中。 
  
使用**组 SPOTenantCdnPolicy** cmdlet 可定义的可由 CDN 中的公用和专用来源承载静态文件类型。默认情况下，将为示例.css、.gif、.jpg 和.js 允许常见的资源类型。 
  
在 SharePoint Online 的 Windows PowerShell:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

若要查看的 CDN 当前允许哪些文件类型，使用**Get-SPOTenantCdnPolicies** cmdlet: 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

有关这些 cmdlet 的详细信息，请参阅[设置 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[Get SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>（可选）若要更改您要从 Office 365 CDN 排除网站分类的列表
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> 排除时网站分类使用**集 SPOTenantCdnPolicy** cmdlet，您会覆盖当前定义的列表。如果您想要排除其他网站分类，使用 cmdlet 首先了解已排除哪些分类并然后将其添加以及您新的。 
  
使用**组 SPOTenantCdnPolicy** cmdlet 可以排除不希望公开通过 CDN 的网站分类。默认情况下，没有网站分类会被排除。 
  
在 SharePoint Online 的 Windows PowerShell:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

若要查看当前限制哪些网站分类，使用**Get-SPOTenantCdnPolicies** cmdlet: 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

有关这些 cmdlet 的详细信息，请参阅[设置 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[Get SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。
  
### <a name="to-add-an-origin-for-your-assets"></a>若要添加您的资产的来源
<a name="Office365CDNforSPOOrigin"> </a>

使用**添加 SPOTenantCdnOrigin** cmdlet 可以定义来源。您可以定义多个来源。原点是指向 SharePoint 库或包含您想要承载的 CDN 的资产的文件夹的 URL。 
  
> [!IMPORTANT]
> 如果在您 CDN 识别公共的原点而言，应永远不会将被视为对您的组织敏感的原点而言的公共或 SharePoint Online 的库中的资源。 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

其中路径是包含资产的文件夹的路径。您可以使用通配符除了相对路径。例如，要包含的所有资产在您的所有站点的 masterpages 文件夹中作为内 CDN 公共来源，请键入以下命令：
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

有关此命令和语法的详细信息，请参阅[添加 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。
  
运行此命令之后，系统将跨数据中心同步配置。这需要 15 分钟。
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>示例： 为 SharePoint Online 中配置公共的原点为您的母版页和样式库
<a name="ExamplePublicOrigin"> </a>

通常，这些来源是为您设置默认情况下当为 Office 365 CDN 启用公共来源。但是，如果您想要手动启用这些，请按照下列步骤。
  
- 使用**添加 SPOTenantCdnOrigin** cmdlet 可定义为公共原点而言的 Office 365 CDN 中的样式库。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- 使用**添加 SPOTenantCdnOrigin** cmdlet 可定义为公共原点而言的 Office 365 CDN 中的母版页。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- 有关此命令和语法的详细信息，请参阅[添加 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。
    
    运行此命令之后，系统将跨数据中心同步配置。这需要 15 分钟。
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>示例： 配置 SharePoint online 专用原点而言的网站资产、 网站页面和发布图像
<a name="ExamplePrivateOrigin"> </a>

- 使用**添加 SPOTenantCdnOrigin** cmdlet 可定义为私有原点而言的 Office 365 CDN 中的网站资产文件夹。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- 使用**添加 SPOTenantCdnOrigin** cmdlet 可定义为私有原点而言的 Office 365 CDN 中的网站页面文件夹。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- 使用**添加 SPOTenantCdnOrigin** cmdlet 可定义为私有原点而言的 Office 365 CDN 中的发布图像文件夹。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    有关此命令和语法的详细信息，请参阅[添加 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。
    
    运行此命令之后，系统将跨数据中心同步配置。这需要 15 分钟。
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>示例： SharePoint online 中配置网站集的专用来源
<a name="ExamplePrivateOriginSiteCollection"> </a>

使用**添加 SPOTenantCdnOrigin** cmdlet 可定义为私有原点而言的 Office 365 CDN 中的网站集。例如， 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

有关此命令和语法的详细信息，请参阅[添加 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。
  
运行此命令之后，系统将跨数据中心同步配置。这需要 15 分钟。
  
## <a name="manage-the-office-365-cdn"></a>管理 Office 365 CDN
<a name="CDNManage"> </a>

一旦您已设置 CDN，您可以更改您的配置随着更新内容或更改您的需求，本节中所述。
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a>若要添加、 更新或删除 Office 365 CDN 的资产
<a name="Office365CDNforSPOaddremoveasset"> </a>

完成安装步骤之后，您可以添加新资产和更新或删除现有资产，只要您希望。只需对标识为原点的 SharePoint 库或文件夹中的资产进行更改。如果您添加新的资源，可通过 CDN 立即是。但是，如果您更新资产，它需要 15 分钟传播和成为 CDN 中提供的新副本。
  
如果您需要检索的原点位置，您可以使用**Get-SPOTenantCdnOrigins** cmdlet。有关如何使用此 cmdlet 的信息，请参阅[Get SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx)。
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a>若要从 Office 365 CDN 删除来源
<a name="Office365CDNforSPORemoveOrigin"> </a>

如果需要则可以删除对文件夹或标识为原点的 SharePoint 库的访问。若要执行此操作，使用**删除 SPOTenantCdnOrigin** cmdlet。有关如何使用此 cmdlet 的信息，请参阅[删除 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx)。
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a>若要修改在 Office 365 CDN 来源
<a name="Office365CDNforSPORemoveOrigin"> </a>

不能修改您已创建来源。相反，删除原点，然后添加一个新。有关详细信息，请参阅[删除从 Office 365 CDN 原点](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin)和[添加您的资产的来源](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)。
  
### <a name="to-disable-the-office-365-cdn"></a>若要禁用 Office 365 CDN
<a name="Office365CDNforSPODisable"> </a>

使用**组 SPOTenantCdnEnabled** cmdlet 禁用组织 CDN。如果必须启用了 CDN 的两个公用和专用来源，您需要运行 cmdlet 的以下示例所示的两倍。 
  
若要禁用的 CDN，在 Windows Powershell for SharePoint Online 中的公共来源使用输入以下命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

若要禁用的专用来源 CDN 中使用，请输入以下命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

有关此 cmdlet 的详细信息，请参阅[设置 SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)。
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a>Office 365 CDN 配置疑难解答
<a name="CDNManage"> </a>

终结点将立即不可可供使用，直至扫描仪登记传播到整个 CDN 的时间。配置需要 15 分钟。
  

