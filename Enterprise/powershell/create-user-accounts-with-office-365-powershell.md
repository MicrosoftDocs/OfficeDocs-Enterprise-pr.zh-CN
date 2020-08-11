---
title: 使用 PowerShell 创建 Microsoft 365 用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 在本文中，我们将了解如何使用 PowerShell 创建用户帐户或多个 Microsoft 365 用户帐户。
ms.openlocfilehash: 2f4d7b42e68e3bd426ea73c8568e0c603af06dcb
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605988"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="f8c89-103">使用 PowerShell 创建 Microsoft 365 用户帐户</span><span class="sxs-lookup"><span data-stu-id="f8c89-103">Create Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="f8c89-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="f8c89-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="f8c89-105">您可以使用适用于 Microsoft 365 的 PowerShell 高效地创建用户帐户，尤其是多个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="f8c89-105">You can use PowerShell for Microsoft 365 to efficiently create user accounts, especially multiple user accounts.</span></span> <span data-ttu-id="f8c89-106">当您在 PowerShell 中创建用户帐户时，某些帐户属性始终是必需的。</span><span class="sxs-lookup"><span data-stu-id="f8c89-106">When you create user accounts in PowerShell, certain account properties are always required.</span></span> <span data-ttu-id="f8c89-107">其他属性对于创建帐户则不是必需的，但也很重要。</span><span class="sxs-lookup"><span data-stu-id="f8c89-107">Other properties aren't required to create the account, but are otherwise important.</span></span> <span data-ttu-id="f8c89-108">下表介绍了这些属性：</span><span class="sxs-lookup"><span data-stu-id="f8c89-108">These properties are described in the following table:</span></span>
  
