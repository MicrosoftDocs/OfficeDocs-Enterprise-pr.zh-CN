---
title: "SharePoint Online 的团队站点开发/测试环境的独立"
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
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: "摘要： 配置 Office 365 开发/测试环境中组织的其余部分隔离的 SharePoint Online 工作组网站。"
ms.openlocfilehash: c6115e48f1b2453aaf173b384a30c1cc34ce7b5a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a>SharePoint Online 的团队站点开发/测试环境的独立

 **摘要：**配置与您 Office 365 的开发/测试环境中组织的其余部分隔离的 SharePoint Online 工作组网站。
  
Office 365 中的 SharePoint Online 工作组网站是协作使用公共的文档库，OneNote 笔记本和其他服务的地方。在许多情况下，跨部门或组织希望广泛访问和协作。但是，在某些情况下，要严格控制访问和权限的一小群人之间的协作。
  
通过 SharePoint 组和权限级别控制访问 SharePoint Online 的工作组站点和用户可以执行哪些操作。默认情况下，SharePoint Online 网站有三个访问级别：
  
- **成员**，可以查看、 创建和修改站点上的资源。
    
- **所有者**，拥有网站的完全控制，包括更改权限的能力。
    
- **访问者**的用户才可以查看资源的网站上。
    
此步骤通过秘密研究项目独立 SharePoint Online 团队站点的配置命名为 ProjectX。访问要求如下：
  
- 只有此项目的成员才能访问网站及其内容（文档、OneNote 笔记本、网页），编辑和查看 SharePoint 权限级别是通过组成员身份进行控制。
    
- 只有网站创建者和网站管理员组成员才能管理网站，包括可以修改网站级权限。
    
没有设置独立的 SharePoint Online 团队站点您 Office 365 的开发/测试环境中的三个阶段：
  
1. 创建 Office 365 开发/测试环境。
    
2. 创建 ProjectX 用户和组。
    
3. 创建新的团队 ProjectX SharePoint Online 网站并将其隔离。
    
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果要仅达到最低要求轻量级的方式创建独立的在线 SharePoint 工作组网站，按照在阶段 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)。
  
如果您想要在模拟的企业配置中创建独立的在线 SharePoint 工作组网站，请按[您 Office 365 的开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)。
  
> [!NOTE]
> 创建独立 SharePoint Online 网站不需要模拟的企业开发/测试环境（包括连接 Internet 的模拟 Intranet 和 Windows Server AD 林的目录同步）。可以根据需要选择此选项，以便能够测试独立 SharePoint Online 网站，并在代表典型组织的环境中对其进行试验。 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a>第 2 阶段： 创建用户帐户和访问组

使用中的说明[连接到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)连接到您的全局管理员帐户从 Office 365 跟踪订阅：
  
- 你的计算机（对于轻量级的 Office 365 开发/测试环境）。
    
- CLIENT1 虚拟机（对于企业 Office 365 开发/测试环境）。
    
若要创建新的访问组的 ProjectX 在线 SharePoint 工作组网站，请在 Windows Azure 活动目录模块用于 Windows PowerShell 提示符下运行以下命令：
  
```
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

> [!TIP]
> 单击[此处](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1)为包含所有这篇文章中的 PowerShell 命令的文本文件。
  
填写组织名称（示例：contosotoycompany），你所在位置的两位字符的国家/地区代码，然后从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

从**新建 MsolUser**命令显示时，请注意生成的密码会导致设计器帐户并将其记录在安全的地方。
  
从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

从**新建 MsolUser**命令显示时，请注意生成的密码会导致研究人员帐户并将其记录在安全的地方。
  
从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

从**新建 MsolUser**命令显示时，请注意开发副总裁帐户生成的密码并将其记录在安全的地方。
  
接下来，要到新的访问组中添加新帐户，这些 PowerShell 命令提示符处运行 Windows Azure 活动目录模块用于 Windows PowerShell:
  
```
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

结果：
  
- ProjectX 成员访问组包含会导致设计器和领导研究员用户帐户
    
