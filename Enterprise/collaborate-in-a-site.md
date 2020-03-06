---
title: 在网站中与来宾协作
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords: NOCSH
description: 了解如何在 SharePoint 网站中与来宾进行协作。
ms.openlocfilehash: 8c1c34fded910701275a80aa0740a746a2458156
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549111"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="ad55e-103">在网站中与来宾协作</span><span class="sxs-lookup"><span data-stu-id="ad55e-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="ad55e-104">如果需要在文档、数据和列表之间与来宾进行协作，则可以使用 SharePoint 网站。</span><span class="sxs-lookup"><span data-stu-id="ad55e-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="ad55e-105">新式 SharePoint 网站连接到可管理网站成员身份的 Office 365 组，并提供其他协作工具（如共享邮箱和日历）。</span><span class="sxs-lookup"><span data-stu-id="ad55e-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="ad55e-106">在本文中，我们将逐步完成为与来宾协作设置 SharePoint 网站所必需的 Microsoft 365 配置步骤。</span><span class="sxs-lookup"><span data-stu-id="ad55e-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="ad55e-107">视频演示</span><span class="sxs-lookup"><span data-stu-id="ad55e-107">Video demonstration</span></span>

<span data-ttu-id="ad55e-108">该视频显示了本文档中描述的配置步骤。</span><span class="sxs-lookup"><span data-stu-id="ad55e-108">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="ad55e-109">Azure 组织关系设置</span><span class="sxs-lookup"><span data-stu-id="ad55e-109">Azure Organizational relationships settings</span></span>

