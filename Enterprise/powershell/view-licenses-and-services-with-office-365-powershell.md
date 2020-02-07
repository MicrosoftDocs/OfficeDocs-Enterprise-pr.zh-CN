---
title: 使用 Office 365 PowerShell 查看许可证和服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: 说明如何使用 Office 365 PowerShell 查看有关 Office 365 组织中可用的许可计划、服务和许可证的信息。
ms.openlocfilehash: 9ecaad00d46cf920822419ca1ccdd547ff060fa0
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844133"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="c3989-103">使用 Office 365 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="c3989-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="c3989-104">每个 Office 365 订阅都包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="c3989-104">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="c3989-105">**许可计划**这些计划也称为许可证计划或 Office 365 计划。</span><span class="sxs-lookup"><span data-stu-id="c3989-105">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="c3989-106">许可计划定义可供用户使用的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="c3989-106">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="c3989-107">您的 Office 365 订阅可能包含多个许可计划。</span><span class="sxs-lookup"><span data-stu-id="c3989-107">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="c3989-108">Office 365 企业版 E3 是许可计划的一个示例。</span><span class="sxs-lookup"><span data-stu-id="c3989-108">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="c3989-109">**服务**这些也称为服务计划。</span><span class="sxs-lookup"><span data-stu-id="c3989-109">**Services** These are also known as service plans.</span></span> <span data-ttu-id="c3989-110">服务是在每个许可计划中可用的 Office 365 产品、功能和功能，例如 Exchange Online 和 Office Professional Plus。</span><span class="sxs-lookup"><span data-stu-id="c3989-110">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus.</span></span> <span data-ttu-id="c3989-111">可以从授予不同服务访问权限的不同许可计划向用户分配多个许可证。</span><span class="sxs-lookup"><span data-stu-id="c3989-111">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="c3989-112">**许可证**每个许可计划包含您购买的许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="c3989-112">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="c3989-113">您将许可证分配给用户，以便他们可以使用由许可计划定义的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="c3989-113">You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="c3989-114">每个用户帐户都需要一个许可计划中的至少一个许可证，以便他们可以登录 Office 365 并使用服务。</span><span class="sxs-lookup"><span data-stu-id="c3989-114">Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="c3989-115">您可以使用 Office 365 PowerShell 来查看有关 Office 365 组织中可用的许可计划、许可证和服务的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c3989-115">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization.</span></span> <span data-ttu-id="c3989-116">有关在不同的 Office 365 订阅中提供的产品、功能和服务的详细信息，请参阅[Office 365 计划选项](https://go.microsoft.com/fwlink/p/?LinkId=691147)。</span><span class="sxs-lookup"><span data-stu-id="c3989-116">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c3989-117">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3989-117">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c3989-118">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="c3989-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="c3989-119">若要查看有关当前许可计划和每个计划的可用许可证的摘要信息，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="c3989-119">To view summary information about your current licensing plans and the available licenses for each plan, run this command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="c3989-120">结果中包含：</span><span class="sxs-lookup"><span data-stu-id="c3989-120">The results contain:</span></span>
  
- <span data-ttu-id="c3989-121">**SkuPartNumber：** 显示组织的可用许可计划。</span><span class="sxs-lookup"><span data-stu-id="c3989-121">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="c3989-122">例如， `ENTERPRISEPACK`是 Office 365 企业版 E3 的许可证计划名称。</span><span class="sxs-lookup"><span data-stu-id="c3989-122">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="c3989-123">**Enabled：** 您为特定许可计划购买的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="c3989-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="c3989-124">**ConsumedUnits：** 您已从特定许可计划中分配给用户的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="c3989-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="c3989-125">若要查看有关所有许可计划中可用的 Office 365 服务的详细信息，请首先显示你的许可证计划的列表。</span><span class="sxs-lookup"><span data-stu-id="c3989-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="c3989-126">接下来，将许可证计划信息存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="c3989-126">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="c3989-127">接下来，在特定的许可证计划中显示服务。</span><span class="sxs-lookup"><span data-stu-id="c3989-127">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="c3989-128">\<index> 是一个整数，它指定从`Get-AzureADSubscribedSku | Select SkuPartNumber`命令的显示（减1）的许可证计划的行数。</span><span class="sxs-lookup"><span data-stu-id="c3989-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="c3989-129">例如，如果`Get-AzureADSubscribedSku | Select SkuPartNumber`命令的显示为：</span><span class="sxs-lookup"><span data-stu-id="c3989-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="c3989-130">然后，显示 ENTERPRISEPREMIUM 许可证计划的服务的命令如下所示：</span><span class="sxs-lookup"><span data-stu-id="c3989-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="c3989-131">ENTERPRISEPREMIUM 是第三行。</span><span class="sxs-lookup"><span data-stu-id="c3989-131">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="c3989-132">因此，索引值为（3-1）或2。</span><span class="sxs-lookup"><span data-stu-id="c3989-132">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="c3989-133">有关许可证计划（也称为产品名称）、其包含的服务计划及其相应的友好名称的完整列表，请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="c3989-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c3989-134">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="c3989-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c3989-135">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="c3989-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="c3989-136">PowerShell 脚本可自动执行本主题中描述的过程。</span><span class="sxs-lookup"><span data-stu-id="c3989-136">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="c3989-137">具体来说，该脚本允许您查看和禁用 Office 365 组织中的服务，包括 Sway。</span><span class="sxs-lookup"><span data-stu-id="c3989-137">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="c3989-138">有关详细信息，请参阅[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="c3989-138">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="c3989-139">若要查看有关当前许可计划和每个计划的可用许可证的摘要信息，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="c3989-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="c3989-140">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="c3989-140">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="c3989-141">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="c3989-141">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="c3989-142">结果包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="c3989-142">The results contain the following information:</span></span>
  
