---
title: "使用 Office 365 PowerShell 查看授权和未授权的用户"
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: "介绍如何使用 Office 365 PowerShell 查看授权和未授权的用户帐户。"
ms.openlocfilehash: fe4f75d9d8dbc85efbc71856192dbaece3e84fbc
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="48029-103">使用 Office 365 PowerShell 查看授权和未授权的用户</span><span class="sxs-lookup"><span data-stu-id="48029-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="48029-104">**摘要：**介绍如何使用 Office 365 PowerShell 查看许可和非许可用户帐户。</span><span class="sxs-lookup"><span data-stu-id="48029-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="48029-p101">您的 Office 365 组织中的用户帐户可能已从组织提供的许可计划中分配到部分或全部可用的许可证，或者未分配到任何许可证。您可以使用 Office 365 PowerShell 快速查找您组织中的授权和未授权的用户。</span><span class="sxs-lookup"><span data-stu-id="48029-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="48029-107">准备工作</span><span class="sxs-lookup"><span data-stu-id="48029-107">Before you begin</span></span>

- <span data-ttu-id="48029-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="48029-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="48029-110">如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="48029-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="48029-111">简版（说明不含解释）</span><span class="sxs-lookup"><span data-stu-id="48029-111">The short version (instructions without explanations)</span></span>

<span data-ttu-id="48029-p103">此部分介绍的步骤未经任何渲染或过多解释。如果您有任何疑问或想了解更多信息，可以阅读本主题的其余部分。</span><span class="sxs-lookup"><span data-stu-id="48029-p103">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="48029-114">若要查看组织中所有用户帐户及其授权状态的列表，请在 Office 365 PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="48029-114">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="48029-115">若要查看组织中所有未授权用户帐户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="48029-115">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="48029-116">若要查看组织中所有授权用户帐户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="48029-116">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="48029-117">长版（说明附有详细解释）</span><span class="sxs-lookup"><span data-stu-id="48029-117">The long version (instructions with detailed explanations)</span></span>

<span data-ttu-id="48029-p104">Office 365 用户帐户和 Office 365 许可证无需一一对应：Office 365 用户可以没有 Office 365 许可证，也可以不向用户分配 Office 365 许可证。（实际上，一个用户帐户甚至可以有*多个* Office 365 许可证。）新建 Office 365 用户帐户时（有关详细信息，请参阅[使用 Windows PowerShell 许可 Office 365 用户](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx)一文），无需为用户分配许可证。也就是说，即使新用户的帐户有效，也无法登录 Office 365。如果尝试登录，将会看到如下内容：</span><span class="sxs-lookup"><span data-stu-id="48029-p104">Office 365 user accounts and Office 365 licenses don't need to have a one-to-one correspondence: it's possible to have Office 365 users who do not have an Office 365 license, and it's possible to have Office 365 licenses that haven't been assigned to a user. (In fact, a single user account can even have  *multiple*  Office 365 licenses.) When you create a new Office 365 user account (see the article [License Office 365 users with Windows PowerShell](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx) for more information) you don't have to assign that user a license: the new user will have a valid account, but he or she won't be able to sign in to Office 365. If they try to sign in, they'll see something similar to this:</span></span>
  
![没有有效 Office 365 许可证的用户。](images/o365_powershell_no_license.png)
  
<span data-ttu-id="48029-p105">同样，您可能有一个用户需要休假或者休产假/陪产假，因此将要延长时间。在这种情况下，您可以删除用户的许可证，但使用户帐户保持不变（即地址、电话号码等所有属性值保持不变）。这样，您可以将其许可证分配给其他人（例如，接替休假人员的临时工作人员）。用户回到工作岗位后，您可以向其签发新的许可证，他们将可以继续工作，就像从来没有离开过一样。</span><span class="sxs-lookup"><span data-stu-id="48029-p105">Likewise, you might have a user who will be taking some extended time off, perhaps for a sabbatical or for maternity/paternity leave. In a case like that, you could remove the user's license but leave the user account intact (that is, leave all its property values, such as address and phone number, as-is). By doing that, you can assign their license to someone else (like, say, a temporary worker filling in for the person on leave). When the user returns to work you can issue them a new license and they'll be able to resume working as if they'd never been gone.</span></span>
  
<span data-ttu-id="48029-p106">这就意味着，您确实可以使用户具有帐户但不具有许可证。反之亦然。</span><span class="sxs-lookup"><span data-stu-id="48029-p106">Which simply means that, yes, you can have users who have accounts but who don't have licenses. Or vice-versa.</span></span>
  
