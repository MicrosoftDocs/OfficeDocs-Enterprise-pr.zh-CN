---
title: 独立 SharePoint Online 团队网站开发/测试环境
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
description: 摘要： 配置的 Office 365 开发/测试环境中的组织的其余部分隔离的 SharePoint Online 团队网站。
ms.openlocfilehash: d2a75f3a3a410116c454892c9ecf3747fb3da53d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915047"
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a>独立 SharePoint Online 团队网站开发/测试环境

 **摘要：** 配置 Office 365 开发/测试环境的组织的其余部分隔离的 SharePoint Online 团队网站。
  
Office 365 中的 SharePoint Online 团队网站是协作使用常见的文档库、 OneNote 笔记本和其他服务的位置。在许多情况下，跨部门或组织希望范围访问和协作。但是，在某些情况下，您想要严格控制访问和小组人之间的协作程序的权限。
  
由 SharePoint 组和权限级别控制访问 SharePoint Online 团队网站和用户可以执行的操作。默认情况下，SharePoint Online 网站具有三种访问级别：
  
- **成员**：可以在网站上查看、创建和修改资源。
    
- **所有者**：可完全控制网站，包括能够更改权限。
    
- **访问者**：只能在网站上查看资源。
    
此文章步骤您通过独立的 SharePoint Online 团队网站机密信息检索项目的配置名为 ProjectX。访问要求如下：
  
- 只有此项目的成员才能访问网站及其内容（文档、OneNote 笔记本、网页），编辑和查看 SharePoint 权限级别是通过组成员身份进行控制。
    
- 只有网站创建者和网站管理员组成员才能管理网站，包括可以修改网站级权限。
    
有三个阶段设置 Office 365 开发/测试环境中的独立 SharePoint Online 团队网站：
  
1. 创建 Office 365 开发/测试环境。
    
2. 创建 ProjectX 用户和组。
    
3. 创建新的 ProjectX SharePoint Online 团队网站，并将其隔离。
    
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境

如果您只想要的最低硬件要求与轻型的方式创建独立的 SharePoint Online 团队网站，请在阶段 2 和 3 的[Office 365 开发/测试环境](office-365-dev-test-environment.md)按照的说明。
  
