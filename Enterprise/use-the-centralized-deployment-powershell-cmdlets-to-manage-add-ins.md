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
ms.openlocfilehash: 34040d11a1ef4d5da2d7a0e980b28e7ef0eba7fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070498"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="165a7-103">使用集中部署 PowerShell cmdlet 管理外接程序</span><span class="sxs-lookup"><span data-stu-id="165a7-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="165a7-104">作为 Office 365 管理员, 您可以通过集中部署功能向用户部署 Office 外接程序 (请参阅[在 office 365 管理中心部署 Office 加载项](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx))。</span><span class="sxs-lookup"><span data-stu-id="165a7-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="165a7-105">除了通过 Office 365 管理中心部署 Office 外接程序之外, 还可以使用 Microsoft PowerShell。</span><span class="sxs-lookup"><span data-stu-id="165a7-105">In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="165a7-106">安装[适用于 Windows PowerShell 的 O365 集中外接程序部署模块](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)。</span><span class="sxs-lookup"><span data-stu-id="165a7-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="165a7-107">使用管理员凭据连接</span><span class="sxs-lookup"><span data-stu-id="165a7-107">Connect using your admin credentials</span></span>

<span data-ttu-id="165a7-108">必须先登录, 然后才能使用集中部署 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="165a7-108">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="165a7-109">启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="165a7-109">Start PowerShell.</span></span>
    
2. <span data-ttu-id="165a7-110">使用您的公司管理员凭据连接到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="165a7-110">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="165a7-111">运行以下 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="165a7-111">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="165a7-112">在 "**输入凭据**" 页面中, 输入 Office 365 全局管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="165a7-112">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="165a7-113">或者, 也可以直接在 cmdlet 中输入您的凭据。</span><span class="sxs-lookup"><span data-stu-id="165a7-113">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="165a7-114">运行以下 cmdlet, 将您的公司管理员凭据指定为 PSCredential 对象。</span><span class="sxs-lookup"><span data-stu-id="165a7-114">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="165a7-115">有关使用 PowerShell 的详细信息, 请参阅[连接到 Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)。</span><span class="sxs-lookup"><span data-stu-id="165a7-115">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="165a7-116">上载外接程序清单</span><span class="sxs-lookup"><span data-stu-id="165a7-116">Upload an add-in manifest</span></span>

<span data-ttu-id="165a7-117">运行 Organizationadd-in cmdlet 以从路径 (可以是文件位置或 URL) 上传外接程序清单。</span><span class="sxs-lookup"><span data-stu-id="165a7-117">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="165a7-118">下面的示例演示_ManifestPath_参数值的文件位置。</span><span class="sxs-lookup"><span data-stu-id="165a7-118">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="165a7-119">您还可以运行 Organizationadd-in cmdlet 以上载外接程序, 并使用_Members_参数直接将其分配给用户或组, 如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="165a7-119">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="165a7-120">使用逗号分隔成员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="165a7-120">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="165a7-121">从 Office 应用商店上载外接程序</span><span class="sxs-lookup"><span data-stu-id="165a7-121">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="165a7-122">运行 OrganizationAddIn cmdlet, 从 Office 应用商店上传清单。</span><span class="sxs-lookup"><span data-stu-id="165a7-122">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="165a7-123">在以下示例中, OrganizationAddIn cmdlet 为美国位置和内容市场的外接程序指定 AssetId。</span><span class="sxs-lookup"><span data-stu-id="165a7-123">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="165a7-124">若要确定_AssetId_参数的值, 可以从外接程序的 Office 应用商店网页的 URL 复制它。</span><span class="sxs-lookup"><span data-stu-id="165a7-124">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="165a7-125">AssetIds 始终以 "WA" 开头, 后跟一个数字。</span><span class="sxs-lookup"><span data-stu-id="165a7-125">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="165a7-126">例如, 在上一示例中, WA104099688 的 AssetId 值的源是外接程序的 Office 应用商店网页 URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。</span><span class="sxs-lookup"><span data-stu-id="165a7-126">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="165a7-127">_Locale_参数和_ContentMarket_参数的值是相同的, 并指示您要从中安装外接程序的国家/地区。</span><span class="sxs-lookup"><span data-stu-id="165a7-127">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="165a7-128">格式为 en-us, fr-fr。</span><span class="sxs-lookup"><span data-stu-id="165a7-128">The format is en-US, fr-FR.</span></span> <span data-ttu-id="165a7-129">等。</span><span class="sxs-lookup"><span data-stu-id="165a7-129">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="165a7-130">从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。</span><span class="sxs-lookup"><span data-stu-id="165a7-130">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="165a7-131">获取外接程序的详细信息</span><span class="sxs-lookup"><span data-stu-id="165a7-131">Get details of an add-in</span></span>

