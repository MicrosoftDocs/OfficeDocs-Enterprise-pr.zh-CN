---
title: 将 SharePoint 站点移到其他地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何将 SharePoint 站点移到其他地理位置。
ms.openlocfilehash: f1837942a72881578930f94ad8c4b57dbdb0c649
ms.sourcegitcommit: 59c250b5f62e72fb51fd0b80d2be636ee8078f6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "35422371"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a><span data-ttu-id="57bf8-103">将 SharePoint 站点移到其他地理位置</span><span class="sxs-lookup"><span data-stu-id="57bf8-103">Move a SharePoint site to a different geo location (Preview)</span></span>

<span data-ttu-id="57bf8-104">利用 SharePoint 站点地理位置移动，你可以将 SharePoint 站点移到多地理位置环境内的其他地理位置。</span><span class="sxs-lookup"><span data-stu-id="57bf8-104">With SharePoint site geo move, you can move SharePoint sites to other geo locations within your multi-geo environment.</span></span>

<span data-ttu-id="57bf8-105">可在地理位置之间移动以下类型的站点：</span><span class="sxs-lookup"><span data-stu-id="57bf8-105">The following types of site can be moved between geo locations:</span></span>

- <span data-ttu-id="57bf8-106">Office 365 组连接的站点</span><span class="sxs-lookup"><span data-stu-id="57bf8-106">Office 365 Group-connected sites</span></span>
- <span data-ttu-id="57bf8-107">没有 Office 365 组关联的新式站点</span><span class="sxs-lookup"><span data-stu-id="57bf8-107">Modern sites without an Office 365 Group association</span></span>
- <span data-ttu-id="57bf8-108">经典 SharePoint 站点</span><span class="sxs-lookup"><span data-stu-id="57bf8-108">Classic SharePoint sites</span></span>
- <span data-ttu-id="57bf8-109">通信站点</span><span class="sxs-lookup"><span data-stu-id="57bf8-109">Communication sites</span></span>

<span data-ttu-id="57bf8-110">你必须是全局管理员或 SharePoint 管理员才能在地理位置之间移动站点。</span><span class="sxs-lookup"><span data-stu-id="57bf8-110">You must be a Global Administrator or SharePoint Administrator to move a site between geo locations.</span></span>

<span data-ttu-id="57bf8-111">在 SharePoint 的移动过程中会有大约 4-6 小时的只读阶段，具体取决于站点内容。</span><span class="sxs-lookup"><span data-stu-id="57bf8-111">There is a read-only window during the SharePoint site geo move of approximately 4-6 hours, depending on site contents.</span></span>
 
## <a name="best-practices"></a><span data-ttu-id="57bf8-112">最佳做法</span><span class="sxs-lookup"><span data-stu-id="57bf8-112">Best practices</span></span>

- <span data-ttu-id="57bf8-113">尝试在测试站点上进行 SharePoint 站点移动，以熟悉程序。</span><span class="sxs-lookup"><span data-stu-id="57bf8-113">Try a SharePoint site move on a test site to get familiar with the procedure.</span></span> 
- <span data-ttu-id="57bf8-114">在安排或执行移动之前，验证站点是否可移动。</span><span class="sxs-lookup"><span data-stu-id="57bf8-114">Validate whether the site can be moved prior to scheduling or performing the move.</span></span> 
- <span data-ttu-id="57bf8-115">尽可能将跨地理位置站点移动安排在非工作时间进行，以便减少用户影响。</span><span class="sxs-lookup"><span data-stu-id="57bf8-115">When possible schedule cross-geo sites moves for outside business hours to reduce user impact.</span></span>
- <span data-ttu-id="57bf8-116">在进行站点移动之前，与受影响的用户沟通。</span><span class="sxs-lookup"><span data-stu-id="57bf8-116">Communicate with impacted users prior to the sites move.</span></span> 

## <a name="communicating-to-your-users"></a><span data-ttu-id="57bf8-117">向用户传达</span><span class="sxs-lookup"><span data-stu-id="57bf8-117">Communicating to your users</span></span>

