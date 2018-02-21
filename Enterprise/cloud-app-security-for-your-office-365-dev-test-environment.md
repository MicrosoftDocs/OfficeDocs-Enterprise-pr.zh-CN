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
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "摘要： 配置和您 Office 365 的开发/测试环境中演示 Office 365 云应用程序安全性。"
ms.openlocfilehash: ac5f5c25ecb4d97ac1c8fe3b48096ee02da2ec3e
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Office 365 开发/测试环境的云应用程序安全性

 **摘要：**配置和您 Office 365 的开发/测试环境中演示 Office 365 云应用程序安全性。
  
Office 365 云应用程序的安全性，以前称为 Office 365 高级安全管理，使您可以创建用于监视和通知您在您的 Office 365 订阅的可疑活动，以便可以调查，并采取可能的策略补救行动。有关详细信息，请参阅[概述的云应用程序安全的 Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。
  
使用本文中的说明进行操作，您可以启用和在您的 Office 365 试用测试云应用程序安全。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果您只需要达到最低要求的轻量方式测试云应用程序安全，按照在阶段 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)。
  
如果您想要测试中模拟企业的云应用程序的安全，请按[您 Office 365 的开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)。
  
> [!NOTE]
> 测试云应用程序的安全不需要模拟的企业开发/测试环境，其中包括连接到 Internet 的模拟内部网和 Windows 服务器 AD 林中的目录同步。它提供此处作为一个选项，以便可以测试云应用程序安全性并试验它代表典型的组织的环境中。 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>第 2 阶段： 之前启用云应用程序安全和创建策略

在此过程中，您展示，在启用云应用程序的安全之前, 更改用户的角色提供了无电子邮件通知给全局管理员。
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>测试 Office 365 的默认通知行为

1. 请转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com)) 并登录到您的 Office 365 试用预订使用全局管理员帐户。
    
  - 如果你使用的是轻型 Office 365 开发/测试环境，请从你的本地计算机登录。
    
  - 如果您使用的模拟的企业 Office 365 开发/测试环境，使用[Azure 门户](https://portal.azure.com)连接到客户端 1 虚拟机，然后从客户端 1 登录。
    
2. 从主门户页面中，单击**管理**。
    
3. 在左边的导航，请单击**用户 > 活动用户**。
    
4. 单击**用户 4**帐户。
    
5. 在**用户 4**页上，单击**角色**行的**编辑**。
    
6. 在**编辑用户角色**页上单击**全局管理员**、**备选电子邮件地址**，键入**user4@contoso.com** ，然后单击**保存**。两次单击**关闭**。
    
7. 在左上方选择的应用程序启动器图标并选择**邮件**。
    
8. 等待 30 分钟。请注意在收件箱通知您这一变化中以全局管理员身份的用户 4 角色没有任何电子邮件。
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>阶段 3： 启用云应用程序的安全，并创建策略

在此过程中，您可以启用云应用程序安全和创建新的策略将电子邮件通知发送给您的更改用户帐户角色的全局管理员帐户。此过程要求：
  
- 你的 Office 365 试用订阅的全局管理员帐户名和密码。
    
- 你的 Office 365 试用订阅的 User 5 帐户的名称和密码。
    
### <a name="enable-and-configure-cloud-app-security"></a>启用和配置云应用程序安全

1. 请转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com)) 并登录到您的 Office 365 试用预订使用全局管理员帐户。
    
2. 单击**安全&amp;法规遵从性**平铺。
    
3. 在左侧的导航窗格中，单击**通知 > 高级警报管理**。
    
4. 在**高级警报管理**页上，单击**打开 Office 365 云应用程序安全性**，然后单击**转到 Office 365 云应用程序的安全**。
    
5. 在新的**仪表板**选项卡，单击**控件 > 策略**。
    
6. 在**策略**页面上单击**创建策略**，然后单击**活动策略**。
    
7. 在**策略名称**中，键入**管理活动**。
    
8. 在**策略严重级别**，单击**高**。
    
9. 在**类别**，请单击**特权的帐户**。
    
10. 在**创建筛选器的策略**，在**匹配以下所有的活动**中，请单击**管理活动**。
    
11. 在**警报**，单击**将预警作为电子邮件发送**。**对**，键入您的全局管理员帐户的电子邮件地址。
    
12. 在页面的底部，单击**创建**。
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>阶段 4： 显示云应用程序安全性操作

在此过程中，演示了云应用程序安全性如何创建警报，以及当用户 4 5 用户密码和用户管理员全局管理员帐户发送电子邮件通知。
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>演示用户帐户角色更改的电子邮件通知

1. 在右上角，单击用户图标，然后单击**注销**。
    
2. 转到[https://portal.office.com](https://portal.office.com)。
    
3. 在 Office 365 提供登录页面，请单击**使用另一个帐户**。
    
4. 4 用户帐户名和密码，键入，然后单击**登录**。
    
5. 如果需要请更改用户 4 帐户密码，并单击**更新密码并登录**。
    
6. 在 Office 365 门户页面上，单击**管理**。
    
7. 如果需要请单击**取消**，当系统提示您更新您的管理员联系信息。
    
8. 从主门户页面中，单击**管理**。
    
9. 在左边的导航，请单击**用户 > 活动用户**。
    
10. 单击**用户 5**帐户。
    
11. 在**用户 5**页上，单击**角色**行的**编辑**。
    
12. 在**编辑用户角色**页中，单击**自定义管理员****密码管理员**和**用户管理员**的**备选电子邮件地址**，键入**user5@contoso.com**和，然后单击**保存**。两次单击**关闭**。
    
13. 单击右上角的用户图标，然后单击**注销**。 
    
14. 转到[https://portal.office.com](https://portal.office.com)。
    
15. 在**Office 365 提供登录**页面上，单击您的全局管理员帐户名。
    
16. 键入密码，然后单击**登录**。
    
17. 从主门户页面中，单击**管理**。
    
18. 单击**安全&amp;法规遵从性**平铺。
    
19. 在左侧的导航窗格中，单击**通知 > 高级警报管理**。
    
20. 在**高级警报管理**页上，单击**转到 Office 365 云应用程序的安全**。
    
21. 新的**仪表板**选项卡上，请注意**管理**活动的两个新的警报。
    
22. **Microsoft Office 主页**选项卡中，单击**邮件**。等待 30 分钟。 
    
    您应该看到两个新的电子邮件收件箱，标题为**Microsoft Azure 广告通知服务**。一条消息指示用户 5 帐户已添加到**管理员密码**角色，和另一条消息指示用户 5 帐户已添加到**用户管理员**角色 (等于中的用户管理管理员角色Office 365 管理中心）。
    
您现在可以使用此环境中进一步试用 Office 365 云应用程序安全地创建新的策略。配置其他文章的链接，请参阅[为 Office 365 云应用程序安全做好准备](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 中的云应用程序安全性的概述](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


