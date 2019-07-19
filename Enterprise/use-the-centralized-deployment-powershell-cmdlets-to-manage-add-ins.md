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
ms.openlocfilehash: c63a48d212bba4eda25fb6b8843f6321892dc54b
ms.sourcegitcommit: d53033c2d2d41d52047e3e2644d77373d4a5dd9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2019
ms.locfileid: "35791247"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="fe6e9-103">使用集中部署 PowerShell cmdlet 管理外接程序</span><span class="sxs-lookup"><span data-stu-id="fe6e9-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="fe6e9-104">作为 Microsoft 365 全局或 Exchange 管理员, 您可以通过集中部署功能向用户部署 Office 外接程序 (请参阅[在管理中心部署 Office 加载项](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx))。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-104">As a Microsoft 365 global, or Exchange admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="fe6e9-105">除了通过 Microsoft 365 管理中心部署 Office 外接程序之外, 你还可以使用 Microsoft PowerShell。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-105">In addition to deploying Office add-ins via the Microsoft 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="fe6e9-106">安装[适用于 Windows PowerShell 的 O365 集中外接程序部署模块](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 

<span data-ttu-id="fe6e9-107">下载模块后, 打开一个常规的 Windows PowerShell 窗口并运行以下 cmdlet:</span><span class="sxs-lookup"><span data-stu-id="fe6e9-107">After you download the module, open a regular Windows PowerShell window and run the following cmdlet:</span></span>

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="fe6e9-108">使用管理员凭据连接</span><span class="sxs-lookup"><span data-stu-id="fe6e9-108">Connect using your admin credentials</span></span>

<span data-ttu-id="fe6e9-109">必须先登录, 然后才能使用集中部署 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-109">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="fe6e9-110">启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-110">Start PowerShell.</span></span>
    
2. <span data-ttu-id="fe6e9-111">使用您的公司管理员凭据连接到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-111">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="fe6e9-112">运行以下 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-112">Run the following cmdlet.</span></span>
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="fe6e9-113">在 "**输入凭据**" 页面中, 输入 Office 365 全局管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-113">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="fe6e9-114">或者, 也可以直接在 cmdlet 中输入您的凭据。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-114">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="fe6e9-115">运行以下 cmdlet, 将您的公司管理员凭据指定为 PSCredential 对象。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-115">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="fe6e9-116">有关使用 PowerShell 的详细信息, 请参阅[连接到 Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-116">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="fe6e9-117">上载外接程序清单</span><span class="sxs-lookup"><span data-stu-id="fe6e9-117">Upload an add-in manifest</span></span>

<span data-ttu-id="fe6e9-118">运行**organizationadd-in** cmdlet 以从路径 (可以是文件位置或 URL) 上传外接程序清单。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-118">Run the **New-OrganizationAdd-In** cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="fe6e9-119">下面的示例演示_ManifestPath_参数值的文件位置。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-119">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="fe6e9-120">您还可以运行**organizationadd-in** cmdlet 以上载外接程序, 并使用_Members_参数直接将其分配给用户或组, 如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-120">You can also run the **New-OrganizationAdd-In** cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="fe6e9-121">使用逗号分隔成员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-121">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="fe6e9-122">从 Office 应用商店上载外接程序</span><span class="sxs-lookup"><span data-stu-id="fe6e9-122">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="fe6e9-123">运行**OrganizationAddIn** cmdlet, 从 Office 应用商店上传清单。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-123">Run the **New-OrganizationAddIn** cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="fe6e9-124">在以下示例中, **OrganizationAddIn** Cmdlet 为美国位置和内容市场的外接程序指定 AssetId。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-124">In the following example, the **New-OrganizationAddIn** cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="fe6e9-125">若要确定_AssetId_参数的值, 可以从外接程序的 Office 应用商店网页的 URL 复制它。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-125">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="fe6e9-126">AssetIds 始终以 "WA" 开头, 后跟一个数字。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-126">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="fe6e9-127">例如, 在上一示例中, WA104099688 的 AssetId 值的源是外接程序的 Office 应用商店网页 URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-127">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="fe6e9-128">_Locale_参数和_ContentMarket_参数的值是相同的, 并指示您要从中安装外接程序的国家/地区。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-128">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="fe6e9-129">格式为 en-us, fr-fr。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-129">The format is en-US, fr-FR.</span></span> <span data-ttu-id="fe6e9-130">等。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-130">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="fe6e9-131">从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-131">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="fe6e9-132">获取外接程序的详细信息</span><span class="sxs-lookup"><span data-stu-id="fe6e9-132">Get details of an add-in</span></span>

