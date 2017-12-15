---
title: "配置组和用户对于政治市场开发/测试环境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "摘要： 使用政治市场开发/测试环境的用户和组创建 Office 365 和企业移动 + 安全 (EMS) 的试用版本。"
ms.openlocfilehash: 7faf428fc2225d3f31297ba6bf83a10a7682009a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>配置组和用户对于政治市场开发/测试环境

 **摘要：**与政治市场开发/测试环境的用户和组创建 Office 365 和企业移动 + 安全 (EMS) 的试用版本。
  
使用本文中的说明创建包括简化的用户帐户和组的[Microsoft 安全指南为政治运动、 非营利性组织和其他的敏捷组织](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)解决方案的开发/测试环境。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>第 1 阶段：创建 Office 365 开发/测试环境

在此阶段中，您将获得 Office 365 E5 和企业移动性 + 表示政治运动的虚拟组织的安全 (EMS) E5 试用订阅。
  
首先，按照**第二阶段**的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。
  
接下来，EMS E5 试用订阅注册，即可将其添加到作为 Office 365 的试用订阅的同一组织。
  
1. 如果需要请登录到您的订购试用期的全局管理员帐户的凭据对 Office 365 门户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 单击**管理**拼贴。
    
3. 在浏览器中，在左边的导航中， **Office 管理中心**选项卡单击**计费 > 购买服务**。
    
4. **购买服务**页上找到**企业移动 + 安全 E5**项。将鼠标指针悬停在其上，单击**启动免费试用版**。
    
5. 在**确认订单**页中，单击**立即尝试**。
    
6. 在**订单收据**页上，单击**继续**。
    
下一步，使您的全局管理员帐户的 EMS E5 许可证。
  
1. 在浏览器中，在左边的导航中， **Office 365 管理中心**选项卡单击**用户 > 活动用户**。
    
2. 单击您的全局管理员帐户，然后单击**编辑****产品**许可证。
    
3. **产品许可证**的窗格中，在打开产品许可证**的企业移动性 + 安全 E5**到**上**，单击**保存**，然后两次单击**关闭**。
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>第 2 阶段： 创建和配置 Azure 活动目录 (AD) 组

在此阶段中，您创建和市场配置的 Azure AD 组。
  
首先，Azure 门户创建一组典型政治市场活动组。
  
1. 您的浏览器在单独的选项卡，请转到 Azure 门户网站位于[https://portal.azure.com](https://portal.azure.com)。如果需要请为您的 Office 365 E5 试用订阅登录的全局管理员帐户的凭据。
    
2. 在 Azure 的门户，单击**Azure Active Directory > 用户和组 > 所有组**。
    
3. 请执行以下步骤在此列表中每个组的名称：
    
  - 高级和战略性工作人员
    
  - IT 人员
    
  - 分析人员
    
  - 常规的核心人员
    
  - 操作人员
    
  - 现场员工
    
1. **所有组**刀片式服务器，请单击**+ 新组**。
    
2. 在**名称**中键入列表中的组名称。
    
3. 选择**动态的用户****成员身份**。
    
4. **启用 Office 功能**，请单击**是**。
    
5. 单击**添加动态查询**。
    
6. 在**中添加用户，**，选择**部门**。
    
7. 在下一个字段中，选择**等于**。
    
8. 在下一个字段中，键入列表中的组名称。
    
9. 单击**添加查询**，然后单击**创建**。
    
10. 单击**用户和组的所有组**。
    
下一步，以便成员会自动分配 Office 365 E5 和 EMS E5 许可证配置组。
  
1. 在 Azure 的门户，单击**Azure Active Directory > 许可证 > 所有产品**。
    
2. 在列表中，选择**企业移动 + 安全 E5**和**Office 365 企业 E5**，然后单击**+ 分配**。
    
3. 在**分派许可证**刀片式服务器，单击**用户和组**。
    
4. 在组列表中，选择下列设置：
    
  - 分析人员
    
  - 现场员工
    
  - IT 人员
    
  - 操作人员
    
  - 常规的核心人员
    
  - 高级和战略性工作人员
    
5. 单击**选择**，然后单击**分配**。
    
6. 关闭您的浏览器中的 Azure 门户选项卡。
    
## <a name="phase-3-add-your-user-accounts"></a>阶段 3： 添加用户帐户

在此阶段中，您添加示例用户帐户为您的政治运动。
  
首先，您[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。
  
接下来，您填写您的组织名称、 您所在的位置和常见的密码，并从 PowerShell 命令提示符或脚本集成环境 (ISE) 运行这些命令：
  
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
> 使用常见是配置的密码的自动化和易于开发/测试环境。不推荐用于生产订阅。随着每个新用户帐户登录，系统会提示您更改密码。 
  
使用下列步骤验证动态组成员关系和基于组的授权工作正常。
  
1. 从浏览器的**Microsoft Office 主页**选项卡上，单击**管理**拼贴。
    
2. 您的浏览器的新**办公室管理中心**标签，单击**用户**。
    
3. 在用户列表中，单击**候选**。
    
4. 在列出**候选**用户帐户的属性窗格中，请验证：
    
  - 它是**高级和战略性工作人员**（在**组成员身份**） 组的成员。
    
  - 它已分配**的企业移动性 + 安全 E5**和**Office 365 企业 E5**许可证 （在**产品许可证**）。
    
5. 关闭**候选**用户帐户窗格。
    
## <a name="record-values-for-future-reference"></a>记录值以供将来参考

记录这些值使用 Office 365 和 EMS 试用版本，此开发/测试环境：
  
- 您的订购试用期的组织名称: ___ 
    
    例如，contoso.onmicrosoft.com 的试用订阅域名，单位名称为"contoso"。
    
- Office 365 全局管理员名称： ___.onmicrosoft.com
    
    此帐户的密码和其他用户帐户的通用初始密码记录在一个安全的位置。
    
## <a name="next-step"></a>后续步骤

构建四个不同类型的 SharePoint Online 工作组网站[创建工作组网站的政治运动开发/测试环境中](create-team-sites-in-a-political-campaign-dev-test-environment.md)具有此开发/测试环境中。
  
## <a name="see-also"></a>See Also

[为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[在政治运动的开发/测试环境中创建工作组网站](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)




