---
title: 将角色分配给用户帐户与 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/31/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 摘要： 使用 Office 365 PowerShell，可以将角色分配给用户帐户。
ms.openlocfilehash: 702c7358ccca9bb36bd106d742b5c454283ee8b4
ms.sourcegitcommit: d0c870c7a487eda48b11f649b30e4818fd5608aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2019
ms.locfileid: "29690433"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d0dda-103">将角色分配给用户帐户与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0dda-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d0dda-104">您可以快速、 方便地向分配角色使用 Office 365 PowerShell 中的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d0dda-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d0dda-105">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0dda-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d0dda-106">第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)使用全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="d0dda-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="d0dda-p101">接下来，确定要向角色添加用户帐户的登录名 (示例： fredsm@contoso.com)。这也称为是用户主体名称 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="d0dda-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="d0dda-p102">接下来，确定角色的名称。使用此命令列出您可以使用 PowerShell 分配的角色。</span><span class="sxs-lookup"><span data-stu-id="d0dda-p102">Next, determine the name of the role. Use this command to list the roles that you can assign with PowerShell.</span></span>

````
Get-AzureADDirectoryRole
````

<span data-ttu-id="d0dda-111">接下来，填写的登录和角色名称，然后运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d0dda-111">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="d0dda-112">下面是一个已完成的命令集的示例：</span><span class="sxs-lookup"><span data-stu-id="d0dda-112">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="Lync Service Administrator"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="d0dda-113">若要显示的特定角色的用户名称列表，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="d0dda-113">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d0dda-114">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="d0dda-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d0dda-115">第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)使用全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="d0dda-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="d0dda-116">单个角色更改</span><span class="sxs-lookup"><span data-stu-id="d0dda-116">For a single role change</span></span>

<span data-ttu-id="d0dda-117">确定以下信息：</span><span class="sxs-lookup"><span data-stu-id="d0dda-117">Determine the following:</span></span>
  
- <span data-ttu-id="d0dda-118">您想要配置用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d0dda-118">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="d0dda-p103">若要指定的用户帐户，您必须确定其显示名称。要获取的完整列表帐户，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="d0dda-p103">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d0dda-p104">此命令列出的用户帐户，按显示名称，一次一屏的显示名称。可以使用**其中**cmdlet 来筛选一较小的列表。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="d0dda-p104">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d0dda-124">此命令将列出其显示名称开头"John"的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d0dda-124">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="d0dda-125">您要分配的角色。</span><span class="sxs-lookup"><span data-stu-id="d0dda-125">The role you want to assign.</span></span>
    
    <span data-ttu-id="d0dda-126">要显示可用的角色，您可以分配给用户帐户的列表，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="d0dda-126">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="d0dda-127">一旦您已确定的帐户的显示名称和角色的名称，使用这些命令将角色分配给该帐户：</span><span class="sxs-lookup"><span data-stu-id="d0dda-127">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="d0dda-p105">复制命令，并将它们粘贴到记事本。**$DispName**和 **$roleName**变量的值替换的说明文本、 删除\<和 > 字符，并将保留为引号。复制已修改的行并将它们粘贴到您的 Windows Azure Active Directory 模块用于 Windows PowerShell 窗口来运行它们。或者，也可以使用 Windows PowerShell 集成脚本环境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="d0dda-p105">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="d0dda-132">下面是一个已完成的命令集的示例：</span><span class="sxs-lookup"><span data-stu-id="d0dda-132">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="d0dda-133">多个角色更改</span><span class="sxs-lookup"><span data-stu-id="d0dda-133">For multiple role changes</span></span>

<span data-ttu-id="d0dda-134">确定以下信息：</span><span class="sxs-lookup"><span data-stu-id="d0dda-134">Determine the following:</span></span>
  
- <span data-ttu-id="d0dda-135">哪些用户帐户想要配置。</span><span class="sxs-lookup"><span data-stu-id="d0dda-135">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="d0dda-p106">若要指定的用户帐户，您必须确定其显示名称。要获取列表帐户，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="d0dda-p106">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d0dda-p107">此命令将列出所有用户帐户，按显示名称，一次一个屏幕显示名称。可以使用**其中**cmdlet 来筛选一较小的列表。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="d0dda-p107">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d0dda-141">此命令将列出其显示名称开头"John"的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d0dda-141">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="d0dda-142">要分配给每个用户帐户的角色。</span><span class="sxs-lookup"><span data-stu-id="d0dda-142">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="d0dda-143">要显示可用的角色，您可以分配给用户帐户的列表，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="d0dda-143">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="d0dda-p108">接下来，创建具有显示名称和角色的以逗号分隔值 (CSV) 文本文件名称字段。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="d0dda-p108">Next, create a comma-separated value (CSV) text file that has the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="d0dda-146">接下来，填写 CSV 文件的位置，然后在 PowerShell 命令提示符处运行生成命令。</span><span class="sxs-lookup"><span data-stu-id="d0dda-146">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="d0dda-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0dda-147">See also</span></span>

- [<span data-ttu-id="d0dda-148">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="d0dda-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="d0dda-149">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="d0dda-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="d0dda-150">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="d0dda-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
