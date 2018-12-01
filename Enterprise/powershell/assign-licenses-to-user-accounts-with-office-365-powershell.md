---
title: 使用 Office 365 PowerShell 向用户帐户分配许可证
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: 介绍如何使用 Office 365 PowerShell 中分配给未许可用户的 Office 365 许可证。
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123289"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="209d5-103">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="209d5-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="209d5-104">**摘要：** 介绍如何使用 Office 365 PowerShell 中分配给未许可用户的 Office 365 许可证。</span><span class="sxs-lookup"><span data-stu-id="209d5-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="209d5-p101">许可 Office 365 中的用户帐户很重要，因为用户不能使用任何 Office 365 服务，直到其帐户已授权。您可以使用 Office 365 PowerShell 中高效地将许可证分配给未经授权的帐户，尤其是多个帐户。</span><span class="sxs-lookup"><span data-stu-id="209d5-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="209d5-107">准备工作</span><span class="sxs-lookup"><span data-stu-id="209d5-107">Before you begin</span></span>
<span data-ttu-id="209d5-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="209d5-108"></span></span>

- <span data-ttu-id="209d5-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="209d5-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="209d5-p103">使用**Get-msolaccountsku** cmdlet 以查看您的组织中的每个计划中可用的许可计划和可用许可证的数目。每个计划中可用的许可证数是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。有关许可计划、 许可证和服务的详细信息，请参阅[查看许可证和身份验证服务与 Office 365 PowerShell 中](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="209d5-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="209d5-114">若要在组织中查找的未经授权的帐户，请运行命令`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="209d5-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="209d5-p104">您可以仅对具有**UsageLocation**属性设置为有效的 ISO 3166-1 alpha 2 国家/地区代码的用户帐户分配许可证。例如，美国的电话和法国 FR 我们。在某些国家/地区，某些 Office 365 服务不可用。有关详细信息，请参阅[关于许可限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="209d5-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="209d5-p105">若要查找不具有**UsageLocation**值的帐户，请运行命令`Get-MsolUser -All | where {$_.UsageLocation -eq $null}`。若要设置帐户**UsageLocation**值，请使用语法`Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`。例如， `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。</span><span class="sxs-lookup"><span data-stu-id="209d5-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="209d5-122">如果您使用**Get-msoluser** cmdlet 而不使用`-All`参数返回仅前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="209d5-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>

## <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="209d5-123">向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="209d5-123">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="209d5-124">若要向用户分配许可证，请在 Office 365 PowerShell 中使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="209d5-124">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="209d5-125">本示例将从许可证分配`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3) 到未经授权的用户的许可计划`belindan@litwareinc.com`。</span><span class="sxs-lookup"><span data-stu-id="209d5-125">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="209d5-126">若要向多个未授权用户分配许可证，请使用以下句法：</span><span class="sxs-lookup"><span data-stu-id="209d5-126">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="209d5-127">**注释**</span><span class="sxs-lookup"><span data-stu-id="209d5-127">**Notes**</span></span>
  
- <span data-ttu-id="209d5-128">您无法使用相同的许可计划为用户分配多个许可证。</span><span class="sxs-lookup"><span data-stu-id="209d5-128">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="209d5-129">如果没有足够可用的许可证，将按照 **Get-MsolUser** cmdlet 返回的顺序为用户分配许可证，直到可用许可证用尽。</span><span class="sxs-lookup"><span data-stu-id="209d5-129">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="209d5-130">本示例将从许可证分配`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3) 到所有未经授权的用户的许可计划。</span><span class="sxs-lookup"><span data-stu-id="209d5-130">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="209d5-131">本示例向美国销售部门的未授权用户分配这些相同的许可证。</span><span class="sxs-lookup"><span data-stu-id="209d5-131">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="209d5-132">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="209d5-132">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="209d5-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="209d5-133">See also</span></span>
<span data-ttu-id="209d5-134"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="209d5-134"></span></span>

<span data-ttu-id="209d5-135">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="209d5-135">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="209d5-136">创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="209d5-136">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="209d5-137">删除并还原用户帐户</span><span class="sxs-lookup"><span data-stu-id="209d5-137">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="209d5-138">阻止用户帐户</span><span class="sxs-lookup"><span data-stu-id="209d5-138">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="209d5-139">从用户帐户删除许可证</span><span class="sxs-lookup"><span data-stu-id="209d5-139">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="209d5-140">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="209d5-140">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="209d5-141">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="209d5-141">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="209d5-142">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="209d5-142">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="209d5-143">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="209d5-143">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="209d5-144">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="209d5-144">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="209d5-145">选择对象</span><span class="sxs-lookup"><span data-stu-id="209d5-145">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="209d5-146">Where-Object</span><span class="sxs-lookup"><span data-stu-id="209d5-146">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