<span data-ttu-id="48029-p107">文章 [使用 Office 365 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)介绍了如何确定您的组织购买的 Office 365 许可证数量，以及为用户分配的这些许可证数量。这是很重要的信息。但了解已向哪些用户分配了这些许可证，哪些用户没有分配许可证同样重要。本文将告诉您如何做到这一点。</span><span class="sxs-lookup"><span data-stu-id="48029-p107">The article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) explains how you can determine the number of Office 365 licenses your organization has purchased as well as how many of those licenses have been assigned to users. That's important information. Equally important, however is knowing which of your users have been assigned these licenses and which ones haven't. And this article will tell you how to do just that.</span></span>
  
<span data-ttu-id="48029-p108">您可能已经知道， **Get-MsolUser** cmdlet 将返回有关所有 Office 365 用户帐户的信息。需要有关所有 Office 365 用户的快速参考信息？请在 Office 365 PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="48029-p108">As you probably know, the **Get-MsolUser** cmdlet returns information about all your Office 365 user accounts. Need some quick info about all your Office 365 users? Then run this command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="48029-135">反之，Get-MsolUser 将返回与以下类似的数据：</span><span class="sxs-lookup"><span data-stu-id="48029-135">In turn, Get-MsolUser returns data similar to this:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BelindaN@litwareinc.com     Belinda Newman                  False
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

<span data-ttu-id="48029-p109">正如您所见，返回的其中一个属性值是 **isLicensed** 属性的值。如果 **isLicensed** 为 `False`，则意味着用户没有 Office 365 的许可证。换句话说，如果您愿意，您可以滚动用户列表，并挑选出将 **isLicensed** 属性设置为 `False` 的用户。</span><span class="sxs-lookup"><span data-stu-id="48029-p109">As you can see, one of the property values returned is for the **isLicensed** property. If **isLicensed** is equal to `False` that means that the user doesn't have a license for Office 365. In other words, and if you wanted to, you could simply scroll through your list of users and pick out the ones where the **isLicensed** property is set to `False`.</span></span>
  
<span data-ttu-id="48029-p110">无论如何，只要您的用户数量相对较少，即可滚动用户列表、尝试挑选出未许可用户。但是，如果您具有大量用户，滚动列表将会非常缓慢。（此外，根据 Windows PowerShell 的配置方式，可能完全无法这样做。这是由于对在 Windows PowerShell 控制台中一次可显示的输出行数存在限制。）</span><span class="sxs-lookup"><span data-stu-id="48029-p110">At any rate, scrolling through a list of users trying to pick out the unlicensed users works as long as you have a relatively small number of users. If you have a large number of users, however, scrolling through that list will be, at best, extremely tedious. (And, depending on how Windows PowerShell has been configured, perhaps downright impossible. That's because there's a limit to the number of lines of output that can be displayed in the Windows PowerShell console at any one time.)</span></span>
  
<span data-ttu-id="48029-143">牢记这一点，列出未许可用户的更好方式是转为运行此命令：</span><span class="sxs-lookup"><span data-stu-id="48029-143">With that in mind, a much better way to list your unlicensed users is to run this command instead:</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="48029-p111">该命令仅返回没有 Office 365 许可证的用户。即：</span><span class="sxs-lookup"><span data-stu-id="48029-p111">That command returns only those users who don't have a license for Office 365. In other words:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="48029-p112">可以看到，我们有一个未许可用户。如果我们仅需要 *已许可*  用户列表，应该怎么做？这略显复杂，但仅一点点复杂而已：</span><span class="sxs-lookup"><span data-stu-id="48029-p112">As you can see we have one unlicensed user. And what is we only wanted a list of the  *licensed*  users? That's a tiny bit more complicated, but only the tiniest bit:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true}
```

<span data-ttu-id="48029-149">查找 **isLicensed** 属性为 `True` 的所有用户帐户的命令将返回与以下类似的信息：</span><span class="sxs-lookup"><span data-stu-id="48029-149">That command, which looks for all the user accounts where the **isLicensed** property is equal to `True`, returns information similar to this:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

<span data-ttu-id="48029-p113">可以看到，未返回 Belinda Newman 的信息。为什么没有返回？是的，原因是：Belinda 的帐户的 **isLicensed** 属性未设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="48029-p113">As you can see, information is not returned for Belinda Newman. Why not? You got it: because the **isLicensed** property for Belinda's account is not set to `True`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="48029-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48029-153">See also</span></span>
<span data-ttu-id="48029-154"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="48029-154"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="48029-155">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="48029-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="48029-156">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="48029-156">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="48029-157">Where-Object</span><span class="sxs-lookup"><span data-stu-id="48029-157">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

