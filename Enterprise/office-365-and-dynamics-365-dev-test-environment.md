---
title: Office 365 和 Dynamics 365 开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 摘要： 使用此测试实验室指南 Dynamics 365 添加到 Office 365 开发/测试环境。
ms.openlocfilehash: 00d5cc0fd347aff7e201056f6af9ca271008d285
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="e1682-103">Office 365 和 Dynamics 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="e1682-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="e1682-104">**摘要：** 使用此测试实验室指南 Dynamics 365 添加到 Office 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="e1682-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="e1682-105">使用本文中的说明进行操作，将 Dynamics 365 试用订阅作为 Office 365 开发/测试环境添加到同一个组织，创建一个 Office 365 和 Dynamics 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="e1682-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Office 365 和 Dynamics 365 开发/测试环境](images/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="e1682-p101">可将 Dynamics 365 试用订阅用于演示 Dynamics 365 的功能和特性。Dynamics 365 计划 1（企业版试用）包括以下解决方案：</span><span class="sxs-lookup"><span data-stu-id="e1682-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="e1682-p102">[Microsoft Dynamics 365 销售的](https://www.microsoft.com/dynamics365/sales)。增加自动化和数字智能帮助您保持重点和工作效率的销售人员与销售。</span><span class="sxs-lookup"><span data-stu-id="e1682-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="e1682-p103">[Microsoft Dynamics 365 客户服务](https://www.microsoft.com/dynamics365/customer-service)。通过授予您的代理的完整信息和提供无缝服务所需的数字智能获得会员。</span><span class="sxs-lookup"><span data-stu-id="e1682-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="e1682-p104">[Microsoft Dynamics 365 域服务](https://www.microsoft.com/dynamics365/field-service)。通过优化您计划、 安装您的员工，以及使用预测工具来提高利润主机服务呼叫。</span><span class="sxs-lookup"><span data-stu-id="e1682-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="e1682-p105">[Microsoft Dynamics 365 项目服务自动化](https://www.microsoft.com/en-us/dynamics365/project-service-automation)。成功完成项目并与提高生产效率的员工和智能工具创建利润关系。</span><span class="sxs-lookup"><span data-stu-id="e1682-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="e1682-117">可以浏览上述一个或多个网站以获取 Dynamics 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="e1682-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Microsoft 云中的测试实验室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="e1682-119">单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="e1682-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="e1682-120">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="e1682-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="e1682-121">如果您只想要测试 Office 365 和 Dynamics 365 轻型方式的最低要求，请在阶段 2 和 3 的[Office 365 开发/测试环境](office-365-dev-test-environment.md)按照的说明。</span><span class="sxs-lookup"><span data-stu-id="e1682-121">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="e1682-122">如果您想要用于模拟企业测试 Office 365 和 Dynamics 365，请按照[目录同步的 Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="e1682-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>

![Office 365 开发/测试环境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="e1682-p106">本文中的配置不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试 Office 365 和 Dynamics 365，并在代表典型组织的环境中对其进行试验。</span><span class="sxs-lookup"><span data-stu-id="e1682-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="e1682-126">第 2 阶段：添加 Dynamics 365 试用订阅</span><span class="sxs-lookup"><span data-stu-id="e1682-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="e1682-127">在此阶段，注册 Dynamics 365 试用订阅，并将其作为 Office 365 试用订阅添加到同一组织。</span><span class="sxs-lookup"><span data-stu-id="e1682-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="e1682-128">注册 Dynamics 365 试用订阅</span><span class="sxs-lookup"><span data-stu-id="e1682-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="e1682-129">在台式计算机 （轻型） 使用浏览器或从 CLIENT1 （模拟企业），登录到 Office 365 门户[https://portal.office.com](https://portal.office.com)的全局管理员帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="e1682-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="e1682-130">单击“管理”磁贴。</span><span class="sxs-lookup"><span data-stu-id="e1682-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="e1682-131">在**Office 管理中心**选项卡的的左侧窗格中，单击**帐单 > 购买服务**。</span><span class="sxs-lookup"><span data-stu-id="e1682-131">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="e1682-p107">在**购买服务**页上，找到**Dynamics 365 规划 1 Enterprise Edition**项目。将鼠标指针悬停在其上，单击**启动免费试用版**。</span><span class="sxs-lookup"><span data-stu-id="e1682-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="e1682-134">在“确认订单”页中，单击“立即试用”。</span><span class="sxs-lookup"><span data-stu-id="e1682-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="e1682-135">在“订单签收”页中，单击“继续”。</span><span class="sxs-lookup"><span data-stu-id="e1682-135">On the **Order receipt** page, click **Continue**.</span></span>

![Office 365 和 Dynamics 365 开发/测试环境](images/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="e1682-p108">Dynamics 365 计划 1 企业版订阅试用期是 30 天。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。</span><span class="sxs-lookup"><span data-stu-id="e1682-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="e1682-140">第 3 阶段：分配 Dynamics 365 许可证和系统管理员</span><span class="sxs-lookup"><span data-stu-id="e1682-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="e1682-141">在此阶段中，将 Dynamics 365 许可证分配给全局管理员、用户 2 和用户 3 的帐户并使之成为系统管理员。</span><span class="sxs-lookup"><span data-stu-id="e1682-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="e1682-142">使用下列步骤分配 Dynamics 365 许可证。</span><span class="sxs-lookup"><span data-stu-id="e1682-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="e1682-143">在**Office 管理中心**选项卡上单击**用户 > 活动用户**。</span><span class="sxs-lookup"><span data-stu-id="e1682-143">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="e1682-144">在活动用户的列表中，单击您的全局管理员帐户，然后单击**产品**许可证的**编辑**。</span><span class="sxs-lookup"><span data-stu-id="e1682-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="e1682-145">**产品许可证**窗格中，打开产品许可证**Dynamics 365 规划 1 Enterprise Edition**到**上**，单击**保存**，然后单击**关闭**两次。</span><span class="sxs-lookup"><span data-stu-id="e1682-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="e1682-146">为用户 2 和用户 3 的帐户执行步骤 2 和步骤 3。</span><span class="sxs-lookup"><span data-stu-id="e1682-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="e1682-147">关闭**Office 管理中心**选项卡。</span><span class="sxs-lookup"><span data-stu-id="e1682-147">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="e1682-148">使用以下步骤将用户 2 和用户 3 的帐户配置为 Dynamics 365 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="e1682-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="e1682-149">从**Microsoft Office Home**选项卡，单击**管理**。</span><span class="sxs-lookup"><span data-stu-id="e1682-149">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="e1682-150">**Office Admin center**选项卡上的的左侧窗格中，单击**管理中心**，，然后单击**Dynamics 365**。</span><span class="sxs-lookup"><span data-stu-id="e1682-150">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="e1682-151">可能需要等到 Dynamics 365 完成预配后，菜单中才会显示 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="e1682-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="e1682-152">在 Dynamics 365 选项卡上，单击**所有这些**，，然后单击**完成安装。**</span><span class="sxs-lookup"><span data-stu-id="e1682-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="e1682-153">等待设置完成。</span><span class="sxs-lookup"><span data-stu-id="e1682-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="e1682-p109">安装完成后，它会显示基于示例数据的一部分的线索订阅销售活动仪表板。花一些时间，以查看**欢迎您的试用版**视频。关闭视频窗口完成后。</span><span class="sxs-lookup"><span data-stu-id="e1682-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="e1682-157">在顶部工具栏中，单击**销售**旁边的向下箭头，单击**设置**，然后单击**安全**。</span><span class="sxs-lookup"><span data-stu-id="e1682-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="e1682-158">在**安全性**页上，单击**用户**。</span><span class="sxs-lookup"><span data-stu-id="e1682-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="e1682-159">在用户的列表中，单击**用户 2**。</span><span class="sxs-lookup"><span data-stu-id="e1682-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="e1682-160">在工具栏中，单击**管理角色**。</span><span class="sxs-lookup"><span data-stu-id="e1682-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="e1682-161">**管理角色**中,，单击**系统管理员联系**，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="e1682-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="e1682-162">在顶部工具栏中单击**安全性**。</span><span class="sxs-lookup"><span data-stu-id="e1682-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="e1682-163">为用户 3 帐户重复步骤 5 到 8。</span><span class="sxs-lookup"><span data-stu-id="e1682-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="e1682-164">关闭**用户： User3**选项卡。</span><span class="sxs-lookup"><span data-stu-id="e1682-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="e1682-165">已为 Office 365 全局管理员帐户自动分配了 Dynamics 365 系统管理员角色。</span><span class="sxs-lookup"><span data-stu-id="e1682-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="e1682-166">现在，你的 Office 365 和 Dynamics 365 开发/测试环境包含：</span><span class="sxs-lookup"><span data-stu-id="e1682-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="e1682-167">与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版和 Dynamics 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="e1682-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="e1682-168">全局企业管理员、用户 2 和用户 3 的帐户都可以使用 Office 365 E5 企业版和 Dynamics 365，并且它们都是 Dynamics 365 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="e1682-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="e1682-169">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e1682-169">Next step</span></span>

<span data-ttu-id="e1682-170">配置，然后说明如何 Office 365 和 Dynamics 365 结合使用[Office 365 和 Dynamics 365 开发/测试环境](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)的 Exchange Online 集成在 Exchange Online 邮箱。</span><span class="sxs-lookup"><span data-stu-id="e1682-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e1682-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1682-171">See Also</span></span>

[<span data-ttu-id="e1682-172">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="e1682-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="e1682-173">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="e1682-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="e1682-174">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="e1682-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="e1682-175">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="e1682-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="e1682-176">Dynamics 365（联机）的订阅管理</span><span class="sxs-lookup"><span data-stu-id="e1682-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="e1682-177">管理 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="e1682-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


