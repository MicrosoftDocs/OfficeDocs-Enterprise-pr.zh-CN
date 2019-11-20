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
ms.openlocfilehash: 1b7b2ccf1bbda5210e563a4cd702ebd90b9f8f5d
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747311"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a><span data-ttu-id="8147c-104">SharePoint Server 2007 停止提供支持路线图</span><span class="sxs-lookup"><span data-stu-id="8147c-104">SharePoint Server 2007 end of support roadmap</span></span>

<span data-ttu-id="8147c-105">*本文适用于 Office 365 企业版和 Microsoft 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="8147c-105">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="8147c-106">在**2017 年10月 10**日，Microsoft Office SharePoint Server 2007 已到达支持终止。</span><span class="sxs-lookup"><span data-stu-id="8147c-106">On **October 10, 2017**, Microsoft Office SharePoint Server 2007 reached end of support.</span></span> <span data-ttu-id="8147c-107">如果尚未开始从 SharePoint Server 2007 迁移到 Office 365 或 SharePoint Server 本地版本的新版本，现在是开始规划的时间。</span><span class="sxs-lookup"><span data-stu-id="8147c-107">If you haven't begun your migration from SharePoint Server 2007 to Office 365 or a newer version of SharePoint Server on-premises, now's the time to start planning.</span></span> <span data-ttu-id="8147c-108">本文详细介绍了帮助用户将数据迁移到 SharePoint Online 或在本地升级 SharePoint Server 的资源。</span><span class="sxs-lookup"><span data-stu-id="8147c-108">This article details resources to help people migrate data to SharePoint Online, or upgrade your SharePoint Server on-premises.</span></span> 
  
## <a name="what-does-end-of-support-mean"></a><span data-ttu-id="8147c-109">支持终止的含义是什么？</span><span class="sxs-lookup"><span data-stu-id="8147c-109">What does end of support mean?</span></span>

<span data-ttu-id="8147c-110">SharePoint Server （如几乎所有 Microsoft 产品）都具有支持生命周期，在此期间，Microsoft 提供了新的功能、缺陷修补程序、安全修补程序等。</span><span class="sxs-lookup"><span data-stu-id="8147c-110">SharePoint Server, like almost all Microsoft products, has a support lifecycle during which Microsoft provides new features, bug fixes, security fixes, and so on.</span></span> <span data-ttu-id="8147c-111">此生命周期通常是从产品初始发布之日起10年的时间，而此生命周期的结束时间也称为产品的支持终止的期限。</span><span class="sxs-lookup"><span data-stu-id="8147c-111">This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support.</span></span> <span data-ttu-id="8147c-112">在支持结束后，Microsoft 将不再提供：</span><span class="sxs-lookup"><span data-stu-id="8147c-112">At end of support, Microsoft no longer provides:</span></span>
  
- <span data-ttu-id="8147c-113">可能出现的问题的技术支持;</span><span class="sxs-lookup"><span data-stu-id="8147c-113">Technical support for problems that may occur;</span></span>
    
- <span data-ttu-id="8147c-114">针对已发现且可能影响服务器的稳定性和可用性的问题的 Bug 修补程序。</span><span class="sxs-lookup"><span data-stu-id="8147c-114">Bug fixes for issues that are discovered and that may impact the stability and usability of the server;</span></span>
    
- <span data-ttu-id="8147c-115">已发现的漏洞安全修补程序以及可能会使服务器易受安全威胁的安全修补程序。并</span><span class="sxs-lookup"><span data-stu-id="8147c-115">Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches; and</span></span> 
    
- <span data-ttu-id="8147c-116">时区更新。</span><span class="sxs-lookup"><span data-stu-id="8147c-116">Time zone updates.</span></span>
    
<span data-ttu-id="8147c-117">尽管您的 SharePoint Server 2007 服务器场在 2017 10 月10日后仍可正常运行，但不会为产品提供进一步的更新、修补程序或修补程序（包括安全修补程序/修补程序），并且 Microsoft 支持将把其支持工作完全转移到产品的较新版本。</span><span class="sxs-lookup"><span data-stu-id="8147c-117">Though your SharePoint Server 2007 farm will still be operational after October 10, 2017, no further updates, patches, or fixes will be shipped for the product (including security patches/fixes), and Microsoft Support will have fully shifted its support efforts to more recent versions of the product.</span></span> <span data-ttu-id="8147c-118">由于你的安装将不再受支持或修补，因为支持方法的结束应升级产品或迁移重要数据。</span><span class="sxs-lookup"><span data-stu-id="8147c-118">Because your installation will no longer supported or patched, as end of support approaches you should upgrade the product, or migrate important data.</span></span>
  
