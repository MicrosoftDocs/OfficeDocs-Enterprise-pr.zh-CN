---
title: 限制 Microsoft 365 中的共享
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
search.appverid:
- SPO160
- MET150
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: 了解在 Microsoft 365 中用于限制或禁用共享的选项。
ms.openlocfilehash: 8e0488aae1d30d33b9046d4372707eb8d8635860
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844913"
---
# <a name="limit-sharing-in-microsoft-365"></a><span data-ttu-id="a7fd6-103">限制 Microsoft 365 中的共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-103">Limit sharing in Microsoft 365</span></span>

<span data-ttu-id="a7fd6-104">虽然无法完全禁用内部共享，也无法删除网站中的“共享”按钮，但可通过多种方式来限制 Microsoft 365 中的共享，以满足组织的需求。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-104">While you can't disable internal sharing entirely or remove the Share button from sites, there are a variety of ways that you can limit sharing in Microsoft 365 to meet the needs of your organization.</span></span>

<span data-ttu-id="a7fd6-105">下表列出了共享文件的方法。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-105">The methods of sharing files are listed in the table below.</span></span> <span data-ttu-id="a7fd6-106">有关详细信息，请单击“**共享方法**”列中的链接。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-106">Click the link in the **Sharing method** column for detailed information.</span></span>

