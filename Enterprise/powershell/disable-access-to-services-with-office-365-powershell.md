---
title: "使用 Office 365 PowerShell 禁止访问服务"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "解释如何使用 Office 365 PowerShell 禁用 Office 365 提供服务，为您的组织中的用户访问。"
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="ea9b4-103">使用 Office 365 PowerShell 禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="ea9b4-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="ea9b4-104">**摘要：**解释如何使用 Office 365 PowerShell 禁用 Office 365 提供服务，为您的组织中的用户访问。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="ea9b4-p101">在 Office 365 帐户从授权计划分配许可证，Office 365 提供服务可供用户从该许可证。但是，您可以控制用户可以访问 Office 365 提供服务。例如，即使许可证允许访问 SharePoint Online，您可以禁用对它的访问。事实上，您可以使用 Office 365 PowerShell 禁止任意数量的服务的访问：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>

- <span data-ttu-id="ea9b4-109">单个帐户。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-109">An individual account.</span></span>
    
- <span data-ttu-id="ea9b4-110">一组帐户。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-110">A group of accounts.</span></span>
    
- <span data-ttu-id="ea9b4-111">组织中的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="ea9b4-112">准备工作</span><span class="sxs-lookup"><span data-stu-id="ea9b4-112">Before you begin</span></span>
<span data-ttu-id="ea9b4-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="ea9b4-113"></span></span>

