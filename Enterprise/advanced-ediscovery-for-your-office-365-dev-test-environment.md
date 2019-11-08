---
title: 用于 Office 365 开发/测试环境的高级电子数据展示
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 摘要：在 Office 365 开发/测试环境中使用示例数据配置并演示 Office 365 高级电子数据展示。
ms.openlocfilehash: dbd03c1a75b63f4fdaff49db47c8d415f267aaf3
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030666"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>用于 Office 365 开发/测试环境的高级电子数据展示

 **摘要：** 在 Office 365 开发/测试环境中使用示例数据配置并演示 Office 365 高级电子数据展示。
  
Office 365 高级电子数据展示使您能够快速查找和分析存储在 Office 365 中的数据（包括电子邮件和文档）中的相关信息。 这样则可以节省大量时间和费用，尤其是在诉讼情景中。 有关详细信息，请参阅 [Office 365 高级电子数据展示](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)。
  
借助本文中的说明可以创建一个虚构的合同纠纷的一小组数据，并使用高级电子数据展示对数据进行分析。
  
> [!TIP]
> 单击[此处](https://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>第 1 阶段：创建 Office 365 开发/测试环境

如果只想使用最低要求以轻型方式测试高级电子数据展示，请按照第2阶段和第3阶段的[Office 365 开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。
  
如果要在模拟企业版中测试高级电子数据展示，请按照[Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。
  
> [!NOTE]
> 测试高级电子数据展示不需要模拟的企业环境，其中包括连接到 Internet 的模拟 intranet 和 Active Directory 域服务（AD DS）林的目录同步。 此处提供了此选项，以便您可以在代表典型组织的环境中执行测试和实验。 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>第 2 阶段：创建高级电子数据展示的示例数据

在此过程中，创建电子邮件，稍后会在高级电子数据展示案例中对这些电子邮件进行分析。
  
1. 打开 Internet Explorer，并登录[https://outlook.com](https://outlook.com)到在[Office 365 开发/测试环境](office-365-dev-test-environment.md)的第2阶段中创建的 Outlook 帐户。
    
  - 如果使用的是轻型开发/测试环境，请打开 Internet Explorer 的专用会话并从本地计算机登录。
    
  - 如果使用的是模拟企业开发/测试环境，请使用 Azure 门户（[https://portal.azure.com](https://portal.azure.com)）连接到 CLIENT1 虚拟机，然后从 CLIENT1 登录。
    
2. 在“**Outlook 邮件**”选项卡上，单击“**新建**”。
    
3. 在 " **To**" 中，键入试用订阅的 User6 帐户的电子邮件地址（ **user6@。**<organization name> **. onmicrosoft.com**）。
    
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
    
14. 单击右上角的用户图标，然后单击“**注销**”。
    
15. 打开一个新的选项卡，并使用试用订阅的 User6[https://www.office.com](https://www.office.com)帐户的帐户名称和密码登录 Office 365 门户（）。
    
16. 在“**Office 365 门户l**”选项卡上，单击“**邮件**”。
    
17. 在 " **User6-outlook** " 选项卡上，检查 User6 收到的所有三封电子邮件是否来自 Outlook 电子邮件帐户。
    
18. 返回到 User6 的“**Office 365 门户**”选项卡。
    
19. 单击右上角的用户图标，然后单击“**注销**”。
    
在此过程中，创建两个 Word 文档，稍后会在高级电子数据展示案例中对这些文档进行分析。
  
1. 在“**Office**”页面上，单击“**登录**”，然后使用全局管理员帐户的凭据登录。
    
2. 在新选项卡上，访问您的生产 SharePoint 网站的 URL： **https://** <fictional organization name> **。 sharepoint.com/sites/production**
    
3. 在“**生产网站集**”选项卡的“**文档**”下，单击“**新建 > Word 文档**”。
    
4. 在**Word**页面上，键入**Tailspin 草稿合同**，等待它在标题中显示 "**已保存**"，然后关闭 " **Word**页面" 选项卡。
    
5. 在“**生产网站集**”选项卡的“**文档**”下，单击“**新建 > Word 文档**”。
    
6. 在 " **Word** " 选项卡上，键入 " **Tailspin 合同争议说明**"，等待它在标题中显示 "**已保存**"，然后关闭 " **Word** " 选项卡。
    
7. 在“**生产网站集**”选项卡上，你应该会在文档列表中看到“**文档**”和“**文档1**”。
    
8. 关闭“**生产网站集**”选项卡。
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>第3阶段：将高级电子数据展示用于法律纠纷

很遗憾，贵组织与 Tailspin Toys 间的合同争议已到达法律诉讼的阶段。 在此过程中，您将创建并配置高级电子数据展示事例，以搜索和分析包含文本 "Tailspin 合同" 的电子邮件和文档。
  
使用高级电子数据展示的流程如下：
  
- 在安全&amp;合规中心中创建搜索，分析其结果，然后准备高级电子数据展示的结果。
    
- 在高级电子数据展示中创建并配置案例，并分析相应的搜索结果。
    
在此过程中，您将在 "Tailspin 合同&amp; " 的安全合规性中心中创建搜索，查看结果，然后准备高级电子数据展示的结果。
  
1. 在“**Office 365 门户**”选项卡上，单击“**管理员**”。
    
2. 在“管理中心”选项卡的左侧导航中，单击“**管理中心>合规性**”。
    
3. 在 "**安全&amp;合规性**" 选项卡上，单击 "**权限**"。
    
4. 在“**权限**”列表中，双击“**组织管理**”。
    
5. 在“**角色组**”窗口的“**成员**”下，单击加号。
    
6. 在“**选择成员**”窗口中，双击管理员帐户的名称，然后单击“**确定**”。
    
7. 在“**角色组**”窗口中，单击“**保存**”。
    
8. 在“**权限**”列表中，双击“**电子数据展示管理器**”。
    
9. 在“**角色组**”窗口的“**电子数据展示管理员**”下，单击加号。
    
10. 在“**选择成员**”窗口中，双击管理员帐户的名称，然后单击“**确定**”。
    
11. 在“**角色组**”窗口中，单击“**保存**”。
    
12. 在左侧导航中，单击 **" &amp;搜索调查 > 内容搜索**"。
    
13. 单击加号添加搜索。
    
14. 在“**新建搜索**”窗口中的“**名称**”中键入“**Tailspin 合同搜索**”。
    
15. 在“**您希望我们在哪里查找?**”中，单击“**搜索所有位置**”并选中“**Exchange**”、“**SharePoint**”和“**公用文件夹**”，然后单击“**下一步**”。
    
16. 在“**您希望我们查找哪些内容?**”中，键入“**Tailspin 合同**”，然后单击“**搜索**”。
    
17. 在搜索列表中，单击“**Tailspin 合同搜索**”名称。
    
18. 在“**Tailspin 合同搜索**”窗格中，单击“**结果**”下的“**预览搜索结果**”。 您应该会看到一个窗口，其中列出了生产 SharePoint 网站（ **Document**和**Document1**）上的两个文档和**测试电子邮件 1** ，并将**电子邮件 3**电子邮件测试到 User6。 关闭该窗口。
    
19. 在“**内容搜索**”窗格的“**使用高级电子数据展示分析结果**”下，单击“**预览用于分析的结果**”。
    
20. 在“**准备用于 Tailspin 合同搜索的搜索结果**”窗口中，单击“**准备**”，然后等待此过程完成。
    
在此过程中，创建高级电子数据展示的新案例并对 Tailspin 合同搜索结果进行分析。
  
1. 在左侧导航中，单击 "**搜索&amp;调查**" 下的 "**电子数据展示**"。
    
2. 在“**电子数据展示**”窗格中，单击“**进入高级电子数据展示**”。
    
3. 在“**高级电子数据展示**”选项卡，单击加号添加新案例。
    
4. 	在“**添加案例**”窗格中的“**名称**”中键入“**Tailspin 合同争议**”，然后单击“**确定**”。等待案例创建完成。
    
5. 双击列表中的“**Tailspin 合同争议**”。 
    
6. 在 "**容器**" 列表中，单击 " **Tailspin 合同搜索**" 容器，然后单击 "**处理**"。 等待完成处理。
    
7. 当窗口底部显示“**处理: 完成**”时，单击左侧导航窗格中的“**处理摘要**”进行查看。
    
8. 在顶部导航中单击“**分析**”。
    
9. 在“**设置**”页面“**主题**”下的“**最大主题数**”中键入“**3**”。
    
10. 单击“**分析**”，然后等待分析完成。 应该会看到一系列包含目标总体、文档、电子邮件和附件的饼图。 有关详细信息，请参阅[查看分析结果](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)。
    
现在可以使用此环境创建新内容、新搜索和新案例，并在 Office 365 中进一步对高级电子数据展示进行试验。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 高级电子数据展示](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


