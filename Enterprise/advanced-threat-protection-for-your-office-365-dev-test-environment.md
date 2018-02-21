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
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Office 365 开发/测试环境中的高级威胁防护

 **摘要：**配置并演示 Office 365 高级威胁保护您 Office 365 的开发/测试环境中。
  
Office 365 高级威胁防护 (ATP) 是一种功能的 Exchange 在线保护 (EOP)，可帮助保持您的电子邮件之外的恶意软件。使用 ATP，创建策略在 Exchange 管理员中心 (EAC) 或安全&amp;有助于确保您的用户访问仅链接或被视为不恶意的电子邮件中的附件的法规遵从性中心。有关详细信息，请参阅[安全附件以及安全链接的高级的威胁防护](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)。
  
使用本文中的说明进行操作，可以配置并测试 Office 365 试用订阅中的 ATP。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果您只想测试中达到最低要求的轻量方法的 ATP，按照在阶段 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)。
  
如果您想要测试 ATP 模拟企业中，按照[您 Office 365 的开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。
  
> [!NOTE]
> 测试 ATP 不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试 ATP，并在代表典型组织的环境中对其进行试验。 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>第 2 阶段： 演示 Office 365 的默认电子邮件传递行为

在此阶段，在配置 ATP 策略之前对其进行演示，潜在的恶意电子邮件会不经屏蔽或缓解发送到 Office 365 邮箱。
  
1. 打开 Internet Explorer 并登录到您在第 2 阶段的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中创建 Outlook 帐户。
    
  - 如果使用的是轻型 Office 365 开发/测试环境，请打开 Internet Explorer 的专用会话并从本地计算机登录。
    
  - 如果您使用的模拟的企业 Office 365 开发/测试环境，使用[Azure 门户](https://portal.azure.com)连接到客户端 1 虚拟机，然后从客户端 1 登录。
    
2. 运行记事本，并输入一些文本。
    
3. 为**getKeys.js**，将文件保存到文档文件夹。
    
4. 从 Internet Explorer 的 Outlook 邮件选项卡上，单击**新建**。
    
5. **对**，键入您的订购试用期的 Office 365 全局管理员名称的电子邮件地址。
    
6. 该主题中，键入**新的密钥**。
    
7. 在正文中，键入**下面是文件**。
    
8. 单击**附加**，双击文档文件夹中的**getKeys.js** ，**作为副本的连接**，请单击，然后单击**发送**。
    
9. 单击**新建**。
    
10. **对**，键入您的订购试用期的 Office 365 全局管理员名称的电子邮件地址。
    
11. 该主题中，键入**新建旅游网站**。
    
12. 在正文中，键入**某人转发此网站**。
    
13. 在正文中，选择**此网站**文本，然后单击工具栏中的超链接图标。
    
14. 在**URL**框中，键入**http://www.spamlink.contoso.com/**，单击**确定**，然后单击**发送**。
    
15. 在私人浏览模式下打开一个单独的 Internet Explorer 实例、 转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com))，并登录到您的 Office 365 试用预订使用全局管理员帐户。
    
16. 从主门户页面中，单击应用程序图块，，然后单击**邮件**。
    
17. 在收件箱，主题为**新密钥**中单击该消息。
    
18. 在垃圾邮件文件夹中，单击**新建旅游网站**使用者消息。消息中，单击**网站**链接。您应该看到"Oops ！Internet Explorer 未能找到 spamlink.contoso.com。"页。这是正确的结果，因为在该位置没有 web 页。
    
请注意这两个这些潜在的恶意电子邮件已成功传递。**新的键**电子邮件可能包含未检测到恶意软件，允许用户已单击**新建旅游网站**的电子邮件中的恶意链接。
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>第 3 阶段：为 ATP 配置安全附件和安全链接策略

在此阶段，可以创建并配置安全附件策略，以防止发送带有潜在恶意附件的电子邮件，并且安全链接策略可防止用户转至可能不安全的 URL。
  
