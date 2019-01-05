---
title: 使用 Office 365 PowerShell 查看授权和未授权的用户
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
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: 介绍如何使用 Office 365 PowerShell 查看授权和未授权的用户帐户。
ms.openlocfilehash: 79f7bf1966d515634c5fc038db650c19547259aa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730337"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>使用 Office 365 PowerShell 查看授权和未授权的用户

**摘要：** 介绍如何使用 Office 365 PowerShell 查看许可和非许可用户帐户。
  
您的 Office 365 组织中的用户帐户可能已从组织提供的许可计划中分配到部分或全部可用的许可证，或者未分配到任何许可证。您可以使用 Office 365 PowerShell 快速查找您组织中的授权和未授权的用户。


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用 Azure Active Directory PowerShell 图模块

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
 
若要查看组织中尚未分配任何许可计划 （未经授权的用户） 的所有用户帐户的列表，请运行以下命令：
  
```
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

若要查看所有用户帐户的列表，组织中的已分配任何您许可计划 （许可用户），运行以下命令：
  
```
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用 Windows PowerShell 的 Microsoft Azure Active Directory 模块

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

若要查看组织中所有用户帐户及其授权状态的列表，请在 Office 365 PowerShell 中运行以下命令：
  
```
Get-MsolUser -All
```

若要查看组织中所有未授权用户帐户的列表，请运行以下命令：
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

若要查看组织中所有授权用户帐户的列表，请运行以下命令：
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
