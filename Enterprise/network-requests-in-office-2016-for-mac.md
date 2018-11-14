---
title: Office mac 版中的网络请求
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Office for Mac 应用程序提供的本机应用程序体验 macOS 平台上。每个应用程序设计以在各种方案，包括状态，无法访问网络时可用。计算机连接到网络后，应用程序将自动连接到一系列的基于 web 的服务，以提供增强的功能。本白皮书介绍了哪些终结点 Url 尝试通，应用程序和提供的服务。疑难解答网络配置问题和网络代理服务器的设置策略时，此信息很有用。本文中的详细信息都适用于 Office 365 URL 和地址范围文章的补充。
ms.openlocfilehash: 929b93433f5d990952b540a1b28fe2ac74edfb5d
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219892"
---
# <a name="network-requests-in-office-for-mac"></a>Office mac 版中的网络请求

Office for Mac 应用程序提供的本机应用程序体验 macOS 平台上。每个应用程序设计以在各种方案，包括状态，无法访问网络时可用。计算机连接到网络后，应用程序将自动连接到一系列的基于 web 的服务，以提供增强的功能。以下信息介绍了哪些终结点 Url 尝试通，应用程序和提供的服务。网络配置问题和网络代理服务器的设置策略疑难解答时，此信息很有用。本文中的详细信息都适用于[Office 365 URL 和地址范围文章](urls-and-ip-address-ranges.md)，其中包括运行 Microsoft Windows 的计算机的终结点专用于补充。除非另行说明，这篇文章中的信息也适用于 Mac 的 Office 2019 和 Office for Mac、 的 2016年可作为一次性购买从零售店或批量许可协议。 

  
本文的大部分是表详述网络 Url、 类型和服务或由该终结点提供的功能的说明。每个 Office 应用程序可能会有所不同在其服务和终结点的使用率。下表中定义了以下应用程序：
  
- W: Word
- P: PowerPoint
- X: Excel
- O: outlook
- N: OneNote
   
URL 类型定义，如下所示：
  
- ST： 静态-的 URL 是硬编码到客户端应用程序。
    
- SS： 分号静态-URL 编码作为网页或重定向的一部分。
    
- CS： 配置服务的 URL 作为返回 Office 配置服务的一部分。

    
## <a name="office-for-mac-default-configuration"></a>Office for Mac 默认配置

 **安装和更新**
  
下列网络终结点用于下载 Microsoft 内容交付网络 (CDN) 中的 Office for Mac 安装程序。
  
|**URL**|**类型**|**说明**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Office 365 门户安装的正向链接到最新的安装包的服务。  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |内容交付网络上的安装包的位置。  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |内容交付网络上的安装包的位置。  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |管理 Microsoft AutoUpdate 控件终结点  <br/> |
   
 **第一个应用程序启动**
  
下列网络终结点取得联系的 Office 应用程序的首次启动。这些终结点增强的 Office 功能，为用户提供和 Url 取得联系无论许可证类型 （包括批量许可安装）。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |Flighting' 配置-允许功能向上轻量和试验。  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Flighting 网络配置测试  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Flighting 网络配置测试  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 配置服务的母版页的服务终结点列表。  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 规则遥测下载-有关哪些数据和要将上载到遥测服务事件通知客户端。  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote 遥测服务  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 遥测上载报告-"Heartbeart"和客户端出现的错误事件上载到遥测服务。  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office Online 模板 Service-为用户提供了在线文档模板。  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office 模板下载-png 文件模板的存储。  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office 应用程序的存储配置。  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office 文档集成服务目录 （的服务和终结点列表） 和主页领域发现。  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |资源的主页领域发现 v2 （15.40 及更高版本）  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 自动更新清单-检查，以查看是否有可用更新  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft Ajax JavaScript 库  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |维基百科应用程序的 Office 配置和资源。  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |必应 Bing 地图应用程序的 Office 配置和资源。  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |人员 Office 配置和资源的图形应用的程序。  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |什么是新的 OneNote 的内容。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |有关 onenote 2003 的新内容。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |什么是新的 OneNote 图像。  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |在应用程序支持服务。  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |电子邮件帐户检测服务。  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook 自动发现  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook 的 Office 365 服务的终结点。  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Outlook 加载项的图标。  <br/> |
   
