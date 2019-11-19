---
title: 使用 Office 365 PowerShell 创建用户帐户
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 了解如何在 Office 365 中使用 Office 365 PowerShell 来创建用户帐户。
ms.openlocfilehash: 9d4aee35a1fc78753087b6eb6695e96966794000
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "38707049"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="32b2c-103">使用 Office 365 PowerShell 创建用户帐户</span><span class="sxs-lookup"><span data-stu-id="32b2c-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="32b2c-104">**摘要：** 了解如何使用 Office 365 PowerShell 在 Office 365 中创建用户帐户。</span><span class="sxs-lookup"><span data-stu-id="32b2c-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="32b2c-p101">您可以使用 Office 365 PowerShell 来高效地创建用户帐户，尤其是多个用户帐户。当您在 Office 365 PowerShell 中创建用户帐户时，某些帐户属性始终是必需的。其他属性对于创建帐户则不是必需的，但也很重要。下表介绍了这些属性：</span><span class="sxs-lookup"><span data-stu-id="32b2c-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
|<span data-ttu-id="32b2c-109">**属性名称**</span><span class="sxs-lookup"><span data-stu-id="32b2c-109">**Property name**</span></span>|<span data-ttu-id="32b2c-110">**是否必需？**</span><span class="sxs-lookup"><span data-stu-id="32b2c-110">**Required?**</span></span>|<span data-ttu-id="32b2c-111">**说明**</span><span class="sxs-lookup"><span data-stu-id="32b2c-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="32b2c-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="32b2c-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="32b2c-113">是</span><span class="sxs-lookup"><span data-stu-id="32b2c-113">Yes</span></span>  <br/> |<span data-ttu-id="32b2c-p102">这是在 Office 365 服务中使用的显示名称。例如，Caleb Sills。</span><span class="sxs-lookup"><span data-stu-id="32b2c-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="32b2c-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="32b2c-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="32b2c-117">是</span><span class="sxs-lookup"><span data-stu-id="32b2c-117">Yes</span></span>  <br/> |<span data-ttu-id="32b2c-p103">这是用于登录到 Office 365 服务的帐户名称。例如，CalebS@contoso.onmicrosoft.com。</span><span class="sxs-lookup"><span data-stu-id="32b2c-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="32b2c-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="32b2c-120">**FirstName**</span></span> <br/> |<span data-ttu-id="32b2c-121">否</span><span class="sxs-lookup"><span data-stu-id="32b2c-121">No</span></span>  <br/> ||
|<span data-ttu-id="32b2c-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="32b2c-122">**LastName**</span></span> <br/> |<span data-ttu-id="32b2c-123">否</span><span class="sxs-lookup"><span data-stu-id="32b2c-123">No</span></span>  <br/> ||
|<span data-ttu-id="32b2c-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="32b2c-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="32b2c-125">否</span><span class="sxs-lookup"><span data-stu-id="32b2c-125">No</span></span>  <br/> |<span data-ttu-id="32b2c-p104">这是许可计划（也称为许可证计划、Office 365 计划或 SKU），使用它可以将可用的许可证分配给用户帐户。该许可证定义可供帐户使用的 Office 365 服务。当你创建帐户时，没有向用户分配许可证，但该帐户需要许可证才能访问 Office 365 服务。创建用户帐户后，有 30 天的时间可以对该用户帐户授权。</span><span class="sxs-lookup"><span data-stu-id="32b2c-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="32b2c-130">**密码**</span><span class="sxs-lookup"><span data-stu-id="32b2c-130">**Password**</span></span> <br/> |<span data-ttu-id="32b2c-131">否</span><span class="sxs-lookup"><span data-stu-id="32b2c-131">No</span></span>  <br/> | <span data-ttu-id="32b2c-p105">如果你没有指定密码，将向用户帐户分配一个随机密码，且该密码将显示在命令结果中。如果你指定了密码，则需要是以下三种类型的 8 到 16 位 ASCII 文本字符：小写字母、大写字母、数字和符号。</span><span class="sxs-lookup"><span data-stu-id="32b2c-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="32b2c-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="32b2c-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="32b2c-135">否</span><span class="sxs-lookup"><span data-stu-id="32b2c-135">No</span></span>  <br/> |<span data-ttu-id="32b2c-p106">这是一个由两位字母组成的有效 ISO 3166-1 国家/地区代码。例如，US 代表美国，FR 代表法国。请务必提供此值，因为某些 Office 365 服务在某些国家不可用，因此不能为用户帐户分配许可证，除非该帐户已配置此值。有关详细信息，请参阅[关于许可证限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="32b2c-p106">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="32b2c-140">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="32b2c-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="32b2c-141">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="32b2c-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="32b2c-142">连接后，使用下列语法创建个人帐户：</span><span class="sxs-lookup"><span data-stu-id="32b2c-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="32b2c-143">本示例为名为 Caleb Sills 的美国用户创建一个帐户：</span><span class="sxs-lookup"><span data-stu-id="32b2c-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="32b2c-144">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="32b2c-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="32b2c-145">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="32b2c-145">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="32b2c-146">创建单个用户帐户</span><span class="sxs-lookup"><span data-stu-id="32b2c-146">Create an individual user account</span></span>

<span data-ttu-id="32b2c-147">若要创建单个帐户，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="32b2c-147">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

<span data-ttu-id="32b2c-148">若要列出可用的许可计划名称，请使用此命令：</span><span class="sxs-lookup"><span data-stu-id="32b2c-148">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="32b2c-149">本示例为美国用户 Caleb Sills 创建一个帐户并通过 `contoso:ENTERPRISEPACK` (Office 365 企业版 E3) 许可计划分配了一个许可证。</span><span class="sxs-lookup"><span data-stu-id="32b2c-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="32b2c-150">创建多个用户帐户</span><span class="sxs-lookup"><span data-stu-id="32b2c-150">Create multiple user accounts</span></span>

1. <span data-ttu-id="32b2c-p107">创建包含所需用户帐户信息的逗号分隔值 (CSV) 文件。例如：</span><span class="sxs-lookup"><span data-stu-id="32b2c-p107">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="32b2c-153">虽然列名称及其在 CSV 文件的第一行中的顺序是任意的，但请确保文件其余部分中的数据与列名称的顺序相匹配，并使用列名称作为 Office 365 PowerShell 命令中的参数值。</span><span class="sxs-lookup"><span data-stu-id="32b2c-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="32b2c-154">使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="32b2c-154">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="32b2c-155">本示例从名为 C:\My Documents\NewAccounts.csv 的文件创建用户帐户，并将结果记录在名为 C:\My Documents\NewAccountResults.csv 的文件中</span><span class="sxs-lookup"><span data-stu-id="32b2c-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="32b2c-p108">查看输出文件以查看结果。我们没有指定密码，这样便于在输出文件中显示 Office 365 生成的随机密码。</span><span class="sxs-lookup"><span data-stu-id="32b2c-p108">Review the output file to see the results. We didn't specify passwords, so the random passwords that Office 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="32b2c-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32b2c-158">See also</span></span>

[<span data-ttu-id="32b2c-159">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="32b2c-159">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="32b2c-160">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="32b2c-160">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="32b2c-161">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="32b2c-161">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
