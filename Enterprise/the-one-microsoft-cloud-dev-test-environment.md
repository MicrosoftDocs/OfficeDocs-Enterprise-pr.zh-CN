---
title: "一个 Microsoft 云开发/测试环境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: "摘要： 使用此测试实验室指南创建包括所有微软云产品的开发/测试环境。"
ms.openlocfilehash: 486aabd769461a7e743ac390d633913053b467a8
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="3674b-103">一个 Microsoft 云开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="3674b-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="3674b-104">**摘要：**此测试实验室指南用于创建包含所有微软云产品的开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="3674b-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="3674b-p101">使用本文中的说明进行操作，您在 Microsoft Azure 的基础结构服务中创建模拟的内联网并将 Microsoft Office 365、 Microsoft 企业移动 + 安全 (EMS) 和 Microsoft Dynamics 365 订阅。其结果是在一个单一的开发测试环境中同时使用所有 Microsoft 的云服务简化的组织。</span><span class="sxs-lookup"><span data-stu-id="3674b-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![包含 Azure、Office 365、EMS 和 Dynamics 365 的 One Microsoft 云开发/测试环境的第 3 阶段](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="3674b-108">您可以使用对生成的配置：</span><span class="sxs-lookup"><span data-stu-id="3674b-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="3674b-109">体验微软云服务，例如提供通过 Azure 活动目录 (AD) 的公共标识基础结构集成。</span><span class="sxs-lookup"><span data-stu-id="3674b-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="3674b-110">对包含多个 Microsoft 云服务的端到端方案进行评估。</span><span class="sxs-lookup"><span data-stu-id="3674b-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="3674b-111">创建演示、 概念验证或使用多个云 Microsoft 产品开发/测试配置。</span><span class="sxs-lookup"><span data-stu-id="3674b-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="3674b-112">构建您的 Microsoft 云技能的职业发展。</span><span class="sxs-lookup"><span data-stu-id="3674b-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="3674b-113">阶段 1： 创建模拟的内联网，并添加 Office 365</span><span class="sxs-lookup"><span data-stu-id="3674b-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="3674b-114">请按[您 Office 365 的开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="3674b-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="3674b-115">图 1 显示您生成的配置，其中包括 Office 365 和模拟的内联网，从内部 Windows 服务器活动目录 (AD) 林在 Azure 的基础设施服务和目录同步运行。</span><span class="sxs-lookup"><span data-stu-id="3674b-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="3674b-116">**图 1： 使用 Office 365 的 Azure 中模拟的 intranet**</span><span class="sxs-lookup"><span data-stu-id="3674b-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![DirSync 的 Office 365 开发/测试环境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="3674b-p102">Azure 试用期为 30 天。Office 365 企业 E5 试用版订购是 30 天，可以轻松地扩展为另一个 30 天。为永久的开发测试环境，创建一个新支付 Azure 订阅和新付款的 Office 365 企业 E5 订购数目较少的许可证。</span><span class="sxs-lookup"><span data-stu-id="3674b-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="3674b-121">阶段 2： 添加 EMS</span><span class="sxs-lookup"><span data-stu-id="3674b-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="3674b-122">在此阶段，注册 EMS 试用订阅，并将其作为 Office 365 试用订阅添加到同一组织。</span><span class="sxs-lookup"><span data-stu-id="3674b-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="3674b-123">使用浏览器在您的桌面计算机或从客户端 1，登录到 Office 365 门户网站位于[https://portal.office.com](https://portal.office.com)的全局管理员帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="3674b-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="3674b-124">单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="3674b-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="3674b-125">在浏览器中，在左边的导航中， **Office 管理中心**选项卡单击**计费 > 购买服务**。</span><span class="sxs-lookup"><span data-stu-id="3674b-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="3674b-p103">**购买服务**页上找到**企业移动 + 安全 E5**项。将鼠标指针悬停在其上，单击**启动免费试用版**。</span><span class="sxs-lookup"><span data-stu-id="3674b-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="3674b-128">在**确认订单**页中，单击**立即尝试**。</span><span class="sxs-lookup"><span data-stu-id="3674b-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="3674b-129">在**订单收据**页上，单击**继续**。</span><span class="sxs-lookup"><span data-stu-id="3674b-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="3674b-p104">企业移动性 + 安全性 E5 的试订阅期为 90 天。对于永久性开发/测试环境，请使用少量许可证新建付费订阅。</span><span class="sxs-lookup"><span data-stu-id="3674b-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="3674b-132">下一步，使企业移动性 + 为所有用户帐户的安全 E5 许可证。</span><span class="sxs-lookup"><span data-stu-id="3674b-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="3674b-133">在浏览器中，在左边的导航中， **Office 365 管理中心**选项卡单击**用户 > 活动用户**。</span><span class="sxs-lookup"><span data-stu-id="3674b-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="3674b-134">单击您的全局管理员帐户，然后单击**编辑****产品**许可证。</span><span class="sxs-lookup"><span data-stu-id="3674b-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="3674b-135">**产品许可证**的窗格中，在打开产品许可证**的企业移动性 + 安全 E5**到**上**，单击**保存**，然后两次单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="3674b-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="3674b-136">对于所有其他帐户 (用户 1、用户 2、用户 3、用户 4 和用户 5)，请执行步骤 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="3674b-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="3674b-137">现在已开发/测试环境：</span><span class="sxs-lookup"><span data-stu-id="3674b-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="3674b-138">在 Azure 的基础结构服务中运行模拟内联网。</span><span class="sxs-lookup"><span data-stu-id="3674b-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="3674b-139">与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版和 EMS 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="3674b-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="3674b-140">启用所有用户帐户以使用 Office 365 E5 企业版和 EMS。</span><span class="sxs-lookup"><span data-stu-id="3674b-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="3674b-141">图 2 显示您生成的配置，它增加了 EMS。</span><span class="sxs-lookup"><span data-stu-id="3674b-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="3674b-142">**图 2： 模拟的 intranet 与 Office 365 和 EMS Azure 中**</span><span class="sxs-lookup"><span data-stu-id="3674b-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![包含 Azure、Office 365 和 EMS 的 Microsoft 云开发/测试环境的第 2 阶段](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="3674b-144">阶段 3： 添加 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="3674b-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="3674b-145">在此阶段，您 Dynamics 365 试用订阅注册，即可将其添加到为您的 Office 365 和 EMS 试用订阅的同一组织。</span><span class="sxs-lookup"><span data-stu-id="3674b-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="3674b-146">您的桌面计算机上使用浏览器或客户端 1，从登录到 Office 365 门户网站位于[https://portal.office.com](https://portal.office.com)的全局管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="3674b-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="3674b-147">单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="3674b-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="3674b-148">**办公室管理中心**选项卡上，左边的导航，请单击**计费 > 购买服务**。</span><span class="sxs-lookup"><span data-stu-id="3674b-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="3674b-p105">**购买服务**页上找到**Dynamics 365 计划 1 企业版**项目。将鼠标指针悬停在其上，单击**启动免费试用版**。</span><span class="sxs-lookup"><span data-stu-id="3674b-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="3674b-151">在**确认订单**页中，单击**立即尝试**。</span><span class="sxs-lookup"><span data-stu-id="3674b-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="3674b-152">在**订单收据**页上，单击**继续**。</span><span class="sxs-lookup"><span data-stu-id="3674b-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="3674b-p106">Dynamics 365 计划 1 企业版订阅试用期是 30 天。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。</span><span class="sxs-lookup"><span data-stu-id="3674b-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="3674b-156">使用下列步骤将 Dynamics 365 许可证分配给全局管理员用户 2，用户 3 帐户，使它们成为系统管理员。</span><span class="sxs-lookup"><span data-stu-id="3674b-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="3674b-157">在**Office 管理员中心**选项卡，单击**用户 > 活动用户**。</span><span class="sxs-lookup"><span data-stu-id="3674b-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="3674b-158">在活动的用户的列表中，单击您的全局管理员帐户，然后单击**编辑****产品**许可证。</span><span class="sxs-lookup"><span data-stu-id="3674b-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="3674b-159">在**产品许可证**窗格中**Dynamics 365 计划 1 企业版**对**上**打开产品许可证、 单击**保存**，然后两次单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="3674b-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="3674b-160">为用户 2 和用户 3 的帐户执行步骤 2 和步骤 3。</span><span class="sxs-lookup"><span data-stu-id="3674b-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="3674b-161">关闭**Office 管理员中心**选项卡。</span><span class="sxs-lookup"><span data-stu-id="3674b-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="3674b-162">使用以下步骤将用户 2 和用户 3 的帐户配置为 Dynamics 365 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="3674b-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="3674b-163">在浏览器中，在左边的导航中， **Office 管理中心**选项卡上**管理居中对齐**，请单击，然后单击**Dynamics 365**。</span><span class="sxs-lookup"><span data-stu-id="3674b-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="3674b-164">可能需要等到 Dynamics 365 完成预配后，菜单中才会显示 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="3674b-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="3674b-165">Dynamics 365 选项卡上，单击**所有这些**，然后单击**完成安装。**</span><span class="sxs-lookup"><span data-stu-id="3674b-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="3674b-166">等待设置完成。</span><span class="sxs-lookup"><span data-stu-id="3674b-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="3674b-p107">安装完成后，它会显示基于样本数据跟踪订阅的一部分销售活动仪表板。花一些时间查看**欢迎您的试用版**视频。关闭完成后视频窗口。</span><span class="sxs-lookup"><span data-stu-id="3674b-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="3674b-170">在顶部的工具栏上，单击**销售**旁的下箭头，单击**设置**，然后单击**安全**。</span><span class="sxs-lookup"><span data-stu-id="3674b-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="3674b-171">在**安全**页中，单击**用户**。</span><span class="sxs-lookup"><span data-stu-id="3674b-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="3674b-172">在用户列表中，单击**用户 2**。</span><span class="sxs-lookup"><span data-stu-id="3674b-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="3674b-173">在工具栏上，单击**管理角色**。</span><span class="sxs-lookup"><span data-stu-id="3674b-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="3674b-174">**管理角色**，单击**系统管理员**，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="3674b-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="3674b-175">在顶部的工具栏中单击**安全**。</span><span class="sxs-lookup"><span data-stu-id="3674b-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="3674b-176">为用户 3 帐户重复步骤 5 到 8。</span><span class="sxs-lookup"><span data-stu-id="3674b-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="3674b-177">关闭**用户： 用户 3**选项卡。</span><span class="sxs-lookup"><span data-stu-id="3674b-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="3674b-178">已为 Office 365 全局管理员帐户自动分配了 Dynamics 365 系统管理员角色。</span><span class="sxs-lookup"><span data-stu-id="3674b-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="3674b-179">现在已开发/测试环境：</span><span class="sxs-lookup"><span data-stu-id="3674b-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="3674b-180">在 Azure 的基础结构服务中运行模拟内联网。</span><span class="sxs-lookup"><span data-stu-id="3674b-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="3674b-181">Office 365 E5 企业，EMS 和 Dynamics 365 试用订阅，您的用户帐户列表与共享相同的组织和相同的 Azure AD 租户。</span><span class="sxs-lookup"><span data-stu-id="3674b-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="3674b-182">启用所有用户帐户以使用 Office 365 E5 企业版和 EMS。</span><span class="sxs-lookup"><span data-stu-id="3674b-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="3674b-183">您的全球企业管理员、 用户 2 和 3 用户帐户都允许使用 Dynamics 365，Dynamics 365 系统管理员。</span><span class="sxs-lookup"><span data-stu-id="3674b-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="3674b-184">图 3 显示了生成的配置。</span><span class="sxs-lookup"><span data-stu-id="3674b-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="3674b-185">**图 3： 使用 Office 365、 EMS 和 Dynamics 365 Azure 中模拟的 intranet**</span><span class="sxs-lookup"><span data-stu-id="3674b-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![包含 Azure、Office 365、EMS 和 Dynamics 365 的 One Microsoft 云开发/测试环境的第 3 阶段](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="3674b-187">后续步骤</span><span class="sxs-lookup"><span data-stu-id="3674b-187">Next steps</span></span>

<span data-ttu-id="3674b-p108">现在，您可以尝试使用一个 Microsoft 云开发/测试环境。这里有一些建议为指导经验：</span><span class="sxs-lookup"><span data-stu-id="3674b-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="3674b-190">在 EMS 为 Office 365 提供应用程序配置移动应用程序 (MAM) 管理策略</span><span class="sxs-lookup"><span data-stu-id="3674b-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="3674b-191">在 Office 365 集成与 Dynamics 365 联系人说明 Exchange 联机</span><span class="sxs-lookup"><span data-stu-id="3674b-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="3674b-192">在 Azure 的基础结构服务来承载基于服务器的工作负载中创建模拟的跨内部网络</span><span class="sxs-lookup"><span data-stu-id="3674b-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="3674b-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3674b-193">See Also</span></span>

[<span data-ttu-id="3674b-194">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="3674b-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="3674b-195">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="3674b-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="3674b-196">混合解决方案</span><span class="sxs-lookup"><span data-stu-id="3674b-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="3674b-197">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="3674b-197">Security solutions</span></span>](security-solutions.md)





