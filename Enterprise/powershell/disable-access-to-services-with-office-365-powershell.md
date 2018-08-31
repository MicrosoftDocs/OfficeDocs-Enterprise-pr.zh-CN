---
title: 使用 Office 365 PowerShell 禁止访问服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/20/2018
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
description: 介绍如何使用 Office 365 PowerShell 中禁用对 Office 365 服务的组织中用户的访问。
ms.openlocfilehash: d65308746ac5c2b60f4749588455fa66471069e3
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914987"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="93f7e-103">使用 Office 365 PowerShell 禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="93f7e-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="93f7e-104">**摘要：** 介绍如何使用 Office 365 PowerShell 中禁用对 Office 365 服务的组织中用户的访问。</span><span class="sxs-lookup"><span data-stu-id="93f7e-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="93f7e-p101">在 Office 365 帐户分配许可证从许可计划时，Office 365 服务可供用户从该许可证。但是，您可以控制用户可以访问 Office 365 服务。例如，即使许可证允许访问 SharePoint Online 服务，您可以禁用对其进行访问。您可以使用 Office 365 PowerShell 中禁用对任意数量的特定许可计划为服务的访问权限：</span><span class="sxs-lookup"><span data-stu-id="93f7e-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to the SharePoint Online service, you can disable access to it. You can use Office 365 PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="93f7e-109">单个帐户。</span><span class="sxs-lookup"><span data-stu-id="93f7e-109">An individual account.</span></span>
    
- <span data-ttu-id="93f7e-110">一组帐户。</span><span class="sxs-lookup"><span data-stu-id="93f7e-110">A group of accounts.</span></span>
    
- <span data-ttu-id="93f7e-111">组织中的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="93f7e-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="93f7e-112">准备工作</span><span class="sxs-lookup"><span data-stu-id="93f7e-112">Before you begin</span></span>
<span data-ttu-id="93f7e-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="93f7e-113"></span></span>

- <span data-ttu-id="93f7e-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="93f7e-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93f7e-p103">使用**Get-msolaccountsku** cmdlet 可以查看您可用的许可计划，以及这些计划中可用的 Office 365 服务。有关详细信息，请参阅[查看许可证和身份验证服务与 Office 365 PowerShell 中](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="93f7e-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93f7e-118">若要查看之前和之后的此主题中的过程的结果，请参阅[查看帐户许可证和服务的详细信息与 Office 365 PowerShell 中](view-account-license-and-service-details-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="93f7e-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93f7e-p104">PowerShell 脚本是可用的自动执行本主题中所述的过程。具体而言，该脚本，可以查看和 Office 365 组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用对 Sway 与 Office 365 PowerShell 中的访问](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="93f7e-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="93f7e-122">如果不使用的_所有_参数的情况下使用**Get-msoluser** cmdlet，则返回仅的第一个 500 的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="93f7e-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="93f7e-123">禁用特定的 Office 365 服务的特定用户特定的许可计划</span><span class="sxs-lookup"><span data-stu-id="93f7e-123">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="93f7e-124">若要禁用一组特定的 Office 365 服务的用户特定的许可计划，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="93f7e-124">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="93f7e-125">许可计划中的不需要的服务标识使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="93f7e-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="93f7e-126">下面的示例创建一个名为许可计划中禁用的 Office Online 和 SharePoint Online 服务的**LicenseOptions**对象`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3)。</span><span class="sxs-lookup"><span data-stu-id="93f7e-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="93f7e-127">将步骤 1 中的 **LicenseOptions** 对象用于一个或多个用户。</span><span class="sxs-lookup"><span data-stu-id="93f7e-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="93f7e-128">若要创建一个已禁用服务的新帐户，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="93f7e-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="93f7e-129">下面的示例创建新帐户的 Allie Bellew 分配许可证和禁用在步骤 1 中所描述的服务。</span><span class="sxs-lookup"><span data-stu-id="93f7e-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="93f7e-130">有关 Office 365 PowerShell 中创建用户帐户的详细信息，请参阅[使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="93f7e-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="93f7e-131">若要禁用现有授权用户的服务，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="93f7e-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="93f7e-132">本示例对用户 BelindaN@litwareinc.com 禁用服务。</span><span class="sxs-lookup"><span data-stu-id="93f7e-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="93f7e-133">若要禁用所有现有的授权用户在步骤 1 中所描述的服务，请指定从的**Get-msolaccountsku** cmdlet （如**litwareinc: enterprisepack**)，显示在 Office 365 计划的名称，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="93f7e-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="93f7e-134">若要对一组现有用户禁用服务，请使用下列两种方法之一来确定用户：</span><span class="sxs-lookup"><span data-stu-id="93f7e-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="93f7e-135">**筛选器基于现有帐户属性的帐户**若要执行此操作，使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="93f7e-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="93f7e-136">以下示例禁止在美国销售部门中的用户的服务。</span><span class="sxs-lookup"><span data-stu-id="93f7e-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="93f7e-137">**使用特定帐户的列表**若要执行此操作，执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="93f7e-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="93f7e-138">创建一个文本文件，在它的每一行上包含一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="93f7e-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="93f7e-139">此示例中，在文本文件是 c:\\My Documents\\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="93f7e-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="93f7e-140">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="93f7e-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="93f7e-141">如果您想要禁用访问服务的多个许可计划，对每个许可计划，确保重复上述说明：</span><span class="sxs-lookup"><span data-stu-id="93f7e-141">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="93f7e-142">许可计划已分配的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="93f7e-142">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="93f7e-143">若要禁用的服务是许可计划中可用。</span><span class="sxs-lookup"><span data-stu-id="93f7e-143">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="93f7e-144">若要禁用 Office 365 服务的用户，而您要将其分配给许可计划，请参阅[禁用访问时分配用户许可证的服务](disable-access-to-services-while-assigning-user-licenses.md)。</span><span class="sxs-lookup"><span data-stu-id="93f7e-144">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="93f7e-145">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="93f7e-145">New to Office 365?</span></span>
<span data-ttu-id="93f7e-146"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="93f7e-146"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="93f7e-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93f7e-147">See also</span></span>
<span data-ttu-id="93f7e-148"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="93f7e-148"></span></span>

<span data-ttu-id="93f7e-149">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="93f7e-149">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="93f7e-150">使用 Office 365 PowerShell 删除和还原用户账户</span><span class="sxs-lookup"><span data-stu-id="93f7e-150">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93f7e-151">使用 Office 365 PowerShell 删除和还原用户账户</span><span class="sxs-lookup"><span data-stu-id="93f7e-151">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93f7e-152">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="93f7e-152">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93f7e-153">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="93f7e-153">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="93f7e-154">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="93f7e-154">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="93f7e-155">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="93f7e-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="93f7e-156">获取内容</span><span class="sxs-lookup"><span data-stu-id="93f7e-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="93f7e-157">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="93f7e-157">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="93f7e-158">新 MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="93f7e-158">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="93f7e-159">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="93f7e-159">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="93f7e-160">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="93f7e-160">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="93f7e-161">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="93f7e-161">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="93f7e-162">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="93f7e-162">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="93f7e-163">Where-Object</span><span class="sxs-lookup"><span data-stu-id="93f7e-163">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