> [!NOTE]
> Office 配置服务用作自动发现服务的所有 Microsoft Office 客户端，而不仅仅是 for mac。非常少，但仍有可能已更改，则响应中返回的终结点是半静态的。 
  
 **登录**
  
登录到基于云的存储区时，下列网络终结点取得联系。根据您的帐户类型，可以通过不同的服务进行联系。例如：
  
- **MSA: Microsoft 帐户**-通常用于消费者和零售方案 
    
- **OrgID： 组织帐户**-通常用于商业方案 
    
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows 授权服务  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 365 登录服务 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 帐户登录服务 (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft 帐户登录服务帮助程序 (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Office 365 登录品牌 (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |文档和位置存储定位器  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |大多数最近使用的 (MRU) 文档服务  <br/> |
   
> [!NOTE]
> 对于基于订阅和零售许可证，同时登录激活该产品，并启用到云的资源，如 OneDrive 的访问。对于批量许可安装，用户仍提示您登录 （默认），但仅根据已激活产品所需的云资源的访问权限。 
  
 **产品激活**
  
下列网络终结点适用于 Office 365 订阅和零售许可证激活。具体而言，这不应用于批量许可安装。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office 许可服务  <br/> |
   
 **什么是新的内容**
  
下列网络终结点仅适用于 Office 365 订阅。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |什么是新的 JSON 页面内容。  <br/> |
   
 **研究工具**
  
下列网络终结点仅适用于 Office 365 订阅。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |研究 Web 服务  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |研究静态内容  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |研究内容提供程序  <br/> |
   
 **智能查找**
  
下列网络终结点适用于 Office 365 订阅和零售/批量许可激活。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |深入了解 Web 服务  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |JQuery 库  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |支持 JavaScript 库  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |见解内容提供程序  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |见解内容提供程序  <br/> |
   
 **PowerPoint 设计器**
  
下列网络终结点仅适用于 Office 365 订阅。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint 设计器 web 服务  <br/> |
   
 **PowerPoint 快速启动**
  
下列网络终结点仅适用于 Office 365 订阅。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint QuickStarter web 服务  <br/> |
   
 **发送笑脸/看起来愁眉苦脸**
  
下列网络终结点适用于 Office 365 订阅和零售/批量许可激活。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |将笑脸服务发送  <br/> |
   
 **与支持部门联系**
  
下列网络终结点适用于 Office 365 订阅和零售/批量许可激活。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |与支持部门联系服务  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |在应用程序支持服务  <br/> |
   
 **另存为 PDF**
  
下列网络终结点适用于 Office 365 订阅和零售/批量许可激活。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Word 文档转换服务 (PDF)  <br/> |
   
 **Office 应用程序 （也称为加载项）**
  
Office 应用程序加载项是受信任时，下列网络终结点适用于 Office 365 订阅和零售/批量许可激活。
  
|**URL**|**应用**|**类型**|**说明**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Office 应用程序存储区配置  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |维基百科应用程序资源  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |必应 Bing 地图应用程序资源  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |人力资源 Graph 应用程序  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office 重定向服务  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office 的 JavaScript 库  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |遥测和 Office 应用程序的报告服务  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Microsoft Ajax JavaScript 库  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft Ajax JavaScript 库  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office 的 JavaScript 库  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |支持资源  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |支持资源  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |支持资源  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |JavaScript 库  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |错误报告  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |字体资源  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |遥测服务  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |遥测报告  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Microsoft 存储资产库  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |维基百科页面资源  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia 媒体资源  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia 沙盒框架  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |映射模板  <br/> |
   
 **安全链接**
  
应用于所有 Office 应用程序的 Office 365 订阅仅网络终结点。
  
|**URL**|**类型**|**说明**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Microsoft 安全链接服务  <br/> |
   
 **崩溃报告**
  
网络终结点适用于 Office 365 订阅和零售/批量许可激活所有 Office 应用程序。如果进程意外崩溃，为生成报表并将其发送到 Watson 服务。
  
|**URL**|**类型**|**说明**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Microsoft 错误报告服务  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office 协作见解服务  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>减少网络请求和通信选项

Office for Mac 的默认配置提供最佳用户体验，包括功能和保持最新的计算机。在某些情况下，您可能希望阻止联系网络终结点的应用程序。本节讨论了这样的选项。
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>禁用云登录和 Office 加载项
  
批量许可客户可能必须将文档保存到基于云的存储有关严格的策略。可以设置以下每个应用程序首选项禁用 MSA/OrgID 登录，以及访问 Office 加载项。
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

如果用户尝试访问登录助手函数，他们将看到的网络连接不存在错误。此首选项还会阻止联机产品激活，因为它只应批量许可安装。具体而言，使用此首选项将防止访问下列终结点的 Office 应用程序：
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- 在登录上一节中列出的所有终结点。
    
- 在上面的智能查找一节中列出的所有终结点。
    
- 在上面的产品激活一节中列出的所有终结点。
    
- 在上面的 Office 应用程序 （也称为加载项） 一节中列出的所有终结点。
    
若要重新建立用户的完整功能，或者设置为"2"的首选项或将其删除。
  
> [!NOTE]
> 此首选项需要 Office for Mac 生成 15.25 [160726] 或更高版本。 
  
### <a name="telemetry"></a>遥测
  
Office mac 版的时间间隔定期将遥测信息发送回 Microsoft。数据上载到结点终结点。遥测数据可帮助评估运行状况和每个 Office 应用程序的任何意外的行为工程团队。有两种类别的遥测：
  
- **检测信号**包含版本和许可信息。在应用程序启动时立即发送此数据。 
    
- **使用率**包含有关如何使用应用程序的信息和非致命错误。此数据发送每隔 60 分钟。 
    
Microsoft 非常重视您的隐私非常。您可以阅读有关 Microsoft 的数据集策略，在[https://privacy.microsoft.com](https://privacy.microsoft.com)。若要阻止发送使用率遥测应用程序，可以调整**SendAllTelemetryEnabled**首选项。首选项是每个应用程序，并可以通过 macOS 配置配置文件，或通过终端手动设置： 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

检测信号遥测始终发送，并且不能禁用。
  
### <a name="crash-reporting"></a>崩溃报告
  
致命的应用程序错误发生时，应用程序将意外终止，并将崩溃报表上载到 Watson 服务。故障报告包含调用堆栈，即步骤导致崩溃处理应用程序的列表。这些步骤帮助工程团队确定失败的具体函数及使用原因。
  
在某些情况下，文档的内容将导致应用程序崩溃。如果应用程序标识原因了文档，它将询问用户是否可接受以同时发送调用堆栈以及文档。用户可以进行明智的选择此问题。IT 管理员可能具有严格要求有关文档的传输和代表用户决定从不发送文档。可以设置以下首选项，以防止文档发送，并取消向用户提示：
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> 如果**SendAllTelemetryEnabled**设置为**FALSE**，所有崩溃报告过程被禁用。若要启用崩溃报告而不发送使用率遥测，可以设置以下首选项：```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>更新
  
Microsoft 发布 Office for Mac 更新定期 （通常每月一次）。我们强烈建议用户和 IT 管理员保留机最新，以确保最新的安全修补程序安装。在 IT 管理员希望紧密控制和管理计算机更新的情况下，可以设置以下首选项，以防止自动检测并提供产品更新 AutoUpdate 流程：
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>阻止与防火墙/代理的请求
  
如果您的组织块通过防火墙或代理服务器请求 url 确保配置为允许，本文档中列出的 Url 或阻止带有 40 X 响应 （例如 403 或 404）。40 X 响应将允许正常接受无法访问该资源，Office 应用程序，并将提供更快的用户体验，比放连接，这将导致反过来客户端重试。
  
如果您的代理服务器要求身份验证，407 响应将返回到客户端。获得最佳体验，确保您正在使用的 Office for Mac 生成 15.27 或更高版本，其中包括有关使用 NTLM 和 Kerberos 服务器特定修补程序。
  
  
## <a name="see-also"></a>另请参阅

[Office 365 URL 和 IP 地址范围](urls-and-ip-address-ranges.md)

