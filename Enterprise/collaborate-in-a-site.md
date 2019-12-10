---
title: 在网站中与来宾协作
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何在 SharePoint 网站中与来宾进行协作。
ms.openlocfilehash: 21717ce0c8e9e51eaf090a449d35a281722f9600
ms.sourcegitcommit: b5992f367ccae97a8ea538738fe36d3d703cd6e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "39919255"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="5e55a-103">在网站中与来宾协作</span><span class="sxs-lookup"><span data-stu-id="5e55a-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="5e55a-104">如果需要在文档、数据和列表之间与来宾进行协作，则可以使用 SharePoint 网站。</span><span class="sxs-lookup"><span data-stu-id="5e55a-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="5e55a-105">新式 SharePoint 网站连接到可管理网站成员身份的 Office 365 组，并提供其他协作工具（如共享邮箱和日历）。</span><span class="sxs-lookup"><span data-stu-id="5e55a-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="5e55a-106">在本文中，我们将逐步完成为与来宾协作设置 SharePoint 网站所必需的 Microsoft 365 配置步骤。</span><span class="sxs-lookup"><span data-stu-id="5e55a-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="5e55a-107">视频演示</span><span class="sxs-lookup"><span data-stu-id="5e55a-107">Video demonstration</span></span>

<span data-ttu-id="5e55a-108">该视频显示了本文档中描述的配置步骤。</span><span class="sxs-lookup"><span data-stu-id="5e55a-108">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="5e55a-109">Azure 组织关系设置</span><span class="sxs-lookup"><span data-stu-id="5e55a-109">Azure Organizational relationships settings</span></span>

