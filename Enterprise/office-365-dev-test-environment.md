---
title: Office 365 开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/02/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 摘要：使用此测试实验室指南创建用于评估或开发/测试的 Office 365 试用订阅。
ms.openlocfilehash: 3e7aafc847b28ad7a81373539c2ea30ce304725a
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487582"
---
# <a name="office-365-devtest-environment"></a>Office 365 开发/测试环境

 **摘要：** 使用此测试实验室指南创建用于评估或开发/测试的 Office 365 试用订阅。
  
可以使用 Office 365 试用订阅并创建应用程序的 Office 365 开发/测试环境，或演示 Office 365 的特性和功能。有两个版本：
  
- 轻型 Office 365 开发/测试环境包含从你的主计算机进行访问的 Office 365 试用订阅。
    
    当希望快速演示功能时使用此环境。对于轻量级的 Office 365 开发/测试环境，请仅完成本文中的阶段 2 和阶段 3。
    
- 模拟企业 Office 365 开发/测试环境包含一个 Office 365 试用订阅和一个连接到 Internet 的简化的组织 Intranet（托管在 Microsoft Azure 基础结构服务中）。你可以完全在云中生成此配置。
    
    在以下情况下使用此环境：演示功能，或演示类似于连接到 Internet 的典型的组织网络的环境中的应用，或演示需要此类环境的功能。对于模拟的企业 Office 365 开发/测试环境，请完成本文中的阶段 1、阶段 2 和阶段 3。
    
> [!NOTE]
> 不妨打印这篇文章，以便记录在 30 天的 Office 365 试用订阅期内需要对此环境使用的特定值。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。 
  
