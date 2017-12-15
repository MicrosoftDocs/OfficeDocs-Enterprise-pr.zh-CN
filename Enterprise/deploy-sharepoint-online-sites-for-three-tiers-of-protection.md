---
title: "部署 SharePoint Online 网站的三个层次的保护"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "摘要： 创建和配置 SharePoint Online 的团队站点的各种级别的信息保护。"
ms.openlocfilehash: 1023eff2542ab1bf41a8261d85d70c06718497cf
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a>部署 SharePoint Online 网站的三个层次的保护

 **摘要：**创建和配置 SharePoint Online 的团队站点的各种级别的信息保护。
  
使用本文中的步骤来设计和部署基准，敏感和高度机密 SharePoint Online 团队站点。这些三个层次的保护有关的详细信息，请参阅[安全 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)。
  
## <a name="baseline-sharepoint-online-team-sites"></a>比较基准在线 SharePoint 工作组网站

基线保护包括两个公共和私人团队站点。公用的工作组网站可以发现，并由组织中的任何人访问。只能发现和访问 Office 365 组与工作组网站的成员的专用网站。这两种类型的工作组站点允许成员与他人共享网站。
  
### <a name="public"></a>公用的

具有公共访问权限和权限创建基线在线 SharePoint 工作组网站，请执行以下操作：
  
1. 登录到 Office 365 门户网站也将用来管理 SharePoint Online 工作组网站 （SharePoint Online 管理员） 的帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在图块的列表中，单击**SharePoint**。
    
3. 在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。
    
4. 在**创建网站**页上，单击**工作组网站**。
    
5. 在**站点名称**中，键入公用团队站点的名称。 
    
6. 在**团队站点的说明**中，键入站点的用途的说明。
    
7. 在**隐私设置**选择**公用-组织中的任何人都可以访问该网站**，，然后单击**下一步**。
    
8. 在**谁您想要添加？**窗格中，单击**完成**。
    
下面是生成的配置。
  
