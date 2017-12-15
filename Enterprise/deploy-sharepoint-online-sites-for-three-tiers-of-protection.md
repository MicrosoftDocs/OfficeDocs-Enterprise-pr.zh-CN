---
title: "部署 SharePoint Online 网站的三个层次的保护"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "摘要： 创建和配置 SharePoint Online 的团队站点的各种级别的信息保护。"
ms.openlocfilehash: 1023eff2542ab1bf41a8261d85d70c06718497cf
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="16ae2-103">部署 SharePoint Online 网站的三个层次的保护</span><span class="sxs-lookup"><span data-stu-id="16ae2-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="16ae2-104">**摘要：**创建和配置 SharePoint Online 的团队站点的各种级别的信息保护。</span><span class="sxs-lookup"><span data-stu-id="16ae2-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="16ae2-p101">使用本文中的步骤来设计和部署基准，敏感和高度机密 SharePoint Online 团队站点。这些三个层次的保护有关的详细信息，请参阅[安全 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="16ae2-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="16ae2-107">比较基准在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="16ae2-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="16ae2-p102">基线保护包括两个公共和私人团队站点。公用的工作组网站可以发现，并由组织中的任何人访问。只能发现和访问 Office 365 组与工作组网站的成员的专用网站。这两种类型的工作组站点允许成员与他人共享网站。</span><span class="sxs-lookup"><span data-stu-id="16ae2-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="16ae2-112">公用的</span><span class="sxs-lookup"><span data-stu-id="16ae2-112">Public</span></span>

<span data-ttu-id="16ae2-113">具有公共访问权限和权限创建基线在线 SharePoint 工作组网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="16ae2-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="16ae2-p103">登录到 Office 365 门户网站也将用来管理 SharePoint Online 工作组网站 （SharePoint Online 管理员） 的帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="16ae2-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="16ae2-116">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="16ae2-117">在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="16ae2-118">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="16ae2-119">在**站点名称**中，键入公用团队站点的名称。</span><span class="sxs-lookup"><span data-stu-id="16ae2-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="16ae2-120">在**团队站点的说明**中，键入站点的用途的说明。</span><span class="sxs-lookup"><span data-stu-id="16ae2-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="16ae2-121">在**隐私设置**选择**公用-组织中的任何人都可以访问该网站**，，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="16ae2-122">在**谁您想要添加？**窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="16ae2-123">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="16ae2-123">Here is your resulting configuration.</span></span>
  
![适用于公共 SharePoint Online 团队网站的基线级保护。](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="16ae2-125">专用</span><span class="sxs-lookup"><span data-stu-id="16ae2-125">Private</span></span>

<span data-ttu-id="16ae2-126">若要具有私有访问权限和权限创建基线在线 SharePoint 工作组网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="16ae2-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="16ae2-p104">登录到 Office 365 门户网站也将用来管理 SharePoint Online 工作组网站 （SharePoint Online 管理员） 的帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="16ae2-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="16ae2-129">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="16ae2-130">在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="16ae2-131">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="16ae2-132">在**站点名称**中，键入专用工作组站点的名称。</span><span class="sxs-lookup"><span data-stu-id="16ae2-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="16ae2-133">在**团队站点的说明**中，键入网站的用途的说明。</span><span class="sxs-lookup"><span data-stu-id="16ae2-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="16ae2-134">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="16ae2-135">在**谁您想要添加？**窗格中，**添加成员**中, 键入有权访问此专用工作组站点的用户帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="16ae2-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="16ae2-136">当您完成将最初的成员集添加到该网站，单击**完成**</span><span class="sxs-lookup"><span data-stu-id="16ae2-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="16ae2-137">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="16ae2-137">Here is your resulting configuration.</span></span>
  
![适用于专用 SharePoint Online 团队网站的基线级保护。](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="16ae2-139">敏感的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="16ae2-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="16ae2-140">敏感的在线 SharePoint 工作组网站是独立的工作组站点，这意味着，通过而不是与工作组网站的 Office 365 组成员身份的 SharePoint 组中的成员身份控制权限。</span><span class="sxs-lookup"><span data-stu-id="16ae2-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="16ae2-141">若要创建独立的工作组网站，有两个主要步骤。</span><span class="sxs-lookup"><span data-stu-id="16ae2-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="16ae2-142">第 1 步： 设计独立的站点</span><span class="sxs-lookup"><span data-stu-id="16ae2-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="16ae2-143">若要设计独立的工作组站点，您需要确定：</span><span class="sxs-lookup"><span data-stu-id="16ae2-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="16ae2-144">您的 SharePoint 组和权限级别。</span><span class="sxs-lookup"><span data-stu-id="16ae2-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="16ae2-145">将中的 SharePoint 组成员的访问组的组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="16ae2-146">访问组的推荐的设置是站点成员之一、 网站浏览者和站点管理员。</span><span class="sxs-lookup"><span data-stu-id="16ae2-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="16ae2-147">您是否使用嵌套组内访问组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="16ae2-148">例如，组建议的结构和权限级别，如下所示：</span><span class="sxs-lookup"><span data-stu-id="16ae2-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="16ae2-149">**SharePoint 组**</span><span class="sxs-lookup"><span data-stu-id="16ae2-149">**SharePoint group**</span></span>|<span data-ttu-id="16ae2-150">**权限级别**</span><span class="sxs-lookup"><span data-stu-id="16ae2-150">**Permission level**</span></span>|<span data-ttu-id="16ae2-151">**访问组 （示例）**</span><span class="sxs-lookup"><span data-stu-id="16ae2-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="16ae2-152">[站点名称]成员</span><span class="sxs-lookup"><span data-stu-id="16ae2-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="16ae2-153">编辑</span><span class="sxs-lookup"><span data-stu-id="16ae2-153">Edit</span></span>  <br/> |<span data-ttu-id="16ae2-154">[站点名称]成员</span><span class="sxs-lookup"><span data-stu-id="16ae2-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="16ae2-155">[站点名称]访问者</span><span class="sxs-lookup"><span data-stu-id="16ae2-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="16ae2-156">读取</span><span class="sxs-lookup"><span data-stu-id="16ae2-156">Read</span></span>  <br/> |<span data-ttu-id="16ae2-157">[站点名称]查看器</span><span class="sxs-lookup"><span data-stu-id="16ae2-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="16ae2-158">[站点名称]所有者</span><span class="sxs-lookup"><span data-stu-id="16ae2-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="16ae2-159">完全控制</span><span class="sxs-lookup"><span data-stu-id="16ae2-159">Full control</span></span>  <br/> |<span data-ttu-id="16ae2-160">[站点名称]管理员</span><span class="sxs-lookup"><span data-stu-id="16ae2-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="16ae2-p105">默认情况下，工作组站点创建 SharePoint 组和权限级别。您需要确定您访问权限的组的名称。</span><span class="sxs-lookup"><span data-stu-id="16ae2-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="16ae2-163">设计过程的详细信息，请参阅[设计独立的在线 SharePoint 工作组网站](design-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="16ae2-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="16ae2-164">步骤 2： 部署独立的站点</span><span class="sxs-lookup"><span data-stu-id="16ae2-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="16ae2-165">若要部署独立的网站，您首先需要：</span><span class="sxs-lookup"><span data-stu-id="16ae2-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="16ae2-166">确定用户帐户和组添加到每个访问组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="16ae2-167">创建访问组并添加用户和组成员。</span><span class="sxs-lookup"><span data-stu-id="16ae2-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="16ae2-168">有关详细步骤，请参阅[部署独立的在线 SharePoint 工作组网站](deploy-an-isolated-sharepoint-online-team-site.md)的**第一阶段**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="16ae2-169">接下来，使用以下步骤创建 SharePoint Online 的工作组网站。</span><span class="sxs-lookup"><span data-stu-id="16ae2-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="16ae2-p106">登录到 Office 365 门户网站也将用来管理 SharePoint Online 工作组网站 （SharePoint Online 管理员） 的帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="16ae2-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="16ae2-172">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="16ae2-173">在您的浏览器的新**SharePoint**选项卡，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="16ae2-174">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="16ae2-175">在**站点名称**中，键入专用工作组站点的名称。</span><span class="sxs-lookup"><span data-stu-id="16ae2-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="16ae2-176">在**团队站点的说明**中，键入可选的说明。</span><span class="sxs-lookup"><span data-stu-id="16ae2-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="16ae2-177">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="16ae2-178">在**谁您想要添加？**窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="16ae2-179">接下来，从新的 SharePoint Online 工作组站点，使用下列步骤配置权限。</span><span class="sxs-lookup"><span data-stu-id="16ae2-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="16ae2-p107">确定用户的 IT 管理员或其他人员将负责响应和解决对网站的访问请求主体名称 (UPN) （belindan@contoso.com 是 UPN 的示例）。编写该 UPN 此处: ___。</span><span class="sxs-lookup"><span data-stu-id="16ae2-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="16ae2-182">在工具栏上，单击设置图标，然后单击**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="16ae2-183">在**网站权限**窗格中，单击**高级的权限设置**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="16ae2-184">您的浏览器新**权限**选项卡上，单击**访问请求设置**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="16ae2-185">在**访问请求设置**对话框中：</span><span class="sxs-lookup"><span data-stu-id="16ae2-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="16ae2-186">清除**允许成员共享的网站和个别文件和文件夹**，并**允许成员要邀请到网站的成员组的其他人**复选框。</span><span class="sxs-lookup"><span data-stu-id="16ae2-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="16ae2-187">**将所有访问请求都发送**键入您的 IT 管理员，从步骤 1 的 UPN。</span><span class="sxs-lookup"><span data-stu-id="16ae2-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="16ae2-188">单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="16ae2-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="16ae2-189">您的浏览器**权限**选项卡上，单击列表中的**[站点名称] 成员**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="16ae2-190">在**用户和用户组**中，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="16ae2-191">在**共享**对话框中，键入此站点的站点成员访问组的名称，选择它，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="16ae2-192">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="16ae2-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="16ae2-193">在列表中单击**[网站名称] 所有者**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="16ae2-194">在**用户和用户组**中，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="16ae2-195">在**共享**对话框中，键入此站点的管理员访问权限的网站用户组的名称，选择它，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="16ae2-196">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="16ae2-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="16ae2-197">单击**[网站名称] 的访问者**列表中。</span><span class="sxs-lookup"><span data-stu-id="16ae2-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="16ae2-198">在**用户和用户组**中，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="16ae2-199">在**共享**对话框中，键入此站点的站点浏览者访问组的名称，选择它，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="16ae2-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="16ae2-200">关闭您的浏览器**权限**选项卡。</span><span class="sxs-lookup"><span data-stu-id="16ae2-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="16ae2-201">这些权限设置的结果是：</span><span class="sxs-lookup"><span data-stu-id="16ae2-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="16ae2-202">**[网站名称] 所有者**SharePoint 组包含所有成员中具有**完全控制**权限级别的网站管理员访问组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="16ae2-203">**[站点名称] 成员**SharePoint 组包含所有成员中具有**编辑**权限级别的网站成员的访问组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="16ae2-204">**[站点名称] 访问**SharePoint 组包含所有成员中具有**读取**权限级别的网站查看器访问组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="16ae2-205">邀请其他成员的成员的功能被禁用。</span><span class="sxs-lookup"><span data-stu-id="16ae2-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="16ae2-206">启用非成员请求访问的能力。</span><span class="sxs-lookup"><span data-stu-id="16ae2-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="16ae2-207">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="16ae2-207">Here is your resulting configuration.</span></span>
  
![适用于独立 SharePoint Online 团队网站的敏感级保护。](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="16ae2-209">现在可以对网站的资源安全地协作网站，通过一个访问组中的组成员资格的成员。</span><span class="sxs-lookup"><span data-stu-id="16ae2-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="16ae2-210">高度机密的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="16ae2-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="16ae2-211">高度机密的在线 SharePoint 工作组网站是独立的工作组站点，这意味着，通过而不是与工作组网站的 Office 365 组成员身份的 SharePoint 组中的成员身份控制权限。</span><span class="sxs-lookup"><span data-stu-id="16ae2-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="16ae2-212">若要创建高度机密信息和协作独立的工作组网站，有两个主要步骤。</span><span class="sxs-lookup"><span data-stu-id="16ae2-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="16ae2-213">第 1 步： 设计独立的站点</span><span class="sxs-lookup"><span data-stu-id="16ae2-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="16ae2-214">若要设计独立的工作组站点，您需要确定：</span><span class="sxs-lookup"><span data-stu-id="16ae2-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="16ae2-215">您的 SharePoint 组和权限级别。</span><span class="sxs-lookup"><span data-stu-id="16ae2-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="16ae2-216">将中的 SharePoint 组成员的访问组的组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="16ae2-217">访问组的推荐的设置是站点成员之一、 网站浏览者和站点管理员。</span><span class="sxs-lookup"><span data-stu-id="16ae2-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="16ae2-218">您是否使用嵌套组内访问组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="16ae2-219">例如，组建议的结构和权限级别，如下所示：</span><span class="sxs-lookup"><span data-stu-id="16ae2-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="16ae2-220">**SharePoint 组**</span><span class="sxs-lookup"><span data-stu-id="16ae2-220">**SharePoint group**</span></span>|<span data-ttu-id="16ae2-221">**权限级别**</span><span class="sxs-lookup"><span data-stu-id="16ae2-221">**Permission level**</span></span>|<span data-ttu-id="16ae2-222">**访问组 （示例）**</span><span class="sxs-lookup"><span data-stu-id="16ae2-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="16ae2-223">[站点名称]成员</span><span class="sxs-lookup"><span data-stu-id="16ae2-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="16ae2-224">编辑</span><span class="sxs-lookup"><span data-stu-id="16ae2-224">Edit</span></span>  <br/> |<span data-ttu-id="16ae2-225">[站点名称]成员</span><span class="sxs-lookup"><span data-stu-id="16ae2-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="16ae2-226">[站点名称]访问者</span><span class="sxs-lookup"><span data-stu-id="16ae2-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="16ae2-227">读取</span><span class="sxs-lookup"><span data-stu-id="16ae2-227">Read</span></span>  <br/> |<span data-ttu-id="16ae2-228">[站点名称]查看器</span><span class="sxs-lookup"><span data-stu-id="16ae2-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="16ae2-229">[站点名称]所有者</span><span class="sxs-lookup"><span data-stu-id="16ae2-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="16ae2-230">完全控制</span><span class="sxs-lookup"><span data-stu-id="16ae2-230">Full control</span></span>  <br/> |<span data-ttu-id="16ae2-231">[站点名称]管理员</span><span class="sxs-lookup"><span data-stu-id="16ae2-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="16ae2-p108">默认情况下，工作组站点创建 SharePoint 组和权限级别。您需要确定您访问权限的组的名称。</span><span class="sxs-lookup"><span data-stu-id="16ae2-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="16ae2-234">设计过程的详细信息，请参阅[设计独立的在线 SharePoint 工作组网站](design-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="16ae2-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="16ae2-235">步骤 2： 部署独立的站点</span><span class="sxs-lookup"><span data-stu-id="16ae2-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="16ae2-236">若要部署独立的网站，您首先需要：</span><span class="sxs-lookup"><span data-stu-id="16ae2-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="16ae2-237">确定每种访问组的用户和组成员</span><span class="sxs-lookup"><span data-stu-id="16ae2-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="16ae2-238">创建访问组并添加用户和组成员</span><span class="sxs-lookup"><span data-stu-id="16ae2-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="16ae2-239">创建使用访问组独立的团队站点</span><span class="sxs-lookup"><span data-stu-id="16ae2-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="16ae2-240">有关详细步骤，请参阅[部署独立的在线 SharePoint 工作组网站](deploy-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="16ae2-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="16ae2-241">权限设置的结果是：</span><span class="sxs-lookup"><span data-stu-id="16ae2-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="16ae2-242">**[网站名称] 所有者**SharePoint 组包含所有成员中具有**完全控制**权限级别的网站管理员访问组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="16ae2-243">**[站点名称] 成员**SharePoint 组包含所有成员中具有**编辑**权限级别的网站成员的访问组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="16ae2-244">**[站点名称] 访问**SharePoint 组包含所有成员中具有**读取**权限级别的网站查看器访问组。</span><span class="sxs-lookup"><span data-stu-id="16ae2-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="16ae2-245">邀请其他成员的成员的功能被禁用。</span><span class="sxs-lookup"><span data-stu-id="16ae2-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="16ae2-246">禁用非成员请求访问的能力。</span><span class="sxs-lookup"><span data-stu-id="16ae2-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="16ae2-247">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="16ae2-247">Here is your resulting configuration.</span></span>
  
![适用于独立 SharePoint Online 团队网站的高度机密级保护。](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="16ae2-249">现在可以对网站的资源安全地协作网站，通过一个访问组中的组成员资格的成员。</span><span class="sxs-lookup"><span data-stu-id="16ae2-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="16ae2-250">后续步骤</span><span class="sxs-lookup"><span data-stu-id="16ae2-250">Next step</span></span>

[<span data-ttu-id="16ae2-251">Office 365 标签和 DLP 与 SharePoint Online 文件保护</span><span class="sxs-lookup"><span data-stu-id="16ae2-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="16ae2-252">See Also</span><span class="sxs-lookup"><span data-stu-id="16ae2-252">See Also</span></span>

[<span data-ttu-id="16ae2-253">SharePoint Online 网站和文件保护</span><span class="sxs-lookup"><span data-stu-id="16ae2-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="16ae2-254">开发/测试环境中的安全 SharePoint Online 网站</span><span class="sxs-lookup"><span data-stu-id="16ae2-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="16ae2-255">为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南</span><span class="sxs-lookup"><span data-stu-id="16ae2-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="16ae2-256">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="16ae2-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




