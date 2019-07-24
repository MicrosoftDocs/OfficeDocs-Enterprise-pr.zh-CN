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
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 使用集中部署 PowerShell cmdlet 可帮助您部署和管理 Office 365 组织的 Office 外接程序。
ms.openlocfilehash: 301e44da4c663fa54c4e2b753552b0b345e2a6e5
ms.sourcegitcommit: 9cd3dcf1e90b21c7651d367dcd3306d6fe0bcbcb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "35834232"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>使用集中部署 PowerShell cmdlet 管理外接程序

作为 Microsoft 365 全局或 Exchange 管理员, 您可以通过集中部署功能向用户部署 Office 外接程序 (请参阅[在管理中心部署 Office 加载项](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx))。 除了通过 Microsoft 365 管理中心部署 Office 外接程序之外, 你还可以使用 Microsoft PowerShell。 安装[适用于 Windows PowerShell 的 O365 集中外接程序部署模块](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)。 

下载模块后, 打开一个常规的 Windows PowerShell 窗口并运行以下 cmdlet:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>使用管理员凭据连接

必须先登录, 然后才能使用集中部署 cmdlet。
  
1. 启动 PowerShell。
    
2. 使用您的公司管理员凭据连接到 PowerShell。 运行以下 cmdlet。
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. 在 "**输入凭据**" 页面中, 输入 Office 365 全局管理员凭据。 或者, 也可以直接在 cmdlet 中输入您的凭据。 
    
    运行以下 cmdlet, 将您的公司管理员凭据指定为 PSCredential 对象。
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> 有关使用 PowerShell 的详细信息, 请参阅[连接到 Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)。 
  
## <a name="upload-an-add-in-manifest"></a>上载外接程序清单

运行**organizationadd-in** cmdlet 以从路径 (可以是文件位置或 URL) 上传外接程序清单。 下面的示例演示_ManifestPath_参数值的文件位置。 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

您还可以运行**organizationadd-in** cmdlet 以上载外接程序, 并使用_Members_参数直接将其分配给用户或组, 如下面的示例所示。 使用逗号分隔成员的电子邮件地址。 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>从 Office 应用商店上载外接程序

运行**OrganizationAddIn** cmdlet, 从 Office 应用商店上传清单。
  
在以下示例中, **OrganizationAddIn** Cmdlet 为美国位置和内容市场的外接程序指定 AssetId。
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

若要确定_AssetId_参数的值, 可以从外接程序的 Office 应用商店网页的 URL 复制它。 AssetIds 始终以 "WA" 开头, 后跟一个数字。 例如, 在上一示例中, WA104099688 的 AssetId 值的源是外接程序的 Office 应用商店网页 URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。
  
_Locale_参数和_ContentMarket_参数的值是相同的, 并指示您要从中安装外接程序的国家/地区。 格式为 en-us, fr-fr。 等。 
  
> [!NOTE]
> 从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。 
  
## <a name="get-details-of-an-add-in"></a>获取外接程序的详细信息

运行以下所示的**OrganizationAddIn** cmdlet, 以获取上载到租户的所有加载项的详细信息, 包括加载项的产品 ID。
  
```powershell
Get-OrganizationAddIn
```

运行**OrganizationAddIn** Cmdlet 和_ProductId_参数的值, 以指定要检索其详细信息的外接程序。 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

若要获取所有外接程序的完整详细信息以及分配的用户和组, 请将**OrganizationAddIn** cmdlet 的输出通过管道传递给格式列表 cmdlet, 如下面的示例所示。
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>打开或关闭外接程序

若要关闭外接程序, 以便向其分配了的用户和组将不再具有访问权限, 请运行带有_ProductId_参数的**OrganizationAddIn** Cmdlet, 并将_Enabled_参数设置为`$false`, 如以下示例所示.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

若要重新打开外接程序, 请运行相同的 cmdlet, 并将_Enabled_参数设置`$true`为。
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>在外接程序中添加或删除用户

若要将用户和组添加到特定加载项, 请运行**OrganizationAddInAssignments** Cmdlet 和_ProductId_、 _add_和_Members_参数。 使用逗号分隔成员的电子邮件地址。 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

若要删除用户和组, 请使用_remove_参数运行相同的 cmdlet。 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

若要将外接程序分配给租户上的所有用户, 请使用_AssignToEveryone_参数 (其值设置为`$true`) 运行相同的 cmdlet。
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

