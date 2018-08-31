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
description: 摘要：配置并演示 Office 365 开发/测试环境中的 Office 365 高级威胁防护。
ms.openlocfilehash: 07411600db11c8eea825c0ef5b82ea1206d20e11
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914957"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="eef42-103">Office 365 开发/测试环境中的高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="eef42-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="eef42-104">**摘要：** 配置并演示 Office 365 开发/测试环境中的 Office 365 高级威胁防护。</span><span class="sxs-lookup"><span data-stu-id="eef42-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="eef42-p101">Office 365 高级威胁保护 (ATP) 是一项功能的 Exchange Online Protection (EOP)，可帮助保持利用您的电子邮件的恶意软件。使用 ATP，创建策略，在 Exchange 管理员中心 (EAC) 或安全&amp;帮助确保您的用户访问仅链接或在标识为不恶意的电子邮件中的附件的合规性中心。有关详细信息，请参阅[高级的威胁保护安全的附件和安全的链接](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="eef42-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="eef42-108">使用本文中的说明进行操作，可以配置并测试 Office 365 试用订阅中的 ATP。</span><span class="sxs-lookup"><span data-stu-id="eef42-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="eef42-109">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="eef42-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="eef42-110">如果您只想要测试 ATP 轻型方式的最低要求，请在阶段 2 和 3 的[Office 365 开发/测试环境](office-365-dev-test-environment.md)按照的说明。</span><span class="sxs-lookup"><span data-stu-id="eef42-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="eef42-111">如果您想要测试 ATP 模拟企业中，按照[目录同步的 Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="eef42-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="eef42-p102">测试 ATP 不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试 ATP，并在代表典型组织的环境中对其进行试验。</span><span class="sxs-lookup"><span data-stu-id="eef42-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="eef42-114">第 2 阶段： 演示 Office 365 的默认电子邮件传递行为</span><span class="sxs-lookup"><span data-stu-id="eef42-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="eef42-115">在此阶段，在配置 ATP 策略之前对其进行演示，潜在的恶意电子邮件会不经屏蔽或缓解发送到 Office 365 邮箱。</span><span class="sxs-lookup"><span data-stu-id="eef42-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="eef42-116">打开 Internet Explorer 并登录到您在第 2 阶段的[Office 365 开发/测试环境](office-365-dev-test-environment.md)中创建的 Outlook 帐户。</span><span class="sxs-lookup"><span data-stu-id="eef42-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="eef42-117">如果使用的是轻型 Office 365 开发/测试环境，请打开 Internet Explorer 的专用会话并从本地计算机登录。</span><span class="sxs-lookup"><span data-stu-id="eef42-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="eef42-118">如果您使用模拟的企业的 Office 365 开发/测试环境，使用[Azure 门户网站](https://portal.azure.com)连接到 CLIENT1 虚拟机，并然后登录从 CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="eef42-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="eef42-119">运行记事本，并输入一些文本。</span><span class="sxs-lookup"><span data-stu-id="eef42-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="eef42-120">将文件以 **getKeys.js** 的形式保存到文档文件夹中。</span><span class="sxs-lookup"><span data-stu-id="eef42-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="eef42-121">在 Internet Explorer 的 Outlook 邮件选项卡上，单击“**新建**”。</span><span class="sxs-lookup"><span data-stu-id="eef42-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="eef42-122">在“**收件人**”中，输入试用订阅 Office 365 全局管理员名称的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="eef42-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="eef42-123">在主题中，键入**你的新密钥**。</span><span class="sxs-lookup"><span data-stu-id="eef42-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="eef42-124">在正文中，键入**此处为文件**。</span><span class="sxs-lookup"><span data-stu-id="eef42-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="eef42-125">单击“**附加**”，双击文档文件夹中的“**getKeys.js**”，单击“**附加为副本**”，然后单击“**发送**”。</span><span class="sxs-lookup"><span data-stu-id="eef42-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="eef42-126">单击"新建"。</span><span class="sxs-lookup"><span data-stu-id="eef42-126">Click **New**.</span></span>
    
