---
title: "使用 Office 365 PowerShell 向用户帐户分配许可证"
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "解释如何使用 Office 365 PowerShell 分派给未经授权的用户的 Office 365 提供许可证。"
ms.openlocfilehash: 88628a78179605c734cd1d3f114a8a1dcb712376
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="ac436-103">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="ac436-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="ac436-104">**摘要：** 解释如何使用 Office 365 PowerShell 分派给未经授权的用户的 Office 365 提供许可证。</span><span class="sxs-lookup"><span data-stu-id="ac436-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="ac436-p101">Office 365 中的用户帐户授权很重要，因为用户不能使用任何 Office 365 提供服务，直到他们的帐户被授予使用许可。您可以使用 Office 365 PowerShell 高效地将许可证分配给未授权的帐户，尤其是多个帐户。</span><span class="sxs-lookup"><span data-stu-id="ac436-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="ac436-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="ac436-107">Before you begin</span></span>
<span data-ttu-id="ac436-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="ac436-108"></span></span>

- <span data-ttu-id="ac436-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ac436-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ac436-p103">使用**Get MsolAccountSku** cmdlet 可以在组织中的每个计划中查看可用的授权计划和可用的许可证数。每个计划中的可用许可证数量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。有关授权计划、 许可协议和服务的详细信息，请参阅[查看许可证和服务与 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ac436-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ac436-114">若要查找未授权的帐户您的组织中，运行命令`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="ac436-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="ac436-p104">您可以仅对具有**UsageLocation**属性设置为有效的 ISO 3166-1-2 字母的国家/地区代码的用户帐户分配许可证。例如，我们的美国和法国的 FR。在某些国家，某些 Office 365 服务不可用。有关详细信息，请参阅[关于许可限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="ac436-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="ac436-p105">若要查找帐户没有一个**UsageLocation**值，运行命令`Get-MsolUser -All | where {$_.UsageLocation -eq $null}`。若要在某个帐户上设置**UsageLocation**值，请使用语法`Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`。例如， `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。</span><span class="sxs-lookup"><span data-stu-id="ac436-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="ac436-122">如果您使用**Get MsolUser** cmdlet 而无需使用`-All`参数，返回前 500 个客户。</span><span class="sxs-lookup"><span data-stu-id="ac436-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="ac436-123">简版（说明不含解释）</span><span class="sxs-lookup"><span data-stu-id="ac436-123">The short version (instructions without explanations)</span></span>
<span data-ttu-id="ac436-124"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="ac436-124"></span></span>

<span data-ttu-id="ac436-p106">此部分介绍了没有详细说明的过程。如果您有疑问或想了解更多信息，您可以阅读本主题的其余部分。</span><span class="sxs-lookup"><span data-stu-id="ac436-p106">This section presents the procedures without detailed explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="ac436-127">要将许可证分配给用户，请在 Office 365 PowerShell 中使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="ac436-127">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="ac436-128">本示例指定从许可证`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3) 给未经授权的用户的授权计划`belindan@litwareinc.com`。</span><span class="sxs-lookup"><span data-stu-id="ac436-128">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ac436-129">若要向多个未授权用户分配许可证，请使用以下句法：</span><span class="sxs-lookup"><span data-stu-id="ac436-129">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="ac436-130">**备注**</span><span class="sxs-lookup"><span data-stu-id="ac436-130">**Notes**</span></span>
  
- <span data-ttu-id="ac436-131">您无法使用相同的许可计划为用户分配多个许可证。</span><span class="sxs-lookup"><span data-stu-id="ac436-131">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="ac436-132">如果没有足够可用的许可证，许可证分配给用户他们正在**获取 MsolUser** cmdlet 返回之前的可用许可证不足的顺序。</span><span class="sxs-lookup"><span data-stu-id="ac436-132">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="ac436-133">本示例指定许可证`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3) 对所有未经授权的用户的授权计划。</span><span class="sxs-lookup"><span data-stu-id="ac436-133">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="ac436-134">本示例向美国销售部门的未授权用户分配这些相同的许可证。</span><span class="sxs-lookup"><span data-stu-id="ac436-134">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="ac436-135">长版（说明附有详细解释）</span><span class="sxs-lookup"><span data-stu-id="ac436-135">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="ac436-136"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="ac436-136"></span></span>

<span data-ttu-id="ac436-p107">[查看授权和未授权用户使用 Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md)文章中所述，就可能让用户拥有有效的 Office 365 提供用户帐户，但谁不发动了哪些 Office 365 提供许可证。这意味着，有效的帐户或任何有效的帐户，这些用户不能登录到 Office 365。然后，如果您无法登录，则不能利用任何 Office 365 提供服务。</span><span class="sxs-lookup"><span data-stu-id="ac436-p107">As noted in the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), it's possible to have users who have valid Office 365 user accounts, but who have not been issued an Office 365 license. That means that, valid account or no valid account, those users will not be able to log on to Office 365. And if you can't log on, you can't take advantage of any Office 365 services.</span></span>
  