|<span data-ttu-id="a7fd6-107">共享方法</span><span class="sxs-lookup"><span data-stu-id="a7fd6-107">Sharing method</span></span>|<span data-ttu-id="a7fd6-108">说明</span><span class="sxs-lookup"><span data-stu-id="a7fd6-108">Description</span></span>|<span data-ttu-id="a7fd6-109">限制选项</span><span class="sxs-lookup"><span data-stu-id="a7fd6-109">Limiting options</span></span>|
|:-------------|:----------|:-------------|
|[<span data-ttu-id="a7fd6-110">Office 365 组或团队</span><span class="sxs-lookup"><span data-stu-id="a7fd6-110">Office 365 group or team</span></span>](#office-365-group-or-team)|<span data-ttu-id="a7fd6-111">被授予加入 Microsoft Teams 团队或 Office 365 组的权限的用户可以编辑关联的 SharePoint 网站中的文件。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-111">People granted access to a Microsoft Teams team or Office 365 group have edit access to files in the associated SharePoint site.</span></span>|<span data-ttu-id="a7fd6-112">如果组或团队是专用的，则用于加入团队的共享邀请将会转到所有者那里以供其审批。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-112">If the group or team is private, sharing invitations to join the team go to the owner for approval.</span></span> <span data-ttu-id="a7fd6-113">管理员可通过禁用来宾访问来阻止组织外部人员的访问。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-113">Admins can disable guest access to prevent access by people from outside the organization.</span></span>|
|[<span data-ttu-id="a7fd6-114">SharePoint 网站</span><span class="sxs-lookup"><span data-stu-id="a7fd6-114">SharePoint site</span></span>](#sharepoint-site)|<span data-ttu-id="a7fd6-115">可向用户授予对 SharePoint 网站的“所有者”、“成员”或“访问者”访问权限，他们将拥有对网站中文件的相应访问权限级别。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-115">People can be granted Owner, Member, or Visitor access to a SharePoint site and will have that level of access to files in the site.</span></span>|<span data-ttu-id="a7fd6-116">可限制网站权限，以便只有网站所有者可以共享网站。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-116">Site permissions can be restricted so that only site owners can share the site.</span></span>|
|[<span data-ttu-id="a7fd6-117">与特定人员共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-117">Sharing with specific people</span></span>](#sharing-with-specific-people)|<span data-ttu-id="a7fd6-118">网站成员和拥有编辑权限的人员可以提供对文件和文件夹的直接权限，或通过使用*特定人员*链接进行共享。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-118">Site members and people with edit permissions can give direct permissions to files and folders or share them by using *Specific people* links.</span></span>|<span data-ttu-id="a7fd6-119">可限制网站权限，以便只有网站所有者可以共享文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-119">Site permissions can be restricted so that only site owners can share files and folders.</span></span> <span data-ttu-id="a7fd6-120">在这种情况下，网站成员提供的直接访问和*特定人员*链接共享将会转到网站所有者那里以供其审批。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-120">In this case, direct access and *Specific people* link sharing by site members goes to site owner for approval.</span></span>|
|[<span data-ttu-id="a7fd6-121">SharePoint 来宾共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-121">SharePoint guest sharing</span></span>](#sharepoint-guest-sharing)|<span data-ttu-id="a7fd6-122">SharePoint 网站所有者和成员可与组织外部的人员共享文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-122">SharePoint site owners and members can share files and folders with people outside the organization.</span></span>|<span data-ttu-id="a7fd6-123">可针对整个组织或单个网站禁用来宾共享。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-123">Guest sharing can be disabled for the entire organization or for individual sites.</span></span>|
|[<span data-ttu-id="a7fd6-124">*你组织中的人员*共享链接</span><span class="sxs-lookup"><span data-stu-id="a7fd6-124">*People in your organization* sharing links</span></span>](#people-in-your-organization-sharing-links)|<span data-ttu-id="a7fd6-125">SharePoint 网站所有者和成员可以使用*你组织中的人员*链接（可用于组织内的所有人）来共享文件。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-125">SharePoint site owners and members can share files using *People in your organization* links, which will work for anyone inside the organization.</span></span>|<span data-ttu-id="a7fd6-126">可在网站级别禁用*你组织中的人员*链接。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-126">*People in your organization* links can be disabled at the site level.</span></span>|
|[<span data-ttu-id="a7fd6-127">电子邮件</span><span class="sxs-lookup"><span data-stu-id="a7fd6-127">Email</span></span>](#email)|<span data-ttu-id="a7fd6-128">有权访问文件的人员可通过电子邮件将其发送给其他人。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-128">People with access to a file can send it to others via email.</span></span>|<span data-ttu-id="a7fd6-129">管理员可以使用敏感度标签对文件进行加密，以防止有人与未经授权的人员共享这些文件。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-129">Admins can encrypt files by using sensitivity labels to prevent them being shared with unauthorized people.</span></span>|
|[<span data-ttu-id="a7fd6-130">下载或文件复制</span><span class="sxs-lookup"><span data-stu-id="a7fd6-130">Download or file copy</span></span>](#download-or-file-copy)|<span data-ttu-id="a7fd6-131">有权访问文件的人员可以下载或复制该文件，并与 Microsoft 365 范围之外的其他人共享。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-131">People with access to a file can download or copy it and share it with others outside the scope of Microsoft 365.</span></span>|<span data-ttu-id="a7fd6-132">管理员可以使用敏感度标签对文件进行加密，以防止有人与未经授权的人员共享这些文件。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-132">Admins can encrypt files by using sensitivity labels to prevent them being shared with unauthorized people.</span></span>|

<span data-ttu-id="a7fd6-133">虽然可使用本文中介绍的管理员控制措施来限制组织内的共享，但我们强烈建议考虑使用 Microsoft 365 中提供的安全和合规性功能，以创建安全的共享环境。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-133">While you can use the admin controls described in this article to limit sharing in your organization, we highly recommend that you consider using the security and compliance features available in Microsoft 365 to create a secure sharing environment.</span></span> <span data-ttu-id="a7fd6-134">有关信息，请参阅[使用 Microsoft 365 在 SharePoint 中进行文件协作](https://docs.microsoft.com/sharepoint/deploy-file-collaboration)和[用于高度管控数据的 Teams](https://docs.microsoft.com/microsoft-365/enterprise/secure-teams-highly-regulated-data-scenario)。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-134">See [File collaboration in SharePoint with Microsoft 365](https://docs.microsoft.com/sharepoint/deploy-file-collaboration) and [Teams for highly regulated data](https://docs.microsoft.com/microsoft-365/enterprise/secure-teams-highly-regulated-data-scenario) for information.</span></span>

<span data-ttu-id="a7fd6-135">若要了解组织中如何使用共享，请[运行文件和文件夹共享报告](https://docs.microsoft.com/sharepoint/sharing-reports)。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-135">To understand how sharing is being used in your organization, [run a report on file and folder sharing](https://docs.microsoft.com/sharepoint/sharing-reports).</span></span>

## <a name="office-365-group-or-team"></a><span data-ttu-id="a7fd6-136">Office 365 组或团队</span><span class="sxs-lookup"><span data-stu-id="a7fd6-136">Office 365 group or team</span></span>

<span data-ttu-id="a7fd6-137">如果想要限制 Office 365 组或 Microsoft Teams 团队中的共享，请务必将组或团队设为专用。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-137">If you want to limit sharing in an Office 365 group or Microsoft Teams team, it's important to make the group or team private.</span></span> <span data-ttu-id="a7fd6-138">组织内部人员可以随时加入公共组或团队。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-138">People inside your organization can join a public group or team anytime.</span></span> <span data-ttu-id="a7fd6-139">除非组或团队是专用的，否则无法在组织内限制团队或其文件的共享。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-139">Unless the group or team is private, there's no way to limit sharing of the team or its files within the organization.</span></span>

### <a name="guest-sharing"></a><span data-ttu-id="a7fd6-140">来宾共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-140">Guest sharing</span></span>

<span data-ttu-id="a7fd6-141">如果想要阻止 Teams 中的来宾访问，可在 Teams 管理中心内关闭来宾共享。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-141">If you want to prevent guest access in Teams, you can turn off guest sharing in the Teams admin center.</span></span>

<span data-ttu-id="a7fd6-142">关闭 Teams 的来宾共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-142">To turn off guest sharing for Teams</span></span>
1. <span data-ttu-id="a7fd6-143">在 Teams 管理中心中，展开“**组织范围的设置**”，然后单击“**来宾访问**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-143">In the Teams admin center, expand **Org-wide settings**, and then click **Guest access**.</span></span>
2. <span data-ttu-id="a7fd6-144">关闭“**在 Teams 中允许访客访问**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-144">Turn off **Allow guest access in Teams**.</span></span>
3. <span data-ttu-id="a7fd6-145">单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-145">Click **Save**.</span></span>

<span data-ttu-id="a7fd6-146">如果想要阻止 Office 365 组中的来宾访问，可在 Microsoft 365 管理中心内关闭组来宾访问设置。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-146">If you want to prevent guest access in Office 365 groups, you can turn off the groups guest access settings in the Microsoft 365 admin center.</span></span>

<span data-ttu-id="a7fd6-147">关闭 Office 365 组中的来宾共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-147">To turn off guest sharing in Office 365 groups</span></span>
1. <span data-ttu-id="a7fd6-148">在 Microsoft 365 管理中心中，单击“**设置**”，然后单击“**设置**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-148">In the Microsoft 365 admin center, click **Settings**, and then click **Settings**.</span></span>
2. <span data-ttu-id="a7fd6-149">在“**服务**”选项卡上，单击“**Office 365 组**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-149">On the **Services** tab, click **Office 365 Groups**.</span></span>
3. <span data-ttu-id="a7fd6-150">取消选中“**允许组织外部的组成员访问组内容**”和“**允许组所有者将组织外部的人员添加到组**”复选框。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-150">Clear the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes.</span></span>
4. <span data-ttu-id="a7fd6-151">单击“**保存更改**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-151">Click **Save changes**.</span></span>

    ![Microsoft 365 管理中心中的 Office 365 组共享设置的屏幕截图](media/office-365-groups-guest-settings-off.png)

> [!NOTE]
> <span data-ttu-id="a7fd6-153">如果想要阻止特定组或团队的来宾共享，可使用 Microsoft PowerShell 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-153">If you want to prevent guest sharing for a particular group or team, you can do so by using Microsoft PowerShell.</span></span> <span data-ttu-id="a7fd6-154">有关详细信息，请参阅[阻止特定组中的来宾用户](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#block-guest-users-from-a-specific-group)。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-154">See [Block guest users from a specific group](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#block-guest-users-from-a-specific-group) for details.</span></span>

<span data-ttu-id="a7fd6-155">可通过在 Azure Active Directory 中允许或阻止域，将来宾共享限制为指定域的用户。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-155">You can limit guest sharing to users from specific domains by allowing or blocking domains in Azure Active Directory.</span></span> <span data-ttu-id="a7fd6-156">如果已启用 [Azure AD B2B 的 SharePoint 和 OneDrive 集成](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)，该操作还会影响 SharePoint 中的来宾共享。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-156">This will also affect guest sharing in SharePoint if you have enabled [SharePoint and OneDrive integration with Azure AD B2B](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview).</span></span>

<span data-ttu-id="a7fd6-157">仅允许向指定域发出共享邀请</span><span class="sxs-lookup"><span data-stu-id="a7fd6-157">To allow sharing invitations only from specified domains</span></span>
1. <span data-ttu-id="a7fd6-158">在 Azure Active Directory 中的“概述”页面上，单击“**组织关系**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-158">In Azure Active Directory, on the Overview page, click **Organizational relationships**.</span></span>
2. <span data-ttu-id="a7fd6-159">单击“**设置**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-159">Click **Settings**.</span></span>
3. <span data-ttu-id="a7fd6-160">在“**协作限制**”下，选择“**拒绝向指定域发出邀请**”或“**仅允许向指定域发出邀请**”，然后键入要使用的域。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-160">Under **Collaboration restrictions**, select **Deny invitations to the specified domains** or **Allow invitations only to the specified domains**, and then type the domains that you want to use.</span></span>
4. <span data-ttu-id="a7fd6-161">单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-161">Click **Save**.</span></span>

    ![Azure Active Directory 中的协作限制设置的屏幕截图](media/azure-ad-allow-only-specified-domains.png)

## <a name="sharepoint-site"></a><span data-ttu-id="a7fd6-163">SharePoint 网站</span><span class="sxs-lookup"><span data-stu-id="a7fd6-163">SharePoint site</span></span>

<span data-ttu-id="a7fd6-164">你可以将 SharePoint 网站共享的执行者限制为仅限网站所有者。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-164">You can limit SharePoint site sharing to site owners only.</span></span> <span data-ttu-id="a7fd6-165">这将防止网站成员共享网站。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-165">This prevents site members from sharing the site.</span></span> <span data-ttu-id="a7fd6-166">请记住，如果网站连接到了一个 Office 365 组，组成员可以邀请其他人加入该组，并且这些用户将拥有网站的访问权限。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-166">Keep in mind that if the site is connected to an Office 365 group, group members can invite others to the group and those users will have site access.</span></span>

<span data-ttu-id="a7fd6-167">将网站共享的执行者限制为所有者</span><span class="sxs-lookup"><span data-stu-id="a7fd6-167">To limit site sharing to owners</span></span>
1. <span data-ttu-id="a7fd6-168">在网站中，单击齿轮图标，然后单击“**网站权限**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-168">In the site, click the gear icon, and then click **Site permissions**.</span></span>
2. <span data-ttu-id="a7fd6-169">在“**共享设置**”下，单击“**更改共享设置**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-169">Under **Sharing settings**, click **Change sharing settings**.</span></span>
3. <span data-ttu-id="a7fd6-170">选择“**网站所有者和成员以及拥有编辑权限的人员可共享文件和文件夹，但只有网站所有者才可共享网站**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-170">Select **Site owners and members, and people with Edit permissions can share files and folders, but only site owners can share the site**.</span></span>
4. <span data-ttu-id="a7fd6-171">单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-171">Click **Save**.</span></span>

    ![SharePoint 网站中共享权限设置的屏幕截图](media/sharepoint-site-sharing-permissions-level-two.png)

<span data-ttu-id="a7fd6-173">可通过关闭访问请求来阻止不是网站成员的用户请求访问。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-173">You can prevent users who are not members of the site from requesting access by turning off access requests.</span></span>

<span data-ttu-id="a7fd6-174">关闭访问请求</span><span class="sxs-lookup"><span data-stu-id="a7fd6-174">To turn off access requests</span></span>
1. <span data-ttu-id="a7fd6-175">在网站中，单击齿轮图标，然后单击“**网站权限**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-175">In the site, click the gear icon, and then click **Site permissions**.</span></span>
2. <span data-ttu-id="a7fd6-176">在“**共享设置**”下，单击“**更改共享设置**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-176">Under **Sharing settings**, click **Change sharing settings**.</span></span>
3. <span data-ttu-id="a7fd6-177">关闭“**允许访问请求**”，然后单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-177">Turn off **Allow access requests**, and then click **Save**.</span></span>

<span data-ttu-id="a7fd6-178">可通过为相应网站允许或阻止域，将网站共享限制为指定域。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-178">You can limit site sharing to specific domains by allowing or blocking domains for the site.</span></span>

<span data-ttu-id="a7fd6-179">按域限制网站共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-179">To limit site sharing by domain</span></span>
1. <span data-ttu-id="a7fd6-180">在 SharePoint 管理中心中的“**网站**”下，单击“**活动站点**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-180">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="a7fd6-181">单击要配置的网站。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-181">Click the site that you want to configure.</span></span>
3. <span data-ttu-id="a7fd6-182">在“**策略**”选项卡的“**外部共享**”下，单击“**编辑**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-182">On the **Policies** tab, under **External sharing** click **Edit**.</span></span>
4. <span data-ttu-id="a7fd6-183">在“**外部共享的高级设置**”下，选中“**按域限制共享**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-183">Under **Advanced settings for external sharing**, select the **Limit sharing by domain**.</span></span>
5. <span data-ttu-id="a7fd6-184">添加你想要允许或阻止的域，然后单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-184">Add the domains that you want to allow or block, and then click **Save**.</span></span>
6. <span data-ttu-id="a7fd6-185">单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-185">Click **Save**.</span></span>

    ![允许的域网站级别设置的屏幕截图](media/limit-site-sharing-by-domain.png)

## <a name="sharing-with-specific-people"></a><span data-ttu-id="a7fd6-187">与特定人员共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-187">Sharing with specific people</span></span>

<span data-ttu-id="a7fd6-188">如果你想限制网站或其内容的共享，可以将网站配置为仅允许网站所有者共享文件、文件夹和该网站。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-188">if you want to limit the sharing of a site or its contents, you can configure the site to only allow site owners to share files, folders, and the site.</span></span> <span data-ttu-id="a7fd6-189">进行此配置后，当网站成员尝试使用*特定人员*链接共享文件或文件夹时，该尝试将会转到网站所有者那里以供其审批。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-189">When this is configured, site members' attempts to share files or folders by using *Specific people* links will go to the site owner for approval.</span></span>

<span data-ttu-id="a7fd6-190">将网站、文件和文件夹共享的执行者限制为所有者</span><span class="sxs-lookup"><span data-stu-id="a7fd6-190">To limit site, file, and folder sharing to owners</span></span>
1. <span data-ttu-id="a7fd6-191">在网站中，单击齿轮图标，然后单击“**网站权限**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-191">In the site, click the gear icon, and then click **Site permissions**.</span></span>
2. <span data-ttu-id="a7fd6-192">在“**共享设置**”下，单击“**更改共享设置**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-192">Under **Sharing settings**, click **Change sharing settings**.</span></span>
3. <span data-ttu-id="a7fd6-193">选择“**只有站点所有者可共享文件、文件夹和站点**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-193">Select **Only site owners can share files, folders, and the site**.</span></span>
4. <span data-ttu-id="a7fd6-194">单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-194">Click **Save**.</span></span>

    ![SharePoint 网站中共享权限设置的屏幕截图](media/sharepoint-site-only-site-owners-can-share.png)

## <a name="sharepoint-guest-sharing"></a><span data-ttu-id="a7fd6-196">SharePoint 来宾共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-196">SharePoint guest sharing</span></span>

<span data-ttu-id="a7fd6-197">如果想要阻止与组织外部的人员共享 SharePoint 或 OneDrive 文件和文件夹，可针对整个组织或单个网站关闭来宾共享。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-197">If you want to prevent sharing SharePoint or OneDrive files and folders with people outside your organization, you can turn off guest sharing for the entire organization or for an individual site.</span></span>

<span data-ttu-id="a7fd6-198">针对组织关闭 SharePoint 来宾共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-198">To turn off SharePoint guest sharing for your organization</span></span>
1. <span data-ttu-id="a7fd6-199">在 SharePoint 管理中心中的“**策略**”下，单击“**共享**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-199">In the SharePoint admin center, under **Policies**, click **Sharing**.</span></span>
2. <span data-ttu-id="a7fd6-200">在“**外部共享**”下，将 SharePoint 滑块向下拖动到“**仅限组织中的人员**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-200">Under **External sharing**, drag the SharePoint slider down to **Only people in your organization**.</span></span>
3. <span data-ttu-id="a7fd6-201">单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-201">Click **Save**.</span></span>

    ![SharePoint 组织级别共享设置的屏幕截图](media/sharepoint-tenant-sharing-off.png)


<span data-ttu-id="a7fd6-203">针对网站关闭来宾共享</span><span class="sxs-lookup"><span data-stu-id="a7fd6-203">To turn off guest sharing for a site</span></span>
1. <span data-ttu-id="a7fd6-204">在 SharePoint 管理中心中的“**网站**”下，单击“**活动站点**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-204">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="a7fd6-205">单击要配置的网站。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-205">Click the site that you want to configure.</span></span>
3. <span data-ttu-id="a7fd6-206">在“**策略**”选项卡的“**外部共享**”下，单击“**编辑**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-206">On the **Policies** tab, under **External sharing** click **Edit**.</span></span>
4. <span data-ttu-id="a7fd6-207">在“**外部共享**”下，选择“**仅限组织中的人员**”，然后单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-207">Under **External sharing**, choose **Only people in your organization**, and then click **Save**.</span></span>

    ![SharePoint 网站级别共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings-off.png)

<span data-ttu-id="a7fd6-209">如果想要允许与组织外部的人员共享，但要确保每个人都进行身份验证，可以针对整个组织或单个网站禁用*任何人*（匿名共享）链接。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-209">If you would like to allow sharing with people outside your organization but you want to make sure that everyone authenticates, you can disable *Anyone* (anonymous sharing) links for the entire organization or for an individual site.</span></span>

<span data-ttu-id="a7fd6-210">在组织级别关闭*任何人*链接</span><span class="sxs-lookup"><span data-stu-id="a7fd6-210">To turn off *Anyone* links at the organization level</span></span>
1. <span data-ttu-id="a7fd6-211">在 SharePoint 管理中心中的“**策略**”下，单击“**共享**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-211">In the SharePoint admin center, under **Policies**, click **Sharing**.</span></span>
2. <span data-ttu-id="a7fd6-212">在“**外部共享**”下，将 SharePoint 滑块向下拖动到“**新来宾和现有来宾**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-212">Under **External sharing**, drag the SharePoint slider down to **New and existing guests**.</span></span>
3. <span data-ttu-id="a7fd6-213">单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-213">Click **Save**.</span></span>

    ![SharePoint 网站级别共享设置的屏幕截图](media/sharepoint-guest-sharing-new-and-existing-guests.png)

<span data-ttu-id="a7fd6-215">针对某个网站关闭*任何人*链接</span><span class="sxs-lookup"><span data-stu-id="a7fd6-215">To turn off *Anyone* links for a site</span></span>
1. <span data-ttu-id="a7fd6-216">在 SharePoint 管理中心中的“**网站**”下，单击“**活动站点**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-216">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="a7fd6-217">单击要配置的网站。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-217">Click the site that you want to configure.</span></span>
3. <span data-ttu-id="a7fd6-218">在“**策略**”选项卡的“**外部共享**”下，单击“**编辑**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-218">On the **Policies** tab, under **External sharing** click **Edit**.</span></span>
4. <span data-ttu-id="a7fd6-219">在“**外部共享**”下，选择“**新来宾和现有来宾**”，然后单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-219">Under **External sharing**, choose **New and existing guests**, and then click **Save**.</span></span>

    ![SharePoint 网站级别共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings-new-and-existing-guests.png)

## <a name="people-in-your-organization-sharing-links"></a><span data-ttu-id="a7fd6-221">*你组织中的人员*共享链接</span><span class="sxs-lookup"><span data-stu-id="a7fd6-221">*People in your organization* sharing links</span></span>

<span data-ttu-id="a7fd6-222">默认情况下，网站的成员可以使用*你组织中的人员*链接来与组织中的其他人共享文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-222">By default, members of a site can share files and folders with other people in your organization by using a *People in your organization* link.</span></span> <span data-ttu-id="a7fd6-223">你可以使用 PowerShell 禁用*你组织中的人员*链接：</span><span class="sxs-lookup"><span data-stu-id="a7fd6-223">You can disable *People in your organization* links by using PowerShell:</span></span>

`Set-SPOSite -Identity <site> -DisableCompanyWideSharingLinks`

<span data-ttu-id="a7fd6-224">例如：</span><span class="sxs-lookup"><span data-stu-id="a7fd6-224">For example:</span></span>

`Set-SPOSite -Identity https://contoso.sharepoint.com -DisableCompanyWideSharingLinks`

## <a name="email"></a><span data-ttu-id="a7fd6-225">电子邮件</span><span class="sxs-lookup"><span data-stu-id="a7fd6-225">Email</span></span>

<span data-ttu-id="a7fd6-226">可通过加密防止不必要的电子邮件共享。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-226">You can prevent unwanted sharing of emails by using encryption.</span></span> <span data-ttu-id="a7fd6-227">这将防止电子邮件被转发或与未经授权的用户共享。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-227">This prevents emails being forwarded or otherwise shared with unauthorized users.</span></span> <span data-ttu-id="a7fd6-228">你可以使用敏感度标签来启用电子邮件加密。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-228">Email encryption can be enabled by using sensitivity labels.</span></span> <span data-ttu-id="a7fd6-229">有关详细信息，请参阅[使用敏感度标签中的加密限制对内容的访问](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-229">See [Restrict access to content by using encryption in sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels) for details.</span></span>

## <a name="download-or-file-copy"></a><span data-ttu-id="a7fd6-230">下载或文件复制</span><span class="sxs-lookup"><span data-stu-id="a7fd6-230">Download or file copy</span></span>

<span data-ttu-id="a7fd6-231">有权访问 Microsoft 365 中的文件和文件夹的用户可以下载文件并将其复制到外部媒体。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-231">Users who have access to files and folders in Microsoft 365 can download files and copy them to external media.</span></span> <span data-ttu-id="a7fd6-232">若要减少不必要的文件共享的风险，可使用敏感度标签对内容进行加密。</span><span class="sxs-lookup"><span data-stu-id="a7fd6-232">To reduce the risk of unwanted file sharing, you can encrypt the content by using sensitivity labels.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7fd6-233">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7fd6-233">See also</span></span>

[<span data-ttu-id="a7fd6-234">Microsoft 365 来宾共享设置参考</span><span class="sxs-lookup"><span data-stu-id="a7fd6-234">Microsoft 365 guest sharing settings reference</span></span>](microsoft-365-guest-settings.md)
