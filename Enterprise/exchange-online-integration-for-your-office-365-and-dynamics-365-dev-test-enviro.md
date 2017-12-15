---
title: "Office 365 和 Dynamics 365 开发/测试环境的 Exchange Online 集成"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- apr17entnews
- DecEntMigration
- mar17entnews
- Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "摘要：使用此测试实验室指南可以实现 Office 365 试用订阅中 Exchange Online 的 Dynamics 365 集成。"
ms.openlocfilehash: 9cecd13f0ffc3c2822ac6c66a3bde9c9e6a3c798
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a>Office 365 和 Dynamics 365 开发/测试环境的 Exchange Online 集成

 **摘要：**使用此测试实验室指南可以实现 Office 365 试用订阅中 Exchange Online 的 Dynamics 365 集成。
  
Microsoft Dynamics 365 的一个重要作用是将所有客户通信都存储在同一个位置，因此具有相应权限的任何人都可以查看所有相关的客户记录。例如，查看与特定联系人、帐户、 商机或案例关联的所有电子邮件。
  
若要将电子邮件和其他邮件记录存储在 Dynamics 365 中，需要与 Dynamics 365 同步你的电子邮件系统。服务器端同步是选择电子邮件同步的方法。
  
此测试实验室指南用于配置和演示 Exchange Online 和 Outlook Online 客户端如何利用 Dynamics 365 中存储的信息。 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a>第 1 阶段：扩展 Office 365 和 Dynamics 365 开发/测试环境

请按照 [Office 365 和 Dynamics 365 开发/测试环境](office-365-and-dynamics-365-dev-test-environment.md) 中的说明创建一个轻型或模拟的企业版 Office 365 和 Dynamics 365 开发/测试环境。
  
> [!NOTE]
> 本文中的配置不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server Active Directory (AD) 林的目录同步。它在此处作为一个选项提供，以便你可以测试 Office 365 和 Dynamics 365，并在代表典型组织的环境中对其进行试验 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a>第 2 阶段：配置和演示 Exchange Online 中的 Dynamics 365 集成

使用下列步骤配置 Dynamics 365 和 Exchange Online 集成的全局管理员邮箱：
  
1. 使用专用浏览器会话，转到[http://portal.office.com](http://portal.office.com) ，并使用您的 Office 365 提供全局管理员帐户进行登录。
    
2. 在"Microsoft Office 主页"页上，单击"邮件"磁贴。
    
3. 在浏览器中的新"邮件"选项卡上，单击"新建"并注意用于键入消息的框下方窗格的底角如何显示"我的模板"图标。
    
     ![空白的新电子邮件未与 Dynamics 365 集成。](images/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. 单击"放弃"，并使"邮件"选项卡保持打开状态。
    
5. 单击浏览器中的"Microsoft Office 主页"选项卡，然后单击"管理"磁贴。
    
6. 在"Office 管理中心"选项卡的左侧导航中，单击"管理中心">"Dynamics 365"。
    
7. 在浏览器中新的"Dynamics 365"选项卡上的 Dynamics 365 实例列表中，单击"打开"。
    
8. 在浏览器中新的"管理"选项卡中，在导航栏上单击"设置"旁边的下箭头，然后单击"系统"下方的"电子邮件配置"。
    
9.  在"电子邮件配置"页上，单击"电子邮件配置设置"。
    
10. 在"系统设置"对话框上的"电子邮件"选项卡中，将"约会、联系人和任务"更改为"服务器端同步"，然后单击"确定"。
    
11. 在"电子邮件配置"页上，单击"邮箱"。
    
12. 在左侧复选标记列中选择 Office 365 全局管理员名称，单击工具栏上的"应用默认电子邮件设置"，然后单击"确定"。
    
13. 单击工具栏上的"批准电子邮件"，然后单击"确定"。
    
14. 在左侧复选标记列中选择 Office 365 全局管理员名称，单击工具栏上的"测试和启用邮箱"，然后单击"确定"。
    
15. 单击打开"邮件"选项卡，并确认全局管理员收到一封测试邮件。
    
16. 返回到浏览器中的"邮箱">"我的可用邮箱"选项卡，然后刷新此页。"传入电子邮件状态"和"传出电子邮件状态"列应针对全局管理员帐户名称设置为"成功"。请注意，可能需要 15 分钟来完成这两个测试。
    
使用以下步骤安装适用于 Outlook 的 Dynamics 365 应用并在全局管理员邮箱内演示 Dynamics 365 功能：
  
1. 在浏览器中的"邮箱">"我的可用邮箱"选项卡上，单击"设置"旁边的下箭头，然后单击"系统"下的"适用于 Outlook 的 Dynamics 365 应用"。
    
2. 在"开始使用适用于 Outlook 的 Microsoft Dynamics 365 应用"页上，单击全局管理员名称，然后单击"将应用添加到 Outlook"。"状态"列将更改为"挂起"。
    
3. 刷新页面，直到状态更改为"添加到 Outlook"。请注意，可能需要 15 分钟来完成此配置。
    
4. 单击浏览器中的"邮件"选项卡，然后将其关闭。
    
5. 单击浏览器中的"Microsoft Office 主页"选项卡，然后单击"邮件"磁贴。
    
6. 在浏览器中新的"邮件"选项卡上，单击"新建"。请注意，用于键入消息的框下方窗格的底角现在显示 Dynamics 365 的图标。
    
     ![空白的新电子邮件与 Dynamics 365 集成，显示新图标。](images/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. 单击 Dynamics 365 图标。应该会看到"Dynamics 365" 窗格，你可以在其中跟踪此电子邮件或访问模板、销售宣传资料或文章。
    
8. 在电子邮件**给**字段中，键入**alex.y.wu@outlook.com**，然后**Dynamics 365**窗格中单击**重试**。在 Alex Wu，从销售应用程序示例数据提供有关您的订购试用期的联系人，您应该看到**Dynamics 365**窗格，其中显示的信息中的**收件人**节。
    
     ![存储在 Dynamics 365 中的销售联系人的 Dynamics 365 信息窗格。](images/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. 单击"放弃"。

> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的项目的所有。
    
## <a name="see-also"></a>See Also

[Office 365 和 Dynamics 365 开发/测试环境](office-365-and-dynamics-365-dev-test-environment.md)
  
[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[Dynamics 365（联机）的订阅管理](https://technet.microsoft.com/library/jj679903.aspx)
  
[管理 Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


