---
title: "Office 365 开发/测试环境中的高级威胁防护"
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
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "摘要： 配置和演示 Office 365 高级威胁保护您 Office 365 的开发/测试环境中。"
ms.openlocfilehash: 6266960287d06ffafdf7ed1f6690396fd4cda9d5
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="67f78-103">Office 365 开发/测试环境中的高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="67f78-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="67f78-104">**摘要：**配置并演示 Office 365 高级威胁保护您 Office 365 的开发/测试环境中。</span><span class="sxs-lookup"><span data-stu-id="67f78-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="67f78-p101">Office 365 高级威胁防护 (ATP) 是一种功能的 Exchange 在线保护 (EOP)，可帮助保持您的电子邮件之外的恶意软件。使用 ATP，创建策略在 Exchange 管理员中心 (EAC) 或安全&amp;有助于确保您的用户访问仅链接或被视为不恶意的电子邮件中的附件的法规遵从性中心。有关详细信息，请参阅[安全附件以及安全链接的高级的威胁防护](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="67f78-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="67f78-108">使用本文中的说明进行操作，可以配置并测试 Office 365 试用订阅中的 ATP。</span><span class="sxs-lookup"><span data-stu-id="67f78-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="67f78-109">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="67f78-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="67f78-110">如果您只想测试中达到最低要求的轻量方法的 ATP，按照在阶段 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="67f78-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="67f78-111">如果您想要测试 ATP 模拟企业中，按照[您 Office 365 的开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="67f78-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="67f78-p102">测试 ATP 不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试 ATP，并在代表典型组织的环境中对其进行试验。</span><span class="sxs-lookup"><span data-stu-id="67f78-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="67f78-114">第 2 阶段： 演示 Office 365 的默认电子邮件传递行为</span><span class="sxs-lookup"><span data-stu-id="67f78-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="67f78-115">在此阶段，在配置 ATP 策略之前对其进行演示，潜在的恶意电子邮件会不经屏蔽或缓解发送到 Office 365 邮箱。</span><span class="sxs-lookup"><span data-stu-id="67f78-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="67f78-116">打开 Internet Explorer 并登录到您在第 2 阶段的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中创建 Outlook 帐户。</span><span class="sxs-lookup"><span data-stu-id="67f78-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="67f78-117">如果使用的是轻型 Office 365 开发/测试环境，请打开 Internet Explorer 的专用会话并从本地计算机登录。</span><span class="sxs-lookup"><span data-stu-id="67f78-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="67f78-118">如果您使用的模拟的企业 Office 365 开发/测试环境，使用[Azure 门户](https://portal.azure.com)连接到客户端 1 虚拟机，然后从客户端 1 登录。</span><span class="sxs-lookup"><span data-stu-id="67f78-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="67f78-119">运行记事本，并输入一些文本。</span><span class="sxs-lookup"><span data-stu-id="67f78-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="67f78-120">为**getKeys.js**，将文件保存到文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="67f78-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="67f78-121">从 Internet Explorer 的 Outlook 邮件选项卡上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="67f78-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="67f78-122">**对**，键入您的订购试用期的 Office 365 全局管理员名称的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="67f78-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="67f78-123">该主题中，键入**新的密钥**。</span><span class="sxs-lookup"><span data-stu-id="67f78-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="67f78-124">在正文中，键入**下面是文件**。</span><span class="sxs-lookup"><span data-stu-id="67f78-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="67f78-125">单击**附加**，双击文档文件夹中的**getKeys.js** ，**作为副本的连接**，请单击，然后单击**发送**。</span><span class="sxs-lookup"><span data-stu-id="67f78-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="67f78-126">单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="67f78-126">Click **New**.</span></span>
    
10. <span data-ttu-id="67f78-127">**对**，键入您的订购试用期的 Office 365 全局管理员名称的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="67f78-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="67f78-128">该主题中，键入**新建旅游网站**。</span><span class="sxs-lookup"><span data-stu-id="67f78-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="67f78-129">在正文中，键入**某人转发此网站**。</span><span class="sxs-lookup"><span data-stu-id="67f78-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="67f78-130">在正文中，选择**此网站**文本，然后单击工具栏中的超链接图标。</span><span class="sxs-lookup"><span data-stu-id="67f78-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="67f78-131">在**URL**框中，键入**http://www.spamlink.contoso.com/**，单击**确定**，然后单击**发送**。</span><span class="sxs-lookup"><span data-stu-id="67f78-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="67f78-132">在私人浏览模式下打开一个单独的 Internet Explorer 实例、 转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com))，并登录到您的 Office 365 试用预订使用全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="67f78-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="67f78-133">从主门户页面中，单击应用程序图块，，然后单击**邮件**。</span><span class="sxs-lookup"><span data-stu-id="67f78-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="67f78-134">在收件箱，主题为**新密钥**中单击该消息。</span><span class="sxs-lookup"><span data-stu-id="67f78-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="67f78-p103">在垃圾邮件文件夹中，单击**新建旅游网站**使用者消息。消息中，单击**网站**链接。您应该看到"Oops ！Internet Explorer 未能找到 spamlink.contoso.com。"页。这是正确的结果，因为在该位置没有 web 页。</span><span class="sxs-lookup"><span data-stu-id="67f78-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="67f78-p104">请注意这两个这些潜在的恶意电子邮件已成功传递。**新的键**电子邮件可能包含未检测到恶意软件，允许用户已单击**新建旅游网站**的电子邮件中的恶意链接。</span><span class="sxs-lookup"><span data-stu-id="67f78-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="67f78-143">第 3 阶段：为 ATP 配置安全附件和安全链接策略</span><span class="sxs-lookup"><span data-stu-id="67f78-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="67f78-144">在此阶段，可以创建并配置安全附件策略，以防止发送带有潜在恶意附件的电子邮件，并且安全链接策略可防止用户转至可能不安全的 URL。</span><span class="sxs-lookup"><span data-stu-id="67f78-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="67f78-145">Internet Explorer **Microsoft Office 主页**选项卡上，单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="67f78-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="67f78-146">在左侧的导航中，**中心的管理**，单击，然后单击**Exchange**。</span><span class="sxs-lookup"><span data-stu-id="67f78-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="67f78-147">在 Exchange 管理员中心选项卡的左侧导航，请单击**高级的威胁**。</span><span class="sxs-lookup"><span data-stu-id="67f78-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="67f78-148">单击**安全附件**选项卡，然后单击加号。</span><span class="sxs-lookup"><span data-stu-id="67f78-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="67f78-149">在**新安全附件策略**窗口中，在**名称**中键入**安全附件策略-块**。</span><span class="sxs-lookup"><span data-stu-id="67f78-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="67f78-150">**安全附件未知的恶意软件的响应**，请单击**块**。</span><span class="sxs-lookup"><span data-stu-id="67f78-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="67f78-151">**重定向检测上的附件**，单击**启用定向**然后键入您 Office 365 的全局管理员帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="67f78-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="67f78-p105">为**应用于**，单击向下箭头，，然后单击**收件人域是**。在窗口中，单击您的组织名称 （如 contoso.onmicrosoft.com)，，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="67f78-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="67f78-p106">单击**保存**。之后更新程序，您应该可以看到新并启用**安全附件策略-块**。</span><span class="sxs-lookup"><span data-stu-id="67f78-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="67f78-156">单击**安全链接**选项卡，然后单击加号。</span><span class="sxs-lookup"><span data-stu-id="67f78-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="67f78-157">在**新安全链接策略**窗口中，在**名称**中键入**安全链接策略**。</span><span class="sxs-lookup"><span data-stu-id="67f78-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="67f78-158">对于**选择未知的潜在的恶意 Url，在邮件中的操作**，请**在上**，单击，然后选择**不允许用户通过单击到原始 URL**。</span><span class="sxs-lookup"><span data-stu-id="67f78-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="67f78-p107">为**应用于**，单击向下箭头，，然后单击**收件人域是**。在窗口中，单击您的组织名称 （如 contoso.onmicrosoft.com)，，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="67f78-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="67f78-p108">单击**保存**。您应该看到新并启用**安全链接策略**。</span><span class="sxs-lookup"><span data-stu-id="67f78-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="67f78-163">第 4 阶段：在操作中显示 ATP</span><span class="sxs-lookup"><span data-stu-id="67f78-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="67f78-164">在此阶段，介绍 ATP 如何处理潜在的恶意电子邮件。</span><span class="sxs-lookup"><span data-stu-id="67f78-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="67f78-165">用于发送电子邮件在阶段 2 中，在左侧导航窗格中的 Internet Explorer 的实例，请单击**已发送的邮件。**</span><span class="sxs-lookup"><span data-stu-id="67f78-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="67f78-166">单击电子邮件标题为**新密钥**，请单击向下箭头图标，，然后单击**转发**。</span><span class="sxs-lookup"><span data-stu-id="67f78-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="67f78-167">对于新的消息，**到**，键入您的订购试用期，Office 365 全局管理员名称的电子邮件地址，然后单击**发送**。</span><span class="sxs-lookup"><span data-stu-id="67f78-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="67f78-168">单击标题为**新建旅游网站**的电子邮件，单击向下箭头图标，单击**全部答复**，，然后单击**发送**。</span><span class="sxs-lookup"><span data-stu-id="67f78-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="67f78-p109">从 Internet Explorer 使用阶段 3 中配置 ATP 策略的实例，单击 Exchange 管理员中心选项卡，应用程序图块，请单击，然后单击**邮件**。您应该看到两个新的电子邮件收件箱：</span><span class="sxs-lookup"><span data-stu-id="67f78-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="67f78-171">一个名为**Fw： 新密钥**</span><span class="sxs-lookup"><span data-stu-id="67f78-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="67f78-172">一个名为**Fw： 新的旅游网站**</span><span class="sxs-lookup"><span data-stu-id="67f78-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="67f78-p110">打开电子邮件的标题为**Fw： 新的旅游网站**，然后单击**该站点**链接。您应该看到"此网站已归类为恶意。"页面。这说明了 ATP 阻止您访问恶意的 web 站点。</span><span class="sxs-lookup"><span data-stu-id="67f78-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="67f78-177">在 Exchange 管理员中心中的选项卡的 Internet Explorer 左侧导航中，单击**邮件流**。</span><span class="sxs-lookup"><span data-stu-id="67f78-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="67f78-178">单击**邮件跟踪**选项卡，然后单击**搜索**。</span><span class="sxs-lookup"><span data-stu-id="67f78-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="67f78-p111">在**邮件跟踪结果**窗口中，双击主题为**新密钥**的消息。此消息已成功传递到收件箱中。关闭此窗口。</span><span class="sxs-lookup"><span data-stu-id="67f78-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="67f78-p112">双击**新建旅游网站**使用者的消息。此消息已成功传递到收件箱中。关闭此窗口。</span><span class="sxs-lookup"><span data-stu-id="67f78-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="67f78-p113">双击该消息使用者**Fw： 新密钥**。请注意，此消息如何处理由 ATP 并再传递到收件箱。关闭此窗口。</span><span class="sxs-lookup"><span data-stu-id="67f78-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="67f78-p114">安全的附件策略的目的是开始扫描恶意代码的附件。GetKeys.js 附件已能使用，因为它不取决于恶意。此步骤显示 ATP 未执行的附件进行扫描。</span><span class="sxs-lookup"><span data-stu-id="67f78-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="67f78-p115">双击该消息使用者**Fw： 新的旅游网站**。请注意，此消息已成功传递到收件箱。</span><span class="sxs-lookup"><span data-stu-id="67f78-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="67f78-193">现在可以使用此环境创建新策略并测试 ATP。</span><span class="sxs-lookup"><span data-stu-id="67f78-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="67f78-194">单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="67f78-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="67f78-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67f78-195">See Also</span></span>

[<span data-ttu-id="67f78-196">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="67f78-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="67f78-197">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="67f78-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="67f78-198">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="67f78-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="67f78-199">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="67f78-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="67f78-200">Office 365 开发/测试环境的云应用程序安全性</span><span class="sxs-lookup"><span data-stu-id="67f78-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="67f78-201">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="67f78-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="67f78-202">安全的附件以及安全链接的高级的威胁防护</span><span class="sxs-lookup"><span data-stu-id="67f78-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


