---
title: "Office 365 和 Dynamics 365 开发/测试环境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: "摘要： 使用此测试实验室指南 Dynamics 365 添加到 Office 365 开发/测试环境。"
ms.openlocfilehash: f13cf81f989867e543439e1ccb6ecd7f8ba55cb6
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 和 Dynamics 365 开发/测试环境

 **摘要：**此测试实验室指南用于 Dynamics 365 添加到 Office 365 开发/测试环境。
  
使用本文中的说明进行操作，将 Dynamics 365 试用订阅作为 Office 365 开发/测试环境添加到同一个组织，创建一个 Office 365 和 Dynamics 365 开发/测试环境。
  
可将 Dynamics 365 试用订阅用于演示 Dynamics 365 的功能和特性。Dynamics 365 计划 1（企业版试用）包括以下解决方案：
  
- [Microsoft Dynamics 365 的销售](https://www.microsoft.com/dynamics365/sales)。提高您的销售自动化和数字智能帮助您的销售人员，将主要精力和更智能地工作。
    
- [Microsoft Dynamics 365 为客户服务](https://www.microsoft.com/dynamics365/customer-service)。通过为您的代理的完整信息和数字智能所需提供无缝服务获得会员。
    
- [Microsoft Dynamics 365 的现场服务](https://www.microsoft.com/dynamics365/field-service)。主服务调用通过优化您的日程，安装企业员工，使用预防性工具来增加利润。
    
- [Microsoft Dynamics 365 项目服务自动化的](https://www.microsoft.com/en-us/dynamics365/project-service-automation)。成功地完成您的项目和员工工作效率和智能工具创建有利的关系。
    
可以浏览上述一个或多个网站以获取 Dynamics 365 试用订阅。
  
![Microsoft 云中的测试实验室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果您只想测试中达到最低要求的轻量级方法 Office 365 和 Dynamics 365，按照在阶段 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)。
  
如果您想要测试 Office 365 和 Dynamics 365 模拟的企业，按照[目录同步为您 Office 365 的开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。
  
> [!NOTE]
> 本文中的配置不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试 Office 365 和 Dynamics 365，并在代表典型组织的环境中对其进行试验。 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>第 2 阶段：添加 Dynamics 365 试用订阅

在此阶段，注册 Dynamics 365 试用订阅，并将其作为 Office 365 试用订阅添加到同一组织。
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>注册 Dynamics 365 试用订阅

1. 台式计算机 （轻型） 上使用浏览器或客户端 1 （模拟企业），到 Office 365 门户网站位于[https://portal.office.com](https://portal.office.com)的全局管理员帐户凭据登录。
    
2. 单击“管理”磁贴。
    
3. **办公室管理中心**选项卡上，左边的导航，请单击**计费 > 购买服务**。
    
4. **购买服务**页上找到**Dynamics 365 计划 1 企业版**项目。将鼠标指针悬停在其上，单击**启动免费试用版**。
    
5. 在“确认订单”页中，单击“立即试用”。
    
6. 在“订单签收”页中，单击“继续”。
    
> [!NOTE]
> Dynamics 365 计划 1 企业版订阅试用期是 30 天。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>第 3 阶段：分配 Dynamics 365 许可证和系统管理员

在此阶段中，将 Dynamics 365 许可证分配给全局管理员、用户 2 和用户 3 的帐户并使之成为系统管理员。
  
使用下列步骤分配 Dynamics 365 许可证。
  
1. 在**Office 管理员中心**选项卡，单击**用户 > 活动用户**。
    
2. 在活动的用户的列表中，单击您的全局管理员帐户，然后单击**编辑****产品**许可证。
    
3. 在**产品许可证**窗格中**Dynamics 365 计划 1 企业版**对**上**打开产品许可证、 单击**保存**，然后两次单击**关闭**。
    
4. 为用户 2 和用户 3 的帐户执行步骤 2 和步骤 3。
    
5. 关闭**Office 管理员中心**选项卡。
    
使用以下步骤将用户 2 和用户 3 的帐户配置为 Dynamics 365 系统管理员。
  
1. 从**Microsoft Office 主页**选项卡上，单击**管理**。
    
2. **Office 管理中心**选项卡上，在左边的导航**中心管理**，请单击，然后单击**Dynamics 365**。
    
    可能需要等到 Dynamics 365 完成预配后，菜单中才会显示 Dynamics 365。
    
3. Dynamics 365 选项卡上，单击**所有这些**，然后单击**完成安装。**
    
    等待设置完成。
    
    安装完成后，它会显示基于样本数据跟踪订阅的一部分销售活动仪表板。花一些时间查看**欢迎您的试用版**视频。关闭完成后视频窗口。
    
4. 在顶部的工具栏上，单击**销售**旁的下箭头，单击**设置**，然后单击**安全**。
    
5. 在**安全**页中，单击**用户**。
    
6. 在用户列表中，单击**用户 2**。
    
7. 在工具栏上，单击**管理角色**。
    
8. **管理角色**，单击**系统管理员**，然后单击**确定**。
    
9. 在顶部的工具栏中单击**安全**。
    
10. 为用户 3 帐户重复步骤 5 到 8。
    
11. 关闭**用户： 用户 3**选项卡。
    
> [!NOTE]
> 已为 Office 365 全局管理员帐户自动分配了 Dynamics 365 系统管理员角色。 
  
现在，你的 Office 365 和 Dynamics 365 开发/测试环境包含：
  
- 与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版和 Dynamics 365 试用订阅。
    
- 全局企业管理员、用户 2 和用户 3 的帐户都可以使用 Office 365 E5 企业版和 Dynamics 365，并且它们都是 Dynamics 365 系统管理员。
    
## <a name="next-step"></a>后续步骤

配置，然后说明如何 Office 365 和 Dynamics 365 结合使用[Office 365 和 Dynamics 365 开发/测试环境](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)的 Exchange 联机集成在 Exchange 在线邮箱。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[Dynamics 365（联机）的订阅管理](https://technet.microsoft.com/library/jj679903.aspx)
  
[管理 Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


