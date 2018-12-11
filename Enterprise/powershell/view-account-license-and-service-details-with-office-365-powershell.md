---
title: 使用 Office 365 PowerShell 查看帐户许可证和服务详细信息
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: 介绍如何使用 Office 365 PowerShell 来确定已分配给用户的 Office 365 服务。
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213949"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>使用 Office 365 PowerShell 查看帐户许可证和服务详细信息

**摘要：** 介绍如何使用 Office 365 PowerShell 来确定已分配给用户的 Office 365 服务。
  
在 Office 365 中，从许可计划许可 （也称为的 Sku 或 Office 365 计划） 向用户授予访问这些计划为定义的 Office 365 服务。但是，用户可能无法访问当前分配给它们的许可证中可用的所有服务。Office 365 PowerShell 中可用于对用户帐户中查看的服务的状态。 

## <a name="before-you-begin"></a>准备工作

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用命令`Get-MsolAccountSku`和`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`查找以下信息：
    
  - 您的组织中提供的许可计划。
    
  - 每个许可计划中提供的服务以及列出它们的顺序（索引号）。
    
     有关许可计划、 许可证和服务的详细信息，请参阅[查看许可证和身份验证服务与 Office 365 PowerShell 中](view-licenses-and-services-with-office-365-powershell.md)。
    
- 使用命令`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`查找分配给用户，并中的顺序的许可证所列出 （索引号）。
    
- 如果您使用 **Get-MsolUser** cmdlet 而无需使用 _All_ 参数，仅可返回前 500 个帐户。
    

## <a name="to-view-services-for-a-user-account"></a>若要查看的用户帐户的服务

若要查看所有 Office 365 服务的用户有权访问，请使用以下语法：
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

本示例显示用户 BelindaN@litwareinc.com 有权访问的服务。此时将显示与分配给其帐户的所有许可证关联的服务。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

本示例说明了用户 BelindaN@litwareinc.com 使用向她的帐户（索引号是 0）分配的第一个许可证有权访问的服务。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

若要查看已分配*多个许可证*的用户的所有服务，请使用以下语法：

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a>另请参阅

请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：
  
- [使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除和还原用户账户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 冻结用户账户](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 向用户帐户分配许可证](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除用户帐户的许可证](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [ConvertTo Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [选择对象](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>刚开始接触 Office 365？


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]