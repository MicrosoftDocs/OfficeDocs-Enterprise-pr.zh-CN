---
title: 使用集中部署 PowerShell cmdlet 管理外接程序
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2020
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
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
ms.custom:
- seo-marvel-apr2020
description: 使用集中部署 PowerShell cmdlet 可帮助您部署和管理适用于 Microsoft 365 组织的 Office 外接程序。
ms.openlocfilehash: 849e27dc3bda5dc9e6b4f45bc100e896eae3e281
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605344"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="d61b8-103">使用集中部署 PowerShell cmdlet 管理外接程序</span><span class="sxs-lookup"><span data-stu-id="d61b8-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="d61b8-104">作为 Microsoft 365 全局管理员，你可以通过集中部署功能向用户部署 Office 外接程序 (请参阅[在管理中心部署 Office 加载项](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins)) 。</span><span class="sxs-lookup"><span data-stu-id="d61b8-104">As a Microsoft 365 global admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the admin center](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins)).</span></span> <span data-ttu-id="d61b8-105">除了通过 Microsoft 365 管理中心部署 Office 外接程序之外，你还可以使用 Microsoft PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d61b8-105">In addition to deploying Office add-ins via the Microsoft 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="d61b8-106">安装[适用于 Windows PowerShell 的 O365 集中外接程序部署模块](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)。</span><span class="sxs-lookup"><span data-stu-id="d61b8-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 

<span data-ttu-id="d61b8-107">下载模块后，打开一个常规的 Windows PowerShell 窗口并运行以下 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="d61b8-107">After you download the module, open a regular Windows PowerShell window and run the following cmdlet:</span></span>

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="d61b8-108">使用管理员凭据连接</span><span class="sxs-lookup"><span data-stu-id="d61b8-108">Connect using your admin credentials</span></span>

<span data-ttu-id="d61b8-109">必须先登录，然后才能使用集中部署 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d61b8-109">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="d61b8-110">启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d61b8-110">Start PowerShell.</span></span>
    
