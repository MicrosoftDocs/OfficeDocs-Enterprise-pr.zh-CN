---
title: 限制意外公开
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
description: 了解如何在与来宾共享文件时限制意外公开信息。
ms.openlocfilehash: d1a12579bdcce03ad74dbf753ddb1a8a6368c88c
ms.sourcegitcommit: c16ab90d0b9902228ce4337f1c64900592936cce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2019
ms.locfileid: "37108260"
---
# <a name="limit-accidental-exposure-to-files-when-sharing-with-guests"></a><span data-ttu-id="fe6f0-103">与来宾共享时限制文件意外公开</span><span class="sxs-lookup"><span data-stu-id="fe6f0-103">Limit accidental exposure to files when sharing with guests</span></span>

<span data-ttu-id="fe6f0-104">与来宾共享文件和文件夹时，可通过多种方法来降低意外共享机密信息的机率。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-104">When sharing files and folders with guests, there are a variety of options to reduce the chances of accidentally sharing confidential information.</span></span> <span data-ttu-id="fe6f0-105">可从本文中的选项中进行选择，以最好地满足贵组织的需求。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-105">You can choose from the options in this article to best meet the needs of your organization.</span></span>

## <a name="use-best-practices-for-anyone-links"></a><span data-ttu-id="fe6f0-106">对“任何人”链接使用最佳做法</span><span class="sxs-lookup"><span data-stu-id="fe6f0-106">Use best practices for Anyone links</span></span>

<span data-ttu-id="fe6f0-107">如果贵组织中的人员需要进行匿名共享，但你担心未经身份验证的来宾修改内容，请阅读[匿名共享的最佳做法](best-practices-anonymous-sharing.md)，获取有关如何处理贵组织中的匿名共享的指南。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-107">If people in your organization need to do anonymous sharing, but you're concerned about unauthenticated guests modifying content, read [Best practices for anonymous sharing](best-practices-anonymous-sharing.md) for guidance on how to work with anonymous sharing in your organization.</span></span>

## <a name="turn-off-anyone-links"></a><span data-ttu-id="fe6f0-108">关闭“任何人”链接</span><span class="sxs-lookup"><span data-stu-id="fe6f0-108">Turn off Anyone links</span></span>

<span data-ttu-id="fe6f0-109">建议对相应内容保持启用“任何人”链接\*\*，因为它是最简单的共享方法，可帮助降低用户查找超出 IT 部门控制范围的其他解决方案的风险。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-109">We recommend leaving *Anyone* links enabled for appropriate content because it's the easiest way to share and can help reduce the risk of users seeking other solutions that are outside the control of your IT department.</span></span> <span data-ttu-id="fe6f0-110">可以将“任何人”\*\* 链接转发给其他人，但是文件访问权只可用于拥有该链接的人。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-110">*Anyone* links can be forwarded to others, but file access is only available to those who have the link.</span></span>

<span data-ttu-id="fe6f0-111">如果你始终希望来宾在访问 SharePoint、组或团队中的内容时进行身份验证，则可关闭“任何人”\*\* 共享。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-111">If you always want guests to authenticate when accessing content in SharePoint, Groups, or Teams, you can turn off *Anyone* sharing.</span></span> <span data-ttu-id="fe6f0-112">这将防止用户匿名共享内容。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-112">This will prevent users from sharing content anonymously.</span></span>

<span data-ttu-id="fe6f0-113">如果禁用“任何人”\*\* 链接，用户仍然可以使用“特定人员”\*\* 链接与来宾轻松共享。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-113">If you disable *Anyone* links, users can still easily share with guests using *Specific people* links.</span></span> <span data-ttu-id="fe6f0-114">在这种情况下，需要对所有来宾进行身份验证，然后才能访问共享内容。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-114">In this case, all guests will be required to authenticate before they can access the shared content.</span></span>

<span data-ttu-id="fe6f0-115">根据你的需要，可以针对特定网站或整个组织禁用“任何人”\*\* 链接。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-115">Depending on your needs, you can disable *Anyone* links for specific sites, or for your whole organization.</span></span>

<span data-ttu-id="fe6f0-116">关闭组织的“任何人”\*\* 链接</span><span class="sxs-lookup"><span data-stu-id="fe6f0-116">To turn off *Anyone* links for your organization</span></span>
1. <span data-ttu-id="fe6f0-117">在 SharePoint 管理中心的左侧导航栏中，单击“共享”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-117">In the SharePoint Online admin center, in the left navigation, click **configure hybrid**.</span></span>
2. <span data-ttu-id="fe6f0-118">将 SharePoint 外部共享设置设为“新来宾和现有来宾”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-118">Set the SharePoint external sharing settings to **New and existing guests**.</span></span></br>
   <span data-ttu-id="fe6f0-119">![SharePoint 网站外部共享设置的屏幕截图](media/sharepoint-organization-external-sharing-controls-new-users.png)</span><span class="sxs-lookup"><span data-stu-id="fe6f0-119">![Screenshot of SharePoint site external sharing settings](media/sharepoint-organization-external-sharing-controls-new-users.png)</span></span>
