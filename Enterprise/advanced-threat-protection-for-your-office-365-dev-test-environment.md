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
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Office 365 开发/测试环境中的高级威胁防护

 **摘要：** 配置并演示 Office 365 开发/测试环境中的 Office 365 高级威胁防护。
  
Office 365 高级威胁保护 (ATP) 是一项功能的 Exchange Online Protection (EOP)，可帮助保持利用您的电子邮件的恶意软件。使用 ATP，创建策略，在 Exchange 管理员中心 (EAC) 或安全&amp;帮助确保您的用户访问仅链接或在标识为不恶意的电子邮件中的附件的合规性中心。有关详细信息，请参阅[高级的威胁保护安全的附件和安全的链接](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)。
  
使用本文中的说明进行操作，可以配置并测试 Office 365 试用订阅中的 ATP。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果您只想要测试 ATP 轻型方式的最低要求，请在阶段 2 和 3 的[Office 365 开发/测试环境](office-365-dev-test-environment.md)按照的说明。
  
如果您想要测试 ATP 模拟企业中，按照[目录同步的 Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明。
  
> [!NOTE]
> 测试 ATP 不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试 ATP，并在代表典型组织的环境中对其进行试验。 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>第 2 阶段： 演示 Office 365 的默认电子邮件传递行为

在此阶段，在配置 ATP 策略之前对其进行演示，潜在的恶意电子邮件会不经屏蔽或缓解发送到 Office 365 邮箱。
  
1. 打开 Internet Explorer 并登录到您在第 2 阶段的[Office 365 开发/测试环境](office-365-dev-test-environment.md)中创建的 Outlook 帐户。
    
  - 如果使用的是轻型 Office 365 开发/测试环境，请打开 Internet Explorer 的专用会话并从本地计算机登录。
    
  - 如果您使用模拟的企业的 Office 365 开发/测试环境，使用[Azure 门户网站](https://portal.azure.com)连接到 CLIENT1 虚拟机，并然后登录从 CLIENT1。
    
2. 运行记事本，并输入一些文本。
    
3. 将文件以 **getKeys.js** 的形式保存到文档文件夹中。
    
4. 在 Internet Explorer 的 Outlook 邮件选项卡上，单击“**新建**”。
    
5. 在“**收件人**”中，输入试用订阅 Office 365 全局管理员名称的电子邮件地址。
    
6. 在主题中，键入**你的新密钥**。
    
7. 在正文中，键入**此处为文件**。
    
8. 单击“**附加**”，双击文档文件夹中的“**getKeys.js**”，单击“**附加为副本**”，然后单击“**发送**”。
    
9. 单击"新建"。
    
10. 在“**收件人**”中，输入试用订阅 Office 365 全局管理员名称的电子邮件地址。
    
11. 在主题中，键入**新旅游网站**。
    
12. 在正文中，键入**某人向我转发此网站**。
    
13. 在正文中，选择“**此网站**”文本，然后单击工具栏中的超链接图标。
    
14. 在**URL**中，键入**http://www.spamlink.contoso.com/**，单击**确定**，，然后单击**发送**。
    
15. 打开 Internet Explorer 的单独实例在专用浏览模式下，都转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com))，并向 Office 365 试用版订阅与全局管理员帐户登录。
    
16. 在主要门户页面上，单击应用磁贴，然后单击“**邮件**”。
    
17. 在收件箱中，单击主题为**你的新密钥**的邮件。
    
18. 在垃圾邮件文件夹中，**新建旅行网站**主题中单击邮件。消息中，单击**此网站**链接。您应该会看到"Oops ！Internet Explorer 找不到 spamlink.contoso.com。"页。这是正确的结果，因为在该位置没有 web 页。
    
请注意，这两封潜在的恶意电子邮件已成功发送。**你的新密钥**电子邮件可能包含未检测到的恶意软件，并允许用户单击**新旅游网站**电子邮件中的潜在恶意链接。
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>第 3 阶段：为 ATP 配置安全附件和安全链接策略

在此阶段，可以创建并配置安全附件策略，以防止发送带有潜在恶意附件的电子邮件，并且安全链接策略可防止用户转至可能不安全的 URL。
  
