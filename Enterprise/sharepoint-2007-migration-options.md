---
title: 需要考虑的 SharePoint 2007 迁移选项
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
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
description: SharePoint Server 2007 已达到结束的支持，并且升级的时间。使用本文可帮助您创建计划。
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169874"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>需要考虑的 SharePoint 2007 迁移选项

Microsoft SharePoint 2007 和 SharePoint Server 2007 已达到结束的支持。是要升级的次 ！本文提供了有关迁移选项的信息。
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>SharePoint 的常用升级策略

有多个 SharePoint Server 环境升级的方法。如果您具有 Microsoft Office SharePoint Server 2007 服务器场，下面是升级方法的一些示例：
  
- 数据库附加
    
- 并行升级
    
- 就地升级
    
- 混合升级 (就地使用已分离数据库 / 单独的数据库附加)
    
- SharePoint 混合 （连接 online 到内部部署 SharePoint）
    
- 手动移动网站集或库之间的数据
    
- FastTrack 向导升级到 Office 365 （[SharePoint Online 部署顾问](https://aka.ms/spoguidance)）
    
- 迁移到 SharePoint Online (SPO) Office 365 中的 API
    
什么最适合您？
  
您的服务器场支持和用于的知识-您是策略性强度当谈升级。人员使用 SharePoint 服务器场的方式将帮助您从您的选项中进行选择。
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 还具有此处未涉及逐步升级。若要升级的特定步骤的列表，请参阅文章请参阅[SharePoint Server 2007 末尾支持路线图](sharepoint-2007-end-of-support.md)。 
  
请记住检查正在升级到 SharePoint 的任何版本的[产品生命周期](https://support.microsoft.com/en-us/lifecycle/search)和系统要求。这样，您将在下次升级将 （例如，如果您在 SharePoint Server 2010 规划多个升级，请确保您知道其末尾支持日期这样的旧式产品暂停），必要时请注意，并准备某些必须支持您的计划的硬件。 
  
如果您计划转换的部分或全部，您 SharePoint 网站添加到 Office 365 在云中，这是书签[的 Office 365 服务说明](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)的链接的时间。您将需要服务说明以了解 SharePoint Online 功能和方式可能不同于内部部署 SharePoint Server。升级功能的 Microsoft Office SharePoint Server 2007 服务器场。如果您安装有会失效的网站，修复这些升级之前。
  
## <a name="a-note-about-managing-risk"></a>有关管理风险的注释

并行类似的方法很重要的升级的逻辑的配色方案中。并行升级时，您将维护 Microsoft Office SharePoint Server 2007 服务器场，但构建服务器场的下一个版本从 (SharePoint Server 2010) 新硬件上。这有助于三种方式：
  
1. 您必须执行的 Microsoft Office SharePoint Server 2007 数据库的备份，单独对其进行升级，请通过使用数据库附加的地方。
    
2. 如果您图的仅少量关键文档库和其他信息在 Microsoft Office SharePoint Server 2007 服务器场使用，您可以选择手动将数据从 Microsoft Office SharePoint Server 2007 移动到 SharePoint Server 2010或向下一个版本 （这可以更轻松地） 执行仅特定站点和网站。
    
3. Microsoft Office SharePoint Server 2007 服务器场，直接，更加安全服务器场的数据包含在您升级执行越小。
    
为您提供更少的轻松选项放弃路径并再次开始与您的原始环境直接在 Microsoft Office SharePoint Server 2007 服务器场，将操作类似的就地升级的方法。尽可能多地，在某些安全措施 （例如笔记记录和测试备份的原始环境） 中构建。例如，如果您的 Microsoft Office SharePoint Server 2007 服务器场是虚拟，并且重复的备份和还原的目的，请用然后备份和还原之前您升级的服务窗口的最新数据库。了解您可以选择要还原的数据库备份不会仅为您提供安全模式，它可以为您提供的放心。
  
> [!TIP]
> 对于[Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx)、 [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx)、 [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)和[SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx)存在升级的最佳做法文档。您还可以搜索[Microsoft 合作伙伴](https://partnercenter.microsoft.com/en-us/pcv/search)拥有与升级或 Office 365 迁移的体验。 
  
## <a name="make-your-plan"></a>使您的计划

如果您需要升级，您需要规划和一个大小不适合在这些情况下所有。您计划可能很简单，例如使用 SharePoint Online 中创建 Office 365 订阅，注册一个域，和重定向保存其文件的人员。且可能不可。该决定是都会，并且它是向您和您的用户真正需要什么。
  
> [!NOTE]
> Risky 要在其生命周期结束的软件上运行它。发现问题时，不再被修补超出支持的产品。这也意味着，如果出现新的安全威胁，将会有任何安全修补程序或修补程序因为不再受支持的结束的生命周期产品。请避免这种情况下 ！ 
  
### <a name="first-know-your-farm"></a>首先，了解您的服务器场

升级时，您的决策应基于您的服务器场为您的组织的用途。它满足什么需要？什么是其角色？公司内的每个服务器场可能具有不同的角色。SharePoint 场的一些可能是*关键*，一些可能文件存档-针对安全保存。或者，如果您的服务器场同时填充的许多角色，然后您可能需要知道哪些网站集、 web 或甚至文档库执行操作，任何自定义项，以及它们是如何重要。分析此级别数据可能看上去大量工作，但它节省时间和精力掌握您的域之前升级，或迁移，它。一旦您知道移动的所有部件，并最重要的二进制文件，也可以知道您已不能满足并可以留下。该知识仅受益您循序。 
  
因此，用户提及的内容最重要的 SharePoint 服务器场？
  
- 内置的 SharePoint 功能
    
- （如存档文件） 的大型数据集
    
- 可用性
    
- 关键应用程序、 web 部件或服务器场 （任务关键服务器场） 中的文档
    
- 满足合规性标准
    
- 自定义项
    
如果您运行从 SharePoint 场对您的业务基本内容，请说它可以用作有关客户端服务要求的关键数据的大型目录，可能会使刻度线旁关键应用程序，但也会是可用性 — 即，您的业务如果您无法使用 SharePoint while，影响。同样，可能会检查自定义，因为关键服务服务器场提供基于自定义代码、 网站定义或协同工作的自定义项的数量。
  
如果 SharePoint 而无需执行任何操作之外使用内置到软件，满足这些需求和您通常对其进行更新，并执行普通管理和维护，您可能已选择内置 SharePoint — 这也可能会您位于 SharePoint 的早期版本的原因。换句话说，它已不会需要其，并且您并不需要升级之前现在，在 Microsoft Office SharePoint Server 2007 结束的支持。
  
当您项目符号列表这些事项做，您为升级创建条件。换句话说，任何升级者必须满足此栏视为。这为您提供了一种方法，以便排除当前不满足您的需求的方法。
  
### <a name="a-simple-sample-plan"></a>一个简单示例计划

那里可能还需要是与高领导层的更多一致和其他 SharePoint 升级将花费的路径上的管理员。SharePoint Server 管理员通常在与 Microsoft SQL Server 管理员合作，使用网络和安全工作组和详细信息。其中有大量的利益干系人，您可能需要生成协议，或调整，您的升级和迁移计划。例如，如果您将数据迁移，以便您的公司的一部分在 Office 365 中使用 SharePoint Online 时，那里可能需要将性能调整或测试您的网络内。提早制定，应该被告知受影响的团队。
  
在我简单示例中，我显示 SharePoint 管理员的建议，然后列出所有利益干系人商定的计划。为清楚起见，记录您的协议和决策。
  
规划服务器场的深入分析后开始，并尝试确定服务器场、 难题和其他重要的信息将导致缩小一些升级选项的角色。此后，升级方案由 SharePoint 管理员和利益干系人达成一致的操作计划。
  
我最重要的项目符号列表：
  
- 可用性、 SharePoint 中内置的功能和合规性标准。
    
- 大部分数据是三个网站集，在与一个使用尤其重要开发小组和多个时区中的大量使用世界各地的会议工作区。
    
- 有十七广泛使用的其他网站。
    
- 两个文档库 （会议工作区和根网站集上的文档） 是最大 （超过 8000 文档每个）。我们有大量的存档的文档和列表的电子表格附件。
    
- 有十四个列表的库，具有必须保持在合规性中的敏感数据。
    
- 我们必须完成保留和电子发现，无论我们的能力。
    
- 此数据的一些必须保持内部部署，由于 InfoSec 规则。
    
 **我的升级和迁移选项：**
  
|||
|:-----|:-----|
|**是** <br/> |**否** <br/> |
|附加数据库的升级数据库  <br/> |就地升级  <br/> |
|与服务器场并行升级  <br/> |混合升级  <br/> |
|迁移 API 到 Office 365 中的 SPO （个人网站数据）  <br/> |SharePoint 混合 （尚未不需要）  <br/> |
|关键数据一些手动数据迁移到 SharePoint Online  <br/> |FastTrack 向导升级到 Office 365  <br/> |
   
 **我建议的计划：**
  
升级，使用本地版本的 SharePoint-并行，某些虚拟化，以便我们可以先升级数据库。从 SharePoint 2007 转到 SharePoint 2010。管理员和开发人员测试结果的服务器场。用户测试期间生成服务器场。在此期间修复显示停止的任何问题。同样，-并行、 升级 SharePoint 2010 数据库到 SharePoint 2013。测试用户测试/试点。在此期间修复显示停止的任何问题。
  
- 请考虑使用 SPO 搜索联合混合是否满足您的需求。
    
- 如果您想要从此处升级到 SharePoint Online，请考虑[FastTrack 帮助](https://fasttrack.microsoft.com)。 
    
- 确定任何网站集是否可以转移到 Office 365 订阅。（office 365 满足很多[合规性标准](https://technet.microsoft.com/library/office-365-compliance.aspx)。Office 365 具有[电子数据展示](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da)和可以通过合规性中心[包含](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E)执行操作。） 
    
否则，请继续-并行升级到 SharePoint Server 2016。
  
> [!NOTE]
> 之间建议规划管理员所做的实际过程和升级的升级依赖于其他利益干系人与发生的对话。例如，有时经济性强制管理员可以更改其计划。任意的最终决策是，您应记录的商定的计划是什么，循序。它可能看起来如下所示： 
  
 **我的行动计划：**
  
内部部署，我们使用虚拟环境来构建默认 SharePoint Server 2010 和 2013年。将新的 2016年满足系统要求的硬件上构建 SharePoint Server 2016。我们将执行数据库附加升级数据库从 SharePoint 2007 通过其与 SharePoint Server 2016 之间的所有版本。核心自定义项的正在重新创建和测试 SharePoint Server 中 2016年环境此时，如果本机功能已不符合我们的需求。如果我们操作成功，我们将具有与已升级数据库的新硬件上的本地服务器场和较少的自定义项。我们将升级后的内容数据库附加到 SharePoint Server 2013，测试、 用户测试/生产中的新网站集，然后执行 DNS 切换到 live 用于新的 SharePoint Server 2016 环境。
  
- 我们将立即不考虑 SharePoint Server 2016 和 SharePoint Online 之间的联盟混合。
    
- 我们网站的估计的 35%可以将转换为与虚拟域的新 SPO 网站或者，最终，成为 OneDrive 业务存储。寻找转换网站，或将新网站路由到 SPO 其他机会。
    
- 一些迁移的这一部分将手动，通过拖放到 OneDrive for Business 个人网站，并通过迁移 API 一些。
    
详细步骤，或为特定的升级说明的链接数应遵循计划。不应停止使用 MOSS 2007 计算机，并应为比较; 维护虚拟环境但是，在升级完成时将用户重定向到 SharePoint Server 2016。
  
选择一种方法通常主要因素是升级的总成本和时间 （您将看到详细介绍此 SharePoint 迁移路线图一文中） 中的成本。但是，规划提前将获益您极大地中设置期望值，明智，选择和组帧哪些成功将如下所示。
  
## <a name="related-links"></a>相关链接

[资源可帮助您升级从 Office 2007 的服务器和客户端](upgrade-from-office-2007-servers-and-products.md)
  
[搜索 Microsoft 生命周期策略和生命周期](https://support.microsoft.com/en-us/lifecycle)
  
[搜索 Microsoft 合作伙伴可帮助进行升级或迁移](https://partnercenter.microsoft.com/en-us/pcv/search)
  

