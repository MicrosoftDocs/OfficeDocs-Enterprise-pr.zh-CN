---
title: 用于 Office 365 开发/测试环境的云应用安全
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 摘要： 配置和演示 Office 365 开发/测试环境中的 Office 365 云应用程序安全性。
ms.openlocfilehash: 089b9771d0600f8c74bc7b4c30ff2a4931c93ae6
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915757"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="15874-103">用于 Office 365 开发/测试环境的云应用安全</span><span class="sxs-lookup"><span data-stu-id="15874-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="15874-104">**摘要：** 配置和演示 Office 365 开发/测试环境中的 Office 365 云应用程序安全性。</span><span class="sxs-lookup"><span data-stu-id="15874-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="15874-p101">Office 365 云应用程序安全性，以前称为 Office 365 高级安全管理，允许您创建的监视和通知您在 Office 365 订阅中，可疑活动，以便可以调查，并采取可能的策略修复操作。有关详细信息，请参阅[概述的云应用程序中的安全性 Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。</span><span class="sxs-lookup"><span data-stu-id="15874-p101">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action. For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="15874-107">使用本文中的说明，您可以启用和测试您的 Office 365 试用版订阅中的云应用程序安全性。</span><span class="sxs-lookup"><span data-stu-id="15874-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="15874-108">单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="15874-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="15874-109">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="15874-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="15874-110">如果您只想要测试的最低硬件要求与轻型方式中的云应用程序安全性，请在阶段 2 和 3 的[Office 365 开发/测试环境](office-365-dev-test-environment.md)中按照说明。</span><span class="sxs-lookup"><span data-stu-id="15874-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="15874-111">如果您想要测试模拟企业中的云应用程序安全性，请按照[目录同步的 Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="15874-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="15874-p102">测试的云应用程序安全性不需要模拟的企业开发/测试环境中，包括连接到 Internet 模拟的 intranet 和 Windows Server AD 林目录同步。它提供此处作为一个选项，以便可以测试云应用程序安全性，并与之试验环境值，该值代表典型组织中。</span><span class="sxs-lookup"><span data-stu-id="15874-p102">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="15874-114">第 2 阶段： 之前启用云应用程序安全性和创建策略</span><span class="sxs-lookup"><span data-stu-id="15874-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="15874-115">在此过程中，您可以演示，然后再启用云应用程序安全性，更改用户的角色提供了无电子邮件通知给全局管理员。</span><span class="sxs-lookup"><span data-stu-id="15874-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="15874-116">测试 Office 365 的默认通知行为</span><span class="sxs-lookup"><span data-stu-id="15874-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="15874-117">转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 和 Office 365 试用版订阅与全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="15874-117">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="15874-118">如果你使用的是轻型 Office 365 开发/测试环境，请从你的本地计算机登录。</span><span class="sxs-lookup"><span data-stu-id="15874-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="15874-119">如果您使用模拟的企业的 Office 365 开发/测试环境，使用[Azure 门户网站](https://portal.azure.com)连接到 CLIENT1 虚拟机，并然后登录从 CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="15874-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="15874-120">在主门户页上，单击“管理员”****。</span><span class="sxs-lookup"><span data-stu-id="15874-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="15874-121">在左侧导航栏中，依次单击“用户”和“活动用户”****。</span><span class="sxs-lookup"><span data-stu-id="15874-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="15874-122">	单击“**User 4**”帐户。</span><span class="sxs-lookup"><span data-stu-id="15874-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="15874-123">在“**User 4**”页面上，针对“**角色**”行单击“**编辑**”。</span><span class="sxs-lookup"><span data-stu-id="15874-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="15874-p103">在“**编辑用户角色**”页面上，单击“**全局管理员**”，在“**备选电子邮件地址**”中键入“**user4@contoso.com**”，然后单击“**保存**”。单击“**关闭**”两次。</span><span class="sxs-lookup"><span data-stu-id="15874-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="15874-126">	选择左上角的应用启动器图标，然后选择“**邮件**”。</span><span class="sxs-lookup"><span data-stu-id="15874-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="15874-p104">等待 30 分钟。请注意，通知您以全局管理员的用户 4 角色中的更改的收件箱中没有任何电子邮件消息。</span><span class="sxs-lookup"><span data-stu-id="15874-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="15874-129">第 3 阶段： 启用云应用程序安全性，并创建策略</span><span class="sxs-lookup"><span data-stu-id="15874-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="15874-p105">在此过程中，您将启用云应用程序安全性，并创建新策略，以向您的用户帐户角色中的更改的全局管理员帐户发送电子邮件通知。此过程需要：</span><span class="sxs-lookup"><span data-stu-id="15874-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="15874-132">你的 Office 365 试用订阅的全局管理员帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="15874-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="15874-133">你的 Office 365 试用订阅的 User 5 帐户的名称和密码。</span><span class="sxs-lookup"><span data-stu-id="15874-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="15874-134">启用和配置云应用程序安全性</span><span class="sxs-lookup"><span data-stu-id="15874-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="15874-135">转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 和 Office 365 试用版订阅与全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="15874-135">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="15874-p106">单击**管理员**图块。在**Office Admin center**选项卡上单击**管理中心 > 安全和合规性**。</span><span class="sxs-lookup"><span data-stu-id="15874-p106">Click the **Admin** tile. On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="15874-138">在左侧的导航窗格中，单击**通知 > 管理高级通知**。</span><span class="sxs-lookup"><span data-stu-id="15874-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="15874-139">在**高级通知的管理**页上，单击**打开 Office 365 云应用程序安全性**，然后单击**转到 Office 365 云应用程序安全性**。</span><span class="sxs-lookup"><span data-stu-id="15874-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="15874-140">在新的**仪表板**选项卡，单击**控件 > 策略**。</span><span class="sxs-lookup"><span data-stu-id="15874-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="15874-141">在**策略**页上，单击**创建策略**，，然后单击**活动策略**。</span><span class="sxs-lookup"><span data-stu-id="15874-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="15874-142">在**策略名称**框中，键入**管理活动**。</span><span class="sxs-lookup"><span data-stu-id="15874-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="15874-143">在“**策略严重性**”中，单击“**高**”。</span><span class="sxs-lookup"><span data-stu-id="15874-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="15874-144">在**类别**中，单击**特权的帐户**。</span><span class="sxs-lookup"><span data-stu-id="15874-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="15874-145">在**创建筛选器策略**，在**以下所有条件匹配的活动**中，单击**管理活动**。</span><span class="sxs-lookup"><span data-stu-id="15874-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="15874-p107">在“**警报**”中，单击“**作为电子邮件发送警报**”。在“**收件人**”中，键入你的全局管理员帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="15874-p107">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="15874-148">在页面底部，单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="15874-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="15874-149">在操作的第 4 阶段： 显示云应用程序安全性</span><span class="sxs-lookup"><span data-stu-id="15874-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="15874-150">在此过程中，可以将演示如何云应用程序安全性创建通知和时用户 4 使用户 5 的密码和用户管理管理员向的全局管理员帐户发送电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="15874-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="15874-151">演示用户帐户角色更改的电子邮件通知</span><span class="sxs-lookup"><span data-stu-id="15874-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="15874-152">在右上角，单击用户图标，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="15874-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="15874-153">转到[https://portal.office.com](https://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="15874-153">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
3. <span data-ttu-id="15874-154">在 Office 365 登录页面上，单击“**使用其他帐户**”。</span><span class="sxs-lookup"><span data-stu-id="15874-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="15874-155">键入 User 4 的帐户名及其密码，然后单击“**登录**”。</span><span class="sxs-lookup"><span data-stu-id="15874-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="15874-156">如果需要，请更改 User 4 的帐户密码，然后单击“**更新密码并登录**”。</span><span class="sxs-lookup"><span data-stu-id="15874-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="15874-157">在 Office 365 门户页面上，单击“**管理员**”。</span><span class="sxs-lookup"><span data-stu-id="15874-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="15874-158">如果需要，请在系统提示更新管理员联系信息时单击“**取消**”。</span><span class="sxs-lookup"><span data-stu-id="15874-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="15874-159">在主门户页上，单击“管理员”****。</span><span class="sxs-lookup"><span data-stu-id="15874-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="15874-160">在左侧导航栏中，依次单击“用户”和“活动用户”****。</span><span class="sxs-lookup"><span data-stu-id="15874-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="15874-161">单击“**User 5**”帐户。</span><span class="sxs-lookup"><span data-stu-id="15874-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="15874-162">在“**User 5**”页面上，针对“**角色**”行单击“**编辑**”。</span><span class="sxs-lookup"><span data-stu-id="15874-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="15874-p108">在“**编辑用户角色**”页面上，依次单击“**自定义管理员**”、“**密码管理员**”和“**用户管理管理员**”，在“**备选电子邮件地址**”中键入“**user5@contoso.com**”，然后单击“**保存**”。单击“**关闭**”两次。</span><span class="sxs-lookup"><span data-stu-id="15874-p108">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="15874-165">单击右上角中的用户图标，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="15874-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="15874-166">转到[https://portal.office.com](https://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="15874-166">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
15. <span data-ttu-id="15874-167">在“**Office 365 登录**”页面上，单击你的全局管理员帐户名。</span><span class="sxs-lookup"><span data-stu-id="15874-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="15874-168">键入密码，然后单击“**登录**”。</span><span class="sxs-lookup"><span data-stu-id="15874-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="15874-169">在主门户页上，单击“管理员”****。</span><span class="sxs-lookup"><span data-stu-id="15874-169">From the main portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="15874-170">单击**安全&amp;合规性**平铺。</span><span class="sxs-lookup"><span data-stu-id="15874-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="15874-171">在左侧的导航窗格中，单击**通知 > 管理高级通知**。</span><span class="sxs-lookup"><span data-stu-id="15874-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="15874-172">在**高级通知的管理**页上，单击**转到 Office 365 云应用程序安全性**。</span><span class="sxs-lookup"><span data-stu-id="15874-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="15874-173">在新**仪表板**选项卡，请注意**管理**活动的两个新通知。</span><span class="sxs-lookup"><span data-stu-id="15874-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="15874-p109">从**Microsoft Office Home**选项卡，单击**邮件**。等待最多 30 分钟。</span><span class="sxs-lookup"><span data-stu-id="15874-p109">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="15874-p110">您应看到两个新的电子邮件收件箱具有标题**Microsoft Azure AD 通知服务**。一条消息指示用户 5 帐户已添加到的**密码管理员**角色和另一条消息指示用户 5 帐户已添加到**用户管理员**角色 (等于中的用户管理管理员角色Office 365 Admin center)。</span><span class="sxs-lookup"><span data-stu-id="15874-p110">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="15874-p111">您现在可以使用此环境以创建新策略，并进一步试用 Office 365 云应用程序安全性。其他配置文章的链接，请参阅[为 Office 365 云应用程序安全性做好准备](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)。</span><span class="sxs-lookup"><span data-stu-id="15874-p111">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="15874-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15874-180">See Also</span></span>

[<span data-ttu-id="15874-181">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="15874-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="15874-182">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="15874-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="15874-183">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="15874-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="15874-184">Office 365 中的云应用程序安全性概述</span><span class="sxs-lookup"><span data-stu-id="15874-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


