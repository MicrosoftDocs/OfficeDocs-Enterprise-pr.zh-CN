---
title: 未经身份验证共享的最佳做法
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
description: 了解有关与身份未经验证用户共享文件和文件夹的最佳做法。
ms.openlocfilehash: decdc068f238329516ae0ce3594e68a753780216
ms.sourcegitcommit: b5992f367ccae97a8ea538738fe36d3d703cd6e7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "39919134"
---
# <a name="best-practices-for-sharing-files-and-folders-with-unauthenticated-users"></a><span data-ttu-id="fe60a-103">有关与身份未经验证用户共享文件和文件夹的最佳做法</span><span class="sxs-lookup"><span data-stu-id="fe60a-103">Best practices for sharing files and folders with unauthenticated users</span></span>

<span data-ttu-id="fe60a-104">未经身份验证共享（*任何人*链接）非常方便，在各种情景中都很有用。</span><span class="sxs-lookup"><span data-stu-id="fe60a-104">Unauthenticated sharing (*Anyone* links) can be convenient and is useful in various scenarios.</span></span> <span data-ttu-id="fe60a-105">*任何人*链接是最简单的共享方式：用户无需身份验证即可打开链接，并可将其自由传递给其他人。</span><span class="sxs-lookup"><span data-stu-id="fe60a-105">*Anyone* links are the easiest way to share: guests can open the link without authentication and are free to pass it on to others.</span></span>

<span data-ttu-id="fe60a-106">通常情况下，并非组织中的所有内容都适合未经身份验证共享。</span><span class="sxs-lookup"><span data-stu-id="fe60a-106">Usually, not all content in an organization is appropriate for unauthenticated sharing.</span></span> <span data-ttu-id="fe60a-107">本文介绍了一些可用选项，这些选项可帮助你创建一个环境，让你的用户能在其中未经身份验证共享文件和文件夹，但其中也有安全措施来帮助你保护组织的内容。</span><span class="sxs-lookup"><span data-stu-id="fe60a-107">This article covers the options available to help you create an environment where your users can use unauthenticated sharing of files and folders, but where there are safeguards in place to help protect your organization's content.</span></span>

> [!NOTE]
> <span data-ttu-id="fe60a-108">若要正常使用未经身份验证共享功能，必须为你的组织以及要使用的各个网站或团队启用该功能。</span><span class="sxs-lookup"><span data-stu-id="fe60a-108">For unauthenticated sharing to work, you must enable it for your organization and for the individual site or team that you'll be using.</span></span> <span data-ttu-id="fe60a-109">对于你希望启用该功能的情景，请参阅[与组织外部人员协作](collaborating-with-people-outside-your-organization.md)。</span><span class="sxs-lookup"><span data-stu-id="fe60a-109">See [Collaborating with people outside your organization](collaborating-with-people-outside-your-organization.md) for the scenario that you want to enable.</span></span>

## <a name="set-an-expiration-date-for-anyone-links"></a><span data-ttu-id="fe60a-110">设置“任何人”链接的到期日期</span><span class="sxs-lookup"><span data-stu-id="fe60a-110">Set an expiration date for Anyone links</span></span>

<span data-ttu-id="fe60a-111">文件通常在网站、组和团队中存储很长一段时间。</span><span class="sxs-lookup"><span data-stu-id="fe60a-111">Files are often stored in sites, groups, and teams for long periods of time.</span></span> <span data-ttu-id="fe60a-112">偶尔有些数据保留策略会要求将文件保留几年时间。</span><span class="sxs-lookup"><span data-stu-id="fe60a-112">Occasionally there are data retention policies that require files to be retained for years.</span></span> <span data-ttu-id="fe60a-113">如果与未经身份验证人员共享此类文件，可能会导致将来在意想不到的情况下访问和更改文件。</span><span class="sxs-lookup"><span data-stu-id="fe60a-113">If such files are shared with unauthenticated people, this could lead to unexpected access and changes to files in the future.</span></span> <span data-ttu-id="fe60a-114">为了降低这种可能性，可为*任何人*链接配置到期时间。</span><span class="sxs-lookup"><span data-stu-id="fe60a-114">To mitigate this possibility, you can configure an expiration time for *Anyone* links.</span></span>

<span data-ttu-id="fe60a-115">*任何人*链接到期后，不能再将其用于访问内容。</span><span class="sxs-lookup"><span data-stu-id="fe60a-115">Once an *Anyone* link expires, it can no longer be used to access content.</span></span>

