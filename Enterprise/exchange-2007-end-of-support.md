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
description: 在2017年4月11日, Exchange Server 2007 已到达支持终止。 如果尚未开始从 Exchange 2007 迁移到 Office 365 或 Exchange 2016, 现在是开始规划的时间。
ms.openlocfilehash: 674de8904d03e024a8a75b945b5ef94319214f92
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33488468"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Exchange 2007 停止提供支持路线图

在**2017 年4月 11**日, Exchange Server 2007 已到达支持终止。 如果尚未开始从 Exchange 2007 迁移到 Office 365 或 Exchange 2016, 现在是开始规划的时间。 
  
## <a name="what-does-end-of-support-mean"></a>支持终止的含义是什么？

与几乎所有 Microsoft 产品一样, Exchange Server 都具有支持生命周期, 在此期间我们提供了新的功能、缺陷修补程序、安全修补程序等。 此生命周期通常是从产品初始发布之日起10年的时间, 而此生命周期的结束时间也称为产品的支持终止的期限。 由于 Exchange 2007 在2017年4月11日到达其支持的结束时间, Microsoft 不再提供:
  
- 可能出现的问题的技术支持;
    
- 针对已发现且可能影响服务器的稳定性和可用性的问题的 Bug 修补程序。
    
- 已发现的漏洞安全修补程序以及可能会使服务器易受安全威胁的安全修补程序。
    
- 时区更新。
    
在此日期之后, 你的 Exchange 2007 安装将继续运行。 但是, 由于上面列出了所做的更改, 强烈建议您尽快从 Exchange 2007 迁移。
  
有关即将结束支持的 office 2007 服务器的详细信息, 请参阅[从 Office 2007 服务器和产品规划升级](upgrade-from-office-2007-servers-and-products.md)。
  
## <a name="what-are-my-options"></a>我的选项是什么？

现在, Exchange 2007 已达到其支持的结尾, 强烈建议您浏览选项并准备迁移计划。 可以执行下列操作：
  
- 使用直接转换、暂存或混合迁移迁移到 Office 365;
    
- 将 exchange 2007 服务器迁移到本地服务器上的较新版本的 exchange。
    
以下各节更详细地探讨了每个选项。
  
### <a name="migrate-to-office-365"></a>迁移到 Office 365

将电子邮件迁移到 Office 365 是帮助您停用 Exchange 2007 部署的最简单且最简单的选项。 通过迁移到 Office 365, 你可以将一个从10年旧的技术到一种跃点, 以提供艺术功能, 如下所示:
  
- 合规性功能, 如保留策略、就地和诉讼保留、就地电子数据展示等;
    
- Office 365 组;
    
- 重点收件箱;
    
- Delve 分析;
    
- 用于以编程方式访问电子邮件、日历、联系人等的 REST api。
    
Office 365 还获取了新的功能和体验, 并且你的用户通常可以立即开始使用它们。 除了新功能之外, 您无需担心:
  
- 购买和维护硬件;
    
- 支付对服务器加热和冷却的费用;
    
- 及时了解安全性、产品和时区的修补程序;
    
- 维护存储和软件以支持合规性要求;
    
- 升级到新版本的 exchange-始终在 Office 365 中的最新版本的 exchange 上。
    
#### <a name="how-should-i-migrate-to-office-365"></a>我应如何迁移到 Office 365？

根据你的组织, 你有几个可帮助你获取 Office 365 的选项。 选择迁移选项时, 需要考虑几个因素, 如需要移动的座位或邮箱数、您希望迁移的持续时间, 以及您是否需要在内部部署安装和 Office 365 之间实现无缝集成迁移。 此表显示了您的迁移选项和最重要的因素, 这些因素将决定您将使用哪种方法。
  
| |
|**迁移选项**|**组织大小**|**Duration**|
|:-----|:-----|:-----|
|直接转换迁移  <br/> |座位数少于150  <br/> |一周或更少  <br/> |
|暂存迁移  <br/> |超过150的座位  <br/> |几周  <br/> |
|完全混合迁移  <br/> |数百到数千个座位  <br/> |几个月或更多  <br/> |
   
