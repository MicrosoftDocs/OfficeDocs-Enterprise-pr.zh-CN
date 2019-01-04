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
# <a name="configure-user-account-properties-with-office-365-powershell"></a>使用 Office 365 PowerShell 配置用户帐户属性

 **摘要：** 使用 Office 365 PowerShell 在 Office 365 租户中配置的单个或多个用户帐户的属性。
  
尽管可以使用 Office 365 管理中心配置 Office 365 租户的用户帐户的属性，还可以使用 Office 365 PowerShell 中，并执行某些操作不能在 Office 365 管理中心中。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用 Azure Active Directory PowerShell 图模块

要使用图模块 Azure Active Directory PowerShell 配置用户帐户的属性，您使用[集 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet 并指定要设置或更改的属性。 

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
   
### <a name="change-properties-for-a-specific-user-account"></a>更改特定的用户帐户属性

您使用 **-ObjectID**参数标识的帐户和设置或更改与其他参数的特定属性。下面是最常见的参数的列表。
  
- 部门"\<部门名称 >"
    
- -DisplayName"\<完整的用户名称 >"
    
- -FacsimilieTelephoneNumber"\<传真号码 >"
    
- -GivenName"\<用户名字 >"
    
- -Surname"\<用户姓氏 >"
    
- -移动"\<的移动电话号码 >"
    
- -JobTitle"\<职务 >"
    
- -PreferredLanguage"\<语言 >"
    
- -StreetAddress"\<街道地址 >"
    
- --市/县"\<城市名称 >"
    
- -状态"\<状态名称 >"
    
- -PostalCode"\<邮政编码 >"
    
- -国家"\<国家/地区名称 >"
    
- -TelephoneNumber"\<办公室电话号码 >"
    
- -UsageLocation"\<2 个字符的国家或地区代码 >"
    
    这是 ISO 3166-1 alpha-2 (A2) 两个字母的国家或地区代码。
    
其他参数，请参阅[设置 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。
  
若要显示您的用户帐户的用户主体名称，请运行以下命令。
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

此命令指示 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 按字母顺序排序的用户主体名称的列表 ( **Sort 对象 UserPrincipalName** ) 并将其发送到下一个命令 ( **|** )。
    
- 显示刚 ( **Select-object UserPrincipalName** ) 的每个帐户的用户主体名称属性。
- 将其显示在一个屏幕 （**详细**） 一次。
    
此命令将列出所有帐户。如果您想要显示用户主体名称的基于其显示帐户名 （名字和姓氏名称）、 填写下面 **$userName**变量 (删除\<和 > 字符)，然后运行以下命令：
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本示例显示了用户主体名称的用户帐户和 Caleb Sills 的显示名称。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

通过使用 **$upn**变量，您可以对基于其显示名称的单个帐户进行更改。下面是一个示例将 Belinda Newman 的使用位置设置为法国，但指定其显示名称，而不是其用户主体名称：
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>更改为所有用户帐户属性

若要更改的所有用户属性，可以使用**Get-AzureADUser**和**设置 AzureADUser** cmdlet 的组合。以下示例更改为法国的所有用户的使用位置：
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

此命令指示 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 设置用户位置为法国 (**集 AzureADUser UsageLocation"FR"** )。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>更改一组特定的用户帐户属性

若要更改的一组特定的用户帐户属性，可以使用**Get-AzureADUser**，**其中**，而**设置 AzureADUser** cmdlet 的组合。下面的示例将更改为法国会计部门中的所有用户的使用位置：
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

此命令指示 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get AzureADUser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 查找所有其部门属性设置为"会计"的用户帐户 (**其中 {$_。部门-eq"Accounting"}** ) 并将生成的信息发送到下一个命令 ( **|** )。
    
- 设置用户位置为法国 (**集 AzureADUser UsageLocation"FR"** )。
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用 Windows PowerShell 的 Microsoft Azure Active Directory 模块

若要使用 Microsoft Azure Active Directory 模块用于 Windows PowerShell 配置用户帐户的属性，您使用 Set-msoluser cmdlet 并指定要设置或更改的属性。 

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。
  
### <a name="change-properties-for-a-specific-user-account"></a>更改特定的用户帐户属性

若要配置的特定用户帐户属性，您使用[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet 并指定要设置或更改的属性。 

您使用 **-UserPrincipalName**参数标识的帐户和设置或更改与其他参数的特定属性。下面是最常见的参数的列表。
  
- --市/县"\<城市名称 >"
    
- -国家"\<国家/地区名称 >"
    
- 部门"\<部门名称 >"
    
- -DisplayName"\<完整的用户名称 >"
    
- -传真"\<传真号码 >"
    
- -FirstName"\<用户名字 >"
    
- -LastName"\<用户姓氏 >"
    
- -MobilePhone"\<的移动电话号码 >"
    
- Office"\<办公地点 >"
    
- -电话号码"\<办公室电话号码 >"
    
- -PostalCode"\<邮政编码 >"
    
- -PreferredLanguage"\<语言 >"
    
- -状态"\<状态名称 >"
    
- -StreetAddress"\<街道地址 >"
    
- -Title"\<标题名称 >"
    
- -UsageLocation"\<2 个字符的国家或地区代码 >"
    
    这是 ISO 3166-1 alpha-2 (A2) 两个字母的国家或地区代码。
    
其他参数，请参阅[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 。
  
若要查看您的所有用户的用户主体名称，请运行以下命令。
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

此命令指示 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 按字母顺序排序的用户主体名称的列表 ( **Sort 对象 UserPrincipalName** ) 并将其发送到下一个命令 ( **|** )。
    
- 显示刚 ( **Select-object UserPrincipalName** ) 的每个帐户的用户主体名称属性。
    
- 将其显示在一个屏幕 （**详细**） 一次。
    
此命令将列出所有帐户。如果您想要显示用户主体名称的基于其显示帐户名 （名字和姓氏名称）、 填写下面 **$userName**变量 (删除\<和 > 字符)，然后运行以下命令：
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本示例显示名为 Caleb Sills 用户的用户主体名称。
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

通过使用 **$upn**变量，您可以对基于其显示名称的单个帐户进行更改。下面是一个示例将 Belinda Newman 的使用位置设置为法国，但指定其显示名称，而不是其用户主体名称：
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>更改为所有用户帐户属性

要更改所有用户的属性，您可以将 **Get-MsolUser** 和 **Set-MsolUser** cmdlet 结合使用。下面的示例将所有用户的使用地点更改为法国：
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

此命令指示 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 设置用户位置为法国 ( **Set-msoluser-UsageLocation"FR"** )。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>更改一组特定的用户帐户属性

若要更改的一组特定的用户帐户属性，可以使用**Get-msoluser**、 **Where-object**和**Set-msoluser** cmdlet 的组合。下面的示例将更改为法国会计部门中的所有用户的使用位置：
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

此命令指示 Office 365 PowerShell:
  
- 获取所有用户帐户 ( **Get-msoluser** ) 上的信息，并将其发送到下一个命令 ( **|** )。
    
- 查找所有的用户帐户的设置为"会计"的部门属性 ( **Where-object {$_。部门-eq"Accounting"}** ) 并将生成的信息发送到下一个命令 ( **|** )。
    
- 设置用户位置为法国 ( **Set-msoluser-UsageLocation"FR"** )。
    

## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
