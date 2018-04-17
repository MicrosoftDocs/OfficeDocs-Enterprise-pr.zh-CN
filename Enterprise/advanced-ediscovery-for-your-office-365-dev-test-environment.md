---
title: 用于 Office 365 开发/测试环境的高级电子数据展示
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
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 摘要： 配置和演示 Office 365 高级的 eDiscovery Office 365 开发/测试环境中的示例数据。
ms.openlocfilehash: e850cf7ebab806d8ff51176a3e88077a692c41ef
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>用于 Office 365 开发/测试环境的高级电子数据展示

 **摘要：**演示 Office 365 高级的 eDiscovery Office 365 开发/测试环境中的示例数据和配置。
  
Office 365 高级的 eDiscovery 可以快速找到并分析整个 Office 365，包括电子邮件和文档中存储的数据的相关信息。这样可以节省大量的时间和费用，特别是在诉讼情形。有关详细信息，请参阅[Office 365 高级 eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)。
  
借助本文中的说明可以创建一个虚构的合同纠纷的一小组数据，并使用高级电子数据展示对数据进行分析。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>第 1 阶段：创建 Office 365 开发/测试环境

如果您只需要达到最低要求的轻量方式测试高级的 eDiscovery，按照第二阶段和第 3 阶段的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。
  
