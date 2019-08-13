---
title: Exchange 2010 结束支持路线图
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 08/12/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 即将停止支持。 将此规划路线图用作准备升级到 Exchange Online 或部署到本地 Exchange Server 的更新版本的指南。
ms.openlocfilehash: a08ef80d2e6081adbc62b4c534ef185dcaff611f
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302745"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 结束支持路线图

在**2020 年1月 14**日, Exchange Server 2010 将达到支持的结束。 如果尚未开始从 Exchange 2010 迁移到 Office 365 或 Exchange 2016, 现在是开始规划的时间。

## <a name="what-does-end-of-support-mean"></a>支持终止的含义是什么？

与几乎所有 Microsoft 产品一样, Exchange Server 都具有支持生命周期, 在此期间我们提供了新的功能、缺陷修补程序、安全修补程序等。 此生命周期通常是从产品初始发布之日起10年的时间, 而此生命周期的结束时间也称为产品的支持终止的期限。
当 Exchange 2010 在2020上到达其支持结束时, Microsoft 将不再提供:

- 可能出现的问题的技术支持;
- 针对已发现且可能影响服务器的稳定性和可用性的问题的 Bug 修补程序。
- 已发现的漏洞安全修补程序以及可能会使服务器易受安全威胁的安全修补程序。
- 时区更新。

在此日期之后, 你的 Exchange 2010 安装将继续运行。 但是, 由于上面列出了所做的更改, 强烈建议您尽快从 Exchange 2010 迁移。

有关即将结束支持的 Office 2010 服务器的详细信息, 请参阅可[帮助您从 Office 2010 服务器和客户端进行升级的资源](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products)。

## <a name="what-are-my-options"></a>我的选项是什么？

随着 Exchange 2010 的支持终止, 这是浏览选项并准备迁移计划的良好时间。 可以执行下列操作：

- 完全迁移到 Office 365。 使用直接转换、最小混合或完全混合迁移迁移邮箱, 然后删除本地 Exchange 服务器和 Active Directory。
- 将 Exchange 2010 服务器迁移到本地服务器上的 Exchange 2016。

> [!IMPORTANT]
> 如果你的组织选择将邮箱迁移到 Office 365, 但打算就地保留 DirSync 或 Azure AD Connect, 以继续从本地 Active Directory 中管理用户帐户, 则需要在本地至少保留一个 Exchange server。 如果删除了最后一台 Exchange 服务器, 将无法更改 Exchange Online 中的 Exchange 收件人。 这是因为颁发机构的来源仍保留在本地 Active Directory 中, 需要进行更改。 在这种情况下, 您有以下几种选择:

- (**推荐**)如果可以将邮箱迁移到 Office 365 并将服务器升级到2020年1月14日, 请使用 Exchange 2010 连接到 Office 365 并迁移邮箱。 接下来, 将 Exchange 2010 迁移到 Exchange 2016 并取消所有剩余的 Exchange 2010 服务器。
- 如果您无法在2020年1月14日完成邮箱迁移和本地服务器升级, 请先将本地 Exchange 2010 服务器升级到 Exchange 2016, 然后使用 Exchange 2016 连接到 Office 365 并迁移邮箱。

> [!NOTE]
> 稍微复杂的是, 您还可以将邮箱迁移到 Office 365, 同时将您的本地 Exchange 2010 服务器迁移到 Exchange 2016。

若要避免停止对 Exchange Server 2010 的支持, 可以采用三种途径。

