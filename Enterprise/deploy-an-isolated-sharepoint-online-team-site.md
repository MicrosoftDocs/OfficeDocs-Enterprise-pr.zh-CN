---
title: "部署独立的在线 SharePoint 工作组网站"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: "摘要： 部署新独立的 SharePoint Online 工作组网站提供这些分步说明。"
ms.openlocfilehash: 297681b688b43eb02ee4f99f983a0f796312e599
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2018
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>部署独立的在线 SharePoint 工作组网站

 **摘要：**部署新独立的 SharePoint Online 工作组网站提供这些分步说明。
  
本文是用于创建和配置 Microsoft Office 365 中的独立在线 SharePoint 工作组网站逐步部署指南。这些步骤假设使用三个默认 SharePoint 用户组和相应的权限级别，与每个级别的访问权限的单个基于 Azure 活动目录 AD 的访问组。
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>阶段 1： 创建并填充团队站点访问组

在此阶段中，您创建的三个默认 SharePoint 组三个 Azure 基于 AD 的访问组和其中填充适当的用户帐户。
  
> [!NOTE]
> 以下步骤假定所有必要的用户帐户已经存在并分配相应的许可证。如果不是，请将它们添加和分配许可证之前，以步骤 1。 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>步骤 1： 列出网站的 SharePoint Online 管理员

确定组的用户帐户对应于独立的工作组网站的 SharePoint Online 管理员。
  
如果您正在管理用户帐户和组通过 Office 365 并且想要使用 Windows PowerShell，使列表中的用户主体名称 (Upn) (UPN 的示例： belindan@contoso.com)。
  
### <a name="step-2-list-the-members-for-the-site"></a>步骤 2： 列出站点的成员

确定的一套独立的工作组站点，将协作资源存储在该网站上的那些成员所对应的用户帐户。
  
如果您的用户帐户和组通过 Office 365 管理并且想要使用 PowerShell，请其 Upn 的列表。如果有大量的网站成员，您可以 Upn 的列表存储在文本文件中并将其添加所有使用单个 PowerShell 命令。
  
### <a name="step-3-list-the-viewers-for-the-site"></a>步骤 3： 列出了网站的观众

确定的一套独立的工作组站点的那些可以查看网站中存储的资源但没有对其进行修改或直接对其内容进行协作的查看器所对应的用户帐户。
  
如果您的用户帐户和组通过 Office 365 管理并且想要使用 PowerShell，请其 Upn 的列表。如果有大量的网站成员，您可以 Upn 的列表存储在文本文件中并将其添加所有使用单个 PowerShell 命令。
  
查看该站点可能包括行政管理、 法律顾问或执行部门间利益干系人。
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>步骤 4： 创建在 Azure AD 站点的三个访问组

您需要在 Azure AD 中创建以下访问组：
  
- 站点管理员 （这将包含从第 1 步的列表）
    
- 网站成员 （它将包含在步骤 2 中的列表）
    
- 站点访问者 （其中将包含从第 3 步的列表）
    
