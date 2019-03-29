---
title: 使用特定 PDL 创建 Office 365 组
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何在多地理位置环境中使用指定的首选数据位置创建 Office 365 组。
ms.openlocfilehash: a46a34d9fd5be9b3acda5ee3859f4eed08797b7c
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "30933950"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="0f1c9-103">使用特定 PDL 创建 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="0f1c9-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="0f1c9-104">当多地理位置环境中的用户创建 Office 365 组时，组首选数据位置将自动设置为用户的该位置。</span><span class="sxs-lookup"><span data-stu-id="0f1c9-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="0f1c9-105">如果需要使用特定 PDL 创建组，你可以使用 Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet 执行该操作。</span><span class="sxs-lookup"><span data-stu-id="0f1c9-105">If you need to create a group with a specific PDL, you can do that using the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="0f1c9-106">执行此操作时，将在指定 PDL 中设置组邮箱以及与该组相关联的 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="0f1c9-106">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="0f1c9-107">你必须是全局管理员或 SharePoint Online 或 Exchange Online 管理员才能执行此操作。</span><span class="sxs-lookup"><span data-stu-id="0f1c9-107">You must be a global administrator or a SharePoint Online or Exchange Online administrator to do this.</span></span>

<span data-ttu-id="0f1c9-108">若要使用指定的 PDL 创建 Office 365 组，请连接到 Exchange Online PowerShell，并传递包含地理位置代码的 *-MailBoxRegion* 参数。</span><span class="sxs-lookup"><span data-stu-id="0f1c9-108">To create an Office 365 Group with the PDL that you specify, connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="0f1c9-109">例如：</span><span class="sxs-lookup"><span data-stu-id="0f1c9-109">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![New-UnifiedGroup PowerShell cmdlet 及语法的屏幕截图](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="0f1c9-111">请注意，SharePoint 组站点设置是按需进行的。</span><span class="sxs-lookup"><span data-stu-id="0f1c9-111">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="0f1c9-112">将在组所有者或成员首次试图访问站点时对其进行设置。</span><span class="sxs-lookup"><span data-stu-id="0f1c9-112">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="0f1c9-113">地理位置代码</span><span class="sxs-lookup"><span data-stu-id="0f1c9-113">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="0f1c9-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f1c9-114">See also</span></span>

[<span data-ttu-id="0f1c9-115">连接到 Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f1c9-115">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)