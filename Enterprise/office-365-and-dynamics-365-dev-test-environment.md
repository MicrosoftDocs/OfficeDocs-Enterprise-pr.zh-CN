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
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 摘要：使用本测试实验室指南将 Dynamics 365 添加到 Office 365 开发/测试环境。
ms.openlocfilehash: 9e4c98129c68ab5d2f0d9fc486ab62740c625af5
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574056"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="f0c56-103">Office 365 和 Dynamics 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="f0c56-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="f0c56-104">**摘要：** 使用本测试实验室指南将 Dynamics 365 添加到 Office 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="f0c56-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="f0c56-105">使用本文中的说明进行操作，将 Dynamics 365 试用订阅作为 Office 365 开发/测试环境添加到同一个组织，创建一个 Office 365 和 Dynamics 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="f0c56-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Office 365 和 Dynamics 365 开发/测试环境](media/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="f0c56-p101">可将 Dynamics 365 试用订阅用于演示 Dynamics 365 的功能和特性。Dynamics 365 计划 1（企业版试用）包括以下解决方案：</span><span class="sxs-lookup"><span data-stu-id="f0c56-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="f0c56-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales)。通过自动化和数字智能提高销售量，帮助销售人员保持专注并高效工作。</span><span class="sxs-lookup"><span data-stu-id="f0c56-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="f0c56-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service)。通过为代理提供所需的完整信息和数字智能获取忠诚度，从而提供无缝服务。</span><span class="sxs-lookup"><span data-stu-id="f0c56-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="f0c56-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service)。通过优化日程安排、配备员工以及使用预测工具来控制服务请求，从而增加利润。</span><span class="sxs-lookup"><span data-stu-id="f0c56-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="f0c56-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/zh-CN/dynamics365/project-service-automation)。成功完成项目，并通过高效率员工和智能工具构建盈利性关系。</span><span class="sxs-lookup"><span data-stu-id="f0c56-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/zh-CN/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="f0c56-117">可以浏览上述一个或多个网站以获取 Dynamics 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="f0c56-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Microsoft 云中的测试实验室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="f0c56-119">单击[此处](http://aka.ms/catlgstack)可以在 One Microsoft 云测试实验室指南堆栈图中直观转到相应的任何文章。</span><span class="sxs-lookup"><span data-stu-id="f0c56-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="f0c56-120">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="f0c56-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="f0c56-121">如果只需要测试达到最低要求的轻型 Office 365 和 Dynamics 365，请按照 [Office 365 开发/测试环境](office-365-dev-test-environment.md)中第 2 阶段和第 3 阶段的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f0c56-121">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="f0c56-122">如果想要为模拟的企业测试 Office 365 和 Dynamics 365，请按照[适用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md) 中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f0c56-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>

![Office 365 开发/测试环境](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="f0c56-p106">本文中的配置不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试 Office 365 和 Dynamics 365，并在代表典型组织的环境中对其进行试验。</span><span class="sxs-lookup"><span data-stu-id="f0c56-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="f0c56-126">第 2 阶段：添加 Dynamics 365 试用订阅</span><span class="sxs-lookup"><span data-stu-id="f0c56-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="f0c56-127">在此阶段，注册 Dynamics 365 试用订阅，并将其作为 Office 365 试用订阅添加到同一组织。</span><span class="sxs-lookup"><span data-stu-id="f0c56-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="f0c56-128">注册 Dynamics 365 试用订阅</span><span class="sxs-lookup"><span data-stu-id="f0c56-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="f0c56-129">通过台式计算机（轻型）或 CLIENT1（模拟企业）上的浏览器，使用全局管理员帐户登录至 Microsoft 365 管理中心（地址为 [https://admin.microsoft.com](https://admin.microsoft.com)）。</span><span class="sxs-lookup"><span data-stu-id="f0c56-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://admin.microsoft.com](https://admin.microsoft.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="f0c56-130">单击“管理员”磁贴\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="f0c56-131">在“**Microsoft 365 管理中心**”选项卡上的左侧导航栏中，单击“**计费 > 购买服务**”。</span><span class="sxs-lookup"><span data-stu-id="f0c56-131">On the **Microsoft 365 admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="f0c56-p107">在“购买服务”页上，找到“Dynamics 365 计划 1 企业版”项。将鼠标指针悬停在此项之上，然后单击“开始免费试用”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="f0c56-134">在“确认订单”页上，单击“立即试用”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="f0c56-135">在“订单签收”\*\*\*\* 页上，单击“继续”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-135">On the **Order receipt** page, click **Continue**.</span></span>

![Office 365 和 Dynamics 365 开发/测试环境](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="f0c56-p108">Dynamics 365 计划 1 企业版订阅试用期是 30 天。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。</span><span class="sxs-lookup"><span data-stu-id="f0c56-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="f0c56-140">第 3 阶段：分配 Dynamics 365 许可证和系统管理员</span><span class="sxs-lookup"><span data-stu-id="f0c56-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="f0c56-141">在此阶段中，将 Dynamics 365 许可证分配给全局管理员、用户 2 和用户 3 的帐户并使之成为系统管理员。</span><span class="sxs-lookup"><span data-stu-id="f0c56-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="f0c56-142">使用下列步骤分配 Dynamics 365 许可证。</span><span class="sxs-lookup"><span data-stu-id="f0c56-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="f0c56-143">在“**Microsoft 365 管理中心**”选项卡上，单击“**用户 > 活动用户**”。</span><span class="sxs-lookup"><span data-stu-id="f0c56-143">On the **Microsoft 365 admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="f0c56-144">在活动用户列表中，单击全局管理员帐户，然后针对“产品许可证”\*\*\*\* 单击“编辑”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="f0c56-145">在“产品许可证”窗格上，将“Dynamics 365 计划 1 企业版”的产品许可证设置为“打开”，单击“保存”，然后单击“关闭”两次\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="f0c56-146">为用户 2 和用户 3 的帐户执行步骤 2 和步骤 3。</span><span class="sxs-lookup"><span data-stu-id="f0c56-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="f0c56-147">关闭 **Microsoft 365 管理员中心**选项卡。</span><span class="sxs-lookup"><span data-stu-id="f0c56-147">Close the **Microsoft 365 admin center** tab.</span></span>
    
<span data-ttu-id="f0c56-148">使用以下步骤将用户 2 和用户 3 的帐户配置为 Dynamics 365 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="f0c56-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="f0c56-149">在“Microsoft Office 主页”\*\*\*\* 选项卡上，单击“管理员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-149">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="f0c56-150">在“Office 管理中心”\*\*\*\* 标签页的左侧导航中，单击“管理中心”\*\*\*\*，然后单击“Dynamics 365”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-150">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="f0c56-151">可能需要等到 Dynamics 365 完成设置后，菜单中才会显示 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="f0c56-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="f0c56-152">在 Dynamics 365 选项卡上，单击“所有内容”，然后单击“完成设置”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="f0c56-153">等待设置完成。</span><span class="sxs-lookup"><span data-stu-id="f0c56-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="f0c56-p109">设置完成后，它会基于试用订阅中示例数据显示一个销售活动仪表板。请花点时间来观看“欢迎使用试用版”\*\*\*\* 视频。完成后关闭视频窗口。</span><span class="sxs-lookup"><span data-stu-id="f0c56-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="f0c56-157">在顶部工具栏上，单击“销售”旁边的向下箭头，单击“设置”，然后单击“安全”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="f0c56-158">在“安全”页上，单击“用户”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="f0c56-159">在用户列表中，单击“用户 2”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="f0c56-160">在工具栏中，单击“管理角色”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="f0c56-161">在“管理角色”中，单击“系统管理员”，然后单击“确定”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="f0c56-162">在顶部工具栏中单击“安全”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0c56-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="f0c56-163">为用户 3 帐户重复步骤 5 到 8。</span><span class="sxs-lookup"><span data-stu-id="f0c56-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="f0c56-164">关闭“用户：User3”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f0c56-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f0c56-165">已为 Office 365 全局管理员帐户自动分配了 Dynamics 365 系统管理员角色。</span><span class="sxs-lookup"><span data-stu-id="f0c56-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="f0c56-166">现在，你的 Office 365 和 Dynamics 365 开发/测试环境包含：</span><span class="sxs-lookup"><span data-stu-id="f0c56-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="f0c56-167">与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版和 Dynamics 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="f0c56-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="f0c56-168">全局企业管理员、用户 2 和用户 3 的帐户都可以使用 Office 365 E5 企业版和 Dynamics 365，并且它们都是 Dynamics 365 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="f0c56-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="f0c56-169">后续步骤</span><span class="sxs-lookup"><span data-stu-id="f0c56-169">Next step</span></span>

<span data-ttu-id="f0c56-170">配置然后演示 Office 365 和 Dynamics 365 如何通过[适用于 Office 365 和 Dynamics 365 开发/测试环境的 Exchange Online 集成](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)在 Exchange Online 邮箱中协作。</span><span class="sxs-lookup"><span data-stu-id="f0c56-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f0c56-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0c56-171">See Also</span></span>

[<span data-ttu-id="f0c56-172">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="f0c56-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="f0c56-173">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="f0c56-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="f0c56-174">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="f0c56-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="f0c56-175">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="f0c56-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="f0c56-176">Dynamics 365（联机）的订阅管理</span><span class="sxs-lookup"><span data-stu-id="f0c56-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="f0c56-177">管理 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="f0c56-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