以下各节提供了这些方法的概述。 请查看[迁移路径](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27), 以了解每个方法的详细信息。 
  
#### <a name="cutover-migration"></a>直接转换迁移

直接转换迁移是指在预先选择的日期和时间, 将所有邮箱、通讯组、联系人等迁移到 Office 365;完成后, 你将关闭本地 Exchange 服务器, 并以独占方式开始使用 Office 365。
  
对于没有很多邮箱的小型组织来说, 直接转换迁移方法非常有用, 要快速获取 Office 365, 并且不希望处理其他方法中的一些复杂性。 但它也受到限制, 因为它应在一周或更短的时间内完成, 因为它要求用户重新配置其 Outlook 配置文件。 虽然直接转换迁移最多可以处理2000个邮箱, 但我们强烈建议您使用此方法最多迁移150个邮箱。 如果您尝试迁移超过150个邮箱, 则可能会在你的截止时间之后停止转移所有邮箱, 并且 IT 支持人员可能会在帮助用户重新配置 Outlook 时遇到大量的情况。
  
如果你正在考虑进行直接转换迁移, 请考虑以下几点:
  
- Office 365 将需要通过 TCP 端口443在 Outlook 无处不在上连接到 Exchange 2007 服务器。
    
- 所有内部部署邮箱都将移至 Office 365;
    
- 您需要具有可访问您的用户邮箱内容的本地管理员帐户, 请参阅。
    
- 需要在 Office 365 中使用的 Exchange 2007 接受域作为服务中的已验证域进行添加;
    
- 在开始迁移和开始完成阶段之间的时间内, office 365 将定期同步 office 365 和本地邮箱。 这样, 你就可以完成迁移, 而无需担心在你的内部部署邮箱中留下的电子邮件。
    
- 用户将收到 Office 365 帐户的新的临时密码, 他们需要在首次登录邮箱时进行更改;
    
- 你将需要 Office 365 许可证, 其中包含你迁移的每个用户邮箱的 Exchange Online;
    
- 用户需要在各自的每台设备上设置一个新的 Outlook 配置文件, 并再次下载他们的电子邮件。 Outlook 将下载的电子邮件数量可能有所不同。 有关详细信息, 请参阅[更改要保持脱机的邮件数量](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)。
    
若要了解有关直接转换迁移的详细信息, 请查看以下内容:
  
