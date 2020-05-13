---
title: 使用 Office 365 PowerShell 删除用户帐户的许可证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
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
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: 介绍如何使用 Office 365 PowerShell 删除之前分配给用户的 Office 365 许可证。
ms.openlocfilehash: 4a99fb115b7c3241beb2cb3b0dd83666622747d5
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208753"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="5ef9d-103">使用 Office 365 PowerShell 删除用户帐户的许可证</span><span class="sxs-lookup"><span data-stu-id="5ef9d-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="5ef9d-104">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ef9d-104">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="5ef9d-105">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-105">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="5ef9d-106">接下来，使用此命令列出租户的许可证计划。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-106">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="5ef9d-107">接下来，获取要删除其许可证的帐户的登录名，也称为用户主体名称（UPN）。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-107">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="5ef9d-108">最后，指定用户登录和许可证计划名称，删除 "<" 和 ">" 字符，然后运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-108">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5ef9d-109">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-109">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="5ef9d-110">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="5ef9d-111">要查看组织中的许可计划 (**AccountSkuID**) 信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="5ef9d-111">To view the licensing plan (**AccountSkuID**) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="5ef9d-112">使用 Office 365 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="5ef9d-112">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="5ef9d-113">使用 Office 365 PowerShell 查看帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="5ef9d-113">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="5ef9d-114">如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-114">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="5ef9d-115">从用户帐户中删除许可证</span><span class="sxs-lookup"><span data-stu-id="5ef9d-115">Removing licenses from user accounts</span></span>

<span data-ttu-id="5ef9d-116">要从现有的用户帐户中删除许可证，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="5ef9d-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="5ef9d-117">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="5ef9d-118">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="5ef9d-119">本示例从用户帐户 BelindaN@litwareinc.com 中删除**litwareinc： ENTERPRISEPACK** （Office 365 企业版 E3）许可证。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-119">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="5ef9d-120">无法使用 `Set-MsolUserLicense` cmdlet 从*已取消*的许可证中取消分配用户。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-120">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="5ef9d-121">您必须为 Microsoft 365 管理中心中的每个用户帐户单独执行此操作。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-121">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="5ef9d-122">若要从一组现有许可用户中删除所有许可证，请使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="5ef9d-122">To remove all licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="5ef9d-123">**基于现有帐户属性筛选帐户**为此，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="5ef9d-123">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="5ef9d-124">本示例将从美国的销售部的所有用户帐户中删除所有许可证。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-124">This example removes all licenses from all user accounts in the Sales department in the United States.</span></span>
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- <span data-ttu-id="5ef9d-125">**对特定的许可证使用特定帐户的列表**为此，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="5ef9d-125">**Use a list of specific accounts for a specific license** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="5ef9d-126">创建并保存一个文本文件，其中每一行都有一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5ef9d-126">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="5ef9d-127">使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="5ef9d-127">Use the following syntax:</span></span>
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId>" }
  ```

<span data-ttu-id="5ef9d-128">本示例从文本文件 C:\My 中定义的用户帐户中删除**litwareinc： ENTERPRISEPACK** （Office 365 企业版 E3）许可证 Documents\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-128">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

<span data-ttu-id="5ef9d-129">若要从所有现有用户帐户中删除所有许可证，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="5ef9d-129">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="5ef9d-130">释放许可证的另一种方法是删除用户帐户。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-130">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="5ef9d-131">有关详细信息，请参阅[Delete and restore user accounts With Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="5ef9d-131">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5ef9d-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ef9d-132">See also</span></span>

[<span data-ttu-id="5ef9d-133">使用 Office 365 PowerShell 管理用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="5ef9d-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="5ef9d-134">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="5ef9d-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5ef9d-135">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="5ef9d-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

