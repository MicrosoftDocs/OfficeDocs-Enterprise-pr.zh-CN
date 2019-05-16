---
title: 在分配用户许可证时禁止访问服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: 了解如何使用 Office 365 PowerShell 将许可证分配给用户帐户并同时禁用特定服务计划。
ms.openlocfilehash: 82a448e4fc7f068fab3b04519b9689506208bee8
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069048"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="a70f1-103">在分配用户许可证时禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="a70f1-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="a70f1-104">**摘要:** 了解如何使用 Office 365 PowerShell 将许可证分配给用户帐户并同时禁用特定服务计划。</span><span class="sxs-lookup"><span data-stu-id="a70f1-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="a70f1-105">Office 365 订阅随附有针对单个服务的服务计划。</span><span class="sxs-lookup"><span data-stu-id="a70f1-105">Office 365 subscriptions come with service plans for individual services.</span></span> <span data-ttu-id="a70f1-106">在向用户分配许可证时, Office 365 管理员通常需要禁用某些计划。</span><span class="sxs-lookup"><span data-stu-id="a70f1-106">Office 365 administrators often need to disable certain plans when assigning licenses to users.</span></span> <span data-ttu-id="a70f1-107">使用本文中的说明, 可以分配 Office 365 许可证, 同时使用 PowerShell 为单个用户帐户或多个用户帐户禁用特定服务计划。</span><span class="sxs-lookup"><span data-stu-id="a70f1-107">With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>


## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a70f1-108">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="a70f1-108">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a70f1-109">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="a70f1-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="a70f1-110">接下来, 运行以下命令查看你的当前订阅:</span><span class="sxs-lookup"><span data-stu-id="a70f1-110">Next, run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="a70f1-111">在显示`Get-MsolAccountSku`命令时:</span><span class="sxs-lookup"><span data-stu-id="a70f1-111">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="a70f1-112">**AccountSkuId**是您的组织在 OrganizationName>: \<\<Subscription> 格式中的一种订阅。</span><span class="sxs-lookup"><span data-stu-id="a70f1-112">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format.</span></span> <span data-ttu-id="a70f1-113">\<OrganizationName> 是您在 Office 365 中注册时提供的值, 并且对于您的组织是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a70f1-113">The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="a70f1-114">\<Subscription> 值适用于特定订阅。</span><span class="sxs-lookup"><span data-stu-id="a70f1-114">The \<Subscription> value is for a specific subscription.</span></span> <span data-ttu-id="a70f1-115">例如, 对于 litwareinc: ENTERPRISEPACK, 组织名称为 litwareinc, 订阅名称为 ENTERPRISEPACK (Office 365 企业版 E3)。</span><span class="sxs-lookup"><span data-stu-id="a70f1-115">For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="a70f1-116">**ActiveUnits**是您为订阅购买的许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="a70f1-116">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="a70f1-117">**WarningUnits**是尚未续订的订阅中的许可证数量, 在30天的宽限期后将过期。</span><span class="sxs-lookup"><span data-stu-id="a70f1-117">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="a70f1-118">**ConsumedUnits**是您为订阅分配给用户的许可证数。</span><span class="sxs-lookup"><span data-stu-id="a70f1-118">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="a70f1-119">请注意包含要许可的用户的 Office 365 订阅的 AccountSkuId。</span><span class="sxs-lookup"><span data-stu-id="a70f1-119">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license.</span></span> <span data-ttu-id="a70f1-120">此外, 请确保有足够的许可证可供分配 (从**ActiveUnits**中减去**ConsumedUnits** )。</span><span class="sxs-lookup"><span data-stu-id="a70f1-120">Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="a70f1-121">接下来, 运行此命令以查看有关所有订阅中可用的 Office 365 服务计划的详细信息:</span><span class="sxs-lookup"><span data-stu-id="a70f1-121">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="a70f1-122">在此命令的显示中, 确定在向用户分配许可证时要禁用的服务计划。</span><span class="sxs-lookup"><span data-stu-id="a70f1-122">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="a70f1-123">下面是服务计划及其对应的 Office 365 服务的部分列表。</span><span class="sxs-lookup"><span data-stu-id="a70f1-123">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="a70f1-124">下表显示了最常用服务的 Office 365 服务计划及其友好名称。</span><span class="sxs-lookup"><span data-stu-id="a70f1-124">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="a70f1-125">服务计划列表可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="a70f1-125">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="a70f1-126">**服务计划**</span><span class="sxs-lookup"><span data-stu-id="a70f1-126">**Service plan**</span></span>|<span data-ttu-id="a70f1-127">**说明**</span><span class="sxs-lookup"><span data-stu-id="a70f1-127">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="a70f1-128">Sway</span><span class="sxs-lookup"><span data-stu-id="a70f1-128">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="a70f1-129">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a70f1-129">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="a70f1-130">Yammer</span><span class="sxs-lookup"><span data-stu-id="a70f1-130">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="a70f1-131">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="a70f1-131">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="a70f1-132">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="a70f1-132">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="a70f1-133">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="a70f1-133">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="a70f1-134">Office Online</span><span class="sxs-lookup"><span data-stu-id="a70f1-134">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="a70f1-135">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a70f1-135">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="a70f1-136">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="a70f1-136">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="a70f1-137">有关许可证计划 (也称为产品名称)、其包含的服务计划及其相应的友好名称的完整列表, 请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="a70f1-137">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="a70f1-138">现在, 您已拥有要禁用的 AccountSkuId 和服务计划, 您可以为单个用户或多个用户分配许可证。</span><span class="sxs-lookup"><span data-stu-id="a70f1-138">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="a70f1-139">对于单个用户</span><span class="sxs-lookup"><span data-stu-id="a70f1-139">For a single user</span></span>

