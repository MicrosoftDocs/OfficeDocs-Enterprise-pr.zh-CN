---
title: 使用 Office 365 PowerShell 配置用户帐户属性
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 摘要： 使用 Office 365 PowerShell，可以在 Office 365 租户中配置的单个或多个用户帐户的属性。
ms.openlocfilehash: 4db63482fdcc1d6cb186e663fd55c13186b33813
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546483"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="da644-103">使用 Office 365 PowerShell 配置用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="da644-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="da644-104">**摘要：** 使用 Office 365 PowerShell 在 Office 365 租户中配置的单个或多个用户帐户的属性。</span><span class="sxs-lookup"><span data-stu-id="da644-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="da644-105">尽管可以使用 Office 365 管理中心配置 Office 365 租户的用户帐户的属性，还可以使用 Office 365 PowerShell 中，并执行某些操作不能在 Office 365 管理中心中。</span><span class="sxs-lookup"><span data-stu-id="da644-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="da644-106">使用 Azure Active Directory PowerShell 图模块</span><span class="sxs-lookup"><span data-stu-id="da644-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="da644-107">要使用图模块 Azure Active Directory PowerShell 配置用户帐户的属性，您使用[集 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="da644-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="da644-108">第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="da644-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="da644-109">更改特定的用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="da644-109">Change properties for a specific user account</span></span>

<span data-ttu-id="da644-p101">您使用 **-ObjectID**参数标识的帐户和设置或更改与其他参数的特定属性。下面是最常见的参数的列表。</span><span class="sxs-lookup"><span data-stu-id="da644-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="da644-112">部门"\<部门名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="da644-113">-DisplayName"\<完整的用户名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="da644-114">-FacsimilieTelephoneNumber"\<传真号码 >"</span><span class="sxs-lookup"><span data-stu-id="da644-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="da644-115">-GivenName"\<用户名字 >"</span><span class="sxs-lookup"><span data-stu-id="da644-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="da644-116">-Surname"\<用户姓氏 >"</span><span class="sxs-lookup"><span data-stu-id="da644-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="da644-117">-移动"\<的移动电话号码 >"</span><span class="sxs-lookup"><span data-stu-id="da644-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="da644-118">-JobTitle"\<职务 >"</span><span class="sxs-lookup"><span data-stu-id="da644-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="da644-119">-PreferredLanguage"\<语言 >"</span><span class="sxs-lookup"><span data-stu-id="da644-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="da644-120">-StreetAddress"\<街道地址 >"</span><span class="sxs-lookup"><span data-stu-id="da644-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="da644-121">--市/县"\<城市名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="da644-122">-状态"\<状态名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="da644-123">-PostalCode"\<邮政编码 >"</span><span class="sxs-lookup"><span data-stu-id="da644-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="da644-124">-国家"\<国家/地区名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="da644-125">-TelephoneNumber"\<办公室电话号码 >"</span><span class="sxs-lookup"><span data-stu-id="da644-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="da644-126">-UsageLocation"\<2 个字符的国家或地区代码 >"</span><span class="sxs-lookup"><span data-stu-id="da644-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="da644-127">这是 ISO 3166-1 alpha-2 (A2) 两个字母的国家或地区代码。</span><span class="sxs-lookup"><span data-stu-id="da644-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="da644-128">其他参数，请参阅[设置 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。</span><span class="sxs-lookup"><span data-stu-id="da644-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="da644-129">若要显示您的用户帐户的用户主体名称，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="da644-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="da644-130">此命令指示 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="da644-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="da644-131">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="da644-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="da644-132">按字母顺序排序的用户主体名称的列表 ( **Sort 对象 UserPrincipalName** ) 并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="da644-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="da644-133">显示刚 ( **Select-object UserPrincipalName** ) 的每个帐户的用户主体名称属性。</span><span class="sxs-lookup"><span data-stu-id="da644-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="da644-134">将其显示在一个屏幕 （**详细**） 一次。</span><span class="sxs-lookup"><span data-stu-id="da644-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="da644-p102">此命令将列出所有帐户。如果您想要显示用户主体名称的基于其显示帐户名 （名字和姓氏名称）、 填写下面 **$userName**变量 (删除\<和 > 字符)，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="da644-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="da644-137">本示例显示了用户主体名称的用户帐户和 Caleb Sills 的显示名称。</span><span class="sxs-lookup"><span data-stu-id="da644-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="da644-p103">通过使用 **$upn**变量，您可以对基于其显示名称的单个帐户进行更改。下面是一个示例将 Belinda Newman 的使用位置设置为法国，但指定其显示名称，而不是其用户主体名称：</span><span class="sxs-lookup"><span data-stu-id="da644-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="da644-140">更改为所有用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="da644-140">Change properties for all user accounts</span></span>

