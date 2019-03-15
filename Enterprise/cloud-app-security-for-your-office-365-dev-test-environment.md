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
description: '摘要: 在 office 365 开发/测试环境中配置和演示 office 365 云应用安全性。'
ms.openlocfilehash: f8630f1666286c2f3cced9323eccbe1f73203fdb
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "30573676"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="99f90-103">用于 Office 365 开发/测试环境的云应用安全</span><span class="sxs-lookup"><span data-stu-id="99f90-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="99f90-104">**摘要:** 在 office 365 开发/测试环境中配置和演示 office 365 云应用安全性。</span><span class="sxs-lookup"><span data-stu-id="99f90-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="99f90-105">office 365 云应用安全性 (以前称为 "office 365 高级安全管理") 允许您创建策略来监视 Office 365 订阅中的可疑活动并告知这些活动, 以便您可以调查并采取补救措施退货.</span><span class="sxs-lookup"><span data-stu-id="99f90-105">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, lets you create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action.</span></span> <span data-ttu-id="99f90-106">有关详细信息, 请参阅[Office 365 中的云应用安全概述](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。</span><span class="sxs-lookup"><span data-stu-id="99f90-106">For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="99f90-107">使用本文中的说明, 可以在 Office 365 试用订阅中启用和测试云应用安全性。</span><span class="sxs-lookup"><span data-stu-id="99f90-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="99f90-108">单击[此处](http://aka.ms/catlgstack)可以在 One Microsoft 云测试实验室指南堆栈图中直观转到相应的任何文章。</span><span class="sxs-lookup"><span data-stu-id="99f90-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="99f90-109">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="99f90-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="99f90-110">如果只想使用最低要求以轻型方式测试云应用安全性, 请按照[Office 365 开发/测试环境](office-365-dev-test-environment.md)的第2阶段和第3阶段中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="99f90-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="99f90-111">如果要在模拟的企业中测试云应用安全性, 请按照[您的 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="99f90-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="99f90-112">测试云应用安全不需要模拟企业开发/测试环境, 其中包括连接到 Internet 的模拟 intranet 和 Windows Server AD 林的目录同步。</span><span class="sxs-lookup"><span data-stu-id="99f90-112">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest.</span></span> <span data-ttu-id="99f90-113">此处提供它作为选项, 以便您可以测试云应用安全性并在代表典型组织的环境中进行试验。</span><span class="sxs-lookup"><span data-stu-id="99f90-113">It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="99f90-114">第2阶段: 启用云应用安全性和创建策略之前</span><span class="sxs-lookup"><span data-stu-id="99f90-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="99f90-115">在此过程中, 您将演示在启用云应用安全性之前, 更改用户的角色不会向全局管理员提供电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="99f90-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="99f90-116">测试 Office 365 的默认通知行为</span><span class="sxs-lookup"><span data-stu-id="99f90-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="99f90-117">转到 Microsoft 365 管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com)), 并使用全局管理员帐户登录到你的 Office 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="99f90-117">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="99f90-118">如果你使用的是轻型 Office 365 开发/测试环境，请从你的本地计算机登录。</span><span class="sxs-lookup"><span data-stu-id="99f90-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="99f90-119">如果使用的是模拟企业 Office 365 开发/测试环境, 请使用[Azure 门户](https://portal.azure.com)连接到 CLIENT1 虚拟机, 然后从 CLIENT1 登录。</span><span class="sxs-lookup"><span data-stu-id="99f90-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="99f90-120">在主门户页上，单击“管理员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="99f90-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="99f90-121">在左侧导航栏中，单击“用户”>“活动用户”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="99f90-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="99f90-122">	单击“*\*User 4*\*”帐户。</span><span class="sxs-lookup"><span data-stu-id="99f90-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="99f90-123">在“**User 4**”页面上，针对“**角色**”行单击“**编辑**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="99f90-p103">在“**编辑用户角色**”页面上，单击“**全局管理员**”，在“**备选电子邮件地址**”中键入“**user4@contoso.com**”，然后单击“**保存**”。单击“**关闭**”两次。</span><span class="sxs-lookup"><span data-stu-id="99f90-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="99f90-126">	选择左上角的应用启动器图标，然后选择“*\*邮件*\*”。</span><span class="sxs-lookup"><span data-stu-id="99f90-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="99f90-127">等待 30 分钟。</span><span class="sxs-lookup"><span data-stu-id="99f90-127">Wait 30 minutes.</span></span> <span data-ttu-id="99f90-128">请注意, 收件箱中没有电子邮件通知你将用户4的角色更改为全局管理员。</span><span class="sxs-lookup"><span data-stu-id="99f90-128">Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="99f90-129">第3阶段: 启用云应用安全性和创建策略</span><span class="sxs-lookup"><span data-stu-id="99f90-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="99f90-130">在此过程中, 您将启用云应用安全性并创建新策略, 以向全局管理员帐户发送电子邮件通知, 以了解用户帐户角色的更改。</span><span class="sxs-lookup"><span data-stu-id="99f90-130">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles.</span></span> <span data-ttu-id="99f90-131">此过程需要以下内容：</span><span class="sxs-lookup"><span data-stu-id="99f90-131">This procedure requires:</span></span>
  