如果您想要测试模拟企业中的高级的 eDiscovery，按照[目录同步为您 Office 365 的开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。
  
> [!NOTE]
> 测试高级的 eDiscovery 不需要模拟的企业环境中，其中包括连接到 Internet 的模拟内部网和 Windows 服务器 AD 林中的目录同步。它提供此处作为一个选项，以便您可以代表典型的组织的环境中执行测试和试验。 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>第 2 阶段：创建高级电子数据展示的示例数据

在此过程中，创建电子邮件，稍后会在高级电子数据展示案例中对这些电子邮件进行分析。
  
1. 打开 Internet Explorer，在登录[https://outlook.com](https://outlook.com)到您在第 2 阶段的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中创建 Outlook 帐户。
    
  - 如果使用的是轻型开发/测试环境，请打开 Internet Explorer 的专用会话并从本地计算机登录。
    
  - 如果您使用的模拟的企业开发/测试环境，则使用 Azure 门户网站 ([https://portal.azure.com](https://portal.azure.com)) 以连接到客户端 1 虚拟机，然后从客户端 1 登录。
    
2. 在**Outlook 邮件**选项卡上，单击**新建**。
    
3. **对**，键入您的订购试用期的 User6 帐户的电子邮件地址 ( **user6 @。**<organization name> **。 onmicrosoft.com**)。
    
4. 该主题中，键入**测试电子邮件 1**。
    
5. 在正文中，键入**Tailspin 合同草稿**，然后单击**发送**。
    
6. 在**Outlook 邮件**选项卡上，单击**新建**。
    
7. **对**，键入您的订购试用期的 User6 帐户的电子邮件地址。
    
8. 该主题中，键入**测试电子邮件 2**。
    
9. 在正文中，键入**Tailspin 午宴**，然后单击**发送**。
    
10. 在**Outlook 邮件**选项卡上，单击**新建**。
    
11. **对**，键入您的订购试用期的 User6 帐户的电子邮件地址。
    
12. 该主题中，键入**测试电子邮件 3**。
    
13. 在正文中，键入**Tailspin 合同不一致**，，然后单击**发送**。
    
14. 单击右上角的用户图标，然后单击**注销**。
    
15. 打开新选项卡，然后登录到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com)) 与帐户名和密码您的订购试用期的 User6 帐户。
    
16. **Office 365 门户**选项卡上，单击**邮件**。
    
17. **邮件-User6-Outlook**选项卡上，验证 User6 收到所有三封电子邮件从 Outlook 电子邮件帐户。
    
18. 切换回至**Office 365 门户选项卡**为 User6。
    
19. 单击右上角的用户图标，然后单击**注销。**
    
在此过程中，创建两个 Word 文档，稍后会在高级电子数据展示案例中对这些文档进行分析。
  
1. 在**Office**页中，单击**登录，**登录您的全局管理员帐户的凭据。
    
2. 在新的选项卡，访问生产 SharePoint 站点的 URL: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. 在**生产站点集合**选项卡上的**文档**，请单击**新建 > Word 文档**。
    
4. 在**单词在线**页面上，键入**Tailspin 草稿合同**，等待，直到它在标题将显示**已保存**，然后关闭**单词在线**页面选项卡。
    
5. 在**生产站点集合**选项卡上的**文档**，请单击**新建 > Word 文档**。
    
6. 在**单词在线**选项卡上，键入**Tailspin 合同争议备注**、 等待，直到它在标题将显示**已保存**，然后关闭**单词在线**选项卡。
    
7. **生产站点集合**选项卡上，您应该看到**文档**和**文档 1**中的文档的列表。
    
8. 关闭**生产站点集合**选项卡。
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>阶段 3： 使用高级的 eDiscovery 的法律争议

遗憾的是，您的组织和乖宝贝玩具公司之间的合同争端已达到的点的法律诉讼。在此过程中，您可以创建和配置高级的 eDiscovery 案例来搜索和分析电子邮件和文档包含文本"Tailspin 协定"。
  
使用高级电子数据展示的流程如下：
  
- 在安全创建搜索&amp;法规遵从性中心，分析其结果，和高级 eDiscovery 准备的结果。
    
- 在高级电子数据展示中创建并配置案例，并分析相应的搜索结果。
    
在此过程中，您创建的搜索结果中安全&amp;法规遵从性中心对于"Tailspin 合同"，查看结果，和高级 eDiscovery 准备的结果。
  
1. **Office 365 门户**选项卡中，单击**管理**。
    
2. 在 Admin 中心选项卡左侧导航，请单击**中心管理 > 法规遵从性**。
    
3. 在**安全&amp;法规遵从性**选项卡上，单击**权限**。
    
4. 在**权限**列表中，双击**组织管理**。
    
5. 在**角色组**窗口中，在**成员**下单击加号。
    
6. 在**选择成员**窗口中，双击您的管理员帐户的名称，然后单击**确定**。
    
7. 在**角色组**窗口中，单击**保存**。
    
8. 在**权限**列表中，双击**数据展示管理器**。
    
9. 在**角色组**窗口下**eDiscovery 管理员**，单击加号图标。
    
10. 在**选择成员**窗口中，双击您的管理员帐户的名称，然后单击**确定**。
    
11. 在**角色组**窗口中，单击**保存**。
    
12. 在左边的导航，请单击**搜索&amp;调查 > 内容搜索**。
    
13. 单击加号添加搜索。
    
14. 在**新的搜索**窗口中，键入**Tailspin 合同搜索**范围**名称**。
    
15. 在**您，希望我们看？**，**无处不在搜索**选择**交换**、 **SharePoint**以及**公用文件夹**，请单击，然后单击**下一步。**
    
16. 在**要我们寻找？**， **Tailspin 合同**，键入，然后单击**搜索**。
    
17. 在搜索列表中，单击**Tailspin 合同搜索**名称。
    
18. 在**Tailspin 合同搜索**窗格中，单击**预览搜索结果**下**的结果**。您应该看到一个窗口，列出在生产 SharePoint 网站 （**文档**和**文档 1**） 和**测试电子邮件 1**和**3 的测试电子邮件**电子邮件发送给 User6 的两个文档。关闭该窗口。
    
19. 在**内容搜索**窗格中，**用高级的 eDiscovery 的分析结果**下**预览结果进行分析**。
    
20. 在**准备搜索 Tailspin 合同搜索结果**窗口中，单击**准备**并等待其完成。
    
在此过程中，创建高级电子数据展示的新案例并对 Tailspin 合同搜索结果进行分析。
  
1. 在左边的导航，请单击下的**eDiscovery** **搜索&amp;调查**。
    
2. **EDiscovery**的窗格中，单击**转到高级 eDiscovery**。
    
3. **EDiscovery 高级**选项卡中，单击加号图标，添加新的用例。
    
4. **加载情况下**的窗格中，在**名称**中键入**Tailspin 合同纠纷**，然后单击**确定**。要创建用例等。
    
5. 双击**Tailspin 合同纠纷**案例的列表中。
    
6. 在**容器**列表中，单击**Tailspin 合同搜索**容器，然后单击**过程**。等待此处理完成。
    
7. 当**进程： 完成**出现在窗口的底部，单击**进程摘要**查看摘要左侧导航中。
    
8. 在顶部的导航中，单击**分析**。
    
9. 在**安装程序**页中的**主题**下，键入**3**中**主题的最大数目**。
    
10. 单击**分析**，并等待要完成的分析。您应该看到一连串饼形图与分析的目标人口、 文档、 电子邮件和附件。有关详细信息，请参阅[查看分析结果](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)。
    
现在可以使用此环境创建新内容、新搜索和新案例，并在 Office 365 中进一步对高级电子数据展示进行试验。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 开发/测试环境的云应用程序安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 高级的 eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


