---
title: One Microsoft 云开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 摘要：使用本测试实验室指南创建包含所有 Microsoft 云产品/服务的开发/测试环境。
ms.openlocfilehash: b8ffd01c9d129d4537c82f0e1f74bd7c1be1388b
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037946"
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="c6049-103">One Microsoft 云开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="c6049-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="c6049-104">**摘要：** 使用本测试实验室指南创建包含所有 Microsoft 云产品/服务的开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="c6049-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="c6049-p101">按照本文中的说明，你可以在 Microsoft Azure 基础结构服务中创建模拟 Intranet，然后添加 Microsoft Office 365、Microsoft 企业移动性 + 安全性 (EMS) 和 Microsoft Dynamics 365 订阅。结果是，得到简化的组织可以在单个开发/测试环境中同时使用所有 Microsoft 云产品/服务。</span><span class="sxs-lookup"><span data-stu-id="c6049-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![包含 Azure、Office 365、EMS 和 Dynamics 365 的 One Microsoft 云开发/测试环境的第 3 阶段](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="c6049-108">你可以使用生成的配置执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c6049-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="c6049-109">体验 Microsoft 云服务的集成，例如 Azure Active Directory (AD) 提供的通用身份基础结构。</span><span class="sxs-lookup"><span data-stu-id="c6049-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="c6049-110">评估包含多个 Microsoft 云产品/服务的端到端方案。</span><span class="sxs-lookup"><span data-stu-id="c6049-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="c6049-111">创建使用多种 Microsoft 云产品/服务的演示、概念验证或开发/测试配置。</span><span class="sxs-lookup"><span data-stu-id="c6049-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="c6049-112">为专业开发构建你的 Microsoft 云技能。</span><span class="sxs-lookup"><span data-stu-id="c6049-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="c6049-113">第 1 阶段：创建一个模拟 Intranet 并添加 Office 365</span><span class="sxs-lookup"><span data-stu-id="c6049-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="c6049-114">按照[适用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md) 中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c6049-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="c6049-115">图 1 显示了你生成的配置，其中包括 Office 365 和在 Azure 基础结构服务中运行的模拟 Intranet，以及本地 Active Directory 域服务 (AD DS) 林中的目录同步。</span><span class="sxs-lookup"><span data-stu-id="c6049-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="c6049-116">**图 1：包含 Office 365 的 Azure 中的模拟 Intranet**</span><span class="sxs-lookup"><span data-stu-id="c6049-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![包含 DirSync 的 Office 365 开发/测试环境](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="c6049-p102">Azure 试用期为 30 天。Office 365 企业版 E5 试用版的订阅期为 30 天，可以轻松延长 30 天。对于永久性开发/测试环境，使用少量许可证创建新的付费 Azure 订阅和新的付费 Office 365 企业版 E5 订阅。</span><span class="sxs-lookup"><span data-stu-id="c6049-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="c6049-121">第 2 阶段：添加 EMS</span><span class="sxs-lookup"><span data-stu-id="c6049-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="c6049-122">在此阶段，注册 EMS 试用订阅，并将其作为 Office 365 试用订阅添加到同一组织。</span><span class="sxs-lookup"><span data-stu-id="c6049-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="c6049-123">通过台式计算机或 CLIENT1 上的浏览器，使用全局管理员帐户的凭据登录 Office 365 门户（地址为 [https://www.office.com](https://www.office.com)）。</span><span class="sxs-lookup"><span data-stu-id="c6049-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://www.office.com](https://www.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="c6049-124">单击“管理员”磁贴\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c6049-125">在浏览器的“Office 管理中心”标签页的左侧导航中，单击“帐单”>“购买服务”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="c6049-p103">在“购买服务”页上，找到“企业移动性 + 安全性 E5”项。将鼠标指针悬停在此项之上，然后单击“开始免费试用”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="c6049-128">在“确认订单”页上，单击“立即试用”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="c6049-129">在“订单签收”页上，单击“继续”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c6049-p104">企业移动性 + 安全性 E5 的试订阅期为 90 天。对于永久性开发/测试环境，请使用少量许可证新建付费订阅。</span><span class="sxs-lookup"><span data-stu-id="c6049-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="c6049-132">接下来，为所有用户帐户启用企业移动性 + 安全性 E5 许可证。</span><span class="sxs-lookup"><span data-stu-id="c6049-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="c6049-133">在浏览器的“Office 365 管理中心”标签页的左侧导航中，单击“用户”>“活动用户”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="c6049-134">单击全局管理员帐户，然后针对“产品许可证”单击“编辑”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="c6049-135">在“产品许可证”窗格中，将“企业移动性 + 安全性 E5”的产品许可证设置为“打开”，单击“保存”，然后单击“关闭”两次\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="c6049-136">对于所有其他帐户（用户 1、用户 2、用户 3、用户 4 和用户 5），请执行步骤 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="c6049-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="c6049-137">开发/测试环境目前包含：</span><span class="sxs-lookup"><span data-stu-id="c6049-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="c6049-138">在 Azure 基础结构服务中运行的模拟 Intranet。</span><span class="sxs-lookup"><span data-stu-id="c6049-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="c6049-139">与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版和 EMS 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="c6049-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="c6049-140">启用所有用户帐户以使用 Office 365 E5 企业版和 EMS。</span><span class="sxs-lookup"><span data-stu-id="c6049-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="c6049-141">图 2 显示添加 EMS 的生成配置。</span><span class="sxs-lookup"><span data-stu-id="c6049-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="c6049-142">**图 2：包含 Office 365 和 EMS 的 Azure 中的模拟 Intranet**</span><span class="sxs-lookup"><span data-stu-id="c6049-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![包含 Azure、Office 365 和 EMS 的 One Microsoft 云开发/测试环境的第 2 阶段](media/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="c6049-144">第 3 阶段：添加 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c6049-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="c6049-145">在此阶段，注册 Dynamics 365 试用订阅，并将其作为 Office 365 和 EMS 试用订阅添加到同一组织。</span><span class="sxs-lookup"><span data-stu-id="c6049-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="c6049-146">通过台式计算机或 CLIENT1 上的浏览器，使用全局管理员帐户的凭据登录 Office 365 门户（地址为 [https://www.office.com](https://www.office.com)）。</span><span class="sxs-lookup"><span data-stu-id="c6049-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://www.office.com](https://www.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="c6049-147">单击“管理员”磁贴\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c6049-148">在“**Microsoft 365 管理中心**”选项卡上的左侧导航栏中，单击“**计费 > 购买服务**”。</span><span class="sxs-lookup"><span data-stu-id="c6049-148">On the **Microsoft 365 admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="c6049-p105">在“购买服务”页上，找到“Dynamics 365 计划 1 企业版”项。将鼠标指针悬停在此项之上，然后单击“开始免费试用”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="c6049-151">在“确认订单”页上，单击“立即试用”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="c6049-152">在“订单签收”页上，单击“继续”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c6049-p106">Dynamics 365 计划 1 企业版订阅试用期是 30 天。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。</span><span class="sxs-lookup"><span data-stu-id="c6049-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="c6049-156">使用以下步骤将 Dynamics 365 许可证分配给全局管理员、用户 2 和用户 3 的帐户并使之成为系统管理员。</span><span class="sxs-lookup"><span data-stu-id="c6049-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="c6049-157">在“**Microsoft 365 管理中心**”选项卡上，单击“**用户 > 活动用户**”。</span><span class="sxs-lookup"><span data-stu-id="c6049-157">On the **Microsoft 365 admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="c6049-158">在活动用户列表中，单击全局管理员帐户，然后针对“产品许可证”\*\*\*\* 单击“编辑”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="c6049-159">在“产品许可证”窗格上，将“Dynamics 365 计划 1 企业版”的产品许可证设置为“打开”，单击“保存”，然后单击“关闭”两次\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="c6049-160">为用户 2 和用户 3 的帐户执行步骤 2 和步骤 3。</span><span class="sxs-lookup"><span data-stu-id="c6049-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="c6049-161">关闭 **Microsoft 365 管理员中心**选项卡。</span><span class="sxs-lookup"><span data-stu-id="c6049-161">Close the **Microsoft 365 admin center** tab.</span></span>
    
<span data-ttu-id="c6049-162">使用以下步骤将用户 2 和用户 3 的帐户配置为 Dynamics 365 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="c6049-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="c6049-163">在浏览器的“Office 管理中心”标签页的左侧导航中，单击“管理中心”\*\*\*\*，然后单击“Dynamics 365”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="c6049-164">你可能需要等到 Dynamics 365 完成设置后，菜单中才会显示 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="c6049-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="c6049-165">在 Dynamics 365 选项卡上，单击“所有内容”，然后单击“完成设置”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="c6049-166">等待设置完成。</span><span class="sxs-lookup"><span data-stu-id="c6049-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="c6049-p107">设置完成后，它会基于试用订阅中的示例数据显示一个销售活动仪表板。请花点时间来观看“欢迎使用试用版”\*\*\*\* 视频。完成后关闭视频窗口。</span><span class="sxs-lookup"><span data-stu-id="c6049-p107">When setup completes, it shows a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="c6049-170">在顶部工具栏上，单击“销售”旁边的向下箭头，单击“设置”，然后单击“安全”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="c6049-171">在“安全”页上，单击“用户”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="c6049-172">在用户列表中，单击“用户 2”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="c6049-173">在工具栏中，单击“管理角色”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="c6049-174">在“管理角色”中，单击“系统管理员”，然后单击“确定”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="c6049-175">在顶部工具栏中单击“安全”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6049-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="c6049-176">为用户 3 帐户重复步骤 5 到 8。</span><span class="sxs-lookup"><span data-stu-id="c6049-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="c6049-177">关闭“用户：User3”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c6049-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c6049-178">已为 Office 365 全局管理员帐户自动分配了 Dynamics 365 系统管理员角色。</span><span class="sxs-lookup"><span data-stu-id="c6049-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="c6049-179">开发/测试环境目前包含：</span><span class="sxs-lookup"><span data-stu-id="c6049-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="c6049-180">在 Azure 基础结构服务中运行的模拟 Intranet。</span><span class="sxs-lookup"><span data-stu-id="c6049-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="c6049-181">与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版、EMS 和 Dynamics 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="c6049-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="c6049-182">启用所有用户帐户以使用 Office 365 E5 企业版和 EMS。</span><span class="sxs-lookup"><span data-stu-id="c6049-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="c6049-183">全局企业管理员、用户 2 和用户 3 的帐户都可以使用 Dynamics 365，并且它们都是 Dynamics 365 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="c6049-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="c6049-184">图 3 显示生成的配置。</span><span class="sxs-lookup"><span data-stu-id="c6049-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="c6049-185">**图 3：包含 Office 365、EMS 和 Dynamics 365 的 Azure 中的模拟 Intranet**</span><span class="sxs-lookup"><span data-stu-id="c6049-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![包含 Azure、Office 365、EMS 和 Dynamics 365 的 One Microsoft 云开发/测试环境的第 3 阶段](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="c6049-187">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c6049-187">Next steps</span></span>

<span data-ttu-id="c6049-p108">你现在可以试用 One Microsoft 云开发/测试环境。以下是有关指导体验的一些思路：</span><span class="sxs-lookup"><span data-stu-id="c6049-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="c6049-190">在 Office 365 应用程序的 EMS 中配置移动应用管理 (MAM) 策略</span><span class="sxs-lookup"><span data-stu-id="c6049-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="c6049-191">在与 Dynamics 365 联系人集成的 Office 365 中演示 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c6049-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="c6049-192">在 Azure 基础结构服务中创建用于托管基于服务器的工作负载的模拟跨界网络</span><span class="sxs-lookup"><span data-stu-id="c6049-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="c6049-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6049-193">See Also</span></span>

[<span data-ttu-id="c6049-194">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="c6049-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c6049-195">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="c6049-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="c6049-196">混合解决方案</span><span class="sxs-lookup"><span data-stu-id="c6049-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="c6049-197">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="c6049-197">Security solutions</span></span>](security-solutions.md)