2. <span data-ttu-id="d61b8-111">使用您的公司管理员凭据连接到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d61b8-111">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="d61b8-112">运行以下 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d61b8-112">Run the following cmdlet.</span></span>
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="d61b8-113">在 "**输入凭据**" 页面中，输入你的 Microsoft 365 全局管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="d61b8-113">In the **Enter Credentials** page, enter your Microsoft 365 global admin credentials.</span></span> <span data-ttu-id="d61b8-114">或者，也可以直接在 cmdlet 中输入您的凭据。</span><span class="sxs-lookup"><span data-stu-id="d61b8-114">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="d61b8-115">运行以下 cmdlet，将您的公司管理员凭据指定为 PSCredential 对象。</span><span class="sxs-lookup"><span data-stu-id="d61b8-115">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="d61b8-116">有关使用 PowerShell 的详细信息，请参阅[Connect To Microsoft 365 With powershell](https://go.microsoft.com/fwlink/p/?linkid=848585)。</span><span class="sxs-lookup"><span data-stu-id="d61b8-116">For more information about using PowerShell, see [Connect to Microsoft 365 with PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="d61b8-117">上载外接程序清单</span><span class="sxs-lookup"><span data-stu-id="d61b8-117">Upload an add-in manifest</span></span>

<span data-ttu-id="d61b8-118">运行**organizationadd-in** cmdlet 以从路径（可以是文件位置或 URL）上传外接程序清单。</span><span class="sxs-lookup"><span data-stu-id="d61b8-118">Run the **New-OrganizationAdd-In** cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="d61b8-119">下面的示例演示_ManifestPath_参数值的文件位置。</span><span class="sxs-lookup"><span data-stu-id="d61b8-119">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="d61b8-120">您还可以运行**organizationadd-in** cmdlet 以上载外接程序，并使用_Members_参数直接将其分配给用户或组，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d61b8-120">You can also run the **New-OrganizationAdd-In** cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="d61b8-121">使用逗号分隔成员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="d61b8-121">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="d61b8-122">从 Office 应用商店上载外接程序</span><span class="sxs-lookup"><span data-stu-id="d61b8-122">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="d61b8-123">运行**OrganizationAddIn** cmdlet，从 Office 应用商店上传清单。</span><span class="sxs-lookup"><span data-stu-id="d61b8-123">Run the **New-OrganizationAddIn** cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="d61b8-124">在以下示例中， **OrganizationAddIn** Cmdlet 为美国位置和内容市场的外接程序指定 AssetId。</span><span class="sxs-lookup"><span data-stu-id="d61b8-124">In the following example, the **New-OrganizationAddIn** cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="d61b8-125">若要确定_AssetId_参数的值，可以从外接程序的 Office 应用商店网页的 URL 复制它。</span><span class="sxs-lookup"><span data-stu-id="d61b8-125">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="d61b8-126">AssetIds 始终以 "WA" 开头，后跟一个数字。</span><span class="sxs-lookup"><span data-stu-id="d61b8-126">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="d61b8-127">例如，在上一示例中，WA104099688 的 AssetId 值的源是外接程序的 Office 应用商店网页 URL： [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688) 。</span><span class="sxs-lookup"><span data-stu-id="d61b8-127">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="d61b8-128">_Locale_参数和_ContentMarket_参数的值是相同的，并指示您要从中安装外接程序的国家/地区。</span><span class="sxs-lookup"><span data-stu-id="d61b8-128">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="d61b8-129">格式为 en-us，fr-fr。</span><span class="sxs-lookup"><span data-stu-id="d61b8-129">The format is en-US, fr-FR.</span></span> <span data-ttu-id="d61b8-130">等。</span><span class="sxs-lookup"><span data-stu-id="d61b8-130">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="d61b8-131">从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。</span><span class="sxs-lookup"><span data-stu-id="d61b8-131">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="d61b8-132">获取外接程序的详细信息</span><span class="sxs-lookup"><span data-stu-id="d61b8-132">Get details of an add-in</span></span>

<span data-ttu-id="d61b8-133">运行以下所示的**OrganizationAddIn** cmdlet，以获取上载到租户的所有加载项的详细信息，包括加载项的产品 ID。</span><span class="sxs-lookup"><span data-stu-id="d61b8-133">Run the **Get-OrganizationAddIn** cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```powershell
Get-OrganizationAddIn
```

<span data-ttu-id="d61b8-134">运行**OrganizationAddIn** Cmdlet 和_ProductId_参数的值，以指定要检索其详细信息的外接程序。</span><span class="sxs-lookup"><span data-stu-id="d61b8-134">Run the **Get-OrganizationAddIn** cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="d61b8-135">若要获取所有外接程序的完整详细信息以及分配的用户和组，请将**OrganizationAddIn** cmdlet 的输出通过管道传递给格式列表 cmdlet，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d61b8-135">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the **Get-OrganizationAddIn** cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="d61b8-136">打开或关闭外接程序</span><span class="sxs-lookup"><span data-stu-id="d61b8-136">Turn on or turn off an add-in</span></span>

<span data-ttu-id="d61b8-137">若要关闭外接程序，以便向其分配了的用户和组将不再具有访问权限，请运行带有_ProductId_参数的**OrganizationAddIn** Cmdlet，并将_Enabled_参数设置为 `$false` ，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d61b8-137">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="d61b8-138">若要重新打开外接程序，请运行相同的 cmdlet，并将_Enabled_参数设置为 `$true` 。</span><span class="sxs-lookup"><span data-stu-id="d61b8-138">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="d61b8-139">在外接程序中添加或删除用户</span><span class="sxs-lookup"><span data-stu-id="d61b8-139">Add or remove users from an add-in</span></span>

<span data-ttu-id="d61b8-140">若要将用户和组添加到特定加载项，请运行**OrganizationAddInAssignments** Cmdlet 和_ProductId_、 _add_和_Members_参数。</span><span class="sxs-lookup"><span data-stu-id="d61b8-140">To add users and groups to a specific add-in, run the **Set-OrganizationAddInAssignments** cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="d61b8-141">使用逗号分隔成员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="d61b8-141">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="d61b8-142">若要删除用户和组，请使用_remove_参数运行相同的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d61b8-142">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="d61b8-143">若要将外接程序分配给租户上的所有用户，请使用_AssignToEveryone_参数（其值设置为）运行相同的 cmdlet `$true` 。</span><span class="sxs-lookup"><span data-stu-id="d61b8-143">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="d61b8-144">若要不向每个人分配外接程序并将其还原到以前分配的用户和组，您可以运行同一 cmdlet，并通过将_AssignToEveryone_参数的值设置为来关闭该参数 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="d61b8-144">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="d61b8-145">更新外接程序</span><span class="sxs-lookup"><span data-stu-id="d61b8-145">Update an add-in</span></span>

<span data-ttu-id="d61b8-146">若要从清单更新外接程序，请运行**OrganizationAddIn** Cmdlet 和_ProductId_、 _ManifestPath_和_Locale_参数，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="d61b8-146">To update an add-in from a manifest, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="d61b8-147">从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。</span><span class="sxs-lookup"><span data-stu-id="d61b8-147">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="d61b8-148">删除外接程序</span><span class="sxs-lookup"><span data-stu-id="d61b8-148">Delete an add-in</span></span>

<span data-ttu-id="d61b8-149">若要删除外接程序，请运行带有_ProductId_参数的**OrganizationAddIn** cmdlet，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="d61b8-149">To delete an add-in, run the **Remove-OrganizationAddIn** cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<!--
## Customize Microsoft Store add-ins for your organization

You must customize the add-in before you deploy it to your organization. Add-ins older than version 1.1 are not supported by this feature. 

We recommend that you deploy a customized add-in  to yourself first to make sure it works as expected before you deploy it to your entire organization.

Note also the following restrictions:
- All URLs must be absolute (include http or https) and valid.
- *DisplayName* must not exceed 125 characters 
- *DisplayName*, *Resources* and *AppDomains* must not include the following characters: 
 
    - \<
    -  \>
    -  ;
    -  =   

If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.

To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value. To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article. For example:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg" 
```
To customize multiple tags for an add-in, add those tags to the commandline:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg" 
```

> [!IMPORTANT]
> You must apply multiple customized tags to one add-in as one command. If you customize tags one by one, only the last customization will be applied. Additionally, if you customize a tag by mistake, you must remove all customizations and start over.

### Tags you can customize

| Tag                  | Description          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| The URL of the image used as the add-in’s icon (in admin center). </br> |
| \<DisplayName>| The title of the add-in  (in admin center).|
| \<Hosts>| List of apps that will support the add-in.|
| \<SourceLocation> | The source URL that the add-in will connect to.| 
| \<AppDomains> | A list of domains that the add-in can connect with. | 
| \<SupportURL>| The URL users can use to access help and support. | 
| \<Resources>  | This tag contains a number of elements including titles, tooltips, and icons of different sizes.| 
|
### Customize Resources tag

Any element in the <Resources> tag of the manifest can be customized dynamically. You first need to check the manifest to find the element id to which you want to assign a new value. The <Resources> tag looks like this:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”https://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”

Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

You can customize as many elements with the command as you need to.

### Remove customization from an add-in

The only option currently available for deleting customizations is to delete all of them at once:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### View add-in customizations

To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet. If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.  

```powershell
Get-OrganizationAddInOverrides 
```
If ProductId is specified, then a list of overrides applied to that add-in is returned. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### Remove an add-in from local cache

If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized. To remive an add-in from cache:

1. Navigate to the “Users” folder in C:\ 
1. Go to your user folder
1. Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office
1. In the *Wef* folder delete the *Manifests* folder.

-->

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="d61b8-150">获取每个 cmdlet 的详细帮助</span><span class="sxs-lookup"><span data-stu-id="d61b8-150">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="d61b8-151">您可以使用 Get-help cmdlet 查看每个 cmdlet 的详细帮助信息。</span><span class="sxs-lookup"><span data-stu-id="d61b8-151">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="d61b8-152">例如，以下 cmdlet 提供有关 OrganizationAddIn cmdlet 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d61b8-152">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


