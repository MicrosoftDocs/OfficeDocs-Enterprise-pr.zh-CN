---
title: 使用 Office 365 PowerShell 禁止访问服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: 使用 Office 365 PowerShell 禁用对用户的 Office 365 服务的访问。
ms.openlocfilehash: bd6961f0de52d95026bae3a743613b33a4af918b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069028"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="b51b4-103">使用 Office 365 PowerShell 禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="b51b4-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="b51b4-104">**摘要:** 介绍如何使用 Office 365 PowerShell 为组织中的用户禁用对 Office 365 服务的访问。</span><span class="sxs-lookup"><span data-stu-id="b51b4-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="b51b4-105">从许可计划中为 Office 365 帐户分配许可证时, 用户将从该许可证中获取 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="b51b4-105">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="b51b4-106">但是, 您可以控制用户可以访问的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="b51b4-106">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="b51b4-107">例如, 即使许可证允许访问 SharePoint Online 服务, 也可以禁用对它的访问。</span><span class="sxs-lookup"><span data-stu-id="b51b4-107">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="b51b4-108">您可以使用 PowerShell 针对特定许可计划禁用对任意数量的服务的访问:</span><span class="sxs-lookup"><span data-stu-id="b51b4-108">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="b51b4-109">单个帐户。</span><span class="sxs-lookup"><span data-stu-id="b51b4-109">An individual account.</span></span>
    
- <span data-ttu-id="b51b4-110">一组帐户。</span><span class="sxs-lookup"><span data-stu-id="b51b4-110">A group of accounts.</span></span>
    
- <span data-ttu-id="b51b4-111">组织中的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="b51b4-111">All accounts in your organization.</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b51b4-112">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="b51b4-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b51b4-113">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="b51b4-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="b51b4-114">接下来, 使用此命令查看可用的许可计划, 也称为 "AccountSkuIds":</span><span class="sxs-lookup"><span data-stu-id="b51b4-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