> [!TIP]
> <span data-ttu-id="8147c-119">如果尚未计划升级或迁移，请参阅： [SharePoint 2007 迁移选项](sharepoint-2007-migration-options.md)，以了解开始位置的一些示例。</span><span class="sxs-lookup"><span data-stu-id="8147c-119">If you haven't already planned for upgrade or migration, please see: [SharePoint 2007 migration options to consider](sharepoint-2007-migration-options.md), for some examples of where to begin.</span></span> <span data-ttu-id="8147c-120">您还可以搜索可帮助升级或 Office 365 迁移的[Microsoft 合作伙伴](https://go.microsoft.com/fwlink/?linkid=841249)（或两者）。</span><span class="sxs-lookup"><span data-stu-id="8147c-120">You can also search for [Microsoft Partners](https://go.microsoft.com/fwlink/?linkid=841249) who can help with upgrade or Office 365 migration (or both).</span></span> 
  
<span data-ttu-id="8147c-121">有关支持结束支持的 Office 2007 服务器的详细信息，请参阅可[帮助您从 Office 2007 服务器和客户端进行升级的资源](upgrade-from-office-2007-servers-and-products.md)。</span><span class="sxs-lookup"><span data-stu-id="8147c-121">For more information about Office 2007 servers reaching the end of support, see [Resources to help you upgrade from Office 2007 servers and clients](upgrade-from-office-2007-servers-and-products.md).</span></span>
  
## <a name="what-are-my-options"></a><span data-ttu-id="8147c-122">我的选项是什么？</span><span class="sxs-lookup"><span data-stu-id="8147c-122">What are my options?</span></span>

