---
title: 将一个 OneDrive 网站移至不同的地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解如何将一个 OneDrive 网站移至不同的地理位置。
ms.openlocfilehash: 7ce9106fa7d8d144f0f8935713b4df926a73fb6b
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="1d0ee-103">将一个 OneDrive 网站移至不同的地理位置</span><span class="sxs-lookup"><span data-stu-id="1d0ee-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="1d0ee-p101">使用 OneDrive 地区移动，可以将用户的 OneDrive 移动到不同的地理位置。SharePoint Online 管理员或 Office 365 全局管理员执行 OneDrive 地区移动。在开始移动地理 OneDrive 之前，请务必通知的用户正在移动的 OneDrive，并建议他们移动的持续时间内关闭所有文件。（如果用户使用 Office 客户端在移动，然后在打开的文档移动的完成文档需要保存到新位置。如果需要，可以在未来的时间，安排移动。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="1d0ee-p102">OneDrive 服务使用 Azure Blob 存储来存储内容。与用户的 OneDrive 存储 blob 将被移动从源到目标地理位置的目标与用户的可用的 OneDrive 的 40 天内。一旦目标 OneDrive 可将恢复对用户的 OneDrive 的访问权限。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="1d0ee-p103">在 OneDrive 地区移动窗口 （大约 2-6 小时） 用户的 OneDrive 设置为只读。用户仍然可以访问他们的文件通过 OneDrive 同步客户端或他们在 SharePoint Online 的 OneDrive 站点。OneDrive 地区移动完成后，用户将自动连接到其目标地理位置的 OneDrive 时他们在 Office 365 提供应用程序启动器会导航到 OneDrive。同步客户端将自动开始从新位置同步。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="1d0ee-115">本文中的步骤需要[Microsoft SharePoint 在线 PowerShell 模块](https://www.microsoft.com/en-us/download/details.aspx?id=35588)。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="1d0ee-116">移动 OneDrive 网站</span><span class="sxs-lookup"><span data-stu-id="1d0ee-116">Moving a OneDrive site</span></span>

<span data-ttu-id="1d0ee-p104">若要执行 OneDrive 地区移动，请组织管理员必须先将用户的首选数据位置 (PDL) 设置为适当的地理位置。PDL 设置后，请等待 PDL 更新跨地理位置同步开始 OneDrive 地区移动前至少 24 小时。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="1d0ee-119">当使用地区移动的 cmdlet 时，连接到 SPO 服务中用户的当前 OneDrive 地理位置，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="1d0ee-120">例如： 若要移动的用户 'Matt@contosoenergy.onmicrosoft.com' OneDrive，连接到欧元 SharePoint 管理中心用户的 OneDrive 欧元的地理位置是：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="1d0ee-121">验证环境</span><span class="sxs-lookup"><span data-stu-id="1d0ee-121">Validating the environment</span></span>

<span data-ttu-id="1d0ee-122">在开始之前 OneDrive 地区移动，我们建议您验证环境。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="1d0ee-123">若要确保所有地理位置都兼容，请运行：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="1d0ee-p105">如果 OneDrive 处于法律封存或如果它包含子网站时，不能移动。您可以使用用-ValidationOnly 参数启动 SPOUserAndContentMove cmdlet 验证如果 OneDrive 能够移动：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="1d0ee-p106">如果 OneDrive 是准备好移动或失败如果没有法律封存或子网站可以防止移动，这将返回成功。一旦您有验证 OneDrive 就可以移动，可以开始移动。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="1d0ee-128">开始 OneDrive 地区移动</span><span class="sxs-lookup"><span data-stu-id="1d0ee-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="1d0ee-129">若要开始移动，运行：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="1d0ee-130">使用这些参数：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-130">Using these parameters:</span></span>

-   <span data-ttu-id="1d0ee-131">_范围内_--正在移动的 OneDrive 的用户的 UPN。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="1d0ee-p107">_DestinationDataLocation_ — OneDrive 需要移动的地理位置。这应该是与用户的首选的数据位置相同。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="1d0ee-134">建议运行`Get-SPOGeoMoveStateCompatibility`与`ValidationOnly`之前启动 OneDrive 地区移动。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="1d0ee-135">例如，若要移动的 matt@contosoenergy.onmicrosoft.com OneDrive 从欧元到澳大利亚，运行：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="1d0ee-136">要安排稍后进行的地区移动，请使用下列参数之一：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="1d0ee-p108">_PreferredMoveBeginDate_ – 移动很可能开始在此指定的时间。必须指定时间以协调世界时 (UTC)。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p108">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="1d0ee-p109">_PreferredMoveEndDate_ – 移动很可能在尽力执行该指定时间之前完成。必须指定时间以协调世界时 (UTC)。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p109">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="1d0ee-141">取消了 OneDrive 地区移动</span><span class="sxs-lookup"><span data-stu-id="1d0ee-141">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="1d0ee-142">您可以停止地区移动用户的 OneDrive 的移动过程中不是前提或使用 cmdlet 完成：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-142">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="1d0ee-143">其中_范围内_为其 OneDrive 移动要停止的用户的 UPN。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-143">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="1d0ee-144">确定当前状态</span><span class="sxs-lookup"><span data-stu-id="1d0ee-144">Determining current status</span></span>