<span data-ttu-id="ac436-140">上述文章还说明了我们可以通过运行此命令返回未许可用户帐户的列表：</span><span class="sxs-lookup"><span data-stu-id="ac436-140">The aforementioned article also noted that we can return a list of unlicensed user accounts by running this command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="ac436-141">该命令将返回任何用户的 Office 365 目前尚未得到有关的信息：</span><span class="sxs-lookup"><span data-stu-id="ac436-141">That command returns information about any users who are not currently licensed for Office 365:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="ac436-p108">正如您所看到的我们有一个未授权的用户： Belinda Newman。因此我们如何分配 Belinda Office 365 许可证？</span><span class="sxs-lookup"><span data-stu-id="ac436-p108">As you can see, we have one unlicensed user: Belinda Newman. So how do we go about assigning Belinda an Office 365 license?</span></span>
  
<span data-ttu-id="ac436-144">对于初学者，我们将运行**Get MsolAccountSku** cmdlet[查看许可证和服务与 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)文章所述：</span><span class="sxs-lookup"><span data-stu-id="ac436-144">For starters, we're going to run the **Get-MsolAccountSku** cmdlet discussed in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="ac436-145">此命令将返回类似于以下的数据：</span><span class="sxs-lookup"><span data-stu-id="ac436-145">That command returns data similar to this:</span></span>
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