![适用于公共 SharePoint Online 团队网站的基线级保护。](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a>专用

若要具有私有访问权限和权限创建基线在线 SharePoint 工作组网站，请执行以下操作：
  
1. 登录到 Office 365 门户网站也将用来管理 SharePoint Online 工作组网站 （SharePoint Online 管理员） 的帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在图块的列表中，单击**SharePoint**。
    
3. 在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。
    
4. 在**创建网站**页上，单击**工作组网站**。
    
5. 在**站点名称**中，键入专用工作组站点的名称。 
    
6. 在**团队站点的说明**中，键入网站的用途的说明。
    
7. 在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。
    
8. 在**谁您想要添加？**窗格中，**添加成员**中, 键入有权访问此专用工作组站点的用户帐户的名称。
    
9. 当您完成将最初的成员集添加到该网站，单击**完成**
    
下面是生成的配置。
  
![适用于专用 SharePoint Online 团队网站的基线级保护。](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a>敏感的在线 SharePoint 工作组网站

敏感的在线 SharePoint 工作组网站是独立的工作组站点，这意味着，通过而不是与工作组网站的 Office 365 组成员身份的 SharePoint 组中的成员身份控制权限。
  
若要创建独立的工作组网站，有两个主要步骤。
  
### <a name="step-1-design-your-isolated-site"></a>第 1 步： 设计独立的站点

若要设计独立的工作组站点，您需要确定：
  
- 您的 SharePoint 组和权限级别。
    
- 将中的 SharePoint 组成员的访问组的组。
    
     访问组的推荐的设置是站点成员之一、 网站浏览者和站点管理员。
    
- 您是否使用嵌套组内访问组。
    
例如，组建议的结构和权限级别，如下所示：
  
|**SharePoint 组**|**权限级别**|**访问组 （示例）**|
|:-----|:-----|:-----|
|[站点名称]成员  <br/> |编辑  <br/> |[站点名称]成员  <br/> |
|[站点名称]访问者  <br/> |读取  <br/> |[站点名称]查看器  <br/> |
|[站点名称]所有者  <br/> |完全控制  <br/> |[站点名称]管理员  <br/> |
   
默认情况下，工作组站点创建 SharePoint 组和权限级别。您需要确定您访问权限的组的名称。
  
设计过程的详细信息，请参阅[设计独立的在线 SharePoint 工作组网站](design-an-isolated-sharepoint-online-team-site.md)。
  
### <a name="step-2-deploy-your-isolated-site"></a>步骤 2： 部署独立的站点

若要部署独立的网站，您首先需要：
  
- 确定用户帐户和组添加到每个访问组。
    
- 创建访问组并添加用户和组成员。
    
有关详细步骤，请参阅[部署独立的在线 SharePoint 工作组网站](deploy-an-isolated-sharepoint-online-team-site.md)的**第一阶段**。
  
接下来，使用以下步骤创建 SharePoint Online 的工作组网站。
  
1. 登录到 Office 365 门户网站也将用来管理 SharePoint Online 工作组网站 （SharePoint Online 管理员） 的帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在图块的列表中，单击**SharePoint**。
    
3. 在您的浏览器的新**SharePoint**选项卡，单击**+ 创建网站**。
    
4. 在**创建网站**页上，单击**工作组网站**。
    
5. 在**站点名称**中，键入专用工作组站点的名称。
    
6. 在**团队站点的说明**中，键入可选的说明。
    
7. 在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。
    
8. 在**谁您想要添加？**窗格中，单击**完成**。
    
接下来，从新的 SharePoint Online 工作组站点，使用下列步骤配置权限。
  
1. 确定用户的 IT 管理员或其他人员将负责响应和解决对网站的访问请求主体名称 (UPN) （belindan@contoso.com 是 UPN 的示例）。编写该 UPN 此处: ___。
    
2. 在工具栏上，单击设置图标，然后单击**网站权限**。
    
3. 在**网站权限**窗格中，单击**高级的权限设置**。
    
4. 您的浏览器新**权限**选项卡上，单击**访问请求设置**。
    
5. 在**访问请求设置**对话框中：
    
  - 清除**允许成员共享的网站和个别文件和文件夹**，并**允许成员要邀请到网站的成员组的其他人**复选框。
    
  - **将所有访问请求都发送**键入您的 IT 管理员，从步骤 1 的 UPN。
    
  - 单击"确定"。
    
6. 您的浏览器**权限**选项卡上，单击列表中的**[站点名称] 成员**。
    
7. 在**用户和用户组**中，单击**新建**。
    
8. 在**共享**对话框中，键入此站点的站点成员访问组的名称，选择它，然后单击**共享**。
    
9. 单击浏览器上的后退按钮。
    
10. 在列表中单击**[网站名称] 所有者**。
    
11. 在**用户和用户组**中，单击**新建**。
    
12. 在**共享**对话框中，键入此站点的管理员访问权限的网站用户组的名称，选择它，然后单击**共享**。
    
13. 单击浏览器上的后退按钮。
    
14. 单击**[网站名称] 的访问者**列表中。
    
15. 在**用户和用户组**中，单击**新建**。
    
16. 在**共享**对话框中，键入此站点的站点浏览者访问组的名称，选择它，然后单击**共享**。
    
17. 关闭您的浏览器**权限**选项卡。
    
这些权限设置的结果是：
  
- **[网站名称] 所有者**SharePoint 组包含所有成员中具有**完全控制**权限级别的网站管理员访问组。
    
- **[站点名称] 成员**SharePoint 组包含所有成员中具有**编辑**权限级别的网站成员的访问组。
    
- **[站点名称] 访问**SharePoint 组包含所有成员中具有**读取**权限级别的网站查看器访问组。
    
- 邀请其他成员的成员的功能被禁用。
    
- 启用非成员请求访问的能力。
    
下面是生成的配置。
  
![适用于独立 SharePoint Online 团队网站的敏感级保护。](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
现在可以对网站的资源安全地协作网站，通过一个访问组中的组成员资格的成员。
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a>高度机密的在线 SharePoint 工作组网站

高度机密的在线 SharePoint 工作组网站是独立的工作组站点，这意味着，通过而不是与工作组网站的 Office 365 组成员身份的 SharePoint 组中的成员身份控制权限。
  
若要创建高度机密信息和协作独立的工作组网站，有两个主要步骤。
  
### <a name="step-1-design-your-isolated-site"></a>第 1 步： 设计独立的站点

若要设计独立的工作组站点，您需要确定：
  
- 您的 SharePoint 组和权限级别。
    
- 将中的 SharePoint 组成员的访问组的组。
    
     访问组的推荐的设置是站点成员之一、 网站浏览者和站点管理员。
    
- 您是否使用嵌套组内访问组。
    
例如，组建议的结构和权限级别，如下所示：
  
|**SharePoint 组**|**权限级别**|**访问组 （示例）**|
|:-----|:-----|:-----|
|[站点名称]成员  <br/> |编辑  <br/> |[站点名称]成员  <br/> |
|[站点名称]访问者  <br/> |读取  <br/> |[站点名称]查看器  <br/> |
|[站点名称]所有者  <br/> |完全控制  <br/> |[站点名称]管理员  <br/> |
   
默认情况下，工作组站点创建 SharePoint 组和权限级别。您需要确定您访问权限的组的名称。
  
设计过程的详细信息，请参阅[设计独立的在线 SharePoint 工作组网站](design-an-isolated-sharepoint-online-team-site.md)。
  
### <a name="step-2-deploy-your-isolated-site"></a>步骤 2： 部署独立的站点

若要部署独立的网站，您首先需要：
  
- 确定每种访问组的用户和组成员
    
- 创建访问组并添加用户和组成员
    
- 创建使用访问组独立的团队站点
    
有关详细步骤，请参阅[部署独立的在线 SharePoint 工作组网站](deploy-an-isolated-sharepoint-online-team-site.md)。
  
权限设置的结果是：
  
- **[网站名称] 所有者**SharePoint 组包含所有成员中具有**完全控制**权限级别的网站管理员访问组。
    
- **[站点名称] 成员**SharePoint 组包含所有成员中具有**编辑**权限级别的网站成员的访问组。
    
- **[站点名称] 访问**SharePoint 组包含所有成员中具有**读取**权限级别的网站查看器访问组。
    
- 邀请其他成员的成员的功能被禁用。
    
- 禁用非成员请求访问的能力。
    
下面是生成的配置。
  
![适用于独立 SharePoint Online 团队网站的高度机密级保护。](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
现在可以对网站的资源安全地协作网站，通过一个访问组中的组成员资格的成员。
  
## <a name="next-step"></a>后续步骤

[Office 365 标签和 DLP 与 SharePoint Online 文件保护](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a>See Also

[SharePoint Online 网站和文件保护](secure-sharepoint-online-sites-and-files.md)
  
[开发/测试环境中的安全 SharePoint Online 网站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)




