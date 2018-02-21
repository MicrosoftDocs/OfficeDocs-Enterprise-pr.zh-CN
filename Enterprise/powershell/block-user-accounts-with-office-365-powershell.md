---
title: "使用 Office 365 PowerShell 冻结用户账户"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "解释如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 提供帐户的访问。"
ms.openlocfilehash: 34d144c982210ddc9d557b6094f71706f8edbb7f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="96279-103">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="96279-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="96279-104">**摘要：** 解释如何使用 Office 365 PowerShell 阻止和取消阻止对 Office 365 提供帐户的访问。</span><span class="sxs-lookup"><span data-stu-id="96279-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="96279-p101">阻止访问 Office 365 的帐户，可以防止任何人使用该帐户登录并访问服务和 Office 365 提供组织中的数据。如果阻止了对帐户的访问，当他们尝试登录用户会收到下面的错误消息：</span><span class="sxs-lookup"><span data-stu-id="96279-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. When you block access to the account, the user receives the following error message when they attempt to sign in:</span></span>
  
![阻止的 Office 365 帐户。](images/o365_powershell_account_blocked.png)
  
<span data-ttu-id="96279-108">您可以使用 Office 365 PowerShell 阻止访问单个和多个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="96279-108">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="96279-109">准备工作</span><span class="sxs-lookup"><span data-stu-id="96279-109">Before you begin</span></span>

- <span data-ttu-id="96279-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="96279-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="96279-112">如果阻止了用户帐户，可能需要最长为 24 小时才可生效，用户的所有设备和客户端上。</span><span class="sxs-lookup"><span data-stu-id="96279-112">When you block a user account, it might take as long as 24 hours to take effect on all the user's devices and clients.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="96279-113">使用 Office 365 PowerShell 阻止对单个用户帐户的访问</span><span class="sxs-lookup"><span data-stu-id="96279-113">Use Office 365 PowerShell to block access to individual user accounts</span></span>

<span data-ttu-id="96279-114">使用以下语法来阻止对单个用户帐户的访问：</span><span class="sxs-lookup"><span data-stu-id="96279-114">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

<span data-ttu-id="96279-115">此示例阻止访问用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="96279-115">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="96279-116">若要取消阻止该用户帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="96279-116">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

<span data-ttu-id="96279-117">在任何时候，您可以检查用户帐户需要具有以下命令封锁的状态：</span><span class="sxs-lookup"><span data-stu-id="96279-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a><span data-ttu-id="96279-118">使用 Office 365 PowerShell 阻止多个用户帐户访问权限</span><span class="sxs-lookup"><span data-stu-id="96279-118">Use Office 365 PowerShell to block access to multiple user accounts</span></span>

<span data-ttu-id="96279-119">首先，创建一个文本文件，包含如下的每一行上的一个帐户：</span><span class="sxs-lookup"><span data-stu-id="96279-119">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="96279-p103">在下面的命令示例文本文件是 C:\My Documents\Accounts.txt。将此替换为您的文本文件的路径和文件名称。</span><span class="sxs-lookup"><span data-stu-id="96279-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="96279-122">若要阻止访问该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="96279-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="96279-123">若要解除阻止该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="96279-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a><span data-ttu-id="96279-124">使用 Azure Active Directory V2 PowerShell 模块阻止访问用户帐户</span><span class="sxs-lookup"><span data-stu-id="96279-124">Use the Azure Active Directory V2 PowerShell module to block access to user accounts</span></span>

<span data-ttu-id="96279-p104">若要使用 Azure Active Directory V2 PowerShell 模块中的 **New-AzureADUser** cmdlet，首先必须连接到自己的订阅。有关说明，请参阅[连接到 Azure Active Directory V2 PowerShell 模块](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="96279-p104">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="96279-127">连接后，使用下列语法阻止单个用户帐户：</span><span class="sxs-lookup"><span data-stu-id="96279-127">After you have connected, use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="96279-128">Set-AzureAD cmdlet 中的 -ObjectID 参数可接受帐户名（也称为“用户主体名称”）或帐户的对象 ID。</span><span class="sxs-lookup"><span data-stu-id="96279-128">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="96279-129">此示例阻止访问用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="96279-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="96279-130">若要取消阻止此用户帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="96279-130">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="96279-131">若要显示 UPN 基于用户的显示名称的用户帐户，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="96279-131">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="96279-132">本示例显示名为 Caleb 窗台的用户的用户帐户 UPN。</span><span class="sxs-lookup"><span data-stu-id="96279-132">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="96279-133">若要阻止基于用户名的帐户，请使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="96279-133">To block an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="96279-134">在任何时候，您可以检查用户帐户需要具有以下命令封锁的状态：</span><span class="sxs-lookup"><span data-stu-id="96279-134">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

<span data-ttu-id="96279-135">要阻止访问的多个用户帐户，请创建一个文本文件，包含如下的每一行上的一个帐户名：</span><span class="sxs-lookup"><span data-stu-id="96279-135">To block access to multiple user accounts, create a text file that contains one account name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="96279-p105">在下面的命令示例文本文件是 C:\My Documents\Accounts.txt。将此替换为您的文本文件的路径和文件名称。</span><span class="sxs-lookup"><span data-stu-id="96279-p105">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="96279-138">若要阻止访问该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="96279-138">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="96279-139">若要解除阻止该文本文件中列出的帐户，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="96279-139">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="see-also"></a><span data-ttu-id="96279-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96279-140">See also</span></span>
<span data-ttu-id="96279-141"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="96279-141"></span></span>

<span data-ttu-id="96279-142">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="96279-142">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="96279-143">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="96279-143">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="96279-144">使用 Office 365 PowerShell 删除和还原用户帐户</span><span class="sxs-lookup"><span data-stu-id="96279-144">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="96279-145">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="96279-145">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="96279-146">使用 Office 365 PowerShell 删除用户帐户的许可证</span><span class="sxs-lookup"><span data-stu-id="96279-146">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="96279-147">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="96279-147">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="96279-148">获取内容</span><span class="sxs-lookup"><span data-stu-id="96279-148">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [<span data-ttu-id="96279-149">一组 MsolUser</span><span class="sxs-lookup"><span data-stu-id="96279-149">Set-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [<span data-ttu-id="96279-150">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="96279-150">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

