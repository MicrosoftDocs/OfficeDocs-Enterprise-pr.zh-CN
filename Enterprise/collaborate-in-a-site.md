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
ms.openlocfilehash: 23f55e22d4c85dcd168c403f50b35f574be9ac07
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992381"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="f3803-103">在网站中与来宾协作</span><span class="sxs-lookup"><span data-stu-id="f3803-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="f3803-104">如果需要在文档、数据和列表之间与来宾进行协作，则可以使用 SharePoint 网站。</span><span class="sxs-lookup"><span data-stu-id="f3803-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="f3803-105">新式 SharePoint 网站连接到可管理网站成员身份的 Office 365 组，并提供其他协作工具（如共享邮箱和日历）。</span><span class="sxs-lookup"><span data-stu-id="f3803-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="f3803-106">在本文中，我们将逐步完成为与来宾协作设置 SharePoint 网站所必需的 Microsoft 365 配置步骤。</span><span class="sxs-lookup"><span data-stu-id="f3803-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="f3803-107">Azure 组织关系设置</span><span class="sxs-lookup"><span data-stu-id="f3803-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="f3803-108">Microsoft 365 中的共享受 Azure Active Directory 中的组织关系设置的最高级别的管辖。</span><span class="sxs-lookup"><span data-stu-id="f3803-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="f3803-109">如果在 Azure AD 中禁用或限制来宾共享，这将替代您在 Microsoft 365 中配置的任何共享设置。</span><span class="sxs-lookup"><span data-stu-id="f3803-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="f3803-110">检查组织关系设置以确保不会阻止与来宾共享。</span><span class="sxs-lookup"><span data-stu-id="f3803-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory 组织关系设置页面的屏幕截图](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="f3803-112">设置组织关系设置</span><span class="sxs-lookup"><span data-stu-id="f3803-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="f3803-113">登录到 Microsoft Azure [https://portal.azure.com](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="f3803-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="f3803-114">在左侧导航中，单击 " **Azure Active Directory**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="f3803-115">在 "**概述**" 窗格中，单击 "**组织关系**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="f3803-116">在 "**组织关系**" 窗格中，单击 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="f3803-117">确保**来宾邀请者角色中的管理员和用户可以邀请**和**成员**都可以邀请都设置为 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="f3803-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="f3803-118">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="f3803-119">请注意 "**协作限制**" 部分中的设置。</span><span class="sxs-lookup"><span data-stu-id="f3803-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="f3803-120">确保不会阻止您要与之进行协作的来宾域。</span><span class="sxs-lookup"><span data-stu-id="f3803-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="f3803-121">Office 365 组来宾设置</span><span class="sxs-lookup"><span data-stu-id="f3803-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="f3803-122">新式 SharePoint 网站使用 Office 365 组来控制网站访问。</span><span class="sxs-lookup"><span data-stu-id="f3803-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="f3803-123">必须打开 Office 365 组来宾设置，才能使 SharePoint 网站中的来宾访问能够正常工作。</span><span class="sxs-lookup"><span data-stu-id="f3803-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Microsoft 365 管理中心中的 Office 365 组来宾设置的屏幕截图](media/office-365-groups-guest-settings.png)

<span data-ttu-id="f3803-125">设置 Office 365 组来宾设置</span><span class="sxs-lookup"><span data-stu-id="f3803-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="f3803-126">在 Microsoft 365 管理中心的左侧导航栏中，展开 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="f3803-127">单击 "**服务" & 外接程序**。</span><span class="sxs-lookup"><span data-stu-id="f3803-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="f3803-128">在列表中，单击 " **Office 365 组**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="f3803-129">确保将**组织外部的成员访问组内容**和**允许组所有者将组织外部的人员添加到组**复选框均选中。</span><span class="sxs-lookup"><span data-stu-id="f3803-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="f3803-130">如果进行了更改，请单击 "**保存更改**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="f3803-131">SharePoint 组织级别的共享设置</span><span class="sxs-lookup"><span data-stu-id="f3803-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="f3803-132">为使来宾能够访问 SharePoint 网站，SharePoint 组织级别的共享设置必须允许与来宾共享。</span><span class="sxs-lookup"><span data-stu-id="f3803-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="f3803-133">组织级别设置确定了哪些设置可用于单个网站。</span><span class="sxs-lookup"><span data-stu-id="f3803-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="f3803-134">网站设置不能比组织级别设置更具有更好的许可。</span><span class="sxs-lookup"><span data-stu-id="f3803-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="f3803-135">如果要允许与匿名用户共享文件和文件夹，请选择 "**任何人**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="f3803-136">如果要确保所有来宾都必须进行身份验证，请选择 "**新建" 和 "现有来宾**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="f3803-137">选择组织中的任何网站将需要的 "最高" 设置。</span><span class="sxs-lookup"><span data-stu-id="f3803-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 组织级共享设置的屏幕截图](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="f3803-139">设置 SharePoint 组织级别的共享设置</span><span class="sxs-lookup"><span data-stu-id="f3803-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="f3803-140">在 Microsoft 365 管理中心的左侧导航栏中，在 "**管理中心**" 下，单击 " **SharePoint**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="f3803-141">在 SharePoint 管理中心的左侧导航栏中，单击 "**共享**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="f3803-142">确保将 SharePoint 的 "外部共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="f3803-143">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-143">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="f3803-144">SharePoint 组织级别的默认链接设置</span><span class="sxs-lookup"><span data-stu-id="f3803-144">SharePoint organization level default link settings</span></span>

<span data-ttu-id="f3803-145">默认的文件和文件夹链接设置确定在用户共享文件或文件夹时，默认情况下向用户显示的链接选项。</span><span class="sxs-lookup"><span data-stu-id="f3803-145">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="f3803-146">如果需要，用户可以在共享之前将链接类型更改为其他选项之一。</span><span class="sxs-lookup"><span data-stu-id="f3803-146">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="f3803-147">请注意，此设置会影响组织中的所有团队和 SharePoint 网站。</span><span class="sxs-lookup"><span data-stu-id="f3803-147">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="f3803-148">选择当用户共享文件和文件夹时默认选择的链接类型：</span><span class="sxs-lookup"><span data-stu-id="f3803-148">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="f3803-149">**任何具有链接的人**-如果您希望与匿名用户共享大量文件和文件夹，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f3803-149">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="f3803-150">如果您希望允许*任何人*链接，但担心意外匿名共享，请将其他选项之一作为默认值。</span><span class="sxs-lookup"><span data-stu-id="f3803-150">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="f3803-151">仅当您已启用**任何**共享时，此链接类型才可用。</span><span class="sxs-lookup"><span data-stu-id="f3803-151">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="f3803-152">**仅限组织中的人员**-如果您希望大多数文件和文件夹共享与组织内部的人员共享，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f3803-152">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="f3803-153">**特定人员**-如果您希望对来宾执行大量文件和文件夹共享，请考虑此选项。</span><span class="sxs-lookup"><span data-stu-id="f3803-153">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="f3803-154">此类型的链接可与来宾配合使用，并要求用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f3803-154">This type of link works with guests and requires them to authenticate.</span></span>
 
![SharePoint 组织级别的文件和文件夹共享设置的屏幕截图](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="f3803-156">设置 SharePoint 组织级别的默认链接设置</span><span class="sxs-lookup"><span data-stu-id="f3803-156">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="f3803-157">导航到 SharePoint 管理中心中的 "共享" 页面。</span><span class="sxs-lookup"><span data-stu-id="f3803-157">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="f3803-158">在 "**文件和文件夹链接**" 下，选择要使用的默认共享链接。</span><span class="sxs-lookup"><span data-stu-id="f3803-158">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="f3803-159">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-159">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="f3803-160">创建网站</span><span class="sxs-lookup"><span data-stu-id="f3803-160">Create a site</span></span>

<span data-ttu-id="f3803-161">下一步是创建您计划用于与来宾协作的网站。</span><span class="sxs-lookup"><span data-stu-id="f3803-161">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="f3803-162">创建网站</span><span class="sxs-lookup"><span data-stu-id="f3803-162">To create a site</span></span>
1. <span data-ttu-id="f3803-163">在 SharePoint 管理中心中的 "**网站**" 下，单击 "**活动网站**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-163">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="f3803-164">单击“**创建**”。 </span><span class="sxs-lookup"><span data-stu-id="f3803-164">Click **Create**.</span></span>
3. <span data-ttu-id="f3803-165">单击 "**团队网站**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-165">Click **Team site**.</span></span>
4. <span data-ttu-id="f3803-166">键入网站名称并输入组所有者的名称（网站所有者）。</span><span class="sxs-lookup"><span data-stu-id="f3803-166">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="f3803-167">在 "**高级设置**" 下，选择是否希望它成为公用或专用网站。</span><span class="sxs-lookup"><span data-stu-id="f3803-167">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="f3803-168">单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="f3803-168">Click **Next**.</span></span>
7. <span data-ttu-id="f3803-169">单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f3803-169">Click **Finish**.</span></span>

<span data-ttu-id="f3803-170">我们将稍后邀请用户。</span><span class="sxs-lookup"><span data-stu-id="f3803-170">We'll invite users later.</span></span> <span data-ttu-id="f3803-171">接下来，请务必检查此网站的网站级共享设置。</span><span class="sxs-lookup"><span data-stu-id="f3803-171">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="f3803-172">SharePoint 网站级别共享设置</span><span class="sxs-lookup"><span data-stu-id="f3803-172">SharePoint site level sharing settings</span></span>

<span data-ttu-id="f3803-173">检查网站级别的共享设置以确保它们允许您对此网站所需的访问类型。</span><span class="sxs-lookup"><span data-stu-id="f3803-173">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="f3803-174">例如，如果将组织级别设置设置为 "**任何人**"，但希望所有来宾都对此网站进行身份验证，请确保将网站级别的共享设置设置为 "**新建" 和 "现有来宾**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-174">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="f3803-175">请注意，不能与匿名用户（**任何人**设置）共享网站，但可以对各个文件和文件夹进行共享。</span><span class="sxs-lookup"><span data-stu-id="f3803-175">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![SharePoint 网站外部共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="f3803-177">设置网站级共享设置</span><span class="sxs-lookup"><span data-stu-id="f3803-177">To set site-level sharing settings</span></span>
1. <span data-ttu-id="f3803-178">在 SharePoint 管理中心中，在左侧导航栏中，展开 "**网站**"，然后单击 "**活动网站**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-178">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="f3803-179">选择您刚刚创建的网站。</span><span class="sxs-lookup"><span data-stu-id="f3803-179">Select the site that you just created.</span></span>
3. <span data-ttu-id="f3803-180">在功能区中，单击 "**共享**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-180">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="f3803-181">确保将 "共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-181">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="f3803-182">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-182">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="f3803-183">邀请用户</span><span class="sxs-lookup"><span data-stu-id="f3803-183">Invite users</span></span>

<span data-ttu-id="f3803-184">现在已配置来宾共享设置，因此您可以开始向网站添加内部用户和来宾。</span><span class="sxs-lookup"><span data-stu-id="f3803-184">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="f3803-185">网站访问通过关联的 Office 365 组进行控制，因此我们将在此处添加用户。</span><span class="sxs-lookup"><span data-stu-id="f3803-185">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="f3803-186">向组邀请内部用户</span><span class="sxs-lookup"><span data-stu-id="f3803-186">To invite internal users to a group</span></span>
1. <span data-ttu-id="f3803-187">导航到要在其中添加用户的网站。</span><span class="sxs-lookup"><span data-stu-id="f3803-187">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="f3803-188">单击右上角的 "**成员**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-188">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="f3803-189">单击“**添加成员**”。</span><span class="sxs-lookup"><span data-stu-id="f3803-189">Click **Add members**.</span></span>
4. <span data-ttu-id="f3803-190">键入要邀请到网站的用户的名称或电子邮件地址，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-190">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="f3803-191">无法从网站添加来宾用户。</span><span class="sxs-lookup"><span data-stu-id="f3803-191">Guest users can't be added from the site.</span></span> <span data-ttu-id="f3803-192">您需要在 web 上使用 Outlook 添加它们。</span><span class="sxs-lookup"><span data-stu-id="f3803-192">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="f3803-193">将来宾邀请到网站</span><span class="sxs-lookup"><span data-stu-id="f3803-193">To invite guests to a site</span></span>
1. <span data-ttu-id="f3803-194">在 web 上的 Outlook 中的 "**组**" 下，单击要在其中添加成员的组。</span><span class="sxs-lookup"><span data-stu-id="f3803-194">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="f3803-195">打开组联系人卡片，然后在 "**更多选项**（...）" 下，单击 "**添加成员**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-195">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="f3803-196">键入要邀请的来宾的电子邮件地址，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="f3803-196">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="f3803-197">单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f3803-197">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3803-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3803-198">See Also</span></span>