10. <span data-ttu-id="eef42-127">在“**收件人**”中，输入试用订阅 Office 365 全局管理员名称的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="eef42-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="eef42-128">在主题中，键入**新旅游网站**。</span><span class="sxs-lookup"><span data-stu-id="eef42-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="eef42-129">在正文中，键入**某人向我转发此网站**。</span><span class="sxs-lookup"><span data-stu-id="eef42-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="eef42-130">在正文中，选择“**此网站**”文本，然后单击工具栏中的超链接图标。</span><span class="sxs-lookup"><span data-stu-id="eef42-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="eef42-131">在**URL**中，键入**http://www.spamlink.contoso.com/**，单击**确定**，，然后单击**发送**。</span><span class="sxs-lookup"><span data-stu-id="eef42-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="eef42-132">打开 Internet Explorer 的单独实例在专用浏览模式下，都转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com))，并向 Office 365 试用版订阅与全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="eef42-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="eef42-133">在主要门户页面上，单击应用磁贴，然后单击“**邮件**”。</span><span class="sxs-lookup"><span data-stu-id="eef42-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="eef42-134">在收件箱中，单击主题为**你的新密钥**的邮件。</span><span class="sxs-lookup"><span data-stu-id="eef42-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="eef42-p103">在垃圾邮件文件夹中，**新建旅行网站**主题中单击邮件。消息中，单击**此网站**链接。您应该会看到"Oops ！Internet Explorer 找不到 spamlink.contoso.com。"页。这是正确的结果，因为在该位置没有 web 页。</span><span class="sxs-lookup"><span data-stu-id="eef42-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="eef42-p104">请注意，这两封潜在的恶意电子邮件已成功发送。**你的新密钥**电子邮件可能包含未检测到的恶意软件，并允许用户单击**新旅游网站**电子邮件中的潜在恶意链接。</span><span class="sxs-lookup"><span data-stu-id="eef42-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="eef42-143">第 3 阶段：为 ATP 配置安全附件和安全链接策略</span><span class="sxs-lookup"><span data-stu-id="eef42-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="eef42-144">在此阶段，可以创建并配置安全附件策略，以防止发送带有潜在恶意附件的电子邮件，并且安全链接策略可防止用户转至可能不安全的 URL。</span><span class="sxs-lookup"><span data-stu-id="eef42-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="eef42-145">在 Internet Explorer 的**Microsoft Office Home**选项卡上，单击**管理员**图块。</span><span class="sxs-lookup"><span data-stu-id="eef42-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="eef42-146">在左侧导航中，单击“**管理中心**”，然后单击“**Exchange**”。</span><span class="sxs-lookup"><span data-stu-id="eef42-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="eef42-147">在“Exchange 管理中心”选项卡的左侧导航中，单击“**高级威胁**”。</span><span class="sxs-lookup"><span data-stu-id="eef42-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="eef42-148">单击“**安全附件**”选项卡，然后再单击加号。</span><span class="sxs-lookup"><span data-stu-id="eef42-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="eef42-149">在**新附件安全策略**窗口中，在**名称**框中，键入**安全附件策略-块**。</span><span class="sxs-lookup"><span data-stu-id="eef42-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="eef42-150">**安全附件未知的恶意软件响应**，单击**阻止**。</span><span class="sxs-lookup"><span data-stu-id="eef42-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="eef42-151">对于“**重定向检测附件**”，单击“**启用重定向**”，然后键入 Office 365 全局管理员帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="eef42-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="eef42-p105">对于**应用于**，单击向下箭头，，然后单击**收件人的域是**。在窗口中，单击您的组织名称 （如 contoso.onmicrosoft.com)，，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="eef42-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="eef42-p106">单击**保存**。更新后，您应该会看到新并启用**安全附件策略-块**。</span><span class="sxs-lookup"><span data-stu-id="eef42-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="eef42-156">单击“**安全链接**”选项卡，然后再单击加号。</span><span class="sxs-lookup"><span data-stu-id="eef42-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="eef42-157">在“**新安全链接策略**”窗口的“**名称**”中键入**安全链接策略**。</span><span class="sxs-lookup"><span data-stu-id="eef42-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="eef42-158">对于“**选择操作以应对邮件中的未知潜在恶意 URL**”，单击“**打开**”，然后选择“**不允许用户单击转到原始 URL**”。</span><span class="sxs-lookup"><span data-stu-id="eef42-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="eef42-p107">对于**应用于**，单击向下箭头，，然后单击**收件人的域是**。在窗口中，单击您的组织名称 （如 contoso.onmicrosoft.com)，，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="eef42-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="eef42-p108">单击“**保存**”。应该会看到新的和已启用的**安全链接策略**。</span><span class="sxs-lookup"><span data-stu-id="eef42-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="eef42-163">第 4 阶段：在操作中显示 ATP</span><span class="sxs-lookup"><span data-stu-id="eef42-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="eef42-164">在此阶段，介绍 ATP 如何处理潜在的恶意电子邮件。</span><span class="sxs-lookup"><span data-stu-id="eef42-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="eef42-165">从您用来发送电子邮件在第 2 阶段，在左侧导航窗格中的 Internet Explorer 实例，单击**已发送邮件。**</span><span class="sxs-lookup"><span data-stu-id="eef42-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="eef42-166">单击电子邮件标题为**您的新密钥**，单击向下箭头图标，，然后单击**转接**。</span><span class="sxs-lookup"><span data-stu-id="eef42-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="eef42-167">对于新邮件，在“**收件人**”中，键入试用订阅 Office 365 全局管理员名称的电子邮件地址，然后单击“**发送**”。</span><span class="sxs-lookup"><span data-stu-id="eef42-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="eef42-168">单击电子邮件标题为**新建旅行网站**，单击向下箭头图标，单击**全部答复**，，然后单击**发送**。</span><span class="sxs-lookup"><span data-stu-id="eef42-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="eef42-p109">在第 3 阶段中用于配置 ATP 策略的 Internet Explorer 实例上，单击“Exchange 管理中心”选项卡，单击应用磁贴，然后单击“**邮件**”。应该会在收件箱中看到两封新电子邮件：</span><span class="sxs-lookup"><span data-stu-id="eef42-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="eef42-171">一封标题为**转发: 你的新密钥**</span><span class="sxs-lookup"><span data-stu-id="eef42-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="eef42-172">一封标题为**转发: 新旅游网站**</span><span class="sxs-lookup"><span data-stu-id="eef42-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="eef42-p110">打开电子邮件标题为**Fw： 新的旅行网站**，然后单击**此网站**链接。您应看到"此网站已归类为恶意。"页。此示例演示 ATP 阻止您访问潜在的恶意网站。</span><span class="sxs-lookup"><span data-stu-id="eef42-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="eef42-177">在 Internet Explorer “Exchange 管理中心”选项卡的左侧导航中单击“**邮件流**”。</span><span class="sxs-lookup"><span data-stu-id="eef42-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="eef42-178">单击“**消息跟踪**”选项卡，然后单击“**搜索**”。</span><span class="sxs-lookup"><span data-stu-id="eef42-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="eef42-p111">在**邮件跟踪结果**窗口中，双击邮件主题为**您的新密钥**。此消息已成功传递到收件箱中。关闭此窗口。</span><span class="sxs-lookup"><span data-stu-id="eef42-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="eef42-p112">双击**新建旅行网站**主题的邮件。此消息已成功传递到收件箱中。关闭此窗口。</span><span class="sxs-lookup"><span data-stu-id="eef42-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="eef42-p113">双击该消息的主题**Fw： 新的密钥**。请注意此消息如何处理由 ATP，然后传递到收件箱。关闭此窗口。</span><span class="sxs-lookup"><span data-stu-id="eef42-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="eef42-p114">安全附件策略的目的是开始扫描附件的恶意代码。GetKeys.js 附件已允许，因为它不取决于要恶意。此步骤显示 ATP 未执行扫描的附件。</span><span class="sxs-lookup"><span data-stu-id="eef42-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="eef42-p115">双击该消息的主题**Fw： 新的旅行网站**。请注意，此消息已成功传递到收件箱。</span><span class="sxs-lookup"><span data-stu-id="eef42-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="eef42-193">现在可以使用此环境创建新策略并测试 ATP。</span><span class="sxs-lookup"><span data-stu-id="eef42-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="eef42-194">单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="eef42-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="eef42-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eef42-195">See Also</span></span>

[<span data-ttu-id="eef42-196">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="eef42-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="eef42-197">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="eef42-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="eef42-198">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="eef42-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="eef42-199">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="eef42-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="eef42-200">用于 Office 365 开发/测试环境的云应用安全</span><span class="sxs-lookup"><span data-stu-id="eef42-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="eef42-201">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="eef42-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="eef42-202">安全附件和安全链接的高级威胁保护</span><span class="sxs-lookup"><span data-stu-id="eef42-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


