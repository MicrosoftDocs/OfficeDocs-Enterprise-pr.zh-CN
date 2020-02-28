---
title: 结合使用 Office 365 内容分发网络和 SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/19/2020
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
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: 介绍如何使用 Office 365 内容传送网络（CDN）加快将 SharePoint Online 资产传递给所有用户，无论它们位于何处或如何访问你的内容。
ms.openlocfilehash: 25e7e6aae0d4dc6dd72278763c8fc5cc3bc454ce
ms.sourcegitcommit: 6ad59ab24a5dc8d27f448ca7fe4f6bdf7ab28066
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/27/2020
ms.locfileid: "42316021"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>结合使用 Office 365 内容分发网络和 SharePoint Online

可以使用内置的 Office 365 内容分发网络 (CDN) 来托管静态资产，以便提高 SharePoint Online 页面的性能。 Office 365 CDN 将静态资产缓存到距离请求这些资产的浏览器更近的位置，这样可以加快下载速度并减少延迟，进而提高性能。 此外，Office 365 CDN 使用[HTTP/2 协议](https://en.wikipedia.org/wiki/HTTP/2)改进了压缩和 HTTP 流水线功能。 Office 365 CDN 服务被归入 SharePoint Online 订阅。

> [!NOTE]
> Office 365 CDN 仅适用于**生产**（全球）云中的租户。 美国政府、中国和德国云中的租户目前不支持 Office 365 CDN。

Office 365 CDN 由多个 CDN 组成，用户可以在多个位置（即_源_）托管静态资产，并从全局高速网络提供这些资产。 可以添加**公共**源、**私有**源或同时添加这两种源，具体取决于想要托管在 Office 365 CDN 中的内容种类。 若要详细了解公共和专用来源之间的差异，请参阅[选择每个来源是否应为公共的或专用](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)的。

![Office 365 CDN 概念图](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 概念图")

如果您已经熟悉 Cdn 的工作方式，则只需完成几个步骤即可为租户启用 Office 365 CDN。 本主题介绍如何操作。 请参阅，了解有关如何开始托管静态资产的信息。

> [!TIP]
> 还有其他 Microsoft 托管的 Cdn，可用于专门使用方案的 Office 365，但不会在本主题中进行讨论，因为它们超出了 Office 365 CDN 的范围。 有关详细信息，请参阅[其他 Microsoft cdn](content-delivery-networks.md#other-microsoft-cdns)。

 **[面向 Office 365 的网络规划和性能调整的](https://aka.ms/tune)封底。**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>在 SharePoint Online 中使用 Office 365 CDN 的概述

若要为您的组织设置 Office 365 CDN，请按照以下基本步骤操作：

+ [规划 Office 365 CDN 的部署](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [确定要在 CDN 上托管的静态资产](use-office-365-cdn-with-spo.md#CDNAssets)。
  + [确定要存储资产的位置](use-office-365-cdn-with-spo.md#CDNStoreAssets)。 此位置可以是 SharePoint 网站、库或文件夹，也可以称为 "_源_"。
  + [选择每个源应该是公共的还是私有](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)的。 您可以添加公共类型和私有类型的多个源。

+ 使用 PowerShell 或 SharePoint Online CLI 设置和配置 CDN

  + [使用 SharePoint Online 命令行管理程序设置和配置 CDN](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  + [使用 PnP PowerShell 设置和配置 CDN](use-office-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [使用 Office 365 CLI 设置和配置 CDN](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  完成此步骤后，您将拥有：

  + 已为你的组织启用 CDN。
  + 添加了将每个源标识为公用或专用的来源。

完成设置后，可以通过以下方式[管理 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage)一段时间：
  
+ 添加、更新和删除资产
+ 添加和删除源
+ 配置 CDN 策略
+ 如有必要，禁用 CDN

最后，请参阅[使用 cdn 资产](use-office-365-cdn-with-spo.md#using-your-cdn-assets)了解如何从公共来源和专用来源访问 cdn 资产。

有关解决常见问题的指南，请参阅[Office 365 CDN 故障排除](use-office-365-cdn-with-spo.md#CDNTroubleshooting)。

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>规划 Office 365 CDN 的部署

在部署 Office 365 租户的 Office 365 CDN 之前，应考虑以下因素作为规划过程的一部分。

  + [确定要在 CDN 上托管的静态资产](use-office-365-cdn-with-spo.md#CDNAssets)
  + [确定要存储资产的位置](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  + [选择每个来源是公共还是私有](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>确定要在 CDN 上托管的静态资产

通常情况下，Cdn 在承载_静态资产_或不经常更改的资产时最为有效。 最好的经验法则是确定满足部分或所有条件的文件：

+ 嵌入在页面中的静态文件（如脚本和图像）可能会对页面加载时间产生重大的增量影响
+ 可执行文件和安装文件等大型文件
+ 支持客户端代码的资源库

例如，在将 SharePoint Online 网站添加到 CDN 源时，重复请求的小型文件（如网站图像和脚本）可以显著改进网站呈现性能，并在您的 SharePoint Online 网站上以增量方式减少负载。 可以从 CDN 下载更大的文件（如安装可执行文件），从而对 SharePoint Online 网站上的负载进行积极的性能影响和后续缩减，即使不经常访问这些文件也是如此。

每个文件的性能改进取决于许多因素，包括客户端离最近的 CDN 终结点、本地网络中的暂时条件等等。 许多静态文件非常小，可以从 Office 365 下载，不应超过一秒钟。 但是，网页可能包含多个嵌入文件，累积下载时间为几秒。 从 CDN 提供这些文件可显著缩短总页面加载时间。 请参阅[CDN 提供了哪些性能增益？](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)示例。

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>确定要存储资产的位置

CDN 从称为 "_来源_" 的位置提取资产。 来源可以是可通过 URL 访问的 SharePoint 网站、文档库或文件夹。 为您的组织指定源时具有极大的灵活性。 例如，您可以指定多个来源或要放置所有 CDN 资产的单个原点。 您可以选择同时为您的组织提供公共来源或专用来源。 大多数组织将选择实现这两个的组合。

您可以为您的起源（如文件夹或文档库）创建新的容器，并添加要从 CDN 中获取的文件。 如果要从 CDN 中获取一组特定的资产，并且希望仅将一组 CDN 资产限制为容器中的那些文件，这是一种很棒的方法。

您还可以将现有网站集、网站、库或文件夹配置为源，这将使容器中的所有符合条件的资产都可从 CDN 中获取。 在将现有容器添加为源之前，请务必确保您了解其内容和权限，以便不会无意中将资产暴露给匿名访问或未经授权的用户。

您可以定义_cdn 策略_以从 CDN 中排除来源的内容。 CDN 策略通过属性（如_文件类型_和_网站分类_）排除公用或专用来源的资产，并将其应用于您在策略中指定的 CdnType （private 或 public）的所有来源。 例如，如果添加了包含多个子网站的网站的专用源，则可以定义一个策略以排除标记为**机密**的网站，以便不会从 CDN 为应用了该分类的网站提供内容。 该策略将应用于已添加到 CDN 的_所有_私人来源的内容。
  
请注意，源数量越多，对 CDN 服务处理请求的时间会产生更大的影响。 建议尽可能多地限制源的数量。
  
<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>选择每个来源是公共还是私有

在标识原点时，指定是应将其设为_公共_的还是_私有_的。 对公共起源中的 CDN 资产的访问权限是匿名的，并且专用来源的 CDN 内容通过动态生成的令牌进行保护以实现更高的安全性。 无论您选择哪个选项，当涉及 CDN 本身的管理时，Microsoft 都会为你执行所有繁重的操作。 此外，您还可以在设置完 CDN 并确定来源之后，再改变主意。

公用和专用选项都提供了类似的性能提升，但各自具有独特的特性和优势。

可以以匿名方式访问 Office 365 CDN 内的**公共**来源，拥有该资产的 URL 的任何人都可以访问托管资产。 由于对公共源中内容的访问属于匿名访问，因此只能使用它们缓存非敏感的常规内容，如 javascript 文件、脚本、图标和图片。

Office 365 CDN 内的**专用**来源提供对用户内容（如 SharePoint Online 文档库、网站和专有图像）的专用访问。 对私人来源中的内容的访问受动态生成的令牌的保护，因此只能由对原始文档库或存储位置具有权限的用户访问。 Office 365 CDN 中的专用来源仅可用于 SharePoint Online 内容，并且您只能通过重定向从 SharePoint Online 租户访问私人来源的资产。

您可以详细了解如何在专用来源中[使用资产](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)的 CDN 访问在专用资源中的工作方式。

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>托管资产在公共起源中的特性和优势
  
+ 每个人都能匿名访问公用源中公开的资产。
    > [!IMPORTANT]
    > 永远不应将包含用户信息或被视为对您的组织敏感的资源置于公共来源中。
+ 如果从公用源中删除某资产，缓存会继续保留此资产最多 30 天；但此 CDN 资产的链接会在 15 分钟内失效。
+ 如果将样式表（CSS 文件）托管到公用源，可以在代码内使用相对路径和 URI。 也就是说，可以引用背景图像和其他对象相对于调用它的资产的位置。
+ 虽然可以硬编码公用源的 URL，但并不建议这样做。 这是因为，如果无法访问 CDN，URL 就不会在 SharePoint Online 中自动解析为相应组织，进而可能会导致链接失效和其他错误抛出。
+ 公共源中包含的默认文件类型为 .css、eot、.gif、.ico、jpeg、.jpg、.js、ttf、woff 和 woff2 中包含的默认文件类型的文件。 您可以指定其他文件类型。
+ 您可以配置策略以排除已由指定的网站分类标识的资产。 例如，可以选择排除所有标记为“机密”或“受限”的资产，即使它们的文件类型受支持且位于公用源中，也不例外。

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>托管资产在专用来源中的属性和优点

+ 专用来源仅可用于 SharePoint Online 资产。
+ 如果用户具有访问容器的权限，则用户只能从私有来源访问资产。 禁止匿名访问这些资产。
+ 私人来源中的资产必须从 SharePoint Online 租户中引用。 对专用 CDN 资产的直接访问不起作用。
+ 如果从专用来源中删除资产，该资产可能会从缓存中持续到一小时的可用状态;但是，在资产删除的15分钟内，我们将使 CDN 中的资产链接无效。
+ 默认情况下，支持为专用源添加下列类型的文件：.gif、.ico、.jpeg、.jpg、.js 和 .png。 您可以指定其他文件类型。
+ 与公共起源一样，您可以将策略配置为排除已由您指定的网站分类标识的资产，即使您使用通配符来包含文件夹或文档库中的所有资产也是如此。

有关使用 Office 365 CDN 的原因的详细信息，请参阅常规 CDN 概念和可与 Office 365 租户一起使用的其他 Microsoft Cdn。请参阅[Content 传递网络](content-delivery-networks.md)。

### <a name="default-cdn-origins"></a>默认 CDN 来源

除非另行指定，否则 Office 365 会在您启用 Office 365 CDN 时为您设置一些默认来源。 如果最初选择不设置它们，则可以在完成安装后添加这些来源。 除非您了解跳过默认来源设置并有特定原因需要执行此操作，否则应允许在启用 CDN 时创建这些后果。
  
默认专用 CDN 来源：
  
+ \*/userphoto.aspx
+ \*/siteassets

默认公共 CDN 来源：
  
+ \*/masterpage
+ \*/style 库
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets_是在12月2017的 OFFICE 365 CDN 服务中添加的默认公共来源。 为使 CDN 中的 SharePoint 框架解决方案正常工作，必须存在此来源。 如果在12月2017之前启用了 Office 365 CDN，或者在启用 CDN 时跳过了默认来源的设置，则可以手动添加此来源。 有关详细信息，请参阅[我的客户端 web 部件或 SharePoint 框架解决方案不起作用](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)。

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>使用 SharePoint Online 命令行管理程序设置和配置 Office 365 CDN

本节中的过程要求您使用 SharePoint Online 命令行管理程序连接到 SharePoint Online。 有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。

完成这些步骤，在 sharepoint online 中使用 SharePoint Online 命令行管理程序设置和配置 CDN 以托管你的资产。

<details>
  <summary>单击展开</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>使你的组织能够使用 Office 365 CDN

在对租户 CDN 设置进行更改之前，应在 Office 365 租户中检索专用 CDN 配置的当前状态。 使用 SharePoint Online 命令行管理程序连接到你的租户：

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

现在，使用**SPOTenantCdnEnabled** cmdlet 检索租户中的 CDN 状态设置：

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

指定 CdnType 的 CDN 状态将输出到屏幕上。

使用**SPOTenantCdnEnabled** cmdlet 可使您的组织使用 OFFICE 365 CDN。 您可以让您的组织同时使用公用来源、私人来源或同时使用这两者。 您还可以将 CDN 配置为在启用时跳过默认来源的设置。 您随时可以按照本主题中所述，在以后添加这些来源。
  
在 Windows Powershell for SharePoint Online 中：

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

例如，若要使组织能够使用公共来源和专用来源，请键入以下命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

若要使组织能够使用公共来源和专用来源，但跳过设置默认来源，请键入以下命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

有关在启用 Office 365 CDN 时默认设置的来源的信息以及跳过默认来源设置的潜在影响，请参阅[默认 CDN 来源](use-office-365-cdn-with-spo.md#default-cdn-origins)。

若要使组织能够使用公共来源，请键入以下命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

若要使您的组织使用专用来源，请键入以下命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

有关此 cmdlet 的详细信息，请参阅[SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx)。

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>更改要包含在 Office 365 CDN 中的文件类型列表（可选）

> [!TIP]
> 使用**运行 set-spotenantcdnpolicy** cmdlet 定义文件类型时，将覆盖当前定义的列表。 如果要向列表中添加其他文件类型，请先使用 cmdlet 找出已允许的文件类型，并将它们包含在列表中以及新的文件类型。
  
使用**运行 set-spotenantcdnpolicy** cmdlet 可以定义可由 CDN 中的公共和专用来源承载的静态文件类型。 默认情况下，允许使用常见资产类型，例如 .css、.gif、.jpg 和 .js。

在 Windows PowerShell for SharePoint Online 中：

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

例如，若要启用 CDN 以承载 .css 和 .png 文件，您需要输入以下命令：

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

若要查看 CDN 当前允许的文件类型，请使用**请运行 get-spotenantcdnpolicies** cmdlet：

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

有关这些 cmdlet 的详细信息，请参阅[运行 set-spotenantcdnpolicy](https://technet.microsoft.com/library/mt800839.aspx)和[请运行 get-spotenantcdnpolicies](https://technet.microsoft.com/library/mt800838.aspx)。

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>更改要从 Office 365 CDN 中排除的网站分类列表（可选）

> [!TIP]
> 当您使用**运行 set-spotenantcdnpolicy** cmdlet 排除网站分类时，将覆盖当前定义的列表。 如果要排除其他网站分类，请先使用 cmdlet 找出已排除的分类，然后将其添加到新的分类中。

运行 **Set-SPOTenantCdnPolicy** cmdlet 可以排除不想通过 CDN 提供的网站分类。 默认情况下，不排除任何网站分类。

在 Windows PowerShell for SharePoint Online 中：

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

若要查看当前受限制的网站分类，请使用**请运行 get-spotenantcdnpolicies** cmdlet：

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

将返回的属性为_IncludeFileExtensions_、 _ExcludeRestrictedSiteClassifications_和_ExcludeIfNoScriptDisabled_。

_IncludeFileExtensions_属性包含将从 CDN 提供服务的文件扩展名的列表。

> [!NOTE]
> 公用和专用的默认文件扩展名是不同的。

_ExcludeRestrictedSiteClassifications_属性包含要从 CDN 中排除的网站分类。 例如，您可以排除标记为**机密**的网站，以便不会从 CDN 为应用了该分类的网站中的内容提供服务。

_ExcludeIfNoScriptDisabled_属性基于网站级_NoScript_属性设置从 CDN 中排除内容。 默认情况下， _NoScript_属性设置为 "为_新式_网站**启用**"，并对_经典_网站**禁用**。 这取决于租户设置。

有关这些 cmdlet 的详细信息，请参阅[运行 set-spotenantcdnpolicy](https://technet.microsoft.com/library/mt800839.aspx)和[请运行 get-spotenantcdnpolicies](https://technet.microsoft.com/library/mt800838.aspx)。

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>为你的资产添加来源

使用**SPOTenantCdnOrigin** cmdlet 可以定义原点。 可以定义多个源。 源是 SharePoint 库或文件夹的 URL，其中包含要由 CDN 托管的资产。
  
> [!IMPORTANT]
> 永远不应将包含用户信息或被视为对您的组织敏感的资源置于公共来源中。

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

_Path_的值是包含这些资产的库或文件夹的相对路径。 除了相对路径之外，还可以使用通配符。 来源支持附加到 URL 的通配符。 这使您可以创建跨多个网站的来源。 例如，若要将所有网站的 masterpages 文件夹中的所有资源作为 CDN 中的公共来源包括在内，请键入以下命令：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ 通配符修饰符 ***/** 仅可在路径的开头使用，并将与指定 URL 下的所有 URL 段匹配。
+ 路径可以指向文档库、文件夹或网站。 例如，路径 _*/site1_将与网站下的所有文档库相匹配。

您可以添加具有特定相对路径的原点。 您不能使用完整路径添加原点。

本示例在特定网站上添加 siteassets 库的专用原点：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

本示例在网站集的 "网站资产" 库中添加 " _folder1_ " 文件夹的专用原点：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

如果路径中有空格，可以将路径括在双引号中，或将空格替换为 URL 编码 %20。 下面的示例将在网站集的 "网站资产" 库中添加_文件夹 1_文件夹的专用来源：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

有关此命令及其语法的详细信息，请参阅[外接程序 SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx)。

> [!NOTE]
> 在专用来源中，从来源共享的资产必须先发布主要版本，然后才能从 CDN 访问它们。
  
运行命令后，系统将同步整个数据中心的配置。 这最长可能需要15分钟。

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>示例：为您的母版页和为 SharePoint Online 的样式库配置公共原点

通常情况下，当您启用 Office 365 CDN 时，将为您设置这些来源。 但是，如果要手动启用它们，请按照以下步骤操作。
  
+ 使用**SPOTenantCdnOrigin** cmdlet 可将样式库定义为公共来源。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ 使用**SPOTenantCdnOrigin** cmdlet 可将母版页定义为公共源。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

有关此命令及其语法的详细信息，请参阅[外接程序 SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx)。

运行命令后，系统将同步整个数据中心的配置。 这最长可能需要15分钟。

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>示例：为 SharePoint Online 的网站资产、网站页面和发布图像配置专用来源

+ 使用**SPOTenantCdnOrigin** cmdlet 可以将 "网站资产" 文件夹定义为专用来源。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ 使用**SPOTenantCdnOrigin** cmdlet 可将 "网站页面" 文件夹定义为专用来源。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ 使用**SPOTenantCdnOrigin** cmdlet 可以将发布映像文件夹定义为专用源。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

有关此命令及其语法的详细信息，请参阅[外接程序 SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx)。

运行命令后，系统将同步整个数据中心的配置。 这最长可能需要15分钟。

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>示例：为 SharePoint Online 的网站集配置专用来源

使用**SPOTenantCdnOrigin** cmdlet 可将网站集定义为私有源。 例如：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

有关此命令及其语法的详细信息，请参阅[外接程序 SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx)。
  
运行命令后，系统将同步整个数据中心的配置。 您可能会看到一个预期的_配置挂起_消息，因为 SharePoint Online 租户连接到 CDN 服务。 这最长可能需要15分钟。

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>管理 Office 365 CDN

设置 CDN 后，您可以在更新内容或需要更改时对配置进行更改，如本节中所述。
  
<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>在 Office 365 CDN 中添加、更新或删除资产

完成设置步骤后，可以在需要时添加新资产，并更新或删除现有资产。 只需对您标识为来源的文件夹或 SharePoint 库中的资产进行更改即可。 如果添加新资产，可立即通过 CDN 使用它。 但是，如果您更新资产，最长需要15分钟才能在 CDN 中传播并变为可用的新副本。
  
如果需要检索原点的位置，则可以使用**运行 get-spotenantcdnorigins** cmdlet。 有关如何使用此 cmdlet 的信息，请参阅[运行 get-spotenantcdnorigins](https://technet.microsoft.com/library/mt790770.aspx)。

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>从 Office 365 CDN 中删除源

您可以删除您标识为来源的文件夹或 SharePoint 库的访问权限。 为此，请使用**SPOTenantCdnOrigin** cmdlet。

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

有关如何使用此 cmdlet 的信息，请参阅[SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790761.aspx)。

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>在 Office 365 CDN 中修改原点

您不能修改已创建的原点。 相反，请删除该原点，然后添加一个新的原点。 有关详细信息，请参阅[从 Office 365 CDN 中删除原点](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh)和[为资产添加来源](use-office-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh)。

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>禁用 Office 365 CDN

使用**SPOTenantCdnEnabled** cmdlet 为您的组织禁用 CDN。 如果您同时启用了 CDN 的公共和专用来源，则需要运行 cmdlet 两次，如以下示例所示。
  
若要禁用 CDN 中的公共来源，请输入以下命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

若要禁用 CDN 中的专用来源的使用，请输入以下命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

有关此 cmdlet 的详细信息，请参阅[SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx)。

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>使用 PnP PowerShell 设置和配置 Office 365 CDN

本节中的过程要求您使用 PnP PowerShell 连接到 SharePoint Online。 有关说明，请参阅[PnP PowerShell](https://github.com/SharePoint/PnP-PowerShell#getting-started)入门。

完成这些步骤，在 SharePoint Online 中使用 PnP PowerShell 设置和配置 CDN 以托管你的资产。

<details>
  <summary>单击展开</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>使你的组织能够使用 Office 365 CDN

在对租户 CDN 设置进行更改之前，应在 Office 365 租户中检索专用 CDN 配置的当前状态。 使用 PnP PowerShell 连接到你的租户：

``` powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

现在，使用**PnPTenantCdnEnabled** cmdlet 检索租户中的 CDN 状态设置：

``` powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

指定 CdnType 的 CDN 状态将输出到屏幕上。

使用**PnPTenantCdnEnabled** cmdlet 可使您的组织使用 OFFICE 365 CDN。 您可以让您的组织同时使用公用来源、专用来源或同时使用这两者。 您还可以将 CDN 配置为在启用时跳过默认来源的设置。 您随时可以按照本主题中所述，在以后添加这些来源。
  
在 PnP PowerShell 中：

``` powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

例如，若要使组织能够使用公共来源和专用来源，请键入以下命令：

``` powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

若要使组织能够使用公共来源和专用来源，但跳过设置默认来源，请键入以下命令：

``` powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

有关在启用 Office 365 CDN 时默认设置的来源的信息以及跳过默认来源设置的潜在影响，请参阅[默认 CDN 来源](use-office-365-cdn-with-spo.md#default-cdn-origins)。

若要使组织能够使用公共来源，请键入以下命令：

``` powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

若要使您的组织使用专用来源，请键入以下命令：

``` powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

有关此 cmdlet 的详细信息，请参阅[PnPTenantCdnEnabled](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled)。

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>更改要包含在 Office 365 CDN 中的文件类型列表（可选）

> [!TIP]
> 使用**PnPTenantCdnPolicy** cmdlet 定义文件类型时，将覆盖当前定义的列表。 如果要向列表中添加其他文件类型，请先使用 cmdlet 找出已允许的文件类型，并将它们包含在列表中以及新的文件类型。
  
使用**PnPTenantCdnPolicy** cmdlet 可以定义可由 CDN 中的公共和专用来源承载的静态文件类型。 默认情况下，允许使用常见资产类型，例如 .css、.gif、.jpg 和 .js。

在 PnP PowerShell 中：

``` powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

例如，若要启用 CDN 以承载 .css 和 .png 文件，您需要输入以下命令：

``` powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

若要查看 CDN 当前允许的文件类型，请使用**PnPTenantCdnPolicies** cmdlet：

``` powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

有关这些 cmdlet 的详细信息，请参阅[PnPTenantCdnPolicy](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy)和[PnPTenantCdnPolicies](https://docs.microsoft.com/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies)。

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>更改要从 Office 365 CDN 中排除的网站分类列表（可选）

> [!TIP]
> 当您使用**PnPTenantCdnPolicy** cmdlet 排除网站分类时，将覆盖当前定义的列表。 如果要排除其他网站分类，请先使用 cmdlet 找出已排除的分类，然后将其添加到新的分类中。

使用**PnPTenantCdnPolicy** cmdlet 可以排除您不希望通过 CDN 提供的站点分类。 默认情况下，不排除任何网站分类。

在 PnP PowerShell 中：

``` powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

若要查看当前受限制的网站分类，请使用**PnPTenantCdnPolicies** cmdlet：

``` powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

将返回的属性为_IncludeFileExtensions_、 _ExcludeRestrictedSiteClassifications_和_ExcludeIfNoScriptDisabled_。

_IncludeFileExtensions_属性包含将从 CDN 提供服务的文件扩展名的列表。

> [!NOTE]
> 公用和专用的默认文件扩展名是不同的。

_ExcludeRestrictedSiteClassifications_属性包含要从 CDN 中排除的网站分类。 例如，您可以排除标记为**机密**的网站，以便不会从 CDN 为应用了该分类的网站中的内容提供服务。

_ExcludeIfNoScriptDisabled_属性基于网站级_NoScript_属性设置从 CDN 中排除内容。 默认情况下， _NoScript_属性设置为 "为_新式_网站**启用**"，并对_经典_网站**禁用**。 这取决于租户设置。

有关这些 cmdlet 的详细信息，请参阅[PnPTenantCdnPolicy](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy)和[PnPTenantCdnPolicies](https://docs.microsoft.com/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies)。

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>为你的资产添加来源

使用**PnPTenantCdnOrigin** cmdlet 可以定义原点。 可以定义多个源。 源是 SharePoint 库或文件夹的 URL，其中包含要由 CDN 托管的资产。
  
> [!IMPORTANT]
> 永远不应将包含用户信息或被视为对您的组织敏感的资源置于公共来源中。

``` powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

_Path_的值是包含这些资产的库或文件夹的相对路径。 除了相对路径之外，还可以使用通配符。 来源支持附加到 URL 的通配符。 这使您可以创建跨多个网站的来源。 例如，若要将所有网站的 masterpages 文件夹中的所有资源作为 CDN 中的公共来源包括在内，请键入以下命令：

``` powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ 通配符修饰符 ***/** 仅可在路径的开头使用，并将与指定 URL 下的所有 URL 段匹配。
+ 路径可以指向文档库、文件夹或网站。 例如，路径 _*/site1_将与网站下的所有文档库相匹配。

您可以添加具有特定相对路径的原点。 您不能使用完整路径添加原点。

本示例在特定网站上添加 "网站资产" 库的专用来源：

``` powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

本示例在网站集的 "网站资产" 库中添加 " _folder1_ " 文件夹的专用原点：

``` powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

如果路径中有空格，可以将路径括在双引号中，或将空格替换为 URL 编码 %20。 下面的示例将在网站集的 "网站资产" 库中添加_文件夹 1_文件夹的专用来源：

``` powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

``` powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

有关此命令及其语法的详细信息，请参阅[外接程序 PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin)。

> [!NOTE]
> 在专用来源中，从来源共享的资产必须先发布主要版本，然后才能从 CDN 访问它们。
  
运行命令后，系统将同步整个数据中心的配置。 这最长可能需要15分钟。

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>示例：为您的母版页和为 SharePoint Online 的样式库配置公共原点

通常情况下，当您启用 Office 365 CDN 时，将为您设置这些来源。 但是，如果要手动启用它们，请按照以下步骤操作。
  
+ 使用**PnPTenantCdnOrigin** cmdlet 可将样式库定义为公共来源。

``` powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ 使用**PnPTenantCdnOrigin** cmdlet 可将母版页定义为公共源。

``` powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

有关此命令及其语法的详细信息，请参阅[外接程序 PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin)。

运行命令后，系统将同步整个数据中心的配置。 这最长可能需要15分钟。

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>示例：为 SharePoint Online 的网站资产、网站页面和发布图像配置专用来源

+ 使用**PnPTenantCdnOrigin** cmdlet 可以将 "网站资产" 文件夹定义为专用来源。

``` powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ 使用**PnPTenantCdnOrigin** cmdlet 可将 "网站页面" 文件夹定义为专用来源。

``` powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ 使用**PnPTenantCdnOrigin** cmdlet 可以将发布映像文件夹定义为专用源。

``` powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

有关此命令及其语法的详细信息，请参阅[外接程序 PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin)。

运行命令后，系统将同步整个数据中心的配置。 这最长可能需要15分钟。

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>示例：为 SharePoint Online 的网站集配置专用来源

使用**PnPTenantCdnOrigin** cmdlet 可将网站集定义为私有源。 例如：

``` powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

有关此命令及其语法的详细信息，请参阅[外接程序 PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin)。
  
运行命令后，系统将同步整个数据中心的配置。 您可能会看到一个预期的_配置挂起_消息，因为 SharePoint Online 租户连接到 CDN 服务。 这最长可能需要15分钟。

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>管理 Office 365 CDN

设置 CDN 后，您可以在更新内容或需要更改时对配置进行更改，如本节中所述。
  
<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>在 Office 365 CDN 中添加、更新或删除资产

完成设置步骤后，可以在需要时添加新资产，并更新或删除现有资产。 只需对您标识为来源的文件夹或 SharePoint 库中的资产进行更改即可。 如果添加新资产，可立即通过 CDN 使用它。 但是，如果您更新资产，最长需要15分钟才能在 CDN 中传播并变为可用的新副本。
  
如果需要检索原点的位置，则可以使用**PnPTenantCdnOrigin** cmdlet。 有关如何使用此 cmdlet 的信息，请参阅[PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin)。

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>从 Office 365 CDN 中删除源

您可以删除您标识为来源的文件夹或 SharePoint 库的访问权限。 为此，请使用**PnPTenantCdnOrigin** cmdlet。

``` powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

有关如何使用此 cmdlet 的信息，请参阅[PnPTenantCdnOrigin](https://docs.microsoft.com/powershell/module/sharepoint-pnp/remove-pnptenantcdnorigin)。

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>在 Office 365 CDN 中修改原点

您不能修改已创建的原点。 相反，请删除该原点，然后添加一个新的原点。 有关详细信息，请参阅[从 Office 365 CDN 中删除原点](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh)和[为资产添加来源](use-office-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh)。

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>禁用 Office 365 CDN

使用**PnPTenantCdnEnabled** cmdlet 为您的组织禁用 CDN。 如果您同时启用了 CDN 的公共和专用来源，则需要运行 cmdlet 两次，如以下示例所示。
  
若要禁用 CDN 中的公共来源，请输入以下命令：

``` powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

若要禁用 CDN 中的专用来源的使用，请输入以下命令：

``` powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

有关此 cmdlet 的详细信息，请参阅[PnPTenantCdnEnabled](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled)。

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a>使用 Office 365 CLI 设置和配置 Office 365 CDN

本节中的过程要求您已安装[Office 365 CLI](https://aka.ms/o365cli)。 接下来，使用[login](https://pnp.github.io/office365-cli/cmd/login/)命令连接到 Office 365 租户。

完成这些步骤，在 SharePoint Online 中使用 Office 365 CLI 设置和配置 CDN 以托管你的资产。

<details>
  <summary>单击展开</summary>

### <a name="enable-the-office-365-cdn"></a>启用 Office 365 CDN

可以运行 [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) 命令，在租户中管理 Office 365 CDN 的状态。

若要在租户中启用 Office 365 公用 CDN，请运行以下命令：

```sh
spo cdn set --type Public --enabled true
```

若要启用 Office 365 SharePoint CDN，请执行以下操作：

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>查看 Office 365 CDN 的当前状态

若要检查是否已启用或禁用特定类型的 Office 365 CDN，请使用[spo CDN get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/)命令。

若要检查 Office 365 公用 CDN 是否已启用，请运行以下命令：

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>查看 Office 365 CDN 来源

若要查看当前配置的 Office 365 公用 CDN 源，请运行以下命令：

```sh
spo cdn origin list --type Public
```

有关启用 Office 365 CDN 时默认设置的来源的信息，请参阅[默认 CDN 来源](use-office-365-cdn-with-spo.md#default-cdn-origins)。

### <a name="add-an-office-365-cdn-origin"></a>添加 Office 365 CDN 源

> [!IMPORTANT]
> 永远不要在配置为公共来源的 SharePoint 文档库中将被视为对您的组织敏感的资源放置。

运行 [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) 命令可以定义 CDN 源。 可以定义多个源。 源是 SharePoint 库或文件夹的 URL，其中包含要由 CDN 托管的资产。

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

其中`path` ，是包含资产的文件夹的相对路径。 除了相对路径之外，还可以使用通配符。

若要将所有网站的**母版页样式库**中的所有资产包含为公共来源，请执行以下操作：

```sh
spo cdn origin add --type Public --origin */masterpage
```

若要配置特定网站集的专用源，请运行以下命令：

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> 添加 CDN 源后，最长可能需要 15 分钟，才能通过 CDN 服务检索文件。 可以运行 [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) 命令，验证特定源是否已启用。

### <a name="remove-an-office-365-cdn-origin"></a>删除 Office 365 CDN 源

运行 [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) 命令可以删除指定类型 CDN 的 CDN 源。

若要从 CDN 配置中删除公用源，请执行以下操作：

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> 删除 CDN 源不会影响与该来源相匹配的任何文档库中存储的文件。 如果使用 SharePoint URL 引用这些资产，SharePoint 将自动切换回指向文档库的原始 URL。 但是，如果已使用公用 CDN URL 引用资产，则删除该原点将断开链接，您将需要手动更改它们。

### <a name="modify-an-office-365-cdn-origin"></a>修改 Office 365 CDN 源

无法修改现有 CDN 源。 而应运行 `spo cdn origin remove` 命令删除以前定义的 CDN 源，并运行 `spo cdn origin add` 命令添加新源。

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>更改要包含在 Office 365 CDN 中的文件类型

默认情况下，以下文件类型包含在 CDN： _.css、eot、.gif、.ico、.map、.jpg、ttf、woff 和 woff2_中的文件类型中。.、和。 如果需要在 CDN 中添加其他类型的文件，可以运行 [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) 命令更改 CDN 配置。

> [!NOTE]
> 如果更改文件类型列表，也就是覆盖当前定义的列表。 若要添加其他文件类型，请先运行 [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) 命令，确定当前配置的文件类型。

若要将_JSON_文件类型添加到公用 CDN 中包含的文件类型的默认列表中，请执行以下操作：

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>更改要从 Office 365 CDN 中排除的网站分类列表

运行 [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) 命令可以排除不想通过 CDN 提供的网站分类。 默认情况下，不排除任何网站分类。

> [!NOTE]
> 如果更改已排除的网站分类列表，也就是覆盖当前定义的列表。 若要排除其他分类，请先运行 [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) 命令，确定当前配置的分类。

若要从公用 CDN 中排除作为_HBI_分类的站点，请执行

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>禁用 Office 365 CDN

若要禁用 Office 365 CDN，请运行 `spo cdn set` 命令。例如：

```sh
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>使用 CDN 资产

现在，您已启用 CDN 和已配置的来源和策略，您可以开始使用 CDN 资产。

本部分将帮助您了解如何在 SharePoint 页面和内容中使用 CDN Url，以便 SharePoint 将公用源和专用来源的资产的请求重定向到 CDN。

+ [更新与 CDN 资产的链接](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [在公共来源中使用资产](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [在专用来源中使用资产](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

有关如何使用 CDN 来承载客户端 web 部件的信息，请参阅[从 Office 365 CDN 托管客户端 web 部件（Hello World 第4部分）](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)。

> [!NOTE]
> 如果将_ClientSideAssets_文件夹添加到**专用**CDN 来源列表中，则 CDN 承载的自定义 web 部件将无法呈现。 SPFX web 部件使用的文件只能利用公用 CDN 和 ClientSideAssets 文件夹作为公用 CDN 的默认来源。 

### <a name="updating-links-to-cdn-assets"></a>更新与 CDN 资产的链接

若要使用已添加到源中的资产，只需将指向原始文件的链接与原始文件的路径一起更新到原始文件。

+ 编辑包含已添加到来源的资产链接的页面或内容。 如果要更新指向给定资产的链接，则可以使用以下几种方法之一在进入网站或网站集中进行全局搜索和替换链接。
+ 对于指向源中的资产的每个链接，将路径替换为 CDN 源中的文件路径。 您可以使用相对路径。
+ 保存页面或内容。

例如，请考虑已复制到文档库文件夹中的图像 _/site/SiteAssets/images/image.png_ _/site/CDN_origins/public/_。 若要使用 CDN 资产，请将原始路径替换为指向源的路径，并将新 URL _/site/CDN_origins/public/image.png_。

如果要将完整 URL 用于资产而不是相对路径，请按如下所示构造链接：

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> 通常情况下，不应直接将 Url 硬编码到 CDN 中的资产。 但是，如果需要，您可以在公用源中手动构造资产的 Url。 有关详细信息，请参阅[HARDCODING CDN url for 公共资产](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets)。

若要了解如何验证资产是否通过 CDN 提供，请参阅[如何确认资产是否受 cdn 的服务？](use-office-365-cdn-with-spo.md#CDNConfirm)在 " [Office 365 CDN 的疑难解答](use-office-365-cdn-with-spo.md#CDNTroubleshooting)" 部分中。

### <a name="using-assets-in-public-origins"></a>在公共来源中使用资产

SharePoint Online 中的**发布功能**会自动将公共起源中存储的资产的 url 重写为其 CDN 等效项，以便从 cdn 服务而不是 SharePoint 提供资产。

如果您的源位于启用了 "发布" 功能的网站中，并且您要向 CDN 中转移的资产属于以下类别之一，则 SharePoint 将自动重写源中资产的 Url，前提是该资产尚未被 CDN 排除 政策.

下面概述了 SharePoint 发布功能自动重写的链接：

+ 经典发布页面 HTML 响应中的 IMG/LINK/CSS URL
  + 这包括作者在页面的 HTML 内容中添加的图像
+ 图片库幻灯片 Web 部件图像 URL
+ SPList REST API (RenderListDataAsStream) 结果中的图像字段
  + 使用新的属性_ImageFieldsToTryRewriteToCdnUrls_提供以逗号分隔的字段列表
  + 支持 hyperlink 字段和 PublishingImage 字段
+ SharePoint 图像呈现形式

下图演示了 SharePoint 收到来自公共来源的资产的页面请求时的工作流。

![工作流图表：从公共来源检索 Office 365 CDN 资产](media/O365-CDN/o365-cdn-public-steps-transparent.svg "工作流：从公共来源检索 Office 365 CDN 资产")

> [!TIP]
> 如果要对页面上的特定 Url 禁用自动重写，则可以签出该页面并添加查询字符串参数 **？NoAutoReWrites = true**指向要禁用的每个链接的末尾。

#### <a name="hardcoding-cdn-urls-for-public-assets"></a>Hardcoding 适用于公共资产的 CDN Url

如果没有为公用源启用_发布_功能，或者资产不是 cdn 服务自动重写功能支持的链接类型之一，则可以手动构建指向资产的 CDN 位置的 url，并在内容中使用这些 url。

> [!NOTE]
> 您不能将 CDN Url 硬编码到私有源中的资产，因为在请求资源时，会生成构成 URL 最后一部分的必需访问令牌。

对于公共 CDN 资产，URL 格式将如下所示：

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

将**TenantHostName**替换为你的租户名称。 示例：

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a>在专用来源中使用资产

使用专用来源的资产不需要额外的配置。 SharePoint Online 会自动为私人来源中的资产重写 Url，因此这些资产的请求将始终通过 CDN 提供。 无法在专用来源中手动生成 CDN 资产的 Url，因为这些 Url 包含在请求资产时必须由 SharePoint Online 自动生成的令牌。

对私人来源资产的访问受基于用户权限对源的动态生成令牌的保护，以及以下各节中介绍的注意事项。 用户必须至少具有对 CDN 的**读取**访问权限才能呈现内容。

下图说明了在 SharePoint 收到来自专用来源的资产的请求时，该工作流的工作流。

![工作流图表：从私有源检索 Office 365 CDN 资产](media/O365-CDN/o365-cdn-private-steps-transparent.svg "工作流：从私有源检索 Office 365 CDN 资产")

#### <a name="token-based-authorization-in-private-origins"></a>专用来源的基于令牌的授权

在 Office 365 CDN 中对私人来源的资产的访问权限由 SharePoint Online 生成的令牌授予。 如果用户已有权访问由来源指定的文件夹或库，则会自动向其授予允许用户根据其权限级别访问文件的令牌。 这些访问令牌在生成后有效期为30至90分钟，以帮助防止令牌重播攻击。

在生成访问令牌后，SharePoint Online 将向客户端返回一个自定义 URI，其中包含两个授权参数_吃_（边缘授权令牌）和_oat_ （原始授权令牌）。 每个令牌的结构在 " _Epoch 时间格式" 中< "到期时间" >__< "安全签名" >_。 例如：

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> 拥有令牌的任何人都可以访问 CDN 中的资源。 但是，包含这些访问令牌的 Url 仅通过 HTTPS 共享，因此，除非最终用户在令牌过期之前显式共享该 URL，否则，未经授权的用户将无法访问该资源。

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>私人来源的资产不支持项目级权限

请务必注意，SharePoint Online 不支持私人来源资产的项目级权限。 例如，对于位于的文件，在`https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`以下情况下，用户可以有效访问文件：

|用户  |Permissions  |有效访问  |
|---------|---------|---------|
|用户1     |有权访问 folder1         |可以从 CDN 访问 image1         |
|用户 2     |不具有对 folder1 的访问权限         |无法从 CDN 访问 image1         |
|用户 3     |不具有对 folder1 的访问权限，但被授予了在 SharePoint Online 中访问 image1 的显式权限         |可以直接从 SharePoint Online 访问资产 image1，但不能从 CDN 访问         |
|用户 4     |有权访问 folder1，但已明确拒绝对 SharePoint Online 中的 image1 的访问         |无法从 SharePoint Online 访问资产，但可以从 CDN 访问资产，尽管在 SharePoint Online 中拒绝对文件的访问         |

<a name="CDNTroubleshooting"> </a>
## <a name="troubleshooting-the-office-365-cdn"></a>Office 365 CDN 故障排除

<a name="CDNConfirm"> </a>
### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>如何确认 CDN 是否正在为资产提供服务？

将 CDN 资产的链接添加到页面后，您可以通过浏览页面来确认是否已从 CDN 提供资产，在呈现并查看图像 URL 后，右键单击该图像。

您还可以使用浏览器的开发人员工具来查看页面上的每个资源的 URL，或使用第三方网络跟踪工具。

> [!NOTE]
> 如果使用网络工具（例如 Fiddler）在从 SharePoint 页面呈现资产的外部测试您的资产，您必须手动将 referer 标头 "Referer： `https://yourdomain.sharepoint.com`" 添加到 URL 为 sharepoint Online 租户的根 URL 的 GET 请求中。

您无法直接在 web 浏览器中测试 CDN Url，因为您必须具有来自 SharePoint Online 的 referer。 但是，如果将 CDN 资产 URL 添加到 SharePoint 页面，然后在浏览器中打开该页面，则会看到页面上呈现的 CDN 资产。

有关在 Microsoft Edge 浏览器中使用开发人员工具的详细信息，请参阅[Microsoft Edge 开发人员工具](https://docs.microsoft.com/microsoft-edge/devtools-guide)。

若要观看[SharePoint 开发人员模式和实践 YouTube 频道](https://aka.ms/sppnp-videos)中托管的简短视频，演示如何验证 cdn 是否正常工作，请参阅[验证 cdn 使用情况和确保最佳网络连接](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5)。

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>为什么来自新来源的资产不可用？
新资源源中的资产不会立即可供使用，因为注册通过 CDN 传播以及将资产从来源上载到 CDN 存储需要花费时间。 在 CDN 中提供资产所需的时间取决于资产和文件的大小。

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>我的客户端 web 部件或 SharePoint 框架解决方案不起作用

为公共起源启用 Office 365 CDN 时，CDN 服务会自动创建以下默认来源：

+ */MASTERPAGE
+ */STYLE 库
+ */CLIENTSIDEASSETS

如果缺少 */clientsideassets 原点，SharePoint 框架解决方案将失败，并且不会生成警告或错误消息。 由于启用了 _-NoDefaultOrigins_参数设置为 **$true**，或者已手动删除了来源，因此此来源可能丢失。

您可以使用以下 PowerShell 命令查看是否存在哪些来源：

``` powershell
Get-SPOTenantCdnOrigins -CdnType Public
```

或者，您可以使用 Office 365 CLI 进行检查：

``` powershell
spo cdn origin list
```

若要在 PowerShell 中添加源，请执行以下操作：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

若要在 Office 365 CLI 中添加原点，请执行以下操作：

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>我需要哪些 PowerShell 模块和 CLI shell 才能与 Office 365 CDN 配合使用？

您可以使用**SharePoint Online 命令行管理**程序 PowerShell 模块或**office 365 CLI**选择使用 office 365 CDN。

+ [SharePoint Online 命令行管理程序入门](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
+ [安装 Office 365 CLI](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a>另请参阅

[内容分发网络](https://aka.ms/o365cdns)

[Office 365 网络计划和性能优化](https://aka.ms/tune)

[SharePoint 性能系列-Office 365 CDN 视频系列](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