1. 在浏览器中，转到 Azure 门户网站位于[https://portal.azure.com](https://portal.azure.com)并使用已分配的用户管理管理员或公司管理员角色帐户的凭据登录。
    
2. 在 Azure 门户中，单击“Azure Active Directory”>“用户和组”>“所有组”。
    
3. 在“所有组”边栏选项卡上，单击“+ 新建组”。
    
4. 在“组”边栏选项卡上：
    
  - 在**名称**中键入组的名称。
    
  - 在“成员身份”中选择“已分配”。
    
  - 对“启用 Office 功能”单击“是”。
    
5. 单击“创建”，然后关闭“组”边栏选项卡。
    
6. 对于其他的组，请重复步骤 3-5。
    
> [!NOTE]
> 您需要使用 Azure 门户创建组，以使它们具有 Office 功能已启用。如果以后为高度机密站点使用 Azure 信息保护 (AIP) 标签对文件进行加密并将权限分配给特定的组配置 SharePoint Online 的独立的网站，允许的组必须创建的 Office 功能已启用。它创建后，不能更改 Office 功能设置 Azure AD 组。 
  
这里有三个站点访问组与您生成的配置。
  
![三个适用于部署独立 SharePoint Online 网站的访问组。](images/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>第 5 步。将用户帐户添加到访问组

在此步骤中，请执行以下操作：
  
1. 向站点管理员访问权限组第 1 步中添加的用户的列表
    
2. 在步骤 2 中的用户列表添加成员访问权限的网站用户组
    
3. 到网站查看器访问组从第 3 步中添加的用户的列表
    
如果您在管理用户帐户和组通过 Windows 服务器 AD，将用户添加到适当的访问权限组使用正常的 Windows 服务器 AD 用户和组的管理过程，并等待与 Office 365 订阅进行同步处理。
  
如果您在管理用户帐户和组通过 Office 365，您可以使用 Office 管理中心或 PowerShell。如果您有访问组中的任何重复的组名，您应使用办公室管理中心。
  
对于 Office 管理中心，使用已分配的用户的帐户管理员或公司管理员角色的用户帐户登录和使用组添加合适的用户帐户和组添加到适当的访问权限组。
  
对于 PowerShell，第一个[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。
  
接下来，使用下面的命令块将单个用户帐户添加到访问组：
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> 对于文本文件，其中包含所有 PowerShell 命令和 Excel 配置 PowerShell 命令将生成的工作表中根据您的组和用户帐户名称、 下载[独立 SharePoint 在线团队站点部署工具包](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)。 
  
如果在文本文件中存储访问组中的任何用户帐户的 Upn，可以使用下面的 PowerShell 命令块要一次添加它们：
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

对于 PowerShell，使用下面的命令块单独的组添加到访问组：
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

结果应如下：
  
- 站点管理员 Azure AD 组包含站点管理员用户帐户或组
    
- 网站成员 Azure AD 组包含站点成员用户帐户或组
    
- 网站查看 Azure AD 组中包含的用户帐户或组，可以只查看网站内容
    
验证列表中的每个访问组与 Office 管理中心或以下 PowerShell 命令块组成员：
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

这里是您生成的配置与使用用户帐户或组填充三个站点访问组。
  
![三个使用用户帐户填充的访问组。](images/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>第 2 阶段： 创建和配置独立的工作组站点

在此阶段中，您可以创建独立的 SharePoint Online 网站并配置默认 SharePoint Online 权限级别来使用新的 Azure 基于 AD 的访问组的权限。
  
首先，通过这些步骤创建 SharePoint Online 的工作组网站。
  
1. 登录到 Office 365 门户网站也将用来管理 SharePoint Online 工作组网站 （SharePoint Online 管理员） 的帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磁贴列表中，单击“SharePoint”。
    
3. 在您的浏览器的新**SharePoint**选项卡，单击**+ 创建网站**。
    
4. 在“创建网站”页中，单击“团队网站”。
    
5. 在**站点名称**中，键入工作组网站的名称。 
    
6. 在**团队站点描述中，**键入站点的用途的可选说明。
    
7. 在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。
    
8. 在“希望添加哪些人员?”窗格中，单击“完成”。
    
接下来，从新的 SharePoint Online 团队站点配置权限。
  
1. 在工具栏上，单击设置图标，然后单击**网站权限**。
    
2. 在“网站权限”窗格中，单击“高级权限设置”。
    
3. 在浏览器的新“权限”标签页中，单击“访问请求设置”。
    
4. 在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**，并**允许访问请求**（以使所有三个复选框都被清除），然后单击**确定**。
    
5. 在浏览器**权限**选项卡上，单击**\<网站名称 > 成员**列表中。
    
6. 在**用户和用户组**中，单击**新建**。
    
7. 在**共享**对话框中，键入成员访问权限的网站用户组的名称，选择它，然后单击**共享**。
    
8. 单击浏览器上的后退按钮。
    
9. 单击**\<网站名称 > 所有者**在列表中。
    
10. 在**用户和用户组**中，单击**新建**。
    
11. 在**共享**对话框中，键入管理员访问权限的网站用户组的名称，选择它，然后单击**共享**。
    
12. 单击浏览器上的后退按钮。
    
13. 单击**\<网站名称 > 访问者**在列表中。
    
14. 在**用户和用户组**中，单击**新建**。
    
15. 在**共享**对话框中，键入站点查看器访问组的名称，选择它，，然后单击**共享**。
    
16. 关闭浏览器的“权限”选项卡。
    
这些权限设置的结果是：
  
- **\<网站名称 > 所有者**SharePoint 组包含所有成员中具有**完全控制**权限级别的网站管理员访问组。
    
- **\<网站名称 > 成员**SharePoint 组包含在所有的成员拥有**编辑**权限级别的网站成员访问组。
    
- **\<网站名称 > 访问者**SharePoint 组包含所有成员中具有**读取**权限级别的网站查看器访问组。
    
- 邀请其他成员的成员或非成员请求访问的功能被禁用。
    
这里是您与网站配置为使用与用户帐户填充的三个访问组或 Azure AD 组三个 SharePoint 组生成的配置。
  
![包含访问组和用户帐户的独立 SharePoint Online 网站的最终配置。](images/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
您和网站，通过一个访问组中的组成员资格的成员可以立即协同使用网站的资源。
  
## <a name="next-step"></a>后续步骤

当您需要更改网站访问组成员身份或创建具有自定义权限的文档文件夹时，请参阅[管理独立的在线 SharePoint 工作组网站](manage-an-isolated-sharepoint-online-team-site.md)。
  
## <a name="see-also"></a>另请参阅

[SharePoint Online 的独立的团队站点](isolated-sharepoint-online-team-sites.md)
  
[设计独立的在线 SharePoint 工作组网站](design-an-isolated-sharepoint-online-team-site.md)
  
[管理独立的在线 SharePoint 工作组网站](manage-an-isolated-sharepoint-online-team-site.md)
  
[安全解决方案](security-solutions.md)



