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
ms.openlocfilehash: 9870f666a979d00ce6621e9459a1f9ad236f9799
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573826"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Office 365 开发/测试环境中的高级威胁防护

 **摘要:** 在 office 365 开发/测试环境中配置和演示 office 365 高级威胁防护。
  
Office 365 高级威胁防护 (ATP) 是 Exchange Online Protection (EOP) 的一项功能, 可帮助您的电子邮件阻止恶意软件。 使用 ATP, 可以在 Exchange 管理中心 (EAC) 或安全&amp;合规中心中创建策略, 以确保您的用户仅访问电子邮件中标识为非恶意的链接或附件。 有关详细信息，请参阅[安全附件和安全链接的高级威胁保护](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)。
  
使用本文中的说明, 可以在 Office 365 试用订阅中配置和测试 ATP。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果只想使用最低要求以轻量方式测试 ATP, 请按照[Office 365 开发/测试环境](office-365-dev-test-environment.md)的第2阶段和第3阶段中的说明进行操作。
  
如果要在模拟企业版中测试 ATP, 请按照[您的 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。
  
> [!NOTE]
> 测试 ATP 不需要模拟的企业开发/测试环境, 其中包括连接到 Internet 的模拟 intranet 和 Windows Server AD 林的目录同步。 此处提供它作为选项, 以便您可以在代表典型组织的环境中测试 ATP 并进行实验。 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>第2阶段: 演示 Office 365 的默认电子邮件传递行为

在此阶段中, 您将演示在配置 ATP 策略之前, 潜在的恶意电子邮件将被传递到 Office 365 邮箱, 而不会进行屏蔽或缓解。
  
1. 打开 Internet Explorer, 并登录到在[Office 365 开发/测试环境](office-365-dev-test-environment.md)的第2阶段中创建的 Outlook 帐户。
    
  - 如果使用的是轻型 Office 365 开发/测试环境, 请打开 Internet Explorer 的专用会话并从本地计算机登录。
    
  - 如果使用的是模拟企业 Office 365 开发/测试环境, 请使用[Azure 门户](https://portal.azure.com)连接到 CLIENT1 虚拟机, 然后从 CLIENT1 登录。
    
2. 运行记事本并输入一些文本。
    
3. 将文件作为**getkeys.js**保存到 Documents 文件夹中。
    
4. 在 Internet Explorer 的 "Outlook 邮件" 选项卡上, 单击 "**新建**"。
    
5. 在 " **To**" 中, 键入试用订阅的 Office 365 全局管理员名称的电子邮件地址。
    
6. 对于 "主题", 请键入**新密钥**。
    
7. 在正文中, 键入**此处为文件**。
    
8. 单击 "**附加**", 双击 "文档" 文件夹中的 " **getkeys.js** ", 单击 "**附加为副本**", 然后单击 "**发送**"。
    
9. 单击"新建"。
    
10. 在 " **To**" 中, 键入试用订阅的 Office 365 全局管理员名称的电子邮件地址。
    
11. 对于 "主题", 键入 "**新建旅行网站**"。
    
12. 在正文中, 键入**某人向我转发此网站**。
    
13. 在正文中, 选择 "**此网站**" 文本, 然后单击工具栏中的 "超链接" 图标。
    
14. 在 **"URL**" **http://www.spamlink.contoso.com/** 中, 键入, 单击 **"确定**", 然后单击 "**发送**"。
    
15. 在专用浏览模式中打开 Internet Explorer 的单独实例, 转到 Microsoft 365 管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com)), 并使用全局管理员帐户登录到你的 Office 365 试用订阅。
    
16. 从主门户页面, 单击 "应用" 磁贴, 然后单击 "**邮件**"。
    
17. 在 "收件箱" 中, 单击主题为**你的新密钥**的邮件。
    
18. 在 "垃圾邮件" 文件夹中, 单击主题为 "**新建旅行网站**" 的邮件。 在邮件中, 单击 "**此网站**" 链接。 您应该会看到一个 "抱歉! Internet Explorer 找不到 spamlink.contoso.com。 页符. 这是正确的结果, 因为该位置没有网页。
    
请注意, 这两个可能的恶意电子邮件已成功传递。 **您的新密钥**电子邮件可能包含未检测到的恶意软件, 并允许用户单击**新的旅游网站**电子邮件中的潜在恶意链接。
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>第3阶段: 为 ATP 配置安全附件和安全链接策略

在此阶段中, 您将创建并配置安全附件策略, 以防止电子邮件发送潜在的恶意附件和安全链接策略, 以防止用户继续使用可能不安全的 url。
  