<span data-ttu-id="ac436-p109">我们是为什么运行**获取 MsolAccountSku**的？("Sku，"如果您想知道，是的缩写"库存单元。对于我们来说，它是只是业务-说出的"产品。）有两个原因为什么我们运行**Get MsolAccountSku**。首先，我们需要确保我们实际上有一个许可证分配 Belinda。我们有，我们可以将其分配任何许可证吗？若要确定，我们会**ActiveUnits**属性 (25) 的值，并减去**WarningUnits** (0) 和**ConsumedUnits** (24) 属性的值：</span><span class="sxs-lookup"><span data-stu-id="ac436-p109">Why did we run **Get-MsolAccountSku** ? ("Sku," in case you're wondering, is short for "stock-keeping unit." For our purposes, that's just business-speak for "product.") There are two reasons why we ran **Get-MsolAccountSku**. First, we need to make sure we actually have a license to assign Belinda. Do we have any licenses we can assign her? To determine that, we take the value of **ActiveUnits** property (25) and subtract the values of the **WarningUnits** (0) and **ConsumedUnits** (24) properties:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="ac436-p110">**ActiveUnits**属性告诉我们我们购买的许可证数量和组合的值的**WarningUnits**和**ConsumedUnits**告诉我们多少个许可证目前正在使用。如果我们减去已说的从我们购买的许可证数量的许可证的数量，我们将知道多少个许可证是否仍然可用。会让它，因为我们有一个许可证可用于分发：</span><span class="sxs-lookup"><span data-stu-id="ac436-p110">The **ActiveUnits** property tells us how many licenses we've purchased, and the combined value of **WarningUnits** and **ConsumedUnits** tells us how many licenses are currently in use. If we subtract the number of licenses already spoken for from the number of licenses we purchased, we'll know how many licenses are still available. As luck would have it, we have one license available for distribution:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="ac436-p111">第二，为了新的许可证，我们需要知道我们授权计划的名称分配 Belinda （这就是说，我们需要知道**AccountSkuId** ）。在这种情况下，这很简单： 我们只有一个单一的授权计划 ( `litwareinc:ENTERPRISEPACK`)。但是请注意，可能会对组织有多个授权计划。在这种情况下， **Get MsolAccountSku**将返回两个不同**AccountSkuIds**，您将需要选择相应的授权计划分配许可证时。现在，不过，我们要坚持使用最简单的情况，假设我们只是一个授权的计划。</span><span class="sxs-lookup"><span data-stu-id="ac436-p111">Second, in order to assign Belinda a new license we need to know the name of our licensing plan (that is, we need to know the **AccountSkuId** ). In this case, that's easy: we only have a single licensing plan ( `litwareinc:ENTERPRISEPACK`). Note, however, that it's possible for an organization to have multiple licensing plans. In that case, **Get-MsolAccountSku** would return two different **AccountSkuIds**, and you would need to pick the appropriate licensing plan when assigning licenses. For now, though, we're going to stick with the simplest case, and assume we have just one licensing plan.</span></span>
  
<span data-ttu-id="ac436-p112">那么如何**我们分配 Belinda Newman 新的许可证？喜欢这个：</span><span class="sxs-lookup"><span data-stu-id="ac436-p112">So then how  *do*  we assign Belinda Newman a new license? Like this:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ac436-162">也是您需要做： 只需调用**一组 MsolUserLicense** cmdlet，确保您指定的用户和相应的授权计划的_范围内_参数。</span><span class="sxs-lookup"><span data-stu-id="ac436-162">That's also you have to do: just call the **Set-MsolUserLicense** cmdlet, making sure that you specify the _UserPrincipalName_ parameter for the user and the appropriate licensing plan.</span></span>
  
<span data-ttu-id="ac436-163">当**一组 MsolUserLicense**完成运行时，您会看到类似于此屏幕上：</span><span class="sxs-lookup"><span data-stu-id="ac436-163">When **Set-MsolUserLicense** finishes running, you'll see something similar to this onscreen:</span></span>
  
 `PS C:\\windows\\system32>`
  
<span data-ttu-id="ac436-p113">换句话说，它不会看起来有的事情。验证用户具有已分配的许可，运行如下命令：</span><span class="sxs-lookup"><span data-stu-id="ac436-p113">In other words, it won't look like anything has happened. To verify that the user has been assigned a license, run a command like the following:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

<span data-ttu-id="ac436-166">如果一切运行正常，您应看到现在将 Belinda 的 isLicensed 属性设置为 True:</span><span class="sxs-lookup"><span data-stu-id="ac436-166">If everything worked as expected, you should see that Belinda's isLicensed property is now set to True:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [!安全说明]<span data-ttu-id="ac436-p114">: 问得好： 如果您犯了一个并尝试向已有许可证的用户分派许可证？您最终会为单个用户提供两个许可证？> 快速的答案吗？没有;Office 365 不允许您分配给同一用户的多个许可证。（好吧，从相同的授权计划的多个许可证，这就是。如果您尝试这样做您的命令将失败并显示以下错误消息： > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> 不可否认，此错误消息是稍微有点令人误解： 许可证不是真的无效，它只是分配给用户谁已经*有*一个许可证。但是，放在一边，错误消息的重要的事情是一个用户不会得到多个许可证。</span><span class="sxs-lookup"><span data-stu-id="ac436-p114"> Good question: what if you made a mistake and tried to assign a license to a user who already has a license? Will you end up giving two licenses to a single user? > The quick answer? No; Office 365 won't let you assign more than one license to the same user. (Well, more than one license from the same licensing plan, that is.) If you try to do that your command will fail with the following error message: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Admittedly, that error message is a tiny bit misleading: the license isn't really invalid, it's just being assigned to a user who already  *has*  a license. But, error message aside, the important thing is that one user won't end up with multiple licenses.</span></span>
  
<span data-ttu-id="ac436-p115">如刚才所见，它是非常容易使用的 Office 365 PowerShell 将单个许可证分配给单个用户。和这产生了一个明显的问题： 岂不是一样简单，也许更容易，使用 Office 365 管理中心为单个用户分配单个许可证？嗯，有可能;这取决于，在情况下，无论您是使用 Windows PowerShell 更舒适或更娴熟地使用 Office 365 管理中心。其中 Windows PowerShell 确实非常出色，但是，是当您需要分配给多个用户的多个许可证。例如，此命令将 Office 365 许可证分配给任何没有许可证的用户：</span><span class="sxs-lookup"><span data-stu-id="ac436-p115">As you've just seen, it's very easy to use Office 365 PowerShell to assign a single license to a single user. And that leads to an obvious question: wouldn't it be just as easy, maybe even easier, to use the Office 365 admin center to assign a single license to a single user? Well, maybe; that depends, in part, on whether you're more comfortable using Windows PowerShell or more comfortable using the Office 365 admin center. Where Windows PowerShell really shines, however, is when you need to assign multiple licenses to multiple users. For example, this command assigns an Office 365 license to any of your users that don't already have a license:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ac436-p116">在上述命令中，我们使用**Get MsolUser**和_UnlicensedUsersOnly_参数来返回所有未授权的用户帐户的集合。我们然后将该集合传递到**一组 MsolUserLicense** cmdlet;反过来，**集 MsolUserLicense**分配许可证 (来自`litwareinc:ENTERPRISEPACK`授权计划) 为集合中的每个用户。</span><span class="sxs-lookup"><span data-stu-id="ac436-p116">In the preceding command, we use **Get-MsolUser** and the _UnlicensedUsersOnly_ parameter to return a collection of all the unlicensed user accounts. We then pass that collection to the **Set-MsolUserLicense** cmdlet; in turn, **Set-MsolUserLicense** assigns a license (taken from the `litwareinc:ENTERPRISEPACK` licensing plan) to each user in the collection.</span></span>
  
<span data-ttu-id="ac436-p117">不过，如果有 5 个未经许可的用户，但只有一个可用的许可证？在这种情况下**设置 MsolUserLicense**将**获得 MsolUser**返回的第一个用户提供可用的许可证。**集 MsolUserLicense**将尽职尽责地试图向其他四个用户分派许可证，但这些尝试的所有四个会失败以及下面的错误消息：</span><span class="sxs-lookup"><span data-stu-id="ac436-p117">Ah, but what if you have 5 unlicensed users but only one available license? In that case **Set-MsolUserLicense** will give the available license to the first user returned by **Get-MsolUser**. **Set-MsolUserLicense** will then dutifully try to assign a license to the other four users, but all four of those attempts will fail along with the following error message:</span></span>
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
<span data-ttu-id="ac436-p118">换句话说，一组 MsolUserLicense 不会只是失败。相反，它将指定任意多个许可证，因为它可以。那时将会失败。</span><span class="sxs-lookup"><span data-stu-id="ac436-p118">In other words, Set-MsolUserLicense won't just fail. Instead, it will assign as many licenses as it can. Only then will it fail.</span></span>
  
<span data-ttu-id="ac436-p119">让我们尝试另一个示例。也许您想要向销售部门中的所有用户分派许可证。没关系：</span><span class="sxs-lookup"><span data-stu-id="ac436-p119">Let's try another example. Maybe you'd like to assign a license to all the users in the Sales department. No problem:</span></span>
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ac436-189">或者，如果您想要来点新奇的，想将错误消息和计算处理保持在最低水平，只需将许可证分配给销售部门中的未许可用户。</span><span class="sxs-lookup"><span data-stu-id="ac436-189">Or, if you want to get really fancy, and if you want to keep error messages and computing processing to a minimum, just assigned a license to unlicensed users from the Sales department:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ac436-p120">毕竟，没有尝试已有许可证的许可证用户点。因为我们已经看到，它不起作用。</span><span class="sxs-lookup"><span data-stu-id="ac436-p120">After all, there's no point trying to license users who already have a license. As we've already seen, that won't work.</span></span>
  
<span data-ttu-id="ac436-p121">这里是另一个示例。也许您想要所有美国用户的当前没有 Office 365 都许可证的都许可证。在这种情况下：</span><span class="sxs-lookup"><span data-stu-id="ac436-p121">Here's another example. Maybe you'd like to license all the US users who don't currently have an Office 365 license. In that case:</span></span>
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ac436-195">等等。</span><span class="sxs-lookup"><span data-stu-id="ac436-195">And so on and so on.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ac436-p122">若要运行的命令说，对所有未经授权的用户颁发许可证需要多长时间？这是难以说： 这取决于您有为您的网络连接速度的用户数，无所不包。如果您有几个用户许可证这会相当快速地转到 （即，它不会花费超过一分钟或两个）。如果有 10000 个用户许可它显然需要稍长的时间。但远，只要它能够通过使用 Office 365 管理中心将许可证分配给 10000 个用户。</span><span class="sxs-lookup"><span data-stu-id="ac436-p122">How long does it take to run a command that, say, issues licenses to all your unlicensed users? That's difficult to say: it depends on everything from the number of users you have to the speed of your network connection. If you have a couple hundred users to license this will go reasonably quickly (that is, it shouldn't take more than a minute or two). If you have 10,000 users to license it will obviously take a little longer. But nowhere near as long as it would take to assign licenses to 10,000 users by using the Office 365 admin center.</span></span> 
  
