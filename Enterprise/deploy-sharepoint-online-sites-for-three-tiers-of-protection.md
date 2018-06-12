---
title: 部署具有三层保护的 SharePoint Online 网站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: 摘要：为各种级别的信息保护创建和配置 SharePoint Online 团队网站。
ms.openlocfilehash: 84b455809e210fb40d4a92396b2d8c4eb18245b1
ms.sourcegitcommit: b2058b34196022668eac15e723962fefd82d6774
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2018
ms.locfileid: "19631393"
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a>部署具有三层保护的 SharePoint Online 网站

 **摘要：** 为各种级别的信息保护创建和配置 SharePoint Online 团队网站。
  
使用本文中的步骤设计和部署基线、敏感和高度机密的 SharePoint Online 团队网站。 有关三层保护的详细信息，请参阅[保护 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)。
  
## <a name="baseline-sharepoint-online-team-sites"></a>基线 SharePoint Online 团队网站

基线保护同时包括公共和专用团队网站。 组织中的任何人均可发现并访问公共团队网站。 只有与团队网站关联的 Office 365 组的成员才可以发现并访问专用网站。 两种类型的团队网站均允许成员与他人共享网站。
  
### <a name="public"></a>公开

若要创建具有公共访问和权限的基线 SharePoint Online 团队网站，请执行以下操作：
  
