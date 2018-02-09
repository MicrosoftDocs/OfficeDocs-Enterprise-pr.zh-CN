---
title: "在政治运动的开发/测试环境中创建工作组网站"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "摘要： 政治市场开发/测试环境中创建公共、 私人、 敏感和高度机密 SharePoint Online 的工作组网站。"
ms.openlocfilehash: cc410dc98e37ca6fc0e96f00f413e57ba1958d50
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="49d58-103">在政治运动的开发/测试环境中创建工作组网站</span><span class="sxs-lookup"><span data-stu-id="49d58-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="49d58-104">**摘要：**政治市场开发/测试环境中创建公共、 私人、 敏感和高度机密 SharePoint Online 的工作组网站。</span><span class="sxs-lookup"><span data-stu-id="49d58-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="49d58-p101">使用本文中的说明进行操作以创建[Microsoft 安全指南为政治运动、 非营利性组织和其他的敏捷组织](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)在包括四个不同类型的联机 SharePoint 工作组网站的开发/测试环境解决方案。这些站点上主题 10，题为**SharePoint 和 OneDrive 业务的**详细介绍。</span><span class="sxs-lookup"><span data-stu-id="49d58-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="49d58-107">阶段 1： 创建您的政治运动的开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="49d58-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="49d58-108">首先，按照[配置组和用户对于政治市场开发/测试环境](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)中的说明进行操作，以创建您的订阅、 用户和组。</span><span class="sxs-lookup"><span data-stu-id="49d58-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="49d58-109">第 2 阶段： 创建 Office 365 的标签</span><span class="sxs-lookup"><span data-stu-id="49d58-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="49d58-110">在此阶段中，您创建的标签进行不同级别的 SharePoint Online 团队站点文档文件夹的安全性。</span><span class="sxs-lookup"><span data-stu-id="49d58-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="49d58-p102">如果需要请登录到您的订购试用期的全局管理员帐户的凭据对 Office 365 门户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="49d58-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="49d58-113">**Microsoft Office 主页**选项卡中，单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="49d58-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="49d58-114">您的浏览器的新**办公室管理中心**标签，请单击**中心管理 > 安全&amp;法规遵从性**。</span><span class="sxs-lookup"><span data-stu-id="49d58-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="49d58-115">从新**家庭-安全&amp;法规遵从性**选项卡上的浏览器中，单击**分类 > 标签**。</span><span class="sxs-lookup"><span data-stu-id="49d58-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="49d58-116">从**主页 > 标签**窗格中，单击**创建一个标签**。</span><span class="sxs-lookup"><span data-stu-id="49d58-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="49d58-117">在**标签名称**窗格中**内部**，键入，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="49d58-118">在**标签设置**窗格中，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="49d58-119">上的**查看设置**窗格中，单击**创建此标签**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="49d58-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="49d58-120">这些附加的标签，请重复步骤 5 到 8:</span><span class="sxs-lookup"><span data-stu-id="49d58-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="49d58-121">专用</span><span class="sxs-lookup"><span data-stu-id="49d58-121">Private</span></span>
    
  - <span data-ttu-id="49d58-122">敏感</span><span class="sxs-lookup"><span data-stu-id="49d58-122">Sensitive</span></span>
    
  - <span data-ttu-id="49d58-123">高度机密</span><span class="sxs-lookup"><span data-stu-id="49d58-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="49d58-124">从**主页 > 标签**窗格中，单击**发布标签**。</span><span class="sxs-lookup"><span data-stu-id="49d58-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="49d58-125">在**选择要发布的标签**窗格上，单击**发布选择标志**。</span><span class="sxs-lookup"><span data-stu-id="49d58-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="49d58-126">在**选择标签**窗格中，单击**添加**，选择所有四个标签。</span><span class="sxs-lookup"><span data-stu-id="49d58-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="49d58-127">单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="49d58-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="49d58-128">在**选择要发布的标签**窗格上，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="49d58-129">在**选择位置**窗格中，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="49d58-130">在**您的策略名称**窗格中，在**名称**中键入**市场**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="49d58-131">上的**查看设置**窗格中，单击**发布标签**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="49d58-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="49d58-132">阶段 3： 创建 SharePoint Online 团队站点</span><span class="sxs-lookup"><span data-stu-id="49d58-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="49d58-133">在此阶段中，您创建和政治市场对应于四种类型的 SharePoint Online 工作组站点配置 SharePoint Online 的工作组网站。</span><span class="sxs-lookup"><span data-stu-id="49d58-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="49d58-134">市场活动范围工作组站点</span><span class="sxs-lookup"><span data-stu-id="49d58-134">Campaign wide team site</span></span>

