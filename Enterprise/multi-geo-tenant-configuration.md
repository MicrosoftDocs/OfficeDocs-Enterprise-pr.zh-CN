---
title: OneDrive for Business 多地理位置租户配置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: 了解如何配置 OneDrive for Business 多地理位置。
ms.openlocfilehash: 6c4a1012f3f26265ef88d82c55bb3ac11cc82da4
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849868"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="1f6c9-103">OneDrive for Business 多地理位置租户配置</span><span class="sxs-lookup"><span data-stu-id="1f6c9-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="1f6c9-p101">在配置 OneDrive for Business 多地理位置之前，请确保已阅读[规划 OneDrive for Business 多地理位置](plan-for-multi-geo.md)。若要执行本文中的步骤，你需要具有想要启用作为附属位置的地理位置的列表和要在这些位置中预配的测试用户。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="1f6c9-106">将 Office 365 中的多地理位置功能计划添加到租户</span><span class="sxs-lookup"><span data-stu-id="1f6c9-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="1f6c9-p102">要使用 OneDrive for Business 多地理位置，你需要有 _Office 365 的多地理位置功能_计划。与你的帐户团队合作，将此计划添加到你的租户。你的帐户团队会为你联系合适的许可专家，并配置你的租户。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="1f6c9-p103">请注意，_Office 365 的多地理位置功能_计划是一个用户级别的服务计划。你需要为每个想要托管在附属位置的用户提供许可证。随着你将用户添加到附属位置，你可以随时添加更多许可证。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="1f6c9-113">你的租户配置了 _Office 365 的多地理位置功能_计划后，便可使用 [OneDrive 管理中心的](https://admin.onedrive.com)“地理位置”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="1f6c9-114">向租户添加附属地理位置</span><span class="sxs-lookup"><span data-stu-id="1f6c9-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="1f6c9-p104">必须为想要使用 OneDrive for Business 的每个地理位置添加附属位置。下表显示了可用的地理位置：</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p104">You must add a satellite location for each geo location where you want to use OneDrive for Business. Available geo locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="1f6c9-117"><strong>位置</strong></span><span class="sxs-lookup"><span data-stu-id="1f6c9-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="1f6c9-118"><strong>代码</strong></span><span class="sxs-lookup"><span data-stu-id="1f6c9-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="1f6c9-119">亚太地区</span><span class="sxs-lookup"><span data-stu-id="1f6c9-119">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="1f6c9-120">APC</span><span class="sxs-lookup"><span data-stu-id="1f6c9-120">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1f6c9-121">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="1f6c9-121">Australia</span></span></td>
<td align="left"><span data-ttu-id="1f6c9-122">AUS</span><span class="sxs-lookup"><span data-stu-id="1f6c9-122">AUS</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1f6c9-123">加拿大</span><span class="sxs-lookup"><span data-stu-id="1f6c9-123">Canada</span></span></td>
<td align="left"><span data-ttu-id="1f6c9-124">CAN</span><span class="sxs-lookup"><span data-stu-id="1f6c9-124">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1f6c9-125">欧洲/中东/非洲</span><span class="sxs-lookup"><span data-stu-id="1f6c9-125">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="1f6c9-126">EUR</span><span class="sxs-lookup"><span data-stu-id="1f6c9-126">EUR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1f6c9-127">法国</span><span class="sxs-lookup"><span data-stu-id="1f6c9-127">France</span></span></td>
<td align="left"><span data-ttu-id="1f6c9-128">FRA</span><span class="sxs-lookup"><span data-stu-id="1f6c9-128">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="1f6c9-129">日本</span><span class="sxs-lookup"><span data-stu-id="1f6c9-129">Japan</span></span></td>
<td align="left"><span data-ttu-id="1f6c9-130">JPN</span><span class="sxs-lookup"><span data-stu-id="1f6c9-130">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1f6c9-131">韩国</span><span class="sxs-lookup"><span data-stu-id="1f6c9-131">Korea</span></span></td>
<td align="left"><span data-ttu-id="1f6c9-132">KOR</span><span class="sxs-lookup"><span data-stu-id="1f6c9-132">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="1f6c9-133">北美</span><span class="sxs-lookup"><span data-stu-id="1f6c9-133">North America</span></span></td>
<td align="left"><span data-ttu-id="1f6c9-134">NAM</span><span class="sxs-lookup"><span data-stu-id="1f6c9-134">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="1f6c9-135">英国</span><span class="sxs-lookup"><span data-stu-id="1f6c9-135">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="1f6c9-136">GBR</span><span class="sxs-lookup"><span data-stu-id="1f6c9-136">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="1f6c9-137">添加附属位置</span><span class="sxs-lookup"><span data-stu-id="1f6c9-137">To add a satellite geo location</span></span>