1. 请通过还可用于管理 SharePoint Online 团队网站的帐户（即 SharePoint Online 管理员帐户）登录 Office 365 门户。如需帮助，请参阅[在何处登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磁贴列表中，单击“SharePoint”****。
    
3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”********。
    
4. 在“创建网站”页中，单击“团队网站”********。
    
5. 在“网站名称”中，键入公共团队网站的名称****。 
    
6. 在“团队网站说明”中，键入关于网站用途的说明。****
    
7. 在“隐私设置”中，选择“公用 - 组织中的任何人均可访问此网站”，然后单击“下一步”************。
    
8. 在“希望添加哪些人员?”窗格中，单击“完成”********。
    
下面是生成的配置。
  
![适用于公共 SharePoint Online 团队网站的基线级保护。](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a>私有

若要创建具有私有访问和权限的基线 SharePoint Online 团队网站，请执行以下操作：
  
1. 请通过还可用于管理 SharePoint Online 团队网站的帐户（即 SharePoint Online 管理员帐户）登录 Office 365 门户。如需帮助，请参阅[在何处登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磁贴列表中，单击“SharePoint”****。
    
3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”********。
    
4. 在“创建网站”页中，单击“团队网站”********。
    
5. 在“网站名称”中，键入专用团队网站的名称****。 
    
6. 在“团队网站说明”中，键入关于网站用途的说明。****
    
7. 在“隐私设置”中，选择“专用 - 仅成员可以访问此网站”，然后单击“下一步”************。
    
8. 在“希望添加哪些人员?”窗格中的“添加成员”中，键入有权访问此专用团队网站的用户帐户的名称********。
    
9. 将最初的一组成员添加到网站后，单击“完成”。****
    
下面是生成的配置。
  
![适用于专用 SharePoint Online 团队网站的基线级保护。](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a>敏感 SharePoint Online 团队网站

敏感 SharePoint Online 团队网站是独立的团队网站，这意味着通过 SharePoint 组的成员身份而不是与该团队网站关联的 Office 365 组中的成员身份控制权限。
  
要创建一个独立的团队网站，请按照以下两个主要步骤操作。
  
### <a name="step-1-design-your-isolated-site"></a>步骤 1：设计独立网站

要设计独立的团队网站，需要确定：
  
- SharePoint 组和权限级别。
    
- 将成为 SharePoint 组的成员的一组访问组。
    
     一组建议的访问组，团队成员、网站查看者和网站管理员各一个。
    
- 是否会在访问组中使用嵌套组。
    
例如，建议的组结构和权限级别如下所示：
  
|**SharePoint 组**|**权限级别**|**访问组（示例）**|
|:-----|:-----|:-----|
|[网站名称] 成员  <br/> |编辑  <br/> |[网站名称] 成员  <br/> |
|[网站名称] 访问者  <br/> |读取  <br/> |[网站名称] 查看者  <br/> |
|[网站名称] 所有者  <br/> |完全控制  <br/> |[网站名称] 管理员  <br/> |
   
默认情况下，为团队网站创建了 SharePoint 组和权限级别。 需要确定访问组的名称。
  
有关设计过程的详细信息，请参阅[设计独立的 SharePoint Online 团队网站](design-an-isolated-sharepoint-online-team-site.md)。
  
### <a name="step-2-deploy-your-isolated-site"></a>步骤 2：部署独立网站

要部署独立网站，首先需要：
  
- 确定要添加到每个访问组的用户帐户和组。
    
- 创建访问组并添加用户和组成员。
    
有关详细步骤，请参阅[部署独立的 SharePoint Online 团队网站](deploy-an-isolated-sharepoint-online-team-site.md)的阶段 1****。
  
接下来，使用以下步骤创建 SharePoint Online 团队网站。
  
1. 请通过还可用于管理 SharePoint Online 团队网站的帐户（即 SharePoint Online 管理员帐户）登录 Office 365 门户。如需帮助，请参阅[在何处登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磁贴列表中，单击“SharePoint”****。
    
3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。********
    
4. 在“创建网站”页中，单击“团队网站”********。
    
5. 在“网站名称”中，键入专用团队网站的名称****。
    
6. 在“团队网站”说明中，键入说明（可选）。****
    
7. 在“隐私设置”中，选择“专用 - 仅成员可以访问此网站”，然后单击“下一步”************。
    
8. 在“希望添加哪些人员?”窗格中，单击“完成”********。
    
接下来，在新的 SharePoint Online 团队网站中，按照以下步骤操作来配置权限。
  
1. 确定 IT 管理员或将负责响应和处理网站访问请求的其他人员的用户主体名称 (UPN)（例如，belindan@contoso.com）。记下此 UPN：![](./images/Common_Images/TableLine.png)。
    
2. 在工具栏中，依次单击设置图标和“网站权限”****。
    
3. 在“网站权限”窗格中，单击“高级权限设置”********。
    
4. 在浏览器的新“权限”标签页中，单击“访问请求设置”********。
    
5. 在“访问请求设置”对话框中****：
    
  - 清除“允许成员共享网站和单独的文件和文件夹”和“允许成员邀请他人到网站成员组”复选框********。
    
  - 在“发送所有访问请求”中键入步骤 1 中的 IT 管理员的 UPN****。
    
  - 单击" **确定**"。
    
6. 在浏览器的新“权限”标签页中，单击列表中的“[网站名称] 成员”********。
    
7. 在“人员和组”中，单击“新建”********。
    
8. 在“共享”对话框中，键入此网站的网站成员访问组的名称，将其选中，然后单击“共享”********。
    
9. 单击浏览器上的后退按钮。
    
10. 在列表中单击“[网站名称] 所有者”****。
    
11. 在“人员和组”中，单击“新建”********。
    
12. 在“共享”对话框中，键入此网站的网站管理员访问组的名称，将其选中，然后单击“共享”********。
    
13. 单击浏览器上的后退按钮。
    
14. 在列表中单击“[网站名称] 访问者”****。
    
15. 在“人员和组”中，单击“新建”********。
    
16. 在“共享”对话框中，键入此网站的网站查看者访问组的名称，将其选中，然后单击“共享”********。
    
17. 关闭浏览器的“权限”标签页****。
    
以下是这些权限设置的结果：
  
- [网站名称] 所有者：SharePoint 组包含网站管理员访问组，其中的所有成员均具有“完全控制”权限级别********。
    
- [网站名称] 成员：SharePoint 组包含网站成员访问组，其中的所有成员均具有编辑权限级别********。
    
- [网站名称] 访问者：SharePoint 组包含网站查看者访问组，其中的所有成员均具有读取权限级别********。
    
- 禁用成员邀请其他成员的功能。
    
- 启用非成员请求访问的功能。
    
下面是生成的配置。
  
![适用于独立 SharePoint Online 团队网站的敏感级保护。](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
通过其中一个访问组的组成员身份，网站成员现可对网站资源进行安全协作。
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a>高度机密的 SharePoint Online 团队网站

高度机密的 SharePoint Online 团队网站是独立的团队网站，这意味着通过 SharePoint 组的成员身份而不是与该团队网站关联的 Office 365 组中的成员身份控制权限。
  
要针对高度机密的信息和协作创建独立的团队网站，需要完成两个主要步骤。
  
### <a name="step-1-design-your-isolated-site"></a>步骤 1：设计独立网站

要设计独立的团队网站，需要确定：
  
- SharePoint 组和权限级别。
    
- 将成为 SharePoint 组的成员的一组访问组。
    
     一组建议的访问组，团队成员、网站查看者和网站管理员各一个。
    
- 是否会在访问组中使用嵌套组。
    
例如，建议的组结构和权限级别如下所示：
  
|**SharePoint 组**|**权限级别**|**访问组（示例）**|
|:-----|:-----|:-----|
|[网站名称] 成员  <br/> |编辑  <br/> |[网站名称] 成员  <br/> |
|[网站名称] 访问者  <br/> |读取  <br/> |[网站名称] 查看者  <br/> |
|[网站名称] 所有者  <br/> |完全控制  <br/> |[网站名称] 管理员  <br/> |
   
默认情况下，为团队网站创建了 SharePoint 组和权限级别。 需要确定访问组的名称。
  
有关设计过程的详细信息，请参阅[设计独立的 SharePoint Online 团队网站](design-an-isolated-sharepoint-online-team-site.md)。
  
### <a name="step-2-deploy-your-isolated-site"></a>步骤 2：部署独立网站

要部署独立网站，首先需要：
  
- 确定每个访问组的用户和组成员
    
- 创建访问组并添加用户和组成员
    
- 创建使用访问组的独立团队网站
    
有关详细步骤，请参阅[部署独立的 SharePoint Online 团队网站](deploy-an-isolated-sharepoint-online-team-site.md)。
  
以下是这些权限设置的结果：
  
- [网站名称] 所有者：SharePoint 组包含网站管理员访问组，其中的所有成员均具有“完全控制”权限级别********。
    
- [网站名称] 成员：SharePoint 组包含网站成员访问组，其中的所有成员均具有编辑权限级别********。
    
- [网站名称] 访问者：SharePoint 组包含网站查看者访问组，其中的所有成员均具有读取权限级别********。
    
- 禁用成员邀请其他成员的功能。
    
- 禁用非成员请求访问的功能。
    
下面是生成的配置。
  
![适用于独立 SharePoint Online 团队网站的高度机密级保护。](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
通过其中一个访问组的组成员身份，网站成员现可对网站资源进行安全协作。
  
## <a name="next-step"></a>后续步骤

[使用 Office 365 标签和 DLP 保护 SharePoint Online 文件](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a>另请参阅

[保护 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)
  
[在开发/测试环境中保护 SharePoint Online 网站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)




