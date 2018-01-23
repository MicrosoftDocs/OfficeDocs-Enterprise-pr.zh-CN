---
title: "使用 Office 365 PowerShell 删除用户帐户的许可证"
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
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "解释如何使用 Office 365 PowerShell 删除先前已指派给用户的 Office 365 提供许可证。"
ms.openlocfilehash: 21aed391cf0395bf51a7e99cf9f8f0e34bfd9d10
ms.sourcegitcommit: f10e47df0dca4a241659f33061db5217ebc3401e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c4fe2-103">使用 Office 365 PowerShell 删除用户帐户的许可证</span><span class="sxs-lookup"><span data-stu-id="c4fe2-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c4fe2-104">**摘要：**解释如何使用 Office 365 PowerShell 删除先前已指派给用户的 Office 365 提供许可证。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="c4fe2-105">准备工作</span><span class="sxs-lookup"><span data-stu-id="c4fe2-105">Before you begin</span></span>

- <span data-ttu-id="c4fe2-p101">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c4fe2-108">若要查看组织中的授权计划 ( **AccountSkuID** ) 信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="c4fe2-109">使用 Office 365 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="c4fe2-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="c4fe2-110">使用 Office 365 PowerShell 查看帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="c4fe2-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="c4fe2-111">如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="c4fe2-112">简版（说明不含解释）</span><span class="sxs-lookup"><span data-stu-id="c4fe2-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="c4fe2-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="c4fe2-113"></span></span>

<span data-ttu-id="c4fe2-p102">此部分介绍的步骤未经任何渲染或过多解释。如果您有任何疑问或想了解更多信息，可以阅读本主题的其余部分。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="c4fe2-116">要从现有的用户帐户中删除许可证，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="c4fe2-117">本示例删除`litwareinc:ENTERPRISEPACK`BelindaN@litwareinc.com 的用户帐户 (Office 365 企业 E3) 许可证。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="c4fe2-118">要从一组现有的授权用户中删除许可证，请使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="c4fe2-119">**筛选器基于现有帐户属性的帐户**若要执行此操作，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="c4fe2-120">本示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3) 许可证从众所周知的美国销售部门中的用户。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="c4fe2-121">**使用特定的帐户列表**若要执行此操作，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="c4fe2-122">创建并保存一个文本文件，其中每一行都有一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="c4fe2-123">使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="c4fe2-124">本示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3) 许可证 C:\My Documents\Accounts.txt 文件中定义的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="c4fe2-125">要从所有现有的用户帐户中删除许可证，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="c4fe2-126">本示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3) 从所有现有的许可证授权用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="c4fe2-127">长版（说明附有详细解释）</span><span class="sxs-lookup"><span data-stu-id="c4fe2-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="c4fe2-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="c4fe2-128"></span></span>

<span data-ttu-id="c4fe2-p103">不会永远持续下去，并包含 Office 365 许可证： 迟早会同时那里一次当您需要从用户帐户中移除许可证。也许用户怎么回事请假;也许用户不再需要许可证;也许-好吧，有显然因多种原因为什么您可能希望移除用户许可证。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="c4fe2-p104">我们进一步转很重要，请注意，删除许可证要求您，好之前，删除该许可证： 禁用许可证上的所有服务不是不同于删除许可证。例如，假设我们已经耗尽我们所有 Office 365 许可证;换句话说，我们没有任何可用许可证。如果决定采用中[禁止访问 Office 365 PowerShell 的服务](disable-access-to-services-with-office-365-powershell.md)来禁用所有服务，比如 Belinda Newman 帐户上的过程。我们所做，多少许可证后将我们有提供给我们？没错： 零。是的从该主题中的过程将*禁用*Belinda 的许可证上的所有服务，但它不都会禁用 （即删除） 许可证本身。许可证将仍然是有效的而且它仍将分配给 Belinda Newman。她只是不能使用该许可证访问 Office 365 提供的任何服务。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="c4fe2-p105">这一点很重要： 如果您想要删除用户的许可证，您必须实际*删除*许可证。禁用所有服务将阻止用户登录到 Office 365，但它不会释放他或她的许可。如果您想要收回一个许可证，当前分配给您需要运行与此类似，使用_RemoveLicenses_参数来实际删除以前分配给 Belinda 许可的命令的命令的用户：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="c4fe2-142">运行该命令，并不再将授权 Belinda Newman 使用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c4fe2-p106">如您所见，当您使用_RemoveLicenses_参数必须指定要删除的许可证的名称。如果您不确定使用了哪些许可计划将许可证分配给用户只运行如下命令：`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="c4fe2-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="c4fe2-145">若要确定许可证确实已删除，可使用 Get-MsolUser 检查提及的用户帐户：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="c4fe2-146">如果一切按计划，将立即被 Belinda 的**isLicensed**属性设置`False`:</span><span class="sxs-lookup"><span data-stu-id="c4fe2-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="c4fe2-p107">另一种方式来释放许可证是删除用户帐户。有关详细信息，请参阅[删除和还原 Office 365 PowerShell 的用户帐户](delete-and-restore-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fe2-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c4fe2-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4fe2-149">See also</span></span>

<span data-ttu-id="c4fe2-150">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="c4fe2-151">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="c4fe2-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c4fe2-152">使用 Office 365 PowerShell 删除和还原用户帐户</span><span class="sxs-lookup"><span data-stu-id="c4fe2-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c4fe2-153">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="c4fe2-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c4fe2-154">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="c4fe2-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="c4fe2-155">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="c4fe2-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="c4fe2-156">获取内容</span><span class="sxs-lookup"><span data-stu-id="c4fe2-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="c4fe2-157">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="c4fe2-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="c4fe2-158">一组 MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="c4fe2-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="c4fe2-159">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="c4fe2-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="c4fe2-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="c4fe2-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="c4fe2-161">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="c4fe2-161">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