<span data-ttu-id="fe60a-116">设置“任何人”链接的到期日期</span><span class="sxs-lookup"><span data-stu-id="fe60a-116">To set an expiration date for Anyone links</span></span>
1. <span data-ttu-id="fe60a-117">打开 SharePoint Online 管理中心。</span><span class="sxs-lookup"><span data-stu-id="fe60a-117">Open the SharePoint Online admin center.</span></span>
2. <span data-ttu-id="fe60a-118">在左侧导航中，单击“**共享**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-118">In the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="fe60a-119">在“**‘任何人’链接的高级设置**”下，选中“**这些链接必须在这些天数内过期**”复选框。</span><span class="sxs-lookup"><span data-stu-id="fe60a-119">Under **Advanced settings for "Anyone" links**, select the **These links must expire within this many days** check box.</span></span></br>
   <span data-ttu-id="fe60a-120">![SharePoint 组织级别的“任何人”链接到期设置的屏幕截图](media/sharepoint-organization-anyone-link-expiration.png)</span><span class="sxs-lookup"><span data-stu-id="fe60a-120">![Screenshot of SharePoint organization-level Anyone link expiration settings](media/sharepoint-organization-anyone-link-expiration.png)</span></span>
4. <span data-ttu-id="fe60a-121">在输入框中键入天数，然后单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-121">Type a number of days in the box, and then click **Save**.</span></span>

<span data-ttu-id="fe60a-122">请注意，*任何人*链接到期后，可以使用新的“*任何人*”链接重新共享该文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="fe60a-122">Note that once an *Anyone* link expires, the file or folder can be re-shared with a new *Anyone* link.</span></span>

## <a name="set-link-permissions"></a><span data-ttu-id="fe60a-123">设置链接权限</span><span class="sxs-lookup"><span data-stu-id="fe60a-123">Set link permissions</span></span>

<span data-ttu-id="fe60a-124">默认情况下，文件的*任何人*链接允许用户编辑文件，而文件夹的*任何人*链接允许用户编辑和查看其中的文件以及向文件夹上传新文件。</span><span class="sxs-lookup"><span data-stu-id="fe60a-124">By default, *Anyone* links for a file allow people to edit the file, and *Anyone* links for a folder allow people to edit and view files, and upload new files to the folder.</span></span> <span data-ttu-id="fe60a-125">可单独将这些文件和文件夹的权限更改为“仅查看”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-125">You can change these permissions for files and for folders independently to view-only.</span></span>

<span data-ttu-id="fe60a-126">如果希望允许未经身份验证共享，但担心未经身份验证的人员修改组织的内容，可考虑将文件和文件夹权限设置为“**查看**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-126">If you want to allow unauthenticated sharing, but are concerned about unauthenticated people modifying your organization's content, consider setting the file and folder permissions to **View**.</span></span>

<span data-ttu-id="fe60a-127">设置“任何人”链接权限</span><span class="sxs-lookup"><span data-stu-id="fe60a-127">To set permissions for Anyone links</span></span>
1. <span data-ttu-id="fe60a-128">打开 SharePoint Online 管理中心。</span><span class="sxs-lookup"><span data-stu-id="fe60a-128">Open the SharePoint Online admin center.</span></span>
2. <span data-ttu-id="fe60a-129">在左侧导航中，单击“**共享**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-129">In the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="fe60a-130">在“**‘任何人’链接的高级设置**”下，选择要使用的文件和文件夹权限。</span><span class="sxs-lookup"><span data-stu-id="fe60a-130">Under **Advanced settings for "Anyone" links**, select the file and folder permissions that you want to use.</span></span></br>
   <span data-ttu-id="fe60a-131">![SharePoint 组织级别的“任何人”链接权限设置的屏幕截图](media/sharepoint-organization-anyone-link-permissions.png)</span><span class="sxs-lookup"><span data-stu-id="fe60a-131">![Screenshot of SharePoint organization-level Anyone link permissions settings](media/sharepoint-organization-anyone-link-permissions.png)</span></span>

<span data-ttu-id="fe60a-132">“*任何人*”链接设置为“**查看**”后，用户仍可与来宾共享文件和文件夹，并可使用*特定人员*链接为其提供编辑权限。</span><span class="sxs-lookup"><span data-stu-id="fe60a-132">With *Anyone* links set to **View**, users can still share files and folders with guests and give them edit permissions by using *Specific people* links.</span></span> <span data-ttu-id="fe60a-133">这些链接要求组织外人员作为来宾进行身份验证，并且你可以跟踪和审核使用这些链接共享的文件和文件夹上的来宾活动。</span><span class="sxs-lookup"><span data-stu-id="fe60a-133">These links require guests to authenticate, and you can track and audit guest activity on files and folders shared with these links.</span></span>

