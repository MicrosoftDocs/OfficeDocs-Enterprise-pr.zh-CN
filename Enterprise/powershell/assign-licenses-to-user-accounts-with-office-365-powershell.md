---
title: 使用 Office 365 PowerShell 向用户帐户分配许可证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: 介绍如何使用 Office 365 PowerShell 中分配给未许可用户的 Office 365 许可证。
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123289"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 向用户帐户分配许可证

**摘要：** 介绍如何使用 Office 365 PowerShell 中分配给未许可用户的 Office 365 许可证。
  
许可 Office 365 中的用户帐户很重要，因为用户不能使用任何 Office 365 服务，直到其帐户已授权。您可以使用 Office 365 PowerShell 中高效地将许可证分配给未经授权的帐户，尤其是多个帐户。 

## <a name="before-you-begin"></a>准备工作
<a name="RTT"> </a>

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用**Get-msolaccountsku** cmdlet 以查看您的组织中的每个计划中可用的许可计划和可用许可证的数目。每个计划中可用的许可证数是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。有关许可计划、 许可证和服务的详细信息，请参阅[查看许可证和身份验证服务与 Office 365 PowerShell 中](view-licenses-and-services-with-office-365-powershell.md)。
    
- 若要在组织中查找的未经授权的帐户，请运行命令`Get-MsolUser -All -UnlicensedUsersOnly`
    
- 您可以仅对具有**UsageLocation**属性设置为有效的 ISO 3166-1 alpha 2 国家/地区代码的用户帐户分配许可证。例如，美国的电话和法国 FR 我们。在某些国家/地区，某些 Office 365 服务不可用。有关详细信息，请参阅[关于许可限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。
    
    若要查找不具有**UsageLocation**值的帐户，请运行命令`Get-MsolUser -All | where {$_.UsageLocation -eq $null}`。若要设置帐户**UsageLocation**值，请使用语法`Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`。例如， `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。
    
- 如果您使用**Get-msoluser** cmdlet 而不使用`-All`参数返回仅前 500 个帐户。

## <a name="assigning-licenses-to-user-accounts"></a>向用户帐户分配许可证
    
若要向用户分配许可证，请在 Office 365 PowerShell 中使用以下语法：
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

本示例将从许可证分配`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3) 到未经授权的用户的许可计划`belindan@litwareinc.com`。
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

若要向多个未授权用户分配许可证，请使用以下句法：
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **注释**
  
- 您无法使用相同的许可计划为用户分配多个许可证。
    
- 如果没有足够可用的许可证，将按照 **Get-MsolUser** cmdlet 返回的顺序为用户分配许可证，直到可用许可证用尽。
    
本示例将从许可证分配`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3) 到所有未经授权的用户的许可计划。
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

本示例向美国销售部门的未授权用户分配这些相同的许可证。
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>刚开始接触 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另请参阅
<a name="SeeAlso"> </a>

请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：
  
- [创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
- [删除并还原用户帐户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [阻止用户帐户](block-user-accounts-with-office-365-powershell.md)
    
- [从用户帐户删除许可证](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [Get-msolaccountsku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-msoluserlicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [选择对象](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

