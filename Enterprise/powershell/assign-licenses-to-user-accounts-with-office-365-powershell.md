---
title: 使用 PowerShell 将 Microsoft 365 许可证分配给用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: 在本文中，我们将了解如何使用 PowerShell 将 Microsoft 365 许可证分配给未经许可的用户。
ms.openlocfilehash: 824d6b786c3334ae36929e50298e6be0aafd9cb2
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606468"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a><span data-ttu-id="12c2b-103">使用 PowerShell 将 Microsoft 365 许可证分配给用户帐户</span><span class="sxs-lookup"><span data-stu-id="12c2b-103">Assign Microsoft 365 licenses to user accounts with PowerShell</span></span>

<span data-ttu-id="12c2b-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="12c2b-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="12c2b-105">用户在向其帐户分配许可计划中的许可证之前，不能使用任何 Microsoft 365 服务。</span><span class="sxs-lookup"><span data-stu-id="12c2b-105">Users can't use any Microsoft 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="12c2b-106">您可以使用 PowerShell 将许可证快速分配给未经许可的帐户。</span><span class="sxs-lookup"><span data-stu-id="12c2b-106">You can use PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="12c2b-107">必须为用户帐户分配一个位置。</span><span class="sxs-lookup"><span data-stu-id="12c2b-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="12c2b-108">您可以从 Microsoft 365 管理中心或 PowerShell 中的用户帐户的属性中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="12c2b-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="12c2b-109">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="12c2b-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="12c2b-110">首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="12c2b-110">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="12c2b-111">接下来，使用此命令列出租户的许可证计划。</span><span class="sxs-lookup"><span data-stu-id="12c2b-111">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="12c2b-112">接下来，获取要向其添加许可证（也称为 "用户主体名称" (UPN) ）的帐户的登录名。</span><span class="sxs-lookup"><span data-stu-id="12c2b-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="12c2b-113">接下来，请确保已为用户帐户分配了使用位置。</span><span class="sxs-lookup"><span data-stu-id="12c2b-113">Next, ensure that the user account has a usage location assigned.</span></span>

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="12c2b-114">如果没有分配的使用位置，则可以使用以下命令分配一个：</span><span class="sxs-lookup"><span data-stu-id="12c2b-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="12c2b-115">最后，指定用户登录名和许可证计划名称，并运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="12c2b-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="12c2b-116">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="12c2b-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="12c2b-117">首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="12c2b-117">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="12c2b-118">运行 `Get-MsolAccountSku` 命令以查看组织中每个计划中可用的许可计划和可用许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="12c2b-118">Run the `Get-MsolAccountSku` command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="12c2b-119">每个计划中可用的许可证数量是**ActiveUnits**  -  **WarningUnits**  -  **ConsumedUnits**。</span><span class="sxs-lookup"><span data-stu-id="12c2b-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="12c2b-120">有关许可计划、许可证和服务的详细信息，请参阅[使用 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="12c2b-120">For more information about licensing plans, licenses, and services, see [View licenses and services with PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

>[!Note]
><span data-ttu-id="12c2b-121">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="12c2b-121">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="12c2b-122">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="12c2b-122">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="12c2b-123">若要在组织中查找未授权帐户，请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="12c2b-123">To find the unlicensed accounts in your organization, run this command.</span></span>

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="12c2b-124">只能将许可证分配给其**UsageLocation**属性设置为有效的 ISO 3166-1 alpha-2 国家/地区代码的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="12c2b-124">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="12c2b-125">例如，US 代表美国，FR 代表法国。</span><span class="sxs-lookup"><span data-stu-id="12c2b-125">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="12c2b-126">某些 Microsoft 365 服务在某些国家/地区不可用。</span><span class="sxs-lookup"><span data-stu-id="12c2b-126">Some Microsoft 365 services aren't available in certain countries.</span></span> <span data-ttu-id="12c2b-127">有关详细信息，请参阅[关于许可证限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="12c2b-127">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="12c2b-128">若要查找不具有**UsageLocation**值的帐户，请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="12c2b-128">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="12c2b-129">若要设置帐户的**UsageLocation**值，请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="12c2b-129">To set the **UsageLocation** value on an account, run this command.</span></span>

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="12c2b-130">例如：</span><span class="sxs-lookup"><span data-stu-id="12c2b-130">For example:</span></span>

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="12c2b-131">如果使用 **Get-MsolUser** cmdlet，而未使用 **-All** 参数，只返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="12c2b-131">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="12c2b-132">向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="12c2b-132">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="12c2b-133">若要将许可证分配给用户，请在 PowerShell 中使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="12c2b-133">To assign a license to a user, use the following command in PowerShell.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="12c2b-134">本示例将**litwareinc： ENTERPRISEPACK** (Office 365 企业版 E3) 许可计划中的许可证分配给未经许可的**用户 \@ belindan litwareinc.com**：</span><span class="sxs-lookup"><span data-stu-id="12c2b-134">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="12c2b-135">若要将许可证分配给所有未经许可的用户，请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="12c2b-135">To assign a license to all unlicensed users, run this command.</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="12c2b-136">您无法使用相同的许可计划为用户分配多个许可证。</span><span class="sxs-lookup"><span data-stu-id="12c2b-136">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="12c2b-137">如果没有足够可用的许可证，将按照 **Get-MsolUser** cmdlet 返回的顺序为用户分配许可证，直到可用许可证用尽。</span><span class="sxs-lookup"><span data-stu-id="12c2b-137">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="12c2b-138">此示例将**litwareinc： ENTERPRISEPACK** (Office 365 企业版 E3) 许可计划中的许可证分配给所有未经许可的用户：</span><span class="sxs-lookup"><span data-stu-id="12c2b-138">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="12c2b-139">本示例将这些相同的许可证分配给美国的销售部门中未经许可的用户：</span><span class="sxs-lookup"><span data-stu-id="12c2b-139">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="12c2b-140">使用 Azure Active Directory PowerShell for Graph 模块将用户移动到其他订阅 (许可证计划) </span><span class="sxs-lookup"><span data-stu-id="12c2b-140">Move a user to a different subscription (license plan) with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="12c2b-141">首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="12c2b-141">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="12c2b-142">接下来，获取要对其进行切换订阅（也称为用户主体名称 (UPN) ）的用户帐户的登录名。</span><span class="sxs-lookup"><span data-stu-id="12c2b-142">Next, get the sign-in name of the user account for which you want switch subscriptions, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="12c2b-143">接下来，使用此命令列出租户 (许可证计划) 的订阅。</span><span class="sxs-lookup"><span data-stu-id="12c2b-143">Next, list the subscriptions (license plans) for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="12c2b-144">接下来，使用这些命令列出用户帐户当前拥有的订阅。</span><span class="sxs-lookup"><span data-stu-id="12c2b-144">Next, list the subscriptions that the user account currently has with these commands.</span></span>

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

<span data-ttu-id="12c2b-145">确定用户当前已 (FROM 订阅) 的订阅，以及用户将移动到的订阅 (到订阅) 。</span><span class="sxs-lookup"><span data-stu-id="12c2b-145">Identify the subscription the user currently has (the FROM subscription) and the subscription to which the user is moving (the TO subscription).</span></span>

<span data-ttu-id="12c2b-146">最后，指定 TO 和 FROM 订阅名称 (SKU 部件号) 并运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="12c2b-146">Finally, specify the TO and FROM subscription names (SKU part numbers) and run these commands.</span></span>

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

<span data-ttu-id="12c2b-147">您可以使用这些命令验证用户帐户的订阅更改。</span><span class="sxs-lookup"><span data-stu-id="12c2b-147">You can verify the change in subscription for the user account with these commands.</span></span>

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a><span data-ttu-id="12c2b-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12c2b-148">See also</span></span>

[<span data-ttu-id="12c2b-149">使用 PowerShell 管理用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="12c2b-149">Manage user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="12c2b-150">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="12c2b-150">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="12c2b-151">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="12c2b-151">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