- <span data-ttu-id="99f90-132">你的 Office 365 试用订阅的全局管理员帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="99f90-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="99f90-133">你的 Office 365 试用订阅的 User 5 帐户的名称和密码。</span><span class="sxs-lookup"><span data-stu-id="99f90-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="99f90-134">启用和配置云应用安全性</span><span class="sxs-lookup"><span data-stu-id="99f90-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="99f90-135">转到 Microsoft 365 管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com)), 并使用全局管理员帐户登录到你的 Office 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="99f90-135">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="99f90-136">单击“管理员”磁贴\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="99f90-136">Click the **Admin** tile.</span></span> <span data-ttu-id="99f90-137">在 " **Office 管理中心**" 选项卡上, 单击 "**管理中心" > Security & 合规性**。</span><span class="sxs-lookup"><span data-stu-id="99f90-137">On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="99f90-138">在左侧导航窗格中, 单击 "**通知 > 管理高级警报**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="99f90-139">在 "**管理高级通知**" 页面上, 单击 "**启用 office 365 云应用安全性**", 然后单击 "**转到 office 365 云应用安全性**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="99f90-140">在 "新建**仪表板**" 选项卡上, 单击 "**控制 > 策略**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="99f90-141">在 "**策略**" 页上, 单击 "**创建策略**", 然后单击 "**活动策略**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="99f90-142">在 "**策略名称**" 中, 键入 "**管理活动**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="99f90-143">在“**策略严重性**”中，单击“**高**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="99f90-144">在 "**类别**" 中, 单击 "**特权帐户**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="99f90-145">在 **"为策略创建筛选器**" 中, 在**匹配以下所有**项的活动中, 单击 "**管理活动**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="99f90-p107">在“**警报**”中，单击“**作为电子邮件发送警报**”。在“**收件人**”中，键入你的全局管理员帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="99f90-p107">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="99f90-148">在页面底部，单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="99f90-149">第4阶段: 显示操作中的云应用安全</span><span class="sxs-lookup"><span data-stu-id="99f90-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="99f90-150">在此过程中, 您将演示云应用安全性如何在用户4使用户5成为密码和用户管理管理员时创建通知并向全局管理员帐户发送电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="99f90-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="99f90-151">演示用户帐户角色更改的电子邮件通知</span><span class="sxs-lookup"><span data-stu-id="99f90-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="99f90-152">在右上方，单击用户图标，然后单击“**注销**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="99f90-153">转到 [https://www.office.com](https://www.office.com)。</span><span class="sxs-lookup"><span data-stu-id="99f90-153">Go to [https://www.office.com](https://www.office.com).</span></span>
    
