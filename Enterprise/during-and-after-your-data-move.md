---
title: 数据移动期间和数据移动之后
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
f1.keywords:
- NOCSH
description: 数据移动是指 Microsoft 将租户的服务和关联数据移到新的数据中心地理位置时发生的后端操作。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6dbfbd9f33aba84086b257ce5a93f01bb707a54c
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606408"
---
# <a name="during-and-after-your-data-move"></a>数据移动期间和数据移动之后

数据移动是一种后端操作，对最终用户影响最小。 在 Microsoft 将租户的每项服务和关联数据移动到新的数据中心地理位置时，无需执行任何操作。 数据传输和验证在后台进行，并对用户影响最小。
  
> [!NOTE]
> 每个服务的移动发生在不同的时间。 因此，你将在不同时间看到每个服务的已描述缩减功能。 
  
观看 Microsoft 365 消息中心，以在每个 Exchange Online、SharePoint Online、团队和 Skype for Business 移动完毕时进行确认。 如下表所示，在注册期结束后，可能需要长达24个月，以完成针对特定地理位置的所有客户的所有请求的数据移动。 如果你在移动后发现你的租户存在任何问题，请联系[支持人员](https://go.microsoft.com/fwlink/p/?LinkID=522459)以获取帮助。 
  

|**在中注册国家/地区的客户**|**所有移动完成者**|
|:-----|:-----|
|澳大利亚、新西兰、斐济  <br/> |2022年7月1日  <br/> |
|日本  <br/> |2022年7月1日  <br/> |
|印度  <br/> |2022年7月1日  <br/> |
|加拿大  <br/> |2022年7月1日  <br/> |
|韩国  <br/> |2022年7月1日  <br/> |
|英国  <br/> |2022年7月1日  <br/> |
|法国  <br/> |2022年7月1日  <br/> |
|阿拉伯联合酋长国  <br/> |2022年7月1日  <br/> |
|南非  <br/> |2022年7月1日  <br/> |
|瑞士，列支敦士登  <br/> |2022年7月1日  <br/> |
|德国  <br/> |相同  <br/> |
|挪威  <br/> |2022年11月1日  <br/> |

## <a name="exchange-online"></a>Exchange Online

由于需要花费时间将每个用户移动到单个租户的新数据中心地理位置，因此在移动期间，某些用户将仍处于旧的数据中心地理位置，而其他用户则位于新的数据中心地理位置。 这意味着，涉及访问多个邮箱的某些功能在移动过程中可能不会完全工作，这可能是持续几周的一段时间。 以下各节介绍了这些功能。
  
### <a name="open-shared-folder-in-outlook-web-access"></a>在 Outlook Web Access 中打开 "共享文件夹"

某些用户从其他邮箱打开共享邮件文件夹， (用户具有使用 "共享文件夹" 功能在 Outlook Web Access 中) 的读取或写入权限。 下表介绍了在邮箱移动过程中共享文件夹的访问工作方式。 请注意，对共享邮箱拥有完全权限的用户可以在移动过程中使用 Outlook Web Access 打开邮箱。 
  
|**配置**|**说明**|
|:-----|:-----|
|用户拥有对另一个邮箱的邮箱文件夹权限  <br/> |可能受到限制。  <br/> 如果在租户移动过程中，用户 A 和邮箱 B 不在同一地理位置，如果用户 A 对邮箱 B 中的特定文件夹有权限，则用户 A 无法在 Outlook Web Access 中打开邮箱 B 的文件夹。  <br/> 若要添加共享文件夹，请右键单击左侧导航面板中的用户名，然后选择 "**添加共享文件夹**"。  <br/> |
|具有对另一个邮箱的 "完全邮箱" 权限的用户  <br/> |完全支持。  <br/> 如果用户 A 对邮箱 B 具有 "完全访问权限" 权限，则用户 A 可以在 Outlook Web Access 的左侧导航窗格中单击共享文件夹以打开显示邮箱 B 的窗口。 在移动过程中，用户可以使用 Outlook Web Access 打开共享邮箱，而不会产生任何负面影响。 限制仅适用于邮箱中的文件夹级共享。           |
  
## <a name="sharepoint-online"></a>SharePoint Online

移动 SharePoint Online 时，还会移动以下服务的数据：
  
- OneDrive for Business
    
- Project Online
    
- Microsoft 365 的项目
    
- Microsoft 365 视频服务
    
- 浏览器中的 Office
    
- Microsoft 365 企业应用版
    
- Visio Pro for Microsoft 365
    
完成移动 SharePoint Online 数据后，您可能会看到以下某些效果。
  
### <a name="microsoft-365-video-services"></a>Microsoft 365 视频服务

- 视频的数据移动比在 SharePoint Online 中移动其他内容的时间长。
    
- 移动 SharePoint Online 内容之后，将会有一个时间段，无法播放视频。
    
- 我们要从以前的数据中心删除交易编码副本，并在新数据中心中再次转换它们。
    
### <a name="search"></a>搜索

在移动 SharePoint Online 数据的过程中，我们会将搜索索引和搜索设置迁移到新位置。 在我们**完成**对 SharePoint Online 数据的移动之前，我们将继续为你的用户提供原始位置的索引。 在新位置，在完成移动 SharePoint Online 数据后，搜索将自动开始对你的内容进行爬网。 从现在开始，我们通过迁移的索引为你的用户提供服务。 在进行爬网之前，迁移后对你的内容所做的更改不会包含在迁移的索引中。 大多数客户都不会注意到，在我们完成移动其 SharePoint Online 数据后，结果就会变得不太新鲜，但有些客户可能会在前24-48 小时内体验到缩减新鲜度 
  
以下搜索功能将受到影响：
  
- 搜索结果和搜索 Web 部件：结果中不包含迁移之后发生的更改，直到爬网进行挑选。 
    
- Delve： Delve 不包含迁移之后发生的更改，直到爬网对其进行挑选。
    
- 网站的热门程度和搜索报告：新位置中 Excel 报告的计数仅包括在完成移动 SharePoint Online 数据后运行的使用率报告中的已迁移计数和计数。 来自临时时段的任何计数都将丢失，且无法恢复。 此期间通常为几天。 有些客户可能会遇到较短或更长的损失。
    
- 视频门户：查看视频门户的计数和统计信息取决于 Excel 报告的统计信息，因此，在与 Excel 报告相同的时间段内，视频门户的查看次数和统计信息将会丢失。
    
- 电子数据展示：在爬网选取更改之前，不会显示在迁移过程中更改的项目。
    
- 数据丢失保护 (DLP) ：不会对更改的项目强制执行策略，直到爬网选取更改。

## <a name="microsoft-teams"></a>Microsoft Teams

除了 Exchange Online、SharePoint Online 和 OneDrive for Business，Microsoft 还会将团队数据迁移到本地数据中心。

- 工作组聊天邮件，包括私人邮件和频道消息。
- 在聊天中使用的团队图像。

团队文件存储在 SharePoint Online 中，团队聊天文件存储在 OneDrive for Business 中。 语音邮件、日历、聊天历史记录和联系人存储在 Exchange Online 中。 在许多情况下，Exchange Online、SharePoint Online 和 OneDrive for business 已由本地数据中心地理位置的客户使用，并且也是适用于符合条件的客户国家/地区的 Microsoft 365 迁移计划的一部分。

## <a name="skype-for-business"></a>Skype for Business

Skype for Business 移动可用于澳大利亚、日本、印度、加拿大、英国和韩国。

在剪切转移过程中，所有用户都将从 Skype for Business 客户端软件注销。 自动登录将在两分钟内重新连接用户。
  
|**在整个移动过程中工作的功能**|**移动过程中可能会受到限制的功能**|
|:-----|:-----|
| 即时消息和语音呼叫  <br/>  用户可以添加联系人、添加联系人组、添加会议、设置其位置并更改 "今天发生的情况"。  <br/>  音频会议提供商 (ACP) 设置将被复制到目标数据中心地理位置。 如果目标数据中心中存在 ACP 提供程序，则它将正常工作。 否则，它将不会。  <br/> | 租户管理员 TRPS (租户远程 PowerShell) 将不可供管理员创建会话。  <br/>  租户管理员 LAC 将不可供管理员登录并更改用户设置。  <br/> |
   
|**移动后**|
|:-----|
| 会议数据 (上传的演示文稿等，) 不会移动，需要重新上载。  <br/>  较旧的 Lync 客户端（如 Lync 2010 客户端和 Lync for Mac 2011 客户端）被识别为导致登录问题的服务缓存 DNS 信息。 如果用户不在最新的 Skype for Business Windows 客户端上，则可能需要清除 DNS 缓存。 请参阅[Office 365 中的 Skype For Business ONLINE DNS 配置问题故障排除](https://docs.microsoft.com/skypeforbusiness/troubleshoot/online-configuration/dns-configuration-issue)。 适用于 Mac 客户端用户的 Lync 应按照[这些说明](https://support.microsoft.com/kb/2629861)操作。  <br/> |
   
### <a name="skype-for-business-moves-that-involve-a-third-party-audio-conferencing-provider"></a>涉及第三方音频会议提供商的 Skype for Business 移动
适用于 Skype for business 的第三方音频会议提供商附加服务不适用于驻留在新地理位置的新数据中心中的用户。  使用第三方音频会议提供商服务的现有客户不应请求移动到新的特定地理位置的数据中心。  如果新客户部署到新的特定地理位置数据中心，则需要请求移动到区域数据中心以使用第三方音频会议提供商。
  
## <a name="related-topics"></a>相关主题 
 
[如何请求数据移动](request-your-data-move.md)
    
[数据移动常见问题解答](data-move-faq.md)
  
[适用于 Microsoft Dynamics CRM Online 的新数据中心信息](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[按区域的 Azure 服务](https://azure.microsoft.com/regions/)
