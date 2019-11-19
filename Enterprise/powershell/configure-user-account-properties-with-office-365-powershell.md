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
# <a name="configure-user-account-properties-with-office-365-powershell"></a>使用 Office 365 PowerShell 配置用户帐户的属性

 **摘要：** 使用 Office 365 PowerShell 配置 Office 365 租户中单个或多个用户帐户的属性。
  
虽然您可以使用 Microsoft 365 管理中心来配置 Office 365 租户的用户帐户的属性，但您也可以使用 Office 365 PowerShell 并执行管理中心无法执行的某些操作。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

若要为使用 Azure Active Directory PowerShell for Graph 模块的用户帐户配置属性，请使用[AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet 并指定要设置或更改的属性。 

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
   
### <a name="change-properties-for-a-specific-user-account"></a>更改特定用户帐户的属性

使用 **-ObjectID**参数标识帐户，并使用其他参数设置或更改特定属性。 下面列出了最常见的参数。
  
- -部门 "\<部门名称>"
    
- -DisplayName "\<full user name>"
    
- -FacsimilieTelephoneNumber "\<fax number>"
    
- -GivenName "\<user first name>"
    
- -姓 "\<user last name>"
    
- -移动 "\<移动电话号码>"
    
- -JobTitle "\<职务>"
    
- -PreferredLanguage "\<language>"
    
- -StreetAddress "\<街道地址>"
    
- -市/\<县 "城市名称>"
    
- -State "\<state name>"
    
- -邮政编码 "\<>"
    
- -国家/\<地区 "国家/地区名称>"
    
- -TelephoneNumber "\<office 电话号码>"
    
- -UsageLocation "\<2 个字符的国家或地区代码>"
    
    这是 ISO 3166-1 alpha-2 （A2）两个字母的国家/地区代码。
    
有关其他参数，请参阅[AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。


若要显示用户帐户的用户主体名称，请运行以下命令。
  
```powershell
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

此命令指示 Office 365 PowerShell：
  
- 获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 按字母顺序（**排序对象 UserPrincipalName** ）对用户主体名称列表进行排序，并将其发送到下**|** 一个命令（）。
    
- 仅显示每个帐户（**选择-对象 UserPrincipalName** ）的用户主体名称属性。
- 一次显示一屏（**更多**）。
    
此命令将列出你的所有帐户。 如果要根据其显示名称（名和姓）显示帐户的用户主体名称，请填写下面的 **$userName**变量（删除\<和 > 字符），然后运行以下命令：
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本示例显示名为 Caleb Sills 的用户帐户的用户主体名称。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

通过使用 **$upn**变量，可以根据各个帐户的显示名称对其进行更改。 下面的示例展示了如何将 Belinda Newman 的使用位置设置为华北，但指定了她的显示名称而不是她的用户主体名称：
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>更改所有用户帐户的属性

若要更改所有用户的属性，您可以使用**AzureADUser**和**AzureADUser** cmdlet 的组合。 下面的示例将所有用户的使用地点更改为法国：
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

此命令指示 Office 365 PowerShell：
  
- 获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 将用户位置设置为 "法国 **" （AzureADUser-UsageLocation "FR"** ）。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>更改特定用户帐户集的属性

若要更改特定用户帐户集的属性，您可以使用**AzureADUser**、 **Where**和**AzureADUser** cmdlet 的组合。 下面的示例将会计部门的所有用户的使用地点更改为法国：
  
```powershell
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

此命令指示 Office 365 PowerShell：
  
- 获取用户帐户（ **AzureADUser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 查找其 "部门" 属性设置为 "记帐" 的所有用户帐户（**其中 {$ _）。部门-eq "记帐"}** ）并将生成的信息发送到下一个命令**|** （）。
    
- 将用户位置设置为 "法国 **" （AzureADUser-UsageLocation "FR"** ）。
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块

若要使用适用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块配置用户帐户的属性，请使用 Get-msoluser cmdlet 并指定要设置或更改的属性。 

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。
  
### <a name="change-properties-for-a-specific-user-account"></a>更改特定用户帐户的属性

若要配置特定用户帐户的属性，请使用[get-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet 并指定要设置或更改的属性。 

您可以使用 **-UserPrincipalName**参数标识帐户，并使用其他参数设置或更改特定属性。 下面是最常见的参数的列表。
  
- -市/\<县 "城市名称>"
    
- -国家/\<地区 "国家/地区名称>"
    
- -部门 "\<部门名称>"
    
- -DisplayName "\<full user name>"
    
- -Fax "\<fax 号码>"
    
- -FirstName "\<user first name>"
    
- -LastName "\<user last name>"
    
- -MobilePhone "\<移动电话号码>"
    
- -Office "\<office 位置>"
    
- -PhoneNumber "\<office 电话号码>"
    
- -邮政编码 "\<>"
    
- -PreferredLanguage "\<language>"
    
- -State "\<state name>"
    
- -StreetAddress "\<街道地址>"
    
- -Title "\<title name>"
    
- -UsageLocation "\<2 个字符的国家或地区代码>"
    
    这是 ISO 3166-1 alpha-2 （A2）两个字母的国家/地区代码。
    
有关其他参数，请参阅[get-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 。

若要查看所有用户的用户主体名称，请运行以下命令。
  
```powershell
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

此命令指示 Office 365 PowerShell：
  
- 获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 按字母顺序（**排序对象 UserPrincipalName** ）对用户主体名称列表进行排序，并将其发送到下**|** 一个命令（）。
    
- 仅显示每个帐户（**选择-对象 UserPrincipalName** ）的用户主体名称属性。
    
- 一次显示一屏（**更多**）。
    
此命令将列出你的所有帐户。 如果要根据其显示名称（名和姓）显示帐户的用户主体名称，请填写下面的 **$userName**变量（删除\<和 > 字符），然后运行以下命令：
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本示例显示名为 Caleb Sills 的用户的用户主体名称。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

通过使用 **$upn**变量，可以根据各个帐户的显示名称对其进行更改。 下面的示例展示了如何将 Belinda Newman 的使用位置设置为华北，但指定了她的显示名称而不是她的用户主体名称：
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>更改所有用户帐户的属性

要更改所有用户的属性，您可以将 **Get-MsolUser** 和 **Set-MsolUser** cmdlet 结合使用。下面的示例将所有用户的使用地点更改为法国：
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

此命令指示 Office 365 PowerShell：
  
- 获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 将用户位置设置为 "法国 **" （get-msoluser-UsageLocation "FR"** ）。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>更改特定用户帐户集的属性

若要更改一组特定用户帐户的属性，您可以使用**get-msoluser**、 **Where-Object**和**get-msoluser** cmdlet 的组合。 下面的示例将会计部门的所有用户的使用地点更改为法国：
  
```powershell
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

此命令指示 Office 365 PowerShell：
  
- 获取用户帐户（ **get-msoluser** ）上的所有信息，并将其发送到下一个命令（ **|** ）。
    
- 查找其 "部门" 属性设置为 "记帐" 的所有用户帐户（**其中-对象 {$ _）。部门-eq "记帐"}** ）并将生成的信息发送到下一个命令**|** （）。
    
- 将用户位置设置为 "法国 **" （get-msoluser-UsageLocation "FR"** ）。
    

## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