<span data-ttu-id="fe6e9-133">运行以下所示的**OrganizationAddIn** cmdlet, 以获取上载到租户的所有加载项的详细信息, 包括加载项的产品 ID。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-133">Run the **Get-OrganizationAddIn** cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```powershell
Get-OrganizationAddIn
```

<span data-ttu-id="fe6e9-134">运行**OrganizationAddIn** Cmdlet 和_ProductId_参数的值, 以指定要检索其详细信息的外接程序。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-134">Run the **Get-OrganizationAddIn** cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="fe6e9-135">若要获取所有外接程序的完整详细信息以及分配的用户和组, 请将**OrganizationAddIn** cmdlet 的输出通过管道传递给格式列表 cmdlet, 如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-135">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the **Get-OrganizationAddIn** cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="fe6e9-136">打开或关闭外接程序</span><span class="sxs-lookup"><span data-stu-id="fe6e9-136">Turn on or turn off an add-in</span></span>

<span data-ttu-id="fe6e9-137">若要关闭外接程序, 以便向其分配了的用户和组将不再具有访问权限, 请运行带有_ProductId_参数的**OrganizationAddIn** Cmdlet, 并将_Enabled_参数设置为`$false`, 如以下示例所示.</span><span class="sxs-lookup"><span data-stu-id="fe6e9-137">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="fe6e9-138">若要重新打开外接程序, 请运行相同的 cmdlet, 并将_Enabled_参数设置`$true`为。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-138">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="fe6e9-139">在外接程序中添加或删除用户</span><span class="sxs-lookup"><span data-stu-id="fe6e9-139">Add or remove users from an add-in</span></span>

<span data-ttu-id="fe6e9-140">若要将用户和组添加到特定加载项, 请运行**OrganizationAddInAssignments** Cmdlet 和_ProductId_、 _add_和_Members_参数。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-140">To add users and groups to a specific add-in, run the **Set-OrganizationAddInAssignments** cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="fe6e9-141">使用逗号分隔成员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-141">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="fe6e9-142">若要删除用户和组, 请使用_remove_参数运行相同的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-142">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="fe6e9-143">若要将外接程序分配给租户上的所有用户, 请使用_AssignToEveryone_参数 (其值设置为`$true`) 运行相同的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-143">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="fe6e9-144">若要不向每个人分配外接程序并将其还原到以前分配的用户和组, 您可以运行同一 cmdlet, 并通过将_AssignToEveryone_参数的值设置`$false`为来关闭该参数。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-144">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="fe6e9-145">更新外接程序</span><span class="sxs-lookup"><span data-stu-id="fe6e9-145">Update an add-in</span></span>

<span data-ttu-id="fe6e9-146">若要从清单更新外接程序, 请运行**OrganizationAddIn** Cmdlet 和_ProductId_、 _ManifestPath_和_Locale_参数, 如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-146">To update an add-in from a manifest, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="fe6e9-147">从 Office 应用商店上传的外接程序将在 Office 应用商店上的最新更新更新几天内自动更新。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-147">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="fe6e9-148">删除外接程序</span><span class="sxs-lookup"><span data-stu-id="fe6e9-148">Delete an add-in</span></span>

<span data-ttu-id="fe6e9-149">若要删除外接程序, 请运行带有_ProductId_参数的**OrganizationAddIn** cmdlet, 如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-149">To delete an add-in, run the **Remove-OrganizationAddIn** cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a><span data-ttu-id="fe6e9-150">为你的组织自定义 Microsoft Store 外接程序</span><span class="sxs-lookup"><span data-stu-id="fe6e9-150">Customize Microsoft Store add-ins for your organization</span></span>

<span data-ttu-id="fe6e9-151">必须先自定义外接程序, 然后才能将其部署到组织中。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-151">You must customize the add-in before you deploy it to your organization.</span></span> <span data-ttu-id="fe6e9-152">此功能不支持早于版本1.1 的外接程序。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-152">Add-ins older than version 1.1 are not supported by this feature.</span></span> 

<span data-ttu-id="fe6e9-153">另请注意以下限制:</span><span class="sxs-lookup"><span data-stu-id="fe6e9-153">Note also the following restrictions:</span></span>
- <span data-ttu-id="fe6e9-154">所有 Url 都必须是绝对 Url (包括 http 或 https) 且有效。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-154">All URLs must be absolute (include http or https) and valid.</span></span>
- <span data-ttu-id="fe6e9-155">*DisplayName*不得超过125个字符</span><span class="sxs-lookup"><span data-stu-id="fe6e9-155">*DisplayName* must not exceed 125 characters</span></span> 
- <span data-ttu-id="fe6e9-156">*DisplayName*、*资源*和*appdomain*不能包含以下字符:</span><span class="sxs-lookup"><span data-stu-id="fe6e9-156">*DisplayName*, *Resources* and *AppDomains* must not include the following characters:</span></span> 
 
    - \<
    -  \>
    -  <span data-ttu-id="fe6e9-157">;</span><span class="sxs-lookup"><span data-stu-id="fe6e9-157"></span></span>
    -  =   

<span data-ttu-id="fe6e9-158">如果要自定义已部署的加载项, 则必须将其卸载到管理中心, 并查看 "[从本地缓存中删除加载项](#remove-an-add-in-from-local-cache)", 以了解将其从已部署到的每台计算机中删除的步骤。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-158">If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.</span></span>

<span data-ttu-id="fe6e9-159">若要自定义外接程序, 请运行**OrganizationAddInOverrides** Cmdlet 和*ProductId*作为参数, 后跟要覆盖的标记和新值。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-159">To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value.</span></span> <span data-ttu-id="fe6e9-160">若要了解如何获取*产品 id* , 请参阅本文中的获取外接程序的[详细信息](#get-details-of-an-add-in)。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-160">To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article.</span></span> <span data-ttu-id="fe6e9-161">例如：</span><span class="sxs-lookup"><span data-stu-id="fe6e9-161">For example:</span></span>

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
<span data-ttu-id="fe6e9-162">若要自定义外接程序的多个标记, 请将这些标记添加到命令行中:</span><span class="sxs-lookup"><span data-stu-id="fe6e9-162">To customize multiple tags for an add-in, add those tags to the commandline:</span></span>

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> <span data-ttu-id="fe6e9-163">您必须将多个自定义标记作为一个命令应用于一个加载项。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-163">You must apply multiple customized tags to one add-in as one command.</span></span> <span data-ttu-id="fe6e9-164">如果逐个自定义标记, 则只会应用最后一个自定义项。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-164">If you customize tags one by one, only the last customization will be applied.</span></span> <span data-ttu-id="fe6e9-165">此外, 如果错误地自定义标记, 则必须删除所有自定义项并重新开始。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-165">Additionally, if you customize a tag by mistake, you must remove all customizations and start over.</span></span>

### <a name="tags-you-can-customize"></a><span data-ttu-id="fe6e9-166">您可以自定义的标记</span><span class="sxs-lookup"><span data-stu-id="fe6e9-166">Tags you can customize</span></span>

| <span data-ttu-id="fe6e9-167">Tag</span><span class="sxs-lookup"><span data-stu-id="fe6e9-167">Tag</span></span>                  | <span data-ttu-id="fe6e9-168">说明</span><span class="sxs-lookup"><span data-stu-id="fe6e9-168">Description</span></span>          |
| :------------------- | :------------------- |
| <span data-ttu-id="fe6e9-169">\<IconURL></span><span class="sxs-lookup"><span data-stu-id="fe6e9-169">\<IconURL></span></span>   </br>| <span data-ttu-id="fe6e9-170">用作加载项图标的图像的 URL (在管理中心中)。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-170">The URL of the image used as the add-in’s icon (in admin center).</span></span> </br> |
| <span data-ttu-id="fe6e9-171">\<DisplayName></span><span class="sxs-lookup"><span data-stu-id="fe6e9-171">\<DisplayName></span></span>| <span data-ttu-id="fe6e9-172">加载项的标题 (在管理中心中)。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-172">The title of the add-in  (in admin center).</span></span>|
| <span data-ttu-id="fe6e9-173">\<主机></span><span class="sxs-lookup"><span data-stu-id="fe6e9-173">\<Hosts></span></span>| <span data-ttu-id="fe6e9-174">将支持外接程序的应用程序的列表。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-174">List of apps that will support the add-in.</span></span>|
| <span data-ttu-id="fe6e9-175">\<SourceLocation></span><span class="sxs-lookup"><span data-stu-id="fe6e9-175">\<SourceLocation></span></span> | <span data-ttu-id="fe6e9-176">外接程序将连接到的源 URL。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-176">The source URL that the add-in will connect to.</span></span>| 
| <span data-ttu-id="fe6e9-177">\<Appdomain></span><span class="sxs-lookup"><span data-stu-id="fe6e9-177">\<AppDomains></span></span> | <span data-ttu-id="fe6e9-178">外接程序可与之连接的域的列表。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-178">A list of domains that the add-in can connect with.</span></span> | 
| <span data-ttu-id="fe6e9-179">\<SupportURL></span><span class="sxs-lookup"><span data-stu-id="fe6e9-179">\<SupportURL></span></span>| <span data-ttu-id="fe6e9-180">用户可用于访问帮助和支持的 URL。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-180">The URL users can use to access help and support.</span></span> | 
| <span data-ttu-id="fe6e9-181">\<资源></span><span class="sxs-lookup"><span data-stu-id="fe6e9-181">\<Resources></span></span>  | <span data-ttu-id="fe6e9-182">此标记包含多个元素, 包括标题、工具提示和不同大小的图标。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-182">This tag contains a number of elements including titles, tooltips, and icons of different sizes.</span></span>| 
|
### <a name="customize-resources-tag"></a><span data-ttu-id="fe6e9-183">自定义 Resources 标记</span><span class="sxs-lookup"><span data-stu-id="fe6e9-183">Customize Resources tag</span></span>

<span data-ttu-id="fe6e9-184">可以动态自定义<Resources>清单标记中的任何元素。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-184">Any element in the <Resources> tag of the manifest can be customized dynamically.</span></span> <span data-ttu-id="fe6e9-185">首先需要检查清单以查找要向其分配新值的元素 id。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-185">You first need to check the manifest to find the element id to which you want to assign a new value.</span></span> <span data-ttu-id="fe6e9-186"><Resources>标记如下所示:</span><span class="sxs-lookup"><span data-stu-id="fe6e9-186">The <Resources> tag looks like this:</span></span>

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
<span data-ttu-id="fe6e9-187">在这种情况下, 图像的元素 id 为 "img16icon", 与关联的值为 "http:<i></i>//site。<i> </i>com/img. "</span><span class="sxs-lookup"><span data-stu-id="fe6e9-187">In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”</span></span>

<span data-ttu-id="fe6e9-188">确定要自定义的元素后, 请在 Powershell 中使用以下命令将新值分配给这些元素:</span><span class="sxs-lookup"><span data-stu-id="fe6e9-188">Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:</span></span>

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

<span data-ttu-id="fe6e9-189">您可以根据需要自定义多个元素和命令。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-189">You can customize as many elements with the command as you need to.</span></span>

### <a name="remove-customization-from-an-add-in"></a><span data-ttu-id="fe6e9-190">从外接程序中删除自定义项</span><span class="sxs-lookup"><span data-stu-id="fe6e9-190">Remove customization from an add-in</span></span>

<span data-ttu-id="fe6e9-191">当前可用于删除自定义项的唯一选项是一次性删除所有自定义项:</span><span class="sxs-lookup"><span data-stu-id="fe6e9-191">The only option currently available for deleting customizations is to delete all of them at once:</span></span>

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a><span data-ttu-id="fe6e9-192">查看加载项自定义项</span><span class="sxs-lookup"><span data-stu-id="fe6e9-192">View add-in customizations</span></span>

<span data-ttu-id="fe6e9-193">若要查看已应用的自定义项列表, 请运行**OrganizationAddInOverrides** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-193">To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet.</span></span> <span data-ttu-id="fe6e9-194">如果在没有*ProductId*的情况下运行**OrganizationAddInOverrides** , 则将返回所有应用了替代的外接程序的列表。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-194">If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.</span></span>  

```powershell
Get-OrganizationAddInOverrides 
```
<span data-ttu-id="fe6e9-195">如果指定了 ProductId, 则将返回应用于该外接程序的替代项列表。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-195">If ProductId is specified, then a list of overrides applied to that add-in is returned.</span></span> 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a><span data-ttu-id="fe6e9-196">从本地缓存中删除外接程序</span><span class="sxs-lookup"><span data-stu-id="fe6e9-196">Remove an add-in from local cache</span></span>

<span data-ttu-id="fe6e9-197">如果已部署加载项, 则必须先将其从每台计算机的缓存中删除, 然后才能对其进行自定义。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-197">If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized.</span></span> <span data-ttu-id="fe6e9-198">从缓存中 remive 外接程序:</span><span class="sxs-lookup"><span data-stu-id="fe6e9-198">To remive an add-in from cache:</span></span>

1. <span data-ttu-id="fe6e9-199">导航到 C:\ 中的 "Users" 文件夹</span><span class="sxs-lookup"><span data-stu-id="fe6e9-199">Navigate to the “Users” folder in C:\</span></span> 
1. <span data-ttu-id="fe6e9-200">转到您的用户文件夹</span><span class="sxs-lookup"><span data-stu-id="fe6e9-200">Go to your user folder</span></span>
1. <span data-ttu-id="fe6e9-201">导航到 "AppData\Local\Microsoft\Office", 然后选择与您的 Office 版本相关联的文件夹</span><span class="sxs-lookup"><span data-stu-id="fe6e9-201">Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office</span></span>
1. <span data-ttu-id="fe6e9-202">在 " *Wef* " 文件夹中, 删除 "*清单*" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-202">In the *Wef* folder delete the *Manifests* folder.</span></span>

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="fe6e9-203">获取每个 cmdlet 的详细帮助</span><span class="sxs-lookup"><span data-stu-id="fe6e9-203">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="fe6e9-204">您可以使用 Get-help cmdlet 查看每个 cmdlet 的详细帮助信息。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-204">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="fe6e9-205">例如, 以下 cmdlet 提供有关 OrganizationAddIn cmdlet 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="fe6e9-205">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


