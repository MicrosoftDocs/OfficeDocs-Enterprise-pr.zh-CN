---
title: "使用 Office 365 PowerShell 删除和还原用户账户"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "了解如何使用 Office 365 PowerShell 删除和还原 Office 365 用户帐户。"
ms.openlocfilehash: fc72d51532780d2ddaaff20ecc6aebab06a001f4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a><span data-ttu-id="23fb3-103">使用 Office 365 PowerShell 删除和还原用户账户</span><span class="sxs-lookup"><span data-stu-id="23fb3-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="23fb3-104">**摘要：**了解如何使用 Office 365 PowerShell 删除和还原 Office 365 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="23fb3-104">**Summary:**  Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts.</span></span>
  
<span data-ttu-id="23fb3-p101">当您使用 Office 365 PowerShell 删除用户帐户时，该帐户不会被永久删除。您可以在 30 天内还原已删除的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="23fb3-p101">When you use Office 365 PowerShell to delete a user account, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="23fb3-107">准备工作</span><span class="sxs-lookup"><span data-stu-id="23fb3-107">Before you begin</span></span>

- <span data-ttu-id="23fb3-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="23fb3-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="23fb3-110">如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="23fb3-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="23fb3-111">使用 Office 365 PowerShell 阻止对单个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="23fb3-111">Use Office 365 PowerShell to block access to individual user accounts</span></span>
<span data-ttu-id="23fb3-112"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="23fb3-112"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="23fb3-113">若要删除一个用户帐户，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="23fb3-113">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="23fb3-114">本示例删除用户帐户 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="23fb3-114">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="23fb3-115">若要在 30 天的宽限期内还原已删除的用户帐户，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="23fb3-115">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="23fb3-116">本示例还原已删除的帐户 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="23fb3-116">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="23fb3-117">**注意：**</span><span class="sxs-lookup"><span data-stu-id="23fb3-117">**Notes:**</span></span>
  
- <span data-ttu-id="23fb3-118">若要查看可以还原的已删除用户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="23fb3-118">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="23fb3-119">如果用户帐户的初始用户主体名称已被另一个帐户使用，那么在还原用户帐户时，请使用  _NewUserPrincipalName_ 参数而不是 _UserPrincipalName_ 来指定一个不同的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="23fb3-119">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a><span data-ttu-id="23fb3-120">使用 Azure Active Directory V2 PowerShell 模块删除用户帐户</span><span class="sxs-lookup"><span data-stu-id="23fb3-120">Use the Azure Active Directory V2 PowerShell module to remove a user account</span></span>
<span data-ttu-id="23fb3-121"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="23fb3-121"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="23fb3-p103">若要使用 Azure Active Directory V2 PowerShell 模块中的 **Remove-AzureADUser** cmdlet，必须先连接到订阅。有关说明，请参阅[使用 Azure Active Directory V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="23fb3-p103">To use the **Remove-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="23fb3-124">连接后，使用下列语法删除单个用户帐户：</span><span class="sxs-lookup"><span data-stu-id="23fb3-124">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <Account>
```

<span data-ttu-id="23fb3-125">本示例将删除用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="23fb3-125">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="23fb3-126">**Remove-AzureAD** cmdlet 中的 **-ObjectID** 参数可接受帐户名（也称为"用户主体名称"）或帐户的对象 ID。</span><span class="sxs-lookup"><span data-stu-id="23fb3-126">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="23fb3-127">若要显示基于用户名的帐户名称，请使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="23fb3-127">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="23fb3-128">本示例显示名为 Caleb Sills 的用户的帐户名称。</span><span class="sxs-lookup"><span data-stu-id="23fb3-128">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="23fb3-129">若要删除基于用户名的帐户，请使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="23fb3-129">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a><span data-ttu-id="23fb3-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23fb3-130">See also</span></span>
<span data-ttu-id="23fb3-131"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="23fb3-131"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="23fb3-132">若要了解如何使用 Office 365 PowerShell 管理用户，请参阅下面这些附加主题：</span><span class="sxs-lookup"><span data-stu-id="23fb3-132">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="23fb3-133">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="23fb3-133">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="23fb3-134">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="23fb3-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="23fb3-135">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="23fb3-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="23fb3-136">使用 Office 365 PowerShell 删除用户帐户的许可证</span><span class="sxs-lookup"><span data-stu-id="23fb3-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="23fb3-137">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="23fb3-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="23fb3-138">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="23fb3-138">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="23fb3-139">Remove-MsolUser</span><span class="sxs-lookup"><span data-stu-id="23fb3-139">Remove-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [<span data-ttu-id="23fb3-140">Restore-MsolUser</span><span class="sxs-lookup"><span data-stu-id="23fb3-140">Restore-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [<span data-ttu-id="23fb3-141">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="23fb3-141">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

