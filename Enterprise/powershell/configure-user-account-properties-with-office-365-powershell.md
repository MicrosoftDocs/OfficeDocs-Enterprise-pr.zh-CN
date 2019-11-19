---
title: 使用 Office 365 PowerShell 配置用户帐户的属性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
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
ms.openlocfilehash: 94596326c9d52b4010f6e9baf67fe3c7a12399be
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "38706989"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="a73f6-103">使用 Office 365 PowerShell 配置用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="a73f6-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="a73f6-104">**摘要：** 使用 Office 365 PowerShell 配置 Office 365 租户中单个或多个用户帐户的属性。</span><span class="sxs-lookup"><span data-stu-id="a73f6-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="a73f6-105">虽然您可以使用 Microsoft 365 管理中心来配置 Office 365 租户的用户帐户的属性，但您也可以使用 Office 365 PowerShell 并执行管理中心无法执行的某些操作。</span><span class="sxs-lookup"><span data-stu-id="a73f6-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="a73f6-106">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="a73f6-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="a73f6-107">若要为使用 Azure Active Directory PowerShell for Graph 模块的用户帐户配置属性，请使用[AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="a73f6-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="a73f6-108">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="a73f6-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="a73f6-109">更改特定用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="a73f6-109">Change properties for a specific user account</span></span>

<span data-ttu-id="a73f6-110">使用 **-ObjectID**参数标识帐户，并使用其他参数设置或更改特定属性。</span><span class="sxs-lookup"><span data-stu-id="a73f6-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="a73f6-111">下面列出了最常见的参数。</span><span class="sxs-lookup"><span data-stu-id="a73f6-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="a73f6-112">-部门 "\<部门名称>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="a73f6-113">-DisplayName "\<full user name>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="a73f6-114">-FacsimilieTelephoneNumber "\<fax number>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="a73f6-115">-GivenName "\<user first name>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="a73f6-116">-姓 "\<user last name>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="a73f6-117">-移动 "\<移动电话号码>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="a73f6-118">-JobTitle "\<职务>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="a73f6-119">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="a73f6-120">-StreetAddress "\<街道地址>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="a73f6-121">-市/\<县 "城市名称>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="a73f6-122">-State "\<state name>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="a73f6-123">-邮政编码 "\<>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="a73f6-124">-国家/\<地区 "国家/地区名称>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="a73f6-125">-TelephoneNumber "\<office 电话号码>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="a73f6-126">-UsageLocation "\<2 个字符的国家或地区代码>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="a73f6-127">这是 ISO 3166-1 alpha-2 （A2）两个字母的国家/地区代码。</span><span class="sxs-lookup"><span data-stu-id="a73f6-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="a73f6-128">有关其他参数，请参阅[AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。</span><span class="sxs-lookup"><span data-stu-id="a73f6-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="a73f6-129">若要显示用户帐户的用户主体名称，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="a73f6-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="a73f6-130">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a73f6-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a73f6-131">获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a73f6-132">按字母顺序（**排序对象 UserPrincipalName** ）对用户主体名称列表进行排序，并将其发送到下**|** 一个命令（）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a73f6-133">仅显示每个帐户（**选择-对象 UserPrincipalName** ）的用户主体名称属性。</span><span class="sxs-lookup"><span data-stu-id="a73f6-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="a73f6-134">一次显示一屏（**更多**）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="a73f6-135">此命令将列出你的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="a73f6-135">This command will list all of your accounts.</span></span> <span data-ttu-id="a73f6-136">如果要根据其显示名称（名和姓）显示帐户的用户主体名称，请填写下面的 **$userName**变量（删除\<和 > 字符），然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a73f6-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a73f6-137">本示例显示名为 Caleb Sills 的用户帐户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="a73f6-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a73f6-138">通过使用 **$upn**变量，可以根据各个帐户的显示名称对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="a73f6-138">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="a73f6-139">下面的示例展示了如何将 Belinda Newman 的使用位置设置为华北，但指定了她的显示名称而不是她的用户主体名称：</span><span class="sxs-lookup"><span data-stu-id="a73f6-139">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="a73f6-140">更改所有用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="a73f6-140">Change properties for all user accounts</span></span>

<span data-ttu-id="a73f6-141">若要更改所有用户的属性，您可以使用**AzureADUser**和**AzureADUser** cmdlet 的组合。</span><span class="sxs-lookup"><span data-stu-id="a73f6-141">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="a73f6-142">下面的示例将所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="a73f6-142">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="a73f6-143">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a73f6-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a73f6-144">获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a73f6-145">将用户位置设置为 "法国 **" （AzureADUser-UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="a73f6-146">更改特定用户帐户集的属性</span><span class="sxs-lookup"><span data-stu-id="a73f6-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="a73f6-147">若要更改特定用户帐户集的属性，您可以使用**AzureADUser**、 **Where**和**AzureADUser** cmdlet 的组合。</span><span class="sxs-lookup"><span data-stu-id="a73f6-147">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="a73f6-148">下面的示例将会计部门的所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="a73f6-148">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="a73f6-149">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a73f6-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a73f6-150">获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a73f6-151">查找其 "部门" 属性设置为 "记帐" 的所有用户帐户（**其中 {$ _）。部门-eq "记帐"}** ）并将生成的信息发送到下一个命令**|** （）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a73f6-152">将用户位置设置为 "法国 **" （AzureADUser-UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a73f6-153">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="a73f6-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a73f6-154">若要使用适用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块配置用户帐户的属性，请使用 Get-msoluser cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="a73f6-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="a73f6-155">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="a73f6-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="a73f6-156">更改特定用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="a73f6-156">Change properties for a specific user account</span></span>

<span data-ttu-id="a73f6-157">若要配置特定用户帐户的属性，请使用[get-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="a73f6-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="a73f6-158">您可以使用 **-UserPrincipalName**参数标识帐户，并使用其他参数设置或更改特定属性。</span><span class="sxs-lookup"><span data-stu-id="a73f6-158">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="a73f6-159">下面是最常见的参数的列表。</span><span class="sxs-lookup"><span data-stu-id="a73f6-159">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="a73f6-160">-市/\<县 "城市名称>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="a73f6-161">-国家/\<地区 "国家/地区名称>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="a73f6-162">-部门 "\<部门名称>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="a73f6-163">-DisplayName "\<full user name>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="a73f6-164">-Fax "\<fax 号码>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="a73f6-165">-FirstName "\<user first name>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="a73f6-166">-LastName "\<user last name>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="a73f6-167">-MobilePhone "\<移动电话号码>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="a73f6-168">-Office "\<office 位置>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="a73f6-169">-PhoneNumber "\<office 电话号码>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="a73f6-170">-邮政编码 "\<>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="a73f6-171">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="a73f6-172">-State "\<state name>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="a73f6-173">-StreetAddress "\<街道地址>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="a73f6-174">-Title "\<title name>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="a73f6-175">-UsageLocation "\<2 个字符的国家或地区代码>"</span><span class="sxs-lookup"><span data-stu-id="a73f6-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="a73f6-176">这是 ISO 3166-1 alpha-2 （A2）两个字母的国家/地区代码。</span><span class="sxs-lookup"><span data-stu-id="a73f6-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="a73f6-177">有关其他参数，请参阅[get-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="a73f6-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

<span data-ttu-id="a73f6-178">若要查看所有用户的用户主体名称，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="a73f6-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="a73f6-179">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a73f6-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a73f6-180">获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a73f6-181">按字母顺序（**排序对象 UserPrincipalName** ）对用户主体名称列表进行排序，并将其发送到下**|** 一个命令（）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a73f6-182">仅显示每个帐户（**选择-对象 UserPrincipalName** ）的用户主体名称属性。</span><span class="sxs-lookup"><span data-stu-id="a73f6-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="a73f6-183">一次显示一屏（**更多**）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="a73f6-184">此命令将列出你的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="a73f6-184">This command will list all of your accounts.</span></span> <span data-ttu-id="a73f6-185">如果要根据其显示名称（名和姓）显示帐户的用户主体名称，请填写下面的 **$userName**变量（删除\<和 > 字符），然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a73f6-185">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a73f6-186">本示例显示名为 Caleb Sills 的用户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="a73f6-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a73f6-187">通过使用 **$upn**变量，可以根据各个帐户的显示名称对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="a73f6-187">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="a73f6-188">下面的示例展示了如何将 Belinda Newman 的使用位置设置为华北，但指定了她的显示名称而不是她的用户主体名称：</span><span class="sxs-lookup"><span data-stu-id="a73f6-188">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="a73f6-189">更改所有用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="a73f6-189">Change properties for all user accounts</span></span>

<span data-ttu-id="a73f6-p109">要更改所有用户的属性，您可以将 **Get-MsolUser** 和 **Set-MsolUser** cmdlet 结合使用。下面的示例将所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="a73f6-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="a73f6-192">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a73f6-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a73f6-193">获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a73f6-194">将用户位置设置为 "法国 **" （get-msoluser-UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="a73f6-195">更改特定用户帐户集的属性</span><span class="sxs-lookup"><span data-stu-id="a73f6-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="a73f6-196">若要更改一组特定用户帐户的属性，您可以使用**get-msoluser**、 **Where-Object**和**get-msoluser** cmdlet 的组合。</span><span class="sxs-lookup"><span data-stu-id="a73f6-196">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="a73f6-197">下面的示例将会计部门的所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="a73f6-197">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="a73f6-198">此命令指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a73f6-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a73f6-199">获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a73f6-200">查找其 "部门" 属性设置为 "记帐" 的所有用户帐户（**其中-对象 {$ _）。部门-eq "记帐"}** ）并将生成的信息发送到下一个命令**|** （）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a73f6-201">将用户位置设置为 "法国 **" （get-msoluser-UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="a73f6-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="a73f6-202">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a73f6-202">See also</span></span>

[<span data-ttu-id="a73f6-203">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="a73f6-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="a73f6-204">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="a73f6-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a73f6-205">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="a73f6-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
