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
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 摘要： 配置和演示 Office 365 开发/测试环境中的 Office 365 云应用程序安全性。
ms.openlocfilehash: d62524b6c4373c851a67b4039146ad8b6a610790
ms.sourcegitcommit: 3a4ab28f3f4172d596426f0da40bcab8c46ef74d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2018
ms.locfileid: "20215874"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>用于 Office 365 开发/测试环境的云应用安全

 **摘要：** 配置和演示 Office 365 开发/测试环境中的 Office 365 云应用程序安全性。
  
Office 365 云应用程序安全性，以前称为 Office 365 高级安全管理，允许您创建的监视和通知您在 Office 365 订阅中，可疑活动，以便可以调查，并采取可能的策略修复操作。有关详细信息，请参阅[概述的云应用程序中的安全性 Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。
  
使用本文中的说明，您可以启用和测试您的 Office 365 试用版订阅中的云应用程序安全性。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果您只想要测试的最低硬件要求与轻型方式中的云应用程序安全性，请在阶段 2 和 3 的[Office 365 开发/测试环境](office-365-dev-test-environment.md)中按照说明。
  
如果您想要测试模拟企业中的云应用程序安全性，请按照[目录同步的 Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明。
  
> [!NOTE]
> 测试的云应用程序安全性不需要模拟的企业开发/测试环境中，包括连接到 Internet 模拟的 intranet 和 Windows Server AD 林目录同步。它提供此处作为一个选项，以便可以测试云应用程序安全性，并与之试验环境值，该值代表典型组织中。 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>第 2 阶段： 之前启用云应用程序安全性和创建策略

在此过程中，您可以演示，然后再启用云应用程序安全性，更改用户的角色提供了无电子邮件通知给全局管理员。
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>测试 Office 365 的默认通知行为

1. 转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 和 Office 365 试用版订阅与全局管理员帐户登录。
    
  - 如果你使用的是轻型 Office 365 开发/测试环境，请从你的本地计算机登录。
    
  - 如果您使用模拟的企业的 Office 365 开发/测试环境，使用[Azure 门户网站](https://portal.azure.com)连接到 CLIENT1 虚拟机，并然后登录从 CLIENT1。
    
2. 在主门户页上，单击“管理员”****。
    
3. 在左侧导航栏中，单击“用户”>“活动用户”****。
    
4. 	单击“**User 4**”帐户。
    
5. 在“**User 4**”页面上，针对“**角色**”行单击“**编辑**”。
    
6. 在“**编辑用户角色**”页面上，单击“**全局管理员**”，在“**备选电子邮件地址**”中键入“**user4@contoso.com**”，然后单击“**保存**”。单击“**关闭**”两次。
    
7. 	选择左上角的应用启动器图标，然后选择“**邮件**”。
    
8. 等待 30 分钟。请注意，通知您以全局管理员的用户 4 角色中的更改的收件箱中没有任何电子邮件消息。
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>第 3 阶段： 启用云应用程序安全性，并创建策略

在此过程中，您将启用云应用程序安全性，并创建新策略，以向您的用户帐户角色中的更改的全局管理员帐户发送电子邮件通知。此过程需要：
  
- 你的 Office 365 试用订阅的全局管理员帐户名和密码。
    
- 你的 Office 365 试用订阅的 User 5 帐户的名称和密码。
    
### <a name="enable-and-configure-cloud-app-security"></a>启用和配置云应用程序安全性

1. 转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 和 Office 365 试用版订阅与全局管理员帐户登录。
    
2. 单击**管理员**图块。在**Office Admin center**选项卡上单击**管理中心 > 安全和合规性**。
    
3. 在左侧的导航窗格中，单击**通知 > 管理高级通知**。
    
4. 在**高级通知的管理**页上，单击**打开 Office 365 云应用程序安全性**，然后单击**转到 Office 365 云应用程序安全性**。
    
5. 在新的**仪表板**选项卡，单击**控件 > 策略**。
    
6. 在**策略**页上，单击**创建策略**，，然后单击**活动策略**。
    
7. 在**策略名称**框中，键入**管理活动**。
    
8. 在“**策略严重性**”中，单击“**高**”。
    
9. 在**类别**中，单击**特权的帐户**。
    
10. 在**创建筛选器策略**，在**以下所有条件匹配的活动**中，单击**管理活动**。
    
11. 在“**警报**”中，单击“**作为电子邮件发送警报**”。在“**收件人**”中，键入你的全局管理员帐户的电子邮件地址。
    
12. 在页面底部，单击“**创建**”。
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>在操作的第 4 阶段： 显示云应用程序安全性

在此过程中，可以将演示如何云应用程序安全性创建通知和时用户 4 使用户 5 的密码和用户管理管理员向的全局管理员帐户发送电子邮件通知。
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>演示用户帐户角色更改的电子邮件通知

1. 在右上角，单击用户图标，然后单击**注销**。
    
2. 转到[https://portal.office.com](https://portal.office.com)。
    
3. 在 Office 365 登录页面上，单击“**使用其他帐户**”。
    
4. 键入 User 4 的帐户名及其密码，然后单击“**登录**”。
    
5. 如果需要，请更改 User 4 的帐户密码，然后单击“**更新密码并登录**”。
    
6. 在 Office 365 门户页面上，单击“**管理员**”。
    
7. 如果需要，请在系统提示更新管理员联系信息时单击“**取消**”。
    
8. 在主门户页上，单击“管理员”****。
    
9. 在左侧导航栏中，单击“用户”>“活动用户”****。
    
10. 单击“**User 5**”帐户。
    
11. 在“**User 5**”页面上，针对“**角色**”行单击“**编辑**”。
    
12. 在“**编辑用户角色**”页面上，依次单击“**自定义管理员**”、“**密码管理员**”和“**用户管理管理员**”，在“**备选电子邮件地址**”中键入“**user5@contoso.com**”，然后单击“**保存**”。单击“**关闭**”两次。
    
13. 单击右上角中的用户图标，然后单击**注销**。 
    
14. 转到[https://portal.office.com](https://portal.office.com)。
    
15. 在“**Office 365 登录**”页面上，单击你的全局管理员帐户名。
    
16. 键入密码，然后单击“**登录**”。
    
17. 在主门户页上，单击“管理员”****。
    
18. 单击**安全&amp;合规性**平铺。
    
19. 在左侧的导航窗格中，单击**通知 > 管理高级通知**。
    
20. 在**高级通知的管理**页上，单击**转到 Office 365 云应用程序安全性**。
    
21. 在新**仪表板**选项卡，请注意**管理**活动的两个新通知。
    
22. 从**Microsoft Office Home**选项卡，单击**邮件**。等待最多 30 分钟。 
    
    您应看到两个新的电子邮件收件箱具有标题**Microsoft Azure AD 通知服务**。一条消息指示用户 5 帐户已添加到的**密码管理员**角色和另一条消息指示用户 5 帐户已添加到**用户管理员**角色 (等于中的用户管理管理员角色Office 365 Admin center)。
    
您现在可以使用此环境以创建新策略，并进一步试用 Office 365 云应用程序安全性。其他配置文章的链接，请参阅[为 Office 365 云应用程序安全性做好准备](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 中的云应用程序安全性概述](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


