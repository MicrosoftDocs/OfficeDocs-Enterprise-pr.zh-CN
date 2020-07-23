---
title: 在分配用户许可证时禁用对 Microsoft 365 服务的访问
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: 了解如何使用 PowerShell for Microsoft 365 将许可证分配给用户帐户并同时禁用特定服务计划。
ms.openlocfilehash: 31199fa2fa61ec5da671da5def2bf648a07e7dd4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230688"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a><span data-ttu-id="55d7b-103">在分配用户许可证时禁用对 Microsoft 365 服务的访问</span><span class="sxs-lookup"><span data-stu-id="55d7b-103">Disable access to Microsoft 365 services while assigning user licenses</span></span>

<span data-ttu-id="55d7b-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="55d7b-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="55d7b-105">Microsoft 365 订阅随附有针对单个服务的服务计划。</span><span class="sxs-lookup"><span data-stu-id="55d7b-105">Microsoft 365 subscriptions come with service plans for individual services.</span></span> <span data-ttu-id="55d7b-106">Microsoft 365 管理员通常需要在向用户分配许可证时禁用某些计划。</span><span class="sxs-lookup"><span data-stu-id="55d7b-106">Microsoft 365 administrators often need to disable certain plans when assigning licenses to users.</span></span> <span data-ttu-id="55d7b-107">使用本文中的说明，可以分配 Microsoft 365 许可证，同时使用 PowerShell 为单个用户帐户或多个用户帐户禁用特定服务计划。</span><span class="sxs-lookup"><span data-stu-id="55d7b-107">With the instructions in this article, you can assign a Microsoft 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="55d7b-108">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="55d7b-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="55d7b-109">首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="55d7b-109">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="55d7b-110">接下来，使用此命令列出租户的许可证计划。</span><span class="sxs-lookup"><span data-stu-id="55d7b-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="55d7b-111">接下来，获取要向其添加许可证（也称为用户主体名称（UPN））的帐户的登录名。</span><span class="sxs-lookup"><span data-stu-id="55d7b-111">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="55d7b-112">接下来，编译要启用的服务的列表。</span><span class="sxs-lookup"><span data-stu-id="55d7b-112">Next, compile a list of services to enable.</span></span> <span data-ttu-id="55d7b-113">有关许可证计划（也称为产品名称）、其包含的服务计划及其相应的友好名称的完整列表，请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="55d7b-113">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="55d7b-114">对于下面的命令块，请填写用户帐户的用户主体名称、SKU 部件号以及用于启用和删除说明文本和字符的服务计划列表 \< and > 。</span><span class="sxs-lookup"><span data-stu-id="55d7b-114">For the command block below, fill in the user principal name of the user account, the SKU part number, and the list of service plans to enable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="55d7b-115">然后，在 PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="55d7b-115">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="55d7b-116">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="55d7b-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="55d7b-117">首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="55d7b-117">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="55d7b-118">接下来，运行以下命令查看你的当前订阅：</span><span class="sxs-lookup"><span data-stu-id="55d7b-118">Next, run this command to see your current subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="55d7b-119">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="55d7b-119">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="55d7b-120">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="55d7b-120">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="55d7b-121">在显示 `Get-MsolAccountSku` 命令时：</span><span class="sxs-lookup"><span data-stu-id="55d7b-121">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="55d7b-122">**AccountSkuId**是您的组织的订阅 \<OrganizationName> ： \<Subscription> 格式。</span><span class="sxs-lookup"><span data-stu-id="55d7b-122">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format.</span></span> <span data-ttu-id="55d7b-123">是您在 \<OrganizationName> Microsoft 365 中注册时提供的值，并且对于您的组织是唯一的。</span><span class="sxs-lookup"><span data-stu-id="55d7b-123">The \<OrganizationName> is the value that you provided when you enrolled in Microsoft 365, and is unique for your organization.</span></span> <span data-ttu-id="55d7b-124">\<Subscription>该值是针对特定订阅的。</span><span class="sxs-lookup"><span data-stu-id="55d7b-124">The \<Subscription> value is for a specific subscription.</span></span> <span data-ttu-id="55d7b-125">例如，对于 litwareinc： ENTERPRISEPACK，组织名称为 litwareinc，订阅名称为 ENTERPRISEPACK （Office 365 企业版 E3）。</span><span class="sxs-lookup"><span data-stu-id="55d7b-125">For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="55d7b-126">**ActiveUnits**是您为订阅购买的许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="55d7b-126">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="55d7b-127">**WarningUnits**是尚未续订的订阅中的许可证数量，在30天的宽限期后将过期。</span><span class="sxs-lookup"><span data-stu-id="55d7b-127">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="55d7b-128">**ConsumedUnits**是您为订阅分配给用户的许可证数。</span><span class="sxs-lookup"><span data-stu-id="55d7b-128">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="55d7b-129">记下 Microsoft 365 订阅的 AccountSkuId，其中包含要许可的用户。</span><span class="sxs-lookup"><span data-stu-id="55d7b-129">Note the AccountSkuId for your Microsoft 365 subscription that contains the users you want to license.</span></span> <span data-ttu-id="55d7b-130">此外，请确保有足够的许可证可供分配（从**ActiveUnits**中减去**ConsumedUnits** ）。</span><span class="sxs-lookup"><span data-stu-id="55d7b-130">Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="55d7b-131">接下来，运行此命令以查看有关所有订阅中可用的 Microsoft 365 服务计划的详细信息：</span><span class="sxs-lookup"><span data-stu-id="55d7b-131">Next, run this command to see the details about the Microsoft 365 service plans that are available in all your subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="55d7b-132">在此命令的显示中，确定在向用户分配许可证时要禁用的服务计划。</span><span class="sxs-lookup"><span data-stu-id="55d7b-132">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="55d7b-133">下面是服务计划及其对应的 Microsoft 365 服务的部分列表。</span><span class="sxs-lookup"><span data-stu-id="55d7b-133">Here is a partial list of service plans and their corresponding Microsoft 365 services.</span></span>

