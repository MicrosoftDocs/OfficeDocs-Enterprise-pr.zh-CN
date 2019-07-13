---
title: 从 SharePoint 2010 升级
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 07/11/2019
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 和 SharePoint Server 2010 的支持结束时间在13年10月 13 2020 日结束。 使用本文作为升级到 SharePoint Online 或本地 SharePoint Server 的更新版本的指南。
ms.openlocfilehash: c3860e8229c8633ea605228d7d3553d0f673a7d3
ms.sourcegitcommit: d3f8df9439e9cd15333f01b5cde2001fb4b74113
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2019
ms.locfileid: "35643055"
---
# <a name="upgrading-from-sharepoint-2010"></a>从 SharePoint 2010 升级

Microsoft SharePoint 2010 和 SharePoint Server 2010 将在**年10月 13 2020 日**到达支持的结尾。 本文详细介绍了可帮助您将现有的 SharePoint Server 2010 数据迁移到 Office 365 中的 SharePoint Online 或升级本地 SharePoint Server 2010 环境的资源。
  
## <a name="what-is-end-of-support"></a>什么是支持结束？

当您的 SharePoint Server 2010 和 SharePoint Foundation 2010 软件达到其支持生命周期 (Microsoft 提供新功能、缺陷修补程序、安全修补程序等) 的结束时间时, 这称为软件的 "支持结束时间", 或者有时, 它是 "退休"。 在产品的支持 (或 EOS) 结束时, 什么都不会真正关闭或停止工作;但是, 在软件支持结束时, Microsoft 不再提供:
  
- 可能出现的问题的技术支持;
    
- 针对已发现且可能影响服务器的稳定性和可用性的问题的 Bug 修补程序。
    
- 已发现的漏洞安全修补程序以及可能会使服务器易受安全威胁的安全修补程序。
    
- 时区更新。
    
这意味着将不会为产品提供任何进一步的更新、修补程序或修补程序 (包括安全修补程序/修补程序), 并且 Microsoft 支持会将其支持工作完全转移到更新的最新版本。 在支持 SharePoint Server 2010 方法之后, 您应该利用机会在升级产品和/或迁移重要数据之前, 对不再需要的数据进行修整。
  
