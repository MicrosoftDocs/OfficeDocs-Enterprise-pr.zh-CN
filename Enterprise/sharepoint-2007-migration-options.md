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
f1.keywords:
- NOCSH
description: SharePoint Server 2007 已到达支持的结束时间，现在是时候升级了。 使用本文可帮助您创建计划。
ms.openlocfilehash: e319438e2d760c391414f699de5967738d8c6b81
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774987"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a><span data-ttu-id="5177a-104">要考虑的 SharePoint 2007 迁移选项</span><span class="sxs-lookup"><span data-stu-id="5177a-104">SharePoint 2007 migration options to consider</span></span>

<span data-ttu-id="5177a-105">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="5177a-105">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="5177a-106">Microsoft SharePoint 2007 和 SharePoint Server 2007 已达到支持的结尾。</span><span class="sxs-lookup"><span data-stu-id="5177a-106">Microsoft SharePoint 2007 and SharePoint Server 2007 have reached end of support.</span></span> <span data-ttu-id="5177a-107">是时候升级了！</span><span class="sxs-lookup"><span data-stu-id="5177a-107">It's time to upgrade!</span></span> <span data-ttu-id="5177a-108">本文提供了有关迁移选项的信息。</span><span class="sxs-lookup"><span data-stu-id="5177a-108">This article provides information about your migration options.</span></span>
  
## <a name="common-upgrade-strategies-for-sharepoint"></a><span data-ttu-id="5177a-109">SharePoint 的常见升级策略</span><span class="sxs-lookup"><span data-stu-id="5177a-109">Common upgrade strategies for SharePoint</span></span>

<span data-ttu-id="5177a-110">有多种方法可以升级 SharePoint Server 环境。</span><span class="sxs-lookup"><span data-stu-id="5177a-110">There are multiple methods to upgrade a SharePoint Server environment.</span></span> <span data-ttu-id="5177a-111">如果你拥有 Microsoft Office SharePoint Server 2007 场，则以下是升级方法的一些示例：</span><span class="sxs-lookup"><span data-stu-id="5177a-111">If you have a Microsoft Office SharePoint Server 2007 farm, here are some examples of the upgrade methods:</span></span>
  
- <span data-ttu-id="5177a-112">数据库附加</span><span class="sxs-lookup"><span data-stu-id="5177a-112">Database attach</span></span>
    
- <span data-ttu-id="5177a-113">并行升级</span><span class="sxs-lookup"><span data-stu-id="5177a-113">Side-by-side upgrade</span></span>
    
- <span data-ttu-id="5177a-114">就地升级</span><span class="sxs-lookup"><span data-stu-id="5177a-114">In-place upgrade</span></span>
    
- <span data-ttu-id="5177a-115">混合升级（就地与已分离的数据库/单独的数据库附加）</span><span class="sxs-lookup"><span data-stu-id="5177a-115">Hybrid upgrade (in-place with detached databases / separate database attach)</span></span>
    
- <span data-ttu-id="5177a-116">SharePoint 混合（联机连接到本地 SharePoint）</span><span class="sxs-lookup"><span data-stu-id="5177a-116">SharePoint hybrids (connect online to on-premises SharePoint)</span></span>
    
- <span data-ttu-id="5177a-117">在网站集或库之间手动移动数据</span><span class="sxs-lookup"><span data-stu-id="5177a-117">Manually move data between site collections or libraries</span></span>
    
