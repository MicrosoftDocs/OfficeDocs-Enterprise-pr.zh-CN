---
title: 使用 Office 365 PowerShell 冻结用户账户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: 介绍如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 帐户的访问。
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546473"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d43ad-103">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="d43ad-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d43ad-104">**摘要：** 介绍如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 帐户的访问。</span><span class="sxs-lookup"><span data-stu-id="d43ad-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="d43ad-p101">阻止对 Office 365 帐户访问可防止任何人使用的帐户登录和访问的服务和 Office 365 组织中的数据。Office 365 PowerShell 中可用于阻止对单个访问和多个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d43ad-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d43ad-107">使用 Azure Active Directory PowerShell 图模块</span><span class="sxs-lookup"><span data-stu-id="d43ad-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d43ad-108">第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="d43ad-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="d43ad-109">阻止对单个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="d43ad-109">Block access to individual user accounts</span></span>

<span data-ttu-id="d43ad-110">使用以下语法阻止单个用户帐户：</span><span class="sxs-lookup"><span data-stu-id="d43ad-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="d43ad-111">设置 AzureAD cmdlet 中的 ObjectID 参数接受任一的帐户登录名称，也称为用户主体名称或该帐户的对象 id。</span><span class="sxs-lookup"><span data-stu-id="d43ad-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="d43ad-112">此示例阻止访问用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="d43ad-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="d43ad-113">若要取消阻止此用户帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d43ad-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="d43ad-114">若要显示 UPN 基于用户的显示名称的用户帐户，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="d43ad-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="d43ad-115">本示例显示名为 Caleb Sills 的用户的用户帐户 UPN。</span><span class="sxs-lookup"><span data-stu-id="d43ad-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d43ad-116">若要阻止基于用户的显示名称的帐户，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="d43ad-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="d43ad-117">在任何时候，您可以检查阻止的状态的用户帐户，使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="d43ad-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="d43ad-118">阻止对多个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="d43ad-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="d43ad-119">若要阻止对多个用户帐户的访问，请创建包含一个帐户登录名称类似的每一行上一个文本文件：</span><span class="sxs-lookup"><span data-stu-id="d43ad-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="d43ad-p102">以下命令，在示例文本文件是 C:\My Documents\Accounts.txt。将此替换为文本文件的路径和文件名称。</span><span class="sxs-lookup"><span data-stu-id="d43ad-p102">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="d43ad-122">若要阻止访问该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d43ad-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="d43ad-123">若要解除阻止该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d43ad-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d43ad-124">使用 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="d43ad-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d43ad-125">第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="d43ad-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="d43ad-126">阻止对单个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="d43ad-126">Block access to individual user accounts</span></span>

<span data-ttu-id="d43ad-127">使用以下语法来阻止对单个用户帐户的访问：</span><span class="sxs-lookup"><span data-stu-id="d43ad-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="d43ad-128">此示例阻止访问用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="d43ad-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="d43ad-129">若要取消阻止该用户帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d43ad-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="d43ad-130">在任何时候，您可以检查阻止的状态的用户帐户，使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="d43ad-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="d43ad-131">阻止对多个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="d43ad-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="d43ad-132">首先，创建一个文本文件，包含如下所示的每一行上的一个帐户：</span><span class="sxs-lookup"><span data-stu-id="d43ad-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="d43ad-p103">以下命令，在示例文本文件是 C:\My Documents\Accounts.txt。将此替换为文本文件的路径和文件名称。</span><span class="sxs-lookup"><span data-stu-id="d43ad-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="d43ad-135">若要阻止访问该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d43ad-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="d43ad-136">若要解除阻止该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d43ad-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="d43ad-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d43ad-137">See also</span></span>

[<span data-ttu-id="d43ad-138">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="d43ad-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d43ad-139">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="d43ad-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d43ad-140">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="d43ad-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