<span data-ttu-id="1d0ee-145">您可以检查地区移入或移出相连使用 Get SPOUserAndContentMoveState cmdlet 的地理 OneDrive 的状态。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-145">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="1d0ee-146">移动状态下表所述。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-146">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="1d0ee-147"><strong>状态</strong></span><span class="sxs-lookup"><span data-stu-id="1d0ee-147"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="1d0ee-148"><strong>说明</strong></span><span class="sxs-lookup"><span data-stu-id="1d0ee-148"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="1d0ee-149">NotStarted</span><span class="sxs-lookup"><span data-stu-id="1d0ee-149">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="1d0ee-150">尚未开始移动。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-150">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1d0ee-151">正在进行 (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="1d0ee-151">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="1d0ee-152">在移动过程中进度处于以下状态之一： 验证 (1/4)，备份 (2/4)，还原 (3/4)，清理 (4/4)。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-152">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="1d0ee-153">成功</span><span class="sxs-lookup"><span data-stu-id="1d0ee-153">Success</span></span></td>
<td align="left"><span data-ttu-id="1d0ee-154">移动已成功完成。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-154">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1d0ee-155">Failed</span><span class="sxs-lookup"><span data-stu-id="1d0ee-155">Failed</span></span></td>
<td align="left"><span data-ttu-id="1d0ee-156">移动失败。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-156">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="1d0ee-157">若要查找特定用户的移动的状态，使用范围内参数：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-157">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="1d0ee-158">若要查找所有这些移动的状态，或从您连接到的地理位置，使用 MoveState 参数具有下列值之一： NotStarted、 正在进行、 成功、 失败，所有。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-158">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="1d0ee-159">您还可以添加`-Verbose`参数有关的移动状态的更详细说明。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-159">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="1d0ee-160">用户体验</span><span class="sxs-lookup"><span data-stu-id="1d0ee-160">User Experience</span></span>

<span data-ttu-id="1d0ee-p110">如果他们 OneDrive 移动到不同的地理位置，OneDrive 的用户应该注意到极小的中断。除了简短只读状态在移动的过程中，现有的链接和权限将继续如期完成移动后起作用。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p110">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="1d0ee-163">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="1d0ee-163">OneDrive for Business</span></span>

<span data-ttu-id="1d0ee-p111">在移动过程中用户的 OneDrive 设置为只读。完成移动后，用户被定向到新的地理位置及其 OneDrive，当 Office 365 提供应用程序启动程序或 web 浏览器导航到 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p111">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="1d0ee-166">OneDrive 内容的权限</span><span class="sxs-lookup"><span data-stu-id="1d0ee-166">Permissions on OneDrive content</span></span>

<span data-ttu-id="1d0ee-167">对 OneDrive 的内容具有权限的用户将继续在移动的过程中和完成后，必须对内容的访问。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-167">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="1d0ee-168">OneDrive 同步客户端</span><span class="sxs-lookup"><span data-stu-id="1d0ee-168">OneDrive Sync Client</span></span> 

<span data-ttu-id="1d0ee-p112">OneDrive 同步客户端将自动检测并无缝地传输同步到新的 OneDrive 位置，一旦完成 OneDrive 地区移动。用户不需要再次登录以或采取任何其他操作。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p112">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="1d0ee-171">如果用户更新文件正在 OneDrive 地区移动时，同步客户端将通知这些文件上载处于挂起状态时移动正在进行之中。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-171">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="1d0ee-172">共享链接</span><span class="sxs-lookup"><span data-stu-id="1d0ee-172">Sharing links</span></span> 

<span data-ttu-id="1d0ee-173">在 OneDrive 地区的移动完成，现有的共享的链接已移动的文件将自动重定向到新的地理位置。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-173">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="1d0ee-174">OneNote 体验</span><span class="sxs-lookup"><span data-stu-id="1d0ee-174">OneNote Experience</span></span> 

<span data-ttu-id="1d0ee-p113">OneNote win32 客户端和 UWP （通用） 的应用程序将自动检测和 OneDrive 地区移动完毕后无缝同步到新的 OneDrive 位置的笔记本。用户不需要再次登录以或采取任何其他操作。用户仅可以看见的指示灯是笔记本同步 OneDrive 地区移动时将失败。这种体验是以下 OneNote 的客户端版本上可用：</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p113">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="1d0ee-179">OneNote win32-版本 16.0.8326.2096 （及更高版本）</span><span class="sxs-lookup"><span data-stu-id="1d0ee-179">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="1d0ee-180">OneNote UWP – 版本 16.0.8431.1006 （及更高版本）</span><span class="sxs-lookup"><span data-stu-id="1d0ee-180">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="1d0ee-181">OneNote 移动应用程序 – 16.0.8431.1011 版 （及更高版本）</span><span class="sxs-lookup"><span data-stu-id="1d0ee-181">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="1d0ee-182">团队的应用程序</span><span class="sxs-lookup"><span data-stu-id="1d0ee-182">Teams app</span></span>

<span data-ttu-id="1d0ee-p114">在 OneDrive 地区移动完成，用户有权访问其团队应用程序上的 OneDrive 文件另外，共享团队聊天，从他们 OneDrive 地区移动之前通过的文件仍然可以工作在移动完成后。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p114">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="1d0ee-185">企业移动应用程序 (iOS) OneDrive</span><span class="sxs-lookup"><span data-stu-id="1d0ee-185">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="1d0ee-186">在 OneDrive 地区的移动完成，用户需要注销并重新登录在 iOS 移动应用程序同步到新的 OneDrive 位置。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-186">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="1d0ee-187">现有的执行组和站点</span><span class="sxs-lookup"><span data-stu-id="1d0ee-187">Existing followed groups and sites</span></span>

<span data-ttu-id="1d0ee-p115">随后的站点和组将显示在业务无论其地理位置的用户的 OneDrive。站点和组驻留在另一个地理位置将在单独的选项卡中打开。</span><span class="sxs-lookup"><span data-stu-id="1d0ee-p115">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
