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
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 了解如何使用 Office 365 PowerShell 维护 Office 365 组中的成员身份。
ms.openlocfilehash: 397f8d93df5e9abef0779e4eb56df7bab9ef2344
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841479"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a><span data-ttu-id="e1482-103">使用 Office 365 PowerShell 维护组成员身份</span><span class="sxs-lookup"><span data-stu-id="e1482-103">Maintain group membership with Office 365 PowerShell</span></span>

<span data-ttu-id="e1482-104">您可以使用 Office 365 PowerShell 作为 Microsoft 365 管理中心的替代方法来维护 Office 365 中的组成员身份。</span><span class="sxs-lookup"><span data-stu-id="e1482-104">You can use Office 365 PowerShell as an alternative to the Microsoft 365 admin center to maintain group membership in Office 365.</span></span> 

> [!TIP]
> <span data-ttu-id="e1482-105">若要通过指定用户帐户和组名称生成现成的 PowerShell 命令，请使用此[组维护 Microsoft Excel 工作簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)。</span><span class="sxs-lookup"><span data-stu-id="e1482-105">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e1482-106">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1482-106">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="e1482-107">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="e1482-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="e1482-108">将用户帐户添加或删除为组的成员</span><span class="sxs-lookup"><span data-stu-id="e1482-108">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="e1482-109">**若要通过其 UPN 添加用户帐户**，请填写用户帐户用户主体名称（UPN）（示例： belindan@contoso.com）和组显示名称，删除 "<" 和 ">" 字符，并在 powershell 窗口或 Powershell 集成脚本环境（ISE）中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-109">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="e1482-110">**若要按照其显示名称添加用户帐户**，请填写用户帐户显示名称（示例： Belinda Newman）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-110">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="e1482-111">**若要通过其 UPN 删除用户帐户**，请填写用户帐户 UPN （示例： belindan@contoso.com）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-111">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="e1482-112">**若要按其显示名称删除用户帐户**，请填写用户帐户显示名称（示例： Belinda Newman）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-112">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="e1482-113">将组添加或删除为组的成员</span><span class="sxs-lookup"><span data-stu-id="e1482-113">Add or remove groups as members of a group</span></span>

<span data-ttu-id="e1482-114">安全组可以将其他组包含为成员。</span><span class="sxs-lookup"><span data-stu-id="e1482-114">Security groups can contain other groups as members.</span></span> <span data-ttu-id="e1482-115">但是，Office 365 组不能。</span><span class="sxs-lookup"><span data-stu-id="e1482-115">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="e1482-116">此部分包含 PowerShell 命令，仅用于为安全组添加或删除组。</span><span class="sxs-lookup"><span data-stu-id="e1482-116">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="e1482-117">**若要按照其显示名称添加组**，请填写要添加的组的显示名称和将包含该成员组的组的显示名称，并在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-117">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="e1482-118">**若要按其显示名称删除组**，请填写要删除的组的显示名称和将包含该成员组的组的显示名称，并在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-118">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e1482-119">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="e1482-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e1482-120">首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="e1482-120">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="e1482-121">将用户帐户添加或删除为组的成员</span><span class="sxs-lookup"><span data-stu-id="e1482-121">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="e1482-122">**若要通过其 UPN 添加用户帐户**，请填写用户帐户用户主体名称（UPN）（示例： belindan@contoso.com）和组显示名称，删除 "<" 和 ">" 字符，并在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-122">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="e1482-123">**若要按照其显示名称添加用户帐户**，请填写用户帐户显示名称（示例： Belinda Newman）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-123">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="e1482-124">**若要通过其 UPN 删除用户帐户**，请填写用户帐户 UPN （示例： belindan@contoso.com）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-124">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="e1482-125">**若要按其显示名称删除用户帐户**，请填写用户帐户显示名称（示例： Belinda Newman）和组显示名称，然后在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-125">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="e1482-126">将组添加或删除为组的成员</span><span class="sxs-lookup"><span data-stu-id="e1482-126">Add or remove groups as members of a group</span></span>

<span data-ttu-id="e1482-127">安全组可以将其他组包含为成员。</span><span class="sxs-lookup"><span data-stu-id="e1482-127">Security groups can contain other groups as members.</span></span> <span data-ttu-id="e1482-128">但是，Office 365 组不能。</span><span class="sxs-lookup"><span data-stu-id="e1482-128">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="e1482-129">此部分包含 PowerShell 命令，仅用于为安全组添加或删除组。</span><span class="sxs-lookup"><span data-stu-id="e1482-129">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="e1482-130">**若要按照其显示名称添加组**，请填写要添加的组的显示名称和将包含该成员组的组的显示名称，并在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-130">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="e1482-131">**若要按其显示名称删除组**，请填写要删除的组的显示名称和将包含该成员组的组的显示名称，并在 powershell 窗口或 powershell ISE 中运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1482-131">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="e1482-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1482-132">See also</span></span>

[<span data-ttu-id="e1482-133">使用 Office 365 PowerShell 管理用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="e1482-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e1482-134">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="e1482-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e1482-135">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="e1482-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

