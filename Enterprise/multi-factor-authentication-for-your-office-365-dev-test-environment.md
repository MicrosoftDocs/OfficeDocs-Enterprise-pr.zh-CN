---
title: Office 365 开发/测试环境的多重身份验证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
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
ms.openlocfilehash: 453dbc6bda3cfbc6806159d53c9a805c4c6cac97
ms.sourcegitcommit: 8e2760cbcaf564923595147ccf6da468edaed364
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2019
ms.locfileid: "30242074"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Office 365 开发/测试环境的多重身份验证

 **摘要：** 使用发送到 Office 365 开发/测试环境中的智能手机的短信来配置多重身份验证。
  
有关登录到 Office 365 订阅的其他安全级别, 可以启用 Azure 多重身份验证, 这需要使用用户名和密码才能对帐户进行身份验证。对于 Office 365 的多重身份验证, 用户需要确认电话呼叫、在短信中键入验证代码, 或者在正确输入密码后在智能手机上指定应用密码。只有在满足第二个身份验证因素之后, 他们才能登录。 
  
本文介绍如何为特定 Office 365 帐户启用和测试基于短信的身份验证。
  
在开发/测试环境中，设置 Office 365 多重身份验证包含两个阶段：
  
1. 创建 Office 365 开发/测试环境。
    
2. 为 User 2 帐户启用并测试多重身份验证。
    
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可以在 One Microsoft 云测试实验室指南堆栈图中直观转到相应的任何文章。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果只想使用最低要求以轻型方式测试多重身份验证, 请按照[Office 365 开发/测试环境](office-365-dev-test-environment.md)的第2阶段和第3阶段中的说明进行操作。
  
如果要在模拟的企业中测试多重身份验证, 请按照[DirSync for Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。
  
> [!NOTE]
> 测试多重身份验证不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试多重身份验证，并在代表典型组织的环境中对其进行试验。 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>阶段 2：启用和测试 User 2 帐户的多重身份验证

通过以下步骤为 User 2 帐户启用多重身份验证：
  
1. 打开浏览器的单独实例, 转到 office 365 门户 ([https://portal.office.com](https://portal.office.com)), 然后使用全局管理员帐户登录到 office 365 试用订阅。
    
2. 在主门户页上，单击“管理员”****。
    
3. 在左侧导航栏中，单击“用户”>“活动用户”****。
    
4. 在 "活动用户" 窗格中, 单击 "**更多 > 多重身份验证设置**"。
    
5. 在列表中, 选择 "**用户 2** " 帐户。
    
6. 在 "**用户 2** " 部分的 "**快速步骤**" 下, 单击 "**启用**"。
    
7. 在 "**关于启用多重身份验证**" 对话框中, 单击 "**启用多重身份验证**"。
    
8. 在 "**更新成功**" 对话框中, 单击 "**关闭**"。
    
9. 在 " **Microsoft Office 主页**" 选项卡上, 单击右上角的 "用户帐户" 图标, **** 然后单击 "注销"。
    
10. 关闭浏览器实例。
    
完成 User 2 帐户的配置，通过以下步骤，使用短信对其进行验证和测试：
  
1. 打开浏览器的新实例。
    
2. 转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)), 并使用 User 2 帐户 (用户2、\<组织 name>) 和密码登录。
    
3. 登录后, 系统会提示您设置帐户以进行其他安全验证。单击 "**立即设置**"。
    
4. 在 "**其他安全验证**" 页上:
    
  - 选择你所在的国家或地区。
    
  - 键入接收短信的智能手机的电话号码。
    
  - 在**方法**中, 单击 "**通过短信向我发送代码**"。
    
5. 单击“下一步”。****
    
6. 输入智能手机上收到的短信中的验证码, 然后单击 "**验证**"。
    
7. 在 "**步骤 3: 保留现有应用程序**" 页上, 将 "User 2" 帐户的显示应用密码记录在安全位置, 然后单击 "**完成**"。
    
8. 如果这是第一次使用用户2帐户登录, 则系统会提示您更改密码。键入原始密码和新密码两次, 然后单击 "**更新密码" 和 "登录**"。将新密码记录在安全位置。
    
    您应在浏览器的 " **Microsoft Office 主页**" 选项卡上看到 "用户 2" 的 Office 365 门户。
    
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 部署的多重身份验证计划](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

