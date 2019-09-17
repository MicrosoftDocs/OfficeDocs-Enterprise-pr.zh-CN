---
title: 与团队中的来宾协作
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何与团队中的来宾进行协作。
ms.openlocfilehash: 9a169e33a9cbd8f079966443bd3d830aa79f4971
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992411"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="43d77-103">与团队中的来宾协作</span><span class="sxs-lookup"><span data-stu-id="43d77-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="43d77-104">如果需要在文档、任务和对话中与来宾进行协作，我们建议使用 Microsoft 团队。</span><span class="sxs-lookup"><span data-stu-id="43d77-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="43d77-105">团队提供了 Office 和 SharePoint 中提供的所有协作功能，并在统一的用户体验中提供了持续聊天和可自定义且可扩展的协作工具集。</span><span class="sxs-lookup"><span data-stu-id="43d77-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="43d77-106">在本文中，我们将完成必要的 Microsoft 365 配置步骤，以设置一个团队以与来宾协作。</span><span class="sxs-lookup"><span data-stu-id="43d77-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="43d77-107">Azure 组织关系设置</span><span class="sxs-lookup"><span data-stu-id="43d77-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="43d77-108">Microsoft 365 中的共享受 Azure Active Directory 中的组织关系设置的最高级别的管辖。</span><span class="sxs-lookup"><span data-stu-id="43d77-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="43d77-109">如果在 Azure AD 中禁用或限制来宾共享，这将替代您在 Microsoft 365 中配置的任何共享设置。</span><span class="sxs-lookup"><span data-stu-id="43d77-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="43d77-110">检查组织关系设置以确保不会阻止与来宾共享。</span><span class="sxs-lookup"><span data-stu-id="43d77-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory 组织关系设置页面的屏幕截图](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="43d77-112">设置组织关系设置</span><span class="sxs-lookup"><span data-stu-id="43d77-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="43d77-113">登录到 Microsoft Azure [https://portal.azure.com](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="43d77-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="43d77-114">在左侧导航中，单击 " **Azure Active Directory**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="43d77-115">在 "**概述**" 窗格中，单击 "**组织关系**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="43d77-116">在 "**组织关系**" 窗格中，单击 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="43d77-117">确保**来宾邀请者角色中的管理员和用户可以邀请**和**成员**都可以邀请都设置为 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="43d77-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="43d77-118">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="43d77-119">请注意 "**协作限制**" 部分中的设置。</span><span class="sxs-lookup"><span data-stu-id="43d77-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="43d77-120">确保不会阻止您要与之进行协作的来宾域。</span><span class="sxs-lookup"><span data-stu-id="43d77-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="43d77-121">团队来宾访问设置</span><span class="sxs-lookup"><span data-stu-id="43d77-121">Teams guest access settings</span></span>

<span data-ttu-id="43d77-122">团队具有用于来宾访问的主开/关开关，以及可用于控制来宾在团队中可执行的操作的各种设置。</span><span class="sxs-lookup"><span data-stu-id="43d77-122">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="43d77-123">主开关，**允许在团队中\*\*\*\*进行来宾**访问，以便来宾访问能够在团队中工作。</span><span class="sxs-lookup"><span data-stu-id="43d77-123">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="43d77-124">检查以确保在团队中启用了来宾访问，并根据你的业务需求对来宾设置进行任何调整。</span><span class="sxs-lookup"><span data-stu-id="43d77-124">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="43d77-125">请记住，这些设置会影响所有团队。</span><span class="sxs-lookup"><span data-stu-id="43d77-125">Keep in mind that these settings affect all teams.</span></span>

![团队来宾访问切换的屏幕截图](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="43d77-127">设置团队来宾访问设置</span><span class="sxs-lookup"><span data-stu-id="43d77-127">To set Teams guest access settings</span></span>

1. <span data-ttu-id="43d77-128">登录到 Microsoft 365 管理中心[https://admin.microsoft.com](https://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="43d77-128">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="43d77-129">在左侧导航中，单击 "**全部显示**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-129">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="43d77-130">在 "**管理中心**" 下，单击 "**团队**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-130">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="43d77-131">在团队管理中心的左侧导航栏中，展开 "**组织范围的设置**"，然后单击 "**来宾访问**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-131">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="43d77-132">确保将 "**允许在团队中进行来宾访问**" 设置为 **"开"**。</span><span class="sxs-lookup"><span data-stu-id="43d77-132">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="43d77-133">对其他来宾设置进行所需的更改，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-133">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="43d77-134">"团队来宾" 设置可能需要24小时才能在打开后变为活动状态。</span><span class="sxs-lookup"><span data-stu-id="43d77-134">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="43d77-135">Office 365 组来宾设置</span><span class="sxs-lookup"><span data-stu-id="43d77-135">Office 365 Groups guest settings</span></span>

<span data-ttu-id="43d77-136">团队使用适用于团队成员资格的 Office 365 组。</span><span class="sxs-lookup"><span data-stu-id="43d77-136">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="43d77-137">必须打开 Office 365 组来宾设置，才能使团队中的来宾访问能够正常工作。</span><span class="sxs-lookup"><span data-stu-id="43d77-137">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Microsoft 365 管理中心中的 Office 365 组来宾设置的屏幕截图](media/office-365-groups-guest-settings.png)

<span data-ttu-id="43d77-139">设置 Office 365 组来宾设置</span><span class="sxs-lookup"><span data-stu-id="43d77-139">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="43d77-140">在 Microsoft 365 管理中心的左侧导航栏中，展开 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-140">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="43d77-141">单击 "**服务" & 外接程序**。</span><span class="sxs-lookup"><span data-stu-id="43d77-141">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="43d77-142">在列表中，单击 " **Office 365 组**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-142">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="43d77-143">确保将**组织外部的成员访问组内容**和**允许组所有者将组织外部的人员添加到组**复选框均选中。</span><span class="sxs-lookup"><span data-stu-id="43d77-143">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="43d77-144">如果进行了更改，请单击 "**保存更改**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-144">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="43d77-145">SharePoint 组织级别的共享设置</span><span class="sxs-lookup"><span data-stu-id="43d77-145">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="43d77-146">为使来宾能够访问团队中的文件，SharePoint 组织级别的共享设置必须允许与来宾共享。</span><span class="sxs-lookup"><span data-stu-id="43d77-146">In order for guests to have access to files in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="43d77-147">组织级别设置决定了可用于单个网站的设置，包括与团队相关的网站。</span><span class="sxs-lookup"><span data-stu-id="43d77-147">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="43d77-148">网站设置不能比组织级别设置更具有更好的许可。</span><span class="sxs-lookup"><span data-stu-id="43d77-148">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="43d77-149">如果要允许与匿名用户共享文件和文件夹，请选择 "**任何人**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-149">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="43d77-150">如果要确保所有来宾都必须进行身份验证，请选择 "**新建" 和 "现有来宾**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-150">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="43d77-151">选择组织中的任何网站将需要的 "最高" 设置。</span><span class="sxs-lookup"><span data-stu-id="43d77-151">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 组织级共享设置的屏幕截图](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="43d77-153">设置 SharePoint 组织级别的共享设置</span><span class="sxs-lookup"><span data-stu-id="43d77-153">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="43d77-154">在 Microsoft 365 管理中心的左侧导航栏中，在 "**管理中心**" 下，单击 " **SharePoint**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-154">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="43d77-155">在 SharePoint 管理中心的左侧导航栏中，单击 "**共享**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-155">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="43d77-156">确保将 SharePoint 的 "外部共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-156">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="43d77-157">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-157">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="43d77-158">SharePoint 组织级别的默认链接设置</span><span class="sxs-lookup"><span data-stu-id="43d77-158">SharePoint organization level default link settings</span></span>

<span data-ttu-id="43d77-159">默认的文件和文件夹链接设置确定在用户共享文件或文件夹时，默认情况下向用户显示的链接选项。</span><span class="sxs-lookup"><span data-stu-id="43d77-159">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="43d77-160">如果需要，用户可以在共享之前将链接类型更改为其他选项之一。</span><span class="sxs-lookup"><span data-stu-id="43d77-160">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="43d77-161">请注意，此设置会影响组织中的所有团队和 SharePoint 网站。</span><span class="sxs-lookup"><span data-stu-id="43d77-161">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="43d77-162">选择当用户共享文件和文件夹时默认选择的链接类型：</span><span class="sxs-lookup"><span data-stu-id="43d77-162">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="43d77-163">**任何具有链接的人**-如果您希望与匿名用户共享大量文件和文件夹，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="43d77-163">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="43d77-164">如果您希望允许*任何人*链接，但担心意外匿名共享，请将其他选项之一作为默认值。</span><span class="sxs-lookup"><span data-stu-id="43d77-164">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="43d77-165">仅当您已启用**任何**共享时，此链接类型才可用。</span><span class="sxs-lookup"><span data-stu-id="43d77-165">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="43d77-166">**仅限组织中的人员**-如果您希望大多数文件和文件夹共享与组织内部的人员共享，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="43d77-166">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="43d77-167">**特定人员**-如果您希望对来宾执行大量文件和文件夹共享，请考虑此选项。</span><span class="sxs-lookup"><span data-stu-id="43d77-167">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="43d77-168">此类型的链接可与来宾配合使用，并要求用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="43d77-168">This type of link works with guests and requires them to authenticate.</span></span>
 
![SharePoint 组织级别的文件和文件夹共享设置的屏幕截图](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="43d77-170">设置 SharePoint 组织级别的默认链接设置</span><span class="sxs-lookup"><span data-stu-id="43d77-170">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="43d77-171">导航到 SharePoint 管理中心中的 "共享" 页面。</span><span class="sxs-lookup"><span data-stu-id="43d77-171">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="43d77-172">在 "**文件和文件夹链接**" 下，选择要使用的默认共享链接。</span><span class="sxs-lookup"><span data-stu-id="43d77-172">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="43d77-173">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-173">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="43d77-174">创建团队</span><span class="sxs-lookup"><span data-stu-id="43d77-174">Create a team</span></span>

<span data-ttu-id="43d77-175">下一步是创建计划用于与来宾协作的团队。</span><span class="sxs-lookup"><span data-stu-id="43d77-175">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="43d77-176">创建团队</span><span class="sxs-lookup"><span data-stu-id="43d77-176">To create a team</span></span>
1. <span data-ttu-id="43d77-177">在团队中的 "**团队**" 选项卡上，单击 "加入" 或 "在左窗格底部**创建团队**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-177">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="43d77-178">单击 "**创建团队**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-178">Click **Create a team**.</span></span>
3. <span data-ttu-id="43d77-179">单击 "**从头开始构建团队**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-179">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="43d77-180">选择 "**专用**" 或 "**公共**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-180">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="43d77-181">键入团队的名称和说明，然后单击 "**创建**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-181">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="43d77-182">单击 "**跳过**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-182">Click **Skip**.</span></span>

<span data-ttu-id="43d77-183">我们将稍后邀请用户。</span><span class="sxs-lookup"><span data-stu-id="43d77-183">We'll invite users later.</span></span> <span data-ttu-id="43d77-184">接下来，请务必检查与团队关联的 SharePoint 网站的网站级别共享设置。</span><span class="sxs-lookup"><span data-stu-id="43d77-184">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="43d77-185">SharePoint 网站级别共享设置</span><span class="sxs-lookup"><span data-stu-id="43d77-185">SharePoint site level sharing settings</span></span>

<span data-ttu-id="43d77-186">检查网站级别的共享设置以确保它们允许此团队的访问类型。</span><span class="sxs-lookup"><span data-stu-id="43d77-186">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="43d77-187">例如，如果将组织级别设置设置为 "**任何人**"，但希望所有来宾都对此团队进行身份验证，请确保将网站级别的共享设置设置为 "**新建" 和 "现有来宾**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-187">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![SharePoint 网站外部共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="43d77-189">设置网站级共享设置</span><span class="sxs-lookup"><span data-stu-id="43d77-189">To set site-level sharing settings</span></span>
1. <span data-ttu-id="43d77-190">在 SharePoint 管理中心中，在左侧导航栏中，展开 "**网站**"，然后单击 "**活动网站**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-190">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="43d77-191">为您刚创建的团队选择网站。</span><span class="sxs-lookup"><span data-stu-id="43d77-191">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="43d77-192">在功能区中，单击 "**共享**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-192">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="43d77-193">确保将 "共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-193">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="43d77-194">如果进行了更改，请单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-194">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="43d77-195">邀请用户</span><span class="sxs-lookup"><span data-stu-id="43d77-195">Invite users</span></span>

<span data-ttu-id="43d77-196">现在已配置来宾共享设置，因此您可以开始向团队添加内部用户和来宾。</span><span class="sxs-lookup"><span data-stu-id="43d77-196">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="43d77-197">向团队邀请内部用户</span><span class="sxs-lookup"><span data-stu-id="43d77-197">To invite internal users to a team</span></span>
1. <span data-ttu-id="43d77-198">在团队中，单击 "**更多选项**" （**\*\***），然后单击 "**添加成员**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-198">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="43d77-199">键入要邀请的人员的姓名。</span><span class="sxs-lookup"><span data-stu-id="43d77-199">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="43d77-200">单击“**添加**”，然后单击“**关闭**”。</span><span class="sxs-lookup"><span data-stu-id="43d77-200">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="43d77-201">向团队邀请来宾</span><span class="sxs-lookup"><span data-stu-id="43d77-201">To invite guests to a team</span></span>
1. <span data-ttu-id="43d77-202">在团队中，单击 "**更多选项**" （**\*\***），然后单击 "**添加成员**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-202">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="43d77-203">键入要邀请的来宾的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="43d77-203">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="43d77-204">单击 "**编辑来宾信息**"。</span><span class="sxs-lookup"><span data-stu-id="43d77-204">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="43d77-205">键入来宾的全名并单击复选标记。</span><span class="sxs-lookup"><span data-stu-id="43d77-205">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="43d77-206">单击“**添加**”，然后单击“**关闭**”。</span><span class="sxs-lookup"><span data-stu-id="43d77-206">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="43d77-207">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43d77-207">See Also</span></span>