3. <span data-ttu-id="fe6f0-120">单击“保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-120">Click **Save**.</span></span>

<span data-ttu-id="fe6f0-121">关闭站点的“任何人”\*\* 链接</span><span class="sxs-lookup"><span data-stu-id="fe6f0-121">To turn off *Anyone* links for a site</span></span>
1. <span data-ttu-id="fe6f0-122">在 SharePoint 管理中心的左侧导航栏中，展开“站点”\*\*\*\*，然后单击“活动站点”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-122">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="fe6f0-123">选择刚才创建的团队站点。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-123">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="fe6f0-124">在功能区中，单击“共享”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-124">In the ribbon, click **New**.</span></span>
4. <span data-ttu-id="fe6f0-125">确保将共享设置为“新来宾和现有来宾”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-125">Ensure that sharing is set to **New and existing guests**.</span></span></br>
   <span data-ttu-id="fe6f0-126">![SharePoint 网站外部共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings.png)</span><span class="sxs-lookup"><span data-stu-id="fe6f0-126">![Screenshot of SharePoint site external sharing settings](media/sharepoint-site-external-sharing-settings.png)</span></span>
5. <span data-ttu-id="fe6f0-127">如果进行了任何更改，请单击“保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-127">If you made any changes, click **Validate**.</span></span>

## <a name="domain-filtering"></a><span data-ttu-id="fe6f0-128">域筛选</span><span class="sxs-lookup"><span data-stu-id="fe6f0-128">Domain filtering</span></span>

<span data-ttu-id="fe6f0-129">可使用域的允许或拒绝列表来确定用户可从哪些域中邀请来宾。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-129">You can use domain allow or deny lists to determine which domains your users can invite guests from.</span></span>

<span data-ttu-id="fe6f0-130">使用允许列表，可以指定贵组织用户可从中邀请来宾的域的列表。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-130">With an allow list, you can specify a list of domains from which users in your organization can invite guests.</span></span> <span data-ttu-id="fe6f0-131">其他域的来宾邀请被阻止。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-131">Guest invitations to other domains are blocked.</span></span> <span data-ttu-id="fe6f0-132">如果贵组织仅从特定域的列表中与来宾进行协作，则可以使用此功能阻止与其他域共享。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-132">If your organization only collaborates with guests from a list of specific domains, you can use this feature to prevent sharing with other domains.</span></span>

<span data-ttu-id="fe6f0-133">使用拒绝列表，可以指定贵组织用户无法从中邀请来宾的域的列表。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-133">With a deny list, you can specify a list of domains from which users in your organization cannot invite guests.</span></span> <span data-ttu-id="fe6f0-134">列出的域的来宾邀请被阻止。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-134">Guest invitations to the listed domains are blocked.</span></span> <span data-ttu-id="fe6f0-135">如果你有竞争对手（例如你想要阻止其成为贵组织中的来宾），此功能可能非常有用。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-135">This can be useful if you have competitors, for example, who you want to prevent from becoming guests in your organization.</span></span>

<span data-ttu-id="fe6f0-136">允许列表和拒绝列表仅影响与经过身份验证的来宾的共享。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-136">The allow and deny lists only affect sharing with authenticated guests.</span></span> <span data-ttu-id="fe6f0-137">如果你尚未禁用用户，用户仍可使用“任何人”\*\* 链接与被禁止域中的来宾共享。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-137">Users can still share with guests from prohibited domains by using *Anyone* links if you haven't disabled them.</span></span> <span data-ttu-id="fe6f0-138">若要使用域允许和拒绝列表获得最佳结果，请考虑按上面所述禁用“任何人”\*\* 链接。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-138">For best results with domain allow and deny lists, consider disabling *Anyone* links as described above.</span></span>

<span data-ttu-id="fe6f0-139">为来宾共享设置域允许或拒绝列表</span><span class="sxs-lookup"><span data-stu-id="fe6f0-139">To set up a domain allow or deny list for guest sharing</span></span>
1. <span data-ttu-id="fe6f0-140">在 SharePoint 管理中心的左侧导航栏中，单击“共享”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-140">In the SharePoint Online admin center, in the left navigation, click **configure hybrid**.</span></span>
2. <span data-ttu-id="fe6f0-141">在“用于外部共享的高级设置”\*\*\*\* 下，选中“限制外部共享(按域)”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-141">Under **Advanced settings for external sharing**, select the **Limit external sharing by domain** check box.</span></span>
3. <span data-ttu-id="fe6f0-142">单击“添加域”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-142">Click **Add domains**.</span></span>
4. <span data-ttu-id="fe6f0-143">选择是否要阻止域，键入域，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-143">Select whether you want to block domains, type the domains, and click **OK**.</span></span></br>
   <span data-ttu-id="fe6f0-144">![SharePoint 按域限制外部共享设置的屏幕截图](media/sharepoint-sharing-block-domain.png)</span><span class="sxs-lookup"><span data-stu-id="fe6f0-144">![Screenshot of SharePoint limit external sharing by domain setting](media/sharepoint-sharing-block-domain.png)</span></span>
