---
title: "使用 Office 365 PowerShell 查看帐户许可证和服务详细信息"
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
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: "解释如何使用 Office 365 PowerShell 确定已指派给用户的 Office 365 提供服务。"
ms.openlocfilehash: 69784b43e6e2b24f776d07a937877e5ae0c74888
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="a9cd1-103">使用 Office 365 PowerShell 查看帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="a9cd1-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="a9cd1-104">**摘要：**解释如何使用 Office 365 PowerShell 确定已指派给用户的 Office 365 提供服务。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="a9cd1-p101">Office 365 中许可证的授权计划 （也称为的 Sku 或 Office 365 计划） 允许用户访问的计划，这些计划定义 Office 365 提供服务。但是，用户可能不具有访问中当前分配给它们的许可证提供的所有服务。Office 365 PowerShell 可用于对用户帐户查看服务的状态。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="a9cd1-108">准备工作</span><span class="sxs-lookup"><span data-stu-id="a9cd1-108">Before you begin</span></span>
<span data-ttu-id="a9cd1-109"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="a9cd1-109"></span></span>

- <span data-ttu-id="a9cd1-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a9cd1-112">使用命令`Get-MsolAccountSku`和`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`查找以下信息：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-112">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="a9cd1-113">您的组织中提供的许可计划。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-113">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="a9cd1-114">每个许可计划中提供的服务以及列出它们的顺序（索引号）。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-114">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="a9cd1-115">有关授权计划、 许可和服务的详细信息，请参阅[查看许可证和服务与 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-115">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a9cd1-116">使用命令`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`若要查找分配给用户，并在订单的许可证所列 （索引号）。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-116">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="a9cd1-117">如果您使用 **Get-MsolUser** cmdlet 而无需使用 _All_ 参数，仅可返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-117">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="a9cd1-118">简版（说明不含解释）</span><span class="sxs-lookup"><span data-stu-id="a9cd1-118">The short version (instructions without explanations)</span></span>
<span data-ttu-id="a9cd1-119"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="a9cd1-119"></span></span>

<span data-ttu-id="a9cd1-120">若要查看用户有权访问的所有 Office 365 PowerShell 的服务，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-120">To view all the Office 365 PowerShell services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="a9cd1-p103">本示例显示 BelindaN@litwareinc.com 的用户有权访问的服务。这将显示与所有许可证分配给她的帐户相关联的服务。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="a9cd1-123">本示例说明了用户 BelindaN@litwareinc.com 使用向她的帐户（索引号是 0）分配的第一个许可证有权访问的服务。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="a9cd1-124">若要查找已启用或未启用特定服务的所有授权用户，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-124">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="a9cd1-125">这些示例使用下面的信息：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-125">These examples use the following information:</span></span>
  
- <span data-ttu-id="a9cd1-126">使我们感兴趣的 Office 365 服务访问的许可证是第一个许可证分配给所有用户 （索引号为 0）。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-126">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="a9cd1-p104">我们感兴趣的 Office 365 提供服务是 Skype 的在线业务和在线交换。对于与授权计划关联的许可证，Skype 的在线业务是列出六个服务 （索引号为 5），且 Exchange Online 9 日服务列出 （索引号为 8）。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="a9cd1-129">本示例返回所有获得许可的用户启用了 Skype 的在线业务和在线交换。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-129">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="a9cd1-130">本示例返回所有授权的用户未启用 Skype 的在线业务或 Exchange 联机。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-130">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="a9cd1-131">长版（说明附有详细解释）</span><span class="sxs-lookup"><span data-stu-id="a9cd1-131">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="a9cd1-132"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="a9cd1-132"></span></span>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a><span data-ttu-id="a9cd1-133">查找用户有权访问 Office 365 PowerShell 服务</span><span class="sxs-lookup"><span data-stu-id="a9cd1-133">Find the Office 365 PowerShell services that a user has access to</span></span>

