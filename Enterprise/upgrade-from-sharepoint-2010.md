---
title: 从 SharePoint 2010 升级
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 和 SharePoint Server 2010 即将结束的支持。使用本文作为指南升级到 SharePoint Online 或 SharePoint Server 内部部署的更新版本。
ms.openlocfilehash: c88c6010aa398d8076fce59976bf6f5c0aa1a743
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169864"
---
# <a name="upgrading-from-sharepoint-2010"></a>从 SharePoint 2010 升级

在 Oct 13 2020年上 Microsoft Office SharePoint Server 2010 达到结束的支持。本文介绍可帮助用户迁移到 SharePoint Online，他们现有的 SharePoint Server 2010 数据或升级 SharePoint Server 本地资源。
  
## <a name="what-is-end-of-support"></a>什么是支持的结束？

SharePoint Server 2010 和 SharePoint Foundation 2010 软件达到其支持生命周期 （在此期间 Microsoft 提供的新功能、 bug 修复、 安全修补程序、 等的时间） 的末尾时这称为软件末端支持，或，有时，其退休。在产品的支持 （或 EOS） 结束时，nothing 实际关闭或停止工作;但是，在软件支持的结束时，Microsoft 不再提供：
  
- 可能出现; 的问题的技术支持
    
- Bug 修复的问题的发现以及可能影响的稳定性和可用性的服务器。
    
- 安全漏洞的发现和可能使该服务器安全轻易; 地受到修补程序
    
- 更新所在的时区。
    
这意味着，将不再更新、 修补程序，或修补程序将传送的产品 （包括安全修补程序修补程序） 和 Microsoft 支持将具有完全改在其支持的努力较新版本。随着临近结束的 SharePoint Server 2010 的支持，您应利用修整不再需要升级该产品、 和/或迁移重要数据之前的数据的机会。
  
