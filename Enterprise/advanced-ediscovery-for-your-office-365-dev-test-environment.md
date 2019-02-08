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
description: 摘要：在 Office 365 开发/测试环境中使用示例数据配置并演示 Office 365 高级电子数据展示。
ms.openlocfilehash: c93900e07b8b9adbe0f1120eca77019b9dcc1eda
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897505"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>用于 Office 365 开发/测试环境的高级电子数据展示

 **摘要：** 在 Office 365 开发/测试环境中使用示例数据配置并演示 Office 365 高级电子数据展示。
  
Office 365 高级电子数据展示允许您快速查找和分析跨 Office 365，包括电子邮件和文档中存储的数据的相关信息。这样可以节省大量的时间和开支，特别是在诉讼情形。有关详细信息，请参阅[Office 365 高级电子数据展示](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)。
  
借助本文中的说明可以创建一个虚构的合同纠纷的一小组数据，并使用高级电子数据展示对数据进行分析。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>第 1 阶段：创建 Office 365 开发/测试环境

如果您只想要测试的最低硬件要求与轻型方式高级电子数据展示，按照在第 2 阶段和[Office 365 开发/测试环境中](office-365-dev-test-environment.md)的第 3 阶段的说明。
  
如果您想要测试高级电子数据展示模拟企业中，按照[目录同步的 Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明。
  
> [!NOTE]
> 测试高级电子数据展示不需要模拟的企业环境中，其中包括连接到 Internet 模拟的 intranet 和 Windows Server AD 林目录同步。它提供此处作为一个选项，以便您可以代表典型组织的环境中执行测试和试验。 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>第 2 阶段：创建高级电子数据展示的示例数据

在此过程中，创建电子邮件，稍后会在高级电子数据展示案例中对这些电子邮件进行分析。
  
1. 打开 Internet Explorer 并在登录[https://outlook.com](https://outlook.com)到您在第 2 阶段的[Office 365 开发/测试环境](office-365-dev-test-environment.md)中创建的 Outlook 帐户。
    
  - 如果使用的是轻型开发/测试环境，请打开 Internet Explorer 的专用会话并从本地计算机登录。
    
  - 如果您使用模拟的企业开发/测试环境，使用 Azure 门户 ([https://portal.azure.com](https://portal.azure.com)) 连接到 CLIENT1 虚拟机，并然后登录从 CLIENT1。
    
2. 在“**Outlook 邮件**”选项卡上，单击“**新建**”。
    
3. 中**到**，键入您的试用版订阅的 User6 帐户的电子邮件地址 ( **user6 @。**<organization name> **。 onmicrosoft.com**)。
    
4. 在主题中，键入“**测试电子邮件 1**”。
    
5. 在正文中，键入“**Tailspin 合同草案**”，然后单击“**发送**”。
    
6. 在“**Outlook 邮件**”选项卡上，单击“**新建**”。
    
7. 在“**收件人**”中，键入试用订阅的 User6 帐户的电子邮件地址。
    
8. 在主题中，键入“**测试电子邮件 2**”。
    
9. 在正文中，键入“**Tailspin 午餐会议**”，然后单击“**发送**”。
    
10. 在“**Outlook 邮件**”选项卡上，单击“**新建**”。
    
11. 在“**收件人**”中，键入试用订阅的 User6 帐户的电子邮件地址。
    
12. 在主题中，键入“**测试电子邮件 3**”。
    
13. 在正文中，键入“**Tailspin 合同争议**”，然后单击“**发送**”。
    
14. 单击右上角中的用户图标，然后单击**注销**。
    
15. 打开新选项卡并登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 的帐户名称和您的试用版订阅的 User6 帐户的密码。
    
16. 在“**Office 365 门户l**”选项卡上，单击“**邮件**”。
    
17. 在**邮件-User6-Outlook**选项卡中，选中 User6 从 Outlook 电子邮件帐户收到所有三个电子邮件。
    
18. 返回到 User6 的“**Office 365 门户**”选项卡。
    
19. 单击右上角的用户图标，然后单击“**注销**”。
    
在此过程中，创建两个 Word 文档，稍后会在高级电子数据展示案例中对这些文档进行分析。
  
1. 在“**Office**”页面上，单击“**登录**”，然后使用全局管理员帐户的凭据登录。
    
2. 在新建选项卡上，访问您的生产 SharePoint 网站的 URL: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. 在“**生产网站集**”选项卡的“**文档**”下，单击“**新建 > Word 文档**”。
    
4. 在“**Word Online**”页面，键入“**Tailspin 草案合同**”，等待标题中显示“**已保存**”，然后关闭“**Word Online**”页面选项卡。
    
5. 在“**生产网站集**”选项卡的“**文档**”下，单击“**新建 > Word 文档**”。
    
6. 	在“**Word Online**”选项卡上，键入“**Tailspin 合同争议说明**”，等待标题中显示“**已保存**”，然后关闭“**Word Online**”选项卡。
    
7. 在“**生产网站集**”选项卡上，你应该会在文档列表中看到“**文档**”和“**文档1**”。
    
8. 关闭“**生产网站集**”选项卡。
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>第 3 阶段： 使用高级电子数据展示的法律争议

遗憾的是，您的组织和 Tailspin Toys 之间合同争议已达到合法操作的时间点。在此过程中，您可以创建和配置搜索和分析电子邮件和文档包含文本"Tailspin 合同"高级电子数据展示案例。
  
使用高级电子数据展示的流程如下：
  
- 在安全中创建搜索&amp;合规中心分析其结果，然后准备高级电子数据展示的结果。
    
- 在高级电子数据展示中创建并配置案例，并分析相应的搜索结果。
    
在此过程中，您将创建安全中的搜索&amp;合规性中心对于"Tailspin 合同"，查看结果，在和高级电子数据展示准备结果。
  
1. 在“**Office 365 门户**”选项卡上，单击“**管理员**”。
    
2. 在“管理中心”选项卡的左侧导航中，单击“**管理中心>合规性**”。
    
3. 在**安全&amp;合规性**选项卡上，单击**权限**。
    
4. 在“**权限**”列表中，双击“**组织管理**”。
    
5. 在“**角色组**”窗口的“**成员**”下，单击加号。
    
6. 在“**选择成员**”窗口中，双击管理员帐户的名称，然后单击“**确定**”。
    
7. 在“**角色组**”窗口中，单击“**保存**”。
    
8. 在“**权限**”列表中，双击“**电子数据展示管理器**”。
    
9. 在“**角色组**”窗口的“**电子数据展示管理员**”下，单击加号。
    
10. 在“**选择成员**”窗口中，双击管理员帐户的名称，然后单击“**确定**”。
    
11. 在“**角色组**”窗口中，单击“**保存**”。
    
12. 在左侧导航窗格中，单击**搜索&amp;调查 > 内容搜索**。
    
13. 单击加号添加搜索。
    
14. 在“**新建搜索**”窗口中的“**名称**”中键入“**Tailspin 合同搜索**”。
    
15. 在“**您希望我们在哪里查找?**”中，单击“**搜索所有位置**”并选中“**Exchange**”、“**SharePoint**”和“**公用文件夹**”，然后单击“**下一步**”。
    
16. 在“**您希望我们查找哪些内容?**”中，键入“**Tailspin 合同**”，然后单击“**搜索**”。
    
17. 在搜索列表中，单击“**Tailspin 合同搜索**”名称。
    
18. 在**Tailspin 合同搜索**窗格中，单击在**结果**下的**预览搜索结果**。您应看到列出两个文档 （**文档**和**Document1**） 的生产 SharePoint 网站和**测试电子邮件 1**和**测试电子邮件 3**电子邮件发送给 User6 上一个窗口。关闭窗口。
    
19. 在“**内容搜索**”窗格的“**使用高级电子数据展示分析结果**”下，单击“**预览用于分析的结果**”。
    
20. 在“**准备用于 Tailspin 合同搜索的搜索结果**”窗口中，单击“**准备**”，然后等待此过程完成。
    
在此过程中，创建高级电子数据展示的新案例并对 Tailspin 合同搜索结果进行分析。
  
1. 在左窗格中，单击下的**电子数据展示****搜索&amp;调查**。
    
2. 在“**电子数据展示**”窗格中，单击“**进入高级电子数据展示**”。
    
3. 在“**高级电子数据展示**”选项卡，单击加号添加新案例。
    
4. 	在“**添加案例**”窗格中的“**名称**”中键入“**Tailspin 合同争议**”，然后单击“**确定**”。等待案例创建完成。
    
5. 双击列表中的“**Tailspin 合同争议**”。 
    
6. 在**容器**列表中，单击**Tailspin 合同搜索**容器，然后单击**过程**。等待处理以完成。
    
7. 当窗口底部显示“**处理: 完成**”时，单击左侧导航窗格中的“**处理摘要**”进行查看。
    
8. 在顶部导航中单击“**分析**”。
    
9. 在“**设置**”页面“**主题**”下的“**最大主题数**”中键入“**3**”。
    
10. 单击**分析**并等待完成分析。您应看到的目标总体、 文档、 电子邮件和附件的分析饼图一系列。有关详细信息，请参阅[查看分析结果](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)。
    
现在可以使用此环境创建新内容、新搜索和新案例，并在 Office 365 中进一步对高级电子数据展示进行试验。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的云应用安全](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 高级电子数据展示](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


