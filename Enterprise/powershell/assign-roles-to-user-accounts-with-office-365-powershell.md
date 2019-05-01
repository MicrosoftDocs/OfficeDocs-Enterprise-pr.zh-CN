---
title: 将角色分配给用户帐户与 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
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
description: '摘要: 使用 Office 365 PowerShell 向用户帐户分配角色。'
ms.openlocfilehash: 78f2e08df6d46588b93dc217d0e16b7c3a350a88
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491988"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="cd694-103">将角色分配给用户帐户与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd694-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="cd694-104">您可以使用 Office 365 PowerShell 快速而轻松地向用户帐户分配角色。</span><span class="sxs-lookup"><span data-stu-id="cd694-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="cd694-105">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd694-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="cd694-106">首先, 使用全局管理员帐户[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="cd694-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="cd694-107">接下来, 确定要添加到角色的用户帐户的登录名 (例如: fredsm@contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="cd694-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="cd694-108">这也称为用户主体名称 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="cd694-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="cd694-109">接下来, 确定角色的名称。</span><span class="sxs-lookup"><span data-stu-id="cd694-109">Next, determine the name of the role.</span></span> <span data-ttu-id="cd694-110">[在 Azure Active Directory 中使用此管理员角色权限列表](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="cd694-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="cd694-111">请注意本文中的注释。</span><span class="sxs-lookup"><span data-stu-id="cd694-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="cd694-112">对于 Azure AD PowerShell, 某些角色名称不同。</span><span class="sxs-lookup"><span data-stu-id="cd694-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="cd694-113">例如, Microsoft 365 管理中心中的 "sharepoint 管理员" 角色为 Azure AD PowerShell 命名为 "sharepoint 服务管理员"。</span><span class="sxs-lookup"><span data-stu-id="cd694-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="cd694-114">接下来, 填写登录名和角色名称, 并运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="cd694-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="cd694-115">下面的示例展示了已完成的命令集:</span><span class="sxs-lookup"><span data-stu-id="cd694-115">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="cd694-116">若要显示特定角色的用户名列表, 请使用这些命令。</span><span class="sxs-lookup"><span data-stu-id="cd694-116">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="cd694-117">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="cd694-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="cd694-118">首先, 使用全局管理员帐户[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="cd694-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="cd694-119">对于单个角色更改</span><span class="sxs-lookup"><span data-stu-id="cd694-119">For a single role change</span></span>

<span data-ttu-id="cd694-120">确定下列事项：</span><span class="sxs-lookup"><span data-stu-id="cd694-120">Determine the following:</span></span>
  
- <span data-ttu-id="cd694-121">要配置的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="cd694-121">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="cd694-122">若要指定用户帐户, 必须确定其显示名称。</span><span class="sxs-lookup"><span data-stu-id="cd694-122">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="cd694-123">若要获取完整的列表帐户, 请使用以下命令:</span><span class="sxs-lookup"><span data-stu-id="cd694-123">To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="cd694-124">此命令将列出用户帐户的显示名称, 按显示名称排序, 一次显示一个屏幕。</span><span class="sxs-lookup"><span data-stu-id="cd694-124">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="cd694-125">您可以使用**Where** cmdlet 将列表筛选为一个较小的集。</span><span class="sxs-lookup"><span data-stu-id="cd694-125">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="cd694-126">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="cd694-126">Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="cd694-127">此命令仅列出其显示名称以 "John" 开头的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="cd694-127">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="cd694-128">要分配的角色。</span><span class="sxs-lookup"><span data-stu-id="cd694-128">The role you want to assign.</span></span>
    
    <span data-ttu-id="cd694-129">若要显示可分配给用户帐户的可用角色的列表, 请使用以下命令:</span><span class="sxs-lookup"><span data-stu-id="cd694-129">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="cd694-130">确定帐户的显示名称和角色的名称后, 请使用以下命令将角色分配给帐户:</span><span class="sxs-lookup"><span data-stu-id="cd694-130">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="cd694-131">复制命令并将其粘贴到记事本中。</span><span class="sxs-lookup"><span data-stu-id="cd694-131">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="cd694-132">对于 **$dispName**和 **$roleName**变量, 将说明文本替换为它们的值, 删除\<和 > 字符, 并保留引号。</span><span class="sxs-lookup"><span data-stu-id="cd694-132">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="cd694-133">复制修改过的行并将其粘贴到 windows PowerShell 的 windows Azure Active Directory 模块中, 以运行它们。</span><span class="sxs-lookup"><span data-stu-id="cd694-133">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="cd694-134">或者, 也可以使用 Windows PowerShell 集成脚本环境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="cd694-134">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="cd694-135">下面的示例展示了已完成的命令集:</span><span class="sxs-lookup"><span data-stu-id="cd694-135">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="cd694-136">对于多个角色更改</span><span class="sxs-lookup"><span data-stu-id="cd694-136">For multiple role changes</span></span>

<span data-ttu-id="cd694-137">确定下列事项：</span><span class="sxs-lookup"><span data-stu-id="cd694-137">Determine the following:</span></span>
  
- <span data-ttu-id="cd694-138">要配置的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="cd694-138">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="cd694-139">若要指定用户帐户, 必须确定其显示名称。</span><span class="sxs-lookup"><span data-stu-id="cd694-139">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="cd694-140">若要获取列表帐户, 请使用以下命令:</span><span class="sxs-lookup"><span data-stu-id="cd694-140">To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="cd694-141">此命令将列出所有用户帐户的显示名称, 按显示名称排序, 一次显示一个屏幕。</span><span class="sxs-lookup"><span data-stu-id="cd694-141">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="cd694-142">您可以使用**Where** cmdlet 将列表筛选为一个较小的集。</span><span class="sxs-lookup"><span data-stu-id="cd694-142">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="cd694-143">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="cd694-143">Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="cd694-144">此命令仅列出其显示名称以 "John" 开头的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="cd694-144">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="cd694-145">要分配给每个用户帐户的角色。</span><span class="sxs-lookup"><span data-stu-id="cd694-145">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="cd694-146">若要显示可分配给用户帐户的可用角色的列表, 请使用以下命令:</span><span class="sxs-lookup"><span data-stu-id="cd694-146">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="cd694-147">接下来, 创建一个包含 "DisplayName" 和 "角色名称" 字段的逗号分隔值 (CSV) 文本文件。</span><span class="sxs-lookup"><span data-stu-id="cd694-147">Next, create a comma-separated value (CSV) text file that has the DisplayName and role Name fields.</span></span> <span data-ttu-id="cd694-148">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="cd694-148">Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="cd694-149">接下来, 填写 CSV 文件的位置, 并在 PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="cd694-149">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="cd694-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd694-150">See also</span></span>

- [<span data-ttu-id="cd694-151">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="cd694-151">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="cd694-152">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="cd694-152">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="cd694-153">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="cd694-153">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
