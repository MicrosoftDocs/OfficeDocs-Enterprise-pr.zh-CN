---
title: "使用 Office 365 PowerShell 查看许可证和服务"
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
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: "解释如何使用 Office 365 PowerShell 查看有关授权计划、 服务和 Office 365 提供组织中可用的许可证信息。"
ms.openlocfilehash: 718b26c7afb978384918b2de8ea37d01638d3e16
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="23466-103">使用 Office 365 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="23466-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="23466-104">**摘要：**解释如何使用 Office 365 PowerShell 查看有关授权计划、 服务和 Office 365 提供组织中可用的许可证信息。</span><span class="sxs-lookup"><span data-stu-id="23466-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="23466-105">每个 Office 365 预订由下列元素组成：</span><span class="sxs-lookup"><span data-stu-id="23466-105">Every Office 365 subscription consists of the following elements:</span></span>
- <span data-ttu-id="23466-p101">**授权计划**这些也是已知的 aslicense 计划或 Office 365 计划。授权计划定义可供用户使用的 Office 365 提供服务。Office 365 订阅可能含有多个许可计划。示例授权计划将 Office 365 企业 E3。</span><span class="sxs-lookup"><span data-stu-id="23466-p101">**Licensing plans** These are also known aslicense plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="23466-p102">**服务**这些也是已知的 asservice 计划。服务是 Office 365 的产品、 功能和功能所提供的每个授权的计划，例如，Exchange 联机和 Office Professional Plus。用户可以具有分配给它们从不同的授权计划授予的访问权限不同服务的多个许可证。</span><span class="sxs-lookup"><span data-stu-id="23466-p102">**Services** These are also known asservice plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="23466-p103">**许可证**每个授权计划包含您购买的许可证的数量。将许可证分配给用户以便他们可以使用 Office 365 提供服务所定义的授权计划。每个用户帐户要求从一个授权计划至少一个许可证，因此他们可以登录到 Office 365 提供和使用服务。</span><span class="sxs-lookup"><span data-stu-id="23466-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="23466-p104">Office 365 PowerShell 可用于查看 Office 365 提供组织中可用的授权计划、 许可证和服务有关的详细信息。有关产品、 功能和 Office 365 的不同预订中提供的服务的详细信息，请参阅[Office 365 计划选项](https://go.microsoft.com/fwlink/p/?LinkId=691147)。</span><span class="sxs-lookup"><span data-stu-id="23466-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="23466-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="23466-118">Before you begin</span></span>
<span data-ttu-id="23466-119"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="23466-119"></span></span>

- <span data-ttu-id="23466-p105">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="23466-p105">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="23466-p106">PowerShell 提供了一个脚本来自动执行本主题中描述的过程。具体来说，脚本允许您查看和您 Office 365 的组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用 Office 365 PowerShell 的 Sway 访问](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="23466-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a><span data-ttu-id="23466-125">查看有关许可计划和可用的许可证的信息</span><span class="sxs-lookup"><span data-stu-id="23466-125">View information about licensing plans and the available licenses</span></span>
<span data-ttu-id="23466-126"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="23466-126"></span></span>

<span data-ttu-id="23466-127">若要查看有关您当前的授权计划和每个计划的可用许可证摘要信息，请在 Office 365 PowerShell 运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="23466-127">To view summary information about your current licensing plans and the available licenses for each plan, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="23466-128">结果包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="23466-128">The results contain the following information:</span></span>
  
- <span data-ttu-id="23466-p107">**AccountSkuId:**显示可用的授权计划为您的组织使用的语法`<CompanyName>:<LicensingPlan>`。 _<CompanyName>_为您提供当您注册 Office 365 并为您的组织中是唯一的。_<LicensingPlan>_值是相同的所有人。例如中值, `litwareinc:ENTERPRISEPACK`，公司名称是`litwareinc`，和授权计划名称`ENTERPRISEPACK`，即 Office 365 企业 E3 的系统名称。</span><span class="sxs-lookup"><span data-stu-id="23466-p107">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="23466-133">**ActiveUnits:**您已为特定的授权计划购买的许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="23466-133">**ActiveUnits:** Number of licenses that you've purchases for a specific licensing plan.</span></span>
    
- <span data-ttu-id="23466-134">**WarningUnits:**您没有更新的且将过期 30 天宽限期过后的授权计划中的许可证数。</span><span class="sxs-lookup"><span data-stu-id="23466-134">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="23466-135">**ConsumedUnits:**从某一特定的授权计划已经指派给用户的许可证的数量。</span><span class="sxs-lookup"><span data-stu-id="23466-135">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="23466-136">若要查看有关 Office 365 提供可用服务在所有许可证计划的详细信息，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="23466-136">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="23466-p108">下表显示 Office 365 提供服务的计划和他们最常见的服务的友好名称。您的服务计划列表可能会有所不同。服务计划和其友好名称的完整列表，请联系[办公室的支持](https://support.office.com/home/contact)。</span><span class="sxs-lookup"><span data-stu-id="23466-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different. For a complete list of service plans and their friendly names, contact [Office Support](https://support.office.com/home/contact).</span></span>
  
|<span data-ttu-id="23466-140">服务计划 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="23466-140">****Service plan****</span></span>|<span data-ttu-id="23466-141">说明 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="23466-141">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="23466-142">Sway</span><span class="sxs-lookup"><span data-stu-id="23466-142">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="23466-143">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="23466-143">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="23466-144">Yammer</span><span class="sxs-lookup"><span data-stu-id="23466-144">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="23466-145">Azure 权限管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="23466-145">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="23466-146">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="23466-146">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="23466-147">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="23466-147">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="23466-148">Office Online</span><span class="sxs-lookup"><span data-stu-id="23466-148">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="23466-149">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="23466-149">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="23466-150">Exchange Online 计划 2</span><span class="sxs-lookup"><span data-stu-id="23466-150">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="23466-151">若要查看有关 Office 365 提供服务所提供的某一特定的授权计划的详细信息，请使用下面的语法。</span><span class="sxs-lookup"><span data-stu-id="23466-151">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq " <AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="23466-152">此示例演示 Office 365 提供服务所提供的 litwareinc:ENTERPRISEPACK (Office 365 企业 E3) 授权计划。</span><span class="sxs-lookup"><span data-stu-id="23466-152">This example shows the Office 365 services that are available in the  litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a><span data-ttu-id="23466-153">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="23466-153">New to Office 365?</span></span>
<span data-ttu-id="23466-154"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="23466-154"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="23466-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23466-155">See also</span></span>
<span data-ttu-id="23466-156"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="23466-156"></span></span>

#### 

[<span data-ttu-id="23466-157">使用 Office 365 PowerShell 查看授权和未授权的用户</span><span class="sxs-lookup"><span data-stu-id="23466-157">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
  
[<span data-ttu-id="23466-158">使用 Office 365 PowerShell 查看帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="23466-158">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
#### 

[<span data-ttu-id="23466-159">获得 MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="23466-159">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)

