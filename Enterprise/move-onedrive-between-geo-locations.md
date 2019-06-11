---
title: 将 OneDrive 站点移动到其他地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何将 OneDrive 站点移到其他地理位置。
ms.openlocfilehash: 352e8317a3f62e23c4dc0faed4cb412707f525d8
ms.sourcegitcommit: 921545ad533001a7ab055d3e6b19bfc8869df286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "34814714"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>将 OneDrive 站点移动到其他地理位置 

使用 OneDrive 异地移动，可将用户的 OneDrive 移动到其他地理位置。OneDrive 异地移动由 SharePoint Online 管理员或 Office 365 全局管理员执行。在启动 OneDrive 异地移动前，请确保通知其 OneDrive 要被移动的用户，并建议他们在移动期间关闭所有文件。（如果用户在移动期间有使用 Office 客户端打开的文档，则在移动完成后，需要将该文档保存到新位置。）如有需要，可将移动设置为在未来的某个时间执行。

OneDrive 服务使用 Azure Blob 存储来存储内容。与用户的 OneDrive 关联的存储 Blob 将在目标 OneDrive 对用户可用后的 40 天内从源地理位置移动到目标地理位置。目标 OneDrive 可用后，将立即恢复对用户的 OneDrive 的访问。

在 OneDrive 异地移动窗口期间（约 2-6 小时），用户的 OneDrive 将被设置为只读。用户仍可通过 OneDrive 同步客户端访问其文件或访问其在 SharePoint Online 中的 OneDrive 站点。OneDrive 异地移动完成后，当用户导航到 Office 365 应用启动器中的 OneDrive 时，将被自动连接到他们在目标地理位置中的 OneDrive。同步客户端将自动从新位置开始同步。