## <a name="set-default-link-type-to-only-work-for-people-in-your-organization"></a><span data-ttu-id="fe60a-134">将默认链接类型设置为仅适用于组织内部人员</span><span class="sxs-lookup"><span data-stu-id="fe60a-134">Set default link type to only work for people in your organization</span></span>

<span data-ttu-id="fe60a-135">为组织启用*任何人*共享后，通常将默认共享链接设置为“**任何人**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-135">When *Anyone* sharing is enabled for your organization, the default sharing link is normally set to **Anyone**.</span></span> <span data-ttu-id="fe60a-136">虽然这对用户来说非常方便，但是会增加意外的未经身份验证的共享风险。</span><span class="sxs-lookup"><span data-stu-id="fe60a-136">While this can be convenient for users, it can increase the risk of unintentional unauthenticated sharing.</span></span> <span data-ttu-id="fe60a-137">如果用户忘记在共享敏感文档时更改链接类型，可能会意外地创建不需要身份验证的共享链接。</span><span class="sxs-lookup"><span data-stu-id="fe60a-137">If a user forgets to change the link type while sharing a sensitive document, they might accidentally create a sharing link that doesn't require authentication.</span></span>

<span data-ttu-id="fe60a-138">你可以通过将默认链接设置更改为仅适用于组织内部人员的链接来降低此风险。</span><span class="sxs-lookup"><span data-stu-id="fe60a-138">You can mitigate this risk by changing the default link setting to a link that only works for people inside your organization.</span></span> <span data-ttu-id="fe60a-139">确实需要未经身份验证共享的用户，则必须明确选择该选项。</span><span class="sxs-lookup"><span data-stu-id="fe60a-139">Users who want to share with unauthenticated people would then have to specifically select that option.</span></span>

<span data-ttu-id="fe60a-140">设置默认的文件和文件夹共享链接</span><span class="sxs-lookup"><span data-stu-id="fe60a-140">To set the default file and folder sharing link</span></span>
1. <span data-ttu-id="fe60a-141">在 SharePoint 管理中心的左侧导航栏中，单击“**共享**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="fe60a-142">在“**文件和文件夹链接**”下，选中“**仅限组织中的人员**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-142">Under **File and folder links**, select **Only people in your organization**.</span></span></br>
   <span data-ttu-id="fe60a-143">![SharePoint 默认链接类型设置的屏幕截图](media/sharepoint-default-sharing-link-company-link.png)</span><span class="sxs-lookup"><span data-stu-id="fe60a-143">![Screenshot of SharePoint default link type setting](media/sharepoint-default-sharing-link-company-link.png)</span></span>
3. <span data-ttu-id="fe60a-144">单击“**保存**”</span><span class="sxs-lookup"><span data-stu-id="fe60a-144">Click **Save**</span></span>

## <a name="protect-against-malicious-files"></a><span data-ttu-id="fe60a-145">防范恶意文件</span><span class="sxs-lookup"><span data-stu-id="fe60a-145">Protect against malicious files</span></span>

<span data-ttu-id="fe60a-146">如果允许匿名用户上传文件，可能会增加他人上载恶意文件的风险。</span><span class="sxs-lookup"><span data-stu-id="fe60a-146">When you allow anonymous users to upload files, you're at an increased risk of someone uploading a malicious file.</span></span> <span data-ttu-id="fe60a-147">在 Microsoft 365 中，可使用高级威胁防护中的*安全附件*功能自动扫描上传的文件并隔离发现的不安全文件。</span><span class="sxs-lookup"><span data-stu-id="fe60a-147">In Microsoft 365, you can use the *safe attachments* feature in Advanced Threat Protection to automatically scan uploaded files and quarantine files that are found to be unsafe.</span></span>

