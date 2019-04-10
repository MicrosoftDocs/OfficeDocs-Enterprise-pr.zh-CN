---
title: Office 365 开发/测试环境中的高级威胁防护
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: '摘要: 在 office 365 开发/测试环境中配置和演示 office 365 高级威胁防护。'
ms.openlocfilehash: 53bff386490ed9647a511f75c997cb91b0acc181
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741338"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="aab3e-103">Office 365 开发/测试环境中的高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="aab3e-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="aab3e-104">**摘要:** 在 office 365 开发/测试环境中配置和演示 office 365 高级威胁防护。</span><span class="sxs-lookup"><span data-stu-id="aab3e-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="aab3e-105">Office 365 高级威胁防护 (ATP) 是 Exchange Online Protection (EOP) 的一项功能, 可帮助您的电子邮件阻止恶意软件。</span><span class="sxs-lookup"><span data-stu-id="aab3e-105">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span> <span data-ttu-id="aab3e-106">使用 ATP, 可以在 Exchange 管理中心 (EAC) 或安全&amp;合规中心中创建策略, 以确保您的用户仅访问电子邮件中标识为非恶意的链接或附件。</span><span class="sxs-lookup"><span data-stu-id="aab3e-106">With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious.</span></span> <span data-ttu-id="aab3e-107">有关详细信息，请参阅[安全附件和安全链接的高级威胁保护](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="aab3e-107">For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="aab3e-108">使用本文中的说明, 可以在 Office 365 试用订阅中配置和测试 ATP。</span><span class="sxs-lookup"><span data-stu-id="aab3e-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="aab3e-109">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="aab3e-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="aab3e-110">如果只想使用最低要求以轻量方式测试 ATP, 请按照[Office 365 开发/测试环境](office-365-dev-test-environment.md)的第2阶段和第3阶段中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="aab3e-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="aab3e-111">如果要在模拟企业版中测试 ATP, 请按照[您的 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="aab3e-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="aab3e-112">测试 ATP 不需要模拟企业开发/测试环境, 其中包括连接到 Internet 的模拟 intranet 和 Active directory 域服务 (AD DS) 林的目录同步。</span><span class="sxs-lookup"><span data-stu-id="aab3e-112">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="aab3e-113">此处提供它作为选项, 以便您可以在代表典型组织的环境中测试 ATP 并进行实验。</span><span class="sxs-lookup"><span data-stu-id="aab3e-113">It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="aab3e-114">第2阶段: 演示 Office 365 的默认电子邮件传递行为</span><span class="sxs-lookup"><span data-stu-id="aab3e-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="aab3e-115">在此阶段中, 您将演示在配置 ATP 策略之前, 潜在的恶意电子邮件将被传递到 Office 365 邮箱, 而不会进行屏蔽或缓解。</span><span class="sxs-lookup"><span data-stu-id="aab3e-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="aab3e-116">打开 Internet Explorer, 并登录到在[Office 365 开发/测试环境](office-365-dev-test-environment.md)的第2阶段中创建的 Outlook 帐户。</span><span class="sxs-lookup"><span data-stu-id="aab3e-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="aab3e-117">如果使用的是轻型 Office 365 开发/测试环境, 请打开 Internet Explorer 的专用会话并从本地计算机登录。</span><span class="sxs-lookup"><span data-stu-id="aab3e-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="aab3e-118">如果使用的是模拟企业 Office 365 开发/测试环境, 请使用[Azure 门户](https://portal.azure.com)连接到 CLIENT1 虚拟机, 然后从 CLIENT1 登录。</span><span class="sxs-lookup"><span data-stu-id="aab3e-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="aab3e-119">运行记事本并输入一些文本。</span><span class="sxs-lookup"><span data-stu-id="aab3e-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="aab3e-120">将文件作为**getkeys.js**保存到 Documents 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="aab3e-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="aab3e-121">在 Internet Explorer 的 "Outlook 邮件" 选项卡上, 单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="aab3e-122">在 " **To**" 中, 键入试用订阅的 Office 365 全局管理员名称的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="aab3e-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="aab3e-123">对于 "主题", 请键入**新密钥**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="aab3e-124">在正文中, 键入**此处为文件**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="aab3e-125">单击 "**附加**", 双击 "文档" 文件夹中的 " **getkeys.js** ", 单击 "**附加为副本**", 然后单击 "**发送**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="aab3e-126">单击"新建"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-126">Click **New**.</span></span>
    
10. <span data-ttu-id="aab3e-127">在 " **To**" 中, 键入试用订阅的 Office 365 全局管理员名称的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="aab3e-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="aab3e-128">对于 "主题", 键入 "**新建旅行网站**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="aab3e-129">在正文中, 键入**某人向我转发此网站**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="aab3e-130">在正文中, 选择 "**此网站**" 文本, 然后单击工具栏中的 "超链接" 图标。</span><span class="sxs-lookup"><span data-stu-id="aab3e-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="aab3e-131">在 **"URL**" **http://www.spamlink.contoso.com/** 中, 键入, 单击 **"确定**", 然后单击 "**发送**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="aab3e-132">在专用浏览模式中打开 Internet Explorer 的单独实例, 转到 Microsoft 365 管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com)), 并使用全局管理员帐户登录到你的 Office 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="aab3e-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="aab3e-133">从主门户页面, 单击 "应用" 磁贴, 然后单击 "**邮件**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="aab3e-134">在 "收件箱" 中, 单击主题为**你的新密钥**的邮件。</span><span class="sxs-lookup"><span data-stu-id="aab3e-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="aab3e-135">在 "垃圾邮件" 文件夹中, 单击主题为 "**新建旅行网站**" 的邮件。</span><span class="sxs-lookup"><span data-stu-id="aab3e-135">In the Junk Mail folder, click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="aab3e-136">在邮件中, 单击 "**此网站**" 链接。</span><span class="sxs-lookup"><span data-stu-id="aab3e-136">Within the message, click the **this site** link.</span></span> <span data-ttu-id="aab3e-137">您应该会看到一个 "抱歉!</span><span class="sxs-lookup"><span data-stu-id="aab3e-137">You should see a "Oops!</span></span> <span data-ttu-id="aab3e-138">Internet Explorer 找不到 spamlink.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="aab3e-138">Internet Explorer could not find spamlink.contoso.com."</span></span> <span data-ttu-id="aab3e-139">页符.</span><span class="sxs-lookup"><span data-stu-id="aab3e-139">page.</span></span> <span data-ttu-id="aab3e-140">这是正确的结果, 因为该位置没有网页。</span><span class="sxs-lookup"><span data-stu-id="aab3e-140">This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="aab3e-141">请注意, 这两个可能的恶意电子邮件已成功传递。</span><span class="sxs-lookup"><span data-stu-id="aab3e-141">Notice that both of these potentially malicious emails were delivered successfully.</span></span> <span data-ttu-id="aab3e-142">**您的新密钥**电子邮件可能包含未检测到的恶意软件, 并允许用户单击**新的旅游网站**电子邮件中的潜在恶意链接。</span><span class="sxs-lookup"><span data-stu-id="aab3e-142">The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="aab3e-143">第3阶段: 为 ATP 配置安全附件和安全链接策略</span><span class="sxs-lookup"><span data-stu-id="aab3e-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="aab3e-144">在此阶段中, 您将创建并配置安全附件策略, 以防止电子邮件发送潜在的恶意附件和安全链接策略, 以防止用户继续使用可能不安全的 url。</span><span class="sxs-lookup"><span data-stu-id="aab3e-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="aab3e-145">在 Internet Explorer 的 " **Microsoft Office 主页**" 选项卡上, 单击 "**管理**" 磁贴。</span><span class="sxs-lookup"><span data-stu-id="aab3e-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="aab3e-146">在左侧导航中, 单击 "**管理中心**", 然后单击 " **Exchange**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="aab3e-147">在 "Exchange 管理中心" 选项卡的左侧导航中, 单击 "**高级威胁**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="aab3e-148">单击 "**安全附件**" 选项卡, 然后单击加号。</span><span class="sxs-lookup"><span data-stu-id="aab3e-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="aab3e-149">在 "**新建安全附件策略**" 窗口中的 "**名称**" 中, 键入**安全附件策略-阻止**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="aab3e-150">对于**安全附件未知的恶意软件响应**, 请单击 "**阻止**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="aab3e-151">对于**检测上的重定向附件**, 请单击 "**启用重定向**", 然后键入 Office 365 全局管理员帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="aab3e-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="aab3e-152">对于 "**应用**于", 单击向下箭头, 然后单击 **"收件人域"**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-152">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="aab3e-153">在窗口中, 单击您的组织名称 (如 contoso.onmicrosoft.com), 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-153">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="aab3e-154">单击“保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aab3e-154">Click **Save**.</span></span> <span data-ttu-id="aab3e-155">更新之后, 您应该会看到新的和已启用的**安全附件策略块**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-155">After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="aab3e-156">单击 "**安全链接**" 选项卡, 然后单击加号。</span><span class="sxs-lookup"><span data-stu-id="aab3e-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="aab3e-157">在 "**新建安全链接策略**" 窗口中的 "**名称**" 中, 键入**安全链接策略**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="aab3e-158">若要为**邮件中未知的潜在恶意 url 选择操作**, 请单击 "**打开**", 然后选择 "**不允许用户单击浏览原始 URL**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="aab3e-159">对于 "**应用**于", 单击向下箭头, 然后单击 **"收件人域"**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-159">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="aab3e-160">在窗口中, 单击您的组织名称 (如 contoso.onmicrosoft.com), 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-160">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="aab3e-161">单击“保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aab3e-161">Click **Save**.</span></span> <span data-ttu-id="aab3e-162">您应该会看到新的和已启用的**安全链接策略**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-162">You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="aab3e-163">第4阶段: 显示操作中的 ATP</span><span class="sxs-lookup"><span data-stu-id="aab3e-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="aab3e-164">在此阶段中, 您将演示 ATP 如何处理潜在的恶意电子邮件。</span><span class="sxs-lookup"><span data-stu-id="aab3e-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="aab3e-165">在第2阶段中用于发送电子邮件的 Internet Explorer 实例, 在左侧导航栏中, 单击 "**已发送邮件"。**</span><span class="sxs-lookup"><span data-stu-id="aab3e-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="aab3e-166">单击标题为**你的新密钥**的电子邮件, 单击向下箭头图标, 然后单击 "**转发**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="aab3e-167">对于新邮件, 在 "**至**" 中, 键入试用订阅的 Office 365 全局管理员名称的电子邮件地址, 然后单击 "**发送**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="aab3e-168">单击标题为 "**新建旅行网站**" 的电子邮件, 单击向下箭头图标, 单击 "**全部答复**", 然后单击 "**发送**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="aab3e-169">在第3阶段中用于配置 ATP 策略的 Internet Explorer 实例中, 单击 "Exchange 管理中心" 选项卡, 单击 "应用" 磁贴, 然后单击 "**邮件**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-169">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**.</span></span> <span data-ttu-id="aab3e-170">您应该会在收件箱中看到两封新电子邮件:</span><span class="sxs-lookup"><span data-stu-id="aab3e-170">You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="aab3e-171">一个标题为**的 Fw: 你的新密钥**</span><span class="sxs-lookup"><span data-stu-id="aab3e-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="aab3e-172">一个标题为的**Fw: 新的旅行网站**</span><span class="sxs-lookup"><span data-stu-id="aab3e-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="aab3e-173">打开标题为 " **Fw: 新建旅行网站**" 的电子邮件, 然后单击 "**此网站**" 链接。</span><span class="sxs-lookup"><span data-stu-id="aab3e-173">Open the email message titled **Fw: New travel web site** and click the **this site** link.</span></span> <span data-ttu-id="aab3e-174">您应该会看到 "此网站已被分类为恶意网站"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-174">You should see a "This website has been classified as malicious."</span></span> <span data-ttu-id="aab3e-175">页符.</span><span class="sxs-lookup"><span data-stu-id="aab3e-175">page.</span></span> <span data-ttu-id="aab3e-176">这表明 ATP 阻止您访问潜在的恶意网站。</span><span class="sxs-lookup"><span data-stu-id="aab3e-176">This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="aab3e-177">在 Internet Explorer 的 "Exchange 管理中心" 选项卡上, 在左侧导航中, 单击 "**邮件流**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="aab3e-178">单击 "**邮件跟踪**" 选项卡, 然后单击 "**搜索**"。</span><span class="sxs-lookup"><span data-stu-id="aab3e-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="aab3e-179">在**邮件跟踪结果**窗口中, 双击主题为**你的新密钥**的邮件。</span><span class="sxs-lookup"><span data-stu-id="aab3e-179">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**.</span></span> <span data-ttu-id="aab3e-180">此邮件已成功传递到收件箱。</span><span class="sxs-lookup"><span data-stu-id="aab3e-180">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="aab3e-181">请关闭此窗口。</span><span class="sxs-lookup"><span data-stu-id="aab3e-181">Close this window.</span></span>
    