如果您想要创建独立的 SharePoint Online 团队网站模拟的企业配置中，按照[目录同步的 Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明。
  
> [!NOTE]
> 创建独立 SharePoint Online 网站不需要模拟的企业开发/测试环境（包括连接 Internet 的模拟 Intranet 和 Windows Server AD 林的目录同步）。可以根据需要选择此选项，以便能够测试独立 SharePoint Online 网站，并在代表典型组织的环境中对其进行试验。 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a>阶段 2： 创建用户帐户并访问组

使用中的说明[连接到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)连接到您的全局管理员帐户从 Office 365 线索订阅：
  
- 你的计算机（对于轻量级的 Office 365 开发/测试环境）。
    
- CLIENT1 虚拟机（对于模拟的企业 Office 365 开发/测试环境）。
    
若要创建新的访问组 ProjectX SharePoint Online 团队网站，请在 Windows Azure Active Directory 模块用于 Windows PowerShell 提示符处运行以下命令：
  
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

在安全的位置上，记下显示的 **New-MsolUser** 命令中为 Lead Designer 帐户生成的密码。
  
从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

在安全的位置上，记下显示的 **New-MsolUser** 命令中为 Lead Researcher 帐户生成的密码。
  
从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

在安全的位置上，记下显示的 **New-MsolUser** 命令中为 Development VP 帐户生成的密码。
  
接下来，将新的帐户添加到新的访问组，这些 PowerShell 命令提示符处运行 Windows Azure Active Directory 的 Windows PowerShell 模块：
  
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
  
- ProjectX 成员访问组包含导致 Designer 和导致研究人员用户帐户
    
- ProjectX Admins 访问组包含您的试用版订阅的全局管理员帐户
    
- ProjectX 查看器访问组包含开发 VP 用户帐户
    
图 1 显示了访问组和其成员资格。
  
**图 1**

![独立 SharePoint Online 组网站的 Office 365 组及其成员资格](media/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a>阶段 3： 创建新的 ProjectX SharePoint Online 团队网站，并将其隔离

要创建 ProjectX SharePoint Online 团队网站，请执行以下操作：
  
1. 本地计算机 （轻型配置） 上使用浏览器或在 CLIENT1 上 （模拟的企业配置），登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用全局管理员帐户。
    
2. 在磁贴列表中，单击“SharePoint”****。
    
3. 在新 SharePoint 选项卡在浏览器中，单击 **+ 创建网站**。
    
4. 在**工作组网站名称**框中，键入**ProjectX**。在**隐私设置**中，选择**专用-只有成员可以访问此网站**。
    
5. 在**团队网站说明**框中，键入**ProjectX 的 SharePoint 网站**，然后单击**下一步**。
    
6. 在**要添加人员**？窗格中，单击**完成**。
    
7. 在浏览器中，在工具栏中，在新**ProjectX 主页**选项卡上单击设置图标，然后单击**网站权限**。
    
8. 在“网站权限”窗格中，单击“高级权限设置”********。
    
9. 在新**权限： 项目 X**选项卡上在浏览器中，单击**访问请求设置**。
    
10. 在**访问请求设置**对话框中，清除**允许成员来共享网站和单独的文件和文件夹**和**允许访问请求**（以便清除所有三个复选框），然后单击**确定**。
    
11. 在列表中单击**ProjectX 成员**。
    
12. 在“人员和组”页中，单击“新建”********。
    
13. **共享**对话框中，键入**ProjectX 成员**和选择它，然后单击**共享**。
    
14. 单击浏览器上的后退按钮。
    
15. 在列表中单击**ProjectX 所有者**。
    
16. 在“人员和组”页中，单击“新建”********。
    
17. 在**共享**对话框中，键入**ProjectX 管理员**，选择它，，然后单击**共享**。
    
18. 单击浏览器上的后退按钮。
    
19. 在列表中，单击**ProjectX 访问者**。
    
20. 在“人员和组”页中，单击“新建”********。
    
21. **共享**对话框中，键入**ProjectX 查看者**，选择它，，然后单击**共享**。
    
22. 关闭浏览器中的**人员和组**选项卡，单击浏览器中， **ProjectX 主页**选项卡，然后关闭**网站权限**窗格。
    
权限的配置结果如下所示：
  
- ProjectX 成员 SharePoint 组包含仅 ProjectX 成员访问 （其中包含只会导致设计器和导致研究人员用户帐户） 和 ProjectX 组 （其中包含仅的全局管理员用户帐户）。
    
- ProjectX 所有者 SharePoint 组包含仅 ProjectX Admins 访问组 （其中包含仅的全局管理员用户帐户）。
    
- ProjectX 访问者 SharePoint 组包含仅 ProjectX 查看器访问组 （其中包含只有开发 VP 用户帐户）。
    
- 成员无法修改网站级权限（只有 ProjectX-Admins 组成员才能修改）。
    
- 其他用户帐户无法访问网站及其资源，也无法请求访问网站。
    
图 2 展示了 SharePoint 组及其成员身份。
  
**图 2**

![独立 SharePoint Online 组网站的 SharePoint Online 组及其成员资格](media/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
现在让我们演示使用导致设计器的用户帐户的访问：
  
1. 关闭浏览器中， **ProjectX 主页**选项卡，然后单击在浏览器中的**Microsoft Office Home**选项卡。
    
2. 单击您的全局管理员的名称，然后单击**注销**。
    
3. 登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用导致 Designer 帐户名和其密码。
    
4. 在磁贴列表中，单击“SharePoint”****。
    
5. 在新**SharePoint**选项卡在浏览器中，在搜索框中键入**ProjectX**激活搜索，，然后单击**ProjectX**工作组网站。在浏览器中的 ProjectX 工作组网站，您应看到新选项卡。
    
6. 单击设置图标。请注意，没有**网站**权限的选项。这是正确的因为只会将 ProjectX Admins 组的成员可以修改网站上的权限
    
7. 打开选择的记事本或文本编辑器。
    
8. 复制 ProjectX 工作组网站的 URL，并将其粘贴到记事本或文本编辑器中的新行。
    
9. 在新**ProjectX 主页**选项卡在浏览器中，单击**文档**。
    
10. 将 ProjectX 文档文件夹的 URL 复制并粘贴到记事本或文本编辑器中的新行上。
    
11. 在新**ProjectX 文档**选项卡在浏览器中，单击**新建 > Word 文档**。
    
12. 在**Word Online**页上键入一些文本，等待状态指示**保存**，单击浏览器中，在后退按钮，然后刷新页面。您应看到新**Document.docx** **文档**文件夹中。
    
13. 单击省略号**Document.docx**文档，然后单击**获取链接**。
    
14. 在**共享 Document.docx'** 对话框中复制的 URL 和将其粘贴到记事本或文本编辑器中中的新行，然后关闭**共享 Document.docx**对话框中。
    
15. 关闭浏览器中的**ProjectX 文档**和**SharePoint**选项卡，然后单击**Microsoft Office Home**选项卡。
    
16. 单击**导致设计器**名称，然后单击**注销**。
    
现在让我们演示使用开发 VP 用户帐户的访问：
  
1. 登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用的开发 VP 帐户名和其密码。
    
2. 在磁贴列表中，单击“SharePoint”****。
    
3. 在新**SharePoint**选项卡在浏览器中，在搜索框中键入**ProjectX**激活搜索，，然后单击**ProjectX**工作组网站。在浏览器中的 ProjectX 工作组网站，您应看到新选项卡。
    
4. 单击**文档**，然后单击**Document.docx**文件。
    
5. 在浏览器中**Document.docx**选项卡上，在尝试修改的文本。您应看到一条消息指出**本文档是只读的。** 此举有望因为的开发 VP 用户帐户只具有该网站的查看权限。
    
6. 关闭浏览器中的**Document.docx**、 **ProjectX 文档**和**SharePoint**选项卡。
    
7. 单击**Microsoft Office Home**选项卡，单击**开发 VP**名称，然后单击**注销**。
    
现在让我们演示使用没有任何权限的用户帐户的访问：
  
1. 登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用用户 3 帐户名和其密码。
    
2. 在磁贴列表中，单击“SharePoint”****。
    
3. 在新**SharePoint**选项卡在浏览器中，在搜索框中键入**ProjectX** ，然后激活搜索。您应看到消息**Nothing 此处匹配您的搜索。**
    
4. 从记事本或文本编辑器打开实例，将 ProjectX 网站的 URL 复制到您的浏览器的地址栏，然后按**Enter**。您应看到**访问被拒绝**页面。
    
5. 从记事本或文本编辑器中，将 ProjectX 文档文件夹的 URL 复制到您的浏览器的地址栏，然后按**Enter**。您应看到**访问被拒绝**页面。
    
6. 从记事本或文本编辑器中，复制到您的浏览器的地址栏的 Documents.docx 文件的 URL，然后按**Enter**。您应看到**访问被拒绝**页面。
    
7. 关闭浏览器中的**SharePoint**选项卡，单击**Microsoft Office Home**选项卡，单击**用户 3**的名称，，然后单击**注销**。
    
独立的 SharePoint Online 网站现在就您的其他实验。
  
## <a name="next-step"></a>后续步骤

当准备好在生产中部署单独的 SharePoint Online 团队网站后，请参阅[设计单独的 SharePoint Online 团队网站](design-an-isolated-sharepoint-online-team-site.md)中的分步设计注意事项。
  
## <a name="see-also"></a>另请参阅

[独立 SharePoint Online 团队网站](isolated-sharepoint-online-team-sites.md)
  
[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)