<span data-ttu-id="fe60a-148">启用安全附件</span><span class="sxs-lookup"><span data-stu-id="fe60a-148">To turn on safe attachments</span></span>
1. <span data-ttu-id="fe60a-149">打开 [Microsoft 365 安全](https://security.microsoft.com)管理中心。</span><span class="sxs-lookup"><span data-stu-id="fe60a-149">Open the [Microsoft 365 security](https://security.microsoft.com) admin center.</span></span>
2. <span data-ttu-id="fe60a-150">在左侧导航中，单击“**策略**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-150">In the left navigation, click **Policies**.</span></span>
3. <span data-ttu-id="fe60a-151">在“**威胁防护**”下，单击“**ATP 安全附件(Office 365)**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-151">Under **Threat protection**, click **ATP safe attachments (Office 365)**.</span></span>
4. <span data-ttu-id="fe60a-152">选中“**为 SharePoint、OneDrive 和 Microsoft Teams 启用 ATP**”复选框，然后单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-152">Select the **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams** check box, and then click **Save**.</span></span></br>
   <span data-ttu-id="fe60a-153">![安全与合规中心的安全附件设置的屏幕截图](media/safe-attachments-setting.png)</span><span class="sxs-lookup"><span data-stu-id="fe60a-153">![Screenshot of the safe attachments setting in the Security and Compliance center](media/safe-attachments-setting.png)</span></span>

## <a name="add-copyright-information-to-your-files"></a><span data-ttu-id="fe60a-154">将版权信息添加到文件</span><span class="sxs-lookup"><span data-stu-id="fe60a-154">Add copyright information to your files</span></span>

<span data-ttu-id="fe60a-155">如果在 Microsoft 365 合规管理中心使用灵敏度标签，则可以配置标签，以便自动向组织的 Office 文档添加水印或页眉/页脚。</span><span class="sxs-lookup"><span data-stu-id="fe60a-155">If you use sensitivity labels in the Microsoft 365 Compliance admin center, you can configure your labels to add a watermark or a header or footer automatically to your organization's Office documents.</span></span> <span data-ttu-id="fe60a-156">通过这种方法，可确保共享文件包含版权或其他所有权信息。</span><span class="sxs-lookup"><span data-stu-id="fe60a-156">In this way, you can make sure that shared files contain copyright or other ownership information.</span></span>

<span data-ttu-id="fe60a-157">向带标签的文件添加页脚</span><span class="sxs-lookup"><span data-stu-id="fe60a-157">To add a footer to a labeled file</span></span>
1. <span data-ttu-id="fe60a-158">打开 [Microsoft 365 合规管理中心](https://compliance.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="fe60a-158">Open the [Microsoft 365 compliance admin center](https://compliance.microsoft.com).</span></span>
2. <span data-ttu-id="fe60a-159">在左侧导航中的“**分类**”下，单击“**敏感度标签**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-159">In the left navigation, under **Classification**, click **Sensitivity labels**.</span></span>
3. <span data-ttu-id="fe60a-160">单击要添加页脚的标签，然后单击“**编辑标签**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-160">Click the label that you want to have add a footer, and then click **Edit label**.</span></span>
4. <span data-ttu-id="fe60a-161">单击“**内容标记**”选项卡，然后**打开**内容标记。</span><span class="sxs-lookup"><span data-stu-id="fe60a-161">Click the **Content marking** tab, and then turn **On** content marking.</span></span>
5. <span data-ttu-id="fe60a-162">选中要添加的文本类型的复选框，然后单击“**自定义文本**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-162">Select the check box for the type of text you want to add, and then click **Customize text**.</span></span>
6. <span data-ttu-id="fe60a-163">键入要添加到文档中的文本，选择所需的文本选项，然后单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-163">Type the text that you want added to your documents, select the text options that you want, and then click **Save**.</span></span></br>
   <span data-ttu-id="fe60a-164">![灵敏度标签的内容标记设置的屏幕截图](media/content-marking-for-anonymous-sharing.png)</span><span class="sxs-lookup"><span data-stu-id="fe60a-164">![Screenshot of the content marking settings for a sensitivity label](media/content-marking-for-anonymous-sharing.png)</span></span>
7. <span data-ttu-id="fe60a-165">单击“**保存**”，然后单击“**关闭**”。</span><span class="sxs-lookup"><span data-stu-id="fe60a-165">Click **Save**, and then click **Close**.</span></span>

<span data-ttu-id="fe60a-166">为标签启用内容标记后，用户应用该标签时，你指定的文本将添加到 Office 文档。</span><span class="sxs-lookup"><span data-stu-id="fe60a-166">With content marking enabled for the label, the text you specified will be added to Office documents when a user applies that label.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe60a-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe60a-167">See Also</span></span>


[<span data-ttu-id="fe60a-168">敏感度标签概述</span><span class="sxs-lookup"><span data-stu-id="fe60a-168">Overview of sensitivity labels</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)

[<span data-ttu-id="fe60a-169">与来宾共享时限制文件意外曝光</span><span class="sxs-lookup"><span data-stu-id="fe60a-169">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

[<span data-ttu-id="fe60a-170">创建安全的来宾共享环境</span><span class="sxs-lookup"><span data-stu-id="fe60a-170">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)