<span data-ttu-id="57bf8-118">在地理位置之间移动 SharePoint 站点时，请务必向站点的用户（通常是能够编辑站点的任何人）传达预期结果。</span><span class="sxs-lookup"><span data-stu-id="57bf8-118">When moving SharePoint sites between geo locations, it's important to communicate to the sites' users (generally anyone with the ability to edit the site) what to expect.</span></span> <span data-ttu-id="57bf8-119">这可帮助减少用户困惑和致电技术支持的次数。</span><span class="sxs-lookup"><span data-stu-id="57bf8-119">This can help reduce user confusion and calls to your help desk.</span></span> <span data-ttu-id="57bf8-120">在移动之前向站点的用户发送电子邮件，告知他们以下信息：</span><span class="sxs-lookup"><span data-stu-id="57bf8-120">Email your sites' users before the move and let them know the following information:</span></span>

- <span data-ttu-id="57bf8-121">移动应该开始的时间和需要花费的时长</span><span class="sxs-lookup"><span data-stu-id="57bf8-121">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="57bf8-122">其站点要移动到的地理位置和用于访问新位置的 URL</span><span class="sxs-lookup"><span data-stu-id="57bf8-122">What geo location their site is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="57bf8-123">移动期间，他们应关闭文件，不进行任何编辑。</span><span class="sxs-lookup"><span data-stu-id="57bf8-123">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="57bf8-124">文件权限和共享不会因移动而更改。</span><span class="sxs-lookup"><span data-stu-id="57bf8-124">File permissions and sharing will not change because of the move.</span></span>
- <span data-ttu-id="57bf8-125">多地理位置环境中的预期用户体验</span><span class="sxs-lookup"><span data-stu-id="57bf8-125">What to expect from the user experience in a multi-geo environment</span></span>

<span data-ttu-id="57bf8-126">移动成功完成后，务必向站点的用户发送电子邮件，告知他们可在站点上恢复工作。</span><span class="sxs-lookup"><span data-stu-id="57bf8-126">Be sure to send your sites' users an email when the move has successfully completed informing them that they can resume working on their sites.</span></span>

## <a name="scheduling-sharepoint-site-moves"></a><span data-ttu-id="57bf8-127">安排 SharePoint 站点移动</span><span class="sxs-lookup"><span data-stu-id="57bf8-127">Scheduling SharePoint site moves</span></span>

<span data-ttu-id="57bf8-128">你可以提前安排 SharePoint 站点移动 （在本文后面介绍）。</span><span class="sxs-lookup"><span data-stu-id="57bf8-128">You can schedule SharePoint site moves in advance (described later in this article).</span></span> <span data-ttu-id="57bf8-129">可以按如下方式安排移动：</span><span class="sxs-lookup"><span data-stu-id="57bf8-129">You can schedule moves as follows:</span></span>

- <span data-ttu-id="57bf8-130">一次最多可以安排 4,000 次移动。</span><span class="sxs-lookup"><span data-stu-id="57bf8-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="57bf8-131">移动开始后，可以安排更多移动操作，在在队列及任何给定时间内最多有 4,000 个待处理移动。</span><span class="sxs-lookup"><span data-stu-id="57bf8-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
 
<span data-ttu-id="57bf8-132">若要将 SharePoint 站点移动安排在稍后进行，请在开始移动时包括以下参数之一：</span><span class="sxs-lookup"><span data-stu-id="57bf8-132">To schedule a SharePoint site geo move for a later time, include one of the following parameters when you start the move:</span></span>
- <span data-ttu-id="57bf8-133">`PreferredMoveBeginDate` -移动将可能在此指定时间开始。</span><span class="sxs-lookup"><span data-stu-id="57bf8-133">`PreferredMoveBeginDate` – The move will likely begin at this specified time.</span></span>
- <span data-ttu-id="57bf8-134">`PreferredMoveEndDate` -移动将尽可能在此指定时间之前完成。</span><span class="sxs-lookup"><span data-stu-id="57bf8-134">`PreferredMoveEndDate` – The move will likely be completed by this specified time, on a best effort basis.</span></span> 

<span data-ttu-id="57bf8-135">对于这两个参数，均必须以协调世界时 (UTC) 指定时间。</span><span class="sxs-lookup"><span data-stu-id="57bf8-135">Time must be specified in Coordinated Universal Time (UTC) for both parameters.</span></span>

## <a name="moving-the-site"></a><span data-ttu-id="57bf8-136">移动站点</span><span class="sxs-lookup"><span data-stu-id="57bf8-136">Moving the site</span></span>

