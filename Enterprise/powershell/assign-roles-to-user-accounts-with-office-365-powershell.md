---
title: "将角色分配给用户帐户与 Office 365 PowerShell"
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: "摘要： 使用 Office 365 PowerShell 和添加 MsolRoleMember cmdlet 将角色分配给用户帐户。"
ms.openlocfilehash: dee9aede72a79a32f03c94a0793464e1393edd95
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="06f34-103">将角色分配给用户帐户与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="06f34-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="06f34-104">**摘要：**使用 Office 365 PowerShell 和**添加 MsolRoleMember** cmdlet 将角色分配给用户帐户。</span><span class="sxs-lookup"><span data-stu-id="06f34-104">**Summary:** Use Office 365 PowerShell and the **Add-MsolRoleMember** cmdlet to assign roles to user accounts.</span></span>
  
<span data-ttu-id="06f34-105">您可以快速而轻松地分配角色通过 Office 365 PowerShell 标识的用户帐户显示名称和角色名称的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="06f34-105">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="06f34-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="06f34-106">Before you begin</span></span>

<span data-ttu-id="06f34-p101">本主题中的过程要求您连接到 Office 365 PowerShell 使用全局管理员帐户。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="06f34-p101">The procedures in this topic require you to connect to Office 365 PowerShell using a global administrator account. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="for-a-single-role-change"></a><span data-ttu-id="06f34-109">单个角色的变化</span><span class="sxs-lookup"><span data-stu-id="06f34-109">For a single role change</span></span>

<span data-ttu-id="06f34-110">确定下列因素：</span><span class="sxs-lookup"><span data-stu-id="06f34-110">Determine the following:</span></span>
  
- <span data-ttu-id="06f34-111">您想要配置的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="06f34-111">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="06f34-p102">若要指定用户帐户，您必须确定其显示名称。要获取完整列表帐户，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="06f34-p102">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="06f34-p103">此命令将列出您的用户帐户，按显示名称，一次一屏的显示名称。您可以将列表筛选为一个较小集使用**的**cmdlet。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="06f34-p103">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="06f34-117">此命令将列出为其显示名称的开头是"约翰"的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="06f34-117">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="06f34-118">要分配的角色。</span><span class="sxs-lookup"><span data-stu-id="06f34-118">The role you want to assign.</span></span>
    
    <span data-ttu-id="06f34-119">若要显示可用的角色，您可以分配给用户帐户的列表，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="06f34-119">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="06f34-120">一旦确定了该帐户的显示名称和角色的名称，可以使用这些命令来为该帐户分配角色：</span><span class="sxs-lookup"><span data-stu-id="06f34-120">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="06f34-p104">复制命令并将其粘贴到记事本。**$DispName**和**$roleName**变量的值替换说明文本，删除\<和 > 字符，并将引号。将已修改的行复制并粘贴到您的 Windows Azure 活动目录模块用于 Windows PowerShell 窗口来运行它们。或者，您可以使用 Windows PowerShell 集成脚本环境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="06f34-p104">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="06f34-125">这里是完成的命令集的示例：</span><span class="sxs-lookup"><span data-stu-id="06f34-125">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a><span data-ttu-id="06f34-126">为多个角色更改</span><span class="sxs-lookup"><span data-stu-id="06f34-126">For multiple role changes</span></span>

<span data-ttu-id="06f34-127">确定下列因素：</span><span class="sxs-lookup"><span data-stu-id="06f34-127">Determine the following:</span></span>
  
- <span data-ttu-id="06f34-128">您想要配置的哪个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="06f34-128">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="06f34-p105">若要指定用户帐户，您必须确定其显示名称。要获取列表的帐户，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="06f34-p105">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="06f34-p106">此命令将列出所有用户帐户，按显示名称，一次一屏的显示名称。您可以将列表筛选为一个较小集使用**的**cmdlet。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="06f34-p106">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="06f34-134">此命令将列出为其显示名称的开头是"约翰"的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="06f34-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="06f34-135">您想要分配给每个用户帐户所属的角色。</span><span class="sxs-lookup"><span data-stu-id="06f34-135">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="06f34-136">若要显示可用的角色，您可以分配给用户帐户的列表，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="06f34-136">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="06f34-p107">接下来，创建以逗号分隔值 (CSV) 文本文件，其中包含显示名称和角色名称的字段。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="06f34-p107">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="06f34-139">下一步，填写该 CSV 文件的位置，PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="06f34-139">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="06f34-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06f34-140">See also</span></span>

#### 

[<span data-ttu-id="06f34-141">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="06f34-141">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="06f34-142">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="06f34-142">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="06f34-143">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="06f34-143">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
#### 

[<span data-ttu-id="06f34-144">添加 MsolRoleMember</span><span class="sxs-lookup"><span data-stu-id="06f34-144">Add-MsolRoleMember</span></span>](https://msdn.microsoft.com/library/dn194120.aspx)

