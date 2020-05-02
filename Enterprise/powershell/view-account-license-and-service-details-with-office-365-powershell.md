---
title: 使用 Office 365 PowerShell 查看帐户许可证和服务详细信息
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: 说明如何使用 Office 365 PowerShell 确定已分配给用户的 Office 365 服务。
ms.openlocfilehash: 603470be87aea2d58f343511026fb2860e58b688
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004485"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="1f236-103">使用 Office 365 PowerShell 查看帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="1f236-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="1f236-104">在 Office 365 中，许可计划（也称为 Sku 或 Office 365 计划）的许可证为用户提供了对为这些计划定义的 Office 365 服务的访问权限。</span><span class="sxs-lookup"><span data-stu-id="1f236-104">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans.</span></span> <span data-ttu-id="1f236-105">但是，用户可能无法访问当前分配给他们的许可证中可用的所有服务。</span><span class="sxs-lookup"><span data-stu-id="1f236-105">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="1f236-106">您可以使用 Office 365 PowerShell 来查看用户帐户上的服务的状态。</span><span class="sxs-lookup"><span data-stu-id="1f236-106">You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="1f236-107">有关许可计划、许可证和服务的详细信息，请参阅[使用 Office 365 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1f236-107">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1f236-108">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f236-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1f236-109">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="1f236-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="1f236-110">接下来，使用此命令列出租户的许可证计划。</span><span class="sxs-lookup"><span data-stu-id="1f236-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="1f236-111">使用这些命令列出每个许可计划中可用的服务。</span><span class="sxs-lookup"><span data-stu-id="1f236-111">Use these commands to list the services that are available in each licensing plan.</span></span>

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

<span data-ttu-id="1f236-112">使用这些命令列出分配给用户帐户的许可证。</span><span class="sxs-lookup"><span data-stu-id="1f236-112">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1f236-113">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="1f236-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1f236-114">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="1f236-114">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="1f236-115">接下来，运行此命令，列出您的组织中可用的许可计划。</span><span class="sxs-lookup"><span data-stu-id="1f236-115">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```
>[!Note]
><span data-ttu-id="1f236-116">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="1f236-116">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="1f236-117">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="1f236-117">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="1f236-118">接下来，运行此命令，列出每个许可计划中可用的服务，以及这些服务的列出顺序（索引号）。</span><span class="sxs-lookup"><span data-stu-id="1f236-118">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
<span data-ttu-id="1f236-119">使用此命令可列出分配给用户的许可证以及它们的列出顺序（索引号）。</span><span class="sxs-lookup"><span data-stu-id="1f236-119">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="1f236-120">查看用户帐户的服务</span><span class="sxs-lookup"><span data-stu-id="1f236-120">To view services for a user account</span></span>

<span data-ttu-id="1f236-121">若要查看用户有权访问的所有 Office 365 服务，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="1f236-121">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="1f236-122">本示例显示用户 BelindaN@litwareinc.com 有权访问的服务。</span><span class="sxs-lookup"><span data-stu-id="1f236-122">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="1f236-123">这将显示与分配给她的帐户相关联的所有许可证相关联的服务。</span><span class="sxs-lookup"><span data-stu-id="1f236-123">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="1f236-124">本示例显示了用户 BelindaN@litwareinc.com 可以从分配给她的帐户（索引号为0）的第一个许可证访问的服务。</span><span class="sxs-lookup"><span data-stu-id="1f236-124">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="1f236-125">若要查看已分配*多个许可证*的用户的所有服务，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="1f236-125">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a><span data-ttu-id="1f236-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f236-126">See also</span></span>

[<span data-ttu-id="1f236-127">使用 Office 365 PowerShell 管理用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="1f236-127">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1f236-128">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="1f236-128">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1f236-129">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="1f236-129">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