<span data-ttu-id="57bf8-137">SharePoint 站点地理位置移动要求你通过站点所在的地理位置中的 SharePoint 管理 URL 连接并执行移动。</span><span class="sxs-lookup"><span data-stu-id="57bf8-137">SharePoint site geo move requires that you connect and perform the move from the SharePoint Admin URL in the geo location where the site is.</span></span>

<span data-ttu-id="57bf8-138">例如，如果站点 URL 为 https://contosohealthcare.sharepoint.com/sites/Turbines，请连接到位于 https://contosohealthcare-admin.sharepoint.com: 的 SharePoint 管理 URL</span><span class="sxs-lookup"><span data-stu-id="57bf8-138">For example, if the site URL is https://contosohealthcare.sharepoint.com/sites/Turbines, connect to the SharePoint Admin URL at https://contosohealthcare-admin.sharepoint.com:</span></span>

`connect-sposervice -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a><span data-ttu-id="57bf8-139">验证环境</span><span class="sxs-lookup"><span data-stu-id="57bf8-139">Validating the environment</span></span>

<span data-ttu-id="57bf8-140">在安排任何站点移动之前，我们建议你执行验证来确保站点可移动。</span><span class="sxs-lookup"><span data-stu-id="57bf8-140">We recommend that before scheduling any site move, you perform a validation to ensure that the site can be moved.</span></span>

<span data-ttu-id="57bf8-141">我们不支持移动包含以下各项的站点：</span><span class="sxs-lookup"><span data-stu-id="57bf8-141">We do not support moving sites with:</span></span>
-   <span data-ttu-id="57bf8-142">Business Connectivity Services</span><span class="sxs-lookup"><span data-stu-id="57bf8-142">Business Connectivity Services</span></span>
-   <span data-ttu-id="57bf8-143">InfoPath 表单</span><span class="sxs-lookup"><span data-stu-id="57bf8-143">InfoPath forms</span></span> 

<span data-ttu-id="57bf8-144">若要确保所有地理位置都兼容，请运行 `Get-SPOGeoMoveCrossCompatibilityStatus`：</span><span class="sxs-lookup"><span data-stu-id="57bf8-144">To ensure all geo locations are compatible, run `Get-SPOGeoMoveCrossCompatibilityStatus`.</span></span> <span data-ttu-id="57bf8-145">这将显示所有地理位置，并显示环境是否与目标地理位置兼容。</span><span class="sxs-lookup"><span data-stu-id="57bf8-145">This will display all your geo locations and whether the environment is compatible with the destination geo location.</span></span>

<span data-ttu-id="57bf8-146">若要在站点上执行仅验证检查，请将 `Start-SPOSiteContentMove`与 `-ValidationOnly` 参数结合使用，验证是否能够移动站点。</span><span class="sxs-lookup"><span data-stu-id="57bf8-146">To perform a validation-only check on your site, use `Start-SPOSiteContentMove` with the `-ValidationOnly` parameter to validate if the site is able to be moved.</span></span> <span data-ttu-id="57bf8-147">例如：</span><span class="sxs-lookup"><span data-stu-id="57bf8-147">For example:</span></span>

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

<span data-ttu-id="57bf8-148">如果站点可移动，这将返回 *Success*，如果存在任何造成阻碍的情况，则返回 *Fail*。</span><span class="sxs-lookup"><span data-stu-id="57bf8-148">This will return *Success* if the site is ready to be moved or *Fail* if any of blocked conditions are present.</span></span>

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a><span data-ttu-id="57bf8-149">为没有关联 Office 365 组的站点开始 SharePoint 站点地理位置移动</span><span class="sxs-lookup"><span data-stu-id="57bf8-149">Start a SharePoint site geo move for a site with no associated Office 365 Group</span></span>

<span data-ttu-id="57bf8-150">默认情况下，站点的初始 URL 将更改为目标地理位置的 URL。</span><span class="sxs-lookup"><span data-stu-id="57bf8-150">By default, initial URL for the site will change to the URL of the destination geo location.</span></span> <span data-ttu-id="57bf8-151">例如：</span><span class="sxs-lookup"><span data-stu-id="57bf8-151">For example:</span></span>

<span data-ttu-id="57bf8-152">https://Contoso.sharepoint.com/sites/projectx 更改为 https://ContosoEUR.sharepoint.com/sites/projectx</span><span class="sxs-lookup"><span data-stu-id="57bf8-152">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projectx</span></span>

<span data-ttu-id="57bf8-153">对于没有 Office 365 组关联的站点，你也可以通过使用 `-DestinationUrl` 参数来重命名站点。</span><span class="sxs-lookup"><span data-stu-id="57bf8-153">For sites with no Office 365 Group association, you can also rename the site by using the `-DestinationUrl` parameter.</span></span> <span data-ttu-id="57bf8-154">例如：</span><span class="sxs-lookup"><span data-stu-id="57bf8-154">For example:</span></span>

<span data-ttu-id="57bf8-155">https://Contoso.sharepoint.com/sites/projectx 重命名为 https://ContosoEUR.sharepoint.com/sites/projecty</span><span class="sxs-lookup"><span data-stu-id="57bf8-155">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projecty</span></span>

<span data-ttu-id="57bf8-156">若要开始站点移动，请运行：</span><span class="sxs-lookup"><span data-stu-id="57bf8-156">To start the site move, run:</span></span>

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![显示 Start-SPOSiteContentMove cmdlet 的 PowerShell 窗口的屏幕截图](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a><span data-ttu-id="57bf8-158">为 Office 365 组连接的站点开始 SharePoint 站点地理位置移动</span><span class="sxs-lookup"><span data-stu-id="57bf8-158">Start a SharePoint site geo move for an Office 365 Group-connected site</span></span>

<span data-ttu-id="57bf8-159">若要移动 Office 365 组连接的站点，全局管理员首先必须更改 Office 365 组的首选数据位置 (PDL) 属性。</span><span class="sxs-lookup"><span data-stu-id="57bf8-159">To move an Office 365 Group-connected site, the global administrator must first change the Preferred Data Location (PDL) attribute for the Office 365 Group.</span></span>

<span data-ttu-id="57bf8-160">若要为 Office 365 组设置 PDL，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="57bf8-160">To set the PDL for an Office 365 Group:</span></span>

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
<span data-ttu-id="57bf8-161">更新 PDL 之后，你就可以开始站点移动：</span><span class="sxs-lookup"><span data-stu-id="57bf8-161">Once you have updated the PDL, you can start the site move:</span></span> 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a><span data-ttu-id="57bf8-162">取消 SharePoint 站点地理位置移动</span><span class="sxs-lookup"><span data-stu-id="57bf8-162">Cancel a SharePoint site geo move</span></span>

<span data-ttu-id="57bf8-163">如果移动尚未进行或尚未完成，则可以使用 `Stop-SPOSiteContentMove` cmdlet 来停止 SharePoint 站点地理位置移动。</span><span class="sxs-lookup"><span data-stu-id="57bf8-163">You can stop a SharePoint site geo move, provided the move is not in progress or completed by using the `Stop-SPOSiteContentMove` cmdlet.</span></span>

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a><span data-ttu-id="57bf8-164">确定 SharePoint 站点地理位置移动的状态</span><span class="sxs-lookup"><span data-stu-id="57bf8-164">Determining the status of a SharePoint site geo move</span></span>

<span data-ttu-id="57bf8-165">通过使用以下 cmdlet，你可以确定站点移入或移出所连接到的地理位置的状态：</span><span class="sxs-lookup"><span data-stu-id="57bf8-165">You can determine the status of a site move in our out of the geo that you are connected to by using the following cmdlets:</span></span>

- <span data-ttu-id="57bf8-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate)（非组连接的站点）</span><span class="sxs-lookup"><span data-stu-id="57bf8-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (non-Group-connected sites)</span></span>
- <span data-ttu-id="57bf8-167">Get-SPOUnifiedGroupMoveState（组连接的站点）</span><span class="sxs-lookup"><span data-stu-id="57bf8-167">Get-SPOUnifiedGroupMoveState (Group-connected sites)</span></span>

<span data-ttu-id="57bf8-168">使用 `-SourceSiteUrl` 参数来指定要查看其移动状态的站点。</span><span class="sxs-lookup"><span data-stu-id="57bf8-168">Use the `-SourceSiteUrl` parameter to specify the site for which you want to see move status.</span></span>

<span data-ttu-id="57bf8-169">下表描述了这些移动状态。</span><span class="sxs-lookup"><span data-stu-id="57bf8-169">The move statuses are described in the following table.</span></span>

|<span data-ttu-id="57bf8-170">状态</span><span class="sxs-lookup"><span data-stu-id="57bf8-170">Status</span></span>|<span data-ttu-id="57bf8-171">说明</span><span class="sxs-lookup"><span data-stu-id="57bf8-171">Description</span></span>|
|:-----|:----------|
|<span data-ttu-id="57bf8-172">Ready to Trigger</span><span class="sxs-lookup"><span data-stu-id="57bf8-172">Ready to Trigger</span></span>|<span data-ttu-id="57bf8-173">移动尚未开始。</span><span class="sxs-lookup"><span data-stu-id="57bf8-173">The move has not started.</span></span>|
|<span data-ttu-id="57bf8-174">Scheduled</span><span class="sxs-lookup"><span data-stu-id="57bf8-174">Scheduled</span></span>|<span data-ttu-id="57bf8-175">移动在队列中，但尚未开始。</span><span class="sxs-lookup"><span data-stu-id="57bf8-175">The move is in queue but has not yet started.</span></span>|
|<span data-ttu-id="57bf8-176">InProgress (n/4)</span><span class="sxs-lookup"><span data-stu-id="57bf8-176">InProgress (n/4)</span></span>|<span data-ttu-id="57bf8-177">移动正在进行中，状态为以下之一：验证 (1/4)、备份 (2/4)、还原 (3/4)、清除 (4/4)。</span><span class="sxs-lookup"><span data-stu-id="57bf8-177">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span>|
|<span data-ttu-id="57bf8-178">Success</span><span class="sxs-lookup"><span data-stu-id="57bf8-178">Success</span></span>|<span data-ttu-id="57bf8-179">移动已成功完成。</span><span class="sxs-lookup"><span data-stu-id="57bf8-179">The move has completed successfully.</span></span>|
|<span data-ttu-id="57bf8-180">Failed</span><span class="sxs-lookup"><span data-stu-id="57bf8-180">Failed</span></span>|<span data-ttu-id="57bf8-181">移动失败。</span><span class="sxs-lookup"><span data-stu-id="57bf8-181">The move failed.</span></span>|

<span data-ttu-id="57bf8-182">你也可以应用 `-Verbose` 选项来查看有关移动的其他信息。</span><span class="sxs-lookup"><span data-stu-id="57bf8-182">You can also apply the `-Verbose` option to see additional information about the move.</span></span>

## <a name="user-experience"></a><span data-ttu-id="57bf8-183">用户体验</span><span class="sxs-lookup"><span data-stu-id="57bf8-183">User experience</span></span>

<span data-ttu-id="57bf8-184">将站点用户的站点移动到其他地理位置时，应最大限度地减少用户会注意到的中断情况。</span><span class="sxs-lookup"><span data-stu-id="57bf8-184">Site users should notice minimal disruption when their site is moved to a different geo location.</span></span> <span data-ttu-id="57bf8-185">除了在移动过程中会有很短的一段时间处于只读状态外，现有链接和权限在移动完成后将继续按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="57bf8-185">Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="site"></a><span data-ttu-id="57bf8-186">站点</span><span class="sxs-lookup"><span data-stu-id="57bf8-186">Site</span></span>

<span data-ttu-id="57bf8-187">移动进行时站点会设为只读状态。</span><span class="sxs-lookup"><span data-stu-id="57bf8-187">While the move is in progress the site is set to read-only.</span></span> <span data-ttu-id="57bf8-188">移动完成后，当用户单击书签或其他站点链接时，系统会将用户定向到新地理位置中的新站点。</span><span class="sxs-lookup"><span data-stu-id="57bf8-188">Once the move is completed, the user is directed to the new site in the new geo location when they click on bookmarks or other links to the site.</span></span>

### <a name="permissions"></a><span data-ttu-id="57bf8-189">权限</span><span class="sxs-lookup"><span data-stu-id="57bf8-189">Permissions</span></span>

<span data-ttu-id="57bf8-190">在移动进行时和完成后，有权访问站点的用户将仍然能够继续访问站点。</span><span class="sxs-lookup"><span data-stu-id="57bf8-190">Users with permissions to site will continue to have access to the site during the move and after it's complete.</span></span>

### <a name="sync-client"></a><span data-ttu-id="57bf8-191">同步客户端</span><span class="sxs-lookup"><span data-stu-id="57bf8-191">Sync Client</span></span>

<span data-ttu-id="57bf8-192">站点移动完成后，同步客户端将自动检测并将同步无缝转移到新站点位置。</span><span class="sxs-lookup"><span data-stu-id="57bf8-192">The sync client will automatically detect and seamlessly transfer syncing to the new site location once the site move is complete.</span></span> <span data-ttu-id="57bf8-193">用户无需再次登录或进行其他操作。</span><span class="sxs-lookup"><span data-stu-id="57bf8-193">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="57bf8-194">（需要同步客户端版本 17.3.6943.0625 或更高版本。）</span><span class="sxs-lookup"><span data-stu-id="57bf8-194">(Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="57bf8-195">如果用户在移动进行时更新文件，则同步客户端将告知用户“在移动过程中，文件上传处于待定状态”。</span><span class="sxs-lookup"><span data-stu-id="57bf8-195">If a user updates a file while the move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="57bf8-196">共享链接</span><span class="sxs-lookup"><span data-stu-id="57bf8-196">Sharing links</span></span>

<span data-ttu-id="57bf8-197">SharePoint 站点地理位置移动完成后，被移动文件的现有共享链接将自动重定向到新地理位置。</span><span class="sxs-lookup"><span data-stu-id="57bf8-197">When the SharePoint site geo move completes, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="most-recently-used-files-in-office-mru"></a><span data-ttu-id="57bf8-198">Office 中最近使用的文件 (MRU)</span><span class="sxs-lookup"><span data-stu-id="57bf8-198">Most Recently Used files in Office (MRU)</span></span>

<span data-ttu-id="57bf8-199">移动完成后，MRU 服务将随站点 URL 及其内容 URL 一起更新。</span><span class="sxs-lookup"><span data-stu-id="57bf8-199">The MRU service is updated with the site url and its content URLs once the move completes.</span></span> <span data-ttu-id="57bf8-200">这适用于 Word、Excel 和 PowerPoint。</span><span class="sxs-lookup"><span data-stu-id="57bf8-200">This applies to Word, Excel, and PowerPoint.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="57bf8-201">OneNote 体验</span><span class="sxs-lookup"><span data-stu-id="57bf8-201">OneNote experience</span></span>

<span data-ttu-id="57bf8-202">站点移动完成后，OneNote win32 客户端和 UWP （通用）应用会自动检测并将笔记本无缝同步到新站点位置。</span><span class="sxs-lookup"><span data-stu-id="57bf8-202">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new site location once site move is complete.</span></span> <span data-ttu-id="57bf8-203">用户无需再次登录或进行其他操作。</span><span class="sxs-lookup"><span data-stu-id="57bf8-203">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="57bf8-204">站点移动正在进行时，用户只会看到笔记本同步将失败的指示符。</span><span class="sxs-lookup"><span data-stu-id="57bf8-204">The only visible indicator to the user is notebook sync would fail when site move is in progress.</span></span> <span data-ttu-id="57bf8-205">以下 OneNote 客户端版本上提供了此体验：</span><span class="sxs-lookup"><span data-stu-id="57bf8-205">This experience is available on the following OneNote client versions:</span></span>

- <span data-ttu-id="57bf8-206">OneNote win32 – 版本 16.0.8326.2096（及更高版本）</span><span class="sxs-lookup"><span data-stu-id="57bf8-206">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>
- <span data-ttu-id="57bf8-207">OneNote UWP – 版本16.0.8431.1006（及更高版本）</span><span class="sxs-lookup"><span data-stu-id="57bf8-207">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>
- <span data-ttu-id="57bf8-208">OneNote 移动应用 – 版本 16.0.8431.1011（及更高版本）</span><span class="sxs-lookup"><span data-stu-id="57bf8-208">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-applicable-to-office-365-group-connected-sites"></a><span data-ttu-id="57bf8-209">Teams（适用于 Office 365 组连接的站点）</span><span class="sxs-lookup"><span data-stu-id="57bf8-209">Teams (applicable to Office 365 Group connected sites)</span></span>

<span data-ttu-id="57bf8-210">SharePoint 站点地理位置移动完成后，用户将能在 Teams 应用访问其 Office 365 组站点文件。</span><span class="sxs-lookup"><span data-stu-id="57bf8-210">When the SharePoint site geo move completes, users will have access to their Office 365 Group site files on the Teams app.</span></span> <span data-ttu-id="57bf8-211">此外，在地理位置移动之前通过 Teams 聊天从其站点中共享的文件在移动完成后将继续工作。</span><span class="sxs-lookup"><span data-stu-id="57bf8-211">Additionally, files shared via Teams chat from their site prior to geo move will continue to work after move is complete.</span></span>

### <a name="sharepoint-mobile-app-iosandroid"></a><span data-ttu-id="57bf8-212">SharePoint 移动应用 (iOS/Android)</span><span class="sxs-lookup"><span data-stu-id="57bf8-212">SharePoint Mobile App (iOS/Android)</span></span>

<span data-ttu-id="57bf8-213">SharePoint 移动应用跨地理位置兼容，并能够检测站点的新地理位置。</span><span class="sxs-lookup"><span data-stu-id="57bf8-213">The SharePoint Mobile App is cross geo compatible and able to detect the site's new geo location.</span></span>

### <a name="sharepoint-workflows"></a><span data-ttu-id="57bf8-214">SharePoint 工作流</span><span class="sxs-lookup"><span data-stu-id="57bf8-214">SharePoint workflows</span></span>

<span data-ttu-id="57bf8-215">需要在站点移动之后重新发布 SharePoint 2013 工作流。</span><span class="sxs-lookup"><span data-stu-id="57bf8-215">SharePoint 2013 workflows need to be republished after the site move.</span></span> <span data-ttu-id="57bf8-216">SharePoint 2010 工作流应会继续正常工作。</span><span class="sxs-lookup"><span data-stu-id="57bf8-216">SharePoint 2010 workflows should continue to function normally.</span></span>

### <a name="apps"></a><span data-ttu-id="57bf8-217">应用</span><span class="sxs-lookup"><span data-stu-id="57bf8-217">Apps</span></span>

<span data-ttu-id="57bf8-218">如果移动具有应用的站点，你必须在站点的新地理位置重新实例化应用，因为应用及其连接在目标地理位置中可能不可用。</span><span class="sxs-lookup"><span data-stu-id="57bf8-218">If you are moving a site with apps, you must re-instantiate the app in the site's new geo location as the app and its connections may not be available in the destination geo location.</span></span>

### <a name="flow"></a><span data-ttu-id="57bf8-219">流程</span><span class="sxs-lookup"><span data-stu-id="57bf8-219">Flow</span></span>

<span data-ttu-id="57bf8-220">在大多数情况，流程在 SharePoint 站点地理位置移动后将继续工作。</span><span class="sxs-lookup"><span data-stu-id="57bf8-220">In most cases Flows will continue to work after a SharePoint site geo move.</span></span> <span data-ttu-id="57bf8-221">我们建议你在移动完成后测试流程。</span><span class="sxs-lookup"><span data-stu-id="57bf8-221">We recommend that you test them once the move has completed.</span></span>

### <a name="powerapps"></a><span data-ttu-id="57bf8-222">PowerApps</span><span class="sxs-lookup"><span data-stu-id="57bf8-222">PowerApps</span></span>

<span data-ttu-id="57bf8-223">需要在目标位置中重新创建 PowerApps。</span><span class="sxs-lookup"><span data-stu-id="57bf8-223">PowerApps need to be recreated in the destination location.</span></span>

### <a name="data-movement-between-geo-locations"></a><span data-ttu-id="57bf8-224">地理位置之间的数据移动</span><span class="sxs-lookup"><span data-stu-id="57bf8-224">Data movement between geo locations</span></span>

<span data-ttu-id="57bf8-225">SharePoint 为其内容使用 Azure Blob 存储，而与站点关联的元数据及其文件存储在 SharePoint 内。</span><span class="sxs-lookup"><span data-stu-id="57bf8-225">SharePoint uses Azure Blob storage for its content, while the metadata associated with sites and its files is stored within SharePoint.</span></span> <span data-ttu-id="57bf8-226">将站点从其源地理位置移到目标位置后，服务也会移动其关联的 Blob 存储。</span><span class="sxs-lookup"><span data-stu-id="57bf8-226">After the site is moved from its source geo location to its destination geo location, the service will also move its associated Blob Storage.</span></span> <span data-ttu-id="57bf8-227">Blob 存储移动将在大约 40 天内完成。</span><span class="sxs-lookup"><span data-stu-id="57bf8-227">Blob Storage moves complete in approximately 40 days.</span></span> 