![Exchange Server 2010 升级路径](./media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

以下各节更详细地探讨了每个选项。

## <a name="migrate-to-office-365"></a>迁移到 Office 365

将电子邮件迁移到 Office 365 是帮助您停用 Exchange 2010 部署的最简单且最简单的选项。 通过迁移到 Office 365, 你可以从旧技术到一流功能的单一跃点, 如下所示:

- 合规性功能, 如保留策略、就地和诉讼保留、就地电子数据展示等;
- Microsoft 团队;
- Power BI;
- 重点收件箱;
- Delve 分析;

Office 365 还获取了新的功能和体验, 并且你的用户通常可以立即开始使用它们。 除了新功能之外, 您无需担心:

- 购买和维护硬件;
- 支付对服务器加热和冷却的费用;
- 及时了解安全性、产品和时区的修补程序;
- 维护存储和软件以支持合规性要求;
- 升级到新版本的 Exchange-始终在 Office 365 中的最新版本的 Exchange 上。

### <a name="how-should-i-migrate-to-office-365"></a>我应如何迁移到 Office 365？

根据你的组织, 你有几个可帮助你获取 Office 365 的选项。 选择迁移选项时, 需要考虑几个因素, 如需要移动的座位或邮箱数、您希望迁移的持续时间, 以及您是否需要在内部部署安装和 Office 365 之间实现无缝集成迁移。 此表显示了您的迁移选项和最重要的因素, 这些因素将决定您将使用哪种方法。

| **迁移选项**     | **组织大小** | **Duration**        |
|--------------------------|-----------------------|---------------------|
| 直接转换迁移        | 座位数少于150  | 一周或更少      |
| 最小混合迁移 | 座位数少于150  | 几个星期或更少 |
| 完全混合迁移    | 超过150的座位   | 几周或更多 |

以下各节提供了这些方法的概述。 请查看[迁移路径](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27), 以了解每个方法的详细信息。

### <a name="cutover-migration"></a>直接转换迁移

直接转换迁移是指在预先选择的日期和时间, 将所有邮箱、通讯组、联系人等迁移到 Office 365;完成后, 你将关闭本地 Exchange 服务器, 并以独占方式开始使用 Office 365。

对于没有很多邮箱的小型组织来说, 直接转换迁移方法非常有用, 要快速获取 Office 365, 并且不希望处理其他方法中的一些复杂性。 但它也受到限制, 因为它应在一周或更短的时间内完成, 因为它要求用户重新配置其 Outlook 配置文件。 虽然直接转换迁移最多可以处理2000个邮箱, 但我们强烈建议您使用此方法最多迁移150个邮箱。 如果您尝试迁移超过150个邮箱, 则可能会在你的截止时间之后停止转移所有邮箱, 并且 IT 支持人员可能会在帮助用户重新配置 Outlook 时遇到大量的情况。

如果你正在考虑进行直接转换迁移, 请考虑以下几点:

- Office 365 将需要通过 TCP 端口443在 Outlook 无处不在上连接到 Exchange 2010 服务器。
- 所有内部部署邮箱都将移至 Office 365;
- 您需要具有可访问您的用户邮箱内容的本地管理员帐户, 请参阅。
- 需要在 Office 365 中使用的 Exchange 2010 接受域作为服务中的已验证域进行添加;
- 在开始迁移和开始完成阶段之间的时间内, Office 365 将定期同步 Office 365 和本地邮箱。 这样, 你就可以完成迁移, 而无需担心在你的内部部署邮箱中留下的电子邮件。
- 用户将收到 Office 365 帐户的新的临时密码, 他们需要在首次登录邮箱时进行更改;
- 你将需要 Office 365 许可证, 其中包含你迁移的每个用户邮箱的 Exchange Online;
- 用户需要在各自的每台设备上设置一个新的 Outlook 配置文件, 并再次下载他们的电子邮件。 Outlook 将下载的电子邮件数量可能有所不同。 有关详细信息, 请参阅[更改要保持脱机的邮件数量](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1)。

若要了解有关直接转换迁移的详细信息, 请查看以下内容:

- [您需要了解的有关直接转换电子邮件迁移到 Office 365 的相关信息](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [执行电子邮件到 Office 365 的直接转换迁移](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>最小混合迁移

最小混合或快速迁移是指您有几百个要迁移到 Office 365 的邮箱, 可以在几个星期内完成迁移, 而不需要任何高级混合迁移功能 (如共享的忙/闲日历)信息.

最小混合迁移非常适合需要花费更长时间将其邮箱迁移到 Office 365 的组织, 但仍计划在几个星期内完成迁移。 你可以获得更高级完全混合迁移的一些好处, 而不是很复杂。 您可以控制在给定时间迁移邮箱的数量, 以及对邮箱进行迁移的时间。将使用本地帐户的用户名和密码创建 Office 365 邮箱;与直接转换迁移不同, 用户不需要重新创建其 Outlook 配置文件。

如果您正在考虑执行最少混合迁移, 请考虑以下几点:

- 你将需要在内部部署 Active Directory 服务器和 Office 365 之间执行一次性目录同步;
- 用户将能够使用在迁移邮箱时使用的用户名和密码登录到他们的 Office 365 邮箱;
- 你将需要 Office 365 许可证, 其中包含你迁移的每个用户邮箱的 Exchange Online;
- 用户无需在其大多数设备上设置新的 Outlook 配置文件 (一些较早的 Android 手机可能需要新的配置文件), 无需重新下载其电子邮件。

若要了解有关最简单的混合迁移的详细信息, 请参阅[使用最少混合以将 Exchange 邮箱快速迁移到 Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### <a name="full-hybrid"></a>完全混合

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

- 完全混合迁移不适合于所有类型的组织。 由于完全混合迁移的复杂性, 少于几百个邮箱的组织通常不会看到好处, 从而证明了设置一个好的工作量和成本所需的好处。 如果这听起来像是你的组织, 强烈建议你改为考虑转换或最少的混合迁移。
- 你需要在本地 Active Directory 服务器和 Office 365 之间使用 Azure Active Directory Connect (AADConnect) 设置目录同步;
- 用户将能够使用登录到本地网络时使用的用户名和密码登录到他们的 Office 365 邮箱 (需要使用密码同步和/或 Active Directory 联合身份验证服务的 Azure Active Directory 连接);
- 你将需要 Office 365 许可证, 其中包含你迁移的每个用户邮箱的 Exchange Online;
- 用户无需在其大多数设备上设置新的 Outlook 配置文件 (一些较早的 Android 手机可能需要新的配置文件), 无需重新下载其电子邮件。

> [!IMPORTANT]
> 如果你的组织选择将邮箱迁移到 Office 365, 但打算就地保留 DirSync 或 Azure AD Connect, 以继续从本地 Active Directory 中管理用户帐户, 则需要在本地至少保留一个 Exchange server。 如果删除了最后一台 Exchange 服务器, 将无法更改 Exchange Online 中的 Exchange 收件人。 这是因为颁发机构的来源仍保留在本地 Active Directory 中, 需要进行更改。

如果完全混合迁移听起来非常适合你, 请查看以下资源, 以帮助你进行迁移:

- [Exchange 部署助理](https://aka.ms/exdeploy)
- [Exchange Server 混合部署](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
- [混合配置向导](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
- [混合配置向导常见问题解答](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
- [混合部署先决条件](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>升级到本地 Exchange Server 的较新版本

虽然我们强烈认为您可以通过完全迁移到 Office 365 实现最佳价值和用户体验, 但我们还了解一些组织需要在本地保留一些 Exchange 服务器。 这可能是因为法规要求, 以保证数据不会存储在位于其他国家/地区的数据中心中, 也可能是因为您在云中无法满足唯一的设置或要求, 也可能只是需要 Exchange 才能管理云邮箱, 因为您仍在本地使用 Active Directory。 在选择或需要保留 Exchange 本地的任何情况下, 应确保将 Exchange 2010 环境升级到至少 Exchange 2013 或 Exchange 2016, 并在支持日期结束之前删除 exchange 2010。

为了获得最佳体验, 我们建议您将其余的本地环境升级到 Exchange 2016。 如果要直接从 Exchange Server 2010 转到 Exchange Server 2016, 则无需安装 Exchange Server 2013。

Exchange 2016 包括早期版本的 Exchange 中附带的所有功能和改进, 并且与 Office 365 提供的体验最为匹配 (尽管某些功能仅适用于 Office 365)。 请查看以下内容中缺少的几个内容:

| **Exchange 发布**                     | **功能**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | 简化的体系结构将服务器角色数减少到三个 (邮箱、客户端访问、边缘传输)                                                                                                                                        |
|                                          | 数据丢失防护策略 (DLP), 可帮助防止敏感信息泄露                                                                                                                                                                |
|                                          | 显著改进的 Outlook Web App 体验                                                                                                                                                                                                    |
| Exchange 2016                            | *Exchange 2013 中的功能和 .。。*                                                                                                                                                                                                                   |
|                                          | 将服务器角色进一步简化为仅限邮箱和边缘传输                                                                                                                                                                                   |
|                                          | 改进了 DLP 以及与 SharePoint 的集成                                                                                                                                                                                                  |
|                                          | 改进的数据库恢复能力                                                                                                                                                                                                                         |
|                                          | 在线文档协作                                                                                                                                                                                                                        |

| **方面**                        | **详细信息**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 支持日期结束                     | 与 Exchange 2010 一样, 每个 Exchange 版本都有自己的支持日期结尾:                                                                                                                                                                        |
|                                          | **Exchange 2013** -4 月2023                                                                                                                                                                                                                       |
|                                          | **Exchange 2016** -10 月2025                                                                                                                                                                                                                     |
|                                          | 在较早的支持日期结束时, 您将需要执行另一个迁移。 4月2023比你想像的要大得多!                                                                                                                 |
| 迁移到 Exchange 2013 或2016的路径  | 无论您选择 Exchange 2013 还是 Exchange 2016, 从 Exchange 2010 到较新版本的迁移路径都是相同的:                                                                                                                              |
|                                          | 将 Exchange 2013 或2016安装到现有的 Exchange 2010 组织中。若要 Exchange 2013 或 2016, 请将邮箱和公用文件夹移动到 Exchange 2013 或2016停止其余的 Exchange 2010 服务器  |
| 版本共存                      | 迁移到 Exchange 2013 或 Exchange 2016 时, 您可以将其中一个版本安装到现有的 Exchange 2010 组织中。 这使您可以安装一个或多个 Exchange 2013 或 Exchange 2016 服务器并执行迁移。             |
| 服务器硬件                          | 服务器硬件要求已从 Exchange 2010 更改。 您需要确保要使用的硬件是兼容的。 您可以在此处查找有关每个版本的硬件要求的详细信息:                                      |
|                                          | [Exchange 2016 系统要求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Exchange 2013 系统要求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | 你会发现 Exchange 性能的显著改进以及较新的服务器中计算的计算能力和存储容量的增加, 可能需要较少的服务器来支持相同数量的邮箱。                       |
| 操作系统版本                 | 每个版本支持的最低操作系统版本为:                                                                                                                                                                                |
|                                          | **Exchange 2016**Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013**Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | 您可以在 Exchange 可支持性[矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关操作系统支持的详细信息。                                                                        |
| Active Directory 林功能级别 | 每个版本支持的最小 Active Directory 林功能级别为:                                                                                                                                                                |
|                                          | **Exchange 2016**Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013**Windows Server 2003                                                                                                                                                                                                                |
|                                          | 可以在[Exchange 可支持性矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关林功能级别支持的详细信息。                                                                 |
| Office 客户端版本                   | 每个版本的受支持的 Office 客户端版本最低为:                                                                                                                                                                                   |
|                                          | **Exchange 2016**Office 2010 (包含最新的更新)                                                                                                                                                                                              |
|                                          | **Exchange 2013**Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | 您可以在 Exchange 可支持性[矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关 Office 客户端支持的详细信息。                                                                           |

您可以使用以下资源来帮助您进行迁移:

- [Exchange 部署助理](https://aka.ms/exdeploy)
- Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)的 Active Directory 架构更改
- Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)的系统要求
- Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx)、 [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)的先决条件

## <a name="what-if-i-need-help"></a>如果我需要帮助, 该怎么办？

如果要迁移到 Office 365, 你可能有资格使用我们的 Microsoft FastTrack 服务。 FastTrack 提供了最佳实践、工具和资源, 使您可以尽可能无缝地迁移到 Office 365。 尤其可贵的是, 你将拥有真正的支持工程师, 它将引导你完成迁移, 从规划和设计一直到迁移你的最后一个邮箱。 若要了解有关 FastTrack 的详细信息, 请参阅[Microsoft FastTrack](https://fasttrack.microsoft.com/)。

如果您在迁移到 Office 365 期间遇到任何问题, 并且您不使用 FastTrack, 或迁移到较新版本的 Exchange Server, 我们将在这里为你提供帮助。 以下是您可以使用的一些资源:

- [技术社区](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
- [客户支持](https://support.microsoft.com/en-us/gp/support-options-for-business)

## <a name="related-topics"></a>相关主题

[可帮助您从 Office 2010 服务器和客户端进行升级的资源](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Office 退休组 (Microsoft 技术社区)](https://go.microsoft.com/fwlink/?linkid=842065)
