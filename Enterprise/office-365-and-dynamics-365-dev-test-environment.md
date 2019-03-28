---
title: Office 365 和 Dynamics 365 开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 摘要：使用本测试实验室指南将 Dynamics 365 添加到 Office 365 开发/测试环境。
ms.openlocfilehash: 9e4c98129c68ab5d2f0d9fc486ab62740c625af5
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574056"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 和 Dynamics 365 开发/测试环境

 **摘要：** 使用本测试实验室指南将 Dynamics 365 添加到 Office 365 开发/测试环境。
  
使用本文中的说明进行操作，将 Dynamics 365 试用订阅作为 Office 365 开发/测试环境添加到同一个组织，创建一个 Office 365 和 Dynamics 365 开发/测试环境。

![Office 365 和 Dynamics 365 开发/测试环境](media/o365-dynamics365-dev-test.png)
  
  
可将 Dynamics 365 试用订阅用于演示 Dynamics 365 的功能和特性。Dynamics 365 计划 1（企业版试用）包括以下解决方案：
  
- [Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales)。通过自动化和数字智能提高销售量，帮助销售人员保持专注并高效工作。
    
- [Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service)。通过为代理提供所需的完整信息和数字智能获取忠诚度，从而提供无缝服务。
    
- [Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service)。通过优化日程安排、配备员工以及使用预测工具来控制服务请求，从而增加利润。
    
- [Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/zh-CN/dynamics365/project-service-automation)。成功完成项目，并通过高效率员工和智能工具构建盈利性关系。
    
可以浏览上述一个或多个网站以获取 Dynamics 365 试用订阅。
  
![Microsoft 云中的测试实验室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可以在 One Microsoft 云测试实验室指南堆栈图中直观转到相应的任何文章。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果只需要测试达到最低要求的轻型 Office 365 和 Dynamics 365，请按照 [Office 365 开发/测试环境](office-365-dev-test-environment.md)中第 2 阶段和第 3 阶段的说明进行操作。
  
如果想要为模拟的企业测试 Office 365 和 Dynamics 365，请按照[适用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md) 中的说明进行操作。

![Office 365 开发/测试环境](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> 本文中的配置不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试 Office 365 和 Dynamics 365，并在代表典型组织的环境中对其进行试验。 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>第 2 阶段：添加 Dynamics 365 试用订阅

在此阶段，注册 Dynamics 365 试用订阅，并将其作为 Office 365 试用订阅添加到同一组织。
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>注册 Dynamics 365 试用订阅

1. 通过台式计算机（轻型）或 CLIENT1（模拟企业）上的浏览器，使用全局管理员帐户登录至 Microsoft 365 管理中心（地址为 [https://admin.microsoft.com](https://admin.microsoft.com)）。
    
2. 单击“管理员”磁贴****。
    
3. 在“**Microsoft 365 管理中心**”选项卡上的左侧导航栏中，单击“**计费 > 购买服务**”。
    
4. 在“购买服务”页上，找到“Dynamics 365 计划 1 企业版”项。将鼠标指针悬停在此项之上，然后单击“开始免费试用”************。
    
5. 在“确认订单”页上，单击“立即试用”********。
    
6. 在“订单签收”**** 页上，单击“继续”****。

![Office 365 和 Dynamics 365 开发/测试环境](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> Dynamics 365 计划 1 企业版订阅试用期是 30 天。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>第 3 阶段：分配 Dynamics 365 许可证和系统管理员

在此阶段中，将 Dynamics 365 许可证分配给全局管理员、用户 2 和用户 3 的帐户并使之成为系统管理员。
  
使用下列步骤分配 Dynamics 365 许可证。
  
1. 在“**Microsoft 365 管理中心**”选项卡上，单击“**用户 > 活动用户**”。
    
2. 在活动用户列表中，单击全局管理员帐户，然后针对“产品许可证”**** 单击“编辑”****。
    
3. 在“产品许可证”窗格上，将“Dynamics 365 计划 1 企业版”的产品许可证设置为“打开”，单击“保存”，然后单击“关闭”两次********************。
    
4. 为用户 2 和用户 3 的帐户执行步骤 2 和步骤 3。
    
5. 关闭 **Microsoft 365 管理员中心**选项卡。
    
使用以下步骤将用户 2 和用户 3 的帐户配置为 Dynamics 365 系统管理员。
  
1. 在“Microsoft Office 主页”**** 选项卡上，单击“管理员”****。
    
2. 在“Office 管理中心”**** 标签页的左侧导航中，单击“管理中心”****，然后单击“Dynamics 365”****。
    
    可能需要等到 Dynamics 365 完成设置后，菜单中才会显示 Dynamics 365。
    
3. 在 Dynamics 365 选项卡上，单击“所有内容”，然后单击“完成设置”********。
    
    等待设置完成。
    
    设置完成后，它会基于试用订阅中示例数据显示一个销售活动仪表板。请花点时间来观看“欢迎使用试用版”**** 视频。完成后关闭视频窗口。
    
4. 在顶部工具栏上，单击“销售”旁边的向下箭头，单击“设置”，然后单击“安全”************。
    
5. 在“安全”页上，单击“用户”********。
    
6. 在用户列表中，单击“用户 2”****。
    
7. 在工具栏中，单击“管理角色”****。
    
8. 在“管理角色”中，单击“系统管理员”，然后单击“确定”************。
    
9. 在顶部工具栏中单击“安全”****。
    
10. 为用户 3 帐户重复步骤 5 到 8。
    
11. 关闭“用户：User3”**** 选项卡。
    
> [!NOTE]
> 已为 Office 365 全局管理员帐户自动分配了 Dynamics 365 系统管理员角色。 
  
现在，你的 Office 365 和 Dynamics 365 开发/测试环境包含：
  
- 与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版和 Dynamics 365 试用订阅。
    
- 全局企业管理员、用户 2 和用户 3 的帐户都可以使用 Office 365 E5 企业版和 Dynamics 365，并且它们都是 Dynamics 365 系统管理员。
    
## <a name="next-step"></a>后续步骤

配置然后演示 Office 365 和 Dynamics 365 如何通过[适用于 Office 365 和 Dynamics 365 开发/测试环境的 Exchange Online 集成](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)在 Exchange Online 邮箱中协作。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[Dynamics 365（联机）的订阅管理](https://technet.microsoft.com/library/jj679903.aspx)
  
[管理 Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


