---
title: 使用 Office 365 PowerShell 查看授权和未授权的用户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: 介绍如何使用 Office 365 PowerShell 查看授权和未授权的用户帐户。
ms.openlocfilehash: 9bef0994d516de9c06da64969f090135aad4fa46
ms.sourcegitcommit: 16a060c0732c6234bb2ebc037786a7c4872fe686
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "38308577"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="bc245-103">使用 Office 365 PowerShell 查看授权和未授权的用户</span><span class="sxs-lookup"><span data-stu-id="bc245-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="bc245-104">**摘要：** 介绍如何使用 Office 365 PowerShell 查看许可和非许可用户帐户。</span><span class="sxs-lookup"><span data-stu-id="bc245-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="bc245-p101">您的 Office 365 组织中的用户帐户可能已从组织提供的许可计划中分配到部分或全部可用的许可证，或者未分配到任何许可证。您可以使用 Office 365 PowerShell 快速查找您组织中的授权和未授权的用户。</span><span class="sxs-lookup"><span data-stu-id="bc245-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="bc245-107">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc245-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="bc245-108">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="bc245-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="bc245-109">若要查看您的组织中尚未分配任何许可计划（未经许可的用户）的所有用户帐户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="bc245-109">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="bc245-110">若要查看组织中已向其分配任何许可计划（许可用户）的所有用户帐户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="bc245-110">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```
>[!Note]
><span data-ttu-id="bc245-111">若要列出订阅中的所有用户，请使用`Get-AzureAdUser -All $true`命令。</span><span class="sxs-lookup"><span data-stu-id="bc245-111">To list all of the users in your subscription, use the `Get-AzureAdUser -All $true` command.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="bc245-112">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="bc245-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="bc245-113">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="bc245-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="bc245-114">若要查看组织中所有用户帐户及其授权状态的列表，请在 Office 365 PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="bc245-114">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```powershell
Get-MsolUser -All
```

<span data-ttu-id="bc245-115">若要查看组织中所有未授权用户帐户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="bc245-115">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="bc245-116">若要查看组织中所有授权用户帐户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="bc245-116">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="bc245-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc245-117">See also</span></span>

[<span data-ttu-id="bc245-118">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="bc245-118">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="bc245-119">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="bc245-119">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="bc245-120">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="bc245-120">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
