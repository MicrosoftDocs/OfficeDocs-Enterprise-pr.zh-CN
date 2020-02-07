---
title: 使用 Windows PowerShell 在 Office 365 中创建报告
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/22/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Office_Other
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: 摘要：使用 Office 365 PowerShell 创建无法在 Microsoft 365 管理中心内生成的报表。
ms.openlocfilehash: 3a20c47e462bb522e1fb98ba28fb8c7cee89408c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841239"
---
# <a name="use-windows-powershell-to-create-reports-in-office-365"></a><span data-ttu-id="ab359-103">使用 Windows PowerShell 在 Office 365 中创建报告</span><span class="sxs-lookup"><span data-stu-id="ab359-103">Use Windows PowerShell to create reports in Office 365</span></span>

<span data-ttu-id="ab359-104">Microsoft 365 管理中心中提供很多不同的报告。</span><span class="sxs-lookup"><span data-stu-id="ab359-104">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="ab359-105">但是，这些报告提供的信息有限，有时你可能需要更多信息。</span><span class="sxs-lookup"><span data-stu-id="ab359-105">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="ab359-106">这就是你需要 Office 365 PowerShell 的时候</span><span class="sxs-lookup"><span data-stu-id="ab359-106">That's when you need Office 365 PowerShell</span></span>
  
<span data-ttu-id="ab359-107">这些文章介绍如何使用 Office 365 PowerShell 以从你的 Office 365 租户获取信息：</span><span class="sxs-lookup"><span data-stu-id="ab359-107">These articles that describe how to use Office 365 PowerShell to obtain information from your Office 365 tenant:</span></span>
  
- <span data-ttu-id="ab359-108">开始使用 Office 365 PowerShell 进行报告：</span><span class="sxs-lookup"><span data-stu-id="ab359-108">Getting started with reporting using Office 365 PowerShell:</span></span>
    
  - [<span data-ttu-id="ab359-109">Office 365 PowerShell 可能会显示你通过管理中心无法看到的其他信息</span><span class="sxs-lookup"><span data-stu-id="ab359-109">Office 365 PowerShell can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="ab359-110">Office 365 PowerShell 善于筛选数据</span><span class="sxs-lookup"><span data-stu-id="ab359-110">Office 365 PowerShell is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="ab359-111">Office 365 PowerShell 方便打印或保存数据</span><span class="sxs-lookup"><span data-stu-id="ab359-111">Office 365 PowerShell makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="ab359-112">用户帐户和许可证报告：</span><span class="sxs-lookup"><span data-stu-id="ab359-112">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="ab359-113">使用 Office 365 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="ab359-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="ab359-114">使用 Office 365 PowerShell 查看授权和未授权的用户</span><span class="sxs-lookup"><span data-stu-id="ab359-114">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="ab359-115">使用 Office 365 PowerShell 查看帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="ab359-115">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="ab359-116">查看用户帐户与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab359-116">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="ab359-117">SharePoint Online 报告：</span><span class="sxs-lookup"><span data-stu-id="ab359-117">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="ab359-118">使用 Office 365 PowerShell 管理 SharePoint Online 用户和组</span><span class="sxs-lookup"><span data-stu-id="ab359-118">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/9680af2e-a965-4e62-92ee-da72105c7800.aspx)
    
  - [<span data-ttu-id="ab359-119">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab359-119">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="ab359-120">Exchange Online 报告：</span><span class="sxs-lookup"><span data-stu-id="ab359-120">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="ab359-121">Display Exchange Online mailbox information with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab359-121">Display Exchange Online mailbox information with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="ab359-122">Display Exchange Online reports with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab359-122">Display Exchange Online reports with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="see-also"></a><span data-ttu-id="ab359-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab359-123">See also</span></span>

[<span data-ttu-id="ab359-124">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="ab359-124">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ab359-125">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="ab359-125">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="ab359-126">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ab359-126">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="ab359-127">使用 Office 365 PowerShell 管理用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="ab359-127">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