若要不向每个人分配外接程序并将其还原到以前分配的用户和组, 您可以运行同一 cmdlet, 并通过将_AssignToEveryone_参数的值设置`$false`为来关闭该参数。
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>更新外接程序

若要从清单更新外接程序, 请运行**OrganizationAddIn** Cmdlet 和_ProductId_、 _ManifestPath_和_Locale_参数, 如以下示例中所示。 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> 从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。 
  
## <a name="delete-an-add-in"></a>删除外接程序

若要删除外接程序, 请运行带有_ProductId_参数的**OrganizationAddIn** cmdlet, 如以下示例所示。 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a>为你的组织自定义 Microsoft Store 外接程序

必须先自定义外接程序, 然后才能将其部署到组织中。 此功能不支持早于版本1.1 的外接程序。 

我们建议您先将自定义加载项部署到自己, 以确保它按预期工作, 然后再将其部署到整个组织。

另请注意以下限制:
- 所有 Url 都必须是绝对 Url (包括 http 或 https) 且有效。
- *DisplayName*不得超过125个字符 
- *DisplayName*、*资源*和*appdomain*不能包含以下字符: 
 
    - \<
    -  \>
    -  ;
    -  =   

如果要自定义已部署的加载项, 则必须将其卸载到管理中心, 并查看 "[从本地缓存中删除加载项](#remove-an-add-in-from-local-cache)", 以了解将其从已部署到的每台计算机中删除的步骤。

若要自定义外接程序, 请运行**OrganizationAddInOverrides** Cmdlet 和*ProductId*作为参数, 后跟要覆盖的标记和新值。 若要了解如何获取*产品 id* , 请参阅本文中的获取外接程序的[详细信息](#get-details-of-an-add-in)。 例如：

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
若要自定义外接程序的多个标记, 请将这些标记添加到命令行中:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> 您必须将多个自定义标记作为一个命令应用于一个加载项。 如果逐个自定义标记, 则只会应用最后一个自定义项。 此外, 如果错误地自定义标记, 则必须删除所有自定义项并重新开始。

### <a name="tags-you-can-customize"></a>您可以自定义的标记

| Tag                  | 说明          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| 用作加载项图标的图像的 URL (在管理中心中)。 </br> |
| \<DisplayName>| 加载项的标题 (在管理中心中)。|
| \<主机>| 将支持外接程序的应用程序的列表。|
| \<SourceLocation> | 外接程序将连接到的源 URL。| 
| \<Appdomain> | 外接程序可与之连接的域的列表。 | 
| \<SupportURL>| 用户可用于访问帮助和支持的 URL。 | 
| \<资源>  | 此标记包含多个元素, 包括标题、工具提示和不同大小的图标。| 
|
### <a name="customize-resources-tag"></a>自定义 Resources 标记

可以动态自定义<Resources>清单标记中的任何元素。 首先需要检查清单以查找要向其分配新值的元素 id。 <Resources>标记如下所示:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
在这种情况下, 图像的元素 id 为 "img16icon", 与关联的值为 "http:<i></i>//site。<i> </i>com/img. "

确定要自定义的元素后, 请在 Powershell 中使用以下命令将新值分配给这些元素:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

您可以根据需要自定义多个元素和命令。

### <a name="remove-customization-from-an-add-in"></a>从外接程序中删除自定义项

当前可用于删除自定义项的唯一选项是一次性删除所有自定义项:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a>查看加载项自定义项

若要查看已应用的自定义项列表, 请运行**OrganizationAddInOverrides** cmdlet。 如果在没有*ProductId*的情况下运行**OrganizationAddInOverrides** , 则将返回所有应用了替代的外接程序的列表。  

```powershell
Get-OrganizationAddInOverrides 
```
如果指定了 ProductId, 则将返回应用于该外接程序的替代项列表。 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a>从本地缓存中删除外接程序

如果已部署加载项, 则必须先将其从每台计算机的缓存中删除, 然后才能对其进行自定义。 从缓存中 remive 外接程序:

1. 导航到 C:\ 中的 "Users" 文件夹 
1. 转到您的用户文件夹
1. 导航到 "AppData\Local\Microsoft\Office", 然后选择与您的 Office 版本相关联的文件夹
1. 在 " *Wef* " 文件夹中, 删除 "*清单*" 文件夹。

## <a name="get-detailed-help-for-each-cmdlet"></a>获取每个 cmdlet 的详细帮助

您可以使用 Get-help cmdlet 查看每个 cmdlet 的详细帮助信息。 例如, 以下 cmdlet 提供有关 OrganizationAddIn cmdlet 的详细信息。
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