5. <span data-ttu-id="fe6f0-145">单击“保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-145">Click **Save**.</span></span>

<span data-ttu-id="fe6f0-146">如果想要在高于 SharePoint 和 OneDrive 的级别限制按域共享，则可以在 Azure Active Directory 中[允许或阻止来自特定组织的 B2B 用户的邀请](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-146">If you want to limit sharing by domain at a higher level than SharePoint and OneDrive, you can [allow or block invitations to B2B users from specific organizations](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list) in Azure Active Directory.</span></span> <span data-ttu-id="fe6f0-147">（必须配置 [SharePoint 和 OneDrive 与 Azure AD B2B Preview 的集成](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)，这些设置才会影响 SharePoint 和 OneDrive。）</span><span class="sxs-lookup"><span data-stu-id="fe6f0-147">(You must configure the [SharePoint and OneDrive integration with Azure AD B2B Preview](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview) for these settings to affect SharePoint and OneDrive.)</span></span>

## <a name="limit-guest-sharing-of-files-folders-and-sites-to-specified-security-groups"></a><span data-ttu-id="fe6f0-148">将文件、文件夹和站点的来宾共享限制到指定的安全组</span><span class="sxs-lookup"><span data-stu-id="fe6f0-148">Limit guest sharing of files, folders, and sites to specified security groups</span></span>

<span data-ttu-id="fe6f0-149">可以将文件、文件夹和站点的来宾共享限制到特定的安全组成员。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-149">You can restrict guest sharing of files, folders, and sites to members of a specific security group.</span></span> <span data-ttu-id="fe6f0-150">如果你希望启用来宾共享，但有批准工作流或请求流程，则此功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-150">This is useful if you want to enable guest sharing, but with an approval workflow or request process.</span></span>

<span data-ttu-id="fe6f0-151">将来宾共享限制到安全组的成员</span><span class="sxs-lookup"><span data-stu-id="fe6f0-151">To limit guest sharing to members of a security group</span></span>
1. <span data-ttu-id="fe6f0-152">在 SharePoint 管理中心的左侧导航栏中，单击“共享”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-152">In the SharePoint Online admin center, in the left navigation, click **configure hybrid**.</span></span>
2. <span data-ttu-id="fe6f0-153">在“其他设置”\*\*\*\* 下，</span><span class="sxs-lookup"><span data-stu-id="fe6f0-153">Under **Other settings**.</span></span> <span data-ttu-id="fe6f0-154">按照“将外部共享的范围限制到特定安全组”\*\*\*\* 链接操作。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-154">follow the **Limit external sharing to specific security groups** link.</span></span>
3. <span data-ttu-id="fe6f0-155">在“可进行组织外共享的人员”\*\*\*\* 下，选中复选框之一或全部选中：a.</span><span class="sxs-lookup"><span data-stu-id="fe6f0-155">Under **Who can share outside your organization**, select one or both of the check boxes: a.</span></span> <span data-ttu-id="fe6f0-156">“仅让所选安全组中的用户与已验证的外部用户共享”\*\*\*\* 以指定可与已经过身份验证的用户共享的安全组。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-156">**Let only users in selected security groups share with authenticated external users** to specify a security group that can share with authenticated users b.</span></span> <span data-ttu-id="fe6f0-157">“仅让所选安全组中的用户使用匿名链接与已验证的外部用户共享”\*\*\*\* 以指定可使用“任何人”链接与已经过身份验证的用户共享的安全组。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-157">**Let only users in selected security groups share with authenticated external users and using anonymous links** to specify a security group that can share with authenticated users and by using Anyone links</span></span>
4. <span data-ttu-id="fe6f0-158">单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-158">Click **OK**.</span></span>

<span data-ttu-id="fe6f0-159">请注意，这会影响文件、文件夹和站点，但不会影响 Office 365 组或团队。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-159">Note that this affects files, folders, and sites, but not Office 365 groups or Teams.</span></span> <span data-ttu-id="fe6f0-160">当成员将来宾邀请到 Microsoft Teams 中的私有 Office 365 组或私人团队中时，该邀请会发送给组或团队所有者进行审批。</span><span class="sxs-lookup"><span data-stu-id="fe6f0-160">When members invite guests to a private Office 365 group or a private team in Microsoft Teams, the invitation is sent to the group or team owner for approval.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe6f0-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe6f0-161">See Also</span></span>

[<span data-ttu-id="fe6f0-162">创建安全的来宾共享环境</span><span class="sxs-lookup"><span data-stu-id="fe6f0-162">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

[<span data-ttu-id="fe6f0-163">有关与匿名用户共享文件和文件夹的最佳做法</span><span class="sxs-lookup"><span data-stu-id="fe6f0-163">Best practices for sharing files and folders with anonymous users</span></span>](best-practices-anonymous-sharing.md)