- <span data-ttu-id="c3989-143">**AccountSkuId：** 使用语法`<CompanyName>:<LicensingPlan>`显示您的组织可用的许可计划。</span><span class="sxs-lookup"><span data-stu-id="c3989-143">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="c3989-144">"公司名称>" 是您在 Office 365 中注册时提供的值，并且对于您的组织是唯一的。 _ \<_</span><span class="sxs-lookup"><span data-stu-id="c3989-144">_\<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="c3989-145">LicensingPlan>值对所有用户都是相同的。 _ \<_</span><span class="sxs-lookup"><span data-stu-id="c3989-145">The _\<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="c3989-146">例如，在 "值`litwareinc:ENTERPRISEPACK`"、"公司名称`litwareinc`" 和 "许可计划名称`ENTERPRISEPACK`" 中，是 Office 365 企业版 E3 的系统名称。</span><span class="sxs-lookup"><span data-stu-id="c3989-146">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="c3989-147">**ActiveUnits：** 您为特定许可计划购买的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="c3989-147">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="c3989-148">**WarningUnits：** 尚未续订的许可计划中的许可证数量，在30天的宽限期后将过期。</span><span class="sxs-lookup"><span data-stu-id="c3989-148">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="c3989-149">**ConsumedUnits：** 您已从特定许可计划中分配给用户的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="c3989-149">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="c3989-150">若要查看有关所有许可计划中可用的 Office 365 服务的详细信息，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="c3989-150">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="c3989-151">下表显示了最常用服务的 Office 365 服务计划及其友好名称。</span><span class="sxs-lookup"><span data-stu-id="c3989-151">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="c3989-152">服务计划列表可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="c3989-152">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="c3989-153">**服务计划**</span><span class="sxs-lookup"><span data-stu-id="c3989-153">**Service plan**</span></span>|<span data-ttu-id="c3989-154">**说明**</span><span class="sxs-lookup"><span data-stu-id="c3989-154">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="c3989-155">Sway</span><span class="sxs-lookup"><span data-stu-id="c3989-155">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="c3989-156">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c3989-156">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="c3989-157">Yammer</span><span class="sxs-lookup"><span data-stu-id="c3989-157">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="c3989-158">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="c3989-158">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="c3989-159">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="c3989-159">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="c3989-160">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="c3989-160">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="c3989-161">Office</span><span class="sxs-lookup"><span data-stu-id="c3989-161">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="c3989-162">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c3989-162">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="c3989-163">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="c3989-163">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="c3989-164">有关许可证计划（也称为产品名称）、其包含的服务计划及其相应的友好名称的完整列表，请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="c3989-164">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="c3989-165">若要查看有关特定许可计划中可用的 Office 365 服务的详细信息，请使用以下语法。</span><span class="sxs-lookup"><span data-stu-id="c3989-165">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="c3989-166">本示例显示了 litwareinc： ENTERPRISEPACK （Office 365 企业版 E3）许可计划中可用的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="c3989-166">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a><span data-ttu-id="c3989-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3989-167">See also</span></span>

[<span data-ttu-id="c3989-168">使用 Office 365 PowerShell 管理用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="c3989-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c3989-169">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="c3989-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c3989-170">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="c3989-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
