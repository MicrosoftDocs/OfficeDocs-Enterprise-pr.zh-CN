---
title: "Office 365 标签和 DLP 与 SharePoint Online 文件保护"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: "摘要： Office 365 标签和数据丢失防护 (DLP) 将策略应用各种级别的信息保护的 SharePoint Online 团队站点的。"
ms.openlocfilehash: dd4f71d8fae458d6d20f7a5b35b46e14a72853f1
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a>Office 365 标签和 DLP 与 SharePoint Online 文件保护

 **摘要：**Office 365 标签和数据丢失防护 (DLP) 将策略应用各种级别的信息保护的 SharePoint Online 团队站点的。
  
使用本文中的步骤来设计和部署 Office 365 标签和基线，敏感和高度机密 SharePoint Online 团队站点的 DLP 策略。这些三个层次的保护有关的详细信息，请参阅[安全 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)。
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a>SharePoint Online 网站的 office 365 标签

有三个阶段创建，然后将 Office 365 到 SharePoint Online 团队站点标签。
  
### <a name="phase-1-determine-the-office-365-label-names"></a>第 1 阶段： 确定 Office 365 标签名称

在此阶段中，您将确定四个级别的信息保护应用于在线 SharePoint 工作组网站的 Office 365 标签的名称。下表列出了每个级别的建议的名称。
  
|**SharePoint Online 团队站点保护级别**|**标签名称**|
|:-----|:-----|
|比较基准公共  <br/> |内部公众  <br/> |
|比较基准专用  <br/> |专用  <br/> |
|敏感  <br/> |敏感  <br/> |
|高度机密  <br/> |高度机密  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a>第 2 阶段： 创建 Office 365 的标签

在此阶段中，创建，然后再发布确定的标签为不同级别的信息保护。
  
若要创建标签，可以使用 Office 365 管理中心或 Microsoft PowerShell。
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a>使用 Office 365 管理中心创建 Office 365 标签

1. Office 365 门户拥有安全管理员或公司管理员角色的帐户登录。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. **Microsoft Office 主页**选项卡中，单击**管理**拼贴。
    
3. 您的浏览器的新**办公室管理中心**标签，请单击**中心管理 > 安全&amp;法规遵从性**。
    
4. 从新**家庭-安全&amp;法规遵从性**选项卡上的浏览器中，单击**分类 > 标签**。
    
5. 从**主页 > 标签**窗格中，单击**创建一个标签**。
    
6. 在**标签名称**窗格中，键入标签的名称，然后单击**下一步**。
    
7. 在**标签设置**窗格中，单击**下一步**。
    
8. 上的**查看设置**窗格中，单击**创建此标签**，然后单击**关闭**。
    
9. 其他标签，请重复步骤 5 到 8。
    
### <a name="create-office-365-labels-with-powershell"></a>使用 PowerShell 创建 Office 365 标签

1. [连接到 Office 365 安全&amp;使用远程 PowerShell 的法规遵从性中心](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409)，并指定具有安全管理员或公司管理员角色的帐户的凭据。
    
2. 填写标签名称的列表，然后在 PowerShell 命令提示符下运行以下命令：
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

接下来，使用以下步骤来发布新的 Office 365 提供标签。
  
1. 从**主页 > 标签**窗格中安全&amp;法规遵从性中心，单击**发布标签**。
    
2. 在**选择要发布的标签**窗格上，单击**发布选择标志**。
    
3. 在**选择标签**窗格中，单击**添加**，选择所有四个标签。
    
4. 单击**完成**。
    
5. 在**选择要发布的标签**窗格上，单击**下一步**。
    
6. 在**选择位置**窗格中，单击**下一步**。
    
7. 在**您的策略名称**窗格中，在**名称**中键入您的标签集的名称，然后单击**下一步**。
    
8. 上的**查看设置**窗格中，单击**发布标签**，然后单击**关闭**。
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a>阶段 3： 将 Office 365 标签应用于您的 SharePoint Online 网站

使用下列步骤将 Office 365 标签应用于您在线 SharePoint 工作组网站的文档文件夹。
  
1. 从浏览器的**Microsoft Office 主页**选项卡上，单击**SharePoint**拼贴。
    
2. 在浏览器中新**SharePoint**选项卡，单击需要分配一个 Office 365 提供标签的站点。
    
3. 在新建 SharePoint 网站选项卡浏览器，单击**文档**。
    
4. 单击设置图标，然后单击**库设置**。
    
5. 在**权限和管理**，请单击**应用于此库中的项目的标签**。
    
6. 在**设置应用标签**，选择适当的标签，，然后单击**保存**。
    
7. 关闭 SharePoint Online 网站选项卡。
    
8. 重复步骤 3 至 8 将 Office 365 标签分配给其他 SharePoint Online 网站。
    
下面是生成的配置。
  