<span data-ttu-id="49d58-135">要创建基准公共联机 SharePoint 工作组网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="49d58-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="49d58-136">如果需要请使用本地计算机上的浏览器，然后登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用您的全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="49d58-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="49d58-137">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="49d58-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="49d58-138">在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="49d58-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="49d58-139">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="49d58-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="49d58-140">在**站点名称**输入**市场活动范围**。</span><span class="sxs-lookup"><span data-stu-id="49d58-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="49d58-141">在**团队站点的说明**中，键入**整个市场的 SharePoint 网站**。</span><span class="sxs-lookup"><span data-stu-id="49d58-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="49d58-142">在**隐私设置**选择**公用-组织中的任何人都可以访问该网站**，，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="49d58-143">在**谁您想要添加？**窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="49d58-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="49d58-144">接下来，配置内部标签市场宽工作组网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="49d58-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="49d58-145">在浏览器的**市场活动范围内开始**选项卡上，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="49d58-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="49d58-146">单击设置图标，然后单击**库设置**。</span><span class="sxs-lookup"><span data-stu-id="49d58-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="49d58-147">在**权限和管理**，请单击**应用于此库中的项目的标签**。</span><span class="sxs-lookup"><span data-stu-id="49d58-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="49d58-148">在**设置应用标签**，选择**内部**，，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="49d58-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="49d58-149">市场活动项目 1 小组站点</span><span class="sxs-lookup"><span data-stu-id="49d58-149">Campaign project 1 team site</span></span>

<span data-ttu-id="49d58-150">若要创建比较基准专用 SharePoint 联机工作组网站的宣传活动中的一个项目，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="49d58-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="49d58-151">如果需要请使用本地计算机上的浏览器，然后登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用您的全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="49d58-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="49d58-152">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="49d58-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="49d58-153">在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="49d58-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="49d58-154">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="49d58-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="49d58-155">在**站点名称**输入**市场活动项目 1**。</span><span class="sxs-lookup"><span data-stu-id="49d58-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="49d58-156">在**团队站点的说明，**键入**市场活动项目 1 的 SharePoint 网站**。</span><span class="sxs-lookup"><span data-stu-id="49d58-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="49d58-157">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="49d58-158">在**谁您想要添加？**窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="49d58-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="49d58-159">接下来，配置专用的标签市场活动项目 1 工作组网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="49d58-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="49d58-160">在浏览器的**市场活动项目 1-主页**选项卡上，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="49d58-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="49d58-161">单击设置图标，然后单击**库设置**。</span><span class="sxs-lookup"><span data-stu-id="49d58-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="49d58-162">在**权限和管理**，请单击**应用于此库中的项目的标签**。</span><span class="sxs-lookup"><span data-stu-id="49d58-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="49d58-163">在**设置应用标签**，选择**专用**，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="49d58-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="49d58-164">市场活动的市场营销团队站点</span><span class="sxs-lookup"><span data-stu-id="49d58-164">Campaign marketing team site</span></span>

