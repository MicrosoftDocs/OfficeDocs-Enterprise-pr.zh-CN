---
title: 使用 Office 365 PowerShell 查看许可证和服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
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
description: 介绍如何使用 Office 365 PowerShell 中查看许可计划、 服务和 Office 365 组织中可用的许可证的信息。
ms.openlocfilehash: 8efc123e2820560b4bd8547f4c99bccae242956f
ms.sourcegitcommit: 96313c3c812bae47819f603af995839f4da034c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2019
ms.locfileid: "27786148"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="9c6f6-103">使用 Office 365 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="9c6f6-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="9c6f6-104">**摘要：** 介绍如何使用 Office 365 PowerShell 中查看许可计划、 服务和 Office 365 组织中可用的许可证的信息。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="9c6f6-105">每个 Office 365 订阅包括以下元素：</span><span class="sxs-lookup"><span data-stu-id="9c6f6-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="9c6f6-p101">**许可计划**这些是也称为许可计划或 Office 365 plans。许可计划定义适用于用户的 Office 365 服务。Office 365 订阅可能包含多个许可计划。示例许可计划将为 Office 365 企业版 E3。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="9c6f6-p102">**服务**这些是也称为服务计划。服务是 Office 365 产品、 功能和功能所提供的每个许可计划，例如 Exchange Online 和 Office Professional Plus。用户可以具有多个许可证分配给它们从不同的许可计划授予的访问权限不同的服务。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="9c6f6-p103">**许可证**每个许可计划包含您购买的许可证数量。以便他们可以使用 Office 365 服务所定义的许可计划，可以向用户分配许可证。每个用户帐户需要至少一个许可证从一个许可计划，以便他们可以登录到 Office 365，并使用服务。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="9c6f6-p104">Office 365 PowerShell 中可用于在 Office 365 组织中查看有关可用许可计划、 许可证和服务的详细信息。有关产品、 功能和在不同的 Office 365 订阅中可用的服务的详细信息，请参阅[Office 365 计划选项](https://go.microsoft.com/fwlink/p/?LinkId=691147)。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="9c6f6-118">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c6f6-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="9c6f6-119">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="9c6f6-120">若要查看有关您当前的许可计划和每个计划可用的许可证的摘要信息，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9c6f6-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="9c6f6-121">结果包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="9c6f6-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="9c6f6-p105">**SkuPartNumber:** 显示为您的组织可用的许可计划。例如，`ENTERPRISEPACK`是 Office 365 企业版 E3 的系统名称。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-p105">**SkuPartNumber:** Shows the available licensing plans for your organization. For example, `ENTERPRISEPACK` is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="9c6f6-124">**启用：** 您已为特定的许可计划购买的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="9c6f6-125">**ConsumedUnits:** 从特定的许可计划已分配给用户的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="9c6f6-126">若要查看有关所有许可计划中可用的 Office 365 服务的详细信息，请首先显示许可计划的列表。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-126">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="9c6f6-127">接下来，在一个变量中存储的许可计划信息。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-127">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="9c6f6-128">接下来，在特定的许可计划中显示服务。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-128">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlans
````

<span data-ttu-id="9c6f6-129">\<索引 > 是一个整数，指定的行数的许可计划从显示的`Get-AzureADSubscribedSku | Select SkuPartNumber`命令，减 1 之间。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="9c6f6-130">例如，如果显示的`Get-AzureADSubscribedSku | Select SkuPartNumber`命令这是：</span><span class="sxs-lookup"><span data-stu-id="9c6f6-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="9c6f6-131">然后命令来显示 ENTERPRISEPREMIUM 许可计划的服务是：</span><span class="sxs-lookup"><span data-stu-id="9c6f6-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlans
````

<span data-ttu-id="9c6f6-p106">ENTERPRISEPREMIUM 是第三行。因此，索引值是 (3-1），或 2。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-p106">ENTERPRISEPREMIUM is the third row. Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="9c6f6-134">有关许可计划 （也称为产品名称） 的完整列表，其包含的服务计划和其相应的友好名称，请参阅[产品名称和授权的服务计划标识符](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="9c6f6-135">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="9c6f6-136">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-136">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="9c6f6-p107">PowerShell 脚本是可用的自动执行本主题中所述的过程。具体而言，该脚本允许您查看和 Office 365 组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用对 Sway 与 Office 365 PowerShell 中的访问](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-p107">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="9c6f6-140">若要查看有关您当前的许可计划和每个计划可用的许可证的摘要信息，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9c6f6-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="9c6f6-141">结果包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="9c6f6-141">The results contain the following information:</span></span>
  
- <span data-ttu-id="9c6f6-p108">**AccountSkuId:** 显示为您的组织可用的许可计划使用语法`<CompanyName>:<LicensingPlan>`。 _<CompanyName>_ 是注册 Office 365 中，为您的组织都是唯一时提供的值。_<LicensingPlan>_ 值是相同的每个人。例如，在值`litwareinc:ENTERPRISEPACK`，公司名为`litwareinc`，许可计划名称和`ENTERPRISEPACK`，这是 Office 365 企业版 E3 的系统名称。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-p108">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="9c6f6-146">**ActiveUnits:** 您已为特定的许可计划购买的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-146">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="9c6f6-147">**WarningUnits:** 您还未更新的且将过期后 30 天的宽限期的许可计划中的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-147">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="9c6f6-148">**ConsumedUnits:** 从特定的许可计划已分配给用户的许可证数量。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-148">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="9c6f6-149">若要查看有关所有许可计划中可用的 Office 365 服务的详细信息，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9c6f6-149">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="9c6f6-p109">下表显示了 Office 365 服务计划和其最常见的服务的友好名称。您的服务计划列表可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-p109">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="9c6f6-152">**服务计划**</span><span class="sxs-lookup"><span data-stu-id="9c6f6-152">**Service plan**</span></span>|<span data-ttu-id="9c6f6-153">**说明**</span><span class="sxs-lookup"><span data-stu-id="9c6f6-153">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="9c6f6-154">Sway</span><span class="sxs-lookup"><span data-stu-id="9c6f6-154">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="9c6f6-155">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9c6f6-155">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="9c6f6-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="9c6f6-156">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="9c6f6-157">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="9c6f6-157">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="9c6f6-158">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="9c6f6-158">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="9c6f6-159">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="9c6f6-159">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="9c6f6-160">Office Online</span><span class="sxs-lookup"><span data-stu-id="9c6f6-160">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="9c6f6-161">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c6f6-161">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="9c6f6-162">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="9c6f6-162">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="9c6f6-163">有关许可计划 （也称为产品名称） 的完整列表，其包含的服务计划和其相应的友好名称，请参阅[产品名称和授权的服务计划标识符](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-163">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="9c6f6-164">若要查看有关特定的许可计划中可用的 Office 365 服务的详细信息，请使用以下语法。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-164">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="9c6f6-165">本示例显示 litwareinc: enterprisepack (Office 365 企业版 E3) 许可计划中可用的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="9c6f6-165">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="9c6f6-166">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="9c6f6-166">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="9c6f6-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c6f6-167">See also</span></span>


[<span data-ttu-id="9c6f6-168">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="9c6f6-168">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="9c6f6-169">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="9c6f6-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9c6f6-170">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="9c6f6-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
