---
title: Exchange 2010 末尾的支持路线图
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 已接近结束的支持。使用本规划指南作为指南准备升级到 Exchange Online 或 Exchange Server 内部部署的更新版本。
ms.openlocfilehash: e655edcc38723acd622fc6abc62a00d3f3e36738
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915187"
---
# <a name="exchange-2010-end-of-support-roadmap"></a><span data-ttu-id="d80a8-104">Exchange 2010 末尾的支持路线图</span><span class="sxs-lookup"><span data-stu-id="d80a8-104">Exchange 2010 end of support roadmap</span></span>

<span data-ttu-id="d80a8-p102">**于 2020 年 1 月 14 日**，在 Exchange Server 2010 将到达结束的支持。如果您没有已开始迁移到 Office 365 的 Exchange 2010 或 Exchange 2016，现在是开始规划过程的时间。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p102">On **January 14, 2020**, Exchange Server 2010 will reach end of support. If you haven't already begun your migration from Exchange 2010 to Office 365 or Exchange 2016, now's the time to start your planning.</span></span> 
  
## <a name="what-does-end-of-support-mean"></a><span data-ttu-id="d80a8-107">支持平均值内容的末尾？</span><span class="sxs-lookup"><span data-stu-id="d80a8-107">What does end of support mean?</span></span>

<span data-ttu-id="d80a8-p103">Exchange Server，几乎所有 Microsoft 产品，如具有支持生命周期期间我们提供的新功能、 bug 修复、 安全修补程序，等等。此生命周期通常会持续 10 年中的产品的初始发布日期和此生命周期的结束称为产品的结束的支持。Exchange 2010 年 1 月 14 2020年支持的到期时将不再提供 Microsoft:</span><span class="sxs-lookup"><span data-stu-id="d80a8-p103">Exchange Server, like almost all Microsoft products, has a support lifecycle during which we provide new features, bug fixes, security fixes, and so on. This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support. When Exchange 2010 reaches its end of support on January 14, 2020, Microsoft will no longer provide:</span></span>
  
- <span data-ttu-id="d80a8-111">可能出现; 的问题的技术支持</span><span class="sxs-lookup"><span data-stu-id="d80a8-111">Technical support for problems that may occur;</span></span>
    
- <span data-ttu-id="d80a8-112">Bug 修复的问题的发现以及可能影响的稳定性和可用性的服务器。</span><span class="sxs-lookup"><span data-stu-id="d80a8-112">Bug fixes for issues that are discovered and that may impact the stability and usability of the server;</span></span>
    
- <span data-ttu-id="d80a8-113">安全漏洞的发现和可能使该服务器安全轻易; 地受到修补程序</span><span class="sxs-lookup"><span data-stu-id="d80a8-113">Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches;</span></span>
    
- <span data-ttu-id="d80a8-114">更新所在的时区。</span><span class="sxs-lookup"><span data-stu-id="d80a8-114">Time zone updates.</span></span>
    
<span data-ttu-id="d80a8-p104">Exchange 2010 的安装将继续此日期之后运行。但是，由于上面列出的更改，强烈建议您迁移从 Exchange 2010 尽快。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p104">Your installation of Exchange 2010 will continue to run after this date. However, because of the changes listed above, we strongly recommend that you migrate from Exchange 2010 as soon as possible.</span></span>
  
<span data-ttu-id="d80a8-117">有关接近结束的支持的 Office 2010 服务器的详细信息，请参阅[资源以帮助您升级从 Office 2010 的服务器和客户端](upgrade-from-office-2010-servers-and-products.md)。</span><span class="sxs-lookup"><span data-stu-id="d80a8-117">For more information about Office 2010 servers nearing the end of support, see [Resources to help you upgrade from Office 2010 servers and clients](upgrade-from-office-2010-servers-and-products.md).</span></span>
  
## <a name="what-are-my-options"></a><span data-ttu-id="d80a8-118">我的选项是什么？</span><span class="sxs-lookup"><span data-stu-id="d80a8-118">What are my options?</span></span>

<span data-ttu-id="d80a8-p105">与 Exchange 2010 达到其结束，这是支持的一个极好浏览您的选项和准备迁移计划。您可以：</span><span class="sxs-lookup"><span data-stu-id="d80a8-p105">With Exchange 2010 reaching its end of support, this is a great time to explore your options and prepare a migration plan. You can:</span></span>
  
- <span data-ttu-id="d80a8-121">迁移到 Office 365 使用直接转换、 express 或混合迁移;</span><span class="sxs-lookup"><span data-stu-id="d80a8-121">Migrate to Office 365 using cutover, express, or hybrid migration;</span></span> 
    
- <span data-ttu-id="d80a8-122">将 Exchange 2010 服务器迁移到新版本的 Exchange 本地服务器上。</span><span class="sxs-lookup"><span data-stu-id="d80a8-122">Migrate your Exchange 2010 servers to a newer version of Exchange on your on-premises servers.</span></span>
    
<span data-ttu-id="d80a8-123">以下各节浏览更多详细信息中的每个选项。</span><span class="sxs-lookup"><span data-stu-id="d80a8-123">The following sections explore each option in more detail.</span></span>
  
### <a name="migrate-to-office-365"></a><span data-ttu-id="d80a8-124">迁移到 Office 365</span><span class="sxs-lookup"><span data-stu-id="d80a8-124">Migrate to Office 365</span></span>

<span data-ttu-id="d80a8-p106">您的电子邮件迁移到 Office 365 是您最佳和最简单的选项可帮助您停用您的 Exchange 2010 部署。使用到 Office 365 迁移，您可以像进行单个从旧技术跃点先进的功能：</span><span class="sxs-lookup"><span data-stu-id="d80a8-p106">Migrating your email to Office 365 is your best and simplest option to help you retire your Exchange 2010 deployment. With a migration to Office 365, you can make a single hop from old technology to state of the art features, like:</span></span>
  