<span data-ttu-id="a70f1-140">对于单个用户, 请填写用户帐户的用户主体名称、AccountSkuId 以及要禁用的服务计划列表, 并删除说明文本和\<和 > 字符。</span><span class="sxs-lookup"><span data-stu-id="a70f1-140">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="a70f1-141">然后, 在 PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="a70f1-141">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
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

<span data-ttu-id="a70f1-142">以下是名为 belindan@contoso.com 的帐户的示例命令块, 用于 contoso: ENTERPRISEPACK 许可证, 要禁用的服务计划包括 RMS_S_ENTERPRISE、SWAY、INTUNE_O365 和 YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="a70f1-142">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
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

### <a name="for-multiple-users"></a><span data-ttu-id="a70f1-143">为多个用户</span><span class="sxs-lookup"><span data-stu-id="a70f1-143">For multiple users</span></span>

<span data-ttu-id="a70f1-144">若要对多个用户执行此管理任务, 请创建一个逗号分隔值 (CSV) 文本文件, 该文件包含 UserPrincipalName 和 UsageLocation 字段。</span><span class="sxs-lookup"><span data-stu-id="a70f1-144">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields.</span></span> <span data-ttu-id="a70f1-145">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a70f1-145">Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="a70f1-146">接下来, 填写输入和输出 CSV 文件的位置、帐户 SKU ID 和要禁用的服务计划的列表, 然后在 PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="a70f1-146">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
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

<span data-ttu-id="a70f1-147">此 PowerShell 命令块:</span><span class="sxs-lookup"><span data-stu-id="a70f1-147">This PowerShell command block:</span></span>
  
- <span data-ttu-id="a70f1-148">显示每个用户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="a70f1-148">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="a70f1-149">将自定义许可证分配给每个用户。</span><span class="sxs-lookup"><span data-stu-id="a70f1-149">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="a70f1-150">创建一个 CSV 文件, 其中包含已处理的所有用户, 并显示其许可证状态。</span><span class="sxs-lookup"><span data-stu-id="a70f1-150">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a70f1-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a70f1-151">See also</span></span>

[<span data-ttu-id="a70f1-152">使用 Office 365 PowerShell 禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="a70f1-152">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="a70f1-153">使用 Office 365 PowerShell 禁止访问 Sway</span><span class="sxs-lookup"><span data-stu-id="a70f1-153">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="a70f1-154">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="a70f1-154">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="a70f1-155">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="a70f1-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

