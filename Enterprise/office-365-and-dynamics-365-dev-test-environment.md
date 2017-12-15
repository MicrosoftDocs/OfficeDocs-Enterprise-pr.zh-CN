---
title: "Office 365 和 Dynamics 365 开发/测试环境"
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
- jan17entnews
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: "摘要： 使用此测试实验室指南 Dynamics 365 添加到 Office 365 开发/测试环境。"
ms.openlocfilehash: 49648dd357d23eaee2d08d35252e18edf6a5d2ec
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="13127-103">Office 365 和 Dynamics 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="13127-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="13127-104">**摘要：**此测试实验室指南用于 Dynamics 365 添加到 Office 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="13127-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="13127-105">使用本文中的说明进行操作，将 Dynamics 365 试用订阅作为 Office 365 开发/测试环境添加到同一个组织，创建一个 Office 365 和 Dynamics 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="13127-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
<span data-ttu-id="13127-p101">可将 Dynamics 365 试用订阅用于演示 Dynamics 365 的功能和特性。Dynamics 365 计划 1（企业版试用）包括以下解决方案：</span><span class="sxs-lookup"><span data-stu-id="13127-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="13127-p102">[Microsoft Dynamics 365 的销售](https://www.microsoft.com/dynamics365/sales)。提高您的销售自动化和数字智能帮助您的销售人员，将主要精力和更智能地工作。</span><span class="sxs-lookup"><span data-stu-id="13127-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="13127-p103">[Microsoft Dynamics 365 为客户服务](https://www.microsoft.com/dynamics365/customer-service)。通过为您的代理的完整信息和数字智能所需提供无缝服务获得会员。</span><span class="sxs-lookup"><span data-stu-id="13127-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="13127-p104">[Microsoft Dynamics 365 的现场服务](https://www.microsoft.com/dynamics365/field-service)。主服务调用通过优化您的日程，安装企业员工，使用预防性工具来增加利润。</span><span class="sxs-lookup"><span data-stu-id="13127-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="13127-p105">[Microsoft Dynamics 365 项目服务自动化的](https://www.microsoft.com/en-us/dynamics365/project-service-automation)。成功地完成您的项目和员工工作效率和智能工具创建有利的关系。</span><span class="sxs-lookup"><span data-stu-id="13127-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="13127-116">可以浏览上述一个或多个网站以获取 Dynamics 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="13127-116">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Microsoft 云中的测试实验室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="13127-118">单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="13127-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="13127-119">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="13127-119">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="13127-120">如果您只想测试中达到最低要求的轻量级方法 Office 365 和 Dynamics 365，按照在阶段 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="13127-120">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="13127-121">如果您想要测试 Office 365 和 Dynamics 365 模拟的企业，按照[目录同步为您 Office 365 的开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="13127-121">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="13127-p106">本文中的配置不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试 Office 365 和 Dynamics 365，并在代表典型组织的环境中对其进行试验。</span><span class="sxs-lookup"><span data-stu-id="13127-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="13127-124">第 2 阶段：添加 Dynamics 365 试用订阅</span><span class="sxs-lookup"><span data-stu-id="13127-124">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="13127-125">在此阶段，注册 Dynamics 365 试用订阅，并将其作为 Office 365 试用订阅添加到同一组织。</span><span class="sxs-lookup"><span data-stu-id="13127-125">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="13127-126">注册 Dynamics 365 试用订阅</span><span class="sxs-lookup"><span data-stu-id="13127-126">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="13127-127">台式计算机 （轻型） 上使用浏览器或客户端 1 （模拟企业），到 Office 365 门户网站位于[https://portal.office.com](https://portal.office.com)的全局管理员帐户凭据登录。</span><span class="sxs-lookup"><span data-stu-id="13127-127">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="13127-128">单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="13127-128">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="13127-129">**办公室管理中心**选项卡上，左边的导航，请单击**计费 > 购买服务**。</span><span class="sxs-lookup"><span data-stu-id="13127-129">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="13127-p107">**购买服务**页上找到**Dynamics 365 计划 1 企业版**项目。将鼠标指针悬停在其上，单击**启动免费试用版**。</span><span class="sxs-lookup"><span data-stu-id="13127-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="13127-132">在**确认订单**页中，单击**立即尝试**。</span><span class="sxs-lookup"><span data-stu-id="13127-132">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="13127-133">在**订单收据**页上，单击**继续**。</span><span class="sxs-lookup"><span data-stu-id="13127-133">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="13127-p108">Dynamics 365 计划 1 企业版订阅试用期是 30 天。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。</span><span class="sxs-lookup"><span data-stu-id="13127-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="13127-137">第 3 阶段：分配 Dynamics 365 许可证和系统管理员</span><span class="sxs-lookup"><span data-stu-id="13127-137">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="13127-138">在此阶段中，将 Dynamics 365 许可证分配给全局管理员、用户 2 和用户 3 的帐户并使之成为系统管理员。</span><span class="sxs-lookup"><span data-stu-id="13127-138">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="13127-139">使用下列步骤分配 Dynamics 365 许可证。</span><span class="sxs-lookup"><span data-stu-id="13127-139">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="13127-140">在**Office 管理员中心**选项卡，单击**用户 > 活动用户**。</span><span class="sxs-lookup"><span data-stu-id="13127-140">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="13127-141">在活动的用户的列表中，单击您的全局管理员帐户，然后单击**编辑****产品**许可证。</span><span class="sxs-lookup"><span data-stu-id="13127-141">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="13127-142">在**产品许可证**窗格中**Dynamics 365 计划 1 企业版**对**上**打开产品许可证、 单击**保存**，然后两次单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="13127-142">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="13127-143">为用户 2 和用户 3 的帐户执行步骤 2 和步骤 3。</span><span class="sxs-lookup"><span data-stu-id="13127-143">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="13127-144">关闭**Office 管理员中心**选项卡。</span><span class="sxs-lookup"><span data-stu-id="13127-144">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="13127-145">使用以下步骤将用户 2 和用户 3 的帐户配置为 Dynamics 365 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="13127-145">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="13127-146">从**Microsoft Office 主页**选项卡上，单击**管理**。</span><span class="sxs-lookup"><span data-stu-id="13127-146">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="13127-147">**Office 管理中心**选项卡上，在左边的导航**中心管理**，请单击，然后单击**Dynamics 365**。</span><span class="sxs-lookup"><span data-stu-id="13127-147">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="13127-148">可能需要等到 Dynamics 365 完成预配后，菜单中才会显示 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="13127-148">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="13127-149">Dynamics 365 选项卡上，单击**所有这些**，然后单击**完成安装。**</span><span class="sxs-lookup"><span data-stu-id="13127-149">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="13127-150">等待设置完成。</span><span class="sxs-lookup"><span data-stu-id="13127-150">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="13127-p109">安装完成后，它会显示基于样本数据跟踪订阅的一部分销售活动仪表板。花一些时间查看**欢迎您的试用版**视频。关闭完成后视频窗口。</span><span class="sxs-lookup"><span data-stu-id="13127-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="13127-154">在顶部的工具栏上，单击**销售**旁的下箭头，单击**设置**，然后单击**安全**。</span><span class="sxs-lookup"><span data-stu-id="13127-154">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="13127-155">在**安全**页中，单击**用户**。</span><span class="sxs-lookup"><span data-stu-id="13127-155">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="13127-156">在用户列表中，单击**用户 2**。</span><span class="sxs-lookup"><span data-stu-id="13127-156">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="13127-157">在工具栏上，单击**管理角色**。</span><span class="sxs-lookup"><span data-stu-id="13127-157">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="13127-158">**管理角色**，单击**系统管理员**，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="13127-158">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="13127-159">在顶部的工具栏中单击**安全**。</span><span class="sxs-lookup"><span data-stu-id="13127-159">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="13127-160">为用户 3 帐户重复步骤 5 到 8。</span><span class="sxs-lookup"><span data-stu-id="13127-160">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="13127-161">关闭**用户： 用户 3**选项卡。</span><span class="sxs-lookup"><span data-stu-id="13127-161">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="13127-162">已为 Office 365 全局管理员帐户自动分配了 Dynamics 365 系统管理员角色。</span><span class="sxs-lookup"><span data-stu-id="13127-162">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="13127-163">现在，你的 Office 365 和 Dynamics 365 开发/测试环境包含：</span><span class="sxs-lookup"><span data-stu-id="13127-163">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="13127-164">与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版和 Dynamics 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="13127-164">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="13127-165">全局企业管理员、用户 2 和用户 3 的帐户都可以使用 Office 365 E5 企业版和 Dynamics 365，并且它们都是 Dynamics 365 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="13127-165">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="13127-166">后续步骤</span><span class="sxs-lookup"><span data-stu-id="13127-166">Next step</span></span>

<span data-ttu-id="13127-167">配置，然后说明如何 Office 365 和 Dynamics 365 结合使用[Office 365 和 Dynamics 365 开发/测试环境](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)的 Exchange 联机集成在 Exchange 在线邮箱。</span><span class="sxs-lookup"><span data-stu-id="13127-167">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="13127-168">See Also</span><span class="sxs-lookup"><span data-stu-id="13127-168">See Also</span></span>

[<span data-ttu-id="13127-169">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="13127-169">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="13127-170">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="13127-170">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="13127-171">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="13127-171">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="13127-172">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="13127-172">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="13127-173">Dynamics 365（联机）的订阅管理</span><span class="sxs-lookup"><span data-stu-id="13127-173">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="13127-174">管理 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="13127-174">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