> [!NOTE]
> 从产品的初始发行版的日期 10 年通常持续软件生命周期。您可以搜索与升级到下一个版本的软件，或 Office 365 迁移 （或两者） 可帮助的[Microsoft 合作伙伴](https://go.microsoft.com/fwlink/?linkid=841249)。请确保您知道的末尾，关键基础技术支持日期特别是您与 SharePoint 结合使用的 SQL server 的版本。 
  
## <a name="what-are-my-options"></a>我的选项是什么？

首先，检查[产品生命周期网站](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010)上支持结束日期。接下来，请务必规划此日期的知识与您升级或迁移的时间。请记住，您产品*不会停止工作*日期列出，并且您可以继续使用，但是，因为不再将该日期后修补安装，您需要将帮助您更平稳转换到下一个版本的策略产品。 
  
此矩阵有助于绘制课程，当谈到迁移产品功能和用户数据：
  
|**支持产品的末尾**|**较好**|**最好**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint 混合  <br/> |SharePoint Server 2016 （本地）  <br/> |
|||SharePoint 云混合搜索  <br/> |
   
如果您选择的低末尾扩展 （良好选项） 上的选项，您需要开始推出后从 SharePoint Server 2010 的迁移完成规划另一个升级。（结束的支持的 SharePoint Server 2010 和 SharePoint Foundation 2010 计划为 2020，Oct 13，但*请注意*您应始终检查[产品生命周期网站](https://support.microsoft.com/en-us/lifecycle)您最准确日期 ！） 
  
## <a name="where-should-i-go-next"></a>其中应转下？

SharePoint Server 2013 和 SharePoint Foundation 2013 可以安装在本地您自己的服务器上。否则，您可以使用 SharePoint Online，这是 Microsoft Office 365 的一部分的联机服务。您可以选择：
  
- 迁移到 SharePoint Online
    
- 升级 SharePoint 服务器或 SharePoint Foundation 本地
    
- 执行以上两项操作
    
- 实现[SharePoint 混合](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)解决方案 
    
注意隐藏相关的成本与维护服务器场循序，维护或自定义项，迁移和升级 SharePoint 服务器所依赖的硬件。如果您知道并具有所有这些占，它将可以更轻松地继续升级内部部署。否则，如果没有大量自定义的旧 SharePoint 服务器上运行您的服务器场，您可以受益于计划迁移到 SharePoint Online。还有可能的内部部署 SharePoint Server 在咖啡馆，只要可能选择将某些数据放入 SharePoint Online，从而减少硬件管理保留所有其数据的本地涉及的量。它可能更为经济将某些数据移到 SharePoint Online。
  
> [!NOTE]
> SharePoint 管理员可能[创建 Office 365 订阅](https://go.microsoft.com/fwlink/?linkid=843152)，请设置全新的 SharePoint Online 网站，然后完全，剪切离开 SharePoint Server 2010 的全新的 SharePoint Online 站点采用仅的最重要的文档。从，任何剩余的数据可能会耗尽从 SharePoint Server 2010 网站到内部部署存档。 
  
|**SharePoint Online (SPO)**|**SharePoint Server 内部部署**|
|:-----|:-----|
|时间跟踪成本很高 (计划 / 执行 / 验证)  <br/> |时间跟踪成本很高 (计划 / 执行 / 验证)  <br/> |
|资金 （没有硬件购买） 中降低成本  <br/> |资金 （购买的硬件） 中的成本较高  <br/> |
|一次性迁移中的成本  <br/> |一次性成本重复每未来迁移  <br/> |
|较低的总体拥有成本 / 维护  <br/> |总体拥有成本高 / 维护  <br/> |
   
迁移到 Office 365 时，一次性移动将时间粗成本花费了规划，前期 （时您组织的数据，还可以决定要让进入云内容和要留下）。但是，一旦迁移数据时，升级将自动从那时，这在您不再需要管理硬件和软件更新，并将一个 Microsoft 服务级别协议 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) 备份服务器场的运行时间。
  
### <a name="migrate-to-sharepoint-online"></a>迁移到 SharePoint Online

确保 SharePoint Online 提供了您需要通过查看关联的服务说明的所有功能。下面是指向所有 Office 365 服务说明的链接：
  
[Office 365 服务说明](https://go.microsoft.com/fwlink/?linkid=272060)
  
当前没有依据您可以直接从迁移 SharePoint Server 2010 （或 SharePoint Foundation 2010） 到 SharePoint Online 一种方法，因此多工作是手动。这确实为您提供机会到存档和修剪数据和不再需要再移动的网站。您可以存档存储到的其他数据。此外，请记住 SharePoint Server 2010 和 SharePoint Foundation 2010 都不将停止运行末尾支持，因此管理员可以在此期间 SharePoint 仍在运行如果他们的客户忘记将其数据的一些移动一段时间。
  
如果您升级到 SharePoint Server 2013 或 SharePoint Server 2016，并决定将数据放入 SharePoint Online，您移动还可能涉及使用[SharePoint 迁移 API](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) （要迁移到 OneDrive for Business 的信息）。 
  
|**联机 Pro**|**联机手段**|
|:-----|:-----|
|Microsoft 提供 SPO 硬件和所有硬件管理。  <br/> |可用的功能可能不同于 SharePoint Server 本地和 SPO。  <br/> |
|是您的订阅的全局管理员和可能向 SPO 网站分配管理员。  <br/> |为 SharePoint Server 内部部署中的服务器场管理员可用某些操作不存在 （或不是必需的） 在 Office 365 中，但 SharePoint 管理中的 SharePoint 管理员角色，网站集管理和网站所有权是本地您的组织  <br/> |
|Microsoft 应用修补程序和修复基础硬件和软件 （包括 SQL server 的 SharePoint Online 运行） 的更新。  <br/> |因为没有基础服务中的文件系统无法访问，一些自定义项将受到限制。  <br/> |
|Microsoft 发布[服务级别协议](https://go.microsoft.com/fwlink/?linkid=843153)，并移动快速以解决服务级别的事件。  <br/> |备份和还原和其他恢复选项自动通过 SharePoint Online 中的服务-备份将覆盖否则使用。  <br/> |
|安全测试和服务器性能优化持续服务中由执行 Microsoft。  <br/> |对用户界面和其他 SharePoint 功能安装服务，可能需要进行切换打开或关闭的更改。  <br/> |
|Office 365 满足很多行业标准： [Office 365 合规性](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |迁移[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)协助是有限的。  <br/> 大部分升级将手动，或通过 SPO 迁移 API 中所述的[SharePoint Online 和 OneDrive 迁移内容指南](https://go.microsoft.com/fwlink/?linkid=843184)。  <br/> |
|Microsoft 支持工程师和数据中心中的员工都不具有无管理员访问权限限制到您的订阅。  <br/> |如果硬件基础结构需要升级以支持使用较新版本的 SharePoint，或者如果辅助服务器场上的升级需要，可以是额外的成本。  <br/> |
|合作伙伴可与一次性作业将数据迁移到 SharePoint Online 的帮助。  <br/> |在控件内将对 SharePoint Online 的不是所有更改。迁移后，设计差异菜单、 库和其他功能可能暂时会影响可用性。  <br/> |
|联机产品会自动更新跨这意味着可能废弃功能，但没有任何结束，则返回 true 的支持生命周期的服务。  <br/> |以及基础 SQL 服务器没有结束的支持生命周期的 SharePoint 服务器 （或 SharePoint Foundation）。  <br/> |
   
如果您决定创建新的 Office 365 网站，并将手动将数据迁移到它所需，您可以查看您的 Office 365 选项权利：
  
[Office 365 计划选项](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>升级 SharePoint Server 内部部署

为 SharePoint 内部部署产品 (SharePoint Server 2016) 的最新版本，必须*顺次*转 SharePoint 服务器升级，这意味着没有方法来从 SharePoint Server 2010 升级到 SharePoint Server 2016 直接。 
  
|||
|:-----|:-----|
||串行升级路径 ***: SharePoint Server 2010 **\>** SharePoint Server 2013 **\>** SharePoint Server 2016 |
   
如果您选择从 SharePoint 2010 到 SharePoint Server 2016 遵循的完整路径，这将花费时间和规划。升级涉及方面 （注意 SQL 服务器也必须进行升级） 的已升级的硬件、 软件和管理成本。此外，自定义项可能需要升级，或甚至放弃。确保升级 SharePoint 服务器场之前，在所有关键自定义收集注释。
  
> [!NOTE]
> 可以维护您的支持 SharePoint 2010 服务器场这一端，安装 SharePoint Server 2016 场在新硬件上 （以便在单独的服务器场运行的并行），然后规划和执行手动 （对于下载和重新将内容上载的内容的迁移示例）。有 （如文档来自 2010年具有与执行手动移动操作的帐户的别名当前的最后一个修改的帐户的），这些手动移动到的潜在缺陷和提早制定必须完成的一些工作 (重新创建网站、 子网站、 权限和列表结构）。它是合适的时间考虑的数据您可以将移入存储，或不再需要哪种产品。这样可以减少迁移的影响。无论进行上述，清理升级您的环境之前。在某些现有服务器场升级，才能正常运行，并且 （确定） 之前停用 ！ 
  
请记住，若要查看**支持和不支持的升级途径**： 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您有**自定义项**，它非常重要的迁移路径中有一个计划升级每个步骤： 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**内部部署 Pro**|**在本地手段**|
|:-----|:-----|
|设置从服务器硬件完全控制的 SharePoint 服务器场 （和它的 SQL） 的所有方面。  <br/> |所有换和修补程序都发生的公司责任 （但如果您的产品不支持的末尾，您可以进行付费的 Microsoft 支持）：  <br/> |
|SharePoint Server 的完整功能集在本地与 SharePoint Online 订阅通过混合连接的本地服务器场的选项。  <br/> |升级、 修补程序、 安全修补程序、 硬件升级和 SharePoint Server 并 SQL 服务器场的所有维护是本地托管。  <br/> |
|更高版本比使用 SharePoint Online 的自定义选项的完全访问权限。  <br/> |[支持的 Office 365 的合规性标准](https://go.microsoft.com/fwlink/?linkid=843165)必须是本地手动配置。  <br/> |
|安全，执行测试和服务器性能调整，在您的本地 （由您控制）。  <br/> |Office 365 可能使功能可供 SharePoint Online 的不能与部署 SharePoint Server 互操作  <br/> |
|合作伙伴可帮助迁移到下一个版本的 SharePoint Server （及其他认证实战） 的数据。  <br/> |SharePoint Server 网站不会自动使用[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)证书中所示是 SharePoint Online。  <br/> |
|完全控制权限的命名约定、 备份和还原和部署 SharePoint Server 中的其他恢复选项。  <br/> |SharePoint Server 本地非常重视产品生命周期。  <br/> |
   
### <a name="upgrade-resources"></a>升级的资源

首先比较硬件和软件要求。如果您不能满足基本升级上当前的硬件要求，可以意味着您需要先，升级中的服务器场或 SQL server 的硬件或还可以决定将您的网站的一些百分比移动到的 SharePoint Online 长绿硬件。一旦您已进行评估，按照支持的升级途径和方法。
  
- **硬件/软件要求**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **软件边界和限制**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **升级过程概述**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>创建 SharePoint Online 和 SharePoint Server 本地之间的 SharePoint 混合解决方案

（可能在本地和一些迁移的联机领域的优势的需要） 的另一种选择是混合，可以将 SharePoint Server 2013 或 2016年服务器场连接到 SharePoint Online，从而创建 SharePoint 混合：[了解有关 SharePoint 混合解决方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
如果您决定迁移目标是混合 SharePoint 服务器场，请确保规划哪些站点和用户应将移动到联机状态，并且其需要保持内部部署。查看和 SharePoint Server 服务器场的内容 （确定哪些数据如何提高公司的高、 中型或低影响） 的排名可能非常有帮助进行此决定。可能的唯一需要与 SharePoint Online 共享是 （a） 用户帐户登录和 （b） 的 SharePoint Server 搜索索引-这可能不是清除直到一下如何使用您的网站。如果您的公司稍后决定将您的所有内容迁移到 SharePoint Online，您可以联机移动所有剩余的帐户和数据并停用的本地服务器场，并管理 SharePoint 场将通过 Office 365从上的点的控制台。
  
请务必熟悉现有的混合以及如何配置您的本地 SharePoint 场和 Office 365 订阅之间的连接类型。
  
请参阅混合 SharePoint 服务器场的工作原理一个好方法是通过创建[Office 365 开发/测试环境](https://go.microsoft.com/fwlink/?linkid=843152)。一旦您具有试用版或购买 Office 365 订阅，您就会在您的方式在 SharePoint Online，您可以向其迁移数据中创建网站集、 web 和文档库 (请手动，通过使用的迁移 api，或-如果您想要迁移我网站内容到 OneDrive for Business-通过混合向导）。
  
> [!NOTE]
> 请记住在 SharePoint Server 2010 服务器场将首先需要升级，本地、 SharePoint Server 2013 或 SharePoint Server 2016 用于混合选项。SharePoint Foundation 2010 和 SharePoint Foundation 2013 无法使用 SharePoint Online 创建混合连接。 
  
## <a name="related-topics"></a>相关主题

[资源以帮助您从 Office 2007 升级或 2010年服务器和客户端](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[从 SharePoint 2010 升级到 SharePoint 2013 的最佳做法](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[在 SharePoint 2013 中解决数据库升级问题](https://go.microsoft.com/fwlink/?linkid=843195)
  
[搜索 Microsoft 合作伙伴，从而帮助进行升级](https://go.microsoft.com/fwlink/?linkid=841249)
  
[SharePoint 2013 的更新产品服务策略](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[SharePoint Server 2016 的更新产品服务策略](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

