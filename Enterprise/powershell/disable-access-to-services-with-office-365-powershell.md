---
title: 使用 Office 365 PowerShell 禁止访问服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: 使用 Office 365 PowerShell 禁用对用户的 Office 365 服务的访问。
ms.openlocfilehash: 17927b6d7e402aff66c059e159ae81a950667ad1
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106213"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="451df-103">使用 Office 365 PowerShell 禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="451df-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="451df-104">从许可计划中为 Office 365 帐户分配许可证时，用户将从该许可证中获取 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="451df-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="451df-105">但是，您可以控制用户可以访问的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="451df-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="451df-106">例如，即使许可证允许访问 SharePoint Online 服务，也可以禁用对它的访问。</span><span class="sxs-lookup"><span data-stu-id="451df-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="451df-107">您可以使用 PowerShell 针对特定许可计划禁用对任意数量的服务的访问：</span><span class="sxs-lookup"><span data-stu-id="451df-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="451df-108">单个帐户。</span><span class="sxs-lookup"><span data-stu-id="451df-108">An individual account.</span></span>
- <span data-ttu-id="451df-109">一组帐户。</span><span class="sxs-lookup"><span data-stu-id="451df-109">A group of accounts.</span></span>
- <span data-ttu-id="451df-110">组织中的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="451df-110">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="451df-111">有一些 Office 365 服务依赖项可以阻止您在其他服务依赖于指定的服务时禁用该服务。</span><span class="sxs-lookup"><span data-stu-id="451df-111">There are Office 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="451df-112">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="451df-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="451df-113">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="451df-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="451df-114">接下来，使用此命令查看可用的许可计划，也称为 "AccountSkuIds"：</span><span class="sxs-lookup"><span data-stu-id="451df-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="451df-115">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="451df-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="451df-116">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="451df-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="451df-117">有关详细信息，请参阅[使用 Office 365 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="451df-117">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="451df-118">若要查看本主题中的过程的前后结果，请参阅[使用 Office 365 PowerShell 查看帐户许可证和服务详细信息](view-account-license-and-service-details-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="451df-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="451df-119">PowerShell 脚本可自动执行本主题中描述的过程。</span><span class="sxs-lookup"><span data-stu-id="451df-119">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="451df-120">具体来说，该脚本允许您查看和禁用 Office 365 组织中的服务，包括 Sway。</span><span class="sxs-lookup"><span data-stu-id="451df-120">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="451df-121">有关详细信息，请参阅[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="451df-121">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="451df-122">针对特定用户禁用特定许可计划的特定 Office 365 服务</span><span class="sxs-lookup"><span data-stu-id="451df-122">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="451df-123">若要为用户禁用特定许可计划的一组特定的 Office 365 服务，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="451df-123">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="451df-124">步骤1：使用以下语法确定许可计划中不需要的服务：</span><span class="sxs-lookup"><span data-stu-id="451df-124">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="451df-125">下面的示例创建一个**LicenseOptions**对象，该对象禁用名为`litwareinc:ENTERPRISEPACK` （Office 365 企业版 E3）的许可计划中的 Office 和 SharePoint Online services。</span><span class="sxs-lookup"><span data-stu-id="451df-125">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="451df-126">步骤2：在一个或多个用户上使用步骤1中的**LicenseOptions**对象。</span><span class="sxs-lookup"><span data-stu-id="451df-126">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="451df-127">若要创建一个已禁用服务的新帐户，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="451df-127">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="451df-128">下面的示例为 Allie Bellew 创建了一个新帐户，该帐户分配许可证并禁用步骤1中所述的服务。</span><span class="sxs-lookup"><span data-stu-id="451df-128">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="451df-129">有关在 Office 365 PowerShell 中创建用户帐户的详细信息，请参阅[Create user accounts With office 365 powershell](create-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="451df-129">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="451df-130">若要禁用现有授权用户的服务，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="451df-130">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="451df-131">本示例对用户 BelindaN@litwareinc.com 禁用服务。</span><span class="sxs-lookup"><span data-stu-id="451df-131">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="451df-132">若要禁用步骤1中对所有现有许可用户所述的服务，请从**get-msolaccountsku** cmdlet （如**litwareinc： ENTERPRISEPACK**）的显示中指定 Office 365 计划的名称，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="451df-132">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="451df-133">如果使用**get-msoluser** cmdlet，而不使用_All_参数，则仅返回前500个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="451df-133">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="451df-134">若要对一组现有用户禁用服务，请使用下列两种方法之一来确定用户：</span><span class="sxs-lookup"><span data-stu-id="451df-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="451df-135">**方法1。基于现有帐户属性筛选帐户**</span><span class="sxs-lookup"><span data-stu-id="451df-135">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="451df-136">为此，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="451df-136">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="451df-137">下面的示例为美国的销售部门中的用户禁用服务。</span><span class="sxs-lookup"><span data-stu-id="451df-137">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="451df-138">**方法2：使用特定帐户的列表**</span><span class="sxs-lookup"><span data-stu-id="451df-138">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="451df-139">若要完成此操作，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="451df-139">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="451df-140">创建一个文本文件，在它的每一行上包含一个帐户，如下所示：</span><span class="sxs-lookup"><span data-stu-id="451df-140">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="451df-141">在此示例中，文本文件为 C：\\我的文档\\帐户 .txt。</span><span class="sxs-lookup"><span data-stu-id="451df-141">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="451df-142">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="451df-142">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="451df-143">如果要对多个许可计划禁用服务访问，请针对每个许可计划重复上述说明，以确保：</span><span class="sxs-lookup"><span data-stu-id="451df-143">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="451df-144">已为用户帐户分配许可计划。</span><span class="sxs-lookup"><span data-stu-id="451df-144">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="451df-145">要禁用的服务在许可计划中可用。</span><span class="sxs-lookup"><span data-stu-id="451df-145">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="451df-146">若要在向用户分配许可计划时为其禁用 Office 365 服务，请参阅在[分配用户许可证时禁用对服务的访问](disable-access-to-services-while-assigning-user-licenses.md)。</span><span class="sxs-lookup"><span data-stu-id="451df-146">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="451df-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="451df-147">See also</span></span>

[<span data-ttu-id="451df-148">使用 Office 365 PowerShell 管理用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="451df-148">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="451df-149">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="451df-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="451df-150">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="451df-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
