---
title: "在分配用户许可时，禁用对服务的访问"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "了解如何将许可证分配给用户帐户，并在同一时间使用 Office 365 PowerShell 禁用特定的服务计划。"
ms.openlocfilehash: 96ce12f811ee147a92da6b6928c2f6e3391c9b1f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="e67f6-103">在分配用户许可时，禁用对服务的访问</span><span class="sxs-lookup"><span data-stu-id="e67f6-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="e67f6-104">**摘要：** 了解如何将许可证分配给用户帐户，并在同一时间使用 Office 365 PowerShell 禁用特定的服务计划。</span><span class="sxs-lookup"><span data-stu-id="e67f6-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="e67f6-p101">Office 365 订阅带有单个服务的服务计划。Office 365 管理员经常需要向用户分配许可证时禁用某些计划。与本文中的说明进行操作，您可以禁用特定服务计划使用 PowerShell 的单个用户帐户或多个用户帐户时分配 Office 365 提供许可证。</span><span class="sxs-lookup"><span data-stu-id="e67f6-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e67f6-108">这篇文章基于 Siddhartha Parmar，Microsoft 技术支持升级工程师的工作。</span><span class="sxs-lookup"><span data-stu-id="e67f6-108">This article is based on the work of Siddhartha Parmar, a Microsoft Support Escalation Engineer.</span></span> 
  
## <a name="before-you-begin"></a><span data-ttu-id="e67f6-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="e67f6-109">Before you begin</span></span>

<span data-ttu-id="e67f6-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="e67f6-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="e67f6-112">收集有关订阅和服务计划的信息</span><span class="sxs-lookup"><span data-stu-id="e67f6-112">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="e67f6-113">运行以下命令以查看您当前的订阅：</span><span class="sxs-lookup"><span data-stu-id="e67f6-113">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="e67f6-114">在显示的`Get-MsolAccountSku`命令：</span><span class="sxs-lookup"><span data-stu-id="e67f6-114">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="e67f6-p103">**AccountSkuId**是在您组织的订阅\<单位名称 >:\<订阅 > 格式。\<单位名称 > 是提供当您注册 Office 365 并为您的组织中是唯一的值。\<订阅 > 值是为特定的预订。例如，对于 litwareinc:ENTERPRISEPACK，组织名称是 litwareinc，而订阅名称是 ENTERPRISEPACK (Office 365 企业 E3)。</span><span class="sxs-lookup"><span data-stu-id="e67f6-p103">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="e67f6-119">**ActiveUnits**为您的订阅购买的许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="e67f6-119">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="e67f6-120">**WarningUnits**是在您还没有更新的且 30 天宽限期过后将过期的订阅许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="e67f6-120">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="e67f6-121">**ConsumedUnits**是已指派给订阅的用户许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="e67f6-121">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="e67f6-p104">请注意您的 Office 365 订阅包含您想要授予许可的用户 AccountSkuId。另外，请确保有足够的许可来分配 （减去从**ActiveUnits** **ConsumedUnits** ）。</span><span class="sxs-lookup"><span data-stu-id="e67f6-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="e67f6-124">下一步，运行以下命令可查看有关 Office 365 提供服务计划所提供的所有订阅的详细信息：</span><span class="sxs-lookup"><span data-stu-id="e67f6-124">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="e67f6-125">通过此命令显示，确定您想要禁用时将许可证分配给用户的服务计划。</span><span class="sxs-lookup"><span data-stu-id="e67f6-125">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="e67f6-126">这里是服务计划和其相应的 Office 365 提供服务的部分列表。</span><span class="sxs-lookup"><span data-stu-id="e67f6-126">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="e67f6-127">**服务计划**</span><span class="sxs-lookup"><span data-stu-id="e67f6-127">**Service plan**</span></span>|<span data-ttu-id="e67f6-128">**说明**</span><span class="sxs-lookup"><span data-stu-id="e67f6-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e67f6-129">SWAY</span><span class="sxs-lookup"><span data-stu-id="e67f6-129">SWAY</span></span>  <br/> |<span data-ttu-id="e67f6-130">Sway</span><span class="sxs-lookup"><span data-stu-id="e67f6-130">Sway</span></span>  <br/> |
|<span data-ttu-id="e67f6-131">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="e67f6-131">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="e67f6-132">Office 365 移动设备管理</span><span class="sxs-lookup"><span data-stu-id="e67f6-132">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="e67f6-133">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="e67f6-133">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="e67f6-134">Yammer</span><span class="sxs-lookup"><span data-stu-id="e67f6-134">Yammer</span></span>  <br/> |
|<span data-ttu-id="e67f6-135">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="e67f6-135">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="e67f6-136">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="e67f6-136">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="e67f6-137">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e67f6-137">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="e67f6-138">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="e67f6-138">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="e67f6-139">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="e67f6-139">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="e67f6-140">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="e67f6-140">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="e67f6-141">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="e67f6-141">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="e67f6-142">Office Online</span><span class="sxs-lookup"><span data-stu-id="e67f6-142">Office Online</span></span>  <br/> |
|<span data-ttu-id="e67f6-143">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="e67f6-143">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="e67f6-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e67f6-144">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="e67f6-145">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="e67f6-145">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="e67f6-146">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="e67f6-146">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="e67f6-147">既然您已经有 AccountSkuId 和禁用的服务计划，还可以为单个用户或多个用户的许可证。</span><span class="sxs-lookup"><span data-stu-id="e67f6-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="e67f6-148">为单个用户</span><span class="sxs-lookup"><span data-stu-id="e67f6-148">For a single user</span></span>

<span data-ttu-id="e67f6-p105">对于单个用户，填写用户主要名称的用户帐户、 AccountSkuId，以及服务计划的列表禁用和删除 ' 的说明文字和\<和 > 字符。然后，PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="e67f6-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

<span data-ttu-id="e67f6-151">下面是示例命令块名 belindan@contoso.com，为 contoso:ENTERPRISEPACK 许可证，有关的帐户，若要禁用的服务计划 RMS_S_ENTERPRISE、 SWAY、 INTUNE_O365 和 YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="e67f6-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a><span data-ttu-id="e67f6-152">多个用户</span><span class="sxs-lookup"><span data-stu-id="e67f6-152">For multiple users</span></span>

<span data-ttu-id="e67f6-p106">若要为多个用户执行此管理任务，创建范围内和 UsageLocation 字段包含逗号分隔值 (CSV) 文本文件。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="e67f6-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="e67f6-155">下一步，填写的输入和输出的 CSV 文件、 帐户 SKU ID 和服务计划，若要禁用，列表的位置，然后 PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="e67f6-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="e67f6-156">此 PowerShell 命令块：</span><span class="sxs-lookup"><span data-stu-id="e67f6-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="e67f6-157">显示每个用户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="e67f6-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="e67f6-158">指定自定义每个用户的许可证。</span><span class="sxs-lookup"><span data-stu-id="e67f6-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="e67f6-159">与已处理的所有用户创建 CSV 文件，并显示其许可证状态。</span><span class="sxs-lookup"><span data-stu-id="e67f6-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e67f6-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e67f6-160">See also</span></span>

#### 

[<span data-ttu-id="e67f6-161">使用 Office 365 PowerShell 禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="e67f6-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="e67f6-162">禁止访问与 Office 365 PowerShell 的 Sway</span><span class="sxs-lookup"><span data-stu-id="e67f6-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="e67f6-163">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="e67f6-163">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e67f6-164">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="e67f6-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