<span data-ttu-id="8147c-123">您的第一位应是[产品生命周期网站](https://go.microsoft.com/fwlink/?linkid=843148)。</span><span class="sxs-lookup"><span data-stu-id="8147c-123">Your first stop should be the [Product Lifecycle site](https://go.microsoft.com/fwlink/?linkid=843148).</span></span> <span data-ttu-id="8147c-124">如果你的本地 Microsoft 产品是老化的，则应检查其支持日期的结束日期，以便在你的迁移通常需要一年或更长时间后，或在你的迁移过程中安排升级或迁移。</span><span class="sxs-lookup"><span data-stu-id="8147c-124">If you have an on-premises Microsoft product that is aging, you should check for its end of support date so that, a year or so out - or as long as your migrations generally require - you can schedule upgrade or migrations.</span></span> <span data-ttu-id="8147c-125">在选择下一步时，它可能会帮助您了解什么是足够好、更好，并且在产品功能方面最适合。</span><span class="sxs-lookup"><span data-stu-id="8147c-125">When choosing the next step, it might help to think in terms of what would be good enough, better, and best when it comes to product features.</span></span> <span data-ttu-id="8147c-126">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="8147c-126">Here's an example:</span></span>
  
|<span data-ttu-id="8147c-127">**Good**</span><span class="sxs-lookup"><span data-stu-id="8147c-127">**Good**</span></span>|<span data-ttu-id="8147c-128">**能**</span><span class="sxs-lookup"><span data-stu-id="8147c-128">**Better**</span></span>|<span data-ttu-id="8147c-129">**最好**</span><span class="sxs-lookup"><span data-stu-id="8147c-129">**Best**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8147c-130">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="8147c-130">SharePoint Server 2010</span></span>  <br/> |<span data-ttu-id="8147c-131">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="8147c-131">SharePoint Server 2013</span></span>  <br/> |<span data-ttu-id="8147c-132">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8147c-132">SharePoint Online</span></span>  <br/> |
||<span data-ttu-id="8147c-133">SharePoint 混合</span><span class="sxs-lookup"><span data-stu-id="8147c-133">SharePoint Hybrid</span></span>  <br/> |<span data-ttu-id="8147c-134">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="8147c-134">SharePoint Server 2016</span></span>  <br/> |
|||<span data-ttu-id="8147c-135">SharePoint 混合</span><span class="sxs-lookup"><span data-stu-id="8147c-135">SharePoint Hybrid</span></span>  <br/> |
   
<span data-ttu-id="8147c-136">如果你在规模的低端（足够好）选择选项，请记住，从 SharePoint Server 2007 迁移完成后，你将需要立即开始规划升级。</span><span class="sxs-lookup"><span data-stu-id="8147c-136">If you choose options on the low end of the scale (good enough), remember you will need to begin planning for upgrade very soon after migration from SharePoint Server 2007 is complete.</span></span> <span data-ttu-id="8147c-137">（SharePoint Server 2007 支持的结尾为10月10日，2017。</span><span class="sxs-lookup"><span data-stu-id="8147c-137">(end of support for SharePoint Server 2007 is October 10, 2017.</span></span> <span data-ttu-id="8147c-138">请注意，这些日期可能会发生更改，并可检查[产品生命周期网站](https://support.microsoft.com/lifecycle)。</span><span class="sxs-lookup"><span data-stu-id="8147c-138">Please note that these dates are subject to change and check the [Product Lifecycle site](https://support.microsoft.com/lifecycle).)</span></span>
  
## <a name="where-can-i-go-next"></a><span data-ttu-id="8147c-139">接下来如何操作？</span><span class="sxs-lookup"><span data-stu-id="8147c-139">Where can I go next?</span></span>

<span data-ttu-id="8147c-140">可以在自己的服务器上将 SharePoint Server 安装在本地，也可以使用 SharePoint Online，这是 Microsoft Office 365 的一部分的联机服务。</span><span class="sxs-lookup"><span data-stu-id="8147c-140">SharePoint Server can be installed on-premises on your own servers, or you can use SharePoint Online, which is an online service that is part of Microsoft Office 365.</span></span> <span data-ttu-id="8147c-141">您可以选择执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8147c-141">You can choose to:</span></span>
  
- <span data-ttu-id="8147c-142">迁移到 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8147c-142">Migrate to SharePoint Online</span></span>
    
- <span data-ttu-id="8147c-143">升级本地 SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="8147c-143">Upgrade SharePoint Server on-premises</span></span>
    
- <span data-ttu-id="8147c-144">执行上述两项操作</span><span class="sxs-lookup"><span data-stu-id="8147c-144">Do both of the above</span></span>
    
- <span data-ttu-id="8147c-145">实现[SharePoint 混合](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)解决方案</span><span class="sxs-lookup"><span data-stu-id="8147c-145">Implement a [SharePoint hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) solution</span></span> 
    
<span data-ttu-id="8147c-146">了解与维护服务器场以继续、维护或迁移自定义设置以及升级 SharePoint Server 所依赖的硬件相关的隐藏成本。</span><span class="sxs-lookup"><span data-stu-id="8147c-146">Be aware of hidden costs associated with maintaining a server farm going forward, maintaining or migrating customizations, and upgrading the hardware upon which SharePoint Server depends.</span></span> <span data-ttu-id="8147c-147">如果是必需的，则为内部部署 SharePoint Server 服务器场进行奖励;否则，如果在旧版 SharePoint 服务器上运行服务器场，而不进行大量自定义，则可以从计划迁移到 SharePoint Online 中受益。</span><span class="sxs-lookup"><span data-stu-id="8147c-147">Having an on-premises SharePoint Server farm is rewarding if it is a necessity; otherwise, if you run your farm on legacy SharePoint Servers, without heavy customization, you can benefit from a planned migration to SharePoint Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="8147c-148">如果不经常使用 SharePoint 2007 中的内容，也可以选择另一个选项。</span><span class="sxs-lookup"><span data-stu-id="8147c-148">There is another option if the content in SharePoint 2007 is infrequently used.</span></span> <span data-ttu-id="8147c-149">某些 SharePoint 管理员可以选择[创建 Office 365 订阅](https://go.microsoft.com/fwlink/?linkid=843152)，设置全新的 SharePoint Online 网站，然后将其完全从 sharepoint 2007 中裁出，将最重要的文档完全从 sharepoint online 网站中删除。</span><span class="sxs-lookup"><span data-stu-id="8147c-149">Some SharePoint Administrators may choose to [create an Office 365 Subscription](https://go.microsoft.com/fwlink/?linkid=843152), set up a brand new SharePoint Online site, and then cut away from SharePoint 2007, cleanly, taking only the most essential documents to the fresh SharePoint Online sites.</span></span> <span data-ttu-id="8147c-150">从这里可以将数据从 SharePoint 2007 网站中排出到存档中。</span><span class="sxs-lookup"><span data-stu-id="8147c-150">From there, data may be drained from the SharePoint 2007 site into archives.</span></span> <span data-ttu-id="8147c-151">请考虑用户如何使用 SharePoint 2007 安装数据。</span><span class="sxs-lookup"><span data-stu-id="8147c-151">Give thought to how users work with data your SharePoint 2007 installation.</span></span> <span data-ttu-id="8147c-152">可能有一些创造性的方法可以解决此问题！</span><span class="sxs-lookup"><span data-stu-id="8147c-152">There may be creative ways to resolve this problem!</span></span> 
  
|<span data-ttu-id="8147c-153">**SharePoint Online （SPO）**</span><span class="sxs-lookup"><span data-stu-id="8147c-153">**SharePoint Online (SPO)**</span></span>|<span data-ttu-id="8147c-154">**SharePoint Server 本地**</span><span class="sxs-lookup"><span data-stu-id="8147c-154">**SharePoint Server on-premises**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8147c-155">较高的时间成本（规划/执行/验证）</span><span class="sxs-lookup"><span data-stu-id="8147c-155">High cost in time (plan / execution / verification)</span></span>  <br/> |<span data-ttu-id="8147c-156">较高的时间成本（规划/执行/验证）</span><span class="sxs-lookup"><span data-stu-id="8147c-156">High cost in time (plan / execution / verification)</span></span>  <br/> |
|<span data-ttu-id="8147c-157">降低资金成本（无需购买硬件）</span><span class="sxs-lookup"><span data-stu-id="8147c-157">Lower cost in funds (no hardware purchases)</span></span>  <br/> |<span data-ttu-id="8147c-158">资金成本较高（硬件 + devs/管理员）</span><span class="sxs-lookup"><span data-stu-id="8147c-158">Higher cost in funds (hardware + devs / admins)</span></span>  <br/> |
|<span data-ttu-id="8147c-159">迁移的一次性成本</span><span class="sxs-lookup"><span data-stu-id="8147c-159">One-time cost in migration</span></span>  <br/> |<span data-ttu-id="8147c-160">每次迁移时重复的一次性成本</span><span class="sxs-lookup"><span data-stu-id="8147c-160">One-time cost repeated per future migration</span></span>  <br/> |
|<span data-ttu-id="8147c-161">低总拥有成本/维护</span><span class="sxs-lookup"><span data-stu-id="8147c-161">Low total cost of ownership / maintenance</span></span>  <br/> |<span data-ttu-id="8147c-162">高总拥有成本/维护</span><span class="sxs-lookup"><span data-stu-id="8147c-162">High total cost of ownership / maintenance</span></span>  <br/> |
   
<span data-ttu-id="8147c-163">当迁移到 Office 365 时，一次性移动将具有较高的成本，而您可以对数据进行组织，并决定要对云执行哪些操作以及留下哪些内容。</span><span class="sxs-lookup"><span data-stu-id="8147c-163">When you migrate to Office 365, the one-time move will have a heavier cost up-front, while you're organizing data and deciding what to take to the cloud and what to leave behind.</span></span> <span data-ttu-id="8147c-164">但是，升级将从该点自动进行，你将不再需要管理硬件和软件更新，并且你的服务器场的启动时间将由 Microsoft 服务级别协议（[SLA](https://go.microsoft.com/fwlink/?linkid=843153)）进行支持。</span><span class="sxs-lookup"><span data-stu-id="8147c-164">However, upgrades will be automatic from that point, you will no longer need to manage hardware and software updates, and the up-time of your farm will be backed by a Microsoft Service Level Agreement ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).</span></span>
  
### <a name="migrate-to-sharepoint-online"></a><span data-ttu-id="8147c-165">迁移到 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8147c-165">Migrate to SharePoint Online</span></span>

<span data-ttu-id="8147c-166">通过查看关联的服务说明，确保 SharePoint Online 具有你所需的所有功能。</span><span class="sxs-lookup"><span data-stu-id="8147c-166">Make sure that SharePoint Online has all the features you need by reviewing the associated service description.</span></span> <span data-ttu-id="8147c-167">以下是指向所有 Office 365 服务说明的链接：</span><span class="sxs-lookup"><span data-stu-id="8147c-167">Here's the link to all Office 365 Service Descriptions:</span></span>
  
[<span data-ttu-id="8147c-168">Office 365 服务说明</span><span class="sxs-lookup"><span data-stu-id="8147c-168">Office 365 Service Descriptions</span></span>](https://go.microsoft.com/fwlink/?linkid=272060)
  
<span data-ttu-id="8147c-169">没有直接从 SharePoint 2007 迁移到 SharePoint Online 的方法;您的迁移到 SharePoint Online 将手动执行。</span><span class="sxs-lookup"><span data-stu-id="8147c-169">There is no direct way to migrate from SharePoint 2007 to SharePoint Online; your move to SharePoint Online would be done manually.</span></span> <span data-ttu-id="8147c-170">如果升级到 SharePoint Server 2013 或 SharePoint Server 2016，则移动可能还涉及使用 SharePoint 迁移 API （例如，将信息迁移到 OneDrive for Business）。</span><span class="sxs-lookup"><span data-stu-id="8147c-170">If you upgrade to SharePoint Server 2013 or SharePoint Server 2016, your move might also involve using the SharePoint Migration API (to migrate information into OneDrive for Business, for example).</span></span>
  
|<span data-ttu-id="8147c-171">**Online Pro**</span><span class="sxs-lookup"><span data-stu-id="8147c-171">**Online Pro**</span></span>|<span data-ttu-id="8147c-172">**联机 Con**</span><span class="sxs-lookup"><span data-stu-id="8147c-172">**Online Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8147c-173">Microsoft 提供 SPO 硬件和所有硬件管理。</span><span class="sxs-lookup"><span data-stu-id="8147c-173">Microsoft supplies SPO hardware and all hardware administration.</span></span>  <br/> |<span data-ttu-id="8147c-174">SharePoint Server 本地和 SPO 之间的可用功能可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="8147c-174">Available features may be different between SharePoint Server on-premises and SPO.</span></span>  <br/> |
|<span data-ttu-id="8147c-175">你是订阅的全局管理员，并且可能会向管理员分配 SPO 网站。</span><span class="sxs-lookup"><span data-stu-id="8147c-175">You are the global administrator of your subscription, and may assign administrators to SPO sites.</span></span>  <br/> |<span data-ttu-id="8147c-176">在 Office 365 的 SharePoint 管理员角色中，在本地 SharePoint Server 中对服务器场管理员可用的某些操作不存在（或不必要）。</span><span class="sxs-lookup"><span data-stu-id="8147c-176">Some actions available to a Farm Administrator in SharePoint Server on-premises do not exist (or are not necessary) included in the SharePoint Administrator role in Office 365.</span></span>  <br/> |
|<span data-ttu-id="8147c-177">Microsoft 对底层硬件和软件应用修补程序、修补程序和更新。</span><span class="sxs-lookup"><span data-stu-id="8147c-177">Microsoft applies patches, fixes and updates to underlying hardware and software.</span></span>  <br/> |<span data-ttu-id="8147c-178">由于对服务中的基础文件系统没有访问权限，因此某些自定义项受到限制。</span><span class="sxs-lookup"><span data-stu-id="8147c-178">Because there is no access to the underlying file system in the service, some customizations are limited.</span></span>  <br/> |
|<span data-ttu-id="8147c-179">Microsoft 发布[服务级别协议](https://go.microsoft.com/fwlink/?linkid=843153)并快速移动以解决服务级别事件。</span><span class="sxs-lookup"><span data-stu-id="8147c-179">Microsoft publishes [Service Level Agreements](https://go.microsoft.com/fwlink/?linkid=843153) and moves quickly to resolve service level incidents.</span></span>  <br/> |<span data-ttu-id="8147c-180">备份和还原和其他恢复选项通过 SharePoint Online 中的服务自动进行，如果不使用，则会覆盖备份。</span><span class="sxs-lookup"><span data-stu-id="8147c-180">Backup and restore and other recovery options are automated by the service in SharePoint Online - backups are overwritten if not used.</span></span>  <br/> |
|<span data-ttu-id="8147c-181">Microsoft 在服务中不断执行安全测试和服务器性能调整。</span><span class="sxs-lookup"><span data-stu-id="8147c-181">Security testing and server performance tuning are carried out on an ongoing basis in the service by Microsoft.</span></span>  <br/> |<span data-ttu-id="8147c-182">对用户界面和其他 SharePoint 功能的更改由服务安装，并且可能需要开启或关闭。</span><span class="sxs-lookup"><span data-stu-id="8147c-182">Changes to the user interface and other SharePoint features are installed by the service and may need to be toggled on or off.</span></span>  <br/> |
|<span data-ttu-id="8147c-183">Office 365 符合多种行业标准： [office 365 合规性](https://go.microsoft.com/fwlink/?linkid=843165)。</span><span class="sxs-lookup"><span data-stu-id="8147c-183">Office 365 meets many industry standards: [Office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).</span></span>  <br/> |<span data-ttu-id="8147c-184">迁移的[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)协助受到限制。</span><span class="sxs-lookup"><span data-stu-id="8147c-184">[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) assistance for migration is limited.</span></span>  <br/> <span data-ttu-id="8147c-185">大部分升级都是手动进行的，也可以通过[SharePoint Online 和 OneDrive 迁移内容路线图](https://go.microsoft.com/fwlink/?linkid=843184)中介绍的 SPO 迁移 API 进行。</span><span class="sxs-lookup"><span data-stu-id="8147c-185">Much of the upgrade will be manual, or via the SPO Migration API described in the [SharePoint Online and OneDrive Migration Content Roadmap](https://go.microsoft.com/fwlink/?linkid=843184).</span></span>  <br/> |
|<span data-ttu-id="8147c-186">Microsoft 支持工程师和数据中心中的员工都不受无限制地对订阅进行管理员访问。</span><span class="sxs-lookup"><span data-stu-id="8147c-186">Neither Microsoft Support Engineers nor employees in the datacenter have unrestricted admin access to your subscription.</span></span>  <br/> |<span data-ttu-id="8147c-187">如果需要升级硬件基础结构以支持较新版本的 SharePoint，或者如果升级需要辅助服务器场，则可能会有额外的成本。</span><span class="sxs-lookup"><span data-stu-id="8147c-187">There can be additional costs if hardware infrastructure needs to be upgraded to support the newer version of SharePoint, or if a secondary farm is required for upgrade.</span></span>  <br/> |
|<span data-ttu-id="8147c-188">合作伙伴可协助将数据迁移到 SharePoint Online 的一次性作业。</span><span class="sxs-lookup"><span data-stu-id="8147c-188">Partners can assist with the one-time job of migrating your data to SharePoint Online.</span></span>  <br/> ||
|<span data-ttu-id="8147c-189">在线产品是通过服务自动更新的，这意味着功能可能弃用，但不提供真正的支持结束。</span><span class="sxs-lookup"><span data-stu-id="8147c-189">Online products are updated automatically across the service meaning that though features may deprecate, there is no true end of support.</span></span>  <br/> ||
   
<span data-ttu-id="8147c-190">如果您已决定创建新的 Office 365 网站，并将在需要时手动将数据迁移到它，则可以在此处查看 Office 365 选项：</span><span class="sxs-lookup"><span data-stu-id="8147c-190">If you've decided to create a new Office 365 site, and will manually migrate data to it as is needed, you can look at your Office 365 options right here:</span></span>
  
[<span data-ttu-id="8147c-191">Office 365 计划选项</span><span class="sxs-lookup"><span data-stu-id="8147c-191">Office 365 Plan Options</span></span>](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a><span data-ttu-id="8147c-192">升级本地 SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="8147c-192">Upgrade SharePoint Server on-premises</span></span>

<span data-ttu-id="8147c-193">目前没有办法跳过 SharePoint 升级中的版本，至少是在发布 SharePoint Server 2016 时才会跳过。</span><span class="sxs-lookup"><span data-stu-id="8147c-193">There is historically no way to skip versions in SharePoint Upgrades, at least not as of the release of SharePoint Server 2016.</span></span> <span data-ttu-id="8147c-194">这意味着升级以串行方式进行：</span><span class="sxs-lookup"><span data-stu-id="8147c-194">That means upgrades go serially:</span></span>
  
|||
|:-----|:-----|
||<span data-ttu-id="8147c-195">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="8147c-195">SharePoint 2007</span></span> | <span data-ttu-id="8147c-196">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="8147c-196">SharePoint Server 2010</span></span> | <span data-ttu-id="8147c-197">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="8147c-197">SharePoint Server 2013</span></span> | <span data-ttu-id="8147c-198">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="8147c-198">SharePoint Server 2016</span></span> |
   
<span data-ttu-id="8147c-199">从 SharePoint 2007 迁移到 SharePoint Server 2016 的完整路径意味着需要大量的时间，并将在升级后的硬件方面产生成本（请注意，还必须升级 SQL server）、软件和管理。</span><span class="sxs-lookup"><span data-stu-id="8147c-199">To take the entire path from SharePoint 2007 to SharePoint Server 2016 will mean a significant investment of time and will involve a cost in terms of upgraded hardware (be aware that SQL servers must also be upgraded), software, and administration.</span></span> <span data-ttu-id="8147c-200">根据功能的关键程度，需要升级或放弃自定义项。</span><span class="sxs-lookup"><span data-stu-id="8147c-200">Customizations will need to be upgraded or abandoned, according to the criticality of the feature.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8147c-201">可以维护您的生命期结束的 SharePoint 2007 服务器场，在新硬件上安装 SharePoint Server 2016 场（因此单独的服务器场并行运行），然后规划和执行内容的手动迁移（用于下载和重新上载内容）示例）。</span><span class="sxs-lookup"><span data-stu-id="8147c-201">It's possible to maintain your end-of-life SharePoint 2007 farm, install a SharePoint Server 2016 farm on new hardware (so the separate farms run side-by-side), and then plan and execute a manual migration of content (for downloading and re-uploading content, for example).</span></span> <span data-ttu-id="8147c-202">了解手动移动的一些陷阱（例如，文档移动将上次修改的帐户替换为执行手动移动的帐户的别名）以及必须提前完成的工作（如重新创建网站、子网站、权限和列表）。结构）。</span><span class="sxs-lookup"><span data-stu-id="8147c-202">Be aware of some of the gotchas of manual moves (such as moves of documents replacing the last modified account with the alias of the account doing the manual move), and the work that must be done ahead of time (such as recreating sites, sub-sites, permissions and list structures).</span></span> <span data-ttu-id="8147c-203">同样，这也是考虑可以移动到存储或不再需要的数据的时间，可降低迁移影响的操作。</span><span class="sxs-lookup"><span data-stu-id="8147c-203">Again, this is the time to consider what data you can move into storage, or no longer need, an action that can reduce the impact of migration.</span></span>
  
<span data-ttu-id="8147c-204">无论哪种方式，都要在升级之前清理环境。</span><span class="sxs-lookup"><span data-stu-id="8147c-204">Either way, clean your environment prior to upgrade.</span></span> <span data-ttu-id="8147c-205">请确保你的现有服务器场在升级之前运行正常，并在停止之前（确保）运行！</span><span class="sxs-lookup"><span data-stu-id="8147c-205">Be certain your existing farm is functional before you upgrade, and (for sure) before you decommission!</span></span> 
  
<span data-ttu-id="8147c-206">请记住查看**支持的和不受支持的升级路径**：</span><span class="sxs-lookup"><span data-stu-id="8147c-206">Remember to review the **supported and unsupported upgrade paths**:</span></span> 
  
- [<span data-ttu-id="8147c-207">SharePoint Server 2007</span><span class="sxs-lookup"><span data-stu-id="8147c-207">SharePoint Server 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="8147c-208">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="8147c-208">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="8147c-209">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="8147c-209">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843157)
    
<span data-ttu-id="8147c-210">如果您具有**自定义项**，则在迁移路径中为每个步骤规划升级都很重要：</span><span class="sxs-lookup"><span data-stu-id="8147c-210">If you have **customizations**, it's critical you have a plan your upgrade for each step in the migration path:</span></span> 
  
- [<span data-ttu-id="8147c-211">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="8147c-211">SharePoint 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [<span data-ttu-id="8147c-212">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="8147c-212">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [<span data-ttu-id="8147c-213">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="8147c-213">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843162)
    
|<span data-ttu-id="8147c-214">**本地 Pro**</span><span class="sxs-lookup"><span data-stu-id="8147c-214">**On-premises Pro**</span></span>|<span data-ttu-id="8147c-215">**本地 Con**</span><span class="sxs-lookup"><span data-stu-id="8147c-215">**On-premises Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8147c-216">从服务器硬件上完全控制 SharePoint 场的各个方面。</span><span class="sxs-lookup"><span data-stu-id="8147c-216">Full control of all aspects of your SharePoint Farm, from the server hardware up.</span></span>  <br/> |<span data-ttu-id="8147c-217">所有中断和修复都是贵公司的责任（如果你的产品不在支持的基础上，可以与付费 Microsoft 支持部门联系）：</span><span class="sxs-lookup"><span data-stu-id="8147c-217">All breaks and fixes are the responsibility of your company (can engage paid Microsoft Support if your product is not at end of support):</span></span>  <br/> |
|<span data-ttu-id="8147c-218">SharePoint Server 本地的完整功能集以及通过混合将本地服务器场连接到 SharePoint Online 订阅的选项。</span><span class="sxs-lookup"><span data-stu-id="8147c-218">Full feature set of SharePoint Server on-premises with the option to connect your on-premises farm to a SharePoint Online subscription via hybrid.</span></span>  <br/> |<span data-ttu-id="8147c-219">在本地托管的 SharePoint Server 的升级、修补程序、安全修补程序和所有维护。</span><span class="sxs-lookup"><span data-stu-id="8147c-219">Upgrade, patches, security fixes, and all maintenance of SharePoint Server managed on-premises.</span></span>  <br/> |
|<span data-ttu-id="8147c-220">完全访问权限以进行更好的自定义。</span><span class="sxs-lookup"><span data-stu-id="8147c-220">Full access for greater customization.</span></span>  <br/> |<span data-ttu-id="8147c-221">[Office 365 支持的合规性标准](https://go.microsoft.com/fwlink/?linkid=843165)必须在本地手动配置。</span><span class="sxs-lookup"><span data-stu-id="8147c-221">[Compliance standards supported by Office 365](https://go.microsoft.com/fwlink/?linkid=843165) must be manually configured on-premises.</span></span>  <br/> |
|<span data-ttu-id="8147c-222">在您的内部部署（在您的控制之下）执行安全测试和服务器性能调整。</span><span class="sxs-lookup"><span data-stu-id="8147c-222">Security testing, and server performance tuning, carried out on your premises (is under your control).</span></span>  <br/> |<span data-ttu-id="8147c-223">Office 365 可能会对 SharePoint Online 可用的功能，这些功能无法与本地 SharePoint Server 进行互操作</span><span class="sxs-lookup"><span data-stu-id="8147c-223">Office 365 may make features available to SharePoint Online that do not interoperate with SharePoint Server on-premises</span></span>  <br/> |
|<span data-ttu-id="8147c-224">合作伙伴可协助将数据迁移到 SharePoint Server 的下一个版本（和更高版本）。</span><span class="sxs-lookup"><span data-stu-id="8147c-224">Partners can assist with migrating data to the next version of SharePoint Server (and beyond).</span></span>  <br/> |<span data-ttu-id="8147c-225">您的 SharePoint Server 网站不会自动使用在 SharePoint Online 中显示的[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)证书。</span><span class="sxs-lookup"><span data-stu-id="8147c-225">Your SharePoint Server sites will not automatically use [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) certificates as is seen in SharePoint Online.</span></span>  <br/> |
|<span data-ttu-id="8147c-226">在本地 SharePoint Server 中完全控制命名约定、备份和还原以及其他恢复选项。</span><span class="sxs-lookup"><span data-stu-id="8147c-226">Full control of naming conventions, backup and restore and other recovery options in SharePoint Server on-premises.</span></span>  <br/> |<span data-ttu-id="8147c-227">本地 SharePoint Server 对产品生命周期非常敏感。</span><span class="sxs-lookup"><span data-stu-id="8147c-227">SharePoint Server on-premises is sensitive to product lifecycles.</span></span>  <br/> |
   
### <a name="upgrade-resources"></a><span data-ttu-id="8147c-228">升级资源</span><span class="sxs-lookup"><span data-stu-id="8147c-228">Upgrade Resources</span></span>

<span data-ttu-id="8147c-229">先知道您是否满足硬件和软件要求，然后再遵循受支持的升级方法。</span><span class="sxs-lookup"><span data-stu-id="8147c-229">Begin by knowing that you meet hardware and software requirements, then follow supported upgrade methods.</span></span>
  
- <span data-ttu-id="8147c-230">**的硬件/软件要求**：</span><span class="sxs-lookup"><span data-stu-id="8147c-230">**Hardware/software requirements for**:</span></span> 
    
    <span data-ttu-id="8147c-231">[Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | sharepoint server[2010](https://go.microsoft.com/fwlink/?linkid=843204) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span><span class="sxs-lookup"><span data-stu-id="8147c-231">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span></span>
    
- <span data-ttu-id="8147c-232">**的软件边界和限制**：</span><span class="sxs-lookup"><span data-stu-id="8147c-232">**Software boundaries and limits for**:</span></span> 
    
    <span data-ttu-id="8147c-233">[Sharepoint server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | sharepoint server[2010](https://go.microsoft.com/fwlink/?linkid=843247) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span><span class="sxs-lookup"><span data-stu-id="8147c-233">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span></span>
    
- <span data-ttu-id="8147c-234">以下项**的升级过程概述**：</span><span class="sxs-lookup"><span data-stu-id="8147c-234">**The upgrade process overview for**:</span></span> 
    
    <span data-ttu-id="8147c-235">[Sharepoint server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | sharepoint server[2010](https://go.microsoft.com/fwlink/?linkid=843251) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span><span class="sxs-lookup"><span data-stu-id="8147c-235">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span></span>
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a><span data-ttu-id="8147c-236">在 SharePoint Online 和本地部署之间创建 SharePoint 混合解决方案</span><span class="sxs-lookup"><span data-stu-id="8147c-236">Create a SharePoint hybrid solution between SharePoint Online and on-premises</span></span>

<span data-ttu-id="8147c-237">如果迁移的答案需要在本地提供的自控制之间，以及 SharePoint Online 提供的较低的所有权成本，则可以通过混合将 SharePoint Server 2013 或2016服务器场连接到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="8147c-237">If the answer to your migration needs is somewhere between the self-control offered by on-premises, and the lower cost of ownership offered by SharePoint Online, you can connect SharePoint Server 2013 or 2016 farms to SharePoint Online, through hybrids.</span></span> [<span data-ttu-id="8147c-238">了解 SharePoint 混合解决方案</span><span class="sxs-lookup"><span data-stu-id="8147c-238">Learn about SharePoint hybrid solutions</span></span>](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
<span data-ttu-id="8147c-239">如果你确定混合 SharePoint 服务器场将对你的业务带来好处，请熟悉现有的混合类型，以及如何配置你的本地 SharePoint 场和 Office 365 订阅之间的连接。</span><span class="sxs-lookup"><span data-stu-id="8147c-239">If you decide that a hybrid SharePoint Server farm will benefit your business, familiarize yourself with the existing types of hybrid and how to configure the connection between your on-premises SharePoint farm and your Office 365 subscription.</span></span>
  
<span data-ttu-id="8147c-240">查看[Office 365 开发/测试环境](https://go.microsoft.com/fwlink/?linkid=843152)的工作原理是一种很棒的方法。</span><span class="sxs-lookup"><span data-stu-id="8147c-240">One good way to see how this works is by creating an [Office 365 dev/test environment](https://go.microsoft.com/fwlink/?linkid=843152).</span></span> <span data-ttu-id="8147c-241">拥有试用版或购买的 Office 365 订阅后，您将能够在 SharePoint Online 中创建网站集、web 和文档库，您可以在其中迁移数据（通过使用迁移 API 手动进行），或者-如果您想要迁移我的通过混合向导将网站内容传递到 OneDrive for business。</span><span class="sxs-lookup"><span data-stu-id="8147c-241">Once you have a trial or purchased Office 365 subscription, you'll be on your way to creating the site collections, webs, and document libraries in SharePoint Online to which you can migrate data (either manually, by use of the Migration API, or - if you want to migrate My Site content to OneDrive for Business - through the hybrid wizard).</span></span>
  
> [!NOTE]
> <span data-ttu-id="8147c-242">请注意，您的 SharePoint 2007 服务器场将需要升级到 SharePoint Server 2013 或 SharePoint Server 2016，才能使用 "混合" 选项</span><span class="sxs-lookup"><span data-stu-id="8147c-242">Remember that your SharePoint 2007 farm will need to be upgraded, on-premises, to either SharePoint Server 2013 or SharePoint Server 2016 to use the hybrid option</span></span> 
  
## <a name="related-topics"></a><span data-ttu-id="8147c-243">相关主题</span><span class="sxs-lookup"><span data-stu-id="8147c-243">Related topics</span></span>

[<span data-ttu-id="8147c-244">疑难解答和恢复升级（Office SharePoint Server 2007）</span><span class="sxs-lookup"><span data-stu-id="8147c-244">Troubleshoot and resume upgrade (Office SharePoint Server 2007)</span></span>](https://go.microsoft.com/fwlink/?linkid=843192)
  
[<span data-ttu-id="8147c-245">解决升级问题（SharePoint Server 2010）</span><span class="sxs-lookup"><span data-stu-id="8147c-245">Troubleshoot upgrade issues (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?linkid=843194)
  
[<span data-ttu-id="8147c-246">在 SharePoint 2013 中解决数据库升级问题</span><span class="sxs-lookup"><span data-stu-id="8147c-246">Troubleshoot database upgrade issues in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843195)
  
[<span data-ttu-id="8147c-247">搜索 Microsoft 合作伙伴以帮助进行升级</span><span class="sxs-lookup"><span data-stu-id="8147c-247">Search for Microsoft Partners to help with Upgrade</span></span>](https://go.microsoft.com/fwlink/?linkid=841249)
  
[<span data-ttu-id="8147c-248">可帮助您从 Office 2007 服务器和客户端进行升级的资源</span><span class="sxs-lookup"><span data-stu-id="8147c-248">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  