![Microsoft 云中的测试实验室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>第 1 阶段：在 Azure 中创建基本配置

按照[基本配置开发/测试环境](base-configuration-dev-test-environment.md)中的说明执行操作。
  
你将需要有一个 Azure 订阅。你可以使用 [Azure 免费试用版](https://azure.microsoft.com/pricing/free-trial/)进行此设置。如果你有 MSDN 或 Visual Studio 订阅，请参阅 [Visual Studio 订阅者的每月 Azure 额度](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。
  
下面是生成的配置。
  
![Azure 中的基础配置开发/测试环境](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
该配置包括 Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>第 2 阶段：创建 Office 365 试用订阅

要启动 Office 365 E5 试用订阅，你首先需要一个虚构公司名称和一个新的 Microsoft 帐户。
  
1. 我们建议你将公司名称 Contoso 的变体用作你的公司名称，它是 Microsoft 示例内容中使用的虚构公司，但这并不是必需的。在此记录虚构的公司名称：![](./media/Common-Images/TableLine.png)
    
2. 要注册新的 Microsoft 帐户，请转到 [https://outlook.com](https://outlook.com)，然后使用新的电子邮件帐户和地址创建一个帐户。此帐户将用于注册 Office 365。
    
  - 在此记录新帐户的名字和姓氏：![](./media/Common-Images/TableLine.png)
    
  - 在此记录新的电子邮件帐户地址：![](./media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>注册 Office 365 E5 试用订阅

1. 对于轻量级的 Office 365 开发/测试环境，打开你的计算机上的 Internet 浏览器并转到 [https://aka.ms/e5trial](https://aka.ms/e5trial)。 
    
    对于模拟的企业 Office 365 开发/测试环境，请使用 CORP\User1 帐户从 Azure 门户连接到 CLIENT1。

    从“开始”屏幕中，运行 Microsoft Edge 然后转到 [https://aka.ms/e5trial](https://aka.ms/e5trial)。
    
2. 在“欢迎，很高兴认识你”**** 页上，请指定：
    
  - 你的实际位置
    
  - 你新的 Microsoft 帐户的名字和姓氏
    
  - 你新的电子邮件帐户地址
    
  - 业务电话号码
    
  - 你虚构的公司名称
    
  - 规模达 250-999 人的组织
    
3. 单击“只需再执行一步”****。
    
4. 在“**创建你的用户 ID**”页上，基于你新的电子邮件地址、@ 符号之后你的虚构公司（删除名称中的所有空格）键入用户名，然后为此新的 Office 365 帐户键入密码（两次）。
    
    将你键入的密码记录在安全的位置。
    
    在此记录你的虚构公司名称，将其称为“组织名称”****：![](./media/Common-Images/TableLine.png)
    
5. 单击“创建我的帐户”****。
    
6. 在“证明你不是机器人”**** 页上，键入可发短信的手机号码，然后单击“给我发短信”****。
    
7. 键入短信中收到的验证代码，然后单击“下一步”****。
    
8. 在此记录登录页面 URL（选择并复制）：![](./media/Common-Images/TableLine.png)
    
9. 在此记录用户 ID（选择并复制）：![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    此值将被称为“Office 365 全局管理员名称”****。
    
10. 看到“你已准备就绪”**** 时，请单击它。
    
11. 在下一页，等到 Office 365 完成设置并且显示所有标题。
    
你应可看到 Office 365 门户主页，可从该页访问 Office Online 服务和 Microsoft 365 管理中心。
  
对于模拟的企业 Office 365 的开发/测试环境，以下是你的结果配置。
  
![Office 365 开发/测试环境](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
此配置包括： 
  
- Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。
    
- Office 365 E5 试用订阅。
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>第 3 阶段：配置 Office 365 试用订阅

在这个阶段，配置包含其他用户的 Office 365 订阅，并为这些用户分配 Office 365 E5 许可证。
  
按照[连接到 Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module) 中的说明，使用以下位置中的 Azure Active Directory PowerShell for Graph 模块连接到 Office 365 订阅：
  
- 你的计算机（对于轻量级的 Office 365 开发/测试环境）。
    
- CLIENT1 虚拟机（对于模拟的企业 Office 365 开发/测试环境）。
    
 在“Windows PowerShell 凭据请求”对话框中，键入 Office 365 全局管理员名称（示例：jdoe@contosotoycompany.onmicrosoft.com）和密码。
  
填写组织名称（示例：contosotoycompany）、你所在位置的两位字符的国家/地区代码以及通用帐户密码，然后 PowerShell 提示符中运行以下命令：

```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a>第 4 阶段：创建 3 个新的 SharePoint Online 团队网站（可选）

在本阶段，配置一组 SharePoint Online 团队网站。
  
1. 安装 [SharePoint Online 命令行管理程序](https://go.microsoft.com/fwlink/p/?LinkId=255251)（x64 版本）。
    
2. 单击“启动”****，键入 **sharepoint**，然后单击“SharePoint Online 命令行管理程序”****。
    
3. 填写你的组织名称（示例：contosotoycompany），然后从 SharePoint Online Management Shell 提示符中运行以下命令以连接到 SharePoint Online 服务
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. 在“Microsoft SharePoint Online 命令行管理程序”**** 对话框中，键入 Office 365 全局管理员名称（示例：jdoe@contosotoycompany.onmicrosoft.com）和密码，然后单击“登录”****。
    
5. 若要创建 3 个新的团队网站（销售、生产和支持），请填入 Office 365 全局管理员名称，然后从 SharePoint Online 命令行管理程序提示符处运行以下命令：
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. 运行此命令以列出这些新网站的 URL：
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. 在 Internet Explorer 中输入生产网站的 URL，以查看生产部门的默认 SharePoint Online 团队网站。
    
## <a name="record-values-for-future-reference"></a>记录这些值以供将来参考

记录这些值，以便用于或部署此测试环境中的其他测试实验室指南：
  
- Office 365 全局管理员名称：![](./media/Common-Images/TableLine.png).onmicrosoft.com（在第 2 阶段的第 9 步中）
    
    此外，还应将此帐户的密码记录在安全位置。
    
- 试用订阅组织名称：![](./media/Common-Images/TableLine.png)（在第 2 阶段的第 4 步中）
    
- 要列出 User 2、User 3、User 4 和 User 5 的帐户，从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：
    
  ```
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    在此记录帐户名称：
    
  - User 2 的帐户名称：user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - User 3 的帐户名称：user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - User 4 的帐户名称：user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - User 5 的帐户名称：user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    此外，在安全位置记录这些帐户的密码。
    
- （可选）若要列出销售、生产和支持团队网站的 URL，从 SharePoint Online 命令行管理程序提示符运行以下命令：
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - 生产网站 URL：https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production
    
  - 销售网站 URL：https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales
    
  - 支持网站 URL：https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support
    
## <a name="next-steps"></a>后续步骤

在 Office 365 开发/测试环境中使用这些附加的文章：
  
- [Office 365 开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)
    
- [用于 Office 365 开发/测试环境的多重身份验证](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [用于 Office 365 开发/测试环境的联合身份](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [用于 Office 365 开发/测试环境的云应用安全](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [Office 365 开发/测试环境中的高级威胁防护](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [用于 Office 365 开发/测试环境的高级电子数据展示](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Office 365 开发/测试环境中的敏感文件保护](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [独立的 SharePoint Online 团队网站开发/测试环境](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [Office 365 开发/测试环境中的数据分类和标记](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
## <a name="see-also"></a>另请参阅

- [云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
- [云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)


