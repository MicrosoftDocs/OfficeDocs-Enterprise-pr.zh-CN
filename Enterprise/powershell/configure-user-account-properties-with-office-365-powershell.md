---
title: 使用 Office 365 PowerShell 配置用户帐户的属性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 摘要：使用 Office 365 PowerShell 配置 Office 365 租户中单个或多个用户帐户的属性。
ms.openlocfilehash: b9cd529cd5881d522285ff43a60e954bc9ebd193
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072234"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="d03a1-103">使用 Office 365 PowerShell 配置用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="d03a1-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="d03a1-104">虽然您可以使用 Microsoft 365 管理中心来配置 Office 365 租户的用户帐户的属性，但您也可以使用 Office 365 PowerShell 并执行管理中心无法执行的某些操作。</span><span class="sxs-lookup"><span data-stu-id="d03a1-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d03a1-105">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="d03a1-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d03a1-106">若要为使用 Azure Active Directory PowerShell for Graph 模块的用户帐户配置属性，请使用[AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="d03a1-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="d03a1-107">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="d03a1-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d03a1-108">更改特定用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="d03a1-108">Change properties for a specific user account</span></span>

<span data-ttu-id="d03a1-109">使用 **-ObjectID**参数标识帐户，并使用其他参数设置或更改特定属性。</span><span class="sxs-lookup"><span data-stu-id="d03a1-109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="d03a1-110">下面列出了最常见的参数。</span><span class="sxs-lookup"><span data-stu-id="d03a1-110">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d03a1-111">-部门 "\<部门名称>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d03a1-112">-DisplayName "\<full user name>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d03a1-113">-FacsimilieTelephoneNumber "\<fax number>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="d03a1-114">-GivenName "\<user first name>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="d03a1-115">-姓 "\<user last name>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="d03a1-116">-移动 "\<移动电话号码>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d03a1-117">-JobTitle "\<职务>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="d03a1-118">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d03a1-119">-StreetAddress "\<街道地址>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d03a1-120">-市/\<县 "城市名称>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d03a1-121">-State "\<state name>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d03a1-122">-邮政编码 "\<>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d03a1-123">-国家/\<地区 "国家/地区名称>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d03a1-124">-TelephoneNumber "\<office 电话号码>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d03a1-125">-UsageLocation "\<2 个字符的国家或地区代码>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d03a1-126">这是 ISO 3166-1 alpha-2 （A2）两个字母的国家/地区代码。</span><span class="sxs-lookup"><span data-stu-id="d03a1-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d03a1-127">有关其他参数，请参阅[AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。</span><span class="sxs-lookup"><span data-stu-id="d03a1-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="d03a1-128">若要显示用户帐户的用户主体名称，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d03a1-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="d03a1-129">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="d03a1-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d03a1-130">获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d03a1-131">按字母顺序（**排序 UserPrincipalName** ）对用户主体名称列表进行排序，并将其发送到**|** 下一个命令（）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d03a1-132">仅显示每个帐户的 "用户主体名称" 属性（**选择 "UserPrincipalName** "）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="d03a1-133">一次显示一屏（**更多**）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d03a1-134">此命令将列出你的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="d03a1-134">This command will list all of your accounts.</span></span> <span data-ttu-id="d03a1-135">如果要根据其显示名称（名和姓）显示帐户的用户主体名称，请填写下面的 **$userName**变量（删除\<和 > 字符），然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d03a1-135">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d03a1-136">本示例显示名为 Caleb Sills 的用户帐户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="d03a1-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d03a1-137">通过使用 **$upn**变量，可以根据各个帐户的显示名称对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="d03a1-137">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="d03a1-138">下面的示例展示了如何将 Belinda Newman 的使用位置设置为华北，但指定了她的显示名称而不是她的用户主体名称：</span><span class="sxs-lookup"><span data-stu-id="d03a1-138">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d03a1-139">更改所有用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="d03a1-139">Change properties for all user accounts</span></span>

<span data-ttu-id="d03a1-140">若要更改所有用户的属性，您可以使用**AzureADUser**和**AzureADUser** cmdlet 的组合。</span><span class="sxs-lookup"><span data-stu-id="d03a1-140">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="d03a1-141">下面的示例将所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="d03a1-141">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d03a1-142">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="d03a1-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d03a1-143">获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d03a1-144">将用户位置设置为 "法国 **" （AzureADUser-UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d03a1-145">更改特定用户帐户集的属性</span><span class="sxs-lookup"><span data-stu-id="d03a1-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d03a1-146">若要更改特定用户帐户集的属性，您可以使用**AzureADUser**、 **Where**和**AzureADUser** cmdlet 的组合。</span><span class="sxs-lookup"><span data-stu-id="d03a1-146">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="d03a1-147">下面的示例将会计部门的所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="d03a1-147">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d03a1-148">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="d03a1-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d03a1-149">获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d03a1-150">查找其 "部门" 属性设置为 "记帐" 的所有用户帐户（**其中 {$ _）。部门-eq "记帐"}** ）并将生成的信息发送到下一个命令**|** （）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d03a1-151">将用户位置设置为 "法国 **" （AzureADUser-UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d03a1-152">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="d03a1-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d03a1-153">若要使用适用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块配置用户帐户的属性，请使用**get-msoluser** cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="d03a1-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="d03a1-154">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="d03a1-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="d03a1-155">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="d03a1-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d03a1-156">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="d03a1-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d03a1-157">更改特定用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="d03a1-157">Change properties for a specific user account</span></span>

<span data-ttu-id="d03a1-158">若要配置特定用户帐户的属性，请使用[get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="d03a1-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="d03a1-159">您可以使用 **-UserPrincipalName**参数标识帐户，并使用其他参数设置或更改特定属性。</span><span class="sxs-lookup"><span data-stu-id="d03a1-159">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="d03a1-160">下面是最常见的参数的列表。</span><span class="sxs-lookup"><span data-stu-id="d03a1-160">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d03a1-161">-市/\<县 "城市名称>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d03a1-162">-国家/\<地区 "国家/地区名称>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d03a1-163">-部门 "\<部门名称>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d03a1-164">-DisplayName "\<full user name>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d03a1-165">-Fax "\<fax 号码>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="d03a1-166">-FirstName "\<user first name>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="d03a1-167">-LastName "\<user last name>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="d03a1-168">-MobilePhone "\<移动电话号码>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d03a1-169">-Office "\<office 位置>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="d03a1-170">-PhoneNumber "\<office 电话号码>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d03a1-171">-邮政编码 "\<>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d03a1-172">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d03a1-173">-State "\<state name>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d03a1-174">-StreetAddress "\<街道地址>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d03a1-175">-Title "\<title name>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="d03a1-176">-UsageLocation "\<2 个字符的国家或地区代码>"</span><span class="sxs-lookup"><span data-stu-id="d03a1-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d03a1-177">这是 ISO 3166-1 alpha-2 （A2）两个字母的国家/地区代码。</span><span class="sxs-lookup"><span data-stu-id="d03a1-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d03a1-178">有关其他参数，请参阅[get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) 。</span><span class="sxs-lookup"><span data-stu-id="d03a1-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="d03a1-179">若要查看所有用户的用户主体名称，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d03a1-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="d03a1-180">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="d03a1-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d03a1-181">获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d03a1-182">按字母顺序（**排序 UserPrincipalName** ）对用户主体名称列表进行排序，并将其发送到**|** 下一个命令（）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d03a1-183">仅显示每个帐户的 "用户主体名称" 属性（**选择 "UserPrincipalName** "）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="d03a1-184">一次显示一屏（**更多**）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d03a1-185">此命令将列出你的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="d03a1-185">This command will list all of your accounts.</span></span> <span data-ttu-id="d03a1-186">如果要根据其显示名称（名和姓）显示帐户的用户主体名称，请填写下面的 **$userName**变量（删除\<和 > 字符），然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d03a1-186">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d03a1-187">本示例显示名为 Caleb Sills 的用户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="d03a1-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d03a1-188">通过使用 **$upn**变量，可以根据各个帐户的显示名称对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="d03a1-188">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="d03a1-189">下面的示例展示了如何将 Belinda Newman 的使用位置设置为华北，但指定了她的显示名称而不是她的用户主体名称：</span><span class="sxs-lookup"><span data-stu-id="d03a1-189">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d03a1-190">更改所有用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="d03a1-190">Change properties for all user accounts</span></span>

<span data-ttu-id="d03a1-p110">要更改所有用户的属性，您可以将 **Get-MsolUser** 和 **Set-MsolUser** cmdlet 结合使用。下面的示例将所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="d03a1-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d03a1-193">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="d03a1-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d03a1-194">获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d03a1-195">将用户位置设置为 "法国 **" （get-msoluser-UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d03a1-196">更改特定用户帐户集的属性</span><span class="sxs-lookup"><span data-stu-id="d03a1-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d03a1-197">若要更改特定用户帐户集的属性，您可以使用**get-msoluser**、 **Where**和**get-msoluser** cmdlet 的组合。</span><span class="sxs-lookup"><span data-stu-id="d03a1-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="d03a1-198">下面的示例将会计部门的所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="d03a1-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d03a1-199">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="d03a1-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d03a1-200">获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d03a1-201">查找其 "部门" 属性设置为 "记帐" 的所有用户帐户（**其中 {$ _）。部门-eq "记帐"}** ）并将生成的信息发送到下一个命令**|** （）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d03a1-202">将用户位置设置为 "法国 **" （get-msoluser-UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="d03a1-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="d03a1-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d03a1-203">See also</span></span>

[<span data-ttu-id="d03a1-204">使用 Office 365 PowerShell 管理用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="d03a1-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d03a1-205">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="d03a1-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d03a1-206">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="d03a1-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