<span data-ttu-id="49d58-165">若要创建区分级别独立的 SharePoint Online 工作组站点的市场营销资源，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="49d58-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="49d58-166">在您的本地计算机上使用浏览器，登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用您的全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="49d58-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="49d58-167">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="49d58-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="49d58-168">在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="49d58-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="49d58-169">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="49d58-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="49d58-170">在**团队站点名称**框中，键入**市场营销**。</span><span class="sxs-lookup"><span data-stu-id="49d58-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="49d58-171">在**团队站点的说明**中，键入**SharePoint 站点的市场营销 （敏感）**。</span><span class="sxs-lookup"><span data-stu-id="49d58-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="49d58-172">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="49d58-173">在**谁您想要添加？**窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="49d58-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="49d58-174">在您的浏览器工具条中，在新的**市场营销**选项卡上单击设置图标，然后单击**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="49d58-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="49d58-175">在**网站权限**窗格中，单击**高级的权限设置**。</span><span class="sxs-lookup"><span data-stu-id="49d58-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="49d58-176">在新**权限**选项卡浏览器中，单击**访问请求设置**。</span><span class="sxs-lookup"><span data-stu-id="49d58-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="49d58-177">在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**和**允许成员若要邀请其他人到网站用户组成员**复选框，键入**ITAdmin1 @** <your organization name> **。onmicrosoft.com**在**将所有访问请求都发送**，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="49d58-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="49d58-178">单击列表中的**成员的市场营销的市场活动**。</span><span class="sxs-lookup"><span data-stu-id="49d58-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="49d58-179">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="49d58-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="49d58-180">在**共享**对话框中，键入**高级和战略性工作人员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="49d58-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="49d58-181">**分析人员**组和**Regular1**的用户帐户，请重复步骤 14 和 15。</span><span class="sxs-lookup"><span data-stu-id="49d58-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="49d58-182">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="49d58-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="49d58-183">单击列表中的**市场营销的所有者**。</span><span class="sxs-lookup"><span data-stu-id="49d58-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="49d58-184">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="49d58-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="49d58-185">在**共享**对话框中，键入**的 IT 人员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="49d58-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="49d58-186">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="49d58-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="49d58-187">关闭您的浏览器中的**用户和用户组**选项卡，单击您的浏览器中的**市场营销总部**选项卡，然后关闭**网站权限**窗格。</span><span class="sxs-lookup"><span data-stu-id="49d58-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="49d58-188">下面介绍了权限配置结果：</span><span class="sxs-lookup"><span data-stu-id="49d58-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="49d58-189">**市场营销成员**SharePoint 组包含只有**高级和战略性工作人员**组 （其中包含的候选、 ChiefOfStaff 和 Strategic1 的用户帐户），**市场营销**组 (其中包含全局管理员用户帐户），**分析人员**组 （其中包含 DataScientist1 用户帐户），和**Regular1**的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="49d58-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="49d58-190">**市场营销负责人**SharePoint 组包含仅**IT staff**组 （其中包含仅 ITAdmin1 和 ITAdmin2 用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="49d58-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="49d58-191">**市场营销者**SharePoint 组包含任何组或用户帐户。</span><span class="sxs-lookup"><span data-stu-id="49d58-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="49d58-192">成员不能修改网站级别的权限 （这只可以通过**市场营销所有者**组的成员）。</span><span class="sxs-lookup"><span data-stu-id="49d58-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="49d58-193">其他用户帐户无法访问网站或它的资源，但可以请求访问该网站，将电子邮件发送给 ITAdmin1 用户帐户邮箱。</span><span class="sxs-lookup"><span data-stu-id="49d58-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="49d58-194">接下来，配置敏感标签的市场营销团队站点的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="49d58-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="49d58-195">在您的浏览器的**市场营销总部**选项卡上，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="49d58-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="49d58-196">单击设置图标，然后单击**库设置**。</span><span class="sxs-lookup"><span data-stu-id="49d58-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="49d58-197">在**权限和管理**，请单击**应用于此库中的项目的标签**。</span><span class="sxs-lookup"><span data-stu-id="49d58-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="49d58-198">在**设置应用标签**，选择**敏感**，，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="49d58-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="49d58-p103">接下来，将它们与组织外部的敏感标签共享联机 SharePoint 工作组网站上的文档时通知用户的数据丢失防护 (DLP) 策略的配置。这个 DLP 策略将应用于市场营销站点中的资源。</span><span class="sxs-lookup"><span data-stu-id="49d58-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="49d58-201">从**Microsoft Office 主页**选项卡上的在浏览器中，单击**安全&amp;法规遵从性**平铺。</span><span class="sxs-lookup"><span data-stu-id="49d58-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="49d58-202">对新**安全&amp;法规遵从性**在您的浏览器选项卡上，单击**数据丢失防范 > 策略**。</span><span class="sxs-lookup"><span data-stu-id="49d58-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="49d58-203">在**数据丢失防范**窗格中，单击**+ 创建策略**。</span><span class="sxs-lookup"><span data-stu-id="49d58-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="49d58-204">在**从模板开始创建自定义策略或**窗格中，单击**自定义**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="49d58-205">**名称您的策略**中，在**名称**中键入**敏感标签 SharePoint Online 工作组站点**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="49d58-206">在**选择位置**窗格中，**让我来选择特定的位置**，请单击，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="49d58-207">在位置列表中，禁用**Exchange 电子邮件**帐户和**OneDrive 帐户**位置，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="49d58-208">在**自定义类型您想要保护的敏感信息**窗格中，单击**编辑**。</span><span class="sxs-lookup"><span data-stu-id="49d58-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="49d58-209">在**选择要保护的内容的类型**窗格中，单击下拉列表框中，**添加**，然后单击**标签**。</span><span class="sxs-lookup"><span data-stu-id="49d58-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="49d58-210">在**标签**窗格中，单击**+ 添加**，选择**敏感**标签，单击**添加**，然后单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="49d58-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="49d58-211">在**选择要保护的内容的类型**窗格中，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="49d58-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="49d58-212">在**自定义类型您想要保护的敏感信息**窗格中，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="49d58-213">在**您想要我们检测敏感信息办？**窗格中，单击**自定义提示和电子邮件**。</span><span class="sxs-lookup"><span data-stu-id="49d58-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="49d58-214">在**自定义策略的提示和电子邮件通知**窗格中，单击**自定义策略提示文本**。</span><span class="sxs-lookup"><span data-stu-id="49d58-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="49d58-215">在文本框中，键入或粘贴以下：</span><span class="sxs-lookup"><span data-stu-id="49d58-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="49d58-p104">若要与组织外部的用户共享，下载该文件，然后将其打开。单击文件然后保护文档，然后使用密码加密和再指定一个强密码。在另一个电子邮件或其他通讯手段发送密码。</span><span class="sxs-lookup"><span data-stu-id="49d58-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="49d58-219">单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="49d58-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="49d58-220">在**您想要我们检测敏感信息办？**窗格中，清除**阻止某些人共享，并限制对内容的访问**复选框，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="49d58-221">在**所需的策略或测试的事情，首先打开？**窗格中，单击**是，立即启用**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="49d58-222">在**查看设置**窗格上，单击**创建**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="49d58-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="49d58-223">市场战略工作组网站</span><span class="sxs-lookup"><span data-stu-id="49d58-223">Campaign strategy team site</span></span>

