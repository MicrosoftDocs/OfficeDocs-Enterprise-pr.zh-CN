---
title: "Office 365 开发/测试环境的多重身份验证"
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
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "摘要： 配置使用文本消息发送到 Office 365 的开发/测试环境中的智能电话的多因素身份验证。"
ms.openlocfilehash: 23c5aa4e205937899cac813b3b39780c989a1073
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Office 365 开发/测试环境的多重身份验证

 **摘要：**配置使用文本消息发送到智能手机在 Office 365 的开发/测试环境中的多因素身份验证。
  
对于登录 Office 365 订阅的其他安全级别，可以启用 Azure 多重身份验证，这需要使用用户名和密码之外的其他内容来验证帐户。使用适用于 Office 365 的多重身份验证时，用户需要在正确输入密码后确认智能手机上的电话呼叫、键入通过短信发送的验证码或指定应用密码。仅在满足第二个身份验证因素时才能登录。  
  
本文介绍如何为特定 Office 365 帐户启用和测试基于短信的身份验证。
  
在开发/测试环境中，设置 Office 365 多重身份验证包含两个阶段：
  
1. 创建 Office 365 开发/测试环境。
    
2. 为 User 2 帐户启用并测试多重身份验证。
    
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果您只是想要测试中达到最低要求的轻量方法的多因素身份验证，则按照在阶段 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)的说明。
  
如果您想要测试中模拟企业的多因素身份验证，请按[您 Office 365 的开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)。
  
> [!NOTE]
> 测试多重身份验证不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试多重身份验证，并在代表典型组织的环境中对其进行试验。 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>阶段 2：启用和测试 User 2 帐户的多重身份验证

通过以下步骤为 User 2 帐户启用多重身份验证：
  
1. 打开一个单独的浏览器实例，请转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com))，然后登录到您的 Office 365 试用预订使用全局管理员帐户。
    
2. 从主门户页面中，单击**管理**。
    
3. 在左边的导航，请单击**用户 > 活动用户**。
    
4. 在活动用户窗格中，单击**更 > 设置 Azure 多因素身份验证**。
    
5. 在列表中，单击**用户 2**帐户。
    
6. 在**用户 2**部分下**快速步骤**中, 单击**启用**。
    
7. **有关启用多因素身份验证**对话框中，单击**启用多因素身份验证**。
    
8. 在**更新成功**对话框中，单击**关闭**。
    
9. **Microsoft Office 主页**选项卡上，单击右上方的用户帐户图标，然后单击**注销**。
    
10. 关闭浏览器实例。
    
完成 User 2 帐户的配置，通过以下步骤，使用短信对其进行验证和测试：
  
1. 打开浏览器的新实例。
    
2. 请转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com)) 和登录用户 2 帐户 (用户 @ 2\<组织名称 >。 onmicrosoft.com) 和密码。
    
3. 登录后，您可以设置额外的安全验证的帐户。单击**立即设置**。
    
4. 在**更高的安全性验证**页上：
    
  - 选择你所在的国家或地区。
    
  - 键入接收短信的智能手机的电话号码。
    
  - 选择**向我发送文本消息的代码**。
    
5. 单击**我的联系人**。
    
6. 从智能手机上收到的短信输入验证码，然后单击**验证**。
    
7. 在**第 3 步： 保留现有的应用程序**页上，在一个安全的位置，记录用户 2 帐户的显示应用程序密码，然后单击**完成**。
    
8. 重新打开登录页中，键入用户 2 帐户的密码，然后单击**登录**。
    
9. 从智能手机上收到的短信输入验证码，然后单击**登录**。
    
10. 如果是第一次您登录用户 2 帐户，系统会提示您更改密码。两次，输入原密码和新密码，然后单击**更新密码并登录**。在一个安全的位置中记录新的密码。
    
    应能看到 User 2 的 Office 365 门户。
    
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)

[多因素身份验证对于 Office 365 的部署计划](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

