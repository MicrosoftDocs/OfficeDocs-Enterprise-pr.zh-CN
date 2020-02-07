---
title: 使用集中部署 PowerShell cmdlet 管理外接程序
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 使用集中部署 PowerShell cmdlet 可帮助您部署和管理 Office 365 组织的 Office 外接程序。
ms.openlocfilehash: 586b66ac3632a5d86a63014a50f3c605b1c005e7
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844153"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>使用集中部署 PowerShell cmdlet 管理外接程序

作为 Office 365 管理员，您可以通过集中部署功能向用户部署 Office 外接程序（请参阅[在管理中心中管理 Office 365 外接程序的部署](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)）。 除了通过管理中心部署 Office 加载项外，还可以使用 Microsoft PowerShell。 从 Microsoft 下载中心[下载](https://go.microsoft.com/fwlink/p/?linkid=850850)集中部署 PowerShell cmdlet。 
  
## <a name="what-do-you-want-to-do"></a>要执行什么操作？

[使用管理员凭据连接](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[上载外接程序清单](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[从 Office 应用商店上载外接程序](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[获取外接程序的详细信息](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[打开或关闭外接程序](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[在外接程序中添加或删除用户](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[更新外接程序](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[删除外接程序](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[获取每个 cmdlet 的详细帮助](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>使用管理员凭据连接
<a name="BKMK_Connect"> </a>

必须先登录，然后才能使用集中部署 cmdlet。
  
1. 启动 PowerShell。
    
2. 使用您的公司管理员凭据连接到 PowerShell。 运行以下 cmdlet。
    
  ```
  Connect-OrganizationAddInService
  ```

3. 在 "**输入凭据**" 页面中，输入 Office 365 全局管理员凭据。 或者，也可以直接在 cmdlet 中输入您的凭据。 
    
    运行以下 cmdlet，将您的公司管理员凭据指定为 PSCredential 对象。
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> 有关使用 PowerShell 的详细信息，请参阅[连接到 Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)。 
  
## <a name="upload-an-add-in-manifest"></a>上载外接程序清单
<a name="BKMK_UploadManifest"> </a>

运行 Organizationadd-in cmdlet 以从路径（可以是文件位置或 URL）上传外接程序清单。 下面的示例演示_ManifestPath_参数值的文件位置。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

您还可以运行 Organizationadd-in cmdlet 以上载外接程序，并使用_Members_参数直接将其分配给用户或组，如下面的示例所示。 使用逗号分隔成员的电子邮件地址。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>从 Office 应用商店上载外接程序
<a name="BKMK_UploadAddin"> </a>

运行 OrganizationAddIn cmdlet，从 Office 应用商店上传清单。
  
在以下示例中，OrganizationAddIn cmdlet 为美国位置和内容市场的外接程序指定 AssetId。
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

若要确定_AssetId_参数的值，可以从外接程序的 Office 应用商店网页的 URL 复制它。 AssetIds 始终以 "WA" 开头，后跟一个数字。 例如，在上一示例中，WA104099688 的 AssetId 值的源是外接程序的 Office 应用商店网页 URL： [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。
  
_Locale_参数和_ContentMarket_参数的值是相同的，并指示您要从中安装外接程序的国家/地区。 格式为 en-us，fr-fr。 等。 
  
> [!NOTE]
> 从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。 
  
## <a name="get-details-of-an-add-in"></a>获取外接程序的详细信息
<a name="BKMK_GetDetails"> </a>

运行以下所示的 OrganizationAddIn cmdlet，以获取上载到租户的所有加载项的详细信息，包括加载项的产品 ID。
  
```
Get-OrganizationAddIn
```

运行 OrganizationAddIn cmdlet 和_ProductId_参数的值，以指定要检索其详细信息的外接程序。 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

若要获取所有外接程序的完整详细信息以及分配的用户和组，请将 OrganizationAddIn cmdlet 的输出通过管道传递给格式列表 cmdlet，如下面的示例所示。
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>打开或关闭外接程序
<a name="BKMK_TurnOnOff"> </a>

若要关闭外接程序，以便向其分配了的用户和组将不再具有访问权限，请运行带有_ProductId_参数的 OrganizationAddIn cmdlet，并将_Enabled_参数设置为`$false`，如下面的示例所示。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

若要重新打开外接程序，请运行相同的 cmdlet，并将_Enabled_参数设置`$true`为。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>在外接程序中添加或删除用户
<a name="BKMK_AddRemove"> </a>

若要将用户和组添加到特定加载项，请运行 OrganizationAddInAssignments cmdlet 和_ProductId_、 _add_和_Members_参数。 使用逗号分隔成员的电子邮件地址。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

若要删除用户和组，请使用_remove_参数运行相同的 cmdlet。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

若要将外接程序分配给租户上的所有用户，请使用_AssignToEveryone_参数（其值设置为`$true`）运行相同的 cmdlet。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

若要不向每个人分配外接程序并将其还原到以前分配的用户和组，您可以运行同一 cmdlet，并通过将_AssignToEveryone_参数的值设置`$false`为来关闭该参数。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>更新外接程序
<a name="BKMK_UpdateAddin"> </a>

若要从清单更新外接程序，请运行 OrganizationAddIn cmdlet 和_ProductId_、 _ManifestPath_和_Locale_参数，如以下示例中所示。 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> 从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。 
  
## <a name="delete-an-add-in"></a>删除外接程序
<a name="BKMK_Delete"> </a>

若要删除外接程序，请运行带有_ProductId_参数的 OrganizationAddIn cmdlet，如以下示例所示。 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>获取每个 cmdlet 的详细帮助
<a name="BKMK_GetHelp"> </a>

您可以使用 Get-help cmdlet 查看每个 cmdlet 的详细帮助信息。 例如，以下 cmdlet 提供有关 OrganizationAddIn cmdlet 的详细信息。
  
```
Get-help Remove-OrganizationAddIn -Full
```


