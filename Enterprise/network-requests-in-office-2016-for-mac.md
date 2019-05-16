---
title: Office for Mac 中的网络请求
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Office for Mac 应用程序在 macOS 平台上提供了本机应用程序体验。 每个应用程序设计为在各种情况下运行, 包括在没有网络访问权限的情况下使用的状态。 当计算机连接到网络时, 应用程序将自动连接到一系列基于 web 的服务, 以提供增强功能。 本白皮书介绍了应用程序尝试访问的终结点和 Url, 以及提供的服务。 此信息在对网络配置问题进行故障排除以及为网络代理服务器设置策略时非常有用。 本文中的详细信息旨在补充 Office 365 URL 和地址范围文章。
ms.openlocfilehash: 0493fcc0954456ed190791b089fe4e0a568e82d7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069650"
---
# <a name="network-requests-in-office-for-mac"></a>Office for Mac 中的网络请求

Office for Mac 应用程序在 macOS 平台上提供了本机应用程序体验。 每个应用程序设计为在各种情况下运行, 包括在没有网络访问权限的情况下使用的状态。 当计算机连接到网络时, 应用程序将自动连接到一系列基于 web 的服务, 以提供增强功能。 以下信息介绍了应用程序尝试访问的终结点和 Url, 以及提供的服务。 此信息在对网络配置问题进行故障排除并为网络代理服务器设置策略时非常有用。 本文中的详细信息旨在补充[Office 365 URL 和地址范围的文章](urls-and-ip-address-ranges.md), 其中包括运行 Microsoft Windows 的计算机的终结点。 除非另行说明, 否则本文中的信息也适用于 Office 2019 for mac 和 Office 2016 for Mac, 可用作来自零售商店的一次性购买或通过批量许可协议。 

  
本文大部分是详细介绍网络 Url、类型和该终结点提供的服务或功能说明的表格。 每个 Office 应用程序的服务和终结点的使用可能各不相同。 下面的表中定义了以下应用程序:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
URL 类型定义如下:
  
- ST: Static-URL 已硬编码到客户端应用程序中。
    
- SS: 半静态-URL 作为网页或重定向器的一部分进行编码。
    
- CS: Config Service-URL 作为 Office 配置服务的一部分返回。

    
## <a name="office-for-mac-default-configuration"></a>Office for Mac 默认配置

 **安装和更新**
  
以下网络终结点用于从 Microsoft Content 传递网络 (CDN) 下载 Office for Mac 安装程序。
  
|**URL**|**类型**|**说明**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |圣保罗  <br/> |Office 365 安装门户将链接服务到最新的安装程序包。  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |内容传递网络上安装包的位置。  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |内容传递网络上安装包的位置。  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |圣保罗  <br/> |Microsoft 自动更新的管理控制终结点  <br/> |
   
 **首次应用启动**
  
首次启动 Office 应用时, 将会联系到以下网络终结点。 这些终结点为用户提供增强的 Office 功能, 而不管许可证类型 (包括批量许可证安装) 如何联系 Url。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |圣保罗  <br/> |"Flighting" 配置-允许功能细调和实验。  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |圣保罗  <br/> |"Flighting" 网络配置测试  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |圣保罗  <br/> |"Flighting" 网络配置测试  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |圣保罗  <br/> |Office 配置服务-服务终结点的主列表。  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |圣保罗  <br/> |Office 规则遥测下载-通知客户端要上载到遥测服务的数据和事件。  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |客户  <br/> |OneNote 遥测服务  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |圣保罗  <br/> |Office 遥测上载报告-将客户端上发生的 "Heartbeart" 和错误事件上传到遥测服务。  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |客户  <br/> |Office Online 模板服务-为用户提供联机文档模板。  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |客户  <br/> |Office 模板下载-PNG 模板图像的存储。  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |客户  <br/> |Office 应用的存储配置。  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |客户  <br/> |Office Document Integration Services 目录 (服务和终结点列表) 和主领域发现。  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |客户  <br/> |适用于家庭领域发现 v2 的资源 (15.40 及更高版本)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |圣保罗  <br/> |Microsoft 自动更新清单-检查以查看是否有可用更新  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft Ajax JavaScript 库  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |固件  <br/> |SS  <br/> |适用于 Office 的维基百科应用配置和资源。  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |适用于 Office 配置和资源的 Bing 地图应用程序。  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |面向 Office 的人员配置和资源应用程序的关系图。  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |圣保罗  <br/> |OneNote 的新增内容。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |圣保罗  <br/> |OneNote 的新内容。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |OneNote 的新增内容图像。  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |圣保罗  <br/> |应用程序内支持服务。  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |圣保罗  <br/> |电子邮件帐户检测服务。  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |圣保罗  <br/> |Outlook 自动发现  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |圣保罗  <br/> |适用于 Office 365 服务的 Outlook 终结点。  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |圣保罗  <br/> |Outlook 外接程序的图标。  <br/> |
   
