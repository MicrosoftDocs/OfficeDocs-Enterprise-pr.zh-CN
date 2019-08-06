---
title: 使用 Office 365 PowerShell 向用户帐户分配许可证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/05/2019
audience: Admin
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
search.appverid:
- MET150
description: 如何使用 Office 365 PowerShell 将 Office 365 许可证分配给未经许可的用户。
ms.openlocfilehash: c244e60016cb04008e27e2df444703ac7e41db12
ms.sourcegitcommit: 6c3003380491fba6dacb299754716901c20ba629
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2019
ms.locfileid: "36198644"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="7fa92-103">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="7fa92-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="7fa92-104">**摘要:** 如何使用 Office 365 PowerShell 将 Office 365 许可证分配给未经许可的用户。</span><span class="sxs-lookup"><span data-stu-id="7fa92-104">**Summary:**  How to use Office 365 PowerShell to assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="7fa92-105">用户在向其帐户分配许可计划中的许可证之前, 不能使用任何 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="7fa92-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="7fa92-106">您可以使用 Office 365 PowerShell 将许可证快速分配给未经许可的帐户。</span><span class="sxs-lookup"><span data-stu-id="7fa92-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="7fa92-107">必须为用户帐户分配一个位置。</span><span class="sxs-lookup"><span data-stu-id="7fa92-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="7fa92-108">您可以从 Microsoft 365 管理中心或 PowerShell 中的用户帐户的属性中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="7fa92-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="7fa92-109">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="7fa92-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="7fa92-110">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="7fa92-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="7fa92-111">接下来, 使用此命令列出租户的许可证计划。</span><span class="sxs-lookup"><span data-stu-id="7fa92-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="7fa92-112">接下来, 获取要向其添加许可证 (也称为用户主体名称 (UPN)) 的帐户的登录名。</span><span class="sxs-lookup"><span data-stu-id="7fa92-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="7fa92-113">接下来, 请确保已为用户帐户分配了使用位置。</span><span class="sxs-lookup"><span data-stu-id="7fa92-113">Next, ensure that the user account has a usage location assigned.</span></span>

```
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="7fa92-114">如果没有分配的使用位置, 则可以使用以下命令分配一个:</span><span class="sxs-lookup"><span data-stu-id="7fa92-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="7fa92-115">最后, 指定用户登录名和许可证计划名称, 并运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="7fa92-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="7fa92-116">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="7fa92-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="7fa92-117">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="7fa92-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="7fa92-118">运行**get-msolaccountsku**命令可以查看组织中每个计划中可用的许可计划和可用许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="7fa92-118">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="7fa92-119">每个计划中可用的许可证数量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。</span><span class="sxs-lookup"><span data-stu-id="7fa92-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="7fa92-120">有关许可计划、许可证和服务的详细信息, 请参阅[使用 Office 365 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="7fa92-120">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="7fa92-121">若要在组织中查找未授权帐户, 请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="7fa92-121">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="7fa92-122">只能将许可证分配给其**UsageLocation**属性设置为有效的 ISO 3166-1 alpha-2 国家/地区代码的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="7fa92-122">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="7fa92-123">例如，US 代表美国，FR 代表法国。</span><span class="sxs-lookup"><span data-stu-id="7fa92-123">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="7fa92-124">某些 Office 365 服务在某些国家/地区不可用。</span><span class="sxs-lookup"><span data-stu-id="7fa92-124">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="7fa92-125">有关详细信息，请参阅[关于许可证限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="7fa92-125">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="7fa92-126">若要查找不具有**UsageLocation**值的帐户, 请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="7fa92-126">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="7fa92-127">若要设置帐户的**UsageLocation**值, 请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="7fa92-127">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="7fa92-128">例如：</span><span class="sxs-lookup"><span data-stu-id="7fa92-128">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="7fa92-129">如果使用 **Get-MsolUser** cmdlet，而未使用 **-All** 参数，只返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="7fa92-129">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="7fa92-130">向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="7fa92-130">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="7fa92-131">若要将许可证分配给用户, 请使用 Office 365 PowerShell 中的以下命令。</span><span class="sxs-lookup"><span data-stu-id="7fa92-131">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="7fa92-132">本示例将**litwareinc: ENTERPRISEPACK** (Office 365 企业版 E3) 许可计划中的许可证分配给未经许可的用户**belindan@litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="7fa92-132">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="7fa92-133">若要将许可证分配给多个未经许可的用户, 请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="7fa92-133">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="7fa92-134">您无法使用相同的许可计划为用户分配多个许可证。</span><span class="sxs-lookup"><span data-stu-id="7fa92-134">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="7fa92-135">如果没有足够可用的许可证，将按照 **Get-MsolUser** cmdlet 返回的顺序为用户分配许可证，直到可用许可证用尽。</span><span class="sxs-lookup"><span data-stu-id="7fa92-135">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="7fa92-136">此示例将**litwareinc: ENTERPRISEPACK** (Office 365 企业版 E3) 许可计划中的许可证分配给所有未经许可的用户:</span><span class="sxs-lookup"><span data-stu-id="7fa92-136">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="7fa92-137">本示例将这些相同的许可证分配给美国的销售部门中未经许可的用户:</span><span class="sxs-lookup"><span data-stu-id="7fa92-137">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="7fa92-138">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="7fa92-138">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="7fa92-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7fa92-139">See also</span></span>

[<span data-ttu-id="7fa92-140">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="7fa92-140">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="7fa92-141">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="7fa92-141">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="7fa92-142">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="7fa92-142">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
