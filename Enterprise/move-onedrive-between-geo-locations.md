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
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>将一个 OneDrive 网站移至不同的地理位置 

使用 OneDrive 地区移动，可以将用户的 OneDrive 移动到不同的地理位置。SharePoint Online 管理员或 Office 365 全局管理员执行 OneDrive 地区移动。在开始移动地理 OneDrive 之前，请务必通知的用户正在移动的 OneDrive，并建议他们移动的持续时间内关闭所有文件。（如果用户使用 Office 客户端在移动，然后在打开的文档移动的完成文档需要保存到新位置。如果需要，可以在未来的时间，安排移动。

OneDrive 服务使用 Azure Blob 存储来存储内容。与用户的 OneDrive 存储 blob 将被移动从源到目标地理位置的目标与用户的可用的 OneDrive 的 40 天内。一旦目标 OneDrive 可将恢复对用户的 OneDrive 的访问权限。

在 OneDrive 地区移动窗口 （大约 2-6 小时） 用户的 OneDrive 设置为只读。用户仍然可以访问他们的文件通过 OneDrive 同步客户端或他们在 SharePoint Online 的 OneDrive 站点。OneDrive 地区移动完成后，用户将自动连接到其目标地理位置的 OneDrive 时他们在 Office 365 提供应用程序启动器会导航到 OneDrive。同步客户端将自动开始从新位置同步。