1. 在 Internet Explorer 的**Microsoft Office Home**选项卡上，单击**管理员**图块。
    
2. 在左侧导航中，单击“**管理中心**”，然后单击“**Exchange**”。
    
3. 在“Exchange 管理中心”选项卡的左侧导航中，单击“**高级威胁**”。
    
4. 单击“**安全附件**”选项卡，然后再单击加号。
    
5. 在**新附件安全策略**窗口中，在**名称**框中，键入**安全附件策略-块**。
    
6. **安全附件未知的恶意软件响应**，单击**阻止**。
    
7. 对于“**重定向检测附件**”，单击“**启用重定向**”，然后键入 Office 365 全局管理员帐户的电子邮件地址。
    
8. 对于**应用于**，单击向下箭头，，然后单击**收件人的域是**。在窗口中，单击您的组织名称 （如 contoso.onmicrosoft.com)，，然后单击**确定**。
    
9. 单击**保存**。更新后，您应该会看到新并启用**安全附件策略-块**。
    
10. 单击“**安全链接**”选项卡，然后再单击加号。
    
11. 在“**新安全链接策略**”窗口的“**名称**”中键入**安全链接策略**。
    
12. 对于“**选择操作以应对邮件中的未知潜在恶意 URL**”，单击“**打开**”，然后选择“**不允许用户单击转到原始 URL**”。
    
13. 对于**应用于**，单击向下箭头，，然后单击**收件人的域是**。在窗口中，单击您的组织名称 （如 contoso.onmicrosoft.com)，，然后单击**确定**。
    
14. 单击“**保存**”。应该会看到新的和已启用的**安全链接策略**。
    
## <a name="phase-4-show-atp-in-action"></a>第 4 阶段：在操作中显示 ATP

在此阶段，介绍 ATP 如何处理潜在的恶意电子邮件。
  
1. 从您用来发送电子邮件在第 2 阶段，在左侧导航窗格中的 Internet Explorer 实例，单击**已发送邮件。**
    
2. 单击电子邮件标题为**您的新密钥**，单击向下箭头图标，，然后单击**转接**。
    
3. 对于新邮件，在“**收件人**”中，键入试用订阅 Office 365 全局管理员名称的电子邮件地址，然后单击“**发送**”。
    
4. 单击电子邮件标题为**新建旅行网站**，单击向下箭头图标，单击**全部答复**，，然后单击**发送**。
    
5. 在第 3 阶段中用于配置 ATP 策略的 Internet Explorer 实例上，单击“Exchange 管理中心”选项卡，单击应用磁贴，然后单击“**邮件**”。应该会在收件箱中看到两封新电子邮件：
    
  - 一封标题为**转发: 你的新密钥**
    
  - 一封标题为**转发: 新旅游网站**
    
6. 打开电子邮件标题为**Fw： 新的旅行网站**，然后单击**此网站**链接。您应看到"此网站已归类为恶意。"页。此示例演示 ATP 阻止您访问潜在的恶意网站。
    
7. 在 Internet Explorer “Exchange 管理中心”选项卡的左侧导航中单击“**邮件流**”。
    
8. 单击“**消息跟踪**”选项卡，然后单击“**搜索**”。
    
9. 在**邮件跟踪结果**窗口中，双击邮件主题为**您的新密钥**。此消息已成功传递到收件箱中。关闭此窗口。
    
10. 双击**新建旅行网站**主题的邮件。此消息已成功传递到收件箱中。关闭此窗口。
    
11. 双击该消息的主题**Fw： 新的密钥**。请注意此消息如何处理由 ATP，然后传递到收件箱。关闭此窗口。
    
    > [!NOTE]
    > 安全附件策略的目的是开始扫描附件的恶意代码。GetKeys.js 附件已允许，因为它不取决于要恶意。此步骤显示 ATP 未执行扫描的附件。 
  
12. 双击该消息的主题**Fw： 新的旅行网站**。请注意，此消息已成功传递到收件箱。
    
现在可以使用此环境创建新策略并测试 ATP。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的云应用安全](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md) 

[安全附件和安全链接的高级威胁保护](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