<span data-ttu-id="b51b4-115">有关详细信息, 请参阅[使用 Office 365 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="b51b4-115">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="b51b4-116">若要查看本主题中的过程的前后结果, 请参阅[使用 Office 365 PowerShell 查看帐户许可证和服务详细信息](view-account-license-and-service-details-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="b51b4-116">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="b51b4-117">PowerShell 脚本可自动执行本主题中描述的过程。</span><span class="sxs-lookup"><span data-stu-id="b51b4-117">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="b51b4-118">具体来说, 该脚本允许您查看和禁用 Office 365 组织中的服务, 包括 Sway。</span><span class="sxs-lookup"><span data-stu-id="b51b4-118">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="b51b4-119">有关详细信息，请参阅[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="b51b4-119">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="b51b4-120">针对特定用户禁用特定许可计划的特定 Office 365 服务</span><span class="sxs-lookup"><span data-stu-id="b51b4-120">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="b51b4-121">若要为用户禁用特定许可计划的一组特定的 Office 365 服务, 请执行以下步骤:</span><span class="sxs-lookup"><span data-stu-id="b51b4-121">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="b51b4-122">使用以下语法确定许可计划中不希望的服务:</span><span class="sxs-lookup"><span data-stu-id="b51b4-122">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  <span data-ttu-id="b51b4-123">下面的示例创建一个**LicenseOptions**对象, 该对象禁用名为`litwareinc:ENTERPRISEPACK` (Office 365 企业版 E3) 的许可计划中的 Office online 和 SharePoint online services。</span><span class="sxs-lookup"><span data-stu-id="b51b4-123">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="b51b4-124">将步骤 1 中的 **LicenseOptions** 对象用于一个或多个用户。</span><span class="sxs-lookup"><span data-stu-id="b51b4-124">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="b51b4-125">若要创建一个已禁用服务的新帐户，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="b51b4-125">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  <span data-ttu-id="b51b4-126">下面的示例为 Allie Bellew 创建了一个新帐户, 该帐户分配许可证并禁用步骤1中所述的服务。</span><span class="sxs-lookup"><span data-stu-id="b51b4-126">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  <span data-ttu-id="b51b4-127">有关在 Office 365 PowerShell 中创建用户帐户的详细信息, 请参阅[Create user accounts With office 365 powershell](create-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="b51b4-127">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="b51b4-128">若要禁用现有授权用户的服务，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="b51b4-128">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  <span data-ttu-id="b51b4-129">本示例对用户 BelindaN@litwareinc.com 禁用服务。</span><span class="sxs-lookup"><span data-stu-id="b51b4-129">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="b51b4-130">若要禁用步骤1中对所有现有许可用户所述的服务, 请从**get-msolaccountsku** cmdlet (如**litwareinc: ENTERPRISEPACK**) 的显示中指定 Office 365 计划的名称, 然后运行以下命令:</span><span class="sxs-lookup"><span data-stu-id="b51b4-130">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="b51b4-131">如果使用**get-msoluser** cmdlet, 而不使用_All_参数, 则仅返回前500个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="b51b4-131">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>


  - <span data-ttu-id="b51b4-132">若要对一组现有用户禁用服务，请使用下列两种方法之一来确定用户：</span><span class="sxs-lookup"><span data-stu-id="b51b4-132">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="b51b4-133">**基于现有帐户属性筛选帐户**为此, 请使用以下语法:</span><span class="sxs-lookup"><span data-stu-id="b51b4-133">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="b51b4-134">下面的示例为美国的销售部门中的用户禁用服务。</span><span class="sxs-lookup"><span data-stu-id="b51b4-134">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="b51b4-135">**使用特定帐户的列表**为此, 请执行以下步骤:</span><span class="sxs-lookup"><span data-stu-id="b51b4-135">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="b51b4-136">创建一个文本文件，在它的每一行上包含一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b51b4-136">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="b51b4-137">在此示例中, 文本文件为 C:\\我的文档\\帐户 .txt。</span><span class="sxs-lookup"><span data-stu-id="b51b4-137">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="b51b4-138">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b51b4-138">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="b51b4-139">如果要对多个许可计划禁用服务访问, 请针对每个许可计划重复上述说明, 以确保:</span><span class="sxs-lookup"><span data-stu-id="b51b4-139">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="b51b4-140">已为用户帐户分配许可计划。</span><span class="sxs-lookup"><span data-stu-id="b51b4-140">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="b51b4-141">要禁用的服务在许可计划中可用。</span><span class="sxs-lookup"><span data-stu-id="b51b4-141">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="b51b4-142">若要在向用户分配许可计划时为其禁用 Office 365 服务, 请参阅在[分配用户许可证时禁用对服务的访问](disable-access-to-services-while-assigning-user-licenses.md)。</span><span class="sxs-lookup"><span data-stu-id="b51b4-142">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="b51b4-143">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="b51b4-143">New to Office 365?</span></span>
<span data-ttu-id="b51b4-144"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="b51b4-144"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="b51b4-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b51b4-145">See also</span></span>
<span data-ttu-id="b51b4-146"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="b51b4-146"></span></span>

<span data-ttu-id="b51b4-147">请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：</span><span class="sxs-lookup"><span data-stu-id="b51b4-147">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="b51b4-148">使用 Office 365 PowerShell 删除和还原用户账户</span><span class="sxs-lookup"><span data-stu-id="b51b4-148">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="b51b4-149">使用 Office 365 PowerShell 删除和还原用户账户</span><span class="sxs-lookup"><span data-stu-id="b51b4-149">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="b51b4-150">使用 Office 365 PowerShell 冻结用户账户</span><span class="sxs-lookup"><span data-stu-id="b51b4-150">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="b51b4-151">使用 Office 365 PowerShell 向用户帐户分配许可证</span><span class="sxs-lookup"><span data-stu-id="b51b4-151">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="b51b4-152">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="b51b4-152">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
