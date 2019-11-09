---
title: SharePoint Server 2007 停止提供支持路线图
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: 在2017年10月10日，SharePoint Server 2007 的支持已结束。 阅读本文，了解有关升级选项、故障排除、最佳做法、系统要求、升级步骤以及如何从 Microsoft 合作伙伴获取帮助的信息。
ms.openlocfilehash: 55511852997f9781f9c05d0a846aac7cb1c72309
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078091"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>SharePoint Server 2007 停止提供支持路线图

在**2017 年10月 10**日，Microsoft Office SharePoint Server 2007 已到达支持终止。 如果尚未开始从 SharePoint Server 2007 迁移到 Office 365 或 SharePoint Server 本地版本的新版本，现在是开始规划的时间。 本文详细介绍了帮助用户将数据迁移到 SharePoint Online 或在本地升级 SharePoint Server 的资源。 
  
## <a name="what-does-end-of-support-mean"></a>支持终止的含义是什么？

SharePoint Server （如几乎所有 Microsoft 产品）都具有支持生命周期，在此期间，Microsoft 提供了新的功能、缺陷修补程序、安全修补程序等。 此生命周期通常是从产品初始发布之日起10年的时间，而此生命周期的结束时间也称为产品的支持终止的期限。 在支持结束后，Microsoft 将不再提供：
  
- 可能出现的问题的技术支持;
    
- 针对已发现且可能影响服务器的稳定性和可用性的问题的 Bug 修补程序。
    
- 已发现的漏洞安全修补程序以及可能会使服务器易受安全威胁的安全修补程序。并 
    
- 时区更新。
    
尽管您的 SharePoint Server 2007 服务器场在 2017 10 月10日后仍可正常运行，但不会为产品提供进一步的更新、修补程序或修补程序（包括安全修补程序/修补程序），并且 Microsoft 支持将把其支持工作完全转移到产品的较新版本。 由于你的安装将不再受支持或修补，因为支持方法的结束应升级产品或迁移重要数据。
  