<span data-ttu-id="a9cd1-p105">很显然一定要知道哪些用户已签发 Office 365 的许可证以及哪些用户还没有。（请参阅文章[使用 Office 365 PowerShell 的授权和未授权用户查看](view-licensed-and-unlicensed-users-with-office-365-powershell.md)详细信息）。但是，仅有一个 Office 365 许可证并没有告诉您的任何有关该用户实际上如何使用 Office 365。可以他或她使用 Exchange 联机或 Skype 的在线业务？此用户可以访问 SharePoint Online 吗？他或她是否有权访问 Office Professional Plus？没有许可证只是意味着用户都有可能来访问这些服务。但是，提供给用户的功能取决于他或她的许可证已启用的服务。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p105">It's obviously important for you to know which users have been issued Office 365 licenses and which users haven't. (See the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) for more information). However, simply having an Office 365 license doesn't tell you anything about what that user can actually do with Office 365. Can he or she use Exchange Online or Skype for Business Online? Can this user access SharePoint Online? Does he or she have access to Office Professional Plus? Having a license simply means that the user has the potential to access these services. However, the capabilities available to a user depend on the services that have been enabled on his or her license.</span></span>
  
<span data-ttu-id="a9cd1-p106">我们如何可以确定哪些 Office 365 功能用户具有访问权限？为此，我们需要运行一个与此类似的命令：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p106">So how can we determine which Office 365 features a user has access to? To do that we need to run a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

<span data-ttu-id="a9cd1-144">在此命令中，我们使用**Get MsolUser** cmdlet 返回有关 BelindaN@litwareinc.com 的帐户信息。一旦我们已经返回该信息，然后管道为**选择对象**cmdlet 的帐户数据，提出要"展开"**许可证**属性的值的**选择对象**：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-144">In this command, we're using the **Get-MsolUser** cmdlet to return information about the account BelindaN@litwareinc.com. Once we've returned that information, we then pipe the account data to the **Select-Object** cmdlet and ask **Select-Object** to "expand" the value of the **Licenses** property:</span></span>
  
 `Select-Object -ExpandProperty Licenses`
  
<span data-ttu-id="a9cd1-p107">这么做的原因？好的默认情况下，**许可证**属性只告诉我们 Belinda 的许可证来自何处的许可包的名称：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p107">Why do we do that? Well, by default the **Licenses** property only tells us the name of the licensing pack where Belinda's license came from:</span></span>
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

<span data-ttu-id="a9cd1-147">"展开"**许可证**属性为我们提供了一些详细信息：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-147">"Expanding" the **Licenses** property gives us a little more information:</span></span>
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

<span data-ttu-id="a9cd1-148">然后通过扩展的**ServiceStatus**属性我们可以得到更多的信息：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-148">And then by expanding the **ServiceStatus** property we can get back even more information:</span></span>
  
|<span data-ttu-id="a9cd1-149">服务计划 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="a9cd1-149">****Service plan****</span></span>|<span data-ttu-id="a9cd1-150">说明 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="a9cd1-150">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="a9cd1-151">Sway</span><span class="sxs-lookup"><span data-stu-id="a9cd1-151">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="a9cd1-152">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a9cd1-152">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="a9cd1-153">Yammer</span><span class="sxs-lookup"><span data-stu-id="a9cd1-153">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="a9cd1-154">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="a9cd1-154">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="a9cd1-155">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="a9cd1-155">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="a9cd1-156">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="a9cd1-156">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="a9cd1-157">Office Online</span><span class="sxs-lookup"><span data-stu-id="a9cd1-157">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="a9cd1-158">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a9cd1-158">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="a9cd1-159">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="a9cd1-159">Exchange Online Plan 2</span></span>  <br/> |
   
> [!NOTE]
> <span data-ttu-id="a9cd1-p108">您说这是太多键入？好吧，如果您可以用很少的 Windows PowerShell obtuseness 拍卖中，您可以运行命令此精简的版本相反： >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p108">You say that's too much typing? Well, if you can put up with a little Windows PowerShell obtuseness, you can run this condensed version of the command instead: >  `(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span></span>
  
