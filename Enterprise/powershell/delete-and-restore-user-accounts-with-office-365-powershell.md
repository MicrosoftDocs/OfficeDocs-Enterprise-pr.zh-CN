---
title: 使用 Office 365 PowerShell 删除用户帐户
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: 了解如何使用 Office 365 PowerShell 删除 Office 365 用户帐户。
ms.openlocfilehash: b7c30ec422475a4cf11b28249e8a20d64a3c90a4
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746425"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="835bf-103">使用 Office 365 PowerShell 删除用户帐户</span><span class="sxs-lookup"><span data-stu-id="835bf-103">Delete user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="835bf-104">可使用 Office 365 PowerShell 删除用户帐户。</span><span class="sxs-lookup"><span data-stu-id="835bf-104">You can use Office 365 PowerShell to delete a user account.</span></span>
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="835bf-105">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="835bf-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="835bf-106">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="835bf-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="835bf-107">连接后，使用下列语法删除单个用户帐户：</span><span class="sxs-lookup"><span data-stu-id="835bf-107">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="835bf-108">本示例将删除用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="835bf-108">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="835bf-109">**Remove-AzureAD** cmdlet 中的 **-ObjectID** 参数可接受帐户登录名（也称为“用户主体名称”）或帐户的对象 ID。</span><span class="sxs-lookup"><span data-stu-id="835bf-109">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="835bf-110">若要显示基于用户名的帐户名，请使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="835bf-110">To display the account name based on the user's name, use the following commands:</span></span>
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="835bf-111">本示例显示名为 Caleb Sills 的用户的帐户名。</span><span class="sxs-lookup"><span data-stu-id="835bf-111">This example displays the account name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="835bf-112">若要删除基于用户显示名称的帐户，请使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="835bf-112">To remove an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="835bf-113">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="835bf-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="835bf-p101">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块删除用户帐户时，该帐户不会被永久删除。可以在 30 天内还原已删除的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="835bf-p101">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="835bf-116">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="835bf-116">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="835bf-117">若要删除一个用户帐户，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="835bf-117">To delete a user account, use the following syntax:</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="835bf-118">本示例删除用户帐户 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="835bf-118">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="835bf-119">若要在 30 天的宽限期内还原已删除的用户帐户，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="835bf-119">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="835bf-120">本示例还原已删除的帐户 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="835bf-120">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="835bf-121">**注意：**</span><span class="sxs-lookup"><span data-stu-id="835bf-121">**Notes:**</span></span>
  
- <span data-ttu-id="835bf-122">若要查看可以还原的已删除用户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="835bf-122">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="835bf-123">如果用户帐户的初始用户主体名称已被另一个帐户使用，那么在还原用户帐户时，请使用 _NewUserPrincipalName_ 参数而不是 _UserPrincipalName_ 来指定一个不同的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="835bf-123">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="835bf-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="835bf-124">See also</span></span>

[<span data-ttu-id="835bf-125">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="835bf-125">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="835bf-126">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="835bf-126">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="835bf-127">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="835bf-127">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