10. <span data-ttu-id="aab3e-182">双击带有主题 "**新建旅行网站**" 的邮件。</span><span class="sxs-lookup"><span data-stu-id="aab3e-182">Double-click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="aab3e-183">此邮件已成功传递到收件箱。</span><span class="sxs-lookup"><span data-stu-id="aab3e-183">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="aab3e-184">请关闭此窗口。</span><span class="sxs-lookup"><span data-stu-id="aab3e-184">Close this window.</span></span>
    
11. <span data-ttu-id="aab3e-185">双击带有主题 Fw 的邮件 **: 您的新密钥**。</span><span class="sxs-lookup"><span data-stu-id="aab3e-185">Double-click the message with the subject **Fw: Your new keys**.</span></span> <span data-ttu-id="aab3e-186">请注意, 此邮件是由 ATP 处理的, 然后传递到收件箱。</span><span class="sxs-lookup"><span data-stu-id="aab3e-186">Note how this message was processed by ATP and then delivered to the Inbox.</span></span> <span data-ttu-id="aab3e-187">请关闭此窗口。</span><span class="sxs-lookup"><span data-stu-id="aab3e-187">Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="aab3e-188">安全附件策略的目的是开始扫描附件中的恶意代码。</span><span class="sxs-lookup"><span data-stu-id="aab3e-188">The purpose of the safe attachments policy was to begin scanning attachments for malicious code.</span></span> <span data-ttu-id="aab3e-189">getkeys.js 附件被允许, 因为它未被确定为恶意。</span><span class="sxs-lookup"><span data-stu-id="aab3e-189">The getKeys.js attachment was allowed because it was not determined to be malicious.</span></span> <span data-ttu-id="aab3e-190">此步骤显示 ATP 确实执行了附件扫描。</span><span class="sxs-lookup"><span data-stu-id="aab3e-190">This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="aab3e-191">双击带有主题**Fw: "新建旅行网站**" 的邮件。</span><span class="sxs-lookup"><span data-stu-id="aab3e-191">Double-click the message with the subject **Fw: New travel web site**.</span></span> <span data-ttu-id="aab3e-192">请注意, 此邮件已成功传递到收件箱。</span><span class="sxs-lookup"><span data-stu-id="aab3e-192">Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="aab3e-193">现在, 您可以使用此环境创建新策略并试用 ATP。</span><span class="sxs-lookup"><span data-stu-id="aab3e-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="aab3e-194">单击[此处](http://aka.ms/catlgstack)可查看 Office 365 测试实验室指南堆栈中所有文章的直观映射。</span><span class="sxs-lookup"><span data-stu-id="aab3e-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="aab3e-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aab3e-195">See Also</span></span>

[<span data-ttu-id="aab3e-196">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="aab3e-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="aab3e-197">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="aab3e-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="aab3e-198">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="aab3e-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="aab3e-199">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="aab3e-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="aab3e-200">用于 Office 365 开发/测试环境的云应用安全</span><span class="sxs-lookup"><span data-stu-id="aab3e-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="aab3e-201">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="aab3e-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="aab3e-202">安全附件和安全链接的高级威胁保护</span><span class="sxs-lookup"><span data-stu-id="aab3e-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