<span data-ttu-id="165a7-132">运行以下所示的 OrganizationAddIn cmdlet, 以获取上载到租户的所有加载项的详细信息, 包括加载项的产品 ID。</span><span class="sxs-lookup"><span data-stu-id="165a7-132">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="165a7-133">运行 OrganizationAddIn cmdlet 和_ProductId_参数的值, 以指定要检索其详细信息的外接程序。</span><span class="sxs-lookup"><span data-stu-id="165a7-133">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="165a7-134">若要获取所有外接程序的完整详细信息以及分配的用户和组, 请将 OrganizationAddIn cmdlet 的输出通过管道传递给格式列表 cmdlet, 如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="165a7-134">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="165a7-135">打开或关闭外接程序</span><span class="sxs-lookup"><span data-stu-id="165a7-135">Turn on or turn off an add-in</span></span>

<span data-ttu-id="165a7-136">若要关闭外接程序, 以便向其分配了的用户和组将不再具有访问权限, 请运行带有_ProductId_参数的 OrganizationAddIn cmdlet, 并将_Enabled_参数设置为`$false`, 如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="165a7-136">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="165a7-137">若要重新打开外接程序, 请运行相同的 cmdlet, 并将_Enabled_参数设置`$true`为。</span><span class="sxs-lookup"><span data-stu-id="165a7-137">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="165a7-138">在外接程序中添加或删除用户</span><span class="sxs-lookup"><span data-stu-id="165a7-138">Add or remove users from an add-in</span></span>

<span data-ttu-id="165a7-139">若要将用户和组添加到特定加载项, 请运行 OrganizationAddInAssignments cmdlet 和_ProductId_、 _add_和_Members_参数。</span><span class="sxs-lookup"><span data-stu-id="165a7-139">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="165a7-140">使用逗号分隔成员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="165a7-140">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="165a7-141">若要删除用户和组, 请使用_remove_参数运行相同的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="165a7-141">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="165a7-142">若要将外接程序分配给租户上的所有用户, 请使用_AssignToEveryone_参数 (其值设置为`$true`) 运行相同的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="165a7-142">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="165a7-143">若要不向每个人分配外接程序并将其还原到以前分配的用户和组, 您可以运行同一 cmdlet, 并通过将_AssignToEveryone_参数的值设置`$false`为来关闭该参数。</span><span class="sxs-lookup"><span data-stu-id="165a7-143">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="165a7-144">更新外接程序</span><span class="sxs-lookup"><span data-stu-id="165a7-144">Update an add-in</span></span>

<span data-ttu-id="165a7-145">若要从清单更新外接程序, 请运行 OrganizationAddIn cmdlet 和_ProductId_、 _ManifestPath_和_Locale_参数, 如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="165a7-145">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="165a7-146">从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。</span><span class="sxs-lookup"><span data-stu-id="165a7-146">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="165a7-147">删除外接程序</span><span class="sxs-lookup"><span data-stu-id="165a7-147">Delete an add-in</span></span>

<span data-ttu-id="165a7-148">若要删除外接程序, 请运行带有_ProductId_参数的 OrganizationAddIn cmdlet, 如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="165a7-148">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="165a7-149">获取每个 cmdlet 的详细帮助</span><span class="sxs-lookup"><span data-stu-id="165a7-149">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="165a7-150">您可以使用 Get-help cmdlet 查看每个 cmdlet 的详细帮助信息。</span><span class="sxs-lookup"><span data-stu-id="165a7-150">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="165a7-151">例如, 以下 cmdlet 提供有关 OrganizationAddIn cmdlet 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="165a7-151">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


