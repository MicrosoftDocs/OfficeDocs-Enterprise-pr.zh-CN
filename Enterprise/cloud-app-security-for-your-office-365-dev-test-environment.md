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
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>用于 Office 365 开发/测试环境的云应用安全

 **摘要:** 在 office 365 开发/测试环境中配置和演示 office 365 云应用安全性。
  
office 365 云应用安全性 (以前称为 "office 365 高级安全管理") 允许您创建策略来监视 Office 365 订阅中的可疑活动并告知这些活动, 以便您可以调查并采取补救措施退货. 有关详细信息, 请参阅[Office 365 中的云应用安全概述](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。
  
使用本文中的说明, 可以在 Office 365 试用订阅中启用和测试云应用安全性。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可以在 One Microsoft 云测试实验室指南堆栈图中直观转到相应的任何文章。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果只想使用最低要求以轻型方式测试云应用安全性, 请按照[Office 365 开发/测试环境](office-365-dev-test-environment.md)的第2阶段和第3阶段中的说明进行操作。
  
如果要在模拟的企业中测试云应用安全性, 请按照[您的 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。
  
> [!NOTE]
> 测试云应用安全不需要模拟企业开发/测试环境, 其中包括连接到 Internet 的模拟 intranet 和 Windows Server AD 林的目录同步。 此处提供它作为选项, 以便您可以测试云应用安全性并在代表典型组织的环境中进行试验。 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>第2阶段: 启用云应用安全性和创建策略之前

在此过程中, 您将演示在启用云应用安全性之前, 更改用户的角色不会向全局管理员提供电子邮件通知。
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>测试 Office 365 的默认通知行为

1. 转到 Microsoft 365 管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com)), 并使用全局管理员帐户登录到你的 Office 365 试用订阅。
    
  - 如果你使用的是轻型 Office 365 开发/测试环境，请从你的本地计算机登录。
    
  - 如果使用的是模拟企业 Office 365 开发/测试环境, 请使用[Azure 门户](https://portal.azure.com)连接到 CLIENT1 虚拟机, 然后从 CLIENT1 登录。
    
2. 在主门户页上，单击“管理员”****。
    
3. 在左侧导航栏中，单击“用户”>“活动用户”****。
    
4. 	单击“**User 4**”帐户。
    
5. 在“**User 4**”页面上，针对“**角色**”行单击“**编辑**”。
    
6. 在“**编辑用户角色**”页面上，单击“**全局管理员**”，在“**备选电子邮件地址**”中键入“**user4@contoso.com**”，然后单击“**保存**”。单击“**关闭**”两次。
    
7. 	选择左上角的应用启动器图标，然后选择“**邮件**”。
    
8. 等待 30 分钟。 请注意, 收件箱中没有电子邮件通知你将用户4的角色更改为全局管理员。
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>第3阶段: 启用云应用安全性和创建策略

在此过程中, 您将启用云应用安全性并创建新策略, 以向全局管理员帐户发送电子邮件通知, 以了解用户帐户角色的更改。 此过程需要以下内容：
  
- 你的 Office 365 试用订阅的全局管理员帐户名和密码。
    
- 你的 Office 365 试用订阅的 User 5 帐户的名称和密码。
    
### <a name="enable-and-configure-cloud-app-security"></a>启用和配置云应用安全性

1. 转到 Microsoft 365 管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com)), 并使用全局管理员帐户登录到你的 Office 365 试用订阅。
    
2. 单击“管理员”磁贴****。 在 " **Office 管理中心**" 选项卡上, 单击 "**管理中心" > Security & 合规性**。
    
3. 在左侧导航窗格中, 单击 "**通知 > 管理高级警报**"。
    
4. 在 "**管理高级通知**" 页面上, 单击 "**启用 office 365 云应用安全性**", 然后单击 "**转到 office 365 云应用安全性**"。
    
5. 在 "新建**仪表板**" 选项卡上, 单击 "**控制 > 策略**"。
    
6. 在 "**策略**" 页上, 单击 "**创建策略**", 然后单击 "**活动策略**"。
    
7. 在 "**策略名称**" 中, 键入 "**管理活动**"。
    
8. 在“**策略严重性**”中，单击“**高**”。
    
9. 在 "**类别**" 中, 单击 "**特权帐户**"。
    
10. 在 **"为策略创建筛选器**" 中, 在**匹配以下所有**项的活动中, 单击 "**管理活动**"。
    
11. 在“**警报**”中，单击“**作为电子邮件发送警报**”。在“**收件人**”中，键入你的全局管理员帐户的电子邮件地址。
    
12. 在页面底部，单击“**创建**”。
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>第4阶段: 显示操作中的云应用安全

在此过程中, 您将演示云应用安全性如何在用户4使用户5成为密码和用户管理管理员时创建通知并向全局管理员帐户发送电子邮件通知。
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>演示用户帐户角色更改的电子邮件通知

1. 在右上方，单击用户图标，然后单击“**注销**”。
    
2. 转到 [https://www.office.com](https://www.office.com)。
    
3. 在 Office 365 登录页面上，单击“**使用其他帐户**”。
    
4. 键入 User 4 的帐户名及其密码，然后单击“**登录**”。
    
5. 如果需要，请更改 User 4 的帐户密码，然后单击“**更新密码并登录**”。
    
6. 在 Office 365 门户页面上，单击“**管理员**”。
    
7. 如果需要，请在系统提示更新管理员联系信息时单击“**取消**”。
    
8. 在主要门户页面上，单击“**管理员**”。
    
9. 在左侧导航窗格中，单击“**用户 > 活动用户**”。
    
10. 单击“**User 5**”帐户。
    
11. 在“**User 5**”页面上，针对“**角色**”行单击“**编辑**”。
    
12. 在“**编辑用户角色**”页面上，依次单击“**自定义管理员**”、“**密码管理员**”和“**用户管理管理员**”，在“**备选电子邮件地址**”中键入“**user5@contoso.com**”，然后单击“**保存**”。单击“**关闭**”两次。
    
13. 单击右上方的用户图标，然后单击“**注销**”。 
    
14. 转到 [https://www.office.com](https://www.office.com)。
    
15. 在“**Office 365 登录**”页面上，单击你的全局管理员帐户名。
    
16. 键入密码，然后单击“**登录**”。
    
17. 在 "Office 365 门户" 页中, 单击 "**管理**"。
    
18. 单击 "**安全&amp;符合性**磁贴"。
    
19. 在左侧导航窗格中, 单击 "**通知 > 管理高级警报**"。
    
20. 在 "**管理高级通知**" 页上, 单击 "**转到 Office 365 云应用安全性**"。
    
21. 在 "新建**仪表板**" 选项卡上, 请注意两个用于**管理活动**的新警报。
    
22. 在 " **Microsoft Office 主页**" 选项卡上, 单击 "**邮件**"。 最多等待 30 分钟。 
    
    您应该会在收件箱中看到两封新电子邮件, 标题为**Microsoft Azure AD 通知服务**。 一条消息指示已将用户5帐户添加到**密码管理员**角色, 另一条消息指示已将用户5帐户添加到**用户管理员**角色 (等于中的用户管理管理员角色)。Office 365 管理中心)。
    
现在, 你可以使用此环境创建新策略, 并对 Office 365 云应用安全性进行进一步实验。 有关指向其他配置文章的链接, 请参阅[获取 Office 365 云应用安全性的准备](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)工作。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 中的云应用安全概述](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


