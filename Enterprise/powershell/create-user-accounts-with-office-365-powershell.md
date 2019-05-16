---
title: 使用 Office 365 PowerShell 创建用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 了解如何在 Office 365 中使用 Office 365 PowerShell 来创建用户帐户。
ms.openlocfilehash: 846dafb842b87f119670f44848152a99341939e7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069058"
---
# <a name="create-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 创建用户帐户

**摘要：** 了解如何使用 Office 365 PowerShell 在 Office 365 中创建用户帐户。
  
您可以使用 Office 365 PowerShell 来高效地创建用户帐户，尤其是多个用户帐户。当您在 Office 365 PowerShell 中创建用户帐户时，某些帐户属性始终是必需的。其他属性对于创建帐户则不是必需的，但也很重要。下表介绍了这些属性：
  
|**属性名称**|**是否必需？**|**说明**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |是  <br/> |这是在 Office 365 服务中使用的显示名称。例如，Caleb Sills。  <br/> |
|**UserPrincipalName** <br/> |是  <br/> |这是用于登录到 Office 365 服务的帐户名称。例如，CalebS@contoso.onmicrosoft.com。  <br/> |
|**FirstName** <br/> |否  <br/> ||
|**LastName** <br/> |否  <br/> ||
|**LicenseAssignment** <br/> |否  <br/> |这是许可计划（也称为许可证计划、Office 365 计划或 SKU），使用它可以将可用的许可证分配给用户帐户。该许可证定义可供帐户使用的 Office 365 服务。当你创建帐户时，没有向用户分配许可证，但该帐户需要许可证才能访问 Office 365 服务。创建用户帐户后，有 30 天的时间可以对该用户帐户授权。 |
|**密码** <br/> |否  <br/> | 如果你没有指定密码，将向用户帐户分配一个随机密码，且该密码将显示在命令结果中。如果你指定了密码，则需要是以下三种类型的 8 到 16 位 ASCII 文本字符：小写字母、大写字母、数字和符号。 <br/> |
|**UsageLocation** <br/> |否  <br/> |这是一个由两位字母组成的有效 ISO 3166-1 国家/地区代码。例如，US 代表美国，FR 代表法国。请务必提供此值，因为某些 Office 365 服务在某些国家不可用，因此不能为用户帐户分配许可证，除非该帐户已配置此值。有关详细信息，请参阅[关于许可证限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。<br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。

连接后，使用下列语法创建个人帐户：
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

本示例为名为 Caleb Sills 的美国用户创建一个帐户：
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

### <a name="create-an-individual-user-account"></a>创建单个用户帐户

若要创建单个帐户，请使用下面的语法：
  
```
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

若要列出可用的许可计划名称，请使用此命令：

````
Get-MsolAccountSku
````

本示例为美国用户 Caleb Sills 创建一个帐户并通过 `contoso:ENTERPRISEPACK` (Office 365 企业版 E3) 许可计划分配了一个许可证。
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>创建多个用户帐户

1. 创建包含所需用户帐户信息的逗号分隔值 (CSV) 文件。例如：
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>虽然列名称及其在 CSV 文件的第一行中的顺序是任意的，但请确保文件其余部分中的数据与列名称的顺序相匹配，并使用列名称作为 Office 365 PowerShell 命令中的参数值。
    
2. 使用以下语法：
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

本示例从名为 C:\My Documents\NewAccounts.csv 的文件创建用户帐户，并将结果记录在名为 C:\My Documents\NewAccountResults.csv 的文件中
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. 查看输出文件以查看结果。我们没有指定密码，这样便于在输出文件中显示 Office 365 生成的随机密码。
    
## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
