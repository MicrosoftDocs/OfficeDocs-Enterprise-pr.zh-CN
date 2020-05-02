---
title: 使用 Office 365 PowerShell 维护组成员身份
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 了解如何使用 Office 365 PowerShell 维护 Office 365 组中的成员身份。
ms.openlocfilehash: 0e6c5f2e27f9d146bb2a053bd3bdb6694fb07276
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004625"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a>使用 Office 365 PowerShell 维护组成员身份

您可以使用 Office 365 PowerShell 作为 Microsoft 365 管理中心的替代方法来维护 Office 365 中的组成员身份。 

> [!TIP]
> 若要通过指定用户帐户和组名称生成现成的 PowerShell 命令，请使用此[组维护 Microsoft Excel 工作簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)。 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell
首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>将用户帐户添加或删除为组的成员

**若要通过其 UPN 添加用户帐户**，请填写用户帐户用户主体名称（UPN）（示例： belindan@contoso.com）和组显示名称，删除 "<" 和 ">" 字符，并在 powershell 窗口或 Powershell 集成脚本环境（ISE）中运行这些命令。

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要按照其显示名称添加用户帐户**，请填写用户帐户显示名称（示例： Belinda Newman）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要通过其 UPN 删除用户帐户**，请填写用户帐户 UPN （示例： belindan@contoso.com）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要按其显示名称删除用户帐户**，请填写用户帐户显示名称（示例： Belinda Newman）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>将组添加或删除为组的成员

安全组可以将其他组包含为成员。 但是，Office 365 组不能。 此部分包含 PowerShell 命令，仅用于为安全组添加或删除组。

**若要按照其显示名称添加组**，请填写要添加的组的显示名称和将包含该成员组的组的显示名称，并在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要按其显示名称删除组**，请填写要删除的组的显示名称和将包含该成员组的组的显示名称，并在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>将用户帐户添加或删除为组的成员

**若要通过其 UPN 添加用户帐户**，请填写用户帐户用户主体名称（UPN）（示例： belindan@contoso.com）和组显示名称，删除 "<" 和 ">" 字符，并在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要按照其显示名称添加用户帐户**，请填写用户帐户显示名称（示例： Belinda Newman）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要通过其 UPN 删除用户帐户**，请填写用户帐户 UPN （示例： belindan@contoso.com）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要按其显示名称删除用户帐户**，请填写用户帐户显示名称（示例： Belinda Newman）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>将组添加或删除为组的成员

安全组可以将其他组包含为成员。 但是，Office 365 组不能。 此部分包含 PowerShell 命令，仅用于为安全组添加或删除组。

**若要按照其显示名称添加组**，请填写要添加的组的显示名称和将包含该成员组的组的显示名称，并在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**若要按其显示名称删除组**，请填写要删除的组的显示名称和将包含该成员组的组的显示名称，并在 powershell 窗口或 powershell ISE 中运行这些命令。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理用户帐户、许可证和组](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

