---
title: 删除附属位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何删除 Office 365 多地理位置中的附属位置。
ms.openlocfilehash: 68152d24c68ad31375cf882340460428424931cb
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931741"
---
# <a name="delete-a-satellite-location-in-office-365-multi-geo"></a><span data-ttu-id="0943f-103">删除 Office 365 多地理位置中的附属位置</span><span class="sxs-lookup"><span data-stu-id="0943f-103">Delete a satellite location in Office 365 Multi-Geo</span></span>

<span data-ttu-id="0943f-104">如果不再需要附属位置，可以在 SharePoint 管理中心内将它从租户中删除。</span><span class="sxs-lookup"><span data-stu-id="0943f-104">If you no longer need a satellite location, you can delete it from your tenant from the OneDrive admin center</span></span>

> [!WARNING]
> <span data-ttu-id="0943f-105">附属位置中的所有用户数据都将被永久删除。</span><span class="sxs-lookup"><span data-stu-id="0943f-105">All user data in the satellite location will be permanently deleted.</span></span> <span data-ttu-id="0943f-106">这包括所有 OneDrive for Business 内容、SharePoint 网站和 Exchange 邮箱（包括 Office 365 组邮箱）。</span><span class="sxs-lookup"><span data-stu-id="0943f-106">This includes all OneDrive for Business content, SharePoint sites and Exchange mailboxes including Office 365 Group mailboxes.</span></span> <span data-ttu-id="0943f-107">删除附属位置前，必须先将所有数据都迁移到其他附属位置或中心位置。</span><span class="sxs-lookup"><span data-stu-id="0943f-107">You must migrate any data to another satellite location or the central location before you delete the satellite location.</span></span> <span data-ttu-id="0943f-108">此操作无法撤消。</span><span class="sxs-lookup"><span data-stu-id="0943f-108">This action cannot be undone.</span></span>

<span data-ttu-id="0943f-109">只有全局管理员可以删除附属位置。</span><span class="sxs-lookup"><span data-stu-id="0943f-109">Only global administrators can delete satellite locations.</span></span>

![显示地理位置删除 UI 的多地理位置管理中心屏幕截图](media/multi-geo-delete-satellite-location.png)

<span data-ttu-id="0943f-111">删除附属位置的具体步骤</span><span class="sxs-lookup"><span data-stu-id="0943f-111">To delete a satellite location</span></span>

1. <span data-ttu-id="0943f-112">打开 SharePoint 管理中心</span><span class="sxs-lookup"><span data-stu-id="0943f-112">Open the Exchange admin center</span></span>

2. <span data-ttu-id="0943f-113">导航到“地理位置”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="0943f-113">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="0943f-114">在地图上，单击要删除的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0943f-114">On the map, click the geo location that you want to delete.</span></span>

4. <span data-ttu-id="0943f-115">单击“删除位置”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="0943f-115">Click **Delete location**.</span></span>

5. <span data-ttu-id="0943f-116">通过选择确认复选框来确认删除。</span><span class="sxs-lookup"><span data-stu-id="0943f-116">Confirm the deletion by selecting the confirmation check boxes.</span></span>

6. <span data-ttu-id="0943f-117">单击“删除”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="0943f-117">Click **Delete**.</span></span>
