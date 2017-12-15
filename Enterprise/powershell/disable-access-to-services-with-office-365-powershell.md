---
title: "使用 Office 365 PowerShell 禁止访问服务"
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
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "解释如何使用 Office 365 PowerShell 添加或删除组织中用户的 Office 365 提供服务的访问。"
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="ec8ba-103">使用 Office 365 PowerShell 禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="ec8ba-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="ec8ba-104">**摘要：**解释如何使用 Office 365 PowerShell 添加或删除组织中用户的 Office 365 提供服务的访问。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-104">**Summary:** Explains how to use Office 365 PowerShell to add or remove access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="ec8ba-p101">在 Office 365 帐户从授权计划分配许可证，Office 365 提供服务可供用户从该许可证。但是，您可以控制用户可以访问 Office 365 提供服务。例如，即使许可证允许访问 SharePoint Online，您可以禁用对它的访问。事实上，您可以使用 Office 365 PowerShell 禁止任意数量的服务的访问：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>
- <span data-ttu-id="ec8ba-109">单个帐户。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-109">An individual account.</span></span>
    
- <span data-ttu-id="ec8ba-110">一组帐户。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-110">A group of accounts.</span></span>
    
- <span data-ttu-id="ec8ba-111">组织中的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-111">All accounts in your organization.</span></span>
    
 <span data-ttu-id="ec8ba-112">**内容：**[简短的版本 （无需解释的说明）](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[长版 （详细的解释与说明）](disable-access-to-services-with-office-365-powershell.md#LongVersion)[请参见](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span><span class="sxs-lookup"><span data-stu-id="ec8ba-112">**Contents:**[The short version (instructions without explanations)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[The long version (instructions with detailed explanations)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[See also](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="ec8ba-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="ec8ba-113">Before you begin</span></span>
<span data-ttu-id="ec8ba-114"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="ec8ba-114"></span></span>

- <span data-ttu-id="ec8ba-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ec8ba-p103">使用**Get MsolAccountSku** cmdlet 以查看您可用的授权计划，并可在这些计划中的 Office 365 提供服务。有关详细信息，请参阅[查看许可证和 Office 365 PowerShell 的服务](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ec8ba-119">若要查看之前和之后本主题中的过程的结果，请参阅[查看帐户许可证和服务的详细信息与 Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-119">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ec8ba-p104">PowerShell 提供了一个脚本来自动执行本主题中描述的过程。具体来说，脚本允许您查看和您 Office 365 的组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用 Office 365 PowerShell 的 Sway 访问](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ec8ba-123">如果您使用 **Get-MsolUser** cmdlet 而无需使用 _All_ 参数，仅可返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-123">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="ec8ba-124">简版（说明不含解释）</span><span class="sxs-lookup"><span data-stu-id="ec8ba-124">The short version (instructions without explanations)</span></span>
<span data-ttu-id="ec8ba-125"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="ec8ba-125"></span></span>

<span data-ttu-id="ec8ba-p105">此部分介绍的步骤未经任何渲染或过多解释。如果您有任何疑问或想了解更多信息，可以阅读本主题的其余部分。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p105">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="ec8ba-128">要禁用 Office 365 提供服务的用户从单个授权计划，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-128">To disable Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="ec8ba-129">通过使用下面的语法授权计划中确定的令人不快的服务：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-129">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="ec8ba-130">本示例创建一个**LicenseOptions**对象，名为授权计划中禁用 Office Online 和 SharePoint Online 服务`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3)。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-130">This example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="ec8ba-131">对一个或多个用户使用步骤 1 中的**LicenseOptions**对象。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-131">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="ec8ba-132">若要创建一个已禁用服务的新帐户，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-132">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="ec8ba-133">本示例为 Allie Bellew 创建一个新帐户，用来分配许可证和禁用步骤 1 中所述的服务。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-133">This example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="ec8ba-134">有关在 Office 365 PowerShell 创建用户帐户的详细信息，请参阅[Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-134">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="ec8ba-135">若要禁用现有授权用户的服务，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-135">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="ec8ba-136">本示例对用户 BelindaN@litwareinc.com 禁用服务。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-136">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="ec8ba-137">若要禁用所有现有的授权用户在步骤 1 中所描述的服务，指定 Office 365 计划从**Get MsolAccountSku** cmdlet （如**litwareinc:ENTERPRISEPACK** )，显示的名称，然后运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-137">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - <span data-ttu-id="ec8ba-138">若要对一组现有用户禁用服务，请使用下列两种方法之一来确定用户：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-138">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="ec8ba-139">**筛选器基于现有帐户属性的帐户**若要执行此操作，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-139">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="ec8ba-140">本示例对美国销售部门的用户禁用服务。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-140">This example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="ec8ba-141">**使用特定的帐户列表**若要执行此操作，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-141">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="ec8ba-142">创建一个文本文件，在它的每一行上包含一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-142">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    <span data-ttu-id="ec8ba-143">在此示例中，该文本文件是 c:\\我的文档\\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-143">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="ec8ba-144">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-144">Run the following command:</span></span>
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="ec8ba-145">要禁用 Office 365 提供服务的用户，而分配的授权计划，请参阅[禁止访问服务时指派用户许可证](disable-access-to-services-while-assigning-user-licenses.md)。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-145">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
<span data-ttu-id="ec8ba-146">若要禁用用户的 Office 365 提供服务中所有可用的授权计划，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-146">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="ec8ba-147">将此脚本复制并粘贴到记事本。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-147">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="ec8ba-148">为您的环境自定义以下值：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-148">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="ec8ba-149">_<UndesirableService>_在此示例中，我们将使用 Office 联机和 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-149">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="ec8ba-150">_<Account>_在此示例中，我们将使用 belindan@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-150">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="ec8ba-151">自定义的脚本如下所示：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-151">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="ec8ba-p106">保存为脚本`RemoveO365Services.ps1`在易于查找的位置。对于本示例，我们将保存文件" `C:\\O365 Scripts`"。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p106">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in " `C:\\O365 Scripts`".</span></span>
    
4. <span data-ttu-id="ec8ba-154">通过使用下面的命令在 Office 365 PowerShell 运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-154">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="ec8ba-155">若要反转这些过程的影响 (即以重新启用这些禁用的服务)，再次运行该过程，但使用的值`$null` _DisabledPlans_参数。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-155">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value  `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="ec8ba-156">返回页首</span><span class="sxs-lookup"><span data-stu-id="ec8ba-156">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="ec8ba-157">长版（说明附有详细解释）</span><span class="sxs-lookup"><span data-stu-id="ec8ba-157">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="ec8ba-158"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="ec8ba-158"></span></span>

<span data-ttu-id="ec8ba-p107">默认情况下，当您通过使用 Office 365 PowerShell 颁发许可证启用所有服务。通常这就是一件好事： 这意味着，您可以快速而轻松地分配许可证用户而无需指定启用前进路上的每个服务。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p107">By default, all services are enabled when you issue a license by using Office 365 PowerShell. And often that's a good thing: that means that you can quickly and easily assign licenses to users without having to specify that each and every service be enabled along the way.</span></span>
  
<span data-ttu-id="ec8ba-p108">虽然这样说，但是，它也是如此，您可能想要限制可用的服务您的部分用户;例如，也许某些用户能够访问 Office Professional Plus，Skype 在线业务和 Exchange 联机，但那些相同的用户无权访问到 SharePoint Online 或 Office 联机。您可以限制以该方式的帐户？事实证明，也可以。为了帮助说明该方法的原理，让我们处理此问题采取一种两步的方法：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p108">Having said that, however, it's also true that you might want to restrict the services available some of your users; for example, maybe some users should have access to Office Professional Plus, Skype for Business Online, and Exchange Online, but those same users shouldn't have access to SharePoint Online or to Office Online. Can you restrict accounts in that fashion? As it turns out, you can. To help explain how this works, let's take a two-step approach to tackling this problem:</span></span>
  
1. <span data-ttu-id="ec8ba-165">为该用户指派的所有服务将自动都启用 Office 365 提供许可证。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-165">Assign the user an Office 365 license that automatically enables all the services.</span></span>
    
2. <span data-ttu-id="ec8ba-166">运行 Office 365 PowerShell 命令，禁用该用户指定的服务的一对。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-166">Run a pair of Office 365 PowerShell commands that disable specified services for that user.</span></span>
    
<span data-ttu-id="ec8ba-p109">我们已经采取关心的第 1 步： 我们的用户 (Belinda Newman) 已经为她提供了对所有 Office 365 提供服务的访问 Office 365 提供许可证。然而，我们想要修改 Belinda 的帐户，以使她不能访问 SharePoint Online ( `SHAREPOINTENTERPRISE`) 或 Office Online ( `SHAREPOINTWAC`)。但是，我们应如何做到这一点呢？</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p109">We've already taken care of step 1: our user (Belinda Newman) has an Office 365 license that provides her with access to all the Office 365 services. However, we want to modify Belinda's account so that she doesn't have access to SharePoint Online ( `SHAREPOINTENTERPRISE`) or to Office Online ( `SHAREPOINTWAC`). But how are we supposed to do that?</span></span>
  
<span data-ttu-id="ec8ba-p110">下面是如何。开头的我们将使用**新建 MsolLicenseOptions** cmdlet 来创建一个**LicenseOption**对象，该对象包含了我们想要禁用的服务。在 Belinda 的情况下，我们想要禁用`SHAREPOINTENTERPRISE`， `SHAREPOINTWAC`，因此我们使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p110">Here's how. To begin with, we're going to use the **New-MsolLicenseOptions** cmdlet to create a **LicenseOption** object that contains the services that we want disabled. In Belinda's case, we want to disable `SHAREPOINTENTERPRISE` and `SHAREPOINTWAC`, so we use this command:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="ec8ba-p111">看到它的工作原理吗？指定的授权计划 ( `litwareinc:ENTERPRISEPACK`)，然后指明每个禁用的服务所需，用逗号隔开这些服务。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p111">See how that works? You specify the licensing plan ( `litwareinc:ENTERPRISEPACK`) and then indicate each of the services that you want disabled, separating those services by using commas.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ec8ba-p112">请确保将您的新**LicenseOption**对象存储在变量中。在前面的示例中，我们使用`$x`，但您可以使用任何有效的 Windows PowerShell 变量名称。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p112">Make sure you store your new **LicenseOption** object in a variable. In the preceding example, we used `$x`, although you can use any valid Windows PowerShell variable name.</span></span> 
  
<span data-ttu-id="ec8ba-177">此时我们可以使用下面的命令以禁用 Belinda 的对这两项服务的访问权限：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-177">At this point we can use the following command to disable Belinda's access to the two services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="ec8ba-p113">没有什么特别在这里，或者： 我们只是调用**一组 MsolUserLicense** cmdlet 和_LicenseOptions_参数，以及变量包括 ( `$x`) 包含要禁用的计划。然后我们看到了什么现在是否我们看一下 Belinda 的许可证信息通过运行命令： `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`？我们看到：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p113">Nothing too fancy here, either: we just call the **Set-MsolUserLicense** cmdlet and include the _LicenseOptions_ parameter, along with the variable ( `$x`) containing the plans we want to disable. And what do we see now if we take a peek at Belinda's license information by running the command:  `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? We see this:</span></span>
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

<span data-ttu-id="ec8ba-p114">很酷吧？而且，当然，我们可以做同一问题给多个用户如果我们想的话。例如，以下命令禁用为所有许可用户相同的两个服务。指定的名称 （如**litwareinc:ENTERPRISEPACK** )，**获得 MsolAccountSku** cmdlet 的显示 Office 365 计划并运行它们。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p114">Pretty cool, huh? And, of course, we could do this same thing to multiple users if we wanted to. For example, these commands disable the same two services for all our licensed users. Specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run them.</span></span>
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

<span data-ttu-id="ec8ba-p115">请记住 Belinda 仍有有效的 Office 365 许可证;它就是现在，她有权访问更少服务。我们禁用这两项服务之前，Belinda 有新闻、 OneDrive 和 SharePoint 访问联机站点：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p115">Keep in mind that Belinda still has a valid Office 365 license; it's just that now she has access to fewer services. Before we disabled the two services, Belinda had access to newsfeeds, OneDrive, and SharePoint Online sites:</span></span>
  
![具有 SharePoint 访问权限的用户。](images/o365_powershell_with_sharepoint.png)
  
<span data-ttu-id="ec8ba-188">现在这些选项对她不再可用：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-188">Now those options are no longer available to her:</span></span>
  
![没有 SharePoint 访问权限的用户。](images/o365_powershell_without_sharepoint.png)
  
<span data-ttu-id="ec8ba-190">这正是我们希望发生的。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-190">Which is exactly what we hoped would happen.</span></span>
  
<span data-ttu-id="ec8ba-p116">并且如果我们改变我们的主意以后： 是否可以重新启用这些服务？当然可以。要重新启用所有用户的服务，只需使用此命令创建下面的**LicenseOption**对象：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p116">And what if we change our mind later on: is it possible to re-enable these services? You bet it is. To re-enable all the services for a user, just use this command to create the following **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="ec8ba-p117">该命令的作用是什么？以开头的 Windows PowerShell 常数`$null`表示"没有"。（或者，在稍有更多的技术语言，它意味着"空值"。）作为您回想一下，当我们使用**New MsolLicenseOptions** cmdlet 我们必须表示我们想要禁用的服务。在这种情况下，我们不希望任何服务被禁用。它可能会导致您相信我们可以使用如下所示，在其中我们不指定_DisabledPlans_参数的值的命令的命令：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p117">What does that command do? To begin with, the Windows PowerShell constant  `$null` means "nothing." (Or, in slightly-more technical language, it means a "null value.") As you recall, when we use the **New-MsolLicenseOptions** cmdlet we have to indicate the services that we want disabled. In this case, we don't want any of the services to be disabled. That might lead you to believe that we could use a command like the following, a command where we don't specify a value for the _DisabledPlans_ parameter:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

<span data-ttu-id="ec8ba-p118">但是，它将不起作用。相反，则会生成一条错误消息：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p118">However, that won't work. Instead, it generates an error message:</span></span>
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
<span data-ttu-id="ec8ba-201">幸运的是我们，将参数值设置为`$null`可以正常工作：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-201">Fortunately for us, setting the parameter value to  `$null` does work:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="ec8ba-202">这只意味着，当我们运行**一组 MsolUserLicense** cmdlet，我们会告诉**集 MsolUserLicense** ，我们不希望 Belinda 具有任何已禁用的服务：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-202">This simply means that, when we run the **Set-MsolUserLicense** cmdlet, we're telling **Set-MsolUserLicense** that we don't want Belinda to have any disabled services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="ec8ba-203">如果没有禁用任何服务，这必须意味着所有服务都已启用，这很合理。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-203">And, logically enough, if none of the services are disabled that must mean that all of the services are enabled.</span></span>
  
<span data-ttu-id="ec8ba-p119">既然您了解了整个工作原理，让我们向您展示如何颁发许可证并禁用指定的服务，并且都具备相同的命令。听起来非常深刻的印象，但老实说，其实没什么对它： 您只需包括_AddLicenses_和_LicenseOptions_参数在相同的命令。换句话说，您首先创建**LicenseOption**对象：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p119">Now that you understand how this all works, let's show you how you can issue a license and disable specified services, and all with the same command. That sounds pretty impressive, but, to be honest, there's really nothing to it: you just include both the  _AddLicenses_ and the _LicenseOptions_ parameters in the same command. In other words, you first create your **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="ec8ba-207">然后，然后，正如前述，使用_AddLicenses_和_LicenseOptions_参数在您的命令：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-207">And then, as noted previously, you use both the  _AddLicenses_ and the _LicenseOptions_ parameters in your command:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

<span data-ttu-id="ec8ba-208">命令将发出 Belinda Newman 新的许可证，但许可证的 Skype 的在线业务 ( `SHAREPOINTWAC`) 和 SharePoint Online ( `SHAREPOINTENTERPRISE`) 都被禁用。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-208">That command will issue Belinda Newman a new license, but a license in which Skype for Business Online ( `SHAREPOINTWAC`) and SharePoint Online ( `SHAREPOINTENTERPRISE`) are both disabled.</span></span>
  
[<span data-ttu-id="ec8ba-209">返回页首</span><span class="sxs-lookup"><span data-stu-id="ec8ba-209">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a><span data-ttu-id="ec8ba-210">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="ec8ba-210">New to Office 365?</span></span>
<span data-ttu-id="ec8ba-211"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="ec8ba-211"></span></span>

||
|:-----|
|<span data-ttu-id="ec8ba-p120">![LinkedIn 学习的短图标](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 提供指向新建？**        **Office 365 管理员和 IT 专业人员使用**，LinkedIn 学习者发现免费视频课程。</span><span class="sxs-lookup"><span data-stu-id="ec8ba-p120">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="ec8ba-214">See also</span><span class="sxs-lookup"><span data-stu-id="ec8ba-214">See also</span></span>
<span data-ttu-id="ec8ba-215"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="ec8ba-215"></span></span>

<span data-ttu-id="ec8ba-216">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-216">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="ec8ba-217">使用 Office 365 PowerShell 删除和还原用户账户</span><span class="sxs-lookup"><span data-stu-id="ec8ba-217">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ec8ba-218">使用 Office 365 PowerShell 删除和还原用户账户</span><span class="sxs-lookup"><span data-stu-id="ec8ba-218">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ec8ba-219">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="ec8ba-219">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ec8ba-220">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="ec8ba-220">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ec8ba-221">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="ec8ba-221">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="ec8ba-222">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="ec8ba-222">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="ec8ba-223">获取内容</span><span class="sxs-lookup"><span data-stu-id="ec8ba-223">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="ec8ba-224">获得 MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="ec8ba-224">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="ec8ba-225">新 MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="ec8ba-225">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="ec8ba-226">获得 MsolUser</span><span class="sxs-lookup"><span data-stu-id="ec8ba-226">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="ec8ba-227">新 MsolUser</span><span class="sxs-lookup"><span data-stu-id="ec8ba-227">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="ec8ba-228">一组 MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="ec8ba-228">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="ec8ba-229">ForEach 对象</span><span class="sxs-lookup"><span data-stu-id="ec8ba-229">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="ec8ba-230">Where-Object</span><span class="sxs-lookup"><span data-stu-id="ec8ba-230">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[<span data-ttu-id="ec8ba-231">返回页首</span><span class="sxs-lookup"><span data-stu-id="ec8ba-231">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  

