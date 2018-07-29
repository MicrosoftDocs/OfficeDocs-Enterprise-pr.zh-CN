---
title: Exchange 2007 停止提供支持路线图
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
description: 11 2017 年，在 Exchange Server 2007 达到结束的支持。如果您没有已开始迁移到 Office 365 的 Exchange 2007 或 Exchange 2016，现在是开始规划过程的时间。
ms.openlocfilehash: 4bb8933977c280b4bfaa686e858fc818a1dc4ace
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169804"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Exchange 2007 停止提供支持路线图

**2017 年 4 月 11，**，在 Exchange Server 2007 达到结束的支持。如果您没有已开始迁移到 Office 365 的 Exchange 2007 或 Exchange 2016，现在是开始规划过程的时间。 
  
## <a name="what-does-end-of-support-mean"></a>支持平均值内容的末尾？

Exchange Server，几乎所有 Microsoft 产品，如具有支持生命周期期间我们提供的新功能、 bug 修复、 安全修补程序，等等。此生命周期通常会持续 10 年中的产品的初始发布日期和此生命周期的结束称为产品的结束的支持。Exchange 2007 达到其结束的支持上 2017 年 4 月 11，因为 Microsoft 不再提供：
  
- 可能出现; 的问题的技术支持
    
- Bug 修复的问题的发现以及可能影响的稳定性和可用性的服务器。
    
- 安全漏洞的发现和可能使该服务器安全轻易; 地受到修补程序
    
- 更新所在的时区。
    
安装 Exchange 2007 的将继续此日期之后运行。但是，由于上面列出的更改，我们强烈建议您迁移从 Exchange 2007 尽快。
  
有关接近结束的支持的 Office 2007 服务器的详细信息，请参阅[规划从 Office 2007 服务器和产品升级](upgrade-from-office-2007-servers-and-products.md)。
  
## <a name="what-are-my-options"></a>我的选项是什么？

现在，Exchange 2007 已达到其结束的支持，我们强烈建议您浏览您的选项和准备迁移计划。您可以：
  
- 迁移到 Office 365 使用直接转换、 暂存，或混合迁移;
    
- 将 Exchange 2007 服务器迁移到新版本的 Exchange 本地服务器上。
    
以下各节浏览更多详细信息中的每个选项。
  
### <a name="migrate-to-office-365"></a>迁移到 Office 365

您的电子邮件迁移到 Office 365 是您最佳和最简单的选项可帮助您停用您的 Exchange 2007 部署。与迁移到 Office 365，您可以像进行单个从 10 岁技术跃点先进的功能：
  
- 合规性功能，如保留策略就地和诉讼保留，就地电子数据展示，和更多;
    
- Office 365 组;
    
- 重点收件箱;
    
- 深入分析;
    
- REST Api 以编程方式访问电子邮件、 日历、 联系人和等等。
    
Office 365 还获取新功能和体验第一个和您和您的用户可以通常开始立即使用它们。除了新功能，您不必担心：
  
- 购买和维护硬件;
    
- 用于供暖和制冷服务器; 的情况
    
- 保持最新的安全、 产品和时区修复;
    
- 维护存储和软件来支持合规性要求;
    
- 升级到新版本的 Exchange-您始终在 Office 365 中 Exchange 的最新版本上。
    
#### <a name="how-should-i-migrate-to-office-365"></a>如何应将迁移到 Office 365？

根据您的组织，您必须将帮助您到 Office 365 的几个选项。时选择的迁移选项，您需要考虑的一些像数座位或需要移动的邮箱、 长要迁移到最后一个，以及是否需要您的本地安装和过程中的 Office 365 之间进行无缝集成迁移。此表显示了迁移选项和最重要的因素将确定您将使用哪种方法。
  
