---
title: 使用 Office 365 PowerShell 删除用户帐户的许可证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: 介绍如何使用 Office 365 PowerShell 中删除之前已分配给用户的 Office 365 许可证。
ms.openlocfilehash: a993737f4bd1186a7fb5beb7fa0f6a2ae6782618
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123299"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="18828-103">使用 Office 365 PowerShell 删除用户帐户的许可证</span><span class="sxs-lookup"><span data-stu-id="18828-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="18828-104">**摘要：** 介绍如何使用 Office 365 PowerShell 中删除之前已分配给用户的 Office 365 许可证。</span><span class="sxs-lookup"><span data-stu-id="18828-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="18828-105">准备工作</span><span class="sxs-lookup"><span data-stu-id="18828-105">Before you begin</span></span>

- <span data-ttu-id="18828-p101">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="18828-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="18828-108">若要查看组织中的许可计划 (**AccountSkuID** ) 信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="18828-108">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="18828-109">使用 Office 365 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="18828-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="18828-110">使用 Office 365 PowerShell 查看帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="18828-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="18828-111">如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="18828-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="18828-112">从用户帐户删除许可证</span><span class="sxs-lookup"><span data-stu-id="18828-112">Removing licenses from user accounts</span></span>

<span data-ttu-id="18828-113">要从现有的用户帐户中删除许可证，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="18828-113">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="18828-114">此示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3) 许可证的用户帐户 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="18828-114">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="18828-115">要从一组现有的授权用户中删除许可证，请使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="18828-115">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="18828-116">**筛选器基于现有帐户属性的帐户**若要执行此操作，使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="18828-116">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="18828-117">此示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3) 许可证从众所周知在美国销售部门中的用户。</span><span class="sxs-lookup"><span data-stu-id="18828-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="18828-118">**使用特定帐户的列表**若要执行此操作，执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="18828-118">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="18828-119">创建并保存一个文本文件，其中每一行都有一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="18828-119">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="18828-120">使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="18828-120">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="18828-121">此示例删除`litwareinc:ENTERPRISEPACK`从文本文件 C:\My Documents\Accounts.txt 中定义的用户帐户 (Office 365 企业版 E3) 许可证。</span><span class="sxs-lookup"><span data-stu-id="18828-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="18828-122">要从所有现有的用户帐户中删除许可证，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="18828-122">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="18828-123">此示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3) 从所有现有的许可证许可用户帐户。</span><span class="sxs-lookup"><span data-stu-id="18828-123">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="18828-p102">通过删除的用户帐户是另一种方式以释放许可证。有关详细信息，请参阅[删除并还原与 Office 365 PowerShell 中的用户帐户](delete-and-restore-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="18828-p102">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="18828-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18828-126">See also</span></span>

<span data-ttu-id="18828-127">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="18828-127">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="18828-128">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="18828-128">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="18828-129">使用 Office 365 PowerShell 删除和还原用户账户</span><span class="sxs-lookup"><span data-stu-id="18828-129">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="18828-130">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="18828-130">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="18828-131">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="18828-131">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="18828-132">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="18828-132">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="18828-133">获取内容</span><span class="sxs-lookup"><span data-stu-id="18828-133">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="18828-134">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="18828-134">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="18828-135">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="18828-135">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="18828-136">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="18828-136">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="18828-137">Where-Object</span><span class="sxs-lookup"><span data-stu-id="18828-137">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="18828-138">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="18828-138">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