1. Internet Explorer **Microsoft Office 主页**选项卡上，单击**管理**拼贴。
    
2. 在左侧的导航中，**中心的管理**，单击，然后单击**Exchange**。
    
3. 在 Exchange 管理员中心选项卡的左侧导航，请单击**高级的威胁**。
    
4. 单击**安全附件**选项卡，然后单击加号。
    
5. 在**新安全附件策略**窗口中，在**名称**中键入**安全附件策略-块**。
    
6. **安全附件未知的恶意软件的响应**，请单击**块**。
    
7. **重定向检测上的附件**，单击**启用定向**然后键入您 Office 365 的全局管理员帐户的电子邮件地址。
    
8. 为**应用于**，单击向下箭头，，然后单击**收件人域是**。在窗口中，单击您的组织名称 （如 contoso.onmicrosoft.com)，，然后单击**确定**。
    
9. 单击**保存**。之后更新程序，您应该可以看到新并启用**安全附件策略-块**。
    
10. 单击**安全链接**选项卡，然后单击加号。
    
11. 在**新安全链接策略**窗口中，在**名称**中键入**安全链接策略**。
    
12. 对于**选择未知的潜在的恶意 Url，在邮件中的操作**，请**在上**，单击，然后选择**不允许用户通过单击到原始 URL**。
    
13. 为**应用于**，单击向下箭头，，然后单击**收件人域是**。在窗口中，单击您的组织名称 （如 contoso.onmicrosoft.com)，，然后单击**确定**。
    
14. 单击**保存**。您应该看到新并启用**安全链接策略**。
    
## <a name="phase-4-show-atp-in-action"></a>第 4 阶段：在操作中显示 ATP

在此阶段，介绍 ATP 如何处理潜在的恶意电子邮件。
  
1. 用于发送电子邮件在阶段 2 中，在左侧导航窗格中的 Internet Explorer 的实例，请单击**已发送的邮件。**
    
2. 单击电子邮件标题为**新密钥**，请单击向下箭头图标，，然后单击**转发**。
    
3. 对于新的消息，**到**，键入您的订购试用期，Office 365 全局管理员名称的电子邮件地址，然后单击**发送**。
    
4. 单击标题为**新建旅游网站**的电子邮件，单击向下箭头图标，单击**全部答复**，，然后单击**发送**。
    
5. 从 Internet Explorer 使用阶段 3 中配置 ATP 策略的实例，单击 Exchange 管理员中心选项卡，应用程序图块，请单击，然后单击**邮件**。您应该看到两个新的电子邮件收件箱：
    
  - 一个名为**Fw： 新密钥**
    
  - 一个名为**Fw： 新的旅游网站**
    
6. 打开电子邮件的标题为**Fw： 新的旅游网站**，然后单击**该站点**链接。您应该看到"此网站已归类为恶意。"页面。这说明了 ATP 阻止您访问恶意的 web 站点。
    
7. 在 Exchange 管理员中心中的选项卡的 Internet Explorer 左侧导航中，单击**邮件流**。
    
8. 单击**邮件跟踪**选项卡，然后单击**搜索**。
    
9. 在**邮件跟踪结果**窗口中，双击主题为**新密钥**的消息。此消息已成功传递到收件箱中。关闭此窗口。
    
10. 双击**新建旅游网站**使用者的消息。此消息已成功传递到收件箱中。关闭此窗口。
    
11. 双击该消息使用者**Fw： 新密钥**。请注意，此消息如何处理由 ATP 并再传递到收件箱。关闭此窗口。
    
    > [!NOTE]
    > 安全的附件策略的目的是开始扫描恶意代码的附件。GetKeys.js 附件已能使用，因为它不取决于恶意。此步骤显示 ATP 未执行的附件进行扫描。 
  
12. 双击该消息使用者**Fw： 新的旅游网站**。请注意，此消息已成功传递到收件箱。
    
现在可以使用此环境创建新策略并测试 ATP。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 开发/测试环境的云应用程序安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md) 

[安全的附件以及安全链接的高级的威胁防护](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


