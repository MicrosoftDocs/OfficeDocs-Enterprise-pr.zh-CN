---
title: 要考虑的 SharePoint 2007 迁移选项
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
description: SharePoint Server 2007 已到达支持的结束时间，现在是时候升级了。 使用本文可帮助您创建计划。
ms.openlocfilehash: 2ed36816eeb466cd35b999b48521495406d28641
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078101"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>要考虑的 SharePoint 2007 迁移选项

Microsoft SharePoint 2007 和 SharePoint Server 2007 已达到支持的结尾。 是时候升级了！ 本文提供了有关迁移选项的信息。
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>SharePoint 的常见升级策略

有多种方法可以升级 SharePoint Server 环境。 如果你拥有 Microsoft Office SharePoint Server 2007 场，则以下是升级方法的一些示例：
  
- 数据库附加
    
- 并行升级
    
- 就地升级
    
- 混合升级（就地与已分离的数据库/单独的数据库附加）
    
- SharePoint 混合（联机连接到本地 SharePoint）
    
- 在网站集或库之间手动移动数据
    
- FastTrack 向导升级到 Office 365 （[SharePoint Online 部署顾问](https://aka.ms/spoguidance)）
    
- Office 365 中的迁移 API 到 SharePoint Online （SPO）
    
哪种方法最适合你？
  
在需要升级时，您对服务器场所做和使用的知识方面的知识就是战术性的强项。 用户使用 SharePoint 服务器场的方式将有助于您从选项中进行选择。
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 还包含此处未涵盖的逐步升级。 若要查看特定于步骤的升级文章的列表，请参阅[SharePoint Server 2007 end Support 路线图](sharepoint-2007-end-of-support.md)。 
  
请务必查看要升级到的任何 SharePoint 版本的[产品生命周期](https://support.microsoft.com/lifecycle/search)和系统要求。 这样，你就可以知道何时需要进行下一次升级（例如，如果你在 SharePoint Server 2010 等旧产品上暂停以规划更多升级），请确保你知道其支持日期的结束时间，并确保你有支持你的计划的硬件。 
  
如果您计划将 SharePoint 网站的部分或全部转换为云中的 Office 365，这是将指向[office 365 的服务说明](https://technet.microsoft.com/library/office-365-service-descriptions.aspx)的链接做成书签的时间。 你将需要服务说明来了解 SharePoint Online 功能以及它们可能与本地 SharePoint Server 的不同之处。 升级功能 Microsoft Office SharePoint Server 2007 场。 如果您的安装中存在损坏的网站，请在升级之前将其修复。
  
## <a name="a-note-about-managing-risk"></a>有关管理风险的说明

诸如 "并行" 的方法在升级逻辑的方案中非常重要。 并行升级时，将维护 Microsoft Office SharePoint Server 2007 场，但在新硬件上构建场中的下一个版本（SharePoint Server 2010）。 这有助于以下三种方式：
  
1. 您可以使用数据库附加来备份 Microsoft Office SharePoint Server 2007 数据库，从而单独升级这些数据库。
    
2. 如果你确定只有少量关键文档库和其他信息在 Microsoft Office SharePoint Server 2007 场中使用，则可以选择将 Microsoft Office SharePoint Server 2007 中的数据手动移动到 SharePoint Server 2010，或者仅将特定网站和 web 仅用于下一版本（这可以使您的工作更轻松）。
    
3. 对 Microsoft Office SharePoint Server 2007 服务器场所做的操作越少，服务器场包含的数据越安全。
    
就地升级等方法将直接在 Microsoft Office SharePoint Server 2007 场中直接操作，为您提供更少的选择，以放弃路径并再次开始使用 pristine 环境。 尽可能地构建一些安全措施（如采用和测试原始环境的备份）。 例如，如果您的 Microsoft Office SharePoint Server 2007 服务器场是虚拟的，并且出于备份和还原目的而复制，则在升级服务时段之前备份和还原最新的数据库。 如果知道您可以还原数据库备份，则不会仅为您提供故障保护，从而使您高枕无忧。
  
> [!TIP]
> [Microsoft Office SharePoint server 2007](https://technet.microsoft.com/library/cc261992%28v=office.12%29.aspx)、 [sharepoint server 2010](https://technet.microsoft.com/library/cc261992%28v=office.14%29.aspx)、 [Sharepoint server 2013](https://technet.microsoft.com/library/cc261992%28v=office.15%29.aspx)和[SharePoint server 2016](https://technet.microsoft.com/library/cc261992%28v=office.16%29.aspx)的升级的最佳实践文档存在。 您还可以搜索对升级或 Office 365 迁移有经验的[Microsoft 合作伙伴](https://partnercenter.microsoft.com/pcv/search)。 
  
## <a name="make-your-plan"></a>制定计划

如果需要升级，则需要一个计划，并且一种大小不能在这些情况下适用。 您的计划可能非常简单，如 "使用 SharePoint Online 创建 Office 365 订阅，注册一个域，重定向用户将文件保存到"。 也可能不是。 这是你的决定，并将其用于你和你的用户真正需要的内容。
  
> [!NOTE]
> 在其生命周期结束的软件上运行会有风险。 如果发现问题，则无法再对不支持的产品进行修补。 这也意味着，如果出现新的安全威胁，由于不再支持生命周期产品，因此不会有安全修补程序或修补程序。 请避免出现这种情况！ 
  
### <a name="first-know-your-farm"></a>首先，了解你的服务器场

在升级时，您的决策应取决于您的服务器场为您的组织执行的操作。 它满足的需求是什么？ 其角色是什么？ 公司中的每个服务器场可能具有不同的角色。 你的一些 SharePoint 场可能非常*关键*，一些可能是文件存档，也可能是安全保留的。 或者，如果您的服务器场同时填充了多个角色，则您可能需要了解网站集、web 甚至文档库的功能、任何自定义设置以及它们的重要性。 在此级别分析数据看起来可能相当于许多工作，但在升级或迁移之前，它会节省时间和精力来主控域。 知道所有移动部件和最重要的位之后，您还将了解已 outgrown 的内容并可能会留下。 这种知识只会对您的未来有益。 
  
那么，用户说什么对你的 SharePoint Server 服务器场最重要？
  
- 内置的 SharePoint 功能
    
- 大型数据文档集（如文件存档）
    
- 供应情况
    
- 服务器场中的关键应用程序、web 部件或文档（任务关键型服务器场）
    
- 满足合规性标准
    
- 自定义项
    
如果您在 SharePoint 服务器场中运行重要的业务，则假设它的作用类似于有关客户端服务要求的关键数据的大型目录，则可以在 "关键应用程序" 旁添加一个勾选标记，也可以在 "可用性" 旁进行 "可用性"，也就是说，您的业务将如果你无法使用 SharePoint 一段时间，则会受到影响。 同样，您可以检查 "自定义"，因为您的服务器场提供的关键服务基于自定义代码、网站定义或可协同工作的大量自定义项。
  
如果 SharePoint 满足这些需求，而无需在使用软件的内置功能的情况下执行任何操作，并且通常会将其更新并执行常规管理和维护，则可能选择了 "内置 SharePoint"，这也可能是置于较旧版本的 SharePoint 上的原因。 换句话说，它已完成您所需的操作，并且在 Microsoft Office SharePoint Server 2007 的支持终止之前，您不需要进行升级。
  
当您在项目中列出这些内容时，请为升级创建条件。 换句话说，任何升级都必须满足要考虑的这条。 这为您提供了一种方法，用于排除当前无法满足您需求的方法。
  
### <a name="a-simple-sample-plan"></a>一个简单的示例计划

在你的 SharePoint 升级将采用的路径上，可能需要更大的与领导和其他管理员达成一致意见。 SharePoint Server 管理员通常与 Microsoft SQL Server 管理员合作，与网络和安全团队协同工作，等等。 在有大量利益干系人的情况下，您可能需要为升级和迁移计划构建协议或调整。 例如，如果您迁移数据以便贵公司的一部分使用 Office 365 中的 SharePoint Online，则可能需要在网络中进行性能调整或测试。 应提前通知受影响的团队。
  
在我的简单示例中，我显示了 SharePoint 管理员的建议，然后列出了所有利益干系人同意的计划。 为清楚起见，请记录你的协议和决策。
  
计划在对服务器场进行深入分析之后开始，并尝试确定服务器场的角色、痛点和其他重要信息，这将导致缩小某些升级选项。 随后，SharePoint 管理员将提出升级建议，并且利益干系人同意行动计划。
  
我的 "最重要" 项目符号列表：
  
- 可用性、SharePoint 内置功能以及合规性标准。
    
- 大多数数据都在三个网站集上，而开发团队使用一个会议工作区尤为重要，并且在全球范围内多个时间区域使用。
    
- 有17个其他网站广泛使用。
    
- 两个文档库（根网站集上的会议工作区和文档）最大（每个文档库超过8000个文档）。 我们有大量存档文档和列表，其中包含电子表格附件。
    
- 有十四个具有敏感数据的库列表，必须保持合规性。
    
- 我们必须能够在任何位置执行保留和电子发现。
    
- 由于 InfoSec 规则，这些数据中的某些数据必须保持本地。
    
 **我的升级和迁移选择：**
  
|||
|:-----|:-----|
|**是** <br/> |**否** <br/> |
|使用数据库附加升级数据库  <br/> |就地升级  <br/> |
|并行升级服务器场  <br/> |混合升级  <br/> |
|迁移 API 到 Office 365 中的 SPO （针对个人网站数据）  <br/> |SharePoint 混合（尚不需要）  <br/> |
|对关键数据的一些手动数据迁移到 SharePoint Online  <br/> |FastTrack 向导升级到 Office 365  <br/> |
   
 **我建议的计划：**
  
本地升级（包含 SharePoint 并行的版本），以进行虚拟化，以便我们可以先升级数据库。 从 SharePoint 2007 转到 SharePoint 2010。 管理员和 Devs 测试生成的服务器场。 用户测试生成的服务器场。 解决此期间的任何显示停止问题。 同样，并行将 SharePoint 2010 数据库升级到 SharePoint 2013。 测试. 用户测试/试点。 解决此期间的任何显示停止问题。
  
- 如果与 SPO 的联合混合搜索符合你的需求，请考虑使用。
    
- 如果要从此处升级到 SharePoint Online，请考虑[FastTrack 帮助](https://fasttrack.microsoft.com)。 
    
- 确定是否可以将任何网站集卸载到 Office 365 订阅。 （Office 365 符合许多[合规性标准](https://technet.microsoft.com/library/office-365-compliance.aspx)。 Office 365 具有[电子数据展示](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da)，可以通过合规性中心进行[保留](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E)。 
    
否则，继续并行升级到 SharePoint Server 2016。
  
> [!NOTE]
> 在计划升级和实际过程的管理员之间的建议是，与升级所依赖的其他利益干系人进行的对话。 例如，经济性有时强制管理员更改其计划。 无论最终的决定是什么，您都应记录商定的计划是什么，即将进行。 它可能如下所示： 
  
 **我的行动计划：**
  
在内部部署中，我们使用虚拟环境构建默认的 SharePoint Server 2010 和2013。 SharePoint Server 2016 将构建在满足2016的系统要求的新硬件上。 我们会将数据库附加到从 SharePoint 2007 升级数据库，通过 it 和 SharePoint Server 2016 之间的所有版本。 此时，在 SharePoint Server 2016 环境中为和测试核心自定义项，前提是本机功能尚未满足我们的需求。 如果我们成功，我们将在具有升级数据库的新硬件上安装本地服务器场，并减少自定义项。 我们会将升级后的内容数据库附加到 SharePoint Server 2013 中的新网站集、测试、用户测试/试点，然后将 DNS 剪切到新的 SharePoint Server 2016 环境以供实时使用。
  
- 现在，我们不会在 SharePoint Server 2016 和 SharePoint Online 之间考虑联合混合。
    
- 我们的网站的估计35% 可以通过虚域转换为新的 SPO 网站，也可以是最终成为 OneDrive for business 存储。 寻找其他机会来转换网站，或将新网站路由到 SPO。
    
- 此部分迁移过程是手动进行的，通过拖放到 OneDrive for business 个人网站，有些是迁移 API。
    
更详细的步骤或指向特定升级方向的多个链接应遵循计划。 MOSS 2007 计算机不应退役，应维护虚拟环境以进行比较;但是，当用户被重定向到 SharePoint Server 2016 时，将完成升级。
  
选择方法的主要因素是升级的总成本和时间成本（您将在 SharePoint 迁移路线图文章中详细了解）。 但是，事先规划将有益于设置预期、明智选择和确定成功的外观。
  
## <a name="related-links"></a>相关链接

[可帮助您从 Office 2007 服务器和客户端进行升级的资源](upgrade-from-office-2007-servers-and-products.md)
  
[Microsoft 生命周期策略和生命周期搜索](https://support.microsoft.com/lifecycle)
  
[搜索可帮助升级或迁移的 Microsoft 合作伙伴](https://partnercenter.microsoft.com/pcv/search)
  

