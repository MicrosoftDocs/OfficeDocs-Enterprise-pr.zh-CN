---
title: 使用集中部署 PowerShell cmdlet 管理加载项
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 使用集中部署 PowerShell cmdlet 可帮助您部署和管理 Office 加载项为 Office 365 组织。
ms.openlocfilehash: f15bd1048d9240a125a1ae8245c773d83c6c935d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539559"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>使用集中部署 PowerShell cmdlet 管理加载项

为 Office 365 管理员，可向通过集中部署的用户部署 Office 加载项功能 （请参阅[管理 Office 365 中的加载项在 Office 365 管理中心的部署](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)）。除了部署 Office 加载项通过 Office 365 管理中心，您还可以使用 Microsoft PowerShell。[下载](https://go.microsoft.com/fwlink/p/?linkid=850850)从 Microsoft 下载中心下载的集中部署 PowerShell cmdlet。 
  
## <a name="what-do-you-want-to-do"></a>要执行什么操作？

[使用管理员凭据连接](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[上载的外接程序清单](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[上载外接程序从 Office 商店](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[获取外接程序的详细信息](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[打开或关闭外接程序](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[添加或删除的用户外接程序](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[外接程序更新](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[删除外接程序](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[每个 cmdlet 获得详细的帮助](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>使用管理员凭据连接
<a name="BKMK_Connect"> </a>

您可以使用集中部署 cmdlet 之前，您需要登录。
  
1. 启动 PowerShell。
    
2. 使用您的公司管理员凭据连接到 PowerShell。运行以下 cmdlet。
    
  ```
  Connect-OrganizationAddInService
  ```

3. 在**输入凭据**页上，输入您的 Office 365 全局管理员凭据。另外，您可以直接在 cmdlet 输入您的凭据。 
    
    运行以下 cmdlet 指定您的公司管理员凭据作为 PSCredential 对象。
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> 有关使用 PowerShell 的详细信息，请参阅[Connect to Office 365 PowerShell 中](https://go.microsoft.com/fwlink/p/?linkid=848585)。 
  
## <a name="upload-an-add-in-manifest"></a>上载的外接程序清单
<a name="BKMK_UploadManifest"> </a>

运行新建入式 OrganizationAdd cmdlet 来上载外接程序将清单从路径，它可以是一个文件位置或 URL。下面的示例演示_ManifestPath_参数的值的文件位置。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

您还可以运行新建入式 OrganizationAdd cmdlet 来上载外接程序，并将其分配给用户或组直接使用_Members_参数，如下面的示例中所示。用逗号分隔成员的电子邮件的地址。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>上载外接程序从 Office 商店
<a name="BKMK_UploadAddin"> </a>

运行新建 OrganizationAddIn cmdlet 来上载来自 Office 商店的清单。
  
在以下示例中，新建 OrganizationAddIn cmdlet 指定 AssetId 美国位置和内容市场的加载项。
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

若要确定_AssetId_参数的值，可以将其复制从 Office 商店网页加载 AssetIds 始终开始使用"WA"跟一个数字的 URL。例如，在上一示例中，WA104099688 AssetId 值的源是加载项的 Office 应用商店网页 URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。
  
_Locale_参数和_ContentMarket_参数的值相同，并指明您尝试安装外接程序从国家/地区。格式为 EN-US、 fr 法属等。 
  
> [!NOTE]
> 在 Office 商店正在可用的最新更新的几天内，从 Office 商店上载的加载项将自动更新。 
  
## <a name="get-details-of-an-add-in"></a>获取外接程序的详细信息
<a name="BKMK_GetDetails"> </a>

运行 Get OrganizationAddIn cmdlet，如下所示以获取详细信息的所有加载项上载到租户，包括外接程序的产品 id。
  
```
Get-OrganizationAddIn
```

使用_ProductId_参数指定该外接程序您想要检索的详细信息的值与运行 Get OrganizationAddIn cmdlet。 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

要获取的所有加载项以及分配给的用户和组的完整详细信息，请输出通过管道传递到 Format-list cmdlet，获取 OrganizationAddIn cmdlet 的以下示例中所示。
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>打开或关闭外接程序
<a name="BKMK_TurnOnOff"> </a>

若要关闭外接程序以便用户和组分配给它将不再能够访问，运行设置 OrganizationAddIn cmdlet 与_ProductId_参数和_Enabled_参数设置为`$false`，如下面的示例所示。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

要启用外接程序后，请运行带有_Enabled_参数设置为同一 cmdlet `$true`。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>添加或删除的用户外接程序
<a name="BKMK_AddRemove"> </a>

要添加到特定的加载项的用户和组，请运行带有_ProductId_，_添加_和_成员_参数集 OrganizationAddInAssignments cmdlet。用逗号分隔成员的电子邮件的地址。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

要删除的用户和组，请运行相同 cmdlet 使用_删除_参数。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

要分配租户上的所有用户外接程序，请运行相同 cmdlet 使用_AssignToEveryone_参数以及其值设置为`$true`。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

若要不向每个人分配外接程序，并还原到先前分配的用户和组，可以运行相同 cmdlet，并通过其值设置为关闭_AssignToEveryone_参数`$false`。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>外接程序更新
<a name="BKMK_UpdateAddin"> </a>

若要更新外接程序的清单中，运行_ProductId_、 _ManifestPath_，和_区域设置_参数集 OrganizationAddIn cmdlet 下面的示例中所示。 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> 在 Office 商店正在可用的最新更新的几天内，从 Office 商店上载的加载项将自动更新。 
  
## <a name="delete-an-add-in"></a>删除外接程序
<a name="BKMK_Delete"> </a>

若要删除外接程序，请使用_ProductId_参数中，运行删除 OrganizationAddIn cmdlet 下面的示例中所示。 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>每个 cmdlet 获得详细的帮助
<a name="BKMK_GetHelp"> </a>

您可以通过使用 get-help cmdlet 查看每个 cmdlet 的帮助详细信息。例如，以下 cmdlet 提供了有关删除 OrganizationAddIn cmdlet 的详细的信息。
  
```
Get-help Remove-OrganizationAddIn -Full
```