<span data-ttu-id="ac436-p123">只要我们在主题上，以下是您需要提防的分配许可证时： 如果用户没有配置为**UsageLocation**属性的值则不能将该用户指派一个 Office 365 提供许可证。相反，将收到错误信息类似于这样：</span><span class="sxs-lookup"><span data-stu-id="ac436-p123">As long as we're on the subject, here's something you need to watch out for when assigning licenses: if a user does not have a value configured for the **UsageLocation** property you won't be able to assign that user an Office 365 license. Instead, you'll get an error message similar to this:</span></span>
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
<span data-ttu-id="ac436-p124">有点迂回的方式，此错误消息告诉我们，问题中的用户不具备**UsageLocation**。您可能已经猜到， **UsageLocation**属性 （这表明该地区或国家用户通常使用 Office 365） 是极其重要的。为什么？这是因为用户可用的服务不只取决于用户所在的位置还购买许可包： 由于局部规则和法规，有些服务可能不能给某些用户。如果用户没有**UsageLocation**，Office 365 已无法知道哪些服务可以依法公开给该用户。因此，Office 365 无法提供任何服务用于该用户，至少不直到指定了**UsageLocation** 。</span><span class="sxs-lookup"><span data-stu-id="ac436-p124">In somewhat-roundabout fashion, this error message tells us that the user in question has not been assigned a **UsageLocation**. As you might have guessed, the **UsageLocation** property (which indicates the region or country where the user typically uses Office 365) is extremely important. Why? That's because the services available to a user depend not only on the licensing pack that you purchased but also on where the user lives: due to local rules and regulations, some services might not be available to some users. If a user doesn't have a **UsageLocation**, Office 365 has no way of knowing which services can legally be exposed to that user. Therefore, Office 365 can't offer any services to that user, at least not until the **UsageLocation** has been specified.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ac436-p125">配置用户帐户时您将立即知道是否有与世界上的指定部分的所有许可限制。例如，如果将**UsageLocation**为已授权的用户更改为伊朗 ( `IR`)，该命令将失败，出现此错误消息： `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> 这是因为 Office 365 不是当前可供用户在伊朗。有关详细信息，请参阅[关于许可限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。顺便说一下，Office 365 使用标准化 (ISO) 由国际组织的双字母国家/地区代码。您可以在[ISO 网站](https://go.microsoft.com/fwlink/p/?LinkId=84073)上找到这些代码。</span><span class="sxs-lookup"><span data-stu-id="ac436-p125">When you configure a user account you'll know immediately if there are any license restrictions associated with the specified part of the world. For example, if you change the **UsageLocation** for a licensed user to Iran ( `IR`), the command will fail with this error message: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> That's because Office 365 is not currently available to users in Iran. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidentally, Office 365 uses the two-letter country codes produced by the International Organization for Standardization (ISO). You can find those codes on the [ISO web site](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span></span> 
  