> [!TIP]
> 如果尚未计划升级或迁移，请参阅： [SharePoint 2007 迁移选项](sharepoint-2007-migration-options.md)，以了解开始位置的一些示例。 您还可以搜索可帮助升级或 Office 365 迁移的[Microsoft 合作伙伴](https://go.microsoft.com/fwlink/?linkid=841249)（或两者）。 
  
有关支持结束支持的 Office 2007 服务器的详细信息，请参阅可[帮助您从 Office 2007 服务器和客户端进行升级的资源](upgrade-from-office-2007-servers-and-products.md)。
  
## <a name="what-are-my-options"></a>我的选项是什么？

您的第一位应是[产品生命周期网站](https://go.microsoft.com/fwlink/?linkid=843148)。 如果你的本地 Microsoft 产品是老化的，则应检查其支持日期的结束日期，以便在你的迁移通常需要一年或更长时间后，或在你的迁移过程中安排升级或迁移。 在选择下一步时，它可能会帮助您了解什么是足够好、更好，并且在产品功能方面最适合。 下面是一个示例：
  
|**Good**|**能**|**最好**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint 混合  <br/> |SharePoint Server 2016  <br/> |
|||SharePoint 混合  <br/> |
   
如果你在规模的低端（足够好）选择选项，请记住，从 SharePoint Server 2007 迁移完成后，你将需要立即开始规划升级。 （SharePoint Server 2007 支持的结尾为10月10日，2017。 请注意，这些日期可能会发生更改，并可检查[产品生命周期网站](https://support.microsoft.com/lifecycle)。
  
## <a name="where-can-i-go-next"></a>接下来如何操作？

可以在自己的服务器上将 SharePoint Server 安装在本地，也可以使用 SharePoint Online，这是 Microsoft Office 365 的一部分的联机服务。 您可以选择执行以下操作：
  
- 迁移到 SharePoint Online
    
- 升级本地 SharePoint Server
    
- 执行上述两项操作
    
- 实现[SharePoint 混合](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)解决方案 
    
了解与维护服务器场以继续、维护或迁移自定义设置以及升级 SharePoint Server 所依赖的硬件相关的隐藏成本。 如果是必需的，则为内部部署 SharePoint Server 服务器场进行奖励;否则，如果在旧版 SharePoint 服务器上运行服务器场，而不进行大量自定义，则可以从计划迁移到 SharePoint Online 中受益。
  
> [!IMPORTANT]
> 如果不经常使用 SharePoint 2007 中的内容，也可以选择另一个选项。 某些 SharePoint 管理员可以选择[创建 Office 365 订阅](https://go.microsoft.com/fwlink/?linkid=843152)，设置全新的 SharePoint Online 网站，然后将其完全从 sharepoint 2007 中裁出，将最重要的文档完全从 sharepoint online 网站中删除。 从这里可以将数据从 SharePoint 2007 网站中排出到存档中。 请考虑用户如何使用 SharePoint 2007 安装数据。 可能有一些创造性的方法可以解决此问题！ 
  
|**SharePoint Online （SPO）**|**SharePoint Server 本地**|
|:-----|:-----|
|较高的时间成本（规划/执行/验证）  <br/> |较高的时间成本（规划/执行/验证）  <br/> |
|降低资金成本（无需购买硬件）  <br/> |资金成本较高（硬件 + devs/管理员）  <br/> |
|迁移的一次性成本  <br/> |每次迁移时重复的一次性成本  <br/> |
|低总拥有成本/维护  <br/> |高总拥有成本/维护  <br/> |
   
当迁移到 Office 365 时，一次性移动将具有较高的成本，而您可以对数据进行组织，并决定要对云执行哪些操作以及留下哪些内容。 但是，升级将从该点自动进行，你将不再需要管理硬件和软件更新，并且你的服务器场的启动时间将由 Microsoft 服务级别协议（[SLA](https://go.microsoft.com/fwlink/?linkid=843153)）进行支持。
  
### <a name="migrate-to-sharepoint-online"></a>迁移到 SharePoint Online

通过查看关联的服务说明，确保 SharePoint Online 具有你所需的所有功能。 以下是指向所有 Office 365 服务说明的链接：
  
[Office 365 服务说明](https://go.microsoft.com/fwlink/?linkid=272060)
  
没有直接从 SharePoint 2007 迁移到 SharePoint Online 的方法;您的迁移到 SharePoint Online 将手动执行。 如果升级到 SharePoint Server 2013 或 SharePoint Server 2016，则移动可能还涉及使用 SharePoint 迁移 API （例如，将信息迁移到 OneDrive for Business）。
  
|**Online Pro**|**联机 Con**|
|:-----|:-----|
|Microsoft 提供 SPO 硬件和所有硬件管理。  <br/> |SharePoint Server 本地和 SPO 之间的可用功能可能有所不同。  <br/> |
|你是订阅的全局管理员，并且可能会向管理员分配 SPO 网站。  <br/> |在 Office 365 的 SharePoint 管理员角色中，在本地 SharePoint Server 中对服务器场管理员可用的某些操作不存在（或不必要）。  <br/> |
|Microsoft 对底层硬件和软件应用修补程序、修补程序和更新。  <br/> |由于对服务中的基础文件系统没有访问权限，因此某些自定义项受到限制。  <br/> |
|Microsoft 发布[服务级别协议](https://go.microsoft.com/fwlink/?linkid=843153)并快速移动以解决服务级别事件。  <br/> |备份和还原和其他恢复选项通过 SharePoint Online 中的服务自动进行，如果不使用，则会覆盖备份。  <br/> |
|Microsoft 在服务中不断执行安全测试和服务器性能调整。  <br/> |对用户界面和其他 SharePoint 功能的更改由服务安装，并且可能需要开启或关闭。  <br/> |
|Office 365 符合多种行业标准： [office 365 合规性](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |迁移的[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)协助受到限制。  <br/> 大部分升级都是手动进行的，也可以通过[SharePoint Online 和 OneDrive 迁移内容路线图](https://go.microsoft.com/fwlink/?linkid=843184)中介绍的 SPO 迁移 API 进行。  <br/> |
|Microsoft 支持工程师和数据中心中的员工都不受无限制地对订阅进行管理员访问。  <br/> |如果需要升级硬件基础结构以支持较新版本的 SharePoint，或者如果升级需要辅助服务器场，则可能会有额外的成本。  <br/> |
|合作伙伴可协助将数据迁移到 SharePoint Online 的一次性作业。  <br/> ||
|在线产品是通过服务自动更新的，这意味着功能可能弃用，但不提供真正的支持结束。  <br/> ||
   
如果您已决定创建新的 Office 365 网站，并将在需要时手动将数据迁移到它，则可以在此处查看 Office 365 选项：
  
[Office 365 计划选项](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>升级本地 SharePoint Server

目前没有办法跳过 SharePoint 升级中的版本，至少是在发布 SharePoint Server 2016 时才会跳过。 这意味着升级以串行方式进行：
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
从 SharePoint 2007 迁移到 SharePoint Server 2016 的完整路径意味着需要大量的时间，并将在升级后的硬件方面产生成本（请注意，还必须升级 SQL server）、软件和管理。 根据功能的关键程度，需要升级或放弃自定义项。
  
> [!NOTE]
> 可以维护您的生命期结束的 SharePoint 2007 服务器场，在新硬件上安装 SharePoint Server 2016 场（因此单独的服务器场并行运行），然后规划和执行内容的手动迁移（用于下载和重新上载内容）示例）。 了解手动移动的一些陷阱（例如，文档移动将上次修改的帐户替换为执行手动移动的帐户的别名）以及必须提前完成的工作（如重新创建网站、子网站、权限和列表）。结构）。 同样，这也是考虑可以移动到存储或不再需要的数据的时间，可降低迁移影响的操作。
  
无论哪种方式，都要在升级之前清理环境。 请确保你的现有服务器场在升级之前运行正常，并在停止之前（确保）运行！ 
  
请记住查看**支持的和不受支持的升级路径**： 
  
- [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您具有**自定义项**，则在迁移路径中为每个步骤规划升级都很重要： 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**本地 Pro**|**本地 Con**|
|:-----|:-----|
|从服务器硬件上完全控制 SharePoint 场的各个方面。  <br/> |所有中断和修复都是贵公司的责任（如果你的产品不在支持的基础上，可以与付费 Microsoft 支持部门联系）：  <br/> |
|SharePoint Server 本地的完整功能集以及通过混合将本地服务器场连接到 SharePoint Online 订阅的选项。  <br/> |在本地托管的 SharePoint Server 的升级、修补程序、安全修补程序和所有维护。  <br/> |
|完全访问权限以进行更好的自定义。  <br/> |[Office 365 支持的合规性标准](https://go.microsoft.com/fwlink/?linkid=843165)必须在本地手动配置。  <br/> |
|在您的内部部署（在您的控制之下）执行安全测试和服务器性能调整。  <br/> |Office 365 可能会对 SharePoint Online 可用的功能，这些功能无法与本地 SharePoint Server 进行互操作  <br/> |
|合作伙伴可协助将数据迁移到 SharePoint Server 的下一个版本（和更高版本）。  <br/> |您的 SharePoint Server 网站不会自动使用在 SharePoint Online 中显示的[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)证书。  <br/> |
|在本地 SharePoint Server 中完全控制命名约定、备份和还原以及其他恢复选项。  <br/> |本地 SharePoint Server 对产品生命周期非常敏感。  <br/> |
   
### <a name="upgrade-resources"></a>升级资源

先知道您是否满足硬件和软件要求，然后再遵循受支持的升级方法。
  
- **的硬件/软件要求**： 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | sharepoint server[2010](https://go.microsoft.com/fwlink/?linkid=843204) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **的软件边界和限制**： 
    
    [Sharepoint server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | sharepoint server[2010](https://go.microsoft.com/fwlink/?linkid=843247) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- 以下项**的升级过程概述**： 
    
    [Sharepoint server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | sharepoint server[2010](https://go.microsoft.com/fwlink/?linkid=843251) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>在 SharePoint Online 和本地部署之间创建 SharePoint 混合解决方案

如果迁移的答案需要在本地提供的自控制之间，以及 SharePoint Online 提供的较低的所有权成本，则可以通过混合将 SharePoint Server 2013 或2016服务器场连接到 SharePoint Online。 [了解 SharePoint 混合解决方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
如果你确定混合 SharePoint 服务器场将对你的业务带来好处，请熟悉现有的混合类型，以及如何配置你的本地 SharePoint 场和 Office 365 订阅之间的连接。
  
查看[Office 365 开发/测试环境](https://go.microsoft.com/fwlink/?linkid=843152)的工作原理是一种很棒的方法。 拥有试用版或购买的 Office 365 订阅后，您将能够在 SharePoint Online 中创建网站集、web 和文档库，您可以在其中迁移数据（通过使用迁移 API 手动进行），或者-如果您想要迁移我的通过混合向导将网站内容传递到 OneDrive for business。
  
> [!NOTE]
> 请注意，您的 SharePoint 2007 服务器场将需要升级到 SharePoint Server 2013 或 SharePoint Server 2016，才能使用 "混合" 选项 
  
## <a name="related-topics"></a>相关主题

[疑难解答和恢复升级（Office SharePoint Server 2007）](https://go.microsoft.com/fwlink/?linkid=843192)
  
[解决升级问题（SharePoint Server 2010）](https://go.microsoft.com/fwlink/?linkid=843194)
  
[在 SharePoint 2013 中解决数据库升级问题](https://go.microsoft.com/fwlink/?linkid=843195)
  
[搜索 Microsoft 合作伙伴以帮助进行升级](https://go.microsoft.com/fwlink/?linkid=841249)
  
[可帮助您从 Office 2007 服务器和客户端进行升级的资源](upgrade-from-office-2007-servers-and-products.md)
  