- <span data-ttu-id="d80a8-127">合规性功能，如保留策略就地和诉讼保留，就地电子数据展示，和更多;</span><span class="sxs-lookup"><span data-stu-id="d80a8-127">Compliance capabilities such as Retention Policies, In-Place and Litigation Hold, in-place eDiscovery, and more;</span></span>
    
- <span data-ttu-id="d80a8-128">Microsoft 团队;</span><span class="sxs-lookup"><span data-stu-id="d80a8-128">Microsoft Teams;</span></span>
    
- <span data-ttu-id="d80a8-129">Power BI;</span><span class="sxs-lookup"><span data-stu-id="d80a8-129">Power BI;</span></span>
    
- <span data-ttu-id="d80a8-130">重点收件箱;</span><span class="sxs-lookup"><span data-stu-id="d80a8-130">Focused Inbox;</span></span>
    
- <span data-ttu-id="d80a8-131">深入分析;</span><span class="sxs-lookup"><span data-stu-id="d80a8-131">Delve Analytics;</span></span>
    
- <span data-ttu-id="d80a8-132">REST Api 以编程方式访问电子邮件、 日历、 联系人和等等。</span><span class="sxs-lookup"><span data-stu-id="d80a8-132">REST APIs for programmatic access to email, calendars, contacts, and so on.</span></span>
    
<span data-ttu-id="d80a8-p107">Office 365 还获取新功能和体验第一个和您和您的用户可以通常开始立即使用它们。除了新功能，您不必担心：</span><span class="sxs-lookup"><span data-stu-id="d80a8-p107">Office 365 also gets new features and experiences first and you and your users can usually start using them right away. In addition to new features, you won't have to worry about:</span></span>
  
- <span data-ttu-id="d80a8-135">购买和维护硬件;</span><span class="sxs-lookup"><span data-stu-id="d80a8-135">Purchasing and maintaining hardware;</span></span>
    
- <span data-ttu-id="d80a8-136">用于供暖和制冷服务器; 的情况</span><span class="sxs-lookup"><span data-stu-id="d80a8-136">Paying for heating and cooling of your servers;</span></span>
    
- <span data-ttu-id="d80a8-137">保持最新的安全、 产品和时区修复;</span><span class="sxs-lookup"><span data-stu-id="d80a8-137">Keeping up to date on security, product, and time zone fixes;</span></span>
    
- <span data-ttu-id="d80a8-138">维护存储和软件来支持合规性要求;</span><span class="sxs-lookup"><span data-stu-id="d80a8-138">Maintaining storage and software to support compliance requirements;</span></span>
    
- <span data-ttu-id="d80a8-139">升级到新版本的 Exchange-您始终在 Office 365 中 Exchange 的最新版本上。</span><span class="sxs-lookup"><span data-stu-id="d80a8-139">Upgrading to a new version of Exchange - you're always on the latest version of Exchange in Office 365.</span></span>
    
#### <a name="how-should-i-migrate-to-office-365"></a><span data-ttu-id="d80a8-140">如何应将迁移到 Office 365？</span><span class="sxs-lookup"><span data-stu-id="d80a8-140">How should I migrate to Office 365?</span></span>

<span data-ttu-id="d80a8-p108">根据您的组织，您必须将帮助您到 Office 365 的几个选项。时选择的迁移选项，您需要考虑的一些像数座位或需要移动的邮箱、 长要迁移到最后一个，以及是否需要您的本地安装和过程中的 Office 365 之间进行无缝集成迁移。此表显示了迁移选项和最重要的因素将确定您将使用哪种方法。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p108">Depending on your organization, you have a few options that'll help you get to Office 365. When choosing a migration option, you need to consider a few things like the number of seats or mailboxes you need to move, how long you want the migration to last, and whether you need a seamless integration between your on-premises installation and Office 365 during the migration. This table shows your migration options and the most important factors that'll determine which method you'll use.</span></span>
  
|<span data-ttu-id="d80a8-144">**迁移选项**</span><span class="sxs-lookup"><span data-stu-id="d80a8-144">**Migration option**</span></span>|<span data-ttu-id="d80a8-145">**组织的规模**</span><span class="sxs-lookup"><span data-stu-id="d80a8-145">**Organization size**</span></span>|<span data-ttu-id="d80a8-146">**Duration**</span><span class="sxs-lookup"><span data-stu-id="d80a8-146">**Duration**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d80a8-147">直接转换迁移</span><span class="sxs-lookup"><span data-stu-id="d80a8-147">Cutover migration</span></span>  <br/> |<span data-ttu-id="d80a8-148">少于 150 座位</span><span class="sxs-lookup"><span data-stu-id="d80a8-148">Fewer than 150 seats</span></span>  <br/> |<span data-ttu-id="d80a8-149">每周或更少</span><span class="sxs-lookup"><span data-stu-id="d80a8-149">A week or less</span></span>  <br/> |
|<span data-ttu-id="d80a8-150">Express 迁移</span><span class="sxs-lookup"><span data-stu-id="d80a8-150">Express migration</span></span>  <br/> |<span data-ttu-id="d80a8-151">少于 150 座位</span><span class="sxs-lookup"><span data-stu-id="d80a8-151">Fewer than 150 seats</span></span>  <br/> |<span data-ttu-id="d80a8-152">几周或更少</span><span class="sxs-lookup"><span data-stu-id="d80a8-152">A couple weeks or less</span></span>  <br/> |
|<span data-ttu-id="d80a8-153">完整的混合迁移</span><span class="sxs-lookup"><span data-stu-id="d80a8-153">Full hybrid migration</span></span>  <br/> |<span data-ttu-id="d80a8-154">多个 150 座位</span><span class="sxs-lookup"><span data-stu-id="d80a8-154">More than 150 seats</span></span>  <br/> |<span data-ttu-id="d80a8-155">几周或更多</span><span class="sxs-lookup"><span data-stu-id="d80a8-155">A few weeks or more</span></span>  <br/> |
   