执行本文中的步骤需要安装 [Microsoft SharePoint Online PowerShell 模块](https://www.microsoft.com/en-us/download/details.aspx?id=35588)。

## <a name="communicating-to-your-users"></a>向用户传达

如果在地理位置之间移动 OneDrive 网站，请务必向用户传达预期内容。这有助于减少用户混淆并联系支持人员。移动前向用户发送电子邮件，让他们了解以下信息：

- 移动应该开始的时间和需要花费的时长
- 其 OneDrive 要移动到的地理位置和用于访问新位置的 URL
- 移动期间，他们应关闭文件，不进行任何编辑。
- 文件权限和共享不会因移动而更改。
- [多地理位置环境中的用户体验](multi-geo-user-experience.md)预期将呈现的内容

移动成功后，务必向用户发送电子邮件，告知他们可在 OneDrive 中恢复工作。

## <a name="scheduling-onedrive-site-moves"></a>安排 OneDrive 网站移动

可以提前安排 OneDrive 网站移动（在本文后面介绍）。建议先通过少数用户验证工作流和通信策略。如果你对该过程感到满意，可以按如下方式安排移动：

- 一次最多可以安排 4,000 次移动。
- 移动开始后，可以安排更多移动操作，在在队列及任何给定时间内最多有 4,000 个待处理移动。
- 建议每月不要安排超过 4,000 次移动。

## <a name="moving-a-onedrive-site"></a>移动 OneDrive 网站

若要执行 OneDrive 异地移动，租户管理员必须首先将用户的首选数据位置 (PDL) 设置为相应的地理位置。PDL 一旦设置，请等待至少 24 小时，以使 PDL 更新在 OneDrive 异地移动开始前跨地理位置同步。

在使用异地移动 cmdlet 时，使用以下语法连接到用户当前 OneDrive 地理位置的 SPO 服务：

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

例如，若要移动用户“Matt@contosoenergy.onmicrosoft.com”的 OneDrive，请连接到 EUR SharePoint 管理中心，因为该用户的 OneDrive 位于 EUR 地理位置：

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![显示 connect-sposervice cmdlet 的 PowerShell 窗口的屏幕截图](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>验证环境

在启动 OneDrive 异地移动前，我们建议验证环境。

要确保所有地理位置都可兼容，请运行：

`Get-SPOGeoMoveCrossCompatibilityStatus`

你将会看到可以在其中移动的地理位置和天气内容列表将显示为“兼容”。 如果命令返回“不兼容”，请稍后重新验证状态。

举例来说，如果 OneDrive 包含子网站，则不能移动它。 你可以将 Start-SPOUserAndContentMove cmdlet 与 -ValidationOnly 参数结合使用，以验证 OneDrive 是否可以移动：

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

如果 OneDrive 可以移动，则返回“成功”，如果存在阻止 OneDrive 移动的法定保留或子网站，则返回“失败”。验证 OneDrive 可以移动后，即可开始移动。

## <a name="start-a-onedrive-geo-move"></a>启动 OneDrive 异地移动

若要开始移动，请运行：  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

使用以下参数：

-   _UserPrincipalName_ – 要移动其 OneDrive 的用户的 UPN。

-   _DestinationDataLocation_ – 要移动的 OneDrive 的地理位置。该位置应与用户的首选数据位置相同。

例如，若要将 matt@contosoenergy.onmicrosoft.com 的 OneDrive 从 EUR 移动到 AUS，请运行：

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![显示 Start-SPOUserAndContentMove cmdlet 的 PowerShell 窗口的屏幕截图](media/move-onedrive-between-geo-locations-image2.png)

若要设置在以后执行的异地移动，请使用以下参数之一：

-   _PreferredMoveBeginDate_ – 可能在此指定的时间内开始移动。必须使用协调世界时 (UTC) 指定时间。

-   _PreferredMoveEndDate_ – 可能在此指定的时间内完成移动。必须使用协调世界时 (UTC) 指定时间。 

## <a name="cancel-a-onedrive-geo-move"></a>取消 OneDrive 异地移动 

如果移动尚未进行或尚未完成，可以使用 cmdlet 来停止移动用户的 OneDrive：

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

其中 _UserPrincipalName_ 是你想要停止移动其 OneDrive 的用户的 UPN。

## <a name="determining-current-status"></a>确定当前状态

可以使用 Get-SPOUserAndContentMoveState cmdlet 在地理位置内外查看你所连接到的 OneDrive 异地移动的状态。

下表描述了这些移动状态。

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
<td align="left">移动尚未开始。</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">移动正在进行中，状态为以下之一：验证 (1/4)、备份 (2/4)、还原 (3/4)、清除 (4/4)。</td>
</tr>
<tr class="odd">
<td align="left">Success</td>
<td align="left">移动已成功完成。</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">移动失败。</td>
</tr>
</tbody>
</table>

若要查找特定用户的移动状态，请使用 UserPrincipalName 参数：

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

若要在地理位置内外查找你所连接到的所有移动状态，请使用含有以下值之一的 MoveState 参数：NotStarted、InProgress、Success、Failed、All。

`Get-SPOUserAndContentMoveState -MoveState <value>`

此外，还可以添加 `-Verbose` 参数，以获取移动状态更为详细的说明。

## <a name="user-experience"></a>用户体验

在用户的 OneDrive 被移动到其他地理位置时，OneDrive 用户应会注意到最小的中断。除了在移动期间的简要只读状态以外，一旦移动完成，现有链接和权限即可继续按预期运行。

### <a name="onedrive-for-business"></a>OneDrive for Business

当移动进行时，用户的 OneDrive 被设置为只读状态。一旦移动完成，当用户导航到 Office 365 应用启动器或 Web 浏览器中的 OneDrive 时，用户即被定向到他们在新地理位置的 OneDrive。

### <a name="permissions-on-onedrive-content"></a>OneDrive 内容权限

在移动进行时和完成后，有权访问 OneDrive 内容的用户将仍然能够继续访问内容。

### <a name="onedrive-sync-client"></a>OneDrive 同步客户端 

OneDrive 异地移动完成后，OneDrive 同步客户端将自动检测同步并将其无缝转移到新的 OneDrive 位置。用户无需重新登录或执行任何其他操作。（需要 17.3.6943.0625 版或更高版本同步客户端。）

如果用户在 OneDrive 异地移动进行时更新文件，则同步客户端将告知用户“在移动过程中，文件上传处于待定状态”。

### <a name="sharing-links"></a>共享链接 

OneDrive 异地移动完成后，被移动文件的现有共享链接将自动重定向到新地理位置。

### <a name="onenote-experience"></a>OneNote 体验 

OneDrive 异地移动完成后，OneNote win32 客户端和 UWP（通用）应用将自动检测笔记本并将其无缝同步到新的 OneDrive 位置。用户无需重新登录或执行任何其他操作。对用户唯一可见的指示符是，当 OneDrive 异地移动进行时，笔记本同步可能失败。以下 OneNote 客户端版本提供了此体验：

-   OneNote win32 – 版本 16.0.8326.2096（及更高版本）

-   OneNote UWP – 版本16.0.8431.1006（及更高版本）

-   OneNote 移动应用 – 版本 16.0.8431.1011（及更高版本）

### <a name="teams-app"></a>Teams 应用

在 OneDrive 异地移动完成后，用户将可以访问其在 Teams 应用上的 OneDrive 文件。此外，在异地移动前通过 Teams 聊天从其 OneDrive 中共享的文件将可在移动完成后继续使用。

### <a name="onedrive-for-business-mobile-app-ios"></a>OneDrive for Business 移动应用 (iOS) 

在 OneDrive 异地移动完成后，用户需要在 iOS 移动应用上注销并重新登录，以同步到新的 OneDrive 位置。

### <a name="existing-followed-groups-and-sites"></a>现有已关注组和网站

已关注网站和组将显示在用户的 OneDrive for Business 中，而无关其地理位置。在其他地理位置托管的网站和组将在单独的标签页中打开。