![四种类型的 SharePoint Online 团队网站的 Office 365 标签。](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a>SharePoint Online 网站的 DLP 策略

使用下列步骤来配置它们共享组织外的 SharePoint Online 敏感工作组网站上的文档时通知用户的 DLP 策略。
  
1. 从**Microsoft Office 主页**选项卡上的在浏览器中，单击**安全&amp;法规遵从性**平铺。
    
2. 对新**安全&amp;法规遵从性**在您的浏览器选项卡上，单击**数据丢失防范 > 策略**。
    
3. 在**数据丢失防范**窗格中，单击**+ 创建策略**。
    
4. 在**从模板开始创建自定义策略或**窗格中，单击**自定义**，然后单击**下一步**。
    
5. **名称您的策略**中，在**名称**中键入的敏感级 DLP 策略的名称，然后单击**下一步**。
    
6. 在**选择位置**窗格中，**让我来选择特定的位置**，请单击，然后单击**下一步**。
    
7. 在位置列表中，禁用**Exchange 电子邮件**帐户和**OneDrive 帐户**位置，然后单击**下一步**。
    
8. 在**自定义类型您想要保护的敏感信息**窗格中，单击**编辑**。
    
9. 在**选择要保护的内容的类型**窗格中，单击下拉列表框中，**添加**，然后单击**标签**。
    
10. 在**标签**窗格中，单击**+ 添加**，选择**敏感**标签，单击**添加**，然后单击**完成**。
    
11. 在**选择要保护的内容的类型**窗格中，单击**保存**。
    
12. 在**自定义类型您想要保护的敏感信息**窗格中，单击**下一步**。
    
13. 在**您想要我们检测敏感信息办？**窗格中，单击**自定义提示和电子邮件**。
    
14. 在**自定义策略的提示和电子邮件通知**窗格中，单击**自定义策略提示文本**。
    
15. 在文本框中，键入或粘贴以下：
    
  - 若要与组织外部的用户共享，下载该文件，然后将其打开。单击文件然后保护文档，然后使用密码加密和再指定一个强密码。在另一个电子邮件或其他通讯手段发送密码。
    
    或者，键入或粘贴您的策略提示，指导用户如何共享您的组织之外的文件中。
    
16. 单击“**确定**”。
    
17. 在**您想要我们检测敏感信息办？**窗格中，清除**阻止某些人共享，并限制对内容的访问**复选框，然后单击**下一步**。
    
18. 在**所需的策略或测试的事情，首先打开？**窗格中，单击**是，立即启用**，然后单击**下一步**。
    
19. 在**查看设置**窗格上，单击**创建**，然后单击**关闭**。
    
这里是结果敏感 SharePoint Online 的团队站点的配置。
  
![使用敏感 Office 365 标签的独立 SharePoint Online 团队网站的 DLP 策略。](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
接下来，使用下列步骤配置 DLP 策略阻止用户时它们共享组织外的 SharePoint Online 高度机密的工作组网站上的文档。
  
1. 从**Microsoft Office 主页**选项卡上的在浏览器中，单击**安全&amp;法规遵从性**平铺。
    
2. 对新**安全&amp;法规遵从性**在您的浏览器选项卡上，单击**数据丢失防范 > 策略**。
    
3. 在**数据丢失防范**窗格中，单击**+ 创建策略**。
    
4. 在**从模板开始创建自定义策略或**窗格中，单击**自定义**，然后单击**下一步**。
    
5. 在**您的策略名称**窗格中，在**名称**中键入高度敏感级别 DLP 策略的名称，然后单击**下一步**。
    
6. 在**选择位置**窗格中，**让我来选择特定的位置**，请单击，然后单击**下一步**。
    
7. 在位置列表中，禁用**Exchange 电子邮件**帐户和**OneDrive 帐户**位置，然后单击**下一步**。
    
8. 在**自定义类型您想要保护的敏感信息**窗格中，单击**编辑**。
    
9. 在**选择要保护的内容的类型**窗格中，单击下拉列表框中，**添加**，然后单击**标签**。
    
10. **标签**的窗格中，单击**+ 添加**，选择**高度机密**标签，单击**添加**，然后单击**完成**。
    
11. 在**选择要保护的内容的类型**窗格中，单击**保存**。
    
12. 在**自定义类型您想要保护的敏感信息**窗格中，单击**下一步**。
    
13. 在**您想要我们检测敏感信息办？**窗格中，单击**自定义提示和电子邮件**。
    
14. 在**自定义策略的提示和电子邮件通知**窗格中，单击**自定义策略提示文本**。
    
15. 在文本框中，键入或粘贴以下：
    
  - 若要与组织外部的用户共享，下载该文件，然后将其打开。单击文件然后保护文档，然后使用密码加密和再指定一个强密码。在另一个电子邮件或其他通讯手段发送密码。
    
    或者，键入或粘贴您的策略提示，指导用户如何共享您的组织之外的文件中。
    
16. 单击“**确定**”。
    
17. 在**您想要我们检测敏感信息办？**窗格中，选择**需要重写的理由**，然后再单击**下一步**。
    
18. 在**所需的策略或测试的事情，首先打开？**窗格中，单击**是，立即启用**，然后单击**下一步**。
    
19. 在**查看设置**窗格上，单击**创建**，然后单击**关闭**。
    
这里是您得到高保密性 SharePoint Online 团队站点的配置。
  
![使用高度机密 Office 365 标签的独立 SharePoint Online 团队网站的 DLP 策略。](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a>后续步骤

[SharePoint Online Azure 的信息保护文件保护](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a>另请参阅

[SharePoint Online 网站和文件保护](secure-sharepoint-online-sites-and-files.md)
  
[开发/测试环境中的安全 SharePoint Online 网站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)