<span data-ttu-id="d80a8-p109">以下各节提供了这些方法的概述。签出[Decide 迁移路径上的](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27)，若要了解每种方法的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p109">The following sections give you an overview of these methods. Check out [Decide on a migration path](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) to learn the details of each method.</span></span> 
  
#### <a name="cutover-migration"></a><span data-ttu-id="d80a8-158">直接转换迁移</span><span class="sxs-lookup"><span data-stu-id="d80a8-158">Cutover migration</span></span>

<span data-ttu-id="d80a8-159">直接转换迁移是一个位置，在预选的日期和时间，您将迁移所有邮箱、 通讯组、 联系人和等等，到 Office 365;当您已完成，您将关闭内部部署 Exchange 服务器并启动以独占方式使用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="d80a8-159">A cutover migration is one where, at a pre-selected date and time, you'll migrate all your mailboxes, distribution groups, contacts, and so on, to Office 365; when you've finished, you'll shut down your on-premises Exchange servers and start using Office 365 exclusively.</span></span>
  
<span data-ttu-id="d80a8-p110">直接转换迁移方法非常，没有很多个邮箱的小型组织要迅速到 Office 365，并无需处理一些其他方法的复杂性。但它的也有一些限制因为它应小于或等于一周中已完成，因为它要求用户重新配置其 Outlook 配置文件。时直接转换迁移可以处理最多 2,000 个邮箱，我们强烈建议使用此方法迁移 150 邮箱的最大值。如果您尝试迁移 150 多个邮箱、 无法用完之前您截止日期，传输所有邮箱的时间和 IT 支持人员可能会收到大量帮助用户重新配置 Outlook。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p110">The cutover migration method is great for small organizations that don't have very many mailboxes, want to get to Office 365 quickly, and don't want to deal with some of the complexities of the other methods. But it's also somewhat limited because it should be completed in a week or less and because it requires users to reconfigure their Outlook profiles. While cutover migration can handle up to 2,000 mailboxes, we strongly recommend you migrate a maximum of 150 mailboxes with this method. If you try to migrate more than 150 mailboxes, you could run out of time to transfer all the mailboxes before your deadline, and your IT support staff may get overwhelmed helping users reconfigure Outlook.</span></span>
  
<span data-ttu-id="d80a8-164">如果您正在考虑执行直接转换迁移，下面是需要考虑的几件事，请考虑：</span><span class="sxs-lookup"><span data-stu-id="d80a8-164">If you're thinking about doing a cutover migration, here are a few things to think consider:</span></span>
  
- <span data-ttu-id="d80a8-165">Office 365 需要连接到 Exchange 2010 服务器通过 TCP 端口 443; 使用 Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="d80a8-165">Office 365 will need to connect to your Exchange 2010 servers using Outlook Anywhere over TCP port 443;</span></span>
    
- <span data-ttu-id="d80a8-166">所有内部部署邮箱将被移动到 Office 365;</span><span class="sxs-lookup"><span data-stu-id="d80a8-166">All on-premises mailboxes will be moved to Office 365;</span></span>
    
- <span data-ttu-id="d80a8-167">您将需要有权读取用户邮箱; 的内容的本地管理员帐户</span><span class="sxs-lookup"><span data-stu-id="d80a8-167">You'll need an on-premises administrator account that has access to read the contents of your users' mailboxes;</span></span>
    
- <span data-ttu-id="d80a8-168">Exchange 2010 接受您想要使用 Office 365 需要中添加为服务; 中的已验证域的域</span><span class="sxs-lookup"><span data-stu-id="d80a8-168">The Exchange 2010 accepted domains that you want to use in Office 365 need to be added as verified domains in the service;</span></span>
    
- <span data-ttu-id="d80a8-p111">在开始迁移之间的时间和开始完成阶段时，Office 365 将定期同步的 Office 365 和内部部署邮箱。这样可以完成迁移，而不必担心留在您的内部部署邮箱; 电子邮件</span><span class="sxs-lookup"><span data-stu-id="d80a8-p111">Between the time you start the migration and when you begin the completion phase, Office 365 will periodically synchronize the Office 365 and on-premises mailboxes. This lets you complete the migration without worrying about email being left behind in your on-premises mailboxes;</span></span>
    
- <span data-ttu-id="d80a8-171">用户将收到新临时密码他们将需要更改首次; 登录到其邮箱时其 Office 365 帐户</span><span class="sxs-lookup"><span data-stu-id="d80a8-171">Users will receive new temporary passwords for their Office 365 account that they'll need to change when they log in to their mailboxes for the first time;</span></span>
    
- <span data-ttu-id="d80a8-172">您将需要为每个用户邮箱迁移; 包括 Exchange Online 的 Office 365 许可证</span><span class="sxs-lookup"><span data-stu-id="d80a8-172">You'll need an Office 365 license that includes Exchange Online for each user mailbox you migrate;</span></span>
    
