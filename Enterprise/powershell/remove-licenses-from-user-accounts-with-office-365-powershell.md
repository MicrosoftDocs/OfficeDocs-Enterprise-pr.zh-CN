---
title: 使用 Office 365 PowerShell 删除用户帐户的许可证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/23/2019
audience: Admin
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
description: 介绍如何使用 Office 365 PowerShell 删除之前分配给用户的 Office 365 许可证。
ms.openlocfilehash: bfd333b649df1d346a45abc3e8b9e35666f8f582
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747538"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="62c89-103">使用 Office 365 PowerShell 删除用户帐户的许可证</span><span class="sxs-lookup"><span data-stu-id="62c89-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="62c89-104">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="62c89-104">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="62c89-105">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="62c89-105">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="62c89-106">接下来，使用此命令列出租户的许可证计划。</span><span class="sxs-lookup"><span data-stu-id="62c89-106">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="62c89-107">接下来，获取要删除其许可证的帐户的登录名，也称为用户主体名称（UPN）。</span><span class="sxs-lookup"><span data-stu-id="62c89-107">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="62c89-108">最后，指定用户登录和许可证计划名称，删除 "<" 和 ">" 字符，然后运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="62c89-108">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="62c89-109">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="62c89-109">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="62c89-110">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="62c89-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

   
<span data-ttu-id="62c89-111">若要查看组织中的许可计划（**AccountSkuID** ）信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="62c89-111">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="62c89-112">使用 Office 365 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="62c89-112">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="62c89-113">使用 Office 365 PowerShell 查看帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="62c89-113">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="62c89-114">如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="62c89-114">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="62c89-115">从用户帐户中删除许可证</span><span class="sxs-lookup"><span data-stu-id="62c89-115">Removing licenses from user accounts</span></span>

<span data-ttu-id="62c89-116">要从现有的用户帐户中删除许可证，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="62c89-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="62c89-117">本示例从用户`litwareinc:ENTERPRISEPACK`帐户 BelindaN@litwareinc.com 中删除（Office 365 企业版 E3）许可证。</span><span class="sxs-lookup"><span data-stu-id="62c89-117">This example removes the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="62c89-118">您不能使用 Set-msoluserlicense cmdlet 从*已取消*的许可证中取消分配用户。</span><span class="sxs-lookup"><span data-stu-id="62c89-118">You cannot use the Set-MsolUserLicense cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="62c89-119">您必须为 Microsoft 365 管理中心中的每个用户帐户单独执行此操作。</span><span class="sxs-lookup"><span data-stu-id="62c89-119">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="62c89-120">要从一组现有的授权用户中删除许可证，请使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="62c89-120">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="62c89-121">**基于现有帐户属性筛选帐户**为此，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="62c89-121">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="62c89-122">本示例将从`litwareinc:ENTERPRISEPACK`美国的销售部门的用户的所有帐户中删除（Office 365 企业版 E3）许可证。</span><span class="sxs-lookup"><span data-stu-id="62c89-122">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="62c89-123">**使用特定帐户的列表**为此，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="62c89-123">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="62c89-124">创建并保存一个文本文件，其中每一行都有一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="62c89-124">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="62c89-125">使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="62c89-125">Use the following syntax:</span></span>
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

<span data-ttu-id="62c89-126">本示例从文本文件`litwareinc:ENTERPRISEPACK` C:\My Documents\Accounts.txt. 中定义的用户帐户中删除（Office 365 企业版 E3）许可证。</span><span class="sxs-lookup"><span data-stu-id="62c89-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

<span data-ttu-id="62c89-127">要从所有现有的用户帐户中删除许可证，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="62c89-127">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="62c89-128">本示例从所有`litwareinc:ENTERPRISEPACK`现有的授权用户帐户中删除（Office 365 企业版 E3）许可证。</span><span class="sxs-lookup"><span data-stu-id="62c89-128">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="62c89-129">释放许可证的另一种方法是删除用户帐户。</span><span class="sxs-lookup"><span data-stu-id="62c89-129">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="62c89-130">有关详细信息，请参阅[Delete and restore user accounts With Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="62c89-130">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="62c89-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62c89-131">See also</span></span>

[<span data-ttu-id="62c89-132">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="62c89-132">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="62c89-133">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="62c89-133">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="62c89-134">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="62c89-134">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a><span data-ttu-id="62c89-135">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="62c89-135">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

