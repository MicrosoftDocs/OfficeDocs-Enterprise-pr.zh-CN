---
title: 创建具有特定 PDL 的 Microsoft 365 组
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: 了解如何在多地理位置环境中创建具有指定首选数据位置的 Microsoft 365 组。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1648a9c974e7d25d989156c5a8e2d6818727a3b6
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606828"
---
# <a name="create-a-microsoft-365-group-with-a-specific-pdl"></a><span data-ttu-id="d26bf-103">创建具有特定 PDL 的 Microsoft 365 组</span><span class="sxs-lookup"><span data-stu-id="d26bf-103">Create a Microsoft 365 Group with a specific PDL</span></span>

<span data-ttu-id="d26bf-104">在多地理位置环境中的用户创建 Microsoft 365 组时，组首选数据位置将自动设置为用户的。</span><span class="sxs-lookup"><span data-stu-id="d26bf-104">When users in a multi-geo environment create a Microsoft 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="d26bf-105">全局管理员、SharePoint 管理员和 Exchange 管理员可在其所选的任何区域中创建组。</span><span class="sxs-lookup"><span data-stu-id="d26bf-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="d26bf-106">如需使用特定 PDL 创建组，可使用 SharePoint 管理中心或 Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet 执行该操作。</span><span class="sxs-lookup"><span data-stu-id="d26bf-106">If you need to create a group with a specific PDL, you can do that using from the SharePoint admin center or through the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="d26bf-107">执行此操作时，将在指定 PDL 中设置组邮箱以及与该组相关联的 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="d26bf-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="d26bf-108">若要使用您指定的 PDL 创建 Microsoft 365 组，请转到要在其中创建组网站的地理位置中的 SharePoint 管理中心。</span><span class="sxs-lookup"><span data-stu-id="d26bf-108">To create a Microsoft 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="d26bf-109">例如：</span><span class="sxs-lookup"><span data-stu-id="d26bf-109">For example:</span></span>

<span data-ttu-id="d26bf-110">如果想要在澳大利亚位置创建一个组站点，可转到 https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span><span class="sxs-lookup"><span data-stu-id="d26bf-110">If you want to create a group site in your Australia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="d26bf-111">选择“**+创建**”。</span><span class="sxs-lookup"><span data-stu-id="d26bf-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="d26bf-112">按照流程创建组站点。</span><span class="sxs-lookup"><span data-stu-id="d26bf-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="d26bf-113">将在与你发起站点创建请求的 SharePoint 管理中心相对应的地理位置中预配组站点。</span><span class="sxs-lookup"><span data-stu-id="d26bf-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="d26bf-114">使用 Exchange PowerShell</span><span class="sxs-lookup"><span data-stu-id="d26bf-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="d26bf-115">连接到 Exchange Online PowerShell，并传递包含地理位置代码的 *-MailBoxRegion* 参数。</span><span class="sxs-lookup"><span data-stu-id="d26bf-115">Connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="d26bf-116">例如：</span><span class="sxs-lookup"><span data-stu-id="d26bf-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![New-UnifiedGroup PowerShell cmdlet 及语法的屏幕截图](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="d26bf-118">请注意，SharePoint 组站点设置是按需进行的。</span><span class="sxs-lookup"><span data-stu-id="d26bf-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="d26bf-119">将在组所有者或成员首次试图访问站点时对其进行设置。</span><span class="sxs-lookup"><span data-stu-id="d26bf-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="d26bf-120">地理位置代码</span><span class="sxs-lookup"><span data-stu-id="d26bf-120">Geo location codes</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="related-topics"></a><span data-ttu-id="d26bf-121">相关主题</span><span class="sxs-lookup"><span data-stu-id="d26bf-121">Related topics</span></span>

[<span data-ttu-id="d26bf-122">连接到 Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="d26bf-122">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