- <span data-ttu-id="ea9b4-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ea9b4-p103">使用**Get MsolAccountSku** cmdlet 以查看您可用的授权计划，并可在这些计划中的 Office 365 提供服务。有关详细信息，请参阅[查看许可证和 Office 365 PowerShell 的服务](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ea9b4-118">若要查看之前和之后本主题中的过程的结果，请参阅[查看帐户许可证和服务的详细信息与 Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ea9b4-p104">PowerShell 提供了一个脚本来自动执行本主题中描述的过程。具体来说，脚本允许您查看和您 Office 365 的组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用 Office 365 PowerShell 的 Sway 访问](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ea9b4-122">如果您不使用的_所有_参数使用**Get MsolUser** cmdlet，只有第一个 500 用户帐户返回。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a><span data-ttu-id="ea9b4-123">单个授权计划的特定用户的的特定 Office 365 提供服务</span><span class="sxs-lookup"><span data-stu-id="ea9b4-123">Specific Office 365 services for specific users for a single licensing plan</span></span>
  
<span data-ttu-id="ea9b4-124">要禁用一组特定的用户从单个授权计划的 Office 365 提供服务，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-124">To disable a specific set of Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="ea9b4-125">通过使用下面的语法授权计划中确定的令人不快的服务：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="ea9b4-126">下面的示例创建一个**LicenseOptions**对象，名为授权计划中禁用 Office Online 和 SharePoint Online 服务`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3)。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="ea9b4-127">对一个或多个用户使用步骤 1 中的**LicenseOptions**对象。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="ea9b4-128">若要创建一个已禁用服务的新帐户，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="ea9b4-129">下面的示例创建一个新帐户的 Allie Bellew 分配许可证和禁用在步骤 1 中所描述的服务。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="ea9b4-130">有关在 Office 365 PowerShell 创建用户帐户的详细信息，请参阅[Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="ea9b4-131">若要禁用现有授权用户的服务，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="ea9b4-132">本示例对用户 BelindaN@litwareinc.com 禁用服务。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="ea9b4-133">若要禁用所有现有的授权用户在步骤 1 中所描述的服务，指定 Office 365 计划从**Get MsolAccountSku** cmdlet （如**litwareinc:ENTERPRISEPACK**)，显示的名称，然后运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="ea9b4-134">若要对一组现有用户禁用服务，请使用下列两种方法之一来确定用户：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="ea9b4-135">**筛选器基于现有帐户属性的帐户**若要执行此操作，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="ea9b4-136">下面的示例禁用在美国销售部门中的用户服务。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="ea9b4-137">**使用特定的帐户列表**若要执行此操作，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="ea9b4-138">创建一个文本文件，在它的每一行上包含一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="ea9b4-139">在此示例中，该文本文件是 c:\\我的文档\\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="ea9b4-140">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="ea9b4-141">要禁用 Office 365 提供服务的用户，而分配的授权计划，请参阅[禁止访问服务时指派用户许可证](disable-access-to-services-while-assigning-user-licenses.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a><span data-ttu-id="ea9b4-142">用户能够从所有的授权计划的特定 Office 365 提供服务</span><span class="sxs-lookup"><span data-stu-id="ea9b4-142">Specific Office 365 services for users from all licensing plans</span></span>
  
<span data-ttu-id="ea9b4-143">若要禁用用户的 Office 365 提供服务中所有可用的授权计划，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-143">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="ea9b4-144">将此脚本复制并粘贴到记事本。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-144">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="ea9b4-145">为您的环境自定义以下值：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-145">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="ea9b4-146">_<UndesirableService>_在此示例中，我们将使用 Office 联机和 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-146">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="ea9b4-147">_<Account>_在此示例中，我们将使用 belindan@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-147">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="ea9b4-148">自定义的脚本如下所示：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-148">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="ea9b4-p105">保存为脚本`RemoveO365Services.ps1`在易于查找的位置。对于本示例，我们将保存文件`C:\\O365 Scripts`。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-p105">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in `C:\\O365 Scripts`.</span></span>
    
4. <span data-ttu-id="ea9b4-151">通过使用下面的命令在 Office 365 PowerShell 运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-151">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="ea9b4-152">若要反转这些过程的影响 (即以重新启用这些禁用的服务)，再次运行该过程，但使用的值`$null` _DisabledPlans_参数。</span><span class="sxs-lookup"><span data-stu-id="ea9b4-152">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="ea9b4-153">返回页首</span><span class="sxs-lookup"><span data-stu-id="ea9b4-153">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a><span data-ttu-id="ea9b4-154">所有 Office 365 提供服务的所有用户的单个许可计划</span><span class="sxs-lookup"><span data-stu-id="ea9b4-154">All Office 365 services for all users for a single licensing plan</span></span>
 
<span data-ttu-id="ea9b4-155">若要禁用所有 Office 365 提供服务的所有用户在某一特定的授权计划，授权计划为指定的名称 （如**litwareinc:ENTERPRISEPACK**)，$acctSKU，然后 PowerShell 命令窗口中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-155">To disable all Office 365 services for all users in a specific licensing plan, specify the licensing plan name for $acctSKU (such as **litwareinc:ENTERPRISEPACK**), and then run these commands in the PowerShell command window:</span></span>

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a><span data-ttu-id="ea9b4-156">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="ea9b4-156">New to Office 365?</span></span>
<span data-ttu-id="ea9b4-157"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="ea9b4-157"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="ea9b4-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea9b4-158">See also</span></span>
<span data-ttu-id="ea9b4-159"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="ea9b4-159"></span></span>

<span data-ttu-id="ea9b4-160">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-160">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="ea9b4-161">使用 Office 365 PowerShell 删除和还原用户账户</span><span class="sxs-lookup"><span data-stu-id="ea9b4-161">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ea9b4-162">使用 Office 365 PowerShell 删除和还原用户帐户</span><span class="sxs-lookup"><span data-stu-id="ea9b4-162">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ea9b4-163">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="ea9b4-163">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ea9b4-164">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="ea9b4-164">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ea9b4-165">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="ea9b4-165">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="ea9b4-166">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="ea9b4-166">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="ea9b4-167">获取内容</span><span class="sxs-lookup"><span data-stu-id="ea9b4-167">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="ea9b4-168">获得 MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="ea9b4-168">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="ea9b4-169">新 MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="ea9b4-169">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="ea9b4-170">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="ea9b4-170">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="ea9b4-171">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="ea9b4-171">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="ea9b4-172">一组 MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="ea9b4-172">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="ea9b4-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="ea9b4-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="ea9b4-174">Where-Object</span><span class="sxs-lookup"><span data-stu-id="ea9b4-174">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