<span data-ttu-id="55d7b-134">下表显示了最常用服务的 Microsoft 365 服务计划及其友好名称。</span><span class="sxs-lookup"><span data-stu-id="55d7b-134">The following table shows the Microsoft 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="55d7b-135">服务计划列表可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="55d7b-135">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="55d7b-136">**服务计划**</span><span class="sxs-lookup"><span data-stu-id="55d7b-136">**Service plan**</span></span>|<span data-ttu-id="55d7b-137">**描述**</span><span class="sxs-lookup"><span data-stu-id="55d7b-137">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="55d7b-138">Sway</span><span class="sxs-lookup"><span data-stu-id="55d7b-138">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="55d7b-139">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="55d7b-139">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="55d7b-140">Yammer</span><span class="sxs-lookup"><span data-stu-id="55d7b-140">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="55d7b-141">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="55d7b-141">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="55d7b-142">适用于企业的 Microsoft 365 应用程序 *（以前称为 Office 365 专业增强版）*</span><span class="sxs-lookup"><span data-stu-id="55d7b-142">Microsoft 365 Apps for enterprise *(previously named Office 365 ProPlus)*</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="55d7b-143">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="55d7b-143">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="55d7b-144">Office</span><span class="sxs-lookup"><span data-stu-id="55d7b-144">Office</span></span>   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="55d7b-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="55d7b-145">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="55d7b-146">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="55d7b-146">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="55d7b-147">有关许可证计划（也称为产品名称）、其包含的服务计划及其相应的友好名称的完整列表，请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="55d7b-147">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="55d7b-148">现在，您已拥有要禁用的 AccountSkuId 和服务计划，您可以为单个用户或多个用户分配许可证。</span><span class="sxs-lookup"><span data-stu-id="55d7b-148">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="55d7b-149">对于单个用户</span><span class="sxs-lookup"><span data-stu-id="55d7b-149">For a single user</span></span>

<span data-ttu-id="55d7b-150">对于单个用户，请填写用户帐户的用户主体名称、AccountSkuId 以及要禁用的服务计划的列表，并删除说明文本和 \< and > 字符。</span><span class="sxs-lookup"><span data-stu-id="55d7b-150">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="55d7b-151">然后，在 PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="55d7b-151">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

<span data-ttu-id="55d7b-152">以下是名为 belindan@contoso.com 的帐户的示例命令块，用于 contoso： ENTERPRISEPACK 许可证，要禁用的服务计划包括 RMS_S_ENTERPRISE、SWAY、INTUNE_O365 和 YAMMER_ENTERPRISE：</span><span class="sxs-lookup"><span data-stu-id="55d7b-152">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a><span data-ttu-id="55d7b-153">为多个用户</span><span class="sxs-lookup"><span data-stu-id="55d7b-153">For multiple users</span></span>

<span data-ttu-id="55d7b-154">若要对多个用户执行此管理任务，请创建一个逗号分隔值（CSV）文本文件，该文件包含 UserPrincipalName 和 UsageLocation 字段。</span><span class="sxs-lookup"><span data-stu-id="55d7b-154">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields.</span></span> <span data-ttu-id="55d7b-155">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="55d7b-155">Here is an example:</span></span>
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="55d7b-156">接下来，填写输入和输出 CSV 文件的位置、帐户 SKU ID 和要禁用的服务计划的列表，然后在 PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="55d7b-156">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="55d7b-157">此 PowerShell 命令块：</span><span class="sxs-lookup"><span data-stu-id="55d7b-157">This PowerShell command block:</span></span>
  
- <span data-ttu-id="55d7b-158">显示每个用户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="55d7b-158">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="55d7b-159">将自定义许可证分配给每个用户。</span><span class="sxs-lookup"><span data-stu-id="55d7b-159">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="55d7b-160">创建一个 CSV 文件，其中包含已处理的所有用户，并显示其许可证状态。</span><span class="sxs-lookup"><span data-stu-id="55d7b-160">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="55d7b-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55d7b-161">See also</span></span>

[<span data-ttu-id="55d7b-162">使用 PowerShell 禁用对 Microsoft 365 服务的访问</span><span class="sxs-lookup"><span data-stu-id="55d7b-162">Disable access to Microsoft 365 services with PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="55d7b-163">使用 PowerShell 禁用对 Sway 的访问</span><span class="sxs-lookup"><span data-stu-id="55d7b-163">Disable access to Sway with PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="55d7b-164">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="55d7b-164">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="55d7b-165">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="55d7b-165">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