- ProjectX 管理员访问组中包含您的订购试用期的全局管理员帐户
    
- 使用 ProjectX 查看器访问组包含开发副总裁用户帐户
    
图 1 显示的访问组，其成员资格。
  
**图 1**

![独立 SharePoint Online 组网站的 Office 365 组及其成员资格](images/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a>阶段 3： 创建新的团队 ProjectX SharePoint Online 网站并将其隔离

要为 ProjectX 创建 SharePoint Online 的工作组网站，请执行以下操作：
  
1. 本地计算机 （轻量配置） 上使用浏览器或客户端 1 （模拟的企业配置），登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用您的全局管理员帐户。
    
2. 在图块的列表中，单击**SharePoint**。
    
3. 在您的浏览器新 SharePoint 选项卡上，单击**+ 创建网站**。
    
4. 在**团队站点名称**框中，键入**ProjectX**。在**隐私设置**，选择**专用的只有成员才能访问此网站**。
    
5. 在**团队站点的说明**中，键入**ProjectX 的 SharePoint 网站**，，然后单击**下一步**。
    
6. **谁您想要添加吗**？窗格中，单击**完成**。
    
7. 您的浏览器工具栏中的新**ProjectX 主页**选项卡上单击设置图标，然后单击**网站权限**。
    
8. 在**网站权限**窗格中，单击**高级的权限设置**。
    
9. 在新**权限： 项目 X**在您的浏览器选项卡上，单击**访问请求的设置**。
    
10. 在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**，并**允许访问请求**（以使所有三个复选框都被清除），然后单击**确定**。
    
11. 单击列表中的**ProjectX 成员**。
    
12. 在**用户和用户组**页上，单击**新建**。
    
13. 在**共享**对话框中，键入**ProjectX 成员**，选择它，，然后单击**共享**。
    
14. 单击浏览器上的后退按钮。
    
15. 单击列表中的**ProjectX 的所有者**。
    
16. 在**用户和用户组**页上，单击**新建**。
    
17. 在**共享**对话框中，键入**ProjectX 管理员**，选择它，然后单击**共享**。
    
18. 单击浏览器上的后退按钮。
    
19. 单击列表中的**ProjectX 的访问者**。
    
20. 在**用户和用户组**页上，单击**新建**。
    
21. 在**共享**对话框中，类型**ProjectX 查看器**，选择它，然后单击**共享**。
    
22. 关闭您的浏览器中的**用户和用户组**选项卡，单击在浏览器中， **ProjectX 主页**选项卡，然后关闭**网站权限**窗格。
    
下面介绍了权限配置结果：
  
- ProjectX 成员 SharePoint 组包含仅 ProjectX 成员访问组 （其中包含只会导致设计器和领导研究员用户帐户） 和 ProjectX 组 （其中包含只有全局管理员用户帐户）。
    
- ProjectX 的所有者 SharePoint 组包含仅 ProjectX 管理员访问组 （其中包含只有全局管理员用户帐户）。
    
- ProjectX 访问 SharePoint 组包含仅 ProjectX 查看器访问组 （其中包含开发副总裁用户帐户）。
    
- 成员无法修改网站级权限（只有 ProjectX-Admins 组成员才能修改）。
    
- 其他用户帐户无法访问网站及其资源，也无法请求访问网站。
    
图 2 展示了 SharePoint 组及其成员身份。
  
**图 2**

![独立 SharePoint Online 组网站的 SharePoint Online 组及其成员资格](images/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
现在让我们来演示使用会导致设计器用户帐户的访问权限：
  
1. 关闭您的浏览器， **ProjectX 主页**选项卡，再单击在浏览器中的**Microsoft Office 家庭**。
    
2. 单击您的全局管理员的名称，然后单击**注销**。
    
3. 登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用会导致设计器的帐户名和密码。
    
4. 在图块的列表中，单击**SharePoint**。
    
5. 在您的浏览器的新**SharePoint**选项卡，请在搜索框中，键入**ProjectX**激活搜索，，然后单击**ProjectX**工作组站点。ProjectX 团队站点浏览器中，您会看到一个新的选项卡。
    
6. 单击设置图标。注意到没有为**站点权限**选项。这是正确的因为只有 ProjectX 管理员组的成员可以修改网站上的权限
    
7. 打开选择的记事本或文本编辑器。
    
8. ProjectX 团队站点的 URL 复制并粘贴到记事本或文本编辑器中的新行。
    
9. 在浏览器中新**ProjectX 主页**选项卡，单击**文档**。
    
10. 将 ProjectX 文档文件夹的 URL 复制并粘贴到记事本或文本编辑器中的新行上。
    
11. 在浏览器中的新**ProjectX 文档**选项卡，单击**新建 > Word 文档**。
    
12. **联机单词**页中键入一些文本，等待状态以指明**保存**，请单击浏览器上的后退按钮，然后刷新该页。您应该看到新**Document.docx**在**文档**文件夹中。
    
13. 对于**Document.docx**的文档，单击，然后单击**获取链接**。
    
14. 在**共享 Document.docx**对话框中复制的 URL 并将其粘贴在记事本或文本编辑器中，在新的一行，然后关闭**共享 Document.docx**对话框中。
    
15. 关闭您的浏览器中的**ProjectX 文档**和**SharePoint**选项卡，然后单击**Microsoft Office 主页**选项卡。
    
16. **会导致设计器**的名称，请单击，然后单击**注销**。
    
现在让我们来演示使用开发副总裁用户帐户的访问权限：
  
1. 登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用开发副总裁帐户名和密码。
    
2. 在图块的列表中，单击**SharePoint**。
    
3. 在您的浏览器的新**SharePoint**选项卡，请在搜索框中，键入**ProjectX**激活搜索，，然后单击**ProjectX**工作组站点。ProjectX 团队站点浏览器中，您会看到一个新的选项卡。
    
4. 单击**文档**，然后单击**Document.docx**文件。
    
5. 您的浏览器的**Document.docx**选项卡上，在尝试修改的文本。您应该看到一条消息指出**此文档是只读的。**这被预期行为，因为开发副总裁用户帐户仅具有查看该站点的权限。
    
6. 关闭您的浏览器中的**Document.docx**、 **ProjectX 文档**和**SharePoint**选项卡。
    
7. 单击**Microsoft Office 主页**选项卡，单击**开发副总裁**的名称，然后单击**退出**。
    
现在让我们证明没有权限的用户帐户的访问权限：
  
1. 登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用用户 3 帐户名和密码。
    
2. 在图块的列表中，单击**SharePoint**。
    
3. 在您的浏览器的新**SharePoint**选项卡，在搜索框中键入**ProjectX** ，然后激活搜索。您应该看到该消息**这里没有什么可以与您的搜索。**
    
4. 从记事本或您的文本编辑器打开实例，将 ProjectX 网站的 URL 复制到浏览器的地址栏，然后按**Enter**。您应该看到**拒绝访问**页。
    
5. 在记事本或文本编辑器中，将 ProjectX 文档文件夹的 URL 复制到浏览器的地址栏，然后按**Enter**。您应该看到**拒绝访问**页。
    
6. 在记事本或文本编辑器中，将 Documents.docx 文件的 URL 复制到浏览器的地址栏，然后按**Enter**。您应该看到**拒绝访问**页。
    
7. 关闭您的浏览器中的**SharePoint**选项卡，单击**Microsoft Office 主页**选项卡，单击**用户 3**名，然后单击**注销**。
    
独立的 SharePoint Online 网站现准备了更多的试验过程。
  
## <a name="next-step"></a>下一步

当您准备部署在生产环境中的独立的 SharePoint Online 工作组网站时，请参阅[设计独立的在线 SharePoint 工作组网站](design-an-isolated-sharepoint-online-team-site.md)中的分步设计考虑事项。
  
## <a name="see-also"></a>另请参阅

[SharePoint Online 的独立的团队站点](isolated-sharepoint-online-team-sites.md)
  
[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)




