---
title: 使用 Office 365 PowerShell 查看帐户许可证和服务详细信息
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/27/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: 介绍如何使用 Office 365 PowerShell 来确定已分配给用户的 Office 365 服务。
ms.openlocfilehash: 78608c3a52151c115eaf80b5315bb71b61e62356
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223104"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="c67cd-103">使用 Office 365 PowerShell 查看帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="c67cd-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="c67cd-104">**摘要：** 介绍如何使用 Office 365 PowerShell 来确定已分配给用户的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="c67cd-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="c67cd-p101">在 Office 365 中，从许可计划许可 （也称为的 Sku 或 Office 365 计划） 向用户授予访问这些计划为定义的 Office 365 服务。但是，用户可能无法访问当前分配给它们的许可证中可用的所有服务。Office 365 PowerShell 中可用于对用户帐户中查看的服务的状态。</span><span class="sxs-lookup"><span data-stu-id="c67cd-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="c67cd-108">准备工作</span><span class="sxs-lookup"><span data-stu-id="c67cd-108">Before you begin</span></span>

- <span data-ttu-id="c67cd-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="c67cd-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c67cd-111">使用命令`Get-MsolAccountSku`和`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`查找以下信息：</span><span class="sxs-lookup"><span data-stu-id="c67cd-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="c67cd-112">您的组织中提供的许可计划。</span><span class="sxs-lookup"><span data-stu-id="c67cd-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="c67cd-113">每个许可计划中提供的服务以及列出它们的顺序（索引号）。</span><span class="sxs-lookup"><span data-stu-id="c67cd-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="c67cd-114">有关许可计划、 许可证和服务的详细信息，请参阅[查看许可证和身份验证服务与 Office 365 PowerShell 中](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="c67cd-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c67cd-115">使用命令`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`查找分配给用户，并中的顺序的许可证所列出 （索引号）。</span><span class="sxs-lookup"><span data-stu-id="c67cd-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="c67cd-116">如果您使用 **Get-MsolUser** cmdlet 而无需使用 _All_ 参数，仅可返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="c67cd-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="c67cd-117">若要查看的用户帐户的服务</span><span class="sxs-lookup"><span data-stu-id="c67cd-117">To view services for a user account</span></span>

<span data-ttu-id="c67cd-118">若要查看所有 Office 365 服务的用户有权访问，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="c67cd-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="c67cd-p103">本示例显示用户 BelindaN@litwareinc.com 有权访问的服务。此时将显示与分配给其帐户的所有许可证关联的服务。</span><span class="sxs-lookup"><span data-stu-id="c67cd-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="c67cd-121">本示例说明了用户 BelindaN@litwareinc.com 使用向她的帐户（索引号是 0）分配的第一个许可证有权访问的服务。</span><span class="sxs-lookup"><span data-stu-id="c67cd-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="c67cd-122">若要查找已启用或未启用特定服务的所有授权用户，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="c67cd-122">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="c67cd-123">这些示例使用下面的信息：</span><span class="sxs-lookup"><span data-stu-id="c67cd-123">These examples use the following information:</span></span>
  
- <span data-ttu-id="c67cd-124">提供对我们感兴趣的 Office 365 服务的访问的许可证分配给 （索引号为 0） 的所有用户的第一个许可证。</span><span class="sxs-lookup"><span data-stu-id="c67cd-124">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="c67cd-p104">我们感兴趣的 Office 365 服务是 Skype 业务 Online 和 Exchange Online。对于与许可计划相关联的许可证，业务 online Skype 是列出的第六个服务 （索引号，5） 和 Exchange Online 是第九服务列出 （索引号为 8）。</span><span class="sxs-lookup"><span data-stu-id="c67cd-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="c67cd-127">本示例返回所有许可的用户启用了 Skype 业务 Online 和 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="c67cd-127">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="c67cd-128">本示例返回所有许可的用户未启用的 Skype 业务 Online 或 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="c67cd-128">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="c67cd-129">若要查看已分配*多个许可证*的用户的所有服务，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="c67cd-129">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a><span data-ttu-id="c67cd-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c67cd-130">See also</span></span>

<span data-ttu-id="c67cd-131">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="c67cd-131">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="c67cd-132">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="c67cd-132">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c67cd-133">使用 Office 365 PowerShell 删除和还原用户账户</span><span class="sxs-lookup"><span data-stu-id="c67cd-133">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c67cd-134">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="c67cd-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c67cd-135">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="c67cd-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c67cd-136">使用 Office 365 PowerShell 删除用户帐户的许可证</span><span class="sxs-lookup"><span data-stu-id="c67cd-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="c67cd-137">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="c67cd-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="c67cd-138">ConvertTo Html</span><span class="sxs-lookup"><span data-stu-id="c67cd-138">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="c67cd-139">Format-List</span><span class="sxs-lookup"><span data-stu-id="c67cd-139">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="c67cd-140">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="c67cd-140">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="c67cd-141">选择对象</span><span class="sxs-lookup"><span data-stu-id="c67cd-141">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="c67cd-142">Where-Object</span><span class="sxs-lookup"><span data-stu-id="c67cd-142">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="c67cd-143">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="c67cd-143">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]