| |
|**迁移选项**|**组织的规模**|**Duration**|
|:-----|:-----|:-----|
|直接转换迁移  <br/> |少于 150 座位  <br/> |每周或更少  <br/> |
|暂存迁移  <br/> |多个 150 座位  <br/> |几周  <br/> |
|完整的混合迁移  <br/> |数百到数千个座位  <br/> |几个月或更多  <br/> |
   
以下各节提供了这些方法的概述。签出[Decide 迁移路径上的](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27)，若要了解每种方法的详细信息。 
  
#### <a name="cutover-migration"></a>直接转换迁移

直接转换迁移是一个位置，在预选的日期和时间，您将迁移所有邮箱、 通讯组、 联系人和等等，到 Office 365;当您已完成，您将关闭内部部署 Exchange 服务器并启动以独占方式使用 Office 365。
  
直接转换迁移方法非常，没有很多个邮箱的小型组织要迅速到 Office 365，并无需处理一些其他方法的复杂性。但它的也有一些限制因为它应小于或等于一周中已完成，因为它要求用户重新配置其 Outlook 配置文件。时直接转换迁移可以处理最多 2,000 个邮箱，我们强烈建议使用此方法迁移 150 邮箱的最大值。如果您尝试迁移 150 多个邮箱、 无法用完之前您截止日期，传输所有邮箱的时间和 IT 支持人员可能会收到大量帮助用户重新配置 Outlook。
  
如果您正在考虑执行直接转换迁移，下面是需要考虑的几件事，请考虑：
  
- Office 365 需要连接到 Exchange 2007 服务器通过 TCP 端口 443; 使用 Outlook Anywhere
    
- 所有内部部署邮箱将被移动到 Office 365;
    
- 您将需要有权读取用户邮箱; 的内容的本地管理员帐户
    
- Exchange 2007 接受您想要使用 Office 365 需要中添加为服务; 中的已验证域的域
    
- 在开始迁移之间的时间和开始完成阶段时，Office 365 将定期同步的 Office 365 和内部部署邮箱。这样可以完成迁移，而不必担心留在您的内部部署邮箱; 电子邮件
    
- 用户将收到新临时密码他们将需要更改首次; 登录到其邮箱时其 Office 365 帐户
    
- 您将需要为每个用户邮箱迁移; 包括 Exchange Online 的 Office 365 许可证
    
- 用户将需要设置新的 Outlook 配置文件在每台其设备上，并再次下载其电子邮件。Outlook 将下载的电子邮件量可能各不相同。有关详细信息，了解一下[更改多少邮件的保留脱机](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)。
    
若要了解有关直接转换迁移的详细信息，看看：
  
