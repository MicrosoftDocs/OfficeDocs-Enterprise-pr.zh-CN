---
title: SharePoint Server 2007 停止提供支持路线图
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
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
ms.collection: Ent_O365
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
description: 在 2017 年 10 月 10，支持结束 SharePoint Server 2007。阅读此文，了解有关疑难解答、 最佳实践、 系统要求、 升级步骤和如何从 Microsoft 合作伙伴获取帮助您升级选项。
ms.openlocfilehash: b548e7623a72d57793c18409a80506bb832df858
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169794"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a><span data-ttu-id="62fa3-104">SharePoint Server 2007 停止提供支持路线图</span><span class="sxs-lookup"><span data-stu-id="62fa3-104">SharePoint Server 2007 end of support roadmap</span></span>

<span data-ttu-id="62fa3-p102">在**2017 年 10 月 10，**，Microsoft Office SharePoint Server 2007 达到结束的支持。如果您没有开始从 SharePoint Server 2007 迁移到 Office 365 或 SharePoint Server 内部部署的更新版本，那么现在以开始规划。本文介绍了资源以帮助人们将数据迁移到 SharePoint Online，或升级 SharePoint Server 本地。</span><span class="sxs-lookup"><span data-stu-id="62fa3-p102">On **October 10, 2017**, Microsoft Office SharePoint Server 2007 reached end of support. If you haven't begun your migration from SharePoint Server 2007 to Office 365 or a newer version of SharePoint Server on-premises, now's the time to start planning. This article details resources to help people migrate data to SharePoint Online, or upgrade your SharePoint Server on-premises.</span></span> 
  
## <a name="what-does-end-of-support-mean"></a><span data-ttu-id="62fa3-108">支持平均值内容的末尾？</span><span class="sxs-lookup"><span data-stu-id="62fa3-108">What does end of support mean?</span></span>

<span data-ttu-id="62fa3-p103">SharePoint Server 像几乎在所有 Microsoft 产品，具有支持生命周期期间 Microsoft 提供的新功能、 bug 修复、 安全修补程序，等等。此生命周期通常会持续 10 年中的产品的初始发布日期和此生命周期的结束称为产品的结束的支持。在支持的末尾，Microsoft 不再提供：</span><span class="sxs-lookup"><span data-stu-id="62fa3-p103">SharePoint Server, like almost all Microsoft products, has a support lifecycle during which Microsoft provides new features, bug fixes, security fixes, and so on. This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support. At end of support, Microsoft no longer provides:</span></span>
  
- <span data-ttu-id="62fa3-112">可能出现; 的问题的技术支持</span><span class="sxs-lookup"><span data-stu-id="62fa3-112">Technical support for problems that may occur;</span></span>
    
- <span data-ttu-id="62fa3-113">Bug 修复的问题的发现以及可能影响的稳定性和可用性的服务器。</span><span class="sxs-lookup"><span data-stu-id="62fa3-113">Bug fixes for issues that are discovered and that may impact the stability and usability of the server;</span></span>
    
- <span data-ttu-id="62fa3-114">安全漏洞的发现和可能使该服务器安全轻易; 地受到修补程序和</span><span class="sxs-lookup"><span data-stu-id="62fa3-114">Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches; and</span></span> 
    
- <span data-ttu-id="62fa3-115">更新所在的时区。</span><span class="sxs-lookup"><span data-stu-id="62fa3-115">Time zone updates.</span></span>
    
<span data-ttu-id="62fa3-p104">上述 SharePoint Server 2007 服务器场仍可正常工作后年 10 月 10，2017，没有进一步更新、 修补程序，或修补程序将传送的产品 （包括安全修补程序修补程序） 和 Microsoft 支持将完全移动了到其支持的努力较新版本的产品。因为您的安装将不再受支持或修补，作为末尾支持方法应升级该产品，或迁移重要数据。</span><span class="sxs-lookup"><span data-stu-id="62fa3-p104">Though your SharePoint Server 2007 farm will still be operational after October 10, 2017, no further updates, patches, or fixes will be shipped for the product (including security patches/fixes), and Microsoft Support will have fully shifted its support efforts to more recent versions of the product. Because your installation will no longer supported or patched, as end of support approaches you should upgrade the product, or migrate important data.</span></span>
  