<span data-ttu-id="ad55e-110">Microsoft 365 中的共享受 Azure Active Directory 中的组织关系设置的最高级别的管辖。</span><span class="sxs-lookup"><span data-stu-id="ad55e-110">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="ad55e-111">如果在 Azure AD 中禁用或限制来宾共享，这将替代您在 Microsoft 365 中配置的任何共享设置。</span><span class="sxs-lookup"><span data-stu-id="ad55e-111">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="ad55e-112">检查组织关系设置以确保不会阻止与来宾共享。</span><span class="sxs-lookup"><span data-stu-id="ad55e-112">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory 组织关系设置页面的屏幕截图](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="ad55e-114">设置组织关系设置</span><span class="sxs-lookup"><span data-stu-id="ad55e-114">To set organizational relationship settings</span></span>

1. <span data-ttu-id="ad55e-115">登录到 Microsoft Azure [https://portal.azure.com](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="ad55e-115">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="ad55e-116">在左侧导航中，单击 " **Azure Active Directory**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-116">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="ad55e-117">在 "**概述**" 窗格中，单击 "**组织关系**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-117">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="ad55e-118">在 "**组织关系**" 窗格中，单击 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-118">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="ad55e-119">确保**来宾邀请者角色中的管理员和用户可以邀请**和**成员**都可以邀请都设置为 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="ad55e-119">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="ad55e-120">如果进行了任何更改，请单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="ad55e-120">If you made changes, click **Save**.</span></span>

<span data-ttu-id="ad55e-121">请注意 "**协作限制**" 部分中的设置。</span><span class="sxs-lookup"><span data-stu-id="ad55e-121">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="ad55e-122">确保不会阻止您要与之进行协作的来宾域。</span><span class="sxs-lookup"><span data-stu-id="ad55e-122">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="ad55e-123">Office 365 组来宾设置</span><span class="sxs-lookup"><span data-stu-id="ad55e-123">Office 365 Groups guest settings</span></span>

<span data-ttu-id="ad55e-124">新式 SharePoint 网站使用 Office 365 组来控制网站访问。</span><span class="sxs-lookup"><span data-stu-id="ad55e-124">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="ad55e-125">必须打开 Office 365 组来宾设置，才能使 SharePoint 网站中的来宾访问能够正常工作。</span><span class="sxs-lookup"><span data-stu-id="ad55e-125">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Microsoft 365 管理中心中的 Office 365 组来宾设置的屏幕截图](media/office-365-groups-guest-settings.png)

<span data-ttu-id="ad55e-127">设置 Office 365 组来宾设置</span><span class="sxs-lookup"><span data-stu-id="ad55e-127">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="ad55e-128">在 Microsoft 365 管理中心的左侧导航栏中，展开 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-128">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="ad55e-129">单击 "**服务" & 外接程序**。</span><span class="sxs-lookup"><span data-stu-id="ad55e-129">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="ad55e-130">在列表中，单击 " **Office 365 组**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-130">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="ad55e-131">确保将**组织外部的成员访问组内容**和**允许组所有者将组织外部的人员添加到组**复选框均选中。</span><span class="sxs-lookup"><span data-stu-id="ad55e-131">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="ad55e-132">如果进行了更改，请单击 "**保存更改**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-132">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="ad55e-133">SharePoint 组织级别的共享设置</span><span class="sxs-lookup"><span data-stu-id="ad55e-133">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="ad55e-134">为使来宾能够访问 SharePoint 网站，SharePoint 组织级别的共享设置必须允许与来宾共享。</span><span class="sxs-lookup"><span data-stu-id="ad55e-134">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="ad55e-135">组织级别设置确定了哪些设置可用于单个网站。</span><span class="sxs-lookup"><span data-stu-id="ad55e-135">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="ad55e-136">网站设置不能比组织级别设置更具有更好的许可。</span><span class="sxs-lookup"><span data-stu-id="ad55e-136">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="ad55e-137">如果要允许未经身份验证的文件和文件夹共享，请选择 "**任何人**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-137">If you want to allow unauthenticated file and folder sharing, choose **Anyone**.</span></span> <span data-ttu-id="ad55e-138">如果要确保组织外部的所有人员都必须进行身份验证，请选择 "**新建" 和 "现有来宾**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-138">If you want to ensure that all people outside your organization have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="ad55e-139">选择组织中的任何网站将需要的 "最高" 设置。</span><span class="sxs-lookup"><span data-stu-id="ad55e-139">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 组织级别共享设置的屏幕截图](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="ad55e-141">设置 SharePoint 组织级别的共享设置</span><span class="sxs-lookup"><span data-stu-id="ad55e-141">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="ad55e-142">在 Microsoft 365 管理中心的左侧导航栏中，在 "**管理中心**" 下，单击 " **SharePoint**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-142">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="ad55e-143">在 SharePoint 管理中心的左侧导航栏中，单击“**共享**”。</span><span class="sxs-lookup"><span data-stu-id="ad55e-143">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="ad55e-144">确保将 SharePoint 的 "外部共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-144">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="ad55e-145">如果进行了任何更改，请单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="ad55e-145">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="ad55e-146">创建网站</span><span class="sxs-lookup"><span data-stu-id="ad55e-146">Create a site</span></span>

<span data-ttu-id="ad55e-147">下一步是创建您计划用于与来宾协作的网站。</span><span class="sxs-lookup"><span data-stu-id="ad55e-147">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="ad55e-148">创建网站</span><span class="sxs-lookup"><span data-stu-id="ad55e-148">To create a site</span></span>
1. <span data-ttu-id="ad55e-149">在 SharePoint 管理中心中的“**网站**”下，单击“**活动站点**”。</span><span class="sxs-lookup"><span data-stu-id="ad55e-149">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="ad55e-150">单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="ad55e-150">Click **Create**.</span></span>
3. <span data-ttu-id="ad55e-151">单击 "**团队网站**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-151">Click **Team site**.</span></span>
4. <span data-ttu-id="ad55e-152">键入网站名称并输入组所有者的名称（网站所有者）。</span><span class="sxs-lookup"><span data-stu-id="ad55e-152">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="ad55e-153">在 "**高级设置**" 下，选择是否希望它成为公用或专用网站。</span><span class="sxs-lookup"><span data-stu-id="ad55e-153">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="ad55e-154">单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-154">Click **Next**.</span></span>
7. <span data-ttu-id="ad55e-155">单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad55e-155">Click **Finish**.</span></span>

<span data-ttu-id="ad55e-156">我们将稍后邀请用户。</span><span class="sxs-lookup"><span data-stu-id="ad55e-156">We'll invite users later.</span></span> <span data-ttu-id="ad55e-157">接下来，请务必检查此网站的网站级共享设置。</span><span class="sxs-lookup"><span data-stu-id="ad55e-157">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="ad55e-158">SharePoint 网站级别共享设置</span><span class="sxs-lookup"><span data-stu-id="ad55e-158">SharePoint site level sharing settings</span></span>

<span data-ttu-id="ad55e-159">检查网站级别的共享设置以确保它们允许您对此网站所需的访问类型。</span><span class="sxs-lookup"><span data-stu-id="ad55e-159">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="ad55e-160">例如，如果将组织级别设置设置为 "**任何人**"，但希望所有来宾都对此网站进行身份验证，请确保将网站级别的共享设置设置为 "**新建" 和 "现有来宾**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-160">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="ad55e-161">请注意，不能将网站与未经身份验证的人员（**任何人**设置）共享，但可以对各个文件和文件夹进行共享。</span><span class="sxs-lookup"><span data-stu-id="ad55e-161">Note that the site cannot be shared with unauthenticated people (**Anyone** setting), but individual files and folders can.</span></span>

![SharePoint 网站外部共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="ad55e-163">设置网站级共享设置</span><span class="sxs-lookup"><span data-stu-id="ad55e-163">To set site-level sharing settings</span></span>
1. <span data-ttu-id="ad55e-164">在 SharePoint 管理中心的左侧导航栏中，展开 **“站点”**，然后单击 **“活动站点”**。</span><span class="sxs-lookup"><span data-stu-id="ad55e-164">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="ad55e-165">选择您刚刚创建的网站。</span><span class="sxs-lookup"><span data-stu-id="ad55e-165">Select the site that you just created.</span></span>
3. <span data-ttu-id="ad55e-166">在功能区中，单击 **“共享”**。</span><span class="sxs-lookup"><span data-stu-id="ad55e-166">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="ad55e-167">确保将 "共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-167">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="ad55e-168">如果进行了任何更改，请单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="ad55e-168">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="ad55e-169">邀请用户</span><span class="sxs-lookup"><span data-stu-id="ad55e-169">Invite users</span></span>

<span data-ttu-id="ad55e-170">现在已配置来宾共享设置，因此您可以开始向网站添加内部用户和来宾。</span><span class="sxs-lookup"><span data-stu-id="ad55e-170">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="ad55e-171">网站访问通过关联的 Office 365 组进行控制，因此我们将在此处添加用户。</span><span class="sxs-lookup"><span data-stu-id="ad55e-171">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="ad55e-172">向组邀请内部用户</span><span class="sxs-lookup"><span data-stu-id="ad55e-172">To invite internal users to a group</span></span>
1. <span data-ttu-id="ad55e-173">导航到要在其中添加用户的网站。</span><span class="sxs-lookup"><span data-stu-id="ad55e-173">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="ad55e-174">单击右上角的 "**成员**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-174">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="ad55e-175">单击“**添加成员**”。</span><span class="sxs-lookup"><span data-stu-id="ad55e-175">Click **Add members**.</span></span>
4. <span data-ttu-id="ad55e-176">键入要邀请到网站的用户的名称或电子邮件地址，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-176">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="ad55e-177">无法从网站添加来宾用户。</span><span class="sxs-lookup"><span data-stu-id="ad55e-177">Guest users can't be added from the site.</span></span> <span data-ttu-id="ad55e-178">您需要在 web 上使用 Outlook 添加它们。</span><span class="sxs-lookup"><span data-stu-id="ad55e-178">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="ad55e-179">将来宾邀请到组</span><span class="sxs-lookup"><span data-stu-id="ad55e-179">To invite guests to a group</span></span>
1. <span data-ttu-id="ad55e-180">在 web 上的 Outlook 中的 "**组**" 下，单击要在其中添加成员的组。</span><span class="sxs-lookup"><span data-stu-id="ad55e-180">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="ad55e-181">打开组联系人卡片，然后在 "**更多选项**（...）" 下，单击 "**添加成员**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-181">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="ad55e-182">键入要邀请的来宾的电子邮件地址，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="ad55e-182">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="ad55e-183">单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad55e-183">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad55e-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad55e-184">See Also</span></span>

[<span data-ttu-id="ad55e-185">有关与未经认证用户共享文件和文件夹的最佳做法</span><span class="sxs-lookup"><span data-stu-id="ad55e-185">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="ad55e-186">与来宾共享时限制文件意外曝光</span><span class="sxs-lookup"><span data-stu-id="ad55e-186">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

<span data-ttu-id="ad55e-187">[Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md)（创建安全的来宾共享环境）</span><span class="sxs-lookup"><span data-stu-id="ad55e-187">[Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md)</span></span>

[<span data-ttu-id="ad55e-188">创建托管有来宾的 B2B 外联网</span><span class="sxs-lookup"><span data-stu-id="ad55e-188">Create a B2B extranet with managed guests</span></span>](b2b-extranet.md)