<span data-ttu-id="a9cd1-p109">如果您想知道，我们可以"展开"**许可证**属性因为**许可证**是多值的属性： 它是单个属性，可以存储多个值。当我们展开一个属性值，我们只是向下钻取获得下列附加属性值，默认情况下，则不会显示在屏幕上。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p109">In case you're wondering, we can "expand" the **Licenses** property because **Licenses** is a multivalued property: it's a single property that can store multiple values. When we expand a property value we simply drill down to get at these additional values that, by default, are not displayed onscreen.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a9cd1-p110">因此是您是如何知道一个值是多值的属性？嗯，要查找出的问题，请尝试运行与以下类似的命令： > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`>**获取成员**cmdlet 返回信息的对象，然后重试。在这种情况下，属性信息值组成用户帐户对象。这里是说有关**许可证**属性**获取成员**有： > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> 如果有关集合的属性定义说点什么 (在这种情况下， `System.Collections.Generic.List`) 则可以确定要处理的多值属性。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p110">So how are you supposed to know that a value is a multivalued property? Well, to find that out, try running a command similar to this: >  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> The **Get-member** cmdlet returns information about the object itself; in this case, information about the property values that make up a user account object. Here's what **Get-Member** has to say about the **Licenses** property:>  `Licenses Property System.Collections.Generic.List[Microsoft.On...`> If the property definition says something about collections (in this case,  `System.Collections.Generic.List`) then you know you're dealing with a multivalued property.</span></span> 
  
<span data-ttu-id="a9cd1-p111">那么什么？ 所有这是否意味着要回答此问题，让我们首先看另一个**Get MsolUser** cmdlet 返回的信息看：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p111">So what does all this mean? To answer that, let's first take another look at the information returned by the **Get-MsolUser** cmdlet:</span></span>
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

<span data-ttu-id="a9cd1-169">然后，让我们也看一看表，解释这些奇怪命名服务计划的真正代表：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-169">And let's also take a look at a table that explains what these oddly-named service plans really represent:</span></span>
  
|<span data-ttu-id="a9cd1-170">服务计划 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="a9cd1-170">****Service plan****</span></span>|<span data-ttu-id="a9cd1-171">说明 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="a9cd1-171">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="a9cd1-172">Sway</span><span class="sxs-lookup"><span data-stu-id="a9cd1-172">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="a9cd1-173">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a9cd1-173">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="a9cd1-174">Yammer</span><span class="sxs-lookup"><span data-stu-id="a9cd1-174">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="a9cd1-175">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="a9cd1-175">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="a9cd1-176">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="a9cd1-176">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="a9cd1-177">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="a9cd1-177">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="a9cd1-178">Office Online</span><span class="sxs-lookup"><span data-stu-id="a9cd1-178">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="a9cd1-179">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a9cd1-179">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="a9cd1-180">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="a9cd1-180">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="a9cd1-p112">都清楚了吗？ `MCOSTANDARD`是在线业务只是为 Skype 的内部编程名称时`OFFICESUSBCRIPTION`只是 Office Professional Plus 的内部编程名称。它不是最直观明了，但只要您保留此表方便使用 Office 365 提供服务时不会有很多问题。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p112">Got all that?  `MCOSTANDARD` is just an internal programming name for Skype for Business Online, while `OFFICESUSBCRIPTION` is just the internal programming name for Office Professional Plus. It's not the most intuitive thing in the world, but as long as you keep this table handy you won't have many problems when it comes to working with Office 365 services.</span></span>
  
<span data-ttu-id="a9cd1-p113">但等待： 还有更多。当我们[查看许可证和服务与 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)，文章中都学到，如果将**ProvisioningStatus**设置为`Success`则表示，已完全启用服务;例如如果`MCOSTANDARD`设置为`Success`，意味着用户可以访问 Skype 的在线业务。如果将**ProvisioningStatus**设置为`PendingInput`，意味着 Office 365 仍在处理服务请求;但是，用户通常可以登录并访问服务，而该请求完成处理。(`YAMMER_ENTERPRISE`将始终显示为`PendingInput`，但这也没关系:，不会阻止用户登录到 Yammer)。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p113">But wait: there's more. As we learned in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), if the **ProvisioningStatus** is set to `Success` that means that the service has been fully enabled; for example if `MCOSTANDARD` is set to `Success` that means that the user can access Skype for Business Online. If the **ProvisioningStatus** is set to `PendingInput` that means that Office 365 is still processing the service request; however, the user can typically log on and access the service while the request finishes processing. ( `YAMMER_ENTERPRISE` will always be shown as `PendingInput`, but that's OK: that won't stop a user from logging on to Yammer).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="a9cd1-188">用户可以安装并激活新的 Office Professional Plus 安装时`OFFICESUBSCRIPTION`在`PendingInput`状态。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-188">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="a9cd1-189">并且，毫无疑问，是一项服务设置为`Disabled`，意味着讨论的服务的不是向用户提供。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-189">And, needless to say, is a service is set to  `Disabled` that means that the service in question is not available to the user.</span></span>
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a><span data-ttu-id="a9cd1-190">查找用户有权访问特定的 Office 365 PowerShell 服务</span><span class="sxs-lookup"><span data-stu-id="a9cd1-190">Find users that have access to specific Office 365 PowerShell services</span></span>

<span data-ttu-id="a9cd1-p114">在单独的文章中，我们看到了如何使用 Office 365 PowerShell 禁用用户对服务的访问。（如果您错过了这篇文章，请参阅[禁用访问 Office 365 PowerShell 的服务](disable-access-to-services-with-office-365-powershell.md)）。这产生了一个明显的问题： 有什么办法可以确定哪些*用户*(即多个用户) 已启用或禁用的服务？</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p114">In a separate article, we saw how you can use Office 365 PowerShell to disable user access to services. (If you missed that article, see [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). That leads to an obvious question: is there any way to determine which  *users*  (that is, more than one user) have which services enabled or disabled?</span></span>
  
<span data-ttu-id="a9cd1-p115">我们希望有人会问这个问题。为了回答这个问题，让我们回顾一下我们第一次看文章[查看许可证和服务与 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)中我们唯一可用的授权计划的服务的表`litwareinc:ENTERPRISEPACK`:</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p115">We were hoping that someone would ask that. In order to answer that question, let's review the table of services that we first looked at in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) for our only available licensing plan `litwareinc:ENTERPRISEPACK`:</span></span>
  
|<span data-ttu-id="a9cd1-196">服务计划 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="a9cd1-196">****Service plan****</span></span>|<span data-ttu-id="a9cd1-197">说明 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="a9cd1-197">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="a9cd1-198">Sway</span><span class="sxs-lookup"><span data-stu-id="a9cd1-198">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="a9cd1-199">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a9cd1-199">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="a9cd1-200">Yammer</span><span class="sxs-lookup"><span data-stu-id="a9cd1-200">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="a9cd1-201">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="a9cd1-201">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="a9cd1-202">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="a9cd1-202">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="a9cd1-203">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="a9cd1-203">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="a9cd1-204">Office Online</span><span class="sxs-lookup"><span data-stu-id="a9cd1-204">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="a9cd1-205">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a9cd1-205">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="a9cd1-206">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="a9cd1-206">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="a9cd1-p116">您可能还记得，服务计划只是一种产品; 的内部编程名称例如， `OFFICESUBSCRIPTION`，为一个名称，则 Office Professional Plus 的内部编程名称。如果`OFFICESUBSCRIPTION`显示为`SUCCESS`对用户的服务计划，则意味着允许用户访问 Office Professional Plus。如果`EXCHANGE_S_ENTERPRISE`被列为`DISABLED`，意味着用户不能使用 Exchange 联机。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p116">As you might recall, the service plan is nothing more than the internal programming name for a product; for example,  `OFFICESUBSCRIPTION`, to name one, is the internal programming name for Office Professional Plus. If  `OFFICESUBSCRIPTION` shows up as `SUCCESS` on a user's service plan, then that means that the user is allowed to access Office Professional Plus. If `EXCHANGE_S_ENTERPRISE` is listed as `DISABLED` that means the user can't use Exchange Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="a9cd1-210">用户可以安装并激活新的 Office Professional Plus 安装时`OFFICESUBSCRIPTION`在`PendingInput`状态。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-210">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="a9cd1-p117">现在是时间服务的顺序是极其重要的位置。Windows PowerShell 将分配给列表中的每一项的索引号。第一项是 0 下, 一项为 1，依此类推。结果详见下表：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p117">Now is the time where the order in which the services appear is extremely important. Windows PowerShell assigns an index number to each entry in the list. The first entry is 0, the next entry is 1, and so on. The results are explained in the following table:</span></span>
  
|<span data-ttu-id="a9cd1-215">索引号 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="a9cd1-215">****Index number****</span></span>|<span data-ttu-id="a9cd1-216">服务计划 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="a9cd1-216">****Service plan****</span></span>|
|:-----|:-----|
|<span data-ttu-id="a9cd1-217">0</span><span class="sxs-lookup"><span data-stu-id="a9cd1-217">0</span></span>  <br/> | `SWAY` <br/> |
|<span data-ttu-id="a9cd1-218">1</span><span class="sxs-lookup"><span data-stu-id="a9cd1-218">1</span></span>  <br/> | `INTUNE_O365` <br/> |
|<span data-ttu-id="a9cd1-219">2</span><span class="sxs-lookup"><span data-stu-id="a9cd1-219">2</span></span>  <br/> | `YAMMER_ENTERPRISE` <br/> |
|<span data-ttu-id="a9cd1-220">3</span><span class="sxs-lookup"><span data-stu-id="a9cd1-220">3</span></span>  <br/> | `RMS_S_ENTERPRISE` <br/> |
|<span data-ttu-id="a9cd1-221">4</span><span class="sxs-lookup"><span data-stu-id="a9cd1-221">4</span></span>  <br/> | `OFFICESUBSCRIPTION` <br/> |
|<span data-ttu-id="a9cd1-222">5</span><span class="sxs-lookup"><span data-stu-id="a9cd1-222">5</span></span>  <br/> | `MCOSTANDARD` <br/> |
|<span data-ttu-id="a9cd1-223">6</span><span class="sxs-lookup"><span data-stu-id="a9cd1-223">6</span></span>  <br/> | `SHAREPOINTWAC` <br/> |
|<span data-ttu-id="a9cd1-224">7</span><span class="sxs-lookup"><span data-stu-id="a9cd1-224">7</span></span>  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|<span data-ttu-id="a9cd1-225">8</span><span class="sxs-lookup"><span data-stu-id="a9cd1-225">8</span></span>  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
<span data-ttu-id="a9cd1-226">正如您所看到的`SWAY`第一个服务列出，因此，它获取指定索引号是 0。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-226">As you can see,  `SWAY` is the first service listed, so it gets assigned index number 0.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="a9cd1-p118">为什么 0 和 1 的不？这就是编程的事情。编程语言中索引告诉您远一项从数组的开头"偏移"。第一项*为*数组，因此其偏移量为 0 开头。第二项是从一开始的 1 项的数组，因此其偏移量为 1。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p118">Why 0 and not 1? That's a programming thing. In programming languages indices tell you how far an item is "offset" from the beginning of the array. The first item  *is*  the beginning of the array, so its offset is 0. The second item is 1 item from the beginning of the array, so its offset is 1.</span></span>
  
<span data-ttu-id="a9cd1-p119">我们可以试一个示例。假设我们想要的所有授权用户都尚未启用 Exchange 联机列表。要做到这一点，我们可以使用下面的命令：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p119">Let's try an example. Suppose we'd like a list of all the licensed users who have not been enabled for Exchange Online. To do that, we can use the following command:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="a9cd1-p120">不可否认，正是般简单的命令，让我们花点时间来解释它的工作原理。这是实际上分为两部分的命令，并且第一部分非常简单： 我们使用**Get MsolUser** cmdlet 返回我们 Office 365 中的所有用户的集合 （有许可证的和无许可证的）：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p120">Admittedly, that's a cryptic-looking little command, so let's take a minute to explain how it works. This is actually a two-part command, and the first part is very simple: we use the **Get-MsolUser** cmdlet to return a collection of all our Office 365 users (both licensed and unlicensed):</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="a9cd1-p121">然后，这些信息被输送到**位置对象**cmdlet。**位置对象**经历的所有用户帐户并寻找这些帐户符合下列要求：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p121">That information is then piped to the **Where-Object** cmdlet. **Where-Object** goes through all the user accounts and looks for those accounts that meet both of the following criteria:</span></span>
  
- <span data-ttu-id="a9cd1-p122">**IsLicensed**属性等于 ( `-eq`) `True` ( `$true`)。它使我们能够滤出的未经授权的用户。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p122">The **isLicensed** property is equal to ( `-eq`)  `True` ( `$true`). That enables us to weed out the unlicensed users.</span></span>
    
- <span data-ttu-id="a9cd1-p123">**许可证 [0] 的值。ServiceStatus [8]。ProvisioningStatus**属性等于 ( `-eq`) `Disabled`。我们的直接目的，为此笨拙的属性名称的重要部分是：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p123">The value of the **Licenses[0].ServiceStatus[8].ProvisioningStatus** property is equal to ( `-eq`)  `Disabled`. For our immediate purposes, the important part of this unwieldy property name is this:</span></span>
    
     `ServiceStatus[8]`
    
    <span data-ttu-id="a9cd1-p124">`[8]`表示 Exchange 联机索引号。（我们知道，从几分钟前查看表）。如果我们想怎么查找启用 Skype 的在线业务的所有用户？嗯，Skype 业务联机索引号是 5，因此我们将使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p124">The  `[8]` represents the index number for Exchange Online. (We know that from looking at the table a few minutes ago). What if we wanted to find all the users enabled for Skype for Business Online? Well, the index number for Skype for Business Online is 5, so we'd use this syntax:</span></span>
    
     `ServiceStatus[5]`
    
    <span data-ttu-id="a9cd1-247">等等。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-247">Etc., etc.</span></span>
    
    <span data-ttu-id="a9cd1-p125">顺便说一下，`Licenses[0]`表示我们想要看的授权计划。由于我们测试域中只有一个授权计划这不重要得多。但是，假设我们有已从两个不同的许可证计划许可证分配的用户。在这种情况下，`Licenses[0]`则表示第一个授权计划，和`Licenses[1]`则表示第二个的授权计划。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p125">Incidentally,  `Licenses[0]` indicates the licensing plan that we want to look at. Since our test domain only has one licensing plan this doesn't matter much. But suppose we had a user who has been assigned licenses from two different licensing plans. In that case, `Licenses[0]` would represent the first licensing plan, and `Licenses[1]` would represent the second licensing plan.</span></span>
    
    <span data-ttu-id="a9cd1-252">若要查找分配给用户的许可证以及列出它们的顺序，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-252">To find the licenses that are assigned to a user, and the order in which they are listed, run the following command:</span></span>
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

<span data-ttu-id="a9cd1-p126">您看到了所有的工作原理？Office Professional Plus 的索引号是 4;因此，此命令会返回尚未为 Office Professional Plus 启用所有用户的列表：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p126">Do you see how this all works? The index number for Office Professional Plus is 4; therefore, this command returns a list of all the users who have not been enabled for Office Professional Plus:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="a9cd1-p127">并且要是我们想已*启用*Office Professional Plus 的用户的列表？好吧，如果您已启用了然后您**ServiceStatus**将`PendingInput`或`Success`;换句话说，您的**ServiceStatus**将*不*等 ( `-ne`) `Disabled`。这意味着我们所要做的就是采取我们前一个命令和换出`-eq`运算符，用于`-ne`运算符：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p127">And what if we wanted a list of users who have been  *enabled*  for Office Professional Plus? Well, if you've been enabled then your **ServiceStatus** will either be `PendingInput` or `Success`; in other words, your **ServiceStatus** will *not*  equal ( `-ne`)  `Disabled`. That means all we have to do is take our previous command and swap out the  `-eq` operator for the `-ne` operator:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="a9cd1-p128">俗话说离时，代码可能不会赢得很多美妙的比赛。而且，事实告诉他们，该代码可以获取更多 tangled。例如，假设我们想要查找的用户已启用这两种 Skype 的在线业务和 Exchange Online 的：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p128">As the saying goes, that code probably won't win many beauty contests. And, truth be told, the code can get even more tangled. For example, suppose we want to look for users who have been enabled for both Skype for Business Online and Exchange Online:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="a9cd1-p129">但不要担心太多关于如何麻烦，可能看起来： 重要的是，与相对较少的工作，您可以检索此信息。无法获取同样的信息使用 Office 365 管理中心？从理论上讲，可以，但，在实际情况下，则不。若要获取同样的信息使用 Office 365 管理中心将需要查看每个用户的授权信息，一次，一个用户，然后手动跟踪的那些先前已启用*x*和谁没有。它会起作用，但让我们坦白： 如果您有多个 10 或 11 的用户，您不打算这样做。它是太乏味而耗时。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p129">But don't worry too much about how gnarly that might look: the important thing is that, with relatively little effort, you can retrieve this information. Can't you get at this same information using the Office 365 admin center? In theory, yes but, in practical terms, no. To get at this same information using the Office 365 admin center you'd need to look at the licensing information for each user, one user at a time, and then manually keep track of who'd been enabled for  *X*  and who hadn't. That would work, but let's be honest: if you have more than 10 or 11 users, you're not going to do this. It's way too tedious and time-consuming.</span></span>
  
<span data-ttu-id="a9cd1-267">这，当然，这是为什么我们有 Windows PowerShell: Windows PowerShell 有助于节省您从乏味而耗时的任务，例如。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-267">Which, of course, is why we have Windows PowerShell: Windows PowerShell helps save you from tedious and time-consuming tasks such as that.</span></span>
  
<span data-ttu-id="a9cd1-268">当我们解决它时，下面是用于查看服务信息的最终命令：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-268">While we're at it, here's the ultimate command for viewing service information:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[0].ProvisioningStatus}}, @{Name="MDM";Expression={$_.Licenses[0].ServiceStatus[1].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[2].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[3].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[4].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[5].ProvisioningStatus}}, @{Name="OfficeWeb";Expression={$_.Licenses[0].ServiceStatus[6].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[8].ProvisioningStatus}} | ConvertTo-Html > "C:\\My Documents\\Service Info.html"
```

<span data-ttu-id="a9cd1-p130">是的这也非常怪模怪样的命令。但是，它将创建 CSV 文件显示您的所有用户和所有及其服务状态。</span><span class="sxs-lookup"><span data-stu-id="a9cd1-p130">And yes, that's a very crazy-looking command. But it creates a CSV file showing all of your users and all of their service statuses.</span></span>

  
## <a name="see-also"></a><span data-ttu-id="a9cd1-271">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9cd1-271">See also</span></span>
<span data-ttu-id="a9cd1-272"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="a9cd1-272"></span></span>

<span data-ttu-id="a9cd1-273">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-273">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="a9cd1-274">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="a9cd1-274">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a9cd1-275">使用 Office 365 PowerShell 删除和还原用户帐户</span><span class="sxs-lookup"><span data-stu-id="a9cd1-275">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a9cd1-276">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="a9cd1-276">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a9cd1-277">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="a9cd1-277">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a9cd1-278">使用 Office 365 PowerShell 删除用户帐户的许可证</span><span class="sxs-lookup"><span data-stu-id="a9cd1-278">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="a9cd1-279">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="a9cd1-279">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="a9cd1-280">ConvertTo Html</span><span class="sxs-lookup"><span data-stu-id="a9cd1-280">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="a9cd1-281">格式列表</span><span class="sxs-lookup"><span data-stu-id="a9cd1-281">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="a9cd1-282">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a9cd1-282">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="a9cd1-283">选择对象</span><span class="sxs-lookup"><span data-stu-id="a9cd1-283">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="a9cd1-284">Where-Object</span><span class="sxs-lookup"><span data-stu-id="a9cd1-284">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="a9cd1-285">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="a9cd1-285">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]