<span data-ttu-id="ac436-214">如果您想要验证给定的用户有**UsageLocation** ，您可以使用类似下面的命令：</span><span class="sxs-lookup"><span data-stu-id="ac436-214">If you want to verify that a given user has a **UsageLocation** you can use a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

<span data-ttu-id="ac436-215">或者，可以返回使用此命令没有**UsageLocation**的所有用户的列表：</span><span class="sxs-lookup"><span data-stu-id="ac436-215">Alternatively, you can return a list of all the users who don't have a **UsageLocation** by using this command:</span></span>
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> <span data-ttu-id="ac436-p126">当您分派许可证给用户，用户，默认情况下允许访问到您的组织有权访问的所有 Office 365 提供服务。例如，如果您的 Office 365 企业 E3 购买许可证，新授权用户将自动授予访问 Exchange 联机、 Skype 等服务的在线业务和 SharePoint Online。如果您希望限制对这些服务的用户的访问权限 (例如，您可能希望用户能够访问 SharePoint Online 但*不是*到 Exchange 联机和 Skype 的在线业务) 然后，请参阅文章[禁用访问 Office 365 的服务PowerShell](disable-access-to-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ac436-p126">When you assign a license to a user that user will, by default, be given access to all the Office 365 services that your organization has access to. For example, if you purchased licenses for Office 365 Enterprise E3, your newly-licensed user will automatically be granted access to services like Exchange Online, Skype for Business Online, and SharePoint Online. If you would prefer to limit a user's access to those services (for example, you might want a user to have access to SharePoint Online but  *not*  to Exchange Online and Skype for Business Online) then see the article [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span></span> 
  
## <a name="new-to-office-365"></a><span data-ttu-id="ac436-219">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="ac436-219">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="ac436-p127">![LinkedIn 学习的短图标](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 提供指向新建？**        [Office 365 管理员和 IT 专业人员使用](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5)，LinkedIn 学习者发现免费视频课程。</span><span class="sxs-lookup"><span data-stu-id="ac436-p127">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="ac436-222">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac436-222">See Also</span></span>
<span data-ttu-id="ac436-223"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="ac436-223"></span></span>

<span data-ttu-id="ac436-224">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="ac436-224">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="ac436-225">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="ac436-225">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ac436-226">使用 Office 365 PowerShell 删除和还原用户帐户</span><span class="sxs-lookup"><span data-stu-id="ac436-226">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ac436-227">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="ac436-227">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ac436-228">使用 Office 365 PowerShell 删除用户帐户的许可证</span><span class="sxs-lookup"><span data-stu-id="ac436-228">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="ac436-229">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="ac436-229">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="ac436-230">获得 MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="ac436-230">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="ac436-231">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="ac436-231">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="ac436-232">一组 MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="ac436-232">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="ac436-233">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="ac436-233">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="ac436-234">选择对象</span><span class="sxs-lookup"><span data-stu-id="ac436-234">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="ac436-235">Where-Object</span><span class="sxs-lookup"><span data-stu-id="ac436-235">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

