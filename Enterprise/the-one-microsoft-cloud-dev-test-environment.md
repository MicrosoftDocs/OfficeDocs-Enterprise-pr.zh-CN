---
title: One Microsoft 云开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 摘要：使用本测试实验室指南创建包含所有 Microsoft 云产品/服务的开发/测试环境。
ms.openlocfilehash: b8ffd01c9d129d4537c82f0e1f74bd7c1be1388b
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037946"
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a>One Microsoft 云开发/测试环境

 **摘要：** 使用本测试实验室指南创建包含所有 Microsoft 云产品/服务的开发/测试环境。
  
按照本文中的说明，你可以在 Microsoft Azure 基础结构服务中创建模拟 Intranet，然后添加 Microsoft Office 365、Microsoft 企业移动性 + 安全性 (EMS) 和 Microsoft Dynamics 365 订阅。结果是，得到简化的组织可以在单个开发/测试环境中同时使用所有 Microsoft 云产品/服务。 
  
![包含 Azure、Office 365、EMS 和 Dynamics 365 的 One Microsoft 云开发/测试环境的第 3 阶段](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
你可以使用生成的配置执行以下操作：
  
- 体验 Microsoft 云服务的集成，例如 Azure Active Directory (AD) 提供的通用身份基础结构。
    
- 评估包含多个 Microsoft 云产品/服务的端到端方案。
    
- 创建使用多种 Microsoft 云产品/服务的演示、概念验证或开发/测试配置。
    
- 为专业开发构建你的 Microsoft 云技能。
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a>第 1 阶段：创建一个模拟 Intranet 并添加 Office 365

按照[适用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md) 中的说明进行操作。
  
图 1 显示了你生成的配置，其中包括 Office 365 和在 Azure 基础结构服务中运行的模拟 Intranet，以及本地 Active Directory 域服务 (AD DS) 林中的目录同步。
  
**图 1：包含 Office 365 的 Azure 中的模拟 Intranet**

![包含 DirSync 的 Office 365 开发/测试环境](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> Azure 试用期为 30 天。Office 365 企业版 E5 试用版的订阅期为 30 天，可以轻松延长 30 天。对于永久性开发/测试环境，使用少量许可证创建新的付费 Azure 订阅和新的付费 Office 365 企业版 E5 订阅。 
  
## <a name="phase-2-add-ems"></a>第 2 阶段：添加 EMS

在此阶段，注册 EMS 试用订阅，并将其作为 Office 365 试用订阅添加到同一组织。
  
1. 通过台式计算机或 CLIENT1 上的浏览器，使用全局管理员帐户的凭据登录 Office 365 门户（地址为 [https://www.office.com](https://www.office.com)）。
    
2. 单击“管理员”磁贴****。
    
3. 在浏览器的“Office 管理中心”标签页的左侧导航中，单击“帐单”>“购买服务”********。
    
4. 在“购买服务”页上，找到“企业移动性 + 安全性 E5”项。将鼠标指针悬停在此项之上，然后单击“开始免费试用”************。
    
5. 在“确认订单”页上，单击“立即试用”********。
    
6. 在“订单签收”页上，单击“继续”********。
    
> [!NOTE]
> 企业移动性 + 安全性 E5 的试订阅期为 90 天。对于永久性开发/测试环境，请使用少量许可证新建付费订阅。 
  
接下来，为所有用户帐户启用企业移动性 + 安全性 E5 许可证。
  
1. 在浏览器的“Office 365 管理中心”标签页的左侧导航中，单击“用户”>“活动用户”********。
    
2. 单击全局管理员帐户，然后针对“产品许可证”单击“编辑”********。
    
3. 在“产品许可证”窗格中，将“企业移动性 + 安全性 E5”的产品许可证设置为“打开”，单击“保存”，然后单击“关闭”两次********************。
    
4. 对于所有其他帐户（用户 1、用户 2、用户 3、用户 4 和用户 5），请执行步骤 2 和 3。
    
开发/测试环境目前包含：
  
- 在 Azure 基础结构服务中运行的模拟 Intranet。
    
- 与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版和 EMS 试用订阅。
    
- 启用所有用户帐户以使用 Office 365 E5 企业版和 EMS。
    
图 2 显示添加 EMS 的生成配置。
  
**图 2：包含 Office 365 和 EMS 的 Azure 中的模拟 Intranet**

![包含 Azure、Office 365 和 EMS 的 One Microsoft 云开发/测试环境的第 2 阶段](media/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a>第 3 阶段：添加 Dynamics 365

在此阶段，注册 Dynamics 365 试用订阅，并将其作为 Office 365 和 EMS 试用订阅添加到同一组织。
  
1. 通过台式计算机或 CLIENT1 上的浏览器，使用全局管理员帐户的凭据登录 Office 365 门户（地址为 [https://www.office.com](https://www.office.com)）。
    
2. 单击“管理员”磁贴****。
    
3. 在“**Microsoft 365 管理中心**”选项卡上的左侧导航栏中，单击“**计费 > 购买服务**”。
    
4. 在“购买服务”页上，找到“Dynamics 365 计划 1 企业版”项。将鼠标指针悬停在此项之上，然后单击“开始免费试用”************。
    
5. 在“确认订单”页上，单击“立即试用”********。
    
6. 在“订单签收”页上，单击“继续”********。
    
> [!NOTE]
> Dynamics 365 计划 1 企业版订阅试用期是 30 天。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。 
  
使用以下步骤将 Dynamics 365 许可证分配给全局管理员、用户 2 和用户 3 的帐户并使之成为系统管理员。
  
1. 在“**Microsoft 365 管理中心**”选项卡上，单击“**用户 > 活动用户**”。
    
2. 在活动用户列表中，单击全局管理员帐户，然后针对“产品许可证”**** 单击“编辑”****。
    
3. 在“产品许可证”窗格上，将“Dynamics 365 计划 1 企业版”的产品许可证设置为“打开”，单击“保存”，然后单击“关闭”两次********************。
    
4. 为用户 2 和用户 3 的帐户执行步骤 2 和步骤 3。
    
5. 关闭 **Microsoft 365 管理员中心**选项卡。
    
使用以下步骤将用户 2 和用户 3 的帐户配置为 Dynamics 365 系统管理员。
  
1. 在浏览器的“Office 管理中心”标签页的左侧导航中，单击“管理中心”****，然后单击“Dynamics 365”********。
    
    你可能需要等到 Dynamics 365 完成设置后，菜单中才会显示 Dynamics 365。
    
2. 在 Dynamics 365 选项卡上，单击“所有内容”，然后单击“完成设置”********。
    
    等待设置完成。
    
    设置完成后，它会基于试用订阅中的示例数据显示一个销售活动仪表板。请花点时间来观看“欢迎使用试用版”**** 视频。完成后关闭视频窗口。
    
3. 在顶部工具栏上，单击“销售”旁边的向下箭头，单击“设置”，然后单击“安全”************。
    
4. 在“安全”页上，单击“用户”********。
    
5. 在用户列表中，单击“用户 2”****。
    
6. 在工具栏中，单击“管理角色”****。
    
7. 在“管理角色”中，单击“系统管理员”，然后单击“确定”************。
    
8. 在顶部工具栏中单击“安全”****。
    
9. 为用户 3 帐户重复步骤 5 到 8。
    
10. 关闭“用户：User3”**** 选项卡。
    
> [!NOTE]
> 已为 Office 365 全局管理员帐户自动分配了 Dynamics 365 系统管理员角色。 
  
开发/测试环境目前包含：
  
- 在 Azure 基础结构服务中运行的模拟 Intranet。
    
- 与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版、EMS 和 Dynamics 365 试用订阅。
    
- 启用所有用户帐户以使用 Office 365 E5 企业版和 EMS。
    
- 全局企业管理员、用户 2 和用户 3 的帐户都可以使用 Dynamics 365，并且它们都是 Dynamics 365 系统管理员。
    
图 3 显示生成的配置。
  
**图 3：包含 Office 365、EMS 和 Dynamics 365 的 Azure 中的模拟 Intranet**

![包含 Azure、Office 365、EMS 和 Dynamics 365 的 One Microsoft 云开发/测试环境的第 3 阶段](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a>后续步骤

你现在可以试用 One Microsoft 云开发/测试环境。以下是有关指导体验的一些思路：
  
- [在 Office 365 应用程序的 EMS 中配置移动应用管理 (MAM) 策略](https://technet.microsoft.com/library/mt764059.aspx)
    
- [在与 Dynamics 365 联系人集成的 Office 365 中演示 Exchange Online](https://technet.microsoft.com/library/mt798313.aspx)
    
- [在 Azure 基础结构服务中创建用于托管基于服务器的工作负载的模拟跨界网络](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
  
[混合解决方案](hybrid-solutions.md)
  
[安全解决方案](security-solutions.md)