- <span data-ttu-id="d80a8-p112">用户将需要设置新的 Outlook 配置文件在每台其设备上，并再次下载其电子邮件。Outlook 将下载的电子邮件量可能各不相同。有关详细信息，了解一下[更改多少邮件的保留脱机](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p112">Users will need to set up a new Outlook profile on each of their devices and download their email again. The amount of email that Outlook will download can vary. For more information, take a look at [Change how much mail to keep offline](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).</span></span>
    
<span data-ttu-id="d80a8-176">若要了解有关直接转换迁移的详细信息，看看：</span><span class="sxs-lookup"><span data-stu-id="d80a8-176">To learn more about cutover migration, take a look at:</span></span>
  
- [<span data-ttu-id="d80a8-177">有关使用直接转换迁移将电子邮件迁移到 Office 365 的注意事项</span><span class="sxs-lookup"><span data-stu-id="d80a8-177">What you need to know about a cutover email migration to Office 365</span></span>](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [<span data-ttu-id="d80a8-178">执行直接转换迁移到 Office 365 的电子邮件</span><span class="sxs-lookup"><span data-stu-id="d80a8-178">Perform a cutover migration of email to Office 365</span></span>](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="express-migration"></a><span data-ttu-id="d80a8-179">Express 迁移</span><span class="sxs-lookup"><span data-stu-id="d80a8-179">Express migration</span></span>

<span data-ttu-id="d80a8-180">Express 迁移是一个包含您想要迁移到 Office 365，可以完成的几周之内迁移，而且不需要任何共享忙/闲日历信息之类的高级的混合迁移功能的几个几百个邮箱。</span><span class="sxs-lookup"><span data-stu-id="d80a8-180">An express migration is one where you have a few hundred mailboxes that you want to migrate to Office 365, can complete the migration within a couple weeks, and don't need any of the advanced hybrid migration features like shared Free/Busy calendar information.</span></span>
  
<span data-ttu-id="d80a8-p113">Express 迁移非常适合于需要更多时间，以将其邮箱迁移到 Office 365 中，但仍计划完成迁移的几周之内的组织。获取不包含许多复杂性更高级的完整混合迁移的一些好处。您可以控制多少，以及哪些，邮箱在给定时间; 迁移Office 365 邮箱将创建具有用户名和密码的其内部部署帐户;和直接转换迁移，与您的用户不需要重新创建其 Outlook 配置文件。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p113">Express migration is great for organizations that need to take more time to migrate their mailboxes to Office 365, but still plan to complete the migration within a couple weeks. You get some benefits of the more advanced full hybrid migration without many of the complexities. You can control how many, and which, mailboxes are migrated at a given time; Office 365 mailboxes will be created with the username and passwords of their on-premises accounts; and, unlike cutover migrations, your users won't need to recreate their Outlook profiles.</span></span>
  
<span data-ttu-id="d80a8-184">如果您正在考虑执行暂存的迁移，下面是要考虑的几个事项：</span><span class="sxs-lookup"><span data-stu-id="d80a8-184">If you're thinking about doing a staged migration, here are a few things to consider:</span></span>
  
- <span data-ttu-id="d80a8-185">Office 365 需要连接到 Exchange 2010 服务器通过 TCP 端口 443; 使用 Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="d80a8-185">Office 365 will need to connect to your Exchange 2010 servers using Outlook Anywhere over TCP port 443;</span></span>
    
- <span data-ttu-id="d80a8-186">您需要执行您的本地 Active Directory 服务器与 Office 365; 之间一次性目录同步</span><span class="sxs-lookup"><span data-stu-id="d80a8-186">You'll need to perform a one-time directory synchronization between your on-premises Active Directory servers and Office 365;</span></span>
    
- <span data-ttu-id="d80a8-187">用户将能够登录到他们使用的相同的用户名和密码时迁移其邮箱; 它们所使用的 Office 365 邮箱</span><span class="sxs-lookup"><span data-stu-id="d80a8-187">Users will be able to log in to their Office 365 mailbox using the same username and password they were using when their mailbox was migrated;</span></span>
    
- <span data-ttu-id="d80a8-188">您将需要为每个用户邮箱迁移; 包括 Exchange Online 的 Office 365 许可证</span><span class="sxs-lookup"><span data-stu-id="d80a8-188">You'll need an Office 365 license that includes Exchange Online for each user mailbox you migrate;</span></span>
    
- <span data-ttu-id="d80a8-189">用户不需要在他们的设备 （某些旧的 Android 电话可能需要一个新的配置文件） 的最新的 Outlook 配置文件设置，并不需要重新下载其电子邮件。</span><span class="sxs-lookup"><span data-stu-id="d80a8-189">Users don't need to set up a new Outlook profile on most of their devices (some older Android phones might need a new profile) and won't need to re-download their email.</span></span>
    
<span data-ttu-id="d80a8-190">若要了解有关分阶段迁移的详细信息，看看[使用最少混合快速迁移到 Office 365 的 Exchange 邮箱](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)</span><span class="sxs-lookup"><span data-stu-id="d80a8-190">To learn more about staged migration, take a look at [Use Minimal Hybrid to quickly migrate Exchange mailboxes to Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)</span></span>
  
#### <a name="full-hybrid"></a><span data-ttu-id="d80a8-191">完整的混合</span><span class="sxs-lookup"><span data-stu-id="d80a8-191">Full hybrid</span></span>

<span data-ttu-id="d80a8-p114">一个其中贵组织拥有许多百，最多为数万，邮箱和您要移动到 Office 365 的部分或所有这些完整混合迁移。由于这些迁移通常长期，混合迁移使可能：</span><span class="sxs-lookup"><span data-stu-id="d80a8-p114">A full hybrid migration is one where your organization has many hundreds, up to tens of thousands, of mailboxes and you want to move some or all of them to Office 365. Because these migrations are typically longer-term, hybrid migrations make it possible to:</span></span>
  
- <span data-ttu-id="d80a8-194">Office 365 中的用户的忙/闲日历信息显示在本地用户，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="d80a8-194">Show on-premises users the free/busy calendar information for users in Office 365, and vice versa;</span></span>
    
- <span data-ttu-id="d80a8-195">请参阅包含在本地和 Office 365; 中的收件人的统一全局地址列表</span><span class="sxs-lookup"><span data-stu-id="d80a8-195">See a unified global address list that contains recipients in both on-premises and Office 365;</span></span>
    
- <span data-ttu-id="d80a8-196">查看所有用户，而不考虑它们是否在本地或 Office 365; 中的完整 Outlook 收件人卡</span><span class="sxs-lookup"><span data-stu-id="d80a8-196">View full Outlook recipient cards for all users, regardless of whether they're on-premises or in Office 365;</span></span>
    
- <span data-ttu-id="d80a8-197">内部部署 Exchange 服务器与 Office 365 使用 TLS 和证书; 之间的安全电子邮件通信</span><span class="sxs-lookup"><span data-stu-id="d80a8-197">Secure email communication between on-premises Exchange servers and Office 365 using TLS and certificates;</span></span>
    
- <span data-ttu-id="d80a8-198">将内部部署 Exchange 服务器和 Office 365 之间发送为内部，从而使他们的消息：</span><span class="sxs-lookup"><span data-stu-id="d80a8-198">Treat messages sent between on-premises Exchange servers and Office 365 as internal, enabling them to:</span></span>
    
  - <span data-ttu-id="d80a8-199">正确进行评估和处理设定; 内部消息的传输和合规性代理</span><span class="sxs-lookup"><span data-stu-id="d80a8-199">Be properly evaluated and processed by transport and compliance agents targeting internal messages;</span></span>
    
  - <span data-ttu-id="d80a8-200">绕过反垃圾邮件筛选器。</span><span class="sxs-lookup"><span data-stu-id="d80a8-200">Bypass anti-spam filters.</span></span>
    
<span data-ttu-id="d80a8-p115">完整的混合迁移是最适用于组织希望在留在多个月或更多的混合配置。使用联机邮箱移动，您将获取列出前面的此部分中，加上目录同步和更好集成的合规性功能，能够将邮箱移动到与 Office 365 的功能。Office 365 成为内部部署组织的扩展。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p115">Full hybrid migrations are best for organizations that expect to stay in a hybrid configuration for many months or more. You'll get the features listed earlier in this section, plus directory synchronization, better integrated compliance features, and the ability to move mailboxes to and from Office 365 using online mailbox moves. Office 365 becomes an extension of your on-premises organization.</span></span>
  
<span data-ttu-id="d80a8-204">如果您正在考虑执行操作完全混合迁移，下面是要考虑的几个事项：</span><span class="sxs-lookup"><span data-stu-id="d80a8-204">If you're thinking about doing a full hybrid migration, here are a few things to consider:</span></span>
  
- <span data-ttu-id="d80a8-p116">完整的混合迁移不适合于组织的所有类型。由于完整混合迁移的复杂性，与小于几个几百个邮箱的组织通常看不到 justify 工作量和一个设置所需的成本的好处。如果这听起来您的组织，则强烈建议您改用; 考虑 Cutover 或暂存迁移</span><span class="sxs-lookup"><span data-stu-id="d80a8-p116">Full hybrid migrations aren't suited to all types of organizations. Due to the complexity of full hybrid migrations, organizations with less than a few hundred mailboxes don't typically see benefits that justify the effort and cost needed to set one up. If this sounds like your organization, we strongly recommend that you consider Cutover or Staged migrations instead;</span></span>
    
- <span data-ttu-id="d80a8-208">Office 365 需要连接到 Exchange 2010 服务器通过 TCP 端口 443; 使用 Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="d80a8-208">Office 365 will need to connect to an Exchange 2010 server using Outlook Anywhere over TCP port 443;</span></span>
    
- <span data-ttu-id="d80a8-209">您需要设置您的本地 Active Directory 服务器与 Office 365; 之间使用 Azure Active Directory 连接 (AADConnect) 的目录同步</span><span class="sxs-lookup"><span data-stu-id="d80a8-209">You'll need to set up directory synchronization using Azure Active Directory Connect (AADConnect) between your on-premises Active Directory servers and Office 365;</span></span>
    
- <span data-ttu-id="d80a8-210">用户将能够登录到使用相同的用户名和密码时他们登录到本地网络 （需要使用密码同步和/或 Active Directory 联合身份验证服务的 Azure Active Directory 连接）; 它们使用其 Office 365 邮箱</span><span class="sxs-lookup"><span data-stu-id="d80a8-210">Users will be able to log in to their Office 365 mailbox using the same username and password they use when they log into the local network (requires Azure Active Directory Connect with password synchronization and/or Active Directory Federation Services);</span></span>
    
- <span data-ttu-id="d80a8-211">您将需要为每个用户邮箱迁移; 包括 Exchange Online 的 Office 365 许可证</span><span class="sxs-lookup"><span data-stu-id="d80a8-211">You'll need an Office 365 license that includes Exchange Online for each user mailbox you migrate;</span></span>
    
- <span data-ttu-id="d80a8-212">用户不需要在他们的设备 （某些旧的 Android 电话可能需要一个新的配置文件） 的最新的 Outlook 配置文件设置，并不需要重新下载其电子邮件。</span><span class="sxs-lookup"><span data-stu-id="d80a8-212">Users don't need to set up a new Outlook profile on most of their devices (some older Android phones might need a new profile) and won't need to re-download their email.</span></span>
    
<span data-ttu-id="d80a8-213">如果适合您的完整混合迁移声音，看看以下资源可帮助您实现您的迁移：</span><span class="sxs-lookup"><span data-stu-id="d80a8-213">If a full hybrid migration sounds right for you, take a look at the following resources to help you with your migration:</span></span>
  
- [<span data-ttu-id="d80a8-214">Exchange 部署助理</span><span class="sxs-lookup"><span data-stu-id="d80a8-214">Exchange Deployment Assistant</span></span>](https://aka.ms/exdeploy)
    
- [<span data-ttu-id="d80a8-215">Exchange Server 混合部署</span><span class="sxs-lookup"><span data-stu-id="d80a8-215">Exchange Server Hybrid Deployments</span></span>](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="d80a8-216">混合配置向导</span><span class="sxs-lookup"><span data-stu-id="d80a8-216">Hybrid Configuration wizard</span></span>](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="d80a8-217">混合配置向导常见问题解答</span><span class="sxs-lookup"><span data-stu-id="d80a8-217">Hybrid Configuration wizard FAQs</span></span>](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="d80a8-218">混合部署先决条件</span><span class="sxs-lookup"><span data-stu-id="d80a8-218">Hybrid deployment prerequisites</span></span>](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a><span data-ttu-id="d80a8-219">迁移到新版本的 Exchange Server</span><span class="sxs-lookup"><span data-stu-id="d80a8-219">Migrate to a newer version of Exchange Server</span></span>

<span data-ttu-id="d80a8-p117">尽管我们强烈相信，您可以通过迁移到 Office 365 中实现的最佳值和用户体验，我们还了解一些组织需要保留其电子邮件的本地。这可能是由于法规要求，以确保数据不存储在数据中心位于另一个国家/地区，依此类推。如果您选择保留电子邮件内部部署，您可以将 Exchange 2010 环境迁移到 Exchange 2013 或 Exchange 2016。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p117">While we strongly believe that you can achieve the best value and user experience by migrating to Office 365, we also understand that some organizations need to keep their email on-premises. This could be because of regulatory requirements, to guarantee data isn't stored in a datacenter located in another country, and so on. If you choose to keep your email on-premises, you can migrate your Exchange 2010 environment to Exchange 2013 or Exchange 2016.</span></span>
  
<span data-ttu-id="d80a8-p118">我们建议如果无法迁移到 Office 365 迁移到 Exchange 2016。Exchange 2016 包含所有的功能和改进包括与早期版本的 Exchange 和 （尽管某些功能仅适用于 Office 365） 提供与 Office 365 体验最密切匹配。签出只需几个您已被不了解的事项：</span><span class="sxs-lookup"><span data-stu-id="d80a8-p118">We recommend that you migrate to Exchange 2016 if you can't migrate to Office 365. Exchange 2016 includes all the features and advancements included with previous releases of Exchange, and it most closely matches the experience available with Office 365 (although some features are available only in Office 365). Check out just a few of the things you've been missing out on:</span></span>
  
|<span data-ttu-id="d80a8-226">**Exchange 版本**</span><span class="sxs-lookup"><span data-stu-id="d80a8-226">**Exchange release**</span></span>|<span data-ttu-id="d80a8-227">**功能**</span><span class="sxs-lookup"><span data-stu-id="d80a8-227">**Features**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d80a8-228">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="d80a8-228">Exchange 2013</span></span>  <br/> | <span data-ttu-id="d80a8-229">简化的体系结构减少到三个服务器角色的 （邮箱，客户端访问边缘传输）</span><span class="sxs-lookup"><span data-stu-id="d80a8-229">Simplified architecture reducing the number of server roles to three (Mailbox, Client Access, Edge Transport)</span></span>  <br/>  <span data-ttu-id="d80a8-230">帮助保持泄露敏感信息的数据丢失预防策略 (DLP)</span><span class="sxs-lookup"><span data-stu-id="d80a8-230">Data loss prevention policies (DLP) that help keep sensitive information from leaking</span></span>  <br/>  <span data-ttu-id="d80a8-231">显著改进 Outlook Web 应用程序体验</span><span class="sxs-lookup"><span data-stu-id="d80a8-231">Significantly improved Outlook Web App Experience</span></span>  <br/> |
|<span data-ttu-id="d80a8-232">Exchange 2016</span><span class="sxs-lookup"><span data-stu-id="d80a8-232">Exchange 2016</span></span>  <br/> | <span data-ttu-id="d80a8-233">*从 Exchange 2013 的功能和...*</span><span class="sxs-lookup"><span data-stu-id="d80a8-233">*Features from Exchange 2013 and…*</span></span>  <br/>  <span data-ttu-id="d80a8-234">进一步简化的服务器角色到刚邮箱和边缘传输</span><span class="sxs-lookup"><span data-stu-id="d80a8-234">Further simplified server roles to just Mailbox and Edge Transport</span></span>  <br/>  <span data-ttu-id="d80a8-235">与 SharePoint 以及集成改进的 DLP</span><span class="sxs-lookup"><span data-stu-id="d80a8-235">Improved DLP along with integration with SharePoint</span></span>  <br/>  <span data-ttu-id="d80a8-236">改进的数据库恢复</span><span class="sxs-lookup"><span data-stu-id="d80a8-236">Improved database resilience</span></span>  <br/>  <span data-ttu-id="d80a8-237">联机文档协作</span><span class="sxs-lookup"><span data-stu-id="d80a8-237">Online document collaboration</span></span>  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a><span data-ttu-id="d80a8-238">应迁移到哪个版本？</span><span class="sxs-lookup"><span data-stu-id="d80a8-238">Which version should I migrate to?</span></span>

<span data-ttu-id="d80a8-p119">我们建议您最初假定您将迁移到 Exchange 2016。然后，使用以下信息，以确认您的假设或 Exchange 2016 出规则。如果您不能将迁移到 Exchange 2016 的一个原因或其他，执行相同处理 Exchange 2013，等等。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p119">We recommend that you initially assume that you'll migrate to Exchange 2016. Then, use the following information to confirm your assumption or to rule out Exchange 2016. If you can't migrate to Exchange 2016 for one reason or another, do the same process with Exchange 2013, and so on.</span></span>
  
|<span data-ttu-id="d80a8-242">**注意事项**</span><span class="sxs-lookup"><span data-stu-id="d80a8-242">**Consideration**</span></span>|<span data-ttu-id="d80a8-243">**更多信息**</span><span class="sxs-lookup"><span data-stu-id="d80a8-243">**More Info**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d80a8-244">支持日期结束</span><span class="sxs-lookup"><span data-stu-id="d80a8-244">End of support dates</span></span>  <br/> | <span data-ttu-id="d80a8-245">Exchange 2010，如每个版本的 Exchange 具有自己末尾支持日期：</span><span class="sxs-lookup"><span data-stu-id="d80a8-245">Like Exchange 2010, each version of Exchange has its own end of support date:</span></span>  <br/> <span data-ttu-id="d80a8-246">**Exchange 2013** -年 4 月 2023</span><span class="sxs-lookup"><span data-stu-id="d80a8-246">**Exchange 2013** - April 2023</span></span>  <br/> <span data-ttu-id="d80a8-247">**Exchange 2016** -年 10 月 2025</span><span class="sxs-lookup"><span data-stu-id="d80a8-247">**Exchange 2016** - October 2025</span></span>  <br/>  <span data-ttu-id="d80a8-p120">前面的末尾支持日期、 更快您需要执行其他迁移。年 4 月 2023年是大量仔细，比你想象 ！</span><span class="sxs-lookup"><span data-stu-id="d80a8-p120">The earlier the end of support date, the sooner you'll need to perform another migration. April 2023 is a lot closer than you think!  </span></span><br/> |
|<span data-ttu-id="d80a8-250">Exchange 2013 或 2016年迁移路径</span><span class="sxs-lookup"><span data-stu-id="d80a8-250">Migration path to Exchange 2013 or 2016</span></span>  <br/> |<span data-ttu-id="d80a8-251">下面是用于迁移到 Exchange 2013 的一般阶段：</span><span class="sxs-lookup"><span data-stu-id="d80a8-251">Here are the general phases for migrating to Exchange 2013:</span></span>  <br/> <span data-ttu-id="d80a8-252">安装 Exchange 2013 或 2016年到现有的 Exchange 2010 组织移动服务，并且到 Exchange 2013 或 2016年移动邮箱的其他基础结构和公用文件夹到 Exchange 2013 或 2016年取消剩余 Exchange 2010 服务器</span><span class="sxs-lookup"><span data-stu-id="d80a8-252">Install Exchange 2013 or 2016 into your existing Exchange 2010 organization Move services and other infrastructure to Exchange 2013 or 2016 Move mailboxes and public folders to Exchange 2013 or 2016 Decommission remaining Exchange 2010 servers</span></span> |
|<span data-ttu-id="d80a8-253">版本共存</span><span class="sxs-lookup"><span data-stu-id="d80a8-253">Version coexistence</span></span>  <br/> |<span data-ttu-id="d80a8-p121">迁移到 Exchange 2013 或 Exchange 2016 时，您可以安装到现有的 Exchange 2010 组织的任一版本。这样可以安装一个或多个 Exchange 2013 或 Exchange 2016 服务器，并执行迁移。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p121">When migrating to Exchange 2013 or Exchange 2016, you can install either version into an existing Exchange 2010 organization. This enables you to install one or more Exchange 2013 or Exchange 2016 servers and perform your migration.</span></span>  <br/> |
|<span data-ttu-id="d80a8-256">服务器硬件</span><span class="sxs-lookup"><span data-stu-id="d80a8-256">Server hardware</span></span>  <br/> | <span data-ttu-id="d80a8-p122">从 Exchange 2010，服务器硬件要求已发生更改。您需要确保您要使用的硬件兼容。您可以找出有关每个版本此处的硬件要求的详细信息：</span><span class="sxs-lookup"><span data-stu-id="d80a8-p122">Server hardware requirements have changed from Exchange 2010. You'll need to make sure the hardware you're going to use is compatible. You can find out more about hardware requirements for each version here:  </span></span><br/> [<span data-ttu-id="d80a8-260">Exchange 2016 系统要求</span><span class="sxs-lookup"><span data-stu-id="d80a8-260">Exchange 2016 System Requirements</span></span>](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [<span data-ttu-id="d80a8-261">Exchange 2013 系统要求</span><span class="sxs-lookup"><span data-stu-id="d80a8-261">Exchange 2013 System Requirements</span></span>](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/>  <span data-ttu-id="d80a8-262">您会发现，使用 Exchange 性能和增加的计算能力的重要改进和更高版本服务器中的存储容量，您可能需要较少的服务器来支持相同的邮箱数。</span><span class="sxs-lookup"><span data-stu-id="d80a8-262">You'll find that with the significant improvements in Exchange performance, and the increased computing power and storage capacity in newer servers, you'll likely need fewer servers to support the same number of mailboxes.</span></span>  <br/> |
|<span data-ttu-id="d80a8-263">操作系统版本</span><span class="sxs-lookup"><span data-stu-id="d80a8-263">Operating system version</span></span>  <br/> | <span data-ttu-id="d80a8-264">每个版本的最小受支持的操作系统版本是：</span><span class="sxs-lookup"><span data-stu-id="d80a8-264">The minimum supported operating system versions for each version are:</span></span>  <br/> <span data-ttu-id="d80a8-265">**Exchange 2016**Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d80a8-265">**Exchange 2016** Windows Server 2012</span></span>  <br/> <span data-ttu-id="d80a8-266">**Exchange 2013**Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d80a8-266">**Exchange 2013** Windows Server 2008 R2 SP1</span></span>  <br/>  <span data-ttu-id="d80a8-267">您可以在[Exchange 可支持性矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关支持的操作系统的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d80a8-267">You can find more information about operating system support at [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).</span></span>  <br/> |
|<span data-ttu-id="d80a8-268">Active Directory 林功能级别</span><span class="sxs-lookup"><span data-stu-id="d80a8-268">Active Directory forest functional level</span></span>  <br/> | <span data-ttu-id="d80a8-269">最小支持 Active Directory 林功能级别的每个版本是：</span><span class="sxs-lookup"><span data-stu-id="d80a8-269">The minimum supported Active Directory forest functional levels for each version are:</span></span>  <br/> <span data-ttu-id="d80a8-270">**Exchange 2016**Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d80a8-270">**Exchange 2016** Windows Server 2008 R2 SP1</span></span>  <br/> <span data-ttu-id="d80a8-271">**Exchange 2013**Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="d80a8-271">**Exchange 2013** Windows Server 2003</span></span>  <br/>  <span data-ttu-id="d80a8-272">您可以在[Exchange 可支持性矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关林功能级别支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d80a8-272">You can find more information about forest functional level support at [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).</span></span>  <br/> |
|<span data-ttu-id="d80a8-273">Office 客户端版本</span><span class="sxs-lookup"><span data-stu-id="d80a8-273">Office client versions</span></span>  <br/> | <span data-ttu-id="d80a8-274">每个版本的受支持的最小 Office 客户端版本是：</span><span class="sxs-lookup"><span data-stu-id="d80a8-274">The minimum supported Office client versions for each version are:</span></span>  <br/> <span data-ttu-id="d80a8-275">**Exchange 2016**Office 2010 （具有最新的更新）</span><span class="sxs-lookup"><span data-stu-id="d80a8-275">**Exchange 2016** Office 2010 (with the latest updates)</span></span>  <br/> <span data-ttu-id="d80a8-276">**Exchange 2013**Office 2007 SP3</span><span class="sxs-lookup"><span data-stu-id="d80a8-276">**Exchange 2013** Office 2007 SP3</span></span>  <br/>  <span data-ttu-id="d80a8-277">您可以在[Exchange 可支持性矩阵](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)中找到有关 Office 客户端支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d80a8-277">You can find more information about Office client support at [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).</span></span>  <br/> |
   
#### <a name="how-do-i-migrate"></a><span data-ttu-id="d80a8-278">如何迁移</span><span class="sxs-lookup"><span data-stu-id="d80a8-278">How do I migrate?</span></span>

<span data-ttu-id="d80a8-279">如果您决定要保留电子邮件内部部署，您可以使用以下资源可帮助您实现您的迁移：</span><span class="sxs-lookup"><span data-stu-id="d80a8-279">If you've decided that you want to keep your email on-premises, you can use the following resources to help you with your migration:</span></span>
  
- [<span data-ttu-id="d80a8-280">Exchange 部署助理</span><span class="sxs-lookup"><span data-stu-id="d80a8-280">Exchange Deployment Assistant</span></span>](https://aka.ms/exdeploy)
    
- <span data-ttu-id="d80a8-281">Exchange [2016 的](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx)， [2013年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)的 active Directory 架构更改</span><span class="sxs-lookup"><span data-stu-id="d80a8-281">Active Directory schema changes for Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)</span></span>
    
- <span data-ttu-id="d80a8-282">Exchange [2016年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)， [2013年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)的系统要求</span><span class="sxs-lookup"><span data-stu-id="d80a8-282">System requirements for Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)</span></span>
    
- <span data-ttu-id="d80a8-283">Exchange [2016年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx)， [2013年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)的先决条件</span><span class="sxs-lookup"><span data-stu-id="d80a8-283">Prerequisites for Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)</span></span>
    
## <a name="what-if-i-need-help"></a><span data-ttu-id="d80a8-284">如果需要帮助？</span><span class="sxs-lookup"><span data-stu-id="d80a8-284">What if I need help?</span></span>

<span data-ttu-id="d80a8-p123">如果您正在迁移到 Office 365，您可能有资格使用我们的 Microsoft FastTrack 服务。FastTrack 提供最佳实践、 工具和资源，以使您的迁移到 Office 365 尽可能流畅。最重要的是，您必须实际支持工程师，它将指导您完成迁移，从规划和设计一直到把最后一个邮箱迁移。如果您想要了解有关 FastTrack 的详细信息，了解一下[Microsoft FastTrack](https://fasttrack.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="d80a8-p123">If you're migrating to Office 365, you might be eligible to use our Microsoft FastTrack service. FastTrack provides best practices, tools, and resources to make your migration to Office 365 as seamless as possible. Best of all, you'll have a real support engineer that will walk you through your migration, from planning and design all the way to migrating your last mailbox. If you want to know more about FastTrack, take a look at [Microsoft FastTrack](https://fasttrack.microsoft.com/).</span></span>
  
<span data-ttu-id="d80a8-p124">如果您遇到任何问题期间迁移到 Office 365，并且您不使用 FastTrack 或在迁移到新版本的 Exchange 服务器，我们将帮助。以下是您可以使用一些资源：</span><span class="sxs-lookup"><span data-stu-id="d80a8-p124">If you run into any problems during your migration to Office 365 and you aren't using FastTrack, or your migration to a newer version of Exchange Server, we're here to help. Here are some resources you can use:</span></span>
  
- [<span data-ttu-id="d80a8-291">技术社区</span><span class="sxs-lookup"><span data-stu-id="d80a8-291">Technical community</span></span>](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [<span data-ttu-id="d80a8-292">客户支持</span><span class="sxs-lookup"><span data-stu-id="d80a8-292">Customer support</span></span>](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a><span data-ttu-id="d80a8-293">相关主题</span><span class="sxs-lookup"><span data-stu-id="d80a8-293">Related topics</span></span>

[<span data-ttu-id="d80a8-294">资源可帮助您升级从 Office 2010 的服务器和客户端</span><span class="sxs-lookup"><span data-stu-id="d80a8-294">Resources to help you upgrade from Office 2010 servers and clients</span></span>](upgrade-from-office-2010-servers-and-products.md)
  
[<span data-ttu-id="d80a8-295">Office 退休组 （Microsoft 技术社区）</span><span class="sxs-lookup"><span data-stu-id="d80a8-295">Office Retirement Group (Microsoft Tech Community)</span></span>](https://go.microsoft.com/fwlink/?linkid=842065)
  

