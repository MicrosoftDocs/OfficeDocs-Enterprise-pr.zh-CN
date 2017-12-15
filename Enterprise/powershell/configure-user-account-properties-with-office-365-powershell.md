---
title: "使用 Office 365 PowerShell 配置用户帐户的属性"
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
- DecEntMigration
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "摘要： 使用 Office 365 PowerShell Office 365 租户中配置单个或多个用户帐户的属性。"
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="6c0ff-103">使用 Office 365 PowerShell 配置用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6c0ff-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="6c0ff-104">**摘要：**使用 Office 365 PowerShell Office 365 租户中配置单个或多个用户帐户的属性。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="6c0ff-105">虽然您可以使用 Office 365 管理中心配置 Office 365 租户的用户帐户的属性，您还可以使用 Office 365 PowerShell 并做一些 Office 365 管理中心不能。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="6c0ff-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="6c0ff-106">Before you begin</span></span>

<span data-ttu-id="6c0ff-p101">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="6c0ff-109">更改特定用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6c0ff-109">Change properties for a specific user account</span></span>

<span data-ttu-id="6c0ff-p102">要配置为使用特定用户帐户的属性，请使用[组 MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet 并指定要设置或更改的属性。本示例命令将更改为法国 Belinda Newman 使用位置：</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="6c0ff-p103">您使用**的范围内**参数识别帐户并设置或更改使用附加参数的特定属性。这是最常见的参数列表。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="6c0ff-114">-市/县"\<城市名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="6c0ff-115">-国家"\<国家/地区名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="6c0ff-116">-部门"\<部门名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="6c0ff-117">-显示名称"\<完整的用户名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="6c0ff-118">-传真"\<传真号码 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="6c0ff-119">名字"\<用户名字 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="6c0ff-120">姓氏的"\<用户姓氏 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="6c0ff-121">-MobilePhone"\<的移动电话号码 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="6c0ff-122">机构"\<办公地点 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="6c0ff-123">-电话号码"\<办公室电话号码 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="6c0ff-124">邮政编码的"\<邮政编码 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="6c0ff-125">-PreferredLanguage"\<语言 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="6c0ff-126">-国家"\<状态名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="6c0ff-127">-街道地址"\<街道地址 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="6c0ff-128">的标题"\<标题名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="6c0ff-129">-UsageLocation"\<2 个字符的国家或地区代码 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="6c0ff-130">这是 ISO 3166-1 alpha 2 (A2) 两个字母的国家或地区代码。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="6c0ff-131">额外的参数，请参阅[设置 MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="6c0ff-132">若要查看所有用户的用户主体名称，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="6c0ff-133">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6c0ff-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="6c0ff-134">获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c0ff-135">按字母顺序排序列表中的用户主要名称 ( **Sort 对象范围内**) 并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c0ff-136">显示只需为每个帐户 (**选择对象的范围内**) 的用户主体名称属性。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="6c0ff-137">它们一屏一次显示 （**更多**）。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="6c0ff-p104">此命令将列出您的所有帐户。如果您想要显示基于其显示名称帐户的用户主体名称 （第一个和最后一个名称），填入下面的**$userName**变量 (删除\<和 > 字符)，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="6c0ff-140">本示例显示名为 Caleb 窗台用户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="6c0ff-p105">通过使用**$upn**变量，您可以到基于其显示名称的个人帐户进行更改。下面是一个示例设置 Belinda Newman 使用位置到法国，但指定她显示名称，而不是她的用户主体名称：</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="6c0ff-143">更改对所有用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6c0ff-143">Change properties for all user accounts</span></span>

<span data-ttu-id="6c0ff-p106">若要更改所有用户的属性，可以使用**Get MsolUser**和**一组 MsolUser** cmdlet 的组合。下面的示例更改为法国所有用户的使用位置：</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="6c0ff-146">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6c0ff-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="6c0ff-147">获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c0ff-148">将用户的位置设置为法国 (**集 MsolUser UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="6c0ff-149">更改一组特定的用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6c0ff-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="6c0ff-p107">若要更改一组特定的用户帐户的属性，可以使用**Get MsolUser**、**位置对象**和**一组 MsolUser** cmdlet 的组合。下面的示例更改为法国会计部门的所有用户的使用位置：</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="6c0ff-152">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6c0ff-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="6c0ff-153">获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c0ff-154">找到所有的用户帐户具有的部门属性设置为"会计"(**位置对象 {$_。部门 eq"记帐"}** ) 并将得到的信息发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c0ff-155">将用户的位置设置为法国 (**集 MsolUser UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="6c0ff-156">它们一屏一次显示 （**更多**）。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="6c0ff-157">使用 Azure 活动目录 V2 PowerShell 模块可配置用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="6c0ff-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="6c0ff-p108">要使用 Azure 活动目录 V2 PowerShell 模块配置用户帐户的属性，使用[集 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet 并指定要设置或更改的属性。但首先，您必须连接到您的订购。有关说明，请参阅[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="6c0ff-161">更改特定用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6c0ff-161">Change properties for a specific user account</span></span>

<span data-ttu-id="6c0ff-162">本示例命令将更改为法国 Belinda Newman 使用位置：</span><span class="sxs-lookup"><span data-stu-id="6c0ff-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="6c0ff-p109">您使用**的对象 Id**参数识别帐户并设置或更改使用附加参数的特定属性。这是最常见的参数列表。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="6c0ff-165">-部门"\<部门名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="6c0ff-166">-显示名称"\<完整的用户名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="6c0ff-167">-FacsimilieTelephoneNumber"\<传真号码 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="6c0ff-168">-GivenName"\<用户名字 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="6c0ff-169">-Surname"\<用户姓氏 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="6c0ff-170">-移动"\<的移动电话号码 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="6c0ff-171">-职务"\<职务 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="6c0ff-172">-PreferredLanguage"\<语言 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="6c0ff-173">-街道地址"\<街道地址 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="6c0ff-174">-市/县"\<城市名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="6c0ff-175">-国家"\<状态名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="6c0ff-176">邮政编码的"\<邮政编码 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="6c0ff-177">-国家"\<国家/地区名称 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="6c0ff-178">-TelephoneNumber"\<办公室电话号码 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="6c0ff-179">-UsageLocation"\<2 个字符的国家或地区代码 >"</span><span class="sxs-lookup"><span data-stu-id="6c0ff-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="6c0ff-180">这是 ISO 3166-1 alpha 2 (A2) 两个字母的国家或地区代码。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="6c0ff-181">额外的参数，请参阅[设置 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="6c0ff-182">若要显示您的用户帐户的用户主体名称，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="6c0ff-183">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6c0ff-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="6c0ff-184">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c0ff-185">按字母顺序排序列表中的用户主要名称 ( **Sort 对象范围内**) 并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c0ff-186">显示只需为每个帐户 (**选择对象的范围内**) 的用户主体名称属性。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="6c0ff-187">它们一屏一次显示 （**更多**）。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="6c0ff-p110">此命令将列出您的所有帐户。如果您想要显示基于其显示名称帐户的用户主体名称 （第一个和最后一个名称），填入下面的**$userName**变量 (删除\<和 > 字符)，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="6c0ff-190">本示例显示名为 Caleb 窗台用户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="6c0ff-p111">通过使用**$upn**变量，您可以到基于其显示名称的个人帐户进行更改。下面是一个示例设置 Belinda Newman 使用位置到法国，但指定她显示名称，而不是她的用户主体名称：</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="6c0ff-193">更改对所有用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6c0ff-193">Change properties for all user accounts</span></span>

<span data-ttu-id="6c0ff-p112">若要更改所有用户的属性，可以使用**Get AzureADUser**和**一组 AzureADUser** cmdlet 的组合。下面的示例更改为法国所有用户的使用位置：</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="6c0ff-196">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6c0ff-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="6c0ff-197">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c0ff-198">将用户的位置设置为法国 (**集 AzureADUser UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="6c0ff-199">更改一组特定的用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6c0ff-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="6c0ff-p113">若要更改一组特定的用户帐户的属性，可以使用**Get AzureADUser**，**在其中**，而**集 AzureADUser** cmdlet 的组合。下面的示例更改为法国会计部门的所有用户的使用位置：</span><span class="sxs-lookup"><span data-stu-id="6c0ff-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="6c0ff-202">此命令指示向 Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6c0ff-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="6c0ff-203">获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c0ff-204">找到所有的用户帐户具有的部门属性设置为"会计"(**其中 {$_。部门 eq"记帐"}** ) 并将得到的信息发送到下一个命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c0ff-205">将用户的位置设置为法国 (**集 AzureADUser UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="6c0ff-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="6c0ff-206">See also</span><span class="sxs-lookup"><span data-stu-id="6c0ff-206">See also</span></span>

#### 

[<span data-ttu-id="6c0ff-207">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="6c0ff-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="6c0ff-208">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="6c0ff-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6c0ff-209">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="6c0ff-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