<span data-ttu-id="5e55a-110">Microsoft 365 中的共享受 Azure Active Directory 中的组织关系设置的最高级别的管辖。</span><span class="sxs-lookup"><span data-stu-id="5e55a-110">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="5e55a-111">如果在 Azure AD 中禁用或限制来宾共享，这将替代您在 Microsoft 365 中配置的任何共享设置。</span><span class="sxs-lookup"><span data-stu-id="5e55a-111">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="5e55a-112">检查组织关系设置以确保不会阻止与来宾共享。</span><span class="sxs-lookup"><span data-stu-id="5e55a-112">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory 组织关系设置页面的屏幕截图](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="5e55a-114">设置组织关系设置</span><span class="sxs-lookup"><span data-stu-id="5e55a-114">To set organizational relationship settings</span></span>

1. <span data-ttu-id="5e55a-115">登录到 Microsoft Azure [https://portal.azure.com](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="5e55a-115">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="5e55a-116">在左侧导航中，单击 " **Azure Active Directory**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-116">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="5e55a-117">在 "**概述**" 窗格中，单击 "**组织关系**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-117">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="5e55a-118">在 "**组织关系**" 窗格中，单击 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-118">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="5e55a-119">确保**来宾邀请者角色中的管理员和用户可以邀请**和**成员**都可以邀请都设置为 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="5e55a-119">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="5e55a-120">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-120">If you made changes, click **Save**.</span></span>

<span data-ttu-id="5e55a-121">请注意 "**协作限制**" 部分中的设置。</span><span class="sxs-lookup"><span data-stu-id="5e55a-121">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="5e55a-122">确保不会阻止您要与之进行协作的来宾域。</span><span class="sxs-lookup"><span data-stu-id="5e55a-122">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="5e55a-123">Office 365 组来宾设置</span><span class="sxs-lookup"><span data-stu-id="5e55a-123">Office 365 Groups guest settings</span></span>

<span data-ttu-id="5e55a-124">新式 SharePoint 网站使用 Office 365 组来控制网站访问。</span><span class="sxs-lookup"><span data-stu-id="5e55a-124">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="5e55a-125">必须打开 Office 365 组来宾设置，才能使 SharePoint 网站中的来宾访问能够正常工作。</span><span class="sxs-lookup"><span data-stu-id="5e55a-125">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Microsoft 365 管理中心中的 Office 365 组来宾设置的屏幕截图](media/office-365-groups-guest-settings.png)

<span data-ttu-id="5e55a-127">设置 Office 365 组来宾设置</span><span class="sxs-lookup"><span data-stu-id="5e55a-127">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="5e55a-128">在 Microsoft 365 管理中心的左侧导航栏中，展开 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-128">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="5e55a-129">单击 "**服务" & 外接程序**。</span><span class="sxs-lookup"><span data-stu-id="5e55a-129">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="5e55a-130">在列表中，单击 " **Office 365 组**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-130">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="5e55a-131">确保将**组织外部的成员访问组内容**和**允许组所有者将组织外部的人员添加到组**复选框均选中。</span><span class="sxs-lookup"><span data-stu-id="5e55a-131">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="5e55a-132">如果进行了更改，请单击 "**保存更改**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-132">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="5e55a-133">SharePoint 组织级别的共享设置</span><span class="sxs-lookup"><span data-stu-id="5e55a-133">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="5e55a-134">为使来宾能够访问 SharePoint 网站，SharePoint 组织级别的共享设置必须允许与来宾共享。</span><span class="sxs-lookup"><span data-stu-id="5e55a-134">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="5e55a-135">组织级别设置确定了哪些设置可用于单个网站。</span><span class="sxs-lookup"><span data-stu-id="5e55a-135">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="5e55a-136">网站设置不能比组织级别设置更具有更好的许可。</span><span class="sxs-lookup"><span data-stu-id="5e55a-136">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="5e55a-137">如果要允许未经身份验证的文件和文件夹共享，请选择 "**任何人**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-137">If you want to allow unauthenticated file and folder sharing, choose **Anyone**.</span></span> <span data-ttu-id="5e55a-138">如果要确保组织外部的所有人员都必须进行身份验证，请选择 "**新建" 和 "现有来宾**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-138">If you want to ensure that all people outside your organization have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="5e55a-139">选择组织中的任何网站将需要的 "最高" 设置。</span><span class="sxs-lookup"><span data-stu-id="5e55a-139">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 组织级别共享设置的屏幕截图](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="5e55a-141">设置 SharePoint 组织级别的共享设置</span><span class="sxs-lookup"><span data-stu-id="5e55a-141">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="5e55a-142">在 Microsoft 365 管理中心的左侧导航栏中，在 "**管理中心**" 下，单击 " **SharePoint**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-142">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="5e55a-143">在 SharePoint 管理中心的左侧导航栏中，单击“**共享**”。</span><span class="sxs-lookup"><span data-stu-id="5e55a-143">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="5e55a-144">确保将 SharePoint 的 "外部共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-144">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="5e55a-145">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-145">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="5e55a-146">创建网站</span><span class="sxs-lookup"><span data-stu-id="5e55a-146">Create a site</span></span>

<span data-ttu-id="5e55a-147">下一步是创建您计划用于与来宾协作的网站。</span><span class="sxs-lookup"><span data-stu-id="5e55a-147">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="5e55a-148">创建网站</span><span class="sxs-lookup"><span data-stu-id="5e55a-148">To create a site</span></span>
1. <span data-ttu-id="5e55a-149">在 SharePoint 管理中心中的 "**网站**" 下，单击 "**活动网站**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-149">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="5e55a-150">单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="5e55a-150">Click **Create**.</span></span>
3. <span data-ttu-id="5e55a-151">单击 "**团队网站**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-151">Click **Team site**.</span></span>
4. <span data-ttu-id="5e55a-152">键入网站名称并输入组所有者的名称（网站所有者）。</span><span class="sxs-lookup"><span data-stu-id="5e55a-152">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="5e55a-153">在 "**高级设置**" 下，选择是否希望它成为公用或专用网站。</span><span class="sxs-lookup"><span data-stu-id="5e55a-153">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="5e55a-154">单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-154">Click **Next**.</span></span>
7. <span data-ttu-id="5e55a-155">单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5e55a-155">Click **Finish**.</span></span>

<span data-ttu-id="5e55a-156">我们将稍后邀请用户。</span><span class="sxs-lookup"><span data-stu-id="5e55a-156">We'll invite users later.</span></span> <span data-ttu-id="5e55a-157">接下来，请务必检查此网站的网站级共享设置。</span><span class="sxs-lookup"><span data-stu-id="5e55a-157">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="5e55a-158">SharePoint 网站级别共享设置</span><span class="sxs-lookup"><span data-stu-id="5e55a-158">SharePoint site level sharing settings</span></span>

<span data-ttu-id="5e55a-159">检查网站级别的共享设置以确保它们允许您对此网站所需的访问类型。</span><span class="sxs-lookup"><span data-stu-id="5e55a-159">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="5e55a-160">例如，如果将组织级别设置设置为 "**任何人**"，但希望所有来宾都对此网站进行身份验证，请确保将网站级别的共享设置设置为 "**新建" 和 "现有来宾**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-160">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="5e55a-161">请注意，不能将网站与未经身份验证的人员（**任何人**设置）共享，但可以对各个文件和文件夹进行共享。</span><span class="sxs-lookup"><span data-stu-id="5e55a-161">Note that the site cannot be shared with unauthenticated people (**Anyone** setting), but individual files and folders can.</span></span>

![SharePoint 网站外部共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="5e55a-163">设置网站级共享设置</span><span class="sxs-lookup"><span data-stu-id="5e55a-163">To set site-level sharing settings</span></span>
1. <span data-ttu-id="5e55a-164">在 SharePoint 管理中心中，在左侧导航栏中，展开 "**网站**"，然后单击 "**活动网站**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-164">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="5e55a-165">选择您刚刚创建的网站。</span><span class="sxs-lookup"><span data-stu-id="5e55a-165">Select the site that you just created.</span></span>
3. <span data-ttu-id="5e55a-166">在功能区中，单击 "**共享**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-166">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="5e55a-167">确保将 "共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-167">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="5e55a-168">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-168">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="5e55a-169">邀请用户</span><span class="sxs-lookup"><span data-stu-id="5e55a-169">Invite users</span></span>

<span data-ttu-id="5e55a-170">现在已配置来宾共享设置，因此您可以开始向网站添加内部用户和来宾。</span><span class="sxs-lookup"><span data-stu-id="5e55a-170">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="5e55a-171">网站访问通过关联的 Office 365 组进行控制，因此我们将在此处添加用户。</span><span class="sxs-lookup"><span data-stu-id="5e55a-171">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="5e55a-172">向组邀请内部用户</span><span class="sxs-lookup"><span data-stu-id="5e55a-172">To invite internal users to a group</span></span>
1. <span data-ttu-id="5e55a-173">导航到要在其中添加用户的网站。</span><span class="sxs-lookup"><span data-stu-id="5e55a-173">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="5e55a-174">单击右上角的 "**成员**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-174">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="5e55a-175">单击“**添加成员**”。</span><span class="sxs-lookup"><span data-stu-id="5e55a-175">Click **Add members**.</span></span>
4. <span data-ttu-id="5e55a-176">键入要邀请到网站的用户的名称或电子邮件地址，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-176">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="5e55a-177">无法从网站添加来宾用户。</span><span class="sxs-lookup"><span data-stu-id="5e55a-177">Guest users can't be added from the site.</span></span> <span data-ttu-id="5e55a-178">您需要在 web 上使用 Outlook 添加它们。</span><span class="sxs-lookup"><span data-stu-id="5e55a-178">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="5e55a-179">将来宾邀请到网站</span><span class="sxs-lookup"><span data-stu-id="5e55a-179">To invite guests to a site</span></span>
1. <span data-ttu-id="5e55a-180">在 web 上的 Outlook 中的 "**组**" 下，单击要在其中添加成员的组。</span><span class="sxs-lookup"><span data-stu-id="5e55a-180">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="5e55a-181">打开组联系人卡片，然后在 "**更多选项**（...）" 下，单击 "**添加成员**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-181">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="5e55a-182">键入要邀请的来宾的电子邮件地址，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="5e55a-182">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="5e55a-183">单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5e55a-183">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e55a-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e55a-184">See Also</span></span>

[<span data-ttu-id="5e55a-185">有关与未经认证用户共享文件和文件夹的最佳做法</span><span class="sxs-lookup"><span data-stu-id="5e55a-185">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="5e55a-186">与来宾共享时限制文件意外曝光</span><span class="sxs-lookup"><span data-stu-id="5e55a-186">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

<span data-ttu-id="5e55a-187">[创建安全来宾共享环境](create-a-secure-guest-sharing-environment.md)）</span><span class="sxs-lookup"><span data-stu-id="5e55a-187">[Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md))</span></span>

