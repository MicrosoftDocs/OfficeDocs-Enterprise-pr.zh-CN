---
title: 使用 Office 365 PowerShell 冻结用户账户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: 介绍如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 帐户的访问。
ms.openlocfilehash: 3cc063fac2fa7795ba924b7b937efc9afe6594a1
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "38706979"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="75a12-103">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="75a12-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="75a12-104">**摘要：** 介绍如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 帐户的访问。</span><span class="sxs-lookup"><span data-stu-id="75a12-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="75a12-105">阻止访问 Office 365 帐户将阻止任何人使用该帐户登录并访问 Office 365 组织中的服务和数据。</span><span class="sxs-lookup"><span data-stu-id="75a12-105">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="75a12-106">您可以使用 Office 365 PowerShell 阻止对单个和多个用户帐户的访问。</span><span class="sxs-lookup"><span data-stu-id="75a12-106">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="75a12-107">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="75a12-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="75a12-108">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="75a12-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="75a12-109">阻止对单个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="75a12-109">Block access to individual user accounts</span></span>

<span data-ttu-id="75a12-110">使用以下语法来阻止单个用户帐户：</span><span class="sxs-lookup"><span data-stu-id="75a12-110">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="75a12-111">AzureAD cmdlet 中的-ObjectID 参数可接受帐户登录名（也称为 "用户主体名称"）或帐户的对象 ID。</span><span class="sxs-lookup"><span data-stu-id="75a12-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="75a12-112">此示例阻止访问用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="75a12-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="75a12-113">若要取消阻止此用户帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="75a12-113">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="75a12-114">若要根据用户的显示名称显示用户帐户 UPN，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="75a12-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="75a12-115">本示例显示名为 Caleb Sills 的用户的用户帐户 UPN。</span><span class="sxs-lookup"><span data-stu-id="75a12-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="75a12-116">若要基于用户的显示名称阻止某个帐户，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="75a12-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="75a12-117">在任何时候，都可以使用以下命令检查用户帐户的阻止状态：</span><span class="sxs-lookup"><span data-stu-id="75a12-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="75a12-118">阻止对多个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="75a12-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="75a12-119">若要阻止对多个用户帐户的访问，请创建一个文本文件，其中每行包含一个帐户登录名，如下所示：</span><span class="sxs-lookup"><span data-stu-id="75a12-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="75a12-120">在以下命令中，示例文本文件为 C:\My Documents\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="75a12-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="75a12-121">将此替换为您的文本文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="75a12-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="75a12-122">若要阻止访问该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="75a12-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="75a12-123">若要解除阻止该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="75a12-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="75a12-124">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="75a12-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="75a12-125">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="75a12-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="75a12-126">阻止对单个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="75a12-126">Block access to individual user accounts</span></span>

<span data-ttu-id="75a12-127">使用以下语法来阻止对单个用户帐户的访问：</span><span class="sxs-lookup"><span data-stu-id="75a12-127">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="75a12-128">此示例阻止访问用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="75a12-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="75a12-129">若要取消阻止该用户帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="75a12-129">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="75a12-130">在任何时候，都可以使用以下命令检查用户帐户的阻止状态：</span><span class="sxs-lookup"><span data-stu-id="75a12-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="75a12-131">阻止对多个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="75a12-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="75a12-132">首先，创建一个文本文件，其中每行包含一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="75a12-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="75a12-133">在以下命令中，示例文本文件为 C:\My Documents\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="75a12-133">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="75a12-134">将此替换为您的文本文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="75a12-134">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="75a12-135">若要阻止访问该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="75a12-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="75a12-136">若要解除阻止该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="75a12-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="75a12-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75a12-137">See also</span></span>

[<span data-ttu-id="75a12-138">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="75a12-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="75a12-139">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="75a12-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="75a12-140">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="75a12-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