- [有关使用直接转换迁移将电子邮件迁移到 Office 365 的注意事项](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [执行电子邮件到 Office 365 的直接转换迁移](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>暂存迁移

暂存迁移是指您有几百或几个要迁移到 Office 365 的数千个邮箱, 需要花费一周或更长时间才能完成迁移, 而不需要任何高级混合迁移功能 (如共享的忙/闲日历信息)rmation。
  
暂存迁移非常适合需要花费更多时间将其邮箱迁移到 Office 365 的组织, 但仍计划在几个星期内完成迁移。 您可以在 "批处理" 中迁移邮箱, 这些邮箱使您能够控制在给定时间迁移邮箱的数量。 例如, 您可能在同一部门中对用户的邮箱进行批处理, 以确保同时移动它们。 或者, 您可能在最后一个批处理之前离开行政邮箱。 与直接转换迁移一样, 用户将需要重新创建其 Outlook 配置文件。
  
如果您正在考虑执行暂存迁移, 请考虑以下几点:
  
- Office 365 将需要通过 TCP 端口443在 Outlook 无处不在上连接到 Exchange 2007 服务器。
    
- 您需要具有可访问您的用户邮箱内容的本地管理员帐户, 请参阅。
    
- 需要在 Office 365 中使用的 Exchange 2007 接受域作为服务中的已验证域进行添加;
    
- 您需要创建一个 CSV 文件, 其中包含要在批处理中迁移的每个邮箱的完整名称和电子邮件地址。 您还需要为要迁移的每个邮箱包含一个新密码, 然后将其密码发送给每个用户。 用户首次登录到其新的 Office 365 邮箱时, 系统将提示用户更改密码;
    
- 在开始迁移批处理和开始完成阶段之间, office 365 将定期同步批次中包含的 office 365 和本地邮箱。 这样, 你就可以完成迁移, 而无需担心在你的内部部署邮箱中留下的电子邮件。
    
- 用户将收到 Office 365 帐户的新临时密码, 他们需要在首次登录邮箱时进行更改;
    
- 你将需要 Office 365 许可证, 其中包含你迁移的每个用户邮箱的 Exchange Online;
    
- 用户需要在各自的每台设备上设置一个新的 Outlook 配置文件, 并再次下载他们的电子邮件。 Outlook 将下载的电子邮件数量可能有所不同。 有关详细信息, 请参阅[更改要保持脱机的邮件数量](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)。
    
若要了解有关暂存迁移的详细信息, 请查看以下内容:
  
- [有关使用暂存迁移将电子邮件迁移到 Office 365 的注意事项](https://support.office.com/en-us/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [执行到 Office 365 的暂存迁移电子邮件](https://support.office.com/en-us/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>完全混合

完全混合迁移是指组织有多个数百个、多达数万个的邮箱, 并且您希望将其中的部分或全部移动到 Office 365。 由于这些迁移的时间通常较长, 混合迁移使其能够:
  
- 向本地用户显示 Office 365 中用户的忙/闲日历信息, 反之亦然。
    
- 查看包含内部部署和 Office 365 中的收件人的统一全局地址列表;
    
- 查看所有用户的完整 Outlook 收件人卡片, 而不管他们是在本地还是在 Office 365 中;
    
- 使用 TLS 和证书在本地 Exchange 服务器和 Office 365 之间进行安全的电子邮件通信;
    
- 将在内部部署 Exchange 服务器和 Office 365 之间发送的邮件视为内部邮件, 使其能够:
    
  - 通过面向内部邮件的传输和合规性代理进行正确评估和处理;
    
  - 绕过反垃圾邮件筛选器。
    
完全混合迁移最适用于希望在多个月或更多个月内保持混合配置的组织。 您将获得本部分前面列出的功能, 以及目录同步、更好的集成合规性功能, 以及使用在线邮箱移动将邮箱移动到 Office 365 的功能。 Office 365 将成为您的内部部署组织的扩展。
  
如果你想要执行完全混合迁移, 请考虑以下几点:
  
- 完全混合迁移不适合于所有类型的组织。 由于完全混合迁移的复杂性, 少于几百个邮箱的组织通常不会看到好处, 从而证明了设置一个好的工作量和成本所需的好处。 如果这听起来像您的组织, 我们强烈建议您改为考虑进行直接转换或暂存迁移。
    
- 您需要在 exchange 2007 组织中至少部署一个 exchange 2013 服务器, 以充当 "混合服务器"。 此服务器将代表你的 Exchange 2007 服务器与 Office 365 进行通信;
    
- Office 365 将需要通过 TCP 端口443使用 Outlook Anywhere 连接到 "混合服务器";
    
- 你需要在本地 Active directory 服务器和 Office 365 之间使用 Azure Active directory Connect (AADConnect) 设置目录同步;
    
- 用户将能够使用登录到本地网络时使用的用户名和密码登录到他们的 Office 365 邮箱 (需要使用密码同步和/或 Active directory 联合身份验证服务的 Azure Active Directory 连接);
    
- 你将需要 Office 365 许可证, 其中包含你迁移的每个用户邮箱的 Exchange Online;
    
- 用户无需在其大多数设备上设置新的 Outlook 配置文件 (一些较早的 Android 手机可能需要新的配置文件), 无需重新下载其电子邮件。
    
如果完全混合迁移听起来非常适合你, 请查看以下资源, 以帮助你进行迁移:
  
- [Exchange 部署助理](https://aka.ms/exdeploy)
    
- [Exchange Server 混合部署](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [混合配置向导](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [混合配置向导常见问题解答](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [混合部署先决条件](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>迁移到较新版本的 Exchange Server

虽然我们强烈相信你可以通过迁移到 Office 365 实现最佳价值和用户体验, 但我们还会了解某些组织需要将其电子邮件保存在本地。 这可能是由于法规要求, 保证数据不会存储在其他国家/地区的数据中心中, 等等。 如果您选择将您的电子邮件保留在本地, 则可以将 exchange 2007 环境迁移到 exchange 2010、exchange 2013 或 exchange 2016。
  
如果无法迁移到 Office 365, 建议您迁移到 Exchange 2016。 exchange 2016 包括早期版本的 Exchange 中附带的所有功能和改进, 并且与 office 365 提供的体验最为匹配 (尽管某些功能仅适用于 office 365)。 请查看以下内容中缺少的几个内容:
  
|**Exchange 发布**|**功能**|
|:-----|:-----|
|Exchange 2010  <br/> | 基于角色的访问控制 (没有 acl 的权限)  <br/>  Outlook Web Access 邮箱策略  <br/>  能够在组织之间共享忙/闲和代理日历  <br/> |
|Exchange 2013  <br/> | *Exchange 2010 中的功能和 .。。*  <br/>  简化的体系结构将服务器角色数减少到三个 (邮箱、客户端访问、边缘传输)  <br/>  数据丢失防护策略 (DLP), 可帮助防止敏感信息泄露  <br/>  显著改进的 Outlook Web App 体验  <br/> |
|Exchange 2016  <br/> | *Exchange 2013 中的功能和 .。。*  <br/>  将服务器角色进一步简化为仅限邮箱和边缘传输  <br/>  改进了 DLP 以及与 SharePoint 的集成  <br/>  改进的数据库恢复能力  <br/>  在线文档协作  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>应将哪种版本迁移到？

我们建议您先假设您将迁移到 Exchange 2016。 然后, 使用以下信息来确认您的假设或排除 Exchange 2016。 如果由于某种原因无法迁移到 Exchange 2016, 请执行与 exchange 2013 相同的过程, 依此类推。
  
|**方面**|**详细信息**|
|:-----|:-----|
|支持日期结束  <br/> | 与 exchange 2007 一样, 每个 exchange 版本都有自己的支持日期结尾:  <br/> **Exchange 2010** -1 月2020  <br/> **Exchange 2013** -4 月2023  <br/> **Exchange 2016** -10 月2025  <br/>  在较早的支持日期结束时, 您将需要执行另一个迁移。 2020年1月比你想像的事情大得多!  <br/> |
|Exchange 2010 和2013的迁移路径  <br/> |以下是迁移到 exchange 2010 或 exchange 2013 的一般阶段:  <br/> 将 exchange 2010 或2013安装到现有的 exchange 2007 组织中。若要 exchange 2010 或 2013, 请将邮箱和公用文件夹移动到 exchange 2010 或2013停止其余的 exchange 2007 服务器 |
|迁移到 Exchange 2016 的路径  <br/> |以下是迁移到 Exchange 2016 的一般阶段:  <br/> 将 exchange 2013 安装到现有的 exchange 2007 组织中。将邮箱和公用文件夹移动到 exchange 2013 将邮箱和公用文件夹移动到 exchange 2013 停止其余 exchange 2007 服务器将 Exchange 2016 安装到现有Exchange 2013 组织。 将邮箱、公用文件夹、服务和其他基础结构移动到 Exchange 2016 (不考虑顺序)。 停用其余的 Exchange 2013 [!NOTE]服务器 > > 从 Exchange 2013 迁移到 exchange 2016 非常简单。 这两个版本几乎具有相同的硬件要求。 这意味着, 这些版本是如此兼容的, 这意味着您可以重新生成为 Exchange 2013 购买的服务器并在其上安装 exchange 2016。 而且, 在联机邮箱移动时, 大多数用户将永远不会注意到其邮箱将移出服务器, 然后在您使用 Exchange 2016 重新生成后再返回。           |
|版本共存  <br/> | 迁移到以下项时:  <br/> **Exchange 2016**无法在包含 exchange 2007 服务器的组织中安装 Exchange 2016。 首先需要迁移到 Exchange 2010 或 2013 (强烈建议采用 exchange 2013), 删除所有 exchange 2007 服务器, 然后迁移到 Exchange 2016。  <br/> **exchange 2010 或 exchange 2013**您可以将 exchange 2010 或 exchange 2013 安装到现有的 Exchange 2007 组织中。 这使您可以安装一个或多个 Exchange 2010 或2013服务器, 并执行迁移。  <br/> |
|服务器硬件  <br/> | 服务器硬件要求已从 Exchange 2007 更改。 您需要确保要使用的硬件是兼容的。 您可以在此处查找有关每个版本的硬件要求的详细信息:  <br/> [Exchange 2016 系统要求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Exchange 2013 系统要求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/> [Exchange 2010 系统要求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx) <br/>  你会发现 Exchange 性能的显著改进以及较新的服务器中计算的计算能力和存储容量的增加, 可能需要较少的服务器来支持相同数量的邮箱。  <br/> |
|操作系统版本  <br/> | 每个版本支持的最低操作系统版本为:  <br/> **Exchange 2016**Windows Server 2012  <br/> **Exchange 2013**Windows Server 2008 R2 SP1  <br/> **Exchange 2010**Windows Server 2008 SP2  <br/>  您可以在 Exchange 可支持性[矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关操作系统支持的详细信息。  <br/> |
|Active Directory 林功能级别  <br/> | 每个版本支持的最小 Active Directory 林功能级别为:  <br/> **Exchange 2016**Windows Server 2008 R2 SP1  <br/> **Exchange 2013**Windows Server 2003  <br/> **Exchange 2010**Windows Server 2003  <br/>  可以在[Exchange 可支持性矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关林功能级别支持的详细信息。  <br/> |
|Office 客户端版本  <br/> | 每个版本的受支持的 Office 客户端版本最低为:  <br/> **Exchange 2016**Office 2010 (包含最新的更新)  <br/> **Exchange 2013**Office 2007 SP3  <br/> **Exchange 2010**Office 2003  <br/>  您可以在 Exchange 可支持性[矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关 Office 客户端支持的详细信息。  <br/> |
   
#### <a name="how-do-i-migrate"></a>如何迁移？

如果您已决定要将电子邮件保留在本地, 则可以使用以下资源来帮助您进行迁移:
  
- [Exchange 部署助理](https://aka.ms/exdeploy)
    
- Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)、 [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)的 Active Directory 架构更改
    
- Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)、 [2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx)的系统要求
    
- Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)、 [2010](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.141%29.aspx)的先决条件
    
## <a name="what-if-i-need-help"></a>如果我需要帮助, 该怎么办？

如果要迁移到 Office 365, 你可能有资格使用我们的 Microsoft FastTrack 服务。 FastTrack 提供了最佳实践、工具和资源, 使您可以尽可能无缝地迁移到 Office 365。 尤其可贵的是, 你将拥有真正的支持工程师, 它将引导你完成迁移, 从规划和设计一直到迁移你的最后一个邮箱。 若要了解有关 FastTrack 的详细信息, 请参阅[Microsoft FastTrack](https://fasttrack.microsoft.com/)。
  
如果您在迁移到 Office 365 期间遇到任何问题, 并且您不使用 FastTrack, 或迁移到较新版本的 Exchange Server, 我们将在这里为你提供帮助。 以下是您可以使用的一些资源:
  
- [技术社区](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [客户支持](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>相关主题

[帮助您升级 Office 2007 服务器和客户端的资源](upgrade-from-office-2007-servers-and-products.md)
  
[Office 退休组 (Microsoft 技术社区)](https://go.microsoft.com/fwlink/?linkid=842065)
  

