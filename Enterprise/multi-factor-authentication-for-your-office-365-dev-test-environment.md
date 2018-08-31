---
title: Office 365 开发/测试环境的多重身份验证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
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
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 摘要：使用发送到 Office 365 开发/测试环境中的智能手机的短信来配置多重身份验证。
ms.openlocfilehash: 12458e2dd41518deb0b540e809a08c4df865a3df
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915657"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Office 365 开发/测试环境的多重身份验证

 **摘要：** 使用发送到 Office 365 开发/测试环境中的智能手机的短信来配置多重身份验证。
  
对于登录 Office 365 订阅的其他安全级别，可以启用 Azure 多重身份验证，这需要使用用户名和密码之外的其他内容来验证帐户。使用适用于 Office 365 的多重身份验证时，用户需要在正确输入密码后确认智能手机上的电话呼叫、键入通过短信发送的验证码或指定应用密码。仅在满足第二个身份验证因素时才能登录。  
  
本文介绍如何为特定 Office 365 帐户启用和测试基于短信的身份验证。
  
在开发/测试环境中，设置 Office 365 多重身份验证包含两个阶段：
  
1. 创建 Office 365 开发/测试环境。
    
2. 为 User 2 帐户启用并测试多重身份验证。
    
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果您只想要测试的最低硬件要求与轻型方式中的多因素身份验证，请在阶段 2 和 3 的[Office 365 开发/测试环境](office-365-dev-test-environment.md)中按照说明。
  
如果您想要测试模拟企业中的多因素身份验证，请按照[目录同步的 Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明。
  
> [!NOTE]
> 测试多重身份验证不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试多重身份验证，并在代表典型组织的环境中对其进行试验。 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>阶段 2：启用和测试 User 2 帐户的多重身份验证

通过以下步骤为 User 2 帐户启用多重身份验证：
  
1. 打开一个单独的浏览器实例，请转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com))，然后向 Office 365 试用版订阅与全局管理员帐户登录。
    
2. 在主门户页上，单击“管理员”****。
    
3. 在左侧导航栏中，依次单击“用户”和“活动用户”****。
    
4. 在活动用户窗格中，单击**更多 > 安装 Azure 多因素身份验证**。
    
5. 在列表中，选择的**用户 2**帐户。
    
6. 在**用户 2**部分中，单击**快速步骤**下的**启用**。
    
7. 在**有关启用多重身份验证**对话框中，单击**启用多重身份验证**。
    
8. 在**更新成功**对话框中，单击**关闭**。
    
9. 在**Microsoft Office Home**选项卡上，单击右上方中的用户帐户图标，然后单击**注销**。
    
10. 关闭浏览器实例。
    
完成 User 2 帐户的配置，通过以下步骤，使用短信对其进行验证和测试：
  
1. 打开浏览器的新实例。
    
2. 转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 和使用用户 2 帐户的登录 (user2 @\<组织名称 >。 onmicrosoft.com) 和密码。
    
3. 在登录后被提示设置的其他安全验证的帐户。单击**立即设置**。
    
4. 在**其他安全验证**页上：
    
  - 选择你所在的国家或地区。
    
  - 键入接收短信的智能手机的电话号码。
    
  - 在**方法**中，单击**给我发送的短信代码**。
    
5. 单击"下一步"。
    
6. 输入介于智能手机上收到的文本消息验证代码，然后单击**验证**。
    
7. 在**步骤 3： 保留现有的应用程序**页上，在安全的位置，记录用户 2 帐户的显示应用程序密码，然后单击**完成**。
    
8. 如果这是首次您使用登录用户 2 帐户后，在系统提示您要更改的密码。两次，键入原始密码和新密码，然后单击**更新密码和登录**。记录在安全位置的新密码。
    
    您应在浏览器的**Microsoft Office Home**选项卡上看到用户 2 的 Office 365 门户。
    
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)

[规划多因素身份验证的 Office 365 部署](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