3. <span data-ttu-id="99f90-154">在 Office 365 登录页面上，单击“**使用其他帐户**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="99f90-155">键入 User 4 的帐户名及其密码，然后单击“**登录**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="99f90-156">如果需要，请更改 User 4 的帐户密码，然后单击“**更新密码并登录**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="99f90-157">在 Office 365 门户页面上，单击“**管理员**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="99f90-158">如果需要，请在系统提示更新管理员联系信息时单击“**取消**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="99f90-159">在主要门户页面上，单击“**管理员**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="99f90-160">在左侧导航窗格中，单击“**用户 > 活动用户**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="99f90-161">单击“**User 5**”帐户。</span><span class="sxs-lookup"><span data-stu-id="99f90-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="99f90-162">在“**User 5**”页面上，针对“**角色**”行单击“**编辑**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="99f90-p108">在“**编辑用户角色**”页面上，依次单击“**自定义管理员**”、“**密码管理员**”和“**用户管理管理员**”，在“**备选电子邮件地址**”中键入“**user5@contoso.com**”，然后单击“**保存**”。单击“**关闭**”两次。</span><span class="sxs-lookup"><span data-stu-id="99f90-p108">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="99f90-165">单击右上方的用户图标，然后单击“**注销**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="99f90-166">转到 [https://www.office.com](https://www.office.com)。</span><span class="sxs-lookup"><span data-stu-id="99f90-166">Go to [https://www.office.com](https://www.office.com).</span></span>
    
15. <span data-ttu-id="99f90-167">在“**Office 365 登录**”页面上，单击你的全局管理员帐户名。</span><span class="sxs-lookup"><span data-stu-id="99f90-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="99f90-168">键入密码，然后单击“**登录**”。</span><span class="sxs-lookup"><span data-stu-id="99f90-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="99f90-169">在 "Office 365 门户" 页中, 单击 "**管理**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-169">From the Office 365 portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="99f90-170">单击 "**安全&amp;符合性**磁贴"。</span><span class="sxs-lookup"><span data-stu-id="99f90-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="99f90-171">在左侧导航窗格中, 单击 "**通知 > 管理高级警报**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="99f90-172">在 "**管理高级通知**" 页上, 单击 "**转到 Office 365 云应用安全性**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="99f90-173">在 "新建**仪表板**" 选项卡上, 请注意两个用于**管理活动**的新警报。</span><span class="sxs-lookup"><span data-stu-id="99f90-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="99f90-174">在 " **Microsoft Office 主页**" 选项卡上, 单击 "**邮件**"。</span><span class="sxs-lookup"><span data-stu-id="99f90-174">From the **Microsoft Office Home** tab, click **Mail**.</span></span> <span data-ttu-id="99f90-175">最多等待 30 分钟。</span><span class="sxs-lookup"><span data-stu-id="99f90-175">Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="99f90-176">您应该会在收件箱中看到两封新电子邮件, 标题为**Microsoft Azure AD 通知服务**。</span><span class="sxs-lookup"><span data-stu-id="99f90-176">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**.</span></span> <span data-ttu-id="99f90-177">一条消息指示已将用户5帐户添加到**密码管理员**角色, 另一条消息指示已将用户5帐户添加到**用户管理员**角色 (等于中的用户管理管理员角色)。Office 365 管理中心)。</span><span class="sxs-lookup"><span data-stu-id="99f90-177">One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="99f90-178">现在, 你可以使用此环境创建新策略, 并对 Office 365 云应用安全性进行进一步实验。</span><span class="sxs-lookup"><span data-stu-id="99f90-178">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security.</span></span> <span data-ttu-id="99f90-179">有关指向其他配置文章的链接, 请参阅[获取 Office 365 云应用安全性的准备](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)工作。</span><span class="sxs-lookup"><span data-stu-id="99f90-179">See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="99f90-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99f90-180">See Also</span></span>

[<span data-ttu-id="99f90-181">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="99f90-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="99f90-182">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="99f90-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="99f90-183">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="99f90-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="99f90-184">Office 365 中的云应用安全概述</span><span class="sxs-lookup"><span data-stu-id="99f90-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


