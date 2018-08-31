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
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="52fc2-103">使用集中部署 PowerShell cmdlet 管理加载项</span><span class="sxs-lookup"><span data-stu-id="52fc2-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="52fc2-p101">为 Office 365 管理员，可向通过集中部署的用户部署 Office 加载项功能 （请参阅[管理 Office 365 中的加载项在 Office 365 管理中心的部署](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)）。除了部署 Office 加载项通过 Office 365 管理中心，您还可以使用 Microsoft PowerShell。[下载](https://go.microsoft.com/fwlink/p/?linkid=850850)从 Microsoft 下载中心下载的集中部署 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="52fc2-p101">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the Office 365 admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell. [Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="52fc2-107">要执行什么操作？</span><span class="sxs-lookup"><span data-stu-id="52fc2-107">What do you want to do?</span></span>

[<span data-ttu-id="52fc2-108">使用管理员凭据连接</span><span class="sxs-lookup"><span data-stu-id="52fc2-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="52fc2-109">上载的外接程序清单</span><span class="sxs-lookup"><span data-stu-id="52fc2-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="52fc2-110">上载外接程序从 Office 商店</span><span class="sxs-lookup"><span data-stu-id="52fc2-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="52fc2-111">获取外接程序的详细信息</span><span class="sxs-lookup"><span data-stu-id="52fc2-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="52fc2-112">打开或关闭外接程序</span><span class="sxs-lookup"><span data-stu-id="52fc2-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="52fc2-113">添加或删除的用户外接程序</span><span class="sxs-lookup"><span data-stu-id="52fc2-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="52fc2-114">外接程序更新</span><span class="sxs-lookup"><span data-stu-id="52fc2-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="52fc2-115">删除外接程序</span><span class="sxs-lookup"><span data-stu-id="52fc2-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="52fc2-116">每个 cmdlet 获得详细的帮助</span><span class="sxs-lookup"><span data-stu-id="52fc2-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="52fc2-117">使用管理员凭据连接</span><span class="sxs-lookup"><span data-stu-id="52fc2-117">Connect using your admin credentials</span></span>
<span data-ttu-id="52fc2-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="52fc2-118"></span></span>

<span data-ttu-id="52fc2-119">您可以使用集中部署 cmdlet 之前，您需要登录。</span><span class="sxs-lookup"><span data-stu-id="52fc2-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="52fc2-120">启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="52fc2-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="52fc2-p102">使用您的公司管理员凭据连接到 PowerShell。运行以下 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="52fc2-p102">Connect to PowerShell by using your company admin credentials. Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="52fc2-p103">在**输入凭据**页上，输入您的 Office 365 全局管理员凭据。另外，您可以直接在 cmdlet 输入您的凭据。</span><span class="sxs-lookup"><span data-stu-id="52fc2-p103">In the **Enter Credentials** page, enter your Office 365 global admin credentials. Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="52fc2-125">运行以下 cmdlet 指定您的公司管理员凭据作为 PSCredential 对象。</span><span class="sxs-lookup"><span data-stu-id="52fc2-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="52fc2-126">有关使用 PowerShell 的详细信息，请参阅[Connect to Office 365 PowerShell 中](https://go.microsoft.com/fwlink/p/?linkid=848585)。</span><span class="sxs-lookup"><span data-stu-id="52fc2-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="52fc2-127">上载的外接程序清单</span><span class="sxs-lookup"><span data-stu-id="52fc2-127">Upload an add-in manifest</span></span>
<span data-ttu-id="52fc2-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="52fc2-128"></span></span>

<span data-ttu-id="52fc2-p104">运行新建入式 OrganizationAdd cmdlet 来上载外接程序将清单从路径，它可以是一个文件位置或 URL。下面的示例演示_ManifestPath_参数的值的文件位置。</span><span class="sxs-lookup"><span data-stu-id="52fc2-p104">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL. The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="52fc2-p105">您还可以运行新建入式 OrganizationAdd cmdlet 来上载外接程序，并将其分配给用户或组直接使用_Members_参数，如下面的示例中所示。用逗号分隔成员的电子邮件的地址。</span><span class="sxs-lookup"><span data-stu-id="52fc2-p105">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example. Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="52fc2-133">上载外接程序从 Office 商店</span><span class="sxs-lookup"><span data-stu-id="52fc2-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="52fc2-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="52fc2-134"></span></span>

<span data-ttu-id="52fc2-135">运行新建 OrganizationAddIn cmdlet 来上载来自 Office 商店的清单。</span><span class="sxs-lookup"><span data-stu-id="52fc2-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="52fc2-136">在以下示例中，新建 OrganizationAddIn cmdlet 指定 AssetId 美国位置和内容市场的加载项。</span><span class="sxs-lookup"><span data-stu-id="52fc2-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="52fc2-p106">若要确定_AssetId_参数的值，可以将其复制从 Office 商店网页加载 AssetIds 始终开始使用"WA"跟一个数字的 URL。例如，在上一示例中，WA104099688 AssetId 值的源是加载项的 Office 应用商店网页 URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。</span><span class="sxs-lookup"><span data-stu-id="52fc2-p106">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in. AssetIds always begin with "WA" followed by a number. For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="52fc2-p107">_Locale_参数和_ContentMarket_参数的值相同，并指明您尝试安装外接程序从国家/地区。格式为 EN-US、 fr 法属等。</span><span class="sxs-lookup"><span data-stu-id="52fc2-p107">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from. The format is en-US, fr-FR. and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="52fc2-143">在 Office 商店正在可用的最新更新的几天内，从 Office 商店上载的加载项将自动更新。</span><span class="sxs-lookup"><span data-stu-id="52fc2-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="52fc2-144">获取外接程序的详细信息</span><span class="sxs-lookup"><span data-stu-id="52fc2-144">Get details of an add-in</span></span>
<span data-ttu-id="52fc2-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="52fc2-145"></span></span>

<span data-ttu-id="52fc2-146">运行 Get OrganizationAddIn cmdlet，如下所示以获取详细信息的所有加载项上载到租户，包括外接程序的产品 id。</span><span class="sxs-lookup"><span data-stu-id="52fc2-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="52fc2-147">使用_ProductId_参数指定该外接程序您想要检索的详细信息的值与运行 Get OrganizationAddIn cmdlet。</span><span class="sxs-lookup"><span data-stu-id="52fc2-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="52fc2-148">要获取的所有加载项以及分配给的用户和组的完整详细信息，请输出通过管道传递到 Format-list cmdlet，获取 OrganizationAddIn cmdlet 的以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="52fc2-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="52fc2-149">打开或关闭外接程序</span><span class="sxs-lookup"><span data-stu-id="52fc2-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="52fc2-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="52fc2-150"></span></span>

<span data-ttu-id="52fc2-151">若要关闭外接程序以便用户和组分配给它将不再能够访问，运行设置 OrganizationAddIn cmdlet 与_ProductId_参数和_Enabled_参数设置为`$false`，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="52fc2-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="52fc2-152">要启用外接程序后，请运行带有_Enabled_参数设置为同一 cmdlet `$true`。</span><span class="sxs-lookup"><span data-stu-id="52fc2-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="52fc2-153">添加或删除的用户外接程序</span><span class="sxs-lookup"><span data-stu-id="52fc2-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="52fc2-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="52fc2-154"></span></span>

<span data-ttu-id="52fc2-p108">要添加到特定的加载项的用户和组，请运行带有_ProductId_，_添加_和_成员_参数集 OrganizationAddInAssignments cmdlet。用逗号分隔成员的电子邮件的地址。</span><span class="sxs-lookup"><span data-stu-id="52fc2-p108">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters. Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="52fc2-157">要删除的用户和组，请运行相同 cmdlet 使用_删除_参数。</span><span class="sxs-lookup"><span data-stu-id="52fc2-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="52fc2-158">要分配租户上的所有用户外接程序，请运行相同 cmdlet 使用_AssignToEveryone_参数以及其值设置为`$true`。</span><span class="sxs-lookup"><span data-stu-id="52fc2-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="52fc2-159">若要不向每个人分配外接程序，并还原到先前分配的用户和组，可以运行相同 cmdlet，并通过其值设置为关闭_AssignToEveryone_参数`$false`。</span><span class="sxs-lookup"><span data-stu-id="52fc2-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="52fc2-160">外接程序更新</span><span class="sxs-lookup"><span data-stu-id="52fc2-160">Update an add-in</span></span>
<span data-ttu-id="52fc2-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="52fc2-161"></span></span>

<span data-ttu-id="52fc2-162">若要更新外接程序的清单中，运行_ProductId_、 _ManifestPath_，和_区域设置_参数集 OrganizationAddIn cmdlet 下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="52fc2-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="52fc2-163">在 Office 商店正在可用的最新更新的几天内，从 Office 商店上载的加载项将自动更新。</span><span class="sxs-lookup"><span data-stu-id="52fc2-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="52fc2-164">删除外接程序</span><span class="sxs-lookup"><span data-stu-id="52fc2-164">Delete an add-in</span></span>
<span data-ttu-id="52fc2-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="52fc2-165"></span></span>

<span data-ttu-id="52fc2-166">若要删除外接程序，请使用_ProductId_参数中，运行删除 OrganizationAddIn cmdlet 下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="52fc2-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="52fc2-167">每个 cmdlet 获得详细的帮助</span><span class="sxs-lookup"><span data-stu-id="52fc2-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="52fc2-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="52fc2-168"></span></span>

<span data-ttu-id="52fc2-p109">您可以通过使用 get-help cmdlet 查看每个 cmdlet 的帮助详细信息。例如，以下 cmdlet 提供了有关删除 OrganizationAddIn cmdlet 的详细的信息。</span><span class="sxs-lookup"><span data-stu-id="52fc2-p109">You can look at detailed help for each cmdlet by using the Get-help cmdlet. For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