1. 在 Internet Explorer 的 " **Microsoft Office 主页**" 选项卡上, 单击 "**管理**" 磁贴。
    
2. 在左侧导航中, 单击 "**管理中心**", 然后单击 " **Exchange**"。
    
3. 在 "Exchange 管理中心" 选项卡的左侧导航中, 单击 "**高级威胁**"。
    
4. 单击 "**安全附件**" 选项卡, 然后单击加号。
    
5. 在 "**新建安全附件策略**" 窗口中的 "**名称**" 中, 键入**安全附件策略-阻止**。
    
6. 对于**安全附件未知的恶意软件响应**, 请单击 "**阻止**"。
    
7. 对于**检测上的重定向附件**, 请单击 "**启用重定向**", 然后键入 Office 365 全局管理员帐户的电子邮件地址。
    
8. 对于 "**应用**于", 单击向下箭头, 然后单击 **"收件人域"**。 在窗口中, 单击您的组织名称 (如 contoso.onmicrosoft.com), 然后单击 **"确定"**。
    
9. 单击“保存”****。 更新之后, 您应该会看到新的和已启用的**安全附件策略块**。
    
10. 单击 "**安全链接**" 选项卡, 然后单击加号。
    
11. 在 "**新建安全链接策略**" 窗口中的 "**名称**" 中, 键入**安全链接策略**。
    
12. 若要为**邮件中未知的潜在恶意 url 选择操作**, 请单击 "**打开**", 然后选择 "**不允许用户单击浏览原始 URL**"。
    
13. 对于 "**应用**于", 单击向下箭头, 然后单击 **"收件人域"**。 在窗口中, 单击您的组织名称 (如 contoso.onmicrosoft.com), 然后单击 **"确定"**。
    
14. 单击“保存”****。 您应该会看到新的和已启用的**安全链接策略**。
    
## <a name="phase-4-show-atp-in-action"></a>第4阶段: 显示操作中的 ATP

在此阶段中, 您将演示 ATP 如何处理潜在的恶意电子邮件。
  
1. 在第2阶段中用于发送电子邮件的 Internet Explorer 实例, 在左侧导航栏中, 单击 "**已发送邮件"。**
    
2. 单击标题为**你的新密钥**的电子邮件, 单击向下箭头图标, 然后单击 "**转发**"。
    
3. 对于新邮件, 在 "**至**" 中, 键入试用订阅的 Office 365 全局管理员名称的电子邮件地址, 然后单击 "**发送**"。
    
4. 单击标题为 "**新建旅行网站**" 的电子邮件, 单击向下箭头图标, 单击 "**全部答复**", 然后单击 "**发送**"。
    
5. 在第3阶段中用于配置 ATP 策略的 Internet Explorer 实例中, 单击 "Exchange 管理中心" 选项卡, 单击 "应用" 磁贴, 然后单击 "**邮件**"。 您应该会在收件箱中看到两封新电子邮件:
    
  - 一个标题为**的 Fw: 你的新密钥**
    
  - 一个标题为的**Fw: 新的旅行网站**
    
6. 打开标题为 " **Fw: 新建旅行网站**" 的电子邮件, 然后单击 "**此网站**" 链接。 您应该会看到 "此网站已被分类为恶意网站"。 页符. 这表明 ATP 阻止您访问潜在的恶意网站。
    
7. 在 Internet Explorer 的 "Exchange 管理中心" 选项卡上, 在左侧导航中, 单击 "**邮件流**"。
    
8. 单击 "**邮件跟踪**" 选项卡, 然后单击 "**搜索**"。
    
9. 在**邮件跟踪结果**窗口中, 双击主题为**你的新密钥**的邮件。 此邮件已成功传递到收件箱。 请关闭此窗口。
    
10. 双击带有主题 "**新建旅行网站**" 的邮件。 此邮件已成功传递到收件箱。 请关闭此窗口。
    
11. 双击带有主题 Fw 的邮件 **: 您的新密钥**。 请注意, 此邮件是由 ATP 处理的, 然后传递到收件箱。 请关闭此窗口。
    
    > [!NOTE]
    > 安全附件策略的目的是开始扫描附件中的恶意代码。 getkeys.js 附件被允许, 因为它未被确定为恶意。 此步骤显示 ATP 确实执行了附件扫描。 
  
12. 双击带有主题**Fw: "新建旅行网站**" 的邮件。 请注意, 此邮件已成功传递到收件箱。
    
现在, 您可以使用此环境创建新策略并试用 ATP。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)，可以在“One Microsoft 云测试实验室指南”堆栈图中直观转到相应的文章。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的云应用安全](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md) 

[安全附件和安全链接的高级威胁保护](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


