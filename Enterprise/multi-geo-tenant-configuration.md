---
title: Microsoft 365 多地理位置租户配置
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: 了解如何配置 Microsoft 365 多地理位置。
ms.openlocfilehash: ffacd18a95288cfcce0794afceaf7ff22bfa2c76
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057718"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a><span data-ttu-id="b528f-103">Microsoft 365 多地理位置租户配置</span><span class="sxs-lookup"><span data-stu-id="b528f-103">Microsoft 365 Multi-Geo tenant configuration</span></span>

<span data-ttu-id="b528f-104">配置 Microsoft 365 多地理位置租户前，请务必先阅读[计划使用 Microsoft 365 多地理位置](plan-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="b528f-104">Before you configure your tenant for Microsoft 365 Multi-Geo, be sure you have read [Plan for Microsoft 365 Multi-Geo](plan-for-multi-geo.md).</span></span> <span data-ttu-id="b528f-105">若要执行本文中的步骤，需要列出要作为附属位置启用的地理位置，以及要为这些位置预配的测试用户。</span><span class="sxs-lookup"><span data-stu-id="b528f-105">To follow the steps in this article, you'll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-microsoft-365-plan-to-your-tenant"></a><span data-ttu-id="b528f-106">将“Microsoft 365 中的多地理位置功能”计划添加到租户</span><span class="sxs-lookup"><span data-stu-id="b528f-106">Add the Multi-Geo Capabilities in Microsoft 365 plan to your tenant</span></span>

<span data-ttu-id="b528f-107">若要使用 Microsoft 365 多地理位置，需要有“_Microsoft 365 中的多地理位置功能_”计划。</span><span class="sxs-lookup"><span data-stu-id="b528f-107">To use Microsoft 365 Multi-Geo, you need the _Multi-Geo Capabilities in Microsoft 365_ plan.</span></span> <span data-ttu-id="b528f-108">与帐户团队合作，以向租户添加此计划。</span><span class="sxs-lookup"><span data-stu-id="b528f-108">Work with your account team to add this plan to your tenant.</span></span> <span data-ttu-id="b528f-109">帐户团队会让你与相应的许可专家联系，并配置你的租户。</span><span class="sxs-lookup"><span data-stu-id="b528f-109">Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="b528f-p103">请注意，“_Microsoft 365 的多地理位置功能_”计划是一个用户级别的服务计划。你需要为每个想要托管在附属位置的用户提供许可证。随着你将用户添加到附属位置，你可以随时添加更多许可证。</span><span class="sxs-lookup"><span data-stu-id="b528f-p103">Note that the _Multi-Geo Capabilities in Microsoft 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="b528f-113">在为租户预配了“_Microsoft 365 中的多地理位置功能_”计划后，便能在 OneDrive 和 SharePoint 管理中心内使用“**地理位置**”选项卡。</span><span class="sxs-lookup"><span data-stu-id="b528f-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Microsoft 365_ plan, the **Geo locations** tab will become available in the OneDrive and SharePoint admin centers.</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="b528f-114">向租户添加附属位置</span><span class="sxs-lookup"><span data-stu-id="b528f-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="b528f-115">必须为要存储数据的每个地理位置添加附属位置。</span><span class="sxs-lookup"><span data-stu-id="b528f-115">You must add a satellite location for each geo location where you want to store data.</span></span> <span data-ttu-id="b528f-116">下表列出了可用的地理位置：</span><span class="sxs-lookup"><span data-stu-id="b528f-116">Available geo locations are shown in the following table:</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![SharePoint 管理中心内“地理位置”页屏幕截图](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="b528f-118">添加附属位置的具体步骤</span><span class="sxs-lookup"><span data-stu-id="b528f-118">To add a satellite location</span></span>

1. <span data-ttu-id="b528f-119">打开 SharePoint 管理中心。</span><span class="sxs-lookup"><span data-stu-id="b528f-119">Open the SharePoint admin center.</span></span>

2. <span data-ttu-id="b528f-120">导航到“地理位置”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="b528f-120">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="b528f-121">单击“添加位置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b528f-121">Click **Add location**.</span></span>

4. <span data-ttu-id="b528f-122">选择要添加的位置，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b528f-122">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="b528f-123">键入想要与地理位置一同使用的域，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b528f-123">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="b528f-124">单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b528f-124">Click **Close**.</span></span>

<span data-ttu-id="b528f-p105">预配可能需要几小时到 72 小时，具体要取决于租户的大小。附属位置设置完成后，你将收到电子邮件确认。当新地理位置在 OneDrive 管理中心的“地理位置”\*\*\*\* 选项卡的地图上以蓝色显示时，你可以继续将用户的首选数据位置设置为该地理位置。</span><span class="sxs-lookup"><span data-stu-id="b528f-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="b528f-p106">你的新附属位置将使用默认设置进行设置。这可使你根据当地合规性要求来配置该附属位置。</span><span class="sxs-lookup"><span data-stu-id="b528f-p106">Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="b528f-130">设置用户的首选数据位置</span><span class="sxs-lookup"><span data-stu-id="b528f-130">Setting users' preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="b528f-p107">一旦启用了所需的附属位置，就可以更新你的用户帐户以使用适当的首选数据位置。我们建议你为每个用户设置一个首选数据位置，即使该用户处于中心位置。</span><span class="sxs-lookup"><span data-stu-id="b528f-p107">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b528f-133">如果用户的首选数据位置设置为未配置为附属位置或中心位置的位置，系统会在预配 OneDrive 和 SharePoint 网站以及组邮箱时，默认使用中心位置。</span><span class="sxs-lookup"><span data-stu-id="b528f-133">If a user's preferred data location is set to a location that has not been configured as a satellite location or the central location, the system will default to the central location when provisioning OneDrive and SharePoint sites and Group mailboxes.</span></span>

> [!TIP]
> <span data-ttu-id="b528f-134">建议先使用测试用户或少量用户进行验证，再在组织内更广泛地推出多地理位置功能。</span><span class="sxs-lookup"><span data-stu-id="b528f-134">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="b528f-135">在 Azure Active Directory 中，有以下两种类型的用户对象：仅限云用户和同步用户。</span><span class="sxs-lookup"><span data-stu-id="b528f-135">In Azure Active Directory there are two types of user objects: cloud only users and synchronized users.</span></span> <span data-ttu-id="b528f-136">请按照用户类型对应的说明操作。</span><span class="sxs-lookup"><span data-stu-id="b528f-136">Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a><span data-ttu-id="b528f-137">使用 Azure Active Directory Connect 同步用户的首选数据位置</span><span class="sxs-lookup"><span data-stu-id="b528f-137">Synchronize user's Preferred Data Location using Azure Active Directory Connect</span></span> 

<span data-ttu-id="b528f-p109">如果将公司的用户从本地 Active Directory 系统同步到 Azure Active Directory，则其 PreferredDataLocation 必须在 AD 中填充并同步到 AAD。请遵循 [Azure Active Directory Connect 同步：为 Microsoft 365 资源配置首选数据位置](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation)中的过程，将首选数据位置同步从本地 Active Directory 配置为 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="b528f-p109">If your company’s users are synchronized from an on-premises Active Directory system to Azure Active Directory, their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure Active Directory Connect sync: Configure preferred data location for Microsoft 365 resources](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from on-premises Active Directory to Azure Active Directory.</span></span>

<span data-ttu-id="b528f-140">建议在标准用户创建工作流中设置用户的首选数据位置。</span><span class="sxs-lookup"><span data-stu-id="b528f-140">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b528f-141">对于未预配 OneDrive 的新用户，请在将用户的 PDL 同步到 Azure Active Directory 之后至少等待 24 小时，以便在用户登录 OneDrive for Business 之前传播更改。</span><span class="sxs-lookup"><span data-stu-id="b528f-141">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure Active Directory for the changes to propagate before the user logs in to OneDrive for Business.</span></span> <span data-ttu-id="b528f-142">（在用户登录预配 OneDrive for Business 前设置首选数据位置，可确保在正确的位置中预配用户的新 OneDrive。）</span><span class="sxs-lookup"><span data-stu-id="b528f-142">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="b528f-143">设置仅限云用户的首选数据位置</span><span class="sxs-lookup"><span data-stu-id="b528f-143">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="b528f-144">如果公司的用户没有从本地 Active Directory 系统同步到 Azure Active Directory，这意味着他们是在 Microsoft 365 或 Azure Active Directory 中创建的，必须使用 Azure Active Directory PowerShell 设置 PDL。</span><span class="sxs-lookup"><span data-stu-id="b528f-144">If your company's users are not synchronized from an on-premises Active Directory system to Azure Active Directory, meaning they are created in Microsoft 365 or Azure Active Directory, then the PDL must be set using Azure Active Directory PowerShell.</span></span>

<span data-ttu-id="b528f-p111">此部分中的步骤需要使用[用于 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)。如果已安装 Azure Active Directory PowerShell，请确保更新到最新版本。</span><span class="sxs-lookup"><span data-stu-id="b528f-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have Azure Active Directory PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="b528f-147">打开用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="b528f-147">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="b528f-148">运行 `Connect-MsolService`，然后输入租户的全局管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="b528f-148">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="b528f-p112">使用 [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet 来设置每位用户的首选数据位置。例如：</span><span class="sxs-lookup"><span data-stu-id="b528f-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="b528f-p113">你可以使用 Get-MsolUser cmdlet 进行检查，以确认首选数据位置已正确更新。例如：</span><span class="sxs-lookup"><span data-stu-id="b528f-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![显示 set-msoluser 的 PowerShell 窗口屏幕截图](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="b528f-154">建议在标准用户创建工作流中设置用户的首选数据位置。</span><span class="sxs-lookup"><span data-stu-id="b528f-154">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b528f-155">对于未预配 OneDrive 的新用户，请在设置用户的 PDL 之后至少等待 24 小时，以便在用户登录 OneDrive 之前传播更改。</span><span class="sxs-lookup"><span data-stu-id="b528f-155">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive.</span></span> <span data-ttu-id="b528f-156">（在用户登录预配 OneDrive for Business 前设置首选数据位置，可确保在正确的位置中预配用户的新 OneDrive。）</span><span class="sxs-lookup"><span data-stu-id="b528f-156">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="b528f-157">OneDrive 设置和 PDL 效果</span><span class="sxs-lookup"><span data-stu-id="b528f-157">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="b528f-158">如果用户已有在租户中创建的 OneDrive 网站，设置用户 PDL 不会自动移动他们的现有 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="b528f-158">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive.</span></span> <span data-ttu-id="b528f-159">若要移动用户的 OneDrive，请参阅 [OneDrive for Business 异地移动](move-onedrive-between-geo-locations.md)，并按照“在地理位置之间移动 OneDrive”中的说明操作。</span><span class="sxs-lookup"><span data-stu-id="b528f-159">To move a user's OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span> <span data-ttu-id="b528f-160">（请注意，用户的 Exchange 邮箱不会在你设置用户的 PDL 后自动移动。）</span><span class="sxs-lookup"><span data-stu-id="b528f-160">(Note that the user's Exchange mailbox does move automatically when you set the user's PDL.)</span></span>

<span data-ttu-id="b528f-161">如果用户在租户内没有 OneDrive 网站，将会根据用户的 PDL 值为他们预配 OneDrive，假定用户的 PDL 与公司的附属位置之一匹配。</span><span class="sxs-lookup"><span data-stu-id="b528f-161">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company's satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="b528f-162">配置多地理位置搜索</span><span class="sxs-lookup"><span data-stu-id="b528f-162">Configuring Multi-Geo search</span></span>

<span data-ttu-id="b528f-163">你的多地理位置租户将具有聚合搜索功能，允许搜索查询从租户中的任何位置返回结果。</span><span class="sxs-lookup"><span data-stu-id="b528f-163">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="b528f-164">默认情况下，即使每个搜索索引位于其相关地理位置中，这些入口点的搜索也会返回聚合结果：</span><span class="sxs-lookup"><span data-stu-id="b528f-164">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="b528f-165">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="b528f-165">OneDrive for business</span></span>

- <span data-ttu-id="b528f-166">Delve</span><span class="sxs-lookup"><span data-stu-id="b528f-166">Delve</span></span>

- <span data-ttu-id="b528f-167">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="b528f-167">SharePoint Home</span></span>

- <span data-ttu-id="b528f-168">搜索中心</span><span class="sxs-lookup"><span data-stu-id="b528f-168">Search Center</span></span>

<span data-ttu-id="b528f-169">此外，可为使用 SharePoint 搜索 API 的自定义搜索应用程序配置多地理位置搜索功能。</span><span class="sxs-lookup"><span data-stu-id="b528f-169">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="b528f-170">有关说明（包括任何限制和差异），请查看[为 OneDrive for Business 多地理位置配置搜索](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="b528f-170">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a><span data-ttu-id="b528f-171">验证 Microsoft 365 多地理位置配置</span><span class="sxs-lookup"><span data-stu-id="b528f-171">Validating the Microsoft 365 Multi-Geo configuration</span></span>

<span data-ttu-id="b528f-172">下面是建议在公司中更广泛地推出 Microsoft 365 多地理位置前，在验证计划中添加的一些基本用例。</span><span class="sxs-lookup"><span data-stu-id="b528f-172">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out Microsoft 365 Multi-Geo to your company.</span></span> <span data-ttu-id="b528f-173">完成这些测试以及与公司相关的其他任何用例后，可以选择继续在初始试点组中添加用户。</span><span class="sxs-lookup"><span data-stu-id="b528f-173">Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="b528f-174">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="b528f-174">**OneDrive for Business**</span></span>

<span data-ttu-id="b528f-175">从 Microsoft 365 应用启动器中选择“OneDrive”，并确认是否自动定向到用户的相应地理位置（以用户 PDL 为依据）。</span><span class="sxs-lookup"><span data-stu-id="b528f-175">Select OneDrive from the Microsoft 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user's PDL.</span></span> <span data-ttu-id="b528f-176">OneDrive for Business 现在应该开始在相应位置进行预配。</span><span class="sxs-lookup"><span data-stu-id="b528f-176">OneDrive for Business should now begin provisioning at that location.</span></span> <span data-ttu-id="b528f-177">预配后，立即尝试上传并下载一些文档。</span><span class="sxs-lookup"><span data-stu-id="b528f-177">Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="b528f-178">**OneDrive 移动应用**</span><span class="sxs-lookup"><span data-stu-id="b528f-178">**OneDrive Mobile App**</span></span>

<span data-ttu-id="b528f-p118">使用测试帐户凭据登录 OneDrive 移动应用。确认你可以看到 OneDrive for business 文件，并可以通过移动设备与它们进行交互。</span><span class="sxs-lookup"><span data-stu-id="b528f-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="b528f-181">**OneDrive 同步客户端**</span><span class="sxs-lookup"><span data-stu-id="b528f-181">**OneDrive sync client**</span></span>

<span data-ttu-id="b528f-p119">确认 OneDrive 同步客户端在登录后可自动检测你的 OneDrive for Business 地理位置。如果你需要下载同步客户端，则可单击 OneDrive 库中的“同步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b528f-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="b528f-184">**Office 应用程序**</span><span class="sxs-lookup"><span data-stu-id="b528f-184">**Office applications**</span></span>

<span data-ttu-id="b528f-p120">通过从 Office 应用程序（如 Word）登录，确认你可以访问 OneDrive for Business。打开 Office 应用程序，然后选择“OneDrive – <TenantName>”。Office 将检测你的 OneDrive 位置，并显示可打开的文件。</span><span class="sxs-lookup"><span data-stu-id="b528f-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="b528f-188">**共享**</span><span class="sxs-lookup"><span data-stu-id="b528f-188">**Sharing**</span></span>

<span data-ttu-id="b528f-p121">尝试共享 OneDrive 文件。确认人员选取器向你显示所有 SharePoint 在线用户，而不管他们的地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="b528f-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
