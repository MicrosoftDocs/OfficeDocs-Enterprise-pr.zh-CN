---
title: OneDrive 业务多地区租户配置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解如何配置 OneDrive 业务多的地区。
ms.openlocfilehash: 56268acd319684ecb713e674b8accbe311d08dce
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="c58e8-103">OneDrive 业务多地区租户配置</span><span class="sxs-lookup"><span data-stu-id="c58e8-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="c58e8-p101">配置您的 OneDrive 的租户业务多的地区之前，请确保您已经阅读了[规划 OneDrive 业务多的地区](plan-for-multi-geo.md)。按照本文中的步骤操作，您将需要您想要启用的位置和您要在其中配置这些位置的测试用户的列表。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="c58e8-106">将 Office 365 计划多地区功能添加到您的租户</span><span class="sxs-lookup"><span data-stu-id="c58e8-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="c58e8-p102">若要使用 OneDrive 业务多的地区，需要_Office 365 中的多个地区功能_计划。使用您的帐户小组将该计划添加到您的租户。您的客户小组将连接您具有适当的授权专家并获得您配置的租户。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="c58e8-p103">请注意， _Office 365 中的多个地区能力_计划的用户级服务计划。您需要为要承载卫星位置中的每个用户的许可证。您可以添加更多许可证随着时间的推移，因为卫星位置中添加用户。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="c58e8-113">一旦您租户已配置_Office 365 中的多个地区能力_计划，**地理位置**选项卡将变为可用的[OneDrive 管理中心](https://admin.onedrive.com)。</span><span class="sxs-lookup"><span data-stu-id="c58e8-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="c58e8-114">将允许数据位置 (ADL) 设置为您的租户</span><span class="sxs-lookup"><span data-stu-id="c58e8-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="c58e8-p104">您必须设置允许数据位置的 SharePoint 为每个地理位置想要使用 OneDrive 业务。下表显示可用的地理位置：</span><span class="sxs-lookup"><span data-stu-id="c58e8-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="c58e8-117"><strong>位置</strong></span><span class="sxs-lookup"><span data-stu-id="c58e8-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="c58e8-118"><strong>代码</strong></span><span class="sxs-lookup"><span data-stu-id="c58e8-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="c58e8-119">北美洲</span><span class="sxs-lookup"><span data-stu-id="c58e8-119">North America</span></span></td>
<td align="left"><span data-ttu-id="c58e8-120">名称</span><span class="sxs-lookup"><span data-stu-id="c58e8-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c58e8-121">欧洲 / 中东 / 非洲</span><span class="sxs-lookup"><span data-stu-id="c58e8-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="c58e8-122">欧元</span><span class="sxs-lookup"><span data-stu-id="c58e8-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c58e8-123">亚太</span><span class="sxs-lookup"><span data-stu-id="c58e8-123">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="c58e8-124">APC 公司</span><span class="sxs-lookup"><span data-stu-id="c58e8-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c58e8-125">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="c58e8-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="c58e8-126">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="c58e8-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c58e8-127">日本</span><span class="sxs-lookup"><span data-stu-id="c58e8-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="c58e8-128">日文</span><span class="sxs-lookup"><span data-stu-id="c58e8-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c58e8-129">加拿大</span><span class="sxs-lookup"><span data-stu-id="c58e8-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="c58e8-130">可以</span><span class="sxs-lookup"><span data-stu-id="c58e8-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c58e8-131">英国</span><span class="sxs-lookup"><span data-stu-id="c58e8-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="c58e8-132">GBR</span><span class="sxs-lookup"><span data-stu-id="c58e8-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c58e8-133">韩国</span><span class="sxs-lookup"><span data-stu-id="c58e8-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="c58e8-134">韩文</span><span class="sxs-lookup"><span data-stu-id="c58e8-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="c58e8-135">若要添加一个附属的地理位置</span><span class="sxs-lookup"><span data-stu-id="c58e8-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="c58e8-136">打开[OneDrive 管理中心](https://admin.onedrive.com)。</span><span class="sxs-lookup"><span data-stu-id="c58e8-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="c58e8-137">导航到**地理位置**选项卡。</span><span class="sxs-lookup"><span data-stu-id="c58e8-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="c58e8-138">单击**添加位置**。</span><span class="sxs-lookup"><span data-stu-id="c58e8-138">Click **Add location**.</span></span>

4. <span data-ttu-id="c58e8-139">选择要添加的位置，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="c58e8-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="c58e8-140">键入您想要使用的地理位置，域，然后单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="c58e8-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="c58e8-141">单击"关闭"。</span><span class="sxs-lookup"><span data-stu-id="c58e8-141">Click **Close**.</span></span>

<span data-ttu-id="c58e8-p105">资源调配可能需要从几小时到 72 小时，具体取决于您组织的大小。完成资源调配的附属位置后，您将收到电子邮件确认。当新的地理位置出现在蓝色上 OneDrive 管理中心中的**地理位置**选项卡上的映射时，您可以继续该地理位置设置用户的首选的数据位置。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="c58e8-p106">使用默认设置，将设置新卫星地理位置。这将允许您配置该地理位置适合于您的本地法规遵从性需要。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="c58e8-147">设置用户首选的数据位置</span><span class="sxs-lookup"><span data-stu-id="c58e8-147">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="c58e8-p107">一旦您启用所需的数据的位置，您可以更新您的用户帐户以使用适当的数据的位置。建议您设置每个用户的首选的数据位置，即使该用户保持在默认数据位置。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="c58e8-150">我们建议您多地区功能推广到更广泛组织之前开始验证与测试用户或用户组小。</span><span class="sxs-lookup"><span data-stu-id="c58e8-150">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="c58e8-p108">在 AAD 有两种类型的用户对象： 云只有用户和同步的用户。请按照相应说明，您的用户类型。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="c58e8-153">同步用户的首选数据位置使用 AD 连接</span><span class="sxs-lookup"><span data-stu-id="c58e8-153">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="c58e8-p109">如果您的公司用户从内部活动目录 (AD) 系统同步到 Azure 活动目录 (AAD)，必须在广告中填充并同步到 AAD 他们 PreferredDataLocation。请按照中的过程， [Azure AD 连接同步： 更改了默认配置](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)配置首选数据位置同步从内部到 AAD 的广告。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="c58e8-156">我们建议，包括设置用户的首选数据位置作为标准用户创建工作流的一部分。</span><span class="sxs-lookup"><span data-stu-id="c58e8-156">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c58e8-p110">为新用户设置没有 OneDrive，等待至少 24 小时之后用户的 PDL 同步到所做的更改的 AAD 传播之前该用户在登录到 OneDrive 的业务。（设置首选的数据位置之前用户登录时提供的业务及其 OneDrive 可确保在正确的位置，将提供用户的新 OneDrive。）</span><span class="sxs-lookup"><span data-stu-id="c58e8-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="c58e8-159">为云只有用户设置首选数据位置</span><span class="sxs-lookup"><span data-stu-id="c58e8-159">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="c58e8-160">如果您的公司用户不同步从内部活动目录 (AD) 系统到 Azure 活动目录 (AAD)，即用 Office 365 或 AAD，然后 PDL 必须设置使用 AAD PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c58e8-160">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="c58e8-p111">本节中的步骤需要[Microsoft Azure 活动目录的 Windows PowerShell 模块](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)。如果您已经安装的 AAD PowerShell，请确保您更新为最新版本。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="c58e8-163">打开 Windows PowerShell Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="c58e8-163">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="c58e8-164">运行`Connect-MsolService`为您的租户输入全局管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="c58e8-164">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="c58e8-p112">使用[组 MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet 来设置每个用户的首选的数据位置。例如：</span><span class="sxs-lookup"><span data-stu-id="c58e8-p112">Use the [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="c58e8-p113">您可以检查以确认首选的数据位置已正确更新，可以使用 Get MsolUser cmdlet。例如：</span><span class="sxs-lookup"><span data-stu-id="c58e8-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="c58e8-169">我们建议，包括设置用户的首选数据位置作为标准用户创建工作流的一部分。</span><span class="sxs-lookup"><span data-stu-id="c58e8-169">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c58e8-p114">为新用户设置没有 OneDrive，等待至少 24 小时之后用户的 PDL 设置的更改将传播到 SharePoint OneDrive 在用户登录之前。（设置首选的数据位置之前用户登录时提供的业务及其 OneDrive 可确保在正确的位置，将提供用户的新 OneDrive。）</span><span class="sxs-lookup"><span data-stu-id="c58e8-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="c58e8-172">OneDrive 资源调配以及 PDL 的效果</span><span class="sxs-lookup"><span data-stu-id="c58e8-172">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="c58e8-p115">如果用户已在组织中创建的 OneDrive 网站，设置其 PDL 不会自动移动他们现有的 OneDrive。若要移动用户的 OneDrive，请参阅[OneDrive 移动业务地区的](move-onedrive-between-geo-locations.md)地理位置之间请按照移动 OneDrive 中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="c58e8-175">如果用户不具有组织内的 OneDrive 网站，OneDrive 中将提供它们为 PDL 值，根据假设用户 PDL 匹配的公司允许的数据位置 (ADLs) 之一。</span><span class="sxs-lookup"><span data-stu-id="c58e8-175">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="c58e8-176">配置多地区搜索</span><span class="sxs-lookup"><span data-stu-id="c58e8-176">Configuring Multi-Geo search</span></span>

<span data-ttu-id="c58e8-177">多个地区组织将具有聚合搜索功能允许搜索查询返回结果，从任何地方组织内。</span><span class="sxs-lookup"><span data-stu-id="c58e8-177">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="c58e8-178">默认情况下，从这些入口点的搜索将返回聚合结果，即使每个搜索索引在其相关的地理位置：</span><span class="sxs-lookup"><span data-stu-id="c58e8-178">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="c58e8-179">OneDrive 为公司的</span><span class="sxs-lookup"><span data-stu-id="c58e8-179">OneDrive for business</span></span>

- <span data-ttu-id="c58e8-180">Delve</span><span class="sxs-lookup"><span data-stu-id="c58e8-180">Delve</span></span>

- <span data-ttu-id="c58e8-181">SharePoint 主页</span><span class="sxs-lookup"><span data-stu-id="c58e8-181">SharePoint Home</span></span>

- <span data-ttu-id="c58e8-182">搜索中心</span><span class="sxs-lookup"><span data-stu-id="c58e8-182">Search Center</span></span>

<span data-ttu-id="c58e8-183">此外，多地区搜索功能可以配置为自定义搜索应用程序使用 SharePoint 搜索 API。</span><span class="sxs-lookup"><span data-stu-id="c58e8-183">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="c58e8-184">请包括任何限制和差异的说明，查看[配置搜索 OneDrive 业务多的地区](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="c58e8-184">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="c58e8-185">验证业务多地区配置 OneDrive</span><span class="sxs-lookup"><span data-stu-id="c58e8-185">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="c58e8-p116">下面是您可能希望验证计划之前广泛推出 OneDrive 业务多的地区为您的公司中包括一些基本的用例。一旦完成这些测试，与贵公司相关的任何其他使用用例，您可以选择将上移动到初始实验组中添加用户。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="c58e8-188">**OneDrive 为公司的**</span><span class="sxs-lookup"><span data-stu-id="c58e8-188">**OneDrive for Business**</span></span>

<span data-ttu-id="c58e8-p117">从 Office 365 提供应用程序启动程序中选择 OneDrive，并确认被自动定向到合适的地理位置的用户，根据用户的 PDL。OneDrive 为企业现在应该开始在该位置设置。一次调配，重试上载和下载某些文档。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="c58e8-192">**OneDrive 移动应用程序**</span><span class="sxs-lookup"><span data-stu-id="c58e8-192">**OneDrive Mobile App**</span></span>

<span data-ttu-id="c58e8-p118">登录到您的测试帐户凭据与您 OneDrive 移动应用程序。请确认您可以看到您的业务文件 OneDrive，并可以从您的移动设备与它们进行交互。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="c58e8-195">**OneDrive 同步客户端**</span><span class="sxs-lookup"><span data-stu-id="c58e8-195">**OneDrive sync client**</span></span>

<span data-ttu-id="c58e8-p119">请确认 OneDrive 同步客户端会自动检测您的业务的地理位置在登录时的 OneDrive。如果您需要下载同步客户端，您可以单击 OneDrive 库中的**同步**。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="c58e8-198">**Office 应用程序**</span><span class="sxs-lookup"><span data-stu-id="c58e8-198">**Office applications**</span></span>

<span data-ttu-id="c58e8-p120">请确认您可以访问 OneDrive 业务为通过从 Office 应用程序 （如 Word) 记录。打开 Office 应用程序，然后选择"OneDrive- <TenantName>"。办公室将检测您的 OneDrive 位置并显示您可以打开的文件。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="c58e8-202">**Sharing**</span><span class="sxs-lookup"><span data-stu-id="c58e8-202">**Sharing**</span></span>

<span data-ttu-id="c58e8-p121">尝试共享 OneDrive 文件。确认人员选取器显示您所有 SharePoint 联机用户无论其地理位置如何。</span><span class="sxs-lookup"><span data-stu-id="c58e8-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