> [!TIP]
> <span data-ttu-id="62fa3-p105">如果您已尚未升级或迁移的计划，请参阅： [SharePoint 2007 迁移选项，要考虑](sharepoint-2007-migration-options.md)的开始位置的一些示例。您还可以搜索[Microsoft 合作伙伴](https://go.microsoft.com/fwlink/?linkid=841249)可帮助进行升级或 Office 365 迁移 （或两者）。</span><span class="sxs-lookup"><span data-stu-id="62fa3-p105">If you haven't already planned for upgrade or migration, please see: [SharePoint 2007 migration options to consider](sharepoint-2007-migration-options.md), for some examples of where to begin. You can also search for [Microsoft Partners](https://go.microsoft.com/fwlink/?linkid=841249) who can help with upgrade or Office 365 migration (or both).</span></span> 
  
<span data-ttu-id="62fa3-120">有关 Office 2007 服务器达到结束的支持的详细信息，请参阅[规划 Office 2007 服务器的升级](https://support.office.com/article/4e5eab5f-05db-4627-9e17-421a6bf89606.aspx)。</span><span class="sxs-lookup"><span data-stu-id="62fa3-120">For more information about Office 2007 servers reaching the end of support, see [Plan your upgrade for Office 2007 servers](https://support.office.com/article/4e5eab5f-05db-4627-9e17-421a6bf89606.aspx).</span></span>
  
## <a name="what-are-my-options"></a><span data-ttu-id="62fa3-121">我的选项是什么？</span><span class="sxs-lookup"><span data-stu-id="62fa3-121">What are my options?</span></span>

<span data-ttu-id="62fa3-p106">您的第一个停止应[产品生命周期网站](https://go.microsoft.com/fwlink/?linkid=843148)。如果您有老化设置在本地 Microsoft 产品，您应检查其末尾支持日期，以便，一年或这样出-或，只要您迁移通常需要-可以安排升级或迁移。当选择下一步，它可能有助于想到什么将够好、 更好、 和最佳当谈到产品功能。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="62fa3-p106">Your first stop should be the [Product Lifecycle site](https://go.microsoft.com/fwlink/?linkid=843148). If you have an on-premises Microsoft product that is aging, you should check for its end of support date so that, a year or so out - or as long as your migrations generally require - you can schedule upgrade or migrations. When choosing the next step, it might help to think in terms of what would be good enough, better, and best when it comes to product features. Here's an example:</span></span>
  
|<span data-ttu-id="62fa3-126">**较好**</span><span class="sxs-lookup"><span data-stu-id="62fa3-126">**Good**</span></span>|<span data-ttu-id="62fa3-127">**更好**</span><span class="sxs-lookup"><span data-stu-id="62fa3-127">**Better**</span></span>|<span data-ttu-id="62fa3-128">**最好**</span><span class="sxs-lookup"><span data-stu-id="62fa3-128">**Best**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="62fa3-129">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="62fa3-129">SharePoint Server 2010</span></span>  <br/> |<span data-ttu-id="62fa3-130">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="62fa3-130">SharePoint Server 2013</span></span>  <br/> |<span data-ttu-id="62fa3-131">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="62fa3-131">SharePoint Online</span></span>  <br/> |
||<span data-ttu-id="62fa3-132">SharePoint 混合</span><span class="sxs-lookup"><span data-stu-id="62fa3-132">SharePoint Hybrid</span></span>  <br/> |<span data-ttu-id="62fa3-133">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="62fa3-133">SharePoint Server 2016</span></span>  <br/> |
|||<span data-ttu-id="62fa3-134">SharePoint 混合</span><span class="sxs-lookup"><span data-stu-id="62fa3-134">SharePoint Hybrid</span></span>  <br/> |
   
<span data-ttu-id="62fa3-p107">如果您选择选项低一端的小数 （足够好），请记住您将需要在开始从 SharePoint Server 2007 的迁移后很快规划升级已完成。（结束的 SharePoint Server 2007 是支持的 2017 年 10 月 10。请注意，这些日期受到更改，并检查[产品生命周期网站](https://support.microsoft.com/en-us/lifecycle)。）</span><span class="sxs-lookup"><span data-stu-id="62fa3-p107">If you choose options on the low end of the scale (good enough), remember you will need to begin planning for upgrade very soon after migration from SharePoint Server 2007 is complete. (end of support for SharePoint Server 2007 is October 10, 2017. Please note that these dates are subject to change and check the [Product Lifecycle site](https://support.microsoft.com/en-us/lifecycle).)</span></span>
  
## <a name="where-can-i-go-next"></a><span data-ttu-id="62fa3-138">其中可以继续下一步？</span><span class="sxs-lookup"><span data-stu-id="62fa3-138">Where can I go next?</span></span>

<span data-ttu-id="62fa3-p108">SharePoint Server 可以是在本地安装在您自己的服务器，或者您可以使用 SharePoint Online，这是 Microsoft Office 365 的一部分的联机服务。您可以选择：</span><span class="sxs-lookup"><span data-stu-id="62fa3-p108">SharePoint Server can be installed on-premises on your own servers, or you can use SharePoint Online, which is an online service that is part of Microsoft Office 365. You can choose to:</span></span>
  
- <span data-ttu-id="62fa3-141">迁移到 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="62fa3-141">Migrate to SharePoint Online</span></span>
    
- <span data-ttu-id="62fa3-142">升级 SharePoint Server 内部部署</span><span class="sxs-lookup"><span data-stu-id="62fa3-142">Upgrade SharePoint Server on-premises</span></span>
    
- <span data-ttu-id="62fa3-143">执行以上两项操作</span><span class="sxs-lookup"><span data-stu-id="62fa3-143">Do both of the above</span></span>
    
- <span data-ttu-id="62fa3-144">实现[SharePoint 混合](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)解决方案</span><span class="sxs-lookup"><span data-stu-id="62fa3-144">Implement a [SharePoint hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) solution</span></span> 
    
<span data-ttu-id="62fa3-p109">注意隐藏相关的成本与维护服务器场循序，维护或自定义项，迁移和升级 SharePoint 服务器所依赖的硬件。具有内部部署 SharePoint Server 服务器场必不可少; 如果奖励有否则，如果您的服务器场运行旧 SharePoint 服务器上，而不必大量自定义，您可以受益于计划迁移到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="62fa3-p109">Be aware of hidden costs associated with maintaining a server farm going forward, maintaining or migrating customizations, and upgrading the hardware upon which SharePoint Server depends. Having an on-premises SharePoint Server farm is rewarding if it is a necessity; otherwise, if you run your farm on legacy SharePoint Servers, without heavy customization, you can benefit from a planned migration to SharePoint Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="62fa3-p110">SharePoint 2007 中的内容很少使用时的另一个选项。某些 SharePoint 管理员可以选择为[创建 Office 365 订阅](https://go.microsoft.com/fwlink/?linkid=843152)，请设置全新的 SharePoint Online 网站，然后完全，剪切离开 SharePoint 2007 的全新的 SharePoint Online 站点采用仅的最重要的文档。从，数据可能会耗尽从 SharePoint 2007 站点到存档。授予用户如何使用数据 SharePoint 2007 安装到灵感。可能有创作方法可以解决此问题 ！</span><span class="sxs-lookup"><span data-stu-id="62fa3-p110">There is another option if the content in SharePoint 2007 is infrequently used. Some SharePoint Administrators may choose to [create an Office 365 Subscription](https://go.microsoft.com/fwlink/?linkid=843152), set up a brand new SharePoint Online site, and then cut away from SharePoint 2007, cleanly, taking only the most essential documents to the fresh SharePoint Online sites. From there, data may be drained from the SharePoint 2007 site into archives. Give thought to how users work with data your SharePoint 2007 installation. There may be creative ways to resolve this problem!</span></span> 
  
|<span data-ttu-id="62fa3-152">**SharePoint Online (SPO)**</span><span class="sxs-lookup"><span data-stu-id="62fa3-152">**SharePoint Online (SPO)**</span></span>|<span data-ttu-id="62fa3-153">**SharePoint Server 内部部署**</span><span class="sxs-lookup"><span data-stu-id="62fa3-153">**SharePoint Server on-premises**</span></span>|
|:-----|:-----|
|<span data-ttu-id="62fa3-154">时间跟踪成本很高 (计划 / 执行 / 验证)</span><span class="sxs-lookup"><span data-stu-id="62fa3-154">High cost in time (plan / execution / verification)</span></span>  <br/> |<span data-ttu-id="62fa3-155">时间跟踪成本很高 (计划 / 执行 / 验证)</span><span class="sxs-lookup"><span data-stu-id="62fa3-155">High cost in time (plan / execution / verification)</span></span>  <br/> |
|<span data-ttu-id="62fa3-156">资金 （没有硬件购买） 中降低成本</span><span class="sxs-lookup"><span data-stu-id="62fa3-156">Lower cost in funds (no hardware purchases)</span></span>  <br/> |<span data-ttu-id="62fa3-157">资金中的成本更高 (硬件 + 开发人员 / admins)</span><span class="sxs-lookup"><span data-stu-id="62fa3-157">Higher cost in funds (hardware + devs / admins)</span></span>  <br/> |
|<span data-ttu-id="62fa3-158">一次性迁移中的成本</span><span class="sxs-lookup"><span data-stu-id="62fa3-158">One-time cost in migration</span></span>  <br/> |<span data-ttu-id="62fa3-159">一次性成本重复每未来迁移</span><span class="sxs-lookup"><span data-stu-id="62fa3-159">One-time cost repeated per future migration</span></span>  <br/> |
|<span data-ttu-id="62fa3-160">较低的总体拥有成本 / 维护</span><span class="sxs-lookup"><span data-stu-id="62fa3-160">Low total cost of ownership / maintenance</span></span>  <br/> |<span data-ttu-id="62fa3-161">总体拥有成本高 / 维护</span><span class="sxs-lookup"><span data-stu-id="62fa3-161">High total cost of ownership / maintenance</span></span>  <br/> |
   
<span data-ttu-id="62fa3-p111">迁移到 Office 365 时，一次性移动时您组织的数据，还可以决定要让进入云内容和要留下将有前期，粗成本。但是，升级将自动从那时、 不再需要管理硬件和软件更新，并且将 Microsoft 服务级别协议 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) 通过备份服务器场的运行时间。</span><span class="sxs-lookup"><span data-stu-id="62fa3-p111">When you migrate to Office 365, the one-time move will have a heavier cost up-front, while you're organizing data and deciding what to take to the cloud and what to leave behind. However, upgrades will be automatic from that point, you will no longer need to manage hardware and software updates, and the up-time of your farm will be backed by a Microsoft Service Level Agreement ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).</span></span>
  
### <a name="migrate-to-sharepoint-online"></a><span data-ttu-id="62fa3-164">迁移到 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="62fa3-164">Migrate to SharePoint Online</span></span>

<span data-ttu-id="62fa3-p112">请确保 SharePoint Online 具有所需的查看关联的服务说明的所有功能。下面是指向所有 Office 365 服务说明的链接：</span><span class="sxs-lookup"><span data-stu-id="62fa3-p112">Make sure that SharePoint Online has all the features you need by reviewing the associated service description. Here's the link to all Office 365 Service Descriptions:</span></span>
  
[<span data-ttu-id="62fa3-167">Office 365 服务说明</span><span class="sxs-lookup"><span data-stu-id="62fa3-167">Office 365 Service Descriptions</span></span>](https://go.microsoft.com/fwlink/?linkid=272060)
  
<span data-ttu-id="62fa3-p113">没有直接方法从 SharePoint 2007 迁移到 SharePoint Online;将手动完成迁移到 SharePoint Online。如果升级到 SharePoint Server 2013 或 SharePoint Server 2016 时，您移动还可能涉及使用 SharePoint 迁移 API （例如迁移到 OneDrive for Business，信息）。</span><span class="sxs-lookup"><span data-stu-id="62fa3-p113">There is no direct way to migrate from SharePoint 2007 to SharePoint Online; your move to SharePoint Online would be done manually. If you upgrade to SharePoint Server 2013 or SharePoint Server 2016, your move might also involve using the SharePoint Migration API (to migrate information into OneDrive for Business, for example).</span></span>
  
|<span data-ttu-id="62fa3-170">**联机 Pro**</span><span class="sxs-lookup"><span data-stu-id="62fa3-170">**Online Pro**</span></span>|<span data-ttu-id="62fa3-171">**联机手段**</span><span class="sxs-lookup"><span data-stu-id="62fa3-171">**Online Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="62fa3-172">Microsoft 提供 SPO 硬件和所有硬件管理。</span><span class="sxs-lookup"><span data-stu-id="62fa3-172">Microsoft supplies SPO hardware and all hardware administration.</span></span>  <br/> |<span data-ttu-id="62fa3-173">可用的功能可能不同于 SharePoint Server 本地和 SPO。</span><span class="sxs-lookup"><span data-stu-id="62fa3-173">Available features may be different between SharePoint Server on-premises and SPO.</span></span>  <br/> |
|<span data-ttu-id="62fa3-174">是您的订阅的全局管理员和可能向 SPO 网站分配管理员。</span><span class="sxs-lookup"><span data-stu-id="62fa3-174">You are the global administrator of your subscription, and may assign administrators to SPO sites.</span></span>  <br/> |<span data-ttu-id="62fa3-175">Office 365 中的 SharePoint 管理员角色中包含到 SharePoint 服务器的本地不存在 （或不是必需的） 中的服务器场管理员提供一些操作。</span><span class="sxs-lookup"><span data-stu-id="62fa3-175">Some actions available to a Farm Administrator in SharePoint Server on-premises do not exist (or are not necessary) included in the SharePoint Administrator role in Office 365.</span></span>  <br/> |
|<span data-ttu-id="62fa3-176">Microsoft 应用修补程序和修复基础硬件和软件更新。</span><span class="sxs-lookup"><span data-stu-id="62fa3-176">Microsoft applies patches, fixes and updates to underlying hardware and software.</span></span>  <br/> |<span data-ttu-id="62fa3-177">因为没有基础服务中的文件系统无法访问，一些自定义项将受到限制。</span><span class="sxs-lookup"><span data-stu-id="62fa3-177">Because there is no access to the underlying file system in the service, some customizations are limited.</span></span>  <br/> |
|<span data-ttu-id="62fa3-178">Microsoft 发布[服务级别协议](https://go.microsoft.com/fwlink/?linkid=843153)，并移动快速以解决服务级别的事件。</span><span class="sxs-lookup"><span data-stu-id="62fa3-178">Microsoft publishes [Service Level Agreements](https://go.microsoft.com/fwlink/?linkid=843153) and moves quickly to resolve service level incidents.</span></span>  <br/> |<span data-ttu-id="62fa3-179">备份和还原和其他恢复选项自动通过 SharePoint Online 中的服务-备份将覆盖否则使用。</span><span class="sxs-lookup"><span data-stu-id="62fa3-179">Backup and restore and other recovery options are automated by the service in SharePoint Online - backups are overwritten if not used.</span></span>  <br/> |
|<span data-ttu-id="62fa3-180">安全测试和服务器性能优化持续服务中由执行 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="62fa3-180">Security testing and server performance tuning are carried out on an ongoing basis in the service by Microsoft.</span></span>  <br/> |<span data-ttu-id="62fa3-181">对用户界面和其他 SharePoint 功能安装服务，可能需要进行切换打开或关闭的更改。</span><span class="sxs-lookup"><span data-stu-id="62fa3-181">Changes to the user interface and other SharePoint features are installed by the service and may need to be toggled on or off.</span></span>  <br/> |
|<span data-ttu-id="62fa3-182">Office 365 满足很多行业标准： [Office 365 合规性](https://go.microsoft.com/fwlink/?linkid=843165)。</span><span class="sxs-lookup"><span data-stu-id="62fa3-182">Office 365 meets many industry standards: [Office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).</span></span>  <br/> |<span data-ttu-id="62fa3-183">迁移[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)协助是有限的。</span><span class="sxs-lookup"><span data-stu-id="62fa3-183">[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) assistance for migration is limited.</span></span>  <br/> <span data-ttu-id="62fa3-184">大部分升级将手动，或通过 SPO 迁移 API 中所述的[SharePoint Online 和 OneDrive 迁移内容指南](https://go.microsoft.com/fwlink/?linkid=843184)。</span><span class="sxs-lookup"><span data-stu-id="62fa3-184">Much of the upgrade will be manual, or via the SPO Migration API described in the [SharePoint Online and OneDrive Migration Content Roadmap](https://go.microsoft.com/fwlink/?linkid=843184).</span></span>  <br/> |
|<span data-ttu-id="62fa3-185">Microsoft 支持工程师和数据中心中的员工都不具有无管理员访问权限限制到您的订阅。</span><span class="sxs-lookup"><span data-stu-id="62fa3-185">Neither Microsoft Support Engineers nor employees in the datacenter have unrestricted admin access to your subscription.</span></span>  <br/> |<span data-ttu-id="62fa3-186">如果硬件基础结构需要升级以支持使用较新版本的 SharePoint，或者如果辅助服务器场上的升级需要，可以是额外的成本。</span><span class="sxs-lookup"><span data-stu-id="62fa3-186">There can be additional costs if hardware infrastructure needs to be upgraded to support the newer version of SharePoint, or if a secondary farm is required for upgrade.</span></span>  <br/> |
|<span data-ttu-id="62fa3-187">合作伙伴可与一次性作业将数据迁移到 SharePoint Online 的帮助。</span><span class="sxs-lookup"><span data-stu-id="62fa3-187">Partners can assist with the one-time job of migrating your data to SharePoint Online.</span></span>  <br/> ||
|<span data-ttu-id="62fa3-188">联机产品会自动更新跨这意味着可能废弃功能，但没有任何结束，则返回 true 的支持的服务。</span><span class="sxs-lookup"><span data-stu-id="62fa3-188">Online products are updated automatically across the service meaning that though features may deprecate, there is no true end of support.</span></span>  <br/> ||
   
<span data-ttu-id="62fa3-189">如果您决定创建新的 Office 365 网站，并将手动将数据迁移到它所需，您可以查看您的 Office 365 选项权利：</span><span class="sxs-lookup"><span data-stu-id="62fa3-189">If you've decided to create a new Office 365 site, and will manually migrate data to it as is needed, you can look at your Office 365 options right here:</span></span>
  
[<span data-ttu-id="62fa3-190">Office 365 计划选项</span><span class="sxs-lookup"><span data-stu-id="62fa3-190">Office 365 Plan Options</span></span>](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a><span data-ttu-id="62fa3-191">升级 SharePoint Server 内部部署</span><span class="sxs-lookup"><span data-stu-id="62fa3-191">Upgrade SharePoint Server on-premises</span></span>

<span data-ttu-id="62fa3-p114">没有过去方法以跳过 SharePoint 升级中至少截止 SharePoint Server 2016 版的版本。这意味着升级顺次转：</span><span class="sxs-lookup"><span data-stu-id="62fa3-p114">There is historically no way to skip versions in SharePoint Upgrades, at least not as of the release of SharePoint Server 2016. That means upgrades go serially:</span></span>
  
|||
|:-----|:-----|
||<span data-ttu-id="62fa3-194">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="62fa3-194">SharePoint 2007</span></span> | <span data-ttu-id="62fa3-195">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="62fa3-195">SharePoint Server 2010</span></span> | <span data-ttu-id="62fa3-196">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="62fa3-196">SharePoint Server 2013</span></span> | <span data-ttu-id="62fa3-197">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="62fa3-197">SharePoint Server 2016</span></span> |
   
<span data-ttu-id="62fa3-p115">要执行的完整路径，从 SharePoint 2007 到 SharePoint Server 2016 将意味着的时间投入大量资金和涉及将成本方面 （注意 SQL 服务器也必须进行升级） 的已升级硬件、 软件和管理。自定义项需要升级或放弃，根据该功能的关键程度。</span><span class="sxs-lookup"><span data-stu-id="62fa3-p115">To take the entire path from SharePoint 2007 to SharePoint Server 2016 will mean a significant investment of time and will involve a cost in terms of upgraded hardware (be aware that SQL servers must also be upgraded), software, and administration. Customizations will need to be upgraded or abandoned, according to the criticality of the feature.</span></span>
  
> [!NOTE]
> <span data-ttu-id="62fa3-p116">可以维护生命周期结束 SharePoint 2007 服务器场、 安装 SharePoint Server 2016 场在新硬件上 （以便在单独的服务器场运行的并行），然后规划和执行手动 （对于下载和重新将内容上载的内容的迁移示例）。注意一些手动移动 （如移动的文档的最后一个修改的帐户替换执行手动移动操作的帐户的别名），以及提早制定 （如重新创建网站、 子网站、 权限和列表必须完成的工时陷阱结构）。同样，这是应考虑哪些数据，您可以将它们移动到存储，或不再需要，可以减少迁移的影响操作的时间。</span><span class="sxs-lookup"><span data-stu-id="62fa3-p116">It's possible to maintain your end-of-life SharePoint 2007 farm, install a SharePoint Server 2016 farm on new hardware (so the separate farms run side-by-side), and then plan and execute a manual migration of content (for downloading and re-uploading content, for example). Be aware of some of the gotchas of manual moves (such as moves of documents replacing the last modified account with the alias of the account doing the manual move), and the work that must be done ahead of time (such as recreating sites, sub-sites, permissions and list structures). Again, this is the time to consider what data you can move into storage, or no longer need, an action that can reduce the impact of migration.</span></span>
  
<span data-ttu-id="62fa3-p117">无论进行上述，清理升级您的环境之前。在某些现有服务器场升级，才能正常运行，并且 （确定） 之前停用 ！</span><span class="sxs-lookup"><span data-stu-id="62fa3-p117">Either way, clean your environment prior to upgrade. Be certain your existing farm is functional before you upgrade, and (for sure) before you decommission!</span></span> 
  
<span data-ttu-id="62fa3-205">请记住，若要查看**支持和不支持的升级途径**：</span><span class="sxs-lookup"><span data-stu-id="62fa3-205">Remember to review the **supported and unsupported upgrade paths**:</span></span> 
  
- <span data-ttu-id="62fa3-206">
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)</span><span class="sxs-lookup"><span data-stu-id="62fa3-206">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)</span></span>
    
- [<span data-ttu-id="62fa3-207">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="62fa3-207">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="62fa3-208">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="62fa3-208">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843157)
    
<span data-ttu-id="62fa3-209">如果您有**自定义项**，它非常重要的迁移路径中有一个计划升级每个步骤：</span><span class="sxs-lookup"><span data-stu-id="62fa3-209">If you have **customizations**, it's critical you have a plan your upgrade for each step in the migration path:</span></span> 
  
- [<span data-ttu-id="62fa3-210">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="62fa3-210">SharePoint 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [<span data-ttu-id="62fa3-211">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="62fa3-211">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [<span data-ttu-id="62fa3-212">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="62fa3-212">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843162)
    
|<span data-ttu-id="62fa3-213">**内部部署 Pro**</span><span class="sxs-lookup"><span data-stu-id="62fa3-213">**On-premises Pro**</span></span>|<span data-ttu-id="62fa3-214">**在本地手段**</span><span class="sxs-lookup"><span data-stu-id="62fa3-214">**On-premises Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="62fa3-215">完全控制权限的 SharePoint 服务器场，从服务器硬件上的所有方面。</span><span class="sxs-lookup"><span data-stu-id="62fa3-215">Full control of all aspects of your SharePoint Farm, from the server hardware up.</span></span>  <br/> |<span data-ttu-id="62fa3-216">如果您的产品不支持的末尾 （可以使用付费的 Microsoft 支持） 贵公司负责所有页符和修补程序：</span><span class="sxs-lookup"><span data-stu-id="62fa3-216">All breaks and fixes are the responsibility of your company (can engage paid Microsoft Support if your product is not at end of support):</span></span>  <br/> |
|<span data-ttu-id="62fa3-217">SharePoint Server 的完整功能集在本地与 SharePoint Online 订阅通过混合连接的本地服务器场的选项。</span><span class="sxs-lookup"><span data-stu-id="62fa3-217">Full feature set of SharePoint Server on-premises with the option to connect your on-premises farm to a SharePoint Online subscription via hybrid.</span></span>  <br/> |<span data-ttu-id="62fa3-218">升级、 修补程序、 安全修补程序和 SharePoint Server 的所有维护托管在本地。</span><span class="sxs-lookup"><span data-stu-id="62fa3-218">Upgrade, patches, security fixes, and all maintenance of SharePoint Server managed on-premises.</span></span>  <br/> |
|<span data-ttu-id="62fa3-219">更高版本的自定义的完全访问权限。</span><span class="sxs-lookup"><span data-stu-id="62fa3-219">Full access for greater customization.</span></span>  <br/> |<span data-ttu-id="62fa3-220">[支持的 Office 365 的合规性标准](https://go.microsoft.com/fwlink/?linkid=843165)必须是本地手动配置。</span><span class="sxs-lookup"><span data-stu-id="62fa3-220">[Compliance standards supported by Office 365](https://go.microsoft.com/fwlink/?linkid=843165) must be manually configured on-premises.</span></span>  <br/> |
|<span data-ttu-id="62fa3-221">安全，执行测试和服务器性能调整，在您的本地 （的控制之下是）。</span><span class="sxs-lookup"><span data-stu-id="62fa3-221">Security testing, and server performance tuning, carried out on your premises (is under your control).</span></span>  <br/> |<span data-ttu-id="62fa3-222">Office 365 可能使功能可供 SharePoint Online 的不能与部署 SharePoint Server 互操作</span><span class="sxs-lookup"><span data-stu-id="62fa3-222">Office 365 may make features available to SharePoint Online that do not interoperate with SharePoint Server on-premises</span></span>  <br/> |
|<span data-ttu-id="62fa3-223">合作伙伴可帮助迁移到下一个版本的 SharePoint Server （及其他认证实战） 的数据。</span><span class="sxs-lookup"><span data-stu-id="62fa3-223">Partners can assist with migrating data to the next version of SharePoint Server (and beyond).</span></span>  <br/> |<span data-ttu-id="62fa3-224">SharePoint Server 网站不会自动使用[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)证书中所示是 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="62fa3-224">Your SharePoint Server sites will not automatically use [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) certificates as is seen in SharePoint Online.</span></span>  <br/> |
|<span data-ttu-id="62fa3-225">完全控制权限的命名约定、 备份和还原和部署 SharePoint Server 中的其他恢复选项。</span><span class="sxs-lookup"><span data-stu-id="62fa3-225">Full control of naming conventions, backup and restore and other recovery options in SharePoint Server on-premises.</span></span>  <br/> |<span data-ttu-id="62fa3-226">SharePoint Server 本地非常重视产品生命周期。</span><span class="sxs-lookup"><span data-stu-id="62fa3-226">SharePoint Server on-premises is sensitive to product lifecycles.</span></span>  <br/> |
   
### <a name="upgrade-resources"></a><span data-ttu-id="62fa3-227">升级的资源</span><span class="sxs-lookup"><span data-stu-id="62fa3-227">Upgrade Resources</span></span>

<span data-ttu-id="62fa3-228">首先了解您是否满足硬件和软件要求，然后按照支持的升级方法。</span><span class="sxs-lookup"><span data-stu-id="62fa3-228">Begin by knowing that you meet hardware and software requirements, then follow supported upgrade methods.</span></span>
  
- <span data-ttu-id="62fa3-229">**硬件/软件要求**：</span><span class="sxs-lookup"><span data-stu-id="62fa3-229">**Hardware/software requirements for**:</span></span> 
    
    <span data-ttu-id="62fa3-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span><span class="sxs-lookup"><span data-stu-id="62fa3-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span></span>
    
- <span data-ttu-id="62fa3-231">**软件边界和限制**：</span><span class="sxs-lookup"><span data-stu-id="62fa3-231">**Software boundaries and limits for**:</span></span> 
    
    <span data-ttu-id="62fa3-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span><span class="sxs-lookup"><span data-stu-id="62fa3-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span></span>
    
- <span data-ttu-id="62fa3-233">**升级过程概述**：</span><span class="sxs-lookup"><span data-stu-id="62fa3-233">**The upgrade process overview for**:</span></span> 
    
    <span data-ttu-id="62fa3-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span><span class="sxs-lookup"><span data-stu-id="62fa3-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span></span>
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a><span data-ttu-id="62fa3-235">创建 SharePoint Online 和本地之间的 SharePoint 混合解决方案</span><span class="sxs-lookup"><span data-stu-id="62fa3-235">Create a SharePoint hybrid solution between SharePoint Online and on-premises</span></span>

<span data-ttu-id="62fa3-p118">如果迁移需要的答案位于内部部署，并提供的 SharePoint Online 的所有权降低成本提供自我之间，您可以 SharePoint Server 2013 或 2016年场通过连接到 SharePoint Online、 混合。[了解 SharePoint 混合解决方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)</span><span class="sxs-lookup"><span data-stu-id="62fa3-p118">If the answer to your migration needs is somewhere between the self-control offered by on-premises, and the lower cost of ownership offered by SharePoint Online, you can connect SharePoint Server 2013 or 2016 farms to SharePoint Online, through hybrids. [Learn about SharePoint hybrid solutions](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)</span></span>
  
<span data-ttu-id="62fa3-238">如果您决定混合 SharePoint 服务器场受益业务，熟悉一下现有的混合以及如何配置您的本地 SharePoint 场和 Office 365 订阅之间的连接类型。</span><span class="sxs-lookup"><span data-stu-id="62fa3-238">If you decide that a hybrid SharePoint Server farm will benefit your business, familiarize yourself with the existing types of hybrid and how to configure the connection between your on-premises SharePoint farm and your Office 365 subscription.</span></span>
  
<span data-ttu-id="62fa3-p119">请参阅原理一个好方法是通过创建[Office 365 开发/测试环境](https://go.microsoft.com/fwlink/?linkid=843152)。一旦您具有试用版或购买 Office 365 订阅，您就会在您的方式在 SharePoint Online，您可以向其迁移数据中创建网站集、 web 和文档库 (请手动，通过使用的迁移 api，或-如果您想要迁移我网站内容到 OneDrive for Business-通过混合向导）。</span><span class="sxs-lookup"><span data-stu-id="62fa3-p119">One good way to see how this works is by creating an [Office 365 dev/test environment](https://go.microsoft.com/fwlink/?linkid=843152). Once you have a trial or purchased Office 365 subscription, you'll be on your way to creating the site collections, webs, and document libraries in SharePoint Online to which you can migrate data (either manually, by use of the Migration API, or - if you want to migrate My Site content to OneDrive for Business - through the hybrid wizard).</span></span>
  
> [!NOTE]
> <span data-ttu-id="62fa3-241">请记住，SharePoint 2007 服务器场需要升级，本地、 SharePoint Server 2013 或 SharePoint Server 2016 用于混合选项</span><span class="sxs-lookup"><span data-stu-id="62fa3-241">Remember that your SharePoint 2007 farm will need to be upgraded, on-premises, to either SharePoint Server 2013 or SharePoint Server 2016 to use the hybrid option</span></span> 
  
## <a name="related-topics"></a><span data-ttu-id="62fa3-242">相关主题</span><span class="sxs-lookup"><span data-stu-id="62fa3-242">Related topics</span></span>

[<span data-ttu-id="62fa3-243">疑难解答和继续升级 (Office SharePoint Server 2007)</span><span class="sxs-lookup"><span data-stu-id="62fa3-243">Troubleshoot and resume upgrade (Office SharePoint Server 2007)</span></span>](https://go.microsoft.com/fwlink/?linkid=843192)
  
[<span data-ttu-id="62fa3-244">解决升级问题 (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="62fa3-244">Troubleshoot upgrade issues (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?linkid=843194)
  
[<span data-ttu-id="62fa3-245">在 SharePoint 2013 中解决数据库升级问题</span><span class="sxs-lookup"><span data-stu-id="62fa3-245">Troubleshoot database upgrade issues in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843195)
  
[<span data-ttu-id="62fa3-246">搜索 Microsoft 合作伙伴，从而帮助进行升级</span><span class="sxs-lookup"><span data-stu-id="62fa3-246">Search for Microsoft Partners to help with Upgrade</span></span>](https://go.microsoft.com/fwlink/?linkid=841249)
  
[<span data-ttu-id="62fa3-247">资源可帮助您升级从 Office 2007 的服务器和客户端</span><span class="sxs-lookup"><span data-stu-id="62fa3-247">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  