|<span data-ttu-id="f8c89-109">**属性名称**</span><span class="sxs-lookup"><span data-stu-id="f8c89-109">**Property name**</span></span>|<span data-ttu-id="f8c89-110">**是否必需？**</span><span class="sxs-lookup"><span data-stu-id="f8c89-110">**Required?**</span></span>|<span data-ttu-id="f8c89-111">**说明**</span><span class="sxs-lookup"><span data-stu-id="f8c89-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f8c89-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="f8c89-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="f8c89-113">是</span><span class="sxs-lookup"><span data-stu-id="f8c89-113">Yes</span></span>  <br/> |<span data-ttu-id="f8c89-114">这是在 Microsoft 365 服务中使用的显示名称。</span><span class="sxs-lookup"><span data-stu-id="f8c89-114">This is the display name that's used in Microsoft 365 services.</span></span> <span data-ttu-id="f8c89-115">例如，Caleb Sills。</span><span class="sxs-lookup"><span data-stu-id="f8c89-115">For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="f8c89-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="f8c89-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="f8c89-117">是</span><span class="sxs-lookup"><span data-stu-id="f8c89-117">Yes</span></span>  <br/> |<span data-ttu-id="f8c89-118">这是用于登录 Microsoft 365 服务的帐户名称。</span><span class="sxs-lookup"><span data-stu-id="f8c89-118">This is the account name that's used to sign in to Microsoft 365 services.</span></span> <span data-ttu-id="f8c89-119">例如，CalebS@contoso.onmicrosoft.com。</span><span class="sxs-lookup"><span data-stu-id="f8c89-119">For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="f8c89-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="f8c89-120">**FirstName**</span></span> <br/> |<span data-ttu-id="f8c89-121">否</span><span class="sxs-lookup"><span data-stu-id="f8c89-121">No</span></span>  <br/> ||
|<span data-ttu-id="f8c89-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="f8c89-122">**LastName**</span></span> <br/> |<span data-ttu-id="f8c89-123">否</span><span class="sxs-lookup"><span data-stu-id="f8c89-123">No</span></span>  <br/> ||
|<span data-ttu-id="f8c89-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="f8c89-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="f8c89-125">否</span><span class="sxs-lookup"><span data-stu-id="f8c89-125">No</span></span>  <br/> |<span data-ttu-id="f8c89-126">这是许可计划 (也称为 "许可证计划" 或 "SKU) ，可将可用许可证分配给用户帐户。</span><span class="sxs-lookup"><span data-stu-id="f8c89-126">This is the licensing plan (also known as the license plan or SKU) from which an available license is assigned to the user account.</span></span> <span data-ttu-id="f8c89-127">许可证定义了可供帐户使用的 Microsoft 365 服务。</span><span class="sxs-lookup"><span data-stu-id="f8c89-127">The license defines the Microsoft 365 services that are available to account.</span></span> <span data-ttu-id="f8c89-128">您不必在创建帐户时向用户分配许可证，但该帐户需要许可证才能访问 Microsoft 365 服务。</span><span class="sxs-lookup"><span data-stu-id="f8c89-128">You don't have to assign a license to a user when you create the account, but the account requires a license to access Microsoft 365 services.</span></span> <span data-ttu-id="f8c89-129">创建用户帐户后，您有 30 天的时间可以对该用户帐户授权。</span><span class="sxs-lookup"><span data-stu-id="f8c89-129">You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="f8c89-130">**密码**</span><span class="sxs-lookup"><span data-stu-id="f8c89-130">**Password**</span></span> <br/> |<span data-ttu-id="f8c89-131">否</span><span class="sxs-lookup"><span data-stu-id="f8c89-131">No</span></span>  <br/> | <span data-ttu-id="f8c89-p105">如果你没有指定密码，将向用户帐户分配一个随机密码，且该密码将显示在命令结果中。如果你指定了密码，则需要是以下三种类型的 8 到 16 位 ASCII 文本字符：小写字母、大写字母、数字和符号。</span><span class="sxs-lookup"><span data-stu-id="f8c89-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="f8c89-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="f8c89-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="f8c89-135">否</span><span class="sxs-lookup"><span data-stu-id="f8c89-135">No</span></span>  <br/> |<span data-ttu-id="f8c89-136">这是一个由两位字母组成的有效 ISO 3166-1 国家/地区代码。</span><span class="sxs-lookup"><span data-stu-id="f8c89-136">This is a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="f8c89-137">例如，US 代表美国，FR 代表法国。</span><span class="sxs-lookup"><span data-stu-id="f8c89-137">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="f8c89-138">提供此值非常重要，因为某些 Microsoft 365 服务在某些国家/地区不可用，因此，除非帐户配置了此值，否则不能向用户帐户分配许可证。</span><span class="sxs-lookup"><span data-stu-id="f8c89-138">It's important to provide this value, because some Microsoft 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured.</span></span> <span data-ttu-id="f8c89-139">有关详细信息，请参阅[关于许可证限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="f8c89-139">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>  <br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f8c89-140">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8c89-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="f8c89-141">首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="f8c89-141">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="f8c89-142">连接后，使用下列语法创建个人帐户：</span><span class="sxs-lookup"><span data-stu-id="f8c89-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="f8c89-143">本示例为名为 Caleb Sills 的美国用户创建一个帐户：</span><span class="sxs-lookup"><span data-stu-id="f8c89-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f8c89-144">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="f8c89-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f8c89-145">首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="f8c89-145">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="f8c89-146">创建单个用户帐户</span><span class="sxs-lookup"><span data-stu-id="f8c89-146">Create an individual user account</span></span>

<span data-ttu-id="f8c89-147">若要创建单个帐户，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="f8c89-147">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
><span data-ttu-id="f8c89-148">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="f8c89-148">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="f8c89-149">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="f8c89-149">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="f8c89-150">若要列出可用的许可计划名称，请使用此命令：</span><span class="sxs-lookup"><span data-stu-id="f8c89-150">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="f8c89-151">本示例为美国用户 Caleb Sills 创建一个帐户并通过 `contoso:ENTERPRISEPACK` (Office 365 企业版 E3) 许可计划分配了一个许可证。</span><span class="sxs-lookup"><span data-stu-id="f8c89-151">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="f8c89-152">创建多个用户帐户</span><span class="sxs-lookup"><span data-stu-id="f8c89-152">Create multiple user accounts</span></span>

1. <span data-ttu-id="f8c89-p108">创建包含所需用户帐户信息的逗号分隔值 (CSV) 文件。例如：</span><span class="sxs-lookup"><span data-stu-id="f8c89-p108">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="f8c89-155">CSV 文件的第一行中的列名和它们的顺序是任意的，但请确保文件中的其余部分的数据与列名的顺序相匹配，并对 PowerShell for Microsoft 365 命令中的参数值使用列名称。</span><span class="sxs-lookup"><span data-stu-id="f8c89-155">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the PowerShell for Microsoft 365 command.</span></span>
    
2. <span data-ttu-id="f8c89-156">使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="f8c89-156">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="f8c89-157">本示例从名为 C:\My Documents\NewAccounts.csv 的文件创建用户帐户，并将结果记录在名为 C:\My Documents\NewAccountResults.csv 的文件中</span><span class="sxs-lookup"><span data-stu-id="f8c89-157">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="f8c89-158">查看输出文件以查看结果。</span><span class="sxs-lookup"><span data-stu-id="f8c89-158">Review the output file to see the results.</span></span> <span data-ttu-id="f8c89-159">未指定密码，因此 Microsoft 365 生成的随机密码在输出文件中可见。</span><span class="sxs-lookup"><span data-stu-id="f8c89-159">We didn't specify passwords, so the random passwords that Microsoft 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="f8c89-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8c89-160">See also</span></span>

[<span data-ttu-id="f8c89-161">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="f8c89-161">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f8c89-162">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f8c89-162">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f8c89-163">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="f8c89-163">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
