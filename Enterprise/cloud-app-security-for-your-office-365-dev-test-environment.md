---
title: "Office 365 开发/测试环境的云应用程序安全性"
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
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "摘要： 配置和您 Office 365 的开发/测试环境中演示 Office 365 云应用程序安全性。"
ms.openlocfilehash: 1fab5ebfd6e0670ba59fe34b2cca8a7282e75723
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="d8418-103">Office 365 开发/测试环境的云应用程序安全性</span><span class="sxs-lookup"><span data-stu-id="d8418-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="d8418-104">**摘要：**配置和您 Office 365 的开发/测试环境中演示 Office 365 云应用程序安全性。</span><span class="sxs-lookup"><span data-stu-id="d8418-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="d8418-p101">Office 365 云应用程序的安全性，以前称为 Office 365 高级安全管理，使您可以创建用于监视和通知您在您的 Office 365 订阅的可疑活动，以便可以调查，并采取可能的策略补救行动。有关详细信息，请参阅[概述的云应用程序安全的 Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。</span><span class="sxs-lookup"><span data-stu-id="d8418-p101">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action. For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="d8418-107">使用本文中的说明进行操作，您可以启用和在您的 Office 365 试用测试云应用程序安全。</span><span class="sxs-lookup"><span data-stu-id="d8418-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="d8418-108">单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="d8418-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="d8418-109">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="d8418-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="d8418-110">如果您只需要达到最低要求的轻量方式测试云应用程序安全，按照在阶段 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="d8418-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="d8418-111">如果您想要测试中模拟企业的云应用程序的安全，请按[您 Office 365 的开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="d8418-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="d8418-p102">测试云应用程序的安全不需要模拟的企业开发/测试环境，其中包括连接到 Internet 的模拟内部网和 Windows 服务器 AD 林中的目录同步。它提供此处作为一个选项，以便可以测试云应用程序安全性并试验它代表典型的组织的环境中。</span><span class="sxs-lookup"><span data-stu-id="d8418-p102">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="d8418-114">第 2 阶段： 之前启用云应用程序安全和创建策略</span><span class="sxs-lookup"><span data-stu-id="d8418-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="d8418-115">在此过程中，您展示，在启用云应用程序的安全之前, 更改用户的角色提供了无电子邮件通知给全局管理员。</span><span class="sxs-lookup"><span data-stu-id="d8418-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="d8418-116">测试 Office 365 的默认通知行为</span><span class="sxs-lookup"><span data-stu-id="d8418-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="d8418-117">请转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com)) 并登录到您的 Office 365 试用预订使用全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="d8418-117">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="d8418-118">如果你使用的是轻型 Office 365 开发/测试环境，请从你的本地计算机登录。</span><span class="sxs-lookup"><span data-stu-id="d8418-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="d8418-119">如果您使用的模拟的企业 Office 365 开发/测试环境，使用[Azure 门户](https://portal.azure.com)连接到客户端 1 虚拟机，然后从客户端 1 登录。</span><span class="sxs-lookup"><span data-stu-id="d8418-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="d8418-120">从主门户页面中，单击**管理**。</span><span class="sxs-lookup"><span data-stu-id="d8418-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="d8418-121">在左边的导航，请单击**用户 > 活动用户**。</span><span class="sxs-lookup"><span data-stu-id="d8418-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="d8418-122">单击**用户 4**帐户。</span><span class="sxs-lookup"><span data-stu-id="d8418-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="d8418-123">在**用户 4**页上，单击**角色**行的**编辑**。</span><span class="sxs-lookup"><span data-stu-id="d8418-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="d8418-p103">在**编辑用户角色**页上单击**全局管理员**、**备选电子邮件地址**，键入**user4@contoso.com** ，然后单击**保存**。两次单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="d8418-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="d8418-126">在左上方选择的应用程序启动器图标并选择**邮件**。</span><span class="sxs-lookup"><span data-stu-id="d8418-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="d8418-p104">等待 30 分钟。请注意在收件箱通知您这一变化中以全局管理员身份的用户 4 角色没有任何电子邮件。</span><span class="sxs-lookup"><span data-stu-id="d8418-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="d8418-129">阶段 3： 启用云应用程序的安全，并创建策略</span><span class="sxs-lookup"><span data-stu-id="d8418-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="d8418-p105">在此过程中，您可以启用云应用程序安全和创建新的策略将电子邮件通知发送给您的更改用户帐户角色的全局管理员帐户。此过程要求：</span><span class="sxs-lookup"><span data-stu-id="d8418-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="d8418-132">你的 Office 365 试用订阅的全局管理员帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="d8418-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="d8418-133">你的 Office 365 试用订阅的 User 5 帐户的名称和密码。</span><span class="sxs-lookup"><span data-stu-id="d8418-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="d8418-134">启用和配置云应用程序安全</span><span class="sxs-lookup"><span data-stu-id="d8418-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="d8418-135">请转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com)) 并登录到您的 Office 365 试用预订使用全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="d8418-135">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="d8418-136">单击**安全&amp;法规遵从性**平铺。</span><span class="sxs-lookup"><span data-stu-id="d8418-136">Click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="d8418-137">在左侧的导航窗格中，单击**通知 > 高级警报管理**。</span><span class="sxs-lookup"><span data-stu-id="d8418-137">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="d8418-138">在**高级警报管理**页上，单击**打开 Office 365 云应用程序安全性**，然后单击**转到 Office 365 云应用程序的安全**。</span><span class="sxs-lookup"><span data-stu-id="d8418-138">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="d8418-139">在新的**仪表板**选项卡，单击**控件 > 策略**。</span><span class="sxs-lookup"><span data-stu-id="d8418-139">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="d8418-140">在**策略**页面上单击**创建策略**，然后单击**活动策略**。</span><span class="sxs-lookup"><span data-stu-id="d8418-140">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="d8418-141">在**策略名称**中，键入**管理活动**。</span><span class="sxs-lookup"><span data-stu-id="d8418-141">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="d8418-142">在**策略严重级别**，单击**高**。</span><span class="sxs-lookup"><span data-stu-id="d8418-142">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="d8418-143">在**类别**，请单击**特权的帐户**。</span><span class="sxs-lookup"><span data-stu-id="d8418-143">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="d8418-144">在**创建筛选器的策略**，在**匹配以下所有的活动**中，请单击**管理活动**。</span><span class="sxs-lookup"><span data-stu-id="d8418-144">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="d8418-p106">在**警报**，单击**将预警作为电子邮件发送**。**对**，键入您的全局管理员帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="d8418-p106">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="d8418-147">在页面的底部，单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="d8418-147">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="d8418-148">阶段 4： 显示云应用程序安全性操作</span><span class="sxs-lookup"><span data-stu-id="d8418-148">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="d8418-149">在此过程中，演示了云应用程序安全性如何创建警报，以及当用户 4 5 用户密码和用户管理员全局管理员帐户发送电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="d8418-149">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="d8418-150">演示用户帐户角色更改的电子邮件通知</span><span class="sxs-lookup"><span data-stu-id="d8418-150">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="d8418-151">在右上角，单击用户图标，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="d8418-151">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="d8418-152">转到[https://portal.office.com](https://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="d8418-152">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
3. <span data-ttu-id="d8418-153">在 Office 365 提供登录页面，请单击**使用另一个帐户**。</span><span class="sxs-lookup"><span data-stu-id="d8418-153">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="d8418-154">4 用户帐户名和密码，键入，然后单击**登录**。</span><span class="sxs-lookup"><span data-stu-id="d8418-154">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="d8418-155">如果需要请更改用户 4 帐户密码，并单击**更新密码并登录**。</span><span class="sxs-lookup"><span data-stu-id="d8418-155">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="d8418-156">在 Office 365 门户页面上，单击**管理**。</span><span class="sxs-lookup"><span data-stu-id="d8418-156">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="d8418-157">如果需要请单击**取消**，当系统提示您更新您的管理员联系信息。</span><span class="sxs-lookup"><span data-stu-id="d8418-157">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="d8418-158">从主门户页面中，单击**管理**。</span><span class="sxs-lookup"><span data-stu-id="d8418-158">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="d8418-159">在左边的导航，请单击**用户 > 活动用户**。</span><span class="sxs-lookup"><span data-stu-id="d8418-159">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="d8418-160">单击**用户 5**帐户。</span><span class="sxs-lookup"><span data-stu-id="d8418-160">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="d8418-161">在**用户 5**页上，单击**角色**行的**编辑**。</span><span class="sxs-lookup"><span data-stu-id="d8418-161">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="d8418-p107">在**编辑用户角色**页中，单击**自定义管理员****密码管理员**和**用户管理员**的**备选电子邮件地址**，键入**user5@contoso.com**和，然后单击**保存**。两次单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="d8418-p107">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="d8418-164">单击右上角的用户图标，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="d8418-164">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="d8418-165">转到[https://portal.office.com](https://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="d8418-165">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
15. <span data-ttu-id="d8418-166">在**Office 365 提供登录**页面上，单击您的全局管理员帐户名。</span><span class="sxs-lookup"><span data-stu-id="d8418-166">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="d8418-167">键入密码，然后单击**登录**。</span><span class="sxs-lookup"><span data-stu-id="d8418-167">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="d8418-168">从主门户页面中，单击**管理**。</span><span class="sxs-lookup"><span data-stu-id="d8418-168">From the main portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="d8418-169">单击**安全&amp;法规遵从性**平铺。</span><span class="sxs-lookup"><span data-stu-id="d8418-169">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="d8418-170">在左侧的导航窗格中，单击**通知 > 高级警报管理**。</span><span class="sxs-lookup"><span data-stu-id="d8418-170">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="d8418-171">在**高级警报管理**页上，单击**转到 Office 365 云应用程序的安全**。</span><span class="sxs-lookup"><span data-stu-id="d8418-171">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="d8418-172">新的**仪表板**选项卡上，请注意**管理**活动的两个新的警报。</span><span class="sxs-lookup"><span data-stu-id="d8418-172">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="d8418-p108">**Microsoft Office 主页**选项卡中，单击**邮件**。等待 30 分钟。</span><span class="sxs-lookup"><span data-stu-id="d8418-p108">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="d8418-p109">您应该看到两个新的电子邮件收件箱，标题为**Microsoft Azure 广告通知服务**。一条消息指示用户 5 帐户已添加到**管理员密码**角色，和另一条消息指示用户 5 帐户已添加到**用户管理员**角色 (等于中的用户管理管理员角色Office 365 管理中心）。</span><span class="sxs-lookup"><span data-stu-id="d8418-p109">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="d8418-p110">您现在可以使用此环境中进一步试用 Office 365 云应用程序安全地创建新的策略。配置其他文章的链接，请参阅[为 Office 365 云应用程序安全做好准备](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)。</span><span class="sxs-lookup"><span data-stu-id="d8418-p110">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d8418-179">See Also</span><span class="sxs-lookup"><span data-stu-id="d8418-179">See Also</span></span>

[<span data-ttu-id="d8418-180">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="d8418-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="d8418-181">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="d8418-181">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="d8418-182">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="d8418-182">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="d8418-183">Office 365 中的云应用程序安全性的概述</span><span class="sxs-lookup"><span data-stu-id="d8418-183">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


