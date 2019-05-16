---
title: 使用 Office 365 PowerShell 查看许可证和服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: 说明如何使用 Office 365 PowerShell 查看有关 Office 365 组织中可用的许可计划、服务和许可证的信息。
ms.openlocfilehash: 9e84797de29337d9414d9a578a98f6799ee816cb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071088"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="23d45-103">使用 Office 365 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="23d45-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="23d45-104">**摘要:** 说明如何使用 Office 365 PowerShell 查看有关 Office 365 组织中可用的许可计划、服务和许可证的信息。</span><span class="sxs-lookup"><span data-stu-id="23d45-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="23d45-105">每个 Office 365 订阅都包含以下元素:</span><span class="sxs-lookup"><span data-stu-id="23d45-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="23d45-106">**许可计划**这些计划也称为许可证计划或 Office 365 计划。</span><span class="sxs-lookup"><span data-stu-id="23d45-106">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="23d45-107">许可计划定义可供用户使用的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="23d45-107">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="23d45-108">您的 Office 365 订阅可能包含多个许可计划。</span><span class="sxs-lookup"><span data-stu-id="23d45-108">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="23d45-109">Office 365 企业版 E3 是许可计划的一个示例。</span><span class="sxs-lookup"><span data-stu-id="23d45-109">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="23d45-110">**服务**这些也称为服务计划。</span><span class="sxs-lookup"><span data-stu-id="23d45-110">**Services** These are also known as service plans.</span></span> <span data-ttu-id="23d45-111">服务是在每个许可计划中可用的 Office 365 产品、功能和功能, 例如 Exchange Online 和 Office Professional Plus。</span><span class="sxs-lookup"><span data-stu-id="23d45-111">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus.</span></span> <span data-ttu-id="23d45-112">可以从授予不同服务访问权限的不同许可计划向用户分配多个许可证。</span><span class="sxs-lookup"><span data-stu-id="23d45-112">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="23d45-113">**许可证**每个许可计划包含您购买的许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="23d45-113">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="23d45-114">您将许可证分配给用户, 以便他们可以使用由许可计划定义的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="23d45-114">You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="23d45-115">每个用户帐户都需要一个许可计划中的至少一个许可证, 以便他们可以登录 Office 365 并使用服务。</span><span class="sxs-lookup"><span data-stu-id="23d45-115">Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="23d45-116">您可以使用 Office 365 PowerShell 来查看有关 Office 365 组织中可用的许可计划、许可证和服务的详细信息。</span><span class="sxs-lookup"><span data-stu-id="23d45-116">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization.</span></span> <span data-ttu-id="23d45-117">有关在不同的 Office 365 订阅中提供的产品、功能和服务的详细信息, 请参阅[Office 365 计划选项](https://go.microsoft.com/fwlink/p/?LinkId=691147)。</span><span class="sxs-lookup"><span data-stu-id="23d45-117">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="23d45-118">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="23d45-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="23d45-119">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="23d45-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="23d45-120">若要查看有关当前许可计划和每个计划的可用许可证的摘要信息, 请运行以下命令:</span><span class="sxs-lookup"><span data-stu-id="23d45-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="23d45-121">结果包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="23d45-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="23d45-122">**SkuPartNumber:** 显示组织的可用许可计划。</span><span class="sxs-lookup"><span data-stu-id="23d45-122">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="23d45-123">例如, `ENTERPRISEPACK`是 Office 365 企业版 E3 的许可证计划名称。</span><span class="sxs-lookup"><span data-stu-id="23d45-123">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="23d45-124">**Enabled:** 您为特定许可计划购买的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="23d45-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="23d45-125">**ConsumedUnits:** 您已从特定许可计划中分配给用户的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="23d45-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="23d45-126">若要查看有关所有许可计划中可用的 Office 365 服务的详细信息, 请首先显示你的许可证计划的列表。</span><span class="sxs-lookup"><span data-stu-id="23d45-126">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="23d45-127">接下来, 将许可证计划信息存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="23d45-127">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="23d45-128">接下来, 在特定的许可证计划中显示服务。</span><span class="sxs-lookup"><span data-stu-id="23d45-128">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlans
````

<span data-ttu-id="23d45-129">\<index> 是一个整数, 它指定从`Get-AzureADSubscribedSku | Select SkuPartNumber`命令的显示 (减 1) 开始的许可证计划的行号。</span><span class="sxs-lookup"><span data-stu-id="23d45-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="23d45-130">例如, 如果`Get-AzureADSubscribedSku | Select SkuPartNumber`命令的显示为:</span><span class="sxs-lookup"><span data-stu-id="23d45-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="23d45-131">然后, 显示 ENTERPRISEPREMIUM 许可证计划的服务的命令如下所示:</span><span class="sxs-lookup"><span data-stu-id="23d45-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlans
````

<span data-ttu-id="23d45-132">ENTERPRISEPREMIUM 是第三行。</span><span class="sxs-lookup"><span data-stu-id="23d45-132">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="23d45-133">因此, 索引值为 (3-1) 或2。</span><span class="sxs-lookup"><span data-stu-id="23d45-133">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="23d45-134">有关许可证计划 (也称为产品名称)、其包含的服务计划及其相应的友好名称的完整列表, 请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="23d45-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="23d45-135">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="23d45-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="23d45-136">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="23d45-136">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="23d45-137">PowerShell 脚本可自动执行本主题中描述的过程。</span><span class="sxs-lookup"><span data-stu-id="23d45-137">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="23d45-138">具体来说, 该脚本允许您查看和禁用 Office 365 组织中的服务, 包括 Sway。</span><span class="sxs-lookup"><span data-stu-id="23d45-138">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="23d45-139">有关详细信息，请参阅[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="23d45-139">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="23d45-140">若要查看有关当前许可计划和每个计划的可用许可证的摘要信息, 请运行以下命令:</span><span class="sxs-lookup"><span data-stu-id="23d45-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="23d45-141">结果包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="23d45-141">The results contain the following information:</span></span>
  
- <span data-ttu-id="23d45-142">**AccountSkuId:** 使用语法`<CompanyName>:<LicensingPlan>`显示您的组织可用的许可计划。</span><span class="sxs-lookup"><span data-stu-id="23d45-142">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="23d45-143">_<CompanyName>_ 是您在 Office 365 中注册时提供的值, 并且对于您的组织是唯一的。</span><span class="sxs-lookup"><span data-stu-id="23d45-143">_<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="23d45-144">对于_<LicensingPlan>_ 所有人而言, 值都是相同的。</span><span class="sxs-lookup"><span data-stu-id="23d45-144">The _<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="23d45-145">例如, 在 "值`litwareinc:ENTERPRISEPACK`"、"公司名称`litwareinc`" 和 "许可计划名称`ENTERPRISEPACK`" 中, 是 Office 365 企业版 E3 的系统名称。</span><span class="sxs-lookup"><span data-stu-id="23d45-145">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="23d45-146">**ActiveUnits:** 您为特定许可计划购买的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="23d45-146">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="23d45-147">**WarningUnits:** 尚未续订的许可计划中的许可证数量, 在30天的宽限期后将过期。</span><span class="sxs-lookup"><span data-stu-id="23d45-147">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="23d45-148">**ConsumedUnits:** 您已从特定许可计划中分配给用户的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="23d45-148">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="23d45-149">若要查看有关所有许可计划中可用的 Office 365 服务的详细信息, 请运行以下命令:</span><span class="sxs-lookup"><span data-stu-id="23d45-149">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="23d45-150">下表显示了最常用服务的 Office 365 服务计划及其友好名称。</span><span class="sxs-lookup"><span data-stu-id="23d45-150">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="23d45-151">服务计划列表可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="23d45-151">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="23d45-152">**服务计划**</span><span class="sxs-lookup"><span data-stu-id="23d45-152">**Service plan**</span></span>|<span data-ttu-id="23d45-153">**说明**</span><span class="sxs-lookup"><span data-stu-id="23d45-153">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="23d45-154">Sway</span><span class="sxs-lookup"><span data-stu-id="23d45-154">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="23d45-155">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="23d45-155">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="23d45-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="23d45-156">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="23d45-157">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="23d45-157">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="23d45-158">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="23d45-158">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="23d45-159">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="23d45-159">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="23d45-160">Office Online</span><span class="sxs-lookup"><span data-stu-id="23d45-160">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="23d45-161">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="23d45-161">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="23d45-162">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="23d45-162">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="23d45-163">有关许可证计划 (也称为产品名称)、其包含的服务计划及其相应的友好名称的完整列表, 请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="23d45-163">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="23d45-164">若要查看有关特定许可计划中可用的 Office 365 服务的详细信息, 请使用以下语法。</span><span class="sxs-lookup"><span data-stu-id="23d45-164">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="23d45-165">本示例显示了 litwareinc: ENTERPRISEPACK (Office 365 企业版 E3) 许可计划中可用的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="23d45-165">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="23d45-166">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="23d45-166">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="23d45-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23d45-167">See also</span></span>


[<span data-ttu-id="23d45-168">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="23d45-168">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="23d45-169">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="23d45-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="23d45-170">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="23d45-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