- [有关使用直接转换迁移将电子邮件迁移到 Office 365 的注意事项](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [执行直接转换迁移到 Office 365 的电子邮件](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>暂存迁移

暂存的迁移是一个其中有几个几百个或几个数千个邮箱您想要迁移到 Office 365，需要执行一周或更多以完成迁移，并且不需要的任何高级的混合迁移功能喜欢共享的忙/闲日历信息rmation。
  
暂存的迁移非常适合于需要更多时间，以将其邮箱迁移到 Office 365 中，但仍计划完成几周内的迁移的组织。您可以迁移中"批处理"，使您能够控制多少，以及哪些邮箱、 邮箱迁移在给定时间。您可能批处理的邮箱的同一部门中的用户，例如，若要确保您所有移动它们在同一时间。或者，您可能直到最后一个批保持 executive 邮箱。使用直接转换迁移，用户将需要重新创建其 Outlook 配置文件。
  
如果您正在考虑执行暂存的迁移，下面是要考虑的几个事项：
  
- Office 365 需要连接到 Exchange 2007 服务器通过 TCP 端口 443; 使用 Outlook Anywhere
    
- 您将需要有权读取用户邮箱; 的内容的本地管理员帐户
    
- Exchange 2007 接受您想要使用 Office 365 需要中添加为服务; 中的已验证域的域
    
- 您需要创建 CSV 文件的完整名称和要迁移批次中的每个邮箱的电子邮件地址。此外需要包括您正在迁移，每个邮箱的新密码，然后将其密码发送给每个用户。将提示用户首次登录到其新的 Office 365 邮箱; 更改密码
    
- 开始迁移批次之间的时间和开始完成阶段时，Office 365 定期同步的批次中包含的 Office 365 和内部部署邮箱。这样可以完成迁移，而不必担心留在您的内部部署邮箱; 电子邮件
    
- 用户将收到新临时密码他们将需要更改首次; 登录到其邮箱时其 Office 365 帐户
    
- 您将需要为每个用户邮箱迁移; 包括 Exchange Online 的 Office 365 许可证
    
- 用户将需要设置新的 Outlook 配置文件在每台其设备上，并再次下载其电子邮件。Outlook 将下载的电子邮件量可能各不相同。有关详细信息，了解一下[更改多少邮件的保留脱机](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)。
    
若要了解有关分阶段迁移的详细信息，看看：
  
- [您需要了解的有关暂存电子邮件迁移到 Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [执行暂存的迁移到 Office 365 的电子邮件](https://support.office.com/en-us/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>完整的混合

一个其中贵组织拥有许多百，最多为数万，邮箱和您要移动到 Office 365 的部分或所有这些完整混合迁移。由于这些迁移通常长期，混合迁移使可能：
  
- Office 365 中的用户的忙/闲日历信息显示在本地用户，反之亦然。
    
- 请参阅包含在本地和 Office 365; 中的收件人的统一全局地址列表
    
- 查看所有用户，而不考虑它们是否在本地或 Office 365; 中的完整 Outlook 收件人卡
    
- 内部部署 Exchange 服务器与 Office 365 使用 TLS 和证书; 之间的安全电子邮件通信
    
- 将内部部署 Exchange 服务器和 Office 365 之间发送为内部，从而使他们的消息：
    
  - 正确进行评估和处理设定; 内部消息的传输和合规性代理
    
  - 绕过反垃圾邮件筛选器。
    
完整的混合迁移是最适用于组织希望在留在多个月或更多的混合配置。使用联机邮箱移动，您将获取列出前面的此部分中，加上目录同步和更好集成的合规性功能，能够将邮箱移动到与 Office 365 的功能。Office 365 成为内部部署组织的扩展。
  
如果您正在考虑执行操作完全混合迁移，下面是要考虑的几个事项：
  
- 完整的混合迁移不适合于组织的所有类型。由于完整混合迁移的复杂性，与小于几个几百个邮箱的组织通常看不到 justify 工作量和一个设置所需的成本的好处。如果这听起来您的组织，则强烈建议您改用; 考虑 Cutover 或暂存迁移
    
- 您将需要部署"混合服务器"作为您 Exchange 2007 组织中的至少一个 Exchange 2013 服务器。此服务器将 Exchange 2007 服务器; 代表通信与 Office 365
    
- Office 365 需要连接到"混合服务器"通过 TCP 端口 443; 使用 Outlook Anywhere
    
- 您需要设置您的本地 Active Directory 服务器与 Office 365; 之间使用 Azure Active Directory 连接 (AADConnect) 的目录同步
    
- 用户将能够登录到使用相同的用户名和密码时他们登录到本地网络 （需要使用密码同步和/或 Active Directory 联合身份验证服务的 Azure Active Directory 连接）; 它们使用其 Office 365 邮箱
    
- 您将需要为每个用户邮箱迁移; 包括 Exchange Online 的 Office 365 许可证
    
- 用户不需要在他们的设备 （某些旧的 Android 电话可能需要一个新的配置文件） 的最新的 Outlook 配置文件设置，并不需要重新下载其电子邮件。
    
如果适合您的完整混合迁移声音，看看以下资源可帮助您实现您的迁移：
  
- [Exchange 部署助理](https://aka.ms/exdeploy)
    
- [Exchange Server 混合部署](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- ["混合配置"向导](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [混合配置向导 FAQ](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [混合部署先决条件](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>迁移到新版本的 Exchange Server

尽管我们强烈相信，您可以通过迁移到 Office 365 中实现的最佳值和用户体验，我们还了解一些组织需要保留其电子邮件的本地。这可能是由于法规要求，以确保数据不存储在数据中心位于另一个国家/地区，依此类推。如果您选择保留电子邮件内部部署，您可以将您的 Exchange 2007 环境迁移到 Exchange 2010、 Exchange 2013 或 Exchange 2016。
  
我们建议如果无法迁移到 Office 365 迁移到 Exchange 2016。Exchange 2016 包含所有的功能和改进包括与早期版本的 Exchange 和 （尽管某些功能仅适用于 Office 365） 提供与 Office 365 体验最密切匹配。签出只需几个您已被不了解的事项：
  
|**Exchange 版本**|**功能**|
|:-----|:-----|
|Exchange 2010  <br/> | 角色基于访问控制 （不 Acl 权限）  <br/>  Outlook Web Access 邮箱策略  <br/>  共享忙/闲和委派组织之间的日历能力  <br/> |
|Exchange 2013  <br/> | *从 Exchange 2010 的功能和...*  <br/>  简化的体系结构减少到三个服务器角色的 （邮箱，客户端访问边缘传输）  <br/>  帮助保持泄露敏感信息的数据丢失预防策略 (DLP)  <br/>  显著改进 Outlook Web 应用程序体验  <br/> |
|Exchange 2016  <br/> | *从 Exchange 2013 的功能和...*  <br/>  进一步简化的服务器角色到刚邮箱和边缘传输  <br/>  与 SharePoint 以及集成改进的 DLP  <br/>  改进的数据库恢复  <br/>  联机文档协作  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>应迁移到哪个版本？

我们建议您最初假定您将迁移到 Exchange 2016。然后，使用以下信息，以确认您的假设或 Exchange 2016 出规则。如果您不能将迁移到 Exchange 2016 的一个原因或其他，执行相同处理 Exchange 2013，等等。
  
|**注意事项**|**更多信息**|
|:-----|:-----|
|支持日期结束  <br/> | Exchange 2007，如每个版本的 Exchange 具有自己末尾支持日期：  <br/> **Exchange 2010** -年 1 月 2020  <br/> **Exchange 2013** -年 4 月 2023  <br/> **Exchange 2016** -年 10 月 2025  <br/>  前面的末尾支持日期、 更快您需要执行其他迁移。年 1 月 2020年是大量仔细，比你想象 ！<br/> |
|Exchange 2010 和 2013年迁移路径  <br/> |下面是有关迁移到 Exchange 2010 或 Exchange 2013 的一般阶段：  <br/> 将 Exchange 2010 或 2013年安装到现有 Exchange 2007 组织移动服务和其他基础结构到 Exchange 2010 或 2013年移动邮箱到 Exchange 2010 或 2013年取消剩余 Exchange 2007 服务器的公用文件夹 |
|Exchange 2016 迁移路径  <br/> |下面是用于迁移到 Exchange 2016 的一般阶段：  <br/> Exchange 2013 安装到现有 Exchange 2007 组织移动服务和其他基础结构到 Exchange 2013 移动邮箱到 Exchange 2013 取消剩余 Exchange 2007 服务器安装 Exchange 2016 到现有的公用文件夹Exchange 2013 组织。将邮箱、 公用文件夹、 服务和其他基础结构移动到 Exchange 2016 （顺序无关紧要）。停用剩余 Exchange 2013 服务器 > [!NOTE]> 从 Exchange 2013 迁移到 Exchange 2016 很简单。这两个版本有几乎相同的硬件要求。此，并且这些版本是因此兼容，意味着您可以重新生成您购买 Exchange 2013 服务器，并在其上安装 Exchange 2016 这一事实。和具有联机邮箱移动大多数用户将从不发现其邮箱移动关闭服务器，然后再后已使用 Exchange 2016 重建它。           |
|版本共存  <br/> | 当迁移到：  <br/> **Exchange 2016**不能包括 Exchange 2007 服务器的组织中安装 Exchange 2016。首先需要身份验证迁移到 Exchange 2010 或 2013 （我们强烈建议 Exchange 2013） 和删除所有 Exchange 2007 服务器，然后迁移到 Exchange 2016。<br/> **Exchange 2010 或 Exchange 2013**您可以安装到现有的 Exchange 2007 组织的 Exchange 2010 或 Exchange 2013。这样可以安装一个或多个 Exchange 2010 或 2013年服务器，并执行迁移。<br/> |
|服务器硬件  <br/> | 从 Exchange 2007，服务器硬件要求已发生更改。您需要确保您要使用的硬件兼容。您可以找出有关每个版本此处的硬件要求的详细信息：<br/> [Exchange 2016 系统要求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Exchange 2013 系统要求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/> [Exchange 2010 系统要求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx) <br/>  您会发现，使用 Exchange 性能和增加的计算能力的重要改进和更高版本服务器中的存储容量，您可能需要较少的服务器来支持相同的邮箱数。  <br/> |
|操作系统版本  <br/> | 每个版本的最小受支持的操作系统版本是：  <br/> **Exchange 2016**Windows Server 2012  <br/> **Exchange 2013**Windows Server 2008 R2 SP1  <br/> **Exchange 2010**Windows Server 2008 SP2  <br/>  您可以在[Exchange 可支持性矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关支持的操作系统的详细信息。  <br/> |
|Active Directory 林功能级别  <br/> | 最小支持 Active Directory 林功能级别的每个版本是：  <br/> **Exchange 2016**Windows Server 2008 R2 SP1  <br/> **Exchange 2013**Windows Server 2003  <br/> **Exchange 2010**Windows Server 2003  <br/>  您可以在[Exchange 可支持性矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关林功能级别支持的详细信息。  <br/> |
|Office 客户端版本  <br/> | 每个版本的受支持的最小 Office 客户端版本是：  <br/> **Exchange 2016**Office 2010 （具有最新的更新）  <br/> **Exchange 2013**Office 2007 SP3  <br/> **Exchange 2010**Office 2003  <br/>  您可以在[Exchange 可支持性矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关 Office 客户端支持的详细信息。  <br/> |
   
#### <a name="how-do-i-migrate"></a>如何迁移

如果您决定要保留电子邮件内部部署，您可以使用以下资源可帮助您实现您的迁移：
  
- [Exchange 部署助理](https://aka.ms/exdeploy)
    
- Exchange [2016年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)、 [2010年](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)的 active Directory 架构更改
    
- Exchange [2016年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)， [2013年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)， [2010年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx)的系统要求
    
- Exchange [2016年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx)， [2013年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)， [2010年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.141%29.aspx)的先决条件
    
## <a name="what-if-i-need-help"></a>如果需要帮助？

如果您正在迁移到 Office 365，您可能有资格使用我们的 Microsoft FastTrack 服务。FastTrack 提供最佳实践、 工具和资源，以使您的迁移到 Office 365 尽可能流畅。最重要的是，您必须实际支持工程师，它将指导您完成迁移，从规划和设计一直到把最后一个邮箱迁移。如果您想要了解有关 FastTrack 的详细信息，了解一下[Microsoft FastTrack](https://fasttrack.microsoft.com/)。
  
如果您遇到任何问题期间迁移到 Office 365，并且您不使用 FastTrack 或在迁移到新版本的 Exchange 服务器，我们将帮助。以下是您可以使用一些资源：
  
- [技术社区](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [客户支持](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>相关主题

[资源可帮助您升级您的 Office 2007 服务器和客户端](upgrade-from-office-2007-servers-and-products.md)
  
[Office 退休组 （Microsoft 技术社区）](https://go.microsoft.com/fwlink/?linkid=842065)
  