- <span data-ttu-id="5177a-118">FastTrack 向导升级到 Microsoft 365 （[SharePoint Online 部署顾问](https://aka.ms/spoguidance)）</span><span class="sxs-lookup"><span data-stu-id="5177a-118">FastTrack Wizard upgrade to Microsoft 365 ([SharePoint Online deployment advisor](https://aka.ms/spoguidance))</span></span>
    
- <span data-ttu-id="5177a-119">Microsoft 365 中的迁移 API 到 SharePoint Online （SPO）</span><span class="sxs-lookup"><span data-stu-id="5177a-119">Migration API to SharePoint Online (SPO) in Microsoft 365</span></span>
    
<span data-ttu-id="5177a-120">哪种方法最适合你？</span><span class="sxs-lookup"><span data-stu-id="5177a-120">What works best for you?</span></span>
  
<span data-ttu-id="5177a-121">在需要升级时，您对服务器场所做和使用的知识方面的知识就是战术性的强项。</span><span class="sxs-lookup"><span data-stu-id="5177a-121">Your knowledge of what your farm does and is used for is a tactical strength when it comes to upgrade.</span></span> <span data-ttu-id="5177a-122">用户使用 SharePoint 服务器场的方式将有助于您从选项中进行选择。</span><span class="sxs-lookup"><span data-stu-id="5177a-122">The way people use the SharePoint Farm will help you choose from your options.</span></span>
  
> [!TIP]
> <span data-ttu-id="5177a-123">Microsoft Office SharePoint Server 2007 还包含此处未涵盖的逐步升级。</span><span class="sxs-lookup"><span data-stu-id="5177a-123">Microsoft Office SharePoint Server 2007 also has a gradual upgrade not covered here.</span></span> <span data-ttu-id="5177a-124">若要查看特定于步骤的升级文章的列表，请参阅[SharePoint Server 2007 end Support 路线图](sharepoint-2007-end-of-support.md)。</span><span class="sxs-lookup"><span data-stu-id="5177a-124">To see a list of step-specific upgrade articles see the [SharePoint Server 2007 end of support Roadmap](sharepoint-2007-end-of-support.md).</span></span> 
  
<span data-ttu-id="5177a-125">请务必查看要升级到的任何 SharePoint 版本的[产品生命周期](https://support.microsoft.com/lifecycle/search)和系统要求。</span><span class="sxs-lookup"><span data-stu-id="5177a-125">Remember to check the [Product Lifecycle](https://support.microsoft.com/lifecycle/search) and System Requirements for whatever version of SharePoint you're upgrading to.</span></span> <span data-ttu-id="5177a-126">这样，你就可以知道何时需要进行下一次升级（例如，如果你在 SharePoint Server 2010 等旧产品上暂停以规划更多升级），请确保你知道其支持日期的结束时间，并确保你有支持你的计划的硬件。</span><span class="sxs-lookup"><span data-stu-id="5177a-126">This is so you'll be aware when the next upgrade will be necessary (for example, if you pause at a legacy product like SharePoint Server 2010 to plan for more upgrades, be sure you know its end of support date), and to be certain you have hardware that supports your plan.</span></span> 
  
<span data-ttu-id="5177a-127">如果您计划将 SharePoint 网站的部分或全部转换为云中的 Microsoft 365，这是将指向[microsoft 365 和 Office 365 服务说明](https://docs.microsoft.com/office365/servicedescriptions/office-365-service-descriptions-technet-library)的链接加入书签的时间。</span><span class="sxs-lookup"><span data-stu-id="5177a-127">If you're planning to transition some, or all, of your SharePoint sites to Microsoft 365 in the Cloud, this is a time to bookmark a link to the [Microsoft 365 and Office 365 service descriptions](https://docs.microsoft.com/office365/servicedescriptions/office-365-service-descriptions-technet-library).</span></span> <span data-ttu-id="5177a-128">你将需要服务说明来了解 SharePoint Online 功能以及它们可能与本地 SharePoint Server 的不同之处。</span><span class="sxs-lookup"><span data-stu-id="5177a-128">You'll need the Service Descriptions to learn about SharePoint Online features and how they might differ from on-premises SharePoint Server.</span></span> <span data-ttu-id="5177a-129">升级功能 Microsoft Office SharePoint Server 2007 场。</span><span class="sxs-lookup"><span data-stu-id="5177a-129">Upgrade functional Microsoft Office SharePoint Server 2007 farms.</span></span> <span data-ttu-id="5177a-130">如果您的安装中存在损坏的网站，请在升级之前将其修复。</span><span class="sxs-lookup"><span data-stu-id="5177a-130">If your installation has sites that are broken, fix them prior to upgrade.</span></span>
  
## <a name="a-note-about-managing-risk"></a><span data-ttu-id="5177a-131">有关管理风险的说明</span><span class="sxs-lookup"><span data-stu-id="5177a-131">A note about managing risk</span></span>

<span data-ttu-id="5177a-132">诸如 "并行" 的方法在升级逻辑的方案中非常重要。</span><span class="sxs-lookup"><span data-stu-id="5177a-132">Methods like 'side-by-side' are important in the scheme of upgrade logic.</span></span> <span data-ttu-id="5177a-133">并行升级时，将维护 Microsoft Office SharePoint Server 2007 场，但在新硬件上构建场中的下一个版本（SharePoint Server 2010）。</span><span class="sxs-lookup"><span data-stu-id="5177a-133">When you upgrade side-by-side, you maintain your Microsoft Office SharePoint Server 2007 farm, but build a farm the next version up from it (SharePoint Server 2010) on new hardware.</span></span> <span data-ttu-id="5177a-134">这有助于以下三种方式：</span><span class="sxs-lookup"><span data-stu-id="5177a-134">This helps in three ways:</span></span>
  
1. <span data-ttu-id="5177a-135">您可以使用数据库附加来备份 Microsoft Office SharePoint Server 2007 数据库，从而单独升级这些数据库。</span><span class="sxs-lookup"><span data-stu-id="5177a-135">You have a place to take backups of your Microsoft Office SharePoint Server 2007 databases to upgrade them separately, by using database attach.</span></span>
    
2. <span data-ttu-id="5177a-136">如果你确定只有少量关键文档库和其他信息在 Microsoft Office SharePoint Server 2007 场中使用，则可以选择将数据从 Microsoft Office SharePoint Server 2007 手动移动到 SharePoint Server 2010，或者仅将特定网站和网站转到下一个版本（这可以使工作更轻松）。</span><span class="sxs-lookup"><span data-stu-id="5177a-136">If you figure out that only a small number of critical document libraries and other information are in use on your Microsoft Office SharePoint Server 2007 farm, you can choose to manually move data from Microsoft Office SharePoint Server 2007 to SharePoint Server 2010, or take only specific sites and webs to the next version (which can make your job easier).</span></span>
    
3. <span data-ttu-id="5177a-137">对 Microsoft Office SharePoint Server 2007 服务器场所做的操作越少，服务器场包含的数据越安全。</span><span class="sxs-lookup"><span data-stu-id="5177a-137">The less you do to the Microsoft Office SharePoint Server 2007 server farm, directly, the safer the data that farm contains as you upgrade.</span></span>
    
<span data-ttu-id="5177a-138">就地升级等方法将直接在 Microsoft Office SharePoint Server 2007 场中直接操作，为您提供更少的选择，以放弃路径并再次开始使用 pristine 环境。</span><span class="sxs-lookup"><span data-stu-id="5177a-138">Methods like In-Place upgrade will act directly on your Microsoft Office SharePoint Server 2007 farm, giving you fewer easy options to abandon a path and begin again with your pristine environment.</span></span> <span data-ttu-id="5177a-139">尽可能地构建一些安全措施（如采用和测试原始环境的备份）。</span><span class="sxs-lookup"><span data-stu-id="5177a-139">As much as possible, build in some safety measures (like taking and testing backups of the original environment).</span></span> <span data-ttu-id="5177a-140">例如，如果您的 Microsoft Office SharePoint Server 2007 服务器场是虚拟的，并且出于备份和还原目的而复制，则在升级服务时段之前备份和还原最新的数据库。</span><span class="sxs-lookup"><span data-stu-id="5177a-140">For example, if your Microsoft Office SharePoint Server 2007 farm is virtual, and is duplicated for the purposes of backup and restore, then back-up and restore the most current databases prior to your service window for the upgrade.</span></span> <span data-ttu-id="5177a-141">如果知道您可以还原数据库备份，则不会仅为您提供故障保护，从而使您高枕无忧。</span><span class="sxs-lookup"><span data-stu-id="5177a-141">Knowing that you have the option to restore database backups will not only give you a failsafe, it can give you peace of mind.</span></span>
  
> [!TIP]
> <span data-ttu-id="5177a-142">[Microsoft Office SharePoint server 2007](https://technet.microsoft.com/library/cc261992%28v=office.12%29.aspx)、 [sharepoint server 2010](https://technet.microsoft.com/library/cc261992%28v=office.14%29.aspx)、 [Sharepoint server 2013](https://technet.microsoft.com/library/cc261992%28v=office.15%29.aspx)和[SharePoint server 2016](https://technet.microsoft.com/library/cc261992%28v=office.16%29.aspx)的升级的最佳实践文档存在。</span><span class="sxs-lookup"><span data-stu-id="5177a-142">Best practices documents for upgrade exist for [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/library/cc261992%28v=office.15%29.aspx), and [SharePoint Server 2016](https://technet.microsoft.com/library/cc261992%28v=office.16%29.aspx).</span></span> <span data-ttu-id="5177a-143">您还可以搜索对升级或 Microsoft 365 迁移有经验的[Microsoft 合作伙伴](https://partnercenter.microsoft.com/pcv/search)。</span><span class="sxs-lookup"><span data-stu-id="5177a-143">You can also search for [Microsoft Partners](https://partnercenter.microsoft.com/pcv/search) who have experience with upgrades or Microsoft 365 migrations.</span></span> 
  
## <a name="make-your-plan"></a><span data-ttu-id="5177a-144">制定计划</span><span class="sxs-lookup"><span data-stu-id="5177a-144">Make your plan</span></span>

<span data-ttu-id="5177a-145">如果需要升级，则需要一个计划，并且一种大小不能在这些情况下适用。</span><span class="sxs-lookup"><span data-stu-id="5177a-145">If you need to upgrade, you need a plan, and one-size doesn't fit all in these cases.</span></span> <span data-ttu-id="5177a-146">您的计划可能非常简单，如 "使用 SharePoint Online 创建 Microsoft 365 订阅，注册一个域，重定向用户将文件保存到"。</span><span class="sxs-lookup"><span data-stu-id="5177a-146">Your plan may be as simple as 'Create a Microsoft 365 subscription with SharePoint Online, register a domain, and redirect people to save their files there'.</span></span> <span data-ttu-id="5177a-147">也可能不是。</span><span class="sxs-lookup"><span data-stu-id="5177a-147">And it may not be.</span></span> <span data-ttu-id="5177a-148">这是你的决定，并将其用于你和你的用户真正需要的内容。</span><span class="sxs-lookup"><span data-stu-id="5177a-148">That decision is yours, and it's down to what you and your users really need.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5177a-149">在其生命周期结束的软件上运行会有风险。</span><span class="sxs-lookup"><span data-stu-id="5177a-149">It's risky to run on software whose lifecycle has ended.</span></span> <span data-ttu-id="5177a-150">如果发现问题，则无法再对不支持的产品进行修补。</span><span class="sxs-lookup"><span data-stu-id="5177a-150">Products that are out of support are no longer patched when issues are found.</span></span> <span data-ttu-id="5177a-151">这也意味着，如果出现新的安全威胁，由于不再支持生命周期产品，因此不会有安全修补程序或修补程序。</span><span class="sxs-lookup"><span data-stu-id="5177a-151">This also means that if new security threats arise, there will be no security patches or fixes because the end-of-lifecycle products are no longer supported.</span></span> <span data-ttu-id="5177a-152">请避免出现这种情况！</span><span class="sxs-lookup"><span data-stu-id="5177a-152">Please avoid that situation!</span></span> 
  
### <a name="first-know-your-farm"></a><span data-ttu-id="5177a-153">首先，了解你的服务器场</span><span class="sxs-lookup"><span data-stu-id="5177a-153">First, know your farm</span></span>

<span data-ttu-id="5177a-154">在升级时，您的决策应取决于您的服务器场为您的组织执行的操作。</span><span class="sxs-lookup"><span data-stu-id="5177a-154">When upgrading, your decision-making should be based on what your farm does for your organization.</span></span> <span data-ttu-id="5177a-155">它满足的需求是什么？</span><span class="sxs-lookup"><span data-stu-id="5177a-155">What need does it satisfy?</span></span> <span data-ttu-id="5177a-156">其角色是什么？</span><span class="sxs-lookup"><span data-stu-id="5177a-156">What's its role?</span></span> <span data-ttu-id="5177a-157">公司中的每个服务器场可能具有不同的角色。</span><span class="sxs-lookup"><span data-stu-id="5177a-157">Each farm in your company may have a different role.</span></span> <span data-ttu-id="5177a-158">你的一些 SharePoint 场可能非常*关键*，一些可能是文件存档，也可能是安全保留的。</span><span class="sxs-lookup"><span data-stu-id="5177a-158">Some of your SharePoint farms may be  *critical*  , some may be file archives -- there for safe-keeping.</span></span> <span data-ttu-id="5177a-159">或者，如果您的服务器场同时填充了多个角色，则您可能需要了解网站集、web 甚至文档库的功能、任何自定义设置以及它们的重要性。</span><span class="sxs-lookup"><span data-stu-id="5177a-159">Or, if your farm fills many roles at once, then you may need to know what site collections, webs, or even document libraries do, any customizations, and how important they are.</span></span> <span data-ttu-id="5177a-160">在此级别分析数据看起来可能相当于许多工作，但在升级或迁移之前，它会节省时间和精力来主控域。</span><span class="sxs-lookup"><span data-stu-id="5177a-160">Analyzing your data at this level may seem like a lot of work, but it saves time and effort to master your domain before you upgrade, or migrate, it.</span></span> <span data-ttu-id="5177a-161">知道所有移动部件和最重要的位之后，您还将了解已 outgrown 的内容并可能会留下。</span><span class="sxs-lookup"><span data-stu-id="5177a-161">Once you know all the moving parts, and the most important bits, you'll also know what you've outgrown and can leave behind.</span></span> <span data-ttu-id="5177a-162">这种知识只会对您的未来有益。</span><span class="sxs-lookup"><span data-stu-id="5177a-162">That knowledge will only benefit you going forward.</span></span> 
  
<span data-ttu-id="5177a-163">那么，用户说什么对你的 SharePoint Server 服务器场最重要？</span><span class="sxs-lookup"><span data-stu-id="5177a-163">So, what are users saying is most important about your SharePoint Server farm?</span></span>
  
- <span data-ttu-id="5177a-164">内置的 SharePoint 功能</span><span class="sxs-lookup"><span data-stu-id="5177a-164">Built-in SharePoint features</span></span>
    
- <span data-ttu-id="5177a-165">大型数据文档集（如文件存档）</span><span class="sxs-lookup"><span data-stu-id="5177a-165">The large data corpus (such as an archive of files)</span></span>
    
- <span data-ttu-id="5177a-166">供应情况</span><span class="sxs-lookup"><span data-stu-id="5177a-166">Availability</span></span>
    
- <span data-ttu-id="5177a-167">服务器场中的关键应用程序、web 部件或文档（任务关键型服务器场）</span><span class="sxs-lookup"><span data-stu-id="5177a-167">Critical apps, web parts, or docs in the farm (Mission critical farm)</span></span>
    
- <span data-ttu-id="5177a-168">满足合规性标准</span><span class="sxs-lookup"><span data-stu-id="5177a-168">The Compliance standards met</span></span>
    
- <span data-ttu-id="5177a-169">自定义项</span><span class="sxs-lookup"><span data-stu-id="5177a-169">Customizations</span></span>
    
<span data-ttu-id="5177a-170">如果您在 SharePoint 服务器场中运行重要的业务，则假设它的作用类似于有关客户端服务要求的关键数据的大型目录，则可以在 "关键应用程序" 旁添加一个滴答，也可以在 "可用性" 旁进行，如果您无法使用 SharePoint 一段时间，则您的企业将受到影响。</span><span class="sxs-lookup"><span data-stu-id="5177a-170">If you run something essential to your business from your SharePoint farm, say it acts like a large catalog of critical data about client service requirements, you may put a tick beside 'Critical apps', but also 'Availability' -- that is, your business would be impacted if you couldn't use SharePoint for a while.</span></span> <span data-ttu-id="5177a-171">同样，您可以检查 "自定义"，因为您的服务器场提供的关键服务基于自定义代码、网站定义或可协同工作的大量自定义项。</span><span class="sxs-lookup"><span data-stu-id="5177a-171">Likewise, you might check 'Customizations' because the critical services your farm offers are based on custom code, site definitions, or a number of customizations that work together.</span></span>
  
<span data-ttu-id="5177a-172">如果 SharePoint 满足这些需求，而无需在使用软件的内置功能的情况下执行任何操作，并且通常会将其更新并执行常规管理和维护，则您可能选择了 "内置 SharePoint"，这也可能是您在 SharePoint 的较早版本上进行的原因。</span><span class="sxs-lookup"><span data-stu-id="5177a-172">If SharePoint met those needs without your having to do anything outside of using what's built-in to the software, and you generally update it and carry out normal administration and maintenance, you may have chosen 'Built-in SharePoint' -- this may also be your reason for sitting on an older version of SharePoint.</span></span> <span data-ttu-id="5177a-173">换句话说，它已完成您所需的操作，并且在 Microsoft Office SharePoint Server 2007 的支持终止之前，您不需要进行升级。</span><span class="sxs-lookup"><span data-stu-id="5177a-173">In other words, it already does what you need it to and you haven't needed to upgrade until now, at Microsoft Office SharePoint Server 2007 end of support.</span></span>
  
<span data-ttu-id="5177a-174">当您在项目中列出这些内容时，请为升级创建条件。</span><span class="sxs-lookup"><span data-stu-id="5177a-174">When you bullet-list these things, you create criteria for your upgrade.</span></span> <span data-ttu-id="5177a-175">换句话说，任何升级都必须满足要考虑的这条。</span><span class="sxs-lookup"><span data-stu-id="5177a-175">In other words, any upgrade would have to meet this bar to be considered.</span></span> <span data-ttu-id="5177a-176">这为您提供了一种方法，用于排除当前无法满足您需求的方法。</span><span class="sxs-lookup"><span data-stu-id="5177a-176">This gives you a way to rule out methods that don't currently fit your needs.</span></span>
  
### <a name="a-simple-sample-plan"></a><span data-ttu-id="5177a-177">一个简单的示例计划</span><span class="sxs-lookup"><span data-stu-id="5177a-177">A simple sample plan</span></span>

<span data-ttu-id="5177a-178">在你的 SharePoint 升级将采用的路径上，可能需要更大的与领导和其他管理员达成一致意见。</span><span class="sxs-lookup"><span data-stu-id="5177a-178">There may need to be wider consensus with leadership and other admins on the path your SharePoint Upgrade will take.</span></span> <span data-ttu-id="5177a-179">SharePoint Server 管理员通常与 Microsoft SQL Server 管理员合作，与网络和安全团队协同工作，等等。</span><span class="sxs-lookup"><span data-stu-id="5177a-179">SharePoint Server Administrators often cooperate with Microsoft SQL Server admins, work with Networking and Security teams, and more.</span></span> <span data-ttu-id="5177a-180">在有大量利益干系人的情况下，您可能需要为升级和迁移计划构建协议或调整。</span><span class="sxs-lookup"><span data-stu-id="5177a-180">Where there are a lot of stakeholders, you may need to build agreement for, or adjust, your upgrade and migration plan.</span></span> <span data-ttu-id="5177a-181">例如，如果您迁移数据以便贵公司的一部分在 Microsoft 365 中使用 SharePoint Online，则可能需要在网络中进行性能调整或测试。</span><span class="sxs-lookup"><span data-stu-id="5177a-181">For example, if you migrate data so that part of your company uses SharePoint Online in Microsoft 365, there will likely need to be performance tuning or testing inside your network.</span></span> <span data-ttu-id="5177a-182">应提前通知受影响的团队。</span><span class="sxs-lookup"><span data-stu-id="5177a-182">Affected teams should be informed ahead of time.</span></span>
  
<span data-ttu-id="5177a-183">在我的简单示例中，我显示了 SharePoint 管理员的建议，然后列出了所有利益干系人同意的计划。</span><span class="sxs-lookup"><span data-stu-id="5177a-183">In my simple sample, I show a SharePoint administrator's proposal and then list out the plan that all the stakeholders agreed upon.</span></span> <span data-ttu-id="5177a-184">为清楚起见，请记录你的协议和决策。</span><span class="sxs-lookup"><span data-stu-id="5177a-184">For clarity, document your agreements and decisions.</span></span>
  
<span data-ttu-id="5177a-185">计划在对服务器场进行深入分析之后开始，并尝试确定服务器场的角色、痛点和其他重要信息，这将导致缩小某些升级选项。</span><span class="sxs-lookup"><span data-stu-id="5177a-185">The plan starts after an in-depth analysis of a farm, and tries to identify the role of the farm, pain points, and other important information that will lead to narrowing down some upgrade options.</span></span> <span data-ttu-id="5177a-186">随后，SharePoint 管理员将提出升级建议，并且利益干系人同意行动计划。</span><span class="sxs-lookup"><span data-stu-id="5177a-186">Afterward, an upgrade proposal is made by SharePoint administrator, and stakeholders agree on an action plan.</span></span>
  
<span data-ttu-id="5177a-187">我的 "最重要" 项目符号列表：</span><span class="sxs-lookup"><span data-stu-id="5177a-187">My 'most important' bullet list:</span></span>
  
- <span data-ttu-id="5177a-188">可用性、SharePoint 内置功能以及合规性标准。</span><span class="sxs-lookup"><span data-stu-id="5177a-188">Availability, features built-in to SharePoint, and Compliance standards.</span></span>
    
- <span data-ttu-id="5177a-189">大多数数据都在三个网站集上，而开发团队使用一个会议工作区尤为重要，并且在全球范围内多个时间区域使用。</span><span class="sxs-lookup"><span data-stu-id="5177a-189">Most of the data is on three site collections, with one Meeting Workspace used by a Dev team particularly important and in heavy use in multiple time-zones worldwide.</span></span>
    
- <span data-ttu-id="5177a-190">有17个其他网站广泛使用。</span><span class="sxs-lookup"><span data-stu-id="5177a-190">There are seventeen other sites that are widely used.</span></span>
    
- <span data-ttu-id="5177a-191">两个文档库（根网站集上的会议工作区和文档）最大（每个文档库超过8000个文档）。</span><span class="sxs-lookup"><span data-stu-id="5177a-191">Two document libraries (Meeting Workspace and Documents on the root site collection) are largest (over 8000 docs each).</span></span> <span data-ttu-id="5177a-192">我们有大量存档文档和列表，其中包含电子表格附件。</span><span class="sxs-lookup"><span data-stu-id="5177a-192">We have a large number of archived docs and list with spreadsheet attachments.</span></span>
    
- <span data-ttu-id="5177a-193">有十四个具有敏感数据的库列表，必须保持合规性。</span><span class="sxs-lookup"><span data-stu-id="5177a-193">There are fourteen lists of libraries that have sensitive data that MUST stay in Compliance.</span></span>
    
- <span data-ttu-id="5177a-194">我们必须能够在任何位置执行保留和电子发现。</span><span class="sxs-lookup"><span data-stu-id="5177a-194">We MUST have the ability to do holds and e-discovery wherever we go.</span></span>
    
- <span data-ttu-id="5177a-195">由于 InfoSec 规则，这些数据中的某些数据必须保持本地。</span><span class="sxs-lookup"><span data-stu-id="5177a-195">Some of this data MUST stay on-premises, due to InfoSec rules.</span></span>
    
 <span data-ttu-id="5177a-196">**我的升级和迁移选择：**</span><span class="sxs-lookup"><span data-stu-id="5177a-196">**My upgrade and migration choices:**</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="5177a-197">**是**</span><span class="sxs-lookup"><span data-stu-id="5177a-197">**Yes**</span></span> <br/> |<span data-ttu-id="5177a-198">**否**</span><span class="sxs-lookup"><span data-stu-id="5177a-198">**No**</span></span> <br/> |
|<span data-ttu-id="5177a-199">使用数据库附加升级数据库</span><span class="sxs-lookup"><span data-stu-id="5177a-199">Upgrade databases with database attach</span></span>  <br/> |<span data-ttu-id="5177a-200">就地升级</span><span class="sxs-lookup"><span data-stu-id="5177a-200">In-place upgrade</span></span>  <br/> |
|<span data-ttu-id="5177a-201">并行升级服务器场</span><span class="sxs-lookup"><span data-stu-id="5177a-201">Upgrade with farms side-by-side</span></span>  <br/> |<span data-ttu-id="5177a-202">混合升级</span><span class="sxs-lookup"><span data-stu-id="5177a-202">Hybrid Upgrade</span></span>  <br/> |
|<span data-ttu-id="5177a-203">迁移 API 到 Microsoft 365 中的 SPO （针对个人网站数据）</span><span class="sxs-lookup"><span data-stu-id="5177a-203">Migration API to SPO in Microsoft 365 (for personal site data)</span></span>  <br/> |<span data-ttu-id="5177a-204">SharePoint 混合（尚不需要）</span><span class="sxs-lookup"><span data-stu-id="5177a-204">SharePoint Hybrid (not needed yet)</span></span>  <br/> |
|<span data-ttu-id="5177a-205">对关键数据的一些手动数据迁移到 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5177a-205">Some manual data migrations to SharePoint Online for critical data</span></span>  <br/> |<span data-ttu-id="5177a-206">FastTrack 向导升级到 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="5177a-206">FastTrack wizard upgrade to Microsoft 365</span></span>  <br/> |
   
 <span data-ttu-id="5177a-207">**我建议的计划：**</span><span class="sxs-lookup"><span data-stu-id="5177a-207">**My proposed plan:**</span></span>
  
<span data-ttu-id="5177a-208">本地升级（包含 SharePoint 并行的版本），以进行虚拟化，以便我们可以先升级数据库。</span><span class="sxs-lookup"><span data-stu-id="5177a-208">Upgrade on-premises, with versions of SharePoint side-by-side, some virtualized, so that we can upgrade the databases first.</span></span> <span data-ttu-id="5177a-209">从 SharePoint 2007 转到 SharePoint 2010。</span><span class="sxs-lookup"><span data-stu-id="5177a-209">Go from SharePoint 2007 to SharePoint 2010.</span></span> <span data-ttu-id="5177a-210">管理员和 Devs 测试生成的服务器场。</span><span class="sxs-lookup"><span data-stu-id="5177a-210">Admins and Devs test the resulting farm.</span></span> <span data-ttu-id="5177a-211">用户测试生成的服务器场。</span><span class="sxs-lookup"><span data-stu-id="5177a-211">Users test the resulting farm.</span></span> <span data-ttu-id="5177a-212">解决此期间的任何显示停止问题。</span><span class="sxs-lookup"><span data-stu-id="5177a-212">Fix any show-stopping issues during this time.</span></span> <span data-ttu-id="5177a-213">同样，并行将 SharePoint 2010 数据库升级到 SharePoint 2013。</span><span class="sxs-lookup"><span data-stu-id="5177a-213">Again, side-by-side, upgrade SharePoint 2010 databases to SharePoint 2013.</span></span> <span data-ttu-id="5177a-214">测试.</span><span class="sxs-lookup"><span data-stu-id="5177a-214">Test.</span></span> <span data-ttu-id="5177a-215">用户测试/试点。</span><span class="sxs-lookup"><span data-stu-id="5177a-215">User test/pilot.</span></span> <span data-ttu-id="5177a-216">解决此期间的任何显示停止问题。</span><span class="sxs-lookup"><span data-stu-id="5177a-216">Fix any show-stopping issues during this time.</span></span>
  
- <span data-ttu-id="5177a-217">如果与 SPO 的联合混合搜索符合你的需求，请考虑使用。</span><span class="sxs-lookup"><span data-stu-id="5177a-217">Consider if a Search Federated Hybrid with SPO meets your needs.</span></span>
    
- <span data-ttu-id="5177a-218">如果要从此处升级到 SharePoint Online，请考虑[FastTrack 帮助](https://fasttrack.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="5177a-218">Consider [FastTrack assistance](https://fasttrack.microsoft.com) if you would like to upgrade to SharePoint Online from here.</span></span> 
    
- <span data-ttu-id="5177a-219">确定是否可以将任何网站集卸载到 Microsoft 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="5177a-219">Determine if any site collections can be offloaded to a Microsoft 365 Subscription.</span></span> <span data-ttu-id="5177a-220">（Microsoft 365 符合多种[合规性标准](https://technet.microsoft.com/library/office-365-compliance.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5177a-220">(Microsoft 365 meets many [Compliance standards](https://technet.microsoft.com/library/office-365-compliance.aspx).</span></span> <span data-ttu-id="5177a-221">Microsoft 365 具有[电子数据展示](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da)，可以通过合规性中心进行[保留](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E)。</span><span class="sxs-lookup"><span data-stu-id="5177a-221">Microsoft 365 has [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) and can do [Holds](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) through the Compliance Centre.)</span></span> 
    
<span data-ttu-id="5177a-222">否则，继续并行升级到 SharePoint Server 2016。</span><span class="sxs-lookup"><span data-stu-id="5177a-222">Otherwise, continue with a side-by-side upgrade to SharePoint Server 2016.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5177a-223">在计划升级和实际过程的管理员之间的建议是，与升级所依赖的其他利益干系人进行的对话。</span><span class="sxs-lookup"><span data-stu-id="5177a-223">In between recommendations made by the administrators planning the upgrade and the actual process are the conversations that happen with other stakeholders on which the upgrade relies.</span></span> <span data-ttu-id="5177a-224">例如，经济性有时强制管理员更改其计划。</span><span class="sxs-lookup"><span data-stu-id="5177a-224">For example, sometimes economics force administrators to change their plans.</span></span> <span data-ttu-id="5177a-225">无论最终的决定是什么，您都应记录商定的计划是什么，即将进行。</span><span class="sxs-lookup"><span data-stu-id="5177a-225">Whatever the final decision is, you should document what the agreed-upon plan is, going forward.</span></span> <span data-ttu-id="5177a-226">它可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="5177a-226">It might look something like this:</span></span> 
  
 <span data-ttu-id="5177a-227">**我的行动计划：**</span><span class="sxs-lookup"><span data-stu-id="5177a-227">**My action plan:**</span></span>
  
<span data-ttu-id="5177a-228">在内部部署中，我们使用虚拟环境构建默认的 SharePoint Server 2010 和2013。</span><span class="sxs-lookup"><span data-stu-id="5177a-228">On-premises, we use a virtual environment to build default SharePoint Server 2010, and 2013.</span></span> <span data-ttu-id="5177a-229">SharePoint Server 2016 将构建在满足2016的系统要求的新硬件上。</span><span class="sxs-lookup"><span data-stu-id="5177a-229">SharePoint Server 2016 will be built on new hardware that meets system requirements for 2016.</span></span> <span data-ttu-id="5177a-230">我们会将数据库附加到从 SharePoint 2007 升级数据库，通过 it 和 SharePoint Server 2016 之间的所有版本。</span><span class="sxs-lookup"><span data-stu-id="5177a-230">We will do database attaches to upgrade databases from SharePoint 2007 through all versions between it and SharePoint Server 2016.</span></span> <span data-ttu-id="5177a-231">此时，在 SharePoint Server 2016 环境中为和测试核心自定义项，前提是本机功能尚未满足我们的需求。</span><span class="sxs-lookup"><span data-stu-id="5177a-231">Core customizations are being recreated for and tested in the SharePoint Server 2016 environment at this time, if native features don't already meet our needs.</span></span> <span data-ttu-id="5177a-232">如果我们成功，我们将在具有升级数据库的新硬件上安装本地服务器场，并减少自定义项。</span><span class="sxs-lookup"><span data-stu-id="5177a-232">If we are successful, we will have an on-premises farm on new hardware with upgraded databases, and fewer customizations.</span></span> <span data-ttu-id="5177a-233">我们会将升级后的内容数据库附加到 SharePoint Server 2013 中的新网站集、测试、用户测试/试点，然后将 DNS 剪切到新的 SharePoint Server 2016 环境以供实时使用。</span><span class="sxs-lookup"><span data-stu-id="5177a-233">We'll attach the upgraded content databases to new site collections in SharePoint Server 2013, test, user test/pilot, and then do a DNS cut-over to the new SharePoint Server 2016 environment for live use.</span></span>
  
- <span data-ttu-id="5177a-234">现在，我们不会在 SharePoint Server 2016 和 SharePoint Online 之间考虑联合混合。</span><span class="sxs-lookup"><span data-stu-id="5177a-234">We will not consider Federated Hybrid between SharePoint Server 2016 and SharePoint Online right now.</span></span>
    
- <span data-ttu-id="5177a-235">我们的网站的估计35% 可以通过虚域转换为新的 SPO 网站，也可以是最终成为 OneDrive for business 存储。</span><span class="sxs-lookup"><span data-stu-id="5177a-235">An estimated 35% of our sites can be turned into new SPO sites with vanity domains, or, ultimately, become OneDrive for Business storage.</span></span> <span data-ttu-id="5177a-236">寻找其他机会来转换网站，或将新网站路由到 SPO。</span><span class="sxs-lookup"><span data-stu-id="5177a-236">Looking for other opportunities to convert sites, or route new sites to SPO.</span></span>
    
- <span data-ttu-id="5177a-237">此部分迁移过程是手动进行的，通过拖放到 OneDrive for business 个人网站，有些是迁移 API。</span><span class="sxs-lookup"><span data-stu-id="5177a-237">Some of this part of the migration will be manual, by drag-and-drop to OneDrive for Business personal sites, and some by migration API.</span></span>
    
<span data-ttu-id="5177a-238">更详细的步骤或指向特定升级方向的多个链接应遵循计划。</span><span class="sxs-lookup"><span data-stu-id="5177a-238">More detailed steps, or a number of links to specific upgrade directions should follow a plan.</span></span> <span data-ttu-id="5177a-239">MOSS 2007 计算机不应退役，应维护虚拟环境以进行比较;但是，当用户被重定向到 SharePoint Server 2016 时，将完成升级。</span><span class="sxs-lookup"><span data-stu-id="5177a-239">The MOSS 2007 computer should not be decommissioned, and virtual environments should be maintained for the sake of comparison; however, the upgrade will be complete when users are redirected to SharePoint Server 2016.</span></span>
  
<span data-ttu-id="5177a-240">选择方法的主要因素是升级的总成本和时间成本（您将在 SharePoint 迁移路线图文章中详细了解）。</span><span class="sxs-lookup"><span data-stu-id="5177a-240">Often major factors in choosing a method are the total cost of the upgrade and the cost in time (you'll see more on this in the SharePoint Migration Roadmap article).</span></span> <span data-ttu-id="5177a-241">但是，事先规划将有益于设置预期、明智选择和确定成功的外观。</span><span class="sxs-lookup"><span data-stu-id="5177a-241">However, planning ahead will benefit you greatly in setting expectations, choosing wisely, and framing what success will look like.</span></span>
  
## <a name="related-links"></a><span data-ttu-id="5177a-242">相关链接</span><span class="sxs-lookup"><span data-stu-id="5177a-242">Related links</span></span>

[<span data-ttu-id="5177a-243">可帮助您从 Office 2007 服务器和客户端进行升级的资源</span><span class="sxs-lookup"><span data-stu-id="5177a-243">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  
[<span data-ttu-id="5177a-244">Microsoft 生命周期策略和生命周期搜索</span><span class="sxs-lookup"><span data-stu-id="5177a-244">Microsoft Lifecycle Policy and Lifecycle search</span></span>](https://support.microsoft.com/lifecycle)
  
[<span data-ttu-id="5177a-245">搜索可帮助升级或迁移的 Microsoft 合作伙伴</span><span class="sxs-lookup"><span data-stu-id="5177a-245">Search for Microsoft Partners who can help with upgrade or migration</span></span>](https://partnercenter.microsoft.com/pcv/search)
  

