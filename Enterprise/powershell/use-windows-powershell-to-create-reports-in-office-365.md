---
title: 使用 PowerShell 为 Microsoft 365 创建报告
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: 摘要：使用适用于 Microsoft 365 的 PowerShell 创建无法在 Microsoft 365 管理中心生成的报告。
ms.openlocfilehash: 855f6529445b95dd949fb672f978a82f1afd6149
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229798"
---
# <a name="use-powershell-to-create-reports-for-microsoft-365"></a><span data-ttu-id="65e9e-103">使用 PowerShell 为 Microsoft 365 创建报告</span><span class="sxs-lookup"><span data-stu-id="65e9e-103">Use PowerShell to create reports for Microsoft 365</span></span>

<span data-ttu-id="65e9e-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="65e9e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="65e9e-105">Microsoft 365 管理中心中提供很多不同的报告。</span><span class="sxs-lookup"><span data-stu-id="65e9e-105">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="65e9e-106">但是，这些报告提供的信息有限，有时你可能需要更多信息。</span><span class="sxs-lookup"><span data-stu-id="65e9e-106">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="65e9e-107">如果你需要适用于 Microsoft 365 的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="65e9e-107">That's when you need PowerShell for Microsoft 365</span></span>
  
<span data-ttu-id="65e9e-108">这些文章介绍了如何使用适用于 Microsoft 365 的 PowerShell 从你的 Microsoft 365 租户获取信息：</span><span class="sxs-lookup"><span data-stu-id="65e9e-108">These articles that describe how to use PowerShell for Microsoft 365 to obtain information from your Microsoft 365 tenant:</span></span>
  
- <span data-ttu-id="65e9e-109">使用 PowerShell for Microsoft 365 进行报告入门：</span><span class="sxs-lookup"><span data-stu-id="65e9e-109">Getting started with reporting using PowerShell for Microsoft 365:</span></span>
    
  - [<span data-ttu-id="65e9e-110">PowerShell for Microsoft 365 可以显示你无法通过管理中心看到的其他信息</span><span class="sxs-lookup"><span data-stu-id="65e9e-110">PowerShell for Microsoft 365 can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="65e9e-111">适用于 Microsoft 365 的 PowerShell 非常适合筛选数据</span><span class="sxs-lookup"><span data-stu-id="65e9e-111">PowerShell for Microsoft 365 is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="65e9e-112">适用于 Microsoft 365 的 PowerShell 可轻松打印或保存数据</span><span class="sxs-lookup"><span data-stu-id="65e9e-112">PowerShell for Microsoft 365 makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="65e9e-113">用户帐户和许可证报告：</span><span class="sxs-lookup"><span data-stu-id="65e9e-113">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="65e9e-114">使用 PowerShell 查看 Microsoft 365 许可证和服务</span><span class="sxs-lookup"><span data-stu-id="65e9e-114">View Microsoft 365 licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="65e9e-115">使用 PowerShell 查看 Microsoft 365 许可和未经许可的用户</span><span class="sxs-lookup"><span data-stu-id="65e9e-115">View Microsoft 365 licensed and unlicensed users with PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="65e9e-116">使用 PowerShell 查看 Microsoft 365 帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="65e9e-116">View Microsoft 365 account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="65e9e-117">使用 PowerShell 查看 Microsoft 365 用户帐户</span><span class="sxs-lookup"><span data-stu-id="65e9e-117">View Microsoft 365 user accounts with PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="65e9e-118">SharePoint Online 报告：</span><span class="sxs-lookup"><span data-stu-id="65e9e-118">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="65e9e-119">SharePoint Online 命令行管理程序入门</span><span class="sxs-lookup"><span data-stu-id="65e9e-119">Get started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
    
  - [<span data-ttu-id="65e9e-120">使用 PowerShell 管理 SharePoint Online 网站用户组</span><span class="sxs-lookup"><span data-stu-id="65e9e-120">Manage SharePoint Online site groups with PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="65e9e-121">Exchange Online 报告：</span><span class="sxs-lookup"><span data-stu-id="65e9e-121">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="65e9e-122">使用 PowerShell 显示 Exchange Online 邮箱信息</span><span class="sxs-lookup"><span data-stu-id="65e9e-122">Display Exchange Online mailbox information with PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="65e9e-123">使用 PowerShell 显示 Exchange Online 报告</span><span class="sxs-lookup"><span data-stu-id="65e9e-123">Display Exchange Online reports with PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="see-also"></a><span data-ttu-id="65e9e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65e9e-124">See also</span></span>

[<span data-ttu-id="65e9e-125">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="65e9e-125">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="65e9e-126">Microsoft 365 的 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="65e9e-126">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="65e9e-127">使用 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="65e9e-127">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="65e9e-128">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="65e9e-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
