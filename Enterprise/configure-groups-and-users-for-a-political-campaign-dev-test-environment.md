---
title: 为政治宣传活动开发/测试环境配置组和用户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: 摘要：通过用户和组创建适用于政治宣传活动开发/测试环境的 Office 365 和 Microsoft 企业移动性 + 安全性 (EMS) 试用订阅。
ms.openlocfilehash: df737e3f745ba0fa4ab4752609e09e8af64ce6b0
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "19168506"
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>为政治宣传活动开发/测试环境配置组和用户

 **摘要**：通过用户和组创建适用于政治宣传活动开发/测试环境的 Office 365 和 Microsoft 企业移动性 + 安全性 (EMS) 试用订阅。
  
使用本文中的说明创建一个开发/测试环境，其中包含[面向政治宣传活动、非盈利组织和其他敏捷组织的 Microsoft 安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)解决方案的简化用户帐户和组。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>第 1 阶段：创建 Office 365 开发/测试环境

在此阶段，将获取用于虚拟组织（代表政治宣传活动）的 Office 365 E5 和企业移动性 + 安全性 (EMS) E5 的试用订阅。
  
首先，按照 [Office 365 开发/测试环境](office-365-dev-test-environment.md)的**阶段 2** 中的说明进行操作。
  
下一步，注册 EMS E5 试用订阅，并将其作为 Office 365 试用订阅添加到同一组织。
  
1. 如有需要，请使用试用订阅的全局管理员帐户的凭据登录 Office 365 门户。如需帮助，请参阅[在哪里登录 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 单击“管理员”磁贴****。
    
3. 在浏览器的“Office 管理中心”标签页的左侧导航中，单击“帐单”>“购买服务”********。
    
4. 在“购买服务”页上，找到“企业移动性 + 安全性 E5”项。将鼠标指针悬停在此项之上，然后单击“开始免费试用”************。
    
5. 在“确认订单”页上，单击“立即试用”********。
    
6. 在“订单签收”页上，单击“继续”********。
    
接下来，为全局管理员帐户启用 EMS E5 许可证。
  
1. 在浏览器的“Office 365 管理中心”**** 标签页的左侧导航中，单击“用户”>“活动用户”****。
    
2. 单击全局管理员帐户，然后针对“产品许可证”单击“编辑”********。
    
3. 在“产品许可证”**** 窗格，将“企业移动 +安全 E5”**** 的产品许可证设置为“打开”****，单击“保存”****，然后单击“关闭”**** 两次。
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>第 2 阶段：创建和配置 Azure Active Directory (AD) 组

在此阶段，为活动创建和配置 Azure AD 组。
  
首先，通过 Azure 门户为典型政治宣传活动创建一系列组。
  
1. 在浏览器的单独标签页上，转到 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))。如有需要，请使用 Office 365 E5 试用订阅的全局管理员帐户凭据登录。
    
2. 在 Azure 门户中，单击“Azure Active Directory”>“用户和组”>“所有组”****。
    
3. 对此列表中的每个组名称执行以下步骤：
    
  - 高级和战略人员
    
  - IT 人员
    
  - 分析人员
    
  - 常规核心人员
    
  - 运营人员
    
  - 现场人员
    
1. 在“所有组”边栏选项卡上，单击“+ 新建组”********。
    
2. 在“名称”**** 中键入列表中的组名称。
    
3. 在“成员资格”**** 中选择“动态用户”****。
    
4. 对“启用 Office 功能”单击“是”********。
    
5. 单击“添加动态查询”****。
    
6. 在“添加以下位置的用户”**** 中，选择“部门”****。
    
7. 在下一个字段中，选择“等于”****。
    
8. 在下一个字段中，键入列表中的组名称。
    
9. 单击“添加查询”****，然后单击“创建”****。
    
10. 单击“用户和组 - 所有组”****。
    
接下来，配置组以便成员被自动分配 Office 365 E5 和 EMS E5 许可证。
  
1. 在 Azure 门户中，单击“Azure Active Directory”>“许可证”>“所有产品”****。
    
2. 在列表中，选择“企业移动性 + 安全性 E5”**** 和“Office 365 企业版 E5”****，然后单击“+ 分配”****。
    
3. 在“分配许可证”边栏选项卡中，单击“用户和组”********。
    
4. 在组列表中，选择以下各项：
    
  - 分析人员
    
  - 现场人员
    
  - IT 人员
    
  - 运营人员
    
  - 常规核心人员
    
  - 高级和战略人员
    
5. 单击“选择”****，然后单击“分配”****。
    
6. 关闭浏览器中的 Azure 门户选项卡。
    
## <a name="phase-3-add-your-user-accounts"></a>第 3 阶段：添加用户帐户

在这一阶段，为政治宣传活动添加示例用户帐户。
  
首先，[连接到 Azure Active Directory V2 PowerShell 模块](https://go.microsoft.com/fwlink/?linkid=842218)。
  
接下来，填写你的组织名称、位置和常用密码，然后从 PowerShell 命令提示符或集成的脚本环境 (ISE) 运行这些命令：
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> 此处使用常用密码是为了自动化和方便配置开发/测试环境。但是对于生产订阅，不建议这样做。在登录这些新用户帐户时，系统将提示你更改密码。 
  
使用这些步骤验证动态组成员资格和基于组的许可是否工作正常。
  
1. 在浏览器的“Microsoft Office 主页”标签页中，单击“管理员”磁贴********。
    
2. 在浏览器的新“Office 管理中心”标签页中，单击“用户”********。
    
3. 在用户列表中，单击“候选人”****。
    
4. 在列出“候选人”**** 用户帐户属性的窗格中，确保：
    
  - 它是“高级和战略人员”**** 组（位于“组成员资格”****）的成员。
    
  - 它已被分配“企业移动性 + 安全性 E5”**** 和“Office 365 企业 E5”**** 许可证（位于“产品许可证”**** 中）。
    
5. 关闭“候选人”**** 用户帐户窗格。
    
## <a name="record-values-for-future-reference"></a>记录这些值以供将来参考

记录此开发/测试环境的这些值以用于 Office 365 和 EMS 试用订阅：
  
- 试用订阅组织名称：![](./images/Common_Images/TableLine.png) 
    
    例如，对于 contoso.onmicrosoft.com 的试用订阅域名，组织名称是“contoso”。
    
- Office 365 全局管理员名称：![](./images/Common_Images/TableLine.png).onmicrosoft.com
    
    在安全位置记录此帐户的密码和其他用户帐户的常用初始密码。
    
## <a name="next-step"></a>后续步骤

通过[在政治宣传活动开发/测试环境中创建团队网站](create-team-sites-in-a-political-campaign-dev-test-environment.md)，在此开发/测试环境中构建四种不同类型的 SharePoint Online 团队网站。
  
## <a name="see-also"></a>另请参阅

[Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[在政治宣传活动开发/测试环境中创建团队网站](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)