<span data-ttu-id="49d58-224">以市场战略资源的高度机密级别创建独立的在线 SharePoint 工作组网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="49d58-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="49d58-225">如果需要请使用本地计算机上的浏览器，然后登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用您的全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="49d58-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="49d58-226">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="49d58-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="49d58-227">在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="49d58-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="49d58-228">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="49d58-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="49d58-229">在**团队站点名称**，键入**市场策略**。</span><span class="sxs-lookup"><span data-stu-id="49d58-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="49d58-230">在**团队站点的说明**中，键入**SharePoint 网站上 （高度机密） 的市场战略**。</span><span class="sxs-lookup"><span data-stu-id="49d58-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="49d58-231">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="49d58-232">在**谁您想要添加？**窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="49d58-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="49d58-233">在您的浏览器工具条中，在新的**市场策略**选项卡上单击设置图标，然后单击**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="49d58-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="49d58-234">在**网站权限**窗格中，单击**高级的权限设置**。</span><span class="sxs-lookup"><span data-stu-id="49d58-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="49d58-235">在新**权限**选项卡浏览器中，单击**访问请求设置**。</span><span class="sxs-lookup"><span data-stu-id="49d58-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="49d58-236">在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**，并**允许成员要邀请到网站的成员组的其他人**（以便所有三个复选框都被清除），然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="49d58-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="49d58-237">单击列表中的**成员的市场策略**。</span><span class="sxs-lookup"><span data-stu-id="49d58-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="49d58-238">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="49d58-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="49d58-239">在**共享**对话框中，键入**高级和战略性工作人员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="49d58-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="49d58-240">单击列表中的**活动策略的所有者**。</span><span class="sxs-lookup"><span data-stu-id="49d58-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="49d58-241">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="49d58-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="49d58-242">在**共享**对话框中，键入**的 IT 人员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="49d58-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="49d58-243">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="49d58-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="49d58-244">关闭您的浏览器中的**用户和用户组**选项卡，单击您的浏览器中的**市场战略总部**选项卡，然后关闭**网站权限**窗格。</span><span class="sxs-lookup"><span data-stu-id="49d58-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="49d58-245">下面介绍了权限配置结果：</span><span class="sxs-lookup"><span data-stu-id="49d58-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="49d58-246">**市场策略成员**SharePoint 组包含仅**高级和战略性工作人员**组 （其中包含只候选、 ChiefOfStaff 和 Strategic1 用户帐户） 和**市场战略**组 （其中包含只有全局管理员用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="49d58-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="49d58-247">**市场策略所有者**SharePoint 组包含仅**IT staff**组 （其中包含仅 ITAdmin1 和 ITAdmin2 用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="49d58-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="49d58-248">**市场策略访问**SharePoint 组包含任何组或用户帐户。</span><span class="sxs-lookup"><span data-stu-id="49d58-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="49d58-249">成员不能修改网站级别的权限 （这只可以通过**市场策略所有者**组的成员）。</span><span class="sxs-lookup"><span data-stu-id="49d58-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="49d58-p105">其他用户帐户无法访问该站点或其资源或请求访问该网站。必须由全局管理员或**市场策略所有者**组的成员对网站的其他权限。</span><span class="sxs-lookup"><span data-stu-id="49d58-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="49d58-252">接下来，配置为高度机密的标签市场战略工作组网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="49d58-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="49d58-253">在您的浏览器的**市场战略总部**选项卡上，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="49d58-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="49d58-254">单击设置图标，然后单击**库设置**。</span><span class="sxs-lookup"><span data-stu-id="49d58-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="49d58-255">在**权限和管理**，请单击**应用于此库中的项目的标签**。</span><span class="sxs-lookup"><span data-stu-id="49d58-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="49d58-256">在**设置应用标签**，选择**高度机密**，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="49d58-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="49d58-p106">当它们与组织外部的标签高度机密共享联机 SharePoint 工作组网站上的文档，接下来，配置 DLP 策略阻止用户。这个 DLP 策略将应用于市场活动战略站点中的资源。</span><span class="sxs-lookup"><span data-stu-id="49d58-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="49d58-259">如果需要请使用本地计算机上的浏览器，到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 拥有安全管理员或公司管理员角色的帐户登录。</span><span class="sxs-lookup"><span data-stu-id="49d58-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="49d58-260">从**Microsoft Office 主页**选项卡上的在浏览器中，单击**安全&amp;法规遵从性**平铺。</span><span class="sxs-lookup"><span data-stu-id="49d58-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="49d58-261">对新**安全&amp;法规遵从性**在您的浏览器选项卡上，单击**数据丢失防范 > 策略**。</span><span class="sxs-lookup"><span data-stu-id="49d58-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="49d58-262">在**数据丢失防范**窗格中，单击**+ 创建策略**。</span><span class="sxs-lookup"><span data-stu-id="49d58-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="49d58-263">在**从模板开始创建自定义策略或**窗格中，单击**自定义**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="49d58-264">**名称您的策略**中，在**名称**中键入**高度机密的标签 SharePoint Online 工作组站点**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="49d58-265">在**选择位置**窗格中，**让我来选择特定的位置**，请单击，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="49d58-266">在位置列表中，禁用**Exchange 电子邮件**帐户和**OneDrive 帐户**位置，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="49d58-267">在**自定义类型您想要保护的敏感信息**窗格中，单击**编辑**。</span><span class="sxs-lookup"><span data-stu-id="49d58-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="49d58-268">在**选择要保护的内容的类型**窗格中，单击下拉列表框中，**添加**，然后单击**标签**。</span><span class="sxs-lookup"><span data-stu-id="49d58-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="49d58-269">**标签**的窗格中，单击**+ 添加**，选择**高度机密**标签，单击**添加**，然后单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="49d58-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="49d58-270">在**选择要保护的内容的类型**窗格中，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="49d58-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="49d58-271">在**自定义类型您想要保护的敏感信息**窗格中，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="49d58-272">在**您想要我们检测敏感信息办？**窗格中，单击**自定义提示和电子邮件**。</span><span class="sxs-lookup"><span data-stu-id="49d58-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="49d58-273">在**自定义策略的提示和电子邮件通知**窗格中，单击**自定义策略提示文本**。</span><span class="sxs-lookup"><span data-stu-id="49d58-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="49d58-274">在文本框中，键入或粘贴以下：</span><span class="sxs-lookup"><span data-stu-id="49d58-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="49d58-p107">若要与组织外部的用户共享，下载该文件，然后将其打开。单击文件然后保护文档，然后使用密码加密和再指定一个强密码。在另一个电子邮件或其他通讯手段发送密码。</span><span class="sxs-lookup"><span data-stu-id="49d58-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="49d58-278">单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="49d58-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="49d58-279">在**您想要我们检测敏感信息办？**窗格中，选择**需要重写的理由**，然后再单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="49d58-280">在**所需的策略或测试的事情，首先打开？**窗格中，单击**是，立即启用**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="49d58-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="49d58-281">在**查看设置**窗格上，单击**创建**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="49d58-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="49d58-282">在[Office 365 管理中心激活 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)使用的说明。</span><span class="sxs-lookup"><span data-stu-id="49d58-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="49d58-283">接下来，使用一个指定了作用域的新策略和子标签保护和权限与以下步骤配置 Azure 信息保护：</span><span class="sxs-lookup"><span data-stu-id="49d58-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="49d58-p108">Office 365 门户拥有安全管理员或公司管理员角色的帐户登录。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="49d58-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="49d58-286">在浏览器的单独的选项卡，请转到 Azure 门户网站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="49d58-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="49d58-287">如果这是首次配置 Azure 信息保护，请参见以下[说明](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="49d58-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="49d58-288">在列表窗格中，单击**更多服务**，键入**信息**，，然后单击**Azure 信息保护**。</span><span class="sxs-lookup"><span data-stu-id="49d58-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="49d58-289">**Azure 信息保护**刀片式服务器，，单击**范围策略 > 添加新策略 +**。</span><span class="sxs-lookup"><span data-stu-id="49d58-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="49d58-290">键入**策略的名称**和**标签市场战略工作组网站中的文档****说明**在**CampaignStrategy** 。</span><span class="sxs-lookup"><span data-stu-id="49d58-290">Type **CampaignStrategy** in **Policy name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="49d58-291">单击**选择哪些用户或组获取该策略 > 用户/用户组**，然后选择**高级和战略性的员工**。</span><span class="sxs-lookup"><span data-stu-id="49d58-291">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
8. <span data-ttu-id="49d58-292">单击**选择 > 确定**。</span><span class="sxs-lookup"><span data-stu-id="49d58-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="49d58-293">**高度机密**的标签，请单击省略号 （...），然后单击**添加子标签**。</span><span class="sxs-lookup"><span data-stu-id="49d58-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="49d58-294">键入**名称**和说明中**说明**的标签的子标签的名称。</span><span class="sxs-lookup"><span data-stu-id="49d58-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="49d58-295">在**设置权限的文档和电子邮件包含此标签**，请单击**保护**。</span><span class="sxs-lookup"><span data-stu-id="49d58-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="49d58-296">在**保护**部分中，单击**Azure （云键）**。</span><span class="sxs-lookup"><span data-stu-id="49d58-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="49d58-297">在**保护**刀片式服务器下**保护设置**，, 单击**+ 添加权限**。</span><span class="sxs-lookup"><span data-stu-id="49d58-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="49d58-298">**添加权限**刀片式服务器，在**指定用户和组**，请单击**+ 浏览目录**。</span><span class="sxs-lookup"><span data-stu-id="49d58-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="49d58-299">在**AAD 的用户和组**窗格中，选择**高级和战略性工作人员**，然后单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="49d58-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="49d58-300">在**选择权限从预设**清除**打印**、**复制和内容的提取**和**转发**复选框。</span><span class="sxs-lookup"><span data-stu-id="49d58-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="49d58-301">单击**确定**两次。</span><span class="sxs-lookup"><span data-stu-id="49d58-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="49d58-302">在**子标签**刀片式服务器，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="49d58-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="49d58-303">关闭新的指定了作用域的策略刀片。</span><span class="sxs-lookup"><span data-stu-id="49d58-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="49d58-304">在**Azure 信息保护的指定了作用域策略**刀片式服务器，单击**发布**，然后单击**是**。</span><span class="sxs-lookup"><span data-stu-id="49d58-304">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="49d58-305">现在您就可以开始在以下四个网站中创建文档，并测试您的订购试用期对它们与不同的用户帐户的访问。</span><span class="sxs-lookup"><span data-stu-id="49d58-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="49d58-306">要保护与 Azure 的信息保护和此新的标签文档，则必须在测试机器上[安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)、 从 Office 365 管理门户安装 Office，**中的帐户然后登录从 Microsoft Word高级和战略人员**组您的订购试用期。</span><span class="sxs-lookup"><span data-stu-id="49d58-306">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="49d58-307">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49d58-307">See Also</span></span>

[<span data-ttu-id="49d58-308">为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南</span><span class="sxs-lookup"><span data-stu-id="49d58-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="49d58-309">配置组和用户对于政治市场开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="49d58-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="49d58-310">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="49d58-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="49d58-311">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="49d58-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




