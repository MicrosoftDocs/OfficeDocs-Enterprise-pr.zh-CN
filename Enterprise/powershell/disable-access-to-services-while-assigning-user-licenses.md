---
title: 分配用户许可证时禁用访问服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: 了解如何将许可证分配给用户帐户和使用 Office 365 PowerShell 中的同时禁用特定的服务计划。
ms.openlocfilehash: 40abaa37b5a88eb69b01779894e851068a6454ee
ms.sourcegitcommit: fe406eacd92dd5b3bd8c127b7bd8f2d0ef216404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2018
ms.locfileid: "20017398"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="18275-103">分配用户许可证时禁用访问服务</span><span class="sxs-lookup"><span data-stu-id="18275-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="18275-104">**摘要：** 了解如何将许可证分配给用户帐户和使用 Office 365 PowerShell 中的同时禁用特定的服务计划。</span><span class="sxs-lookup"><span data-stu-id="18275-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="18275-p101">Office 365 订阅附带的个别服务的服务计划。Office 365 管理员通常需要禁用某些计划时向用户分配许可证。使用本文中的说明，您可以禁用特定的服务计划使用 PowerShell 为单个用户帐户或多个用户帐户时分配 Office 365 许可证。</span><span class="sxs-lookup"><span data-stu-id="18275-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="18275-108">准备工作</span><span class="sxs-lookup"><span data-stu-id="18275-108">Before you begin</span></span>

<span data-ttu-id="18275-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="18275-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="18275-111">收集有关订阅和服务计划信息</span><span class="sxs-lookup"><span data-stu-id="18275-111">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="18275-112">运行以下命令以查看您当前的订阅：</span><span class="sxs-lookup"><span data-stu-id="18275-112">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="18275-113">在显示的`Get-MsolAccountSku`命令：</span><span class="sxs-lookup"><span data-stu-id="18275-113">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="18275-p103">**AccountSkuId**是您组织中的订阅\<OrganizationName >:\<订阅 > 格式。\<OrganizationName > 是注册 Office 365 中，为您的组织都是唯一时提供的值。\<订阅 > 值是特定订阅。例如，对于 litwareinc: enterprisepack，组织名称为 litwareinc，并且订阅名称是 ENTERPRISEPACK (Office 365 企业版 E3)。</span><span class="sxs-lookup"><span data-stu-id="18275-p103">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="18275-118">**ActiveUnits**是您已购买订阅的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="18275-118">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="18275-119">**WarningUnits**是，您还未更新的且将过期后 30 天的宽限期订阅中的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="18275-119">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="18275-120">**ConsumedUnits**已分配给订阅的用户的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="18275-120">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="18275-p104">请注意 AccountSkuId 为您的 Office 365 订阅包含您想要许可证的用户。此外，还要确保有足够的许可证分配 （减去从**ActiveUnits** **ConsumedUnits** ）。</span><span class="sxs-lookup"><span data-stu-id="18275-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="18275-123">接下来，运行以下命令以查看有关所有订阅中可用的 Office 365 服务计划的详细信息：</span><span class="sxs-lookup"><span data-stu-id="18275-123">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="18275-124">通过此命令显示，确定想要禁用时向用户分配许可证哪些服务计划。</span><span class="sxs-lookup"><span data-stu-id="18275-124">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="18275-125">下面是服务计划和其相应的 Office 365 服务的部分列表。</span><span class="sxs-lookup"><span data-stu-id="18275-125">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="18275-126">**服务计划**</span><span class="sxs-lookup"><span data-stu-id="18275-126">**Service plan**</span></span>|<span data-ttu-id="18275-127">**说明**</span><span class="sxs-lookup"><span data-stu-id="18275-127">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="18275-128">SWAY</span><span class="sxs-lookup"><span data-stu-id="18275-128">SWAY</span></span>  <br/> |<span data-ttu-id="18275-129">Sway</span><span class="sxs-lookup"><span data-stu-id="18275-129">Sway</span></span>  <br/> |
|<span data-ttu-id="18275-130">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="18275-130">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="18275-131">Office 365 移动设备管理</span><span class="sxs-lookup"><span data-stu-id="18275-131">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="18275-132">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="18275-132">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="18275-133">Yammer</span><span class="sxs-lookup"><span data-stu-id="18275-133">Yammer</span></span>  <br/> |
|<span data-ttu-id="18275-134">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="18275-134">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="18275-135">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="18275-135">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="18275-136">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="18275-136">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="18275-137">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="18275-137">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="18275-138">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="18275-138">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="18275-139">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="18275-139">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="18275-140">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="18275-140">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="18275-141">Office Online</span><span class="sxs-lookup"><span data-stu-id="18275-141">Office Online</span></span>  <br/> |
|<span data-ttu-id="18275-142">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="18275-142">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="18275-143">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="18275-143">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="18275-144">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="18275-144">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="18275-145">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="18275-145">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="18275-146">现在，您有 AccountSkuId 以及禁用的服务计划，您可以分配单个用户或多个用户的许可证。</span><span class="sxs-lookup"><span data-stu-id="18275-146">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="18275-147">为单个用户</span><span class="sxs-lookup"><span data-stu-id="18275-147">For a single user</span></span>

<span data-ttu-id="18275-p105">为单个用户，填写的用户帐户、 AccountSkuId，并禁用和删除的说明性文本服务计划的列表的用户主体名称和\<和 > 字符。然后，在 PowerShell 命令提示符处运行生成命令。</span><span class="sxs-lookup"><span data-stu-id="18275-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
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

<span data-ttu-id="18275-150">下面是用于 contoso:ENTERPRISEPACK 许可证，名为 belindan@contoso.com 的帐户的示例命令块，若要禁用的服务计划 RMS_S_ENTERPRISE、 SWAY、 INTUNE_O365 和 YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="18275-150">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
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

## <a name="for-multiple-users"></a><span data-ttu-id="18275-151">为多个用户</span><span class="sxs-lookup"><span data-stu-id="18275-151">For multiple users</span></span>

<span data-ttu-id="18275-p106">若要执行此管理任务的多个用户，创建包含 UserPrincipalName 和 UsageLocation 字段的逗号分隔值 (CSV) 文本文件。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="18275-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="18275-154">接下来，填写的输入和输出 CSV 文件、 SKU ID 的帐户和服务计划，若要禁用，列表的位置，然后在 PowerShell 命令提示符中运行生成命令。</span><span class="sxs-lookup"><span data-stu-id="18275-154">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="18275-155">此 PowerShell 命令块：</span><span class="sxs-lookup"><span data-stu-id="18275-155">This PowerShell command block:</span></span>
  
- <span data-ttu-id="18275-156">显示每个用户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="18275-156">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="18275-157">分配自定义为每个用户的许可证。</span><span class="sxs-lookup"><span data-stu-id="18275-157">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="18275-158">与已处理的所有用户创建一个 CSV 文件，并显示其许可证状态。</span><span class="sxs-lookup"><span data-stu-id="18275-158">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="18275-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18275-159">See also</span></span>

[<span data-ttu-id="18275-160">使用 Office 365 PowerShell 禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="18275-160">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="18275-161">禁用对 Sway 与 Office 365 PowerShell 访问</span><span class="sxs-lookup"><span data-stu-id="18275-161">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="18275-162">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="18275-162">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="18275-163">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="18275-163">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

