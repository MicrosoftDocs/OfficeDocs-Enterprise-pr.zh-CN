---
title: 数据移动期间和数据移动之后
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 10/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: 数据移动是对最终用户影响最小的后端操作。Microsoft 会到新的数据中心按地理为您的租户中移动的每个服务和关联的数据时，不不需要任何操作。出现在后台提前和最小的影响用户数据传输和验证。
ms.openlocfilehash: 6975a2ea4a1f2b2ebabe5f64b12ae58657180903
ms.sourcegitcommit: b745d570fd6691606d226f6232cfaafd2d875a2d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "25361500"
---
# <a name="during-and-after-your-data-move"></a>数据移动期间和数据移动之后

数据移动是对最终用户影响最小的后端操作。Microsoft 会到新的数据中心按地理为您的租户中移动的每个服务和关联的数据时，不不需要任何操作。出现在后台提前和最小的影响用户数据传输和验证。
  
> [!NOTE]
> 在不同时间对每种服务时出现移动。因此，您将在不同时间看到每个服务所述的缩减的功能。 
  
完成每个 Exchange Online、 SharePoint Online 和 Skype for Business 的移动时，请观看 Office 365 邮件中心以确认。下表中所示，可以最多 24 个月，注册期结束后，完成所有请求的数据移动的特定地理位置中的所有客户。如果您在移动后与您的租户看到的任何问题，请联系[Office 365 支持](https://go.microsoft.com/fwlink/p/?LinkID=522459)以获得帮助。 
  

|**客户与帐单中的地址**|**通过完成的所有移动**|
|:-----|:-----|
|澳大利亚，新西兰，斐济  <br/> |2017 年 10 月 31 日  <br/> |
|日本  <br/> |2018 年 10 月 31 日  <br/> |
|印度  <br/> |2018 年 10 月 31 日  <br/> |
|加拿大  <br/> |2019 年 6 月 30日，  <br/> |
|韩国  <br/> |2018 年 10 月 31 日  <br/> |
|英国  <br/> |2019 年 9 月 15日，  <br/> |
|法国  <br/> |于 2020 2020年 9 月 15日日  <br/> |
   
## <a name="moves-that-involve-a-third-party-audio-conferencing-provider"></a>涉及第三方音频会议提供商的移动

- 用户驻留在新的地理位置特有的数据中心的 Skype for Business 的第三方音频会议提供商加载项服务不可用。 
    
- 使用第三方音频会议提供商服务的现有客户不应请求移动到新的地理位置特有的数据中心。 
    
- 部署到新的地理位置特有的数据中心的新客户需要请求移动到区域数据中心，以使用第三方音频会议提供商。 
    
## <a name="exchange-online"></a>Exchange Online

因为对于单租户将每个用户移动到新的数据中心按地理时间，某些用户仍然会在旧数据中心按地理期间移动，而其他中新数据中心按地理。这意味着涉及访问多个邮箱的某些功能不会完全处理在移动过程中，一段内后者可以最后一个星期。以下各节将介绍这些功能。
  
### <a name="mailbox-move"></a>邮箱移动

当单个邮箱移动 crosses 数据中心 geo 邮箱内容是首先预暂存以便现有数据而不影响邮箱复制到目标地理位置。切换到目标地理位置时，在几分钟内已锁定源地理位置中的邮箱。在此期间，电子邮件客户端无法暂时连接。任何其他更改复制到目标地理位置，然后邮箱完成移动到目标地理位置。没有在移动过程中的邮件流中断。
  
某些用户可能需要重新启动 Outlook 桌面[知识库文章 2591913](https://support.microsoft.com/kb/2591913)中所述移动邮箱后。
  
### <a name="shared-mailbox"></a>共享邮箱

具有对共享邮箱的"完全控制"权限的用户移动过程中不受影响。
  
### <a name="resource-mailbox"></a>资源邮箱

需要管理资源邮箱配置，通过在 Outlook Web Access 选项页的用户可以继续这样移动过程中。
  
如果直接通过 Exchange cmdlet 管理资源邮箱，如果执行用户和资源邮箱都在不同 geo 不工作的 Set-mailboxregionalconfiguration cmdlet 和 Set-mailboxcalendarconfiguration。
  
### <a name="calendar-delegation"></a>日历委派

忙/闲和日历共享租户移动过程中不会受到影响。对日历文件夹的邮箱 B 的写权限的用户仍可以管理邮箱 B 使用 Outlook 桌面日历文件夹。但是，移动，过程中用户 A 和 B 邮箱不在相同的地理位置，如果用户 A 不能编辑 Outlook Web Access 中的邮箱 B 的日历同时将移动到目标地理位置为止。
  
### <a name="open-shared-folder-in-outlook-web-access"></a>在 Outlook Web Access 中打开"共享文件夹"

一些用户从 Outlook Web Access 使用"共享文件夹"功能 （即用户具有读取或写入的权限） 另一个邮箱中打开的共享的邮件文件夹。下表介绍如何移动到共享的文件夹 works 期间邮箱的访问。请注意具有对共享邮箱的完全权限的用户可以通过移动过程中使用 Outlook Web Access 中打开邮箱。 
  
|**配置**|**说明**|
|:-----|:-----|
|用户具有到另一个邮箱的邮箱文件夹权限  <br/> |可能有限。  <br/> 如果用户 A 和 B 邮箱不租户移动过程中相同的地理位置中，用户 A 如果无法打开邮箱 B 的文件夹中 Outlook Web Access 用户 A 将只具有到邮箱 B.中特定文件夹的权限  <br/> 若要添加的共享的文件夹，右键单击左侧的导航面板中的用户名，然后选择**添加共享的文件夹**。  <br/> |
|具有到另一个邮箱的邮箱完全控制权限的用户  <br/> |完全支持。  <br/> 如果用户 A 具有对邮箱 B"完全访问"权限，通过，用户 A 可以单击在 Outlook Web Access 中，打开一个显示邮箱 B.窗口的左侧的导航面板中的共享的文件夹  <br/> > [!NOTE]> 用户可以打开共享的邮箱没有任何负面影响移动过程中使用 Outlook Web Access。限制仅适用于文件夹级共享邮箱中。           |
   
### <a name="public-folders"></a>公用文件夹

如果公用文件夹邮箱暂时位于不同的数据中心按地理从用户尝试访问它，用户不能访问它。 
  
### <a name="online-archives"></a>联机存档

在移动过程中，通过 Outlook Web Access 连接的用户不能连接到其联机存档邮箱。支持与 Outlook 连接的用户对存档邮箱的访问。
  
### <a name="ediscovery-amp-auditing"></a>电子数据展示&amp;审核

电子数据展示和审核 Office 365 安全性功能&amp;合规性中心支持跨地理租户移动。与 Exchange 管理员中心 (EAC) 中，不支持不同查询并没有尚未移动到一旦租户移动用户已开始。有关安全性的详细信息&amp;合规性中心，请参阅[Office 365 安全性&amp;合规性中心](https://go.microsoft.com/fwlink/p/?linkid=841313)。 
  
下表显示如何访问电子数据展示和通过 EAC 和安全审核&amp;合规性中心。
  
||**Exchange 管理中心**|**安全&amp;合规性中心**|
|:-----|:-----|:-----|
|电子数据展示  <br/> | 转到https://portal.office.com，然后单击**管理员**图块。 <br/> 单击**管理中心** \> **Exchange**。 <br/> 选择**合规性管理** \> **就地电子数据展示&amp;保留**。 | 转到https://portal.office.com，然后单击管理员图块。 <br/> 单击**管理中心** \> **安全&amp;合规性**。 <br/> 选中**搜索&amp;调查** \> **电子数据展示**。|
|审核  <br/> | 转到https://portal.office.com，然后单击**管理员**图块。 <br/> 单击**管理中心** \> **Exchange**。选择**合规性管理** \> **审核**。 | 转到https://portal.office.com，然后单击管理员图块。 <br/> 单击**管理中心** \> **安全&amp;合规性**。 <br/> 选中**搜索&amp;调查** \> **审核日志搜索**。 |
   
### <a name="mailbox-migration"></a>邮箱迁移

时 geo 之间移动一个租户，迁移批次可能在迁移批次中留在源地理位置中的某些用户报告错误。在这种情况下，删除现有的迁移批次，以删除基础的同步请求。批处理完全清理后，创建批处理再次，其中将开始在目标地理位置中创建同步请求。
  
## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online 移动时，还移动数据的以下服务：
  
- OneDrive for Business
    
- Project Online
    
- Project for Office 365
    
- Office 365 视频服务
    
- Office Online
    
- Office 365 ProPlus
    
- Visio Pro for Office 365
    
我们已完成移动 SharePoint Online 数据后，您可能会看到以下效果的一些。
  
### <a name="office-365-video-services"></a>Office 365 视频服务

- 执行数据移动的视频考虑超过为您在 SharePoint Online 中的内容的其余部分移动。
    
- SharePoint Online 内容移动后时，会出现一个时间范围不能播放视频。
    
- 我们要删除译码从以前的数据中心和转码将它们复制再次新数据中心中。
    
### <a name="search"></a>搜索

在过程中将您的 SharePoint Online 数据移动，我们将迁移您的搜索索引和搜索设置到新位置。我们已**完成**的 SharePoint Online 数据移动，直到我们继续提供您的用户从原始位置中的索引。在新位置，搜索将自动启动我们已完成移动 SharePoint Online 数据后，您的内容进行爬网。从这点，并开始向上我们提供您的用户从迁移的索引。爬网选取这些之前，向内容迁移后发生的更改不包括在迁移的索引。大多数客户不发现结果了较少全新右后我们已经完成移动其 SharePoint Online 数据，但在第一个 24 48 小时内，有些客户可能会遇到降低的新鲜度 
  
下面的搜索功能会受到影响：
  
- 搜索结果和搜索 Web 部件： 结果不包括直到爬网提取这些迁移后发生的更改。 
    
- 深入： 深入不包括直到爬网提取这些迁移后发生的更改。
    
- 热门程度和搜索报告网站： 计数的新位置中的 Excel 报表仅包括迁移的计数和从我们完成移动 SharePoint Online 数据后运行的使用率报告的计数。从临时的时间段的任何计数都将丢失，无法恢复。此时间通常是几天。有些客户可能会遇到短或更长时间损失。
    
- 视频门户： 视图计数和视频门户的统计信息取决于 Excel 报告，以便查看计算的统计信息和视频门户的统计信息会丢失与 Excel 报表的同一时间段。
    
- 电子数据展示： 爬网拾取所做的更改之前不显示在迁移期间发生更改的项目。
    
- 数据丢失保护 (DLP): 策略不强制执行对之前所做的更改的爬网拾取更改的项目。
    
## <a name="skype-for-business"></a>Skype for Business

所有用户将都注销从业务客户端软件 Skype 期间切换。自动登录将重新连接用户在两分钟内。
  
|**在整个移动期间工作的功能**|**过程移动的一部分中可能会受到限制的功能**|
|:-----|:-----|
| 即时消息和语音呼叫  <br/>  用户可以添加联系人、 添加联系人组、 添加会议，设置其位置，并更改"今天的最新动态"。  <br/>  音频会议提供商 (ACP) 设置复制到目标数据中心按地理。如果存在于目标数据中心中的 ACP 提供程序，它将正常工作。否则，它将不。  <br/> | 租户管理员 TRPS (租户远程 PowerShell) 将不可用供管理员用来创建会话。  <br/>  租户管理员 LAC 将不可用供管理员用来登录并更改用户设置。  <br/> |
   
|**移动后**|
|:-----|
| 会议数据 （上载演示文稿等） 将不会移动，并将需要重新上载。  <br/>  较旧的 Lync 客户端，例如 Lync 2010 客户端和 Lync for Mac 2011 客户端，一些已知到缓存 DNS 导致登录问题的服务信息。如果用户不在业务 Windows 客户端的最新的 Skype 上可能需要清除 DNS 缓存。询问用户运行[疑难解答向导](https://support.microsoft.com/en-us/kb/2541980)，并按照说明如何清除客户端缓存。Lync for Mac 客户端用户应遵循[以下说明](https://support.microsoft.com/en-us/kb/2629861)。<br/> |
   
## <a name="data-for-other-services-including-yammer-and-power-bi"></a>对于其他服务，包括 Yammer 和 Power BI 数据

我们仅用于 Exchange Online、 SharePoint Online 和 for Business 的 Skype 移动客户数据。我们不会移动其他服务的数据。没有更改或向您作为客户或其他服务的用户的影响。移动过程不会影响，并其客户数据的位置保持不变。
  
## <a name="related-topics"></a>相关主题 
 
[如何请求数据移动](request-your-data-move.md)
    
[数据移动常见问题解答](data-move-faq.md)
  
[Microsoft Dynamics CRM online 的新数据中心 geo](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure 服务区域](https://azure.microsoft.com/en-us/regions/)

