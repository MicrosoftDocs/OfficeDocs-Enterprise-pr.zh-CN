---
title: Office 365 开发/测试环境中的敏感文件保护
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 摘要：配置和演示 Office 365 信息权限管理如何保护您的敏感文件，即使这些文件发布到错误的 SharePoint Online 网站集也是如此。
ms.openlocfilehash: 3fa771d63ca30fb53ac2c77466546cf3a2098deb
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031567"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Office 365 开发/测试环境中的敏感文件保护

 **摘要：** 配置并演示 Office 365 信息权限管理如何保护您的敏感文件，即使这些文件发布到错误的 SharePoint Online 网站集也是如此。
  
Office 365 中的信息权限管理 (IRM) 是一系列保护从 SharePoint Online 库和列表下载的文档的功能。下载的文件经加密处理并且包含显示存储文件的 SharePoint Online 库的打开、复制、保存和打印权限。
  
使用本文中的说明进行操作，你可以启用和测试 Office 365 中的 IRM，以查看 Office 365 试用订阅中的文件是否包含潜在敏感信息。
  
> [!TIP]
> 单击[此处](https://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>第 1 阶段：构建 Office 365 开发/测试环境

如果只需要测试达到最低要求的轻型敏感文件保护，请按照 [Office 365 dev/test environment](office-365-dev-test-environment.md) 中第 2 阶段和第 3 阶段的说明进行操作。
  
如果你想要测试模拟企业中的敏感文件保护，请按照 [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) 中的说明进行操作。
  
> [!NOTE]
> 测试敏感文件保护不需要模拟企业开发/测试环境，其中包括连接到 Internet 的模拟 intranet 和 Active Directory 域服务（AD DS）林的目录同步。 它在此处作为一个选项提供，以便你可以测试敏感文件保护，并在代表典型组织的环境中对其进行试验。 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>阶段 2：演示受权限保护的站点中的文档如何被泄漏

在此阶段，证明某人可以从受权限保护的站点下载文档，然后将其上载到具有完全开放权限的站点。
  
首先，你可以添加三个新的代表执行人员的用户帐户，并为他们分配 Office 365 E5 许可证。
  
使用[连接到 Office 365 powershell](https://technet.microsoft.com/library/dn975125.aspx)中的说明安装 powershell 模块（如果需要），并连接到你的新 Office 365 订阅（如果需要）：
  
- 你的计算机（对于轻量级的 Office 365 开发/测试环境）。
    
- CLIENT1 虚拟机（对于模拟的企业 Office 365 开发/测试环境）。
    
在“**Windows PowerShell 凭据请求**”对话框中，键入 Office 365 试用订阅中的 Office 365 全局管理员名称（示例：jdoe@contosotoycompany.onmicrosoft.com）和密码。
  
填写组织名称（示例：contosotoycompany）以及你所在位置的两位字符的国家/地区代码，然后从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

在显示的 **New-MsolUser** 命令中，记下 CEO 帐户的生成密码并将其记录在安全的位置。
  
从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

在显示的 **New-MsolUser** 命令中，记下 CFO 帐户的生成密码并将其记录在安全的位置。
  
从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

在显示的 **New-MsolUser** 命令中，记下 COO 帐户的生成密码并将其记录在安全的位置。
  
接下来，创建一个专用的执行人员组，并向其添加新的执行帐户。
  
1. 在浏览器中，转到 Office 门户， [https://admin.microsoft.com](https://admin.microsoft.com)并使用全局管理员帐户登录到你的 office 365 试用订阅。
    
  - 如果使用的是轻型 Office 365 开发/测试环境，请打开 Internet Explorer 或浏览器的专用会话并从本地计算机登录。
    
  - 如果你使用的是模拟的企业 Office 365 开发/测试环境，请使用 Azure 门户连接到 CLIENT1 虚拟机，然后从 CLIENT1 登录。
    
2. 在“**Microsoft Office 主页**”选项卡上，单击“**管理 > 组 > 组**”，然后单击“**添加组**”。
    
3. 在“**添加组**”中，选择“**Office 365 组**”组类型，在“**名称**”和“**组 ID**”中键入“**执行人员**”，为“**隐私**”选择“**专用**”，然后单击“**选择所有者**”。
    
4. 在列表中，单击你的全局管理员帐户名。
    
5. 单击“**添加**”，然后单击“**关闭**”。
    
6. 在组列表中，单击“**执行人员**”。
    
7. 单击“**编辑成员**”。
    
8. 单击“**添加成员**”。在成员列表中，选择下列用户帐户：
    
  - 首席执行官
    
  - 首席财务官
    
  - 首席运营官
    
9. 单击“**保存**”，然后单击“**关闭**”。
    
10. 关闭“**Office 管理中心**”选项卡。
    
接下来，创建一个执行人员网站集，并仅允许执行人员组的成员对其进行访问。
  
1. 在 " **Microsoft Office 主页**" 选项卡上，单击 "**管理**" 磁贴。
    
2. 在 " **Office 管理中心**" 选项卡上，单击 "**管理员中心 > SharePoint**"。
    
3. 在 " **SharePoint 管理中心**" 选项卡上，单击 "**新建 > 专用网站集**"。
    
4. 在 "新建网站集" 窗格**中，在**"URL" 框中键入**行政主管**，在 "**管理员**" 中指定全局管理员帐户的名称，然后单击 **"确定"**。
    
5. 等到创建新网站集。 完成后，复制新的 "执行人员" 网站集的 URL，并将其粘贴到浏览器的新选项卡中。
    
6. 在“**执行人员**”网站集的右上方，单击设置图标，然后单击“**共享**”。
    
7. 在**共享 "高级管理人员"** 中，单击 "**高级**"。
    
8. 在 SharePoint 组列表中，单击“**执行人员成员**”。
    
9. 在“**人员和组**”页中，单击“**新建**”。
    
10. 在 **"共享 ' 执行人员 '"** 中，键入**主管**，单击 "**主管**" 组，然后单击 "**共享**"。
    
11. 关闭 "**人员和组**" 选项卡。
    
接下来，允许每个人访问销售网站集。
  
1. 在 " **SharePoint 管理中心**" 选项卡上，复制 "销售" 网站集的 URL，并将其粘贴到浏览器的新选项卡中。
    
2. 在右上方，单击“设置”图标，然后单击“**共享**”。
    
3. 在 **"共享 ' 销售 ' 网站集 '"** 中，单击 "**高级**"。
    
4. 在 SharePoint 组列表中，单击“**销售网站集成员**”。
    
5. 在“**人员和组**”页面上，单击“**新建**”。
    
6. 在 **"共享" "销售网站集"** 中，键入**everyone**，单击 "**除外部用户之外的所有人**"，然后单击 "**共享**"。
    
7. 关闭“**销售网站集**”和“**SharePoint**”选项卡。
    
接下来，使用执行人员帐户登录并在执行人员网站集中创建文档。
  
1. 在“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。
    
2. 转到 [https://admin.microsoft.com](https://admin.microsoft.com)。
    
3. 在“**Office 365 登录**”页面上，单击“**使用其他帐户**”。
    
4. 键入 **CEO** 帐户名及其密码，然后单击“**登录**”。
    
5. 在浏览器的新选项卡上，键入 "执行人员" 网站集的 URL （ **https://**\<组织名称>**sharepoint.com/sites/executives**）。
    
6. 单击 "**文档**"，单击 "**新建"，** 然后单击 " **Word 文档**"。
    
7. 单击“标题栏”并键入 **SensitiveData BeforeIRM**。
    
8. 单击文档正文并键入**最新董事会会议的会议记录**，然后单击“**执行人员**”。
    
      应该会在**文档**文件夹中看到 **SensitiveData BeforeIRM.docx**。
    
接下来，下载 SensitiveData BeforeIRM.docx 文档的本地副本，然后再意外地将其发布到销售网站集。
  
1. 在您的本地计算机上，创建一个新文件夹（例如，C\\：\\tlg SensitiveDataTestFiles）。
    
2. 在浏览器的“**文档**”选项卡上，选择 **SensitiveData BeforeIRM.docx** 文档，单击省略号，然后单击“**下载**”。
    
3. 将 **SensitiveData BeforeIRM.docx** 文档存储在步骤 1 中创建的文件夹中。
    
4. 在浏览器的新选项卡上，键入 "销售" 网站集的 URL （ **https://**\<组织名称>**sharepoint.com/sites/sales**）。
    
5. 单击**销售网站集**的“**文档**”文件夹。
    
6. 单击“**上载**”，指定步骤 1 中创建的文件夹中的 **SensitiveData BeforeIRM.docx** 文档，然后单击“**确定**”。
    
7. 验证 **SensitiveData BeforeIRM.docx** 文档位于**文档**文件夹。
    
8. 关闭“**销售**”和“**SharePoint**”选项卡。
    
接下来，以 User5 身份登录并尝试打开销售网站集中的 SensitiveData-BeforeIRM.docx 文档。
  
1. 在“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。
    
2. 转到 [https://admin.microsoft.com](https://admin.microsoft.com)。
    
3. 在“**Office 365 登录**”页面上，单击“**使用其他帐户**”。
    
4. 键入 User 5 帐户名及其密码，然后单击“**登录**”。
    
5. 在浏览器的新选项卡上，键入销售网站集的 URL。
    
6. 在**销售网站集**的**文档**文件夹中，单击“**SensitiveData BeforeIRM.docx**”文档。 
    
    应该会看到其内容。
    
7. 关闭“**文档**”和“**销售网站集**”选项卡。
    
通过在销售网站集上意外发布 SensitiveData BeforeIRM.docx 文档，CEO 可以绕过执行人员网站集的权限安全性。
  
若要为阶段 3 和 4 准备 Office 365，请为 SharePoint Online 启用 IRM。
  
1. 在“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。
    
2. 转到 [https://admin.microsoft.com](https://admin.microsoft.com)。
    
3. 在“**Office 365 登录**”页，单击全局管理员帐户名，键入其密码，然后单击“**登录**”。
    
4. 在“**Microsoft Office 主页**”选项卡上，单击“**管理员 > 管理中心 > SharePoint**”。
    
5. 在“**SharePoint 管理中心**”选项卡上，单击“**设置**”。
    
6. 在页面上的 "**信息权限管理（IRM）** " 部分中，选择 "**使用您的配置中指定的 IRM 服务"**，然后选择 "**刷新 IRM 设置**"。
    
7. 关闭“**SharePoint 管理中心**”选项卡。
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>第 3 阶段：将 SharePoint 信息权限管理与 Office 365 专用组配合使用

在此阶段，将 SharePoint 信息权限管理与 Office 365 专用组配合使用以保护对包含敏感信息的文档的访问，即使它在公开权限的站点上发布。
  
首先，可以为执行人员网站集文档库启用和配置 IRM。  
  
1. 在浏览器的新选项卡上，键入 "执行人员" 网站集的 URL。
    
2. 单击“文档”****。
    
3. 在右上方，单击设置图标，然后单击“**库设置**”。
    
4. 在“**设置**”页的“**权限和管理**”下方，单击“**信息权限管理**”。
    
5. 在“**信息权限管理设置**”页上：
    
  - 选择“**限制此库文档的下载权限**”。
    
  - 对于**创建权限策略标题**，键入**执行人员**。
    
  - 对于**添加权限策略说明**，键入**针对执行人员的 IRM**。
    
6. 单击“**显示选项**”。
    
7. 在“**设置其他 IRM 库设置**”下方，选择“**不允许用户上载不支持 IRM 的文档**”。
    
8. 在“**配置文档访问权限**”下方，选择“**允许查看者打印**”和“**允许查看者写入下载文档副本**”。
    
9. 在 "**设置组保护和凭据间隔**" 下，选择 "**允许组保护"。默认组**，然后键入**高级管理人员**。
    
10. 单击“**确定**”。
    
接下来，以 CEO 身份进行操作，将新文档上载到执行人员文档文件夹，下载它，再意外地将其上载到销售文档文件夹。
  
1. 打开存储 **SensitiveData BeforeIRM.docx** 文档的本地文件夹。
    
2. 	右键单击“**SensitiveData BeforeIRM.docx**”，然后单击“**复制**”。
    
3. 在该文件夹内右键单击，然后单击“**粘贴**”。
    
4. 将新的**SensitiveData-BeforeIRM-复制的 .docx**文件重命名为**sensitivedata afterirm.docx**。
    
5. 在浏览器的“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。
    
6. 转到 [https://admin.microsoft.com](https://admin.microsoft.com)。
    
7. 在“**Office 365 登录**”页，单击 CEO 帐户名，键入其密码，然后单击“**登录**”。
    
8. 在浏览器的新选项卡上，键入 "执行人员" 网站集的 URL。
    
9. 在“**文档**”页上，单击“**上载**”，指定本地文件夹中的 **SensitiveData AfterIRM.docx** 文档，然后单击“**打开**”。
    
10. 选择“**文档**”页上新的 **SensitiveData AfterIRM.docx** 文档，单击菜单栏中的省略号 (…)，然后单击“**下载**”。
    
11. 出现提示时，保存本地文件夹中的 **SensitiveData AfterIRM.docx** 文档，并覆盖原始版本。
    
12. 关闭“**文档**”页的选项卡。
    
13. 在浏览器的新选项卡上，键入销售网站集的 URL。
    
14. 单击“文档”****。
    
15. 在“**文档**”页上，单击“**上载**”，指定本地文件夹中的 **SensitiveData AfterIRM.docx** 文档，然后单击“**打开**”。
    
16. 关闭“**销售网站集**”和“**SharePoint**”选项卡。
    
接下来，以普通用户身份进行操作，尝试访问销售文档文件夹中的 **SensitiveData AfterIRM.docx** 文档。
  
1. 在浏览器的“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。
    
2. 转到 [https://admin.microsoft.com](https://admin.microsoft.com)。
    
3. 在 " **Office 365 登录**" 页上，单击 User5 帐户名，键入其密码，然后单击 "**登录**"。
    
4. 在浏览器的新选项卡上，键入销售网站集的 URL。
    
5. 单击“文档”****。
    
6. 在“**文档**”页上，打开 **SensitiveData AfterIRM.docx** 文档。 
    
    您应该会看到一条消息，提示 "对不起，Word 无法打开此文档，因为它受信息权限管理（IRM）保护"。 
    
7. 单击“**在 Word 中编辑**”。如果要打开文件，系统会提示你。单击“**是**”。
    
8. 将提示你登录。键入帐户名称 User5，然后单击“**下一步**”。
    
9. 将提示你提供密码。键入 User 5 帐户密码，然后单击“**登录**”。  
    
    应该会看到一条消息显示如下：“你没有允许打开此文档的凭据”。
    
10. 单击“**否**”。
    
查看 IRM 保护的另一个方法是浏览本地文件夹中的文件。**SensitiveData AfterIRM.docx** 应远大于 **SensitiveData BeforeIRM.docx** 文件。**SensitiveData AfterIRM.docx** 文件经加密处理，并添加有 IRM 保护信息。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)