<span data-ttu-id="da644-p104">若要更改的所有用户属性，可以使用**Get-AzureADUser**和**设置 AzureADUser** cmdlet 的组合。以下示例更改为法国的所有用户的使用位置：</span><span class="sxs-lookup"><span data-stu-id="da644-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="da644-143">此命令指示 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="da644-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="da644-144">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="da644-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="da644-145">设置用户位置为法国 (**集 AzureADUser UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="da644-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="da644-146">更改一组特定的用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="da644-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="da644-p105">若要更改的一组特定的用户帐户属性，可以使用**Get-AzureADUser**，**其中**，而**设置 AzureADUser** cmdlet 的组合。下面的示例将更改为法国会计部门中的所有用户的使用位置：</span><span class="sxs-lookup"><span data-stu-id="da644-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="da644-149">此命令指示 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="da644-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="da644-150">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="da644-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="da644-151">查找所有其部门属性设置为"会计"的用户帐户 (**其中 {$_。部门-eq"Accounting"}** ) 并将生成的信息发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="da644-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="da644-152">设置用户位置为法国 (**集 AzureADUser UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="da644-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="da644-153">使用 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="da644-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="da644-154">若要使用 Microsoft Azure Active Directory 模块用于 Windows PowerShell 配置用户帐户的属性，您使用 Set-msoluser cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="da644-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="da644-155">第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="da644-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="da644-156">更改特定的用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="da644-156">Change properties for a specific user account</span></span>

<span data-ttu-id="da644-157">若要配置的特定用户帐户属性，您使用[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="da644-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="da644-p106">您使用 **-UserPrincipalName**参数标识的帐户和设置或更改与其他参数的特定属性。下面是最常见的参数的列表。</span><span class="sxs-lookup"><span data-stu-id="da644-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="da644-160">--市/县"\<城市名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="da644-161">-国家"\<国家/地区名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="da644-162">部门"\<部门名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="da644-163">-DisplayName"\<完整的用户名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="da644-164">-传真"\<传真号码 >"</span><span class="sxs-lookup"><span data-stu-id="da644-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="da644-165">-FirstName"\<用户名字 >"</span><span class="sxs-lookup"><span data-stu-id="da644-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="da644-166">-LastName"\<用户姓氏 >"</span><span class="sxs-lookup"><span data-stu-id="da644-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="da644-167">-MobilePhone"\<的移动电话号码 >"</span><span class="sxs-lookup"><span data-stu-id="da644-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="da644-168">Office"\<办公地点 >"</span><span class="sxs-lookup"><span data-stu-id="da644-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="da644-169">-电话号码"\<办公室电话号码 >"</span><span class="sxs-lookup"><span data-stu-id="da644-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="da644-170">-PostalCode"\<邮政编码 >"</span><span class="sxs-lookup"><span data-stu-id="da644-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="da644-171">-PreferredLanguage"\<语言 >"</span><span class="sxs-lookup"><span data-stu-id="da644-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="da644-172">-状态"\<状态名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="da644-173">-StreetAddress"\<街道地址 >"</span><span class="sxs-lookup"><span data-stu-id="da644-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="da644-174">-Title"\<标题名称 >"</span><span class="sxs-lookup"><span data-stu-id="da644-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="da644-175">-UsageLocation"\<2 个字符的国家或地区代码 >"</span><span class="sxs-lookup"><span data-stu-id="da644-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="da644-176">这是 ISO 3166-1 alpha-2 (A2) 两个字母的国家或地区代码。</span><span class="sxs-lookup"><span data-stu-id="da644-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="da644-177">其他参数，请参阅[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="da644-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="da644-178">若要查看您的所有用户的用户主体名称，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="da644-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="da644-179">此命令指示 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="da644-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="da644-180">获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="da644-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="da644-181">按字母顺序排序的用户主体名称的列表 ( **Sort 对象 UserPrincipalName** ) 并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="da644-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="da644-182">显示刚 ( **Select-object UserPrincipalName** ) 的每个帐户的用户主体名称属性。</span><span class="sxs-lookup"><span data-stu-id="da644-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="da644-183">将其显示在一个屏幕 （**详细**） 一次。</span><span class="sxs-lookup"><span data-stu-id="da644-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="da644-p107">此命令将列出所有帐户。如果您想要显示用户主体名称的基于其显示帐户名 （名字和姓氏名称）、 填写下面 **$userName**变量 (删除\<和 > 字符)，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="da644-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="da644-186">本示例显示名为 Caleb Sills 用户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="da644-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="da644-p108">通过使用 **$upn**变量，您可以对基于其显示名称的单个帐户进行更改。下面是一个示例将 Belinda Newman 的使用位置设置为法国，但指定其显示名称，而不是其用户主体名称：</span><span class="sxs-lookup"><span data-stu-id="da644-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="da644-189">更改为所有用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="da644-189">Change properties for all user accounts</span></span>

<span data-ttu-id="da644-p109">要更改所有用户的属性，您可以将 **Get-MsolUser** 和 **Set-MsolUser** cmdlet 结合使用。下面的示例将所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="da644-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="da644-192">此命令指示 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="da644-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="da644-193">获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="da644-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="da644-194">设置用户位置为法国 ( **Set-msoluser-UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="da644-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="da644-195">更改一组特定的用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="da644-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="da644-p110">若要更改的一组特定的用户帐户属性，可以使用**Get-msoluser**、 **Where-object**和**Set-msoluser** cmdlet 的组合。下面的示例将更改为法国会计部门中的所有用户的使用位置：</span><span class="sxs-lookup"><span data-stu-id="da644-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="da644-198">此命令指示 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="da644-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="da644-199">获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="da644-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="da644-200">查找所有的用户帐户的设置为"会计"的部门属性 ( **Where-object {$_。部门-eq"Accounting"}** ) 并将生成的信息发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="da644-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="da644-201">设置用户位置为法国 ( **Set-msoluser-UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="da644-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="da644-202">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da644-202">See also</span></span>

[<span data-ttu-id="da644-203">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="da644-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="da644-204">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="da644-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="da644-205">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="da644-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