1. <span data-ttu-id="1f6c9-138">打开 [OneDrive 管理中心](https://admin.onedrive.com)。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-138">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="1f6c9-139">导航到“地理位置”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-139">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="1f6c9-140">单击“添加位置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-140">Click **Add location**.</span></span>

4. <span data-ttu-id="1f6c9-141">选择要添加的位置，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-141">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="1f6c9-142">键入想要与地理位置一同使用的域，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-142">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="1f6c9-143">单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-143">Click **Close**.</span></span>

<span data-ttu-id="1f6c9-p105">预配可能需要几小时到 72 小时，具体要取决于租户的大小。附属位置设置完成后，你将收到电子邮件确认。当新地理位置在 OneDrive 管理中心的“地理位置”\*\*\*\* 选项卡的地图上以蓝色显示时，你可以继续将用户的首选数据位置设置为该地理位置。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="1f6c9-p106">你的新附属位置将使用默认设置进行设置。这可使你根据当地合规性要求来配置该附属位置。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="1f6c9-149">设置用户的首选数据位置</span><span class="sxs-lookup"><span data-stu-id="1f6c9-149">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="1f6c9-p107">一旦启用了所需的附属位置，就可以更新你的用户帐户以使用适当的首选数据位置。我们建议你为每个用户设置一个首选数据位置，即使该用户处于中心位置。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="1f6c9-152">我们建议你在组织内更广泛地推广多地理位置之前，请先以测试用户或少量用户来进行验证。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-152">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="1f6c9-p108">在 AAD 中，有两种类型的用户对象：仅限云的用户和同步用户。请按照针对用户类型的相应说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="1f6c9-155">使用 AD Connect 同步用户的首选数据位置</span><span class="sxs-lookup"><span data-stu-id="1f6c9-155">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="1f6c9-p109">如果将公司的用户从本地 Active Directory 系统同步到 Azure Active Directory，则其 PreferredDataLocation 必须在 AD 中填充并同步到 AAD。按照 [Azure AD Connect 同步：更改默认配置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)中的流程，将首选数据位置同步从本地 Active Directory 配置到 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="1f6c9-158">我们建议你在标准用户创建工作流中加入设置用户的“首选数据位置”。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-158">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f6c9-p110">对于未预配 OneDrive 的新用户，请在用户的 PDL 同步到 Azure Active Directory 后至少等待 24 小时，以便在用户登录到 OneDrive for Business 之前传播更改。（在用户登录之前设置首选数据位置，以预配 OneDrive for Business，这可确保用户的新 OneDrive 将在正确的位置进行设置。）</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="1f6c9-161">为仅限云的用户设置首选数据位置</span><span class="sxs-lookup"><span data-stu-id="1f6c9-161">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="1f6c9-162">如果公司的用户没有从本地 Active Directory 系统同步到 Azure Active Directory，这意味着它们是在 Office 365 或 Azure Active Directory 中创建的，必须使用 Azure Active Directory PowerShell 设置 PDL。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-162">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="1f6c9-p111">此部分中的步骤需要使用[用于 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)。如果已安装 Azure Active Directory PowerShell，请确保更新到最新版本。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="1f6c9-165">打开用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-165">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="1f6c9-166">运行 `Connect-MsolService`，然后输入租户的全局管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-166">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="1f6c9-p112">使用 [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet 来设置每位用户的首选数据位置。例如：</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="1f6c9-p113">你可以使用 Get-MsolUser cmdlet 进行检查，以确认首选数据位置已正确更新。例如：</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="1f6c9-171">我们建议你在标准用户创建工作流中加入设置用户的“首选数据位置”。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-171">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f6c9-p114">对于未设置 OneDrive 的新用户，请在用户的 PDL 设置后至少等待 24 小时，以便在用户登录到 OneDrive 之前传播更改。（在用户登录之前设置首选数据位置，以预配 OneDrive for Business，这可确保用户的新 OneDrive 将在正确的位置进行设置。）</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="1f6c9-174">OneDrive 设置和 PDL 效果</span><span class="sxs-lookup"><span data-stu-id="1f6c9-174">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="1f6c9-p115">如果用户已拥有在租户中创建的 OneDrive 网站，则设置其 PDL 将不能自动移动其现有 OneDrive。若要移动该用户的 OneDrive，请参阅 [OneDrive for Business 地理位置移动](move-onedrive-between-geo-locations.md)，在地理位置之间移动 OneDrive 时，请按照其中的说明。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="1f6c9-177">如果用户在租户内没有 OneDrive 网站，则假定用户的 PDL 与公司的附属位置之一相匹配，根据其 PDL 值为他们设置 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-177">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="1f6c9-178">配置多地理位置搜索</span><span class="sxs-lookup"><span data-stu-id="1f6c9-178">Configuring Multi-Geo search</span></span>

<span data-ttu-id="1f6c9-179">你的多地理位置租户将具有聚合搜索功能，允许搜索查询从租户中的任何位置返回结果。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-179">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="1f6c9-180">默认情况下，即使每个搜索索引位于其相关地理位置中，这些入口点的搜索也会返回聚合结果：</span><span class="sxs-lookup"><span data-stu-id="1f6c9-180">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="1f6c9-181">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="1f6c9-181">OneDrive for business</span></span>

- <span data-ttu-id="1f6c9-182">Delve</span><span class="sxs-lookup"><span data-stu-id="1f6c9-182">Delve</span></span>

- <span data-ttu-id="1f6c9-183">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="1f6c9-183">SharePoint Home</span></span>

- <span data-ttu-id="1f6c9-184">搜索中心</span><span class="sxs-lookup"><span data-stu-id="1f6c9-184">Search Center</span></span>

<span data-ttu-id="1f6c9-185">此外，可为使用 SharePoint 搜索 API 的自定义搜索应用程序配置多地理位置搜索功能。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-185">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="1f6c9-186">有关说明（包括任何限制和差异），请查看[为 OneDrive for Business 多地理位置配置搜索](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-186">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="1f6c9-187">验证 OneDrive for Business 多地理位置配置</span><span class="sxs-lookup"><span data-stu-id="1f6c9-187">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="1f6c9-p116">以下是在你向公司广泛推出 OneDrive for Business 多地理位置之前，可能希望将其纳入验证计划的一些基本用例。在完成了这些测试以及任何与公司相关的其他用例后，你可以选择继续添加初始试点组中的用户。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="1f6c9-190">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="1f6c9-190">**OneDrive for Business**</span></span>

<span data-ttu-id="1f6c9-p117">从 Office 365 应用启动器中选择 OneDrive，并根据用户的 PDL 确认你已自动定向到用户的相应地理位置。OneDrive for Business 现在应该开始在该位置进行预配。完成预配后，可尝试上传和下载一些文件。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="1f6c9-194">**OneDrive 移动应用**</span><span class="sxs-lookup"><span data-stu-id="1f6c9-194">**OneDrive Mobile App**</span></span>

<span data-ttu-id="1f6c9-p118">使用测试帐户凭据登录 OneDrive 移动应用。确认你可以看到 OneDrive for business 文件，并可以通过移动设备与它们进行交互。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="1f6c9-197">**OneDrive 同步客户端**</span><span class="sxs-lookup"><span data-stu-id="1f6c9-197">**OneDrive sync client**</span></span>

<span data-ttu-id="1f6c9-p119">确认 OneDrive 同步客户端在登录后可自动检测你的 OneDrive for Business 地理位置。如果你需要下载同步客户端，则可单击 OneDrive 库中的“同步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="1f6c9-200">**Office 应用程序**</span><span class="sxs-lookup"><span data-stu-id="1f6c9-200">**Office applications**</span></span>

<span data-ttu-id="1f6c9-p120">通过从 Office 应用程序（如 Word）登录，确认你可以访问 OneDrive for Business。打开 Office 应用程序，然后选择“OneDrive – <TenantName>”。Office 将检测你的 OneDrive 位置，并显示可打开的文件。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="1f6c9-204">**共享**</span><span class="sxs-lookup"><span data-stu-id="1f6c9-204">**Sharing**</span></span>

<span data-ttu-id="1f6c9-p121">尝试共享 OneDrive 文件。确认人员选取器向你显示所有 SharePoint 在线用户，而不管他们的地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="1f6c9-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
