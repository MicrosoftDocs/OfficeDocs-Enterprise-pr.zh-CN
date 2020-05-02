---
title: 使用 Office 365 PowerShell 冻结用户账户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
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
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: 介绍如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 帐户的访问。
ms.openlocfilehash: 5633c35feee67ede65c4fffa8bc55276c3b979b8
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004725"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="0262e-103">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="0262e-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="0262e-104">阻止访问 Office 365 帐户将阻止任何人使用该帐户登录并访问 Office 365 组织中的服务和数据。</span><span class="sxs-lookup"><span data-stu-id="0262e-104">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="0262e-105">您可以使用 Office 365 PowerShell 阻止对单个和多个用户帐户的访问。</span><span class="sxs-lookup"><span data-stu-id="0262e-105">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="0262e-106">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="0262e-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="0262e-107">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="0262e-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="0262e-108">阻止对单个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="0262e-108">Block access to individual user accounts</span></span>

<span data-ttu-id="0262e-109">使用以下语法来阻止单个用户帐户：</span><span class="sxs-lookup"><span data-stu-id="0262e-109">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="0262e-110">AzureAD cmdlet 中的-ObjectID 参数可接受帐户登录名（也称为 "用户主体名称"）或帐户的对象 ID。</span><span class="sxs-lookup"><span data-stu-id="0262e-110">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="0262e-111">此示例阻止访问用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="0262e-111">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="0262e-112">若要取消阻止此用户帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0262e-112">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="0262e-113">若要根据用户的显示名称显示用户帐户 UPN，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="0262e-113">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="0262e-114">本示例显示名为 Caleb Sills 的用户的用户帐户 UPN。</span><span class="sxs-lookup"><span data-stu-id="0262e-114">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="0262e-115">若要基于用户的显示名称阻止某个帐户，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="0262e-115">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="0262e-116">在任何时候，都可以使用以下命令检查用户帐户的阻止状态：</span><span class="sxs-lookup"><span data-stu-id="0262e-116">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="0262e-117">阻止对多个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="0262e-117">Block access to multiple user accounts</span></span>

<span data-ttu-id="0262e-118">若要阻止对多个用户帐户的访问，请创建一个文本文件，其中每行包含一个帐户登录名，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0262e-118">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="0262e-119">在以下命令中，示例文本文件为 C:\My Documents\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="0262e-119">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="0262e-120">将此替换为您的文本文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="0262e-120">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="0262e-121">若要阻止访问该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0262e-121">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="0262e-122">若要解除阻止该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0262e-122">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="0262e-123">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="0262e-123">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="0262e-124">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="0262e-124">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="0262e-125">阻止对单个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="0262e-125">Block access to individual user accounts</span></span>

<span data-ttu-id="0262e-126">使用以下语法来阻止对单个用户帐户的访问：</span><span class="sxs-lookup"><span data-stu-id="0262e-126">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="0262e-127">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="0262e-127">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="0262e-128">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="0262e-128">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="0262e-129">此示例阻止访问用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="0262e-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="0262e-130">若要取消阻止该用户帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0262e-130">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="0262e-131">在任何时候，都可以使用以下命令检查用户帐户的阻止状态：</span><span class="sxs-lookup"><span data-stu-id="0262e-131">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="0262e-132">阻止对多个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="0262e-132">Block access to multiple user accounts</span></span>

<span data-ttu-id="0262e-133">首先，创建一个文本文件，其中每行包含一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0262e-133">First, create a text file that contains one account on each line like this:</span></span>
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

<span data-ttu-id="0262e-134">在以下命令中，示例文本文件为 C:\My Documents\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="0262e-134">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="0262e-135">将此替换为您的文本文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="0262e-135">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="0262e-136">若要阻止访问该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0262e-136">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="0262e-137">若要解除阻止该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0262e-137">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="0262e-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0262e-138">See also</span></span>

[<span data-ttu-id="0262e-139">使用 Office 365 PowerShell 管理用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="0262e-139">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="0262e-140">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="0262e-140">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="0262e-141">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="0262e-141">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
