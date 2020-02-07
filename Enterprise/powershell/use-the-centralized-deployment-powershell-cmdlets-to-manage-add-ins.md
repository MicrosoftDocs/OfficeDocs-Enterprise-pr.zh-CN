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
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="d58eb-103">使用集中部署 PowerShell cmdlet 管理外接程序</span><span class="sxs-lookup"><span data-stu-id="d58eb-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="d58eb-104">作为 Office 365 管理员，您可以通过集中部署功能向用户部署 Office 外接程序（请参阅[在管理中心中管理 Office 365 外接程序的部署](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)）。</span><span class="sxs-lookup"><span data-stu-id="d58eb-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="d58eb-105">除了通过管理中心部署 Office 加载项外，还可以使用 Microsoft PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d58eb-105">In addition to deploying Office add-ins via the admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="d58eb-106">从 Microsoft 下载中心[下载](https://go.microsoft.com/fwlink/p/?linkid=850850)集中部署 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d58eb-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="d58eb-107">要执行什么操作？</span><span class="sxs-lookup"><span data-stu-id="d58eb-107">What do you want to do?</span></span>

[<span data-ttu-id="d58eb-108">使用管理员凭据连接</span><span class="sxs-lookup"><span data-stu-id="d58eb-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="d58eb-109">上载外接程序清单</span><span class="sxs-lookup"><span data-stu-id="d58eb-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="d58eb-110">从 Office 应用商店上载外接程序</span><span class="sxs-lookup"><span data-stu-id="d58eb-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="d58eb-111">获取外接程序的详细信息</span><span class="sxs-lookup"><span data-stu-id="d58eb-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="d58eb-112">打开或关闭外接程序</span><span class="sxs-lookup"><span data-stu-id="d58eb-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="d58eb-113">在外接程序中添加或删除用户</span><span class="sxs-lookup"><span data-stu-id="d58eb-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="d58eb-114">更新外接程序</span><span class="sxs-lookup"><span data-stu-id="d58eb-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="d58eb-115">删除外接程序</span><span class="sxs-lookup"><span data-stu-id="d58eb-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="d58eb-116">获取每个 cmdlet 的详细帮助</span><span class="sxs-lookup"><span data-stu-id="d58eb-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="d58eb-117">使用管理员凭据连接</span><span class="sxs-lookup"><span data-stu-id="d58eb-117">Connect using your admin credentials</span></span>
<span data-ttu-id="d58eb-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="d58eb-118"><a name="BKMK_Connect"> </a></span></span>

<span data-ttu-id="d58eb-119">必须先登录，然后才能使用集中部署 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d58eb-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="d58eb-120">启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d58eb-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="d58eb-121">使用您的公司管理员凭据连接到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d58eb-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="d58eb-122">运行以下 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d58eb-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="d58eb-123">在 "**输入凭据**" 页面中，输入 Office 365 全局管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="d58eb-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="d58eb-124">或者，也可以直接在 cmdlet 中输入您的凭据。</span><span class="sxs-lookup"><span data-stu-id="d58eb-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="d58eb-125">运行以下 cmdlet，将您的公司管理员凭据指定为 PSCredential 对象。</span><span class="sxs-lookup"><span data-stu-id="d58eb-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="d58eb-126">有关使用 PowerShell 的详细信息，请参阅[连接到 Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)。</span><span class="sxs-lookup"><span data-stu-id="d58eb-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="d58eb-127">上载外接程序清单</span><span class="sxs-lookup"><span data-stu-id="d58eb-127">Upload an add-in manifest</span></span>
<span data-ttu-id="d58eb-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="d58eb-128"><a name="BKMK_UploadManifest"> </a></span></span>

<span data-ttu-id="d58eb-129">运行 Organizationadd-in cmdlet 以从路径（可以是文件位置或 URL）上传外接程序清单。</span><span class="sxs-lookup"><span data-stu-id="d58eb-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="d58eb-130">下面的示例演示_ManifestPath_参数值的文件位置。</span><span class="sxs-lookup"><span data-stu-id="d58eb-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="d58eb-131">您还可以运行 Organizationadd-in cmdlet 以上载外接程序，并使用_Members_参数直接将其分配给用户或组，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d58eb-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="d58eb-132">使用逗号分隔成员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="d58eb-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="d58eb-133">从 Office 应用商店上载外接程序</span><span class="sxs-lookup"><span data-stu-id="d58eb-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="d58eb-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="d58eb-134"><a name="BKMK_UploadAddin"> </a></span></span>

<span data-ttu-id="d58eb-135">运行 OrganizationAddIn cmdlet，从 Office 应用商店上传清单。</span><span class="sxs-lookup"><span data-stu-id="d58eb-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="d58eb-136">在以下示例中，OrganizationAddIn cmdlet 为美国位置和内容市场的外接程序指定 AssetId。</span><span class="sxs-lookup"><span data-stu-id="d58eb-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="d58eb-137">若要确定_AssetId_参数的值，可以从外接程序的 Office 应用商店网页的 URL 复制它。</span><span class="sxs-lookup"><span data-stu-id="d58eb-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="d58eb-138">AssetIds 始终以 "WA" 开头，后跟一个数字。</span><span class="sxs-lookup"><span data-stu-id="d58eb-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="d58eb-139">例如，在上一示例中，WA104099688 的 AssetId 值的源是外接程序的 Office 应用商店网页 URL： [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。</span><span class="sxs-lookup"><span data-stu-id="d58eb-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="d58eb-140">_Locale_参数和_ContentMarket_参数的值是相同的，并指示您要从中安装外接程序的国家/地区。</span><span class="sxs-lookup"><span data-stu-id="d58eb-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="d58eb-141">格式为 en-us，fr-fr。</span><span class="sxs-lookup"><span data-stu-id="d58eb-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="d58eb-142">等。</span><span class="sxs-lookup"><span data-stu-id="d58eb-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="d58eb-143">从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。</span><span class="sxs-lookup"><span data-stu-id="d58eb-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="d58eb-144">获取外接程序的详细信息</span><span class="sxs-lookup"><span data-stu-id="d58eb-144">Get details of an add-in</span></span>
<span data-ttu-id="d58eb-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="d58eb-145"><a name="BKMK_GetDetails"> </a></span></span>

<span data-ttu-id="d58eb-146">运行以下所示的 OrganizationAddIn cmdlet，以获取上载到租户的所有加载项的详细信息，包括加载项的产品 ID。</span><span class="sxs-lookup"><span data-stu-id="d58eb-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="d58eb-147">运行 OrganizationAddIn cmdlet 和_ProductId_参数的值，以指定要检索其详细信息的外接程序。</span><span class="sxs-lookup"><span data-stu-id="d58eb-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="d58eb-148">若要获取所有外接程序的完整详细信息以及分配的用户和组，请将 OrganizationAddIn cmdlet 的输出通过管道传递给格式列表 cmdlet，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d58eb-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="d58eb-149">打开或关闭外接程序</span><span class="sxs-lookup"><span data-stu-id="d58eb-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="d58eb-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="d58eb-150"><a name="BKMK_TurnOnOff"> </a></span></span>

<span data-ttu-id="d58eb-151">若要关闭外接程序，以便向其分配了的用户和组将不再具有访问权限，请运行带有_ProductId_参数的 OrganizationAddIn cmdlet，并将_Enabled_参数设置为`$false`，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d58eb-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="d58eb-152">若要重新打开外接程序，请运行相同的 cmdlet，并将_Enabled_参数设置`$true`为。</span><span class="sxs-lookup"><span data-stu-id="d58eb-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="d58eb-153">在外接程序中添加或删除用户</span><span class="sxs-lookup"><span data-stu-id="d58eb-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="d58eb-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="d58eb-154"><a name="BKMK_AddRemove"> </a></span></span>

<span data-ttu-id="d58eb-155">若要将用户和组添加到特定加载项，请运行 OrganizationAddInAssignments cmdlet 和_ProductId_、 _add_和_Members_参数。</span><span class="sxs-lookup"><span data-stu-id="d58eb-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="d58eb-156">使用逗号分隔成员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="d58eb-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="d58eb-157">若要删除用户和组，请使用_remove_参数运行相同的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d58eb-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="d58eb-158">若要将外接程序分配给租户上的所有用户，请使用_AssignToEveryone_参数（其值设置为`$true`）运行相同的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d58eb-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="d58eb-159">若要不向每个人分配外接程序并将其还原到以前分配的用户和组，您可以运行同一 cmdlet，并通过将_AssignToEveryone_参数的值设置`$false`为来关闭该参数。</span><span class="sxs-lookup"><span data-stu-id="d58eb-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="d58eb-160">更新外接程序</span><span class="sxs-lookup"><span data-stu-id="d58eb-160">Update an add-in</span></span>
<span data-ttu-id="d58eb-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="d58eb-161"><a name="BKMK_UpdateAddin"> </a></span></span>

<span data-ttu-id="d58eb-162">若要从清单更新外接程序，请运行 OrganizationAddIn cmdlet 和_ProductId_、 _ManifestPath_和_Locale_参数，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="d58eb-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="d58eb-163">从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。</span><span class="sxs-lookup"><span data-stu-id="d58eb-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="d58eb-164">删除外接程序</span><span class="sxs-lookup"><span data-stu-id="d58eb-164">Delete an add-in</span></span>
<span data-ttu-id="d58eb-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="d58eb-165"><a name="BKMK_Delete"> </a></span></span>

<span data-ttu-id="d58eb-166">若要删除外接程序，请运行带有_ProductId_参数的 OrganizationAddIn cmdlet，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="d58eb-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="d58eb-167">获取每个 cmdlet 的详细帮助</span><span class="sxs-lookup"><span data-stu-id="d58eb-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="d58eb-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="d58eb-168"><a name="BKMK_GetHelp"> </a></span></span>

<span data-ttu-id="d58eb-169">您可以使用 Get-help cmdlet 查看每个 cmdlet 的详细帮助信息。</span><span class="sxs-lookup"><span data-stu-id="d58eb-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="d58eb-170">例如，以下 cmdlet 提供有关 OrganizationAddIn cmdlet 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d58eb-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