> [!NOTE]
> 软件生命周期通常从产品初始发布之日起10年后持续。 您可以搜索[Microsoft 解决方案提供商](https://go.microsoft.com/fwlink/?linkid=841249), 他们可以帮助升级到下一版本的软件, 或使用 Office 365 迁移 (或两者)。 一定要确保您了解关键基础技术的支持日期的结束日期, 尤其是您在使用 SharePoint 时使用的 SQL Server 版本。 
  
## <a name="what-are-my-options"></a>我的选项是什么？

首先, 检查[产品生命周期网站](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010)上的支持结束的日期。 接下来, 请务必通过了解此日期来规划升级或迁移时间。 请注意, 你的产品不会在列出的日期*停止工作*, 并且你可以继续使用它, 但是, 因为在该日期之后安装不再会修补, 所以你将需要一种策略来帮助你更顺利地转换到下一个版本产品的。 
  
此矩阵有助于在迁移产品功能和用户数据时绘制课程:
  
|**支持产品的结束**|**Good**|**最好**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013 (本地)  <br/> |SharePoint Online  <br/> |
||SharePoint Server 2013 与 SharePoint Online 的混合  <br/> |SharePoint Server 2016 (本地)  <br/> |
|||SharePoint 云混合搜索  <br/> |
   
如果您在规模的低端 (好的选项) 上选择选项, 则在从 SharePoint Server 2010 迁移完成后, 你将需要立即开始规划另一次升级。 

若要避免停止 SharePoint Server 2010 支持, 可以采用三种途径。

![SharePoint Server 2010 升级路径](./media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

>[!Note]
>SharePoint Server 2010 和 SharePoint Foundation 2010 的支持结束时间为 Oct 13、2020, 但*请注意*, 应始终检查[产品生命周期网站](https://support.microsoft.com/en-us/lifecycle)的最新日期。
>

  
## <a name="where-should-i-go-next"></a>下一步应转到哪里？

可以在自己的服务器上的本地安装 SharePoint Server 2013 和 SharePoint Foundation 2013。 否则, 您可以使用 SharePoint Online, 这是 Microsoft Office 365 中的一种联机服务。 您可以选择执行以下操作:
  
- 迁移到 SharePoint Online
    
- 本地升级 SharePoint Server 或 SharePoint Foundation
    
- 执行上述两项操作
    
- 实现[SharePoint 混合](https://docs.microsoft.com/sharepoint/hybrid/hybrid)解决方案 
    
了解与维护服务器场以继续、维护或迁移自定义设置以及升级 SharePoint Server 所依赖的硬件相关的隐藏成本。 如果你意识到所有这些都是在内的, 则继续在本地进行升级会更容易。 否则, 如果在不进行大量自定义的旧版 SharePoint 服务器上运行服务器场, 则可以从计划迁移到 SharePoint Online 中获益。 此外, 对于您的本地 SharePoint Server 环境, 也可以选择将一些数据放在 SharePoint Online 中, 以减少保留本地数据的硬件管理量。 将一些数据移动到 SharePoint Online 可能会更经济。
  
> [!NOTE]
> SharePoint 管理员可以[创建 Office 365 订阅](https://go.microsoft.com/fwlink/?linkid=843152), 设置全新的 SharePoint Online 网站, 然后将其完全从 sharepoint Server 2010 中裁出, 将最重要的文档完全放在新的 SharePoint online 网站中。 在这里, 任何剩余的数据可能会从 SharePoint Server 2010 网站排出到本地存档中。 
  
|**SharePoint Online**|**SharePoint Server 本地**|
|:-----|:-----|
|较高的时间成本 (规划/执行/验证)  <br/> |较高的时间成本 (规划/执行/验证)  <br/> |
|降低资金成本 (无需购买硬件)  <br/> |资金成本较高 (硬件购买)  <br/> |
|迁移的一次性成本  <br/> |每次迁移时重复的一次性成本  <br/> |
|低总拥有成本/维护  <br/> |高总拥有成本/维护  <br/> |
   
当迁移到 Office 365 时, 一次性移动将有较重的时间花在计划内 (在组织数据和决定对云执行的操作以及留下的准备工作的过程中) 的一段时间。 但是, 一旦迁移了数据, 升级将从该点自动进行查看, 因为您不再需要管理硬件和软件更新, 并且您的服务器场的启动时间将由 Microsoft 服务级别协议 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) 进行支持。
  
### <a name="migrate-to-sharepoint-online"></a>迁移到 SharePoint Online

请确保 SharePoint Online 通过查看其[服务说明](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description)来提供你所需的所有功能。
  
目前尚无可直接从 SharePoint Server 2010 (或 SharePoint Foundation 2010) 迁移到 SharePoint Online 的方法, 因此大部分工作是手动进行的。 这将使您有机会在移动之前存档和修剪不再需要的数据和网站。 您可以将其他数据存档到存储中。 另请注意, SharePoint Server 2010 和 SharePoint Foundation 2010 都不会在支持结束时停止工作, 因此, 如果客户忘记移动某些数据, 则管理员可能会有一段时间, 在此期间, SharePoint 仍在运行。
  
如果升级到 SharePoint Server 2013 或 SharePoint Server 2016, 并决定将数据放入 SharePoint Online 中, 则移动可能还涉及使用[SharePoint 迁移 API](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (将信息迁移到 OneDrive for business)。 
  
|**SharePoint Online 优势**|**SharePoint Online 的缺点**|
|:-----|:-----|
|Microsoft 提供 SPO 硬件和所有硬件管理。  <br/> |SharePoint Server 本地和 SPO 之间的可用功能可能有所不同。  <br/> |
|你是订阅的全局管理员, 并且可能会向管理员分配 SPO 网站。  <br/> |在本地 SharePoint Server 中, 对服务器场管理员可用的某些操作在 Office 365 中的 SharePoint 管理员角色中不存在 (或不是必需的), 但 SharePoint 管理、网站集管理和网站所有权是本地的你的组织。  <br/> |
|Microsoft 会对底层硬件和软件 (包括 SharePoint Online 运行的 SQL server) 应用修补程序、修补程序和更新。  <br/> |由于对服务中的基础文件系统没有访问权限, 因此某些自定义项受到限制。  <br/> |
|Microsoft 发布[服务级别协议](https://go.microsoft.com/fwlink/?linkid=843153)并快速移动以解决服务级别事件。  <br/> |备份和还原和其他恢复选项通过 SharePoint Online 中的服务自动进行, 如果不使用, 则会覆盖备份。  <br/> |
|Microsoft 在服务中不断执行安全测试和服务器性能调整。  <br/> |对用户界面和其他 SharePoint 功能的更改由服务安装, 并且可能需要开启或关闭。  <br/> |
|Office 365 符合多种行业标准: [office 365 合规性](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |迁移的[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)协助受到限制。  <br/> 大部分升级都是手动进行的, 也可以通过[SharePoint Online 和 OneDrive 迁移内容路线图](https://go.microsoft.com/fwlink/?linkid=843184)中介绍的 SPO 迁移 API 进行。  <br/> |
|Microsoft 支持工程师和数据中心中的员工都不受无限制地对订阅进行管理员访问。  <br/> |如果需要升级硬件基础结构以支持较新版本的 SharePoint, 或者如果升级需要辅助服务器场, 则可能会有额外的成本。  <br/> |
|解决方案提供商可协助将您的数据迁移到 SharePoint Online 的一次性作业。  <br/> |并非对 SharePoint Online 所做的所有更改都在您的控制范围内。 迁移之后, 菜单、库和其他功能中的设计差异可能会暂时影响可用性。  <br/> |
|在线产品通过服务自动更新意味着, 尽管功能可能弃用, 但没有真正的支持生命周期的结束。  <br/> |SharePoint Server (或 SharePoint Foundation) 和基础 SQL server 的支持生命周期已结束。  <br/> |
   
如果您已决定创建新的 Office 365 网站, 并将在需要时手动将数据迁移到它, 则可以查看[Office 365 计划选项](https://go.microsoft.com/fwlink/?linkid=843151)。
  

  
### <a name="upgrade-sharepoint-server-on-premises"></a>升级本地 SharePoint Server

从最新版本的 SharePoint 本地产品 (SharePoint Server 2016) 开始, SharePoint Server 升级必须以*串行*方式进行, 这意味着无法直接从 sharepoint server 2010 升级到 sharepoint server 2016。 
  
|||
|:-----|:-----|
||串行升级路径 * * * *: SharePoint Server 2010 **\>** sharepoint server 2013 **\>** sharepoint server 2016 |
   
如果选择跟踪从 SharePoint 2010 到 SharePoint Server 2016 的整个路径, 将需要花费时间和进行规划。 升级涉及升级的硬件方面的成本 (请注意, 还必须升级 SQL server)、软件和管理。 此外, 可能还需要升级自定义项, 甚至放弃自定义项。 在升级 SharePoint Server 服务器场之前, 请务必先收集所有关键自定义项的注释。
  
> [!NOTE]
> 可以保持您的 2010 SharePoint Server 2016 的最终安装服务器场, 在新硬件上安装 SharePoint Server 场 (因此单独的服务器场并行运行), 然后计划并执行手动的内容迁移 (用于下载和重新上载内容)。示例)。 这些手动移动 (例如, 来自2010的文档拥有具有执行手动移动的帐户别名的当前最后修改的帐户) 以及某些工作必须提前完成 (重新创建网站、子网站、权限和列表结构)。 最好是考虑哪些数据可以移动到存储, 或者不再需要。 这样可以降低迁移的影响。 无论哪种方式, 都要在升级之前清理环境。 请确保你的现有服务器场在升级之前运行正常, 并在停止之前 (确保) 运行! 
  
请记住查看**支持的和不受支持的升级路径**: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您具有**自定义项**, 则在迁移路径中为每个步骤规划升级都很重要: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**内部部署优势**|**本地缺点**|
|:-----|:-----|
|从服务器硬件上完全控制 SharePoint 场的所有方面 (以及 SQL)。  <br/> |所有中断和修复都是贵公司的责任 (但如果你的产品不支持, 你可以联系付费 Microsoft 支持):  <br/> |
|SharePoint Server 本地的完整功能集以及通过混合将本地服务器场连接到 SharePoint Online 订阅的选项。  <br/> |SharePoint Server 的升级、修补程序、安全修补程序、硬件升级和所有维护都将在本地管理其 SQL 服务器场。  <br/> |
|对比 SharePoint Online 更高的自定义选项的完全访问权限。  <br/> |[Office 365 支持的合规性标准](https://go.microsoft.com/fwlink/?linkid=843165)必须在本地手动配置。  <br/> |
|在您的内部部署 (在您的控制之下) 执行安全测试和服务器性能调整。  <br/> |Office 365 可能会对 SharePoint Online 可用的功能, 这些功能无法与本地 SharePoint Server 进行互操作  <br/> |
|解决方案提供商可以帮助将数据迁移到 SharePoint Server 的下一个版本 (及更高版本)。  <br/> |您的 SharePoint Server 网站不会自动使用在 SharePoint Online 中显示的[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)证书。  <br/> |
|在本地 SharePoint Server 中完全控制命名约定、备份和还原以及其他恢复选项。  <br/> |本地 SharePoint Server 对产品生命周期非常敏感。  <br/> |
   
### <a name="upgrade-resources"></a>升级资源

首先比较硬件和软件要求。 如果您不符合对当前硬件的升级的基本要求, 这可能意味着您需要先升级服务器场或 SQL server 中的硬件, 或者您可能决定将一些站点的一部分移动到 SharePoint Online 的 "长绿" 硬件。 完成评估后, 请遵循受支持的升级途径和方法。
  
- **的硬件/软件要求**: 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | sharepoint server[2013](https://go.microsoft.com/fwlink/?linkid=843206) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **的软件边界和限制**: 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | sharepoint server[2013](https://go.microsoft.com/fwlink/?linkid=843248) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- 以下项**的升级过程概述**: 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | sharepoint server[2013](https://go.microsoft.com/fwlink/?linkid=843252) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>在 SharePoint Online 和本地 SharePoint Server 之间创建 SharePoint 混合解决方案

另一个选项 (可能是用于某些迁移需求的本地和在线领域的最佳选择) 是一种混合部署, 您可以将 SharePoint Server 2013 或2016场连接到 SharePoint Online 以创建 SharePoint 混合:[了解 sharepoint 混合解决方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
如果你决定将 SharePoint Server 场混合为你的迁移目标, 请务必规划应将哪些网站和用户移动到联机, 以及需要在本地部署。 对 SharePoint Server 服务器场内容的审阅和排名 (确定对公司的高、中或低影响的数据) 可能有助于做出此决定。 您可能只需要与 SharePoint Online 共享 (a) 用户帐户进行登录, 并且 (b) SharePoint Server 搜索索引--这可能不会很清楚, 除非您了解如何使用您的网站。 如果您的公司后来决定将所有内容迁移到 SharePoint Online, 您可以将所有剩余的帐户和数据联机移动, 并使您的本地服务器场退役, 并且 SharePoint 服务器场的管理/管理将通过 Office 365 完成。来自该点的控制台。
  
请务必熟悉混合的现有类型, 以及如何配置您的本地 SharePoint 场和 Office 365 订阅之间的连接。
  
通过创建[Office 365 开发/测试环境](https://go.microsoft.com/fwlink/?linkid=843152), 了解混合 SharePoint 服务器场的工作方式的一个不错的方法。 拥有试用版或购买的 Office 365 订阅后, 您将能够在 SharePoint Online 中创建网站集、web 和文档库, 您可以在其中迁移数据 (通过使用迁移 API 手动进行), 或者-如果您想要迁移我的通过混合向导将网站内容传递到 OneDrive for business。
  
> [!NOTE]
> 请注意, 您的 SharePoint Server 2010 服务器场首先需要升级到 SharePoint Server 2013 或 SharePoint Server 2016, 才能使用 "混合" 选项。 SharePoint Foundation 2010 和 SharePoint Foundation 2013 无法创建与 SharePoint Online 的混合连接。 
  
## <a name="related-topics"></a>相关主题

[可帮助您从 Office 2007 或2010服务器和客户端进行升级的资源](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[从 SharePoint 2010 升级到 SharePoint 2013 的最佳做法](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[在 SharePoint 2013 中解决数据库升级问题](https://go.microsoft.com/fwlink/?linkid=843195)
  
[搜索 Microsoft 解决方案提供商以帮助你进行升级](https://go.microsoft.com/fwlink/?linkid=841249)
  
[SharePoint 2013 的更新产品服务策略](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[SharePoint Server 2016 的更新产品服务策略](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

