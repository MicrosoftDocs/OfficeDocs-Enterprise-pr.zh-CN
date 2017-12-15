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
# <a name="configure-user-account-properties-with-office-365-powershell"></a>使用 Office 365 PowerShell 配置用户帐户的属性

 **摘要：**使用 Office 365 PowerShell Office 365 租户中配置单个或多个用户帐户的属性。
  
虽然您可以使用 Office 365 管理中心配置 Office 365 租户的用户帐户的属性，您还可以使用 Office 365 PowerShell 并做一些 Office 365 管理中心不能。
  
## <a name="before-you-begin"></a>开始之前

若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
## <a name="change-properties-for-a-specific-user-account"></a>更改特定用户帐户的属性

要配置为使用特定用户帐户的属性，请使用[组 MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet 并指定要设置或更改的属性。本示例命令将更改为法国 Belinda Newman 使用位置：
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

您使用**的范围内**参数识别帐户并设置或更改使用附加参数的特定属性。这是最常见的参数列表。
  
- -市/县"\<城市名称 >"
    
- -国家"\<国家/地区名称 >"
    
- -部门"\<部门名称 >"
    
- -显示名称"\<完整的用户名称 >"
    
- -传真"\<传真号码 >"
    
- 名字"\<用户名字 >"
    
- 姓氏的"\<用户姓氏 >"
    
- -MobilePhone"\<的移动电话号码 >"
    
- 机构"\<办公地点 >"
    
- -电话号码"\<办公室电话号码 >"
    
- 邮政编码的"\<邮政编码 >"
    
- -PreferredLanguage"\<语言 >"
    
- -国家"\<状态名称 >"
    
- -街道地址"\<街道地址 >"
    
- 的标题"\<标题名称 >"
    
- -UsageLocation"\<2 个字符的国家或地区代码 >"
    
    这是 ISO 3166-1 alpha 2 (A2) 两个字母的国家或地区代码。
    
额外的参数，请参阅[设置 MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 。
  
若要查看所有用户的用户主体名称，请运行以下命令。
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 按字母顺序排序列表中的用户主要名称 ( **Sort 对象范围内**) 并将其发送到下一个命令 ( **|** )。
    
- 显示只需为每个帐户 (**选择对象的范围内**) 的用户主体名称属性。
    
- 它们一屏一次显示 （**更多**）。
    
此命令将列出您的所有帐户。如果您想要显示基于其显示名称帐户的用户主体名称 （第一个和最后一个名称），填入下面的**$userName**变量 (删除\<和 > 字符)，然后运行以下命令：
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本示例显示名为 Caleb 窗台用户的用户主体名称。
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

通过使用**$upn**变量，您可以到基于其显示名称的个人帐户进行更改。下面是一个示例设置 Belinda Newman 使用位置到法国，但指定她显示名称，而不是她的用户主体名称：
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a>更改对所有用户帐户的属性

若要更改所有用户的属性，可以使用**Get MsolUser**和**一组 MsolUser** cmdlet 的组合。下面的示例更改为法国所有用户的使用位置：
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 将用户的位置设置为法国 (**集 MsolUser UsageLocation"FR"** )。
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>更改一组特定的用户帐户的属性

若要更改一组特定的用户帐户的属性，可以使用**Get MsolUser**、**位置对象**和**一组 MsolUser** cmdlet 的组合。下面的示例更改为法国会计部门的所有用户的使用位置：
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get MsolUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 找到所有的用户帐户具有的部门属性设置为"会计"(**位置对象 {$_。部门 eq"记帐"}** ) 并将得到的信息发送到下一个命令 ( **|** )。
    
- 将用户的位置设置为法国 (**集 MsolUser UsageLocation"FR"** )。
    
- 它们一屏一次显示 （**更多**）。
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>使用 Azure 活动目录 V2 PowerShell 模块可配置用户帐户属性

要使用 Azure 活动目录 V2 PowerShell 模块配置用户帐户的属性，使用[集 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet 并指定要设置或更改的属性。但首先，您必须连接到您的订购。有关说明，请参阅[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。
  
### <a name="change-properties-for-a-specific-user-account"></a>更改特定用户帐户的属性

本示例命令将更改为法国 Belinda Newman 使用位置：
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

您使用**的对象 Id**参数识别帐户并设置或更改使用附加参数的特定属性。这是最常见的参数列表。
  
- -部门"\<部门名称 >"
    
- -显示名称"\<完整的用户名称 >"
    
- -FacsimilieTelephoneNumber"\<传真号码 >"
    
- -GivenName"\<用户名字 >"
    
- -Surname"\<用户姓氏 >"
    
- -移动"\<的移动电话号码 >"
    
- -职务"\<职务 >"
    
- -PreferredLanguage"\<语言 >"
    
- -街道地址"\<街道地址 >"
    
- -市/县"\<城市名称 >"
    
- -国家"\<状态名称 >"
    
- 邮政编码的"\<邮政编码 >"
    
- -国家"\<国家/地区名称 >"
    
- -TelephoneNumber"\<办公室电话号码 >"
    
- -UsageLocation"\<2 个字符的国家或地区代码 >"
    
    这是 ISO 3166-1 alpha 2 (A2) 两个字母的国家或地区代码。
    
额外的参数，请参阅[设置 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。
  
若要显示您的用户帐户的用户主体名称，请运行以下命令。
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 按字母顺序排序列表中的用户主要名称 ( **Sort 对象范围内**) 并将其发送到下一个命令 ( **|** )。
    
- 显示只需为每个帐户 (**选择对象的范围内**) 的用户主体名称属性。
- 它们一屏一次显示 （**更多**）。
    
此命令将列出您的所有帐户。如果您想要显示基于其显示名称帐户的用户主体名称 （第一个和最后一个名称），填入下面的**$userName**变量 (删除\<和 > 字符)，然后运行以下命令：
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本示例显示名为 Caleb 窗台用户的用户主体名称。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

通过使用**$upn**变量，您可以到基于其显示名称的个人帐户进行更改。下面是一个示例设置 Belinda Newman 使用位置到法国，但指定她显示名称，而不是她的用户主体名称：
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>更改对所有用户帐户的属性

若要更改所有用户的属性，可以使用**Get AzureADUser**和**一组 AzureADUser** cmdlet 的组合。下面的示例更改为法国所有用户的使用位置：
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 将用户的位置设置为法国 (**集 AzureADUser UsageLocation"FR"** )。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>更改一组特定的用户帐户的属性

若要更改一组特定的用户帐户的属性，可以使用**Get AzureADUser**，**在其中**，而**集 AzureADUser** cmdlet 的组合。下面的示例更改为法国会计部门的所有用户的使用位置：
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

此命令指示向 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息并将其发送到下一个命令 ( **|** )。
    
- 找到所有的用户帐户具有的部门属性设置为"会计"(**其中 {$_。部门 eq"记帐"}** ) 并将得到的信息发送到下一个命令 ( **|** )。
    
- 将用户的位置设置为法国 (**集 AzureADUser UsageLocation"FR"** )。
    
## <a name="see-also"></a>See also

#### 

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