本文中的步骤需要[Microsoft SharePoint 在线 PowerShell 模块](https://www.microsoft.com/en-us/download/details.aspx?id=35588)。

## <a name="moving-a-onedrive-site"></a>移动 OneDrive 网站

若要执行 OneDrive 地区移动，请组织管理员必须先将用户的首选数据位置 (PDL) 设置为适当的地理位置。PDL 设置后，请等待 PDL 更新跨地理位置同步开始 OneDrive 地区移动前至少 24 小时。

当使用地区移动的 cmdlet 时，连接到 SPO 服务中用户的当前 OneDrive 地理位置，请使用下面的语法：

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

例如： 若要移动的用户 'Matt@contosoenergy.onmicrosoft.com' OneDrive，连接到欧元 SharePoint 管理中心用户的 OneDrive 欧元的地理位置是：

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>验证环境

在开始之前 OneDrive 地区移动，我们建议您验证环境。

若要确保所有地理位置都兼容，请运行：

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

如果 OneDrive 处于法律封存或如果它包含子网站时，不能移动。您可以使用用-ValidationOnly 参数启动 SPOUserAndContentMove cmdlet 验证如果 OneDrive 能够移动：

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

如果 OneDrive 是准备好移动或失败如果没有法律封存或子网站可以防止移动，这将返回成功。一旦您有验证 OneDrive 就可以移动，可以开始移动。

## <a name="start-a-onedrive-geo-move"></a>开始 OneDrive 地区移动

若要开始移动，运行：  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

使用这些参数：

-   _范围内_--正在移动的 OneDrive 的用户的 UPN。

-   _DestinationDataLocation_ — OneDrive 需要移动的地理位置。这应该是与用户的首选的数据位置相同。

> [!NOTE]
> 建议运行`Get-SPOGeoMoveStateCompatibility`与`ValidationOnly`之前启动 OneDrive 地区移动。

例如，若要移动的 matt@contosoenergy.onmicrosoft.com OneDrive 从欧元到澳大利亚，运行：

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

要安排稍后进行的地区移动，请使用下列参数之一：

-   _PreferredMoveBeginDate_ – 移动很可能开始在此指定的时间。必须指定时间以协调世界时 (UTC)。

-   _PreferredMoveEndDate_ – 移动很可能在尽力执行该指定时间之前完成。必须指定时间以协调世界时 (UTC)。 

## <a name="cancel-a-onedrive-geo-move"></a>取消了 OneDrive 地区移动 

您可以停止地区移动用户的 OneDrive 的移动过程中不是前提或使用 cmdlet 完成：

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

其中_范围内_为其 OneDrive 移动要停止的用户的 UPN。

## <a name="determining-current-status"></a>确定当前状态

您可以检查地区移入或移出相连使用 Get SPOUserAndContentMoveState cmdlet 的地理 OneDrive 的状态。

移动状态下表所述。

<table>
<thead>
<tr class="header">
<th align="left"><strong>状态</strong></th>
<th align="left"><strong>说明</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">NotStarted</td>
<td align="left">尚未开始移动。</td>
</tr>
<tr class="even">
<td align="left">正在进行 (<em>n</em>/4)</td>
<td align="left">在移动过程中进度处于以下状态之一： 验证 (1/4)，备份 (2/4)，还原 (3/4)，清理 (4/4)。</td>
</tr>
<tr class="odd">
<td align="left">成功</td>
<td align="left">移动已成功完成。</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">移动失败。</td>
</tr>
</tbody>
</table>

若要查找特定用户的移动的状态，使用范围内参数：

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

若要查找所有这些移动的状态，或从您连接到的地理位置，使用 MoveState 参数具有下列值之一： NotStarted、 正在进行、 成功、 失败，所有。

`Get-SPOUserAndContentMoveState -MoveState <value>`

您还可以添加`-Verbose`参数有关的移动状态的更详细说明。

## <a name="user-experience"></a>用户体验

如果他们 OneDrive 移动到不同的地理位置，OneDrive 的用户应该注意到极小的中断。除了简短只读状态在移动的过程中，现有的链接和权限将继续如期完成移动后起作用。

### <a name="onedrive-for-business"></a>OneDrive for Business

在移动过程中用户的 OneDrive 设置为只读。完成移动后，用户被定向到新的地理位置及其 OneDrive，当 Office 365 提供应用程序启动程序或 web 浏览器导航到 OneDrive。

### <a name="permissions-on-onedrive-content"></a>OneDrive 内容的权限

对 OneDrive 的内容具有权限的用户将继续在移动的过程中和完成后，必须对内容的访问。

### <a name="onedrive-sync-client"></a>OneDrive 同步客户端 

OneDrive 同步客户端将自动检测并无缝地传输同步到新的 OneDrive 位置，一旦完成 OneDrive 地区移动。用户不需要再次登录以或采取任何其他操作。

如果用户更新文件正在 OneDrive 地区移动时，同步客户端将通知这些文件上载处于挂起状态时移动正在进行之中。

### <a name="sharing-links"></a>共享链接 

在 OneDrive 地区的移动完成，现有的共享的链接已移动的文件将自动重定向到新的地理位置。

### <a name="onenote-experience"></a>OneNote 体验 

OneNote win32 客户端和 UWP （通用） 的应用程序将自动检测和 OneDrive 地区移动完毕后无缝同步到新的 OneDrive 位置的笔记本。用户不需要再次登录以或采取任何其他操作。用户仅可以看见的指示灯是笔记本同步 OneDrive 地区移动时将失败。这种体验是以下 OneNote 的客户端版本上可用：

-   OneNote win32-版本 16.0.8326.2096 （及更高版本）

-   OneNote UWP – 版本 16.0.8431.1006 （及更高版本）

-   OneNote 移动应用程序 – 16.0.8431.1011 版 （及更高版本）

### <a name="teams-app"></a>团队的应用程序

在 OneDrive 地区移动完成，用户有权访问其团队应用程序上的 OneDrive 文件另外，共享团队聊天，从他们 OneDrive 地区移动之前通过的文件仍然可以工作在移动完成后。

### <a name="onedrive-for-business-mobile-app-ios"></a>企业移动应用程序 (iOS) OneDrive 

在 OneDrive 地区的移动完成，用户需要注销并重新登录在 iOS 移动应用程序同步到新的 OneDrive 位置。

### <a name="existing-followed-groups-and-sites"></a>现有的执行组和站点

随后的站点和组将显示在业务无论其地理位置的用户的 OneDrive。站点和组驻留在另一个地理位置将在单独的选项卡中打开。