> [!NOTE]
> Office 配置服务充当所有 Microsoft Office 客户端 (而不仅仅是 Mac) 的自动发现服务。 在响应中返回的终结点在此更改中非常不频繁, 但仍可能是完全静态的。 
  
 **登录**
  
登录到基于云的存储时, 将联系以下网络终结点。 根据您的帐户类型, 可以联系到不同的服务。 例如：
  
- **MSA: Microsoft 帐户**-通常用于消费者和零售方案 
    
- **OrgID: 组织帐户**-通常用于商业方案 
    
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |圣保罗  <br/> |Windows 授权服务  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |圣保罗  <br/> |Office 365 登录服务 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |圣保罗  <br/> |Microsoft 帐户登录服务 (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |客户  <br/> |Microsoft 帐户登录服务帮助程序 (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Office 365 登录品牌 (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |客户  <br/> |文档和位置存储定位程序  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |客户  <br/> |最近使用的 (MRU) 文档服务  <br/> |
   
> [!NOTE]
> 对于基于订阅的许可证和零售许可证, 登录既激活了产品, 又支持对云资源 (如 OneDrive) 的访问。 对于批量许可证安装, 仍会提示用户登录 (默认情况下), 但仅当产品已激活时, 才需要访问云资源。 
  
 **产品激活**
  
以下网络终结点适用于 Office 365 订阅和零售许可证激活。 具体来说, 这不会应用于批量许可证安装。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |客户  <br/> |Office 许可服务  <br/> |
   
 **新增内容**
  
以下网络终结点仅适用于 Office 365 订阅。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |新增功能 JSON 页面内容。  <br/> |
   
 **研究工具**
  
以下网络终结点仅适用于 Office 365 订阅。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |固件  <br/> |客户  <br/> |研究工具 Web 服务  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |固件  <br/> |客户  <br/> |研究工具静态内容  <br/> |
|```https://www.bing.com/```  <br/> |固件  <br/> |客户  <br/> |研究工具内容提供程序  <br/> |
   
 **智能查找**
  
以下网络终结点适用于 Office 365 订阅和零售/批量许可证激活。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |客户  <br/> |Insights Web 服务  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |客户  <br/> |JQuery 库  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |客户  <br/> |支持 JavaScript 库  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |客户  <br/> |Insights 内容提供程序  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |客户  <br/> |Insights 内容提供程序  <br/> |
   
 **PowerPoint 设计器**
  
以下网络终结点仅适用于 Office 365 订阅。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |客户  <br/> |PowerPoint Designer web 服务  <br/> |
   
 **PowerPoint 快速启动**
  
以下网络终结点仅适用于 Office 365 订阅。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |客户  <br/> |PowerPoint 快速启动 web 服务  <br/> |
   
 **发送微笑/哭脸**
  
以下网络终结点适用于 Office 365 订阅和零售/批量许可证激活。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |客户  <br/> |发送微笑服务  <br/> |
   
 **联系支持人员**
  
以下网络终结点适用于 Office 365 订阅和零售/批量许可证激活。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |客户  <br/> |联系支持服务  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |客户  <br/> |应用程序内支持服务  <br/> |
   
 **另存为 PDF**
  
以下网络终结点适用于 Office 365 订阅和零售/批量许可证激活。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |固件  <br/> |客户  <br/> |Word 文档转换服务 (PDF)  <br/> |
   
 **Office 应用 (亦称为 "外接程序")**
  
当 Office 应用外接程序受信任时, 以下网络终结点适用于 Office 365 订阅和零售/批量许可证激活。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |客户  <br/> |Office 应用商店配置  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |固件  <br/> |SS  <br/> |维基百科应用资源  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing 地图应用资源  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |人员关系图应用程序资源  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office 重定向服务  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office JavaScript 库  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |适用于 Office 应用的遥测和报告服务  <br/> |
|```https://ajax.microsoft.com/```  <br/> |固件  <br/> |SS  <br/> |Microsoft Ajax JavaScript 库  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft Ajax JavaScript 库  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office JavaScript 库  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |支持资源  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |支持资源  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |支持资源  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |JavaScript 库  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |错误报告  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |字体资源  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |遥测服务  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |遥测报告  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Microsoft Store 资产库  <br/> |
|```https://*.wikipedia.org/```  <br/> |固件  <br/> |SS  <br/> |维基百科页面资源  <br/> |
|```https://upload.wikimedia.org/```  <br/> |固件  <br/> |SS  <br/> |维基百科媒体资源  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |固件  <br/> |SS  <br/> |维基百科沙盒框架  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |地图模板  <br/> |
   
 **安全链接**
  
以下网络终结点仅适用于 Office 365 订阅的所有 Office 应用程序。
  
|**URL**|**类型**|**说明**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |客户  <br/> |Microsoft 安全链接服务  <br/> |
   
 **故障报告**
  
以下网络终结点适用于 Office 365 订阅和零售/批量许可证激活的所有 Office 应用程序。 当某个进程意外地发生故障时, 将生成报告并将其发送到 Watson 服务。
  
|**URL**|**类型**|**说明**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |圣保罗  <br/> |Microsoft 错误报告服务  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |圣保罗  <br/> |Office 协作 Insights 服务  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>用于减少网络请求和流量的选项

Office for Mac 的默认配置提供了最佳用户体验, 包括功能和保持计算机为最新状态。 在某些情况下, 您可能希望阻止应用程序与网络终结点联系。 本部分讨论用于执行此操作的选项。
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>禁用云登录和 Office 外接程序
  
批量许可客户可能对将文档保存到基于云的存储具有严格的策略。 可以将以下每个应用程序的首选项设置为禁用 MSA/OrgID 登录, 并访问 Office 外接程序。
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

如果用户尝试访问登录功能, 则会看到一条错误消息, 指出网络连接不存在。 由于此首选项也阻止联机产品激活, 因此只应将其用于批量许可证安装。 具体而言, 使用此首选项将阻止 Office 应用程序访问以下终结点:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- 上面的 "登录" 一节中列出的所有终结点。
    
- 上面的 "智能查找" 部分中列出的所有终结点。
    
- 上面的 "产品激活" 一节中列出的所有终结点。
    
- 上面的 "Office 应用 (称为外接程序)" 一节中列出的所有终结点。
    
若要为用户重新建立完整的功能, 请将首选项设置为 "2" 或将其删除。
  
> [!NOTE]
> 此首选项需要 Office for Mac build 15.25 [160726] 或更高版本。 
  
### <a name="telemetry"></a>遥测
  
Office for Mac 定期以固定时间间隔向 Microsoft 发送遥测信息。 将数据上载到 "结点" 终结点。 遥测数据可帮助工程团队评估每个 Office 应用程序的运行状况和任何意外行为。 有两种类别的遥测:
  
- **检测信号**包含版本和许可证信息。 此数据将在应用程序启动时立即发送。 
    
- **用法**包含有关如何使用应用程序和非致命错误的信息。 此数据每60分钟发送一次。 
    
Microsoft 会认真对待你的隐私。 你可以在上[https://privacy.microsoft.com](https://privacy.microsoft.com)阅读有关 Microsoft 的数据收集策略的信息。 若要防止应用程序发送 "Usage" 遥测, 可以调整**SendAllTelemetryEnabled**首选项。 首选项为每个应用程序, 可以通过 macOS 配置文件进行设置, 也可以通过终端手动进行设置: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

始终发送检测信号遥测, 且不能禁用。
  
### <a name="crash-reporting"></a>故障报告
  
出现致命的应用程序错误时, 应用程序将意外终止并将故障报告上传到 "Watson" 服务。 故障报告由调用堆栈组成, 该堆栈是应用程序处理的导致崩溃的步骤列表。 这些步骤可帮助工程团队确定失败的确切功能以及原因。
  
在某些情况下, 文档的内容将导致应用程序崩溃。 如果应用程序将文档标识为原因, 它将询问用户是否可以同时随呼叫栈一起发送文档。 用户可以为此问题做出明智的选择。 IT 管理员可能严格要求传输文档, 并让用户代表用户从不发送文档。 可以设置以下首选项以阻止发送文档, 并禁止提示用户:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> 如果将**SendAllTelemetryEnabled**设置为**FALSE**, 则会禁用该进程的所有故障报告。 若要启用故障报告而不发送使用遥测, 可以设置以下首选项:```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>更新
  
Microsoft 按固定时间间隔 (通常每月一次) 发布 Office for Mac 更新。 我们强烈建议用户和 IT 管理员将计算机保持最新, 以确保安装了最新的安全修补程序。 在 IT 管理员希望密切控制和管理计算机更新的情况下, 可以设置以下首选项, 以防止自动更新过程自动检测和提供产品更新:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>使用防火墙/代理阻止请求
  
如果你的组织通过防火墙或代理服务器阻止对 Url 的请求, 请确保将此文档中列出的 Url 配置为 "允许" 或 "阻止" (例如, 403 或 404) "阻止"。 40X 响应将允许 Office 应用程序正常接受无法访问资源的情况, 并提供更快的用户体验, 而不只是删除连接, 这将导致客户端重试。
  
如果代理服务器需要身份验证, 则407响应将返回到客户端。 为获得最佳体验, 请确保您使用的是 Office for Mac 版本15.27 或更高版本, 因为它们包含用于使用 NTLM 和 Kerberos 服务器的特定修补程序。
  
  
## <a name="see-also"></a>另请参阅

[Office 365 URL 和 IP 地址范围](urls-and-ip-address-ranges.md)

